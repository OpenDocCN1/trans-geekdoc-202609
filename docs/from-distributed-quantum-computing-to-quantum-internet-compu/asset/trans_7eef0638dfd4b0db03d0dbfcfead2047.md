

在 Grover 迭代中重复使用该操作 $O(\sqrt{n})$ 次，即可得到问题的解。

但我们的问题是分布式的，A 拥有 $a$，B 拥有 $b$。那么，如何让 $A$ 运行 Grover 算法，但以分布式的方式执行上述 $V_{a,b}$ 操作呢？一种方法如下。

### 实现 $V_{a,b}$ 的算法

每当 $A$ 想要对某个状态 $|\psi\rangle = \sum_{i=0}^{n-1} \alpha_i |i\rangle$ 执行 $V_{a,b}$，也就是说，$A$ 想要得到

$$V_{a,b} |\psi\rangle = V_{a,b} \left( \sum_{i=0}^{n-1} \alpha_i |i\rangle \right) = \sum_{i=0}^{n-1} \alpha_i V_{a,b} |i\rangle = \sum_{i=0}^{n-1} \alpha_i (-1)^{a_i \wedge b_i} |i\rangle$$

机器 $A$ 可以执行以下步骤：

- 1. 机器 $A$ 创建状态

$$\sum_{i=0}^{n-1} \alpha_i |i\rangle |a_i\rangle$$

有效地将 $a_i$ 作为额外的量子比特附加到状态 $|\psi\rangle$ 上。该状态可以按以下方式制备：假设我们有一个操作 $U_a |i\rangle |p\rangle = |i\rangle |p \oplus a_i\rangle$，之前已证明它是一个酉操作，然后将 $U_a$ 应用到 $|\psi\rangle |0\rangle$，即，$U_a |\psi\rangle |0\rangle = U_a (\sum_{i=0}^{n-1} \alpha_i |i\rangle) |0\rangle = \sum_{i=0}^{n-1} \alpha_i U_a |i\rangle |0\rangle = \sum_{i=0}^{n-1} \alpha_i |i\rangle |a_i\rangle$。

- 2. 然后，$A$ 将状态 $\sum_{i=0}^{n-1} \alpha_i |i\rangle |a_i\rangle$ 发送给 $B$，该状态包含 $(l+1)$ 个量子比特（为了简便，我们假设 $n=2^l$）。

- 3. 然后，机器 $B$ 对接收到的状态 $\sum_{i=0}^{n-1} \alpha_i |i\rangle |a_i\rangle$ 应用酉操作：$O_b : |i\rangle |x\rangle \rightarrow (-1)^{x \wedge b_i} |i\rangle |x\rangle$，以得到：

$$O_b \left( \sum_{i=0}^{n-1} \alpha_i |i\rangle |a_i\rangle \right) = \sum_{i=0}^{n-1} \alpha_i O_b |i\rangle |a_i\rangle = \sum_{i=0}^{n-1} \alpha_i (-1)^{a_i \wedge b_i} |i\rangle |a_i\rangle$$

（注意，操作 $O_b$ 在某个状态 $|i\rangle |x\rangle$ 上可以按以下方式实现：假设我们有一个操作 $U'_b$，它将 $|i\rangle |p\rangle |q\rangle$ 映射到 $|i\rangle |p\rangle |q \oplus (p \wedge b_i)\rangle$，$^3$ 执行计算

$$
\begin{aligned}
U'_b(I^{\otimes(l+1)} \otimes Z)U'_b |i\rangle |x\rangle |0\rangle &= U'_b(I^{\otimes(l+1)} \otimes Z) |i\rangle |x\rangle |0 \oplus (x \wedge b_i)\rangle \\
&= U'_b(-1)^{x \wedge b_i} |i\rangle |x\rangle |x \wedge b_i\rangle \\
&= (-1)^{x \wedge b_i} U'_b |i\rangle |x\rangle |x \wedge b_i\rangle \\
&= (-1)^{x \wedge b_i} |i\rangle |x\rangle |(x \wedge b_i) \oplus (x \wedge b_i)\rangle \\
&= (-1)^{x \wedge b_i} |i\rangle |x\rangle |0\rangle
\end{aligned}
$$

