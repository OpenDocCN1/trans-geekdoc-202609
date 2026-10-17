
该函数的目的是自动化决策树分类器的训练和超参数调优过程。通过在一系列超参数上进行网格搜索，该函数有助于识别表现最佳的模型配置。随后，该调优模型可用于分类任务，与默认参数设置相比，可能提高准确率和预测性能。

然后，在 `Machine_Learning` 类中，定义一个名为 `implement_DT()` 的新方法：

```python
def implement_DT(self, chosen, X_train, X_test, y_train, y_test):
    file_path = os.getcwd() + "/DT_Model.pkl"

    if os.path.exists(file_path):
        model = joblib.load('DT_Model.pkl')
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    else:
        model = self.decision_trees(chosen, X_train, X_test, y_train, y_test)
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)

    # Saves result into excel file
    self.obj_data.save_result(y_test, y_pred, "results_DT.csv")

    print("Training Decision Trees done...")

    return model, y_pred
```

`implement_DT()` 函数负责训练和使用决策树分类器进行二分类任务。让我们分析其组成部分和功能：

### 函数参数

*   `chosen`：代表所选分类模型或标识符的字符串。
*   `X_train`、`X_test`、`y_train`、`y_test`：训练和测试数据的划分，包含特征矩阵（`X_train` 和 `X_test`）和目标向量（`y_train` 和 `y_test`）。

### 文件路径检查

该函数检查当前工作目录（`os.getcwd()`）下是否存在名为 `'DT_Model.pkl'` 的文件。该文件假定包含一个预训练的决策树模型。

### 模型加载或训练

*   如果 `'DT_Model.pkl'` 文件存在，函数使用 `joblib` 加载预训练模型（`joblib.load`）。
*   否则，它通过调用 `decision_trees()` 函数来训练一个决策树分类器。
*   此过程的结果是训练好的模型，存储在变量 `model` 中。

### 模型预测

*   函数通过调用 `run_model()` 函数并设置 `proba=True`，使用训练好的模型对测试数据（`X_test`）进行预测。
*   预测的标签或概率存储在变量 `y_pred` 中。

### 保存结果

真实标签（`y_test`）和预测标签（`y_pred`）通过 `obj_data` 对象的 `save_result` 方法保存到名为 `"results_DT.csv"` 的 Excel 文件中。

### 打印确认信息

打印一条消息，表明决策树训练已完成。

### 返回模型和预测结果

训练好的模型（`model`）和相应的预测结果（`y_pred`）从函数中返回。

该函数的目的是为训练和使用决策树分类器提供统一接口。如果有预训练模型可用，则可以加载并用于预测。否则，将使用提供的训练数据训练新模型。然后函数保存结果，并返回模型和预测结果以供进一步分析或评估。

可以使用各种评估指标（如准确率、精确率、召回率和 F1 分数）来评估模型性能，这些指标可基于 `y_test`（真实标签）和 `y_pred`（预测标签）计算得出。

然后，在 `Helper_Plot` 类中，将以下代码添加到 `choose_plot_ML()` 方法的末尾：

```python
if chosen == "Decision Trees":
    best_model, y_pred = self.obj_ml.implement_DT(chosen, X_train, X_test, y_train, y_test)
    # Plots confusion matrix and ROC
    self.plot_cm_roc(best_model, X_test, y_test, y_pred, chosen, figure1, canvas1)
    # Plots true values versus predicted values diagram and learning curve
    self.plot_real_pred_val_learning_curve(best_model, X_train, y_train, X_test, y_test, y_pred, chosen, figure2, canvas2)
    # Shows table of result
    df_lr = self.obj_data.read_dataset("results_DT.csv")
    self.shows_table(root, df_lr, 450, 750, "Y_test and Y_pred of Decision Trees")
```

该代码块是一个条件语句，用于检查选定的机器学习模型是否为 "Decision Trees"。如果是，则执行一系列与训练、评估和显示决策树分类器结果相关的操作。让我们分解代码的每个部分：

#### 1. 条件检查

代码检查变量 `chosen`（代表选定的机器学习模型）的值是否等于字符串 "Decision Trees"。

