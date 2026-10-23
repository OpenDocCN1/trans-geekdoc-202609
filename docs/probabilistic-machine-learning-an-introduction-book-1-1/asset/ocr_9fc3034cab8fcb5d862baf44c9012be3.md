# 7.6.7.1 Bayesian χ²-test for difference in rates

Suppose you are about to buy something from Amazon.com, and there are two sellers offering it for the same price. Seller 1 has 90 positive reviews and 10 negative reviews. Seller 2 has 2 positive reviews and 0 negative reviews. On the face of it, you should pick seller 2, because they have no negative reviews. However, we cannot be very confident that seller 2 is better since they have had so few reviews. In this section, we sketch a Bayesian analysis of this problem.

Since the reviews from the two sellers are for different items, we will use an unpaired test. Let θ₁ and θ₂ be the unknown reliabilities of the two sellers. The likelihood function is yᵢ ~ Bin(Nᵢ, θᵢ), where yᵢ is the number of positive reviews, and Nᵢ is the total number of reviews (so we have y₁ = 90, N₁ = 100, y₂ = 2, N₂ = 2). Since we don’t know anything about these sellers a priori, we’ll use a uniform priors for both unknown parameters, θᵢ ~ Unif(0, 1). This is equivalent to θᵢ ~ Beta(1,1). Therefore the posteriors are p(θ₁|𝒟₁) = Beta(91,11) and p(θ₂|𝒟₂) = Beta(3,1), where 𝒟ᵢ = (yᵢ, Nᵢ) is the observed data.

We want to compute p(θ₁ > θ₂|𝒟). For convenience, let us define δ = θ₁ − θ₂ as the difference in the rates. (Alternatively we might want to work in terms of the log-odds ratio.) We can determine which seller is better by computing

```
p(δ > 0|𝒟) = ∫₀¹ ∫₀¹ 𝕀(θ₁ > θ₂) Beta(θ₁|y₁ + 1, N₁ − y₁ + 1) × Beta(θ₂|y₂ + 1, N₂ − y₂ + 1) dθ₁ dθ₂ (7.216)
```

We can compute this integral numerically, or analytically [Coo05]. An even simpler approach is to approximate the posterior p(δ|𝒟) by Monte Carlo sampling. This is easy, since θ₁ and θ₂ are independent in the posterior, and both have beta distributions, which can be sampled from using standard methods. An MC approximation to p(δ|𝒟), is shown Figure 7.26. We can then approximate p(δ > 0|𝒟) by counting the fraction of samples where θ₁ > θ₂; this turns out to be 0.718, which closely matches the results of numerical integration. This means you are better off buying from seller 1, even though they have more negative reviews.

We call this method a Bayesian χ²-test, because it is similar in spirit to the frequentist test discussed in Sec. E.7.4.

# 7.6.7.2 Bayesian t-test for difference in means

Let us revisit the example from Sec. 7.6.7.1, but suppose our goal is now to decide which seller is cheaper on average, based on the set of prices they list for a set of shared items. Let yᵢʲ be the cost of item i from seller j. Since the items are comparable across groups, we can use a paired test. Let xᵢ = yᵢ¹ − yᵢ². It is often reasonable to assume that xᵢ ~ 𝒩(δ, σ²), where δ is the unknown effect size. We are interested in p(δ|x), where x = (x₁, …, x_N).

We will use the uninformative Jeffreys prior for the unknown parameters (δ, σ) given in Eq. (7.154). The posterior marginal for the mean is given by Eq. (7.97), which we repeat here for convenience:

```
p(δ|x) = 𝒯(δ| x̄, s²/N, N − 1) (7.217)
```