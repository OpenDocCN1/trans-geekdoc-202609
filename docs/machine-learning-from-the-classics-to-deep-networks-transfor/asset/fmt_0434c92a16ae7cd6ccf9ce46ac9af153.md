
## 16.2.1 Constructing a join tree

Starting from a triangulated graph, the following algorithmic steps construct a join tree ([32]):

*   Select a node in a maximal clique of the triangulated graph, which is **not** shared by other cliques. Eliminate this node and keep removing nodes from the clique, as long as they are **not** shared by other cliques. Denote the set of the remaining nodes of this clique as `S[i]`, where `i` is the number of the nodes eliminated so far. This set is called a *separator*. Use `V[i]` to denote the set of all the nodes in the clique, prior to the elimination process.

*   Select another maximal clique and repeat the process with the index counting the node elimination starting from `i`.

*   Continue the process until all cliques have been eliminated. Once the previous peeling off procedure has been completed, join together the parts that have resulted, so that each separator, `S[i]`, is joined to `V[i]` on one of its sides and to a clique node (set) `V[j]` (`j > i`), such that `S[i] ⊂ V[j]`. This is in line with the running intersection property. It can be shown that the resulting graph is a join tree (part of the proof in Problem [16.1](#Chp016_805-853_B9780443292385000226.xhtml#o0045)). Sometimes, the definition of a junction tree refers to this type of join trees that are constructed to include separators as links.

An alternative algorithmic path to construct a join tree, once the cliques have been formed, is the following. Build an undirected graph having as nodes the maximal cliques of the triangulated graph. For each pair of linked nodes, `V[i]`, `V[j]`, assign a weight `w[ij]` on the respective edge equal to the cardinality of `V[i] ∩ V[j]`. Then run the `maximal spanning tree` algorithm (e.g., [43]) to identify a tree in this graph such that the sum of weights is maximal [41]. It turns out that such a procedure guarantees the running intersection property.

### Example 16.2
