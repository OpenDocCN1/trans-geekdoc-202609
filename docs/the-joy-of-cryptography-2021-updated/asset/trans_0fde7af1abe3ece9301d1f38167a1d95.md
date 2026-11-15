

6.16. 证明一轮密钥 Feistel 密码 **不能** 成为安全的 PRP，无论其轮函数是什么。也就是说，构造一个区分器，它仅在知道 \(F\) 是一轮 Feistel 密码的情况下，成功区分 \(\mathcal{L}_{\text{prp-real}}^F\) 和 \(\mathcal{L}_{\text{prp-rand}}^F\)。特别是，目的是攻击 Feistel 变换而非其轮函数，因此你的攻击无论轮函数如何都应有效。

6.17. 证明两轮密钥 Feistel 密码 **不能** 成为安全的 PRP，无论其轮函数是什么。你的攻击不需要知道轮密钥，并且即使使用不同的（独立的）轮密钥也应有效。

6.18. 证明任何作为三轮密钥 Feistel 密码的函数 \(F\) **不能** 成为安全的 _强_ PRP。如上，你的区分器不需要知道轮函数是什么，并且攻击即使使用不同的（独立的）轮函数也应有效。

6.19. 在本题中，你将证明没有密钥时 PRP 难以反转（只要分组长度足够大）。设 \(F\) 是一个具有分组长度 \(\mathit{blen} \geq \lambda$ 的候选 PRP。假设存在一个程序 \(\mathcal{A}$，使得：

\(\Pr_{y \leftarrow \{0,1\}^{blen}} [\mathcal{A}(y) \diamond \mathcal{L}_{\text{prp-real}}^F \text{ outputs } F^{-1}(k, y)] \text{ is non-negligible.}\)

该记号表示 \(\mathcal{A}$ 接收一个随机分组 \(y$ 作为输入（并且也链接到 \(\mathcal{L}_{\text{prp-real}}\)）。\(k$ 指的是 \(\mathcal{L}_{\text{prp-real}}\) 中的私有变量。因此，当仅获得正向评估 \(F$ 的能力（通过 \(\mathcal{L}_{\text{prp-real}}\)）时，\(\mathcal{A}$ 可以反转一个均匀选择的分组 \(y$。

证明如果存在这样的 \(\mathcal{A}$，那么 \(F$ 不是安全的 PRP。使用 \(\mathcal{A}$ 构造一个违反 PRP 安全定义的区分器。你在哪里使用了 \(\mathit{blen} \geq \lambda$ 的事实？你如何处理 \(\mathcal{A}$ 可能以高概率给出错误答案的事实？

6.20. 设 \(F$ 是一个具有分组长度 \(\mathit{blen} = \lambda$ 的安全 PRP，并考虑 \(\widehat{F}(k, x) = F(k, x) \oplus F(k, x)$。

- (a) 证明 \(\widehat{F}$ 不是强 PRP（即使 \(F$ 是）。
- ★ (b) 证明 \(\widehat{F}$ 是安全的（普通）PRP。

## 7 防受明文攻击安全

我们之前的加密安全定义捕获的是密钥仅用于加密一个明文的情况。显然，拥有一个允许在同一密钥下加密多个明文的加密方案会更有用。

幸运的是，我们以一种自然的方式修改早期定义，从而得到“正确”的安全定义。我们只需让库一次性选择一个密钥，并用它来加密所有明文。更正式地：

Definition 7.1 (CPA 安全) 设 \(\Sigma$ 为一个加密方案。如果 \(\mathcal{L}^\Sigma_{\text{cpa-L}} \approx \mathcal{L}^\Sigma_{\text{cpa-R}}$，则我们称 \(\Sigma$ 具有抗选择明文攻击安全性（CPA 安全），其中：

```
\(\mathcal{L}^\Sigma_{\text{cpa-L}}\)
\(k \leftarrow \Sigma.KeyGen\)
\(\underline{\text{EAVESDROP}(m_L, m_R \in \Sigma.\mathcal{M})}\):
\(c := \Sigma.\text{Enc}(k, m_L)\)
return \(c\)
```

```
\(\mathcal{L}^\Sigma_{\text{cpa-R}}\)
\(k \leftarrow \Sigma.KeyGen\)
\(\underline{\text{EAVESDROP}(m_L, m_R \in \Sigma.\mathcal{M})}\):
\(c := \Sigma.\text{Enc}(k, m_R)\)
return \(c\)
```

注意密钥 \(k$ 在初始化时选定，并且对所有 Enc 调用都是静态的。CPA 安全通常被称为“IND-CPA”安全，意思是“在选择明文攻击下密文不可区分”。

### 7.1 确定性加密的局限性

我们已经见过分组密码 / PRP，它们似乎满足安全加密方案所需的一切。对于分组密码，\(F$ 对应加密，\(F^{-1}$ 对应解密，并且 \(F$ 的所有输出看起来都是伪随机的。在一个好的加密方案中，你还能要求什么呢？

示例 我们将看到，分组密码如果“原样”使用，**不是** CPA 安全的加密方案。设 \(F$ 表示分组密码，并假设其分组长度为 \(blen$。考虑以下试图区分 \(\mathcal{L}_{\text{cpa-*}}$ 库的对手 \(\mathcal{A}$：

```
\(\mathcal{A}\)
\(c_1 := \text{EAVESDROP}(0^{blen}, 0^{blen})\)
\(c_2 := \text{EAVESDROP}(0^{blen}, 1^{blen})\)
return \(c_1 \stackrel{?}{=} c_2\)
```

```
A
c1 := EAVESDROP(0^blen, 0^blen)
c2 := EAVESDROP(0^blen, 1^blen)
return c1 =? c2
```

```
L^Sigma_cpa-L
k <- {0, 1}^lambda
EAVESDROP(mL, mR):
c := F(k, mL)
return c
```

当 A 链接到 L_cpa-L 时，EAVESDROP 算法会加密其第一个参数。因此，c1 和 c2 都将被计算为 F(k, 0^blen)。由于 F 是确定性函数，这导致 EAVESDROP 输出相同。换句话说 c1 = c2，且 A 链接到 L_cpa-L 始终输出 1。

```
A
c1 := EAVESDROP(0^blen, 0^blen)
c2 := EAVESDROP(0^blen, 1^blen)
return c1 =? c2
```

```
L^Sigma_cpa-R
k <- {0, 1}^lambda
EAVESDROP(mL, mR):
c := F(k, mR)
return c
```

当 A 链接到 L_cpa-R 时，EAVESDROP 算法会加密其第二个参数。因此，c1 和 c2 分别计算为 c1 = F(k, 0^blen) 和 c2 = F(k, 1^blen)。由于 F 是置换，c1 != c2，所以 A 链接到 L_cpa-R 永远不会输出 1。

这个对手在区分库方面具有优势 1，因此原始分组密码 F 不是 CPA 安全的加密方案。

### 确定性加密的不可能性

原始分组密码不能提供 CPA 安全的原因是它是确定性的。用相同的密钥和相同的明文调用 Enc(k, m) 两次会导致相同的密文。即使一次性密码本也是确定性的。1 CPA 安全的首要且最重要的方面之一是它与确定性加密不兼容。确定性加密永远不能是 CPA 安全的！换句话说，仅知道某方案 Sigma 是确定性加密，我们就可以攻击其 CPA 安全性。该攻击是我们针对原始 PRP 的攻击的简单推广：

```
A
arbitrarily choose distinct plaintexts x, y in M
c1 := EAVESDROP(x, x)
c2 := EAVESDROP(x, y)
return c1 =? c2
```

思考确定性加密出了什么问题的一个好方法是，它泄露了两个密文是否编码相同的明文，而 CPA 安全不允许这种情况。可以将密封信封视为加密的类比。我不应该能判断两个密封信封是否包含相同的文本！我们之所以现在才看到这个问题，是因为这是我们的安全定义第一次允许对手看到在相同密钥下加密的多个密文。

1请记住，我们总是可以考虑用相同的密钥+明文运行两次一次性密码本加密会发生什么。一次性保密定义不会就以这种方式使用一次性密码本向我们提供任何安全保证，但我们仍然可以将其视为思想实验。

### 避免确定性加密

CPA 安全甚至可能吗？我们究竟如何才能构建一个非确定性加密方案？这听起来很有挑战性！我们必须设计一个 Enc 算法，使得用相同的明文和密钥调用它两次会产生不同的密文（否则上面的攻击 \(\mathcal{A}$ 将违反 CPA 安全性）。此外，必须能够将同一明文的所有这些不同加密解密为正确的值！

设计非确定性加密方案有 3 种一般方法：

- 加密/解密可以是 **有状态** 的，意味着每次调用 Enc 或 Dec 都会实际修改 \(k$ 的值。第 5.5 节中描述的对称棘轮构造可以被视为这种有状态的构造。每次加密都会通过棘轮机制更新密钥。有状态加密的一个重大缺点是，发送方和接收方之间的同步很脆弱，如果密文在传输中丢失，同步可能会中断。

- 加密可以是 **随机** 的。每次加密明文时，Enc 算法都会选择专用于该次加密的全新独立随机性。设计随机加密方法的主要挑战在于将随机性纳入每个密文，同时仍能实现解密。虽然这听起来相当有挑战性，但我们已经见过这样的方法，并将在下一节证明其 CPA 安全性。在本书中，我们将几乎完全专注于随机加密。

- 加密可以是 **基于 nonce** 的。“nonce”代表“仅使用一次的数字”，指的是传递给 Enc 和 Dec 算法的一个额外参数。nonce 不需要随机选择；不需要保密；它只需要在所有对 Enc 的调用中**不同**。通过保证 Enc 的某个输入每次都会不同（即使密钥和明文重复），Enc 算法可以是确定性的，同时仍能提供 CPA 安全性。

基于 nonce 的加密要求更改加密接口，因此也要求更改正确性和安全性定义。加密/解密算法语法更新为 Enc(\(k, v, m$) 和 Dec(\(k, v, c$)，其中 \(v$ 是 nonce。正确性属性是对于所有 \(k, v, m$，Dec(\(k, v$, Enc(\(k, v, m$)) = \(m$，因此加密和解密算法都应使用相同的 nonce。安全定义允许对手选择 nonce，但如果对手尝试使用相同的 nonce 加密多个密文，则会报错。通过这种方式，定义强制要求 nonce 不同。

| | |
|---|---|
| \(k \leftarrow \Sigma.\)KeyGen<br>\(V := \emptyset\)<br>EAVESDROP(\(v, m_L, m_R \in \Sigma.\mathcal{M}\)):<br>if \(v \in V\): return err<br>\(V := V \cup \{v\}\)<br>\(c := \Sigma.\)Enc(\(k, v, m_L\))<br>return \(c\) | \(k \leftarrow \Sigma.\)KeyGen<br>\(V := \emptyset\)<br>EAVESDROP(\(v, m_L, m_R \in \Sigma.\mathcal{M}\)):<br>if \(v \in V\): return err<br>\(V := V \cup \{v\}\)<br>\(c := \Sigma.\)Enc(\(k, v, m_R\))<br>return \(c\) |

