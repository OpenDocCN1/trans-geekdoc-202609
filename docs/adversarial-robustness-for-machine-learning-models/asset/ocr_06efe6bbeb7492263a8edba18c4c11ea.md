![](bbox=[0.11, 0.1, 0.84, 0.33])

Figure 16.2 Comparing certified (robust) errors of 1-NN, ConvNet (a simple convolutional network), and RandSmooth (a defense neural network via random smoothing proposed by Cohen et al. (2019)). For RandSmooth, we choose the noise standard deviation \(\sigma = 0.2\). 1-NN is more robust on these two datasets.

# 16.2 Defenses with nearest-neighbor classifiers

We have shown how to compute the robustness of K-NN, but can we use these techniques to improve the robustness of K-NN? The answer is affirmative.

Note that in the original K-NN models defined in the Euclidean space, we measure the distance between two points by \(\|\boldsymbol{x}-\boldsymbol{x}'\|_2\). However, we can generalize the distance measurement to a family of Mahalanobis distances as follows:

```
d_M(\boldsymbol{x}, \boldsymbol{x}') = (\boldsymbol{x}-\boldsymbol{x}')^\top M(\boldsymbol{x}-\boldsymbol{x}'), \quad (16.10)
```

where \(M \in \mathbb{R}^{D \times D}\) is a positive semidefinite matrix. We can then try to learn a positive semidefinite matrix \(M\) to minimize the certified robust training error.

For a classifier \(f\) on an instance \((\boldsymbol{x}, y)\), following the previous sections, we can define the *minimal adversarial perturbation* as

```
\operatorname{argmin}_{\boldsymbol{\delta}} \|\boldsymbol{\delta}\| \quad \text{s.t.} f(\boldsymbol{x} + \boldsymbol{\delta}) \neq y, \quad (16.11)
```

which is the smallest perturbation that could lead to “misclassification”. Note that if \((\boldsymbol{x}, y)\) is not correctly classified, the minimal adversarial perturbation is the zero vector \(\mathbf{0}\). Let \(\boldsymbol{\delta}^*(\boldsymbol{x}, y)\) denote the optimal solution,