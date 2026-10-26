
12.7 考虑一个由 \(\theta_D \in \mathbb{R}^d\) 参数化的分布族 \(\mathcal{D}\)，我们希望根据观测 \(Z_1, \ldots, Z_n \sim N(\theta_D, I)\) 来估计该分布族。假设 \(\theta_D\) 是稀疏的：对于某个 \(s \ll d\)，\(\|\theta_D\|_0 = s\)。

- 对于以 \(Q(\theta, \mathcal{D}) = \|\theta - \theta_D\|_2^2\) 为损失估计 \(\theta\) 的问题，推导一个下界。
- 推导一个与之匹配的上界。

## 序贯随机变量的概率不等式

在接下来几章研究的序贯估计问题中，我们观察一列随机变量 $Z_t \in \mathcal{Z}$，其中 $t = 1,2,\dots$，每个 $Z_t$ 可能依赖于之前的观测 $\mathcal{S}_{t-1} = [Z_1,\dots,Z_{t-1}] \in \mathcal{Z}^{t-1}$。由 $\{\mathcal{S}_t\}$ 生成的σ-代数构成一个自然滤流 $\{\mathcal{F}_t\}$。

若每个 $\xi_t$ 都是 $\mathcal{S}_t$ 的函数，则称序列 $\{\xi_t\}$ 适应于滤流 $\{\mathcal{F}_t\}$。也就是说，在时刻 $t$，每个 $\xi_t$ 不依赖于未来的观测 $Z_s$（$s > t$）。等价地，也可以说 $\xi_t$ 在 $\mathcal{F}_t$ 上是可测的。序列

$$ \xi'_t = \xi_t - \mathbb{E}[\xi_t|\mathcal{F}_{t-1}],\ \text{or equivalently}\ \xi'_t(\mathcal{S}_t) = \xi_t(\mathcal{S}_t) - \mathbb{E}_{Z_t|\mathcal{S}_{t-1}}\xi_t(\mathcal{S}_t), $$

被称为一个*鞅差序列*，它具有如下性质

