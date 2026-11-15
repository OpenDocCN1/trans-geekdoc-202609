To obtain a sharp pseudo-Lipschitz constant for \( x \mapsto \|x\|^r \) in (B.18) above, we apply the following elementary inequality.

# **Lemma B.20.** If \( a, b \ge 0 \) and \( r \ge 1 \), then \( |a^r - b^r| \le \max(1, r/2) |a - b| (a^{r-1} + b^{r-1}) \).

Proof. Suppose without loss of generality that \( 0 \le b \le a \). If \( r \ge 2 \), then \( t \mapsto rt^{r-1} \) is convex on \( [0, \infty) \), so

```
\( a^r - b^r = \int_a^b r t^{r-1} dt \le \int_a^b r \left( \frac{t-b}{a-b} a^{r-1} + \frac{a-t}{a-b} b^{r-1} \right) dt = \frac{r}{2}(a - b)(a^{r-1} + b^{r-1}) \).
```

If \( r \in [1, 2] \), then \( 0 \le (ab)^{r-1}(a^{2-r} - b^{2-r}) = ab^{r-1} - ba^{r-1} \), so \( a^r - b^r \le (a - b)(a^{r-1} + b^{r-1}) \).

When we have a sequence of possibly random probability measures \( P_n \equiv P_n(\omega) \) on \( \mathbb{R}^D \), we can apply the deterministic Theorem B.17 to obtain Corollary B.21 below, in which we equip \( \mathcal{P}(r) \) with the Borel \( \sigma \)-algebra \( \mathcal{B}_r \equiv \mathcal{B}(\mathcal{P}(r)) \) associated with the \( d_r \) (or equivalently the \( \tilde{d}_r \)) metric. Note that \( \tilde{d}_r(P_n, P) \) is measurable (i.e. a bona fide random variable) for each \( n \) by Proposition B.16. The measurability of \( d_r(P_n, P) \) is guaranteed by Villani (2009, Corollary 5.22); see also Panaretos and Zemel (2020, Lemma 2.4.6).

# **Corollary B.21.** Fix \( P \in \mathcal{P}(r) \equiv \mathcal{P}_D(r) \) and let \( (P_n) \) be a sequence of random elements \( P_n: \Omega \to \mathcal{P}(r) \).

+   (a) Then the following are equivalent:

+   (i) \( \int_{\mathbb{R}^D} \psi \, dP_n \xrightarrow{a.s.} \int_{\mathbb{R}^D} \psi \, dP \) for every \( \psi \in \text{PL}_D(r) \);
+   (ii) \( \tilde{d}_r(P_n, P) \xrightarrow{a.s.} 0 \);
+   (iii) \( d_r(P_n, P) \xrightarrow{a.s.} 0 \).

+   (b) The same equivalences hold if the mode of convergence in (i)–(iii) is instead taken to be either convergence in probability or complete convergence.