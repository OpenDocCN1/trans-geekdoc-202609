# The Jump Behavior of a Foreign Exchange Market

The first equation in equation (52.1) is the observation (level) equation, and the second is the state (transition) equation. At a given time t, the observation equation implies that the change in the exchange rate follows a normal distribution with mean d and variance h_{t-1}. The state equation, by contrast, describes how the state variable h_t evolves over time. The variance for the next period is serially correlated with that of the current period. The covariance matrix of ε_t and u_t is

```
var(e_t) ≡ Σ ≡ \begin{pmatrix} 1 & \rho\sigma_v \\ \rho\sigma_v & \sigma_v^2 \end{pmatrix},
where e_t ≡ (ε_t, u_t)'.
```

If there is an asymptotic relationship in the time series, the rise or fall of the observation equation will affect the realization of the state variable and the correlation coefficient will not be zero. The correlation coefficient between the residuals of the observation and state equations is a measure of the leverage effect. In some financial time series, the leverage effect plays a significant role. For example, the leverage effect in the US stock market index is about -0.3 to -0.5 (Jacquier et al. 2004).

If we add a jump component to the observation equation, the model becomes

```
r_t = d + \sqrt{h_{t-1}}\varepsilon_t + \xi_t^r J_t^r
h_t = \alpha + \delta h_{t-1} + \sqrt{h_{t-1}}u_t.
(52.2)
```

We refer to this as the SVJ. The jump component \xi_t^r J_t^r is a product of J_t^r, which controls whether the jump occurs, and \xi_t^r, which controls the size of the jump. The jump event variable J_t^r follows a Bernoulli distribution, with pr(J_t^r = 1) = \lambda_r. The jump size variable \xi_t^r is normally distributed with mean u_r and variance \sigma_r^2.

Moving one step further, we can add a jump component to the state equation as well. If the jump in the level and state equations is independent, we arrive at an SV model with independent jumps in the level and state equations (SVIIJ). The SVIIJ model can be written as follows:

```
r_t = d + \sqrt{h_{t-1}}\varepsilon_t + \xi_t^r J_t^r
h_t = \alpha + \delta h_{t-1} + \sqrt{h_{t-1}}u_t + \xi_t^v J_t^v.
(52.3)
```

The jump event variable in the state equation J_t^v also follows a Bernoulli distribution, with pr(J_t^v = 1) = \lambda_v. To ensure positive jump sizes in the state equation, \xi_t^v follows an exponential distribution with mean u_v. With