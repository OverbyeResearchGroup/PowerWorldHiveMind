---
title: "TS Models — HVDC (Part 1 of 2)"
part: "Transient Models"
chapter_file: "45-ts-models-hvdc-part1.md"
topics: 30
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — HVDC (Part 1 of 2)

HVDC and VSC DC line dynamic models.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (30)**

- [HVDC](#hvdc)
- [Overview of HVDC Modelling](#overview-of-hvdc-modelling)
- [DC Line](#dc-line)
- [BPA_D](#bpa-d)
- [CDC1T](#cdc1t)
- [CDCMC](#cdcmc)
- [CEEL2T](#ceel2t)
- [CHATGY](#chatgy)
- [CHIGATT](#chigatt)
- [CHVDC2](#chvdc2)
- [CMDWS2T](#cmdws2t)
- [EPCDC](#epcdc)
- [RSPDC3](#rspdc3)
- [DC Line Auxiliary Controllers](#dc-line-auxiliary-controllers)
- [CHAAUT](#chaaut)
- [PAUX1T](#paux1t)
- [PAUX12T](#paux12t)
- [PAUX2T](#paux2t)
- [FCWDPT](#fcwdpt)
- [CFCAUT](#cfcaut)
- [SQBAUT](#sqbaut)
- [MTDC Convertor](#mtdc-convertor)
- [CONV_Adelanto](#conv-adelanto)
- [CONV_CELILO_E](#conv-celilo-e)
- [CONV_CELILO_N](#conv-celilo-n)
- [CONV_SYLMAR](#conv-sylmar)
- [Multi-Terminal DC](#multi-terminal-dc)
- [MTDC_IPP](#mtdc-ipp)
- [MTDC_PDCI](#mtdc-pdci)
- [VSC DC Line](#vsc-dc-line)

---

<a id="hvdc"></a>

## HVDC

*Source: [`Content/TransientModels_HTML/HVDC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/HVDC.htm)*

_This topic has no body text in the source help file._

---

<a id="overview-of-hvdc-modelling"></a>

## Overview of HVDC Modelling

*Source: [`Content/TransientModels_HTML/Overview of HVDC Modelling.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Overview of HVDC Modelling.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="dc-line"></a>

## DC Line

*Source: [`Content/TransientModels_HTML/DC Line.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line.htm)*

_This topic has no body text in the source help file._

---

<a id="bpa-d"></a>

## BPA_D

*Source: [`Content/TransientModels_HTML/DC Line BPA_D.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line BPA_D.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

PDF file to be added, please contact us.

**Parameters:**

|                |                                                                                                                                                                                   |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ControlMode\_r | Rectifier Control Mode: 0 = power control; 1 = current control                                                                                                                    |
| ControlMode\_i | Inverter Control Mode: 0 = power control; 1 = current control                                                                                                                     |
| MSU\_r         | Rectifier Margin switching unit key. A zero indicates that this situation has a margin switching unit, otherwise a margin swithcing unit is assumed not to exist for this station |
| MSU\_i         | Inverter Margin switching unit key. A zero indicates that this situation has a margin switching unit, otherwise a margin swithcing unit is assumed not to exist for this station  |
| TC\_r          | Rectifier Current measuring circuit time constant in seconds                                                                                                                      |
| TC\_i          | Inverter Current measuring circuit time constant in seconds                                                                                                                       |
| TV\_r          | Rectifier Voltage measuring circuit time constant in seconds                                                                                                                      |
| TV\_i          | Inverter Voltage measuring circuit time constant in seconds                                                                                                                       |
| T1\_r          | Rectifier Current regulator time constant in seconds                                                                                                                              |
| T1\_i          | Inverter Current regulator time constant in seconds                                                                                                                               |
| T2\_r          | Rectifier Current regulator time constant in seconds                                                                                                                              |
| T2\_i          | Inverter Current regulator time constant in seconds                                                                                                                               |
| T3\_r          | Rectifier Current regulator time constant in seconds                                                                                                                              |
| T3\_i          | Inverter Current regulator time constant in seconds                                                                                                                               |
| KA\_r          | Rectifier Current Regulotr gain in per unit DC voltage diviced by per unit DC current                                                                                             |
| KA\_i          | Inverter Current Regulotr gain in per unit DC voltage diviced by per unit DC current                                                                                              |
| IMAX\_r        | Rectifier Overload current capability in per unit                                                                                                                                 |
| IMAX\_i        | Inverter Overload current capability in per unit                                                                                                                                  |
| IMARGIN\_r     | Rectifier Current margin in per unit                                                                                                                                              |
| IMARGIN\_i     | Inverter Current margin in per unit                                                                                                                                               |
| ALPHASTOP\_r   | Rectifier Minimum firing angle in degress for operation of this sation as an inverter. The minimum firing angle for rectifier operation is specified in the power flow data       |
| ALPHASTOP\_i   | Inverter Minimum firing angle in degress for operation of this sation as an inverter. The minimum firing angle for rectifier operation is specified in the power flow data        |
| TD\_r          | Rectifier Commutating voltage time constant in seconds                                                                                                                            |
| TD\_i          | Inverter Commutating voltage time constant in seconds                                                                                                                             |
| VLIM\_r        | Rectifier percent of rated terminal voltage where current limiting begins                                                                                                         |
| VLIM\_i        | Inverter percent of rated terminal voltage where current limiting begins                                                                                                          |

---

<a id="cdc1t"></a>

## CDC1T

*Source: [`Content/TransientModels_HTML/DC Line CDC6.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line CDC6.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection on the Tmeasr, Tmeasi, and Tvrdc parameters

  - If 0.0 \< T \< 0.5\*Mult\*TimeStep then T = 0, ElseIf 0.5\*Mult\*TimeStep \< T \< Mult\*TimeStep then T = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![HVDC CDC6 0001](images/HVDC_CDC6_0001.svg)

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

**Parameters for CDC1T:**

|       |                                           |
| ----- | ----------------------------------------- |
| T1    | dc voltage transducer time constant (sec) |
| T2    | dc line current time constant (sec)       |
| IMIN  | minimum current demand (amps)             |
| I1    | limit point 1, current (amps)             |
| V2    | limit point 2, voltage (V)                |
| I2    | limit point 2, current (amps)             |
| V3    | limit point 3, voltage (V)                |
| I3    | limit point 3, current (amps)             |
| DELTI | current margin (pu)                       |
| VMIN  | shutdown voltage (pu)                     |
| VON   | unblocking voltage (pu)                   |
| TMIN  | minimum blocking time (sec)               |
| RAMP  | recovery rate (pu/sec)                    |

**Parameters for CDC4T:**

|          |                                                                                                        |
| -------- | ------------------------------------------------------------------------------------------------------ |
| AlphaMin | Minimum rectifier firing angle, degrees                                                                |
| GammaMin | Minimum inverter firing angle, degrees                                                                 |
| Tmeasv   | D.C. voltage transducer time constant,sec.                                                             |
| tmeasi   | D.C. current transducer time constant,sec.                                                             |
| Vblock   | Rectifier a.c. blocking voltage, p.u.                                                                  |
| Vunbl    | Rectifier a.c. unblocking voltage, p.u.                                                                |
| Tblock   | Minimum blocking time, sec.                                                                            |
| Vbypas   | Inverter d.c. voltage for bypassing, p.u.                                                              |
| Vunby    | Inverter a.c. unbypassing voltage, p.u.                                                                |
| Tbypas   | Minimum bypassing time, sec.                                                                           |
| Rsvolt   | Minimum d.c. voltage following block, kV                                                               |
| Rscur    | Minimum d.c. current following block, amps                                                             |
| Vramp    | Restart voltage ramping rate, pu/sec. (set to \<= 0 to ignore ramp and return to setpoint immediately) |
| Cramp    | Restart current ramping rate, pu/sec. (set to \<= 0 to ignore ramp and return to setpoint immediately) |
| C0       | Minimum d.c. current, amps                                                                             |
| V1       | VDCOL curve points, kV, amps                                                                           |
| C1       | VDCOL curve points, d.c. voltage, kv                                                                   |
| V2       | VDCOL curve points, kV, amps                                                                           |
| C2       | VDCOL curve points, d.c. voltage, kv                                                                   |
| V3       | VDCOL curve points, kV, amps                                                                           |
| C3       | VDCOL curve points, d.c. voltage, kv                                                                   |
| Tcmode   | Minimum time in forced current mode, sec.                                                              |

**Parameters for CDC6:**

|          |                                                                                                        |
| -------- | ------------------------------------------------------------------------------------------------------ |
| AlphaMin | Minimum rectifier firing angle, degrees                                                                |
| GammaMin | Minimum inverter firing angle, degrees                                                                 |
| Tmeasv   | D.C. voltage transducer time constant,sec.                                                             |
| tmeasi   | D.C. current transducer time constant,sec.                                                             |
| Vblock   | Rectifier a.c. blocking voltage, p.u.                                                                  |
| Vunbl    | Rectifier a.c. unblocking voltage, p.u.                                                                |
| Tblock   | Minimum blocking time, sec.                                                                            |
| Vbypas   | Inverter d.c. voltage for bypassing, p.u.                                                              |
| Vunby    | Inverter a.c. unbypassing voltage, p.u.                                                                |
| Tbypas   | Minimum bypassing time, sec.                                                                           |
| Rsvolt   | Minimum d.c. voltage following block, kV                                                               |
| Rscur    | Minimum d.c. current following block, amps                                                             |
| Vramp    | Restart voltage ramping rate, pu/sec. (set to \<= 0 to ignore ramp and return to setpoint immediately) |
| Cramp    | Restart current ramping rate, pu/sec. (set to \<= 0 to ignore ramp and return to setpoint immediately) |
| C0       | Minimum d.c. current, amps                                                                             |
| V1       | VDCOL curve points, kV, amps                                                                           |
| C1       | VDCOL curve points, d.c. voltage, kv                                                                   |
| V2       | VDCOL curve points, kV, amps                                                                           |
| C2       | VDCOL curve points, d.c. voltage, kv                                                                   |
| V3       | VDCOL curve points, kV, amps                                                                           |
| C3       | VDCOL curve points, d.c. voltage, kv                                                                   |
| Tcmode   | Minimum time in forced current mode, sec.                                                              |
| Vdeblk   | Rectifier time delayed blocking voltage, p.u.                                                          |
| Tdeblk   | Rectifier blocking delay time, sec.                                                                    |
| Treblk   | Rectifier unblocking delay time, sec.                                                                  |
| Vinblk   | Inverter time delayed blocking voltage, p.u.                                                           |
| Tcomb    | Communication delay for inverter blocl, sec.                                                           |
| Vacbyp   | Inverter a.c. voltage for bypass, p.u.                                                                 |
| Tdebyp   | Inverter time delayed bypass time, sec.                                                                |
| Tinblk   | Inverter unblocking delay time, sec.                                                                   |
| Tinbyp   | Inverter unbypassing delay time, sec.                                                                  |
| Tvrdc    | Rectifier d.c. voltage transducer time constant, sec.                                                  |
| Imarg    | Dynamic Current Margin, amps                                                                           |

**Parameters for CDC6T:**

|          |                                                                                                        |
| -------- | ------------------------------------------------------------------------------------------------------ |
| AlphaMin | Minimum rectifier firing angle, degrees                                                                |
| GammaMin | Minimum inverter firing angle, degrees                                                                 |
| Tmeasv   | D.C. voltage transducer time constant,sec.                                                             |
| tmeasi   | D.C. current transducer time constant,sec.                                                             |
| Vblock   | Rectifier a.c. blocking voltage, p.u.                                                                  |
| Vunbl    | Rectifier a.c. unblocking voltage, p.u.                                                                |
| Tblock   | Minimum blocking time, sec.                                                                            |
| Vbypas   | Inverter d.c. voltage for bypassing, p.u.                                                              |
| Vunby    | Inverter a.c. unbypassing voltage, p.u.                                                                |
| Tbypas   | Minimum bypassing time, sec.                                                                           |
| Rsvolt   | Minimum d.c. voltage following block, kV                                                               |
| Rscur    | Minimum d.c. current following block, amps                                                             |
| Vramp    | Restart voltage ramping rate, pu/sec. (set to \<= 0 to ignore ramp and return to setpoint immediately) |
| Cramp    | Restart current ramping rate, pu/sec. (set to \<= 0 to ignore ramp and return to setpoint immediately) |
| C0       | Minimum d.c. current, amps                                                                             |
| V1       | VDCOL curve points, kV, amps                                                                           |
| C1       | VDCOL curve points, d.c. voltage, kv                                                                   |
| V2       | VDCOL curve points, kV, amps                                                                           |
| C2       | VDCOL curve points, d.c. voltage, kv                                                                   |
| V3       | VDCOL curve points, kV, amps                                                                           |
| C3       | VDCOL curve points, d.c. voltage, kv                                                                   |
| Tcmode   | Minimum time in forced current mode, sec.                                                              |
| Vdeblk   | Rectifier time delayed blocking voltage, p.u.                                                          |
| Tdeblk   | Rectifier blocking delay time, sec.                                                                    |
| Treblk   | Rectifier unblocking delay time, sec.                                                                  |
| Vinblk   | Inverter time delayed blocking voltage, p.u.                                                           |
| Tcomb    | Communication delay for inverter blocl, sec.                                                           |
| Vacbyp   | Inverter a.c. voltage for bypass, p.u.                                                                 |
| Tdebyp   | Inverter time delayed bypass time, sec.                                                                |
| Tinblk   | Inverter unblocking delay time, sec.                                                                   |
| Tinbyp   | Inverter unbypassing delay time, sec.                                                                  |
| Tvrdc    | Rectifier d.c. voltage transducer time constant, sec.                                                  |

---

<a id="cdcmc"></a>

## CDCMC

*Source: [`Content/TransientModels_HTML/DC Line CDCMC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line CDCMC.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC CDCMC 0001](images/HVDC_CDCMC_0001.svg)

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

**Parameters:**

|         |                                                                                        |
| ------- | -------------------------------------------------------------------------------------- |
| ALFDY   | Minimum alpha for dynamics                                                             |
| GAMDY   | Minimum gamma for dynamics                                                             |
| KGI     | gain of gamma error feedback                                                           |
| TGI     | time constant of gamma error feedback                                                  |
| KACI    | inverter AC voltage error gain                                                         |
| KGR     | gain of alpha error feedback                                                           |
| TGR     | time constant of alpha error feedback                                                  |
| KACR    | rectifier AC voltage error gain                                                        |
| TAC2    | AC error signal lead time constant                                                     |
| TAC1    | AC error signal lag time constant                                                      |
| VACIHL  | high limit on inverter AC voltage feedback                                             |
| VACILL  | low limit on inverter AC voltage feedback                                              |
| VACRHL  | high limit o rectifier AC voltage feedback                                             |
| VACRLL  | low limit on rectifier AC voltage feedback                                             |
| EACHL   | AC error signal high limit                                                             |
| EACLL   | AC error signal low limit                                                              |
| KEDO    | Edo regulator gain                                                                     |
| TEDO    | Edo regulator time constant                                                            |
| EDOHL   | Edo regulator high limit                                                               |
| EDOLL   | Edo regulator low limit                                                                |
| VRFIMN  | Minimum AC inverter voltage (pu) which will create an initial limit violation warning  |
| VRFIMX  | Maximum AC inverter voltage (pu) which will create an initial limit violation warning  |
| VRFRMN  | Minimum AC rectifier voltage (pu) which will create an initial limit violation warning |
| VRFRMX  | Maximum AC rectifier voltage (pu) which will create an initial limit violation warning |
| ALFAH   | Alpha Hysteresis. Angle is not presently used by PowerWorld.                           |
| TP      | standard rectifier control lap time constant                                           |
| EVHL    | scheduled DC voltage high limit                                                        |
| EVLL    | scheduled DC voltage low limit                                                         |
| EDONOM  | nominal Edo regulator setpoint                                                         |
| TVDC    | voltage dip compensation lag time constant                                             |
| TOVDC   | voltage dip compensation time delay                                                    |
| IDCMX   | voltage dip compensation DC current maximum                                            |
| IDCMN   | voltage dip compensation DC current minimum                                            |
| VDCPK   | voltage dip compensation DC pickup voltage                                             |
| VDCMN   | voltage dip compienstion DC voltage minimum                                            |
| VDBASE  | rated DC line volts (kV)                                                               |
| IDBASE  | rated DC line current Amps                                                             |
| VBLOCK1 | delayed blocking threshold                                                             |
| VBLOCK2 | immediately block threshold                                                            |
| VUNBLOK | voltage for restart following blocking                                                 |
| TBLOCK  | delay time following dip below Vblockl                                                 |
| TUNBLOK | delay time for restart after dip to Vblock2                                            |
| CRAMP   | unblocking current ramp rate                                                           |

---

<a id="ceel2t"></a>

## CEEL2T

*Source: [`Content/TransientModels_HTML/DC Line CEEL2T.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line CEEL2T.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC CEEL2T 0001](images/HVDC_CEEL2T_0001.svg)

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

**Parameters:**

|            |                                                                                                                                           |
| ---------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| ALFDY      | minimum alpha for dynamics (degrees)                                                                                                      |
| GAMDY      | minimum gamma for dynamics (degrees)                                                                                                      |
| DELAYVDCL  | DELAY for VDCL (sec)                                                                                                                      |
| TIDR       | current order time constant (sec)                                                                                                         |
| SAMPLEVDCL | Sample rate for VDCL (sec)                                                                                                                |
| VUNBL      | rectifier ac unblocking voltage (pu)                                                                                                      |
| TBLKBY     | minimum blocking and bypass time (sec)                                                                                                    |
| dVdI       | Inverter DeltaV/DeltaI slope characteristic (V/amps)                                                                                      |
| VUNBY      | inverter ac unbypassing voltage (pu)                                                                                                      |
| ACCL       | model acceleration factor                                                                                                                 |
| RSVOLT     | minimum dc voltage following block (kV)                                                                                                   |
| RSCUR      | minimum dc current following block (amps)                                                                                                 |
| VRAMP      | voltage recovery rate (pu/sec)                                                                                                            |
| CRAMP      | current recovery rate (pu/sec)                                                                                                            |
| C0         | minimum current demand (amps)                                                                                                             |
| CL         | current lower on hysteresis limit (amps)                                                                                                  |
| CH         | current higher on hysteresis limit (amps) \>= CL                                                                                          |
| VL1        | voltage limit point 1 (pu)                                                                                                                |
| VL2        | voltage limit point 2 (pu)                                                                                                                |
| VH1        | voltage limit point 3 (pu)                                                                                                                |
| VH2        | voltage limit point 4 (pu)                                                                                                                |
| ALFMXI     | maximum inverter firing angle (degrees)                                                                                                   |
| VDEBLK     | rectifier ac voltage which causes a block if remains for time TDEBLK (pu)                                                                 |
| TDEBLK     | time delay for block (sec)                                                                                                                |
| TREBLK     | time delay after rectifier ac voltage recovers above VUNBL before line unblocks (sec)                                                     |
| VINBLK     | inverter ac voltage which causes block after communication delay TCOMB (pu)                                                               |
| TCOMB      | communication delay to signal rectifier to block because of low inverter voltage (sec)                                                    |
| VACBYP     | inverter ac voltage which causes bypass if remains for time TDEBYP (pu)b                                                                  |
| TDEBYP     | time delay for bypass (sec)                                                                                                               |
| TINBLK     | time delay after inverter ac voltage recovers above VUNBY before line unblocks (this value should also include communication delay) (sec) |
| TINBYP     | time delay after inverter ac voltage recovers above VUNBY before line unbypasses (sec)                                                    |
| TVP        | power control VDC transducer time constant (sec)                                                                                          |

---

<a id="chatgy"></a>

## CHATGY

*Source: [`Content/TransientModels_HTML/DC Line CHATGY.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line CHATGY.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC CHATGY 0001](images/HVDC_CHATGY_0001.svg)

![HVDC CHATGY 0002](images/HVDC_CHATGY_0002.svg)

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

**Parameters:**

|                |                                                                                                                                                                                    |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Direction      | Set to \>= 0 for the forward direction; Set to \< 0 for reverse direction                                                                                                          |
| BR\_Cntl       | Set to 0 to disable the Bang-Ramp limit                                                                                                                                            |
| LVCL\_Cntl     | Specify input voltage to low voltage current order limit (LVCL). 0 : disables LVCL; 1 : use filtered rectifier AC per unit voltage; 2 : user filtered inverter AC per unit voltage |
| CSP\_Cntl      | Set to 0 disables the CSP stabilizing power                                                                                                                                        |
| ISW            | \>=0 to subtract second signal from first; \<0 to subtract first signal from second (CHAAUT)                                                                                       |
| ALFRMIN        | Minimum alpha for dynamics                                                                                                                                                         |
| TIR            | Desired Current Output Time Constant (sec)                                                                                                                                         |
| TACV           | AC Voltage Transducer Time Constant (sec)                                                                                                                                          |
| TPR            | Power Reg Time Constant (sec)                                                                                                                                                      |
| TMPI           | AC Power Transducer (sec)                                                                                                                                                          |
| PIPOS          | Power Regulate Loop Max (MW)                                                                                                                                                       |
| PINEG          | Power Regulate Loop Min (MW)                                                                                                                                                       |
| TOverAllow     | Overload Time Allowed (sec)                                                                                                                                                        |
| TOverDelay     | Power Overload Initiation Delay (sec)                                                                                                                                              |
| IMAX           | Max Continuous Current (amps)                                                                                                                                                      |
| C0             | Minimum Current Demand (amps)                                                                                                                                                      |
| V1             | V Limit Point 1 (AC pu)                                                                                                                                                            |
| C1             | Current Limit Point 1 (amps)                                                                                                                                                       |
| V2             | V Limit Point 2 (AC pu)                                                                                                                                                            |
| C2             | Current Limit Point 2(amps)                                                                                                                                                        |
| V3             | V Limit Point 3 (AC pu)                                                                                                                                                            |
| C3             | Current Limit Point 3(amps)                                                                                                                                                        |
| VDEBLK         | Rectifier AC Volt Cause Blk                                                                                                                                                        |
| VUNBL          | Rect AC Unblock V (pu)                                                                                                                                                             |
| VINBLK         | Inverter Block V (pu)                                                                                                                                                              |
| VIUNB          | Inverter AC Unblock V (pu)                                                                                                                                                         |
| TDEBLK         | Time Delay for Block (sec)                                                                                                                                                         |
| TREBLK         | Delay After AC Volt Recovers (sec)                                                                                                                                                 |
| RampDown       | Ramp Rate Down (kA/sec)                                                                                                                                                            |
| RampUp         | Generator Ramp Rate Up (kA/sec)                                                                                                                                                    |
| BR\_I          | Current Bang-Ramp (A)                                                                                                                                                              |
| BR\_V          | AC per unit Volt Bang-Ramp Activate (pu)                                                                                                                                           |
| BR\_TD         | Time for Decrease Bang-Ramp (sec)                                                                                                                                                  |
| BR\_TU         | Time for Increase Bang-Ramp (sec)                                                                                                                                                  |
| BR\_TBOT       | Time for bottom for Bang-Ramp (sec)                                                                                                                                                |
| BR\_Tdelay     | Bang-Ramp Init delay (sec)                                                                                                                                                         |
| BR\_Ireset     | Bang-Ramp reset current (A)                                                                                                                                                        |
| BR\_Max        | Bang-Ramp max number of bangs                                                                                                                                                      |
| CSP\_T1        | CSP – Beau Modulation (sec)                                                                                                                                                        |
| CSP\_T2        | CSP – Beau Modulation (sec)                                                                                                                                                        |
| CSP\_T3        | CSP – Beau Modulation (sec)                                                                                                                                                        |
| CSP\_K         | CSP Gain – Beau Modulation (sec)                                                                                                                                                   |
| CSP\_Lp        | CSP Lmt – Beau Modulation (sec)                                                                                                                                                    |
| CSP\_Ln        | CSP Lmt – Beau Modulation (sec)                                                                                                                                                    |
| Vramp          | Voltage ramp-up (kV/sec)                                                                                                                                                           |
| Cramp          | Current ramp-up (kA/sec)                                                                                                                                                           |
| TLVCLI         | Transducer time constant at inverter for LVCL (sec)                                                                                                                                |
| TLVCLR         | Transducer time constant at rectifier for LVCL (sec)                                                                                                                               |
| RISERATE\_LVCL | LVCL Bottom Line Rise Rate (A/sec)                                                                                                                                                 |
| FP1            | Signal 1 positive frequency deviation dead band threshold (Hz) (CHAAUT)                                                                                                            |
| FN1            | Signal 1 negative frequency deviation dead band threshold (Hz) (CHAAUT)                                                                                                            |
| MP1            | Signal 1 positive slope (MW/Hz) (CHAAUT)                                                                                                                                           |
| MN1            | Signal 1 negative slope (MW/Hz) (CHAAUT)                                                                                                                                           |
| KP1            | Signal 1 Proportional Gain (CHAAUT)                                                                                                                                                |
| KD1            | Signal 1 Derivative Gain (CHAAUT)                                                                                                                                                  |
| T1             | Signal 1 first time constant (sec) (CHAAUT)                                                                                                                                        |
| T2             | Signal 1 second time constant (sec) (CHAAUT)                                                                                                                                       |
| FP2            | Signal 2 positive frequency deviation dead band threshold (Hz) (CHAAUT)                                                                                                            |
| FN2            | Signal 2 negative frequency deviation dead band threshold (Hz) (CHAAUT)                                                                                                            |
| MP2            | Signal 2 positive slope (MW/Hz) (CHAAUT)                                                                                                                                           |
| MN2            | Signal 2 negative slope (MW/Hz) (CHAAUT)                                                                                                                                           |
| KP2            | Signal 2 Proportional Gain (CHAAUT)                                                                                                                                                |
| KD2            | Signal 2 Derivative Gain (CHAAUT)                                                                                                                                                  |
| T3             | Signal 2 first time constant (sec) (CHAAUT)                                                                                                                                        |
| T4             | Signal 2 second time constant (sec) (CHAAUT)                                                                                                                                       |
| DPDTMX         | Signal 1 Rate Limit Maximum (MW/sec) (CHAAUT)                                                                                                                                      |
| DPDTMN         | Signal 1 Rate Limit Minimum (MW/sec) (CHAAUT)                                                                                                                                      |
| TM1            | Signal 1 transducer time constant (sec) (CHAAUT)                                                                                                                                   |
| TM2            | Signal 2 transducer time constant (sec) (CHAAUT)                                                                                                                                   |
| P1POS          | Signal 1 Maximum (MW) (CHAAUT)                                                                                                                                                     |
| P1NEG          | Signal 1 Minimum (MW) (CHAAUT)                                                                                                                                                     |
| P2POS          | Signal 2 Maximum (MW) (CHAAUT)                                                                                                                                                     |
| P2NEG          | Signal 2 Minimum (MW) (CHAAUT)                                                                                                                                                     |

---

<a id="chigatt"></a>

## CHIGATT

*Source: [`Content/TransientModels_HTML/DC Line CHIGATT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line CHIGATT.htm)*

**AutoCorrection Properties**

To be documented.

**HVDC CHIGATT: Two terminal D.C. Transmission**

This model has most of the same dynamic characteristics as CDC6T but with some modifications

> • Auxiliary Signal Index 1 feeds into the MW schedule.

> • Auxiliary Signal 2 feeds into the voltage signal.

> • Input Parameter dVdI can be specified to change the slope of DC voltage/DC current characteristic as a transition between the full current and drop due to current margin is done. See the Bridge and Line Simulation Logic in the CDC6T help. dVdI represents the slope between points Y and X on that curve

> • The voltage measurement used for the input to the VDCOL has 2 different time constants

> > o VDCOLUP is the time constant used when the voltage is increasing

> > o VDCOLDN is the time constant used when the voltage is decreasing

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

Model supported by PSSE

**Parameters:**

|         |                                                                                                                                           |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| ALFDY   | minimum alpha for dynamics (degrees)                                                                                                      |
| GAMDY   | minimum gamma for dynamics (degrees)                                                                                                      |
| VDCOLUP | voltage transducer time constant up (sec)                                                                                                 |
| TIDC    | dc current transducer time constant (sec)                                                                                                 |
| VDCOLDN | voltage transducer time constant down (sec)                                                                                               |
| VUNBL   | rectifier ac unblocking voltage (pu)                                                                                                      |
| TBLKBY  | minimum blocking and bypassing time (sec)                                                                                                 |
| dVdI    | Inverter DeltaV/DeltaI slope characteristic (V/amps)                                                                                      |
| VUNBY   | inverter ac unbypassing voltage (pu)                                                                                                      |
| ACCL    | model acceleration factor                                                                                                                 |
| RSVOLT  | minimum dc voltage following block (kV)                                                                                                   |
| RSCUR   | minimum dc current following block (amps)                                                                                                 |
| VRAMP   | voltage recovery rate (pu/sec)                                                                                                            |
| CRAMP   | current recovery rate (pu/sec)                                                                                                            |
| C0      | minimum current demand (amps)                                                                                                             |
| V1      | voltage limit point 1                                                                                                                     |
| C1      | current limit (amps); \>= C0                                                                                                              |
| V2      | voltage limit point 2                                                                                                                     |
| C2      | current limit point 2 (amps)                                                                                                              |
| V3      | voltage limit point 3                                                                                                                     |
| C3      | current limit point 3 (amps)                                                                                                              |
| ALFMXI  | maximum inverter firing angle (degrees)                                                                                                   |
| VDEBLK  | rectifier ac voltage that causes a block if remains for time TDEBLK (pu)                                                                  |
| TDEBLK  | time delay for block (sec)                                                                                                                |
| TREBLK  | time delay after rectifier ac voltage recovers above VUNBL before line unblocks (sec)                                                     |
| VINBLK  | inverter ac voltage that causes block after communication delay TCOMB (pu)                                                                |
| TCOMB   | communication delay to signal rectifier to block because of low inverter voltage (sec)                                                    |
| VACBYP  | inverter ac voltage that causes bypass if remains for time TDEBYP (pu)                                                                    |
| TDEBYP  | time delay for bypass (sec)                                                                                                               |
| TINBLK  | time delay after inverter ac voltage recovers above VUNBY before line unblocks (this value should also include communication delay) (sec) |
| TINBYP  | time delay after inverter ac voltage recovers above VUNBY before line unbypasses (sec)                                                    |
| TVP     | power control VDC transducer time constant (sec)                                                                                          |

---

<a id="chvdc2"></a>

## CHVDC2

*Source: [`Content/TransientModels_HTML/DC Line CHVDC2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line CHVDC2.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< 0.5\*Mult\*TimeStep then Ts = 0, ElseIf 0.5\*Mult\*TimeStep \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep  
    (same done for Tref, Tmax, Tur, Tdr, Tui, Tdi, and Tram)
  - If Tvd \< Mult\*TimeStep then Tvd = Mult\*TimeStep
  - If rmax\< rmin then swap the values. If rmax \< 0 then rmax change sign to positive. If rmin \> 0 then change sign to negative.  
    (same is done for max\_err and min\_err)

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - if Vac\_ref is larger than either the initial inverter bus or rectifier bus ac per unit voltage and the AC VDCOL is active, then Vac\_ref will be modified to be equal to the minimum of these two values.
  - If the natural frequency of the RLC circuit formed by DC circuit is to large, then this would result in numerical problems. To prevent this, the capacitance of the DC line will be ignored.
  - if either Talpr and Talpi are less than 2\*TimeStep, then they are changed to be equal to 2\*TimeStep.

Model Equations and/or Block Diagrams

![HVDC CHVDC2 0001](images/HVDC_CHVDC2_0001.svg)

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

**Parameters:**

|                 |                                                                                                   |
| --------------- | ------------------------------------------------------------------------------------------------- |
| Flag            | If = 1 then use AC VDCOL is in-service, else it is disabled                                       |
| Talpr           | time constant for current control for rectifier controls                                          |
| Kir             | integral gain for current control for rectifier controls                                          |
| Kpr             | proportional gain for current control for rectifier controls                                      |
| Alpha\_max\_r   | maximum alpha on rectifier side in degrees                                                        |
| Alpha\_min\_r   | minimum alpha on rectifier side in degrees                                                        |
| Idc\_margin\_r  | dc current margin on rectifier side                                                               |
| maxc            | max for alpha max calculation loop on Ierr                                                        |
| minc            | max for alpha max calculation loop on Ierr                                                        |
| rmax            | Angle Control max Rate in Degrees per second                                                      |
| rmin            | Angle Control min Rate in Degrees per second                                                      |
| Tr              | measurement transducer time constant                                                              |
| Talpi           | time constant for current control for inverter controls                                           |
| Kii             | integral gain for current control for inverter controls                                           |
| Kpi             | proportional gain for current control for inverter controls                                       |
| Kcos            | proportional gain for alpha max calculation loop                                                  |
| Kref            | gain for alpha max calculation loop on Iref                                                       |
| Tref            | time constant for alpha max calculation loop on Iref                                              |
| Kmax            | proportional gain for alpha max calculation loop on Ierr                                          |
| Tmax            | time constant for alpha max calculation loop on Ierr                                              |
| cosmin\_i       | constant                                                                                          |
| Alpha\_min\_i   | minimum alpha on inverter side in degrees                                                         |
| Idc\_margin\_i  | dc current margin on inverter side                                                                |
| Imax1           | VDCOL break point 1 in per unit of the Irate parameter                                            |
| Imax2           | VDCOL break point 2 in per unit of the Irate parameter                                            |
| V1              | VDCOL break point 1 in per unit of the Vrate parameter                                            |
| V2              | VDCOL break point 2 in per unit of the Vrate parameter                                            |
| Tur             | VDCOL Measurement transducer time constant for voltage rising rectifier side                      |
| Tdr             | VDCOL Measurement transducer time constant for voltage falling rectifier side                     |
| Tui             | VDCOL Measurement transducer time constant for voltage rising inverter side                       |
| Tdi             | VDCOL Measurement transducer time constant for voltage falling inverter side                      |
| Imax\_lim       | VDCOL output current order maximum limit                                                          |
| Imin\_lim       | VDCOL output current order minimum limit                                                          |
| max\_err        | VDCOL AC voltage input error maximum limit                                                        |
| min\_err        | VDCOL AC voltage input error minimum limit                                                        |
| Tvd             | VDCOL integrator time constant                                                                    |
| Vac\_ref        | VDCOL AC voltage reference (pu)                                                                   |
| alpha\_max\_ram | Rectifier Alpha Min Limiter (RAML) max alpha in degrees                                           |
| Tram            | Rectifier Angle Minimum Limiter (RAML) washout time constant                                      |
| Vram            | Rectifier Angle Minimum Limiter (RAML) ac voltage setpoint                                        |
| Ttram           | Rectifier Angle Minimum Limiter (RAML) timer                                                      |
| Lline           | DC line inductance (mH)                                                                           |
| Lsmr\_rec       | The inductance of the smoothing reactor at the rectifier end (mH)                                 |
| Lsmr\_inv       | The inductance of the smoothing reactor at the inverter end (mH)                                  |
| C               | DC line capacitance (microF)                                                                      |
| gamma\_cf       | angle below which commutation failure is likely (default value = 10 degrees)                      |
| Tcf             | minimum time duration that commutation failure is likely to last ( default value = 0.034 seconds) |
| Vac\_ucf        | voltage above which converter will recover from commutation failure (default value = 0.9)         |
| Irate           | DC Current Rating in Amps                                                                         |
| Vrate           | DC Voltage Rating in kV                                                                           |

![HVDC CHVDC2 0002](images/HVDC_CHVDC2_0002.svg)

![HVDC CHVDC2 0003](images/HVDC_CHVDC2_0003.svg)

![HVDC CHVDC2 0004](images/HVDC_CHVDC2_0004.svg)

![HVDC CHVDC2 0005](images/HVDC_CHVDC2_0005.svg)

![HVDC CHVDC2 0006](images/HVDC_CHVDC2_0006.svg)

![HVDC CHVDC2 0007](images/HVDC_CHVDC2_0007.svg)

![HVDC CHVDC2 0008](images/HVDC_CHVDC2_0008.svg)

![HVDC CHVDC2 0009](images/HVDC_CHVDC2_0009.svg)

---

<a id="cmdws2t"></a>

## CMDWS2T

*Source: [`Content/TransientModels_HTML/DC Line CMDWS2T.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line CMDWS2T.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC CMDWS2T 0001](images/HVDC_CMDWS2T_0001.svg)

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

**Parameters:**

|            |                                                                                              |
| ---------- | -------------------------------------------------------------------------------------------- |
| ALFDY      | minimum alpha for dynamics (degrees)                                                         |
| GAMDY      | minimum gamma for dynamics (degrees)                                                         |
| DELAYVDCL  | DELAY for VDCL (sec)                                                                         |
| TIODC      | TIDC dc current order time constant (sec)                                                    |
| SAMPLEVDCL | Sample rate for VDCL (sec)                                                                   |
| VUNBL      | rectifier ac unblocking voltage (pu)                                                         |
| TBLKBY     | minimum blocking and bypass time (sec)                                                       |
| dVdI       | Inverter DeltaV/DeltaI slope characteristic (V/amps)                                         |
| VUNBY      | inverter ac unbypassing and unblocking voltage (pu)                                          |
| ACCL       | model acceleration factor                                                                    |
| RSVOLT     | minimum dc voltage following block (kV)                                                      |
| RSCUR      | minimum dc current following block (amps)                                                    |
| VRAMP      | voltage recovery rate (pu/sec)                                                               |
| CRAMP      | current recovery rate (amps/sec)                                                             |
| C0         | minimum current demand (amps)                                                                |
| CL         | current lower on hysteresis limit (amps)                                                     |
| CH         | current higher on hysteresis limit (amps) \>= CL                                             |
| VL1        | voltage limit point 1 (pu)                                                                   |
| VL2        | voltage limit point 2 (pu)                                                                   |
| VH1        | voltage limit point 3 (pu)                                                                   |
| VH2        | voltage limit point 4 (pu)                                                                   |
| ALFMXI     | maximum inverter firing angle (degrees)                                                      |
| VDEBLK     | rectifier ac voltage that causes a block if remains for time TDEBLK (pu)                     |
| TDEBLK     | time delay for block                                                                         |
| TREBLK     | time delay after rectifier ac voltage recovers above VUNBL before line unblocks              |
| VINBLK     | inverter ac voltage that causes block after communication delay TCOMB (pu)                   |
| TCOMB      | communication delay to signal rectifier to block because of low inverter voltage (sec)       |
| VACBYP     | inverter ac voltage that causes bypass if remains for time TDEBYP (pu)                       |
| TDEBYP     | time delay for bypass                                                                        |
| TINBLK     | time delay after inverter ac voltage recovers above VUNBY before line unblocks or unbypasses |
| VRAMPI     | dc voltage threshold to ramp current up or down                                              |
| TVP        | power control VDC transducer time constant (sec);                                            |

---

<a id="epcdc"></a>

## EPCDC

*Source: [`Content/TransientModels_HTML/DC Line EPCDC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line EPCDC.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC EPCDC 0001](images/HVDC_EPCDC_0001.svg)

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

**Parameters:**

|          |                                                      |
| -------- | ---------------------------------------------------- |
| alphamin | Minimum rectifier firing angle, degrees              |
| gammamin | Minimum inverter firing angle, degrees               |
| tmeasv   | D.C. voltage transducer time constant, sec.          |
| tmeasi   | D.C. current transducer time constant, sec.          |
| trdown   | Rectifier VDCOL downward time constant               |
| trup     | Rectifier VDCOL upward time constant                 |
| tidown   | Inverter VDCOL downward time constant                |
| tiup     | Inverter VDCOL upward time constant                  |
| v1r      | Rectifier VDCOL voltage break points, Kv             |
| v2r      | Rectifier VDCOL voltage break points, Kv             |
| v3r      | Rectifier VDCOL voltage break points, Kv             |
| v4r      | Rectifier VDCOL voltage break points, Kv             |
| c1r      | Rectifier VDCOL current break points. p.u.           |
| c2r      | Rectifier VDCOL current break points. p.u.           |
| v1i      | Inverter VDCOL voltage break points, Kv              |
| v2i      | Inverter VDCOL voltage break points, Kv              |
| v3i      | Inverter VDCOL voltage break points, Kv              |
| v4i      | Inverter VDCOL voltage break points, Kv              |
| c1i      | Inverter VDCOL current break points, p.u.            |
| c2i      | Inverter VDCOL current break points, p.u.            |
| cmin     | Minimum current order, amps                          |
| cmax     | Maximum current order, amps                          |
| vblock   | Rectifier ac voltage for inst. block,p.u.            |
| vunbl    | Rectifier ac voltage for unblock, p.u.               |
| tblock   | Rectifier minimum block time, sec.                   |
| vbypas   | Inverter dc voltage for bypassing, p.u.              |
| vunby    | Inverter ac voltage for unbypass, p.u.               |
| tbypas   | Inverter minimum bypass time, sec.                   |
| tcmode   | Minimum time in enforced current mode, sec.          |
| vdeblk   | Rectifier ac voltage for delayed block, p.u.         |
| tdeblk   | Rectifier pickup time for delayed block, sec.        |
| treblk   | Rect. min block time for delayed block, sec.         |
| vacbyp   | Inverter ac voltage for delayed bypass, p.u.         |
| tdebyp   | Inv pickup time for time delayed bypass, sec.        |
| tinbyp   | Inv min bypass time for delayed bypass, sec.         |
| vchange  | Sudden inv ac volt change for inst bypass, p.u.      |
| tvchange | Sudden voltage change detector time constant, sec.   |
| imarg    | Current margin, amps                                 |
| rcut     | NOT USED. Apparent Res of volt rise controller, ohms |
| alphamax | NOT USED. Maximum rectifier firing angle, degrees    |
| gammamax | NOT USED. Maximum inverter firing angle, degrees     |
| accel    | NOT USED. Solution acceleration factor               |
| tpcmcu   | NOT USED. Integration time constant of bpa PCMCU     |

---

<a id="rspdc3"></a>

## RSPDC3

*Source: [`Content/TransientModels_HTML/DC Line RSPDC3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line RSPDC3.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC RSPDC3 0001](images/HVDC_RSPDC3_0001.svg)

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

**Parameters:**

|          |                                                                                                                |
| -------- | -------------------------------------------------------------------------------------------------------------- |
| INITMODE | Set to value \<= 0 to attempt to control to initial rectifier power; Set to \> 0 to regular to initial current |
| MODMODE  | 1 means use the FCWDPT signal; 2 means use the CFCAUX signal; otherwise no modulation signal                   |
| ALFDY    | Minimum rectifier firing angle (degrees) (CDC6T)                                                               |
| GAMDY    | Minimum inverter firing angle (degrees) (CDC6T)                                                                |
| TVDC     | DC voltage transducer time constant (sec) (CDC6T)                                                              |
| TIDC     | DC current transducer time constant (sec) (CDC6T)                                                              |
| VBLOCK   | Rectifier ac blocking voltage (pu) (CDC6T)                                                                     |
| VUNBL    | Rectifier ac unblocking voltage (pu) (CDC6T)                                                                   |
| TBLOCK   | Minimum blocking time (sec) (CDC6T)                                                                            |
| VBYPAS   | Inverter dc voltage for bypassing (kV) (CDC6T)                                                                 |
| VUNBY    | Inverter ac unbypassing voltage (pu) (CDC6T)                                                                   |
| TBYPAS   | Minimum bypassing time (sec) (CDC6T)                                                                           |
| RSVOLT   | Minimum dc voltage following block (kV) (CDC6T)                                                                |
| RSCUR    | Minimum dc current following block (amps) (CDC6T)                                                              |
| VRAMP    | Restart voltage ramping rate (kv/sec) (CDC6T)                                                                  |
| CRAMP    | Restart current ramping rate (amps/sec) (CDC6T)                                                                |
| C0       | Minimum dc current (amps) (CDC6T)                                                                              |
| V1       | Point 1 VDCOL curve (kv) (CDC6T)                                                                               |
| C1       | Point 1 VDCOL curve (Amp) (CDC6T)                                                                              |
| V2       | Point 2 VDCOL curve (kv) (CDC6T)                                                                               |
| C2       | Point 2 VDCOL curve (Amp) (CDC6T)                                                                              |
| V3       | Point 3 VDCOL curve (kv) (CDC6T)                                                                               |
| C3       | Point 3 VDCOL curve (Amp) (CDC6T)                                                                              |
| TCMODE   | Minimum time in forced current mode (sec) (CDC6T)                                                              |
| VDEBLK   | Rectifier time delayed blocking voltage (pu) (CDC6T)                                                           |
| TDEBLK   | Rectifier blocking delay time (sec) (CDC6T)                                                                    |
| TREBLK   | Rectifier unblocking delay time (sec) (CDC6T)                                                                  |
| VINBLK   | Inverter time delayed blocking voltage (pu) (CDC6T)                                                            |
| TCOMB    | Communication delay for inverter block (sec) (CDC6T)                                                           |
| VACBYP   | Inverter ac voltage for bypass (pu) (CDC6T)                                                                    |
| TDEBYP   | Inverter time delayed bypass time (sec) (CDC6T)                                                                |
| TINBLK   | Inverter unblocking delay time (sec) (CDC6T)                                                                   |
| TINBYP   | Inverter unbypassing delay time (sec) (CDC6T)                                                                  |
| TVRDC    | Rectifier dc volt transducer time constant (sec) (CDC6T)                                                       |
| TMFD     | Time Constant (sec) (FCWDPT)                                                                                   |
| dbH      | Deadband High (Hz) (FCWDPT)                                                                                    |
| dbL      | Deadband Low (Hz) (FCWDPT)                                                                                     |
| K1       | K1 (MW/Hz) (FCWDPT)                                                                                            |
| DPMAX    | Deadband Maximum (MW) (FCWDPT)                                                                                 |
| DPMIN    | Deadband Minimum (MW) (FCWDPT)                                                                                 |
| K2       | K2 (MW/Hz) (FCWDPT)                                                                                            |
| TMFP     | Time Constant (Sec) (CFCAUT)                                                                                   |
| KP       | Proportional Gain (MW/hz) (CFCAUT)                                                                             |
| KI       | Integral Gain (MW/hz/sec) (CFCAUT)                                                                             |
| IPMAX    | Integral Maximum (MW) (CFCAUT)                                                                                 |
| IPMIN    | Integral Minimum (MW) (CFCAUT)                                                                                 |
| PMAX     | Auxiliary Maximum (MW)                                                                                         |
| PMIN     | Auxiliary Minimum (MW)                                                                                         |

---

<a id="dc-line-auxiliary-controllers"></a>

## DC Line Auxiliary Controllers

*Source: [`Content/TransientModels_HTML/DC Line Auxiliary Controllers.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line Auxiliary Controllers.htm)*

_This topic has no body text in the source help file._

---

<a id="chaaut"></a>

## CHAAUT

*Source: [`Content/TransientModels_HTML/DC Line CHAAUT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line CHAAUT.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC CHAAUT 0001](images/HVDC_CHAAUT_0001.svg)

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

**Parameters:**

|        |                                                                                     |
| ------ | ----------------------------------------------------------------------------------- |
| ISW    | \>=0 to subtract second signal from first; \<0 to subtract first signal from second |
| FP1    | Signal 1 positive frequency deviation dead band threshold (Hz)                      |
| FN1    | Signal 1 negative frequency deviation dead band threshold (Hz)                      |
| MP1    | Signal 1 positive slope (MW/Hz)                                                     |
| MN1    | Signal 1 negative slope (MW/Hz)                                                     |
| KP1    | Signal 1 Proportional Gain                                                          |
| KD1    | Signal 1 Derivative Gain                                                            |
| T1     | Signal 1 first time constant (sec)                                                  |
| T2     | Signal 1 second time constant (sec)                                                 |
| FP2    | Signal 2 positive frequency deviation dead band threshold (Hz)                      |
| FN2    | Signal 2 negative frequency deviation dead band threshold (Hz)                      |
| MP2    | Signal 2 positive slope (MW/Hz)                                                     |
| MN2    | Signal 2 negative slope (MW/Hz)                                                     |
| KP2    | Signal 2 Proportional Gain                                                          |
| KD2    | Signal 2 Derivative Gain                                                            |
| T3     | Signal 2 first time constant (sec)                                                  |
| T4     | Signal 2 second time constant (sec)                                                 |
| DPDTMX | Signal 1 Rate Limit Maximum (MW/sec)                                                |
| DPDTMN | Signal 1 Rate Limit Minimum (MW/sec)                                                |
| TM1    | Signal 1 transducer time constant (sec)                                             |
| TM2    | Signal 2 transducer time constant (sec)                                             |
| P1POS  | Signal 1 Maximum (MW)                                                               |
| P1NEG  | Signal 1 Minimum (MW)                                                               |
| P2POS  | Signal 2 Maximum (MW)                                                               |
| P2NEG  | Signal 2 Minimum (MW)                                                               |

---

<a id="paux1t"></a>

## PAUX1T

*Source: [`Content/TransientModels_HTML/DC Line PAUX1T.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line PAUX1T.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC PAUX1T 0001](images/HVDC_PAUX1T_0001.svg)

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

**Parameters:**

|     |                                                  |
| --- | ------------------------------------------------ |
| TR  | Time Constant (sec)                              |
| TD  | Pure Delay (sec). Must be 10 or fewer time-steps |
| KC  | Gain                                             |
| MAX | Maximum (MW)                                     |
| MIN | Minimum (MW)                                     |

---

<a id="paux12t"></a>

## PAUX12T

*Source: [`Content/TransientModels_HTML/DC Line PAUX12T.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line PAUX12T.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC PAUX12T 0001](images/HVDC_PAUX12T_0001.svg)

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

**Parameters:**

|       |                                                  |
| ----- | ------------------------------------------------ |
| TR11  | Time Constant (sec)                              |
| TD11  | Pure Delay (sec). Must be 10 or fewer time-steps |
| KC11  | Gain                                             |
| MAX11 | Maximum (pu)                                     |
| MIN11 | Minimum (pu)                                     |
| TR12  | Time Constant (sec)                              |
| TD12  | Pure Delay (sec). Must be 10 or fewer time-steps |
| KC12  | Gain                                             |
| MAX12 | Maximum (pu)                                     |
| MIN12 | Minimum (pu)                                     |
| TR2   | Time Constant (sec)                              |
| TD2   | Pure Delay (sec). Must be 9 or fewer time-steps  |
| KC2   | Gain                                             |
| T1    | Washout 1 Numerator \> 0 (sec)                   |
| T2    | Washout 2 Numerator \> 0 (sec)                   |
| T3    | Washout 1 Demominator \> 0 (sec)                 |
| T4    | Washout 2 Demominator \> 0 (sec)                 |
| MAX2  | Maximum (pu)                                     |
| MIN2  | Minimum (pu)                                     |

---

<a id="paux2t"></a>

## PAUX2T

*Source: [`Content/TransientModels_HTML/DC Line PAUX2T.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line PAUX2T.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC PAUX2T 0001](images/HVDC_PAUX2T_0001.svg)

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

**Parameters:**

|     |                                                 |
| --- | ----------------------------------------------- |
| TR  | Time Constant (sec)                             |
| TD  | Pure Delay (sec). Must be 9 or fewer time-steps |
| KC  | Gain                                            |
| T1  | Washout 1 Numerator \> 0 (sec)                  |
| T2  | Washout 2 Numerator \> 0 (sec)                  |
| T3  | Washout 1 Demominator \> 0 (sec)                |
| T4  | Washout 2 Demominator \> 0 (sec)                |
| MAX | Maximum (MW)                                    |
| MIN | Minimum (MW)                                    |

---

<a id="fcwdpt"></a>

## FCWDPT

*Source: [`Content/TransientModels_HTML/DC Line FCWDPT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line FCWDPT.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC FCWDPT 0001](images/HVDC_FCWDPT_0001.svg)

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

**Parameters:**

|       |                                      |
| ----- | ------------------------------------ |
| TMFD  | Time Constant (sec)                  |
| dbH   | Deadband High (Hz)                   |
| dbL   | Deadband Low (Hz)                    |
| K1    | Gain subject to deadband (MW/Hz)     |
| DPMAX | Maximum (MW)                         |
| DPMIN | Minimum (MW)                         |
| K2    | Gain not subject to deadband (MW/Hz) |

---

<a id="cfcaut"></a>

## CFCAUT

*Source: [`Content/TransientModels_HTML/DC Line CFCAUT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line CFCAUT.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC CFCAUT 0001](images/HVDC_CFCAUT_0001.svg)

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

**Parameters:**

|       |                           |
| ----- | ------------------------- |
| TMFP  | Time Constant (sec)       |
| KP    | Proportional Gain (MW/Hz) |
| KI    | Integral Gain (MW/Hz/Sec) |
| IPMAX | Integral Maximum (MW)     |
| IPMIN | Integral Minimum (MW)     |

---

<a id="sqbaut"></a>

## SQBAUT

*Source: [`Content/TransientModels_HTML/DC Line SQBAUT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/DC Line SQBAUT.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC SQBAUT 0001](images/HVDC_SQBAUT_0001.svg)

For a Detailed Treatment of how DC lines are implemented in the software see the help topic [here](#overview-of-hvdc-modelling).

**Parameters:**

|       |                                               |
| ----- | --------------------------------------------- |
| KDC   | Proportional Gain (Amps/Hz)                   |
| KAC   | Derivative Gain (Amp\*Second/Hz)              |
| T2    | Time Constant (seconds) \>0                   |
| A1    | Notch Filter Numerator s                      |
| A2    | Notch Filter Numerator s^2                    |
| B1    | Notch Filter Denominator s                    |
| B2    | Notch Filter Denominator s^2, \>0             |
| IMAX  | Maximum Current (Amps)                        |
| IMIN  | Minimum Current (Amps)                        |
| ISTEP | Current step (Amps)                           |
| TD    | Communication delay (seconds) \<10 time steps |
| TL    | Lag Time (seconds)                            |

---

<a id="mtdc-convertor"></a>

## MTDC Convertor

*Source: [`Content/TransientModels_HTML/MTDC Convertor.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/MTDC Convertor.htm)*

_This topic has no body text in the source help file._

---

<a id="conv-adelanto"></a>

## CONV_Adelanto

*Source: [`Content/TransientModels_HTML/HVDC CONV_IntMtnPP and Conv_Adelanto.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/HVDC CONV_IntMtnPP and Conv_Adelanto.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC CONV IntMtnPP and Conv Adelanto 0001](images/HVDC_CONV_IntMtnPP_and_Conv_Adelanto_0001.svg)

![HVDC CONV IntMtnPP and Conv Adelanto 0002](images/HVDC_CONV_IntMtnPP_and_Conv_Adelanto_0002.svg)

![HVDC CONV IntMtnPP and Conv Adelanto 0003](images/HVDC_CONV_IntMtnPP_and_Conv_Adelanto_0003.svg)

---

<a id="conv-celilo-e"></a>

## CONV_CELILO_E

*Source: [`Content/TransientModels_HTML/HVDC CONV_CELILO_E.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/HVDC CONV_CELILO_E.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC CONV CELILO E 0001](images/HVDC_CONV_CELILO_E_0001.svg)

---

<a id="conv-celilo-n"></a>

## CONV_CELILO_N

*Source: [`Content/TransientModels_HTML/HVDC CONV_CELILO_N.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/HVDC CONV_CELILO_N.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC CONV CELILO N 0001](images/HVDC_CONV_CELILO_N_0001.svg)

![HVDC CONV CELILO N 0002](images/HVDC_CONV_CELILO_N_0002.svg)

---

<a id="conv-sylmar"></a>

## CONV_SYLMAR

*Source: [`Content/TransientModels_HTML/HVDC CONV_SYLMAR.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/HVDC CONV_SYLMAR.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams

![HVDC CONV SYLMAR 0001](images/HVDC_CONV_SYLMAR_0001.svg)

![HVDC CONV SYLMAR 0002](images/HVDC_CONV_SYLMAR_0002.svg)

---

<a id="multi-terminal-dc"></a>

## Multi-Terminal DC

*Source: [`Content/TransientModels_HTML/Multi-Terminal DC.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Multi-Terminal DC.htm)*

_This topic has no body text in the source help file._

---

<a id="mtdc-ipp"></a>

## MTDC_IPP

*Source: [`Content/TransientModels_HTML/HVDC MTDC_IPP.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/HVDC MTDC_IPP.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="mtdc-pdci"></a>

## MTDC_PDCI

*Source: [`Content/TransientModels_HTML/HVDC MTDC_PDCI.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/HVDC MTDC_PDCI.htm)*

**AutoCorrection Properties**

To be documented.

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="vsc-dc-line"></a>

## VSC DC Line

*Source: [`Content/TransientModels_HTML/VSC DC Line.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/VSC DC Line.htm)*

_This topic has no body text in the source help file._
