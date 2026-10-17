
### 12.3.1 数值单变量图

在“获取数据”菜单中查找插入数据的额外支持，如图 12-6 所示。

搜索并点击“R 脚本”，如图 12-7 所示。

![](img/3c3c87d78136583581b0cf0620f5ae66_263_0.png)

![](img/3c3c87d78136583581b0cf0620f5ae66_263_1.png)

![](img/3c3c87d78136583581b0cf0620f5ae66_264_0.png)

图 12-8 使用 R 脚本导入 tooth growth 数据

源 (12-8)

```
Tooth_data <- ToothGrowth
```

导入 R 支持的数据以创建数值单变量图。输入源，如图 12-8 所示。

- `ToothGrowth` 数据

`ToothGrowth` 数据集包含了一项研究维生素 C 对 60 只实验鼠牙齿生长影响的实验结果。每只动物接受了三种剂量水平的维生素 C 之一（0.5、1 和 2 mg/天），通过两种给药方法之一：橙汁或抗坏血酸（维生素 C 的一种形式，编码为 VC）。

`ToothGrowth` 数据的属性是“len”（意味着牙齿长度）、“supp”（意味着支持类型 VC 或 OJ）和“dose”（意味着毫克/天的剂量数）。

加载后，你可以检查 `ToothGrowth` 数据，如图 12-9 所示。

数据导入完成后，用户可以注意到数据现在出现在“字段”中，如图 12-10 所示。检查右侧的“字段”以将数据导入 R 脚本。

![](img/3c3c87d78136583581b0cf0620f5ae66_265_0.png)

### 图 12-9 ToothGrowth 数据

![](img/3c3c87d78136583581b0cf0620f5ae66_265_1.png)

### 图 12-10 ToothGrowth 数据

数值数据如重量是连续的。通常情况下，身高等数据符合正态分布。

![](img/3c3c87d78136583581b0cf0620f5ae66_266_0.png)

### 图 12-11 ToothGrowth 数据

![](img/3c3c87d78136583581b0cf0620f5ae66_266_1.png)

### 图 12-12 ToothGrowth 数据

![](img/3c3c87d78136583581b0cf0620f5ae66_267_0.png)

### 图 12-13 ToothGrowth 分布

![](img/3c3c87d78136583581b0cf0620f5ae66_267_1.png)

### 图 12-14 ToothGrowth 分布

![](img/3c3c87d78136583581b0cf0620f5ae66_268_0.png)

### 图 12-15 ToothGrowth 分布

![](img/3c3c87d78136583581b0cf0620f5ae66_269_0.png)

### 图 12-16 ToothGrowth 分布

![](img/3c3c87d78136583581b0cf0620f5ae66_269_1.png)

### 图 12-17 ToothGrowth 分布

### 源代码 (12-19)

```
# dataset <- data.frame(dose, len, supp)
# dataset <- unique(dataset)

qqnorm(dataset$len, pch = 20)
qqline(dataset$len)
```

### 12.3.2 分类单变量图

点击“获取数据”（Get Data）菜单查找插入数据的更多支持，如图 12-20 所示。

![](img/3c3c87d78136583581b0cf0620f5ae66_271_0.png)

图 12-20 额外数据导入方法

搜索并点击如图 12-21 所示的“R脚本”图标。生成示例数据以创建分类单变量图。在 R脚本窗口中输入以下源代码，如图 12-22 所示。

256 机器学习：概念、工具与数据可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_272_0.png)

图 12-21 R 脚本数据导入方法

![](img/3c3c87d78136583581b0cf0620f5ae66_272_1.png)

图 12-22 生成示例数据

源代码 (12-22)

```
set.seed(1)
lang <- sample(x=1:5, size=100, replace=TRUE)
lang <- c("R", "JAVA", "Python", "C", "Swift")[lang]
Lang_data <- data.frame(lang)
```

加载后，你可以检查创建的示例数据，如图 12-23 所示。输入源代码后，你可以看到图表没有正常绘制，如图 12-24 所示。

![](img/3c3c87d78136583581b0cf0620f5ae66_273_0.png)

图 12-23 示例数据生成完成

![](img/3c3c87d78136583581b0cf0620f5ae66_273_1.png)

图 12-24 Power BI 中的 R 脚本错误

258 机器学习：概念、工具与数据可视化

### 源代码 (12-24)

