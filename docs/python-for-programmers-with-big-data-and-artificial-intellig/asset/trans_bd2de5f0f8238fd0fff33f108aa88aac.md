

13 frequencies[random.randrange(1, 7) - 1] += 1
14

## 函数 update：配置柱状图和文本

函数 update 中的第 16 行调用 matplotlib.pyplot 模块的 cla（清除坐标轴）函数，在为当前动画帧绘制新柱状图之前移除现有的柱状图元素。我们在上一章的数据科学简介部分讨论了第 17–27 行的代码。第 17–20 行创建柱状图，设置柱状图标题，设置 x 轴和 y 轴标签，并缩放图表为每个柱状图上方的频率和百分比文本留出空间。第 23–27 行显示频率和百分比文本。

单击此处查看代码图片

```
15 # reconfigure plot for updated die frequencies
16 plt.cla() # clear old contents of current Figure
17 axes = sns.barplot(faces, frequencies, palette='bright') # new
18 axes.set_title(f'Die Frequencies for {sum(frequencies):,} Rolls')
19 axes.set(xlabel='Die Value', ylabel='Frequency')
20 axes.set_ylim(top=max(frequencies) * 1.10) # scale y-axis by
21
22 # display frequency & percentage above each patch (bar)
23 for bar, frequency in zip(axes.patches, frequencies):
24     text_x = bar.get_x() + bar.get_width() / 2.0
25     text_y = bar.get_height()
26     text = f'{frequency:,}\\n{frequency / sum(frequencies):.3%}'
27     axes.text(text_x, text_y, text, ha='center', va='bottom')
28
```

## 用于配置图表和维护状态的变量

第 30 行和第 31 行使用 sys 模块的 argv 列表获取脚本的命令行参数。第 33 行指定 Seaborn 的 'whitegrid' 样式。第 34 行调用 matplotlib.pyplot 模块的 figure 函数以获取 Figure 对象，FuncAnimation 在其中显示动画。该函数的参数是窗口标题。如您不久将看到，这是 FuncAnimation 的必需参数之一。第 35 行创建一个包含骰子面值 1–6 的列表，用于在图表的 x 轴上显示。第 36 行创建一个六元素的 frequencies 列表，每个元素初始化为 0——我们会在每次掷骰子时更新此列表的计数。

单击此处查看代码图片

```
29 # read command-line arguments for number of frames and rolls per frame
30 number_of_frames = int(sys.argv[1])
31 rolls_per_frame = int(sys.argv[2])
32
33 sns.set_style('whitegrid') # white background with gray grid lines
34 figure = plt.figure('Rolling a Six-Sided Die') # Figure for animation
35 values = list(range(1, 7)) # die faces for display on x-axis
36 frequencies = [0] * 6 # six-element list of die frequencies
37
```

## 调用 animation 模块的 FuncAnimation 函数

第 39–41 行调用 Matplotlib 动画模块的 FuncAnimation 函数以动态更新柱状图。该函数返回一个表示动画的对象。尽管未显式使用，但您 *必须* 存储对动画的引用；否则，Python 会立即终止动画并将其内存返还给系统。

单击此处查看代码图片

```
38 # configure and start animation that calls function update
39 die_animation = animation.FuncAnimation(
40     figure, update, repeat=False, frames=number_of_frames, interval
41     fargs=(rolls_per_frame, values, frequencies))
42
43 plt.show() # display window
```

FuncAnimation 有两个必需参数：

- figure—用于显示动画的 Figure 对象，以及
- update—每帧动画调用一次的函数。

在此示例中，我们还传递以下可选关键字参数：

