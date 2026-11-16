

![](img/fb3eb7e935470a2da12b03f528f097ee_129_0.png)

图 4.2 Eisert 等人的分布式 CNOT

考虑上面切片 1 中系统的状态，我们设 |c⟩ = α|0⟩ + β|1⟩：

在切片 1 处：(α|0⟩ + β|1⟩) ⊗ (1/√2|00⟩ + 1/√2|11⟩) ⊗ |t⟩
= (α/√2|000⟩ + α/√2|011⟩ + β/√2|100⟩ + β/√2|111⟩) ⊗ |t⟩

然后，对前两个量子比特应用 CNOT，我们在切片 2 处有：

在切片 2 处：( (α/√2|000⟩ + α/√2|011⟩ + β/√2|110⟩ + β/√2|101⟩ ) ⊗ |t⟩ )

然后，测量第二个量子比特（从上往下数），并且

- 1) 如果得到 0，并且这从 A 发送到 B，由于它是 0，X 门不应用，那么在切片 3 处，我们有：

在切片 3 处：√2 · ( (α/√2|000⟩ + β/√2|101⟩ ) ⊗ |t⟩ )
= (α|000⟩ + β|101⟩) ⊗ |t⟩

因为 1/√(第二个量子比特中测得 0 的概率) = 1/√(|α/√2|² + |β/√2|²) = 1/√(1/2) = √2，然后在 B 上局部对两个量子比特应用 CNOT：

在切片 4 处：α|000⟩|t⟩ + β|101⟩(X|t⟩)

然后，对第三行（从上往下数）应用门 H：

在切片 5 处：α|00⟩(H|0⟩)|t⟩ + β|10⟩(H|1⟩)(X|t⟩)
= α/√2 |000⟩|t⟩ + α/√2 |001⟩|t⟩ + β/√2 |100⟩(X|t⟩)
- β/√2 |101⟩(X|t⟩)

然后，测量 _B_ 处的量子比特（从上往下数第三行）：

- a) 假设我们得到 0，则有：

在切片 6 处：\(\alpha|000\rangle|t\rangle + \beta|100\rangle(X|t\rangle)\)

\(= \alpha|0\rangle|00\rangle|t\rangle + \beta|1\rangle|00\rangle(X|t\rangle)\)

并且将“0”发送到 _A_ 意味着 _Z_ 门不应用，因此，省略第二个和第三个量子比特，并添加下标，我们可以将最终状态写成

\(\alpha|0\rangle_A|t\rangle_B + \beta|1\rangle_A(X|t\rangle_B)\)

- b) 假设我们得到 1，则有：

在切片 6 处：\(\alpha|001\rangle|t\rangle - \beta|101\rangle(X|t\rangle)\)

\(= \alpha|0\rangle|01\rangle|t\rangle - \beta|1\rangle|01\rangle(X|t\rangle)\)

并且将“1”发送到 _A_ 意味着 _Z_ 门应用，因此，省略第二个和第三个量子比特，并添加下标，我们可以将最终状态写成

\(\alpha|0\rangle_A|t\rangle_B + \beta|1\rangle_A(X|t\rangle_B)\)

这与情况 (a) 相同。

- 2) 并且如果我们得到 1，并且这从 _A_ 发送到 _B_，由于它是 1，_X_ 门应用，那么在切片 3 处，我们有：

在切片 3 处：\((\alpha|010\rangle + \beta|111\rangle) \otimes |t\rangle\)

然后在 _B_ 上局部对两个量子比特应用 CNOT：

在切片 4 处：\(\alpha|010\rangle|t\rangle + \beta|111\rangle(X|t\rangle)\)

然后对第三行（从上往下数）应用门 _H_：

在切片 5 处：\(\alpha|01\rangle(H|0\rangle)|t\rangle + \beta|11\rangle(H|1\rangle)(X|t\rangle)\)

\(= \frac{\alpha}{\sqrt{2}}|010\rangle|t\rangle + \frac{\alpha}{\sqrt{2}}|011\rangle|t\rangle + \frac{\beta}{\sqrt{2}}|110\rangle(X|t\rangle)\)

\(- \frac{\beta}{\sqrt{2}}|111\rangle(X|t\rangle)\)

然后，测量 _B_ 处的量子比特（第三个量子比特或从上往下数第三行）：

- a) 假设我们得到 0，则有：

