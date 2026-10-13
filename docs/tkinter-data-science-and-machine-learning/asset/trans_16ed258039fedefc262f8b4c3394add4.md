

## 摘要

此函数使用网格搜索自动化 KNN 分类器的超参数调优过程。它为 KNN 模型找到最佳超参数集，并保存优化后的模型以供后续使用。这是机器学习中的常见做法，旨在确保模型在给定数据集上实现最优性能。

## `Machine_Learning` 类中的实现

定义一个名为 `implement_KNN()` 的新方法：

```python
def implement_KNN(self, chosen, X_train, X_test, y_train, y_test):
    file_path = os.getcwd() + "/KNN_Model.pkl"
    if os.path.exists(file_path):
        model = joblib.load('KNN_Model.pkl')
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    else:
        model = self.knearest_neigbors(chosen, X_train, X_test, y_train, y_test)
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    # 将结果保存到 Excel 文件
    self.obj_data.save_result(y_test, y_pred, "results_KNN.csv")
    print("Training KNN done...")
    return model, y_pred
```

### 代码解释

`implement_KNN()` 函数负责实现和训练 K-近邻 (KNN) 分类器，以及保存和评估结果。

#### 1. 函数定义
该函数接受以下参数：
*   `chosen`：表示所选模型名称或标识符的字符串（本例中为 "K-Nearest Neighbors"）。
*   `X_train`：训练数据的特征矩阵。
*   `X_test`：测试数据的特征矩阵。
*   `y_train`：训练数据的目标标签。
*   `y_test`：测试数据的目标标签。

#### 2. 文件路径检查
它检查当前工作目录 (`os.getcwd()`) 下是否存在名为 `KNN_Model.pkl` 的文件。该文件用于存储训练好的 KNN 模型。

#### 3. 模型加载或训练
*   如果 `KNN_Model.pkl` 存在，则有可用的训练好 KNN 模型。代码使用 `joblib.load` 加载此模型。
*   如果文件不存在，则需要训练模型。代码调用 `knearest_neigbors()` 函数来训练并优化 KNN 模型。

#### 4. 模型预测
加载或训练 KNN 模型后，函数调用 `run_model` 函数使用该模型对测试数据 (`X_test`) 进行预测。`proba` 参数设置为 `True`，表示该函数应返回预测概率。

#### 5. 结果保存
实际目标标签 (`y_test`) 和预测标签/概率 (`y_pred`) 用于通过 `obj_data` 提供的 `save_result` 函数将结果保存到名为 `results_KNN.csv` 的 Excel 文件中。该文件通常包含模型的预测结果和真实标签，以供后续分析。

#### 6. 打印状态
向控制台打印一条消息，指示 KNN 模型的训练或加载已完成。

### 总结
此函数作为实现 KNN 模型的统一接口。它检查是否有可用的训练模型，若找到则加载，否则训练新模型。进行预测后，它将结果保存到 Excel 文件并提供状态消息。这种方法允许复用预训练模型，并简化了运行和评估 KNN 分类器的过程。

## `Helper_Plot` 类中的实现

将此代码添加到 `choose_plot_ML()` 方法的末尾：

```python
if chosen == "K-Nearest Neighbors":
    best_model, y_pred = self.obj_ml.implement_KNN(chosen, X_train, X_test, y_train, y_test)
    # 绘制混淆矩阵和 ROC 曲线
    self.plot_cm_roc(best_model, X_test, y_test, y_pred, chosen, figure1, canvas1)
    # 绘制真实值与预测值对比图及学习曲线
    self.plot_real_pred_val_learning_curve(best_model, X_train, y_train,
                                           X_test, y_test, y_pred, chosen, figure2, canvas2)
    # 显示结果表格
    df_lr = self.obj_data.read_dataset("results_KNN.csv")
    self.shows_table(root, df_lr, 450, 750, "Y_test and Y_pred of KNN")
```

### 代码解释
此代码负责执行 K-近邻 (KNN) 分类器，评估其性能并显示结果。

#### 1. 条件检查
代码以一个 `if` 语句开始，检查变量 `chosen` 的值是否等于字符串 `"K-Nearest Neighbors"`。此条件决定是否执行 KNN 分类器。

#### 2. KNN 实现与评估
如果条件满足，将执行以下操作：
*   代码调用 `obj_ml` 对象的 `implement_KNN()` 方法，传入 `chosen`、`X_train`、`X_test`、`y_train` 和 `y_test` 作为参数。该方法负责训练或加载 KNN 模型并进行预测。
*   获得训练好的模型和预测结果 (`y_pred`) 后，代码继续评估模型性能。

#### 3. 性能可视化与报告
*   代码调用 `plot_cm_roc()` 方法生成两个图表：混淆矩阵和接收者操作特征 (ROC) 曲线。这些图表提供了关于模型分类性能及其区分类别能力的洞察。
*   接着，它调用 `plot_real_pred_val_learning_curve()` 方法创建两个额外图表：
    *   真实值与预测值对比散点图，直观对比模型预测与实际目标值。
    *   学习曲线，展示模型性能随训练数据集大小增加而变化的情况。该曲线有助于评估模型的偏差-方差权衡。
*   最后，代码使用 `obj_data` 提供的 `read_dataset()` 方法从名为 `results_KNN.csv` 的 Excel 文件中读取 KNN 模型预测结果。该文件数据包含模型预测和真实标签。

#### 4. 表格显示
代码使用 `shows_table` 方法显示结果表格。该表格推测展示实际值和预测值，允许对模型性能进行详细分析。

### 结论
此代码旨在实现、评估和可视化 K-近邻分类器的性能。它生成各种图表并显示结果表格，提供关于模型在给定数据集上表现如何的洞察。

## 执行步骤
1.  运行 `main_class.py`。
2.  点击 **SPLIT DATA** 按钮。
3.  选择 **K-Nearest Neighbors** 查看结果，如图 33 所示。

![Image](images/image-3.png)

**图 33** 使用 K-近邻分类器的结果

### 输出
```text
K-Nearest Neighbors
accuracy: 0.8689384010484927
recall: 0.8689384010484927
precision: 0.8706714584974559
f1: 0.8687919116352781
 precision recall f1-score support
 0 0.90 0.84 0.86 382
 1 0.85 0.90 0.87 381
 accuracy 0.87 763
 macro avg 0.87 0.87 0.87 763
weighted avg 0.87 0.87 0.87 763
```

### 输出分析
输出代表 K-近邻 (KNN) 分类器在数据集上的性能指标和评估结果。

#### 1. 分类器信息
*   **分类器名称**：K-Nearest Neighbors
*   **样本数量**：763（推测为测试数据集大小）

#### 2. 性能指标
*   **准确率**：KNN 分类器的准确率约为 0.869，意味着它在测试数据集中正确分类了约 86.9% 的样本。
*   **召回率**：召回率得分也约为 0.869，表明模型正确识别了约 86.9% 的正类（类别 1）样本。该指标衡量模型找出所有相关正类实例的能力。

