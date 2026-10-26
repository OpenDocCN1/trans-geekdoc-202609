
The second inequality used the fact that all $\tilde{\mathcal{S}}_{m'}$ have identical distributions.

It is also easy to check the following equality by definition:

$\bar{g}_{m',m}(\mathcal{S}_{n+1}) = \bar{g}_{m',m'}(\mathcal{S}_{n+1}) + \frac{1}{m'} \sum_{i=1}^{m'} \big[ \mathbb{E}_{\mathcal{S}_{m'}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i) - \mathbb{E}_{\mathcal{S}_{m}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i) \big] .$

Now using this decomposition, and by applying Jensen’s inequality to the convex function $\ln \mathbb{E}_{\mathcal{S}_{n+1}} \exp(g'(\mathcal{S}_{n+1}))$ with respect to $g'(\cdot)$, we obtain for all $\lambda'$ and $\ell > 1$,

$\ln \mathbb{E}_{\mathcal{S}_{n+1}} \exp\big(\lambda' \bar{g}_{m',m}(\mathcal{S}_{n+1})\big)$
$\le \frac{\ell - 1}{\ell} \ln \mathbb{E}_{\mathcal{S}_{n+1}} \exp\left(\frac{\ell \lambda'}{\ell - 1} \bar{g}_{m',m'}(\mathcal{S}_{n+1})\right)$
$+ \frac{1}{\ell} \ln \mathbb{E}_{\mathcal{S}_{n+1}} \exp\left(\frac{\ell \lambda'}{m'} \sum_{i=1}^{m'} \big[ \mathbb{E}_{\mathcal{S}_{m'}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i) - \mathbb{E}_{\mathcal{S}_{m}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i) \big]\right).$ (7.17)

Now by fixing $\{Z_{m+1},\dots,Z_n\}$, we may consider a function of $\mathcal{S}_{m'+1,\dots,m}=\{Z_{m'+1},\dots,Z_m\}$ defined as follows (we note that the function does not depend on $Z_{n+1}$ due to the expectation with respect to $Z_{n+1}$ over $\mathcal{S}_{m'}^{(i)}$ and $\mathcal{S}_m^{(i)}$):

$g'(\mathcal{S}_{m'+1,m}) = \ln \mathbb{E}_{\mathcal{S}_{m'}} \exp\left(\frac{\lambda}{m'} \sum_{i=1}^{m'} \big[ \mathbb{E}_{\mathcal{S}_{m'}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i) - \mathbb{E}_{\mathcal{S}_{m}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i) \big]\right).$

