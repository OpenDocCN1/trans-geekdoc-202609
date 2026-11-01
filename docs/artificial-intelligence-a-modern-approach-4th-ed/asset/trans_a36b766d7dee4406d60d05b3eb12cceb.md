
# 贝叶斯网络

## 13.1 贝叶斯网络示例

箭头从标记为 `Burglary` 和 `Earthquake` 的节点指向标记为 `Alarm` 的节点。箭头从 `Alarm` 节点指向标记为 `John Calls` 和 `Mary Calls` 的节点。每个节点旁边都显示了概率表。概率表如下。`Burglary`：表由两行组成。行条目为：第 1 行：`P(B equals true)`。第 2 行：0.001。`Earthquake`：表由两行组成。行条目为：第 1 行：`P(E equals true)`。第 2 行：0.002。`Alarm`：表由两列和四行组成。列标题如下：列 1，`B`。列 2，`E`。列 3，`P("A" equals true given B, E)`。行条目如下。第 1 行：列 1，t。列 2，t。列 3，0.70。第 2 行：列 1，t。列 2，f。列 3，0.01。第 3 行：列 1，f。列 2，t。列 3，0.70。第 4 行：列 1，f。列 2，f。列 3，0.01。`John Calls`：表由两列和两行组成。列标题为：列 1，`"A"`。列 2，`P(J equals true given "A")`。行条目如下。第 1 行：列 1，t。列 2，0.90。第 2 行：列 1，f。列 2，0.05。`Mary Calls`：表由两列和两行组成。列标题为列 1，`"A"`。列 2，`P(M equals true given "A")`。行条目如下。第 1 行：列 1，t。列 2，0.70。第 2 行：列 1，f。列 2，0.01。

×![](images/Fig-169.jpg)

图 13.2 一个典型的贝叶斯网络，显示了拓扑结构和条件概率表（CPT）。在 CPT 中，字母 `B`、`E`、`A`、`J` 和 `M` 分别代表 `Burglary`、`Earthquake`、`Alarm`、`JohnCalls` 和 `MaryCalls`。

