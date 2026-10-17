
### 命题 4.3.1
设 `d, K ∈ ℕ`，`L ∈ [0, ∞)`，设 `E ⊆ ℝ^{d}` 为一个集合，设 `f₁, f₂, …, f_K ∈ E`，设 `f: E → ℝ` 满足对所有 `x, y ∈ E` 都有 `|f(x) - f(y)| ≤ L ‖x - y‖₁`，且设 `y ∈ ℝ^{K}`，`Φ ∈ ℕ` 满足 `η = (f(f₁), f(f₂), …, f(f_K))` 以及

$$\Phi = \mathbb{M}_{K} \bullet \mathbf{A}_{-L1K,n} \bullet \mathbf{P}_{K}\big(\mathbb{L}_{d} \bullet \mathbf{A}_{1_{d}-\mathbf{f}_{1}}, \mathbb{L}_{d} \bullet \mathbf{A}_{1_{d}-\mathbf{f}_{2}}, \ldots, \mathbb{L}_{d} \bullet \mathbf{A}_{1_{d}-\mathbf{f}_{K}}\big) \bullet \mathbb{T}_{d,K} \quad (4.77)$$

参见定义 1.3.1, 1.5.5, 2.1.1, 2.2.1, 2.3.1, 2.4.6, 3.3.4, 4.2.1, 和 4.2.5。则

$$\operatorname{sup}_{x \in E}|(\mathcal{R}_{\mathbf{r}}^{\mathbb{N}}(\Phi))(x) - f(x)| \leq 2L \big[\operatorname{sup}_{x \in E}(\min_{k \in \{1, \ldots, K\}} \|x - \mathbf{f}_{k}\|_{1})\big] \quad (4.78)$$

参见定义 1.2.4 和 1.3.4。

命题 4.3.1 的证明。在整个证明过程中，设 `F: ℝ^{d} → ℝ` 满足对所有 `x ∈ ℝ^{d}` 都有

$$F(x) = \max_{k \in \{1, \ldots, K\}}(f(\mathbf{f}_{k}) - L\|x - \mathbf{f}_{k}\|_{1}). \quad (4.79)$$

注意到推论 4.1.4、公式 `(4.79)` 以及假设条件“对所有 `x, y ∈ E` 都有 `|f(x) - f(y)| ≤ L‖x - y‖₁`”保证了

$$\operatorname{sup}_{x \in E}|F(x) - f(x)| \leq 2L \big[\operatorname{sup}_{x \in E}(\min_{k \in \{1, \ldots, K\}}\|x - \mathbf{f}_{k}\|_{1})\big]. \quad (4.80)$$

此外，请注意引理 4.2.9 确保了对所有 `x ∈ E`，都有 `F(x) = (\mathcal{R}_{\mathbf{r}}^{\mathbb{N}}(\Phi))(x)`。将此与 `(4.80)` 结合即证明了 `(4.78)`。命题 4.3.1 的证明至此完成。

习题 4.3.1。证明或反驳以下陈述：存在 `Φ ∈ ℕ` 使得 `\mathcal{I}(\Phi) = 2`，`\mathcal{O}(\Phi) = 1`，`\mathcal{P}(\Phi) < 20`，并且

$$\sup_{v = (x,y) \in [0,2]^{2}} \big| x^{2} + y^{2} - 2x - 2y + 2 - (\mathcal{R}_{\mathbf{r}}^{\mathbb{N}}(\Phi))(v) \big| \leq \frac{3}{8}. \quad (4.81)$$

## 4.3.2 覆盖数估计

### 定义 4.3.2 覆盖数
设 `(E, δ)` 为一个度量空间，设 `r ∈ [0, ∞)`。则我们用 `\mathcal{C}^{(E,\delta),r} ∈ ℕ₀ ∪ {∞}`  表示由下式给出的扩展实数

$$\mathcal{C}^{(E,\delta),r} = \min \bigg( \big\{n \in ℕ₀ \colon \big[\exists A ⊆ E \colon \big[(|A| ≤ n) ∧ (\forall x ∈ E \colon ∃ a ∈ A \colon δ_{(a,x)} ≤ r)\big]\big] \big\} ∪ \{∞\} \bigg) \quad (4.82)$$

