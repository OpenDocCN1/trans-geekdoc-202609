
For a lower bound (verification), by extending (16.7) to the K > 1 case we have the following lemma.

### Lemma 3

For a K-NN model with odd K, we have the following lower bound for the minimum adversarial perturbation:

```
\epsilon^* \ge s\text{-th}\min_{j \in [n^+]} \left( s\text{-th}\max_{i \in [n^+]} \sqrt{2\epsilon^{(i,j)}} \right), \quad \text{(16.9)}
```

where s = (K + 1)/2 is a positive integer, “sth min” and “sth max” select the sth minimum value and the sth maximum value, respectively, and

```
\epsilon^{(i,j)} = \frac{\max(\|z - x_j^-\|^2 - \|z - x_i^+\|^2, 0)^2}{8\|x_j^- - x_i^+\|^2}.
```

This is a simple extension of the 1-NN case. Note that the lower bound (16.9) can be efficiently computed. It requires O(n^2 d) time to compute all ε(i,j), and then the top-s selection can be done in linear time, so the overall complexity is just O(n^2 d), which is independent of K.

## Robustness of KNN vs neural network on simple problems

Using the above-mentioned algorithms implemented by Wang et al. (2019c), we are able to 1) efficiently compute the exact robustness of 1-NN models for a reasonable number of examples (e.g., for MNIST dataset, Wang et al. (2019c) showed that we can conduct evaluation in few seconds) and 2) for K-NN models, compute the certified robustness (verification) efficiently using Lemma 3.

With these algorithms, we can then compare the robustness between K-NN models and neural networks. We compare certified robust errors, defined as the fractions with lower bounds less than the given threshold (if an instance is wrongly classified, then the lower bound is 0), of 1-NN, a simple convolutional network (ConvNet), and a strong ℓ2 certified defense network (RandSmooth) (Cohen et al., 2019) in Fig. 16.2 (see Chapter 13 for more details on randomized smoothing). The results show that 1-NN can achieve better certified robust errors than neural networks on these two datasets. This is partially because the proposed verification algorithm provides very tight certified regions for NN classifiers. Note that this is not saying that K-NN is more robust than neural networks on more complex datasets such as CIFAR and ImageNet. However, this is showing K-NN could obtain better certified robust errors on some simpler tasks.

![](img/fa92deee3de0f00ea56e92ca0b92c8e4_180_0.png)

Figure 16.2 Comparing certified (robust) errors of 1-NN, ConvNet (a simple convolutional network), and RandSmooth (a defense neural network via random smoothing proposed by Cohen et al. (2019)). For RandSmooth, we choose the noise standard deviation \(\sigma = 0.2\). 1-NN is more robust on these two datasets.

## 16.2 Defenses with nearest-neighbor classifiers

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

which is the smallest perturbation that could lead to “misclassification”. Note that if \((\boldsymbol{x}, y)\) is not correctly classified, the minimal adversarial perturbation is the zero vector \(\mathbf{0}\). Let \(\boldsymbol{\delta}^*(\boldsymbol{x}, y)\) denote the optimal solution, and let \(\epsilon^*(\mathbf{x}, y) = \|\delta^*(\mathbf{x}, y)\|\) be the optimal value. Since the Mahalanobis K-NN classifier is parameterized by a positive semidefinite matrix \(M\) and the training set \(\mathbb{S}\), we further let the optimal solution \(\delta^*_{\mathbb{S}}(\mathbf{x}, y; M)\) and the optimal value \(\epsilon^*_{\mathbb{S}}(\mathbf{x}, y; M)\) explicitly indicate their dependence on \(M\) and \(\mathbb{S}\).

To learn an \(M\) that leads to robust K-NN, Wang et al. (2020c) define the objective function as

```
\(\min_{G \in \mathbb{R}^{D \times D}} \frac{1}{N} \sum_{i=1}^N \ell \left( \epsilon^*_{\mathbb{S} - \{(x_i, y_i)\}}(\mathbf{x}_i, y_i; M) \right) \text{ s.t. } M = G^\top G,\) (16.12)
```

where \(\ell : \mathbb{R} \to \mathbb{R}\) is a nonincreasing function, e.g., the hinge loss \([1 - \epsilon]_+\), exponential loss \(\exp(-\epsilon)\), logistic loss \(\log(1 + \exp(-\epsilon))\), or "negative" loss \(-\epsilon\). The constraint \(M = G^\top G\) is used to enforce the positive semidefiniteness of the \(M\) matrix, otherwise the Mahalanobis distance defined by \(M\) will not be a valid distance metric. Also, the minimal adversarial perturbation is defined on the training set excluding \((\mathbf{x}_i, y_i)\) itself, since otherwise a 1-nearest neighbor classifier with any distance measurement will have 100% accuracy. Therefore, the above objective can be viewed as minimizing the "leave-one-out" certified robust error.

