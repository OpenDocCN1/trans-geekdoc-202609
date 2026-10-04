
42. `42` C. Sun, Y. Jin, R. Cheng, J. Ding, and J. Zeng, “高维困难问题的代理辅助协同群优化，” IEEE Transactions on Evolutionary Computation, vol. 21, no. 4, pp. 644–660, 2017.

# 7 电力系统中的进化大规模多目标优化

## 7.1 引言

由于技术的快速进步以及对高效、可靠和可持续能源管理日益增长的需求，电力系统变得日益复杂。可再生能源、分布式发电和智能电网技术的整合进一步增加了这种复杂性。管理和优化电力系统需要同时处理多个目标，因为系统性能的各个方面（如发电、输电、配电和消费）通常是相互关联且相互依赖的。

为了有效应对这些挑战，需要先进的优化技术，能够捕捉多个目标之间错综的关系，并为电力系统中遇到的各种问题提供高质量的解决方案。进化算法是基于种群的元启发式优化算法，能够在单次运行中获得一组权衡解，并且较不容易受到局部最优的影响。在过去的几十年里，进化算法在解决广泛领域的多目标优化问题方面取得了显著的成功。然而，当它们被用于处理大规模多目标优化问题（LSMOPs）时，其性能通常会大幅下降，这归因于维度灾难。事实上，维度灾难在电力系统中广泛存在。毕竟，电力系统中的优化问题通常有数万或更多决策变量需要优化。

本章深入探讨了进化算法在电力系统中的应用，特别关注涉及电压变器（VTs）比误差的案例研究。在案例研究中，首先，我们讨论了电压变器比误差估计的重要性以及现有方法的限限。然后，我们引入了时变比误差估计（TREE）方法，作为解决现有方法缺点的创新解决方案。接下来，我们提出了一种数据驱动的方法，将 `TREE` 问题建模为 LSMOP，详细说明了从配电系统中提取统计学原理和物理原理的过程。最后，设计了一种问题知识驱动的协同进化算法来解决 `TREE` 问题，展示了进化算法在解决电力系统复杂现实世界问题方面的潜力。

## 7.2 电压变器的比误差估计

### 7.2.1 问题介绍

电压变器是广泛应用于工业输电系统（特别是变电站）中测量电压值的基础设备。

