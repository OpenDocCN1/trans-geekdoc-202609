of collaboration. Indeed, in the context of (social) network analysis, clustering as finding well connected subgraphs is also known as community detection.

"Are there any challenges specific to clustering analysis on graph and network data?" In most of the clustering methods discussed so far, objects are represented using a set of attributes. A unique feature of graph and network data is that only objects (as vertices) and relationships between them (as edges) are given. No dimensions or attributes are explicitly defined. To conduct cluster analysis on graph and network data, there are two major new challenges.

+   "How can we measure the similarity between two objects on a graph accordingly?" Typically, we cannot use conventional distance measures, such as Euclidean distance. Instead, we need to develop new measures to quantify the similarity. Such measures often are not metric and thus raise new challenges regarding the development of efficient clustering methods. Similarity measures for graphs are discussed in Section 9.5.2.

+   "How can we design clustering models and methods that are effective on graph and network data?" Graph and network data are often complicated, carrying topological structures that are more sophisticated than traditional cluster analysis applications. Many graph data sets are large, such as the web graph containing at least tens of billions of web pages in the publicly indexable Web. Graphs can also be sparse where, on average, a vertex is connected to only a small number of other vertices in the graph. To discover accurate and useful knowledge hidden deep in the data, a good clustering method has to accommodate these factors. Clustering methods for graph and network data are introduced in Section 9.5.3.

# ## 9.5.2 Similarity measures

"How can we measure the similarity or distance between two vertices in a graph?" In our discussion, we examine two types of measures: geodesic distance and distance based on random walk.

# ### Geodesic distance

A simple measure of the distance between two vertices in a graph is the shortest path between the vertices. Formally, the **geodesic distance** _d_(_u_, _v_) between two vertices _u_ and _v_ is the length in terms of the number of edges of the shortest path between the vertices. For two vertices that are not connected in a graph, the geodesic distance is defined as infinite, that is, _d_(_u_, _v_) = +∞ if _u_ and _v_ are not connected.

Using geodesic distance, we can define several other useful measurements for graph analysis and clustering. Given an undirected graph _G_ = (_V_, _E_), where _V_ is the set of vertices and _E_ is the set of edges, we define the following:

+   For a vertex _v_ ∈ _V_, the **eccentricity** of _v_, denoted _eccen_(_v_), is the largest geodesic distance between _v_ and any other vertex _u_ ∈ _V_ − {_v_}. That is,

```
eccen(v) = max_{u∈V−{v}} {d(u, v)}.
```

The eccentricity of _v_ captures how far away _v_ is from its remotest vertex in the graph.

+   The **radius** of graph _G_ is the minimum eccentricity of all vertices. That is,

```
r = min_{v∈V} {eccen(v)}. (9.28)
```