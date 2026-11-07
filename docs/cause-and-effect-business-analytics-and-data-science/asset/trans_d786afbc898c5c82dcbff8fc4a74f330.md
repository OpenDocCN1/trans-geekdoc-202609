
### 1. 相同属性集（响应面方法）
在最佳属性组合落在“角点解”（例如最低 APR 水平、最高返利、最高信用额度）的情况中，人们可能会想知道是否进一步扩展可能水平会带来更好的结果。同样，即使目前最好的属性水平位于可能水平的中间，人们也可能会想知道它是否确实是“最优”水平（例如，如果就产生增量收入而言最好的 APR 水平是 6.9%，人们可能想知道 5.9%、6.5%、7.5% 或 7.9% 是否会更好）。在这些情况下，我们可能希望“继续测试”，直到获得更“全局最优解”。在工业实验（工业产品设计、质量控制等）中一种常见的方法，即响应面方法（Response Surface Methodology, RSM），旨在通过沿最陡上升方向搜索，迭代地寻找同一组属性下更好、最终最优的水平。虽然 RSM 是工业实验中的常见方法，但在第203页营销或相关商业环境中却鲜为人知，但这无疑是一个机会。我们在本章中不讨论 RSM（因为它本身就需要一整章），但感兴趣的读者可以参考 [Box 等 (1978)](#chapter7.xhtml#ref7_4)、[Montgomery (1991)](#chapter7.xhtml#ref7_30)、[Box (2006)](#chapter7.xhtml#ref7_3)、[Khuri 和 Mukhopadhyay (2010)](#chapter7.xhtml#ref7_17) 或 [Goos 和 Jones (2011)](#chapter7.xhtml#ref7_13)。

### 2. 新属性
秉承 Kaizen（持续改进）和可持续竞争优势的精神，人们会尝试发挥创造力，构想其他可能有助于改善响应结果的属性。因此，以持续的方式测试新的、潜在有用的属性是自然而然的。

### 3. 根本性转变
客户行为或其他条件（经济、地理、人口统计等）的变化可能导致响应函数发生偏移。例如，在瞬息万变的科技世界中，无论是销售软件还是硬件，竞争格局、底层技术以及消费者需求和兴趣都可能随着时间的推移而迅速演变。人们可能需要考虑根据市场变化更新设计属性和预测模型。

## 附录 7.1：方程 (7.6) 和 (7.7) 中四组比较的功效计算和样本量确定的推导
假设决策规则为 `△p̂[1] − △p̂[2] > a`，其中 `a` 为某个常数，`^` 表示样本估计值。
`P(Type I error) = α = P(△p̂[1] − △p̂[2] > a | H0)`
$$~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ \\cong ~P\\left( {\\frac{\\left. \\left( \\bigtriangleup \\hat{p} \\right.\_{1}{- \\bigtriangleup \\hat{p}}\_{2} \\right) - 0}{I} > \\frac{a}{I}~~~~~} \\middle| H\_{0} \\right),$$
(A7.1)
其中
$$I = \\sqrt{\\frac{{\\hat{p}}\_{1t}\\left( 1 - {\\hat{p}}\_{1t} \\right)}{n\_{1t}} + \\frac{{\\hat{p}}\_{1c}\\left( 1 - {\\hat{p}}\_{1c} \\right)}{n\_{1c}} + \\frac{{\\hat{p}}\_{2t}\\left( 1 - {\\hat{p}}\_{2t} \\right)}{n\_{2t}} + \\frac{{\\hat{p}}\_{2c}\\left( 1 - {\\hat{p}}\_{2c} \\right)}{n\_{2c}}},$$
(A7.2)
它使用样本响应率近似 `△p̂[1] − △p̂[2]` 的标准差。
用 `zα` 表示 `a/I`，它与 `α` 相关的临界值。
第204页同样地，
`P(Type II error) = β = P(△p̂[1] − △p̂[2] ≤ a | H1)`
$$~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ \\cong ~P\\left( {\\frac{\\left. \\left( \\bigtriangleup \\hat{p} \\right.\_{1}{- \\bigtriangleup \\hat{p}}\_{2} \\right) - \\left( \\bigtriangleup p \\right.\_{1} - ~{\\bigtriangleup p}\_{2)}}{I} \\leq \\frac{a - \\left( \\bigtriangleup p \\right.\_{1} - ~{\\bigtriangleup p}\_{2)}}{I}~~} \\middle| {~H}\_{1} \\right).$$
(A7.3)
现在，用 `zβ` 表示 `a - (△p1 - △p2)/I`，它与 `β` 相关的临界值。
结合 (A7.1) 和 (A7.3)，我们有：
$$- z\_{\\beta} = z\_{\\alpha} - \\frac{\\left. \\left( \\bigtriangleup p \\right.\_{1} - ~{\\bigtriangleup p}\_{2} \\right)}{I}~~~~~~~~~~~~~~~~~~~~~~~~~~~~$$
(A7.4)
因此，
`Power = 1 − P(Type II Error)`
$$= 1 - Ф\\left( \\frac{\\left. a - \\left( \\bigtriangleup p \\right.\_{1} - ~{\\bigtriangleup p}\_{2} \\right)}{I} \\right)$$
$$= 1 - Ф\\left( {z\_{\\alpha} - \\frac{\\left( \\bigtriangleup p \\right.\_{1} - ~{\\bigtriangleup p}\_{2)}}{I}} \\right)~~~~from~\\left( {A7.4} \\right),~which~is~Eqn.~\\left( A7.3 \\right),$$
其中 (`△p[1]− △p[2]`) 由其样本估计值 (`△p̂[1] − △p̂[2]`) 估计。
再次，从方程 (A7.4) 可得，
(`zα+zβ`)² `I`² = (`△p[1]− △p[2]`)².
(A7.5)
为方便起见，我们定义以下比率，它们是样本设计的输入参数：
$$R\_{1} = \\frac{n\_{1t}}{n\_{1c}},~~~~R\_{2} = \\frac{n\_{2t}}{n\_{2c}},~~~~and~{~R}\_{t} = \\frac{n\_{1t}}{n\_{2t}}.$$
用上述定义的比率重新表示方程 (A7.2)：
$$I^{2} = \\frac{{\\hat{p}}\_{1t}\\left( {1 - {\\hat{p}}\_{1t}} \\right)~ + ~{\\hat{p}}\_{1c}\\left( {1 - {\\hat{p}}\_{1c}} \\right)R\_{1} + ~{\\hat{p}}\_{2t}\\left( {1 - {\\hat{p}}\_{2t}} \\right)R\_{t} + ~{\\hat{p}}\_{2c}\\left( {1 - {\\hat{p}}\_{2c}} \\right)~R\_{t}R\_{2}~~}{n\_{1t}} = \\frac{J}{n\_{1t}},$$
(A7.6)
第205页其中 `J` 定义为 `I²` 的分子，一旦比率（输入参数）确定即可轻松计算。将方程 (A7.6) 代入 (A7.5)，我们可以得到 `n1t` 如下：
$$n\_{1t} = \\frac{\\left. {J\\left( z \\right.}\_{\\alpha} + z\_{\\beta} \\right)^{2}}{\\left. \\left( \\bigtriangleup p \\right.\_{1} - ~{\\bigtriangleup p}\_{2} \\right)^{2}~},$$
我们也可以通过输入比率参数得到其他样本量：
$$n\_{1c} = \\frac{n\_{1t}}{R\_{1}},~~~{n\_{2t} = \\frac{n\_{1t}}{{~R}\_{t}},~~~~~and~~n}\_{2c} = \\frac{n\_{1t}}{{~R}\_{t}R\_{2}},$$
这与方程 (7.6) 相同。
接下来，我们将上述方程组 (7.6) 应用于确定对照组规模，使得最高十分位在统计上显著优于整体样本（如果存在这种差异）。在这种情况下，`△p[1]` 表示最高十分位的提升，`△p[2]` 表示其余十分位（即第 2–10 十分位）的提升。由于最高十分位占整体样本的 10%，根据方程 (A7.5)，我们现在有：
$$\\left( \\frac{{\\bigtriangleup p}\_{1} - ~{\\bigtriangleup p}\_{2}}{z\_{\\alpha} + z\_{\\beta}}~~ \\right)^{2} = \\frac{{\\hat{p}}\_{1t}\\left( 1 - {\\hat{p}}\_{1t} \\right)}{0.1n\_{t}} + \\frac{{\\hat{p}}\_{1c}\\left( 1 - {\\hat{p}}\_{1c} \\right)}{0.1n\_{c}} + \\frac{{\\hat{p}}\_{2t}\\left( 1 - {\\hat{p}}\_{2t} \\right)}{0.9n\_{t}} + \\frac{{\\hat{p}}\_{2c}\\left( 1 - {\\hat{p}}\_{2c} \\right)}{0.9n\_{c}}.$$
用 `nt` 和其他分量表示 `nc`，我们有：
$$n\_{c} = ~\\frac{\\frac{{\\hat{p}}\_{1c}\\left( 1 - {\\hat{p}}\_{1c} \\right)}{0.1}~ + ~\\frac{{\\hat{p}}\_{2c}\\left( 1 - {\\hat{p}}\_{2c} \\right)}{0.9}}{\\left( \\frac{{\\bigtriangleup p}\_{1} - ~{\\bigtriangleup p}\_{2}}{z\_{\\alpha} + z\_{\\beta}}~~ \\right)^{2} - \\frac{1}{n\_{t}}~\\left\\lbrack ~\\frac{{\\hat{p}}\_{1t}\\left( {1 - {\\hat{p}}\_{1t}} \\right)}{0.1} + \\frac{{\\hat{p}}\_{2t}\\left( {1 - {\\hat{p}}\_{2t}} \\right)}{0.9} \\right\\rbrack}$$
这就是方程 (7.7)。

## 注释
