
这段示例说明了一个相当重要的事实：矩阵乘法不具有交换性。

# Tip

如果你想要在矩阵乘法方面多练习一点，可以尝试访问 [`FreeMathHelp.com`](http://FreeMathHelp.com) 或 [`www.freemathhelp.com/matrix-multiplication.html`](http://www.freemathhelp.com/matrix-multiplication.html)。

## Matrix Transposition

矩阵 `transposition` 简单地将行和列的顺序颠倒。虽然我们主要关注 2×2 矩阵，但转置操作最容易通过一个行列数不同的矩阵来观察。请参考下面所示的矩阵。

![Images](Images/image00601.jpeg)

要对矩阵进行转置，需要将行和列交换，从而得到一个 2×3 矩阵。第一行现在变成了第一列。你可以在下面的示意图中看到这一点。

![Images](Images/image00602.jpeg)

## Submatrix

一个 `submatrix` 是任意矩阵的一部分，即在删除任意数量的行或列后保留下来的矩阵。请参考下面的矩阵：

![Images](Images/image00603.jpeg)

如果你删除第二列和第二行，

![Images](Images/image00604.jpeg)

你剩下的就是下面所示的矩阵：

![Images](Images/image00605.jpeg)

这个矩阵是原始矩阵的子矩阵。

## Identity Matrix

一个 `identity matrix` 其实非常简单。回想一下群的单位元性质。单位矩阵的作用是使得矩阵乘以它自身后保持不变。要构造一个单位矩阵，需要将主对角线上的元素全部设为 1，其余元素设为 0。请参考下面所示的矩阵（见 [Figure 5-1](#part0013.xhtml#ch05fig01)）。

![Images](Images/image00606.jpeg)

* * *

**FIGURE 5-1    A 2×2 matrix**

现在考虑单位矩阵。它必须是行列相等的矩阵，其主对角线上的元素全部为 1，其余元素全部为 0。你可以在下面看到单位矩阵（见 [Figure 5-2](#part0013.xhtml#ch05fig02)）。

![Images](Images/image00607.jpeg)

* * *

**FIGURE 5-2    The identity matrix**

如果你将原始矩阵（见 [Figure 5-3](#part0013.xhtml#ch05fig03)）与单位矩阵相乘，结果将与原始矩阵相同。这一点在下面的图中有所体现。

![Images](Images/image00608.jpeg)

* * *

**FIGURE 5-3    The product of a matrix and its identity matrix**

**Note**

在这些例子中，我不仅关注方阵、2×2 矩阵，还涉及仅包含整数的矩阵。矩阵可以包含有理数、实数，甚至函数。但由于本节旨在介绍矩阵代数的概念，我并未深入探讨这些细节。

矩阵代数的一个应用是线性变换。一个 *linear transformation*，有时也称为 *linear mapping* 或 *linear function*，是两个向量空间之间的映射，它保留了加法和标量乘法的运算。

**Note**

Wolfram MathWorld ([http://mathworld.wolfram.com/VectorSpace.html](http://mathworld.wolfram.com/VectorSpace.html)) 定义向量空间如下：“向量空间 V 是一个在有限向量加法和标量乘法下封闭的集合。”换句话说，向量空间是由我们称之为向量的对象（这里是整数）组成的集合，这些向量可以相加，也可以被（所谓的）标量（数）缩放。

考虑矩阵乘法（无论是与标量相乘还是与另一个矩阵相乘），这个过程会把第一个矩阵中的每个元素映射到第二个矩阵中的某个元素。这很好地是一个线性变换的例子。该过程在物理、工程和密码学中有许多实际应用。

**Tip**

关于矩阵代数的通用教程，网站 S.O.S. Mathematics 提供了有用的教程，网址为 [`www.sosmath.com/matrix/matrix.html`](http://www.sosmath.com/matrix/matrix.html)。

## Algorithms

从本节起，你将研究各种算法。那些已经学习过计算机科学的人很可能已经修过数据结构和算法课程。本节将介绍一些算法概念，随后在排序算法的背景下讨论一般算法分析。本节结束时，我们将研究一个非常重要的算法。

### Basic Algorithms

一个 *algorithm* 只是一种系统化解决问题的方法。如果你遵循该过程，就能得到预期的结果。算法是计算机编程的常规部分。通常，算法研究的重点是排序算法。排序列表是一个非常常见的任务，因此也是算法研究的常见主题。

同时，我们需要有一种清晰的方法来评估算法的有效性。对于任何算法，如果能够得到期望的结果，那么显然该算法是可行的。但真正的问题是，它工作得有多好？如果你对只有 10 个元素的列表进行排序，排序耗时并不特别关注。但如果列表包含 1 百万个元素，排序耗时（即你选择的算法）就至关重要。类似的问题也出现在现代加密算法的评估上。显然，它们必须工作（即是安全的），而且必须高效。例如，如果用于电子商务的加密算法效率不佳，电子商务就不会如此普及。

幸运的是，有很好的方法来分析任何算法。分析算法时，我们通常关注 *asymptotic* 上下界。渐近分析是用来衡量计算机算法性能的过程。这种性能通常以 *computational complexity*（通常指时间或所需资源（内存）的度量）来衡量。算法通常可以为时间或资源进行优化，但不能同时两者兼得。渐近上界是给定算法的最坏情况场景，而渐近下界是最佳情况。

有些分析者更倾向于使用平均情况；然而，了解最好和最差情况在某些情况下可能很有用。简单来说，渐近上界和下界必须落在你所解决的问题的参数范围内。你必须假设最坏情况会在某些情况下发生。

之所以上界和下界之间存在差异，是因为集合的初始状态。如果你将排序算法应用于信息熵最大（即最混乱）的集合，那么算法的运行时间将达到渐近上界。相反，如果集合已经非常接近有序，则算法可能接近或达到渐近下界。

评估算法有效性的最常用方法是 *Big O notation*。该方法衡量算法的执行情况，通常是根据问题规模 n（在排序算法中，n 为待排序的元素数量）所需的迭代次数。表示 f(n) = O(g(n)) 意味着它小于某个常数倍的 g(n)。换句话说，“f of n 是 Big O of g of n”。如果一个算法是 2n，意味着它需要执行列表中两倍的元素数量。Big O 记号本质上测量函数的渐近上界，并且是最常用的分析方法。

Big O 记号最早由德国数学家 Paul Bachmann 在 1894 年的著作 *Analytische Zahlentheorie*（分析数论）中引入，该书是关于解析数论的工作。随后，德国数学家 Edmund Landau 将其推广，该记号有时被称为“Landau 符号”。

