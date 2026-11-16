
### Figure 8. Comparison of Active power losses for different conditions

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_47_0.png)

### Figure 9. Comparison of real power generation cost for different conditions

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_47_1.png)

bus 26 nodal voltage magnitude at 1 p.u. From the Figure 10 it is observed that by incorporating UPFC in BAT algorithm based optimal Power flow calculations voltage profile has been improved. By placing the UPFC between bus no 25 and bus no 26 its voltage at bus no 26 has been increased from 0.8159 p.u to 1 p.u. Table 14 represents the total Active power losses when the bus no 26 is loaded. From the table it is observed that losses are increased by increasing load. From the Figure 11 it is observed that by placing the UPFC in BAT algorithm based optimal power flow the losses are less. Similarly from Figure 12 it is observed that by placing the UPFC in BAT algorithm based optimal power flow real power generation cost is less and by increasing the load at particular bus real power generation cost is also increased.

### Table 13. Comparison of bus VOLTAGES FOR 30-bus system using BAT OPF without and with UPFC

| Bus No. | Newton-Raphson Method | DE-OPF with UPFC(UPFC placed between bus 25 and bus 26) | BAT-OPF with UPFC(UPFC placed between bus 25 and bus 26) | CSA-OPF with UPFC(UPFC placed between bus 25 and bus 26) | FA-OPF with UPFC(UPFC placed between bus 25 and bus 26) |
|---|---|---|---|---|---|
| | Voltage magnitude (volts) | Voltage magnitude (volts) | Voltage magnitude (volts) | Voltage magnitude (volts) | Voltage magnitude (volts) |
| 1 | 1.0600 | 1.06 | 1.06 | 1.06 | 1.06 |
| 2 | 1.0430 | 1.0430 | 1.0430 | 1.0430 | 1.0430 |
| 3 | 0.9568 | 0.9641 | 0.9660 | 0.95660 | 0.9710 |
| 4 | 0.9756 | 0.9836 | 0.9869 | 0.9989 | 0.9962 |
| 5 | 1.01 | 1.0100 | 1.0100 | 1.0100 | 1.01 |
| 6 | 1.008 | 1.0118 | 1.0142 | 1.012 | 1.01 |
| 7 | 0.9967 | 0.9985 | 0.9997 | 0.997 | 0.999 |
| 8 | 1.01 | 1.0100 | 1.0100 | 1.0100 | 1.0100 |
| 9 | 0.9536 | 0.9637 | 0.9697 | 0.9978 | 0.9789 |
| 10 | 0.893 | 0.9045 | 0.9199 | 0.9099 | 0.9389 |
| 11 | 1.082 | 1.0820 | 1.0820 | 1.0820 | 1.0820 |
| 12 | 0.9179 | 0.9288 | 0.9396 | 0.9299 | 0.9468 |
| 13 | 1.071 | 1.0710 | 1.0710 | 1.0710 | 1.0710 |
| 14 | 0.8588 | 0.8707 | 0.8872 | 0.8842 | 0.8986 |
| 15 | 0.8521 | 0.8641 | 0.8851 | 0.8765 | 0.8982 |
| 16 | 0.8803 | 0.8920 | 0.9049 | 0.9095 | 0.9493 |
| 17 | 0.87 | 0.8821 | 0.8966 | 0.8912 | 0.8999 |
| 18 | 0.8207 | 0.8335 | 0.8544 | 0.8444 | 0.8964 |
| 19 | 0.8136 | 0.8267 | 0.8468 | 0.8348 | 0.8685 |
| 20 | 0.8374 | 0.8501 | 0.8682 | 0.8620 | 0.8827 |
| 21 | 0.8599 | 0.8717 | 0.8943 | 0.8848 | 0.8993 |
| 22 | 0.8529 | 0.8644 | 0.8933 | 0.8736 | 0.8993 |
| 23 | 0.8298 | 0.8415 | 0.8764 | 0.8664 | 0.8974 |
| 24 | 0.8349 | 0.8455 | 0.8927 | 0.8887 | 0.8978 |
| 25 | 0.8532 | 0.8610 | 0.9360 | 0.9160 | 0.9603 |
| 26 | 0.8075 | 1.0000 | 1.0000 | 1.0000 | 1.0000 |
| 27 | 0.9449 | 0.9480 | 0.9720 | 0.9567 | 0.9956 |
| 28 | 0.9824 | 0.9847 | 0.9934 | 0.9899 | 0.9974 |
| 29 | 0.9617 | 0.9633 | 0.9755 | 0.9711 | 0.9877 |
| 30 | 0.95 | 0.963 | 0.972 | 0.9700 | 0.9889 |
| 31 | ---- | 0.9562 | 0.9678 | 0.9469 | 0.9789 |

### Figure 10. Comparison of Voltage Profile with and without UPFC

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_49_0.png)

### Table 14. Total Active Power Losses comparison with bus 26 loaded

| S No | Bus 26 Loaded (Load in MW) | Active Power losses in MW (DE OPF with UPFC placed between bus 25 and bus 26) | Active Power losses in MW (BAT OPF with UPFC placed between bus 25 and bus 26) | Active Power losses in MW (CSA OPF with UPFC placed between bus 25 and bus 26) | Active Power losses in MW (FA OPF with UPFC placed between bus 25 and bus 26) |
|---|---|---|---|---|---|
| 1 | 10 | 22.123 | 20.9837 | 21.0972 | 20.3217 |
| 2 | 20 | 24.692 | 22.2221 | 23.234 | 21.6546 |
| 3 | 30 | 28.654 | 27.4585 | 28.4298 | 26.9856 |
| 4 | 40 | 32.996 | 31.6879 | 32.8691 | 30.8978 |
| 5 | 50 | 39.578 | 37.6059 | 38.9562 | 36.9746 |

