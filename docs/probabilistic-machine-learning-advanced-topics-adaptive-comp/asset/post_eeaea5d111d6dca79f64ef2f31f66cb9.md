
## 12.5.5 Riemann manifold HMC

If we let the covariance matrix change as we move position, so $\Sigma$ is a function of $\theta$, the method is known as **Riemann manifold HMC** or **RM-HMC** [GC11; Bet13], since the moves follow a curved manifold, rather than the flat manifold induced by a constant $\Sigma$.

A natural choice for the covariance matrix is to use the Hessian at the current location, to capture the local geometry:

$\Sigma(\theta) = \nabla^2 \mathcal{E}(\theta)$ (12.78)

Since this is not always positive definite, an alternative, that can be used for some problems, is to use the Fisher information matrix (Section 3.3.4), given by

$\Sigma(\theta) = -\mathbb{E}_{p(x|\theta)} [\nabla^2 \log p(x|\theta)]$ (12.79)

Once we have computed $\Sigma(\theta)$, we can compute the kinetic energy as follows:

$\mathcal{K}(\theta, v) = \frac{1}{2} \log((2\pi)^D |\Sigma(\theta)|) + \frac{1}{2} v^\top \Sigma(\theta) v$ (12.80)

Unfortunately the Hamiltonian updates of $\theta$ and $v$ are no longer separable, which makes the RM-HMC algorithm more complex to implement, so it is not widely used.

## 12.5.6 Langevin Monte Carlo (MALA)

A special case of HMC occurs when we take $L=1$ leapfrog steps. This is known as **Langevin Monte Carlo (LMC)**, or the **Metropolis adjusted Langevin algorithm (MALA)** [RT96]. This gives rise to the simplified algorithm shown in Algorithm 12.4.

```
Algorithm 12.4: Langevin Monte Carlo
1 for t = 1 : T do
2   Generate random momentum $v_{t-1} \sim \mathcal{N}(0, \Sigma)$
3   $\theta^* = \theta_{t-1} - \frac{\eta^2}{2} \Sigma^{-1} \nabla \mathcal{E}(\theta_{t-1}) + \eta \Sigma^{-1} v_{t-1}$
4   $v^* = v_{t-1} - \frac{\eta}{2} \nabla \mathcal{E}(\theta_{t-1}) - \frac{\eta}{2} \nabla \mathcal{E}(\theta^*)$
5   Compute $\alpha = \min(1, \exp[-\mathcal{H}(\theta^*, v^*)] / \exp[-\mathcal{H}(\theta_{t-1}, v_{t-1})])$
6   Set $\theta_t = \theta^*$ with probability $\alpha$, otherwise $\theta_t = \theta_{t-1}$.
```

A further simplification is to eliminate the MH acceptance step. In this case, the update becomes

$\theta_t = \theta_{t-1} - \frac{\eta^2}{2} \Sigma^{-1} \nabla \mathcal{E}(\theta_{t-1}) + \eta \Sigma^{-1} v_{t-1}$ (12.81)

$= \theta_{t-1} - \frac{\eta^2}{2} \Sigma^{-1} \nabla \mathcal{E}(\theta_{t-1}) + \eta \sqrt{\Sigma^{-1}} \epsilon_{t-1}$ (12.82)

where $v_{t-1} \sim \mathcal{N}(0, \Sigma)$ and $\epsilon_{t-1} \sim \mathcal{N}(0, \mathbf{I})$. This is just like gradient descent with added noise. If we set $\Sigma$ to be the Fisher information matrix, this becomes natural gradient descent (Section 6.4) with added noise.

Now suppose \(\boldsymbol{\Sigma} = \mathbf{I}\), and we set \(\eta = \sqrt{2}\). In continuous time, we get the following stochastic differential equation (SDE), known as **Langevin diffusion**:

\(d\boldsymbol{\theta}_t = -\nabla \mathcal{E}(\boldsymbol{\theta}_t)dt + \sqrt{2}d\mathbf{B}_t\) (12.83)

where \(\mathbf{B}_t\) represents \(D\)-dimensional Brownian motion. If we use this to generate the samples, the method is known as the **unadjusted Langevin algorithm** or **ULA** [Par81; RT96].

## 12.5.7 Connection between SGD and Langevin sampling

