

## 网络结构

- 一个层由一组节点组成
- 在全连接模型中，一层中的每个节点都连接到下一层的所有节点

![](img/357c1568568ec7942f9e3cf49122ebd5_30_0.png)

图片来源：towardsdatascience

## 在 Keras 的 R 接口中定义网络模型

```
model <- keras_model_sequential()
model %>%
  layer_dense(units = 256, activation = 'relu') %>%
  layer_dense(units = 128, activation = 'relu') %>%
  layer_dense(units = 10, activation = 'softmax')
```

keras.rstudio.com

## 网络结构

回顾基本神经网络模型（一层，p 个预测变量）

y = \beta_0 + \sum_{k=1}^K \beta_k \sigma_k(\alpha_{0k} + \alpha_{1k}x_1 + \alpha_{2k}x_2 + \cdots + \alpha_{3p}x_p)

激活函数

激活函数

- 计算开销低
- 深度学习成功的关键之一

## 激活函数

- **Sigmoid**

  \(\sigma(x) = \frac{1}{1+e^{-x}}\)

![](img/357c1568568ec7942f9e3cf49122ebd5_33_0.png)

- **Leaky ReLU**

  \(max(0.1x, x)\)

![](img/357c1568568ec7942f9e3cf49122ebd5_33_1.png)

- **tanh**

  \(\tanh(x)\)

![](img/357c1568568ec7942f9e3cf49122ebd5_33_2.png)

- **Maxout**

  \(max(w_1^T x + b_1, w_2^T x + b_2)\)

- **ReLU**

  \(max(0, x)\)

![](img/357c1568568ec7942f9e3cf49122ebd5_33_3.png)

- **ELU**

  \(\begin{cases} x & x \ge 0 \\ \alpha(e^x - 1) & x < 0 \end{cases}\)

![](img/357c1568568ec7942f9e3cf49122ebd5_33_4.png)

图片来源：medium.com

## 网络结构

### ReLU（修正线性单元）激活函数

