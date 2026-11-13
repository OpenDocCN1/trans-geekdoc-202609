The next step is to be more specific about the likelihood. This can be done non-parametrically (via kernel estimation) or with common distributions (Gaussian for continuous data, Bernoulli for binary data). In factor investing, the features are continuous, thus the Gaussian law is more adequate:

```
P[x_{i,k} = z|\mathbf{y}_i = c] = \frac{e^{-\frac{(z-m_c)^2}{2\sigma_c^2}}}{\sigma_c\sqrt{2\pi}},\n
```

where \(c\) is the value of the classes taken by \(y\) and \(\sigma_c\) and \(m_c\) are the standard error and mean of \(x_{i,k}\), conditional on \(y_i\) being equal to \(c\). In practice, each class is spanned, the training set is filtered accordingly and \(\sigma_c\) and \(m_c\) are taken to be the sample statistics. This Gaussian parametrization is probably ill-suited to our dataset because the features are uniformly distributed. Even after conditioning, it is unlikely that the distribution will be even remotely close to Gaussian. Technically, this can be overcome via a double transformation method. Given a vector of features \(\mathbf{x}_k\) with empirical cdf \(F_{\mathbf{x}_k}\), the variable

```
\tilde{\mathbf{x}}_k = \Phi^{-1} \left( F_{\mathbf{x}_k}(\mathbf{x}_k) \right),\n(9.13)
```

will have a standard normal law whenever \(F_{\mathbf{x}_k}\) is not pathological. Non-pathological cases are when the cdf is continuous and strictly increasing and when observations lie in the open interval (0,1). If all features are independent, the transformation should not have any impact on the correlation structure. Otherwise, we refer to the literature on the NORmal-To-Anything (NORTA) method (see, e.g., Chen (2001) and Coqueret (2017)).

Lastly, the prior \(P[\mathbf{y}]\) in Equation (9.12) is often either taken to be uniform across the classes (\(1/K\) for all \(k\)) or equal to the sample distribution.

We illustrate the naive Bayes classification tool with a simple example. While the package e1071 embeds such a classifier, the naivebayes library offers more options (Gaussian, Bernoulli, multinomial and nonparametric likelihoods). Below, since the features are uniformly distributed, thus the transformation in (9.13) amounts to apply the Gaussian quantile function (inverse cdf).

For visual clarity, we only use the small set of features.

```
library(naivebayes)\ngauss_features_train <- training_sample %>% # Load package\n  dplyr::select(features_short) %>% # Build sample\n  as.matrix() %>%\n  '*'(0.999) %>% # Features smaller than 1\n  + (0.0001) %>% # Features larger than 0\n  qnorm() %>% # Inverse Gaussian cdf\n  colnames<-(features_short)\nfit_NB_gauss <- naive_bayes(x = gauss_features_train, # Transformed features\n                            y = training_sample$R1M_Usd_C) # Label\nlayout(matrix(c(1,2,3,4,5,6,7, 4, 2, byrow = TRUE), # Organize graphs\n              widths=c(0.9,0.45))\npar(mar=c(1, 1, 1, 1))\nplot(fit_NB_gauss, prob = "conditional")
```