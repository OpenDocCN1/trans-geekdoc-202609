
```
{ 0:8 1:5 2:2 3:7 4:9 } lt LIST ( level-order index:value pairs)
lt ( invoke the list before processing the list)
GSC { #: SPLIT 7 EQ >R DROP ?? } LREPEAT
R>. ( → 3)
```

### 17.2.5 Tree Glossary

- Root: Top or first node. May be referred to as level 0 or 1.
- Node: An element of a tree. May be a root, child node, or leaf.
- Edge: Line connecting two nodes.
- Leaf: A node without children.
- Level (Height): The number of nodes along the tree's longest path.
- Subtree: A tree within a larger tree. Has its own root.
- Balanced binary tree: A tree in which the height of right and left subtrees of any node do not differ by more than 1.
- Full binary tree: Each node has either two branches or no branches.
- Complete binary tree: At all tree levels, with the possible exception of the lowest, all nodes have two child nodes.

## 17.3 GRAPHS

A graph is a collection of distinct *vertices* (nodes), that may or may not be connected. A tree is a graph, but a graph is not a tree, as a cyclical path exists among the vertices.

Each vertex may be associated with a label and other data, including the count of neighboring connections, referred to as its *degree*. Vertices are neighbors if they are connected by an *edge*.

Generally, a vertex may contain the following records:

- Label or name.
- Degree.
- Records of neighbors and the weights of their respective edges.
- Count of traversals or visits.

Graphs can be represented by adjacency matrices and adjacency lists, which may in turn be constructed of lists, arrays, or tables.

Symbolically, a set of vertices V and a set of edges E comprise a graph G, or G(V, E). The vertices in V are denoted as $v_i$ and the edges in E are denoted $e_i$.

If an edge connects two vertices, then we denote these vertices as adjacent or *neighbors*. Such a pair may be referred to as *endpoints*, $v_1$ and $v_2$, of edge $e_1$ and may be expressed as:

$e_1 = \{v_1, v_2\}$

### 17.3.1 Computations for Graphs

Each vertex in a graph has a number of connecting edges which is referred to as the *degree* of the vertex. For example, the degree of a particular vertex 1 may be denoted as $deg(v_1) = 2$.

The total degrees in a graph depends on the total number of edges and is computed as:

$2 \times edges$

The total number of edges in a complete directed graph of \( n \) vertices is computed as:

\( n \times (n - 1) \)

The total number of edges in a complete undirected graph of \( n \) vertices is computed as:

\( n \times \frac{(n - 1)}{2} \)

If most vertices in a graph are connected by edges to other vertices, then the graph is said to be *dense*. The maximum density of a graph is 1, or 100%, and the minimum density is 0, representing an *isolated graph*. The computation for graph density is:

\( \frac{2 \times \text{number of edges}}{n \times (n - 1)} \)

The distance between any two vertices in a graph is the sum of their intermediary edges. Edges may, in turn, be weighted in terms of a distance, cost, statistical coefficient, etc.

### 17.3.2 Graphs as Relations

Relations in graphs are entirely relative to a vertex's connections to other vertices. For graphs that are not trees, there is no vertical property such as height in the graphs. Thus, directional edges between vertices are necessary for any order or hierarchy. For example, we can say that a relation exists between objects A and B when object B derives from object A, or when A is greater than B, etc.

### Graph Relation Properties:

- Reflexive: Every vertex has a loop (an edge from itself to itself).
- Symmetric: Every edge is bi-directional.
- Antisymmetric: Every edge is unidirectional.
- Transitive: Paths between vertices A and B, as well between vertices B and C, indicate that a path exists between vertices A and C.

![](img/ff796e63b14a88ab72583e78f3994e90_401_0.png)

Figure 17.13 A relation of two objects: B depends on A. B is directed to A.

Suppose that both B and C derive from A.

That relation R can be represented in set form where:

```
R = { (b, a) (c, a) }
```

... for a set of elements S, where:

```
S = { a b c }
```

