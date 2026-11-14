
### 12.5.2.1 Euler's method

The simplest way to model the time evolution is to update the position and momentum simultaneously by a small amount, known as the step size \(\eta\):

\(\begin{aligned} v_{t+1} &= v_t + \eta \frac{dv}{dt}(\theta_t, v_t) = v_t - \eta \frac{\partial \mathcal{E}(\theta_t)}{\partial \theta} \\ \theta_{t+1} &= \theta_t + \eta \frac{d\theta}{dt}(\theta_t, v_t) = \theta_t + \eta \frac{\partial \mathcal{K}(v_t)}{\partial v} \end{aligned}\) (12.67) (12.68)

If the kinetic energy has the form in Equation (12.64) then the second expression simplifies to

\(\theta_{t+1} = \theta_t + \eta \Sigma^{-1} v_{t+1}\) (12.69)

This is known as Euler's method.

### 12.5.2.2 Modified Euler's method

The modified Euler's method is slightly more accurate, and works as follows: First update the momentum, and then update the position using the new momentum:

\(\begin{aligned} v_{t+1} &= v_t + \eta \frac{dv}{dt}(\theta_t, v_t) = v_t - \eta \frac{\partial \mathcal{E}(\theta_t)}{\partial \theta} \\ \theta_{t+1} &= \theta_t + \eta \frac{d\theta}{dt}(\theta_t, v_{t+1}) = \theta_t + \eta \frac{\partial \mathcal{K}(v_{t+1})}{\partial v} \end{aligned}\) (12.70) (12.71)

Unfortunately, the asymmetry of this method can cause some theoretical problems (see e.g., [BZ20, p287]) which we resolve below.

### 12.5.2.3 Leapfrog integrator

In this section, we discuss the leapfrog integrator, which is a symmetrized version of the modified Euler method. We first perform a “half” update of the momentum, then a full update of the position, and then finally another “half” update of the momentum:

\(\begin{aligned} v_{t+1/2} &= v_t - \frac{\eta}{2} \frac{\partial \mathcal{E}(\theta_t)}{\partial \theta} \\ \theta_{t+1} &= \theta_t + \eta \frac{\partial \mathcal{K}(v_{t+1/2})}{\partial v} \\ v_{t+1} &= v_{t+1/2} - \frac{\eta}{2} \frac{\partial \mathcal{E}(\theta_{t+1})}{\partial \theta} \end{aligned}\) (12.72) (12.73) (12.74)

If we perform multiple leapfrog steps, it is equivalent to performing a half step update of \(\mathbf{v}\) at the beginning and end of the trajectory, and alternating between full step updates of \(\theta\) and \(v\) in between.

### 12.5.2.4 Higher order integrators

It is possible to define higher order integrators that are more accurate, but take more steps. For details, see [BRSS18].

## 12.5.3 The HMC algorithm

We now describe how to use Hamiltonian dynamics to define an MCMC sampler in the expanded state space \((\boldsymbol{\theta}, \boldsymbol{v})\). The target distribution has the form

\( p(\boldsymbol{\theta}, \boldsymbol{v}) = \frac{1}{Z} \exp[-\mathcal{H}(\boldsymbol{\theta}, \boldsymbol{v})] = \frac{1}{Z} \exp\left[-\mathcal{E}(\boldsymbol{\theta}) - \frac{1}{2} \boldsymbol{v}^\text{T} \boldsymbol{\Sigma} \boldsymbol{v} \right] \quad (12.75) \)

The marginal distribution over the latent variables of interest has the form

\( p(\boldsymbol{\theta}) = \int p(\boldsymbol{\theta}, \boldsymbol{v}) d\boldsymbol{v} = \frac{1}{Z_q} e^{-\mathcal{E}(\boldsymbol{\theta})} \int \frac{1}{Z_p} e^{-\frac{1}{2} \boldsymbol{v}^\text{T} \boldsymbol{\Sigma} \boldsymbol{v}} d\boldsymbol{v} = \frac{1}{Z_q} e^{-\mathcal{E}(\boldsymbol{\theta})} \quad (12.76) \)

Suppose the previous state of the Markov chain is \((\boldsymbol{\theta}_{t-1}, \boldsymbol{v}_{t-1})\). To sample the next state, we proceed as follows. We set the initial position to \(\boldsymbol{\theta}'_0 = \boldsymbol{\theta}_{t-1}\), and sample a new random momentum, \(\boldsymbol{v}'_0 \sim \mathcal{N}(\boldsymbol{0}, \boldsymbol{\Sigma})\). We then initialize a random trajectory in the phase space, starting at \((\boldsymbol{\theta}'_0, \boldsymbol{v}'_0)\), and followed for \(L\) leapfrog steps, until we get to the final proposed state \((\boldsymbol{\theta}^*, \boldsymbol{v}^*) = (\boldsymbol{\theta}'_L, \boldsymbol{v}'_L)\). If we have simulated Hamiltonian mechanics correctly, the energy should be the same at the start and end of this process; if not, we say the HMC has **diverged**, and we reject the sample. If the energy is constant, we compute the MH acceptance probability

\( \alpha = \min \left( 1, \frac{p(\boldsymbol{\theta}^*, \boldsymbol{v}^*)}{p(\boldsymbol{\theta}_{t-1}, \boldsymbol{v}_{t-1})} \right) = \min (1, \exp[-\mathcal{H}(\boldsymbol{\theta}^*, \boldsymbol{v}^*) + \mathcal{H}(\boldsymbol{\theta}_{t-1}, \boldsymbol{v}_{t-1})]) \quad (12.77) \)

