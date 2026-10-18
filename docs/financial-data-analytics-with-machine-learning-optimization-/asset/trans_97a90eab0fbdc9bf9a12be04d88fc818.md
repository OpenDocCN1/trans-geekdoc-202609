

[程序 5.29](#c05.xhtml#c05-gra-00029) 通过 Python 和 [5.30](#c05.xhtml#c05-gra-00030) 通过 `R` 报告了在 CEV 模型下，不同参数 `θ` 时欧洲看涨期权的 Delta 和 Vega 估计值，采用前向差分法和中心差分法。当 `θ equals 2` 时，等同于经典 Black–Scholes 模型，随着 `h` 变小，两种方法的 Delta 和 Vega 估计值分别收敛到其理论值 0.8555 和 2.2735。可以观察到，与前向差分法相比，中心差分法提供了更准确的估计；无论使用 Python 还是 `R`，Vega 的估计性能均不如 Delta。请注意，当 `θ equals 2` 时 `σ(t) = σ S_t`，当 `θ equals 1.8` 时 `σ(t) = σ S_t^0.9`，与 `θ equals 2` 相比，`θ less-than 2` 时 `S_t` 的相应动态相对于其当前价格水平波动性较小，导致 `σ` 在期权定价中相对不那么重要，因此我们预期当 `θ` 变小时 Vega 的值会相对较小。相反，在缺乏较大波动率的情况下，初始股票价格 `S_0` 对期权定价变得更加关键，因此我们预期随着 `θ` 变小，Delta 的值会更大。特别是，当 `θ equals 1.8` 时，Delta 和 Vega 估计值分别收敛到 0.893 和 1.4；当 `θ equals 1` 时，Delta 和 Vega 估计值分别收敛到 0.997 和 0.024。

## (II) 路径微分法

可交换性假设指出 `α′(θ) = d/dθ E[y(θ)] = E[d y(θ) / d θ]`。当以下条件成立时，该假设可以成立：

```
|y(θ₁) − y(θ₂)| < C |θ₁ − θ₂|, for all θ₁ and θ₂, almost surely, for some C > 0.
```

确实，该条件保证了根据 *Lebesgue Dominated Convergence Theorem* 可以交换微分和期望的取值。

假设衍生品的收益由 `y = f(S_T)` 给出。为了说明 *pathwise differentiation approach* 的工作原理，我们考虑该衍生品在 Black–Scholes 框架下的 Delta，即相对于当前股票价格 `S_0` 的价格敏感度。基于可交换性假设，我们考虑相对于当前价格的随机收益的导数：

