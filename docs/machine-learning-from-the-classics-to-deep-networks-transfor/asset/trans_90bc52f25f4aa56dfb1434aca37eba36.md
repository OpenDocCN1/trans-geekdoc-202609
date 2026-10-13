

## E-步骤 1c

我们有

$$
\ln q_{\beta}^{(j+1)}(\beta) = \mathbb{E}_{q_{\boldsymbol{\theta}}^{(j+1)} q_{\boldsymbol{\alpha}}^{(j+1)}}[\ln p(\mathbf{y}, \boldsymbol{\theta}, \boldsymbol{\alpha}, \beta)] + \text{常数}
$$

$$
= \mathbb{E}_{q_{\boldsymbol{\theta}}^{(j+1)} q_{\boldsymbol{\alpha}}^{(j+1)}}[\ln p(\mathbf{y}|\boldsymbol{\theta}, \beta) + \ln p(\beta)] + \text{常数}。
$$

这与公式 [(13.36)](#Chp013_635-716_B9780443292385000196.xhtml#deq46) 形式相同，遵循类似的步骤（习题 [13.3](#Chp013_635-716_B9780443292385000196.xhtml#o0115)），可以证明

$$
q_{\beta}^{(j+1)}(\beta) = \text{Gamma}(\beta | \tilde{c}, \tilde{d}),
$$

$$
\tilde{c} = c + \frac{N}{2}。
$$

![Equation](images/B9780443292385000196/si119.png) (13.42)

![Equation](images/B9780443292385000196/si120.png)

![Equation](images/B9780443292385000196/si121.png) (13.43)

![Equation](images/B9780443292385000196/si122.png) (13.44)

