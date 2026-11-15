
Hence,

\(\text{ADRE}(\hat{\theta}_n^{\text{PTR}}(\lambda) : \hat{\theta}_n^{\text{UR}}) = \left(1 + \frac{\text{tr}(\mathcal{K}_2)}{\text{tr}(\mathcal{K}_1)}\right)(A(\lambda, \Delta))^{-1} \quad (4.7.1)\)

where

\(A(\lambda, \Delta) = 1 + \frac{\text{tr}(\mathcal{K}_2)}{\text{tr}(\mathcal{K}_1)} \left\{ 1 - \mathcal{H}_{p_2+2}(\chi_{p_2}^2(\lambda^2), \Delta^2) \right\}\)
\(+ \frac{\Delta^2 \text{Ch}_{\min}(\mathcal{K}_2)}{\text{tr}(\mathcal{K}_1)} \left( 2\mathcal{H}_{p_2+2}(\chi_{p_2}^2(\lambda^2), \Delta^2) - \mathcal{H}_{p_2+4}(\chi_{p_2}^2(\lambda^2), \Delta^2) \right) . \quad (4.7.2)\)

## 4.7.2 The Stein-Saleh-type R-estimator

Note that \(\hat{\theta}_n^{\text{PTR}}(\lambda)\) is a discrete function and some desirable properties of the estimator may lost in the process. Hence, we consider the continuous version of \(\hat{\theta}_n^{\text{PTR}}(\lambda)\) to be called the Stein-Saleh-type R-estimator and defined by

\(\hat{\theta}_n^{\text{SSR}}(\lambda) = \left( \hat{\theta}_{1n}^{\text{UR}\top}, \hat{\theta}_{2n}^{\text{UR}\top}(1 - \lambda \mathcal{L}_n^{-1}) \right)^\top \text{ with } p_2 - 2 \ge 3. \quad (4.7.3)\)

**Theorem 4.4** Under the local alternatives, \(K_{(n)}\), the asymptotic distributional bias, and \(\text{ADL}_2\)-risk of the Stein-Saleh-type R-estimator, \(\hat{\theta}_n^{\text{SSR}}(\lambda)\), are respectively given by

\(\text{ADB}(\hat{\theta}_n^{\text{SSR}}(\lambda)) = \left( \mathbf{0}_{p_1}^\top, -\hat{\theta}_2^\top(p_2 - 2)\mathbb{E}\left[ \chi_{p_2+2}^{-2}(\Delta^2) \right] \right)^\top\)

and

\(\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{SSR}}(\lambda)) = \eta^2 \left\{ (\text{tr}(\mathcal{K}_1) + \text{tr}(\mathcal{K}_2)) - \lambda \text{tr}(\mathcal{K}_2) \left( \mathbb{E}\left[ \chi_{p_2+2}^{-2}(\Delta^2) \right] \right.\right.\)
\(\left.\left. + \Delta^2 \mathbb{E}\left[ \chi_{p_2+4}^{-2}(\Delta^2) \right] \right) + \lambda(\lambda + 4) \delta_2^\top \delta_2 \mathbb{E}\left[ \chi_{p_2+4}^{-4}(\Delta^2) \right] \right\}.\)

The lower bound of \(\text{ADL}_2\)-risk is given by

\(\text{ADL}_2^*\text{-risk}(\hat{\theta}_n^{\text{SSR}}(\lambda)) = \eta^2 \left[ \text{tr}(\mathcal{K}_1) + \text{tr}(\mathcal{K}_2) - (p_2 - 2)\text{tr}(\mathcal{K}_2) \right.\)
\(\left. \times \left( \mathbb{E}\left[ \chi_{p_2+2}^{-2}(\Delta^2) \right] + \Delta^2 \mathbb{E}\left[ \chi_{p_2+4}^{-2}(\Delta^2) \right] \right) + (p_2^2 - 4)\Delta^2 \text{Ch}_{\min}(\mathcal{K}_2) \mathbb{E}\left[ \chi_{p_2+4}^{-4}(\Delta^2) \right] \right].\)

Hence,

$$ \text{ADRE}(\hat{\theta}_n^{\text{SSR}}(\lambda) : \hat{\theta}_n^{\text{UR}}) = \left( 1 + \frac{\text{tr}(\mathcal{K}_2)}{\text{tr}(\mathcal{K}_1)} \right) (B(\Delta))^{-1} $$

where

$$ \begin{aligned} B(\Delta) &= 1 + \frac{\text{tr}(\mathcal{K}_2)}{\text{tr}(\mathcal{K}_1)} \left\{ 1 - (p_2 - 2) \left( \mathbb{E} \left[ \chi_{p_2+2}^{-2}(\Delta^2) \right] + \Delta^2 \mathbb{E} \left[ \chi_{p_2+2}^{-4}(\Delta^2) \right] \right) \right\} \\ &+ (p_2^2 - 4) \frac{\Delta^2 \text{Ch}_{\min}(\mathcal{K}_2)}{\text{tr}(\mathcal{K}_1)} \mathbb{E} \left[ \chi_{p_2+4}^{-4}(\Delta^2) \right] \end{aligned} $$

