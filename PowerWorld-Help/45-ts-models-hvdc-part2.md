---
title: "TS Models — HVDC (Part 2 of 2)"
part: "Transient Models"
chapter_file: "45-ts-models-hvdc-part2.md"
topics: 4
source: "https://www.powerworld.com/WebHelp/"
generated: "2026-09-18"
---

# TS Models — HVDC (Part 2 of 2)

HVDC and VSC DC line dynamic models.

> Part of the offline PowerWorld Simulator help repository. See [`00-INDEX.md`](00-INDEX.md) for the full topic index and [`00-MAP.md`](00-MAP.md) for the structure map.

**Topics in this file (4)**

- [VHVDC_A1](#vhvdc-a1)
- [VHVDC1](#vhvdc1)
- [VHVDC2](#vhvdc2)
- [VSCDT](#vscdt)

---

<a id="vhvdc-a1"></a>

## VHVDC_A1

*Source: [`Content/TransientModels_HTML/VSC DC Line VHVDC_A1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/VSC DC Line VHVDC_A1.htm)*

Model added in the June 22, 2026 patch of Simulator 24. Beta versions had been available in the 2 months before this, but users should have the June 22, 2026 patch or later to properly use this model)

September 8, 2026 patch of Simulator 24 included support for allowing Ldc = 0 in the DC circuit equation.

Model Equations and/or Block Diagrams   

![VSCDC VHVDC A1 0001](images/VSCDC_VHVDC_A1_0001.svg)

![VSCDC VHVDC A1 0002](images/VSCDC_VHVDC_A1_0002.svg)

![VSCDC VHVDC A1 0003](images/VSCDC_VHVDC_A1_0003.svg)

![VSCDC VHVDC A1 0004](images/VSCDC_VHVDC_A1_0004.svg)

![VSCDC VHVDC A1 0005](images/VSCDC_VHVDC_A1_0005.svg)

**Object Parameters:**

<table>
<tbody>
<tr class="odd">
<td><p>MeasBus1</p></td>
<td><p>OtherObject:0</p></td>
<td><p>Measurement Bus 1. This is the terminal bus of the Measurement Branch 1 at which Qac1, Pac1, Vac1 and Theta1 are measured. Note that the parameter MeasFlag1 determines whether the flow is measured into or out of the branch.</p></td>
</tr>
<tr class="even">
<td><p>MeasBranch1</p></td>
<td><p>OtherObject:1</p></td>
<td><p>Measurement Branch 1. Branch on which Qac1 and Pac1 are measured.</p>
<p>This branch should be in series with the VSCDCLine on the SideBus1 side of the VSCDCLine, but does not have to be directly connected to the terminal SideBus1.</p></td>
</tr>
<tr class="odd">
<td><p>MeasBus2</p></td>
<td><p>OtherObject:2</p></td>
<td><p>Measurement Bus 2. This is the terminal bus of the Measurement Branch 2 at which Qac2, Pac2, Vac2 and Theta2 are measured. Note that the parameter MeasFlag2 determines whether the flow is measured into or out of the branch.</p></td>
</tr>
<tr class="even">
<td><p>MeasBranch2</p></td>
<td><p>OtherObject:3</p></td>
<td><p>Measurement Branch 2. Branch on which Qac2 and Pac2 are measured.</p>
<p>This branch should be in series with the VSCDCLine on the SideBus2 side of the VSCDCLine, but does not have to be directly connected to the terminal SideBus2.</p></td>
</tr>
</tbody>
</table>

**Parameters taken from the Power Flow Data input for VSCDCLine objects:**

|            |                                                                                                              |
| ---------- | ------------------------------------------------------------------------------------------------------------ |
| Rdc        | Resistance in Ohms of the DC Line used in the DC Line Model                                                  |
| ACMVABase1 | For converter at the Side1Bus, Maximum AC MVA which is used as the ACMVABase for the converter dynamic model |
| Aloss1     | For converter at the Side1Bus, Constant term of the converter loss function \[kW\]                           |
| Bloss1     | For converter at the Side1Bus, Linear term of the converter loss function \[MW per kA\] or \[kW per Amp\]    |
| Pminloss1  | For converter at the Side1Bus, Minimum loss of the converter \[kW\]                                          |
| ACMVABase2 | For converter at the Side2Bus, Maximum AC MVA which is used as the ACMVABase for the converter dynamic model |
| Aloss2     | For converter at the Side2Bus, Constant term of the converter loss function \[kW\]                           |
| Bloss2     | For converter at the Side2Bus, Linear term of the converter loss function \[MW per kA\] or \[kW per Amp\]    |
| Pminloss2  | For converter at the Side2Bus, Minimum loss of the converter \[kW\]                                          |

**Integer Parameter Flags:**

<table>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p>OpMode</p></td>
<td><p>0=Interconnection; 1=Islanded operation (for example an off-shore wind farm) (default = 0)</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p>Qmode1Flag</p></td>
<td><p>Side-1 Q control mode: 0=Q; 1=QV; 2=PF (default = 0)</p></td>
</tr>
<tr class="odd">
<td><p>2</p></td>
<td><p>Qmode2Flag</p></td>
<td><p>Side-2 Q control mode: 0=Q; 1=QV; 2=PF (default = 0)</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>MeasFlag1</p></td>
<td><p>0 indicate that positive flow for MeasBranch1 is leaving MeasBus1 going out to the line.</p>
<p>1 indicate that positive flow for MeasBranch1 is arriving at MeasBus1 coming in from the line.</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>MeasFlag2</p></td>
<td><p>0 indicate that positive flow for MeasBranch2 is leaving MeasBu2s going out to the line.</p>
<p>1 indicate that positive flow for MeasBranch2 is arriving at MeasBus2 coming in from the line.</p></td>
</tr>
</tbody>
</table>

**Float Parameters:**

Parameter values are not auto-corrected for the VHVDC\_A1, but instead internally the model may modify what value is used for the input parameter based on the integration time step. The integration time step in the notes below is denoted as ΔT.

Part of Model

Parameter

Treatment in Numerical Simulation

Description

Default

Network

Interface

0

TPLLsync

If \<2\*ΔT use 0

If \<4\*ΔT use 4\*ΔT

PLL synchronization time constant for both Side 1 and Side 2 \[seconds\]

0.05

1

R1a

Side 1 arm resistance in per unit on Side 1 ACMVABase

0.10

2

X1a

Side 1 arm resistance in per unit on Side 1 ACMVABase

0.10

DC Line Model

3

Vdcrated

Rated DC voltage of the converters \[kV\]

525.0

4

Ldc

If \<0 Use 0

DC line total inductance \[milli Henry\]

129.3

5

Cdc

If \<0 Use 0

DC line total capacitance \[micro Farad\]

140.5

6

C1

If \<5 Use 5

Equivalence Capacitance of Side 1 converter \[micro Farad\]

221.7

7

C2

If \<5 Use 5

Equivalence Capacitance of Side 2 converter \[micro Farad\]

221.7

Main Converter

Control

on Side 1 for

Interconnection

Applications

8

Kxfmr1ratio

Side 1, AC transformer off-nominal ratio

1.00

9

Tvac1f2

If \<4\*ΔT use 0

Side 1, Second AC voltage filter time constant \[s\]

0.02

10

TId1f

If \<4\*ΔT use 4\*ΔT

Side 1, Id filter time constant (\>0) \[s\]

0.02

11

Tvf1long

If \<4\*ΔT use 0

Side 1, AC voltage filter long time constant \[s\]

60.0

12

Tuq1

If \<4\*ΔT use 4\*ΔT

Side 1, Integral time of Iq controller (\>0) \[s\]

10.0

13

DIq1ctrlmax

Use +(absolute value)

Side 1, Maximum Delta Iq control limit \[pu\]

0.3

14

Iq1ctrlmax

Use +(absolute value)

Side 1, Maximum Iq control limit \[pu\]

0.35

15

Iq1max

Side 1, Maximum Iq limit \[pu\]

1.1

16

Kvac1dyn

Side 1, Vac error gain during faults

1.0

17

dbVac1dyn

Use +(absolute value)

Side 1, Deadband Uac error in faults \[pu\]

0.1

18

dVac1th1

Use +(absolute value)

Side 1, First high AC voltage error threshold \[pu\]

0.1

19

Tdrop11

Side 1, First delay of high AC voltage error \[s\]

0.01

20

dbVdc1

Side 1, Deadband of DC voltage error \[pu\]

0.01

21

KVdc1dyn

Side 1, Feedforward Vdc gain

6.0

22

KpVdc1

Side 1, Gain of Proportional control of DC PI controller

4.0

23

KiVdc1

Side 1, Gain of Integral control of DC PI controller (\>=0. Zero allowed.) \[1/s\]

0.05

24

DId1ctrlmax

Use +(absolute value)

Side 1, Maximum Delta Id control limit \[pu\]

0.3

25

Id1refrateup

Use +(absolute value)

Side 1, Id limit ramp-up rate \[pu/s\]. Up is defined as away from zero,  
therefore this is used in negative ramp direction for Id1min.

9.0

26

Id1refratedown

Use -(absolute value)

Side 1, Id limit ramp-down rate \[pu/s\]. Down is defined as towards zero,  
therefore this is used in positive ramp direction for Id1min.

\-9999

Reactive Power

Control

on Side 1 for

Interconnection

Applications

27

TVac1

If \<4\*ΔT use 0

Side 1, Q Control Vac filter time constant \[s\]

0.02

28

TP1

If \<4\*ΔT use 0

Side 1, Q Control P filter time constant \[s\]

0.5

29

Tpf1order

If \<4\*ΔT use 0

Side 1, Smoothing time constant of PF order \[s\]

1.0

30

dbVac1

Use +(absolute value)

Side 1, Deadband QV control \[pu\]

0.0

31

DVac1max

Side 1, Maximum AC voltage error in Q-V control \[pu\]

0.2

32

Kiu1

Side 1, Proportional gain QV control \[pu\]

20.0

33

Kdroop1

Side 1, Inverse droop in deltaV/deltaQ \[pu\]

0.1

34

dVac1th2

Use +(absolute value)

Side 1, Second high AC voltage error threshold \[pu\]

0.18

35

Tdrop12

Side 1, Second delay of high AC voltage error \[s\]

0.15

36

pf1min

Side 1, Minimum PF value

0.9

37

pf1max

Side 1, Maximum PF value

1.0

38

Qac1max

Side 1, Maximum reactive power \[pu\]

0.33

39

Qac1min

Side 1, Minimum reactive power \[pu\]

\-0.33

40

Qac1refrateup

Use +(absolute value)

Side 1, Reactive power setpoint ramp-rate upper limit \[pu/s\]

9999

41

Qac1refratedown

Use +(absolute value)

Side 1, Reactive power setpoint ramp-rate lower limit \[pu/s\]

\-9999

Id1max vs Vac1

Lookup Table

for Side 1 in

Interconnection

applications

(When X value is less than previous, the remainder of curve is ignored)

42

Ic1max

If \<= 0 then ignore limit

Side 1, Maximum Total Current \[pu\]

1.1

43

Tvac1f1

If \<4\*ΔT use 0

Side 1, First AC voltage filter time constant \[s\]

0.04

44

Vac1X1

Side 1, X1 for Id1max vs Vac1 lookup table

0.0

45

Id1maxY1AC

Side 1, Y1 for Id1max vs Vac1 lookup table

0.2

46

Vac1X2

Side 1, X2 for Id1max vs Vac1 lookup table

0.5

47

Id1maxY2AC

Side 1, Y2 for Id1max vs Vac1 lookup table

0.2

48

Vac1X3

Side 1, X3 for Id1max vs Vac1 lookup table

0.85

49

Id1maxY3AC

Side 1, Y3 for Id1max vs Vac1 lookup table

1.1

50

Vac1X4

Side 1, X4 for Id1max vs Vac1 lookup table

2.0

51

Id1maxY4AC

Side 1, Y4 for Id1max vs Vac1 lookup table

1.1

52

Vac1X5

Side 1, X5 for Id1max vs Vac1 lookup table

2.1

53

Id1maxY5AC

Side 1, Y5 for Id1max vs Vac1 lookup table

1.1

54

Vac1X6

Side 1, X6 for Id1max vs Vac1 lookup table

2.2

55

Id1maxY6AC

Side 1, Y6 for Id1max vs Vac1 lookup table

1.1

Main Converter

Control

on Side 1 in

Islanded

Applications

56

TVac1f3

If \<4\*ΔT use 0

Side 1, Third AC voltage filter time constant \[s\]

0.0001

57

KpVac1w

Side 1, Proportional gain voltage controller \[pu\]

4.0

58

KiVac1w

Side 1, Integral gain of voltage controller (\>= 0. Zero allowed) \[1/s\]

2.0

59

Iq1ctrlmaxw

Side 1, Maximum Iq in Vac control \[pu\]

0.3

60

KVac1fw

Side 1, Feed-forward gain in Vac control \[pu\]

3

61

Iq1maxw

Side 1, Maximum current Iq \[pu\]

1.1

62

TIq1fw

If \<4\*ΔT use 0

Side 1, Time constant of filter iq \[s\]

0.02

63

KpIac1w

Side 1, Proportional gain of current controller \[pu\]

0.25

64

KiIac1w

Side 1, Integral gain of current controller (\> 0. Zero not allowed) \[1/s\]

2.0

65

Vc1minw

Side 1, Minimum limit of offshore converter voltage \[pu\]

\-0.1

66

Vc1maxw

Side 1, Maximum limit of offshore converter voltage \[pu\]

1.3

DC Chopper

67

Vdc2CHon

DC Chopper, activation threshold voltage \[pu\]

1.035

68

KVdc2CH

Use -(absolute value)

DC Chopper, Proportional gain control (\<= 0) \[pu\]

\-20.0

69

TVdc2CH

If \<4\*ΔT use 4\*ΔT

DC Chopper, Integrator time constant control (\>0) \[s\]

0.025

70

Idc2CHmax

DC Chopper, Maximum current \[pu\]

1.4

71

KIdc2CH

If \< 1 use 1

DC Chopper, Proportional gain of current control \[pu\]

0.9

72

TIdc2CH

If \<4\*ΔT use 4\*ΔT

DC Chopper, Integrator time constant of current control \[s\]

0.15

73

InomCH

DC Chopper, nominal current \[kA\]

1.8

74

ECHmax

DC Chopper, Maximum energy \[MJ\]

2142.2

Main Converter

Control

on Side 2

75

Kxfmr2ratio

Side 2, AC transformer off-nominal ratio

1.00

76

Tvac2f2

If \<4\*ΔT use 0

Side 2, Second AC voltage filter time constant \[s\]

0.02

77

TId2f

If \<4\*ΔT use 4\*ΔT

Side 2, Id filter time constant (\>0) \[s\]

0.02

78

Tvf2long

If \<4\*ΔT use 0

Side 2, AC voltage filter long time constant \[s\]

60.0

79

Tuq2

If \<4\*ΔT use 4\*ΔT

Side 2, Integral time of iq controller (\>0) \[s\]

10.0

80

DIq2ctrlmax

Use +(absolute value)

Side 2, Maximum Delta Iq control limit \[pu\]

0.3

81

Iq2ctrlmax

Use +(absolute value)

Side 2, Maximum Iq control limit \[pu\]

0.35

82

Iq2max

Side 2, Maximum Iq limit \[pu\]

1.1

83

Kvac2dyn

Side 2, Vac error gain during faults

1.0

84

dbVac2dyn

Use +(absolute value)

Side 2, Deadband Uac error in faults \[pu\]

0.1

85

dVac2th1

Use +(absolute value)

Side 2, First high AC voltage error threshold \[pu\]

0.1

86

Tdrop21

Side 2, First delay of high AC voltage error \[s\]

0.01

87

dbVdc2

Side 2, Deadband of DC voltage error \[pu\]

0.01

88

KVdc2dyn

Side 2, Feedforward Vdc gain

6.0

89

KpVdc2

Side 2, Gain of Proportional control of DC PI controller

4.0

90

KiVdc2

Side 2, Gain of Integral control of DC PI controller (\>=0. Zero allowed.) \[1/s\]

0.05

91

DId2ctrlmax

Use +(absolute value)

Side 2, Maximum Delta Id control limit \[pu\]

0.3

92

Id2refrateup

Use +(absolute value)

Side 2, Id limit ramp-up rate \[pu/s\]. Up is defined as away from zero,  
therefore this is used in negative ramp direction for Id2min.

9.0

93

Id2refratedown

Use -(absolute value)

Side 2, Id limit ramp-down rate \[pu/s\]. Down is defined as towards zero,  
therefore this is used in positive ramp direction for Id2min.

\-9999

94

Tpac2

If \<4\*ΔT use 4\*ΔT

Side 2, Integral time of active power controller (\>0) \[s\]

20.0

95

Pac2refrateup

Use +(absolute value)

Side 2, Upper limit of active power setpoint ramp-rate \[pu/s\]

9999

96

Pac2refratedown

Use -(absolute value)

Side 2, Lower limit of active power setpoint ramp-rate \[pu/s\]

\-9999

Reactive Power

Control

on Side 2

97

TVac2

If \<4\*ΔT use 0

Side 2, QControl Vac filter time constant \[s\]

0.02

98

TP2

If \<4\*ΔT use 0

Side 2, QControl P filter time constant \[s\]

0.50

99

Tpf2order

If \<4\*ΔT use 0

Side 2, Smoothing time constant of PF order \[s\]

1.00

100

dbVac2

Use +(absolute value)

Side 2, Deadband QV control \[pu\]

0.00

101

DVac2max

Side 2, Maximum AC voltage error in Q-V control \[pu\]

0.20

102

Kiu2

Side 2, Proportional gain QV control \[pu\]

20.0

103

Kdroop2

Side 2, Inverse droop in deltaV/deltaQ \[pu\]

0.10

104

dVac2th2

Use +(absolute value)

Side 2, Second high AC voltage error threshold \[pu\]

0.18

105

Tdrop22

Side 2, Second delay of high AC voltage error \[s\]

0.15

106

pf2min

Side 2, Minimum PF value

0.90

107

pf2max

Side 2, Maximum PF value

1.00

108

Qac2max

Side 2, Maximum reactive power \[pu\]

0.33

109

Qac2min

Side 2, Minimum reactive power \[pu\]

\-0.33

110

Qac2refrateup

Use +(absolute value)

Side 2, Reactive power setpoint ramp-rate upper limit \[pu/s\]

9999

111

Qac2refratedown

Use +(absolute value)

Side 2, Reactive power setpoint ramp-rate lower limit \[pu/s\]

\-9999

Id2max vs Vac2

Lookup Table

for Side 2

(When X value is less than previous, the remainder of curve is ignored)

112

Ic2max

If \<= 0 then ignore limit

Side 2, Maximum Total Current \[pu\]

1.1

113

Tvac2f1

If \<4\*ΔT use 0

Side 2, First AC voltage filter time constant \[s\]

0.04

114

Vac2X1

Side 2, X1 for Id1max vs Vac1 lookup table

0.00

115

Id2maxY1AC

Side 2, Y1 for Id2max vs Vac2 lookup table

0.20

116

Vac2X2

Side 2, X2 for Id1max vs Vac1 lookup table

0.50

117

Id2maxY2AC

Side 2, Y2 for Id2max vs Vac2 lookup table

0.20

118

Vac2X3

Side 2, X3 for Id2max vs Vac2 lookup table

0.85

119

Id2maxY3AC

Side 2, Y3 for Id2max vs Vac2 lookup table

1.05

120

Vac2X4

Side 2, X4 for Id2max vs Vac2 lookup table

2.00

121

Id2maxY4AC

Side 2, Y4 for Id2max vs Vac2 lookup table

1.05

122

Vac2X5

Side 2, X5 for Id2max vs Vac2 lookup table

2.10

123

Id2maxY5AC

Side 2, Y5 for Id2max vs Vac2 lookup table

1.05

124

Vac2X6

Side 2, X6 for Id2max vs Vac2 lookup table

2.20

125

Id2maxY6AC

Side 2, Y6 for Id2max vs Vac2 lookup table

1.05

Id2min vs Vdc2

Lookup Table

for Side 2

126

Vdc2X1min

Side 2, X1 for Id2min vs Vdc2 lookup table

1.05

127

Id2minY1DC

Side 2, Y1 for Id2min vs Vdc2 lookup table

\-1.00

128

Vdc2X2min

Side 2, X2 for Id2min vs Vdc2 lookup table

1.10

129

Id2minY2DC

Side 2, Y2 for Id2min vs Vdc2 lookup table

0.00

Id2max vs Vdc2

Lookup Table

for Side 2

130

Vdc2X1max

Side 2, X1 for Id2max vs Vdc2 lookup table

0.90

131

Id2maxY1DC

Side 2, Y1 for Id2max vs Vdc2 lookup table

0.00

132

Vdc2X2max

Side 2, X2 for Id2max vs Vdc2 lookup table

0.96

133

Id2maxY2DC

Side 2, Y2 for Id2max vs Vdc2 lookup table

1.10

![VSCDC VHVDC A1 0006](images/VSCDC_VHVDC_A1_0006.svg)

![VSCDC VHVDC A1 0007](images/VSCDC_VHVDC_A1_0007.svg)

![VSCDC VHVDC A1 0008](images/VSCDC_VHVDC_A1_0008.svg)

![VSCDC VHVDC A1 0009](images/VSCDC_VHVDC_A1_0009.svg)

---

<a id="vhvdc1"></a>

## VHVDC1

*Source: [`Content/TransientModels_HTML/VSC DC Line VHVDC1.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/VSC DC Line VHVDC1.htm)*

Added support for this model in Version 21, build on November 20, 2020

**AutoCorrection Properties**

Following corrections are applied when initializing this model in Transient Stability for the parameters Tr, Tp, Tq

  - If 0.0 \< T \< 2\*TimeStep then T = 0, ElseIf 2\*TimeStep \< T \< 4\*TimeStep then T = 4\*TimeStep

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="vhvdc2"></a>

## VHVDC2

*Source: [`Content/TransientModels_HTML/VSC DC Line VHVDC2.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/VSC DC Line VHVDC2.htm)*

Added support for this model in Version 24, build on April 28, 2025

**AutoCorrection Properties**

Following corrections are applied when initializing this model in Transient Stability for the parameters Tr, Tp, Tq

  - If 0.0 \< T \< 2\*TimeStep then T = 0, ElseIf 2\*TimeStep \< T \< 4\*TimeStep then T = 4\*TimeStep

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams   View in fullscreen

---

<a id="vscdt"></a>

## VSCDT

*Source: [`Content/TransientModels_HTML/VSC DC Line VSCDT.htm`](https://www.powerworld.com/WebHelp/Content/TransientModels_HTML/VSC DC Line VSCDT.htm)*

Added support for this model in Version 21, build on November 20, 2020

**AutoCorrection Properties**

Following corrections are applied when initializing this model in Transient Stability for the parameters Tpo1, Tpo2, Tacm1, Tacm2, TpoDCL

  - If 0.0 \< T \< 2\*TimeStep then T = 0, ElseIf 2\*TimeStep \< T \< 4\*TimeStep then T = 4\*TimeStep

Following corrections are applied when initializing this model in Transient Stability for the parameters Tac1, Tac2, Tpolim

  - If 0 \< T \< 4\*TimeStep then T = 4\*TimeStep

TimeStep represents the integration time step being used as described on [TimeStep](37-transient-stability-analysis-dialog-part1.md#simulation)

Model Equations and/or Block Diagrams   View in fullscreen
