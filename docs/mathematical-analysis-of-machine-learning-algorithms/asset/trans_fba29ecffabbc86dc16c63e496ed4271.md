

第一个不等式应用了所有 $\tilde{\mathcal{S}}_{m'}$ 具有相同分布这一事实。

同样，根据定义很容易验证以下等式：

$\bar{g}_{m',m}(\mathcal{S}_{n+1}) = \bar{g}_{m',m'}(\mathcal{S}_{n+1}) + \frac{1}{m'} \sum_{i=1}^{m'} \big[ \mathbb{E}_{\mathcal{S}_{m'}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i) - \mathbb{E}_{\mathcal{S}_{m}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i) \big] .$

现在利用这一分解，并对凸函数 $\ln \mathbb{E}_{\mathcal{S}_{n+1}} \exp(g'(\mathcal{S}_{n+1}))$ 关于 $g'(\cdot)$ 应用 Jensen 不等式，对所有 $\lambda'$ 和 $\ell > 1$，我们得到

$\ln \mathbb{E}_{\mathcal{S}_{n+1}} \exp\big(\lambda' \bar{g}_{m',m}(\mathcal{S}_{n+1})\big)$
$\le \frac{\ell - 1}{\ell} \ln \mathbb{E}_{\mathcal{S}_{n+1}} \exp\left(\frac{\ell \lambda'}{\ell - 1} \bar{g}_{m',m'}(\mathcal{S}_{n+1})\right)$
$+ \frac{1}{\ell} \ln \mathbb{E}_{\mathcal{S}_{n+1}} \exp\left(\frac{\ell \lambda'}{m'} \sum_{i=1}^{m'} \big[ \mathbb{E}_{\mathcal{S}_{m'}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i) - \mathbb{E}_{\mathcal{S}_{m}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i) \big]\right).$ (7.17)

现在固定 $\{Z_{m+1},\dots,Z_n\}$，我们可以将 $\mathcal{S}_{m'+1,\dots,m}=\{Z_{m'+1},\dots,Z_m\}$ 的函数定义如下（我们注意到该函数不依赖于 $Z_{n+1}$，因为对 $Z_{n+1}$ 在 $\mathcal{S}_{m'}^{(i)}$ 和 $\mathcal{S}_m^{(i)}$ 上取了期望）：

$g'(\mathcal{S}_{m'+1,m}) = \ln \mathbb{E}_{\mathcal{S}_{m'}} \exp\left(\frac{\lambda}{m'} \sum_{i=1}^{m'} \big[ \mathbb{E}_{\mathcal{S}_{m'}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i) - \mathbb{E}_{\mathcal{S}_{m}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i) \big]\right).$

