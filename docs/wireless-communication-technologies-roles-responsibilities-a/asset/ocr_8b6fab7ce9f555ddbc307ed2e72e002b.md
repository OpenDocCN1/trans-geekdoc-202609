round. In this thesis, Multi-hop routing technique is used to transmit the aggregated data to the remote sink node.

# 14.2.1 OPTIMIZATION TECHNIQUES

A sensor network is defined from information point of view, as a WSN graph GWSN comprising a set {Ve,Li} where, Ve (1 ≤ e ≤ n) and n is the number of WNs. Ve specifies WN in a WSN and Li(1 ≤ i ≤ n2) represents a link between two vertices with its associated costs.

A graph GWSN is having vertices as Ve and links between them as Li. A link is incident at both vertices which are adjacent to each other. Edges are of two types:

+   Parallel: Two links with same vertices
+   Loop: A link with same end points

Graphs with no parallel edges or loops are called Simple graph. Complete Graph is a simple graph with a path existing in between every pair of vertices. The link cost for each node may vary depending on the remaining energy available, distance from the sink node, and energy consumption by each WN. The ultimate goal is to find an optimal path formed by linking a set of nodes with the minimum total cost associated with it. To find this optimal path there are many optimization techniques available in the literature.

The following are some of the techniques available to optimize the path:

# 14.2.1.1 Minimum Spanning Trees

It is a collection of edges of a connected, undirected graph without any cycles, connecting all the vertices together, with minimum total edge weight.

A telecommunication firm is planning to lay cable in a new area. The constraint here is to lay the cables only along the road side. Here, an undirected graph is established in that area containing all the houses. Some paths might be more expensive than others based on the length of the cable required to establish a connection. These expensive connections are assigned with larger weights than the connections that are cheaper. A minimum spanning tree in this case is a subset of those paths, which connects every house with lowest total cost and no cycles.

# 14.2.1.2 Shortest Path Algorithms

A route R in a graph GWSN is a sequence V1,L1,V2, ... Lm, Vm, where each Ve is a vertex and each link is Li for 1<e<m, the ends of Li are Ve-1 and Ve. One of the objectives of this thesis is to find the route for information transmitted by each node to a distant sink node with minimum energy consumption. To satisfy the objective a directed graph is used. For example, if one wishes to make a street map table of minimum driving distance from one place of a city to every other street corner in the city obeying the directions one-way, then there are many possible ways to do that. This can be regarded as a directed graph, as one-ways are also to be considered.