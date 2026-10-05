# Biological Pattern Discovery with R

After modelling, the model parameters were extracted. The mean values for two Gaussian densities were 0.27 and 8.91, obtained using the following code:

```
mu=model$parameter$mean
```

The mixing coefficients of the two components in this mixture were 0.86 and 0.14, obtained using the following code:

```
w=model$parameter$pro
```

The standard deviation of the components was 1.62, obtained using the following code,

```
sigma=sqrt(model$parameter$variance$sigmas)
```

Based on these two components, a Gaussian mixture for this data set was estimated using the following code,

```
mixture1=dnorm(x0,mean=mu[1], sd=sigma)
mixture2=dnorm(x0,mean=mu[2], sd=sigma)
w=w[1]*mixture1+w[2]*mixture2
```

In the above code, mixture and mixture2 stand for two components. They were mixed using two mixing coefficients, i.e., w[1] and w[2]. Note that in the above code, two components had an identical variance. If two components had different variances, they should be clearly spelt out,

```
mixture1=dnorm(x0,mean=mu[1], sd=sigma[1])
mixture2=dnorm(x0,mean=mu[2], sd=sigma[2])
w=w[1]*mixture1+w[2]*mixture2
```

# 2.2.4.2 Gamma mixture

The Gamma mixture has been popular for analysing biology data with positive continuous values. A Gamma component density is defined as below,

> $$\mathcal{T}(\alpha, \beta) = \frac{\beta^\alpha x^{\alpha-1}e^{-\beta x}}{\Gamma(\alpha)}$$ (2.13)