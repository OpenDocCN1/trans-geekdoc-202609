# Table 74.3: Estimations of ψ² in international markets.

| Region | Weight on return | Min \hat ψ² | Max \hat ψ² | No. of negative \hat ψ_u² | No. of estimates |
|---|---|---|---|---|---|
| Global | Value-weighted | 0.5154 | 2.1029 | 32 | 271 |
|  | Equal-weighted | 0.7988 | 2.3846 | 0 | 271 |
| Asia (excluding Japan) | Value-weighted | 0.5464 | 2.2252 | 14 | 271 |
|  | Equal-weighted | 0.5351 | 2.7283 | 7 | 271 |
| Japan | Value-weighted | 0.2690 | 1.1737 | 192 | 271 |
|  | Equal-weighted | 0.2805 | 1.2978 | 142 | 271 |
| Europe | Value-weighted | 0.6464 | 3.4789 | 17 | 271 |
|  | Equal-weighted | 0.6021 | 2.8728 | 3 | 271 |
| US | Value-weighted | 0.2943 | 2.1658 | 384 | 1039 |
|  | Equal-weighted | 0.3701 | 3.0002 | 286 | 1039 |

Notes: This table reports the range for \hat ψ² and the number of incidents of negative unbiased estimates \hat ψ_u². We conduct the estimation in different regions based on monthly returns from July 1990 to December 2017 using rolling five-year windows. For the US market, our moving window starts from July 1926. The test portfolios are the 25 size and book-to-market portfolios for each region.

While a value of zero is reasonable for (μ_g^+)^2 / σ_g^2, it is not acceptable for ψ² because ψ is the slope of the asymptote to the minimum variance frontier and should be strictly positive. In this regard, we resort to Bayes method. Assume that ψ is located within the interval [0, Ψ] and the prior distribution is g(ψ), we take the expected value of posterior distribution as our Bayes estimator.

\hat ψ²_Bayes = { E[ ψ | \hat ψ² ] }² = { ∫_a^Ψ ψ f( ψ | \hat ψ² ) dψ }

= { ∫_a^Ψ ψ f( \hat ψ² | ψ ) g(ψ) dψ / ∫_a^Ψ f( \hat ψ² | ψ ) g(ψ) dψ }, (74.12)

where f( \hat ψ² | ψ ) is conditional distribution of \hat ψ² on ψ. f( \hat ψ² | ψ ) has an explicit form because \hat ψ² is non-central F-distributed.