
The transformed model output represents a categorical distribution over possible classes `y` ∈ {1, 2, …, `K`}. For a point estimate, we take the most probable category `ŷ` = argmax[k][`Pr`(`y` = `k`|**f**[**x**, ![c5-fig-5004.jpg](images/c5-fig-5004.jpg)])]. This corresponds to whichever curve is highest for that value of **x** in [figure 5.10](#c005.xhtml#c5-fig-0010).

---

Notebook 5.3

Multiclass cross-entropy loss

---

### 5.5.1 Predicting other data types

In this chapter, we have focused on regression and classification because these problems are widespread. However, to make different types of predictions, we simply choose an appropriate distribution over that domain and apply the recipe in section 5.2. [Figure 5.11](#c005.xhtml#c5-fig-0011) enumerates a series of probability distributions and their prediction domains. Some of these are explored in the problems at the end of the chapter.

---

Problems 5.3–5.6

---

![Figure 5.11 Distributions for loss functions for different prediction types.](images/c5-fig-0011.jpg)

[Figure 5.11](#c005.xhtml#c5-fig-0011a) Distributions for loss functions for different prediction types.

## 5.6 Multiple outputs

Often, we wish to make more than one prediction with the same model, so the target output **y** is a vector. For example, we might want to predict a molecule's melting and boiling point (a multivariate regression problem, figure 1.2b) or the object class at every point in an image (a multivariate classification problem, figure 1.4a). While it is possible to define multivariate probability distributions and use a neural network to model their parameters as a function of the input, it is more usual to treat each prediction as *independent*.

Independence implies that we treat the probability `Pr`(**y**|**f**[**x**[i], `ϕ`]) as a product of univariate terms for each element `y[d]` ∈ **y**:

![c5-fig-5026.jpg](images/c5-fig-5026.jpg)

 (5.25)

where **f**[d][**x**[i], `ϕ`] is the `d^(th)` set of network outputs, which describe the parameters of the distribution over `y[d]`. For example, to predict multiple continuous variables `y[d]` ∈ ℝ, we use a normal distribution for each `y[d]`, and the network outputs `f`[d][**x**[i], `ϕ`] predict the means of these distributions. To predict multiple discrete variables `y[d]` ∈ {1, 2, …, `K`}, we use a categorical distribution for each `y[d]`. Here, each set of network outputs **f**[d][**x**[i], `ϕ`] predicts the `K` values that contribute to the categorical distribution for `y[d]`.

---

Appendix C.1.5

Independence

---

When we minimize the negative log probability, this product becomes a sum of terms:

![c5-fig-5027.jpg](images/c5-fig-5027.jpg)

 (5.26)

where `y[id]` is the `d^(th)` output from the `i^(th)` training example.

To make two or more prediction types simultaneously, we similarly assume the errors in each are independent. For example, to predict wind direction and strength, we might choose the von Mises distribution (defined on circular domains) for the direction and the exponential distribution (defined on positive real numbers) for the strength. The independence assumption implies that the joint likelihood of the two predictions is the product of individual likelihoods. These terms will become additive when we compute the negative log-likelihood.

---

Problems 5.7–5.10

---

## 5.7 Cross-entropy loss

In this chapter, we developed loss functions that minimize negative log-likelihood. However, the term *cross-entropy* loss is also commonplace. In this section, we describe the cross-entropy loss and show that it is equivalent to using negative log-likelihood.

The cross-entropy loss is based on the idea of finding parameters `θ` that minimize the distance between the empirical distribution `q`(`y`) of the observed data `y` and a model distribution `Pr`(`y`|`θ`) ([figure 5.12](#c005.xhtml#c5-fig-0012)). The distance between two probability distributions `q`(`z`) and `p`(`z`) can be evaluated using the Kullback-Leibler (KL) divergence:

![c5-fig-5028.jpg](images/c5-fig-5028.jpg)

 (5.27)

---

Appendix C.5.1

KL Divergence

---

![Figure 5.12 Cross-entropy method. a) Empirical distribution of training samples (arrows denote Dirac delta functions). b) Model distribution (a normal distribution with parameters θ = μ, σ2). In the cross-entropy approach, we minimize the distance (KL divergence) between these two distributions as a function of the model parameters θ.](images/c5-fig-0012.jpg)

[Figure 5.12](#c005.xhtml#c5-fig-0012a) Cross-entropy method. a) Empirical distribution of training samples (arrows denote Dirac delta functions). b) Model distribution (a normal distribution with parameters `θ` = `μ, σ`²). In the cross-entropy approach, we minimize the distance (KL divergence) between these two distributions as a function of the model parameters `θ`.

Now consider that we observe an empirical data distribution at points ![c5-fig-5029.jpg](images/c5-fig-5029.jpg). We can describe this as a weighted sum of point masses:

![c5-fig-5030.jpg](images/c5-fig-5030.jpg)

 (5.28)

where `δ`[•] is the Dirac delta function. We want to minimize the KL divergence between the model distribution `Pr`(`y`|`θ`) and this empirical distribution:

![c5-fig-5031.jpg](images/c5-fig-5031.jpg)

 (5.29)

---

Appendix B.1.3

Dirac delta function

---

where the first term disappears, as it has no dependence on `θ`. The remaining second term is known as the *cross-entropy.* It can be interpreted as the amount of uncertainty that remains in one distribution after taking into account what we already know from the other. Now, we substitute in the definition of `q`(`y`) from equation 5.28:

![c5-fig-5032.jpg](images/c5-fig-5032.jpg)

 (5.30)

The product of the two terms in the first line corresponds to pointwise multiplying the point masses in [figure 5.12a](#c005.xhtml#c5-fig-0012) with the logarithm of the distribution in [figure 5.12b](#c005.xhtml#c5-fig-0012). We are left with a finite set of weighted probability masses centered on the data points. In the last line, we have eliminated the constant scaling factor 1/`I`, as this does not affect the position of the minimum.

In machine learning, the distribution parameters `θ` are computed by the model **f**[**x**[i], `ϕ`], so we have:

![c5-fig-5033.jpg](images/c5-fig-5033.jpg)

 (5.31)

This is precisely the negative log-likelihood criterion from the recipe in section 5.2.

It follows that the negative log-likelihood criterion (from maximizing the data likelihood) and the cross-entropy criterion (from minimizing the distance between the model and empirical data distributions) are equivalent.

## 5.8 Summary

We previously considered neural networks as directly predicting outputs **y** from data **x**. In this chapter, we shifted perspective to think about neural networks as computing the parameters `θ` of probability distributions `Pr`(**y**∣`θ`) over the output space. This led to a principled approach to building loss functions. We selected model parameters `ϕ` that maximized the likelihood of the observed data under these distributions. We saw that this is equivalent to minimizing the negative log-likelihood.

The least squares criterion for regression is a natural consequence of this approach; it follows from the assumption that `y` is normally distributed and that we are predicting the mean. We also saw how the regression model could be (i) extended to estimate the uncertainty over the prediction and (ii) extended to make that uncertainty dependent on the input (the heteroscedastic model). We applied the same approach to both binary and multiclass classification and derived loss functions for each. We discussed how to tackle more complex data types and how to deal with multiple outputs. Finally, we argued that cross-entropy is an equivalent way to think about fitting models.