电压变器的比误差（RE）在数学上可以表示为 [[5]](c07.xhtml#c07-bib-0005)

(7.1)![RE equals StartFraction upper V Subscript m Baseline minus upper V Subscript t Baseline Over upper V Subscript t Baseline EndFraction](img/c07-math-0001.png)

```
<math display="block" overflow="scroll"><mtext>RE</mtext><mo>=</mo><mfrac><mrow><msub><mrow><mi>V</mi></mrow><mo><mi>m</mi></mo></msub><mo>&#8722;</mo><msub><mrow><mi>V</mi></mrow><mo><mi>t</mi></mo></msub></mrow><mrow><msub><mrow><mi>V</mi></mrow><mo><mi>t</mi></mo></msub></mrow></mfrac><mo>,</mo></math>
```

其中 $V_m$ 代表由 VT 测量的一次侧电压值，而 $V_t$（始终未知）表示对应的真实一次侧电压值。图 7.1 展示了一个代表性 110 kV 变电站图，其输电系统中包含四组三相 VT。具体而言，`VT-1` 和 `VT-2` 并联测量相同的三相一次侧电压值 $A_0, B_0, C_0$，而 `VT-3` 和 `VT-4` 并联测量相同的三相二次侧电压值 $a_0, b_0, c_0$。因此，四个 VT 通过真实电压值进行相互作用。例如，`VT-1` 和 `VT-2` 测量相同的一次侧电压值，而 `VT-3` 和 `VT-4` 测量相同的二次侧电压值。由于一次侧电压值与二次侧电压值成正比，`VT-1` 和 `VT-2` 与 `VT-3` 和 `VT-4` 相关。同时，我们将第 $i$ 组 VT 获取的一次侧和二次侧电压值分别表示为 $A_i, B_i, C_i$ 和 $a_i, b_i, c_i$。在该变电站中，可以根据其中一个一次电压，例如 $(A_i - A_0)$、$(B_i - B_0)$ 或 $(C_i - C_0)$ 来计算 RE。

![图 7.1 代表性输电系统中 VT 的示意图，其中 $A_0, B_0, C_0$ 和 $a_0, b_0, c_0$ 分别为真实的一次侧和二次侧三相值。注意，一次侧和二次侧通过电力变压器连接](img/c07f001.png)

图 7.1 代表性输电系统中 VT 的示意图，其中 $A_0, B_0, C_0$ 和 $a_0, b_0, c_0$ 分别为真实的一次侧和二次侧三相电压值。注意，一次侧和二次侧通过电力变压器连接。

为了获取 VT 的 RE，主要有两种类型的方法：校准法和数据驱动估计法。校准通过切断电源并手动将未校准的 VT 与标准 VT 进行来进行 6。典型方法包括离线校准和现场校准 [7–9]。相比之下，数据驱动估计法构建 VT 的特定模型，并根据源自电气关系的约束和从 VT 收集的数据来估计 RE，例如自适应检测法 [10] 和线路参数估计法 11。然而，校准法和数据驱动估计法都存在实际中的缺陷。虽然校准法在标准工作条件下提供准确的 RE，但在时间和成本上代价较高，且必须定期使用 [6]。

在本节中，我们展示了六个不同 `TREE`（从 `TREE1` 到 `TREE6`）问题的数据驱动问题建模，将其描述为带有不等式约束的 LSMOP。根据涉及的数据，这些问题被分为三类：仅包含一次电压值的数据（第 1 类）、同时包含一次和二次电压值的数据（第 2 类）以及同时包含电压和相位角的数据（第 3 类）。图 7.2 展示了每个问题中未校准电压变压器（VT）测得的一次/二次电压值或相位角值。

![图 7.2 由真实世界未校准 VT 测量的 TREE1 到 TREE6 问题的电压（分别为 PV 和 SV）或相位角值。维度编号表示测量的样本索引。](img/c07f002.png)

图 7.2 由真实世界未校准 VT 测量的 `TREE1` 到 `TREE6` 问题的电压（分别为 PV 和 SV）或相位角值。维度编号表示测量的样本索引。

我们使用三个符号 $K$、$P$ 和 $T$ 来对 `TREE` 问题进行建模，详细设置见表 7.1。$K$ 代表一次和/或二次电压相的总数，$P$ 表示问题中涉及的 VT 组数，$T$ 是测量的序列数据的长度。

![表 7.1 每个 TREE 问题中上 M, J, K, P, T 的设置以及涉及的数据类型，其中上 M 和 J 分别表示目标数量和约束数量。](img/c07-i0038.png)

表 7.1 每个 `TREE` 问题中 $M$、$J$、$K$、$P$、$T$ 的设置以及涉及的数据类型，其中 $M$ 和 $J$ 分别表示目标和约束的数量。

在 `TREE` 问题的建模中，决策变量定义如下：

(7.2)![bold x equals (x1, ..., xT, ..., xK, ..., xT)](img/c07-math-0002)

```
<math display="block"><mi-bold="true">x</mi><mo>=</mo><mo stretchy="false">(</msub><mi>x</mi><mi>1</mi></msub><mo>,</mo><mi>&#8230</mi><mo>,</mo><msub><mi>x</mi><mi>T</mi></msub><mo>,</mo><mi>&#8230</mi><mo>,</mo><msub><mi>x</mi><mi>K</mi></msub><mo>,</mo><mi>&#8230</mi><mo>,</mo><msub><mi>x</mi><mi>T</mi></msub><mo stretchy="false">)</mo></math>
```

其中 $x_{i,j}$ 表示 `j` 时刻第 `i` 个相位（见 7.1）。决策变量的数量由 `D = K T` 给出。从 `i` 组 VT 收集的数据表示为

(7.3)![bold d equals (d1, ..., dT, ..., dK, ..., dT)](img/c07-math-0003.png)

```
<math display="block"><mi-bold="true">d</mi><mo>^i</mo</msup><mo>=</mo><mo stretchy="false">(</msub><mi>d</mi><mi>1</mi></msub><mo>,</mo><mi>&#8230</mi><mo>,</mo><msub><mi>d</mi><mi>T</mi></msub><mo>,</mo><mi>&#8230</mi><mo>,</mo><msub><mi>d</mi><mi>K</mi></msub><mo>,</mo><mi>&#8230</mi><mo>,</mo><msub><mi>d</mi><mi>T</mi></msub><mo stretchy="false">)</mo></math>
```

其中 $i \in [1, 2, \dots, P]$ 和 $d_{p,q}$ 表示 `q` 时刻的第 `p` 个测量数据。这些 VT 的相对误差（RE）可以根据 7.1 并使用 7.4 进行计算。

$$e^i = \left( \int_{x_{1,1}}^{x_{1,1}} d_{1,1}^i, \dots, \int_{x_{1,T}}^{x_{1,T}} d_{1,T}^i, \dots, \int_{x_{K,1}}^{x_{K,1}} d_{K,1}^i, \dots, \int_{x_{K,T}}^{x_{K,T}} d_{K,T}^i \right)$$

为了简化起见，RE 记为：

$$e^i = (e_{1,1}^i, \dots, e_{1,T}^i, \dots, e_{K,1}^i, \dots, e_{K,T}^i)$$

此外，RE 随时间的变化为：

$$\Delta e^i = \begin{cases} (e_{1,2}^i - e_{1,1}^i, \dots, e_{1,T}^i - e_{1,T-1}^i, \dots) \\ (e_{K,2}^i - e_{K,1}^i, \dots, e_{K,T}^i - e_{K,T-1}^i, \dots) \end{cases}$$

为了简化起见，RE 随时间的变化表示为：

$$\Delta e^i = (\Delta e_{1,1}^i, \dots, \Delta e_{1,T}^i, \dots, \Delta e_{K,1}^i, \dots, \Delta e_{K,T}^i)$$

在 `TREE6` 的情况下，从电力变压器初级侧和次级侧测量的相位角信息表示为

```math
<math display="block" overflow="scroll"><mi mathvariant="bold">&#934;</mi><mo>=</mo><mo stretchy="false">(</mo><mi mathvariant="normal">&#916;</mi><msup><mrow><mi>&#981;</mi></mrow><mrow><mn>12</mn></mrow></msup><mo>,</mo><mi mathvariant="normal">&#916;</mi><msup><mrow><mi>&#981;</mi></mrow><mrow><mn>23</mn></mrow></msup><mo>,</mo><mi mathvariant="normal">&#916;</mi><msup><mrow><mi>&#981;</mi></mrow><mrow><mn>13</mn></mrow></msup><mo stretchy="false">)</mo><momomo></math>
```

其中，
