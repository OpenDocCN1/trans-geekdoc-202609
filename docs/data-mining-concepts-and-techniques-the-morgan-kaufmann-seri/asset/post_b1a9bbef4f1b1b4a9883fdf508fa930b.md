
![](img/90c930779c8f928df6ff4481fc59f9a3_571_0.png)

FIGURE 10.37 A toy social network (a). The topology of the social network is represented by its adjacency matrix A (b) and the node attributes are represented by the attribute matrix X (c). (d) The 2-D embedding vectors of nodes are denoted by Z.

to emphasize the use of neural networks techniques to learn the node embedding. The learned low-dimensional vectors (i.e., the node embedding) can be used as the input of a variety of downstream applications, such as classification, clustering, outlier detection, and link prediction.

## 10.5.2 Graph convolutional networks

An effective type of GNNs is called GCNs. Given an input graph A with node attributes X, a GCN model uses a set of weight matrices W^l (l = 1, ..., L), one weight matrix for each layer, to produce the node embedding matrix Z^l whose rows are the embedding of the corresponding nodes. The algorithm is summarized in Fig. 10.38. The steps are described next.

**Preprocessing and initialization:** We first add a self-edge to each node i. For a given node i, this will enable the GCN model to “remember” its own embedding while aggregating its neighboring nodes’ embedding that will be described next. In terms of the adjacency matrix, adding a self edge to each node is equivalent to updating the adjacency matrix by an identity matrix I (Step 1), where I(i, i) = 1 and I(i, j) = 0 ∀i ≠ j (i, j = 1, ..., n). Then, in Step 2, we calculate the degree matrix D of the updated adjacency matrix A, where D(i, i) = Σ_{j=1}^n A(i, j) and D(i, j) = 0 ∀i ≠ j (i, j = 1, ..., n). Using the degree matrix D, in Step 3, we calculate a normalized matrix Â as Â = D^{-1/2} A D^{-1/2}, which is also referred to as the normalized graph Laplacian of matrix A. Each element in the matrix Â is obtained by normalizing the corresponding element in A by the square root of the degrees of the source and the target nodes of the given element: Â(i, j) = A(i, j) / √(D(i,i)D(j,j)). In Step 4, the initial embedding is simply set as the input node attribute matrix Z^0 = X.

**Producing node embedding layer-by-layer:** GCNs produce the node embedding at a given layer Z^l based on the embedding from the previous layer Z^{l-1} through the following three steps. First (Step 6), for each dimension p of the previous node embedding of each node i, we take a weighted aggregation of the embedding of its neighboring nodes: Z̃^{l-1}(i, p) = Σ_{j=1}^n Â(i, j) Z^{l-1}(j, p). This step is also referred to as propagation, and in the matrix form, we have that Z̃^{l-1} = Â Z^{l-1}. Second

- Algorithm: Graph convolutional networks for producing node embedding at different layers.

  - Input:
    - A, adjacency matrix of the input graph of size n x n;
    - X, the node attribute matrix of size n x d;
    - W^l (l = 1, ..., L), the weight matrix at each layer;
    - L, the number of layers;
    - f, nonlinear activation function (e.g., sigmoid or ReLU function).

  - Output: The node embedding matrices Z^l (l = 1, ..., L).

  - Method:
    - //Preprocessing and Initialization
    - (1) Add a self-edge for each node: A <- A + I where I is an identity matrix;
    - (2) Calculate the degree matrix D of A;
    - (3) Normalize A_hat = D^-1/2 A D^-1/2;
    - (4) Initialize Z^0 = X;
    - (5) for (l = 1, ..., L) { // for each layer of GCNs
    - //Propagation
    - (6) Z_bar^(l-1) = A_hat Z^(l-1); // aggregate the neighboring embedding
    - //Linear Transformation
    - (7) Z_tilde^l = Z_bar^(l-1) W^l; // linear transformation of aggregated embedding
    - //Nonlinear activation
    - (8) Z^l = f(Z_tilde^l); // nonlinear activation of linearly transformed embedding
    - (9) }

FIGURE 10.38
Graph convolutional networks. We assume the weights are given and the bias vectors are omitted for brevity.

