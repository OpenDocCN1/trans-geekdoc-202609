
where, under the assumptions that lead to Eq. [(19.75)](#Chp019_997-1102_B9780443292385000251.xhtml#deq149), `Σ[θ*](x[t], t) = σ[t]²I`. The term `γ > 0` is a user-defined gradient scale factor that can act beneficially to the performance. Note that in the second term on the right hand side in Eq. [(19.82)](#Chp019_997-1102_B9780443292385000251.xhtml#deq160), we can equivalently write

```
γ∇[x[t]]ln p[ϕ*](y|x[t], t) = ∇[x[t]]ln (p[ϕ*](y|x[t], t))^(γ).
```

For `γ > 1`, the distribution `(p[ϕ*](y|x[t], t))^(γ)` becomes sharper than the optimally trained classifier, `p[ϕ*](y|x[t], t)`, since larger values are amplified by the exponent. Hence, using a larger scaling factor, `γ`, the focus turns more on the modes of the classifier, which is potentially desirable for producing higher fidelity, albeit less diverse, samples, [44].

The classifier is trained on samples that result from the same noising distribution as the corresponding diffusion model. After training, the classifier is incorporated into the sampling process of the diffusion model according to Eq. [(19.82)](#Chp019_997-1102_B9780443292385000251.xhtml#deq160).

It is interesting to shed more light into Eq. [(19.82)](#Chp019_997-1102_B9780443292385000251.xhtml#deq160), not for the sake of mathematics but for the sake of understanding the rationale behind the method. The starting point for satisfying the conditional sampling constraint is to express the (true) conditional reverse process as `q(x[t−1]|x[t], y)`. Mobilizing the Bayes theorem and after a bit of algebra (see, [44] for details), it turns out that for the class-conditional reverse transition pdfs, the following holds true:
