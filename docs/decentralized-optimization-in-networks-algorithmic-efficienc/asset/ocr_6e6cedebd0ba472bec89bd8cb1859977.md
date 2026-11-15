algorithm has strict requirements for the matrix \( W \), which may not always be practical compared to algorithms using column-stochastic matrices in unbalanced directed networks. To address this issue, [27] proposed a decentralized dual averaging push algorithm, incorporating the push-sum averaging protocol, detailed as follows for each \( i \in \mathcal{V} \) :

```
\(\left\{\begin{array}{ c }
h_i(k + 1) = \sum_{j=1}^v P_{ij}(k)h_j(k) + g_i(k), \\ \\
q_i(k + 1) = \sum_{j=1}^v P_{ij}(k)q_j(k), \\ \\
x_i(k + 1) = \Pi_{\Omega}^{w} [\frac{h_i(k+1)}{q_i(k+1)}, \gamma(k)], \\
\end{array}\right.\)
```

where \( q_i(k) \) is an auxiliary variable. This algorithm has been considered in this chapter. However, it does not address the privacy concerns of nodes in the network, which is critical when data is being continuously transmitted. Although recent research [37] has considered using differential privacy strategies to achieve this goal, it leads to inexact convergence of the algorithm, deviating from our initial objectives. This motivates us to develop an effective algorithm that not only protects node privacy but also accurately converges to the optimal solution of problem (7.1) over time-varying directed networks. This is the primary motivation for the next subsection.

> **Remark 7.2.** The push-sum protocol is the most commonly used method to address the imbalance caused by time-varying directed networks and has been proven to be efficient and practical in numerous studies, such as [11,26–28,31,36]. The decentralized dual averaging push algorithm integrates the push-sum protocol into the decentralized dual averaging method, making it effective for solving general constrained optimization problems over time-varying directed networks.

# ## 7.3.2 Privacy-protected decentralized dual averaging push algorithm

It is important to note that not all nodes in the network are benign; some may be malicious. While adhering to the update rules, malicious nodes may intentionally gather information sent by normal nodes and collude to access local subgradients containing critical data about the local cost functions of normal nodes. Additionally, frequent information transmission among nodes can lead to privacy exposure. Therefore our aim is to ensure all nodes in the network can accurately agree on the optimal solution while safeguarding the private information of normal nodes.

Our algorithm operates as follows. At time \( k \), each node \( i \) maintains three local variables: a primal variable \( x_i(k) \in \Omega \), a state variable \( h_i(k) \in \mathbb{R}^d \), and an auxiliary variable \( q_i(k) \in \mathbb{R} \), initialized with \( x_I(1) \in \Omega \), \( h_I(1) \in \mathbb{R}^d \), and \( q_I(1) = 1 \). At time \( k \ge 1 \), each node \( i \) first utilizes a correlated perturbation mechanism inspired by