并称 `\mathcal{C}^{(E,\delta),r}` 为 `(E, δ)` 的 `r`-覆盖数。

### 引理 4.3.3
设 `(E,δ)` 为一个度量空间，设 `r ∈ [0, ∞]`。则

$$\mathcal{C}_{(E,\delta), r} = \begin{cases} \emptyset & : X = \emptyset \\ \inf \left( \left\{ n ∈ ℕ : \left( \exists x_1, x_2, \dots, x_n ∈ E : \right. \left. E ⊆ \bigcup_{m=1}^n \{ v ∈ E : d(x_m, v) ≤ r \} \right) \right\} ∪ \{ \infty \} \right) & : X ≠ \emptyset \end{cases} \tag{4.83}$$

参见定义 4.3.2。

引理 4.3.3 的证明。在整个证明过程中，不失一般性，假设 `E ≠ ∅`。注意到引理 12.2.4 确立了公式 `(4.83)`。引理 4.3.3 的证明至此完成。

习题 4.3.2。证明或反驳以下陈述：对于每个度量空间 `(X, d)`，每个 `Y ⊆ X`，以及每个 `r ∈ [0, ∞]`，都有 `\mathcal{C}_{(Y, d|_{Y × Y}), r} ≤ \mathcal{C}_{(X, d), r}`。

习题 4.3.3。证明或反驳以下陈述：对于每个度量空间 `(E,δ)`，都有 `\mathcal{C}_{(E,δ), ∞} = 1`。

习题 4.3.4。证明或反驳以下陈述：对于每个度量空间 `(E,δ)` 和每个满足 `\mathcal{C}_{(E,δ), r} < ∞` 的 `r ∈ [0, ∞)`，都有 `E` 是有界的。

习题 4.3.5。证明或反驳以下陈述：对于每个有界度量空间 `(E,δ)` 和每个 `r ∈ [0, ∞)`，都有 `\mathcal{C}_{(E,δ), r} < ∞`。

### 引理 4.3.4
设 `d ∈ ℕ`，`a ∈ ℝ`，`b ∈ (a, ∞)`，`r ∈ (0, ∞)`，且对于每个 `p ∈ [1, ∞)`，设 `δ_p : ([a, b]^d × ([a, b]^d) → [0, ∞)` 满足对所有 `x, y ∈ [a, b]^d` 都有 `δ_p(x, y) = ‖ x - y ‖_p`。则对于所有 `p ∈ [1, ∞)`，都有

$$\mathcal{C}_{([a,b]^d,\delta_p),r} \leq \left( \frac{d^{1/p}(b-a)}{2r} \right)^d \leq \begin{cases} 1 & : r ≥ \frac{d^{1/p}(b-a)}{2} \\ \left( \frac{d(b-a)}{r} \right)^d & : r < \frac{d^{1/p}(b-a)}{2}. \end{cases} \tag{4.84}$$

参见定义 4.2.6 和 4.3.2。

引理 4.3.4 的证明。在整个证明过程中，设 `(\mathfrak{N}_p)_{p ∈ [1, ∞)} ⊆ ℕ` 满足对所有 `p ∈ [1, ∞)` 都有

$$\mathfrak{N}_p = \left\lceil \frac{d^{1/p}(b-a)}{2r} \right\rceil, \tag{4.85}$$

对于每个 `N ∈ ℕ`，`i ∈ { 1, 2, …, N }`，设 `g_{N, i} ∈ [a, b]` 由下式给出

$$g_{N, i} = a + \frac{(i-1/2)(b-a)}{N} \tag{4.86}$$

且对于每个 `p ∈ [1, ∞)`，设 `A_p ⊆ [a, b]^d` 由下式给出

$$A_p = \{g_{\mathfrak{N}_p,1}, g_{\mathfrak{N}_p,2}, \dots, g_{\mathfrak{N}_p,\mathfrak{N}_p}\}^d \tag{4.87}$$

注意到对于所有 `N ∈ ℕ`，`i ∈ {1, 2, …, N}`，`x ∈ [a + \frac{(i-1)(b-a)}{N}, g_{N,i}]`，都有

