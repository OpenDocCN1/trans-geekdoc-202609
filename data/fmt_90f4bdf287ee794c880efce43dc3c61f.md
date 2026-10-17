
```python
#### 在批次上训练
for i in range(n_iterations):
    batch_x, batch_y = mnist.train.next_batch(batch_size)
    sess.run(train_step, feed_dict={
        X: batch_x, Y: batch_y, keep_prob: dropout
    })

    # 打印每个批次的损失和准确率
    if i % 100 == 0:
        minibatch_loss, minibatch_accuracy = sess.run(
            [cross_entropy, accuracy],
            feed_dict={X: batch_x, Y: batch_y, keep_prob: 1.0}
        )
        print(
            "Iteration {}".format(i),
            "\t Loss = {}".format(minibatch_loss),
            "\t Accuracy = {}".format(minibatch_accuracy)
        )
```

图 47。

| 迭代次数 | 损失 (Loss) | 准确率 (Accuracy) |
|---|---|---|
| 0 | 3.56325 | 0.132815 |
| 100 | 0.556247 | 0.84375 |
| 200 | 0.2929745 | 0.898475 |
| 300 | 0.2296962 | 0.9375 |
| 400 | 0.3628574 | 0.882815 |
| 500 | 0.4162858 | 0.882815 |
| 600 | 0.3385977 | 0.9140625 |
| 700 | 0.3483944 | 0.921875 |
| 800 | 0.2768194 | 0.929675 |
| 900 | 0.1626674 | 0.953125 |

图 48。

```python
test_accuracy = sess.run(accuracy, feed_dict={X: mnist.test.images, Y: mnist.test.labels, keep_prob: 1.0})
print("Accuracy on test set: %s", test_accuracy)
```

测试集准确率：0.9179

图 49。

```bash
tensorflow-cpu C:\Users\anwar\Desktop\test_img.png
```

| 总百分比 (%) | 验证百分比 (%) | 传输百分比 (%) | 平均速度 | 总耗时 | 剩余时间 | 当前 |
|---|---|---|---|---|---|---|
| 100 | 393 | 0 | 0:00:00 | 0:00:01 | 513 |

图 50。

```python
import numpy as np
from PIL import Image
img = np.array(Image.open("C:/Users/anwar/Desktop/test_img.png").convert('L'))
prediction = sess.run(tf.argmax(output_layer, 1), feed_dict={X: img})
print("Prediction for test image:", np.squeeze(prediction))
```

# TensorFlow 的优缺点

## 优点

- 它是开源库，可以免费获取。
- 它使用 TensorBoard 提供图形可视化，有助于理解模型。
- 它支持 CPU 和 GPU。
- 它拥有优秀的社区支持。
- 它提供定期更新和新功能的频繁发布。
- 可扩展性。

## 缺点

- 它不支持 Windows 操作系统（如果你是 Windows 用户，可以通过 anaconda 或 python 包库安装）。
- 运行简单的 hello world 程序需要额外的步骤；我们需要使用 session 来运行程序。
- 它仅支持 NVIDIA GPU，并且对 python 语言有完全支持。
- 它的结构独特，调试程序困难。

## 参考文献

- Abadi, M., Agarwal, A., Barham, P., Chen, Z., Citro, C., Ghemawat, S. (2016). TensorFlow: Large-scale machine learning on distributed systems. arXiv preprint arXiv:1603.0467.
- Aryan, M. (2018). How to Use TensorBoard? 于 2019年9月12日来自 https://itnext.io/how-to-use-tensorboard-5d82f08b65496
- Jason, B. (2019). What is Deep Learning? 于 2020年1月10日来自 https://machinelearning-mastery.com/what-is-deep-learning/
- LeCun, Y., Cortes, C., & Burges, C. J. (1998). The MNIST database of handwritten digits. http://yann.lecun.com/exdb/mnist
- Ramsundar, B., & Zadeh, R. B. (2018). TensorFlow for deep learning: from linear regression to reinforcement learning. O'Reilly Media, Inc.
- TensorFlow. (2016). 于 2019年9月4日来自 https://www.tensorflow.org/guide/graphs
- Zaccone, G., Karim, M., & Menshaw, A. (2017). Deep Learning with TensorFlow. Packt Publishing.

# 第 5 章

## 使用机器学习预测员工流失

Krishna Kumar Mohbey

https://orcid.org/0000-0002-7566-0703

拉拉斯坦中央大学计算机科学系

### 摘要

在任何行业中，流失都是一个大问题，无论是组织的员工流失还是电子商务网站的客户流失。如果我们能准确预测哪些客户或员工将离开目前的公司或组织，这将节省大量的时间、精力和成本，并帮助他们提前招聘替代者，从而不会对组织的持续流程产生影响。在本章中，对朴素贝叶斯、SVM、决策树、随机森林和逻辑回归等各种机器学习方法进行了对比分析。结果显示，逻辑回归方法在准确率上可以达到 86%，高于其他机器学习方法。

