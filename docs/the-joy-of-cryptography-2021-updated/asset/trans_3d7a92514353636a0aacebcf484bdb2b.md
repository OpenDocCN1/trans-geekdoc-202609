

攻击 $F$ 意味着设计一个区分者，使其在两个 $\mathcal{L}^F_{\text{prf-}\star}$ 库的存在下表现得尽可能不同。我们要表明即使 $G$ 是一个优秀的 PRG，$F$ 也是不安全的。我们不应试图将攻击建立在区分 $G$ 的输出与随机值的基础上。相反，我们必须尝试**破坏构建 PRF 时使用 $G$ 的不当方式**来构建一个 PRF。

区分者必须使用 $\mathcal{L}_{\text{prf-}\star}$ 库的接口——即，对 LOOKUP 子程序进行一些调用，并根据得到的答案输出 0 或 1。LOOKUP 子程序接受一个参数，因此区分者必须选择使用哪些参数。

我们可以做出的一个观察是，如果调用程序只看到一个形式为 $G(k) \oplus x$ 的值，它将看起来是伪随机的。这基本上就是我们在第 5.3 节中展示的内容。因此，我们应该寻找一个对 LOOKUP 进行不止一次调用的调用程序。

如果我们对 LOOKUP 进行两次调用——例如，在输入 $x_1$ 和 $x_2$ 上——来自 $\mathcal{L}^F_{\text{prf-real}}$ 的响应将是 $G(k) \oplus x_1$ 和 $G(k) \oplus x_2$。要成为一个安全的 PRF，这些响应必须看起来是独立且均匀的。为什么？它们实际上有一个调用程序可以注意到的模式：它们的异或始终是 $x_1 \oplus x_2$，这是调用程序已经知道的值。

我们可以将所有观察结果浓缩为以下区分者：

```
$\mathcal{A}$
pick $x_1, x_2 \in \{0, 1\}^{2\lambda}$ arbitrarily so that $x_1 \neq x_2$
$z_1 := \text{LOOKUP}(x_1)$
$z_2 := \text{LOOKUP}(x_2)$
return $z_1 \oplus z_2 \stackrel{?}{=} x_1 \oplus x_2$
```

让我们通过考虑 $\mathcal{A}$ 与这两个库链接时的行为，来计算它在区分 $\mathcal{L}^F_{\text{prf-real}}$ 与 $\mathcal{L}^F_{\text{prf-rand}}$ 方面的优势：

| $\mathcal{A}$ | $\mathcal{L}^F_{\text{prf-real}}$ |
| :--- | :--- |
| pick $x_1 \neq x_2 \in \{0, 1\}^{2\lambda}$<br>$z_1 := \text{LOOKUP}(x_1)$<br>$z_2 := \text{LOOKUP}(x_2)$<br>return $z_1 \oplus z_2 \stackrel{?}{=} x_1 \oplus x_2$ | $k \leftarrow \{0, 1\}^\lambda$<br>LOOKUP(x):<br>return $G(k) \oplus x$ // $F(k, x)$ |

当 $\mathcal{A}$ 与 $\mathcal{L}^F_{\text{prf-real}}$ 链接时，库将选择一个密钥 $k$。然后 $z_1$ 设置为 $G(k) \oplus x_1$，$z_2$ 设置为 $G(k) \oplus x_2$。因此 $z_1 \oplus z_2$ 始终等于 $x_1 \oplus x_2$，且 $\mathcal{A}$ 始终输出 1。即，

$\Pr[\mathcal{A} \diamond \mathcal{L}^F_{\text{prf-real}} \Rightarrow 1] = 1$.

| $\mathcal{A}$ | $\mathcal{L}^F_{\text{prf-rand}}$ |
| :--- | :--- |
| pick $x_1 \neq x_2 \in \{0, 1\}^{2\lambda}$<br>$z_1 := \text{LOOKUP}(x_1)$<br>$z_2 := \text{LOOKUP}(x_2)$<br>return $z_1 \oplus z_2 = x_1 \oplus x_2$ | $T :=$ empty assoc. array<br>LOOKUP(x):<br>if $T[x]$ undefined:<br>$T[x] \leftarrow \{0, 1\}^{2\lambda}$<br>return $T[x]$ |

当 $\mathcal{A}$ 与 $\mathcal{L}^F_{\text{prf-rand}}$ 链接时，两次 LOOKUP 调用的响应将被均匀且独立地选择，因为 LOOKUP 是在不同的输入上被调用的。考虑第二次 LOOKUP 调用即将发生的时刻。此时，$x_1$、$x_2$ 和 $z_1$ 已经全部确定，而 $z_2$ 即将由库均匀选择。利用异或的性质，我们可以看到，$\mathcal{A}$ 将当且仅当 $z_2$ 被选择为恰好是值 $x_1 \oplus x_2 \oplus z_1$ 时输出 1。这种情况发生的概率仅为 $1/2^{2\lambda}$。即，

$\Pr[\mathcal{A} \diamond \mathcal{L}^F_{\text{prf-rand}} \Rightarrow 1] = 1/2^{2\lambda}$.

因此 $\mathcal{A}$ 的优势为 $1 - 1/2^{2\lambda}$，这无疑是非可忽略的，因为它甚至不趋近于 0。这表明 $F$ 不是一个安全的 PRF。

从更哲学的角度来看，我们想要识别 $G$ 被以不当方式使用的精确所在。PRG 安全库保证当 $G$ 的种子为每次对 $G$ 的调用重新选择时是安全的。$F$ 的这种构造违反了该规则，并允许相同的种子在对 $G$ 的不同调用中被使用两次，而结果应当看起来是独立的。

