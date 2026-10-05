
# Solution

The center can be modeled as an M/M/20. The arrival rate $\lambda = \frac{30}{60} = 0.5$ per minute and the service rate of $\mu = \frac{1}{10}$ per minute

The traffic intensity $\rho = \frac{\lambda}{k\mu} = \frac{0.25}{20(1/10)}$

# 2.18.5 M/M/$\infty$ Queueing System

This is case in which we have an infinite number of servers so that an arriving customer can always find a server and not queue. This model can be used to study the effect of delay in large systems. The state transition diagram for the M/M/$\infty$ system is shown in Figure 2.28. Like we did before, we assume a Poisson arrival at rate $\lambda$ and exponentially distributed service times with mean $1/\mu$. We adopt a birth-and-death process with parameters

```
$\lambda_n = \lambda, \quad n=0,1,2,\dots \quad (2.176)
```

```
$\mu_n = n\mu, \quad n=0,1,2,\dots \quad (2.177)
```

![](img/d3b56042c756fbcc011ff06f1b9f53f0_120_0.png)

FIGURE 2.28 State transition diagram for M/M/$\infty$ queueing system.

The balance equation is

```
$\lambda p_n = (n+1)\mu p_{n+1} \quad (2.178)
```

which can be solved to give

```
$p_n = \frac{\rho^n}{n!} p_0, \quad n=0,1,2,\dots \quad (2.179)
```

MATHEMATICAL FOUNDATIONS FOR COMPUTER NETWORKS • 97

where $\rho = \lambda / \mu$. Applying the normalization condition $\sum_{n=0}^{\infty} p_n = 1$ gives

```
$p_0 = e^{-\rho}$ (2.180)
```

The utilization of the server

```
$U = 1 - p_0 = 1 - e^{-\rho}$ (2.181)
```

The average number of customers in the system

```
$E[N] = \sum_{n=0}^{\infty} np_n = \rho$ (2.182)
```

We apply Little's theorem in finding the average time spent in the system,

```
$E[T] = \frac{E[N]}{\lambda}$ (2.183)
```

Also,

```
$E[N_q] = 0 = E[W_q]$ (2.184)
```

that is, the average waiting time and the average number of customers waiting in the queue are both zero.

# 2.19 M/G/1 QUEUEING SYSTEM

The M/G/1 queuing system, the simplest non-Markovian system, is shown in Figure 2.29. We analyze assuming that it is in the steady state. An M/G/1 system assumes a FIFO service discipline, an infinite queue size, a Poisson input process (with arrival rate $\lambda$), general service times (with arbitrary but known distribution function $H$, mean $\tau = 1/\mu$, and variance $\sigma^2$), and one server.

![](img/d3b56042c756fbcc011ff06f1b9f53f0_121_0.png)

FIGURE 2.29 The M/G/1 queue system has a general service time distribution.

In order to find the waiting time of the M/G/1 model, we apply the method of $z$-transform or generating functions.

The probability of having $k$ arrivals during the service time is

```
$p_k = \int_{0}^{\infty} p(k)dH(t) = \int_{0}^{\infty} \frac{(\lambda t)^k}{k!} e^{-\lambda t} dH(t) \quad (2.185)$
```

$H(t)$ is the service time distribution.

Let $N$ be the number of customers present in the system and $Q$ be the number of customers in the queue. The probability that an arriving customer finds $j$ other customers present be

```
$\Pi_j = \text{Prob}(N=j), \quad j=0, 1, 2, ... \quad (2.186)$
```

It can be shown using the theorem of total probability and the equilibrium imbedded-Markov-chain that

```
$\Pi_j = p_j\Pi_0 + \sum_{i=1}^{j+1} p_{j-i+1}\Pi_i, \quad j=0, 1, 2, ... \quad (2.187)$
```

We define the probability-generating functions

```
$g(z) = \sum_{j=0}^{\infty} \Pi_j z^j \quad (2.188a)$
```

```
$h(z) = \sum_{j=0}^{\infty} p_j z^j \quad (2.188b)$
```

Substituting Equation (2.188a) into Equation (2.187) results in

```
$g(z) = \frac{(z-1)h(z)}{z-h(z)}\Pi_0 \quad (2.189)$
```

The normalization equation

```
$\sum_{j=0}^{\infty} \Pi_j = 1 \quad (2.190)$
```

implies that g(1) = 1. With a single application of L'Hopital's rule, we find

$$\Pi_0 = 1 - \rho$$ (2.191)

where $\rho = \lambda / \mu = \lambda\tau$. If we define $\eta(s)$ as the Laplace-Stieltjes transform of the service-time distribution function H(t),

$$\eta(s) = \int_0^{\infty} e^{-st} dH(t)$$ (2.192)

Substitution of Equation (2.185) into Equation (2.188b) yields

$$$h(z) = \eta(\lambda - \lambda z)$$ (2.193)

and substitution of Equation (2.191) and Equation (2.193) leads to (2.189) leads to

