
In traditional linear regression models, the response variable `y` is assumed to be normally distributed, while the functional relationship between the predictors `x1, ..., xp` and `y` is linear. However, many real‐world applications require models to accommodate different types of response variables and nonlinear relationships. Enriching the potential applications of regression analysis, the vast class of `Generalized Linear Models` (GLMs) is prevalent in these scenarios. In these models, the response variables follow a distribution from the so‐called `exponential dispersion family` (EDF), whose mean is connected, via the `link function`, with the `linear predictor` or `systematic component` `η = x̃ᵀβ`, which is a linear combination of the standard versions of the feature (explanatory) variables `x1, ..., xp`.

Let us go into more detail of the GLM. For simplicity, we consider a one‐dimensional setting only. We first briefly introduce some fundamental properties of the EDF. The pdf (or pmf in the discrete case) of a distribution in the EDF takes the following general form:

[(10.8)](#c10.xhtml#R_c10-disp-0023)
```
f(y; θ, φ) = exp((yθ - b(θ)) / φ + S(y, φ)),
```

where `θ` is called the `natural parameter`, and `b(θ) ∈ C²` and `S(y, φ)` are known functions. From ([10.8](#c10.xhtml#c10-disp-0023)), we can see that EDF is a sub‐class of the exponential family where the sufficient statistic of `θ` equals `y` divided by the scale parameter `φ`. Many commonly used distributions in financial and insurance analytics belong to the EDF, including but not limited to the normal, gamma, Poisson and binomial distributions. From ([10.8](#c10.xhtml#c10-disp-0023)), we can readily derive the mgf of `y`:
