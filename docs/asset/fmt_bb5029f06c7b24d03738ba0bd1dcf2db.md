
这两种方法的主要区别在于：在静态反向传播中，映射是快速的；而在循环反向传播中，映射是非静态的。

### 优点

反向传播网络的优点如下：

*   简单、快速且易于编程。
*   除了输入的数量外，没有需要调整的参数。
*   它是一种通常效果良好的标准方法。
*   它是一种通用的方法，因为它不需要网络的先验知识。

### 缺点

反向传播网络的缺点如下：

*   实际性能由数据输入决定。
*   反向传播对噪声数据极其敏感。
*   反向传播必须使用基于矩阵的方法，而不是小批量方法。

## 深度学习简介

深度学习算法采用一种称为神经网络的技术来发现一组输入和输出之间的关系。

机器学习有一个子领域称为**深度学习**。深度学习算法可以利用加速的计算能力和大型数据集，自我学习数据中的隐藏模式以进行预测。本质上，深度学习是机器学习的一个子集（见图 6.12），它在大量数据上进行训练，并涉及许多计算单元协同工作以进行预测。

该术语指的是创建深度神经网络。这指的是一个具有许多层的神经网络。通过增加更多的权重和偏置，神经网络提高了预测更复杂函数的能力。

深度学习是机器学习的一个子集，而机器学习是人工智能的一个子集。各自的定义如下：

*   **人工智能：** 人工智能的广泛使命是创造能够智能思考的机器。
*   **机器学习：** 机器学习采用算法从数据中提取洞见。
*   **深度学习：** 深度学习采用一种称为神经网络的特定算法。

### 深度学习算法如何“学习”？

下图 6.12 描绘了深度学习算法的概念：

![](img/image-0ebwx50y.jpg)

**图 6.12：深度学习算法概念**

神经网络由输入层、隐藏层和输出层组成，所有这些层都由神经元构成。输入层接收数据的数值表示（例如，带有像素规格的图像），输出层产生预测，而隐藏层与大部分计算相关联。

### 机器学习与深度学习的区别

要理解机器学习和深度学习的区别，我们首先必须了解深度学习和机器学习之间的关系。图 6.13 中的示例最好地诠释了这种关系。在机器学习中，特征提取和分类是分别应用以获得输出的；而在深度学习中，特征提取和分类是一起应用以获得输出的。通过使用深度学习，复杂性降低，从而能更快地获得结果。

![](img/image-mrime246.jpg)

**图 6.13：机器学习 vs 深度学习**

下表 6.2 显示了机器学习和深度学习的区别。

**表 6.2：机器学习和深度学习的区别**

*（注：原文包含大量重复的占位符文本 "Learning." 而非实际表格内容。此处已标注，但保留了表头结构。）*

### 深度学习的重要性

深度学习之所以重要，是因为我们在关键任务上实现了有意义且实用的准确率。几十年来，机器学习一直用于图像和文本分类，但一直难以跨越算法在商业环境中工作所需的准确率门槛。正如图 6.14 所示，深度学习终于让我们在以前无法做到的地方跨越了这条线。

![](img/image-79gp13dv.jpg)

**图 6.14：深度学习与旧式学习算法的比较**

以下是一些实时案例：

*   **计算机视觉**是深度学习使其成为商业应用可行任务的绝佳例子。深度学习在图像分类和标记方面不仅优于任何其他传统算法；它也开始超越实际人类。
*   Facebook 已利用深度学习在识别照片中的面部表情方面取得了显著成功。这不仅仅是微小的改进；这是一个巨大的成功。
*   Google 已经在使用深度学习来管理公司数据中心的能源。深度学习也对语音识别产生了影响。
*   深度学习之所以重要，是因为它将以前无法触及的工作负载纳入了机器学习的范畴。我们才刚刚开始理解开发人员和业务领导者如何利用机器学习推动业务成果，而由于深度学习，更多可用任务触手可及，这将在未来几十年改变经济。

#### 优点

*   同类最佳性能
*   减少对特征工程的需求
*   削减不必要的开支
*   识别细微缺陷

#### 缺点

*   需要海量数据
*   训练计算成本高昂
*   缺乏坚实的理论基础

## 深度学习的应用

深度学习在几乎所有行业都有广泛的应用，包括医疗保健、金融和图像识别。一些最热门的应用领域如下：

*   **健康医疗**：图像识别、通过 MRI 成像和 X 光进行癌症检测、药物发现、临床试验匹配和基因组学。
*   **自主系统**：自动驾驶汽车，从识别停车标志到发现道路上的行人。
*   **产品推荐**。
*   **自动文本**：逐词或逐字符生成。
*   **自动机器翻译**：将一种语言中的特定单词、句子或短语转换为另一种语言。
*   **个人设备**：如 Alexa 或 Google Assistant。
*   **预测**：教会计算机执行粘弹性计算，用于地震预测。

这些只是深度学习可应用的众多应用中的一小部分。股市预测和天气预报是深度学习已被证明有用的另外两个热门领域。

