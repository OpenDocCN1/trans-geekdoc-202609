
[Figure 7.7](#ch07.xhtml#fig7.7) 显示了一个线段，该线段近似了若干点的散点图（其中一些点与线段相交）。[Figure 7.7](#ch07.xhtml#fig7.7) 中的线段的均方误差 (MSE) 计算如下：

MSE = (1\*1 + (-1)\*(-1) + (-1)\*(-1) + 1\*1)/7 = 4/7 ![Figure 7.7 ¶ A Line Graph that Approximates Points of a Scatter Plot.](images/fig7.7.jpg)

Figure 7.7 ¶ A Line Graph that Approximates Points of a Scatter Plot.

[Figure 7.8](#ch07.xhtml#fig7.8) 显示了一组点和一条线，这条线可能是数据的最佳拟合直线。[Figure 7.8](#ch07.xhtml#fig7.8) 中的线段的均方误差 (MSE) 计算如下：

MSE = ((-2)\*(-2) + 2\*2)/7 = 8/7 ![Figure 7.8 ¶ A Line Graph that Approximates Points of a Scatter Plot.](images/fig7.8.jpg)

Figure 7.8 ¶ A Line Graph that Approximates Points of a Scatter Plot.

因此，[Figure 7.7](#ch07.xhtml#fig7.7) 中的直线的 MSE 小于 [Figure 7.8](#ch07.xhtml#fig7.8) 中的直线的 MSE，这可能让你感到惊讶（或者你猜对了？）

在这两个图中，我们轻松快速计算了 MSE，但总体而言，这要困难得多。例如，如果我们在欧几里得平面上绘制 10 个点且它们不紧贴一条直线，且各项数值都不是整数，我们可能需要使用计算器。

更好的解决方案是使用 NumPy 函数，例如 np.linspace() API，如下一节所讨论。

## **Approximating Linear Data with np.linspace()**

[Listing 7.4](#ch07.xhtml#list7.4) 显示了 np_linspace1.py 的内容，该文件演示了如何结合 np.linspace() API 使用“扰动技术”生成一些数据。

***LISTING 7.4: np_linspace1.py***

import numpy as np  trainX = np.linspace(-1, 1, 6) trainY = 3\*trainX+ np.random.randn(\*trainX.shape)\*0.5  print("trainX: ", trainX) print("trainY: ", trainY) 

该代码示例的目的仅仅是生成并显示一组随机数。本章后面，我们将使用这段代码作为实际线性回归任务的起点。

[Listing 7.4](#ch07.xhtml#list7.4) 以 trainX 数组变量的定义开始，该变量通过 np.linspace() API 初始化。随后，通过“扰动技术”定义 trainY 数组变量，这是你在之前的代码示例中已经看到的方法。[Listing 7.4](#ch07.xhtml#list7.4) 的输出如下：

trainX:  [ -1.  -0.6 -0.2  0.2  0.6  1. ] trainY:  [ -2.9008553  -2.26684745 -0.59516253  0.66452207  1.82669051  2.30549295] trainX:  [ -1.  -0.6 -0.2  0.2  0.6  1. ] trainY:  [ -2.9008553  -2.26684745 -0.59516253  0.66452207  1.82669051  2.30549295] 

## **What are Ensemble Methods?**

在机器学习中，*ensembles* 指的是结合多个模型预测的方法。其核心思想是通过组合多个已训练的分类器的结果，来超越单个分类器的表现；而且，最差的集合结果通常不会比集合中最差的分类器更差。虽然前面的陈述只是一种启发性（没有正式且严格的证明），但在实践中它大多运行良好。

集合的结果或预测可以通过各种“组合”规则来决定（平均规则是最常用）：

*   多数投票

*   平均值

*   加权平均

*   最大值

*   最小值

*   乘积

最常用的两种集合方法是 *bagging* 和 *boosting*（它们采用相反的方法），并在本节后续内容中讨论。

集合方法是元算法，它们将多种机器学习技术组合成一个预测模型，因为这样可以降低方差（bagging）或偏差（boosting）。这些方法也可以改善预测（stacking）。Adaboost（稍后讨论）是一种序列集合方法。

集合方法构建一个分类器集合，然后通过取（加权）多数投票来对新数据点进行分类。原始的集合方法是贝叶斯平均，更近期的算法包括错误校正输出编码、bagging 和 boosting。

关键思想是，多个模型的预测优于单个模型的预测。然而，分类器必须足够多样化，才能使集合产生良好结果。这可以通过以下方式实现：

*   使用不同的基分类器

*   使用不同的特征进行训练

*   使用训练集的不同部分进行训练

*   使用不同的参数

*Stacking ensembles* 是一类算法，它们训练一个元学习器，以找到基础学习者的最佳组合。与 bagging 和 boosting 不同，stacking 的目标是对强健且多样的学习者集合进行集合。

*Random forest ensembles* 是一种用于分类、回归和其他任务的集合学习方法，它在训练时构建大量决策树：分类时输出类的众数，回归时输出平均预测。

## **Four Types of Ensemble Methods**

集合方法可以分为以下四类：

*   bagging

*   boosting

*   stacking

*   blending

下面的子节提供了上述列表中每一项的简要介绍。

### **Bagging**

*Bagging*（“boosted aggregation”）并行训练许多强分类器，以降低过拟合的可能性。下一步是通过平均化它们的预测来组合所有强分类器。Bagging 通过结合基于同一数据集不同子样本的多个分类器的结果，降低了预测方差。

用于随机森林的 bagging 模型是一个 ensemble，它通过使用多个算法的预测来计算最终的聚合预测，从而防止过拟合，并降低算法的方差。

### **Boosting**

*Boosting* 使用所谓的弱分类器，这些分类器可能具有相当高的错误率。Boosting 按顺序训练大量弱分类器，以提升简单模型的预测能力。每个弱模型尝试改进其前一个模型的预测。Boosting 然后将弱分类器组合成一个强分类器。

尽管 boosting 的预测精度优于 bagging，但它也更容易对训练数据过拟合。下面列出了一些 boosting 算法：

*   AdaBoost

*   Random Forest

*   AdaBoost

*   GBM

*   XGB

*   Light GBM

*   CatBoost

*   LPBoost

*   TotalBoost

*   BrownBoost

*   xgboost

*   MadaBoost

*   LogitBoost

*Adaptive boosting* 是一种对训练数据点和假设进行加权的方法。许多 boosting 算法适用于 *AnyBoost* 框架，该框架表明 boosting 在使用凸损失函数时，在函数空间中执行梯度下降。

下面的步骤描述了寻找弱规则的处理过程：

1.  使用不同的分布运行基础学习（ML）算法

2.  每次运行基础学习算法时，都会生成一个新的弱预测规则

3.  经过多次迭代后，boosting 算法将这些弱规则组合成一个强预测规则。

首先在整个数据集上训练第一个预测器，初始时对每个观测值赋予相同的权重。如果第一个学习者预测错误类别，则对未被正确分类的观测值赋予更高权重。

随后的预测器是基于前一个预测器的表现，在训练集上进行训练。持续添加分类器学习者，直到达到模型数量的限制或精度满足要求。

### **Stacked Models and Blending Models**

*Stacked models* 包含以下步骤：

1.  创建多个基础模型。

2.  收集基础模型的结果。

3.  在基础模型之上创建一个元模型。

