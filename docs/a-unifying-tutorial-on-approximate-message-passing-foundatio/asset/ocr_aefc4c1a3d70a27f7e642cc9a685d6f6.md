We write $X_n = o_c(1)$ if $X_n \xrightarrow{c} 0$, and write $X_n = O_c(1)$ if $Y_n = O_{a.s.}(1)$ (i.e., $\limsup_{n\to\infty} \|Y_n\|_E < \infty$ almost surely) for any sequence of $E$-valued random elements $(Y_n)$ with $Y_n \stackrel{d}{=} X_n$ for all $n$.

# **Proposition 1.2.** For a sequence $(X_n)$ of random elements taking values in a Euclidean space $(E, \|\cdot\|_E)$, we have

+   (a) $X_n = o_c(1)$ if and only if $\sum_n \mathbb{P}(\|X_n\|_E > \varepsilon) < \infty$ for all $\varepsilon > 0$;

+   (b) $X_n = O_c(1)$ if and only if there exists $C > 0$ such that $\sum_n \mathbb{P}(\|X_n\|_E > C) < \infty$.

For a deterministic $x \in E$, we see that $X_n \xrightarrow{c} x$ if and only if $\sum_n \mathbb{P}(\|X_n - x\|_E > \varepsilon) < \infty$ for all $\varepsilon > 0$. Moreover, if $X_n \xrightarrow{c} x$, then $X_n = O_c(1)$. The proof of Proposition 1.2, along with various other properties of complete convergence and a calculus for $o_c(1)$ and $O_c(1)$ notation, is given in Section B.1; see also Remark A.1.

# **Wasserstein distances and pseudo-Lipschitz functions:** For $D \in \mathbb{N}$ and $r \in [1, \infty)$, we write $\mathcal{P}(r) \equiv \mathcal{P}_D(r)$ for the set of all Borel probability measures $P$ on $\mathbb{R}^D$ with $\int_{\mathbb{R}^D} \|x\|^r dP(x) < \infty$. For $P, Q \in \mathcal{P}_D(r)$, the $r$-*Wasserstein distance* between $P$ and $Q$ is defined by

$$d_r(P, Q) := \inf_{(X,Y)} \mathbb{E}(\|X - Y\|^r)^{1/r},$$

where the infimum is taken over all pairs of random vectors $(X, Y)$ defined on a common probability space with $X \sim P$ and $Y \sim Q$. For $P, P_1, P_2, ... \in \mathcal{P}_D(r)$, we have $d_r(P_n, P) \to 0$ if and only if both $\int_{\mathbb{R}^D} \|x\|^r dP_n(x) \to \int_{\mathbb{R}^D} \|x\|^r dP(x)$ and $P_n \to P$ weakly (e.g., Villani, 2003, Theorem 7.12). Furthermore, for $L > 0$, we write $\text{PL}_D(r, L)$ for the set of functions $\psi: \mathbb{R}^D \to \mathbb{R}$ such that

$$|\psi(x) - \psi(y)| \le L \|x - y\| (1 + \|x\|^{r-1} + \|y\|^{r-1}) \tag{1.3}$$

for all $x, y \in \mathbb{R}^D$, and denote by $\text{PL}_D(r) := \bigcup_{L>0} \text{PL}_D(r, L)$ the class of *pseudo-Lipschitz functions* $f: \mathbb{R}^D \to \mathbb{R}$ of order $r$. Note that $\text{PL}_D(1, L)$ is precisely the class of all $(3L)$-Lipschitz functions on $\mathbb{R}^D$, and that $\text{PL}_D(s) \subseteq \text{PL}_D(r)$ for any $1 \le s \le r$. Moreover, for any probability measure $P \in \mathcal{P}_D(r)$, we have $|\int_{\mathbb{R}^d} \psi dP| \le L \int_{\mathbb{R}^D}(\|x\| + \|x\|^r) dP(x) +$