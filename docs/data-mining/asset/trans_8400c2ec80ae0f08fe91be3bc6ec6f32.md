
$\\sqrt{w\_{1}^{2}{(x\_{1} - y\_{1})}^{2} + w\_{2}^{2}{(x\_{2} - y\_{2})}^{2} + \\cdots + w\_{n}^{2}{(x\_{n} - y\_{n})}^{2}}.$<mml:math><mml:msqrt><mml:mrow><mml:msubsup><mml:mrow><mml:mi>w</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msubsup><mml:msup><mml:mrow><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>&#8722;</mml:mo><mml:msub><mml:mrow><mml:mi>y</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msup><mml:mo>+</mml:mo><mml:msubsup><mml:mrow><mml:mi>w</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msubsup><mml:msup><mml:mrow><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>&#8722;</mml:mo><mml:msub><mml:mrow><mml:mi>y</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msup><mml:mo>+</mml:mo><mml:mo>&#8943;</mml:mo><mml:mo>+</mml:mo><mml:msubsup><mml:mrow><mml:mi>w</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msubsup><mml:msup><mml:mrow><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub><mml:mo>&#8722;</mml:mo><mml:msub><mml:mrow><mml:mi>y</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msup></mml:mrow></mml:msqrt><mml:mo>.</mml:mo></mml:math>![方程](images/F000108si2.png)

在类别特定的特征权重的情况下，每个类别将有一套独立的权重。

所有属性权重在每个训练实例被分类后都会更新，并且最相似的范例（或每个类别中最相似的范例）被用作更新的基础。将训练实例称为 `x`，最相似的范例称为 `y`。对于每个属性 `i`，差值 |`x[i]` − `y[i]`|<mml:math><mml:mi>|</mml:mi><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mo>&#8722;</mml:mo><mml:msub><mml:mrow><mml:mi>y</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mi>|</mml:mi></mml:math>![方程](images/F000108si3.png) 是该属性对决策贡献的度量。如果该差值很小，则该属性起积极作用，而如果很大则可能起负面作用。基本思想是根据该差值的大小以及分类是否确实正确来更新第 `i` 个权重。如果分类正确，则相关权重增加；如果分类错误，则减少；增减的幅度由差值的大小决定，差值越小增减幅度越大，反之亦然。权重变化通常随后进行重归一化步骤。一种更简单的策略，可能同样有效，是如果决策正确则保持权重不变，如果决策错误则增加差异最大的那些属性的权重，从而突出差异。

检验属性加权方案是否有效的良好方法是向数据集中所有示例添加无关属性。理想情况下，引入无关属性不应影响预测质量或存储的范例数量。

### 泛化范例

在一定程度上，移除噪声或冗余的训练范例有助于理解数据的结构。为了进一步提高可解释性，范例需要被泛化。

泛化范例是实例空间中的矩形区域，称为 *超矩形*，因为它们是高维的。在对新实例进行分类时，需要如本章后面所述修改距离函数，以便能够计算到超矩形的距离。当新范例被正确分类时，它通过简单地与同一类别最近的范例合并来泛化。最近的范例可能是一个单一实例或一个超矩形。在前一种情况下，会创建一个覆盖旧实例和新实例的新超矩形。在后一种情况下，超矩形会扩大以包含新实例。最后，如果预测错误且导致错误预测的是一个超矩形，则该超矩形的边界会被改变，使其远离新实例收缩。

必须在开始时决定是否允许由嵌套或重叠超矩形引起的过度泛化。如果要避免泛化，在泛化新示例之前会进行检查，以查看特征空间的任何区域是否与拟议的新超矩形冲突。如果冲突，则中止泛化，并逐字存储该示例。请注意，重叠的超矩形与规则集中同一示例被两条或多条规则覆盖的情况完全类似。

在某些方案中，泛化范例可以嵌套，即它们可能完全包含在彼此内部，就像在某些表示中规则可能有例外一样。为此，每当示例被错误分类时，如果使用第二近邻的回退启发式会产生正确预测，则会尝试进一步泛化。此二次机会机制促进了超矩形的嵌套。如果一个示例落入错误类别的矩形内，而该矩形已包含同一类别的范例，则两者会被泛化为嵌套在原始矩形内的新的“例外”超矩形。对于嵌套的泛化范例，学习过程通常从少量种子实例开始，以防止同一类别的所有示例被泛化为覆盖大部分问题空间的单个矩形。

### 泛化范例的距离函数

使用泛化范例时，有必要将距离函数泛化，以计算实例到泛化范例的距离，以及到另一个实例的距离。实例到超矩形的距离定义为如果点位于超矩形内则为零。泛化距离函数以计算外部点到超矩形的距离的最简单方法是选择其内的最近实例并测量到该实例的距离。然而，这降低了泛化的好处，因为它重新引入了对特定单一示例的依赖。更精确地说，虽然恰好位于超矩形内的新实例继续受益于泛化，但位于外部的实例则不会。最好使用到超矩形最近部分的距离。

[图 9.1](#Ch010_347-389_B9780443158889000108.xhtml#f0010) 显示了如果距离度量调整为测量到矩形最近点的距离，则在两个矩形类别之间形成的隐式边界。即使在二维情况下，边界也包含总共九个区域（它们已编号以便易于识别）；对于更高维的超矩形，情况会更复杂。

![图 9.1 两个矩形类别之间的边界。](images/F000108f09-01-9780443158889.jpg)

[图 9.1](#Ch010_347-389_B9780443158889000108.xhtml#Bf0010) 两个矩形类别之间的边界。
