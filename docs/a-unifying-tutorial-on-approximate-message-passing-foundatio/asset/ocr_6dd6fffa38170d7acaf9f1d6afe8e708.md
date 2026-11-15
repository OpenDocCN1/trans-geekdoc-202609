$N(0, 1)$. Then by Lemma B.23(a), there exists \(K_k > 0\), depending only on the deterministic \(\bar{\alpha}^k \equiv (\bar{\alpha}^k_1, \dots, \bar{\alpha}^k_k)\), \(\hat{\tau}_{k+1}\) and \(r\), such that \(\psi_v \in \mathrm{PL}_1(r, K_k L_{\|v\|})\) with \(L_{\|v\|} = L(1 \vee \|v\|^{r-1})\). For a fixed integer \(n > k\) and \(v^{(1)}, \dots, v^{(n)} \in \mathbb{R}^{k+1}\), define \(\check{L} \equiv \check{L}(v^{(1)}, \dots, v^{(n)}) := (L_{|v^{(1)}|}, \dots, L_{|v^{(n)}|})\). Let \(r' = r/(r-1) \in (1, 2]\) be as in the proof of \(\mathcal{H}_1(c)\), so that \(1/r + 1/r' = 1\), and note that since \(\|\cdot\|_{p'} \le \|\cdot\|_p\) for \(1 \le p \le p' \le \infty\), we have

```
\(\frac{\|\check{L}\|_\infty}{n^{1/r'}} \le \frac{\|\check{L}\|_2}{n^{1/r'}} \le \frac{\|\check{L}\|_{r'}}{n^{1/r'}} = \|\check{L}\|_{n,r'} = \left( \frac{1}{n} \sum_{i=1}^n \left( L_{|v^{(i)}|} \right)^{r'} \right)^{1/r'} \le L \left( 1 + \frac{1}{n} \sum_{i=1}^n \|v^{(i)}\|^r \right)^{1/r'} . \text{(A.43)}\)
```

By Lemma B.12, it follows as in (A.27) that there exists a universal constant \(C > 0\) such that if \(Z_1, \dots, Z_n \stackrel{\mathrm{iid}}{\sim} N(0, 1)\), then

```
\(P(n, t, v^{(1)}, \dots, v^{(n)}) := \mathbb{P} \left( \left| \frac{1}{n} \sum_{i=1}^n \bar{\psi}_{v^{(i)}}(Z_i) \right| \ge t \right) \le \exp \left( 1 - \min \left\{ \left( \frac{nt}{(Cr)^r K_k \|\check{L}\|_2} \right)^2, \left( \frac{nt}{(Cr)^r K_k \|\check{L}\|_\infty} \right)^{2/r} \right\} \right) \le \exp \left( 1 - \min \left\{ \left( \frac{n^{1/r} t}{(Cr)^r K_k \|\check{L}\|_{n,r'}} \right)^2, \left( \frac{n^{1/r} t}{(Cr)^r K_k \|\check{L}\|_{n,r'}} \right)^{2/r} \right\} \right) = E_r(n, t, K_k \|\check{L}\|_{n,r'}) \equiv E_r \left( n, t, K_k \|\check{L}(v^{(1)}, \dots, v^{(n)})\|_{n,r'} \right) \text{(A.44)}\)
```

for every \(t \ge 0\). Next, define the \(\mathcal{S}_k\)-measurable vectors \(v_k^{(i)} := (h^1_i, \dots, h^k_i, \gamma_i)\) for \(1 \le i \le n\). Returning to (A.42) and recalling (A.38), we see that

```
\(\psi(h^1_i, \dots, h^k_i, \tilde{h}^{k+1}_i, \gamma_i) - \mathbb{E}(\psi(h^1_i, \dots, h^k_i, \tilde{h}^{k+1}_i, \gamma_i) \mid \mathcal{S}_k) = \psi_{v_k^{(i)}}(\tilde{Z}^{k+1}_i) - \mathbb{E}(\psi_{v_k^{(i)}}(\tilde{Z}^{k+1}_i) \mid \mathcal{S}_k) = \bar{\psi}_{v_k^{(i)}}(\tilde{Z}^{k+1}_i)\)
```

for all \(1 \le i \le n\), where the final equality follows from Lemma B.7 and the fact that \(\tilde{Z}^{k+1} \equiv \tilde{Z}^{k+1}(n)\) is independent of \(\mathcal{S}_k \equiv \mathcal{S}_k(n)\). We deduce