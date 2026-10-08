
a single value for $\mu$, but a posterior distribution over $\mu$. All possible values are considered by taking the integral

```
$p(x|D) = \int_{\alpha}^{\beta} p(x|\mu) f(\mu|N, \alpha, \beta) d\mu = \int_{m+\alpha}^{N} \mu f(\mu,N, \alpha, \beta) d\mu = \mathcal{E}(\mu|N, \alpha, \beta)$ (2.21)
```

Because of the inclusion of $\alpha$ and $\beta$, the probability can never become zero, even if $m=0$ or $1$, if $m=N$, contrary to the MLE it incorporates the uncertainty caused by using a *finite* set of data.

The above result no longer depends on $\mu$. It is an example of a *latent* variable.

Figure 2.30 shows how the beta distribution changes from a prior distribution with $\alpha=\beta=2$ as more data is observed. If zero stands for tails when flipping a coin, the second to seventh plots a sequence of three times followed by three heads. As more tails are observed, the mean of the distribution moves to the left, with more observations of heads, it moves right towards the center. The last is after 100 coin flips, where an equal number of heads and tails are observed. The posterior distribution becomes more peaked around $N$ increases, $\alpha$ and $\beta$ become relatively small compared to $\mu$, and $p(x=1|D)$ approaches the maximum likelihood estimate $\mu_{ML}$ for $D$ which is $m/N$.

As seen in Figure 2.30, this approach can be used in online learning where data arrives are updated when more knowledge is gained. It can also be used for large datasets, where it is not possible to load all data into memory at the same time.

The beta distribution is the conjugate distribution to the Bernoulli and binomial distribution. It was motivated by choosing a appropriate prior describing an unknown parameter ($\mu$). There is also a mathematical motivation, since the posterior distribution arising from Bayes' rule has the same functional form as the prior and therefore can be determined in closed form. This is not always the case. When choosing appropriate distributions to describe the data, mathematical convenience should play a subordinate role to data and expert knowledge.

If the data is categorical in nature, the outcomes are described using a One-of-K representation and follow the categorical distribution as given in (2.9). Let $D=\{\mathbf{x}_1, \dots, \mathbf{x}_N\}$ be the results of experiments. The likelihood of such data is

```
$p(D|\mu) = \prod_{n=1}^N \text{Cat}(\mathbf{x}_n|\mu) = \prod_{n=1}^N \prod_{k=1}^K \mu_k^{x_{nk}} = \prod_{k=1}^K \mu_k^{\sum_{n=1}^N x_{nk}}$
```

Since $x_n$ is a 1-of-K representation, let $m_k$ the number of times we have

Prior: $\alpha = \beta = 2$

![](img/c6c76bf52016db7e78a5e30d4766ef81_83_0.png)

$\mathcal{D} = \{0\}$

![](img/c6c76bf52016db7e78a5e30d4766ef81_83_1.png)

$\mathcal{D} = \{(0,0)\}$

![](img/c6c76bf52016db7e78a5e30d4766ef81_83_2.png)

$\mathcal{D} = \{(0,0,0)\}$

![](img/c6c76bf52016db7e78a5e30d4766ef81_83_3.png)

$\mathcal{D} = \{(0,0,0,1)\}$

![](img/c6c76bf52016db7e78a5e30d4766ef81_83_4.png)

$\mathcal{D} = \{(0,0,0,1,1)\}$

![](img/c6c76bf52016db7e78a5e30d4766ef81_83_5.png)

Figure 2.30: Prior (top left) and posterior beta probability distributions after some observations. The bottom right shows the beta distribution after an equal number of zeros and ones.

$x_{nk} = 1$ for $n = 1, \dots, N$. The likelihood then becomes

$p(\mathcal{D}|\mu) = \prod_{k=1}^{K} \mu_k^{m_k}$

Again an estimate for $\mu$ can be found by maximizing the likelihood, or equivalently its logarithm. However, this task is not as straightforward as before, since $\mu$ has to satisfy the constraints

$$\sum_{k=1}^{K} \mu_k = 1 \quad \text{and} \quad 0 \leq \mu_k \leq 1, k = 1, \dots, K.$$

hence the task is a constraint optimization.

Let $i$ be any index in $\{1, \dots, K\}$. We incorporate the first constraint noting

$$\mu_i = 1 - \sum_{k \neq i} \mu_k.$$

With this modification, the log likelihood is

$$\log p(D|\mu) = \sum_{k} m_k \log \mu_k + m_j \log \mu_j \left( 1 - \sum_{k \neq j} \mu_k \right).$$

Let $j \neq i$ be any other index. The parameter $\mu_j$ appears in both sums, and the derivative with respect to $\mu_j$ is

