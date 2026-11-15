

```
$\mathcal{L}_{\text{hyb-4}}$:
EAVESDROP($m_L, m_R$):
$z \leftarrow \{0, 1\}^{\lambda + \ell}$
$c := z \oplus m_R$
return $c$
```

rOTP 的（完美）一次性保密性允许我们将 $\mathcal{L}^{\text{OTP}}_{\text{ots-L}}$ 替换为 $\mathcal{L}^{\text{OTP}}_{\text{ots-R}}$；两者可以互换。

证明的其余部分本质上是前面步骤的“镜像”，我们执行相同的步骤，但顺序相反（并且使用 \(m_R\) 而不是 \(m_L\)）。

```
EAVESDROP($m_L, m_R$):
$z \leftarrow$ QUERY()
$c := z \oplus m_R$
return $c$
```

```
$\mathcal{L}^G_{\text{prg-rand}}$
QUERY():
$r \leftarrow \{0, 1\}^{\lambda + \ell}$
return $r$
```

一条语句已被提取到子程序中，它恰好与 $\mathcal{L}^G_{\text{prg-rand}}$ 完全匹配。

```
EAVESDROP($m_L, m_R$):
$z \leftarrow$ QUERY()
$c := z \oplus m_R$
return $c$
```

```
$\mathcal{L}^G_{\text{prg-real}}$
QUERY():
$s \leftarrow \{0, 1\}^\lambda$
return $G(s)$
```

从 $G$ 的 PRG 安全性出发，我们可以将 $\mathcal{L}^G_{\text{prg-rand}}$ 替换为 $\mathcal{L}^G_{\text{prg-real}}$。得到的库与前一个库不可区分。

```
$\mathcal{L}^{\text{pOTP}}_{\text{ots-R}}$
EAVESDROP($m_L, m_R$):
\(k \leftarrow \{0, 1\}^\lambda\)
\(c := G(k) \oplus m_R\)
return \(c\)
```

已将子程序内联。结果为 $\mathcal{L}^{\text{pOTP}}_{\text{ots-R}}$。

总结一下，我们展示了一组满足以下条件的混合库序列：

\(\mathcal{L}^{\text{pOTP}}_{\text{ots-L}} \equiv \mathcal{L}_{\text{hyb-1}} \approx \mathcal{L}_{\text{hyb-2}} \equiv \mathcal{L}_{\text{hyb-3}} \equiv \mathcal{L}_{\text{hyb-4}} \equiv \mathcal{L}_{\text{hyb-5}} \approx \mathcal{L}_{\text{hyb-6}} \equiv \mathcal{L}^{\text{pOTP}}_{\text{ots-R}}.\)

因此，$\mathcal{L}^{\text{pOTP}}_{\text{ots-L}} \approx \mathcal{L}^{\text{pOTP}}_{\text{ots-R}}$，pOTP 具有（计算）一次性保密性。

## 5.4 扩展 PRG 的伸展量

PRG 的伸展量衡量其输出比输入长多少。我们可以使用伸展量较小的 PRG 来构造伸展量较大的 PRG 吗？答案是肯定的，但只有当你采用正确的方法时才行！

### 增加伸展量的两种方法

假设 \(G : \{0, 1\}^\lambda \rightarrow \{0, 1\}^{2\lambda}\) 是一个长度翻倍 PRG（即伸展量为 \(\lambda\) 的 PRG）。下面是构造更长伸展量 PRG 的两种思路：

![](img/da79fa21b263fe549aecaabd2a0a41c8_103_0.png)

尽管这两种构造相似，但只有其中一种是安全的。在继续阅读之前，你能猜出 \(H_1\) 和 \(H_2\) 中哪一个是安全的 PRG，哪一个是不安全的吗？通过仔细比较这两种方法，我希望你能更好地理解 PRG 安全性定义。

### 一则安全性证明

我认为，从期望的结论出发并逆向推导，有助于阐释安全性证明的“策略”。还不如以伽利略风格的苏格拉底对话来呈现吗？²

萨尔维亚蒂：我肯定 \(H_1\) 是安全的 PRG。

辛普利西奥：如果我正确理解了 PRG 的安全性定义，您的意思是当 \(H_1\) 的输入是均匀分布时，其输出看起来与均匀分布不可区分。您为什么这么说？

萨尔维亚蒂：简单！\(H_1\) 的输出由名为 \(x\)、\(u\) 和 \(v\) 的片段组成。这些片段都是 \(G\) 的输出，而由于 \(G\) 本身就是一个 PRG，它的输出看起来是均匀的。

辛普利西奥：我真希望有您那样的胆量，萨尔维亚蒂。我自己更加谨慎。如果 \(G\) 是安全的 PRG，那么它的输出确实与均匀分布不可区分，但这肯定只在输入均匀时才成立！您在这里就那么肯定吗？

萨尔维亚蒂：您提出了很好的观点，辛普利西奥。在这类工作中，谨慎行事总是更可取。当我们要主张 \(H_1\) 是安全的 PRG 时，我们考虑当种子 \(s\) 是均匀分布时其输出的性质。由于 \(H_1\) 将该种子 \(s\) 直接输入到 \(G\)，您的顾虑已得到消除。

