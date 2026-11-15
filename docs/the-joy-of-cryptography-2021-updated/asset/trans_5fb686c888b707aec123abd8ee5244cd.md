

=\left|\begin{aligned} &\left( \Pr[\mathcal{A} \diamond \mathcal{L}_{left} \Rightarrow 1 \mid \mathcal{B}_{left}] \cdot p^* + \Pr[\mathcal{A} \diamond \mathcal{L}_{left} \Rightarrow 1 \mid \overline{\mathcal{B}_{left}}](1 - p^*) \right) \\ -\left( \Pr[\mathcal{A} \diamond \mathcal{L}_{right} \Rightarrow 1 \mid \mathcal{B}_{right}] \cdot p^* + \Pr[\mathcal{A} \diamond \mathcal{L}_{right} \Rightarrow 1 \mid \overline{\mathcal{B}_{right}}](1 - p^*) \right) \end{aligned}\right|\\
=\left|\begin{aligned} &p^* \left( \Pr[\mathcal{A} \diamond \mathcal{L}_{left} \Rightarrow 1 \mid \mathcal{B}_{left}] - \Pr[\mathcal{A} \diamond \mathcal{L}_{right} \Rightarrow 1 \mid \mathcal{B}_{right}] \right) \\ &(1 - p^*) \left( \Pr[\mathcal{A} \diamond \mathcal{L}_{left} \Rightarrow 1 \mid \overline{\mathcal{B}_{left}}] - \Pr[\mathcal{A} \diamond \mathcal{L}_{right} \Rightarrow 1 \mid \overline{\mathcal{B}_{right}}] \right) \end{aligned}\right|

在表达式 \(\Pr[\mathcal{A} \diamond \mathcal{L}_{left} \Rightarrow 1 \mid \overline{\mathcal{B}_{left}}]\) 和 \(\Pr[\mathcal{A} \diamond \mathcal{L}_{right} \Rightarrow 1 \mid \overline{\mathcal{B}_{right}}]\) 中，我们条件化于 bad 永不被设置为 1。在这种情况下，两个库正在执行相同的指令序列，因此概率相等（概率差为零）。代入后，我们得到：

advantage_\mathcal{A} = p^* \left| \Pr[\mathcal{A} \diamond \mathcal{L}_{left} \Rightarrow 1 \mid \mathcal{B}_{left}] - \Pr[\mathcal{A} \diamond \mathcal{L}_{right} \Rightarrow 1 \mid \mathcal{B}_{right}] \right|

直观地讲，证明正在确认这样一个观点：只有当 bad 被设置为 1 时，才能注意到 \(\mathcal{L}_{left}\) 和 \(\mathcal{L}_{right}\) 之间的差异（这对应于我们对 \(\mathcal{B}_{left}\) 和 \(\mathcal{B}_{right}\) 的条件化）。

绝对值内的量是两个概率的差，因此其最大值可以是 1。因此，

advantage_\mathcal{A} \leq^* p^* \stackrel{\text{def}}{=} \Pr[\mathcal{B}_{left}] = \Pr[\mathcal{A} \diamond \mathcal{L}_{left} \text{ sets bad } = 1].

这就完成了证明。

**示例** 考虑之前示例中的 \(\mathcal{L}_{left}\) 和 \(\mathcal{L}_{right}\)（其中调用程序试图“预测”均匀采样的 \(\lambda\)-位字符串的结果）。我们可以用以下杂交序列证明它们不可区分：

![](img/da79fa21b263fe549aecaabd2a0a41c8_85_0.png)

让我们为每个步骤辩护：

-   \(\mathcal{L}_{left} \equiv \mathcal{L}_{hyb-L}\)：唯一的区别是 \(\mathcal{L}_{hyb-L}\) 维护了一个变量“bad”。由于它从未实际从该变量读取，此更改无任何影响。

-   \(\mathcal{L}_{hyb-L}\) 和 \(\mathcal{L}_{hyb-R}\) 仅在高亮行不同，该行仅在 \(bad = 1\) 时可达。因此，根据坏事件引理：

