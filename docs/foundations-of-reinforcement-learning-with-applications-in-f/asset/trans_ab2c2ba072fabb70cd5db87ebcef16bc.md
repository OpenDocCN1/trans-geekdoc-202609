

理解了马尔可夫决策过程的动态后，我们现在转向根据当前状态指定 `Agent` 的动作。在一般情况下，我们假设 Agent 将根据当前状态 `S[t]` 的函数所定义的概率分布执行随机动作 `A[t]`。我们将此函数称为 `Policy`（策略）。形式上，`Policy` 是一个函数

$$\\begin{array}{r} \\left. \\pi:\\mathcal{N} \\times \\mathcal{A}\\rightarrow\\lbrack 0,1\\rbrack \\right. \\\\ \\end{array}$$  

定义为：

$$\\begin{array}{r} {\\pi(s,a) = {\\mathbb{P}}\\lbrack A\_{t} = a|S\_{t} = s\\rbrack\\text{~for~time~steps~}t = 0,1,2,\\ldots,\\text{~for~all~}s \\in \\mathcal{N},a \\in \\mathcal{A}} \\\\ \\end{array}$$  

使得：

$$\\begin{array}{r} {{\\sum\\limits\_{a \\in \\mathcal{A}}\\pi}(s,a) = 1\\text{~for~all~}s \\in \\mathcal{N}} \\\\ \\end{array}$$  

请注意，上述定义假设 Policy 是马尔可夫的，即动作概率仅取决于当前状态而不取决于历史。上述定义还假设 Policy 是 `Stationary`（静态的），即 ℙ\[`A[t]` = `a`|`S[t]` = `s`\] 在时间 `t` 上不变。如果我们确实遇到策略需要依赖于时间 `t` 的情况，我们只需将 `t` 包含为状态的一部分，这将使 Policy 变为静态（尽管代价是状态空间膨胀，从而增加计算成本）。

当我们拥有一个策略，使得每个状态的动作概率分布集中在单一动作上时，我们称其为确定性策略。形式上，确定性策略 `π[D]`:𝒩→𝒜 具有以下性质：对于所有 `s` ∈ 𝒩，

$$\\begin{array}{r} {\\pi(s,\\pi\_{D}(s)) = 1\\text{~and~}\\pi(s,a) = 0\\text{~for~all~}a \\in \\mathcal{A}\\text{~with~}a \\neq \\pi\_{D}(s)} \\\\ \\end{array}$$  

因此，我们将确定性策略简单地表示为函数 `π[D]`。我们将非确定性策略称为随机策略（stochastic 一词反映了 Agent 将根据由 `π` 指定的概率分布执行随机动作这一事实）。因此，当我们使用符号 `π` 时，假设我们处理的是随机（即非确定性）策略；当我们使用符号 `π[D]` 时，假设我们处理的是确定性策略。

让我们编写一些代码来掌握 Policy 的概念。我们从设计一个名为 `Policy` 的抽象类开始，它代表一个通用的 Policy，正如我们上面所阐述的那样。它包含的唯一方法是一个抽象方法 `act`，它接受状态作为输入：`NonTerminal[S]`（如前所述，在类 `MarkovProcess` 和 `MarkovRewardProcess` 中，`S` 是表示通用状态空间的泛型类型），并输出一个 `Distribution[A]`，表示随机动作作为输入非终端状态的函数的概率分布。请注意，`A` 表示表示通用动作空间的泛型类型。

![](images/comp04_1.jpg)

接下来，我们实现一个用于确定性策略的类。

![](images/comp04_2.jpg)

我们经常会遇到从每个非终端状态向所有动作分配相等概率的策略。我们按如下方式实现此类策略：

![](images/comp04_3.jpg)

上述代码位于文件 `rl/policy.py` 中。

现在让我们编写一些代码，为我们熟悉的示例——简单库存示例创建一些具体策略。我们首先创建一个具体类 `SimpleInventoryDeterministicPolicy`，用于确定性库存补货策略，它是 `DeterministicPolicy` 的派生类。请注意，泛型状态类型 `S` 在这里被类 `InventoryState` 替换，该类表示库存示例中的一个状态，包含 On-Hand 和 On-Order 库存数量。还要注意，泛型动作类型 `A` 在这里被 `int` 类型替换，因为在这个示例中，动作是在店铺关闭时要订购的库存数量（这是一个整数数量）。调用 `SimpleInventoryDeterministicPolicy` 的 `act` 方法将运行以下确定性策略：

