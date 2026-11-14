

### E2.1.5 任选三个应用，并使用任意三个机器学习任务对每个应用进行建模，并举例说明。

### E2.1.6 针对以下问题开发一个简单的设计（如示例所示）：

1.  天气预测
2.  医学诊断
3.  情感分类

## 自我评估问题

### E.2.2 多项选择题

给出答案并说明正确和错误选项的理由。

1.  **E2.2.1 什么是表示？**
    1.  指示所学内容被表征的方式。
    2.  指示输入被表示的方式
    3.  指示算法被表示的方式

2.  **E2.2.2 特征也被称为**
    1.  因变量
    2.  目标变量
    3.  自变量

3.  **E2.2.3 标记样本由...组成**
    1.  仅特征
    2.  特征和标签
    3.  仅标签

4.  **E2.2.4 模型选择涉及**
    1.  选择模型
    2.  选择学习算法
    3.  选择算法的自由参数

5.  **E2.2.5 验证样本是**
    1.  用于调整模型参数
    2.  用于测试模型
    3.  用于训练模型

6.  **E2.2.6 奥卡姆剃刀原则是**
    1.  倾向于完全拟合数据的复杂假设
    2.  倾向于最好地拟合数据的更简单假设
    3.  倾向于不拟合数据的更简单假设

7.  **E2.2.7 学习步骤涉及**
    1.  找到优化误差函数的参数集
    2.  找到拟合数据的模型
    3.  寻找测试数据

### E.2.3 匹配列

| # | 任务 | 匹配选项 |
|---|---|---|
| E.2.3.1 | 分类 | **A** 输出连续值 |
| E.2.3.2 | 排序 | **B** 基于可用的先前数据提前指示某事 |
| E.2.3.3 | 回归 | **C** 搜索问题的状态空间表述 |
| E.2.3.4 | 标记 | **D** 输入所属的给定类别集合中的一个 |
| E.2.3.5 | 预测建模 | **E** 判断一个实体是否在一个或多个指定的品质或特征上像另一个实体 |
| E.2.3.6 | 异常检测 | **F** 通过发现它们之间的相似性将项目分组为同质组 |
| E.2.3.7 | 维度检测 | **G** 减少数据集中的输入变量数量 |
| E.2.3.8 | 匹配 | **H** 分析一组对象或事件以发现其中任何异常或非典型的对象 |
| E.2.3.9 | 问题求解 | **I** 自动分配标签或令牌以进行识别或分析 |
| E.2.3.10 | 聚类 | **J** 将一类实体从高到低排序 |

### E.2.4 简答题

1.  **E2.4.1** 机器学习的三个重要组成部分是什么？
2.  **E2.4.2** 假设空间是什么意思？
3.  **E2.4.3** 在机器学习语境下，什么是推理？
4.  **E2.4.4** 为什么损失函数在机器学习中很重要？
5.  **E2.4.5** 分类和回归有什么区别？
6.  **E2.4.6** 分类和聚类有什么区别？
7.  **E2.4.7** 将关联规则挖掘作为一种机器学习任务进行描述。
8.  **E2.4.8** 假设输入有三个特征，给出机器学习任务设计的步骤。
9.  **E2.4.9** 为什么特征选择在机器学习中很重要？
10. **E2.4.10** 假设你有一个学生数据库。给出两个你想要学习的机器学习任务，概述每个任务所需的不同特征。

## 参考文献

*   [Google](#ch2.xhtml#R_ref2_2). (2023). 机器学习术语表。 [https://developers.google.com/machine-learning/glossary](https://developers.google.com/machine-learning/glossary)
*   [Huyen, C.](#ch2.xhtml#R_ref2_3) (2022). 设计机器学习系统。 [https://huyenchip.com/machine-learning-systems-design/design-a-machine-learning-system.html](https://huyenchip.com/machine-learning-systems-design/design-a-machine-learning-system.html)
*   [Kumar, A.](#ch2.xhtml#R_ref2_4) (2022年12月4日). 最常见的机器学习任务。数据分析。 [https://vitalflux.com/7-common-machine-learning-tasks-related-methods/](https://vitalflux.com/7-common-machine-learning-tasks-related-methods/)
*   [Mohri, M., Rostamizadeh, A., & Talwalkar, A.](#ch2.xhtml#R_ref2_5) (2012). 机器学习基础。MIT Press.
*   [Nkengsa, B.](#ch2.xhtml#R_ref2_6) (2018年10月26日). 应用机器学习识别手写字符。Medium。 [https://medium.com/the-andela-way/applying-machine-learning-to-recognize-handwritten-characters-babcd4b8d705](https://medium.com/the-andela-way/applying-machine-learning-to-recognize-handwritten-characters-babcd4b8d705)
*   [Pykes, K.](#ch2.xhtml#R_ref2_7) (2021年9月5日). 如何设计机器学习系统。Medium。 [https://medium.com/geekculture/how-to-design-a-machine-learning-system-89d806ff3d3b](https://medium.com/geekculture/how-to-design-a-machine-learning-system-89d806ff3d3b)

# 3 数学基础与机器学习

DOI: [10.1201/9781003290100-3](https://dx.doi.org/10.1201/9781003290100-3)

## 3.1 简介

在[表 3.1](#ch3.xhtml#table3_1)中，我们列出了使用数学概念的上下文。

**表 3.1 机器学习中使用的数学概念**

| 数学概念 | 机器学习中的应用 |
|---|---|
| **面向机器学习的线性代数** | 数据表示和数据预处理——输入、图像、音频、文本的属性<br>对向量和矩阵进行运算以发现数据中的模式<br>线性方程对数据建模<br>线性变换映射输入和输出<br>向量间的余弦相似度<br>特征向量、主成分和降维 |
| **面向机器学习的概率论** | 分类模型通常预测类别成员的概率。<br>许多迭代机器学习技术（如`maximum likelihood estimation (MLE)`）基于概率论。`MLE`用于`linear regression`、`logistic regression`和`artificial neural networks`等模型的训练。<br>基于`Bayes theorem`的许多机器学习框架统称为`Bayesian learning`（例如`naive Bayes`、`Bayesian networks`）。<br>学习算法使用概率做决策（例如信息增益）。<br>算法在概率框架下训练（例如最大似然）。<br>模型使用概率损失函数进行拟合（例如`log loss`和`cross entropy`）。<br>模型超参数通过概率配置（例如`Bayesian optimization`）。<br>概率度量用于评估模型技能（例如`brier score`、`receiver operator characteristic (ROC)`）。 |
| **面向机器学习的信息论** | `Entropy`是决策树学习中使用的信息增益和互信息的基础——`ID3`算法。<br>`Cross-entropy`用作衡量分类模型性能的损失函数。<br>`Kullback–Liebler (KL) divergence`度量用于深度学习。<br>`KL divergence`也用于降维技术——`t-distributed stochastic neighbour embedding (t-SNE)`。`Entropy`可用于计算目标类别不平衡。 |

表中提到的应用将在后续章节中讨论。

## 3.2 什么是线性代数？

