266

DATA SCIENCE

# 14.1.2 AR(p) Process

To efficiently forecast the future of a finite series of random variables we need to admit that these variables are somehow dependent from each other. If it is not the case, the series is purely random and not predictable. This section introduces autoregressive models:

Formally, the autoregressive process of order p, denoted as AR(p) is defined as:

```
$X_t = c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t, \quad (14.1)$
```

where $\phi_1, \dots, \phi_p$ are the parameters of the model, $c$ is a constant and $\{\epsilon_i\}$ the white noise, i.e. $\epsilon_i \sim N(0, \sigma_i^2)$. $E[\epsilon_i] = 0, s < t$. Its expectation is $E[X_t] = c + \sum_{i=1}^p \phi_i E[X_{t-i}]$. If $|\phi_i| < 1, \forall i \in [1]$, the process 14.1 is wide-stationary and $E[X_{t-i}]$ is identical for all values of $t$. Denoting $E[X_t] = \mu, \mu = c + \mu \sum_{i=1}^p \phi_i$, i.e.

```
$$\mu = \frac{c}{1 - \sum_{i=1}^p \phi_i} \quad (14.2)$
```

The variance of (14.1) solves $Var[X_t] = \sum_{i=1}^p \phi_i^2 Var[X_{t-i}] + Var[\epsilon_i]$. If the process $X_t$ is homoskedastic, i.e. $\forall t: Var[X_t] = \sigma^2$,

```
$$\sigma^2 = \frac{\sigma_\epsilon^2}{1 - \sum_{i=1}^p \phi_i^2} \quad (14.3)$
```

The autocovariance $E[X_t X_{t-n}]$ with $t > n$ solves:

```
$$E[X_t X_{t-n}] = E[(c + \sum_{i=1}^p \phi_i X_{t-i} + \epsilon_t)(c + \sum_{i=1}^p \phi_i X_{t-i-n} + \epsilon_{t-n})]$ \n$= c^2 + c \sum_{i=1}^p \phi_i E[X_{t-i}] + c \sum_{i=1}^p \phi_i E[X_{t-i-n}] + (\sum_{i=1}^p \phi_i E[\epsilon_{t-i}])(\sum_{i=1}^p \phi_i E[\epsilon_{t-i-n}]) \quad (14.4)$
```

If $X_t$ is homoskedastic with mean $\mu$:

```
$$E[X_t X_{t-n}] == (c + \mu \sum_{i=1}^p \phi_i)^2.$
```

# 14.1.2.1 Simulation

The autoregressive model $X_t = 0.82X_{t-1} + \epsilon_t$ can be simulated as

\of {y+0.82+x} \eps