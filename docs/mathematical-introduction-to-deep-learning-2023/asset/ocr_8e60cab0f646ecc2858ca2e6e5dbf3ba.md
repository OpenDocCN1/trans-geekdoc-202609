**Lemma 6.3.3** (An explicit representation of momentum terms). *Let* $\mathbf{d} \in \mathbb{N}$, $(\alpha_n)_{n \in \mathbb{N}} \subseteq \mathbb{R}$, $(a_{n,k})_{(n,k) \in (\mathbb{N}_0)^2} \subseteq \mathbb{R}$, $(\mathscr{G}_n)_{n \in \mathbb{N}_0} \subseteq \mathbb{R}^\mathbf{d}$, $(\mathbf{m}_n)_{n \in \mathbb{N}_0} \subseteq \mathbb{R}^\mathbf{d}$ *satisfy for all* $n \in \mathbb{N}$, $\mathbf{k} \in \{0, 1, \dots, n-1\}$ *that*

$\mathbf{m}_0 = \mathbf{0}, \quad \mathbf{m}_n = \alpha_n \mathbf{m}_{n-1} + (1 - \alpha_n)\mathscr{G}_{n-1}, \quad \text{and} \quad a_{n,k} = (1 - \alpha_{k+1}) \left[ \prod_{l=k+2}^{n} \alpha_l \right] \eqno{(6.196)}$

*Then*

+   (i) *it holds for all* $n \in \mathbb{N}_0$ *that*

$\mathbf{m}_n = \sum_{k=0}^{n-1} a_{n,k} \mathscr{G}_k \eqno{(6.197)}$

+   and
(ii) *it holds for all* $n \in \mathbb{N}_0$ *that*

$\sum_{k=0}^{n-1} a_{n,k} = 1 - \prod_{k=1}^{n} \alpha_k. \eqno{(6.198)}$

*Proof of Lemma 6.3.3.* *Throughout this proof, let* $(m_n)_{n \in \mathbb{N}_0} \subseteq \mathbb{R}$ *satisfy for all* $n \in \mathbb{N}_0$ *that*

$m_n = \sum_{k=0}^{n-1} a_{n,k}. \eqno{(6.199)}$

We now prove item (i) by induction on $n \in \mathbb{N}_0$. For the base case $n=0$ note that (6.196) ensures that

$\mathbf{m}_0 = \mathbf{0} = \sum_{k=0}^{-1} a_{n,k} \mathscr{G}_k. \eqno{(6.200)}$

This establishes item (i) in the base case $n=0$. For the induction step note that (6.196) assures that for all $n \in \mathbb{N}_0$ with $\mathbf{m}_n = \sum_{k=0}^{n-1} a_{n,k} \mathscr{G}_k$ it holds that

```
$
\begin{split}
\mathbf{m}_{n+1} &= \alpha_{n+1} \mathbf{m}_n + (1 - \alpha_{n+1}) \mathscr{G}_n \\
&= \left[ \sum_{k=0}^{n-1} \alpha_{n+1} a_{n,k} \mathscr{G}_k \right] + (1 - \alpha_{n+1}) \mathscr{G}_n \\
&= \left[ \sum_{k=0}^{n-1} \alpha_{n+1} (1 - \alpha_{k+1}) \left[ \prod_{l=k+2}^{n} \alpha_l \right] \mathscr{G}_k \right] + (1 - \alpha_{n+1}) \mathscr{G}_n \\
&= \left[ \sum_{k=0}^{n-1} (1 - \alpha_{k+1}) \left[ \prod_{l=k+2}^{n+1} \alpha_l \right] \mathscr{G}_k \right] + (1 - \alpha_{n+1}) \mathscr{G}_n \\
&= \sum_{k=0}^{n} (1 - \alpha_{k+1}) \left[ \prod_{l=k+2}^{n+1} \alpha_l \right] \mathscr{G}_k = \sum_{k=0}^{n} a_{n+1,k} \mathscr{G}_k.
\end{split}
$ \eqno{(6.201)}
```