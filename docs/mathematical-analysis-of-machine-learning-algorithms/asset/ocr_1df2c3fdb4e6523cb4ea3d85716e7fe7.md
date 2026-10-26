This matches the lower bound of Corollary 12.20.

For $q > 2$, the generalization bound for empirical risk minimization method is

$$\mathbb{E}_{S_n \sim \mathcal{D}^n} \mathbb{E}_{X \sim \mathcal{D}_X} (\hat f_{\mathrm{erm}}(X) - f_{\mathcal{D}}(X))^2 = O(n^{-1/q}),$$

and since $1/q < 2/(q + 2)$, the rate is inferior to the minimax rate. In general, this rate cannot be improved without additional assumptions (Birgé and Massart, 1993). Therefore when the nonparametric family has a large entropy, ERM can be suboptimal.

It is possible to achieve the optimal rate of $O(n^{-2/(q+2)})$ even when $q > 2$. One of the optimal methods is least squares on sieves, and a related method is the Gibbs algorithm with an appropriate prior. A third method is the exponential model aggregation method, studied in Section 15.3.

In the following, we consider the sieve method (Grenander, 1981; Geman and Hwang, 1982; Birgé and Massart, 1998), which, in our setting, is simply least squares regression on discrete $\epsilon$-net.

Given a function class $\mathcal{F}$, instead of running least squares on $\mathcal{F}$ with

$$\hat f = \arg\min_{f \in \mathcal{F}} \sum_{i=1}^{n} (f(X_i) - Y_i)^2,$$

the sieve method considers a subset $\mathcal{F}_n \subset \mathcal{F}$, and then performs least squares regression restricted to this subset:

$$\hat f_{\mathcal{F}_n} = \arg\min_{f \in \mathcal{F}_n} \sum_{i=1}^{n} (f(X_i) - Y_i)^2.$$

The following result shows that with appropriate $\mathcal{F}_n$, we may achieve the minimax risk of Corollary 12.20.

# **Proposition 12.21**

Assume that the distribution of $X$ is $\mathcal{D}_X$. Let $\mathcal{F}_n$ be an $\epsilon$ packing subset of $\mathcal{F}$ in the $L_2(\mathcal{D}_X)$ metric with $M(\epsilon, \mathcal{F}, L_2(\mathcal{D}_X))$ members. Assume there exists $b > 0$ such that $|f(X) - f'(X)| \le 2b$ for all $f, f' \in \mathcal{F}$. Assume that $f_{\mathcal{D}} \in \mathcal{F}$ and $Y$ is sub-Gaussian:

$$\ln \mathbb{E}_{Y|X} \exp(\lambda(Y - f_{\mathcal{D}}(X))) \le \frac{\lambda^2 b^2}{2}.$$

Then

$$\mathbb{E}_{S_n \sim \mathcal{D}^n} \mathbb{E}_{X \sim \mathcal{D}_X} (\hat f_{\mathcal{F}_n}(X) - f_{\mathcal{D}}(X))^2 \le \left[ 4\epsilon^2 + \frac{14 b^2}{n} \ln M(\epsilon, \mathcal{F}, L_2(\mathcal{D}_X)) \right].$$

*Proof* Let $\phi(f, Z) = (f(X)-Y)^2 - (f_{\mathcal{D}}(X)-Y)^2$ with $Z = (X, Y)$. Let $\rho = b^{-2}/4$. Then we have