#### 2. 模型训练与预测

如果满足条件（即选定的模型是决策树），则调用 `implement_DT()` 函数来训练并获取决策树分类器的预测结果。该函数返回两个值：`best_model`（训练好的模型）和 `y_pred`（模型在测试数据上的预测结果）。

#### 3. 可视化与评估

获得训练好的模型和预测结果后，代码执行以下操作：

*   使用 `plot_cm_roc()` 函数绘制决策树分类器的混淆矩阵和 ROC 曲线。这些可视化有助于从分类准确率以及真正例率与假正例率的权衡方面评估模型性能。
*   使用 `plot_real_pred_val_learning_curve()` 函数绘制真实值与预测值对比图以及学习曲线。这些可视化提供了关于模型行为及其泛化新数据能力的见解。
*   使用 `obj_data.read_dataset()` 方法读取 "results_DT.csv" 文件以显示结果表。该表包含与决策树模型相关的评估指标和性能统计数据。

#### 4. 结果显示

代码可能会将结果（如可视化图表和表格）显示在用户界面（UI）中，或与图形用户界面（GUI）工具包（如 Tkinter）交互以供用户操作。

总的来说，该代码块代表了当决策树分类器被选为机器学习模型时，用于训练、评估和可视化结果的逻辑。其目的是提供关于模型性能的见解，并根据模型的预测和评估指标帮助用户做出明智决策。

运行 `main_class.py`。接下来，点击 SPLIT DATA 按钮。然后，选择 Decision Trees 以查看使用决策树分类器的结果，如图 34 所示。

![Image](img/image-4.png)

**Figure 34** The results of using Decision Trees classifier

Output:

```
Decision Trees
accuracy: 0.8636959370904325
recall: 0.8636959370904325
precision: 0.8641929000245966
f1: 0.8636533127958457
 precision recall f1-score support
 0 0.88 0.85 0.86 382
 1 0.85 0.88 0.87 381
 accuracy 0.86 763
 macro avg 0.86 0.86 0.86 763
 weighted avg 0.86 0.86 0.86 763
```

让我们详细分析 "Decision Trees" 模型并得出具体结论：

**分析：**

1.  **准确率**：模型达到了 86.37% 的准确率，表现相当不错。这意味着它在测试数据集中正确分类了约 86.37% 的总实例。
2.  **召回率**：召回率得分为 0.8637，也称为灵敏度或真正例率。这意味着模型正确识别了数据集中约 86.37% 的实际正例（响应客户）。在识别所有正例至关重要的场景中，较高的召回率是理想的。
3.  **精确率**：精确率得分为 0.8642。这表明在所有被预测为正例（响应客户）的实例中，约 86.42% 是真正例。精确率衡量模型做出准确正例预测的能力。
4.  **F1 分数**：F1 分数为 0.8637。F1 分数是精确率和召回率的调和平均数，提供了模型性能的平衡度量。在本例中，它表明精确率和召回率之间达到了良好的平衡。
5.  **类别特定指标**：
    *   **类别 0（响应）**：
        *   精确率：0.88
        *   召回率：0.85
        *   F1 分数：0.86
    *   **类别 1（不响应）**：
        *   精确率：0.85
        *   召回率：0.88
        *   F1 分数：0.87
    这些类别特定指标显示模型对响应和不响应客户的表现相似，两个类别的精确率和召回率均衡。
6.  **宏平均与加权平均**：考虑类别平衡的宏平均 F1 分数约为 0.86。考虑类别不平衡的加权平均 F1 分数也约为 0.86。这些值表明模型在各类别上的表现一致。

**结论：**

"Decision Trees" 机器学习模型在给定的分类任务中表现良好。它达到了约 86.37% 的准确率，并在响应和不响应客户类别上表现出均衡的精确率和召回率。这种平衡表明模型能有效正确识别这两类客户，使其成为该任务的合适选择。

模型在不同评估指标和类别特定度量上的一致性能进一步支持了其可靠性。因此，基于提供的结果，"Decision Trees" 模型可被视为对客户响应性进行分类的稳健有效解决方案。

### 梯度提升分类器与网格搜索

