

```
ATTACK(m_1, ..., m_n):
s_0 <- {0, 1}^\lambda
for i = 1 to n:
    s_i || t_i := G(s_{i-1})
    c_i <- Sigma.Enc(t_i, m_i)
return (c_1, ..., c_n, s_n)
```

![](img/da79fa21b263fe549aecaabd2a0a41c8_110_0.png)

如我们所见，阴影框（即从 s_0 计算 t_1, ..., t_n 的过程）实际上是一个 PRG。让我们用这个 PRG H_n 来重写库：

```
ATTACK(m_1, ..., m_n):
s_0 <- {0, 1}^\lambda
t_1 || ... || t_n || s_n := H_n(s_0)
for i = 1 to n:
    c_i <- Sigma.Enc(t_i, m_i)
return (c_1, ..., c_n, s_n)
```

![](img/da79fa21b263fe549aecaabd2a0a41c8_110_1.png)

现在，我们可以应用 H_n 的 PRG 安全性，改为均匀地选择 t_1, ..., t_n 和 s_n。这一更改是不可区分的，根据 PRG 的安全性。请注意，我们没有写出标准的显式步骤（将 ATTACK 的前两行用 L^{prg-real} 分解，替换为 L^{prg-rand}，并内联）。

```
ATTACK(m_1, ..., m_n):
for i = 1 to n:
    t_i <- {0, 1}^\lambda
    s_n <- {0, 1}^\lambda
for i = 1 to n:
    c_i <- Sigma.Enc(t_i, m_i)
return (c_1, ..., c_n, s_n)
```

```
ATTACK(m_1, ..., m_n):
for i = 1 to n:
    t_i <- {0, 1}^\lambda
    c_i <- Sigma.Enc(t_i, m_i)
    s_n <- {0, 1}^\lambda
return (c_1, ..., c_n, s_n)
```

此时，加密方案正被“按预期使用”，意味着我们均匀/独立地生成其密钥 t_i，并且每个密钥仅用于一次加密，不做其他用途。从形式上讲，这意味着我们可以将 for 循环体用 L^{ots$-real} 分解出来：

```
ATTACK(m_1, ..., m_n):
for i = 1 to n:
    c_i <- CTXT(m_i)
s_n <- {0, 1}^\lambda
return (c_1, ..., c_n, s_n)
```

```
L^{\Sigma}_{ots$-real}
CTXT(m \in \Sigma.\mathcal{M}):
k <- \Sigma.KeyGen
c <- \Sigma.Enc(k, m)
return c
```

我们现在可以将 \(\mathcal{L}_{\text{ots\$-real}}\) 替换为 \(\mathcal{L}_{\text{ots\$-rand}}\) 并内联子程序（不展示中间库）。结果如下：

```
ATTACK(m_1, ..., m_n):
for i = 1 to n:
    c_i \leftarrow \Sigma.C
s_n \leftarrow {0, 1}^\lambda
return (c_1, ..., c_n, s_n)
```

这个最终库与第一个库不可区分。如承诺，我们证明攻击者无法将前 n 个密文与随机值区分开来，即使看到 s_n。

此证明使用了均匀密文属性，但同样的逻辑基本适用于您关心的任何加密属性——只需想象将加密步骤用不同于 \(\mathcal{L}_{\text{ots\$-real}}\) 的库来分解即可。

## 练习

### 5.1. 设 G : {0, 1}^\lambda -> {0, 1}^{\lambda+\ell} 为一个单射（即一对一）PRG。考虑以下区分器：

```
\mathcal{A}
x := QUERY()
for all s' \in {0, 1}^\lambda:
    if G(s') = x then return 1
return 0
```

- (a) A 区分 L^G_{prg-real} 和 L^G_{prg-rand} 的优势是多少？它是可忽略的吗？
- (b) 这是否与 G 是 PRG 的事实相矛盾？为什么或为什么不？
- (c) 如果 G 不是单射，优势会发生什么变化？

### 5.2. 设 G : {0, 1}^\lambda -> {0, 1}^{\lambda+\ell} 为一个单射 PRG，并考虑以下区分器：

```
\mathcal{A}
x := QUERY()
s' \leftarrow {0, 1}^\lambda
return G(s') = x
```

A 区分 L^G_{prg-real} 与 L^G_{prg-rand} 的优势是多少？

