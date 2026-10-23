# 23 Graph embeddings¹

# 23.1 Introduction

We now turn our focus to data which has semantic relationships between training samples {x_n}_{n=1}^N. The relationships (known as edges) connect training samples (nodes) with an application specific meaning (commonly similarity). Graphs provide the mathematical foundations for reasoning about these kind of relationships

Graphs are universal data structures that can represent complex relational data (composed of nodes and edges), and appear in multiple domains such as social networks, computational chemistry [Gil+17], biology [Sta+06], recommendation systems [KSJ09], semi-supervised learning [GB18], and others.

Let A ∈ {0,1}^{N×N} be the adjacency matrix, where N is the number of nodes, and let W ∈ ℝ^{N×N} be a weighted version. In the methods we discuss below, some set W = A while others set W to a transformation of A, such as row-wise normalization. Finally, let X ∈ ℝ^{N×D} be a matrix of node features.

When designing and training a neural network model over graph data, we desire the designed method be applicable to nodes which participate in different graph settings (e.g. have differing connections and community structure). Contrast this with a neural network model designed for images, where each pixel (node) has the same neighborhood structure. By contrast, an arbitrary graph has no specified alignment of nodes, and further, each node might have a different neighborhood structure. See Fig. 23.1 for a comparison. Consequently, operations like Euclidean spatial convolution cannot be directly applied on irregular graphs: Euclidean convolutions strongly rely on geometric priors (such as shift invariance), which don’t generalize to non-Euclidean domains.

These challenges led to the development of Geometric Deep Learning (GDL) research [Bro+17b], which aims at applying deep learning techniques to non-Euclidean data. In particular, given the widespread prevalence of graphs in real-world applications, there has been a surge of interest in applying machine learning methods to graph-structured data. Among these, Graph Representation Learning (GRL) [Cha+20] methods aim at learning low-dimensional continuous vector representations for graph-structured data, also called embeddings.

We divide GRL here into two classes of problems: unsupervised and supervised (or semi-supervised) GRL. The first class aims at learning low-dimensional Euclidean representations optimizing an objective, e.g. one that preserve the structure of an input graph. The second class also learns low-dimensional Euclidean representations but for a specific downstream prediction task such as