$$\frac{d \log p(D|\mu)}{d \mu_j} = \frac{m_j}{\mu_j} - \frac{m_i}{1 - \sum_{k \neq j} \mu_k} \frac{\mu_i}{\mu_j}.$$

Setting this to zero, we find that the ratio of $\mu_j$ to $\mu_i$ to be the same as the ratio $m_j$ to $m_i$. Since $i$ and $j$ are freely chosen, the ratio of any pair of $\mu$ must be the ratio of the corresponding pair in $\mathbf{m} = (m_1, \dots, m_K)$. The only possible choice for $\mu_k$, which satisfies the second constraint to lie between zero and one, is the MLE

$$\mu_k = \frac{m_k}{m_1 + \dots + m_K}, \quad k = 1, \dots, K.$$

As this could be a poor estimate if $N$ is not large enough. Constraint problems often occur in Machine Learning. A general technique uses *Lagrange multipliers*, which we will encounter in Section 4.6. For more background on optimization see Bertsimas & Tsitsik (1997). The vector $\mu$ of the probabilities of different outcomes needs to be estimated. The Dirichlet distribution $\text{Dir}(\mu|\alpha)$ is chosen as conjugate prior for $\mu$, where $\alpha$ is suitably chosen. The posterior density function is proportional to the product of the likelihood and the prior (which is the joint distribution):

$$f(\mu|\alpha) \propto \prod_{k=1}^K \mu_k^{\alpha_k - 1},$$

where all constants were dropped due to the proportional sign. The posterior has again functional form of Dirichlet distribution. Incorporating the factor such that the posterior integrates to

$$f(\mu|\alpha) = \frac{\Gamma(\alpha_0 + N)}{\Gamma(\alpha_1 + m_1) \dots \Gamma(\alpha_K + m_K)} \prod_{k=1}^K \mu_k^{\alpha_k - 1} = \text{Dir}(\mu|\alpha),$$

where $\alpha_0 = \alpha_1 + \cdots \alpha_K$.

As before with the beta distribution, the knowledge gained from the experiments is given by $\mathbf{m}$ and modifies the location of the mean and the shape of the distribution. The parameters $\alpha$ and $\beta$ in the prior beta distribution and $\alpha$ in the prior Dirichlet distribution can be viewed as initial guesses of the true distribution informed by expert knowledge and experience.

The probability of a particular outcome $x_k = 1$ is

```
$p(x_k = 1) = \int p(x_k|\mu)f(\mu|\mathbf{m}, \alpha)d\mu$
```

where the integral is over the simplex, $\mu$ must lie. $p(x_k = 1|D)=$

```
$p(x_k=1|D) = \int \mu f(\mu|\mathbf{m}, \alpha)d\mu = E[\mu|\mathbf{m}, \alpha] = \frac{m_k + \alpha_k}{N + \alpha_0}. \quad (2.22)$
```

depends on $\mu$ and therefore $\mu$ is a latent variable.

We have seen two examples of probability distributions and will see more. For example, if the mean of a normal distribution is the unknown parameter, the conjugate prior is also a normal distribution. Gelman et al. (2013) gives a more thorough treatment of *conjugacy*.

# 2.7 Graphical Representations

In the previous section, the joint probability distribution followed by Bayes' rule was used, to achieve better predictions for seeing a particular outcome. In the following, we illustrate the dependencies between random variables and can be visualized.

The elements of a graph are *nodes*, also known as *vertices*, and *edges*, also called *links* or *arcs*. In a graphical representation, each node represents random variables, which could be a vector, group of random variables, or parameter or group of parameters. If there is a relationship between nodes, they are joined by an edge. If there is a directed relationship between nodes, the edge has a direction indicated by an arrow. This is a *directed graph*.

Let $D=\{x_1, \dots, x_n\}$ be a set of observed, binary variables. In (2.20), the data $D$ is governed by the latent variable $\mu$, which in turn is governed by the parameters $\alpha$ and $\beta$. The corresponding graph is:

![](img/c6c76bf52016db7e78a5e30d4766ef81_86_0.png)

The nodes of random variables are circles, while the nodes of parameters are clear. Random variables which are observed are shaded, $x_1$, latent ones, which are not observed, are not shaded. The observations $x_1, \dots, x_N$ are of the same nature. The graph can become cluttered when writing these out as individual nodes. They are summarized as a representative node $x_n$ surrounded by a box, called a *plate*, labelled with $N$ showing there are $N$ of these.

![](img/c6c76bf52016db7e78a5e30d4766ef81_86_1.png)

Equation (2.21) gives the probability of $x=1$ having the data $\mathcal{D}$ into
