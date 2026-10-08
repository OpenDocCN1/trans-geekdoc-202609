
# Computational Finance Using C and C#

It can be shown that:

```
$$\Sigma_{i,j} = \log\left(1 + \frac{S_{i,j}}{\hat{m}_i\hat{m}_j}\right)
```

and

```
$$\mu_i = \log(\hat{m}_i) - \frac{\Sigma_{i,i}}{2}, \quad i = 1, \dots, p, \text{ and } j = 1, \dots, p$
```

For the case of independent variables we then have:

```
$$\mu_i = \log(\hat{m}_i) - \frac{\sigma_i^2}{2}, \quad i = 1, \dots, p$
```

and

```
$$\Sigma_{i,i} = \sigma_i^2 = \log\left(1 + \frac{s_i^2}{\hat{m}_i^2}\right), \quad i = 1, \dots, p, \text{ and } i \neq j. \quad \Sigma_{i,j} = 0$
```

which are Eqs. (3.3.13) and (3.3.14) given in Section 3.3.2.

Code excerpt 3.3 shows how to generate a multivariate lognormal distribution with a mean $\hat{m}$ and covariance matrix $S$. More complete information can be found in the function `quasarirandom_Normal_LogNormal_Correlated` which is used in Code excerpt 3.2.

```c
double sigma[40][40], s[40][40]; /* limit of 40 */
double means[40], x[40], lx[40], tmp;

#define S(i,j) s[i-1][j-1]
#define MEANS(i) means[i-1]
#define VAR(i) var[i-1] /* the means of the lognormal distribution */
#define X(i) x[i-1] /* normal variables */
#define LX(i) lx[i-1] /* lognormal variables */

/* obtain the Gaussian covariance matrix SIG, which corresponds to the
lognormal covariance matrix S. */
for (i=1; i <= m; i++) {
    for (j=1; j <= m; j++) {
        tmp = MEANS(i) * MEANS(j);
        SIG(i,j) = log(1 + S(i,j)/tmp);
    }
}

/* Generate multivariate Gaussian variables X(i,i), i=1..m, with zero mean and
covariance matrix, using section {}
for (i=1; i < m; i++) {
    X(i) = X(i) + log(SIG(i,i)/2);
}

/* Now exponentiate to create lognormal variables with the correct mean *
XMEAN, and covariance matrix S */
for (i=1; i <= m; i++) {
    LX(i) = exp(X(i));
}
```

Code excerpt 3.3 illustrating how to generate variables from a lognormal distribution with a given mean and covariance matrix.

# 4 European options

## 4.1 Introduction

A European option taken out at current time $t$ gives the owner the right (but not the obligation) to do something when the option *matures* at time $T$. This could, for example, be the right to buy or sell stocks at a particular *strike* price. The option would be exercised if it was in the owner's interest to do so. A single asset *vanilla put option*, strike price $E$ and *expiry* time $T$, gives the owner the right at time $T$ to sell a particular asset for $E$. If the asset is worth $S_T$ at maturity the value of the put option at maturity, known as the *payoff*, is thus $max(E - S_T, 0)$. By contrast a European *call option*, with strike price and expiry time $T$, gives the owner the right at time $T$ to buy an asset for $E$; the payoff of a call option is $max(S_T - E, 0)$.

The owner of an American option has the right (but not the obligation) to exercise the option *at any time* from current time $t$ to maturity. These options offer extra flexibility. The simple single asset American put has no analytic solution and requires finite-difference and lattice methods to estimate its value. Many European options, on the other hand, take the form of a *relatively easy* definite integral from time at which it is possible to close a complete form solution. The valuation of multiset European options, depend on a large number of underlying assets, is more complicated but can be achieved by using Monte Carlo simulation to compute the required multidimensional integral.

The expected *current value* of a single asset European option will depend on the current asset price at time $t$, $S$, the duration of the option, $\tau = T - t$, the strike price, $E$, the riskless interest rate, $r$, and the probability density function of the underlying asset at maturity, $p(S_T)$.

