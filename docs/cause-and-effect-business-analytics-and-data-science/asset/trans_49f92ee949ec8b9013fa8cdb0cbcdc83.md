
### 4. R-学习者
该方法采用交叉验证，并在调整结果模型和倾向得分模型后使用特定的损失函数进行最小化，详情请参阅 `Nie and Wagner (2021)`。

### 5. 双重稳健 (DR) 学习者
该方法同时估计倾向得分和结果模型，只要其中至少一个正确即可有效。该方法是对估计平均处理效应的 DR 方法的扩展，在数据为观察性数据（即非实验性）时特别有用，详情请参阅 [Kennedy (2023)](#chapter9.xhtml#ref9_21)。

## 附录 9.1：四象限方法的证明——通过添加概率权重修改 Lai 方法
考虑 [图 9.1](#chapter9.xhtml#fig9_1b) 中的 2 × 2 表格。将我们的估计目标（即提升）定义为协变量 `x` 的函数：
`Z(x)` ≡ `P(R|T,x)` – `P(R|C,x)`，其中 `R` = 响应的事件。`Z(x)` 是在给定一组特征 `x` 的情况下，处理组与对照组之间的响应概率差异（提升）。它可以重新表达如下。
`Z(x)` = `P(R|T,x)`− (1−`P(N|C,x)`)，其中 `N` = 无响应
= `P(R|T,x)`+ `P(N|C,x)` − 1
$$= \\frac{P\\left( {TR} \\middle| x \\right)}{P\\left( T \\middle| x \\right)} + \\frac{P\\left( {CN} \\middle| x \\right)}{P\\left( C \\middle| x \\right)} - 1,~by~Bayes^{'}rule$$
$$= \\frac{P\\left( {TR} \\middle| x \\right)}{P\\left( T \\right)} + \\frac{P\\left( {CN} \\middle| x \\right)}{P\\left( C \\right)} - 1,$$
(A9.1)
第 280 页由于处理和对照的随机化，即处理/对照的分配是随机的且不依赖于 `x`。请注意，式 (A9.1) 表明 `P(TR|x)` 和 `P(CN|x)` 对提升有正向贡献。
同样，如果我们以另一种方式来看 `Z(x)`，
`Z(x)` = (1−`P(N|T,x)`) − `P(R|C,x)`
$$= 1 - \\frac{P\\left( {TN} \\middle| x \\right)}{P\\left( T \\right)} - \\frac{P\\left( {CR} \\middle| x \\right)}{P\\left( C \\right)},$$
(A9.2)
其中式 (A9.2) 表明 `P(TN|x)` 和 `P(CR|x)` 对提升有负向贡献。
请注意式 (A9.1) 和 (A9.2) 是相同的方程，只是表达方式不同。将式 (A9.1) 和 (A9.2) 相加，我们得到：
$$2Z\\left( x \\right) = \\frac{P\\left( {TR} \\middle| x \\right)}{P\\left( T \\right)} + \\frac{P\\left( {CN} \\middle| x \\right)}{P\\left( C \\right)} - \\frac{P\\left( {TN} \\middle| x \\right)}{P\\left( T \\right)} - \\frac{P\\left( {CR} \\middle| x \\right)}{P\\left( C \\right)},or~$$
$$\\frac{~P\\left( C \\right)\\left( P\\left( {TR} \\middle| x \\right) - P\\left( {TN} \\middle| x \\right) \\right) + P\\left( T \\right)\\left( {P\\left( {CN} \\middle| x \\right) - P\\left( {CR} \\middle| x \\right)} \\right)}{P\\left( T \\right)P\\left( C \\right)}~$$
(A9.3)
通常情况下，市场营销项目的处理组样本量大于对照组；即 `P(C)` < `P(T)`，因为营销人员通常希望通过联系更多个人来获得更多收入。可以很容易地证明 [Lai (2006)](#chapter9.xhtml#ref9_23) 的方法是一种特殊情况，其中 `P(T)` = `P(C)` = 0.5，这在一般情况下在数学上是不正确的。然而，[Lai (2006)](#chapter9.xhtml#ref9_23) 也提出了基于经验发现的权重，但事实上，如式 (A9.3) 所示，存在一个简单的数学方程。请注意，尽管该方法与方法 A1 和 A2 具有相同的数学目标，即最大化 `P(R|T)` – `P(R|C)`，但由于估计方法不同，经验上会导致不同的估计结果。

## 附录 9.2：非随机化数据的加权基尼系数和加权前 15% 基尼系数的计算
本附录是对 [附录 6.1](#chapter6.xhtml#app6_1) 的推广，即将随机化数据扩展到非随机化数据情况，其中可用于调整的权重可用。如 [附录 6.1](#chapter6.xhtml#app6_1) 中所述，假设我们按半十分位对 `holdout` 样本 第 281 页 进行排序，即 20 个组，每组 5%。将第 `j` 组的平均提升定义为：
`lift(j)` = `P(R|T,j)` − `P(R|C,j)`，
其中 `P(R|T,j)` 和 `P(R|C,j)` 分别表示处理组和对照组中半十分位子组 `j` 中的响应概率，可通过 `holdout` 样本中响应的相对频率来估计。然后，
$$Weighted~Gini~coefficient = {\\sum\\limits\_{g = 1}^{20}\\left( {\\text{cum}\\%\\text{lift}\\left( g \\right) - \\text{cum}\\%\\text{sam}\\left( g \\right)} \\right)},$$
其中
`cum%lift(g)` = 累计提升百分比 直到半十分位组 `g`
$$= ~\\frac{\\overset{-}{lift}\\left( 1,\\ldots,g \\right){\\sum\\limits\_{j = 1}^{g}{\\sum\_{i}w\_{tji}}}}{\\overset{-}{lift}{\\sum\\limits\_{j = 1}^{20}{\\sum\_{i}w\_{tji}}}}~ = ~\\frac{\\overset{-}{lift}\\left( 1,\\ldots,g \\right){\\sum\\limits\_{j = 1}^{g}w\_{tj}}}{\\overset{-}{lift}{\\sum\\limits\_{j = 1}^{20}w\_{tj}}},$$
其中
$$\\overset{-}{lift} = overall~weighted~lift~\\left( of~all~20~semi - deciles \\right)$$
$$= \\frac{\\sum\\limits\_{j = 1}^{20}\\left( {\\sum\_{i}{\\left. w\_{tji} \\right)~{\\overset{-}{y}}\_{tj}~}} \\right.}{\\sum\\limits\_{j = 1}^{20}{\\sum\_{i}w\_{tji}}} - \\frac{\\sum\\limits\_{j = 1}^{20}\\left( {\\sum\_{i}{\\left. w\_{cji} \\right)~{\\overset{-}{y}}\_{cj}~}} \\right.}{\\sum\\limits\_{j = 1}^{20}{\\sum\_{i}w\_{cji}}},$$
并且
`lift(1,…,g)` = 来自半十分位 1,…, `g` 的加权提升，（其中 `g` = 1,…, 20）
$$= ~\\frac{\\sum\\limits\_{j = 1}^{g}\\left( {\\sum\_{i}{\\left. w\_{tji} \\right)~{\\overset{-}{y}}\_{tj}~}} \\right.}{\\sum\\limits\_{j = 1}^{g}{\\sum\_{i}w\_{tji}}} - \\frac{\\sum\\limits\_{j = 1}^{g}\\left( {\\sum\_{i}{\\left. w\_{cji} \\right)~{\\overset{-}{y}}\_{cj}~}} \\right.}{\\sum\\limits\_{j = 1}^{g}{\\sum\_{i}w\_{cji}}}$$
$$= \\frac{\\sum\\limits\_{j = 1}^{g}{w\_{tj}~{\\overset{-}{y}}\_{tj}}}{\\sum\\limits\_{j = 1}^{g}w\_{tj}} - \\frac{\\sum\\limits\_{j = 1}^{g}{w\_{cj}~{\\overset{-}{y}}\_{cj}}}{\\sum\\limits\_{j = 1}^{g}w\_{cj}},$$
并且 `w[tji]` = 与 `holdout` 样本中处理组、半十分位 `j` 和个体 `i` 相关的权重；同样，`w[cji]` = 与 第 282 页 对照组、半十分位 `j` 和个体 `i` 在 `holdout` 样本中相关的权重。此外，`$w_{tj} = {\sum\limits_{i}{w_{tji}~}}$`和 `$w_{cj} = {\sum\limits_{i}w_{cji}}$`，分别表示处理组和对照组在半十分位 `j` 处的总权重。进一步，
`cum%sam(g)` = 累计样本百分比 直到半十分位组 `g`
$$= ~\\frac{\\sum\\limits\_{j = 1}^{g}{\\sum\_{i}w\_{tji}}}{\\sum\\limits\_{j = 1}^{20}{\\sum\_{i}w\_{tji}}} = ~\\frac{\\sum\\limits\_{j = 1}^{g}w\_{tj}}{\\sum\\limits\_{j = 1}^{20}w\_{tj}}~.$$
同样，加权前 15% 基尼系数仅关注加权基尼系数公式中的前 15%，即前 3 个半十分位：
$$Weighted~Top~15\\%~Gini = ~{\\sum\\limits\_{g = 1}^{3}\\left( {cum\\% lift\\left( g \\right) - cum\\% pop\\left( g \\right)} \\right)}.$$

## 附录 9.3：非随机化数据的倾向得分加权的证明
将 `Y[1]` 和 `Y[0]` 定义为处理和对照（未处理）的潜在结果。实际上，对于个人而言，这两者中只有一个是可观察的。可以使用 `IPW` 方法计算整个总体的 `ATE`、接受治疗者的平均处理效应 (`ATT`) 或对照者的平均处理效应 (`ATC`)。下面我们将使用 `ATC` 进行说明。
`ATC` 定义为：
`ATC` = `E(Y[1]|T=0)` − `E(Y[0]|T=0)`
