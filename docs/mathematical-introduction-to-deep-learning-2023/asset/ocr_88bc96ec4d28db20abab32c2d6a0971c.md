let $K \in \mathbb{N}$, $c \in [\max\{1, L, |a|, |b|, 2|u|, 2|v|\}, \infty)$, $B \in [c, \infty)$, for every $k, n \in \mathbb{N}_0$ let $\Theta_{k, n} \colon \Omega \rightarrow \mathbb{R}^{\mathbf{d}}$ be a random variable, assume $\bigcup_{k=1}^{\infty} \Theta_{k, 0}(\Omega) \subseteq [-B, B]^{\mathbf{d}}$, assume that $\Theta_{k,0}$, $k \in \{1,2,\dots,K\}$, are i.i.d., assume that $\Theta_{\mathbf{1},0}$ is continuously uniformly distributed on $[-c, c]^{\mathbf{d}}$, let $(\gamma_n)_{n \in \mathbb{N}} \subseteq \mathbb{R}$ satisfy for all $k, n \in \mathbb{N}$ that

$$\Theta_{k,n} = \Theta_{k,n-1} - \gamma_n \mathcal{G}^{k,n}(\Theta_{k,n-1}),$$

let $N \in \mathbb{N}$, $\mathbf{T} \subseteq \{0,1,\dots,N\}$ satisfy $0 \in \mathbf{T}$, let $\mathbf{k} \colon \Omega \rightarrow (\mathbb{N}_0)^2$ be a random variable, and assume for all $\omega \in \Omega$ that

$$\mathbf{k}(\omega) \in \{(k, n) \in \{1,2,\dots,K\} \times \mathbf{T} \colon \|\Theta_{k,n}(\omega)\|_\infty \le B\}$$

and
$$\mathscr{R}(\Theta_{\mathbf{k}(\omega)}(\omega)) = \min_{(k,n) \in \{1,2,\dots,K\} \times \mathbf{T}, \|\Theta_{k,n}(\omega)\|_\infty \le B} \mathscr{R}(\Theta_{k,n}(\omega))$$

(*cf.* Definitions 3.3.4 and 4.4.1). Then

$$\begin{aligned}
&\mathbb{E}\left[\int_{[a,b]^d} \left|\mathcal{A}^{\Theta_{k,1}}_{u,v}(x) - \mathcal{E}(x)\right| \mathbb{P}_{X_{\mathbf{1},0}^{0,0}}(\mathrm{d}x)\right]
&\quad \le \frac{6dc^2}{\min\{\mathbf{L}_1, \mathbf{L}_2, \dots, \mathbf{L}_{\mathbf{L}-1}\}^{1/d}} + \frac{5B^2\mathbf{L}\mathbf{L}(\|\mathbf{L}\|_\infty + 1)\ln(eM)}{M^{1/4}} + \frac{2\mathbf{L}(\|\mathbf{L}\|_\infty + 1)\mathbf{L}c^{\mathbf{L}+1}}{K(2\mathbf{L})^{-1}(|\mathbf{L}|_\infty + 1)^{-2}}
\end{aligned}$$

(*cf.* Lemma 15.1.1).

*Proof of Corollary 15.2.2*. Observe that Jensen’s inequality ensures that

$$\mathbb{E}\left[\int_{[a,b]^d} \left|\mathcal{A}^{\Theta_{k,1}}_{u,v}(x) - \mathcal{E}(x)\right| \mathbb{P}_{X_{\mathbf{1},0}^{0,0}}(\mathrm{d}x)\right] \le \mathbb{E}\left[\left(\int_{[a,b]^d} \left|\mathcal{A}^{\Theta_{k,1}}_{u,v}(x) - \mathcal{E}(x)\right|^2 \mathbb{P}_{X_{\mathbf{1},0}^{0,0}}(\mathrm{d}x)\right)^{1/2}\right].$$

This and Corollary 15.2.1 (applied with $p \sim 1$ in the notation of Corollary 15.2.1) establish (15.69). The proof of Corollary 15.2.2 is thus complete.

**Corollary 15.2.3.** *Let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, $M, d \in \mathbb{N}$, for every $k, n, j \in \mathbb{N}_0$ let $X_j^{k,n} \colon \Omega \rightarrow [0,1]^d$ and $Y_j^{k,n} \colon \Omega \rightarrow [0,1]$ be random variables, assume that $(X_j^{0,0}, Y_j^{0,0})$, $j \in \{1,2,\dots,M\}$, are i.i.d., for every $k, n \in \mathbb{N}_0$, $J \in \mathbb{N}$ let $\mathscr{R}_J^{k,n} \colon \mathbb{R}^{\mathbf{d}} \times \Omega \rightarrow [0,\infty)$ satisfy for all $\theta \in \mathbb{R}^{\mathbf{d}}$ that*

$$\mathscr{R}_J^{k,n}(\theta, \omega) = \frac{1}{J} \left[\sum_{i=1}^{J} \left|\mathcal{A}_{0,1}^{\Theta_{k,1}}(X_j^{k,n}(\omega)) - Y_j^{k,n}(\omega)\right|^2\right],$$

*let $\mathbf{d}, \mathbf{L} \in \mathbb{N}$, $\mathbf{1} = (\mathbf{1}_0, \mathbf{1}_1, \dots, \mathbf{1}_\mathbf{L}) \in \mathbb{N}^{\mathbf{L}+1}$ satisfy*

$$\mathbf{1}_0 = d, \qquad \mathbf{1}_\mathbf{L} = 1, \qquad \text{and} \qquad \mathbf{d} \ge \sum_{i=1}^{\mathbf{L}} \mathbf{1}_i(\mathbf{1}_{i-1} + 1),$$

*let $\mathcal{E} \colon [0,1]^d \rightarrow [0,1]$ satisfy $\mathbb{P}$-a.s. that*

$$\mathcal{E}(X_{\mathbf{1}}^{0,0}) = \mathbb{E}[\mathbb{Y}_1^{0,0} | X_{\mathbf{1}}^{0,0}],$$