附加在 [图 13.2](#Chapter13-01.xhtml#fig13-2) 中每个节点的局部概率信息以条件概率表（`CPT`）的形式出现。（`CPT` 只能用于离散变量；其他表示，包括适用于连续变量的表示，描述于 [第 13.2 节](#Chapter13-02.xhtml#sec13-2) 中。）`CPT` 中的每一行都包含一个条件案例下每个节点值的条件概率。条件案例只是父节点值的可能组合——如果愿意，可以看作一个微型可能世界。每一行必须总和为 1，因为条目代表变量的穷尽情况集合。对于布尔变量，一旦知道真值的概率为 p，假值的概率必须为 1 – p，因此我们经常省略第二个数字，如 [图 13.2](#Chapter13-01.xhtml#fig13-2) 所示。一般来说，一个具有 k 个布尔父节点的布尔变量的表包含 2^k 个可独立指定的概率。没有父节点的节点只有一行，表示变量每个可能值的先验概率。

<p class="sidebar">条件概率表 (CPT)</p> <p class="sidebar">条件案例</p>

请注意，网络没有对应于 Mary 目前正在听大声音乐或电话铃声并让 John 困惑的节点。这些因素被概括为 `Alarm` 到 `JohnCalls` 和 `MaryCalls` 的链接相关的不确定性。这显示了懒惰和无知同时在起作用，正如 [第 404 页](#Chapter12-01.xhtml#page_404) 所解释的那样：弄清楚为什么在特定情况下这些因素更可能或更不可能发生需要大量工作，而且我们无论如何也没有合理的方法获得相关信息。

概率实际上概括了警报可能失效的潜在无限种情况（高湿度、停电、电池没电、线路被切断、死老鼠卡在铃内部等）或 John 或 Mary 可能未能打电话报告的情况（外出吃午饭、度假、暂时失聪、经过的直升机等）。通过这种方式，一个小的智能体可以应对一个非常大的世界，至少近似如此。

## 13.2 贝叶斯网络的语义

Bayes 网的语法由一个有向无环图组成，每个节点附带一些局部概率信息。语义定义了语法如何对应于网络变量上的联合分布。

假设 Bayes 网包含 n 个变量，`X1,...,Xn`。联合分布中的一个通用条目则是 `P(X1 = x1 ∧ ... ∧ Xn = x n)`，或 `P(x1,..., xn)` 为简写。贝叶斯网的语义将联合分布中的每个条目定义如下：

$\\begin{matrix} {P(x\_{1},\\ldots,x\_{n}) = {\\prod\\limits\_{i = 1}^{n}\\left. \\theta(x\_{i} \\middle| \\text{parents(}X\_{i})) \\right.},} & {\\,\\,\\,\\,\\,\\,\\,\\,(13.1)} \\\\ \\end{matrix}$

其中 `parents(Xi)` 表示出现在 `x1,...,xn` 中的 `Parents(Xi)` 的值。因此，联合分布中的每个条目由 Bayes 网中局部条件分布的适当元素的乘积表示。

为说明这一点，我们可以计算警报响起，但既没有发生盗窃也没有发生地震，且 John 和 Mary 都打电话的概率。我们只需将局部条件分布中的相关条目相乘（缩写变量名）：

$\\begin{array}{l} {P\\text{(~}j,m,\\, a,\\neg b,\\neg e\\text{)}} \\\\ \\\\ \\end{array}\\,\\,\\begin{array}{l} = \\\\ = \\\\ \\end{array}\\,\\,\\begin{array}{l} \\left. P(j \\middle| a)P(m \\middle| a)P(a \\middle| \\neg b \\land \\neg e)P(\\neg b)P(\\neg e) \\right. \\\\ {\\text{0}\\text{.90} \\times \\text{0}\\text{.70} \\times \\text{0}\\text{.001} \\times 0.\\text{999} \\times 0.\\text{998~=~0}\\text{.000628}\\text{.}} \\\\ \\end{array}$

[第 12.3 节](#Chapter12-03.xhtml#sec12-3) 解释了完整的联合分布可用于回答关于该领域的任何查询。如果 Bayes 网是联合分布的表示，那么它也可以通过对所有相关的联合概率值求和来回答任何查询，每个值都是通过将局部条件分布的概率相乘计算得出的。[第 13.3 节](#Chapter13-03.xhtml#sec13-3) 更详细地解释了这一点，但也描述了更高效的方法。

到目前为止，我们忽略了一个重要问题：进入局部条件分布 `θ(xi | parents(Xi))` 的数字的含义是什么？事实证明，从 [公式 (13.1)](#Chapter13-02.xhtml#eq13-1) 我们可以证明参数 `θ(xi | parents(Xi))` 正是联合分布所隐含的条件概率 `P(xi | parents(Xi))`。请记住，条件概率可以从联合分布按如下方式计算：

$\\begin{array}{r} {P\\text{(}x\_{i}\\text{~|~}parents\\text{(}X\_{i}\\text{))} \\equiv \\frac{P\\text{(}x\_{i}\\text{,~}parents\\text{(}X\_{i}\\text{))}}{P\\text{(}parents\\text{(}X\_{i}\\text{))}}\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,} \\\\ {= \\frac{\\sum\_{y}P(x\_{i},parents\\text{(}X\_{i}\\text{),}\\mathbf{y})}{\\sum{x^{\\prime}}\_{i},\_{y}P({x^{\\prime}}\_{i},parents\\text{(}X\_{i}\\text{),}\\mathbf{y}\\text{)}}} \\\\ \\end{array}$

其中 `y` 表示除 `Xi` 及其父节点之外的所有变量的值。从这一行可以证明 `P(xi | parents(Xi)) = θ(xi | parents(Xi))` (Exercise 13.CPTE)。因此，我们可以将 [公式 (13.1)](#Chapter13-02.xhtml#eq13-1) 重写为

$\\begin{matrix} {P(x\_{1},\\ldots,x\_{n}) = {\\prod\\limits\_{i = 1}^{n}\\left. P(x\_{i} \\middle| parents\\text{(}X\_{i}\\text{))~}. \\right.}} & {\\,\\,\\,\\,\\,(13.2)} \\\\ \\end{matrix}$

这意味着当估计局部条件分布的值时，它们需要是变量给定其父节点时的实际条件概率。例如，当我们指定 `θ(JohnCalls = true | Alarm = true) = 0.90` 时，应该是在警报响起时约 90% 的时间 John 会打电话。网络的每个参数仅就一小组变量而言具有精确含义这一事实对于模型的稳健性和易于指定至关重要。

## 构建贝叶斯网络的方法

