
## EM Convergence Properties

### E-Step

- EM improves the lower bound
$\mathcal{L}(q_{new}, \theta_{new}) \geq \mathcal{L}(q_{old}, \theta_{old})$

- M-step: Lower bound increases
- E-step: KL is set to 0, lower bound has to go up

![](img/f01928df50903c99ce023dd3c527a33d_631_0.png)

- EM improves the marginal likelihood
$\log p(x|\theta_{new}) \geq \log p(x|\theta_{old})$

- M-step: Lower bound increases and KL increases (can't get smaller than 0)
- E-step: Marginal likelihood is unaffected (does not depend on q)

### M-Step

![](img/f01928df50903c99ce023dd3c527a33d_631_1.png)

## Illustration of EM

- Lower bound (blue curve) is a convex approximation of the marginal likelihood (red curve)
- Maximum of lower bound can be easily obtained ($\theta^{\text{new}}$)
- Closed form solutions available, no gradient descent required
- Compute new lower bound for $\theta^{\text{new}}$ (green curve)
- Due to the local approximation of the lowerbound, EM can only find local optima

![](img/f01928df50903c99ce023dd3c527a33d_632_0.png)

## EM for full dataset

**For all data-points**, the lower bound is given by:

$\mathcal{L}(q,\theta) = \sum_{i} \left(\int_{z} q_i(z) \log p(\boldsymbol{x}_i,z|\theta)dz - \int_{z} q_i(z) \log q_i(z)dz\right)$

- One latent variable $z_i$ per data-point
- If $z$ is discrete with $K$ different values, then

$q_i(z=k) = p(z=k|\boldsymbol{x}_i, \theta_{old})$

- can be represented as a N x K matrix
- We will write $q_{ik} = q_i(z=k)$

## EM for GMMs revisited

- Mixture coefficient: $p(k) = \pi_k$, with $0 \le \pi_k \le 1$, $\sum_k \pi_k = 1$
- Mixture component: $p(\boldsymbol{x}|k) = \mathcal{N}(\boldsymbol{x}|\boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)$
- Mixture distribution: $p(\boldsymbol{x}) = \sum_{k=1}^K \pi_k \mathcal{N}(\boldsymbol{x}|\boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)$
- Always integrates to 1
- Parameters of the mixture $\theta = \{\pi_1, \boldsymbol{\mu}_1, \boldsymbol{\Sigma}_1, \dots, \pi_K, \boldsymbol{\mu}_K, \boldsymbol{\Sigma}_K\}$

### E-Step

- Compute "responsibilities"

$q_{ik} = q_i(z=k) = \frac{\pi_k \mathcal{N}(\boldsymbol{x}_i|\boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)}{\sum_{j=1}^K \pi_j \mathcal{N}(\boldsymbol{x}_i|\boldsymbol{\mu}_j, \boldsymbol{\Sigma}_j)}$

- How much component k contributes to generation of $\boldsymbol{x}_i$ according to current mixture model

## EM for GMMs revisited

**M-Step:** $\theta = \arg \max_{\theta} \sum_{i} \sum_{k} q_{ik} \log p(k)p(x_i|k) = \arg \max_{\theta} \sum_{k} \sum_{i} q_{ik} \log p(k) + \sum_{k} \sum_{i} q_{ik}p(x_i|k)$

- We can separate updates of single components and coefficients
- just additive objectives in lower bound

- **Update coefficients:**
$\pi = \arg \max_{\pi} \sum_{i} \sum_{k} q_{ik} \log \pi_k$

- **Update components:**
$\mu_k, \Sigma_k = \arg \max_{\mu_k, \Sigma_k} \sum_{i} q_{ik} \log \mathcal{N}(x_i|\mu_k, \Sigma_k)$
- Each data-point is weighted by $q_{ik}$
- Weighted maximum likelihood estimate

## EM for Gaussian Mixture Models

**Weighted Maximum Likelihood** updates:

- Update coefficients: $\pi = \arg \max_{\pi} \sum_{i} \sum_{k} q_{ik} \log \pi_k$
- Result: $\pi_k = \frac{\sum_{i} q_{ik}}{\sum_{k} q_{ik}} = \frac{\sum_{i} q_{ik}}{N}$
- Update components: $\mu_k, \Sigma_k = \arg \max_{\mu_k, \Sigma_k} \sum_{i} q_{ik} \log \mathcal{N}(x_i|\mu_k, \Sigma_k)$
- Mean: $\mu_k = \frac{\sum_{i} q_{ik} x_i}{\sum_{i} q_{ik}}$
- Covariance: $\Sigma_k = \frac{\sum_{i} q_{ik}(x_i - \mu_k)(x_i - \mu_k)^T}{\sum_{i} q_{ik}}$

**Same as before, but now derived!**

## Additional Notes for EM

EM assumes that E-step can set the KL to zero:

- i.e. we can evaluate the posterior
- Lower bound is tight
- Marginal likelihood always improves (good to check for!)
- Only possible if z is discrete or we have linear models

For more complex latent variable models (e.g. Deep Neural Networks), this is not possible:

- Extension of EM called Variational Bayes / Variational Inference can still do that
- Approximates the posterior, i.e. KL will be > 0
- Very active research, underlying algorithm of many deep learning architectures (e.g. variational autoencoder)
- Will be covered in the end

## Takeaway

You know now:

- What mixture models and latent variable models are
- What the Expectation-Maximization idea and algorithm are
- Why does EM converge
- How to apply EM to GMMs

![](img/f01928df50903c99ce023dd3c527a33d_638_0.png)

## Self-test questions

- What are mixture models?
- Should gradient methods be used for mixture models?
- How does the EM algorithm work?
- What is the problem of mixture models?
- How does EM decompose the marginal likelihood?
- Why does EM always improve the lower bound?
- Why does EM always improve the marginal likelihood?
- Why can we optimize each mixture independently

## Continuous Latent Variable Models and Variational Autoencoders

## Machine Learning SS2024

Prof. Gerhard Neumann
KIT, Institut für Informatik und Robotik

## Learning Outcome for today...

In this lecture, we will..

- Understand the autoencoders and what you can do with it
- How to use them as generative model and its connection to latent variable models
- What variational autoencoders are...
- ... and how to train them using Variational Bayes

## EM for Continuous Latent Variables

## EM for Dimensionality Reduction

We can also formulate dimensionality reduction using latent variables

Idea: Introduce a latent variable model to relate a D-dimensional observation vector to a corresponding M-dimensional Gaussian latent variable (with M < D)

```
x = Wz + \mu + \epsilon
```

- **z** is a latent variable (our low dimensional representation)
- **W** is a $D \times M$ matrix relating the latent space **z** with the original space **x**
- **$\mu$** is a constant offset vector
- **$\epsilon$** is a D-dimensional noise vector $\epsilon \sim \mathcal{N}(0, \sigma^2 I)$

![](img/f01928df50903c99ce023dd3c527a33d_643_0.png)

## EM for Dimensionality Reduction

Probabilistic Dimensionality Reduction Model:

$z \in \mathbb{R}^M, \quad x \in \mathbb{R}^D, \quad M < D$

- Continuous Latent Variable:
  - $p(z) = \mathcal{N}(\mathbf{0}, \mathbf{I})$
  - 0 mean, unit variance distribution in latent space

![](img/f01928df50903c99ce023dd3c527a33d_644_0.png)

- Observation Model
  - $p(x|z, \theta) = \mathcal{N}(\mathbf{W}z + \mathbf{\mu}, \sigma^2 \mathbf{I})$
  - with parameters $\theta = \{\mathbf{W}, \mathbf{\mu}, \sigma^2\}$

## Generative Process

Our model can be interpreted in terms of a generative process

1. Sample latent variable
$z \sim \mathcal{N}(0, I)$
2. Linearly project to high-D space
$y = Wz + \mu$
3. Sample noise
$\epsilon \sim \mathcal{N}(0, \sigma^2 I)$
4. Add noise to obtain x
$x = y + \epsilon$

![](img/f01928df50903c99ce023dd3c527a33d_645_0.png)

## Marginal likelihood

Marginal likelihood is given by:

$$$p(\boldsymbol{x}|\theta) = \int_z p(\boldsymbol{x}|\boldsymbol{z}, \theta)p(\boldsymbol{z})dz = \int_z \mathcal{N}(\boldsymbol{x}|\boldsymbol{W}\boldsymbol{z} + \boldsymbol{\mu}, \sigma^2\boldsymbol{I})\mathcal{N}(\boldsymbol{z}|\mathbf{0}, \boldsymbol{I})dz$$

Maximize the marginal log-likelihood:

$$$loglike(\theta) = \sum_{i=1}^N \log p(\boldsymbol{x}_i|\theta) = \sum_{i=1}^N \log \left( \int_z \mathcal{N}(\boldsymbol{x}_i|\boldsymbol{W}\boldsymbol{z} + \boldsymbol{\mu}, \sigma^2\boldsymbol{I})\mathcal{N}(\boldsymbol{z}|\mathbf{0}, \boldsymbol{I})dz \right)$$$
