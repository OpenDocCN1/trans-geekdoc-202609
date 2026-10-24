
## Pattern-growth approach

The Apriori-based approach has to use the breadth-first search (BFS) strategy because of its level-wise candidate generation. In order to determine whether a size-(k + 1) graph is frequent, it must check all of its corresponding size-k subgraphs to obtain an upper bound of its frequency. Thus before mining any size-(k + 1) subgraph, the Apriori-like approach usually has to complete the mining of size-k subgraphs. Therefore, BFS is necessary in the Apriori-like approach. In contrast, the pattern-growth approach is more flexible regarding its search method. It can use breadth-first search and depth-first search (DFS), the latter of which consumes less memory.

A graph g can be extended by adding a new edge e. The newly formed graph is denoted by g ⋈_x e. Edge e may or may not introduce a new vertex to g. If e introduces a new vertex, we denote the new graph by g ⋈_xf e, otherwise, g ⋈_xb e, where f or b indicates that the extension is in a forward or backward direction.

Fig. 5.16 illustrates a general framework for pattern growth-based frequent substructure mining. We refer to the algorithm as PatternGrowthGraph. For each discovered graph g, it performs extensions recursively until all the frequent graphs with g embedded are discovered. The recursion stops once no frequent graph can be generated.

PatternGrowthGraph is simple, but not efficient. The bottleneck is at the inefficiency of extending a graph. The same graph can be discovered many times. For example, there may exist n different (n − 1)-edge graphs that can be extended to the same n-edge graph. The repeated discovery of the same graph is computationally inefficient. We call a graph that is discovered at the second time a duplicate graph. Although line 1 of PatternGrowthGraph gets rid of duplicate graphs, the generation and detection of duplicate graphs may increase the workload. In order to reduce the generation of duplicate graphs, each frequent graph should be extended as conservatively as possible. This principle leads to the design of several new algorithms. A typical example is the gSpan algorithm as described below.

The gSpan algorithm is designed to reduce the generation of duplicate graphs. It does not need to search previously discovered frequent graphs for duplicate detection. It does not extend any duplicate graph, yet still guarantees the discovery of the complete set of frequent graphs.

Let's see how the gSpan algorithm works. To traverse graphs, it adopts depth-first search. Initially, a starting vertex is randomly chosen and the vertices in a graph are marked so that we can tell which vertices have been visited. The visited vertex set is expanded repeatedly until a full depth-first search (DFS) tree is built. One graph may have various DFS trees depending on how the depth-first search is

```
Algorithm: PatternGrowthGraph(g, D, minsup, S)
Input: A frequent graph g, a graph data set D, and the support threshold minsup.
Output: The frequent graph set S.
1: if g ∈ S then return;
2: else insert g to S;
3: scan D once, find all the edges e such that g can be extended to g ⋈_x e ;
4: for each frequent g ⋈_x e do
5: Call PatternGrowthGraph(g ⋈_x e, D, minsup, S);
6: return;
```

### FIGURE 5.16
PatternGrowthGraph.

![](img/90c930779c8f928df6ff4481fc59f9a3_246_0.png)

### FIGURE 5.17

DFS subscripting.

performed, that is, the vertex visiting order. The darkened edges in Figs. 5.17(b) to 5.17(d) show three DFS trees for the same graph of Fig. 5.17(a). The vertex labels are x, y, and z; the edge labels are a and b. Alphabetic order is taken as the default order in the labels. When building a DFS tree, the visiting sequence of vertices forms a linear order. We use subscripts to record this order, where i < j means vi is visited before vj when the depth-first search is performed. A graph G subscripted with a DFS tree T is written as GT. T is called a DFS subscribing of G. Given a DFS tree T, we call the starting vertex in T, v0, the root, and the last visited vertex, vn, the right-most vertex. The straight path from v0 to vn is called the right-most path. In Figs. 5.17(b) to 5.17(d), three different subscribings are generated based on the corresponding DFS trees. The right-most path is (v0, v1, v3) in Figs. 5.17(b) and 5.17(c), and (v0, v1, v2, v3) in Fig. 5.17(d).

PatternGrowth extends a frequent graph in every possible position, which may generate a large number of duplicate graphs. The gSpan algorithm introduces a more sophisticated extension method. The new method restricts the extension as follows: Given a graph G and a DFS tree T in G, a new edge e can be added between the right-most vertex and other vertices on the right-most path (backward extension); or it can introduce a new vertex and connect to vertices on the right-most path (forward extension). Since both kinds of extensions take place on the right-most path, we call them right-most extension, denoted by G <> e (for brevity, T is omitted here).

### Example 5.22. Backward extension and forward extension.

If we want to extend the graph in Fig. 5.17(b), the backward extension candidates can be (v3, v0). The forward extension candidates can be edges extending from v3, v1, or v0 with a new vertex introduced.

Figs. 5.18(b) to 5.18(g) show all the potential right-most extensions of Fig. 5.18(a). The darkened spots show the rightmost path. Among these, Figs. 5.18(b) to 5.18(d) grow from the rightmost vertex while Figs. 5.18(e) to 5.18(g) grow from other vertices on the rightmost path. Figs. 5.18(b.0) to 5.18(b.4) are children of Fig. 5.18(b), and Figs. 5.18(f.0) to 5.18(f.3) are children of Fig. 5.18(f). In summary, backward extension only takes place on the rightmost vertex while forward extension introduces a new edge from vertices on the rightmost path.

Since many DFS trees/subscriptions may exist for the same graph, we choose one of them as the base subscribing and only conduct right-most extension on that DFS tree/subscription. Otherwise, right-most extension cannot reduce the generation of duplicate graphs because we would have to extend the same graph for every DFS subscribing.

We transform each subscripted graph to an edge sequence, called a DFS code, so that we can build an order among these sequences. The goal is to select the subscribing that generates the minimum

![](img/90c930779c8f928df6ff4481fc59f9a3_247_0.png)

### Table 5.6 DFS code for Fig. 5.17(b), 5.17(c), and 5.17(d).

| edge | $\gamma_0$ | $\gamma_1$ | $\gamma_2$ |
|---|---|---|---|
| $e_0$ | (0, 1, X, a, X) | (0, 1, X, a, X) | (0, 1, Y, b, X) |
| $e_1$ | (1, 2, X, a, Z) | (1, 2, X, b, Y) | (1, 2, X, a, X) |
| $e_2$ | (2, 0, Z, b, X) | (1, 3, X, a, Z) | (2, 3, X, b, Z) |
| $e_3$ | (1, 3, X, b, Y) | (3, 0, Z, b, X) | (3, 1, Z, a, X) |

Based on this ordering, three different DFS codes, γ0, γ1, and γ2, generated by DFS subscriptings in Figs. 5.17(b), 5.17(c), and 5.17(d), respectively, are shown in Table 5.6. An edge is represented by a 5-tuple, (i, j, li, l(i,j), lj), li and lj are the labels of vi and vj, respectively, and l(i,j) is the label of the edge connecting them.

Through DFS coding, a one-to-one mapping is built between a subscripted graph and a DFS code (a one-to-many mapping between a graph and DFS codes). When the context is clear, we treat a sub-
