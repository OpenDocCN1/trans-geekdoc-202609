
# 小批量随机梯度下降

随机梯度下降根据从一个示例计算得到的梯度来更新模型参数。小批量变体使用数据的一个小子集，并基于批次中示例的平均梯度来更新参数。这与常规流程完全相同——初始化参数，进入参数更新循环，并通过监控验证集来终止。然而，与标准随机梯度下降相反，主循环遍历从训练集获得的小批量，并在处理完每个批次后更新参数。通常这些批次是训练集的随机选择的互不相交的子集，可能在每个 epoch 后进行洗牌，具体取决于所需的时间。

Each pass through a set of mini-batches that represent the complete training set is an epoch. 使用经验风险加上正则化项作为目标函数，处理完一个小批量后，参数按如下方式更新

$\\left. \\mathbf{\\theta}^{\\mathit{new}}\\leftarrow\\mathbf{\\theta} - \\eta\_{t}\\left\\lbrack \\frac{1}{B\_{k}}\\sum\\limits\_{i \\in I}\\left\\lbrack \\frac{\\partial}{\\partial\\mathbf{\\theta}}L(f(\\mathbf{x}\_{i};\\mathbf{\\theta}),\\mathbf{y}\_{i}) \\right\\rbrack + \\frac{B\_{k}}{N}\\lambda\\frac{\\partial}{\\partial\\mathbf{\\theta}}R\\left( \\mathbf{\\theta} \\right) \\right\\rbrack, \\right.$<mml:math><mml:msup><mml:mrow><mml:mi mathvariant="bold-italic">&#952;</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="italic">new</mml:mi></mml:mrow></mml:msup><mml:mo>&#8592;</mml:mo><mml:mi mathvariant="bold-italic">&#952;</mml:mi><mml:mo>&#8722;</mml:mo><mml:msub><mml:mrow><mml:mi>&#951;</mml:mi></mml:mrow><mml:mrow><mml:mi>t</mml:mi></mml:mrow></mml:msub><mml:mo>\[</mml:mo><mml:mfrac><mml:mrow><mml:mn>1</mml:mn></mml:mrow><mml:mrow><mml:msub><mml:mrow><mml:mi>B</mml:mi></mml:mrow><mml:mrow><mml:mi>k</mml:mi></mml:mrow></mml:msub></mml:mrow></mml:mfrac><mml:munder><mml:mo>&#8721;</mml:mo><mml:mrow><mml:mi>i</mml:mi><mml:mo>&#8712;</mml:mo><mml:mi>I</mml:mi></mml:mrow></mml:munder><mml:mrow><mml:mo>\[</mml:mo><mml:mfrac><mml:mrow><mml:mo>&#8706;</mml:mo></mml:mrow><mml:mrow><mml:mo>&#8706;</mml:mo><mml:mi mathvariant="bold-italic">&#952;</mml:mi></mml:mrow></mml:mfrac><mml:mi>L</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>f</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi mathvariant="bold-italic">x</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mi mathvariant="normal">;</mml:mi><mml:mi mathvariant="bold-italic">&#952;</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi mathvariant="bold-italic">y</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo><mml:mo>\]</mml:mo></mml:mrow><mml:mo>+</mml:mo><mml:mfrac><mml:mrow><mml:msub><mml:mrow><mml:mi>B</mml:mi></mml:mrow><mml:mrow><mml:mi>k</mml:mi></mml:mrow></mml:msub></mml:mrow><mml:mrow><mml:mi>N</mml:mi></mml:mrow></mml:mfrac><mml:mi>&#955;</mml:mi><mml:mfrac><mml:mrow><mml:mo>&#8706;</mml:mo></mml:mrow><mml:mrow><mml:mo>&#8706;</mml:mo><mml:mi mathvariant="bold-italic">&#952;</mml:mi></mml:mrow></mml:mfrac><mml:mi>R</mml:mi><mml:mo>(</mml:mo><mml:mi mathvariant="bold-italic">&#952;</mml:mi><mml:mo>)</mml:mo><mml:mo>\]</mml:mo><mml:mo>,</mml:mo></mml:math>

![方程](images/F00011Xsi37.png)

其中 `η[t]` 是学习率（可能取决于 epoch `t`）；第 `k` 个批次包含 `B[k]` 个示例，并由索引集合 `I` = `I(t, k)` 表示，该集合指向原始数据；`N` 是训练集的大小；`L(f(x[i]; θ), y[i])` 是示例 `x[i]`、标签 `y[i]` 和参数 `θ` 的损失；`R(θ)` 是正则化项，权重为 `λ`。在一种极端情况下，单个小批量包含整个训练集，即批量梯度下降的标准更新；而在另一种极端情况下，批量大小为 1，即标准单示例随机梯度下降更新。

小批量通常包含几十到数百个示例，尽管对于大型模型，选择可能受计算资源限制。批量大小通常会影响学习的稳定性和速度；某些大小对于给定的模型和数据集特别有效。有时会在启动长时间优化之前，对一组潜在的批量大小进行搜索，以找到一个效果良好的大小。

批次中类别标签的混合会影响结果。对于不平衡数据，使用标签平衡的小批量预训练模型，然后使用不平衡的标签统计信息微调上层或多层可能有优势。这可能涉及实现一种采样方案，确保在循环遍历示例时，它们以无偏的方式呈现给学习过程。

## 基于小批量的随机梯度下降的伪代码

给定数据 `x[i]`、`y[i]`、`I` = 1, …, `N`、具有参数 `θ` 的损失函数 `L[f(x[i]; θ), y[i]]`，以及由 `λ` 加权的参数正则化项 `R(θ)`，我们希望优化经验风险加上正则化项，即，
