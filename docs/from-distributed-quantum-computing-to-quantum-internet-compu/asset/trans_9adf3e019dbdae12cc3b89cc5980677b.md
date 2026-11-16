

![](img/fb3eb7e935470a2da12b03f528f097ee_108_0.png)

图 3.10 用餐密码学家问题图形表示示意图，包含 5 方和 10 条边（完全连接），每条边表示相应双方之间共享的一个秘密位，之所以是秘密，是因为所有其他方都无法知道该位是什么。

协议如下。每一轮：

- 1. 如果发言者（假设为索引为 s 的方）希望广播值 c = 0，则发言者只需设置 $p_s = \oplus_{i \in B_s} b_i$ 作为要宣布的值，其中 $B_s$ 是所有与 $P_s$ 关联的边（位）的集合；如果发言者希望广播值 c = 1，则发言者翻转 $B_s$ 中某个 $b_i$（例如 $b_s$）的值。也就是说，发言者设置 $p_s = \overline{b_s} \oplus (\oplus_{i \in B_s - \{b_j\}, b_i})$ 作为要宣布的值；所有其他方（对于 $j \neq s$）为非发言者，只需设置 $p_j = \oplus_{i \in B_i} b_i$ 作为要宣布的值。

- 2. 每个方将其 $p_i$ 值宣布给其他所有人，然后由于每个方都持有所有人的 $p_i$ 值，每个方都可以计算总的奇偶性值：$p = p_1 \oplus \dots \oplus p_n$。

我们可以使用图 3.10 中的场景来说明这个版本的协议。假设发言者是 $P_2$，则发言者宣布：$p_2 = \overline{b_2} \oplus b_7 \oplus b_8 \oplus b_3$，其余各方宣布：$p_1 = b_1 \oplus b_{10} \oplus b_6 \oplus b_2$，$p_3 = b_3 \oplus b_6 \oplus b_9 \oplus b_4$，$p_4 = b_4 \oplus b_8 \oplus b_{10} \oplus b_5$，以及 $p_5 = b_5 \oplus b_9 \oplus b_7 \oplus b_1$。当发言者广播 c = 1 时，总的奇偶性 p 为：

```
p = p_1 \oplus p_2 \oplus p_3 \oplus p_4 \oplus p_5
= (b_1 \oplus b_{10} \oplus b_6 \oplus b_2) \oplus (\overline{b_2} \oplus b_7 \oplus b_8 \oplus b_3)
\oplus (b_3 \oplus b_6 \oplus b_9 \oplus b_4) \oplus (b_4 \oplus b_8 \oplus b_{10} \oplus b_5)
\oplus (b_5 \oplus b_9 \oplus b_7 \oplus b_1)
= (b_1 \oplus b_1) \oplus (b_2 \oplus \overline{b_2}) \oplus (b_3 \oplus b_3) \oplus (b_4 \oplus b_4) \oplus (b_5 \oplus b_5)
\oplus (b_6 \oplus b_6) \oplus (b_7 \oplus b_7) \oplus (b_8 \oplus b_8) \oplus (b_9 \oplus b_9) \oplus (b_{10} \oplus b_{10}) = 1
```

当 c = 0 时，p = 0。

请注意，成对秘密位在每一轮中都会被使用，因此，如果协议需要进行多轮（例如，发言者要说的远不止一位！），则每对之间都需要多个秘密位（秘密指除了该对之外无人知晓）—— QKD 协议可用于在每对之间创建这样一串 $r$ 个秘密位，用于 $r$ 轮。

如 Huang et al. [2022] 所示，并基于 Broadbent 和 Tapp [2007]，对这些思想的巧妙变体和扩展催生了其他有趣的协议，例如 veto（一项或多项用户可以否决提案，且所有否决者的身份均隐藏）、notification（一个用户可以通知一个或多个其他用户，而通知者和接收者的身份以及接收者数量均保持隐藏）、collision detection（在匿名广播协议中可以检测到多个发言者）以及 anonymous private message transmission（发送者可以匿名向接收者传输一条 $m$ 位消息，接收者不知道发送者是谁）。

另一种量子匿名传输协议由 Christandl 和 Wehner [2005] 提出，使用广义 GHZ 态，具体如下。

- 1. 所有 $n$ 方共享 $n$ 量比特态 $\frac{1}{\sqrt{2}}(|0\rangle^{\otimes n} + |1\rangle^{\otimes n})$。

