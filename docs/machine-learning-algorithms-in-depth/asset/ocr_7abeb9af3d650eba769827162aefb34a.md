In the previous example, we used a normalized proposal distribution. However, for more complex distributions we often do not know the normalization constant (aka the partition function), since we are working with ratios of pdfs we’ll see that the math holds for unnormalized distributions in addition we’ll look at a way of estimating ratios of partition functions and discuss IS properties as an estimator.

Let’s define a normalized PDF $p(x)$ and $q(x)$ as follows.

$$p(x) = \frac{1}{Z_p}\tilde{p}(x)\qquad q(x) = \frac{1}{Z_p}\tilde{q}(x)\tag{2.26}$$

Here, $Z_p$ and $Z_q$ are normalization constants of $p(x)$ and $q(x)$, respectively, and $\tilde{p}(x)$ and $\tilde{q}(x)$ are unnormalized distributions. We can write our estimate as follows.

$$E[f(x)] = \int f(x)p(x)dx$$ $$= \int f(x)\frac{q(x)}{q(x)}p(x)dx = \frac{Z_q}{Z_p}\int f(x)\frac{\tilde{p}(x)}{\tilde{q}(x)}q(x)dx$$ $$\approx \frac{Z_q}{Z_p}\frac{1}{S}\sum_{s=1}^{S}\tilde{w}(s)f(s),\ \text{where } s\sim q(x)\text{ and }\tilde{w}(s)=\frac{\tilde{p}(s)}{\tilde{q}(s)}\tag{2.27}$$

Notice in equation 2.27, $\tilde{w}(s)$ are unnormalized importance weights. We can compute the ratio of normalizing constants as follows.

$$\frac{Z_p}{Z_q}=\frac{1}{Z_q}\int\tilde{p}(x)dx=\frac{1}{Z_q}\int\frac{\tilde{p}(x)}{q(x)}q(x)dx=\int\frac{\tilde{p}(x)}{\tilde{q}(x)}q(x)dx=\frac{1}{S}\sum_{s=1}^{S}\tilde{w}(s)\tag{2.28}$$

Combining the two expressions above, we get the following.

$$E[f(x)]\approx\frac{Z_q}{Z_p}\frac{1}{S}\sum_{s=1}^{S}\tilde{w}(s)f(s)=\frac{\frac{1}{S}\sum_s\tilde{w}(s)f(s)}{\frac{1}{S}\sum_s\tilde{w}(s)}=\sum_{s=1}^{S}w(s)f(s)\tag{2.29}$$

Equation 2.29 justifies our computation in the code example for the estimate of $E[f(x)]$. Let’s look at a few properties of IS estimator and compute quantities relevant to characterizing the performance of IS. The IS estimator can be defined as follows.