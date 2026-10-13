
# 结论

Extreme Gradient Boosting (XGBoost) 分类器在给定数据集上表现良好，在两个类别上均实现了高准确率、召回率、精确率和 F1 分数。这些指标表明该模型能有效区分两个类别并做出准确预测。平衡的 F1 分数表明该模型适用于精确率和召回率均至关重要的任务，例如类别不平衡的二分类问题。

# 多层感知机分类器与网格搜索

在 `Machine_Learning` 类中，定义一个名为 `multi_layer_perceptron()` 的新方法，如下所示：

```python
def multi_layer_perceptron(self, name, X_train, X_test, y_train, y_test):
    # Define the parameter grid for the grid search
    param_grid = {
        'hidden_layer_sizes': [(50,), (100,), (50, 50), (100, 50), (100, 100)],
        'activation': ['logistic', 'relu'],
        'solver': ['adam', 'sgd'],
        'alpha': [0.0001, 0.001, 0.01],
        'learning_rate': ['constant', 'invscaling', 'adaptive'],
    }

    # Initialize the MLP Classifier
    mlp = MLPClassifier(random_state=2021)

    # Create GridSearchCV with the MLP Classifier and the parameter grid
    grid_search = GridSearchCV(mlp, param_grid, cv=3, scoring='accuracy', n_jobs=-1)

    # Train and perform grid search
    grid_search.fit(X_train, y_train)

    # Get the best MLP Classifier model from the grid search
    best_model = grid_search.best_estimator_

    # Saves model
    joblib.dump(best_model, 'MLP_Model.pkl')

    # Print the best hyperparameters found
    print(f"Best Hyperparameters for MLP:")
    print(grid_search.best_params_)

    return best_model
```

`multi_layer_perceptron()` 函数是用于训练和评估多层感知机 (MLP) 分类器的机器学习流水线的一部分。以下是该函数关键组件的细分：

1.  **参数网格**：你定义了一个包含用于调优 MLP 模型的各种超参数的参数网格 `param_grid`。这些超参数包括神经网络架构（隐藏层大小）、激活函数、优化算法、正则化强度 (`alpha`) 和学习率调度。
2.  **MLP 分类器初始化**：你使用固定的随机种子 (`random_state=2021`) 初始化一个 MLP 分类器实例。MLP 分类器是一种用于分类任务的人工神经网络。
3.  **网格搜索**：你创建一个名为 `grid_search` 的 `GridSearchCV` 对象，它将对前面定义的超参数网格进行详尽搜索。网格搜索用于为 MLP 模型找到最佳的超参数组合。
4.  **训练与网格搜索**：你使用 `GridSearchCV` 对象在训练数据 (`X_train`, `y_train`) 上拟合（训练）MLP 模型。这将使用不同的超参数组合训练多个 MLP 模型，并使用交叉验证 (`cv=3`) 评估其性能。
5.  **最佳模型选择**：网格搜索完成后，你使用 `grid_search.best_estimator_` 从搜索结果中获得最佳 MLP 模型。
6.  **模型保存**：如果需要，你可以使用 `joblib` 将最佳 MLP 模型保存到名为 `'MLP_Model.pkl'` 的文件中。这使你可以在未来重用训练好的模型，而无需重新训练。
7.  **打印最佳超参数**：你打印出网格搜索找到的最佳超参数。此信息有助于你了解哪些超参数促成了最佳模型的性能。

总体而言，此函数自动化了 MLP 分类器的超参数调优过程，并允许你高效地搜索最佳配置，以在分类任务上实现最优性能。

---

然后，在 `Machine_Learning` 类中，定义一个名为 `implement_MLP()` 的新方法：

```python
def implement_MLP(self, chosen, X_train, X_test, y_train, y_test):
    file_path = os.getcwd() + "/MLP_Model.pkl"

    if os.path.exists(file_path):
        model = joblib.load('MLP_Model.pkl')
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)
    else:
        model = self.multi_layer_perceptron(chosen, X_train, X_test, y_train, y_test)
        y_pred = self.run_model(chosen, model, X_train, X_test, y_train, y_test, proba=True)

    # Saves result into excel file
    self.obj_data.save_result(y_test, y_pred, "results_MLP.csv")

    print("Training Multi-Layer Perceptron done...")

    return model, y_pred
```

`implement_MLP()` 函数是机器学习流水线的一部分，用于为给定数据集实现和评估多层感知机 (MLP) 分类器。以下是该函数关键组件的细分：

1.  **模型加载或训练**：首先，该函数检查当前工作目录下名为 `'MLP_Model.pkl'` 的预训练 MLP 模型文件是否存在。如果存在，它使用 `joblib.load` 加载预训练模型。如果不存在，它将继续训练一个新的 MLP 模型。
2.  **模型训练**：如果预训练模型不存在，该函数调用 `multi_layer_perceptron()` 函数，传入选定的配置、训练数据 (`X_train` 和 `y_train`) 以及测试数据 (`X_test` 和 `y_test`)。此函数执行 MLP 模型的超参数调优和训练。
3.  **模型评估**：在加载预训练模型或训练新模型后，该函数通过调用 `run_model` 函数使用训练好的模型对测试数据 (`X_test`) 进行预测。它请求概率预测 (`proba=True`)，表明它想要每个类别的概率分数。
4.  **结果保存**：实际值和预测值（概率）使用 `obj_data` 对象的 `save_result()` 方法保存到名为 `'results_MLP.csv'` 的 Excel 文件中。这允许稍后分析和比较模型的性能。
5.  **打印状态**：最后，该函数打印一条消息，指示 MLP 模型的训练或加载已完成。

总体而言，此函数处理训练和评估 MLP 分类器的整个流水线，包括如果存在预训练模型则加载它的选项。这种方法通过避免在先前已训练相同配置时不必要地重新训练模型来节省时间和资源。

---

然后，在 `Helper_Plot` 类中，将此代码添加到 `choose_plot_ML()` 方法的末尾：

```python
if chosen == "Multi-Layer Perceptron":
    best_model, y_pred = self.obj_ml.implement_MLP(chosen, X_train, X_test, y_train, y_test)

    # Plots confusion matrix and ROC
    self.plot_cm_roc(best_model, X_test, y_test, y_pred, chosen, figure1, canvas1)

    # Plots true values versus predicted values diagram and learning curve
    self.plot_real_pred_val_learning_curve(best_model, X_train, y_train,
                                           X_test, y_test, y_pred, chosen, figure2, canvas2)

    # Shows table of result
    df_lr = self.obj_data.read_dataset("results_MLP.csv")
    self.shows_table(root, df_lr, 450, 750, "Y_test and Y_pred of Multi-Layer Perceptron")
```

以下是其逐步执行的操作：

1.  **模型实现 (`implement_MLP()`)**：如果选择的模型是 "Multi-Layer Perceptron"，它会加载预训练的 MLP 模型（如果存在，保存为当前工作目录下名为 "MLP_Model.pkl" 的文件）。如果预训练模型不存在，它会使用网格搜索来寻找最佳超参数来训练一个新的 MLP 模型。然后，它使用该模型对测试数据进行预测。

2.  **性能可视化 (`plot_cm_roc()` 和 `plot_real_pred_val_learning_curve()`)**：获得 MLP 模型的预测结果后，它继续创建两种类型的图表：
    *   **混淆矩阵和 ROC 曲线 (`plot_cm_roc()`)**：它生成混淆矩阵和 ROC 曲线，以直观地评估 MLP 模型在测试数据上的性能。
