

Observing the resemblance in properties between the results in (1.50) and (1.34), we shall omit the remaining details of the proof for Theorem 1.2 for brevity. \(\square\)

Adopting procedures akin to Corollaries 1.1–1.3 for error-bound and complexity analyses, we omit the details here for brevity.

## 1.6 Simulation examples

In this section, to verify the theoretical claims, we apply our proposed algorithms to decentralized resource allocation scenarios over both static and dynamic directed networks. The experiments are conducted on a laptop using Matlab® R2016b, with an Intel i7 – 8700 CPU @3.2 GHz, 8 GB RAM, and Windows 10 OS. We leverage the Matlab optimization toolbox to obtain optimal solutions, serving as a benchmark for comparing the performance of our algorithms.

### 1.6.1 Simulation on general resource allocation problems

Analogous to the method in [41], we postulate that the cost function (strictly convex) at node \(i\) within the set \(\{1, \dots, n\}\) is

\(C_i(x_i) = \log(1 + \exp(b_i(x_i - d_i))) + \frac{1}{2}a_i(x_i - c_i)^2,\)

where the coefficients \(a_i\), \(b_i\), \(c_i\), and \(d_i\) are randomly selected from the ranges \((0, 2]\), \([-2, 2]\), \([-3, 3]\), and \([-3, 3]\), respectively. To demonstrate the effectiveness of Algorithms 1 and 2, we present two examples based on distinct network configurations.

#### 1.6.1.1 Example 1: simulation on general directed networks

In this example, we focus on a network comprising \(n = 5\) nodes communicating through a directed cycle-like structure (imbalanced). It is worth noting that the gossip-based communication protocol limits information transmission to a single directed edge randomly activated at each iteration. As the number of edges in the network increases, so does the number of iterations required to traverse and activate all effective edges, ultimately achieving consensus. To mitigate redundant iterations, we adopt a directed cycle-like network for this simulation. Additionally, we assume a total resource pool of \(K = 10\), with each node requiring a local resource of \(r_i = 2\) for all \(i = 1, \dots, 5\). Each optimal estimator \(x_i\) is further constrained to fall within the interval \([1, 3]\). Our goal is to employ Algorithm 1 to determine the optimal resource allocation across all nodes, aiming to minimize the overall network operating cost while adhering to total resource and local constraints.

- 1) Convergence results: In this simulation, we evaluate the convergence properties of Algorithm 1, and the results are presented in Fig. 1.1. Specifically, Figs. 1.1(a) and 1.1(b) jointly demonstrate that Algorithm 1 is capable of achieving the optimal allocation despite employing a gossip-based communication protocol. Fig. 1.1(c) indicates that the dual variable \(y_i^t\) converges to a consensus value at the optimal solution for all nodes \(i = 1, ..., 5\). Fig. 1.1(d) further shows that the auxiliary variable \(k_i^t\) converges to the optimal value for each individual function \(J_i\), where \(i\) ranges from 1 to 5. Moreover, Fig. 1.1 validates the effectiveness of the epigraph strategy in handling the imbalance caused by directed networks in the decentralized resource allocation problem.

![](img/3cc494b92b35bef197b953dcaa648a44_44_0.png)

**FIGURE 1.1** The convergence of Algorithm 1. (a): Convergence of the primal variable x. (b): Optimal resource allocation. (c): Convergence of the dual variable y. (d): Convergence of the auxiliary variable k.

- 2) Comparisons for the convergence rate and the communication cost: In this simulation, we undertake a comparative analysis of Algorithm 1 with a related decentralized method presented in [31], as well as a variant of Algorithm 1 that excludes the gossip-based communication protocol. For the purpose of comparison, we utilize the residual \((1/n)\log_{10}(\mathbb{E}[\sum_{i=1}^n \|x_i^t - x^*\|])\) as the evaluation metric. The outcomes of this comparison are depicted in Fig. 1.2, which displays the iterations and the total number of communications across the entire network on the x-axis. Fig. 1.2(a) reveals that Algorithm 1 exhibits a comparable sublinear convergence rate to the

![](img/3cc494b92b35bef197b953dcaa648a44_45_0.png)

FIGURE 1.2 The comparison. (a): x-axis is the iterations. (b): x-axis is the number of communications.

method in [31], maintaining its performance even when utilizing the gossip-based communication protocol or the epigraph strategy. Fig. 1.2(b) highlights that, in comparison to the decentralized method from [31] and the variant of Algorithm 1 without the gossip-based communication, our proposed Algorithm 1 requires a significantly reduced number of communications, thereby lowering the communication cost to a considerable extent.

![](img/3cc494b92b35bef197b953dcaa648a44_45_1.png)

FIGURE 1.3 The comparison. (a): x-axis is the number of iterations. (b): x-axis is the convergence time (s).

