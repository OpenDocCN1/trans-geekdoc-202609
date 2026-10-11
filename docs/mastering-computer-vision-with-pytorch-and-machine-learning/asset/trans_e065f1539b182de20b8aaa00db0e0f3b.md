

# Pascal VOC 2012 与国际象棋棋子数据集

Pascal VOC 2012 数据库并非一个现成的数据集。利用 Utility 01–04 中定义的辅助函数，我们可以将那些图像及其标签打包成用于 YOLOv1 模型训练的数据集。然而，Pascal VOC 2012 数据集对于我的笔记本电脑来说太大了。根据 Redmon *et al* [2016](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib6) 的记载，YOLOv1 模型的前 20 个卷积层是在 ImageNet 数据集上训练了一周。随后又增加了 4 个卷积层和 2 个全连接层，并利用 PASCAL VOC 2007 和 2012 的图像进行了更长时间的训练。为了演示 YOLOv1 模型训练，我必须使用一个小型数据集：国际象棋棋子数据集。2021 年 2 月，Roboflow 以公共许可证免费发布了该数据集。在一个 17 MB 的 zip 文件中，包含 693 张图像，分为 13 个类别，用于 YOLOv7 模型训练。关于棋子图像的边界框信息存储在文本文件中，而非 XML 文件。从这些文件中可以看到每个物体的类别索引、物体中心坐标、以及归一化到 416 后的边界框宽度和高度。以下是第一张测试图像（白象棋子）的标签文本文件示例：

```
7 0.5120192307692307 0.0829326923076923 0.04567307692307692 0.13341346153846154
```

所有图像文件和标签文件位于名为 `Chess` 的文件夹下的三个子文件夹中：`train`、`test` 和 `valid`。`Utility 05` 中的代码可用于将这三个子文件夹中的文本文件转换为用于 YOLOv1 模型训练的 XML 文件。由于原始文件名过长难以记忆，`Utility 05` 第 20 行的代码将文件名更改为三位整数。由白象文本文件转换而来的 XML 文件如下所示。该 XML 文件结构比 VOC 数据集中的更简单。在 `<object>` 项下没有 `<bndbox>` 项。当我们为数据集打包这些文件时，必须删除 `Utility 01` 第 10 到 11 行中的 `['bndbox']` 以适配棋子数据集。请注意第 20 行 `str(idx + I)` 中的整数。使用 `Utility 05`，`train`、`valid` 和 `test` 子文件夹中的所有 693 个样本被转换并移动到一个名为 `chess4yolov1` 的文件夹中，该文件夹包含两个子文件夹：`Annotations` 和 `JPEGimages`。转换后的样本文件名为从 `000` 到 `692` 的三位数字。如果 `Utility 05` 第 3 行的根文件夹设置为 `train` 子文件夹，则第 20 行 `str(idx + I)` 中的整数 `I` 等于 `0`；对于 `valid` 子文件夹，`I` 等于 `606`；对于 `test` 子文件夹，`I` 等于 `664`。名为 `688` 的样本被删除，因为 `688.xml` 为空。数据集中存在无目标样本会导致我的代码在模型训练期间出现问题。`Utility 05` 中的代码可在配合 Python 3.9 的 VS Code 中运行，不支持 Python 3.6，因为后者不支持将 pandas DataFrame 写入 XML 文件。

![](images/bk978-0-7503-6244-3ch7uf5_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf6_pr.gif)

运行 `Utility 05` 中针对 `train`、`test` 和 `valid` 三个子文件夹文件的代码后，图像文件被获取并移动到 `JPEGimages` 子文件夹，所有 XML 文件被移动到 `Annotations` 文件夹。在随后的项目 [7.1](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7ueqn8) 将这些文件打包成数据集之前，Cell 01 中导入了项目所需的所有模块或工具，并设置了超参数。对于我拥有 6 GB 显存的 RTX 2060 GPU，最大批次大小为 8。使用 Kaggle 免费的 16 GB GPU 显存，最大批次大小可达 128。通常，较小的批次大小训练效果更好。Cell 01 的最后两行分别用于列出 XML 文件列表和图像文件列表。我必须将 `Utility 01` 放在 Cell 01 之后，因为 Chess 数据集的 XML 文件结构与 VOC 数据集不同。Cell 02 中构建的 Chess 数据集被随机分割为三个数据集，从而得到一个训练 dataloader、一个验证 dataloader 和一个测试 dataloader。它们的样本数量分别为 560、80 和 52。Cell 04 中的代码用于显示 dataloader 中的部分图像。Cell 03 中定义的名为 `grid2bboxes` 的函数提取图像编码网格单元的信息，作为边界框的参数。

