
## Some warm up...

- Which distribution $q$ minimizes minimizes $KL(q||p)$?

$p(\mathbf{x}) = \mathcal{N}(\boldsymbol{\mu} = [0, 0]^T, \boldsymbol{\Sigma})$

$q(x_1, x_2) = \mathcal{N}_1(x_1 | \mu_1, \sigma_1^2)\mathcal{N}_2(x_2 | \mu_2, \sigma_2^2)$

![](img/f01928df50903c99ce023dd3c527a33d_691_0.png)

## Start with Recap...

- Latent variable models
- Marginal log likelihood very hard to compute and optimize!
  $\log p_{\theta}(\boldsymbol{x}) = \log \int p_{\theta}(\boldsymbol{x}|\boldsymbol{z})p(\boldsymbol{z})dz$

- Optimize Lower Bound (ELBO) instead
  $\log p_{\theta}(\boldsymbol{x}) \geq \int q_{\phi}(\boldsymbol{z}|\boldsymbol{x}) \log \frac{p_{\theta}(\boldsymbol{x}|\boldsymbol{z})p(\boldsymbol{z})}{q_{\phi}(\boldsymbol{z}|\boldsymbol{x})}dz$
  $= \int q_{\phi}(\boldsymbol{z}|\boldsymbol{x}) \log p_{\theta}(\boldsymbol{x}|\boldsymbol{z}) - KL(q_{\phi}(\boldsymbol{z}|\boldsymbol{x})||p(\boldsymbol{z})) = \mathcal{L}(p, q)$

- Bound is tight with the right $q(\boldsymbol{z}|\boldsymbol{x})$

![](img/f01928df50903c99ce023dd3c527a33d_692_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_692_1.png)

## Reparameterization trick

- Lower bound: $\mathcal{L}(p, q) = \int q_\phi(z|\boldsymbol{x}) \log p_{\theta}(\boldsymbol{x}|z)dz - KL(q_\phi(z|\boldsymbol{x})||p(z))$
$\over{\text{Reconstruction}}$ $\over{\text{Prior matching}}$

- Distribution: $q_\phi(z|\boldsymbol{x}) = \mathcal{N}(z|\mu_\phi(\boldsymbol{x}), \sigma_\phi^2(\boldsymbol{x})\boldsymbol{I})$

- Reparameterization function: $\boldsymbol{h}_\phi(\boldsymbol{\xi}, \boldsymbol{x}) = \mu_\phi(\boldsymbol{x}) + \sigma_\phi(\boldsymbol{x}) \circ \boldsymbol{\xi}$

- Reparameterized lower bound with $\boldsymbol{z} = \boldsymbol{h}_\phi(\boldsymbol{\xi}, \boldsymbol{x})$:
$\mathcal{L}(q, p) = \frac{1}{N} \sum_i \int p(\boldsymbol{\xi}) \left( \log p_{\theta}(\boldsymbol{x}_i|\boldsymbol{h}_\phi(\boldsymbol{\xi}, \boldsymbol{x}_i)) \right) - \log \frac{q_\phi(\boldsymbol{h}_\phi(\boldsymbol{\xi}, \boldsymbol{x}_i)|\boldsymbol{x}_i)}{p_{\theta}(\boldsymbol{h}_\phi(\boldsymbol{\xi}, \boldsymbol{x}_i))}$
$\over{\text{reconstruction}}$ $\over{\text{Prior matching}}$

![](img/f01928df50903c99ce023dd3c527a33d_693_0.png)

## Recap: Multivariate Chain rule

**With vectors:**

$u = \mathbf{u}(x), \quad \frac{\partial \mathbf{g}(u)}{\partial \mathbf{x}} = \frac{\partial \mathbf{u}(x)}{\partial \mathbf{x}} \frac{\partial \mathbf{g}(u)}{\partial u}$

- Note: Swapped order
- Special case (scalar -> vector -> scalar):

$u = \mathbf{u}(t), \quad \frac{\partial \mathbf{g}(u)}{\partial t} = \frac{\partial \mathbf{u}(t)}{\partial t} \frac{\partial \mathbf{g}(u)}{\partial u} = \sum_{i=1}^{d} \frac{\partial u_i(t)}{\partial t} \frac{\partial \mathbf{g}(u)}{\partial u_i}$
$1 \times d \quad d \times 1$

## Reparametrization Example

$h(\xi; \phi) = \mu_{\phi}(x) + \sigma_{\phi}(x) * \xi$

$$\frac{\partial h}{\partial \mu_{\phi}} = I, \quad \frac{\partial h}{\partial \sigma_{\phi}} = \text{diag}(\xi)$$

$$\log p(x|z^{h(\xi,\phi)}) \frac{\partial z}{\partial d} \times 1$$
$\text{(chain rule)}^{m \times d} d \times d \times 1 \Rightarrow m \times 1$$

$$\frac{\partial \mu_{\phi}(x)}{\partial \phi} = \frac{\partial \mu}{\partial \phi} \frac{\partial h}{\partial \mu} + \frac{\partial \sigma}{\partial \phi} \frac{\partial h}{\partial \sigma} \frac{\partial p}{\partial z}$$

## Hierarchical VAEs

