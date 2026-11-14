Thirdly, we show that $D_N^*(M, T)$ is strictly monotonically increasing with respect to $T \in \{1, \dots, M\}$; that is, for any fixed $N \in \mathbb{N}_0$ and $M \in \mathfrak{N}$ and $\forall T_1 < T_2 \in \{1, \dots, M\}$, we claim $D_N^*(M, T_1) < D_N^*(M, T_2)$.

For $T_1, T_2 \le M$, by Definition 4.10 of $D_N^*(M, T)$, there exists a sequence $\boldsymbol{\alpha}^* \in \mathcal{A}^{(M, T_1)}$ such that $D(\boldsymbol{\alpha}^*) = D_N^*(M, T_1)$. However, since $T_2 > T_1$, we also have $\boldsymbol{\alpha}^* \in \mathcal{A}^{(M, T_2)}$; that is, any optimal sequence from $\mathcal{A}^{(M, T_1)}$ is also in the space $\mathcal{A}^{(M, T_2)}$ but has a trailing sequence of zeros: $\alpha_{T_1+1}^* = \dots = \alpha_{T_2}^* = 0$. Alternatively, there is some last index $\tau < T_2$ such that $\alpha_\tau^* > 0$ and $\alpha_t^* = 0$ for all $t > \tau$.

In fact, this $\tau^{\text{th}}$ element must be greater than 1 since, by Theorem 4.14, the non-zero elements of $\boldsymbol{\alpha}^*$ must be non-decreasing. Thus, either $\alpha_\tau^* > 1$ or all previous elements must be in $\{0, 1\}$. However, since $\tau < T_2 \le M$, such a sequence can have at most $M - 1$ elements, but the first part of this theorem already showed that such a sequence is not optimal. Hence, $\alpha_\tau^* > 1$.

Using this fact, we can construct an alternative sequence $\boldsymbol{\alpha}' \in \mathcal{A}^{(M, T_2)}$ that moves one attack point from the $\tau^{\text{th}}$ element of $\boldsymbol{\alpha}^*$ to its $(\tau+1)^{\text{th}}$ element:

```
\(\alpha'_t = \begin{cases} \alpha_t^*, & \text{if } t < \tau \\ \alpha_t^* - 1, & \text{if } t = \tau \\ 1, & \text{if } t = \tau + 1 \\ \alpha_{t-1}^*, & \text{if } t > \tau + 1 \end{cases}\)
```

By design, $\boldsymbol{\alpha}^*$ and $\boldsymbol{\alpha}'$ are $(\tau, 1)$-differing sequences and Lemma B.1 yields

```
\(\Delta_{\boldsymbol{\alpha}^*, \boldsymbol{\alpha}'} = \frac{(\mu_{\tau-1}^{(\boldsymbol{\alpha}^*)} + \alpha'_\tau) \cdot \alpha'_\tau \cdot \alpha^*_{\tau+1} - (\mu_{\tau-1}^{(\boldsymbol{\alpha}^*)} + \alpha^*_\tau) \cdot \alpha'_\tau \cdot \alpha'_{\tau+1}}{(\mu_{\tau-1}^{(\boldsymbol{\alpha}^*)} + \alpha^*_\tau) \left( \mu_{\tau-1}^{(\boldsymbol{\alpha}^*)} + \alpha'_\tau \right) \left( \mu_{\tau-1}^{(\boldsymbol{\alpha}^*)} + \alpha^*_\tau + \alpha^*_{\tau+1} \right)}\)
\(= \frac{-1 \cdot \left( \mu_{\tau-1}^{(\boldsymbol{\alpha}^*)} + \alpha'_\tau \right) \cdot (\alpha^* - 1)}{\left( \mu_{\tau-1}^{(\boldsymbol{\alpha}^*)} + \alpha^*_\tau \right) \left( \mu_{\tau-1}^{(\boldsymbol{\alpha}^*)} + \alpha'_\tau \right) \left( \mu_{\tau-1}^{(\boldsymbol{\alpha}^*)} + \alpha^*_\tau + \alpha^*_{\tau+1} \right)}\)
```

in which $\mu_t^{(\alpha^\text{opt})} = N + \sum_{\ell=1}^t \alpha_\ell^{opt}$. This difference is negative, from which we conclude that $D(\boldsymbol{\alpha}^*) < D(\boldsymbol{\alpha}')$. This contradicts assumption (B.3) that $\boldsymbol{\alpha}^*$ is optimal in $\mathcal{A}^{(M, T_2)}$; i.e., we have shown there is a sequence in $\mathcal{A}^{(M, T_2)}$ whose distance exceeds $D_N^*(M, T_1)$. Thus, $D_N^*(M, T)$ is strictly monotonically increasing for $T \le M$.

Finally, to see that $D_N^*(M, T) = D_N^*(M, \infty)$ for $T \ge M$, any sequence in $\mathcal{A}^{(M, T)}$ must have at least $M - T$ zero elements. As we showed in Theorem 4.12, the distance of a sequence is invariant to the placement of these zero elements so, without loss of generality, we can place them at the end. Thus, any sequence in $\mathcal{A}^{(M, T)}$ achieves the same distance as a sequence in $\mathcal{A}^{(M, M)}$, and the optimal distances achieved within these two spaces is equal.

Notice that the above argument does not hold for the space $\mathcal{B}^{(M, \infty)}$ of all positive-real-valued sequences with total mass of $M$ since there need not be a greatest non-zero element in such a sequence. However, optimality is not well-defined on such a space. This proof does, however, extend directly to sequences in $\mathcal{B}^{(M, T)}$ since the finite attack duration $T$ implies the existence of a greatest non-zero element.