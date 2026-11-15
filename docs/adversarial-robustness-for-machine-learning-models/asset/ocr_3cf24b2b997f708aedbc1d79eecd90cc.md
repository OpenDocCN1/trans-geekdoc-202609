and let \(\epsilon^*(\mathbf{x}, y) = \|\delta^*(\mathbf{x}, y)\|\) be the optimal value. Since the Mahalanobis K-NN classifier is parameterized by a positive semidefinite matrix \(M\) and the training set \(\mathbb{S}\), we further let the optimal solution \(\delta^*_{\mathbb{S}}(\mathbf{x}, y; M)\) and the optimal value \(\epsilon^*_{\mathbb{S}}(\mathbf{x}, y; M)\) explicitly indicate their dependence on \(M\) and \(\mathbb{S}\).

To learn an \(M\) that leads to robust K-NN, Wang et al. (2020c) define the objective function as

```
\(\min_{G \in \mathbb{R}^{D \times D}} \frac{1}{N} \sum_{i=1}^N \ell \left( \epsilon^*_{\mathbb{S} - \{(x_i, y_i)\}}(\mathbf{x}_i, y_i; M) \right) \text{ s.t. } M = G^\top G,\) (16.12)
```

where \(\ell : \mathbb{R} \to \mathbb{R}\) is a nonincreasing function, e.g., the hinge loss \([1 - \epsilon]_+\), exponential loss \(\exp(-\epsilon)\), logistic loss \(\log(1 + \exp(-\epsilon))\), or "negative" loss \(-\epsilon\). The constraint \(M = G^\top G\) is used to enforce the positive semidefiniteness of the \(M\) matrix, otherwise the Mahalanobis distance defined by \(M\) will not be a valid distance metric. Also, the minimal adversarial perturbation is defined on the training set excluding \((\mathbf{x}_i, y_i)\) itself, since otherwise a 1-nearest neighbor classifier with any distance measurement will have 100% accuracy. Therefore, the above objective can be viewed as minimizing the "leave-one-out" certified robust error.

As mentioned in the previous section, computing the exact \(\epsilon^*_{\mathbb{S}}(\mathbf{x}, y; M)\) is too expensive and becomes impossible when \(K > 1\). Therefore we focus on improving the *certified robust error*. Let \(\underline{\epsilon}^*(\mathbf{x}, y)\) be a lower bound of the norm of the minimal adversarial perturbation \(\epsilon^*(\mathbf{x}, y)\), which can be computed by extending our K-NN certified bound derived in Lemma 3 to the Mahalanobis distance setting. Since the derivation is quite simple, we directly show the results below. The detailed proof can be found in (Wang et al., 2020c).

# **Theorem 4** (Robustness verification for Mahalanobis K-NN). Given a Mahalanobis K-NN classifier parameterized by a neighbor parameter \(K\), a training dataset \(\mathbb{S}\), and a positive semidefinite matrix \(M\), for any instance \((\mathbf{x}_{text}, y_{text})\), we have

```
\(\epsilon^*(\mathbf{x}_{text}, y_{text}; M) \ge k^{th} \min_{j: y_j \neq y_{text}} k^{th} \max_{i: y_i = y_{text}} \tilde{\epsilon}(\mathbf{x}_i, \mathbf{x}_j, \mathbf{x}_{text}; M),\) (16.13)
```

where \(k^{th}\) max and \(k^{th}\) min select the \(k\)th maximum and \(k\)th minimum, respectively, with \(k = (K + 1)/2\), and

```
\(\tilde{\epsilon}(\mathbf{x}^+, \mathbf{x}^-, \mathbf{x}; M) = \frac{d_M(\mathbf{x}, \mathbf{x}^-) - d_M(\mathbf{x}, \mathbf{x}^+)}{2\sqrt{(\mathbf{x}^+ - \mathbf{x}^-)^\top M^\top M (\mathbf{x}^+ - \mathbf{x}^-)}}.\) (16.14)
```