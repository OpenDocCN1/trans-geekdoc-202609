# # Back to optimization over the variational distribution

+   - Lower bound: $\mathcal{L}(q, p) = \frac{1}{N} \sum_{i} \int q_\phi(oldsymbol{z}|oldsymbol{x}_i) \log p_\varphi(oldsymbol{x}_i|oldsymbol{z}) doldsymbol{z} - 	ext{KL}(q_\phi(oldsymbol{z}|oldsymbol{x}_i) || p_\varphi(oldsymbol{z}))$

+   - Distribution: $q_\phi(oldsymbol{z}|oldsymbol{x}) = \mathcal{N}(oldsymbol{z}|\mu_\phi(oldsymbol{x}), \sigma_\phi^2(oldsymbol{x})oldsymbol{I})$

+   - Reparameterization function: $oldsymbol{h}_\phi(oldsymbol{\xi}, oldsymbol{x}) = \mu_\phi(oldsymbol{x}) + \sigma_\phi(oldsymbol{x}) \circ oldsymbol{\xi}$

+   - Reparametrized lower bound:
$\mathcal{L}(q, p) = \frac{1}{N} \sum_{i} \int p(oldsymbol{\xi}) \left( \underbrace{\log p_\varphi(oldsymbol{x}_i|oldsymbol{h}(oldsymbol{\xi}, oldsymbol{x}_i))}_{	ext{reconstruction}} - \underbrace{\log q_\phi(oldsymbol{h}(oldsymbol{\xi}, oldsymbol{x}_i)|oldsymbol{x}_i)}_{	ext{KL-term}} ight)$