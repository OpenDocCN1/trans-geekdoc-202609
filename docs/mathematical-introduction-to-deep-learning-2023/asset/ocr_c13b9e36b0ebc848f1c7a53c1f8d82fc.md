Therefore, we obtain for all \(\theta \in \mathbb{R}\) with \(|\theta| \leq \frac{\varepsilon}{4}\) that

> \begin{align}
\sum_{k=N+1}^{\infty} |a_{k}| |\theta|^{k} &\leq |\theta|^{N+1} \left[ \left\{ \max\{ |a_{1}|, |a_{2}|, \ldots, |a_{M}| \} \right\} \left( \sum_{k=0}^{\infty} \left| \frac{1}{4} \right|^{k} \right) + \left( 2\varepsilon^{-1} \right)^{N+1} \left( \sum_{k=1}^{\infty} \left| \frac{1}{2} \right|^{k} \right) \right] \\
&\leq |\theta|^{N+1} \left[ 2\left\{ \max\{ |a_{1}|, |a_{2}|, \ldots, |a_{M}| \} + \left( 2\varepsilon^{-1} \right)^{N+1} \right\} \right].
\end{align}

(9.84)

This demonstrates that for all \(\theta \in \mathbb{R}\) with \(|\theta| \leq \delta\) it holds that

> \begin{align}
\sum_{k=N+1}^{\infty} |a_{k}| |\theta|^{k} \leq |a_{N}| |\theta|^{N}.
\end{align}

(9.85)

Hence, we obtain for all \(\theta \in \mathbb{R}\) with \(|\theta| \leq \delta\) that

> \begin{align}
\left| \mathcal{L}(\theta) - \mathcal{L}(0) \right| = \left| \sum_{k=N}^{\infty} a_{k}\theta^{k} \right| \leq |a_{N}| |\theta|^{N} + \sum_{k=N+1}^{\infty} |a_{k}| |\theta|^{k} \leq 2|a_{N}| |\theta|^{N}.
\end{align}

(9.86)

Next observe that the assumption that for all \(k \in \mathbb{N} \cap [M, \infty)\) it holds that \(k|a_{k}| \leq \left( 2\varepsilon^{-1} \right)^{k}\) ensures that for all \(K \in \mathbb{N} \cap [M, \infty)\) it holds that

> \begin{align}
\sum_{k=N+1}^{N+K+1} k|a_{k}| |\theta|^{k-1}
&= |\theta|^{N} \left[ \left( \sum_{k=0}^{M-N-1} (k+N+1)|a_{k+N+1}| |\theta|^{k} \right) + \left( \sum_{k=M-N}^{K} (k+N+1)|a_{k+N+1}| |\theta|^{k} \right) \right] \\
&\leq |\theta|^{N} \left[ \max\{ |a_{1}|, 2|a_{2}|, \ldots, M|a_{M}| \} \left( \sum_{k=0}^{M-N-1} |\theta|^{k} \right) + \left( \sum_{k=M-N}^{K} \left( 2\varepsilon^{-1} \right)^{k+N+1} |\theta|^{k} \right) \right] \\
&\leq |\theta|^{N} \left[ \max\{ |a_{1}|, 2|a_{2}|, \ldots, M|a_{M}| \} \left( \sum_{k=0}^{M-N-1} |\theta|^{k} \right) + \left( 2\varepsilon^{-1} \right)^{N+1} \left( \sum_{k=M-N}^{K-N} \left| 2\varepsilon^{-1}\theta \right|^{k} \right) \right].
\end{align}

(9.87)

Therefore, we obtain for all \(\theta \in \mathbb{R}\) with \(|\theta| \leq \frac{\varepsilon}{4}\) that

> \begin{align}
\sum_{k=N+1}^{\infty} k|a_{k}| |\theta|^{k-1}
&\leq |\theta|^{N} \left[ \max\{ |a_{1}|, 2|a_{2}|, \ldots, M|a_{M}| \} \left( \sum_{k=0}^{\infty} \left| \frac{1}{4} \right|^{k} \right) + \left( 2\varepsilon^{-1} \right)^{N+1} \left( \sum_{k=1}^{\infty} \left| \frac{1}{2} \right|^{k} \right) \right] \\
&\leq |\theta|^{N} \left[ 2\left\{ \max\{ |a_{1}|, 2|a_{2}|, \ldots, M|a_{M}| \} + \left( 2\varepsilon^{-1} \right)^{N+1} \right\} \right].
\end{align}

(9.88)

This establishes that for all \(\theta \in \mathbb{R}\) with \(|\theta| \leq \delta\) it holds that

> \begin{align}
\sum_{k=N+1}^{K} k|a_{k}| |\theta|^{k-1} \leq |a_{N}| |\theta|^{N-1}.
\end{align}

(9.89)