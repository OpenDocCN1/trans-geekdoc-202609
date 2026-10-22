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

# 15.3.4. Objective Functions

The optimization process uses the reservoir operation model to identify what parameters of the ML models represent the best solutions (i.e., nondominated solutions). There are three objectives: Flood control, water supply for irrigation, and hydropower generation.

# OF1. Flood Control

The goal is to minimize $Q_{f,t}$, which is obtained in each time step $t$ from the conditional equation (15.9), where $(Q_t - \bar{q})^2$ represents the square of the excess flows, being $Q_t$ (m³/s) the reservoir's daily discharge and $\bar{q}$ a proposed limit flood flow. The following function defines OF1 for the entire analysis period $T$:

$OF1 = \sum_{t=1}^{T} (Q_{f,t})$,  (15.8)

$Q_{f,t} = \begin{cases} 0 & \text{if } Q_t \le \bar{q} \\ (Q_t - \bar{q})^2 & \text{otherwise} \end{cases}$.  (15.9)

In the present study, a flow limit is proposed from which the optimizer seeks to punish the discharges. Similar to Saavedra et al. (2010), this limit flow is set as the average of all the daily discharge values ($Q_t$) of the reservoir that exceeded the average discharge flow of the series ($Q_{mean}$). Therefore,