在切片 6 处：\(\alpha|010\rangle|t\rangle + \beta|110\rangle(X|t\rangle)\)

\(= \alpha|0\rangle|10\rangle|t\rangle + \beta|1\rangle|10\rangle(X|t\rangle)\)

并且将“0”发送到 _A_ 意味着 _Z_ 门不应用，因此，省略第二个和第三个量子比特，并添加下标，我们可以将最终状态写成

\(\alpha|0\rangle_A|t\rangle_B + \beta|1\rangle_A(X|t\rangle_B)\)

- b) 假设我们得到 1，则有：

在切片 6 处：\(\alpha|011\rangle|t\rangle - \beta|111\rangle(X|t\rangle)\)

\(= \alpha|0\rangle|11\rangle|t\rangle - \beta|1\rangle|11\rangle(X|t\rangle)\)

并且将"1"发送到 A 意味着 Z 门应用，因此，省略第二个和第三个量子比特，并添加下标，我们可以将最终状态写成

\(\alpha|0\rangle_A|t\rangle_B + \beta|1\rangle_A(X|t\rangle_B)\)

这与情况 (a) 相同。

请注意，如果只考虑第一个和第四个量子比特，则情况 (1)(a)、(1)(b)、(2)(b) 和 (2)(a) 都有相同的结果，这也与量子隐形传态方法的结果相同，这是我们所期望的——我们现在有了一种更高效的方法来实现分布式 CNOT。请注意，在这种方法中，分布式 CNOT 操作是使用 A 和 B 之间共享的一对纠缠量子比特（即一个 ebit）和两个经典比特（一个从 A 到 B，另一个从 B 到 A）完成的，这仅为量子隐形传态方法所需资源的一半！事实证明，如 Eisert 等人 [2000] 所示，这是最优的，即一个从 A 到 B 的经典比特通信、一个从 B 到 A 的经典比特和一个共享 ebit 共同构成了实现分布式 CNOT 门所需的最少资源。

让我们更仔细地看看上面的方法为什么有效。一个主要观察是，在两种情况下，第一个和第三个量子比特（如下面加下划线所示）在切片 3 处形成一个类猫态：

- case (1) : \((\alpha |000\rangle + \beta |101\rangle) \otimes |t\rangle\)
- case (2) : \((\alpha |010\rangle + \beta |111\rangle) \otimes |t\rangle\)

也就是说，省略第二个量子比特，两种情况下的类猫态为

\(\alpha |00\rangle |t\rangle + \beta |11\rangle (X |t\rangle)\)

来自加下划线的量子比特，其中我们看到第一个和第三个量子比特始终具有相同的值（0 或 1）——这意味着对第一个量子比特（在 A 处）进行控制等同于对第三个量子比特（即 B 处的第一个量子比特）进行控制。现在，在切片 3 处为第一个和第三个量子比特以及目标量子比特的位置添加下标：

\(\alpha |0\rangle_A |0\rangle_B |t\rangle_B + \beta |1\rangle_A |1\rangle_B (X|t\rangle_B)\)

我们看到步骤 4（B 处第三和第四个量子比特之间的本地 CNOT）实际上是第一个量子比特（在 A 处）和第四个量子比特（在 B 处）之间的 CNOT！

分布此类类猫态是利用纠缠作为资源实现分布式控制门的关键。一般而言，我们可以通过以下电路总结这一概念——其中第二个量子比特被省略。

![](img/fb3eb7e935470a2da12b03f528f097ee_132_0.png)

如果控制量子比特是类猫态 \(\alpha|00\rangle + \beta|11\rangle\) 中的两个量子比特之一，则目标将以相同方式受到影响，因为这两个量子比特将具有有效相同的状态，它们以概率 \(|\alpha|^2\) 同时为 0，或以概率 \(|\beta|^2\) 同时为 1。这意味着如果类猫态 \(|c\rangle\) 的两个量子比特分布在不同机器上，则可以对其中任意一个进行控制。请注意，应用 \(H\) 门（即图 4.2 中从第 4 张幻灯片开始的步骤）以及测量并发送测量结果以控制 \(Z\) 的目的是，在完成分布式 CNOT 后，将第一个量子比特（在 \(A\) 处）与第三个量子比特（即 \(B\) 的第一个量子比特）解纠缠。

## 4.2 超越分布式 CNOT

