Observe that Corollary 12.1.18 and (12.57) ensure that

$\begin{aligned}\mathbb{P}\left(\left[\sum_{n=1}^{N}\left(X_{n}-\mathbb{E}\left[X_{n}\right]\right)\leq-\varepsilon\right)&=\mathbb{P}\left(\left[\sum_{n=1}^{N}\left(-X_{n}-\mathbb{E}\left[-X_{n}\right]\right)\geq \varepsilon\right)\\&=\mathbb{P}\left(\left[\sum_{n=1}^{N}\left(\mathbf{X}_{n}-\mathbb{E}\left[\mathbf{X}_{n}\right]\right)\geq \varepsilon\right)\leq \exp \left(\frac{-2 \varepsilon^{2}}{\sum_{n=1}^{N}\left(b_{n}-a_{n}\right)^{2}}\right).\end{aligned} \tag{12.58}$

The proof of Corollary 12.1.19 is thus complete.

# 12.1.5.5 Hoeffding's inequality

**Corollary 12.1.20.** Let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $N \in \mathbb{N}$, $\varepsilon \in[0, \infty)$, $a_{1}, a_{2}, \ldots$, $a_{N} \in \mathbb{R}$, $b_{1} \in\left[a_{1}, \infty\right)$, $b_{2} \in\left[a_{2}, \infty\right)$, $\ldots$, $b_{N} \in\left[a_{N}, \infty\right)$ satisfy $\sum_{n=1}^{N}\left(b_{n}-a_{n}\right)^{2} \neq 0$, and let $X_{n}: \Omega \rightarrow\left[a_{n}, b_{n}\right]$, $n \in\{1,2, \ldots, N\}$, be independent random variables. Then

$\begin{equation*}\mathbb{P}\left(\left|\sum_{n=1}^{N}\left(X_{n}-\mathbb{E}\left[X_{n}\right]\right)\right|\geq \varepsilon\right)\leq 2 \exp \left(\frac{-2 \varepsilon^{2}}{\sum_{n=1}^{N}\left(b_{n}-a_{n}\right)^{2}}\right).\tag{12.59}\end{equation*}$

*Proof of Corollary 12.1.20.* Observe that

$\begin{aligned}\mathbb{P}\left(\left|\sum_{n=1}^{N}\left(X_{n}-\mathbb{E}\left[X_{n}\right]\right)\right|\geq \varepsilon\right)\\&=\mathbb{P}\left(\left\{\left[\sum_{n=1}^{N}\left(X_{n}-\mathbb{E}\left[X_{n}\right]\right)\right] \geq \varepsilon\right\} \cup\left\{\left[\sum_{n=1}^{N}\left(X_{n}-\mathbb{E}\left[X_{n}\right]\right)\right] \leq-\varepsilon\right\}\right)\\&\leq \mathbb{P}\left(\left[\sum_{n=1}^{N}\left(X_{n}-\mathbb{E}\left[X_{n}\right]\right)\right] \geq \varepsilon\right)+\mathbb{P}\left(\left[\sum_{n=1}^{N}\left(X_{n}-\mathbb{E}\left[X_{n}\right]\right)\right] \leq-\varepsilon\right).\end{aligned} \tag{12.60}$

Combining this with Corollary 12.1.18 and Corollary 12.1.19 establishes (12.59). The proof of Corollary 12.1.20 is thus complete.

**Corollary 12.1.21.** Let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $N \in \mathbb{N}$, $\varepsilon \in[0, \infty)$, $a_{1}, a_{2}, \ldots$, $a_{N} \in \mathbb{R}$, $b_{1} \in\left[a_{1}, \infty\right)$, $b_{2} \in\left[a_{2}, \infty\right)$, $\ldots$, $b_{N} \in\left[a_{N}, \infty\right)$ satisfy $\sum_{n=1}^{N}\left(b_{n}-a_{n}\right)^{2} \neq 0$, and let $X_{n}: \Omega \rightarrow\left[a_{n}, b_{n}\right]$, $n \in\{1,2, \ldots, N\}$, be independent random variables. Then

$\begin{equation*}\mathbb{P}\left(\frac{1}{N}\left|\sum_{n=1}^{N}\left(X_{n}-\mathbb{E}\left[X_{n}\right]\right)\right|\geq \varepsilon\right)\leq 2 \exp \left(\frac{-2 \varepsilon^{2} N^{2}}{\sum_{n=1}^{N}\left(b_{n}-a_{n}\right)^{2}}\right).\tag{12.61}\end{equation*}$