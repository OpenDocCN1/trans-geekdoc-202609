
Let $x_1, \ldots, x_n$ be iid non-degenerate random variables and denote their maximum by $M_n := \max\{x_1, \ldots, x_n\}$. Two distribution functions $F(x)$ and $G(x)$ are said to be of the *same type* if there exist $a > 0$ and $b \in \mathbb{R}$ such that $F(x) = G(ax + b)$ for all $x \in \mathbb{R}$. The *Fisher–Tippett theorem* [\[18\]](#c08.xhtml#c08-bib-0018), one of the cornerstone results of EVT, asserts that if there exist norming constants $a_n > 0$ and $b_n \in \mathbb{R}$, for $n = 1, 2, \ldots$ and some non-degenerate distribution function $H$ such that

[(8.17)](#c08.xhtml#R_c08-disp-0078)
$$
a_n^{-1}(M_n - b_n) \xrightarrow{d} H \quad \text{as } n \to \infty,
$$

then $H$ must belong to one of the classes of distributions being of the same type as one of the following three types of distribution functions: for $\alpha > 0$,

(i) Fréchet: $\Phi_\alpha(x) = \begin{cases} 0, & x \le 0 \\ \exp\{-x^{-\alpha}\}, & x > 0 \end{cases}$;

(ii) Gumbel: $\Lambda(x) = \exp\{-e^{-x}\}, \quad x \in \mathbb{R}$;

(iii) Weibull: $\Psi_\alpha(x) = \begin{cases} \exp\{-(-x)^\alpha\}, & x < 0 \\ 1, & x \ge 0 \end{cases}$.
