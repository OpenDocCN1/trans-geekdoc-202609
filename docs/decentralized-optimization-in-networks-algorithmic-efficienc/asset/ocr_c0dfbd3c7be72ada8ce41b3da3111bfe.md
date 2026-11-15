[39,40] to generate a series of correlated random noises $\{\tau_{ji}(k)\}_{j \in \mathcal{N}_i^{\text{out}}(k)}$ and calculates the noise $\tau_{ii}(k)$ as follows:

\(\tau_{ii}(k) = - \frac{\sum_{j \in \mathcal{N}_i^{\text{out}}(k)} P_{ji}(k) \tau_{ji}(k)}{P_{ii}(k)}.\) (7.3)

Then, the state variable \(h_i(k)\) is perturbed by the correlated random noises \(\tau_{ji}(k)\), \(j \in \mathcal{N}_i^{\text{out}}(k)\), i.e.,

\(\tilde{h}_{ji}(k) = h_i(k) + \tau_{ji}(k).\) (7.4)

Node \(i\) then transmits \(P_{ji}(k)\tilde{h}_{ji}(k)\) and \(P_{ji}(k)q_i(k)\) to its out-neighbors \(j \in \mathcal{N}_i^{\text{out}}(k)\). Upon receiving \(P_{ij}(k)\tilde{h}_{ij}(k)\) and \(P_{ij}(k)q_j(k)\) from its in-neighbors \(j \in \mathcal{N}_i^{\text{in}}(k)\), node \(i\) aggregates the information and updates its state variable \(h_i(k+1)\) (by accumulating the subgradient \(g_i(k) \in \partial f_i(x_i(k))\)) and auxiliary variable \(q_i(k+1)\) as follows:

\(h_i(k+1) = \sum_{j=1}^v P_{ij}(k)\tilde{h}_{ij}(k) + g_i(k),\) (7.5a)
\(q_i(k+1) = \sum_{j=1}^v P_{ij}(k)q_j(k).\) (7.5b)

Using the projection operator \(\Pi_\Omega^\varphi(\cdot)\), the primal variable \(x_i(k+1)\) is obtained. Finally, each node \(i\) calculates its local average \(\hat{x}_i(k)\) (local estimated optimal solution). The detailed update process, at time \(t \ge 1\), is as follows:

\(x_i(k+1) = \Pi_\Omega^\varphi(\frac{h_i(k+1)}{q_i(k+1)}, \gamma(k)),\) (7.6)

where \(\gamma(k) > 0\) is a decreasing step-size specified in the following section. We summarize the above in Algorithm 1.

The noises in the network comply with the following condition:

\(\sum_{j=1}^v P_{ji}(k)\tau_{ji}(k) = 0,\) (7.7)

where \(\tau_{ji}(k)\) equals 0 if node \(j\) is not part of the set \(\mathcal{N}_i^{\text{out}}(k) \cup i\). Due to the edge-based and locally balanced nature of the added noises, as expressed in (7.7), nodes in the network are not required to coordinate in generating the noises, offering more flexibility in noise design compared to node-based methods in [35,43]. Additionally, the noises \(\tau_{ji}(k)\), for \(j \in \mathcal{N}_i^{\text{in}}(k)\), can be chosen such that

\(\tau_{ji}(k) \in [-\eta\delta_i/d, -\eta\delta_i/d]^d, \forall i \in \mathcal{V},\)