

尽管很受欢迎，但很少有专家推荐使用 `GradientDescentOptimizer` 而不是其他替代方案。要了解原因，你需要理解它用于执行优化的算法。在本讨论中，我将介绍梯度下降的理论，然后解释如何在代码中创建和使用 `GradientDescentOptimizer`。

## 梯度下降算法

`GradientDescentOptimizer` 使用梯度下降算法最小化损失，该算法依赖于一个关键的数学事实：在某一点上，函数沿其负梯度方向下降最快。

如果你学过微积分，你就知道函数在某一点的导数等于函数在该点的斜率。也就是说，如果 `f(x)` 可微，其关于 *x* 的导数记为 `f'(x)`，而在点 *a* 处的斜率记为 `f'(a)`。[图 5-1](#09_9788126592555-ch05.xhtml#c05-fig-0001) 显示了函数导数的样子。

![FIGURE 5-1: The derivative at a point equals the slope of the curve at that point.](images/9788126592555-fg0501.png)

[FIGURE 5-1:](#09_9788126592555-ch05.xhtml#rc05-fig-0001) The derivative at a point equals the slope of the curve at that point.

具有多个变量的函数有多个导数。以 `f(x, y)` 为例，它有关于 *x* 的导数和关于 *y* 的导数。这些是 *偏导数*，用以下记号表示：

![images](images/eq05003.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mtable columnalign="left"><m:mtr><m:mtd><m:mi mathvariant="normal">Partial&#160;derivative&#160;of&#160;f(x,&#160;y)&#160;with&#160;respect&#160;to&#160;x:&#160;</m:mi><m:mfrac><m:mrow><m:mo>&#8706;</m:mo><m:mi>f</m:mi></m:mrow><m:mrow><m:mo>&#8706;</m:mo><m:mi>x</m:mi></m:mrow></m:mfrac></m:mtd></m:mtr><m:mtr><m:mtd><m:mi mathvariant="normal">Partial&#160;derivative&#160;of&#160;f(x,&#160;y)&#160;with&#160;respect&#160;to&#160;y:&#160;</m:mi><m:mfrac><m:mrow><m:mo>&#8706;</m:mo><m:mi>f</m:mi></m:mrow><m:mrow><m:mo>&#8706;</m:mo><m:mi>y</m:mi></m:mrow></m:mfrac></m:mtd></m:mtr></m:mtable></m:math> 

[图 5-2](#09_9788126592555-ch05.xhtml#c05-fig-0002) 描绘了关系 ![images](images/eq05004.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi mathvariant="normal">f</m:mi><m:mrow><m:mo>(</m:mo><m:mrow><m:mi mathvariant="normal">x</m:mi><m:mo>,</m:mo><m:mi mathvariant="normal">&#160;y</m:mi></m:mrow><m:mo>)</m:mo></m:mrow><m:mo>=</m:mo><m:mn>16</m:mn><m:mo>&#45;</m:mo><m:mn>4</m:mn><m:msup><m:mi mathvariant="normal">x</m:mi><m:mn>2</m:mn></m:msup><m:mo>&#45;</m:mo><m:mn>2</m:mn><m:msup><m:mi mathvariant="normal">y</m:mi><m:mn>2</m:mn></m:msup></m:mrow></m:math>。在点 (1, 2) 处，关于 *x* 的偏导数为 –8，关于 *y* 的偏导数为 –8。

![FIGURE 5-2: The gradient points in the direction of steepest ascent.](images/9788126592555-fg0502.png)

[FIGURE 5-2:](#09_9788126592555-ch05.xhtml#rc05-fig-0002) The gradient points in the direction of steepest ascent.

从几何上讲，*向量* 是一个具有大小和方向的量。向量可以用分量来定义，这些分量标识其在正交方向上的大小。你可以将向量视为空间中的箭头。如果一个向量在正 x 方向上指向两个单位，在负 y 方向上指向三个单位，它可以表示为 <2, -3>。

梯度下降算法关注一种特殊的向量，称为 *梯度*。函数的梯度是一个向量，其分量等于函数的偏导数。*f* 的梯度记为 ∇*f*，如果函数有三个变量，可以将其梯度表示如下：

![images](images/eq05005.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mo>&#8711;</m:mo><m:mi>f</m:mi><m:mo stretchy="false">(</m:mo><m:mi>x</m:mi><m:mo>,</m:mo><m:mi>y</m:mi><m:mo>,</m:mo><m:mi>z</m:mi><m:mo stretchy="false">)</m:mo><m:mo>=</m:mo><m:mrow><m:mo>\[</m:mo><m:mrow><m:mfrac><m:mrow><m:mo>&#8706;</m:mo><m:mi>f</m:mi></m:mrow><m:mrow><m:mo>&#8706;</m:mo><m:mi>x</m:mi></m:mrow></m:mfrac><m:mo>,</m:mo><m:mfrac><m:mrow><m:mo>&#8706;</m:mo><m:mi>f</m:mi></m:mrow><m:mrow><m:mo>&#8706;</m:mo><m:mi>y</m:mi></m:mrow></m:mfrac><m:mo>,</m:mo><m:mfrac><m:mrow><m:mo>&#8706;</m:mo><m:mi>f</m:mi></m:mrow><m:mrow><m:mo>&#8706;</m:mo><m:mi>z</m:mi></m:mrow></m:mfrac></m:mrow><m:mo>\]</m:mo></m:mrow></m:mrow></m:math> 

如果函数有两个变量，其梯度向量将有两个分量。在 [图 5-2](#09_9788126592555-ch05.xhtml#c05-fig-0002) 中，(1, 2) 处的梯度是向量 <-8, -8>。该向量由从点 (1, 2) 延伸出的黑色箭头表示。

假设图中函数代表瑞士阿尔卑斯山的一座山。如果你是一名阿尔卑斯登山者，梯度标识了最陡的攀登方向。这种指定并非巧合。函数的梯度始终指向最陡上升的方向。同样，反向向量标识了最陡下降的方向。

在你理解了梯度的意义后，你就可以着手解决梯度下降算法了。该算法计算损失的梯度并更新模型的变量，直到损失的梯度降为零。为了以数学方式表达此操作，我需要引入一些记号：

* 可训练变量的集合记为 `θ`。第 *t* 步变量的值记为 `θ[t]`。
* 损失，即包含模型变量的数学关系，记为 `J(θ)`。损失的梯度为 `∇J(θ)`。
* 学习率，记为 `η`，是影响 `θ[j]` 从一步到下一步变化多少的值。

有了这个记号，你可以用以下方程表达 `GradientDescentOptimizer` 的每次优化步骤：

![images](images/eq05006.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:msub><m:mi>&#952;</m:mi><m:mi>t</m:mi></m:msub><m:mo>=</m:mo><m:msub><m:mi>&#952;</m:mi><m:mrow><m:mi>t</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn></m:mrow></m:msub><m:mo>&#45;</m:mo><m:mi>&#951;</m:mi><m:mo>&#8711;</m:mo><m:mi>J</m:mi><m:mrow><m:mo>(</m:mo><m:mi>&#952;</m:mi><m:mo>)</m:mo></m:mrow></m:mrow></m:math> 

这显示了模型变量在每次训练操作中的变化方式。随着训练的继续，`∇J(θ)` 应接近零，这意味着每组新变量应近似等于前一组变量。此时，优化已完成，因为优化器已收敛到最小值。

`η` 的值由开发者确定，选择该值是一个关键决策。如果 `η` 太大，算法将快速进展，但它可能会绕过最小值而永远达不到最终值。

如果 `η` 太小，算法将更精确地移动，但需要花费大量时间。此外，优化器可能会在局部最小值处停止，而不是全局最小值。

## 创建 GradientDescentOptimizer

应用程序可以通过创建 `GradientDescentOptimizer` 使用梯度下降算法执行优化。构造函数如下所示：

`tf.train.GradientDescentOptimizer(learning_rate, use_locking=False, name='GradientDescent')`

`learning_rate` 参数设置 `η`，即学习率。以下代码创建优化器并将其学习率设置为 0.1：

```
learn_rate = 0.1
optimizer = tf.train.GradientDescentOptimizer(learn_rate)
optimizer_op = optimizer.minimize(loss)
```

