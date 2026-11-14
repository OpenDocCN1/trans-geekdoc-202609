$z_t = \mu_t + \sigma_t \odot \in, \in \sim -N(0, I)$

where

$\mu_t, \sigma_t = \text{\textit{BiLSTM}}_\theta(X^t)$

Decoder,

$X'^t = \text{GRU}_\phi(z_t)$

Loss function,

$L_{\text{TVAE}} = E[||X^t - X'^t||^2] + \beta \cdot D_{KL}(q(z|X^t)N(0, I))$

# Step 5: Clinical Text Representation

Each clinical document $d_i \in X^u$ is embedded using BioClinicalBERT.

Tokenization,

$\text{input} = [\text{CLS}] + \text{tokens}(d_i) + [\text{SEP}]$

Embedding,

$e_i = \text{BERT}_{[\text{CLS}]}(d_i) \in R^{768}$

Salient concept detection,

$S_i = \{ c \in d_i \mid c \in \text{UMLS concepts} \}$

Final document vector,

$v_i^{\text{text}} = \text{AttentionPool}(e_i, S_i)$

# Step 6: Multimodal Fusion

Three modalities are combined:

+   - $H_G$: Graph embeddings
+   - $Z_t$: Temporal embeddings
+   - $V_u$: Text embeddings

# Gated Fusion

$F_{fused} = \sigma(W_g[H_G||Z_t||V_u] + b_g)$

where $W_g \in R^{512 \times 3d}$, $\sigma$ is sigmoid gate.