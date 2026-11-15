# 17.4(b). Trees and graphs entail different algorithms for their processing.

Trees are a type of graph. A graph can be a tree if:

+   - The edges are directed.
+   - There are no cycles.
+   - All vertices have a path to the root vertex.

¹We often refer to the elements of a tree as _nodes_ and the elements of a graph as _vertices_.

Two trees and/or graphs may be:

+   - Equal: The structure, data, and order are the same.
+   - Identical: The structure may differ while having the same data and order. Identical structures may or may not be equal.
+   - Isomorphic: The structures have the same form or shape. The data may or may not be the same.

Here, the word _structure_ refers to the relationship between the nodes, as seen in their respective connections by edges. In that respect, identical graphs can look different.

If there exists a function that maps nodes from one graph onto those of another such that the set of connections for each node remain identical, the two graph are said to be isomorphic.

For example, the graphs in Figure 17.5 are all isomorphic to each other.