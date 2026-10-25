+   3. Node D dominates node E because the degree of membership of D with respect to E is 0.9, which is higher than the threshold value of 0.6.

In this example, the fuzzy membership values in the adjacency matrix generate domination connections, and the threshold value for domination determines whether a node dominates another in the fuzzy network.

Fuzzy graphs' definition of domination and threshold value can be changed to fit the application or study.

**Definition:** Let $G = (V, E)$ be a fuzzy graph with fuzzy adjacency matrix $F = [f_{ij}]$, where $V = \{v_1, v_2, ..., v_h\}$ is the set of vertices (nodes) and $E \subseteq V \times V$ is the set of edges (links). Let $F(v_i, v_j)$ denote the degree of membership or degree of domination of vertex $v_i$ with respect to vertex $v_j$ in the fuzzy graph. A vertex $v_i$ is said to dominate vertex $v_j$ in the fuzzy graph G if and only if:

$F(v_i, v_j) \ge \alpha, \quad for \ some \ \alpha \in [0,1]$

where $\alpha$ is the threshold value for domination, and $F(v_i, v_j)$ represents the degree of membership or degree of domination of vertex $v_i$ with respect to vertex $v_j$ in the fuzzy adjacency matrix.

In other words, vertex $v_i$ dominates vertex $v_j$ if the degree of membership or degree of domination of $v_i$ with respect to $v_j$ is equal to or greater than the threshold value $\alpha$.

Based on the degree of membership or degree of domination values in the fuzzy adjacency matrix, this equational definition enables the determination of domination relationships in fuzzy graphs, and the threshold value can be modified to meet the needs of the particular application or analysis.

# ## 3.3.2 DIFFERENT TYPES OF FUZZY DOMINATION (TOTAL DOMINATION, STRONG DOMINATION, WEAK DOMINATION)

Fuzzy domination in fuzzy graphs can be categorized into different types based on the strength and extent of domination. The three commonly recognized types of fuzzy domination are as follows:

+   1. **Total domination:** A vertex $v_i$ is said to totally dominate a vertex $v_j$ if the degree of membership or degree of domination of $v_i$ with respect to $v_j$ is equal to 1, i.e. $F(v_i, v_j) = 1$. This means that $v_i$ has complete control or influence over $v_j$ in the fuzzy graph, and $v_j$ is fully dominated by $v_i$.

**Example:** Consider a fuzzy graph with the following fuzzy adjacency matrix (Figure 3.7).

In this case, vertex A totally dominates vertex D, as $F(A, D) = 1$, indicating that A has complete control or influence over D in the fuzzy graph.