
## GANs: a variant of ADA
- Transfer the properties of source domain to target domain
- Source domain: e.g. real image, $y = 1$
- Target domain: e.g. generated image, $y = 0$

![](img/cb490ed30bca4eda5fbba81c52a2c173_136_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_136_1.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_137_0.png)

## GANs: a variant of ADA
- Implicit distribution over $x \sim p_\theta(x\mid y)$

$$p_\theta(x\mid y)=\begin{cases}p_{g_\theta}(x) & y=0 \quad \text{(distribution of generated images)}\\p_{data}(x) & y=1. \quad \text{(distribution of real images)}\end{cases}$$

- $x \sim p_{g_\theta}(x) \Longleftrightarrow x=G_\theta(z),\ z\sim p(z\mid y=0)$
- $x \sim p_{data}(x)$
  - the code space of $z$ is degenerated
  - sample directly from data

## GANs: new formulation
- Again, rewrite GAN objectives in the "variational-EM" format
- Recap: conventional formulation:
  $$\max_{\phi} \mathcal{L}_{\phi} = \mathbb{E}_{\boldsymbol{x}=G_{\theta}(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=0)}[\log(1 - D_{\phi}(\boldsymbol{x}))] + \mathbb{E}_{\boldsymbol{x}\sim p_{data}(\boldsymbol{x})}[\log D_{\phi}(\boldsymbol{x})]$$
  $$\max_{\theta} \mathcal{L}_{\theta} = \mathbb{E}_{\boldsymbol{x}=G_{\theta}(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=0)}[\log D_{\phi}(\boldsymbol{x})] + \mathbb{E}_{\boldsymbol{x}\sim p_{data}(\boldsymbol{x})}[\log(1 - D_{\phi}(\boldsymbol{x}))]$$
  $$= \mathbb{E}_{\boldsymbol{x}=G_{\theta}(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=0)}[\log D_{\phi}(\boldsymbol{x})]$$
- Rewrite in the new form
  $$\max_{\phi} \mathcal{L}_{\phi} = \mathbb{E}_{p_{\theta}(\boldsymbol{x}|y)p(y)}[\log q_{\phi}(y|\boldsymbol{x})]$$
  $$\max_{\theta} \mathcal{L}_{\theta} = \mathbb{E}_{p_{\theta}(\boldsymbol{x}|y)p(y)}[\log q_{\phi}^{r}(y|\boldsymbol{x})]$$
- Exactly the same with ADA !
- The same correspondence to variational EM !

![](img/cb490ed30bca4eda5fbba81c52a2c173_138_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_141_0.png)

## GANs: minimizing KLD
- As in Variational EM, we can further rewrite in the form of **minimizing KLD** to reveal more insights into the optimization problem

- For each optimization step of $p_{\theta}(x|y)$ at point $(\theta=\theta_0,\phi=\phi_0)$, let
  - $p(y)$: a uniform distribution
  - $p_{\theta=\theta_0}(x)=\mathbb{E}_{p(y)}[p_{\theta=\theta_0}(x|y)]$: prior distribution over $x$
  - $q^r(x|y)\propto q^r_{\phi=\phi_0}(y|x)p_{\theta=\theta_0}(x)$: posterior distribution over $x$

- **Lemma 1:** The updates of $\theta$ at $\theta_0$ have

$$
\left.\nabla_{\theta}\left[-\mathbb{E}_{p_{\theta}(x|y)p(y)}\left[\log q^r_{\phi=\phi_0}(y|x)\right]\right]\right|_{\theta=\theta_0}
=
\left.\nabla_{\theta}\left[\mathbb{E}_{p(y)}\left[KL\left(p_{\theta}(x|y)\|q^r(x|y)\right)-JSD\left(p_{\theta}(x|y=0)\|p_{\theta}(x|y=1)\right)\right]\right]\right|_{\theta=\theta_0}
$$

- KL: KL divergence
- JSD: Jensen-Shannon divergence

## GANs: minimizing KLD

![](img/cb490ed30bca4eda5fbba81c52a2c173_142_0.png)

- *Lemma 1*: The updates of θ at θ₀ have
  ∇_θ[ - 𝔼_{p_θ(x|y)p(y)}[log q^r_{φ=φ₀}(y|x)] ]|_{θ=θ₀} =
  ∇_θ[ 𝔼_{p(y)}[KL(p_θ(x|y)||q^r(x|y))] - JSD(p_θ(x|y=0)||p_θ(x|y=1)) ]|_{θ=θ₀}
- Connection to variational inference
  - See x as latent variables, y as visible
  - p_{θ=θ₀}(x): prior distribution
  - q^r(x|y) ∝ q^r_{φ=φ₀}(y|x)p_{θ=θ₀}(x) : posterior distribution
  - p_θ(x|y): variational distribution
    - Amortized inference: updates model parameter θ
- Suggests relations to VAEs, as we will explore shortly

## GANs: minimizing KLD
$p_{\theta=\theta_0}(\mathbf{x}|y=1)=p_{data}(\mathbf{x})$  $p_{\theta=\theta_0}(\mathbf{x}|y=0)=p_{g\,\theta=\theta_0}(\mathbf{x})$  $q^r(\mathbf{x}|y=0)$  $p_{\theta=\theta^{new}}(\mathbf{x}|y=0)=p_{g\,\theta=\theta^{new}}(\mathbf{x})$

![](img/cb490ed30bca4eda5fbba81c52a2c173_143_0.png)

