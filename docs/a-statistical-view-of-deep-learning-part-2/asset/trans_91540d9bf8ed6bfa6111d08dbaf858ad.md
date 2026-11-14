

## 正则化与 Dropout

### Dropout

- 将模型中比例的权重随机设置为 0
- 通过更稀疏的网络防止过拟合
- Dropout rate = 设置为 0 的权重比例

## 正则化与 Dropout

```
model <- keras_model_sequential()
model %>%
layer_dense(units = 256, activation = 'relu', input_shape
layer_dropout(rate = 0.4) %>%
layer_dense(units = 128, activation = 'relu') %>%
layer_dropout(rate = 0.3) %>%
layer_dense(units = 10, activation = 'softmax')
```

Rstudio 的 keras 页面

## 正则化与 Dropout

来源：Srivastava 等人. 放弃法：防止神经网络过拟合的简单方法

![](img/357c1568568ec7942f9e3cf49122ebd5_58_0.png)

图 4：不同架构的测试误差

## 正则化

你也可以通过在损失函数中添加类似 LASSO 的惩罚来实现正则化（Tibshirani, 1996）

### 正则化

损失 + 正则化惩罚

### L1 正则化

$Loss + \lambda \sum_{i=1}^{M} |w_i|$

其中

- $w_1, \dots, w_M$ 表示所有模型权重（参数）
- $\lambda$ 是调参参数

## Epochs and Batch Size

面对大型数据集时，深度学习优化算法将数据分成子集。

### 模型拟合选项：

- 批量大小：在更新模型前处理的训练样本数量
- 时代：完整遍历数据集的次数
- 验证分割：用作每个时代验证数据的训练数据比例。

## Epochs and Batch Size

小示例：使用 `fit()` 函数训练模型 30 个时代，每批 128 张图片：

```
history <- model %>% fit(
x_train, y_train,
epochs = 30, batch_size = 128,
validation_split = 0.2
)
```

有用参考：machinelearningmastery.com

## Epoch 图

准确率
时代
训练准确率
验证准确率：轻微过拟合
验证准确率：严重过拟合

图片来源：towardsdatascience.com

## 这是你的机器学习系统？

是啊！你把数据倒进这个巨大的线性代数堆里，然后在另一边收集答案。

如果答案错了呢？

搅动这个堆，直到它们看起来正确为止。

![](img/357c1568568ec7942f9e3cf49122ebd5_63_0.png)

## 架构

网络架构：网络的整体结构

### 一般建议

- 使用你能负担得起的最大网络
- 保持每层节点数相同
- 尝试不同的层大小
- 隐藏层使用 ReLU 单元
- 为你的数据选择合适的损失函数
- 确保输出层的激活函数与损失函数匹配

## 深度学习模型类型

## 深度学习模型类型

### 架构家族：

- 1. 深度前馈网络：我们迄今所涵盖的内容
- 2. 卷积网络
- 3. 循环和递归网络
- 4. 生成对抗网络
- 5. 贝叶斯网络
- 6. 总有新方法涌现

## 深度学习模型类型

### 卷积网络

- 用于图像等网格状数据
- 数据需要以某种方式相关（我认为）
- 每一层使用内核而不是整个图像来检测边缘等小型、有意义的特征
- 稀疏连接

## 深度学习模型类型

### 卷积边缘检测

![](img/357c1568568ec7942f9e3cf49122ebd5_68_0.png)

输入

| 1 | -1 |
|---|---|

内核

![](img/357c1568568ec7942f9e3cf49122ebd5_68_1.png)

输出

## 卷积网络

图像：Deep Learning，图 1.2

![](img/357c1568568ec7942f9e3cf49122ebd5_69_0.png)

输出（对象身份）

汽车

人

动物

第 3 个隐藏层（对象部分）

第 2 个隐藏层（角和轮廓）

第 1 个隐藏层（边缘）

可见层（输入像素）

## 深度学习模型类型

### 循环和递归网络

- 用于处理序列数据
- 示例：时间序列、金融数据、文本、语音

### 生成对抗网络

- 两个神经网络竞争生成与旧数据相似的新数据
- 用于图像生成、视频生成和语音生成

## 深度学习模型类型

### 贝叶斯网络

- 可以是上述任何一种（例如，贝叶斯卷积网络）
- 优点：估计不确定性
- 缺点：计算速度慢
- 变分贝叶斯是当前的推断方法
- 当前方法相当粗糙

## 生态学中深度学习的统计视角

### 第 1 部分：简介

- 机器学习简介
- 深度学习简介

### 第 2 部分：深入探讨

- 从 3 个视角看神经网络
- 深度学习的数学
- 模型拟合
- 深度学习模型类型

### 第 3 部分：深度学习实践

- 深度学习伦理
- 生态学中的深度学习

## 深度学习的一些有用参考

- I. Goodfellow, Y. Bengio 和 A. Courville 著《深度学习》（2016）MIT Press
- F. Chollet 和 J.J. Allaire 著《使用 R 进行深度学习》（2018）Manning Publications
- 第 1-3 章可在线阅读
- 重点是 Keras

## 用于开发此演示文稿的其他参考资料

### 书籍：

- *计算统计学*
  Givens 和 Hoeting 著（第 2 版，Wiley）
- *统计学习方法*
  Hastie, Tibshirani, 和 Friedman 著
- *统计学习导论*
  James, Witten, Hastie, Tibshirani 著

课程材料由：
Ian Goodfellow, Darren Homrighausen, Ander Wilson, Asa Ben-Hur 提供

## 感谢

- ISEC2020 组织者，尤其是 David Warton 和 Gordana Popovic
- 课程助教：Tess Hamzeh, Winston Hilton, Rachael Krawczyk
- Alison Ketz 和 Dan Walsh

## 资助支持致谢

本材料基于国家科学基金会（NSF）在拨款编号 AGS-1419558 下、美国地质调查局（USGS）（G17AC00409）以及科罗拉多州立大学（CSU）支持的工作而编写。本材料中表达的任何意见、发现、结论或建议均为作者的观点，不一定反映 NSF、USGS 或 CSU 的观点。

