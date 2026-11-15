Another reason for programming with objects is to protect function data. The incentive becomes more clear when we define multiple complex words with similar functionality, as we leave the door open to unintended side effects. The situation is compounded when operations involve a complex nesting of data structures, making resource conflicts more likely. For example, we may have multiple operations simultaneously vying for the use of a single data stack. In such a cases, it would be better to have the data isolated and protected, as can be achieved by defining objects that contain their own data.

# 17.3.10 Graph Glossary

+   - Edge: A connection between a distinct pair of vertices.
+   - Subgraph: A graph that exists within a graph. Given G = G(V, E), a subgraph may be denoted as H = H(V', E').
+   - Digraph: A directed graph, wherein edges enforce direction of traversal.
+   - Connected graph: Defined by a path between any two vertices.
+   - Complete graph: A graph in which there exists an edge between every distinct vertex pair.
+   - Directed and complete graph: Each vertex pair is connected by two directed edges, one in each direction.
+   - Strongly connected: When a digraph has a path from every vertex to every other vertex.
+   - Weighted graph: the edges have numeric values in terms of weight, cost, distance, ....
+   - Degree of vertex: The number of edges incident to a vertex. The degree of vertex 1 can be denoted such as