并舍弃辅助量子比特 $|0\rangle$，我们就将 $|i\rangle |x\rangle$ 映射到了 $(-1)^{x \wedge b_i} |i\rangle |x\rangle$。）

- 4. 机器 B 然后将结果 $\sum_{i=0}^{n-1} \alpha_i(-1)^{a_i \wedge b_i} |i\rangle |a_i\rangle$ 发回给 A，即 (l + 1) 个量子比特。

- 5. 机器 A 接收到结果，并通过应用 $U_a$ 将最后一个量子比特设为 $|0\rangle$：

$$
\begin{aligned}
U_a \left( \sum_{i=0}^{n-1} \alpha_i(-1)^{a_i \wedge b_i} |i\rangle |a_i\rangle \right) &= \sum_{i=0}^{n-1} \alpha_i(-1)^{a_i \wedge b_i} U_a |i\rangle |a_i\rangle \\
&= \sum_{i=0}^{n-1} \alpha_i(-1)^{a_i \wedge b_i} |i\rangle |a_i \oplus a_i\rangle \\
&= \sum_{i=0}^{n-1} \alpha_i(-1)^{a_i \wedge b_i} |i\rangle |0\rangle
\end{aligned}
$$

最后一个量子比特可以被丢弃/忽略，因此机器 A 得到：

$$\sum_{i=0}^{n-1} \alpha_i(-1)^{a_i \wedge b_i} |i\rangle$$

正如所需，我们已计算出 \(V_{a,b} |\psi\rangle\)！

总之，计算分布式交集问题解的算法如下，在 A 处执行：

- 1. 从 l 量子比特状态 $|0\rangle^{\otimes l}$ 开始，制备状态 $|s\rangle = \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} |i\rangle$，例如通过 $|s\rangle = H^{\otimes l} |0\rangle^{\otimes l}$

- 2. 从状态 $|s\rangle$ 开始，应用 Grover 迭代 G，t 次，其中 G 定义如下（与之前的形式等价）：$G = (2 |s\rangle \langle s| - I)V_{a,b}$，每次应用 $V_{a,b}$ 时都涉及与 B 的通信（如上所述）；也就是说，我们计算 $\underbrace{G \dots G}_t |s\rangle$

$$
\begin{aligned}
&\left( \sum_{i \in \{0,1\}^l, p \in \{0,1\}, q \in \{0,1\}} \alpha_{l,p,q} \langle i | \langle p | \langle q \oplus (p \wedge b_i) | \right)^\dagger \left( \sum_{i \in \{0,1\}^l, p \in \{0,1\}, q \in \{0,1\}} \alpha_{l,p,q} |i\rangle |p\rangle |q \oplus (p \wedge b_i)\rangle \right) \\
&= \left( \sum_{i \in \{0,1\}^l, p \in \{0,1\}, q \in \{0,1\}} \alpha_{l,p,q} \langle i | \langle p \langle q \oplus (p \wedge b_i) | \right) \left( \sum_{i \in \{0,1\}^l, p \in \{0,1\}, q \in \{0,1\}} \alpha_{l,p,q} |i\rangle |p\rangle |q \oplus (p \wedge b_i)\rangle \right) \\
&= \sum_{i \in \{0,1\}^l, p \in \{0,1\}, q \in \{0,1\}} \alpha^2_{l,p,q} \langle i | \langle p \langle q \oplus (p \wedge b_i) | |i\rangle |p\rangle |q \oplus (p \wedge b_i)\rangle \\
&= \sum_{i \in \{0,1\}^l, p \in \{0,1\}, q \in \{0,1\}} \alpha^2_{l,p,q} = \langle \psi | \psi \rangle
\end{aligned}
$$

- 3. 在计算基下测量结果状态中所有量子比特

