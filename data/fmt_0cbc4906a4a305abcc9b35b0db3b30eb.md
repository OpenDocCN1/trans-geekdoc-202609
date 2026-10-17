
| 12 | 该数据集包含胸 X 光图像 | Kaggle | https://www.kaggle.com/datasets/h0537cd3666/heart1024?select=00675dc |

| 13 | 该数据集包含胸 X 光图像 | Kaggle | https://www.kaggle.com/datasets/h0537cd3666/heart1024?select=00675dc |

| 14 | 该数据集包含胸 X 光图像 | Kaggle | https://www.kaggle.com/datasets/h0537cd3666/heart1024?select=00675dc |

| 15 | 该数据集包含胸 X 光图像 | Kaggle | https://www.kaggle.com/datasets/h0537cd3666/heart1024?select=00675dc |

| 16 | 该数据集包含胸 X 光图像 | Kaggle | https://www.kaggle.com/datasets/h0537cd3666/heart1024?select=00675dc |

| 17 | 该数据集包含胸 X 光图像 | Kaggle | https://www.kaggle.com/datasets/h0537cd3666/heart1024?select=00675dc |

# 机器学习在知识挖掘中的进展

- 6. 指定产品类别并激活使用机制，设计同步模型。

```
model.add(Dense(25, activation='relu', kernel_initializer='uniform', input_dim=inputs))
model.add(Dense(1, activation='sigmoid'))
```

- 7. 通过引入要使用的参数（包括梯度下降）组装系统。构建 `(loss="binary crossentropy", optimizer="adam", metrics="precision")`。

- 8. 返回模型。

## 5.7.2 R 语言

- 1. 可以 `neuralnet` 包来简化安装 `packages("neuralnet")`。

- 2. 此外，使用 `library` 加载包：`library("neuralnet")`。

- 3. 使用 `data.csv` 加载 CSV 文件。

- 4. 预览数据集以供使用：`View()`。

- 5. 使用 ID 变量 `str()` 容量来验证开发。

- 6. 使用 `scale(Any var[1:12])` 变量将数据块缩放至相似的大小。

- 7. 生成随机种子集合：`seed(200)`。

- 8. 将数据集划分为 70-30 的训练集和测试集：

  - `ind <- sample(2, nrow(Any), replace=TRUE, prob=c(0.7, 0.3))`

  - `Any var[ind 14:141], train.data`

  - `Any var[ind 142:142], test.data`

- 9. 提供神经连接，具有一个隐藏层、两个中心，并将直接输出设为 `false`。

- 10. 创建摘要。

- 11. 创建绘制神经网络 (`nn`) 的图表。

```
neuralnet(formula = FSTAT + AGE + SEX + CPK + SHO + CHF + MIORD - MITYYPE + YEAR + YRGRP + LENSTAY + DSTAT + LENFOL, data=train.data, hidden=2, errtol="ce", linear.output=FALSE)
```

## 5.7.3 MATLAB

- 1. 满足数据存储路径 (`path`)。

- 2. 使用 `ImageDatastore` 将数据加载为 `ImageDatastore(path)`。

- 3. 可使用 `ImageDatastore.imshow` 显示数据集数据 (`()`)。

- 4. 将数据集中的每个标签划分到训练集和测试集中 (`()`)。

- 5. 详细描述神经网络模型。通过使用参数 `[imageInputLayer(dimension), convolution2dLayer(dimension), reluLayer, maxPooling2dLayer(stride dimension), fullyConnectedLayer(10), softmaxLayer, classificationLayer]`，可以创建一个卷积神经网络。

- 6. 按需设置训练选项：`trainingOptions(optimization technique, maximum no. of epochs, initial learning rate)`。

## 使用深度学习模型进行心血管疾病诊断

- 7. 准备模型：`trainNetwork(traindata, layers, options)`。

- 8. 执行预测：`categorise()`。

- 9. 计算精度。

## 5.7.4 JULIA

- 1. 使用数据集名 `traindata()` 和数据集名 `-testdata` 加载训练和测试数据 (`()`)。

- 2. 通过解挤压 (`traindata,layerno`) 和 (`testdata,layerno`) 添加通道层。

- 3. 使用 `onehotbatch(traindata, 0:9)` 和 `onehotbatch(testdata,0:9)` 对标签编码。

- 4. 使用 `DataLoader(traindata, batchsize=14)` 创建数据集。

- 5. 使用函数 `chain(Conv(dimension), pad14, stride14, activation function)` 构建 CNN。

- 6. 可以使用 `maxpooling()` 方法执行最大池化，而 `GlobalMeanPool` 可用于执行平均池化 (`()`)。

