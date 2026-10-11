

# 实验编号 10

实现非参数局部加权回归算法以拟合数据点。为实验选择合适的数据集并绘制图形。

## 局部加权回归算法

### 回归

回归是统计学中的一种技术，当目标量是连续时，用于预测所需目标量的值。

在回归中，我们寻求识别（或估计）与给定输入向量 `x` 相关联的连续变量 `y`。

*   `y` 称为因变量。
*   `x` 称为自变量。

![](image-9ji1yrpb.jpg)

### Loess/Lowess 回归

Loess 回归是一种非参数技术，它使用局部加权回归在散点图中拟合一条穿过数据点的平滑曲线。

![](image-jrxmolyl.jpg)

### Lowess 算法

局部加权回归是统计学习中使用的一种非常强大的非参数模型。

给定数据集 `X`、`y`，我们试图找到一个模型参数 `β(x)`，使加权平方误差残差和最小化。

权重由核函数（`k` 或 `w`）给出，可以任意选择。

#### 算法

1.  将给定的数据样本读入 `X`，将曲线（线性或非线性）读入 `Y`。
2.  设置平滑参数或自由参数的值，记为 `τ`。
3.  设置偏置/关注点集 `x0`，它是 `X` 的子集。
4.  使用以下公式确定权重矩阵：
    ![](image-8fnziujm.jpg)
5.  使用以下公式确定模型项参数 `β` 的值：
    ![](image-slpiqqlf.jpg)
6.  预测值 `= x0 * β`：

### 程序

```python
import numpy as np
import matplotlib.pyplot as plt

def local_regression(x0, X, Y, tau):
    # add bias term
    x0 = np.r_[1, x0]  # Add one to avoid the loss in information
    X = np.c_[np.ones(len(X)), X]

    # fit model: normal equations with kernel
    xw = X.T * radial_kernel(x0, X, tau)  # XTranspose * W
    beta = np.linalg.pinv(xw @ X) @ xw @ Y  # @ Matrix Multiplication or Dot Product

    # predict value
    return x0 @ beta  # @ Matrix Multiplication or Dot Product for prediction

def radial_kernel(x0, X, tau):
    return np.exp(np.sum((X - x0) ** 2, axis=1) / (-2 * tau * tau))
    # Weight or Radial Kernal Bias Function

n = 1000
# generate dataset
X = np.linspace(-3, 3, num=n)
Y = np.log(np.abs(X ** 2 - 1) + .5)

# jitter X
X += np.random.normal(scale=.1, size=n)

domain = np.linspace(-3, 3, num=300)

def plot_lwr():
    # prediction through regression for tau = 10.0
    prediction = [local_regression(x0, X, Y, 10.0) for x0 in domain]
    fig, axs = plt.subplots(2, 2, figsize=(10, 8))

    axs[0, 0].plot(X, Y, 'o', alpha=0.5)
    axs[0, 0].plot(domain, prediction, color='red')
    axs[0, 0].set_title(f"tau = 10.0")

    # prediction through regression for tau = 1.0
    prediction = [local_regression(x0, X, Y, 1.0) for x0 in domain]
    axs[0, 1].plot(X, Y, 'o', alpha=0.5)
    axs[0, 1].plot(domain, prediction, color='red')
    axs[0, 1].set_title(f"tau = 1.0")

    # prediction through regression for tau = 0.1
    prediction = [local_regression(x0, X, Y, 0.1) for x0 in domain]
    axs[1, 0].plot(X, Y, 'o', alpha=0.5)
    axs[1, 0].plot(domain, prediction, color='red')
    axs[1, 0].set_title(f"tau = 0.1")

    # prediction through regression for tau = 0.01
    prediction = [local_regression(x0, X, Y, 0.01) for x0 in domain]
    axs[1, 1].plot(X, Y, 'o', alpha=0.5)
    axs[1, 1].plot(domain, prediction, color='red')
    axs[1, 1].set_title(f"tau = 0.01")

    fig.tight_layout()
    return plt

plot_lwr()
```

### 输出

![](image-berpti8k.jpg)

---

# 模拟试卷 – 1

## 选择题

1.  **机器学习是包含学习算法的人工智能领域，这些算法**
    *   提高其性能
    *   在执行某项任务时
    *   随着时间推移通过经验
    *   **以上皆是**

2.  **不同的学习方法不包括**
    *   记忆
    *   类比
    *   演绎
    *   **引入**

3.  **什么是感知机？**
    *   **带有预处理的单层前馈神经网络**
    *   自联想神经网络
    *   双层自联想神经网络
    *   包含反馈的神经网络

4.  **在无标签数据中寻找隐藏结构的问题称为**
    *   监督学习
    *   **无监督学习**
    *   强化学习
    *   以上都不是

5.  **一家电商公司希望将客户细分为不同群体以发送合适的优惠，这是以下哪项的示例**
    *   **无监督学习**
    *   监督学习
    *   强化学习
    *   以上都不是

6.  **以下哪项是无监督学习的应用？**
    *   聚类
    *   异常检测
    *   神经网络
    *   **以上皆是**

7.  **在 k-means 聚类算法中，k 是：**
    *   **正整数**
    *   负整数
    *   随机数
    *   复数

8.  **两个不同簇中距离最近的两点之间的最短距离被视为：**
    *   **单链接**
    *   全链接
    *   平均链接
    *   质心链接

9.  **什么是机器学习？**
    *   **通过使用计算机程序自主获取知识**
    *   通过使用手工程序自主获取知识
    *   通过使用计算机程序选择性获取知识
    *   通过使用手工程序选择性获取知识

10. **以下哪项关于神经网络的描述是正确的？**
    *   训练时间取决于网络的大小。
    *   神经网络可以在传统计算机上模拟。
    *   人工神经元在操作上与生物神经元完全相同。
    *   以上所有
    *   (ii) 为真
    *   **(i) 和 (ii) 为真**
    *   以上都不是

## 填空题

1.  根据面积、房间数量等预测房价是 **监督** 机器学习的示例。
2.  工科学生的专业是一个 **分类 / 标称** 特征。
3.  在机器学习中，**数据 / 特征** 作为输入，**标签 / 预测** 作为输出。
4.  **聚类 / 无监督学习算法** 处理未分类数据并将其划分为不同的簇。
5.  Q-learning 技术是一种 **强化学习** 方法。

## 简答题

1.  什么是机器学习？
2.  解释机器学习的应用。
3.  解释分类错误。
4.  找出 PCA 和 ICA 的区别。
5.  解释支持向量机 (SVM)。

## 论述题

1.  解释执行机器学习所用的不同步骤。
2.  区分监督学习、无监督学习和强化学习。
3.  回归和分类有什么区别？举例说明。
4.  定义聚类。解释聚类和分类的区别。
5.  解释单链接法和全链接法的区别。
6.  Apriori 算法有哪些优缺点？
7.  解释凝聚层次聚类的逐步工作原理。
8.  定义 GMM 并详细解释高斯混合模型的工作原理。
9.  简述以下任意两项
    *   线性二次调节
    *   Q-learning
    *   MDPs (马尔可夫决策过程)
    *   价值函数近似
10. 考虑以下事务数据集，使用 FP-growth 算法找出频繁模式并生成关联规则。
    *   条件：最小支持度 = 50%，最小置信度 = 60%。

