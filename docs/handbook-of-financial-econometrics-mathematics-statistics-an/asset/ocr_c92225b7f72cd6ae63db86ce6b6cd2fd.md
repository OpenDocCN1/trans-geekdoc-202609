Thus

$$\frac{p|\log u - \tilde{\mu}|^3 + (1-p)|\log d - \tilde{\mu}|^3}{\hat{\sigma}^3\sqrt{n}}$$

$$= \frac{p(1-p)[(1-p)^2 - p^2] |\log \frac{u}{d}|^3}{\left(\sqrt{p(1-p)}\log\left(\frac{u}{d}\right)\right)^3 \sqrt{n}}$$

$$= \frac{(1-p)^2 + p^2}{\sqrt{np(1-p)}}.$$

Recall that $p = \frac{\hat{r}-d}{u-d}$ with $\hat{r}=r^{t/n}$, $u = e^{\sigma\sqrt{t/n}}$, $d = e^{-\sigma\sqrt{t/n}}$, we have

$$p = \frac{e^{\frac{t}{n}\log r} - e^{-\sigma\sqrt{\frac{t}{n}}}}{e^{\sigma\sqrt{\frac{t}{n}}} - e^{-\sigma\sqrt{\frac{t}{n}}}}$$

$$= \frac{1 + \frac{t}{n}\log r - \left[1 - \sigma\sqrt{\frac{t}{n}} + \frac12\sigma^2\frac{t}{n}\right] + O(n^{-3/2})}{1 + \sigma\sqrt{\frac{t}{n}} - \left[1 - \sigma\sqrt{\frac{t}{n}}\right] + O(n^{-3/2})}$$

$$= \frac12 + \frac12\left[\frac{\log r - \frac12\sigma^2}{\sigma}\right]\sqrt{\frac{t}{n}} + O(n^{-1})$$

Therefore, $\frac{(1-p)^2+p^2}{\sqrt{np(1-p)}} \to 0$ as $n \to \infty$.

Hence the condition for the theorem to hold as stated in equation (102.29) is satisfied. It is noted that the condition (102.29) is a special case of Lyapunov's condition where $\delta = 1$. Next, we will show that the binomial option pricing model as given in equation (102.23) will indeed coincide with the Black-Scholes option pricing formula. We can see that there are apparent similarities in equation (102.23). In order to show the limiting result, we need to show that

As $n \to \infty$, $B_1(a; n, p') \to N(x)$ and $B_2(a; n, p) \to N(x - \sigma\sqrt{t})$. In this section we will only show the second convergence result, as the same argument will hold true for the first convergence. From the definition of $B_2(a; n, p)$, it is clear that

$$1 - B_2(a; n, p) = \Pr(j \le a - 1)$$

$$= \Pr\left(\frac{j - np}{\sqrt{np(1-p)}} \le \frac{a - 1 - np}{\sqrt{np(1-p)}}\right). \tag{102.31}$$