- 3) Comparisons for the computational complexity and convergence time: In this simulation, we delve deeper into the performance of Algorithm 1, considering both nonuniform and uniform step-sizes, and compare it with the approach outlined in [31]. Our assessment uses a different residual measure as the benchmark: \((1/n)\log_{10}(\mathbb{E}[J^K - J^*])\). Fig. 1.3 provides a visual representation of the results, with the \(x\)-axis representing the number of iterations and convergence time (in seconds). Fig. 1.3(a) suggests that Algorithm 1 achieves a computational complexity comparable to that of the method in [31]. Specifically, to reach a residual of \(\mathbb{E}[J^K - J^*] = 10^{-2}\), Algorithm 1 requires 3883 iterations, while the uniform step-size variant demands 2478 iterations, and the method in [31] necessitates 1400 iterations. Fig. 1.3(b) reveals that, despite employing the gossip-based communication protocol, the convergence time of Algorithm 1 does not experience a significant increase compared to the decentralized method in [31]. Specifically, to achieve a residual of \(\mathbb{E}[J^K - J^*] = 10^{-2}\), the corresponding convergence times for Algorithm 1, its uniform step-size variant, and the method in [31] are 15.5322 s, 9.9210 s, and 3.5218 s, respectively.

![](img/3cc494b92b35bef197b953dcaa648a44_46_0.png)

**FIGURE 1.4** Impacts of the size of the network. (a): The performance of Algorithm 1 with the network containing different number of nodes. (b): Optimal resource allocation with the network containing different number of nodes.

- 4) Impacts of the size of the network: In this simulation, which utilizes the same relevant parameters as in Part 1, we investigate the influence of network size on the convergence outcomes of Algorithm 1. Specifically, we examine nodes communicating within directed, cycle-like network structures. The findings are depicted in Fig. 1.4. Fig. 1.4(a) reveals that as the number of nodes rises, the performance of Algorithm 1 may undergo some degradation due to the utilization of a gossip-based communication protocol. However, Fig. 1.4(b) demonstrates that Algorithm 1 still attains optimal allocation despite the presence of more nodes in these directed, interconnected networks. This observation underscores the robustness of Algorithm 1 to variations in network size.

- 5) The performance results on general cost functions: In this simulation, we assess the effectiveness of Algorithm 1 when using approximate convex functions. Specifically, we employ a polygonal function \(P(\cdot)\) based on predefined partitions to approximate the quadratic terms \((x_i - c_i)^2\) in the cost function \(C_i(x_i)\). For the interval \(\hat{x} = (x_i - c_i) \in [-3, 3]\) (the function remains unchanged for the other interval), we approximate \((x_i - c_i)^2\) using the polynomial function \(P(\hat{x}) = \frac{1}{2}(\hat{x} - 12) + \frac{5}{4}|\hat{x} + \frac{3}{2}| + \frac{3}{4}|\hat{x} + \frac{1}{2}| + \frac{3}{4}|\hat{x}| + \frac{5}{4}|\hat{x} - 1| + |\hat{x} - \frac{5}{2}|\). Then, the simulation results are presented in Fig. 1.5, which demonstrates that Algorithm 1 also achieves comparable convergence results even when utilizing these approximate convex functions.

![](img/3cc494b92b35bef197b953dcaa648a44_47_0.png)

**FIGURE 1.5** The convergence of Algorithm 1. (a): Convergence of the primal variable \(x\). (b): Optimal resource allocation.

**Remark 1.7.** We highlight that while there is a marginal dip in performance in comparison to the approach outlined in [31], Algorithm 1 introduces a novel approach by employing the epigraph strategy to address the imbalance arising from directed networks. This distinctive methodology has yet to be integrated into current methods for handling resource allocation challenges in directed networks.

#### 1.6.1.2 Example 2: simulation on time-varying directed networks

In this example, we are concerned with a network consisting of \(n = 10\) nodes that communicate via time-varying directed networks. To construct these networks, we initially create a strongly connected graph \(\mathcal{G}\) and subsequently divide it into two distinct topologies (designated as topology 1 and topology 2, as depicted in Fig. 1.6) to ensure neither is strongly connected. We then assume that the nodes’ communication network alternates periodically between these two topologies. Additionally, we assume a total of \(K = 20\) resources, with each node having a local demand of \(r_i = 2\) resources. The optimal estimator \(x_i\) for each node is constrained to lie within the interval [0.5, 4]. Moreover, a random sleep probability of 0.5 is set for this example. Akin to Example 1, we evaluate Algorithm 2 in two aspects: its convergence properties and overall performance.

Subsequently, the results of the simulations are presented in Figs. 1.7 and 1.8, highlighting the convergence properties and efficiency of Algorithm 2. As depicted in Fig. 1.7, Algorithm 2 is capable of achieving the optimal allocation for the decentralized resource allocation challenge, even when employing a random sleep protocol,

