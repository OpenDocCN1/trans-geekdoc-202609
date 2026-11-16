

= \frac{1}{4} (|000\rangle + |001\rangle + |010\rangle + |011\rangle + |100\rangle + |101\rangle + |110\rangle + |111\rangle) - (|000\rangle + |001\rangle + |010\rangle - |011\rangle + |100\rangle - |101\rangle - |110\rangle + |111\rangle) = \frac{1}{2} (|001\rangle + |010\rangle + |100\rangle + |111\rangle)

3. 应用运算 \sqrt{Z} \otimes \sqrt{Z} \otimes \sqrt{Z}，其中 \sqrt{Z} = \begin{bmatrix} 1 & 0 \\ 0 & i \end{bmatrix}，即 \sqrt{Z} |0\rangle = |0\rangle \text{且 } \sqrt{Z} |1\rangle = i |1\rangle (\text{且 } \sqrt{Z}\sqrt{Z} = Z) - \text{注意，我们在后续第 5 章中也将 Z 门的平方根称为 P 门：}

\left( \sqrt{Z} \otimes \sqrt{Z} \otimes \sqrt{Z} \right) \frac{1}{2} (|001\rangle + |010\rangle + |100\rangle + |111\rangle) = \frac{1}{2} (i |001\rangle + i |010\rangle + i |100\rangle + i(i)^2 |111\rangle) = i \frac{1}{2} (|001\rangle + |010\rangle + |100\rangle - |111\rangle)

\text{并且忽略全局相位 } i，\text{ 我们有 } \frac{1}{2} (|001\rangle + |010\rangle + |100\rangle - |111\rangle) \text{ 如所要求。}

现在我们用 \( A, B \) 和 \( C \) 运行以下算法，其中 \( H \) 是将 \( |0\rangle \) 映射到 \( \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle) \) 并将 \( |1\rangle \) 映射到 \( \frac{1}{\sqrt{2}}(|0\rangle - |1\rangle) \) 的 Hadamard 变换，且测量在标准（或计算）基中进行：

- 0. 对每个 \( p \in \{A, B, C\} \)：
- 1. 对每个 \( i \in \{1, ..., n\} \)：
- 2. 如果 \( x_i^p = 0 \) 则
- 3. 对 \( \psi_i^p \) 应用 \( H \)
- 4. 否则
- 5. 对 \( \psi_i^p \) 不做任何操作
- 6. 测量 \( \psi_i^p \) 得到比特 \( s_i^p \)
- 7. \( s^p := s_1^p \oplus ... \oplus s_n^p \)

然后，\( B \) 和 \( C \) 将它们的结果（即 \( s^B \) 和 \( s^C \)）发送到 \( A \)，\( A \) 已经拥有 \( s^A \)，并计算值 \( s^A \oplus s^B \oplus s^C \)，并且由于我们有条件 \( x^A \oplus x^B \oplus x^C = 1 \)，

\( s^A \oplus s^B \oplus s^C = f(x^A, x^B, x^C) \)

并且 \( A \) 仅通过发送两个经典比特给它就成功了。让我们看看上述等式为什么成立。

首先，我们观察到对于每个 \( i \)：

$s_i^A \oplus s_i^B \oplus s_i^C = x_i^A \cdot x_i^B \cdot x_i^C$

这是因为由于 $x^A \oplus x^B \oplus x^C = \mathbf{1}$，即 $x_i^A \oplus x_i^B \oplus x_i^C = 1$，$x_i^A, x_i^B, x_i^C$ 的值只有四种可能的组合，即 0, 0, 1 或 0, 1, 0 或 1, 0, 0 或 1, 1, 1（仅奇数个 1），并且我们可以从下表中看到，对于每个 $i$，对于 $x_i^A, x_i^B, x_i^C$ 的每个可能值，我们有 $s_i^A \oplus s_i^B \oplus s_i^C = x_i^A \cdot x_i^B \cdot x_i^C$。

| $x_i^A \cdot x_i^B \cdot x_i^C$ | 算法第 5 行后的状态 | $s_i^A \oplus s_i^B \oplus s_i^C$ |
|---|---|---|
| $0 \cdot 0 \cdot 1 = 0$ | $H \otimes H \otimes I(\rho_{ABC}) = \frac{1}{2}(|011\rangle + |101\rangle + |000\rangle - |110\rangle)$ | 0 |
| $0 \cdot 1 \cdot 0 = 0$ | $H \otimes I \otimes H(\rho_{ABC}) = \frac{1}{2}(|011\rangle + |110\rangle + |000\rangle - |101\rangle)$ | 0 |
| $1 \cdot 0 \cdot 0 = 0$ | $I \otimes H \otimes H(\rho_{ABC}) = \frac{1}{2}(|101\rangle + |110\rangle + |000\rangle - |011\rangle)$ | 0 |
| $1 \cdot 1 \cdot 1 = 1$ | $I \otimes I \otimes I(\rho_{ABC}) = \frac{1}{2}(|001\rangle + |010\rangle + |100\rangle - |111\rangle)$ | 1 |

请注意，对于每个 $i$，在选择性地应用 Hadamard 门后（表格中间列）三个量比特的状态取决于 $x_i^A, x_i^B, x_i^C$ 的四个值组合中哪些出现。

基于以上内容，我们有：

