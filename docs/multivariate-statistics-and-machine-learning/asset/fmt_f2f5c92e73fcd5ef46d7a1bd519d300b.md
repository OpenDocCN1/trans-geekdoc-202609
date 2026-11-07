
We note in [Figure 7.5](#c7.xhtml#f7.5) that as the bins get progressively narrower, we eventually “zero in” on the actual data points that make up the theoretical regression line as well as the actual points that happen to fall on the sample regression line. Hence, in this extreme version of nonparametric regression where each data point is a mean, we are simply *connecting the means* located within the bins. Clearly, such an approach would usually not be useful, and we are better off increasing the size of each bin. However, if we increase the bin size too much, we miss out on the *locality* of the data we initially were after; *this is the nature of the trade-off*.

What makes this approach *nonparametric* is that no assumptions about the population or form of the relationship are made. Sample size plays a crucial role here as well. As the sample size increases, the intervals become successively narrower, each containing more data, where in the limit as sample size gets larger, the naïve nonparametric regression coincides with the population regression ([Fox, 2016](#ref.xhtml#re_CIT000106)). What happens with this approach when there are many explanatory variables? Not surprisingly, the previously discussed *curse of dimensionality* rears its ugly head. For simplicity, we focus on the case where we only have a single predictor.

A glaring weakness of this approach is that for a bin of a given size, assuming the bin is larger than each single data point, the estimate within each bin will be inexact for surrounding data points. That is, if the bin size contains 20 data points, the mean computed on these 20 data points will be a rather *coarse* representation of locality. Is there a way we can do better than the mean? Is there a way we can represent the data within each interval more “fairly” or precisely? The answer to this will be yes, via *kernel regression*.

### 7.3.2 Kernel Regression – “Locally Weighted Averaging”

Kernel regression seeks to improve on simple local-averaging by attempting to explicitly give more weight to observations that are close to the focal `x[0]` and less weight to more remote values in the training data ([Fox, 2016](#ref.xhtml#re_CIT000106)). What is a “focal `x[0]`”? This is the hypothetical value from which you wish to make a prediction of the response, `y`. This is an attractive idea, as doing so will provide a better representation of the data *within* each interval or “bin” of data. The distance `x[i]` from `x[0]` can be represented by ([Fox, 2016](#ref.xhtml#re_CIT000106), p. 529):

`z[i] = (x[i]-x[0])/h`

(7.11)

The scale factor here is `h` and is the *bandwidth* of the kernel estimator, controlling its degree of smoothness. As an example, suppose the distance (`x[i]-x[0]`) is equal to 5, with a bandwidth `h` equal to 1, yielding a `z[i]` equal to 5. If we increase the bandwidth to 2, then `z[i]` is equal to 2.5. The function of `h` then is to *scale* the distance (`x[i]-x[0]`). For a constant distance, as `h` grows larger and larger, the interval on the `x`-axis becomes smaller relative to `h` and we obtain a *finer* fit. The 305smoothness of the fitted function is thus largely influenced by the size of the bandwidth, `h`. In general, as `h` increases, the function becomes smoother. Too fine, or too smooth a fit could be detrimental in modeling scientific data, especially if the finer or smoother fit provides too “general” of a modeling approach across the span of the data where perhaps one strategy is more appropriate than another for particular ranges of the data space.

Scaling deviations `x[i] - x[0]` by the bandwidth `h` is fine, but we can do even better and apply a kernel function to the scaled deviation to obtain final weights, `w[i]`:

`w[i] = K[(x[i]-x[0])/h]`

(7.12)

Using the above weights `w[i]`, the fitted value at `x[0]` is computed by weighted local-averaging of the `y[i]` values:

$$\\left. \\hat{f}\\left( x\_{0} \\right) = \\hat{y} \\middle| x\_{0} = \\frac{\\sum\\limits\_{i = 1}^{n}{w\_{i}y\_{i}}}{\\sum\\limits\_{i = 1}^{n}w\_{i}} \\right.$$

(7.13)

We thus see that kernel regression is effectively a form of *weighted regression*, where the weights feature the use of a kernel.

### 7.3.3 A Variety of Kernels

Note that in our description of kernel regression and the computation of weights, `w[i]`, we have not yet described the nature of `K`, that is, the *kernel function* we are choosing to use for the given problem and by which we are applying to `[(x[i]-x[0])/h]`. Not surprisingly, there are many choices for a kernel function. One choice, perhaps the default, is to use the *Gaussian* (or “normal”) kernel:

$$K\\left( z \\right) = \\frac{1}{\\sqrt{2\\pi}}e^{- z^{2}/2}$$

(7.14)

where the bandwidth in (7.14) is the standard deviation. As noted by [Fox (2016](#ref.xhtml#re_CIT000106), p. 530), distances greater than `2*h` from the focal value of `x[0]` receive virtually no weight due to the nature and shape of the normal density.

Following Fox ([2016](#ref.xhtml#re_CIT000106), p. 530), another possibility is to use the *tricube kernel*,

$$K\_{T}\\left( z \\right) = \\left\\{ \\begin{array}{l} \\left. \\left( 1 - \\middle| z \\middle| {}\_{3} \\right)3, \\middle| z \\middle| < \\,\\, 1 \\right. \\\\ \\left. 0, \\middle| z \\middle| \\geq 1 \\right. \\\\ \\end{array} \\right.$$

(7.15)

or the *rectangular kernel*,

$$K\_{R}\\left( z \\right) = \\left\\{ \\begin{array}{l} \\left. 1, \\middle| z \\middle| < 1 \\right. \\\\ \\left. 0, \\middle| z \\middle| \\geq 1 \\right. \\\\ \\end{array} \\right.$$

(7.16)

There are other kernels we can choose from, however according to [Fox (2016)](#ref.xhtml#re_CIT000106), the choice of kernel function is not that critical in carrying out the regression. There is nothing wrong with trying out a variety of kernels to study their impact on the given regression solution.306

### 7.3.4 Kernel Regression Is Not Nonlinear; It Is Nonparametric

We reiterate that kernel regression should not be considered specifically a nonlinear approach to regression in the same vein as polynomial regression (in terms of modeling nonlinear trends, not the model being nonlinear). Rather, it is a *nonparametric approach*, which implies that it *learns from the data*. If that learned form is linear, then so be it, but the point is that kernel regression does not *a priori* assume a linear or nonlinear form. It is first and foremost nonparametric because it essentially makes no parametric assumptions regarding the shape of the true function. *Local-polynomial regression* extends kernel regression where polynomials are instead fit at the focal value of `x[0]`; however this is beyond the scope of this book. For an excellent discussion of kernel regression (and much of anything else to do with regression), see [Fox (2016)](#ref.xhtml#re_CIT000106).

### 7.3.5 Kernel Regression in R

Kernel regression in R can be fit using the package `gplm` ([Mueller, 2016](#ref.xhtml#re_CIT000255)). We adapt an example from the package’s documentation below, where we first create data on 1000 observations for variable `x`:

```
> library(gplm)
> n <- 1000
> x <- rnorm(n)
> head(x)
[1] -0.71040656 0.25688371 -0.24669188 -0.34754260 -0.95161857 -0.04502772
```

We next create `m` as a function of `x` and then `y` as a function of `m`:

```
> m <- sin(x)
> head(m)
[1] -0.65214204 0.25406776 -0.24419733 -0.34058836 -0.81435593 -0.04501251
> y <- m + rnorm(n)
> head(y)
[1] 0.2638500 1.0546901 -1.1807664 -1.7413758 -0.6540784 -0.3189749
> plot(x,y,col=“gray”)
> lines(kreg(x,y),lwd=2)
```

307

The squiggly line ([Figure 7.6](#c7.xhtml#f7.6)) is the kernel regression estimate, using the Nadaraya-Watson estimator (see [Nadaraya, 1964](#ref.xhtml#re_CIT000262)). See the package for many more functions that can be applied to the kernel regression, including extracting estimated fitted values.
