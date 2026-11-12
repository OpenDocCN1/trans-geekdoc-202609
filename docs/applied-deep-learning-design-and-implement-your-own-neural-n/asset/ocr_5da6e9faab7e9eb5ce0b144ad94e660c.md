Figure 4.170 shows the architecture of LeNet-5:

![](bbox=[0.13, 0.13, 0.86, 0.33])

Figure 4.170: LeNet-5 architecture. “Source: Y. LeCun, L. Bottou, Y. Bengio, and P. Haffner. Gradient-based learning applied to document recognition. Proceedings of the IEEE, November 1998”

Table 4.2 shows the detailed architecture of LeNet-5:

| Layer (l) | Input size | No. of Filters ($n_c^l$) | Filter Size (F) | Padding (P) | Stride (S) | Output size | Trainable Parameters | Connections |
|---|---|---|---|---|---|---|---|---|
| Convolution Layer 1 | 32 * 32 * 1 | 6 | (5 * 5 * 1) | 0 | 1 | 28 * 28 * 6 | Weights + Bias = (F * F * $n_c^{l-1}$ * $n_c^l$ + $n_c^l$) = (5 * 5 * 1) * 6 + 6 = 156 | 28 * 28 * 156 = 122304 |
| Pooling Layer 1 (Average Pooling) | 28 * 28 * 6 | 1 | (2 * 2) | 0 | 2 | 14 * 14 * 6 | (Coefficient + Bias) * Filters (1 + 1) * 6 = 12 | 14 * 14 * 30 = 5880 |
| Convolution Layer 2 | 14 * 14 * 6 | 16 | (5 * 5 * 6) | 0 | 1 | 10 * 10 * 16 | Weights + Bias = (F * F * $n_c^{l-1}$ * $n_c^l$ + $n_c^l$) = (5 * 5 * 6) * 16 + 1 = 2416 | 28 * 28 * 2416 = 1894144 |
| Pooling Layer 2 (Average Pooling) | 10 * 10 * 16 | 1 | (2 * 2) | 0 | 2 | 5 * 5 * 16 | (Coefficient + Bias) * Filters (1 + 1) * 16 = 32 | 5 * 5 * 80 = 2000 |