### 引言

如今，流失是全球行业面临的主要问题之一。它是行业最紧迫的问题之一，高流失率会导致组织出现许多方面的问题，包括人才和知识的流失、培训和招聘问题。我们，许多因素会导致员工流失，包括环境、满意度、雇主行为、时间安排以及最重要的薪资或福利。

# 使用机器学习方法进行员工流失预测

本章的目的是对用于员工流失预测的不同机器学习方法进行对比分析。在这里，我们显著增强了训练过程，以解决类别不平衡问题。

### 方法论

在本章中，使用了多种监督机器学习方法。本节提供了这些方法的通用描述。

#### 朴贝叶斯

这是一种概率方法，利用贝叶斯定理来预测类别的后验概率。它根据相关特征的先验知识计算事件的后验概率（Rane & Kumar, 2018）。公式1显示了后验概率的计算方法。

```
$P\left(\frac{Cl}{x}\right) = \frac{P(Cl|x)}{P(x)}$ (1)
```

其中，$Cl$：指定的类别

$x$:用于分类的样本

$P(Cl)$ 和 $P(x)$:先验概率

$P\left(\frac{Cl}{x}\right)$：后验概率

#### 支持向量机

这是一种用于分类和回归的非参数监督机器学习方法。它最初由 Vapnik 在1995年提出（Cortes & Vapnik, 1995）。它将新数据分配到两个可能的类别之一，定义了一个将n维数据分分为两类的超平面。

# 逻辑回归

这是一个用于将观测值分配到特定类的传统的分类方法。它通过 sigmoid 函数转换输出，返回映射到类的概率值。这是一个广泛使用的分类器，在线性可分类上表现良好（Raschka, 2015）。

#### 随机森林

它由许多决策树组成，用于训练数据（Ho, 1995）。随机森林中的每棵树输出一个类别，得票最多的类别成为模型的预测结果。它使用集成方法，对基础树结构进行了改进。

#### 决策树

这是一种在树结构中构建分类模型的监督学习方法。它通过自顶向方法生成分类规则，以确定观测值的类别。它使用剪枝方法来处理过拟合（Morgan & Sonquist, 1963）。

#### 数据集与工具

在工作中，我们使用了公开的人力数据集。该数据集是由 IBM Watson 创建的模拟数据集（McKinley Stacker, 2015）。该数据集包含年龄、性别、教育程度、最近一次晋升等标准HR特征。该数据集包含1470名员工，其中237名员工流失为“是”，1223名员工流失为“否”。所有非数值值通过 Python 中的 Scikit-learn 包进行了标签编码转换。此外，本工作使用 Python 来训练和评估各种机器学习方法。不同特征的相关性见图1的热力图。图1显示了HR数据不同特征的相关性。同时也显示了低相关特征和高相关特征。

#### 实验设计

在本节中，展示了各种机器学习方法的结果。所有方法都根据精确率、召回率和AUC（ROC曲线下面积）进行了评估。下方描述了各种性能参数（Alduay & Rajmaat, 2018; Powers, 2011）。

```
Accuracy = \frac{TP+TN}{TP+TN+FP+FN} (2)
```

```
Precision = \frac{TP}{TP+FP} (3)
```

```
Recall = \frac{TP}{TP+FN} (4)
```

```
F-measure = \frac{2*Precision*Recall}{Precision + Recall} (5)
```

# 使用机器学习方法进行员工流失预测

图1.不同特征之间的相关性

![](img/c5bbc72cd5e7b9be32079eac36d85c_144_0.png)

> $$AUC = Recall - \frac{FP}{FP+TN}+1$$ (6)

其中，TP为真阳性，TN为真阴性，FP为假阳性，FN为假阴性。表1比较了各种机器学习方法的性能，包括员工流失预测的精确率、召回率和准确率。

表1 不同方法的精确率、召回率和f1分数对比

| 方法 | 精确率 (Precision) | 召回率 (Recall) | f1分数 |
|---|---|---|---|
| 随机森林 | 0.84 | 0.85 | 0.80 |
| 朴贝叶斯 | 0.75 | 0.54 | 0.59 |
| 逻辑回归 | **0.87** | **0.86** | **0.83** |
| SVM | 0.77 | 0.41 | 0.45 |
| 决策树 | 0.79 | 0.80 | 0.79 |

表1显示，逻辑回归方法相比其他对比方法具有更高的f1分数。图1显示了不同机器学习方法的准确率。可以得出，逻辑回归方法在HR数据集上的准确率优于其他方法。另一种对比是使用AUC值进行的，如图2所示。

图2. 各种机器学习方法的准确率对比

![](img/c5bbc72cd5e7b9be32079eac36d85c_145_0.png)

## 结论

