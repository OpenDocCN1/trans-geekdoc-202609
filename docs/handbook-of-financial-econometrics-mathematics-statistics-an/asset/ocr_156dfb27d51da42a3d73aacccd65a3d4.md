Widder, D. V. (1961). *Advanced Calculus* 2nd Edition, Prentice-Hall Inc.

Zhang, P. G. (1994). Bounds for Option Prices and Expected Payoffs. *Review of Quantitative Finance and Accounting*, 4(2), 179–198.

Zuluaga, L. F., Peña, J. and Du, D. (2009). Third-Order Extensions of Lo’s Semiparametric Bound for European Call Options. *European Journal of Operational Research*, 198, 557–570.

# Appendix 7A

**Proofs of Proposition 7.1–7.3.** If any distribution function $F(x)$ is continuous, then there is a one to one correspondence between $0 \leq x < +\infty$ and $0 \leq F(x) < 1$, and the inverse function of $F(x)$ exists uniquely. Let $x=F^{-1}(x)=x(F')$ and $s=F(x)$. The five moments (7.3)–(7.7) become

\[
\int_0^1 1\,dF=1,\qquad \int_0^1 x\,dF=\mu,\qquad \int_0^1 (x-\mu)^2\,dF=\sigma^2,\qquad \int_0^1 (x-\mu)^3\,dF=k\sigma^3,
\]

\[
\int_0^1 (x-\mu)^4\,dF=\eta\sigma^4. \tag{7A.1}
\]

let $Q(x)=\operatorname{Max}(x-K,0)$. $Q(x)$ is a continuous function of $x$. Using Schwarz inequality (see Widder (1961, p. 364)), we get

\[
\left(\int_\beta^\alpha Q(x)\,dF\right)^2 \leq \left\{\int_\beta^\alpha [Q(x)]^2\,dF\right\}\left\{\int_\beta^\alpha 1^2\,dF\right\}
\\
= (\alpha-\beta)\int_\beta^\alpha [Q(x)]^2\,dF, \tag{7A.2}
\]

where $\alpha$ and $\beta$ are arbitrary real numbers satisfying $\alpha \geq \beta$.

Using equation (7A.2) we get the following inequality

\[
(R_C)^2=\left\{\int_s^1 \operatorname{Max}(x-K,0)\,dF\right\}^2 \leq (1-s)\int_s^1 (x-K)^2\,dF. \tag{7A.3}
\]

Squaring both sides of equation (7A.3) and using equation (7A.2) again yield

\[
(R_C)^4 \leq (1-s)^3\int_s^1 (x-K)^4\,dF,
\]

or

\[
\frac{(R_C)^4}{(1-s)^3}\leq\int_s^1 (x-K)^4\,dF. \tag{7A.4}
\]

Similarly, we get the inequality for the expected payoff of the put as follows:

\[
\frac{(R_P)^4}{s^3}\leq\int_s^1 (x-K)^4\,dF. \tag{7A.5}
\]