- “Flat” VAEs suffer from simple priors
- Making both inference model and generative model hierarchical
![](img/f01928df50903c99ce023dd3c527a33d_696_0.png)
- Better likelihoods are achieved with hierarchies of latent variables
Inference model **$q(z|x)$**
Generative model **$p(x,z)$**

## Hierarchical VAEs

Can generate high quality images with fine details (SOTA 2020)

![](img/f01928df50903c99ce023dd3c527a33d_697_0.png)
[Velling, Kautz, "NVAE: A Deep Variational Autoencoder", NeurIPS 2020]
(a) MNIST (t = 1.0)
(b) CIFAR-10 (t = 0.7)
(c) CelebA 64 (t = 0.6)
![](img/f01928df50903c99ce023dd3c527a33d_697_1.png)
(d) CelebA HQ (t = 0.6)
(e) FFHQ (t = 0.5)

## VAEs: challenges

- Optimization can be difficult for large models
- The ELBO enforces an information bottleneck (through its loss function) at latent variables 'z', making VAE prone to bad local minima.
- Posterior collapse is a dreaded local minimum where the latents do not transmit any information.
![](img/f01928df50903c99ce023dd3c527a33d_698_0.png)

## Denoising Diffusion

## Denoising Diffusion Models as VAEs

Diffusion models are essentially Hierarchical VAEs with 3 restrictions:

1. Latent dimension is the same as the data dimension
2. The encoder $q$ has no parameters to be learnt. It is defined to be a linear gaussian such that the $t$-th gaussian is centered around the previous latent $Z_{t-1}$
3. The parameters for the gaussians are scheduled such that the final latent is a standard gaussian. $z_T \sim \mathcal{N}(z_T; 0, \mathbf{I})$

![](img/f01928df50903c99ce023dd3c527a33d_700_0.png)

## Denoising Diffusion Probabilistic Models (DDPMs)

## Learning to generate by denoising

- Forward diffusion process that gradually adds noise to input
- Reverse denoising process that learns to generate data by denoising
![](img/f01928df50903c99ce023dd3c527a33d_701_0.png)
slides from https://cvpr2022-tutorial-diffusion-models.github.io/

## Forward Diffusion Process

The formal definition of the forward process in T steps:

![](img/f01928df50903c99ce023dd3c527a33d_702_0.png)
Similar to the inference model in hierarchical VAEs.

## Forward Diffusion Process

Can we skip the single noising steps?

- I.e. can we directly compute down

$q(\mathbf{x}_t|\mathbf{x}_0) = \int_{d\mathbf{x}_{1:t-1}} \prod_{k=1}^{t} q(\mathbf{x}_k|\mathbf{x}_{k-1})d\mathbf{x}_{1:t-1}$

Yes, using properties of the Gaussian!

## Properties of Gaussian Distribution

- Sum of 2 Gaussians is Gaussian
- Product of 2 Gaussian is Gaussian
- Conditional Distribution of a joint Gaussian is Gaussian
- Marginal Distribution of a joint Gaussian is Gaussian

![](img/f01928df50903c99ce023dd3c527a33d_704_0.png)

## Basics: Gaussian Identities

Eq (1): joint from Marginal and Conditional: $p(x) \leftarrow p(y|x) \leftarrow p(x, y)$

$\mathcal{N}(x|\mu_x,\Sigma_x)\mathcal{N}(y|x) = \mathcal{N}(x|\mu_x,\Sigma_x)\mathcal{N}(y|\mu_y,\Sigma_y) = \mathcal{N}(x,y|\mu_x,\mu_y, \begin{pmatrix} \Sigma_x & C \\ C^T & \Sigma_y \end{pmatrix})$

Eq (2): Marginal and Conditional from Joint: $p(x, y) \rightarrow p(y|x),p(x)$

$\mathcal{N}(x,y|\mu_x,\mu_y, \begin{pmatrix} \Sigma_x & C \\ C^T & \Sigma_y \end{pmatrix}) = \mathcal{N}(x|\mu_x,\Sigma_x)\mathcal{N}(y|\mu_y + C^T\Sigma_x^{-1}(x-\mu_x), \Sigma_y - C^T\Sigma_x^{-1}C)$

## Basics: Gaussian Bayes rule

- Do not remember exact equations... but remember their properties

-- Both rules are mathematically equivalent...
-- However, numerically it can be a huge difference

-- Bayes rule 1: used for derivation with kernels
- Mean: $\mu_{x|y} = \mu_{x} + \Sigma_{x}F^T(\sigma_{y}^2 I + F\Sigma_{x}F^T)^{-1}(y - F\mu_{x})$
- Covariance: $\Sigma_{x|y} = \Sigma_{x} - \Sigma_{x}F^T(\sigma_{y}^2 I + F\Sigma_{x}F^T)^{-1}F\Sigma_{x}$

-- Bayes rule 2: used for derivation with features
- Mean: $\mu_{x|y} = \mu_{x} + (\sigma_{y}^2\Sigma_{x}^{-1} + F^T F)^{-1}F^T(y - F\mu_{x})$
- Covariance: $\Sigma_{x|y} = \sigma_{y}^2(\sigma_{y}^2\Sigma_{x}^{-1} + F^T F)^{-1}$
