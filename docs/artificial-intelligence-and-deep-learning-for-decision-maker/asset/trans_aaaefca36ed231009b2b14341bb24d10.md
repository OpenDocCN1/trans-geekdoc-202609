
使用交叉验证，用户可以估计特定学习方法的测试误差，其次，他们可以选择所选学习方法的最佳灵活性，以最小化与偏差和方差相关的误差。

## 性能指标

指标用于衡量和比较算法的性能。各种指标例如混淆矩阵和 ROC 曲线下的面积可用于检查预测结果的准确性。

## 超参数优化

超参数用于检测训练和测试模型所需的大致时间。

## 模型评估与模式预测

在选择在训练数据集上拟合良好的模型后，下一步是在测试数据集上应用该模型以预测模式。如果它产生令人满意的结果，所选模型可用于预测新数据。

例如，让我们以热板为例，其目标是检测板是否发热以及检测板中的裂纹。数据集包含板的图像，任务是识别板上可能存在裂纹的区域：

![](OEBPS/images/Fig1.16.jpg)

**图 1.16：** 真实带裂纹的热板图像

收集数据的各个步骤如下。

### 数据收集

1. 数据以 `.jpg` 图像的形式存在。因此，为了从图像中检测对象，需要对图像进行标注，即在图像中标记所需对象，以便机器能够学习需要识别的对象。
2. 有各种工具可用于解释图像，例如 `Labellmg` 和 `Labelme`。为了以精确的多边形图像形式进行标注，我们将使用 `Labelme` 工具，因为 `Labellmg` 工具用于以矩形框形式解释对象。进行标注时，首先打开 `Labelme` 标注工具并登录账户。然后创建上传图像的集合（一次最多上传 20 张图像）。在图像上围绕所需对象绘制多边形边界。绘制边界后，命名标签并保存 `.jpg` 和标注文件。因此，使用 `Labelme` 工具，图像被解释并以 `XML` 文件的形式保存。
3. 之后，为了从图像中获取所需检测对象的点，使用 `OpenCV` 生成掩码以查找轮廓函数：
```
ret,thresh = cv2.threshold(imgray,127,255,0)
#setting the threshold value to classify the pixel values of the image
im2, contours, hierarchy = cv2.findContours(thresh,cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)
#finding the white object from the black background
#first one is the source image, second is the contour retrieval mode and third is the contour approximation method
#get the result as a list of points in the form of list as "contours"
```
4. 观察到图像数量不足以实现目标检测。因此，使用数据增强方法增加图像数量。可以使用 `Augmentor` Python 库进行许多操作。`Augmentor` 是一个 Python 库，用于执行增强并为机器学习和深度学习任务人工生成图像数据。使用 `Augmentor` Python 库，通过指定操作来开发管道。执行管道并将所有结果保存在指定目录的路径中。
5. 以下是几个函数：
```
p.rotate(probability=0.7, max_left=10, max_right=10)
#rotating the image with probability 0.7 and maximum movement towards left and right is 10
p.zoom(probability=0.5, min_factor=1.1, max_factor=1.5)
#zooming the image with 0.5 probability within certain range of factor
```

### 数据预处理

1. 从上述获得的 `XML` 文件中，使用 for 循环获取点，并将接收到的结果以 `CSV` 文件的形式存储。
2. 之后，观察到目标检测 API 不能在多边形点上工作；它只在矩形边界框上工作。因此，需要将多边形点转换为矩形边界框。它使用 `planar` 库和边界框函数执行。以下是一个示例：
```
for j in cor_list:
bbox1 = BoundingBox(j)
# the points are listed in "cor_list" and BoundingBox function is used to fetch points in the form of rectangular box
box_list_xmin.append(bbox1.min_point.x)
box_list_ymin.append(bbox1.min_point.y)
box_list_xmax.append(bbox1.max_point.x)
box_list_ymax.append(bbox1.max_point.y)
#fetch the extreme points of x and y and append them in the lists
```
3. 然后，我们观察到有关图像高度和图像宽度的信息缺失，然而，这对于实现目标检测模块是必要的。因此，使用 `PIL` 库来获取它。示例如下：
```
for xml_file in glob.glob(image_path + '/*.jpg'):
xml_data = Image.open(xml_file)
size_image = list(xml_data.size)
value = size_image, os.path.basename(xml_file)
list.append(value)
#fetch all the jpg files from the given specified using glob python library
#Open the fetched file
#fetch the height and width of the image using "size" function of PIL python library
#store the name of the file with its image in a variable and append them into the list
```

### 数据准备

1. 在数据预处理后，它按 80% 和 20% 的比例拆分为训练和测试数据集。
2. 之后，训练和测试数据集都转换为 `Tf.record` 文件。`Tf.record` 文件是 `Tensorflow` 框架的格式，它将其用作训练模型的输入。`Tf.record` 根据图像上获取的点创建边界。

### 数据训练

首先，安装 `Tensorflow` 的目标检测 API。
1. 创建名为 `data` 的目录，在其中下载模型：
```
From tensorflow/models/research/
mkdir data
#command to create tfrecords
```
2. 创建目录后，请按照以下说明操作：
   1. 将 `Train` 和 `Test tf.record` 文件传输到 `data` 目录中。
   2. 将裂纹检测标签文件传输到 `data` 目录中。
   3. 创建名为 `new_crack_model` 的目录，在其中下载模型：
```
#From tensorflow/models/research/
mkdir new_crack_model
```
3. 创建目录后，请按照以下说明操作：
   1. 将配置文件传输到 `new_crack_model` 目录中。
   2. 按照主流程的 *步骤 3* 和 *4* 操作。
   3. 在 `new_crack_model` 内创建名为 `train` 的目录。
```
From tensorflow/models/research/
mkdir train
```
4. 创建目录后，请按照以下说明操作：
   1. 将 `model.ckpt.data-00000-of-00001, model.ckpt.index and model.ckpt.meta` 文件从 `faster_rcnn_resnet101_coco_11_06_2017` 预训练模型传输到 `train` 目录。
   2. 在 `new_crack_model` 目录内创建名为 `eval` 的目录：
```
# From tensorflow/models/research/
mkdir eval
```

### 实现步骤

* 在给定的配置文件中设置路径：
  * 设置初始检查点的路径。
  * 设置裂纹检测标签文件的路径。
  * 设置训练记录文件的路径。
  * 设置测试记录文件的路径。
* 使用以下命令开始训练模型：
```
python object_detection/train.py \
--logtostderr \
--pipeline_config_path="path of configuration file" \
--train_dir="path of train directory"
```
