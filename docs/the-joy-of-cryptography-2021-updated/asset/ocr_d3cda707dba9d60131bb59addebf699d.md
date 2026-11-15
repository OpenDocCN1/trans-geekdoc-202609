| $\mathcal{M} = \Sigma.\mathcal{M}$ | Share(m): | Reconstruct(s1, s2): |
|---|---|---|
| $t=2$ | $s_1 \leftarrow \Sigma.KeyGen$ | |
| $n=2$ | $s_2 \leftarrow \Sigma.Enc(s_1, m)$ | return $\Sigma.Dec(s_1, s_2)$ |
| | return $(s_1, s_2)$ | |

# 3.3 Polynomial Interpolation

You are probably familiar with the fact that two points determine a line (in Euclidean geometry). It is also true that 3 points determine a parabola, and so on. The next secret-sharing scheme we discuss is based on the following principle:

$d + 1$ points determine a *unique* degree-$d$ polynomial.

A note on terminology: If $f$ is a polynomial that can be written as $f(\boldsymbol{x}) = \sum_{i=0}^d f_i x^i$, then we say that $f$ is a **degree-$d$** polynomial. It would be more technically correct to say that the degree of $f$ is *at most $d$* since we allow the leading coefficient $f_d$ to be zero. For convenience, we’ll stick to saying “degree-$d$” to mean “degree at most $d$.”

# Polynomials Over the Reals

Theorem 3.8 (Poly Interpolation) Let $\{(x_1, y_1), \dots, (x_{d+1}, y_{d+1})\} \subseteq \mathbb{R}^2$ be a set of points whose $x_i$ values are all distinct. Then there is a **unique** degree-$d$ polynomial $f$ with real coefficients that satisfies $y_i = f(x_i)$ for all $i$.

Proof To start, consider the following polynomial:

\(\ell_1(\boldsymbol{x}) = \frac{(\boldsymbol{x} - \boldsymbol{x}_2)(\boldsymbol{x} - \boldsymbol{x}_3) \cdots (\boldsymbol{x} - \boldsymbol{x}_{d+1})}{(\boldsymbol{x}_1 - \boldsymbol{x}_2)(\boldsymbol{x}_1 - \boldsymbol{x}_3) \cdots (\boldsymbol{x}_1 - \boldsymbol{x}_{d+1})}\).

The notation is potentially confusing. $\ell_1$ is a polynomial with formal variable $\boldsymbol{x}$ (written in bold). The non-bold $x_i$ values are just plain numbers (scalars), given in the theorem statement. Therefore the numerator in $\ell_1$ is a degree-$d$ polynomial in $\boldsymbol{x}$. The denominator is just a scalar, and since all of the $x_i$’s are distinct, we are not dividing by zero. Overall, $\ell_1$ is a degree-$d$ polynomial.

What happens when we evaluate $\ell_1$ at one of the special $x_i$ values?

+   - Evaluating $\ell_1(x_1)$ makes the numerator and denominator the same, so $\ell_1(x_1) = 1$.
+   - Evaluating $\ell_1(x_i)$ for $i \neq 1$ leads to a term $(x_i - x_i)$ in the numerator, so $\ell_1(x_i) = 0$.

Of course, $\ell_1$ can be evaluated at any point (not just the special points $x_1, \dots, x_{d+1}$), but we don’t care about what happens in those cases.

We can similarly define other polynomials $\ell_j$:

\(\ell_j(\boldsymbol{x}) = \frac{(\boldsymbol{x} - \boldsymbol{x}_1) \cdots (\boldsymbol{x} - \boldsymbol{x}_{j-1})(\boldsymbol{x} - \boldsymbol{x}_{j+1}) \cdots (\boldsymbol{x} - \boldsymbol{x}_{d+1})}{(\boldsymbol{x}_j - \boldsymbol{x}_1) \cdots (\boldsymbol{x}_j - \boldsymbol{x}_{j-1})(\boldsymbol{x}_j - \boldsymbol{x}_{j+1}) \cdots (\boldsymbol{x}_j - \boldsymbol{x}_{d+1})}\).

The pattern is that the numerator is “missing” the term $(\boldsymbol{x} - \boldsymbol{x}_j)$ and the denominator is missing the term $(x_j - x_j)$, because we don’t want a zero in the denominator. Polynomials