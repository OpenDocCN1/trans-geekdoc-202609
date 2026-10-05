# Time Series Econometrics

A straightforward implementation of the Yule-Walker and Durbin-Levinson algorithms is given by the functions .quantQ.ts.YuleWalker[p;data] and .quantQ.ts.DurbinLevinson[data;p] described in the second part of the chapter. The least square method produces the same estimates of the AR(p) parameters as the Yule-Walker equations but is much slower than the iterative approach. The Durbin Levinson algorithm is as fast as inverting the Toeplitz matrix $R_p^{-1}r_p$.

```
simData::quantQ.ts.simAR(0.4;0.3;100000?quantQ.simul.genBoxMuller([])
quantQ.ts.estARP(simData[3])
quantQ.ts.yuleWalker(simData[3])
quantQ.ts.DurbinLevinson[simData[3])
```

```
returns:
0.02288053 0.3942897 0.2985167 0.008251775
0.3943002 0.2985118 0.008257555
0.3943002 0.2985118 0.008257555
```

However,
\t quantQ.ts.estARP[data:3]
\t quantQ.ts.yuleWalker[data:3]
\t quantQ.ts.DurbinLevinson[data:3])

shows that it takes 913 milliseconds to estimate the parameters of 100,000 random numbers following the ARMA(1,1) model $X_t = 0.4X_{t-1} + 0.3X_t + \epsilon_t$, by solving the SLS estimator which takes 26 milliseconds by inverting the Toeplitz matrix and only 12 milliseconds by solving the Durbin-Levinson iterative algorithm:

+   913
26
12

# 14.1.3 MA(q) Process

Autoregressive processes are long memory models. They generally have an infinite non-zero autocorrelation decaying over time. Autoregressive processes cannot represent short memory series, where the current value of the series $X_t$ is only correlated with a few past values $X_{t-1}$. This section presents moving average processes that are generally a function of a short process of order $q$, denoted as MA(q), is defined as:

$X_t = c + \epsilon_t + \alpha_1\epsilon_{t-1} + \alpha_2\epsilon_{t-2} + \dots + \alpha_q\epsilon_{t-q}$,

where $\alpha_1, \alpha_2,\dots, \alpha_q$ are the coefficients of the process, $c$ and $\epsilon$ is the white noise, $\epsilon_i \sim N(0,\sigma^2)$. The MA(q) process is stationary by construction. Its expectation is $E[X_t]$ and variance is $Var[X_t] = \gamma(0) = \sigma^2(1 + \alpha_1^2 + \alpha_2^2 + \dots + \alpha_q^2)$.

The autocorrelation $\gamma(s) = \frac{1}{\gamma(0)}\sigma^2(\alpha_s + \alpha_{s+1}\alpha_1 + \alpha_{s+2}\alpha_2 + \dots + \alpha_q\alpha_{q-s}) s \leq q$,

that $X_t$ is a zero-mean process with finite variance for each $t$ and $E[X_tX_j] = \gamma(i,j)$, where $|i-j|=n$ is non-singular for each $n=1,2,\dots$