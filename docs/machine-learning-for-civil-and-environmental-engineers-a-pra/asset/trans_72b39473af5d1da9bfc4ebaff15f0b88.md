

## 4.1.1.18.1 可视化该算法

Jonas Greitemann [50] 开发了一个整洁的在线界面73 和工具74，用于展示 SVM 算法的工作原理。图 4.22 展示了该界面的两个片段。你可以先添加随机点并选择一个核函数。我展示了线性函数和 Sigmoid 函数生成的支持向量。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_132_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_132_1.png)

切换 清除点 v = 0.15 [slider] 内核: Linear [dropdown] gamma = 1.0 c0 = 0.0 K(x, y) = x . y [ ] 高亮支持向量

切换 清除点 v = 0.15 [slider] 内核: Linear [dropdown] gamma = 1.0 c0 = 0.0 K(x, y) = x . y [ ] 高亮支持向量

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_132_2.png)

切换 清除点 v = 0.15 [slider] 内核: Sigmoid [dropdown] gamma = 1.0 c0 = 0.0 K(x, y) = tanh (gamma.x.y + c0) [ ] 高亮支持向量

图 4.22 使用 Jonas Greitemann 的界面和不同内核对 SVM 算法进行说明 [50] / 获许可使用。

73 https://jgreitemann.github.io/svm-demo. 74 https://jgreitemann.github.io/messing-with-wasm/svm-demo.

## 4.1.1.18.2 编程该算法

SVM 算法的 Python 和 R 代码如下：

### Python 软件包

```
import sklearn
from sklearn import svm
model = svm.SVC()
```

### R 软件包：

```
>install.packages ("e1071")
>library(e1071)
>svm(formula, data = NULL, ..., subset, na.action = na.omit, scale = TRUE)
```

## 4.1.1.19 TensorFlow (TF)*

TensorFlow (TF) 是一个开源且免费的、基于神经网络的模型，使用深度学习，自 2015 年起由 Google 托管（并在 2019 年进行了改版）[51]。该模型创建数据流图，描述数据如何通过一系列处理节点移动，其中每个节点表示一个数学运算，节点之间的每个连接都是一个多维数据数组（张量）[51]。

## 4.1.1.19.1 可视化 TF

在 TF 中，计算过程被描述为图。其中一个图在图 4.23 中显示。

## 4.1.1.19.2 编程该算法

使用 TF 的 Python 和 R 代码如下：

### Python 软件包

```
import tensorflow as tf
from keras.models import Sequential
tf.keras.Sequential()
```

### R 软件包：

```
>install.packages ("tensorflow")
>library(tensorflow)
>install_tensorflow()
```

## 4.1.1.20 Transformers (T)*

变换器 (T) 是由 Google Brain 引入的一种深度学习模型 [52]。变换器采用自注意力机制来识别输入数据中各部分的重要性。该机制关联单个序列的不同位置，以计算序列的表示（而不使用序列对齐的循环架构）。从某种意义上说，该机制计算特征表示的加权平均值，权重与表示对之间的相似度得分成正比。该算法主要用于与自然语言处理75 (NLP) 和计算机视觉76 相关的问题。

## 4.1.1.20.1 编程该算法

该算法的示例 Python 代码脚本如下：

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_134_0.png)

### Python 软件包（来自 PyTorch）

```
#Import required libraries
import torch
from pytorch_transformers import GPT2Tokenizer,
GPT2LMHeadModel
```

## 4.1.1.21 Vowpal Wabbit (VW)*

Vowpal Wabbit (VW) 是一个开源的快速在线交互式机器学习系统库，起始于 Yahoo，随后转移到 Microsoft [53]。VW 是一种核外算法学习器，能够处理数据流，这对于现有硬件无法支持的大型数据集非常有用。77

## 4.1.1.21.1 编程该算法

VW 算法的 Python 和 R 代码如下：

### Python 软件包

```
import vowpalwabbit
model = vowpalwabbit.Workspace(quiet=True)
```

### R 软件包

```
>install.packages ("RVowpalWabbit")
>library (RVowpalWabbit)
>vw (args, quiet=TRUE)
```

## 4.1.2 无监督学习

在本节中，我们将注意力转移到处理没有目标（响应）标签或没有目标变量的数据集的问题。我将首先介绍异常检测78 算法，然后深入聚类和降维算法。79

### 4.1.2.1 Isolation Forest (IF) 异常检测算法

孤立森林 (IF) 异常检测算法80 持有这样一种观点：与内点不同，异常值易于隔离。81 该算法具有树结构，因此隔离一个样本所需的分割次数等于路径长度。82

### 它是如何工作的？

IF 算法通过随机选择一个特征，然后任意选择一个介于同一选定特征的最大值和最小值之间的分割值，来隔离给定数据集中的观测值。该算法使用 100 棵树来启动一个随机森林，其预期异常比例为 10%，这是其开发者推荐的 [54, 55]。

### 4.1.2.1.1 可视化该算法

图 4.24 描绘了 IF 算法的可视化，其中异常是路径长度最短的树的一侧。

77 在大多数问题中可能不是问题。然而，我们不知道未来会怎样！
78 异常检测（也称为异常值检测）将数据中与正常数据相比的异常模式/偏差识别出来。
79 诚然，我没有涵盖关联规则，因为它们更适合数据挖掘而非机器学习。有关这些内容的更多信息，请访问 [86]。
80 值得注意的是，该算法有一个称为扩展孤立森林 [87] 的扩展。
81 可以这样想，异常值少且不同；因此它们易于隔离！
82 路径长度：正常性的一种度量，异常与路径较短相关。

### 4.1.2.1.2 编程该算法

IF 算法的 Python 和 R 代码脚本如下。

### Python 软件包

```
import sklearn
from sklearn.ensemble import IsolationForest
model=IsolationForest()
```

### R 软件包

```
>install.packages("solitude")
> library("solitude")
> isolationForest$new( sample_size = 256, num_trees = 100, replace = FALSE, seed = 101,nproc = NULL, respect_unordered_factors = NULL, max_depth = ceiling(log2(sample_size) ))
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_135_0.png)

图 4.24 孤立森林 (IF) 异常检测算法中的一棵树演示 [注释：最左侧异常的浅深度]。

### 4.1.2.2 Local Outlier Factor (LOF) 异常检测算法

局部异常因子 (LOF) 异常检测算法测量特定观测值相对于其邻域的密度偏差。在此机制中，算法可以将那些密度显著低于其邻域的观测值识别为异常值。当异常得分返回大于 0.5 的值时，视为异常 [54]。除上述算法外，还可以使用其他异常算法，如马氏距离 [56]。

### 它是如何工作的？

对于特定数据点，局部密度是通过估计与之相邻的数据点之间的距离来计算的。估计的距离属于 k-最近邻，并用于计算可达距离。计算所有可达距离以确定该点的局部可达密度。当点很近时，它们的距离较小，从而导致较高的密度。换句话说，较低的局部可达密度值表明最近的簇远离当前点。

### 4.1.2.2.1 可视化该算法

查看图 4.25 显示了 LOF 过程的演示，其中空心点（绿色主机外部）被标记为异常值。

### 4.1.2.2.2 编程该算法

LOF 算法的 Python 和 R 代码脚本如下。该算法也可在 DataRobot 平台中找到。

### Python 软件包

```
import sklearn
from sklearn.neighbors import LocalOutlierFactor
model = LocalOutlierFactor()
```

### R 软件包

```
>install.packages("DMwR")
>library("DMwR")
>lofactor(data, k)
```

