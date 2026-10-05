# MATHEMATICAL FOUNDATIONS FOR COMPUTER NETWORKS • 107

![](bbox=[0.238, 0.131, 0.835, 0.332])

FIGURE 2.33 A queuing system with Splitting.

Thus,

$P(Y_2(t)=k)=\sum_{n=k}^{\infty}P(Y_2(t)=k|X_1(t)=n)P(X_1(t)=n) \quad (2.224)$

When $n$ has to be at least as large as $k$. Therefore,

$P(Y_2(t)=k)=\sum_{n=k}^{\infty}\frac{(\lambda t)^n}{n!} \frac{n!}{k!(n-k)!}p^k(1-p)^{n-k} \\n\frac{p^ke^{-\lambda t}}{k!}\sum_{n=k}^{\infty}\frac{[\lambda t(1-p)]^{n-k}}{(n-k)!} \\n\frac{(p\lambda t)^k e^{-\lambda t}}{k!}e^{\lambda t(1-p)} \\n\frac{(p\lambda t)^k e^{-p\lambda t}}{k!} \quad (2.225)$

Thus, $Y_2(t)$ forms a Poisson distribution with input rate $p\lambda$.

# 2.21.3 Queueing System with Feedback

Queueing systems with feedback are applicable to a limited set of circumstances. A typical example is shown in Figure 2.34. The problem here is that the combination of the external Poisson process and the feedback process is not Poisson because the processes being superposed are not independent due to the feedback. However, consideration of the steady