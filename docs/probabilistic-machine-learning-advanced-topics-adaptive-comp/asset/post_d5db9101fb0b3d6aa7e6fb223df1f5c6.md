
### 3.8.7.1 Minimum description length (MDL)

We can think about the problem of scoring different models in terms of information theory (Chapter 5). The goal is for the sender to communicate the data to the receiver. First the sender needs to specify which model m to use; this takes C(m) = -log p(m) bits (see Section 5.2). Then the receiver can fit the model, by computing \(\hat{\theta}_m\), and can thus approximately reconstruct the data. To perfectly reconstruct the data, the sender needs to send the residual errors that cannot be explained by the model; this takes

```
-L(m) = - \log p(\mathcal{D}|\hat{\theta}, m) = - \sum_n \log p(y_n | x_n, \hat{\theta}, m)
```

bits. (We are ignoring the cost of sending the input features \(\boldsymbol{x}_n\), if present.) The total cost is

```
\mathcal{L}_{\text{MDL}}(m) = - \log p(\mathcal{D}|\hat{\theta}, m) + C(m)
```

Choosing the model which minimizes this cost is known as the minimum description length or MDL principle. See e.g., [HY01] for details.

### 3.8.7.2 The Bayesian information criterion (BIC)

The Bayesian information criterion or BIC [Sch78] is similar to the MDL, and has the form

```
\mathcal{L}_{\text{BIC}}(m) = -2 \log p(\mathcal{D}|\hat{\theta}, m) + D_m \log N
```

where D_m is the degrees of freedom of model m.

We can derive the BIC score as a simple approximation to the log marginal likelihood. In particular, suppose we make a Gaussian approximation to the posterior, as discussed in Section 7.4.3. Then we get (from Equation (7.28)) the following:

```
\log p(\mathcal{D}|m) \approx \log p(\mathcal{D}|\hat{\theta}_{\text{map}}) + \log p(\hat{\theta}_{\text{map}}) - \frac{1}{2} \log |\mathbf{H}|
```

where H is the Hessian of the negative log joint log p(\(\mathcal{D}, \theta\)) evaluated at the MAP estimate \(\hat{\theta}_{\text{map}}\). We see that Equation (3.309) is the log likelihood plus some penalty terms. If we have a uniform prior, \(p(\theta) \propto 1\), we can drop the prior term, and replace the MAP estimate with the MLE, \(\hat{\theta}\), yielding

```
\log p(\mathcal{D}|m) \approx \log p(\mathcal{D}|\hat{\theta}) - \frac{1}{2} \log |\mathbf{H}|
```

We now focus on approximating the log \(|\mathbf{H}|\) term, which is sometimes called the Occam factor, since it is a measure of model complexity (volume of the posterior distribution). We have \(\mathbf{H} = \sum_{i=1}^N \mathbf{H}_i\), where \(\mathbf{H}_i = \nabla \nabla \log p(\mathcal{D}_i | \theta)\). Let us approximate each \(\mathbf{H}_i\) by a fixed matrix \(\hat{\mathbf{H}}\). Then we have

```
\log |\mathbf{H}| = \log |N \hat{\mathbf{H}}| = \log (N^D |\hat{\mathbf{H}}|) = D \log N + \log |\hat{\mathbf{H}}|
```

where D = \(\dim(\theta)\) and we have assumed H is full rank. We can drop the log \(|\hat{\mathbf{H}}|\) term, since it is independent of N, and thus will get overwhelmed by the likelihood. Putting all the pieces together, we get the BIC score that we want to maximize:

```
J_{\text{BIC}}(m) = \log p(\mathcal{D}|\hat{\theta}, m) - \frac{D_m}{2} \log N
```

We can also define the **BIC loss**, that we want to minimize, by multiplying by $-2$:

```
$\mathcal{L}_{\text{BIC}}(m) = -2 \log p(\mathcal{D}|\hat{\theta}, m) + D_m \log N$
```

### 3.8.7.3 Akaike information criterion

The **Akaike information criterion** [Aka74] is closely related to BIC. It has the form

```
$\mathcal{L}_{\text{AIC}}(m) = -2 \log p(\mathcal{D}|\hat{\theta}, m) + 2 D_m$
```

This penalizes complex models less heavily than BIC, since the regularization term is independent of $N$. This estimator can be derived from a frequentist perspective.

### 3.8.7.4 Widely applicable information criterion (WAIC)

The main problem with MDL, BIC, and AIC is that it can be hard to compute the degrees of freedom of a model, needed to define the complexity term, since most parameters are highly correlated and not uniquely identifiable from the likelihood. In particular, if the mapping from parameters to the likelihood is not one-to-one, then the model is known as a **singular statistical model**, since the corresponding Fisher information matrix (Section 3.3.4), and hence the Hessian **H** above, may be singular (have determinant 0). An alternative criterion that works even in the singular case is known as the **widely applicable information criterion** (WAIC), also known as the **Watanabe–Akaike information criterion** [Wat10; Wat13].

WAIC is like other information criteria, except it is more Bayesian. First it replaces the log likelihood $L(m)$, which uses a point estimate of the parameters, with the LPPD, which marginalizes them out. (see Equation (3.295)). For the complexity term, WAIC uses the variance of the predictive distribution:

