

$$
\mathbb{E}\left\lbrack {(\widehat{\mathbf{\theta}} - \mathbf{\theta}_{o})}^{T}(\widehat{\mathbf{\theta}} - \mathbf{\theta}_{o}) \right\rbrack \geq \mathbb{E}\left\lbrack {(\widehat{\mathbf{\theta}}_{\text{LS}} - \mathbf{\theta}_{o})}^{T}(\widehat{\mathbf{\theta}}_{\text{LS}} - \mathbf{\theta}_{o}) \right\rbrack.
$$

![Equation](images/B9780443292385000123/si54.png)(6.9)

确实，从各自的定义可知

$$
\widehat{\mathbf{\theta}} = H(X\mathbf{\theta}_{o} + \mathbf{\eta}) = HX\mathbf{\theta}_{o} + H\mathbf{\eta}.
$$

![Equation](images/B9780443292385000123/si55.png)(6.10)

然而，因为已假设 $\widehat{\mathbf{\theta}}$ 无偏，公式 [(6.10)](#Chp006_249-291_B9780443292385000123.xhtml#deq27) 意味着 $HX = I$ 且

$$
\widehat{\mathbf{\theta}} - \mathbf{\theta}_{o} = H\mathbf{\eta}.
$$

![Equation](images/B9780443292385000123/si58.png)

因此，

$$
\Sigma_{\widehat{\theta}} := \mathbb{E}\left\lbrack (\widehat{\mathbf{\theta}} - \mathbf{\theta}_{o}){(\widehat{\mathbf{\theta}} - \mathbf{\theta}_{o})}^{T} \right\rbrack = \sigma_{\eta}^{2}HH^{T}.
$$

![Equation](images/B9780443292385000123/si59.png)

然而，考虑到 $HX = I$，很容易验证（不妨一试）

