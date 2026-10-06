
## 88 CHAPTER | 4 European Options

$P(m^Z \le b|Z_{t_2}, Z_{t_1}),$

where $m^Z$ denotes the maximum of $Z$ over the time interval $[t_1, t_2]$.
The probability of $Z_{t_2}$ conditional on $Z_{t_1}$ is

```
$P(Z_{t_2}|Z_{t_1}) = \frac{1}{\sigma\sqrt{2\pi\Delta t}} \exp\left\{\frac{(Z_{t_2}-Z_{t_1}-v\Delta t)^2}{2\sigma^2\Delta t}\right\},$
```

where $\Delta t = t_2 - t_1$.
From Bayes, we know that

```
$P(m^Z \le b|(Z_{t_2}, Z_{t_1})) = \frac{P(\{m^Z \le b, Z_{t_2}\}|Z_{t_1})}{P(Z_{t_2}|Z_{t_1})}.$
```

We show in [Appendix H.1](#)

```
$P(\{m^Z \le b, Z_{t_2}\}|Z_{t_1}) = \frac{1}{\sigma\sqrt{2\pi\Delta t}} \exp\left(\frac{2v(b-Z_{t_1})^2}{\sigma^2}\right)\exp\left(\frac{(Z_{t_2}+Z_{t_1}-2b-v\Delta t)^2}{2\sigma^2\Delta t}\right\},$
```

so

```
$P(m^Z \le b|(Z_{t_2}, Z_{t_1})) = \exp\left(\frac{2v(b-Z_{t_1})^2}{\sigma^2}\right)\exp\left(\frac{(Z_{t_2}+Z_{t_1}-2b-v\Delta t)^2+(Z_{t_2}-Z_{t_1}-v\Delta t)^2}{2\sigma^2\Delta t}\right).$
```

We will now use algebra to simplify this expression.

```
$P(m^Z \le b|(Z_{t_2}, Z_{t_1})) = \exp\left(\frac{4v\Delta t(b-Z_{t_1})^2+(Z_{t_2}+Z_{t_1}-2b-v\Delta t)^2+(Z_{t_2}-Z_{t_1}-v\Delta t)^2}{2\sigma^2\Delta t}\right)$
= \exp\left(\frac{4v\Delta t(b-Z_{t_1})-(Z_{t_2}-Z_{t_1}-v\Delta t)^2+2(b-Z_{t_1}))^2+(Z_{t_2}-Z_{t_1}-v\Delta t)^2}{2\sigma^2\Delta t}\right)$
= \exp\left(\frac{4v\Delta t(b-Z_{t_1})+4(b-Z_{t_1})(Z_{t_2}-Z_{t_1}-v\Delta t)+4(b-Z_{t_1})^2}{2\sigma^2\Delta t}\right)$
= \exp\left(\frac{2(b-Z_{t_1})(b-Z_{t_2})}{\sigma^2\Delta t}\right).$
```

which finally yields

```
$P(m^Z \le b|(Z_{t_2}, Z_{t_1})) = \exp\left(\frac{2(\log(b)-\log(S_{t_1}))(\log(b)-\log(S_{t_2}))}{\sigma^2\Delta t}\right). (4.5.19)$
```

Equation (4.5.19) gives the probability of the option having been knocked out between times $t_1$ and $t_2$ even when the asset prices $S_{t_1}$ and $S_{t_2}$ are greater

## Barrier Options Section | 4.5 89

B. The probability that the option has not been knocked out between times $t_1$ and $t_2$ is therefore

```
$P(m^Z > b|Z_{t_1}, Z_{t_2}) = 1 - \exp\left\{ -\frac{2(\log(B) - \log(S_{t_1}))(\log(B) - \log(S_{t_2}))}{\sigma^2 \Delta t} \right\}. (4.5.20)
```

This means that for the (complete) $i$-th scenario path, of $n$ time steps, the probability that $m^Z > b$ is

```
$BB_C^i = \prod_{j=0}^{n-1} \left\{ 1 - \exp\left\{ -\frac{2(\log(B) - \log(S_{t_j}^i))(\log(B) - \log(S_{t_{j+1}}^i))}{\sigma^2 \Delta t} \right\} \right\}$
```

where $S_t^i$ is the $i$-th scenario asset price at time $t_i$. The basic Monte Carlo $i$-th scenario option value $DO_i$ can therefore be adjusted as

```
$DO_i^i = DO_i BB^c$.
```

and the New Monte estimate $DO^*$ is

```
$DO^* = \frac{\sum_{i=1}^{Scenarios} DO_i^*}{Scenarios}$
```

where more details can be found in Code example 4.8.

```cpp
private double MonteCarloSim(bool is_put)
    int seed = ill;
    double[] asset_path = new double[timeSteps];
    double time_step = timeToExpiry / timeSteps;
    double sqrt_time = System.Math.Sqrt(time_step);
    double disc = System.Math.Exp(-RiskFree * timeToExpiry);
    set_seed(seed);
    double opt_val = 0.0;
    bool not_out = true;
    int k = 0;
    double strike = 0.0;
    double mean = (RiskFree - DividendYield) * Fstrike * 0.5 * time_step;
    double std = Fstrike * Sqrt(time_step);
    for (int i = 0; i < Scenarios; i++) {
        // generate the asset path
        double STN = F1;
        not_out = true;
        k = 0;
        while (not_out && k < timeSteps) {
            z = RndNorm(mean, std);
            STN *= System.Math.Exp(z);
            if (STN < BarrierLevel) not_out = false;
            asset_path[k] = STN;
            k++;
        }
        if (is) {
            opt_val = System.Math.Max(Strike - STN, 0.0); // The Brownian barrier crossing crossing probability to enhance
```

**Code example 4.8** An example using the pricing of a European down and call option.

## 90 CHAPTER | 4 European Options

```cpp
        else
        {
            opt_val = System.Math.Max(Strike, 0.0);
        }
        if (not_out) {
            // only has value if asset value is above the barrier
            // compute the probability that the asset remained after the
            if (UseBrownianBridge) {
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
            } else {
                // do not use Brownian Bridge
                sum_vals = opt_val * disc;
            }
            double temp = sum_vals / scenarios;
            return temp;
```## 4.6 SELECTED EXERCISES

1. Write a program using Excel's functions NORMS and RAND to compute the value of European put and call options. Verify that the values agree with expressions in Section 4.5.
2. Write a program that finds the strike $E_p$, required to make the value of a European put option have the same as a European call option, or write a program that finds the strike $E_p$, required to make the value of a European put option have the same as a European call, that is $C(S, E, \tau) = P(S, E_p, \tau)$.
3. Consider the mean reversion process $dS_t = \alpha(\mu - \log(S_t))S_t dt + \sigma S_t dW_t$, where $S_t$ is the asset value at time $t$, $\alpha > 0$ is speed of mean reversion, $\mu$ is long-term mean, $\sigma$ is volatility, and $dW_t$ is Brownian motion. Let $X_t = \log(S_t)$ and show using results of Section 4.5 that the mean and variance at time $T > 0$ are given

```
$E[X_T] = \exp(-\alpha T)X_0 + (\mu - \frac{\sigma^2}{2\alpha})(1 - \exp(-\alpha T))$
```
$Var[X_T] = \frac{\sigma^2}{2\alpha}(1 - \exp(-2\alpha T))$
respectively.

## Selected Exercises Section | 4.6 91

Hence, show that the value of a call option is

$c(S, E, \tau) = N(d_1) - e^{-r\tau}N(d_2),$

where

$d_2 = \frac{\log(S/E) + (r - \frac{\sigma^2}{2})\tau}{\sigma\sqrt{\tau}} = d_1 - \sigma\sqrt{\tau}$

and

$\hat{\sigma}^2 = \frac{\sigma^2}{2\alpha}(1 - \exp(-2\alpha T)).$

4. Let the price of an asset $S_t$ follow GBM, and also the interest rate be $r = 0$. Show that the conditional variance $Var(S_t|S_t \geq K)$, when $S_t$ is greater or equal to $K$ is given by

$Var(S_t|S_t \geq K) = S_t^2 \exp(\sigma^2\tau)N(d_3) - 2KN(d_1) + K^2N(d_2) - C(S,K,\tau)^2,$

where $C(S,K,\tau)$ follow Weibull distribution of a European call option

$d_1 = \frac{\log(S/K) + \frac{1}{2}\sigma^2\tau}{\sigma\sqrt{\tau}}, \quad d_2 = \frac{\log(S/K) - \frac{1}{2}\sigma^2\tau}{\sigma\sqrt{\tau}}$

$d_3 = \frac{\log(S/K) + \frac{3}{2}\sigma^2\tau}{\sigma\sqrt{\tau}}$

5. Let the variable $X$ follow a Weibull distribution with density function

$f(X) = \alpha\beta X^{\beta-1} \exp(-\alpha X^{\beta}).$

The value of a call option $C(X,K)$ is obtained by evaluating the integral $\int_{-\infty}^{\infty} (X-K)^+ \alpha\beta X^{\beta-1} \exp(-\alpha X^{\beta})dX$.

Show that

$C(X,K) = \frac{1}{\alpha^{\beta}} \Gamma(1+\frac{1}{\beta}) \left\{1-P(1+\frac{1}{\beta},\alpha K^{\beta})\right\} - K\exp(-\alpha K^{\beta}),$

where $P(a,b)$ is the incomplete gamma function given by

$P(a,b) = \frac{1}{\Gamma(a)} \int_{0}^{b} \omega^{a-1} \exp(-\omega)dw,$

and $\Gamma(a)$ is the gamma function.

## Chapter 5

## Single Asset American Options

## 5.1 INTRODUCTION

In Chapter 4, we discussed single asset European options and the analytic formulae we were used to price them. Here, we will consider the valuation of single asset American style options using both numeric methods and analytic formula; in addition, we will discuss the use of numerical techniques to value certain European options. The coverage in this section is as follows:

- Analytic approximation techniques for the valuation of American options.
- Binomial lattice techniques used for the valuation of American and European options.
- The valuation of American and European barrier options using finite-difference grids.
- The valuation of American options via Monte Carlo simulation.

It should be mentioned that although much of the discussion concerns vanilla European and American puts and calls, the techniques can be modified without much difficulty to include more exotic options with customized payoffs and early exercise features.

## 5.2 APPROXIMATIONS FOR VANILLA AMERICAN OPTIONS

### 5.2.1 American Call Options with Dividends

In this section, we will consider the valuation of vanilla American call options with cash dividends and discuss the methods of both the Roll and Geske, and Whaley and Black. We will first consider the Roll, Geske, and Whaley method.

The Roll, Geske, and Whaley Approximation This method uses the work of Roll (1977), Geske (1979), and Whaley (1981). Let $S$ be the current (time $t$) price of an asset which pays a single cash dividend $D_1$ at time $t_1$. At the ex-dividend date, $t_1$, there will be a decrease in the value of $S_t$ to $S_t-D_1$. Also the current price of netcrow dividends is

```
$S_D = S - D_1 \exp(-r(t_1 - t)). (5.2.1)
```

Now consider an American call option, with strike $E$ and expiry time $T$, which is taken out on this asset. At $t_1$, there will be a given ex-dividend asset