$s^A \oplus s^B \oplus s^C = (s_1^A \oplus \cdots \oplus s_n^A) \oplus (s_1^B \oplus \cdots \oplus s_n^B) \oplus (s_1^C \oplus \cdots \oplus s_n^C)$
$= (s_1^A \oplus s_1^B \oplus s_1^C) \oplus \cdots \oplus (s_n^A \oplus s_n^B \oplus s_n^C)$
$= (x_1^A \cdot x_1^B \cdot x_1^C) \oplus \cdots \oplus (x_n^A \cdot x_n^B \cdot x_n^C)$
$= f(x^A, x^B, x^C)$

这是 \( A \) 计算的值。如 Cleve 和 Buhrman [1997] 所解释，如果没有共享纠缠比特，$A$、$B$ 和 $C$ 之间两个经典比特的通信不足以让 \( A \) 计算 \( f(a,b,c) \)，并且需要通信三个经典比特。以一种有趣的方式，共享量比特似乎“取代”了一个经典比特的通信：对于这个问题，$n\) 个纠缠量比特三元组加上两个经典比特的通信等同于三个经典比特的通信！

## 3.1.1.2 分布式 Deutsch–Jozsa 承诺问题

让我们考虑另一个基于 Buhrman et al. [2010] 中的问题，与另一个称为 Deutsch–Jozsa 算法$^1$ 的问题（及其解决方案/算法）相关，如下。假设我们有 $A$ 和 $B$，$A$ 拥有一个 $n$ 位字符串 $a = a_1 \dots a_n$，$B$ 拥有一个 $n$ 位字符串 $b = b_1 ... b_n$。问题是确定 (1) $a = b$，或 (2) $a$ 和 $b$ 在恰好 $n/2$ 个位置上不同，其中 $n$ 为偶数（在此，我们还假设 $n$ 是 2 的幂），并且这是一个 *承诺问题*，这意味着它不适用于所有字符串对 $(x,y) \in \{0, 1\}^n \times \{0, 1\}^n$，而仅适用于 (1) 或 (2) 为真的那些对（显然，对于给定的字符串对，两者不能同时为真）。

求解此问题的一个算法如下，假设 $n = 2^l$（或 $l = \log_2 n$）：

- 1. $B$ 使用 $b$ 和 $l$ 个 $|0\rangle$-量比特，制备状态 $\frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} |i\rangle$；请注意，这里的想法是将 $b$ 中的 $n$ 位信息编码在 $l$ 量比特状态的 $n$ 个分量的“符号”（即 $(-1)^{b_i}$）中（由于 $l \ll 2^l$，我们试图“侥幸”通过传输更少的比特）。这可以按以下方式完成：(i) 在 $l$ 个 $|0\rangle$-量比特上应用 $H^{\otimes l}$ 以获得状态 $\frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} |i\rangle$；例如，对于 $n = 2^3$，$H \otimes H \otimes H |000\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle) \otimes \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle) = \frac{1}{\sqrt{2^3}} \sum_{i=0}^{2^3-1} |i\rangle$ (ii) 假设存在一个作用于 $(l + 1)$ 个量比特的单位运算 $U_b$，它将 $|i\rangle |p\rangle$ 映射到 $|i\rangle |p \oplus b_i\rangle$（参见 **旁注**）。

> **旁注：** $U_b$ 是单位的，即 $U_b^\dagger U_b = I$，如我们现在所示。请注意，对于 $i \in \{0, 1\}^l$ 和 $b \in \{0, 1\}$ 的状态 $|i\rangle|p\rangle$ 构成一组基，并设 \(|\psi\rangle = \sum_{i \in \{0, 1\}^l, p \in \{0, 1\}} \alpha_{l,p} |i\rangle|p\rangle\)，则：
> $$ \langle \psi | U_b^\dagger U_b | \psi \rangle $$
> $$ = (U_b | \psi \rangle)^\dagger U_b | \psi \rangle $$
> $$ = \left( U_b \left( \sum_{i \in \{0, 1\}^l, p \in \{0, 1\}} \alpha_{l,p} |i\rangle|p\rangle \right) \right)^\dagger U_b \left( \sum_{i \in \{0, 1\}^l, p \in \{0, 1\}} \alpha_{l,p} |i\rangle|p\rangle \right) $$
> $$ = \left( \sum_{i \in \{0, 1\}^l, p \in \{0, 1\}} \alpha_{l,p} U_b |i\rangle |p\rangle \right)^\dagger \left( \sum_{i \in \{0, 1\}^l, p \in \{0, 1\}} \alpha_{l,p} U_b |i\rangle |p\rangle \right) $$
> $$ = \left( \sum_{i \in \{0, 1\}^l, p \in \{0, 1\}} \alpha_{l,p} |i\rangle |p \oplus b_i\rangle \right)^\dagger \left( \sum_{i \in \{0, 1\}^l, p \in \{0, 1\}} \alpha_{l,p} |i\rangle |p \oplus b_i\rangle \right) $$
> $$ = \sum_{i \in \{0,1\}^l, p \in \{0,1\}} \alpha_{l,p}^2 \langle i | \langle p \oplus b_i | i \rangle | p \oplus b_i \rangle $$
> $$ = \sum_{i \in \{0,1\}^l, p \in \{0,1\}} \alpha_{l,p}^2 = \langle \psi | \psi \rangle $$

$^1$ 请注意，原始 Deutsch–Jozsa 问题是确定给定函数（例如 $f : \{0, 1\}^n \mapsto \{0, 1\}$）是常数（对所有输入返回 0 或对所有输入返回 1）还是平衡（对一半输入返回 0 且对另一半输入返回 1），并且我们承诺该函数是这两者之一。解决方案见 https://en.wikipedia.org/wiki/Deutsch-Jozsa_algorithm。

