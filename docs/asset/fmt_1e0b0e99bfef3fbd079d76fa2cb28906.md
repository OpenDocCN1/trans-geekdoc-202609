
```
num <- c(1, 3.4, -2, -10.85) # numeric vector
char <- c("a", "hello", "280") # character vector
bool <- c(TRUE, FALSE, TRUE, FALSE, FALSE) # logical vector
print(num)
```

[1] 1.0 3.4 -2.0 -10.85

* **矩阵 (Matrix):** 矩阵是一个二维数据结构，可以使用 `matrix()` 函数创建。可以使用 `nrow` 和 `ncol` 参数定义行和列的值。然而，不需要提供两个参数，另一个维度可以通过 `length` 参数（第一个索引：最后一个索引）自动获取。![images](img/319-1.png)

* **列表 (List):** 这种数据结构与向量略有不同，之处在于它包含了不同数据类型的混合。列表使用 `list()` 函数创建。![images](img/319-2.png)

* **因子 (Factor):** 因子将分类值存储为范围在 `[1...k]` 内的整数向量（其中 `k` 是分类变量中唯一值的数量），以及一个映射到这些项目的内部字符字符串向量（原始值）。

```
data <- c('A', 'B', 'B', 'C', 'A', 'B', 'C', 'C', 'B')
fact <- factor(data)
fact
[1] A B B C A B C C B
Levels: A B C
```

```
table(fact) # 以表格格式排列参数项 fact
A B C # 唯一项目映射到频数
2 4 3
```

* **数据框 (Data frame):** 这种数据结构是列表的一种特例，其中每个组件的长度相同。数据框使用 `frame()` 函数创建。![images](img/319-4.png)

### A.1.3.3 循环

#### For 循环 (For loop)

**语法：**

```
for (variable in sequence)
{
    (loop_body)
}
```

**示例:** 打印从 1 到 3 所有整数的平方。

```
for (i in c(1:3))
{
    j = i*i
    print(j)
}
```

[1] 1

[1] 4

[1] 9

#### While 循环 (While loop)

**语法：**

```
while (condition)
{
    (loop_body)
}
```

**示例:** 打印从 1 到 3 所有整数的平方。

```
i <- 1
while(i <= 3)
{
    sqr <- i*i
    print(sqr)
    i <- i + 1
}
```

[1] 1

[1] 4

[1] 9

#### If-else 语句 (If-else statement)

**语法：**

```
if (condition 1)
{
    Statement 1
}
else if (condition 2)
{
    Statement 2
}
else
{
    Statement 4
}
```

**示例：**

```
x = 0
if (x > 0)
{
    print("positive")
} else if (x == 0)
{
    print("zero")
} else
{
    print("negative")
}
```

[1] "zero"

### A.1.3.4 编写函数

在脚本中编写函数：

**语法：**

```
function_name <- function(argument_list)
{
    (function_body)
}
```

**示例:** 计算输入数字 `n` 阶乘的函数。

```
factorial <- function(n)
{
    fact <- 1
    for(i in 1:n)
    {
        fact <- fact * i
    }
    return(fact)
}
```

运行函数（在使用 `source('script_name')` 编译脚本后）：

```
f <- factorial(6)
print(f)
```

[1] 720

### A.1.3.5 数据类型上的数学运算

* **向量 (Vectors):**

```
n <- 10
m <- 5
n + m # 加法
[1] 15
n - m # 减法
[1] 5
n * m # 乘法
[1] 50
n / m # 除法
[1] 2
```

* **矩阵 (Matrices):** ![images](img/322-2.png)![images](img/323-1.png)

### A.1.3.6 基础数据处理命令

```
data <- read.csv("auto-mpg.csv") # 从 .csv 文件上传数据
class(data) # 获取加载的数据集的类型
[1] "data.frame"
dim(data) # 获取加载的数据集的维度，即行数和列数
[1] 398 9
nrow(data) # 获取行数
[1] 398
ncol(data) # 获取列数
[1] 9
names(data) #
[1] "mpg" "cylinders" "displacement" "horsepower" "weight"
[6] "acceleration" "model.year" "origin" "car.name"
head(data, 3) # 显示前 3 行
tail(data, 3) # 显示后 3 行
```