- 2. 如果 $c = 1$（即想要匿名广播 1），发言者对其量比特（即共享状态的其部分）应用相位翻转 $Z$ 门，否则不执行任何操作。

- 3. 每个方（包括发言者）执行以下操作：
  - (i) 对其量比特应用 Hadamard 变换 $H$，
  - (ii) 在计算基下测量其量比特，
  - (iii) 广播其测量结果，
  - (iv) 接收所有人宣布的测量结果并统计 1 的总数（记为 $k$），以及
  - (v) 如果 $k$ 为奇数，则得出 $c = 1$ 的结论，否则得出 $c = 0$ 的结论

- 4. 如果有一个或多个玩家未使用广播信道，则协议中止。

该协议中的匿名性源于以下事实：在 $n$ 方共享的 $n$ 量比特态 $\frac{1}{\sqrt{2}}(|0\rangle^{\otimes n} + |1\rangle^{\otimes n})$ 中，如果任意一方对其量比特应用 $Z$ 门，得到的状态为 $\frac{1}{\sqrt{2}}(|0\rangle^{\otimes n} - |1\rangle^{\otimes n})$。而且，仅从该状态无法追溯是谁对某个量比特应用了 $Z$ 门。请注意，当 $c = 0$ 时我们需要 $\frac{1}{\sqrt{2}}(|0\rangle^{\otimes n} + |1\rangle^{\otimes n})$，当 $c = 1$ 时需要 $\frac{1}{\sqrt{2}}(|0\rangle^{\otimes n} - |1\rangle^{\otimes n})$，即我们需要：$\frac{1}{\sqrt{2}}(|0\rangle^{\otimes n} + (-1)^c|1\rangle^{\otimes n})$。另外，协议中的步骤 3 用于确定全局状态的相位是否确实发生了变化，也就是说，是否有人对共享状态中的某个量比特应用了 $Z$ 门。为了解释原因，我们按照步骤 3(i) 考虑以下计算：

```
H^{\otimes n} \left( \frac{1}{\sqrt{2}} (|0\rangle^{\otimes n} + (-1)^c |1\rangle^{\otimes n}) \right)
= \frac{1}{\sqrt{2}} (H^{\otimes n} |0\rangle^{\otimes n} + (-1)^c H^{\otimes n} |1\rangle^{\otimes n})
```