We can have a self-loop whereby a vertex points to itself. If vertex C in Figure 17.14 has a self-loop, then there is a paired relation set (c, c). When all vertices of a graph have self-loops, then the graph is said to be reflexive, as shown in Figure 17.15.

![](img/ff796e63b14a88ab72583e78f3994e90_402_0.png)

Figure 17.14 Relations of objects.

![](img/ff796e63b14a88ab72583e78f3994e90_402_1.png)

Figure 17.15 A reflexive relation.

The reflexive relation in Figure 17.15 is presented in set form as follows:

```
R = { (b, a) (c, a) (a, a) (b, b) (c, c) }
```

### 17.3.3 Quantifying an Undirected Graph

Consider the graph of the states of New England in Figure 17.16. Vertices are connected for states that are adjacent to each other. The graph is connected, but undirected.

![](img/ff796e63b14a88ab72583e78f3994e90_403_0.png)

Figure 17.16 An undirected graph representing the bordering states of New England.

Notice that some vertices are not adjacent. Therefore, it is not a complete graph. In contrast, Figure 17.17 shows an example of a complete graph. Every vertex connects to every other vertex.

![](img/ff796e63b14a88ab72583e78f3994e90_404_0.png)

Figure 17.17 A complete graph.

For the complete and undirected graph in Figure 17.17, the number of edges is computed, using n = 6, as:

```
\frac{n \times (n - 1)}{2} = \frac{6 \times (5)}{2} = 15
```

Assuming that a complete and undirected graph actually has six vertices and two edges between each pair of vertices, the number of edges is then computed as:

```
n \times (n - 1) = 6(5) = 30
```

As can be seen in Figure 17.17, there are six vertices and five degrees per vertex for a total of 15 edges. This graph's density is computed as:

```
\frac{2 \times number of edges}{n \times (n - 1)} = \frac{2 \times 15}{6 \times (6 - 1)} = 1, \text{or } 100\%.
```

### 17.3.4 Graph as Adjacency Matrix

We can construct an adjacency matrix to show which vertices are adjacent. Intersections in the matrix may be assigned 0 or 1 (true or false) for unweighted graphs, or otherwise have some weighted value such as a distance in miles, a correlation coefficient, etc.

If the graph is directed, then a value of 1 is entered only if direction to that vertex exists. Otherwise the entry is 0.

Unless there are self-loops, the diagonal of the adjacency matrix should be all 0s. If the graph is undirected, the graph can be represented by just one side of the diagonal.

Consider the adjacency matrix in Figure 17.2, which represents the graph in Figure 17.18. Note how edge (B, C) has an entry of 0 while edge (C, B) has an entry of 1. This is because vertex B is adjacent to vertex C, but vertex C is not adjacent to vertex B.

### TABLE 17.2 An adjacency matrix

| | A | B | C | D | E | F | G |
|---|---|---|---|---|---|---|---|
| A | 0 | 1 | 0 | 1 | 0 | 1 | 0 |
| B | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
| C | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
| D | 0 | 0 | 0 | 0 | 1 | 1 | 0 |
| E | 0 | 0 | 0 | 0 | 0 | 1 | 1 |
| F | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| G | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

![](img/ff796e63b14a88ab72583e78f3994e90_407_0.png)

Figure 17.18 An incomplete directed graph.

### 17.3.5 Graph as Adjacency List

An adjacency list is a linear alternative to the two-dimensional adjacency matrix. An adjacency list consists only of those vertex pairs that are adjacent. It is effectively a *list-of-lists*. The exclusion of non-adjacent vertices saves on system resources, such as memory and disk space. This is preferable for the storage of large sparse graphs.

An adjacency list of the vertex pairs in the graph in Figure 17.18 can be represented by a list as follows:

```
{ A:B A:D A:F B:B C:B D:E D:F E:F E:G F:G } al LIST
```

Alternatively, a more explicit list-of-lists can be defined, with a list consisting of the sublists of each vertex's adjacencies, such as:
