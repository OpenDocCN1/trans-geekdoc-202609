been detected as *changed* pixels by all of the methods except the TCD-Net and dual-channel deep network. The TCD-Net and dual-channel deep network provide significant results compared to other methods in the detection of *no-changed* pixels. However, the TCD-Net (Figure 7g), in detail, discovers subtle *change* pixels better than the dual-channel deep network (Figure 7f). Therefore, the TCD-Net provides a promising result in the detection of both *change* and *no-change* pixels.

![](bbox=[0.11, 0.24, 0.32, 0.38])

![](bbox=[0.35, 0.24, 0.56, 0.38])

![](bbox=[0.6, 0.24, 0.81, 0.38])

![](bbox=[0.11, 0.42, 0.32, 0.56])

![](bbox=[0.35, 0.42, 0.56, 0.56])

![](bbox=[0.6, 0.42, 0.81, 0.56])

![](bbox=[0.11, 0.6, 0.32, 0.74])

![](bbox=[0.35, 0.6, 0.56, 0.74])

Figure 7. Visualized results of various CD methods on dataset#1; (a) PCA_kmeans, (b) NR_ELM, (c) Gabor_PCANet, (d) DP_PCANet, (e) CWNN, (f) dual-channel deep network, (g) TCD-Net, and (h) ground truth. The red circles highlight different output performances in *no-change* pixels.

In Table 6, CD quantitative results show that the TCD-Net algorithm performed better than other methods in terms of OA, KC, precision and DR indicators. In particular, the