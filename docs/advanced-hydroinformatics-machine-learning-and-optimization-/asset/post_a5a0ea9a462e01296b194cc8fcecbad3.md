
![](img/dd2f1e467aed0a84f984e6e656b2cc0f_92_0.png)

Figure 3.4 Multi-objective optimization procedure of the benchmark test in the (a) fifth, (b) tenth, and (c) fifteenth iterations.

But there are large deviations between the FNPs and their validated values. In the tenth and fifteenth iterations, the deviations between the FNPs and their validated values decrease. As shown in Figure 3.4b and c, the FNPs and their validated values are all in the crucial ranges but the validated values of FNPs in the tenth iteration are closer to the split line of BIAS_LX and BIAS_QZ. It is interesting that the deviation in the fifteenth iteration is slightly larger than the one in the tenth iteration. This phenomenon is caused by the marginal error of ANN when the simulated objectives are reached to the bounds. It does not usually happen when calibrating the model in an actual basin, for NSE seldom gets to 1 and Bias to 0. Therefore, it is thought that the results shown in Figure 3.4 are reasonable and interpretable.

The trace plots of the seven calibrated parameters versus the benchmark values in the fifteenth iteration are shown in Figure 3.5. It is clearly shown that the parameters converge to the benchmarks. In the end, the nondominated solutions are very close to the benchmark values we set. As shown in Table 3.3, the relative errors of D2, D3, b_inf, Ds, and v given by SM are less than 10%, where the value of v has the largest relative error of 5.71%. Meanwhile, the relative error of Wsmax is 11.13%, which is larger than the other parameters but less than the 10% of the optimal scope (0 to 30). This parameter set is also validated in the VIC model whose objective functions are 0.9996, 0.0001, 0.9995, and 0.0009 for NSE_LX, BIAS_LX, NSE_QZ, and BIAS_QZ, respectively.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_93_0.png)

Figure 3.5 Trace plots of the seven calibrated parameters. The All population dots are the variable parameters for the nondominated population and the Non-dominated population dots are the variable parameters for all the population in the fifteenth optimization. The Benchmark lines are the artificial benchmarks.

## 3.5.2. Pareto Solutions of the Surrogate Model in Two Study Areas

In order to choose the crucial ranges of NSE and Bias, the multi-objective optimization program was operated for 20 generations and then the crucial ranges were selected according to the ranges of the population. The ε-NSGA II was operated to select crucial ranges for the four optimization objectives. In each generation, the values of population were counted. In Figure 3.6a, the ranges of NSE are decreasing with the

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_94_0.png)

Figure 3.6 Population values with the increasing generations of (a) NSE at LX, (b) Bias at LX, (c) NSE at QZ, and (d) Bias at QZ in the LJR basin; the boxplots contain the medians (middle lines), the outliers (plus signs), the 25% and 75% quantiles (the edges of the box), and most extreme data points (whiskers).

Increasing iterations. At first, the range of NSE is from around 0.6 to around 0.8; then the ranges decrease gradually and the medians increase gradually; after the number of iterations reaches the value of 8, the ranges of population become stable in a relatively small range from about 0.8 to 0.9. Similar results are shown in Figure 3.6b–d and Figure 3.7.

With the results of Figure 3.6 and Figure 3.7, the crucial ranges of the objective function at each station in each basin are defined. The crucial ranges in the LJR basin and the XJR basin are shown in Table 3.4.

Since a stochastic algorithm is used, the calibration results (objective value and parameter set) vary when multiple calibration runs are performed. It is necessary that independent runs of calibration using SM be repeated. In this study, the calibration using SM was run 10 times in each study area. The obtained optimal points given by SM, the corresponding validating points, and the Pareto fronts estimated with ε-NSGA II in the LJR basin and the XJR basin are shown in Figure 3.8

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_95_0.png)

Figure 3.7 Population values with the increasing generations of (a) NSE at HY, (b) Bias at HY, (c) NSE at XT, and (d) Bias at XT in the XJR basin; the boxplots contain the medians (middle lines), the outliers (plus signs), the 25% and 75% quantiles (the edges of the box) and most extreme data points (whiskers).

**Table 3.4** Crucial ranges of *NSE* and *Bias* in each gauge station.

| Gauge station | Crucial ranges: *NSE* | Crucial ranges: *Bias* |
|---|---:|---:|
| Lanxi | 0.85–1 | 0–0.1 |
| Quzhou | 0.8–1 | 0–0.1 |
| Xiangtan | 0.7–1 | 0–0.15 |
| Hengyang | 0.7–1 | 0–0.15 |

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_96_0.png)

