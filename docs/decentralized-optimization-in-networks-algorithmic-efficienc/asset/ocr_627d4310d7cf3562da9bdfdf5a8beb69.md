$a^{i,l} = -1$. In other words, for every $(i, l)$ pair, if $(y_t^*)^\top c_t^{i,l} + h_t^* \ge 0$, then $a^{i,l}$ equals $1$; otherwise, it equals $-1$. Consequently, this online classification task can be framed as a minimization problem at every time step $t \ge 1$:

$$\min_{y,h} \sum_{i=1}^n \sum_{l=1}^{v^i} \log(1 + e^{-a^{i,l}(y^\top c_t^{i,l} + h)}) + \frac{K}{2}(\|y\|^2 + h^2),$$

where $K = 1$ is the regularization parameter. Each point $c_t^{i,l} \in \mathbb{R}^2$ traverses along a circular path, adhering to the subsequent rule:

$$c_t^{i,l} = c_p^{i,l} + r \left[ \begin{array}{c} \cos(t/100) \\ \sin(t/100) \end{array} \right],$$

with radius $r = 1$, where $c_p^{i,l} \in \mathbb{R}^2$ denotes the randomly generated circle center. We define $\alpha_t$ as $\frac{1}{20\sqrt{t+1}}$, set $\delta$ equal to $\frac{d}{\sqrt{T}}$, and assign $b_t$ a value of $5$. Subsequently, the simulation results are presented in three distinct segments as follows.

**1) Comparison:** In this part, our primary objective is to demonstrate the convergence behavior of Algorithm 1, alongside two comparable algorithms from [20, 40], across a temporal horizon of $T = 200$. The results are visually presented in Fig. 6.4, mirroring the overarching conclusions drawn from Fig. 6.1. Specifically, Algorithm 1 exhibits remarkable suitability for dynamic directed networks, demonstrating an asymptotic sublinear convergence rate, even under the consideration of privacy-preservation measures.

![](bbox=[0.314, 0.56, 0.725, 0.791])

**FIGURE 6.4**
Evolutions of the average regret $\bar{R}_{\text{avg}}(T)$ of Algorithm 1 and other related algorithms.

**2) Machine learning:** To reinforce the efficacy of Algorithm 1 in the realm of large-scale machine learning, we harness the MNIST dataset sourced from [57] to