
Hence, \( Q_{pwn}^n \) converges to a matrix \( Q^* \), where every row of \( Q^* \) equals \( \pi \) [12]. So, \( s_{pwn}(deg(v), \rho) \) converges to \( (K - 1) \times \frac{1}{K} \), this value is same as the upper bound for \( s_{sln} \). We summarize this discussion about \( s_{pwn} \) as:

### Theorem 2. \( s_{pwn}(deg(v), \rho) \), the probability with which the label of node \( v \) is changed in presence of Sequential flipping+PWN model, satisfies the following:

- 1. \( s_{pwn} \) forms a cycle of alternating increasing and decreasing phases. It initially increases, followed by a period of decrease, and this pattern continues.
- 2. For any fixed \( \rho \) we have \( s_{pwn}(deg(v), \rho) = r(deg(v), \rho) \), for \( deg(v) \le K - 1 \).
- 3. \( s_{pwn}(deg(v), \rho) \) converges to \( \frac{K-1}{K} \) as \( deg(v) \to \infty \).

## 4 Experiments and Results

### 4.1 Datasets and their Splits

We test the impact of EDN on existing GNNs and Noise-robust algorithms. using Citeseer [21], Cora [21], and Amazon Photo [22], with splits similar to DeGLIF [14]. Details about dataset statistics are in Table 1. These datasets were selected as they vary in node count, feature dimensions, and average degree.

**Table 1. Dataset Statistics**

| Dataset | # Nodes | # Edges | Feature dim | # Classes |
|---|---|---|---|---|
| CiteSeer | 3,327 | 9,104 | 3,703 | 6 |
| Cora | 2,708 | 10,556 | 1,433 | 7 |
| Amazon Photo | 7,650 | 238,162 | 745 | 8 |

**Datasets Split Details:** We use split similar to [14]. For the Cora dataset, we use 172 nodes per class for training, 500 nodes for validation, and 1000 nodes for testing. For the Citeseer dataset, we use 250 randomly sampled nodes per class for training, 500 nodes for validation, and 1000 nodes for testing. For the Amazon Photo dataset, we use 54 nodes per class for training, 500 nodes in total for validation, and the rest of the nodes for testing. All datasets have been fetched from the PyTorch Geometric library, with feature normalisation being true.

### 4.2 Injecting EDN Noise

The same value of \( \rho \) can lead to different levels of noise using different variants of EDN noise models. Also, as variants of EDN are degree-dependent, graphs with different degree distributions can have different noise levels for the same \( \rho \). Let \( d(n) \) represent the degree distribution of a graph, then the expected noise level in the graph is given by \( \sum_{i=1}^{maxdegree} l(i)d(i) \) where \( l \) is \( q, r \) or \( s \). To make a fair comparison with the existing noise model and among different variants of EDN, we choose different \( \rho \) for each variant and each dataset so that the expected noise level in the graph is the same. A ready-to-refer value of \( \rho \) for different datasets, corresponding to overall noise levels in the graph ranging from 5% to 50% in increments of 5%, is available in Table 6 of the supplementary material.

### 4.3 Experimental Setup

We add different types of noise to data, where the noise level is between 5% and 50% in increments of 5%. GCN, GraphSAGE, GAT and Graph Transformer have been implemented using PyTorch Geometric using GCNConv, SAGEConv, GAT-Conv and Graph Transformer respectively. For GCN and GraphSAGE we use 1 hidden layer of size 16 and relu activation. For GAT and Graph Transformer, we use 1 hidden layer with 8 heads of size 8. For GIN we use implementation by [13]. It is worth mentioning that the comparison is not between GNNs but between different noise models, so using slightly different architectures for different GNNs strengthens our experiments. We use implementation by [13] for all noise-robust algorithms except for DeGLIF, for which we use implementation by [14]. Each experiment is repeated 10 times, with mean ± standard deviation reported. Models are trained on a 24 GB Nvidia RTX 4090 GPU.

