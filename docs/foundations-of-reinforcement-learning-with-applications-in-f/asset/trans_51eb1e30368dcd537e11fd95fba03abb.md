

现在让我们进一步发展一些理论。给定 `𝒫[*R*]` 的规范，我们可以提取：

*   隐式马尔可夫过程的转移概率函数 `𝒫:𝒩×𝒮→[0,1]`，定义为：

    $$\\begin{array}{r} {\\mathcal{P}(s,s^{\\prime}) = {\\sum\\limits\_{r \\in \\mathcal{D}}\\mathcal{P}\_{R}}(s,r,s^{\\prime})} \\\\ \\end{array}$$  

*   奖励转移函数：

    $$\\begin{array}{r} \\left. \\mathcal{R}\_{T}:\\mathcal{N} \\times \\mathcal{S}\\rightarrow{\\mathbb{R}} \\right. \\\\ \\end{array}$$  

    定义为：

    $$\\begin{array}{r} {\\mathcal{R}\_{T}(s,s^{\\prime}) = \\mathbb{E}\\lbrack R\_{t + 1}|S\_{t + 1} = s^{\\prime},S\_{t} = s\\rbrack = {\\sum\\limits\_{r \\in \\mathcal{D}}\\frac{\\mathcal{P}\_{R}(s,r,s^{\\prime})}{\\mathcal{P}(s,s^{\\prime})}} \\cdot r = {\\sum\\limits\_{r \\in \\mathcal{D}}\\frac{\\mathcal{P}\_{R}(s,r,s^{\\prime})}{{\\sum\\limits\_{r \\in \\mathcal{D}}\\mathcal{P}\_{R}}(s,r,s^{\\prime})}} \\cdot r} \\\\ \\end{array}$$  

我们在实践中遇到的大多数马尔可夫奖励过程的奖励规范可以直接表示为奖励转移函数 `ℛ[*T*]`（与更通用的 `𝒫[*R*]` 规范相对）。最后，我们想强调，我们可以将 `𝒫[*R*]` 或 `ℛ[*T*]` 中的任意一个转换为一个“更紧凑”的奖励函数，该函数足以执行涉及马尔可夫奖励过程的关键计算。这个奖励函数

$$\\begin{array}{r} \\left. \\mathcal{R}:\\mathcal{N}\\rightarrow{\\mathbb{R}} \\right. \\\\ \\end{array}$$  

定义为：

$$\\begin{array}{r} {\\mathcal{R}(s) = \\mathbb{E}\\lbrack R\_{t + 1}|S\_{t} = s\\rbrack = {\\sum\\limits\_{s^{\\prime} \\in \\mathcal{S}}\\mathcal{P}}(s,s^{\\prime}) \\cdot \\mathcal{R}\_{T}(s,s^{\\prime}) = {\\sum\\limits\_{s^{\\prime} \\in \\mathcal{S}}{\\sum\\limits\_{r \\in \\mathcal{D}}\\mathcal{P}\_{R}}}(s,r,s^{\\prime}) \\cdot r} \\\\ \\end{array}$$  

