
## 9.5.3 Graph clustering methods

Let us consider how to conduct clustering on a graph. We first describe the intuition behind graph clustering. We then discuss two general categories of graph clustering methods.

The intuition of finding clusters in a graph is to cut the graph into pieces, each piece being a cluster, such that the vertices within a cluster are well connected, and the vertices in different clusters are connected in a much weaker way. Formally, for a graph, G = (V, E), a cut, C = (S, T), is a partitioning of the set of vertices V in G, that is, V = S ∪ T and S ∩ T = ∅. The cut set of a cut is the set of edges, {(u, v) ∈ E | u ∈ S, v ∈ T}. The size of the cut is the number of edges in the cut set. For weighted graphs, the size of a cut is the sum of the weights of the edges in the cut set.

“What kinds of cuts are good for deriving clusters in graphs?” In graph theory and some network applications, a minimum cut is of importance. A cut is minimum if the size of the cut is not greater than the size of any other cut. There are polynomial time algorithms to compute minimum cuts of graphs. Can we use those algorithms in graph clustering?

### Example 9.19. Cuts and clusters.

Consider graph G in Fig. 9.17. The graph has two clusters: {a, b, c, d, e, f} and {g, h, i, j, k}, and one outlier vertex, l.

Consider cut C1 = {(a, b, c, d, e, f, g, h, i, j, k), {l}}. Only one edge, namely, (e, l), crosses the two partitions created by C1. Therefore, the cut set of C1 is {(e, l)}, and the size of C1 is 1. (Note that the size of any cut in a connected graph cannot be smaller than 1.) As a minimum cut, C1 does not lead to a good clustering because it only separates the outlier vertex, l, from the rest of the graph.

Cut C2 = {(a, b, c, d, e, f, l}, {g, h, i, j, k}) leads to a much better clustering than C1. The edges in the cut set of C2 are those connecting the two “natural clusters” in the graph. Specifically, for edges (d, h) and (e, k) that are in the cut set, most of the edges connecting d, h, e, and k belong to one cluster.

Example 9.19 indicates that using a minimum cut is unlikely to lead to a good clustering. We are better off choosing a cut where, for each vertex u that is involved in an edge in the cut set, most of the edges connecting to u belong to one cluster. Formally, let deg(u) be the degree of u, that is, the number of edges connecting to u.

![](img/90c930779c8f928df6ff4481fc59f9a3_500_0.png)

FIGURE 9.17 A graph G and two cuts.

The sparsity of a cut C = (S, T) is defined as

\(\Phi = \frac{\text{cut size}}{\min\{|S|, |T|\}}.\) (9.41)

A cut is sparsest if its sparsity is not greater than the sparsity of any other cut. There may be more than one sparsest cut.

In Example 9.19 and Fig. 9.17, C2 is a sparsest cut. Using sparsity as the objective function, a sparsest cut tries to minimize the number of edges crossing the partitions and balance the partitions in size.

Consider a clustering on a graph G = (V, E) that partitions the graph into k clusters. The modularity of a clustering assesses the quality of the clustering and is defined as

\(Q = \sum_{i=1}^k \left( \frac{l_i}{|E|} - \left( \frac{d_i}{2|E|} \right)^2 \right),\) (9.42)

where \(l_i\) is the number of edges between vertices in the \(i\)th cluster, and \(d_i\) is the sum of the degrees of the vertices in the \(i\)th cluster. The modularity of a clustering of a graph is the difference between the fraction of all edges that fall into individual clusters and the fraction that would do so if the graph vertices were randomly connected. The optimal clustering of graphs maximizes the modularity.

Theoretically, many graph clustering problems can be regarded as finding good cuts, such as the sparsest cuts, on the graph. In practice, however, a number of challenges exist:

- **High computational cost:** Many graph cut problems are computationally expensive. The sparsest cut problem, for example, is NP-hard. Therefore finding the optimal solutions on large graphs is often impossible. A good trade-off between efficiency/scalability and quality has to be achieved.

- **Sophisticated graphs:** Graphs can be more sophisticated than the ones described here, involving weights and/or cycles.