![](img/f56761e6196132d5b74909d98468408f_232_0.png)

**Fig. 2.** GCN accuracy at same noise level but different noise models on Citeseer dataset.

### 4.4 Computational Results

In this section, we attempt to empirically understand the impact of EDN on existing graph learning algorithms. To do so we try to answer following questions:

### Q1. How does GCN Architecture Perform in the Presence of EDN?

GCN [23] is one of the widely used GNN architecture, it is also used as a backbone for many noise robust algorithms for graph [9,10,14]. We test GCN under different noise variants of EDN, as well as SLN and PWN. Results for the Citeseer dataset are reported in Fig. 2. Results for all datasets at 5%, 25%, and 45% noise level is presented in Table 2. Due to the large size of tables and lack of space, results for all datasets at all noise levels are provided in Tables 7,8,9 in the supplementary material. GCN performance in the presence of the Majority vote variant is comparable to existing noise models, SLN and PWN. GCN shows more degradation in performance when injected with Veto Power and Sequential flipping variants of EDN as compared to the existing node label noise model. At low noise levels (less than 15%) the gap is low. However, at higher noise levels, veto power and sequential flipping gap widen, and they degrade GCN performance the most.

| GNN Architecture | Noise Level | SLN | MV + SLN | Veto + SLN | Seq + SLN | PWN | MV + PWN | Veto + PWN | Seq + PWN |
|---|---|---|---|---|---|---|---|---|---|
| GCN | 5% | 73.92±1.1 | 72.64±0.5 | 72.27±0.7 | 72.34±0.6 | 73.99±1 | 72.91±0.6 | 72.24±0.6 | 72.23±0.58 |
| | 25% | 65.55±1.74 | 65.34±1.20 | 61.64±1.43 | 61.79±1.42 | 64.29±1.91 | 63.93±1.22 | 58.42±1.76 | 58.17±2.43 |
| | 45% | 52.47±2.39 | 52.33±1.55 | 43.86±2.21 | 45.57±2.21 | 47.30±2.34 | 47.36±1.25 | 37.93±2.02 | 38.05±2.56 |
| GIN | 5% | 71.92±4.50 | 69.52±1.93 | 68.59±2.76 | 67.76±3.35 | 67.09±3.27 | 68.56±3.01 | 68.78±2.22 | 68.58±1.95 |
| | 25% | 60.12±5.71 | 63.39±3.58 | 54.51±4.01 | 55.42±2.66 | 54.22±9.29 | 61.47±3.51 | 49.34±7.72 | 49.98±4.16 |
| | 45% | 42.29±8.80 | 47.87±7.42 | 37.98±5.40 | 39.28±5.53 | 39.19±3.55 | 46.07±6.53 | 34.25±5.86 | 33.50±1.65 |
| GraphSAGE | 5% | 79.95±0.96 | 74.96±0.51 | 74.69±0.49 | 74.61±0.62 | 75.97±0.88 | 75.07±0.56 | 74.00±0.53 | 73.69±1.30 |
| | 25% | 70.96±1.49 | 70.70±1.07 | 68.42±1.36 | 68.99±0.91 | 68.93±1.92 | 68.33±1.07 | 63.27±1.43 | 65.70±2.16 |
| | 45% | 59.61±1.99 | 59.97±1.79 | 52.89±2.11 | 54.17±2.08 | 49.71±2.85 | 49.19±1.56 | 41.19±2.29 | 44.32±4.10 |
| GAT | 5% | 76.46±1.53 | 74.75±0.67 | 74.33±0.89 | 74.36±0.67 | 76.62±1.49 | 74.93±0.85 | 74.39±0.66 | 76.61±1.39 |
| | 25% | 74.59±1.61 | 73.06±1.04 | 71.81±1.06 | 72.16±1.39 | 73.31±1.84 | 71.32±1.50 | 68.13±1.45 | 71.42±2.64 |
| | 45% | 70.88±1.64 | 70.45±1.81 | 66.60±2.33 | 67.51±1.87 | 55.00±3.75 | 53.93±2.64 | 43.41±3.18 | 45.97±6.50 |
| Graph Transformer | 5% | 76.28±0.86 | 75.64±0.52 | 76.28±0.50 | 76.54±0.54 | 76.10±1.40 | 75.50±0.14 | 76.16±0.35 | 75.50±0.95 |
| | 25% | 70.24±1.63 | 70.36±0.60 | 68.84±0.68 | 68.68±0.86 | 68.86±1.03 | 67.48±1.12 | 64.94±0.68 | 65.45±2.00 |
| | 45% | 58.10±1.24 | 59.22±1.42 | 52.38±0.60 | 53.58±0.94 | 49.04±2.25 | 48.94±2.43 | 43.00±1.01 | 44.09±2.77 |
| GCN | 5% | 84.73±0.94 | 85.00±0.44 | 85.19±0.74 | 85.09±0.73 | 84.27±0.98 | 85.36±0.48 | 85.36±0.50 | 84.58±0.54 |
| | 25% | 76.46±1.48 | 77.46±1.99 | 74.49±2.09 | 74.65±2.03 | 71.97±1.77 | 74.84±2.58 | 68.85±2.30 | 70.35±1.44 |
| | 45% | 62.29±2.29 | 63.16±2.94 | 57.12±2.54 | 58.06±2.54 | 50.52±2.76 | 52.86±3.87 | 44.28±2.62 | 50.18±3.92 |
| GIN | 5% | 80.95±2.01 | 81.11±0.88 | 80.45±2.63 | 82.11±2.60 | 80.35±2.38 | 83.34±1.55 | 80.77±2.21 | 79.36±1.99 |
| | 25% | 79.02±2.77 | 77.87±5.65 | 74.90±2.73 | 76.57±2.59 | 73.66±3.74 | 73.32±4.28 | 64.84±3.21 | 67.62±2.51 |
| | 45% | 71.02±4.38 | 75.17±2.36 | 66.79±9.06 | 65.95±1.18 | 48.40±5.01 | 53.90±4.37 | 42.55±10.1 | 48.36±3.33 |
| GraphSAGE | 5% | 83.10±1.19 | 83.38±0.68 | 83.37±1.18 | 83.41±0.90 | 82.84±1.31 | 83.56±0.46 | 83.22±1.13 | 84.43±0.81 |
| | 25% | 70.72±1.85 | 72.39±2.37 | 68.83±1.91 | 69.02±2.12 | 67.69±2.50 | 69.64±2.76 | 66.53±1.93 | 71.62±0.48 |
| | 45% | 55.27±2.50 | 53.93±3.23 | 51.14±2.74 | 51.35±2.62 | 47.20±3.15 | 49.40±3.33 | 46.21±2.12 | 47.7±5.17 |
| GAT | 5% | 79.50±1.80 | 80.05±1.02 | 80.39±1.14 | 80.45±1.20 | 79.35±1.67 | 79.43±1.51 | 79.45±1.37 | 79.06±1.5 |
| | 25% | 70.33±2.16 | 69.58±2.69 | 70.77±2.57 | 70.48±1.44 | 65.87±3.48 | 65.64±2.34 | 64.80±2.47 | 66.09±2.37 |
| | 45% | 57.46±3.68 | 57.14±3.53 | 55.49±2.94 | 55.56±3.14 | 44.76±3.42 | 46.71±3.98 | 43.82±3.07 | 45.25±5.46 |
| Graph Transformer | 5% | 84.42±0.84 | 84.78±0.29 | 84.70±0.41 | 84.64±0.67 | 84.06±0.71 | 84.70±0.14 | 84.96±0.54 | 84.12±0.99 |
| | 25% | 73.30±0.91 | 76.56±0.70 | 77.18±0.67 | 77.50±0.87 | 72.12±1.05 | 72.18±1.08 | 72.88±0.05 | 70.33±2.01 |
| | 45% | 61.16±1.75 | 62.16±1.86 | 61.32±1.56 | 60.62±2.15 | 50.08±2.15 | 51.92±0.92 | 51.28±1.44 | 48.11±2.4 |
| GCN | 5% | 86.78±1.43 | 83.65±6.28 | 85.05±4.56 | 83.55±6.18 | 86.66±1.46 | 84.65±5.59 | 85.35±4.21 | 84.85±2.89 |
| Amazon | 25% | 83.96±2.99 | 78.28±9.38 | 81.87±4.08 | 80.58±7.92 | 77.00±5.47 | 74.15±9.42 | 70.81±7.69 | 66.82±8.03 |
| GraphSAGE | 45% | 73.45±5.67 | 75.36±8.82 | 66.92±11.98 | 67.85±11.36 | 44.15±4.85 | 49.57±7.92 | 40.74±2.65 | 40.03±5.61 |
| | 5% | 80.24±4.32 | 81.32±2.95 | 67.86±17.99 | 64.96±15.31 | 66.24±17.36 | 78.09±23.77 | 77.10±5.15 | 34.24±6.73 |
| Z | 25% | 50.58±19.81 | 67.24±10.88 | 35.04±23.90 | 33.62±8.99 | 50.16±10.90 | 69.38±14.52 | 41.78±10.62 | 33.94±7.74 |
| O | 45% | 34.38±7.71 | 40.28±4.80 | 24.74±4.46 | 27.04±7.18 | 33.52±17.39 | 48.84±17.31 | 25.14±3.94 | 22.58±7.66 |
| GraphSAGE | 5% | 90.56±0.86 | 90.41±0.61 | 90.29±0.82 | 90.20±0.64 | 90.39±1.01 | 90.64±0.50 | 90.29±0.79 | 89.93±1.16 |
| P H | 45% | 65.88±3.47 | 68.72±2.34 | 61.36±4.87 | 62.66±4.42 | 50.78±4.01 | 55.60±4.85 | 47.78±4.23 | 43.61±6.1 |
| GAT | 5% | 78.20±1.79 | 79.07±1.89 | 77.75±1.95 | 77.29±1.60 | 77.36±2.45 | 78.79±1.52 | 76.30±1.64 | 76.81±1.79 |
| | 25% | 63.20±3.03 | 66.08±2.52 | 63.15±3.23 | 62.52±2.51 | 61.62±3.64 | 63.45±3.42 | 61.21±1.97 | 58.14±3.82 |
| O | 45% | 47.79±3.67 | 48.55±3.52 | 46.59±3.19 | 46.70±3.37 | 45.01±2.82 | 47.40±4.53 | 42.69±3.05 | 40.29±4.36 |
| Graph Transformer | 5% | 85.57±0.83 | 80.87±8.55 | 84.13±1.88 | 84.25±1.38 | 85.48±0.95 | 85.80±0.72 | 84.32±1.22 | 84.94±0.61 |
| | 25% | 74.34±3.35 | 76.04±2.34 | 71.73±2.25 | 72.54±3.45 | 71.27±4.41 | 73.05±2.94 | 72.28±1.72 | 69.8±1.86 |
| | 45% | 58.77±2.13 | 58.33±4.13 | 57.54±2.01 | 57.76±1.11 | 54.38±2.85 | 49.03±6.71 | 54.25±3.26 | 49.8±4.64 |

### Q2. How do Other GNN Architectures Perform in the Presence of EDN? Maybe GCN is not robust enough for EDN, what about other GNN architectures, we test common GNN architectures GIN [24], GraphSAGE [25], GAT [26], and Graph Transformer [27]. Result for Citeseer with 40% noise is pictorially reported in Fig. 3. For all datasets at 5%, 25%, and 45% noise levels, result is presented in Table 2. Detailed results for all datasets at all noise levels are in Tables 7,8,9. We observe that, similar to GCN, other GNN architectures’ performance is also degraded more in the presence of Veto power and the Sequential flipping variant of EDN as compared to the existing noise model and majority vote variant.
