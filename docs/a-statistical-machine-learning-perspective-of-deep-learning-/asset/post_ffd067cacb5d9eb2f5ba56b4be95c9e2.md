
## Generative Adversarial Nets (GANs)
- [Goodfellow et al., 2014]
- Generative model $x = G_\theta(z),\ z \sim p(z)$
  - Map noise variable $z$ to data space $x$
  - Define an *implicit distribution* over $x$: $p_{g_\theta}(x)$
    - a stochastic process to simulate data $x$
    - Intractable to evaluate likelihood
- Discriminator $D_\phi(x)$
  - Output the probability that $x$ came from the data rather than the generator
- No explicit inference model
- No obvious connection to previous models with inference networks like VAEs
  - We will build formal connections between GANs and VAEs later

## Generative Adversarial Nets (GANs)
- Learning
  - Train $G$ to fool the discriminator
  - The original loss suffers from vanishing gradients when $D$ is too strong
  - Instead use the following in practice
    $\max_G \mathcal{L}_G = \mathbb{E}_{\boldsymbol{x}\sim G(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z})} [\log D(\boldsymbol{x})]$

![](img/cb490ed30bca4eda5fbba81c52a2c173_121_0.png)

[Figure courtesy: Kim's slides]

![](img/cb490ed30bca4eda5fbba81c52a2c173_124_0.png)

## The Zoo of DGMs
- Variational autoencoders (VAEs) [Kingma & Welling, 2014]
  - Adversarial autoencoder [Makhzani et al., 2015]
  - Importance weighted autoencoder [Burda et al., 2015]
  - Implicit variational autoencoder [Mescheder et al., 2017]
- Generative adversarial networks (GANs) [Goodfellow et al., 2014]
  - InfoGAN [Chen et al., 2016]
  - CycleGAN [Zhu et al., 2017]
  - Wasserstein GAN [Arjovsky et al., 2017]
- Autoregressive neural networks
  - PixelRNN / PixelCNN [Oord et al., 2016]
  - RNN (e.g., for language modeling)
- Generative moment matching networks (GMMNs) [Li et al., 2015; Dziugaite et al., 2015]
- Restricted Boltzmann Machines (RBMs) [Smolensky, 1986]

## Alchemy Vs Modern Chemistry

![](img/cb490ed30bca4eda5fbba81c52a2c173_125_0.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_125_1.png)

![](img/cb490ed30bca4eda5fbba81c52a2c173_125_2.png)

© Mind Juice Media Inc. All rights reserved

## Outline
- Overview of advances in deep generative models
- Theoretical backgrounds of deep generative models
  - Wake sleep algorithm
  - Variational autoencoders
  - Generative adversarial networks
- A unified view of deep generative models
  - new formulations of deep generative models
  - Symmetric modeling of latent and visible variables

Z Hu, Z Yang, R Salakhutdinov, E Xing,
“On Unifying Deep Generative Models”, arxiv 1706.00550

## Adversarial domain adaptation (ADA)
- Let’s start from ADA
  - The application of adversarial approach on domain adaptation
  - We then show GANs can be seen as a special case of ADA
  - Correspondence of elements:

| Elements | GANs | ADA |
|---|---|---|
| *x* | data/generation | features |
| *z* | code vector | Data from source/target domains |
| *y* | Real/fake indicator | Source/target domain indicator |

![](img/cb490ed30bca4eda5fbba81c52a2c173_128_0.png)

## ADA: conventional formulation
- Train $D_\phi$ to distinguish between domains

$\max_\phi \mathcal{L}_\phi = \mathbb{E}_{\boldsymbol{x}=G_\theta(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=1)}[\log D_\phi(\boldsymbol{x})] + \mathbb{E}_{\boldsymbol{x}=G_\theta(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=0)}[\log(1 - D_\phi(\boldsymbol{x}))]$

- Train $G_\theta$ to fool $D_\phi$

$\max_\theta \mathcal{L}_\theta = \mathbb{E}_{\boldsymbol{x}=G_\theta(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=1)}[\log(1 - D_\phi(\boldsymbol{x}))] + \mathbb{E}_{\boldsymbol{x}=G_\theta(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=0)}[\log D_\phi(\boldsymbol{x})]$

## ADA: new formulation
- To reveal the connections to conventional variational approaches, let’s rewrite the objectives in a format that resembles variational EM
- Implicit distribution over $\boldsymbol{x} \sim p_\theta(\boldsymbol{x}|y)$
  $\boldsymbol{x} = G_\theta(\boldsymbol{z}), \ \boldsymbol{z} \sim p(\boldsymbol{z}|y)$
- Discriminator distribution $q_\phi(y|\boldsymbol{x})$
  $q_\phi^r(y|\boldsymbol{x}) = q_\phi(1 - y|\boldsymbol{x})$
- Rewrite the objective in the new form (up to constant scale factor)
  $\max_\phi \mathcal{L}_\phi = \mathbb{E}_{p_\theta(\boldsymbol{x}|y)p(y)}[\log q_\phi(y|\boldsymbol{x})]$
  $\max_\theta \mathcal{L}_\theta = \mathbb{E}_{p_\theta(\boldsymbol{x}|y)p(y)}[\log q_\phi^r(y|\boldsymbol{x})]$
  - $\boldsymbol{z}$ is encapsulated in the implicit distribution $p_\theta(\boldsymbol{x}|y)$
    $\max_\phi \mathcal{L}_\phi = \mathbb{E}_{p_\theta(\boldsymbol{x}|y=0)p(y=0)}[\log q_\phi(y=0|\boldsymbol{x})] + \mathbb{E}_{p_\theta(\boldsymbol{x}|y=1)p(y=1)}[\log q_\phi(y=1|\boldsymbol{x})]$
    $= \frac{1}{2}\mathbb{E}_{\boldsymbol{x}=G_\theta(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=0)}[\log(1 - D_\phi(\boldsymbol{x}))] + \frac{1}{2}\mathbb{E}_{\boldsymbol{x}=G_\theta(\boldsymbol{z}),\boldsymbol{z}\sim p(\boldsymbol{z}|y=1)}[\log D_\phi(\boldsymbol{x})]$
  - (Ignore the constant scale factor 1/2)

![](img/cb490ed30bca4eda5fbba81c52a2c173_132_0.png)

## ADA: new formulation
- New formulation

$$\max_{\phi}\mathcal{L}_{\phi}=\mathbb{E}_{p_{\theta}(x\mid y)p(y)}\left[\log q_{\phi}(y\mid x)\right]$$

$$\max_{\theta}\mathcal{L}_{\theta}=\mathbb{E}_{p_{\theta}(x\mid y)p(y)}\left[\log q_{\phi}^{r}(y\mid x)\right]$$

- The only **difference** between optimizing $\theta$ and $\phi$: $q$ vs. $q^{r}$

- This is where the **adversarial** mechanism comes about

## ADA vs. Variational EM
### Variational EM
- **Objectives**
  - $$\max_{\phi}\mathcal{L}_{\phi,\theta}=\mathbb{E}_{q_{\phi}(z|x)}[\log p_{\theta}(x|z)]+KL\left(q_{\phi}(z|x)\|p(z)\right)$$
  - $$\max_{\theta}\mathcal{L}_{\phi,\theta}=\mathbb{E}_{q_{\phi}(z|x)}[\log p_{\theta}(x|z)]+KL\left(q_{\phi}(z|x)\|p(z)\right)$$
- Single objective for both $\theta$ and $\phi$
- Extra prior regularization by $p(z)$

### ADA
- **Objectives**
  - $$\max_{\phi}\mathcal{L}_{\phi}=\mathbb{E}_{p_{\theta}(x|y)p(y)}\left[\log q_{\phi}(y|x)\right]$$
  - $$\max_{\theta}\mathcal{L}_{\theta}=\mathbb{E}_{p_{\theta}(x|y)p(y)}\left[\log q_{\phi}^{r}(y|x)\right]$$
- Two objectives
- Have global optimal state in the game theoretic view

## ADA vs. Variational EM
### Variational EM
- Objectives
  max_φ L_{φ,θ} = E_{q_φ(z|x)}[log p_θ(x|z)] + KL(q_φ(z|x)||p(z))
  max_θ L_{φ,θ} = E_{q_φ(z|x)}[log p_θ(x|z)] + KL(q_φ(z|x)||p(z))
- Single objective for both θ and φ
- Extra prior regularization by p(z)
- The reconstruction term: maximize the conditional log-likelihood of x with the generative distribution p_θ(x|z) conditioning on the latent code z inferred by q_φ(z|x)
- p_θ(x|z) is the generative model
- q_φ(z|x) is the inference model

### ADA
- Objectives
  max_φ L_φ = E_{p_θ(x|y)p(y)}[log q_φ(y|x)]
  max_θ L_θ = E_{p_θ(x|y)p(y)}[log q_φ^r(y|x)]
- Two objectives
- Have global optimal state in the game theoretic view
- The objectives: maximize the conditional log-likelihood of y (or 1 − y) with the distribution q_φ(y|x) conditioning on latent feature x inferred by p_θ(x|y)
- Interpret q_φ(y|x) as the generative model
- Interpret p_θ(x|y) as the inference model

## ADA: graphical model
Define:
- Solid-line arrows ($x \to y$):
  - generative process
- Dashed-line arrows (y, z -> $x$):
  - inference
- Hollow arrows (z -> $x$):
  - deterministic transformation
  - leading to implicit distributions
- Blue arrows ($x \to y$):
  - adversarial mechanism
  - involves both $q_\phi(y|\boldsymbol{x})$ and $q_\phi^r(y|\boldsymbol{x})$

![](img/cb490ed30bca4eda5fbba81c52a2c173_135_0.png)

max$_\phi$ $\mathcal{L}_\phi$ = $\mathbb{E}_{p_\theta(\boldsymbol{x}|y)p(y)}$ [$\log q_\phi(y|\boldsymbol{x})$]
max$_\theta$ $\mathcal{L}_\theta$ = $\mathbb{E}_{p_\theta(\boldsymbol{x}|y)p(y)}$ [$\log q_\phi^r(y|\boldsymbol{x})$]
