
of information caused by activation quantization; therefore, the proposed method suffers almost no loss of classification accuracy while obtaining more than six times improved memory and computational efficiency.

## 4.2 Rate-distortion theory and sparse encoding

Recently, there has been growing interest in applying information theory to deep neural network activation compression. By interpreting the deep neural network as a lossy data compression approach, the black box of the deep neural network may be opened, and its performance can be optimized by the tool of the rate-distortion theory, which is widely applied in the area of telecommunications [15].

### 4.2.1 Rate-distortion theory

Let the random variable \(\mathbf{X}^{(l)} \in \mathbb{R}^{P \times Q \times K}\) be the floating-point neural network activation tensor associated with the \(l\)th layer, where \(P\), \(Q\), \(K\) are respectively the height, width, and number of feature maps at the \(l\)th layer. The common quantization function \(\mathcal{Q}\) can be written as

```
\(\hat{\mathbf{X}}^{(l)} = \mathcal{Q}(\mathbf{X}^{(l)}),\) \tag{4.1}
```

where \(\hat{\mathbf{X}}^{(l)}\) is the fixed-point representation of the floating-point activation. The goal of lossy data compression is to achieve minimal distortion given the constraint of the maximum code rate. Let \(g\) be the function that indicates the number of bits of the given data. According to the rate-distortion theory, the typical lossy data compression approach attempts to minimize the distortion function \(d\) given the maximum number of bits \(\eta\) as

```
\(\min_{\mathcal{Q}(\cdot)} \mathbb{E}(d(\mathbf{X}^{(l)}, \mathcal{Q}(\mathbf{X}^{(l)}))) \quad \text{s.t. } \mathbb{E}(g(\hat{\mathbf{X}}^{(l)})) \le \eta.\) \tag{4.2}
```

In practice, the quantization function \(\mathcal{Q}\) is nondifferentiable and non-convex due to its integer output, which makes Eq. (4.2) difficult to solve. Different from typical rounding-based quantization approaches that settle for suboptimal solutions, this chapter attempts to find the optimal solution by reformulating Eq. (4.2) as a sparse coding problem.

### 4.2.2 Activation quantization via bitwise bottleneck encoding

In practice, we could approximate the solution of Eq. (4.2) using a training sample set. Assume \(\mathbf{X}_i^{(l)} \in \mathbb{R}^{P \times Q \times K}\) is the floating-point activation tensor

![](img/5fa4874adaccc5ede04575a2e9e5662a_72_0.png)

**Figure 4.1** Illustration of the Bitwise Bottleneck approach. The bitwise bottleneck operation can be inserted in the convolutional neural network for activation quantization. The idea of the proposed method is to substitute the constant levels of the standard quantization, which are the power of two in this example, for variable coefficients. By exploiting the sparsity of the bitwise coefficients, the bottleneck could reduce the number of bits required for activation representation.

associated with the ith sample output by the lth layer. Fig. 4.1 illustrates the Bitwise Bottleneck approach. Formally speaking, assume \(\hat{\mathbf{X}}_i^{(l)}\) is the D-bit fixed-point approximation of \(\mathbf{X}_i^{(l)}\) as defined in Eq. (4.3), where \(\hat{\mathbf{X}}_{ij}^{(l)} \in \{0, 1\}^{P \times Q \times K}\) is a three-dimensional binary tensor representing the jth bit of \(\hat{\mathbf{X}}_i^{(l)}\).

```
\(\hat{\mathbf{X}}_i^{(l)} = \mathcal{Q}(\mathbf{X}_i^{(l)}) = 2^0 \hat{\mathbf{X}}_{i1}^{(l)} + 2^1 \hat{\mathbf{X}}_{i2}^{(l)} + \dots + 2^{D-1} \hat{\mathbf{X}}_{iD}^{(l)}\) (4.3)
```

where, each bitwise data matrix is assigned a constant coefficient of \(2^0, \dots, 2^{D-1}\). In practice, this bitwise activation representation allows the computation of fixed-point data to be implemented in a bitwise way. The computational and memory complexity is proportional to the number of bits of different representations.

Technically, the binary quantization of Eq. (4.3) inherently assumes that each of the D bits in the activation representation is needed, although different bits contain different but fixed amounts of information. By removing this assumption the proposed method substitutes the fixed coefficient for a variable \(\boldsymbol{\alpha}^{(l)} \in \mathbb{R}^D\) as

```
\(\hat{\mathbf{X}}_i^{(l)} = \mathcal{Q}(\mathbf{X}_i^{(l)}) = \alpha_1^{(l)} \hat{\mathbf{X}}_{i1}^{(l)} + \alpha_2^{(l)} \hat{\mathbf{X}}_{i2}^{(l)} + \cdots + \alpha_D^{(l)} \hat{\mathbf{X}}_{iD}^{(l)}.\) (4.4)
```

