

![math](images/eq07002.png)
<m:math display="block" overflow="scroll" xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="left"><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>4</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>5</m:mn></m:mtd></m:mtr><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>2</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>4</m:mn></m:mtd></m:mtr><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>3</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>3</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="right"><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>3</m:mn></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mrow><m:mo>&#45;</m:mo><m:mn>2</m:mn></m:mrow></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced><m:mo>=</m:mo><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="right"><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>2</m:mn></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mrow><m:mo>&#45;</m:mo><m:mn>2</m:mn></m:mrow></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>3</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced></m:mrow></m:math>

![math](images/eq07003.png)
<m:math display="block" overflow="scroll" xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="left"><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>4</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>5</m:mn></m:mtd></m:mtr><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>2</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>4</m:mn></m:mtd></m:mtr><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>3</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>3</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="right"><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mrow><m:mo>&#45;</m:mo><m:mn>2</m:mn></m:mrow></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>5</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced><m:mo>=</m:mo><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="right"><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mrow><m:mn>17</m:mn></m:mrow></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mrow><m:mn>16</m:mn></m:mrow></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>9</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced></m:mrow></m:math>

现在你所要做的就是将得到的列向量取出来，使用第一个列向量作为新矩阵的第一列，以此类推，通过列向量的乘法重建输出矩阵。

![math](images/eq07004.png)
<m:math display="block" overflow="scroll" xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mtext>XB</m:mtext><m:mo>=</m:mo><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="left"><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>4</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>5</m:mn></m:mtd></m:mtr><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>2</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>4</m:mn></m:mtd></m:mtr><m:mtr columnalign="left"><m:mtd columnalign="left"><m:mn>3</m:mn></m:mtd><m:mtd columnalign="left"><m:mn>3</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="right"><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>3</m:mn></m:mtd><m:mtd columnalign="right"><m:mrow><m:mo>&#45;</m:mo><m:mn>2</m:mn></m:mrow></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mrow><m:mo>&#45;</m:mo><m:mn>2</m:mn></m:mrow></m:mtd><m:mtd columnalign="right"><m:mn>5</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced><m:mo>=</m:mo><m:mfenced open="\[" close="\]"><m:mrow><m:mrow><m:mtable columnalign="right"><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>2</m:mn></m:mtd><m:mtd columnalign="right"><m:mrow><m:mn>17</m:mn></m:mrow></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mrow><m:mo>&#45;</m:mo><m:mn>2</m:mn></m:mrow></m:mtd><m:mtd columnalign="right"><m:mrow><m:mn>16</m:mn></m:mrow></m:mtd></m:mtr><m:mtr columnalign="right"><m:mtd columnalign="right"><m:mn>3</m:mn></m:mtd><m:mtd columnalign="right"><m:mn>9</m:mn></m:mtd></m:mtr></m:mtable></m:mrow></m:mrow></m:mfenced></m:mrow></m:math>

![Remember](images/remember.png)在矩阵乘法中，由于矩阵的形状，顺序很重要。因此，你不能像标量数乘法那样颠倒项的顺序。5\*2 或 2\*5 的乘积是一样的，因为标量乘法具有交换律，但 XB 与 BX 不相同，因为有时乘法是不可能的（因为矩阵形状不兼容），或者更糟的是，它会产生不同的结果。当你有一系列矩阵乘法，例如 ABC 时，运算顺序无关紧要；无论你是先计算 AB 还是先计算 BC，结果都是一样的，因为像标量一样，矩阵乘法具有结合律。

### 浏览高级矩阵运算

你在某些算法表述中可能会遇到两个重要的矩阵运算。它们是矩阵的转置和逆。当形状为 n x m 的矩阵通过交换行和列转换为形状为 m x n 的矩阵时，就会发生*转置*。大多数测试使用上标 T 表示此运算，如 A^T。你最常看到此运算用于乘法，以便获得正确的维度。在使用 Python 时，你可以使用如下代码执行转置：

```
A = np.array([[1, 2, 3], [2, 3, 5], [7, 11, 13]]) print(A.transpose())
```

输出显示转置结果：

```
[[ 1 2 7] [ 2 3 11] [ 3 5 13]]
```

你对形状为 m x m 的矩阵应用*矩阵逆运算*，这些是行数和列数相同的方阵。此运算非常重要，因为它允许立即求解涉及矩阵乘法的方程，例如 y=bX，其中你需要发现向量 b 中的值。因为大多数标量数（零除外）都有一个乘积结果为 1 的数，其思想是找到一个矩阵逆，其乘积结果为一个称为单位矩阵的特殊矩阵，其元素为零，除了对角线元素（索引 i 等于索引 j 的位置上的元素）。求标量的逆非常简单（标量数 n 的逆为 n^(\-1)，即 1/n）。矩阵的情况则不同。矩阵逆运算涉及大量计算，因此特殊的数学函数在 Python 中执行这些计算。矩阵 A 的逆表示为 A^(\-1)。你使用以下代码对矩阵求逆：

```
print(np.linalg.inv(A))
```

输出显示逆矩阵：

```
[[-3.2 1.4 0.2] [ 1.8 -1.6 0.2] [ 0.2 0.6 -0.2]]
```

![Remember](images/remember.png)有时，求矩阵的逆是不可能的。当一个矩阵不能求逆时，它被称为*奇异矩阵*或*退化矩阵*。奇异矩阵并非常态；它们相当罕见。

### 有效使用向量化

如果执行矩阵运算（例如矩阵与向量相乘）看起来有点困难，请考虑你的计算机完成了所有艰苦的工作。你所要做的就是在理论表述中确定当你将数字放入矩阵、向量和常数时数字会发生什么，然后对它们求和、相减、相除或相乘。

