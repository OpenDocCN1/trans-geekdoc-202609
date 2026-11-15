

## Exercises

14.1. 记 \( p \) 为奇素数，如常。回顾 \(\text{QR}_p^*\) 是模 \( p \) 的二次剩余集合——即，\(\text{QR}_p^* = \{x \in \mathbb{Z}_p^* \mid \exists y : x \equiv_p y^2\}\)。证明，若 \( g \) 是 \(\mathbb{Z}_p^*\) 的原根，则 \(\langle g^2 \rangle = \text{QR}_p^*\)。

*Note:* 这意味着 \( g^a \in \text{QR}_p^*\) 当且仅当 \( a \) 为偶数——特别是，生成元 \( g \) 的选择无关紧要。

14.2. 假设 \( N = pq \)，其中 \( p \) 和 \( q \) 为不同素数。证明 \( |\text{QR}_N^*| = |\text{QR}_p^*| \cdot |\text{QR}_q^*|\)。

提示：

14.3. 假设已知 \( X \in \langle g \rangle \)。你可以任意选择 \( X' \neq X \) 并得知 \( X' \) 关于底数 \( g \) 的离散对数。证明你可以利用此能力求得 \( X \) 的离散对数。

14.4. 设 \(\langle g \rangle\) 为具有 \( n \) 个元素的循环群，生成元为 \( g \)。证明对任意整数 \( a \)，均有 \( g^a = g^{a \% n} \)。

*Note:* 因此，\(\langle g \rangle\) 与加法群 \(\mathbb{Z}_n\) 同构。

14.5. 设 \( g \) 为 \(\mathbb{Z}_n^*\) 的原根。回顾 \(\mathbb{Z}_n^*\) 有 \(\phi(n)\) 个元素。证明 \( g^a \) 是 \(\mathbb{Z}_n^*\) 的原根当且仅当 \(\gcd(a, \phi(n)) = 1\)。

*Note:* 由此可见，对任意 \( n \)，模 \( n \) 的原根个数要么为 0，要么为 \(\phi(\phi(n))\)。

14.6. 设 \(\langle g \rangle\) 为具有 \( n \) 个元素的循环群。证明对任意 \( x, y \in \langle g \rangle \)，均有 \( x^n = y^n \)。

提示：

14.7.
- (a) 证明 Lemma 4.10 的如下变体：假设固定一个值 \( x \in \mathbb{Z}_N \)。则从 \(\mathbb{Z}_N\) 中均匀采样 \( q = \sqrt{2N} \) 个值 \( r_1, \dots, r_q \) 时，至少有 0.6 的概率存在 \( i \neq j \) 使得 \( r_i \equiv_N r_j + x \)。

- (b) 设 \( g \) 为 \(\mathbb{Z}_p^*\)（某素数 \( p \) 下）的原根。考虑计算 \( X \in \mathbb{Z}_p^*\) 关于 \( g \) 的离散对数问题——即，找到 \( x \) 使得 \( X \equiv_p g^x \)。论证若能找到整数 \( r \) 和 \( s \) 使得 \( g^r \equiv_p X \cdot g^s \)，则可求得 \( X \) 的离散对数。

- (c) 结合上述两点观察，描述一个 \( O(\sqrt{p}) \) 时间算法，用于求解 \(\mathbb{Z}_p^*\) 中的离散对数问题。

14.8. 在 DHKA 执行过程中，窃听者观察到以下值：

\( p = 461733370363 \quad A = 114088419126 \)
\( g = 2 \quad \quad \quad \quad \quad B = 276312808197 \)

Alice 和 Bob 的共享密钥是多少？

14.9. 解释以下论证的错误之处：

在 Diffie-Hellman 密钥交换中，Alice 发送 \(A = g^a\)，Bob 发送 \(B = g^b\)。它们的共享密钥是 \(g^{ab}\)。要破解该方案，窃听者可以直接计算 \(A \cdot B = (g^a)(g^b) = g^{ab}\)。

14.10. 设 \(\mathbb{G}\) 为具有 \( n \) 个元素的循环群，生成元为 \( g \)。考虑以下算法：

```
RAND(A, B, C):
r, s, t \leftarrow \mathbb{Z}_n
A' := A^t g^r
B' := B g^s
C' := C B' A^{st} g^{rs}
return (A', B', C')
```

令 \(DH = \{(g^a, g^b, g^{ab}) \in \mathbb{G}^3 \mid a, b \in \mathbb{Z}_n\}\)。

- (a) 假设 \((A, B, C) \in DH\)。证明 \(\text{RAND}(A, B, C)\) 的输出分布是 \(DH\) 上的均匀分布。

- (b) 假设 \((A, B, C) \notin DH\)。证明 \(\text{RAND}(A, B, C)\) 的输出分布是 \(\mathbb{G}^3\) 上的均匀分布。

- ★ (c) 考虑判定给定三元组 \((A, B, C)\) 是否属于集合 \(DH\) 的问题。假设你有一个算法 \(\mathcal{A}\)，该算法平均解决此问题的成功率略好于随机猜测。即：

```
Pr[\mathcal{A}(A, B, C) = 1] > 0.51 when (A, B, C) chosen uniformly in DH
Pr[\mathcal{A}(A, B, C) = 0] > 0.51 when (A, B, C) chosen uniformly in \mathbb{G}^3
```

如果你有一个*特定*的三元组 \((A, B, C)\) 并真正想知道它是否属于 \(DH\)，算法 \(\mathcal{A}\) 似乎不太有用。你可能恰好拥有一个 \(\mathcal{A}\) 给出错误答案的三元组，并且无法真正得知这一点。

