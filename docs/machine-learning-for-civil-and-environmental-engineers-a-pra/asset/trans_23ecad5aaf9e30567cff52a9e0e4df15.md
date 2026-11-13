

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_111_0.png)

### (a) 第一步：手写数字一

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_111_1.png)

### (b) 第一卷积层演示

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_112_0.png)

### (c) 第二卷积层演示

图 4.8（续）CNN 工作原理图解 [14] / 经 Springer Nature 授权使用。

我将展示以下关于我手写数字一的示意图。如您所见，该工具展示了得出对“一”的首次推测和对“九”的第二次推测的每个过程。

DL 下的最终可视化工具是由 Andreas Madsen [15] 创建的。如您所见，图 4.9 为基于文本数据的自动补全任务创建了一个整洁的 RNN 可视化 33。该工具展示了梯度消失问题，即早期步骤的贡献在高级步骤中变得微不足道（即，从早期文本输入到后续输入）。

## 4.1.1.4.2 编程 CNN 和 RNN

使用 TensorFlow 深度学习库进行典型深度学习的 Python 和 R 代码如下：

### Python 包

```
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense
model = Sequential()
model.add(Dense(12, input_shape=(8,), activation='relu'))
model.add(Dense(8, activation='relu'))
model.add(Dense(1, activation='sigmoid'))
```

### R 包：

```
library(keras)
install_tensorflow()
```

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_113_0.png)

自动补全：一种具有可由人类解释的输出的应用程序，同时依赖于对短期和长期上下文的理解。在此示例中，网络使用过去的信息，并理解下一个词应该是一个国家。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_113_1.png)

梯度消失：早期步骤的贡献在香草 RNN 单元的梯度中变得微不足道。

图 4.9 RNN 演示（来自 [15]）。

典型 CNN 和 RNN 的 Python 和 R 代码如下：

### CNN Python 包

```
import tensorflow as tf
from keras.models import Sequential
from keras.layers import convolutional
from convolutional import Conv2D
model = Sequential()
model.add(Conv2D)
```

### CNN R 包：

```
>install.packages("keras")
>library(keras)
>k_convNd(x, kernel, strides = c(1, 1, 1),
padding = "valid", data_format = NULL,
 dilation_rate = c(1, 1, 1)
 )
 N=[1, 2, 3] for 1D/2D/3D convolutional
```

### RNN Python 包

```
import tensorflow as tf
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense, Dropout, LSTM #We are using an LSTM variant here
```

### RNN R 包：

```
install.packages('rnn')
```

## 4.1.1.5 生成对抗网络（GAN）

生成对抗网络（GAN）是一种现代算法架构，它让两个神经网络相互对抗 34，以生成新的但合成的观测值，这些观测值可以冒充真实数据。GAN 由 Ian Goodfellow 等人 [16] 提出。

### GAN 如何工作？

GANs 使用两个神经网络，将识别数据结构的非监督问题重新表述为监督问题。第一个网络称为生成器，它生成我们观测值的新示例。这些新的合成观测值被传递给第二个神经网络，以说服它这些是真实的观测值。但是，判别器（第二个网络）将此类数据分类为真实或虚假。两个网络都在零和博弈中进行训练，直到判别器模型大约有一半的时间被骗过。35

## 4.1.1.5.1 可视化 GLM 和 GAM

佐治亚理工学院 Polo Club 为 GAN 创建了一个出色的可视化 36 工具 [17, 18]。图 4.10 是基于我亲手绘制的简单形状的 GAN 示意图。37 如您所见，GAN 需要超过 7000 个 epoch 38 才能复制该图画。

## 4.1.1.6 广义模型（GM）

本节将介绍两种广义 39 模型（GM），即广义线性模型（GLM）和广义可加模型（GAM）。为了完整性，我们将两者与传统线性回归进行比较。