In this section, we discuss a deep connection between stochastic gradient descent (SGD) and Langevin sampling, following the presentation of [BZ20, Sec 10.2.3].

Consider the minimization of the additive loss

\(\mathcal{L}(\boldsymbol{\theta}) = \sum_{n=1}^N \mathcal{L}_n(\boldsymbol{\theta})\) (12.84)

For example, we may define \(\mathcal{L}_n(\boldsymbol{\theta}) = -\log p(y_n|\mathbf{x}_n, \boldsymbol{\theta})\). We will use a minibatch approximation to the gradients:

\(\nabla_B \mathcal{L}(\boldsymbol{\theta}) = \frac{1}{B} \sum_{n \in S} \nabla \mathcal{L}_n(\boldsymbol{\theta})\) (12.85)

where \(\mathcal{S} = \{i_1, \dots, i_B\}\) is a randomly chosen set of indices of size \(B\). For simplicity of analysis, we assume the indices are chosen with replacement from \(\{1, \dots, N\}\).

Let us define the (scaled) error (due to minibatching) in the estimated gradient by

\(\boldsymbol{v}_t \triangleq \sqrt{\eta} (\nabla \mathcal{L}(\boldsymbol{\theta}_t) - \nabla_B \mathcal{L}(\boldsymbol{\theta}_t))\) (12.86)

This is called the **diffusion term**. Then we can rewrite the SGD update as

\(\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \eta \nabla_B \mathcal{L}(\boldsymbol{\theta}_t) = \boldsymbol{\theta}_t - \eta \nabla \mathcal{L}(\boldsymbol{\theta}_t) + \sqrt{\eta} \boldsymbol{v}_t\) (12.87)

The diffusion term \(\boldsymbol{v}_t\) has mean 0, since

\(\mathbb{E}[\nabla_B \mathcal{L}(\boldsymbol{\theta})] = \frac{1}{B} \sum_{j=1}^B \mathbb{E}[\nabla \mathcal{L}_{i_j}(\boldsymbol{\theta})] = \frac{1}{B} \sum_{j=1}^B \nabla \mathcal{L}(\boldsymbol{\theta}) = \nabla \mathcal{L}(\boldsymbol{\theta})\) (12.88)

To compute the variance of the diffusion term, note that

\(\mathbb{V}[\nabla_B \mathcal{L}(\boldsymbol{\theta})] = \frac{1}{B^2} \sum_{j=1}^B \mathbb{V}[\nabla \mathcal{L}_{i_j}(\boldsymbol{\theta})]\) (12.89)

![](img/ca72c1626f4850f058a9edc138c1ac73_548_0.png)

Figure 12.10: (a) A mixture model. (b) After integrating out the discrete latent variables.

$$
\mathbb{V} [\nabla \mathcal{L}_{i_j}(\boldsymbol{\theta})] = \mathbb{E} [ \nabla \mathcal{L}_{i_j}(\boldsymbol{\theta}) \nabla \mathcal{L}_{i_j}(\boldsymbol{\theta})^\mathsf{T} ] - \mathbb{E} [ \nabla \mathcal{L}_{i_j}(\boldsymbol{\theta}) ] \mathbb{E} [ \nabla \mathcal{L}_{i_j}(\boldsymbol{\theta})^\mathsf{T} ] \quad (12.90)
$$
$$
= \left( \frac{1}{N} \sum_{n=1}^N \nabla \mathcal{L}_n(\boldsymbol{\theta}) \nabla \mathcal{L}_n(\boldsymbol{\theta})^\mathsf{T} \right) - \nabla \mathcal{L}(\boldsymbol{\theta}) \nabla \mathcal{L}(\boldsymbol{\theta})^\mathsf{T} \triangleq \mathbf{D}(\boldsymbol{\theta}) \quad (12.91)
$$

where \(\mathbf{D}(\boldsymbol{\theta})\) is called the **diffusion matrix**. Hence \(\mathbb{V}[\mathbf{v}_t] = \frac{\eta}{B}\mathbf{D}(\boldsymbol{\theta}_t)\).

[LTW15] prove that the following continuous time stochastic differential equation is a first-order approximation of minibatch SGD (assuming the loss function is Lipschitz continuous):

$$
d\boldsymbol{\theta}(t) = -\nabla \mathcal{L}(\boldsymbol{\theta}(t))dt + \sqrt{\frac{\eta}{B}\mathbf{D}(\boldsymbol{\theta}_t)}d\mathbf{B}(t) \quad (12.92)
$$

