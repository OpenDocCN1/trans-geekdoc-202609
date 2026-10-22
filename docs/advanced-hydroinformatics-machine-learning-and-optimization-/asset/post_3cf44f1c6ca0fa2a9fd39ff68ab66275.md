
Table 15.1 Performance metrics for test runs of the ML models.

| Measures | MLP |  |  | RBN |  |  | LF | Naive |
|---|---|---|---|---|---|---|---|---|
|  | 6-7-1 | 6-6-1 | 6-4-1 | 6-7-1 | 6-6-1 | 6-4-1 |  |  |
| RMSE | 5.17 | 5.33 | 5.25 | 5.19 | 5.47 | 5.48 | 6.22 | 6.89 |
| MAE | 2.97 | 3.27 | 3.14 | 2.92 | 3.32 | 3.20 | 3.60 | 3.38 |
| Correlation | 0.988 | 0.987 | 0.988 | 0.988 | 0.987 | 0.987 | 0.982 | 0.978 |
| Nash-Sutcliffe | 0.976 | 0.974 | 0.975 | 0.976 | 0.973 | 0.973 | 0.965 | 0.957 |

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_441_0.png)

Figure 15.9 Test run for 6-7-1 MLP configuration for simulation of real reservoir operation.

July 2019. This means that the actual operation of the reservoir for that period can be very predictive for any model.

## 15.3.3. Incorporating ML Models Into the Reservoir Operation Model

Each of the ML models built in the previous section were coupled to the reservoir operation model described in section 15.2.3 to define the controlled discharges Q_{c,t} at each time step t. The ML models were integrated into the water release decision component (see dashed line segmented rectangle in Fig. 15.5). Therefore, inside the reservoir operation model, the outputs of the ML models Q_t are redefined as Q_{ml,t}, as indicated in equation (15.2). Table 15.2 and Figure 15.10 summarize the main components of the ML models.

The reservoir operation model described in section 15.2.3 is completed by coupling the ML models. In summary, seven different ML model configurations were built, each one elaborated in Python. The parameters of the ML models are the decision variables of the optimization process, described in section 15.3.5.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_442_0.png)

Figure 15.10 Configuration of the (a) MLP and (b) RBN proposed for the operation models.

Table 15.2 Summary of the parameters and configuration of the ML models.

| Model | Configuration | Inputs | Output | Parameters | Range | Number of parameters |
|---|---|---|---|---|---|---|
| MLP | 6-7-1 | $IN_{t-2}, IN_{t-1}, S_{t-2}, S_{t-1}, Q_{t-2}, Q_{t-1}$ | $Q_t$ | $w_i, b_i$ | $[-1, 1]$ | 57 |
| MLP | 6-6-1 | $IN_{t-2}, IN_{t-1}, S_{t-2}, S_{t-1}, Q_{t-2}, Q_{t-1}$ | $Q_t$ | $v_i, c$ | $[-1, 1]$ | 49 |
| MLP | 6-4-1 | $IN_{t-2}, IN_{t-1}, S_{t-2}, S_{t-1}, Q_{t-2}, Q_{t-1}$ | $Q_t$ |  | $[-1, 1]$ | 33 |
| RBN | 6-7-1 | $IN_{t-2}, IN_{t-1}, S_{t-2}, S_{t-1}, Q_{t-2}, Q_{t-1}$ | $Q_t$ | $c_i, r_i$ | $[-10, 10]$ | 91 |
| RBN | 6-6-1 | $IN_{t-2}, IN_{t-1}, S_{t-2}, S_{t-1}, Q_{t-2}, Q_{t-1}$ | $Q_t$ | $w_i$ | $[-10, 10]$ | 78 |
| RBN | 6-4-1 | $IN_{t-2}, IN_{t-1}, S_{t-2}, S_{t-1}, Q_{t-2}, Q_{t-1}$ | $Q_t$ |  | $[-10, 10]$ | 52 |
| LF | – | $IN_{t-2}, IN_{t-1}, S_{t-2}, S_{t-1}, Q_{t-2}, Q_{t-1}$ | $Q_t$ | $b, \beta_1, \beta_2, \beta_3, \beta_4, \beta_5, \beta_6$ | $[-5, 5]$ | 7 |

## 15.3.4. Objective Functions

The optimization process uses the reservoir operation model to identify what parameters of the ML models represent the best solutions (i.e., nondominated solutions). There are three objectives: Flood control, water supply for irrigation, and hydropower generation.

### OF1. Flood Control

The goal is to minimize $Q_{f,t}$, which is obtained in each time step $t$ from the conditional equation (15.9), where $(Q_t - \bar{q})^2$ represents the square of the excess flows, being $Q_t$ (m³/s) the reservoir's daily discharge and $\bar{q}$ a proposed limit flood flow. The following function defines OF1 for the entire analysis period $T$:

$OF1 = \sum_{t=1}^{T} (Q_{f,t})$,  (15.8)

$Q_{f,t} = \begin{cases} 0 & \text{if } Q_t \le \bar{q} \\ (Q_t - \bar{q})^2 & \text{otherwise} \end{cases}$.  (15.9)

In the present study, a flow limit is proposed from which the optimizer seeks to punish the discharges. Similar to Saavedra et al. (2010), this limit flow is set as the average of all the daily discharge values ($Q_t$) of the reservoir that exceeded the average discharge flow of the series ($Q_{mean}$). Therefore,

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_444_0.png)

Figure 15.11 Demand for irrigation downstream of the reservoir.

using equation (15.10), the flow limit q̄ is obtained, where N = number of records that exceeded the average discharge flow of the series.

q̄ = Σ_{i=1}^{N} Q_i / N ; Q_i > Q_mean. (15.10)

