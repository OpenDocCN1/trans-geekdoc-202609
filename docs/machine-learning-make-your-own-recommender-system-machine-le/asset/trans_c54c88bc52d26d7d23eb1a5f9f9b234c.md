

## 机器学习
## 制作您自己的推荐系统

![](img/a19c36b1869b7a68ada55e0c3c42a30d_0_0.png)

Oliver Theobald

## 机器学习入门：制作您自己的推荐系统

机器学习入门系列

由 Scatterplot Press 出版

Oliver Theobald

## 第一版

版权 © 2018 Oliver Theobald
由 Scatterplot Press 出版

版权所有。未经出版商事先书面许可，不得以任何形式或任何手段复制、分发或传播本出版物的任何部分，包括影印、录音或其他电子或机械方法，但版权法允许的书评中的简短引用以及某些其他非商业用途除外。

如有反馈、媒体联系或本书的遗漏或错误，请联系作者 oliver.theobald@scatterplotpress.com。

## 目录

- 前言
- 本书使用的数据集
- 简介
- 解剖结构
- 搭建沙箱环境
- 处理数据
- 数据降维
- 协同过滤 第一部分
- 协同过滤 第二部分
- 基于内容的过滤
- 评估
- 隐私与伦理
- 推荐系统的未来
- 进一步资源

## 关注我们：

**Skillshare**
www.skillshare.com/user/machinelearning_beginners

**Teachable**
http://scatterplotpress.teachable.com/

**YouTube**
Scatterplot Media

**Instagram**
machinelearning_beginners

## 前言

从 Facebook 上的相关朋友推荐到 Amazon 上的商品推荐，推荐系统的存在无处不在。看看您最近在线浏览和消费的内容，因为您的许多在线活动，包括发现这本书，很可能都源自算法驱动的推荐。这些数据驱动的系统正在削弱传统搜索引擎的主导地位，同时帮助小众和晦涩物品的可发现性。作为机器学习的一个分支领域，理解这些模型的工作原理比以往任何时候都更加重要，而在这本书中，我们更进一步，编写三个基本的推荐系统。

本书专为具有部分数据科学和机器学习背景知识的初学者设计，包括统计学和使用 Python 进行计算机编程。如果这是您第一次涉足数据科学，在开始之前，您可能需要先花几个小时阅读我的第一本书《机器学习绝对入门》。

## 本书使用的数据集

### Goodbooks-10k 数据集（第 6 章）

这两个数据集包含从 www.goodreads.com 收集的图书和用户评分信息。第一个数据集包含单个用户的图书评分，而第二个数据集包含单个图书的信息，例如平均评分、五星级评分数量、ISBN 号码、作者等。
https://www.kaggle.com/sriharshavogeti/collaborative-recommender-system-on-goodreads/data

### 广告数据集（第 7 章）

该数据集包含关于响应在线广告的用户特征的虚构信息，包括他们的性别、年龄、位置、每天在线时间以及是否点击了广告。该数据集由 Pierian Data 的 Udemy 课程讲师 Jose Portilla 创建，并在他的课程 Python for Data Science and Machine Learning Bootcamp 中使用。
https://www.kaggle.com/fayomi/advertising/data

### 墨尔本住房市场（第 8 章）

这个第三个数据集包含澳大利亚墨尔本的房屋、公寓和联排别墅价格数据。该数据集包含每周在 www.domain.com.au 上发布的公开可用房源的抓取数据。完整数据集包含 14,242 个房源和 21 个变量，包括地址、郊区、土地面积、房间数量、价格、经度、纬度、邮政编码等。
https://www.kaggle.com/anthonypino/melbourne-housing-market/

## 介绍 Scikit-Learn

Scikit-learn 是通用机器学习的核心库。它提供了大量浅层算法[1]的存储库，包括逻辑回归、决策树、线性回归、梯度提升等，以及一系列评估指标，如平均绝对误差，以及包括分割验证和交叉验证在内的数据分区方法。

Scikit-learn 还用于执行许多重要的机器学习任务，包括训练模型和使用训练好的模型来预测测试数据。

