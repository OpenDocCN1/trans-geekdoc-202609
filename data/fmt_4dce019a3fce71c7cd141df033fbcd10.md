
**预测**：具有缺失值的属性可以被目标变量预测。因此，可以使用机器学习算法对其进行预测。在采用这种方法时，至关重要的是记住，机器学习算法不允许空值的存在。否则，算法可能会将空值视为有效值。

## 8.2 数据预处理

从源收集的数据通过保持文件格式和处理缺失值进行预处理。因此，数据包含了所有准确的值，没有缺失值，并且属性对齐。让我们来看图 8.3 中的我们的数据集。

![FIGURE 8.3: Rattle 中预处理的 IoT 实验数据](img/fig8_3.jpg)

图 8.3：Rattle 中预处理的 IoT 实验数据

查看我们的数据的选项有限。在 Rattle 中，我们可以查看我们的数据。查看我们的数据的选项有限。在 Rattle 中，我们可以查看我们的数据。查看我们的数据的选项有限。在 Rattle 中，我们可以查看我们的数据。查看我们的数据的选项有限。在 Rattle 中，我们可以查看我们的数据。查看我们的数据的选项有限。在 Rattle 中，我们可以查看我们的数据。查看我们的数据的选项有限。在 Rattle 中，我们可以查看我们的数据。查看图 8.2。

## 8.3 数据清洗

从源收集的数据通过保持文件格式和处理缺失值进行预处理。因此，数据包含了所有准确的值，没有缺失值，并且属性对齐。让我们来看图 8.3 中的我们的数据集。

```
[1] 0
```

完整的工作过程由算法 1 给出。为了更清晰地理解 CNN 的功能，R 语言中 CNN 程序的截图在图 8.4 中。上方显示了带有代码和输出的完整程序。CNN 通过 NN 算法找到一致子集以正确分类剩余实例。在第一个实例的帮助下，它遍历整个集合并找到被完全分类的实例。

程序 1 在 R 语言中实现。首先，包含 CNN 所需的库。我们已经像之前的示例那样，使用分割数据函数检索了某些数据。CNN 的输出可以通过下文讨论的各种参数如 `repIdx` 和 `repLab` 来查看。

- `cleanData`：一个存储过滤后数据集的数据框。
- `remIdx`：一个包含被移除实例索引的向量（行号向量）。
- `repIdx`：一个包含修复实例索引的向量。
- `repLab`：展示了修复实例的新标签。

![图 8.4: 在 R 中实现紧凑近邻规则](img/fig8_4.jpg)

图 8.4：在 R 中实现紧凑近邻规则

- `parameters`：它代表参数值。
- `call`：它代表函数调用。
- `extraInf`：它是额外的有趣信息。

### 8.3.2 Tomek

使用 Tomek 链接解决不平衡分类问题的函数命名为 `TomekClassif`。它通过破坏一个或多个链接来执行欠采样，从而破坏 Tomek 链接。`TomekClassif` 函数的语法如下。

```
TomekClassif(form, data, dist = “Euclidean”, Cl = “all”, rem = “both”)
```

在此函数中，使用的参数讨论如下：

- `Form`：它是描述预测期间问题的公式。
- `Data`：它是你将用于机器学习模型实验的数据。所使用的数据集可能是不平衡的。
- `Distance`：有各种距离度量来估计最近邻。它以字符形式指定。定义了一些指标，例如对于数值实例——`Canberra`、`Manhattan`、`Chebyshev`、`Euclidean`、`p-norm`；对于名义实例为 `overlap`；对于两种实例为 `HEOM` 和 `HVDM`。

![图 8.5: 用于不平衡分类问题的 Tomek 链接实现](img/fig8_5.jpg)

图 8.5：用于不平衡分类问题的 Tomek 链接实现

- `p`：仅在选择的距离度量为 `p-norm` 时定义。其值等同于 `p-norm` 的 `p`。
- `Cl`：定义了目标为欠采样的类。可以是类的特定子集。
- `rem`：定义了要被丢弃的类。如果两个类都要被丢弃，则设置为 `both`。

`TomekClassif` 函数的工作由图 8.5 展示。它的语法和参数在之前已经定义。

**程序 2：**

```
library(ggplot2)
library(readr)
library(DMwR)
library(lattice)
library(unbalanced)
library(grid)
library(UBL)
data(segmentationData)
segmentationData
data <- segmentationData[-c(1,2)]
form <- as.formula(Class.)
a <- TomekClassif(form, data, dist = “HVDM”)
b <- TomekClassif(form, data, dist = “HEOM”)
c <- TomekClassif(form, data, dist = “HVDM”)
d <- TomekClassif(form, data, dist = “HVDM”)
s <- TomekClassif(form, data, dist = “Euclidean”)
```

**输出：**

```
summary(s)
summary(a)
summary(b)
summary(c)
summary(d)
```

### 8.3.3 单侧

`OSSClassif` 函数用于单侧策略。`OSSClassif` 的语法如下。

