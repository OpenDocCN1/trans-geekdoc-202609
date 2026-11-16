# Figure 1. Model of open loop 3-area transfer function with SMES

![](bbox=[0.142, 0.133, 0.853, 0.469])

is very important that is fed to the connected plants. The generated control signal from PID controller is given by:

$u_1(t) = -K_{p1}ACE_1 - K_{i1}\int ACE_1 dt - T_d K_{d1}\frac{d}{dt}ACE_1$ (1)

$u_2(t) = -K_{p2}ACE_2 - K_{i2}\int ACE_2 dt - T_d K_{d2}\frac{d}{dt}ACE_2$ (2)

$u_3(t) = -K_{p3}ACE_3 - K_{i3}\int ACE_3 dt - T_d K_{d3}\frac{d}{dt}ACE_3$ (3)

The area control error (ACE) that generated in area 1, area 2 and area 3 is given by:

$ACE_1=\Delta F_1 . B_1 + \Delta P_{tie_{12}}$ (4)