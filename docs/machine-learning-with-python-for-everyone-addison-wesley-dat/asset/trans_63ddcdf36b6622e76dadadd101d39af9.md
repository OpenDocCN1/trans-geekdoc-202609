
到一个常数。常数是一种特定、受限类型的 *水平* 线。我们穿过 y = −3 的黄色线就是其中之一。

我们可以将关于 np.dot 的想法与关于线的想法结合起来，编写一些略有不同的代码来绘制此图。不使用 (m, b) 对，我们可以写一个值数组 w = (w₁, w₀)。这里有一个技巧：我把 w₀ 放在第二位，以与 b 对齐。通常，在数学中就是这样写的：w₀ 是常数。

有了 ws，我们就可以使用 np.dot，只要我们用一列 1 来扩充 xs。我将这个扩充后的 xs 记为 xs_p1，你可以读作“xs plus a column of ones”。这一列 1 在 y = mx + b 中扮演 1 的角色。等等，你没看到 1 吗？让我重写一下：y = mx + b = mx + b · 1。你看我如何把 b 重写为 b · 1？这正是我们需要做的让 np.dot 满意的事情。dot 想要把某物乘以 w₁，把某物乘以 w₀。我们确保乘以 w₀ 的东西是一个 1。

我把在后面加上 1 列这个过程称为 *加一技巧* 或 *+1 技巧*，我稍后会更多地谈论它。下面是 *加一技巧* 对我们原始数据的作用：

In [26]:

```
# np.c_[] lets us create an array column-by-column
xs = np.linspace(-3, 3, 100)
xs_p1 = np.c_[xs, np.ones_like(xs)]

# view the first few rows
display(pd.DataFrame(xs_p1).head())
```

|   | 0 | 1 |
|---|---|---|
| 0 | -3.0000 | 1.0000 |
| 1 | -2.9394 | 1.0000 |
| 2 | -2.8788 | 1.0000 |
| 3 | -2.8182 | 1.0000 |
| 4 | -2.7576 | 1.0000 |

现在，我们可以非常简洁地组合我们的数据和权重：

In [27]:

```
w = np.array([1.5, -3])
ys = np.dot(xs_p1, w)

ax = plt.gca()
ax.plot(xs, ys)

# styling
ax.set_ylim(-4, 4)
high_school_style(ax)
```

```
ax.plot(0, -3,'ro')  # y-intercept
ax.plot(2, 0,'ro');  # two steps to the right should be three whole steps up
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_67_0.png)

这里是我们在代码中使用的两种形式：ys = m*xs + b 和 ys = np.dot(xs_p1, w)。在数学上，它们看起来像 y = mx + b 和 y = wx⁺。这里，我用 x⁺ 作为在 x 后面加上 1 的缩写。这两种定义 ys 的形式含义相同。它们在实现时只是有一些差异。第一种形式让每个分量各自独立。第二种形式要求 x⁺ 用 1 进行扩充，并允许我们方便地使用点积。

## 2.6.2 超越直线

我们可以至少以两种方式扩展线的概念。我们可以进展到波浪曲线和多项式——像 f(x) = x³ + x² + x + 1 这样的方程。这里，我们对一个输入值 x 进行更复杂的计算。或者，我们可以走向多维度的道路：平面、超平面等等！例如，在 f(x, y, z) = x + y + z 中，我们有多个输入值，我们将它们组合在一起。由于我们将非常关注多元数据——也就是多个输入——我将直接进入其中。

让我们重新审视摇滚音乐会场景。如果我们想购买的不止一种商品会怎样？例如，你可能会惊讶地得知人们喜欢在音乐会上饮用饮料。通常，他们喜欢饮用我母亲亲切地称之为“root beer”的东西。那么，如果我们有停车费用、票价，以及我们团体订购的每杯 root beer 的费用呢？为了考虑这一点，我们需要一个新的公式。令 rb 代表 root beer，我们有：

total_cost = ticket_cost × number_people + rb_cost × number_rbs + parking_cost

如果我们代入停车费用、每张票费用和每杯 root beer 费用的已知值，那么我们就有更具体的内容：

total_cost = 80 × number_people + 10 × number_rbs + 40

对于一个商品，我们有一个简单的二维线图，其中一个轴方向来自输入“多少人”，另一个来自输出“总费用”。对于两个商品，我们现在有两个“多少”，但仍然只有一个 total_cost，总共三个维度。幸运的是，我们仍然可以相当合理地绘制它。首先，我们创建一些数据：

In [28]:

```
number_people = np.arange(1, 11) # 1-10 people
number_rbs    = np.arange(0, 20) # 0-19 rootbeers

# numpy tool to get cross-product of values (each against each)
# in two paired arrays. try it out: np.meshgrid([0, 1], [10, 20])
# "perfect" for functions of multiple variables
number_people, number_rbs = np.meshgrid(number_people, number_rbs)

total_cost = 80 * number_people + 10 * number_rbs + 40
```

我们可以从几个不同的角度——字面意义上——来看这些数据。下面，我们从五个不同的视角展示同一个图。请注意，它们都是平坦的表面，但从不同视角看，表面的明显倾斜或斜率看起来不同。平坦的表面称为平面。

In [29]:

```
# import needed for 'projection':'3d'
from mpl_toolkits.mplot3d import Axes3D
fig,axes = plt.subplots(2, 3,
                        subplot_kw={'projection':'3d'},
                        figsize=(9, 6))

