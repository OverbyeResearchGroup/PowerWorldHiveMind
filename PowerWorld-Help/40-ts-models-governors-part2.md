---
title: "TS Models — Governors (Part 2 of 4)"
part: "Transient Models"
chapter_file: "40-ts-models-governors-part2.md"
topics: 8
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — Governors (Part 2 of 4)

Turbine-governor models (GGOV, IEEEG, GAST, HYGOV, WT*T, and the rest).

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (8)**

- [H6E](#h6e)
- [HRSGSimple](#hrsgsimple)
- [Hydro_Bradley](#hydro-bradley)
- [HYG3](#hyg3)
- [HYGOV](#hygov)
- [HYGOV2](#hygov2)
- [HYGOV4](#hygov4)
- [HYGOVR](#hygovr)

---

<a id="h6e"></a>

## H6E

*Source: [`Content/TransientModels_HTML/Governor H6E.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor H6E.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - Values of Tpe, Td, Tg, Tbd, and Tbs must be larger than Mult\*TimeStep. If they are between 0 and 0.5\*Mult\*TimeStep, then they are changed to 0.0. If they are between 0.5\*Mult\*TimeStep they are changed to Mult\*TimeStep
  - Abs(Tsp) must be larger than Mult\*TimeStep. If it is not it is changed to an absolute value of Mult\*TimeStep. Reminder that Tsp can be negative indicating that the input is per unit bus frequency instead of per unit rotor speed.
  - If 0.0 \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If Gmax \< Gmin then the values are flipped by auto-correction
  - If (Bgvmin \>= 0.99999) OR (Bgvmin \< 0) then an error message is displayed and the simulation will not run.

Following treatment is handled during the transient numerical simulation

  - If Fd is not either 0 or 1, then it is treated as though it is a 1.
  - If Ki \<= 0.000001 then it is treated as a value of 0.000001
  - If Gate \> Gmax, then Gmax = Gate or if Gate \< Gmin, then Gmin = Gate
  - Negative values of velm, buv, blg, dbbd, blb, dbbs, and blv will be treated as the absolute value of the number specified
  - Negative values of dturb and deff will be ignored and treated as a value of 0.0000
  - Sprate \<= 0 will be treated as indication to ignore sprate

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams

![Governor H6E 0001](images/Governor_H6E_0001.svg)

**Parameters:**

<table>
<tbody>
<tr class="odd">
<td>trate</td>
<td>Turbine power base, MW</td>
</tr>
<tr class="even">
<td>fd</td>
<td><p>Flag for proportional elec power signal; 0 = Speed control mode - droop is based on gate servo stroke;</p>
<p>1 = Load control mode - droop is based on electric power</p></td>
</tr>
<tr class="odd">
<td>re</td>
<td>Permanent droop for electrical power feedback, pu</td>
</tr>
<tr class="even">
<td>rg</td>
<td>Permanent droop for gate position feedback, pu</td>
</tr>
<tr class="odd">
<td>tpe</td>
<td>Electric power feedback transducer time const, sec</td>
</tr>
<tr class="even">
<td>tsp</td>
<td>Shaft speed transducer time const, sec</td>
</tr>
<tr class="odd">
<td>kp</td>
<td>Governor proportional gain</td>
</tr>
<tr class="even">
<td>ki</td>
<td>Governor integral gain</td>
</tr>
<tr class="odd">
<td>kd</td>
<td>Governor derivative gain</td>
</tr>
<tr class="even">
<td>td</td>
<td>Derivative gain filter time constant, sec</td>
</tr>
<tr class="odd">
<td>velm</td>
<td>Maximum gate actuator velocity, pu/sec</td>
</tr>
<tr class="even">
<td>gmax</td>
<td>Maximum gate actuator stroke, pu</td>
</tr>
<tr class="odd">
<td>gmin</td>
<td>Minimum gate actuator stroke, pu</td>
</tr>
<tr class="even">
<td>buf</td>
<td>Upper limit of gate buffer region, pu</td>
</tr>
<tr class="odd">
<td>buv</td>
<td>Max gate closing rate in buffer region, pu</td>
</tr>
<tr class="even">
<td>kg</td>
<td>Pilot servovalve gain</td>
</tr>
<tr class="odd">
<td>tg</td>
<td>Pilot servovalve time constant, sec</td>
</tr>
<tr class="even">
<td>blg</td>
<td>Backlash in ring linkage</td>
</tr>
<tr class="odd">
<td>dbbd</td>
<td>Deliberate sliding deadband in digital blade cam output</td>
</tr>
<tr class="even">
<td>tbd</td>
<td>Time constant of sliding deliberate dead band, sec</td>
</tr>
<tr class="odd">
<td>blb</td>
<td>Backlash in blade adjustment linkage</td>
</tr>
<tr class="even">
<td>dbbs</td>
<td>Mechanical deadband in blade servovalve/motor</td>
</tr>
<tr class="odd">
<td>tbs</td>
<td>Blade servo time constant, sec</td>
</tr>
<tr class="even">
<td>bgvmin</td>
<td>Flow area factor of blades when at minimum position</td>
</tr>
<tr class="odd">
<td>blv</td>
<td>Maximum stroking rate of blade servomotor</td>
</tr>
<tr class="even">
<td>dturb</td>
<td>Turbine speed sensitivity constant</td>
</tr>
<tr class="odd">
<td>pgc</td>
<td>Electric motoring power with gates fully closed, pu</td>
</tr>
<tr class="even">
<td>deff</td>
<td>Off blade angle power decrease factor</td>
</tr>
<tr class="odd">
<td>hdam</td>
<td>Operating head, pu</td>
</tr>
<tr class="even">
<td>tw</td>
<td>water inertia time constant, sec</td>
</tr>
<tr class="odd">
<td>sprate</td>
<td>speed-load setpoint adjustment rate, pu/sec</td>
</tr>
<tr class="even">
<td>gv0</td>
<td>Abscissa value 0 for wicket gate and blade curves</td>
</tr>
<tr class="odd">
<td>gv1</td>
<td>Abscissa value 1 for wicket gate and blade curves</td>
</tr>
<tr class="even">
<td>gv2</td>
<td>Abscissa value 2 for wicket gate and blade curves</td>
</tr>
<tr class="odd">
<td>gv3</td>
<td>Abscissa value 3 for wicket gate and blade curves</td>
</tr>
<tr class="even">
<td>gv4</td>
<td>Abscissa value 4 for wicket gate and blade curves</td>
</tr>
<tr class="odd">
<td>gv5</td>
<td>Abscissa value 5 for wicket gate and blade curves</td>
</tr>
<tr class="even">
<td>gv6</td>
<td>Abscissa value 6 for wicket gate and blade curves</td>
</tr>
<tr class="odd">
<td>gv7</td>
<td>Abscissa value 7 for wicket gate and blade curves</td>
</tr>
<tr class="even">
<td>gv8</td>
<td>Abscissa value 8 for wicket gate and blade curves</td>
</tr>
<tr class="odd">
<td>gv9</td>
<td>Abscissa value 9 for wicket gate and blade curves</td>
</tr>
<tr class="even">
<td>pgv0</td>
<td>Value 0 for Curve of wicket gate flow area</td>
</tr>
<tr class="odd">
<td>pgv1</td>
<td>Value 1 for Curve of wicket gate flow area</td>
</tr>
<tr class="even">
<td>pgv2</td>
<td>Value 2 for Curve of wicket gate flow area</td>
</tr>
<tr class="odd">
<td>pgv3</td>
<td>Value 3 for Curve of wicket gate flow area</td>
</tr>
<tr class="even">
<td>pgv4</td>
<td>Value 4 for Curve of wicket gate flow area</td>
</tr>
<tr class="odd">
<td>pgv5</td>
<td>Value 5 for Curve of wicket gate flow area</td>
</tr>
<tr class="even">
<td>pgv6</td>
<td>Value 6 for Curve of wicket gate flow area</td>
</tr>
<tr class="odd">
<td>pgv7</td>
<td>Value 7 for Curve of wicket gate flow area</td>
</tr>
<tr class="even">
<td>pgv8</td>
<td>Value 8 for Curve of wicket gate flow area</td>
</tr>
<tr class="odd">
<td>pgv9</td>
<td>Value 9 for Curve of wicket gate flow area</td>
</tr>
<tr class="even">
<td>bgv0</td>
<td>Value 0 for Curve of Kaplan turbine blade flow area as function of gate servo stroke</td>
</tr>
<tr class="odd">
<td>bgv1</td>
<td>Value 1 for Curve of Kaplan turbine blade flow area as function of gate servo stroke</td>
</tr>
<tr class="even">
<td>bgv2</td>
<td>Value 2 for Curve of Kaplan turbine blade flow area as function of gate servo stroke</td>
</tr>
<tr class="odd">
<td>bgv3</td>
<td>Value 3 for Curve of Kaplan turbine blade flow area as function of gate servo stroke</td>
</tr>
<tr class="even">
<td>bgv4</td>
<td>Value 4 for Curve of Kaplan turbine blade flow area as function of gate servo stroke</td>
</tr>
<tr class="odd">
<td>bgv5</td>
<td>Value 5 for Curve of Kaplan turbine blade flow area as function of gate servo stroke</td>
</tr>
<tr class="even">
<td>bgv6</td>
<td>Value 6 for Curve of Kaplan turbine blade flow area as function of gate servo stroke</td>
</tr>
<tr class="odd">
<td>bgv7</td>
<td>Value 7 for Curve of Kaplan turbine blade flow area as function of gate servo stroke</td>
</tr>
<tr class="even">
<td>bgv8</td>
<td>Value 8 for Curve of Kaplan turbine blade flow area as function of gate servo stroke</td>
</tr>
<tr class="odd">
<td>bgv9</td>
<td>Value 9 for Curve of Kaplan turbine blade flow area as function of gate servo stroke</td>
</tr>
</tbody>
</table>

![Governor H6E 0002](images/Governor_H6E_0002.svg) ![Governor H6E 0003](images/Governor_H6E_0003.svg)

**PowerWorld Implementation in Pseudo-Code**

**User Input Parameters for Model**

ffd, ftrate, fre, frg, finvtpe, finvtsp, fkp, fki, fkd,

finvtd, fvelm, fgmax, fgmin, fbuf, fbuv, fkg, finvtg,

fblg, fdbbd, finvtbd, fblb, fdbbs, finvtbs, fbgvmin,

fblv, fdturb, fpgc, fdeff, fhdam, finvtw, fsprate : **single**;

// Note various parameters such as finvtpe are storing 1/tpe

fBackLash\_blb, fBackLash\_blg : BackLash Object; // see below

fP\_Q, fB\_GV : Nonlinear Lookup Tables

These tables are created from the input parameters GV0…GV9, PGV0…PGV9, and BGV0…BGV9.

See section below for details of how these are calculated.

Cached Values with model

These variables are availabe inside all functions.

cache\_Spref, cache\_LastTimeStepGateCommand, cache\_GateCommand, cache\_Hscroll,

cache\_BC, cache\_GV, cache\_BB, cache\_BH, cache\_AB, cache\_AF : **double**;

State and Derivative Value Syntax

`Derivative[INDEX] : Derivative of state INDEX for model`

`StateVector[INDEX] : Value of state INDEX for model`

`IgnoreStateVector[INDEX] : boolean indicating if state INDEX is ignored`

**Nonlinear Lookup Curves** **(GV0…GV9, PGV0…PGV9, BGV0…BGV9)**

After reading these input parameters three lookup tables are created

  // force fbgvmin to between 0 and 1, but not equal to those numbers

  **if**      fbgvmin \< **0.00001** **then** fbgvmin := **0.00001**

  **else** **if** fbgvmin \> **0.99999** **then** fbgvmin := **0.99999**;

  **for** i := **0** **to** **9** **do begin**

    // Calculate steady state Q for particular gate value

**  ** QGV\[i\] := GV\[i\]\*( fbgvmin + (**1**-fbgvmin) \* BGV\[i\]);

  **End**;

  // Create lookup function and add first point. 

  // The FALSE in constructor means to not extrapolite past the start and end point

  fP\_Q := PiecewiseLinearFunctionObject.Create(QGV\[**0**\],PGV\[**0**\],**FALSE**);

  fB\_GV := PiecewiseLinearFunctionObject.Create( GV\[**0**\],BGV\[**0**\],**FALSE**);

  **For** i := **1** **to** **9** **Do** **Begin**

    **if** (GV\[i\] \> **0**) **then** **begin**

      fP\_Q.AddPointInOrder(QGV\[i\],PGV\[i\]); // Power vs Q

      fB\_GV.AddPointInOrder(GV\[i\],BGV\[i\]); // B vs Gate

    **end**;

  **End**;

// PiecewiseLinearFunctionObject just encapsulates a lookup function. 

// Method X(index) returns the X value of the X,Y part at a particular index

// Method Y(index) returns the Y value of the X,Y part at a particular index

// Method XtoY takes an input X value and calculates the output Y// Method YtoX takes an output Y value and calculates the input X

BackLash Object

    fDeadband : **Double**; 

    fLastOutput: **Double**;  // Tells the last output value

  **Public**

    **Constructor** **CreateBackLash**(tDeadband,tInitialOutput : **Double**);

    **Function** **Output**(anInput : **Double**) : **Double**;

**BackLash**.**CreateBackLash**(tDeadband,tInitialOutput : **Double**);

Begin

  fDeadBand := tDeadBand;

  **If** fDeadband \< **0** **Then** fDeadband := **0**;  // Must be non-negative

  fLastOutput := tInitialOutput;

**End**;

**Function** **BackLash**.**Output**(anInput : **Double**) : **Double**;

Begin

  **If** (anInput \>= fLastOutput-fDeadband) **and** (anInput \<= fLastOutput+fDeadBand) **Then begin**

**  ** Result := fLastOutput;

  **End**

**  Else** **Begin**

    **If** anInput \> fLastOutput+fDeadband

    **Then** Result := anInput-fDeadBand // Going up, subtract off deadband

    **Else** Result := anInput+fDeadBand; // Going down, add deadband

    fLastOutput := Result;

  **End**;

**End**;

Start of Each TimeStep

Begin

  cache\_LastTimeStepGateCommand := cache\_GateCommand;

`    ``// Update the cache_Spref value using a rate limiter`

`    `**if**`  Pref > cache_Spref  `**then** **begin**

    cache\_spref := cache\_spref + fsprate \* timeStepSeconds;

`      `**if**`  cache_spref > Pref  `**then**`  cache_spref := Pref; `

`    `**end**

`    `**else** **if**`  Pref < cache_Spref  `**then** **begin**

    cache\_spref := cache\_spref - fsprate \* timeStepSeconds;

`      `**if**`  cache_spref < Pref  `**then**`  cache_spref := Pref; `

`    `**end**`;`

**end**`;`

function to return the Pmech to feed to machine model

**var**`  local_Q, local_MinQ :  `**double**`;`

begin

`  local_Q := StateVector[`**9**`];`

`  // hydraulic power`

`    `**if**`  fP_Q.Count >  `**0** **then** **begin**

`    local_MinQ := fP_Q.X(`**1**`);`

`      `**if**`  (local_Q < local_MinQ)  `**and**`  (local_MinQ >  `**0**`)`

`      `**then** `result``  := cache_Hscroll * (fpgc * (local_Q - local_MinQ)/local_MinQ) `

`      `**else** `result``  := cache_Hscroll * (fP_Q.XtoY( local_Q ) - fdeff* ``sqr``(cache_bh - cache_bb));`

`    `**end**

`    `**else** **begin**

`      ``result``  := cache_Hscroll * (local_Q - fdeff* ``sqr``(cache_bh - cache_bb));`

`    `**end**`;`

`    ``result``  :=  ``result``  - deltaWPU * fDTurb * cache_GV; `

`  // put turbine power on appropriate per unit base`

`    ``result``  :=  ``result``/GenObject.MVABase*fTrate;`

**end**`;`

**InitializeForIntegration Function**

**Var**`  local_pq, `

    local\_gv,

    local\_q,

`     local_af    :  `**Double**` ;   ``// local values for initialization`

`     Local_Pmech :  `**double**`;`

`     Local_PElec :  `**double**` ;  `

Begin

  Local\_Pmech := GenObject.PMechObjectInitInternal;

  Local\_Pmech := Local\_Pmech\*GenObject.MVABase/fTrate;

  Local\_PElec := PElec;

  Local\_PElec := Local\_PElec\*GenObject.MVABase/fTrate;

`  local_pq := Local_Pmech/(`**1.0**`*fHdam);`

`    `**if**`  local_pq > fP_Q.LastY  `**then begin** `// added initial limit violation check in February 2022`

`    fHdam := local_Pmech / fP_Q.LastY;` `// added some log messages`

`    local_pq := Local_Pmech/(`**1.0**`*fHdam);`

`    `**end;**

  local\_q := fP\_Q.YtoX(local\_pq);

`  local_af := local_q/``sqrt``(fHdam);`** **

`  local_afmax := fgmax* (fbgvmin + (1-fbgvmin)*fB_GV.XtoY(fgmax) );`

**if** `(local_af > local_afmax)`

`      and  `**LOCAL\_BackSolveForQ**`(local_afmax, local_Pmech, local_q)`

**then begin** `// added initial limit violation check in September 2022`

    local\_gv := fgmax;

    local\_af := local\_afmax;

`     fHdam := sqr(local_q/local_afmax);  ``// added some log messages``      `

  end

  else begin

`     local_gv :=  `**LOCAL\_BackSolveForGate**` (local_af);  ``// see on following pages`

  end;

  // Modified fgmin and fgmax if Governor Response Limits flag ("base load") is used.

  cache\_GateCommand := local\_gv;

  cache\_LastTimeStepGateCommand := local\_gv;

  cache\_BC := fB\_GV.XtoY(local\_gv);

  cache\_GV := local\_gv;

  cache\_BB := cache\_BC;

  cache\_BH := cache\_BC;

`  cache_AB := (fbgvmin + (`**1**`-fbgvmin)*cache_BB);`

  cache\_AF := cache\_AB \* local\_gv;

  cache\_Hscroll := GOVERNOR\_DivideAndSquareForHead(local\_q, cache\_af, fHdam);

`    `**If**`  fblb <>  `**0** **Then**`  fBackLash_blb := TTxBacklash.CreateBackLash( `**self**`,fblb,cache_BB);`

`    `**If**`  fblg <>  `**0** **Then**`  fBackLash_blg := TTxBacklash.CreateBackLash( `**self**`,fblg,local_GV);`

`  StateVector[`**1**`] := Local_PElec;`

`  StateVector[`**2**` ] :=  `**1.0**` ;  ``// speed`

`  StateVector[`**4**` ] :=  `**0.0**` ;  ``// model input to derivative state as (speed - 1)`

`  StateVector[`**5**` ] :=  `**0.0**`;`

`  StateVector[`**6**`] := local_gv;`

`  StateVector[`**7**`] := cache_BC;`

`  StateVector[`**8**`] := cache_BC;`

`  StateVector[`**9**`] := local_q;`

`    ``// PIDInput = Pref - Speed - Relec*PElec - Rg*Gate`

`    ``//            PIDInput must be zero initially because we require Ki > 0`

`    ``// 1.0 here represents the initial speed`

`    `**if**`  ffd = 0  `**then** **begin**

`     Pref :=  `**1.0**`  + local_gv*fRg; `

`    StateVector[`**3**` ] := local_gv;  `

`    `**end**

`    `**else** **begin**

`     Pref :=  `**1.0**`  + local_PElec*fRe; `

`    StateVector[`**3**` ] := local_gv - fKp*(Pref -  `**1.0**` );  `

`    `**end**`;`

  cache\_Spref := Pref;

`  // Set ignored states (this is a boolean vector PowerWorld uses to signify ignored states)`

`    `**if**`  fInvtpe =  `**0** **then**`  IgnoreStateVector[ `**1**`] := True;`

`    `**if**`  fInvtsp =  `**0** **then**`  IgnoreStateVector[ `**2**`] := True;`

`    ``// 23 is the Ki integrator`

`    `**if**`  fInvTd  =  `**0** **then**`  IgnoreStateVector[ `**4**`] := True;`

`    `**if**`  fInvtg  =  `**0** **then**`  IgnoreStateVector[ `**5**`] := True;`

`    ``// 56 is the gate integrator`

`    `**if**`  fInvtbd =  `**0** **then** `IgnoreStateVector[`**7**`] := True;`

`    `**if**`  fInvtbs =  `**0** **then**`  IgnoreStateVector[ `**8**`] := True;`

`    ``// 89 is the water integrator`

**end**`;`

**function** **LOCAL\_BackSolveForGate**` (local_af :  `**double**` ) :  `**double**`;`

`    `**var**`  i :  `**integer**`;`

      local\_gk, local\_gm, local\_bk, local\_bm,

      local\_slope,

`       local_A, local_B, local_C :  `**double**`;`

`    `**begin**

`      ``Result``  :=  `**0**` ;  `

    i := fB\_GV.Count;

`      `**if**`  i =  `**0** **then** **begin** `        ``// just assume Bgv = 1.0 always, which means that`

`        ``result``  := local_af; `

`        `**exit**`;`

`      `**end**`;`

`      `**if**`  i =  `**1** **then** **begin**

`      local_bk := fB_GV.Y(`**1**`);`

`        ``result``  := local_af/( fbgvmin + local_bk*( `**1**`-fbgvmin) );`

`        `**exit**`;`

`      `**end**`;`

`      `**while**`  i >=  `**0** **do** **begin**

      local\_gk := fB\_GV.X(i);

`       local_bk := fB_GV.Y(i);    `

`        `**if** ` local_af < local_gk*( fbgvmin + local_bk*(1-fbgvmin) )  `**then** **begin** ` // just keep going  `

`          `**if**`  i =  `**1** **then** **begin             ** `// However if i = 1, this is degenerate case!`

`           ` `result :=``  local_af/( fbgvmin + local_bk*( `**1**`-fbgvmin) );`

`            `**exit**`;`

`          `**end**`;`

`        `**end**

`        `**else** **begin**

`          `**if**`  (i = fB_GV.Count)  `**then** **begin**

`            `` result  ``:= local_af/( fbgvmin + local_bk*(`**1**` -fbgvmin) );  ``// just use this last Bk value`

`            `**exit**`;`

`          `**end**

`          `**else** **begin**

`          local_gm := fB_GV.X(i+`**1**`);`

`          local_bm := fB_GV.Y(i+`**1**`);`

          local\_slope := (local\_bm - local\_bk)/(local\_gm - local\_gk);

`            `**if** `abs`` (local_Slope) >  `**1E-6** **then** **begin**

`              ``{`

             we are trying to solve for gv given the value of af.

                 af = gv \* \[ bgvmin + (1-bgvmin)\*Bgv \]

             Solve this for Bgv to make it easier for next step and we have

                       af/gv - bgvmin

                 Bgv = --------------

                         1 - bgvmin

             If we're one of the line segments of the Bgv vs Gv curve then we have

             a line segement going from (gk, bk) sloping up to (gm, bm)

                                      (bm-bk)

                 Bgv = bk + (gv-gk) \* -------

                                      (gm-gk)

           Now equate these two function for Bgv and solve for gv  (Note | just grouping stuff)

                     1    |   -af    |    |  bgvmin               (bm-bk)|        |(bm-bk)|

                0 = --- \* |--------- |  + |---------- + bk - gk \* -------| + gv \* |-------|

                    gv    |(1-bgvmin)|    |(1-bgvmin)             (gm-gk)|        |(gm-gk)|

             Now, multiply through by gv and make terms for "A, B, C" for quadratic function

`                0 = C + B*gv + C*sqr(gv)   }`

`            local_C := -local_AF/(`**1**`-fbgvmin);`

`            local_B := fbgvmin/(`**1**`-fbgvmin) + local_bk - local_gk*local_slope;`

            local\_A := local\_Slope;

`              ``result``  := (- local_B +  ``sqrt`` (  ``sqr`` (local_B) -  `**4**`*local_A*local_C))/ (`**2**`*local_A);`

`              `**exit**`;`

`            `**end**

`            `**else** **begin**

`              ``{`

            We're on a slope with constant Bk, so back to  af = gv \* \[ bgvmin + (1-bgvmin)\*Bgv \]

            Which can be solved as                         gv = af/bgvmin + bk\*(1-bgvmin)

            }

`              ``result``  := local_af/( fbgvmin + local_bk*( `**1**`-fbgvmin) );`

`              `**exit**`;`

`            `**end**`;`

`          `**end**`;`

`        `**end**`;`

`       i := i -  `**1**`;`

`      `**end**`;`

`    `**end**`;`

**function** **LOCAL\_BackSolveForQ**` (local_afmax, local_Pmech :  `**double**` ; var local_q :  `**double**` ) :  `**boolean**`;`

`        ``{`

This function was added in September 2022 to handle situation where the maximum gate

Value is not enough to achieve the af value necessary to get Pmech desired. 

We will again solve this by increasing the Hdam value

       Solving Equations: sqr(q/afmax) = Hdam  and  P(q)\*Hdam = Pmech

       Substitute first equation into the second one --\>   P(q)\*sqr(q/afmax) = Pmech

          P(q)\*sqr(q) = Pmech\*sqr(afmax)

          P(q)\*sqr(q) - Pmech\*sqr(afmax) = 0

       If P(q) = q  (meaning we have piecewise linear function at all this degenerate solution is

          q \* sqr(q/afmax) = Pmech --\> q = (Pmech\*sqr(afmax)) ^ (1/3)

       Otherwise, we have only 1 point (or we end up on a horizontal segment), then this mean that P(q) is a constant

       If P(q) = Pk (1 point, or we have a zero slope on this segment)

          Pk \* sqr(q/afmax) = Pmech --\> q = sqrt(Pmech/Pk)\*afmax

       Otherwise we're looking at somewhere between 2 points

       Assume we're on line segment between (qk, Pk) and (qm, Pm), so we can write

                               (Pm-Pk)

          P(q) = Pk + (q-qk) \* -------

                               (qm-qk)

                      (Pm-Pk)             (Pm-Pk)

          P(q) =  q \* ------- + Pk - qk \* -------

                      (qm-qk)             (qm-qk)

                      (Pm-Pk)

       Define Slope = -------

                      (qm-qk)

          P(q) = q\*Slope + Pk - qk\*Slope

          P(q)\*sqr(q) - Pmech\*sqr(afmax) = 0

          (q\*slope + Pk - qk\*Slope)\*sqr(q) - Pmech\*sqr(afmax) = 0

          \[Slope\]\*q^3 + \[Pk - qk\*Slope\]\*q^2 + \[- Pmech\*sqr(afmax)\] = 0;

          Slope = (Pm-Pk)/(qm-qk)

`          A     = Slope              // A > 0 (bad user input otherwise)`

`          B     = Pk - qk*Slope      // B can be positive or negative`

`          D     = -Pmech*sqr(afmax)  // D < 0 (Pmech can’t be negative!)`

`       By assuming Slope > 0 this means that we have 1 sign change when looking through the`

`       Polynomial coefficients, so by Descartes sign rule, we have exactly 1 positive real root`

       Degenerate situation when no P vs Q curve exists. In this situation P(q) = q always

`       (multiplier is just 1.00)`

          P(q)\*sqr(q) - Pmech\*sqr(afmax) = 0

          q^3 = Pmech\*sqr(afmax)

          q = ( Pmech\*sqr(afmax) ) ^(1/3) // cube root

`        Degenerate situation when Slope = 0, then this is  `

                A=0; B=Pk; C=0; D=-Pmech\*sqr(afmax)

                Pk\*sqr(q) = Pmech\*sqr(afmax)

          Solution is then

                q = sqrt(Pmech/Pk)\*afmax

      }

`      `**procedure** **LOCAL\_HandlePkConstant**` (local_Pk:  `**double**`);`

`      `**begin**

`        `**if** ` local_Pk < 0.0001  `**then** ` local_Pk := 0.0001;  ``// this should never happen!`

      Result := true;

      Local\_q := sqrt(local\_Pmech/local\_Pk) \* local\_afmax;

`      `**end**`;`

`    `**var** ` i :  `**integer**`;`

      local\_qk, local\_qm, local\_Pk, local\_Pm,

`       _A, _B, _D, local_slope, _Pmech_sqrAfmax :  `**double**`;`

**begin**

    result := false;

    \_Pmech\_sqrAfmax := local\_Pmech\*sqr(local\_afmax);

    i := fP\_Q.Count;

`      `**if**`  i = 0  `**then begin**

`       result := true;  `

`       local_q := GOVERNOR_CubeRoot(_Pmech_sqrAfmax);  `

`    `**   ** `exit;`

    end;

`      `**if**`  i = 1  `**then begin**

      local\_Pk := fP\_Q.Y(1);

`        `**LOCAL\_HandlePkConstant**`(local_Pk);`

**    ** `exit;`

    end;

    Result := 0;

`     ` **while** ` i >= 0  `**do begin**

      local\_qk := fP\_Q.X(i);

      local\_Pk := fP\_Q.Y(i);

`        `**if** ` sqr(local_qk)*local_Pk > _Pmech_sqrAfmax  `**then begin**

        // just keep going normally here,       

`        `**  if** ` i = 1  `**then begin** `// However if i = 1, this is silly case!`

`            `**LOCAL\_HandlePkConstant**`(local_Pk);`

          exit;

`          `**end**`;`

      end

      else begin

`          `**if** ` (i = fP_Q.Count)  `**then begin**

`            `**LOCAL\_HandlePkConstant**`(local_Pk);`

**       end**

        else begin

          local\_qm := fP\_Q.X(i+1);

          local\_Pm := fP\_Q.Y(i+1);

          local\_slope := (local\_Pm - local\_Pk)/(local\_qm - local\_qk);

`            `**if** ` abs(local_Slope) < 1E-6  `**then begin**

`              `**LOCAL\_HandlePkConstant**`(local_Pk);`**           **

          end

**          else if** ` local_Slope > 0  `**then begin** `// Solving A*q^3 + B*q^2 + D = 0`

`             _A := local_Slope;                      ``// must be positive`

`            _B := local_Pk - local_qk*local_Slope;``  // Could by pos or neg `

`             _D := -_Pmech_sqrAfmax;                 ``// must be negative`

`              `` // Because A>0 and D<0, then there is exactly 1 sign change  `

`            // By Descartes Rule of Signs, this means there is ONE positive answer`

            result := true;            

`             Local_q := SolveCubicAndReturnPositiveRealAnswer(_A,_B,0,_D);  `

          end;

        end;

**       ** ` Exit;  ``// exit no matter what here.  If a local_Slope < 0, don’t do anything`

      end;

      i := i - 1;

    end;

  end;

Derivative Function

`    `**procedure** **LOCAL\_HandleNonWindup**` (theStateOffset :  `**integer**` ; theDeriv, themax, themin :  `**double**`);`

`    `**var**`  local_s :  `**double**`;`

`    `**begin**

`    local_s := StateVector[theStateOffset];`

`      `**if**`  ( local_s >  themax)  `**then** `StateVector[theStateOffset] := themax;`

`      `**if**`  ( local_s <  themin)  `**then** `StateVector[theStateOffset] := themin;`

`    Derivative[theStateOffset] := theDeriv;`

`      `**if**`  ( local_s >= themax)  `**and**`  ( Derivative[theStateOffset] >  `**0**`  )  `**then**

**    ** ` Derivative[theStateOffset] :=  `**0**`;`

`      `**if**`  ( local_s <= themin)  `**and**`  ( Derivative[theStateOffset] <  `**0**`  )  `**then**

`       Derivative[theStateOffset] :=  `**0**`;`

`    `**end**`;`

**var**`  local_Pelec, `

    local\_Speed,

    local\_PropIn,

`    local_IntIn,`

`     local_SpeedError :  `**double**`;`

`     local_Deriv :  `**double**`;`

Begin

  local\_Pelec := PElec\*GenObject.MVABase/fTrate;

`    `**if**`  finvTsp <  `**0** **then**`  local_Speed := GenObject.GetBusFreqPU  ``// bus frequency`

`    `**else**`  local_Speed := actualWPU;  ``// rotor speed`

`    `**If**`  IgnoreStateVector[ `**1**` ]  `**Then** `StateVector[`**1**`] := local_Pelec;`

`    `**If**`  IgnoreStateVector[ `**2**` ]  `**Then** `StateVector[`**2**`] := local_Speed;`

`    `**If**`  IgnoreStateVector[ `**4**` ]  `**Then** `StateVector[`**4**`] := StateVector[`**1**` ] -  `**1.0**`;`

`  Derivative[`**2**` ] :=  ``abs``(finvTsp)*(local_Speed - StateVector[`**2**`]);`

`  Derivative[`**4**`] := finvTd*(StateVector[`**2**` ] -  `**1.0**`  - StateVector[ `**4**`]);`

`  local_SpeedError := cache_Spref - StateVector[`**2**` ] + GenObject.Paux/GetTRate;  ``// AAA 03/13/20`

`    `**if**`  fFD = 0  `**then** **begin**

`    Derivative[`**1**` ] :=  `**0**`;`

`      ``// proportional control DOES include gate droop when FD = 0`

    local\_PropIn := local\_SpeedError - fRg\*cache\_LastTimeStepGateCommand;

`    local_IntIn := local_PropIn;`

`    `**end**

`    `**else** **begin**

`    Derivative[`**1**`] := finvTpe*(local_Pelec - StateVector[`**1**`]);`

`      ``// proportional control DOES NOT include Pelec droop term when FD = 1`

    local\_PropIn := local\_SpeedError;

`    local_IntIn := local_SpeedError - fRe*StateVector[`**1**`];`

`    `**end**`;`

`    `**LOCAL\_HandleNonWindup**`(`**3**`, fKi*local_IntIn, fgmax - local_PropIn*fKp, fgmin - local_PropIn*fKp);`

`  cache_GateCommand := fKp*local_PropIn + StateVector[`**3**` ];  ``// proportional + Integrator`

`    ``// Derivative block effect`

`    `**If** **not** `IgnoreStateVector[`**4**` ]  `**Then** **begin**

`    cache_GateCommand := cache_GateCommand -`

`                         fKd*finvTd*(StateVector[`**2**` ] -  `**1.0**`  - StateVector[ `**4**`]);`

`    `**end**`;`

`    `**if**`  cache_GateCommand > fGmax  `**then**`  cache_GateCommand := fgmax; `

`    `**if**`  cache_GateCommand < fgmin  `**then**`  cache_GateCommand := fgmin; `

`  local_Deriv := fInvTg*( fKg *(cache_GateCommand - StateVector[`**6**`]) - StateVector[`**5**`] );`

** ** **LOCAL\_HandleNonWindup**`(`**5**`, local_Deriv, fvelm, -fvelm);`

** ** **LOCAL\_HandleNonWindup**`(`**6**`, StateVector[`**5**`], fgmax, fgmin);`

`    ``// gate buffer`

`    `**if**`  (StateVector[ `**6**` ] < fbuf)  `**AND**`  (Derivative[ `**6**` ] < -fbuv)  `**then** `Derivative[`**6**`] := -fbuv;`

`    ``// handle gate backlash`

`  cache_gv := StateVector[`**6**`];`

`    `**if**`  fBacklash_blg <>  `**nil** **then**`  cache_gv := fBacklash_blg.output( cache_gv ); `

  cache\_BC := fB\_GV.XtoY(cache\_GateCommand);

`    `**if**`  ( fInvtbd >  `**0**`  )  `**then** **begin**

`    local_Deriv := cache_BC - StateVector[`**7**`];`

`      `**if**`       ( local_Deriv >  fdbbd )  `**then**`  local_Deriv := local_Deriv - fdbbd `

`      `**else** **if**`  ( local_Deriv < -fdbbd )  `**then**`  local_Deriv := local_Deriv + fdbbd; `

`    Derivative[`**7**`] := finvTbd * local_Deriv;`

`    cache_bh := StateVector[`**7**`];`

`    `**end**

`    `**else** **begin**

`    StateVector[`**7**`] := cache_bc;`

`    Derivative[`**7**` ] :=  `**0**`;`

`      ``// note this won't always update the bh value!`

`      ``// That's fine, this is hysterisis.  It only moves once the deviation is large enough`

`      `**if**`  (cache_bc - fdbbd) > cache_bh  `**then**`  cache_bh := cache_bc - fdbbd; `

`      `**if**`  (cache_bc + fdbbd) < cache_bh  `**then**`  cache_bh := cache_bc + fdbbd; `

`    `**end**`;`

`    `**if**`  finvTbs >  `**0** **then** **begin**

`    local_Deriv := cache_bh - StateVector[`**78**`];`

`      `**if**`       ( local_Deriv >  fdbbs )  `**then**`  local_Deriv := local_Deriv - fdbbs `

`      `**else** **if**`  ( local_Deriv < -fdbbs )  `**then**`  local_Deriv := local_Deriv + fdbbs; `

    local\_Deriv := finvTbs \* local\_Deriv;

`      `**if**`       local_Deriv > +fblv  `**then**`  local_Deriv := +fblv `

`      `**else** **if**`  local_Deriv < -fblv  `**then**`  local_Deriv := -fblv; `

`    Derivative[`**8**`] := local_Deriv;`

`    `**end**

`    `**else** **begin**

`    StateVector[`**8**`] := cache_bh;`

`    Derivative[`**8**` ] :=  `**0**`;`

`    `**end**`;`

`  cache_bb := StateVector[`**8**`];`

`    `**if**`  fBacklash_blb <>  `**nil** **then**`  cache_bb := fBacklash_blb.output( cache_bb ); `

`  cache_ab := fbgvmin + (`**1**`  - fbgvmin)*cache_bb; `

  cache\_af := cache\_ab \* cache\_gv;

  // when cache\_af value input to water dynamics is an extremely small number,

  // the dynamics can become extremely fast because we divide by cache\_af.

  // Model starts entering a region we have have 0/0 as Q value also goes to zero.

  // Model these dynamics as algebraic and instantly change the state value to handle this.

  // Otherwise numerical problems related to 0/0 will result

`    `**if**`  cache_af <  `**0.005** **then** `StateVector[`**9**` ] :=  ``sqrt``(fHdam)*cache_af;`

  cache\_Hscroll := sqr(StateVector\[**9**\]/cache\_af);

  // Don’t allow the water flow to drop below 0.0001 per unit (more avoid 0/0 situations)

**LOCAL\_HandleNonWindup**`(`**9**` , finvTw*( fHdam - cache_hscroll ),  `**1E10**` ,  `**0.0001**`);`

**end**`;`

---

<a id="hrsgsimple"></a>

## HRSGSimple

*Source: [`Content/TransientModels_HTML/Governor HRSGSimple.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor HRSGSimple.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T \< 0.5\*Mult\*TimeStep then T = 0, ElseIf 0.5\*Mult\*TimeStep \< T \< Mult\*TimeStep then T = Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Pmech \> Pmax , then Pmax = Pmech or if Pmech \< Pmin , then Pmin = Pmech

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="hydro-bradley"></a>

## Hydro_Bradley

*Source: [`Content/TransientModels_HTML/Governor Bradley.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor Bradley.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - KPV\_1: Alpha can not be 0.0. Error will be created.
  - Alphad\_1: Beta can not be 0.0. Error will be created.
  - Alphan\_2: Gamma can not be 0.0. Error will be created.
  - To\_2: Gamma can not be 0.0. Error will be created.
  - Tc\_2: Gamma can not be 0.0. Error will be created.
  - Tdd\_1:If Tdd\_1\*Alphad\_1 \< 2\*TimeStep then Tdd\_1 = 2\*TimeStep.
  - Tdn\_1:If Tdn\_1\*Alphan\_2 \< 2\*TimeStep then Tdd\_1 = 2\*TimeStep.
  - Tdn\_1:If Tdn\_1\*Alphan\_2 \< 2\*TimeStep then Tdd\_1 = 2\*TimeStep.
  - TPV\_1:If TPV\_1/KPV\_1 \< 2\*TimeStep then Tdd\_1 = 2\*TimeStep.
  - If 0.0 \< Tf\_1 \< Mult\*TimeStep then Tf\_1 = Mult\*TimeStep
  - If 0.0 \< Tpe\_1\< Mult\*TimeStep then Tpe\_1= Mult\*TimeStep

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="hyg3"></a>

## HYG3

*Source: [`Content/TransientModels_HTML/Governor HYG3.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor HYG3.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If At \<= 0 then At = Mult\*TimeStep
  - If 0.0 \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If Pmax \< Pmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If GV \> Pmax , then Pmax = GV or if GV \< Pmin , then Pmin = GV

Model Equations and/or Block Diagrams  

![Governor HYG3 0001](images/Governor_HYG3_0001.svg)

**Parameters:**

|          |                                                     |
| -------- | --------------------------------------------------- |
| Trate    | Turbine rating, MW                                  |
| Pmax     | Maximum gate opening, pu of mwcap                   |
| Pmin     | Minimum gate opening, pu of mwcap                   |
| Cflag    | Governor control flag, 1=PID, -1=Double Derivative  |
| Rgate    | Steady-state droop, pu for governor output feedback |
| Relec    | Steady-state droop, pu, for electric power feedback |
| Td       | Input filter time constant, sec                     |
| Tf       | Filter time constant, sec                           |
| Tp       | Lead time constant, sec                             |
| Velopen  | Maximum gate opening velocity, pu/sec               |
| Velclose | Maximum gate closing velocity, pu/sec               |
| K1       | Double derivative gain, pu                          |
| K2       | Double derivative gain, pu, if Cflag = -1           |
| Ki       | Integral gain, pu                                   |
| Kg       | Gate servo gain, pu                                 |
| Tt       | Power feedback time constant, sec                   |
| db1      | Intentional deadband width, Hz                      |
| Eps      | Intentional db hysteresis, Hz                       |
| db2      | Unintentional deadband, MW                          |
| Tw       | Water inertia time constant, sec                    |
| At       | Turbine gain, pu                                    |
| Dturb    | Turbine damping coefficient, pu                     |
| Qnl      | No-load flow at nominal head, pu                    |
| H0       | Turbine nominal head, pu                            |
| Gv1      | Nonlinear gain point 1, pu gv                       |
| Pgv1     | Nonlinear gain point 1, pu power                    |
| Gv2      | Nonlinear gain point 2, pu gv                       |
| Pgv2     | Nonlinear gain point 2, pu power                    |
| Gv3      | Nonlinear gain point 3, pu gv                       |
| Pgv3     | Nonlinear gain point 3, pu power                    |
| Gv4      | Nonlinear gain point 4, pu gv                       |
| Pgv4     | Nonlinear gain point 4, pu power                    |
| Gv5      | Nonlinear gain point 5, pu gv                       |
| Pgv5     | Nonlinear gain point 5, pu power                    |
| Gv6      | Nonlinear gain point 6, pu gv                       |
| Pgv6     | Nonlinear gain point 6, pu power                    |

---

<a id="hygov"></a>

## HYGOV

*Source: [`Content/TransientModels_HTML/Governor HYGOV and HYGOVD.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor HYGOV and HYGOVD.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tf \< Mult\*TimeStep then Tf = Mult\*TimeStep
  - If 0.0 \< Tg \< Mult\*TimeStep then Tg = Mult\*TimeStep
  - If 0.0 \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If Gmax \< Gmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If GV \> Gmax , then Gmax = GV or if GV \< Gmin , then Gmin = GV

Model Equations and/or Block Diagrams

![Governor HYGOV 0001](images/Governor_HYGOV_0001.svg)

**Parameters for HYGOV:**

|        |                                    |
| ------ | ---------------------------------- |
| Trate  | Turbine rating, MW                 |
| Rperm  | Permanent droop, pu                |
| Rtemp  | Temporary droop, pu                |
| Tr     | Washout time constant, sec         |
| Tf     | Filter time constant, sec          |
| Tg     | Gate servo time constant, sec      |
| Velm   | Maximum gate velocity, pu/sec      |
| Gmax   | Maximum gate velocity, pu of mwcap |
| Gmin   | Minimum gate velocity, pu of mwcap |
| Tw     | Water inertia time constant, sec   |
| At     | Turbine gain, pu                   |
| Dturb  | Turbine damping coefficient, pu    |
| Qnl    | No-load flow at nominal head, pu   |
| Ttur   | Turbine trip flag                  |
| Tn     | Lag time constant, sec             |
| Tnp    | Lead time constant, sec            |
| db1    | Intentional deadband width, Hz     |
| Eps    | Intentional db hysteresis, Hz      |
| db2    | Unintentional deadband, MW         |
| Gv0    | Nonlinear gain point 0, pu gv      |
| Pgv0   | Nonlinear gain point 0, pu power   |
| Gv1    | Nonlinear gain point 1, pu gv      |
| Pgv1   | Nonlinear gain point 1, pu power   |
| Gv2    | Nonlinear gain point 2, pu gv      |
| Pgv2   | Nonlinear gain point 2, pu power   |
| Gv3    | Nonlinear gain point 3, pu gv      |
| Pgv3   | Nonlinear gain point 3, pu power   |
| Gv4    | Nonlinear gain point 4, pu gv      |
| Pgv4   | Nonlinear gain point 4, pu power   |
| Gv5    | Nonlinear gain point 5, pu gv      |
| Pgv5   | Nonlinear gain point 5, pu power   |
| Hdam   | Head available at dam, pu          |
| Bgv0   | Kaplan blade servo point 0, pu     |
| Bgv1   | Kaplan blade servo point 1, pu     |
| Bgv2   | Kaplan blade servo point 2, pu     |
| Bgv3   | Kaplan blade servo point 3, pu     |
| Bgv4   | Kaplan blade servo point 4, pu     |
| Bgv5   | Kaplan blade servo point 5, pu     |
| Bmax   | Maximum blade adjustment factor    |
| Tblade | Blade servo time constant, sec     |

**Parameters for HYGOVD:**

|       |                                    |
| ----- | ---------------------------------- |
| Rperm | Permanent droop, pu                |
| Rtemp | Temporary droop, pu                |
| Tr    | Washout time constant, sec         |
| Tf    | Filter time constant, sec          |
| Tg    | Gate servo time constant, sec      |
| Velm  | Maximum gate velocity, pu/sec      |
| Gmax  | Maximum gate velocity, pu of mwcap |
| Gmin  | Minimum gate velocity, pu of mwcap |
| Tw    | Water inertia time constant, sec   |
| At    | Turbine gain, pu                   |
| Dturb | Turbine damping coefficient, pu    |
| Qnl   | No-load flow at nominal head, pu   |
| dbH   | Deadband High (pu)                 |
| dbL   | Deadband Low (pu)                  |
| Trate | Turbine rating, MW                 |

---

<a id="hygov2"></a>

## HYGOV2

*Source: [`Content/TransientModels_HTML/Governor HYGOV2 and HYGOV2D.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor HYGOV2 and HYGOV2D.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< T3 \< Mult\*TimeStep then T3= Mult\*TimeStep
  - If 0.0 \< T4 \< Mult\*TimeStep then T4= Mult\*TimeStep
  - If 0.0 \< T6 \< Mult\*TimeStep then T6= Mult\*TimeStep
  - If 0.0 \< Tr \< Mult\*TimeStep then Tr= Mult\*TimeStep
  - If Vgmax \< 0 then change the sign to positive.
  - If Gmax \< Gmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Gate \> Pmax , then Pmax = Gate or if Gate \< Pmin , then Pmin = Gate

Model Equations and/or Block Diagrams

![Governor HYGOV2 0001](images/Governor_HYGOV2_0001.svg)

**Parameters for HYGOV2:**

|       |                                                |
| ----- | ---------------------------------------------- |
| Kp    | Proportional gain, pu                          |
| Ki    | Integral gain, pu                              |
| Ka    | Governor gain                                  |
| T1    | Governor mechanism time constant, sec          |
| T2    | Turbine power time constant, sec               |
| T3    | Turbine exhaust temperature time constant, sec |
| T4    | Governor lead time constant, sec               |
| T5    | Governor lag time constant, sec                |
| T6    | T, sec                                         |
| Tr    | Washout time constant, sec                     |
| Rtemp | Temporary droop, pu                            |
| R     | Permanent droop, pu                            |
| Vgmax | Model Parameters\\Vgmax                        |
| Gmax  | Maximum gate velocity, pu of mwcap             |
| Gmin  | Minimum gate velocity, pu of mwcap             |
| Pmax  | Maximum gate opening, pu of mwcap              |

**Parameters for HYGOV2D:**

|       |                                                |
| ----- | ---------------------------------------------- |
| Kp    | Proportional gain, pu                          |
| Ki    | Integral gain, pu                              |
| Ka    | Governor gain                                  |
| T1    | Governor mechanism time constant, sec          |
| T2    | Turbine power time constant, sec               |
| T3    | Turbine exhaust temperature time constant, sec |
| T4    | Governor lead time constant, sec               |
| T5    | Governor lag time constant, sec                |
| T6    | T, sec                                         |
| Tr    | Washout time constant, sec                     |
| Rtemp | Temporary droop, pu                            |
| R     | Permanent droop, pu                            |
| Vgmax | Model Parameters\\Vgmax                        |
| Gmax  | Maximum gate velocity, pu of mwcap             |
| Gmin  | Minimum gate velocity, pu of mwcap             |
| Pmax  | Maximum gate opening, pu of mwcap              |
| dbH   | Deadband High (pu)                             |
| dbL   | Deadband Low (pu)                              |
| Trate | Turbine rating, MW                             |

---

<a id="hygov4"></a>

## HYGOV4

*Source: [`Content/TransientModels_HTML/Governor HYGOV4.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor HYGOV4.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If 0.0 \< Tr \< Mult\*TimeStep then Tr = Mult\*TimeStep
  - If 0.0 \< Tg \< Mult\*TimeStep then Tg = Mult\*TimeStep
  - If 0.0 \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If Pmax \< Pmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If Gate \> Pmax , then Pmax = Gate or if Gate \< Pmin , then Pmin = Gate

Model Equations and/or Block Diagrams

![Governor HYGOV4 0001](images/Governor_HYGOV4_0001.svg)

**Parameters:**

|        |                                                                              |
| ------ | ---------------------------------------------------------------------------- |
| Trate  | Turbine rating, MW                                                           |
| Tg     | Gate servo time constant, sec                                                |
| Tp     | Lead time constant, sec                                                      |
| Uo     | Maximum valve opening velocity, pu/sec                                       |
| Uc     | Maximum valve closing velocity, pu/sec                                       |
| Pmax   | Maximum gate opening, pu of mwcap                                            |
| Pmin   | Minimum gate opening, pu of mwcap                                            |
| Rperm  | Permanent droop, pu                                                          |
| Rtemp  | Temporary droop, pu                                                          |
| Tr     | Washout time constant, sec                                                   |
| Tw     | Water inertia time constant, sec                                             |
| At     | Turbine gain, pu                                                             |
| Dturb  | Turbine damping coefficient, pu                                              |
| Hdam   | Head available at dam, pu                                                    |
| Qnl    | No-load flow at nominal head, pu                                             |
| db1    | Intentional deadband width, Hz                                               |
| Eps    | Intentional db hysteresis, Hz                                                |
| db2    | Unintentional deadband, MW                                                   |
| Gv0    | Nonlinear gain point 0, pu gv                                                |
| Pgv0   | Nonlinear gain point 0, pu power                                             |
| Gv1    | Nonlinear gain point 1, pu gv                                                |
| Pgv1   | Nonlinear gain point 1, pu power                                             |
| Gv2    | Nonlinear gain point 2, pu gv                                                |
| Pgv2   | Nonlinear gain point 2, pu power                                             |
| Gv3    | Nonlinear gain point 3, pu gv                                                |
| Pgv3   | Nonlinear gain point 3, pu power                                             |
| Gv4    | Nonlinear gain point 4, pu gv                                                |
| Pgv4   | Nonlinear gain point 4, pu power                                             |
| Gv5    | Nonlinear gain point 5, pu gv                                                |
| Pgv5   | Nonlinear gain point 5, pu power                                             |
| Hdam1  | Head available at dam, pu. If \> 0 this overrides the first one in the list. |
| Bgv0   | Kaplan blade servo point 0, pu                                               |
| Bgv1   | Kaplan blade servo point 1, pu                                               |
| Bgv2   | Kaplan blade servo point 2, pu                                               |
| Bgv3   | Kaplan blade servo point 3, pu                                               |
| Bgv4   | Kaplan blade servo point 4, pu                                               |
| Bgv5   | Kaplan blade servo point 5, pu                                               |
| Bmax   | Maximum blade adjustment factor                                              |
| Tblade | Blade servo time constant, sec                                               |

---

<a id="hygovr"></a>

## HYGOVR

*Source: [`Content/TransientModels_HTML/Governor HYGOVR.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/Governor HYGOVR.htm)*

**AutoCorrection Properties**

Following checks and corrections are applied during Validation and AutoCorrection.

  - If At \<= 0 then At = Mult\*TimeStep
  - If 0.0 \< Tt \< 0.5\*Mult\*TimeStep then Tt = 0, ElseIf 0.5\*Mult\*TimeStep \< Tt \< Mult\*TimeStep then Tt = Mult\*TimeStep
  - If 0.0 \< Tp \< 0.5\*Mult\*TimeStep then Tp = 0, ElseIf 0.5\*Mult\*TimeStep \< Tp \< Mult\*TimeStep then Tp = Mult\*TimeStep
  - If 0.0 \< Tw \< Mult\*TimeStep then Tw = Mult\*TimeStep
  - If Gmax \< Gmin then swap the values.

Mult represents the user-specified value **Minimum time constant size as multiple of time step** option on the [Validation page of the Transient Stability Dialog](37-transient-stability-analysis-dialog-part3.md#validation)

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Following treatment is handled during the transient numerical simulation

  - If GV \> Gmax , then Gmax = GV or if GV \< Gmin , then Gmin = GV

Model Equations and/or Block Diagrams

   ![Governor HYGOVR 0001](images/Governor_HYGOVR_0001.svg)

**Parameters:**

|          |                                                |
| -------- | ---------------------------------------------- |
| Trate    | Turbine rating, MW                             |
| Pmax     | Maximum gate opening, pu of mwcap              |
| Pmin     | Minimum gate opening, pu of mwcap              |
| R        | Permanent droop, pu                            |
| Td       | Input filter time constant, sec                |
| T1       | Governor mechanism time constant, sec          |
| T2       | Turbine power time constant, sec               |
| T3       | Turbine exhaust temperature time constant, sec |
| T4       | Governor lead time constant, sec               |
| T5       | Governor lag time constant, sec                |
| T6       | T, sec                                         |
| T7       | T, sec                                         |
| T8       | T, sec                                         |
| Tp       | Lead time constant, sec                        |
| Velopen  | Maximum gate opening velocity, pu/sec          |
| Velclose | Maximum gate closing velocity, pu/sec          |
| Ki       | Integral gain, pu                              |
| Kg       | Gate servo gain, pu                            |
| Gmax     | Maximum gate velocity, pu of mwcap             |
| Gmin     | Minimum gate velocity, pu of mwcap             |
| Tt       | Power feedback time constant, sec              |
| db1      | Intentional deadband width, Hz                 |
| Eps      | Intentional db hysteresis, Hz                  |
| db2      | Unintentional deadband, MW                     |
| Tw       | Water inertia time constant, sec               |
| At       | Turbine gain, pu                               |
| Dturb    | Turbine damping coefficient, pu                |
| Qnl      | No-load flow at nominal head, pu               |
| H0       | Turbine nominal head, pu                       |
| Gv1      | Nonlinear gain point 1, pu gv                  |
| Pgv1     | Nonlinear gain point 1, pu power               |
| Gv2      | Nonlinear gain point 2, pu gv                  |
| Pgv2     | Nonlinear gain point 2, pu power               |
| Gv3      | Nonlinear gain point 3, pu gv                  |
| Pgv3     | Nonlinear gain point 3, pu power               |
| Gv4      | Nonlinear gain point 4, pu gv                  |
| Pgv4     | Nonlinear gain point 4, pu power               |
| Gv5      | Nonlinear gain point 5, pu gv                  |
| Pgv5     | Nonlinear gain point 5, pu power               |
| Gv6      | Nonlinear gain point 6, pu gv                  |
| Pgv6     | Nonlinear gain point 6, pu power               |
