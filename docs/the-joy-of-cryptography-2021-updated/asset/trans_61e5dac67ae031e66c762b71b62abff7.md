

```
(A, B, C) <- DHQUERY()
count = 0
GETPK():
return A
QUERY(M ∈ G):
count := count + 1
if count > 1: return null
X := M · C
return (B, X)
```

```
L_dh-real
DHQUERY():
a, b <- Z_n
return (g^a, g^b, g^ab)
```

我们可以从决策性 Diffie-Hellman 安全定义（定义 14.5）中，在 L_dh-real 库的框架下提取 A、B、C 的生成。

```
(A, B, C) <- DHQUERY()
count = 0
GETPK():
return A
QUERY(M ∈ G):
count := count + 1
if count > 1: return null
X := M · C
return (B, X)
```

```
L_dh-rand
DHQUERY():
a, b, c <- Z_n
return (g^a, g^b, g^c)
```

应用 DDH 的安全性，我们可以用 L_dh-rand 替换 L_dh-real。

```
a, b, c <- Z_n
A := g^a; B := g^b; C := g^c
count = 0
GETPK():
return A
QUERY(M ∈ G):
count := count + 1
if count > 1: return null
X := M · C
return (B, X)
```

对 DHQUERY 的调用已被内联。

```
a \leftarrow \mathbb{Z}_n
A := g^a
count = 0

GETPK():
    return A

QUERY(M \in \mathbb{G}):
    count := count + 1
    if count > 1: return null
    b, c \leftarrow \mathbb{Z}_n
    B := g^b ; C := g^c
    X := M \cdot C
    return (B, X)
```

与之前一样，由于 QUERY 的主体只能执行一次，我们可以将 B 和 C 的选择移入该子程序，而不是在初始化时进行。

```
\mathcal{L}_{\text{pk-ots}\$-rand}
a \leftarrow \mathbb{Z}_n
A := g^a
count = 0

GETPK():
    return A

QUERY(M \in \mathbb{G}):
    count := count + 1
    if count > 1: return null
    b, x \leftarrow \mathbb{Z}_n
    B := g^b ; X := g^x
    return (B, X)
```

当 b 从 $\mathbb{Z}_n$ 中均匀采样时，表达式 $B = g^b$ 是 $\mathbb{G}$ 中的一个均匀分布元素。还要回顾，当 C 是 $\mathbb{G}$ 中的均匀分布元素时，$M \cdot C$ 也是均匀分布的——这与一次性密码本属性类似（参见练习 2.5）。应用此更改得到左侧的库。

在最终混合体中，对 QUERY 的响应是一对均匀分布的群元素 (B, X)。因此该库正是 $\mathcal{L}_{\text{pk-ots}\$-rand}$，符合预期。

## 15.4 混合加密

一般而言，公钥加密方案的计算开销远大于对称密钥方案。以 ElGamal 为代表性例子，在密码学安全的循环群中计算 g^b 远比一次 AES 计算开销大得多。随着明文数据长度的增加，公钥与对称密钥技术之间的成本差距只会越来越大。

一种巧妙的最小化公钥密码学成本的方法是使用一种称为混合加密的技术。其思想是使用昂贵的公钥方案来加密对称密钥方案的临时密钥，然后使用该临时密钥（廉价地）加密大量明文数据。

解密时，可以使用公钥方案的解密密钥来获取临时密钥。然后可以使用该临时密钥来解密主载荷。

### 构造 15.8（混合加密）

设 \(\Sigma_{pub}\) 为一个公钥加密方案，\(\Sigma_{sym}\) 为一个对称密钥加密方案，其中 \(\Sigma_{sym}.\mathcal{K} \subseteq \Sigma_{pub}.\mathcal{M}\) —— 也就是说，公钥方案能够加密对称密钥方案的密钥。

```
Enc(pk, m):
  tk <- \Sigma_sym.KeyGen
  c_pub <- \Sigma_pub.Enc(pk, tk)
  c_sym <- \Sigma_sym.Enc(tk, m)
  return (c_pub, c_sym)

M = \Sigma_sym.M
C = \Sigma_pub.C \times \Sigma_sym.C

KeyGen:
(pk, sk) <- \Sigma_pub.KeyGen
return (pk, sk)

Dec(sk, (c_pub, c_sym)):
  tk := \Sigma_pub.Dec(sk, c_pub)
  return \Sigma_sym.Dec(tk, c_sym)
```

重要的是，混合加密方案的消息空间是对称密钥方案的消息空间（可以将其视为涉及非常长的明文），但加密和解密仅在小的临时密钥上涉及昂贵的公钥运算（可以将其视为一个非常短的字符串）。

该方案的正确性可以通过以下方式验证：

```
Dec(sk, Enc(pk, m)) = Dec(sk, (\Sigma_pub.Enc(pk, tk), \Sigma_sym.Enc(tk, m)))
= \Sigma_sym.Dec( \Sigma_pub.Dec(sk, \Sigma_pub.Enc(pk, tk)), \Sigma_sym.Enc(tk, m) )
= \Sigma_sym.Dec( tk, \Sigma_sym.Enc(tk, m) )
= m.
```

为了证明混合加密是一种有效的数据加密方式，我们证明当其两个组件具有适当的安全属性时，它提供 CPA 安全性：

