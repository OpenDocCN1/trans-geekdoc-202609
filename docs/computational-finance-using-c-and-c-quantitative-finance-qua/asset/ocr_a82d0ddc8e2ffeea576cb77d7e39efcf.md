# 92 Computational Finance Using C and C#

If the barrier level is B the option will be knocked out when $S \le B$, or equivalently $\log(S) \le \log(B)$. This will be expressed as $X \le b$, where $b = \log(B)$.

The basic approach to simulating the down and out option is to first decide many scenarios and also how many TimeSteps are to be in each scenario. The size of each time step is $time\step = TimeTimeToExpiry/TimeSteps$. For each scenario the path of $X_t$ is advanced in time $t$ to $t + \Delta t$ using Eq. (4.5.18), with $dr = time\step$ and a value for $W_t$, from a Gaussian random number generator. Path construction is stopped if either the option expiry time is reached or if the option is knocked out before-i.e., $X \le b$. The option is knocked out before the payoff for that scenario is zero. We will denote the option value obtained from the $i$th scenario by $DO_i$ where $i=1, \dots$. Scenarios. The option value is the average of $DO_i$ over all scenarios; for more details see Code excerpt4.8.

One problem with this approach is that it does not take into account the possibility that $X_T \le b, t < \tau < t + \Delta t$, even though $X_t > b$ and $X_{t+\Delta t} > b$. In these circumstances the option would be knocked out, since X hit (or crossed) the barrier $b$ at time $\tau$, but then increased to the value of $X_{t+\Delta t}$ at time $t + \Delta t$.

We will now discuss the Brownian bridge method deals with this situation. We take two time points $t_1$ and $t_2 = t_1 + \Delta t$, and assume that both $X_{t_1}$ and $X_{t_2}$ are above the (logarithmic) barrier level $b$. We want to find the probability that in the time interval $[t_1, t_2]$, the asset price went lower than $B$, and use this to get more accurate values for down and out options. The required barrier crossing probability is thus:

> $P(m_{t_1}^{t_2} \le b|X_{t_1}, X_{t_2}) =$

where $m_{t_1}^{t_2}$ denotes the minimum of X over the time interval $[t_1, t_2]$. The probability density of $X_{t_2}$ conditional on $X_{t_1}$ is

```
$p(X_{t_2}|X_{t_1}) = \frac{1}{\sigma \sqrt{2\Delta t}} \exp\left\{ \frac{(X_{t_2} - X_{t_1} - v\Delta t)^2}{2\sigma^2 \Delta t} \right\}$
```

where $\Delta t = t_2 - t_1$. From Bayes law we know that:

```
$p(m_{t_1}^{t_2} \le b|X_{t_1}, X_{t_2}) = \frac{p(m^X \le b|X_{t_2})}{p(X_{t_2}|X_{t_1})}$
```

We show in Appendix I that

```
$p(m_{t_1}^{t_2} \le b|X_{t_1}) = \frac{1}{\sigma \sqrt{2\pi \Delta t}} \exp\left\{ \frac{2v(b - X_{t_1})}{\sigma^2} \right\} \exp\left\{ \frac{(X_{t_2} + X_{t_1} - 2b - v\Delta t)^2}{2\sigma^2 \Delta t} \right\}$
```