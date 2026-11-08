
$\\theta\_{\\mathit{MCL}} = \\text{arg}\\max\\limits\_{\\theta}\\sum\\limits\_{i = 1}^{n}{\\log\\mathit{p}(y\_{i}\\text{∣}x\_{i};\\theta)}.$<mml:math><mml:msub><mml:mrow><mml:mi>&#952;</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="italic">MCL</mml:mi></mml:mrow></mml:msub><mml:mo>=</mml:mo><mml:mrow><mml:mtext>arg</mml:mtext></mml:mrow><mml:munder><mml:mrow><mml:mi>max</mml:mi></mml:mrow><mml:mrow><mml:mi>&#952;</mml:mi></mml:mrow></mml:munder><mml:munderover><mml:mo>&#8721;</mml:mo><mml:mrow><mml:mi>i</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:munderover><mml:mrow><mml:mi mathvariant="normal">log</mml:mi><mml:mi mathvariant="italic">p</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>y</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mtext mathvariant="normal">&#8739;</mml:mtext><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mi mathvariant="normal">;</mml:mi><mml:mi>&#952;</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:mrow><mml:mo>.</mml:mo></mml:math>

![方程](images/F000145si29.png)

## 最大后验参数估计

最大似然假设所有参数值在先验上是等可能的；我们不会在考虑观测之前就认为某些参数值比其他参数值更可能。但假设我们有理由相信模型的參數遵循某种先验分布。将它们视为指定模型每个实例的随机变量时，可以应用贝叶斯规则，利用数据和参数的联合概率来计算参数的后验分布：

$p(\\theta\\text{∣}x\_{1},x\_{2},\\ldots,x\_{n}) = \\frac{p(x\_{1},x\_{2},\\ldots,x\_{n}\\text{∣}\\theta)p\\left( \\theta \\right)}{p\\left( x\_{1},x\_{2},\\ldots,x\_{n} \\right)}.$<mml:math><mml:mi>p</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>&#952;</mml:mi><mml:mtext mathvariant="normal">&#8739;</mml:mtext><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:mo>&#8230;</mml:mo><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:mi>p</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:mo>&#8230;</mml:mo><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub><mml:mtext mathvariant="normal">&#8739;</mml:mtext><mml:mi>&#952;</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mi>p</mml:mi><mml:mo>(</mml:mo><mml:mi>&#952;</mml:mi><mml:mo>)</mml:mo></mml:mrow><mml:mrow><mml:mi>p</mml:mi><mml:mo>(</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:mo>&#8230;</mml:mo><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub><mml:mo>)</mml:mo></mml:mrow></mml:mfrac><mml:mo>.</mml:mo></mml:math>

![方程](images/F000145si30.png)

由于我们计算的是参数的后验分布，因此我们使用 | 或“给定”记号代替分号。分母是一个常数，并且在假设观测是独立同分布的情况下，参数的后验概率与似然和先验的乘积成正比：

$p(\\theta\\text{∣}x\_{1},x\_{2},\\ldots,x\_{n}) \\propto \\prod\\limits\_{i = 1}^{n}{p(x\_{i};\\theta)}p\\left( \\theta \\right).$<mml:math><mml:mi>p</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>&#952;</mml:mi><mml:mtext mathvariant="normal">&#8739;</mml:mtext><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:mo>&#8230;</mml:mo><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo><mml:mo>&#8733;</mml:mo><mml:munderover><mml:mo>&#8719;</mml:mo><mml:mrow><mml:mi>i</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:munderover><mml:mrow><mml:mi>p</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mi mathvariant="normal">;</mml:mi><mml:mi>&#952;</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:mrow><mml:mi>p</mml:mi><mml:mo>(</mml:mo><mml:mi>&#952;</mml:mi><mml:mo>)</mml:mo><mml:mo>.</mml:mo></mml:math>

![方程](images/F000145si31.png)

再次切换到对数，最大后验参数估计过程寻求一个值

$\\theta\_{\\mathit{MAP}} = \\text{arg}\\max\\limits\_{\\theta}\\left\\lbrack \\sum\\limits\_{i = 1}^{n}\\log p(x\_{i};\\theta) + \\log\\mathit{p}\\left( \\theta \\right) \\right\\rbrack.$<mml:math><mml:msub><mml:mrow><mml:mi>&#952;</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="italic">MAP</mml:mi></mml:mrow></mml:msub><mml:mo>=</mml:mo><mml:mrow><mml:mtext>arg</mml:mtext></mml:mrow><mml:munder><mml:mrow><mml:mi>max</mml:mi></mml:mrow><mml:mrow><mml:mi>&#952;</mml:mi></mml:mrow></mml:munder><mml:mo>\[</mml:mo><mml:munderover><mml:mo>&#8721;</mml:mo><mml:mrow><mml:mi>i</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:munderover><mml:mrow><mml:mi mathvariant="normal">log</mml:mi></mml:mrow><mml:mi>p</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mi mathvariant="normal">;</mml:mi><mml:mi>&#952;</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>+</mml:mo><mml:mi mathvariant="normal">log</mml:mi><mml:mi mathvariant="italic">p</mml:mi><mml:mo>(</mml:mo><mml:mi>&#952;</mml:mi><mml:mo>)</mml:mo><mml:mo>\]</mml:mo><mml:mo>.</mml:mo></mml:math>

![方程](images/F000145si32.png)

同样，这一思想也可以应用于学习条件概率模型。

我们恢复使用分号记号，以强调最大后验参数估计涉及参数的点估计，在似然和先验分布下对其进行评估。这与完全贝叶斯方法形成对比，后者显式地操作参数的分布，通常通过对参数的不确定性进行积分而不是优化点估计来处理。分号被“给定”记号取代的使用在完全贝叶斯方法中更为常见，我们将遵循这一惯例。

## 13.2 贝叶斯网络

[第 4.2 节](#Ch004_91-164_B9780443158889000054.xhtml#s0020) 的朴素贝叶斯分类器和 [第 4.6 节](#Ch004_91-164_B9780443158889000054_a.xhtml#s0095) 的逻辑回归模型都产生概率估计而不是硬分类。对于每个类别值，它们估计给定实例属于该类别的概率。如果需要，大多数其他类型的分类器也可以被迫产生这种信息。例如，可以通过计算叶节点中每个类别的相对频率从决策树中获得概率，并通过检查特定规则所覆盖的实例从决策列表中获得概率。
