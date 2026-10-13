
# 比较结果

现在让我们将上述获得的结果与 scikit-learn 库提供的现成梯度提升分类器的结果进行比较。

完整的代码文件可以从我们在 Google Drive 中的共享文件夹下载：

[https://drive.google.com/drive/folders/1FqJvo4ZPazNbEH_GlHFoodqvegnQmHcn?usp=share_link](https://drive.google.com/drive/folders/1FqJvo4ZPazNbEH_GlHFoodqvegnQmHcn?usp=share_link)

![](Images/9789815136982-C6-B4.jpg)

![](Images/9789815136982-C6-B5.jpg)

![](Images/9789815136982-C6-B6.jpg)

![](Images/9789815136982-C6-B7.jpg)

从 scikit-learn 梯度提升分类器的结果可以看出，与我们手动计算的结果相比，生成了相同的决策树，所有决策树节点具有相同的 `squared_error`，所有决策树叶节点具有相同的 gamma 值（注意 scikit-learn 在决策树图中简单地使用 "value" 来表示 "gamma value"）。此外，获得了相同的 3 个训练样本的预测概率（即 3 个样本属于类别 1 的概率，x1 的 P1=0.7653，x2 的 P2=0.4579，x3 的 P3=0.7224）。然后，相应地获得了相同的预测类别（即 x1 预测为类别 1，x2 预测为类别 0，x3 预测为类别 1）。最后，获得了相同的先前未见过的 3 卧室房屋的预测概率和类别（即它属于类别 1 的概率是 0.7224，预测类别是 1）。

# 结论

在本章中，我们讨论了用于回归和分类的梯度提升概念。为了使材料更易懂，我们将抽象数学理论保持在最低限度。相反，我们专注于两个具体的数值示例，使用小数据集预测房屋销售价格和房屋在房地产市场是否容易出售，逐步演示它们。我们还提供了示例代码，并与现成库 scikit-learn 的梯度提升回归和分类模型进行了比较。在本章结束时，读者应该对梯度提升机器学习在幕后如何工作、数学如何与算法的实现和性能相关联有一个全面的理解，并能更好地将其应用于他们的项目中。

# 参考文献

| 引用 | 内容 |
| --- | --- |
| [1] | Friedman J.H.. Greedy function approximation: A gradient boosting machine., *Ann. Stat..* **2001;** 29(5): 1189-1232.  [[CrossRef]](http://dx.doi.org/10.1214/aos/1013203451) |
| [2] | Wade C.. , . Hands-On Gradient Boosting with XGBoost and scikit-learn: Perform accessible machine learning and extreme gradient boosting with Python.. Birmingham, England: Packt Publishing; 2020. |
| [3] | Wang Z., Li J., Rangaiah G.P., Wu Z.. Machine learning aided multi-objective optimization and multi-criteria decision making: Framework and two applications in chemical engineering., *Comput. Chem. Eng..* **2022;** 165(107945): 107945.  [[CrossRef]](http://dx.doi.org/10.1016/j.compchemeng.2022.107945) |
| [4] | Hastie T., Tibshirani R., Friedman J.. , . The elements of statistical learning: Data mining, inference, and prediction.. 2nd ed. New York, NY: Springer; 2009. |

# 支持向量机

**Zhiyuan Wang**, **Sayed Ameenuddin Irfan**, **Christopher Teoh**, **Priyanka Hriday Bhoyar**

## 摘要

在本章中，我们研究了线性可分和线性不可分情况下的支持向量机（SVM），通过最小化抽象数学理论来强调易懂性。我们提供了带有小数据集的具体数值示例，并提供逐步演示，说明 SVM 的内部工作原理。此外，我们提供了示例代码，并与 scikit-learn 库中可用的 SVM 模型进行了比较。完成本章后，读者将获得对 SVM 机制的全面理解，及其与算法实现和性能的联系，并做好充分准备将其应用于实际应用中。

**关键词：** 线性可分、线性不可分、数值示例、多项式核、径向基函数核、支持向量机、小数据集、Scikit-Learn。

## 7.1 支持向量机简介

支持向量机（缩写为 `SVM`）是一种强大且广泛适用的机器学习算法，已成功应用于各个领域，如图像和语音识别、自然语言处理、生物信息学和金融等。`SVM` 算法的目标是在 N 维空间（其中 N 是特征数量）中确定一个超平面，以清晰可辨的方式对数据点进行分类。其定义方式使得 N 维空间中不同类别数据点之间的边距距离最大化 [[1]](#9789815136982-C7.html#r1)[[2]](#9789815136982-C7.html#r2)。如果边距距离最大化，那么后续的新数据点（先前未见过的）将以更大的信心被分类。对于线性不可分数据集，`SVM` 主要采用核函数将原始数据映射到高维希尔伯特空间以实现线性可分，从而解决线性不可分问题 [[3]](#9789815136982-C7.html#r3)。此外，值得一提的是，支持向量只是更接近超平面的训练数据点。这些数据点对于构建 `SVM` 模型更为相关和关键，因为它们有助于确定分离超平面的方程 [[4]](#9789815136982-C7.html#r4)。图（[**7.1**](#9789815136982-C7.html#f7.1)）说明了

使用来自 2 个类别（即正类（+）和负类（-））的 10 个样本的数据集，说明了超平面、支持向量和边距。

![](Images/9789815136982-C7-F1.jpg)
**图 (7.1)**

SVM 超平面、支持向量和边距的示意图。

## 7.2 支持向量机的数学原理：线性可分情况

图（[**7.1**](#9789815136982-C7.html#f7.1)）中使用的数据集已简化以降低复杂性。因此，现在只有 2 个属于正类（+）的数据点，和 2 个属于负类（-）的数据点，如图（[**7.2**](#9789815136982-C7.html#f7.2)）所示。目标是找到与最大边距相关的超平面。接下来，我们绘制一个向量 `w→`（任意长度），它从原点开始并垂直于假设的超平面。此外，假设我们还有先前未见过的数据 `u→`，我们想要预测 `u→` 的类别，无论它是 + 类还是 - 类。

![](Images/9789815136982-C7-F2.jpg)
**图 (7.2)**

2 个 + 类数据点、2 个 - 类数据点、垂直于假设边距的 `w→` 和先前未见过的 `u→` 的示意图。

将 `u→` 投影到垂直于边距的向量（即 `w→`）上，如果该投影大于或等于（≥）某个常数 `c`，该常数穿过中线，那么它必须是正（+）数据点。这可以用数学方式表示为：

`w→⋅u→≥c`，则 `u→` 标记为 +

执行简单变换：

`w→⋅u→-c≥0`

`w→⋅u→+bt≥0`，其中 `bt=-c`

边距的中线：

`w→⋅u→+bt=0`

边距的边缘线（靠近 +）：

`w→⋅u→+bt=ä`

此处，`ä` 为正常数

两边同时除以 `ä`：

`w→/ä⋅u→+bt/ä=1`

令 `W→=w→/ä` 和 `b=bt/ä`，

边距的边缘线（靠近 +）更新为：

`W→⋅u→+b=1`

边距的中线更新为：

`W→⋅u→+b=0`

对称地，如图（[**7.3**](#9789815136982-C7.html#f7.3)）所示，边距的边缘线（靠近 -）更新为：

![](Images/9789815136982-C7-F3.jpg)
**图 (7.3)**

超平面、边缘线（靠近 +）和边缘线（靠近 -）的通用方程示意图。

`W→⋅u→+b=-1`
