![](bbox=[0.38, 0.1, 0.7, 0.28])

Figure 9.3: Geometry of LDA in the 2 class case where Σ₁ = Σ₂ = I.

# 9.2.2 Linear decision boundaries

Now we consider a special case of Gaussian discriminant analysis in which the covariance matrices are tied or shared across classes, so Σ_c = Σ. If Σ is independent of c, we can simplify Eq. (9.4) as follows:

log p(y = c|x, θ) = log π_c − 1/2 (x − μ_c)ᵀ Σ⁻¹ (x − μ_c)   (9.5)
= log π_c − 1/2 μ_cᵀ Σ⁻¹ μ_c + xᵀ Σ⁻¹ μ_c − 1/2 xᵀ Σ⁻¹ x   (9.6)
= γ_c + xᵀ β_c + κ   (9.7)

The final term is independent of c, and hence is an irrelevant additive constant that can be dropped. Hence we see that the discriminant function is a linear function of x, so the decision boundaries will be linear. Hence this method is called linear discriminant analysis or LDA. See Fig. 9.2b for an example.

# 9.2.3 The connection between LDA and logistic regression

In this section, we derive an interesting connection between LDA and logistic regression, which we introduced in Sec. 3.2.3. From Eq. (9.7) we can write

p(y = c|x, θ) = e^{β_cᵀ x + γ_c} / Σ_{c'} e^{β_{c'}ᵀ x + γ_{c'}} = e^{w_cᵀ [1, x]} / Σ_{c'} e^{w_{c'}ᵀ [1, x]}   (9.8)

where w_c = [γ_c, β_c]. We see that Eq. (9.8) has the same form as the multinomial logistic regression model. The key difference is that in LDA, is that we first fit the Gaussians (and class prior) to maximize the joint likelihood p(x, y|θ), as discussed in Sec. 9.2.4, and then we derive w from θ. By contrast, in logistic regression, we estimate w directly to maximize the conditional likelihood p(y|x, w). In general, these can give different results (see Exercise 10.3). To gain further insight into Eq. (9.8), let us consider the binary case. In this case, the posterior is