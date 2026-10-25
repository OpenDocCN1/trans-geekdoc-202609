

# 第五部分

# 因式分解

# 第 14 章

## 矩阵分解

许多复杂的矩阵操作无法使用计算机的有限精度高效或稳定地求解。矩阵分解是将矩阵减少为组成部分的方法，从而使计算更复杂的矩阵操作变得更容易。矩阵分解方法，也称为矩阵因式分解方法，是计算机中线性代数的基础，即使是求解线性方程组、计算逆矩阵和计算矩阵行列式等基本操作也是如此。在本教程中，你将了解矩阵分解以及如何在 Python 中计算它们。完成本教程后，你将知道：

- 什么是矩阵分解以及为什么这类操作很重要。
- 如何在 Python 中计算 LU 和 QR 矩阵分解。
- 如何在 Python 中计算 Cholesky 矩阵分解。

让我们开始吧。

## 14.1 教程概览

本教程分为 3 部分，分别是：

- 什么是矩阵分解
- LU 分解
- QR 分解
- Cholesky 分解

## 14.2 什么是矩阵分解

矩阵分解是将矩阵减少为其组成部分的方法。这是一种方法，可以简化在分解后的矩阵上而不是在原始矩阵本身上执行的更复杂的矩阵操作。矩阵分解的常见类比是数的因式分解，例如将 10 分解为 2 × 5。出于这个原因，矩阵分解也称为矩阵因式分解。像因式分解实数值一样，有

## 13.4.4 张量除法

一个张量与另一个具有相同维度的张量的逐元素除法会产生一个具有相同维度的新张量，其中每个标量值是父张量中标量的逐元素除法。

\( A = \begin{pmatrix} a_{1,1,1} & a_{1,2,1} & a_{1,3,1} \\ a_{2,1,1} & a_{2,2,1} & a_{2,3,1} \end{pmatrix}, \begin{pmatrix} a_{1,1,2} & a_{1,2,2} & a_{1,3,2} \\ a_{2,1,2} & a_{2,2,2} & a_{2,3,2} \end{pmatrix} \) (13.14)

\( B = \begin{pmatrix} b_{1,1,1} & b_{1,2,1} & b_{1,3,1} \\ b_{2,1,1} & b_{2,2,1} & b_{2,3,1} \end{pmatrix}, \begin{pmatrix} b_{1,1,2} & b_{1,2,2} & b_{1,3,2} \\ b_{2,1,2} & b_{2,2,2} & b_{2,3,2} \end{pmatrix} \) (13.15)

\( C = \frac{A}{B} \) (13.16)

\( C = \begin{pmatrix} \frac{a_{1,1,1}}{b_{1,1,1}} & \frac{a_{1,2,1}}{b_{1,2,1}} & \frac{a_{1,3,1}}{b_{1,3,1}} \\ \frac{a_{2,1,1}}{b_{2,1,1}} & \frac{a_{2,2,1}}{b_{2,2,1}} & \frac{a_{2,3,1}}{b_{2,3,1}} \end{pmatrix}, \begin{pmatrix} \frac{a_{1,1,2}}{b_{1,1,2}} & \frac{a_{1,2,2}}{b_{1,2,2}} & \frac{a_{1,3,2}}{b_{1,3,2}} \\ \frac{a_{2,1,2}}{b_{2,1,2}} & \frac{a_{2,2,2}}{b_{2,2,2}} & \frac{a_{2,3,2}}{b_{2,3,2}} \end{pmatrix} \) (13.17)

在 NumPy 中，我们可以通过除数组来直接除张量。

```
# tensor division
from numpy import array
# define first tensor
A = array([
    [[1,2,3], [4,5,6], [7,8,9]],
    [[11,12,13], [14,15,16], [17,18,19]],
    [[21,22,23], [24,25,26], [27,28,29]]])
# define second tensor
B = array([
    [[1,2,3], [4,5,6], [7,8,9]],
    [[11,12,13], [14,15,16], [17,18,19]],
    [[21,22,23], [24,25,26], [27,28,29]]])
# divide tensors
C = A / B
print(C)
```

### 清单 13.7：张量 Hadamard 积示例。

运行示例打印乘以张量的结果。

```
[[[ 1  4  9]
  [ 16 25 36]
  [ 49 64 81]]]

[[121 144 169]
 [196 225 256]
 [289 324 361]]]

[[441 484 529]
 [576 625 676]
 [729 784 841]]]
```

### 清单 13.8：张量 Hadamard 积的示例输出。

### 清单 13.9：除张量示例。

运行示例打印除以张量的结果。

```
[[[ 1.  1.  1.]
  [ 1.  1.  1.]
  [ 1.  1.  1.]]]

[[ 1.  1.  1.]
 [ 1.  1.  1.]
 [ 1.  1.  1.]]

[[ 1.  1.  1.]
 [ 1.  1.  1.]
 [ 1.  1.  1.]]]
```

### 清单 13.10：除张量的示例输出。

## 13.5 张量积

张量积算子通常表示为中间带有小 x 的圆圈。我们在此将其表示为 \(\otimes\)。给定具有 \(q\) 个维度的张量 \(A\) 和具有 \(r\) 个维度的张量 \(B\)，这些张量的乘积将是一个新张量，其阶数为 \(q + r\)，或者说具有 \(q + r\) 个维度。张量积不仅限于张量，也可以在矩阵和向量上执行，这可以作为练习的好地方，以便为更高维度建立直觉。让我们来看看向量的张量积。