where \(\mathbf{B}(t)\) is Brownian motion. Thus the noise from minibatching causes SGD to act like a Langevin sampler. (See [Hu+17] for more information.)

The scale factor for the noise, \(\tau = \frac{\eta}{B}\), plays the role of **temperature**. Thus we see that using a smaller batch size is like using a larger temperature; the added noise ensures that SGD avoids going into narrow ravines, and instead spends most of its time in flat minima which have better generalization performance [Kes+17]. See Section 17.4.1 for more discussion of this point.

## 12.5.8 Applying HMC to constrained parameters

To apply HMC, we require that all the latent quantities be continuous (real-valued) and have unconstrained support, i.e., \(\boldsymbol{\theta} \in \mathbb{R}^D\), so discrete latent variables need to be marginalized out (although some recent work, such as [NDL20; Zho20], relaxes this requirement).
As an example of how this can be done, consider a GMM. We can easily write the likelihood without discrete latents as follows:

$$p(\boldsymbol{x}_n|\boldsymbol{\theta}) = \sum_{k=1}^K \pi_k \mathcal{N}(\boldsymbol{x}_n|\boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)$$

The corresponding “collapsed” model is shown in Figure 12.10(b). (Note that this is the opposite of Section 12.3.8, where we integrated out the continuous parameters in order to apply Gibbs sampling to the discrete latents.) We can apply similar techniques to other discrete latent variable models. For example, to apply HMC to HMMs, we can use the forwards algorithm (Section 9.2.2) to efficiently compute $$p(\boldsymbol{x}_n|\boldsymbol{\theta}) = \sum_{\boldsymbol{z}_{1:T}} p(\boldsymbol{x}_n, \boldsymbol{z}_{n

In addition to marginalizing out any discrete latent variables, we need to ensure the remaining continuous latent variables are unconstrained. This often requires performing a change of variables using a bijector. For example, instead of sampling the discrete probability vector from the probability simplex $\boldsymbol{\pi} \in \mathbb{S}^K$, we should sample the logits $\boldsymbol{\eta} \in \mathbb{R}^K$. After sampling, we can transform back, since bijectors are invertible. (For a practical example, see change_of_variable_hmc.ipynb.)

## 12.5.9 Speeding up HMC

Although HMC uses gradient information to explore the typical set, sometimes the geometry of the typical set can be difficult to sample from. See Section 12.5.4.3 for ways to estimate the mass matrix, which can help with such difficult cases.

Another issue is the cost of evaluating the target distribution, $\mathcal{E}(\boldsymbol{\theta}) = -\log \tilde{p}(\boldsymbol{\theta})$. For many ML applications, this has the form $\log \tilde{p}(\boldsymbol{\theta}) = \log p_0(\boldsymbol{\theta}) + \sum_{n=1}^N \log p(\boldsymbol{\theta}_n|\boldsymbol{\theta})$. This takes $O(N)$ time to compute. We can speed this up by using stochastic gradient methods; see Section 12.7 for details.

## 12.6 MCMC convergence

We start MCMC from an arbitrary initial state. As we explained in Section 2.6.4, the samples will be coming from the chain’s stationary distribution only when the chain has “forgotten” where it started from. The amount of time it takes to enter the stationary distribution is called the mixing time (see Section 12.6.1 for details). Samples collected before the chain has reached its stationary distribution do not come from $p^*$, and are usually thrown away. The initial period, whose samples will be ignored, is called the burn-in phase.

For example, consider a uniform distribution on the integers $\{0, 1, \dots, 20\}$. Suppose we sample from this using a symmetric random walk. In Figure 12.11, we show two runs of the algorithm. On the left, we start in state 10; on the right, we start in state 17. Even in this small problem it takes over 200 steps until the chain has “forgotten” where it started from. Proposal distributions that make larger changes can converge faster. For example, [BD92; Man] prove that it takes about 7 riffle shuffles to properly mix a deck of 52 cards (i.e., to ensure the distribution is uniform).

In Section 12.6.1 we discuss how to compute the mixing time theoretically. In practice, this can be very hard [BBM10] (this is one of the fundamental weaknesses of MCMC), so in Section 12.6.2, we discuss practical heuristics.
