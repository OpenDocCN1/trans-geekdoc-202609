# 90 CHAPTER | 4 European Options

```
}
else
{
    opt_val = System.Math.Max(Strike, 0.0);
}
if (not_out)
{// only has value if asset value is above the barrier_level
// compute the probability that the asset remained after the barrier
if (UseBrownianBridge)
{
    double total_probability = 1.0, pr;
    double sigma2, f1 = sigma1;
    double log_barrier_level = System.Math.Log(barrierLevel);
    double fac;
    for (int j = 0; j < fSteps; j++) {
        double log_S_i = System.Math.Log(asset_path[j]);
        double log_S_i1 = System.Math.Log(asset_path[j + 1]);
        fac = exp(-2.0 * (barrier_level - log_S_i) * (barrier_level - log_S_i1) / (sigma2 * time_step)); // probability of staying above the barrier between i and i+1
        pr *= fac;
    }
sum_vals = total_probability * opt_val * disc;
}\else{
    // do not use the Brownian Bridge
    sum_vals = opt_val * disc;
}
double temp = sum_vals / (double)numberScenarios;

return temp;
```

Code excerpt 4.8 (Continued).

# 4.6 SELECTED EXERCISES

+   1. Write a program using Excel's functions NORMSINV and RAND to compute the value of European put and call options. Verify that the values agree with the expressions given in Section 4.4.5.
2. Write a program that finds the strike, $E_p$, required to make the value of a European put option have the same as a European call option, or Write a program that finds the strike, $E_p$, required to make the value of a European put option have the same as a European call option, that is, $C(S, E_c, 	au) = P(S, E_p, 	au)$.
3. Consider the mean reversion stochastic process

$dS_t = \alpha(\mu - \log(S_t))S_t dt + \sigma S_t dW_t$,

Where $S_t$ is the asset value at time $t$, $\alpha > 0$ is the speed of mean reversion, $\mu$ is the long-term mean, $\sigma$ is the volatility, and $dW_t$ is the Brownian motion.
Let $X_t = \log(S_t)$ and show using the results of Section 2.10 that the mean and variance at time $T > 0$ are given

```
$E[X_T] = \exp(-\alpha T)X_0 + (\mu - \frac{\sigma^2}{2\alpha})(1 - \exp(-\alpha T))$
```

```
$Var[X_T] = \frac{\sigma^2}{2\alpha}(1 - \exp(-2\alpha T))$
```

respectively.