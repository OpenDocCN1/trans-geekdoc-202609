can show that, as $N$ increases, the distribution of this sum approaches

```
$$p(S_N = u) = \frac{1}{\sqrt{2\pi N\sigma^2}} \exp\left(-\frac{(u-N\mu)^2}{2N\sigma^2}\right) \quad \text{(D.80)}$$
```

Hence the distribution of the quantity

```
$$Z_N \triangleq \frac{S_N - N\mu}{\sigma\sqrt{N}} = \frac{\overline{X} - \mu}{\sigma/\sqrt{N}} \quad \text{(D.81)}$$
```

converges to the standard normal, where $\overline{X} = S_N/N$ is the sample mean. This is called the **central limit theorem**. See e.g., [Jay03, p222] or [Ric95, p169] for a proof.

In Fig. D.14 we give an example in which we compute the sample mean of rv's drawn from a beta distribution. We see that the sampling distribution of this mean rapidly converges to a Gaussian distribution.

# **D.6  Exercises**

# **Exercise D.1** [Conditional independence]

(Source: Koller.)

a. Let $H \in \{1, \dots, K\}$ be a discrete random variable, and let $e_1$ and $e_2$ be the observed values of two other random variables $E_1$ and $E_2$. Suppose we wish to calculate the vector

```
$$\hat{P}(H|e_1, e_2) = (P(H=1|e_1, e_2), \dots, P(H=K|e_1, e_2))$$
```

Which of the following sets of numbers are sufficient for the calculation?

+   i. $P(e_1, e_2), P(H), P(e_1|H), P(e_2|H)$
+   ii. $P(e_1, e_2), P(H), P(e_1, e_2|H)$
+   iii. $P(e_1|H), P(e_2|H), P(H)$

b. Now suppose we now assume $E_1 \perp E_2|H$ (i.e., $E_1$ and $E_2$ are conditionally independent given $H$). Which of the above 3 sets are sufficient now?

Show your calculations as well as giving the final result. Hint: use Bayes rule.

# **Exercise D.2** [Pairwise independence does not imply mutual independence]

We say that two random variables are pairwise independent if

```
$$p(X_2|X_1) = p(X_2) \quad \text{(D.82)}$$
```

and hence

```
$$p(X_2, X_1) = p(X_1)p(X_2|X_1) = p(X_1)p(X_2) \quad \text{(D.83)}$$
```

We say that $n$ random variables are mutually independent if

```
$$p(X_i|X_S) = p(X_i) \text{ for } S \subseteq \{1, \dots, n\} \setminus \{i\} \quad \text{(D.84)}$$
```

and hence

```
$$p(X_{1:n}) = \prod_{i=1}^{n} p(X_i) \quad \text{(D.85)}$$
```

Show that pairwise independence between all pairs of variables does not necessarily imply mutual independence. It suffices to give a counter example.