

![](img/bd21298357d8484151447cff0b2f138b_105_0.png)

图 3.17 – Jupyter Notebook

(b) 点击 Lab1-bankchurn 文件夹，你将看到 churn.csv 文件。

- 3. 实验与模型构建：现在，让我们在 Jupyter Notebook 环境中创建一个新的数据科学笔记本。要做到这一点，点击 New（新建）下拉菜单并选择 Python 3（见下方的截图）：

![](img/bd21298357d8484151447cff0b2f138b_105_1.png)

图 3.18 – 创建新的 Jupyter notebook

- 4. 你将看到一个与下方截图类似的界面。这是一个空白笔记本，我们将用它来探索和构建模型。**In []:** 之后的后续部分被称为 *cell*（单元格），我们将代码输入到单元格中。要运行单元格中的代码，你需要点击工具栏上的 **Run**（运行）按钮。要添加新单元格，请点击工具栏上的 + 按钮：

![](img/bd21298357d8484151447cff0b2f138b_106_0.png)

图 3.19 – 空白 Jupyter notebook

- 5. 首先，让我们通过以下代码块配置 Jupyter 环境以使用正确的 Python 库：在第一个空白单元格中输入该代码，并点击工具栏上的 **Run** 按钮运行单元格。*sys.executable* 指向我们之前安装的 Python3 位置。这里，*sys.path* 需要包含安装额外库包的附加路径。注意，此代码块仅适用于 Mac。在 PC 上无须运行此代码：

```python
import sys
sys.executable = "/usr/local/bin/python3"
sys.path = sys.path + ['/usr/local/lib/python3.9/site-packages']
```

- 6. 点击工具栏上的 + 按钮添加新单元格，在第一个空白单元格中输入代码块，并点击工具栏上的 **Run** 按钮运行单元格。此代码下载了用于数据处理（**pandas**）、可视化（**matplotlib**）以及模型训练与评估（scikit-learn）的多个 Python 包。我们将在*第5章，开源机器学习库*中详细介绍 scikit-learn。我们将在后续章节中使用这些包：

```python
!pip3 install pandas
!pip3 install matplotlib
!pip3 install scikit-learn
```

- 7. 现在，我们可以加载并探索数据。在新单元格中添加以下代码块以加载 Python 库包并从 churn.csv 文件加载数据。你将看到一个有 14 列的表格，其中 Existing 列是目标列：

```python
import pandas as pd
churn_data = pd.read_csv("churn.csv")
churn_data.head()
```

- 8. 你可以使用多种工具探索数据集，并使用后续命令了解信息，例如数据集统计数据、不同特征之间的两两相关性以及数据分布。describe() 函数返回每个数值列的基本统计信息，如均值、标准差、最小值和最大值。hist() 函数为所选列绘制直方图，corr() 计算数据中不同特征之间的相关性矩阵。尝试在一个新的单元格中逐一运行以理解数据：

```python
# 以下命令计算各个特征的各种统计数据
for features.
churn_data.describe()
# 下一个命令显示不同特征的直方图
# 你可以替换列名来绘制直方图
for other features
churn_data.hist(['CreditScore', 'Age', 'Balance'])
# 下一个命令计算特征之间的相关性
churn_data.corr()
```

- 9. 数据集需要进行转换才能用于模型训练。以下代码块将把 Geography 和 Gender 的值从分类字符串转换为序数，以便之后供 ML 算法处理。请注意，模型的准确性不是本次练习的主要目的，我们进行序数转换仅用于演示。请在新单元格中复制并运行以下代码块：

```python
from sklearn.preprocessing import OrdinalEncoder
encoder_1 = OrdinalEncoder()
encoder_2 = OrdinalEncoder()
churn_data['Geography_code'] = encoder_1.fit_transform(churn_data[['Geography']]])
churn_data['Gender_code'] = encoder_2.fit_transform(churn_data[['Gender']]])
```

- 10. 模型训练需要一些列。我们可以使用以下代码块删除它们：

```python
churn_data.drop(columns=['Geography', 'Gender', 'RowNumber', 'Surname'], inplace=True)
```

- 11. 现在，数据集只剩下我们关心的特征。接下来，我们需要对数据进行划分以用于训练和验证。我们还通过将目标变量 Exited 与其他输入特征分离来准备每个数据集。在新单元格中输入并运行以下代码块：

```python
# 我们导入 train_test_split 类用于数据划分
from sklearn.model_selection import train_test_split

# 将数据集划分为训练集(80%)和测试集(20%)
X_train, X_test, y_train, y_test = train_test_split(churn_data.drop('Exited', axis=1), churn_data['Exited'], test_size=0.2)
```

- 12. 现在，我们准备好训练模型了。在新单元格中输入并运行以下代码块。在这里我们将使用随机森林算法来训练模型：

```python
# 我们使用 RandomForest 算法训练模型
from sklearn.ensemble import RandomForestClassifier
model_clf = RandomForestClassifier(max_depth=2, random_state=0)
model_clf.fit(X_train, y_train)
```

- 13. 最后，我们将使用测试集测试模型的准确性。在这里我们获取模型返回的预测值，并使用 accuracy_score 根据预测值 (churn_prediction) 和真实值 (y_test) 计算准确性：

```python
# 我们使用 sklearn 库中的 accuracy_score 类计算准确性
from sklearn.metrics import accuracy_score

# 我们使用训练模型对测试集生成预测
churn_prediction = model_clf.predict(X_test)

# 我们使用 accuracy_score 测量准确性
accuracy_score(y_test, churn_prediction)
```

恭喜！你成功在本地安装了数据科学环境并使用随机森林算法训练了模型。你验证了机器学习方法可以解决这个问题。

# 总结

本章介绍了用于解决不同类型机器学习任务的多种算法。你现在应该了解哪些算法适用于哪些机器学习问题。你还在本地创建了简单的数据科学环境，使用了 scikit-learn 机器学习库进行数据探索和准备，并训练了机器学习模型。

在下一章中，我们将讨论数据管理如何与机器学习生命周期交叉，并在 AWS 上构建数据管理平台。

# 4 机器学习的数据管理

作为一名**机器学习 (ML)** 解决方案架构师，我经常被请求为机器学习负载的数据管理平台提供架构建议。虽然数据管理平台架构主要被认为是一个独立的学科领域，但它是机器学习负载不可或缺的一部分。为了设计全面的机器学习平台，ML 架构师需要熟悉机器学习的关键数据考虑因素，并了解数据管理的技术细节，以满足数据科学家和自动化机器学习流水线的需求。在本章中，我们将研究数据管理与机器学习交叉点。我们将讨论设计机器学习数据管理平台的关键考虑因素。然后，我们将深入数据管理平台的核心架构组件，以及在 AWS 上构建数据管理平台相关的 **AWS** 技术和服务。最后，你将进行实际操作，在 AWS 上创建一个支持**数据目录**管理、**数据发现**和**数据处理**工作流的**数据湖**。

