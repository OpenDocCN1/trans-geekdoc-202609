
1. *Without coordination between agents*: This is a purely decentralized approach, where agents optimize their actions purely based on local environment information, without any constraints imposed by a coordinator entity. As such, they have full control over both bandwidth and RSRQ threshold.

2. *With coordination between agents*: The initially presented hierarchical approach from [Figure 4.7](#c04.xhtml#c04-fig-0007), where agents have constraints imposed by a coordinator entity. The agents can only control the RSRQ threshold values, while the bandwidth action is imposed by a coordinator agent.

3. *With online learning abilities*: Similar to the previous scheme, except that after agents take an action, they evaluate the observed outcome against the expected estimates (i.e. values inferred through the `DNN`) and can choose another action if the actual encountered value is ranked lower than the estimates of other actions. This can be useful when the initially estimated second‐ranked action turns out to be more effective than the first‐ranked action.

As a baseline, we choose the full‐frequency reuse. This is because, as observed in (Marinescu et al., [2018](#c04.xhtml#c04-bib-0018)), static‐frequency reuse schemes tend to perform worse on average than full‐frequency reuse, with respect to edge users. Even though some static‐frequency reuse schemes can improve performance for specific cells when particular UE distributions are encountered, expanding these schemes to a large group of neighboring cells when involving realistic UE distributions at network level turns out to be detrimental to the overall performance of the network.

We summarise the performance achieved by the three types of MAS in [Table 4.3](#c04.xhtml#c04-tbl-0003), considering the cells previously presented in [Figure 4.10](#c04.xhtml#c04-fig-0010). We chose the inner three cells for evaluation since only the nine cells are controlled by agents, and as such we can best notice the impact of actions within the inner three cells. This performance can be also visualized in [Figure 4.12](#c04.xhtml#c04-fig-0012).

[Table 4.3](#c04.xhtml#R_c04-tbl-0003) Inner three cells (2, 4, 9): maximizing minimum throughput policy.

| Improv. over FR || A. W/o Coord || B. W/ Coord || C. Online Learning || Optimal |
| --- | --- | --- | --- | --- |
| Bottom 10% UEs ||  10% ||  15% ||  16% ||  18% |
| --- | --- | --- | --- | --- |
| Bottom 5% UEs ||  13% ||  23% ||  23% ||  27% |
| Bottom 1% UEs ||  28% ||  56% ||  59% ||  66% |
| Worst UE || 133% || 231% || 263% || 264% |

It can be noticed how each addition to the MAS improves performance. Even a MAS without a coordinator entity achieves better performance when compared to the full‐frequency reuse baseline, with performance improvements most noticeable for edge users. Coordination significantly improves the performance of edge users, while learning abilities bring the efficiency of the MAS to near‐optimal levels, after only five or six iterations of the agent action selection process.[1](#c04.xhtml#c04-note-0001) The performance for the worst user in a cell (in terms of proximity to edge of cell) is improved almost threefold with this type of MAS, providing a 263% improvement, which is very close to the 264% performance that can be achieved optimally. Optimal performance can only be computed after all agents iterate through all the available actions (both coordinator imposed and locally available), a process that can be highly detrimental to the performance of the network, as many of the actions negatively impact the operation of the network. Here, we iterate through these via `ns-3` simulations, for the purpose of computing the optimal solution *a posteriori*.

![Figure 4.12 Performance over the inner three cells: maximizing minimum throughput policy.](images/c04f012.jpg)

[Figure 4.12](#c04.xhtml#R_c04-fig-0012) Performance over the inner three cells: maximizing minimum throughput policy.

### 4.4.5 Summary

This section presented the improvements that neural network‐based multi‐agent systems can bring to `LTE` network performance. The framework presented is a highly adaptable solution that adjusts to a broad variety of user distributions in a network, addresses imbalances in load between cells, and includes learning capabilities in order to improve performance in the situations that might differ too much from the training base of the neural networks. This chapter also showcases how `ML`‐based agents can achieve improved performance at the global network level by cooperating via a coordinator entity. The neural network proposed in this chapter can assist wireless networks in making optimal choices through inference, without needing to explore sub‐optimal actions, which can negatively impact the `LTE` network at runtime. With this `ML`‐based dynamic frequency reuse scheme, the increase in coverage can be almost threefold for edge users, while the network was shown to retain 95% of its capacity from the full‐frequency reuse case.[2](#c04.xhtml#c04-note-0002)

## 4.5 Conclusions

In this chapter, we have shown how machine learning–assisted solutions can improve performance in coverage and capacity optimization–related problems in wireless networks. Two different approaches were presented, targeting long‐term and short‐term adaptations to traffic demands and network environment conditions. The long‐term solution involved turning `BSs` on or off through a deep `RL` approach in order to save energy while still catering to user needs under non‐stationary traffic conditions. The performance of the solution here improves when traffic models are also employed. On the other hand, the short‐term solution, complementary in our vision to the long‐term one, redistributes currently available resources in the network to maximize global network performance depending on the conditions in the network. Here, a multi‐agent system framework based on neural networks' guided cell agents is used to implement dynamic fractional frequency reuse, to improve network coverage while minimizing potential capacity loss. Both of these techniques take advantage of the massive amounts of data/`KPIs` available in wireless networks to assist the decision‐making processes. This way, the presented `ML` heuristics manage to successfully address complex problems in a timely manner.

Real‐time data availability and modelling are essential to these algorithms' decision‐making processes. The more historical data is available, the better the algorithms can infer potential future behavior of the wireless network. Predictions of future network behavior can help improve the solution's performance, as agents can preemptively take actions to address upcoming changes, in either the short term or the long term. As such, we expect accurate `ML`‐based traffic and mobility modelling to play a critical role in the future in addressing coverage and capacity optimization issues of wireless networks.

## Bibliography

1. Nicola Baldo, Marco Miozzo, Manuel Requena‐Esteso, and Jaume Nin‐Guerrero. An open source product‐oriented lte network simulator based on `ns-3`. In *Proceedings of the 14th International conference on Modeling, analysis and simulation of wireless and mobile systems*, pages 293–298. ACM, 2011.

2. Mehdi Bennis, Samir M. Perlaza, Pol Blasco, Zhu Han, and H. Vincent Poor. Self‐organization in small cell networks: A reinforcement learning approach. Transactions on Wireless Communications, 12(7):3202–3212, 2013.

3. François Chollet et al. `Keras`. [https://github.com/fchollet/keras](https://github.com/fchollet/keras), 2015.

4. Mariana Dirani and Zwi Altman. A cooperative reinforcement learning approach for inter‐cell interference coordination in ofdma cellular networks. In *Modeling and Optimization in Mobile, Ad Hoc and Wireless Networks (WiOpt), 2010 Proceedings of the 8th International Symposium on*, pages 170–176. IEEE, 2010.