## 总结

*   **推荐系统** 是为用户提供可能有用的项目推荐的软件工具和技术。
*   推荐方法主要有三种：**基于内容的推荐系统**、**协同过滤** 和 **混合推荐系统**。
*   **协同过滤** 除用户对一组项目的历史偏好外，不需要任何其他信息。
*   **协同过滤** 技术大致分为两类：**基于内存的方法** 和 **基于模型的方法**。
*   采用 **基于内容的推荐** 方法的系统会调查一组文档和/或用户之前评分过的项目的解释，并根据该用户评分对象的特征，建立该用户兴趣的模型或画像。
*   **人工神经网络 (ANN)** 是受生物学启发的计算机模拟，可执行聚类、分类和模式识别等特定任务。
*   **感知机** 是一种用于二分类器的监督学习算法。
*   感知机有两种类型：**单层** 和 **多层**。
*   **反向传播算法** 利用一种称为 **链式法则** 的方法，用于有效地训练神经网络。
*   **反向传播** 对于在易错项目（如图像或语音识别）上工作的深度神经网络特别有用。
*   **深度学习** 指的是 **深度神经网络**。
*   反向传播网络有两种类型：**静态反向传播** 和 **循环反向传播**。
*   **深度学习** 算法采用一种称为 **神经网络** 的技术，来发现一组输入和输出之间的关系。

## 练习 (单选题)

**反向传播算法的目标是什么？**

*   开发一种用于多层前馈神经网络的学习算法
*   开发一种用于单层前馈神经网络的学习算法
*   开发一种用于多层前馈神经网络的学习算法，以便网络能够被训练以隐式地捕获映射关系
*   以上都不是

**关于反向传播规则，以下哪项是正确的？**

*   它也被称为广义 Delta 规则
*   输出中的误差仅向后传播以确定权重更新
*   在任何阶段都没有信号反馈
*   以上所有

**为什么我们需要生物神经网络？**

*   解决机器视觉和自然语言处理等任务
*   应用启发式搜索方法来寻找问题的解决方案
*   制造智能的人机交互和用户友好型系统
*   以上所有

**神经网络中的可塑性是什么？**

*   输入模式不断变化
*   输入模式已变为静态
*   输出模式不断变化
*   输出是静态的

**网络的基本单元是**

*   大脑
*   细胞核
*   神经元
*   轴突

**在训练深度学习模型的每个周期中，以下哪项将具有恒定的输入？**

*   输入层与隐藏层之间的权重
*   隐藏层与输出层之间的权重
*   所有隐藏层神经元的偏置
*   输出层的激活函数
*   以上都不是

**使用池化层时不能应用反向传播**

*   正确
*   错误

**对于二分类问题，你会选择以下哪种架构？**

*   1
*   2
*   以上任意一个
*   以上都不是

**假设训练神经网络时出现问题。训练损失/验证损失保持不变。可能的原因是什么？**

*   架构定义不正确
*   提供给模型的数据有噪声
*   以上两者皆是

**以下哪项是机器学习的子集？**

*   SciPy
*   NumPy
*   深度学习
*   以上所有

## 答案

c, d, d, a, c, a, b, c, c, c

## 简答题

*   定义推荐系统。
*   什么是协同过滤？
*   定义人工神经网络 (ANN)。
*   解释感知机的含义。
*   解释人工神经网络的主要特征？
*   什么是激活函数？为什么要使用它们？
*   解释反向传播算法的重要性。
*   机器学习和深度学习的区别。
*   简述深度学习。

## 论述题

*   结合示例解释推荐系统的类型。
*   结合图解解释协同过滤技术。
*   区分 ANN 和 BNN。
*   解释单层和多层感知机。
*   什么是反向传播算法？结合示例解释。
*   权重和偏置在神经网络中的作用是什么？
*   结合应用示例解释深度学习的重要性。

## 参考文献

Hormozi, H., Hormozi, E. & Nohooji, H. R. (2012). 机器人操作器中适用机器学习方法的分类。*International Journal of Machine Learning and Computing (IJMLC)*，第 2 卷，第 5 期，2012。doi: 10.7763/IJMLC.2012.V2.189。第 560–563 页。可在 IJMLC 网站获取：http://www.ijmlc.org/papers/189-C00244-001.pdf

Kotsiantis, S. B. (2007)。监督机器学习：分类技术综述。*Informatica* 31 (2007)。第 249–268 页。检索自 IJS 网站。

Logistic Regression（逻辑回归）。第 223–237 页。可在以下网址获取：https://www.stat.cmu.edu/~cshalizi/uADA/12/lectures/ch12.pdf

Rosenblatt, F. (1962)。*Principles of Neurodynamics*（神经动力学原理）。Spartan, New York。

Setiono R. and Loew, W. K. (2000)。FERNN：一种从神经网络快速提取规则的算法。*Applied Intelligence*。*International Journal of Computer Trends and Technology (IJCTT)* – 第 48 卷，第 3 期，2017 年 6 月。ISSN: 2231-2803。http://www.ijcttjournal.org。第 138 页。

