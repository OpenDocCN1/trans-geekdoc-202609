
*   `y_test`：测试数据的目标标签。

## 2. 用于超参数调优的网格搜索

定义了一个参数网格（`param_grid`），指定了逻辑回归分类器的一系列超参数。这包括正则化强度（`C`）、惩罚类型（`penalty`）和求解器方法（`solver`）的不同值。

## 3. 逻辑回归模型初始化

使用一些配置初始化了一个逻辑回归分类器（`logreg`），包括最大迭代次数和随机种子。`max_iter` 参数设置为 5000 以确保求解器收敛，`random_state` 设置为 2021 以保证可复现性。

## 4. 交叉验证网格搜索

使用 `GridSearchCV` 执行带有交叉验证的网格搜索。它接收初始化的逻辑回归模型（`logreg`）、参数网格（`param_grid`）、交叉验证折数（`cv=3`）、评分指标（`scoring='accuracy'`）以及并行化搜索的选项（`n_jobs=-1`）。

## 5. 训练与模型选择

使用训练数据（`X_train`、`y_train`）调用网格搜索对象（`grid_search`）的 `fit()` 方法，以训练具有不同超参数组合的多个逻辑回归模型。

### 6. 最佳模型选择

使用 `grid_search.best_estimator_` 获取具有最优超参数的表现最佳的逻辑回归模型。

### 7. 模型保存

使用 `joblib.dump` 方法将表现最佳的逻辑回归模型保存到名为 `LR_Model.pkl` 的 pickle 文件中。这使得模型可以在以后重复使用，而无需重新训练。

### 8. 打印最佳超参数

该方法打印在逻辑回归分类器的网格搜索过程中找到的最佳超参数。

### 9. 返回值

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

### 1. 方法参数

*   `chosen`：表示选定类别或目标变量的字符串。
*   `X_train`：训练数据的特征矩阵。
*   `X_test`：测试数据的特征矩阵。
*   `y_train`：训练数据的目标标签。
*   `y_test`：测试数据的目标标签。

### 2. 检查预训练模型

该方法通过构建 `LR_Model.pkl` 的文件路径并使用 `os.path.exists(file_path)`，检查当前工作目录中是否存在预训练的逻辑回归模型。

### 3. 模型加载或训练

*   如果存在预训练模型，则使用 `joblib.load('LR_Model.pkl')` 加载它。否则，调用 `logistic_regression` 方法通过超参数调优训练一个新的逻辑回归模型。
*   无论模型是被加载还是被训练，都将存储在 `model` 变量中。

### 4. 模型评估与预测

*   调用 `run_model()` 方法在测试数据（`X_test`、`y_test`）上评估模型性能。`proba` 参数设置为 `True`，表示应计算类别预测的概率分数。
*   预测的类别概率或标签存储在 `y_pred` 变量中。

### 5. 保存模型结果

该方法使用 `Process_Data` 类（`self.obj_data`）的 `save_result()` 方法将模型结果（包括实际标签和预测标签）保存到名为 `results_LR.csv` 的 Excel 文件中。

### 6. 打印状态

打印一条消息以指示逻辑回归模型的训练或加载已完成。

### 7. 返回值

训练或加载的逻辑回归模型（`model`）和预测的类别概率或标签（`y_pred`）作为输出返回。

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

### 1. 方法参数

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

### 2. 基于所选算法的条件块

该方法检查 `chosen` 变量的值以确定选择了哪种机器学习算法。

### 3. 逻辑回归（所选算法）

如果选择的算法是“Logistic Regression”，则会调用 `Machine_Learning` 类的 `implement_LR` 方法，根据模型文件是否存在来加载预训练模型或训练新模型。

针对 Logistic Regression 执行以下可视化和操作：

*   使用 `plot_cm_roc()` 绘制混淆矩阵和 ROC 曲线。
*   使用 `plot_real_pred_val_learning_curve()` 绘制真实值与预测值对比图及学习曲线。
*   使用 `shows_table()` 从 CSV 文件读取结果（包括实际标签和预测标签）并在表格中显示。

## 显示可视化结果

所选机器学习算法生成的可视化图表和表格将显示在 Tkinter 根窗口（`root`）中，供用户交互。

总的来说，该方法提供了一种模块化且有条理的方式来选择机器学习算法、训练或加载模型，并根据所选算法显示相关的可视化图表和结果表格。这有助于在分析机器学习模型性能时保持清晰且易于使用。

接着，在 `Main_Class` 中定义一个名为 `train_ML()` 的新方法，如下所示：

```python
def train_ML(self):
    file_path = os.getcwd() + "/X_train.pkl"
    if os.path.exists(file_path):
        self.X_train, self.X_test, self.y_train, self.y_test = self.obj_ML.load_files()
    else:
        self.obj_ML.oversampling_splitting(self.X, self.y)
        self.X_train, self.X_test, self.y_train, self.y_test = self.obj_ML.load_files()
    print("Loading files done...")
    # turns on combo4 and combo5 after splitting is done
    self.obj_window.combo4['state'] = 'normal'
    self.obj_window.combo5['state'] = 'normal'
    self.obj_window.button2.config(state="disabled")
```

