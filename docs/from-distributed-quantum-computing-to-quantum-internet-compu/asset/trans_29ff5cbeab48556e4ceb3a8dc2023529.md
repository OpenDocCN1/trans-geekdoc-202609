
然后对 \( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} |i\rangle |0\rangle \) 应用 \( U_b \)（即 (i) 的结果加上处于 \( |0\rangle \) 状态的辅助量子位），得到：

\( U_b \left( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} |i\rangle |0\rangle \right) = \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} U_b |i\rangle |0\rangle \)

（按线性）

\( = \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} |i\rangle |0 \oplus b_i\rangle = \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} |i\rangle |b_i\rangle \)

(iii) 然后对 (ii) 的结果应用 \( I^{\otimes l} \otimes Z \)，得到：

\( (I^{\otimes l} \otimes Z) \left( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} |i\rangle |b_i\rangle \right) = \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} |i\rangle |b_i\rangle \)

(iv) 最后，为了将前 \( l \) 个量子位与最后一个量子位“解纠缠”，我们对 (iii) 的结果再次应用 \( U_b \)，得到：

\( U_b \left( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} |i\rangle |b_i\rangle \right) \\
= \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} U_b |i\rangle |b_i\rangle = \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} |i\rangle |b_i \oplus b_i\rangle \\
= \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} |i\rangle |0\rangle = \left( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} |i\rangle \right) \otimes |0\rangle \)

也就是说，在 (ii)–(iv) 中，我们应用了 \( U_b(I^{\otimes l} \otimes Z)U_b \)，最后一个量子位可以被测量（丢弃）以得到我们想要准备的状态 \( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} |i\rangle \)；这个 \( l \) 量子位状态随后被发送到 \( A \)（例如，通过量子隐形传态——比如说，分别对每个量子位进行隐形传态）。

- 2. \( A \) 接收该状态，并应用一个将 \( |i\rangle \) 映射到 \( (-1)^{\alpha_i} |i\rangle \) 的操作，然后还对每个量子位应用 Hadamard 变换，并测量得到的 \( l \)-量子位比特串。

将 \( |i\rangle \) 映射到 \( (-1)^{\alpha_i} |i\rangle \) 的映射可以使用类似于上面 \( U_b \) 定义的操作 \( U_a \) 来完成；也就是说，我们在带有辅助量子位 \( |0\rangle \) 的接收状态上应用 \( U_a(I^{\otimes l} \otimes Z)U_a \)：

\( U_a(I^{\otimes l} \otimes Z)U_a \left( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} |i\rangle \right) |0\rangle = \left( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{\alpha_i + b_i} |i\rangle \right) |0\rangle \)

丢弃最后一个量子位。然后，在 Hadamard 变换之后，被测量的状态是：

\( H^{\otimes l} \left( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{\alpha_i + b_i} |i\rangle \right) = \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{\alpha_i + b_i} H^{\otimes l} |i\rangle \)

