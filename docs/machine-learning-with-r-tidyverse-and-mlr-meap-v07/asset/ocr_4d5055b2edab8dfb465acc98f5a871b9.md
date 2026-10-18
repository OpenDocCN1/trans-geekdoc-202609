# Listing 19.1 Performing and plotting mixture model clustering

```
```r
swissMclust <- Mclust(swissTib)

plot(swissMclust)
```
```

The first plot available to us shows the *Bayesian information criterion* (BIC) for the range of cluster numbers and model types the `Mclust()` function tried. This plot is shown in figure 19.3. The BIC is a metric for comparing the fit of different models, that penalizes us for having too many parameters in the model. The BIC is usually defined as in equation 19.9.

**EQUATION 19.9**

\[
BIC = \ln(n)p - 2\ln(L)
\]

where *n* is the number of cases, *p* is the number of parameters in the model, and *L* is the overall likelihood of the model.

Therefore, for a fixed likelihood, as the number of parameters increase, so the BIC increases. Conversely, for a fixed number of parameters, as the model likelihood increases, so the BIC decreases. Therefore the smaller the BIC, the better and/or more parsimonious our model is. Imagine we had two models, each of which fit the dataset equally well, but one has three parameters and the other has ten, the model with three parameters will have the lower BIC.

The form of BIC shown in the plot is actually sort of the other way around, and takes the form shown in equation 19.10. After being rearranged this way, better fitting and/or more parsimonious models will actually have a higher BIC value.

**EQUATION 19.10**

\[
BIC = L - 0.5 \times p \times \ln(n)
\]

So we know what the BIC is and how to interpret it, but what are all the lines in figure 19.3? Well the `Mclust()` function tries a range of cluster numbers for us, for a range of different model types. For each combination of model type and cluster number, the function evaluates the BIC. This information is conveyed in our BIC plot. But what do I mean when I say "model types"? I didn’t mention anything about this when I showed you how Gaussian mixture models work. When we train a mixture model, it’s possible to put constraints on the covariance matrix to reduce the number of parameters needed to describe the model. This can help to prevent us from overfitting the data.