我们可以从多方面推广上述内容：

- 在不同机器上对多个目标量子比特使用相同的控制量子比特；
- 使用不同机器上的多个控制量子比特来控制同一目标量子比特；以及
- 从对目标量子比特执行 NOT 运算超越到执行一般单位运算 \(U\)。

我们将在本节中考察这些内容。

### 4.2.1 不同机器上多个目标量子比特共用同一控制量子比特

假设我们想使用 \(A\) 中的控制量子比特来控制多个其他机器上的目标量子比特。当然，一种方法是将控制量子比特依次隐形传态到每个机器，并在每个机器上对接收到的量子比特进行控制。然而，一种更高效的方法是将此类类猫态推广到超过两个量子比特，采用第 2 章中提到的 GHZ 态形式。考虑下面的三个量子比特类猫态示例。

![](img/fb3eb7e935470a2da12b03f528f097ee_132_1.png)

如果控制量子比特是类猫态 \(\alpha|000\rangle + \beta|111\rangle\) 中的三个量子比特之一，则目标将以相同方式受到影响，因为这三个量子比特将具有相同的状态，它们以概率 \(|\alpha|^2\) 同时为 0，或以概率 \(|\beta|^2\) 同时为 1。

让我们详细看看这是如何工作的。从单目标情况推广，让我们考虑另一台机器 \(C\)，它也有一个量子比特 \(|s\rangle\) 由 \(A\) 处的量子比特 \(|c\rangle\) 进行控制，如图 4.3 所示。请注意，三个节点共享一个（分布式）GHZ 态（每个节点一个量子比特），由三个节点间的波浪线标记。$^1$

现在考虑图 4.3 中切片 1 处系统的状态，我们设 \(|c\rangle = \alpha|0\rangle + \beta|1\rangle\)，并重新排序表达式中的量子比特，即将 \(B\) 的目标量子比特写在 \(C\) 的目标量子比特之前：

```
at slice 1 : (\( \alpha |0\rangle + \beta |1\rangle \)) \(\otimes\) (\( \frac{1}{\sqrt{2}}|000\rangle + \frac{1}{\sqrt{2}}|111\rangle \)) \(\otimes |t\rangle \otimes |s\rangle\)

= (\( \frac{\alpha}{\sqrt{2}}|0000\rangle + \frac{\alpha}{\sqrt{2}}|0111\rangle + \frac{\beta}{\sqrt{2}}|1000\rangle + \frac{\beta}{\sqrt{2}}|1111\rangle \))

\(\otimes |t\rangle \otimes |s\rangle\)
```

然后，对前两个量子比特应用 CNOT，我们在切片 2 处有：

```
at slice 2 : (\( \frac{\alpha}{\sqrt{2}}|0000\rangle + \frac{\alpha}{\sqrt{2}}|0111\rangle + \frac{\beta}{\sqrt{2}}|1100\rangle + \frac{\beta}{\sqrt{2}}|1011\rangle \))

\(\otimes |t\rangle \otimes |s\rangle\)
```

1 分布式 GHZ 态可以通过融合多个 Bell 对创建，如第 2 章所述。例如，如果我们在 A 和 B 之间（量子比特 a 和 b1）以及在 B 和 C 之间（量子比特 b2 和 c）拥有（分布式）Bell 对，如下所示：\((|00\rangle_{ab_1} + |11\rangle_{ab_1}\))/\(\sqrt{2}\) 和 (\(|00\rangle_{b_2c} + |11\rangle_{b_2c}\))/\(\sqrt{2}\)，那么可以在 B 和 C 上执行以下操作（Pauli 门修正 X\(^m\)，取决于从 B 发送到 C 的 b2 的测量结果 m \(\in\) {0, 1}）来合并两个 Bell 对形成 GHZ 态：

![](img/fb3eb7e935470a2da12b03f528f097ee_133_0.png)

生成的状态是一个跨越 A、B 和 C 分布的 GHZ 态。创建 n 量子比特 GHZ 态的协议在 de Bone 等人 [2020] 中有详细讨论。这样的电路（包括从初始态（两个 \(|00\rangle\) 对）生成两个 Bell 对的组件，可以封装为一个门）可能被称为纠缠门，记为 E2，或更一般地，En 用于生成 \(|GHZ_n\rangle\)。请注意，Bell 对各自分布在两个节点之间。