angles = [0, 45, 90, 135, 180]
for ax,angle in zip(axes.flat, angles):
    ax.plot_surface(number_people, number_rbs, total_cost)
    ax.set_xlabel("People")
    ax.set_ylabel("RootBeers")
    ax.set_zlabel("TotalCost")
    ax.azim = angle

# we don't use the last axis
```

```
axes.flat[-1].axis('off')
fig.tight_layout()
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_69_0.png)

在代码和数学中，超越三维是相当直接的。然而，如果我们尝试将其绘制出来，就会变得非常混乱。幸运的是，我们可以使用一个老式的好工具——对内行来说那是 GOFT——并制作一个结果表。下面是一个例子，它还包括了我们音乐会参与者的一些食物。我们将以每根 5 美元的价格吃一些热狗：

total_cost = 80 × number_people + 10 × number_rbs + 5 × number_hotdogs + 40

我们将为音乐会系统中的物品数量使用几个简单的值：

```
In [30]:

number_people = np.array([2, 3])
number_rbs = np.array([0, 1, 2])
number_hotdogs = np.array([2, 4])

costs = np.array([80, 10, 5])

columns = ["People", "RootBeer", "HotDogs", "TotalCost"]
```

我通过一个辅助函数 np_cartesian_product 将几个 numpy 数组在所有可能的组合中组合起来，这与 itertools 的 combinations 函数所做的事情类似。它涉及一点黑魔法，所以我把它隐藏在 mlwpy.py 中。随意调查，如果你敢的话。

```
In [31]:

counts = np_cartesian_product(number_people,
                              number_rbs,
                              number_hotdogs)

totals = (costs[0] * counts[:, 0] +
         costs[1] * counts[:, 1] +
         costs[2] * counts[:, 2] + 40)

display(pd.DataFrame(np.c_[counts, totals],
                     columns=columns).head(8))
```

|  | 人数 | 根啤 | 热狗 | 总费用 |
|---|---|---|---|---|
| 0 | 2 | 0 | 2 | 210 |
| 1 | 2 | 0 | 4 | 220 |
| 2 | 3 | 0 | 2 | 290 |
| 3 | 3 | 0 | 4 | 300 |
| 4 | 2 | 1 | 2 | 220 |
| 5 | 2 | 1 | 4 | 230 |
| 6 | 3 | 1 | 2 | 300 |
| 7 | 3 | 1 | 4 | 310 |

对 totals 的赋值——在上一个单元格的第 6-8 行——相当丑陋。我们能改进它吗？想想！想想！一定有更好的方法！那里发生了什么？我们在把几样东西加起来。而我们加起来的东西来自逐元素相乘。会是吗？是点积吗？是的，就是。

```
In [32]:

costs = np.array([80, 10, 5])
counts = np_cartesian_product(number_people,
                              number_rbs,
                              number_hotdogs)

totals = np.dot(counts, costs) + 40
display(pd.DataFrame(np.column_stack([counts, totals]),
                     columns=columns).head(8))
```

|  | 人数 | 根啤 | 热狗 | 总费用 |
|---|---|---|---|---|
| **0** | 2 | 0 | 2 | 210 |
| **1** | 2 | 0 | 4 | 220 |
| **2** | 3 | 0 | 2 | 290 |
| **3** | 3 | 0 | 4 | 300 |
| **4** | 2 | 1 | 2 | 220 |
| **5** | 2 | 1 | 4 | 230 |
| **6** | 3 | 1 | 2 | 300 |
| **7** | 3 | 1 | 4 | 310 |

使用点积给我们带来两个好处：(1) 赋给 total 的代码行得到了极大的改进，(2) 我们可以在很大程度上任意扩展我们的成本和计数，而完全不需要修改计算代码。你可能会注意到我手工加上了 +40。那是因为我不想回到 *+1 技巧*——但我本可以。

顺便说一下，这在数学课上会发生什么。正如我们从重复加法到点积的代码行压缩所看到的，当我们使用高级符号时，细节往往会被抽象掉或移到幕后。以下是发生了什么的详细分解。首先，我们通过删除详细的变量名进行抽象，然后用通用标识符替换我们已知的数值：

$y = 80x_3 + 10x_2 + 5x_1 + 40$

$y = w_3x_3 + w_2x_2 + w_1x_1 + w_0 \cdot 1$

我们在代码中更进一步，用点积替换 wx 和：

$y = w_{[3,2,1]} \bullet x + w_0 \cdot 1$

w 上奇怪的 [3, 2, 1] 下标表示我们没有使用所有的权重。也就是说，我们没有在左边的项中使用 w0。w0 在右边的项中乘以 1。它只被使用一次。最后的致命一击是执行 *+1 技巧*：

$y = wx^+$

总之，代替 $y = w_3x_3 + w_2x_2 + w_1x_1 + w_0$，我们可以写成 $y = wx^+$。

## 2.7 符号与加一技巧

现在你知道了 *加一技巧* 是什么，我想展示几种我们可以谈论数据表的方式。这些数据可能由值组成，例如我们去棒球场的旅行费用表。我们可以取这个表并在它周围画一些括号：
