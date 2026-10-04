
Extensive experimental results on remote sensing datasets demonstrate the effectiveness of two-order GCN, Hypergraph p-Laplacian GCN and manifold regularized dynamic GCN in comparison to many state-of-the-art semi-supervised learning methods. In addition, we also give some analysis of some related future woks.

## 2.Related Works

In this section, we briefly give a description of some related works including the local geometry structure preserving method and spectral graph convolution on graph structured data.

### 2.1 Hypergraph p-Laplacian theory

In the theory research of a simple graph, researchers often suppose that there only exists a pairwise correspondence relationship between different data objects. In the simple graph, a data object represents a vertex on the graph, and the edge between any two vertices is used to describe the correspondence relationships of different data objects. In real life, different objects are not just pairwise relationships simply, most are complicatedly diversified relationships [[45](#chap9.xhtml#fsr45)], such as one-to-many and many-to-many. For the simple graph, it is difficult to accurately express the complex relationships that are common in practical applications. For Hypergraph, each edge can connect two or more vertices to describe its more complex correlation information. On the one hand, it can capture the complicated information between different data objects, on the other hand, it indirectly guarantees the integrity of data information. [Figure 1](#chap9.xhtml#fig1) gives the difference between a Hypergraph and a simple graph.

In this chapter, we use `V^(h)` to describe a finite set of all vertices. `E^(h)` represents a family of all hyper-edges on a Hypergraph. A subset of `V^(h)` can construct a hyper-edge (`e` ∈ `E^(h)`) of a Hypergraph, i.e., `U [∈E^h] = V`. For each hyper-edge, it has a nonnegative weight `w(e)`. `W^(h)` denotes the diagonal matrix of all hyper-edge weights. Thus, we can use `G(V^(h), E^(h), W^(h))` to represent any Hypergraph structure with weights. To better understand its structure for readers, we can utilize a `|V^(h)| × |E^h|` correlation matrix `H` to show it, i.e.,

![figure](images/p214-1.png)

The degree matrix of each vertex, i.e., the sum of all the hyper-edge weights of its connections, can be expressed in the following form.

![figure](images/p214-2.png)

For each Hypergraph, its degree matrix can be defined as the sum of all vertices or the edge weights on each hyper-edge.

![figure](images/p214-3.jpg)

**Figure 1:**The difference between a Hypergraph and a simple graph. (a) A simple graph: each edge of a simple graph has only two vertices. (b) A Hypergraph. In a Hypergraph, each edge can connect *N* vertices (*N* ≥ 2).

![figure](images/p215-1.png)

where `D[v]` expresses the diagonal matrix including the degree matrix of each vertex. In the past few years, many Hypergraph learning-based models have achieved great success. The first methods first convert a Hypergraph to a simple graph, and then use the spectral clustering methods that are applied to the simple graph to address the Hypergraph issue, such as clique averaging [[46](#chap9.xhtml#fsr46)], Rodriguez’s Laplacian [[47](#chap9.xhtml#fsr47)], star expansion [[48](#chap9.xhtml#fsr48)] and clique expansion [[49](#chap9.xhtml#fsr49)]. The second type of methods, including Bolla Laplacian [[50](#chap9.xhtml#fsr50)] and Zhou’s normalized Laplacian [[51](#chap9.xhtml#fsr51)], are to construct a Hypergraph Laplacian by the definition of a simple graph Laplacian. The third type of methods [[52](#chap9.xhtml#fsr52), [53](#chap9.xhtml#fsr53)] utilize a tensor to describe the Hypergraph structure. Then the Hypergraph is segmented by using the joint clustering methods.

The computational process of the adjacency matrix on the Hypergraph can be divided into four parts. Firstly, we use the `K`-nearest neighbor with the Euclidean distance method to acquire the adjacency matrix `W^(s)` of the simple graph. Then, we regard each central node and its `K` neighbor nodes as a hyper-edge. Third, we can acquire all hyper-edge weights matrix `W^(h)` of the Hypergraph. Finally, the adjacency matrix of Hypergraph can be expressed by the following definition, i.e.,

![figure](images/p215-2.png)

Tan *et al*. [[54](#chap9.xhtml#fsr54)] gave the definition of unnormalized graph Laplacian operator `Δ[2]` by introducing the inner product, i.e.,

![figure](images/p215-3.png)

where `W[ij]` denotes the weight of any two nodes on the simple graph. According to the above-mentioned formula, we also can acquire the inner product form of graph p-Laplacian operator `Δ[p]` by the choice of the parameter `p`(`p` ≥ 1).

![figure](images/p215-4.png)

In other words, high-order graph p-Laplacian [[55](#chap9.xhtml#fsr55), [56](#chap9.xhtml#fsr56)] is a nonlinear generalization of unnormalized graph Laplacian (one order). In addition, we can show the definition of graph p-Laplacian operator `Δ[p]` in the unnormalized and normalized matrix forms.

![figure](images/p216-1.png)

where ![figure](images/in216-1.png) is the degree function of the graph. `φ[p(x)] = |x|^(p−1) sign(x)`. Compared with graph Laplacian, the upper and lower bounds on the second eigenvalue approximate the optimal Cheeger cut value well because of the existence of the tighter isoperimetric inequality on the graph p-Laplacian [[57](#chap9.xhtml#fsr57), [58](#chap9.xhtml#fsr58)]. [Figure 2](#chap9.xhtml#fig2) shows the difference between graph Laplacian and graph p-Laplacian in the manifold structure preserving of data.

Liu *et al*. [[26](#chap9.xhtml#fsr26)] made a generalization for the Laplacian regularized sparse coding by utilizing graph p-Laplacian to describe the manifold distribution of data. Extensive experiment results demonstrate the effectiveness of the p-Laplacian regularized sparse coding model on the human activity datasets. Luo *et al*. [[56](#chap9.xhtml#fsr56)] introduced an efficient gradient descend to analyze the properties of its full eigenvectors on the graph p-Laplacian in detail, which can solve the multi-class clustering problems. Ma *et al*. [[59](#chap9.xhtml#fsr59)] proposed the ensemble p-Laplacian regularization for remote sensing image recognition by the effective combination of multiple graphs to approximate the intrinsic geometry structure of data.

Recently, Ma *et al*. [[60](#chap9.xhtml#fsr60)] proposed a Hypergraph p-Laplacian regularization-based logistic regression for remote sensing image recognition. Fu *et al*. [[41](#chap9.xhtml#fsr41)] proposed a Hypergraph p-Laplacian GCN. These models all use the Hypergraph p-Laplacian to explore its manifold structure information. Compared with Hypergraph and graph p-Laplacian, the effective combination of Hypergraph and graph p-Laplacian (Hypergraph p-Laplacian) can better express the intrinsic structure relationships between nodes. The computational process of `HL[p]` is divided into the following parts: First, we can compute the Hypergraph Laplacian `HL` according to ![figure](images/in216-2.png) and ![figure](images/in216-3.png). Second, we make an eigenvector decomposition on `HL`. Then, we can acquire the full eigenvalues of `HL` by using the gradient descend that was proposed in Ref. [[56](#chap9.xhtml#fsr56)] to solve the embedding problem. Finally, we can get the approximation of `HL[p]` by means of the above full eigenvectors and eigenvalues.

![figure](images/p217-1.jpg)
