

## 第 10 章：检测异常行为

训练集中正常实例的平均重构误差为 0.811。如果我们观察分位数，可以发现大多数实例的误差 <= 0.887。根据此信息，我们可以将阈值设置为 < 1.0。如果重构误差 > 阈值，则我们认为其为异常。

```r
# 在异常测试集上进行预测。
preds.test_abnormal <- autoencoder %
predict_on_batch(as.matrix(test.test_abnormal[,c(1:2)]))
```

```r
# 计算重构误差。
errors.test.abnormal <- squared.errors(preds.test_abnormal,
as.matrix(test.test_abnormal[,c(1:2)]))
```

```r
# 根据阈值预测标签：1: 异常, 0: 正常。
pred.labels.abnormal <- as.integer(errors.test.abnormal > threshold)
```

```r
# 统计检测到多少异常实例。
sum(pred.labels.abnormal)
#> [1] 46
```

通过使用该阈值，自动编码器能够检测出 54 个异常点中的 46 个。从下面的混淆矩阵我们还可以看到有 16 个假阳性。

```
#> 参考
#> 预测 0 1
#> 0 202 8
#> 1 16 46
```

从 ROC 曲线图中可以看到，AUC 为 0.93，这于孤立森林（Isolation Forest）实现的 0.96，但通过精调和更多轮次的训练，自动编码器应该能够获得相似的结果。

# ROC 曲线
AUC = 0.9326368

![](img/91c149cc24c3e5af2971580c9dda9d8b_355_0.png)

图 10.13：ROC 曲线和 AUC。虚线代表随机模型。

## 10.4 总结

本章介绍了两种异常检测模型，即孤立森林（Isolation Forests）和自动编码器（autoencoders）。还展示了如何使用这些模型进行异常轨迹检测的示例。本章还介绍了 ROC 曲线和 AUC，它们可用于评估模型的性能。

- **孤立森林（Isolation Forests）**通过对特征进行随机划分，直到所有实例都被孤立。
- 异常点在首次划分期间更有可能被孤立。
- 异常点的平均树路径长度比正常点短。
- 根据路径长度计算介于 0–1 之间的**异常评分（anomaly score）**，越接近 1，该点越可能是异常。
- **ROC 曲线**用于可视化模型在不同阈值下的敏感性和假阳性率。
- 曲线下的面积 **AUC** 可用于总结模型的性能。
- 简单的**自动编码器（autoencoder）**是一种人工神经网络，其输出层与输入层具有相同的形状。
- 自动编码器将数据编码到低维，然后对其进行重构。
- **重构误差（reconstruction error）**（损失）衡量预测与真实值之间的距离，可以作为异常评分。

## 附录 A

### 设置你的环境

书中的示例是在 R 4.0.2 中测试的。你可以从其官方网站获取最新的 R 版本：www.r-project.org/

作为 IDE，我使用 RStudio (https://rstudio.com/)，但你可以使用你喜欢的。书中的大多数代码示例依赖于数据集。以下两个部分描述了如何安装数据集和源代码。如果你想尝试这些示例，我建议按照以下两个部分的说明进行。

最后一部分包含了如何安装 Keras 和 TensorFlow 的说明，这是构建和训练深度学习模型所需的库。深度学习将在第 8 章中介绍。在此之前，你不需要这些库。

## A.1 安装数据集

你可以在这里下载包含书中使用的大部分数据集的压缩文件：https://github.com/enruiguet/behavior-datasets。

下载数据集集合文件（behavior_book_datasets.zip）并将其解压到本地目录，例如 C:/datasets/。此合集包含了大多数数据集。由于某些数据集文件较大或受许可证限制，并非所有数据集都包含在集合中。但你可以单独下载它们。尽管某个数据集可能未包含在编译集中，但仍然会有一个对应的目录，其中包含一个 README 文件，上面写了如何获取它的说明。下面的图片显示了我的电脑上的目录结构看起来。

![](img/91c149cc24c3e5af2971580c9dda9d8b_358_0.png)

## A.2 安装示例源代码

示例源代码可以在这里下载：https://github.com/enriquegit/behavior-code

你可以使用 git 获取代码，如果你不熟悉，可以点击“Code”按钮然后点击“Download zip”。然后，将文件解压到你选择的本地目录。

`auxiliary_functions/` 文件夹包含一个脚本：install.R。

```r
datasets_path <- "C:/datasets"
```

## 附录 A. 设置你的环境

### A.3 运行 Shiny 应用

Shiny 应用¹是用 R 编写的交互式应用程序。本书包含了演示某些概念的 shiny 应用。Shiny 应用文件名以 shiny 前缀开头，加上特定名称。有些具有 .Rmd 扩展，而一些具有 .R 扩展。无论扩展如何，它们的运行方式相同。在运行 shiny 应用之前，确保你已经安装了 shiny 和 shinydashboard 包。

```r
install.packages("shiny")
install.packages("shinydashboard")
```

¹https://shiny.rstudio.com/

### 设置环境

要运行应用，只需在 RStudio 中打开相应的文件。RStudio 会检测到这是一个 shiny 应用并显示“Run Document”或“Run App”按钮。点击该按钮启动应用。

![](img/91c149cc24c3e5af2971580c9dda9d8b_360_0.png)

## A.4 安装 Keras 和 TensorFlow

Keras 和 TensorFlow 将用于第 8 章。如果你还没到那里，就不需要它们。

TensorFlow 有两个主要版本：CPU 版本和 GPU 版本。GPU 版本利用某些显卡的能力来执行更快的操作。书中的示例可以在 CPU 版本上运行。以下说明适用于 CPU 版本。安装 GPU 版本需要某些特定平台的细节。我建议你先安装 CPU 版本，如果你想或需要执行更快的计算，再考虑 GPU 版本。

带有 TensorFlow（CPU 版本）作为后端安装 Keras 需要四个简单的步骤：

1. 如果你在 Windows 上，你应该安装 Anaconda。
2. 使用 `install.packages("keras")` 安装 keras R 包。
3. 使用 `library(keras)` 加载 keras。
4. 运行 `install_keras()`。此函数将安装 TensorFlow 作为后端。如果你没有安装 Anaconda，它会询问是否要安装 Miniconda。

你可以通过以下地址测试安装：

> https://www.anaconda.com/

