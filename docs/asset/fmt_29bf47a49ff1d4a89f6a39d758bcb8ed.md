
进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`。

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

---

```python
# 如果未提供视频路径，则获取摄像头
if not args.get("video"):
    camera = cv2.VideoCapture(0)

# 否则，加载视频
else:
    camera = cv2.VideoCapture(args["video"])
```

我们准备好开始循环处理视频中的帧了：

```python
# 持续循环
while True:
    # 获取当前帧
    grabbed, frame = camera.read()

    # 如果我们正在查看视频且没有获取到帧
    if args.get("video") and not grabbed:
        break
```

第 37 行从视频流中读取下一帧。如果没有获取到帧（即设置为`False`）且我们正在从视频流中读取帧，说明我们已到达文件末尾，因此跳出循环（第 41 和第 42 行）。否则，就可以对帧进行预处理，将其高度调整为 300 像素并转换为灰度图：

```python
# 调整帧的大小并转换为灰度图
frame = imutils.resize(frame, width=300)
gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
```

我们初始化了一个空画布（第 50 行），其宽度为 300px，高度为 200px。我们将使用这个画布来绘制 CNN 检测到的概率分布：

```python
# 初始化用于可视化的画布，然后克隆帧以便在上面进行绘制
canvas = np.zeros((200, 300, 3), dtype="uint8")
frameClone = frame.copy()
```

第 55-57 行使用 OpenCV 的 Haar 级联检测帧中的人脸。如果你对了解更多关于通过 Haar 进行目标检测知识，请参考 *Practical Python and OpenCV*（https://pyimagesearch.com/）。在接下来的代码中，我们通过 CNN 准备帧 ROI（感兴趣区域）：

```python
# 在输入帧中检测人脸，克隆画布以便在上面进行绘制
rects = detector.detectMultiScale(gray, scaleFactor=1.1, minNeighbors=6, minSize=(30, 30), flags=cv2.CASCADE_SCALE_IMAGE)
```

第 60 行确保帧中至少检测到一个人脸。如果检测到至少一个人脸，我们根据边界框的大小进行排序，将较大的人脸放在列表前面（第 62 和第 64 行）。

### 5 实时情绪检测

第 68 行从灰度图中提取人脸区域，然后通过将人脸调整大小为 48x48 像素来对其进行预处理（`EmotionVGGNet`需要此输入尺寸）。从那里开始，我们将`roi`转换为浮点数据类型，将其缩放到 [0,1] 范围，并将其转换为 Keras 兼容的数组（第 69-72 行）。

```python
# 在继续之前确保找到至少一张脸
if len(rects) > 0:
    # 确定最大的人脸区域
    rect = sorted(rects, reverse=True, key=lambda x: (x[2] - x[0]) * (x[3] - x[1]))[0]
    (fx, fy, fh, fw) = rect
    # 从图像中提取人脸 ROI，然后为网络进行预处理
    roi = gray[fy:fy+fh, fx:fx+fw]
    roi = cv2.resize(roi, (48, 48))
    roi = roi.astype('float32') / 255.0
    roi = img_to_array(roi)
    roi = np.expand_dims(roi, axis=0)
```

现在`roi`已经过预处理，我们可以将其通过模型获取类别概率：第 76 行调用模型的方法返回预测的类别概率。标签是概率最大的标签（第 77 行）。

```python
# 对 ROI 进行预测
```

由于人类面部表情是情绪的混合，观察标签的概率分布更有趣。为了实现这一点，我们在第 80 行遍历标签及其关联概率。第 86 和 87 行绘制条形图，每个条柱的宽度与预测的类别概率成比例。第 88-90 行在画布上绘制标签名称。

最后一个代码块详细演示了 OpenCV 绘制函数的工作原理，请参考 *Practical Python and OpenCV*（https://pyimagesearch.com/）。

我们的下一个代码块处理在屏幕上绘制概率最高的标签，并为我们预测情绪的人脸绘制边界框：

```python
# 在帧上绘制标签
cv2.putText(frameClone, label, (fx, fy - 10), cv2.FONT_HERSHEY_SIMPLEX, 0.45, (0, 0, 255), 2)
cv2.rectangle(frameClone, (fx, fy), (fx + fw, fy + fh), (0, 0, 255), 2)
```

我们实时可视化结果：简单的示例显示了输出以便查看：

```python
# 显示我们的分类 + 概率
cv2.imshow("Face", frameClone)
cv2.imshow("Probabilities", canvas)

# 如果按下 'q' 键，停止循环
if cv2.waitKey(1) & 0xFF == ord("q"):
    break

