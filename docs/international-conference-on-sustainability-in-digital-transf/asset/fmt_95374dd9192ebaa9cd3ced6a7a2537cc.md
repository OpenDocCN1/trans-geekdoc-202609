
In recent years, natural disasters such as climate change, ecosystem shifts, coral reef mortality, flooding, rising sea levels, and melting glaciers have increased. This can be attributed to the worsening energy crisis and environmental pollution. According to scientists, humans are responsible for nearly 90% of global climate change \[[1](#ch6.xhtml#ref6_1)\]. We have met our energy needs with petrochemical fuel for the past century, resulting in increased emissions of greenhouse gases such as carbon dioxide, a worsening greenhouse effect, and climatic anomalies. Anthropogenic processes such as livestock husbandry, agriculture, the extraction of fossil fuels for transportation, and refrigerant manufacturing all contribute to the acceleration of climate change \[[2](#ch6.xhtml#ref6_2), [3](#ch6.xhtml#ref6_3) and [4](#ch6.xhtml#ref6_4)\]. Efforts are being made globally to find solutions to energy and pollution problems. A concerning trend is an exponential increase in the number of automobiles in circulation, resulting in pollution issues involving hydrocarbons (`HC`), lead (`Pb`), sulfur oxides (`SOx`), nitrogen oxides (`NOx`), and carbon monoxide (`CO`) \[[5](#ch6.xhtml#ref6_5)\]. Logically, `HEV`s contribute to environmental sustainability by reducing petroleum consumption and emissions, the two primary causes of environmental degradation and the energy crisis. `HEV`s utilize electrical and mechanical energy to power the propulsion cycle, with the former derived from an electric motor and the latter from an internal combustion engine \[[6](#ch6.xhtml#ref6_6)\]. This configuration renders `HEV`s exceptionally technologically advanced.

Control mechanisms are in place to regulate the energy that must be stored and the power consumption of `HEV`s to ensure that the energy is distributed appropriately. The economy can be optimized by reducing emissions and petroleum consumption by implementing a carefully selected control system. The efficacy of the vehicle must remain uncompromised while striving for maximum efficiency \[[7](#ch6.xhtml#ref6_7), [8](#ch6.xhtml#ref6_8) and [9](#ch6.xhtml#ref6_9)\].

By analyzing the vehicle’s fuel consumption, emissions, and dynamic performance, the proposed algorithm will determine the optimal parameter values for the control strategy \[[10](#ch6.xhtml#ref6_10)\]. The vehicle’s driving performance was simulated using the software `ADVISOR`, with the configurations modified by the control parameters \[[11](#ch6.xhtml#ref6_11)\]. The simulations are executed utilizing two separate populations and iterations, and the control parameters are established using `MA`. The performance standards of the vehicle are considered constraints in this study, and a penalty function accounts for them. Furthermore, the `UDDS` driving cycle is optimized by implementing the Electric Assist Strategy \[[12](#ch6.xhtml#ref6_12), [13](#ch6.xhtml#ref6_13) and [14](#ch6.xhtml#ref6_14)\]. The simulation findings indicate that the vehicle’s performance remains consistent while `FC` and emissions improve, in contrast to the preset parallel `HEV` specified in `ADVISOR`.

## Methodology

### The HEV control strategy

The IC engine and the electric motor are two drives that provide power to the parallel hybrid electric vehicle. For this operation, the power must be distributed between the IC engine and the motor, and accordingly, the torque distribution happens with the help of an exemplary control approach. Many such approaches are there for the control process, but the most commonly used is electric assist.

In this strategy, the ICE engine is the primary source, and the electric motor is the auxiliary supply source. In case the IC engine cannot provide efficient energy or the maximum allowable range of torque is exceeded due to demanded power, the electric motor has been used by this electric assist approach \[[15](#ch6.xhtml#ref6_15)\]. The state of charge value of the battery decides the motor operation working as the generator, and the extra amount of torque is used in the charging operation of the battery.

```
x = SOC_L, SOC_H, T_ch, T_min, T_off, E_LSL, E_LSH, D_ch
```

`SOC[L]`, `SOC[H]`, represents the state of charge value in the lower and upper stages. The above expression shows the variables included in this strategy for optimizing the control parameters.

### Designing Objective Function

This study’s `HEV` control technique aims to accomplish several objectives simultaneously, including reducing `FC` and exhaust emissions (`HC`, `CO`, and `NOx`) while maintaining vehicle performance. Therefore, the main objectives are lowering `FC` and exhaust emissions (i.e., `CO`, `HC`, and `NOx`). The objective function is laid out as follows: (2).

```
min Obj(x) = NOX + FC + CO + HC
```

Where `x` denotes one of the solutions, i.e., the `MO`-encoded chromosomes, and `X` denotes the solution space. Nitrogen oxide is abbreviated as `NOx`, fuel consumption is abbreviated as `FC`, carbon monoxide is `CO`, and hydrocarbon is `HC`.

### Apply MA to design the appropriate HEV control strategy

The algorithm is based on Darwinian survival and the survival of the fittest, and it is comparable to the genetic algorithm (`GA`). In order to produce superior offspring, the preferred species of the chosen species undergo a random exchange of genetic information with one another. This process is repeated until the most adaptable species is created. The flowchart in [Figure 1](#ch6.xhtml#fig6_1) shows the iterative process that makes up the `MO` Algo.

![Figure 6.1 Figure Showing Flowchart of the Multi-Objective Algorithm](images/fig6_1_C.jpg)

[Figure 6.1 Figure Showing Flowchart of the Multi-Objective Algorithm](#ch6.xhtml#R_fig6_1)

The steps are illustrated in figure: -
* The initial population is generated randomly
* Make a local search
* The fitness value is calculated
* Termination of the algorithm is decided
* Selection
* Cross-over
* Poor individual is replaced
* The initial population is generated randomly.

For the initial population generation, dozens to hundreds of chromosomes are generated first without duplicating, and this initial population is expressed by (1).
* Make a local search.

In order to get a better chromosome, a local search is performed in the area near the original chromosome. In each iteration, all offspring will join in the local search, ensuring that the best solution for each part of the chromosome is always kept, and the best solution is finally determined.
* Calculate the fitness value.

The fitness function can detect whether a chromosome is excellent or poor and calculate the global optimum of each chromosome.

When the algorithm is employed, the vehicle performance criteria are defined as constraints. To verify that vehicle performance was not degraded during optimization, the `PNGV` passenger car restrictions were applied in this work. As a result, the fitness function is as follows:

```
f(x) = \frac{1}{\left\lbrack {Obj.(x) + {\sum\limits_{i = 1}^{n}y_{i}} + P_{i}(x)} \right\rbrack}
```
* Termination of the algorithm is decided

The goal of the method suggested in this study is to complete the algorithm operation with the maximum number of iterations of 1000.
* Selection

The character of progeny will be impacted by the selected outcomes, given that fitness selection is the true purpose of natural selection. In order to improve progeny production, the selection of species to include in the training corpus for cross-over purposes may be influenced by species fitness levels. Using competitive selection as its principal methodology, two chromosomes are chosen for subsequent screening in this study.
* Cross-over
