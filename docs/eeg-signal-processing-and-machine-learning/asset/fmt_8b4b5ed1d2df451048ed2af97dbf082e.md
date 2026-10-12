
### 8.9.1 Diffusion Kalman Filtering

(8.41)
```
E[[[w_i; v_{k,i}] [w_i; v_{k,i}]^T]] = [[Q_i δ_ij, 0]; [0, R_{k,i} δ_kl δ_ij]]
```
where `δ[ij]` is the Kronecker delta, `Q[i]` and `R[k,i]` are assumed to be positive definite and bounded.

The diffusion Kalman filtering approach in [[67]](#c08.xhtml#c8-bib-0067), schematically presented as in [Figure 8.4](#c08.xhtml#c8-fig-0004), aims at estimating stable state `x[i]`, while sharing data with its neighbours only. In this algorithm at every time instant `i`, node `k` transmits the quantities `H_{k,i}^T R_{k,i}^{-1} H_{k,i}` and `H_{k,i}^T R_{k,i}^{-1} H_{k,i}` to its neighbours in updating each intermediate estimate `ψ[k, i]`. Information from the neighbouring nodes are combined using a `p × p` diffusion matrix `C[k, l, i]` subject to:

(8.42)
```
∑_{l∈N_{k,i}} C_{k,l,i} = I_p, C_{k,l,i} = 0 for l∉N_{k,i}
```
where `I[p]` is a `p × p` identity matrix. The combination coefficients `C[kl]` combine the information from the neighbouring nodes. Hence, their identification or estimation based on physical or physiological constraints, or an adaptive method such as [[68]](#c08.xhtml#c8-bib-0068), enhances the accuracy of overall diffusion filtering.

![Figure 8.4 Representation of node k and its neighbouring nodes for diffusion Kalman filtering algorithm.](images/c08f004.gif)

[**Figure 8.4**](#c08.xhtml#R_c8-fig-0004) Representation of node `k` and its neighbouring nodes for diffusion Kalman filtering algorithm.

As mentioned earlier connectivity estimation methods such as SEM or MVAR may be used to define the link weights. This is currently under research. CI estimation, conversely, assumes that node `k` is to fuse the estimates `x̂_{l,i|i-1} (l∈N_{k,i})` using its neighbours and through the estimates of their error covariance matrices `P[l, i|i-1] > 0`. Based on the CI algorithm by Julier and Uhlman as reported in [[68]](#c08.xhtml#c8-bib-0068):

(8.43)
```
ψ_{k,i} = C_{k,l,i} x̂_{l,i|i-1}
```
where

(8.44)
```
C_{k,l,i} = β_{k,l,i} Λ_{k,i} P_{l,i|i-1}^{-1} / (Λ_{k,i} = (∑_{l∈N_{k,i}} β_{k,l,i} P_{l,i|i-1}^{-1})^{-1})
```
`0 ≤ β[k, l, i] ≤ 1` where `∑_{l∈N_{k,i}} β_{k,l,i} = 1` is computed such that the trace or determinant of `Λ[k,i]` is minimized. The above optimization is often nonlinear. Therefore, some CI algorithms such as one presented in [[68]](#c08.xhtml#c8-bib-0068) have been proposed to estimate these parameters.

### 8.9.2 Task‐Related Adaptive Connectivity