```
# dataset <- data.frame(lang)
# dataset <- unique(dataset)

seed(1)
Lang_data.tab <- table(Lang_data)
barplot(Lang_data.tab,main="",col="Blue",xlab="Language",ylab="Number")
```

然而，在图 12-25 中，你可以看到 R Studio 运行正常。

![](img/3c3c87d78136583581b0cf0620f5ae66_274_0.png)

图 12-25 R Studio

![](img/3c3c87d78136583581b0cf0620f5ae66_275_0.png)

### 图 12-26 语言数据柱图

```
# dataset <- data.frame(lang)
# dataset <- unique(dataset)

set.seed(1)
lang <- sample(x=1:5, size=100, replace=TRUE)
lang <- c("R", "JAVA", "Python", "C", "Swift")[lang]
Lang_data <- data.frame(lang)
Lang_data.tab <- table(Lang_data)
barplot(Lang_data.tab,main="",col="Blue",xlab="Language",ylab="Number")
```

在 R 脚本窗口中输入以下源代码，如图 12-26 所示。由于导入过程中数据结构变化导致的错误，让我们利用 R Studio 的源代码作为解决此问题的手段。

260 机器学习：概念、工具与数据可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_276_0.png)

你可以检查柱图是否正在正常绘制。在 R 脚本窗口中输入下方源代码，如图 12-27 所示，以绘制相对比例柱图。

执行 R 脚本后，你可以看到相对比例柱图已经创建，如图 12-28 所示。

![](img/3c3c87d78136583581b0cf0620f5ae66_276_1.png)

### 源代码 (12-28)

```
# dataset <- data.frame(lang)
# dataset <- unique(dataset)

set.seed(1)
lang <- sample(1:5, size=100, replace=TRUE)
lang <- c("R", "JAVA", "Python", "C", "Swift")[lang]
Lang_data <- data.frame(lang)
Lang_data.tab <- table(Lang_data)
Lang_data.prop <- prop.table(Lang_data)
barplot(Lang_data.prop,main="",col="Blue",xlab="Language",ylab="Number")
```

饼图用于介绍分类数据的分布。在 R 脚本窗口中输入以下源代码，如图 12-29 所示。

![](img/3c3c87d78136583581b0cf0620f5ae66_277_0.png)

图 12-29 语言数据饼图

262 机器学习：概念、工具与数据可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_278_0.png)

图 12-30 语言数据饼图

源代码 (12-30)

```
# dataset <- data.frame(lang)
# dataset <- unique(dataset)
set.seed(1)
lang <- sample(x=1:5, size=100, replace=TRUE)
lang <- c("R", "JAVA", "Python", "C", "Swift")[lang]
Lang_data <- data.frame(lang)
Lang_data.tab <- table(Lang_data)
pie(Lang_data.tab, main="Language")
```

你可以看到饼图已经创建，如图 12-30 所示。

### 12.3.3 数值双变量图

在绘制数值图之前，你需要安装一个包来导入 Galton 数据。在 R Studio 中输入以下代码，如图 12-31 所示。设置下载区域，下载将开始。下载完成后，在 R Studio 中输入以下源代码，如图 12-32 所示。你可以通过 `dim()` 函数检查数据的结构。

![](img/3c3c87d78136583581b0cf0620f5ae66_279_0.png)

图 12-31 插入 Galton 数据的包

```
install.packages("HistData")
```

![](img/3c3c87d78136583581b0cf0620f5ae66_279_1.png)

图 12-32 插入 Galton 数据的包

```
library(HistData)
data(Galton)
dim(Galton)
```

机器学习：概念、工具与数据可视化

通过在 R 脚本窗口中输入以下源代码导入 Galton 数据，如图 12-33 所示。

![](img/3c3c87d78136583581b0cf0620f5ae66_280_0.png)

### 源代码 (12-33)

```
library(HistData)
Galton_data <- data(Galton)
```

- Galton 数据

Galton (1886) 以表格形式展示了这些数据，显示了 205 对父母出生的 928 名成年子女及其父母身高的交叉表。我们视觉上平滑了双变量频率分布，显示出形成的同心类似椭圆，从而为相关性、回归和双变量正态分布奠定了基础。创建了一个包含 928 个观测值的数据框：

- parent：数值向量：父母身高（父亲和母亲的平均值）

- child：数值向量：子女身高

![](img/3c3c87d78136583581b0cf0620f5ae66_281_0.png)