\(a = \begin{pmatrix} a_1 \\ a_2 \end{pmatrix}\) (13.18)

\(b = \begin{pmatrix} b_1 \\ b_2 \end{pmatrix}\) (13.19)

\(C = a \otimes b\) (13.20)

\(C = \begin{pmatrix} a_1 \times \begin{pmatrix} b_1 \\ b_2 \end{pmatrix} \\ a_2 \times \begin{pmatrix} b_1 \\ b_2 \end{pmatrix} \end{pmatrix}\) (13.21)

或者，展开为：

\(C = \begin{pmatrix} a_1 \times b_1 & a_1 \times b_2 \\ a_2 \times b_1 & a_2 \times b_2 \end{pmatrix}\) (13.22)

让我们来看看矩阵的张量积。

\(A = \begin{pmatrix} a_{1,1} & a_{1,2} \\ a_{2,1} & a_{2,2} \end{pmatrix}\) (13.23)

$$B = \begin{pmatrix} b_{1,1} & b_{1,2} \\ b_{2,1} & b_{2,2} \end{pmatrix}$$ (13.24)

$$C = A \otimes B$$ (13.25)

$$C = \begin{pmatrix} a_{1,1} \times \begin{pmatrix} b_{1,1} & b_{1,2} \\ b_{2,1} & b_{2,2} \end{pmatrix} & a_{1,2} \times \begin{pmatrix} b_{1,1} & b_{1,2} \\ b_{2,1} & b_{2,2} \end{pmatrix} \\ a_{2,1} \times \begin{pmatrix} b_{1,1} & b_{1,2} \\ b_{2,1} & b_{2,2} \end{pmatrix} & a_{2,2} \times \begin{pmatrix} b_{1,1} & b_{1,2} \\ b_{2,1} & b_{2,2} \end{pmatrix} \end{pmatrix}$$ (13.26)

或者，展开为：

$$C = \begin{pmatrix} a_{1,1} \times b_{1,1} & a_{1,1} \times b_{1,2} & a_{1,2} \times b_{1,1} & a_{1,2} \times b_{1,2} \\ a_{1,1} \times b_{2,1} & a_{1,1} \times b_{2,2} & a_{1,2} \times b_{2,1} & a_{1,2} \times b_{2,2} \\ a_{2,1} \times b_{1,1} & a_{2,1} \times b_{1,2} & a_{2,2} \times b_{1,1} & a_{2,2} \times b_{1,2} \\ a_{2,1} \times b_{2,1} & a_{2,1} \times b_{2,2} & a_{2,2} \times b_{2,1} & a_{2,2} \times b_{2,2} \end{pmatrix}$$ (13.27)

张量积可以使用 NumPy 中的 `tensordot()` 函数实现。该函数将要相乘的两个张量以及对乘积求和的轴作为参数，称为归约求和。要计算张量积（在 NumPy 中也称为张量点积），轴必须设置为 0。在下面的示例中，我们定义两个一阶张量（向量）并计算张量积。

```
# tensor product
from numpy import array
from numpy import tensordot
# define first vector
A = array([1,2])
# define second vector
B = array([3,4])
# calculate tensor product
C = tensordot(A, B, axes=0)
print(C)
```

### 清单 13.11：张量积示例。

运行示例打印张量积的结果。结果是一个二阶张量（矩阵），长度为 2 × 2。

```
[[3 4]
 [6 8]]
```

### 清单 13.12：张量积的示例输出。

张量积是你可能遇到的最常见的张量乘法形式，但存在许多其他类型的张量乘法，例如张量点积和张量缩并。

## 13.6 扩展

本节列出了一些你可能希望探索的扩展教程的想法。

- 使用你自己编造的小张量数组数据更新每个示例。
- 使用小向量或矩阵数据实现本教程未涵盖的三种其他类型的张量乘法。
- 编写自己的函数来实现每种张量算术运算。

如果你探索其中任何扩展，我很乐意了解。

## 13.7 进一步阅读

如果你希望深入了解，本节提供了更多关于该主题的资源。

### 13.7.1 书籍

- _《向量与张量学生指南》, 2011. http://amzn.to/2kmUvvF
- 第 12 章，特殊主题，_《矩阵计算》, 2012. http://amzn.to/2B9xnLD
- _《工程师张量代数与张量分析》, 2015. http://amzn.to/2C6gzCu

### 13.7.2 API

- N 维数组。https://docs.scipy.org/doc/numpy-1.13.0/reference/arrays.ndarray.html
- numpy.tensordot() API。https://docs.scipy.org/doc/numpy-1.13.0/reference/generated/numpy.tensordot.html

### 13.7.3 文章

- 维基百科上的张量代数。https://en.wikipedia.org/wiki/Tensor_algebra
- 维基百科上的张量。https://en.wikipedia.org/wiki/Tensor
- 维基百科上的张量积。https://en.wikipedia.org/wiki/Tensor_product
- 维基百科上的外积。https://en.wikipedia.org/wiki/Outer_product

## 13.8 总结

在本教程中，你了解了什么是张量以及如何在 Python 中使用 NumPy 操作它们。具体来说，你学习了：

- 张量是矩阵的推广，并使用 n 维数组表示。
- 如何使用张量实现逐元素操作。
- 如何执行张量积。

### 13.8.1 下一步

这是关于矩阵部分的结束，下一部分是关于矩阵因式分解，从矩阵分解方法的温和介绍开始。

