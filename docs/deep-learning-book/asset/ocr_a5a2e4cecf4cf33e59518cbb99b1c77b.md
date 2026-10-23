![](bbox=[0.37, 0.07, 0.65, 0.13])

Figure 16.3: An undirected graph representing how your roommate's health h_r, your health h_y, and your work colleague's health h_c affect each other. You and your roommate might infect each other with a cold, and you and your work colleague might do the same, but assuming that your roommate and your colleague do not know each other, they can only infect each other indirectly via you.

defined on an undirected graph G. For each clique C in the graph,3 a factor φ(C) (also called a clique potential) measures the affinity of the variables in that clique for being in each of their possible joint states. The factors are constrained to be nonnegative. Together they define an unnormalized probability distribution

tilde{p}(x) = Π_{C∈G} φ(C). (16.3)

The unnormalized probability distribution is efficient to work with so long as all the cliques are small. It encodes the idea that states with higher affinity are more likely. However, unlike in a Bayesian network, there is little structure to the definition of the cliques, so there is nothing to guarantee that multiplying them together will yield a valid probability distribution. See figure 16.4 for an example of reading factorization information from an undirected graph.

Our example of the cold spreading between you, your roommate, and your colleague contains two cliques. One clique contains h_y and h_c. The factor for this clique can be defined by a table and might have values resembling these:

| | h_y = 0 | h_y = 1 |
|---|---|---|
| h_c = 0 | 2 | 1 |
| h_c = 1 | 1 | 10 |

A state of 1 indicates good health, while a state of 0 indicates poor health (having been infected with a cold). Both of you are usually healthy, so the corresponding state has the highest affinity. The state where only one of you is sick has the lowest affinity, because this is a rare state. The state where both of you are sick (because one of you has infected the other) is a higher affinity state, though still not as common as the state where both are healthy.

3 A clique of the graph is a subset of nodes that are all connected to each other by an edge of the graph.