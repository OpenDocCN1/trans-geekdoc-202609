
The top row of [Figure 10.2](#9783110785951_034588.xhtml#b_9783110785968-010_fig_002) shows the effect of a biased measurement, where already a small non-linearity in the response function leads to sizeable distortions. The generic response function `A(x|y) = δ(x − b(y))` preserves normalization, and if the function `b(y)` is strictly monotonic, then every measurement `x` can unambiguously be associated with a true value `y`. For `b'(y) > 0` and for the given example one obtains

(10.8) $g(x) = \frac{f\left( {b^{- 1}(x)} \right)}{b^{\prime}\left( {b^{- 1}(x)} \right)} = \frac{\beta}{\pi\left( {1 + e^{- x\beta}} \right)}\quad\text{~with~}\quad\beta = \frac{\ln\left( {e^{2\pi} - 1} \right)}{\pi},\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\left( 10.8 \right)$

and calculation of the Fisher information per measurement for the expansion coefficients `a[k]` yields

(10.9) $I_{g}\left( a_{k} \right) = {\int d}x\frac{1}{g(x)}\left( \frac{\partial g(x)}{\partial a_{k}} \right)^{2} = {\int_{0}^{\pi}d}z\frac{1}{f(z)}\cos^{2}(kz) = I_{f}\left( a_{k} \right)\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\left( 10.9 \right)$

with `z = b^(−1)(x)`. This result is actually independent of any specific assumption about `f(y)`. Regarding the information content in cases where the only distortion is a bias term one finds

(10.10) `ω[k] = 1 ∀k.` (10.10)

No information is lost for a one-to-one mapping between observation `x` and true value `y`.

### 10.2.2.2 Efficiency

Next we consider the case of no bias and perfect resolution while allowing for efficiency losses. The response function describing the measurement process in this case is `A(x|y) = δ(x − y)ϵ(y)`, where the function `ϵ(y)` is the probability that a true value `y` is actually recorded. Here the normalization is not conserved. Like the true pdf, the observed density is defined over `x ∈ [0, π]` and one has

(10.11) `g(x) = f(x)ϵ(x)` with normalization `G = ∫dx g(x).` (10.11)

The normalization `G` has to be taken into account when calculating the Fisher information of a measurement `x` about a parameter `a[k]`. One finds

(10.12) $I_{g}\left( a_{k} \right) = {\int d}x\frac{1}{g(x)/G}\left( \frac{dg(x)/G}{da_{k}} \right)^{2} = \frac{1}{G}{\int_{0}^{\pi}d}x\frac{\epsilon(x)}{f(x)}\cos^{2}(kx).\,\,\,\,\,\,\,\,\,\,\,\,\,\,\left( 10.12 \right)$

If the efficiency is constant `ϵ(x) = ϵ`, then one has `G = ϵ` and the information per measurement is again `I[f](a[k])`. In this case, each recorded measurement contributes the same information as a measurement for a perfect detector. The efficiency function leads only to an overall reduction of the number of measurements compared with what one ideally would have recorded.

For a non-uniform efficiency function, the information content of a single measurement is affected. This is easily seen for the specific case Equation 10.6. For `k = 0` one has `I[f](a[0]) = I[g](a[0]) = π²`, and for `k > 0` the explicit expressions are

(10.13) $I_{f}\left( a_{k} \right) = \frac{\pi^{2}}{2}\quad\text{~and~}\quad I_{g}\left( a_{k} \right) = \frac{\pi^{2}}{2} - \frac{3}{2k^{2}}.\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\left( 10.13 \right)$

One finds `ω[0] = 1`, and

(10.14) $\omega_{k} = 1 - \frac{3}{k^{2}\pi^{2}}\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\left( 10.14 \right)$

for `k > 0`. There is a small loss of information in the low-order coefficients, but asymptotically each measurement contains as much information as if it had been recorded by an ideal detector. The main loss is due to the average efficiency, which results in an overall reduction in the number of usable data.

### 10.2.2.3 Resolution

The last effect to address is that of finite resolution. Here we will discuss only the special example Equation 10.7 of a uniform true density and a Gaussian response function, which is unbiased and conserves normalization. As before, the information of the true pdf is `I[f](a[0]) = π²` and `I[f](a[k]) = π²/2` for `k > 0`. What remains is to determine the information about the coefficients `a[k]` per actual measurement `x`, which requires the observable density `g(x)` and its derivative with respect to `a[k]`. With `f(y) = 1/π` over `y ∈ [0, π]` one finds

(10.15) $g(x) = \frac{1}{\sqrt{2\pi}\sigma}{\int_{0}^{\pi}d}ye^{- {(x - y)}^{2}/2\sigma^{2}}f(y) = \frac{1}{2\pi}\left( {{erf}\left( \frac{x}{\sqrt{2}\sigma} \right) - {erf}\left( \frac{x - \pi}{\sqrt{2}\sigma} \right)} \right)\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\left( 10.15 \right)$

and

(10.16) $\frac{dg(x)}{da_{k}} = \frac{1}{\sqrt{2\pi}\sigma}{\int_{0}^{\pi}d}ye^{- {(x - y)}^{2}/2\sigma^{2}}\cos(ky).\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\left( 10.16 \right)$

Even for the simple case considered here, there exists no closed-form expression for the information in terms of elementary functions. However, the respective integrals can be calculated numerically, and a qualitative understanding of the case `σ ≪ π` is gained by considering the limiting cases `k → 0` and `k → ∞`.

As shown in the bottom row of [Figure 10.2](#9783110785951_034588.xhtml#b_9783110785968-010_fig_002), the requirement `σ ≪ π` leads to `g(x) ≈ f(x)`, since in the limit `σ → 0` the smearing function `A(x|y)` approached a delta function. Furthermore, for small values of `k` one finds that the derivatives `dg(x)/da[k]` are dominated by contributions from the interior of the interval `[0, π]`, and since that interval is much larger than `σ` one finds

(10.17) $\frac{dg(x)}{da_{k}} \approx \frac{1}{\sqrt{2\pi}\sigma}{\int_{- \infty}^{\infty}d}ye^{- {(x - y)}^{2}/2\sigma^{2}}\cos(ky) = \cos(kx)e^{- \sigma^{2}k^{2}/2},\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\left( 10.17 \right)$

and the result for the leading coefficients becomes

(10.18) $I_{g}\left( a_{k} \right) \approx e^{- k^{2}\sigma^{2}}I_{f}\left( a_{k} \right)\text{~and~thus~}\lim\limits_{k\rightarrow 0}\omega_{k} = e^{- k^{2}\sigma^{2}}.\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\left( 10.18 \right)$

For `k → ∞` a different behaviour is observed. Now the rapid oscillation of the cosine function leads to a negligible contribution from the interior of `[0, π]`, and the derivative `dg(x)/da[k]` as defined in Equation 10.16 is dominated by the contributions from the end points. This follows from the identity

![Fig. 10.3: Illustration of the derivatives dg(x)/dak for k = 0, 8 and 18.](graphic/b_9783110785968-010_fig_003.png)

Fig. 10.3: Illustration of the derivatives `dg(x)/dak` for `k = 0, 8 and 18`.

(10.19) ${\int_{0}^{\pi}d}yf(y)\cos(ky) = {\sum\limits_{m = 1}^{\infty}\frac{{( - 1)}^{m}}{k^{2m}}}\left\lbrack {f^{(2m - 1)}(0) - {( - 1)}^{k}f^{(2m - 1)}(\pi)} \right\rbrack,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\left( 10.19 \right)$

where substituting `f(y) = A(x|y)` and keeping only the leading term `m = 1` yields

(10.20) $\frac{dg(x)}{da_{k}} \approx \frac{1}{k^{2}\sigma^{2}}\frac{1}{\sqrt{2\pi}\sigma}\left( {{( - 1)}^{k}(x - \pi)e^{- {(x - \pi)}^{2}/2\sigma^{2}} - xe^{- x^{2}/2\sigma^{2}}} \right).\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\left( 10.20 \right)$
