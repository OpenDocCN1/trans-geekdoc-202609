

[图 A.1](#a02.xhtml#c0-fig-1) 展示了一个线性方程的示例。

![图 A.1 线性方程的可视化（粗体斜体 y 等于 2 粗体斜体 x 加 3）。](images/cappf001.png)

[图 A.1](#a02.xhtml#rc0-fig-1) 线性方程的可视化 (<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll" display="inline"><mstyle mathvariant="bold"><mi mathvariant="bold-italic">y</mi><mo>=</mo><mrow><mn>2</mn></mrow><mi mathvariant="bold-italic">x</mi><mo>+</mo><mrow><mn>3</mn></mrow></mstyle></math>![粗体斜体 y 等于 2 粗体斜体 x 加 3](images/a02_dequ4.png))。

### 标量

*标量* 是一个单独的数字，通常表示只有大小没有方向的量。例如，它可以表示温度或质量：

<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll" display="block"><mi>s</mi><mspace width="0.2em"/><mo>=</mo><mspace width="0.2em"/><mn>5</mn></math>![s 等于 5](images/a02_dequ5.png)

### 向量

*向量* 是一组数字，同时表示大小和方向。它通常被可视化为空间中的一个箭头：

<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll" display="block"><mover accent="true"><mi>v</mi><mo>&#8594;</mo></mover><mo>=</mo><mfenced close="\]" open="\["><mtable columnalign="center"><mtr><mtd><mn>1</mn></mtd></mtr><mtr><mtd><mn>2</mn></mtd></mtr><mtr><mtd><mn>3</mn></mtd></mtr></mtable></mfenced></math>![顶部带箭头的向量 v 等于左括号，3 行 1 列矩阵，1，2，3，右括号。](images/a02_dequ6.png)

向量 <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mover accent="true"><mi>v</mi><mo>&#8594;</mo></mover></math>![向量 v](images/a02_dequ7.png) 所包含的单个数字用索引表示，索引用于标识它们的位置。例如，以下公式

<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll" display="block"><msub><mi>v</mi><mn>1</mn></msub><mo>=</mo><mn>1</mn></math>![v 下标 1 等于 1](images/a02_dequ8.png)

表示向量 <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mover accent="true"><mi>v</mi><mo>&#8594;</mo></mover></math>![向量 v](images/a02_dequ9.png) 的第一个元素的值为 1。

### 矩阵

*矩阵* 是一个二维 (2D) 数字数组，可用于表示线性变换或方程组：

<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll" display="block"><mi>M</mi><mo>=</mo><mfenced close="\]" open="\["><mtable columnalign="center"><mtr><mtd><mn>1</mn></mtd><mtd><mn>2</mn></mtd><mtd><mn>3</mn></mtd></mtr><mtr><mtd><mn>4</mn></mtd><mtd><mn>5</mn></mtd><mtd><mn>6</mn></mtd></mtr><mtr><mtd><mn>7</mn></mtd><mtd><mn mathvariant="bold">8</mn></mtd><mtd><mn>9</mn></mtd></mtr></mtable></mfenced></math>![M 等于 3×3 矩阵。第 1 行：1，2，3。第 2 行：4，5，6。第 3 行：7，粗体 8，9。](images/a02_dequ11.png)

因为矩阵是一个二维数组，所以矩阵中的某个数字用两个索引表示：第一个索引选择该数字所在的行，第二个索引选择该数字所在的列。例如矩阵 <math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>M</mi></math>![M](images/a02_dequ13.png) 中的数字 8 位于第三行第二列。因此，

<math xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll" display="block"><msub><mi>m</mi><mn>32</mn></msub><mo>=</mo><mn>8</mn></math>![下标 m 32 等于 8](images/a02_dequ14.png)

### 张量

*张量* 是标量、向量和矩阵向高维的推广。张量可以表示更复杂的数据结构，例如机器学习或物理学中的多维数据集。

以下张量 <math class="a" xmlns="http://www.w3.org/1998/Math/MathML" overflow="scroll"><mi>T</mi></math>![T](images/MathcabEQ_0001.png) 是一个四维 (4D) 数组，选择每个元素需要四个索引。

请注意张量中的行和列可以是向量或矩阵，而不仅仅是标量（单个数字）：

