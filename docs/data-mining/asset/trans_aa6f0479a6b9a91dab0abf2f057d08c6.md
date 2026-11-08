
$\\mathbf{S}\_{W} = \\sum\\limits\_{j = 1}^{C}{\\sum\\limits\_{i:c\_{i} = j}{(\\mathbf{x}\_{i} - \\mathbf{\\mu}\_{j}){(\\mathbf{x}\_{i} - \\mathbf{\\mu}\_{j})}^{T}}}$<mml:math><mml:msub><mml:mrow><mml:mi mathvariant="bold-italic">S</mml:mi></mml:mrow><mml:mrow><mml:mi>W</mml:mi></mml:mrow></mml:msub><mml:mo>=</mml:mo><mml:munderover><mml:mo stretchy="true">&#8721;</mml:mo><mml:mrow><mml:mi>j</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:mrow><mml:mrow><mml:mi>C</mml:mi></mml:mrow></mml:munderover><mml:mrow><mml:munder><mml:mo>&#8721;</mml:mo><mml:mrow><mml:mi>i</mml:mi><mml:mo>:</mml:mo><mml:msub><mml:mrow><mml:mi>c</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mo>=</mml:mo><mml:mi>j</mml:mi></mml:mrow></mml:munder><mml:mrow><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi mathvariant="bold-italic">x</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mo>&#8722;</mml:mo><mml:msub><mml:mrow><mml:mi mathvariant="bold-italic">&#956;</mml:mi></mml:mrow><mml:mrow><mml:mi>j</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo><mml:msup><mml:mrow><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi mathvariant="bold-italic">x</mml:mi></mml:mrow><mml:mrow><mml:mi>i</mml:mi></mml:mrow></mml:msub><mml:mo>&#8722;</mml:mo><mml:msub><mml:mrow><mml:mi mathvariant="bold-italic">&#956;</mml:mi></mml:mrow><mml:mrow><mml:mi>j</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo></mml:mrow><mml:mrow><mml:mi>T</mml:mi></mml:mrow></mml:msup></mml:mrow></mml:mrow></mml:math>

![Equation](images/F000078si25.png)

$\\mathbf{S}\_{B} = \\sum\\limits\_{c = 1}^{C}{n\_{c}(\\mathbf{\\mu}\_{c} - \\mathbf{\\mu}){(\\mathbf{\\mu}\_{c} - \\mathbf{\\mu})}^{T}}.$<mml:math><mml:msub><mml:mrow><mml:mi mathvariant="bold-italic">S</mml:mi></mml:mrow><mml:mrow><mml:mi>B</mml:mi></mml:mrow></mml:msub><mml:mo>=</mml:mo><mml:munderover><mml:mo>&#8721;</mml:mo><mml:mrow><mml:mi>c</mml:mi><mml:mo>=</mml:mo><mml:mn>1</mml:mn></mml:mrow><mml:mrow><mml:mi>C</mml:mi></mml:mrow></mml:munderover><mml:mrow><mml:msub><mml:mrow><mml:mi>n</mml:mi></mml:mrow><mml:mrow><mml:mi>c</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi mathvariant="bold-italic">&#956;</mml:mi></mml:mrow><mml:mrow><mml:mi>c</mml:mi></mml:mrow></mml:msub><mml:mo>&#8722;</mml:mo><mml:mi mathvariant="bold-italic">&#956;</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:msup><mml:mrow><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi mathvariant="bold-italic">&#956;</mml:mi></mml:mrow><mml:mrow><mml:mi>c</mml:mi></mml:mrow></mml:msub><mml:mo>&#8722;</mml:mo><mml:mi mathvariant="bold-italic">&#956;</mml:mi><mml:mo stretchy="false">)</mml:mo></mml:mrow><mml:mrow><mml:mi>T</mml:mi></mml:mrow></mml:msup></mml:mrow><mml:mo>.</mml:mo></mml:math>

![Equation](images/F000078si26.png)

`A` 是使以下式最大化的矩阵

$J\\left( \\mathbf{A} \\right) = \\frac{|A^{T}\\mathbf{S}\_{B}A|}{|A^{T}\\mathbf{S}\_{W}A|}.$<mml:math><mml:mi>J</mml:mi><mml:mo>(</mml:mo><mml:mi mathvariant="bold-italic">A</mml:mi><mml:mo>)</mml:mo><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:mi mathvariant="normal">|</mml:mi><mml:msup><mml:mrow><mml:mi>A</mml:mi></mml:mrow><mml:mrow><mml:mi>T</mml:mi></mml:mrow></mml:msup><mml:msub><mml:mrow><mml:mi mathvariant="bold-italic">S</mml:mi></mml:mrow><mml:mrow><mml:mi>B</mml:mi></mml:mrow></mml:msub><mml:mi>A</mml:mi><mml:mi mathvariant="normal">|</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="normal">|</mml:mi><mml:msup><mml:mrow><mml:mi>A</mml:mi></mml:mrow><mml:mrow><mml:mi>T</mml:mi></mml:mrow></mml:msup><mml:msub><mml:mrow><mml:mi mathvariant="bold-italic">S</mml:mi></mml:mrow><mml:mrow><mml:mi>W</mml:mi></mml:mrow></mml:msub><mml:mi>A</mml:mi><mml:mi mathvariant="normal">|</mml:mi></mml:mrow></mml:mfrac><mml:mo>.</mml:mo></mml:math>

![Equation](images/F000078si27.png)

该行列式比是对先前使用的比值 `J(a)` 的推广。行列式可作为在多个维度上计算并相乘的方差的类比，但在散布矩阵的主方向上计算。

求解此问题需要复杂的线性代数。其思想是为矩阵 `A` 的每一列构造一种称为“广义特征值问题”的问题。最优 `A` 的列是对应于最大特征值 `λ[i]` 的广义特征向量 `a[i]`![Equation](images/F000078si28.png) 满足方程 `S[B]a[i] = λ[i]S[W]a[i]`![Equation](images/F000078si29.png)。([附录 A.1](#TableA1_617-636_B9780443158889000212.xhtml#TableA1_617-636_B9780443158889000212)) 提供了关于特征值和特征向量的更多信息。) 已证明解的形式为 `a = S[W]^(-1/2)U`![Equation](images/F000078si30.png)，其中 `U` 由 `S[W]^(-1/2)S[B]S[W]^(-1/2)`![Equation](images/F000078si31.png) 的特征向量得到。

Fisher 线性判别分析在实现降维方面相当流行，但对于 `C` 类，它最多只能找到 `C` – 1 维的投影。本章末尾的 *进一步阅读* 部分讨论了一种变体，该变体可以超越 `C` – 1 维并提供非线性投影。

之前的分析基于均值和散布矩阵的使用，但不像普通线性判别分析那样假设潜在的高斯分布。当然，逻辑回归，见 [第 4.6 节](#Ch004_91-164_B9780443158889000054_a.xhtml#s0095)，是创建线性二元分类器的更直接的方法。逻辑回归是应用统计中最流行的方法之一；我们在 [第 14.4 节](#Ch015_516-570_B9780443158889000157_a.xhtml#s0160) 中讨论了多类版本。

### 文本到属性向量
