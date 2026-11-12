Step 5: Residual Connection and Sequence Reduction. Finally, we reintroduce the residual query information by adding back the previously stored queries $\mathbf{Q}_{\text{res}}$, maintaining strong local fidelity:

```
$\mathbf{Y} = \mathbf{O} + \mathbf{Q}_{\text{res}}, \quad \mathbf{Y} \in \mathbb{R}^{B \times M \times D}. \quad (15)$
```

The sequence length is effectively reduced from $N$ to $M$ by selecting a stride $s = 2$, ensuring $M = N/2$. This hierarchical summarization progressively condenses ECG features, capturing local and global information.

Our LG self-attention combines standard self-attention, convolution, and hierarchical transformers while overcoming their limitations. Unlike traditional self-attention, which lacks locality and scales quadratically, or convolutions, which struggle with long-range dependencies, our method extracts locally-informed queries via overlapping convolutional projections while maintaining global attention through sequence-wide keys and values. Additionally, convolutional projections inherently encode positional information, removing the need for explicit positional encodings. The local-global attentions is illustrated in Fig. 2.

![](bbox=[0.16, 0.43, 0.85, 0.6])

Fig. 2. Local-global self-attention operation for one ECG embedding window.

# 3.2 Transformer Block with Local-Global Self-attention

The Transformer Block integrates the local-global self-attention mechanism within a standard transformer architecture. It consists of two sub-layers: LGA and a feed-forward network, both with layer normalization and residual connections for stable training.

Given an input tensor $\mathbf{X} \in \mathbb{R}^{B \times N \times D}$, where $B$ is the batch size, $N$ is the sequence length, and $D$ is the embedding dimension, the Transformer Block initially applies layer normalization along the embedding dimension:

```
$\tilde{\mathbf{X}} = \text{LayerNorm}(\mathbf{X}), \quad \tilde{\mathbf{X}} \in \mathbb{R}^{B \times N \times D}. \quad (16)$
```