展示如何构建一个随机算法 \(\mathcal{A}'\)，使得对每个 \((A, B, C) \in \mathbb{G}^3\)：

```
Pr [\mathcal{A}'(A, B, C) = [(A, B, C) \in DH]] > 0.99
```

此处输入 \(A, B, C\) 固定，概率取自 \(\mathcal{A}'\) 内部的随机性。因此，在*每个*可能的输入上，\(\mathcal{A}'\) 都会给出非常可靠的答案。

## 15 公钥加密

迄今为止，我们所见的加密方案均为**对称密钥**方案。同一个密钥既用于加密也用于解密。本章介绍**公钥**（有时也称为*非对称*）加密方案，其加密与解密使用不同的密钥。其理念是加密密钥可以*公开*，这样任何人都可以向该密钥的所有者发送加密消息，即使两位用户从未通信过且没有共享秘密。解密密钥是私有的，因此只有指定的所有者才能解密。

我们按如下方式修改加密方案的语法。公钥加密方案由以下三个算法组成：

KeyGen：输出一对 \((pk, sk)\)，其中 \(pk\) 是公钥，\(sk\) 是私钥/秘密密钥。

Enc：接收公钥 \(pk\) 和明文 \(m\) 作为输入，输出密文 \(c\)。

Dec：接收密钥 \(sk\) 和密文 \(c\) 作为输入，输出明文 \(m\)。

我们以类似方式修改正确性条件。公钥加密方案满足*正确性*的条件是：对所有 \(m \in \mathcal{M}\) 和所有 \((pk, sk) \leftarrow \mathsf{KeyGen}\)，有 \(\mathsf{Dec}(sk, \mathsf{Enc}(pk, m)) = m\)（随 Enc 的随机性，概率为 1）。

### 15.1 安全定义

我们现在修改 CPA 安全的定义以适应公钥加密设置。与之前一样，对手会使用两个明文调用 CHALLENGE 子例程——两个库的区别在于哪个明文实际被加密。当然，加密操作现在接收公钥。

最大的变化是我们希望让公钥*公开*。换句话说，调用程序应有一种方式来获取公钥（否则该库无法模拟公钥已知于对手的情形）。为此，我们只需添加另一个返回公钥的子例程。

定义 15.1 设 \(\Sigma\) 为公钥加密方案。若 \(\mathcal{L}^\Sigma_{\text{pk-cpa-L}} \approx \mathcal{L}^\Sigma_{\text{pk-cpa-R}}\)，则称 \(\Sigma\) 是**抗选明文攻击安全（CPA 安全）**的，其中：

| \(\mathcal{L}^\Sigma_{\text{pk-cpa-L}}\) | \(\mathcal{L}^\Sigma_{\text{pk-cpa-R}}\) |
|---|---|
| \((pk, sk) \leftarrow \Sigma.\text{KeyGen}\)<br>GETPK(): 返回 \(pk\)<br>CHALLENGE(\(m_L, m_R \in \Sigma.\mathcal{M}\)): 返回 \(\Sigma.\text{Enc}(pk, m_L)\) | \((pk, sk) \leftarrow \Sigma.\text{KeyGen}\)<br>GETPK(): 返回 \(pk\)<br>CHALLENGE(\(m_L, m_R \in \Sigma.\mathcal{M}\)): 返回 \(\Sigma.\text{Enc}(pk, m_R)\) |

**待办事项** 再次论述如何证明确定性加密在公钥设置下仍不能满足 CPA 安全。

### 伪随机密文

我们可以以类似方式修改/调整伪随机密文的定义以适用于公钥加密：

**定义 15.2** *设* \(\Sigma\) *为公钥加密方案。则* \(\Sigma\) *具有**选择明文攻击下的伪随机密文（CPA$ 安全）**，当且仅当* \(\mathcal{L}^\Sigma_{\text{pk-cpa\$-real}} \approx \mathcal{L}^\Sigma_{\text{pk-cpa\$-rand}}\)*，其中：*

| \(\mathcal{L}^\Sigma_{\text{pk-cpa\$-real}}\) | \(\mathcal{L}^\Sigma_{\text{pk-cpa\$-rand}}\) |
|---|---|
| \((pk, sk) \leftarrow \Sigma.\text{KeyGen}\)<br>GETPK(): 返回 \(pk\)<br>CHALLENGE(\(m \in \Sigma.\mathcal{M}\)): 返回 \(\Sigma.\text{Enc}(pk, m)\) | \((pk, sk) \leftarrow \Sigma.\text{KeyGen}\)<br>GETPK(): 返回 \(pk\)<br>CHALLENGE(\(m \in \Sigma.\mathcal{M}\)): \(c \leftarrow \Sigma.\mathcal{C}\)<br>返回 \(c\) |

与对称密钥设置一样，公钥加密的 CPA$ 安全意味着 CPA 安全：

**主张 15.3** *设* \(\Sigma\) *为公钥加密方案。若* \(\Sigma\) *具有 CPA$ 安全，则* \(\Sigma\) *具有 CPA 安全。*

证明与对称密钥加密中类似陈述（定理 7.3）的证明极为相似，且留作练习。

### 15.2 一次性安全意味着多次性安全

迄今为止，公钥加密的一切都与我们在对称密钥加密中看到的直接类似。我们现在讨论一个在两种设置之间不同的独特性质。

