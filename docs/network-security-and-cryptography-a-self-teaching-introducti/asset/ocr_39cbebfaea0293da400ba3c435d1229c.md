Similarly, for queue 2

$p_j = (1 - ho_2)\rho_2^j, \quad \rho_2 = \frac{\lambda}{\mu_2} \quad (2.219)

A simple product solution for this two-node network is

$p_{i,j} = (1 - \rho_i)(1 - \rho_j)\rho_i^i\rho_j^j, \quad \rho_i = \frac{\lambda}{\mu_i}, \quad \rho_j = \frac{\lambda}{\mu_j} \quad (2.220)

The average number of customers in the system is given by

$E(N) = \sum_{i,j} (i+j)p_{i,j} = \sum_{i} \frac{\lambda}{\mu_i}(1 - \frac{\lambda}{\mu_i}) + \sum_{j} \frac{\lambda}{\mu_j}(1 - \frac{\lambda}{\mu_j}) \quad (2.221)\n\= \frac{\lambda}{\mu_1 - \lambda} + \frac{\lambda}{\mu_2 - \lambda}$

From this we find the average time a customer spends in the system is given by

$E(W) = \frac{E(N)}{\mu_1 - \lambda} + \frac{1}{\mu_2 - \lambda} \quad (2.222)

# 2.2.1.2 Queueing System with Splitting

Splitting a Poisson distribution is shown in Figure 2.33. Suppose that a proportion $p$ of the departures from an M/M/1 system (or an M/M/k or an M/M/$\infty$) joined a second system, and the remainder depart altogether. The input to the second system is a Poisson distribution with rate $p\lambda$. Let $X_1(t)$ be the number of departures from the first system and $Y_2(t)$ be the number of arrivals to the second system by time $t$. Then

$P(Y_2(t) = k|X_1(t) = n) = \binom{n}{k}p^k(1-p)^{n-k} \quad (2.223)