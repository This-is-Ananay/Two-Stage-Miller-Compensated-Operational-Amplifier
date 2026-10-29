# Two-Stage-Miller-Compensated-Operational-Amplifier
All the derivations can be found in textbook by P. Allen and D. Holberg,"CMOS Analog Circuit Design", The Oxford Series in Electrical and Computer Engineering.


## DESIGN SPECIFICATION OF OPAMP
Gain= 60db
Slew rate = 20 V/uS
GBW (Gain Bandwidth) = 30 MHz
ICMR(+)= 1.6 V
ICMR(-)= 800 mV
Vdc = 1.8 V
Cl (Load Capacitance) = 2pF

## CIRCUIT DIAGRAM
The circuit of opamp which includes all the differntial pair and current mirror made using the nmos2v and pmos2v from the 90nm (gpdk90) library.

<p align="center">
  <img src="images/1_Schematics.jpeg" width="48%">
  <img src="images/18.jpeg" width="48%">
</p>

## DESIGN 
### Design of input transistor M1 and M2 
The design process is 90nm so L>= 2Lmin , thus L=500nm is used for the design.

![M1 and M2 design calculations](images/design_m1_m2.jpeg)

### Finding Minimum and maximum Threshold value
After designing M1 and M2 the circuit arrangement is used to find the threshold limits.

Now for for M3 and M4 the threshold can be obtained from the circuit. Note until now they are not designed so assume a suitable W/L ratio and take a margin of safety in threshold value obtained.

![Threshold calculations](images/design_m1_m2.jpeg)

### Design of mirror load (M3 and M4) and tail current source transistor (M5 and M8)

![M3, M4, M5, M8 design calculations](images/designbd.jpeg)

### Design of second stage input transistor M6 

![M6 design calculations](images/design_m1_m2.jpeg)

### Design of current source transistor for second stage M7

![M7 design calculations](images/design_m1_m2.jpeg)

### Deciding values of compensation capacitor (Cc) and bias current (I)
We have target Slew rate and given Load capacitor CL in the specification. We also have the target of Phase margin > 60 degree. The condition for 60 degree phase margin is Cc>=0.22xCL Hence, for our project Cc should be more than or equal to 2.2pF. So initially choosing Cc = 800fF. Now, Slew Rate = I5 / Cc so I5 (I) = SR x Cc = 20μA.

## Re-Design
After the initial design and DC analysis the obtained DC operating points are used to calculate the gain.

![M7 design calculations](images/design_m1_m2.jpeg)

In both cases the obtained gain is lesser then the desired target. So will increase the "Length" keeping same W/L ratios to obtain a higher gain and simultaneously will adjust Cc value to get phase margin closer to 60 degree. The length is increased from 500um to 1000um and Cc = 850fF to meet the specifications. For precise tunning we can further change length and Cc accordingly but this is a rough estimation with no length related constraints. All this is monitored and measured using the AC analysis by plotting gain and phase margin plot.

The final Gain and Phase margin plots for different common mode voltages are:

<p align="center">
  <img src="images/5_AC_1p6V.jpeg" width="48%">
  <img src="images/6_AC_0p8V.jpeg" width="48%">
</p>

Furthermore we can also calculate further design parameters.

## COMMON MODE REJECTION RATIO (CMRR)

![M7 design calculations](images/design_m1_m2.jpeg)

## SLEW RATE 

<p align="center">
  <img src="images/5_AC_1p6V.jpeg" width="48%">
  <img src="images/6_AC_0p8V.jpeg" width="48%">
</p>

## POWER DISSIPATION

![M7 design calculations](images/design_m1_m2.jpeg)