\left| \Pr[\mathcal{A} \diamond \mathcal{L}_{hyb-L} \Rightarrow 1] - \Pr[\mathcal{A} \diamond \mathcal{L}_{hyb-R} \Rightarrow 1] \right| \leq \Pr[\mathcal{A} \diamond \mathcal{L}_{hyb-L} \text{ sets bad } = 1].

但 \(\mathcal{A} \diamond \mathcal{L}_{\text{hyb-L}}\) 仅在调用程序在 \(\text{PREDICT}\) 的某次调用中成功预测 \(s\) 时才设置 \(bad = 1\)。在 \(\text{PREDICT}\) 有 \(q\) 次调用的情况下，此事件发生的总概率最多为 \(q/2^\lambda\)，当调用程序在多项式时间运行时这可以忽略不计。因此 \(\mathcal{L}_{\text{hyb-L}} \approx \mathcal{L}_{\text{hyb-R}}\)。

-   \(\mathcal{L}_{\text{hyb-R}} \equiv \mathcal{L}_{\text{right}}\)：与上述类似，注意 \(\mathcal{L}_{\text{hyb-R}}\) 中 \(\text{PREDICT}\) 的前 3 行实际上什么也不做。子程序无论如何都会返回 false。两个库具有相同的行为。

由于 \(\mathcal{L}_{\text{left}} \equiv \mathcal{L}_{\text{hyb-L}} \approx \mathcal{L}_{\text{hyb-R}} \equiv \mathcal{L}_{\text{right}}\)，这证明了 \(\mathcal{L}_{\text{left}} \approx \mathcal{L}_{\text{right}}\)。

## 4.4 生日概率与采样有/无放回

在许多密码学方案中，用户会反复选择随机字符串（例如，每次加密消息时），如果同一个字符串被选择两次，安全性就会被破坏。因此，重复样本的概率可以忽略不计非常重要。在本节中，我们计算此类事件的概率，并以模块化的方式表达我们的发现，即作为关于两个库不可区分性的陈述。

### 生日概率

如果房间里有 \(q\) 个人，两个人生日相同的概率是多少（假设每个人的生日均匀地从一年中可能的日子中选择）？这个问题被称为 **生日问题**，并且之所以著名，是因为答案对大多数人来说高度违背直觉。\(^9\)

让我们将问题推广。假设从 \(N\) 个项目的集合中取 \(q\) 个独立且均匀的样本。同一个值被选择超过一次的概率是多少？换句话说，以下程序输出 1 的概率是多少？

```
B(q, N)
for i := 1 to q:
    s_i <- {1, ..., N}
    for j := 1 to i - 1:
        if s_i = s_j then return 1
return 0
```

让我们为这个概率命名：

\(BirthdayProb(q, N) \stackrel{\text{def}}{=} \Pr[\mathcal{B}(q, N) \text{ outputs } 1]\).

可以为这个概率写出精确公式：

引理 4.9 \(BirthdayProb(q, N) = 1 - \prod_{i=1}^{q-1} \left( 1 - \frac{i}{N} \right)\).

\(^9\)它有时被称为“生日悖论”，尽管它实际上并不是一个悖论。真正的生日悖论在于，“生日悖论”并不是一个悖论。

证明 让我们改为计算 \(\mathcal{B}\) 输出 0 的概率，这样我们就可以进而求解它输出 1 的概率。为了让 \(\mathcal{B}\) 输出 0，它必须在主循环的每次迭代中避免提前终止条件。因此：

```
\(\text{Pr}[\mathcal{B}(q, N) \text{ outputs } 0] = \text{Pr}[\mathcal{B}(q, N) \text{ doesn't terminate early in iteration } i = 1]\)
\(\cdot \text{Pr}[\mathcal{B}(q, N) \text{ doesn't terminate early in iteration } i = 2]\)
\(\vdots\)
\(\cdot \text{Pr}[\mathcal{B}(q, N) \text{ doesn't terminate early in iteration } i = q]\)
```

