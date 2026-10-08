**Lemma 11.3.3.** *Let $d \in \mathbb{N}$. Then it holds for all $x, y \in \mathbb{R}^{d}$ that*

$$\|\mathfrak{A}_d(x) - \mathfrak{A}_d(y)\|_{\infty} \le \|x - y\|_{\infty} \tag{11.73}$$

*(cf. Definitions 1.2.5 and 3.3.4).*

*Proof of Lemma 11.3.3.* *Observe that Lemma 11.3.1 demonstrates (11.73). The proof of Lemma 11.3.3 is thus complete.* $\square$

**Lemma 11.3.4.** *Let $d \in \mathbb{N}$, $u \in [-\infty, \infty)$, $v \in (u, \infty]$. Then it holds for all $x, y \in \mathbb{R}^{d}$ that*

$$\|\mathfrak{C}_{u,v,d}(x) - \mathfrak{C}_{u,v,d}(y)\|_{\infty} \le \|x - y\|_{\infty} \tag{11.74}$$

*(cf. Definitions 1.2.10 and 3.3.4).*

*Proof of Lemma 11.3.4.* *Note that Lemma 11.3.1, Corollary 11.3.2, and the fact that for all $x \in \mathbb{R}$ it holds that $\max\{-\infty, x\} = x = \min\{x, \infty\}$ imply that for all $x, y \in \mathbb{R}$ it holds that*

$$
\begin{aligned}
|\mathfrak{c}_{u,v}(x) - \mathfrak{c}_{u,v}(y)| &= |\max\{u, \min\{x, v\}\} - \max\{u, \min\{y, v\}\} | \\
&\le |\min\{x, v\} - \min\{y, v\}| \le |x - y| 
\end{aligned}
\tag{11.75}
$$

*(cf. Definition 1.2.9).* *Hence, we obtain that for all $x = (x_1, x_2, \ldots, x_d)$, $y = (y_1, y_2, \ldots, y_d) \in \mathbb{R}^{d}$ it holds that*

$$
\begin{aligned}
\|\mathfrak{c}_{u,v,d}(x) - \mathfrak{c}_{u,v,d}(y)\|_{\infty} &= \max_{i \in \{1, 2, \ldots, d\}} |\mathfrak{c}_{u,v}(x_i) - \mathfrak{c}_{u,v}(y_i)| \\
&\le \max_{i \in \{1, 2, \ldots, d\}} |x_i - y_i| = \|x - y\|_{\infty}
\end{aligned}
\tag{11.76}
$$

*(cf. Definitions 1.2.10 and 3.3.4).* *The proof of Lemma 11.3.4 is thus complete.* $\square$

**Lemma 11.3.5** *(Row sum norm, operator norm induced by the maximum norm).* *Let $a, b \in \mathbb{N}$, $M = (M_{i,j})_{(i,j) \in \{1, \ldots, a\} \times \{1, 2, \ldots, b\}} \in \mathbb{R}^{a \times b}$. Then*

$$
\sup_{v \in \mathbb{R}^{b} \setminus \{0\}} \left[ \frac{\|Mv\|_{\infty}}{\|v\|_{\infty}} \right] = \max_{i \in \{1, 2, \ldots, a\}} \left[ \sum_{j=1}^{b} |M_{i,j}| \right] \le b \left[ \max_{i \in \{1, \ldots, a\}} \max_{j \in \{1, \ldots, b\}} |M_{i,j}| \right] \tag{11.77}
$$

*(cf. Definition 3.3.4).*