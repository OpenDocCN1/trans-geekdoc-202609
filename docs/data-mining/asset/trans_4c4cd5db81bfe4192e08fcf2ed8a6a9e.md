
第一个问题可以使用和积算法求解，第二个使用最大积算法，第三个使用 EM 算法，其中所需的期望值使用和积算法计算。如果存在对应于观测序列的隐变量序列的标记数据，则所需的条件概率分布可以像我们对贝叶斯网络所做的那样从相应的计数中计算得出。

将隐马尔可夫模型视为动态贝叶斯网络时参数估计任务与在贝叶斯网络中学习条件概率表的更新之间的唯一区别在于，可以对每个时间步获得的统计数据进行平均，因为发射矩阵和转移矩阵在每个步骤中都相同。基本的隐马尔可夫模型公式在利用更一般的动态贝叶斯网络模型随时间耦合更复杂的概率模型时可作为参考点。

### 条件随机场

隐马尔可夫模型并不是处理序列数据时唯一有用的模型。`Conditional random fields` 是一种考虑上下文的统计建模技术，通常结构化为线性链。它们广泛用于数据挖掘中的序列处理任务，但在图像处理和计算机视觉中也很流行。[图 14.12](#Ch015_516-570_B9780443158889000157_b.xhtml#f0065)说明了从电子邮件文本中提取会议地点和日期的问题，可使用链式条件随机场解决。一个主要优点是，这些模型可以被赋予输入序列的任意复杂特征以用于预测——例如，将单词匹配到组织列表并处理已知缩写的变体。

![图 14.12 从邮件中挖掘会议详情.](images/F000157f14-12-9780443158889.jpg)

图 14.12 从邮件中挖掘会议详情。

链式条件随机场的推理可以使用前面讨论的和积和最大积算法高效地执行。和积算法可用于计算学习它们所需的期望梯度，而最大积算法用于为新序列标记标签，例如指示位置或房间的“where”和与会议相关的“time”标签。

我们首先给出一般定义，然后重点关注线性条件随机场的简单情况。[图 14.13D](#Ch015_516-570_B9780443158889000157_b.xhtml#f0070)展示了一个链式条件随机场，以因子图形式表示，可与[图 14.13B](#Ch015_516-570_B9780443158889000157_b.xhtml#f0070)中描绘的马尔可夫随机场以及[图 14.13C](#Ch015_516-570_B9780443158889000157_b.xhtml#f0070)中的隐马尔可夫模型进行对比，后者也以因子图形式显示。在[图 14.13D](#Ch015_516-570_B9780443158889000157_b.xhtml#f0070)中未使用圆圈表示观测变量，因为底层条件随机场模型并未在图中将这些变量显式编码为随机变量。

![图 14.13 (A) 隐马尔可夫模型的动态贝叶斯网络表示。(B) 结构相似的马尔可夫随机场。(C) (A) 的因子图。(D) 线性链条件随机场的因子图。](images/F000157f14-13-9780443158889.jpg)

图 14.13 (A) 隐马尔可夫模型的动态贝叶斯网络表示。(B) 结构相似的马尔可夫随机场。(C) (A) 的因子图。(D) 线性链条件随机场的因子图。

#### 从马尔可夫随机场到条件随机场

虽然贝叶斯网络和马尔可夫随机场都定义了数据的联合概率模型，但条件随机场（也称为“structured prediction”技术）定义了多个预测的联合*条件*分布。对于一组随机变量 `X`，我们已经看到马尔可夫随机场如何使用指数化能量函数 `F(X)` 对 `X` 的联合分布进行分解：

$\\begin{matrix} {P\\left( X \\right) = \\frac{1}{Z}\\exp( - F\\left( X \\right)),} \\\\ {Z = \\sum\\limits\_{X}{\\exp\\left( - F\\left( X \\right) \\right)},} \\\\ \\end{matrix}$<mml:math><mml:mtable><mml:mtr><mml:mtd><mml:mi>P</mml:mi><mml:mo>(</mml:mo><mml:mi>X</mml:mi><mml:mo>)</mml:mo><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:mn>1</mml:mn></mml:mrow><mml:mrow><mml:mi>Z</mml:mi></mml:mrow></mml:mfrac><mml:mi>exp</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>&#8722;</mml:mo><mml:mi>F</mml:mi><mml:mo>(</mml:mo><mml:mi>X</mml:mi><mml:mo>)</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>,</mml:mo></mml:mtd></mml:mtr><mml:mtr><mml:mtd><mml:mi>Z</mml:mi><mml:mo>=</mml:mo><mml:munder><mml:mo>&#8721;</mml:mo><mml:mrow><mml:mi>X</mml:mi></mml:mrow></mml:munder><mml:mrow><mml:mi>exp</mml:mi><mml:mo>(</mml:mo><mml:mo>&#8722;</mml:mo><mml:mi>F</mml:mi><mml:mo>(</mml:mo><mml:mi>X</mml:mi><mml:mo>)</mml:mo><mml:mo>)</mml:mo></mml:mrow><mml:mo>,</mml:mo></mml:mtd></mml:mtr></mml:mtable></mml:math>

![方程](images/F000157si313.png)

其中求和是对 `X` 中所有变量的所有状态进行的。条件随机场对某些观测进行条件化，得出条件分布：

$\\begin{matrix} {P(Y \\mid X) = \\frac{1}{Z\\left( X \\right)}\\exp( - F(Y,X)),} \\\\ {Z\\left( X \\right) = \\sum\\limits\_{Y}{\\exp\\left( - F\\left( Y,X \\right) \\right)},} \\\\ \\end{matrix}$<mml:math><mml:mtable><mml:mtr><mml:mtd><mml:mi>P</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>Y</mml:mi><mml:mo stretchy="false" mathvariant="normal">&#8739;</mml:mo><mml:mi>X</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:mn>1</mml:mn></mml:mrow><mml:mrow><mml:mi>Z</mml:mi><mml:mo>(</mml:mo><mml:mi>X</mml:mi><mml:mo>)</mml:mo></mml:mrow></mml:mfrac><mml:mi>exp</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>&#8722;</mml:mo><mml:mi>F</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>Y</mml:mi><mml:mo>,</mml:mo><mml:mi>X</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>,</mml:mo></mml:mtd></mml:mtr><mml:mtr><mml:mtd><mml:mi>Z</mml:mi><mml:mo>(</mml:mo><mml:mi>X</mml:mi><mml:mo>)</mml:mo><mml:mo>=</mml:mo><mml:munder><mml:mo>&#8721;</mml:mo><mml:mrow><mml:mi>Y</mml:mi></mml:mrow></mml:munder><mml:mrow><mml:mi>exp</mml:mi><mml:mo>(</mml:mo><mml:mo>&#8722;</mml:mo><mml:mi>F</mml:mi><mml:mo>(</mml:mo><mml:mi>Y</mml:mi><mml:mo>,</mml:mo><mml:mi>X</mml:mi><mml:mo>)</mml:mo><mml:mo>)</mml:mo></mml:mrow><mml:mo>,</mml:mo></mml:mtd></mml:mtr></mml:mtable></mml:math>

![方程](images/F000157si314.png)

其中求和是对 `Y` 中所有变量的所有状态进行的。马尔可夫和条件随机场都可以为一般模型结构定义，但能量函数通常只包含一个或两个变量——一元和成对势。概念上，为了基于 `Y` 中变量的 `U` 个一元和 `V` 个成对函数为 `P(Y|X)` 创建条件随机场，能量函数的形式为