and

$$ \mathbb{E} \left[ \chi_{p+2}^{-2}(\Delta^2) \right] = \exp \left\{ - \frac{\Delta^2}{2} \right\} \sum_{r \ge 0} \frac{1}{r!} \left( \frac{\Delta^2}{2} \right)^r \frac{1}{p+2r} = \mathbb{E}_R \left[ \frac{1}{p+2R} \right]. $$

In the above, \(\mathbb{E}_R\) stands for the expectation with respect to a Poisson variable \(R\) with mean \(\frac{\Delta^2}{2}\). We may obtain the following useful identities:

$$ \begin{aligned} \mathbb{E} \left[ \chi_{p+2}^{-4}(\Delta^2) \right] &= \exp \left\{ - \frac{\Delta^2}{2} \right\} \sum_{r \ge 0} \frac{1}{r!} \left( \frac{\Delta^2}{2} \right)^r \frac{1}{(p+2r)(p+2r-2)} \\ &= \mathbb{E}_R \left[ \frac{1}{(p+2R)(p+2R-2)} \right], \\ \Delta^2 \mathbb{E} \left[ \chi_{p+2}^{-2}(\Delta^2) \right] &= 1 - (p-2) \mathbb{E} \left[ \chi_p^{-2}(\Delta^2) \right], \\ \Delta^2 \mathbb{E} \left[ \chi_{p+4}^{-4}(\Delta^2) \right] &= \mathbb{E} \left[ \chi_{p+2}^{-2}(\Delta^2) \right] - (p-2) \mathbb{E} \left[ \chi_{p+2}^{-4}(\Delta^2) \right], \\ 2 \mathbb{E} \left[ \chi_p^{-2}(\Delta^2) \right] &= \mathbb{E} \left[ \chi_p^{-2}(\Delta^2) \right] - \mathbb{E} \left[ \chi_{p+2}^{-2}(\Delta^2) \right]. \end{aligned} $$

We note that the above Stein–Saleh R-estimator depends on \(p_2 - 2 \ge 3\). Saleh (2006) considers the case of \(p_2 - 2 < 3\) in Chapter 2.

## 4.7.3 The Positive-rule Stein–Saleh-type R-estimator

The estimator in the previous section may change signs in some cases. As a remedy, we consider the positive-rule Stein–Saleh-type R-estimator which is denoted by \(\hat{\theta}_n^{\text{SSR+}}(\lambda)\) and defined by

$$ \hat{\theta}_n^{\text{SSR+}}(\lambda) = \left( \hat{\theta}_{1n}^{\text{UR}\top}, \hat{\theta}_{2n}^{\text{UR}\top} (1 - \lambda \mathcal{L}_n^{-1}) I(\mathcal{L}_n > \lambda) \right) \quad \text{with} \quad p_2 - 2 \ge 3. $$

**Theorem 4.5** Under the local alternatives, \(K_{(n)}\), the asymptotic distributional bias, and \(\text{ADL}_2\)-risk of the positive-rule Stein–Saleh-type R-estimator, \(\hat{\theta}_n^{\text{SSR+}}(\lambda)\), are respectively given by

\(\text{ADB}(\hat{\theta}_n^{\text{SSR+}}(\lambda)) = \begin{pmatrix} \mathbf{0}_{p_1} \\ -\delta_2^\top \mathbb{E} \left[ (1-(p_2-2)\chi_{p_2+2}^{-2}(\Delta^2))I(\chi_{p_2+2}^2(\Delta^2) < p_2-2) \right] \end{pmatrix}\)

and

\(\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{SSR+}}(\lambda)) = \text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{SSR}}(\lambda)) - \eta^2 \text{tr}(\mathcal{K}_2) \mathbb{E} \left[ \left( 1-(p_2-2)\chi_{p_2+2}^{-2}(\Delta^2) \right)^2 I(\chi_{p_2+2}^2(\Delta^2) < p_2-2) \right] + \delta_2^\top \delta_2 \left\{ 2 \mathbb{E} \left[ (1-(p_2-2)\chi_{p_2+2}^{-2}(\Delta^2)) I(\chi_{p_2+2}^2(\Delta^2) < p_2-2) \right] - \mathbb{E} \left[ \left( 1-(p_2-2)\chi_{p_2+4}^{-2}(\Delta^2) \right)^2 I(\chi_{p_2+4}^2(\Delta^2) < p_2-2) \right] \right\}.\)

The lower bound of \(\text{ADL}_2\)-risk is given by

\(\text{ADL}_2^*\text{-risk}(\hat{\theta}_n^{\text{SSR+}}(\lambda)) = \text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{SSR}}(\lambda)) - \frac{\eta^2}{p_2-2} \text{tr}(\mathcal{K}_2^{-1}) \mathbb{E} \left[ \left( 1-(p_2-2)\chi_{p_2+2}^{-2}(\Delta^2) \right)^2 I(\chi_{p_2+2}^2(\Delta^2) < p_2-2) \right] + \Delta^2 \text{Ch}_{\min}(\mathcal{K}_2) \left\{ 2 \mathbb{E} \left[ (1-(p_2-2)\chi_{p_2+2}^{-2}(\Delta^2)) I(\chi_{p_2+2}^2(\Delta^2) < p_2-2) \right] - \mathbb{E} \left[ \left( 1-(p_2-2)\chi_{p_2+4}^{-2}(\Delta^2) \right)^2 I(\chi_{p_2+4}^2(\Delta^2) < p_2-2) \right] \right\}.\)

