interval \(\hat{x} = (x_i - c_i) \in [-3, 3]\) (the function remains unchanged for the other interval), we approximate \((x_i - c_i)^2\) using the polynomial function \(P(\hat{x}) = \frac{1}{2}(\hat{x} - 12) + \frac{5}{4}|\hat{x} + \frac{3}{2}| + \frac{3}{4}|\hat{x} + \frac{1}{2}| + \frac{3}{4}|\hat{x}| + \frac{5}{4}|\hat{x} - 1| + |\hat{x} - \frac{5}{2}|\). Then, the simulation results are presented in Fig. 1.5, which demonstrates that Algorithm 1 also achieves comparable convergence results even when utilizing these approximate convex functions.

![](bbox=[0.16, 0.225, 0.76, 0.415])

**FIGURE 1.5**
The convergence of Algorithm 1. (a): Convergence of the primal variable \(x\). (b): Optimal resource allocation.

**Remark 1.7.** We highlight that while there is a marginal dip in performance in comparison to the approach outlined in [31], Algorithm 1 introduces a novel approach by employing the epigraph strategy to address the imbalance arising from directed networks. This distinctive methodology has yet to be integrated into current methods for handling resource allocation challenges in directed networks.

# **1.6.1.2 Example 2: simulation on time-varying directed networks**

In this example, we are concerned with a network consisting of \(n = 10\) nodes that communicate via time-varying directed networks. To construct these networks, we initially create a strongly connected graph \(\mathcal{G}\) and subsequently divide it into two distinct topologies (designated as topology 1 and topology 2, as depicted in Fig. 1.6) to ensure neither is strongly connected. We then assume that the nodes’ communication network alternates periodically between these two topologies. Additionally, we assume a total of \(K = 20\) resources, with each node having a local demand of \(r_i = 2\) resources. The optimal estimator \(x_i\) for each node is constrained to lie within the interval [0.5, 4]. Moreover, a random sleep probability of 0.5 is set for this example. Akin to Example 1, we evaluate Algorithm 2 in two aspects: its convergence properties and overall performance.

Subsequently, the results of the simulations are presented in Figs. 1.7 and 1.8, highlighting the convergence properties and efficiency of Algorithm 2. As depicted in Fig. 1.7, Algorithm 2 is capable of achieving the optimal allocation for the decentralized resource allocation challenge, even when employing a random sleep protocol,