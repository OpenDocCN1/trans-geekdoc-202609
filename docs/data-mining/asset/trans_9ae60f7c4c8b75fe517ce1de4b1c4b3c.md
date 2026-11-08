
• 信息应遵循我们所说明的多阶段性质。

值得注意的是，事实证明只有一个函数满足所有这些性质，它被称为 `information value` 或 `entropy`：

`Entropy(p[1], p[2], …, p[n]) = - p[1] log p[1] - p[2] log p[2] … - p[n] log p[n]`<mml:math><mml:mi mathvariant="normal">Entropy</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:msub><mml:mrow><mml:mi>p</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>p</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:mo>&#8230;</mml:mo><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>p</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mo>&#8722;</mml:mo><mml:msub><mml:mrow><mml:mi>p</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mi>log</mml:mi><mml:msub><mml:mrow><mml:mi>p</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>&#8722;</mml:mo><mml:msub><mml:mrow><mml:mi>p</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mi>log</mml:mi><mml:msub><mml:mrow><mml:mi>p</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>&#8230;</mml:mo><mml:mo>&#8722;</mml:mo><mml:msub><mml:mrow><mml:mi>p</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub><mml:mi>log</mml:mi><mml:msub><mml:mrow><mml:mi>p</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub></mml:math>

![方程](images/F000054si45.png)

负号的原因在于分数 `p[1]`、`p[2]`、…、`p[n]`<mml:math><mml:msub><mml:mrow><mml:mi>p</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>p</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub><mml:mo>,</mml:mo><mml:mo>&#8230;</mml:mo><mml:mo>,</mml:mo><mml:msub><mml:mrow><mml:mi>p</mml:mi></mml:mrow><mml:mrow><mml:mi>n</mml:mi></mml:mrow></mml:msub></mml:math>![方程](images/F000054si46.png) 的对数是负数，因此熵实际上是正数。通常对数以 2 为底表示，此时熵的单位称为 `bits`——也就是计算机中常用的那种比特。

`entropy` 公式中的参数 `p[1]`<mml:math><mml:msub><mml:mrow><mml:mi>p</mml:mi></mml:mrow><mml:mrow><mml:mn>1</mml:mn></mml:mrow></mml:msub></mml:math>![方程](images/F000054si47.png)、 `p[2]`<mml:math><mml:msub><mml:mrow><mml:mi>p</mml:mi></mml:mrow><mml:mrow><mml:mn>2</mml:mn></mml:mrow></mml:msub></mml:math>![方程](images/F000054si48.png)、… 表示为总和为一的分数，因此，

`Info([2,3,4]) = entropy(2/9,3/9,4/9)`.<mml:math><mml:mi mathvariant="normal">Info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>\[</mml:mo><mml:mn>2,3,4</mml:mn><mml:mo>\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mi mathvariant="normal">entropy</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mn>2</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>9,3</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>9,4</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>9</mml:mn><mml:mo stretchy="false">)</mml:mo><mml:mo>.</mml:mo></mml:math>

![方程](images/F000054si49.png)

因此多阶段决策性质可以一般写成

`Entropy(p,q,r) = entropy(p,q + r) + (q + r) · entropy(q/(q + r), r/(q + r))`<mml:math><mml:mi mathvariant="normal">Entropy</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>p</mml:mi><mml:mo>,</mml:mo><mml:mi>q</mml:mi><mml:mo>,</mml:mo><mml:mi>r</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mi mathvariant="normal">entropy</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mi>p</mml:mi><mml:mo>,</mml:mo><mml:mi>q</mml:mi><mml:mo>+</mml:mo><mml:mi>r</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>+</mml:mo><mml:mo stretchy="false">(</mml:mo><mml:mi>q</mml:mi><mml:mo>+</mml:mo><mml:mi>r</mml:mi><mml:mo stretchy="false">)</mml:mo><mml:mo>&#8901;</mml:mo><mml:mi mathvariant="normal">entropy</mml:mi><mml:mo stretchy="true">(</mml:mo><mml:mfrac><mml:mrow><mml:mi>q</mml:mi></mml:mrow><mml:mrow><mml:mi>q</mml:mi><mml:mo>+</mml:mo><mml:mi>r</mml:mi></mml:mrow></mml:mfrac><mml:mo>,</mml:mo><mml:mfrac><mml:mrow><mml:mi>r</mml:mi></mml:mrow><mml:mrow><mml:mi>q</mml:mi><mml:mo>+</mml:mo><mml:mi>r</mml:mi></mml:mrow></mml:mfrac><mml:mo stretchy="true">)</mml:mo></mml:math>

