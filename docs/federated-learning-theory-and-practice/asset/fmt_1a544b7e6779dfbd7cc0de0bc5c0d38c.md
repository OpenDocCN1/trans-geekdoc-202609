
## Lipschitz Continuity

Examples of Lipschitz continuous functions include norms, smoothed approximation of norms (e.g., $F(w): = \sum_{i = 1}^{p}{(w_{j}^{2} + \epsilon^{2})}^{1/2}$ for a small $\epsilon$), or continuous functions with a bounded domain. Note that when $F$ is convex, $M$-Lipschitz continuity is equivalent to $M$-bounded [sub]gradient, i.e., $\|\nabla F(w)\| \le M$ for all $w \in \mathbb{R}^{(p)}$. This assumption is usually used in subgradient-type or stochastic gradient-type methods.

## L-Smoothness

Function $F$ is called $L$-smooth if the gradient $\nabla F$ of $F$ satisfies

$$
\|\nabla F(w) - \nabla F(w')\| \le L\|w - w'\|, \quad \forall w, w' \in \mathbb{R}^{(p)}. \tag{1.9}
$$

If $w, w' \in \mathcal{W}$ for a compact domain $\mathcal{W}$ and $F$ is continuously differentiable, then $F$ is $L$-smooth on $\mathcal{W}$. This concept can be extended to an $L$-average smoothness in the finite-sum or stochastic settings. For instance, if $F(w): = \frac{1}{n}\sum_{i = 1}^{n}F_{i}(w)$, then we can modify [(1.9)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq10) as $\frac{1}{n}\sum_{i = 1}^{n}{\|\nabla F_{i}(w) - \nabla F_{i}(w')\|}^{2} \leqslant L^{2}{\| w - w'\|}^{2}$ for all $w, w' \in \mathbb{R}^{(p)}$. Alternatively, if $F(w) := \mathbb{E}[F(w, \xi)]$, then we can use $\mathbb{E}[\|\nabla F(w) - \nabla F(w')\|^2|w, w'] \le L^2\|w - w'\|^2$ for all $w, w' \in \mathbb{R}^{(p)}$. These assumptions are usually used in variance-reduction SGD methods, see, e.g., [52, 66]. Note that other extensions are possible, see, e.g., [34]. Verifying the $L$-smoothness is generally not straightforward. However, if $F(w): = \frac{1}{n}\sum_{i = 1}^{n}\ell_{i}(X_{i}^{\top}w - y_{i})$ as, e.g., in a generalized linear model, then we can verify the $L$-smoothness of $F$ by verifying the $L$-smoothness of each one-variable function $\ell_{i}$. This model is ubiquitous in machine learning.

One key property of [(1.9)](#Chp001_3-28_B9780443190377000089_split_001.xhtml#deq10) is the following bound:

$$
|F(w') - F(w) - \langle\nabla F(w), w' - w\rangle| \le \frac{L}{2}{\| w' - w\|}^{2}, \tag{1.10}
$$

which shows that $F$ can be globally upper bounded by a convex quadratic function and globally lower bounded by a concave quadratic function. If, additionally, $F$ is convex, then stronger bounds as well as the co-coerciveness of $\nabla F$ can be obtained, see, e.g., [45]. One can also extend the $L$-smoothness of $F$ to a Hölder smoothness as $\|\nabla F(w) - \nabla F(w')\| \le L\|w - w'\|^{(\nu)}$ for some $0 \le \nu \le 1$. This concept unifies both the $L$-smoothness ($\nu = 1$) and the bounded gradient ($\nu = 0$) conditions. It has been used in universal first-order methods for both deterministic and stochastic methods, e.g., [47].

## Convexity

Function $F$ is said to be $\mu$-[strongly] convex if

$$
F(\widehat{w}) \ge F(w) + \langle\nabla F(w), \widehat{w} - w\rangle + \frac{\mu}{2}{\|\widehat{w} - w\|}^{2}, \quad \forall w, \widehat{w} \in \mathbb{R}^{p}. \tag{1.11}
$$

Here, $\nabla F(w)$ can be a gradient or a subgradient of $F$ at $w$. This inequality shows that $F$ can be lower bounded by either a linear ($\mu = 0$) or a quadratic approximation ($\mu \ne 0$). If $\mu = 0$, then $F$ is just convex or merely convex. If $\mu > 0$, then $F$ is strongly convex, and $\mu$ is called the strong convexity parameter. If $\mu < 0$, then $F$ is called weakly convex. Convexity and strong convexity are key concepts in convex analysis, optimization, and related fields, see, e.g., [7, 57], and we do not further discuss them here.

These are three key and also basic assumptions to analyze the convergence of [(1.2)](#Chp001_3-28_B9780443190377000089_split_000.xhtml#deq2) and its variants. Nevertheless, other assumptions can also be exploited. For example, the following conditions are commonly used in different methods:

## Gradient Dominance and PL Condition

Function $F$ is called $\sigma$-gradient dominant if $F(w) - F(w^\star) \le \sigma\|\nabla F(w)\|^2$ for all $w \in \mathbb{R}^{(p)}$ and $w^\star$ is a minimizer of $F$. Clearly, if $F$ is strongly convex, then it is gradient dominant. However, there exist nonconvex functions that are gradient dominant. Note that one can consider local gradient dominance by limiting $w$ in a neighborhood of $w^\star$. We can also extend this concept to different variants. The gradient dominance condition allows us to obtain a convergence guarantee on the objective residual $F(\hat{w}) - F(w^\star)$ even in the nonconvex setting. Note that this condition is also called Polyak–Łojasiewicz (PL) condition. These conditions can be used to establish linear convergence or linear-like convergence rates (i.e., linear converge to a small neighborhood of an optimal solution) [30, 52].