\(\sigma(x) = \max(0, x) = \left\{ \begin{array}{ll} 0 & \text{for } x < 0 \\ x & \text{for } x \ge 0 \end{array} \right.\)

### Softmax 激活函数

- 用于输出层的分类问题
- 输入：\( x \in \Re \)，输出：\( 0 \le \sigma(x_i) \le 1 \)

\(\sigma(x_i) = \frac{\exp(x_i)}{\sum_{j=1}^J \exp(x_j)} \quad \text{for } i = 1, \dots, J\)

## 网络结构

### 在 Keras 的 R 接口中定义网络模型

```
model <- keras_model_sequential()
model %>%
  layer_dense(units = 256, activation = 'relu') %>%
  layer_dense(units = 128, activation = 'relu') %>%
  layer_dense(units = 10, activation = 'softmax')
```

- 序列模型：神经网络层的线性堆叠
- layer_dense：全连接层
- units：层中的节点数
- 激活函数

keras.rstudio.com

## 深度学习：模型拟合

### 回顾极大似然估计

- 模型拟合的步骤
  1. 定义网络结构
  2. 选择损失函数
  3. 选择优化器

![](img/357c1568568ec7942f9e3cf49122ebd5_36_0.png)

## 损失函数

损失函数

- 衡量网络的预测性能
- 衡量最后一层的输出与观测值的接近程度
- 必须是一个数值摘要

模型拟合的目标：

找到使损失最小化的参数值（权重）

## 损失函数

均方误差：用于连续响应数据

\(\frac{1}{n} \sum_{i=1}^n(y_i - \hat{y}_i)^2\)

交叉熵（偏差）：用于分类响应数据

\(- \sum_{i=1}^n \sum_{g=1}^G y_{ig} \log(\widehat{\pi}_{ig})\)

对于具有以下特征的问题：

- g = 1, ..., G 个类别
- \(\widehat{\pi}_{ig} = \) 观测值 i 属于第 g 个类别的预测概率

## 损失函数

选择与最终层（输出层）激活函数兼容的损失函数

| 任务 | 损失函数 | 最后一层激活函数 |
| :--- | :--- | :--- |
| 二分类 | 二元交叉熵 | Sigmoid |
| 多类，单标签分类 | 类别交叉熵 | Softmax |
| 多类，多标签分类 | 二元交叉熵 | Sigmoid |
| 回归到任意值 | 均方误差 (MSE) | 无 |
| 回归到 0 到 1 之间的值 | MSE 或二元交叉熵 | Sigmoid |

## 损失函数

在 R Keras 中，

1. 设置模型（参见上文）。
2. 使用合适的损失函数、优化器和指标编译模型。

```
model %>%
  compile(
    loss = 'categorical_crossentropy',
    optimizer = optimizer_rmsprop(),
    metrics = c('accuracy')
  )
```

R keras 中的损失函数

## 模型拟合

### 模型拟合的步骤

1. 定义网络结构
2. 选择损失函数
3. 选择优化器

## 模型拟合

### 目标：

- 找到使损失最小化的参数值（权重）
- 估计参数值 $\beta, \alpha, ...$

### 模型拟合也称为

- 计算机科学：训练模型
- 统计学：估计参数
- 数学：优化损失函数

## 模型拟合

神经网络有**许多**未知参数（权重）。

### 参数计数

- 一个节点中有 p + 1 个参数
  - p 个协变量加上截距（偏置）
  - 参数：$(\alpha_{k0}, \alpha_{k1}, ..., \alpha_{kp})$
- 每层 k = 1, ..., K 个节点加上截距：$(\beta_{g0}, ..., \beta_{gK})$
- g = 1, ..., G 层

总计 $K(p + 1) + G(K + 1)$ 个参数

## 模型拟合

示例：

- p = 100 个协变量
- K = 128 个节点/层
- G = 5 层
- 128(100 + 1) + 5(128 + 1) = 13,573 个参数

含义：

- 参数众多，且
- 所有参数高度相关。
- 因此，你需要大量数据和一种特殊的方法来估计参数。

## 优化

- 最小化损失的一般方法是使用随机梯度下降
  - 为权重分配初始值
  - 计算损失函数对每个权重的偏导数
  - 沿下降方向（梯度的反方向）迈出一步
  - 重复直到权重收敛

![](img/357c1568568ec7942f9e3cf49122ebd5_45_0.png)

## 优化

### 深度学习优化

- 这是对优化的简要概述。
- Goodfellow 等人编写的《Deep Learning》一书中有很好的概述
- Keras 中的优化器：SGD, RMSprop, Adagrad, Adadelta, Adam, Adamax, Nadam
- 优化器概述

## 优化：综合所有内容（2 层网络）

- 输入 X
- 权重
- 层数据变换
- 权重
- 层数据变换
- 权重更新
- 预测值 Y'
- 真实目标 Y
- 优化器
- 损失函数
- 损失分数

## 深度学习：实践中的模型拟合

## 实践中的模型拟合

训练深度学习模型需要做出许多决策

你选择：

- 模型架构
- 损失函数
- 优化方法
- 所有这些工作原理的细节

## 实践中的模型拟合

### 需要调整的一些深度学习参数

- 隐藏层数量和单元数
- 正则化
- 迭代次数和批量大小
- 一般实践建议

## 隐藏层数量和单元数

宽度

![](img/357c1568568ec7942f9e3cf49122ebd5_51_0.png)

深度

## 隐藏层数量和单元数

### 多少层？

- 旧策略：一层足够
  - 通用逼近定理：一个隐藏层足以以任意精度表示任何函数的近似
  - 理论与实践！
- 当前建议
  - 从具有一个或两个隐藏层且包含大量单元的网络开始
  - 如果性能不佳且已调试，请尝试深度学习

## 欠拟合和过拟合

### 简单示例

![](img/357c1568568ec7942f9e3cf49122ebd5_53_0.png)

欠拟合

良好拟合/鲁棒

过拟合

图片来源：medium.com

## 欠拟合和过拟合

### 过拟合：

- 结果无法推广到训练集之外
- 解决方案：获取更多训练数据或使用正则化

### 欠拟合：

- 结果无用
- 解决方案：调整模型结构或模型拟合设置

## 正则化

<- 欠拟合

过拟合 ->

最佳拟合

测试误差

训练误差

误差

模型"复杂度"

图片来源：www.analyticsvidhya.com

