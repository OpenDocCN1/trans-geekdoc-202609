where $\alpha_0 = \alpha_1 + \cdots \alpha_K$.

As before with the beta distribution, the knowledge gained from the experiments is given by $\mathbf{m}$ and modifies the location of the mean and the shape of the distribution. The parameters $\alpha$ and $eta$ in the prior beta distribution and $\alpha$ in the prior Dirichlet distribution can be viewed as initial guesses of the true distribution or fictional trials informed by expert knowledge and experience.

The probability of a particular outcome $x_k = 1$ is

```
$p(x_k = 1) = \int p(x_k|\mu)f(\mu|\mathbf{m}, \alpha)d\mu$
```

where the integral is over the simplex, $\mu$ must lie. $p(x_k = 1|mu) =$

```
$p(x_k=1|D) = \int \mu f(\mu|\mathbf{m}, \alpha)d\mu = E[\mu|\mathbf{m}, \alpha] = \frac{m_k + \alpha_k}{N + \alpha_0}. \quad (2.22)$
```

longer depends on $\mu$ and therefore $\mu$ is a latent variable.

We have seen two examples of probability distributions and will see more. For example, if the mean of a normal distribution is the unknown parameter, the conjugate prior is also a normal distribution. Gelman et al. (2013) gives a more thorough treatment of *conjugacy*.

# 2.7 Graphical Representations

In the previous section, the joint probability distribution followed by Bayes' rule was used, to achieve better predictions for seeing a particular outcome. In the following, we illustrate the dependencies between random variables and can be visualized.

The elements of a graph are *nodes*, also known as *vertices*, and *edges*, also called *links* or *arcs*. In a graphical representation, each node represents random variables, which could be a vector, group of random variables, or parameter or group of parameters. If there is a relationship between nodes, they are joined by an edge. If there is a directed relationship between nodes, the edge has a direction indicated by an arrow. This is a *directed graph*.

Let $D=\{x_1, \dots, x_n\}$ be a set of observed, binary variables. In (2.20), the data $D$ is governed by the latent variable $\mu_$, which in turn is governed by the