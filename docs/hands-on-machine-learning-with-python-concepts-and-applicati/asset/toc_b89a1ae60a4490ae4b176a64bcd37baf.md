## 献词
## 作者简介
## 来自 AI Sciences 出版社
## 前言
## 主题概览
## 赠送礼物
## 安装与设置
## Python 快速入门
## Jupyter Notebook
## 使用 Jupyter Notebook 和 Python 库进行数据科学
### 核心库：NumPy、Pandas、SciPy、Matplotlib、Scikit-learn
### 导入数据集、分类器和指标
#### NumPy
#### Pandas
#### Matplotlib
#### Scikit-learn
## Numerical Python (NumPy)
### 矩阵乘积
## Pandas
## Scientific Python (SciPy)
### Scipy
## Matplotlib
## Jupyter notebooks 的魔法命令
### 计算正弦曲线上点的 x 和 y 坐标
### 使用 matplotlib 绘制点
## Scikit-Learn
### 示例决策树分类器
#### 加载鸢尾花数据集
#### 将 CART 模型拟合到数据
#### 进行预测
#### 总结模型的拟合情况
### 关于 Google TensorFlow
## 你的第一个机器学习项目
### 泰坦尼克号生存预测
## 数据探索与特征工程
### 数据概览
### 特征筛选
### 假设与验证
#### 乘客等级 (`Pclass`) 与生存率
#### 性别 (`Sex`) 与生存率
#### 同行兄弟姐妹/配偶 (`SibSp`) 与生存率
#### 同行父母/子女 (`Parch`) 与生存率
### 数据可视化
#### 年龄 (`Age`) 分布
#### 乘客等级 (`Pclass`) 与生存情况
#### 登船港口 (`Embarked`) 的影响
### 特征工程实施
## 数据预处理与模型训练
### Fare 特征分箱与序数化
### 模型选择与训练
#### 逻辑回归
#### 随机森林分类器
### 启示与可能性
## 通用工作流程
## 通用机器学习概念
### 什么是机器学习
## 机器学习概述
### 机器学习的三大主要分支
#### 监督学习
#### 无监督学习
#### 半监督学习算法
#### 强化学习算法
### 深度学习
## 那么有什么区别呢？
### 过拟合与欠拟合
### 正确性
### 偏差-方差权衡
### 特征提取与选择
### 机器学习为何流行
## 回归
### 简单线性回归与多元线性回归
## matplotlib magic command for Jupyter notebook
## 线性回归示例
### 数据准备
### 模型训练
### import linear regression classifier, initialize and fit the model
### 预测
### 评估
### The coefficients
### The mean squared error
### Explained variance score: 1 is perfect prediction
### 结果可视化
### 完整代码
### import libraries
### load dataset
### plot crime vs price
### separate predictors and targets
### import linear regression classifier, initialize and fit the model
### The coefficients
### The mean squared error
### Explained variance score: 1 is perfect prediction
### plot predicted prices vs actual prices
## 逻辑回归
### Pima 印第安人糖尿病分类
### Training the model
### 广义线性模型
### data.exog 是自变量 X
### 使用默认连接函数实例化一个泊松族模型。
### 回归示例：预测波士顿房价
#### 执行分析的步骤
##### 导入库：
##### 导入模型
##### 如何预测
## K 近邻算法
### K 近邻算法简介
### 如何创建和测试 K 近邻分类器
### 导入模型
### K 近邻分类器实现
#### 使用 Scikit-Learn 的基础实现
##### 完整代码示例
###### import libraries
###### read dataset from csv file
###### display first five observations
###### get shape of dataset, number of observations, number of features
###### get information on data distribution
###### plot correlation between features
###### create features and labels
###### split dataset into training set and test set
###### import nearest neighbor classifier
###### fit data
###### get predicted class labels
###### get accuracy of model on test set
#### 另一个应用：鸢尾花分类
##### 导入库
### 计算相似度
### 定位邻居
### K 近邻算法实现
#### loop over all observations
### 生成响应
#### instantiate learning model (k = 3)
#### fitting the model
### 评估准确率
#### predicting the test set results
### 维度灾难
## 朴素贝叶斯
### 朴素贝叶斯的应用
### 如何在 Python 中使用朴素贝叶斯构建基础模型
### comment the magic command below if not running in Jupyter notebook
## 决策树与随机森林
### 分区的熵
### 熵与决策树
### 创建决策树
### 如果不在 Jupyter notebook 中运行，请注释掉下面的魔法命令
### 随机森林
#### load dataset
#### separate features and labels
#### split dataset into train and test sets
#### import random forest classifier from sklearn
#### fit classifier on data
#### predict classes of test set samples
#### evaluate classifier performance using accuracy metric
## 神经网络
### 感知机
### 反向传播
### 如何使用 TensorFlow 运行神经网络
### 如何获取数据
### TensorFlow MNIST 教程
#### 加载数据和库
##### Import MNIST data
#### 如何训练和测试数据
##### 参数
###### Parameters
###### Network Parameters
##### 图输入
###### tf Graph input
###### Store layers weight & bias
##### 创建模型
###### Create model
##### 构建模型、损失函数和优化器
###### Construct model
###### Define loss and optimizer
###### Evaluate model (with test logits, for dropout to be disabled)
###### Initialize the variables (i.e. assign their default value)
##### 开始训练
###### Start training
#### 完整代码清单
##### Parameters
##### Network Parameters
##### tf Graph input
##### Store layers weight & bias
##### Create model
##### Construct model
##### Define loss and optimizer
##### Evaluate model (with test logits, for dropout to be disabled)
##### Initialize the variables (i.e. assign their default value)
##### Start training
##### Calculate accuracy for MNIST test images
## 聚类
### 聚类简介
### 聚类示例
### 使用 Scikit-Learn 运行 K-means
#### import libraries
#### read dataset from csv file
#### display first five observations
#### finding the optimum number of clusters for k-means classification
#### plotting the results onto a line graph, allowing us to observe 'The elbow'
### K-means 聚类与层次聚类
#### 用于寻找最优 K 的肘部法则
#### 创建 K-means 模型
##### 创建 kmeans 对象
#### 可视化聚类
##### 可视化聚类
##### 绘制聚类的质心
#### 模型实现
#### 自底向上层次聚类
#### K-means 聚类
## 网络分析
### 介数中心性
### 特征向量中心性
## 推荐系统
## 分类
## Overview of Classification Algorithms
### Multi-class Classification
### Common Classification Algorithms
### Support Vector Machines
### How to Create and Test a Support Vector Machine Classifier
#### import libraries
#### read dataset from csv file
#### create features and labels
#### split dataset into training set and test set
#### import support vector machine classifier
#### fit data
#### get predicted class labels
#### get accuracy of model on test set
## Deep Learning with TensorFlow
## 深度学习概述
### 深度学习与其他机器学习方法的比较
## 深度学习概述
### 深度学习的应用
### Python 深度学习框架
### 安装 TensorFlow
#### 在 Windows 上安装 TensorFlow
#### 在 Linux 上安装 TensorFlow
#### 在 macOS 上安装 TensorFlow
### 如何创建神经网络模型
### 深度学习案例研究
### 银行客户流失建模
## 使用深度学习进行客户流失建模
### import all relevant libraries
### load the dataset
### get first five rows (observations)
### encoding categorical data
### splitting the dataset into the training set and test set
### feature scaling
### build the neural network
### define model
### we start training by applying gradient descent algorithm
## 情感分析
### load IMDB dataset
### data preprocessing
### sequence padding
### converting labels to binary vectors
### building the convolutional network
## 训练
### import tflearn, layers and data utilties
### load IMDB dataset
### data preprocessing
### sequence padding
### converting labels to binary vectors
### building the convolutional network
### training
## 来源与参考
### 软件、库与编程语言
### 数据集
### 在线书籍、教程与其他参考资料