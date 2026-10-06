
## Graph Neural Networks (GNNs)

![](img/f01928df50903c99ce023dd3c527a33d_555_0.png)

New Notation: $\mathcal{G} = \{\mathbf{A}, \mathbf{X}\}$

- Adjacency matrix $\mathbf{A} \in \mathbb{R}^{N \times N}$
- Feature matrix $\mathbf{X} \in \mathbb{R}^{N \times F}$

- **Main Idea**: Pass messages between pairs of nodes and agglomerate
- **Alternative Interpretation**: Pass messages between nodes to refine node (and possibly edge) representations / features

## Recap: Convolutional Neural Networks (CNNs) on Grids

Single CNN layer with 3x3 filter:

![](img/f01928df50903c99ce023dd3c527a33d_556_0.png)

Update for a single pixel:

- Transform messages individually $W_i h_i$
- Add everything up $\sum_i W_i h_i$

$h_0 \quad h_1 \quad \dots$
$h_i$

$h_i \in \mathbb{R}^F$ are (hidden layer) activations of a pixel/node

## Recap: Convolutional Neural Networks (CNNs) on Grids

### Single CNN layer with 3x3 filter:

![](img/f01928df50903c99ce023dd3c527a33d_557_0.png)

### Update for a single pixel:

- Transform messages individually $W_i h_i$
- Add everything up $\sum_i W_i h_i$

$h_i \in \mathbb{R}^F$ are (hidden layer) activations of a pixel/node

### Full update:

```
$h_4^{(l+1)} = \sigma \left(W_0^{(l)}h_0^{(l)} + W_1^{(l)}h_1^{(l)} + \dots + W_8^{(l)}h_8^{(l)} \right)$
```

## Graph Convolutional Networks (GCNs)

Consider this undirected graph:

![](img/f01928df50903c99ce023dd3c527a33d_558_0.png)

## Graph Convolutional Networks (GCNs)

Consider this undirected graph:

Calculate update for node in red:

Aggregate all information from neighbouring nodes to update representation

![](img/f01928df50903c99ce023dd3c527a33d_559_0.png)

## Graph Convolutional Networks (GCNs)

Consider this undirected graph:

Calculate update for node in red:

Aggregate all information from neighoured nodes to update representation

![](img/f01928df50903c99ce023dd3c527a33d_560_0.png)

Desirable properties:

- Weight sharing over all locations
- Invariance to permutations
- Linear complexity O(E)

```
Update rule: $h_i^{(l+1)} = \sigma \left( h_i^{(l)} W_0^{(l)} + \sum_{j \in \mathcal{N}_i} \frac{1}{c_{ij}} h_j^{(l)} W_1^{(l)} \right)$
```

Scalability: subsample messages [Hamilton et al., NIPS 2017]

$\mathcal{N}_i$ : neighbor indices $c_{ij}$ : norm. constant (fixed/trainable)

Kipf & Welling (ICLR 2017), related previous works by Duvenaud et al. (NIPS 2015) and Li et al. (ICLR 2016)

Gerhard Neumann | Machine Learning | KIT | SS 2024

## GNNs with Edge Embeddings

![](img/f01928df50903c99ce023dd3c527a33d_561_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_561_1.png)

Edge Features

Node Features

Formally: $v\to e : h_{(i,j)}^l = f_e^l([h_i^l, h_j^l, \mathbf{x}_{(i,j)}^l])$
$e\to v : h_j^{l+1} = f_v^l(\sum_{i\in\mathcal{N}_j} h_{(i,j)}^l, \mathbf{x}_j)$

## GNNs with Edge Embeddings

![](img/f01928df50903c99ce023dd3c527a33d_562_0.png)

### Pros:

- Support edge features
- More expressive than GCN
- Very general

### Cons:

- Need to store intermediate edge-based activations
- Limited to small graphs

Formally: $v \leftarrow e : \mathbf{h}_{(i,j)}^l = f_e^l([\mathbf{h}_i^l, \mathbf{h}_j^l, \mathbf{x}_{(i,j)}])$

$e \leftarrow v : \mathbf{h}_j^{l+1} = f_v^l([\sum_{i \in \mathcal{N}_j} \mathbf{h}_{(i,j)}^l, \mathbf{x}_j])$

## Graph Neural Networks (GNNs) with Attention

![](img/f01928df50903c99ce023dd3c527a33d_563_0.png)

[Figure from Veličković et al. (ICLR 2018)]

```
$$\vec{h}'_i = \sigma \left( \frac{1}{K} \sum_{k=1}^K \sum_{j \in \mathcal{N}_i} \alpha_{ij}^k \mathbf{W}^k \vec{h}_j \right)$$
```
Monti et al. (CVPR 2017), Vos (NIPS 2017), Veličković et al. (ICLR 2018)

Gerhard Neumann | Machine Learning | KIT | SS 2024

## Graph Attention

### Multi-Head Attention:

Last layer
$$\vec{h}_i' = \sigma \left(\frac{1}{K} \sum_{k=1}^K \sum_{j \in \mathcal{N}_i} \alpha_{ij}^k \mathbf{W}^k \vec{h}_j\right)$$

Previous layers
$$\vec{h}_i' = \sigma \left(\sum_{j \in \mathcal{N}_i} \alpha_{ij}^k \mathbf{W}^k \vec{h}_j\right)$$