```
OSSClassif(form, data, dist = “Euclidean”, p = 2, Cl = “smaller”, start = “CNN”)
```

在此函数使用的参数讨论如下：

1. `Form`：它是描述预测问题的公式。
2. `Data`：它是用于实验机器学习模型的数据。数据集可能是不平衡的。
3. `Distance`：有各种距离度量来估计最近邻。它以字符形式指定。定义了一些指标，例如数值实例——`Canberra`、`Manhattan`、`Chebyshev`、`Euclidean`、`p-norm`；名义实例为 `overlap`；对于两种实例为 `HEOM` 和 `HVDM`。
4. `p`：仅在选择的距离度量为 `p-norm` 时定义。其值等同于 `p-norm` 的 `p`。
5. `Cl`：定义了目标为欠采样的类。可以是类的特定子集。
6. `Start`：决定初始功能，即函数的策略。它可以是 `CNN` 或 `Tomek`。两种策略都应用了，可以设置优先级。

**程序 3：**

```
library(DMwR)
library(UBL)
data(segmentationData)
segmentationData
data <- segmentationData[-c(1,2)]
form <- as.formula(Class.)
a <- OSSClassif(form, data, dist = “HVDM”)
b <- OSSClassif(form, data, dist = “HEOM”, start = “Tomek”)
c <- OSSClassif(form, data, dist = “HVDM”, start = “CNN”)
d <- OSSClassif(form, data, dist = “HVDM”, start = “Tomek”)
e <- OSSClassif(form, data, dist = “HEOM”)
```

**输出：**

```
summary(a)
summary(b)
summary(c)
summary(d)
summary(e)
```

### 8.3.4 SMOTE

`SMOTE` 函数如图 8.6 所示，处理不平衡分类问题。在 SMOTE 处理后的数据中实现变异后，输出展示在图 8.7 中。该函数的语法如下：

```
SMOTE(form, data, perc.over = 200, k = 5, perc.under = 200, learner = NULL, ...)
```

下文讨论了该函数使用的不同参数。

1. `form`：描述设计问题工作原理的公式。
2. `data`：这是一个不平衡数据集，旨在通过此函数进行平衡。
3. `perc.over`：这是一个参数，指定为少数类样本创建的案例数量。通常，它等于 100 以保持比例。
4. `k`：这会为少数类数量创建案例数量，但该参数指示用于生成实例的最近邻的频率。
5. `perc.under`：这是一个参数，指定为少数类样本从多数类样本中选择的额外案例数量。

![图 8.6：用于不平衡分类问题的 SMOTE 实现](img/fig8_6.jpg)

图 8.6：用于不平衡分类问题的 SMOTE 实现

![图 8.7：用于不平衡分类问题的 SMOTE 结果绘图](img/fig8_7.jpg)

图 8.7：用于不平衡分类问题的 SMOTE 结果绘图

6. `learner`：这是一个可选参数，用于指定分类算法。
7. `…`：如果你指定了学习器（参数 `learner`），你可以指定在调用此学习器时可以使用 `f` 参数。

**程序 4：**

```r
library(UBL)
data(segmentationData)
segmentationData
data <- segmentationData[,-c(1,2)]
form <- as.formula(Class.)
newData<- SMOTE(form, data, perc.over = 600,perc.under=100)
plot(data[, 1], data[, 2], pch = 19 + as.integer(data[, 3]), main = “Original Data”)
plot(newData[, 1], newData[, 2], pch = 19 + as.integer(newData[,3]), main = “SMOTE’d Data”)
classTree<- SMOTE(form, data, perc.over = 600,perc.under=100, learner=’rpartXse’,se=0.5)
rpartXse(form,data,se=0.5)
```

**输出：** n= 2019（`data` 中的实例数量）

```
1) root 2019 719 PS (0.64388311 0.35611689)
2) TotalIntenCh2< 47256.5 967 83 PS (0.91416753 0.08583247) *
3) TotalIntenCh2>=47256.5 1052 416 WS (0.39543726 0.60456274)
6) FiberWidthCh1< 11.19756 434 175 PS (0.59677419 0.40322581)
12) AvgIntenCh1< 165.0862 323 99 PS (0.69349845 0.30650155) *
13) AvgIntenCh1>=165.0862 111 35 WS (0.31531532 0.68468468)
26) TotalIntenCh3>=59653.5 32 10 PS (0.68750000 0.31250000) *
27) TotalIntenCh3< 59653.5 79 13 WS (0.16455696 0.83544304) *
7) FiberWidthCh1>=11.19756 618 157 WS (0.25404531 0.74595469)
14) ConvexHullPerimRatioCh1< 0.8160616 22 5 PS (0.77272727 0.22727273) *
15) ConvexHullPerimRatioCh1>=0.8160616 596 140 WS .6 *
```

### 8.3.5 ADASYN 算法

`Adasynif` 函数提供了不平衡分类问题的解决方案。它通过在 SMOTE 中通过生成合成示例来处理不平衡的类别。因此，ADASYN 算法的实现在图 8.8 中。ADASYN 算法的结果展示在图 8.9 中。其实现在图 8.10 中。

