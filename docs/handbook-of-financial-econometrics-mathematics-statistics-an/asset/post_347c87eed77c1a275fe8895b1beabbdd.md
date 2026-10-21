
Substituting equation (97.9) into equation (97.13), we have a differential equation as

```
\dot{p}(t) + \left[ \frac{\lambda \dot{n}(t)}{n(t)} - k \right] p(t) = -H(t),
```

where

```
H(t) = \frac{(\bar{r}(t) - g(t)) A'(0) e^{\int_0^t g(s) ds}}{n(t)} - \frac{a' A'(0)^2 \sigma^2(t) e^{2 \int_0^t g(s) ds}}{n(t)^2}.
```

Solving the differential equation (97.14), we have

```
p(t) = \frac{e^{kt}}{n(t)^\lambda} \int_t^T H(s) n(s)^\lambda e^{-ks} ds.
```

Then, equation (97.17) can be obtained from equations (97.15) and (97.16) implying that the initial value of a stock can be expressed as the summation of present values of its earnings stream adjusted by the risk taken by the firm.

```
p(0) = \frac{1}{n(0)^\lambda} \int_0^T \left[ n(t)^{\lambda-1} (\bar{r}(t) - g(t)) A'(0) e^{\int_0^t g(s) ds} - a' A'(0)^2 \sigma^2(t) n(t)^{\lambda-2} e^{2 \int_0^t g(s) ds} \right] e^{-kt} dt
```

We maximize the stock price per share at time 0, p(0), defined in equation (97.17) by allowing both the growth rate g(t) and the number of shares outstanding n(t) to change over time. When the growth rate g(t) is determined, then the amount of new investment is also obtained. Once the amount of new investment and new equity issue \dot{n}(t)p(t) are determined, then we can calculate the amount of the new debt and retained earnings (or dividend payout) at the same time. Therefore, this implies that we can obtain the optimal growth rate and the optimal payout ratio simultaneously by maximizing the stock price.

Following the Euler–Lagrange condition (see Chiang, 1984), we take the first-order conditions on equation (97.17) with respect to t for both n(t) and g(t), and set these two first-order conditions equal to zero.⁶ Then we can obtain equations (97.18) and (97.19), respectively.

> For the derivation of the partial differential equation, please refer to Appendix 97A.

> For example, we assume that the amount of new investment is $1,000,000, new equity issue is $200,000, the target debt-to-total-asset ratio is 30%, and net income is $2,000,000. Then we know the new debt issue is $1,000,000 × 30% = $300,000. Therefore, the retained earnings will be $1,000,000 – $200,000 – $300,000 = $500,000. In other words, the optimal payout ratio is ($2,000,000 – $500,000)/$2,000,000 = 75%.

$$n(t)=\frac{(\lambda-2)a'A'(0)\,\sigma^{2}(t)\,e^{\int_{0}^{t}g(s)ds}}{(\lambda-1)[\bar{r}(t)-g(t)]},\text{ and}\tag{97.18}$$ $$n(t)=\frac{2a'A'(0)\,\sigma^{2}(t)\,e^{\int_{0}^{t}g(s)ds}}{\bar{r}(t)-g(t)-\frac{\dot{g}(t)}{g(t)}}.\tag{97.19}$$

From equations (97.18) and (97.19), we have

$$\lambda g(t)^{2}-\lambda\bar{r}(t)g(t)+(2-\lambda)\dot{g}(t)=0.\tag{97.20}$$

Under the assumption $\bar{r}(t)=\bar{r}$, equation (97.18) is a nonlinear differential equation in $g(t)$, which is the logistic equation discovered by Verhulst (1845, 1847). Therefore, the optimal growth rate $g^{*}(t)$ from equation (97.20) is⁷

$$g^{*}(t)=\frac{\bar{r}}{1-\left(1-\frac{\bar{r}}{g_{0}}\right)e^{\lambda\bar{r}t/(\lambda-2)}}$$ $$=\frac{g_{0}\bar{r}}{g_{0}+(\bar{r}-g_{0})e^{\lambda\bar{r}t/(\lambda-2)}},\tag{97.21}$$

where $g_{0}$ is the initial growth rate.

Equation (97.21) shows an optimal growth rate, $g^{*}(t)$, exists when we maximize a firm's stock price per share by jointly determining the growth rate and the payout ratio. Therefore, different from Higgins' (1977) sustainable growth rate model, the payout ratio (or retention rate) does not affect the optimal growth rate.

## 97.2.4 Comparative statics analyses on optimal growth rate

The optimal growth rate can be determined by (1) the time horizon $(t)$, (2) the degree of market perfection or imperfection $(\lambda)$, (3) the rate of return on equity $(\bar{r})$, and (4) the initial growth rate $(g_{0})$. In addition, the optimal growth rate is a logistic equation which has a special characteristic called the mean-reverting process. In the following subsections, we will numerically and graphically show how the mean-reverting process of the optimal growth rate works. Furthermore, we provide the sensitivity analysis and the partial derivatives on the optimal growth rate with respect to the time horizon (t), the degree of market perfection (λ), the rate of return on equity (r̄), and the initial growth rate (g0). We will discuss how these factors affect the optimal growth rate, respectively. In addition, empirical evidence of the mean-reverting process of the optimal growth rate is provided in Section 97.4.

### 97.2.4.1 Case I: Time horizon

Taking the derivative of the optimal growth rate with respect to the time, we can obtain equation (97.22).