$$ \mathbb{E}[\xi'_t|\mathcal{F}_{t-1}] = \mathbb{E}_{Z_t|\mathcal{S}_{t-1}}\xi'_t(\mathcal{S}_t) = 0. $$

鞅差序列的和

$$ \sum_{s=1}^t \xi'_s = \sum_{s=1}^t \xi'_s(\mathcal{S}_s) $$

被称为一个*鞅*，它对所有 $t$ 满足以下等式：

$$ \mathbb{E}\left[\sum_{s=1}^t \xi'_s|\mathcal{F}_{t-1}\right] = \sum_{s=1}^{t-1} \xi'_s,\ \text{or}\ \mathbb{E}_{Z_t|\mathcal{S}_{t-1}} \sum_{s=1}^t \xi'_s(\mathcal{S}_s) = \sum_{s=1}^{t-1} \xi'_s(\mathcal{S}_s). $$

鞅是独立随机变量之和（在第2章中研究）在序贯估计背景下的一种自然推广，它允许每个随机变量依赖于之前的随机变量。本章研究鞅的概率不等式和一致收敛性，这些对于分析序贯统计估计问题至关重要。

下面我们采用一种更精细的记号：设 $\mathcal{Z} = \mathcal{Z}^{(x)} \times \mathcal{Z}^{(y)}$，并且每个 $Z_t \in \mathcal{Z}$ 可写为 $Z_t = (Z_t^{(x)}, Z_t^{(y)})$。我们关注的是关于 $Z_t^{(y)}|Z_t^{(x)},\mathcal{S}_{t-1}$ 的条件期望，而不是关于 $Z_t|\mathcal{S}_{t-1}$ 的条件期望。这种形式在许多统计估计问题（如回归）中很有用。为了不引起混淆，本章通篇采用如下简化记号：

$$ \mathbb{E}_{Z_t^{(y)}}[\cdot] = \mathbb{E}_{Z_t^{(y)}|Z_t^{(x)},\mathcal{S}_{t-1}}[\cdot]. $$

### 13.1 鞅指数不等式

利用对数矩生成函数的技术，我们可以得到与第2章类似的鞅不等式。

**引理 13.1**  *考虑一列实值随机（可测）函数 ξ₁(S₁), …, ξₜ(Sₜ)。设 τ ≤ T 是一个停时，使得 1(t ≤ τ) 在 Sₜ 中可测。则有*

$$E_{S_T}\exp\left(\sum_{i=1}^{\tau}ξ_i-\sum_{i=1}^{\tau}\ln E_{Z_i^{(y)}}e^{ξ_i}\right)=1.$$

*证明.* 通过对 T 归纳来证明引理。当 T = 0 时，等式平凡成立。假设对于某个 T ≥ 1，命题在 T − 1 时成立。现在用归纳假设证明在时间 T 时的等式。

注意 ξ̃ᵢ = ξᵢ1(i ≤ τ) 在 Sᵢ 中可测。我们有

$$\sum_{i=1}^{\tau}ξ_i-\sum_{i=1}^{\tau}\ln E_{Z_i^{(y)}}e^{ξ_i}=\sum_{i=1}^{T}ξ̃_i-\sum_{i=1}^{T}\ln E_{Z_i^{(y)}}e^{ξ̃_i}.$$

因此

$$E_{Z_1,\ldots,Z_T}\exp\left(\sum_{i=1}^{\tau}ξ_i-\sum_{i=1}^{\tau}\ln E_{Z_i^{(y)}}e^{ξ_i}\right)$$
$$=E_{Z_1,\ldots,Z_T}\exp\left(\sum_{i=1}^{T}ξ̃_i-\sum_{i=1}^{T}\ln E_{Z_i^{(y)}}e^{ξ̃_i}\right)$$
$$=E_{Z_1,\ldots,Z_{T-1},Z_T^{(y)}}\exp\left(\sum_{i=1}^{T-1}ξ̃_i-\sum_{i=1}^{T-1}\ln E_{Z_i^{(y)}}e^{ξ̃_i}\right)E_{Z_T^{(y)}}\exp\left(ξ̃_T-\ln E_{Z_T^{(y)}}e^{ξ̃_T}\right)=1$$
$$=E_{Z_1,\ldots,Z_{T-1}}\exp\left(\sum_{i=1}^{T-1}ξ̃_i-\sum_{i=1}^{T-1}\ln E_{Z_i^{(y)}}e^{ξ̃_i}\right)$$
$$=E_{Z_1,\ldots,Z_{T-1}}\exp\left(\sum_{i=1}^{\min(τ,T-1)}ξ_i-\sum_{i=1}^{\min(τ,T-1)}\ln E_{Z_i^{(y)}}e^{ξ_i}\right)=1.$$

注意最后一个等式由归纳假设以及 min(τ, T − 1) 是 ≤ T − 1 的停时这一事实得出。

下面的结果是引理13.1的直接推论，它将关于独立变量和的定理2.5推广到鞅。

**定理 13.2**  *考虑一列随机函数 ξ₁(S₁), …, ξₜ(Sₜ), …，具有滤流 {Fₜ}。则对任意 δ ∈ (0, 1) 和 λ > 0，有*

$$\Pr\left[\exists n>0:-\sum_{i=1}^{n}ξ_i\ge\frac{\ln(1/δ)}{λ}+\frac{1}{λ}\sum_{i=1}^{n}\ln E_{Z_i^{(y)}}e^{-λξ_i}\right]\le δ.$$

*进一步，考虑一列适应于 {F_t} 的 {z_t ∈ ℝ}，以及 F_t 上的事件 A_t：*

ln Pr[∃n > 0: ∑_{i=1}^n ξ_i ≤ z_n & S_n ∈ A_n] ≤ inf_{λ>0} sup_{n>0} sup_{S_n ∈ A_n} [λ z_n + ∑_{i=1}^n ln E_{Z_i^{(y)}} e^{-λ ξ_i}] .

*证明* 我们将对有限时间序列 ξ_1(S_1), …, ξ_T(S_T) 证明该结果。令 T → ∞ 即可得到所需结果。令

ξ_τ(λ) = -∑_{i=1}^τ ln E_{Z_i^{(y)}} e^{-λ ξ_i} - λ ∑_{i=1}^τ ξ_i,

其中 τ 是一个停时，则由引理13.1可得：E e^{ξ_τ(λ)} = 1。现在对任意给定的序列 ẑ_n(S_n) 和 A_n，定义停时 τ 为 T，或第一个满足下面条件的时间步 n：

ξ_n(λ) ≥ -ẑ_n(S_n) 且 S_n ∈ A_n

对于每个序列 S_T。于是有

Pr(∃n : ξ_n(λ) ≥ -ẑ_n(S_n) & S_n ∈ A_n) inf_{n>0, S_n ∈ A_n} e^{-ẑ_n(S_n)} ≤ E[ e^{ξ_τ(λ)+ẑ_τ(S_τ)} 1(S_τ ∈ A_τ) ] inf_{n>0, S_n ∈ A_n} e^{-ẑ_n(S_n)} ≤ E[ e^{ξ_τ(λ)+ẑ_τ(S_τ)} 1(S_τ ∈ A_τ) e^{-ẑ_τ(S_τ)} ] ≤ E e^{ξ_τ(λ)} = 1.

因此我们得到

ln Pr[∃n > 0: -λ ∑_{i=1}^n ξ_i ≥ -ẑ_n(S_n) + ∑_{i=1}^n ln E_{Z_i^{(y)}} e^{-λ ξ_i} & S_n ∈ A_n] ≤ sup_{n>0 : S_n ∈ A_n} ẑ_n(S_n).

令 ẑ(S_n) = ln δ，即得第一个不等式。令

ẑ_n(S_n) = λ z_n + ∑_{i=1}^n ln E_{Z_i^{(y)}} e^{-λ ξ_i},

即得第二个不等式。□

定理 13.2 与定理 2.5 的一个区别是：在后者中，可以对 λ 进行优化，从而得到用速率函数 I_X(z) 表示的不等式。然而，对于序贯问题，我们不能直接优化定理 13.2 中第一个不等式中的 λ，否则需要付出与 λ 上的一致收敛相关的代价（通常会导致额外的 ln n 项）。这是因为在序贯问题中，条件期望可能仍然依赖于观测 S_n，因此对 λ 进行优化会导致 λ 依赖于样本。定理 13.2 中的第二个不等式通过在受限事件 A_n 上限制对 λ 的优化来解决这一问题。

现在，利用第2章的对数矩生成函数，我们得到以下结果。

**定理 13.3（鞅次高斯不等式）**

考虑一列随机函数 ξ₁(S₁), …, ξₜ(Sₜ), …。假设每个 ξᵢ 关于 Zᵢ^(y) 是次高斯的：

$$\ln \mathbb{E}_{Z_i^{(y)}} e^{\lambda \xi_i} \le \lambda \mathbb{E}_{Z_i^{(y)}} \xi_i + \frac{\lambda^2 \sigma_i^2}{2}$$

其中某些 σᵢ 可能依赖于 Sᵢ₋₁ 和 Zᵢ^(x)。则对所有 σ > 0，以至少 1 − δ 的概率有

$$\forall n > 0: \sum_{i=1}^n \mathbb{E}_{Z_i^{(y)}} \xi_i < \sum_{i=1}^n \xi_i + \left(\sigma + \frac{\sum_{i=1}^n \sigma_i^2}{\sigma}\right) \sqrt{\frac{\ln(1/\delta)}{2}}.$$

证明 我们可以取 λ = √{2 ln(1/δ)}/σ，然后应用定理13.2的第一个不等式。

由于在定理13.3中允许 σᵢ 依赖于数据，我们通常不能直接取 σ² = ∑ᵢ₌₁ⁿ σᵢ²。然而，如果 σᵢ 不依赖于数据，那么我们可以针对特定时间范围 n 进一步优化 σ。特别地，次高斯不等式的一个直接推论是加性Chernoff界，如下所述。它通常被称为Azuma不等式（Azuma, 1967）。

**定理 13.4（Azuma不等式）**

考虑一列随机函数 ξ₁(S₁), …, ξₙ(Sₙ)，其中固定数量 n > 0。如果对每个 i，有 sup ξᵢ − inf ξᵢ ≤ Mᵢ（Mᵢ 为某个常数），则以至少 1 − δ 的概率有

$$\frac{1}{n} \sum_{i=1}^n \mathbb{E}_{Z_i^{(y)}} \xi_i < \frac{1}{n} \sum_{i=1}^n \xi_i + \sqrt{\frac{\sum_{i=1}^n M_i^2 \ln(1/\delta)}{2 n^2}}.$$

证明 利用次高斯矩界（见例2.14），取定理13.3中的 σᵢ = Mᵢ/2，并令 4σ² = ∑ᵢ₌₁ⁿ Mᵢ²，即可得到所需界。

对于乘性Chernoff界的类比，我们可以得到比推论2.18稍弱的一个版本。

**定理 13.5**

考虑一列随机函数 ξ₁(S₁), …, ξₜ(Sₜ), …，使得对所有 i 有 ξᵢ ∈ [0,1]。则对于 λ > 0，以至少 1 − δ 的概率有

$$\forall n > 0: \frac{1}{n} \sum_{i=1}^n \mathbb{E}_{Z_i^{(y)}} \xi_i < \frac{\lambda}{1 - e^{-\lambda}} \frac{1}{n} \sum_{i=1}^n \xi_i + \frac{\ln(1/\delta)}{(1 - e^{-\lambda}) n}.$$

类似地，对于 λ > 0，以至少 1 − δ 的概率有

$$\forall n > 0: \frac{1}{n} \sum_{i=1}^n \mathbb{E}_{Z_i^{(y)}} \xi_i > \frac{\lambda}{e^{\lambda} - 1} \frac{1}{n} \sum_{i=1}^n \xi_i - \frac{\ln(1/\delta)}{(e^{\lambda} - 1) n}.$$