辛普利西奥：是的，我可以看到在表达式 \(x||y := G(s)\) 中，\(G\) 的输入是均匀分布，因此其输出 \(x\) 和 \(y\) 与随机分布不可区分。由于 \(x\) 是 \(H_1\) 的输出的一部分，我们正在朝着证明 \(H_1\) 的完整输出与随机分布不可区分的方向迈进！然而，\(H_1\) 的输出还包含项 \(u\) 和 \(v\)。当我检查它们是如何生成的，即 \(u||v := G(y)\) 时，我又感到担忧了。肯定 \(y\) 不是均匀的，所以我看不到应用 \(G\) 安全性的方法！

萨尔维亚蒂：哦，天啦。答案再明显不过了！确实 \(y\) 不服从均匀分布。但您不是刚刚说服自己 \(y\) 与均匀分布不可区分吗？这难道不够吗？

辛普利西奥：难以置信！我相信我现在明白了。让我试着总结一下：我们假设输入到 H1 的 \(s\) 是均匀选择的，并检查 H1 的输出会发生什么。在表达式 \(x||y := G(s)\) 中，\(G\) 的输入是均匀分布，因此 \(x\) 和 \(y\) 与均匀分布不可区分。现在，考虑表达式 \(u||v := G(y)\)，其结果与 \(y\) 真正是均匀分布的情景不可区分。但如果 \(y\) 真正是均匀分布，那么输出 \(u\) 和 \(v\) 将与均匀分布不可区分！总而言之，\(x\)、\(u\) 和 \(v\)（即 \(H_1\) 的输出）都与均匀分布不可区分！

希望这对你来说和对我一样有趣。³ 正式的安全性证明及其混合库序列将遵循辛普利西奥总结中的大纲。我们首先对第一次调用 G 应用 PRG 安全性定义，并将其输出替换为真正均匀的值。经过这一更改后，第二次调用 G 的输入变为均匀分布，从而使我们能够再次应用 PRG 安全性定义。

主张 5.5 如果 G 是安全的长度翻倍 PRG，那么 H1（如上定义）是安全的（长度三倍）PRG。

证明 此证明中棘手的方面之一是，我们使用安全的 PRG G 来证明另一个 PRG H1 的安全性。这意味着 \(\mathcal{L}^{H_1}_{\text{prg-star}}\) 和 \(\mathcal{L}^G_{\text{prg-star}}\) 都将出现在本证明中。这两个库/接口都有一个名为 "QUERY" 的子程序，我们将把这些子程序重命名为 QUERY_{H1} 和 QUERY_{G} 以消除歧义。

我们想要证明 \(\mathcal{L}^{H_1}_{\text{prg-real}} \approx \mathcal{L}^{H_1}_{\text{prg-rand}}\)。和往常一样，我们通过混合库序列来实现这一点。

由于我们假设 G 是安全的 PRG，我们可以使用 \(\mathcal{L}^G_{\text{prg-real}} \approx \mathcal{L}^G_{\text{prg-rand}}$ 这一事实。

```
$\mathcal{L}^{H_1}_{\text{prg-real}}$
QUERY_{H1}():
  $s \leftarrow \{0, 1\}^\lambda$
  $x||y := G(s)$
  $u||v := G(y)$
  return $x||u||v$
```

起点是 \(\mathcal{L}^{H_1}_{\text{prg-real}}\)，此处填充了 H1 的细节。

```
QUERY_{H1}():
  $x||y := QUERY_G()$
  $u||v := G(y)$
  return $x||u||v$

$\mathcal{L}^G_{\text{prg-real}}$
QUERY_G():
  $s \leftarrow \{0, 1\}^\lambda$
  return $G(s)$
```

第一次调用 G 已被提取为子程序。得到的混合库包含一个 \(\mathcal{L}^G_{\text{prg-real}}$ 的实例。

从 G 的 PRG 安全性出发，我们可以将 $\mathcal{L}^G_{\text{prg-real}}$ 的实例替换为 $\mathcal{L}^G_{\text{prg-rand}}$。得到的混合库不可区分。

已将子程序内联。

选择 $2\lambda$ 个均匀随机位然后将其分成两半，与选择 $\lambda$ 个均匀随机位并独立再选 $\lambda$ 个具有完全相同的效果。

剩余的 G 调用已被提取为子程序。现在 $\mathcal{L}^G_{\text{prg-real}}$ 第二次出现。

再次，G 的 PRG 安全性允许我们将 $\mathcal{L}^G_{\text{prg-real}}$ 替换为 $\mathcal{L}^G_{\text{prg-rand}}$。得到的混合库不可区分。

已将子程序内联。

与上述类似，将 $\lambda$ 个均匀位与 $2\lambda$ 个独立均匀位拼接，与采样 $3\lambda$ 个均匀位的效果相同。此更改的结果是 $\mathcal{L}^{H_1}_{\text{prg-rand}}'$。

