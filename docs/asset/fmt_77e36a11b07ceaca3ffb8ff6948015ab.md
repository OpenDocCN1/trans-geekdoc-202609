
| Number of examples : 4590 |

| Training loss : 1.2978 |

| Training time (sec) : 174.5081 |

现在你将能够进行建模，以便用 Core ML 加载它。使用 T Create 使用模型有两种方法。第一：

```
model.save("HealthySnacks.model")
```

这以 Turi Create 自己的格式保存模型，允许你稍后使用 `t.c.Load_model()` 将其加载到 Python notebook。一旦训练了 T Create 模型，你之后无法对其进行修改，但你可能想在不同的测试数据上对其进行评估，或仔细检查指标。

运行此命令获取 Core ML 模型：

```
model.export_coreml("HealthySnacks.mlmodel")
```

你可以按照通常的方法将 mlmodel 添加到 Xcode，如果你想将其与 Create ML 模型比较。尽管基于相同的预训练模型，该模型的准确率略低，尺寸只有 Create ML 模型的一半。

### 关闭 Jupyter

要关闭 Jupyter，点击此浏览器窗口中的 **Logout** 按钮以及显示你 ML 目录的窗口。

在你运行 jupyter notebook 的 **Terminal** 窗口中——或者使用 Anaconda Navigator 启动 Jupyter——按 **Control-C** 停止服务器。你可能需要按两次。如果提示符没有返回，关闭此终端。

### 取消激活的环境

如果你在命令行激活了 **turienv**，输入此命令取消激活：

```
conda deactivate
```

这取消了 **turienv** 环境；命令行提示符。

### Docker 和 Colab

支持 Python 机器学习有两个高级工具：Docker 和 Google。

Docker 像虚拟机但简单。Docker 是一种容器系统，允许你重用和模块化环境，它是扩展和服务应用程序的基础。安装 Docker 可以让你访问以 Docker 镜像分发的大机器学习资源。

Docker 镜像可以与同事或伙伴共享预定义的环境，但在某些情况下它们需要编写 Docker 镜像（通过编辑 Dockerfile），这超出了我们涵盖的范围。

你可以从 https://dockr.ly/2hwNOZZ 下载适用于 Mac 的社区版 Docker。要搜索 Docker Hub hub.docker.com，点击 **Explore**，然后搜索 image classifier：

![](img/5720be5c3cca252e12448e68d25607b5_156_0.png)

在 Docker Hub 搜索 image classifier

# Google Collaboratory

Google Research 的 colab.research.google.com 是一个运行在浏览器中的 Jupyter Notebook 环境。它已经安装了你需要的许多机器学习库。它最好的功能是，你可以将笔记本的**运行时类型**设置为 **GPU** 来免费使用 Google 的 GPU。它甚至允许使用 Google 的 TPU（张量处理单元）。

## 机器学习第 4 章：Python 与 Turi Create 入门

如果你没有可以运行机器学习的计算机，你完全可以使用 Colab 来跟进本书的部分内容。然而，本书的作者建议读者通过本地安装的 Python 来跟进学习。如果你选择使用 Colab，将需要进行以下设置。当然，你需要一个 Google 账户才能继续。

在 drive.google.com 访问你的 Google 云硬盘，从侧边菜单创建一个名为 **machine-learning** 的新**文件夹**。

![](img/5720be5c3cca252e12448e68d25607b5_157_0.png)

双击该文件夹，将解压后的 snapshots 数据集拖放到其中。这可能需要一些时间。在等待期间，你将将 Colab 作为“应用”添加到 Google 云硬盘中。在 **machine-learning** 文件夹的任何处点击鼠标右键，在对话框中选择**更多**，然后选择 + **选择连接更多应用**。

### 机器学习

第 4 章：Python 与 Turi Create 入门

![](img/5720be5c3cca252e12448e68d25607b5_158_0.png)

在打开的“连接应用到 Google 云硬盘”窗口中，在搜索字段中搜索 colab，并选择 + 连接。

## 第 4 章：Python 与 Turi Create 入门

![](img/5720be5c3cca252e12448e68d25607b5_159_0.png)

安装成功后，关闭窗口，再次在任何处点击鼠标右键，在**更多**对话框中选择**Collaboratory**。这将打开一个新标签页或窗口，看起来非常像 Jupyter 笔记本。

### 机器学习

第 4 章：Python 与 Turi Create 入门

![](img/5720be5c3cca252e12448e68d25607b5_160_0.png)

通过点击标题并内联重命名，将文件重命名为 **getting-started.ipynb**。

![](img/5720be5c3cca252e12448e68d25607b5_160_1.png)

### 机器学习

## 第 4 章：Python 与 Turi Create 入门

从工具栏中，选择运行时（Runtime） > 更改运行时类型（Change Runtime type）。

![](img/5720be5c3cca252e12448e68d25607b5_161_0.png)

在打开的笔记本设置对话框中，将硬件加速（Hardware accelerator）从无（None）更改为 GPU。保存更改。

![](img/5720be5c3cca252e12448e68d25601_1.png)

### 机器学习

