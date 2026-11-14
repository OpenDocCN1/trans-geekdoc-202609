# 3.9.1 Posterior predictive checks

Suppose we are trying to estimate the probability of heads for a coin, \(\theta \in [0, 1]\). We have two candidate models or hypotheses, \(M_1\) which corresponds to \(\theta = 0.99\) and \(M_2\) which corresponds to \(\theta = 0.01\). Suppose we flip the coin 40 times and it comes up heads 30 times. Obviously we have \(p(M = M_1 | \mathcal{D}) \gg p(M = M_2 | \mathcal{D})\). However model \(M_1\) is still a very bad model for the data. (This example is from [Kru15, p331].)

To evaluate how good a candidate model \(M\) is, after seeing some data \(\mathcal{D}\), we can imagine using the model to generate synthetic future datasets, by drawing from the posterior predictive distribution:

```
\(\tilde{\mathcal{D}}^s \sim p(\tilde{\mathcal{D}} | M, \mathcal{D}) = \{y_{1:N}^s \sim p(\cdot | M, \theta^s), \theta^s \sim p(\theta | \mathcal{D}, M)\}\)
```

These represent "plausible hallucinations" of the model. To assess the quality of our model, we can compute how "typical" our observed data \(\mathcal{D}\) is compared to the model's hallucinations. To perform this comparison, we create one or more scalar **test statistics**, \(\text{test}(\tilde{\mathcal{D}}^s)\), and compare them to the test statistics on the actual data, \(\text{test}(\mathcal{D})\). These statistics should measure features of interest (since it will not, in general, be possible to capture every aspect of the data with a given model). If there is a large difference between the distribution of \(\text{test}(\tilde{\mathcal{D}}^s)\) across different \(s\) and the value of \(\text{test}(\mathcal{D})\), it suggests the model is not a good one. This approach called a **posterior predictive check** [Rub84].

# 3.9.1.1 Example: 1d Gaussian

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