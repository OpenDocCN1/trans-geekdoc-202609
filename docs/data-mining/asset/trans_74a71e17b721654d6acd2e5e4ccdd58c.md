
$P(\\mathbf{\\theta},z \\mid \\mathbf{w},\\mathbf{\\alpha},\\mathbf{B}) = \\frac{P(\\mathbf{\\theta},z,\\mathbf{w} \\mid \\mathbf{\\alpha},\\mathbf{B})}{P(\\mathbf{w} \\mid \\mathbf{\\alpha},\\mathbf{B})}$<mml:math><mml:mi>P</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi mathvariant="bold-italic">&#952;</mml:mi><mml:mo>,</mml:mo><mml:mi>z</mml:mi><mml:mo stretchy="false" mathvariant="normal">&#8739;</mml:mo><mml:mi mathvariant="bold-italic">w</mml:mi><mml:mo>,</mml:mo><mml:mi mathvariant="bold-italic">&#945;</mml:mi><mml:mo>,</mml:mo><mml:mi mathvariant="bold-italic">B</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:mi>P</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi mathvariant="bold-italic">&#952;</mml:mi><mml:mo>,</mml:mo><mml:mi>z</mml:mi><mml:mo>,</mml:mo><mml:mi mathvariant="bold-italic">w</mml:mi><mml:mo stretchy="false" mathvariant="normal">&#8739;</mml:mo><mml:mi mathvariant="bold-italic">&#945;</mml:mi><mml:mo>,</mml:mo><mml:mi mathvariant="bold-italic">B</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:mrow><mml:mrow><mml:mi>P</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi mathvariant="bold-italic">w</mml:mi><mml:mo stretchy="false" mathvariant="normal">&#8739;</mml:mo><mml:mi mathvariant="bold-italic">&#945;</mml:mi><mml:mo>,</mml:mo><mml:mi mathvariant="bold-italic">B</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:mrow></mml:mfrac></mml:math>

![Equation](images/F000157si118.png)

遗憾的是，这不可行。对于 `M`-step，需要更新超参数 `α`<mml:math><mml:mi mathvariant="bold">&#945;</mml:mi></mml:math>![Equation](images/F000157si119.png) 和 `B`<mml:math><mml:mi mathvariant="bold">B</mml:mi></mml:math>![Equation](images/F000157si120.png)，这可以通过使用来自 `E`-step 的期望充分统计量计算最大似然估计来完成。变分 EM 过程相当于为每个 `θ[i]`<mml:math><mml:msub><mml:mrow><mml:mi mathvariant="bold">&#952;</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub></mml:math>![Equation](images/F000157si121.png) 和每个 `z[ij]` 计算并使用单独的近似后验。

一种称为“collapsed Gibbs sampling”的方法被证明是执行 `LDA^b` 的变分方法的特别有效的替代方案。首先考虑 [图 14.4B](#Ch015_516-570_B9780443158889000157.xhtml#f0025) 中的模型可以扩展为 [图 14.4C](#Ch015_516-570_B9780443158889000157.xhtml#f0025) 中所示的模型，后者最初被表述为 `LDA^b` 的平滑版本。然后在 `B`<mml:math><mml:mi mathvariant="bold">B</mml:mi></mml:math> 的主题参数上添加另一个参数由 `Γ`<mml:math><mml:mi mathvariant="bold">&#915;</mml:mi></mml:math> 给出的 Dirichlet 先验，这种表述进一步减少了过拟合的影响。标准 Gibbs 采样涉及迭代采样隐藏随机变量 `z[ij]`、 `θ[i]`’s 和矩阵 `B`<mml:math><mml:mi mathvariant="bold">B</mml:mi></mml:math> 的元素。Collapsed Gibbs 采样是通过解析地积分掉 `θ[i]`’s 和 `B`<mml:math><mml:mi mathvariant="bold">B</mml:mi></mml:math> 得到，这可以精确处理这些分布。因此，在 `Γ`<mml:math><mml:mi mathvariant="bold">&#915;</mml:mi></mml:math>、 `α`<mml:math><mml:mi mathvariant="bold">&#945;</mml:mi></mml:math> 的当前估计以及文档语料库的观测词的条件下，Gibbs 采样器只需通过迭代更新每个 `z[ij]` 来计算所需的近似后验。使用样本或变分近似，然后相对容易获得 `θ[i]`’s 和 `B`<mml:math><mml:mi mathvariant="bold">B</mml:mi></mml:math> 的估计。

使用平滑的、collapsed 的 `LDA^b` 模型从文档集合中提取主题的整体方法可概括如下。首先根据 [图 14.4C](#Ch015_516-570_B9780443158889000157.xhtml#f0025) 的结构为文档和词的联合分布定义一个分层贝叶斯模型。我们可以认为存在一个贝叶斯 `E-step`，它使用 Gibbs 采样进行近似推断，从模型中所有文档的 `joint posterior` 上对 `all` 主题进行采样，即 `P(z[ij] | w[ij], Γ, α)`<mml:math><mml:mi>P</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>z</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="italic">ij</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false" mathvariant="normal">&#8739;</mml:mo><mml:msub><mml:mrow><mml:mi>w</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="italic">ij</mml:mi></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:mi mathvariant="bold">&#915;</mml:mi><mml:mo>,</mml:mo><mml:mi mathvariant="bold">&#945;</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:math>![Equation](images/F000157si130.png)，其中 `θ[i]`’s 和 `B`<mml:math><mml:mi mathvariant="bold">B</mml:mi></mml:math> 已被积分掉。随后是 `M-step`，它使用这些样本来更新 `θ[i]`’s 和 `B`<mml:math><mml:mi mathvariant="bold">B</mml:mi></mml:math> 的估计，使用的是 `Γ`<mml:math><mml:mi mathvariant="bold">&#915;</mml:mi></mml:math>、 `α`<mml:math><mml:mi mathvariant="bold">&#945;</mml:mi></mml:math> 和样本的函数形式的更新方程。该过程在分层贝叶斯模型内执行，因此更新后的参数可用于在给定观测词的情况下创建关于新词和新主题的贝叶斯预测分布。

[表 14.1](#Ch015_516-570_B9780443158889000157.xhtml#t0010) 显示了由 [Griffiths and Steyvers (2004)](#References_705-736_B978044315888900025X.xhtml#fur235) 通过将 `LDA^b` 应用于 1991 年至 2001 年间发表于 *《美国国家科学院院刊》* 的 28,154 篇论文摘要并由作者按子类别信息标记而挖掘的主题采样中的最高概率词。分析这些标签的分布可识别出每个主题的最高概率用户标签，这些标签显示在 [表 14.1](#Ch015_516-570_B9780443158889000157.xhtml#t0010) 的底部。请注意，用户标签未用于创建主题，但我们可以看出提取的主题与人工标签的匹配程度如何。

表 14.1

从科学文章集合中提取的主题样本的最高概率词和用户标签

| Topic 2 || Topic 39 || Topic 102 || Topic 201 || Topic 210 |
| --- | --- | --- | --- | --- |
| Species || Theory || Tumor || Resistance || Synaptic |
| --- | --- | --- | --- | --- |
| Global || Time || Cancer || Resistant || Neurons |
| Climate || Space || Tumors || Drug || Postsynaptic |
| Co[2] || Given || Human || Drugs || Hippocampal |
| Water || Problem || Cells || Sensitive || Synapses |
| Geophysics, geology, ecology || Physics, math, applied math || Medical sciences || Pharmacology || Neurobiology |

![Image](images/T000157tabt0010.png)

### 因子图
