

# 组合网络与深度网络

## 图 4.1 组合两个各含三个隐藏单元的单层网络

a) 第一个网络的输出 `y` 构成了第二个网络的输入。  
b) 第一个网络使用一个由三个线性区域组成的函数，将输入 `x ∈ [−1, 1]` 映射到输出 `y ∈ [−1, 1]`，这三个区域的选择使得它们的斜率符号交替。多个输入 `x`（灰色圆圈）现在映射到同一个输出 `y`（青色圆圈）。  
c) 第二个网络定义了一个包含三个线性区域的函数，它接收 `y` 并返回 `y′`（即青色圆圈被映射为棕色圆圈）。  
d) 当这两个函数组合时，其综合效果是：(i) 三个不同的输入 `x` 通过第一个网络映射到任意给定的 `y` 值，并且 (ii) 以相同的方式被第二个网络处理；结果是面板 (c) 中第二个网络定义的函数被复制了三次，根据面板 (b) 中各区域的斜率，分别进行翻转和缩放。

![c4-fig-5002.jpg](images/c4-fig-5002.jpg)  
(4.2)

第二个网络以 `y` 为输入并返回 `y′`，其定义为：

![c4-fig-5003.jpg](images/c4-fig-5003.jpg)  
(4.3)

以及

![c4-fig-5004.jpg](images/c4-fig-5004.jpg)  
(4.4)

使用 ReLU 激活函数时，该模型同样描述了一族分段线性函数。然而，线性区域的数量可能大于具有六个隐藏单元的浅层网络。为了理解这一点，考虑选择第一个网络以产生三个正负斜率交替的区域（[图 4.1b](#c004.xhtml#c4-fig-0001)）。这意味着三个不同的 `x` 范围被映射到相同的输出范围 `y ∈ [−1, 1]`，随后从该 `y` 范围到 `y′` 的映射被应用了三次。总体效果是第二个网络定义的函数被复制三次，从而创建出九个线性区域。同一原理也适用于高维空间（[图 4.2](#c004.xhtml#c4-fig-0002)）。

---

**问题 4.1**

---

**笔记本 4.1**  
组合网络

---

## 图 4.2 组合具有二维输入的神经网络

a) 第一个网络（来自图 3.8）有三个隐藏单元，接收两个输入 `x[1]` 和 `x[2]` 并返回一个标量输出 `y`。这被传递给一个具有两个隐藏单元的第二个网络以产生 `y′`。  
b) 第一个网络产生一个由七个线性区域组成的函数，其中一个区域是平坦的。  
c) 第二个网络定义了一个在 `y ∈ [−1, 1]` 中包含两个线性区域的函数。  
d) 当这些网络组合时，第一个网络的六个非平坦区域中的每一个都被第二个网络分成两个新区域，从而创建总共 13 个线性区域。

![Figure 4.2 Composing neural networks with a 2D input. a) The first network (from figure 3.8) has three hidden units and takes two inputs x1 and x2 and returns a scalar output y. This is passed into a second network with two hidden units to produce y′. b) The first network produces a function consisting of seven linear regions, one of which is flat. c) The second network defines a function comprising two linear regions in y ∈ [−1, 1]. d) When these networks are composed, each of the six non-flat regions from the first network is divided into two new regions by the second network to create a total of 13 linear regions.](images/c4-fig-0002.jpg)

[图 4.2](#c004.xhtml#c4-fig-0002a) 组合具有二维输入的神经网络。a) 第一个网络（来自图 3.8）有三个隐藏单元，接收两个输入 `x[1]` 和 `x[2]` 并返回一个标量输出 `y`。这被传递给一个具有两个隐藏单元的第二个网络以产生 `y′`。b) 第一个网络产生一个由七个线性区域组成的函数，其中一个区域是平坦的。c) 第二个网络定义了一个在 `y ∈ [−1, 1]` 中包含两个线性区域的函数。d) 当这些网络组合时，第一个网络的六个非平坦区域中的每一个都被第二个网络分成两个新区域，从而创建总共 13 个线性区域。

另一种理解组合网络的方式是：第一个网络将输入空间 `x` “折叠”回自身，使得多个输入产生相同的输出。然后第二个网络应用一个函数，该函数在所有被折叠重叠的点上被复制（[图 4.3](#c004.xhtml#c4-fig-0003)）。

![Figure 4.3 Deep networks as folding input space. a) One way to think about the first network from figure 4.1 is that it “folds” the input space back on top of itself. b) The second network applies its function to the folded space. c) The final output is revealed by “unfolding” again.](images/c4-fig-0003.jpg)

