
### 4.3.2 GNN Layer Computation

(4.26) $$h_{v}^{(l + 1)} = \overset{\text{UPDATE}_{\theta}^{(l + 1)}}{\overbrace{W_{2}\left[h_{v}^{(l)} \underset{w \in \mathcal{N}(v)}{\oplus} \underset{\text{MESSAGE}_{\theta}^{(l + 1)}}{\underbrace{W_{1}\left\lbrack {h_{v}^{(l)},h_{w}^{(l)}} \right\rbrack}}\right]}}$$

where `W[1]` and `W[2]` denote trainable weight matrices, and

(4.27) $$\oplus = \underset{\text{Scalers}}{\underbrace{\begin{bmatrix} 1 \\ s(\deg(v),1) \\ s(\deg(v), -1) \\ \end{bmatrix}}} \otimes \underset{\text{Aggregators}}{\underbrace{\begin{bmatrix} \text{mean} \\ \min \\ \max \\ \end{bmatrix}}}$$

with `⊗` being the tensor product and

(4.28) $$s(d,\alpha) = \left( \frac{\log(d + 1)}{\frac{1}{|\mathcal{V}|}\sum_{v \in \mathcal{V}}\log(\deg(v) + 1)} \right)^{\alpha}$$

denoting degree-based scalers. Having introduced the basic concepts of message passing within GNNs, we now look more closely at their practical implementation (Section 4.3.3) and resource efficiency (Section 4.3.4).

![Fig. 4.10 Computation scheme of a GNN layer by leveraging gather and scatter methods based on edge indices I, hence alternating between node parallel space and edge parallel space.](graphic/b_9783110785944-004_fig_010.png)

Fig. 4.10 Computation scheme of a GNN layer by leveraging gather and scatter methods based on edge indices `I`, hence alternating between node parallel space and edge parallel space.

### 4.3.3 PyTorch Geometric: Implementing Graph Neural Networks

The practical implementation of graph neural networks is challenging, as high GPU throughput needs to be achieved on highly sparse and irregular data of varying size. Here, we introduce and discuss the *PyTorch Geometric* library [225], a library for deep learning on irregularly structured data, built upon PyTorch [555]. In addition to general graph data structures and processing methods, it contains a variety of recently published methods from the domains of relational learning and 3D data processing. PyTorch Geometric achieves high data throughput by leveraging sparse GPU acceleration, by providing dedicated CUDA kernels, and by introducing efficient mini-batch handling for input examples of different sizes. All implemented methods support both CPU and GPU computations and follow an immutable data flow paradigm that enables dynamic changes in graph structures through time. PyTorch Geometric is released under the MIT license and is available on GitHub.[^17]

In PyTorch Geometric, we represent a graph $\mathcal{G} = (X, (I, E))$ by a node feature matrix $X \in \mathbb{R}^{N \times F}$ of $N$ nodes holding $F$ features, and a sparse adjacency tuple $(I, E)$ of $E$ edges, where $I \in \mathbb{N}^{2 \times E}$ encodes edge indices in COOrdinate (COO) format and $E \in \mathbb{R}^{E \times D}$ (optionally) holds $D$-dimensional edge features. All user-facing APIs, e.g., data-loading routines, multi-GPU support, data augmentation, and model instantiations are heavily inspired by PyTorch to keep them as familiar as possible.

In practice, the realization of Equation 4.20 can be achieved by gathering and scattering node features and a vectorized elementwise computation of `MESSAGE` and `UPDATE` functions, as visualized in Figure 4.10. Although working on irregularly structured input, this scheme can be heavily accelerated by the GPU. In contrast to implementations via sparse matrix multiplications, the usage of gather and scatter proves to be advantageous for low-degree graphs and non-coalesced input, and allows for the integration of central node and multi-dimensional edge information directly while aggregating. We implement different reductions for the scattering of neighboring node features via dedicated CUDA kernels, although execution on other hardware is applicable as well. For more, see Chapter 6.

We provide the user with a general `MessagePassing` interface to allow for rapid and clean prototyping of new research ideas. In order to use the interface, users only need to define the methods `MESSAGE[θ]` (i.e., `message`) and `UPDATE[θ]` (i.e., `update`), and choose `⨁` an aggregation scheme. For implementing `message`, node features are automatically mapped to the respective source and target nodes. Almost all recently proposed neighborhood aggregation functions can be lifted to this interface, including (but not limited to) the methods already integrated in PyTorch Geometric. Overall, PyTorch Geometric currently bundles over 40 different GNN operators proposed in literature, as well as over 15 complete models.

#### (Hierarchical) Pooling

PyTorch Geometric also supports graph-level outputs as opposed to node-level outputs by providing a variety of graph-level pooling functions [435, 687, 736]. To further extract hierarchical information and to allow deeper GNN models, various pooling approaches can be applied in a deterministic or data-dependent manner [118, 175, 205, 241, 588, 633, 697, 724].

#### Mini-Batch Handling

Our framework supports batches of multiple graph instances (of potentially different size) by automatically creating a single (sparse) block-diagonal adjacency matrix and concatenating feature matrices in the node dimension. Therefore, neighborhood aggregation methods can be applied without any modifications, since no messages are exchanged between disconnected graphs. In addition, an automatically generated assignment vector ensures that node-level information is not aggregated across graphs as when executing global aggregation operators.

#### Processing of Datasets

We provide a consistent data format and an easy-to-use interface for the creation and processing of datasets, both for large datasets and for datasets that can be kept in memory during training. In order to create new datasets, users just need to read/download their data and convert it to the PyTorch Geometric data format via the respective `process` method. In addition, datasets can be modified by the use of transforms, which take in separate graphs and transform them, say, for data augmentation, for enhancing node features with synthetic structural graph properties, in order to automatically generate graphs from point clouds or to sample point clouds from meshes.

#### Empirical Evaluation

We evaluated the correctness of the implemented methods by performing a comprehensive comparative study in homogeneous evaluation scenarios, reaching state-of-the-art performance on several graph benchmark tasks. For example, experiments for the semi-supervised node classification performance of common GNN

**Tab. 4.1** Performance (accuracy and standard deviation) of semi-supervised node classification experiments for fixed and random splits across 100 runs.

| **Method** | **Cora** | | **CiteSeer** | | **PubMed** | |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| | **Fixed** | **Random** | **Fixed** | **Random** | **Fixed** | **Random** |
| Cheby [164] | 81.4±0.7 | 77.8±2.2 | 70.2±1.0 | 67.7±1.7 | 78.4±0.4 | 75.8±2.2 |
