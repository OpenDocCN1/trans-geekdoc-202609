
In the current algorithm, mating is selected randomly as one of the evolutionary procedures. Two parent species are selected randomly from the breeding pool, their genetic material is exchanged, and two more progeny are produced as part of the cross-over procedure. This procedure can provide valuable insights into the parents’ genetic composition, potentially enhancing their progeny quality. Mutation is a process by which genetic material on chromosomes is altered. This occurs when a mutation site is arbitrarily selected from the chromosomes of one species from a population.

### Poor individual is replaced.

In order to accomplish the objective of evolution, which is to obtain the best alternative, the less advantageous population members will also undergo cross-over and modified species after mutation and cross-over processes conclude.

## Results

The `ADVISOR` software enables the simulation of research to enhance fuel economy, vehicle performance, and exhaust emissions by manipulating various control plan parameters. By these standards, the parameters and model of the vehicle’s components for a parallel `HEV` have been established. [Table 6.1](#ch6.xhtml#tab6_1) below showing the vehicle parameters taken for the analysis

[Table 6.1 Table showing vehicle parameters for the analysis](#ch6.xhtml#R_tab6_1)

| Parameter || Value |
| --- | --- |
| Vehicle mass || 590 Kg |
| --- | --- |
| Cargo mass || 130 Kg |
| Frontal area(vehicle) || 2.5 m2 |
| Aerodynamic drag coefficient || 0.330 |
| Energy storage system || VRLA (12V,26Ah) |
| Rolling resistance coefficient || 0.007 |
| Fuel converter || 45 KW SI Engine |
| Electric motor || 75 KW AC motor |

### Algorithm Parameters and the Control Strategy Description

The algorithm has different parameters that need to be adjusted, which include iterations, mutation rate, crossover rate, and population size (5 and 10 used here). Around 1100 iterations have been done, and the rate of mutation and cross-over is set to 0.2 and 1, respectively. `EUDC` cycle is taken to simulate the default parallel hybrid electric vehicle on the `ADVISOR` for this optimal strategy. Random variables are selected from the solution’s whole space to initialize the algorithm’s population. In [Table 6.2](#ch6.xhtml#tab6_2), all the parameters used in this strategy are detailed based on the simulation of the `EUDC` cycle.

[Table 6.2 Table showing control strategy parameters for different population size](#ch6.xhtml#R_tab6_2)

| Control Strategy Parameters |
| --- |
| Parameter || Population Size |
|  || 5 || 10 |
| `Max. SOC` || 0.95 || 0.74 |
| --- | --- | --- |
| `Min. SOC` || 0.03 || 0.18 |
| `ELS_H` || 53.0 || 26.0 |
| `ELS_L` || 4.0 || 7.0 |
| `T_min` || 0.23 || 0.69 |
| `T_ch` || 24.3 || 10.5 |
| `T_off` || 0.27 || 0.38 |

In [Figures 6.2](#ch6.xhtml#fig6_2) and [6.3](#ch6.xhtml#fig6_3), the process history is shown for the `EUDC` cycle, and it is observed that along with the iterations, the fitness value is improved for different population sizes. These parameters can be selected optimally using the multi-objective algorithm used in this work.

![Figure 6.2 Figure Showing Optimization History for population size 10](images/fig6_2_B.jpg)

[Figure 6.2 Figure Showing Optimization History for population size 10](#ch6.xhtml#R_fig6_2)

![Figure 6.3 Figure Showing Optimization History for population size 5](images/fig6_3_B.jpg)

[Figure 6.3 Figure Showing Optimization History for population size 5](#ch6.xhtml#R_fig6_3)

The results show that different control strategies have different emission and fuel economy specifications, and a better selection of these parameters will help improve fuel economy. The control strategy parameters are affected by the population size of the strategy.

[Table 6.3](#ch6.xhtml#tab6_3) presents the driving cycle's fuel economy and emissions in detail, and the vehicle's performance for the drive cycle is also shown.

[Table 6.3 Table showing emission parameters and the dynamic performance of the vehicle](#ch6.xhtml#R_tab6_3)

| Parameter || Size-5 || Size-10 |
| --- | --- | --- |
| `FC and Emissions` ||  ||  |
| --- | --- | --- |
| CO || 5.563 || 3.754 |
| NOx || 0.546 || 0.648 |
| HC || 0.618 || 0.664 |
| FC || 31.550 || 31.667 |
| `Vehicle Dynamic Performance` ||  ||  |
| 0-60mph || 10.248 || 10.641 |
| 40-60 mph || 5.323 || 5.568 |
| 0-85 mph || 21.8116 || 22.821 |
| Max. speed || 111.402 || 109.829 |
| Max. acceleration || 16.238 || 16.238 |
| Distance || 173.803 || 171.559 |
| Gradability || 6.6 || 6.6 |

## Conclusion

A challenge for optimizing the Electric Assist Strategy on the `UDDS` driving cycle was formulated to achieve the minimum gasoline consumption and emissions possible without compromising vehicle performance. Appropriate control strategy configurations can be generated using the `MO Algo` with one thousand iterations and two moderate population sizes (five and ten). The ideal values for the control approach were ascertained by employing two lesser populations, each consisting of 5, 10, and 1000 iterations. Without compromising vehicle performance, this research enhances engine efficiency and emissions to combat pollution and the energy crisis. The analysis results indicate that by optimizing fuel efficiency and reducing emissions, `MA` can be utilized to improve the parameters of the control strategy. This method of operating efficiently scans the vehicle without compromising its performance. `MA` can increase the control strategy parameters in parallel `HEV`s, which can aid in mitigating the energy crisis and climate risks, as opposed to the parallel `HEV`s predefined in `ADVISOR`, according to the results.

## References

1. [Wu, Y., Zhang, S., Hao, J., Liu, H., Wu, X., Hu, J., et al.](#ch6.xhtml#R_ref6_1) (2017). On-road vehicle emissions and their control in China: a review and outlook. Science of the Total Environment, 574, 332–349.

2. [Lin, C.-C., Peng, H., and Grizzle, J. W.](#ch6.xhtml#R_ref6_2) (2004). A stochastic control strategy for hybrid electric vehicles. In Proceedings of the 2004 American Control Conference, (Vol. 5, pp. 4710–4715). IEEE, 2004.

3. [Saraswat, M., and Chauhan, N. R.](#ch6.xhtml#R_ref6_3) (2020). Comparative assessment of butanol and algae oil as alternate fuel for SI engines. Engineering Science and Technology, an International Journal, 23(1), 92–100.

4. [Paganelli, G., Guezennec, Y., and Rizzoni, G.](#ch6.xhtml#R_ref6_4) (2002). Optimizing control strategy for hybrid fuel cell vehicle. SAE Transactions, 398–406.

5. [Kumar, P., Singh, P. K., Nagar, S., Sharma, K., and Saraswat, M.](#ch6.xhtml#R_ref6_5) (2021). Effect of different concentration of functionalized graphene on charging time reduction in thermal energy storage system. Materials Today: Proceedings, 44, 146–152.

6. [Pisu, P. and Rizzoni, G.](#ch6.xhtml#R_ref6_6) (2007). A comparative study of supervisory control strategies for hybrid electric vehicles. IEEE Transactions on Control Systems Technology, 15(3), 506–518.

7. [Singh, P. K., Sharma, K., Kumar, A., and Shukla, M.](#ch6.xhtml#R_ref6_7) (2017). Effects of functionalization on the mechanical properties of multiwalled carbon nanotubes: a molecular dynamics approach. Journal of Composite Materials, 51(5), 671–680.

8. [Yi, T., Xin, Z., Liang, Z., and Xin, Z.](#ch6.xhtml#R_ref6_8) (2011). Fuzzy control strategy for hybrid electric vehicle based on neural network identification of driving conditions. Control Theory and Applications, 28(3), 363–369.

9. [Verma, S. K., Sharma, K., Gupta, N. K., Soni, P., and Upadhyay, N.](#ch6.xhtml#R_ref6_9) (2020). Performance comparison of innovative spiral-shaped solar collector design with conventional flat plate solar collector. Energy, 194, 116853.