提示：在计算 Pr[A^L...] 时，根据 x 是否为 G 的可能输出来分开概率。

### 5.3. 对于任何 PRG \( G : \{0, 1\}^\lambda \to \{0, 1\}^{\lambda+\ell} \)，都会有很多 \( \{0, 1\}^{\lambda+\ell} \) 中的字符串无法作为 G 的输出。设 S 为任意一组这样的不可能的 G-输出，并考虑以下将 S 硬编码的对手：

```
\mathcal{A}
x := QUERY()
return x \in S ?
```

\( \mathcal{A} \) 区分 \( \mathcal{L}^G_{\text{prg-real}} \) 与 \( \mathcal{L}^G_{\text{prg-rand}} \) 的优势是多少？为什么像这样的对手不会自动破解每个 PRG？

### 5.4. 证明第 5.3 节中的方案不具备完美一次性保密性，方法是证明必然存在两个消息 \( m_1 \) 和 \( m_2 \)，其密文分布不同。

提示：
[反转文本块：存在字符串 s_1, s_2 ... 使得 ... 注意，攻击者知道 m_1 和 m_2 是合法的。s_1 和 s_2 ... 因为这些仅是 G 本身的属性，不取决于运行 ... 时所做的随机选择。当库 ... 加密算法 ...]

### 5.5. 要求 5.5 的证明对两次 G 调用都应用了 PRG 安全性规则，从第一次调用开始。描述当你尝试以相反顺序对这两次调用应用 G 的 PRG 安全性时会发生什么。证明是否仍然成立，还是仅在所呈现的顺序下才成立？

### 5.6. 设 \( \ell' > \ell > 0 \)。扩展“PRG 反馈”构造，将任何 stretch 为 \( \ell \) 的 PRG 转换为 stretch 为 \( \ell' \) 的 PRG。正式定义新的 PRG，并使用基础 PRG 的安全性证明其安全性。

### 5.7. 证明如果 G 是安全的 PRG，那么函数 \( H(s) = G(\bar{s}) \) 也是安全的 PRG。

### 5.8. 设 \( G : \{0, 1\}^\lambda \to \{0, 1\}^{3\lambda} \) 为安全的长度三倍 PRG。对于下面的每个函数，说明它是否也是安全的 PRG。如果该函数是安全的 PRG，给出证明。如果不是，描述一个成功的区分器并明确计算其优势。当我们写 \( a\|b\|c := G(s) \) 时，a、b、c 的长度均为 \( \lambda \)。

- (a)
```
H(s):
x||y||z := G(s)
return G(x)||G(z)
```

- (b)
```
H(s):
x||y||z := G(s)
return x||y
```

- (c)
```
H(s):
x := G(s)
y := G(s)
return x||y
```

- (d)
```
H(s):
x := G(s)
y := G(0^\lambda)
return x||y
```

- (e)
```
H(s):
x := G(s)
y := G(0^\lambda)
return x \oplus y
```

```
// H : {0, 1}^{2\lambda} \to \{0, 1\}^{3\lambda}
H(s_L || s_R):
  x := G(s_L)
  y := G(s_R)
  return x \oplus y
```

```
// H : {0, 1}^{2\lambda} \to \{0, 1\}^{\lambda}
H(s_L || s_R):
  x := G(s_L)
  y := G(s_R)
  return x || y
```

### 5.9. 设 $G : \{0, 1\}^\lambda \to \{0, 1\}^{3\lambda}$ 为安全的长度三倍 PRG。证明以下每个函数也是安全的 PRG：

```
// H : {0, 1}^{2\lambda} \to \{0, 1\}^{4\lambda}
H(s_L || s_R):
  y := G(s_R)
  return s_L || y
```

请注意，H 将其一半输入直接包含在输出中。你如何将此事实与练习 5.14(b) 的结论调和？

```
// H : {0, 1}^{2\lambda} \to \{0, 1\}^{3\lambda}
H(s_L || s_R):
  return G(s_L)
```

### ★ 5.10. 设 G 为安全的长度倍增 PRG。以下两个构造中有一个是安全的 PRG，另一个不是。孰是孰非？为其中一个给出安全证明，为另一个给出攻击。

```
H_1(s):
  x||y := G(s)
  u||v := G(y)
  return (x \oplus y)||u||v

H_2(s):
  x||y := G(s)
  u||v := G(y)
  return x||(y \oplus u)||v
```

