
## 2.1.1 The properties of Brownian motion

In formal terms a process $W = (W_t; t \geqslant 0)$ is (one-dimensional) Brownian motion if:

- (i) $W_t$ is continuous, and $W_0 = 0$,
- (ii) $W_t \sim N(0, t)$,
- (iii) the increment $dW_t = W_{t+dr} - W_t$ is normally distributed as $dW_t \sim N(0, dt)$, so $E[dW_t] = 0$ and $Var[dW_t] = dt$. The increment $dW_t$ is independent of the history of the process up to time $t$.

From (iii) we can further state that since increments $dW_t$ are independent of past values $W_t$, a Brownian process is also a *Markov* process. In addition we will now show that a Brownian process is also a *martingale* process.

In a martingale $P_t, t \geqslant 0$, the conditional expectation $E[P_{t+dr}|\mathcal{F}_t] = P_t$, where $\mathcal{F}_t$ is called the *filtration* of the process and contains the information learned by observing the process up to time $t$. For Brownian motion we have

```
$E[W_{t+dr}|\mathcal{F}_t] = E[(W_{t+dr} - W_t) + W_t|\mathcal{F}_t] = E[W_{t+dr} - W_t] + W_t = E[dW_t] + W_t$
```

where we used the fact that $E[dW_t] = 0$. Since $E[W_{t+dr}|\mathcal{F}_t] = W_t$ the Brownian motion $W$ is a martingale process.

Using property (iii) we can also derive an expression for the covariance of Brownian motion. The independent increment requirement means that for the $n$ times $0 \leqslant t_0 < t_1 < t_2 \dots \leqslant t_n$ the random variables $W_{t_1} - W_{t_0}, W_{t_2} - W_{t_1}, \dots, W_{t_n} - W_{t_{n-1}}$ are independent. So

```
$Cov[W_{t_i} - W_{t_{i-1}}, W_{t_j} - W_{t_{j-1}}] = 0, \quad i \neq j \quad (2.1.1)$
```

We will show that $W_{t_0} = 0$, and assuming $t \geqslant s$ we have

```
$Cov[W_s - W_{t_0}, W_t - W_{t_0}] = Cov[W_s, W_t] = Cov[W_s, W_s + (W_t - W_s)]$
```

From Appendix C.3.2 we have

```
$Cov[W_s, W_s + (W_t - W_s)] = Cov[W_s, W_s] + Cov[W_s, W_t - W_s] = Var[W_s] + Cov[W_s, W_t - W_s]$
```

Therefore

Now

```
$Cov[W_s, W_t - W_s] = Cov[W_s - W_{t_0}, W_t - W_{t_0}] = 0$
```

where we used Eq. (2.1.1) with $n=2, t_1=s$ and $t_2=t$.

## Introduction to stochastic processes

We thus obtain

Cov[W_s, W_t] = s

So
Cov[W_s, W_t] = s \wedge t (2.1.2)

We will now consider the Brownian increments over the time interval dt in more detail. Let us first define the process X such that:

```
dX_t = dW_t (2.1.3)
```

where dW_t is a random variable drawn from a normal distribution with mean zero and variance dt, we denote as $dW_t \sim N(0, dt)$. Equation (2.1.3) can also be written in the equivalent form:

```
dX_t = \sqrt{dt} dZ (2.1.4)
```

where dZ is a random variable drawn from a standard normal distribution (that is a normal distribution with mean zero and unit variance). Equations (2.1.3) and (2.1.4) give the incremental change in the value of X over the time interval dt for standard Brownian motion.

We shall now generalize these equations by introducing the extra (volatility) parameter sigma which controls the variance of the process. We now have:

```
dX_t = \sigma dW_t (2.1.5)
```

where $dW_t \sim N(0, dt)$ and $dX_t \sim N(0, \sigma^2 dt)$. Equation (2.1.5) can also be written in the equivalent form:

```
dX_t = \sigma\sqrt{dt} dZ, dZ \sim N(0, 1) (2.1.6)
```

or equivalently
$dX_t = \sqrt{\sigma^2 dt} dZ, dZ \sim N(0, 0)$ (2.1.7)

We are now in a position to provide a mathematical description of the movement of the pollen grains. We will start by assuming that the container of water is perfectly level. This will ensure that there is no drift of the pollen grains in any direction. Let us denote the position of a particular grain at time $t$ by $X_t$, and set the position at $t=0, X_0$, to zero. The statistical distribution of the grain's position, $X_t$, at some later time $T$, can be found as follows:

