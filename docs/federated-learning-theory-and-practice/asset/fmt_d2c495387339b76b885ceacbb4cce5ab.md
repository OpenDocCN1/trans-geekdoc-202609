
Compared to `(*ϵ*, 0)`\-DP, the relaxation by `*δ*` allows an improved and asymptotically tight analysis of the cumulative privacy loss incurred by composition of multiple differentially private mechanisms; [[18]](#Chp002_29-55_B9780443190377000090_split_001.xhtml#br0090) states an advanced composition theorem (a factor of one-half improvement over [[19]](#Chp002_29-55_B9780443190377000090_split_001.xhtml#br0095)): For all `*ϵ*, *δ*, *δ*^′ ≥ 0`, the class of `(*ϵ*, *δ*^′)`\-DP mechanisms satisfies

```
(\sqrt{2k\ln(1/\delta)} \cdot \epsilon + k\epsilon(e^{\epsilon} - 1)/2,k\delta^{\prime} + \delta)\text{-DP}
```

under `*k*`\-fold adaptive composition. This means that only for `*k* ≤ (1 − *δ*)/*δ*^′` the privacy failure probability remains bounded to something smaller than 1.

For group privacy, the literature shows `(*g**ϵ*, *g**e*^(*g* − 1)*δ*)`\-DP for groups of size `*g*`. Here, we see an exponential dependency in `*g*` due to the `*g**e*^(*g* − 1)` term in the privacy failure probability. This means that only for very small `*δ*`, the failure probability remains bounded to something smaller than 1.

We conclude that `*k*`\-fold composition and group privacy for group size `*g*` only lead to useful bounds for relatively small `*k*` and `*g*`. If we restrict ourselves to a subclass of mechanisms, then we may be able to prove practical DP bounds for composition and group privacy for much larger and practical `*k*` and `*g*`. We will define such subclasses by imposing properties on the privacy loss.

### 2.3.3 Divergence-based DP measures

In order to get better trade-offs for composition and group privacy, we want to weigh the tail distribution of unlikely observations in such a way that more unlikely observations are allowed to leak even more privacy. So, rather than weighing all unlikely observations equally likely, which results in the privacy failure probability `*δ*`, we want to be more careful. This will allow improved DP bounds for composition and group privacy.

The first idea is to treat the loss function [(2.5)](#Chp002_29-55_B9780443190377000090_split_000.xhtml#deq17) as a random variable `*Z*` and note that in a `*k*`\-fold composition we observe `*k*` drawings of random variable `*Z*`. Due to the law of large numbers, the average of these drawings will be concentrated around the mean of the loss function. This leads to the notion of Concentrated Differential Privacy (CDP), first introduced in [[18]](#Chp002_29-55_B9780443190377000090_split_001.xhtml#br0090) by framing the loss function as a sub-Gaussian random variable after subtracting its mean. This was re-interpreted and relaxed by using Renyi entropy in [[5]](#Chp002_29-55_B9780443190377000090_split_001.xhtml#br0025) and its authors followed up with the notion zero-CDP (zCDP) in [[5]](#Chp002_29-55_B9780443190377000090_split_001.xhtml#br0025): A mechanism `ℳ` is `*ρ*`\-zCDP if, for all `*α* > 1`, the Renyi divergence

```
\mathtt{D}_{\alpha}(\mathcal{M}(d)\|\mathcal{M}(d^{\prime})) = \frac{\ln(\mathbb{E}_{o \sim \mathcal{M}(d)}[ e^{(1 - \alpha)Z}])}{1 - \alpha}\text{~with~}Z = L_{\mathcal{M}(d)\|\mathcal{M}(d^{\prime})}^{o}
```

satisfies

`D`[*α*](`ℳ`(*d*)∥`ℳ`(*d*^′)) ≤ `*ρ**α*`.

(2.6)

This DP guarantee requires the tail of `*Z*` to be sub-Gaussian, i.e., `Pr` [`*Z*` > `*t*` + `*ρ*`\] < `*e*^( − *t*²/(4*ρ*))` for all `*t*` ≥ 0 (the tail behaves like `*Z*` ∼ 𝒩(`*ρ*`, 2`*ρ*))). If the loss function satisfies this property for a collection of `*k*` mechanisms (each of the mechanisms is `*ρ*`\-zCDP), then their `*k*`\-fold adaptive composition is `*kρ*`\-zCDP. If a mechanism is `*ρ*`\-zCDP for individual privacy, then it is `*g*²*ρ*`\-zCDP for groups of size `*g*`. This shows that if we can prove that our DP principles lead to a sub-Gaussian tail of the loss function `*Z*`, then we obtain interpretable DP guarantees even for large `*k*` and `*g*`.

After the introduction of `*ρ*`\-zCDP, Renyi DP (RDP) was introduced by [[41]](#Chp002_29-55_B9780443190377000090_split_001.xhtml#br0205); `(*ω*, *τ*)`\-RDP requires

`D`[*α*](`ℳ`(*d*)∥`ℳ`(*d*^′)) ≤ `*τ*` for all `*α*` ∈ (1, `*ω*`).

Here, `*α*` = 1 bounds the geometric mean of `*e*^(*Z*)`, `*α*` = 2 bounds the arithmetic mean of `*e*^(*Z*)`, `*α*` = 3 bounds the quadratic mean of `*e*^(*Z*)`, etc., and `*α*` = ∞ bounds the maximum value of `*e*^(*Z*)` which is equivalent to `(*τ*, 0)`\-DP. RDP also leads to simple computable composition and group privacy. The advantage of zCDP over RDP is that it covers all `*α*` at once: Larger `*α*` put more weight on the tail of `*Z*`, also the mean gets larger. This means that `*τ*` in the RDP definition should increase with `*α*` and this is realized by zCDP by setting `*τ*` = `*ρ**α*` for all `*α*` ∈ (1, ∞).

The above discussion leads naturally to the definition of `(*ρ*, *ω*)`\-tCDP [[4]](#Chp002_29-55_B9780443190377000090_split_001.xhtml#br0020): A mechanism is `*ω*`\-truncated `*ρ*`\-CDP if it satisfies [(2.6)](#Chp002_29-55_B9780443190377000090_split_001.xhtml#deq20) only for `*α*` ∈ (1, `*ω*`). tCDP requires `*Z*` to be sub-Gaussian near the origin (like zCDP), i.e., `Pr` [`*Z*` > `*t*` + `*ρ*`\] < `*e*^( − *t*²/(4*ρ*))` for all 0 ≤ `*t*` ≤ 2`*ρ*`(`*ω*` − 1), but only subexponential in `*Z*`'s tail, i.e., we get the weaker subexponential tail bound `Pr` [`*Z*` > `*t*` + `*ρ*`\] ≤ `*e*^((*ω* − 1)²*ρ`)`*e*^( − (*ω* − 1)*t`)`. This relaxes zCDP while still obtaining interpretable DP guarantees for composition and group privacy, and also subsampling.
