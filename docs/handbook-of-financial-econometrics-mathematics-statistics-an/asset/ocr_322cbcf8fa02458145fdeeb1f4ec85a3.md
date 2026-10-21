# Application of Structural Equation Modeling in Behavioral Finance

where x is a q × 1 vector of exogenous observed variables, and q is the number of x associated with ξ. ξ denotes a n × 1 vector of exogenous latent variables, and n denotes the number of ξ. Λx is a q × n matrix of coefficients of regression of x on ξ, and δ is a q × 1 vector of measurement errors in x.

```
y = Λ_y η + ε, (16A.2)
```

where y is a p × 1 vector of endogenous observed variables, and p is the number of y associated with η. η denotes a m × 1 vector of endogenous latent variables, and m denotes the number of η. Λy is a p × m matrix of coefficients of regression of y on η, and ε is a p × 1 vector of measurement errors in y.

The structural model is used to examine the path relationship between latent variables, which is specified by equation (16A.3):

```
η = Bη + Γξ + ζ, (16A.3)
```

where B is an m × m matrix of coefficients of the η-variables in the structural relationship, with zeros in the diagonal, and I−B should be non-singular. Γ denotes an m × n matrix of coefficients of the ξ-variables, and ζ denotes an m × 1 vector of equation errors in the structural relationship between η and ξ.

In addition, the random components in structural equation model are presumed to satisfy the following minimal assumptions: δ is uncorrelated with ξ, ε is uncorrelated with η, ζ is uncorrelated with ξ, and ζ, ε, and δ are mutually uncorrelated. Covariance matrices include cov(ξ) = Φ (n × n), cov(ζ) = Φ (m × m) cov(δ) = Θ_δ (q × q), and cov(ε) = Θ_ε (p × p). The covariance matrix of the observations implied by SEM is represented as follows:

```
Σ = Cov(y) = (
  Λ_y A (Γ Φ Γ' + Ψ) A' Λ_y' + Θ_ε    Λ_y A Γ Φ Λ_x'
  Λ_x Φ Γ' A' Λ_y'     Λ_x Φ Λ_x' + Θ_δ 
), (16A.4)
where A = (I - B)^{-1}.
```

In this study, the measurement model consists of 21 observed variables: 14 exogenous observed variables (x) and seven endogenous observed variables (y). The structural model consists of five latent variables: three exogenous latent variables (i.e., ξ = MA, RA, and SC) and two endogenous latent variables (i.e., η = DE and PF).