### 声明 15.9

如果 \(\Sigma_{sym}\) 是一个一次性秘密对称密钥加密方案，且 \(\Sigma_{pub}\) 是一个 CPA 安全的公钥加密方案，那么混合方案 \(\Sigma_{hyb}$（构造 15.8）也是一个 CPA 安全的公钥加密方案。

请注意，\(\Sigma_{sym}$ 甚至不需要是 CPA 安全的。直观上，一次性秘密就足够了，因为每个临时密钥 \(tk\) 仅被用来加密单个明文一次。

### 证明

如常，我们的目标是证明 \(\mathcal{L}^{\Sigma_{hyb}}_{\text{pk-cpa-L}} \approx \mathcal{L}^{\Sigma_{hyb}}_{\text{pk-cpa-R}}$，我们通过一系列标准的混合体来实现：

```
\mathcal{L}^{\Sigma_{\text{hyb}}}_{\text{pk-cpa-L}}
(pk, sk) \leftarrow \Sigma_{\text{pub}}.\text{KeyGen}
\underline{\text{GETPK}():
return } pk
\underline{\text{CHALLENGE}(m_L, m_R):
tk \leftarrow \Sigma_{\text{sym}}.\text{KeyGen}
c_{\text{pub}} \leftarrow \Sigma_{\text{pub}}.\text{Enc}(pk, tk)
c_{\text{sym}} \leftarrow \Sigma_{\text{sym}}.\text{Enc}(tk, m_L)
return (c_{\text{pub}}, c_{\text{sym}})
}
```

起点是 $\mathcal{L}_{\text{pk-cpa-L}}$，这里填充了 $\Sigma_{\text{hyb}}$ 的细节。

我们唯一的目标是以某种方式将 $m_L$ 替换为 $m_R$。由于 $m_L$ 仅作为 $\Sigma_{\text{sym}}$ 的明文使用，很诱人直接应用 $\Sigma_{\text{sym}}$ 的一次性秘密属性来论证 $m_L$ 可以被 $m_R$ 替换。不幸的是，这行不通，因为用于该密文的密钥是 $tk$，而 $tk$ 在其他地方也被使用。特别是，它被用作 $\Sigma_{\text{pub}}.\text{Enc}$ 的参数。

然而，如果 $\Sigma_{\text{pub}}$ 是 CPA 安全的，那么将 $tk$ 作为 $\Sigma_{\text{pub}}.\text{Enc}$ 的明文参数，应当对调用程序隐藏 $tk$。也就是说，$\Sigma_{\text{pub}}$ 对 $tk$ 的加密应该看起来像是对某个不相关的哑值的 $\Sigma_{\text{pub}}$ 加密。更正式地，我们可以按照以下方式，基于 $\mathcal{L}_{\text{pk-cpa-L}}$ 库提取对 $\Sigma_{\text{pub}}.\text{Enc}$ 的调用：

```
\underline{\text{CHALLENGE}(m_L, m_R):
tk \leftarrow \Sigma_{\text{sym}}.\text{KeyGen}
tk' \leftarrow \Sigma_{\text{sym}}.\text{KeyGen}
c_{\text{pub}} \leftarrow \text{CHALLENGE}'(tk, tk')
c_{\text{sym}} \leftarrow \Sigma_{\text{sym}}.\text{Enc}(tk, m_L)
return (c_{\text{pub}}, c_{\text{sym}})
}
```

```
\mathcal{L}^{\Sigma_{\text{pub}}}_{\text{pk-cpa-L}}
(pk, sk) \leftarrow \Sigma_{\text{pub}}.\text{KeyGen}
\underline{\text{GETPK}():
return } pk
\underline{\text{CHALLENGE}'(tk_L, tk_R):
return } \Sigma_{\text{pub}}.\text{Enc}(pk, tk_L)
}
```

这里我们更改了 CHALLENGE' 参数的变量名，以避免不必要的混淆。还要注意，CHALLENGE 现在选择两个临时密钥——一个实际上用于加密 $m_L$，另一个在任何地方都不使用。这是因为在语法上，我们必须向 CHALLENGE' 传递两个参数。

现在想象将 $\mathcal{L}_{\text{pk-cpa-L}}$ 替换为 $\mathcal{L}_{\text{pk-cpa-R}}$ 并内联子程序调用。结果是：

```
(pk, sk) \leftarrow \Sigma_{\text{pub}}.\text{KeyGen}
\underline{\text{GETPK}():
return } pk
\underline{\text{CHALLENGE}(m_L, m_R):
tk \leftarrow \Sigma_{\text{sym}}.\text{KeyGen}
tk' \leftarrow \Sigma_{\text{sym}}.\text{KeyGen}
c_{\text{pub}} \leftarrow \Sigma_{\text{pub}}.\text{Enc}(pk, tk')
c_{\text{sym}} \leftarrow \Sigma_{\text{sym}}.\text{Enc}(tk, m_L)
return (c_{\text{pub}}, c_{\text{sym}})
}
```

此时，可以基于 $\mathcal{L}_{\text{ots-L}}$ 库提取对 $\Sigma_{\text{sym}}.\text{Enc}$ 的调用。这是因为密钥 $tk$ 在库中不再在其他地方被使用。结果是

