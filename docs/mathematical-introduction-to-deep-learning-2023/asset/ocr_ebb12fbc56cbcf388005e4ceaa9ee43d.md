# 14.2  Overall error decomposition

**Proposition 14.2.1.** *Let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $M, d \in \mathbb{N}$, $D \subseteq \mathbb{R}^{d}$, $u \in \mathbb{R}$, $v \in (u, \infty)$, for every $j \in \{1, 2, \ldots, M\}$ let $X_j: \Omega \rightarrow D$ and $Y_j: \Omega \rightarrow [u, v]$ be random variables, let $\mathbf{R}: \mathbb{R}^{d} \rightarrow \mathbb{R}$ satisfy for all $\theta \in \mathbb{R}^{d}$ that*

\begin{equation}
\mathbf{R}(\theta)=\mathbb{E}[|\mathscr{A}_{u, v}^{\theta, 1}(X_1)-Y_1|^2],
\end{equation}

*let $\mathbf{d}, \mathbf{L} \in \mathbb{N}$, $\mathbf{l} = (0, \mathbf{l}_1, \ldots, \mathbf{l}_{\mathbf{L}}) \in \mathbb{N}^{\mathbf{L}+1}$ satisfy*

\begin{equation}
\mathbf{l}_0 = \mathbf{d}, \quad \quad \mathbf{l}_{\mathbf{L}} = 1, \quad \quad \text{and} \quad \quad \mathbf{d} \ge \sum_{i=1}^{\mathbf{L}} \mathbf{l}_i(\mathbf{l}_{i-1} + 1),
\end{equation}

*let $\mathscr{R}: \mathbb{R}^{d} 	imes \Omega \rightarrow \mathbb{R}$ satisfy for all $\theta \in \mathbb{R}^{d}$ that*

\begin{equation}
\mathscr{R}(\theta) = \frac{1}{M} \left[ \sum_{j=1}^{M} |\mathscr{A}_{u, v}^{\theta, 1}(X_j) - Y_j|^2 \right],
\end{equation}

*let $\mathcal{E}: D \rightarrow [u, v]$ be $\mathcal{B}(D)/\mathcal{B}([u, v])$-measurable, assume $\mathbb{P}$-a.s. that*

\begin{equation}
\mathcal{E}(X_1) = \mathbb{E}[Y_1 | X_1],
\end{equation}

*let $B \in [0, \infty)$, for every $k, n \in \mathbb{N}_0$ let $\Theta_{k, n}: \Omega \rightarrow \mathbb{R}^{d}$ be a function, let $K, N \in \mathbb{N}$, $\mathbf{T} \subseteq \{0, 1, \ldots, N\}$, let $\mathbf{k}: \Omega \rightarrow (\mathbb{N}_0)^2$ satisfy for all $\omega \in \Omega$ that*

\begin{equation}
\mathbf{k}(\omega) \in \{(k, n) \in \{1, 2, \ldots, K\} \times \mathbf{T}: \|\Theta_{k, n}(\omega)\|_{\infty} \le B\}
\end{equation}
*and*

\begin{equation}
\mathscr{R}(\Theta_{\mathbf{k}(\omega)}(\omega)) = \min_{(k,n) \in \{1,\ldots,K\} \times \mathbf{T}: \|\Theta_{k,n}(\omega)\|_\infty \le B} \mathscr{R}(\Theta_{k,n}(\omega))
\end{equation}

*(*cf.* Definitions 3.3.4 and 4.4.1) *Then it holds for all* $\theta \in [-B, B]^d$ *that*

\begin{equation}
\begin{aligned}
&\int_D |\mathscr{A}_{u, v}^{\Theta_{k, n}}(x) - \mathcal{E}(x)|^2 \mathbb{P}_{X_1}(dx) \\
&\quad \le \left[ \sup_{x \in D} |\mathscr{A}_{u, v}^{\theta, 1}(x) - \mathcal{E}(x)|^2 + 2 \left[ \sup_{\vartheta \in [-B, B]^d} |\mathscr{R}(\vartheta) - \mathbf{R}(\theta)| \right] \right. \\
&\qquad \left. + \min_{(k,n) \in \{1,\ldots,K\} \times \mathbf{T}: \|\Theta_{k,n}\|_\infty \le B} \mathscr{R}(\Theta_{k, n}) - \mathscr{R}(\vartheta) \right].
\end{aligned}
\end{equation}

*Proof of Proposition 14.2.1.* Throughout this proof, let $\mathbf{r}: \mathcal{L}^2(\mathbb{P}_{X_1}; \mathbb{R}) \rightarrow [0, \infty)$ satisfy for all $f \in \mathcal{L}^2(\mathbb{P}_{X_1}; \mathbb{R})$ that

\begin{equation}
\mathbf{r}(f) = \mathbb{E}[|f(X_1) - Y_1|^2].
\end{equation}

Observe that the assumption that for all $\omega \in \Omega$ it holds that $Y_1(\omega) \in [u, v]$ and the fact that for all $\theta \in \mathbb{R}^d$, $x \in \mathbb{R}^d$ it holds that $\mathscr{A}_{u,v}^{\theta,1}(x) \in [u,v]$ imply that for all $\theta \in \mathbb{R}^d$ it holds that $\mathbb{E}[|Y_1|^2] \le \max\{u^2, v^2\} < \infty$ and

\begin{equation}
\int_D |\mathscr{A}_{u, v}^{\theta, 1}(x)|^2 \mathbb{P}_{X_1}(dx) = \mathbb{E}[|\mathscr{A}_{u, v}^{\theta, 1}(X_1)|^2] \le \max\{u^2, v^2\} < \infty.
\end{equation}