$$
= \frac{1}{\sqrt{2}}((H|0\rangle)^{\otimes n} + (-1)^c (H|1\rangle)^{\otimes n})
= \frac{1}{\sqrt{2}} \left( \left( \frac{1}{\sqrt{2}} (|0\rangle + |1\rangle) \right)^{\otimes n} + (-1)^c \left( \frac{1}{\sqrt{2}} (|0\rangle - |1\rangle) \right)^{\otimes n} \right)
= \frac{1}{\sqrt{2}} \left( \left( \frac{1}{\sqrt{2}} \right)^n (|0\rangle + |1\rangle)^{\otimes n} + (-1)^c \left( \frac{1}{\sqrt{2}} \right)^n (|0\rangle - |1\rangle)^{\otimes n} \right)
= \left( \frac{1}{\sqrt{2}} \right)^{n+1} ((|0\rangle + |1\rangle)^{\otimes n} + (-1)^c (|0\rangle - |1\rangle)^{\otimes n})
= \left( \frac{1}{\sqrt{2}} \right)^{n+1} \left( \sum_{x \in \{0,1\}^n} |x\rangle + (-1)^c \sum_{x \in \{0,1\}^n} (-1)^{[x]} |x\rangle \right)
= \left( \frac{1}{\sqrt{2}} \right)^{n+1} \sum_{x \in \{0,1\}^n} (1 + (-1)^{c+[x]}) |x\rangle
```

其中 [x] 用于表示字符串 x 的汉明重量，即在此例中，x 中 1 的个数。根据上述表达式，如果 c = 0，则

1 + (-1)^{c+[x]} = 1 + (-1)^{0+[x]} = \begin{cases} 0, & \text{if } [x] \text{ is odd} \\ 2, & \text{if } [x] \text{ is even} \end{cases}

因此上述表达式简化为：

\left( \frac{1}{\sqrt{2}} \right)^{n+1} \sum_{x \in \{0,1\}^n \text{ such that } [x] \text{ is even}} |x\rangle

也就是说，振幅仅存在于 [x] 为偶数的态上。但是，如果 c = 1，则

1 + (-1)^{c+[x]} = 1 + (-1)^{1+[x]} = \begin{cases} 2, & \text{if } [x] \text{ is odd} \\ 0, & \text{if } [x] \text{ is even} \end{cases}

因此上述表达式简化为：

\left( \frac{1}{\sqrt{2}} \right)^{n+1} \sum_{x \in \{0,1\}^n \text{ such that } [x] \text{ is odd}} |x\rangle

也就是说，振幅仅存在于 [x] 为奇数的态上。然后，在步骤 3(ii) 进行测量时，我们得到一个确定的 x 值，记为 x'，对应于得到的状态 |x'>，并且 k = [x']。根据上述内容，如果 c = 0，由于振幅仅存在于汉明权重为偶数的态上，k 必须为偶数。同样，如果 c = 1，k 为奇数，这正是步骤 3(v) 中看到的情况。我们假设每轮只有一个发言者 — 有处理多个发送者/发言者以及传输量比特而非经典位的协议 [Christandl and Wehner, 2005]。

### 3.2.5 量子投票

投票是民主社会中的关键概念，量子电子投票协议已在 Arapinis et al. [2021] 中得到广泛讨论。在此，我们概述了基于 Khabiboulline et al. [2021] 的量子信息投票方案。

一般想法是使用量子态作为一种“选票”，选民可以在其中登记一票（此处的投票为二进制，例如“是”[记为 1] 或“否”[记为 0]），投票结果通过统计得到的 1 和 0 的数量来得出。一个关键考量是，选民不应能够提交多张票（而不被发现），从而损害选举的公正性。

我们有一个计票人，他采样一个随机比特串 \(x \in \{0, 1\}^n\)，其中 \(n = O(N^2)\) 以使协议正确运行，并准备 \(N\) 份选票态的副本，其中 \(N\) 是选民人数：

\(|\psi_x\rangle = \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{x_i} |i\rangle\)

其中 \(x_i\) 是 \(n\) 比特字符串 \(x = x_0 \dots x_{n-1}\) 的第 \(i\) 个比特，选票态使用 \(\lceil \log n \rceil\) 个量比特。

例如，对于 \(n = 6\)，我们使用三个量比特，而 \(x = 101100\) 的选票态是六个态的叠加：

\(\frac{1}{\sqrt{6}} (-|000\rangle + |001\rangle - |010\rangle - |011\rangle + |100\rangle + |101\rangle)\)

请注意，由于字符串只有 6 位，\(|110\rangle\) 和 \(|111\rangle\) 的系数被视为 0。选票态通过 \(|i\rangle\) 的负号在 \(i\) 位置标记一个 1，即每个分量为 \((-1)^{x_i} |i\rangle\)。

选民如何投票？在收到选票态后，选民在一个由两个态的叠加（形式为 \(\frac{1}{2}(|i\rangle + |j\rangle)\) 和 \(\frac{1}{2}(|i\rangle - |j\rangle)\)，其中 \(i \neq j\)）上的投影算符组成的基中进行测量。

如果将选票态中的六个分量态视为图的节点，那么两个节点 \((i, j)\) 之间的一条边可以用 \((|i\rangle + |j\rangle)\) 或 \((|i\rangle - |j\rangle)\) 形式的项来表示。

一个测量基的示例是一组投影算符（使用这些态）：

\(\left\{ \begin{aligned} \frac{1}{\sqrt{2}}(|000\rangle + |011\rangle), \quad \frac{1}{\sqrt{2}}(|000\rangle - |011\rangle), \\ \frac{1}{\sqrt{2}}(|001\rangle + |100\rangle), \quad \frac{1}{\sqrt{2}}(|001\rangle - |100\rangle), \\ \frac{1}{\sqrt{2}}(|010\rangle + |101\rangle), \quad \frac{1}{\sqrt{2}}(|010\rangle - |101\rangle) \end{aligned} \right\}\)

这对应于态之间的三条边，在用于测量时实际上会从三条可能的边中选出一条，得到 \((|i\rangle + |j\rangle)\) 或 \((|i\rangle - |j\rangle)\)，这对应于 $x_i$ 和 $x_j$ 的奇偶性，根据定义

