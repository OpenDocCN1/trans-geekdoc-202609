A Gamma mixture is defined as below,

```
$f(x_i) = \sum_{k=1}^{K} w_k \mathcal{T}(x_i|\alpha_k, \beta_k) \eqno (2.14)$
```

The parameters of a Gamma mixture model can be estimated using the likelihood maximisation approach [Dempster, et al., 1977] or the Bayesian approach [Mohammadi, et al., 2013] as well. mixR is an R package for the Gamma mixture modelling using the likelihood maximisation approach. The function for estimating a Gamma mixture density in this package is mixfit. For instance, the following code was used to estimate the density of the first replicate of the airway sequencing count data [Himes, et al., 2014] if the raw count data have been saved in a matrix x. Only non-zero count data were logarithm transformed for the density estimate. Figure 2.15(a) shows the estimated density, which shows a clear Gamma mixture.

```
x=log(1+x)
z=as.numeric(x[which(x[,1]>0)],
model=mixfit(z,ncomp=2,family='gamma')
```

![](bbox=[0.196, 0.542, 0.772, 0.725])

Fig. 2.15. The Gamma mixture model for the first replicate of the airway sequencing count data. (a) The two component Gamma mixture model. Two thin curves stand for the component densities of two Gammas and the thick line stands for the final Gamma mixture density. (b) The model optimisation process based on the BIC in mixR.

The mixR package also has a function for optimising the model structure to select an optimal number of Gammas for a mixture based on the use of the Bayesian Information Criterion (BIC) [Schwarz, 1978]. To