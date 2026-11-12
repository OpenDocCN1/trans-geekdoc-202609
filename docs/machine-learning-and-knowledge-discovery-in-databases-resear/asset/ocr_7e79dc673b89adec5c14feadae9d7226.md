larizes feature propagation without altering GCN architecture or graph structure. Unlike prior methods, LGT maintains representation diversity and depth scalability through an optimization-centered approach, and is inherently compatible with normalization-based techniques such as PairNorm and ContraNorm for further performance gains.

# 3 Problem Definition

Referring the methods of evaluating over-smoothing [11,21], we consider the standard semi-supervised node classification task on a graph \(\mathcal{G} = (\mathcal{V}, \mathcal{E})\), where \(\mathcal{V} = \{v_1, v_2, \dots, v_n\}\) is the set of nodes and \(\mathcal{E}\) is the set of edges. Each node \(v_i \in \mathcal{V}\) is associated with a feature vector \(x_i \in \mathbb{R}^f\), and all node features form the feature matrix \(\mathbf{X} \in \mathbb{R}^{n \times f}\). A subset of nodes \(\mathcal{V}_L = \{v_1, \dots, v_m\}\) with \(m \ll n\) are labeled, while the remaining nodes \(\mathcal{V}_U = \mathcal{V} \\ \mathcal{V}_L\) are unlabeled.

The graph structure is encoded via the adjacency matrix \(\mathbf{A} \in \{0, 1\}^{n \times n}\), where \(\mathbf{A}_{ij} = 1\) if an edge exists between nodes \(v_i\) and \(v_j\). We adopt the normalized graph Laplacian: \(\mathbf{L} = \mathbf{D}^{-\frac{1}{2}}(\mathbf{A} + \mathbf{I})\mathbf{D}^{-\frac{1}{2}},\) (1) where \(\mathbf{I}\) is the identity matrix and \(\mathbf{D}\) is the diagonal degree matrix with \(\mathbf{D}_{ii} = \sum_j \mathbf{A}_{ij}\).

The objective of semi-supervised node classification is to train a GCN that minimizes the cross-entropy loss over labeled nodes: \(\mathcal{L} = - \sum_{v_i \in \mathcal{Y}_L} \sum_{c=1}^{C} y_{i,c} \log \hat{y}_{i,c},\) (2) where \(C\) is the number of classes, \(y_{i,c}\) is the one-hot label, and \(\hat{y}_{i,c}\) is the predicted class probability for node \(v_i\).

A key challenge arises when scaling GCNs to deep architectures due to the over-smoothing effect, where node representations \(H^{(K)}\) progressively converge to a subspace with minimal discriminative information: \(\lim_{K \to \infty} H^{(K)} \approx \mathbf{C},\) (3)

where \(\mathbf{C}\) is a constant matrix independent of node identity. This phenomenon severely degrades classification accuracy on unlabeled nodes. Therefore, an effective GCN should maintain high classification accuracy even as the network depth \(K\) increases. Our goal is to design a training strategy that mitigates over-smoothing while enabling deeper GCNs to preserve discriminative node representations.

# 4 Layer-Wise Gradual Training

While deep GCNs suffer from over-smoothing, our empirical analysis (Fig.1) reveals that trainable linear transformations accelerate feature collapse even at