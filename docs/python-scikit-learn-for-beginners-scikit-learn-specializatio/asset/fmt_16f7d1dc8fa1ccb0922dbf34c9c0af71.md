
# 5.3. Multi-output Regression Problems

正如之前所解释的，多输出回归是一种回归类型，你需要在输出中预测多个连续值。让我们创建一个包含 2,000 条记录、8 个特征和 3 个输出值的虚拟数据集。为此，你可以执行以下脚本。该脚本还会打印数据集中特征（`X`）和标签（`y`）的形状。

**Script 20:**
```
![](Image00238.jpg)
```
**Output:**
```
(2000, 8) (2000, 3)
```
输出显示你有 2,000 条记录，包含 8 个特征和 3 个输出。因此，这是一个多输出回归问题。让我们将虚拟数据集划分为训练集和测试集，并对其进行特征缩放。

**Script 21:**
```
![](Image00239.jpg)
```
Scikit-learn 库中的一些算法默认支持多输出回归。例如，你可以直接使用 `Linear Regression` 和 `Random Forest Regression` 来预测多输出回归值，无需任何修改。

## 5.3.1 Linear Regression for Multi-output Regression

从下面的输出可以看出，你不需要对线性回归算法做任何更改，即可对具有多个回归输出的数据集进行预测。

**Script 22:**
```
![](Image00240.jpg)
```
**Output:**
```
Mean Absolute Error: 0.24400622004095515
Mean Squared Error: 0.09288200051053495
Root Mean Squared Error: 0.3047654844475256
```
以下脚本对单个测试点进行预测。

**Script 23:**
```
![](Image00241.jpg)
```
输出显示了预测输出和实际输出。你可以看到输出中现在有三个值，因为这是一个多输出回归问题。

**Output:**
```
[[52.14499321 154.07153888 29.65411176]]
[50.3331556 155.43458476 26.52621361]
```

## 5.3.2 Random Forest for Multi-output Regression

以下脚本展示了如何使用 `Random Forest Regressor` 进行多输出回归。你可以看到，该脚本与单输出回归问题的脚本没有任何区别。

**Script 24:**
```
![](Image00242.jpg)
```
**Output:**
```
Mean Absolute Error: 17.578462377518566
Mean Squared Error: 737.569952450891
Root Mean Squared Error: 27.158239126476722
```
以下脚本使用训练好的 `Random Forest Regressor` 算法对单个数据点进行预测。

**Script 25:**
```
![](Image00243.jpg)
```
**Output:**
```
[[15.29925902 114.41624666 12.90183432]]
[50.3331556 155.43458476 26.52621361]
```
一些算法（如支持向量机，在回归问题中也称为支持向量回归器 `SVR`）无法默认对具有多个回归输出的数据集进行预测。在这种情况下，你有两个选择。你可以使用直接多类输出包装器算法进行回归，或者使用链式多输出包装器算法进行回归。

# 5.4. Direct Multi-output Regression with Wrapper Algorithms

在直接多类输出回归包装器算法中，每一个多输出回归标签都被视为单独的标签。因此，如果你有三个输出标签 `y1`、`y2` 和 `y3`，以及一个特征集 `X`，直接包装器算法将在后台训练三个单独的模型，每个模型使用特征集 `X` 预测输出标签 `y1`、`y2` 和 `y3`。

要实现直接多输出回归，你可以使用 Sklearn 库 `multioutput` 模块中的 `MultiOutputRegressor` 类。你想要训练的算法作为参数传递给 `MultiOutputRegressor` 类。以下脚本使用 `MultiOutputRegressor` 类配合 `SVR` 回归模型对多输出数据集进行预测。一旦将 `SVR` 类传递给 `MultiOutputRegressor` 类对象，其余过程就类似于使用常见算法进行预测。你必须将特征集和标签集传递给 `MultiOutputRegressor` 类的 `fit` 方法。

**Script 26:**
```
![](Image00244.jpg)
```
**Output:**
```
Mean Absolute Error: 0.24566521365979566
Mean Squared Error: 0.09412825912574384
Root Mean Squared Error: 0.30680329060449113
```
最后，你也可以使用直接多输出回归包装器算法对单个数据点进行预测，如以下脚本所示。

**Script 27:**
```
![](Image00245.jpg)
```
**Output:**
```
[[52.10616073 154.0113967 29.64235478]]
[50.3331556 155.43458476 26.52621361]
```

# 5.5. Chained Multi-output Regression with Wrapper Algorithms

在链式多类输出回归中，每个类的输出预测是增量式的。例如，如果你有一个特征集 `X` 和输出标签 `y1`、`y2` 和 `y3`，在第一次增量中，算法使用特征集 `X` 预测 `y1`。在下一次迭代中，特征集 `X` 和先前预测的 `y1` 值被连接起来并用于预测 `y2`。在下一次迭代中，特征集 `X` 和 `y2` 的预测值被用于预测 `y3`。

要对多输出回归问题进行预测，你可以使用 Sklearn 库 `multioutput` 模块中的 `RegressorChain` 类，如下所示。基础算法连同你想要按顺序或链式预测的输出类别顺序一起传递给 `RegressorChain` 类。以下脚本使用 `LinearSVR` 算法配合 `RegressorChain` 包装器进行多类输出回归预测。

**Script 28:**
```
![](Image00246.jpg)
```
**Output:**
```
Mean Absolute Error: 0.2999883276581629
Mean Squared Error: 0.14873277575291557
Root Mean Squared Error: 0.3856588852249039
```
最后，以下脚本展示了如何使用 `LinearSVR` 算法配合 `RegressorChain` 包装器对单个数据点进行预测。

**Script 29:**
```
![](Image00247.jpg)
```
**Output:**
```
[[52.11002869 154.00609972 29.12383881]]
[50.3331556 155.43458476 26.52621361]
```
在下一章中，你将看到如何使用 Scikit (Sklearn) 库中的机器学习算法解决分类问题。

---

## Hands-on Time - Exercise

现在轮到你了。按照下面练习中的说明操作，以检查你对机器学习中回归算法的理解。这些问题的答案在本书末尾给出。

### Exercise 5.1

**Question 1** Which one of the following is an example of a regression output?
1. True
2. Red
3. C.
4. D.

**Question 2** Which one of the following algorithms is a lazy algorithm?
1. Random Forest
2. KNN
3. C.
4. D.

**Question 3** Which one of the following algorithms is not a regression metric?
1. Accuracy
2. Recall
3. C.
4. D.

### Exercise 5.2

Using the ‘Diamonds’ dataset from the Seaborn library, train a regression algorithm of your choice, which predicts the price of the diamond. Perform all the preprocessing steps.
