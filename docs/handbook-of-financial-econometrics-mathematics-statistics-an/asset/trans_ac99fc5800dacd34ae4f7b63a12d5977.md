
向量。然后 Y 被称为具有偏态正态分布，如果其概率密度函数如下所示：

$$
f_Y(y) = 2\phi_k(y,\Omega_Y)\Phi(\alpha^t y)
$$

其中 $\alpha$ 是一个 $k$ 维列向量，$\phi_k(y,\Omega_Y)$ 是均值为零且相关矩阵为 $\Omega_Y$ 的 $k$ 维标准正态随机变量的概率密度函数，而 $\Phi(\alpha^t y)$ 是在 $\alpha^t y$ 处求值的 1 维标准正态随机变量的概率分布函数。

## 11.3.1.3 ARCH 和 GARCH 方法

自 ARCH 和 GARCH 模型发展以来，用于估计对冲比率的 OLS 方法已得到推广，以考虑公式 (11.20) 中误差项的异方差性。在这种情况下，而不是使用无条件样本方差和协方差，GARCH 模型中的条件方差和协方差用于估计对冲比率。如上所述，这种技术允许在对冲期间更新对冲比率。

考虑以下双变量 GARCH 模型（参见 Cecchetti et al., 1988; Baillie and Myers, 1991）：

$$
\begin{bmatrix} \Delta S_t \\ \Delta F_t \end{bmatrix} = \begin{bmatrix} \mu_1 \\ \mu_2 \end{bmatrix} + \begin{bmatrix} e_{1t} \\ e_{2t} \end{bmatrix} \iff \Delta Y_t = \mu + e_t,
$$

$$
e_t|\Omega_{t-1} \sim N(0, H_t), \quad H_t = \begin{bmatrix} H_{11,t} & H_{12,t} \\ H_{12,t} & H_{22,t} \end{bmatrix},
$$

