# 9.3. Single-layer perceptron

A single-layer perceptron consists of multiple neurons organized in one layer. These neurons share the same input features, but each of them produces a different output, as illustrated in Fig. 9.5.

![](bbox=[0.321, 0.203, 0.668, 0.396])

Figure 9.5 A single-layer perceptron consisting of three artificial neurons and three outputs. Each neuron $k$ is mathematically defined as $\hat{y}_k = f(z_k), z_k = \sum_j w_{jk}x_j$. For simplicity, the individual weights have been dropped from the diagram as compared to the diagram of the artificial neuron in Fig. 9.1.

The multi-output single-layer perceptron model can be mathematically written as

$z_k = \sum_{j=0}^D w_{jk}x_j \quad (9.9)$

$\hat{y}_k = f(z_k), \quad k = 1, \dots, K \quad (9.10)$

where the neuron $k$ has the weight vector $(w_{1k}, \dots, w_{Dk})^T$ and the output $\hat{y}_k$. Eq. (9.9) can be conveniently written in a matrix formulation as

$\mathbf{z} = \mathbf{Wx}, \quad (9.11)$

where the matrix $\mathbf{W}$ with shape $K \times (D+1)$ represents the weights of the neurons, $K$ is the number of outputs in the output vector $\mathbf{\hat{y}} =(\hat{y}_1, \dots, \hat{y}_K)^T$, and $D$ is the number of input features arranged in the feature vector $\mathbf{x} = (x_1, \dots, x_D)$. Eq. (9.11) represents one **linear layer**, also called a **fully connected layer**, as all inputs contribute to all outputs. The linear layer with $D$ inputs and $K$ outputs (Eq. (9.11)) is implemented in PyTorch as

```
torch.nn.Linear(D, K)
```

Each output of the linear layer $z_k$ is passed through the same activation function $f$ (Eq. (9.10)) to obtain $\hat{y}_k$.