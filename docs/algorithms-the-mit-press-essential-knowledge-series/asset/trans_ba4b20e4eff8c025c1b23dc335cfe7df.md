
为了更简洁地表达，我们将贝果包和牛角包的价格写成一个向量：

[2.00 1.50]

我们将每日销售额写在一个矩阵中。该矩阵有两列（每列代表一家商店）两行（分别代表贝果包和牛角包）：

```
\begin{bmatrix} 10 & 15 \\ 20 & 10 \end{bmatrix}
```

然后为了找到每家商店的总销售额，我们将向量的元素与销售矩阵的每一列相乘并相加。这定义了向量与矩阵的乘积：

```
[2.00 1.50] \times \begin{bmatrix} 10 & 15 \\ 20 & 10 \end{bmatrix} = [2.00 \times 10 + 1.50 \times 20 \quad 2.00 \times 15 + 1.50 \times 10] = [50 45]
```

向量与矩阵的乘积是两个矩阵乘积的一种特例。让我们扩展这个例子，不再使用包含贝果包和牛角包价格的向量，而是使用包含每笔销售价格和利润的矩阵：

```
$\begin{bmatrix} 2.00 & 1.50 \\ 0.20 & 0.10 \end{bmatrix}
```

为了找到每家商店的总销售额和总利润，我们将创建一个矩阵，其中第 $i$ 行第 $j$ 列的元素将是价格利润矩阵第 $i$ 行与销售矩阵第 $j$ 行乘积之和。这就是两个矩阵乘积的定义：

```
$\begin{bmatrix} 2.00 & 1.50 \\ 0.10 & 0.20 \end{bmatrix} \times \begin{bmatrix} 10 & 15 \\ 20 & 15 \end{bmatrix} = \begin{bmatrix} 2.00 \times 10 + 1.50 \times 20 & 2.00 \times 15 + 1.50 \times 10 \\ 0.10 \times 10 + 0.20 \times 20 & 0.10 \times 15 + 0.20 \times 15 \end{bmatrix} = \begin{bmatrix} 50 & 45 \\ 5 & 3.5 \end{bmatrix}
```

回到 pagerank，在每一轮中，pagerank 向量的计算实际上是上一轮 pagerank 向量的值与超链接矩阵的积。随着我们进行，我们得到了 pagerank 的连续估计——即由它们组成的 pagerank 向量的连续估计。

为了获得这些 pagerank 向量的连续估计，我们只需要在每一轮将向量与超链接矩阵相乘，从而得到下一轮的向量。

在第一轮，我们从一个内容全部等于 $1 / n$ 的 pagerank 向量开始，其中 $n$ 是页面数量。如果我们将第一个 pagerank 向量标记为 $\pi_1$，第一轮结束时的 pagerank 向量标记为 $\pi_2$，超链接矩阵标记为 $H$，则有：

$\pi_2 = \pi_1 \times H$

在每一轮中，我们都使用该轮的 pagerank 向量来计算下一轮的 pagerank 向量。在第二轮投票中，我们得到了第三个页面排名估计值——即我们的第三个 pagerank 向量——我们执行了计算：

$\pi_3 = \pi_2 \times H = (\pi_1 \times H) \times H = \pi_1 \times (H \times H) = \pi_1 \times H^2$

在第三轮投票中，我们得到了第四个 pagerank 向量：

$\pi_4 = \pi_3 \times H = (\pi_1 \times H^2) \times H = \pi_1 \times (H^2 \times H) = \pi_1 \times H^3$

正如每次迭代一样，我们将上一次迭代的结果乘以超链接矩阵，最后，这是一系列 pagerank 向量连续估计与超链接矩阵的乘积。正如我们所看到的，这等于将初始 pagerank 向量乘以超链接矩阵的递次幂。这种计算连续近似的方法被称为幂法（power method）。因此我们看到，计算一组网页的 pagerank 是幂方法在 pagerank 向量和超链接矩阵的应用，直到生成的 pagerank 向量不再变化，或者正如我们所说的，直到收敛到一个稳定值——我们的最终 pagerank 指标。

我们刚刚得到了关于如何计算网页图 pagerank 的更精确的描述：

- 1. 构建图的超链接矩阵。
- 2. 从初始 pagerank 估计开始，给每个页面一个 $1 / n$ 的 pagerank，其中 $n$ 是页面总数。
- 3. 应用幂法，将 pagerank 向量乘以超链接矩阵，直到 pagerank 向量的值收敛。

除了简洁之外，这种公式允许我们将问题转移到线性代数领域……（此处由于原文存在大量重复内容，已按要求处理重复部分）
