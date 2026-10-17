
```math
    <td><mtext>s.t.</mtext><mspace width="0.3em"/><mspace width="0.15em"/><mi mathvariant="bold">x</mi><mo>=</mo><mo stretchy="false">(</mo><msub><mrow><mi>x</mi></mrow><mrow><mn>1</mn></mrow></msub><momo><msub><mrow><mi>x</mi></mrow><mrow><mn>2</mn></mrow></msub><momo><mi>&#8230;</mi</momo><momo><msub><mrow><mi>x</mi></mrow><mrow><mi>D</mi></mrow></msub><mo stretchy="false">)</mo><momomo</mo></td>
  </tr>
  <tr>
    <td></td>
    <td><msub><mrow><mi>x</mi></mrow><mrow><mn>1</mn></mrow></msub><momo><msub><mrow><mi>x</mi></mrow><mrow><mn>2</mn></mrow></msub><momo><mi>&#8230;</mi</momo><momo><msub><mrow><mi>x</mi></mrow><mrow><mi>M</mi><mo>&#8722</mo><mn>1</mn></mrow></msub><mo>&#8712</mo><mo stretchy="false">\[</mo><mn>0</mn><momo><mn>1</mn><mo stretchy="false">\]</mo><momo</mo></td>
  </tr>
  <tr>
    <td></td>
    <td><msub><mrow><mi>x</mi></mrow><mrow><mi>M</mi><mo>+</mo><mi>K</mi><mo>&#8722</mo><mn>1</mn></mrow></msub><momo><mi>&#8230;</mi</momo><momo><msub><mrow><mi>x</mi></mrow><mrow><mi>D</mi></mrow></msub><mo>&#8712</mo><mo stretchy="false">\[</mo><mo>&#8722</mo><mn>1</mn><momo><mn>2</mn><mo stretchy="false">\]</mo</momo</mo></td>
  </tr>
</</table>
</mrow>
</mfenced>
</math>
```

其中 $f_1, f_2, \dots, f_M$ 是目标函数，$\mathbf{x} = (x_1, x_2, \dots, x_D)$ 是包含 $D$ 个决策变量的决策向量。决策向量 $\mathbf{x}$ 被分为三部分，其中 $x_1, x_2, \dots, x_{M-1}$ 与形状函数 $h_1, h_2, \dots, h_M$ 相关，$x_M, x_{M+1}, \dots, x_{M+K-1}$ 与景观适应度函数 $g_{ns}$ 相关，而 $x_{M+K}, x_{M+K+1}, \dots, x_D$ 与景观适应度函数 $g_s$ 相关。此外，最后 $D-M+1$ 个决策变量的下界设置为 $-1$，这与将下界设置为 0 的 ZDT 测试问题不同。

对于 SMOP 测试问题，当且仅当 $g_{ns} = 0$ 且 $g_s = 0$ 时，解是帕累托最优的，其中当 $x_1, x_2, \dots, x_{M-1}$ 取特定值时，$g_{ns}$ 可以为 0，而只有当 $x_{M+K}, x_{M+K+1}, \dots, x_D$ 被设定时，$g_s$ 才能为 0。因此，当决策变量 $x_{M+K}, x_{M+K+1}, \dots, x_D$ 为零时，这八个问题的最优解是稀疏的。此外，参数 $K$ 由下式决定：

(2.18) $K = \lceil \theta(D-M+1) \rceil$，

其中 $\theta \in [0, 1]$ 是控制帕累托最优解稀疏性的参数。

表 2.8 给出了八个 SMOP 基准测试问题的详细信息。其中涉及三种帕累托前沿，即线性帕累托前沿、凸前沿和凹凸前沿。在景观特征方面，采用了单峰、多峰、欺骗性和混合函数，这给大多数现有的多目标进化算法（MOEAs）获取稀疏最优解带来了挑战。

SMMOP 是另一种针对稀疏大规模多目标优化的基准测试集。每个 SMMOP 测试问题都有多个等效的稀疏帕累托最优解，它们在目标空间中相似但在决策空间中完全不同。这意味着 SMMOP 基准测试集是为稀疏大规模多模型多目标优化设计的。公式 (2.19) 给出了 SMMOP 测试问题的均匀设计公式。

