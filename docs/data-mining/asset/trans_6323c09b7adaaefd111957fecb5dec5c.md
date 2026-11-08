
$B\\left( \\mathbf{\\alpha} \\right) = \\frac{\\prod\_{k = 1}^{K}\\Gamma\\left( \\alpha\_{k} \\right)}{\\Gamma{({\\sum\_{k = 1}^{K}\\alpha\_{k}})},$<mml:math><mml:mi>B</mml:mi><mml:mrow><mml:mo stretchy="true">(</mml:mo><mml:mi mathvariant="bold">&#945;</mml:mi><mml:mo stretchy="true">)</mml:mo></mml:mrow><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:msubsup><mml:mo>&#8719;</mml:mo><mml:msp1 /><mml:mrow><mml:mi>k</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:mrow><mml:msp1 /><mml:mi>K</mml:mi></mml:msubsup><mml:mi mathvariant="normal">&#915;</mml:mi><mml:mrow><mml:mo stretchy="true">(</mml:mo><mml:mrow><mml:msub><mml:mrow><mml:mi>&#945;</mml:mi></mml:mrow><mml:mrow><mml:mi>k</mml:mi></mml:mrow></mml:msub></mml:mrow><mml:mo stretchy="true">)</mml:mo></mml:mrow></mml:mrow><mml:mrow><mml:mi mathvariant="normal">&#915;</mml:mi><mml:mrow><mml:mrow><mml:mo stretchy="true">(</mml:mo></mml:mrow><mml:mrow><mml:msubsup><mml:mo>&#8721;</mml:mo><mml:msp1 /><mml:mrow><mml:mi>k</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:mrow><mml:msp1 /><mml:mi>K</mml:mi></mml:msubsup><mml:msub><mml:mrow><mml:mi>&#945;</mml:mi></mml:mrow><mml:mrow><mml:mi>k</mml:mi></mml:mrow></mml:msub></mml:mrow><mml:mrow><mml:mo stretchy="true">)</mml:mo></mml:mrow></mml:mrow></mml:mrow></mml:mfrac><mml:mo>,</mml:mo></mml:math>

![Equation](images/F000212si109.png)

其中 `Γ`(⋅)<mml:math><mml:mi mathvariant="normal">&#915;</mml:mi><mml:mrow><mml:mo stretchy="true">(</mml:mo><mml:mo>&#8901;</mml:mo><mml:mo stretchy="true">)</mml:mo></mml:mrow></mml:math>![Equation](images/F000212si110.png) 是伽马函数。

Dirichlet 分布很有用，因为它可以用作分类分布和多项分布的共轭先验分布。其均值（向量）是

$\\mathbf{\\pi}\_{D} = \\frac{\\mathbf{\\alpha}}{\\sum\_{k = 1}^{K}\\alpha\_{k}}.$<mml:math><mml:msub><mml:mrow><mml:mi mathvariant="bold">&#960;</mml:mi></mml:mrow><mml:mrow><mml:mi>D</mml:mi></mml:mrow></mml:msub><mml:mo>=</mml:mo><mml:mfrac><mml:mi mathvariant="bold">&#945;</mml:mi><mml:mrow><mml:msubsup><mml:mo>&#8721;</mml:mo><mml:msp1 /><mml:mrow><mml:mi>k</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:mrow><mml:msp1 /><mml:mi>K</mml:mi></mml:msubsup><mml:msub><mml:mrow><mml:mi>&#945;</mml:mi></mml:mrow><mml:mrow><mml:mi>k</mml:mi></mml:mrow></mml:msub></mml:mrow></mml:mfrac><mml:mo>.</mml:mo></mml:math>

![Equation](images/F000212si111.png)

它推广了具有 Beta 先验的伯努利分布的情况。也就是说，可以证明如果分类分布的传统最大似然估计由 `π`[ML] 给出，那么由分类似然和 Dirichlet 先验组成的模型的后验均值 `π`[*] 具有 Dirichlet 分布的均值形式

`π`[*] = `w``π`[*D*] + (1-`w`)`π`[*ML*],<mml:math><mml:msub><mml:mrow><mml:mi mathvariant="bold">&#960;</mml:mi></mml:mrow><mml:mrow><mml:mo>&#8270;</mml:mo></mml:mrow></mml:msub><mml:mo>=</mml:mo><mml:mi>w</mml:mi><mml:msub><mml:mrow><mml:mi mathvariant="bold">&#960;</mml:mi></mml:mrow><mml:mrow><mml:mi>D</mml:mi></mml:mrow></mml:msub><mml:mo>+</mml:mo><mml:mrow><mml:mo stretchy="true">(</mml:mo><mml:mrow><mml:mn>1</mml:mn><mml:mo>&#8722;</mml:mo><mml:mi>w</mml:mi></mml:mrow><mml:mo stretchy="true">)</mml:mo></mml:mrow><mml:msub><mml:mrow><mml:mi mathvariant="bold">&#960;</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="normal">ML</mml:mi></mml:mrow></mml:msub><mml:mo>,</mml:mo></mml:math>

![Equation](images/F000212si113.png)

其中

$w = \\frac{\\alpha\_{K}}{\\alpha\_{K} + n},\\alpha\_{K} = \\sum\\limits\_{k = 1}^{K}\\alpha\_{k},$<mml:math><mml:mi>w</mml:mi><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:msub><mml:mrow><mml:mi>&#945;</mml:mi></mml:mrow><mml:mrow><mml:mi>K</mml:mi></mml:mrow></mml:msub></mml:mrow><mml:mrow><mml:msub><mml:mrow><mml:mi>&#945;</mml:mi></mml:mrow><mml:mrow><mml:mi>K</mml:mi></mml:mrow></mml:msub><mml:mo>+</mml:mo><mml:mi>n</mml:mi></mml:mrow></mml:mfrac><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>&#945;</mml:mi></mml:mrow><mml:mrow><mml:mi>K</mml:mi></mml:mrow></mml:msub><mml:mo>=</mml:mo><mml:munderover><mml:mo>&#8721;</mml:mo><mml:mrow><mml:mi>k</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:mrow><mml:mi>K</mml:mi></mml:munderover><mml:msub><mml:mrow><mml:mi>&#945;</mml:mi></mml:mrow><mml:mrow><mml:mi>k</mml:mi></mml:mrow></mml:msub><mml:mo>,</mml:mo></mml:math>

![Equation](images/F000212si114.png)

其中 `n` 是用于估计 `π`[ML] 的示例数量。因此，在分类概率模型中将后验均值 `π`[*] 用作正则化或平滑估计以替代 `π`[ML] 的做法，在贝叶斯原理下是合理的，因为具有 Dirichlet 先验的分类模型的后验预测分布的均值等价于将 Dirichlet 后验的后验均值参数代入分类概率模型，即

$p(\\mathbf{x} \\mid D) = \\int\\limits\_{\\mathbf{\\pi}}{Cat}(\\mathbf{x} \\mid \\mathbf{\\pi}){Dirichlet}(\\mathbf{\\pi} \\mid D)d\\mathbf{\\pi} = {Cat}\\left( {\\mathbf{x};\\mathbf{\\pi}\_{\\ast}} \\right).$<mml:math><mml:mi>p</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi mathvariant="bold">x</mml:mi><mml:mo stretchy="false">&#8739;</mml:mo><mml:mi>D</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:munder><mml:mo>&#8747;</mml:mo><mml:mi mathvariant="bold">&#960;</mml:mi></mml:munder><mml:mi mathvariant="normal">Cat</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi mathvariant="bold">x</mml:mi><mml:mo stretchy="false">&#8739;</mml:mo><mml:mi mathvariant="bold">&#960;</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mi mathvariant="normal">Dirichlet</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi mathvariant="bold">&#960;</mml:mi><mml:mo stretchy="false">&#8739;</mml:mo><mml:mi>D</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mi>d</mml:mi><mml:mi mathvariant="bold">&#960;</mml:mi><mml:mo>=</mml:mo><mml:mi mathvariant="normal">Cat</mml:mi><mml:mrow><mml:mo stretchy="true">(</mml:mo><mml:mrow><mml:mi mathvariant="bold">x</mml:mi><mml:mo>;</mml:mo><mml:msub><mml:mrow><mml:mi mathvariant="bold">&#960;</mml:mi></mml:mrow><mml:mrow><mml:mo>&#8270;</mml:mo></mml:mrow></mml:msub></mml:mrow><mml:mo stretchy="true">)</mml:mo></mml:mrow><mml:mo>.</mml:mo></mml:math>

![Equation](images/F000212si116.png)

再次，将 Dirichlet 的参数向量 `α` 的每个元素 `α`[*k*] 视为虚构观测值的直观概念在贝叶斯分析下是合理的。

### 估计离散分布的参数

假设我们希望估计离散概率分布的参数，二元分布是其特例。设变量处于类别 `k` 的概率为 `π`[*k*]，并将分布的参数写为长度为 `k` 的向量 `π`。使用 one hot 向量 `x`[*i*] 编码每个示例，`i` = 1<mml:math><mml:mi>i</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:math>![Equation](images/F000212si117.png)，…，`N`，其全部为零，除了对应于观测类别的一个维度，其中 `x`[*i*, `k`] = 1<mml:math><mml:msub><mml:mrow><mml:mi>x</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi><mml:mo>,</mml:mo><mml:mi>k</mml:mi></mml:mrow></mml:msub><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:math>![Equation](images/F000212si118.png)。数据集的概率可以表示为