图 12-34 Galton 数据导入成功

加载后，你可以检查 Galton 数据，如图 12-34 所示。在 R 脚本中输入下方源代码，如图 12-35 所示，以分析父母与子女身高之间的关系。

![](img/3c3c87d78136583581b0cf0620f5ae66_281_1.png)

图 12-35 父母与子女身高之间的关系

266 机器学习：概念、工具与数据可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_282_0.png)

图 12-36 父母与子女身高之间的关系

### 源代码 (12-36)

```
# dataset <- data.frame(child, parent)
# dataset <- unique(dataset)

plot(child ~ parent, data = dataset, pch = 19, main = "The relationship between the parent and child height")
```

图 12-36 间接显示存在相关性。让我们通过线性回归线来确保存在相关性。

![](img/3c3c87d78136583581b0cf0620f5ae66_283_0.png)

图 12-37 父母与子女身高之间的回归线

![](img/3c3c87d78136583581b0cf0620f5ae66_283_1.png)

图 12-38 父母与子女的回归线

在 R 脚本窗口中输入下方源代码，如图 12-37 所示，以绘制线性回归线。

图 12-38 的结果确认了正相关性。

### 源代码 (12-38)

```
# dataset <- data.frame(child, parent)
# dataset <- unique(dataset)

plot(child ~ parent, data = dataset, pch = 19, main = "The relationship between the parent and child height")
lm.fit <- lm(child ~ parent, data = dataset)
abline(lm.fit, col = "Blue")
```

之前的图似乎没有代表所有的 928 个数据点。由于它们重叠在同一个区域，让我们对散点图进行散化。在 R 脚本窗口中输入以下源代码，如图 12-39 所示。

![](img/3c3c87d78136583581b0cf0620f5ae66_284_0.png)

图 12-39 父母子女身高的散点图

### 在 Power BI 中使用 R 进行可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_285_0.png)

图 12-40 父母与孩子身高散点图

### 来源 (12-40)

```r
# dataset <- data.frame(parent, child)
# dataset <- unique(dataset)
```

```r
plot(jitter(child, 3) ~ jitter(parent, 3), data = dataset, main = "The relationship between the parent and child height", xlab="parent", ylab="child")
```

图 12-40 显示了散点图上的点。

机器学习：概念、工具与数据可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_286_0.png)

### 来源 (12-41)

```r
# dataset <- data.frame(child, parent)
# dataset <- unique(dataset)

library(HistData)
dataset <- Galton
tab <- table(dataset)
x <- as.numeric(dimnames(tab)$parent)
y <- as.numeric(dimnames(tab)$child)
axis.grid <- expand.grid(x,y)
plot(axis.grid, tab, cex=sqrt(tab/pi), col="Blue", pch=19, main="The relationship between the parent and child height", xlab="parent", ylab="child")
```

图 12-41 显示了点的大小与其频率成正比。该图的表示方式与图 12-41 相同。它被称为气泡图。要应用气泡图，请在 R 脚本窗口中输入以下源码，如图 12-41 所示。

### 12.3.4 分类二变量图

在绘制分类二变量图之前，让我们通过导入 R Studio 提供的 Titanic（泰坦尼克号）数据来查看其结构。

### 在 Power BI 中使用 R 进行可视化 271

![](img/3c3c87d78136583581b0cf0620f5ae66_287_0.png)

图 12-42 Titanic 数据结构

### 来源 (12-42)

```r
Titanic
```

在 R Studio 中输入以下源码，如图 12-42 所示。

- Titanic 数据

Titanic 数据集提供了关于“泰坦尼克号”客轮船在该次灾难性首次航行中乘客的命运相关信息，并根据经济地位（等级）、性别、年龄和幸存情况进行了总结。

272 机器学习：概念、工具与数据可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_288_0.png)

图 12-43 Titanic 数据堆叠柱图

### 来源 (12-43)

```r
par(mfrow = c(2,1))
barplot(apply(Titanic, c(4,1), sum), col =c("Red", "Blue"), main = "Number of Survivors by Seat Class")
legend("topleft", fill = c("Red", "Blue"), c("Death", "Survive"))
spineplot(margin.table(Titanic, c(1,4)), col = c("Red", "Blue"), main = "Number of Survivors by Seat Class")
```

图 12-43 显示了根据等级划分的幸存者和死亡人数以及比例。将以下源码输入 R Studio 以实现。
