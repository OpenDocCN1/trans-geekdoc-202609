
$$q(W) := q(\boldsymbol{\beta}, \Theta, \mathbf{k}) = \prod_{i=1}^{T-1} q_{\boldsymbol{\gamma}_i}(\beta_i) \prod_{i=1}^{T} q_{\mathbf{r}_i}(\boldsymbol{\theta}_i) \prod_{n=1}^{N} q_{\boldsymbol{\phi}_n}(k_n).$$

![Equation](images/B9780443292385000196/si519.png) (13.123)

请注意，`θ[i]` 的后验 PDF 估计由变分参数 `r[i]` 控制，且属于指数族，如前所述。指示变量的后验估计被选为具有变分参数 `ϕ[n]` 的多项分布（分类分布）。Beta 变量的后验估计被选为具有变分参数 `γ[i]` 的 Beta 分布。请注意，第一个乘积包含 `T - 1` 个因子。这是由于截断以及概率之和为一的事实。这必然导致 `β[T] = 1`，因此 `q(β[T]) = 1`（问题 [13.21](#Chp013_635-716_B9780443292385000196.xhtml#o0205)）。

下一步是通过最大化不等式 [(12.68)](#Chp012_583-634_B9780443292385000184.xhtml) 中的下界来学习上述后验分布以及所涉及的参数，在我们的情况下，这变为

$$
\ln p(\mathcal{X}; \boldsymbol{\xi}) \ge \mathcal{F}(q; \boldsymbol{\xi}) = \mathbb{E}_q \left[ \ln p(W, \mathcal{X}; \boldsymbol{\xi}) \right] - \mathbb{E}_q \left[ \ln q(W) \right],
$$

![Equation](images/B9780443292385000196/si527.png)
