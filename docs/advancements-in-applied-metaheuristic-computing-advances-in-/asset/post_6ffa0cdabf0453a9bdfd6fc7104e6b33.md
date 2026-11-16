
## Table 4. Input parameters of differential evaluation

| S.No | Parameters | Quantity |
| :--- | :--- | :--- |
| 1 | Population size | 20 |
| 2 | Number of generations | 50 |
| 3 | DE-step size | 0.8 |
| 4 | Crossover probability constant | 0.8 |

Initially, the optimal power flow solution i.e. active power generation cost and power loss for 5-bus system are calculated using proposed BAT algorithm, cuckoo search algorithm and firefly algorithm method without UPFC. Next, for the same system the optimal power flow solution is obtained using proposed BAT algorithm, cuckoo search algorithm and firefly algorithm method with UPFC. The results obtained with BAT algorithm, cuckoo search algorithm and firefly algorithm are compared with Differential evaluation. The active power generation cost and power loss for 5 bus test system without UPFC is shown in Table 5 and Table 6 represents the same as above with UPFC. From Table 5 and 6, it can be seen that total active power generation required is reduced to 150.0192 MW from 151.3557 MW and power loss has been reduced to 5.0192 MW from 6.3557 MW because of UPFC. Further, it is observed that there is a significant reduction in the cost because of UPFC. From Table 7, it is clear that the voltage profiles has been improved for most of buses because of UPFC and The UPFC shunt converter is set to regulate bus 3 nodal voltage magnitude at 1 p.u.

From the Figure 5 it is observed that by incorporating UPFC in Power flow calculations voltage profile has been improved. By placing the UPFC between bus no 3 and bus no 4 its voltage at bus no 3 has been increased from 0.9519 to 1 p.u. From the Table 8 it is observed that the active power losses are 5.0192 MW when the UPFC is placed between bus no 3 and bus no 4 which is the less as compared

## Table 5. Comparison in case of OPF without UPFC

| Variables | DE-OPF | BAT-OPF | CSA-OPF | FA-OPF |
| :--- | :--- | :--- | :--- | :--- |
| PG1(MW) | 139.0764 | 109.1800 | 91.0192 | 57.5634 |
| PG2(MW) | 12.8518 | 42.1757 | 60.00 | 93.4171 |
| Total real power generation(MW) | 151.9282 | 151.3557 | 151.0192 | 150.9805 |
| Total real power generation cost ($/hr) | 1893.3 | 1726.4 | 1769.3 | 1689.8 |
| Total real power Loss (MW) | 6.9282 | 6.3557 | 6.0192 | 5.9805 |

## Table 6. Comparison in case of OPF with UPFC

| Variables | DE-OPF | BAT-OPF | CSA-OPF | FA-OPF |
| :--- | :--- | :--- | :--- | :--- |
| PG1(MW) | 133.8120 | 90.0192 | 60.456 | 62.5170 |
| PG2(MW) | 16.8338 | 60.0000 | 89.6312 | 88.3601 |
| UPFC(p.u.) VcR VvR | 0.0400 1.0759 | 0.0370 1.0436 | 0.038 1.042 | 0.029 1.012 |
| UPFC θcr (angle in degrees) θvr | -87.1236 -15.2311 | -86.1393 -12.3421 | -86.9576 -13.1258 | -85.456 -10.632 |
| Total real power generation(MW) | 150.6458 | 150.0192 | 150.0872 | 149.8771 |
| Total real power generation cost ($/hr) | 1814.804 | 1684.3 | 1688.71 | 1672.56 |
| Total real power Loss (MW) | 5.6458 | 5.0192 | 5.0872 | 4.8771 |

## Table 7. Comparison of bus voltages and its angles for 5 bus system using Bat OPF without and with UPFC