```math
<math display="block" overflow="scroll"><mfenced open="{" close="." separators=""><mrow><mtable><mtr><mtd><msub><mrow><mi>f</mi></mrow><mrow><mn>1</mn></mrow></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo></td><td><mo>=</mo><msub><mrow><mi>h</mi></mrow><mrow><mn>1</mn></mrow></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><mo stretchy="false">(</mo><mn>1</mn><mo+</mo><mi>min</mi><mo stretchy="false">(</mo><msub><mrow><mi>g</mi></mrow><mrow><mn>1</mn></mrow></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><momo><msub><mrow><mi>g</mi></mrow><mrow><mn>2</mn></mrow></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><momo><mi>&#8230;</mi><mo>,</mo><msub><mrow><mi>g</mi></mrow><mrow><msub><mi>n</mi></mrow><mrow><mi>p</mrow></msub></mrow></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><mo stretchy="false)</mo><momo></td></mtr></mtr><mtd><msub><msub><mi>f</f</mi><mrow><mrow>mi</M</mn></mrow></msub></mo stretchymo stretchy="false="mo><mo="x="x</mo</mo="false="false="mo><mo><mo><mo><msub><msub><mi>h</mi></mrow><mrow><mn>2</mn></mo></mo><mo stretchy="momomomomomo="mox</momomomomomomo><mo stretchy="false><mo><mn>1</mo><mo+</mo><mi>min</mi><mo stretchy="false">(</mo><msub><mrow><mi>g</mi></mrow><mrow><mn>1</mn></mrow></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><momo><msub><mrow><mi>g</mi></mrow><mrow><mn>2</mn></mrow></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><momo><mi>&#8230;</mi><momomo><msub><mrow><mi>g</mi></mrow><mrow><msub><mi>n</mi></mrow><mrow><mi>p</mrow></msub></mrow></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="falsemomomomomo="momomomomomomomomomomomomomomomomo></></></momomomomoommomomomo3mo33momomomomomomo><><><><><><><><><><><><><><><><</</</</m</</omomomomomomomomomomomomomomomomomomomomomomomomomomomomomomomomommomomomomomomomomomo="mommo><mo stretchy="falsemomo><mo><="falsemmomomo><mo>1</mo><moomo><mo>min</mo><mo stretchy="falsemomo><msub><mrow><mi>g</mi></mrow><mrow><mn>1</mn></mrow></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><momo><msub><mrow><mi>g</mi></mrow><mrow><mn>2</mn></mrow></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><momo><mi>&#8230;</mi><mo>,</mo><msub><mrow><mi>g</mi></mrow><mrow><msub><mi>n</mi></mrow><mrow><mi>p</mrow></msub></mrow></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false)</mo><mo stretchy="falsemomo><mo stretchy="falsemmo><mo stretchy="falsemomo><momomomomomomomomo></td></mo><mtr><mtd></mtd><td><mi><&#8230;</mi</mo></td></mtr><mtd><msub><msub><mrow><f</f</mi><mrow><mrow>mi</M</mn></mrow></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo></td><td><mo>=</mo><msub><mrow><mi>h</mi></mrow><mrow><mi>M</mn></mrow></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><mo stretchy="false(mo><mn>1</mn><mo+</mo><mi>min</mi><mo stretchy="false">(</mo><msub><mrow><mi>g</mi></mrow><mrow><mn>1</mn></></></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false">)</mo><momo><msub><mrow><mi>g</mi></mrow><mrow><mn>2</mn></></></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="falsemomo><momo><mi>&#8230;</mi><mo>,</mo><msub><mrow><mi>g</mi></mrow><mrow><msub><mi>n</mi></mrow><mrow><mi>p</mrow></msub></mrow></msub><mo stretchy="false">(</mo><mi mathvariant="bold">x</mi><mo stretchy="false)</mo><mo stretchy="false)</mo><mo><omomom</omomommo><mo stretchy="false</mo><mo>1</mo</mo></mo</om</omom stretchyomfalse</mo><mo="bold>x</mi><mo stretchy="falsemmo><mo><><</><</</</</</</mo</mo</omomom</om</omomomomom</mo><mo stretchy="falsemomo><mo stretchy="falsemmo><mo>1</mo><moomo><mo>min</mo><mo stretchy="momomomo><mo><mrow><mi>g</mi></mo><mo><mo>1</mo></mo></mo</mo</om</mo</mo</omomomom</mo></mo</mo</mo></mo</om></om></om><mo</om></om></om></om></om></om></</></</></</></</></omom
</mo>
</math>
```