提示：通常，如果某物不安全，它对于任何构建块选择都不安全。在这种情况下，攻击仅适用于特定的 G。基本上，你需要构造一个特定的 G，证明它是安全的 PRG，然后证明当使用此 G 时 H1/H2 不安全。

### 5.11. 密码学论坛中一个常见问题是：是否可以通过观察输出样本来确定使用了哪种 PRG 实现。

设 G_1 和 G_2 为输入/输出长度匹配的两个 PRG。定义两个库 \( \mathcal{L}_{\text{which-prg}}^{G_1} \) 和 \( \mathcal{L}_{\text{which-prg}}^{G_2} \) 如下：

```
\mathcal{L}_{\text{which-prg}}^{G_1}
QUERY():
  s \leftarrow \{0, 1\}^\lambda
  return G_1(s)
```

```
\mathcal{L}_{\text{which-prg}}^{G_2}
QUERY():
  s \leftarrow \{0, 1\}^\lambda
  return G_2(s)
```

证明，如果 G_1 和 G_2 都是安全的 PRG，那么 \( \mathcal{L}_{\text{which-prg}}^{G_1} \approx \mathcal{L}_{\text{which-prg}}^{G_2} \) —— 也就是说，仅通过接收输出样本，无法可行地区分使用了哪种 PRG。

### 5.12. 设 \( G_1 \) 和 \( G_2 \) 为确定性函数，每个接受长度为 \( \lambda \) 的输入并生成长度为 \( 3\lambda \) 的输出。

- (a) 定义函数 \( H(s_1||s_2) = G_1(s_1) \oplus G_2(s_2) \)。证明，如果 \( G_1 \) 或 \( G_2 \)（或两者）中有任何一个是安全的 PRG，那么 H 也是。
- (b) 当 \( G_1 \) 或 \( G_2 \) 中有一个是安全的 PRG 时，你对更简单的构造 \( H(s) = G_1(s) \oplus G_2(s) \) 有何看法？

### ★ 5.13. 证明，如果存在 PRG，则 P \(\neq\) NP。

### 5.14. (a) 设 \( f \) 为任意函数。证明以下函数 \( G\) **不是**安全的 PRG，无论 f 是什么。描述一个成功的区分器并明确计算其优势：

```
G(s):
return s||f(s)
```

- (b) 设 \( G : \{0, 1\}^\lambda \to \{0, 1\}^{\lambda + \ell} \) 为候选 PRG。假设存在一个多项式时间算法 V，它以非可忽略的概率反转 G。即，

\(\Pr_{s \leftarrow \{0,1\}^\lambda} [V(G(s)) = s]\) 是非可忽略的。

证明，如果存在具有此属性的算法 V，那么 G 不是安全的 PRG。换句话说，构造一个违反 G 的 PRG 安全性的区分器，并表明它能实现非可忽略的区分优势。

> 注：不要对 V 的输出做任何假设，除了上述属性。特别是，V 可能会非常频繁地输出“错误”的结果。

### 5.15. 设 \( s_0, s_1, \dots \) 和 \( t_1, t_2, \dots \) 按照对称棘轮（构造 5.9）定义。

- (a) 证明，如果 G 是安全的 PRG，那么对于任何多项式时间算法 \( \mathcal{A} \)，以下两个库不可区分：

| \( \mathcal{L}_{\text{left}} \) | \( \mathcal{L}_{\text{right}} \) |
| :--- | :--- |
| TEST(): | TEST(): |
| \( s_{n-1} \leftarrow \{0, 1\}^\lambda \) | \( s_n \leftarrow \{0, 1\}^\lambda \) |
| \( s_n || t_n := G(s_{n-1}) \) | \( \tilde{t} = \mathcal{A}(s_n) \) |
| \( \tilde{t} = \mathcal{A}(s_n) \) | \( t_n \leftarrow \{0, 1\}^\lambda \) |
| return \( \tilde{t} \stackrel{?}{=} t_n \) | return \( \tilde{t} \stackrel{?}{=} t_n \) |

- (b) 在 \( \mathcal{L}_{\text{right}} \) 中，TEST 输出 true 的概率是多少？

- (c) 证明，对于任何多项式时间算法 \( \mathcal{A} \)，\( \Pr[\mathcal{A}(s_n) = t_n] \) 是可忽略的，其中 \( s_n, t_n \) 按照对称棘轮构造生成。