$$|x - g_{N,i}| ≤ \frac{b-a}{2N}. \tag{4.88}$$

此外，注意到对于所有 `N ∈ ℕ`，`i ∈ {1, 2, …, N}`，`x ∈ [g_{N,i}, a + \frac{i(b-a)}{N}]`，都有

$$|x - g_{N,i}| ≤ \frac{b-a}{2N}. \tag{4.89}$$

将此与 `(4.88)` 结合可知，对于所有 `N ∈ ℕ`，`i ∈ {1, 2, …, N}`，`x ∈ [a + \frac{(i-1)(b-a)}{N}, a + \frac{i(b-a)}{N}]`，都有 `|x - g_{N,i}| ≤ \frac{(b-a)}{2N}`。这证明了对于每个 `N ∈ ℕ`，`x ∈ [a, b]`，存在 `y ∈ {g_{N,1}, g_{N,2}, …, g_{N,N}}` 使得

$$|x - y| ≤ \frac{b-a}{2N}. \tag{4.90}$$

这确立了对于每个 `p ∈ [1, ∞)`，`x = (x_1, x_2, …, x_d) ∈ [a, b]^d`，存在 `y = (y_1, y_2, …, y_d) ∈ A_p` 使得

$$\delta_p(x, y) = \|x - y\|_p = \left(\sum_{i=1}^d |x_i - y_i|^p\right)^{1/p} ≤ \frac{d^{1/p}(b-a)}{2\mathfrak{N}_p} ≤ r. \tag{4.91}$$

将此与 `(4.82)`、`(4.87)`、`(4.85)` 结合可知，对于所有 `p ∈ [1, ∞)`，都有

$$\mathcal{C}^{([a,b]^d, \delta_p), r} ≤ |A_p| = |\mathfrak{N}_p|^d$$

引理 4.3.4 的证明至此完成。

## 4.3.3 逼近误差的收敛速率

### 引理 4.3.5
设 `d ∈ ℕ`，`L, a ∈ ℝ`，`b ∈ (a, ∞)`，设 `f: [a, b]^d → ℝ` 满足对所有 `x, y ∈ [a, b]^d` 都有 `|f(x) - f(y)| ≤ L ‖x - y‖₁`，且设 `\mathbf{F} = \mathbf{A}_{0, f([a+b)/2, (a+b)/2]^{\times d}} ∈ ℝ^{1 × d} × ℝ^1`。则

(i) 成立 `\mathcal{I}(\mathbf{F}) = d`，

(ii) `\mathcal{O}(\mathbf{F}) = 1` 成立，

(iii) `\mathcal{H}(\mathbf{F}) = 0` 成立，

(iv) `\mathcal{P}(\mathbf{F}) = d + 1` 成立，

(v) `‖\mathcal{T}(\mathbf{F})‖_∞ ≤ \sup_{x ∈ [a,b]^d} |f(x)|` 成立，且

(vi) `\sup_{x ∈ [a,b]^d} | (\mathcal{R}_v^\mathbf{N}(\mathbf{F}))(x) - f(x)| ≤ \frac{d L (b-a)}{2}` 成立

参见定义 1.2.4, 1.3.1, 1.3.4, 和 1.3.5。

引理 4.3.5 的证明。注意，假设对于所有 `x, y ∈ [a,b]^d` 都有 `|f(x) - f(y)| ≤ L ‖x - y‖₁` 成立，这保证了 `L ≥ 0`。接下来观察，引理 2.3.2 保证了对于所有 `x ∈ ℝ^d` 都有

$$ (\mathcal{R}_v^\mathbf{N}(\mathbf{F}))(x) = f((a+b)/2, (a+b)/2, \dots, (a+b)/2). \qquad (4.93) $$

对于所有 `x ∈ [a,b]` 都有 `|x - (a+b)/2| ≤ (b-a)/2` 成立，且假设对于所有 `x, y ∈ [a,b]^d` 都有 `|f(x) - f(y)| ≤ L ‖x - y‖₁` 成立，因此确保对于所有 `x = (x_1, x_2, …, x_d) ∈ [a,b]^d` 都有
