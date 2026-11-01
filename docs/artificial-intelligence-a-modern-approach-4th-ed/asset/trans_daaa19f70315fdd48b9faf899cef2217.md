
图13.19 拒绝采样和似然加权在保险网络上的性能。x轴显示生成的样本数量，y轴显示查询 `PropertyCost` 的概率值中最大绝对误差。

## 13.4.2 马尔可夫链模拟推理

马尔可夫链蒙特卡罗（`MCMC`）算法的工作方式与拒绝采样和似然加权不同。不是从头生成每个样本，`MCMC` 算法通过对前一个样本进行随机更改来生成样本。可以将 `MCMC` 算法视为处于特定当前状态，该状态为每个变量指定一个值，并通过对当前状态进行随机更改来生成下一个状态。

马尔可夫链蒙特卡罗

术语马尔可夫链指的是生成状态序列的随机过程。（马尔可夫链也在[第14章](#Chapter14-00.xhtml)和[第16章](#Chapter16-00.xhtml)中占据重要地位；[第4章](#Chapter04-00.xhtml)中的模拟退火算法和[第7章](#Chapter07-00.xhtml)中的WALK SAT算法也是`MCMC`家族的成员。）我们首先描述一种称为吉布斯采样（Gibbs sampling）的特定形式的`MCMC`，它特别适合贝叶斯网络。然后我们描述更一般的Metropolis–Hastings算法，该算法在生成样本方面允许更大的灵活性。

马尔可夫链 吉布斯采样 Metropolis–Hastings

## 贝叶斯网络中的吉布斯采样

贝叶斯网络的吉布斯采样算法从任意状态开始（证据变量固定在其观测值），并通过随机采样一个非证据变量 `Xi` 的值来生成下一个状态。回想一下[第437页](#Chapter13-02.xhtml#page_437)中所述，`Xi` 在其马尔可夫毯（其父节点、子节点和子节点的其他父节点）给定条件下与所有其他变量独立；因此，`Xi` 的吉布斯采样意味着在马尔可夫毯中变量的当前值条件下进行采样。算法在状态空间中随机游走——可能的完整赋值空间——一次翻转一个变量，但保持证据变量固定。完整算法显示在[图13.20](#Chapter13-04.xhtml#fig13-20)。

![](images/Fig-187.jpg)

图13.20 贝叶斯网络近似推理的吉布斯采样算法；此版本随机选择变量，但循环遍历变量也同样有效。

考虑网络中查询 `P(Rain | Sprinkler = true, WetGrass = true)`，该网络在[图13.15(a)](#Chapter13-03.xhtml#fig13-15)。证据变量 `Sprinkler` 和 `WetGrass` 固定在其观测值（均为真），而非证据变量 `Cloudy` 和 `Rain` 随机初始化为，例如，分别真和假。因此，初始状态为 [true, true, false, true]，其中我们用粗体标记了固定的证据值。现在非证据变量 `Zi` 根据选择变量的概率分布 `ρ(i)` 在某种随机顺序中重复采样。例如：
1. `Cloudy` 被选中然后采样，给定其马尔可夫毯的当前值：在这种情况下，我们从 `P(Cloudy | Sprinkler = true, Rain = false)` 采样。假设结果为 `Cloudy = false`。那么新的当前状态为 [false, true, false, true]。
2. `Rain` 被选中然后采样，给定其马尔可夫毯的当前值：在这种情况下，我们从 `P(Rain | Cloudy = false, Sprinkler = true, WetGrass = true)` 采样。假设这产生 `Rain = true`。新的当前状态为 [false, true, true, true]。

剩下的一个细节涉及马尔可夫毯分布 `P(Xi | mb(Xi))` 的计算方法，其中 `mb(Xi)` 表示 `Xi` 的马尔可夫毯 `MB(Xi)` 中变量的值。幸运的是，这不涉及任何复杂推理。如练习13.MARB所示，分布由下式给出
$\\begin{matrix} \\left. P\\text{(}x\_{i} \\middle| mb\\text{(}X\_{i}\\text{))~=}\\alpha\\ P\\text{(}x\_{i} \\middle| parents\\text{(}X\_{i}\\text{))}{\\prod\\limits\_{Y\_{j} \\in Children(X\_{i})}\\left. P\\text{(}y\_{j} \\middle| parents\\text{(}Y\_{j}\\text{))~}\\text{.} \\right.} \\right. & {\\text{(13}\\text{.10)}} \\\\ \\end{matrix}$

换句话说，对于每个值 `x_i`，概率是通过将 `Xi` 及其子节点的CPT中的概率相乘得到的。例如，在上面显示的第一次采样步骤中，我们从 `P(Cloudy | Sprinkler = true, Rain = false)` 采样。根据[公式(13.10)](#Chapter13-04.xhtml#eq13-10)，并缩写变量名，我们有
$\\begin{matrix} \\left. P(c \\middle| s,\\neg r)\\ = \\alpha\\ P(c)P(s \\middle| c)P(\\neg r \\middle| c)\\ = \\alpha\\ 0.5\\ \\text{·}\\ 0.1\\ \\text{·}\\ 0.2 \\right. \\\\ \\left. P(\\neg c \\middle| s,\\neg r)\\ = \\ P(\\neg c)P(s \\middle| \\neg c)P(\\neg r \\middle| \\neg c)\\ = \\alpha\\ 0.5\\ \\text{·}\\ 0.5\\ \\text{·}\\ 0.8, \\right. \\\\ \\end{matrix}$
因此采样分布为 α〈0.001,0.020〉 ≈ 〈0.048,0.952〉。

[图13.21(a)](#Chapter13-04.xhtml#fig13-21) 显示了变量均匀选择的情况，即 `ρ(Cloudy) = ρ(Rain) = 0.5` 时的完整马尔可夫链。算法只是在此图中游走，遵循所声明概率的链接。此过程中访问的每个状态都是对查询变量 `Rain` 的估计有贡献的样本。如果过程访问 `Rain` 为真的20个状态和 `Rain` 为假的60个状态，则查询的答案为 `NORMALIZE(〈20, 60〉) = 〈0.25,0.75〉`。

描述
在两部分中，不同的状态均由四个矩形块表示。块的标签为 `c r`、`c not r`、`not c r` 和 `not c not r`。部分（“a”）：从 `c r` 指向自身的标签为0.6296的循环。标签为0.0926的箭头从 `c r` 指向 `c not r`。标签为0.4074的箭头从 `c not r` 指向 `c r`。从 `c not r` 指向自身的标签为0.1164的循环。标签为0.2778的箭头从 `c r` 指向 `not c r`。标签为0.2222的箭头从 `not c r` 指向 `c r`。从 `not c r` 指向自身的标签为0.3856的循环。标签为0.3922的箭头从 `not c r` 指向 `not c not r`。标签为0.1078的箭头从 `not c not r` 指向 `not c r`。从 `not c not r` 指向自身的标签为0.8683的循环。标签为0.0238的箭头从 `not c not r` 指向 `c not r`。标签为0.4762的箭头从 `c not r` 指向 `not c not r`。部分(b)：从 `c r` 指向自身的标签为1.0000的循环。标签为0.0000的箭头从 `c r` 指向 `c not r`。标签为0.5000的箭头从 `c not r` 指向 `c r`。从 `c not r` 指向自身的标签为0.0000的循环。标签为0.0000的箭头从 `c r` 指向 `not c r`。标签为0.5000的箭头从 `not c r` 指向 `c r`。从 `not c r` 指向自身的标签为0.0000的循环。标签为0.5000的箭头从 `not c r` 指向 `not c not r`。标签为0.0000的箭头从 `not c not r` 指向 `not c r`。从 `not c not r` 指向自身的标签为1.0000的循环。标签为0.0000的箭头从 `not c not r` 指向 `c not r`。标签为0.5000的箭头从 `c not r` 指向 `not c not r`。

![](images/Fig-188.jpg)

图13.21(a) 查询 `P(Rain | Sprinkler = true, WetGrass = true)` 的马尔可夫链的状态和转移概率。注意自环：当选择任一变量然后重新采样其已有的相同值时，状态保持不变。(b) 当 `Rain` 的CPT约束其具有与 `Cloudy` 相同的值时的转移概率。

## 马尔可夫链的分析

我们说过吉布斯采样通过在状态空间中随机游走来生成样本。为了解释为什么吉布斯采样能正确工作——即为什么其估计在极限情况下收敛到正确值——我们需要进行一些细致的分析。（本节有些数学性，首次阅读时可以跳过。）
