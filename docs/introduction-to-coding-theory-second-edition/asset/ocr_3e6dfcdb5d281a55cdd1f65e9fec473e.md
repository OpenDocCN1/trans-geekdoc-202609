# PROOF

Let $A = (x)_\infty$, an effective divisor of degree $n$. By definition, $x \in L(A)$. It is easy to see that $y \in L(A)$. In fact, let $P$ be such that $v_P(x) = -m < 0$. We want to show that $v_P(y) \ge -m$. Divide the irreducible equation by $x^n$ and work with $z = y/x$. We want to show that $z$ is defined at $P$. In fact,

$$z^n + \frac{f_1(x)}{x} z^{n-1} + \cdots + \frac{f_{n-1}(x)}{x^{n-1}} z + \frac{f_n(x)}{x^n} = 0.$$

Then $f_j(x)/x^j$ is a polynomial in $1/x$ and therefore satisfies $v_P(f_j(x)/x^j) \ge 0$. This shows the claim.

Let $l > n$ be large enough such that $\dim(lA) = l n + 1 - g$. Then $lA$ contains the linearly independent elements $x^i y^j$ where $j = 0, \dots, n-1$ and $0 \le i \le l - j$. Comparison yields the claim.