在主循环的第 \(i\) 次迭代中，有 \(i-1\) 个先前选择的值 \(s_1, ..., s_{i-1}\)。如果其中任何一个再次被选为 \(s_i\)，程序就会提前终止，否则它继续到下一次迭代。换句话说，有 \(i-1\)（在 \(N\) 中）种选择 \(s_i\) 的方式会导致提前终止——\(s_i\) 的所有其他选择都避免提前终止。由于 \(s_i\) 的 \(N\) 种可能性等可能发生：

```
\(\text{Pr}[\mathcal{B}(q, N) \text{ doesn't terminate early in iteration } i] = 1 - \frac{i - 1}{N}.\)
```

把一切放在一起：

```
\(\text{BirthdayProb}(q, N) = \text{Pr}[\mathcal{B}(q, N) \text{ outputs } 1]\)
\(= 1 - \text{Pr}[\mathcal{B}(q, N) \text{ outputs } 0]\)
\(= 1 - \left(1 - \frac{1}{N}\right) \left(1 - \frac{2}{N}\right) \cdots \left(1 - \frac{q - 1}{N}\right)\)
\(= 1 - \prod_{i=1}^{q-1} \left(1 - \frac{i}{N}\right)\)
```

这就完成了证明。

### 示例

\(\text{BirthdayProb}(q, N)\) 的这个公式一眼不易理解。我们可以通过绘制它作为 \(q\) 的函数的图像来更好地了解其行为。以下是 \(N = 365\) 的图像，对应于经典的生日问题：

![](img/da79fa21b263fe549aecaabd2a0a41c8_87_0.png)

仅有 \(q = 23\) 个人时，共享生日的概率就已超过 50%。图表可以向右扩展（一直到 \(q = 365\)），但即使在 \(q = 70\) 时，概率也超过 99.9%。

### 生日概率的渐近界

拥有一个关于 BirthdayProb(q, N) 如何作为 q 和 N 的函数增长的 *渐近* 公式将会很有帮助。我们最感兴趣的是 q 相对于 N 相对较小的情况（例如，当 q 是 \(\lambda\) 的多项式函数而 N 是指数时）。

**引理 4.10**（生日界）如果 \( q \le \sqrt{2N} \)，则

\( 0.632 \frac{q(q-1)}{2N} \le \text{BirthdayProb}(q, N) \le \frac{q(q-1)}{2N} \).

由于上界和下界仅相差一个常数因子，因此写成 \(\text{BirthdayProb}(q, N) = \Theta(q^2/N)\) 是有意义的。

### 证明

我们将证明分为两部分。

-   为了证明上界，我们使用这样一个事实：当 x 和 y 为正数时，

\( (1-x)(1-y) = 1 - (x+y) + xy \ge 1 - (x+y) \).

更一般地，当所有项 \(x_i\) 为正数时，\(\prod_i(1-x_i) \ge 1 - \sum_i x_i\)。因此，\( 1 - \prod_i(1-x_i) \le 1 - (1 - \sum_i x_i) = \sum_i x_i \).

应用这一事实，

\(\text{BirthdayProb}(q, N) \stackrel{\text{def}}{=} 1 - \prod_{i=1}^{q-1} \left(1 - \frac{i}{N}\right) \le \sum_{i=1}^{q-1} \frac{i}{N} = \frac{\sum_{i=1}^{q-1} i}{N} = \frac{q(q-1)}{2N}.\)

-   为了证明下界，我们使用这样一个事实：当 \( 0 \le x \le 1 \) 时，

\( 1 - x \le e^{-x} \le 1 - 0.632x \).

下面对此作了说明。0.632 的意义在于 \( 1 - \frac{1}{e} = 0.63212 \dots \).

![](img/da79fa21b263fe549aecaabd2a0a41c8_88_0.png)

我们可以利用 \( e^{-x} \) 的上界和下界来证明如下内容：

\( \prod_{i=1}^{q-1} \left(1 - \frac{i}{N}\right) \le \prod_{i=1}^{q-1} e^{-\frac{i}{N}} = e^{-\sum_{i=1}^{q-1} \frac{i}{N}} = e^{-\frac{q(q-1)}{2N}} \le 1 - 0.632 \frac{q(q-1)}{2N} \).

