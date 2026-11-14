

- 所有代码示例均可在 github.com/sapphire008/vectorization-book-supplement 获取。请注意，某些代码示例使用随机输入进行模拟，因此重新运行笔记本未必能得到书中提供的相同结果。

- 为了进一步澄清许多向量化操作，已融入说明性图表以直观展示其背后的逻辑，这些图表通常附有详细说明，无论是放在正文中还是在图注中。

- 本书讨论的原则应与 Python、NumPy、TensorFlow 或 PyTorch 的特定版本无关。默认情况下，我的代码示例使用 python==3.10.6、numpy==1.23.4、pandas==2.1.1、scikit-learn==1.3.0、scipy==1.11.1、tensorflow==2.13.0、keras==2.13.1 和 torch==2.1.0 进行了测试。不过，当所使用的版本不是默认版本，或者在相关或需要强调版本时，我会在代码示例旁注明库版本。

## 局限性：

- 请注意，代码块（带阴影背景）内的回车符号“↲”用于指示换行，以适应长行的格式。

- 为解决某些问题而实现的代码示例和案例研究不一定总是最优解，尽管在撰写本书时，我诚实地尽了最大努力提出这些解决方案。有时，我也特意决定以非最高效的方式实现某些内容，以说明章节中介绍的概念的实际应用。由于本书每章内容相互衔接，我明确选择不使用后续章节才会介绍的功能。尽管如此，这展示了向量化和一般编程的魅力：在实践中，解决特定问题并非只有一种方案。尽管如此，我鼓励读者寻找更高效的方法来解决案例研究问题。另一方面，如果读者在某个实现中发现了错误，欢迎随时在 github.com/sapphire008/vectorization-book-supplement 提交 issue。

- 在比较向量化库时，尽管本书包含的信息是我目前所知的最准确情况，但我可能对某些库特有的功能一无所知。我有时会声称某个库未实现另一个库在撰写时已实现的功能，但如果读者发现另一个库确实实现了该功能，我愿意接受纠正，并将尽最大努力在未来版本的书中更新这些信息。

我希望在读完本书后，读者能够精通实现可扩展机器学习算法的基础和高级向量化技术，并准备好迎接现实世界的挑战。

2023 年 11 月 29 日
纽约

Edward DongBo Cui（崔东博）
数据科学总监
DotDash Meredith，纽约

## 致谢

我向 Ryan Beauchemin 和 Kendall Meyer 表达我最深切的感谢，感谢他们宝贵的审阅和贡献，这些贡献大大提升了本书的质量。我也感谢 Ilmir Moussikaev 对我潜力的信任，并为我提供在 Peacock 流媒体平台创造非凡作品的机会。这段特定经历是我职业生涯的基石，引领我获得撰写本书所需的知识。我也要向我的学生们表达衷心的感谢。教导和指导他们掌握机器学习与数据科学的各种技术，为我撰写本书提供了所需的见解和素材。特别感谢 Chris Haroun，他的灵感与指导激励我踏上这段写作之旅。最后，我要感谢我的妻子，感谢她在整个过程中始终如一的支持。

## 1 向量化简介

### 1.1 什么是向量化

**向量化**是一种并行计算范式，在单个数据处理单元（CPU 或 GPU）上对一组数字执行算术运算 [Intel, 2022]。现代 CPU 根据指令类型，可以执行 4 到 16 次单精度（float32）并行计算 [Intel, 2022]（参见图 1.1）。

这里，SSE（流式 SIMD（单指令多数据）扩展）拥有 128 位寄存器；每个寄存器用于存储 32 位数据以进行计算。这相当于执行四次单精度（float32）运算或两次双精度（float64）运算。另一方面，Intel 的 AVX512（高级矢量扩展 512）拥有 512 位寄存器，因此可以同时处理 512 位数据。这相当于执行 16 次单精度运算或 8 次双精度运算。

“向量化”一词还指将一次只能处理一个数据点的算法转换为同时计算一组数据的操作 [Kharchenko, 2018]。一个经典示例是点积运算，

\(\sum_{i}^{n} a_i b_i = \mathbf{a} \cdot \mathbf{b}\)

