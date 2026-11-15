
is computed by the relationship \( p_i^{t+1} = \min\{\max\{\frac{v_i^{t+1} - b_i}{2c_i}, p_i^{\min}\}, p_i^{\max}\} \), it follows that \( p_i^t \) cannot be inferred as the parameters \(\{p_i^{\max}, p_i^{\min}\}\) and \(\{b_i, c_i\}\) remain unknown to the eavesdroppers. This concludes the proof. \(\square\)

Subsequently, in the following theorem, we will conduct a privacy analysis, taking into account that external eavesdroppers might possess certain network information, such as the parameters \(\{d_i, p_i^{\max}, p_i^{\min}\}\) related to constraints, and the local step-size sequence \(\{\gamma_i^t\}\) for any \( i \in \mathcal{V} \).

**Theorem 8.3.** Even if external eavesdroppers obtain the parameters \(\{d_i, p_i^{\max}, p_i^{\min}\}\) associated with constraints and the local step-size sequence \(\{\gamma_i^t\}\), they are still unable to deduce the private information concerning the output power \( p_i^t \) and the parameters \(\{b_i, c_i\}\) in the local cost function \( J_i \) for any \( i \in \mathcal{V} \) and \( t \ge 0 \).

**Proof.** Let us assume that external eavesdroppers have access to the parameters \(\{d_i, p_i^{\max}, p_i^{\min}\}\) related to constraints, as well as the local step-size sequence \(\{\gamma_i^t\}\) for any \( i \in \mathcal{V} \). Additionally, they are aware of the update rules of (8.25), though the parameters \(\{b_i, c_i\}\) of the cost function remain unknown to them. As per the earlier analysis, the update rules in (8.25) differ fundamentally from the proposed algorithm due to the presence of conditional noises \( \epsilon_i^t \) and the random sleep strategy (which generates a Bernoulli random variable) incorporated in the proposed algorithm.

According to (8.25), external eavesdroppers might use \( T \) iterations of transmitted information to derive a similar equation to (8.26), which contains known network information along with two unknown variables \(\{b_i, c_i\}\). For the eavesdroppers, these two equations could be utilized to calculate \(\{b_i, c_i\}\), such that for any \( t = 0, \dots, T \),

```
\begin{cases}
\tilde{y}_i^t = \tilde{v}_i^{t-1} - \gamma_i^{t-1} \frac{\tilde{v}_i^{t-1} - b_i}{2c_i[\tilde{z}_i^{t-1}]_i} + \gamma_i^{t-1} \frac{d_i}{[\tilde{z}_i^{t-1}]_i}, \\
\tilde{y}_i^{t+1} = \tilde{v}_i^t - \gamma_i^t \frac{\tilde{v}_i^t - b_i}{2c_i[\tilde{z}_i^t]_i} + \gamma_i^t \frac{d_i}{[\tilde{z}_i^t]_i}.
\end{cases}
(8.27)
```

However, the actual updates of the proposed algorithm correspond to

```
\begin{cases}
\begin{cases}
\tilde{y}_i^t = \tilde{v}_i^{t-1} + \epsilon_i^{t-1} - \gamma_i^{t-1} \frac{(\tilde{v}_i^{t-1} - b_i) / 2c_i - d_i}{[\tilde{z}_i^{t-1}]_i}, \ h_i^{t-1} = 1, \\
\tilde{y}_i^t = \tilde{v}_i^{t-1} + \epsilon_i^{t-1}, \ h_i^{t-1} = 0,
\end{cases} \\
\begin{cases}
\tilde{y}_i^{t+1} = \tilde{v}_i^t + \epsilon_i^t - \gamma_i^t \frac{(\tilde{v}_i^t - b_i) / 2c_i - d_i}{[\tilde{z}_i^t]_i}, \ h_i^t = 1, \\
\tilde{y}_i^{t+1} = \tilde{v}_i^t + \epsilon_i^t, \ h_i^t = 0.
\end{cases}
\end{cases}
(8.28)
```

Therefore the values of \(\{b_i, c_i\}\) derived from (8.27) are not reliable. Moreover, numerous equations similar to (8.27) can be generated across \( T \) iterations, each yielding different sets of \(\{b_i, c_i\}\). As a result, external eavesdroppers are unable to determine the exact values of \(\{b_i, c_i\}\), which further prevents them from accurately deducing the local cost function \( J_i \) of generator \( i \in \mathcal{V} \).

Additionally, based on Theorem 8.2, external eavesdroppers cannot access the precise value of $p_i^0$, and the computation of $p_i^t, i \in \mathcal{V}, t \ge 0$, relies on either

$$ \bar{\gamma}_i^{t+1} = \bar{v}_i^t - \gamma_i^t \frac{p_i^t}{[\bar{z}_i^t]_i} + \gamma_i^t \frac{d_i}{[\bar{z}_i^t]_i}, \quad (8.29) $$

or

