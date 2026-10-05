
它定义我们在退火过程中使用的哈密顿量。

你可能记得我们只要求 $A$ 和 $B$ 满足 $A(0) = B(T) = 1$ 且 $A(T) = B(0) = 0$，其中 $T$ 是总退火时间，但除了这些边界条件，我们没有限制 $A$ 和 $B$ 的行为。D-Wave 的退火器有默认计划。你可以在 `https://docs.dwavesys.com/latest/doc/physical_properties.html` 以及设备用户手册中的退火计划中找到它们（可以在同一个网页上找到）。我们可以通过指定我们希望函数在某些中间时间取的值来修改这些默认计划。

我们可以通过一组实数对列表来定义自定义退火计划。每对的第一个数字需要是以微秒给出的时间值，第二个数字必须是 0 到 1 之间的数。这第二个数字被称为**退火比例**（annealing fraction），用 $s$ 表示。$s$ 的值越高，$B$ 的值越高，$A$ 的值越低。结果是，当 $s=1$ 时，我们可以解释为 $B$ 为 1 且 $A$ 为 0；当 $s=0$ 时，我们可以解释为 $B$ 为 0 且 $A$ 为 1。

我们可以使用两种类型的退火计划。第一种被称为**正向退火**（forward annealing），对应于我们从本章开始一直在学习的通常过程。它从 `(0, 0)` 开始结束于 `(T, 1)`，其中 $T$ 是总退火时间。此外，$s$ 不能超过允许的最大时间。正向退火的一个示例可以是：

## 第 4 章：绝热量子计算与量子退火

| | | | | |
| :--- | :--- | :--- | :--- | :--- |
| 6 +1 -1 -1 | -1.0 | 1 | 0.0 |
| 7 +1 +1 -1 | -1.0 | 1 | 0.0 |
| 8 +1 -1 -1 | -1.0 | 1 | 0.0 |
| 9 -1 +1 -1 | -1.0 | 1 | 0.0 |

`['SPIN', 10 行, 10 个样本, 3 个变量]`

一些研究人员发现对于某些问题，反向退火（reverse annealing）比正向退火（forward annealing）更有效。非常有启发性的例子，请参阅 Carugino 等人的论文 [39]。

现在，我们已经知道如何控制退火时间和调度表。在下一个小节中，我们将解释为什么明智地选择耦合强度和惩罚项（penalty terms）非常重要，这一点很容易被忽视，但会极大地影响我们执行的结果。

### 4.4.4 耦合强度的重要性

你一定记得，在某些情况下，我们必须为一些任意常数赋值，以用于设置退火器中的耦合强度。第一种情况是将约束条件作为惩罚项引入目标函数，并使用 `dimod` 包中 `cq_to_bqm` 方法的 `lagrange_multiplier` 参数。第二种情况是为特定嵌入（embedding）中的链（chains）选择耦合强度，这通常由 `EmbeddingComposite` 等类自动处理。

认为你会希望这些常数越大越好，这是很自然的。毕竟，你对不满足问题约束的解感兴趣，也不希望你的链被断开。然而，有一个重要的细节使得选择这些常数的值比预期的要复杂一些。

### 使用 Leap 在量子退火器上求解优化问题

事实证明，D-Wave 退火器中用于比特耦合（qubit couplings）的值范围并不是任意大的。例如，以下指令允许我们检查 `Advantage_system4.1` 设备在情况下的可能值，当然，如果你更改采样器的名称，也可以获取任何其他退火器的值：

```python
sampler = DWaveSampler("Advantage_system4.1")
print("The coupling strength range is")
```

运行这些指令后你将得到如下输出：

耦合强度范围是 `[-4.0, 4.0]`

这意味着，如果你设置的耦合强度（即 $J$ 系数）的绝对值大于 4，最大的那个将被缩减为 4……而你模型中的其余系数将相应地缩放。这可能导致某些值非常接近，甚至比设备的分辨率还要近，从而影响退火过程的结果。让我们用一个例子来说明这一点。

以下代码定义了一个约束问题，使用惩罚常数 $M = 10$ 将其转换为无约束模型，然后在 `Advantage_system4.1` 上运行并获取 100 个样本。然后，它将样本转换回原始问题的变量，像我们在 4.3.3 节中所的那样聚合结果，并显示每个获得解的频率：

```python
sampler = EmbeddingComposite(DWaveSampler("Advantage_system4.1"))

# 定义问题
x0 = dimod.Binary("x0")
x1 = dimod.Binary("x1")
x2 = dimod.Binary("x2")
blp = dimod.ConstrainedQuadraticModel()
blp.set_objective(-5*x0+3*x1-2*x2)
blp.add_constraint(x0 + x2 <= 1, "First constraint")
blp.add_constraint(3*x0 - x1 + 3*x2 <= 4, "Second constraint")
```

# 转换问题并运行

```python
qubo, invert = dimod.cqm_to_bqm(blp, lagrange_multiplier = 10)
result = sampler.sample(qubo, num_reads=100)
```

# 聚合并显示结果

```python
samples = []
occurrences = []
for s in result.data():
    samples.append(invert(s))
    occurrences.append(s.num_occurrences)
sampleset = dimod.Sampleset.from_samples_cqm(samples, blp, num_occurrences=occurrences)
print("The solutions to the original problem are")
print(sampleset.filter(lambda s: s.is_feasible).aggregate())
```
