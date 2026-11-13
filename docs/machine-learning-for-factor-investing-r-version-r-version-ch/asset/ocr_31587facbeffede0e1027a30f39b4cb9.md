# 13.1.4 Partial dependence plot

Partial dependence plots (PDPs) aim at showing the relationship between the output of a model and the value of a feature (we refer to section 8.2 of Friedman (2001) for an early treatment of this subject).

Let us fix a feature $k$. We want to understand the **average impact** of $k$ on the predictions of the trained model $\hat{f}$. In order to do so, we assume that the feature space is random and we split it in two: $k$ versus $-k$, which stands for all features except for $k$. The partial dependence plot is defined as

\(\bar{f}_k(x_k) = \mathbb{E}[\hat{f}(\mathbf{x}_{-k}, x_k)] = \int \hat{f}(\mathbf{x}_{-k}, x_k) \, d\mathbb{IP}_{-k}(\mathbf{x}_{-k}),\) (13.1)

where \(d\mathbb{IP}_{-k}(\cdot)\) is the (multivariate) distribution of the non-$k$ features \(\mathbf{x}_{-k}\). The above function takes the feature values $x_k$ as argument and keeps all other features frozen via their sample distributions: this shows the impact of feature $k$ solely. In practice, the average is evaluated using Monte-Carlo simulations:

\(\bar{f}_k(x_k) \approx \frac{1}{M} \sum_{m=1}^M \hat{f} \, x_k, \mathbf{x}_{-k}^{(m)} ,\) (13.2)

where \(\mathbf{x}_{-k}^{(m)}\) are independent samples of the non-$k$ features.

Theoretically, PDPs could be computed for more than one feature at a time. In practice, this is only possible for two features (yielding a 3D surface) and is more computationally intense.

We illustrate this concept below, using the dedicated package *iml* (interpretable machine learning); see also the *pdp* package documented in Greenwell (2017). The model we seek to explain is the random forest built in Section 6.2. We recycle some variables used therein. We choose to test the impact of the price-to-book ratio on the outcome of the model.

```
library(iml)
mod_iml <- Predictor$new(fit_RF,
                         data = training_sample %>% dplyr::select(features))
pdp_PB = FeatureEffects$new(mod_iml, feature = "Pb")
plot(pdp_PB)
# One package for interpretability
# This line encapsulates the objects
# This line computes the PDP for p/b ratio
# Plot the partial dependence.
```