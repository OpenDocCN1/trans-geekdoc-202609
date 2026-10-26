# ### 6.4 Estimating Rademacher Complexity

This section provides some useful results to estimate Rademacher complexity. We mainly focus on the standard Rademacher complexity. For a finite function class, we have the following simple estimate.

**Theorem 6.23**  If $G$ is a finite function class with $|\mathcal{G}|=N$, then

$$R(\mathcal{G},\mathcal{S}_n) \leq \sup_{g\in\mathcal{G}}\|g\|_{L_2(\mathcal{S}_n)}\cdot\sqrt{\frac{2\ln N}{n}}.$$

If moreover, for all $g\in\mathcal{G}$, $g(z)\in[0,1]$. Consider the offset decomposition (6.3), and let $h_0(g)=0$, and $h_1(g,\mathcal{S}_n)=(\gamma/n)\sum_{i=1}^n g(Z_i)$. Then we have

$$R^h(\mathcal{G},\mathcal{S}_n)\leq\frac{(1+0.5\gamma)^2\ln N}{\gamma n}.$$

*Proof*  Let $B=\sup_{g\in\mathcal{G}}\|g\|_{L_2(\mathcal{S}_n)}$. Then we have for all $\lambda>0$,

$$\begin{aligned}
R(\mathcal{G},\mathcal{S}_n)
&=\mathbb{E}_{\sigma}\sup_{g\in\mathcal{G}}\frac{1}{n}\sum_{i=1}^{n}\sigma_i g(Z_i)\\
&\underset{(a)}{\leq}\mathbb{E}_{\sigma}\frac{1}{\lambda n}\ln\sum_{g\in\mathcal{G}}\exp\left[\lambda\sum_{i=1}^{n}\sigma_i g(Z_i)\right]\\
&\underset{(b)}{\leq}\frac{1}{\lambda n}\ln\mathbb{E}_{\sigma}\sum_{g\in\mathcal{G}}\exp\left[\lambda\sum_{i=1}^{n}\sigma_i g(Z_i)\right]\\
&=\frac{1}{\lambda n}\ln\sum_{g\in\mathcal{G}}\prod_{i=1}^{n}\mathbb{E}_{\sigma_i}\exp[\lambda\sigma_i g(Z_i)]\\
&\underset{(c)}{\leq}\frac{1}{\lambda n}\ln\sum_{g\in\mathcal{G}}\prod_{i=1}^{n}\exp[\lambda^2g(Z_i)^2/2]\\
&\leq\frac{1}{\lambda n}\ln N\exp[\lambda^2nB^2/2].
\end{aligned}$$

In $(a)$, we used soft-max to bound the max operator. In $(b)$, we used Jensen’s inequality and the concavity of logarithm. In $(c)$, we used the moment generating function for bounded random variables (see Example 2.14). Now we can obtain the first desired bound by optimizing over $\lambda>0$.

For the second desired bound, we can obtain by duplicating the previous steps up to step $(c)$ to obtain

$$\begin{aligned}
R^h(\mathcal{G},\mathcal{S}_n)
&=\mathbb{E}_{\sigma}\sup_{g\in\mathcal{G}}\frac{1}{n}\sum_{i=1}^{n}[\sigma_i(1+0.5\gamma)g(Z_i)-0.5\gamma g(Z_i)]\\
&\leq\frac{1}{\lambda n}\ln\sum_{g\in\mathcal{G}}\exp\left[\sum_{i=1}^{n}\left[\lambda^2(1+0.5\gamma)^2g(Z_i)^2/2-0.5\lambda\gamma g(Z_i)\right]\right].
\end{aligned}$$

Now set $\lambda=\gamma/(1+0.5\gamma)^2$, and we obtain $R^h(\mathcal{G},\mathcal{S}_n)\leq\frac{1}{\lambda n}\ln\sum_{g\in\mathcal{G}}1$, which implies the second bound. $\square$