这个例子展示了构建 PRF 的挑战。尽管我们知道如何使任何单个输出看起来是伪随机的，但要使所有输出整体上看起来是独立的，而在现实中它们却派生自单个短种子，这是困难的。

## 6.2 PRFs 与 PRGs；变量混合证明

在本节中，我们将展示 PRG 可用于构建 PRF，**反之亦然**。从 PRF 构建 PRG 是实用的，也是在实践中获得 PRG 的更常见方式之一。从 PRG 构建 PRF 更多的是理论兴趣，并不反映 PRF 在实践中的设计方式。

### 从 PRF 构建 PRG

如承诺，PRF 可用于构建 PRG。这种构造非常自然。为简单起见，假设我们有一个 PRF $F : \{0, 1\}^\lambda \times \{0, 1\}^\lambda \to \{0, 1\}^\lambda$（_即，输入 = 输出 = $\lambda$_）。我们可以如下构建一个长度翻倍的 PRG：

| 构造 6.2（计数器 PRG） |
| --- |
| $G(s)$: |
| $x := F(s, 0\cdots 00)$ |
| $y := F(s, 0\cdots 01)$ |
| return $x\|y$ |

传给 $F$ 的输入 $0\cdots 00$ 和 $0\cdots 01$ 并没有什么特别之处。重要的是它们互不相同。该构造可以扩展以轻松给出超过 2 个输出块，通过将 $F$ 的输入视为一个简单的计数器（因此得名此构造）。

PRF 的保证是，当其种子被均匀选择并且在不同的输入上被调用时，其输出看起来是独立且均匀的。特别是，其在输入 $0\cdots 00$ 和 $0\cdots 01$ 上的输出与均匀输出不可区分。因此，将它们拼接得到一个与均匀 $2\lambda$ 比特字符串不可区分的字符串。

这其实就是该构造安全性的全部内容，但不幸的是，有一个小的技术问题使得安全证明比你可能猜想的更加复杂。我们将不得不引入一种新的**变量混合**技术来应对它。

**主张 6.3** 如果 $F$ 是一个安全的 PRF，那么上述计数器 PRG 构造 $G$ 是一个安全的 PRG。

**证明** 为了证明 $G$ 是一个安全的 PRG，我们必须证明以下库是不可区分的：

```
$\mathcal{L}^G_{\text{prg-real}}$
QUERY():
$s \leftarrow \{0, 1\}^\lambda$
$x := F(s, 00\cdots 00)$
$y := F(s, 00\cdots 01)$
return $x\|y$   // $G(s)$
```

```
$\mathcal{L}^G_{\text{prg-rand}}$
QUERY():
$r \leftarrow \{0, 1\}^{2\lambda}$
return $r$
```

在证明过程中，我们可以使用 $F$ 是一个安全的 PRF 这一事实。也就是说，我们可以使用以下两个库是不可区分的这一事实：

```
$\mathcal{L}^F_{\text{prf-real}}$
$k \leftarrow \{0, 1\}^\lambda$
LOOKUP($x \in \{0, 1\}^\text{in}$):
return $F(k, x)$
```

```
$\mathcal{L}^F_{\text{prf-rand}}$
$T :=$ empty assoc. array
LOOKUP($x \in \{0, 1\}^\text{in}$):
if $T[x]$ undefined:
  $T[x] \leftarrow \{0, 1\}^\text{out}$
return $T[x]$
```

证明中的不便之处源于 $\mathcal{L}^G_{\text{prg-real}}$ 中的 $s$ 变量与 $\mathcal{L}^F_{\text{prf-real}}$ 中的 $k$ 变量的不匹配。在 $\mathcal{L}^G_{\text{prg-real}}$ 中，$s$ 是 QUERY 子程序的局部变量。在执行过程中，$s$ 将取许多值。由于 $s$ 被用作 PRF 种子，我们必须用 $\mathcal{L}^F_{\text{prf-real}}$ 的 LOOKUP 子程序来写对 $F$ 的调用。但在 $\mathcal{L}^F_{\text{prf-real}}$ 中，PRF 种子在整个执行过程中是固定的。换句话说，我们一次只能使用 $\mathcal{L}^F_{\text{prf-real}}$ 来处理单个 PRF 种子，但 $\mathcal{L}^G_{\text{prg-real}}$ 同时处理许多 PRG 种子。

为了解决这个问题，在证明过程中我们将不得不多次应用 $F$ 的安全性（即，用 $\mathcal{L}^F_{\text{prf-rand}}$ 替换 $\mathcal{L}^F_{\text{prf-real}}$）——事实上，对调用程序进行的每次 QUERY 调用都要应用一次。先前的安全证明具有固定数量的混合步骤（例如，主张 5.5 的证明使用了 7 个混合库来显示 $\mathcal{L}^G_{\text{prg-real}} \approx \mathcal{L}_{\text{hyb-1}} \approx \dots \approx \mathcal{L}_{\text{hyb-7}} \approx \mathcal{L}^G_{\text{prg-rand}}$）。本证明将拥有一个**依赖于调用程序的变量数量的混合**。具体来说，我们将证明

$$\mathcal{L}^G_{\text{prg-real}} \approx \mathcal{L}_{\text{hyb-1}} \approx \dots \approx \mathcal{L}_{\text{hyb-}q} \approx \mathcal{L}^G_{\text{prg-rand}},$$

其中 $q$ 是调用程序调用 QUERY 的次数。

