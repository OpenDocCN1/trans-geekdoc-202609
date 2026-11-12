
multiple source domains and adapts it to the target domain with a domain-level weighting strategy. Finally, the AR module refines the classification results output by the under-fitted source classifier during the inference stage. We discuss the details of BotTrans in the following sections.

![](img/f56761e6196132d5b74909d98468408f_296_0.png)

## 4.1 Cross Source Domain Message-Passing

Generally, the CSD-MP module generates node embeddings for all source and target domains. It additionally enhances the discriminability of source node embeddings to facilitate the transfer of more bot-related knowledge. Besides, it aligns the latent embedding spaces of multiple source domains, promoting more stable adaptation from multiple sources to the target.

Given $m$ source graphs $(G^{S_1}, \cdots, G^{S_m})$ and a target graph $G^T$, we first utilize a shared GNN encoder $f$ to generate node embeddings $Z_I$ via message-passing inside each network, which is called in-domain message-passing. Take the $l^{th}$ layer of GCN [18] as an example, the in-domain message-passing for computing the embedding of node $i$ from domain $D$ is:

$Z_{D,i}^{D,(l)} = \sigma(b^{(l-1)} + \sum_{j \in \mathcal{N}(i) \cup i} \frac{1}{c_{ij}} Z_{i,j}^{D,(l-1)} W^{(l-1)}) \quad (1)$

