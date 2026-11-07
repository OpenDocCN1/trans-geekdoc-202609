
Why is Bayes so important? Why do we continuously hear about Bayes in statistics and science? Why are there entire *books* written on Bayesian statistics and Bayesian philosophy? Aside from the fact that Bayes’ theorem has a very long history and is the cornerstone of a branch of statistics appropriately called *Bayesian statistics*, in our current context of classification it is especially important and meaningful because the Bayes’ boundary, or more generally, the Bayes *classifier* has the lowest error rate out of all classifiers ([Cover and Hart, 1967](#ref.xhtml#re_CIT000070); [James et al., 2013](#ref.xhtml#re_CIT000168)), *under the assumption that all terms in Bayes’ theorem can actually be defined and measured*. Under such conditions, as summarized by Cover and Hart ([1967](#ref.xhtml#re_CIT000070), p. 23), “The Bayes risk serves as merely a reference – the limit of excellence beyond which it is not possible to go.”

Long story short, Bayes’ theorem is an optimal sought-after result when it comes to classifying outcomes. It is the theoretical *ideal*. It is what we would wish for all the time if we had the choice. For the 0−1 loss (binary) problem, the Bayes classifier has us classifying to the most probable class using the conditional (discrete) distribution. The error rate generated is called the *Bayes rate* and is the “holy grail” of error rates. Many other methods, both in statistics and machine learning, such as the *k-nearest-neighbor approach*, are meant as direct *approximations* to the Bayesian ideal. They are “second choices” to using a Bayes boundary. *Bayes is always first choice and is always best*. However, nearest-neighbor approaches can have tremendous value in approximating Bayes. Indeed, it has been shown that the nearest-neighbor probability of error, `R`, for a classification problem with `M` categories, is bounded below by the Bayes probability of error, `R′`, and above by `R′(2−M R′/M−1)`. As Cover and Hart have found, “*any* other decision rule based on the infinite data set cut the probability of error by at most one half. In this sense, half of the available information in an infinite collection of classified samples is contained in the nearest neighbor” (p. 27).

## 8.9.2 Why Not Always Bayes?

If Bayes is so wonderful, why not just use it all the time? Ideally, we would use Bayes for virtually all classifier problems. The problem, however, is that the terms needed for Bayes are usually not known. For instance, we do not know the term `f[k](x[i])` in Bayes, and hence, we need a second approach to *estimate* it. The linear discriminant analysis model, and other approaches, are used as *approximations* to the Bayes classifier. However, only when observations are multivariate Gaussian with equal covariance matrix between classes is linear discriminant analysis the estimated Bayes classifier ([Hastie et al., 2009](#ref.xhtml#re_CIT000145)). Hence, our discussion of discriminant analysis should be “housed” in the context of trying to approximate Bayes, but all the while remembering that Bayes is regarded as the optimally desired approach if the terms in Bayes are available. In fictitious toy problems where terms may be available, *all else constant*, one would virtually always choose Bayes over discriminant analysis or any other classifier because it will provide the lowest of error rates. In reality, however, techniques such as discriminant analysis or competitors will usually be employed. Hence, we may say that Bayes is best; however, pragmatic concerns, including variations on sample size availability, will usually suggest a competing methodology such as the linear discriminant analysis model.330

## 8.9.3 Linear Discriminant Analysis Model

We have said that we do not typically know `f[k](x[i])` in the Bayesian formulation. We would like to estimate it. To estimate it, however, we need to make some model assumptions about it. We begin by assuming that `f[k](x[i])` has a normal density. That is, we assume:

$$f\_{k}\\left( x\_{i} \\right) = \\frac{1}{\\sqrt{2\\pi}\\sigma\_{k}}\\exp\\left( {- \\frac{1}{2\\sigma\_{k}^{2}}\\left( x\_{i} - \\mu\_{k} \\right)^{2}} \\right)$$

(8.24)

where the right side of (8.24) is the normal density and `k` is the class or group number. Each class has a mean `μ[k]` and variance `σ[k]²`. In the current setting, there are only two groups on the response variable since it is binary classification, and hence `k = 2`. The density for the first group is thus equal to:

$$f\_{1}\\left( x\_{i} \\right) = \\frac{1}{\\sqrt{2\\pi}\\sigma\_{1}}\\exp\\left( {- \\frac{1}{2\\sigma\_{1}^{2}}\\left( x\_{i} - \\mu\_{1} \\right)^{2}} \\right)$$

and for the second (notice the change in subscripts from 1 to 2),

$$f\_{2}\\left( x\_{i} \\right) = \\frac{1}{\\sqrt{2\\pi}\\sigma\_{2}}\\exp\\left( {- \\frac{1}{2\\sigma\_{2}^{2}}\\left( x\_{i} - \\mu\_{2} \\right)^{2}} \\right)$$

An important assumption made in the classic discriminant analysis model, one which we will relax later when we consider quadratic discriminant analysis, is that the standard deviation or variance is *constant* across both groups or levels on the response variable. That is, we assume

`σ[1]²` =  ⋅  ⋅  ⋅  = `σ[k]²`

(8.25)

We will also assume equality of covariances between responses, which, along with the assumption of equality of variances, yields the *equality of covariance matrices assumption*. This is essentially the same assumption we encountered earlier in our original discussion of MANOVA and discriminant analysis earlier in the book, which as we saw we can evaluate using the *Box M test*.

## 8.9.4 How LDA Approximates Bayes

Here is the trick to understanding how the normal density can be used to approximate Bayes. We desire Bayes in the end, so we substitute in the previous normal densities for the Bayes densities we wish to estimate, those of `f[k](x[i])`, where the numerator is the density for the specific class we are modeling and the denominator is the sum of the classes, mimicking the structure of Bayes,331

$$\\begin{array}{l} {p\\left( y = k \\middle| x = x\_{i} \\right) = \\frac{\\pi\_{k}f\_{k}\\left( x\_{i} \\right)}{\\sum\\limits\_{l = 1}^{K}{\\pi\_{l}f\_{l}\\left( x\_{i} \\right)}}} \\\\ {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, = \\frac{\\pi\_{k}\\frac{1}{\\sqrt{2\\pi}\\sigma\_{k}}\\exp\\left( {- \\frac{1}{2\\sigma\_{k}^{2}}\\left( x\_{i} - \\mu\_{k} \\right)^{2}} \\right)}{{\\sum\\limits\_{l = 1}^{K}\\pi\_{l}}\\frac{1}{\\sqrt{2\\pi}\\sigma\_{}}\\exp\\left( {- \\frac{1}{2\\sigma\_{}^{2}}\\left( x\_{i} - \\mu\_{l} \\right)^{2}} \\right)}} \\\\ \\end{array}$$

(8.26)

where `μ[k]` and `σ[k]²` is the mean and variance for class `k`, the class we are modeling, where again, we assume `σ[k]²` is constant across classes. When we now take the log of equation (8.26), it can be shown that it is equivalent to assigning the observation to the class for which the following gives the largest quantity:

$$\\delta\_{k}\\left( x\_{i} \\right) = x\_{i} \\cdot \\frac{\\mu\_{k}}{\\sigma^{2}} - \\frac{\\mu\_{k}^{2}}{2\\sigma^{2}} + \\log\\left( \\pi\_{k} \\right)$$

(8.27)

But what is (8.27)? What is this function? This function is called the *linear discriminant function*. At a technical level, the linear discriminant function approximates the Bayes classifier by estimating `π[k]`, `μ[k]`, and `σ²`, and substituting these into (8.27). Once we have those values estimated, the approximation to the Bayes classifier is complete.

## 8.9.5 Estimating the Prior Probability and Parameters of the Discriminant Function
