
## 召回-精确率曲线

| 召回-精确率曲线 || 信息检索 || 召回与精确率 || 召回与TP率 `tp` 相同，精确度为 $\\frac{TP}{{TP} + {FP}} \\times 100\\%$<mml:math><mml:mstyle displaystyle="true"><mml:mfrac><mml:mrow><mml:mi mathvariant="normal">TP</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="normal">TP</mml:mi><mml:mo>+</mml:mo><mml:mi mathvariant="normal">FP</mml:mi></mml:mrow></mml:mfrac><mml:mo>&#215;</mml:mo><mml:mn>100</mml:mn><mml:mo>%</mml:mo></mml:mstyle></mml:math>![公式](images/F000066si96.png) |

![图像](images/T000066tabt0040.png)

人们也寻求能够表征性能的单一指标。信息检索中使用的两个指标是 *3点平均召回*，它给出召回率为20%、50%和80%时获得的平均精确度，以及 *11点平均召回*，它给出召回率为0%、10%、20%、30%、40%、50%、60%、70%、80%、90%和100%时获得的平均精确度。信息检索中还使用 *F值*，其为
$\\frac{2 \\times \\mathit{recall} \\times \\mathit{precision}}{\\mathit{recall} + \\mathit{precision}} = \\frac{2 \\cdot \\mathit{TP}}{2 \\cdot \\mathit{TP} + \\mathit{FP} + \\mathit{FN}}$<mml:math><mml:mfrac><mml:mrow><mml:mn>2</mml:mn><mml:mo>&#215;</mml:mo><mml:mi mathvariant="italic">recall</mml:mi><mml:mo>&#215;</mml:mo><mml:mi mathvariant="italic">precision</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="italic">recall</mml:mi><mml:mo>+</mml:mo><mml:mi mathvariant="italic">precision</mml:mi></mml:mrow></mml:mfrac><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:mn>2</mml:mn><mml:mo>&#8901;</mml:mo><mml:mi mathvariant="italic">TP</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn><mml:mo>&#8901;</mml:mo><mml:mi mathvariant="italic">TP</mml:mi><mml:mo>+</mml:mo><mml:mi mathvariant="italic">FP</mml:mi><mml:mo>+</mml:mo><mml:mi mathvariant="italic">FN</mml:mi></mml:mrow></mml:mfrac></mml:math>
![公式](images/F000066si80.png)

不同领域使用不同的术语。医学工作者谈论诊断测试的 `sensitivity` 和 `specificity`。灵敏度是指患病者中测试结果为阳性的比例，例如 `tp`。特异度是指未患病者中测试结果为阴性的比例，即 1 –`fp`<mml:math><mml:mn>1</mml:mn><mml:mspace width="0.25em"/><mml:mi>&#8211;</mml:mi><mml:mi mathvariant="italic">fp</mml:mi></mml:math>![公式](images/F000066si81.png)。有时这些指标的乘积被用作总体衡量标准：
$\\mathit{sensitivity} \\times \\mathit{specificity} = \\mathit{tp}(1–\\mathit{fp}) = \\frac{\\mathit{TP} \\cdot \\mathit{TN}}{\\left( \\text{TP} + \\text{FN} \\right) \\cdot \\left( \\text{FP} + \\mathit{TN} \\right)}$<mml:math><mml:mi mathvariant="italic">sensitivity</mml:mi><mml:mo>&#215;</mml:mo><mml:mi mathvariant="italic">specificity</mml:mi><mml:mo>=</mml:mo><mml:mi mathvariant="italic">tp</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mn>1</mml:mn><mml:mi mathvariant="normal">&#8211;</mml:mi><mml:mi mathvariant="italic">fp</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:mi mathvariant="italic">TP</mml:mi><mml:mo>&#8901;</mml:mo><mml:mi mathvariant="italic">TN</mml:mi></mml:mrow><mml:mrow><mml:mo>(</mml:mo><mml:mtext>TP</mml:mtext><mml:mo>+</mml:mo><mml:mtext>FN</mml:mtext><mml:mo>)</mml:mo><mml:mo>&#8901;</mml:mo><mml:mo>(</mml:mo><mml:mtext>FP</mml:mtext><mml:mo>+</mml:mo><mml:mi mathvariant="italic">TN</mml:mi><mml:mo>)</mml:mo></mml:mrow></mml:mfrac></mml:math>
![公式](images/F000066si82.png)

