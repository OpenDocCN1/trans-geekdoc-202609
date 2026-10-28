2.14  🐁🐁  **(Chernoff inequality: small deviations)** Let’s extend Corollary 2.3.4. Let $X_i$ be independent Bernoulli random variables with parameters $p_i$. Consider their sum $S_N = \sum_{i=1}^N X_i$ and denote its mean by $\mu = \mathbb{E}S_N$. Show that

$$\mathbb{P}\{|S_N-\mu|\ge \delta\mu\}\le 2\exp\left(-\frac{\delta^2\mu}{2+\delta}\right) \quad\text{for every }\delta\ge 0.$$

2.15  🐁  **(Chernoff inequality for bounded random variables)** Argue that all versions of Chernoff inequality (Theorem 2.3.1, Remark 2.3.2, and Corollary 2.3.4) are valid for any independent random variables $X_i$ that take values in the interval $[0,1]$ and have means $p_i$.

2.16  🐁🐁  **(Median-of-means: fixing the proof)** The proof of Theorem 2.4.1 is slightly flawed: $B=t^2/4$ may not be an integer that divides $N$. Fix this.

2.17  🐁🐁🐁  **(No mean estimator is subgaussian everywhere)** You may wonder if Theorem 2.4.1 holds for all $t>0$. It does not. In fact, no mean estimator can provide subgaussian confidence for all quantiles. *Disprove* the following claim:

> > “There exists an absolute constant $c>0$ such that the following holds. For any integer $N>0$ and every $t\ge 0$, one can find a function $\hat{\mu}:\mathbb{R}^N\to\mathbb{R}$ satisfying
> >
> > $$\mathbb{P}\left\{\left|\hat{\mu}(X_1,\ldots,X_N)-\mu\right|\ge \frac{t\sigma}{\sqrt{N}}\right\}\le 2e^{-ct^2}$$
> >
> > for all i.i.d. random variables $X_1,\ldots,X_N$ with mean $\mu$ and variance $\sigma^2$.”

Do this by working out a version of *Le Cam’s two-point method*:

+   (a) Consider two random vectors $X=(X_1,\ldots,X_N)$ and $Y=(Y_1,\ldots,Y_N)$ with independent Laplace¹⁰ coordinates: $X_i\sim\operatorname{Lap}(0,1)$ and $Y_i\sim\operatorname{Lap}(\mu,1)$ for some $\mu>0$. Check that $\mathbb{P}\{X\in B\}\le e^\mu\mathbb{P}\{Y\in B\}$ for any measurable subset $B\subset\mathbb{R}^N$.
+   
+   (b) Assume for contradiction that the claim holds. Apply it to bound the probabilities of the events $|\hat{\mu}(X)|\ge \mu/2$ and $|\hat{\mu}(Y)-\mu|\ge \mu/2$.
+   
+   (c) Choose $\mu$ large enough and replace $Y$ with $X$ using (a) to make both events $|\hat{\mu}(X)|<\mu/2$ and $|\hat{\mu}(X)-\mu|<\mu/2$ likely. Use triangle inequality to arrive at a contradiction.

2.18  🐁  **(Most degrees of sparse random graphs are OK)** In Exercise 1.10, we saw that a typical sparse random graph $G\sim G(n,p)$ has isolated vertices (“friendless students”), resulting in a minimum degree of zero. However, most vertex degrees are still close to the expected degree $d=(n-1)p$. Prove that there exists an absolute constant $C>0$ such that if $d\ge C$, then with probability at least $0.99$ the following event holds: at least $99\%$ of the vertices have their degrees between $0.9d$ and $1.1d$.

2.19  🐁🐁🐁🐁🐁  **(Maximum degrees of sparse random graphs)** In Exercise 1.10, we observed that a typical sparse random graph $G\sim G(n,p)$ has the minimum degree zero. But what about the maximum degree (“the number of friends of the most popular student”), denoted

¹⁰ The Laplace distribution $\operatorname{Lap}(\mu,1)$ has probability density function $\frac{1}{2}e^{-|x-\mu|}$ for $x\in\mathbb{R}$. The mean is $\mu$ and the variance is $2$. (Check!)