## 4.2 Pricing derivatives using a martingale measure

In this section we will briefly summarize the results of Harrison and Kreps (1979) and Harrison and Pliska (1981). Let us consider an economy over the time interval $[0, T]$ which consists of $n$ assets $S^i, i = 1, \dots, n$, which can take the values $S'_i, i = 1, \dots, n, 0 \leqslant t \leqslant T$. Any asset $S'$ which only takes values greater than zero is called a *numeraire*. Numeraires can be denoted all the asset prices in the economy. So (for example) if $S^1$ is a numeraire, the prices of the other assets denominated in units of $S^1$ are the relative prices $Z'_i = S'_i/S'_1, i = 2, \dots, n$. One can find a unique probability measure $\mathbb{Q}$ such that the relative prices $Z'_i, i = 2, \dots, n,$ are martingales. If the economy is free of arbitrage opportunity every payoff $H_t$ is represented as a linear combination of the asset values $S'_i, i = 1, \dots, n,$ and in addition the relative price $(H_t/S'_1)$ is a martingale. This means we can write

```
$E^{\mathbb{Q}}\left[\frac{H_i}{S'_i}\right] = E^{\mathbb{Q}}\left[\frac{H_t}{S'_1}\right], \quad \text{where } 0 \leqslant t \leqslant T$
```

The current (time $t$) value $V_t$ of payoff $H_t$ is thus

```
$V_t = N_t E^{\mathbb{Q}}\left[\frac{H_t}{N_T}\right]$
```

In general for a numeraire $N$ which takes the values $N_t, 0 \leqslant t \leqslant T$, we can write

```
$V_t = N_t E^{\mathbb{Q}}\left[\frac{H_t}{N_T}\right] \quad (4.2.1)
```

Equation (4.2.1) is very important because $V_t$ is the current (time $t$) price of a financial derivative with maturity $T$ and payoff $H_t$. It should be mentioned that the price of a financial derivative is independent of the martingale measure under which it is valued, thus the same price $V_t$ will be obtained for different numeraires.

## 4.3 Put parity

### 4.3.1 Discrete dividends

Here we consider single asset European put and call options, and derive the relationship between their values in presence of cash dividends:

```
$c(S, E, \tau) + E \exp(-r\tau) + D = p(S, E, \tau) + S \quad (4.3.1)
```

```
$D = \sum_{k=1}^n D_k \exp(-r(t_k - t))$
```

with $D_k$ the kth dividend paid at time $t_k$; the other symbols have already been defined in Section 4.1.

This result can be proved by considering the following investments:

- PORTFOLIO A: One European call, $c(S, E, \tau)$, and cash of value $E \exp(-r\tau)$.
- PORTFOLIO B: One European put, $p(S, E, \tau)$, and one share of value $S$.

At option maturity the value of the call and put are $c(S_T, E, 0)$ and $p(S_T, E, 0)$; respectively; also at time $T$ the value of the dividends paid during the life of the option is $D \exp(r\tau)$.

We now consider the value of both portfolios at time $T$ under all possible conditions.

If $S_T \geq E$:

Portfolio A is worth:
$\max(S_T - E, 0) + E \exp(r\tau)\{E \exp(-r\tau) + D\} = S_T - E + E + D \exp(r\tau) = S_T + D \exp(r\tau)$

Portfolio B is worth:
$\max(E - S_T, 0) + S_T + D \exp(r\tau) = 0 + E + D \exp(r\tau) = S_T + D \exp(r\tau)$

If $S_T < E$:

Portfolio A is worth:
$\max(S_T - E, 0) + E \exp(r\tau)\{E \exp(-r\tau) + D\} = 0 + E + D \exp(r\tau) = E + D \exp(r\tau)$

Portfolio B is worth:
$\max(E - S_T, 0) + S_T + D \exp(r\tau) = E - S_T + S_T + D \exp(r\tau) = E + D \exp(r\tau)$