GLM 由 John Nelder 和 Robert Wedderburn 于 1972 年提出，通过最大化对数似然来拟合传统线性模型 [19]。该算法是线性模型的扩展，因此速度快、可解释且高效。在 GLM 中，响应（或目标）的分布可以是明确的非正态分布，也可以是非连续的（分类）。该响应是通过连接函数关联的特征的线性组合得出的。40 GLM 有多种变体，例如泊松广义线性模型（PGLM）、负二项广义线性模型（NBGLM）、广义线性混合模型（GLMM）等。

GLM 的一种特例是广义可加模型（GAM）。GAM 由 Trevor Hastie 和 Robert Tibshirani 于 1986 年创建 [20]。GAM 旨在通过用平滑函数定义模型来最小化目标的预测误差，以

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_115_0.png)

### (a) 选择自己绘制并画出一个形状

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_115_1.png)

（续）

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_116_0.png)

### (b) GAN 中的处理

**图 4.10（续）** GAN 示意图 [17] / 经 GitHub, Inc. 授权使用。

取代特征的参数关系。GAM 还通过允许特征非线性函数的可加性和交互 41 来推广线性模型。

### GLM 和 GAM 如何工作？

在 GLM 中，一种现象的结果类别（Y）被假设为系数（$\beta$）和特征（$x_1$, ..., $x_n$）的线性组合 42——参见公式 4.11。GLM 由三个组件组成：连接函数 g、43 系统性组件 44 和响应的概率分布（也称为随机组件）。

```
Y = \beta_0 + \beta_1 x_{1,i} + ... + \beta_n x_{n,i}
```

另一方面，GAM 的方程与 GLM 相似，但用更灵活的函数形式替代了线性项，如公式 4.12 所示。

```
Y = \beta_0 + f_1(x_1) + f_2(x_2) + ... + f_p(x_p)
```

为完整起见，线性回归公式在公式 4.13 中给出——请注意误差项的存在。

```
Y = \beta_0 + \beta_1 x_1 + ... + \beta_p x_p + \epsilon
```

41 具有交互作用的 GAM -> GA2M！

42 如果您想知道 GLM 与简单（或多元）线性回归有何不同，这是一个非常好的问题！以下是对此问题的解答。GLM 适用于响应的各种分布（即非正态分布），且不必是连续的，即它可以是二项分布、多项分布或有序多项分布。GLM 还通过连接函数关联的特征的线性组合来预测响应（例如，将非线性关系映射为线性关系的函数）。线性回归假设响应与特征之间存在线性关系，而 GLM 则不假设。

43 g 是连接函数，它定义目标的期望值（E(Y)）与其特征的线性预测值之间的关系。

44 指的是特征的线性组合。g(E[y] = \beta_0 + \beta_1 x_{1,i} + ... + \beta_n x_{n,i})，其中红色、绿色和蓝色着色方案分别代表连接函数、随机组件和系统性组件。

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_117_0.png)

### 图 4.11 将线性回归、GLM 和 GAM 拟合到同一组假设数据的示意图。

## 4.1.1.6.1 可视化 GLM 和 GAM

观察图 4.11，可以一窥将线性回归、GLM 和 GAM 模型拟合到同一数据集的对比。希望您能欣赏到 GLM 可能比 GAM 更平滑（这通过比较公式 4.11 和 4.12 可以清楚地看出。

## 4.1.1.6.2 编程该算法

GLM 算法的 Python 和 R 代码如下：

### Python 包

```
#For GLM
from statsmodels.formula.api import glm
Model=glm()
```

```
#For GAM
from pygam import GAM, s, te
```

或者，

```
from pygam import LinearGAM
```

### R 包

```
#For GLM
>install.packages("stats")
>library("stats")
>glm(formula, family = gaussian, data, weights, subset, na.action, start = NULL,
etastart, mustart, offset, control = list(...), model = TRUE, method = "glm.fit", x =
FALSE, y = TRUE, singular.ok = TRUE, contrasts = NULL, ...)
```

```
#For GAM
library(mgcv)
gam_y <- gam(y ~ s(x), method = "REML")
```

## 4.1.1.7 遗传算法（GA）

遗传算法（GA）是一种基于种群的元启发式 45 算法，模仿了 John Holland [21] 引入的达尔文适者生存的进化原理。

