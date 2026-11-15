
不要被所有这些混合库压倒。它们都遵循一个简单的模式。事实上，第 $i$ 个混合库如下：

```
$\mathcal{L}^{\text{hyb-}i}:$:

count := 0
QUERY():
  count := count + 1
  if count \(\leqslant i\):
    \(r \leftarrow \{0, 1\}^{2\lambda}\)
    return \(r\)
  else:
    \(s \leftarrow \{0, 1\}^\lambda\)
    \(x := F(s, 00 \cdots 00)\)
    \(y := F(s, 00 \cdots 01)\)
    return \(x \|\| y\)
```

换句话说，这些混合库仅在于插入到上述代码中的值 \(i\) 不同。如果你熟悉 C 编译器，可以将此视为在上述代码顶部添加 "#define i 427"，从而得到 \(\mathcal{L}^{\text{hyb-427}}\)。

首先注意 \(i\) 取极端值时会发生什么：

- 在 \(\mathcal{L}^{\text{hyb-0}}\) 中，if 分支永远不会被执行（\(count \leqslant 0\) 永远不为真）。该库在每次调用 QUERY 时都给出 PRG 输出，因此其行为与 \(\mathcal{L}^G_{\text{prg-real}}\) 完全一致。

- 如果 \(q\) 是调用程序调用 QUERY 的总次数，则在 \(\mathcal{L}^{\text{hyb-q}}\) 中，if 分支始终会被执行（\(count \leqslant q\) 始终为真）。该库在每次调用 QUERY 时都给出真正均匀的输出，因此其行为与 \(\mathcal{L}^G_{\text{prg-rand}}\) 完全一致。

一般来说，\(\mathcal{L}^{\text{hyb-}i}\) 会对前 \(i\) 次 QUERY 调用给出真正随机的输出。它会对所有后续调用给出我们 PRG 构造的输出。

我们已经论证了 \(\mathcal{L}^G_{\text{prg-real}} \equiv \mathcal{L}^{\text{hyb-0}}\) 且 \(\mathcal{L}^G_{\text{prg-rand}} \equiv \mathcal{L}^{\text{hyb-q}}\)。为了完成证明，我们必须表明对于所有 \(i\)，\(\mathcal{L}^{\text{hyb-}(i - 1)} \approx \mathcal{L}^{\text{hyb-}i}\)。定义如此多的混合库并费此周折的主要原因是，\(\mathcal{L}^{\text{hyb-}(i-1)}\) 和 \(\mathcal{L}^{\text{hyb-}i}\) 完全相同，只不过在响应第 \(i\) 次 QUERY 调用的方式上不同。这一差异仅涉及一次 PRG 调用（因此也仅涉及一个 PRF 种子），这使我们能够应用 PRF 的安全性。

更具体地说，令 \(i\) 为任意值，并考虑从 \(\mathcal{L}^{\text{hyb-}(i - 1)}\) 开始的以下步骤序列：

```
count := 0
QUERY():
  count := count + 1
  if count < i:
    r <- {0, 1}^{2\lambda}
    return r
  elseif count = i:
    s* <- {0, 1}^{\lambda}
    x := F(s*, 0...00)
    y := F(s*, 0...01)
    return x||y
  else:
    s <- {0, 1}^{\lambda}
    x := F(s, 0...00)
    y := F(s, 0...01)
    return x||y
```

我们对 \(\mathcal{L}^{\text{hyb-}(i-1)}\) 进行了处理，仅将 else 分支 \((count \ge i)\) 展开为两个子情况（\(count = i\) 和 \(count > i\)）。然而，两种情况都导致相同的代码块（仅局部变量名称不同），因此该更改对调用程序没有影响。

```
count := 0
QUERY():
  count := count + 1
  if count < i:
    r <- {0, 1}^{2\lambda}
    return r
  elseif count = i:
    x := LOOKUP(0...00)
    y := LOOKUP(0...01)
    return x||y
  else:
    s <- {0, 1}^{\lambda}
    x := F(s, 0...00)
    y := F(s, 0...01)
    return x||y
```

```
\mathcal{L}^F_{\text{prf-real}}
k <- {0, 1}^{\lambda}
LOOKUP(x):
  return F(k, x)
```

我们已将使用种子 \(s^*\)（对应 \(count = i\) 情况）的 \(F\) 调用用 \(\mathcal{L}_{\text{prf-real}}\) 形式提取出来。该更改对调用程序没有影响。

```
count := 0

QUERY():
  count := count + 1
  if count < i:
    r <- {0, 1}^{2\lambda}
    return r
  elseif count = i:
    x := LOOKUP(0...00)
    y := LOOKUP(0...01)
    return x||y
  else:
    s <- {0, 1}^{\lambda}
    x := F(s, 0...00)
    y := F(s, 0...01)
    return x||y
```

```
\mathcal{L}^{\mathcal{F}}_{\text{prf-rand}}

T := empty assoc. array

LOOKUP(x):
  if T[x] undefined:
    T[x] <- {0, 1}^{\lambda}
  return T[x]
```

