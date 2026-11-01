
# 扩展型博弈与逆向归纳

## 逆向归纳与纳什均衡

更详细地说，对于每个非终结状态 `s`，如果 `s` 的所有子节点都已用收益分布标记，则用使在状态 `s` 作出决策的玩家收益最大化的子状态的收益分布来标记 `s`。（如果出现平局，则任意选择；如果有机会节点，则计算期望效用。）`backward induction` 算法保证会终止，而且运行时间在博弈树规模上是多项式的。

随着算法的执行，它为每个玩家追踪出策略。事实证明，这些策略是 `Nash equilibrium` 策略，并且标记初始状态的收益分布是采用 `Nash equilibrium` 策略进行博弈时会得到的收益分布。因此，`extensive-form` 博弈的 `Nash equilibrium` 策略可以使用 `backward induction` 在多项式时间内计算；并且由于算法保证会用收益分布标记初始状态，可知每个 `extensive-form` 博弈至少存在一个纯策略 `Nash equilibrium`。

这些结果很有吸引力，但存在若干需要注意之处。博弈树很快就会变得非常庞大，因此多项式运行时间应在该背景下理解。但更成问题的是，`Nash equilibrium` 本身在应用于 `extensive-form` 博弈时存在一些局限性。考虑图 17.4 中的博弈。`Player 1` 有两种可用的行动：`above` 或 `below`。如果她选择 `below`，则无论 `Player 2` 选择什么行动，两名玩家都获得 0 的收益。如果她选择 `above`，则 `Player 2` 面临选择 `up` 或 `down`：如果她选择 `down`，则两名玩家都获得 0 的收益，而如果她选择 `up`，则他们都获得 1。

描述
椭圆形部分表示机会节点，矩形表示决策节点，而菱形表示效用节点。从标记为 Plug slash Unplug 下标 t 的决策节点发出的一条箭头指向标记为 Charging 下标 t 加 1 BaseLine 的决策节点。从标记为 LeftWheel 下标 t 的决策节点发出的一条箭头指向标记为 X dot 下标 t 加 1 BaseLine 的节点。从标记为 RightWheel 下标 t 的决策节点发出的一条箭头指向标记为 X dot 下标 t 加 1 BaseLine 的节点。从标记为 Charging 下标 t 的机会节点发出三条箭头指向两个标记为 Charging 下标 t 加 1 BaseLine、Battery 下标 t 加 1 BaseLine 的机会节点，以及一个标记为 R 下标 t 的效用节点。从标记为 Battery 下标 t 的机会节点发出两条箭头指向标记为 X dot 下标 t 加 1 BaseLine 和 Battery 下标 t 加 1 BaseLine 的节点。从节点 X dot 下标 t 发出四条箭头指向四个标记为 Charging 下标 t 加 1 BaseLine、Battery 下标 t 加 1 BaseLine、X dot 下标 t 加 1 BaseLine 和 X 下标 t 加 1 BaseLine 的节点。从节点 X 下标 t 发出五条箭头指向标记为 Charging 下标 t 加 1 BaseLine、Battery 下标 t 加 1 BaseLine、X dot 下标 t 加 1 BaseLine、X 下标 t 加 1 BaseLine 的机会节点，以及一个标记为 R 下标 t 的效用节点。从机会节点 Charging 下标 t 加 1 BaseLine 发出三条箭头指向两个标记为 Charging 下标 t 加 2 BaseLine、Battery 下标 t 加 2 BaseLine 的机会节点，以及一个标记为 R 下标 t 加 1 BaseLine 的效用节点。从节点 Battery 下标 t 加 1 BaseLine 发出两条箭头指向两个节点 Battery 下标 t 加 2 BaseLine 和 X dot 下标 t 加 2 BaseLine。从节点 X dot 下标 t 加 1 BaseLine 发出四条箭头指向四个节点 Charging 下标 t 加 2 BaseLine、Battery 下标 t 加 2 BaseLine、X dot 下标 t 加 2 BaseLine 和 X 下标 t 加 2 BaseLine。从节点 X 下标 t 加 1 BaseLine 发出五条箭头指向节点 Charging 下标 t 加 2 BaseLine、Battery 下标 t 加 2 BaseLine、X dot 下标 t 加 2 BaseLine、X 下标 t 加 2 BaseLine，以及效用节点 R 下标 t 加 1 BaseLine。从决策节点 Plug slash Unplug 下标 t 加 1 BaseLine 发出一條箭头指向机会节点 Charging 下标 t 加 2 BaseLine。从标记为 LeftWheel 下标 t 加 1 BaseLine 的决策节点发出的一条箭头指向节点 X dot 下标 t 加 2 BaseLine。从决策节点 RightWheel 下标 t 加 1 BaseLine 发出一條箭头指向节点 X dot 下标 t 加 2 BaseLine。从节点 Charging 下标 t 加 2 BaseLine、Battery 下标 t 加 2 BaseLine、X dot 下标 t 加 2 BaseLine 和 X 下标 t 加 2 BaseLine 发出的箭头指向效用节点 U 下标 t 加 2 BaseLine。