其中 \(\mathbf{a} := [a_1, a_2, a_3, \dots, a_n]\)，且 \(\mathbf{b} := [b_1, b_2, b_3, \dots, b_n]\)。

方程右侧的点积运算是左侧求和过程的向量化形式。它不是一次对数组的一个元素进行操作，而是对集合或数组 \(\mathbf{a}\) 和 \(\mathbf{b}\) 进行操作。

![](img/e891acaacd4fb5b80dab2ed824618203_23_0.png)

图 1.1 CPU 向量计算。

> **注**
> 
> “向量化”这一术语的另一个定义与大型语言模型的最近进展有关：使用向量或一组值来表示一个词。在文献中，这通常被称为 **嵌入式**，起源于自然语言处理中的 word2vec 模型。在第 6 章和第 7 章中，我们将介绍将字符串或分类特征表示为数值的想法，即整数索引、稀疏 one-hot 编码向量和稠密嵌入向量。

### 1.1.1 向量化运作的简单示例

假设我们要对从均匀分布中抽取的 100 万个随机数求点积。使用 Python 的 `for` 循环，我们通常会按以下方式实现此算法：

```
import random
def sqrt_of_n_random_numbers(n=1_000_000) :
    result = 0
    for _ in range(n) :
        a = random.uniform(0, 1)
        b = random.uniform(0, 1)
        result += a * b
    return result
```

在我的 M1 MacBook Pro 上运行 Python 3.11.4，上述函数的运行时间如下：

```
294 ms ± 1.39 ms per loop (mean ± std. dev. of 7 runs, 1 loop each)
```

如果使用 numpy 实现该算法并进行向量化

```
import numpy as np

def sqrt_of_n_random_numbers_np(n=1_000_000) :
    a = np.random.rand(n)
    b = np.random.rand(n)
    result = np.dot(a, b)
    return result
```

在相同设置下，向量化实现的运行时间如下。

```
7.9 ms ± 119 μs per loop (mean ± std. dev. of 7 runs, 100 loops each)
```

向量化带来了约 37 倍的加速！

### 1.1.2 Python 依然可能更快！

然而，上述示例并非旨在否定某些原生 Python 操作仍然比 NumPy 的实现更快这一事实，尽管 NumPy 经常用于向量化操作以简化 Python 中的 for 循环。

例如，我们希望按句号“.”分隔一组字符串列表。

```
X = ["foo.bar", "bar.foo", "x.y", "z.k"] * 1000
[x.split(".") for x in X]
```

第 2 行的运行时间为

```
299 μs ± 5.98 μs per loop (mean ± std. dev. of 7 runs, 1,000 loops each)
```

然而，相比之下，如果我们使用 NumPy 的“向量化”分割操作

```
Y = ["foo.bar", "bar.foo", "x.y", "z.k"] * 1000
Y = np.array(Y)
np.core.defchararray.split(Y, ".")
```

第 3 行的运行时间为

```
1.18 ms ± 4.37 µs per loop (mean ± std. dev. of 7 runs, 1,000
loops each)
```

这比原生 Python 慢约 4.0 倍。

### 1.1.3 向量化操作的内存分配

使用向量化操作时，我们需要考虑内存与速度之间的权衡。有时，向量化操作需要为中间步骤的结果分配更多内存。因此，这会影响程序的整体性能，即空间与时间复杂度的权衡。假设我们想要计算数组中元素平方和的函数。这可以作为 for 循环实现，遍历每个元素，求其平方，并累加平方值作为总和。或者，该函数也可以作为向量化操作实现：先对每个元素求平方，将结果存储在数组中，然后对平方向量求和。

```
import numpy as np

def sum_of_square_vectorized(X):
    x = np.asarray(X)
    x_sq = np.square(x) # x ** 2
    res = x_sq.sum()
    return res

def sum_of_square_for_loop(X):
    res = 0
    for x in X:
        res += x * x
    return res
```

让我们使用 memory_profiler 包来检查两个函数中每一行的内存使用情况。我们可以先通过 pip 安装该包：

