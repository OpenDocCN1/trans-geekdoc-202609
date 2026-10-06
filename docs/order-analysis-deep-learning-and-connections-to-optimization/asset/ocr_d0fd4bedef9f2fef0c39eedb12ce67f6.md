114

6 Basics of Deep Learning

and

$\|x^{t+1} - \bar{x}^t\|_2^2 \leq (1 - \lambda_i \mu)^{t+1} \|x^0 - \bar{x}^t\|_2^2 \text{ for all } i \in \mathbb{N}\{0\},$

where

$1 - \lambda_i \mu \in [1 - \lambda_i \bar{\mu}, \mu] \subseteq (0, 1) \text{ for all } i \in \mathbb{N}\{0\}.

**Proof**, by note Lemma 1.11 the function $f$ has a unique minimal point $\bar{x}$, since $f$ is $\mu$-strongly convex and continuous. For an arbitrary $i \in \mathbb{N}\{0\}$, we then obtain

```
$\|x^{t+1} - \bar{x}^t\|_2^2$
= \|x^t - \bar{x}^t - \lambda_i \nabla f(x^t) - \bar{x}^t\|_2^2$
= (x^t - \bar{x}^t - \lambda_i \nabla f(x^t))^T(x^t - \bar{x}^t) + \lambda_i^2 |\nabla f(x^t)\|_2^2$
= \|x^t - \bar{x}^t\|_2^2 - 2\lambda_i \nabla f(x^t)(x^t - \bar{x}^t) + \lambda_i^2 |\nabla f(x^t)\|_2^2$
$\geq \frac{f(x^t) - f(\bar{x}) - \frac{\mu}{2}\|x^t - \bar{x}\|_2^2}{\mu}$ (by Lemma 6.2)
$\leq (1 - \lambda_i \mu)\|x^t - \bar{x}^t\|_2^2 - 2\lambda_i (f(x^t) - f(\bar{x})) + \lambda_i^2 |\nabla f(x^t) - f(\bar{x})\|_2^2$
\leq2L(f(x^t)-f(\bar{x}))$ (by Lemma 6.3)
$\leq (1 - \lambda_i \mu)\|x^t - \bar{x}^t\|_2^2 - 2\lambda_i \frac{(1 - \lambda_i L)}{L} (f(x^t) - f(\bar{x}))$\n$\geq 0$ (because of $\lambda_i < \frac{1}{L}$)\n$\leq (1 - \lambda_i \mu)\|x^t - \bar{x}^t\|_2^2$,
```

which proves the inequality (6.7). The inequality (6.8) is a direct consequence of the inequality (6.7). With the inequality $\lambda > 0$ and $\mu < \frac{1}{L}$, the assertion (6.9) follows immediately.

**Corollary 6.1 (Linear Convergence of the Gradient Method (Compare [42, Remark 3]))** Let the assumptions of Theorem 6.2 be satisfied. Then the sequence $(x^t)^{t \in \mathbb{N}}$ converges to the unique minimal point $\bar{x}$ of $f$.

**Proof** It is obvious from the inequality (6.8) with condition (6.9) that the sequence $(x^t)^{t \in \mathbb{N}}$ converges to the unique minimal point $\bar{x}$ of $f$. Inequality (6.7) together with condition (6.9) means that the sequence $(x^t)^{t \in \mathbb{N}}$ is linearly convergent.

Now, we turn our attention to a more practical variant of the conceptual Algorithm 6.1. In practice, it makes little sense to work with the optimal step size as lines 6 and 7 of Algorithm 6.1. Therefore, approximations are used, such as those given by Armijo, Goldstein, or Powell in nonlinear optimization (see [46, Chapter 2] among others). In deep learning, however, we need a variant that is characterized