The Bitwise Bottleneck approach treats the design of neural networks as a trade-off between compression and prediction, which assumes that the

![](img/5fa4874adaccc5ede04575a2e9e5662a_73_0.png)

(a) Activation distribution

![](img/5fa4874adaccc5ede04575a2e9e5662a_73_1.png)

(b) Bitwise rate of code one and coefficients of \(\alpha^{(l)}\)

**Figure 4.2** Featurewise vs. bitwise activation sparsity. (a) The distributions of real-valued (upper) and quantized (lower) activations of the first four layers of ResNet50 [25] over CIFAR10. (b) The average rate of code one of each bit of the quantized activation (upper) and the estimated coefficients \(\alpha^{(l)}\) (lower). It seems that the optimal code rates of different layers depend on the level of activation sparsity, and the Bitwise Bottleneck approach can adaptively remove the near-zero high-end bits and the less-informative low-end bits of the activation representation.

bitwise bottlenecks can exploit the sparsity in the activation representation so that the precision of activation representation without hurting classification accuracy can be reduced. Fig. 4.2 illustrates the activation distributions of the first four layers of ResNet50 [25] over the CIFAR10 dataset. It seems that activations of different layers are sparse, but the sparsity varies from layer to layer. Fig. 4.2(b) illustrates the average rate of code one in each bit of the activation representation (upper graph). Despite the change of featurewise sparsity as shown in Fig. 4.2(a), the bitwise sparsity over the high-end bits of activation representation is easier to detect. Therefore we might be able to estimate the optimal and sparse coefficients \(\boldsymbol{\alpha}^{(l)}\) associated with the most significant bits.

According to the rate-distortion theory (Eq. (4.2)), the Bitwise Bottleneck attempts to find the optimal quantization scheme by minimizing the standard squared distortion rate over \(N\) training samples given that less than \(\eta\) bitwise coefficients are nonzero,

```
\(\begin{aligned} \arg \min_{\boldsymbol{\alpha}^{(l)}} \sum_{i=1}^N \|\mathbf{X}_i^{(l)} - \sum_{j=1}^D \alpha_j^{(l)} \hat{\mathbf{X}}_{ij}^{(l)}\|_2^2 \quad \text{s.t.} \quad \|\boldsymbol{\alpha}^{(l)}\|_0 \le \eta, \end{aligned} \quad (4.5)\)
```

where \(\hat{\mathbf{X}}_{ij}^{(l)}\) calculated by initial quantization operation is usually known as the quantization *codebook*. In practice, different initial quantization operations can be applied, and Eq. (4.3) is a simple example of the rounding quantization approach. It is worth noting that since the number of nonzero coefficients in \(\boldsymbol{\alpha}^{(l)}\) equals the number of bits in the fixed-point representation, the constraint function of Eq. (4.5) actually limits the maximum number of bits in the quantized representation as required by the rate-distortion theory. Recent research shows that Eq. (4.5) is equivalent to the following L1-norm-based problem when fulfilling the sparsity requirement, which leads to a sparse solution [26]:

```
\(\begin{aligned} \arg \min_{\boldsymbol{\alpha}^{(l)}} \sum_{i=1}^N \|\mathbf{X}_i^{(l)} - \sum_{j=1}^D \alpha_j^{(l)} \hat{\mathbf{X}}_{ij}^{(l)}\|_2^2 \quad \text{s.t.} \quad \|\boldsymbol{\alpha}^{(l)}\|_1 \le \eta. \end{aligned} \quad (4.6)\)
```

The bitwise bottleneck operation solves Eq. (4.6) to determine the sparse significant bits and leads to the minimal distortion. In practice, Eq. (4.6) is usually calculated by solving its Lagrangian form as

```
\(\begin{aligned} \arg \min_{\boldsymbol{\alpha}^{(l)}} \sum_{i=1}^N \|\mathbf{X}_i^{(l)} - \sum_{j=1}^D \alpha_j^{(l)} \hat{\mathbf{X}}_{ij}^{(l)}\|_2^2 + \lambda \|\boldsymbol{\alpha}^{(l)}\|_1, \end{aligned} \quad (4.7)\)
```

where \(\lambda\) is the hyperparameter for controlling the trade-off between the optimized error rate and the code rate. Eq. (4.6) generally leads to a sparse solution of the coefficients \(\boldsymbol{\alpha}^{(l)}\), so the activation bits associated with zero coefficients are removed during the inference stage. To avoid expensive computations caused by floating-point, we quantize the coefficient vector \(\boldsymbol{\alpha}^{(l)}\) during the retraining process; therefore, the computational efficiency can be significantly improved.
