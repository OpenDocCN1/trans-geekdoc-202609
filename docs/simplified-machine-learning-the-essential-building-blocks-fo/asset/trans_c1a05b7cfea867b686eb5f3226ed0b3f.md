

### 3. 实现 Softmax 动作选择以解决多臂老虎机问题或简单的网格世界。使用温度参数调节来控制探索程度，并将 Softmax 与 ε-greedy 进行比较。

### 4. 为多臂老虎机问题实现 UCB。利用置信界平衡探索与利用，并将其性能与其他探索策略进行比较。

### 5. 模拟一个离散 MDP，其中智能体随时间与环境交互。实现价值迭代或策略迭代算法，以针对不同的奖励结构和状态转移动态寻找最优策略。

### 6. 实现 Q-learning 或 DQN，利用原始像素输入玩经典 Atari 游戏。使用帧堆叠和帧跳过等技术预处理观测值。

### 7. 实现带有 UCB 的情境老虎机，根据用户上下文推荐个性化物品。使用合成或真实世界数据评估 UCB 与其他老虎机算法相比的有效性。

## 问题

1.  什么是强化学习，它与监督学习和无监督学习有何不同？

2.  解释强化学习中智能体、环境、状态、动作和奖励的概念。

3.  什么是 MDP，为什么它在强化学习中很重要？

4.  描述策略在强化学习中的作用。什么是确定性策略和随机策略？

5.  基于价值和基于策略的强化学习方法有什么区别？

6.  解释强化学习中探索与利用的概念。它如何影响智能体的学习过程？

7.  强化学习中的 Q 值、V 值和贝尔曼方程是什么？

8.  描述 Q-learning 算法的主要组成部分。它是如何工作的，解决了什么问题？

9.  解释强化学习中函数逼近的概念。它在深度 Q 网络中是如何使用的？

10. 强化学习算法有哪些常见挑战或局限性？

11. 描述强化学习在现实场景中的一些应用。

12. 解释强化学习中在线策略学习和离线策略学习的区别。

13. 基于模型与无模型强化学习方法各有什么优缺点？

14. 时序差分方法（如 SARSA 和 Q-learning）在更新规则和收敛性质上有何不同？

15. 讨论不同探索策略（如 ε-greedy、Softmax 和 UCB）之间的权衡。

# 第 10 章 项目

## 简介

在前几章中，我们详细探讨了机器学习及其类型和模型。尽管前几章已通过编程示例探讨了多种机器学习方法，但本章将利用保存在 CSV 文件中的数据集，探讨一个心脏病预测的现实问题。本章提供了从 [www.kaggle.com](https://www.kaggle.com) 获取的 `heart_disease` 数据集的详细分析，包括其中包含的信息、列数、分类列、数值列、数据预处理、数据集列与目标变量的关联、数据集不同列间的相关性等。随后，在预处理后，应用了五个主要模型对数据集进行分类、预测和准确率评估。这些模型分别是逻辑回归、K 近邻、决策树、随机森林和 AdaBoost。特此说明，该项目基于监督学习，目标值已给出。目标值 1 代表疾病存在，目标值 0 代表疾病不存在。评估数据集的其他列与目标变量的关联，以确定系统的准确性并验证预测。模型提供的输出揭示了上述各模型的性能。

## 结构

本章涵盖以下主题：

*   详细的机器学习项目

## 目标

本章旨在使读者/学习者熟悉疾病预测、准确率和分类的现实问题。用户可以替换为自己的数据集以查看结果。通过学习本章，可以使用机器学习技术构建分类模型，用于预测和评估准确率。

## 详细机器学习项目

为了基于各种参数（如 `age`、`sex`、`cp`、`trestbps`、`chol`、`fbs`、`restecg`、`thalach`、`exang`、`oldpeak`、`slope`、`ca`、`thal`、`target`）分析和预测某人是否可能患有心脏病。所有这些参数均存在名为 `heart.csv` 的数据集中。

完整的分步代码始于 [代码 10.1](#ch10.xhtml#cd10-1)。您可以按顺序阅读，以深入了解机器学习模型构建。在模型构建的第一部分，导入项目顺利执行所需的所有必要库。在本项目中，数据集从 csv 文件读取。您可以在项目开始时导入必要的库，也可以在项目开发过程中根据需要导入。

最初，名为 `heart.csv` 的心脏病数据集被读入名为 `data` 的数据框中，如 [代码 10.1](#ch10.xhtml#cd10-1) 所示。此后，所有计算和处理均在该数据框上执行。调用 `data.info()` 方法以获取数据集信息，它提供完整信息，如数据集条目数、各自的类型和列名。正如我们所见，数据集中有 14 列、303 个条目，其类型均为 `int64` 或 `float64`。

**代码 10.1：读取数据集文件**

```python
import pandas as pd

from sklearn.model_selection import train_test_split

from sklearn.metrics import accuracy_score, classification_report

# Load the dataset
data = pd.read_csv('e:/dataset/heart.csv') # heart.csv dataset is read into a dataframe named data
data.info() # the information of the dataset is retrieved
```

请参考 [图 10.1](#ch10.xhtml#fig10-1) 查看代码输出：

![](images/10.1.png)

图 10.1：代码 10.1 的输出

此后，调用 `data.head()` 方法以获取数据集列的值，如 [代码 10.2](#ch10.xhtml#cd10-2) 所示。默认显示前五行作为输出，其中最后一列为目标变量。目标变量可以是 1 或 0。1 表示存在心脏病，0 表示无疾病。

**代码 10.2：读取数据集文件的前几行**

```python
data.head() # the heads of each column of dataset are retrieved
```

请参考 [图 10.2](#ch10.xhtml#fig10-2) 查看代码输出：

![](images/10.2.png)

图 10.2：代码 10.2 的输出

此后，创建 `grab_col_name()` 函数以获取数据集的观察情况，如 [代码 10.3](#ch10.xhtml#cd10-3) 所示。从输出中我们可以看到，共有 303 个条目、14 列，其中包含 5 个数值列和 9 个分类列。注意，在 14 列中，有 9 列被假定为分类列，尽管它们表现为数值，例如 `sex` 列。

**代码 10.3：获取数据集的详细观察情况**

```python
# detailed observations of the dataset are retrieved by the following #function
def grab_col_name(data, cat_nbr=10, car_nbr=20):
    cat_col = [col for col in data.columns if data[col].dtypes =="O"]
    num_but_cat = [col for col in data.columns if data[col].dtypes !="O" and data[col].nunique() < cat_nbr]
    cat_but_car = [col for col in data.columns if data[col].dtypes == 'O' and data[col].nunique() > car_th]
```

