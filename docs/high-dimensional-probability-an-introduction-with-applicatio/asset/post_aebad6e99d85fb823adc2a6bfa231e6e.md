
## 2.9 Bernstein inequality

We are ready to state and prove a version of Hoeffding’s inequality (Theorem [2.7.3](#)) that works for subexponential distributions:

**Theorem 2.9.1** (Subexponential Bernstein inequality). *Let* $X_1,\ldots,X_N$ *be independent, mean-zero, subexponential random variables. Then, for every* $t\ge 0$, *we have*

$$\mathbb{P}\left\{\left|\sum_{i=1}^{N}X_i\right|\ge t\right\}\le 2\exp\left[-c\min\left(\frac{t^2}{\sum_{i=1}^{N}\|X_i\|_{\psi_1}^2},\frac{t}{\max_i\|X_i\|_{\psi_1}}\right)\right].$$

where $c>0$ is an absolute constant.

If this bound seems a bit intimidating, do not worry—we will break it down and simplify it after the proof.

**Proof.** We use the exponential moment method, which we learned in the proof of Hoeffding and Chernoff inequalities (Theorems [2.2.1](#) and [2.3.1](#)). Denote $S_N=\sum_{i=1}^{N}X_i$, multiply both sides of the inequality $S_N\ge t$ by a parameter $\lambda\ge 0$, exponentiate, and use Markov inequality and independence. This leads to (2.9):

$$\mathbb{P}\{S_N\ge t\}\le e^{-\lambda t}\prod_{i=1}^{N}\mathbb{E}\exp(\lambda X_i). \tag{2.27}$$

To bound the MGF of each term $X_i$, we use property **(iv)** in Proposition [2.8.1](#). It says that if $\lambda$ is small enough so that

$$|\lambda|\le \frac{c}{\max_i\|X_i\|_{\psi_1}}, \tag{2.28}$$

then<sup>8</sup> $\mathbb{E}\exp(\lambda X_i)\le \exp(C\lambda^2\|X_i\|_{\psi_1}^2)$. Substituting this into (2.27), we obtain

$$\mathbb{P}\{S_N\ge t\}\le \exp(-\lambda t+C\lambda^2\sigma^2),\qquad \text{where }\sigma^2=\sum_{i=1}^{N}\|X_i\|_{\psi_1}^2.$$

Now we minimize this expression in $\lambda$ subject to the constraint (2.28). The optimal choice is $\lambda=\min\left(\frac{t}{2C\sigma^2},\frac{c}{\max_i\|X_i\|_{\psi_1}}\right)$, for which we obtain

$$\mathbb{P}\{S_N\ge t\}\le \exp\left[-\min\left(\frac{t^2}{4C\sigma^2},\frac{ct}{2\max_i\|X_i\|_{\psi_1}}\right)\right].$$

Repeating this argument for $-X_i$ instead of $X_i$, we obtain the same bound for $\mathbb{P}\{-S_N\ge t\}$. Combining these two bounds completes the proof.

To make Theorem [2.9.1](#) more handy, let us apply it for $a_iX_i$ instead of $X_i$. This gives us a version of (2.20) for subexponential distributions:

<sup>8</sup> Recall that by Proposition [2.8.1](#) and definition of the subexponential norm, property **(iv)** holds for a value of $K_4$ that is within an absolute constant factor of $\|X\|_{\psi_1}$.

2.14 🐁🐁 **(Chernoff inequality: small deviations)** Let’s extend Corollary 2.3.4. Let $X_i$ be independent Bernoulli random variables with parameters $p_i$. Consider their sum $S_N = \sum_{i=1}^N X_i$ and denote its mean by $\mu = \mathbb{E}S_N$. Show that

$$\mathbb{P}\{|S_N-\mu|\ge \delta\mu\}\le 2\exp\left(-\frac{\delta^2\mu}{2+\delta}\right) \quad\text{for every }\delta\ge 0.$$

2.15 🐁 **(Chernoff inequality for bounded random variables)** Argue that all versions of Chernoff inequality (Theorem 2.3.1, Remark 2.3.2, and Corollary 2.3.4) are valid for any independent random variables $X_i$ that take values in the interval $[0,1]$ and have means $p_i$.

2.16 🐁🐁 **(Median-of-means: fixing the proof)** The proof of Theorem 2.4.1 is slightly flawed: $B=t^2/4$ may not be an integer that divides $N$. Fix this.

2.17 🐁🐁🐁 **(No mean estimator is subgaussian everywhere)** You may wonder if Theorem 2.4.1 holds for all $t>0$. It does not. In fact, no mean estimator can provide subgaussian confidence for all quantiles. *Disprove* the following claim:

> > “There exists an absolute constant $c>0$ such that the following holds. For any integer $N>0$ and every $t\ge 0$, one can find a function $\hat{\mu}:\mathbb{R}^N\to\mathbb{R}$ satisfying
> >
> > $$\mathbb{P}\left\{\left|\hat{\mu}(X_1,\ldots,X_N)-\mu\right|\ge \frac{t\sigma}{\sqrt{N}}\right\}\le 2e^{-ct^2}$$
> >
> > for all i.i.d. random variables $X_1,\ldots,X_N$ with mean $\mu$ and variance $\sigma^2$.”

Do this by working out a version of *Le Cam’s two-point method*:

- (a) Consider two random vectors $X=(X_1,\ldots,X_N)$ and $Y=(Y_1,\ldots,Y_N)$ with independent Laplace¹⁰ coordinates: $X_i\sim\operatorname{Lap}(0,1)$ and $Y_i\sim\operatorname{Lap}(\mu,1)$ for some $\mu>0$. Check that $\mathbb{P}\{X\in B\}\le e^\mu\mathbb{P}\{Y\in B\}$ for any measurable subset $B\subset\mathbb{R}^N$.
- (b) Assume for contradiction that the claim holds. Apply it to bound the probabilities of the events $|\hat{\mu}(X)|\ge \mu/2$ and $|\hat{\mu}(Y)-\mu|\ge \mu/2$.
- (c) Choose $\mu$ large enough and replace $Y$ with $X$ using (a) to make both events $|\hat{\mu}(X)|<\mu/2$ and $|\hat{\mu}(X)-\mu|<\mu/2$ likely. Use triangle inequality to arrive at a contradiction.

2.18 🐁 **(Most degrees of sparse random graphs are OK)** In Exercise 1.10, we saw that a typical sparse random graph $G\sim G(n,p)$ has isolated vertices (“friendless students”), resulting in a minimum degree of zero. However, most vertex degrees are still close to the expected degree $d=(n-1)p$. Prove that there exists an absolute constant $C>0$ such that if $d\ge C$, then with probability at least $0.99$ the following event holds: at least $99\%$ of the vertices have their degrees between $0.9d$ and $1.1d$.

2.19 🐁🐁🐁🐁🐁 **(Maximum degrees of sparse random graphs)** In Exercise 1.10, we observed that a typical sparse random graph $G\sim G(n,p)$ has the minimum degree zero. But what about the maximum degree (“the number of friends of the most popular student”), denoted

¹⁰ The Laplace distribution $\operatorname{Lap}(\mu,1)$ has probability density function $\frac{1}{2}e^{-|x-\mu|}$ for $x\in\mathbb{R}$. The mean is $\mu$ and the variance is $2$. (Check!)

Splitting the event based on whether $E_n$ occurs, we get

$$\mathbb{P}\{\sqrt{n}\langle X,v\rangle\le t\}\le \mathbb{P}\{\sqrt{n}\langle X,v\rangle\le t\text{ and }E_n\}+\mathbb{P}(E_n^c)$$
$$\le \mathbb{P}\{g_1\le t_n\}+p_n.$$

Hence

$$\mathbb{P}\{\sqrt{n}\langle X,v\rangle\le t\}-\mathbb{P}\{g_1\le t\}\le \mathbb{P}\{g_1\in[t,t_n]\}+p_n. \tag{3.18}$$

The density of $g_1$ on $[t,t_n]$ is bounded by $e^{-t^2/2}$, so

$$(3.18)\le e^{-t^2/2}(t_n-t)+p_n=e^{-t^2/2}\frac{\ln n}{\sqrt n}+p_n\le \frac{C\ln n}{\sqrt n}+p_n.$$

The right-hand side does not depend on $v$ or $t$, and it goes to zero as $n\to\infty$. A similar argument gives a bound on $\mathbb{P}\{g_1\le t\}-\mathbb{P}\{\sqrt{n}\langle X,v\rangle\le t\}$ that also goes to zero. (Do it!) Combining the two bounds completes the proof.

**Remark 3.3.10** (The density of the 1D marginals of the sphere). The density of the 1D marginals of the uniform distribution on the sphere of radius $\sqrt n$ can be computed. As you will see in Exercise $3.27$, it is proportional to $(1-x^2/n)^{\frac{n-3}{2}}$. For large $n$, this approximates $e^{-x^2/2}$, consistent with the Gaussian limit.

### 3.3.4 Uniform on a convex set

This example comes from convex and computational geometry. A bounded convex set $K\subset\mathbb{R}^n$ with a non-empty interior is called a *convex body*. Let $X$ be a random vector uniformly distributed in $K$:

$$X\sim\operatorname{Unif}(K).$$

The density of $X$ equals $1/\operatorname{Vol}(K)$ on $K$ and zero elsewhere. The mean of $X$,

$$\mu=\mathbb{E}X=\frac{1}{\operatorname{Vol}(K)}\int_K x\,dx,$$

is the center of gravity of $K$. If $\Sigma=\operatorname{cov}(X)$ is the covariance matrix of $K$, then the standard score $Z:=\Sigma^{-1/2}(X-\mu)$ is an isotropic random vector, as we noticed in $(3.10)$. Also, $Z$ is uniformly distributed in the affinely transformed copy of $K$:

$$Z\sim\operatorname{Unif}\left(\Sigma^{-1/2}(K-\mu)\right).$$

(Why?) In summary, we found an affine transformation $T$ that makes the uniform distribution on $T(K)$ isotropic. The convex body $T(K)$ is often itself called an isotropic convex body.

In algorithmic convex geometry, we can think of the isotropic convex body $T(K)$ as a well-conditioned version of $K$, with $T$ acting like a *preconditioner* (see Figure $3.6$). Algorithms such as finding the volume of $K$ usually work better when $K$ is well-conditioned.
