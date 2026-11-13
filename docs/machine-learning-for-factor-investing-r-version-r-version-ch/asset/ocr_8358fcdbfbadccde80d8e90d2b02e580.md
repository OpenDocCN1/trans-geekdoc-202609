# 10.3 The search for good hyperparameters

Therefore, it is critical to choose each trial for **b** wisely. One key assumption of BO is that the distribution of $O$ is Gaussian and that $O$ can be proxied by a linear combination of the $p_i$. Said differently, the aim is to build a Bayesian linear regression between the input $\mathbf{p}$ and the output (dependent variable) $O$. Once a model has been estimated, the information that is concentrated in the posterior density of $O$ is used to make an educated guess at where to look for new values of $\mathbf{p}$.

This educated guess is made based on a so-called **acquisition function**. Suppose we have tested $m$ values for $\mathbf{p}$, which we write $\mathbf{p}^{(m)}$. The current best parameter is written $\mathbf{p}_m^* = \underset{1 \le k \le m}{\text{argmin}} O(\mathbf{p}^{(k)})$. If we test a new point $\mathbf{p}$, then it will lead to an improvement only if $O(\mathbf{p}) < O(\mathbf{p}_m^*)$, that is if the new objective improves the minimum value that we already know. The average value of this improvement is

```
\(\mathbf{EI}_m(\mathbf{p}) = \mathbb{E}_m[[O(\mathbf{p}_m^*) - O(\mathbf{p})]_+],\) (10.11)
```

where the positive part $[\cdot]_+$ emphasizes that when $O(\mathbf{p}) \ge O(\mathbf{p}_m^*)$, the gain is zero. The expectation is indexed by $m$ because it is computed with respect to the posterior distribution of $O(\mathbf{p})$ based on the $m$ samples $\mathbf{p}^{(m)}$. The best choice for the next sample $\mathbf{p}^{m+1}$ is then

```
\(\mathbf{p}^{m+1} = \underset{\mathbf{p}}{\text{argmax}} \mathbf{EI}_m(\mathbf{p}),\) (10.12)
```

which corresponds to the maximum location of the expected improvement. Instead of the EI, the optimization can be performed on other measures, like the probability of improvement, which is $\mathbb{P}_m[O(\mathbf{p}) < O(\mathbf{p}_m^*)]$.

In compact form, the iterative process can be outlined as follows:

+   - **step 1**: compute $O(\mathbf{p}^{(m)})$ for $m = 1, \dots, M_0$ values of parameters.
+   - **step 2a**: compute sequentially the posterior density of $O$ on all available points.
+   - **step 2b**: compute the optimal new point to test $\mathbf{p}^{m+1}$ given in Equation (10.12).
+   - **step 2c**: compute the new objective value $O(\mathbf{p}^{m+1})$.

+   - **step 3**: repeat steps 2a to 2c as much as deemed reasonable and return the $\mathbf{p}^m$ that yields the smallest objective value.

The interested reader can have a look at Snoek et al. (2012) and Frazier (2018) for more details on the numerical facets of this method.

Finally, for the sake of completeness, we mention a last way to tune hyperparameters. Since the optimization scheme is $\underset{\mathbf{p}}{\text{argmin}} O(\mathbf{p})$, a natural way to proceed would be to use the sensitivity of $O$ with respect to $\mathbf{p}$. Indeed, if the gradient $\frac{\partial O}{\partial p_i}$ is known, then a gradient descent will always improve the objective value. The problem is that it is hard to compute a reliable gradient (finite differences can become costly). Nonetheless, some methods (e.g., Maclaurin et al. (2015)) have been applied successfully to optimize over large dimensional parameter spaces.

We conclude by mentioning the survey Bouthillier and Varoquaux (2020), which spans 2 major AI conferences that took place in 2019. It shows that most papers resort to hyperparameter tuning. The two most often cited methods are *manual tuning* (hand-picking) and *grid search*.