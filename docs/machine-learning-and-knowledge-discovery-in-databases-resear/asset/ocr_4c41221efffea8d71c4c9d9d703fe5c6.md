CoAtNet [1] addresses this problem by integrating convolutional inductive biases with global transformers via multi-scale relative attention. While effective, its predefined branches reduce flexibility and increase computational complexity. Similarly, Zhou et al. [20] introduced ELSA, enhancing local feature extraction with Hadamard attention and a ghost head module.

Building upon these strengths and addressing the limitations identified in previous works, the approach we propose introduces a novel local-global attention mechanism designed for ECG signals. Our method efficiently captures both local morphological variations and long-range dependencies while mitigating the computational burden. By leveraging adaptive attention windows and progressive feature aggregation, our approach also enhances ECG feature representation.

# 3 Methods

ECG analysis requires capturing information across multiple temporal scales: wave morphology (P, QRS, T), intra-heartbeat intervals (PR, QT), and inter-beat distances essential for rhythm analysis. We propose a novel self-attention mechanism tailored for ECG signals, which effectively balances fine-grained morphological details with global heartbeat patterns.

The proposed model first uses convolutional layers to project the ECG into an embedding space. Its core comprises layers of a novel windowed self-attention and feed-forward blocks with residual connections. Unlike traditional global self-attention, our method extracts queries (Q) from small overlapping windows to preserve local detail, while keys (K) and values (V) are computed globally, capturing long-range dependencies. Additionally, each self-attention block progressively reduces the sequence length, similar to convolutional pooling, allowing hierarchical abstraction from local waveform characteristics toward global rhythm and beat-to-beat features.

# 3.1 Local-Global Self-attention

The core innovation of our proposed transformer-based architecture lies in its novel local-global self-attention mechanism. Traditional self-attention mechanisms compute interactions uniformly across all tokens, which may overlook crucial local patterns in biomedical signals. In contrast, our method balances fine-grained local feature extraction and broader temporal context modeling.

Let us formally define the input tensor to this attention mechanism as X, with dimensions:

\(\mathbf{X} \in \mathbb{R}^{B \times N \times D},\) (1)

where \(B\) is the batch size, \(N\) the sequence length, and \(D\) the embedding dimension.

**Step 1: Normalization.** First, we apply a standard layer normalization along the embedding dimension to stabilize and normalize the input:

\(\tilde{\mathbf{X}} = \text{LayerNorm}(\mathbf{X}),\quad \tilde{\mathbf{X}} \in \mathbb{R}^{B \times N \times D}.\) (2)