$$\\begin{array}{r} {\\pi\_{D}((\\alpha,\\beta)) = \\max(r - (\\alpha + \\beta),0)} \\\\ \\end{array}$$  

其中 `r` 是一个参数，表示“再订货点”（即，只有当库存位置低于“再订货点”时才订货），`α` 是店铺关闭时的 On-Hand 库存，`β` 是店铺关闭时的 On-Order 库存，库存位置等于 `α` + `β`。在 [第 3 章](#chapter3.xhtml) 中，我们将再订货点设置为等于店铺容量 `C`。

![](images/comp04_4.jpg)

我们可以实例化一个特定的确定性策略，再订货点为 8：

![](images/comp04_5.jpg)

现在让我们编写一些代码，为库存示例创建随机策略。我们创建一个具体类 `SimpleInventoryStochasticPolicy`，它实现抽象类 `Policy` 的接口（具体实现抽象方法 `act`）。`act` 中的代码将随机策略实现为由泊松分布采样驱动的 `SampledDistribution[int]`。具体来说，再订货点 `r` 被视为具有指定均值（例如 `λ` ∈ ℝ[ ≥ 0]）的泊松随机变量。我们从该泊松分布（均值为 `λ`）中采样一个再订货点 `r` 的值。然后，我们创建一个样本订货数量（动作）`θ` ∈ ℤ[ ≥ 0]，定义为：

$$\\begin{array}{r} {\\theta = \\max(r - (\\alpha + \\beta),0)} \\\\ \\end{array}$$  

![](images/comp04_6.jpg)

我们可以实例化一个特定的随机策略，再订货点泊松分布均值为 8.0：

![](images/comp04_7.jpg)

在介绍完马尔可夫决策过程的代码后，我们将稍后再次回到简单库存示例，届时我们将展示如何模拟该简单库存示例的马尔可夫决策过程，其中 Agent 运行确定性策略。但在转向马尔可夫决策过程的代码设计（以配合上述 Policy 实现）之前，我们需要介绍一个重要的洞察，即连接马尔可夫决策过程、策略和马尔可夫奖励过程。

## 4.5 [MARKOV DECISION PROCESS, POLICY]: = MARKOV REWARD PROCESS

本节有一个重要的洞察——如果我们用固定策略 `π`（通常是固定随机策略 `π`）来评估马尔可夫决策过程（MDP），我们将得到由 MDP 和策略 `π` 的组合所 *隐含* 的马尔可夫奖励过程（MRP）。让我们用符号精确性来澄清这一点。但首先，我们需要指出 MDP 和 MRP 之间存在一些符号冲突。我们使用 `𝒫[R]` 来表示 MRP 的转移概率函数，也用于表示 MDP 的状态-奖励转移概率函数。我们使用 `𝒫` 来表示 MRP 中隐含的马尔可夫过程的转移概率函数，也用于表示 MDP 的状态转移概率函数。我们使用 `ℛ[T]` 来表示 MRP 的奖励转移函数，也用于表示 MDP 的奖励转移函数。我们使用 `ℛ` 来表示 MRP 的奖励函数，也用于表示 MDP 的奖励函数。我们可以通过注意 `𝒫[R]`、`𝒫`、`ℛ[T]` 和 `ℛ` 的参数来解决这些符号冲突，但为了更加清晰，我们将为 `π`-隐含 MRP 的每个函数 `𝒫[R]`、`𝒫`、`ℛ[T]` 和 `ℛ` 加上上标 `π`，以区分 MDP 与 `π`-隐含 MRP 中的这些函数。

假设我们有一个固定策略 `π` 和一个由其状态-奖励转移概率函数 `𝒫[R]` 指定的 MDP。那么，由用策略 `π` 评估 MDP 所得到的 MRP 的转移概率函数 `𝒫[R]^π` 定义为：

$$\\begin{array}{r} {\\mathcal{P}\_{R}^{\\pi}(s,r,s^{\\prime}) = {\\sum\\limits\_{a \\in \\mathcal{A}}\\pi}(s,a) \\cdot \\mathcal{P}\_{R}(s,a,r,s^{\\prime})} \\\\ \\end{array}$$  

同样，

