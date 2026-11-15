**Lemma 3.3.** [36] Granted that Assumption 3.2 is valid, it follows that \(\forall x \in \mathbb{R}^{m \times p}\), \(\|Ax - A_\infty x\| \le \sigma_2^2 \|x - A_\infty x\|\), where \(A_\infty = \frac{1}{m} \mathbf{1}_m \mathbf{1}_m^\mathrm{T}\).

**Lemma 3.4.** [52] Provided a non-negative matrix \(B \in \mathbb{R}^{m \times m}\) and a positive vector \(\epsilon \in \mathbb{R}^m\), whenever it holds true that for all \(\alpha > 0\), \(B\epsilon\) is element-wise less than or equal to \(\alpha \epsilon\), then the inequality \(\rho(B) \le \|B\|_\infty \le \alpha\) holds.

# ## 3.4.2 Auxiliary lemmas

To ensure that all nodes converge to the same consensus solution, we will limit the disparity represented by \(\mathbb{E}[\|x_{k+1} - A^\infty x_{k+1}\|^2]\). To achieve the optimal solution arrived at by the consensus, we will restrict the difference denoted by \(\mathbb{E}[\|\overline{x}_{k+1} - x^*\|^2]\). To obtain an exact global gradient estimator, we will bound the divergence given by \(\mathbb{E}[\|y_{k+1} - A^\infty y_{k+1}\|^2]\). Thanks to the integration of the variance-reduction method into our algorithm, we will confine the divergence represented by \(\mathbb{E}[\|t_k^{i,j} - x^*\|^2]\) to neutralize the variance introduced by the stochastic gradient. By defining \(v_k^i\) as \((1/n^i) \sum_{j=1}^{n^i} \|t_k^{i,j} - x^*\|^2\) and setting \(v_k\) as the sum of all \(v_k^i\) from \(j=1\) to \(n^i\), we will limit the scope of \(\mathbb{E}[v_{k+1}]\) as a surrogate for limiting the scope of \(\mathbb{E}[\|t_k^{i,j} - x^*\|^2]\). Initially, we derive Lemma 3.5 by limiting the scope of \(\mathbb{E}[\|x_{k+1} - A^\infty x_{k+1}\|^2]\).

**Lemma 3.5.** Provided that Assumption 3.2 is valid, it follows that: \(\forall k \ge 0\),

```
\(\mathbb{E}[\|x_{k+1} - A^\infty x_{k+1}\|^2] \le (1+a)\sigma_2^2 \mathbb{E}[\|x_k - A^\infty x_k\|^2] + (1+a^{-1})\eta^2 \mathbb{E}[\|y_k - A^\infty y_k\|^2].\)
```

By assigning the values of 1 and \(\frac{1-\sigma_2^2}{2\sigma_2^2}\) to \(a\) in the aforementioned inequality, we can derive the subsequent two results:

```
\(\mathbb{E}[\|x_{k+1} - A^\infty x_{k+1}\|^2] \le 2 \mathbb{E}[\|x_k - A^\infty x_k\|^2] + 2\eta^2 \mathbb{E}[\|y_k - A^\infty y_k\|^2]\)
```

```
\(\mathbb{E}[\|x_{k+1} - A^\infty x_{k+1}\|^2] \le \frac{1+\sigma_2^2}{2} \mathbb{E}[\|x_k - A^\infty x_k\|^2] + \frac{2\eta}{1-\sigma_2^2} \mathbb{E}[\|y_k - A^\infty y_k\|^2].\)
```

**Proof.** Based on the updating principle outlined in (3.7) and Young's inequality, which states that \(\|a+b\|^2 \le (1+\zeta)\|a\|^2 + (1+\frac{1}{\zeta})\|b\|^2, \forall a, b \in \mathbb{R}^{m \times p}, \forall \zeta > 0\) [19], we arrive at the subsequent conclusion:

```
\(\mathbb{E}[\|x_{k+1} - A^\infty x_{k+1}\|^2]\)
\(=\mathbb{E}[\|P_\Omega(Ax_k) - P_\Omega(A^\infty x_k) - A^\infty(P_\Omega(Ax_k) - P_\Omega(A^\infty x_k)) - \eta(I_m - A^\infty)y_k\|^2]\)
\(\le (1+a) \mathbb{E}[\|(I_m - A^\infty)(P_\Omega(Ax_k) - P_\Omega(A^\infty x_k))\|^2]\)
\(+ (1+a^{-1})\eta^2 \mathbb{E}[\|y_k - A^\infty y_k\|^2]\)
```