```
View(data)
```

```
write.csv(data, "new-data.csv") # 将数据导出到 .csv 文件
```

```
summary(data) # 获取数据集的摘要
```

```
cor(data) # 寻找变量之间的相关性
```

# 1. 集中趋势度量 – 平均值、中位数、众数

# 2. 离散度度量

### 2.1 数据离散程度 – 方差、标准差

### 2.2 不同数据值的分布 – 分位数、四分位距 (IQR)

在 R 语言中，有一个函数 `summary`，它可以生成数据集属性的概括统计量。它提供了对数据集的初步理解，并能引发对数据集以及可能存在的异常的思考。我们将使用另一个诊断函数 `str`，它能够紧凑地提供数据框（data frame）的结构以及不同属性的数据类型。现在，让我们开始探索来自加利福尼亚大学欧文分校（UCI）机器学习库的 `Auto MPG 数据集`。我们将对 Auto MPG 数据集运行 `str` 和 `summary` 命令。

![images](img/326-1.png)![images](img/327-1.png)

仔细观察 `summary` 命令的输出，针对属性列出了六项度量（嗯，大多数属性都是如此）。这些是：

1. Min. – 属性的最小值
2. 1st Qu. – 第一四分位数（详细信息请参考第 2 章）
3. Median 中位数
4. Mean 平均值
5. 3rd Qu. – 第三四分位数（详细信息请参考第 2 章）
6. Max. – 属性的最大值

这些度量对数据集属性提供了相当好的理解。现在注意，属性 `car.name` 并没有显示这些值，而是显示了其他内容。这是为什么呢？它显示的是什么值？让我们尝试理解这种差异的原因。

`car.name` 属性是一个名义变量，即分类属性。正如我们在第 2 章中已经看到的，对名义变量无法进行数学或统计操作。因此，只给出了属性的唯一值以及出现的次数或频率。我们可以使用以下 R 命令获取名义属性的完整列表。

![images](img/327-2.png)![images](img/328-1.png)

接下来，让我们尝试探索任何变量在数据值上是否存在需要进行清洗的问题。正如在第 2 章中讨论的，可能存在两个主要数据问题：缺失值和离群值。

让我们首先尝试确定任何属性是否存在缺失值。让我们使用一小段 R 代码来查找数据中的某个属性是否存在缺失/不期望的值。如果存在此类问题，则返回该属性具有缺失/不期望值的行。通过检查所有属性，我们发现 `horsepower` 属性存在缺失值。

![images](img/328-2.png)

数据集中有六行的 `horsepower` 属性存在缺失值。在继续建模活动之前，我们必须修复这些行。我们很快就会处理这一点。

检测离群值最简单且有效的方法是通过属性的箱线图。在箱线图中，离群值被非常清晰地突出显示。当我们稍后使用箱线图探索属性时，将对此方面有一个清晰的视图。

让我们快速查看其他用于获取数值属性统计测量的 R 命令。

```
range(data$mpg) # 给出最小值和最大值
[1] 9.0 46.6

diff(range(data$mpg))
[1] 37.6

quantile(data$mpg)
0% 25% 50% 75% 100%
9.0 17.5 23.0 29.0 46.6

IQR(data$mpg)
[1] 11.5

mean(data$mpg)
[1] 23.51457

median(data$mpg)
[1] 23

var(data$mpg)
[1] 61.08961

sd(data$mpg)
[1] 7.815984
```

**注意：**

为了进行数据探索（以及数据可视化），可以利用 R 的 `ggplot2` 库。`ggplot2` 由 Hadley Wickham 创建，提供了一个全面的图形模块，用于创建详细且复杂的图表。

## A.2.2 用于数据探索的基础图表

要开始使用 `ggplot2` 的库函数，我们需要如下加载该库：

```
library(ggplot2)
```

现在让我们了解用于数据探索的各种图表，以及如何使用 R 代码生成它们。

### A.2.2.1 箱线图

**语法：** `boxplot(x, data, notch, varwidth, names, main)`

**用法：**

```
boxplot(iris) # Iris 是机器学习中常用的数据集，随 R 安装附带
```

```
if (condVar > someVal) {console.log("xxx")}
```
