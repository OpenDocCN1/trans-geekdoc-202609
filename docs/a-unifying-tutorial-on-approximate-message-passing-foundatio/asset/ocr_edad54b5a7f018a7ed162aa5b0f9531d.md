$\phi \in \text{PL}_{k+2}(1)$, it follows that $n^{-1} \sum_{i=1}^n m_i^0 \phi(h_i^1, \dots, h_i^k, h_i^{k+1}) \stackrel{d}{=} n^{-1} \cdot \sum_{i=1}^n m_i^0 \phi(h_i^1, \dots, h_i^k, h_i^{k+1,k}) =: T_n$ for each such $n$. Using (A.38), we now write

```
$$
\begin{aligned}
T_n &= \frac{1}{n} \sum_{i=1}^n m_i^0 \phi(h_i^1, \dots, h_i^k, \tilde{h}_i^{k+1}, \gamma_i) \n&\quad + \frac{1}{n} \sum_{i=1}^n m_i^0 \{ \phi(h_i^1, \dots, h_i^k, h_i^{k+1,k}, \gamma_i) - \phi(h_i^1, \dots, h_i^k, \tilde{h}_i^{k+1}, \gamma_i) \} \n&=: T_{n1} + T_{n2}
\end{aligned}
\tag{A.48}$$
```

for each $n > k$, and aim to prove that $T_{n1} \stackrel{p}{\to} \mathbb{E}(F_0(\bar{\gamma}) \cdot \phi(\bar{G}_1, \dots, \bar{G}_k, \bar{\gamma}))$ and $T_{n2} \stackrel{p}{\to} 0$, which together imply the desired conclusion.

For $T_{n1}$, recall once again from (A.21) or (A.38) that $\bar{h}^{k+1}(n) = \sum_{\ell=1}^k \bar{\alpha}_\ell^k h^\ell(n) + \bar{\tau}_{k+1} \tilde{Z}^{k+1}(n)$ for each $n$, where $\tilde{Z}^{k+1} \equiv \tilde{Z}^{k+1}(n) \sim N_n(0, I_n)$ is independent of $\mathcal{S}_k \equiv \mathcal{S}_k(n) = \sigma(\gamma, m^0, h^1, \dots, h^k)$. Define $\Phi: \mathbb{R}^{k+1} \to \mathbb{R}$ by $\Phi(x_1, \dots, x_k, y) := \mathbb{E}\{\phi(x_1, \dots, x_k, \sum_{\ell=1}^k \bar{\alpha}_\ell^k x_\ell + \bar{\tau}_{k+1} Z, y)\}$ with $Z \sim N(0, 1)$. Then $\Phi \in \text{PL}_{k+1}(1)$ by Lemma B.23(b), and as in (A.40) and (A.41), it follows from the inductive hypothesis $\mathcal{H}_k(d)$ and Lemma B.7 that

```
$$
\begin{aligned}
&\frac{1}{n} \sum_{i=1}^n m_i^0 \mathbb{E}(\phi(h_i^1, \dots, h_i^k, \tilde{h}_i^{k+1}, \gamma_i) \mid \mathcal{S}_k) \n&= \frac{1}{n} \sum_{i=1}^n m_i^0 \Phi(h_i^1, \dots, h_i^k, \gamma_i) \n&\stackrel{p}{\to} \mathbb{E}(F_0(\bar{\gamma}) \cdot \Phi(\bar{G}_1, \dots, \bar{G}_k, \bar{\gamma})) \n&= \mathbb{E}(F_0(\bar{\gamma}) \cdot \phi(\bar{G}_1, \dots, \bar{G}_k, \bar{G}_{k+1}, \bar{\gamma})).
\end{aligned}
\tag{A.49}$$
```

Next, we show as in (A.42) that

```
$$
\begin{aligned}
T'_{n1} &:= \frac{1}{n} \sum_{i=1}^n m_i^0 \{ \phi(h_i^1, \dots, h_i^k, \tilde{h}_i^{k+1}, \gamma_i) \n&\quad - \mathbb{E}(\phi(h_i^1, \dots, h_i^k, \tilde{h}_i^{k+1}, \gamma_i) \mid \mathcal{S}_k) \} \stackrel{p}{\to} 0.
\end{aligned}
\tag{A.50}$$
```

To this end, for each $u \in \mathbb{R}$ and $v \equiv (x_1, \dots, x_k, y) \in \mathbb{R}^{k+1}$, define $\phi_{u,v}, \bar{\phi}_{u,v}: \mathbb{R} \to \mathbb{R}$ by $\phi_{u,v}(z) := u \phi(x_1, \dots, x_k, \sum_{\ell=1}^k \bar{\alpha}_\ell^k x_\ell + \bar{\tau}_{k+1} z, y)$ and $\bar{\phi}_{u,v}(z) := \phi_{u,v}(z) - \mathbb{E}(\phi_{u,v}(Z))$, where $Z \sim N(0, 1)$. Since $\phi \in \text{PL}_{k+2}(1)$, we deduce from Lemma B.23(a) that there exists $K' > 0$,