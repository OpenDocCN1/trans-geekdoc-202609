knowledge about bots and human users shared across multiple source graphs. Particularly, we learn a cross-source-domain topology to connect each source node to more advantageous neighbors. Although they originate from different source domains than the central node, they likely share similar labels and patterns with it and are located nearby in the embedding space. Thus, their information could contribute to recovering the discriminability of central node embeddings via message-passing.

To start with, for any source node $i$ from source domain $p$, we identify its Top-K similar nodes from all source domains excluding $p$ based on cosine similarity between node embeddings, and we establish cross-domain edges between $i$ and each of these K nodes. Thus, a Top-K sparse topology is created. However, edges may contain sub-optimal cross-domain connections between bots and human users, as the feature-camouflage characteristic of social bots may make their embeddings similar to human users. To score the quality of these edges, we resort to the consistency of local subgraph structures. As social relations are more difficult to camouflage, the local subgraph structure, which reveals account behaviors, could be similar within users in the same class (i.e., bot or human user). However, such subgraph-similarity is challenging for GNNs to capture. Therefore, for any cross-domain edge $E_{ij}^{p,q}$ connecting node $i, j$ from source domains $p$ and $q$, we explicitly assign value $e_{ij}^{p,q}$ to it by measuring structural similarity between 3-hop ego-networks $G^p(i), G^q(j)$ centred at $i$ and $j$, respectively:

```
$$e_{ij}^{p,q} = k(G^p(i), G^q(j)) \in (0, 1)$$ (2)
```

where $k$ indicates graphlet kernel which maps local subgraphs to fixed-dim vectors and calculates such embedding similarity.

Consequently, we conduct message-passing on these cross-source-domain edges to compute enhanced embeddings $Z_C$, which is initialized with $Z_I$. We adopt a 1-layer Graph Attention Network (GAT) encoder $f_a$ for aggregating beneficial information from cross-domain neighbors [28]. Generally, the cross-source-domain message-passing could be represented as:

```
$$Z_{C,i}^{D,(l)} = \sigma(b^c + \sum_{j \in \mathcal{N}(i) \cup i} \alpha_{ij} Z_{C,j}^{D',(l)} W^c)$$ (3)
```

where $D, D' \in \{S_1, \cdots, S_m\}$ and $D \neq D'$. $\mathcal{N}(i)$ refers to cross-domain neighbors of node $i$ from the other source domains. Attention coefficient $\alpha_{ij}$ (simple for $\alpha_{ij}^{D,D'}$) is computed by:

```
$$\alpha_{ij} = \frac{exp(s_{ij})}{\sum_{h \in \mathcal{N}(i)} exp(s_{ih})}$$ $$
s_{ij} = \sigma'(a^c [z_{C,i}^{D,(l)} W^c z_{C,j}^{D',(l)} W^c e_{ij}^{D,D'} W_e^c])$$
```

where $b^c, W^c, a^c$ and $W_e^c$ are parameters of GAT, $\sigma'$ represents LeakyReLU activation.

As the aggregated information from cross-domain neighbors might encompass diverse data distributions, and the updated node embeddings may be noisy. To alleviate this problem and further stabilize the adaptation, we align the latent embedding spaces of source domains with a pairwise regularization $Reg^p$:

```
$$Reg^p = \sum_i \sum_{j, j \neq i} Disc(Z_C^{S_i}, Z_C^{S_j})$$ (4)
```