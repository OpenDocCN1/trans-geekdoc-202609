# Introduction to stochastic processes

Ornstein–Uhlenbeck stochastic paths can be simulated using

$X_{t+dt} = X_t \exp(-\alpha dt) + \sigma \sqrt{\frac{1 - \exp(-2\alpha dt)}{2\alpha}} dZ \quad (2.10.15)$

From Eq. (2.10.14) we can write

$E[X_{t+dt}|X_t] = X_t \exp(-\alpha dt)$

$Var[X_{t+dt}|X_t] = \sigma^2 \left\{ \frac{1 - \exp(-2\alpha dt)}{2\alpha} \right\}$

We will show that in the limit $dt \to 0$, Eq. (2.10.15) reduces to the Ornstein–Uhlenbeck process given in Eq. (2.10.1). For small $dt$ we can take a first-order expansion of the exponentials in Eq. (2.10.15) to obtain

$X_{t+dt} = X_t \{(1 - \alpha dt)\} + \sigma \sqrt{\frac{(1 - (1 - 2\alpha dt))}{2\alpha}} dZ$

so

$X_{t+dt} = X_t - X_t \alpha dt + \sigma \sqrt{\frac{2\alpha dt}{2\alpha}} dZ$

Therefore

$X_{t+dt} = X_t - \alpha X_t dt + \sigma \sqrt{dt} dZ$

which is

$dX_t = -\alpha X_t dt + \sigma dW_t$

# 2.11 The Ornstein–Uhlenbeck bridge

An Ornstein–Uhlenbeck process have value $X_{t_0}$ at time $t_0$ and $X_{t_1}$ at time $t_1$. We are interested in the distribution of $X_t$ at an intermediate point, of $P(X_t|{X_{t_0}, X_{t_1}\)$, where $t_0 < t < t_1$. We will show that $X_t$ is a Gaussian with conditional mean

$\mu_t = X_{t_0} \exp(-\alpha(t - t_0)) \left\{ \frac{1 - \exp(-2\alpha(t - t_0))}{\gamma^2} \right\ + X_{t_1} \exp(-\alpha(t - t_1)) \left\{ \frac{1 - \exp(-2\alpha(t - t_1))}{\gamma^2} \right\ \quad (2.11.1)$

and conditional variance

$V_t = \frac{(1 - \exp(-2\alpha(t - t_0)))(1 - \exp(-2\alpha(t - t_1)))}{2\alpha(1 - \exp(-2\alpha(t_1 - t_0)))} \quad (2.11.2)$

where $\gamma = \exp(-\alpha(t_1 - t_0))$.