# 5.6 Simulation examples

In this section, we employ Algorithms 1 and 2 to address the decentralized online localization challenge, as referenced in [23,26,33]. This is done to affirm the theoretical findings through the utilization of sensor networks, wherein interactions among sensors (nodes) are typically directional.

In this simulated scenario, we utilize a dynamic and directed network consisting of \(n=20\) nodes, generated according to the Erdos–Renyi model [53] with a connection likelihood of \(p_c = 0.8\). Each node within the network is tasked with estimating a vector \(x\) belonging to the set \(\Omega\). Given the presence of noise, every node \(i\) in the set \(\mathcal{V}\) acquires an uncertain and evolving observation vector \(q_{i,k}\) from the space \(\mathbb{R}^{m_i}\). This vector is progressively identified by node \(i\) as time \(k\) progresses. Let us assume that each node \(i\) in \(\mathcal{V}\) possesses a linear model represented by \(P_i(x) = P_i x\), where \(P_i\), an element of \(\mathbb{R}^{m_i \times m}\), serves as the observation matrix. A crucial aspect is that \(P_i x\) equals \(0_{m_i}\) if and only if \(x\) equals \(0_{m_i}\). The primary objective is to locate a vector \(\hat{x}\) within \(\Omega\) that best approximates \(x\) by minimizing the designated global loss function, described as follows:

```
$$f(\hat{x}) = \sum_{k=1}^K \sum_{i=1}^n \frac{1}{2} ||q_{i,k} - P_i \hat{x}||^2, \quad \text{s.t.} \quad \hat{x} \in \Omega,$$
```

where the observation vector for node \(i\) at time \(k\) is represented as \(q_{i,k} = P_i x + \beta_{i,k}\), where \(\beta_{i,k}\) signifies the observation noise, considered as white noise. It is important to note that the local loss function for each node changes over time due to the unpredictable nature of noise and the varying scenarios. Consequently, the optimal fixed estimation, denoted as \(x^*\) in hindsight, across a specified time period \(K\), is determined by

```
$$x^* = \frac{1}{K} \sum_{k=1}^K (\sum_{i=1}^n P_i^T P_i)^{-1} (\sum_{i=1}^n P_i^T q_{i,k}).$$
```

Next, we present two examples to demonstrate the effectiveness of Algorithm 1 and Algorithm 2, respectively.

# 5.6.1 The performance of Algorithm 1

Let \(n=20\) and \(m=m_i=2\). The observation made by node \(i\) at time \(k\) can be represented as \(q_{i,k} = t_{i,k} x + \varsigma_{i,k}\), where \(t_{i,k}\) and \(\varsigma_{i,k}\) are randomly chosen from a uniform distribution within \([0, 1]\) and \([-1, 1] \times [-1, 1]\) respectively. In this context, the symbol \(\times\) denotes the Cartesian product of two sets. Furthermore, we define \(\Omega\) as a subset of \([-5, 5] \times [-5, 5]\), set the matrix \(P_i\) equal to \(I_2\) for \(i=1, ..., 20\), and assign a step-size of \(\alpha_k = 1/(2\sqrt{k+1})\). Our current objective is to identify the best possible solution for the decentralized constrained online optimization problem through the application of Algorithm 1. This ensures that the overall operational loss incurred by the entire network is optimized.