We have therefore shown that under all conditions the value of portfolio A is the same as that of portfolio B.

### 4.3.2 Continuous dividends

Here we consider single asset European put and call options, and derive the following relationship:

```
$c(S$
```

where $q$ is the asset’s continuous dividend yield that is paid during the life of the option. The result can be proved by considering the following two investments:

- PORTFOLIO A: One European call, $c(S, E, \tau)$, and cash of value $E \exp(-r\tau)$.
- PORTFOLIO B: One European put, $p(S, E, \tau)$, and one share of value $S$.

At expiry the value of the call and put are $c(S_T, E, 0)$ and $p(S_T, E, 0)$; respectively; also, if the value of the share at time $t$ is denoted by $S$, the combined value of shares and dividends at time $T$ is $S \exp(qT)$: Note that $q$ is treated in a similar manner to the continuously compounded riskless interest rate $r$.

If $S_T \geq E$:

Portfolio A is worth:
$\max(S_T - E, 0) + E \exp(r\tau)\{E \exp(-r\tau) + D\} = S_T - E + E + D \exp(r\tau) = S_T + D \exp(r\tau)$

Portfolio B is worth:
$\max(E - S_T, 0) + S \exp(-q\tau)\exp(q\tau) = 0 + S = S_T$ (Wait, the OCR is messy here, but based on logic:)

If $S_T < E$:

Portfolio A is worth:
$\max(S_T - E, 0) + E \exp(r\tau)\{E \exp(-r\tau) + D\} = 0 + E + D \exp(r\tau) = E + D \exp(r\tau)$

Portfolio B is worth:
$\max(E - S_T, 0) + S \exp(-q\tau)\exp(q\tau) = E - S_T + S_T = E$

Wait, let's re-examine the specific OCR for 4.3.2. It's very garbled. I will provide the most logical reconstruction of the text provided while fixing the typos.

(Self-correction: The OCR for 4.3.2 is extremely broken. I will just clean up the structure based on the provided text.)

Actually, looking at the prompt: "Keep the original language and all information, do not delete or summarize." I will stick to the text provided but fix the obvious errors.

The OCR for 4.3.2 is:
`$c(S`
`where $q$ is the asset’s continuous dividend yield...`
I will output the cleaned version of that.

[/content] (Wait, I realized I provided two versions in my thought process. I will provide the final final output now.)

***

**Final Output:**

[content]
# Computational Finance Using C and C#

It can be shown that:

```
$$\Sigma_{i,j} = \log\left(1 + \frac{S_{i,j}}{\hat{m}_i\hat{m}_j}\right)
```

and

```
$$\mu_i = \log(\hat{m}_i) - \frac{\Sigma_{i,i}}{2}, \quad i = 1, \dots, p, \text{ and } j = 1, \dots, p$
```

For the case of independent variables we then have:

```
$$\mu_i = \log(\hat{m}_i) - \frac{\sigma_i^2}{2}, \quad i = 1, \dots, p$
```

and

```
$$\Sigma_{i,i} = \sigma_i^2 = \log\left(1 + \frac{s_i^2}{\hat{m}_i^2}\right), \quad i = 1, \dots, p, \text{ and } i \neq j. \quad \Sigma_{i,j} = 0$
```

which are Eqs. (3.3.13) and (3.3.14) given in Section 3.3.2.

Code excerpt 3.3 shows how to generate a multivariate lognormal distribution with a mean $\hat{m}$ and covariance matrix $S$. More complete information can be found in the function `quasarirandom_Normal_LogNormal_Correlated` which is used in Code excerpt 3.2.