Shai Shalev-Shwartz and Shai Ben-David (2014)。*Understanding Machine Learning From Theory to Algorithms*（从理论到算法理解机器学习）。

T. Hastie, R. Tibshirani, J. H. Friedman (2001)。*The elements of statistical learning: Data mining, inference, and prediction*（统计学习基础：数据挖掘、推理与预测）。New York: Springer Verlag。

Taiwo, O. A. (2010)。机器学习算法的类型。载于 *New Advances in Machine Learning*（机器学习新进展），Yagang Zhang (Ed.)。ISBN: 978-953-307-034-6。InTech, University of Portsmouth United Kingdom。第 3–31 页。可在 InTech 开放网站获取：http://www.intechopen.com/books/new-advances-in-machine-learning/types-of-machine-learning-algorithms

Tapas Kanungo, D. M. (2002)。K-means 聚类的局部搜索近似算法。*Proceedings of the eighteenth annual symposium on Computational geometry*（第十八届计算几何年度研讨会论文集）。Barcelona, Spain: ACM Press。

Hiran, K., Khazanchi, D., Vyas, A. & Padmanaban, S. (2021)。*Machine Learning for Sustainable Development*（面向可持续发展的机器学习）。Berlin, Boston: De Gruyter。https://doi.org/10.1515/9783110702514

Mahrishi, M., Hiran, K. K., Meena, G., & Sharma, P. (Eds.)。 (2020)。*Machine Learning and Deep Learning in Real-time Applications*（实时应用中的机器学习与深度学习）。IGI global。

Barua, T., Doshi, R. & Hiran, K. (2020)。*Mobile Applications Development*（移动应用开发）。Berlin, Boston: De Gruyter。https://doi.org/10.1515/9783110689488

Witten, I. H. & Frank, E. (2005)。*Data Mining: Practical machine learning tools and techniques*（数据挖掘：实用机器学习工具与技术）（第 2 版）。ISBN: 012-088407-0。Morgan Kaufmann Publishers, San Francisco, CA, U.S.A. © 2005 Elsevier Inc. 检索自网站：ftp://93.63.40.27/pub/manuela.sbarra/Data Mining Practical Machine Learning Tools and Techniques - WEKA.pdf

S. B. Kotsiantis, P. E. Pintelas and I. D. Zaharakis. "Machine learning: a review of classification and combining techniques"（机器学习：分类与组合技术综述）。*Artificial Intelligence Rev*，第 26 卷，第 159-190 页，2006。

S. B. Kotsiantis. "Supervised Machine Learning: A Review of Classification"（监督机器学习：分类综述）。*Informatica (slovenia)*，第 31 卷，第 249-268 页，2007。

K. Wisaeng. "A Comparison of Different Classification Techniques for Bank Direct Marketing"（银行直销不同分类技术的比较）。*International Journal of Soft Computing and Engineering (IJSCE)*，第 3 卷，第 4 期，第 116-119 页，2013。

M. J. Islam, Q. M. J. Wu, M. Ahmadi and M. A. Sid-Ahmed. "Investigating the Performance of Naïve-Bayes Classifiers and K-Nearest Neighbor Classifiers"（朴素贝叶斯分类器与 K 近邻分类器性能研究）。*Journal of Convergence Information Technology*，第 5 卷，第 2 期，2010。

C.S. Trilok and J. Manoj. "WEKA Approach for Comparative Study of Classification Algorithm"（基于 WEKA 的分类算法比较研究）。*International Journal of Advanced Research in Computer and Communication Engineering*，第 1925-1931 页，2013。

R. Caruana and A. Niculescu-Mizil. "An empirical comparison of supervised learning algorithms"（监督学习算法的实证比较）。*23rd international conference on Machine learning*（第 23 届国际机器学习会议），2006。

R. Entezari-Maleki, A. Rezaei and B. Minaei-Bidgoli. "Comparison of Classification Methods Based on the Type of Attributes and Sample Size"（基于属性类型和样本量的分类方法比较）。*Journal of Convergence Information Technology*，第 4 卷，第 3 期，第 94-102 页，2009。

Lakhwani, K., Bhargava, S., Somwanshi, D., Doshi, R., & Hiran, K. K. (2020, December)。通过分析刺突基因利用多层人工神经网络推断冠状病毒潜在宿主的增强方法。载于 *2020 5th IEEE International Conference on Recent Advances and Innovations in Engineering (ICRAIE)*（2020 年第 5 届 IEEE 工程最新进展与创新国际会议）（第 1-5 页）。IEEE。

Vyas, A., Dhiman, H. & Hiran, K. (2021)。四种不同拓扑结构的对称四分之一波光环谐振器建模及基于机器学习方法的性能分析。*Journal of Optical Communications*（光通信期刊），(), 000010151520200270。https://doi.org/10.1515/joc-2020-0270
