
## 3.5.3 Invariant priors

If we have “objective” prior knowledge about a problem in the form of invariances, we may be able to encode this into a prior, as we show below.

### 3.5.3.1 Translation-invariant priors

A location-scale family is a family of probability distributions parameterized by a location $\mu$ and scale $\sigma$. If $x$ is an rv in this family, then $y = a + bx$ is also an rv in the same family.

When inferring the location parameter $\mu$, it is intuitively reasonable to want to use a translation-invariant prior, which satisfies the property that the probability mass assigned to any interval, $[A, B]$ is the same as that assigned to any other shifted interval of the same width, such as $[A-c, B-c]$. That is,

```
\int_{A-c}^{B-c} p(\mu) d\mu = \int_A^B p(\mu) d\mu (3.237)
```

This can be achieved using

```
p(\mu) \propto 1 (3.238)
```

since

```
\int_{A-c}^{B-c} 1 d\mu = (B-c) - (A-c) = (B-A) = \int_A^B 1 d\mu (3.239)
```

This is the same as the Jeffreys prior for a Gaussian with unknown mean $\mu$ and fixed variance. This follows since $F(\mu) = 1/\sigma^2 \propto 1$, from Equation (3.62), and hence $p(\mu) \propto 1$.

### 3.5.3.2 Scale-invariant prior

When inferring the scale parameter $\sigma$, we may want to use a scale-invariant prior, which satisfies the property that the probability mass assigned to any interval $[A, B]$ is the same as that assigned to any other interval $[A/c, B/c]$, where $c > 0$. That is,

```
\int_{A/c}^{B/c} p(\sigma) d\sigma = \int_A^B p(\sigma) d\sigma (3.240)
```

This can be achieved by using

```
p(\sigma) \propto 1/\sigma (3.241)
```

since then

```
\int_{A/c}^{B/c} \frac{1}{\sigma} d\sigma = [\log \sigma]_{A/c}^{B/c} = \log(B/c) - \log(A/c) = \log(B) - \log(A) = \int_A^B \frac{1}{\sigma} d\sigma (3.242)
```

This is the same as the Jeffreys prior for a Gaussian with fixed mean $\mu$ and unknown scale $\sigma$. This follows since $F(\sigma) = 2/\sigma^2$, from Equation (3.62), and hence $p(\sigma) \propto 1/\sigma$.

### 3.5.3.3 Learning invariant priors

Whenever we have knowledge of some kind of invariance we want our model to satisfy, we can use this to encode a corresponding prior. Sometimes this is done analytically (see e.g., [Rob07, Ch.9]). When this is intractable, it may be possible to learn invariant priors by solving a variational optimization problem (see e.g., [NS18]).

## 3.5.4 Reference priors

One way to define a noninformative prior is as a distribution which is maximally far from all possible posteriors, when averaged over datasets. This is the basic idea behind a **reference prior** [Ber05; BBS09]. More precisely, we say that \( p(\theta) \) is a reference prior if it maximizes the expected KL divergence between posterior and prior:

```
$$ p^*(\theta) = \underset{p(\theta)}{\text{argmax}} \int_{\mathcal{D}} p(\mathcal{D}) D_{\text{KL}} (p(\theta|\mathcal{D}) \| p(\theta)) d\mathcal{D} \quad (3.243) $$
```

where \( p(\mathcal{D}) = \int p(\mathcal{D}|\theta)p(\theta)d\theta \). This is the same as maximizing the mutual information \( \mathbb{I}(\theta, \mathcal{D}) \). We can eliminate the integral over datasets by noting that

```
$$ \int p(\mathcal{D}) \int p(\theta|\mathcal{D}) \log \frac{p(\theta|\mathcal{D})}{p(\theta)} = \int p(\theta) \int p(\mathcal{D}|\theta) \log \frac{p(\mathcal{D}|\theta)}{p(\mathcal{D})} = \mathbb{E}_{\theta} [D_{\text{KL}} (p(\mathcal{D}|\theta) \| p(\mathcal{D}))] \quad (3.244) $$
```

where we used the fact that \( \frac{p(\theta|\mathcal{D})}{p(\theta)} = \frac{p(\mathcal{D}|\theta)}{p(\mathcal{D})} \).

One can show that, in 1d, the corresponding prior is equivalent to the Jeffreys prior. In higher dimensions, we can compute the reference prior for one parameter at a time, using the chain rule. However, this can become computationally intractable. See [NS17] for a tractable approximation based on variational inference (Section 10.1).