$$ p_i^t = \min\{\max\{\frac{v_i^t - b_i}{2c_i}, p_i^{\min}\}, p_i^{\max}\}. \quad (8.30) $$

Thus akin to the analysis in Theorem 8.2, the precise value of $p_i^t$ is inaccessible to the external eavesdroppers when calculated using (8.29). Furthermore, the value of $p_i^t$ in (8.30) is only correct when $p_i^t = p_i^{\min}$ or $p_i^t = p_i^{\max}$, but these scenarios are unlikely as the algorithm continues to update. Considering these two situations, this proof is thus concluded.

**Remark 8.9.** In relation to the decentralized primal-dual gradient method (8.25), also discussed in [24], the exact values $\{p_i^t, c_i, b_i\}$ can be inferred if external eavesdroppers possess knowledge of the network information \(\{d_i, p_i^{\max}, p_i^{\min}\}\) and the local step-size sequence \(\{\gamma_i^t\}\) for any \(i \in \mathcal{V}\). Therefore the noises introduced in the proposed algorithm facilitate privacy protection. The proposed algorithm offers privacy protection comparable to the methods mentioned in [31–36], with the potential advantage of reduced data transmission and transmission cost due to the implementation of a random sleep strategy.

## 8.5 Simulation experiments

This section aims to validate the effectiveness of the proposed algorithm. The experiments are conducted in Matlab® R2021a on a personal computer equipped with an Intel i9-12900H 2.5 GHz processor, a GeForce RTX 3060 6 GB GPU, 16.0 GB of RAM, and a 64-bit Windows 11 operating system. The optimal solutions for the following examples are obtained using the Yalmip toolbox in Matlab for verification and comparison purposes.

### 8.5.1 Example 1: 5-bus islanded microgrid

We first examine the Economic Dispatch Problem (EDP) on a 5-bus islanded microgrid [22] as illustrated in Fig. 8.1, where each bus is associated with a generator and a load, and each dotted line represents a directed (unbalanced) and strongly connected interaction link. The local cost function of each generator $i=1, 2, 3, 4, 5$, is quadratic, described by $J_i(p_i) = c_i p_i^2 + b_i p_i + a_i$. The cost coefficients $(c_i, b_i, a_i)$ of each generator $i$ and the generation capacities ($p_i \in [p_i^{\min}, p_i^{\max}]$) are summarized in Table 8.1 [22]. Assume that the total demand required from the microgrids is 120 kW,

![](img/3cc494b92b35bef197b953dcaa648a44_255_0.png)

## FIGURE 8.1
Diagram of the 5-bus islanded microgrid.

with active local demands on each bus being \(d_1 = 35\) kW, \(d_2 = 20\) kW, \(d_3 = 25\) kW, \(d_4 = 30\) kW, and \(d_5 = 10\) kW. In this scenario, we set the local step-size \(\gamma^i = 1 / \Gamma^i\), the random sleep probability \(\mathbb{P}(h_i^t = 1) = \eta_i = 0.8\), and the bounds of the added conditional noises \(\hat{\varepsilon}^i = 1/t^{2.1}\) for all \(i = 1, ..., 5\), and \(t \ge 0\).

- 1) Convergence: The simulation results are depicted in Figs. 8.2 and 8.3. Fig. 8.2(a) illustrates the evolution of the power generation \(p_i\) for each generator \(i = 1, 2, 3, 4, 5\), and Fig. 8.2(b) displays the evolution of the incremental cost \(\gamma_i\), \(i = 1, 2, 3, 4, 5\). From Fig. 8.2, it can be concluded that the optimal power outputs are \(p_1^* = 32.81\) kW, \(p_2^* = 25.51\) kW, \(p_3^* = 23.14\) kW, \(p_4^* = 20.54\) kW, and \(p_5^* = 18.00\) kW, with the optimal incremental cost \(\gamma^* = 7.389\) $/kW. Fig. 8.3(a) shows the balance between total generation and total demand, while Fig. 8.3(b) illustrates the total cost of the microgrid. From Fig. 8.2, it is evident that the total power generation meets the total demand as \(p_i^t\) and \(\gamma_i^t\) converge to the optimal solution, leading to the total cost achieving its optimal value.

- 2) Privacy Protection: Next, we validate the privacy-protection performance of the proposed algorithm. As outlined in Theorem 8.2, external eavesdroppers without

## Table 8.1 Generator parameters in a 5-bus islanded microgrid.

| Bus | \(c_i\) ($/kW^2) | \(b_i\) ($/kW) | \(a_i\) ($) | \([p_i^{\min}, p_i^{\max}]\) (kW) |
|---|---|---|---|---|
| 1 | 0.094 | 1.22 | 51 | [10, 80] |
| 2 | 0.078 | 3.41 | 31 | [8, 60] |
| 3 | 0.105 | 2.53 | 78 | [3.8, 40] |
| 4 | 0.082 | 4.02 | 42 | [5.4, 45] |
| 5 | 0.074 | 3.17 | 62 | [4.2, 18] |