最后，当然，还有我们老朋友的成功率：
$\\frac{\\mathit{TP} + \\mathit{TN}}{\\mathit{TP} + \\mathit{FP} + \\mathit{TN} + \\mathit{FN}}.$<mml:math><mml:mfrac><mml:mrow><mml:mi mathvariant="italic">TP</mml:mi><mml:mo>+</mml:mo><mml:mi mathvariant="italic">TN</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="italic">TP</mml:mi><mml:mo>+</mml:mo><mml:mi mathvariant="italic">FP</mml:mi><mml:mo>+</mml:mo><mml:mi mathvariant="italic">TN</mml:mi><mml:mo>+</mml:mo><mml:mi mathvariant="italic">FN</mml:mi></mml:mrow></mml:mfrac><mml:mo>.</mml:mo></mml:math>
![公式](images/F000066si83.png)

为了用单一数值概括ROC曲线，人们使用曲线下面积（AUC或ROC AUC），因为粗略地说，面积越大，模型越好。该面积还有一个很好的解释，即分类器将随机选择的正实例排在随机选择的负实例之上的概率。尽管在成本和类别分布未知且必须选择一种方案来处理所有情况时，这类指标可能有用，但没有任何单一数字能够捕捉到权衡。只能通过二维图示来完成，例如提升图、ROC曲线和召回-精确率图。

计算ROC曲线下面积常用的方法有几种。一种对应于几何解释，即通过在曲线下拟合若干梯形并求和其面积来近似。另一种是计算分类器将随机选择的正实例排在随机选择的负实例之上的概率。这可以通过计算Mann–Whitney `U` 统计量或更具体地从 `U` 统计量得到的 ρ 统计量来实现。该值可以很容易地从按正类预测概率降序排列的测试实例列表中获得。对于每个正实例，统计排在其下面的负实例数量（如果正实例和负实例排名相同，则计数增加一半）。`U` 统计量就是这些计数的总和。ρ 统计量是通过将 `U` 除以测试集中正实例数和负实例数的乘积得到的——换句话说，如果所有正实例都排在负实例之上所得到的 `U` 值。

精确率-召回曲线下面积是另一种汇总统计量，被一些从业者特别是在信息检索领域所偏好。

## 成本曲线

ROC曲线及其相关曲线对于探索不同分类器在各种场景下的权衡非常有用。然而，在存在已知错误成本的情况下，它们并不是评估机器学习模型的理想方法。例如，对于固定的成本矩阵和类别分布，很难读出分类器的预期成本。同样，你也难以确定不同分类器的适用范围。例如，从 [图 5.4](#Ch005_165-207_B9780443158889000066.xhtml#f0025) 中两个ROC曲线的交叉点，很难判断在何种成本和类别分布下分类器A优于分类器B。

*成本曲线* 是一种不同类型的显示，其中单个分类器对应一条直线，显示性能如何随类别分布变化。同样，它们在二分类情况下效果最好，尽管你总可以将多分类问题转化为二分类问题，通过 singled out 一个类别并将其与剩余类别进行评估。

[图 5.5A](#Ch005_165-207_B9780443158889000066.xhtml#f0030) 绘制了预期误差与其中一个类别的概率之间的关系。你可以想象通过以非均匀方式重采样测试集来调整该概率。我们用 + 和 − 表示两个类别。对角线显示了两个极端分类器的性能——一个总是预测 +，如果数据集中没有 + 实例，则预期误差为一，如果所有实例都是 +，则预期误差为零；另一个总是预测 −，性能相反。虚线水平线显示了总是错误的分类器的性能，而 `x`\-轴本身代表总是正确的分类器。实际上，当然，这两种情况都无法实现。好的分类器具有较低的错误率，所以你希望的位置是尽可能靠近图表底部。

