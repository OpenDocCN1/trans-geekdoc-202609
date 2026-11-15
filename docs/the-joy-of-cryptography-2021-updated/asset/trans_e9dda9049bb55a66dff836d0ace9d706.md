

使用上述不等式，我们利用了 $q \le \sqrt{2N}$ 这一事实，因此 $\frac{q(q-1)}{2N} \le 1$（这是应用不等式 $e^{-x} \le 1 - 0.632x$ 所必需的）。因此：

\(\text{BirthdayProb}(q, N) \stackrel{\text{def}}{=} 1 - \prod_{i=1}^{q-1} \left( 1 - \frac{i}{N} \right) \ge 1 - \left( 1 - 0.632 \frac{q(q-1)}{2N} \right) = 0.632 \frac{q(q-1)}{2N}.\)

证明完成。

示例：下图是这些界限与 BirthdayProb(q, N) 实际值的对比图（N = 365 时）：

![](img/da79fa21b263fe549aecaabd2a0a41c8_89_0.png)

如前所述，在我们关心的取值范围内（$q$ 相对于 $N$ 较小），BirthdayProb(q, N) 大致呈 $q^2/N$ 增长。

## 用不可区分库表述的生日问题

下面是两个库，它们在后续主题中也将很有用。

```
\(\mathcal{L}_{\text{samp-L}}\) \\ $\text{SAMP}():$ \\ $r \leftarrow \{0, 1\}^\lambda$ \\ return $r$
```

```
\(\mathcal{L}_{\text{samp-R}}\) \\ $R := \emptyset$ \\ $\text{SAMP}():$ \\ $r \leftarrow \{0, 1\}^\lambda \setminus R$ \\ $R := R \cup \{r\}$ \\ return $r$
```

两个库都提供一个 SAMP 子例程，用于从 $\{0, 1\}^\lambda$ 中采样一个随机元素。$\mathcal{L}_{\text{samp-L}}$ 的实现每次都从 $\{0, 1\}^\lambda$ 中均匀独立地采样。它进行 **有放回采样**，因此多次调用 SAMP 可能（虽然也许不太可能）在 $\mathcal{L}_{\text{samp-L}}$ 中返回相同的值。

另一方面，$\mathcal{L}_{\text{samp-R}}$ 对 $\lambda$-比特字符串进行 **无放回采样**。它会维护一个集合 $R$，包含之前采样过的所有值，并避免再次选择它们（“$\{0, 1\}^\lambda \setminus R$” 是排除 $R$ 中元素的 $\lambda$-比特字符串集合）。在这个库中，SAMP 永远不会输出两次相同的值。

### “显而易见”的区分策略。

因此，区分这两个库的一种自然方式（但也许不是 *唯一方式*）是多次调用 SAMP。如果你曾经看到重复的输出，那么你可以确定自己连接到了 $\mathcal{L}_{\text{samp-L}}$。在多次调用 SAMP 之后，如果你仍然没有看到任何重复输出，你最终可能会停止并猜测自己连接到了 $\mathcal{L}_{\text{samp-R}}$。

令 $\mathcal{A}_q$ 表示这个“显而易见”的调用程序，它对 SAMP 进行 $q$ 次调用，如果看到重复值则返回 1。显然，当连接到 $\mathcal{L}_{\text{samp-R}}$ 时，该程序永远不会返回 1。另一方面，当连接到 $\mathcal{L}_{\text{samp-L}}$ 时，它以恰好 BirthdayProb$(q, 2^\lambda)$ 的概率返回 1。因此，$\mathcal{A}_q$ 的 *优势* 恰好是 BirthdayProb$(q, 2^\lambda)$。

该程序在这两个库的存在下表现不同，因此它们不是 *可互换* 的。但是这些库是 *不可区分* 的吗？我们已经展示了一个优势为 BirthdayProb$(q, 2^\lambda)$ 的调用程序。我们没有精确指定 $q$，但如果 $\mathcal{A}_q$ 旨在以多项式时间运行（作为 $\lambda$ 的函数），那么 $q$ 必须是 $\lambda$ 的多项式函数。那么 $\mathcal{A}_q$ 的优势是 BirthdayProb$(q, 2^\lambda) = \Theta(q^2/2^\lambda)$，这是 *可忽略* 的！

为了证明这些库是不可区分的，我们必须表明 *所有* 调用程序都具有可忽略的优势。仅展示这个 *特定* 调用程序具有可忽略优势是不够的。也许令人惊讶的是，我们考虑的“显而易见”调用程序是 *最佳可能* 的区分器！

### 引理 4.11（有放回采样）

设 $\mathcal{L}_{\text{samp-L}}$ 和 $\mathcal{L}_{\text{samp-R}}$ 如上定义。那么，对于所有对 SAMP 子例程进行 $q$ 次查询的调用程序 $\mathcal{A}$，$\mathcal{A}$ 在区分这两个库方面的优势 **最多为** BirthdayProb$(q, 2^\lambda)$。

