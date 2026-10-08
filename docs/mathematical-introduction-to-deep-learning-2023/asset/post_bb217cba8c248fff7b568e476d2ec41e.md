
## 15.2 Full strong error analysis with optimization via SGD with random initializations

**Corollary 15.2.1.** Let $(\Omega,\mathcal{F},\mathbb{P})$ be a probability space, let $M, d \in \mathbb{N}$, $a,u \in \mathbb{R}$, $b \in (a, \infty)$, $v \in (u, \infty)$, for every $k,n,j \in \mathbb{N}_0$ let $X_j^{k,n}\colon \Omega \to [a,b]^d$ and $Y_j^{k,n}\colon \Omega \to [u,v]$ be random variables, assume that $(X_j^{0,0},Y_j^{0,0}$, $j \in \{1,2,\ldots,M\}$, are i.i.d, let $\mathbf{d},\mathbf{L} \in \mathbb{N}$, $\mathbf{l} = (\mathbf{l}_0,\mathbf{l}_1,\ldots,\mathbf{l}_{\mathbf{L}}) \in \mathbb{N}^{\mathbf{L}+1}$ satisfy

$$
\mathbf{l}_0 = d, \quad \mathbf{l}_{\mathbf{L}} = 1, \quad \text{and} \quad \mathbf{d} \ge \sum_{i=1}^{\mathbf{L}}\mathbf{l}_i(\mathbf{l}_{i-1}+1). \tag{15.54}
$$

For every $k,n \in \mathbb{N}_0$, $J \in \mathbb{N}$ let $\mathscr{R}_J^{k,n}\colon \mathbb{R}^{\mathbf{d}} \times \Omega \to [0, \infty)$ satisfy for all $\theta \in \mathbb{R}^{\mathbf{d}}$, $\omega \in \Omega$ that

$$
\mathscr{R}_J^{k,n}(\theta,\omega) = \frac{1}{J}\bigg[\sum_{j=1}^{J}\bigl|\mathscr{N}^{\Theta_{u,v}^{0,1}}(X_j^{k,n}(\omega)) - Y_j^{k,n}(\omega)\bigr|^2\bigg], \tag{15.55}
$$

let $\mathcal{E}\colon [a,b]^d \to [u,v]$ satisfy $\mathbb{P}$-a.s. that

$$
\mathcal{E}(X_1^{0,0}) = \mathbb{E}[Y_1^{0,0}|X_1^{0,0}], \tag{15.56}
$$

let $L \in \mathbb{R}$ satisfy for all $x,y \in [a,b]^d$ that $|\mathcal{E}(x)-\mathcal{E}(y)| \le L\|x-y\|_1$, let $(\mathbf{J}_n)_{n \in \mathbb{N}} \subseteq \mathbb{N}$, for every $k,n \in \mathbb{N}$ let $\mathcal{G}_J^{k,n}\colon \mathbb{R}^{\mathbf{d}} \times \Omega \to \mathbb{R}^{\mathbf{d}}$ satisfy for all $\omega \in \Omega$, $\theta \in \{\theta \in \mathbb{R}^{\mathbf{d}}\colon \mathscr{R}_J^{k,n}(\cdot,\omega)\colon \mathbb{R}^{\mathbf{d}} \to [0, \infty)$ is differentiable at $\theta\}$ that

$$
\mathcal{G}_J^{k,n}(\theta,\omega) = (\nabla_\theta\mathscr{R}_J^{k,n})(\theta,\omega), \tag{15.57}
$$

let $K \in \mathbb{N}$, $c \in [\max\{1,L,|a|,|b|,2|u|,2|v|\},\infty)$, $B \in [c,\infty)$, for every $k,n \in \mathbb{N}_0$ let $\Theta_{k,n}\colon \Omega \to \mathbb{R}^{\mathbf{d}}$ be a random variable, assume $\bigcup_{k=1}^{\infty}\Theta_{k,0}(\Omega) \subseteq [-B,B]^{\mathbf{d}}$, assume that $\Theta_{k,0}$, $k \in \{1, 2, \dots, K\}$, are $i.i.d.$, assume that $\Theta_{1,0}$ is continuously uniformly distributed on $[-c, c]^{\mathbf{d}}$, let $(\gamma_n)_{n \in \mathbb{N}} \subseteq \mathbb{R}$ satisfy for all $k, n \in \mathbb{N}$ that

$$
\Theta_{k,n} = \Theta_{k,n-1} - \gamma_n \mathcal{G}^{k,n}(\Theta_{k,n-1}), \qquad\qquad\qquad\qquad\qquad\qquad (15.58)
$$

let $N \in \mathbb{N}$, $\mathbf{T} \subseteq \{0, 1, \dots, N\}$ satisfy $0 \in \mathbf{T}$, let $\mathbf{k} \colon \Omega \to (\mathbb{N}_0)^2$ be a random variable, and assume for all $\omega \in \Omega$ that

$$
\mathbf{k}(\omega) \in \{(k, n) \in \{1, 2, \dots, K\} \times \mathbf{T} \colon \|\Theta_{k,n}(\omega)\|_\infty \le B\} \qquad\qquad\qquad\qquad (15.59)
$$

and

$$
\mathscr{R}(\Theta_{\mathbf{k}(\omega)}(\omega)) = \min_{(k,n) \in \{1, \dots, K\} \times \mathbf{T}, \|\Theta_{k,n}(\omega)\|_\infty \le B} \mathscr{R}(\Theta_{k,n}(\omega)) \qquad\qquad\qquad\qquad (15.60)
$$

(cf. Definitions 3.3.4 and 4.4.1). Then it holds for all $p \in (0, \infty)$ that

$$
\left(\mathbb{E}\left[\left(\int_{[a,b]^d} \mathcal{K}_{u,v}^{\Theta_{k,1}}(x) - \mathcal{E}(x)\right|^2 \mathbb{P}_{X_1^{0,0}}(dx)\right]^{p/2}\right]^{1/p} \qquad\qquad\qquad\qquad (15.61)
$$

$$
\le \frac{6d c^2}{\left[\min\left(\{\mathbf{L}\} \cup \{l_i \colon i \in \mathbf{N} \cap [0, \mathbf{L}]\}\right)\right]^d} + \frac{2\mathbf{L} (\|\mathbf{l}\|_\infty + 1) \mathbf{L}^{\mathbf{L}+1} \max\{1, p\}}{K(2\mathbf{L} - (\|\mathbf{l}\|_\infty + 1)) - 2}
$$

$$
+ \frac{5B^2 \mathbf{L} (\|\mathbf{l}\|_\infty + 1) \max\{p, \ln(\mathcal{E}M)\}}{M^{1/4}}
$$

(cf. Lemma 15.1.1).

Proof of Corollary 15.2.1. Note that Corollary 15.1.6 (applied with $(X_j)_{j \in \mathbb{N}}$ and $(X_j^{0,0})_{j \in \mathbb{N}}$, $(Y_j)_{j \in \mathbb{N}}$ and $(Y_j^{0,0})_{j \in \mathbb{N}}$, $\mathscr{R}$ and $\mathscr{R}_M^{0,0}$ in the notation of Corollary 15.1.6) implies (15.61). The proof of Corollary 15.2.1 is thus complete. $\square$

**Corollary 15.2.2.** Let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $M, d \in \mathbb{N}$, $a, u \in \mathbb{R}$, $b \in (a, \infty)$, $v \in (u, \infty)$, for every $k, n, j \in \mathbb{N}_0$ let $X_j^{k,n} \colon \Omega \to [a, b]^d$ and $Y_j^{k,n} \colon \Omega \to [u, v]$ be random variables, assume that $(X_j^{0,0}, Y_j^{0,0})$, $j \in \{1, 2, \dots, M\}$, are $i.i.d.$, let $\mathbf{d}, \mathbf{L} \in \mathbb{N}$, $\mathbf{l} = (\mathbf{l}_0, \mathbf{l}_1, \dots, \mathbf{l}_\mathbf{L}) \in \mathbb{N}^{\mathbf{L}+1}$ satisfy

$$
\mathbf{l}_0 = d, \qquad\qquad \mathbf{l}_\mathbf{L} = 1, \qquad\qquad \text{and} \qquad\qquad \mathbf{d} \ge \sum_{i=1}^{\mathbf{L}} \mathbf{l}_i (\mathbf{l}_{i-1} + 1), \qquad\qquad\qquad\qquad (15.62)
$$

for every $k, n \in \mathbb{N}_0$, $J \in \mathbb{N}$ let $\mathcal{R}_J^{k,n} \colon \mathbb{R}^d \times \Omega \to [0, \infty)$ satisfy for all $\theta \in \mathbb{R}^d$ that

$$
\mathcal{R}_J^{k,n}(\theta) = \frac{1}{J} \left[\sum_{j=1}^{J} \mathbf{l}_{u,v}^{\theta, 1} (X_j^{k,n} - Y_j^{k,n})^2\right], \qquad\qquad\qquad\qquad (15.63)
$$

let $\mathcal{E} \colon [a, b]^d \to [u, v]$ satisfy $\mathbb{P}$-a.s. that

$$
\mathcal{E}(X_1^{0,0}) = \mathbb{E}[X_1^{0,0} | Y_1^{0,0}], \qquad\qquad\qquad\qquad\qquad\qquad (15.64)
$$

let $L \in \mathbb{R}$ satisfy for all $x, y \in [a, b]^d$ that $|\mathcal{E}(x) - \mathcal{E}(y)| \le L\|x - y\|_1$, let $(\mathbf{J}_n)_{n \in \mathbb{N}} \subseteq \mathbb{N}$, for every $k, n \in \mathbb{N}$ let $\mathcal{G}^{k,n} \colon \mathbb{R}^d \times \Omega \to \mathbb{R}^d$ satisfy for all $\omega \in \Omega$, $\theta \in \{v \in \mathbb{R}^d \colon (\mathcal{R}_J^{k,n}(\cdot, \omega) \colon \mathbb{R}^d \to [0, \infty) \text{ is differentiable at } v\}$ that

$$
\mathcal{G}^{k,n}(\theta, \omega) = (\nabla_\theta \mathcal{R}_{\mathbf{J}_n}^{k,n})(\theta, \omega), \qquad\qquad\qquad\qquad\qquad\qquad (15.65)
$$

let $K \in \mathbb{N}$, $c \in [\max\{1, L, |a|, |b|, 2|u|, 2|v|\}, \infty)$, $B \in [c, \infty)$, for every $k, n \in \mathbb{N}_0$ let $\Theta_{k, n} \colon \Omega \rightarrow \mathbb{R}^{\mathbf{d}}$ be a random variable, assume $\bigcup_{k=1}^{\infty} \Theta_{k, 0}(\Omega) \subseteq [-B, B]^{\mathbf{d}}$, assume that $\Theta_{k,0}$, $k \in \{1,2,\dots,K\}$, are i.i.d., assume that $\Theta_{1,0}$ is continuously uniformly distributed on $[-c, c]^{\mathbf{d}}$, let $(\gamma_n)_{n \in \mathbb{N}} \subseteq \mathbb{R}$ satisfy for all $k, n \in \mathbb{N}$ that

$$
\Theta_{k,n} = \Theta_{k,n-1} - \gamma_n \mathcal{G}^{k,n}(\Theta_{k,n-1}),
$$

let $N \in \mathbb{N}$, $\mathbf{T} \subseteq \{0,1,\dots,N\}$ satisfy $0 \in \mathbf{T}$, let $\mathbf{k} \colon \Omega \rightarrow (\mathbb{N}_0)^2$ be a random variable, and assume for all $\omega \in \Omega$ that

$$
\mathbf{k}(\omega) \in \{(k, n) \in \{1,2,\dots,K\} \times \mathbf{T} \colon \|\Theta_{k,n}(\omega)\|_\infty \le B\}
$$

and
$$
\mathscr{R}(\Theta_{\mathbf{k}(\omega)}(\omega)) = \min_{(k,n) \in \{1,2,\dots,K\} \times \mathbf{T}, \|\Theta_{k,n}(\omega)\|_\infty \le B} \mathscr{R}(\Theta_{k,n}(\omega))
$$

(*cf.* Definitions 3.3.4 and 4.4.1). Then

$$
\begin{aligned}
&\mathbb{E}\left[\int_{[a,b]^d} \left|\mathcal{A}^{\Theta_{k,1}}_{u,v}(x) - \mathcal{E}(x)\right| \mathbb{P}_{X_{1,0}^{0,0}}(\mathrm{d}x)\right]
&\quad \le \frac{6dc^2}{\min\{\mathbf{L}_1, \mathbf{L}_2, \dots, \mathbf{L}_{\mathbf{L}-1}\}^{1/d}} + \frac{5B^2\mathbf{L}\mathbf{L}(\|\mathbf{L}\|_\infty + 1)\ln(eM)}{M^{1/4}} + \frac{2\mathbf{L}(\|\mathbf{L}\|_\infty + 1)\mathbf{L}c^{\mathbf{L}+1}}{K(2\mathbf{L})^{-1}(|\mathbf{L}|_\infty + 1)^{-2}}
\end{aligned}
$$

(*cf.* Lemma 15.1.1).

*Proof of Corollary 15.2.2*. Observe that Jensen’s inequality ensures that

$$
\mathbb{E}\left[\int_{[a,b]^d} \left|\mathcal{A}^{\Theta_{k,1}}_{u,v}(x) - \mathcal{E}(x)\right| \mathbb{P}_{X_{1,0}^{0,0}}(\mathrm{d}x)\right] \le \mathbb{E}\left[\left(\int_{[a,b]^d} \left|\mathcal{A}^{\Theta_{k,1}}_{u,v}(x) - \mathcal{E}(x)\right|^2 \mathbb{P}_{X_{1,0}^{0,0}}(\mathrm{d}x)\right)^{1/2}\right].
$$

This and Corollary 15.2.1 (applied with $p \sim 1$ in the notation of Corollary 15.2.1) establish (15.69). The proof of Corollary 15.2.2 is thus complete.

**Corollary 15.2.3.** *Let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, $M, d \in \mathbb{N}$, for every $k, n, j \in \mathbb{N}_0$ let $X_j^{k,n} \colon \Omega \rightarrow [0,1]^d$ and $Y_j^{k,n} \colon \Omega \rightarrow [0,1]$ be random variables, assume that $(X_j^{0,0}, Y_j^{0,0})$, $j \in \{1,2,\dots,M\}$, are i.i.d., for every $k, n \in \mathbb{N}_0$, $J \in \mathbb{N}$ let $\mathscr{R}_J^{k,n} \colon \mathbb{R}^{\mathbf{d}} \times \Omega \rightarrow [0,\infty)$ satisfy for all $\theta \in \mathbb{R}^{\mathbf{d}}$ that*

$$
\mathscr{R}_J^{k,n}(\theta, \omega) = \frac{1}{J} \left[\sum_{i=1}^{J} \left|\mathcal{A}_{0,1}^{\Theta_{k,1}}(X_j^{k,n}(\omega)) - Y_j^{k,n}(\omega)\right|^2\right],
$$

*let $\mathbf{d}, \mathbf{L} \in \mathbb{N}$, $\mathbf{l} = (\mathbf{l}_0, \mathbf{l}_1, \dots, \mathbf{l}_\mathbf{L}) \in \mathbb{N}^{\mathbf{L}+1}$ satisfy*

$$
\mathbf{l}_0 = d, \qquad \mathbf{l}_\mathbf{L} = 1, \qquad \text{and} \qquad \mathbf{d} \ge \sum_{i=1}^{\mathbf{L}} \mathbf{l}_i(\mathbf{l}_{i-1} + 1),
$$

*let $\mathcal{E} \colon [0,1]^d \rightarrow [0,1]$ satisfy $\mathbb{P}$-a.s. that*

$$
\mathcal{E}(X_{1}^{0,0}) = \mathbb{E}[\mathbb{Y}_1^{0,0} | X_{1}^{0,0}],
$$
