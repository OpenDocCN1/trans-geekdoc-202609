positive definite by Lemma 2.2. We can now apply the continuous mapping theorem for complete convergence (Lemma B.2) to deduce that $(M_k^\top M_k/n)^+ \xrightarrow{\text{c}} (\bar{\Gamma}^{[k]})^{-1}$; see $\mathcal{H}_k(i)$ above for a similar argument. By $\mathcal{H}_k(h)$, we have $v^{k,\ell}/n \xrightarrow{\text{c}} 0 \in \mathbb{R}^k$ for all $0 \le \ell \le k$, so

```
$\tilde{w}^k \equiv \tilde{w}^k(n) := (M_k^\top M_k)^+ \left( v^{k,k} - \sum_{\ell=1}^k \alpha_\ell^k v^{k,\ell-1} \right) \xrightarrow{\text{c}} 0,$
```

formally by Slutsky's lemma for complete convergence (Lemma B.2). Since $\|m^{\ell-1}\|_{n,r} = O_c(1)$ for $1 \le \ell \le k$ by $\mathcal{H}_k(b)$, we have $\|R_{n2}\|_{n,r} = \|M_k\tilde{w}^k\|_{n,r} \le \sum_{\ell=1}^k |\tilde{w}_\ell^k| \|m^{\ell-1}\|_{n,r} = \sum_{\ell=1}^k o_c(1) O_c(1) = o_c(1)$.

Turning to $R_{n3}$ and introducing $\xi_1, ..., \xi_k \overset{\text{iid}}{\sim} N(0,1)$, we see from Lemma A.18 that $\|P_k \tilde{Z}^{k+1}\|_{n,r}$ is stochastically dominated by $\sum_{i=1}^k |\xi_i| / n^{1/r}$ for each $n > k$. By Example 1(a), $\sum_{i=1}^k |\xi_i| / n^{1/r} \le k \max_{1 \le i \le k} |\xi_i| / n^{1/r} = o_c(1)$, so $\|P_k \tilde{Z}^{k+1}\|_{n,r} \xrightarrow{\text{c}} 0$. Since $\|\dot{m}^k\|_n \xrightarrow{\text{c}} \dot{\tau}_{k+1} \in (0, \infty)$ by $\mathcal{H}_k(j)$, we deduce that $\|R_{n3}\|_{n,r} = \|\dot{m}^k\|_n \|P_k \tilde{Z}^{k+1}\|_{n,r} = o_c(1)$.

For the remaining summands $R_{n4}$ and $R_{n5}$, the arguments are similar to those in the proof of $\mathcal{H}_1(a)$. Recall that $(\tilde{Z}^{k+1}, \dot{\zeta}^{k+1}) \equiv (\dot{Z}^{k+1}(n), \dot{\zeta}^{k+1}(n)) \sim N_n(0, I_n) \otimes N(0, 1/n)$. Introducing $\zeta \sim N(0, 1)$, we have $|\dot{\zeta}^{k+1}| \stackrel{d}{=} n^{-1/2} |\zeta| \xrightarrow{\text{c}} 0$ by Example 1(a), and $\|\dot{Z}^{k+1}\|_{n,r} = (n^{-1} \sum_{i=1}^n |\dot{Z}_i^{k+1}|^r)^{1/r} \xrightarrow{\text{c}} \mathbb{E}(|\zeta|^r)^{1/r} \in (0, \infty)$ by Lemma B.12 and Proposition 1.2. By $\mathcal{H}_k(j)$, we have $\|\dot{m}^k\|_n - \dot{\tau}_{k+1} = o_c(1)$. Moreover, $\alpha^k = \bar{\alpha}^k + o_c(1) = O_c(1)$ by $\mathcal{H}_k(i)$ and $\|m^\ell\|_{n,r} = O_c(1)$ for $0 \le \ell \le k$ by $\mathcal{H}_k(b)$, so it follows from (A.4) that

```
$\| \dot{m}^k \|_{n,r} = \|(I - P_k) m^k\|_{n,r} \le \|m^k\|_{n,r} + \sum_{\ell=1}^k |\alpha_\ell^k| \|m^{\ell-1}\|_{n,r}$
$= O_c(1) + \sum_{\ell=1}^k O_c(1) O_c(1) = O_c(1).$
```

Putting everything together, we see that

```
$\| R_{n4} \|_{n,r} + \| R_{n5} \|_{n,r} = \|\dot{m}^k\|_n - \dot{\tau}_{k+1} \|\dot{Z}^{k+1}\|_{n,r} + |\dot{\zeta}^{k+1}| \|\dot{m}^k\|_{n,r}$
$= o_c(1) O_c(1) + o_c(1) O_c(1) = o_c(1).$
```

We have now shown that $\|R_{ns}\|_{n,r} \xrightarrow{\text{c}} 0$ for $s=1, ..., 5$, so $\|\Delta^{k+1}\|_{n,r} \le \sum_{s=1}^5 \|R_{ns}\|_{n,r} \xrightarrow{\text{c}} 0$.