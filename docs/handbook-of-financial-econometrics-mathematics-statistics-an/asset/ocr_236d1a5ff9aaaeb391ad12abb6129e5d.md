pair of vertices. The network approach thus provides an easy way to visualize the correlation structure of a large-scale complex system.

Two vertices are neighbors if they share a common edge. The degree of a vertex is the number of edges it has. A graph is complete if any pair of its vertices is connected. A clique is a complete subset of a graph. A k-star refers to a subset for which k vertices are neighbors to one specific vertex simultaneously. A triangle corresponds to three vertices that are neighbors to each other.

A random network has edges that are randomly produced. The simplest random network is the Erdős–Rényi model, in which the presence of an edge is independent of the presence of any other edge with a constant probability p. Thus, the probability for any vertex to have a degree x is

$$P(X = x) = \binom{N-1}{x} p^x (1-p)^{N-1-x} \approx \frac{\lambda^x e^{-\lambda}}{x!}, \tag{8.1}$$

where $\lambda = (N-1)p$ and the approximation relies on a large $N$.

While the edges are not independent, the probability function for the graph can be quite complex. Dependence graph $D$ on the edge set $E$ may help specify the dependence structure. Its vertex set consists of all pairs $\{i,j\} \in \binom{V}{2}$ and the edge between $E_{ij}$ and $E_{lm}$ exists when they are dependent conditional on the rest of $G$. Clearly, the dependence graph is a nonrandom graph.

By Hammersley–Clifford theorem the probability function of a random graph $G$ can be characterized as

$$\Pr(G) \propto \exp \sum_{A \subseteq G} \alpha_A, \tag{8.2}$$

where $\alpha_A$ is some constant when $A$ is a clique of $D$ and equal to 0 otherwise.

A Markov graph has its dependence graph $D$, which contains no edge between disjoint $E_{ij}$ and $E_{uv}$ for distinct $i,j,u,v$. A random graph satisfying the Markov condition is a Markov random graph. By adding a homogeneity condition that the probability function $\Pr(G)$ are the same for all isomorphic graphs $G$, Frank and Strauss (1986) showed that the probability for any homogenous undirected Markov graph can be reduced to

$$\Pr(G) \propto \exp\left( \alpha_0 T + \sum_k \alpha_k S_k \right), \tag{8.3}$$

where $T$ is the number of triangles, $S_1$ is the number of edges and $S_k$ is the number of $k$-stars. This family of graph models is usually referred as exponential family random graph (ERGM) or $p^*$ models.