**Figure 3.8** Two-dimensional Pareto plots for *Bias* versus *NSE* in the LJR basin at the last iteration in 10 parameter optimizations (a–j).

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_97_0.png)

Figure 3.9 Two-dimensional Pareto plots for Bias versus NSE in the XJR basin at the last iteration in 10 parameter optimizations (a–j).

and Figure 3.9, respectively. The results demonstrated in Figure 3.8 and Figure 3.9 consist of 10 independent optimizations for SM in the two study areas, respectively. As shown in these figures, there are three groups of points, that is, final nondominated population of VIC (FNP_VIC), final nondominated population of SM (FNP_SM), and validated values of FNP_SM (VFNP_SM), which are the true outputs calculated by VIC with the parameter sets given by SM. FNP_VIC is the baseline. The center points of the FNP<sub>VIC</sub>, FNP<sub>SM</sub>, and VFNP<sub>SM</sub> are also shown in each subplot denoted as CP<sub>VIC</sub>, CP<sub>SM</sub>, and CP<sub>VSM</sub>. It is seen that there are errors between FNP<sub>SM</sub> and VFNP<sub>SM</sub>, but CP<sub>SM</sub> and CP<sub>VSM</sub> are close in each optimization in both study areas. Furthermore, CP<sub>SM</sub> and CP<sub>VIC</sub> are also compared in these scatter plots. Since a stochastic algorithm is used in this study, the results are slightly different in each optimization for SM. As seen in two figures, CP<sub>SM</sub> are very close to CP<sub>VIC</sub> in most cases. In Figure 3.8c and e, Figure 3.9b, f, and j, the distances between CP<sub>SM</sub> and CP<sub>VIC</sub> are relatively large but acceptable (less than 0.1 in all the cases).

The compromise parameter sets were selected when the four objective functions reached a good tradeoff. The compromise parameter values (normalized) of VIC and SM in the two study areas are presented in Figure 3.10. The black lines in Figure 3.10 are the results of VIC, which is

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_98_0.png)

**Figure 3.10** Compromise parameters of the surrogate model and VIC in (a) the LJR basin and (b) the XJR basin.

the baseline here. The grey lines are the results of SM. The 10 compromise parameter sets of SM are around the parameter set of VIC as shown in Figure 3.10. The optimal parameters calibrated with SM could be a very accurate approximation of VIC. In Figure 3.10a and b, the parameter set of the LJR basin is very similar to that of the XJR basin since the two study areas are dominated by similar climatic conditions. The large values of Ws in these two study areas, which is a fraction ranged from 0 to 1, mean that the base flows are both small and stable (Ws near 1 in VIC show the base flow generation is linear and small). The phenomenon accords with the feature that the runoff in the LJR basin and the XJR basin is dominated by rainfall.

## 3.5.3. Evaluation of the Surrogate Model in Two Study Areas

The evaluation indicators of the streamflow in the LJR basin and the XJR basin simulated with the parameter sets given by VIC and SM are listed in Tables 3.5 and 3.6. Here, when calculating Bias, we removed the absolute symbol to evaluate whether the streamflow was overestimated. With the parameter set given by VIC, the values of NSE at LX during the calibration and validation periods are 0.8998 and 0.7744, respectively, while those of Bias are 0.0032 and −0.1025, respectively. The ranges of NSE for 10 optimizations of SM at LX during the calibration and validation periods are 0.8990–0.9040 and 0.7616–0.7995, respectively, while those of Bias are 0.0001–0.0560 and −0.1659–-0.0965, respectively. Both NSE and Bias of VIC in the calibration and validation period are in the range of its corresponding parameter of SM at the LX station. Similarly, the results also can be seen at all the stations in the two study

Table 3.5 Evaluations of simulation with the parameter sets given by VIC and SM during calibration and validation in the LJR basin.

| Model | Period | NSE_LX | BIAS_LX (+/-) | NSE_QZ | BIAS_QZ (+/-) |
|-------|--------|--------|---------------|--------|---------------|
| VIC | Calibration | 0.8998 | 0.0032 | 0.8465 | 0.0504 |
| VIC | Validation | 0.7744 | -0.1025 | 0.7788 | -0.0465 |
| SM | Calibration | 0.8980–0.9040 | 0.0001–0.0560 | 0.8416–0.8555 | 0.0474–0.0909 |
| SM | Validation | 0.7616–0.7995 | -0.1659–-0.0965 | 0.7760–0.7860 | -0.1030–-0.0415 |