![](images/bk978-0-7503-6244-3ch7uf7_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf8_pr.gif)

## 7.3 ResNet18 模型、IOU 与损失函数

### 7.3.1 使用 ResNet18 替代 YOLOv1 模型

YOLOv1 模型并无“超能力”，它只是一个由 24 个卷积层后接两个全连接层组成的线性 CNN 模型。2022 年 7 月，我们有了 YOLOv7 模型（Wang *et al* [2022](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib9)）。2023 年 1 月，Ultralytics 发布了更强大的 YOLOv8 模型。简单的 YOLOv1 仍有助于我们理解 YOLO 算法。原始 YOLOv1 模型未使用批量归一化，因为批量归一化（Ioffe and Szegedy [2015](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib4)）比 YOLOv1 晚发明了一年。在 Aladdin Persson 的 GitHub 中，原始 YOLOv1 模型通过在每次卷积操作后添加批量归一化进行了修改。然而，修改后的 YOLOv1 在我的笔记本电脑上对于 Pascal VOC 数据集仍不够强大，因此使用预训练的 ResNet18（第 [2.4](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2s2-4) 节）作为 Chess 数据集的模型。在 Cell 05 的第一行，从 `torchvision` 的 `models` 中导入了预训练的 ResNet18 模型。随后将 ResNet18 最后一个全连接层的输出变量数量从 1000 改为 1127（= 7 × 7 × 23），用于每个 7 × 7 网格单元中 23 个立方体的预测值。我在模型训练的前 100 个 epoch 中仅使用了预训练的 ResNet18 模型。前 100 个 epoch 训练结束时，我将训练好的模型保存到名为 `Chess-Yolo-01.pth` 的文件中，并将第 9 行的 `'''inline-graphic style="height:0.5em;" xlink:href="bk978-0-7503-6244-3ch7ieqn5.gif"/'` 符号移至第 1 行前面。这样我就可以在接下来的 100 个 epoch 中使用该训练好的模型。训练模型文件名应通过增加前一个文件名的最后一位数字来更改。使用 Python v3.6，运行 Cell 09 中的代码进行模型训练每 100 个 epoch 约需 54 分钟。使用 Python v3.9，相同代码的模型训练时间为 37 分钟。在两天约 20 小时内，模型训练给出了足够好的结果（图 [7.3](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7fig3)）。在 Chess 项目中，Adam 优化器似乎优于 SGD 优化器。模型训练期间，学习率由 `ReduceLROnPlateau` 调度器调整。平均精度均值（mAP）是目标检测模型训练的重要指标。如果 mAP 高于 0.5，模型训练足够好；mAP 约 0.7 为良好；mAP 高于 0.9 为优秀。对于优秀的模型训练，图 [7.3](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7fig3) 中的真实边界框和预测边界框应当相同。

![](images/bk978-0-7503-6244-3ch7uf9_pr.gif)

![Figure 7.3. A test image with its true bounding boxes (yellow) and predicted bounding boxes (red) at the end of model training with 100 × 21 epochs. Final mAP for the train, validation and test dataloaders is 0.76, 0.62 and 0.66, respectively. Model training time is 37 min for every 100 epochs. The Chess Pieces Dataset is from Roboflow (2001) with a license CC BY 4.0.](images/bk978-0-7503-6244-3ch7f3_online.jpg)

**Figure 7.3.** A test image with its true bounding boxes (yellow) and predicted bounding boxes (red) at the end of model training with 100 × 21 epochs. Final mAP for the train, validation and test dataloaders is 0.76, 0.62 and 0.66, respectively. Model training time is 37 min for every 100 epochs. The Chess Pieces Dataset is from Roboflow ([2001](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib10)) with a license CC BY 4.0.