- 7. `Crossentropy(model(x))` 产生二元交叉熵损失。

- 8. `Adam` 提供 Adam 优化器，`Descent(learning rate)` 提供梯度下降优化器。

- 9. 我们使用 `@epochs` 训练轮数来训练模型。`Flux(loss, b, w, train data, opt)`，其中 `b` 是偏置，`w` 是权重，`opt` 是所使用的优化器。

- 10. 确定准确率。

## 5.7.5 WOLFRAM

- 1. 加载数据：`EntityPrefetch[EntityProperty["Tag", "Tag"]]; dataName = DeleteMissing@EntityValue[EntityList["Header"], EntityProperty["Tag", "Tag"]];`。

- 2. 嵌套 `BatchNormLayer` 和修改后的激活单元 (`ReLU`) 的反卷积层链。

```
创建一个反卷积平面
DeconvolutionBlock = Functions [{numhiddens, size},
  NetChain([{DeconvolutionLayer [numhiddens, 5, 5}],
  "Step"-> {2, 2}, PaddingSize-> 1],
  PartLayer [{All, 1 ;; size, 1 ;; size}],
  BatchNormLayer [], Ramp]];
为生成器生成功率
Generator = NetChain [{512, 4, 4},
  BatchNormLayer [], Ramp],
  DeconvolutionBlock[256, 8],
  DeconvolutionBlock[128, 16],
  DeconvolutionBlock[64, 32],
  DeconvolutionLayer [3, {5, 5}],
  "step"-> {2, 2}, PaddingSize-> 1 "Load"-> 0),
  PartLayer [{All, 1 ;; 64, 1 ;; 64}]];
```

```
ElementwiseLayer [Tanh #] * 0.5 + .5], "Input"-> 32, "Yield"NetDecoder ["Image"]
```

- 3. 对于判别器，嵌套带破坏性 `ReLU` 的 `BatchNormalizationLayer` 和 `ConvolutionLayer` 链。

```
创建一个卷积块
convolutionBlock = Functions [[numhiddens, size],
  NetChain [[ConvolutionLayer [numhiddens, {5, 5}],
  "step"-> {2, 2}, PaddingSize->2],
  BatchNormalizationLayer []],
  ElementwiseLayer [Max # 1, 0.2 # 1]];
```

```
创建判别能力
Discriminator = NetChain
{{ElementwiseLayer -1 + 2 * #&},
Convolution block [64, 32],
ConvolutionBlock [128,],
convolutionBlock [256, 8],
convolutionBlock [512, 4]],
```

```
LinearLayer [[Sigmoid, "Input"-> 32, "trend"Encoder ["image", {64, 64}], "load"-> 0],
```

- 5. 判别器部分。生成器部分将数据复制到图像。

- 6. 获取结果：`newData = generator`。

- 7. 训练判别器部分。

## 5.8 未来挑战

- 梯度消失

- 梯度爆炸

- 过拟合问题

- 资源

- 训练时间

## 5.9 结论

本节讨论了若干模型的意义，以及 CNN、LSTM 和 GAN 的应用。最后，对关键挑战进行了总结。

## 参考文献

- 1. G. Guo, S. Dong, K. Wang, W. Zhu, S. Cao, and H. Zhang, "心血管", IEEE Transactions on Biomedical Engineering, 65, 9, pp. 1924–1934, Sept.

- 2. A. Pathak, K. Manda, and G. Saha, "基于集成学习的心声图动脉硬硬化检测", IEEE Journal of Biomedical and Health Informatics, 26, 6, pp. 2804–2813.

- 3. J-M. Kwon, Y. Lee, S. Lee, and J. Park, "基于深度学习的算法", Journal of American Association, 7, 13.

- 4. B. Jin, C. Che, Z. Liu, S. Zhang, X. Yin, and Y. Xue, "使用 EHR 数据数据预测心衰风险", IEEE Access, 6, pp. 9256–9261, 2018.

- 5. C. Zotti, Z. Luo, A. Lalande, and P-M. Jodin, "结合形状先验的心脏分割卷积神经网络", IEEE Journal of Biomedical and Health Informatics, 23, 3, pp. 1119–1128, 2019.

- 6. G. Simantis and G. Zirititas, "结合领域约束的扩张卷积心脏 MRI 分割", IEEE Journal of Selected Topics in Signal Processing, 14, 6, pp. 1235–1243, Oct. 2020.

- 7. W. Zhang, G. Yao, B. Yang, W. Zheng, and C. Liu, "使用时空 LSTM 预测心动运动", IEEE Signal Letters, 29, pp. 787–791.

