
# MATHEMATICAL FOUNDATIONS FOR COMPUTER NETWORKS * 89

```
$(\lambda + \mu m)p_n = \mu p_{n+1} + \lambda p_{n-m}$
```

We now apply the method of $z$-transforms to solve for $p_n$. We define the generating function

```
$G(z) = \sum_{t=0}^{\infty} p_t z^t$
```

Multiplying the balance equation for state $n$ by $z^n$ and summing, we obtain

```
$(\lambda + \mu m)p_n z^n = \sum_{n=1}^{\infty} \mu p_{n+1} z^n + \sum_{n=1}^{\infty} \lambda p_{n-m} z^n$
```

Simplifying yields

```
$G(z) = \frac{\mu m(1-z)p_0}{\mu + \lambda z^{m-1} - z(\lambda + \mu m)}$
```

The value of $p_0$ is obtained using the condition $G(1) = 1$.

```
$p_0 = \frac{\lambda m}{\mu} = 1 - \rho, \quad \rho = \frac{\lambda m}{\mu}$
```

## 2.18.2 M/M'/1 (Bulk Service) System

This kind of model is used to analyze systems that wait until a certain message size is reached before releasing the data for transmission. We assume that customers are served in bulk of size $m$, that is, customers served at a time. At equilibrium, the balance equations are:

```
$(\lambda + \mu m)p_n = \lambda p_{n-1} + \mu p_{n+m}, \quad n \ge 1$
```

```
$\lambda p_0 = \mu p_m + \mu p_{m-1} + \dots + \mu p_1$
```

Equation (2.156a) can be written in terms of an operator $D$ so

```
$[\mu D^{m+1} - (\lambda + \mu D)D + \lambda]p_n = 0, \quad n \ge 0$
```

If the roots of the characteristic equation are $r_1, r_2, \dots, r_{m+1}$, then

```
$p_n = \sum_{i=1}^{n+1} C_i r_i^n, \quad n \geq 0 \quad (2.158)$
```

Using the fact that $\sum p_n = 1$, we obtain (corrected from OCR error)

```
$p_n = (1-r_0)r_0^n, \quad n \geq 0, 0 < r_0 < 1 \quad (2.159)$
```

where $r_0$ is the one and only one root of Equation (2.157) that is less than one. Comparing this with Equation (2.138) shows the similarity between this solution and that of M/M/1. Hence,

```
$E[N] = \frac{r_0}{1-r_0} \quad (2.160)$
```

```
$E[T] = \frac{r_0}{\lambda(1-r_0)} \quad (2.161)$
```

## 2.18.3 M/M/1/k Queueing System

In this case, we have situations similar to M/M/1, but the number of customers that is queued is limited to $k$. In other words, this is a system with limited waiting space. If an arriving customer finds the queue full, it is lost or blocked, as shown in Figure 2.24. Hence,

```
$\lambda_n = \begin{cases} \lambda, & \text{if } 0 \leq n < k \\ 0, & n \geq k \end{cases} \quad (2.162)$
```

```
$\mu_n = \mu, \quad 0 \leq n \leq k \quad (2.163)$
```

![](img/d3b56042c756fbcc011ff06f1b9f53f0_114_0.png)

FIGURE 2.24 M/M/1/k queueing system. The state transition diagram is given in Figure 2.25. The balance equations are:

```
$\lambda p_0 = \mu p_1$
$\lambda p_n + \mu p_n = \lambda p_{n-1} + \mu p_{n+1}, \quad 1 \leq n \leq k-1 \quad (2.164)$
$\lambda p_{k-1} = \mu p_k$
```

![](img/d3b56042c756fbcc011ff06f1b9f53f0_115_0.png)

The probability of zero customers in the system, $p_0$, can be obtained from

```
p_0 = \frac{1}{1 + \sum_{n=1}^{k} (\frac{\lambda}{\mu})^n}$
```

The sum is a finite geometric series which can be obtained by


