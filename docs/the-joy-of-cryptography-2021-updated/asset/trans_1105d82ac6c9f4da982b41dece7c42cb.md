

SALVIATI: 哦，西普利西奥，你现在变得烦人了！这个值 $r$ 是 $\lambda$ 比特长，每次均匀随机选择。你不记得我们关于生日悖论的漫长讨论了吗？

SIMPLICIO: 哦对，现在我记清楚了。现在我相信我理解了你的所有推理：在所有生成的密文中，$r$ 不太可能重复，因为生日悖论。现在，只要 $r$ 从不重复，Alice 就在不同的输入上调用 PRF。在不同输入上调用的 PRF 提供的输出在各方面均为均匀随机。因此，将这些输出作为一次性密钥完全隐藏了明文。对吗，萨尔维亚蒂？

SALVIATI: 太棒了！现在我们可以回到讨论太阳和地球的运动了 . . .

请查看西普利西奥的最终总结，它将在正式证明使用的混合体序列中体现出来：

证明 我们使用混合体技术证明 \(\mathcal{L}^\Sigma_{\text{cpa\$-real}} \approx \mathcal{L}^\Sigma_{\text{cpa\$-rand}}\)：

```
\mathcal{L}^\Sigma_{\text{cpa\$-real}}

k \leftarrow \{0, 1\}^\lambda

\underline{\text{CTXT}(m)}:
  r \leftarrow \{0, 1\}^\lambda
  x := F(k, r) \oplus m
  return (r, x)
```

起点是 \(\mathcal{L}^\Sigma_{\text{cpa\$-real}}\)。\(\Sigma\) 的细节已填入并高亮。

```
\underline{\text{CTXT}(m)}:
  r \leftarrow \{0, 1\}^\lambda
  z := \text{LOOKUP}(r)
  x := z \oplus m
  return (r, x)
```

```
\mathcal{L}^F_{\text{prf-real}}

k \leftarrow \{0, 1\}^\lambda

\underline{\text{LOOKUP}(r)}:
  return F(k, r)
```

与 PRF 相关的语句已按 \(\mathcal{L}^F_{\text{prf-real}}\) 库的形式提取出来。

```
\underline{\text{CTXT}(m)}:
  r \leftarrow \{0, 1\}^\lambda
  z := \text{LOOKUP}(r)
  x := z \oplus m
  return (r, x)
```

```
\mathcal{L}^F_{\text{prf-rand}}

T := empty

\underline{\text{LOOKUP}(r)}:
  if T[r] undefined:
    T[r] \leftarrow \{0, 1\}^\text{out}
    return T[r]
```

我们已将 \(\mathcal{L}^F_{\text{prf-real}}\) 替换为 \(\mathcal{L}^F_{\text{prf-rand}}\)。根据 F 的 PRF 安全性，这两个混合体不可区分。

在证明的这个阶段，很容易认为我们完成了。密文形式为 \((r, x)\)，其中 \(r\) 是均匀选择的，而 \(x\) 是用看似“一次性密钥”的 T[r] 加密明文的结果——如果 \(r\) 曾经重复，这个值可能会被多次使用！

正如西普利西奥恰当指出的，当 PRF 在不同输入上被调用时，它会给出独立随机（看起来随机）的输出。但在我们当前的混合体中，无法保证 PRF 输入是不同的！我们的证明必须明确包含关于为什么 PRF 输入不太可能重复的推理。我们通过引用 Lemma 4.11 的有放回采样引理来做到这一点。

我们首先将 r 值的采样提取为一个子程序。该子程序对应于 Lemma 4.11 的 L_samp-L 库：

```
CTXT(m):
r ← SAMP()
z := LOOKUP(r)
x := z ⊕ m
return (r, x)

L^F_prf-rand
T := empty
LOOKUP(r):
if T[r] undefined:
  T[r] ← {0, 1}^out
return T[r]

L_samp-L
SAMP():
r ← {0, 1}^λ
return r
```

接下来，L_samp-L 被 L_samp-R 替换。根据 Lemma 4.11，差异不可区分：

```
CTXT(m):
r ← SAMP()
z := LOOKUP(r)
x := z ⊕ m
return (r, x)

L^F_prf-rand
T := empty
LOOKUP(r):
if T[r] undefined:
  T[r] ← {0, 1}^out
return T[r]

L_samp-R
R := ∅
SAMP():
r ← {0, 1}^λ \ R
R := R ∪ {r}
return r
```

检查前一个混合体，我们可以推断传递给 LOOKUP 的参数保证永不重复。因此 L_prf-rand 库可以大大简化。特别是，L_prf-rand 中的 if 条件始终为真。简化不会影响库的输出行为：

```
CTXT(m):
r ← SAMP()
z := LOOKUP(r)
x := z ⊕ m
return (r, x)

LOOKUP(r):
t ← {0, 1}^out
return t

L_samp-R
R := ∅
SAMP():
r ← {0, 1}^λ \ R
R := R ∪ {r}
return r
```

现在我们确实使用唯一的一次性密钥来掩盖明文。我们比之前好得多。回顾我们的目标是到达一个混合体，其中 CTXT 的输出均匀选择。这些输出包括 r 值，但现在 r 不再均匀选择！我们必须将 r 恢复为均匀采样，然后我们就接近终点了。

```
CTXT(m):
  r <- SAMP()
  z := LOOKUP(r)
  x := z $\oplus$ m
  return (r, x)
```

```
LOOKUP(r):
  t <- {0, 1}$^{\text{out}}$
  return t
```

```
$\mathcal{L}_{\text{samp-L}}$
SAMP():
  r <- {0, 1}$^\lambda$
  return r
```

