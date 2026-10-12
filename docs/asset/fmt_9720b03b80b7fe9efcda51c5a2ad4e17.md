
# 参考文献

- Ren S, He K, Girshick R and Sun J 2015 Faster R-CNN: towards real-time object detection with region proposal networks *Adv. Neural Inform. Process. Syst.* [**28** 91–9](http://dx.doi.org/10.5555/2969239.2969250)
- Roboflow, 2001. Chess Pieces Dataset [`public.roboflow.com/object-detection/chess-full`](https://public.roboflow.com/object-detection/chess-full)
- Wang C-Y, Bochkovskiy A and Liao H-Y M 2022 YOLOv7: trainable bag-of-freebies sets new state-of-the-art for real-time object detectors *arXiv preprint* arXiv:[2207.02696](http://arxiv.org/abs/2207.02696)

---

# IOP Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

---

# 第 8 章

## YOLOv7、YOLOv8、YOLOv9 和 YOLO-World

本章涵盖的主题是 `YOLOv7` 和 `YOLOv8`。由于 `YOLOv8` 安装简便且速度极快，读者只需专注于 `YOLOv8` 即可。在本章构建的自定义数据集 `MNIST4yolo` 的图像数字识别项目中，使用 `YOLOv8`、`YOLOv7` 和 `YOLO-NAS` 进行模型训练的时间分别为 0.5、12 和 4.0 小时。预训练的 `YOLOv8` 模型被用于目标检测、图像分割、图像分类、人体姿态估计、目标跟踪和计数。

自 Wang *et al* 2022 于 2023 年 7 月发表 `YOLOv7` 论文以来，我们拥有了更快、更准确的实时目标检测工具。我们无需编写代码即可实现它们，因为 `YOLOv7` 的源代码可以从 WongKinYiu 的 GitHub 网站下载并克隆到我们的计算机上。Kin-Yiu Wong 是 `YOLOv7` 论文的第一作者。通过安装网站上名为 `requirements.txt` 的文本文件中列出的库和模块，可以在配有 Python v3.9 的 VS Code 中轻松设置环境。在 VS Code 单元格中运行代码：`!python detect.py --conf 0.4 --nosave --view-img --source 0`，你将在电脑屏幕上看到带有边界框的自己。将手机举在摄像头前，你将在屏幕上看到两个边界框。如果想将目标检测视频保存到文件，只需从代码中删除 `--nosave` 选项。当你想终止摄像头的视频录制时，只需按键盘上的 `q` 键。将 source 后的数字 0 替换为带有绝对路径的视频文件名（如 `d:/traffic.mp4`），在播放从 YouTube 下载的视频文件时，你将看到带有边界框的汽车。当然，你也可以录制带有边界框的视频。在我的笔记本电脑上，`YOLOv7` 完成这些工作的速度比 `YOLOv3` 快约 10 倍。将源更改为单个图像文件名或一批带有绝对路径的图像文件（如 `d:/*.jpg`），你将在图像上看到带有边界框的物体。图像目标检测存在一个小问题：带有边界框的图像在屏幕上消失得太快。由于 `YOLOv7` 代码是用 PyTorch 编写的，我们可以在 VS Code 编辑器中打开 `detect.py` 文件。通过将文件第 138 行 `waitKey()` 中的等待时间从 1 毫秒替换为 3000 毫秒，你就能舒适地查看这些图像。你需要将视频的 `waitKey()` 等待时间改回 1 毫秒，否则视频播放速度会非常慢。

### 8.1 面向自定义数据集 MNIST4yolo 的 YOLOv7 目标检测

将 `YOLOv7` 应用于许多知名数据集并获得非常好的目标检测结果并不令人惊讶。我们也需要 `YOLOv7` 模型具备同样的能力，为自定义数据集提供优异的结果。尽管 Hugging Face、Roboflow 和 Kaggle 提供了许多免费的公共计算机视觉数据集，但我仍希望创建并使用我自己的数据集：`MNIST4yolo`。`MNIST4yolo` 数据集中每张黑白图像的分辨率为 448 × 448。项目 8.1 的单元格 01-04 中的代码可以基于 MNIST 图像为 `YOLOv7` 生成样本。照常，单元格 01 用于导入库并设置项目的超参数。在单元格 01 的最后一行，名为 `xml_path` 的字符串只是一个文件夹名称，用于保存合成图像及其边界框的纯文本文件。单元格 02 中的代码对我们来说应该很熟悉。通过它们，我们获得了一个 MNIST 训练数据加载器和一个 MNIST 测试数据加载器。

MNIST 数据加载器的每个批次包含 256 张从 MNIST 数据加载器中随机选取的 MNIST 图像。在一个 16 × 16 的数组中，总共 256 张 MNIST 图像被用于合成一张分辨率为 448 × 448 的大图像，用于 `MNIST4yolov7` 数据集。然后，使用单元格 03 第 06 行开始的 for 循环，我们遮盖约 245/256 张 MNIST 图像，使得在新数据集的合成图像上只有约 10 个数字可见。每个可见 MNIST 数字的位置和标签被记录用于边界框信息：`[label, x_c, y_c, w, h]`。每张 MNIST 图像的宽度和高度相同：28/448。单元格 05 中的一个 for 循环调用上述函数，分别为训练数据集保存 560 张大图像，为测试数据集保存 80 张大图像。当然，每张图像都有一个关于边界框的文本文件。我们无需对这些大图像及其边界框进行编码来构建数据集，因为预训练的 `YOLOv7` 模型将负责这项工作。单元格 01-05 中的代码应在 Python v3.6 中运行。否则，每张合成图像周围都会有一个白色边框。

![](img/bk978-0-7503-6244-3ch8uf1_pr.gif)

![](img/bk978-0-7503-6244-3ch8uf2_pr.gif)

我在名为 `MNIST4yolov7` 的文件夹中创建了两个子文件夹，一个名为 `train`，另一个名为 `test`。它们每个都有两个子文件夹：`images` 和 `labels`。单元格 05 中生成的合成图像及其文本文件（在 `xml_path` 文件夹中）被分别移动到 `MNIST4yolov7` 的子文件夹中。然后将 `MNIST4yolov7` 文件夹移动到从 WongKinYiu 的 GitHub 网站克隆的 `YOLOv7` 文件夹中。复制 `YOLOv7` 文件夹中的一个 `data.yaml` 文件并将其粘贴到 `MNIST4yolov7` 文件夹的 `train` 文件夹中。该文件可以用 MS 记事本或 VS Code 编辑，包含以下信息。

- `train`：`C:/Users/xiaoc/Python/Exercises/yolov7/MNIST4yolov7/train/images`
- `val`：`C:/Users/xiaoc/Python/Exercises/yolov7/MNIST4yolov7/test/images`
- `nc`：`10`
- `names`：`['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']`

在使用自定义数据集训练 YOLOv7 模型时，`data.yaml` 文件提供了关于图像位置、类别数量 (`nc`) 以及类别名称的信息。打开一个配有 Python v3.9 的新 VS Code 终端，并通过 DOS 命令 `cd yolov7` 将文件夹切换到 `yolov7`，因为预训练权重文件 `yolov7.pt` 位于那里。然后运行以下 DOS 命令，使用自定义数据训练 YOLOv7 模型：

```
python train.py --weight yolov7.pt --data MNIST4yolov7/data.yaml --batch-size 4
```

`train.py` 存在一个问题，许多人在网上搜索解决方案。对于我的电脑，一种解决方法是在 `yolov7` 文件夹下的 `train.py` 文件第 4 行的 `import os` 之后添加 `os.environ["KMP_DUPLICATE_LIB_OK"] = "TRUE"`。还有一个问题也困扰了许多人。模型训练的默认批次大小为 16。我的笔记本电脑内存不够大，所以我将批次大小减小到 4。一旦解决了第二个问题，漫长的训练过程便开始了。

默认训练轮数为 300。经过约 2.3 小时的模型训练后，我发现训练结果不佳。混淆矩阵（图 8.1）对角线上的数值较低。数字 3 和数字 5 的数值甚至低于 0.4。在理想结果中，混淆矩阵对角线上的每个数字都应等于 1。这意味着每个真实标签都能被 100% 正确预测。随后，我使用每次训练得到的最佳权重文件 `best.pt` 又进行了六次训练，每次将轮数设为 200。最终结果如图 8.1 所示。混淆矩阵对角线上 10 个数字的数值均高于 0.9。训练 200 个轮次耗时 1.5 小时。总训练时间约为 12 小时。在 VS Code 终端中使用以下命令，我得到了图 8.1 右下角显示的带有数字的黑白图像：

```
python detect.py --weights best6MNIST.pt --conf 0.4 --img-size 448 --view-img --source 0614.jpg
```

训练好的 YOLOv7 模型适用于 MNIST4yolov7 数据集。在纸上书写数字并将上述 DOS 命令中的 source 改为 0，我惊讶地发现训练好的模型无法识别我手写体中的任何数字。随后，我将 MNIST4yolov7 图像复制到手机上，将手机屏幕上显示的图像对准笔记本电脑的摄像头，训练好的模型工作良好。YOLOv7 模型很容易对 Chess 数据集进行训练。仅用 300 个轮次，训练结果就非常好。从 Rob Mulla 发布的 YouTube 视频 ([www.youtube.com/watch?v=RXbtSwZsoEU](https://www.youtube.com/watch?v=RXbtSwZsoEU)) 中，你可以了解更多关于如何使用 YOLOv7 训练自有数据集的信息。

![图 8.1. 使用 MNIST4yolo 数据集对预训练 YOLOv7 模型的训练结果。召回率-精确率曲线的空白中心是一个混淆矩阵。右下角的黑白图像是使用最后一次训练的权重文件检测图像 (0614.jpg) 得到的。](img/bk978-0-7503-6244-3ch8f1_online.jpg)

**图 8.1.** 使用 MNIST4yolo 数据集对预训练 YOLOv7 模型的训练结果。召回率-精确率曲线的空白中心是一个混淆矩阵。右下角的黑白图像是使用最后一次训练的权重文件检测图像 (0614.jpg) 得到的。

### 8.2 YOLOv7 实例分割

图像分割是一项计算机视觉任务，旨在将图像或视频帧划分为不同的区域或片段。它可用于帮助我们在更细粒度的层面上理解和分析图像内容。图像分割主要有三种。第一种是语义分割，它用相同的颜色标记同一类别所有目标的所有像素，甚至图像上的背景（天空、草地、树木）像素也会被标记上颜色。第二种是实例分割，它仅标记图像上可计数目标的像素，并且图像上同一类别的每个目标都通过不同的掩码颜色加以区分。第三种是全景分割，它是上述两种分割的结合。利用 Detectron2 的库，YOLOv7 模型可以为我们执行实例分割。Detectron2 是 Facebook (Meta AI) Research 推出的新一代开源目标检测框架。

在 WongKinYiu 的 GitHub 仓库网站上，有一个 mask 分支。mask 分支中的代码将 Detectron2 的一些模块与 YOLOv7 进行了集成。我们可以从 mask 分支下载一个 zip 文件，并将其解压到 VS Code 工作区中名为 `mask` 的文件夹内。YOLOv7 的虚拟环境可用于 mask 代码。我们还需要从 Detectron2 的 GitHub 仓库下载一个 zip 文件，并将其解压到一个名为 `detectron2` 的文件夹中。在我的 VS Code 工作区中，`detectron2` 文件夹、`mask` 文件夹和 `yolov7` 文件夹位于同一层级。有许多 YouTube 视频指导我们如何在电脑上安装 Detectron2。这并非易事，因为需要 Visual Studio 2022 来编译 `detectron2` 文件夹中的某些 C++ 文件。在我的电脑上，大多数问题源于 CUDA 库。解决 Detectron2 安装问题后，我们就能站在巨人的肩膀上做一些伟大的事情。打开一个新的 Jupyter 笔记本，将其命名为 `mask` 并保存在 VS Code 工作区中 `mask` 文件夹内，然后将项目 8.2 的单元格 01-05 复制到该笔记本中。单元格 01 第 04 至 06 行的代码从 `../mask/utils` 子文件夹中的文件导入库。第 07 至 10 行的代码从 `../detectron2` 子文件夹中的文件导入库。随后，单元格 02 中的代码导入 YOLOv7 模型，并加载预训练权重文件：`yolov7-mask.pt`。根据单元格 02 第 02 行的代码，许多超参数也从文件 `hyp.scratch.mask.yaml` 中导入。你可以在单元格 02 之后的一个额外 VS Code 单元格中使用 `print(hyp)` 来查看这些参数。

单元格 03 中的代码用于对任意输入图像或视频帧进行实例分割。这些代码源自 David Landup（[`stackabuse.com/instance-segmentation-with-yolov7-in-python/`](https://stackabuse.com/instance-segmentation-with-yolov7-in-python/)）和 WongKinYiu 的 GitHub 仓库（[`github.com/WongKinYiu/yolov7/tree/mask`](https://github.com/WongKinYiu/yolov7/tree/mask)），并经过修改。如果没有这两个网站提供的代码，几乎不可能了解模型的输出数据结构（单元格 03 的第 10–12 行）。第 17 行的“ROI Pooling”模块是“region of interest pooling”（感兴趣区域池化）的缩写，源自 Detectron2。单元格 03 的输出是一张带有实例分割的图像，其尺寸为原始图像尺寸（图 8.2(A)）。单元格 03 第 42–43 行的代码用于在图像上为物体添加彩色掩码。你可以在这两行代码前各加一个井号符号来将其停用，以仅查看目标检测结果（图 8.2(B)）。我们可以复用项目 7.5 中单元格 05–07 的函数，以显示文件夹中图像或视频的 YOLOv7 输出。在这些显示函数中，必须将 'yolov3' 改为 'yolov7'。预训练 YOLOv7 模型的视频帧处理速度约为 20 FPS。单元格 03 中定义的 `yolov7` 函数存在一个问题，我从 David Landup 的 [YouTube 视频](https://stackabuse.com/instance-segmentation-with-yolov7-in-python/) 中找到了解决方案。我们需要在文件 `C:\Users\xiaoc\miniconda3\Lib\site-packages\torch\nn\modules\upsampling.py` 中停用第 157 行，但保留该行的 ")"。当然，文件路径中的用户名会有所不同。

![](img/bk978-0-7503-6244-3ch8uf3_pr.gif)

![](img/bk978-0-7503-6244-3ch8uf4_pr.gif)

![图 8.2. (A) 图像的实例分割。(B) 无掩码的实例分割。视频帧处理速度约为 20 FPS。](img/bk978-0-7503-6244-3ch8f2_online.jpg)

**图 8.2.** (A) 图像的实例分割。(B) 无掩码的实例分割。视频帧处理速度约为 20 FPS。

### 8.3 使用 YOLOv7 进行人体姿态估计（关键点检测）

人体姿态估计是一项计算机视觉任务，用于从图像或视频帧中估计人体关节（关键点）的位置和朝向。姿态估计有许多应用。通过随时间跟踪一个人的姿态，可以分析和识别特定的动作或手势。人体关键点是我们身体运动的关键部位。YOLOv7 可追踪人体的 18 个关键点。人鼻尖为 0 号点。连接双肩的线段的中点为 1 号点。从左到右，六个点位于双臂关节上，六个点位于双腿关节上。然后两个点用于双眼，两个点用于双耳。通常，姿态估计需要昂贵的位置跟踪硬件。也有姿态估计软件，如 Google DeepPose 和 MediaPipe。它们分两阶段工作：人体检测和关键点检测。YOLOv7-pose 是一种单阶段多人关键点检测器。在 WongKinYiu 的 YOLOv7 GitHub 仓库中，有一个供我们下载的 pose 分支。将从该分支下载的文件解压到我们 VS Code 工作区的 'mask' 文件夹后，我们即可使用权重文件 `yolov7-w6-pose.pt` 运行预训练的关键点检测模型，以进行人体关键点检测（Maji *et al* 2022）。
