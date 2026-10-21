Several measures are proposed to evaluate the degree of structural hole in a complex network. We use “constraint” in our paper as the major measure for structural hole because it’s the most widely used (Burt, 1992; Zaheer and Bell, 2005; Yu et al., 2018). Network constraint effectively measures a node’s lack of access to structural holes (Burt, 1992), defined as the following:

$C_i = \sum_{j} \left( p_{ij} + \sum_{q} p_{iq} p_{qj} \right)^{2}, \quad i \neq q \neq j \text{ and } j, q \in \rho(i), \qquad (31.1)$

where $\rho(i)$ is the set of neighbors of node $i$, $p_{ij}$ is the proportion of direct ties from $i$ to $j$. $\sum_{q} p_{iq} p_{qj}$ is the sum of indirect tie from $i$ to $j$ via all $q$. Network constraint measures the extent to which the nodes’ vision is limited. Constraint of $i$ would be generally higher if $i$ has just few contacts, or if contacts are highly connected with each other. The higher the network constraint index of a node, the fewer structural holes the node occupies.

The variable of network constraint $C_i$ measures the extent to which the access of node $i$ to information available from other nodes in the network is limited. The following example illustrates the computation of constraints in a simple network as displayed in Figure 31.1.

In Figure 31.1, the constraint of node A is 1/3, while the constraints of node B, C and D are 1s. Assuming that information can only travel along the links connecting the nodes, node A in Figure 31.1 stands at the structural hole of network: In Figure 31.1, Node B, C and D can only get information from A, and will lose their ability to obtain information from other nodes if A disappears. Node B, C and D are therefore “constrained” by A. In our analyst coverage network, analysts occupying node B, C, D will rely on the

![](bbox=[0.35, 0.78, 0.65, 0.9])

Figure 31.1: A simple network.