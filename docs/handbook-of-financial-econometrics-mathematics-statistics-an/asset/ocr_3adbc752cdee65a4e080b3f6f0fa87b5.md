We are considering dividing up the original time period $t$ into many shorter subperiods of length $h$ so that $t = nh$. Our procedure calls for making $n$ larger while keeping the original time period $t$ fixed. As $n \to \infty$, we would at least like the mean and the variance if the continuously compounded return rate of the assumed stock price movement coincided with that of actual stock price. Label the actual empirical values of $\tilde{\mu}n$ and $\tilde{\sigma}^2n$ as $\mu t$ and $\sigma^2t$, respectively. Then we want to choose $u$, $d$, and $p$ so that $\tilde{\mu}n \to \mu t$ and $\tilde{\sigma}^2n \to \sigma^2t$ as $n \to \infty$.

A little algebra shows that we can accomplish this by letting

$$u = e^{\sigma\sqrt{\frac{t}{n}}},\quad d = e^{-\sigma\sqrt{\frac{t}{n}}},$$ $$p = \frac{1}{2} + \frac{1}{2}\left(\frac{\mu}{\sigma}\right)\sqrt{\frac{t}{n}}.\tag{102.28}$$

At this point, in order to proceed further, we need the Lyapunov condition of central limit theorem as follows (Ash and Doleans-Dade 1999, Billingsley 2008).

# Lyapunov's Condition.

Suppose $X_1,X_2,\dots$ are independent and uniformly bounded with $E(X_i)=0$, $Y_n = X_1 + \cdots + X_n$, and $s^2 = E(Y_n^2) = \operatorname{Var}(Y_n)$.

If $\lim_{n\to\infty}\sum_{k=1}^n \frac{1}{s_n^{2+\delta}}E|X_k|^{2+\delta}=0$ for some $\delta>0$, then the distribution of $\frac{Y_n}{s_n}$ converges to the standard normal distribution as $n\to\infty$.

# Theorem. If

$$\frac{p|\log u - \tilde{\mu}|^3 + (1-p)|\log d - \tilde{\mu}|^3}{\tilde{\sigma}^3\sqrt{n}} \to 0 \text{ as } n\to\infty,\quad \text{then}\tag{102.29}$$ $$\Pr\left[\frac{\log\left(\frac{S^*}{S}\right) - \tilde{\mu}n}{\tilde{\sigma}\sqrt{n}} \le z\right] \to N(z),\tag{102.30}$$

where $N(z)$ is the cumulative standard normal distribution function.

# Proof. Since

$$p|\log u - \tilde{\mu}|^3 = p|\log u - p\log\frac{u}{d} - \log d|^3 = p(1-p)^3\left|\log\frac{u}{d}\right|^3$$ and $$(1-p)|\log d - \tilde{\mu}|^3 = (1-p)|\log d - p\log\frac{u}{d} - \log d|^3 = p^3(1-p)\left|\log\frac{u}{d}\right|^3,$$ we have $$p|\log u - \tilde{\mu}|^3 + (1-p)|\log d - \tilde{\mu}|^3 = p(1-p)\big[(1-p)^2 - p^2\big]\left|\log\frac{u}{d}\right|^3.$$