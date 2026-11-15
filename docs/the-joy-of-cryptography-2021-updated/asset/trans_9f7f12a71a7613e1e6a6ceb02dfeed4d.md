

```
\mathcal{L}^\Sigma_{\text{aead\$ -real}}
k \leftarrow \Sigma.\text{KeyGen}
\mathcal{S} := \emptyset
\text{CTXT}(d \in \Sigma.\mathcal{D}, m \in \Sigma.\mathcal{M}):
c := \Sigma.\text{Enc}(k, d, m)
\mathcal{S} := \mathcal{S} \cup \{(d, c)\}
return c
\text{DECRYPT}(d \in \Sigma.\mathcal{D}, c \in \Sigma.\mathcal{M}):
if (d, c) \in \mathcal{S}: return \text{err}
return \Sigma.\text{Dec}(k, d, c)
```

```
\mathcal{L}^\Sigma_{\text{aead\$ -fake}}
\text{CTXT}(d \in \Sigma.\mathcal{D}, m \in \Sigma.\mathcal{M}):
c \leftarrow \Sigma.C(|m|)
return c
\text{DECRYPT}(d \in \Sigma.\mathcal{D}, c \in \Sigma.\mathcal{M}):
return \text{err}
```

### Discussion

将消息与某个上下文 \(d\) 进行认证的一种方法，是在 AE 方案中加密 \(m||d\) 而非仅加密 \(m\)。这确实可行！将 \(d\) 作为明文的一部分确实可以对其进行认证，但也会 _隐藏_ 它。区分明文和关联数据的要点在于，我们假设关联数据是两个参与者之间的 _共享上下文_。换句话说，我们假设发送方和接收方都已经知道上下文 \(d\)。因此，_隐藏 \(d\) 属于过度处理 — 只需要认证即可。通过在 AEAD 中分别区分明文和关联数据，**密文长度只能取决于明文的长度**，而不取决于关联数据的长度。

关联数据 \(d\) 是公开的这一事实，体现在安全定义中由调用程序选择它。

“标准” AE 对应于 \(d\) 始终为空的情况：所有密文都认证到相同的上下文。

## 12.2 实现 AE/AEAD

Encrypt-then-MAC 构造（构造 10.9）具有攻击者无法生成能正确解密的密文的特性。尽管我们引入 encrypt-then-MAC 是为了实现 CCA 安全，但它也实现了更强的 AE 要求。

**主张 12.3** _如果 E 具有 CPA 安全且 M 是一个安全的 MAC，那么 EtM（构造 10.9）具有 AE 安全。_

> to-do
> _这里存在轻微的不匹配，因为我将 AE/AEAD 安全定义为一种“伪随机密文”风格的定义。因此，你实际上需要 CPA$+PRF 而不是 CPA+MAC。但 CPA+MAC 对于左右取样式的 AE/AEAD 安全已经足够。_

安全证明本质上与 CCA 安全的证明（主张 12.5）相同。在该证明中，存在一个混合，其中 DECRYPT 子例程始终返回错误。在该点停止证明将得到 AE 安全的证明。

### 带关联数据的先加密后 MAC

回顾，先加密后 MAC 构造计算密文的 MAC。要融入关联数据，我们只需将密文与关联数据一起计算 MAC。

回顾，实践中大多数 MAC 支持变长输入，但 MAC 标签的长度不取决于消息的长度。因此，这种新的先加密后 MAC 变体具有密文，其长度不取决于关联数据的长度。

```
Construction 12.4
(Enc+MAC+AD)

Enc((k_e, k_m), d, m):
  c <- E.Enc(k_e, m)
  t := M.MAC(k_m, d || c)
  return (c, t)

Dec((k_e, k_m), d, (c, t)):
  if t != M.MAC(k_m, d || c):
    return err
  return E.Dec(k_e, c)
```

Claim 12.5
如果 E 具有 CPA 安全且 M 是一个安全的 MAC，那么构造 12.4 具有 AEAD 安全性，前提是关联数据具有固定长度（即，D = {0, 1}^n，其中 n 为某个固定值）。

> to-do
> 该构造对于变长关联数据是不安全的。修复这一点并不十分困难；参见练习。

## 12.3 Carter-Wegman MACs

假设我们使用先加密后 MAC 范式构建一个 AE[AD] 方案。CPA 安全加密方案的良好选择是 CBC 模式；MAC 方案的良好选择是 ECBC-MAC。结合这两个构建块将产生一个 AE[AD] 方案，该方案对每个明文块调用两次块密码——一次用于 CBC 加密（应用于明文），另一次用于 ECBC-MAC（应用于该密文块）。

是否可以以更低的成本实现 AE[AD]？在本节中，我们将探讨一种针对变长 MAC 的更高效技术，该技术只需要每个消息块执行一次乘法操作，并伴随一次块密码调用。

### 通用哈希函数

Carter-Wegman 风格 MAC 中的主要构建块是一种称为通用哈希函数（UHF）的哈希函数。虽然“通用哈希函数”这个名字听起来一定是一种极其强大的原语，但 UHF 实际上提供的安全保证远比抗碰撞或第二前像抗性哈希函数要弱。