下表简要概述了 Scikit-learn 中常用的机器学习术语和函数。

| 术语 | 解释 | 代码示例 |
|---|---|---|
| estimator | 估计器是指一组超参数值，例如支持向量机中的 C、k-NN 中的 n_neighbors 或随机森林中的 n 棵树。在训练模型之前设置，估计器将每个超参数值映射到学习算法。 | model = ensemble.GradientBoostingRegressor(<br>    n_estimators = 150,<br>    learning_rate = 0.1,<br>    max_depth = 30,<br>    min_samples_split = 4,<br>    min_samples_leaf = 5,<br>    max_features = 0.6,<br>    loss = "huber"<br>)<br><br>这七个超参数中的每一个都代表梯度提升算法的一个单独估计器。 |
| fit() | 设置估计器后，fit() 函数用于在训练数据上运行学习算法并训练预测模型。 | model = KNeighborsClassifier(n_neighbors=5)<br>model.fit(X_train, y_train)<br><br>此代码片段将 k-NN 模型拟合到 X 和 y 训练数据上。 |
| predict() | 模型训练完成后，predict() 函数使用新训练的模型利用 X 测试数据进行预测。在监督学习中，这涉及使用模型来预测 X 测试数据的标签或值。 | prediction = model.predict(X_test)<br><br>在此示例中，训练好的模型被要求预测 X 测试数据，并将其分配为新变量 ("prediction")。 |
| transform() | transform() 函数用于在将数据馈送到学习算法之前对其进行修改（预处理）。这意味着获取原始数据并输出其转换版本。示例包括归一化、标准化、降维。 | from sklearn.preprocessing import StandardScaler<br>scaler = StandardScaler()<br>scaler.fit(X_train)<br>X_train = scaler.transform(X_train)<br><br>导入 StandardScaler 后，我们可以使用 transform 方法重新缩放/标准化 X 训练数据。转换后的训练数据被缩放为单位方差且均值为零，现在可以拟合到学习算法上。 |

表 1：Scikit-learn 关键术语和函数概览

## 简介

不久之前，上网仍像看报纸或看电影一样，是我们日常生活中的一项独立活动。一两个小时里，我们断开电话线，听着调制解调器连接万维网的刺耳声。

加载速度很慢，每次点击前都需要经过一段冗长的思考过程。等待二十秒或更长时间才能渲染页面，点错链接会付出沉重的时间代价。但后来，随着无线宽带互联网进入越来越多的家庭、学校和办公室，在线行为发生了改变，我们的浏览习惯开始变得更加大胆。

哎呀！点错链接了？没问题。点击“后退”按钮，您就回到了原点。可能会损失几秒钟，但正如史蒂夫·克鲁格在《不要让我思考：Web 可用性的常识方法》中写道，“猜错的代价并不大”[2]。克鲁格澄清说，用户不会选择最佳选项，而是选择“第一个合理的选项”，他将这种策略称为“满意化”。“一旦我们找到一个看起来可能通向我们要找的东西的链接，我们很有可能会点击它。”[3]

设计实践也有助于进一步简化用户习惯。随着互联网用户对网站导航越来越熟悉，网页设计师意识到模仿现有设计规范比试图重新发明轮子更容易、更有效。网络用户开始期望在页面右上角看到“登录”按钮，在页脚中看到联系方式和更多菜单选项，并将最大、最亮的按钮作为下一步点击的线索。

但有了这种新的信心，我们作为用户放弃了一部分来自离线世界的行为编程，不再仔细吸收和消化信息。我们变得不耐烦且不易分心，注意力下降，“满意化”占据主导。如技术研究公司 Gartner 的副总裁 Mike McGuire 所说，“如果除了您最初拨入的内容之外，没有其他东西出现来满足您的兴趣，那么您就离开了。”[4]

意识到问题后，互联网公司意识到他们需要一种新的方式来吸引注意力并遏制我们的“掠夺式”思维。他们知道，设计迎合个人需求的在线内容是不可能的