| Bus No. | DE-OPF with UPFC Voltage magnitude (volts) | DE-OPF with UPFC Voltage angle (rad) | BAT-OPF with UPFC Voltage magnitude (volts) | BAT-OPF with UPFC Voltage angle (rad) | CSA-OPF with UPFC Voltage magnitude (volts) | CSA-OPF with UPFC Voltage angle (rad) | FA-OPF with UPFC Voltage magnitude (volts) | FA-OPF with UPFC Voltage angle (rad) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 1.06 | 0 | 1.06 | 0 | 1.0600 | 0 | 1.0600 | 0 |
| 2 | 1 | -0.83 | 1 | -0.74 | 1.0000 | -2.0356 | 1.0000 | -1.0356 |
| 3 | 1 | -3.32 | 1 | -4.21 | 1.0000 | -4.6213 | 1 | -3.6213 |
| 4 | 0.9536 | -3.67 | 0.9753 | -3.59 | 0.9720 | -3.3370 | 0.9863 | -4.3370 |
| 5 | 0.9622 | -4.52 | 0.9806 | -4.37 | 0.9786 | -5.6541 | 0.9929 | -4.2555 |
| UPFC Node | 0.9785 | -4.567 | 0.9806 | -3.17 | 0.9689 | -4.5254 | 0.995 | -3.0524 |

to UPFC placed in other locations. Figure 6 indicates that real power losses are less when the UPFC placed between bus no. 3 and bus no.4. Comparison of real power generation cost after incorporation of UPFC at different locations in BAT algorithm based optimal power flow shown in Fig.7.

## For 30 Bus System

In modified IEEE 30 bus system bus no 1 is consider as a slack bus and bus no’s 2,5,8,11,13 are consider as a PV buses all other buses are consider as PQ buses.

## Figure 5. Comparison of voltage profile with and without UPFC

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_43_0.png)

## Table 8. Incorporation of UPFC in OPF with bat Algorithm in 5 different locations

| UPFC Placed Between Bus No | Total Real Power Generation (MW) | Total Load (MW) | Total Real Power Loss (MW) |
|---|---|---|---|
| 2-3 | 150.663 | 145 | 5.663 |
| 2-4 | 150.9119 | 145 | 5.9119 |
| 2-5 | 151.3845 | 145 | 6.3845 |
| 3-4 | 150.0192 | 145 | 5.0192 |
| 4-5 | 150.8784 | 145 | 5.8784 |

## Table 9. Incorporation of UPFC in OPF with cuckoo search Algorithm in 5 different locations

| UPFC Placed Between Bus No | Total Real Power Generation (MW) | Total Load (MW) | Total Real Power Loss (MW) |
|---|---|---|---|
| 2-3 | 150.7829 | 145 | 5.7829 |
| 2-4 | 150.9829 | 145 | 5.9829 |
| 2-5 | 151.8653 | 145 | 6.8653 |
| 3-4 | 150.0872 | 145 | 5.0872 |
| 4-5 | 150.9489 | 145 | 5.9489 |

## Table 10. Incorporation of UPFC in OPF with firefly Algorithm in 5 Different Locations

| UPFC placed between Bus No | Total real power generation (MW) | Total load (MW) | Total real power loss (MW) |
|---|---|---|---|
| 2-3 | 150.4531 | 145 | 5.4531 |
| 2-4 | 150.0123 | 145 | 5.0123 |
| 2-5 | 150.8562 | 145 | 5.8562 |
| 3-4 | 149.8771 | 145 | 4.8771 |
| 4-5 | 150.4854 | 145 | 5.4854 |

## Figure 6. Incorporation of UPFC at different locations in Optimal Power Flow with BAT Algorithm

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_44_0.png)

This system has 24 load buses with 41 interconnected lines. By simulating the optimal power flow with BAT algorithm in MATLAB it is observed that voltage magnitude at bus no 26 is 0.8159 p.u which is less as compared to other buses. So for the purpose of improve the voltage profile at that bus it is required to place the UPFC between bus no 25 and bus no 26. To include a unified power flow controller an additional node 31 placed in between bus no 25 and bus no 26 in the network. It maintains the active and reactive powers leaving the UPFC towards the bus 25. The UPFC shunt converter is set to regulate bus 26 nodal voltage magnitude at 1 p.u. similarly simulating the optimal power flow with cuckoo search algorithm and firefly algorithm in MATLAB it is observed that voltage magnitude at bus no 26 is less as compared to other buses. So for the purpose of improve the voltage profile at that bus it is required to place the shunt converter of UPFC at that bus. A MATLAB program is implemented for the test system. Twenty runs have been performed for the test system. The optimal solution results over these twenty runs have been tabulated.

