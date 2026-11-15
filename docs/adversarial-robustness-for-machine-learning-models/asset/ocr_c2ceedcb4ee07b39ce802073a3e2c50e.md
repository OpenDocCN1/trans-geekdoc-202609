et al. (2020c) proposed to augment the original neural ODE model (13.4) with two kinds of stochastic terms: one is the diffusion term (to model Gaussian noise), and the other is jump term (to model Bernoulli noise); formally,

```
$h_t = h_s + \underbrace{\int_s^t f(h_\tau, \tau; w)d\tau}_{\text{drift term}} + \underbrace{\int_s^t G(h_\tau, \tau)dB_\tau}_{\text{diffusion term}} \\
+ \underbrace{\int_s^t J(h_\tau, \tau) \odot Z_{N_\tau} dN_\tau}_{\text{jump term}} .$
```

Compared with neural ODE model in (13.4) that only contains deterministic component (drift term), we add two extra terms in (13.6) to model different nature of randomness, diffusion and jump terms. The diffusion term consists of Brownian motion $B_t$ and its coefficient $G$ (optionally) parameterized by unknown variables $v$. Inside the jump term, the deterministic function $J(h_\tau, \tau)$ controls the jump size, the random variables $Z_{N_\tau} \sim \text{Bernoulli}(\pm 1, p)$ control the direction; and $N_\tau \sim \text{Poisson}(\lambda \tau)$ is a Poisson process counting the “frequency” of jumps.

To explain the supervisor robustness performance of RSE, we just need the diffusion term. The $dB_t$ term is also know as the Brownian motion, which can be viewed as i.i.d. Gaussian random variables with distribution $\mathcal{N}(0, dt)$. This is thus a small Gaussian random variable added to the hidden state, similar to the Gaussian noise in RSE but at the continuous limit.

The behavior of model’s prediction, in the Neural ODE case, can be viewed as how the initial value ($h_0$) affects the final value ($h_t$) in the the differential equation like (13.4). The solution of the ODE system is usually more sensitive to the initial point, however, it has been shown that the diffusion term in (13.6) can lead to the “converged” solution under certain input perturbation. More specifically, it can be shown that under certain condition, the Neural SDE system (13.6) has a converged value of $\lim_{t \to \infty} h_t$, which means the prediction will be stable with respect to input perturbation, when there’s infinite depth. More details can be found in (Liu et al., 2020c).

In addition to adding randomness into each convolution block, another method (Liu et al., 2019d) introduced a new min-max formulation to combine adversarial training with Bayesian neural networks (BNNs). All weights in a Bayesian neural network are represented by probability distributions over possible values, rather than having a single fixed value. The