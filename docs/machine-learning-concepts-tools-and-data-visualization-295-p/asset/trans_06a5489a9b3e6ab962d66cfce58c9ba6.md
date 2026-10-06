

## 在 Power BI 中使用 R 进行可视化

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

# 机器学习：概念、工具与数据可视化

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

## 12.3.4 分类二变量图

在绘制分类二变量图之前，让我们通过导入 R Studio 提供的 Titanic（泰坦尼克号）数据来查看其结构。

## 在 Power BI 中使用 R 进行可视化 271

![](img/3c3c87d78136583581b0cf0620f5ae66_287_0.png)

图 12-42 Titanic 数据结构

### 来源 (12-42)

```r
Titanic
```

在 R Studio 中输入以下源码，如图 12-42 所示。

- Titanic 数据

Titanic 数据集提供了关于“泰坦尼克号”客轮船在该次灾难性首次航行中乘客的命运相关信息，并根据经济地位（等级）、性别、年龄和幸存情况进行了总结。

## 272 机器学习：概念、工具与数据可视化

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

![](img/3c3c87d78136583581b0cf0620f5ae66_289_0.png)

图 12-44 Titanic 数据堆叠柱图

### 来源 (12-44)

```r
par(mfrow = c(2,1))
barplot(apply(Titanic, c(4,2), sum), col = c("Red", "Blue"), main = "Number of Survivors by Sex")
legend("topright", fill = c("Red", "Blue"), c("Death", "Survive"))
spineplot(margin.table(Titanic, c(2,4)), col = c("Red", "Blue"), main = "Number of Survivors by Sex")
```

图 12-44 显示了根据性别划分的幸存者和死亡人数以及比例。将以下源码输入 R Studio 以实现。

## 274 机器学习：概念、工具与数据可视化

![](img/3c3c87d78136583581b0cf0620f5ae66_290_0.png)

图 12-45 Titanic 数据堆叠柱图

### 来源 (12-45)

```r
par(mfrow = c(2,1))
barplot(apply(Titanic, c(4,3), sum), col = c("Red", "Blue"), main = "Number Survivors by Age")
legend("topleft", fill = c("Red", "Blue"), c("Death", "Survive"))
spineplot(margin.table(Titanic, c(3,4)), col = c("Red", "Blue"), main = "Number of Survivors by Age")
```

图 12-45 显示了根据年龄划分的幸存者和死亡人数以及比例。将以下源码输入 R Studio 以实现。

## 12.4 练习题

Q1. 解释数值数据与分类数据之间的区别。

Q2. 解释单变量数据与二变量数据之间的区别。

Q3. 解释 Q 图（即分位数点图）。