```
$C(m) = \sum_{n=1}^N \mathbb{V}_{\theta|\mathcal{D},m}[\log p(y_n|x_n, \theta, m)] \approx \sum_{n=1}^N \mathbb{V}\{\log p(y_n|x_n, \theta_s, m) : s = 1 : S\}$
```

The intuition for this is as follows: if, for a given datapoint $n$, the different posterior samples $\theta_s$ make very different predictions, then the model is uncertain, and likely too flexible. The complexity term essentially counts how often this occurs. The final WAIC loss is

```
$\mathcal{L}_{\text{WAIC}}(m) = -2 \text{LPPD}(m) + 2 C(m)$
```

Interestingly, it can be shown that the PSIS LOO estimate in Section 3.8.6 is asymptotically equivalent to WAIC [VGG17].

## 3.9 Model checking

Bayesian inference and decision making is optimal, but only if the modeling assumptions are correct. In this section, we discuss some ways to assess if a model is reasonable. From a Bayesian perspective, this can seem a bit odd, since if we knew there was a better model, why don’t we just use that? Here we assume that we do not have a specific alternative model in mind (so we are not performing model selection, unlike Section 3.8.1). Instead we are just trying to see if the data we observe is “typical” of what we might expect if our model were correct. This is called **model checking**.

### 3.9.1 Posterior predictive checks

Suppose we are trying to estimate the probability of heads for a coin, \(\theta \in [0, 1]\). We have two candidate models or hypotheses, \(M_1\) which corresponds to \(\theta = 0.99\) and \(M_2\) which corresponds to \(\theta = 0.01\). Suppose we flip the coin 40 times and it comes up heads 30 times. Obviously we have \(p(M = M_1 | \mathcal{D}) \gg p(M = M_2 | \mathcal{D})\). However model \(M_1\) is still a very bad model for the data. (This example is from [Kru15, p331].)

To evaluate how good a candidate model \(M\) is, after seeing some data \(\mathcal{D}\), we can imagine using the model to generate synthetic future datasets, by drawing from the posterior predictive distribution:

```
\(\tilde{\mathcal{D}}^s \sim p(\tilde{\mathcal{D}} | M, \mathcal{D}) = \{y_{1:N}^s \sim p(\cdot | M, \theta^s), \theta^s \sim p(\theta | \mathcal{D}, M)\}\)
```

These represent "plausible hallucinations" of the model. To assess the quality of our model, we can compute how "typical" our observed data \(\mathcal{D}\) is compared to the model's hallucinations. To perform this comparison, we create one or more scalar **test statistics**, \(\text{test}(\tilde{\mathcal{D}}^s)\), and compare them to the test statistics on the actual data, \(\text{test}(\mathcal{D})\). These statistics should measure features of interest (since it will not, in general, be possible to capture every aspect of the data with a given model). If there is a large difference between the distribution of \(\text{test}(\tilde{\mathcal{D}}^s)\) across different \(s\) and the value of \(\text{test}(\mathcal{D})\), it suggests the model is not a good one. This approach is called a **posterior predictive check** [Rub84].

### 3.9.1.1 Example: 1d Gaussian

To make things clearer, let us consider an example from [Gel+04]. In 1882, Newcomb measured the speed of light using a certain method and obtained \(N = 66\) measurements, shown in Figure 3.25(a). There are clearly two outliers in the left tails, suggesting that the distribution is not Gaussian. Let us nonetheless fit a Gaussian to it. For simplicity, we will just compute the MLE, and use a plug-in approximation to the posterior predictive density:

```
\(p(\tilde{y} | \mathcal{D}) \approx \mathcal{N}(\tilde{y} | \hat{\mu}, \hat{\sigma}^2), \quad \hat{\mu} = \frac{1}{N} \sum_{n=1}^N y_n, \quad \hat{\sigma}^2 = \frac{1}{N} \sum_{n=1}^N (y_n - \hat{\mu})^2\)
```

Let \(\tilde{\mathcal{D}}^s\) be the \(s\)’th dataset of size \(N = 66\) sampled from this distribution, for \(s = 1 : 1000\). The histogram of \(\tilde{\mathcal{D}}^s\) for some of these samples is shown in Figure 3.25(b). It is clear that none of the samples contain the large negative examples that were seen in the real data. This suggests the model cannot capture the long tails present in the data. (We are assuming that these extreme values are scientifically interesting, and something we want the model to capture.)

A more formal way to test fit is to define a test statistic. Since we are interested in small values, let us use

```
\(\text{test}(\mathcal{D}) = \min\{y : y \in \mathcal{D}\}\)
```

The empirical distribution of \(\text{test}(\tilde{\mathcal{D}}^s)\) for \(s = 1 : 1000\) is shown in Figure 3.25(c). For the real data, \(\text{test}(\mathcal{D}) = -44\), but the test statistics of the generated data, \(\text{test}(\tilde{\mathcal{D}})\), are much larger. Indeed, we see that \(-44\) is in the left tail of the predictive distribution, \(p(\text{test}(\tilde{\mathcal{D}}) | \mathcal{D})\).
