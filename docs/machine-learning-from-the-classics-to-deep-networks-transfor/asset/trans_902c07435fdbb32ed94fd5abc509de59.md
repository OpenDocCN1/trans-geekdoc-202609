
$$
\alpha_{\ast} = - \frac{\text{MSE}(\widehat{\theta}_{\text{MVU}})}{\text{MSE}(\widehat{\theta}_{\text{MVU}}) + \theta_{o}^{2}} = - \frac{1}{1 + \frac{\theta_{o}^{2}}{\text{MSE}(\widehat{\theta}_{\text{MVU}})}}.
$$

![Equation](images/B9780443292385000093/si149.png) (3.27)

因此，我们找到了一种方法，从集合 $\{\widehat{\theta}[b] = (1 + \alpha)\widehat{\theta}[\text{MVU}] : \alpha \in \mathbb{R}\}$![Equation](images/B9780443292385000093/si150.png) 中获得最优估计量，从而得到最小 MSE。这是正确的，但正如生活中的许多美好事物一样，这通常是不可实现的。$\alpha$ 的最优值是用未知的 $\theta_{o}$![Equation](images/B9780443292385000093/si120.png) 来表示的！然而，公式 [(3.27)](#Chp003_65-117_B9780443292385000093.xhtml#deq46) 在许多其他方面很有用。首先，存在 MSE 与 $\theta_{o}^{2}$![Equation](images/B9780443292385000093/si151.png) 成正比的情况；因此可以使用此公式。此外，对于某些情况，它可用于提供有用的界限 [19]。而且，就本书而言，它说明了一个非常重要的问题。如果我们想要比 MVU 做得更好，那么，查看公式 [(3.26)](#Chp003_65-117_B9780443292385000093.xhtml#deq45) 后面的文字，一种可能的方法是*收缩* MVU 估计量的范数。收缩范数是向估计量引入偏差的一种方法。我们将在第 [3.8](#Chp003_65-117_B9780443292385000093.xhtml#s0055) 节以及后续的第 [6](#Chp006_249-291_B9780443292385000123.xhtml) 章和第 [9](#Chp009_417-462_B9780443292385000159.xhtml) 章中讨论实现这一目标的方法。

请注意，到目前为止我们所说的内容很容易推广到参数向量。无偏参数向量估计量满足

$$
\mathbb{E}[\widehat{\mathbf{\theta}}] = \mathbf{\theta}_{o},
$$

![Equation](images/B9780443292385000093/si152.png)

真值 $\mathbf{\theta}_{o}$![Equation](images/B9780443292385000093/si153.png) 周围的 MSE 定义为
