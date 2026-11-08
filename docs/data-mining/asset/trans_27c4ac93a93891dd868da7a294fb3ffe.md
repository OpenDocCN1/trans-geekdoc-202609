

## 感知机学习规则

[图 4.11A](#Ch004_91-164_B9780443158889000054_a.xhtml#f0060) 给出用于寻找分离超平面的感知机学习规则。算法迭代直到找到完美解，但它只有在存在分离超平面时才能正常工作；也就是说，数据是线性可分的。每次迭代遍历所有训练实例。如果遇到被误分类的实例，则改变超平面的参数，使该误分类实例更接近超平面，甚至可能跨过超平面到达正确的一侧。如果实例属于第一类，则通过将其属性值加到权重向量中来实现；否则，从中减去。

![图 4.11 感知机。(A) 学习规则。(B) 作为神经网络的表示。](images/F000054f04-11-9780443158889.jpg)

图 4.11 感知机。(A) 学习规则。(B) 作为神经网络的表示。

要了解其工作原理，请考虑在将属于第一类的实例 `a` 添加之后的情况：

(`w[0]+a[0]`)`a[0]` + (`w[1]+a[1]`)`a[1]` + (`w[2]+a[2]`)`a[2]` + ⋯ + (`w[k]+a[k]`)`a[k]`.<mml:math><mml:mo>(</mml:mo><mml:msub><mml:mrow><mml:mi>w</mml:mi></mml:mrow><mml:mrow><mml:mn>0</mml:mn></mml:mrow></mml:msub><mml:mo>+</mml:mo><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mn>0</mml:mn></mml:mrow></mml:msub><mml:mo>)</mml:mo><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mn>0</mml:mn></mml:mrow></mml:msub><mml:mo>+</mml:mo><mml:mo>(</mml:mo><mml:msub><mml:mrow><mml:mi>w</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>+</mml:mo><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>)</mml:mo><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>+</mml:mo><mml:mo>(</mml:mo><mml:msub><mml:mrow><mml:mi>w</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>+</mml:mo><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>)</mml:mo><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>+</mml:mo><mml:mo>&#8943;</mml:mo><mml:mo>+</mml:mo><mml:mo>(</mml:mo><mml:msub><mml:mrow><mml:mi>w</mml:mi></mml:mrow><mml:mrow><mml:mi>k</mml:mi></mml:mrow></mml:msub><mml:mo>+</mml:mo><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mi>k</mml:mi></mml:mrow></mml:msub><mml:mo>)</mml:mo><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mi>k</mml:mi></mml:mrow></mml:msub><mml:mo>.</mml:mo></mml:math>

![方程](images/F000054si80.png)

这意味着 `a` 的输出增加了

`a[0]` × `a[0]` + `a[1]` × `a[1]` + `a[2]` × `a[2]` + ⋯ + `a[k]` × `a[k]`.<mml:math><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mn>0</mml:mn></mml:mrow></mml:msub><mml:mo>&#215;</mml:mo><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mn>0</mml:mn></mml:mrow></mml:msub><mml:mo>+</mml:mo><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>&#215;</mml:mo><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>+</mml:mo><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>&#215;</mml:mo><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>+</mml:mo><mml:mo>&#8943;</mml:mo><mml:mo>+</mml:mo><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mi>k</mml:mi></mml:mrow></mml:msub><mml:mo>&#215;</mml:mo><mml:msub><mml:mrow><mml:mi>a</mml:mi></mml:mrow><mml:mrow><mml:mi>k</mml:mi></mml:mrow></mml:msub><mml:mo>.</mml:mo></mml:math>

![方程](images/F000054si81.png)

该数值始终为正。因此超平面已朝正确方向移动，以便将实例 `a` 分类为正例。相反，如果属于第二类的实例被误分类，则修改后该实例的输出会减小，再次使超平面朝正确方向移动。

这些修正是增量的，可能干扰之前的更新。然而，可以证明如果数据是线性可分的，算法将在有限次迭代内收敛。当然，如果数据不是线性可分的，算法将不会终止，因此在实际应用该方法时需要对迭代次数施加上限。

结果得到的超平面称为 `perceptron`，它是神经网络的鼻祖（我们将在 [第 9.2 节](#Ch010_347-389_B9780443158889000108.xhtml#s0050)、[第 10 章](#Ch011_391-432_B978044315888900011X.xhtml#Ch011_391-432_B978044315888900011X)、“深度学习：基础”和 [第 11 章](#Ch012_433-471_B9780443158889000121.xhtml#Ch012_433-471_B9780443158889000121)、“高级深度学习方法”中再次讨论神经网络）。[图 4.11B](#Ch004_91-164_B9780443158889000054_a.xhtml#f0060) 将感知机表示为具有节点和加权边的图，形象地称为“神经元”的“网络”。有两层节点：输入层和输出层。输入层对每个属性都有一个节点，外加一个始终设为一的额外节点。输出层仅由一个节点组成。输入层中的每个节点都连接到输出层。连接是加权的，而权重就是感知机学习规则找到的那些数值。

当实例被呈现给感知机时，其属性值用于“激活”输入层。它们与权重相乘并在输出节点求和。如果加权和大于 0，则输出信号为 1，表示第一类；否则为 −1，表示第二类。

### 使用 Winnow 进行线性分类

感知机算法并不是唯一保证能为线性可分问题找到分离超平面的方法。对于具有二进制属性的数据集，有一种称为 `Winnow` 的替代方法，显示在 [图 4.12A](#Ch004_91-164_B9780443158889000054_a.xhtml#f0065) 中。这两种算法的结构非常相似。与感知机一样，Winnow 仅在遇到被误分类的实例时才更新权重向量——它是基于错误的驱动。

![图 4.12 Winnow 算法。(A) 非平衡版本。(B) 平衡版本。](images/F000054f04-12-9780443158889.jpg)

图 4.12 Winnow 算法。(A) 非平衡版本。(B) 平衡版本。

这两种方法在权重更新方式上有所不同。感知机规则采用加法机制，通过添加（或减去）实例的属性向量来改变权重向量。Winnow 采用乘法更新，并通过将权重乘以用户指定的参数 `α`（或其倒数）来单独改变权重。属性值 `a[i]` 要么是 0 要么是 1，因为我们处理的是二进制数据。如果属性值为 0，则权重保持不变，因为此时它们不参与决策。否则，如果该属性有助于做出正确决策，则乘数为 `α`；如果没有，则为 1/`α`。

另一个区别是线性函数中的阈值也是用户指定的参数。我们称此阈值为 `θ`，并且仅当