## FUTURE RESEARCH DIRECTIONS

A combination of these optimization techniques as hybrid optimization techniques can be implemented for future work and better results. In this chapter power system performance has been enhanced by using single FACTS device that is UPFC only. It can be implemented with multi type FACTS devices for future work and better performance. Here optimization planning is done for static environment. For future work this can be a challenging topic for planning for dynamic environment.

## CONCLUSION

In this chapter, Meta heuristic optimization algorithms have been implemented to solve multi objective optimal power flow problem in the presence of Unified power flow controller. The results demonstrate the effectiveness and robustness of the proposed methods with Unified power flow controller. The results obtained for 5 bus test system and modified IEEE 30 bus system using the proposed methods without and with UPFC are compared and observations reveal that the losses are less with UPFC. In 5 bus test system UPFC is placed between bus 3 and bus 4 and in modified IEEE 30 bus system UPFC is placed between bus 25 and bus 26 the simulation results were taken and it was observed that the active power losses has been decreased because of generation reallocation. Simulation results show that UPFC device in the test systems can further minimize total real power generation cost and real power loss. BAT algorithm, CSA and firefly algorithm based optimal power flow with UPFC gives less total generation cost and real power losses as compared to differential evolution algorithm based optimal power flow. While comparing BAT algorithm, cuckoo search algorithm and firefly algorithm, cuckoo search algorithm is simple in implementation, BAT algorithm gives accurate and efficient results, firefly algorithm has robust, high convergence rate and gives best optimal solution in less number of iterations.

## REFERENCES

Acha, E., Fuerte-Esquivel, C., Ambriz-Perez, H., & Angeles, C. (2004). FACTS: Modelling and Simulation in Power Networks. John Wiley & Sons; doi:10.1002/0470020164

Ambriz-Perez, Acha, Fuerte-Esquivel, & De la Torre. (1998). Incorporation of a UPFC model in an Optimal Power Flow Using Newton's method. IEEE Proc.-Generation Transmission Distribution, 145(3).

Aparna, R. R. (2016). Swarm Intelligence for Automatic Video Image Contrast Adjustment. International Journal of Rough Sets and Data Analysis, 3(3), 21–37. doi:10.4018/IJRSDA.2016070102

Ashour, A. S., Samanta, S., Dey, N., Kausar, N., Abdessalemkaraa, W. B., & Hassanien, A. E. (2015). Computed tomography image enhancement using cuckoo search: A log transform based approach. Journal of Signal and Information Processing, 6(03), 244–257. doi:10.4236/jsip.2015.63023

Binh, H. T. T., Hanh, N. T., & Dey, N. (2016). Improved Cuckoo Search and Chaotic Flower Pollination optimization algorithm for maximizing area coverage in Wireless Sensor Networks. *Neural Computing & Applications*, 1–13.

Carpentier. (1979). Optimal Power Flows. *Electrical Power and Energy Systems*, *1*, 959-972.

Chung, T. S., & Li, Y. Z. (2001). A hybrid CA approach for OPF with consideration of FACTS devices. *IEEE Power Engineering Review*, *21*(2), 47–50. doi:10.1109/39.896822

Dey, N., Ashour, A. S., Beagum, S., Pistola, D. S., Gospodinov, M., Gospodinova, E. P., & Tavares, J. M. R. (2015). Parameter optimization for local polynomial approximation based intersection confidence interval filter using genetic algorithm: An application for brain MRI image de-noising. *Journal of Imaging*, *1*(1), 60–84. doi:10.3390/jimaging1010060

Dey, N., Chakraborty, S., & Samanta, S. (2014). Optimization of watermarking in biomedical signal. Lambert Publication. Heinrich-Böcking-Straße, 6, 66121.

Dey, N., Samanta, S., Chakraborty, S., Das, A., Chaudhuri, S. S., & Suri, J. S. (2014). Firefly algorithm for optimization of scaling factors during embedding of manifold medical information: An application in ophthalmology imaging. *Journal of Medical Imaging and Health Informatics*, *4*(3), 384–394. doi:10.1166/jmihi.2014.1265

Dey, N., Samanta, S., Yang, X. S., Das, A., & Chaudhuri, S. S. (2013). Optimisation of scaling factors in electrocardiogram signal watermarking using cuckoo search. *International Journal of Bio-inspired Computation*, *5*(5), 315–326. doi:10.1504/IJBIC.2013.057193

Dutta, S. (2016). Optimal Allocation of Static Synchronous. Academic Press.

Dutta, S., Roy, P. K., & Nandi, D. (2016). Series Compensator Controllers using Chemical Reaction Optimization for Reactive Power Dispatch. *International Journal of Energy Optimization and Engineering*, *5*(3), 43–62. doi:10.4018/IJEOE.2016070103

Edris, A. (2000, March). FACTS Technology Development: An Update. *IEEE Power Engineering Review*.

Goel, S., Sharma, A., & Panchal, V. K. (2014). Multiobjective Cuckoo Search for Anticipating the Enemy's Movements in the Battleground. *International Journal of Applied Metaheuristic Computing*, *5*(4), 26–46. doi:10.4018/ijamc.2014100102
