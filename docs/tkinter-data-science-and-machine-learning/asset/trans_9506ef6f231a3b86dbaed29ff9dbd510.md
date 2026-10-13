

# 从网格搜索获取最佳逻辑回归模型

```python
best_model = grid_search.best_estimator_
```

# 保存模型

```python
joblib.dump(best_model, 'LR_Model.pkl')
```

# 打印找到的最佳超参数

```python
print(f"Best Hyperparameters for LR:")
print(grid_search.best_params_)
```

```python
return best_model
```

`Machine_Learning` 类中的 `logistic_regression()` 方法负责通过网格搜索进行超参数调优来训练逻辑回归分类器。以下是该方法的分步解释：

## 1. 方法参数

*   `name`：表示正在训练的模型名称或标识符的字符串（例如 "Logistic Regression"）。
*   `X_train`：训练数据的特征矩阵。
*   `X_test`：测试数据的特征矩阵。
*   `y_train`：训练数据的目标标签。
*   `y_test`：测试数据的目标标签。

## 2. 用于超参数调优的网格搜索

定义了一个参数网格 (`param_grid`)，指定了逻辑回归分类器的一系列超参数。这包括正则化强度 (`C`)、惩罚类型 (`penalty`) 和求解器方法 (`solver`) 的不同值。

## 3. 逻辑回归模型初始化

使用一些配置初始化了一个逻辑回归分类器 (`logreg`)，包括最大迭代次数和随机种子。`max_iter` 参数设置为 5000 以确保求解器收敛，`random_state` 设置为 2021 以保证可复现性。

## 4. 交叉验证网格搜索

使用 `GridSearchCV` 执行带有交叉验证的网格搜索。它接收初始化的逻辑回归模型 (`logreg`)、参数网格 (`param_grid`)、交叉验证折数 (`cv=3`)、评分指标 (`scoring='accuracy'`) 以及并行化搜索的选项 (`n_jobs=-1`)。

## 5. 训练与模型选择

使用训练数据 (`X_train`, `y_train`) 调用网格搜索对象 (`grid_search`) 的 `fit()` 方法，以训练具有不同超参数组合的多个逻辑回归模型。

## 6. 最佳模型选择

使用 `grid_search.best_estimator_` 获取具有最优超参数的表现最佳的逻辑回归模型。

## 7. 模型保存

使用 `joblib.dump` 方法将表现最佳的逻辑回归模型保存到名为 `LR_Model.pkl` 的 pickle 文件中。这使得模型可以在以后重复使用，而无需重新训练。

## 8. 打印最佳超参数

该方法打印在逻辑回归分类器的网格搜索过程中找到的最佳超参数。

## 9. 返回值

表现最佳的逻辑回归模型作为该方法的输出返回。

总的来说，该方法自动化了逻辑回归分类器的超参数调优过程，确保模型使用网格搜索期间找到的最佳超参数进行训练。

然后，在 `Machine_Learning` 类中，定义一个名为 `implement_LR()` 的新方法，如下所示：

```python
def implement_LR(self, chosen, X_train, X_test, y_train, y_test):
    file_path = os.getcwd() + "/LR_Model.pkl"
    if os.path.exists(file_path):
        model = joblib.load('LR_Model.pkl')
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    else:
        model = self.logistic_regression(chosen, X_train, X_test, y_train, y_test)
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    # 将结果保存到 excel 文件
    self.obj_data.save_result(y_test, y_pred, "results_LR.csv")
    print("Training Logistic Regression done...")
    return model, y_pred
```

`Machine_Learning` 类中的 `implement_LR()` 方法负责为给定数据集和选定类别（目标变量）实现逻辑回归分类器。以下是该方法的分步解释：

## 1. 方法参数

*   `chosen`：表示选定类别或目标变量的字符串。
*   `X_train`：训练数据的特征矩阵。
*   `X_test`：测试数据的特征矩阵。
*   `y_train`：训练数据的目标标签。
*   `y_test`：测试数据的目标标签。

## 2. 检查预训练模型

该方法通过构建 `LR_Model.pkl` 的文件路径并使用 `os.path.exists(file_path)`，检查当前工作目录中是否存在预训练的逻辑回归模型。

## 3. 模型加载或训练

*   如果存在预训练模型，则使用 `joblib.load('LR_Model.pkl')` 加载它。否则，调用 `logistic_regression` 方法通过超参数调优训练一个新的逻辑回归模型。
*   无论模型是被加载还是被训练，都将存储在 `model` 变量中。

## 4. 模型评估与预测

*   调用 `run_model()` 方法在测试数据 (`X_test`, `y_test`) 上评估模型性能。`proba` 参数设置为 `True`，表示应计算类别预测的概率分数。
*   预测的类别概率或标签存储在 `y_pred` 变量中。

## 5. 保存模型结果

该方法使用 `Process_Data` 类 (`self.obj_data`) 的 `save_result()` 方法将模型结果（包括实际标签和预测标签）保存到名为 `results_LR.csv` 的 Excel 文件中。

## 6. 打印状态

打印一条消息以指示逻辑回归模型的训练或加载已完成。

## 7. 返回值

训练或加载的逻辑回归模型 (`model`) 和预测的类别概率或标签 (`y_pred`) 作为输出返回。

总的来说，此方法允许您根据选定类别加载预训练的逻辑回归模型或训练一个新模型，然后在测试数据上评估其性能，同时保存结果以供进一步分析。

然后，在 `Helper_Plot` 类中，定义一个名为 `choose_plot_ML()` 的新方法，如下所示：

```python
def choose_plot_ML(self, root, chosen, X_train, X_test, y_train, y_test, figure1, canvas1, figure2, canvas2):
    if chosen == "Logistic Regression":
        best_model, y_pred = self.obj_ml.implement_LR(chosen, X_train, X_test, y_train, y_test)
        # 绘制混淆矩阵和 ROC
        self.plot_cm_roc(best_model, X_test, y_test, y_pred, chosen, figure1, canvas1)
        # 绘制真实值与预测值对比图和学习曲线
        self.plot_real_pred_val_learning_curve(best_model, X_train, y_train,
                                               X_test, y_test, y_pred, chosen, figure2, canvas2)
        # 显示结果表格
        df_lr = self.obj_data.read_dataset("results_LR.csv")
        self.shows_table(root, df_lr, 450, 750, "Y_test and Y_pred of Logistic Regression")
```

`choose_plot_ML()` 方法负责选择并显示与所选机器学习算法相关的特定图表和可视化。以下是该方法工作原理的细分：

## 1. 方法参数

*   `root`：将在其中显示图表和表格的 Tkinter 根窗口。
*   `chosen`：表示所选机器学习算法的字符串。
*   `X_train`：训练数据的特征矩阵。
*   `X_test`：测试数据的特征矩阵。
*   `y_train`：训练数据的目标标签。
*   `y_test`：测试数据的目标标签。
*   `figure1`：用于第一组图表的 Matplotlib 图形对象。
*   `canvas1`：与 `figure1` 关联的 Matplotlib 画布对象。
*   `figure2`：用于第二组图表的 Matplotlib 图形对象。
*   `canvas2`：与 `figure2` 关联的 Matplotlib 画布对象。

## 2. 基于所选算法的条件块

该方法检查 `chosen` 变量的值以确定选择了哪种机器学习算法。

## 3. 逻辑回归（所选算法）

