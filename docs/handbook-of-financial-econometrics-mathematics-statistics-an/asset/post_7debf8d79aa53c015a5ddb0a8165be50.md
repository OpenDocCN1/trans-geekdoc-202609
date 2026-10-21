
## 31.4.2 Measures of network structural hole

We then merge the analyst-firm data with CRSP to obtain stock price and return information, and with Compustat to gather financial records. We use the two-digit Global Industry Classification Standard (GICS) codes from Compustat in our following analysis, as the GICS classification is commonly used among practitioners (Bhojraj et al., 2003).

We utilize techniques developed in the social science network research to analyze information flows within these annually constructed analyst coverage networks. Specifically, we measure the position of each analyst in the network and focus primarily on analysts who are positioned at “structural holes”. Structural hole is one of the most important concepts from social network research and widely used in psychology and informatics. A structural hole characterizes an absence of bridging ties between two groups. When agents occupy a structural hole, they are able to see early, see more broadly, and translate information across groups. Agents in the position(s) of structural hole are associated with a larger exposure to diverse knowledge base and hence “good ideas” (Burt, 2003). In our context, we expect that analysts occupying structural holes are favorably positioned to be exposed to a diverse and comprehensive set of information in the analyst community.

We choose constraint (Burt, 1992) as our main measure to capture the degree of aggregated information flow of each node in the analyst coverage network. A lower constraint points to analysts with more direct and indirect connections to peers with overlapping research coverage on firms. Peer analysts, referred to as analysts covering the same companies, could provide research coverage on different sets of industries and firms. In our setting, peer analysts can potentially share not only the firm-level information, but also the relevant potential macroeconomic and industry information. In addition, there is a network effect. For example, while analyst A interacts and competes more intensely with peer analysts at other brokerages (i.e., her direct connections), these peers may cover other firms and thus can learn from their own direct connections, so on and so forth. We use structural hole measures to proxy for the size or breadth of an analyst’s information set transmitted in the network, accounting for these higher-order dependencies and effects from an analyst’s indirect connections. In the modern interconnected economy, this type of information may be particularly valuable because seemingly unrelated developments across various parts of the economy may influence one another (Mansharamani, 2012).

Several measures are proposed to evaluate the degree of structural hole in a complex network. We use “constraint” in our paper as the major measure for structural hole because it’s the most widely used (Burt, 1992; Zaheer and Bell, 2005; Yu et al., 2018). Network constraint effectively measures a node’s lack of access to structural holes (Burt, 1992), defined as the following:

$C_i = \sum_{j} \left( p_{ij} + \sum_{q} p_{iq} p_{qj} \right)^{2}, \quad i \neq q \neq j \text{ and } j, q \in \rho(i), \qquad (31.1)$

where $\rho(i)$ is the set of neighbors of node $i$, $p_{ij}$ is the proportion of direct ties from $i$ to $j$. $\sum_{q} p_{iq} p_{qj}$ is the sum of indirect ties from $i$ to $j$ via all $q$. Network constraint measures the extent to which the nodes’ vision is limited. Constraint of $i$ would be generally higher if $i$ has just a few contacts, or if contacts are highly connected with each other. The higher the network constraint index of a node, the fewer structural holes the node occupies.

The variable of network constraint $C_i$ measures the extent to which the access of node $i$ to information available from other nodes in the network is limited. The following example illustrates the computation of constraints in a simple network as displayed in Figure 31.1.

In Figure 31.1, the constraint of node A is 1/3, while the constraints of node B, C and D are 1s. Assuming that information can only travel along the links connecting the nodes, node A in Figure 31.1 stands at the structural hole of the network: In Figure 31.1, Node B, C and D can only get information from A, and will lose their ability to obtain information from other nodes if A disappears. Node B, C and D are therefore “constrained” by A. In our analyst coverage network, analysts occupying node B, C, D will rely on the Node A analyst for accessing information from each other. Consequently, the Node A analyst stands to receive more non-redundant information from the other three analysts by occupying a position of lower constraint.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_1308_0.png)

