# 7.2.5.1 Parameter selection

The ORL face database contains 400 images of 40 people, each containing 10 images. The sample is normalised and the resolution of the image is $64 \times 64$, forming a vector of 4096 dimensions. In this section, let $X = \{x_1, x_2, \ldots, x_N\}$ be a set of training consisting of $N$ samples; $x_i \in R^n$ represents the $i$-th image and $Y = \{y_i, i = 1, 2, \ldots, Ny_i \in R^d\} (d < m)$ denotes the corresponding projection result. Take the weight $W$ between each layer, which can be arbitrarily selected in the range $[-1, 1]$. The ORL face database (10 per person) is divided into five groups; one group is chosen as a training sample, and the remaining groups are used as a test sample.

# 7.2.5.2 Experimental results

The semi-supervised learning based algorithm on the linear Lie group and the semi-supervised learning algorithm based on the parametric Lie group are embedded in the output layer, middle layer, auxiliary layer, and all layers of the three-layer deep structure. The corresponding experimental results are shown in Table 7.1 and Table 7.2, respectively.

From Table 7.1 and Table 7.2, it can be seen that the Lie group semi-supervised learning algorithm works better in all the layers. Therefore, the following set of experiments was conducted in layers 3, 4, 5, and 6 of the deep structure of all layers embedded in the Lie group semi-supervised learning algorithm. The first group of samples was the training sample, and groups 2, 3, and 4 constituted the test sample. The specific experimental results are shown in Fig. 7.5.

Here, Embed_ALL_PLG means that the semi-supervised learning algorithm based on the parameter Lie group is embedded in all the layers of the deep structure; Embed_ALL_GI implies embedding a semi-supervised learning algorithm based on the

**Tab. 7.1:** A semi-supervised learning algorithm based on linear Lie group is embedded on the 3-layer deep structure.

| | Group 1 training Group 2, 3 testing | Group 2 training Group 3, 4 testing | Group 3 training Group 2, 4 testing | Group 4 training Group 1, 3 testing | Average error rate [%] |
|---|---|---|---|---|---|
| Embedded in the output layer | 20/160 | 23/160 | 24/160 | 20/160 | 13.59 |
| Embedded in the middle layer | 19/160 | 21/160 | 25/160 | 21/160 | 13.44 |
| Embedded in the auxiliary layer | 17/160 | 20/160 | 23/160 | 25/160 | 13.28 |
| Embedded in all layers | 18/160 | 22/160 | 19/160 | 18/160 | 12.03 |