`train_ML()` 方法用于准备机器学习所需的数据，包括加载或生成训练集和测试集。以下是该方法功能的详细说明：

### 1. 检查现有数据文件

该方法首先检查数据文件（`X_train.pkl`、`X_test.pkl`、`y_train.pkl` 和 `y_test.pkl`）是否已存在于当前工作目录中。这些文件通常存储预处理和分割后的数据，以避免重复的数据预处理。

### 2. 文件存在性检查

*   如果数据文件存在（`os.path.exists(file_path)` 为 `True`），则使用 `Machine_Learning` 类的 `load_files()` 方法加载训练集和测试集。
*   如果数据文件不存在，则执行以下数据准备步骤。

### 3. 数据过采样与分割（如果文件不存在）

*   如果数据文件不存在，该方法调用 `Machine_Learning` 类的 `oversampling_splitting()` 方法。该方法执行以下步骤：
    *   应用合成少数类过采样技术（SMOTE）处理类别不平衡，生成合成样本以平衡类别。
    *   按 8:2 的比例将数据分割为训练集和测试集。
    *   对特征应用标准化缩放，确保它们具有相似的尺度。

### 4. 加载文件并启用下拉框

*   数据准备完成后，使用 `load_files` 方法加载训练集和测试集。
*   将两个下拉框（`combo4` 和 `combo5`）的状态设置为 `'normal'`，启用用户交互。
*   最后，禁用 `button2` 以防止进一步的数据分割，因为数据已准备就绪。

总的来说，`train_ML()` 方法确保机器学习任务所需的训练集和测试集可用。如果数据文件已存在则加载它们；如果不存在则生成并保存它们，随后启用特定下拉框的交互并禁用进一步的数据分割，以保持机器学习的数据一致性。

接下来，在 `Main_Class` 中定义一个名为 `choose_combobox4()` 的新方法，如下所示：

```python
def choose_combobox4(self, event):
    chosen = self.obj_window.combo4.get()
    self.obj_plot.choose_plot_ML(self.root, chosen, self.X_train, self.X_test,
                                 self.y_train, self.y_test, self.obj_window.figure1,
                                 self.obj_window.canvas1, self.obj_window.figure2,
                                 self.obj_window.canvas2)
```

`choose_combobox4` 方法负责处理应用程序图形用户界面（GUI）中第四个下拉框（`combo4`）的用户交互。当从 `combo4` 中选择某一项时，会触发此方法。以下是其目的和功能的解释：

### 1. 事件绑定

该方法通过 `bind` 方法绑定到 `combo4` 的 `<<ComboboxSelected>>` 事件。这意味着每当用户从 `combo4` 选择一项时，该方法都会自动执行以响应该事件。

### 2. 事件处理

当从 `combo4` 选择一项时，`event` 参数包含事件信息，尽管该方法中未使用它。

### 3. 获取选定选项

该方法使用 `get` 方法从 `combo4` 检索选定的选项。该选项存储在 `chosen` 变量中，代表用户的选择。

### 4. 调用 `choose_plot_ML()` 方法

将选定的选项连同其他必要数据（训练/测试数据集、图形对象、画布对象）作为参数传递给 `obj_plot` 对象的 `choose_plot_ML()` 方法。该方法负责根据用户的选择显示特定的机器学习相关图表和结果。

总之，`choose_combobox4()` 方法是一个响应 `combo4` 用户选择的回调函数。它获取用户的选择并触发相应的操作，以根据该选择显示机器学习相关的图表和结果。

最后，将以下代码添加到 `Main_Class` 中 `binds_event()` 方法的末尾：

```python
###### Binds button2 to train_ML() function
self.obj_window.button2.config(command=self.train_ML)
###### Binds combobox4 to a function
self.obj_window.combo4.bind("<<ComboboxSelected>>", self.choose_combobox4)
```

这些代码行负责为应用程序中 GUI 元素的用户交互设置事件绑定：

1.  **将按钮绑定到函数**：

    `self.obj_window.button2.config(command=self.train_ML)` 将 `button2` 的 `command` 属性绑定到 `train_ML` 函数。这意味着当用户点击 `button2` 时，将执行 `train_ML` 函数。

2.  **将下拉框绑定到函数**：

    `self.obj_window.combo4.bind("<<ComboboxSelected>>", self.choose_combobox4)` 将 `combo4` 的 `<<ComboboxSelected>>` 事件绑定到 `choose_combobox4` 函数。当用户从 `combo4` 选择一项时，将调用 `choose_combobox4` 函数来处理该事件。

总之，这些代码建立了事件绑定，以确保在用户操作时执行指定的函数。点击 `button2` 时将调用 `train_ML()`，从 `combo4` 选择项目时将调用 `choose_combobox4()` 处理事件，使应用程序能够响应用户交互。

运行 `main_class.py`。接着，点击 **SPLIT DATA** 按钮。然后，选择 **Logistic Regression** 查看使用 Logistic Regression 的结果，如图 31 所示。

![Image](img/image-1.png)

**图 31** 使用 Logistic Regression 的结果
