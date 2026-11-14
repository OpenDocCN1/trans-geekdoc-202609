![](bbox=[0.17, 0.11, 0.84, 0.31])

Figure 25.6: Illustration of the forwards diffusion process in continuous time. Yellow lines are sample paths from the SDE. Heat map represents the marginal distribution computed using the probability flow ODE. From Slide 43 of [KGV22]. Used with kind permission of Karsten Kreis.

We can gain some intuition for these processes by looking at the 1d example in Figure 25.6. We can draw multiple paths as follows: sample an initial state from the data distribution, and then integrate over time using **Euler-Maruyama** integration:

```
x(t + \Delta t) = x(t) + f(x(t), t)\Delta t + g(t)\sqrt{\Delta t}\mathcal{N}(\mathbf{0}, \mathbf{I})
```

We can see how the data distributionat at t = 0, on the left hand side, gradually gets transformed to a pure noise distribution at t = 1, on the right hand side.

In [Son+21b], they show that the SDE corresponding to DDPMs, in the T -> infinity limit, is given by

```
dx = -\frac{1}{2}\beta(t)xdt + \sqrt{\beta(t)}d\omega
```

where \beta(t/T) = T\beta_t. Here the drift term is proportional to -x, which encourages the process to return to 0. Consequently, DDPM corresponds to a **variance preserving** process. By contrast, the SDE corresponding to SGMs is given by the following:

```
dx = \sqrt{\frac{d|\sigma(t)|^2}{dt}}d\omega
```

where \sigma(t/T) = \sigma_t. This SDE has zero drift, so corresponds to a **variance exploding** process.

# 25.4.2 Forwards diffusion ODE

Instead of adding Gaussian noise at every step, we can just sample the initial state, and then let it evolve deterministically over time according to the following **ordinary differential equation** or **ODE**:

```
dx = \left[ f(x, t) - \frac{1}{2}g(t)^2 \nabla_x \log p_t(x) \right] dt
```