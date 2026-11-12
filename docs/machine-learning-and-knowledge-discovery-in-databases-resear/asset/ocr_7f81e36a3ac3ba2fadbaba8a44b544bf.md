variant of Dijkstra's algorithm [2], which simultaneously explores the search space from both the source and target nodes. This approach effectively reduces the number of processed nodes, thereby significantly improving query performance.

The classical CH algorithm cannot be directly applied to our context of predicting the most likely route. We need to address the following issues:

+   1. What criteria should be used for node contraction? In our application scenario, it is crucial to minimize the increase in out-degree as much as possible, as this will affect the speed at which our model predicts potential nodes. Therefore, We propose Shortcut-Edge Differential Contraction, a top-down approach that uses edge difference as the criterion for node contraction. This approach ensures that we can contract more nodes without causing an explosion in out-degree.

+   2. How can we generate shortcuts that are more aligned with the most likely route prediction scenario? Directly using the shortcuts derived from classical algorithms is not feasible. Consequently, we employ bidirectional Dijkstra's algorithm on a probabilistic graph generated from historical data to create shortcuts that are more representative of the most likely route. This enables acceleration in our predictions.

# 3 Problem Formulation and Transformation

We begin with the definitions of Road Network, Route and Query. Subsequently, we formally present the research problem and provide its transformation. For the sake of clarity and ease of reference, the notation employed in this paper is presented in Table 2.

# Table 2. Notation and Description Table

| Notation | Description |
| :--- | :--- |
| $G(V, E)$ | A directed graph consisting of vertices $V$ and edges $E$. |
| $|V|, |E|$ | Number of nodes and edges. |
| $G_{agg.log}$ | The graph $G$ weighted by the negative logarithm of probabilities. |
| $R, R^*$ | True routes and Predicted routes. |
| $SC^{(1)}, SC^{(2)}$ | Shortcuts filtered through historical trajectories and Shortcuts generated based on probabilistic graphs. |
| $|R_i|, |R^*_i|$ | Number of edges in the true route and in the predicted route, respectively. |
| $|R_{d=s-t}|$ | Count of predicted paths matching the original path's endpoint. |
| $q = (s, d, t)$ | A query is represented by a tuple, involving start node $s$, destination node $d$, and time $t$. |
| $Pr(R|q)$ | The probability of selecting route $R$ given a specific query $q$. |
| $P_s$ | The set of historical paths within the historical trajectory that share the same start-end pair. |
| $P(e)$ | Probability of selecting edge, $e$. |
| UnConf | The unnormalized confidence score for predictions. |
| $Q(\text{cur}, \text{nbr})|\text{cur}; d; \Theta)$ | Transition probability from the current node to a neighboring node, given the destination and parameterized by $\Theta$. |
| N2V(node) | The embedding of a node using the node2vec algorithm. |
| $W$ | Weight matrix for a layer in the neural network. |
| $T_{total}$ | Total time taken to generate all predicted routes. |

**Definition 1 (Road Network).** A road network is represented as a directed graph $G(V, E)$, in which $V$ and $E$ represent the vertices (crossroads) and edges (road segments) respectively.