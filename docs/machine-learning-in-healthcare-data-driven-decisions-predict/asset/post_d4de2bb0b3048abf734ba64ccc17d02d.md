
Removal from the network may have a substantial influence on the network’s connectedness. This centrality metric is often used with other centrality measures to get a thorough comprehension of node significance in intricate networks.

## 5 Proposed Model

An egocentric doctor network with $N$ nodes is created by activity-driven temporal network formation, where nodes alternate between active and inactive phases throughout time $T$. Let $A_t$ be the Active periods, which suggests that the doctor is staying at a location and makes different links in same place in a period of time (DLSPT) with other nodes. Just like active period inactive periods $I_t$, these time frames indicate when the doctor node does not establish connections with other nodes, but instead receives DLSPT linkages. The DLSPT link is directed from the host (doctor) nodes to other neighbor (family, friends, co-worker, patients, others) nodes. Just like in the above diagram, the doctor will stay at the hospital for a limited period of time, let’s say 10 p.m. to 5 p.m., and spends his time with his co-workers, his regular patients, and other patients in the hospital. After that, the doctor travels and goes home. He spends some time with his family and friends. While he is in hospital, nodes will be active and create links with other nodes or entities in the hospital. After the time period is over, that node is inactive in that place and active in some other place, but he can receive the DLSPT links from the hospital.

The duration of active periods, $A_t$, is stochastically determined by a geometric distribution with parameter $\varepsilon$, i.e., $P_1(A_t) \sim geometric(\varepsilon)$, where $\varepsilon$ represents a constant scaling factor. Meanwhile, the lengths of inactive periods, denoted as $I_t$, are generated from a geometric distribution with parameter $\gamma$, i.e., $(I_t) \sim geometric(\gamma)$, where $\gamma$ is given heterogeneously to represent varying visitor frequency. The activation potentiality $\gamma$, which exhibits heterogeneity, may be described by a power law relationship $F_1(\gamma) \sim \gamma^{-\beta}$, where $\beta$ represents the scaling parameter.

To represent the dynamics of disease transmission, an indirect transmission period, $\pi$, is included for each active phase. During a certain event $A_t$ and its related probability $\pi$, the doctor generates a predetermined quantity of DLSPT linkages, denoted by the variable $l$, as defined by the following equation:

$Pr(l) = (1 - \sigma)\sigma^{l-1}$

where $\sigma$ denotes the willingness to visit public locations. The value of $\sigma$ is sampled from a power law distribution $F_2(\sigma) \sim \sigma^{-a}$, where $a$ is the scaling parameter. The fluctuations in $l$ represent the spatial and temporal (spatio-temporal) patterns within the doctor’s social network.

Every DLSPT connection has certain timing characteristics: $A_t$ denotes the length of the doctor’s presence at the site where interaction occurred, $d_t$ reflects the time delay between the doctor's appearance and the arrival of a neighboring node, and $t_l$ indicates the duration for which the neighboring node (the terminal nodes of a link) remains at the place of interaction. The delay in creating a connection, $d_t$, is sampled from a truncated geometric distribution,

\( Pr(d_t) = \frac{P_l(1 - P_l)^{d_t}}{1 - (1 - P_l)^{A_t + \pi}} \)

Here, $P_l$ represents the likelihood of establishing a connection with a neighboring entity. The value of $t_l$ is sampled from a geometric distribution with a link-breaking probability of $P_{lb}$, denoted as $P_3(t_l) \sim geometric(P_{lb})$. The values of $P_{lb}$ and $P_l$ remain constant across all vertices in the network.

Nodes preserve their social arrangement by using their recollection of past interactions while choosing new connections. The likelihood of being chosen as a neighbor is contingent upon the doctor's level of public accessibility $\sigma$. The selection process takes into account the contact history and social dynamics within the network, and operates in the following manner:

\( Pr(n_{i_t} + 1) = \frac{\sigma_i \gamma}{(n_{i_t} + \sigma_i \gamma)} \)

Where $n_{i_t}$ represents the cumulative number of nodes that node $i$ has interacted with till time $t$. Increased public accessibility, denoted by $\sigma$, leads to larger contact set sizes in nodes. In addition, they must be chosen as a neighbor by a greater nodes count. Therefore, the likelihood of getting chosen as a neighbor is

\( P(\sigma_j) = \frac{\sigma_j}{M(\sigma)} \)

The neighbor selection method additionally takes into account the probability, $P$, of node $j$ selecting nodes that have already included node $j$ as their neighbors. Figure 1 presents the hypergraph for disease spread in egocentric network.

- Family
- Friends
- Others
- Others
- Doctor 'u'
- Other elements who comes in contact with doctor 'u'.
- Hospital
- Co-worker
- Regular Patients

Figure 1: Hypergraph for egocentric network of disease spread.

Connected components of Facebook Graph G

![](img/106ef0dba620d314f9842503e8ef40c8_430_0.png)

Figure 2: Complex network graph G for the considered dataset.

## 6 Results

In this study, we have considered the Facebook dataset for capturing social circles of nodes (or, users). The dataset constituted of 4,039 nodes, 88,234 edges, and average clustering coefficient of 0.6055. The experimentations were performed on an Intel Core (TM) i7-1260P, x64 system with a processing capacity of 2.10 GHz and having 16 GB RAM. The results were generated using Python 3.10 over the Spyder version 5 framework. Figure 2 shows the generated complex network graph G, depicting different nodes and their connected components. Figure 3 provides the plot showing the comparison between the ranks of the nodes in G along with their degree. It can be observed that as the ranks of

the nodes present in G increase, their degree value incurs an exponential decrease, representing lower influence of being in contact with the super-spreader node (ego).

In Figure 4, the sensitivity analysis for nodes count in the complex network is performed over increasing number of degrees. It can be observed from the findings that high degree values are associated with less number of nodes. Thus, a higher degree indicates the count of super-spreaders in the network. Figure 5 shows the frequency histogram for the number of edges presented in the network fitted with its probability density function (PDF). In Figure 6, the frequency histogram for the degree centrality of the network is presented. This merged plot is effective as a network analysis tool because it contains information about the structural features of nodes and their relative significance, in relation to this intricate node-to-node strategy.

Figure 7 represents the frequency histogram plot fitted with the empirical PDF for betweenness centrality. High betweenness centrality nodes on communication channels may govern information flow, making them attractive. These nodes may provide signaling pathway information and disease spread targets. Figure 8 provides the frequency histogram for closeness centrality, fitted with its empirical PDF. More

![](img/106ef0dba620d314f9842503e8ef40c8_431_0.png)

Figure 3: Comparison plot for node rank with the respective degree.

central nodes have shorter distances or better closeness centrality scores, which allow them to interact more quickly and easily with others. A node with strong proximity centrality has a short average route length to all other nodes. Closeness centrality is particularly pertinent in scenarios where effective communication or information dissemination is vital. A high closeness centrality indicates effective identification of disease spread pattern.

The frequency histogram pertaining to the clustering coefficient of each node in the network is presented in Figure 9, which is fitted with the empirical PDF. A high value of clustering coefficient is indicative of dense connectivity among the nodes and hence implies a high chance of disease spread in network. Figure 10 represents the histogram for eigenvalue of the considered network fitted with its empirical PDF. The eigenvalue is important to understand the overall behavior of the network. A node with higher eigenvalue is indicative of more centrality i.e., if a node has high centrality, then its removal can influence the connectivity of the network significantly.
