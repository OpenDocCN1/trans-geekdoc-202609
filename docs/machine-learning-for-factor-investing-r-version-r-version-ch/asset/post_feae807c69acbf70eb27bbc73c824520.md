
thereby following the conventions from Gelman et al. (2013). This notation is suboptimal in this book nonetheless because in all other chapters, **y** stands for the label of a dataset.

In Bayesian analysis, one sophistication (compared to a frequentist approach) comes from the fact that the data is not almighty. The distribution of the parameter \(\theta\) will be a mix between some **prior** distribution set by the statistician (the user, the analyst) and the empirical distribution from the data. More precisely, a simple application of Bayes’ formula yields

\(p(\theta|\mathbf{y}) = \frac{p(\theta)p(\mathbf{y}|\theta)}{p(\mathbf{y})} \propto p(\theta)p(\mathbf{y}|\theta).\)

The interpretation is immediate: the distribution of \(\theta\) knowing the data \(\mathbf{y}\) is proportional to the distribution of \(\theta\) times the distribution of \(\mathbf{y}\) knowing \(\theta\). The term \(p(\mathbf{y})\) is often omitted because it is simply a scaling number that ensures that the density sums or integrates to one.

We use a slightly different notation between Equation (9.1) and Equation (9.2). In the former, \(P\) denotes a true probability, i.e., it is a number. In the latter, \(p\) stands for the whole probability density function of \(\theta\) or \(\mathbf{y}\).

The whole purpose of Bayesian analysis is to compute the so-called **posterior** distribution \(p(\theta|\mathbf{y})\) via the **prior** distribution \(p(\theta)\) and the **likelihood function** \(p(\mathbf{y}|\theta)\). Priors are sometimes qualified as informative, weakly informative or uninformative, depending on the degree to which the user is confident on the relevance and robustness of the prior. The simplest way to define a non-informative prior is to set a constant (uniform) distribution over some realistic interval(s).

The most challenging part is usually the likelihood function. The easiest way to solve the problem is to resort to a specific distribution (possibly a parametric family) for the distribution of the data and then consider that observations are i.i.d., just as in a simple maximum likelihood inference. If we assume that new parameters for the distributions are gathered into \(\lambda\), then the likelihood can be written as

\(p(\mathbf{y}|\theta, \lambda) = \prod_{i=1}^{I} f_{\lambda}(y_i; \beta),\)

but in this case the problem becomes slightly more complex because adding new parameters changes the posterior distribution to \(p(\theta, \lambda|\mathbf{y})\). The user must find out the joint distribution of \(\theta\) and \(\lambda\) - given \(\mathbf{y}\). Because of their nested structure, these models are often called **hierarchical models**.

Bayesian methods are widely used for portfolio choice. The rationale is that the distribution of asset returns depends on some parameter and the main issue is to determine the posterior distribution. We very briefly review a vast literature below. Bayesian asset allocation is investigated in Lai et al. (2011) (via stochastic optimization), Guidolin and Liu (2016) and Dangl and Weissensteiner (2020). Shrinkage techniques (of means and covariance matrices) are tested in Frost and Savarino (1986), Kan and Zhou (2007) and DeMiguel et al. (2015). In a similar vein, Tu and Zhou (2010) build priors that are coherent with asset pricing theories. Finally, Bauder et al. (2020) sample portfolio returns which allows to derive a Bayesian optimal frontier. We invite the interested reader to also delve in the references that are cited within these few articles.

## 9.2 Bayesian sampling

### 9.2.1 Gibbs sampling

One adjacent field of applications of Bayes' theorem is **simulation**. Suppose we want to simulate the multivariate distribution of a random vector **X** given by its density \(p = p(x_1, \dots, x_J)\). Often, the full distribution is complex, but its marginals are more accessible. Indeed, they are simpler because they depend on only one variable (when all other values are known):

\(p(X_j = x_j | X_1 = x_1, \dots, X_{j-1} = x_{j-1}, X_{j+1} = x_{j+1}, \dots, X_J = x_J) = p(X_j = x_j | \mathbf{X}_{-j} = \mathbf{x}_{-j}),\)

where we use the compact notation \(\mathbf{X}_{-j}\) for all variables except \(X_j\). One way to generate samples with law \(p\) is the following and relies both on the knowledge of the conditionals \(p(x_j | \mathbf{x}_{-j})\) and on the notion of **Markov Chain Monte Carlo**, which we outline below. The process is iterative and assumes that it is possible to draw samples of the aforementioned conditionals. We write \(x_j^m\) for the \(m^{th}\) sample of the \(j^{th}\) variable \((X_j)\). The simulation starts with a prior (or fixed, or random) sample \(\mathbf{x}^0 = (x_1^0, \dots, x_J^0)\). Then, for a sufficiently large number of times, say \(T\), new samples are drawn according to

```
\(x_1^{m+1} = p(X_1|X_2 = x_2^m, \dots, X_J = x_J^m);\)
\(x_2^{m+1} = p(X_2|X_1 = x_1^{m+1}, X_3 = x_3^m, \dots, X_J = x_J^m);\)
\(\dots\)
\(x_J^{m+1} = p(X_J|X_1 = x_1^{m+1}, X_2 = x_2^{m+1}, \dots, X_{J-1} = x_{J-1}^{m+1}).\)
```

The important detail is that after each line, the value of the variable is updated. Hence, in the second line, \(X_2\) is sampled with the knowledge of \(X_1 = x_1^{m+1}\) and in the last line, all variables except \(X_J\) have been updated to their \((m+1)^{th}\) state. The above algorithm is called Gibbs sampling. It relates to Markov chains because each new iteration depends only on the previous one.

