

```python
print("my_ints",
simple1.features.feature['my_ints']
int64_list.value)
print("my_floats",simple1.features.feature['my_floats'].float list.value)
print("my_bytes",
simple1.features.feature['my_bytes']
bytes_list.value)
#print("simple1",simple1)
```

列表 6.29 定义了变量 `simple1`，它是 `tf.train.Example` 类的一个实例。`simple1` 变量定义了一个由 `my_ints`、`my_floats` 和 `my_bytes` 字段组成的记录，它们的类型分别为 `Int64List`、`Floatlist` 和 `Bytest`。列表 6.29 的最后部分包含 `print()` 语句，用于显示 `simple1` 变量中元素的值，如下：

```python
('my_ints:', [2L, 5L])
('my_floats:', [3.5999999046325684])
('my_bytes:', ['data'])
```

## 总结

本章向你介绍了 TensorFlow Datasets 和迭代器，它们非常适合处理“正常”大小的数据集，而这些数据集太大，无法完全放入内存中。你学习了如何定义 lambda 表达式并在 TensorFlow Dataset中使用该表达式。

接下来，你学习了各种“惰性操作符”，包括 `filter()`、`map()`、`filter()`、`flatmap()`、`take()` 和 `zip()`，以及如何使用它们来定义 TensorFlow Dataset 中数据的子集。你还学习了如何在 TensorFlow 中使用单次迭代器（one-shot iterators）和可重迭代器（reusable iterators），以遍历 TensorFlow Datasets 中的元素。

然后，你简要地介绍了 `tf.estimators` 命名空间，它包含了实现各种算法的各类类，例如提升树、DNN 分类器、DNN 回归器、线性分类器和线性回归器。之后，你了解到 `tf.layers` 命名空间包含一组用于 DNN（密集神经网络）和 CNN（卷积神经网络）的类。

最后，你学习了 TensorFlow TFRecord，这是一种描述了模型在训练阶段和测试阶段所需数据的文件。

## 索引

### A
- 常量，153, 156
- 在 Pandas DataFrame 中添加列，82–83
- 字母字符测试，18–19
- andas-scatter-df.py, 83–84
- anorm1, 42
- anorm2, 42
- anorm3, 43
- 向数组中添加元素，34–35
- append1.py, 34
- append2.py, 35
- 算术运算
    - 整数，11
    - 在 TensorFlow 图中，160–161
- arr1, 33–39, 167, 168
- arr2, 33, 37–38
- arr3, 37–38
- array-norm.py, 42–43
- 数组，32
    - 向其添加元素，34–35
    - 与指数，37–38
    - 数学运算和，38
    - 乘列表列表和，35–36
    - 在 TensorFlow 中，167–169
        - 将 Python 数组转换为，170
        - 两个相乘，169–170
    - 以及向量操作，40
    - 处理“-1”子范围的，39
- array-vector.py, 40
- ASCII 字符集，15
- ASCII 编码的字节，15
- asqusum, 42

### B
- basic-stuff.ipynb, 94
- batch() 操作符，187–189
- zip() 操作符和，197–198
- best_fit_slope(), 56, 116
- 拟合超平面，51
- 拟合直线，52–53, 118
    - 在 Matplotlib 中，115–116
    - 在 NumPy 中，56–57
- 布尔型 DataFrame，67–68
- 内置数据集，Seaborn，134
- 内置函数，TensorFlow 图和，161–162

### C
- center() 函数，32
- CharTypes.py, 19
- “checkpoint” API，147
- “chunked” 效果，187
- 数据的“块”，89
- 云平台，96
- 代码示例，45–46
- 彩色网格，在 Matplotlib 中，107
- 未标记网格中的彩色正方形，108–109
- 命令行参数，27–29
- “被注释掉”的代码块，190
- Python 中的注释，7
- comments.txt, 193, 194
- Compare.py, 17
- 编译时间，10
- “计算”图，147
- 混淆矩阵，132
- 常量，153, 156
- arr1, 167, 168
    - 在 TensorFlow 中，150–157
    - 在 tf.Session() 中，154
- Conv2D 层，205
- costs 数组，58
- 成本与迭代，59, 61
- CPU，169, 172
- CSV 文件，201
- Pandas DataFrame 和，74–76
- 虚线网格，105
- 数据清洗任务，64–65
- DataFrame, Pandas，64–65
- 布尔，67–68
- 合并，69–71
- 数据操作，71–74
    - 以及 CSV 文件，74–76
    - 以及 Excel 表格，76–78
    - 以及直方图，84–86
    - 数值，66–67
    - NumPy 函数和大型数据集，89
    - 以及随机数，68–69
    - 以及散点图，83–84
    - 选择，添加，并删除列，82–83
    - 以及简单统计，86–87
    - 以及 模拟数据集，78–79
    - 标准化，87
    - 转置，68