特别是，当 $\mathcal{A}$ 为多项式时间（关于 $\lambda$）时，$q$ 作为安全参数的多项式增长。因此，$\mathcal{A}$ 具有可忽略的优势。由于这对所有多项式时间 $\mathcal{A}$ 都成立，我们有 $\mathcal{L}_{\text{samp-L}} \approx \mathcal{L}_{\text{samp-R}}$。

*证明* 考虑以下混合库：

```
$\mathcal{L}_{\text{hyb-L}}$
\( R := \emptyset \)
\( \text{bad} := 0 \)
\(\underline{\text{SAMP()}}:\)
\( r \leftarrow \{0, 1\}^\lambda \)
if \( r \in R \) then:
  \( \text{bad} := 1 \)
\( R := R \cup \{r\} \)
return \( r \)
```

```
$\mathcal{L}_{\text{hyb-R}}$
\( R := \emptyset \)
\( \text{bad} := 0 \)
\(\underline{\text{SAMP()}}:\)
\( r \leftarrow \{0, 1\}^\lambda \)
if \( r \in R \) then:
  \( \text{bad} := 1 \)
\( r \leftarrow \{0, 1\}^\lambda \setminus R \)
\( R := R \cup \{r\} \)
return \( r \)
```

首先，让我们证明关于这些库的一些简单观察：

$\mathcal{L}_{\text{hyb-L}} \equiv \mathcal{L}_{\text{samp-L}}$：请注意，$\mathcal{L}_{\text{hyb-L}}$ 只是从 $\{0, 1\}^\lambda$ 中均匀采样。$\mathcal{L}_{\text{hyb-L}}$ 中额外的 \( R \) 和 \(\text{bad}\) 变量实际上不影响其外部行为（它们仅在证明后面出于方便而使用）。

$\mathcal{L}_{\text{hyb-R}} \equiv \mathcal{L}_{\text{samp-R}}$：与 $\mathcal{L}_{\text{samp-R}}$ 仅通过从 $\{0, 1\}^\lambda \backslash R$ 采样来避免重复不同，这个库 $\mathcal{L}_{\text{hyb-R}}$ 从 $\{0, 1\}^\lambda$ 中均匀采样 $r$，如果结果恰好在 $R$ 中则重试。这种方法称为 *拒绝采样*，它与直接从 $\{0, 1\}^\lambda \backslash R$ 中采样 $r$ 具有相同的效果$^{10}$。

方便的是，$\mathcal{L}_{\text{hyb-L}}$ 和 $\mathcal{L}_{\text{hyb-R}}$ 仅在 bad = 1 时可达的代码中有所不同（高亮部分）。因此，使用引理 4.8，我们可以对调用程序的优势进行界定：

$| \Pr[\mathcal{A} \diamond \mathcal{L}_{\text{samp-L}} \Rightarrow 1] - \Pr[\mathcal{A} \diamond \mathcal{L}_{\text{samp-R}} \Rightarrow 1] |$
$= | \Pr[\mathcal{A} \diamond \mathcal{L}_{\text{hyb-L}} \Rightarrow 1] - \Pr[\mathcal{A} \diamond \mathcal{L}_{\text{hyb-R}} \Rightarrow 1] |$
$\leqslant \Pr[\mathcal{A} \diamond \mathcal{L}_{\text{hyb-L}} \text{ sets bad } := 1].$

最后，我们可以观察到，$\mathcal{A} \diamond \mathcal{L}_{\text{hyb-L}}$ 仅在看到来自 $\{0, 1\}^\lambda$ 的重复样本时才会将 bad 设为 1。这发生的概率是 BirthdayProb($q, 2^\lambda$)。$\blacksquare$

### 讨论

- 将生日问题用不可区分库来表述，使其成为未来安全证明中的有用工具。例如，在证明某个构造的安全性时，我们可以将均匀采样步骤替换为无放回采样步骤。这一变化只有可忽略的影响，但现在证明的其余部分可以利用样本永不重复这一事实。

  换句话说，在考虑密码学构造时，可以“安全地假设”随机采样的长字符串不会重复，并相应地行事。

- 然而，如果安全证明确实使用了生日库的不可区分性，这意味着当用户碰巧重复一个均匀采样的值时，该方案很可能被破解。由于当样本数量趋近于 $\sqrt{2^{\lambda+1}} \sim 2^{\lambda/2}$ 时，这变得不可避免，这意味着该方案只提供 $\lambda/2$ 位的安全性。当方案具有此属性时，我们说它具有 **生日边界安全性**。了解方案何时具有此属性很重要，因为它决定了实际中应该选择的密钥大小。

### 一个推广

如果 samp 曾经返回两次相同的值，调用程序就可以区分前面的库。在对 samp 的任何给定调用中，变量 $\mathcal{R}$ 表示导致库被区分的“有问题”的值集合。在任何时刻，$\mathcal{R}$ 只有多项式个值，因此选择这样一个有问题值的概率是可忽略的。

假设我们考虑一组不同的值被视为有问题。只要在对 samp 的每次调用中只有多项式个有问题的值，证明背后的推理就不会改变太多。这一想法导致了以下推广，其中调用程序显式地写下所有有问题的值：

10 从 $\{0, 1\}^\lambda \backslash R$ 采样的两种方法可能具有不同的运行时间，但我们的模型仅考虑库的输入输出行为。