where $D \in \{S_1, \cdots, S_m, T\}$, $b^{(l-1)}$ and $W^{(l-1)}$ are parameters; $\mathcal{N}(i)$ represents all one-hop neighbors of node $i$ and $c_{ij} = \sqrt{|\mathcal{N}(i)| \sqrt{|\mathcal{N}(j)|}$. $\sigma$ denotes non-linear activation like ReLU.

Following in-domain message-passing, we aim to enhance the discriminability of node embeddings deteriorated by network heterophily. While existing works focus on addressing this problem within the task graph [6,36,39], we instead explore common knowledge about bots and human users shared across multiple source graphs. Particularly, we learn a cross-source-domain topology to connect each source node to more advantageous neighbors. Although they originate from different source domains than the central node, they likely share similar labels and patterns with it and are located nearby in the embedding space. Thus, their information could contribute to recovering the discriminability of central node embeddings via message-passing.

To start with, for any source node $i$ from source domain $p$, we identify its Top-K similar nodes from all source domains excluding $p$ based on cosine similarity between node embeddings, and we establish cross-domain edges between $i$ and each of these K nodes. Thus, a Top-K sparse topology is created. However, edges may contain sub-optimal cross-domain connections between bots and human users, as the feature-camouflage characteristic of social bots may make their embeddings similar to human users. To score the quality of these edges, we resort to the consistency of local subgraph structures. As social relations are more difficult to camouflage, the local subgraph structure, which reveals account behaviors, could be similar within users in the same class (i.e., bot or human user). However, such subgraph-similarity is challenging for GNNs to capture. Therefore, for any cross-domain edge $E_{ij}^{p,q}$ connecting node $i, j$ from source domains $p$ and $q$, we explicitly assign value $e_{ij}^{p,q}$ to it by measuring structural similarity between 3-hop ego-networks $G^p(i), G^q(j)$ centred at $i$ and $j$, respectively:

$$e_{ij}^{p,q} = k(G^p(i), G^q(j)) \in (0, 1)$$ (2)

where $k$ indicates graphlet kernel which maps local subgraphs to fixed-dim vectors and calculates such embedding similarity.

Consequently, we conduct message-passing on these cross-source-domain edges to compute enhanced embeddings $Z_C$, which is initialized with $Z_I$. We adopt a 1-layer Graph Attention Network (GAT) encoder $f_a$ for aggregating beneficial information from cross-domain neighbors [28]. Generally, the cross-source-domain message-passing could be represented as:

$$Z_{C,i}^{D,(l)} = \sigma(b^c + \sum_{j \in \mathcal{N}(i) \cup i} \alpha_{ij} Z_{C,j}^{D',(l)} W^c)$$ (3)

where $D, D' \in \{S_1, \cdots, S_m\}$ and $D \neq D'$. $\mathcal{N}(i)$ refers to cross-domain neighbors of node $i$ from the other source domains. Attention coefficient $\alpha_{ij}$ (simple for $\alpha_{ij}^{D,D'}$) is computed by:

$$\alpha_{ij} = \frac{exp(s_{ij})}{\sum_{h \in \mathcal{N}(i)} exp(s_{ih})}$$

$$s_{ij} = \sigma'(a^c [z_{C,i}^{D,(l)} W^c z_{C,j}^{D',(l)} W^c e_{ij}^{D,D'} W_e^c])$$

where $b^c, W^c, a^c$ and $W_e^c$ are parameters of GAT, $\sigma'$ represents LeakyReLU activation.

As the aggregated information from cross-domain neighbors might encompass diverse data distributions, and the updated node embeddings may be noisy. To alleviate this problem and further stabilize the adaptation, we align the latent embedding spaces of source domains with a pairwise regularization $Reg^p$:

$$Reg^p = \sum_i \sum_{j, j \neq i} Disc(Z_C^{S_i}, Z_C^{S_j})$$ (4)

where $Disc$ indicates discrepancy measurement (e.g., Maximum Mean Discrepancy). Finally, the overall embedding $z_i$ for any source node $i$ is obtained by aggregating embeddings from both in-domain ($Z_{I,i} \in \mathbb{R}^h$, Eq. 1) and cross-domain ($Z_{C,i} \in \mathbb{R}^h$, Eq. 3) channels, which enhances the discriminability of node embeddings while accurately encoding the inherent knowledge within each source domain:

$z_i = \beta_1 Z_{I,i} + \beta_2 Z_{C,i}$ (5)

where coefficients $\beta_1$ and $\beta_2$ are computed by applying a linear transformation matrix $W^{cat}$ mapping from $\mathbb{R}^{2h}$ to $\mathbb{R}^2$:

$\beta_{1(2)} = \frac{exp(W^{cat}[Z_{I,i} || Z_{C,i}]_{1(2)}}{\sum_{h \in \{1,2\}} exp(W^{cat}[Z_{I,i} || Z_{C,i}]_h)}$

## 4.2 Selective Multi-source Transfer

Following the network embedding via Eq. 5, we selectively transfer knowledge from multiple source graphs. The key idea is measuring the relevance between each source and target graph, i.e., $(G^{S_k}, G^T)$. In this section, we first introduce a trivial multi-source adaptation pipeline to learn network-invariant and label-related embeddings with adversarial domain adaptation technique, then we discuss how to improve it in multi-source tasks.

First of all, we use available labels in all source domains to train a shared classifier $g$, which will let source domain embeddings learn label-related knowledge:

$L^{sup} = - \sum_k \frac{1}{n^k} \sum_{i=1}^{n^k} y_i^{S_k} log(g(f(z_i^{S_k})))$ (6)

where $i$ indicates the $i^{th}$ node, $S_k$ is the $k^{th}$ source domain, $n^k$ is the number of training samples from source graph $G^{S_k}$, $y_i^{S_k}$ is groundtruth label of node $i$ and $g(f(z_i^{S_k}))$ is the predicted logits.

Following the supervised training on source graphs, we eliminate domain discrepancy by modelling it with Wasserstein-1 distance, which has been proven to be effective in previous studies [14, 37]. Consequently, we could learn network-invariant embeddings and transfer label-related knowledge from source to target graphs. Generally, the first Wasserstein distance between the source and target distributions of node embedding $Z^{S_k}$ and $Z^T$ is formulated as:

$W_1(Z^{S_k}, Z^T) = \sup_{||d||_L \le 1} \mathbb{E}_{z \sim Z^{S_k}}[d(z)] - \mathbb{E}_{z' \sim Z^T}[d(z')]$ (7)

where $||d||_L \le 1$ is Lipschitz continuity constraint, and $d$ is domain critic outputting a real number for any input node embedding. In practice, we approximate Eq. 7 by maximizing the following domain critic loss:

$L^d = \sum_k \frac{1}{n^{S_k}} \sum_i^{n^{S_k}} d(z_i^{S_k}) - \frac{1}{n^T} \sum_j^{n^T} d(z_j^T)$ (8)

Therefore, by regarding the encoder \( f \) from network embedding as generator and the domain critic \( d \) as discriminator, we solve the following minimax problem:

\(\min_{\Theta_f, \Theta_{oth}} \max_{\Theta_d} L^d\)

where \(\Theta_f\), \(\Theta_d\) denote encoder and classifier parameters, and \(\Theta_{oth}\) includes all other model parameters including \( f_a \) and \( W^{cat} \).

In the above trivial settings, all sources are equally adapted to the target. Given the varying degrees of relevance between each source domain and the task, assigning equal weight to sources during supervised training and adaptation may either introduce noisy and irrelevant information from low-relevant sources or neglect beneficial knowledge from high-relevant sources, potentially impairing adaptation performance. To address this problem, we compute domain-level similarity \( w^k \) between each source graph \( G^{S_k} \) and target graph \( G^T \). Subsequently, we employ a selective knowledge transfer strategy:

\( L^{sup} = - \sum_k \frac{w^k}{n^k} \sum_{i=1}^{n^k} y_i^{S_k} log(g(f(z_i^{S_k})))\)
\( L^d = \sum_k w^k (\frac{1}{n^k} \sum_i^{n^k} d(z_i^{S_k}) - \frac{1}{n^T} \sum_j^{n^T} d(z_j^T)) \) (9)

Generally, the weighted \( L^{sup} \) and \( L^d \) encourage the model to learn bot-related patterns and transfer more knowledge from source graphs that are more similar to target graph, respectively.

The domain-level weight \( w^k \) simultaneously models semantic and structural similarities between the source and target domains. First of all, as the output by domain discriminator \( d \) directly measures similarity between latent embedding spaces, we take it into account and compute semantic similarity score \( w^{k,d} \in (0, 1) \):

\( w^{k,d} = \exp(-|\frac{1}{n^k} \sum_i^{n^k} d(z_i^{S_k}) - \frac{1}{n^T} \sum_j^{n^T} d(z_j^T)|)\)

Moreover, measuring the consistency of user behaviors from different domains is equally important because users usually exhibit different social behaviors on platforms with varying functionalities. These social behaviors are characterized by social relationships. Therefore, we apply graphlet kernel to compute structural similarity score \( w^{k,g} \in (0, 1) \) between topologies of each source graph \( G^{S_k} \) and target graph \( G^T \): \( w^{k,g} = k(G^{S_k}, G^T) \), which is similar with Eq. 2. Consequently, \( w^k \) is computed from both semantic and structure channels:

\( w^k = \gamma w^{k,d} + (1 - \gamma) w^{k,g} \) (10)

where balancing coefficient \( \gamma \) is set manually.