Under some technical assumptions, as \(T\) increases, the distribution of \(\mathbf{x}_T\) converges to that of \(p\). The conditions under which the convergence occurs have been widely discussed in series of articles in the 1990s. The interested reader can have a look for instance at Tierney (1994), Roberts and Smith (1994), as well as at section 11.7 of Gelman et al. (2013).

Sometimes, the full distribution is complex and the conditional laws are hard to determine and to sample. Then, a more general method, called Metropolis-Hastings, can be used that relies on the rejection method for the simulation of random variables.

### 9.2.2 Metropolis-Hastings sampling

The Gibbs algorithm can be considered as a particular case of the Metropolis-Hastings (MH) method, which, in its simplest version, was introduced in Metropolis and Ulam (1949). The premise is similar: the aim is to simulate random variables that follow \(p(\mathbf{x})\) with the ability to sample from a simpler form \(p(\mathbf{x}|\mathbf{y})\) which gives the probability of the future state **x**, given the past one **y**.

Once an initial value for $\mathbf{x}$ has been sampled ($\mathbf{x}_0$), each new iteration ($m$) of the simulation takes place in three stages:

- 1. generate a candidate value $\mathbf{x}'_{m+1}$ from $p(\mathbf{x}|\mathbf{x}_m)$,
- 2. compute the acceptance ratio \(\alpha = \min \frac{p(\mathbf{x}_{m+1})p(\mathbf{x}_m|\mathbf{x}_{m+1})}{p(\mathbf{x}_m)p(\mathbf{x}'_{m+1}|\mathbf{x}_m)}\)
- 3. pick $\mathbf{x}_{m+1} = \mathbf{x}'_{m+1}$ with probability \(\alpha\) or stick with the previous value ($\mathbf{x}_{m+1} = \mathbf{x}_m$) with probability \(1 - \alpha\).

The interpretation of the acceptance ratio is not straightforward in the general case. When the sampling generator is symmetric (\(p(\mathbf{x}|\mathbf{y}) = p(\mathbf{y}|\mathbf{x})\)), the candidate is always chosen whenever \(p(\mathbf{x}'_{m+1}) \ge p(\mathbf{x}_m)\). If the reverse condition holds (\(p(\mathbf{x}'_{m+1}) < p(\mathbf{x}_m)\)), then the candidate is retained with odds equal to \(p(\mathbf{x}'_{m+1})/p(\mathbf{x}_m)\), which is the ratio of likelihoods. The more likely the new proposal, the higher the odds of retaining it.

Often, the first simulations are discarded in order to leave time to the chain to converge to a high probability region. This procedure (often called ‘burn in’) ensures that the first retained samples are located in a zone that is likely, i.e., that they are more representative of the law we are trying to simulate.

For the sake of brevity, we stick to a succinct presentation here, but some additional details are outlined in section 11.2 of Gelman et al. (2013) and in chapter 7 of Kruschke (2014).

## 9.3 Bayesian linear regression

Because Bayesian concepts are rather abstract, it is useful to illustrate the theoretical notions with a simple example. In a linear model, \(y_i = \mathbf{x}_i\mathbf{b} + \epsilon_i\) and it is often statistically assumed that the \(\epsilon_i\) are i.i.d. and normally distributed with zero mean and variance \(\sigma^2\). Hence, the likelihood of Equation (9.3) translates into

\(p(\epsilon|\mathbf{b}, \sigma) = \prod_{i=1}^I \frac{e^{-\frac{\epsilon_i^2}{2\sigma}}}{\sigma\sqrt{2\pi}} = (\sigma\sqrt{2\pi})^{-I} e^{-\frac{\sum \epsilon_i^2}{2\sigma^2}}\).

In a regression analysis, the data is given both by $\mathbf{y}$ and by $\mathbf{X}$, hence both are reported in the notations. Simply acknowledging that \(\epsilon = \mathbf{y} - \mathbf{Xb}\), we get

\(p(\mathbf{y}, \mathbf{X}|\mathbf{b}, \sigma) = \prod_{i=1}^I \frac{e^{-\frac{\epsilon_i^2}{2\sigma^2}}}{\sigma\sqrt{2\pi}} \tag{9.4}\)
\(= (\sigma\sqrt{2\pi})^{-I} e^{-\sum_{i=1}^I \frac{(y_i - \mathbf{x}_i \mathbf{b})^2}{2\sigma^2}} = (\sigma\sqrt{2\pi})^{-I} e^{-\frac{(\mathbf{y} - \mathbf{Xb})(\mathbf{y} - \mathbf{Xb})}{2\sigma^2}}\)
\(= \underbrace{(\sigma\sqrt{2\pi})^{-I} e^{-\frac{(\mathbf{y} - \mathbf{Xb})(\mathbf{y} - \mathbf{Xb})}{2\sigma^2}}}_{\text{depends on } \sigma \text{, not } \mathbf{b}} \times \underbrace{e^{-\frac{(\mathbf{b} - \hat{\mathbf{b}}) \mathbf{X} \mathbf{X} (\mathbf{b} - \hat{\mathbf{b}})}{2\sigma^2}}}_{\text{depends on both } \sigma \text{, and } \mathbf{b}} . \tag{9.5}\)

In the last line, the second term is a function of the difference \(\mathbf{b} - \hat{\mathbf{b}}\), where \(\hat{\mathbf{b}} = (\mathbf{X}'\mathbf{X})^{-1}\mathbf{X}'\mathbf{y}\).
