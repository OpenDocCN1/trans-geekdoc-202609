
# 使用 Penzai 进行训练

管理机器学习实验并系统地跟踪超参数、指标和结果，对于优化模型性能和确保可重复性至关重要。在处理多个模型或调优超参数时，手动跟踪不同的运行和配置可能具有挑战性。为了解决这个问题，我们将使用 Penzai，这是一款专为实验跟踪和管理而设计的工具。在本教程中，我们介绍 Penzai 并演示如何将其集成到基于 JAX 的工作流程中，使我们能够在训练期间记录超参数、指标和其他重要细节，从而使实验更易于监控、比较和重现。

## 关于 Penzai

Penzai 是一个轻量级且灵活的工具，用于管理机器学习实验，可实现对超参数、指标和结果的跟踪。该过程包括：
-   安装 Penzai 并设置项目。
-   在训练过程中记录超参数和指标。
-   使用 Penzai 的可视化和比较工具来分析不同的实验运行。
-   通过保存所有相关的实验细节来确保可重复性。

## 安装 Penzai

先提醒一下，您需要确保 Penzai 已安装在您的系统上。如果您还没有，可以使用以下命令添加：

```
pip install penzai
```

接下来，初始化一个新的 Penzai 项目。此步骤会创建配置文件以管理实验元数据。

```
penzai init --project-name "Fashion MNIST Training"
```

此命令设置名为 "Fashion MNIST Training" 的新项目并创建必要的配置文件。如果需要，您还可以设置存储后端或云集成选项。

## 在训练脚本中配置 Penzai

要将 Penzai 集成到您的 JAX 训练脚本中，请先导入 `penzai` 模块并初始化新的实验运行。

```
import penzai
# Initialize Penzai
penzai.init(project="Fashion MNIST Training")
# Start a new experiment run
run = penzai.start_run(run_name="Baseline Model Training")
```

`start_run` 函数开始一个新的实验，使我们能够记录与此运行相关的超参数、指标和结果。

## 记录超参数

在开始训练之前，记录相关的超参数，例如 `learning_rate`、`batch_size` 和 `num_epochs`。

```
# Hyperparameters
learning_rate = 0.01
batch_size = 128
num_epochs = 10
# Log hyperparameters
run.log_hyperparams({
    "learning_rate": learning_rate,
    "batch_size": batch_size,
    "num_epochs": num_epochs
})
```

此步骤可确保实验的关键设置被记录下来，以便在审阅或重现运行时可以回溯参考。

## 记录训练指标

随着训练的进行，在每个 epoch 记录重要的指标，如 loss 和 accuracy。这使 Penzai 能够随时间跟踪模型的性能。

```
def train_network_with_tracking(train_ds, params, num_epochs):
    for epoch in range(num_epochs):
        epoch_loss = 0
        for batch in train_ds:
            images, labels = batch
            # Compute gradients
            grads = jax.grad(cross_entropy_loss)(params, images, labels)
            # Update parameters
            params = sgd_update(params, grads, learning_rate)
            # Compute batch loss
            batch_loss = cross_entropy_loss(params, images, labels)
            epoch_loss += batch_loss
        # Log the epoch loss
        run.log_metric("epoch_loss", epoch_loss, step=epoch)
        # Optionally, log additional metrics
        accuracy = compute_accuracy(params, test_ds)
        run.log_metric("accuracy", accuracy, step=epoch)
        print(f"Epoch {epoch + 1}, Loss: {epoch_loss}, Accuracy: {accuracy * 100:.2f}%")
    return params
# Train the network while logging metrics
trained_params = train_network_with_tracking(train_ds, params, num_epochs)
```

通过在每个 epoch 记录 `loss` 和 `accuracy` 等指标，您可以在 Penzai 的仪表板中可视化模型的学习曲线。

## 可视化和比较实验

记录指标后，使用 Penzai 的 Web 界面分析训练进度、比较不同的运行并观察趋势。

打开 Penzai 仪表板：

```
penzai ui
```

然后，查看列在 "Fashion MNIST Training" 下的实验，并比较不同运行中的 `loss` 和 `accuracy` 等指标。您还可以使用内置工具创建图表，显示指标如何随时间演变或不同的超参数设置如何影响结果。

## 记录模型产物以实现可重复性

除了跟踪指标和超参数外，保存模型产物（例如训练好的参数）以实现可重复性和进一步分析也很重要。

```
# Save trained model parameters
model_artifact_path = "model_params.pkl"
with open(model_artifact_path, "wb") as f:
    import pickle
    pickle.dump(trained_params, f)
# Log the model artifact
run.log_artifact(model_artifact_path)
```

记录训练好的模型权重等产物可确保您能够重现实验或在需要时进行改进。

## 结束实验运行

完成训练并记录必要信息后，请确保结束实验运行。

```
run.end()
```

这将完成当前实验，使您能够开始新的运行或在 Penzai 中分析已完成的实验。

通过将 Penzai 集成到训练过程中，我们高效地管理了实验，系统地跟踪了超参数，并记录了用于评估模型性能的指标。Penzai 可视化训练进度、比较不同运行并保存模型产物的能力促进了机器学习项目的可重复性和优化。
