# Remark 5.5.2 (Sparsity).

The sparsest graphs for which Theorem 5.5.1 is non-trivial have expected average degree

$$\frac{n(p+q)}{2} = \frac{a+b}{2} \asymp \log n.$$

That’s way sparser than $O(\sqrt{n})$ we have achieved previously (Remark 4.5.3)!

To practice more with these ideas, try Exercise 5.25 to do community detection in the stochastic bock model without loops (a pretty natural model).

# 5.6 Application: covariance estimation for general distributions

In Section 4.7, we learned how to estimate the covariance matrix of a subgaussian distribution in $\mathbb{R}^n$ from a sample of size $O(n)$. Now, we drop the subgaussian assumption, making it work for much broader distributions, even discrete ones. The trade-off is just a logarithmic oversampling factor!

Like in Section 4.7, we estimate the second moment matrix $\Sigma = \mathbb{E} X X^{\top}$ by its sample version

$$\Sigma_m = \frac{1}{m} \sum_{i=1}^m X_i X_i^{\top}.$$

If $X$ has zero mean, then $\Sigma$ is the covariance matrix of $X$, and $\Sigma_m$ is the sample covariance matrix.

# Theorem 5.6.1 (General covariance estimation).

Let $X$ be a random vector in $\mathbb{R}^n$, $n \ge 2$. Assume that for some $K \ge 1$, 

$$\|X\|_2 \le K (\mathbb{E}\|X\|_2^2)^{1/2} \quad \text{almost surely.}\tag{5.20}$$

Then, for every positive integer $m$, we have

$$\mathbb{E}\|\Sigma_m - \Sigma\| \le C\left(\sqrt{\frac{K^2 n \log n}{m}} + \frac{K^2 n \log n}{m}\right) \|\Sigma\|.$$

Proof By Proposition 3.2.1(b), we have $\mathbb{E}\|X\|_2^2 = \operatorname{tr}(\Sigma)$, so (5.20) becomes

$$\|X\|_2^2 \le K^2 \operatorname{tr}(\Sigma) \quad \text{almost surely.}\tag{5.21}$$

Apply the expected version of matrix Bernstein inequality (5.17) for the sum of i.i.d. mean-zero random matrices $X_i X_i^{\top} - \Sigma$ and get$^{17}$

$$\mathbb{E}\|\Sigma_m - \Sigma\| = \frac{1}{m} \mathbb{E}\Big\|\sum_{i=1}^m (X_i X_i^{\top} - \Sigma)\Big\| \lesssim \frac{1}{m} \big(\sigma\sqrt{\log n} + M \log n\big)\tag{5.22}$$

where

$$\sigma^2 = \Big\|\sum_{i=1}^m \mathbb{E}(X_i X_i^{\top} - \Sigma)^2\Big\| = m \big\|\mathbb{E}(X X^{\top} - \Sigma)^2\big\|$$

$^{17}$ As usual, the notation $a \lesssim b$ hides absolute constant factors, i.e. it means that $a \le C b$ where $C$ is an absolute constant.