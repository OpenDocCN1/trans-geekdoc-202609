
$$
\Sigma_{\theta|y} = \left( \frac{1}{\sigma_{\theta}^{2}}I + \frac{1}{\sigma_{\eta}^{2}}\Phi^{T}\Phi \right)^{-1}
$$

![Equation](images/B9780443292385000184/si70.png)(12.19)

$$
\mathbf{\mu}_{\theta|y} = \mathbf{\theta}_{0} + \frac{1}{\sigma_{\eta}^{2}}\left( \frac{1}{\sigma_{\theta}^{2}}I + \frac{1}{\sigma_{\eta}^{2}}\Phi^{T}\Phi \right)^{-1}\Phi^{T}\left( \mathbf{y} - \Phi\mathbf{\theta}_{0} \right).
$$

![Equation](images/B9780443292385000184/si71.png)(12.20)

The integration in Eq. [(12.18)](#Chp012_583-634_B9780443292385000184.xhtml#deq21) can now be carried out analytically as in Eqs. (12.136) and (12.137) and using Eqs. (12.150) and (12.151) in the appendix, with **z** → **θ**, **t** → **y**, **A** → **ϕ**^(T), **μ**[**z**] → **μ**[**θ**|**y**], **Σ**[**z**] → **Σ**[**θ**|**y**], **Σ**[**t**|**z**] → **σ**[**η**]².

![Equation](images/B9780443292385000184/si72.png)

and we obtain

![Equation](images/B9780443292385000184/fx002.jpg)(12.21)

where

$$
\mu[y] = \phi^{(T)}(\mathbf{x})\mu[\theta|y]
$$

![Equation](images/B9780443292385000184/si73.png)(12.22)
