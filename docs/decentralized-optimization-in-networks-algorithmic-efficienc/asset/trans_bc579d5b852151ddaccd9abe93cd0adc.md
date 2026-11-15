

superscript \((\cdot)^\text{T}\) stands for the transpose of a vector or matrix. Let \(\partial f(y)\) represent the subdifferential of \(f\) evaluated at \(y \in \mathbb{R}^n\). The non-negative component of \(f(y)\) is denoted by \([f(y)]_+ = \max\{0, f(y)\}\). We use the abbreviation “a.s.” for “almost surely”. Unless specified otherwise, all directed networks mentioned in this chapter are presumed to be unbalanced.

## 1.2 问题描述

### 1.2.1 问题描述

The chapter aims to solve a decentralized resource allocation challenge over a directed network comprised of \(n\) interconnected nodes, as outlined below:

\(\begin{aligned} \min_x C(x) &= \sum_{i=1}^n C_i(x_i), \qquad \text{(1.1a)} \\ \text{s.t. } \sum_{i=1}^n x_i &= \sum_{i=1}^n r_i = K, \qquad \text{(1.1b)} \\ x_i \in \Omega_i, \quad \forall i &= 1, \dots, n, \qquad \text{(1.1c)} \end{aligned}\)

where \(x = [x_1, x_2, \dots, x_n]^T \in \mathbb{R}^n\) denotes the optimal estimator and \(x_i \in \mathbb{R}\) signifies the quantity of resources assigned to node \(i\). The function \(f_i : \mathbb{R} \rightarrow \mathbb{R}\) portrays the convex cost associated with resource \(x_i\), while \(\Omega_i \subseteq \mathbb{R}\) represents a non-empty, closed, and convex set, unique to node \(i\). The equality constraints, \(\sum_{i=1}^n x_i = \sum_{i=1}^n r_i = K\) serve to interlink the decisions of the nodes, with \(K \in \mathbb{R}\) being the fixed total resources and \(r_i \in \mathbb{R}\) representing the local, virtual demand for resources at node \(i\). Here, we define \(\Omega\) as the Cartesian product of the individual sets \(\Omega_i\), i.e., \(\Omega = \Omega_1 \times \cdots \times \Omega_n\), and we refer to the feasible set of (1.1) as \(\mathcal{D} = \{x \in \Omega | \sum_{i=1}^n x_i = K\}\).

In this context, we have the optimal estimator designated as \(x = [x_1, \dots, x_n]^T \in \mathbb{R}^n\), where \(x_i \in \mathbb{R}\) signifies the allocated resources for node \(i\). Each convex function \(f_i : \mathbb{R} \rightarrow \mathbb{R}\) encapsulates the cost associated with the resource \(x_i\), while the set \(\Omega_i \subseteq \mathbb{R}\) denotes a specific, non-empty, closed, and convex subset for node \(i\). The equality constraints, given by \(\sum_{i=1}^n x_i = \sum_{i=1}^n r_i = K\), serve to synchronize the decisions among nodes, where \(K \in \mathbb{R}\) represents the fixed total resource quantity, and \(r_i \in \mathbb{R}\) represents the localized, virtual resource demand for node \(i\). Here, \(\Omega\) stands for the Cartesian product of the individual sets \(\Omega_i\), expressed as \(\Omega = \Omega_1 \times \cdots \times \Omega_n\), and the feasible set of (1.1) is designated as \(\mathcal{D} = \{x \in \Omega | \sum_{i=1}^n x_i = K\}\).

The transmission of information between nodes can be envisioned as a directed network, labeled $\mathcal{G} = \{\mathcal{V}, \mathcal{E}\}$, which comprises the set of nodes $\mathcal{V} = \{1, 2, ..., n\}$ and the set of edges $\mathcal{E} \subseteq \mathcal{V} \times \mathcal{V}$. When node \(j\) is capable of directly transmitting data to node \(i\), the edge \((j, i)\) belongs to \(\mathcal{E}\), with \(j\) considered an inbound neighbor for \(i\), and conversely, \(i\) is an outbound neighbor of \(j\). The set of inbound neighbors for node \(i\) is defined as $\mathcal{N}_i^{\text{in}} = \{j \in \mathcal{V} | (j, i) \in \mathcal{E}\}$, and similarly, the set of outbound neighbors $\mathcal{N}_i^{\text{out}}$ is delineated. A network is considered unbalanced if the inbound degree of a node \(i\) does not match its outbound degree. The directed network $\mathcal{G}$ is deemed strongly connected if a directed path exists between any two nodes. Furthermore, the key findings of this chapter are grounded on the assumption outlined below [7,28].

**Assumption 1.1.** The mapping \(C_i : \mathbb{R} \to \mathbb{R}\) for all \(i \in \mathcal{V}\) is well-defined, closed-valued, and strictly convex, and the set \(\mathcal{D}\) of admissible solutions is non-vacuous.