## 3.6 Hierarchical priors

Bayesian models require specifying a prior \( p(\theta) \) for the parameters. The parameters of the prior are called **hyperparameters**, and will be denoted by \( \xi \). If these are unknown, we can put a prior on them; this defines a **hierarchical Bayesian model**, or **multi-level model**, which can be visualized like this: \( \xi \to \theta \to \mathcal{D} \). We assume the prior on the hyper-parameters is fixed (e.g., we may use some kind of minimally informative prior), so the joint distribution has the form

```
$$ p(\xi, \theta, \mathcal{D}) = p(\xi)p(\theta|\xi)p(\mathcal{D}|\theta) \quad (3.245) $$
```

The hope is that we can learn the hyperparameters by treating the parameters themselves as datapoints.

A common setting in which such an approach makes sense is when we have \( J > 1 \) related datasets, \( \mathcal{D}_j \), each with their own parameters \( \theta_j \). Inferring \( p(\theta_j|\mathcal{D}_j) \) independently for each group \( j \) can give poor results if \( \mathcal{D}_j \) is a small dataset (e.g., if condition \( j \) corresponds to a rare combination of features, or a sparsely populated region). We could of course pool all the data to compute a single model, \( p(\theta|\mathcal{D}) \), but that would not let us model the subpopulations. A hierarchical Bayesian model lets us borrow statistical strength from groups with lots of data (and hence well-informed posteriors \(p(\theta_j|\mathcal{D})\)) in order to help groups with little data (and hence highly uncertain posteriors \(p(\theta_j|\mathcal{D})\)). The idea is that well-informed groups \(j\) will have a good estimate of \(\theta_j\), from which we can infer \(\xi\), which can be used to help estimate \(\theta_k\) for groups \(k\) with less data. (Information is shared via the hidden common parent node \(\xi\) in the graphical model, as shown in Figure 3.14.) We give some examples of this below.

After fitting such models, we can compute two kinds of posterior predictive distributions. If we want to predict observations for an existing group \(j\), we need to use

\(p(y_j|\mathcal{D}) = \int p(y_j|\theta_j)p(\theta_j|\mathcal{D})d\theta_j\) (3.246)

However, if we want to predict observations for a new group that has not yet been measured, but which is comparable to (or **exchangeable with**) the existing groups \(1:J\), we need to use

\(p(y_*|\mathcal{D}) = \int p(y_*|\theta_*)p(\theta_*|\xi)p(\xi|\mathcal{D})d\theta_*d\xi\) (3.247)

We give some examples below. (More information can be found in e.g., [GH07; Gel+14a].)

### 3.6.1 A hierarchical binomial model

Suppose we want to estimate the prevalence of some disease amongst different groups of individuals, either people or animals. Let \(N_j\) be the size of the \(j\)'th group, and let \(y_j\) be the number of positive cases for group \(j = 1:J\). We assume \(y_j \sim \text{Bin}(N_j, \theta_j)\), and we want to estimate the rates \(\theta_j\). Since some groups may have small population sizes, we may get unreliable results if we estimate each \(\theta_j\) separately; for example we may observe \(y_j = 0\) resulting in \(\hat{\theta}_j = 0\), even though the true infection rate is higher.

One solution is to assume all the \(\theta_j\) are the same; this is called **parameter tying**. The resulting pooled MLE is just \(\hat{\theta}_{\text{pooled}} = \frac{\sum_j y_j}{\sum_j N_j}\). But the assumption that all the groups have the same rate is a rather strong one. A compromise approach is to assume that the \(\theta_j\) are similar, but that there may be group-specific variations. This can be modeled by assuming the \(\theta_j\) are drawn from some common distribution, say \(\theta_j \sim \text{Beta}(a, b)\). The full joint distribution can be written as

\(p(\mathcal{D}, \theta, \xi) = p(\xi)p(\theta|\xi)p(\mathcal{D}|\theta) = p(\xi) \left[ \prod_{j=1}^J \text{Beta}(\theta_j|\xi) \right] \left[ \prod_{j=1}^J \text{Bin}(y_j|N_j, \theta_j) \right]\) (3.248)

where \(\xi = (a, b)\). In Figure 3.14 we represent these assumptions using a directed graphical model (see Section 4.2.8 for an explanation of such diagrams).

It remains to specify the prior \(p(\xi)\). Following [Gel+14a, p110], we use

\(p(a, b) \propto (a + b)^{-5/2}\) (3.249)