如所承诺，\(\mathcal{L}_{\text{samp-R}}\) 已被 \(\mathcal{L}_{\text{samp-L}}\) 替换。差异由于 Lemma 4.11 而不可区分。

```
CTXT(m):
  r <- {0, 1}$^\lambda$
  z <- {0, 1}$^{\text{out}}$
  x := z $\oplus$ m
  return (r, x)
```

所有子程序调用都已内联；对库的输出行为无影响。

```
$\mathcal{L}^\Sigma_{\text{cpa\$-rand}}$:
CTXT(m):
  r <- {0, 1}$^\lambda$
  x <- {0, 1}$^{\text{out}}$
  return (r, x)
```

我们已对变量 \(z\) 和 \(x\) 应用了一次性密钥规则，但省略了我们多次见过的非常熟悉的步骤（提取、替换库、内联）。结果的库正是 \(\mathcal{L}^\Sigma_{\text{cpa\$-rand}}\)，因为它从 \(\Sigma.\mathcal{C} = \{0, 1\}^\lambda \times \{0, 1\}^{\text{out}}\) 中均匀采样。

混合体序列表明 \(\mathcal{L}^\Sigma_{\text{cpa\$-real}} \approx \mathcal{L}^\Sigma_{\text{cpa\$-rand}}\)，因此 \(\Sigma\) 具有伪随机密文。

## 练习

### 7.1. 设 \(\Sigma\) 为一个加密方案，并假设存在一个程序 \(\mathcal{A}\)，它能从选择明文攻击中恢复密钥。更准确地说，\(\Pr[\mathcal{A} \diamond \mathcal{L} \text{ outputs } k]\) 不是可忽略的，其中 \(\mathcal{L}\) 定义为：

```
$\mathcal{L}$
k <- $\Sigma$.KeyGen
CHALLENGE($m \in \Sigma.\mathcal{M}$):
  c := $\Sigma$.Enc(k, m)
  return c
```

证明，如果存在这样的 \(\mathcal{A}\)，则 \(\Sigma\) 不具有 CPA 安全性。在一个违反 CPA 安全性定义的区分器中将 \(\mathcal{A}\) 用作子程序。

换句话说，CPA 安全性意味着从看到选择明文的加密中确定密钥应该是困难的。

### 7.2. 设 \(\Sigma\) 为具有 CPA$ 安全性的加密方案。设 \(\Sigma'\) 为按以下方式定义的加密方案：

$\Sigma'.\text{Enc}(k, m) = 00 || \Sigma.\text{Enc}(k, m)$

\(\Sigma'\) 中的解密算法仅丢弃密文的前两位，然后调用 \(\Sigma\).Dec。

- (a) \(\Sigma'\) 是否具有 CPA$ 安全性？证明或反驳（如果反驳，展示一个区分器并计算其优势）。
- (b) \(\Sigma'\) 是否具有 CPA 安全性？证明或反驳（如果反驳，展示一个区分器并计算其优势）。

### 7.3. 假设用户正在使用构造 7.4，而攻击者观察到两个具有相同 \(r\) 值的密文。

- (a) 在这种情况下，攻击者确切地了解了明文的什么信息？
- (b) 如何将此与这样一个事实调和：在索赔 7.5 的证明中，存在一个混合体，其中 \(r\) 值 *从不* 重复？

### 7.4. 构造 7.4 是一个随机化加密方案，但我们也可以考虑将其定义为 **基于 nonce** 的方案，将 \(r\) 解释为 nonce：Enc\((k, r, m) = (r, F(k, r) \oplus m)\)。形式上证明它作为一个确定性、基于 nonce 的方案是安全的。换句话说，证明以下两个库不可区分，其中 \(\Sigma\) 指的是构造 7.4。

```
k \(\leftarrow\Sigma\).KeyGen
V := \(\emptyset\)
EAVESDROP(v, m_L, m_R \(\in\Sigma.\mathcal{M}\)):
if v \(\in\) V: return err
V := \(V \cup \{v\}\)
c := \(\Sigma\).Enc(k, v, m_L)
return c
```

```
k \(\leftarrow\Sigma\).KeyGen
V := \(\emptyset\)
EAVESDROP(v, m_L, m_R \(\in\Sigma.\mathcal{M}\)):
if v \(\in\) V: return err
V := \(V \cup \{v\}\)
c := \(\Sigma\).Enc(k, v, m_R)
return c
```

### 7.5. 设 \(F\) 为一个安全的 PRP，块长度 \(blen = \lambda\)。考虑以下随机化加密方案：

| | KeyGen | Enc(k, m) |
|---|---|---|
| $\mathcal{K} = \{0, 1\}^\lambda$ | | |
| $\mathcal{M} = \{0, 1\}^\lambda$ | $k \leftarrow \{0, 1\}^\lambda$ | $v \leftarrow \{0, 1\}^\lambda$ |
| $\mathcal{C} = (\{0, 1\}^\lambda)^2$ | return k | $x := F(k, v \oplus m)$ |
| | | return $(v, x)$ |

- (a) 给出该方案的解密算法。
- (b) 证明该方案具有 CPA$ 安全性。
- (c) 假设我们将此方案解释为一个基于 nonce 的方案，其中 \(v\) 是 nonce。证明该方案 **不** 具有基于 nonce 的 CPA 安全性。该定义的库在上一题中给出。

注意：即使在标准 CPA 库中，\(v\) 也会提供给攻击者，且不太可能重复。然而，在基于 nonce 的库中，攻击者可以 *选择* \(v\)，这正是导致问题的原因。

