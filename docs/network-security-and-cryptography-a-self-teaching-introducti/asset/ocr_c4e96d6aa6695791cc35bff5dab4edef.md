# MATHEMATICAL FOUNDATIONS FOR COMPUTER NETWORKS * 91

$\lambda p_0 = \mu p_1$

$\lambda p_n + \mu p_n = \lambda p_{n-1} + \mu p_{n+1}, \quad 1 \leq n \leq k-1 \quad (2.164)$

$\lambda p_{k-1} = \mu p_k$

![](bbox=[0.166, 0.255, 0.81, 0.342])

The probability of zero customers in the system, $p_0$ can be obtained from

$p_0 = \frac{1}{1 + \sum_{n=1}^{k} \frac{\lambda^n}{\mu_1\dots\mu_n}}, \quad p_0 = \left(1 + \sum_{n=1}^{k} (\frac{\lambda}{\mu})^n\right)^{-1}$

The sum is a finite geometric series which can be obtained by

$\sum_{n=1}^{k} \left(\frac{\lambda}{\mu}\right)^n = \frac{\left(\frac{\lambda}{\mu}\right)^k}{1 - \left(\frac{\lambda}{\mu}\right)}$

Now, we get
\n$p_0 = \frac{1-\ho}{1-\rho^{k+1}}$

We solve these equations recursively and apply the normalization condition. If we define $\rho = \lambda / \mu$, the state probabilities at a steady state are given by

$p_n = \begin{cases} \frac{(1-\rho)\rho^n}{1-\rho^{k+1}}, & 0 \leq n \leq k \ 0, & n > k \end{cases} \quad (2.165)$