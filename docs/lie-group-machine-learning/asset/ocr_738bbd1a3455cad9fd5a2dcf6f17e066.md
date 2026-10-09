Where $x_{i}^{\prime} = x_{i} + \varepsilon_{i}$, $(i = 0, 1, 2, \ldots, k)$ are the neighbour points disturbed by the noise, and the corresponding transformation is as follows:

$$\begin{aligned} x_{0}^{\prime} = \sum_{i = 1}^{k} w^{i^\prime} x_{i}^{\prime}, \sum_{i = 1}^{k} w^{i^\prime} = 1. \end{aligned}\tag{11.3}$$

Here, we have $X^{0} = (x_{1}, x_{2}, \ldots, x_{k})$, $X^{0^\prime} = (x_{1}^{\prime}, x_{2}^{\prime}, \ldots, x_{k}^{\prime})$, $w = (w^{1}, w^{2}, \ldots, w^{k})^{T}$, $w^{\prime} = (w^{1^\prime}, w^{2^\prime}, \ldots, w^{k^{\prime}})^{T}$, and

$$\begin{aligned} x_{0} = X^{0}w, \quad x_{0}^{\prime} = X^{0^\prime}w^{\prime}. \end{aligned}\tag{11.4}$$

In the above case, if each noise point is independent of the other with the same mean value, we have the following definition.

**Definition 11.2.** $M$ is a smooth manifold, $X$ is the sampling point set on the manifold, and $\varepsilon$ represents the neighbour domain of $x_{0}$. Furthermore, $\sigma$ is the additional value of noise, and $\varepsilon^{i}$ represents the $i$-th component of $\varepsilon$. $l = \text{rank}(X^{0})$, $\lambda_{\text{min}}$ is the minimum nonzero eigenvalue of $\varepsilon^{2}\varepsilon$, and $w$ is the corresponding weight value. Suppose that $\delta w = w^{\prime} - w$, then we have the following function:

$$\begin{aligned} E\|\delta w\|^{2} \leq \frac{k(k + 3)}{2\lambda_{\text{min}} l} E\|w^{\prime}\|^{2}. \end{aligned}\tag{11.5}$$

Through the above theoretical analysis, we know that noise consists of two types; one includes the weak spots of the original sample points and the other one does not belong to the former type completely. For the first case, there are many improved methods. Many algorithms consider the first case because they cannot ignore this situation. If we add a regularisation item, we can make the local linear embedding algorithm more robust [3]. The local tangent space alignment algorithm has good anti-noise capacity [4]. The local smoothing algorithm can be regarded as the pre-processing method by using the locally weighted algorithm [5]. These improved methods all focus on the first case. However, this article adopts a new method to eliminate the effect of the second type of noise for maintaining the original advantage. This section regards such noise as a new type of manifold data structure. We separate the noise from the original sample data and handle it. Therefore, we introduce the connection learning algorithm based on frame bundle.

# **11.2 Longitudinal space connection learning model**
**based on frame bundle**

In general, there is no global frame field on manifold $M$ with dimension $m$. Nevertheless, the affine connection exists. Therefore, there is a global frame field in the frame bundle $P$. We can handle multiple manifold structures from this perspective, which is easier than handling the manifold $M$.