![方程](images/F000054si50.png)

其中 `p + q + r = 1`

由于 `log` 函数的工作方式，你可以在不计算各个分数的情况下计算信息度量：

`Info([2,3,4]) = - 2/9 × log 2/9 - 3/9 × log 3/9 - 4/9 × log 4/9 = [ - 2 log 2 - 3 log 3 - 4 log 4 + 9 log 9 ] / 9.`<mml:math><mml:mtable width="336pt"><mml:mtr><mml:mtd><mml:mi mathvariant="normal">Info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>\[</mml:mo><mml:mn>2,3,4</mml:mn><mml:mo>\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mo>&#8722;</mml:mo><mml:mn>2</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>9</mml:mn><mml:mo>&#215;</mml:mo><mml:mi>log</mml:mi><mml:mn>2</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>9</mml:mn><mml:mo>&#8722;</mml:mo><mml:mn>3</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>9</mml:mn><mml:mo>&#215;</mml:mo><mml:mi>log</mml:mi><mml:mn>3</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>9</mml:mn><mml:mo>&#8722;</mml:mo><mml:mn>4</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>9</mml:mn><mml:mo>&#215;</mml:mo><mml:mi>log</mml:mi><mml:mn>4</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>9</mml:mn><mml:mo>=</mml:mo><mml:mo stretchy="false">\[</mml:mo><mml:mo>&#8722;</mml:mo><mml:mn>2</mml:mn><mml:mi>log</mml:mi><mml:mn>2</mml:mn><mml:mo>&#8722;</mml:mo><mml:mn>3</mml:mn><mml:mi>log</mml:mi><mml:mn>3</mml:mn><mml:mo>&#8722;</mml:mo><mml:mn>4</mml:mn><mml:mi>log</mml:mi><mml:mn>4</mml:mn><mml:mo>+</mml:mo><mml:mn>9</mml:mn><mml:mi>log</mml:mi><mml:mn>9</mml:mn><mml:mo stretchy="false">\]</mml:mo><mml:mo>&#8725;</mml:mo><mml:mn>9</mml:mn><mml:mo>.</mml:mo></mml:mtd></mml:mtr></mml:mtable></mml:math>

![方程](images/F000054si52.png)

这是在实践中通常计算信息度量的方式。因此，[图 4.2](#Ch004_91-164_B9780443158889000054.xhtml#f0015) 中第一个树的第一个节点的 信息值 为

`Info([2,3]) = -2/5 × log 2/5 -3/5 × log 3/5 = 0.971 bits`,<mml:math><mml:mi mathvariant="normal">Info</mml:mi><mml:mo stretchy="false">(</mml:mo><mml:mo>\[</mml:mo><mml:mn>2,3</mml:mn><mml:mo>\]</mml:mo><mml:mo stretchy="false">)</mml:mo><mml:mo>=</mml:mo><mml:mo>&#8722;</mml:mo><mml:mn>2</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>5</mml:mn><mml:mo>&#215;</mml:mo><mml:mi>log</mml:mi><mml:mn>2</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>5</mml:mn><mml:mo>&#8722;</mml:mo><mml:mn>3</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>5</mml:mn><mml:mo>&#215;</mml:mo><mml:mi>log</mml:mi><mml:mn>3</mml:mn><mml:mo>&#8725;</mml:mo><mml:mn>5</mml:mn><mml:mo>=</mml:mo><mml:mn>0.971</mml:mn><mml:mtext>bits</mml:mtext><mml:mo>,</mml:mo></mml:math>

![方程](images/F000054si53.png)

如前所述。

### 高分支属性

当某些属性具有大量可能取值时，会产生具有许多子节点的 多路分支，这时在 `information gain` 计算中会出现问题。该问题在极端情况下最能体现，即当某个属性在数据集中每个实例都有不同的取值时，就像标识码属性那样。