## Figure 7. Comparison of real power generation cost after incorporation of UPFC at different locations in BAT-OPF.

Real power generation cost in ($/h)

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_45_0.png)

## Table 11. Comparison in case of OPF without UPFC

| Variables | DE-OPF | BAT-OPF | CSA-OPF | FA-OPF |
|---|---|---|---|---|
| PG1(MW) | 169 | 170.1571 | 170.6130 | 173.8325 |
| PG2(MW) | 48.2537 | 50 | 50.3422 | 49.8952 |
| PG5(MW) | 19 | 25.2113 | 21.960 | 22.6231 |
| PG8(MW) | 30.5948 | 19.1717 | 24.1619 | 22.0648 |
| PG11(MW) | 15.4692 | 16 | 13.8316 | 11.5357 |
| PG13(MW) | 12 | 12.0396 | 13.1734 | 12.0871 |
| Total real power generation(MW) | 294.3177 | 292.5795 | 294.0821 | 292.0384 |
| Total real power generation cost ($/hr) | 810.5345 | 804.0134 | 808.4652 | 800.0942 |
| Total real power Loss (MW) | 10.9177 | 9.1795 | 10.6821 | 8.64 |

## Table 12. Comparison in case of OPF with UPFC

| Variables | DE-OPF | BAT-OPF | CSA-OPF | FA-OPF |
| :--- | :--- | :--- | :--- | :--- |
| PG1(MW) | 166.722 | 175.4891 | 174.6537 | 205.7251 |
| PG2(MW) | 50.2537 | 46.9756 | 49.9251 | 31.8026 |
| PG5(MW) | 16 | 21.2113 | 22.0305 | 17.0127 |
| PG8(MW) | 28.7395 | 20.1717 | 21.6118 | 11.8741 |
| PG11(MW) | 17.4692 | 13.5542 | 11.8879 | 10.2405 |
| PG13(MW) | 12 | 12.0396 | 12.0 | 12.7050 |
| UPFC(p.u.) VCr V<sub>R</sub> | 0.0540<br>1.0545 | 0.0410<br>1.0368 | 0.11<br>1.0176 | 0.0945<br>1.0176 |
| UPFC θ<sub>cr</sub> (angle in degrees) θ<sub>VR</sub> | -92.4571<br>-14.3387 | -104.178<br>-10.3848 | -98.5673<br>-12.856 | -87.515<br>-11.649 |
| Total real power generation(MW) | 291.1849 | 289.4415 | 292.109 | 289.36 |
| Total real power generation cost ($/hr) | 801.7493 | 794.5704 | 799.9800 | 793.162 |
| Total real power Loss (MW) | 7.7849 | 6.0415 | 8.7090 | 5.96 |

The total real power generation, total real power generation cost and real power loss for modified IEEE 30 bus system are obtained with BAT algorithm, cuckoo search algorithm, firefly algorithm and differential evaluation considering without and with UPFC are shown in Table 11 and Table 12. From Table 11 and 12, it can be seen that total active power generation required is reduced to 289.4415 MW from 292.5795 MW and power loss has been reduced to 6.0415 MW from 9.1795 MW because of UPFC with BAT algorithm. By incorporating UPFC in cuckoo search algorithm losses has been reduced to 8.709MW from 10.68MW, in firefly algorithm losses are reduced to 5.96MW from 8.64MW, which indicates that latest firefly algorithm gives better results compared to all other optimization algorithms.

Further, it is observed that there is a significant reduction in the cost because of UPFC. From the Figure 8 it is observed that active power losses are reduced to 6.0415MW from 10.9177MW by placing the UPFC in BAT algorithm based optimal power flow. Figure 9 indicates the real power generation cost is less in BAT-OPF as compared to DE-OPF. From Table 12 it can be observed that Firefly algorithm gives better results when compare to other optimization algorithms in OPF problem with UPFC on the modified IEEE 30 bus test system.

Table 13 represents the bus voltage of the network without UPFC and with UPFC. From Table 13, it is clear that the voltage profiles has been improved for most of buses because of UPFC and The UPFC shunt converter is set to regulate
