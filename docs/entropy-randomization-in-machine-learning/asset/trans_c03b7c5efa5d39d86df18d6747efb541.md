

考虑具有独立增量的一些过程的例子。让我们从 `Brownian motion` 开始。对于该过程，概率分布 `P(t, h, ℬ)` 是高斯的。该过程的物理模型是液体中小颗粒的运动，可以用高倍显微镜观察到。这样的颗粒具有恒定的运动，其路径代表一条非常复杂的折线，具有混乱方向的线段。这种运动可以用颗粒与液体分子的碰撞来解释。颗粒相对于每个分子的尺寸具有相对较大的尺寸，并且每秒遭受大量与它们的碰撞。颗粒的可见运动称为布朗运动。在粗略近似下，颗粒因碰撞而产生的位移可以认为彼此独立，因此布朗运动可以被视为具有独立增量的过程。由于位移很小，我们可以假设其总和满足中心极限定理；换句话说，布朗运动可以用具有独立增量的高斯随机过程来描述。

特别地，均质布朗随机过程由两个参数 `m` 和 `σ` 定义：

$$
\begin{array}{r} {\mathcal{M}\left\{ x(t) \right\} = mt,\quad\mathcal{M}\left\{ x^{2}(t) \right\} = \sigma^{2}t.} \\ \end{array}
$$

(2.28)

对于 `m` = 0 和 `σ` = 1，布朗运动过程称为 `the standard Wiener process`。

现在考虑 `Poisson processes`。一种具有独立增量的随机连续过程，取非负整数值，如果对于任意 (`s`, `t`) > 0 且 `s` < `t`，变量 `x(t) - x(s)` 服从泊松概率分布，则称为泊松过程。

设 `x(t[0])` = 0。则变量 `x(t)` 具有概率分布

$$
\begin{array}{r} {\mathbf{P}\left\{ x(t) = m \right\} = \frac{a^{m}(t)}{m!}\exp( - a(t)),\quad\mathcal{M}\left\{ x(t) \right\} = a(t).} \\ \end{array}
$$

(2.29)

由此可得

$$
\begin{aligned} {\mathbf{P}\left\{ x(t) - x(s) = m \right\}} & {= \frac{[a(t) - a(s)]^{m}}{m!}\exp\left( - [a(t) - a(s)] \right),} \\ & {\quad m = 0,1,2,\ldots} \\ \end{aligned}
$$

(2.30)

如果过程是均质的，则

$$
\begin{aligned} & {a(t) = at,} \\ {\mathbf{P}\left\{ x(t) - x(s) = m \right\}} & {= \frac{a^{m}{(t - s)}^{m}}{m!}\exp( - a(t - s)),} \\ {s < t,} & {m = 0,1,2,\ldots} \\ \end{aligned}
$$

(2.31)

### 3. Markov processes

`Markov process` 的概念基于关于非遗传系统（也称为“无后效”系统）的假设。在每个时刻 `t`，这样的系统具有某个状态 `x(t)`，它仅取决于其在先前时刻 `s` < `t` 的状态 `x(s)`。所有允许的状态形成某个集合 `B` ∈ `X`，其中 `X` 是系统的相空间。假设系统是随机演化的，即其在时刻 `t` 的状态不能由在先前时刻 `s` 的状态唯一确定，从而是随机的。用 `P(s, x, t, B)` 表示在条件 `x(s) = x` 下事件 `{ x(t) ∈ B(s < t) }` 的概率，通常称为 `the transition probability` 或系统状态在时刻 `t` 属于集合 `B` 的条件概率，给定其在相空间 `X` 中在时刻 `s` 的状态为 `x`。

假设在状态 `x(s)` 和 `x(t)` 之间存在中间状态 `x(u)`，其中 `s` < `u` < `t`。用 `P(s, x, u, y, t, B)` 表示在给定 `x(s) = x` 且 `x(u) = y` 的条件下事件 `{ x(t) ∈ B }` 的条件概率。利用条件概率的一般性质，写出

$$
\begin{array}{r} {P(s, x, t, B) = \int_{X}P(s, x, u, y, t, B)\, P(s, x, u, y)\, d y.} \\ \end{array}
$$

(2.32)

对于非遗传系统，一个自然的假设是

$$
\begin{array}{r} {P(s, x, u, y, t, B) = P(u, y, t, B).} \\ \end{array}
$$

(2.33)

在这种情况下，等式 (2.34) 取形式

$$
\begin{array}{r} {P(s, x, t, B) = \int_{X}P(u, y, t, B)\, P(s, x, u)\, d y.} \\ \end{array}
$$

(2.34)

这是 `the Chapman–Kolmogorov equation`，它是马尔可夫过程理论的基础 [[47](#refbib.xhtml#r47), 65, 166]。

马尔可夫过程称为 `homogeneous` 如果转移概率仅取决于参数 `t` 和 `s` 的差，即

$$
\begin{array}{r} {P(s, x, t, B) = P(t - s, x, B) = P_{t - s}(x, B).} \\ \end{array}
$$

(2.35)

对于齐次马尔可夫过程，Chapman–Kolmogorov 方程 (2.34) 可以写成更简单的形式

$$
\begin{array}{r} {P_{u + v}(x, B) = \int_{X}P_{u}(x)P_{v}(y, B)\, d y.} \\ \end{array}
$$

(2.36)

本节给出的定义很宽泛，从而涵盖了来源和性质不同的马尔可夫过程。在下文中，我们将讨论一些分类原则和某些马尔可夫过程类。第一个分类属性在于观察到马尔可夫过程的系统的相空间。从这个观点看，初等马尔可夫过程是具有有限或可数个允许状态的过程。在后一种情况下，通过对转移概率施加一些解析约束，我们可以线性化 Chapman–Kolmogorov 方程并获得其线性化对应物。对于一般相空间，可以以广义的方式定义马尔可夫过程类，使转移概率具有更符合实际系统行为的性质。这种观点允许引入以下马尔可夫过程类：

1. `Jump processes.` 它们对应于过程在相空间的某一点移动的想法，在该点停留随机一段时间，然后跳到空间的另一点，等等。

2. `Processes with discrete interference of events.` 这些过程由其轨迹在随机时间发生简单不连续的随机跳变的动态系统生成。

3. `Diffusion processes.` 它们代表在有限维动态系统中在小时间段内具有布朗运动的过程。

4. `Markov processes with independent increments.` 这种过程的来源是有限维动态系统，它们在小时间段内表现得像具有独立增量的过程。

对于上述马尔可夫过程类，也有可能对 Chapman–Kolmogorov 方程进行线性化，将其转化为线性偏微分方程或积分微分方程。

## 2.2 Digital Source of Data

