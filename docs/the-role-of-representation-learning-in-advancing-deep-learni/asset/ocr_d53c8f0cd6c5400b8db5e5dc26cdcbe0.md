# Encoder experiments

This tree encoder addresses the computational cost of global self-attention by restricting the receptive field to small, non-overlapping windows of the input (i.e. local window self-attention). Specifically, the one-stage encoder first groups the node embeddings at level $l$ into non-overlapping windows of shape $K_h \times K_w$, where $K_h$ and $K_w$ are the height and width of the window, respectively. For each window, the tree encoder begins by flattening the node embeddings into a sequence of $K_h \cdot K_w$ vectors. This flattened sequence is then passed through a transformer encoder. Finally, the output of the transformer encoder is averaged to produce a single vector, which represents the embedding of the parent node for that window. The resulting parent node embeddings form the set of nodes at level $l+1$. This process is repeated recursively to construct the tree. Stage I in Figure 6.2 illustrates the one-stage encoder architecture.

Unless otherwise specified, the following hyperparameter values are used for all encoder configurations:

+   - $K_h = 2, K_w = 2$ (window size)
+   - $d_{model} = 256$ (embedding dimension)
+   - $n_{heads} = 8$ (number of attention heads)
+   - Number of encoder layers: 6 (for the two-stage encoder, we use two encoder transformers with 3 layers each to maintain a comparable number of parameters)
+   - Number of decoder layers: 6
+   - $d_{mlp} = 2048$ (hidden dimension of the FFN in the transformer block)

N.B. With a window size of 2x2 and input images of size 512x512, the resulting tree has 5 levels (excluding the root)

The goal of these experiments is to evaluate the impact of the different components of the encoder on model performance. We compare an encoder using global attention, an encoder using only stage I and an encoder using both stage I and stage II with different $n_l$-hop neighborhoods for stage II. We test two configurations: $n_l = 2$ and $n_l = 1, \forall l \in \{0, ..., L-1\}$. In the variable n-hop setting, the number of neighboring nodes varies across levels. Specifically, we test the configuration $n_0 = 2$ and $n_l = 1$ for all $l > 0$. To isolate the effects of the encoder, we do not use a parser in these experiments