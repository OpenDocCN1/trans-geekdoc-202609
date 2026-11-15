Note that Theorem 4 is a generalization of Lemma 3 to the Mahalanobis distance setting.

By replacing the $\epsilon^*$ in (16.12) with the lower bound derived in Theorem 4 we get a trainable objective function for adversarially robust metric learning:

```
\min_{G \in \mathbb{R}^{D \times D}} \frac{1}{N} \sum_{i=1}^N \ell \left( k\text{-th min}_{j: y_j \neq y_i} k\text{-th max}_{i: l \neq y_l = y_i} \tilde{\epsilon}(\boldsymbol{x}_i, \boldsymbol{x}_j, \boldsymbol{x}_l; M) \right) \text{ s.t. } M = G^\top G. \tag{16.15}
```

Although Eq. (16.15) is trainable since $\tilde{\epsilon}$ is a function of $M$, for large datasets, it is time-consuming to run the inner min-max procedure. Furthermore, since what we really care is the generalization performance of the learned metric instead of the leave-one-out robust training error, it is unnecessary to compute the exact solution. Therefore, instead of computing the $k$-th max and $k$-th min exactly, Wang et al. (2020c) proposed to sample positive and negative instances from the neighborhood of each training instance, which leads to the following formulation:

```
\min_{G \in \mathbb{R}^{D \times D}} \frac{1}{N} \sum_{i=1}^N \ell \left( \tilde{\epsilon} \left( \text{randnear}_M^+(\boldsymbol{x}_i), \text{randnear}_M^-(\boldsymbol{x}_i), \boldsymbol{x}_i; M \right) \right) \text{ s.t. } M = G^\top G, \tag{16.16}
```

where $\text{randnear}_M^+(\cdot)$ denotes a sampling procedure for an instance in the same class within $\boldsymbol{x}_i$’s neighborhood, and $\text{randnear}_M^-(\cdot)$ denotes a sampling procedure for an instance in a different class, also within a neighborhood of $\boldsymbol{x}_i$, and the distances are measured by the Mahalanobis distance $d_M$. Wang et al. (2020c) showed that sampling instances from a fixed number of nearest instances is sufficient. As a result, the optimization formulation (16.16) approximately minimizes the certified robust error and significantly improves computational efficiency.

The overall training algorithm is as follows. At every iteration, $G$ is updated with the gradient of the loss function, whereas the calculations of $\text{randnear}_M^+(\cdot)$ and $\text{randnear}_M^-(\cdot)$ do not contribute to the gradient for efficient and stable computation. The algorithm is called *adversarially robust metric learning* (ARML).

Clearly, ARML can significantly improve the robustness of KNN models. In Table 16.1, we show that in 1-NN, when the exact robustness can be computed by the method mentioned in the previous section, ARML