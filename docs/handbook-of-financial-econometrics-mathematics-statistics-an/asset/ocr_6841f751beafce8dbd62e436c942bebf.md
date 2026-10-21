It is also important to note that the key element does not necessarily have to be at the end of the chain, i.e., play a role of pure borrower. The most pivotal element can also be located in the center of the network.

# Appendix 9C: Centrality Measures

Degree centrality refers to the number of ties a node has to other nodes. Nodes have higher centrality to the extent they can gain access to and/or influence over others. A central node occupies a structural position (network location) that serves as a source or a channel for larger volumes of information exchange or other resource transactions with other nodes.

Degree centrality $C_i^d(g)$ of node $i$ in network $g$ is calculated as

$C_i^d(g) = \frac{\eta_i(g)}{n-1} = \frac{|N_i(g)|}{n-1} \in [0,1], \quad (9C.1)$

where $\eta_{i(g)}$ is the degree of $i$ in adjacency matrix $g = [g_{ij}]$ and $N_i(g)$ is the set of neighbors of $i$ in $g$, n is the number of vertices.

Degree centrality for a directed graph has one of two forms: in-degree centrality and out-degree centrality. Accordingly, in-degree centrality is evaluated using the number of in-coming links to the node, and out-degree uses the number of out-going links from the node.

For systemic risk analysis and risk allocation in lending activities weighted in-degree centrality (WInDeg) indicates the most active borrowers on the market. It is important to emphasize that this measure lacks information on the number of links of the neighbors of each borrower. Two borrowers can take the same amount of money, but if one borrower is connected to more lenders, the contagion effect from the failure of this borrower would be higher compared to the failure of the other borrower. Weighted out-degree centrality (WOutDeg) indicates the most active lender, and for risk analysis represents borrowers with the largest financial resources and attractive financial instruments to invest. As a previous measure, this one does not take into consideration information about the number of links. Weighted degree centrality is simply the number of other nodes connected directly to a node taking into account the weights on the edges. It is an indicator of a lender’s financial activity and shows the level of its involvement in all types of financial transactions. The value of weighted degree difference, which could be calculated as Weighted out-degree centrality or weighted in-degree centrality, shows the aggregated role of a particular node in the system. As a result, for systemic