$$
\operatorname{vec}(H_t) = C + A \operatorname{vec}(e_{t-1} e'_{t-1}) + B \operatorname{vec}(H_{t-1}). \tag{11.22}
$$

时间 $t$ 的条件 MV 对冲比率由 $h_{t-1} = H_{12,t}/H_{22,t}$ 给出。该模型允许对冲比率随时间变化，从而产生一系列对冲比率，而不是整个对冲期限的单一对冲比率。公式 (11.22) 表示一个 GARCH 模型。如果 $B$ 等于零，则该 GARCH 模型将简化为 ARCH。

SAS 应用：基于附录 11C 中给出的月度标准普尔 500 指数及其期货，我们在本节中使用公式 (11.22) 中的 ARCH 和 GARCH 方法来估计对冲比率。

```text
proc autoreg data = sp500monthly;
model C_spot = C_future / nlag=2 garch=(q=1,p=1) maxit=50;
ods output ParameterEstimates=estimate_autoreg;
run;
```

| 变量 | DF | 估计值 | 标准误 | t值 | Probt |
|---|---|---|---|---|---|
| Intercept | 1 | 0.0563 | 0.009424 | 5.97 | <0.0001 |
| C_future | 1 | 0.9997 | 0.000461 | 2167.28 | <0.0001 |
| AR1 | 1 | 0.9944 | 0.007702 | 129.12 | <0.0001 |
| AR2 | 1 | 1.0042 | 0.015 | 66.86 | <0.0001 |
| ARCH0 | 1 | 0.005013 | 0.005881 | 0.85 | 0.394 |
| ARCH1 | 1 | 0.8427 | 0.1154 | 7.3 | <0.0001 |
| GARCH1 | 1 | 0.589 | 0.0371 | 15.88 | <0.0001 |

- C_spot — 自 2000 年 1 月 1 日至 2015 年 7 月 31 日的月度现货收益率变化。
- C_future — 自 2000 年 1 月 1 日至 2015 年 7 月 31 日的月度期货收益率变化。

该模型可以扩展以包括一种以上的现金和期货合约（参见 Sephton, 1993a）。例如，考虑一个由现货小麦 ($S_{1t}$)、现货油菜籽 ($S_{2t}$)、小麦期货 ($F_{1t}$) 和油菜籽期货 ($F_{2t}$) 组成的投资组合。我们然后有以下多变量 GARCH 模型：

$$
\begin{bmatrix}\Delta S_{1t}\\\Delta S_{2t}\\\Delta F_{1t}\\\Delta F_{2t}\end{bmatrix}=\begin{bmatrix}\mu_1\\\mu_2\\\mu_3\\\mu_4\end{bmatrix}+\begin{bmatrix}e_{1t}\\e_{2t}\\e_{3t}\\e_{4t}\end{bmatrix}\iff\Delta Y_t = \mu + e_t,\quad e_t|\Omega_{t-1} \sim N(0, H_t).
$$

MV 对冲比率可以使用上面描述的类似技术进行估计。例如，条件 MV 对冲比率由现货和期货价格变化之间的条件协方差除以期货价格变化的条件方差给出。现在，我们展示如何使用 SAS 根据 ARCH 和 GARCH 模型估计对冲比率。

## 11.3.1.4 状态转换 GARCH 模型

上文讨论的 GARCH 模型可以通过允许状态转换而进一步扩展，如 Lee 和 Yoder (2007) 所建议的。在该模型下，数据生成过程可以处于由状态变量 $s_t = \{1, 2\}$ 表示的两种状态或体制之一，假定其遵循一阶马尔可夫过程。状态转移概率假定遵循逻辑分布，其中转移概率由下式给出

$$
\Pr(s_t = 1|s_{t-1} = 1) = \frac{e^{p_0}}{1 + e^{p_0}} \quad \text{and} \quad \Pr(s_t = 2|s_{t-1} = 2) = \frac{e^{q_0}}{1 + e^{q_0}}
$$

条件协方差矩阵由下式给出

$$
H_{t,s_t} = \begin{bmatrix} h_{1,t,s_t} & 0 \\ 0 & h_{2,t,s_t} \end{bmatrix} \begin{bmatrix} 1 & \rho_{t,s_t} \\ \rho_{t,s_t} & 1 \end{bmatrix} \begin{bmatrix} h_{1,t,s_t} & 0 \\ 0 & h_{2,t,s_t} \end{bmatrix}
$$

其中

$$
h_{1,t,s_t}^2 = \gamma_{1,s_t} + \alpha_{1,s_t} e_{1,t-1}^2 + \beta_{1,s_t} h_{1,t-1}^2
$$

$$
h_{2,t,s_t}^2 = \gamma_{2,s_t} + \alpha_{2,s_t} e_{2,t-1}^2 + \beta_{2,s_t} h_{2,t-1}^2
$$

$$
\rho_{t,s_t} = (1 - \theta_{1,s_t} - \theta_{2,s_t}) \rho + \theta_{1,s_t} \rho_{t-1} + \theta_{2,s_t} \phi_{t-1}
$$

$$
\phi_{t-1} = \frac{\sum_{j=1}^2 \varepsilon_{1,t-j} \varepsilon_{2,t-j}}{\sqrt{\left(\sum_{j=1}^2 \varepsilon_{1,t-j}^2\right)\left(\sum_{j=1}^2 \varepsilon_{2,t-j}^2\right)}},
$$

$$
\varepsilon_{i,t} = \frac{e_{i,t}}{h_{it}}, \quad \theta_1,\theta_2 \ge 0 \quad \text{and} \quad \theta_1 + \theta_2 \le 1.
$$

一旦条件协方差矩阵被估计，时变条件 MV 对冲比率由现货和期货收益率之间的协方差与期货收益率的方差之比给出。

## 11.3.1.5 随机系数方法

处理异方差性还有另一种方法。这涉及使用 Grammatikos 和 Saunders (1983) 建议的随机系数模型。该模型采用公式 (11.20) 的以下变体：

$$
\Delta S_t = \beta_0 + \beta_t \Delta F_t + e_t, \tag{11.23}
$$

其中对冲比率 $\beta_t = \bar{\beta} + v_t$ 假定为随机。这种随机系数模型在某些情况下可以提高对冲策略的有效性。然而，即使在估计对冲比率时可以对随机性进行修正，该技术也不允许在时间上更新对冲比率。

## 11.3.1.6 协整与误差修正方法

到目前为止描述的技术没有考虑到现货价格和期货价格序列可能是非平稳的可能性。如果这些序列具有单位根，则会引发不同的问题。如果两个序列如 Engle 和 Granger (1987) 所定义的那样是协整的，则回归方程 (11.20) 将被错误设定，并且必须在方程中包含误差修正项。由于套利条件将现货和期货价格联系在一起，它们在长期内不能相差太远。因此，如果两个序列都遵循随机游走，则我们期望这两个序列是协整的，在这种情况下我们需要估计误差修正模型。这需要使用协整分析。

协整分析涉及两个步骤。首先，每个序列必须进行单位根检验（例如，参见 Dickey 和 Fuller, 1981; Phillips 和 Perron, 1988）。其次，如果发现两个序列都具有单一单位根，则必须进行协整检验（例如，参见 Engle 和 Granger, 1987; Johansen 和 Juselius, 1990; Osterwald-Lenum, 1992）。

如果现货价格和期货价格序列被发现是协整的，则对冲比率可以分两步估计（参见 Ghosh, 1993; Chou et al., 1996）。第一步涉及以下协整回归的估计：

$$
S_t = a + bF_t + u_t. \tag{11.24}
$$

第二步涉及以下误差修正模型的估计：

$$
\Delta S_t = \rho u_{t-1} + \beta \Delta F_t + \sum_{i=1}^{m}\delta_i \Delta F_{t-i} + \sum_{j=1}^{n}\theta_j \Delta S_{t-j} + e_t. \tag{11.25}
$$

其中 $u_t$ 是来自协整回归的残差序列。对冲比率的估计由 $\beta$ 的估计给出。一些研究人员（例如，参见 Lien 和 Luo, 1993b）假设长期协整关系为 $(S_t - F_t)$，并估计以下误差修正模型：

$$
\Delta S_t = \rho(S_{t-1} - F_{t-1}) + \beta \Delta F_t + \sum_{i=1}^{m}\delta_i \Delta F_{t-i} + \sum_{j=1}^{n}\theta_j \Delta S_{t-j} + e_t. \tag{11.26}
$$

另外，Chou et al. (1996) 建议按如下方式估计误差修正模型：

$$
\Delta S_t = \alpha \hat{u}_{t-1} + \beta \Delta F_t + \sum_{i=1}^{m}\delta_i \Delta F_{t-i} + \sum_{j=1}^{n}\theta_j \Delta S_{t-j} + e_t. \tag{11.27}
$$

其中 $\hat{u}_{t-1} = S_{t-1} - (a + bF_{t-1})$；即，序列 $\hat{u}_t$ 是公式 (11.24) 的估计残差序列。对冲比率由公式 (11.26) 中的 $\beta$ 给出。