Figure 31.1: A simple network.

We also use effective size and betweenness centrality as alternative measures of structural hole in the regression analysis. Effective size of i is i's network size (the number of direct connections) subtracted by i's redundancy in the network. It estimates the extent to which contact j is redundant with other contacts of node i and can be calculated as the following:

$$ES_i = \sum_{j}[1 - \sum_{q} p_{iq} m_{jq}], \quad q \neq i, j, \tag{31.2}$$

where $p_{iq}$ is the proportion of $i$'s connection with $q$ as a ratio of all its connections. And $m_{jq}$ is $j$'s interaction with $q$ divided by $j$'s strongest relationship with anyone (this is always 1 if $j$ has a tie to $q$ and 0 otherwise). The sum of the product $p_{iq} m_{jq}$ measures the portion of $i$'s relation with $j$ that is redundant to $i$'s relation with other primary contacts.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_1309_0.png)

To illustrate the idea of effective size in Figure 31.1, we add an edge between node B and C. With an added edge, there is a redundant path from node A to node C: A → B → C and a redundant path from node A to node B: A → C → B. The redundant path from A to B and from A to C are both $\frac{1}{3} * 1 = \frac{1}{3}$, and thus the effective size of node A is $3 - 2/3 = 7/3$. Effective size measures the non-redundant elements of the network and nodes occupy more structural holes when they have a larger effective size.

Betweenness is a centrality measure using the idea of “shortest paths”. For every pair of nodes in a network, there exists at least one shortest path. The betweenness centrality for each node is the number of these shortest paths that pass through that node as a ratio of the total number of shortest paths. The betweenness centrality of node $i$ is calculated as the following:

$$\text{betweenness}_i = \sum_{s \neq i \neq t} \frac{\sigma_{st}(i)}{\sigma_{st}}, \tag{31.3}$$

where $\sigma_{st}$ is the total number of shortest paths from node $s$ to node $t$ and $\sigma_{st}(i)$ is the number of those paths that pass through node $i$. The node with a higher betweenness centrality occupies more structural holes.

To illustrate the idea of betweenness centrality in the network of Figure 31.1, node A lies on all the shortest paths connecting any node-pairs, while none of nodes B, C, and D does. The betweenness centrality of A is 1 and those of B, C, D are all 0s. When a node lies on more of the shortest paths connecting nodes in the network, it is more likely to control the flow of information transmitted in the network.

We calculate the structural hole measures of constraint, effective size and betweenness centrality for each analyst annually for our sample period of 1994-2016. We use the prior year’s (t − 1) structural hole measures to rank analysts to eliminate any dependence of our classification procedures on the excess returns in year t.

## 31.4.3 Analyst attributes

In this section, we describe the variables of analyst attributes used in our analysis. We identify lead (highly ranked) analysts as those in the top decile of structural hole measures in a given year. We compare the working experience and affiliated brokerages of these top-ranked analysts with those of other analysts in results presented in Table 31.2.

We use the number of years dated from the first year the analyst appeared in the I/B/E/S earnings forecast database to the year of measurement to represent an analyst’s experience in that year. Results in Table 31.2 indicate that analysts in the top decile sorted by the structural hole measure are more experienced than other analysts. On average, those top-ranked analysts are senior to others by around three years in the profession.

We then use the number of analysts employed by a brokerage to measure the brokerage size (Hong and Kubik, 2003), and examine whether those top-ranked analysts occupying more structural holes tend to work at large brokerages. Table 31.3 presents the difference of brokerage size between the top decile analysts and others. The result indicates that there is no significant difference in brokerage size between the two groups on average. However, analysts working at larger brokerage houses may have access to more resources (Ke and Yu, 2006). It will be much easier for those analysts to process a rich set of information when occupying structural holes. As a result, the position of structural hole may play a bigger role when analysts work at large brokerage houses. We test this hypothesis in Section 31.5.1.