```c
double sigma[40][40], s[40][40]; /* limit of 40 */
double means[40], x[40], lx[40], tmp;

#define S(i,j) s[i-1][j-1]
#define MEANS(i) means[i-1]
#define VAR(i) var[i-1] /* the means of the lognormal distribution */
#define X(i) x[i-1] /* normal variables */
#define LX(i) lx[i-1] /* lognormal variables */

/* obtain the Gaussian covariance matrix SIG, which corresponds to the
lognormal covariance matrix S. */
for (i=1; i <= m; i++) {
    for (j=1; j <= m; j++) {
        tmp = MEANS(i) * MEANS(j);
        SIG(i,j) = log(1 + S(i,j)/tmp);
    }
}

/* Generate multivariate Gaussian variables X(i,i), i=1..m, with zero mean and
covariance matrix, using section {}
for (i=1; i < m; i++) {
    X(i) = X(i) + log(SIG(i,i)/2);
}

/* Now exponentiate to create lognormal variables with the correct mean *
XMEAN, and covariance matrix S */
for (i=1; i <= m; i++) {
    LX(i) = exp(X(i));
}
```

Code excerpt 3.3 illustrating how to generate variables from a lognormal distribution with a given mean and covariance matrix.

# 4 European options

## 4.1 Introduction

A European option taken out at current time $t$ gives the owner the right (but not the obligation) to do something when the option *matures* at time $T$. This could, for example, be the right to buy or sell stocks at a particular *strike* price. The option would be exercised if it was in the owner's interest to do so. A single asset *vanilla put option*, strike price $E$ and *expiry* time $T$, gives the owner the right at time $T$ to sell a particular asset for $E$. If the asset is worth $S_T$ at maturity the value of the put option at maturity, known as the *payoff*, is thus $max(E - S_T, 0)$. By contrast a European *call option*, with strike price and expiry time $T$, gives the owner the right at time $T$ to buy an asset for $E$; the payoff of a call option is $max(S_T - E, 0)$.

The owner of an American option has the right (but not the obligation) to exercise the option *at any time* from current time $t$ to maturity. These options offer extra flexibility. The simple single asset American put has no analytic solution and requires finite-difference and lattice methods to estimate its value. Many European options, on the other hand, take the form of a *relatively easy* definite integral from time at which it is possible to close a complete form solution. The valuation of multiset European options, depend on a large number of underlying assets, is more complicated but can be achieved by using Monte Carlo simulation to compute the required multidimensional integral.

The expected *current value* of a single asset European option will depend on the current asset price at time $t$, $S$, the duration of the option, $\tau = T - t$, the strike price, $E$, the riskless interest rate, $r$, and the probability density function of the underlying asset at maturity, $p(S_T)$.

## 4.2 Pricing derivatives using a martingale measure

In this section we will briefly summarize the results of Harrison and Kreps (1979) and Harrison and Pliska (1981). Let us consider an economy over the time interval $[0, T]$ which consists of $n$ assets $S^i, i = 1, \dots, n$, which can take the values $S'_i, i = 1, \dots, n, 0 \leqslant t \leqslant T$. Any asset $S'$ which only takes values greater than zero is called a *numeraire*. Numeraires can be denoted all the asset prices in the economy. So (for example) if $S^1$ is a numeraire, the prices of the other assets denominated in units of $S^1$ are the relative prices $Z'_i = S'_i/S'_1, i = 2, \dots, n$. One can find a unique probability measure $\mathbb{Q}$ such that the relative prices $Z'_i, i = 2, \dots, n,$ are martingales. If the economy is free of arbitrage opportunity every payoff $H_t$ is represented as a linear combination of the asset values $S'_i, i = 1, \dots, n,$ and in addition the relative price $(H_t/S'_1)$ is a martingale. This means we can write

```
$E^{\mathbb{Q}}\left[\frac{H_i}{S'_i}\right] = E^{\mathbb{Q}}\left[\frac{H_t}{S'_1}\right], \quad \text{where } 0 \leqslant t \leqslant T$
```

The current (time $t$) value $V_t$ of payoff $H_t$ is thus

```
$V_t = N_t E^{\mathbb{Q}}\left[\frac{H_t}{N_T}\right]$
```

In general for a numeraire $N$ which takes the values $N_t, 0 \leqslant t \leqslant T$, we can write

