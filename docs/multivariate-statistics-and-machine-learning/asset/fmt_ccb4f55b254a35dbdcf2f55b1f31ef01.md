
*Figure 7.4* Imposing the constraint of continuity (right) on the cubic regression spline.[Return to text.⏎](#c7.xhtml#re_f7.4)

This idea of imposing constraints on functions is not at all new. Indeed, virtually every statistical model has constraints either implicitly imposed that we cannot see or that the user imposes manually, such as in structural equation modeling where constraints are regularly imposed. As perhaps the simplest of examples, in linear regression the constraint of *linearity* is imposed, meaning that we will fit a functional form to data *with the constraint that it assumes only a linear form*. While this is an obvious example, it is nonetheless powerful and pedagogical; many researchers perform linear regression analysis without the awareness that they have implicitly constrained their predictive *potential* to that of lines at the expense of other curves such as a higher-order polynomial.302

Constraining a spline regression to have no jumps, or other constraints, gives the model less flexibility as when such parameters need to be estimated, in addition to limiting the type of spline fit so that it is scientifically meaningful to the researcher. Hence, if it is unreasonable to assume a jump can occur in one’s data, then constraining there to be no jumps (or other characteristic of the fitted curve) is perfectly reasonable. On the other hand, if such a jump is a reasonable possibility in the data, then imposing such a constraint would be ill-advised and the data should be modeled in some capacity that incorporates the discontinuity. In this regard, the *science* matters a great deal. If a discontinuity is a reasonable expectation for the given scientific data, it may make little sense to constrain it.

### 7.2.6 Polynomial Regression vs. Regression Splines

In our discussion above, we have presented regression splines as a special case of the more general idea of basis functions, and noted they are more local than methods such as polynomial regression. Which provides the better fit? As argued by [James et al. (2013)](#ref.xhtml#re_CIT000168), regression splines often give superior results. Why? The reason that splines often give better results is that each polynomial regression and splines introduce flexibility in a different manner. *Splines typically do it better*. For polynomial regression, flexibility is introduced by increasing the degree of the function (e.g., from linear to quadratic to cubic and so on). Splines, on the other hand, introduce flexibility by keeping the degree fixed and instead increasing the number of knots, which can range from minimal to maximal. Hence, splines are simply more flexible than fitting a global polynomial, even of increasing degree of complexity, which usually means splines will perform better in cross-validation. What is more, as mentioned, regression splines can serve as a bridge to more generalized modeling such as the generalized linear model ([Fox, 2016](#ref.xhtml#re_CIT000106)).

One-dimensional splines can also be generalized to multidimensional splines though these are beyond the scope of this book. Multidimensional splines are a straight generalization of the one-dimensional spline, however ([Hastie et al., 2009](#ref.xhtml#re_CIT000145)). For an excellent overview of spline options across a variety of R packages, see [Perperoglou et al. (2019)](#ref.xhtml#re_CIT000286). We can also use the `spline2` package ([Wang, 2024](#ref.xhtml#re_CIT000318)) to fit, in addition to natural cubic splines, other splines as well, such as more general `B-splines`, `M-splines`, among others, which we will not detail here (see the package for details). Another popular package for fitting splines in R is that of `gss` ([Gu, 2014](#ref.xhtml#re_CIT000135)). One can also use the `bspline` package ([Sokol, 2024](#ref.xhtml#re_CIT000341)) for estimating spline regression. The `absorber` package ([Savino, 2024](#ref.xhtml#re_CIT000324)) is a variable-selection method using b-splines in multivariate nonparametric regression models that can be useful in choosing the “best” variables in a spline regression problem.303

### 7.3 Nonparametric Regression: Local and Kernel Regression

In our quest to model nonlinearity, we have thus far surveyed two possibilities: polynomial regression and regression splines. Polynomial regression provided a global fit to the data, while splines allowed us to model the data at a more local level. However, both approaches were *parametric* in nature, though splines, depending on the type and how we are using the terms parametric vs. nonparametric, are also often considered nonparametric ([Fox, 2016](#ref.xhtml#re_CIT000106), p. 511).

We now briefly survey two nonparametric approaches: 1) *simple local-averaging*, and 2) *kernel regression*. We will see that kernel regression is a generalization of simple local-averaging and the latter can be used to motivate the former. Kernel regression is our primary focus as a nonparametric technique.

To be more precise, kernel regression is a way to model a *non-hypothesized* form of the relationship, which will typically end up being some undesignated nonlinear form. It can be considered a *nonparametric* approach to regression ([Fox, 2016](#ref.xhtml#re_CIT000106)). The nonparametric feature of kernel regression, as is true of kernel methods in general, allows the data to “speak” and tell us of its shape; we do not in advance assume a hypothetical linear or nonlinear form. That is, if the parametric linear model is

`y = f(x,θ) + ε`

(7.8)

then the nonparametric linear model is

$$\\begin{array}{l} {y = f\\left( x \\right) + \\varepsilon} \\\\ {\\,\\,\\,\\, = f\\left( x\_{1},x\_{2},...,x\_{p} \\right) + \\varepsilon} \\\\ \\end{array}$$

(7.9)

where now there is no parameter vector, `θ` and instead the form of the relation is learned entirely by the data, `x[1]`, `x[2]`, ..., `x[p]`. *Simple local-averaging* on the other hand, is what is generally regarded as a “naïve” approach to regression where averages within predetermined subsets or bins along the `x-axis` are established in order to obtain a more *local flavor* in tracing the response variable. Kernel regression can be interpreted as a more general method of simple local-averaging.

#### 7.3.1 Motivating Kernel Regression via Local-Averaging

In classical least-squares regression, recall that we typically assume that the conditional distribution of `y/x` is Gaussian (i.e., normal). More formally, we model `p(y,x|D)` where `y` is the response, `x` is the predictor, and `D` is the data. That is, in typical classical regression, we are tracing the mean function:

`μ = E(y|x[1],...,x[p]) = α + β[1]x[1] + ... + β[p]x[p]`

(7.10)

Given the assumption that the conditional distribution is normal, consider if we backtracked for a moment and motivated ordinary regression via a naïve approach and dissected the explanatory variable into *bins*, that is, *subsets* of area or *intervals* along the `x-axis`. Not surprisingly, bias is minimized by making the bins as numerous and as narrow as possible ([Fox, 2016](#ref.xhtml#re_CIT000106)). Sampling variance is minimized by using a small number of relatively wide bins, each with many observations. Hence, as usual, there is a trade-off between bias and variance here, encapsulating the classic *bias-variance trade-off*, as illustrated in [Figure 7.5](#c7.xhtml#f7.5).304

![Figure 7.5 Local-averaging in regression. Bias is minimized by making the bins more numerous and narrow; wide bins (left), narrow bins (right).Return to text.⏎](images/fig7.5.jpg)

*Figure 7.5* Local-averaging in regression. Bias is minimized by making the bins more numerous and narrow; wide bins (left), narrow bins (right).[Return to text.⏎](#c7.xhtml#re_f7.5)