```
Adasynif(form, data, baseClass = NULL, k = 5, dist = “Euclidean”)
```

1. `Form`：描述设计问题工作原理的公式。
2. `Data`：这是一个不平衡数据集，旨在通过此函数进行平衡。
3. `under`：指定为少数类样本从多数类样本中选择的额外案例数量的参数。
4. `over`：指定为少数类样本创建的案例数量的参数。
5. `k`：该参数指示用于生成实例的最近邻的频率。
6. `baseClass`：这是一个用于指定多数类平衡比例的可选参数。
7. `beta`：这是一个指定合成示例比例的数值参数，默认为 1。

**程序 5：**

```r
library(rpart)
library(rattle)
library(RColorBrewer)
library(party)
library(partykit)
library(caret)
library(UBL)
data(segmentationData)
segmentationData
data <- segmentationData[,-c(1,2)]
form <- as.formula(Class.)
newData<- Adasynif(form, data)
plot(data[, 1], data[, 2], pch = 19 + as.integer(data[, 3]), col = as.integer(data[, 3]), main = “Original Data”)
plot(newData[, 1], newData[, 2], pch = 19 + as.integer(newData[, 3]), col = as.integer(newData[,3]), main = “New Data”)
out <- Adasynif(form, data)
print(out)
```

**输出：**

```
Class
PS:1300
WS:1225
```

![图 8.10：应用 ADASYN 算法的数据](img/fig8_10.jpg)

图 8.10：应用 ADASYN 算法的数据

### 8.3.6 SOTU

该方法背后的想法是处理由于类别不平衡导致的准确性问题。例如，在标准数据集 WEBSPAM-UK 2007 中，垃圾邮件标签的比例少于其他标签。这可能导致分类器的偏差。当少数类（即垃圾邮件）是目标类时，对其进行了特殊处理。采用的方法是“过采样划分和欠拟合训练”（SOTU）。它通过创建少数类的多个副本来进行过采样。通过一次对一个样本集进行训练来避免过拟合。每个集都包含少数类和多数类的等实例。整个数据集被划分为 11 个样本桶。模型对不同的集合进行 11 次训练和测试。因此，可以说系统是使用无偏数据进行训练的。所提数据清洗方法中的样本分布如图 8.11 所示。

`Eq. 8.1` 用于样本集的公式化。`S` 指数据集的训练文件。`x[m]` 指少数类别的实例，而 `x[n]` 指多数类别的实例。`d` 是样本集的数量；它取决于问题的类型和特征的数量。在分类问题中，它被固定为奇数。在回归问题中，它被固定为偶数。估算的数量应该接近特征的数量（如果需要，建议变动为 1）。由于垃圾邮件检测是一个分类问题，因此估计为奇数。在本提议中，特征数量为 11，这已经是一个奇数了。`d` 固定为值 11，形成的样本集为 11 个。

## 8.4 总结与后续展望

机器学习模型中要处理的数据应该是干净且无噪声的。为了这一点，本章详细阐述了所使用的各种方法。数据格式应该保持一致，因此本章详细阐述了不同的文件格式。此外，解释了各种数据清洗方法，例如压缩最近邻规则、Tomek、单侧选择、SMOTE 等许多方法，如 `Table 8.2` 所示。这些方法在 R 中执行以便进行更好的说明。

![](img/tab8_2_B.gif)

## 8.5 练习

### 思考

1. 在收集数据和执行数据聚合时，需要考虑哪些重要的限制？
2. 有哪些不同的文件格式？
3. 你应该如何处理数据中的缺失值？
4. 数据清洗是指？
5. 详细解释 CNN 方法。
6. 详细解释 Tomek 方法。
7. 详细解释单侧选择方法。
8. 解释 SMOTE 所遵循的方法。
9. 定义 SOTU 所遵循的方法论。
10. 用一个例子简要描述 ADASYN 算法。

### 单选题

**1：实例在 ARFF 文件是如何排列的？**

(a) 有序 (b) 无序 (c) 排序 (d) 以上都不是

**2：压缩文件的扩展名是什么？**

(a) `.zip` (b) `.jar` (c) `.exe` (d) 以上都不是

**3：稀疏文件包含最大数量的：**

(a) 0 (b) 1 (c) 十进制值 (d) 以上都不是

**4：文件中处理缺失数据采用了哪种技术？**

(a) 删除 (b) 替换 (c) 预测 (d) 以上所有

**5：CNN 的哪个参数代表修复实例的标签？**

(a) `cleanData` (b) `repIdx` (c) `repLab` (d) `remIdx`

**6：CNN 的哪个参数用于存储过滤后的数据？**

(a) `cleanData` (b) `repIdx` (c) `repLab` (d) `remIdx`

**7：Tomek 函数的 `p` 参数的作用是什么？**

(a) `p-norm` (b) `p-index` (c) `p-data` (d) 以上都不是

**8：单侧选择策略使用了哪个函数？**