Drawing upon Assumption 1.1, we can deduce that (1.1) is indeed a convex optimization problem, possessing a singular vector \(x^* = [x_1^*, x_2^*, ..., x_n^*]^T\) within the domain \(\mathbb{R}^n\) that attains the minimal value of the problem (1.1).

### 1.2.2 A motivating example

Problem (1.1) revolves around the issue of resource allocation, where diverse individual variables associated with nodes are interconnected through equality constraints while adhering to specific localized restrictions. It is noteworthy that problems of the form (1.1) arise in numerous engineering scenarios, such as the decentralized economic dispatch problems (EDPs) encountered in power systems [10,33,34,36], the decentralized channel allocation problems in wireless communication networks [9], etc. Here, we present a motivating practical application that aligns with the problem (1.1).

**Example 1:** The focal point of decentralized economic dispatch problems (EDPs) lies in minimizing the overall generation cost, while fulfilling the aggregate load demand and adhering to the output constraints of individual generators. Here, we explore a network comprising \(n\) generators interconnected through directed networks. In this framework, the local variable \(x_i\) in problem (1.1) represents the power output of generator \(i\). Consequently, generator \(i\) incurs a cost \(C_i : \mathbb{R} \to \mathbb{R}\) when producing \(x_i\) power, typically adhering to Assumption 1.1. Therefore the total cost \(C\) of the network can be expressed as \(C(x) = \sum_{i=1}^n C_i(x_i)\), which aligns with (1.1a). Notably, EDPs prioritize the balance of the entire network, rather than the power balance of individual generators. To this end, the aggregate power output must match the total load of the network, expressed as a positive constant \(K\), satisfying \(\sum_{i=1}^n x_i = K\), which is (1.1b). Furthermore, it is realistic to assume that each generator \(i\) has a limited power output range, \(x_i \in \Omega_i = \{\hat{x} | x_{i,\min} \leq \hat{x} \leq x_{i,\max}\}\), captured by the constraints (1.1c) for all \(i\). Here, \(x_{i,\min}\) and \(x_{i,\max}\) denote the minimum and maximum power generation capacities. Additionally, in a practical power system, each generator only communicates its own information to neighboring generators without requiring feedback, rendering the communication network directional. However, long-term operation of power systems often results in link failures or partial generator malfunctions, potentially leading to variations in the communication network due to maintenance requirements. Taking this into account, the communication network may vary over time. Given the aforementioned interpretation, it is evident that the optimization problem (1.1) can serve as a modeling framework for capturing the effective demand profiles (EDPs) of actual power systems.

### 1.2.3 Dual decomposition

Analogous to previous studies [28,31,34], the optimization problem (1.1) can be rephrased as a dual problem focused on the equality constraint (1.1b), and subsequently resolved using decentralized optimization methods. Initially, the Lagrangian function, represented as \( L : \Omega \times \mathbb{R} \rightarrow \mathbb{R} \), is introduced and defined as follows:

\( L(x, y) = \sum_{i=1}^n C_i(x_i) - y \sum_{i=1}^n (x_i - r_i), \quad (1.2) \)

where \( y \in \mathbb{R} \) denotes the Lagrangian multiplier. Consequently, the dual counterpart of the optimization problem (1.1) can be articulated in the following manner:

\(\max_{y \in \mathbb{R}} Q(y) = \sum_{i=1}^n Q_i(y), \quad (1.3)\)

where each \( Q_i(y) \) represents a concave function, as detailed in [31], which can be characterized as

\( Q_i(y) = \min_{x_i \in \Omega_i} C_i(x_i) - y(x_i - r_i), i \in \mathcal{V}, \quad (1.4) \)

and \( Q(y) \) may lack differentiability. Assuming that for any \( y, \tilde{x}_i(y), i \in \mathcal{V} \) serves as the minimizer of (1.4), the subdifferential of \( Q(y) \) then takes the form of

\(\partial Q(y) = - \sum_{i=1}^n (\tilde{x}_i(y) - r_i), \quad (1.5)\)

and \(\partial Q_i(y) = -(\tilde{x}_i(y) - r_i), \forall i \in \mathcal{V}\). Here, it is important to clarify that the local demand of resource \( r_i \in \mathbb{R} \) is a hypothetical value for each \( i \in \mathcal{V} \) and is arbitrary. This ensures that the condition \(\sum_{i=1}^n r_i = K\) is satisfied. These hypothetical resource demands do not have a physical interpretation and can be set in various ways, such as \( r_i = K/n, \forall i \in \mathcal{V} \). Furthermore, based on Assumption 1.1, we can infer that a strong duality exists between (1.1) and (1.3) [28,31]. This implies that the set of dual optimal solutions for (1.3) is non-empty (see Proposition 6.4.2 of [35]). In other words, there exists at least one dual optimal solution \( y^* \) to (1.3) that satisfies \( C(x^*) = Q(y^*) \).

