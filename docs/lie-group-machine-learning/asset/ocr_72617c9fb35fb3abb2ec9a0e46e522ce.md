Here, if $X_j$ is not the neighbour of $X_i$, then the weight $W_{ij} = 0$ and $\sum_j W_{ij} = 1$. The cumulative value of each row of the weight matrix is 1.

+   (3) To ensure that the weight remains unchanged, in the low-dimensional space, we can minimise the above formula. The original high-dimensional data points are reconstructed to obtain the low-dimensional representation:

$$\phi(Y) = \left| \sum_i Y_i - \sum_j W_{ij} Y_j \right|^2 \, .$$

The local linear embedding (LLE) algorithm is a manifold learning method that preserves local geometry. It has some properties of rotation, translation, and scaling, and can learn the local linear low-dimensional manifolds of arbitrary dimension. This algorithm is simple, the computational complexity and time complexity are relatively low, and it can be attributed to the eigenvalue problem, which is simple and easy.

# 7.2.4 Lie group deep structure learning algorithm

In this section, the deep structure learning and Lie group learning algorithms are combined to give the Lie group deep structure learning algorithm, i.e., Lie group deep structure learning = Lie group machine learning + deep structure learning.

# 7.2.4.1 Deep structure semi-supervised learning algorithm

The deep structure semi-supervised learning algorithm refers to embedding the semi-supervised learning algorithm in the deep structure. Before embedding, we first set up a simple embedded model [22] and divide it into the following steps:

+   1  Choose an unsupervised learning method;
2  Select a model of a deep structure;
3  Unsupervised learning is inserted into every level of the architecture as an auxiliary task;
4  The same structure is used to train supervised and unsupervised tasks.

Deep learning involves learning a model with several layers of nonlinear mapping. Here, we will consider a multilayer network with M-layer hidden units and give a C-dimensional output vector:

```
$$f_i(x) = \sum_{j=1}^{d} w_j^{o,i} h_j^M(x) + b^{o,i}, i=1, \ldots, C \tag{7.4}$$
```

where $w^o$ is the weight of the output layer. The kth layer is defined as

```
$$h_i^k(x) = S\left( \sum_j w_j^{k,i} h_j^{k-1}(x) + b^{k,i} \right), k > 1 \tag{7.5}$$
```