# 12.5.5 Riemann manifold HMC

If we let the covariance matrix change as we move position, so $\Sigma$ is a function of $\theta$, the method is known as **Riemann manifold HMC** or **RM-HMC** [GC11; Bet13], since the moves follow a curved manifold, rather than the flat manifold induced by a constant $\Sigma$.

A natural choice for the covariance matrix is to use the Hessian at the current location, to capture the local geometry:

$\Sigma(\theta) = \nabla^2 \mathcal{E}(\theta)$ (12.78)

Since this is not always positive definite, an alternative, that can be used for some problems, is to use the Fisher information matrix (Section 3.3.4), given by

$\Sigma(\theta) = -\mathbb{E}_{p(x|\theta)} [\nabla^2 \log p(x|\theta)]$ (12.79)

Once we have computed $\Sigma(\theta)$, we can compute the kinetic energy as follows:

$\mathcal{K}(\theta, v) = \frac{1}{2} \log((2\pi)^D |\Sigma(\theta)|) + \frac{1}{2} v^\top \Sigma(\theta) v$ (12.80)

Unfortunately the Hamiltonian updates of $\theta$ and $v$ are no longer separable, which makes the RM-HMC algorithm more complex to implement, so it is not widely used.

# 12.5.6 Langevin Monte Carlo (MALA)

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

where $v_{t-1} \sim \mathcal{N}(0, \Sigma)$ and $\epsilon_{t-1} \sim \mathcal{N}(0, \mathbf{I})$. This is just like gradient descent with added noise. If we set $\Sigma$ to be the Fisher information matrix, this becomes natural gradient descent (Section 6.4) with