- **High dimensionality:** A graph can have many vertices. In a similarity matrix, a vertex is represented as a vector (a row in the matrix) with a dimensionality that is the number of vertices in the graph. Vertices and edges may carry various attributes, too. Therefore graph clustering methods must handle high dimensionality.

- **Sparsity:** A large graph is often sparse, meaning each vertex on average connects to only a small number of other vertices. A similarity matrix from a large sparse graph can also be sparse.

There are different kinds of methods for clustering graph data, which address these challenges. We introduce some representative ones here.

## Generic high-dimensional clustering methods on graphs

The first group of methods are based on generic clustering methods for high-dimensional data. They extract a similarity matrix from a graph using a similarity measure such as those discussed in Section 9.5.2. A generic clustering method can then be applied on the similarity matrix to discover clusters. Clustering methods for high-dimensional data are typically employed. For example, in many scenarios, once a similarity matrix is obtained, spectral clustering methods (Section 9.4) can be applied. Spectral clustering can approximate optimal graph cut solutions. For additional information, please refer to the bibliographic notes (Section 9.9).

## Specific clustering methods by searching graph structures

The second group of methods are specific to graphs. They search the graph to find well-connected components as clusters. Let us look at a method called SCAN (Structural Clustering Algorithm for Networks) as an example.

Given an undirected graph, G = (V, E), for a vertex, u ∈ V , the neighborhood of u is Γ(u) = {v|(u, v) ∈ E} ∪ {u}. Using the idea of structural-context similarity, SCAN measures the similarity between two vertices, u, v ∈ V , by the normalized common neighborhood size, that is,
σ (u, v) = |Γ(u) ∩ Γ(v)| / √|Γ(u)||Γ(v)|.
(9.43)

The larger the value computed, the more similar the two vertices. SCAN uses a similarity threshold ε to define the cluster membership. For a vertex, u ∈ V , the ε-neighborhood of u is defined as Nε(u) = {v ∈ Γ(u)|σ(u, v) ≥ ε}. The ε-neighborhood of u contains all neighbors of u with a structural-context similarity to u that is at least ε.

In SCAN, a core vertex is a vertex inside of a cluster. That is, u ∈ V is a core vertex if |Nε(u)| ≥ μ, where μ is a popularity threshold. SCAN grows clusters from core vertices. If a vertex v is in the ε-neighborhood of a core u, then v is assigned to the same cluster as u. This process of growing clusters continues until no cluster can be further grown. The process is similar to the density-based clustering method, DBSCAN (Section 8.4.1).

Formally, a vertex v can be directly reached from a core u if v ∈ Nε(u). Transitively, a vertex v can be reached from a core u if there exist vertices w1, ..., wn such that w1 can be reached from u, wi can be reached from wi−1 for 1 < i ≤ n, and v can be reached from wn. Moreover, two vertices, u, v ∈ V , which may or may not be cores, are said to be connected if there exists a core w such that both u and v can be reached from w. All vertices in a cluster are connected. A cluster is a maximum set of vertices such that every pair in the set is connected.

Some vertices may not belong to any cluster. Such a vertex u is a hub if the neighborhood Γ(u) of u contains vertices from more than one cluster. If a vertex does not belong to any cluster, and is not a hub, it is an outlier.

The search framework in SCAN closely resembles the cluster-finding process in DBSCAN. SCAN finds a cut of the graph, where each cluster is a set of vertices that are connected based on the transitive similarity in a structural context. An advantage of SCAN is that its time complexity is linear with respect to the number of edges. In very large and sparse graphs, the number of edges is in the same scale of the number of vertices. Therefore SCAN is expected to have good scalability on clustering large graphs.

## Probabilistic graphical model-based methods

Probabilistic graphical model-based methods regard a graph as a set of observations generated by a probabilistic model. Consequently, probabilistic graphical model-based methods use some heuristics on community generation to find clusters as communities in a graph. They often use probabilistic models of graph structures to describe the dependencies among vertices via the edges.

Three major types of probabilistic graphical models are often used, directed graphical models, undirected graphical models and hybrid graphical models. First, directed graphical models are mainly based on latent variables and leverage similarity of vertices and cluster structures to generate edges that are observable in a graph. Second, undirected graphical models are often based on field structures and use
