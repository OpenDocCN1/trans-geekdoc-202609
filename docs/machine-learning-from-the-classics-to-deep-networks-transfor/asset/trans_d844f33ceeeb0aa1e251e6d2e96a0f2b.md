

其中 `y` 为输出观测值向量，`Z` 为相应潜变量矩阵。对数似然可直接写为

$$
\ln p(\mathbf{y},Z;\mathbf{\Xi},\mathbf{P}) = \sum\limits_{n = 1}^{N}\sum\limits_{k = 1}^{K}z_{nk}\ln\left( P_{k}\mathcal{N}\left( y_{n}|\mathbf{\theta}_{k}^{T}\mathbf{x}_{n},\sigma_{\eta}^{2} \right) \right).
$$

![Equation](images/B9780443292385000184/si394.png)(12.97)

现在我们可以给出 EM 算法的步骤。从某些初始条件 `Ξ^((0))`、`P^((0))` 开始，第 (`j` + 1) 次迭代由下式给出：

*   **E-步：**

$$
\mathcal{Q}(\mathbf{\Xi},\mathbf{P};\mathbf{\Xi}^{(j)},\mathbf{P}^{(j)}) = \mathbb{E}_{Z}\left\lbrack \ln p(\mathbf{y},Z;\mathbf{\Xi},\mathbf{P}) \right\rbrack = \sum\limits_{n = 1}^{N}\sum\limits_{k = 1}^{K}\mathbb{E}\lbrack z_{nk}\rbrack\ln\left( P_{k}\mathcal{N}\left( y_{n}|\mathbf{\theta}_{k}^{T}\mathbf{x}_{n},\sigma_{\eta}^{2} \right) \right).
$$

![Equation](images/B9780443292385000184/si397.png)

*   然而，