- repeat—False 在指定的帧数后终止动画。如果为 True（默认值），动画完成后会从头开始重新播放。
- frames—动画帧总数，控制 FuncAnimation 调用 update 的次数。传递整数相当于传递范围——例如，600 表示 range(600)。FuncAnimation 将此范围中的一个值作为每次调用 update 时的第一个参数传递。
- interval—动画帧之间的毫秒数（此示例中为 33，默认值为 200）。每次调用 update 后，FuncAnimation 会等待 33 毫秒再进行下一次调用。
- fargs（“function arguments”的缩写）要传递给您在 FuncAnimation 第二个参数中指定的函数的其他参数元组。您在 fargs 元组中指定的参数对应于 update 的参数 rolls、faces 和 frequencies（第 9 行）。

有关 FuncAnimation 的其他可选参数列表，请参见

![](img/34b7fc2f1ee27beb73bca14927d42340_255_0.png)

最后，第 43 行显示窗口。

## 6.5 总结

在本章中，我们讨论了 Python 的字典和集合集合。我们说明了什么是字典，并展示了几个示例。我们展示了键–值对的语法，并展示了如何使用它们在花括号 { } 中创建带有逗号分隔的键–值对列表的字典。您还使用字典推导式创建了字典。

您使用方括号 [ ] 检索键对应的值，并插入和更新键–值对。您还使用字典方法 update 更改键关联的值。您遍历了字典的键、值和项。

您创建了由唯一不可变值组成的集合。您使用比较运算符比较集合，使用集合运算符和方法组合集合，使用可变集合操作更改集合的值，并使用集合推导式创建集合。您看到集合是可变的。Frozensets 是不可变的，因此可以用作集合和 frozenset 的元素。

在数据科学简介部分，我们通过展示带有动态柱状图的掷骰子模拟，继续了我们的可视化介绍，使大数定律“栩栩如生”。除了上一章数据科学简介部分展示的 Seaborn 和 Matplotlib 功能外，我们还使用了 Matplotlib 的 FuncAnimation 函数来控制逐帧动画。FuncAnimation 调用了我们定义的一个函数，该函数指定了每个动画帧显示的内容。

在下一章中，我们将讨论使用流行的 NumPy 库进行面向数组的编程。正如您将看到的，NumPy 的 `ndarray` 集合在执行许多与 Python 内置列表相同的操作时，速度可快两个数量级。这种强大功能对于当今的大数据应用将非常有用。

## 使用 NumPy 进行面向数组的编程

### 目标

在本章中，您将：

- 了解数组与列表的区别。
- 使用 `numpy` 模块的高性能 `ndarrays`。
- 使用 IPython `%timeit` 魔法命令比较列表和 `ndarray` 的性能。
- 使用 `ndarrays` 高效存储和检索数据。
- 创建和初始化 `ndarrays`。
- 引用单个 `ndarray` 元素。
- 遍历 `ndarrays`。
- 创建和操作多维 `ndarrays`。
- 执行常见的 `ndarray` 操作。
- 创建和操作 pandas 一维 `Series` 和二维 `DataFrames`。
- 自定义 `Series` 和 `DataFrame` 索引。
- 计算 `Series` 和 `DataFrame` 中数据的基本描述性统计量。
- 自定义 pandas 输出格式中的浮点数精度。

### 大纲

- .1 简介
- .2 从现有数据创建数组
- .3 数组属性
- .4 用特定值填充数组
- .5 从范围创建数组
- .6 列表与数组性能：介绍 %timeit
- .7 数组运算符
- .8 NumPy 计算方法
- .9 通用函数
- .10 索引和切片
- .11 视图：浅拷贝
- .12 深拷贝
- .13 重塑和转置
- .14 数据科学简介：pandas Series 和 DataFrames
- .14.1 pandas Series
- .14.2 DataFrames
- .15 总结

## 7.1 简介

NumPy（数值 Python）库首次出现于 2006 年，是首选的 Python 数组实现。它提供了一种名为 ndarray 的高性能、功能丰富的 n 维数组类型，从本点起我们将使用其同义词 array 来指代它。NumPy 是 Anaconda Python 发行版安装的许多开源库之一。对数组的操作速度可快两个数量级