As mentioned in the previous section, computing the exact \(\epsilon^*_{\mathbb{S}}(\mathbf{x}, y; M)\) is too expensive and becomes impossible when \(K > 1\). Therefore we focus on improving the *certified robust error*. Let \(\underline{\epsilon}^*(\mathbf{x}, y)\) be a lower bound of the norm of the minimal adversarial perturbation \(\epsilon^*(\mathbf{x}, y)\), which can be computed by extending our K-NN certified bound derived in Lemma 3 to the Mahalanobis distance setting. Since the derivation is quite simple, we directly show the results below. The detailed proof can be found in (Wang et al., 2020c).

### Theorem 4 (Robustness verification for Mahalanobis K-NN)

Given a Mahalanobis K-NN classifier parameterized by a neighbor parameter \(K\), a training dataset \(\mathbb{S}\), and a positive semidefinite matrix \(M\), for any instance \((\mathbf{x}_{\text{test}}, y_{\text{test}})\), we have

```
\(\epsilon^*(\mathbf{x}_{\text{test}}, y_{\text{test}}; M) \ge k^{\text{th}} \min_{j: y_j \neq y_{\text{test}}} k^{\text{th}} \max_{i: y_i = y_{\text{test}}} \tilde{\epsilon}(\mathbf{x}_i, \mathbf{x}_j, \mathbf{x}_{\text{test}}; M),\) (16.13)
```

where \(k^{\text{th}}\) max and \(k^{\text{th}}\) min select the \(k\)th maximum and \(k\)th minimum, respectively, with \(k = (K + 1)/2\), and

```
\(\tilde{\epsilon}(\mathbf{x}^+, \mathbf{x}^-, \mathbf{x}; M) = \frac{d_M(\mathbf{x}, \mathbf{x}^-) - d_M(\mathbf{x}, \mathbf{x}^+)}{2\sqrt{(\mathbf{x}^+ - \mathbf{x}^-)^\top M^\top M (\mathbf{x}^+ - \mathbf{x}^-)}}.\) (16.14)
```

Note that Theorem 4 is a generalization of Lemma 3 to the Mahalanobis distance setting.

By replacing the $\epsilon^*$ in (16.12) with the lower bound derived in Theorem 4 we get a trainable objective function for adversarially robust metric learning:

```
\min_{G \in \mathbb{R}^{D \times D}} \frac{1}{N} \sum_{i=1}^N \ell \left( k\text{-th min}_{j: y_j \neq y_i} k\text{-th max}_{l: y_l = y_i} \tilde{\epsilon}(\boldsymbol{x}_i, \boldsymbol{x}_j, \boldsymbol{x}_l; M) \right) \text{ s.t. } M = G^\top G. \tag{16.15}
```

Although Eq. (16.15) is trainable since $\tilde{\epsilon}$ is a function of $M$, for large datasets, it is time-consuming to run the inner min-max procedure. Furthermore, since what we really care is the generalization performance of the learned metric instead of the leave-one-out robust training error, it is unnecessary to compute the exact solution. Therefore, instead of computing the $k$-th max and $k$-th min exactly, Wang et al. (2020c) proposed to sample positive and negative instances from the neighborhood of each training instance, which leads to the following formulation:

```
\min_{G \in \mathbb{R}^{D \times D}} \frac{1}{N} \sum_{i=1}^N \ell \left( \tilde{\epsilon} \left( \text{randnear}_M^+(\boldsymbol{x}_i), \text{randnear}_M^-(\boldsymbol{x}_i), \boldsymbol{x}_i; M \right) \right) \text{ s.t. } M = G^\top G. \tag{16.16}
```

where $\text{randnear}_M^+(\cdot)$ denotes a sampling procedure for an instance in the same class within $\boldsymbol{x}_i$’s neighborhood, and $\text{randnear}_M^-(\cdot)$ denotes a sampling procedure for an instance in a different class, also within a neighborhood of $\boldsymbol{x}_i$, and the distances are measured by the Mahalanobis distance $d_M$. Wang et al. (2020c) showed that sampling instances from a fixed number of nearest instances is sufficient. As a result, the optimization formulation (16.16) approximately minimizes the certified robust error and significantly improves computational efficiency.

The overall training algorithm is as follows. At every iteration, $G$ is updated with the gradient of the loss function, whereas the calculations of $\text{randnear}_M^+(\cdot)$ and $\text{randnear}_M^-(\cdot)$ do not contribute to the gradient for efficient and stable computation. The algorithm is called *adversarially robust metric learning* (ARML).

Clearly, ARML can significantly improve the robustness of KNN models. In Table 16.1, we show that in 1-NN, when the exact robustness can be computed by the method mentioned in the previous section, ARML
