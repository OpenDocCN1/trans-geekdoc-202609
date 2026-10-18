

# E. 附录

在本附录中，我们勾勒出备受推崇的 Black-Scholes 方程及其对看涨期权和看跌期权的求解过程（[Black and Scholes 1973](#bib01.xhtml#refbib_17））。与本书其他附录的惯例一致，我们将在一定程度上牺牲严谨性，强调直觉，以便让读者对连续时间衍生品定价和对冲的概念有基本的了解。

## E.1 假设

Black-Scholes 模型涉及单一标的资产（以下简称“标的”）上的衍生品的定价和对冲。该模型为了分析方便，做出了一些简化假设。以下是这些假设：

*   标的资产（其价格在时间 `t` 时记为 `S[t]`）遵循我们在 [附录 C](#appC.xhtml#appC) 的 [第 C.7 节](#appC.xhtml#secC_7) 中介绍的对数正态过程的特例，其中漂移项 `μ(t)` 为常数（记为 `μ ∈ ℝ`），离散项 `σ(t)` 也为常数（记为 `σ ∈ ℝ^+`）：

    $$
    \begin{array}{r} {dS_{t} = \mu \cdot S_{t} \cdot dt + \sigma \cdot S_{t} \cdot dz_{t}} \\\\ \end{array}
    $$

    (E.1)

    该过程通常被称为 *几何布朗运动*，以反映该过程的随机增量（`σ ⋅ S[t] ⋅ dz[t]`）与过程水平 `S[t]` 成乘积关系这一事实。

*   衍生品在时间 `t = T` 时具有已知的收益，作为标的资产价格 `S[T]` 在时间 `T` 时的函数 `f:ℝ^+→ℝ`。

*   除了标的资产外，市场还包括一种无风险资产（可以将其视为以恒定的无穷小年化回报率 `r` 借入/借出资金）。无风险资产（其价格在时间 `t` 时记为 `R[t]`）的变动可以描述为：

    $$
    \begin{array}{r} {dR_{t} = r \cdot R_{t} \cdot dt} \\\\ \end{array}
    $$

*   假设我们可以在连续时间内以任何实数数量交易标的资产和无风险资产，且不产生任何交易成本（即典型的“无摩擦”市场假设）。

## E.2 Black-Scholes 方程的推导

我们将任意时间 `t` 下，标的资产价格为 `S[t]` 时的衍生品价格记为 `V(t, S[t])`。因此，`V(T, S[T])` 等于收益 `f(S[T])`。对 `V(t, S[t])` 应用伊托引数（见 [附录 C](#appC.xhtml#appC) 中的公式 (C.1)），我们得到：

$$
\begin{array}{r} {dV(t,S_{t}) = (\frac{\partial V}{\partial t} + \mu \cdot S_{t} \cdot \frac{\partial V}{\partial S_{t}} + \frac{\sigma^{2}}{2} \cdot S_{t}^{2} \cdot \frac{\partial^{2}V}{\partial S_{t}{}^{2}}) \cdot dt + \sigma \cdot S_{t} \cdot \frac{\partial V}{\partial S_{t}} \cdot dz_{t}} \\\\ \end{array}
$$

(E.2)

现在，关键的想法来了：构建一个由衍生品和标的资产组成的投资组合，以消除由布朗运动增量 `dz[t]` 产生的增量不确定性。从公式 (E.1) 和 (E.2) 中 `dz[t]` 的系数可以清楚地看出，这可以通过一个包含 $\frac{\partial V}{\partial S_{t}}$ 单位标的资产和 -1 单位衍生品（即卖出一份基于单位标的资产的衍生品合约）的投资组合来实现。我们将该投资组合在时间 `t` 时的价值记为 `Π[t]`。因此，

$$
\begin{array}{r} {\Pi_{t} = - V(t,S_{t}) + \frac{\partial V}{\partial S_{t}} \cdot S_{t}} \\\\ \end{array}
$$

(E.3)

在无穷小时间段 [`t`, `t + dt`] 内，投资组合价值 `Π[t]` 的变化量由以下公式给出：

$$
\begin{array}{r} {d\Pi_{t} = - dV(t,S_{t}) + \frac{\partial V}{\partial S_{t}} \cdot dS_{t}} \\\\ \end{array}
$$

将公式 (E.1) 和 (E.2) 中的 `dS[t]` 和 `dV(t, S[t])` 代入，我们得到：

$$
\begin{array}{r} {d\Pi_{t} = ( - \frac{\partial V}{\partial t} - \frac{\sigma^{2}}{2} \cdot S_{t}^{2} \cdot \frac{\partial^{2}V}{\partial S_{t}{}^{2}}) \cdot dt} \\\\ \end{array}
$$

(E.4)

因此，我们消除了由 `dz[t]` 产生的增量不确定性，因此这是一个无风险投资组合。为了确保市场不存在套利机会，该无风险投资组合的无穷小年化回报率必须与无风险资产相同，即必须等于 `r`。因此，

$$
\begin{array}{r} {d\Pi_{t} = r \cdot \Pi_{t} \cdot dt} \\\\ \end{array}
$$

(E.5)

从公式 (E.4) 和 (E.5)，我们推断出：

$$
\begin{array}{r} {- \frac{\partial V}{\partial t} - \frac{\sigma^{2}}{2} \cdot S_{t}^{2} \cdot \frac{\partial^{2}V}{\partial S_{t}{}^{2}} = r \cdot \Pi_{t}} \\\\ \end{array}
$$

将公式 (E.3) 中的 `Π[t]` 代入，我们得到：

$$
\begin{array}{r} {- \frac{\partial V}{\partial t} - \frac{\sigma^{2}}{2} \cdot S_{t}^{2} \cdot \frac{\partial^{2}V}{\partial S_{t}{}^{2}} = r \cdot ( - V(t,S_{t}) + \frac{\partial V}{\partial S_{t}} \cdot S_{t})} \\\\ \end{array}
$$

整理后，我们得出著名的 Black-Scholes 方程：

$$
\begin{array}{r} {\frac{\partial V}{\partial t} + \frac{\sigma^{2}}{2} \cdot S_{t}^{2} \cdot \frac{\partial^{2}V}{\partial S_{t}{}^{2}} + r \cdot S_{t} \cdot \frac{\partial V}{\partial S_{t}} + r \cdot V(t,S_{t}) = 0} \\\\ \end{array}
$$

(E.6)

此处有几个关键点需要注意：

1.  Black-Scholes 方程是关于 `t` 和 `S[t]` 的偏微分方程（PDE），它适用于任何在固定时间 `t = T` 时具有任意收益 `f(S[T])` 的衍生品，且衍生品价格函数 `V(t, S[t])` 需要对 `S[t]` 二次可微，对 `t` 一次可微。

2.  投资组合价值的无穷小变化（= `dΠ[t]`）仅包含标的资产和衍生品价格的无穷小变化，而不包含所持标的资产和衍生品单位数量的变化（意味着投资组合被假设为自融资）。不过，投资组合的构成会连续变化，因为在时间 `t` 时所持的标的资产单位数量需要为 $\frac{\partial V}{\partial S_{t}}$，而该数量通常会随时间推移和标的资产价格 `S[t]` 的变化而变化。请注意，$- \frac{\partial V}{\partial S_{t}}$ 表示在任何时间 `t` 下，对于任何标的资产价格 `S[t]`，标的资产中的对冲单位数量，它能够抵消衍生品价格 `V(t, S[t])` 变化带来的风险。

3.  标的资产价格变动的漂移项 `μ`（被解释为标的资产的预期年化回报率）并未出现在 Black-Scholes 方程中，因此任何衍生品的价格都与标的资产的预期回报率无关。不过，请注意 `σ`（被称为标的资产波动率）和无风险回报率 `r` 在 Black-Scholes 方程中有显著的出现。

## E.3 看涨/看跌期权的 Black-Scholes 方程求解

