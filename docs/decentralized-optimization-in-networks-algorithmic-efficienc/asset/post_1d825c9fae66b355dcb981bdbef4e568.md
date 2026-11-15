
## 8.2.3 Problem transformation

Following the approach of previous works [23–28], the Lagrangian function $L : P \times R_{\ge 0} \to R$ for (8.1) is formulated as follows:

$$
L(p, y) = \sum_{i=1}^m J_i(p_i) - y \sum_{i=1}^m (p_i - d_i),
$$

where $y \in R_{\ge 0}$. Then, the dual problem of (8.1) is indicated as

$$
\max_{y \in R_{\ge 0}} Q(y) = \sum_{i=1}^m Q_i(y),
$$

where $Q_i(y)$ is described as

$$
Q_i(y) = \min_{p_i \in P_i} J_i(p_i) - y(p_i - d_i), \quad i \in V.
$$

Given an optimal $p^*$, Assumption 8.1 implies that there exists at least one dual optimal solution $y^*$ for (8.3), ensuring a zero duality gap [42], i.e., $J(p^*) = Q(y^*)$. For any non-negative $y$ and under Assumption 8.1, the unique minimizer of (8.4) can be determined as follows:

$$
\tilde{p}_i(y) = \begin{cases} 
p_i^{\max}, & \nabla J_i^{-1}(y) \ge p_i^{\max}, \\ 
\nabla J_i^{-1}(y), & p_i^{\min} < \nabla J_i^{-1}(y) < p_i^{\max}, \\ 
p_i^{\min}, & \nabla J_i^{-1}(y) \le p_i^{\min}, 
\end{cases}
$$

where $\nabla J_i^{-1}(y)$ exists within $[p_i^{\min}, p_i^{\max}]$ as per Assumption 8.1. Given the non-empty set of dual optimal solutions for (8.3), for any dual optimal solution $y^*$, the sole optimal solution to (8.1) is $p_i^* = \tilde{p}_i(y^*), \forall i \in V$. Since $\tilde{p}_i(y)$ is unique for any given $y \in R_{\ge 0}$, it follows from [48] that $Q(y)$ is differentiable at $y$, with its gradient given by

$$
\nabla Q(y) = - \sum_{i=1}^m (\tilde{p}_i(y) - d_i),
$$

and $\nabla Q_i(y) = -(\tilde{p}_i(y) - d_i), \forall i \in V$. For any given $y$, it can further be deduced that $-Q_i(y)$ is a convex function, and $|\nabla Q_i(y)| \le C$, where $C > 0$ (see Proposition 1 in [36] for more details).

Currently, numerous centralized and decentralized methods exist to solve the dual problem (8.3). However, these methods often overlook the issues of private security during information exchange and the computational efficiency of generators in unbalanced directed networks. These are critical concerns in the practical economic dispatch of smart grids. To address these challenges, it is necessary to design an algorithm that not only protects sensitive information and enhances computational efficiency in a decentralized manner but also adapts to the unbalanced directed networks discussed in this chapter. This is the principal motivation behind the algorithm proposed in the following subsection.

## 8.2.4 Algorithm construction

In this subsection, to address the problem in (8.1), we introduce the proposed privacy-protected decentralized random sleep algorithm. This algorithm ensures privacy protection by incorporating conditional noise into the variables transmitted within the network, as per [36], while maintaining optimality. Additionally, the algorithm leverages a random sleep strategy to enhance computational efficiency, as suggested in [24]. Furthermore, the algorithm employs a row-stochastic matrix to rescale the gradient with an auxiliary variable, mitigating the imbalance caused by directed networks.

Before presenting the proposed algorithm, we describe the random sleep strategy. This strategy introduces a novel approach to improving computational efficiency. Here, $\tilde{h}_i^t$ is a random variable that determines if generator $i$ is active at time $t \ge 0$. If $\tilde{h}_i^t = 1$, generator $i$ performs gradient updates at time $t$, otherwise, it only conducts local computations. Specifically, given $0 < \eta_i < 1$ for all $i \in \mathcal{V}$, $\mathbb{P}(\tilde{h}_i^t = 1) = \eta_i$ and $\mathbb{P}(\tilde{h}_i^t = 0) = 1 - \eta_i$. Additionally, we define $\breve{\eta} = \min_{i \in \mathcal{V}}\{\eta_i\}$ and $\hat{\eta} = \max_{i \in \mathcal{V}}\{\eta_i\}$.

The proposed privacy-protected decentralized random sleep algorithm at each generator $i$ is summarized in Algorithm 1. The detailed steps are as follows: at each time $t$, each generator $i$ independently generates a Bernoulli random variable $\tilde{h}_i^t$.

**Algorithm 1** Privacy-protected decentralized random sleep algorithm at each generator $i \in \mathcal{V}$.