我们注意到，对于 $i \le m'$，$[\mathbb{E}_{\mathcal{S}_{m'}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i) - \mathbb{E}_{\mathcal{S}_{m}^{(i)}} g(\mathcal{S}_{n+1}^{(i)}; Z_i)]$ 作为 $Z_i \sim \mathcal{D}$ 的函数，与 $[\mathbb{E}_{\mathcal{S}_{m'}} g(\mathcal{S}_n; Z) - \mathbb{E}_{\mathcal{S}_m} g(\mathcal{S}_n; Z)]$（作为 $Z \sim \mathcal{D}$ 的函数）具有相同的分布。由于 $\{Z_i\}$ 对 $i \le m'$ 是独立的，在给定 $\mathcal{S}_{m'+1,m}$ 的条件下，可得

$g'(\mathcal{S}_{m'+1,m}) = m' \ln \mathbb{E}_Z \exp\left(\frac{\lambda}{m'} [\mathbb{E}_{\mathcal{S}_{m'}} g(\mathcal{S}_n; Z) - \mathbb{E}_{\mathcal{S}_m} g(\mathcal{S}_n; Z)]\right).$ (7.18)

我们还有以下结果是均匀稳定性的直接推论：
$[\mathbb{E}_{\mathcal{S}_{m'}} g(\mathcal{S}_n; Z) - \mathbb{E}_{\mathcal{S}_m} g(\mathcal{S}_n; Z)] \le (m - m')\epsilon.$ (7.19)

在下面的推导中，我们进一步假设 $m \le 2m'$。这意味着 $(m - m')/m' \le 1.$

由此可得
$g'(\mathcal{S}_{m'+1,m}) = m' \ln \mathbb{E}_Z \exp\left(\frac{\lambda}{m'} [\mathbb{E}_{\mathcal{S}_{m'}} g(\mathcal{S}_n; Z) - \mathbb{E}_{\mathcal{S}_m} g(\mathcal{S}_n; Z)]\right)$
$\le m' \big[ \mathbb{E}_Z \exp\left(\frac{\lambda}{m'} [\mathbb{E}_{\mathcal{S}_{m'}} g(\mathcal{S}_n; Z) - \mathbb{E}_{\mathcal{S}_m} g(\mathcal{S}_n; Z)]\right) - 1 - \frac{\lambda}{m'} \mathbb{E}_Z [\mathbb{E}_{\mathcal{S}_{m'}} g(\mathcal{S}_n; Z) - \mathbb{E}_{\mathcal{S}_m} g(\mathcal{S}_n; Z)] \big]$ 
$\le \frac{(\lambda)^2}{m'} \phi(0.4) \mathbb{E}_Z [\mathbb{E}_{\mathcal{S}_{m'}} g(\mathcal{S}_n; Z) - \mathbb{E}_{\mathcal{S}_m} g(\mathcal{S}_n; Z)]^2.$

在推导中，第一个等式使用了 (7.18)。第一个不等式使用了 log(z) ≤ z−1，以及 𝔼_Z g(·; Z) = 0（这是该定理的一个假设）。第二个不等式使用了 φ(z) = (e^z − z − 1)/z² 关于 z 单调递增的事实（这与 Bennett 不等式的推导相同），且 λ/m' [𝔼_{S_{m'}} g(S_n; Z)−𝔼_{S_m} g(S_n; Z)] ≤ 0.4（这由 (7.19) 及 λ(m−m')ε/m' ≤ λ ε ≤ 0.4 得出）。

利用 Efron-Stein 不等式 (6.10) 和 g(·,·) 的 ε 均匀稳定性，我们有

𝔼_{S_{m'+1,m}} g''(S_{m'+1,m}) ≤ 0.5(m−m')ε². (7.20)

另外注意，对于仅相差一个元素的 𝒮_{m'+1,m} 和 𝒮'_{m'+1,m}，我们有

(g''(𝒮_{m'+1,m})−g''(𝒮'_{m'+1,m}))² ≤ (2ε𝔼_Z |𝔼_{S_{m'}} g(S_n; Z)−𝔼_{S_m} g(S_n; Z)| + ε²)² ≤ 5ε² g''(𝒮_{m'+1,m}) + 5ε⁴.

因此，对所有与 𝒮_{m'+1,m} 在 j = m' + 1,…,m 处不同的 𝒮'_{m'+1,m} 求和，我们知道对于 g''，命题 7.25 的条件以 a = 5(m−m')ε² 和 b = 5(m−m')ε⁴ 成立。因此，

ln 𝔼_{S_{m'+1,m}} exp(g'(𝒮_{m'+1,m})) ≤ ln 𝔼_{S_{m'+1,m}} exp( (λ)²/m' φ(0.4) g''(𝒮_{m'+1,m}) ) ≤ (λ)²/m' φ(0.4) 𝔼_{S_{m'+1,m}} g''(𝒮_{m'+1,m}) + 2 (λ)⁴/(m')² φ(0.4)² (5(m−m')ε² 𝔼_{S_{m'+1,m}} g''(𝒮_{m'+1,m}) + 5(m−m')ε⁴).

第二个不等式对 g'' 使用了命题 7.25，其中 a = 5(m−m')ε²，b = 5(m−m')ε⁴，并且注意到 (1−(λ²/m')φ(0.4)a)^{-1} ≤ (1−5(0.4)²φ(0.4))^{-1} ≤ 2.

将上述不等式与 (7.20) 结合，并利用 φ(0.4) ≤ 0.58 和 (m−m')/m' ≤ 1，我们得到

ln 𝔼_{S_{n+1}} exp( λ/m' Σ_{i=1}^{m'} [𝔼_{S_{m'}^{(i)}} g(S_{n+1}^{(i)}; Z_i) − 𝔼_{S_{m}^{(i)}} g(S_{n+1}^{(i)}; Z_i)] ) ≤ 0.3 λ² ε² + 6 λ⁴ ε⁴ ≤ 1.5 λ² ε². (7.21)

第二个不等式使用了 λ ε ≤ 0.4。

现在考虑一个递增序列 1 = m₀ < m₁ < m₂ < … < m_L = n，其中 m_ℓ = min(2^ℓ, n)。令 ℓ > 0 时 λ_ℓ = λ/ℓ，且 λ₀ = λ。我们有

ℓ ln 𝔼_{S_{n+1}} exp( λ_ℓ \bar{g}_{m_ℓ,m_ℓ}(𝒮_{n+1}) ) ≤ ℓ ln 𝔼_{S_{n+1}} exp( λ_ℓ \bar{g}_{m_{ℓ-1},m_ℓ}(𝒮_{n+1}) ) ≤ (ℓ−1) ln 𝔼_{S_{n+1}} exp( λ_{ℓ-1} \bar{g}_{m_{ℓ-1},m_{ℓ-1}}(𝒮_{n+1}) ) + ln 𝔼_{S_{n+1}} exp( λ/m_{ℓ-1} Σ_{i=1}^{m_{ℓ-1}} [𝔼_{S_{m_{ℓ-1}}^{(i)}} g(S_{n+1}^{(i)}; Z_i) − 𝔼_{S_{m_ℓ}^{(i)}} g(S_{n+1}^{(i)}; Z_i)] ) ≤ (ℓ−1) ln 𝔼_{S_{n+1}} exp( λ_{ℓ-1} \bar{g}_{m_{ℓ-1},m_{ℓ-1}}(𝒮_{n+1}) ) + 1.5 λ² ε².

第一个不等式使用了 (7.16)。第二个不等式对 ℓ > 1 使用了 (7.17)，且当 ℓ = 1 时变为等式。第三个不等式使用了 (7.21)。

将 ℓ 从 1 到 L 求和，我们得到

L · ln 𝔼_{S_{n+1}} exp (λ_L \bar{g}(𝒮_{n+1})) = L · ln 𝔼_{S_{n+1}} exp (λ_L \bar{g}_{m_L,m_L}(𝒮_{n+1})) ≤ 1.5 λ² ε² L.

这就得到了第一个期望的界。

第二个界由马尔可夫不等式如下得到。考虑 ε' = 2.5 ln(1/δ) > 0 并取 λ = 0.4/ε。我们有

ln Pr[\bar{g}(𝒮_{n+1}) ≥ L(1 + ε')ε] ≤ ln 𝔼_{S_{n+1}} exp (λ_L \bar{g}(𝒮_{n+1})) − λ_L L(1 + ε')ε ≤ [1.5 λ² ε² − (λ/L)L(1 + ε')ε] ≤ −0.4 ε' = ln δ.

这就得到了第二个界。

## 7.7 历史与文献评注

非随机化算法的均匀稳定性思想由 Bousquet 和 Elisseeff (2002) 提出，作者还考虑了利用 McDiarmid 不等式导出集中界。然而，那里得到的集中结果不是最优的。Feldman 和 Vondrak (2019) 以及 Bousquet 等人 (2020) 近期得到了更好的集中界。定理 7.24 的提出受到了他们分析的启发，其结果与 Bousquet 等人 (2020) 的相当，但证明方法不同。然而，该集中结果仅对均匀稳定性成立。使用留一分析（leave-one-out analysis）来获得期望预言不等式（expected oracle inequality）的思想由 Zhang (2003a) 提出。本章给出的留一稳定性分析推广了 Zhang (2003a) 的分析。

本章讨论的随机化稳定性由 Hardt 等人 (2016) 提出，用于分析随机梯度下降的泛化性能。当需要多次在数据上运行此类算法时，它已成为分析类似 SGD 过程的常用理论工具。例如，在差分隐私 SGD 的泛化分析中，它是一种基本技术（Bassily 等人，2020）。

吉布斯分布起源于物理学（Gibbs, 1902）。McAllester (1999) 在监督学习框架下对其进行了研究，Freund 和 Schapire (1997) 则在线学习框架下进行了研究。

SGLD 算法由 Welling 和 Teh (2011) 提出，用于从贝叶斯后验分布（或吉布斯分布）中采样。其分析引起了广泛的关注，无论是收敛性还是泛化性。定理 7.23 中关于非凸函数的 SGLD 泛化分析与近期一些工作中的信息论方法相关（参见 Russo 和 Zou, 2016, 2019; Xu 和 Raginsky, 2017; Mou 等人, 2018），我们将在 10.3 节进一步研究。

SGLD 算法也出现在差分隐私中，在这种情况下它被称为差分隐私 SGD（DP-SGD）算法（Abadi 等人，2016）。定理 7.23 使用了从 DP-SGD 分析中简化而来的技术（参见 Abadi 等人，2016）。Li 等人 (2020) 中可以找到处理 SGLD 的更复杂分析。