- 数据操作，使用 Pandas DataFrame，71–74
- dataset.flat_map(), 191, 194
- dataset.map(), 189, 191
- Datasets，176
- 基础步骤，176
- 来自 CSV 文件，201
- 模块，119
- 以及随机数，199–200
- 简单，176
- 数据类型，10
- 日期，22–23
- 转换为字符串，24
- datetime2.out, 23
- datetime2.py, 23
- 延迟执行，147
- 在 Pandas DataFrame 中删除列，82–83
- “delta”值，57
- describe() 方法，65
- diagonals1.py, 101–102
- Digits 数据集，122, 123, 178
    - 在 Sklearn 中，119–121
- 数字数字测试，18–19
- 维度，32
- dir() 函数，29
- 显示图像，在 Sklearn 中，122–123
- dotproduct2.py, 41
- 点积，NumPy 和，41–42
- 点线网格，在 Matplotlib 中，104–105
- double-list1.py, 36
- dx.map(), 180

### E
- 动态执行，147
- 使用 for 循环，164–165
- 使用 while 循环，165–166
- easy_install 和 pip，2
- 元素，32
- employees-xl.py, 77–78
- （非垂直）直线，47
- 欧几里得平面中的，47–49, 52
- eval() 函数，11
- Example 类，206
- Excel 表格，Pandas 和，76–78
- 异常处理，24–25
- expl，38
- exponent-array1.py, 37–38
- 指数值，163
- exponent-list1.py, 37
- 指数数组和，37–38
- 列表和，37

### F
- Feature 类，206
- 特性变量，202
- 可馈送迭代器，182
- feed_dict，151
- 占位符和，153–154, 158–159
- file.txt, 185
- filter() 操作符，183–184, 193–194
- find() 方法，20
- FindPos1.py, 19–20
- First.py, 8
- fit() 方法，128, 129, 132
- flat_map() 操作符，191–194
- float() 函数，11
- Floydhub, 96
- for 循环，114, 140, 163–164, 183
- format() 函数，12, 22
- Fraction() 函数，14
- 分数，14
- “模糊”线，110

### G
- getopt 模块，27
- Github，95
- Google Cloud Platform (GCP)，96, 173
- Google Colab，95, 172
- 基于 GPU 的 TensorFlow 代码，95, 96
- GPU 支持，169–170

### H
- “Hadamard”点积，43
- 重负载任务，81
- Hello.py, 28
- help() 函数，9
- history.py, 110
- 水平线，在 Matplotlib 中，100–101

### I
- if/else 语句，65
- import 语句，49
- Python 中的缩进，5
- 可初始化迭代器，182, 183
- input() 函数，26
- int() 函数，2–3
- IPython,
- iq-scores.py, 112–113
- Iris 数据集，132
- 在 Seaborn 中，134–135
- idx 变量，171
- 迭代器
    - 自己的，181
    - 可重用的，182–183
    - TensorFlow 中，181–182
- 索引，在，121, 123, 129, 135, 137, 52
- Jupyter，95, 172
- 特性，93–94
- 从命令行启动，94
- JupyterLab，94

### L
- 有标签的 Pandas DataFrame，65–66
- 标签变量，201
- labs_height 变量，111
- lambda 表达式，179–180, 184, 186, 189–194, 197
- 在 TensorFlow 中，180–181
- 大型数据集，89
- len(sys.argv), 27
- LeNet，205
- 线性回归，51–52
- 数据集，50, 51
- 在 Matplotlib 中，116–118
- 均方误差，53–54
- 多变量分析，52
- 非线性数据集，52–53
- 使用 NumPy，116–118
- 以及 Matplotlib，116–118
- 在 Sklearn 中，129–131
- LinearRegression 类，128, 129
- 折线图
- 广义散点图，57
- 散点点，35
- 线
- 在欧几里得平面中，47–49, 52
- 在 Matplotlib 网格中，105–106
- 使用 Matplotlib 绘图，49–50
- 使用 NumPy 绘图，49–50
- 在 Python 中，6
- 线段
- 网格中的彩色正方形，109
- 分段线性图的，49
- 简单的，112
- 树水平线，47, 101
