# 8.2 Application: empirical processes

Let’s apply Dudley inequality to *empirical processes* – certain natural random processes indexed by functions. Here is a motivating example.

# 8.2.1 The Monte Carlo method

Suppose we want to compute an integral

$$\int_{\Omega} f\,d\mu$$

where $f : \Omega \to \mathbb{R}$ is a given function on some set $\Omega$ and $\mu$ is a probability measure on $\Omega$. For instance, this could just be $\int_0^1 f(x)\,dx$ for a function $f : [0,1] \to \mathbb{R}$ (see Figure 8.3a).

We can do this *probabilistically*. Suppose $X$ is a random point in $\Omega$ drawn according to $\mu$, i.e. $\mathbb{P}\{X \in A\} = \mu(A)$ for any measurable set $A \subset \Omega$. (For instance, $X \sim \operatorname{Unif}[0,1]$ if you are integrating over $[0,1]$.) Then the integral becomes the expectation:

$$\int_{\Omega} f\,d\mu = \mathbb{E}\,f(X).$$

Now take i.i.d. samples $X_1, X_2, \ldots$. By the law of large numbers (Theorem 1.7.1),

$$\frac{1}{n}\sum_{i=1}^{n} f(X_i) \to \mathbb{E}\,f(X) \quad \text{almost surely} \tag{8.18}$$

as $n \to \infty$. So, we can approximate the integral with the arithmetic mean:

$$\int_{\Omega} f\,d\mu \approx \frac{1}{n}\sum_{i=1}^{n} f(X_i) \tag{8.19}$$

(see Figure 8.3b). This is the *Monte Carlo method* – compute the integral by averaging function values at random sample points.

![](bbox=[0.258, 0.657, 0.789, 0.769])

**Figure 8.3** Monte Carlo method for numerical integration.

**Remark 8.2.1** (Error rate). The expected error of the Monte Carlo estimate