# 清理摄像头
camera.release()
cv2.destroyAllWindows()
```

在这个案例研究中，我们将学习如何应用迁移学习（特别是特征提取）来自动检测并纠正图像的朝向。我们之所以从预训练的卷积神经网络（CNN）中提取特征有两点：

- 1. 证明在 ImageNet 上训练的 CNN 所学习的滤波器（filters）在整个 360 度范围内并不具有旋转不变性（否则，这些特征将无法区分图像的旋转）。

- 2. 通过特征提取进行迁移学习在预测图像朝向时可以获得最高的准确率。

正如在《入门包》第 11 章中提到的，有一个常见的误区，认为 CNN 学习的单个滤波器对旋转是不不变的——实际上，滤波器本身并不是的。相反，CNN 能够学习到某些滤波器，当它们在给定旋转下看到特定物体时会激活。因此，滤波器之所以不变，是因为滤波器的数量，理想情况下，其中一些滤波器会在各种旋转下激活。我们将在本章中看到，CNN 并不是完全旋转不变的，否则我们根本无法仅从微调阶段提取的特征来确定图像的朝向。

## 12.1 室内 CVPR 数据集

我们将在此案例研究中使用的数据集是 MIT 发布的室内场景识别（也称为 CVPR）数据集 [36]。该数据库包含 67 种室内房间/场景类别，包括家、办公室、公共空间、商店等等。该数据集的示例见图 12.1。

我们使用这个数据集的原因是，人类非常容易判断一张自然场景图像的朝向是否错误——我们的目标是使用卷积神经网络复制这种水平的性能。然而，Indoor CVPR 中的所有图像的朝向都是正确的；因此，我们需要根据 Indoor CVPR 构建一个包含带有各种旋转标签图像的自定义数据集。

下载 Indoor CVPR 数据集请使用此链接：

![](img/7db52e410ee84ec5a30b3190e73b61d3_167_0.png)

图 12.1：室内场景识别数据集 [36] 中的类别和图像示例。

http://pyimg.com/x772x

点击“Download”链接即可。整个 .tar 压缩包约为 2.4GB，请相应地规划下载。文件下载完成后，将其解压。解压后，你会发现一个名为`Images`的目录，其中包含许多子目录，每个子目录包含数据集中的特定类别：

```
cd Images
ls -l | head -n 10
total
drwxr-xr-x 610 adrianrosebrock staff 20740 Mar 16 2009 airport_inside
drwxr-xr-x 142 adrianrosebrock staff 4828 Mar 16 2009 artstudio
drwxr-xr-x 178 adrianrosebrock staff 6052 Mar 16 2009 auditorium
drwxr-xr-x 407 adrianrosebrock staff 13838 Mar 16 2009 bakery
drwxr-xr-x 606 adrianrosebrock staff 20604 Mar 16 2009 bar
drwxr-xr-x 199 adrianrosebrock staff 6766 Mar 16 2009 bathroom
drwxr-xr-x 664 adrianrosebrock staff 22576 Mar 16 2009 bedroom
drwxr-xr-x 382 adrianrosebrock staff 29888 Mar 16 2009 bookstore
drwxr-xr-x 215 adrianrosebrock staff 7310 Mar 16 2009 bowling
```

为了保持 CVPR 数据集的整洁，我创建了一个名为`indoor_cvpr`的新目录，将`Images`目录移动到其中（将大写“I”改为小写“i”），并创建了两个子目录——`hdf5`和`rotated_images`。我的项目目录结构如下：

```
indoor_cvpr
  - hdf5
  - images
  - rotated_images
```

`hdf5`目录将存储使用预训练的卷积神经网络从我们的输入图像中提取的特征。为了生成训练数据，我们将创建一个自定义 Python 脚本来随机旋转图像。这些旋转后的图像将存储在 HDF5 数据集中。

### 12.1.1 构建数据集

在开始之前，让我们先我们的项目结构：

```
image_orientation
  - create_dataset.py
```

## 12.1 室内 CVPR 数据集

```
| --- extract_features.py |
| --- indoor_cvpr/ |
| --- models/ |
| --- orient_images.py |
| --- train_model.py |
```

我们将使用`create_dataset.py`脚本为输入数据集构建训练集和测试集。之后，`extract_features.py`将用于创建数据的 HDF5 文件。根据提取的特征，可以使用`train_model.py`训练逻辑回归分类器来识别图像朝向，并将结果保存在`models`目录。最后，`orient_images.py`将用于处理测试图像。与之前的示例一样，我们需要创建一个包含各种朝向的数据集。我们将通过对原始图像进行 0、90、180 和 270 度旋转来实现。

以下是创建数据集的代码：

```python
import os
import cv2
import numpy as np
import random
import h5py
import argparse
import imutils
from tqdm import tqdm

