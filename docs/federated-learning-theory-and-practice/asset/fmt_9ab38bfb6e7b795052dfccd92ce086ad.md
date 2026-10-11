
The convergence guarantees of bilevel optimization algorithms have been investigated in recent works [\[5\]](#Chp010_181-197_B9780443190377000181.xhtml#br0025), [\[12\]](#Chp010_181-197_B9780443190377000181.xhtml#br0060). For the BiG-FL problem, it has been shown in [\[25\]](#Chp010_181-197_B9780443190377000181.xhtml#br0125) that when the UL and LL step sizes `α^(t)` and `β^(t)` are chosen on the order of `1/√T`, under the Lipschitz continuity of the UL loss function, as well as its Jacobian and Hessian, plus the strong convexity of the LL loss functions, [Algorithm 4](#Chp010_181-197_B9780443190377000181.xhtml#f0030) needs `O(1/ε⁴)` iterations to reach the FOSPs of Eq. ([10.12](#Chp010_181-197_B9780443190377000181.xhtml#deq15)) in the sense that both the first-order stationarity of the UL optimization variable `φ`, i.e., `E[∥∇ℓ(φ^(t))∥²]`, and the distance between `θ[i]^(t)` and its optimal counterpart, i.e., `E[∥θ[i]^(t) − θ[i]^(*)(φ^(t))∥²]`, `∀i`, are `O(ε)`, where the expectation is taken over both the randomness of data samples and the index of the iterations.

## 10.5 Numerical evaluation of GFL models

In this section, we provide numerical experiments for testing the performance of these GFL models and algorithms with a comparison with the benchmark FedAvg [\[18\]](#Chp010_181-197_B9780443190377000181.xhtml#br0090) on both synthetic and real data, which were partially shown in [\[25\]](#Chp010_181-197_B9780443190377000181.xhtml#br0125).

### 10.5.1 Results on synthetic data

To generate a heterogeneous network with respect to local model parameters, topology-based groundtruth weights (embedding) are generated based on a predefined graph, where inputs `{X[i]}` are randomly generated, and the outputs `{Y[i]}` are obtained by following our model in Eq. [(10.13)](#Chp010_181-197_B9780443190377000181.xhtml#deq17), which is further illustrated in [Fig. 10.2](#Chp010_181-197_B9780443190377000181.xhtml#f0035). In order to evaluate the generalization performance of the models, we need to generate two homologous graphs so that graphs adopted in training and testing share the same distribution. To be specific, we generate two graphs that follow homologous distributions. Each of them has 50 nodes and consists of the same mixture of three standard normal distributions. The range of the centers of these distributions is `[-0.5, 0.5]`, and the standard deviation of all these distributions is 0.5. We use the four closest neighboring nodes to build the graph. The dimension of the generated samples is 64, which is used as the groundtruth weight (reshaped to `8×8`) of the model for each client. For data synthesis, both training and testing sets are independently generated for the 50 LL learning tasks with uniformly distributed samples (`100×8`) in the range of `[-60, 60]` as the input. The output is obtained by matrix multiplication of the input and the groundtruth weights. Parameters used in the synthetic data experiment are shown in [Table 10.1](#Chp010_181-197_B9780443190377000181.xhtml#t0010).

![Figure 10.2 Homologous graph generation and data synthesis.](OEBPS/images/B9780443190377000181/gr006_u1.jpg)

[Figure 10.2](#Chp010_181-197_B9780443190377000181.xhtml#cf0265) Homologous graph generation and data synthesis.

[Table 10.1](#Chp010_181-197_B9780443190377000181.xhtml#cf0270)

Synthetic experiment setting.

| Common Mixture Distribution | | Distribution Type | Gaussian |
| --- | --- | --- | --- |
| | | Number of Center | 3 |
| | | Range of Center | `[-0.5, 0.5]` |
| | | Standard Deviation | 0.5 |
| | | Dimension | 64 |
| Homologous Graph Generation | | Number of Neighbor Connections | 4 |
| | | Node Dimension | 64 |
| | | Node Number of Train Graph | 50 |
| | | Node Number of Test Graph | 50 |
| Node Data Synthesis | | Shape of Ground Truth Weight | `8×8` |
| | | Shape of Input | `100×8` |
| | | Range of Input Distribution | `[-60, 60]` |
| | | Shape of Input | `8×100` |
| Node (Lower Level) Model | | Number of Layer | 3 |
| | | Activation Function | Sigmoid |
| | | Shape of Layers | `[8×16, 16×16, 16×8]` |
| Upper Level Model | | Shape of GNN weight | `512×512` |

The multi-layer perception followed by the sigmoid activation functions is used in the LL learning model, and the total number of layers of `θ[i]` is 3 with shapes of `8×16`, `16×16`, and `16×8`, respectively. The UL task is link-prediction based on negative sampling. For each head node, we randomly sample 10 tail nodes from all negative edges and use the DGL package with a GCN layer [\[22\]](#Chp010_181-197_B9780443190377000181.xhtml#br0110) to generate the graph embedding for learning the edge similarity. The GCN layer is used in the UL task, where `φ` of dimension `512×512` serves as the graph convolution kernel of the GCN layer. Each uploaded LL weight `θ[i]` acts as the node input representative, which is flattened into a shape of `1×512` and fitted into the cosine embedding loss function after message passing. As FeSEM requires prior knowledge about the number of clustering centers, we set `K=3` to reflect the setting of the three mixed Gaussian distributions.

The numerical results are shown in [Fig. 10.3](#Chp010_181-197_B9780443190377000181.xhtml#f0040). It can be observed that the consensus-based models perform the worst in comparison with the cluster or graph embedding based ones, as there are three mixture Gaussian data samples over the graph. FeSEM improves the performance of classic FedAvg and DFL as the EM algorithm is able to find the three centers and tailor the model to fit different kinds of data distributions. BiG-FL shows the best performance among all the models in this case, which justifies the power of the UL learning task for extracting embedding through the graph information and transferring this similarity to the testing phrase.

![Figure 10.3 Performance comparison (local testing loss).](OEBPS/images/B9780443190377000181/gr007.jpg)

[Figure 10.3](#Chp010_181-197_B9780443190377000181.xhtml#cf0280) Performance comparison (local testing loss).

### 10.5.2 Results on real-world data for NLP

A large lookup weight table related to the number of words in the corpus plays a central role in natural language processing (NLP) tasks. Each row of the table corresponds to a word which is involved in the current task (i.e., word embedding). These word embeddings are trainable weights and are non-i.i.d. due to textual word data originating from different domains, and have different dimensions and interleaved weight spaces due to the differences in corpus words.