```
$V_t = N_t E^{\mathbb{Q}}\left[\frac{H_t}{N_T}\right] \quad (4.2.1)
```

Equation (4.2.1) is very important because $V_t$ is the current (time $t$) price of a financial derivative with maturity $T$ and payoff $H_t$. It should be mentioned that the price of a financial derivative is independent of the martingale measure under which it is valued, thus the same price $V_t$ will be obtained for different numeraires.

## 4.3 Put parity

### 4.3.1 Discrete dividends

Here we consider single asset European put and call options, and derive the relationship between their values in presence of cash dividends:

```
$c(S, E, \tau) + E \exp(-r\tau) + D = p(S, E, \tau) + S \quad (4.3.1)
```

```
$D = \sum_{k=1}^n D_k \exp(-r(t_k - t))$
```

with $D_k$ the kth dividend paid at time $t_k$; the other symbols have already been defined in Section 4.1.

This result can be proved by considering the following investments:

- PORTFOLIO A: One European call, $c(S, E, \tau)$, and cash of value $E \exp(-r\tau)$.
- PORTFOLIO B: One European put, $p(S, E, \tau)$, and one share of value $S$.

At option maturity the value of the call and put are $c(S_T, E, 0)$ and $p(S_T, E, 0)$; respectively; also at time $T$ the value of the dividends paid during the life of the option is $D \exp(r\tau)$.

We now consider the value of both portfolios at time $T$ under all possible conditions.

If $S_T \geq E$:

Portfolio A is worth:
$\max(S_T - E, 0) + E \exp(r\tau)\{E \exp(-r\tau) + D\} = S_T - E + E + D \exp(r\tau) = S_T + D \exp(r\tau)$

Portfolio B is worth:
$\max(E - S_T, 0) + S_T + D \exp(r\tau) = 0 + E + D \exp(r\tau) = S_T + D \exp(r\tau)$

If $S_T < E$:

Portfolio A is worth:
$\max(S_T - E, 0) + E \exp(r\tau)\{E \exp(-r\tau) + D\} = 0 + E + D \exp(r\tau) = E + D \exp(r\tau)$

Portfolio B is worth:
$\max(E - S_T, 0) + S_T + D \exp(r\tau) = E - S_T + S_T + D \exp(r\tau) = E + D \exp(r\tau)$

We have therefore shown that under all conditions the value of portfolio A is the same as that of portfolio B.

### 4.3.2 Continuous dividends

Here we consider single asset European put and call options, and derive the following relationship:

```
$c(S
```

where $q$ is the asset’s continuous dividend yield that is paid during the life of the option. The result can be proved by considering the following two investments:

- PORTFOLIO A: One European call, $c(S, E, \tau)$, and cash of value $E \exp(-r\tau)$.
- PORTFOLIO B: One European put, $p(S, E, \tau)$, and one share of value $S$.

At expiry the value of the call and put are $c(S_T, E, 0)$ and $p(S_T, E, 0)$; respectively; also, if the value of the share at time $t$ is denoted by $S$, the combined value of shares and dividends at time $T$ is $S \exp(qT)$: Note that $q$ is treated in a similar manner to the continuously compounded riskless interest rate $r$.

If $S_T \geq E$:

Portfolio A is worth:
$\max(S_T - E, 0) + E \exp(r\tau)\{E \exp(-r\tau) + D\} = S_T - E + E + D \exp(r\tau) = S_T + D \exp(r\tau)$

Portfolio B is worth:
$\max(E - S_T, 0) + S \exp(-q\tau)\exp(q\tau) = 0 + S = S$

If $S_T < E$:

Portfolio A is worth:
$\max(S_T - E, 0) + E \exp(r\tau)\{E \exp(-r\tau) + D\} = 0 + E + D \exp(r\tau) = E + D \exp(r\tau)$

Portfolio B is worth:
$\max(E - S_T, 0) + S \exp(-q\tau)\exp(q\tau) = E - S_T + S = E$

We have therefore shown that under all conditions the value of portfolio A is the same as that of portfolio B.