×![](images/Fig-243.jpg)

图 17.4 一个具有反直觉纳什均衡的扩展型博弈。

`backward induction` 立即告诉我们 `(above, up)` 是 `Nash equilibrium`，使得两名玩家都获得 1 的收益。然而，`(below, down)` 也是一个 `Nash equilibrium`，会使得两名玩家都获得 0 的收益。`Player 2` 对 `Player 1` 发出威胁，表示如果被要求做出决策她将选择 `down`，从而使 `Player 1` 的收益为 0；在这种情况下，`Player 1` 没有比选择 `below` 更好的替代方案。问题在于 `Player 2` 的威胁（选择 `down`）并不是可信的威胁，因为如果 `Player 2` 真的被要求做出选择，她会选择 `up`。

<p class="sidebar">可信威胁</p>

### 子博弈完美纳什均衡

一种称为 `subgame perfect Nash equilibrium` 的 `Nash equilibrium` 改进解决了这个问题。为了定义它，我们需要子博弈的概念。博弈树中的每个决策状态（包括初始状态）都定义了一个子博弈——图 17.4 中的博弈因此包含两个子博弈，一个以 `Player 1` 的决策状态为根，一个以 `Player 2` 的决策状态为根。策略的组合在博弈 `G` 中形成 `subgame perfect Nash equilibrium` 当且仅当它在 `G` 的每个子博弈中都是 `Nash equilibrium`。将此定义应用于图 17.4 的博弈，我们发现 `(above, up)` 是子博弈完美的，但 `(below, down)` 不是，因为选择 `down` 并不是以 `Player 2` 决策状态为根的子博弈的 `Nash equilibrium`。

<p class="sidebar">子博弈完美纳什均衡</p> <p class="sidebar">子博弈</p>

尽管我们需要一些新术语来定义 `subgame perfect Nash equilibrium`，但我们不需要任何新算法。通过 `backward induction` 计算出的策略将是 `subgame perfect Nash equilibria`，由此可知每个 `perfect information` 的 `extensive-form` 博弈都有一个 `subgame perfect Nash equilibrium`，并且可以在博弈树规模上多项式时间内计算。

### 机会与同时行动

为了以扩展形式表示诸如 backgammon 之类的随机博弈，我们增加一个名为 `Chance` 的玩家，其选择由概率分布决定。

为了表示同时行动，如囚徒困境或两指莫拉，我们对玩家施加任意顺序，但我们可以选择断言较早玩家的行动对后续玩家不可观察：例如，Ali 必须先选择拒绝或作证，然后 Bo 选择，但 Bo 在当时并不知道 Ali 做出的选择（我们也可以表示该行动稍后会被揭示）。然而，我们假设玩家始终记得自己所有的先前行动；这一假设称为 `perfect recall`。

### 捕捉不完全信息

扩展形式的一个关键特征使其有别于我们在第 6 章中看到的博弈树，即它可以捕捉部分可观察性。博弈论者使用术语 `imperfect information` 来描述玩家对博弈实际状态不确定的情况。不幸的是，`backward induction` 不能用于 `imperfect information` 的博弈，通常而言，它们比 `perfect information` 的博弈复杂得多。

<p class="sidebar">不完全信息</p>
