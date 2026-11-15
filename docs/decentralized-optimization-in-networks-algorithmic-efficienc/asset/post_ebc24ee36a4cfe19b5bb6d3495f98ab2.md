

Moreover, we formulate the following minimization problem, which is derived from the dual problem (1.3):

```
\min_{y \in \mathbb{R}} J(y) = \sum_{i=1}^n J_i(y),
(1.6)
```

where \(J_i(y) = -Q_i(y)\) represents a convex function for each \(i \in \mathcal{V}\) [36]. It is noteworthy that the set of optimal solutions for problem (1.6) coincides with that of (1.3).

**Remark 1.1.** Currently, various decentralized algorithms have been introduced to solve the minimization problem (1.6) over directed networks, such as Perron vector-inspired algorithms [7,31], push-sum approaches [19,28], and surplus-based methods [37]. Nonetheless, when it comes to the context of row-stochastic mixing matrices, the aforementioned algorithms [7,19,28,31,37] falter in addressing the imbalance stemming from the directed networks discussed in this chapter, specifically those utilizing the gossip communication protocol or exhibiting temporal variations.

### 1.2.4 An epigraph form of problem (1.6)

Distinct from the approaches mentioned in [7,8,22,28,31], the epigraph strategy offers a novel perspective to resolve the imbalance arising from directed networks in (1.6). This unique strategy has yet to find its application in current methods aimed at resolving resource allocation issues within directed networks. More precisely, the epigraph of the function \(J(y) : \mathbb{R} \to \mathbb{R}\) is characterized as detailed in [24,25,32]:

```
\text{epi } J = \{(y, k)|y \in \text{dom}(J), J(y) \le k\},
(1.7)
```

which is a particular segment within the space \(\mathbb{R}^2\). Drawing from the reference [38], we deduce that the epigraph of \(J\) constitutes a convex set, owing to the convex nature of \(J\), as mentioned in the preceding subsection. As a result, minimizing \(J\) amounts to identifying the smallest value of the auxiliary variable \(k\) within its epigraph. Given this framework, we restructure the minimization problem (1.6), whose objective function is a summation of locally convex functions, into an epigraph-based format for facilitation of a solution. By utilizing auxiliary variables to delineate the upper limit of the local objective function, the current objective function is transformed into a singular linear function comprising these auxiliary variables, while the previous local objective function is converted into local constraints.

Given the auxiliary variable \(k \in \mathbb{R}^n\), we now examine the epigraph representation of (1.6). Drawing from the previous deliberations, problem (1.6) can be precisely rephrased in the following manner:

```
\min_{(y,k) \in \mathfrak{S}} \sum_{i=1}^n 1_n^T k, \text{ s.t. } J_i(y) - e_i^T k \le 0, \forall i \in \mathcal{V},
(1.8)
```

where \(k = [k_1, ..., k_n]^T \in \mathbb{R}^n\) and \(\mathfrak{S} = \mathbb{R} \times \mathbb{R}^n\) is the Cartesian product of \(\mathbb{R}\) and \(\mathbb{R}^n\).

It is worth observing that the rephrased epigraph formulation offers a robust solution to the imbalance issue that plagued the communication environment discussed in this chapter, simply by incorporating an additional inequality constraint. As a result, in the upcoming section, we shall introduce an innovative decentralized asynchronous algorithm tailored specifically to tackle the revised problem (1.8). This algorithm boasts a fully decentralized implementation while also minimizing communication overheads.

## 1.3 Algorithm construction

Drawing upon the principles of dual decomposition and the epigraph transformation discussed in the previous section, this section introduces a novel decentralized asynchronous algorithm, coupled with the gossip communication protocol, to solve the resource allocation problem (1.1).

### 1.3.1 Gossip-based communication protocol

Prior to delving into the proposed algorithm, let us first acquaint ourselves with the gossip-based communication protocol. Essentially, this protocol facilitates node j to disseminate its estimates to node i by probabilistically activating a directed edge (j, i) within the strongly connected directed network G during each iteration. This approach ensures robust consensus attainment through sparse communication exchanges.