- K different heads
- Averaged in last layer, concatenated for previous layers
- || denotes the concatenation
$$\frac{\exp\left(\text{LeakyReLU}\left(\vec{a}^T || \vec{h}_j\right)\right)}{\sum_{k \in \mathcal{N}_i} \exp\left(\text{LeakyReLU}\left(\vec{a}^T || \vec{h}_k\right)\right)}$$

### Attention Weights: $\alpha_{ij} =$

- Softmax activation
- Parametrized by $\mathbf{W} \in \mathbb{R}^{F' \times F}$ and $\vec{a} \in \mathbb{R}^{F'}$

## Graph Neural Networks (GNNs) with Attention

![](img/f01928df50903c99ce023dd3c527a33d_565_0.png)

Pros:

- No need to store intermediate edge-based activations (when using dot-product attention)
- Slower than GCN but faster than GNNs with edge embeddings

Cons:

- Most likely less expressive than GNNs with edge embedding
- Can be more difficult to optimize

[Figure from Veličković et al. (ICLR 2018)]

## Classification and Link Prediction with GNNs / GCNs

Input: Feature matrix $X \in \mathbb{R}^{N \times E}$, preprocessed adjacency matrix $\hat{A}$

![](img/f01928df50903c99ce023dd3c527a33d_566_0.png)

Node classification: $softmax(z_n)$ e.g. Kipf & Welling (ICLR 2017)

$H^{(l+1)} = \sigma \left(\hat{A}H^{(l)}W^{(l)}\right)$ $Z = H^{(L)}$

No weight sharing: Each message passing layer has its weights

## Classification and Link Prediction with GNNs / GCNs

Input: Feature matrix $X \in \mathbb{R}^{N \times E}$, preprocessed adjacency matrix $\hat{A}$

![](img/f01928df50903c99ce023dd3c527a33d_567_0.png)

$H^{(l+1)} = \sigma \left(\hat{A}H^{(l)}W^{(l)}\right)$

No weight sharing: Each message passing layer has its weights

## Classification and Link Prediction with GNNs / GCNs

Input: Feature matrix $X \in \mathbb{R}^{N \times E}$, preprocessed adjacency matrix $\hat{A}$

![](img/f01928df50903c99ce023dd3c527a33d_568_0.png)

Node classification: $softmax(\mathbf{z}_n)$ e.g. Kipf & Welling (ICLR 2017)

Graph classification: $softmax(\sum_n \mathbf{z}_n)$ e.g. Duvenaud et al. (NIPS 2015)

Link prediction: $p(A_{ij}) = \sigma(\mathbf{z}_i^T \mathbf{z}_j)$
Kipf & Welling (NIPS 2016)
"Graph Auto-Encoders"

No weight sharing: Each message passing layer has its weights

## Semi-supervised Classification on Graphs

Setting:
Some nodes are labeled (black circle)
All other nodes are unlabeled

Task:
Predict node label of unlabeled nodes

![](img/f01928df50903c99ce023dd3c527a33d_569_0.png)

## Semi-supervised Classification on Graphs

Setting:
Some nodes are labeled (black circle)
All other nodes are unlabeled

Task:
Predict node label of unlabeled nodes

![](img/f01928df50903c99ce023dd3c527a33d_570_0.png)

Evaluate loss on labeled nodes only:

```
$$\mathcal{L} = -\sum_{l\in\mathcal{Y}_L} \sum_{f=1}^{F} Y_{lf} \ln Z_{lf}$$
```

- $\mathcal{Y}_L$ set of labeled node indices
- $\mathbf{Y}$ label matrix
- $\mathbf{Z}$ GCN output (after softmax)

## Semi-supervised Classification on Graphs

Setting:
Some nodes are labeled (black circle)
All other nodes are unlabeled

Task:
Predict node label of unlabeled nodes

![](img/f01928df50903c99ce023dd3c527a33d_571_0.png)

Evaluate loss on labeled nodes only:

$$\mathcal{L} = -\sum_{l \in \mathcal{Y}_L} \sum_{f=1}^{F} Y_{if} \ln Z_{if}$$

$\mathcal{Y}_L$ set of labeled node indices
$Y$ label matrix
$Z$ GCN output (after softmax)

| Method | Citeseer | Cora | Pubmed | NELL |
|---|---|---|---|---|
| ManiReg [3] | 60.1 | 59.5 | 70.7 | 21.8 |
| SemiEmb [28] | 59.6 | 59.0 | 71.1 | 26.7 |
| LP [37] | 45.3 | 58.0 | 63.0 | 26.5 |
| DeepWalk [22] | 43.2 | 67.2 | 65.3 | 25.1 |
| ICA [18] | 69.1 | 75.1 | 79.9 | 58.3 |
| Planetoid* [29] | 64.1 (6cks) | 75.7 (13s) | 77.2 (25s) | 61.0 (185s) |
| GCN (this paper) | 70.3 (7s) | 81.5 (4s) | 79.0 (38s) | 66.0 (48s) |
| GCN (rand. splits) | 67.9 ± 0.5 | 80.1 ± 0.5 | 78.9 ± 0.7 | 58.4 ± 1.7 |