1: **Initialization:** Each generator $i$ starts with $y_i^0 \in \mathbb{R}_{\ge 0}, z_i^0 = e_i \in \mathbb{R}^m, v_i^0 = \sum_{j=1}^m b_{ij} y_j^0 \in \mathbb{R}_{\ge 0}$, and $p_i^0 \in \mathbb{R}_{\ge 0}$.
2: **for** $t=0, 1, 2, ...$ **do**
3: Independently and identically generate a Bernoulli random variable $\tilde{h}_i^t$;
4: Perform the random sleep strategy for optimization:
$$
y_i^{t+1} = \begin{cases} 
v_i^t + \epsilon_i^t - \gamma_i^t \frac{p_i^t - d_i}{[z_i^t]_i}, & \text{if } \tilde{h}_i^t = 1, \\ 
v_i^t + \epsilon_i^t, & \text{if } \tilde{h}_i^t = 0, 
\end{cases}
$$ (8.7)
where $\epsilon_i^t \in \mathbb{R}$ is an arbitrary noise chosen in $[-\hat{\epsilon}^t, \hat{\epsilon}^t]$, $\gamma_i^t$ is a local step-size, and $[z_i^t]_i$ represents the $i$th entry of vector $z_i^t$.
5: Perform dynamic average consensus as:
$$
v_i^{t+1} = \sum_{j=1}^m b_{ij} y_j^{t+1}, \quad z_i^{t+1} = \sum_{j=1}^m b_{ij} z_j^t,
$$ (8.8)
where $b_{ij}$ is the weight between $i$ and $j$.
6: Perform the local update of the primal variable as:
$$
p_i^{t+1} = \min\{\max\{\nabla J_i^{-1}(v_i^{t+1}), p_i^{\min}\}, p_i^{\max}\}. \quad (8.9)
$$
7: **end for**

Then, each generator $i$ applies the random sleep strategy described in (8.7) to obtain the dual-related variable $y_i^{t+1}$, adding an arbitrary noise $\epsilon_i^t$. After updating $y_i^{t+1}$, each generator $i$ calculates the dual variable $v_i^{t+1}$ and the auxiliary variable $z_i^{t+1}$ via dynamic average consensus as per (8.8). Subsequently, each generator $i$ updates the local primal variable $p_i^{t+1}$ using (8.9). The algorithm terminates after a predefined number of iterations.

In Algorithm 1, the local step-size $\gamma_i^t$, for $i \in \mathcal{V}$, diminishes according to the relative frequency of updates by generator $i$, defined as $\gamma_i^t = 1/\Gamma_i^t$, where $\Gamma_i^t$ represents the number of updates performed by generator $i$ up to time $t$ [43]. Moreover, the bound ($\hat{\epsilon}^t$) of conditional noise adheres to the following conditions [36]: (i) $\lim_{t \to \infty} \hat{\epsilon}^t / (t^2) = 0$, for all $t \ge 0$ and $i \in \mathcal{V}$; (ii) $0 < \hat{\epsilon}^t \le \hat{\epsilon}^s$, for all $0 \le s < t$. The matrix $B = [b_{ij}] \in \mathbb{R}^{m \times m}$ collects the weights $b_{ij}, i, j \in \mathcal{V}$, corresponding to the network $\mathcal{G}$, subject to the conditions:

$$
b_{ij} = \begin{cases} 
> \varrho, & j \in \mathcal{N}_i^{\text{in}}, \\ 
0, & \text{otherwise,} 
\end{cases} \quad \sum_{j=1}^m b_{ij} = 1, \forall i \in \mathcal{V} \quad (8.10)
$$

and $b_{ii} = 1 - \sum_{j \in \mathcal{N}_i^{\text{in}}} b_{ij} > \varrho, \forall i \in \mathcal{V}$, where $0 < \varrho < 1$. Here, the matrix $B$ is row-stochastic as verified.

Essentially, $-(p_i^t - d_i)$ in (8.7) is the gradient of $Q_i(y)$ at $y = v_i^t$, i.e., $\nabla Q_i(v_i^t) = d_i - p_i^t, i \in \mathcal{V}$. It is notable that this gradient term is combined with conditional noise, unlike the precise gradient in [25–27], presenting a challenge in proving the convergence of Algorithm 1. Furthermore, the random sleep strategy in (8.7) indicates that each generator need not compute the inexact gradient term when updating $y_i^t$, potentially reducing computation cost. Moreover, (8.7) represents a decentralized inexact gradient ascent step, with the gradient scaled by $[z_i^t]_i$, updated through (8.8). The update of $z_i^t$ in (8.8) is a consensus step designed to address the imbalance caused by the left normalized Perron eigenvector $c = [c_1, ..., c_m]^\mathsf{T} (1_m^\mathsf{T} c = 1)$, associated with the eigenvalue 1 of matrix $B$. This step is similar to those used in [24,37,38]. Lastly, Algorithm 1 avoids using any global parameters, enabling fully decentralized implementation.

From the above analysis, Algorithm 1 achieves the following advantages under the condition of accurate convergence: (i) Protection of sensitive information; (ii) Enhanced computational efficiency; (iii) Applicability to unbalanced directed networks.

**Remark 8.3.** Over the past decade, some effective metaheuristic algorithms [59,60] have been applied to solve the EDP, yielding better performance with complex cost functions or constraints. However, these metaheuristic algorithms do not guarantee convergence to the global optimal solution, which can only be achieved by comparing the costs of all feasible solutions. In contrast to these algorithms [59,60], the proposed algorithm can rigorously be proven to converge to the global optimal solution of the EDP without additional comparisons, thus avoiding resource consumption. Furthermore, most metaheuristic algorithms, which primarily rely on centralized control, may fail if one or more control signal links are disrupted. The proposed algorithm is robust to such scenarios with decentralized control.