The gossip-based communication protocol adheres to a similar asynchronous time model as outlined in [26,27,39]. Each node is equipped with a local Poisson clock that ticks at a rate of 1, effectively serving as a virtual clock. Whenever any local clock ticks, the global virtual clock is considered to tick as well, conforming to a Poisson process with a rate of n. We define Z^t as the absolute time corresponding to the t-th tick of the global Poisson clock. Time is discretized into intervals [Z^(t-1), Z^t), representing discrete-time t. At time t, node i^t wakes up (or transmits information to a chosen outgoing neighbor) and selects an outgoing neighbor j^t for communication. The selection of j^t follows a non-negative stochastic vector κ_i, that aligns with the network G = {V, E}. Specifically, κ_ji > 0 is positive only when there exists a directed edge (i, j) in the network. For the sake of simplicity, we typically assume a directed network structure.

Assumption 1.2.
- (i) The directed network G possesses the property of strong connectivity, guaranteeing that there exists a path from any node to any other node in the network. The corresponding weighted matrix Υ = [wij] ∈ R^(n×n) is comprised of non-negative elements.
- (ii) The in-neighbor selection process exhibits independence and identical distribution. Specifically, at any given time, node j is chosen by its in-neighbor i ∈ N_j^in with a probability κ_ji > 0, provided that i is indeed an in-neighbor of j (κ_ji = 0 if i ∉ N_j^in). This selection occurs independently of the other selections made at that time.

Assumption 1.2 is crucial as it facilitates the dissemination of information within the network. Under this assumption, the gossip-based communication protocol ensures that the information of each node can propagate to other nodes, either directly or indirectly, via the independent and identical in-neighbor selection process. This connectivity enables the nodes’ estimations to converge to a shared solution, a key requirement for achieving consensus in the network.

### 1.3.2 Decentralized asynchronous algorithm

For any non-negative \( t \), we shall define three localized estimates pertaining to node \( i \) as \( x_i^t \in \mathbb{R} \), \( y_i^t \in \mathbb{R} \), and \( k_i^t \in \mathbb{R}^n \). These estimates originate from initial values of \( x_i^0 \in \mathbb{R} \), \( y_i^0 \in \mathbb{R} \), and \( k_i^0 \in \mathbb{R}^n \). Subsequently, the proposed decentralized asynchronous algorithm comprises the following sequential procedures.

**Step 1 (Consensus on the dual variable):** Except for the node \( j^t \), no other nodes update for \( t \ge 1 \), i.e.,

```
\( v_i^t = y_i^{t-1}, u_i^t = k_i^{t-1}, \forall i \neq j^t, \)
```

where \( v_i^t \) and \( u_i^t \) are two interim state variables. For \( t \ge 1 \), node \( j^t \) computes the weighted values of their respective estimations adhering to the subsequent rules:

```
\( v_{j^t}^t = w_{i^t j^t} y_{j^t}^{t-1} + (1 - w_{i^t j^t}) y_{i^t}^{t-1}, \quad u_{j^t}^t = w_{i^t j^t} k_{j^t}^{t-1} + (1 - w_{i^t j^t}) k_{i^t}^{t-1}, \)
```

where \( w_{i^t j^t} \) denotes the weight from node \( j^t \) to node \( i^t \) in the directed network \( \mathcal{G} \).

**Step 2 (Optimization on the primal variable):** Node \( i \) proceeds to update \( x_i^t \) in accordance with the subsequent rules:

```
\( x_i^t = \arg \min_{x_i \in \Omega_i} C_i(x_i) - v_i^t(x_i - r_i), \)
```

where (1.11) represents the primal update step of Lagrangian methods, pertaining to the primal variable, for the purpose of solving (1.4).

**Step 3 (Optimization on the dual variable):** Adhering to the aforementioned scheme, nodes \( i^t \) and \( j^t \) initially address the unconstrained optimization problem, which involves bypassing the constraints outlined in (1.8). They achieve this by employing the decentralized subgradient descent technique, a widely used approach. As a result, they derive an intermediate state variable, labeled \( z_i^t \), which aligns with \( k_i^t \), i.e., for \( i \in \{i^t, j^t\} \),

```
\( z_i^t = u_i^t - \alpha_i^t \mathbf{1}_n, \)
```

where \( \alpha_i^t \) is a step-size of node \( i \). Employing \( \alpha_i^t \), nodes \( i^t \) and \( j^t \) proceed to update the variables \( y_i^t \) and \( k_i^t \). This update process incorporates Polyak’s projection methodology, designed to handle the inequality constraint in (1.8), i.e., for \( i \in \{i^t, j^t\} \),

```
\( y_i^t = v_i^t - \frac{[J_i(v_i^t) - e_i^{\text{T}} z_i^t]_+}{1 + \|a_i^t\|^2} a_i^t, \)
```

