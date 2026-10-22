
based on usage of an existing set of optimal solutions, derived from analysis of historical events (commonly available in some databases), from which the real-time decision is chosen using some criteria. For example, Malekmohammadi et al. (2009) built a hydrodynamic model for Bakhtiari and Dez River-Reservoir systems in Iran, used to derive optimal solutions from historical floods using genetic algorithm. When current observation comes, similar events as well as corresponding optimal solutions would be found by the K nearest neighbor (K-NN) algorithm. However, such research that considers real-time operation is mostly related to reservoir operation or water distribution systems operations, while studies that are considering flood storage area management are absent. To our knowledge, this study is the first one to study both real-time operation and robust optimization of flood storage areas for developing operation strategies.

This chapter proposes robust optimization strategies and near-real-time operation method for operating multiple gates of the flood storage areas considered. Before the start of strategy development, uncertainty of inflow was analyzed, which was realized by sampling synthetic hydrographs, generating 100 possible inflow hydrographs with the characteristic of different severity levels. In order to produce robust strategies, the method of ROPAR was used and the probability of inundation of the considered storage areas was derived. For developing potential real-time operation method, these sampled hydrographs and corresponding optimal solutions were taken as pre-existing set of solutions to be considered during actual strategy selection and extraction. In order to identify the most similar inflow conditions, four methods were proposed and tested. The testing was carried out by three amplified hydrographs (considered actual for real-time operations), which were derived by a standard approach taken in China to represent hydrographs with different return periods. Finally, the robust strategies and real-time decisions were compared so that the suitability of the different methods could be assessed. The analysis of storage area operation could hopefully provide suggestions for local administration with the aim of reducing flood risk in Bengbu City while simultaneously lowering storage area damage.

## 14.2. Materials and Methods

### 14.2.1. Available Data and Models

As this study is a continuation of previous work of Jonoski et al. (2018) and Jonoski et al. (2019), some of their methodologies and results need to be briefly introduced here. These past studies, as well as the one presented here, use a hydrodynamic model and a coupled simulation-optimization model, described below.

### 14.2.2. HEC-RAS Hydrodynamic Model

The hydrodynamic model was built using HEC-RAS software, covering the whole study area, from upstream Lutaizi station to downstream Bengbu City, including four main storage areas. This model simulates the propagation of hydrographs from Lutaizi to Bengbu providing results in terms of water levels in both Bengbu City and four storage areas. These results depend on the upstream hydrograph and certain operations of inlet and outlet gates that control the usage of the flood storage areas. In previous studies, the inflow hydrograph was from observed discharge from 24 June to 7 September 2007 (Fig. 14.2).

### 14.2.3. Coupled Simulation-Optimization Model

The coupled simulation-optimization was set up by embedding the HEC-RAS model in the optimization process using the Nondominated Sorting Genetic Algorithm II (NSGA II).

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_393_0.png)

Figure 14.2 Inflow hydrograph at Lutaizi station from 24 June to 7 September 2007.

The decision variables X in this optimization problem are the values of stage differences between the river and the storage areas, which in HEC-RAS triggers the opening/closing of the control gates. These values are in fact determining the operational strategies for the gates. In order to decrease complexity in the optimization, only the operation of four storage area inlet gates was taken into consideration. (Stage differences for the outlet gates were set at 0.1 m for opening and 0 m for closing, as their use is only after the passage of the flood peak.) For each inlet gate, the stage difference for gate opening is an absolute value while the stage difference for closing uses a variable that is a fraction (from 0 to 1), which multiplies the value of stage difference for gate opening (to ensure that stage differences for closing are always smaller than those for opening). Therefore, there are eight decision variables (X = (X1, X2, X3, X4, X5, X6, X7, X8)) in total (four inlet gates for four storage areas, each with one opening and one closing stage difference value).

The conflicting objectives were described by two objective functions, downstream flood risk (Obj1) at the location of Bengbu City, and storage area damage index (Obj2). The first objective consists of three components: (subobjective 1) the duration when stage in Bengbu is higher than predetermined warning level (HW, 20.3 m), which needs to be as short as possible; (subobjective 2) the difference between maximum stage and warning level, which should be as small as possible; (3) because stage at Bengbu should be strictly below a predetermined safeguard level (HS, 22.3 m), it becomes a constraint in the optimization problem by introducing a penalty function. The function of the first objective is

Min F1(X) = w1 · O1(h(X), HW) + w2 · O2(h(X), HW)
          + P(h(X), HS),          (14.1)

O1(h(X), HW) = T(h(X) > HW),          (14.2)
O2(h(X), HW) = max(h(X)) − HW.          (14.3)
P(h(X), HS) = 10^{17 max(h(X)−HS)},          (14.4)

where, F1(X) is downstream flood risk; X is the vector of decision variables; h(X) is stage hydrograph at Bengbu City; HW is warning level (20.3 m); HS is safeguard level (22.3 m); O1 is subobjective 1 (in unit of day); O2 is subobjective 2 (in unit of decimeter); P is a penalty function; w1 and w2 are weights for subobjective 1 and 2 respectively (both equal to 0.5). T is duration of stage h(X) above HW.

The calculation of subobjective 1 and 2 is indicated in Figure 14.3 with the example of a hydrograph in Bengbu City in 2007.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_396_0.png)

Figure 14.4 Damage curves for four storage areas (Jonoski et al., 2019).

parameters (stage differences), the hydrodynamic model provides water stage information so that the objective functions are calculated. The NSGA II algorithm continues this process toward obtaining improved values of the objective functions, until the end when it identifies the final Pareto set of optimal solutions (Fig. 14.5). Figure 14.6 shows the actual operation with one optimal strategy as well as the results of applying that strategy. The top-left subfigure of Figure 14.6 shows the maximum inundation in the flood storage areas, and the top-right shows the downstream water level at Bengbu with and without using that strategy. The last four subfigures show the gate operations for the four storage areas.

### 14.2.4. Methodology

Based on the previous work and obtained results, the methodology of this study consists of three components. The first one is the determination of uncertain inflow. Synthetic hydrographs were proposed with similar characteristics as the real one used previously (from year 2007), on which

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_397_0.png)

Figure 14.5 Example of Pareto front of the coupled simulated-optimization model.

Latin Hypercube Sampling (LHS) was performed. The obtained results were used for developing robust strategies as well as a similarity-based selection method for real-time operation. The method of Homogeneous Multiple Enlargement (HME) was used to develop hydrographs for verifying the methodologies. The second component is to develop robust strategies using the method of Robust Optimization and Probabilistic Analysis of Robustness (ROPAR). The last component proposed four methods to do similarity selection as ways for selecting real-time optimal strategies, which finally would be compared with the results from ROPAR under the same flood conditions.

### 14.2.5. Uncertainty Analysis of Inflow

Due to the limitation of availability of enough inflow data in the study area, it was decided to sample synthetic hydrographs using parametric functions instead of analysing historical records. The function is
