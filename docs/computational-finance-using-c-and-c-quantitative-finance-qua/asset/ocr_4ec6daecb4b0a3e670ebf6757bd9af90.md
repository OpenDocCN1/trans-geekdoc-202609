# # Appendix C:
Standard statistical results

# ## C.1 The law of large numbers

Let $x_1, x_2, \dots$ be a sequence of independent, identically distributed random variables (IID), each with expected value $\mu$ and variance $\sigma^2$. Define the sequence of averages

$y_n = \sum_{i=1}^n x_i = \frac{x_1 + x_2 + \dots + x_n}{n}, \quad n = 1, 2, \dots$

Then the law of large numbers states that $y_n$ converges to $\mu$ as $n 	o \infty$, that is $Var[y_n] 	o 0$.

The mean of $y_n$ is:

$E[y_n] = \frac{1}{n}(E[x_1] + E[x_2] + \dots + E[x_n]) = \frac{1}{n}\mu = \mu$

The variance of $y_n$ we have:

$Var[y_n] = Var\left[\frac{\sum_{i=1}^n x_i}{n}\right] = \frac{1}{n^2}Var\left[\sum_{i=1}^n x_i\right] = \frac{1}{n^2}n\sigma^2 = \frac{\sigma^2}{n}$

where we have used the fact that the variance of the sum of independent random variables is the sum of their variances; see Section C.2.

We have therefore shown that $n \to \infty, Var[y_n] \to 0$.

# ## C.2 The central limit theorem

Let $x_1, x_2, \dots$ be a sequence of independent, identically distributed random variables (IID), each with expected value $\mu$ and variance $\sigma^2$. If we define $u_i = x_i - \mu$ then:

$E[u_i] = E[u] = 0,\quad Var[u_i] = E[u^2] = \sigma^2$