$\sum_{n=1}^{k} (\frac{\lambda}{\mu})^n = \frac{(\frac{\lambda}{\mu})^k}{1 - (\frac{\lambda}{\mu})}$
```

Now, we get

```
$p_0 = \frac{1-\rho}{1-\rho^{k+1}}$
```

If we define $\rho = \lambda / \mu$, we solve these equations recursively and apply the normalization condition. The steady-state probabilities are given by

```
$p_n = \begin{cases} \frac{(1-\rho)\rho^n}{1-\rho^{k+1}}, & 0 \leq n \leq k \\ 0, & n > k \end{cases} \quad (2.165)$
```

The utilization of the server is given by

```
$U = 1 - p_0 = \frac{\rho(1-\rho^k)}{1-\rho^{k+1}} \quad (2.166)$
```

The average number of customers in the system is

```
$E(N) = \sum_{n=0}^{k} np_n = \frac{\rho}{1-\rho} \left[ \frac{1-\rho^{k+1}}{1-\rho} - k\rho^k \right] \quad (2.167)$
```

Since there can be blocking in this system, the blocking probability is

```
$P_B = p_k = \frac{(1-\rho)\rho^k}{1-\rho^{k+1}} \quad (2.168)$
```

This is the probability that an arriving customer is blocked, that is, because the queue is full.

## 2.10 A system consists of a packet buffer and a communication server and cannot hold more than three packets. Arrivals are Poisson with a rate of 30 packets/ms and the server follows exponential distribution with a mean of 60 packets/ms. Determine the blocking probability of the system.

### Solution

This is an M/M/1/k system with $k=4$.

```
$\rho = \lambda / \mu = 30 / 60 = 0.5$
```

The probability is

```
$P_B = \frac{(1-0.5)0.5^4}{1-0.5^5} = 0.0323$
```

which is about 3 percent.

## 2.18.4 M/M/k Queuing System

This is the case where we have $k$ servers, as shown in Figure 2.26. Upon arrival, a customer is served by any available server. The arriving customer is queued when all servers are found busy, that is, no customer is queued until the number of arrivals exceeds $k$. The state transition diagram is shown in Figure 2.27. The system can be modeled as a birth-and-death process with

```
$\lambda_n = \lambda \quad (2.169)$
```

```
$\mu_n = \begin{cases} n\mu, & 0 \leq n \leq k \\ k\mu, & n \geq k \end{cases}$
```

![](img/d3b56042c756fbcc011ff06f1b9f53f0_117_0.png)

**FIGURE 2.26** The M/M/k queue.

![](img/d3b56042c756fbcc011ff06f1b9f53f0_117_1.png)

**FIGURE 2.27** State transition diagram for M/M/k system.

At a steady state,

```
$p_{n-1} = n\mu p_n, \quad n \leq k \quad (2.170a)$
```

```
$p_{n-1} = k\mu p_n, \quad n > k \quad (2.170b)$
```

From these, we obtain the state probabilities as

```
$p_n = \begin{cases} p_0\frac{(k\rho)^n}{n!}, & n \leq k \\ p_0\frac{(k\rho)^k}{k!} \rho^{n-k}, & n > k \end{cases}
```

where $\rho = \lambda / (k\mu)$. The value of $p_0$ is given

```
$p_0 = \left[ \sum_{n=0}^{k} \frac{(k\rho)^n}{n!} + \frac{(k\rho)^k}{k!(1-\rho)} \right]^{-1} \quad (2.171)$
```

The utilization of the server is given by

```
$U = \rho \quad (2.172)$
```

The average number of customers in the system is

```
$E(N) = \sum_{n=0}^{\infty} np_n = k\rho \left[ \frac{1}{1-\rho} - \frac{k(k\rho)^k}{k!(1-\rho)^2} \right] \quad (2.173)$
```

The average waiting time in the system is

```
$E(W) = \frac{E(N)}{\lambda} \quad (2.174)$
```

The probability that an arriving customer is blocked is

```
$P(B) = 1 - \frac{1-\rho}{\rho} \left[ 1 - \frac{(k\rho)^k}{k!(1-\rho)} \right] \quad (2.175)$
```