- 8. Z.-Z. Zou, K. Xie, Y.-F. Zhao, J. Wan, L. Can, and C. Wen, "基于 GAN 和 LSTM 模型的冠脉干预智能评估", IEEE Access, 8, pp. 90640–90651, 2020.

- 12. H. Mayer, F. Gomez, D. Wierstra, I. Nagy, A. Knoll and J. Schmidhuber, "A System for Robotic Heart Surgery that Learns to Tie Knots Using Recurrent Neural Networks," in 2006 IEEE/RSJ International Conference on Intelligent Robots and Systems, pp. 543–548.

- 13. H. Shin, S. Sun, J. Lee and H. C. Kim, "Complementary Photoplethysmogram Synthesis From Electrocardiogram Using Generative Adversarial Network," in IEEE Access, vol. 9, pp. 7039–7064, 2021.

- 14. A. N. Gu, M. H. Jafari, C. Luong, T. Tsang and P. Abolmaesumi, "Echocardiogram View Conversion using Clinically Constrained Conditional GAN," in 2021 IEEE 18th International Symposium on Biomedical Imaging (ISBI), 2021, pp. 96–99.

- 15. F. Cao, A. Budhotha, H. Chen and K. S. Rajput, "Feature matching ECG generative network for arrhythmia event augmentation," in 2020 42nd Annual International Conference of the IEEE Engineering in Medicine & Biology Society (EMBC), 2020, pp. 296–299.

- 16. J. Chen, G. Yang, H. Khan, Y. Zhang, S. Zhao, R. Mohiaddi, "JAS-GAN: Generative Adversarial Network Based on Unbalanced Aerial Targets," in IEEE Journal of Biomedical and Health Informatics, vol. 26, no. 1, 2022.

- 17. Z. Lou, W. Huo, K. Le and X. Tian, "Whole Heart Segmentation of Cardiac CT Images Using U-Net Based GAN," in 2020 13th International Congress on Image and Signal Processing, Bio Medical Engineering and Informatics (CISP-BMEI), 2020, pp. 192–196.

# 基于机器学习方法的精神分裂症诊断的计算分析

M Indira, K Rajeswari and J Jaivarsini Johnson

## 6.1 引言

许多生物和环境因素与遗传特征相互作用，决定了一个人是更容易产生心理问题，还是对这些问题更具韧性[1]。精神分裂症和大多数精神疾病表现于那些无法应对压力且在压力下表现不佳的敏感个体[2]。多个系统（神经营养因子、氧化应激、代谢标志物、下丘脑垂体-肾上腺轴 (HPA)、自主神经系统、神经递质和免疫系统）参与了韧性的调节。这些系统作为一个整体运作，帮助人们从创伤事件和其他类型的压力中恢复，并在暴露于破坏稳态的压力后成功适应环境[3, 4]。理解韧性可能有助于理解精神分裂症中不同的现实情况[4]。HPA 轴在应对压力时表现出活性增加（即皮质醇和促肾上腺质激素 CRH、肾上腺皮质激素 ACTH 的产生均升高），是管理焦虑的关键机制之一[5, 6]。HPA 轴是自动运行的，并具有负反馈机制来降低其活性。当整体对负面事件或逆境做出反应时，HPA 轴会恢复到"标准"活性或平衡状态[5, 6]。

### 6.1.1 精神分裂症

精神分裂症患者对现实的感知是扭曲的，这些可能是错误的。妄想、高度不理性的思维和行为以及幻觉是精神分裂症的一些症状，它们可能使人瘫痪并难以完成日常生活。精神疾病患者需要持续的帮助。

### 6.1.2 症状

情绪、行为和心理过程（认知）的广泛问题是精神分裂症的特征。有许多不同的预警信号和症状，其中言语模糊、视力模糊、幻觉和能力下降通常是常见的。迹象可能包括：

- 妄想：这些是没有事实依据的错误观念。某些患者可能会感到恐惧或痛苦、成为特定行为或言论的目标、拥有名声或技能、处于恋爱关系中，或处于严重紧急情况的危险中。精神分裂症患者有许多妄想。

- 幻觉：看到或听到虚幻的事是常见现象。然而，对于遭受精神分裂症的患者来说，典型的经历保留了其所有的强度和意义。尽管可以以任何其他形式出现，但听到的声音是最常见的幻觉类型。

- 散漫思维（言语）：言语混乱是心理不稳定的标志。如果对问题的回答完全或部分不相关，对话可能会变得困难。偶尔说话不连贯的技术被称为"词语垃圾"。

- 极度不系统或异常的运动行为：这可能以多种方式表现，从简单的无知到不理性的烦躁。由于缺乏以目标为中心的行为，任务难以完成。拒绝遵循指南、奇怪的体态、无作为或过度的剧烈活动都是行为的例子。
