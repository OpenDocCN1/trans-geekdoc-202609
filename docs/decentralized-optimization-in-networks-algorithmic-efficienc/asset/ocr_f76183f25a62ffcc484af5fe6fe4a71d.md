![](bbox=[0.21, 0.11, 0.84, 0.55])

**FIGURE 1.1**
The convergence of Algorithm 1. (a): Convergence of the primal variable x. (b): Optimal resource allocation. (c): Convergence of the dual variable y. (d): Convergence of the auxiliary variable k.

for all nodes \(i = 1, ..., 5\). Fig. 1.1(d) further shows that the auxiliary variable \(k_i^t\) converges to the optimal value for each individual function \(J_i\), where \(i\) ranges from 1 to 5. Moreover, Fig. 1.1 validates the effectiveness of the epigraph strategy in handling the imbalance caused by directed networks in the decentralized resource allocation problem.

+   2) Comparisons for the convergence rate and the communication cost: In this simulation, we undertake a comparative analysis of Algorithm 1 with a related decentralized method presented in [31], as well as a variant of Algorithm 1 that excludes the gossip-based communication protocol. For the purpose of comparison, we utilize the residual \((1/n)\log_{10}(\mathbb{E}[\sum_{i=1}^n \|x_i^t - x^*\|])\) as the evaluation metric. The outcomes of this comparison are depicted in Fig. 1.2, which displays the iterations and the total number of communications across the entire network on the x-axis. Fig. 1.2(a) reveals that Algorithm 1 exhibits a comparable sublinear convergence rate to the