[图 4.3](#c004.xhtml#c4-fig-0003a) 深度网络作为输入空间的折叠。a) 理解 [图 4.1](#c004.xhtml#c4-fig-0001) 中第一个网络的一种方式是，它将输入空间“折叠”回自身顶部。b) 第二个网络将其函数应用于折叠后的空间。c) 通过再次“展开”，最终输出显现出来。

## 4.2 从组合网络到深度网络

上一节展示了我们可以通过将一个浅层神经网络的输出传递给第二个网络来创建复杂函数。我们现在表明，这是具有两个隐藏层的深度网络的一个特例。

第一个网络的输出（`y = ϕ[0] + ϕ[1]h[1] + ϕ[2]h[2] + ϕ[3]h[3]`）是线性的，第二个网络的第一步运算（方程 4.3，其中我们计算 ![c4-fig-5023.jpg](images/c4-fig-5023.jpg)、![c4-fig-5024.jpg](images/c4-fig-5024.jpg) 和 ![c4-fig-5025.jpg](images/c4-fig-5025.jpg)）也是线性的。将一个线性函数应用于另一个线性函数会产生另一个线性函数。当我们将 `y` 的表达式代入方程 4.3 时，结果为：

![c4-fig-5005.jpg](images/c4-fig-5005.jpg)  
(4.5)

我们可以将其重写为：

![c4-fig-5006.jpg](images/c4-fig-5006.jpg)  
(4.6)

其中 ![c4-fig-5026.jpg](images/c4-fig-5026.jpg)*、* ![c4-fig-5027.jpg](images/c4-fig-5027.jpg)*、* ![c4-fig-5028.jpg](images/c4-fig-5028.jpg) 等。结果是一个具有两个隐藏层的网络（[图 4.4](#c004.xhtml#c4-fig-0004)）。

![Figure 4.4 Neural network with one input, one output, and two hidden layers, each containing three hidden units.](images/c4-fig-0004.jpg)

[图 4.4](#c004.xhtml#c4-fig-0004a) 具有单输入、单输出和两个隐藏层的神经网络，每层包含三个隐藏单元。

由此可见，两层网络可以表示将一个单层网络的输出传递给另一个单层网络所创建的函数族。事实上，它表示一个更广泛的函数族，因为在方程 4.6 中，九个斜率参数 `ψ[11]`、`ψ[21]`、`…`、`ψ[33]` 可以取任意值，而在方程 4.5 中，这些参数被约束为外积 ![c4-fig-5029.jpg](images/c4-fig-5029.jpg)[`ϕ[1]`、`ϕ[2]`、`ϕ[3]`]。

## 4.3 深度神经网络

在上一节中，我们展示了组合两个浅层网络产生了具有两个隐藏层的深度网络的一个特例。现在我们考虑具有两个隐藏层、每层包含三个隐藏单元的深度网络的一般情况（[图 4.4](#c004.xhtml#c4-fig-0004)）。第一层定义为：

![c4-fig-5007.jpg](images/c4-fig-5007.jpg)  
(4.7)

第二层定义为：

![c4-fig-5008.jpg](images/c4-fig-5008.jpg)  
(4.8)

输出定义为：

![c4-fig-5009.jpg](images/c4-fig-5009.jpg)  
(4.9)

考虑这些方程，可以得出另一种关于网络如何构建日益复杂函数的理解方式（[图 4.5](#c004.xhtml#c4-fig-0005)）：

---

**笔记本 4.2**  
裁剪函数

---

1. 第一层中的三个隐藏单元 `h[1]`、`h[2]` 和 `h[3]` 通过形成输入的线性函数并将其通过 ReLU 激活函数来计算，这与常规方式相同（方程 4.7）。
2. 第二层的预激活值通过获取这些隐藏单元的三个新线性函数来计算（方程 4.8 中激活函数的参数）。此时，我们实际上拥有了一个具有三个输出的浅层网络；我们计算了三个分段线性函数，它们的线性区域之间的“关节”位于相同的位置（见图 3.6）。
3. 在第二隐藏层，另一个 ReLU 函数 `a[•]` 被应用到每个函数上（方程 4.8），这会对它们进行裁剪，并为每个函数添加新的“关节”。
4. 最终输出是这些隐藏单元的线性组合（方程 4.9）。