由于 F 是安全的 PRF，我们可以用 \(\mathcal{L}^{\mathcal{F}}_{\text{prf-rand}}\) 替换 \(\mathcal{L}^{\mathcal{F}}_{\text{prf-real}}\)，且总的变化不可区分。

```
count := 0

QUERY():
  count := count + 1
  if count < i:
    r <- {0, 1}^{2\lambda}
    return r
  elseif count = i:
    x := LOOKUP(0...00)
    y := LOOKUP(0...01)
    return x||y
  else:
    s <- {0, 1}^{\lambda}
    x := F(s, 0...00)
    y := F(s, 0...01)
    return x||y
```

```
LOOKUP(x):
  r <- {0, 1}^{\lambda}
  return r
```

由于 count = i 仅发生一次，整个库生命周期内只会进行两次 LOOKUP 调用，且它们的输入不同。因此，LOOKUP 中的 if 分支始终会被执行，T 从不需要（它仅用于“记住”值，并在同一个 x 两次作为参数传给 LOOKUP 时给出相同答案）。因此，简化库对调用程序没有影响：

```
count := 0
QUERY():
  count := count + 1
  if count < i:
    r <- {0, 1}^{2\lambda}
    return r
  elseif count = i:
    x <- {0, 1}^{\lambda}
    y <- {0, 1}^{\lambda}
    return x||y
  else:
    s <- {0, 1}^{\lambda}
    x := F(s, 0...00)
    y := F(s, 0...01)
    return x||y
```

内联子程序对调用程序没有影响。所得库对前 \(i\) 次 QUERY 调用给出均匀随机输出，对其他调用给出我们的 PRG G 的输出。因此，该库与 \(\mathcal{L}_{\text{hyb-}i}\) 具有相同的行为。

我们已经表明 \(\mathcal{L}_{\text{hyb-}(i-1)} \approx \mathcal{L}_{\text{hyb-}i}\)，因此：

$\mathcal{L}^G_{\text{prg-real}} \equiv \mathcal{L}_{\text{hyb-0}} \approx \mathcal{L}_{\text{hyb-1}} \approx \cdots \approx \mathcal{L}_{\text{hyb-q}} \equiv \mathcal{L}^G_{\text{prg-rand}}$

这表明 $\mathcal{L}^G_{\text{prg-real}} \approx \mathcal{L}^G_{\text{prg-rand}}$，因此 G 是安全的 PRG。

## 从 PRG 构造 PRF 的理论方法

我们已经看到，可以将 PRG 的输出再次输入到 PRG 中，以扩展其扩展量（Claim 5.7）。这是通过构建一个长长的 PRG 链（类似于链表）来实现的。从 PRG 构造 PRF 的诀窍是将 PRG 组织成一棵二叉树（类似于练习 5.8(a)）。树的叶子对应于 PRF 的最终输出。如果我们想要一个指数级大小的定义域的 PRF（例如，\(n = \lambda\)），那么二叉树本身也是指数级大小的！然而，通过简单地从根遍历到叶子，仍然可以高效地计算任何单个叶子。这种树遍历本身就是 PRF 算法。这种 PRF 构造方法源自戈德雷奇、戈尔德瓦瑟和米卡利，他们在定义 PRF 概念的论文中提出了该方法。

![](img/da79fa21b263fe549aecaabd2a0a41c8_126_0.png)

想象一棵高度为 $n$ 的完全二叉树（$n$ 将是 PRF 的输入长度）。树中的每个节点都有一个*位置*，可以表示为一个二进制字符串。可以将节点的位置视为从根出发到达该节点的方向，其中 0 表示“向左走”，1 表示“向右走”。例如，根节点的位置为 $\epsilon$（空字符串），根的右子节点位置为 1，依此类推。

该 PRF 构造通过使用长度翻倍的 PRG $G : \{0, 1\}^\lambda \rightarrow \{0, 1\}^{2\lambda}$ 为树中的每个节点分配一个*标签*。为了方便，我们将用 $G_L(k)$ 和 $G_R(k)$ 分别表示 $G(k)$ 的前 $\lambda$ 位和后 $\lambda$ 位。树中的标签是 $\lambda$ 位字符串，根据以下两条规则计算：

- 1. 根节点的标签是 PRF 种子。
- 2. 如果位置 $p$ 处的节点具有标签 $v$，则其左子节点（位置为 $p||0$）获得标签 $G_L(v)$，其右子节点（位置为 $p||1$）获得标签 $G_R(v)$。

如上图所示，节点的标签是其入边上传输的字符串。该树有 $2^n$ 个叶子，其位置为字符串 $\{0, 1\}^n$。我们定义 $F(k, x)$ 为节点/叶子 $x$ 的标签。要计算该标签，可以从根遍历到叶子，在每个节点根据 $x$ 的位决定向左还是向右，并沿着该路径根据标记规则计算标签。如上图所示，高亮路径对应于 $F(k, 1001 \cdots)$ 的计算。

重要的是要记住，二叉树是一个有用的概念工具，但通常来说它是指数级大小的。在某个输入上运行 PRF 不需要计算整棵树的标签，只需沿从根到叶子的单一路径计算即可。