Hence,

\(\text{ADRE}(\hat{\theta}_n^{\text{SSR+}}(\lambda) : \hat{\theta}_n^{\text{UR}}) = \left( 1 + \frac{\text{tr}(\mathcal{K}_2)}{\text{tr}(\mathcal{K}_1)} \right) (C(\Delta))^{-1}\)

where

\(C(\Delta) = \frac{\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{SSR}})}{\eta^2 \text{tr}(\mathcal{K}_1)} - \frac{\text{tr}(\mathcal{K}_2)}{\text{tr}(\mathcal{K}_1)} \mathbb{E} \left[ \left( 1-(p_2-2)\chi_{p_2+2}^{-2}(\Delta^2) \right)^2 I(\chi_{p_2+2}^2(\Delta^2) < (p_2-2)) \right] + \frac{\Delta^2 \text{Ch}_{\min}(\mathcal{K}_2)}{\text{tr}(\mathcal{K}_1)} \left\{ 2 \mathbb{E} \left[ (1-(p_2-2)\chi_{p_2+2}^{-2}(\Delta^2)) I(\chi_{p_2+2}^2(\Delta^2) < (p_2-2)) \right] - \mathbb{E} \left[ \left( 1-(p_2-2)\chi_{p_2+4}^{-2}(\Delta^2) \right)^2 I(\chi_{p_2+4}^2(\Delta^2) < (p_2-2)) \right] \right\}.\)

\(\mathbb{E}\left[\chi_{p+2}^{-2}(\Delta^2)I(\chi_{p+2}^2(\Delta^2)<c)\right] = \mathbb{E}_R\left[\frac{\mathcal{H}_{p+2R}(c;0)}{(p+2R)}\right],\)

and

\(\mathbb{E}\left[\chi_{p+2}^{-4}(\Delta^2)I(\chi_{p+2}^2(\Delta^2)<c)\right] = \mathbb{E}_R\left[\frac{\mathcal{H}_{p-2+2R}(c;0)}{(p+2R)(p-2+2R)}\right].\)

In the above, \(\mathbb{E}_R\) stands for the expectation with respect to a Poisson variable \(R\) with mean \(\frac{\Delta^2}{2}\).

## 4.7.4 The Ridge-type R-estimator

As we described earlier in Section 4.3, LASSO facilitated the partitioning of the R-estimator of \(\theta\) into two sub-vectors \((\theta_1^\top, \theta_2^\top)^\top\) as follows

\(\hat{\theta}_{1n}^{\text{UR}} = (\hat{\theta}_{n_1}^{\text{UR}}, ..., \hat{\theta}_{n_{p_1}}^{\text{UR}})^\top \text{ and } \hat{\theta}_{2n} = (0, ..., 0)^\top\)

where \(\hat{\theta}_{1n}^{\text{UR}}\) contains \(p_1\) non-zero treatment effects and \(\hat{\theta}_{2n}\) contains \(p_2\) 'zero' treatment effects so that \(p_1+p_2=p\). Hence, in general, we may suspect \(\theta_2\) to be \(\mathbf{0}\). In this case, one may use the R-estimator

\(\hat{\theta}_n^{\text{ridgeR}}(\lambda) = \text{argmin}_{\theta_2 \in \mathbb{R}^2} \left\{ \sum_{l=1}^p \sum_{j=1}^{n_l} |y_{lj} - \theta_l| c_{n_l}^{-}(R_{n_l}^{+}(\theta_l)) + \frac{\lambda}{2} \theta_2^\top \theta_2 \right\}.\)

Thus, we define

\(\hat{\theta}_{n_j}^{\text{ridgeR}}(\lambda) = \hat{\theta}_{n_j}^{\text{UR}} \quad j=1,...,p_1, \text{ and } \hat{\theta}_{n_j}^{\text{ridgeR}}(\lambda) = \frac{\hat{\theta}_{n_j}^{\text{UR}}}{1+\lambda} \quad j=p_1+1,...,p, \quad (4.7.4)\)

to obtain the ridge-type R-estimator

\[
\hat{\theta}_n^{\text{ridgeR}}(\lambda) = \left( \begin{matrix} \hat{\theta}_{n_1}^{\text{UR}} \\ \vdots \\ \hat{\theta}_{n_{p_1}}^{\text{UR}} \\ \dots \\ \frac{1}{1+\lambda} \hat{\theta}_{n_{p_1+1}}^{\text{UR}} \\ \vdots \\ \frac{1}{1+\lambda} \hat{\theta}_{n_p}^{\text{UR}} \end{matrix} \right) = \left( \hat{\theta}_{1n}^{\text{UR}\top}, \frac{1}{1+\lambda} \hat{\theta}_{2n}^{\text{UR}\top} \right)^\top. \quad (4.7.5)
\]
