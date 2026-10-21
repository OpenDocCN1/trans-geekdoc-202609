= r X · e^{-rτ} (1 - N(d2)) - S_t \frac{1}{\sqrt{2\pi}} e^{-\frac{d_1^2}{2}} \cdot \left( \frac{\frac{\sigma_s^2}{2}}{\sigma_s \sqrt{\tau}} \right)

= r X · e^{-rτ} (1 - N(d2)) - \frac{S_t \sigma_s}{2 \sqrt{\tau}} \cdot N'(d1)

= r X · e^{-rτ} N(-d2) - \frac{S_t \sigma_s}{2 \sqrt{\tau}} \cdot N'(d1).

For a European call option on a dividend-paying stock, theta can be shown as

Θ = q · S_t e^{-qτ} N(d1) - \frac{S_t e^{-qτ} σ_s}{2 \sqrt{τ}} · N'(d1) - r X · e^{-rτ} N(d2).  (86.15)

The derivation of (86.15) is

Θ = - \frac{∂C_t}{∂τ} = q · S_t e^{-qτ} N(d1) - S_t e^{-qτ} \frac{∂N(d1)}{∂τ} + (-r) · X · e^{-rτ} N(d2) + X e^{-rτ} \frac{∂N(d2)}{∂τ}
= q · S_t e^{-qτ} N(d1) - S_t e^{-qτ} \frac{∂N(d1)}{∂d1} \frac{∂d1}{∂τ} - r X · e^{-rτ} N(d2) + X e^{-rτ} \frac{∂N(d2)}{∂d2} \frac{∂d2}{∂τ}
= q · S_t e^{-qτ} N(d1) - S_t e^{-qτ} \frac{1}{\sqrt{2π}} e^{-\frac{d_1^2}{2}} \left( \frac{r - q + \frac{σ_s^2}{2}}{σ_s \sqrt{τ}} - \frac{\ln(\frac{S_t}{X})}{2 σ_s τ^{3/2}} - \frac{r - q + \frac{σ_s^2}{2}}{2 σ_s \sqrt{τ}} \right) - r X · e^{-rτ} N(d2) + X e^{-rτ} · \left( \frac{1}{\sqrt{2π}} e^{-\frac{d_2^2}{2}} · \frac{S_t}{X} · e^{(r - q)τ} \right) · \left( \frac{r - q}{σ_s \sqrt{τ}} - \frac{\ln(\frac{S_t}{X})}{2 σ_s τ^{3/2}} - \frac{r - q + \frac{σ_s^2}{2}}{2 σ_s \sqrt{τ}} \right)
= q · S_t e^{-qτ} N(d1) - S_t e^{-qτ} \frac{1}{\sqrt{2π}} e^{-\frac{d_1^2}{2}} \left( \frac{r + \frac{σ_s^2}{2}}{σ_s \sqrt{τ}} - \frac{\ln(\frac{S_t}{X})}{2 σ_s τ^{3/2}} - \frac{r + \frac{σ_s^2}{2}}{2 σ_s \sqrt{τ}} \right) - r X · e^{-rτ} N(d2)