- Minimizing the KLD drives $p_{g_\theta}(\mathbf{x})$ to $p_{data}(\mathbf{x})$  
  - By definition: $p_{\theta=\theta_0}(\mathbf{x}) = E_{p(y)}[p_{\theta=\theta_0}(\mathbf{x}|y)] = (p_{g\,\theta=\theta_0}(\mathbf{x}) + p_{data}(\mathbf{x}))/2$  
  - KL$(p_\theta(x|y=1)||q^r(x|y=1)) = KL(p_{data}(x)||q^r(x|y=1))$ : constant, no free parameters  
  - KL$(p_\theta(x|y=0)||q^r(x|y=0)) = KL(p_{g_\theta}(x)||q^r(x|y=0))$ : parameter $\theta$ to optimize  
    - $q^r(\mathbf{x}|y=0) \propto q^r_{\phi=\phi_0}(y=0|\mathbf{x})p_{\theta=\theta_0}(\mathbf{x})$  
      - seen as a mixture of $p_{g\,\theta=\theta_0}(\mathbf{x})$ and $p_{data}(\mathbf{x})$  
      - mixing weights induced from $q^r_{\phi=\phi_0}(y=0|\mathbf{x})$  
  - Drives $p_{g_\theta}(\mathbf{x}|y)$ to mixture of $p_{g\,\theta=\theta_0}(\mathbf{x})$ and $p_{data}(\mathbf{x})$  
    - $\Rightarrow$ Drives $p_{g_\theta}(\mathbf{x})$ to $p_{data}(\mathbf{x})$

![](img/cb490ed30bca4eda5fbba81c52a2c173_143_1.png)

## GANs: minimizing KLD

![](img/cb490ed30bca4eda5fbba81c52a2c173_144_0.png)

p_{θ=θ₀}(x|y = 1) = p_{data}(x)

p_{θ=θ₀}(x|y = 0) = p_{gθ=θ₀}(x)

q^r(x|y = 0)

missed mode

p_{θ=θ^{new}}(x|y = 0) = p_{gθ=θ^{new}}(x)

- Missing mode phenomena of GANs
  - Asymmetry of KLD
    - Concentrates $p_\theta(x|y = 0)$ to large modes of $q^r(x|y)$
      $\Rightarrow p_{g\theta}(x)$ misses modes of $p_{data}(x)$
  - Symmetry of JSD
  - Does not affect the behavior of mode missing

KL($p_{g\theta}(x)||q^r(x|y = 0)$)
= $\int p_{g\theta}(x) \log \frac{p_{g\theta}(x)}{q^r(x|y = 0)} dx$

- Large positive contribution to the KLD in the regions of $x$ space where $q^r(x|y = 0)$ is small, unless $p_{g\theta}(x)$ is also small
- $\Rightarrow p_{g\theta}(x)$ tends to avoid regions where $q^r(x|y = 0)$ is small

![](img/cb490ed30bca4eda5fbba81c52a2c173_147_0.png)

Variational EM

Inference as generation

GANs

valid z space in
two domains

ADA

## Variant of GAN: InfoGAN
- GANs don’t offer the functionality of inferring code **z** given data
- InfoGAN [Chen et al., 2016]
- Introduce inference model $Q_{\eta}(\mathbf{z}|\mathbf{x})$ with parameters $\boldsymbol{\eta}$
- Augment the objectives of GANs by additionally inferring **z**

$\max_D \mathcal{L}_D = \mathbb{E}_{\mathbf{x}\sim p_{data}(\mathbf{x})}[\log D(\mathbf{x})] + \mathbb{E}_{\mathbf{x}\sim G(\mathbf{z}),\mathbf{z}\sim p(\mathbf{z})}[\log(1 - D(\mathbf{x}))],$
$\max_{G,Q} \mathcal{L}_{G,Q} = \mathbb{E}_{\mathbf{x}\sim G(\mathbf{z}),\mathbf{z}\sim p(\mathbf{z})}[\log D(\mathbf{x}) + \log Q(\mathbf{z}|\mathbf{x})].$

![](img/cb490ed30bca4eda5fbba81c52a2c173_148_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_148_1.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_148_2.png)

## InfoGAN: new formulation
- Defines conditional $q_\eta(z|x,y)$

  - $q_\eta(z|x,y=1)$ is fixed without free parameters to learn

    - As GANs assume the code space of real data is degenerated

  - Parameters $\eta$ are only associated with $q_\eta(z|x,y=0)$

- Rewrite in the new form:

$$\max_\phi \mathcal{L}_\phi = \mathbb{E}_{p_\theta(x|y)p(y)}\left[\log q_\eta(z|x,y)q_\phi(y|x)\right]$$

$$\max_{\theta,\eta} \mathcal{L}_{\theta,\eta} = \mathbb{E}_{p_\theta(x|y)p(y)}\left[\log q_\eta(z|x,y)q_\phi^{(r)}(y|x)\right]$$

![](img/cb490ed30bca4eda5fbba81c52a2c173_149_0.png)

## GANs vs InfoGAN

![](img/cb490ed30bca4eda5fbba81c52a2c173_150_0.png)

code data/gen

![](img/cb490ed30bca4eda5fbba81c52a2c173_150_1.png)

max_φ L_φ = 𝔼_{p_θ(x|y)p(y)} [log q_φ(y|x)]
max_θ L_θ = 𝔼_{p_θ(x|y)p(y)} [log q_φ^r(y|x)]

![](img/cb490ed30bca4eda5fbba81c52a2c173_150_2.png)

code data/gen

![](img/cb490ed30bca4eda5fbba81c52a2c173_150_3.png)

max_φ L_φ = 𝔼_{p_θ(x|y)p(y)} [log q_η(z|x,y) q_φ(y|x)]
max_{θ,η} L_{θ,η} = 𝔼_{p_θ(x|y)p(y)} [log q_η(z|x,y) q_φ^r(y|x)]
