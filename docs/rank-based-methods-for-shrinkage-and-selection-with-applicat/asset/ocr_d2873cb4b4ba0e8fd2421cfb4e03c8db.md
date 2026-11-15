Hence,

$$ \text{ADRE}(\hat{\theta}_n^{\text{SSR}}(\lambda) : \hat{\theta}_n^{\text{UR}}) = \left( 1 + \frac{\text{tr}(\mathcal{K}_2)}{\text{tr}(\mathcal{K}_1)} \right) (B(\Delta))^{-1} $$

where

$$ \begin{aligned} B(\Delta) &= 1 + \frac{\text{tr}(\mathcal{K}_2)}{\text{tr}(\mathcal{K}_1)} \left\{ 1 - (p_2 - 2) \left( \mathbb{E} \left[ \mathcal{X}_{p_2+2}^{-2}(\Delta^2) \right] + \Delta^2 \mathbb{E} \left[ \mathcal{X}_{p_2+2}^{-4}(\Delta^2) \right] \right) \right\} \\ &+ (p_2^2 - 4) \frac{\Delta^2 \text{Ch}_{\min}(\mathcal{K}_2)}{\text{tr}(\mathcal{K}_1)} \mathbb{E} \left[ \mathcal{X}_{p_2+4}^{-4}(\Delta^2) \right] \end{aligned} $$

and

$$ \mathbb{E} \left[ \mathcal{X}_{p+2}^{-2}(\Delta^2) \right] = \exp \left\{ - \frac{\Delta^2}{2} \right\} \sum_{r \ge 0} \frac{1}{r!} \left( \frac{\Delta^2}{2} \right)^r \frac{1}{p+2r} = \mathbb{E}_R \left[ \frac{1}{p+2R} \right]. $$

In the above, \(\mathbb{E}_R\) stands for the expectation with respect to a Poisson variable \(R\) with mean \(\frac{\Delta^2}{2}\). We may obtain the following useful identities:

$$ \begin{aligned} \mathbb{E} \left[ \mathcal{X}_{p+2}^{-4}(\Delta^2) \right] &= \exp \left\{ - \frac{\Delta^2}{2} \right\} \sum_{r \ge 0} \frac{1}{r!} \left( \frac{\Delta^2}{2} \right)^r \frac{1}{(p+2r)(p+2r-2)} \\ &= \mathbb{E}_R \left[ \frac{1}{(p+2R)(p+2R-2)} \right], \\ \Delta^2 \mathbb{E} \left[ \mathcal{X}_{p+2}^{-2}(\Delta^2) \right] &= 1 - (p-2) \mathbb{E} \left[ \mathcal{X}_p^{-2}(\Delta^2) \right], \\ \Delta^2 \mathbb{E} \left[ \mathcal{X}_{p+4}^{-4}(\Delta^2) \right] &= \mathbb{E} \left[ \mathcal{X}_{p+2}^{-2}(\Delta^2) \right] - (p-2) \mathbb{E} \left[ \mathcal{X}_{p+2}^{-4}(\Delta^2) \right], \\ 2 \mathbb{E} \left[ \mathcal{X}_p^{-2}(\Delta^2) \right] &= \mathbb{E} \left[ \mathcal{X}_p^{-2}(\Delta^2) \right] - \mathbb{E} \left[ \mathcal{X}_{p+2}^{-2}(\Delta^2) \right]. \end{aligned} $$

We note that the above Stein–Saleh R-estimator depends on \(p_2 - 2 \ge 3\). Saleh (2006) considers the case of \(p_2 - 2 < 3\) in Chapter 2.

# ## 4.7.3 The Positive-rule Stein–Saleh-type R-estimator

The estimator in the previous section may change signs in some cases. As a remedy, we consider the positive-rule Stein–Saleh-type R-estimator which is denoted by \(\hat{\theta}_n^{\text{SSR+}}(\lambda)\) and defined by

$$ \hat{\theta}_n^{\text{SSR+}}(\lambda) = \left( \hat{\theta}_{\text{in}}^{\text{UR}\top}, \hat{\theta}_{2n}^{\text{UR}\top} (1 - \lambda \mathcal{L}_n^{-1}) I(\mathcal{L}_n > \lambda) \right) \quad \text{with} \quad p_2 - 2 \ge 3. $$