\( = \frac{1}{\sqrt{n}}\sum_{i=0}^{n-1}(-1)^{a_i+b_i}(H | i_1 \rangle \otimes \cdots \otimes H | i_l \rangle) \)
（其中 \( | i \rangle = | i_1 \dots i_l \rangle\)，\( i$ 的比特串表示）
\( = \frac{1}{\sqrt{n}}\sum_{i=0}^{n-1}(-1)^{a_i+b_i}\left( \frac{1}{\sqrt{2}} \right)^l (|0\rangle + (-1)^{i_1} |1\rangle) \otimes \cdots \otimes (|0\rangle + (-1)^{i_l} |1\rangle) \)
\( = \frac{1}{n} \sum_{i=0}^{n-1}(-1)^{a_i+b_i} \sum_{j \in \{0,1\}^l} (-1)^{i \cdot j} |j\rangle \)
（因为 \(\left( \frac{1}{\sqrt{2}} \right)^l = \frac{1}{\sqrt{n}}\) 和 \(i \cdot j = i_1 \times j_1 \oplus \cdots \oplus i_l \times j_l\)）

我们注意到，如果 \( a = b$，则 \( | 0 \dots 0 \rangle$ 的幅度为 \(\frac{1}{n} \sum_{i=0}^{n-1} (-1)^{a_i+b_i} = 1$，即如果 \( a = b$，则得到 \( | 0 \dots 0 \rangle$ 的概率为 1。但如果 \( a$ 和 \( b$ 在恰好 \( n/2$ 个位置上不同，则幅度 \(\frac{1}{n} \sum_{i=0}^{n-1} (-1)^{a_i+b_i} = 0$（“1” 和 “-1” 数量相等的求和），得到状态 \( | 0 \dots 0 \rangle$ 的概率为零。

- 3. 如果测量结果是状态 \( | 0 \dots 0 \rangle$，则 \( A$ 输出 1（即我们有情况 (1) \( a = b$）；否则输出 0（即我们有情况 (2) \( a$ 和 \( b$ 在恰好 \( n/2$ 个位置上不同）。

因此，\( A$ 仅需从 \( B$ 发送 \(\log_2 n$ 个量子位即可解决这个承诺问题！（因为对每个量子位进行隐形传态需要两个经典位（和一个共享 ebit），因此需要 \( 2(\log_2 n)$ 或 \( O(\log n)$ 个经典位。）Buhrman 等人 [2010] 指出，经典协议需要发送至少 \( 0.007n$ 个位！因此，对于较小的 \( n$，经典协议可能更高效，但对于较大的 \( n$，经典协议的通信复杂度将呈指数级更高（但需注意量子协议需要使用量子位）。

## 3.1.1.3 分布式交集问题

让我们考虑 Buhrman 等人 [2010] 的另一个问题。假设我们有 \( A$ 和 \( B$，其中 \( A$ 拥有一个 \( n$ 比特字符串 \( a = a_1 \dots a_n$，\( B$ 拥有一个 \( n$ 比特字符串 \( b = b_1 \dots b_n$。问题是计算以下函数 \( g$：

\(g(a, b) = \begin{cases} 1, & \text{if } a_i = b_i = 1 \text{ for at least one } i \\ 0, & \text{otherwise} \end{cases}\)

可以将此想象为用于计算会议时间，其中 \( a$ 和 \( b$ 的比特表示 \( A$ 和 \( B$ 可用的时间段（“0”表示不可用，“1”表示可用），并尝试找到至少一个两人都可用的时间段。

这个问题等同于寻找满足 \( a_i \wedge b_i = 1$ 的索引 \( i$。例如，如果 \( a = 10111$ 和 \( b = 11101$，则当 \( i$ 为 0、2 和 4 时，\( a_i \wedge b_i = 1$。因此，给定两个 \( n$ 比特字符串 \( a$ 和 \( b$，这变成了一个搜索问题，即寻找满足条件 \( a_i \wedge b_i = 1$ 的索引 \( i \in \{1, ..., n\}$（我们也可以使用索引 \( 0$ 到 \( n-1$）。

我们可以使用 Grover（量子）算法 [Grover, 1996] 来执行此搜索，这使我们能够（渐进地）比最佳经典算法更快地搜索到这样的解。Grover 算法使用一个函数 \( f : \{0, ..., n-1\} \to \{0, 1\}$，使得 \( f(x) = 1$ 当且仅当 \( x$ 指向满足搜索标准的项目——我们可以将 \( x$ 视为数据库中项目的索引——让我们就称 \( f$ 为数据库。假设 \( x'$ 是满足 \( f(x') = 1$ 的一个项目，我们假设有一个可使用如下定义的 \( f$ 的量子操作 \( V_{x'}$\(^2$：

\(V_{x'} |x\rangle = \begin{cases} -|x\rangle, & \text{if } x = x', \text{i.e. } f(x) = 1 \\ |x\rangle, & \text{if } x \neq x', \text{i.e. } f(x) = 0 \end{cases}\)

也就是说，\( V_{x'}$ 可以写成 \( V_{x'} |x\rangle = (-1)^{f(x)} |x\rangle$。该操作的想法是“标记”满足特定搜索标准的项目为 “\(-1\)”。在 Grover 算法中，有一个称为 _Grover 迭代_ 的单元操作，定义为 \( G = H^{\otimes l} V_0 H^{\otimes l} V_{x'}$，假设 \( n = 2^l$。Grover 迭代被反复应用，首先应用于如下的状态 \( |s\rangle$，然后反复应用于得到的状态：

- 1. 从 \( l$-量子位状态 \( |0\rangle^{\otimes l}$ 准备状态 \( |s\rangle$，例如通过 \( |s\rangle = H^{\otimes l} |0\rangle^{\otimes l} = \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} |i\rangle$
- 2. 对状态应用 Grover 迭代 \( G$，\( t$ 次
- 3. 在计算基下测量得到的状态中的所有量子位

在上述步骤结束时，可以检查得到的结果（来自 (3) 的比特串）是否确实是问题的解。Grover 算法可以使用 \( O(\sqrt{n})$ 次 \( V_{x'}$ 的应用，以趋近于 1 的概率返回 \( |x'\rangle$，特别是当 \( t = \lceil \frac{\pi}{4}(\sqrt{n}) \rceil$ 时。如果有多个解， say \( m$ 个解，则 \( t = \lceil \frac{\pi}{4}(\sqrt{n/m}) \rceil$。（注意，如果运行 \(\lceil \frac{\pi}{4}(\sqrt{n}) \rceil$ 次迭代后得到的结果不是解，那么很可能一开始就没有解！）

我们将探讨交集问题如何成为 Grover 算法的一个应用。如果 \( a$ 和 \( b$ 在同一台机器上，我们可以定义 \( f$ 使得 \( f(x) = 1$ 当且仅当 \( a_x \wedge b_x = 1$，即 \( f(x) = a_x \wedge b_x$。然后，依赖于 \( a$ 和 \( b$ 的操作 \( V_{a,b}$ 变为：

\(V_{a,b} |x\rangle = (-1)^{a_x \wedge b_x} |x\rangle\)
