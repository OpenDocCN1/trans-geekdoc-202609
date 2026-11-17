# 9.3.2 Four-Layer Neural Network

We are now ready to take the next step toward neural networks by increasing the number of layers, L, from L = 1 to some number L > 1. But how many layers should be added? This is where the art of designing neural networks comes into play. A variety of experiments may be needed to find the right architecture for a given application. There are some well-known architectures for certain problems but each data science problem may require some amount of tweaking to obtain a suitable architecture. We will not delve deeply into this aspect but rather focus on one specific architecture and how it operates.

First, we need to understand why we have layers in neural networks. To begin the discussion, we start with a training set with four real variables, x1, x2, x3, and x4, and one binary response, y, as shown in Figure 9.2. In the rest of this chapter, each entry in the main table will be referred to as xij and each response in the last column as yi, for i = 1, ..., n and j = 1, ..., d. In this case, d = 4. Suppose we know that a linear boundary may not be sufficient to separate the two classes for this binary classification problem. Then, for a nonlinear boundary, we could simply carry out a polynomial expansion for logistic regression until we achieved sufficient accuracy. Unfortunately, it is not straightforward to do this without some prior domain knowledge. For example, should we use a polynomial expansion of order 4 or 5? Should we include all powers and all the cross terms? Should we take various ratios of different variables? It is a matter of trial-and-error to obtain the right set of features if we wish to proceed in this manner.

A better approach is to use a neural network. If we take 12 computational units of the type shown in Figure 9.1 and arrange them as shown in Figure 9.3 and add one more at the output, the result is a four-layer neural network (with the bias terms not included to reduce clutter in the diagram). The units between the inputs and output are called hidden units and each column of hidden units is called a hidden layer. This NN has three hidden layers and one output layer comprising the four layers.1 The architecture of this particular neural network is symmetric but actual networks can be highly asymmetric. That is,

| i | x1 | x2 | x3 | x4 | y |
|---|---|---|---|---|---|
| 1 | 0.306 | 0.898 | 0.239 | 0.902 | 1 |
| 2 | 0.294 | 0.863 | 0.176 | 0.871 | 1 |
| 3 | 0.361 | 0.835 | 0.125 | 0.863 | 1 |
| 4 | 0.310 | 0.902 | 0.235 | 0.741 | 0 |
| 5 | 0.298 | 0.871 | 0.173 | 0.314 | 1 |
| 6 | 0.365 | 0.863 | 0.122 | 0.302 | 1 |
| 7 | 0.314 | 0.741 | 0.235 | 0.173 | 1 |
| 8 | 0.302 | 0.733 | 0.173 | 0.122 | 0 |
| 9 | 0.369 | 0.745 | 0.122 | 0.235 | 0 |
| 10 | 0.318 | 0.757 | 0.239 | 0.173 | 0 |
| ... | ... | ... | ... | ... | ... |
| n | 0.235 | 0.173 | 0.310 | 0.902 | 0 |

Figure 9.2 Hypothetical training set for neural network.