## 第 4 章：Python 与 Turi Create 入门

在笔记本的第一个代码单元中，粘贴以下代码：

```python
from google.colab import drive
drive.mount('/content/drive/')
```

这两行代码将把你的 Google 云硬盘文件夹导入笔记本。这需要允许 Colab 访问你的 Google 云硬盘文件夹。点击代码单元旁的小按钮。按照输出窗口中的说明操作，打开链接以赋予 Colab 访问你云硬盘的权限。你将获得一个访问代码并将其粘贴到笔记本中。

![](img/5720be5c3cca252e12448e68d25607b5_162_0.png)

### 机器学习

第 4 章：Python 与 Turi Create 入门

挂载完成后，添加一个新的代码单元，并运行以下代码：

```bash
ls "/content/drive/My Drive/machine-learning/snacks"
```

![](img/5720be5c3cca252e12448e68d25607b5_163_0.png)

你可能会注意到代码开头有一个感叹号。在允许运行系统命令的 Jupyter 特有语法中，你正尝试列出上传 snacks 数据集的目录内容。如果一切顺利，你现在应该能够将其设为 snacks 数据集的根目录。

你已经完成了 Google 笔记本环境环境的设置，并配置了使用 GPU，你可以将其用于本书的学习。值得重复的是，Colab 针对本书尚未经过测试，你在使用过程中可能会遇到问题。然而，对于想要进行机器学习但没有足够强大的计算机运行机器学习算法的开发者来说，它提供了一个极具吸引力的替代方案。

### 关键点

- 熟悉 Python。它在机器学习领域学术界的广泛应用意味着，如果你学会了 Python，你将非常抢手。
- 熟悉 Conda。
- 熟悉 Jupyter。

### 接下来去哪里？

你已经完成了 Google 笔记本环境的设置，并配置了使用 GPU，你可以将其用于本书的学习。值得重复的是，Colab 针对本书尚未经过测试，你在使用过程中可能会遇到问题。然而，对于想要进行机器学习但没有足够强大的计算机运行机器学习算法的开发者来说，它提供了一个极具吸引力的替代方案。

## 第 4 章：Python 与 Turi Create 入门

如果你没有可以运行机器学习的计算机，你完全可以使用 Colab 来跟进本书的部分内容。然而，本书的作者建议读者通过本地安装的 Python 来跟进学习。如果你选择使用 Colab，将需要进行以下设置。当然，你需要一个 Google 账户才能继续。

在 drive.google.com 访问你的 Google 云硬盘，从侧边菜单创建一个名为 **machine-learning** 的新**文件夹**。

![](img/5720be5c3cca252e12448e68d25607b5_157_0.png)

双击该文件夹，将解压后的 snapshots 数据集拖放到其中。这可能需要一些时间。在等待期间，你将将 Colab 作为“应用”添加到 Google 云硬盘中。在 **machine-learning** 文件夹的任何处点击鼠标右键，在对话框中选择**更多**，然后选择 + **选择连接更多应用**。

### 机器学习

第 4 章：Python 与 Turi Create 入门

![](img/5720be5c3cca252e12448e68d25607b5_158_0.png)

在打开的“连接应用到 Google 云硬盘”窗口中，在搜索字段中搜索 colab，并选择 + 连接。

## 第 4 章：Python 与 Turi Create 入门

![](img/5720be5c3cca252e12448e68d25607b5_159_0.png)

安装成功后，关闭窗口，再次在任何处点击鼠标右键，在**更多**对话框中选择**Collaboratory**。这将打开一个新标签页或窗口，看起来非常像 Jupyter 笔记本。

### 机器学习

第 4 章：Python 与 Turi Create 入门

![](img/5720be5c3cca252e12448e68d25607b5_160_0.png)

通过点击标题并内联重命名，将文件重命名为 **getting-started.ipynb**。

![](img/5720be5c3cca252e12448e68d25607b5_160_1.png)

### 机器学习

## 第 4 章：Python 与 Turi Create 入门

从工具栏中，选择运行时（Runtime） > 更改运行时类型（Change Runtime type）。

![](img/5720be5c3cca252e12448e68d25607b5_161_0.png)

在打开的笔记本设置对话框中，将硬件加速（Hardware accelerator）从无（None）更改为 GPU。保存更改。

![](img/5720be5c3cca252e12448e68d25607b5_161_1.png)

### 机器学习

## 第 4 章：Python 与 Turi Create 入门

在笔记本的第一个代码单元中，粘贴以下代码：

```python
from google.colab import drive
drive.mount('/content/drive/')
```

这两行代码将把你的 Google 云硬盘文件夹导入笔记本。这需要允许 Colab 访问你的 Google 云硬盘文件夹。点击代码单元旁的小按钮。按照输出窗口中的说明操作，打开链接以赋予 Colab 访问你云硬盘的权限。你将获得一个访问代码并将其粘贴到笔记本中。

![](img/5720be5c3cca252e12448e68d25607b5_162_0.png)

### 机器学习

第 4 章：Python 与 Turi Create 入门

挂载完成后，添加一个新的代码单元，并运行以下代码：

