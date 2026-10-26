It follows that

$$\begin{aligned}
D_f(h(W)\|h(Z)) &= \mathbb{E}_{X'\sim Q}f\left(\frac{P(X')}{Q(X')}\right) \\
&\overset{(a)}{=} \mathbb{E}_{X'\sim Q}f\left(\mathbb{E}_{X\sim Q(\cdot\mid X')}\left[\frac{P(X,X')}{Q(X,X')}\right]\right) \\
&\overset{(b)}{\leq} \mathbb{E}_{X'\sim Q}\mathbb{E}_{X\sim Q(\cdot\mid X')}f\left(\frac{P(X,X')}{Q(X,X')}\right) \\
&\overset{(c)}{=} \mathbb{E}_{X'\sim Q}\mathbb{E}_{X\sim Q(\cdot\mid X')}f\left(\frac{P(X)}{Q(X)}\right) \\
&= \mathbb{E}_{[X,X']\sim Q}f\left(\frac{P(X)}{Q(X)}\right)=D_f(W\|Z).
\end{aligned}$$

Note that (B.2) implies (a); (b) follows from Jensen’s inequality, and (c) can be obtained from (B.1).

# ## B.2 Examples of $f$-divergence

In the following, we list useful examples of $f$-divergence encountered in the main text. However, it is worth noting that different $f(t)$ can lead to the same divergence, as shown by the following simple fact.

**Proposition B.5**  The $f$-divergence with $f(t)$ is the same as the $f$-divergence with $\tilde f(t)=f(t)+\beta(1-t)$ for any $\beta\in\mathbb{R}$.

We will choose only one $f(t)$ for each divergence in the example, although one can choose different $f(t)$ for convenience. The examples are all strictly convex at $z=1$, and thus $D_f(P\|Q)=0$ if and only if $P=Q$.

# ### $KL$-divergence

With $f(t)=t\ln t$, we obtain the KL-divergence (Kullback–Leibler divergence) as follows

$$KL(P\|Q)=\int_{\Omega}\ln\left(\frac{p(z)}{q(z)}\right)p(z)\,d\mu(z).$$

KL-divergence can be unbounded.

Given random variables $[X,X']$, with probability measure $P$, their mutual information is defined as

$$I(X,X')=KL(P(X,X')\|P(X)P(X')).$$

Mutual information is often used to measure the independence of the random variables $X$ and $X'$. If the random variables are independent, then the mutual information is zero. In the general case, mutual information can be unbounded.