在 `Machine_Learning` 类中，定义一个名为 `gradient_boosting()` 的新方法，如下所示：

```python
def gradient_boosting(self, name, X_train, X_test, y_train, y_test):
    # Gradient Boosting Classifier
    # Initialize the GradientBoostingClassifier model
    gbt = GradientBoostingClassifier(random_state=2021)
    # Define the parameter grid for the grid search
    param_grid = {
        'n_estimators': [100, 200, 300],
        'max_depth': [10, 20, 30],
        'subsample': [0.6, 0.8, 1.0],
        'max_features': [0.2, 0.4, 0.6, 0.8, 1.0],
    }
    # Create GridSearchCV with the GradientBoostingClassifier model and the parameter grid
    grid_search = GridSearchCV(gbt, param_grid, cv=3, scoring='accuracy', n_jobs=-1)
    # Train and perform grid search
    grid_search.fit(X_train, y_train)
    # Get the best GradientBoostingClassifier model from the grid search
    best_model = grid_search.best_estimator_
    # Saves model
    joblib.dump(best_model, 'GB_Model.pkl')
    # Print the best hyperparameters found
    print(f"Best Hyperparameters for GB:")
    print(grid_search.best_params_)
    return best_model
```

这段代码定义了一个名为 `gradient_boosting()` 的函数，用于训练和超参数调优梯度提升分类器。让我们逐步分解代码：

#### 1. `gradient_boosting` 方法

```python
def gradient_boosting(self, name, X_train, X_test, y_train, y_test):
```

该函数接收以下参数：

*   `name`：模型名称，用于标记或日志记录。
*   `X_train`, `X_test`：训练集和测试集特征数据。
*   `y_train`, `y_test`：对应的训练集和测试集目标标签。

##### 1.1 初始化模型

```python
gbt = GradientBoostingClassifier(random_state=2021)
```

初始化一个梯度提升分类器（`gbt`），固定 `random_state=2021` 以保证可复现性。

##### 1.2 定义超参数网格

```python
param_grid = { ... }
```

定义用于超参数调优的参数网格，包含以下超参数的不同取值：

*   `n_estimators`：提升阶段的数量（树的数量）。
*   `max_depth`：集成中每棵树的最大深度。
*   `subsample`：用于拟合树的样本比例。
*   `max_features`：用于拟合树的特征比例。

##### 1.3 网格搜索与交叉验证

```python
grid_search = GridSearchCV(gbt, param_grid, cv=3, scoring='accuracy', n_jobs=-1)
```

创建 `GridSearchCV` 对象（`grid_search`）进行超参数调优：

*   `gbt`：待调优的模型。
*   `param_grid`：超参数搜索空间。
*   `cv=3`：3 折交叉验证。
*   `scoring='accuracy'`：以准确率作为评估指标。
*   `n_jobs=-1`：使用所有可用 CPU 核心并行加速搜索。

##### 1.4 训练与最佳模型获取

```python
grid_search.fit(X_train, y_train)
best_model = grid_search.best_estimator_
```

在训练数据上拟合 `grid_search` 以寻找最佳超参数，并通过 `best_estimator_` 获取最佳模型。

##### 1.5 模型持久化与结果输出

```python
joblib.dump(best_model, 'GB_Model.pkl')
print(f"Best Hyperparameters for GB:")
print(grid_search.best_params_)
```

将最佳模型保存为 `GB_Model.pkl`，并打印最佳超参数。

> **说明**：此代码属于机器学习工作流的一部分，用于训练和调优梯度提升分类器。

---

#### 2. `implement_GB` 方法

```python
def implement_GB(self, chosen, X_train, X_test, y_train, y_test):
    file_path = os.getcwd() + "/GB_Model.pkl"
    if os.path.exists(file_path):
        model = joblib.load('GB_Model.pkl')
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    else:
        model = self.gradient_boosting(chosen, X_train, X_test, y_train, y_test)
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    # Saves result into excel file
    self.obj_data.save_result(y_test, y_pred, "results_GB.csv")
    print("Training Gradient Boosting done...")
    return model, y_pred
```

##### 2.1 功能概述
