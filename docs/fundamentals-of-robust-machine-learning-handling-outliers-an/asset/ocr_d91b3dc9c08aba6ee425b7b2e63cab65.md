![](bbox=[0.11, 0.11, 0.57, 0.32])

Figure 1.8 One-dimensional Gaussian mixture.

then we would require that

```
$$\sum_{i=1}^K \pi_i = 1$$
```

in order to satisfy a basic probability axiom associated with a valid PDF.

**Example:** The graph shown in Figure 1.8 represents a one-dimensional Gaussian mixture. It is based on the Gaussian mixture model of Eq. (1.8.1). The parameters of the mixture are \(\pi_1 = 0.2, \pi_2 = 0.8, \mu_1 = 6, \sigma_1^2 = 2, \mu_2 = 18, \text{ and } \sigma_2^2 = 5\). When we draw a sample of 14 observations from such a distribution, we obtain a set of random points as depicted along the x-axis. This comprises the dataset that we are given without any prior knowledge about the original distribution. The objective is to identify the two clusters using this data and reconstruct the original distribution on which the sample was based, as represented earlier in Figure 1.4. That is, we want to build a model of an unknown distribution from which the data arose given only the random sample of points. The key concept is that data is always tied to some unknown distribution. The best we can do with the given data is to build an approximate model of it using machine learning.

**Exercise:** What is the area under the curve (AUC) of the Gaussian mixture of Figure 1.8 from \(-\infty\) to \(\infty\)?

**Ans.:** The AUC = 1.0 by definition of a valid probability distribution. In fact, all valid PDFs have normalizing constants to ensure that they integrate to 1.

# 1.8.2 Multidimensional Datasets

Consider a more realistic \(d\)-dimensional Gaussian distribution denoted by \(\mathcal{N}_d(\boldsymbol{\mu}, \boldsymbol{\Sigma})\), where \(\boldsymbol{\mu} = (\mu_1, ..., \mu_d)^\top\) and \(\boldsymbol{\Sigma}\) is a \(d \times d\) nonsingular covariance matrix. In its most general form, we have the following Gaussian mixture:

```
$$f_X(\boldsymbol{x}) = \sum_{i=1}^K \pi_i \mathcal{N}_d(\boldsymbol{\mu}_i, \boldsymbol{\Sigma}_i).$$ (1.8.2)
```