回顾，如果 \(x \neq x'\) 且 \(H(s, x) = H(s, x')\)，则 \((x, x')\) 是盐 \(s\) 下的碰撞。通用哈希函数的特性在于，找到这样的碰撞是困难的 ...

... 当 \(x\) 和 \(x'\) 在不知道盐的情况下被选择时，

... 并且当攻击者只有一次机会为某个特定的盐值寻找碰撞时。

这些约束相当于在 \(x\) 和 \(x'\) 被选择后再选择盐，并且在这种情况下碰撞应该是可忽略的。

定义可以更正式地表述：

### 定义 12.6 (UHF) 具有盐集合 \(S\) 的哈希函数 \(H\) 称为 **通用哈希函数 (UHF)**，如果 \(L_{\text{uhf-real}}^H \cong L_{\text{uhf-fake}}^H\)，其中：

```
L_uhf-real^H
TEST(x, x' ∈ {0, 1}*):
  s ← S
  b := [ H(s, x) =? H(s, x') ]
  return (s, b)
```

```
L_uhf-fake^H
TEST(x, x' ∈ {0, 1}*):
  s ← S
  return (s, false)
```

该定义在精神上与抗碰撞性的正式定义（定义 11.1）相似。就像那个定义一样，这个定义在安全证明中使用起来很麻烦。在使用哈希函数时，人们通常不会显式地检查碰撞，而是直接假设没有碰撞发生。

在 UHF 的情况下，有一种不同且有用的安全思考方式。考虑一个 **“盲抗碰撞性”** 游戏，你试图在没有盐访问权限，甚至 _看不到 H 的输出_ 的情况下找到 \(H\) 下的碰撞！结果表明，如果 \(H\) 是 UHF，那么在这种游戏中找到碰撞是困难的：

### 主张 12.7 如果 \(H\) 是 UHF，那么以下库不可区分：

```
L_bcr-real^H
s ← S
H_inv := empty assoc. array
TEST(x ∈ {0, 1}*):
  y := H(s, x)
  if H_inv[y] defined and H_inv[y] ≠ x:
    return H_inv[y]
  H_inv[y] := x
  return false
```

```
L_bcr-fake^H
TEST(x ∈ {0, 1}*):
  return false
```

在这些库中，调用程序为 UHF 选择输入 \(x\)。\(L_{\text{bcr-real}}\) 库以反向查找表的形式维护所有 \(x\) 值及其哈希的私有记录。\(H_{\text{inv}}[y]\) 将保存被哈希得到 \(y\) 的 \(x\) 值。

如果调用程序对与先前 \(x'\) 发生碰撞的值调用 \(\text{TEST}(x)\)，那么 \(L_{\text{bcr-real}}\) 将响应这个 \(x'\) 值（这样做的目的只是对使用这些库的安全证明有所帮助）；否则它将响应 \(\text{false}\)，不提供关于 \(s\) 或 \(H(s, x)\) 的任何信息。另一个库始终响应 \(\text{false}\)。因此，两者不可区分的前提是找到碰撞很困难。

to-do 即将给出证明。这不难，但很繁琐。

### 使用多项式构建 UHF

与其他类型的哈希相比，UHF 的安全性要弱得多，而且它们实际上可以无条件构建。在数学上最简单的构建之一与多项式有关。

**主张 12.8** 设 \(p\) 为一个素数，\(g\) 为系数在 \(\mathbb{Z}_p\) 中且次数至多为 \(d\) 的非零多项式。那么 \(g\) 在 \(\mathbb{Z}_p\) 中至多有 \(d\) 个零点。

这一观察导致了一个简单的 UHF 构建，其思路是将字符串 \(x\) 解释为多项式的系数，并在点 \(s\)（UHF 的盐）处求值该多项式。更详细地说，设 \(p\) 为满足 \(p > 2^\lambda\) 的素数，并令盐 \(s\) 为 \(\mathbb{Z}_p\) 中均匀选择的元素。要计算 \(x\) 的哈希，首先将 \(x\) 分割为 \(\lambda\) 比特块，以便索引为 \(x_{d-1} || x_{d-2} \cdots || x_0\)。将每个 \(x_i\) 解释为模 \(p\) 的数。然后，哈希值 \(H(s, x)\) 为：

\( s^d + x_{d-1}s^{d-1} + x_{d-2}s^{d-2} + \cdots + x_0 \pmod p \)

这是在点 \(s\) 处求系数为 \((1, x_{d-1}, x_{d-2}, \ldots, x_0)\) 的多项式的结果。求值该多项式的一种方便方法是使用 **Horner 法则：**

\( \cdots \cdot s \cdot (s \cdot (s + x_{d-1}) + x_{d-2}) + x_{d-3} \cdots \)

Horner 法则可以直观地表示如下：

![](img/da79fa21b263fe549aecaabd2a0a41c8_230_0.png)

UHF 构建在下面正式描述。

```
Construction 12.9 (Poly-UHF)

\(\underline{H(s, x):}\)
write \(x = x_{d-1} || x_{d-2} || \cdots || x_0\),
where each \(|x_i| = \lambda\)

\(p = \) a prime \(> 2^\lambda\)
\(\mathcal{S} = \mathbb{Z}_p\)

\(y := 1\)
for \(i = d - 1\) downto 0:
  \(y := s \cdot y + x_i \% p\)
return \(y\)
```

**主张 12.10** Poly-UHF 构建是一个安全的 UHF。

**证明** 只需证明，对于任何 \(x \neq x'\)，\(H(s, x) = H(s, x')\) 的概率（关于随机选择的 \(s\)）是可忽略的。注意 \(H(s, x) = g(s)\)，其中 \(g\) 是系数为 \((1, x_{d-1}, \ldots, x_0)\) 的多项式，而 \(H(s, x') = g'(s)\)，其中 \(g'\) 是从 \(x'\) 推导出的类似多项式。注意 \(x\) 和 \(x'\) 可能被分割成不同数量的块，导致两个多项式的次数（\(d\) 和 \(d'\)）不同。

