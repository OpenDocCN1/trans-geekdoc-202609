# 11.4 Graph neural networks

A wide variety of types of information can be represented by graphs. Some examples of graphs include knowledge graphs, social networks, molecular structures, and document citation networks. Graph neural networks (GNNs) operate on graphs and relational data. In this section, we’ll study graph convolutional networks (GCNs) for classifying nodes in the CORA citation network dataset. But first, let’s look at GNN fundamentals.

Let G=(V, E) be our graph with vertices V and edges E. We can construct an adjacency matrix A to capture the interconnection of edges, such that A_ij = 1 if an edge exists between nodes i and j and 0 otherwise. For undirected graphs, we have a symmetric adjacency matrix such that A = A^T. Another matrix that will prove useful in training GNNs is the node feature matrix x. Assuming we have N nodes and F features per node, the size of X is N×F.

As an example, in a CORA dataset, each node is a document and each edge is a citation that forms a directed edge between two nodes. We can capture the citation relationships in the adjacency matrix A. Since each document is a collection of words, we can introduce indicator features that tell us whether a particular dictionary word is present or absent from the document. In this case, N will be the number of documents and F will be the dictionary size. Thus, we can represent the text information in each document via a binary N×F matrix X.

It’s important to note that edges can have their own features as well. In this case, if the size of edge features is S and the number of edges is M, we can construct an edge feature matrix E of size M×S. It’s also important to make a distinction between classifying the entire graph as a whole (e.g., as in molecule classification) and classifying nodes within a graph (e.g., as in the CORA citation network). The former method is called batch mode classification, while the latter is referred to as single mode.

It’s interesting to draw a parallel between GCNs and CNNs. Images can also be seen as graphs, albeit with regular structure. For example, each node can represent a pixel, the node feature can represent the pixel value, and the edge feature can represent the Euclidean distance between each pixel in a complete graph. In this light, GCNs can be seen as a generalization of CNNs, since they operate on arbitrarily connected graphs.

We can think of information propagation in a spectral GCN as signal propagation along the nodes. Spectral GCN uses Eigen decomposition of a graph Laplacian matrix to propagate the signal with key forward equation as follows.

$$X' = D^{-\frac{1}{2}} (A + I) D^{-\frac{1}{2}} X W + b \tag{11.18}$$

Let’s understand this equation step by step. If we take adjacency matrix A and multiply it by the feature matrix X, the product A X represents the sum of neighboring node features. However, this sum is over all the neighboring nodes except the node itself. To fix this, we add a self-loop in the adjacency matrix by summing it with an