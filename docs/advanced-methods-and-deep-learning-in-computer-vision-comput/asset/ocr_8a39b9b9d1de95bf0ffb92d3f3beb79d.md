One approach that avoids this brute-force online fine-tuning is based on a generative appearance model (AGAME) (Johnander et al., 2019). This approach estimates instead the parameters of a Gaussian mixture model (GMM) and draws deep features from

```
p(x) = sum_{k=1}^{K} p(z = k) p(x | z = k),  (9.62)
```

where p(x | z = k) = N(x | μ_k, Σ_k). A uniform prior 1/K over components k is assumed and the components are either from the background or the foreground. Each of these two classes is divided into a main mode and a mode of hard cases, i.e., we obtain four components in total.

The GMM parameters θ, i.e., means μ_k and variances Σ_k, are initialized from the initial frame. During the bootstrapping, i.e., the subsequent frames I^i, when only estimates of the class memberships are available, soft-assignments for the background, object, and the respective hard cases,

```
α0^i = 1 - ŷ(I^i, θ^{i-1}, Φ)  (9.63)
α1^i = ŷ(I^i, θ^{i-1}, Φ)  (9.64)
α2^i = max(0, α0^i - p(z^i = 0 | x^i, μ0^i, Σ0^i))  (9.65)
α3^i = max(0, α1^i - p(z^i = 1 | x^i, μ1^i, Σ1^i)),  (9.66)
```

are used for the updates. Here, Φ denotes the parameters of the fusion and prediction networks.

The coarse predictions ŷ are computed fusing the mask propagation output and the component score (log-probabilities ln p(z = k) p(x | z = k))

```
s_k^i = - [ ln |Σ_k^{i-1}| + (x^i - μ_k^{i-1})^T (Σ_k^{i-1})^{-1} (x^i - μ_k^{i-1}) ] / 2 ,  (9.67)
```

resulting in the assignments for components 0 and 1. The likelihoods in the cases 2 and 3 are computed using the soft-max of the respective scores. The four soft-assignments are used to compute mean- and variance-updates as weighted first and second moments. The updates are then fed into a moving average similar to (9.9).

During inference, the predictions are refined by an upsampling module to achieve full resolution. The level of performance of the AGAME algorithm renders it useful for the semi-automatic annotation in the RGBT challenge of VOT2019 after additional consistency checks (Berg et al., 2019).

# 9.5.3 A discriminative VOS method

The likelihoods in cases 2 and 3 in the previous section “provide a discriminative mask encoding” (Johnander et al., 2019), which immediately leads to the question whether one can replace the GMM with a discriminative model, a dedicated target model similar to the one in the ATOM-tracker. Similar to the GMM in AGAME, this target model is supposed to adapt to