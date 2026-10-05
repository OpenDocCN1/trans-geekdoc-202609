# 384

# MACHINE LEARNING

In the implementation below, we always provide two types of functions. One performs the normalisation in the sample, i.e. the entire sample is used to provide polarisation parameters. Thus, if the underlying data are a time series, both past and future values are used. This approach is convenient for all calibration and learning purposes. However, this is not convenient for out-of-sample testing or learning unless we want to change the normalisation with every new observation. For that purpose, we provide functions which have static parameters explicitly.

# 19.1.2.1  Normal Score

The common type of normalisation is based on the normal score, or z-score. The purpose of normalisation is to demean the mean and scale the variables to have unit variance. The z-score is defined as

```
z = \frac{X - \mu}{\sigma} (19.1)
```

where $\mu$ is the mean of the variable $X$, and $\sigma$ is the standard deviation of the variable $X$. If both values are known, we can provide them explicitly. The most common situation is the case when both are unknown and to be estimated from the sample. Thus, equation (19.1) takes the form

```
z = \frac{X - \hat{\mu}}{\hat{\sigma}} (19.2)
```

with $\hat{x}$ being the sample, or the estimated, versions of variable $x$.
The q of the in-sample z-score normalization is given as:

```
.quantQ.preml.zScore:[sample]
// sample -- array of values to normalize
:(sample[sample])%dev[sample];
;
```

Let us test the function:

```
testArray.1.0+100?.2.0;
(avg(testArray),sdev[testArray])
```

1.938569 0.569563

The normalized array is then obtained as

```
testArrayNorm:quantQ.preml.zScoreNorm[testArray]
(avg(testArrayNorm),sdev[testArrayNorm])
```

1.55983e-016 1

The static version of the normalisation is implemented as

```
.quantQ.preml.zScoreNormExt:[sample;params]
// sample -- array of values to normalize
// params -- dictionary with `mean` and `std`
:(sample params[`mean`)%params[`std`]);
;
```