$$\dot{g}^*(t) = \frac{\partial g^*(t)}{\partial t} = \frac{\bar{r}\left(1 - \frac{\bar{r}}{g_0}\right)\left(\frac{\bar{r}\lambda}{(\lambda-2)}\right) e^{\bar{r}\lambda t/(\lambda-2)}}{\left[1 - \left(1 - \frac{\bar{r}}{g_0}\right) e^{\bar{r}\lambda t/(\lambda-2)}\right]^2}, \quad (97.22)$$

where

$$g^*(t) = \frac{\bar{r}}{1 - \left(1 - \frac{\bar{r}}{g_0}\right) e^{\lambda\bar{r}t/(\lambda-2)}}.$$

From equation (97.22), we can find that the optimal growth rate follows a mean-reverting process. If the initial growth rate, (g0), is greater than the rate of return on equity, (r̄), the change in the optimal growth rate, ġ*(t), is negative. If the initial growth rate is lower than the rate of return on equity, the change in the optimal growth rate is positive. If the initial growth rate is equal to the rate of return on equity, the change in the optimal growth rate is zero; therefore, the optimal growth rate is approaching the rate of return on equity, r̄, over time. Table 97.1 and Figure 97.1 show the time path of the optimal growth rate from the initial condition (g0) to its steady-state value.

The important implications of the results derived from equation (97.22) and partially graphed in Figure 97.1 are as follows:

- (i) Under a finite time horizon, $g^*(t) < \bar{r}$ and $\dot{g}^*(t) < 0$ when $g_0 < \bar{r}$.
- $g^*(t) = \bar{r}$ and $\dot{g}^*(t) = 0$ when $g_0 = \bar{r}$
- $g^*(t) > \bar{r}$ and $\dot{g}^*(t) > 0$ when $g_0 > \bar{r}$.
- (ii) When time horizon approaches infinity, the optimal growth rate approaches the steady-state value of $\bar{r}$.

## Table 97.1: Mean-reverting process of the optimal growth rate.

Panel A. ROE = 40% λ = 0.95

| Time (t) | g0=5% | g0=15% | g0=25% | g0=35% | g0=40% | g0=45% | g0=55% | g0=65% | g0=75% | g0=85% | g0=95% |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 0.6702 | 0.6336 | 0.5926 | 0.5463 | 0.4938 | 0.4335 | 0.4000 | 0.3638 | 0.2821 | 0.1851 | 0.0681 |
| 2 | 0.5561 | 0.5381 | 0.5170 | 0.4917 | 0.4610 | 0.4228 | 0.4000 | 0.3741 | 0.3099 | 0.2212 | 0.0910 |
| 3 | 0.4972 | 0.4871 | 0.4748 | 0.4597 | 0.4406 | 0.4156 | 0.4000 | 0.3816 | 0.3326 | 0.2560 | 0.1189 |
| 4 | 0.4630 | 0.4569 | 0.4493 | 0.4398 | 0.4274 | 0.4107 | 0.4000 | 0.3870 | 0.3505 | 0.2874 | 0.1512 |
| 5 | 0.4419 | 0.4380 | 0.4331 | 0.4269 | 0.4187 | 0.4074 | 0.4000 | 0.3909 | 0.3642 | 0.3142 | 0.1864 |
| 6 | 0.4283 | 0.4257 | 0.4225 | 0.4183 | 0.4128 | 0.4051 | 0.4000 | 0.3936 | 0.3744 | 0.3361 | 0.2225 |
| 7 | 0.4193 | 0.4176 | 0.4154 | 0.4126 | 0.4089 | 0.4036 | 0.4000 | 0.3955 | 0.3818 | 0.3533 | 0.2571 |
| 8 | 0.4132 | 0.4121 | 0.4106 | 0.4087 | 0.4061 | 0.4025 | 0.4000 | 0.3969 | 0.3872 | 0.3663 | 0.2884 |
| 9 | 0.4091 | 0.4083 | 0.4073 | 0.4060 | 0.4042 | 0.4017 | 0.4000 | 0.3978 | 0.3910 | 0.3759 | 0.3151 |
| 10 | 0.4063 | 0.4058 | 0.4051 | 0.4042 | 0.4029 | 0.4012 | 0.4000 | 0.3985 | 0.3937 | 0.3829 | 0.3368 |
| 11 | 0.4044 | 0.4040 | 0.4035 | 0.4029 | 0.4020 | 0.4008 | 0.4000 | 0.3989 | 0.3956 | 0.3879 | 0.3538 |
| 12 | 0.4030 | 0.4028 | 0.4024 | 0.4020 | 0.4014 | 0.4006 | 0.4000 | 0.3993 | 0.3969 | 0.3915 | 0.3666 |
| 13 | 0.4021 | 0.4019 | 0.4017 | 0.4014 | 0.4010 | 0.4004 | 0.4000 | 0.3995 | 0.3978 | 0.3941 | 0.3762 |
| 14 | 0.4015 | 0.4013 | 0.4012 | 0.4010 | 0.4007 | 0.4003 | 0.4000 | 0.3996 | 0.3985 | 0.3958 | 0.3831 |
| 15 | 0.4010 | 0.4009 | 0.4008 | 0.4007 | 0.4005 | 0.4002 | 0.4000 | 0.3997 | 0.3989 | 0.3971 | 0.3881 |
| 16 | 0.4007 | 0.4006 | 0.4006 | 0.4005 | 0.4003 | 0.4001 | 0.4000 | 0.3998 | 0.3993 | 0.3980 | 0.3916 |
| 17 | 0.4005 | 0.4005 | 0.4004 | 0.4003 | 0.4002 | 0.4001 | 0.4000 | 0.3999 | 0.3995 | 0.3986 | 0.3941 |