(Step 7), we take a linear transformation of the aggregated embedding through the weight matrix: \(\tilde{Z}^l = \tilde{Z}^{l-1} W^l\). That is, we take a linear weighted sum of different dimensions of the aggregated embedding: \(\tilde{Z}^l(i, p) = \sum_{j=1}^n \tilde{Z}^{l-1}(i, j) W^l(j, p)\). Third (Step 8), we pass the linearly transformed embedding matrix \(\tilde{Z}^l\) through a nonlinear activation function, such as sigmoid function or ReLU function.

Notice that the last two steps are similar to a fully connected layer of a feed-forward neural network, with the aggregated embedding matrix \(\tilde{Z}^{l-1}\) as the input, the weight matrix \(W^l\) as the model parameters, and the node embedding matrix \(Z^l\) in Step 8 as the output of this layer. That is,

\(Z^l = f(\tilde{Z}^{l-1} W^l).\) (10.28)

Eq. (10.28) is called batch implementation, in that we have stacked the embedding of all n nodes (i.e., samples) into an \(n \times d^l\) matrix \(Z^l\), where \(d^l\) is the embedding dimension of layer-l, and each row of \(Z^l\) is the embedding of one node (i.e., sample). It is not hard to re-write Eq. (10.28) with respect to each individual node or sample

\(Z^l(i, :) = f(\tilde{Z}^{l-1}(i, :) W^l),\) (10.29)

where \(Z^l(i, :)\) is the embedding of node i of the lth layer (\(i = 1, ..., n\)). A subtle point with respect to notation is that GCNs typically use a row vector (e.g., \(Z^l(i, :)\)) to represent the embedding of a node;

![](img/90c930779c8f928df6ff4481fc59f9a3_573_0.png)

**FIGURE 10.39** A conceptual comparison between GCNs (b) and feed-forward neural networks (a). In the matrix form, the main difference lies the extra propagation (i.e., aggregation) step through the normalized graph Laplacian matrix $\hat{\mathbf{A}}$ in GCNs.

whereas in other deep learning models (e.g., feed-forward neural networks, CNNs, RNNs) and other GNNs models (e.g., GraphSAGE that will be introduced next), the embedding of a data sample (e.g., a node) is represented by a column vector by convention. These two forms can be converted with each other. For example, Eq. (10.29) is equivalent to \((\mathbf{Z}^l(i, :))^T = f((\mathbf{W}^l)^T (\tilde{\mathbf{Z}}^{l-1}(i, :))^T)\), where the column vector \((\mathbf{Z}^l(i, :))^T\) is the transpose of the row vector \(\mathbf{Z}^l(i, :)\).

Conceptually, the main difference between GCNs and feed-forward neural networks lies in the propagation (Step 6). That is, we first propagate (or aggregate) the node embedding matrix \(\mathbf{Z}^{l-1}\) from the previous layer and then use the aggregated embedding matrix \(\tilde{\mathbf{Z}}^{l-1} = \hat{\mathbf{A}}\mathbf{Z}^{l-1}\), instead of \(\mathbf{Z}^{l-1}\), as the input of this layer (layer-\(l\)). See Fig. 10.39 for a comparison.

“But, why do we want to introduce this extra (Propagation or Aggregation) step? Which part of the GCNs algorithm in Fig. 10.38 corresponds to convolution?” Recall that for 2-D convolution, the filter is a fixed, small-sized (e.g., 3 × 3) matrix. For a given element of the input matrix (e.g., a pixel), we place the center of the filter on top of the pixel and thus identify a local neighborhood of the pixel, called the receptive field. Then, we take a weighted sum of all the elements in the receptive field, weighted by the corresponding elements in the filter, as the element in the feature map. However, we cannot directly apply this strategy to perform convolution operations on graphs because the neighborhood of different nodes often have different sizes, and there is no natural ordering of nodes in the neighborhood. The propagation in Step 6 provides a clever way to address these issues as follows. First, the nonzero entries in the \(i\)th row of matrix \(\hat{\mathbf{A}}\) define the neighborhood of node \(i\): \(\mathcal{N}(i) = \{j | j \neq i, \hat{\mathbf{A}}(i, j) \neq 0\}\) (analogous to the receptive field in 2-D convolution). Then, we take a weighted sum of the embedding of node \(i\)’s neighbors, weighted by the corresponding elements in \(\hat{\mathbf{A}}\) (analogous to the filter in the 2-D convolution). Finally, the aggregated embedding from the neighborhood is combined with node \(i\)’s current embedding by a linear weighted sum as the updated embedding of node \(i\) (analogous to the