```bash
ls "/content/drive/My Drive/machine-learning/snacks"
```

![](img/5720be5c3cca252e12448e68d25607b5_163_0.png)

你可能会注意到代码开头有一个感叹号。在允许运行系统命令的 Jupyter 特有语法中，你正尝试列出上传 snacks 数据集的目录内容。如果一切顺利，你现在应该能够将其设为 snacks 数据集的根目录。

你已经完成了 Google 笔记本环境环境的设置，并配置了使用 GPU，你可以将其用于本书的学习。值得重复的是，Colab 针对本书尚未经过测试，你在使用过程中可能会遇到问题。然而，对于想要进行机器学习但没有足够强大的计算机运行机器学习算法的开发者来说，它提供了一个极具吸引力的替代方案。

### 关键点

- 熟悉 Python。它在机器学习领域学术界的广泛应用意味着，如果你学会了 Python，你将非常抢手。
- 熟悉 Conda。
- 熟悉 Jupyter。

# 机器学习第 5 章：深入研究 Turi

当你运行此单元格时，你会发现特征提取的速度比上一章快得许多。这是因为 SqueezeNet 仅从 227×227 像素的图像中提取了 1000 个特征，而 VisionFeaturePrint_Screen 从 299×299 的图像中提取了 2048 个特征。

然而，你可能会对训练和验证准确率感到失望：

| 迭代次数 | 次数 | 步长 | 耗 | 训练准确率 | 验证准确率 |
|---|---|---|---|---|---|
| 9 | 16 | 1.000000 | 2.250278 | 0.447152 | 0.373901 |
| 24 | 41 | 1.000000 | 5.490575 | 0.597476 | 0.533058 |
| 49 | 77 | 1.000000 | 11.472903 | 0.706684 | 0.648760 |
| 74 | 113 | 1.000000 | 17.694513 | 0.755657 | 0.661157 |
| 99 | 162 | 1.000000 | 25.050267 | 0.803525 | 0.670412 |

> 注意：你得到的结果可能与书中显示的略有不同。请记住，未训练的模型（例如模型中的逻辑回归部分）是用随机数初始化的。这会导致不同训练运行之间存在差异。如果你得到的训练准确率远低于65%，请尝试重新运行。机器学习高级用户实际上会利用这些训练运行之间的差异，将多个模型组合成集成模型，从而提供更稳健的预测。

与 Create ML 一样，Turi Create 随机选择 5% 的训练数据作为验证数据，因此验证准确率在不同训练运行之间可能会很大差异。模型在你自己选择的较大的固定验证数据集上可能会表现更好（你将在本章中完成这一点）。

评估模型并显示指标：

```
metrics = model.evaluate(test_data)
print("Accuracy: ")
```

并没有意外 —— 率与验证准确率非常接近：

Accuracy: 0.6470588235294188

Precision: 0.644134936364582

Recall: 0.6445289115646259

# 获取单个预测结果

到目前为止，你只是重复了上一章的步骤。`evaluate()` 指标让你对模型的整体准确率有个大致的了解；你可以获取关于单个预测的更多信息。特别有趣的预测是那些模型错误但对自己正确非常有信心的情况。知道模型在哪里出错可以帮助你改进训练数据集。

![](img/5720be5c3cca252e12448e68d25607b5_169_0.png)

为了更深入地了解发生的情况，请运行以下单元格：

```
metrics.explore()
```

这会打开一个新窗口（仅限 Mac），让你能够可视化地检查准确率和其他指标。它还显示了正确分类以及——更有趣的是——错误分类的图像示例。非常有用！

| 模型 | 迭代次数 | 准确率 | F1 分数 | 总测试数 |
| :--- | :--- | :--- | :--- | :--- |
| squeezeneet_v1 | 135 | 64.71% | 64.43% | 952 |
| 类别名称 | 示例图像 | 准确率 | F1 分数 | 测试数量 |
| 芬 | | 46% | 47% | |
| 冰淇淋 | | 48% | 50% | |
| 蛋糕 | | 48% | 50% | |
| 饼干 | | 50% | 55% | |
| 椒盐结 | | 55% | 57% | 23 |
| 糖果 | | 55% | 64% | |
| 草莓 | | 61% | 62% | |

交互式评估窗口

### 预测与分类

Turi Create 模型除了 `evaluate()` 之外还有其他函数。在下一个单元格中输入并运行这些命令，然后等一会儿：

```
model.predict(test_data)
```

它显示了测试集中每张图像的实际预测：

[ 'apple', 'grape', 'orange', 'orange', 'orange', 'apple', 'orange', 'apple', 'candy', 'apple', 'grape', 'apple', 'strawberry', 'apple', 'apple', 'carrot', 'candy', 'ice cream', 'apple', 'apple', 'apple', ... ]

第一个预测对应于 `test_data[0]` 中的图像，第二个对应于 `test_data[1]`，依此类推。前 50 张图像全都是苹果，但模型将第二张图像分类为“grape（葡萄）”，请看一眼这张图像。在下一个单元格中输入并运行此命令：

```
plt.imshow(test_data[1]["image"])
```