分析：在每个涉及 \( V_{a,b} \) 的 Grover 迭代操作中，会发送两条消息，每条消息包含 \( (l + 1) = (\log_2 n + 1) \) 个量子比特，并且会进行 \( t = O(\sqrt{n}) \) 次迭代；因此，该算法总共使用 \( O(\sqrt{n} \cdot \log n) \) 个量子比特的通信量。每个量子比特通过隐形传态发送，将使用一个共享的 ebit 和两个经典比特，因此，需要 \( O(\sqrt{n} \cdot \log n) \) 个经典比特的通信量。事实上，一个更高效的算法可以做得更好——只需通信 \( O(\sqrt{n}) \) 个量子比特 [Buhrman et al., 2010]。这与经典算法形成对比，经典算法需要通信约 \( n \) 个比特，因此与量子解相比，在通信复杂度中获得了二次差距（特别是当 $n$ 非常大时）！

### 3.1.1.4 讨论

我们已经看到一个分布式计算的例子，其中使用纠缠将通信复杂度降低了一个比特，与最优的经典协议（不使用纠缠）相比；另一个例子是计算 DJ Promise Problem，通过传输量子状态（例如，可能使用纠缠的隐形传态），将通信复杂度降低了指数级差距；第三个例子是计算分布式交集，获得了二次改进差距。这引出了 Buhrman et al. [2010] 提出的问题：“量子通信复杂度是否对于每个通信问题都可能高效得多？”不幸的是，这个问题的答案是否定的，并且有人指出，对于大多数通信复杂度问题，“量子通信帮助不大”；例如，计算内积（两个 \( n \) 位字符串，A 拥有一个，B 拥有另一个）被指出为一个例子，其中最佳经典协议和量子协议都需要通信 \( n \) 个量子比特/比特才能求解。

## 3.1.2 实现经典无法完成的分布式计算

我们已经看到了如何利用量子通信，使某些分布式计算问题可以用更低的通信复杂度解决。现在我们来看某些分布式计算问题，如果不使用量子协议，特别是不使用纠缠，就无法解决。我们来看 Buhrman et al. [2010] 中的两个问题。

### 3.1.2.1 Greenberger–Horne–Zeilinger 和 Mermin（GHZ&M）游戏

GHZ&M 这个名称来源于该问题的早期作者 [Buhrman et al., 2010]。考虑三个参与方，其输入和输出如图所示

![](img/fb3eb7e935470a2da12b03f528f097ee_71_0.png)

图 3.1 GHZ&M 问题是 A、B 和 C 在分别接收到输入 $i_A, i_B,$ 和 $i_C$ 后，计算输出比特 $o_A, o_B,$ 和 $o_C$（分别），使得输出比特之间满足某些属性，且 A、B 和 C 在接收到输入后不进行通信。

图 3.1. GHZ&M 问题是计算输出比特 $o_A$，$o_B$ 和 $o_C$，使得满足以下条件：

$$o_A \oplus o_B \oplus o_C = \begin{cases} 0, & \text{if } i_A i_B i_C = 000 \\ 1, & \text{if } i_A i_B i_C \in \{011, 101, 110\} \end{cases}$$

但一旦 A、B 和 C 接收到输入，就不允许通信（发送经典或量子比特）。请注意，如果输入不是上述四种组合之一，输出是什么都无所谓（或者我们假设输入总是上述四种组合之一（000、011、101、110），每种出现的概率相等）。

让我们来看看量子解。假设 A、B 和 C 分别各有一个量子比特 $\psi_A$、$\psi_B$ 和 $\psi_C$，且 3 量子比特系统的状态为纠缠态：

$$\frac{1}{2}(|000\rangle - |011\rangle - |101\rangle - |110\rangle)$$

这在局部酉（LU）操作下等价于 GHZ 态——请参见旁注。

> **旁注：** 可能有不同的操作；一种如下：
>
> - 1. 从 $\frac{1}{\sqrt{2}}(|000\rangle + |111\rangle)$ 开始，应用操作 $H \otimes H \otimes H$：
>
> $$(H \otimes H \otimes H) \frac{1}{\sqrt{2}}(|000\rangle + |111\rangle)$$
>
> $$= \frac{1}{\sqrt{2}}(H|0\rangle H|0\rangle H|0\rangle + H|1\rangle H|1\rangle H|1\rangle)$$
>
> $$= \frac{1}{4}((|000\rangle + |001\rangle + |010\rangle + |011\rangle + |100\rangle + |101\rangle + |110\rangle + |111\rangle))$$