Let us divide the time $T$ into $n$ intervals $dt = T/n$. Since the position of the particle changes by the amount $dX_t = \sigma\sqrt{dt} dZ$ over the $i^{th}$ time interval, the final position $X_T$ is given by:

```
X_T = \sum_{i=1}^n (\sigma\sqrt{dt} dZ_i) = \sigma\sqrt{dt} \sum_{i=1}^n dZ_i
```

Since $Z_i \sim N(0,1)$, by the Law of Large Numbers (see Appendix C), we have that the expected value of position $X_T$ is:

```
E[X_T] = \sigma\sqrt{dt} \sum_{i=1}^n dZ_i = 0
```

The variance of the position $X_T$:

```
Var[X_T] = Var[\sigma\sqrt{dt} \sum_{i=1}^n dZ_i] = \sigma^2 dt \sum_{i=1}^n Var[dZ_i] (2.1.8)
```

Since all the $dZ_i$ variables are IID $N(0,1)$ we have $Var[dZ_i] = 1$ and $Var[\sum_{i=1}^n X_i] = \sum_{i=1}^n Var[X_i]$ (see Appendix C). Thus

```
Var[X_T] = \sigma^2 dt \sum_{i=1}^n Var[d_i] = \sigma^2 dt \sum_{i=1}^n 1 (2.1.9)
```

which gives:

```
Var[X_T] = \sigma^2 T (2.1.10)
```

So, at time $T$, the position of the pollen grain $X_T$ is distributed as $X_T \sim N(0, \sigma^2)$.

If the water container is not perfectly level the pollen grains will exhibit drift in a particular direction. We can modify Eq. (2.1.5) to take this account as:

```
dX_T = \mu dt + \sigma\sqrt{dt} dZ_i, dZ_i \sim N(0,1) (2.1.11)
```

or equivalently
$dX_T = \mu dt + \sigma dW_t, dW_t \sim N(0, dt)$ (2.1.12)

where we have included the constant drift $\mu$. We proceed in a similar manner to that for the case of zero Brownian motion we have:

```
X_T = \sum_{i=1}^n (\mu dt + \sigma\sqrt{dt} dZ_i) = \mu dt + \sum_{i=1}^n \sigma\sqrt{dt} dZ_i = \mu dt + \sigma\sqrt{dt} \sum_{i=1}^n dZ_i
```

which gives

$E[X_T] = E[\mu dt + \sigma\sqrt{dt} \sum_{i=1}^n dZ_i]$

```
E[X_T] = \mu dt + \sigma\sqrt{dt} E[\sum_{i=1}^n dZ_i] = \mu dt
```

The variance of the position $X_T$ is:

```
Var[X_T] = Var \left[ \mu T + \sigma\sqrt{dt} \sum_{i=1}^n dZ_i \right] = Var \left[ \sigma\sqrt{dt} \sum_{i=1}^n dZ_i \right]
```

Here we have used the fact (see Appendix C.3.1) $Var[a+bX]=b^2Var[X]$, where $a=\mu T$, and $b=1$. From Equs. (2.1.9) and (2.1.10) we have:

```
Var[X_T] = Var \left[ \sigma\sqrt{dt} \sum_{i=1}^n dZ_i \right] = \sigma^2 T.
```

So, at time $T$, the position of the pollen grain $X_T$ is distributed $\sim N(\mu T, \sigma^2)$.

We have shown that when we vary the drift of a Brownian motion, its volatility remains unchanged. This is a very important property and (as we will see later) is used extensively in the theory of derivative pricing.

## 2.2 A Brownian model of asset price movements

In the previous section we showed how Brownian motion can be used to describe the random motion of small particles suspended in a liquid. The first attempt at using Brownian motion to describe financial asset movements was provided by Bachelier (1900). This, however, only had limited success because the significance of an absolute change in asset price depends on the original price. For example, a $\pounds1$ increase in the value of a share originally $\pounds10$ is much more significant than a $\pounds1$ increase in the value of a share originally $\pounds100$. It is for reason that asset price movements are generally described in terms of relative or percentage changes. For example, if the $\pounds1.10$ increases by 11 percent and the $\pounds100$ share increases in value by $\pounds10$, both of these changes have the same significance, and correspond to a 10 percent increase in value. The idea of relative price changes in the value of a share at time $t$. The return, $R_t$, is defined as follows:

```
R_t = \frac{S_{t+dt} - S_t}{S_t} = \frac{dS_t}{S_t} (2.2.1)
```
