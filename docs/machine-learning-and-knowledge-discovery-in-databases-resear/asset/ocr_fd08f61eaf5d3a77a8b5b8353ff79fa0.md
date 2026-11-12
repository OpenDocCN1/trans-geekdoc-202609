information into each node's representation:

$$
\mathbf{X} = \text{LocalStructureEncoder}(\mathcal{G}(E, X)),
\quad (1)
$$

where \(\mathbf{X} \in \mathbb{R}^{N \times F}\) denotes the encoded feature matrix, and \(F\) is the hidden dimension. We adopt graph convolutional networks as the local structure encoder.

To ensure a differentiable community assignment process and prevent excessive community sizes that may cause memory overflow and semantic imbalance, we design a classification-based assignment strategy with a constraint on the"average community size \(N_m = \lceil \frac{N}{M} \rceil\)", where \(M\) is the number of communities. We formulate node assignment as a classification problem and apply the softmax function to normalize the probability \(Z'_{i,j}\) of assigning node \(i\) to community \(j\):

$$
\mathbf{Z} = \mathbf{X}\mathbf{W}_{\text{C}}, \quad Z'_{i,j} = \frac{\exp(\mathbf{Z}_{i,j})}{\sum_{k=1}^M \exp(\mathbf{Z}_{i,k})},
\quad (2)
$$

where \(\mathbf{W}_{\text{C}} \in \mathbb{R}^{F \times M}\) is a learnable matrix, and \(\mathbf{Z}\) is the assignment score matrix. We enforce a fixed number of nodes, \(N_m\), per community by sorting nodes based on assignment probabilities and selecting the top \(N_m\) nodes. Then, we assign a learnable community position embedding \(\mathbf{E}_m \in \mathbb{R}^F\) to each community \(C_m\) to distinguish its semantics and enhance intra-community node consistency:

$$
\mathbf{X}'_i = \mathbf{X}_i + \mathbf{E}_m(i \in C_m),
\quad (3)
$$

Based on node-community affiliations, we obtain the reorganized feature matrix \(\mathbf{X}' \in \mathbb{R}^{M \times N_m \times F}\), which incorporates twofold positional semantics. Here, \(\mathbf{X}'[m, :, :]\) represents the features of all nodes in \(C_m\).

# ### 4.3 Hierarchical and Parallel Transformer Computation

We employ hierarchical aggregation to achieve global feature interaction while mitigating the information over-squeezing problem. First, we compute the query, key, and value matrices for each community \(C_m\). We directly feed \(\mathbf{X}'\) into linear layers to compute the \(\mathbf{Q}\), \(\mathbf{K}\), and \(\mathbf{V}\) in parallel, which reduces memory peak usage because the tensor size of each community is much smaller than the original \(\mathbf{X}\):

$$
\mathbf{Q}_m = \mathbf{W}_Q \mathbf{X}'_m, \quad \mathbf{K}_m = \mathbf{W}_K \mathbf{X}'_m, \quad \mathbf{V}_m = \mathbf{W}_V \mathbf{X}'_m,
\quad (4)
$$

where \(\mathbf{W}_{(\cdot)}\) are learnable weights, \(F\) is the hidden dimension, \(\mathbf{X}'_m\) is \(\mathbf{X}'[m, :, :]\). To mitigate the information over-squeezing issue caused by the \(O(N^2)\) level of feature interactions among all nodes globally, we introduce community-level features to replace node-level interactions outside the community. Nodes within the same community interact via node features, while nodes from different communities engage through a set of community-level features. Since community features have higher semantic consistency and are much fewer in number compared to node features, they effectively prevent information over-squeezing and high noise within node features, thereby improving the efficiency of feature interactions.