员工流失已被确定为任何组织的重大问题。高绩效和人才的流失被认为是该组织的损失。寻找替代员工是一项耗时任务。在这项工作中，我们在HR数据集上评估了各种机器学习方法。这里比较了五种不同的方法。根据准确率测量，逻辑回归在该数据集上的表现良好。它具有更高的精确率、召回率和准确率。流失预测的结果将有助于组织降低公司的流失率。

# 图3. 各种机器学习方法的AUC对比

![](img/c5bbc72cd5e7b9be32079eac36d85c_146_0.png)

## 参考文献

Ajit, P. (2016). Prediction of employee turnover in organizations using machine learning algorithms. Algorithms, 4(5), C5.

Al-Radaieh, Q. A., & Al Nagi, E. (2012). Using data mining techniques to build a classification model for predicting employees performance. International Journal of Advanced Computer Science and Applications, 3(2).

Alao, D., & Adeyemo, A. B. (2013). Analyzing employee attrition using decision tree algorithms. Computing, Information Systems, Development and Allied Research Journal, 4.

Alduay, S. S., & Rajpour, K. (2018). Predicting Employee Attrition using Machine Learning. 2018 International Conference on Innovations in Information Technology (IT), 93–98. 10.1109/INNOVATIONS.2018.8605976

Cortes, C., & Wapnik, V. (1995). Support-vector networks. Journal of Machine Learning, 2(3), 273–297.

Ho, T. K. (1995). Random forests. PhD Thesis.

Pedregosa, F., Varquaux, G., Gramfort, A., Michel, V., Thirir, B., Grisel, O., & . (2011). Scikit-learn: Machine learning in Journal of Machine Learning, 12, 2825–2830.

## 第6章

# 一种用于基因表达数据集识别癌症基因的新型深度学习方法

Pyingkodi Maran

印度 Kongu 工程学院 & 印度安纳大学

Thenmozhi K.

id https://orcid.org/0000-0000-0934-2552

印度 Selvam 技术学院

Shanthi S.

印度 Kongu 工程学院

Hemalatha D.

印度 Kongu 工程学院

Nanthini K.

印度 Kongu 工程学院

## 摘要

计算生物学是一项贡献于生物信息分析的研究领域。癌症相关基因子集的筛选是基因表达数据临床研究中最重要的任务之一。由于一个基因可以扮演多种生物通路的节点，而这些通路仅在特定的实验条件下才能激活，因此本文将堆叠去噪自动编码器（SDAE）与遗传算法相结合，对高维微阵列基因表达数据进行基因聚类。Genetic-SDAE 证明其优于近期提出的方法，并能够通过较低的 MSR（均方根和）和更高的基因方差，更好地确定一组基因表达数据簇的最大相似性。这项工作还就发现的基因对结果进行了评估，提取的簇集得到了生物学证据（如基因功能富集和生物过程）的支持。

# 一种用于基因表达数据集识别癌症基因的深度学习方法

## 引言

生物信息学是一门多学科，涉及计算机科学、数学、生物学、统计学和信息技术等领域。癌症的特征是不规则、不可控的生长，可能会破坏并导致相邻的健康人体组织。过去，医疗人员和放射科医的分类基于临床和形态特征，诊断能力有限。处理不同类型的生物数据。原始基因表达数据的维度和复杂性给数据分析数据管理带来了挑战。微阵列基因表达数据分析的根本目标是寻找基因的行为模式。

计算分子生物学处理各种生物数据。基因表达其中一种。因此，基因表达数据是本文使用的基础数据。基因表达是基因中的信息转换为可观察表型（蛋白质）的过程。它是基因在人体某些组织中活性的程度，通过组织中信使核糖酸（mRNA）的数量来衡量。单个基因可以根据细胞在特定时刻的需要和情况开启（发挥作用）或关闭。因此，基因表达的异常或偏差可能导致细胞死亡或其不受控制的生长，例如（Subramanian 2010）。

基因表达矩阵是归一化后获得的数据。矩阵中的每行对应一个特定的基因，每列对应一个实验条件或测量表达量的特定时间点（Tiвари et al. 2012）。基因在不同实验条件下的表达水平累计称为基因表达谱，而实验条件下每个水平的表达谱条件地称为样本表达谱（Androlakis et al. 2007）。一个实验条件或基因的表达谱被认为是一个向量，可以表示为 $n$ 维空间中的一个向量，其中 $n$ 是条件的数量；具有 $m$ 个基因的条件表达谱可以认为是 $m$ 维空间中的一个向量，其中 $m$ 是基因的数量。图1显示了具有 $m$ 个基因跨 $n$ 个条件的基因表达矩阵 $A$，它被视为 $m \times n$ 矩阵。该矩阵的每个元素 $a_{ij}$ 代表基因 $i$ 在特定条件 $j$ 下的表达水平，用实数表示。

## 基因表达数据

## 使用微阵列进行癌症诊断的意义