*(注：由于原文中数学公式存在大量的 OCR 识别错误和乱码，译文部分保留了其原始代码结构，仅对描述性文本进行了翻译。)*

其中 $f_1, f_2, \dots, f_M$ 是目标函数，$h_1, h_2, \dots, h_M$ 是与 $x_1, x_2, \dots, x_{M-1}$ 相关的形状函数，而 $g_1, g_2, \dots, g_{np}$ 是与 $x_M, x_{M+1}, \dots, x_D$ 相关的景观函数。

$\mathbf{x}$ 是由 $D$ 个决策变量组成的决策向量，$M$ 是目标数量。$\min(g_1(\mathbf{x}), g_2(\mathbf{x}), \dots, g_{np}(\mathbf{x}))$ 引入了 $np$ 个等效的稀疏帕累托最优解集，因为只要 $g_1, g_2, \dots, g_{np}$ 中的其中一个被最小化，该解就可以是帕累托最优。

此外，为了创建具有不同稀疏分布的等效帕累托最优解，景观函数定义为：

(2.20) $g_i(\mathbf{x})² = g_{one}(x_M+(i-1)S, x_M+(i-1)S+1, \dots, x_M+(i-1)S+1) + g_{zero}(x_M, x_{M+1}, \dots, x_D)$

其中 `g_{one} \ge 0` 在相关的决策变量被设置为指定的非零值时可以被最小化，`g_{zero} \ge 0` 在所有相关的决策变量均被设置为零时可以被最小化，而 `S` 控制帕累托最优解的稀疏性。在每个景观函数中，`g_{one}` 和 `g_{zero}` 无法同时最小化，这确保了等效帕累托最优解具有不同的稀疏分布，且等效帕累托集的数量始终等于景观函数的数量 `n_p`。

### SMMOP 基准测试套件

在 SMMOP 基准测试套件中，定义了三种形状函数和五种基础景观函数。基于这些函数，提出了八个基准测试问题，即 `SMMOP1`–`SMMOP8`。对于每个 SMMOP 测试问题，可以灵活指定决策变量的数量、目标的数量以及帕累托最优解的稀疏性，这与 SMOP 测试问题非常相似。主要区别在于 SMMOP 测试问题具有 `n_p` 个等效帕累托最优集，其中 `n_p` 也可以灵活指定。

Table 2.9 提供了八个 SMMOP 测试问题的详细信息。`g_i(x, t)` 是基础景观函数，其中 `x \in [-1, 2]` 是决策变量，`t \in [-1, 2]` 是定义 `x` 优值的参数，即景观函数在 `x = t` 时可以被最小化。值得注意的是，在八个测试问题中，`g_{one}` 的参数 `t` 被设置为 `pi/3`，这是一个多目标优化算法（MOAs）难以发现的值。`g_{zero}` 的参数 `t` 被设置为 0，即 `[-1, 2]` 的边界，这同样难以被发现。相反，如果 MOAs 考虑了帕累托解的稀疏性质，它们可能会找到它。

### 实际问题

由于 LSMOPs 泛化自现实世界，也可以使用来自实际应用中的许多问题来测试 MOAs 处理 LSMOPs 的性能，例如机器学习、网络科学、信号处理和经济学领域。现实世界中总结了 17 个 LSMOPs，其中 8 个被用作实际问题，包括特征选择、实例选择、神经网络训练、社区检测、稀疏信号重建和模式挖掘。

#### 特征选择

该问题旨在以最低的分类错误选择最少的特征。因此，它有两个优化目标，即最小化所选特征的比例以及最小化相对于所选特征的错误率。对应的问题公式如下：

```
Minimize {f1(x) = |x| / D, f2(x) = ErrorRate(x)}
```