parser = argparse.ArgumentParser(description="Create image orientation dataset")
parser.add_argument("--dataset", type=str, help="Path to the input dataset")
parser.add_argument("--output", type=str, help="Path to the output HDF5 file")
args = parser.parse_args()

images_path = os.path.join(args.dataset, "images")
image_classes = [d for d in os.listdir(images_path) if os.path.isdir(os.path.join(images_path, d))]

with h5py.File(args.output, 'w') as hf:
    for class_name in tqdm(image_classes, desc="Processing classes"):
        class_group = hf.create_group(class_name)
        class_path = os.path.join(images_path, class_name)
        for img_name in os.listdir(class_path):
            img_path = os.path.join(class_path, img_name)
            image = cv2.imread(img_path)
            if image is None:
                continue
            for angle in [0, 90, 180, 270]:
                rotated_img = imutils.rotate_bound(image, angle)
                dataset = class_group.create_dataset(f"{img_name}_{angle}", data=rotated_img)
```

现在我们有了一个包含各种朝向图像的 HDF5 文件。在下一节中，我们将学习如何从这些图像中提取特征。

## 12.1 室内 CVPR 数据集

**第 46 行**按角度旋转我们的图像，确保**整张图像保持**在视野内（http://pyimg.co/7xnmk6）。然后，我们再次根据角度确定图像的输出路径。这意味着我们的输出数据集将具有以下目录结构：

```
/output/{angle_name}/{image_filename}.jpg
```

**第 50 和第 51 行**检查`/output/{angle_name}`目录是否存在，如果不存在，则创建所需的子目录。通过使用输出路径，我们可以在**第 55-58 行**通过提取内容推导出实际图像的路径：

- 1. 原始图像扩展名。

- 2. 当前给定角度选定的图像数量。

- 3. 最后，**第 61 行**将我们的输出写入正确的角度子目录，确保我们可以通过简单检查文件路径来轻松确定图像的标签。例如，`/rotated_images/180/image_00000.jpg`因为位于`180`子目录中，所以已经旋转了 180 度。

为了跟踪每个角度的图像数量，我们在下面的代码中更新角度计数字典：

```python
# update the count for the angle
c = angles.get(angle, 0)
angles[angle] = c + 1
bar.update(i)
```

最后，我们在数据集中显示每个角度图像数量的统计信息：

```python
# finish the progress bar
bar.finish()

# loop over the angles and display counts for each of them
for angle in sorted(angles.keys()):
    print("[INFO] angle={}: {}".format(angle, angles[angle]))
```

构建图像数据集，打开终端并执行以下命令：

```bash
$ python create_dataset.py --dataset indoor_cvpr/ \
--output indoor_cvpr/rotated_images
Building Dataset: 1000 | #######################
[INFO] angle=0: 2487
[INFO] angle=90: 2480
[INFO] angle=180: 2525
[INFO] angle=270: 2483
```

从输出结果可以看出，数据集创建过程耗时 1m19s，每个旋转角度约有 2,500 张图像（由于随机采样过程会有几张的偏差）。现在我们已经创建了数据集，可以继续通过特征提取应用迁移学习；这些特征将用于逻辑回归分类器，以预测（并纠正）输入图像的方向。

## 12.2 提取特征

为了从我们的数据集中提取特征，我们将使用在 ImageNet 数据集上预训练过的 VGG16 网络架构。此脚本与我们在《Practitioner Bundle》第 3 章中实现的脚本相同。我们之所以能够重用相同的代码是因为：

- 1. 我们在整本书中构建的工具具有模块化，确保当输入数据集遵循特定的目录结构时，我们可以重用提供的脚本。

- 2. 确保我们的图像遵循目录结构`/dataset_name/class_label/example image.jpg`。

为了完整起见，我将在下方回顾`extract_features.py`，但需更多详细信息，请参考《Practitioner Bundle》的第 3 章：

```python
# import the necessary packages
from keras.applications import VGG16
from keras.applications import imagenet_utils
from keras.preprocessing.image import img_to_array
from keras.preprocessing.image import load_img
from sklearn.preprocessing import LabelEncoder
from dataset import HDF5DatasetWriter
import numpy as np
import progressbar
import argparse
import random
import os
```