We note that for $i \le m'$, $[\mathbb{E}_{\mathcal{S}_{m'}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i) - \mathbb{E}_{\mathcal{S}_{m}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i)]$ as a function of $Z_i \sim \mathcal{D}$ has the same distribution as that of $[\mathbb{E}_{\mathcal{S}_{m'}} g(\mathcal{S}_n; Z) - \mathbb{E}_{\mathcal{S}_m} g(\mathcal{S}_n; Z)]$ (considered as a function of $Z \sim \mathcal{D}$). Since $\{Z_i\}$ are independent for $i \le m'$, conditioned on $\mathcal{S}_{m'+1,m}$, it follows that

$g'(\mathcal{S}_{m'+1,m}) = m' \ln \mathbb{E}_Z \exp\left(\frac{\lambda}{m'} [\mathbb{E}_{\mathcal{S}_{m'}} g(\mathcal{S}_n; Z) - \mathbb{E}_{\mathcal{S}_m} g(\mathcal{S}_n; Z)]\right).$ (7.18)

We also have the following result, which is a direct consequence of uniform stability:
$[\mathbb{E}_{\mathcal{S}_{m'}} g(\mathcal{S}_n; Z) - \mathbb{E}_{\mathcal{S}_m} g(\mathcal{S}_n; Z)] \le (m - m')\epsilon.$ (7.19)
In the following derivations, we further assume that $m \le 2m'$. It implies that $(m - m')/m' \le 1.$

It follows that
$g'(\mathcal{S}_{m'+1,m}) = m' \ln \mathbb{E}_Z \exp\left(\frac{\lambda}{m'} [\mathbb{E}_{\mathcal{S}_{m'}} g(\mathcal{S}_n; Z) - \mathbb{E}_{\mathcal{S}_m} g(\mathcal{S}_n; Z)]\right)$
$\le m' \big[ \mathbb{E}_Z \exp\left(\frac{\lambda}{m'} [\mathbb{E}_{\mathcal{S}_{m'}} g(\mathcal{S}_n; Z) - \mathbb{E}_{\mathcal{S}_m} g(\mathcal{S}_n; Z)]\right) - 1 - \frac{\lambda}{m'} \mathbb{E}_Z [\mathbb{E}_{\mathcal{S}_{m'}} g(\mathcal{S}_n; Z) - \mathbb{E}_{\mathcal{S}_m} g(\mathcal{S}_n; Z)] \big]$ 
$\le \frac{(\lambda)^2}{m'} \phi(0.4) \mathbb{E}_Z [\mathbb{E}_{\mathcal{S}_{m'}} g(\mathcal{S}_n; Z) - \mathbb{E}_{\mathcal{S}_m} g(\mathcal{S}_n; Z)]^2.$

In derivation, the first equality used (7.18). The first inequality used log(z) ≤ z−1, and 𝔼_Z g(·; Z) = 0 (which is an assumption of the theorem). The second inequality used the fact that φ(z) = (e^z − z − 1)/z² is increasing in z (this is the same derivation as that of Bennett’s inequality), and λ/m' [𝔼_{S_{m'}} g(S_n; Z)−𝔼_{S_m} g(S_n; Z)] ≤ 0.4 (which follows from (7.19), and λ(m−m')ε/m' ≤ λ ε ≤ 0.4).

Using the Efron-Stein inequality (6.10) and the ε uniform stability of g(·,·), we have

𝔼_{S_{m'+1,m}} g''(S_{m'+1,m}) ≤ 0.5(m−m')ε². (7.20)

Note also that for 𝒮_{m'+1,m} and 𝒮'_{m'+1,m} that differ by one element, we have

(g''(𝒮_{m'+1,m})−g''(𝒮'_{m'+1,m}))² ≤ (2ε𝔼_Z |𝔼_{S_{m'}} g(S_n; Z)−𝔼_{S_m} g(S_n; Z)| + ε²)² ≤ 5ε² g''(𝒮_{m'+1,m}) + 5ε⁴.

Therefore by summing over 𝒮'_{m'+1,m}, which differs from 𝒮_{m'+1,m} at j = m' + 1,…,m, we know that with g'', the condition of Proposition 7.25 holds with a = 5(m−m')ε² and b = 5(m−m')ε⁴. Therefore,

ln 𝔼_{S_{m'+1,m}} exp(g'(𝒮_{m'+1,m})) ≤ ln 𝔼_{S_{m'+1,m}} exp( (λ)²/m' φ(0.4) g''(𝒮_{m'+1,m}) ) ≤ (λ)²/m' φ(0.4) 𝔼_{S_{m'+1,m}} g''(𝒮_{m'+1,m}) + 2 (λ)⁴/(m')² φ(0.4)² (5(m−m')ε² 𝔼_{S_{m'+1,m}} g''(𝒮_{m'+1,m}) + 5(m−m')ε⁴).

The second inequality used Proposition 7.25 for g'', with a = 5(m−m')ε² and b = 5(m−m')ε⁴, and observe that (1−(λ²/m')φ(0.4)a)^{-1} ≤ (1−5(0.4)²φ(0.4))^{-1} ≤ 2.

By combining the above inequality with (7.20), and using φ(0.4) ≤ 0.58 and (m−m')/m' ≤ 1, we obtain

ln 𝔼_{S_{n+1}} exp( λ/m' Σ_{i=1}^{m'} [𝔼_{S_{m'}^{(i)}} g(S_{n+1}^{(i)}; Z_i) − 𝔼_{S_{m}^{(i)}} g(S_{n+1}^{(i)}; Z_i)] ) ≤ 0.3 λ² ε² + 6 λ⁴ ε⁴ ≤ 1.5 λ² ε². (7.21)

The second inequality used λ ε ≤ 0.4.

Now consider an increasing sequence 1 = m₀ < m₁ < m₂ < … < m_L = n, where m_ℓ = min(2^ℓ, n). Let λ_ℓ = λ/ℓ for ℓ > 0 and λ₀ = λ. We have

ℓ ln 𝔼_{S_{n+1}} exp( λ_ℓ \bar{g}_{m_ℓ,m_ℓ}(𝒮_{n+1}) ) ≤ ℓ ln 𝔼_{S_{n+1}} exp( λ_ℓ \bar{g}_{m_{ℓ-1},m_ℓ}(𝒮_{n+1}) ) ≤ (ℓ−1) ln 𝔼_{S_{n+1}} exp( λ_{ℓ-1} \bar{g}_{m_{ℓ-1},m_{ℓ-1}}(𝒮_{n+1}) ) + ln 𝔼_{S_{n+1}} exp( λ/m_{ℓ-1} Σ_{i=1}^{m_{ℓ-1}} [𝔼_{S_{m_{ℓ-1}}^{(i)}} g(S_{n+1}^{(i)}; Z_i) − 𝔼_{S_{m_ℓ}^{(i)}} g(S_{n+1}^{(i)}; Z_i)] ) ≤ (ℓ−1) ln 𝔼_{S_{n+1}} exp( λ_{ℓ-1} \bar{g}_{m_{ℓ-1},m_{ℓ-1}}(𝒮_{n+1}) ) + 1.5 λ² ε².

The first inequality used (7.16). The second inequality used (7.17) for ℓ > 1, and it becomes equality for ℓ = 1. The third inequality used (7.21).

By summing ℓ from 1 to L, we obtain

L · ln 𝔼_{S_{n+1}} exp (λ_L \bar{g}(𝒮_{n+1})) = L · ln 𝔼_{S_{n+1}} exp (λ_L \bar{g}_{m_L,m_L}(𝒮_{n+1})) ≤ 1.5 λ² ε² L.

This implies the first desired bound.

The second inequality follows from the Markov’s inequality as follows. Consider ε' = 2.5 ln(1/δ) > 0 and take λ = 0.4/ε. We have

ln Pr[\bar{g}(𝒮_{n+1}) ≥ L(1 + ε')ε] ≤ ln 𝔼_{S_{n+1}} exp (λ_L \bar{g}(𝒮_{n+1})) − λ_L L(1 + ε')ε ≤ [1.5 λ² ε² − (λ/L)L(1 + ε')ε] ≤ −0.4 ε' = ln δ.

This implies the second bound.

## 7.7 Historical and Bibliographical Remarks

The idea of uniform stability for nonrandomized algorithms was introduced by Bousquet and Elisseeff (2002), where the authors also considered deriving concentration bounds using McDiarmid’s inequality. However, concentration results obtained there were suboptimal. Better concentration bounds were obtained recently by Feldman and Vondrak (2019) and Bousquet et al. (2020). Theorem 7.24 is motivated by their analysis, and the result is comparable to that of Bousquet et al. (2020), but with a different proof. However, the concentration result holds only for uniform stability. The idea of using leave-one-out analysis to obtain expected oracle inequality was considered by Zhang (2003a). The leave-one-out stability analysis presented here generalizes the analysis of Zhang (2003a).

Randomized stability, discussed in this chapter, was introduced by Hardt et al. (2016) to analyze the generalization of stochastic gradient descent. It has become a popular theoretical tool for analyzing SGD-like procedures when it is necessary to run such algorithms multiple times over the data. For example, it is an essential technique in the generalization analysis of differentially private SGD (Bassily et al., 2020).

Gibbs distribution has its origin in physics (Gibbs, 1902). It has been studied in machine learning by McAllester (1999) in the supervised learning setting, and by Freund and Schapire (1997) in the online learning setting.

The SGLD algorithm was proposed by Welling and Teh (2011) for sampling from Bayesian posterior distributions (or Gibbs distributions). Its analysis has drawn significant interest, both for convergence and for generalization. The generalization analysis of SGLD for nonconvex functions in Theorem 7.23 is related to the information theoretical approach studied in some recent work (see Russo and Zou, 2016, 2019; Xu and Raginsky, 2017; Mou et al., 2018), which we will study further in Section 10.3.

The SGLD algorithm has also appeared in differential privacy, and in that setting it is referred to as the differentially private SGD (DP-SGD) algorithm (Abadi et al., 2016). Theorem 7.23 employs techniques simplified from the DP-SGD analysis (see Abadi et al., 2016). A more complex analysis that handles SGLD can be found in Li et al. (2020).
