# 3.3 Derive the mean, mode, and variance of a Beta$(a,b)$ distribution.

The beta distribution has support over the interval $[0,1]$ and is defined as follows:

$$\operatorname{Beta}(x\mid a,b)=\frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)}x^{a-1}(1-x)^{b-1}$$

We have the following expressions for the mean, mode, and variance of the Beta distribution:

$$E[X]=\frac{a}{a+b}\qquad \operatorname{mode}[X]=\frac{a-1}{a+b-2}\qquad \operatorname{VAR}(X)=\frac{ab}{(a+b)^2(a+b+1)}$$

# 4.1 Prove the following binomial identity: $C(n,k)=C(n-1,k-1)+C(n-1,k)$.

We’ll be using an algebraic proof. By definition, expanding the left-hand side, we have the following:

$$\begin{aligned}
\binom{n-1}{k-1}+\binom{n-1}{k}
&=\frac{(n-1)!}{(n-k)!\,(k-1)!}+\frac{(n-1)!}{(n-k-1)!\,k!}\\
&=\frac{(n-1)!}{(n-k-1)!\,(k-1)!}\left(\frac{1}{n-k}+\frac{1}{k}\right)\\
&=\frac{n!}{(n-k)!\,k!}\\
&=\binom{n}{k}
\end{aligned}$$

# 4.2 Derive the Gibbs inequality $H(p,q)\ge H(q)$, where $H(p,q)=-\sum p(x)\log q(x)$ is the cross-entropy and $H(q)=-\sum q(x)\log q(x)$ is the entropy.

First, we show that KL divergence is nonnegative:

$$\begin{aligned}
-KL(p\|q)&=-\sum_x p(x)\log\frac{p(x)}{q(x)}\,dx=\sum_x p(x)\log\frac{q(x)}{p(x)}\,dx\\
&\le \log\sum_x p(x)\frac{q(x)}{p(x)}\,dx=\log\sum_x q(x)\\
&\le \log 1=0
\end{aligned}$$

Using the previously derived property, we can write down the Gibbs inequality as follows:

$$\begin{aligned}
KL(p\|q)&\ge 0\\
\sum_x p(x)\log p(x)-\sum_x p(x)\log q(x)&\ge 0\\
-H(p)+H(p,q)&\ge 0\\
H(p,q)&\ge H(p)
\end{aligned}$$