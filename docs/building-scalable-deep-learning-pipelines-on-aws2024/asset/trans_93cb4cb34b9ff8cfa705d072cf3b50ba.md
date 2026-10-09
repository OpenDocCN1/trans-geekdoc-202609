
## 第 9 步：主函数定义

在本步骤中，我们创建主函数，它作为主要入口点来协调脚本的整个工作流。它接受一个参数 `file_path`，代表包含待处理数据的 CSV 文件的路径：

```python
def main(file_path):
    """
    主函数，用于协调整个工作流。
    
    参数:
        - file_path (str): CSV 文件的路径。
    
    返回:
        - None
    """
    try:
        tsla_regressor = TSLARegressor()
        train_df, test_df = \
            tsla_regressor.preprocess_data(file_path)
        train_features, train_labels, test_features, \
        test_labels = tsla_regressor.convert_to_numpy(
            train_df,
            test_df
        )
        tsla_regressor.create_and_train_model(
            train_features,
            train_labels
        )
        test_loss = tsla_regressor.evaluate_model(
            test_features,
            test_labels
        )
        r2_score_value = tsla_regressor.predict_and_evaluate(
            test_features,
            test_labels
        )

        logging.info("Test Loss: {}".format(test_loss))
        logging.info("R2 Score: {}".format(r2_score_value))

        plot_actual_vs_predicted(
            tsla_regressor,
            test_features,
            test_labels
        )

    except Exception as e:
        logging.error(f"An error occurred: {e}")
```

该函数首先实例化 `TSLARegressor` 类的一个对象，命名为 `tsla_regressor`。然后，它调用 TSLARegressor 实例的 `preprocess_data` 方法来预处理指定 CSV 文件中的数据。处理后的数据被拆分为训练集和测试集。接着，调用 `convert_to_numpy` 方法将包含训练和测试数据的 Spark DataFrame 转换为 NumPy 数组，以便进一步处理。随后，调用 `create_and_train_model` 方法，使用训练特征和标签创建并训练神经网络模型。模型训练完成后，使用 `evaluate_model` 方法评估模型在测试数据上的表现，计算测试损失。此外，调用 `predict_and_evaluate` 方法对测试数据进行预测并计算 R2 分数。最后，函数使用 logging 模块记录测试损失和 R2 分数。如果在工作流执行过程中发生异常，该异常会被捕获，并使用 logging 模块记录错误信息。

## 第 10 步：条件代码块

在最后一步中，条件代码块检查脚本是否作为主程序直接运行：

```python
if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)
    file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(file_path)
```

-   `if __name__ == "__main__":`：此条件检查脚本是否被直接执行，而不是作为模块被导入到另一个脚本中。
-   `logging.basicConfig(level=logging.INFO)`：此行配置日志系统以显示 INFO 级别或更高级别的日志消息。这确保了严重级别为 INFO 或更高的日志消息会被显示。
-   `file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"`：此行定义了包含 TSLA 股票数据的 CSV 文件的路径。
-   `main(file_path)`：此行调用主函数，并传入指定的 `file_path` 作为参数。主函数将协调脚本的整个工作流，包括数据预处理、模型训练、性能评估以及绘制实际值与预测值的对比图。

为了运行代码，我们将代码保存为“tesla_stock_price_prediction.py”并在 Jupyter Lab 终端中执行（我们也可以在 EC2 实例上直接运行）。由于我们创建了一个名为“myenv”的环境，我们按以下方式激活它：

```bash
source /home/ubuntu/myenv/bin/activate
```

在激活环境后，我们使用 Python 3 通过以下命令执行代码：

```bash
python3 tesla_stock_price_prediction.py
```

现在，让我们查看代码的输出。

第一个输出显示了在 TSLA 股票价格回归模型训练和评估过程中获得的训练损失、测试损失和 R2 分数：

训练损失：

| 轮次 (Epoch) | 损失 (Loss) |
| :--- | :--- |
| 1 | 41,731 |
| 2 | 40,362 |
| 3 | 39,658 |
| 4 | 33,450 |
| 5 | 19,520 |
| 6 | 5,492 |
| 7 | 2,532 |
| 8 | 1,984 |
| 9 | 1,657 |
| 10 | 1,231 |
| ... | ... |
| 100 | 14 |

测试损失：12.11

R2 分数：0.998

我们现在将逐一解释这些指标：

**训练损失：**
-   它显示了训练过程中每个轮次（epoch）的训练损失。
-   每一行代表一个轮次以及该轮次对应的损失值。
-   随着训练的推进，损失逐渐降低。这表明模型正在学习更好地拟合训练数据。最初，损失相对较高，但随着每个轮次的进行迅速降低，直至收敛到一个较低的值。在我们的输出中，训练损失从 41,731 显著降低到 14，表明模型正在学习并改善对训练数据的拟合程度。

**测试损失：**
-   它代表在模型训练完成后，在测试数据集上计算得出的损失（均方误差）。
-   测试损失指示了已训练的模型对未见数据的泛化能力。
-   在我们的输出中，测试损失约为 12，这意味着在测试数据上，模型的预测平均偏差为这个数值（以与目标变量相同的单位衡量，对于股票价格而言是美元）。

**R2 分数：**
-   R2 分数（也称为决定系数）是一个统计量，表示因变量（在此情况下为股票价格）的方差中，可以由自变量（特征）预测的比例。
-   它的取值范围从 0 到 1，1 表示完美拟合。
-   在我们的输出中，R2 分数为 0.998，这意味着模型可以解释测试数据中约 99.8% 的方差，表明具有极高的预测准确性。

综上所述，输出表明模型训练有效，训练损失随轮次增加而降低，且评估指标（测试损失和 R2 分数）显示其在未见数据上表现良好。

代码的第二个输出是前十个 TSLA 实际股票价格与回归模型预测价格的对比：

| 实际值 (Actual) | 预测值 (Predicted) | 百分比差异 (% Difference) |
| :--- | :--- | :--- |
| 118.85 | 117.87 | -1% |
| 123.22 | 122.63 | 0% |
| 283.15 | 282.61 | 0% |
| 284.8 | 281.55 | -1% |
| 34.57 | 35.09 | 2% |
| 34.03 | 34.17 | 0% |
| 281.52 | 280.22 | 0% |
| 283.48 | 282.09 | 0% |
| 143.75 | 138.58 | -4% |
| 209.14 | 211.78 | 1% |

我们添加了实际值与预测值之间的百分比差异，以便更易于解读。如果预测值低于实际值，百分比差异将为负数，表示低估。如果预测值高于实际值，百分比差异将为正数，表示高估。如果预测值与实际值完全相同，百分比差异将为 0%。

在我们的输出中，对于某些条目，例如第二行（实际值 123.22 对比 预测值 122.63），预测值略低于实际值，导致非常小的负百分比差异（小于 −1%），四舍五入后为 0%。同样，在第五行（实际值 34.57 对比 预测值 35.09）中，预测值略高于实际值，导致约为 2% 的正百分比差异。

总体而言，最大差异为 −4%，且 50% 的预测值与实际值吻合（约 0% 差异），表明匹配度很高。

最终输出是一个散点图，用于可视化所有观测值中实际值与预测值之间的关系。在图 5-1 中，实际值绘制在 x 轴上（test_labels），预测值绘制在 y 轴上（test_predictions）。此外，还绘制了一条对角虚线，以表示实际值与预测值相同的理想情况。

