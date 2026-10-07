# Binary neural networks 103

![](bbox=[0.215, 0.076, 0.715, 0.169])

(a)

![](bbox=[0.163, 0.213, 0.715, 0.306])

(b)

Figure 5.4 Block structure of (a) conventional CNN and (b) XNOR-Net

Table 5.1 A single neuron i definition in TNNs [26]

| Teacher network | Student network |
|---|---|
| Weights | $W_i = [w_j], w_j \in R$ | $W_i = [w_j], w_j \in \{-1, 0, 1\}$ |
| Bias | $b_i \in R$ | $b^{lower} \in Z, b^{higher} \in Z |
| Transfer function | $y_i = W_i^T X + b_i$ | $y_i = W_i^T X |
| Activation function | $n_i^t = egin{cases} -1 & 	ext{with probability } -\alpha 	ext{ if } \alpha < 0 \ 1 & 	ext{with probability } \alpha 	ext{ if } \alpha > 0 \ 0 & 	ext{otherwise} \end{cases} \\ \alpha = 	anh(y_i), \alpha \in (-1, 1)$ | $n_i^t = egin{cases} -1 & 	ext{if } y_i < b^{lower} \ 1 & 	ext{if } y_i > b^{higher} \ 0 & 	ext{otherwise} \end{cases}$

A recent method in [26] proposes a TNN and restricts both activations and weights to $\{-1, 0, 1\}$. It uses teacher–student methods to train TNNs. In this method, the teacher and student networks have the same architecture, with each neuron according to Table 5.1. In fact, each neuron of student network imitates the equivalent neuron's behavior in the teacher network without any multiplications.

The TNNs make the model sparse by approximating small weights to zero. Sparsity in TNNs is illustrated in Figure 5.5, where $X$ and $Y$ denote inputs and outputs, respectively. weights and activations are demonstrated by lines and circles, respectively. The forward computation is done when both activation and weight are nonzero, weights and activations are shown by lines in Figure 5.5. In other words, the ternized neural network is a sparse BNN that performs computations, only when both activation and weight are nonzero.