$$g(z) = \frac{(z-1)\eta(\lambda - \lambda z)}{z - \eta(\lambda - \lambda z)} (1 - \rho)$$ (2.194)

Differentiating this and applying the LHopital rule twice, we obtain

$$$g'(1) = \frac{\rho^2}{2(1 - \rho)} (1 + \frac{\sigma^2}{\tau})$$ (2.195)

The mean values of the number of customers in the system and queue are given by

$$$E(N) = \sum_{j=0}^{\infty} j\Pi_j = g'(1)$$ (2.196a)

$$$E(Q) = E(N) - \rho$$ (2.196b)

By applying Little's theorem, the mean value of response time is

$$$E(T) = \frac{E(N)}{\lambda} \frac{\rho\tau}{2(1 - \rho)} (1 + \frac{\sigma^2}{\tau})$$ (2.197)

$$$E(W) + \tau$$

Thus, we obtain the mean waiting time as

$E(W) = \frac{E(Q)}{\lambda} \frac{\rho\tau}{2(1 - \rho)} (1 + \frac{\sigma^2}{\tau})$ (2.198)

where $\rho = \lambda / \mu = \lambda\tau$. This is known as the Pollaczek-Khintchine formula after Russian mathematicians Pollaczek and Khintchine who derived it independently in 1930 and 1932 respectively. The average number of customers $E(N_q)$ in the queue is

$$$E(N_q) = \lambda E(W) = \frac{\rho^2}{2(1-\rho)} (1+\frac{\sigma^2}{\tau})$$ (2.199)

The average response time is

$$$E(T) = E(W) + \tau = \frac{\rho\tau}{2(1-\rho)} (1+\frac{\sigma^2}{\tau})$$ (2.200)

and the mean number of customers in the system is

$$$E(N) = \lambda E(T) = E_q + \rho$$ (2.201)

or

$$$E(N) = \frac{\rho^2}{2(1-\rho)} (1+\frac{\sigma^2}{\tau})$$ (2.202)

We may now obtain the mean waiting time for M/M/1 and M/D/1 models as special cases of the M/G/1 model.

For the M/M/1 queue model, a special case of the M/G/1 model, the service times follow an exponential distribution with mean $\tau = 1/\mu$ and variance $\sigma^2$. That means,

$H(t) = \text{Prob}[X \le t] = 1 - e^{-\mu t}$ (2.203)

Hence,

$\sigma^2 = \tau^2$ (2.204)

MATHEMATICAL FOUNDATIONS FOR COMPUTER NETWORKS • 101

Substituting this in Pollaczek-Khintchine formula in Equation (2.198) gives the mean waiting time as

$$$E(W) = \frac{\rho}{1-\rho}$$ (2.205)

The M/D/1 queue is another special case of the M/G/1 model. For this model, the service times are constant with the mean value $\tau=1/\mu$ and variance $\sigma=0$. Thus, Pollaczek-Khintchine formula in Equation (2.198) gives the mean waiting time as

$$$E(W) = \frac{\rho}{2(1-\rho)}$$ (2.206)

It should be noted from Equations (2.205) and (2.206) that the waiting time for the M/D/1 model is one-half that for M/M/1 model, that is,

$$$E(W)_{M/D/1} = \frac{\rho}{2(1-\rho)} = \frac{1}{2}E(W)_{M/M/1}$$$ (2.207)

# Example 2.12

In the M/G/1 system, prove that:

- 1. Prob (the system is empty) = $1-\rho$
- 2. Average length of time between busy periods = $1/\lambda$
- 3. Average number of customers served in a busy period = $\frac{1}{1-\rho}$ where $\rho=\lambda\bar{X}$ and $\bar{X}$ is the mean service time.

# Solution

- 1. Let $p_b$ = Prob. that the system is busy. Then $p_b$ is the fraction of time the server is busy. At a steady state,

$$
$arrival rate = departure rate \n \lambda = p_b\mu$$
$$

or

$$$p_b = \frac{\lambda}{\mu} = \rho$$

The Prob. that the system is empty is

$$$p_e = 1 - p_b = 1 - \rho$$

- 2. The server is busy only when there are arrivals. The average length of time between busy periods = average interarrival rate = $1/\lambda$. Alternatively, we recall if $t$ is the interarrival time,

$$$f(t) = \lambda e^{-\lambda t}$$$

Hence $E(t) = 1/\lambda$.

- 3. Let $E(B)$ = average busy period, $E(I)$ = average idle period. From part (1),

$$$p_b = \rho = \frac{E(B)}{E(B) + E(I)}$$$$$

From part (2),
$E(I)$ = average length of time between busy periods = $1/\lambda$$

Hence,

$$$\rho = \frac{E(B)}{E(B) + \lambda}$$$$

Solving for $E(B)$ yields

$$$E(B) = \frac{\rho}{\lambda(1 - \rho)} = \frac{\overline{X}}{1 - \rho}$$$$

as required.

The average number of customers served in a busy period is

$$$N_b = \frac{\text{Average length of busy period}}{\text{Average service time}}$$$$
