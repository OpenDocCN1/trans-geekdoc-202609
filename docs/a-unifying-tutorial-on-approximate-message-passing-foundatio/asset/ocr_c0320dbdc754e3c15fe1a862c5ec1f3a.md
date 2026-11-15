For instance, suppose that $X_n = X \sim N(0,1)$ for all $n$. Then $X_n \to X$ almost surely and $X_n = O_p(1)$ but $(X_n)$ is not $O_c(1)$, and $X_n/\log^{1/2} n \to 0$ almost surely but $(X_n/\log^{1/2} n)$ is not $o_c(1)$. 

Using Proposition 1.2, it is straightforward to verify that the continuous mapping theorem and Slutsky's lemma remain valid when stated in terms of complete convergence. 

**Lemma B.2.** Let $(X_n), (Y_n)$ be sequences of random elements taking values in Euclidean spaces $E, E'$ respectively such that $X_n \xrightarrow{c} x$ and $Y_n \xrightarrow{c} y$ for some deterministic limits $x \in E$ and $y \in E'$. Then $(X_n, Y_n) \xrightarrow{c} (x, y)$ in $E \times E'$ and $g(X_n) \xrightarrow{c} g(x)$ in $E'$ for any function $g: E \to E'$ that is continuous at $x$. If in addition $x$ lies in some open set $U \subseteq E$, then $\mathbb{1}_{\{X_n \notin U\}} \xrightarrow{c} 0$. 

Consequently, $X_n + Y_n \xrightarrow{c} x + y$ when $E = E'$. Moreover, $X_n Y_n \xrightarrow{c} xy$ when $E = \mathbb{R}$ and $E'$ is any Euclidean space (in the case of scalar multiplication), or when $E = \mathbb{R}^{k \times \ell}$ and $E' = \mathbb{R}^\ell$ for some $k, \ell \in \mathbb{N}$ (in the case of matrix multiplication). If in addition $k = \ell$ and $x^{-1} \in E$ is well-defined, then $\mathbb{1}_{\{X_n \text{ is not invertible\}}} \xrightarrow{c} 0$ and $X_n^+ Y_n \xrightarrow{c} x^{-1} y$. 

*Proof.* For the first part of the lemma, we apply Proposition 1.2(a). Since $\|(\tilde{x}, \tilde{y})\|_{E \times E'}^2 = \|\tilde{x}\|_E^2 + \|\tilde{y}\|_{E'}^2$ for any $(\tilde{x}, \tilde{y}) \in E \times E'$, we have 

$\sum_n \mathbb{P}(\|(X_n, Y_n) - (x, y)\|_{E \times E'} > \epsilon) \le \sum_n \{ \mathbb{P}(\|X_n - x\|_E > \epsilon/\sqrt{2}) + \mathbb{P}(\|Y_n - y\|_{E'} > \epsilon/\sqrt{2}) \} < \infty$ 

for all $\epsilon > 0$, so $(X_n, Y_n) \xrightarrow{c} (x, y)$ by Proposition 1.2(a). If $g: E \to E'$ is continuous at $x \in E$, then for each $\epsilon > 0$, there exists $\delta > 0$ such that $\|g(\tilde{x}) - g(x)\|_{E'} < \epsilon$ whenever $\|\tilde{x} - x\|_E < \delta$, so 

$\sum_n \mathbb{P}(\|g(X_n) - g(x)\|_{E'} > \epsilon) \le \sum_n \mathbb{P}(\|X_n - x\|_E > \delta) < \infty$. 

This holds for all $\epsilon > 0$, so $g(X_n) \xrightarrow{c} g(x)$ by Proposition 1.2(a). When $x$ lies in some open set $U \subseteq E$, there exists $\epsilon > 0$ such that $\mathbb{P}(X_n \notin U) \le \mathbb{P}(\|X_n - X\|_E > \epsilon)$, so $\mathbb{1}_{\{X_n \notin U\}} \xrightarrow{c} 0$, again by Proposition 1.2(a). 

Having established the first part of the lemma, we can now apply the facts above to deduce the remaining assertions. Indeed, when $E = E'$,