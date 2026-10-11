

![](images/bk978-0-7503-6244-3ch7uf20a_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf20b_pr.gif)

### 参考文献

Everingham M, Gool L V, Williams C, Winn J and Zisserman A 2012 The PASCAL visual object classes challenge 2012 (VOC2012) results [http://www.pascal-network.org/challenges/VOC/voc2012/workshop/index.html](http://www.pascal-network.org/challenges/VOC/voc2012/workshop/index.html)

Girshick R 2015 Fast R-CNN *Proc. of the IEEE Int. Conf. on Computer Vision* pp 1440–8

Girshick R, Donahue J, Darrell T and Malik J 2014 Rich feature hierarchies for accurate object detection and semantic segmentation *Proc. of the IEEE Conf. on Computer Vision and Pattern Recognition* pp 580–7

Ioffe S and Szegedy C 2015 Batch normalization: accelerating deep network training by reducing internal covariate shift *Int. Conf. on Machine Learning* (PMLR) pp 448–56

Liu W, Anguelov D, Erhan D, Szegedy C, Reed S, Fu C-Y and Berg A C 2016 Ssd: Single shot multibox detector *European Conf. on Computer Vision* (Berlin: Springer) pp 21–37

Redmon J, Divvala S, Girshick R and Farhadi A 2016 You only look once: unified, real-time object detection *Proc. of the IEEE Conf. on Computer Vision and Pattern Recognition* pp 779–88

Redmon J and Farhadi A 2018 Yolov3: an incremental improvement *arXiv preprint* arXiv:[1804.02767](http://arxiv.org/abs/1804.02767)

Ren S, He K, Girshick R and Sun J 2015 Faster R-CNN: towards real-time object detection with region proposal networks *Adv. Neural Inform. Process. Syst.* [**28** 91–9](http://dx.doi.org/10.5555/2969239.2969250)

Roboflow, 2001. Chess Pieces Dataset [https://public.roboflow.com/object-detection/chess-full](https://public.roboflow.com/object-detection/chess-full)

Wang C-Y, Bochkovskiy A and Liao H-Y M 2022 YOLOv7: trainable bag-of-freebies sets new state-of-the-art for real-time object detectors *arXiv preprint* arXiv:[2207.02696](http://arxiv.org/abs/2207.02696)

* * *

# IOP Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

# 第 8 章

## YOLOv7、YOLOv8、YOLOv9 和 YOLO-World

本章涵盖的主题是 `YOLOv7` 和 `YOLOv8`。由于 `YOLOv8` 安装简便且速度极快，读者只需专注于 `YOLOv8` 即可。在本章构建的自定义数据集 `MNIST4yolo` 的图像数字识别项目中，使用 `YOLOv8`、`YOLOv7` 和 `YOLO-NAS` 进行模型训练的时间分别为 0.5、12 和 4.0 小时。预训练的 `YOLOv8` 模型被用于目标检测、图像分割、图像分类、人体姿态估计、目标跟踪和计数。

自 Wang *et al* [2022](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8bib2) 于 2023 年 7 月发表 `YOLOv7` 论文以来，我们拥有了更快、更准确的实时目标检测工具。我们无需编写代码即可实现它们，因为 `YOLOv7` 的源代码可以从 WongKinYiu 的 GitHub 网站下载并克隆到我们的计算机上。Kin-Yiu Wong 是 `YOLOv7` 论文的第一作者。通过安装网站上名为 `requirements.txt` 的文本文件中列出的库和模块，可以在配有 Python v3.9 的 VS Code 中轻松设置环境。在 VS Code 单元格中运行代码：`!python detect.py --conf 0.4 --nosave --view-img --source 0`，你将在电脑屏幕上看到带有边界框的自己。将手机举在摄像头前，你将在屏幕上看到两个边界框。如果想将目标检测视频保存到文件，只需从代码中删除 `--nosave` 选项。当你想终止摄像头的视频录制时，只需按键盘上的 `q` 键。将 source 后的数字 0 替换为带有绝对路径的视频文件名（如 `d:/traffic.mp4`），在播放从 YouTube 下载的视频文件时，你将看到带有边界框的汽车。当然，你也可以录制带有边界框的视频。在我的笔记本电脑上，`YOLOv7` 完成这些工作的速度比 `YOLOv3` 快约 10 倍。将源更改为单个图像文件名或一批带有绝对路径的图像文件（如 `d:/*.jpg`），你将在图像上看到带有边界框的物体。图像目标检测存在一个小问题：带有边界框的图像在屏幕上消失得太快。由于 `YOLOv7` 代码是用 PyTorch 编写的，我们可以在 VS Code 编辑器中打开 `detect.py` 文件。通过将文件第 138 行 `waitKey()` 中的等待时间从 1 毫秒替换为 3000 毫秒，你就能舒适地查看这些图像。你需要将视频的 `waitKey()` 等待时间改回 1 毫秒，否则视频播放速度会非常慢。

### 8.1 面向自定义数据集 MNIST4yolo 的 YOLOv7 目标检测

将 `YOLOv7` 应用于许多知名数据集并获得非常好的目标检测结果并不令人惊讶。我们也需要 `YOLOv7` 模型具备同样的能力，为自定义数据集提供优异的结果。尽管 Hugging Face、Roboflow 和 Kaggle 提供了许多免费的公共计算机视觉数据集，但我仍希望创建并使用我自己的数据集：`MNIST4yolo`。`MNIST4yolo` 数据集中每张黑白图像的分辨率为 448 × 448。项目 [8.1](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8ueqn1) 的单元格 01-04 中的代码可以基于 MNIST 图像为 `YOLOv7` 生成样本。照常，单元格 01 用于导入库并设置项目的超参数。在单元格 01 的最后一行，名为 `xml_path` 的字符串只是一个文件夹名称，用于保存合成图像及其边界框的纯文本文件。单元格 02 中的代码对我们来说应该很熟悉。通过它们，我们获得了一个 MNIST 训练数据加载器和一个 MNIST 测试数据加载器。

MNIST 数据加载器的每个批次包含 256 张从 MNIST 数据加载器中随机选取的 MNIST 图像。在一个 16 × 16 的数组中，总共 256 张 MNIST 图像被用于合成一张分辨率为 448 × 448 的大图像，用于 `MNIST4yolov7` 数据集。然后，使用单元格 03 第 06 行开始的 for 循环，我们遮盖约 245/256 张 MNIST 图像，使得在新数据集的合成图像上只有约 10 个数字可见。每个可见 MNIST 数字的位置和标签被记录用于边界框信息：`[label, x_c, y_c, w, h]`。每张 MNIST 图像的宽度和高度相同：28/448。单元格 05 中的一个 for 循环调用上述函数，分别为训练数据集保存 560 张大图像，为测试数据集保存 80 张大图像。当然，每张图像都有一个关于边界框的文本文件。我们无需对这些大图像及其边界框进行编码来构建数据集，因为预训练的 `YOLOv7` 模型将负责这项工作。单元格 01-05 中的代码应在 Python v3.6 中运行。否则，每张合成图像周围都会有一个白色边框。

![](images/bk978-0-7503-6244-3ch8uf1_pr.gif)

![](images/bk978-0-7503-6244-3ch8uf2_pr.gif)

我在名为 `MNIST4yolov7` 的文件夹中创建了两个子文件夹，一个名为 `train`，另一个名为 `test`。它们每个都有两个子文件夹：`images` 和 `labels`。单元格 05 中生成的合成图像及其文本文件（在 `xml_path` 文件夹中）被分别移动到 `MNIST4yolov7` 的子文件夹中。然后将 `MNIST4yolov7` 文件夹移动到从 WongKinYiu 的 GitHub 网站克隆的 `YOLOv7` 文件夹中。复制 `YOLOv7` 文件夹中的一个 `data.yaml` 文件并将其粘贴到 `MNIST4yolov7` 文件夹的 `train` 文件夹中。该文件可以用 MS 记事本或 VS Code 编辑，包含以下信息。

*   `train`：`C:/Users/xiaoc/Python/Exercises/yolov7/MNIST4yolov7/train/images`
*   `val`：`C:/Users/xiaoc/Python/Exercises/yolov7/MNIST4yolov7/test/images`
*   `nc`：`10`
*   `names`：`['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']`