(The transition probabilities cancel since the proposal is reversible.) Finally, we accept the proposal by setting \((\boldsymbol{\theta}_t, \boldsymbol{v}_t) = (\boldsymbol{\theta}^*, \boldsymbol{v}^*)\) with probability \(\alpha\), otherwise we set \((\boldsymbol{\theta}_t, \boldsymbol{v}_t) = (\boldsymbol{\theta}_{t-1}, \boldsymbol{v}_{t-1})\). (In practice we don't need to keep the momentum term, it is only used inside of the leapfrog algorithm.) See Algorithm 12.3 for the pseudocode.\(^6\)

```
**Algorithm 12.3:** Hamiltonian Monte Carlo

1 for t = 1 : T do
2   Generate random momentum v_{t-1} ~ N(0, Sigma)
3   Set (theta'_0, v'_0) = (theta_{t-1}, v_{t-1})
4   Half step for momentum: v'_{1/2} = v'_0 - (eta/2) nabla E(theta'_0)
5   for l = 1 : L - 1 do
6     theta'_l = theta'_{l-1} + eta Sigma^{-1} v'_{l-1/2}
7     v'_{l+1/2} = v'_{l-1/2} - eta nabla E(theta'_l)
8   Full step for location: theta'_L = theta'_{L-1} + eta Sigma^{-1} v'_{L-1/2}
9   Half step for momentum: v'_L = v'_{L-1/2} - (eta/2) nabla E(theta'_L)
10 Compute proposal (theta*, v*) = (theta'_L, v'_L)
11 Compute alpha = min(1, exp[-H(theta*, v*) + H(theta_{t-1}, v_{t-1})])
12 Set theta_t = theta* with probability alpha, otherwise theta_t = theta_{t-1}.
```

6. There are many high-quality implementations of HMC. For example, BlackJAX in JAX.

We need to sample a new momentum at each iteration to satisfy ergodicity. To see why, recall that $\mathcal{H}(\boldsymbol{\theta}, \boldsymbol{v})$ stays approximately constant as we move through phase space. If $\mathcal{H}(\boldsymbol{\theta}, \boldsymbol{v}) = \mathcal{E}(\boldsymbol{\theta}) + \frac{1}{2}\boldsymbol{v}^{\mathsf{T}}\boldsymbol{\Sigma}\boldsymbol{v}$, then clearly $\mathcal{E}(\boldsymbol{\theta}) \le \mathcal{H}(\boldsymbol{\theta}, \boldsymbol{v}) = h$ for all locations $\boldsymbol{\theta}$ along the trajectory. Thus the sampler cannot reach states where $\mathcal{E}(\boldsymbol{\theta}) > h$. To ensure the sampler explores the full space, we must pick a random momentum at the start of each iteration.

## 12.5.4 Tuning HMC

We need to specify three hyperparameters for HMC: the number of leapfrog steps \(L\), the step size \(\eta\), and the covariance \(\boldsymbol{\Sigma}\).

### 12.5.4.1 Choosing the number of steps using NUTS

We want to choose the number of leapfrog steps \(L\) to be large enough that the algorithm explores the level set of constant energy, but without doubling back on itself, which would waste computation, due to correlated samples. Fortunately, there is an algorithm, known as the **no-U-turn sampler** or **NUTS** algorithm [HG14], which can adaptively choose \(L\) for us.

### 12.5.4.2 Choosing the step size

When \(\boldsymbol{\Sigma} = \mathbf{I}\), the ideal step size \(\eta\) should be roughly equal to the width of \(\mathcal{E}(\boldsymbol{\theta})\) in the most constrained direction of the local energy landscape. For a locally quadratic potential, this corresponds to the square root of the smallest marginal standard deviation of the local covariance matrix. (If we think of the energy surface as a valley, this corresponds to the direction with the steepest sides.) A step size much larger than this will cause moves that are likely to be rejected because they move to places which increase the potential energy too much. On the other hand, if the step size is too low, the proposal distribution will not move much from the starting position, and the algorithm will be very slow.

In [BZ20, Sec 9.5.4] they recommend the following heuristic for picking \(\eta\): set \(\boldsymbol{\Sigma} = \mathbf{I}\) and \(L = 1\), and then vary \(\eta\) until the acceptance rates are in the range of 40%-80%. Of course, different step sizes might be needed in different parts of the state space. In this case, we can use learning rate schedules from the optimization literature, such as cyclical schedules [Zha+20d].

### 12.5.4.3 Choosing the covariance (inverse mass) matrix

To allow for larger step sizes, we can use a smarter choice for \(\boldsymbol{\Sigma}\), also called the **inverse mass matrix**. One way to estimate a fixed \(\boldsymbol{\Sigma}\) is to run HMC with \(\boldsymbol{\Sigma} = \mathbf{I}\) for a **warm-up** period, until the chain is “burned in” (see Section 12.6); then we run for a few more steps, so we can compute the empirical covariance matrix using \(\boldsymbol{\Sigma} = \mathbb{E}\left[(\boldsymbol{\theta}-\overline{\boldsymbol{\theta}})(\boldsymbol{\theta}-\overline{\boldsymbol{\theta}})^{\mathsf{T}}\right]\). In [Hof+19] they propose a method called the **NeuTra HMC** algorithm which “neutralizes” bad geometry by learning an inverse autoregressive flow model (Section 23.2.4.3) in order to map the warped distribution to an isotropic Gaussian. This is often an order of magnitude faster than vanilla HMC.