我们在这里制造了一点符号混乱。因此，建议你花几分钟时间暂停、反思并内化 `𝒫[*R*]`、`𝒫`（隐式马尔可夫过程的）、`ℛ[*T*]` 和 `ℛ` 之间的区别。当我们在第 4 章中学习马尔可夫决策过程时，这种记号将类似地再次出现，详见 [第 4 章](#chapter4.xhtml)。此外，本书余下部分将大量使用此记号，因此熟悉其语义是有益的。

## 3.9 作为马尔可夫奖励过程的简单库存示例

现在我们回到简单库存示例，并为其添加奖励结构，将其转变为马尔可夫奖励过程（业务成本将被建模为负奖励）。假设你的商店业务会产生两种类型的成本：

*   每辆留在商店过夜的自行车的持有成本 `h`。可以将其视为“库存利息”——每天你的自行车未售出，你就失去了为购买自行车所支付的现金赚取利息的机会。持有成本还包括库存维护成本。

*   每单位“未满足需求”的缺货成本 `p`，即每位想要购买自行车但你无法用现有库存满足的客户，例如，如果白天有 3 位客户想要各买一辆自行车，而你在早上 8 点（商店开门时间）只有 1 辆自行车，那么你就损失了两单位的需求，产生 `2*p` 的成本。可以将每单位 `p` 的成本视为损失的收入加上客户的失望情绪。通常 `p ≫ h`。

让我们逐一梳理每个 24 小时周期中事件的精确顺序，现在加入奖励：

*   在下午 6 点商店关门时观察 `(α, β)` `State`（将此状态称为 `S[t]`）。

*   立即根据给定的订购政策进行订购：订购数量 `= max(C − (α + β), 0)`。

*   记录上述产生的任何过夜持有成本。

*   如果你 36 小时前订购了自行车，则在早上 6 点收到自行车。

*   早上 8 点开门营业。

*   根据指定的泊松概率经历客户的随机需求（泊松均值 `= λ`）。

*   记录上述因未满足需求产生的任何缺货成本。

*   下午 6 点关门，将奖励 `R[t + 1]` 记录为过夜持有成本和当天缺货成本的负之和，并观察状态（此状态为 `S[t + 1]`）。

由于任何一天的客户需求都可能是无限多种可能性（非负整数全范围上的泊松分布），从给定的当前状态我们可以转移到的下一个状态和奖励的对是无限的。让我们看看这些转移的概率是什么样子。对于给定的当前状态 `S[t] := (α, β)`，如果当天的客户需求为 `i`，那么下一个状态 `S[t + 1]` 为：

$$\\begin{array}{r} {(\\max(\\alpha + \\beta - i,0),\\max(C - (\\alpha + \\beta),0))} \\\\ \\end{array}$$  

奖励 `R[t + 1]` 为：

$$\\begin{array}{r} {- h \\cdot \\alpha - p \\cdot \\max(i - (\\alpha + \\beta),0)} \\\\ \\end{array}$$  

请注意，过夜持有成本适用于商店关门时的每单位现有库存（`= α`），而缺货成本仅适用于任何单位的“未满足需求”（`= max(i − (α + β), 0)`）。由于两个不同的需求值 `i ∈ ℤ[ ≥ 0]` 不会在任何唯一的 `(s′ , r)` 下一个状态和奖励对上发生冲突，我们可以将此简单库存示例作为马尔可夫奖励过程的转移概率函数 `𝒫[*R*]` 表示为：

$$\\begin{array}{r} {\\mathcal{P}\_{R}((\\alpha,\\beta), - h \\cdot \\alpha - p \\cdot \\max(i - (\\alpha + \\beta),0),(\\max(\\alpha + \\beta - i,0),\\max(C - (\\alpha + \\beta),0)))} \\\\ \\end{array}$$  

$$\\begin{array}{r} {= \\frac{e^{- \\lambda}\\lambda^{i}}{i!}\\text{~for~all~}i = 0,1,2,\\ldots} \\\\ \\end{array}$$  

现在让我们编写一些代码，按照上述描述实现这个简单库存示例作为马尔可夫奖励过程。我们所要做的就是创建一个实现抽象类 `MarkovRewardProcess` 接口的具体类（具体实现抽象方法 `transition_reward`）。下面 `SimpleInventoryMRP` 类中 `transition_reward` 方法的代码从泊松分布中采样客户需求，使用上述公式将客户需求样本作为函数计算下一个状态和奖励的对，并返回 `SampledDistribution` 的实例。请注意，泛型状态类型 `S` 在这里被 `@dataclass` `InventoryState` 替换，用于表示此马尔可夫奖励过程的状态，包含现有库存和在途库存数量。

![](images/comp03_22.jpg)

上述代码可在文件 `rl/chapter2/simple_inventory_mrp.py` 中找到。我们将使用 `SimpleInventoryMRP` 继承的 `simulate_reward` 方法进行模拟并分析采样轨迹产生的统计数据作为练习留给你。

## 3.10 有限马尔可夫奖励过程

如果满足以下条件，马尔可夫奖励过程的某些计算可以轻松执行：

*   状态空间是有限的（`𝒮 = {s[1],s[2],…,s[n]}`），并且

*   来自 `𝒩` 中每个状态的下一个状态和奖励转移的唯一对集合是有限的

如果满足上述两个特征，我们将马尔可夫奖励过程称为有限马尔可夫奖励过程。那么让我们为有限马尔可夫奖励过程编写一些代码。我们创建一个具体类 `FiniteMarkovRewardProcess`，它主要继承自 `FiniteMarkovProcess`（一个具体类），并次要实现抽象类 `MarkovRewardProcess` 的接口。我们的第一项任务是思考指定 `FiniteMarkovRewardProcess` 实例所需的数据结构（即我们将传递给 `FiniteMarkovRewardProcess` 的 `__init__` 方法的数据结构）。类似于我们如何将马尔可夫过程的 `𝒫` 柯里化为 `𝒩→(𝒮→[0,1])`（其中 `𝒮 = {s[1],s[2],…,s[n]}` 且 `𝒩` 有 `m ≤ n` 个状态），这里我们将 `𝒫[*R*]` 柯里化为：

