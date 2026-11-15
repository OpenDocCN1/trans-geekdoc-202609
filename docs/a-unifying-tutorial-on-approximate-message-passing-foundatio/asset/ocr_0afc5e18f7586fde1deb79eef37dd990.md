(b) For \(x, y \in \mathbb{R}^D\), we have

```
|\Psi(x) - \Psi(y)|
\le \mathbb{E}[\{\psi(x_1, \dots, x_D, \sum_{\ell=1}^D c_\ell x_\ell + \tau Z)
- \psi(y_1, \dots, y_D, \sum_{\ell=1}^D c_\ell y_\ell + \tau Z)\}]
\le L(1 + \|c\|)\|x - y\| \{1 + 2(1 \vee 2^{r-2}) \mathbb{E}(|\tau Z|^{r-1})
+ (1 \vee 2^{r-2})(1 + \|c\|)^{r-1}(\|x\|^{r-1} + \|y\|^{r-1})\}
\le L_r\|x - y\| (1 + \|x\|^{r-1} + \|y\|^{r-1}),
```

where the second bound again follows from (B.20), (B.21) and the fact that \(\psi \in \text{PL}_{D+1}(r, L)\).

# **Lemma B.24.** Suppose that \(\psi \in \text{PL}_D(r, L)\) for some \(D \in \mathbb{N}, r \in [2, \infty)\) and \(L > 0\). Then for any \(n \in \mathbb{N}\) and vectors \(x^\ell \equiv (x_1^\ell, \dots, x_n^\ell)\) and \(y^\ell \equiv (y_1^\ell, \dots, y_n^\ell)\) for \(1 \le \ell \le D\), we have

```
\frac{1}{n} \sum_{i=1}^n |\psi(x_i^1, \dots, x_i^D) - \psi(y_i^1, \dots, y_i^D)|
\le LD^{\frac{r}{2}-1} \left( \sum_{\ell=1}^D \|x^\ell - y^\ell\|_{n,r}^r \right)^{1/r} \left( 1 + \sum_{\ell=1}^D (\|x^\ell\|_{n,r}^{r-1} + \|y^\ell\|_{n,r}^{r-1}) \right).
```

**Proof.** For \(1 \le i \le n\), define \(X^{(i)} := (x_i^1, \dots, x_i^D)\) and \(Y^{(i)} := (y_i^1, \dots, y_i^D)\), and let \(r' := r/(r-1) \in (1, 2]\) be the Hölder conjugate of \(r\), so that \(1/r + 1/r' = 1\). Then since \(\psi \in \text{PL}_D(r, L)\), an application of Hölder's inequality yields the bound

```
\frac{1}{n} \sum_{i=1}^n |\psi(x_i^1, \dots, x_i^D) - \psi(y_i^1, \dots, y_i^D)| = \frac{1}{n} \sum_{i=1}^n |\psi(X^{(i)}) - \psi(Y^{(i)})|
\le \frac{1}{n} \sum_{i=1}^n L\|X^{(i)} - Y^{(i)}\| (1 + \|X^{(i)}\|^{r-1} + \|Y^{(i)}\|^{r-1})
\le L \left( \frac{1}{n} \sum_{i=1}^n \|X^{(i)} - Y^{(i)}\|^r \right)^{1/r} \left( \frac{1}{n} \sum_{i=1}^n (1 + \|X^{(i)}\|^{r-1} + \|Y^{(i)}\|^{r-1})^{r'} \right)^{1/r'} .
```