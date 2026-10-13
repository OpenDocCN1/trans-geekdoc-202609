
For the case under study in this section, where `p(y|θ)` and `p(θ)` are both assumed to be Gaussians, `p(y)` can be evaluated analytically; it turns out that the joint distribution `p(y, θ)` is also Gaussian and hence the marginal `p(y)` is Gaussian as well. All these are shown in detail in the appendix of this chapter. Indeed, if we set in Eqs. (12.146) and (12.151) of the appendix `z → θ`, `t → y`, and `A → Φ`, it turns out that for the regression model of Eq. [(12.3)](#Chp012_583-634_B9780443292385000184.xhtml#deq5) and the prior PDF in Eq. [(12.8)](#Chp012_583-634_B9780443292385000184.xhtml#deq11) as well as the noise model of Eq. [(12.2)](#Chp012_583-634_B9780443292385000184.xhtml#deq4), we obtain

```
p(y) = N(y|Φθ[0], Σ[η] + ΦΣ[θ]Φ^(T)).
```

Moreover, the posterior `p(θ|y)` is also Gaussian,

```
p(θ|y) = N(θ|μ[θ|y], Σ[θ|y]),
```

where `μ[θ|y]` is given by Eq. [(12.10)](#Chp012_583-634_B9780443292385000184.xhtml#deq13) and the covariance matrix results from Eq. (12.147), after the appropriate notational substitutions, that is,

```
Σ[θ|y] = (Σ[θ]^(−1) + Φ^(T) Σ[η]^(−1) Φ)^(−1).
```