### OF2. Water Supply for Irrigation

The goal is to minimize deficits in the irrigation water supply Q_ir,t in each time step t from the reservoir's daily discharge Q_t (m³/s) with respect to the water demand for irrigation d_t. The following function defines OF2 for the entire period of analysis T:

OF2 = Σ_{t=1}^{T} (Q_ir,t) (15.11)

Q_ir,t = { 0 if Q_t > d_t ; (d_t - Q_t)^2 otherwise } (15.12)

Irrigation demands were obtained using the CROPWAT program (Smith, 1992). Taking into account that the cultivation of rice demands the greatest amount of water and covers the largest area of crops in the lower Yuna, irrigation demand calculations were made from the requirements and the cycle of the rice cultivation. Rice in the Dominican Republic has two sowing periods in the year: (1) December to April, and (2) the months of June, July, and August (Moquete, 2004). Climatic data (temperature, humidity, wind speed, hours of sunshine) and rainfall data were provided by INDRHI (taking monthly mean data for the analysis period). From the cultivation areas, the monthly average demands for the analysis period (2009–2019) were calculated, which are shown in Figure 15.11.

### OF3. Hydropower Generation (Total)

The goal is to maximize the power generated (KW) for the entire analysis period T from the powers generated in each time step P_t. The following function defines OF3:

$$OF3 = \sum_{t=1}^{T} P_t, \tag{15.13}$$ $$P_t = \eta \gamma H_t q_{turb,t}, \tag{15.14}$$ $$\eta = f(q_{turb,t}), \tag{15.15}$$

where γ is the specific weight of water; H_t is the hydraulic head, which depends on the reservoir's water level and the elevation of the turbine axis; η is the efficiency of the turbine as a function of the discharge; and q_{turb,t} is the discharge through turbine (m³/s). It is important to mention that a conversion factor of -1 is applied to OF3 (equation 15.13) within the optimizer in this study, since the modules used by the program (JMETALPY) work only for minimization objectives (Benitez-Hidalgo et al., 2019).

In hydroelectric plants, there are other important indicators, such as firm energy, with which the energy security of a system can be evaluated. Due to the fact that Hatillo hydroelectric plant has a low installed capacity compared with the large hydroelectric plants in the Dominican Republic, total energy is the only objective considered in this study. This simplifies the optimization process; however, a firm energy indicator is evaluated in the results obtained (section 15.4).

## 15.3.5. Optimization and Computational Details

The optimization was performed on the reservoir operation model for the analysis period (2009–2019), using the parameters of the ML models as decision variables. This method belongs to the direct search policy (DPS) approach where the optimizer acts on the parameters of the functions that represent an operation policy, this being the ML models. Table 15.3 summarizes the number of optimized parameters for each model. The objective functions were defined in section 15.3.4.

Two EAs were used to optimize the operation model: the NSGA II and the MOEA / D. JMETALPY (Benitez-Hidalgo et al., 2019), a multi-objective optimization environment (developed in Python) that contains a set of modules with different multi-objective and single-objective optimization algorithms, was also used. With JMETALPY, a set of problems was used to evaluate the optimization algorithms. The operation model was inserted into JMETALPY as a subclass of floating problems.

Table 15.3 Parameters of the optimization process.

| Parameter | MLP 6-7-1 | MLP 6-6-1 | MLP 6-4-1 | RBN 6-7-1 | RBN 6-6-1 | RBN 6-4-1 | LF |
|---|---|---|---|---|---|---|---|
| Configuration | 6-7-1 | 6-6-1 | 6-4-1 | 6-7-1 | 6-6-1 | 6-4-1 |  |
| Weights ($w_i$, $v_i$) | 42+7 | 36+6 | 24+4 | 7 | 6 | 4 | – |
| Bias ($b_i$) | 7+1 | 6+1 | 4+1 | – | – | – | 1 |
| Radius ($r_{j,i}$) | – | – | – | 42 | 36 | 24 | – |
| Centers ($c_{j,i}$) | – | – | – | 42 | 36 | 24 | – |
| LF coefficients | – | – | – | – | – | – | 6 |
| Total | 57 | 49 | 33 | 91 | 78 | 52 | 7 |

The values for population size and individual parameters in the algorithms largely depended on the optimization problem (Ritter, 2016). Trial and error tests were carried out using various population ranges to select the population size. Populations greater than 100 individuals did not improve the results and increased the computational time needed for the NSGA II. For the MOEA / D, the population was defined as 300 individuals. For the other parameters, trial and error tests were performed using small populations (up to 50 individuals) so that the program could converge rapidly. Default values were taken as a basis for the algorithms.

The optimization process was developed by a computer with 16 GB of RAM and eight 2.6 GHz cores. The codes were executed by implementing the Multiprocess Evaluator module, which allowed faster calculations and for different individuals within the same generation to be calculated in parallel. On average, the program reported convergence for each operating model after 8 hr in 10,000 evaluation processes.

Using the JMETALPY display module, the Pareto fronts were obtained for each of the program executions. For each model, a 3-D Pareto front was generated, having been optimized by both the NSGA II algorithm and the MOEA / D. A total of 14 models was simulated. As mentioned above, the decision variables were the parameters of the ML models. Therefore, the optimized parameters for MLP were weights ($w_i$, $v_i$) and biases ($b_i$). In RBN models, they were centers ($c_{j,i}$), radii ($r_{j,i}$), and weights $w_i$. For LF, the coefficients are $\beta_1$, $\beta_2$, … $\beta_M$ and the bias is ($b_i$). The parameters are summarized in Table 15.3.

## 15.4. Results

After compiling the Pareto fronts generated by the optimizers, non-dominated solutions were obtained. These represent different reservoir
