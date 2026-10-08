# Chapter 8

# Backpropagation

In Chapters 6 and 7 we reviewed common deterministic and stochastic GD-type optimization methods used for the training of ANNs. The specific implementation of such methods requires efficient explicit computations of gradients. The most popular and somehow most natural method to explicitly compute such gradients in the case of the training of ANNs is the backpropagation method. In this chapter we derive and present this method in detail.

Further material on the backpropagation method can, for example, be found in the books and overview articles [176], [4, Section 11.7], [60, Section 6.2.3], [63, Section 3.2.3], [97, Section 5.6], and [373, Section 20.6].

# 8.1 Backpropagation for parametric functions

**Proposition 8.1.1** (Backpropagation for parametric functions). Let $L \in \mathbb{N}, l_0, l_1, \ldots, l_L, \mathfrak{d}_1$, $\mathfrak{d}_2, \ldots, \mathfrak{d}_L \in \mathbb{N}$, *for every* $k \in \{1, 2, \ldots, L\}$ *let* $F_k = (F_k(\theta_k, x_{k-1}))_{(\theta_k, x_{k-1}) \in \mathbb{R}^{\mathfrak{d}_k} \times \mathbb{R}^{l_{k-1}}: \mathbb{R}^{\mathfrak{d}_k} \times \mathbb{R}^{l_{k-1}} \to \mathbb{R}^{l_k}$ *be differentiable*, *for every* $k \in \{1, 2, \ldots, L\}$ *let* $f_k = (f_k(\theta_k, \theta_{k+1}, \ldots, \theta_L$, $x_{k-1}))_{(\theta_k, \theta_{k+1}, \ldots, \theta_L, x_{k-1}) \in \mathbb{R}^{\mathfrak{d}_k} \times \mathbb{R}^{\mathfrak{d}_{k+1}} \times \cdots \times \mathbb{R}^{\mathfrak{d}_L} \times \mathbb{R}^{l_{k-1}}: \mathbb{R}^{\mathfrak{d}_k} \times \mathbb{R}^{\mathfrak{d}_{k+1}} \times \cdots \times \mathbb{R}^{\mathfrak{d}_L} \times \mathbb{R}^{l_{k-1}} \to \mathbb{R}^{l_L}$ *satisfy for all* $\vartheta = (\theta_1, \theta_{k+1}, \ldots, \theta_L) \in \mathbb{R}^{\mathfrak{d}_1} \times \mathbb{R}^{\mathfrak{d}_2} \times \cdots \times \mathbb{R}^{\mathfrak{d}_L}, x_{k-1} \in \mathbb{R}^{l_{k-1}}$ *that*

```
$f_k(\theta, x_{k-1}) = (F_L(\theta_L, \cdot) \circ F_{L-1}(\theta_{L-1}, \cdot) \circ \cdots \circ F_k(\theta_k, \cdot))(x_{k-1})$,            (8.1)
```

*let* $\vartheta = (\vartheta_1, \vartheta_2, \ldots, \vartheta_L) \in \mathbb{R}^{\mathfrak{d}_1} \times \mathbb{R}^{\mathfrak{d}_2} \times \cdots \times \mathbb{R}^{\mathfrak{d}_L}, \mathfrak{f}_0 \in \mathbb{R}^{l_0}$, $\mathfrak{f}_1 \in \mathbb{R}^{l_1}, \ldots, \mathfrak{f}_L \in \mathbb{R}^{l_L}$ *satisfy for all* $k \in \{1, 2, \ldots, L\}$ *that*

```
$\mathfrak{f}_k = F_k(\vartheta_k, \mathfrak{f}_{k-1})$,            (8.2)
```

*and let* $D_k \in \mathbb{R}^{l_k \times l_{k-1}}$, $k \in \{1, 2, \ldots, L+1\}$, *satisfy for all* $k \in \{1, 2, \ldots, L\}$ *that* $D_{L+1} = I_{l_L}$ *and*

```
$D_k = D_{k+1} \begin{bmatrix} \frac{\partial F_k}{\partial x_{k-1}} (\vartheta_k, \mathfrak{f}_{k-1}) \end{bmatrix}$            (8.3)
```