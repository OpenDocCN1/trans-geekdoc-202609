
## 缺失值

$\\mathit{SDR} = \\frac{m}{\\mathit{|T|}} \\times \\lbrack\\mathit{sd}(T) - \\sum\\limits\_{j \\in \\{ L,R\\}}{\\frac{|T\_{j}|}{\\mathit{|T|}} \\times \\mathit{sd}(T\_{j})}\\rbrack,$<mml:math><mml:mi mathvariant="italic">SDR</mml:mi><mml:mo>=</mml:mo><mml:mfrac><mml:mrow><mml:mi>m</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="italic">|T|</mml:mi></mml:mrow></mml:mfrac><mml:mo>&#215;</mml:mo><mml:mo stretchy="false">\[</mml:mo><mml:mi mathvariant="italic">sd</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>T</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>&#8722;</mml:mo><mml:munder><mml:mo>&#8721;</mml:mo><mml:mrow><mml:mi>j</mml:mi><mml:mo>&#8712;</mml:mo><mml:mo stretchy="false">{</mml:mo><mml:mi>L</mml:mi><mml:mo>,</mml:mo><mml:mi>R</mml:mi><mml:mo stretchy="false">}</mml:mo></mml:mrow></mml:munder><mml:mrow><mml:mfrac><mml:mrow><mml:mi>|</mml:mi><mml:msub><mml:mrow><mml:mi>T</mml:mi></mml:mrow><mml:mrow><mml:mi>j</mml:mi></mml:mrow></mml:msub><mml:mi>|</mml:mi></mml:mrow><mml:mrow><mml:mi mathvariant="italic">|T|</mml:mi></mml:mrow></mml:mfrac><mml:mo>&#215;</mml:mo><mml:mi mathvariant="italic">sd</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>T</mml:mi></mml:mrow><mml:mrow><mml:mi>j</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo></mml:mrow><mml:mo stretchy="false">\]</mml:mo><mml:mo>,</mml:mo></mml:math>

![Equation](images/F000108si62.png)

其中 `m` 是该属性无缺失值实例的数量，而 `T` 是到达该节点的实例集合。`T[L]`、`T[R]` 是在此属性上分裂后得到的结果集合，因为现在对属性的所有测试都是二元的。

在处理训练和测试实例时，一旦选择了用于分裂的属性，就需要根据该属性的值将实例划分为子集。显而易见的问题是当该值缺失时会出现。一种称为 `surrogate splitting` 的有趣技术被开发出来来处理这种情况。它涉及找到另一个属性来代替原始属性进行分裂并使用它。属性的选择是与原始属性相关性最高的那个。然而，这种技术实现复杂且执行耗时。

一个更简单的启发式方法是用类别值作为替代属性，基于先验认为这是最可能与用于分裂的属性相关联的属性。当然，这仅在处理训练集时才有可能，因为对于测试示例类别是未知的。对于测试示例的一个简单解决方案就是简单地用到达该节点的训练示例中该属性的平均值来替换未知属性值，这对于二元属性而言相当于选择最庞大的子节点。这种简单的方法在实践中似乎效果良好。

让我们更详细地考虑在训练过程中如何使用类别值作为替代属性。我们首先处理所有分裂属性值已知的实例。我们以通常的方式确定分裂阈值，通过根据分裂属性的值对实例进行排序，并对每个可能的分裂点根据前述公式计算 SDR，选择使误差减少最大的分裂点。仅使用分裂属性值已知的实例来确定分裂点。

然后我们根据测试将这些实例划分为两个集合 `L` 和 `R`。我们确定 `L` 或 `R` 中的实例具有更大的平均类别值，并计算这两个平均值的平均值。然后，对于该属性值未知的实例，根据其类别值是否超过此总体平均值将其放入 `L` 或 `R`。如果超过，则放入 `L` 和 `R` 中平均类别值更大的那个；否则，放入平均类别值较小的那个。当分裂停止时，所有缺失值都将被到达叶节点的训练实例对应属性的平均值所替代。

### 模型树归纳的伪代码

[图 9.9](#Ch010_347-389_B9780443158889000108.xhtml#f0050) 给出了我们所描述的模型树算法的伪代码。两个主要部分是通过 `split` 逐步分裂节点来创建树，以及通过 `prune` 从叶节点向上剪枝。`node` 数据结构包含一个类型标志，指示它是内部节点还是叶节点，指向左、右子节点的指针，到达该节点的实例集合，该节点用于分裂的属性，以及表示该节点线性模型的结构。

![图 9.9 模型树归纳的伪代码。](images/F000108f09-09-9780443158889.jpg)

[图 9.9](#Ch010_347-389_B9780443158889000108.xhtml#Bf0050) 模型树归纳的伪代码。

`sd` 函数在主程序开始时以及在 `split` 开始时被调用，用于计算一组实例的类别值的标准差。随后是之前描述过的获取合成二元属性的程序。创建新节点和打印最终树的标准程序未显示。在 `split` 中，`sizeof` 返回集合中的元素数量。缺失属性值按前面所述处理。SDR 根据“缺失值”部分开头的等式计算。尽管代码中未显示，如果在属性上分裂会导致叶节点实例少于两个，则将其设为无穷大。在 `prune` 中，`linearRegression` 例程递归下降子树收集属性，对该节点处的实例作为这些属性的函数执行线性回归，然后如果这样做能改善误差估计，则贪婪地删除项，如前所述。最后，`error` 函数返回

$\\frac{n + v}{n - v} \\times \\frac{\\sum\_{\\mathit{instances}}{|\\text{deviation}{from\\ predicted\\ class}\\text{value}|}}{n},$<mml:math><mml:mfrac><mml:mrow><mml:mi>n</mml:mi><mml:mo>+</mml:mo><mml:mi>v</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi><mml:mo>&#8722;</mml:mo><mml:mi>v</mml:mi></mml:mrow></mml:mfrac><mml:mo>&#215;</mml:mo><mml:mfrac><mml:mrow><mml:msub><mml:mo>&#8721;</mml:mo><mml:mrow><mml:mi mathvariant="italic">instances</mml:mi></mml:mrow></mml:msub><mml:mrow><mml:mi>|</mml:mi><mml:mtext>deviation</mml:mtext><mml:mi mathvariant="normal">from predicted class</mml:mi><mml:mtext>value</mml:mtext><mml:mi>|</mml:mi></mml:mrow></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:mfrac><mml:mo>,</mml:mo></mml:math>

![Equation](images/F000108si63.png)

其中 `n` 是该节点处的实例数量，而 `ν` 是该节点线性模型中的参数数量。
