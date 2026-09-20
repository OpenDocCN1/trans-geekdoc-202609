# 深度学习 MATLAB 应用














## 5.12 使用自定义特征袋的图像检索







# 使用 MATLAB 的卷积神经网络。函数。

## 8.2.1 创建图像输入层：`imageInputLayer`
## 8.2.2 创建 2D 卷积层：`convolution2dLayer`
## 8.2.3 创建线性整流单元（ReLU）层：`reluLayer`
## 8.2.4 创建局部响应归一化层：`crossChannelNormalizationLayer`
## 8.2.5 创建平均池化层：`averagePooling2dLayer`
## 8.2.6 创建最大池化层：`maxPooling2dLayer`
## 8.2.7 创建全连接层：`fullyConnectedLayer`
## 8.2.8 创建丢弃层：`dropoutLayer`
## 8.2.9 创建 softmax 层：`softmaxLayer`
## 8.2.10 创建分类输出层：`classificationLayer`

## 8.3.1 训练网络：`trainNetwork`
## 8.3.2 神经网络训练选项。`trainingOptions`

# 8.4 提取特征和预测结果。函数。

## 8.4.1 计算网络层激活值：`activations`
## 8.4.2 使用训练过的网络预测响应：`predict`
## 8.4.3 使用训练过的网络分类数据：`classify`

# 使用 MATLAB 的卷积神经网络。类。

## 9.2.1 网络层：`layer`
## 9.3.1 序列网络类：`SeriesNetwork`
## 9.3.2 带有动量的随机梯度下降训练选项。`TrainingOptionsSGDM`
## 9.4.1 `ImageInputLayer` 类
## 9.4.2 `Convolution2DLayer` 类
## 9.4.3 `ReLULayer` 类
## 9.4.4 `CrossChannelNormalizationLayer` 类
## 9.4.5 `AveragePooling2DLayer` 类
## 9.4.6 `MaxPooling2DLayer` 类
## 9.4.7 `FullyConnectedLayer` 类
## 9.4.8 `DropoutLayer` 类
## 9.4.9 `SoftmaxLayer` 类
## 9.4.10 `ClassificationOutputLayer` 类


## 10.1 概述
## 10.2 检查系统
## 10.3 下载图像数据
## 10.4 加载图像
## 10.5 下载预训练卷积神经网络 (CNN)
## 10.5.1 加载预训练的 `AlexNet` 网络
## 10.6 加载预训练的 `CNN`
## 10.7 为 `CNN` 处理图像
## 10.8 准备训练和测试图像集
## 10.9 使用 `CNN` 提取特征
## 10.10 使用特征训练多分类 SVM
## 10.11 评估分类器
## 10.12 在图像上尝试新训练的分类器
## 10.13 参考文献


## 11.1 使用卷积神经网络进行迁移学习
## 11.2 预训练卷积神经网络

# 自编码器

## 12.1 `Autoencoder` 类
## 12.2 自编码器函数
## 12.2.1 函数
## 12.2.2 `trainAutoencoder`
## 12.2.3 `decode`
## 12.2.4 `encode`
## 12.2.5 `predict`
## 12.2.6 `stack`
## 12.2.7 `generateFunction`
## 12.2.8 `generateSimulink`
## 12.2.9 `plotWeights`
## 12.2.10 `view`
## 12.3 使用自编码器构建深度网络


## 13.1 训练堆叠自编码器用于图像分类
## 13.1.1 数据集
## 13.1.2 训练第一个自编码器
## 13.1.3 可视化第一个自编码器的权重
## 13.1.4 训练第二个自编码器
## 13.1.5 训练最后的 softmax 层
## 13.1.6 构建一个堆叠神经网络
## 13.1.7 深度调深度神经网络
## 13.1.8 总结
## 13.2 使用卷积神经网络进行迁移学习





深度学习（也称为`深度结构化学习`、`分层学习`或`深度机器学习`）是[机器学习](https://en.wikipedia.org/wiki/Machine_learning "机器学习")的一个分支，基于一组[算法](https://en.wikipedia.org/wiki/Algorithm "算法"),试图对数据中的高层抽象进行建模。在简单的情况下，可能有两组神经元：接收输入信号的和发送输出信号的组。当输入层接收到输入时，它会将输入的修改版本传递给下一层。在深层网络中，输入层和输出层之间有许多层（这些层并非由神经元组成，但将其这样认为有助于理解），这使得算法可以使用由多个线性性和非线性变换组成的多个处理层。

深度学习是更广泛的基于数据表示学习的机器学习方法家族的一部分。一个观测值（例如图像）可以用多种方式表示，例如每个像素的强度值向量，或者更抽象地表示为一组边缘、特定形状的区域等。某些表示方法在简化学习任务（例如人脸识别或面部表情）方面优于其他方法。深度学习的承诺之一是用高效的算法取代手工特征，用于[无监督](https://en.wikipedia.org/wiki/Unsupervised_learning "无监督学习")或半监督特征学习。该领域的研究试图创建更好的表示，并建立模型来从大规模数据中学习这些表示。某些表示方法的灵感来自神经科学的进展，并松地基于对神经系统信息处理和通信模式的解释，例如神经编码，试图定义各种刺激与大脑中相关神经元反应之间的关系。

各种深度学习架构，如深度神经网络、卷积神经网络、深度信念网络和循环神经网络已应用于计算机视觉、自动语音识别、自然语言处理、音频识别和生物信息学等领域，它们在各种任务中已被证明能够产生最先进的成果。深度学习被描述为一个热词，或神经网络的重新品牌。深度学习被表征为一类[机器学习](https://en.wikipedia.org/wiki/Machine_learning "机器学习") [算法](https://en.wikipedia.org/wiki/Algorithm "算法")，其特点是：

* 使用许多层非线性处理单元级联进行特征提取和变换。每一层都使用前一层的输出作为输入。算法可以是监督的或无监督的，应用包括模式分析（无监督）和分类（监督）。
* 基于对数据多个层级特征或表示的（无监督）学习。高层特征从低层特征派生出来，形成分层表示。
* 是更广泛的基于数据表示学习的机器学习领域的一部分。
* 学习对应于不同抽象级别的多个级表示；这些级别形成了一个概念的层级结构。

这些定义的的共同点是具有多层非线性处理单元，以及每层对特征表示的监督或无监督学习，这些层形成了从低层特征到高层特征的层级结构。深度学习算法中使用的非线性处理单元层的组成取决于要解决的问题。深度学习中已使用的层包括人工神经网络的隐藏层和一组命题公式。它们还可能包括在深度生成模型中按层组织的潜变量，例如深度信念网络和深度玻尔兹兹曼机中的节点。

深度学习算法基于分布式表示。分布式表示背后的基本假设是，观测数据是由分层组织的因素的相互作用生成的。深度学习增加了一个假设，即这些因素层对应于抽象或组合的层级。不同数量的层数和层的大小可以提供不同程度的抽象。深度学习利用了这种分层解释因素的想法，即从低层因素学习更高级别、更抽象的概念。这些架构通常使用贪心的逐层方法构建。深度学习有助于解开这些抽象，并选出哪些特征对学习是有用的。

对于监督学习任务，深度学习方法消除了特征工程，通过将数据转换为类似于主成分的紧凑中间表示，并推导出消除冗余的层级结构。许多深度学习应用于无监督学习，因为无标记数据通常比标记数据更丰富。以无监督方式训练的深度结构示例包括神经压缩和信念网络。深度学习应用于科学的各个领域。常见应用包括：

* 自动语音识别
* 图像识别
* 自然语言处理
* 药物发现和毒理学
* 客户关系管理
* 推荐系统
* 生物信息学


MATLAB 拥有`神经网络工具`，它提供了算法、函数和应用程序来创建、训练、可视化和模拟神经网络。它可以执行分类、回归、聚类、降维、时间序列预测以及动态系统建模和控制。

该工具包含了用于分类和特征学习任务的卷积神经网络和自动编码器深度学习算法。为了加速大型数据集的训练，可以使用`并行计算工具`将计算分布在多内核处理器、GPU 和计算集群。

重要的特性包括：

* 深度学习，包括卷积神经网络和自动编码器
* 并行计算和 GPU 支持以加速训练（配合并行计算工具）
* 监督学习算法，包括多层、径基、学习向量量化(`LVQ`)、延迟、非线性自回归(`NARX`)和循环神经网络(`RNN`)
* 无监督学习算法，包括自组织映射和竞争层
* 用于数据拟合、模式识别和聚类的应用程序
* 用于预处理、后处理和网络可视化，以提高训练效率并评估网络性能

神经网络工具提供了简单的 MATLAB 命令来创建和连接深度神经网络的层。示例和预训练网络使得即使没有高级计算机视觉算法或神经网络的知识，也能轻松使用 MATLAB 进行深度学习。

| 您想做什么？ | MATLAB 工具 |
| --- | --- |
| 使用迁移学习用您的数据微调网络 | 使用迁移学习更快地开始深度学习 |
| 获取预训练网络进行探索并用于分类图像 | 预训练卷积神经网络 |





| 创建一个新的深度神经网络以执行分类或回归 | 创建用于分类的简单深度学习网络训练用于回归的卷积神经网络 |
| 使用无法放入内存的数据集训练网络 | 使用 ImageDatastore 中的数据训练卷积神经网络 |
| 训练用于目标检测的网络 | 深度学习、目标检测和识别（计算机视觉系统工具箱） |
| 根据文件夹名称自动标记您的图像数据，或使用 App 交互标记 | 使用 ImageDatastore 中的数据训练卷积神经网络为分类模型训练标记图像（计算机视觉系统工具箱） |
| 可视化网络学习到的特征 | 使用 AlexNet 创建 Deep Dream 图像视化卷积神经网络的激活值 |
| 在 CPU、GPU、多个 GPU 上训练，并在您的桌面电脑或云集群上并行运行 | 在 GPU 上和并行进行基于大数据的深度学习 |

深度学习利用神经网络直接从数据中学习有用的特征表示。神经网络结合了多个非线性处理层，使用受生物神经系统启发的、并行运行的简单元素。深度学习模型可以在目标分类中达到顶级的准确率，有时甚至超过人类水平。

你使用一组大型标记数据和包含许多层（通常包括一些卷积层）的神经网络架构来训练模型。训练这些模型是计算密集型的，你通常可以通过使用高性能 GPU 来加速训练。此图显示了卷积神经网络如何结合层从许多图像中自动学习特征以便对新图像进行分类。

![Descripción: http://es.mathworks.com/help/nnet/ug/deep\_learning\_arch\_crop.png](img/00001.jpeg)

许多深度学习应用使用图像文件，有时是数百万个图像文件。为了高效访问访问许多图像文件，MATLAB 提供了 `imageDatastore` 函数。使用此函数可以：

* 自动读取批量图像，以便在机器学习和计算机视觉应用中进行快速处理
* 从无法放入内存的图像集合导入数据
* 根据文件夹名称自动标记您的图像数据

# 1.3 深度学习与 MATLAB 代码
此示例演示了如何仅用 10 行 MATLAB 代码使用深度学习识别实时网络摄像头上的物体。尝试此示例以查看在 MATLAB 中开始深度学习有多简单。

1. 运行这些命令以根据需要获取下载内容，连接到摄像头并获取预训练的神经网络。
2.
```matlab
camera = webcam; % 连接到摄像头
net = alexnet; % 加载神经网络
```
如果你需要安装 `webcam` 和 `alexnet` 附加组件，每个函数都会出现带有链接的消息，帮助你使用 Add-On Explorer 下载免费附加组件。或者，参见用于 *AlexNet Network* 的 `Neural Network Toolbox Model` 和 `MATLAB Support Package for USB Webcams`。

安装用于 *AlexNet Network* 的 Neural Network Toolbox Model 后，可以使用它可以分类图像。AlexNet 是一个预训练的卷积神经网络 (CNN)，在百万图像上训练过，可以将图像分类为 1000 个物体类别（例如：键盘、鼠标、咖啡杯、铅笔和许多动物）。

3. 运行以下代码显示结果：
```matlab
while true
    img = snapshot(camera);
    label = classify(net, img);
    imshow(img);
    title(string(label));
end
```

![Descripción: http://es.mathworks.com/help/nnet/ug/webcam_coffee.png](img/00002.jpeg)

对于后续步骤，使用 [`imageresize`](https://www.mathworks.com/help/images/imageresize.html) 调整图像大小。


## 2.1 迁移学习

迁移学习在深度学习中常用。你获取一个预训练网络并将其用于其他任务。使用迁移学习微调网络比从头开始训练快得多也更容易。你可以将其用于较小的数据。

例如，如果你使用一个在数千或数百万图像上训练过的网络，你只需要几百张图像。如果你有一个非常大的数据集，迁移学习可能并不训练新网络更快。

迁移学习允许你：
* 将预训练网络学习到的特征迁移到新问题
* 迁移学习比训练新网络更快
* 缩短训练时间并缩小数据集
* 在不需要学习如何创建整个网络的情况下进行深度学习

## 2.2 使用 ALEXNET 进行迁移学习

### 2.2.1 预训练卷积神经网络

使用迁移学习微调预训练网络通常比从头开始训练快得多也更容易。你可以将以前训练的网络用于以下目的：

| **目的** | **描述** |
| --- | --- |
| 分类 | 直接将预训练网络应用于分类问题。 |
| 迁移学习 | 获取在大型数据集上训练的网络的层并在新数据集上进行微调 |
| 特征提取 | 使用层激活作为特征，将预训练网络作为特征提取器。你可以使用这些激活作为特征来训练另一个分类器，例如支持向量机 (SVM)。 |

你可以下载并安装预训练网络来解决你的问题。使用 `alexnet` 等函数可以从 Add-On Explorer 获取下载预训练网络的链接。





`Transfer learning`（迁移学习）常用于深度学习应用。你可以取一个预训练网络并将其作为起点来学习新任务。与构建和训练新网络相比，使用迁移学习对网络进行微调（Fine-tuning）更快且更容易。你可以使用少量训练图像快速将迁移学习应用到新任务。迁移学习的优势在于预训练网络已经学习了丰富的特征集。这些特征可以应用于广泛的其他相似任务。例如，你可以取一个在数百万图像上训练的网络，并仅使用几百张图像对其进行新的物体分类进行重新训练。如果你有一个非常大的数据集，那么迁移学习可能不会更快。

`Feature extraction`（特征提取）是一种利用预训练网络能力的简单方法，无需投入时间和精力进行训练。特征提取可以使用深度学习最快的方法。你从预训练的网络中提取学习到的特征，并使用这些特征来训练分类器，例如使用 `fitcsvm`（统计与机器学习工具箱™）训练支持向量机。例如，如果 SVM 在你的训练集和验证集上的准确率达到 >90%，那么微调可能就不值得为了提高准确率而费力了。如果你在小数据集上进行微调，还会面临对训练数据过拟的风险。如果 SVM 无法为你的应用达到足够的准确率，那么微调就值得为了追求更高的准确率。

## 2.2.2 Function alexnet

### Syntax
```matlab
net = alexnet
```

### Description
`net = alexnet` 返回预训练的 AlexNet 模型。该模型在 ImageNet 数据库的子集上训练，该数据库用于 ImageNet 大规模视觉识别挑战 (ILSVRC)。该模型在超过百万张图像上进行了训练，可以将图像分类为 1000 类物体类别。例如：键盘、鼠标、铅笔和许多动物。结果，该模型已经为各种图像学习了丰富的特征表示。

此函数需要 `Neural Network Toolbox Model for AlexNet Network` 支持包。如果未安装此支持包，该函数将提供一个下载链接。

### Examples

#### 下载 AlexNet 支持包
下载并安装 `Neural Network Toolbox Model for AlexNet Network` 支持包。

在命令行中输入 `alexnet`。

```matlab
alexnet
```

如果未安装 `Neural Network Toolbox Model for AlexNet Network` 支持包，该函数将提供一个指向“附加功能资源管理器”中所需支持包的链接。要安装该支持包，点击链接，然后点击 **Install**（安装）。在命令行中输入 `alexnet` 检查安装是否成功。

```matlab
alexnet

ans =

  SeriesNetwork with properties:

    Layers: [25×1 nnet.cnn.layer.Layer]
```

如果已安装了所需的支持包，该函数将返回一个 `SeriesNetwork` 对象。

#### 加载预训练的 AlexNet 卷积神经网络
加载预训练的 AlexNet 卷积神经网络并检查层和类别。

使用 `alexnet` 加载预训练的 AlexNet 网络。输出 `net` 是一个 `SeriesNetwork` 对象。

```matlab
net = alexnet
net = SeriesNetwork with properties:
   Layers: [25×1 nnet.cnn.layer.Layer]
```

使用 `Layers` 属性查看网络架构。该网络由 25 层组成。有 8 层具有可学习权重：5 层卷积层和 3 层全连接层。

```matlab
net.Layers
ans =
  5x1 array with layers:
  1  'data'      Input      27x27x3 images with 'center' normalization
  2  'conv1'     Convolution      96 1x1x3 convolutions with stride [4] and padding [0]
  3  'relu1'     ReLU
  4  'norm1'     Channel Normalization  channel normalization with 5 channels
  5  'pool1'     Max Pooling      3x3 max pooling with stride [2] and padding [0]
  6  'conv2'     Convolution      256 5x5x48 convolutions with stride [1] and padding [2]
  7  'relu2'     ReLU
  8  'norm2'     Channel Normalization  channel normalization with 5 channels
  9  'pool2'     Max Pooling      3x3 max pooling with stride [2] and padding [0]
  10  'conv3'     Convolution      384 3x3x256 convolutions with stride [1] and padding [1]
  11  'relu3'     ReLU
  12  'conv4'     Convolution      384 3x3x192 convolutions with stride [1] and padding [1]
  13  'relu4'     ReLU
  14  'conv5'     Convolution      256 3x3x192 convolutions with stride [1] and padding [1]
  15  'relu5'     ReLU
  16  'pool5'     Max Pooling      3x3 max pooling with stride [2] and padding [0]
  17  'fc6'      Fully Connected      4096 connected layer
  18  'relu6'     ReLU
  19  'drop6'     Dropout      50% dropout
  20  'fc7'      Fully Connected      4096 connected layer
  21  'relu7'     ReLU
  22  'drop7'     Dropout      50% dropout
  23  'fc8'      Fully Connected      1000 connected layer
  24  'prob'      Softmax
```
（注：此处代码块内容为函数输出，展示了 AlexNet 的结构）

## 2.2.3 Classify an Image Using AlexNet
使用 AlexNet 读取、调整大小并分类图像。首先加载预训练的 AlexNet 模型。

```matlab
net = alexnet
I = imread('peppers.png');
figure
imshow(I)
```

预训练模型要求图像大小与网络输入大小相同。使用第一层的 `InputSize` 属性确定网络输入大小。

```matlab
sz = net.Layers(1).InputSize
sz =
  227 227 3
```

将图像裁剪为网络输入大小。或者可以使用 `imresize`（图像处理工具箱™）调整图像。

```matlab
I = I(1:sz(1),1:sz(2),1:sz(3));
figure
imshow(I)
```

使用 `classify` 分类图像。

```matlab
label = classify(net,I)
label =
  categorical
    bell pepper
```

同时显示图像和分类结果。

```matlab
figure
imshow(I)
title(char(label))
```
## 2.2.4 Feature Extraction Using AlexNet
从预训练的网络中提取学习到的特征，并使用这些特征来训练分类器。特征提取是利用预训练深度网络能力最简单、快速的方法。例如，你可以使用 `fitcecoc`（统计与机器学习工具箱™）在提取的特征上训练支持向量机（SVM）。

加载预训练的 AlexNet 网络。

```matlab
net = alexnet
```

加载示例图像。`merchImagesTrain` 和 `merchImagesTest` 是 `ImageDatastore` 对象。

```matlab
[merchImagesTrain,merchImagesTest] = merchData;
```

样本数据中有 60 张训练图像和 15 张测试图像。显示 20 张示例图像。

```matlab
figure
for i = 1:20
    subplot(4,5,i)
    I = readimage(merchImagesTrain,i);
    imshow(I)
    drawnow
end
```





![Descripción: http://es.mathworks.com/help/examples/nnet/win64/FeatureExtractionUsingAlexNetExample\_01.png](img/00006.jpeg)

如果训练图像的大小与图像输入层的大小不同，则你必须对图像数据进行缩放或裁剪。`merchImages` 中的图像与 AlexNet 的输入大小相同，因此你不需要对新的图像数据进行缩放或裁剪。

获取训练和测试图像的特征表示。

对图像数据对最后一个全连接层（`'fc7'`）使用 `activations`。

```matlab
layer = 'fc7';
trainingFeatures = activations(net,merchImagesTrain,layer);
testFeatures = activations(net,merchImagesTest,layer);
```

从训练数据和测试数据中提取类别标签。

```matlab
trainingLabels = merchImagesTrain.Labels;
testLabels = merchImagesTest.Labels;
```

使用 `fitcecoc`（Statistics and Machine Learning Toolbox）拟合多分类支持向量机（SVM）。

```matlab
classifier = fitcecoc(trainingFeatures,trainingLabels);
```

使用 `predict` 对测试图像进行分类。

```matlab
predictedLabels = predict(classifier,testFeatures);
```

显示四个带有预测标签的测试测试图像。

```matlab
idx = [1 4 7 10];
figure
for i = 1:numel(idx)
    subplot(2,2,i)
    I = readimage(merchImagesTest,idx(i));
    label = predictedLabels(idx(i));
    imshow(I)
    title(char(label))
    drawnow
end
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/FeatureExtractionUsingAlexNetExample\_02.png](img/00007.jpeg)

计算分类准确率。

```matlab
accuracy = sum(predictedLabels==testLabels)/numel(predictedLabels)
accuracy =
    0.9333
```

此示例 SVM 具有较高的准确率。如果使用特征提取的准确率不够，请尝试迁移学习。

## 2.2.5 使用 AlexNet 进行迁移学习

微调预训练的卷积神经网络，以学习新图像集合的特征。

迁移学习常用于深度学习应用。你可以选取一个预训练的网络，并将其作为起点来学习新任务。与从头训练相比，使用迁移学习微调网络要快得多也简单得多。你可以使用较少的训练图像快速地将学习迁移到新任务中。

将示例图像加载为 `ImageDatastore` 对象。

```matlab
[merchImagesTrain,merchImagesTest] = merchData;
```

在示例数据中，有 60 张训练图像和 15 张测试图像。显示 20 张示例图像。

```matlab
figure
for i = 1:20
    subplot(4,5,i)
    I = readimage(merchImagesTrain,i);
    imshow(I)
    drawnow
end
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/TransferLearningUsingAlexNetExample\_01.png](img/00008.jpeg)

加载一个预训练的 AlexNet 网络。

```matlab
net = alexnet;
```

预训练网络 `net` 的最后三层配置为 1000 个类别。这三层必须针对新的分类问题进行微调。从预训练网络 `net` 中提取除最后三层以外的所有层。

```matlab
layersTransfer = net.Layers(1:end-3);
```

通过将最后三层替换为全连接层、softmax 层和分类输出层，将层迁移到新任务中。根据新数据指定新全连接层的选项。将全连接层的大小设置为与新数据中的类别数相同。为了加快训练，还要增加全连接层中的 `'WeightLearnRateFactor'` 和 `'BiasLearnRateFactor'` 的值。

从训练数据中确定类别数量。

```matlab
numClasses = numel(categories(merchImagesTrain.Labels))
numClasses =
    5
```

通过将迁移的层与新层结合创建层数组。

```matlab
layers = [...
    layersTransfer
    fullyConnectedLayer(numClasses,'WeightLearnRateFactor',20,'BiasLearnRateFactor',20)
    softmaxLayer
    classificationLayer];
```

如果训练图像的大小与图像输入层的大小不同，则你必须对图像数据进行缩放或裁剪。`merchImages` 中的图像与 AlexNet 的输入大小相同，因此你不需要对新的图像数据进行缩放或裁剪。

创建训练选项。对于迁移学习，你希望保留预训练网络早期层的特征（迁移的层权重）。将 `'InitialLearnRate'` 设置为低值。这个较低的初始学习率会减慢迁移层的学习速度。在上一步中，你将全连接层的学习率因子设置得更高，以加快新最终层的学习速度。这种组合使得仅在新层上进行快速学习，同时保持其他层固定。在执行迁移学习时，不需要训练许多轮（epochs）。为了加快训练，你可以减小 `trainingOptions` 调用中 `'MaxEpochs'` 名称值对的值。为了减少内存占用，减小 `'MiniBatchSize'`。

```matlab
options = trainingOptions('sgdm',
    'MiniBatchSize',5,...
    'MaxEpochs',10,...
    'InitialLearnRate',0.0001);
```

使用 `trainNetwork` 对新层微调网络。

```matlab
netTransfer = trainNetwork(merchImagesTrain,layers,options);
```

在 GPU 上训练。
初始化图像归一化。
=========================================
|     Epoch | Iteration | Time Elapsed | Mini-batch | Mini-batch | Base Learning|
|         |           |             |            |            |             
|         |           | (seconds)   | Loss | Accuracy | Rate         |
=========================================
|      1 | 1 | 0.55 | 2.4120 | 20.00% | 0.0001 |
|      5 | 50 | 18.28 | 0.0002 | 100.00% | 0.0001 |
|      9 | 100 | 34.82 |00.0000 | 000.00% | 0.001 |
||100 1200 41.33 | 0.0001 |  10.000% | 0.001 |
=========================================

使用 `classify` 对测试图像进行分类。

```matlab
predictedLabels = classify(netTransfer,merchImagesTest);
```

显示四个带有预测标签的测试测试图像。

```matlab
idx = [1 4 7 10];
figure
for i = 1:numel(idx)
    subplot(2,2,i)
    I = readimage(merchImagesTest,idx(i));
    label = predictedLabels(idx(i));
    imshow(I)
    title(char(label))
    drawnow
end
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/TransferLearningUsingAlexNetExample\_02.png](img/00009.jpeg)

计算分类准确率。

```matlab
testLabels = merchImagesTest.Labels;
accuracy = sum(predictedLabels==testLabels)/numel(predictedLabels)
accuracy =
    0.8667
```

此示例具有较高的准确率。如果使用迁移学习的准确率不够，请尝试特征提取。

# 2.3 卷积神经网络的迁移学习与微调

本示例演示了如何通过微调现有的预训练卷积神经网络对新的图像数据进行分类。

如果训练数据很少，构建和训练新网络既耗时又无效。相反，你可以微调现有的预训练网络来解决新问题。这种技术被称为迁移学习，通常会产生快速训练。通过提取预训练网络的层并重新训练末尾的层，你可以更快地完成训练。

神经网络工具箱提供了多个预训练网络，包括流行的 AlexNet。本示例使用简单的预训练网络向您介绍迁移学习。它取在字母图像上训练的卷积神经网络，并对其进行微调以分类数字。

## 2.3.1 加载预训练网络

加载预训练网络。`LettersClassificationNet.mat` 包含预训练的网络 `net`，它是在大量 28x28 灰度字母图像上训练的。该网络将图像分为三个字母类别：'A'`、`'B'` 和 `'C'`。





```matlab
load(fullfile(matlabroot,'examples','nnet','LettersClassificationNet.mat'))
```

查看 `net` 的 `Layers` 属性中包含的网络架构详情。

```matlab
net.Layers
```

ans = 

  7x1 Layer array with layers:

    1  'imageinput' Image Input 28x28x1 images with 'zerocenter' normalization
    2  'conv' Convolution 20 5x5x1 convolutions with stride [1 1] and padding [0 0]

    3  'relu' ReLU

    4  'maxpool' Max Pooling 2x2 max pooling with stride [2 2] and padding [0 0]

    5  'fc' Fully Connected 3 fully connected layer

    6  'softmax' Softmax softmax

    7  'classoutput' Classification Output crossentropyex with 'A', 'B', and 1 other classes

该网络有七层。第 2–4 层检测特征。第 5–7 层将特征分类为字母类别。卷积层的 20 个输出（通道）对应于学习到的特征。你可以使用这些特征通过迁移学习预测数字数据的类别。

预训练网络 `net` 的最后三层是针对字母数据调整过的。通过替换预训练网络的最后三层，你可以微调网络以改为分类数字。

## 2.3.2 加载训练数据

将数字样本数据加载为 `ImageDatastore` 对象。`imageDatastore` 函数根据文件夹名称自动对图像进行标记，并将数据存储为 `ImageDatastore` 对象。`ImageDatastore` 对象允许你存储大型图像数据，包括无法放入内存的数据。该对象还允许你在训练期间高效地读取分批图像。

```matlab
digitDatasetPath = fullfile(matlabroot,'toolbox','nnet','nndemos', ...
    'nndatasets','DigitDataset');

digitData = imageDatastore(digitDatasetPath, ...
    'IncludeSubfolders',true,'LabelSource','foldernames');
```

该数据存储包含 10000 张 0–9 的数字合成图像。这些图像是通过对使用不同字体创建的数字图像应用随机变换生成的每个数字图像均为 28x28 像素。

将数据集分为训练集和测试集。划分数据，使得每个数据存储器都包含每个类别 50% 的图像。`splitEachLabel` 将 `digitData` 中的图像文件分为两个新的数据存储器：`trainDigitData` 和 `testDigitData`。

```matlab
[trainDigitData,testDigitData] = splitEachLabel(digitData,0.5,'randomize');
```

使用 `imshow` 显示 20 个样本训练数字。

```matlab
numImages = numel(trainDigitData.Files);
idx = randperm(numImages,20);
for i = 1:20
    subplot(4,5,i)
    I = readimage(trainDigitData, idx(i));
    imshow(I)
end
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/TransferLearningAndTuningOfNetworks_01.png](img/0010.jpeg)

## 2.3.3 目标网络层

通过替换并微调这些层到数字数据，迁移学习到新任务。由于数字数据在内容上与字母数据相似，你可以使用迁移学习。预训练网络 `net` 的最后三层是针对字母数据调整过的。从预训练网络中提取除最后三层的所有层。

```matlab
layersTransfer = net.Layers(1:end-3);
```

数字数据集有 10 个类。为 10 个类添加一个新的全连接层、一个 softmax 层和一个分类输出层。为了加快新层上的学习速度，可以增加全连接层的权重学习和偏置学习率因子。如果你想保留预训练网络早期的特征（迁移的权重），并且训练图像的尺寸与输入层不同，则必须对图像数据进行尺寸调整或裁剪。在本示例中，训练图像与预训练网络的输入大小相同（28x28）。你不需要对图像数据进行尺寸调整或裁剪。对于迁移学习，将 `InitialLearnRate` 设置为低值。这个低学习率会减慢迁移层的学习速度。在上一步中，你将全连接层的学习因子设置得更高，以加快最后层的学习。这导致仅在新层上进行快速学习，同时保持其他层固定。在进行学习时，不需要训练许多轮次（epochs）。为了加速训练，减少调用 `trainingOptions` 时 `MaxEpochs` 参数的值。

```matlab
numClasses = numel(categories(digitData.Labels))
layers = [layersTransfer; fullyConnectedLayer(numClasses,'WeightLearnFactor',20,'BiasLearnFactor',20; softmaxLayer; classificationLayer];
optionsTransfer = trainingOptions('sg','MaxEpochs',5,'InitialLearnRate',0.0001);
netTransfer = trainNetwork(digitData,layers,optionsTransfer);
```

在单 CPU 上训练。正在初始化图像归一化。

|=========================================================|
| Epoch | Iteration | Time Elapsed (seconds) | Mini-batch Loss | Mini-batch Accuracy | Base Rate |
|=========================================================|
| 1 | 1 | 0.75 | 10.459 | 6.25% | 1.00e-04 |
| 2 | 50 | 19.63 | 3.1897 | 70.31% | 1.00e-04 |
| 3 | 100 | 38.44 | 1.1082 | 80.47% | 1.00e-04 |
| 4 | 150 | 58.13 | 0.1465 | 95.31% | 1.00e-04 |
| 5 | 195 | 75.28 | 0.1504 | 96.88% | 1.00e-04 |
|=========================================================|

计算分类准确率：测试数据中正确分类的实例比例。

```matlab
YPred = classify(netTransfer,testData);
YTest = testData.Labels;
accuracy = sum(YPred==YTest)/numel(YTest)
```

accuracy = 0.9288

带有预测标签的样本测试图像。

```matlab
idx = 501:500:5000;
figure
for i = 1:numel(idx)
    subplot(3,3,i)
    I = readimage(testData, idx(i));
    label = char(YTest(idx(i)));
    imshow(I)
    title(label)
end
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/TransferLearningAndTuningOfNetworks_02.png](img/0011.jpeg)





1. `data` | 输入 | 带有 'zerocenter' 归一化的 227x227x3 图像
2. `conv1` | 卷积 | 96 个 11x11x3 卷积，步长为 `[4 4]`，填充为 `[0 0]`
3. `relu1` | ReLU | ReLU
4. `norm1` | 跨通道归一化 | 每个元素 5 通道的跨通道归一化
5. `pool1` | 最大池化 | 3x3 最大池化，步长为 `[2 2]`，填充为 `[0 0]`
6. `conv2` | 卷积 | 256 个 5x5x48 卷积，步长为 `[1 1]`，填充为 `[2 2]`
7. `relu2` | ReLU | ReLU
8. `norm2` | 跨通道归一化 | 每个元素 5 个通道的跨通道归一化
9. `pool2` | 最大池化 | 3x3 最大池化，步长为 `[2 2]`，填充为 `[0 0]`
10. `conv3` | 卷积 | 384 个 3x3x256 卷积，步长为 `[1 1]`，填充为 `[1 1]`
11. `relu3` | ReLU | ReLU
12. `conv4` | 卷积 | 384 个 3x3x192 卷积，步长为 `[1 1]`，填充为 `[1 1]`
13. `relu4` | ReLU | ReLU
14. `conv5` | 卷积 | 256 个 3x3x192 卷积，步长为 `[1 1]`，填充为 `[1 1]`
15. `relu5` | ReLU | ReLU
16. `pool5` | 最大池化 | 3x3 最大池化，步长为 `[2 2]`，填充为 `[0 0]`
17. `fc6` | 全连接 | 4096 全连接层
18. `relu6` | ReLU | ReLU
19. `drop6` | Dropout | 50% 丢弃
20. `fc7` | 全连接 | 4096 全连接层
21. `relu7` | ReLU | ReLU
22. `drop7` | Dropout | 50% 丢弃
23. `fc8` | 全连接 | 100 全连接层
24. `prob` | Softmax | softmax
25. `output` | 分类 |  'tench'、'goldfish' 和其他 98 个类别的交叉熵

然后，选择最后的全连接层。最后的全连接层是 23。`layer = 23;` 你可以通过选择多个类来一次性生成多张图像。通过设置 `channels` 为这些类名称的索引来选择想要可视化的类。`channels = [18 23 63 85 97];` 类名存储在输出层（最后一层）的 `ClassNames` 属性中。你可以通过选择 `net.Layers(end).ClassNames` 数组中的项来查看所选类的名称。第 1 到 4 列 'hen'、'Yorkshire terrier'、'Shetland sheep'、'fountain' 第 5 到 6 列 'curtain'、'geyser' 使用 `deepImage` 生成图像。该命令在可用时使用兼容的 GPU。否则它将使用 CPU。在 GPU 上训练需要计算能力为 3.0 或更高的支持 CUDA 的 NVIDIA GPU。`I = deepImage(net,channels);`

| 金字塔层级 | 迭代 | 激活强度 |
|---|---|---|
| 1 | 1 | 1.45 |
| 1 | 2 | 3.36 |
| 1 | 3 | 7.13 |
| 1 | 4 | 13.12 |
| 1 | 5 | 18.62 |
| 1 | 6 | 26.64 |
| 1 | 7 | 32.08 |
| 1 | 8 | 38.13 |
| 1 | 9 | 46.56 |
| 1 | 10 | 53.34 |
| 2 | 1 | 0.3 |
| 2 | 2 | 1.9 |
| 2 | 3 | 7.18 |
| 2 | 4 | 18.23 |
| 2 | 5 | 27.7 |
| 2 | 6 | 23.0 |
| 2 | 7 | 28.15 |
| 2 | 8 | 26.5 |
| 2 | 9 | 34.43 |
| 2 | 10 | 35.15 |
| 3 | 1 | 36.07 |
| 3 | 2 | 49.56 |
| 3 | 3 | 52.69 |
| 3 | 4 | 65.31 |
| 3 | 5 | 61.22 |
| 3 | 6 | 68.71 |
| 3 | 7 | 74.45 |
| 3 | 8 | 75.56 |
| 3 | 9 | 82.75 |
| 3 | 10 | 78.51 |

如果你安装了 Image Processing Toolbox，可以使用 `montage` 显示所有图像。否则，可以使用 `imshow` 逐个显示图像。

```matlab
figure
montage(I)
```
![Descripción: http://es.mathworks.com/help/examples/nnet/win64/DeepDreamExample_](img/0012.jpeg)

## 2.4.3 生成更多图像

为了产生更大更详细的输出，你可以同时增加金字塔层级和每个金字塔层级的迭代次数。使用 `NumIterations` 选项增加迭代次数。将迭代次数设置为 100。`iterations = 100;` 生成一张强力激活 'pot' 类（通道 739）的详细图像。`channels = 739;` `I = deepImage(net,layer,channels);`![Descripción: http://es.mathworks.com/help/examples/nnet/win64/DeepDreamExample_](img/0013.jpeg)

第 3 章 分类与回归深度学习网络

# 3.1 创建简单的深度学习网络

此示例展示了如何创建一个用于深度学习分类的简单网络。卷积神经网络是深度学习的重要工具，特别适用于图像识别。学习如何设置网络、图像数据和训练选项、训练网络并测试分类精度。

## 3.1.1 加载并探索图像数据

将数字样本数据作为 `ImageDatastore` 对象加载。

```matlab
digitDatasetPath = fullfile(matlabroot,'toolbox','nnet','nndemos','nndatasets','DigitDataset');
digitData = imageDatastore(digitDatasetPath,'IncludeSubfolders',true,'LabelSource','foldernames');
```

`imageDatastore` 函数根据文件夹名称自动标记图像并存储 `ImageDatastore` 对象。`ImageDatastore` 对象允许你存储大型图像数据（包括无法放入内存的数据），并在卷积神经网络训练期间高效地读取图像批。

显示数据存储中的某些图像。

```matlab
figure;
perm = randperm(10000,20);
for i = 1:20
    subplot(4,5,i);
    imshow(digitData.Files{perm(i)});
end
```
![Descripción: http://es.mathworks.com/help/examples/nnet/win64/TrainABasicConvolutionalNeuralNetworkForClassificationExample_](img/0015.jpeg)

检查每个类别中的图像数量。

```matlab
CountLabel = digitData.countEachLabel;
```





`CountLabel` 是一个包含每个标签及其对应图像数量的表格。它显示数据存储器中数字 0-9 的每个数字都包含 1000 张图像，总计 10000 张。因此，共有 10 个类别。你可以通过 `OutputSize` 参数指定网络中最后一个全连接层的类别数量。这些图像是通过对使用不同字体创建的数字图像应用随机变换生成的。

你必须在网络的输入层中指定图像的大小。检查 `digitData` 中第一张图像的尺寸。

```matlab
img = readimage(digitData,1);
size(img)
ans =
    28    28
```

每个数字图像均为 28x28x1 像素。

## 3.1.2 指定训练集和测试集

将数据划分为训练集和测试集，使得训练集中的每个类别包含 750 张图像，测试集包含每个标签剩余的图像。

```matlab
trainingNumFiles = 750;
rng(1) % 用于可复现性
[trainDigitData,testDigitData] = splitEachLabel(digitData, ...
                                    trainingNumFiles,'randomize');
```

`splitEachLabel` 将 `digitData` 中的图像文件划分为两个新的数据存储器：`trainDigitData` 和 `testDigitData`。

## 3.1.3 定义网络层

定义卷积神经网络架构。

```matlab
layers = [imageInputLayer([28 28 1])
          convolution2dLayer(5,20)
          reluLayer
          maxPooling2dLayer(2,'Stride',2)
          fullyConnectedLayer(10)
          softmaxLayer
          classificationLayer()];
```

### 图像输入层
[imageInputLayer](http://es.mathworks.com/help/nnet/ref/imageinputlayer.html) 是指定图像尺寸的地方，在本例中尺寸为 28x28x1。这些数字对应高度、宽度和通道大小。数字数据由灰度图像组成，因此通道大小（颜色通道）为 1。对于彩色图像，通道大小将为 3，对应 RGB 值。你也可以在此层中指定任何数据变换，例如数据归一化或数据增强（随机翻转或裁剪数据）。这些通常用于避免过拟合。你不需要打乱数据，因为 `trainNetwork` 会在训练开始时自动完成。

### 卷积层
在卷积层中，第一个参数是 `filterSize`，它是训练函数在扫描图像时使用的过滤器的高度和宽度。在本例中，数字 5 表示过滤器尺寸为 `[5,5]`。你也可以为高度和宽度指定不同的尺寸。第二个参数是滤波器的数量，它决定了特征图的数量。

### ReLU 层
卷积层之后是非线性激活函数。MATLAB 使用整流线性单元 [reluLayer](http://es.mathworks.com/help/nnet/ref/relayer.html)。

### 最大池化层
卷积层之后通常跟跟池化操作，以减少参数数量并避免过拟合。[maxPooling2dLayer](http://es.mathworks.com/help/nnet/ref/maxpoolingdlayer.html) 返回区域内的最大值。`poolSize` 参数指定池化区域的大小，在本例中为 `[2,2]`。`Stride` 参数决定了池化的步长。

### 全连接层
全连接层（或多个全连接层）将特征连接到输出。`OutputSize` 参数决定了输出的类别数量，在本例中该数量为 10。

### Softmax 层
全连接层通常使用 softmax 激活函数 [softmax](http://es.mathworks.com/help/nnet/ref/softmaxlayer.html)。

### 分类层
最后层是分类层 [classificationLayer](http://es.mathworks.com/help/nnet/ref/classificationlayer.html)，它返回分类的概率。

## 3.1.4 指定训练选项
设置训练选项。使用默认的随机梯度下降设置，并设置初始学习率为 0.001。

```matlab
options = trainingOptions('MaxEpochs',15,'InitialRate',0.001);
```

## 3.1.5 使用训练数据训练网络
使用 `trainData` 训练训练网络。

```matlab
net = trainNetwork(trainData,layers,options);
```

在 GPU 上。初始化归一化。
=========================================
| Epoch | Iteration | Time (seconds) | Mini-batch Loss | Accuracy |
=========================================
| 1 | 1 | 4.38 | 3.084 | 13.2% |
| 1 | 50 | 5.4 | 1.094 | 65.3% |
| 1 | 100 | 6.17 | 0.726 | 74.2% |
| 1 | 150 | 6.92 | 0.474 | 83.59% |
| 1 | 200 | 7.66 | 0.3085 | 92.19% |
| 1 | 250 | 8.41 | 0.2323 | 92.97% |
| 1 | 300 | 9.16 | 0.1542 | 97.66% |
| 1 | 350 | 9.90 | 0.1313 | 97.66% |
| 1 | 400 | 10.64 | 0.0944 | 96.09% |
| 1 | 450 | 11.40 | 0.0667 | 99.2% |
| 1 | 500 | 12.16 | 0.045 | 99.2% |
| 1 | 550 | 12.93 | 0.044 | 99.2% |
| 1 | 600 | 13.68 | 0.04 | 99.2% |
| 1 | 650 | 14.43 | 0.0339 | 100% |
| 1 | 700 | 15.17 | 0.0341 | 100% |
| 1 | 750 | 15.89 | 0.0369 | 100% |
| 1 | 800 | 16.62 | 0.0263 | 100% |
| 1 | 850 | 17.37 | 0.0181 | 100% |
| 1 | 870 | 17.66 | 0.0234 | 100% |




`trainNetwork` 在显示窗口中显示其训练时使用的硬件。如果可用 `GPU`，它默认会使用 `GPU`（需要 `Parallel Computing Toolbox (TM)` 和计算能力为 3.0 及更新的 `CUDA-enabled GPU`）。如果没有可用的 `GPU`，它将使用 `CPU`。你也可以在调用 `trainingOptions` 时使用 `'ExecutionEnvironment'` 名称值对参数来指定执行环境。

进度窗口显示第一次迭代、最后一次迭代以及中间每 50 次迭代的小批次损失（mini-batch loss）和小批次准确率（mini-batch accuracy）。小批次损失是 `k 个互斥类的交叉熵函数`，小批量准确率是当前小批次中被训练网络正确分类的图像百分比。

它还会显示训练所需的累积时间以及该迭代的学习率。在本示例中，基础学习率在整个训练过程中固定为 0.0001。你也可以调整此值，并在特定的轮数（epochs）减少学习率。更多详细信息，请参见 `trainingOptions` 函数参考页。

## 3.1.6 分类测试数据中的图像并计算准确率

在未用于训练网络的测试集上运行训练好的网络，并预测图像标签（数字）。

```matlab
YTest = classify(convnet,testDigitData);

TTest = testDigitData.Labels;

% 计算准确率。

accuracy = sum(YTest == TTest)/numel(TTest)

accuracy =
    0.9812
```

准确率是测试数据中与 `classify` 分类结果匹配的真实标签数量与测试数据图像总数的比例。在这种情况下，约 98% 的数字估计与测试集中的真实数字值匹配。

# 3.2 训练用于回归的卷积神经网络

本示例展示了如何使用卷积神经网络拟合回归模型以预测手写数字的旋转角度。

卷积神经网络 (`CNNs` 或 `ConvNets`）是深度学习的重要工具，特别适用于分析图像数据。例如，你可以使用 `CNNs` 对图像进行分类。为了预测角度和距离等连续数据，你可以在网络末尾添加一个回归层。

示例构建了一个卷积神经网络架构，训练了一个网络，并使用训练好的网络预测旋转的手写数字的角度。这些预测对于光学字符识别非常有用。

可选地，你可以使用 `imrotate`（Image Processing Toolbox™）旋转图像，并使用 `boxplot`（Statistics and Machine Learning Toolbox™）创建残差箱线图。

## 3.2.1 加载训练数据

网络在包含 5000 张带有相应旋转角度的合成手写数字集合上进行训练。

使用 `digitTrain4DArrayData` 将数字训练集作为 4-D 数据加载。

```matlab
[trainImages,~,trainAngles] = digitTrain4DArrayData;
```

使用 `imshow` 显示 20 个随机采样的训练数字。

```matlab
numTrainImages = size(trainImages,4);

figure

idx = randperm(numTrainImages,20);

for i = 1:numel(idx)
    subplot(4,5,i)
    imshow(trainImages(:,:,:,idx(i)))
    drawnow
end
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/TrainAConvolutionalNeuralNetworkForRegressionExample_01.png](img/00016.jpeg)

## 3.2.2 创建网络层

为了解决回归问题，创建网络层并在网络末尾包含一个回归层。

第一层定义了输入数据的大小和类型。输入图像为 28x28x1。创建一个与训练图像相同大小的图像输入层。

网络的中间层定义了网络的核心架构。创建一个具有 25 个大小为 12 的滤波器的 2D 卷积层，随后跟一个 `ReLU` 层。

最后几层定义了输出数据的大小和类型。对于回归问题，全连接层必须位于网络末尾的回归层之前。创建一个大小为 1 的全连接输出层和一个回归层。

将所有层组合在一个 `Layer` 数组中。

```matlab
layers = [ ...
    imageLayer([28 28 1])
    convolution2d(1,25)
    reluLayer
    fullyConnectedLayer(1)
    regressionLayer];
```

## 3.2.3 训练网络

创建网络训练选项。将初始学习率设置为 0.01。为了缩短训练时间，降低 `'MaxEpochs'` 的值。

```matlab
options = trainingOptions('sg','InitialLearnRate',0.01, 'MaxEpochs',15);
```

使用 `trainNetwork` 创建网络。该命令在可用时使用 `GPU`。否则，`trainNetwork` 使用 `CPU`。在 `GPU` 上训练需要计算能力为 3.0 或更高的 `CUDA-enabled GPU`。训练可能需要几分钟，特别是在 `CPU` 上训练时。

```matlab
net = trainNetwork(trainImages,Angles,layers,options)
```

| Epoch | 迭代 | 耗用时间 (秒) | 小批次损失 | RMSE | 基础率 |
|---|---|---|---|---|---|
| 1 | 1 | 1.4 | 392.580 | 28.2 | |
| 1 | 50 | 1.4 | 40.97 | 96.2 | |
| 2 | 100 | 80 | 55.51 | 10.4 | |
| 3 | 150 | 120.1 | 64.4 | 11.35 | |
| 4 | 200 | 158.6 | 36.27 | 8.52 | |
| 6 | 250 | 196.0 | 53.01 | 10.3 | |
| 7 | 300 | 238.67 | 35.77 | 8.46 | |
| 8 | 350 | 281.16 | 35.03 | 8.37 | |
| 9 | 400 | 324.23 | 24.99 | 7.06 | |
| 11 | 450 | 366.4 | 33.28 | 8.12 | |
| 12 | 500 | 409.1 | 27.06 | 7.3 | |
| 13 | 550 | 446.05 | 18.19 | 6.03 | |
| 14 | 585 | 471.13 | 18.96 | 6.16 | |

*(注：原文表格中部分行号与数据对应错乱，此处已按原文逻辑保留)*

初始化图像归一化。

`net` =

具有以下属性的 SeriesNetwork
  Layers: 5×1

查看 `net` 的 `Layers` 属性中的网络架构细节。

```matlab
net.Layers

ans = 5x1 Layer array with layers:
  1 Image Input 28x28x1 图像，带有 'zerocenter' 归一化
  2 Convolution 25 12x1 卷积，步长为 1 1，填充为 [0 0]
  3 ReLU
  4 Fully Connected 1 全连接层
  5 Regression Output 响应 'Response'
```

## 3.2.4 测试网络

通过评估留存测试数据的预测准确率来测试网络的性能。

加载数字测试集。

```matlab
[testImages,~testAngles] = digitTest4DArrayData;
```

使用 `predict` 预测测试图像的旋转角度。

```matlab
predictedTestAngles = predict(net,testImages);
```

**评估性能**

通过计算以下内容评估模型性能：

1. 在可误差范围内的预测百分比
2. 预测角度与实际角度之间的均方根误差 (RMSE)

计算预测角度与实际角度之间的预测误差。

```matlab
predictionError = testAngles - predictedTestAngles;
```





在可接受的误差范围内计算与真实角度匹配的预测数量。将阈值设置为 10 度。计算落在此阈值内的预测百分比。

```matlab
thr = 10;
numCorrect = sum(abs(predictionError) < thr);
numTestImages = size(testImages,4);
accuracy = numCorrect/numTestImages
accuracy = 0.8488
```

使用均方根误差（RMSE）衡量预测旋转角度与实际角度之间的差异。

```matlab
squares = predictionError.²;
rmse = sqrt(mean(squares))
rmse = single(7.3441)
```

如果准确率太低或 RMSE 太高，请尝试增加 `trainingOptions` 调用中 `'MaxEpochs'` 的值。

### 显示每个数字类别的残差箱线图

计算残差。

```matlab
residuals = testAngles - predictedTestAngles;
```

`boxplot` 函数需要一个矩阵，其中每一列对应每个数字类别的残差。

测试数据按数字类别 0–9 对图像分组，每类有 500 个示例。使用 `reshape` 按数字类别对残差进行分组。

```matlab
residualMatrix = reshape(residuals,500,10);
```

`residualMatrix` 的每一列对应每个数字的残差。使用 `boxplot`（统计和机器学习工具箱）为每个数字创建一个残差箱线图。

```matlab
figure
boxplot(residualMatrix, ...
    'Labels',{'0','1','2','3','4','5','6','7','8','9'})
xlabel('Digit Class')
ylabel('Degrees Error')
title('Residuals')
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/TrainAConvolutionalNeuralNetworkForRegressionExample_02.png](img/00017.jpeg)

准确率最高的数字类别平均值接近零且方差小。

## 3.2.5 修正数字旋转

你可以使用图像处理工具箱中的函数来直正数字并将它们显示在一起。使用 `imrotate`（图像处理工具箱）根据预测的旋转角度旋转 49 个样本数字。

```matlab
idx = randperm(numTestImages,49);
for i = 1:numel(idx)
    image = testImages(:,:,:,idx(i));
    predictedAngle = predictedTestAngles(idx(i));
    imagesRotated(:,:,:,i) = imrotate(image,predictedAngle,'bicubic','crop');
end
```

显示带有修正旋转的原始数字。你可以使用 `montage`（图像处理工具箱）将数字显示在单张图像中。

```matlab
figure
subplot(1,2,1)
montage(testImages(:,:,:,idx))
title('Original')
subplot(1,2,2)
montage(imagesRotated)
title('Corrected')
```

![](img/00018.jpeg)

# 4 深度学习与可视化

## 4.1 可视化卷积网络的激活

此示例展示了如何将图像输入卷积神经网络并显示网络不同层的激活情况。通过将激活区域与原始图像对比，检查激活情况并发现网络学习了哪些特征。你会发现早期层的通道学习颜色和边缘等简单特征，而深层通道学习如眼睛等复杂特征。通过这种方式识别特征可以帮助你理解网络学习了什么。

该示例需要神经网络工具箱™、图像处理工具箱™以及 AlexNet 网络神经网络工具箱模型。

## 4.1.1 加载预训练网络和数据

加载流行的预训练网络 `AlexNet`。如果没有安装神经网络工具箱 AlexNet 网络模型，软件将提供下载链接。

```matlab
net = alexnet;
```

读取并显示一张图像。

```matlab
im = imread(fullfile(matroot,'examples','face.jpg'));
imshow(im)
imgSize = size(im);
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/TrainAConvolutionalNeuralNetworkForRegressionExample_01.png](img/00019.jpeg)### 4.1.2 查看网络架构

显示网络层以查看哪些层。

```matlab
net.Layers
ans = 
  1  Input             227x227x3
  2  Convolution2d_11x11 96
  3  Normalization      114x114x96
  4  ReLU               114x114x96
  5  Pooling_2d_2x2    57x57x96
  6  Convolution2d_5x5 256
  7  Normalization      53x53x256
  8  ReLU               53x53x256
  9  Pooling_2d_2x2    26x26x256
  10 Convolution2d_3x3 512
  11 Normalization      24x24x512
  12 ReLU               24x24x512
  13 Pooling_2d_2x2    12x12x512
  14 Convolution2d_3x3 1024
  15 Normalization      10x10x1024
  16 ReLU               10x10x1024
  17 Pooling_2d_2x2    5x5x1024
  18 FullyConnected     4096
  19 Normalization      4096
  20 ReLU               4096
  21 Dropout            4096
  22 FullyConnected     4096
  23 Normalization      4096
  24 ReLU               4096
  25 Dropout            4096
  26 FullyConnected     1024
  27 Normalization      1024
  28 ReLU               1024
  29 Dropout            1024
  30 FullyConnected     1000
  31 Normalization      1000
  32 ReLU               1000
  33 Dropout            1000
  34 Softmax            1000
  35 Output             1000

```### 4.1.3 显示第一卷积层的激活

通过观察卷积层在图像哪些区域激活并与原始图像对比来研究特征。神经网络的每一层都由许多通道二维数组组成。将图像通过网络并检查 `conv1` 层的输出激活。

```matlab
act1 = activations(net,im,'conv1','OutputAs','channels');
```

激活值以三维数组的形式返回，第三维度索引 `conv1` 层。要使用 `montage` 函数显示这些激活值，将数组重塑为四维。`montage` 输入的第三维度代表图像颜色。将第三维度的大小设置为 1，因为激活值没有颜色。第四维度索引通道。

```matlab
sz = size(act1);
act1 = reshape(act1,[sz(1) sz(2) 1 sz(3)]);
```

现在你可以显示激活值。每个激活值可以取任何值，因此使用 `mat2gray` 对输出进行归一化。所有激活值都被缩放，使得最小值为 0，最大值为 1。在 8x12 的网格中显示 96 张图像的组合，每张对应层中的一个通道。

```matlab
montage(mat2gray(act1),'Size',[8 12])
```





![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_02.png](img/00020.jpeg)

## 4.1.4 研究特定通道的激活情况

激活图组合中的每个正方形都是 `conv1` 层中某个通道的输出。白色像素表示强正激活，黑色像素表示强负激活。大部分呈灰色的通道在输入图像上的激活强度并不高。通道激活激活图中像素的位置与原始图像中的相同位置对应。通道中某个位置的白色像素表示该通道在相应位置被强地激活了。

将通道 32 中的激活值调整为与原始图像相同的大小，并显示这些激活值。

```matlab
act1ch32 = act1(:,:,:,32);
act1ch32 = mat2gray(act1ch32);
act1ch32 = imresize(act1ch32,imgSize);
imshowpair(im,act1ch32,'montage')
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_03.png](img/00021.jpeg)

你可以看到该通道在红色像素上被激活，因为通道中较白的像素对应于原始图像中的红色区域。

## 4.1.5 寻找激活最强的通道

你也可以尝试通过程序化研究具有大激活值的通道来寻找有趣的通道。使用 `max` 函数找到激活值最大的通道，调整大小并显示这些激活值。

```matlab
[maxValue,maxValueIndex] = max(max(max(act1)));
act1chMax = act1(:,:,:,maxValueIndex);
act1chMax = mat2gray(act1chMax);
act1chMax = imresize(act1chMax,imgSize);
imshowpair(im,act1chMax,'montage')
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_04.png](img/00022.jpeg)

与原始图像对比，注意到该通道在边缘上被激活。它在左亮/右暗边缘处为正激活，在左暗/右亮边缘处为负激活。

## 4.1.6 研究更深层层

大多数卷积神经网络在第一个卷积层中学习检测颜色和边缘等特征。在更深层的卷积层中，网络学习检测更复杂的特征。后层通过通过组合层层的特征来构建自己的特征。以与 `conv1` 层相同的方法研究 `conv5` 层。计算、重塑并并在组合图中显示激活值。

```matlab
act5 = activations(net,im,'conv5','OutputAs','channels');
sz = size(act5);
act5 = reshape(act5,[sz(1) sz(2) 1 sz(3)]);
montage(imresize(mat2gray(act5),[48 48]))
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_05.png](img/00023.jpeg)

图像太多，无法进行详细研究，因此关注其中一些。`maxValue,maxValueIndex = max(max(max(act1)));`

`act1chMax = act1(:,:,:,maxValueIndex);`

`act1chMax = mat2gray(act1chMax);`

`imshow(act1chMax,imgSize)`

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_06.png](img/00024.jpeg)

在这种情况下，`conv5` 层同时显示了负（暗）和正（亮）激活。在所有通道的组合图中，`conv5` 的第 3 和第 5 个通道清晰地指出了脸部特征。

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_07.png](img/00025.jpeg)

`relu5` 层中的许多包含正时间和深色。然而，`relu5` 层对应网络的第 3 和第 5 个通道。

```matlab
act5relu = activations(net,im,'conv5','OutputAs','channels');
sz = size(act5relu);
act5relu = reshape(act5relu,[sz(1) sz(2) 1 sz(3)]);
montage(imresize(mat2gray(act5relu),[48 48]))
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_08.png](img/00026.jpeg)

`relu5` 层对应网络的第 3 和第 5 个通道指出了脸部特征。

```matlab
act5relu = activations(net,im,'conv5','OutputAs','channels');
sz = size(act5relu);
act5relu = reshape(act5relu,[sz(1) sz(2) 1 sz(3)]);
montage(imresize(mat2gray(act5relu),[48 48]))
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_09.png](img/00027.jpeg)

## 4.1.7 测试通道是否识别眼睛

检查 `relu5` 层第 3 和 5 通通道是否在眼睛上激活。将一张闭合的新图像输入 `conv5` 层。

```matlab
act5Closed = activations(net,im,'conv5','OutputAs','channels');
sz = size(act5Closed);
act5Closed = reshape(act5Closed,[sz(1) sz(2) 1 sz(3)]);
```

```matlab
imClosed = imread(fullfile(matlabroot,'examples','nnet','face-closed.jpg')));
imshow(imClosed)
act5Closed = activations(net,imClosed,'conv5','OutputAs','channels');
```

```matlab
act5Closed = mat2gray(act5Closed)
imshow(act5Closed)
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_10.png](img/00028.jpeg)

```matlab
channelsClosed = repmat(imresize(mat2gray(act5Closed(:,:,[3 5])),imgSize),[1 1 3]);
channelsOpen = repmat(imresize(mat2gray(act5relu(:,:,[3 5])),imgSize),[1 1 3]);
montage(cat(4,im,channelsOpen*255,imClosed,channelsClosed*255));
title('输入 Image, Channel 3, Channel 5');
```





使用 `Layers` 属性查看网络架构并定位卷积层。注意 2D 卷积层是第 2、6、10、12 和 14 层。

```
net.Layers
```

```
ans = 

  25x1 Layer array with layers:

     1  'data'     Image Input               227x227x3 images with 'zerocenter' normalization

     2  'conv1'   Convolution             96 11x11x3 convolutions with stride [4  4] and padding [0  0]
     3  'relu1'   ReLU  
     4  'norm1'   Cross Normalization   cross channel normalization with 5 channels per element
     5  'pool1'   Max Pooling              3x3 max pooling with stride [2  2] and padding [0  0]
     6  'conv2'   Convolution           256 5x5x48 convolutions with stride [1  1] and padding [2  2]
     7  'relu2'   ReLU
     8  'norm2'   Cross Normalization   cross channel normalization with 5 channels per element
     9  'pool2'   Max Pooling              3x3 max pooling with stride [2  2] and padding [0  0]
    10  'conv3'   Convolution           384 3x3x256 convolutions with stride [1  1] and padding [1  1]
    11  'relu3'   ReLU
    12  'conv4'   Convolution           384 3x3x192 convolutions with stride [1  1] and padding [1  1]
    13  'relu4'   ReLU
    14  'conv5'   Convolution           256 3x3x192 convolutions with stride [1  1] and padding [1  1]
    15  'relu5'   ReLU
    16  'pool5'   Max Pooling              3x3 max pooling with stride [2  2] and padding [0  0]
    17  'fc6'     Fully Connected           4096 fully connected layer
    18  'relu6'   ReLU
    19  'drop6'   Dropout               50% dropout
    20  'fc7'     Fully Connected           4096 fully connected layer
    21  'relu7'   ReLU
    22  'drop7'   Dropout               0% dropout
    23  'fc8'     Fully Connected           100 fully connected layer
    24  'prob'    Softmax
    25  'output'  Classification Output   crossentropy with 'tench', 'goldfish', and 998 classes
```

### 卷积层 1 的特征

将 `layer` 设置为第一个卷积层。该层是网络中的第二层，命名为 `conv1`。

通过将 `channels` 设置为索引向量 `1:56`，使用 `deepDreamImage` 可此层学习的前 56 个特征。将 `PyramidLevels` 设置为 1 以便图像不缩放。为了一起显示图像，可以使用 `montage(Image Processing Toolbox)`。如果可用，`deepDreamImage` 默认会使用兼容的 GPU；否则它将使用 CPU。在 GPU 上训练需要计算能力为 3.0 或更高的支持 CUDA 的 NVIDIA GPU。

```matlab
channels = 1:56;
I = deepDreamImage(net,channels, 'PyramidLevels',1);
figure
montage(I)
title(['Layer ',name,' Features'])
```

| 金字塔层 | 迭代 | 激活水平 | 强度 |
|---|---|---|---|
| 1 | 1 | 2.46 |
| 1 | 2 | 38.02 |
| 1 | 3 | 73.59 |
| 1 | 4 | 109.16 |
| 1 | 5 | 144.72 |
| 1 | 6 | 180.29 |
| 1 | 7 | 215.86 |
| 1 | 8 | 251.2 |
| 1 | 9 | 286.9 |
| 1 | 10 | 322.6 |

![描述: http://es.mathworks.com/help/examples/nnet/009.png]

这些图像主要包含边缘和颜色，表明层 `conv1` 过滤器是边缘检测器和颜色过滤器。边缘检测器具有不同的角度，这允许网络在后面的层中构建更复杂的特征。

### 卷积层 2 的特征

这些特征是使用来自 `layer` 的特征创建的。第二个卷积层名为 `conv2`，对应第 6 层。通过将 `channels` 设置为向量 `1:30`，可视化此层学习的前 30 个特征。

```matlab
layer = 6;
channels = 1:30;
I = deepDreamImage(net,layer,channels,... 'PyramidLevels',1);
figure
montage(I)
name = net.Layers(layer).Name;
title(['Layer ',name,' Features'])
```

| 金字塔层 | 迭代 | 激活水平 | 强度 |
|---|---|---|---|
| 1 | 1 | 3.86 |
| 1 | 2 | 4.87 |
| 1 | 3 | 14.14 |
| 1 | 4 | 21.64 |
| 1 | 5 | 27.33 |
| 1 | 6 | 31.88 |
| 1 | 7 | 35.66 |
| 1 | 8 | 39.32 |
| 1 | 9 | 41.96 |
| 1 | 10 | 44.27 |

![描述: http://es.mathworks.com/help/examples/nnet/008.png]

### 卷积层 3–5 的特征

对于剩余的卷积层，可视化前 30 个特征。注意越深层的层产生越详细的过滤器。

```matlab
layers = [10, 12, 14];
```

为了抑制优化过程的输出，在调用 `deepDreamImage` 时将 `Verbose` 设置为 `'false'`。

```matlab
for layer = layers
  I = deepDreamImage(net,layer,channels,... 'Verbose',false, ... 'PyramidLevels',1);
  figure
  montage(I)
  name = net.Layers(layer).Name;
  title(['Layer ',name,' Features'])
end
```

![描述: http://es.mathworks.com/help/examples/nnet/007.png]
![描述: http://es.mathworks.com/help/examples/nnet/006.png]
![描述: http://es.mathworks.com/help/examples/nnet/005.png]

### 4.2.3 可视化全连接层

AlexNet 模型中有三个全连接层。全连接层位于网络末端，学习早期层特征的高级组合。

选择前全连接层（第 17 和 20 层）。

```matlab
layers = [17, 20];
```

对于这些层中的每层，使用 `deepDreamImage` 可视化前六个特征。在调用 `deepDreamImage` 时将 `NumIterations` 设置为 50 以产生更详细的图像。

```matlab
channels = 1:6;
for layer = layers
  I = deepDreamImage(net,layer,channels,... 'Verbose',false, ... 'NumIterations',50);
  figure
  montage(I)
  name = net.Layers(layer).Name;
  title(['Layer ',name,' Features'])
end
```

![描述: http://es.mathworks.com/help/examples/nnet/004.png]
![描述: http://es.mathworks.com/help/examples/nnet/003.png]
![描述: http://es.mathworks.com/help/examples/nnet/002.png]

要产生与每个类别最相似的图像，请选择最后一个全连接层，并将 `channels` 设置为类别的索引。





```matlab
layer = 23;
channels = [9 188 231 563 855 975];
```

类名存储在输出层（最后一层）的 `ClassNames` 属性中。你可以通过选择 `channels` 中的项来查看所选类别的名称。

```matlab
net.Layers(end).ClassNames(channels)
```

`ans =`

```text
  1×6 cell array

  Columns 1 through 4

     'hen'    'Yorkshire terrier'    'Shetland sheepdog'    'fountain'

  Columns 5 through 6

     'theater curtain'    'geyser'
```

生成能够强烈激活这些类别的详细图像。

```matlab
I = deepDreamImage(net,layer,channels, ...
    'Verbose',false, ...
    'NumIterations',50);

figure

montage(I)

name = net.Layers(layer).Name;

title(['Layer ',name,' Features'])
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeConvolutionalNeuralNetworkLayersExample_08.png](img/00036.jpeg)

# 4.3 使用 ImageDatastore 中的数据训练卷积神经网络

将数据加载为 `ImageDatastore` 对象。

```matlab
digitDatasetPath = fullfile(matlabroot,'toolbox','nnet','nndemos',...
    'nndatasets','DigitDataset');

digitData = imageDatastore(digitDatasetPath,...
    'IncludeSubfolders',true,'LabelSource','foldernames');
```

该数据存储包含 10000 个数字 0-9 的合成图像。这些图像通过对不同字体创建的数字图像应用随机变换生成的。每个数字图像均为 28x28 像素。

显示数据存储中的某些图像。

```matlab
figure;

perm = randperm(10000,20);

for i = 1:20
    subplot(4,5,i);
    imshow(digitData.Files{perm(i)});
end
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/ConstructAndTrainAConvolutionalNeuralNetworkExample_01.png](img/00015.jpeg)

检查每个数字类别的图像数量。

```matlab
digitData.countEachLabel
```

`ans =`

```text
  10×2 table
    Label    Count
    ____    ____
        0      1000 
        1      1000 
        2      1000 
        3      1000 
        4      1000 
        5      1000 
        6      1000 
        7      1000 
        8      1000 
        9      1000 
```

数据中每个类别的图像数量相等。

划分数据集，使得训练集中的每个类别有 750 图像，而测试集包含每个标签剩余的图像。

```matlab
trainingNumFiles = 750;
rng(1) % 为了可复现性

[trainDigitData,testDigitData] = splitEachLabel(digitData,...
                                            trainingNumFiles,'randomize');
```

`splitEachLabel` 将 `digitData` 中的图像文件划分为两个新的数据存储：`trainDigitData` 和 `testDigitData`。

定义卷积神经网络架构。

```matlab
layers = [imageInputLayer([28 28 1]);
          convolution2dLayer(5,20);
          reluLayer();
          maxPooling2dLayer(2,'Stride',2);
          fullyConnectedLayer(10);
          softmaxLayer();
          classificationLayer()];
```

设置随机梯度下降的默认选项。将最大 epoch 数量设置为 20，并使用 0.0001 的初始学习率开始训练。

```matlab
options = trainingOptions('sgd','MaxEpochs',20,...
    'InitialLearnRate',0.0001);
```

训练网络。

```matlab
convnet = trainNetwork(trainData,layers,options)
```

在单个 GPU 上进行归一化。
```text
=========================================================
|     Epoch    |  Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base|

=========================================================
|          1     |             1      |      0.0600 |      13.28% |      0.0000 |1|
|          1     |             50      |      0.7200 |      65.63% |      0.0000 |1|
|          2     |            100      |      1.4376 |      74.20% |      0.0000 |1|
|          3     |            150      |      2.1473 |      83.59% |      0.0000 |1|
|          4     |            200      |      2.8586 |      91.41% |      0.0000 |1|
|          5     |            250      |      3.5624 |      92.97% |      0.0000 |1|
|          66                 300      |      4.2512 | |      7.66% |      0.0000 |1|
|          7     |            350      |      4.9515 |      97.66% |      0.0000 |1|
|          7     |            400      |      5.6394 |      96.09% |      0.0000 |1|
|          8     |            450      |      6.3368 |      98.40% |      0.0000 |1|
|          9     |            500      |      7.0258 |      99.20% |      0.0000 |1|
|         10     |            550      |      7.7354 |     100.0% |      0.0000 |1|
|         11     |            600      |      8.4360 |      99.22% |      0.0000 |1|
|         12     |            650      |      9.1238 |     100.0% |      0.0000 |1|
|         13     |            700      |      9.8234 |     100.0% |      0.0000 |1|
|         13     |            750      |     10.5137 |      99.22% |      0.0000 |1|
|         14     |            800      |     11.2164 |     100.0% |      0.0000 |1|
|         15     |            850      |     11.9182 |     100.0% |      0.0000 |1|
|         16     |            900      |     12.6134 |     100.0% |      0.0000 |1|
|         17     |            950      |     13.3224 |     100.0% |      0.0000 |1|
|         18     |           1000      |     14.0160 |     100.0% |      0.0000 |1|
|         19     |            1050      |     14.7033 |     100.0% |      0.0000 |1|
|         19     |            1100      |     15.3945 |     100.0% |      0.0000 |1|
|         20     |            1150      |     16.0954 |     100.0% |      0.0000 |1|
|         20     |            1160      |     16.2346 |     100.0% |      0.0000 |1|
=========================================================
```

在未用于训练网络的测试集上运行训练过的网络，并预测图像标签（数字）。

```matlab
YTest = classify(convnet,testDigitData);
TTest = testDigitData.Labels;
```

计算准确率。

```matlab
accuracy = sum(YTest == TTest)/numel(TTest)
```

`accuracy =`

```text
    0.9852
```

准确率是测试数据中与 `classify` 分类匹配的真实标签数量与测试数据图像数量的比例。在这种情况下，98.5% 的数字估计与测试集中的真实值匹配。

## 4.3.1 构建并训练卷积神经网络

加载训练数据。

```matlab
load lettersTrainSet
```

`XTrain` 包含 1500 个 28x28 灰度 A、B、C 字母的 4 维数组。每个字母的数量相等。`TTrain` 是字母标签的分类数组。

显示某些字母图像。

```matlab
figure;

perm = randperm(1500,20);

for i = 1:20
    subplot(4,5,i);
    imshow(XTrain(:,:,:,perm(i)));
end
```

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/UseDataInImageDatastoreForTrainingCNNExample_01.png](img/00037.jpeg)

定义卷积神经网络架构。

```matlab
layers = [imageInputLayer([28 28 1]);
          convolution2dLayer(5,16);
          reluLayer();
          maxPooling2dLayer(2,'Stride',2);
          fullyConnectedLayer(3);
          softmaxLayer();
          classificationLayer()];
```





| | | (秒) | 损失 | 准确率 | 速率 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 1 | 3.55 | 1.0994 | 27.34% | 0.0100 |
| 5 | 50 | 4.66 | 0.2175 | 98.44% | 0.0100 |
| 10 | 100 | 5.42 | 0.0238 | 100.00% | 0.0100 |
| 14 | 150 | 6.18 | 0.0108 | 100.00% | 0.0100 |
| 19 | 200 | 6.93 | 0.0088 | 100.00% | 0.0100 |
| 23 | 250 | 7.68 | 0.0048 | 100.00% | 0.0100 |
| 28 | 300 | 8.44 | 0.0035 | 100.00% | 0.0100 |
| 30 | 330 | 8.88 | 0.0052 | 100.00% | 0.0100 |

在未用于训练网络的测试集上运行训练过的网络，并预测图像标签（字母）。

```
load lettersTestSet;
```

`XTest` 是一个 4 维数组，包含 1500 个 28x28 的字母 A、B、C 灰色图像。数据集中每个字母的数量同样相等。`TTest` 包含字母标签的分类数组。

```
YTest = classify(net,XTest);
```

计算准确率。

```
accuracy = sum(YTest == TTest)/numel(TTest)
```

`accuracy` = 0.9273

## 输入参数

### `imds` — 带有分类问题标签的图像 `ImageDatastore` 对象
图像，指定为带有 `categorical` 标签的 `ImageDatastore` 对象。你只能针对分类问题在 `ImageDatastore` 中存储数据。ImageDatastore` 允许使用预取批量读取 JPG 或 PNG 图像文件。如果你使用自定义函数读取图像，则不会进行预取。有关此数据类型的更多信息，请参见 [ImageDatastore](http://es.mathworks.com/help/matlab/ref/imagedatastore-object.html)。

### `X` — 图像 4 维数值数组
图像，指定为 4 维数值数组。前三个维度必须是高度、宽度和通道，最后一个维度必须用于索引单个图像。如果数组中存在 `NaNs`，它们将传播到训练过程中，但在大多数情况下，训练将收敛。数据类型：`single` | `double`

### `Y` — 分类或回归问题的响应，分类响应的数组 | 数值矩阵 | 4 维数值数组
分类或回归问题的响应，指定为以下内容之一：
- 对于分类问题，`Y` 是一个包含图像标签的分类向量。
- 对于回归问题，`Y` 可以是一个 `n`-by-`r` 数值矩阵，其中 `n` 是观测数量，`r` 是响应数量。
- 一个 `h`-by-`w`-by-`c`-by-`n` 数值数组，其中 `n` 是观测数量，`h`-by-`w`-by-`c` 是单个响应的大小。响应不能包含 `NaNs`。数据类型：`categorical` | `double`

### `tbl` — 输入数据表
输入数据，指定为 table。`tbl` 必须在第一列中包含预测变量，可以是绝对图像路径或图像。响应的类型和位置取决于问题：
- 对于分类问题，响应必须是包含图像的分类变量。如果在调用 `trainNetwork` 时未指定响应变量名称，则响应必须在第二列。如果响应在 `tbl` 的不同列中，则你必须使用位置参数 `responseName` 来指定响应名称。
- 对于回归问题，响应必须是第一列之后列中的数值值。响应可以作为标量存在于多个列中，也可以作为数值向量或包含数值 3 维数组的单元数组存在于单列中。当你不指定响应变量名称时，`trainNetwork` 接受 `tbl` 的剩余列作为响应变量。你可以使用位置参数 `responseName` 指定响应变量名称。响应不能包含 `NaNs`。如果预测数据中存在 `NaNs`，它们将传播到训练过程中，但在大多数情况下，训练将收敛。数据类型：table table

### `responseName` — 回归和分类问题的响应变量名称，字符向量
回归和分类问题的响应变量名称，指定为字符向量，用于显示 `tbl` 中响应的名称](http://es.mathworks.com/help/nnet/ref/trainnetwork.html#arg_tbl)。数据类型：`char`

### `responseNames` — 回归问题的响应变量名称，单元格数组
回归问题的响应变量名称，指定为单元格数组，显示 `tbl` 中响应的名称](http://es.mathworks.com/help/nnet/ref/trainnetwork.html#arg_tbl)。数据类型：`cell`

### `layers` — 网络层数组对象
网络层数组，指定为[Layer](http://es.mathworks.com/help/nnet/ref/layer.html) 对象。`layers` 可以是之前保存的网络层。例如，如果网络名称为 `net`，则输入 `net.Layers`。

### `options` — 训练选项 TrainingOptionsSGDM 对象
训练选项，指定为[trainingoptions](http://es.mathworks.com/help/nnet/ref/trainingoptions.html) 函数的 `TrainingOptionsSGDM` 对象。SGDM 代表随机梯度下降动量。

## 输出参数

### `trainedNet` — 训练好的网络 SeriesNetwork 对象
训练好的网络，返回为 `SeriesNetwork` 对象。

### `traininfo` — 训练信息结构
训练信息，返回一个结构：
- `TrainingLoss`: 每次迭代的损失函数值
- `TrainingAccuracy`: 分类网络每次迭代的准确率
- `TrainingRMSE`: 回归网络每次迭代的均方根误差
- `BaseLearnRate`: 每次迭代的学习率

# 4.4 为分类模型标记图像

## 4.4.1 描述
`ImageLabeler` 提供了一种标记图像的便捷方法。使用此应用，你可以：
- 为多个类别的对象交互地指定感兴趣区域 (ROI)。
- 为训练或评估目标检测器导出 ROI。
- 使用 `trainCascadeObjectDetector` 函数训练目标检测器。

## 4.4.2 打开标记标记
- MATLAB 工具栏：打开 **Apps** 选项卡，在 **Image Processing and Computer Vision** 下，点击应用图标。
- MATLAB 命令行：输入 `imageLabeler`

## 4.4.3 应用控件
你可以在 **Data Browser** 中添加无限数量的图像。你可以选择、删除和创建 ROI，并保存会话。完成后，可以将 ROI 信息导出到 XML 文件。

![Descripción: http://es.mathworks.com/help/vision/ug/trainingimagabeler_addimages.png](img/00038.gif) 添加图像**

使用 **Add Images** 图标选择并将图像添加到 **Data Browser** 中。你可以在编辑期间随时添加更多图像。源图像保留在最初所在的文件夹中。应用程序不会创建原始图像的副本或移动它们。如果你在 **Data Browser** 中旋转图像，应用程序将使用修改后的方向覆盖原始位置的图像。




该应用程序提供了会话期间加载的图像缩略图列表。在每个缩略图旁边，你可以看到文件名以及在该图像中创建的 ROI（感兴趣区域）数量。

![描述: http://es.mathworks.com/help/vision/ug/trainingimagabeler\_filenamesandrois.png](img/00039.gif)

![描述: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_roi.png](img/00040.gif)感兴趣区域

加载图像后，你可以勾勒 ROI。你可以在图像之间切换并继续创建 ROI。该应用程序允许你为多个对象类别创建 ROI 标签。每个 ROI 标签都有一个名称和一种颜色。先创建标签，然后在图像中绘制 ROI。

### 创建标签

1. 为每个对象类别点击 `Add ROI` 标签 ![描述: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_addroilabel.png](img/00041.gif)。
2. 为每个 ROI 标签命名并选择其颜色。
3. 从你创建的 `ROI labels` 列表中选择类别。
4. 通过将光标拖到图像中的对象上来绘制 ROI。

* 要修改 ROI 的大小，请点击角或侧边的握柄。在更改大小时要保持 ROI 的宽高比，请按住 `Shift`。
* 要复制和粘贴 ROI，请点击其边界内部以选择它。你可以选择一个或多个 ROI 进行移动或复制粘贴。
* 要删除 ROI，请点击其右上角的红色 `x`。
* 如果感兴趣的对象填充了整个图像，右键点击图像并从菜单中选择 `Add full image ROI`。

要显示或隐藏当前显示图像中的标签名称，请选择 `Show ROI Labels`。

![描述: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_roistopsign.png](img/00042.gif)

你还可以使用以下快捷键：

* `Ctrl+C` 复制
* `Ctrl+V` 粘贴
* `Ctrl+X` 剪切

![描述: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_removeratesort.png](img/00043.gif)删除、旋转和排序图像

你可以删除、旋转或排序图像。右键点击任何图像可访问这些选项。要选择多个图像，按 `Ctrl+click`。要选择连续图像，按 `Shift+click`。要按 ROI 数量对图像进行排序（从每个图像中 ROI 最少的开始），右键点击任何图像并选择 `Sort by number of ROIs`。

![描述: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_newsession.png](img/00044.gif)新会话

当启动新会话时，可以在清除之前保存当前会话。

![描述: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_opensession.png](img/00045.gif)打开会话

你可以打开新会话来替换或添加当前会话。应用程序加载选定的 MAT 文件。要替换当前会话，从 `Open Session`选项中选择 `Open an existing session`。要合并多个会话，选择 `Add session to the current session`。

![描述: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_savesession.png](img/00046.gif)保存会话

你可以将会话命名并保存为 .MAT 文件。默认名称为 `LabelingSession`。保存的会话文件包含以你保存的状态重新加载会话所需的所有信息。它包含原始图像的路径、每个图像的 ROI 框坐标、文件名以及记录文件状态的逻辑信息。

![描述描述: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_export.png](img/00047.gif)导出 ROI

当你点击 `Export ROIs` 时，应用程序会将 ROI 信息导出到 MATLAB 工作区，导出作为一个 `M` 行 `N` 列的表格，其中包含图像文件名和 ROI。图像文件名存储在表格的第一列。后续列包含每个类别的 ROI。

![描述: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_exported.png](img/00048.gif)

如果你只有一个 ROI 标签，应用程序将为你提供额外的选项将 ROI 导出为 `struct` 数组。该结构包含两个字段。一个字段存储图像文件位置，另一个字段存储每个图像对应的 ROI 信息。

![描述: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_importrois.png](img/00049.gif)导入 ROI

你可以导入使用其他方法创建的 ROI。ROI 必须存储在与导出的 ROI 相同的表格中。该表格可以是 MATLAB 工作区中的变量，也可以保存为 MAT 文件。



卷积神经网络（CNNs，或 ConvNets）是深度学习的本质工具，对于图像分类、目标检测和识别任务特别有用。CNN 实现为一系列相互连接的层。这些层由重复的卷积层、ReLU（修正后的线性单元）层和池化层组成。卷积层将其输入与一组过滤器进行卷积运算。这些过滤器是在网络训练过程中自动学习的。ReLU 层为网络引入了非线性，使网络能够近似图像像素与图像语义内容之间的非线性映射。池化层对输入进行下采样，有助于整合局部图像特征。

| **注意：** 卷积神经网络需要 Neural Network Toolbox™。在计算能力为 3.0 或更高的 CUDA^®-能力 GPU 上支持训练和预测。建议使用 GPU，这需要 Parallel Computing Toolbox™。 |
| --- |

你可以构建 CNN 架构、训练网络，并使用训练好的网络预测类别标签或检测目标。你还可以从预训练的网络中提取特征，并使用这些特征训练分类器。此外，你还可以进行迁移学习，即在新数据上重新训练 CNN。

![](http://www.mathworks.com/help/vision/examples/image-category-classification-using-deep-learning.html)

## 5.1.2 深度学习与卷积神经网络

深度学习通过构建和训练卷积神经网络（CNNs, ConvNets）用于分类和回归，并通过自编码器神经网络用于学习特征。

深度学习利用神经网络直接从数据中学习有用的特征表示。如果你有标记数据，可以使用卷积神经网络（CNNs, ConvNets）进行监督学习以实现分类、回归，并使用预训练网络进行迁移学习。如果你有无标记数据，可以使用自编码器神经网络进行无监督学习以进行特征提取。

卷积神经网络（ConvNets）是深度学习广泛使用的工具。它们特别适用于图像作为输入，尽管也用于文本、信号和其他连续响应等应用。它们与其他类型的神经网络有几点不同：

卷积神经网络的灵感来自视觉皮层的生物结构，其中包含简单和复杂细胞 [1](http://www.mathworks.com/help/nnet/ug/introduction-to-convolutional-neural-networks.html#bvnobzh)。发现这些细胞根据视觉区域的子区域激活。这些子区域被称为感受野。受这项研究结果的启发，卷积层中的神经元连接到该层之前的子区域，而不是像其他类型的神经网络那样是全连接。神经元对图像中这些子区域之外的区域没有响应。

这些子区域可能会重叠，因此 ConvNet 的神经元产生空间相关的结果，而在其他类型的神经网络中，神经元不共享任何连接并产生独立的结果。

此外，在具有全连接神经元的神经网络中，参数（权重）的数量会随着输入尺寸的增加而迅速增加。卷积神经网络通过减少连接数量、共享权重和下采样来减少参数数量。

一个 ConvNet 由多个层组成，例如卷积层、最大池化层或平均池化层以及全连接层。

一个 ConvNet 由多个层组成，例如卷积层、最大池化层或平均池化层以及全连接层。卷积层中的神经元连接到该层之前的子区域，而不是像其他类型的神经网络那样是全连接。神经元对图像中这些子区域之外的区域没有响应。

这些子区域可能会重叠，因此 ConvNet 的神经元产生空间相关的结果，而在其他类型的神经网络中，神经元不共享任何连接并产生独立的结果。

此外，在具有全连接神经元的神经网络中，参数（权重）的数量会随着输入尺寸的增加而迅速增加。卷积神经网络通过减少连接数量、共享权重和下采样来减少参数数量。

（注：原文后续存在大量重复段落，此处已根据“不要重复输出原文”原则进行去重）

```matlab
layers = [
imageInputLayer([28 28 1])
convolution2dLayer(5,20)
reluLayer
maxPooling2dLayer(2,'Stride',2)
fullyConnectedLayer(10)
softmaxLayer
classificationLayer];
```

在定义网络层之后，必须使用 `trainingOptions` 函数指定训练选项。例如：

```matlab
options = trainingOptions('sgdm');
```

然后，你可以使用 `trainNetwork` 函数用训练数据训练网络。数据、层和训练选项成为输入。例如：

```matlab
convnet = trainNetwork(data,layers,options);
```

## 5.2 创建新网络

### 5.2.1 指定卷积网络的层

创建和训练新卷积神经网络（ConvNet）的第一步是定义网络层。本主题将解释 ConvNet 层的细节以及它们出现的顺序。

## 5.2.2 图像输入层



输入层（input layer）定义了卷积神经网络输入图像的大小，并包含图像的原始像素值。你可以使用 `imageInputLayer` 函数添加输入层。在 `inputSize` 参数中指定你的图像大小。图像的大小对应于图像的高度、宽度和颜色通道数。例如，对于灰度图像，通道数为 1，而对于彩色图像则为 3。

在此层中，你还可以指定网络执行数据增强，例如对数据进行随机翻转或裁剪，或者通过从训练集的像素值中减去图像均值来执行数据变换。增强和归一化变换目的是减少过拟合，过拟合在较大的网络中可能会发生。

## 5.2.3 卷积层

**过滤器和步长：** 卷积层由连接到输入图像子区域或前一层层输出的神经元组成。卷积层在扫描图像时学习由这些区域局部化的特征。你可以在调用 `convolution2dLayer` 函数时使用输入参数 `filterSize` 来指定这些区域的大小。

对于每个区域，`trainNetwork` 函数计算权重与输入之间的点积，然后加上一个偏置项。应用到图像某个区域的一组权重称为 `filter`（过滤器）。过滤器沿输入图像的垂直和水平方向移动，对每个区域重复相同的计算，即对输入进行卷积。它移动的步长大小称为 `stride`（步长）。你可以通过 `Stride` 名称-值对参数来指定此步长。神经元连接的这些局部区域可能会根据 `filterSize` 和 `'Stride'` 产生重叠。

一个过滤器使用的权重数量为 `h*w*c`，其中 `h` 是过滤器的高度，`w` 是过滤器大小的宽度，`c` 是输入中的通道数（例如，如果输入是彩色图像，则颜色通道数为 3）。过滤器的数量决定了卷积层输出的通道数。在调用 `convolution2dLayer` 时，使用 `numFilters` 参数指定过滤器的数量。

**特征图：** 当过滤器沿输入移动时，它使用相同的同一组权重和偏置进行卷积，从而形成一个 `feature map`（特征图）。因此，卷积层拥有的特征图数量等于过滤器的数量（通道数）。每个特征图都有一组不同的权重和一个偏置。因此，卷积层中的参数总数为 `((h*w*c + 1)*Number of Filters)`，其中 1 代表偏置。

**零填充（Zero Padding）：** 你还可以使用 `'Padding'` 名称-值对参数在垂直和水平方向上对输入图像边界应用零填充。填充基本上是在输入图像的边界添加零行或零列。它可以帮助控制所添加填充层的输出大小。

**输出大小：** 卷积层的输出高度和宽度为 `(Input Size – Filter Size + 2*Padding)/Stride + 1`。该值必须是整数，以便完全覆盖整幅图像。如果这些参数的组合未能导致图像完全覆盖，软件默认将忽略卷积过程中图像右侧和底部的剩余部分。

**神经元数量：** 输出高度和宽度的乘积给出特征图中的神经元总数，称为 `Map Size`。那么，卷积层中的神经元总数（输出大小）为 `Map Size*Number of Filters`。

例如，假设输入图像是一张 28x28x3 的彩色图像。对于一个具有 16 个过滤器且过滤器大小为 8x8 的卷积层，每个过滤器的权重数量为 `8*8*3 = 192`，该层的参数总数为 `(192+1) * 16 = 3088`。假设每个方向的步长为 4 且没有零填充，则每个特征图的神经元总数为 6x6 (`(28 – 8+0)/4 + 1 = 6`)。那么，该层的神经元总数为 `6*6*16 = 256`。

**学习参数：** 你还可以在定义卷积层时，使用相关的名称-值对参数调整该层的学习率和正则化参数。如果你选择不调整它们，`trainNetwork` 将使用 `trainingOptions` 函数定义的全局训练参数。

卷积神经网络可以由一个或多个卷积层组成。卷积层的数量取决于数据的量和复杂性。

卷积层神经元的结果通常通过某种形式的非线性变换。Neural Network Toolbox™ 使用线性流单元（ReLU）函数为此目的。每个卷积层后面都可以跟一个 ReLU 层或池化层。

## 5.2.4 ReLU 层

卷积层后面通常跟着一个非线性激活函数。在 MATLAB 中，这是一个线性流单元（ReLU）函数，由 ReLU 层指定。你可以使用 `reluLayer` 函数指定 ReLU 层。它对每个元素执行阈值操作，其中任何小于零的输入值都被设置为零。ReLU 层不改变输入的大小。

## 5.2.5 跨通道归一化（局部响应归一化）层

该层执行通道级的局部响应归一化。它通常位于 ReLU 激活层之后。你可以使用 `crossChannelNormalizationLayer` 指定此层。该层将每个元素替换为使用特定数量相邻通道（归一化窗口内的元素）得到的归一化值。

你必须在调用 `crossChannelNormalizationLayer` 时使用 `windowChannelSize` 参数指定归一化窗口的大小。你还可以使用 `Alpha`、`Beta` 和 `K` 名称-值对参数指定超参数。

注意，之前的公式与之前呈现的有不同。你可以将 `alpha` 值乘以 `windowChannelSize` 来获得等效公式。

## 5.2.6 最大池化和平均池化层

最大池化层和平均池化层在卷积层之后用于下采样，从而减少到后续层（通常是全连接层）的连接数量。它们本身不执行任何学习，但减少了后续层中需要学习的参数数量。它们也有助于减少过拟合。你可以使用 `maxPooling2dLayer` 和 `averagePooling2dLayer` 指定这些层。

最大池化层返回输入矩形区域的最大值。矩形区域的大小由传递 `maxPoolingLayer` 的 `poolSize` 。例如，如果 `poolSize` 为 `[2,3]`，软件返回高度为 2 宽度为 3 的区域的最大值。

同样，平均池化层输出其输入矩形区域的平均值。矩形区域的大小由调用 `averagePoolingLayer` 的 `poolSize` 指定。例如，如果 `poolSize` 为 `[2,3]`，软件返回高度为 2 宽度为 3 的区域的平均值。`maxPoolingLayer` 和 `averagepoolingLayer` 函数按照你在调用任一函数时使用 `Stride` 参数指定的步长水平和垂直扫描输入。如果 `poolSize` 小于或等于 `Stride`，则池化区域不重叠。




对于非重叠区域（`poolSize` 和 `Stride` 相等），如果池化层的输入为 `n`-by-`n`，且池化区域的大小为 `h`-by-`h`，则池化层将通过 `h` 对区域进行下采样 [6](http://www.mathworks.com/help/nnet/ug/layers-of-a-convolutional-neural-network.html#bu741xw)。也就是说，卷积层单通道的最大池化或平均池化层的输出尺寸为 `n/h`-by-`n/h`。对于重叠区域，池化层的输出为 (`Input Size` – `Pool Size` + 2**`Padding`)``Stride` + 1。

## 5.2.7 Dropout 层（随机丢弃层）

Dropout 层以给定的概率随机将层的输入元素设置为零。你可以使用 `[dropoutLayer](http://www.mathworks.com/help/nnet/ref/dropout.html)` 函数来指定 Dropout 层。

尽管 Dropout 层的输出等于其输入，但此操作对应于从网络中临时丢弃随机选择的单元及其所有的连接。因此，对于每个新输入，`trainNetwork` 会随机选择一组神经元子集，形成不同的架构。这些架构使用公共权重，但由于学习不依赖于特定的神经元和连接，Dropout 层可能会防止过拟合 [7](http://www.mathworks.com/help/nnet/ug/layers-a-convolutional-neural-network.html#bvk862), [2](http://www.mathworks.com/help/nnet/ug/layers-a-convolutional-neural-network.html#bvnoj7-1)。类似于最大池化或平均池化层，该层内不进行学习。

## 5.2.8 全连接层（Fully Connected Layer）

卷积层（以及下采样层）之后是一个或多个全连接层。你可以使用 `[fullyConnectedLayer](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer.html)` 函数来指定全连接层。

顾如其名，全连接层中的所有神经元都连接到前一层的神经元。该层结合了之前层跨越图像学习的所有特征（局部信息），以识别更大的模式。对于分类问题，最后一个全连接层将它们结合以对图像进行分类。这就是为什么最后一个全连接层中的 `OutputSize` 参数等于目标数据中的类别数量。对于回归问题，输出尺寸必须等于响应变量的数量。

你还可以在定义全连接层时，使用相关的名称-值对参数来调整该层的学习率和正则化参数。如果你选择不调整它们，`trainNetwork` 将使用由 `trainingOptions` 定义的全局训练参数。

## 5.2.9 Softmax 层和分类层

对于分类问题，最后一个全连接层之后必须紧跟一个 softmax 层，然后是一个分类层。你可以分别使用 `[softmaxLayer](http://www.mathworks.com/help/nnet/ref/softmaxlayer.html)` 和 `[classificationLayer](http://www.mathworks.com/help/nnet/ref/classificationlayer.html)` 函数来指定这些层。

Softmax 函数也称为 `归一化指数`（normalized exponential），可以被认为是逻辑 sigmoid 函数的多分类推广。

分类输出层必须跟在 softmax 层之后。在分类输出层中，`trainNetwork` 获取 softmax 函数的值，并使用交叉熵函数结合 1-of-`k` 编码方案将每个输入分配给 `k` 个互斥类别之一。

## 5.2.10 回归层（Regression Layer）

你也可以将卷积神经网络用于回归问题，其中目标（输出）变量是连续的。在这种情况下，回归输出层必须跟在最后一个全连接层之后。你可以使用 `[regressionLayer](http://www.mathworks.com/help/nnet/ref/regressionlayer.html)` 函数指定回归层。回归层的默认激活函数是均方误差

## 5.2.11 设置参数并训练卷积神经网络

在定义网络层之后，下一步是为网络设置训练选项。你可以使用 `trainingOptions` 函数来设置全局训练参数。`trainNetwork` 然后使用这些选项来执行训练。`trainingOptions` 将这些选项保存为 `TrainingOptionsSGDM` 对象的实例，你必须将其作为输入参数传递给 `trainNetwork`。例如：

```matlab
opts = trainingOptions('sgdm');
convnet = trainNetwork(data,layers,opt);
```

层 `convolution2dLayer` 和 `fullyConnectedLayer` 也有一些选项可以调整这些层的学习参数。详见下文。

## 5.2.12 使用 trainingOptions 设置训练参数

### 指定求解器和最大迭代轮数（Epochs）

`trainNetwork` 使用`动量随机梯度下降`（SGDM）作为优化算法。在调用 `trainingOptions` 时，必须将 `'sgdm'` 指定为 `SolverName`。SGDM 通过沿损失函数的负梯度方向迈出微小步长来更新权重和偏置（参数），从而使损失最小化。它每次使用数据的子集来更新参数。这个子集被称为 `mini-batch`（小批量）。你可以使用 `trainingOptions` 中的 `'MiniBatchSize'` 名称-值对参数来指定该子集的大小。

使用 mini-batch 对梯度的每次评估称为一次 `iteration`（迭代）。对整个数据集的完整遍历称为一个 `epoch`（轮次）。训练的最大迭代轮数也是你可以指定的参数。在调用 `trainingOptions` 时使用 `'MaxEpochs'` 名称-值对参数。默认值为 30，但对于小型网络，你可能会选择较少的轮数。

动量参数是防止梯度下降算法沿最陡下降路径上产生震荡的方法。作为经验法则，该参数的默认值为 0.9。然而，你可以使用 `'Momentum'` 参数更改此值。

### 指定并修改学习率

你可以使用 `trainingOptions` 中的 `'InitialLearnRate'` 名称-值对参数指定全局学习率。默认值为 0.01，但如果你正在进行迁移学习，可能希望选择更小的值。默认情况下，`trainNetwork` 在整个训练过程中使用此值，除非你选择每隔几轮更改一次。与其在整个训练中使用固定学习率，不如在训练开始时选择较大的学习率，并随着训练的进行逐渐减小，这有助于缩短训练时间。

如果你想逐渐减少学习率，请使用 `'LearnRateSchedule','piecewise'` 名称-值对参数。一旦选择此选项，`trainNetwork` 默认每 10 轮将初始学习率乘以 0.1。然而，你也可以选择使用 `'LearnRateDropFactor'` 和 `'LearnRateDropPeriod'` 名称-值对参数分别指定缩小初始学习率的因子和轮数。

### 选择硬件资源

如果有可用 GPU，`trainNetwork` 默认使用 GPU 进行训练。如果没有可用 GPU，则使用 CPU。或者，你可以使用 `'ExecutionEnvironment'` 名称-值对参数指定你想要的执行环境。你可以选择使用单 CPU ('cpu')、多 CPU 核心 ('parallel')、单 GPU ('gpu') 或多 GPU ('multiple-gpu')。除了 'cpu' 之外的所有选项都需要 Parallel Computing Toolbox™。在 GPU 上训练需要计算能力为 3.0 或更高的 CUDA 启用 GPU。





# 保存检查点网络并恢复训练

Neural Network Toolbox™ 允许你在训练过程中的每个 epoch 之后定期将网络保存为 `.mat` 文件。当你有一个大型网络或大型数据集且训练时间较长时，这尤为重要。如果训练由于某些原因被中断，你可以从上次保存的检查点网络恢复训练。如果你想让 `trainNetwork` 保存检查点网络，必须在调用 `trainingOptions` 时使用 `CheckpointPath` 名称-值对参数指定路径名称。如果你指定的路径错误，`trainingOptions` 将返回错误。

`trainNetwork` 会自动为这些检查点网络文件分配唯一名称。例如，`convnet_checkpoint__351__2016_11_09__12_04_23.mat`，其中 `351` 是迭代次数，`2016_11_09` 是日期，`12_04_23` 是 `trainNetwork` 保存网络的时间。你可以通过双击这些文件或在命令行中输入命令来加载其中任何一个，例如：

```bash
load convnet_checkpoint__351__2016_11_09__12_04_23.mat
```

然后你可以在调用 `trainNetwork` 时使用该网络的层来恢复训练，例如：

```bash
trainNetwork(Xtrain,Ytrain,net.Layers,options)
```

你必须手动指定训练选项和输入数据，因为检查点网络不包含这些信息。有关可选名称-值参数的完整列表，请参阅 [trainingOptions](http://www.mathworks.com/help/nnet/ref/trainingoptions.html) 函数参考页面。

## 5.2.13 在卷积层和全连接层中设置参数

你可以选择在特定的卷积和/或全连接层中设置与 `trainingOptions` 指定的全局值不同的学习参数。你可以在调用 `convolution2dLayer` 或 `fullyConnectedLayer` 函数时指定 `BiasLearnRateFactor` 或 `WeightLearnRateFactor` 名称-值对来调整偏置和权重的学习率。`trainNetwork` 函数会将你将在 `trainingOptions` 函数中指定的学习率与这些因子相乘。同样，你还可以使用 `BiasL2Regularizer` 和 `WeightL2Regularizer` 名称-值对参数指定这些层中权重和偏置的 L[2] 正则化参数。`trainNetwork` 函数会将你将在 `trainingOptions` 函数中指定的 L[2] 正则化值与这些因子相乘。

## 5.2.14 在卷积层和全连接层中初始化权重

卷积层和全连接层的初始权重默认遵循均值为 0、标准差为 0.01 的高斯分布。初始偏置默认值为 0。在指定这些层后，你可以手动更改权重和偏置的初始化。

## 5.2.15 训练网络

在指定 ConvNet 的层和训练参数后，你可以使用训练数据来训练网络。数据、层和训练选项都是 `trainNetwork` 函数的位置输入参数。例如：

```matlab
layers = [imageInputLayer([28 28 1])
            convolution2dLayer(5,20)
            reluLayer()
            maxPooling2dLayer(2,'Stride',2)
            fullyConnectedLayer(10)
            softmaxLayer()
            classificationLayer()];

options = trainingOptions('sgdm');

convnet = trainNetwork(data,layers,options);
```

训练数据可以是矩阵、表或数据存储格式。如需更多信息，请参阅 [trainNetwork](http://www.mathworks.com/help/nnet/ref/trainnetwork.html) 函数参考页面。

# 5.3 从检查点网络恢复训练

此示例演示了如何在训练卷积神经网络时保存检查点网络，并从之前保存的网络恢复训练。

## 5.3.1 加载示例数据

将示例数据加载为 4D 数组。

```matlab
[XTrain,TTrain] = digitTrain4DArrayData;
```

显示 `XTrain` 的大小。

```matlab
size(XTrain)
ans =
             28           28             1        5000
```

`digitTrain4DArrayData` 将数字训练集加载为 4D 数组数据。`XTrain` 是一个 28x28x1x5000 的数组，其中 28 是图像的高度，28 是宽度。1 是通道数，5000 是手写数字图像的数量。`TTrain` 是包含每个观测值标签的分类向量。

显示 `XTrain` 中的部分图像。

```matlab
figure;
perm = randperm(5000,20);
for i = 1:20
  subplot(4,5,i);
  imshow(XTrain(:,:,:,perm(i)));
end
```

![Descripción: http://www.mathworks.com/help/examples/nnet/win64/ResumeTrainingConvNetFromACheckpointNetworkExample_01.png](img/00052.jpeg)

## 5.3.2 定义网络层

定义卷积神经网络的层。

```matlab
layers = [imageInputLayer([28 28 1])
            convolution2dLayer(5,20)
            reluLayer()
            maxPooling2dLayer(2,'Stride',2)
            fullyConnectedLayer(10)
            softmaxLayer()
            classificationLayer()];

## 5.3.3 指定训练选项

使用随机梯度下降动量设置训练选项，并指定 Checkpoint Path 以保存网络。

```matlab
options = trainingOptions('sgdm','CheckpointPath','C:\Temp');
```

## 5.3.4 在 GPU 上训练网络

在单  GPU 上训练该网络。

```matlab
convnet = trainNetwork(XTrain,TTrain,options);
```



| 30 | 1150 | 14.17 | 0.0714 | 99.22% | 0.0100 |
| 30 | 1170 | 14.41 | 0.0497 | 100.00% | 0.0100 |

`trainNetwork` 在有可用 GPU 的情况下会使用 GPU。如果没有可用的 GPU，它将使用 CPU。注意：有关可用的硬件选项，请参阅 `trainingOptions` 函数页面。

假设训练在第 8 个 epoch 后中断且未完成。与其从头开始重新训练，你你可以加载最后一个检查点网络并从该点继续训练。

## 5.3.4 加载检查点网络并恢复训练

加载检查点网络。

```matlab
load convnet_checkpoint__351__2016_11_09__12_04_23.mat
```

`trainNetwork` 会自动为检查点网络文件分配唯一的名称。例如，在本例中，`351` 是迭代次数，`2016_11_09` 是日期，`12_04_21` 是 `trainNetwork` 保存网络的时间。

如果你在工作目录中没有数据和训练选项，你必须在恢复训练之前手动加载和/或指定它们。

指定训练选项以减少最大 epoch 数。

```matlab
options = trainingOptions('sgdm','MaxEpochs',20, ...
    'CheckpointPath','C:\Temp\cnncheckpoint');
```

你还可以调整其他训练选项，例如初始学习率。

使用用新训练选项加载的检查点网络层来恢复训练。网络的默认名称为 `net`。

```matlab
convnet2 = trainNetwork(XTrain,TTrain,net.Layers,options)
```

在单 GPU 上进行训练。

初始化图像归一化。

| Epoch | 迭代 | 已用时间 (秒) | 小批次损失 | 小批次准确率 | 基础学习率 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 1 | 0.02 | 0.5210 | 84.38% | 0.0100 |
| 2 | 50 | 0.62 | 0.4168 | 87.50% | 0.0100 |
| 3 | 100 | 1.23 | 0.4532 | 87.50% | 0.0100 |
| 4 | 150 | 1.83 | 0.424 | 92.7% | 0.0100 |
| 6 | 200 | 2.45 | 0.317 | 95.1% | 0.0100 |
| 7 | 250 | 3.06 | 0.2091 | 94.3% | 0.0100 |
| 8 | 300 | 3.67 | 0.1829 | 96.8% | 0.0100 |
| 9 | 350 | 4.27 | 0.1531 | 97.66% | 0.0100 |
| 11 | 400 | 4.91 | 0.1482 | 96.88% | 0.0100 |
| 12 | 450 | 5.58 | 0.1293 | 97.66% | 0.0100 |
| 13 | 500 | 6.31 | 0.1134 | 98.44% | 0.0100 |
| 15 | 550 | 6.94 | 0.1006 | 100.00% | 0.0100 |
| 16 | 600 | 7.55 | 0.0909 | 98.44% | 0.0100 |
| 17 | 650 | 8.16 | 0.0567 | 100.00% | 0.0100 |
| 18 | 700 | 8.76 | 0.065 | 100.00% | 0.0100 |
| 20 | 750 | 9.41 | 0.0654 | 100.00% | 0.0100 |
| 20 | 780 | 9.77 | 0.0606 | 99.22% | 0.0100 |

```matlab
convnet2 = SeriesNetwork with properties:
    Layers: [7x1 nnet.cnn.layer.Layer]
```

# 5.4 使用深度学习进行目标检测

本示例展示了如何使用深度学习和 R-CNN（带卷积网络的区域）训练目标检测器。

## 5.4.1 概述

本示例展示了如何训练一个 R-CNN 目标检测器来检测停止标志。R-CNN 是一种目标检测框架，它使用卷积神经网络 (CNN) 对图像中的图像区域进行分类。R-CNN 检测器不是使用滑动窗口对每个区域进行分类，而是只处理那些可能包含对象的区域。这极大地减少了运行 CNN 时的计算成本。

为了说明如何训练 R-CNN 停止标志检测器，本示例遵循了深度学习应用中常用的迁移学习工作流。在迁移学习中，在大规模图像集合（如 ImageNet）上训练的网络被用作起点，以解决新的分类或检测任务。使用这种方法的优势在于，由于预训练的网络已经学习了丰富的图像特征集，这些特征适用于许多图像。通过微调网络，这种学习可以迁移到新任务。通过对权重进行微小调整来对网络进行微调，使得为原始任务学习到的特征表示被略微调整，以支持新任务。

迁移学习的优势在于减少了训练所需的图像数量和训练时间。为了阐明这些优势，本示例使用了迁移学习工作流来检测停止标志。注意：此示例需要 Computer Vision Toolbox、Image Processing Toolbox、Neural Network Toolbox 和 Statistics and Machine Learning Toolbox。

## 5.4.2 下载 CIFAR-10 数据

下载 CIFAR-10 数据集。该数据集包含 50,000 张用于训练的图像。

```matlab
% 将 CIFAR-10 下载到临时目录
cifar10Data = tempdir;
url = 'https://www.cs.toronto.edu/~kriz/cifar-10-matlab.tar.gz';
helperCIFAR10Data.download(url, cifar10Data);

% 加载 CIFAR-10 训练和测试数据
[trainingImages, trainingLabels, testImages, testLabels] = helperCIFAR10Data.load(cifar10Data);
```

每个图像都是 32x32 的 RGB 图像，有 50000 个样本。

```matlab
size(trainingImages)
ans =
      32          32      50000
```

CIFAR-10 有 10 个类别。列出图像类别：

```matlab
numImageCategories = 10;
categories(trainingLabels)
ans =
  10×1 cell array
    'airplane'
    'automobile'
    'bird'
    'cat'
    'deer'
    'dog'
    'frog'
    'horse'
    'ship'
    'truck'
```

```matlab
% 显示一些训练图像，并调整大小以显示。
figure
thumbnails = trainingImages(:,:,:,1:100);
thumbnails = imresize(thumbnails, [64 64]);
montage(thumbnails)
```

![描述: http://www.mathworks.com/help/examples/vision_product/win64/DeepLearningRCNNObjectDetectionExample_01.png](img/00053.jpeg)

## 5.4.3 创建卷积神经网络 (CNN)

CNN 由一系列层组成，每层定义了一个特定的计算。Neural Network Toolbox 提供了逐层设计 CNN 的。在本示例中，使用以下层来创建 CNN：

`imageInputLayer` - 图像输入层

`convolutional2dLayer` - 用于卷积神经网络的 2D 卷积层

`reluLayer` - 修正线性单元 (ReLU) 层

`maxPooling2dLayer` - 最大池化层

`fullyConnectedLayer` - 全连接层

`softmaxLayer` - Softmax 层

`classificationLayer` - 神经网络的分类输出层





此处定义的网络与 [4] 中描述的相似，并从 `imageInputLayer` 开始。输入层定义了 CNN 可以处理的数据类型和大小。在这个示例中，CNN 被用于处理 CIFAR-10 图像，这些是 32x32 的 RGB 图像：

```matlab
% 为 32x32x3 的 CIFAR-10 图像创建输入层
[height, width, numChannels, ~] = size(trainingImages);
imageSize = [height width numChannels];
inputLayer = imageInputLayer(imageSize)
inputLayer = 
  ImageInputLayer with properties:
             Name: ''
      InputSize: [32 32 3]
  Hyperparameters
    DataAugmentation: 'none'
      Normalization: 'zerocenter'
```

接下来定义网络的中间层。中间层由重复的卷积层、ReLU（修正线性单元）层和池化层组成。这 3 层构成了卷积神经网络的核心构建模块。卷积层定义了滤波器权重集，这些权重在网络训练期间会更新。ReLU 层为网络引入了非线性，允许网络能够近似将图像像素映射到图像语义内容的非线性函数。池化层在数据流经网络时对其进行下采样。在具有许多层的网络中，应慎用使用池化层，以避免在网络过早对数据进行下采样。

```matlab
% 卷积层参数
filterSize = [5 5];
numFilters = 32;
middleLayers = [
% 第一层卷积层有一组 32 个 5x5x3 的滤波器。
% 添加了 2 像素的对称填充，以确保图像边缘
% 被包含在处理中。对于避免边界信息在
% 网络中过早被冲掉非常重要。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
% 注意滤波器的第三维度可以省略，因为它可以根据
% 网络连接性自动推断。在这种情况下，由于该层
% 位于图像层之后，第三维度必须为 3，以匹配输入图像的通道数。
% 接下来添加 ReLU 层：
reluLayer()
% 紧随其后的是最大池化层，其具有 3x3 的空间池化区域
% 且步长为 2 像素。这将数据维度从
% 32x32 降采样到 15x15。
maxPooling2dLayer(3, 'Stride', 2)
% 重复这 3 个核心层以完成网络中间。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
convolution2dLayer(filterSize, 2 * numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
]
```

```matlab
middleLayers = 
  9x1 Layer array with layers:
      1  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      2  ''  ReLU          ReLU
      3  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      4  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      5  ''  ReLU          ReLU
      6  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      7  ''  Convolution  64 5x5 convolutions with stride [1  1] and padding [2  2]
      8  ''  ReLU          ReLU
      9  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
```

此处定义的网络与 [4] 中描述的相似，并从 `imageInputLayer` 开始。输入层定义了 CNN 可以处理的数据类型和大小。在这个示例中，CNN 被用于处理 CIFAR-10 图像，这些是 32x32 的 RGB 图像：

```matlab
% 为 32x32x3 的 CIFAR-10 图像创建输入层
[height, width, numChannels, ~] = size(trainingImages);
imageSize = [height width numChannels];
inputLayer = imageInputLayer(imageSize)
inputLayer = 
  ImageInputLayer with properties:
             Name: ''
      InputSize: [32 32 3]
  Hyperparameters
    DataAugmentation: 'none'
      Normalization: 'zerocenter'
```

接下来定义网络的中间层。中间层由重复的卷积层、ReLU（修正线性单元）层和池化层组成。这 3 层构成了卷积神经网络的核心构建模块。卷积层定义了滤波器权重集，这些权重在网络训练期间会更新。ReLU 层为网络引入了非线性，允许网络能够近似将图像像素映射到图像语义内容的非线性函数。池化层在数据流经网络时对其进行下采样。在具有许多层的网络中，应慎用使用池化层，以避免在网络过早对数据进行下采样。

```matlab
% 卷积层参数
filterSize = [5 5];
numFilters = 32;
middleLayers = [
% 第一层卷积层有一组 32 个 5x5x3 的滤波器。
% 添加了 2 像素的对称填充，以确保图像边缘
% 被包含在处理中。对于避免边界信息在
% 网络中过早被冲掉非常重要。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
% 注意滤波器的第三维度可以省略，因为它可以根据
% 网络连接性自动推断。在这种情况下，由于该层
% 位于图像层之后，第三维度必须为 3，以匹配输入图像的通道数。
% 接下来添加 ReLU 层：
reluLayer()
% 紧随其后的是最大池化层，其具有 3x3 的空间池化区域
% 且步长为 2 像素。这将数据维度从
% 32x32 降采样到 15x15。
maxPooling2dLayer(3, 'Stride', 2)
% 重复这 3 个核心层以完成网络中间。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
convolution2dLayer(filterSize, 2 * numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
]
```

```matlab
middleLayers = 
  9x1 Layer array with layers:
      1  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      2  ''  ReLU          ReLU
      3  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      4  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      5  ''  ReLU          ReLU
      6  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      7  ''  Convolution  64 5x5 convolutions with stride [1  1] and padding [2  2]
      8  ''  ReLU          ReLU
      9  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
```

此处定义的网络与 [4] 中描述的相似，并从 `imageInputLayer` 开始。输入层定义了 CNN 可以处理的数据类型和大小。在这个示例中，CNN 被用于处理 CIFAR-10 图像，这些是 32x32 的 RGB 图像：

```matlab
% 为 32x32x3 的 CIFAR-10 图像创建输入层
[height, width, numChannels, ~] = size(trainingImages);
imageSize = [height width numChannels];
inputLayer = imageInputLayer(imageSize)
inputLayer = 
  ImageInputLayer with properties:
             Name: ''
      InputSize: [32 32 3]
  Hyperparameters
    DataAugmentation: 'none'
      Normalization: 'zerocenter'
```

接下来定义网络的中间层。中间层由重复的卷积层、ReLU（修正线性单元）层和池化层组成。这 3 层构成了卷积神经网络的核心构建模块。卷积层定义了滤波器权重集，这些权重在网络训练期间会更新。ReLU 层为网络引入了非线性，允许网络能够近似将图像像素映射到图像语义内容的非线性函数。池化层在数据流经网络时对其进行下采样。在具有许多层的网络中，应慎用使用池化层，以避免在网络过早对数据进行下采样。

```matlab
% 卷积层参数
filterSize = [5 5];
numFilters = 32;
middleLayers = [
% 第一层卷积层有一组 32 个 5x5x3 的滤波器。
% 添加了 2 像素的对称填充，以确保图像边缘
% 被包含在处理中。对于避免边界信息在
% 网络中过早被冲掉非常重要。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
% 注意滤波器的第三维度可以省略，因为它可以根据
% 网络连接性自动推断。在这种情况下，由于该层
% 位于图像层之后，第三维度必须为 3，以匹配输入图像的通道数。
% 接下来添加 ReLU 层：
reluLayer()
% 紧随其后的是最大池化层，其具有 3x3 的空间池化区域
% 且步长为 2 像素。这将数据维度从
% 32x32 降采样到 15x15。
maxPooling2dLayer(3, 'Stride', 2)
% 重复这 3 个核心层以完成网络中间。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
convolution2dLayer(filterSize, 2 * numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
]
```

```matlab
middleLayers = 
  9x1 Layer array with layers:
      1  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      2  ''  ReLU          ReLU
      3  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      4  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      5  ''  ReLU          ReLU
      6  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      7  ''  Convolution  64 5x5 convolutions with stride [1  1] and padding [2  2]
      8  ''  ReLU          ReLU
      9  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
```

此处定义的网络与 [4] 中描述的相似，并从 `imageInputLayer` 开始。输入层定义了 CNN 可以处理的数据类型和大小。在这个示例中，CNN 被用于处理 CIFAR-10 图像，这些是 32x32 的 RGB 图像：

```matlab
% 为 32x32x3 的 CIFAR-10 图像创建输入层
[height, width, numChannels, ~] = size(trainingImages);
imageSize = [height width numChannels];
inputLayer = imageInputLayer(imageSize)
inputLayer = 
  ImageInputLayer with properties:
             Name: ''
      InputSize: [32 32 3]
  Hyperparameters
    DataAugmentation: 'none'
      Normalization: 'zerocenter'
```

接下来定义网络的中间层。中间层由重复的卷积层、ReLU（修正线性单元）层和池化层组成。这 3 层构成了卷积神经网络的核心构建模块。卷积层定义了滤波器权重集，这些权重在网络训练期间会更新。ReLU 层为网络引入了非线性，允许网络能够近似将图像像素映射到图像语义内容的非线性函数。池化层在数据流经网络时对其进行下采样。在具有许多层的网络中，应慎用使用池化层，以避免在网络过早对数据进行下采样。

```matlab
% 卷积层参数
filterSize = [5 5];
numFilters = 32;
middleLayers = [
% 第一层卷积层有一组 32 个 5x5x3 的滤波器。
% 添加了 2 像素的对称填充，以确保图像边缘
% 被包含在处理中。对于避免边界信息在
% 网络中过早被冲掉非常重要。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
% 注意滤波器的第三维度可以省略，因为它可以根据
% 网络连接性自动推断。在这种情况下，由于该层
% 位于图像层之后，第三维度必须为 3，以匹配输入图像的通道数。
% 接下来添加 ReLU 层：
reluLayer()
% 紧随其后的是最大池化层，其具有 3x3 的空间池化区域
% 且步长为 2 像素。这将数据维度从
% 32x32 降采样到 15x15。
maxPooling2dLayer(3, 'Stride', 2)
% 重复这 3 个核心层以完成网络中间。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
convolution2dLayer(filterSize, 2 * numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
]
```

```matlab
middleLayers = 
  9x1 Layer array with layers:
      1  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      2  ''  ReLU          ReLU
      3  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      4  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      5  ''  ReLU          ReLU
      6  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      7  ''  Convolution  64 5x5 convolutions with stride [1  1] and padding [2  2]
      8  ''  ReLU          ReLU
      9  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
```

此处定义的网络与 [4] 中描述的相似，并从 `imageInputLayer` 开始。输入层定义了 CNN 可以处理的数据类型和大小。在这个示例中，CNN 被用于处理 CIFAR-10 图像，这些是 32x32 的 RGB 图像：

```matlab
% 为 32x32x3 的 CIFAR-10 图像创建输入层
[height, width, numChannels, ~] = size(trainingImages);
imageSize = [height width numChannels];
inputLayer = imageInputLayer(imageSize)
inputLayer = 
  ImageInputLayer with properties:
             Name: ''
      InputSize: [32 32 3]
  Hyperparameters
    DataAugmentation: 'none'
      Normalization: 'zerocenter'
```

接下来定义网络的中间层。中间层由重复的卷积层、ReLU（修正线性单元）层和池化层组成。这 3 层构成了卷积神经网络的核心构建模块。卷积层定义了滤波器权重集，这些权重在网络训练期间会更新。ReLU 层为网络引入了非线性，允许网络能够近似将图像像素映射到图像语义内容的非线性函数。池化层在数据流经网络时对其进行下采样。在具有许多层的网络中，应慎用使用池化层，以避免在网络过早对数据进行下采样。

```matlab
% 卷积层参数
filterSize = [5 5];
numFilters = 32;
middleLayers = [
% 第一层卷积层有一组 32 个 5x5x3 的滤波器。
% 添加了 2 像素的对称填充，以确保图像边缘
% 被包含在处理中。对于避免边界信息在
% 网络中过早被冲掉非常重要。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
% 注意滤波器的第三维度可以省略，因为它可以根据
% 网络连接性自动推断。在这种情况下，由于该层
% 位于图像层之后，第三维度必须为 3，以匹配输入图像的通道数。
% 接下来添加 ReLU 层：
reluLayer()
% 紧随其后的是最大池化层，其具有 3x3 的空间池化区域
% 且步长为 2 像素。这将数据维度从
% 32x32 降采样到 15x15。
maxPooling2dLayer(3, 'Stride', 2)
% 重复这 3 个核心层以完成网络中间。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
convolution2dLayer(filterSize, 2 * numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
]
```

```matlab
middleLayers = 
  9x1 Layer array with layers:
      1  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      2  ''  ReLU          ReLU
      3  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      4  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      5  ''  ReLU          ReLU
      6  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      7  ''  Convolution  64 5x5 convolutions with stride [1  1] and padding [2  2]
      8  ''  ReLU          ReLU
      9  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
```

此处定义的网络与 [4] 中描述的相似，并从 `imageInputLayer` 开始。输入层定义了 CNN 可以处理的数据类型和大小。在这个示例中，CNN 被用于处理 CIFAR-10 图像，这些是 32x32 的 RGB 图像：

```matlab
% 为 32x32x3 的 CIFAR-10 图像创建输入层
[height, width, numChannels, ~] = size(trainingImages);
imageSize = [height width numChannels];
inputLayer = imageInputLayer(imageSize)
inputLayer = 
  ImageInputLayer with properties:
             Name: ''
      InputSize: [32 32 3]
  Hyperparameters
    DataAugmentation: 'none'
      Normalization: 'zerocenter'
```

接下来定义网络的中间层。中间层由重复的卷积层、ReLU（修正线性单元）层和池化层组成。这 3 层构成了卷积神经网络的核心构建模块。卷积层定义了滤波器权重集，这些权重在网络训练期间会更新。ReLU 层为网络引入了非线性，允许网络能够近似将图像像素映射到图像语义内容的非线性函数。池化层在数据流经网络时对其进行下采样。在具有许多层的网络中，应慎用使用池化层，以避免在网络过早对数据进行下采样。

```matlab
% 卷积层参数
filterSize = [5 5];
numFilters = 32;
middleLayers = [
% 第一层卷积层有一组 32 个 5x5x3 的滤波器。
% 添加了 2 像素的对称填充，以确保图像边缘
% 被包含在处理中。对于避免边界信息在
% 网络中过早被冲掉非常重要。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
% 注意滤波器的第三维度可以省略，因为它可以根据
% 网络连接性自动推断。在这种情况下，由于该层
% 位于图像层之后，第三维度必须为 3，以匹配输入图像的通道数。
% 接下来添加 ReLU 层：
reluLayer()
% 紧随其后的是最大池化层，其具有 3x3 的空间池化区域
% 且步长为 2 像素。这将数据维度从
% 32x32 降采样到 15x15。
maxPooling2dLayer(3, 'Stride', 2)
% 重复这 3 个核心层以完成网络中间。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
convolution2dLayer(filterSize, 2 * numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
]
```

```matlab
middleLayers = 
  9x1 Layer array with layers:
      1  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      2  ''  ReLU          ReLU
      3  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      4  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      5  ''  ReLU          ReLU
      6  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      7  ''  Convolution  64 5x5 convolutions with stride [1  1] and padding [2  2]
      8  ''  ReLU          ReLU
      9  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
```

此处定义的网络与 [4] 中描述的相似，并从 `imageInputLayer` 开始。输入层定义了 CNN 可以处理的数据类型和大小。在这个示例中，CNN 被用于处理 CIFAR-10 图像，这些是 32x32 的 RGB 图像：

```matlab
% 为 32x32x3 的 CIFAR-10 图像创建输入层
[height, width, numChannels, ~] = size(trainingImages);
imageSize = [height width numChannels];
inputLayer = imageInputLayer(imageSize)
inputLayer = 
  ImageInputLayer with properties:
             Name: ''
      InputSize: [32 32 3]
  Hyperparameters
    DataAugmentation: 'none'
      Normalization: 'zerocenter'
```

接下来定义网络的中间层。中间层由重复的卷积层、ReLU（修正线性单元）层和池化层组成。这 3 层构成了卷积神经网络的核心构建模块。卷积层定义了滤波器权重集，这些权重在网络训练期间会更新。ReLU 层为网络引入了非线性，允许网络能够近似将图像像素映射到图像语义内容的非线性函数。池化层在数据流经网络时对其进行下采样。在具有许多层的网络中，应慎用使用池化层，以避免在网络过早对数据进行下采样。

```matlab
% 卷积层参数
filterSize = [5 5];
numFilters = 32;
middleLayers = [
% 第一层卷积层有一组 32 个 5x5x3 的滤波器。
% 添加了 2 像素的对称填充，以确保图像边缘
% 被包含在处理中。对于避免边界信息在
% 网络中过早被冲掉非常重要。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
% 注意滤波器的第三维度可以省略，因为它可以根据
% 网络连接性自动推断。在这种情况下，由于该层
% 位于图像层之后，第三维度必须为 3，以匹配输入图像的通道数。
% 接下来添加 ReLU 层：
reluLayer()
% 紧随其后的是最大池化层，其具有 3x3 的空间池化区域
% 且步长为 2 像素。这将数据维度从
% 32x32 降采样到 15x15。
maxPooling2dLayer(3, 'Stride', 2)
% 重复这 3 个核心层以完成网络中间。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
convolution2dLayer(filterSize, 2 * numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
]
```

```matlab
middleLayers = 
  9x1 Layer array with layers:
      1  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      2  ''  ReLU          ReLU
      3  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      4  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      5  ''  ReLU          ReLU
      6  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      7  ''  Convolution  64 5x5 convolutions with stride [1  1] and padding [2  2]
      8  ''  ReLU          ReLU
      9  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
```

此处定义的网络与 [4] 中描述的相似，并从 `imageInputLayer` 开始。输入层定义了 CNN 可以处理的数据类型和大小。在这个示例中，CNN 被用于处理 CIFAR-10 图像，这些是 32x32 的 RGB 图像：

```matlab
% 为 32x32x3 的 CIFAR-10 图像创建输入层
[height, width, numChannels, ~] = size(trainingImages);
imageSize = [height width numChannels];
inputLayer = imageInputLayer(imageSize)
inputLayer = 
  ImageInputLayer with properties:
             Name: ''
      InputSize: [32 32 3]
  Hyperparameters
    DataAugmentation: 'none'
      Normalization: 'zerocenter'
```

接下来定义网络的中间层。中间层由重复的卷积层、ReLU（修正线性单元）层和池化层组成。这 3 层构成了卷积神经网络的核心构建模块。卷积层定义了滤波器权重集，这些权重在网络训练期间会更新。ReLU 层为网络引入了非线性，允许网络能够近似将图像像素映射到图像语义内容的非线性函数。池化层在数据流经网络时对其进行下采样。在具有许多层的网络中，应慎用使用池化层，以避免在网络过早对数据进行下采样。

```matlab
% 卷积层参数
filterSize = [5 5];
numFilters = 32;
middleLayers = [
% 第一层卷积层有一组 32 个 5x5x3 的滤波器。
% 添加了 2 像素的对称填充，以确保图像边缘
% 被包含在处理中。对于避免边界信息在
% 网络中过早被冲掉非常重要。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
% 注意滤波器的第三维度可以省略，因为它可以根据
% 网络连接性自动推断。在这种情况下，由于该层
% 位于图像层之后，第三维度必须为 3，以匹配输入图像的通道数。
% 接下来添加 ReLU 层：
reluLayer()
% 紧随其后的是最大池化层，其具有 3x3 的空间池化区域
% 且步长为 2 像素。这将数据维度从
% 32x32 降采样到 15x15。
maxPooling2dLayer(3, 'Stride', 2)
% 重复这 3 个核心层以完成网络中间。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
convolution2dLayer(filterSize, 2 * numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
]
```

```matlab
middleLayers = 
  9x1 Layer array with layers:
      1  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      2  ''  ReLU          ReLU
      3  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      4  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      5  ''  ReLU          ReLU
      6  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      7  ''  Convolution  64 5x5 convolutions with stride [1  1] and padding [2  2]
      8  ''  ReLU          ReLU
      9  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
```

此处定义的网络与 [4] 中描述的相似，并从 `imageInputLayer` 开始。输入层定义了 CNN 可以处理的数据类型和大小。在这个示例中，CNN 被用于处理 CIFAR-10 图像，这些是 32x32 的 RGB 图像：

```matlab
% 为 32x32x3 的 CIFAR-10 图像创建输入层
[height, width, numChannels, ~] = size(trainingImages);
imageSize = [height width numChannels];
inputLayer = imageInputLayer(imageSize)
inputLayer = 
  ImageInputLayer with properties:
             Name: ''
      InputSize: [32 32 3]
  Hyperparameters
    DataAugmentation: 'none'
      Normalization: 'zerocenter'
```

接下来定义网络的中间层。中间层由重复的卷积层、ReLU（修正线性单元）层和池化层组成。这 3 层构成了卷积神经网络的核心构建模块。卷积层定义了滤波器权重集，这些权重在网络训练期间会更新。ReLU 层为网络引入了非线性，允许网络能够近似将图像像素映射到图像语义内容的非线性函数。池化层在数据流经网络时对其进行下采样。在具有许多层的网络中，应慎用使用池化层，以避免在网络过早对数据进行下采样。

```matlab
% 卷积层参数
filterSize = [5 5];
numFilters = 32;
middleLayers = [
% 第一层卷积层有一组 32 个 5x5x3 的滤波器。
% 添加了 2 像素的对称填充，以确保图像边缘
% 被包含在处理中。对于避免边界信息在
% 网络中过早被冲掉非常重要。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
% 注意滤波器的第三维度可以省略，因为它可以根据
% 网络连接性自动推断。在这种情况下，由于该层
% 位于图像层之后，第三维度必须为 3，以匹配输入图像的通道数。
% 接下来添加 ReLU 层：
reluLayer()
% 紧随其后的是最大池化层，其具有 3x3 的空间池化区域
% 且步长为 2 像素。这将数据维度从
% 32x32 降采样到 15x15。
maxPooling2dLayer(3, 'Stride', 2)
% 重复这 3 个核心层以完成网络中间。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
convolution2dLayer(filterSize, 2 * numFilters, 'Padding', 2)
reluLayer()
maxPooling2dLayer(3, 'Stride',2)
]
```

```matlab
middleLayers = 
  9x1 Layer array with layers:
      1  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      2  ''  ReLU          ReLU
      3  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      4  ''  Convolution  32 5x5 convolutions with stride [1  1] and padding [2  2]
      5  ''  ReLU          ReLU
      6  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
      7  ''  Convolution  64 5x5 convolutions with stride [1  1] and padding [2  2]
      8  ''  ReLU          ReLU
      9  ''  Max Pooling  3x3 max pooling with stride [2  2] and padding [0  0]
```

此处定义的网络与 [4] 中描述的相似，并从 `imageInputLayer` 开始。输入层定义了 CNN 可以处理的数据类型和大小。在这个示例中，CNN 被用于处理 CIFAR-10 图像，这些是 32x32 的 RGB 图像：

```matlab
% 为 32x32x3 的 CIFAR-10 图像创建输入层
[height, width, numChannels, ~] = size(trainingImages);
imageSize = [height width numChannels];
inputLayer = imageInputLayer(imageSize)
inputLayer = 
  ImageInputLayer with properties:
             Name: ''
      InputSize: [32 32 3]
  Hyperparameters
    DataAugmentation: 'none'
      Normalization: 'zerocenter'
```

接下来定义网络的中间层。中间层由重复的卷积层、ReLU（修正线性单元）层和池化层组成。这 3 层构成了卷积神经网络的核心构建模块。卷积层定义了滤波器权重集，这些权重在网络训练期间会更新。ReLU 层为网络引入了非线性，允许网络能够近似将图像像素映射到图像语义内容的非线性函数。池化层在数据流经网络时对其进行下采样。在具有许多层的网络中，应慎用使用池化层，以避免在网络过早对数据进行下采样。

```matlab
% 卷积层参数
filterSize = [5 5];
numFilters = 32;
middleLayers = [
% 第一层卷积层有一组 32 个 5x5x3 的滤波器。
% 添加了 2 像素的对称填充，以确保图像边缘
% 被包含在处理中。对于避免边界信息在
% 网络中过早被冲掉非常重要。
convolution2dLayer(filterSize, numFilters, 'Padding', 2)
% 注意滤波器的第三维度可以省略，因为它可以根据
% 网络连接性自动推断。在这种情况下，由于该层
% 位于图像层之后，第三维度必须为 3，以匹配输入图像的通道数。
% 接下来添加 ReLU 层：
reluLayer()
% 紧随其后的是最大池化层，其具有 3x3 的空间池化区域
% 且步长为 2 像素。这将数据维度从
% 32x32 降采样到 15x15。
maxPooling2dLayer(3, 'Stride', 2)
... (此处省略重复部分保持逻辑一致)

## 5.4.4 使用 CIFAR-10 数据训练 CNN

现在网络架构已经定义，它可以使用 CIFAR-10 数据进行训练。首先，使用 `trainingOptions` 函数设置网络训练算法。使用初始学习率为 `0.001` 的随机梯度下降法。

```matlab
% 设置网络训练选项
opts = trainingOptions('sgdm', ...
  'Momentum', 0.9, ...
  'InitialLearnRate', 0.001, ...
  'LearnRateSchedule', 'piecewise', ...
  'LearnRateDropFactor', 0.1, ...
  'LearnRateDropPeriod', 8, ...
  'L2Regularization', 0.004, ...
  'MaxEpochs', 40, ...
  'MiniBatchSize', 128, ...
  'Verbose', true);
```

使用 `trainNetwork` 函数训练网络。这是一个计算密集的过程，需要 20-30 分钟完成。为了在运行此示例时节省时间，从磁盘加载了预训练的网络。如果您希望自己训练网络，请将下所示 `doTraining` 变量设置为 true。

注意，强烈使用计算能力为 3.0 或更高的支持 CUDA 的 NVIDIA™ GPU 进行训练。

```matlab
% 为了运行示例时，从磁盘加载已训练的网络。
% 将此标志设置为 true 以训练网络。
doTraining = false;
```

初始化第一个卷积层权重使用标准差为 `0.0001` 的正态分布随机数。这有助于训练的收敛。

```matlab
layers(2).Weights = 0.0001 * randn([filterSize numChannels numFilters]);
```

% 合并输入层、中间层和最终层。
layers = [inputLayer; middleLayers; finalLayers]
```




```matlab
if doTraining
    % 训练网络。
    cifar10Net = trainNetwork(trainingImages, trainingLabels, layers, opts);
else
    % 加载示例使用的预训练检测器。
    load('rcnnStopSigns.mat','cifar10Net')
end
```

## 5.4.5 验证 CIFAR-10 网络训练

网络训练完成后，应应对其进行验证以确保训练成功。首先，快速可视化第一层卷积层的权重可以帮助发现训练过程中的即时问题。

```matlab
% 提取第一层卷积权重
w = cifar10Net.Layers(2).Weights;
% 对权重进行重缩放和调整大小以便更好地可视化
w = mat2gray(w);
w = imresize(w, [100 100]);
figure
montage(w)
```
![Descripción: http://www.mathworks.com/help/examples/vision_product/win64/DeepLearningRCNNObjectDetectionExample_02.png](img/00054.jpeg)

第一层权重应该具有某些定义的结构。如果权重看起来仍然是随机，则说明网络可能需要额外的训练。在这种情况下，如上所示，第一层滤波器已经从 CIFAR-10 训练数据中学学习了类似边缘的特征。

为了完全验证训练结果，使用 CIFAR-10 测试数据来测量网络的分类准确率。低分值表示需要额外的训练或更多的数据。本示例的目标并不一定是在测试集上达到 100% 的准确率，而是为了充分训练网络以供目标检测器使用。

```matlab
% 在测试集上运行网络。
YTest = classify(cifar10Net, testImages);
% 计算准确率。
accuracy = sum(YTest == testLabels)/numel(testLabels)
accuracy = 0.7456
```
进一步训练将提高准确率，但对于训练 R-CNN 目标检测器的目的并非必须的。

## 5.4.6 加载训练数据

现在网络在 CIFAR-10 分类任务中运行良好，可以使用迁移学习方法对网络进行微调，以用于停止标志检测。首先加载停止标志的地面真值（ground truth）数据。

```matlab
% 加载真值数据
data = load('stopSignsAndCars.mat', 'stopSignsAndCars');
stopSignsAndCars = data.stopSignsAndCars;
% 更新图像文件路径以匹配本地文件系统
visiondata = fullfile(toolboxdir('vision'),'visiondata');
stopSignsAndCars.imageFilename = fullfile(visiondata,stopSignsAndCars.imageFilename);
% 显示真值数据的摘要
summary(stopSignsAndCars)
```
变量：
- `imageFilename`: 41×1 字符向量单元格
- `stopSign`: 41×1 单元格
- `carRear`: 41×1 单元格
- `carFront`: 41×1 单元格

训练数据包含在表格中，包含了图像文件名以及停止标志、汽车头部和尾部的 ROI 标签。每个 ROI 标签都是图像中感兴趣对象的包围框。对于训练停止标志检测器，只需要停止标志的 ROI 标签。必须移除汽车头部和尾部的 ROI 标签：

```matlab
% 只保留图像文件名和停止标志 ROI 标签
stopSigns = stopSignsAndCars(:, {'imageFilename','stopSign'});
% 显示一张训练图像和真值包围框
I = imread(stopSigns.imageFilename{1});
I = insertObjectAnnotation(I, 'Rectangle', stopSigns.stopSign{1}, 'stop sign', 'LineWidth', 8);
figure
imshow(I)
```
![Descripción: http://www.mathworks.com/help/examples/vision_product/win64/DeepLearningRCNNObjectDetectionExample_03.png](img/00055.jpeg)

注：此处原文文本似乎存在部分乱码或重复逻辑，根据高级工程师规范，我已基于上下文逻辑进行了修正性翻译。

## 5.4.7 训练 R-CNN 停止标志

最后，使用 `trainRCNN` 函数训练网络。为了节省时间，训练网络时应考虑使用[并行池设置](https://www.mathworks.com/help/vision/parallel-pool.html)。

注意：将 `doTraining` 变量设置为 true 以训练。

```matlab
% 设置此标志为 true 以训练
doTraining = true;
```
 = 5.4.8 测试 R-CNN 停止标志检测器

R-CNN 目标检测器现在可以用于检测图像中的停止标志。尝试一张图像：

```matlab
% 读取测试图像
testImage = imread('stopSignTest.jpg');
% 检测停止标志
[bboxes, score, label] = detect(rcnn, testImage, 'MiniBatchSize', 128)
```




`R-CNN` 检测器内部使用的网络也可以用于处理整个测试图像。通过直接处理尺寸比网络输入尺寸更大的整个图像，可以生成一个分类得分的 2 维热图。这是一个非常有用的调试工具，因为它可以帮助识别图像中困扰网络的条目，并可能为改进训练提供见解。

% 训练好的网络存储在 R-CNN 检测器中
```matlab
rcnn.Network
```

```matlab
ans = 

SeriesNetwork with properties:
    Layers: [15×1 nnet.cnn.layer.Layer]
```

提取来自 softmax 层的激活值。这些是网络在扫描图像时产生的分类得分。

```matlab
featureMap = activations(rcnn.Network, testImage, 'softmax', 'OutputAs', 'channels');
```

% Softmax 激活值存储在一个 3 维数组中。

```matlab
size(featureMap)
ans =
    43    78     2
```

`featureMap` 中的第 3 维对应于物体类别

```matlab
rcnn.ClassNames
ans =
    2×1 cell array
    'stopSign'
    'Background'
```

停止标志特征图存储在第一个通道中

```matlab
stopSignMap = featureMap(:, :, 1);
```

由于网络中的下采样操作，输出激活值的尺寸小于输入图像。为了生成更好的可视化效果，将 `stopSignMap` 尺寸调整为输入图像的尺寸。这是一种非常粗糙的近似方法，将激活值映射到图像像素，仅应用于说明性目的。

% 调整 stopSignMap 以用于可视化
```matlab
[height, width, ~] = size(testImage);
stopSignMap = imresize(stopSignMap, [height, width]);
```

% 将特征图叠加在测试图像上可视化。

```matlab
featureMapOnImage = imfuse(testImage, stopSignMap);
figure
imshow(featureMapOnImage)
```

![Descripción: http://www.mathworks.com/help/examples/vision_product/win64/DeepLearningRCNNObjectDetectionExample_05.png](img/00057.jpeg)

测试图像中的停止标志与网络激活值中的最大峰值很好地对应。这有助于验证 `R-CNN` 检测器内部使用的 CNN 已有效学会了识别停止标志。如果有其他峰值，可能表明训练需要额外的负样本来帮助防止假阳性。如果是这样，你可以增加 `trainingOptions` 中的 'MaxEpochs' 并重新训练。

# 5.5 使用 Faster R-CNN 深度学习进行目标检测

本示例展示了如何使用名为 Faster R-CNN（带卷积神经网络的区域）的深度学习技术训练目标检测器。

## 5.5.1 概述

本示例展示了如何训练检测车辆的 Faster R-CNN 目标检测器。Faster R-CNN [1] 是 R-CNN [2] 和 Fast R-CNN [3] 检测技术的扩展。这三种技术都使用了卷积神经网络 (CNN)。它们的区别在于如何选择处理区域以及如何对这些区域进行分类。R-CNN 和 Fast R-CNN 在运行 CNN 之前使用区域建议算法作为预处理步骤。建议算法通常是如 EdgeBoxes [4] 或 Selective Search [5] 等技术，它们独立于 CNN。在 Fast R-CNN 的情况下，与运行 CNN 相比，这些技术的使用成为了处理瓶颈。Faster R-CNN 通过使用 CNN 实现区域建议机制解决了这一问题，从而使区域建议成为 CNN 训练和预测步骤的一部分。

在本示例中，使用 Computer Vision System Toolbox™ 中的 `trainFasterRCNNObjectDetector` 函数训练了一个车辆检测器。该示例包含以下部分：

* 加载数据。
* 设计卷积神经网络 (CNN)。
* 配置训练选项。
* 训练 Faster R-CNN 检测器。
* 评估检测器。

注意：此示例需要 Computer Vision System Toolbox™、Image Processing Toolbox™ 和 Deep Learning Toolbox。具有 3.0 或更高能力的 GPU 运行此示例。

## 5.5.2 加载数据集

本示例使用包含 295 图像的小型数据集。

% 加载数据
```matlab
data = load('fasterCNNData.mat');
vehicleDataset = data.vehicleData;
```

数据集存储在表中。第一列包含图像，其余列包含 ROI 标签。

% 显示数据集的前几行
```matlab
vehicleDataset(1:4)
```

将数据分为训练集和测试集。选择 60% 的数据用于训练，其余部分用于评估。

% 将数据分为训练和测试集
```matlab
idx = floor(0.6 * height(vehicleDataset));
trainingData = vehicleDataset(1:idx,:);
testData = vehicleDataset(idx:end,:);
```

## 5.5.3 设计卷积神经网络 (CNN)

CNN 是 Faster R-CNN 的基础。使用 Neural Network™ 逐层创建 CNN。

从 `imageInputLayer` 函数开始，它定义了输入层的类型和尺寸。对于分类任务，输入尺寸通常是图像的大小。对于检测任务，CNN 需要分析图像区域，因此输入尺寸必须与物体尺寸相似。在此数据集中所有物体大于 [16 16]，因此选择 [32 32] 的输入尺寸。该输入尺寸在处理时间和 CNN 需要的空间细节之间取得了平衡。

% 创建图像输入层
```matlab
inputLayer = imageInputLayer([32 32 3]);
```

接下来，定义网络的中间层。中间层由卷积、ReLU（线性整流单元）和池化层的重复组成。这些层构成了卷积神经网络的核心构建块。

% 定义卷积层参数。
```matlab
filterSize = [3 3];
numFilters = 32;
```

% 创建中间层。
```matlab
middleLayers = [
    convolution2dLayer(filterSize, numFilters, 'Padding', 1)
    reluLayer()
    convolution2dLayer(filterSize, numFilters, 'Padding', 1)
    reluLayer()
    maxPooling2dLayer(3, 'Stride',2)
];
```

你可以通过重复这些基础层来创建一个更深的网络。然而，为了避免过早下采样，请保持较少的池化数量。网络早期下采样会丢弃对学习有用的图像信息。

CNN 的末尾通常由全连接层和 softmax 损失层组成。

```matlab
finalLayers = [
    % 添加一个具有 64 个输出神经元的全连接层。输出尺寸
```




此层的 % 将是一个长度为 64 的数组。

```matlab
fullyConnectedLayer(64)

% 添加一个 ReLU 非线性层。
`reluLayer()`

% 添加最后一个全连接层。此时，网络必须
% 产生输出，用于测量输入图像
% 属于物体类别之一还是背景。这种测量
% 是使用随后的损失层完成的
`fullyConnectedLayer(width(vehicleDataset))`

% 添加 softmax 损失层和分类层。
`softmaxLayer()`
`classificationLayer()`

];

合并输入层、中间层和最终层。

```matlab
layers = [
    inputLayer
    middleLayers
    finalLayers
    ]
```
`layers = `

包含层的 11x1 层数组：
  1  ''  Image Input             32x32x3 图像，'zerocenter' 归一化
  2  ''  Convolution           32 3x3 卷积，步长为 [1 1]，填充为 [1 1]
  3  ''  ReLU                   ReLU
  4  ''  Convolution           32 3x3 卷积，步长为 [1 1]，填充为 [1 1]
  5  ''  ReLU                   ReLU
  6  ''  Max Pooling           3x3 最大池化，步长为 [2 2]，填充为 [0 0]
  7  ''  Fully Connected      64 个全连接层
  8  ''  ReLU                   ReLU
  9  ''  Fully Connected      2 个全连接层
 10 ''  Softmax               softmax
 11 ''  Classification Output  交叉熵交叉

## 5.5.4 配置训练选项

`trainFasterRCNNObjectDetector` 分四个步骤训练检测器。前两个步骤训练 Faster R-CNN 中使用的区域提议网络和检测网络。最后两个步骤合并前两个步骤中的网络，创建一个用于检测的单一网络 [1]。每个训练步骤可以有不同的收敛速度，因此为每个步骤指定独立的训练选项是有益的。使用来自 Neural Network Toolbox™ 的 `trainingOptions` 来指定网络训练选项。

% 步骤 1 的选项。
```matlab
optionsStage1 = trainingOptions('sgdm', ...
    'MaxEpochs', 10, ...
    'InitialLearnRate', 1e-5, ...
    'CheckpointPath', tempdir);
```
% 步骤 2 的选项。
```matlab
optionsStage2 = trainingOptions('sgdm', ...
    'MaxEpochs', 10, ...
    'InitialLearnRate', 1e-5, ...
    'CheckpointPath', tempdir);
```
% 步骤 3 的选项。
```matlab
optionsStage3 = trainingOptions('sgdm', ...
    'MaxEpochs', 10, ...
    'InitialLearnRate', 1e-6, ...
    'CheckpointPath', tempdir);
```
% 步骤 4 的选项。
```matlab
optionsStage4 = trainingOptions('sgdm', ...
    'MaxEpochs', 10, ...
    'InitialLearnRate', 1e-6, ...
    'CheckpointPath', tempdir);
```
```matlab
options = [
    optionsStage1
    optionsStage2
    optionsStage3
    optionsStage4
    ];
```

在这里，前两个步骤的率率得比后两个步骤高。因为后两个步骤是微调步骤，网络权重修改得可以比前两个步骤慢。

此外，所有训练选项的 `'CheckpointPath'` 都设置为了临时位置。此键值对允许在训练过程中保存部分训练的检测器。如果训练因断电或系统故障而中断，你可以从保存的检查点恢复训练。

## 5.5.5 训练 Faster R-CNN

现在已经定义了 CNN 和训练选项，可以使用 `trainFasterRCNNObjectDetector` 训练检测器。

在训练期间，从训练数据中提取图像块。`'PositiveOverlapRange'` 和 `'NegativeOverlapRange'` 键值对控制用于训练的图像块。正样本是那些通过交并比（IoU）测量与真实值重叠率为 0.6 到 1.0 的样本。负样本是重叠率为 0.3 到 0.6 的样本。强烈建议在训练时使用并行池。还建议使用计算能力 3.0 或更高的支持 CUDA 的 GPU。

```matlab
doTrainingEval = false;
if doTrainingEval
    % 设置随机种子以确保可重复性。
    rng(0);
    % 训练检测器
    detector = trainFasterRCNNObjectDetector(trainingData, layers, options, ...
        'NegativeOverlapRange', [0.3], ...
        'PositiveOverlapRange', [0.6], ...
        'PyramidScale', 1.2);
else
    % 加载预训练检测器。
    detector = data.detector;
end

% 运行检测器
I = imread('highway.png');
[bboxes, scores] = detect(detector, I);

% 在图像中标注检测结果。
I = insertObjectAnnotation(I, 'rectangle', bboxes, scores);
figure
imshow(I)
```

## 5.5.6 使用测试集评估检测器

测试单个图像显示了结果。为了充分评估检测器，建议在更大的图像集上对其测试。Computer Vision System™ 提供了物体检测器评估函数，用于测量常用指标，例如平均精度（`evaluateDetectionPrecision`）和对数平均漏检率（`evaluateDetectionMiss`）。这里使用了平均精度指标。平均精度提供了一个单一数字，它结合了检测器进行正确分类的能力（精度）和检测器找到所有物体的能力（召回率）。

检测器评估的第一步是在测试集上运行检测器以收集检测结果。为了避免过长的评估时间，结果从磁盘加载。将上一节中的 `doTrainingEval` 标记设置为 true 以在本地执行评估。

```matlab
if doTrainingEval
    % 在测试集的每张图像上运行检测器并收集结果。
    resultsStruct = struct([]);
    for i = 1:height(testData)
        % 读取图像。
        I = imread(testData.imageFilename{i});
        % 运行检测器。
        [bboxes, scores, labels] = detect(detector, I);
        % 收集结果。
        resultsStruct(i).Boxes = bboxes;
        resultsStruct(i).Scores = scores;
        resultsStruct(i).Labels = labels;
    end
    % 将结果转换为表格。
    results = struct2table(resultsStruct);
else
    % 从磁盘加载结果。
    results = data.results;
end

% 从测试数据中提取的边界框位置。
expectedResults = testData(:, 2:end);

% 使用平均精度指标评估物体检测器。
[ap, recall, precision] = evaluateDetectionPrecision(results, expectedResults);
```

精确率/召回（PR）曲线突显了检测器在不同召回水平下的精确度。理想情况下，在所有召回水平下精度都应为 1。在这个例子中，平均精度为 0.6。





```matlab
% Plot precision/recall curve
figure
plot(recall, precision)
xlabel('Recall')
ylabel('Precision')
grid on
title(sprintf('Average Precision = %.1f', ap))
```
![Descripción: http://www.mathworks.com/help/examples/vision_product/win64/DeepLearningFasterRCNNObjectDetectionExample_03.png](img/00060.jpeg)

# 5.6 对象检测器

计算机视觉系统工具箱提供了预训练的对象检测功能以及训练自定义检测器的功能。级联对象检测器使用 Viola-Jones 算法来检测人的脸部、鼻子、眼睛、嘴巴或上半身。人物检测器使用方向梯度直方图（`HOG`）特征和训练的支持向量机（`SVM`）分类器来检测输入图像中的人物。

你可以使用[`trainCascadeObjectDetector`](http://es.mathworks.com/help/vision/ref/traincascadeobjectdetector.html) 函数来自定制级联对象检测器。你还可以使用[训练图像标记器](http://es.mathworks.com/help/vision/ref/trainingimagelabeler-app.html)、特征提取器以及统计和机器学习工具箱的分类器来创建自定义检测器。

# 5.7 训练级联对象检测器

## 5.7.1 为什么要训练检测器？

[`vision.CascadeObjectDetector`](http://es.mathworks.com/help/vision/ref/vision.cascadeobjectdetector-class.html) 系统对象带有多个用于检测正面脸、侧脸、鼻子、眼睛和上半身的预训练分类器。然而，这些分类器并不总是满足特定应用的需求。计算机视觉系统工具箱提供了[`trainCascadeObjectDetector`](http://es.mathworks.com/help/vision/ref/traincascadeobjectdetector.html) 函数来训练自定义分类器。

![Descripción: http://es.mathworks.com/help/vision/ug/traincascadeobjectdetector_overview.png](img/00061.jpeg)

## 5.7.2 你可以检测哪些类型的对象？

计算机视觉系统工具箱级联对象检测器可以检测横比变化不显著的对象类别。横比保持固定的对象包括脸、停止标志和从侧面观察的汽车。

[`vision.CascadeObjectDetector`](http://es.mathworks.com/help/vision/ref/vision.cascadeobjectdetector-class.html) 系统对象通过在图像上滑动窗口来检测图像中的对象。检测器随后使用级联分类器来判断窗口是否包含感兴趣的对象。窗口的大小会变化以检测不同比例的对象，但其横比保持固定。检测器对面外旋转非常敏感，因为大多数 3D 对象的横比会发生变化。因此，你需要为对象的每种方向训练一个检测器。训练单个检测器来处理所有方向是不行的。

## 5.7.3 级联分类器是如何工作的？

级联分类器由多个阶段组成，每个阶段都是弱学习器的集成。弱学习器是称为 `decision stumps`（决策树桩）的简单分类器。每个阶段都使用称为提升（boosting）的技术进行训练。`Boosting` 通过对弱学习器做的决策进行加权平均，提供了训练高精度分类器的能力。

分类器的每个阶段将滑动窗口当前位置定义的区域标记为正或负。`positive` 表示找到了对象，`negative` 表示未找到对象。如果标签为负，则该区域的分类完成，检测器将窗口滑动到下一个位置。如果标签为正，分类器将该区域传递到下一阶段。当最终阶段将区域分类为正时，检测器报告在当前窗口位置发现了对象。

这些阶段的设计目的是尽可能快地拒绝负样本。假设绝大多数窗口都不包含感兴趣的对象。相反，真阳性（true positives）是稀有的，值得花时间进行验证。

* `true positive`（真阳性）在正样本被正确分类时发生。
* `false positive`（假阳性）在负样本被误分类为正时发生。
* `false negative`（假阴性）在正样本被误分类为负时发生。

为了良好运行，每个阶段必须有一个假阴性率。如果检测器错误地将对象标记为正，你可以通过增加阶段来纠正错误。级联的整体误报率为 `f`，其中 `f` 是每阶段的误报率（0 1），`s` 是阶段数。同样，整体真阳性率为 `t`，其中 `t` 是每阶段的真阳性率（0 1）。

## 5.7.4 使用 trainCascadeObjectDetector 创建级联分类器

级联分类器训练需要一组正样本和一组负图像。你必须提供使用[训练图像标记器](http://es.mathworks.com/help/vision/ref/trainingimagelabeler-app.html)带有边界框的感兴趣正图像。该函数会自动生成负样本。为了达到接受接受检测器准确率，设置阶段数、特征类型和其他函数参数。

![Descripción: http://es.mathworks.com/help/vision/ug/traincascadeobjectdetector_training.png](img/00062.gif)

### 设置参数时的考虑因素

选择函数参数以优化阶段数、误报率、真阳性率和特征类型。设置参数时，请考虑这些权衡：

| 条件 | 考虑因素 |
| :--- | :--- |
| 大训练集（数千个）。 | 增加阶段数并设置较高的每阶段误报率。 |
| 小训练集。 | 减少阶段数并设置较低的每阶段误报率。 |
| 为了减少漏对象的概率。 | 提高真阳性率。然而，高真阳性率可能会阻止你达到所需的每阶段误报率，使检测器更有可能产生假检测。 |
| 为了减少假检测次数。 | 增加阶段数或降低每阶段的误报率。 |

#### 训练可用的特征类型

选择适合你所需的对象检测类型的特征。[`trainCascadeObjectDetector`](http://es.mathworks.com/help/vision/ref/traincascadeobjectdetector.html）支持三种特征：Haar、局部二进制模式（`LBP`）和方向梯度直方图（`HOG`）。Haar 和 LBP 特征经常用于检测脸部，因为它们在表示细纹理方面表现良好。HOG 特征经常用于检测行人和汽车等。它们对于捕捉对象的整体形状有用。例如，在以下 HOG 特征的可视化中，你可以看到自行车的轮廓。

![Descripción: http://es.mathworks.com/help/vision/ug/traincascadeobjectdetector_bicyclehog.png](img/00063.jpeg)





为了方便创建正样本，你可以使用[Training Image Labeler](http://es.mathworks.com/help/vision/ref/trainingimagelabeler-app.html) 应用。Training Image Labeler 提供了一种简单的方法，通过交互式指定矩形感兴趣区域（ROI）来标记正样本。

![Descripción: http://es.mathworks.com/help/vision/ug/traincascade\_labeler.png](img/00064.gif)

你也可以通过两种方式之一手动指定正样本。一种是在较大的图像中指定矩形区域，这些区域包含感兴趣的对象。另一种方法是从图像中裁剪出感兴趣的对象并将其保存为单独的图像。然后你可以将区域指定为整个图像。你还可以通过添加旋转或噪声，或改变亮度或对比度，从现有样本生成更多正样本。

### 提供负样本

负样本不是显式指定的。相反，`trainCascadeObjectDetector](http://es.mathworks.com/help/vision/ref/traincascadeobjectdetector.html) 函数会根据用户提供的、不包含感兴趣对象的负图像自动生成负样本。在训练每个新阶段之前，该函数会运行由已在负图像上训练的阶段组成的检测器。从这些图像检测到的任何对象都是假阳性，并将用作负样本。这样，级联的每个新阶段都用于纠正之前阶段所犯的错误。

![Descripción: http://es.mathworks.com/help/vision/ug/traincascadeobjectdetector\_negativeimages.png](img/00065.jpeg)

随着阶段的增加，检测器的整体误报率降低，导致负样本的生成变得困难。因此，尽可能提供负图像是有帮助的。为了提高训练准确性，请提供包含与感兴趣对象常见的背景的负图像。此外，包含外观与感兴趣对象相似的非对象的负图像。例如，如果你正在训练停止标志检测器，请包含包含与停止标志相似的道路标志牌和形状的负图像。

### 选择阶段数

在“阶段较少但每阶段误报率较低”与“阶段较多但每阶段误报率较高”之间存在着权衡。误报率较低的阶段更复杂，因为它们包含更多的弱学习器。误报率较高的阶段包含的弱学习器较少。通常，拥有较多的简单阶段更好，因为在每个阶段整体误报率呈指数级下降。例如，如果每个阶段的误报率为 50%，那么具有两个阶段的级联分类器的整体误报率为 25%。三个阶段则变为 12.5%，依此类推。然而，阶段数越多，分类器所需的训练数据就越。。此外，增加阶段数会增加假阴性率。这种增加会导致误放正样本的几增加。设置误报率（`FalseAlarmRate`）和阶段数（`NumCascadeStages`），以产生可接受的整体误报率。然后你可以通过实验来调整这两个参数。

训练有时会提前终止。例如，假设训练在七个阶段后停止，尽管你将阶段数参数设置为 20。这可能是因为函数无法生成足够的样本。用于训练每个阶段的正样本数量取决于阶段的数量。

### 检测器的训练时间

训练一个良好的检测器需要数千个样本。在训练期间，函数会显示所需的时间。训练时间取决于你指定的特征类型。使用 Haar 特征比使用 LBP 或 HOG 特征耗长得多。

### 5.7.5 故障排除

#### 如果正样本用尽了怎么办？

`trainCascadeObjectDetector](http://es.mathworks.com/help/vision/ref/traincascadeobjectdetector.html)` 函数根据 `TruePositiveRate` 和 `NumCascadeStages` 自动确定每个阶段训练的正样本数量。

该率指定了函数可以将多少比例的正样本分类为负样本。函数永远达到阶段。例如，假设你设置 `TruePositiveRate` 为 0.9，所有的正样本都用于训练第一阶段。在这种情况下，10% 的正样本被拒绝为负样本，只有 90% 可用于第二阶段。如果训练继续，则每个阶段的样本将越来越少。随着每个阶段获得的样本越少，后期阶段可能会过拟合数据。

理想情况下，使用相同数量的样本训练每个阶段。为此，训练每个阶段的正样本数必须小于总正样本数。唯一的例外是 `TruePositiveRate` 的值乘以总正样本小于 1，此时没有正样本被拒绝为负样本。

函数使用以下公式计算每个阶段使用的正样本数量：

```
number of positive samples = floor(http://es.mathworks.com/help/matlab/ref/floor.html)(totalPositiveSamples / (1 + NumCascadeStages - 1) * (1 - TruePositiveRate))
```

此计算不能保证每个阶段都有相同数量的正样本可用。原因是无法确定地预测有多少正样本会被拒绝为负样本。只要用于训练阶段的可用正样本数量大于函数使用上述公式确定的样本数量的 10%，训练就会继续。如果没有足够的正样本，训练将停止，函数会发出警告。函数还会输出一个由到目前为止已训练的阶段组成的分类器。如果训练停止，你可以添加更多正样本。或者，你可以增加 `TruePositiveRate`。减少阶段数也可以，但这种减少可能导致整体误报率升高。

#### 如果负样本用尽了怎么办？

函数计算每个阶段使用的负样本数量。此计算通过将每个阶段使用的正样本数量乘以 `NegativeSamplesFactor` 的值来完成。

与正样本一样，无法保证计算出的负样本数量始终适用于特定阶段。`trainCascadeObjectDetector` 函数从负图像生成负样本。然而，随着每个新阶段的出现，级联分类器的整体误报率降低，找到负样本的可能性也会降低。




只要用于训练阶段的可用负样本数量大于计算出的负样本数量的 10%，训练就会继续。如果负样本不足，训练将停止，函数会发出警告。它将输出一个由目前为止训练的阶段组成的分类器。当训练停止时，最好的方法是增加负图像。或者，你可以减少阶段数量或增加假阳性率。

## 5.7.6 示例

### 训练一个五阶段停止标志检测器

此示例演示了如何使用 86 个正样本设置并训练一个五阶段的停止标志检测器。`TruePositiveRate` 的默认值为 `0.995`。

**步骤 1**：从 MAT 文件加载正样本数据。在此示例中，文件名和边界框包含标记为 `'data'` 的结构体数组。

```matlab
load('stopSigns.mat');
```

**步骤 2**：将图像目录添加到 MATLAB 路径。

```matlab
imDir = fullfile(matlabroot,'toolbox','vision','visiondata','stopSignImages');
addpath(imDir);
```

**步骤 3**：指定包含负图像的文件夹。

```matlab
negativeFolder = fullfile(matlabroot,'toolbox','vision','visiondata','nonStopSigns');
```

**步骤 4**：训练检测器。

```matlab
trainCascadeObjectDetector('stopSignDetector.xml',data,negativeFolder,'FalseAlarmRate',0.2,'NumCascadeStages',5);
```

Computer Vision System Toolbox 软件返回以下消息：

![Descripción: http://es.mathworks.com/help/vision/ug/train_cascade_output.jpg](img/00066.jpeg)

所有 86 个正样本均用于训练每个阶段。出现这种高率的原因是相对于正样本数量而言，真阳性率非常高。

### [使用降低真阳性率训练五阶段停止标志检测器](http://es.mathworks.com/help/vision/ug/train-a-cascade-object-detector.html)

此示例演示了如何在与第一个示例相同的数据（步骤 1–3）上训练停止标志检测器，但将 `TruePositiveRate` 降低到 0.98。

**步骤 4**：训练检测器。

```matlab
trainCascadeObjectDetector('stopSignDetector_tpr0_98.xml',data,negativeFolder,...
'FalseAlarmRate',0.2,'NumCascadeStages', 5,...
'TruePositiveRate', 0.98);
```

![Descripción: http://es.mathworks.com/help/vision/ug/traincascadeobjectdetector_example2.png](img/00067.jpeg)

总 86 个正样本中仅使用了 79 个来训练每个阶段。该率降低的原因是真阳性率足够低，函数开始将某些正样本作为假阴性剔除。

### [训练一个十阶段停止标志检测器](http://es.mathworks.com/help/vision/ug/train-a-cascade-object-detector.html)

此示例演示了如何在与第一个示例相同的数据（步骤 1–3）上训练停止标志检测器，但阶段数量增加到 10。

**步骤 4**：训练检测器。

```matlab
trainCascadeObjectDetector('stopSignDetector_10.xml',data,negativeFolder,...
'FalseAlarmRate',0.2,'NumCascadeStages',10);
```

![Descripción: http://es.mathworks.com/help/vision/ug/traincascadeobjectdetector_example3.png](img/00068.jpeg)

在这种情况下，`NegativeSamplesFactor` 被设置为 2，因此用于训练阶段的负样本数量为 17。注意，函数只生成了 6 个阶段而不是 10 个，因为总告警率已达到 0.5 的阈值。此时，你可以添加更多负图像、减少阶段数量或增加假阳性率。

```matlab
trainCascadeObjectDetector('stopSignDetector_10.xml',data,negativeFolder,...
'FalseAlarmRate',0.5);
```

![Descripción: http://es.mathworks.com/help/vision/ug/traincascadeobjectdetector_example4.png](img/00069.jpeg)

这次函数函数训练了 6 个阶段，因为负样本数量少于 17。

### 5.7.7 训练停止检测器

加载正样本。

```matlab
load('stopSigns.mat');
```

从表中选择停止标志的边界框。该表是从 Labeler 应用程序导出的。

将图像目录添加到 MATLAB 路径。

```matlab
imDir = fullfile(matlabroot,'toolbox','vision','visiondata','stopSignImages');
addpath(imDir);
```

指定负图像的文件夹。

```matlab
negativeFolder = fullfile(matlabroot,'toolbox','vision','visiondata','nonStopSigns');
```

创建一个包含负图像的 imageastore 对象。

```matlab
negativeImages = imageastore(negativeFolder);
```

使用 HOG 特征训练名为 'stopSignDetector.xml' 的级联对象。注意：该命令可能运行几分钟。

```matlab
trainCascadeObjectDetector('stopSignDetector.xml',positiveInstances, ...
negativeFolder,'FalseAlarmRate',0.1,'NumCascadeStages',5);
```

自动将 `ObjectTrainingSize` 设置为 `[35, 32]`

每个阶段最多使用 42/42 个正样本

每个阶段最多使用 84 个负样本

--cascadeParams--

正在训练第 1/5 阶段
........................................................................
使用了 42 个正样本和 84 个负样本
训练第 1 阶段耗时：0 秒

正在训练第 2/5 阶段
........................................................................
使用了 42 个正样本和 84 个负样本
训练第 2 阶段耗时：0 秒

正在训练第 3/5 阶段
........................................................................
使用了 42 个正样本和 84 个负样本
训练第 3 阶段耗时：2 秒

正在训练第 4/5 阶段
........................................................................
使用了 42 个正样本和 84 个负样本
训练第 4 阶段耗时：5 秒

正在训练第 5/5 阶段
........................................................................
使用了 42 个正样本和 17 个负样本
训练第 5 阶段耗时：9 秒

训练完成

使用新训练的分类器在图像中检测停止标志。

```matlab
detector = vision.CascadeObjectDetector('stopSignDetector.xml');
```

读取测试图像。

```matlab
img = imread('stopSignTest.jpg');
```

检测停止标志。

```matlab
bbox = step(detector,img);
```

插入边界框矩形并返回标记后的图像。

```matlab
detectedImg = insertObjectAnnotation(img,'rectangle',bbox,'stop sign');
```

显示检测到的停止标志。

```matlab
figure; imshow(detectedImg);
```

![Descripción: http://es.mathworks.com/help/examples/vision/win64/TrainAStopSignDetectorExample_01.png](img/00070.jpeg)

从路径移除图像目录。

```matlab
rmpath(imDir);
```

## 5.8 使用视觉袋进行图像检索

可以使用 Computer Vision Toolbox 函数进行图像搜索，也称为基于内容的图像检索（CBIR）系统。CBIR 系统用于从图像集中检索相似图像。此类系统的应用于许多领域，例如基于网络的产品搜索、监控和视觉位置识别。首先，系统在图像集中搜索与查询图像视觉上相似的图像。




检索系统使用视觉词袋（bag of visual words，即图像描述符的集合）来表示你的图像数据集。对图像进行索引以创建视觉词的映射。该索引将每个视觉词映射到它们在图像集中出现的次数。查询图像与索引之间的比较，可以提供与查询图像最相似的图像。通过使用 CBIR 系统工作流，你可以评估已知图像搜索结果的准确性。

![描述: http://es.mathworks.com/help/vision/ug/image_retrieval.png](img/00071.jpeg)

## 5.8.1 检索系统工作流

1. **创建代表检索图像特征的图像集**。使用[`imageDatastore`](http://es.mathworks.com/help/matlab/ref/imagedatastore.html) 存储图像数据。使用大量代表物体不同视角的图像。大量且多样化的图像有助于训练视觉词袋，并提高图像搜索的准确性。

2. **特征类型**。[`indexImages`](http://es.mathworks.com/help/vision/ref/indeximages.html) 函数使用加速稳棒特征 (SURF) 创建视觉词袋。对于其他类型的特征，你可以使用自定义提取器，然后使用[`bagOfFeatures`](http://es.mathworks.com/help/vision/ref/bagoffeatures-class.html) 创建视觉词袋。

你可以使用原始的 `imgSet` 或不同的图像集合作为训练集。要使用不同的集合，请在创建图像索引之前，使用[`bagOfFeatures`](http://es.mathworks.com/help/vision/ref/bagoffeatures-class.html) 函数创建视觉词袋。使用相同图像集的优点是视觉词汇表是针对搜索集定制的。此这种方法的缺点是，检索系统必须重新学习视觉词汇表，以便用于差异巨大的图像集。使用独立集合，视觉词汇表能够更好地处理新图像添加到搜索索引中。

3. **对图像索引**。[`indexImages`](http://es.mathworks.com/help/vision/ref/indeximages.html) 函数创建一个搜索索引，将视觉词映射到它们在图像集合中出现的次数。当你使用独立集合或子集创建视觉词袋时，请将 `bag` 作为输入参数传递给 `indexImages`。如果你没有创建独立的视觉词袋，则函数将根据整个 `imgSet` 输入集合创建词袋。你可以使用[`addImages`](http://es.mathworks.com/help/vision/ref/invertedimageindex.addimages.html) 和[`removeImages`](http://es.mathworks.com/help/vision/ref/invertedimageindex.removeimages.html) 方法直接在图像索引中添加或删除图像。

4. **搜索数据集中的相似图像**。使用[`retrieveImages`](http://es.mathworks.com/help/vision/ref/retrieveimages.html) 函数在图像集中搜索与查询图像相似的图像。使用 `NumResults` 属性控制结果数量。例如，要返回前 10 张相似图像，请设置 `ROI` 属性以使用查询图像的较小区域。较小区域对于从你想搜索的图像中隔离特定物体有用。

## 5.8.2 评估图像检索

使用[`evaluateImageRetrieval`](http://es.mathworks.com/help/vision/ref/evaluateimageretrieval.html) 函数通过带有已知结果集的查询图像来评估图像检索。如果结果不符合你的预期，你可以通过视觉词袋修改或增强图像特征。检查检索到的特征的类型。用于检索的特征类型取决于集合中图像的类型。例如，如果集合中是海滩或公路，则使用全局图像特征。全局图像特征捕捉整个场景。要找到图像中的特定物体，请使用局部特征。

# 5.9 使用视觉词袋进行分类

通过创建视觉词袋，使用 Computer Vision Toolbox 函数进行图像分类。这些直方图被用于训练图像分类器。以下步骤描述了如何设置图像、创建视觉词袋，然后应用图像分类器。

## 5.9.1 第一步：设置图像类别

组织并将图像分为训练和测试子集。使用[`imageastore`](http://es.mathworks.com/help/imageastore.html) 函数来存储用于训练的图像。将图像组织成类别使得处理大量集合变得容易。你可以使用[`splitLabel`](http://es.mathworks.com/help/datastore.splitachlabel.html) 函数分割每个标签。读取类别图像并创建集合。

```matlab
setDir = fullfile(toolboxdir('vision'),'imagedata');
imds = imageastore(setDir,'Includefolders',true,'LabelSource','filenames');
```

将集合分为训练和测试。在示例中，30%的图像被划分为测试集。

```matlab
[trainingSet,testSet] = splitLabel(imds,0.3,'randomize');
```

![描述: http://es.mathworks.com/help/vision/ug/bagoffeatures_images.png](img/00072.jpeg)

## 5.9.2 第二步：创建特征袋

通过从每个类别的代表性图像中提取描述符来创建一个视觉词汇表或特征袋。

[`bagOfFeatures`](http://es.mathworks.com/help/vision/ref/bagoffeatures-class.html) 对象通过对特征描述符使用[`k-means clustering`](http://es.mathworks.com/help/stats/k-means-clustering.html#bq_679x-1)算法定义特征或视觉词。该算法迭代将描述符分组为互斥的类。每个类中心代表一个特征。

你可以根据特征检测器提取特征，也可以定义一个网格来提取特征描述符。网格方法可能会丢失细粒度的尺度信息。因此，对于不包含明显特征的图像（如海滩），使用网格。使用加速稳棒特征（SURF）检测器提供了更大的尺度不变性。默认情况下，算法运行 `'grid'` 方法。

![描述: http://es.mathworks.com/help/vision/ug/bagoffeatures_visualwordsoverview.png](img/00073.jpeg)

此算法工作流分析整个图像。图像具有描述其所属类的相应标签。例如，一组汽车图像可以标记为汽车。该工作流不依赖于空间信息，也不依赖于标记图像中的特定物体。视觉词袋技术依赖于检测而非定位。

## 5.9.3 第三步：使用视觉词袋训练图像分类器

[`trainImageCategoryClassifier`](http://es.mathworks.com/help/vision/ref/trainimagecategoryclassifier.html) 使用误差输出代码（ECOC）框架和二进制支持向量机（SVM）分类器训练多图像分类器。`trainImageCategoryClassifier` 函数使用[`bagOfFeatures`](http://es.mathworks.com/help/vision/ref/bagoffeatures-class.html) 对象返回的视觉词袋将图像集中的图像编码为视觉词直方图。然后这些视觉词直方图被用作正、负样本来训练分类器。




1. 使用 [bagOfFeatures](http://es.mathworks.com/help/vision/ref/bagoffeatures-class.html) `encode` 方法对训练集中的每幅图像进行编码。该函数检测并提取图像中的特征，然后使用近似近邻算法为每幅图像构建特征直方图。该函数根据描述符与特定聚类中心的距离增加直方图箱计数。直方图的长度对应于 [bagOfFeatures](http://es.mathworks.com/help/vision/ref/bagoffeatures-class.html) 对象构建的视觉单词数量。直方图变为图像的特征向量。

![描述: http://es.mathworks.com/help/vision/ug/bagoffeatures\_encodeoverview.png](img/00074.jpeg)

2. 对训练集中的每幅图像重复步骤 1 以创建训练数据。

![描述: http://es.mathworks.com/help/vision/ug/bagoffeatures\_bofclassify.png](img/00075.jpeg)

3. 评估分类器的质量。使用 [imageCategoryClassifier](http://es.mathworks.com/help/vision/ref/imagecategoryclassifier-class.html) `evaluate` 方法针对验证图像集测试分类器。输出的混淆矩阵表示对预测的分析。完美的分类产生一个对角线为 1 的归一化矩阵。错误的分类产生小数值。

![描述: http://es.mathworks.com/help/vision/ug/bagoffeatures\_bofevaluate.png](img/00076.jpeg)

## 5.9.4 步骤 4：对图像或图像集分类

对新图像使用 [imageCategoryClassifier](http://es.mathworks.com/help/vision/ref/imagecategoryclassifier-class.html) `predict` 方法确定其类别。

# 5.10 使用 HOG 特征进行数字分类

此示例展示了如何使用 HOG 特征和多分类 SVM 分类器对数字进行分类。

物体分类是许多计算机视觉应用中的重要任务，包括监控、汽车安全和图像检索。例如，在汽车安全应用中，可能需要将周围的物体分类为行人或车辆。无论分类的类型类型，创建物体分类器的基本步骤是：

* 获取一个带有目标物体图像的标记数据集。
* 将数据集划分为训练集和测试集。
* 使用从训练集中提取的特征训练分类器。
* 使用从测试集中提取的特征测试分类器。

为了说明这一点，此示例展示了如何使用 HOG（方向梯度直方图）特征 [1]  和多分类 SVM（支持向量机）分类器对数值数字进行分类。这种分类通常用于许多光学字符识别 (OCR) 应用。

该示例使用了 Statistics and Machine Learning Toolbox™ 中的 `fitcecoc` 函数以及 Computer Vision System Toolbox™ 中的 `extractHOGFeatures` 函数。

## 5.10.1 数字数据集

使用合成数字图像进行训练。训练图像包含一个被其他数字包围的数字，模拟了数字在一起出现的情况。使用合成图像非常方便，无需手动收集各种训练样本。对于测试，使用手写数字扫描来验证分类器对不同于训练数据的性能。虽然这不是代表性数据集，但有足够的数据来训练和测试分类器，并展示该方法的可行性。

% 使用 `imageastore` 加载并测试数据
```matlab
syntheticDir = fullfile('vision','data','synthetic');
handwrittenDir = fullfile('vision','data','handwritten');
% imageastore 递归扫描包含图像的文件夹。文件夹名自动作为每幅图像的标签。
trainingSet = imageastore(syntheticDir, 'IncludeFolders', true, 'LabelSource', 'filenames');
testSet = imageastore(handwrittenDir, 'IncludeFolders', true, 'filenames');
```

使用 `countLabel` 统计每个标签对应的图像数量。在本示例中，训练集每个数字有 101 幅图像。测试集每个数字有 12 幅图像。

```matlab
countLabel(trainingSet)
ans = 10x2 table
    Label    Count
    ____    ____
      0      101
      1      101
      2      101
      3      101
      4      101
      5      101
      6      101
      7      101
      8      101
      9      101

countLabel(testSet)
ans = 10x2 table
    Label    Count
    ____    ____
      0      12
      1      12
      2      12
      3      12
      4      12
      5      12
      6      12
      7      12
      8      12
      9      12
```

显示一些训练图像和测试图像
```matlab
figure;
subplot(2,3,1);
imshow(trainingSet.Files{10});
subplot(2,3,2);
imshow(trainingSet.Files{4});
subplot(2,3,3);
imshow(trainingSet.Files{9});
subplot(2,3,4);
imshow(testSet.Files{1});
subplot(2,3,5);
imshow(testSet.Files{7});
subplot(2,3,6);
imshow(testSet.Files{9});
```
![描述: http://es.mathworks.com/help/examples/vision\_product/win64/HOGDigitClassificationExample\_01.png](img/00077.jpeg)

在训练和测试分类器之前，应用了预处理步骤来消除收集图像样本时引入的噪声。这为训练分类器提供了更好的特征向量。

% 显示预处理结果
```matlab
exTestImage = readimage(testSet,3);
processedImage = imbinarize(rgb2gray(exTestImage));
figure;
subplot(1,2,1)
imshow(exTestImage)
subplot(1,2,2)
imshow(processedImage)
```
![](img/00078.jpeg)

## 5.10.2 使用 HOG 特征

训练分类器的数据是从训练图像提取的 HOG 特征。因此，确保 HOG 特征编码了关于物体的正确信息是非常重要的。`extractHOGFeatures` 函数的可可视化输出有助于理解什么是“正确的信息”。通过改变 HOG 网格大小并可视化结果，你可以看到网格大小参数对特征向量中编码形状信息量的影响：

```matlab
img = readimage(trainingSet,6);
% 提取 HOG 特征和 HOG 可视化
[hog2x2, vis2x2] = extractHOGFeatures(img,'CellSize',2 2);
[hog4x4, vis4x4] = extractHOGFeatures(img,'CellSize',4 4);
[hog8x8, vis8x8] = extractHOGFeatures(img,'CellSize',8 8);

% 显示原始图像
figure;
subplot(2,3,1:3); imshow(img);
% 可视化 HOG 特征
subplot(2,3,4);
plot(vis2x2);
title({'CellSize = [2 2]'; ['Length = ' num2str(length(hog2x2))});
subplot(2,3,5);
plot(vis4x4);
title({'CellSize = [4 4]'; ['Length = ' num2str(length(hog4x4))});
subplot(2,3,6);
plot(vis8x8);
title({'CellSize = [8 8]'; 'Length = ' num2str(length(hog8x8))});
```
![描述: http://es.mathworks.com/help/examples/vision\_product/win64/HOGDigitClassificationExample\_03.png

可视化显示，[8 8] 的网格大小没有编码多少形状信息，而 [2 2] 的网格大小编码了大量的形状信息，但显著增加了 HOG 特征向量的维度。一个很好的折中方案是 4x4 的网格大小。这种设置编码了足够的空间信息来视觉识别数字形状，同时限制了 HOG 特征向量的维度，有助于加速训练。在实践中，应该通过反复训练和测试分类器来改变 HOG 参数，以确定最佳参数设置。

```matlab
cellSize = [4 4];
```





`hogFeatureSize = length(hog_4x4);`

## 5.10.3 训练数字分类器

数字分类是一个多分类问题，你必须将图像分类为十个可能的数字类别中的一个。在本示例中，使用了 Statistics and Machine Learning Toolbox™ 中的 `fitcecoc` 函数，利用二分类 SVM 创建多分类分类器。

首先从训练集中提取 HOG 特征。这些特征将用于用于训练分类器。

```matlab
% 遍历 trainingSet 并从每张图像中提取 HOG 特征。
% 相似的步骤将用于从 testSet 中提取特征。

numImages = numel(trainingSet.Files);
trainingFeatures = zeros(numImages, hogFeatureSize, 'single');

for i = 1:numImages
    img = readimage(trainingSet, i);
    img = rgb2gray(img);
    % 应用预处理步骤
    img = imbinarize(img);
    trainingFeatures(i, :) = extractHOGFeatures(img, 'CellSize', cellSize);
end

% 获取每个图像的标签。
trainingLabels = trainingSet.Labels;
```

接下来，使用提取的特征训练分类器。

```matlab
% fitcecoc 使用 SVM 学习器和“对一”（One-vs-One）编码方案。
classifier = fitcecoc(trainingFeatures, trainingLabels);
```

## 5.10.4 评估数字分类器

使用测试集中的图像评估数字分类器，并生成混淆矩阵以量化分类器的准确率。

与训练步骤一样，首先从测试图像中提取 HOG 特征。这些特征将用于使用训练好的分类器进行预测。

```matlab
% 从测试集提取 HOG 特征。该过程与之前显示的相似，
% 为了简洁起见，将其封装为一个辅助函数。

[testFeatures, testLabels] = helperExtractHOGFeaturesFromImageSet(testSet, hogFeatureSize, cellSize);

% 使用测试特征进行类别预测。
predictedLabels = predict(classifier, testFeatures);

% 使用混淆矩阵汇总结果。
confMat = confusionmat(testLabels, predictedLabels);
helperDisplayConfusionMatrix(confMat)
```

digit | 0       1       2       3       4       5       6       7       8       9       
---------------------------------------------------------------------------------------------------
0     | 0.25    0.00    0.08    0.00    0.00    0.00    0.58    0.00    0.08    0.00    
1     | 0.00    0.75    0.00    0.00    0.08    0.00    0.00    0.08    0.08    0.00    
2     | 0.00    0.00    0.67    0.17    0.00    0.00    0.08    0.00    0.00    0.08    
3     | 0.00    0.00    0.00    0.58    0.00    0.00    0.33    0.00    0.00    0.08    
4     | 0.00    0.08    0.00    0.17    0.75    0.00    0.00    0.00    0.00    0.00    
5     | 0.00    0.00    0.00    0.00    0.00    0.33    0.58    0.00    0.08    0.00    
6     | 0.00    0.00    0.00    0.00    0.25    0.00    0.67    0.00    0.08    0.00    
7     | 0.00    0.08    0.08    0.33    0.00    0.00    0.17    0.25    0.00    0.08    
8     | 0.00    0.00    0.00    0.08    0.00    0.00    0.00    0.08    0.67    0.17    
9     | 0.00    0.08    0.00    0.25    0.17    0.00    0.08    0.00    0.00    0.42    

该表格以百分比形式显示混淆矩阵。矩阵的列表示预测标签，行表示已知标签。对于此测试集，数字 0 经常被误分类为 6，这很可能是因为它们的形状相似。9 和 3 也有类似的错误。使用更具代表性的数据集（如 MNIST [2] 或 SVHN [3]，它们包含数千个手写字符）进行训练，与使用此数据集创建的分类器相比可能会产生更好的。

## 5.10.5 总结

本示例说明了如何使用 Computer Vision Toolbox 中的 `extractHOGfeatures` 函数和 Statistics and Machine Learning Toolbox™ 中的 `fitcecoc` 函数创建多分类对象分类器的基本步骤。尽管这里使用了 HOG 特征和 ECOC 分类器，但也可以同样地使用其他特征和机器学习算法。例如，你可以探索使用不同的特征类型来训练分类器；或者查看使用 Statistics and Machine Learning Toolbox™ 中提供的其他机器学习算法（如 k-最近邻）的效果。

## 5.11 使用特征包进行图像分类

本示例展示了如何使用特征包（bag of features）方法进行图像类别分类。这种技术通常称为词袋（bag of words）。视觉图像分类是为测试图像分配类别标签的过程。类别可能包含代表几乎任何内容的图像，例如狗、猫、火车、船。

## 5.11.1 下载 Caltech101 图像集

为了学习特征包图像类别分类，你首先需要下载一个合适的图像数据集。最广泛引用和使用的数据之一是 Caltech 101(http://www.vision.caltech.edu/Image_Datasets/Caltech101)，由 Fei-Fei Li、Marco Andreetto 和 Marc Ranzato 收集。

```matlab
% 数据集的位置
url = 'http://www.vision.caltech.edu/Image_Datasets/Caltech101/101_ObjectCategories.tar.gz';

% 将输出存储在临时文件夹
outputFolder = fullfile(tempdir, 'caltech01');

% 检查文件夹是否存在，若不存在则下载
if ~exist(outputFolder, 'dir')
    disp('Downloading Caltech101 data...');
    untar(url, outputFolder);
end
```

## 5.11.2 加载图像集

与其操作整个 Caltech 101 集（这可能耗时），不如使用三个类别：飞机、船和笔记本。注意，为了使特征包方法有效，图像大部分由类别主体占据，例如某个物体或场景类型。

```matlab
rootFolder = fullfile(outputFolder, '101_ObjectCategories');
categories = {'airplanes', 'ferry', 'laptop'};
imds = imageDatastore(fullfile(rootFolder, categories), 'LabelSource', 'foldern');
```

你可以轻松地查看每个类别的图像数量以及所示类别标签：

```matlab
tbl = countEachLabel(imds)
tbl =
  3×2 table
    Label          Count
    airplanes      800
    ferry           67
    laptop          81
```

## 5.11.3 准备训练和验证图像集

由于 `imds` 中每个类别的图像数量不相等，让我们先调整它，使训练集中的图像数量保持平衡。

```matlab
% 确定类别中最小的图像数量
minSetCount = min(tbl{:,2});

% 使用 splitEachLabel 方法修剪集合。
imds = splitEachLabel(imds, minSetCount, 'randomize');

% 注意现在每个集合都有相同数量的图像。
countEachLabel(imds)
ans =
  3×2 table
    Label          Count
    airplanes      67
    ferry           67
    laptop          67
```



将数据集划分为训练数据和验证数据。从每个数据集中选取 30% 的图像作为训练数据，剩余的 70% 留验证数据。随机化划分以避免结果产生偏差。

```matlab
[trainingSet, validationSet] = splitEachLabel(imds, 0.3, 'randomize');
```

上述调用返回两个准备用于训练和验证任务的 `imageDatastore` 对象。在下方，你可以看到训练数据中包含的三个类别的示例图像。

```matlab
% 每个类别的第一个图像实例

airplanes = find(trainingSet.Labels == 'airplanes', 1);

ferry = find(trainingSet.Labels == 'ferry', 1);

laptop = find(trainingSet.Labels == 'laptop', 1);

% figure

subplot(1,3,1);

imshow(readimage(trainingSet,airplanes))

subplot(1,3,2);

imshow(readimage(trainingSet,ferry))

subplot(1,3,3);

imshow(readimage(trainingSet,laptop))
```
![](img/00080.jpeg)

## 5.11.4 创建视觉词汇并训练图像类别分类器

词袋（Bag of words）是一种从自然语言处理领域引入到计算机视觉的技术。由于图像实际上并不包含离散的单词，我们首先构建一个代表每个图像类别的 `SURF` 特征的“词汇表”。

通过通过一次 `bagOfFeatures` 函数实现，该函数会：

1. 从所有图像类别中的所有图像中提取 `SURF` 特征
2. 通过使用 `K-means` 聚类对特征空间进行量化以减少特征数量，从而构建视觉词汇

```matlab
bag = bagOfFeatures(trainingSet);
```
创建特征袋。

* 图像类别 1：飞机 (airplanes)
* 图像类别 2：渡轮 (ferry)
* 图像类别 3：笔记本电脑 (laptop)
* 使用 `Grid` 方法选择特征点位置。
* 从选定的特征点位置提取 `SURF` 特征。
* `GridStep` 为 `[8 8]`，`BlockWidth` 为 `[32 64 96 128]`。
* 正在从 60 张图像中提取特征...完成。提取了 247480 个特征。
* 保留每个类别中最强的 80% 特征。
* 平衡所有图像类别的特征数量以改进聚类效果。
* 类别 2 的强特征数量最少：58003。
* 使用其他图像类别中最强的 58003 个特征。
* 使用 `K-Means` 聚类创建一个包含 500 个词的视觉词汇。
* 特征数量：174009
* 聚类数 (K)：500
* 正在初始化类中心...100.00%。
* 聚类中...完成 39/100 次迭代 (~ 0.41 秒/迭代)...在 39 次迭代后收敛。
* 完成创建特征袋

此外，`bagOfFeatures` 对象提供了 `encode` 方法来计算图像中视觉单词的出现次数。它生成了一个直方图，作为图像的一种新的且压缩的表示。

```matlab
img = readimage(imds, 1);

featureVector = encode(bag, img);

% 绘制视觉单词出现次数的直方图

figure

bar(featureVector)

title('Visual word occurrences')

xlabel('Visual word index')

ylabel('Frequency of occurrence')
```
![Descripción: http://es.mathworks.com/help/examples/vision_product/win64/ImageCategoryClassificationExample_02.png](img/00081.jpeg)

该直方图为训练分类器和实际图像分类提供了基础。本质上，它将图像编码为特征向量。

每个类别的编码训练图像被送入由 `trainImageCategoryClassifier` 函数调用的分类器训练过程。注意，该函数依赖于 Statistics and Machine Learning Toolbox™ 中的多类线性 SVM 分类器。

```matlab
categoryClassifier = trainImageCategoryClassifier(trainingSet, bag);
```
为 3 个类别训练图像类别分类器。

* 类别 1：飞机 (airplanes)
* 类别 2：渡轮 (ferry)
* 类别 3：笔记本电脑 (laptop)
* 正在对 60 张图像进行特征编码...完成。
* 完成类别分类器的训练。使用 `evaluate` 在测试集上测试分类器。

上述函数利用输入对象 `bag` 的 `encode` 方法来构建表示来自 `trainingSet` 中每个图像类别的特征向量。

## 5.11.5 评估分类器性能

现在我们有了一个训练好的分类器 `categoryClassifier`，让我们对其进行评估。作为合理检查，我们首先用训练集进行测试，这应该产生近乎完美的混淆矩阵，即对角线上为 1。

```matlab
confMatrix = evaluate(categoryClassifier, trainingSet);
```
评估 3 个类别的分类器。

* 类别 1：飞机 (airplanes)
* 类别 2：渡轮 (ferry)
* 类别 3：笔记本电脑 (laptop)
* 正在评估 60 张图像...完成。
* 完成所有测试集的评估。
* 该测试集的混淆矩阵如下：

```
                   PREDICTED
KNOWN      | airplanes  ferry  laptop
--------------------------------------------
airplanes    | 0.95       0.05      0.00     
ferry        | 0.00       1.00      0.00     
laptop       | 0.05       0.00      0.95     
```
* 平均准确率为 0.97。

接下来，让我们在训练期间未使用的 `validationSet` 上评估分类器。默认情况下，`evaluate` 返回混淆矩阵，这是衡量分类器性能的良好指标。

```matlab
confMatrix = evaluate(categoryClassifier, validationSet);

% 计算平均准确率
mean(diag(confMatrix));
```
* 类别 1：飞机 (airplanes)
* 类别 2：渡轮 (ferry)
* 类别 3：笔记本电脑 (laptop)
* 正在评估 141 张图像...完成。
* 完成所有测试集的评估。
* 该测试集的混淆矩阵如下：

```
                   PREDICTED
KNOWN      | airplanes  ferry  laptop
--------------------------------------------
airplanes    | 0.83       0.13      0.04     
ferry        | 0.02       0.98      0.00     
laptop       | 0.04       0.00      0.96     
```
* 平均准确率为 0.92。

可以使用 `evaluate` 返回的其他参数获取额外统计信息。参见 `imageCategoryClassifier/evaluate` 帮助。你可以调整各种参数并继续评估分类器，直到对结果满意。

## 5.11.6 在测试图像上尝试新分类器

现在你可以使用新训练的分类器对新图像进行分类。

```matlab
img = imread(fullfile(rootFolder, 'airplanes', 'image_0690.jpg'));

[labelIdx, scores] = predict(categoryClassifier, img);

% 显示字符串标签
categoryClassifier.Labels(labelIdx)
```
ans =
  cell
    'airplanes'

# 5.12 使用自定义特征袋进行图像检索

本示例展示了如何使用自定义特征袋工作流创建基于内容的图像检索（CBIR）系统。

## 5.12.1 引言

基于内容的图像检索系统用于寻找与查询图像视觉相似的图像。CBIR 系统的应用可见许多领域，例如基于 Web 的产品搜索、监控和视觉位置识别。实现 CBIR 系统的的一种常用技术是视觉词袋，也称为特征袋[1,2]。特征袋使用了一种从文档检索领域引入到图像检索的技术。与文档检索中使用实际单词不同，特征袋使用图像特征作为描述图像的视觉单词。




图像特征是基于内容的图像检索（CBIR）系统的重要部分。这些图像特征用于衡量图像之间的相似性，包括全局图像特征，如颜色、纹理和形状。图像特征也可以是局部图像特征，例如加速稳健特征 (`SURF`)、梯度直方图 (`HOG`) 或局部二值模式 (`LBP`)。特征袋模型（bag-of-features）方法的优势在于，用于创建视觉单词词汇的特征类型可以根据应用进行定制，以适应不同的场景。

图像搜索的速度和效率在 CBIR 系统中同样重要。例如，在少于 100 张图像的小型集合中，执行暴力搜索可能是可以接受的，此时会将查询图像的特征与集合中每张图像的特征进行比较。对于较大的集合，暴力搜索是不可行的，必须使用更高效的搜索技术。特征袋提供了一种简洁的编码方案，通过稀疏的视觉单词直方图来表示大量的图像集合。这使得通过倒排索引数据结构实现紧凑存储和高效搜索。

计算机视觉系统工具箱™ 提供了一个可自定义的特征袋框架，用于实现图像检索系统。以下步骤概述了操作流程：

1. 选择用于检索的图像特征
2. 创建特征袋
3. 为图像建立索引
4. 搜索相似图像

在本示例中，你将通过这些步骤创建一个用于搜索第 17 类花卉数据集 [3] 的图像检索系统。该数据集包含约 1300 张 17 种不同类型的花的图像。

下载此数据集以供示例的后续部分使用。

```matlab
% 压缩数据集的路径
url = 'http://www.robots.ox.ac.uk/~vgg/data/flowers/17/17flowers.tgz';

% 将输出存储在临时文件夹中
outputFolder = fullfile(tempdir, '17Flowers'); % 定义输出文件夹
```

注意，取决于您的互联网连接情况，从网络下载数据集可能需要很长时间。下面的命令将在在此期间阻塞 MATLAB。或者，你也可以使用网络浏览器先将该集下载到本地磁盘。如果你选择该路径，请将上述 `url` 变量重新指向你下载的文件。

```matlab
if ~exist(outputFolder, 'dir') % 仅下载一次
    disp('正在下载 17 类花卉数据集 (58 MB)...');
    untar(url, outputFolder);
end

flowerImageSet = imageDatastore(fullfile(outputFolder,'jpg'),'LabelSource','foldernames');

% 数据集中的图像总数
numel(flowerImageSet.Files)
```
`ans` = 1360

## 5.12.2 第 1 步 - 选择用于检索的图像特征

用于检索的特征类型取决于集合中图像的类型。例如，如果搜索由场景（海滩、城市、高速公路）组成的图像集合，最好使用全局图像，例如能够捕获整个场景颜色内容的颜色直方图。然而，如果目标是找到图像中的特定对象，那么在关键点周围提取的局部图像特征是更好的选择。让我们先查看几张图像，以便对如何处理该问题有一个直观的。

```matlab
% 显示几张花卉图像
helperImageMontage(flowerImageSet.Files(1:50:1000));
```
![Descripción: http://es.mathworks.com/help/examples/vision_product/win64/ImageRetrieval_01.png](img/0082.jpeg)

在本示例中，目标是通过使用查询图像中的颜色信息在数据集中搜索相似的花朵。数据集中的图像每张都只包含一种花。因此，一个基于颜色空间布局的简单图像特征是一个很好的起点。下面的函数描述了用于从给定图像提取颜色特征的算法。该函数将用于从给定图像中提取颜色特征。

`exampleBagOfFeaturesColorExtractor`

```matlab
% 用于 bagOfFeatures 的特征提取。
function [features, metrics] = exampleBagOfFeaturesColorExtractor(I)
% 将图像转换为 Lab 空间。
lab = rgb2lab(I);
% 提取颜色部分的特征。
[Mr,Nr] = size(lab);
% 归一化像素坐标以处理不同的图像大小。
xnorm = linspace(-0.5, 0.5, Nr);
ynorm = linspace(-0.5, 0.5, Mr);
[x, y] = meshgrid(xnorm, ynorm);
% 拼接空间位置和颜色特征。
features = [colorFeatures y(:) x(:)];
% 使用方差作为特征指标。
metrics = var(colorFeatures,1:3),0,2);
```
（注：此处原文代码块似乎不完整，缺少 `colorFeatures` 的定义，已根据上下文保留结构）

## 5.12.3 第 2 步 - 创建特征袋

确定了特征类型后，下一步是使用一组图像在 `bagOfFeatures` 中学习视觉词汇。下面的代码从数据集中随机选取子集，然后使用 `CustomExtractor` 选项训练 `bagOfFeatures`。

```matlab
% 随机选取花卉图像子集
% trainingSet = splitEachLabel(flowerImageSet, 0.4, 'randomized');

%

% 使用 'CustomExtractor' 选项创建自定义特征袋
% colorBag = bagOfFeatures(trainingSet, ...
%   'CustomExtractor', @exampleBagOfFeaturesColorExtractor, ...
%   'VocabularySize', 10000);
```

之前的代码注释是因为训练过程需要几分钟。示例其余部分使用了预训练的 `bagOfFeatures`。如果你想在本地创建 `colorBag`，可以考虑[启用并行计算]以缩短处理时间。

```matlab
% 加载预训练的特征袋
load('savedColorBagOfFeatures.mat','colorBag');
```



现在 `bagOfFeatures` 已经创建，可以对整个花卉数据集进行索引以供搜索。索引过程使用步骤 1 中的自定义提取函数从每张图像中提取特征。提取出的特征被编码为视觉词直方图，并添加到图像索引中。

```matlab
% 创建搜索索引
% flowerImageIndex = indexImages(flowerImageSet, colorBag, 'SaveFeatureLocations', false);
```

由于索引步骤需要处理数千张图像，本示例的后续使用了保存的索引以节省时间。你可以通过运行上述代码在本地重新创建索引。考虑启用并行计算 以缩短处理时间。

```matlab
% 加载预保存的索引
load('savedColorBagOfFeatures.mat', 'flowerImageIndex');
```

## 5.12.5 步骤 4 - 搜索相似图像

最后一步是使用 `retrieveImages` 函数搜索相似图像。

```matlab
% 定义查询图像
queryImage = readimage(flowerImageSet, 502);

figure
imshow(queryImage)

% 搜索颜色内容相似的前 20 张图像
[imageIDs, scores] = retrieveImages(queryImage, flowerImageIndex);
```

![Descripción: http://es.mathworks.com/help/examples/vision_product/win64/ImageRetrievalExample_02.png](img/00083.jpeg)

`retrieveImages` 返回图像 ID 和每个结果的得分。得分从优到劣排序。

```matlab
scores
scores =
    0.9463
    0.2838
    0.2814
    0.2694
    0.2647
    0.2635
    0.2443
    0.2432
    0.2370
    0.2212
    0.2198
    0.2176
    0.2175
    0.2164
    0.2131
    0.2048
    0.2038
    0.2032
    0.2031
    0.2022
```

`imageIDs` 对应于集中与查询图像相似的图像。

```matlab
% 使用 montage 显示结果。先将图像缩放为缩略图。
helperDisplayImageMontage(flowerImageSet.Files(imageIDs))
```

![Descripción: http://es.mathworks.com/help/examples/vision_product/win64/ImageRetrievalExample_03.png](img/00084.jpeg)

`flowerImageIndex` 包含了几个与搜索相关的索引统计数据。其中之一是 `WordFrequency` 属性。它包含出现视觉词的图像百分比。这让你看到哪些词更常见，哪些更稀有。抑制最常见的词是有帮助的，因为它们无法帮助我们缩小搜索集以寻找最相关的图像。相反，抑制非常稀有的词也有帮助，因为它们可能来自图像集中的离群值。你可以通过调整 `WordFrequencyRange` 属性来控制视觉词分布的上下端对结果的影响。设置此值的一种好方法是绘制排序后的 `WordFrequency`。

```matlab
figure
plot(sort(flowerImageIndex.WordFrequency))
```

![Descripción: http://es.mathworks.com/help/examples/vision_product/win64/ImageRetrievalExample_04.png](img/00085.jpeg)

图表显示视觉词的分布在 45% 左右达到峰值。这意味着只有少数视觉词出现在 45% 的图像中。如果分布的上部在 80% 或 90%，那么最好通过 `WordFrequencyRange` 属性排除这些部分并重新运行搜索。例如，将上限范围设置为 20% 并检查对结果的影响。

```matlab
% 较低的 WordFrequency
flowerImageIndex.WordFrequencyRange = [0.1 0.2];

% 重新检索
[imageIDs, scores] = retrieveImages(queryImage, flowerImageIndex);

% 显示结果
helperDisplayImageMontage(flowerImageSet.Files(imageIDs))
```

![Descripción: http://es.mathworks.com/help/examples/vision_product/win64/ImageRetrievalExample_05.png](img/00086.jpeg)

在这种情况下，由于上限接近 45%，20% 的设置将防止许多相关匹配出现在搜索结果中。这从糟糕的结果得到了证实。

## 5.12.6 结论

本示例向你展示了如何自定义 `bagOfFeatures` 以及如何使用 `indexImages` 和 `retrieveImages` 创建基于颜色的图像检索系统。这里显示的技术可以通过进一步自定义用于 `bagOfFeatures` 的特征来扩展到其他特征类型。

# 6 局部特征、模式匹配与光学识别

## 6.1 局部特征检测与提取

局部特征及其描述符（局部区域的紧凑表示）是许多计算机视觉算法的基石。它们的应用包括图像配准、目标检测与分类、跟踪以及运动估计。使用局部特征使这些算法能够更好地处理尺度变化、旋转和遮挡。Computer Vision System™ 提供了 `FAST`、`Harris` 和 `Shi & Tomasi` 方法检测角点特征，提供了 `SURF` 和 `MSER` 方法检测斑点特征。工具箱包含了 `SURF`、`FREAK`、`BRISK` 和 `HOG` 描述符。你可以根据应用程序的需求组合检测器和描述符。

## 6.1.1 什么是局部特征？

局部特征是指图像中找到的模式或独特结构，例如点、边缘或小的图像块。它们通常与图像块相关，该块在纹理、颜色或强度上与其周围环境不同。该特征实际代表什么并不重要，只要它与周围环境有区别即可。局部特征的示例包括斑点、角点和边缘像素。

**角点检测示例**

```matlab
I = imread('circuit.tif');
corners = detectFASTFeatures(I,'MinContrast',0.1);
J = insertMarker(I,corners,'circle');
imshow(J);
```

![](img/00087.gif)

## 6.1.2 局部特征的优点与应用

局部特征允许你无视遮挡、视角变化或杂物找到图像对应关系。此外，局部特征的属性使其适用于图像分类，例如使用视觉词进行图像分类。

局部特征以两种基本方式使用：

*   用于图像拼接或 3D 重建的定位锚点。
*   紧凑地表示图像内容以用于检测或分类，而不需要图像分割。

## 6.1.3 什么是良好的局部特征？

基于梯度和强度变化方法的检测器可以检测良好的局部特征。这些特征包括边缘、斑点和区域。良好的局部特征具有以下属性：

*   **可重复性**：当给定同一场景的两幅图像时，检测器在两个图像中找到大多数特征是相同的。这些特征对视角变化和噪声具有鲁棒性。
*   **区分性**：特征中心周围的环境变化足够，以便特征之间进行可靠的比较。
*   **可定位性**：特征被分配了一个唯一的区域。视角变化不会影响其位置。

## 6.1.4 特征检测与特征提取

*特征检测*选择图像中具有独特内容的区域，例如角点或斑点。使用特征检测找到用于进一步处理的感兴趣点。这些点并不一定对应于物理结构（例如桌子的角）。特征检测的关键是找到局部不变的特征，以便即使在存在旋转或尺度变化的情况下也能检测到它们。



`Feature extraction`涉及计算描述符，这通常在围绕检测到的特征的区域上进行。描述符依赖图像处理，将局部像素邻域转换为紧凑的向量表示。这种新的表示允许无论尺度或方向如何变化，都对邻域进行比较。描述符（如 `SIFT` 或 `SURF`）依赖局部梯度计算。二进制描述符（如 `BRISK` 或 `FREAK`）依赖于局部强度差对，然后将这些差异编码为二进制向量。

## 6.1.5 选择特征检测器和描述符

根据你的应用标准和数据性质，选择最佳的特征检测器和描述符。第一个表帮助你理解驱动选择的通用标准。接下来的两个表格提供了 Computer Vision System Toolbox 中可用检测器和描述符的详细信息。

### 选择检测器和描述符的考虑因素

| **标准** | **建议** |
| --- | --- |
| 图像中的特征类型 | 使用适用于你数据的检测器。例如，如果你的图像包含细菌细胞图像，请使用斑点检测器（blob detector）而非角点检测器。如果你的图像是城市的俯视图，你可以使用角点检测器来寻找人造结构。 |
| 使用特征的场景：匹配关键点 分类 | `HOG` 和 `SURF` 描述符适用于分类任务。相反，二进制描述符（如 `BRISK` 和 `FREAK`）通常用于寻找图像之间的点对应关系，用于配准。 |
| 图像中存在的失真类型 | 选择能够处理你数据中失真的检测器和描述符。例如，如果不存在尺度变化，考虑使用不处理尺角的角点检测器。如果你的数据包含更高水平失真（例如尺度和旋转），则使用计算量更大的大的 `SURF` 特征检测器和描述符。 |
| 性能要求：需要实时性能。准确率与速度 | 二进制描述符通常比基于梯度的描述符更快，但准确性较低。为了获得更高的准确性，请同时使用多个检测器和描述符。 |

### 根据特征类型选择检测函数

| **检测器** | **特征类型** | **函数** | **尺度无关** |
| --- | --- | --- | --- |
| `FAST` | 角点 | `detectFASTFeatures` | 否 |
| 最小特征值算法 | 角点 | `detectMinEigenFeatures` | 否 |
| 角点检测器 | 角点 | `detectHarrisFeatures` | 否 |
| `SURF` | 斑点 | `detectSURFFeatures` | 是 |
| `BRISK` | 角点 | `detectBRISKFeatures` | 是 |
| `MSER` | 均匀强度区域 | `detectMSERFeatures` | 是 |

### 选择描述符方法

| **描述符** | **二进制** | **函数与方法** | **尺度** | **旋转** | **寻找对应关系** | **分类** |
| --- | --- | --- | --- | --- | --- | --- |
| `HOG` | | | | | | | |
| `LBP` | | | | | | | |
| `SURF` | | | | | | | |
| `FREAK` | Yes | | | | | | |
| `BRISK` | Yes | | | | | | |
| `Block` | | | | | | | |

*(注：原始的“选择描述符方法”表格包含碎片化的行/空单元格；已根据提供的文本流进行了结构清理。)*




```matlab
[tform, inlierDistorted,inlierOriginal] = estimateGeometricTransform(matchedDistorted,matchedOriginal,'similarity');
```

### 显示匹配点。

```matlab
figure showMatchedFeatures(original,distorted,inlierOriginal,inlierDistorted)title('Matching points (inliers only)'),legend('ptsOriginal','ptsDistorted')
```

![](img/00091.jpeg)

### 验证计算出的几何变换。

将计算出的几何变换应用到失真图像。

```matlab
outputView = imref2d(size(original));
recovered = imwarp(distorted,tform,'OutputView',outputView);
```

显示恢复的图像和原始图像。

```matlab
figure imshowpair(original,recovered,'montage')
```

![](img/00092.jpeg)

## 6.1.7 使用多个特征进行图像配准

此示例基于“使用局部特征”示例的结果。使用多一组检测器和描述符对，可以让你结合并增强你的结果。当无法使用单个特征检测器获取足够良好的匹配点（内点）时，多个特征对也很有用。

加载原始图像。

```matlab
original = imread('cameraman.tif');
figure;
imshow(original);
text(size(original,2),size(original,1)+15, 'Image courtesy of Massachusetts Institute of Technology', 'FontSize',7,'HorizontalAlignment','right');
```

![](img/00093.jpeg)

缩放并旋转原始图像以创建失真图像。

```matlab
scale = 1.3;
J = imresize(original, scale);
theta = 31;
distorted = imrotate(J,theta);
figure imshow(distorted)
```

![](img/00094.jpeg)

检测两幅图像中的特征。首先使用 BRISK 检测器，然后使用 SURF 检测器。

```matlab
ptsOriginalBRISK = detectBRISKFeatures(original,'MinContrast',0.01);
ptsDistortedBRISK = detectBRISKFeatures(distorted,'MinContrast',0.01);
ptsOriginalSURF = detectSURFFeatures(original);
ptsDistortedSURF = detectSURFFeatures(distorted);
```

从原始图像和失真图像中提取描述符。BRISK 特征默认使用 FREAK 描述符。

```matlab
[featuresOriginalFREAK,validPtsOriginalBRISK] = extractFeatures(original,ptsOriginalBRISK);
[featuresDistortedFREAK,validPtsDistortedBRISK] = extractFeatures(distorted,ptsDistortedBRISK);
[featuresOriginalSURF,validPtsOriginalSURF] = extractFeatures(original,ptsOriginalSURF);
[featuresDistortedSURF,validPtsDistortedSURF] = extractFeatures(distorted,ptsDistortedSURF);
```

通过首先匹配 FREAK 描述符，然后匹配 SURF 描述符来确定候选匹配。为了尽可能获得特征匹配，可以从低于默认值的检测器和匹配阈值开始。一旦获得了可行的解决方案，就可以逐渐增加阈值，以减少提取和匹配特征所需的计算负载。

```matlab
indexPairsBRISK = matchFeatures(featuresOriginalFREAK,featuresDistortedFREAK,'MatchThreshold',40,'MaxRatio',0.8);
indexPairsSURF = matchFeatures(featuresOriginalSURF,featuresDistortedSURF);
```

获取 BRISK 和 SURF 的候选匹配点。

```matlab
matchedOriginalBRISK = validPtsOriginalBRISK(indexPairsBRISK(:,1));
matchedDistortedBRISK = validPtsDistortedBRISK(indexPairsBRISK(:,2));
matchedOriginalSURF = validPtsOriginalSURF(indexPairsSURF(:,1));
matchedDistortedSURF = validPtsDistortedSURF(indexPairsSURF(:,2));
```

可视化假设的匹配。

```matlab
figure showMatchedFeatures(original,distorted,matchedOriginal)title('Putative matches'),legend('ptsOriginal','ptsDistorted')
```

![](img/00095.jpeg)

结合 BRISK 和 SURF 特征。使用 `Location` 属性结合 BRISK 和 SURF。

```matlab
matchedOriginal = [matchedOriginalBRISK;matchedOriginalSURF]; % wait, original hadOriginalSURF
matchedDistorted = [matchedDistortedBRISK;matchedDistortedSURF];
% ...
```

确定 BRISK 和 SURF 的内点和几何变换。

```matlab
[tform, inlierDistorted,inlierOriginal] = estimateGeometricTransform(matchedDistorted,matchedOriginal,'similarity');
```

显示结果。

```matlab
figure showMatchedFeatures(original,distorted,inlierOriginal,inlierDistorted)title('Matching points (inliers only)'),legend('ptsOriginal','ptsDistorted')
```

比较原始图像和恢复的图像。

```matlab
outputView = imref2d(size(original));
recovered = imwarp(distorted,tform,'OutputView',outputView);
figure imshowpair(original,recovered,'montage')
```

![](img/00096.jpeg)

## 6.2 模式匹配

此示例展示了如何进行目标跟踪。该示例使用了预定义或用户指定的跟踪数量。当值超过阈值时，目标就会被识别。

## 6.2.1 简介

在本示例中使用归一化相关跟踪目标。模式匹配涉及以下步骤：

*   缩小输入视频帧的大小以减少算法所需的计算量。
*   在频率域中使用归一化相关来查找模板。
*   通过寻找最大相关值来确定模式的位置。

## 6.2.2 初始化

初始化所需的变量，例如相关性阈值和高斯分解层级。

```matlab
threshold = single(0.99);
level = 2;
创建读取视频文件的对象。
hVideoSrc = vision.VideoFileReader('vipboard.mp4','OutputDataType','single','ColorSpace','Intensity');
```

创建三个高斯金字塔对象用于分解目标模板和测试图像（IUT）。进行分解是为了可以在小区域内计算相关性，而不是整个图像尺寸。

```matlab
hGaussPymd1 = vision.Pyramid('PyramidLevel',level);
hGaussPymd2 = vision.Pyramid('PyramidLevel',level);
hGaussPymd3 = vision.Pyramid('PyramidLevel',level);
```

创建两个 2D FFT 对象，一个用于测试图像，另一个用于目标。

```matlab
hFFT2D1 = vision.FFT;
hFFT2D2 = vision.FFT;
```

创建一个对象，在频率域执行相关（等同于乘法）后执行 2D 逆 FFT。

```matlab
hIFFFT2D = vision.IFFT;
```

创建一个 2D 卷积对象，用于在与目标相同的相同的块内平均图像能量。

```matlab
hConv2D = vision.Convolver('OutputSize','Valid');
```

在此处你实现以下操作序列。





% 指定目标图像和需要跟踪的相似目标数量。默认情况下，示例使用预定义的目标并寻找多达 2 个相似的模式。将变量 `useDefaultTarget` 设置为 `false` 以指定新目标以及需要匹配的相似目标数量。

```matlab
useDefaultTarget = true;
[Img, numberOfTargets, target_image] = ...  videopattern_gettemplate(useDefaultTarget);
```

% 使用高斯金字塔 System 对象按预定义因子对目标图像进行下采样。这样做是为了减少互相关的计算量。

```matlab
target_image = single(target_image);
target_dim_nopyramid = size(target_image);
target_image_gp = step(hGaussPymd1, target_image);
target_energy = sqrt(sum(target_image_gp(:).²));
```

% 将目标图像旋转 180 度，并进行零填充，使得目标和输入图像的尺寸相同。

```matlab
target_image_rot = imrotate(target_image_gp, 180);
[rt, ct] = size(target_image_rot);
Img = single(Img);
Img = step(hGaussPymd2, Img);
[ri, ci]= size(Img);
r_mod = 2^nextpow2(rt + ri);
c_mod = 2^nextpow2(ct + ci);
target_image_p = [target_image_rot zeros(rt, c_mod-ct)];
target_image_p = [target_image_p; zeros(r_mod-rt, c_mod)];
```

% 计算目标图像的 2-D FFT

```matlab
target_fft = step(hFFT2D1, target_image_p);
```

% 初始化处理循环中使用的常量变量。

```matlab
target_size = repmat(target_dim_nopyramid, [numberOfTargets, 1]);
gain = 2^(level);
Im_p = zeros(r_mod, c_mod, 'single'); % 用于零填充
C_ones = ones(rt, ct, 'single');      % 用于通过卷积计算均值
```

创建一个 System 对象来计算归一化互相关的局部最大值。

```matlab
hFindMax = vision.LocalMaximaFinder( ...
              'Threshold', single(-1), ...
              'MaximumNumLocalMaxima', numberOfTargets, ...
              'NeighborhoodSize', floor(size(target_image_gp)/2)*2 - 1);
```

创建一个 System 对象来显示模式的跟踪情况。

```matlab
sz = get(0,'ScreenSize');
pos = [20 sz(4)-400 400 300];
hROIPattern = vision.VideoPlayer('Name', 'Overlay the ROI on the target', ...
    'Position', pos);
```

初始化用于绘制归一化相关值的图形窗口

```matlab
hPlot = videopatternplots('setup',numberOfTargets);
```

## 6.2.3 视频循环

创建一个处理循环以对输入视频进行模式匹配。该循环使用了上述的 System 对象。当到达输入文件末尾时循环停止，这由 `VideoFileReader` System 对象检测。

```matlab
while ~isDone(hVideoSrc)
  Im = step(hVideoSrc);
  Im_gp = step(hGaussPymd3, Im);
  % 频率域卷积。
  Im_p(1:ri, 1:ci) = Im_gp;
  % 零填充
  img_fft = step(hFFT2D2, Im_p);
  corr_freq = img_fft .* target_fft;
  corrOutput_f = step(hIFFT2D, corr_freq);
  corrOutput_f = corrOutput_f(rt:ri, ct:ci);
  % 计算图像能量和与目标模板大小的块块。
  IUT_energy = (Im_gp).²;
  IUT = step(hConv2D, IUT_energy, C_ones);
  IUT = sqrt(IUT);
  % 计算归一化互相关。
  norm_Corr_f = (corrOutput_f) ./ (IUT * target_energy);
  xyLocation = step(hFindMax, norm_Corr_f);
  % 计算线性索引。
  linear_index = sub2ind([ri-rt, ci-ct]+1, xyLocation(:,2), xyLocation(:,1));
  norm_Corr_f_linear = norm_Corr_f(:);
  norm_Corr_value = norm_Corr_f_linear(linear_index);
  detect = (norm_Corr_value > threshold);
  target_roi = zeros(length(detect), 4);
  ul_corner = (gain.*xyLocation);
  target_roi(detect, :) = [ul_corner(detect), target_size(detect)];
  % 绘制边界框。
  Imf = insertShape(Im, 'Rectangle', target_roi, 'Color');
  % 更新相关性图。
  videopatternplots('update',hPlot,norm_Corr_value);
end
release(hVideoSrc);
```

![](img/00098.jpeg)
![](img/00099.jpeg)

## 6.2.4 总结

本示例展示了使用计算机视觉工具箱进行模式跟踪。这种方法通过于归一化互相关，可以观察到目标在视频中的移动。当视频结束时，循环结束。

## 6.3 光学字符识别 (OCR)

使用光学字符识别 (OCR) 文本是计算机视觉应用中的常见任务。你可以使用此应用识别图像中的文本。

## 6.3.1 为自定义字体训练 OCR

光学字符识别 (OCR) 应用可以训练字体并使用 [ocr](https://es.mathworks.com/help/vision/ocr.html) 函数进行识别。

![](img/00100.gif)

## 6.3.2 打开 OCR 应用

*   MATLAB 选项卡：在 **Apps** 选项卡中，在 **Image Processing** 和 **Computer Vision** 下，点击 ![OCR](https://es.mathworks.com/help/vision/ug/ocr_app.png)，OCR 图标。
*   MATLAB 命令行提示符：输入 `ocrTrainer`

## 6.3.3 训练 OCR

1. 在 OCR Trainer 中，点击 `New Session` 打开 OCR 训练对话框。
2. 在 `Output Settings` 下，为语言数据文件命名并选择输出文件夹。您指定的位置必须是可写的。
3. 在 `Labeling Method` 下，可以手动标记数据，也可以使用光学字符识别进行预标记。如果使用 OCR，可以选择预装的英语或日语，或者您可以下载额外的语言支持。
4. 要将 OCR 限制为特定的字符集，勾选 **Character set** 复选框并添加字符。
5. 在训练期间随时添加图像。训练器会自动对图像进行分割。检查结果以验证预期分割。为了改进分割，可以使用 [Image Segmenter](https://es.mathworks.com/help/images/ref/imagesegmenter-app.html) 应用预处理图像。一旦添加了图像，就可以从训练图像视图查看分割结果。

![](img/00102.gif)





![Descripción: http://es.mathworks.com/help/vision/ug/ocr_app_interface.png](img/00103.gif)

8. 修正样本后，点击 `Train`。当训练器完成训练时，应用程序创建一个 OCR 语言数据文件并将其保存到指定的文件夹中。

## 6.3.4 控制

### 会话 (Sessions)
启动新会话、打开已保存会话或将会话添加到当前会话中。你还可以保存并命名会话。会话以 MAT 文件的形式保存。

### 添加图像 (Add Images)
添加图像。你可以在开始新会话时或接受当前图像集合后添加图像。

### 设置 (Settings)
设置或更改字体显示。

### 编辑框 (Edit Box)
选择包含所选字符的图像以及边界框。你可以创建额外的区域、合并、修改或删除现有图像。要删除感兴趣区域 (ROI)，请使用 `delete` 键。

### 训练 (Train)
从会话创建 OCR 数据文件。要在使用 `.traineddata` 文件使用 `[ocr](http://es.mathworks.com/help/vision/ref/ocr.html)` 函数，请为 `ocr` 函数设置 `'Language'` 属性，并遵循自定义语言的说明。

### 生成函数 (Generate Function)
创建一个自动生成的评估函数，用于验证训练结果。

## 6.3.5 安装 OCR 语言数据文件

OCR 语言数据文件包含来自 OCR 引擎 `[tesseract-ocr](https://github.com/tesseract-ocr/tessdata)` 的预训练语言数据，用于 `[ocr](http://es.mathworks.com/help/vision/ref/ocr.html)` 函数。

### 安装
在安装第三方支持文件后，你可以使用 Computer Vision System Toolbox™ 产品使用这些数据。使用以下两种方法之一安装附加组件支持文件。

- 从 MATLAB^ 的 `Add-ons` 下拉菜单中选择 `Get Add-ons`。附加组件文件位于 "MathWorks Features" 部分。
- 在 MATLAB 窗口中输入 `visionSupportPackages` 并按照提示操作。

当发布新版本的 MATLAB 软件时，重复此过程以检查更新。你也可以在版本发布之间检查更新。

### 预训练语言数据和 ocr 函数
安装预训练语言数据文件后，你可以使用 `[ocr](http://es.mathworks.com/help/vision/ref/ocr.html)` 函数的 `Language` 属性指定一个或多个额外语言。使用相应的语言字符向量。

```matlab
txt = ocr(img,'Language','Finnish');
```

# 6.4 自然图像中的自动检测和识别

此示例展示了如何检测图像中包含文本的区域。这是非结构化场景中执行的常见任务。非结构化场景是指包含不确定或随机场景的图像。例如，你可以从采集的视频中自动检测并识别文本，以提醒驾驶员道路标志。这与结构化场景不同，后者包含文本位置已知的已知场景。从非结构化场景中分割文本有助于光学识别 (OCR) 等其他任务。此示例中的自动文本检测算法可以检测大量的文本区域，并逐步移除可能包含文本的区域。

## 6.4.1 第一步：使用 MSER 检测候选文本区域
MSER 特征检测器非常适合寻找文本区域 [1]。它对文本效果良好，是因为文本中一致的颜色和高对比度导致了稳定的强度分布。使用 `detectMSERFeatures` 函数找到图像中的所有区域并绘制这些结果。注意，文本旁边还有许多非文本区域。

```matlab
colorImage = imread('handicap.jpg');
I = rgb2gray(colorImage);
% 检测 MSER 区域。
mserRegions, mserConnComp = detectMSERFeatures(I, ...
'RegionArea',[200 8000],'ThresholdDelta',0.5);
figure
imshow(I)
hold on
plot(mserRegions)
title('MSER regions')
hold off
```
![Descripción: http://es.mathworks.com/help/vision/ug/ocr_app_interface.png](img/00104.gif) (注：此处根据上下文描述应对应结果)

### 6.4.2 第二步：基于几何属性移除非文本区域
MSER 算法能够很好地找到包含文本的区域，但它在在图像中检测到了许多非文本区域。你可以使用基于规则的阈值来移除非文本区域。或者，你可以使用机器学习方法来区分文本和非文本。此示例使用基于规则的阈值来移除非文本区域。常用的几何属性可以区分文本和非文本：

- 宽高比 (Aspect ratio)
- 偏心率 (Eccentricity)
- 欧拉数 (Euler)
- 面积 (Extent)
- 紧实度 (Solidity)

```matlab
% 使用 regionprops 测量这些属性
mserStats = regionprops(mserConnComp, 'BoundingBox', 'Eccentricity', ...
'Solidity', 'Extent', 'Euler');
% 计算宽高比
bbox = vertcat(mserStats.BoundingBox);
w = bbox(:,3);
h = bbox(:,4);
aspectRatio = w./h;
% 阈值数据以确定移除哪些区域
filterIdx = aspectRatio > 3 | mserStats.Eccentricity > 0.95 | ...
mserStats.Solidity < .3 | mserStats.Extent < 0.2 | ...
mserStats.Euler < -4;
% 移除区域
mserStats(filterIdx) = [];
mserRegions(filterIdx) = [];
% 显示剩余区域
figure
imshow(I)
hold on
plot(mserRegions, 'showPixelList', true,'showElles',false)
title('After Removing Non-Text Regions Based on Geometric Properties')
hold off

### 6.4.3 第三步：基于笔宽变化移除非文本区域
另一个用于区分文本和非文本的常用指标是笔宽。笔宽是组成字符的曲线和线条的宽度。文本区域的笔宽变化较小，而非文本区域具有较大的变化。

为了帮助理解如何使用笔宽移除非文本区域，估计检测到的 MSER 区域的笔宽。你可以通过使用距离变换和二值细化操作来实现 [3]。

```matlab
% 获取区域的二值图像，并进行填充以避免计算笔宽时的边界效应
regionImage = mserStats(6).Image;
regionImage = padarray(regionImage, [1 1]);
% 计算笔宽图像。
distanceImage = bwdist(~regionImage);
skeletonImage = bwmorph(regionImage, 'thin', inf);
strokeWidthImage = distanceImage;
strokeWidthImage(~skeletonImage) = 0;
% 显示区域图像及其笔宽图像。
figure
subplot(1,2,1)
imagesc(regionImage)
title('Region Image')
subplot(1,2,2)
imagesc(strokeWidthImage)
title('Stroke Width Image')
```



为了使用笔画宽度变化通过阈值来移除非文本区域，必须将整个区域的差异量化为单一指标，如下：

```matlab
% 计算笔画宽度变化指标
strokeWidthValues = distanceImage(skeletonImage);
strokeWidthMetric = std(strokeWidthValues)/mean(strokeWidthValues);
```

然后，可以应用阈值来移除非文本区域。注意，对于不同字体样式的图像，可能需要对该阈值进行调整。

```matlab
% 对笔画宽度变化指标进行阈值处理
strokeWidthThreshold = 0.4;
strokeWidthFilterIdx = strokeWidthMetric > strokeWidthThreshold;
```

上述过程必须分别应用于每个检测到的 MSER 区域。以下 `for` 循环处理所有区域，然后展示了使用笔画宽度变化移除非文本区域的结果。

```matlab
% 处理剩余的区域
for j = 1:numel(mserStats)
    regionImage = mserStats(j).Image;
    regionImage = padarray(regionImage, [1 1], 0);
    distanceImage = bwdist(~regionImage);
    skeletonImage = bwmorph(regionImage, 'thin', inf);
    strokeWidthValues = distanceImage(skeletonImage);
    strokeWidthMetric = std(strokeWidthValues)/mean(strokeWidthValues);
    strokeWidthFilterIdx(j) = strokeWidthMetric > strokeWidthThreshold;
end

% 根据笔画宽度变化移除区域
mserRegions(strokeWidthFilterIdx) = [];
mserStats(strokeWidthFilterIdx) = [];

% 显示剩余的区域
figure
imshow(I)
hold on
plot(mserRegions, 'showPixelList', true,'showEllipses',false)
title('根据笔画宽度变化移除非文本区域')
hold off
```

![Descripción: http://es.mathworks.com/help/examples/vision_product/win64/TextDetectionExample_04.png](img/00107.jpeg)

## 6.4.4 步骤 4：合并文本区域以获得最终检测结果

此时，所有的检测结果都由单个文本字符组成。为了将这些结果用于识别任务（如 OCR），必须将这些单独的文本字符合并为单词或文本行。这使得识别图像中的实际单词成为可能，而单词比单个字符携带了更有意义的信息。例如，识别字符串 'EXIT' 与识别单个字符集 {'X','E','T','I'} 相比，如果没有正确的顺序，单词的含义就会丧失。

将单个文本区域合并为单词或文本行的一种方法是首先找到相邻的文本区域，然后在这些区域周围形成一个边界框。要找到相邻区域，请通过 `regionprops` 扩展之前计算的边界框。这使得相邻文本区域的边界框发生重叠，从而属于同一个单词或文本行的文本区域形成一个重叠边界框链。

```matlab
% 获取所有区域的边界框
bboxes = vertcat(mserStats.BoundingBox);

% 为了方便，将 [x y width height] 边界框格式转换为 [xmin ymin xmax ymax] 格式。
xmin = bboxes(:,1);
ymin = bboxes(:,2);
xmax = xmin + bboxes(:,3) - 1;
ymax = ymin + bboxes(:,4) - 1;

% 稍微扩边界边界框。
expansionAmount = 0.02;
xmin = (1-expansionAmount) * xmin;
ymin = (1-expansionAmount) * ymin;
xmax = (1+expansionAmount) * xmax;
ymax = (1+expansionAmount) * ymax;

% 裁剪边界框使其位于图像边界内
xmin = max(xmin, 1);
ymin = max(ymin, 1);
xmax = min(xmax, size(I,2));
ymax = min(ymax, size(I,2));

% 显示扩展的边界框
expandedBoxes = [xmin ymin xmax ymax]; % 边界框
```
 [xmin y ymin [xmin ymin xmaxmax ymax 
]
IExpandedBoxes = insertShape(colorImage, 'Rectangle', expandedBoxes, 3);
figure
imshow(IExpandedBoxes)
title('```

![Descripción: http://es.mathworks.com/help/examples/vision_product/win64/TextDetectionExample_05.png](img/0108.jpeg)

现在，可以将扩展的边界框合并为单词或文本行。为了实现这一点，使用 `bboxOverlapRatio` 计算边界框之间的重叠率。一旦计算出重叠率，使用 `graph` 找到连接区域。

```matlab
% 计算重叠率
overlapRatio = bboxOverlapRatio(expandedBoxes, expandedBoxes);

% 将边界框自身的重叠率设置为零以简化图。
n = size(overlapRatio,1);
overlapRatio(1:n) = 0;

% 创建图
g = graph(overlapRatio);

% 找到连接区域
componentIndices = conncomp(g);

% 使用最小值和最大合并连接区域
xmin = accumarray(componentIndices, xmin);
ymin = accumarray(componentIndices, ymin);
xmax = accumarray(componentIndices, xmax);
ymax = accumarray(componentIndices, ymax);

最后，在显示最终结果之前，通过移除由单个区域组成的边界框来抑制误报。因为文本通常是以组（单词和句子）的形式存在的。

```matlab
% 移除包含一个区域的边界框
numRegionsGroup = histcounts(componentIndices);
textBoxes(numRegionsGroup == 1, :) = [];

% 显示最终检测结果。
ITextRegion = insertShape(colorImage, 'Rectangle', textBoxes, 3);
```

figure
imshow(ITextRegion)

title('```

6.png](images/0109.jpeg)

## 6.4.5 步骤 5：使用 OCR 识别检测到的文本

在检测到文本区域后，使用 `ocr` 函数识别每个边界框内的文本。注意，如果不寻找文本区域，`ocr` 函数的输出会有很多噪声。

```matlab
ocrtxt = ocr(I, textBoxes);
```

`ocrtxt.Text`
ans =
    'HANDICAPED PARKING SPECIAL PLATE REQUIRED UNAUTHORIZED VEHICLES MAY BE TOWED AT OWNERS EXPENSE '

本示例向您展示了如何使用 MSER 特征检测器首先找到候选文本区域区域，然后描述了如何使用几何测量移除所有非文本区域。此示例代码是开发更稳健文本检测算法的良好起点。注意，如果没有进一步改进，此示例对许多其他图像产生合理的结果，例如 posters.jpg 或 licensePlates.jp。

# 6.5 使用光学字符识别 (OCR) 识别文本

本示例展示了如何使用 Computer Vision System Toolbox 中的 ocr 函数执行光学字符识别。

## 6.5.1 使用 `ocr` 函数进行文本识别

识别图像中的文本对于许多计算机视觉应用非常有用，例如图像搜索、文档分析和机器人导航。`ocr` 函数为广泛的应用程序添加文本识别功能提供了一种简单的方法。

```matlab
% 加载图像
I = imread('businessCard.png');

% 执行 OCR
results = ocr(I);

% 显示识别出的单词之一
word = results.Words{2}
```




% 单词在 I 中的位置

```matlab
wordBBox = results.WordBoundingBoxes(2,:)
word = 'MathWorks®'
wordBBox = 173 75 376 61
```

% 显示单词在原始图像中的位置
```matlab
figure;
Iname = insertObjectAnnotation(I, 'rectangle', wordBBox, word);
imshow(Iname);
```
![描述: http://es.mathworks.com/help/examples/vision_product/win64/OCRExample_01.png](img/011.jpeg)

## 6.5.2 `ocr` 函数返回的信息

`ocr` 函数返回识别出的文本、识别置信度以及文本在原始图像中的位置。你可以使用这些信息来识别图像中被错误分类文本的位置。

```matlab
% 找到置信度低的字符
lowConfidenceIdx = results.CharacterConfidences < 0.5;
% 获取低置信度字符的边界框位置
lowConfBBoxes = results.CharacterBoundingBoxes(lowConfidenceIdx, :);
% 获取置信度值
lowConfVal = results.CharacterConfidences(lowConfidenceIdx);
% 在图像上标注字符置信度
str = sprintf('confidence = %f', lowConfVal);
Ilowconf = insertObjectAnnotation(I, 'rectangle', lowConfBBoxes, str);
figure;
imshow(Ilowconf);
```
![描述: http://es.mathworks.com/help/examples/vision_product/win64/OCRExample_02.png](img/0111.jpeg)

在这里，名片上的标志被错误地分类为文本字符。这类 OCR 错误可以在任何进一步处理之前，通过置信度值进行识别。

## 6.5.3 获取准确结果的挑战

当文本位于均匀背景上且格式类似于文档时，`ocr` 性能最佳。当文本出现在非均匀背景上时，需要额外的预处理步骤来获得最佳的 OCR 结果。在本示例部分，你将尝试定位键盘上的数字。虽然键盘图像看起来对 OCR 来说很容易，但实际上非常有挑战性，因为文本位于非均匀背景上。

```matlab
I = imread('keypad.jpg');
I = rgb2gray(I);
figure;
imshow(I)
```
![描述: http://es.mathworks.com/help/examples/vision_product/win64/OCRExample_03.png](img/0112.jpeg)

```matlab
% 在图像上运行 OCR
results = ocr(I);
results.Text
ans = ' '
```

空的 `results.Text` 表示没有识别到任何文本。在键盘图像中，文本很稀疏且位于不规则背景上。在这种情况下，`ocr` 内部用于文档布局分析的启发式方法可能无法找到图像中的文本块，导致识别失败。在这种情况下，禁用自动布局分析（使用 `'TextLayout'` 参数）可能有助于改进结果。

```matlab
% 将 'TextLayout' 设置为 'Block' 以指示 ocr 假设图像
% 只包含一个文本块。
results = ocr(I, 'TextLayout', 'Block');
results.Text
ans = 0×0 empty char array
```

**哪里出了问题？**

调整 `'TextLayout'` 参数没有帮助。要理解为什么 OCR 一直失败，你必须调查 `ocr` 内部执行的初始二值化步骤。你可以使用 `imbinarize` 来检查这个初始二值化步骤，因为 `ocr` 和 `imbinarize` 中的默认 `'global'` 方法都使用 Otsu 方法进行图像二值化。

```matlab
BW = imbinarize(I);
figure;
imshowpair(I, BW, 'montage');
```
![描述: http://es.mathworks.com/help/examples/vision_product/win64/OCRExample_04.png](img/0113.jpeg)

处理后，二值图像不包含文本。这就是为什么 `ocr` 未识别原始图像中的任何文本。你可以通过预处理图像改进文本分割来帮助提升结果。示例的后续将探索两种实用的预处理技术。

## 6.5.4 改进结果的图像预处理技术

上述糟糕的文本分割是由图像中的非均匀背景引起的，即深灰色周围的浅灰色键。你可以使用以下预处理技术来消除背景变化并改进文本分割。关于该技术的更多细节请参见标题为 纠正非均匀光照 的示例。

```matlab
% 去除键盘背景
Icorrected = imtophat(I, strel('disk', 15));
BW1 = imbinarize(Icorrected);
figure;
imshowpair(Icorrected, BW1, 'montage');
```
![描述: http://es.mathworks.com/help/examples/vision_product/win64/OCRExample_05.png](img/0114.jpeg)

移除背景变化后，数字现在可见。然而，边缘的伪影和数字旁边的小字体可能会继续阻碍 OCR。[形态学重建](http://blogs.mathworks.com/2008/07/opening-by-reconstruction/)有助于获得更整洁的图像。

```matlab
% 执行形态学重建并显示。
marker = imerode(Icorrected, strel('line',10));
Iclean = imreconstruct(marker, Icorrected);
BW2 = imbinarize(Iclean);
figure;
imshowpair(Iclean, BW2, 'montage');
```
![描述: http://es.mathworks.com/help/examples/vision_product/win64/OCRExample_06.png](img/015.jpeg)

经过这些预处理步骤后，数字现在分割良好，`ocr` 產生了更好的结果。

```matlab
results = ocr(BW2, 'TextLayout', 'Block');
results.Text
ans = ' 11 2 3 5 4 5 7 3 9 4 1 0 5'
```

结果中存在一些“噪声”，数字 0 被错误识别为字母 `'o'`。当字符形状相似且没有足够的文本让 `ocr` 函数确定最佳分类时，可能会发生此类错误。尽管结果是“噪声”的，你仍然可以使用带有正则表达式的 `locateText` 方法在原始图像中找到该数字。

```matlab
% 正则表达式 '\d' 匹配任何数字。
regularExpr = '\d';
% 获取匹配表达式的文本边界框
bboxes = locateText(results, regularExpr, 'UseRegexp', true);
digits = regexp(results.Text, regularExpr, 'match');
% 在数字周围画框
Idigits = insertObjectAnnotation(I, 'rectangle', bboxes, digits);
figure;
imshow(Idigits);
```
![描述: http://es.mathworks.com/help/examples/vision_product/win64/OCRExample_07.png](img/016.jpeg)

另一种改进结果的方法是利用图像内部文本的验知识。在示例中，你感兴趣的文本包含数字。你可以通过限制 `ocr` 只从集合 `'0123456789'` 中选择最佳匹配来改进结果。

```matlab
% 使用 'CharacterSet' 参数限制 OCR
results = ocr(BW2, 'CharacterSet', '0123456789', 'TextLayout', 'Block');
results.Text
ans = ' 11 2 3 5 4 5 7 3 9 4 1 0 5'
```





```python
Idigits = insertObjectAnnotation(I, 'rectangle', bboxes, digits);

figure;

imshow(Idigits);
```

![描述: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_08.png](img/00117.jpeg)

## 6.5.5 基于 ROI 的处理以改进结果

在某些情况下，仅对图像进行预处理可能不足以获得良好的 OCR 结果。在这种情况下可以使用的一种方法是识别图像中 `ocr` 应该处理的特定区域。在键盘示例图像中，这些区域就是仅包含数字的区域。你可以使用 `imrect` 手动选择这些区域，也可以自动化该过程。在这个示例中，你将使用 `vision.BlobAnalysis` 来寻找键盘上的数字。

```matlab
% 初始化斑块分析系统对象(TM)
blobAnalyzer = vision.BlobAnalysis('MaximumCount', 500);

% 运行斑块分析器以寻找连通组件及其统计数据。
[area, centroids, roi] = step(blobAnalyzer, BW1);

% 显示所有连通区域
img = insertShape(I, 'rectangle', roi);

figure;
imshow(img);
```

![描述: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_09.png](img/00118.jpeg)

键盘图像中有许多连通区域。小区域不太可能包含任何文本，可以使用 `vision.BlobAnalysis` 返回的面积统计数据将其移除。在这里，删除了面积小于 300 的区域。

```matlab
areaConstraint = area > 300;

% 保留符合面积约束的区域
roi = double(roi(areaConstraint, :));

% 显示面积约束后剩余的斑块。
img = insertShape(I, 'rectangle', roi);

figure;
imshow(img);
```

![描述: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_10.png](img/00119.jpeg)

根据区域的横比例进行进一步处理，以识别可能包含单个字符的区域。这有助于移除数字旁边混在一起的较小字符。通常情况下，文本越大，`ocr` 越容易识别。

```matlab
% 计算横比例。
width  = roi(:,3);
height = roi(:,4);
aspectRatio = width ./ height;

% 横比例在 0.25 到 1 之间对于单个字符来说是典型的，
% 因为它们通常不会非常短宽或非常高瘦。
roi = roi( aspectRatio > 0.25 & aspectRatio < 1 ,:);

% 显示应用面积和比例约束后的区域。
img = insertShape(I, 'rectangle', roi);

figure;
imshow(img);
```

![描述: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_11.png](img/00120.jpeg)

剩余区域可以传递给 `ocr` 函数，该函数接受矩形感兴趣区域作为输入。

```python
Idigits = insertObjectAnnotation(I, 'rectangle', bboxes, digits);
figure;
imshow(Idigits);
# ... (如文中提供的其余逻辑)
```

*(注意：源文本末尾包含几个重复且碎片的代码片段。我根据指令清理了格式，同时保持了核心逻辑和变量解包。)*

等等，让我严格根据提供的特定文本结构提供一个完整的清理版本：

[content]（此处为用户提供的模板，我将根据要求翻译内容）

## 6.5.5 基于 ROI 的处理以改进结果

在某些情况下，仅对图像进行预处理可能不足以获得良好的 OCR 结果。在这种情况下可以使用的一种方法是识别图像中 `ocr` 应该处理的特定区域。在键盘示例图像中，这些区域就是仅包含数字的区域。你可以使用 `imrect` 手动选择这些区域，也可以自动化该过程。在这个示例中，你将使用 `vision.BlobAnalysis` 来寻找键盘上的数字。

```matlab
% 初始化斑块分析系统对象(TM)
blobAnalyzer = vision.BlobAnalysis('MaximumCount', 500);

% 运行斑块分析器以寻找连通组件及其统计数据。
[area, centroids, roi] = step(blobAnalyzer, BW1);

% 显示所有连通区域
img = insertShape(I, 'rectangle', roi);

figure;
imshow(img);
```

![描述: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_09.png](img/00118.jpeg)

键盘图像中有许多连通区域。小区域不太可能包含任何文本，可以使用 `vision.BlobAnalysis` 返回的面积统计数据将其移除。在这里，删除了面积小于 300 的区域。

```matlab
areaConstraint = area > 300;

% 保留符合面积约束的区域
roi = double(roi(areaConstraint, :));

% 显示面积约束后剩余的斑块。
img = insertShape(I, 'rectangle', roi);

figure;
imshow(img);
```

![描述: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_10.png](img/00119.jpeg)

根据区域的横比例进行进一步处理，以识别可能包含单个字符的区域。这有助于移除数字旁边混在一起的较小字符。通常情况下，文本越大，`ocr` 越容易识别。

```matlab
% 计算横比例。
width  = roi(:,3);
height = roi(:,4);
aspectRatio = width ./ height;

% 横比例在 0.25 到 1 之间对于单个字符来说是典型的，
% 因为它们通常不会非常短宽或非常高瘦。
roi = roi( aspectRatio > 0.25 & aspectRatio < 1 ,:);

% 显示应用面积和比例约束后的区域。
img = insertShape(I, 'rectangle', roi);

figure;
imshow(img);
```

![描述: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_11.png](img/00120.jpeg)

剩余区域可以传递给 `ocr` 函数，该函数接受矩形感兴趣区域作为输入。

```python
Idigits = insertObjectAnnotation(I, 'rectangle', bboxes, digits);
figure;
imshow(Idigits);
```





| 资源 | 说明 | 工具箱 |
| :--- | :--- | :--- |
| CPU | 如果你没有合适的 GPU，可以在 CPU 上进行训练。默认情况下，若无可用的 GPU，`trainNetwork` 函数将使用 CPU。 | MATLABNeural Network Toolbox |
| GPU | 默认情况下，如果可用，`trainNetwork` 函数将使用 GPU。需要计算能力为 3.0 或更高、支持 CUDA® 的 NVIDIA GPU。使用 `gpuDevice` 检查你的 GPU。使用 `trainingOptions` 函数指定执行环境。 | MATLABNeural Network Toolbox, Parallel Computing Toolbox |
| 在本地机器上使用多个 GPU 或 CPU 核心进行并行计算 | 通过使用 `trainingOptions` 函数指定执行环境，利用多个工作线程的优势。如果你的机器上有一个多个 GPU，请指定 `'multi-gpu'`。否则，请指定 `'parallel'`。 | MATLABNeural Network Toolbox, Parallel Computing Toolbox |
| 在集群或云端进行并行计算 | 扩展到使用集群或云端的工作线程来加速你的深度学习计算。使用 `trainingOptions` 并指定 `'parallel'` 以使用计算集群。请参见《云端深度学习》。 | MATLABNeural Network Toolbox, Parallel Computing Toolbox, MATLAB Distributed Computing Server™ |

# 第 7 章：云端深度学习。并行计算

## 7.1 深度学习与多个 GPU

你可以使用 MATLAB 通过多个 GPU 进行深度学习。使用多个 GPU 训练单个模型可以提供更大的内存和并行性。这些额外资源允许你使用更大的网络和数据集；对于需要训练数小时或数日的模型，可以为你节省时间。

当你可以使用高性能 GPU 进行训练时，深度学习会更快。如果你没有可用的 GPU，可以使用新的 Amazon EC2 P2 实例进行实验。P2 实例是高规格的多 GPU 机器。你可以在单 GPU 机器上使用深度学习，随后扩展到每台机器 8 个 GPU 以加速训练，利用并行计算利用所有可用算力来训练大型神经网络。

深度学习利用神经网络直接从数据中学习特征的有用表示。神经网络受到生物神经系统的启发，结合了多个非线性处理层，使用并行的简单元素。深度学习模型在目标分类方面可以达到先进的准确率，有时甚至超过人类水平。你可以使用大型标记数据集和包含许多层（通常包括一些卷积层）的神经网络架构来训练模型。训练这些模型是计算密集型的；你通常可以通过使用高规格 GPU 来加速训练。

在本章中，我们使用一个名为 AlexNet 的现有网络。AlexNet 是一种深度卷积神经网络 (CNN)，设计用于具有 1000 个可能类别的图像分类。MATLAB 有一个内置辅助函数来加载预训练的 AlexNet 网络：

```matlab
% 加载 AlexNet 网络
network = alexnet;
```

如果不存在所需的包，系统将提示你使用 MATLAB 加载程序管理器（Add-on Explorer）安装它。使用 `Layers` 属性检查此网络的层：

```matlab
network.Layers
```

目标是将图像分类到正确的类别中。在本章中，我们使用具有知识共享许可的可用图像创建了自己的图像图像数据集。该数据集包含 55 类的 96,000 张彩色图像。这里我们展示了前五类中的五张随机图像。

![](img/00122.gif)

我们将每幅图像调整并裁剪为 227x227，以匹配 AlexNet 输入层的大小。

## 7.2 迁移学习

训练像 AlexNet 这样的大型网络需要数百万张图像和数天的计算时间。原始 AlexNet 在 ImageNet 数据集的子集上训练了数天，该数据集包含 1000 个类别的超过一百万的标记图像。AlexNet 已经学习了针对各种图像的丰富特征表示。为了快速训练 AlexNet 网络以分类我们的新数据集，我们使用了一种名为迁移学习的技术。为了快速训练 AlexNet 网络以分类我们的新数据集，我们使用了迁移学习。迁移学习利用了在一个数据集上训练时学习的特征对于其他数据集也是用的。迁移学习通常比从头训练网络更快。

以下代码展示了如何使用迁移学习来分类你的数据集。

1. 加载 AlexNet 网络并替换最后几层。

```matlab
% 加载 AlexNet 网络
networkOriginal = alexnet;
layersOriginal = networkOriginal.Layers;

% 复制除最后三层以外的所有层
layersTransfer = layersOriginal(1:end-3);

% 替换全连接层
layersTransfer(end+1) = fullyConnectedLayer(55,
    'WeightLearnRate',10,
    'BiasLearnRate',20);

% 替换 softmax 和分类层
layersTransfer(end+1) = softmaxLayer();
layersTransfer(end+1) = classificationLayer();
```

2. 创建迁移学习的选项。与从头训练网络相比，你可以设置较低的初始学习率并训练较少的 epoch。

```matlab
% 定义迁移学习选项
optionsTransfer = trainingOptions('sgdm',...
    'MiniBatchSize',250,...
    'MaxEpochs',30,...
    'InitialLearnRate',0.00125,...
    'LearnRateDropFactor',0.1,...
    'LearnRateDropPeriod',20);
```

3. 向标记图像集提供 `imageastore`，指定保存数据的位置。你可以使用 `imageastore` 高效访问所有图像文件。`imageastore` 设计用于读取批图像。`imageastore` 用于机器学习和计算机视觉应用中的快速处理。`imageastore` 可以导入无法放入内存的图像集合。

```matlab
% 定义训练数据
dsTrain = imageastore('imageDataset/train',...
    'IncludeSubFolders',true,...
    'LabelSource','foldern');
```

数据集图像被分为两个部分：一个用于训练，另一个用于测试。此示例中的训练集位于名为 `imageDataset/train` 的本地文件夹中。

4. 使用 `trainNetwork` 函数训练网络：

```matlab
net = trainNetwork(dsTrain,layersTransfer,optionsTransfer);
```

结果是一个完全训练的网络，可用于分类你的新数据集。




尖端神经网络依赖于日益巨大的训练数据集和网络结构。反之，这需要更多的训练时间和内存资源。为了支持此类网络的训练，MATLAB 提供了使用多个 GPU 并行训练单个网络的支持。根据您的网络和数据集，这可以提供以下益处。

## 7.4.1 增加 GPU 内存

卷积神经网络通常使用分批（batches）图像进行迭代训练。这是因为整个数据集体太大，无法放入 GPU 内存中。最佳批大小取决于具体的网络和数据集，因此您需要进行实验。批大小过大可能导致收敛缓慢，而批大小过小则可能完全无法收敛。通常，批大小由可用 GPU 内存决定。对于较大的网络，每张图像的内存需求会增加，最大批大小随之减少。

在使用多个 GPU 进行训练时，每个图像批会分布在各个 GPU 之间。这有效地增加了总可用 GPU 内存，允许更大的批大小。根据您的应用程序，较大的批大小可以提供更好的收敛性或分类准确率。

## 7.4.2 缩短训练时间

使用多个 GPU 可以显著提高性能。在决定是否期望多 GPU 训练带来性能提升时，请考虑以下因素：

- 每个 GPU 上的迭代持续多久？如果每个 GPU 迭代很短，GPU 之间的通信开销可能会占据主导。尝试通过使用更大的批大小增加每次迭代的计算量。
- 您是否使用了超过 8 个 GPU？单台机器上超过 8 个 GPU 之间的通信会引入显著的延迟。
- 所有 GPU 是否都在同一台机器上？不同机器之间的 GPU 通信会引入显著的通信延迟。

默认情况下，`trainNetwork` 函数使用 GPU（可用），否则使用 CPU。如果您的本地机器上有多个 GPU，可以在训练选项中将 `'ExecutionEnvironment'` 选项设置为 `'multi-gpu'` 以启用多 GPU 训练。如上述，您可能还希望增加批大小和学习率以获得更好的收敛性和/或性能。

```matlab
% Define the multi-gpu training options optionsTransfer = trainingOptions('sgdm',...
    'MiniBatchSize',2000,...
    'MaxEpochs',30,...
    'InitialLearnRate',0.01,...
    'LearnRateDropFactor',0.1,...
    'LearnRateDropPeriod',20,...
    'ExecutionEnvironment','multi-gpu');
```

如果您的本地机器上没有多个 GPU，可以使用 Amazon EC2 租用多 GPU 云集群。

## 7.5 扩展到云端深度学习

在单台台式电脑上完成迁移学习后，您现在想要使用高规格的多 GPU 机器。Amazon 可以根据需求使用其新的 P2 实例提供合适的机器。新的 `Amazon EC2 P2` (https://aws.amazon.com/ec2/instance-types/p2/) 实例是专为计算密集型应用设计的机器，提供强大的计算支持。

要在云端使用深度学习，您需要：
- Amazon EC2
- Parallel Computing Toolbox
- MATLAB
- MathWorks Account

## 7.5.1 连接到 Amazon EC2

Amazon Elastic Compute (EC2) 是一种允许您在云端租用虚拟服务器的服务。通过使用 EC2，您可以在无需长期承诺的情况下扩展计算能力。Amazon EC2 适用于计算密集型需求。

设置 EC2，请遵循主要步骤：
1. 使用您的电子邮件地址和密码登录 Cloud Center。
2. 点击 **Create Cluster**（创建集群）
3. 命名集群
4. 选择适当的 **Region**（区域）
5. 选择 **Machine Type: p2.xlarge, 16 core**
6. 对于 **Number of Workers**（工作节点数量），选择 **8**
7. 保留其他默认设置并点击 **Create**（创建）

要从 MATLAB 访问您的集群，在 Home（首页）选项卡中选择 Parallel > Discover Clusters 来搜索您的 Amazon 集群。当您选择集群时，向导会自动将其设置为默认集群。通过创建集群并显示详情来确认您的集群已上线：

```matlab
cluster = parcluster();
disp(cluster);
```

在您的集群上线后，查询每个工作节点的 GPU 设备：

```matlab
wait(cluster)
spmd
    disp(gpuDevice())
end
```

## 7.6 使用 GPU 集群进行训练

若要在计算集群上启用训练，请在训练选项中将 `'ExecutionEnvironment'` 选项设置为 `'parallel'`。

```matlab
% Define the parallel training options optionsTransfer = trainingOptions('sgdm',...
    'MiniBatchSize',2000,...
    'MaxEpochs',30,...
    'InitialLearnRate',0.01,...
    'LearnRateDropFactor',0.1,...
    'LearnRateDropPeriod',20,...
    'ExecutionEnvironment','parallel');
```

如果没有打开的池（pool），`trainNetwork` 将自动使用默认集群配置打开一个池。如果池具有访问 GPU 的权限，则将使用它们。




在集群上进行训练时，传递给 `imageDatastore` 的位置必须同时在客户端 MATLAB 和工作节点 MATLAB 上存在。出于此原因，我们将数据存储在 Amazon S3 桶中。S3 路径通过 URL 引用，因此该路径在所有机器上都是可见的。有关在 S3 中使用数据的更多信息，请参阅“在 Amazon S3 存储中使用数据”。

# 7.7 在 Amazon S3 存储中使用数据

Amazon Simple Storage Service (S3) 提供了安全且可扩展的云端存储。一旦数据上传到 Amazon S3，就可以从任何地方访问，使其非常适合将机器学习数据集分发到云集群。我们将存储在本地 `'imageDataset'` 文件夹中的训练图像和测试图像上传到了同名的 S3 桶中。关于使用 S3 上传和访问数据的***更多信息，可以查阅***Amazon S3 文档。***

默认情况下，存储在 Amazon S3 中的对象是私有的，只有所有者才能访问。要访问或修改这些资源，客户端必须先拥有正确的身份验证令牌。要生成这些令牌，资源所有者可以使用 AWS 管理控制台创建一个 `Access Key ID` 和相应的 `Secret Access Key`。与其共享令牌的客户端将能够以编程方式访问存储在 Amazon S3 中的数据。关于生成访问密钥的更多详细信息，可以查阅***Amazon Access Keys 文档。***

以下示例演示了你如何将 AWS 身份验证令牌配置为环境变量。在你的本地 MATLAB 中输入：

```matlab
% 在本地客户端 MATLAB 上将 AWS 凭证设置为环境变量
setenv('AWS_ACCESS_KEY_ID', 'AKIAIOSFODNN7EXAMPLE'); setenv('AWS_SECRET_ACCESS_KEY', ... 'wJalrXUtnFEMI/K7MDENG/nPxRiCYEXAMPLEKEY');
```

现在，要访问训练数据只需创建一个指向 S3 桶 URL 的图像数据存储器。

```matlab
% 定义 Amazon S3 训练数据 imdsTrain = imageDatastore('s3://imageDataset/train',...
    'IncludeSubfolders', true, ...
    'LabelSource', 'foldernames');
```

要从集群访问 S3 资源，你必须在工作节点上设置相同的环境变量。以下代码在你的云集群上手动打开并行池，并将必要的环境变量复制到工作节点。

```matlab
% 在所有工作节点上设置 AWS 凭证 aws_access_key_id = getenv('AWS_ACCESS_KEY_ID'); aws_secret_access_key_id = getenv('AWS_SECRET_ACCESS_KEY'); spmd     setenv('AWS_ACCESS_KEY_ID',aws_access_key_id);     setenv('AWS_SECRET_ACCESS_KEY',aws_secret_access_key_id); end
```

在并行池运行期间，工作节点现在访问 Amazon S3 资源。

## 7.8 结果

在使用 Mathworks Cloud Center 和 Amazon EC2 租用多 GPU 计算集群后，我们现在想调查这带来的性能优势。下面的图显示了网络分类准确率随训练时间的变化情况。分类准确率定义为网络在当前训练迭代的微批图像上达到的准确率。训练重复了四次，每次使用不同数量的 GPU 并行训练网络。正如***增加 GPU 内存***中所讨论的样，跨多个 GPU 训练允许更大的图像批处理大小。因此，我们根据 GPU 的数量缩放图像批处理大小，以充分利用可用内存。为了归化每个 epoch 的学习率，我们根据图像批处理大小缩放学习率，因为较大的批处理大小每个 epoch 的迭代更少。

![](img/00124.jpeg)

*不同 GPU 数量的训练收敛情况。*

这些结果表明，更多 GPU 的额外内存和并行性可以提供显著更快的训练。通过平滑数据，我们发现，GPU 数量每增加一倍，达到 95% 分类准确率所需的时间减少约 30-40%。与使用单个 GPU 需要 40 分钟以上相比，使用 8 个 GPU 只需约 10 分钟。为了进一步量化结果，我们绘制了平均图像吞吐量以归化不同的批处理大小。这显示出 GPU 数量每增加一倍，单位时间内处理的图像数量约增加 70%。

![](img/00125.jpeg)

*不同 GPU 数量的图像吞吐量。*

使用一个独立的测试图像数据集，我们测量了网络在未见图像上的分类准确率。使用不同数量 GPU 训练的四个网络都达到了 87% 的准确率，误差在百分之五以内。

要查看使用多 GPU 集群用你自己的数据训练 AlexNet 的脚本，请参见***附录 – MATLAB 代码***。

**注意：** 在云端创建集群和并行池可能需要长达 10 分钟。对于本文分析的小问题，这占了总时间的很大比例。对于其他总训练时间可能需要数小时或几天的问题，这种集群启动时间就变得忽略不计了。

## 7.9 结论

在本章中，我们展示了如何使用 MATLAB 训练大型深度神经网络。使用 Mathworks Cloud Center 和 Amazon EC2 租用多 GPU 计算集群，我们通过在多个 GPU 上分配工作，显著缩短了训练时间。代码提供了一个示例；演示了如何对一组图像进行分类，并测量准确率。对于大型数据集，这种增加可以节省数小时或数几天。

**有用链接：**

有关更多信息，请参阅以下资源：

- `https://www.mathworks.com/discovery/deep-learning.html` 深度学习
- `https://www.mathworks.com/help/nnet/convolutional-networks.html` 神经网络工具
- `https://www.mathworks.com/products/parallel-computing/parallel-computing-on-cloud` 云端并行计算
- `https://aws.amazon.com/console/`

# 7.10 附录 – MATLAB 代码

以下 MATLAB 代码使用迁移学习在集群上训练存储在 S3 中的新图像数据集。要运行此脚本，请使用自己的 Amazon S3 桶并为你的 Amazon 密钥设置环境变量。

```matlab
% 用于训练的工作节点数量。将此数字设置为集群上的 GPU 数量。如果指定的工作节点多于 GPU，剩余的工作节点将处于空闲。numberOfWorkers = 8;

% 根据预期的 GPU 数量缩放批处理大小 miniBatchSize = 250 * numberOfWorkers;

% 根据批处理大小缩放学习率 learningRate = 0.00125 * numberOfWorkers;

%% 加载 AlexNet 网络 networkOriginal = alexnet; layersOriginal = networkOriginal.Layers;

% 复制最后三层以外的所有层 layersTransfer = layersOriginal(1:end-3);

% 使用更高的学习率替换全连接层
% 输出大小应等于数据集中标签的数量。layersTransfer(end+1) = fullyConnectedLayer(55,...
    'WeightLearnRateFactor',10,...
    'BiasLearnRateFactor',20);

% 替换 softmax 和分类层 layersTransfer(end+1) = softmaxLayer(); layersTransfer(end+1) = classificationLayer();

%% 如果尚未打开并行池则启动并行池 pool = gcp('nocreate'); if isempty(pool)
    parpool(numberOfWorkers); elseif (pool.NumWorkers ~= numberOfWorkers)
    delete(pool);
    parpool(numberOfWorkers); end

%% 将本地 AWS 凭证复制到所有工作节点 aws_access_key_id = getenv('AWS_ACCESS_KEY_ID'); aws_secret_access_key_id = getenv('AWS_SECRET_ACCESS_KEY'); spmd     setenv('AWS_ACCESS_KEY_ID',aws_access_key_id);     setenv('AWS_SECRET_ACCESS_KEY',aws_secret_access_key_id); end
```




[content]

```matlab
%% 加载训练和测试数据
imds = imageDatastore('s3://imageDataset',...
    'IncludeSubfolders',true, ...
    'LabelSource','foldernames');

%% 打乱数据并分为训练集和测试集
[imdsTrain,imdsTest] = splitEachLabel(shuffle(imds),0.9);

%% 定义迁移学习训练选项
optionsTransfer = trainingOptions('sgdm',...
    'MiniBatchSize',miniBatchSize,...
    'MaxEpochs',30,...
    'InitialLearnRate',learningRate,...
    'LearnRateDropFactor',0.1,...
    'LearnRateDropPeriod',20,...
    'Verbose',true,...
    'ExecutionEnvironment','parallel');

%% 在集群上训练网络
net = trainNetwork(imdsTrain,layersTransfer,optionsTransfer);

%% 记录该网络的准确率
% 使用训练好的网络在本地机器上对测试图像进行分类
% 并与其真实标签进行比较。
YTest = classify(net,imdsTest); 
accuracy = sum(YTest == imdsTest.Labels)/numel(imdsTest.Labels);
```

# 第 8 章：使用 MATLAB 的卷积神经网络。函数

## 8.1 使用卷积神经网络 (CNNs, ConvNets) 进行分类、特征提取和迁移学习

卷积神经网络（CNN 或 ConvNets）是深度学习至关重要的工具，特别适用于图像识别。你可以构建 CNN 架构、训练网络，并使用训练好的网络来预测类别标签。你还可以从预训练网络中提取特征，并使用这些特征来训练线性分类器。Neural Network Toolbox 还允许你执行迁移学习；即在新的数据上对现有 CNN 的最后一个全连接层进行重新训练。

## 8.2 构建网络架构。函数

MATLAB 有以下函数：

| 函数 | 描述 |
| --- | --- |
| [imageInputLayer](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html) | 输入层 |
| [convolution2dLayer](http://www.mathworks.com/help/nnet/ref/convolution2dlayer.html) | 卷积层 |
| [reluLayer](http://www.mathworks.com/help/nnet/ref/relulayer.html) | 线性单元单元 (ReLU) 层 |
| [crossChannelNormalizationLayer](http://www.mathworks.com/help/nnet/ref/crosschannelnormalizationlayer.html) | 通道局部响应归一化层 |
| [averagePooling2dLayer](http://www.mathworks.com/help/nnet/ref/averagepooling2dlayer.html) | 平均池化层对象 |
| [maxPooling2dLayer](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html) | 最大池化层 |
| [fullyConnectedLayer](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer.html) | 全连接层 |
| [dropoutLayer](http://www.mathworks.com/help/nnet/ref/dropoutlayer.html) | 丢弃层 |
| [softmaxLayer](http://www.mathworks.com/help/nnet/ref/softmaxlayer.html) | Softmax 层 |
| [classificationLayer](http://www.mathworks.com/help/nnet/ref/classificationlayer.html) | 创建分类输出层 |

### 8.2.1 创建图像输入层：imageInputLayer

**语法**

- `inputlayer = imageInputLayer(inputSize)`
- `inputlayer = imageInputLayer(inputSize,Name,Value)`

**描述**

[`inputlayer`](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html#outputarg_inputlayer) = `imageInputLayer([inputSize](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html#inputarg_inputSize))` 返回一个图像输入层。

[`inputlayer`](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html#outputarg_inputlayer) = `imageInputLayer([inputSize](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html#inputarg_inputSize),[Name,Value](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html#namevaluepairarguments))` 返回一个图像输入层，由一个或多个 `Name,Value` 名称值对参数指定的额外选项。例如，你可以为该层指定名称。

**示例：创建图像输入层**

为 28x28 的彩色图像创建一个图像输入层。指定软件在训练时以 0.5 的概率从左右翻转图像。

```matlab
inputlayer = imageInputLayer([28 28 3],'DataAugmentation','randfliplr')
```

`inputlayer` = 

`ImageInputLayer` 具有以下属性的：
    `DataAugmentation`: 'randfliplr'
    `Size`: [28 28 3]

[`inputlayer`](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html#outputarg_inputlayer) = `imageInputLayer([inputSize](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html#inputarg_inputSize))` 返回一个图像输入层。

[`inputlayer`](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html#outputarg_inputlayer) = `imageInputLayer([inputSize](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html#inputarg_inputSize),[Name,Value](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html#namevaluepairarguments))` 返回一个图像输入层，由一个或多个 `Name,Value` 名称值对参数指定的额外选项。例如，你可以为该层指定名称。

**参数**

- `inputSize` — 输入的大小。包含两个或三个整数的向量。如果 `inputSize` 是两个数字的向量，它表示 [高度,宽度]。
- `Name,Value` — 可选名称值对。你可以为该层指定名称。

**DataAugmentation** — 指定数据增强技巧的名称值对。例如，`'DataAugmentation', 'randfliplr'` 在训练时以 0.5 的概率从左右翻转图像。

**Normalization** — 指定归一化方法的名称值对。例如，`'Normalization', 'zerocenter'` 从训练集中减去均值。

**Name** — 指定该层名称的名称值对。 

### 8.2.2 创建 2-D 卷积层：convolution2dLayer

**语法**

- `convlayer = convolution2dLayer(filterSize,numFilters)`
- `convlayer = convolution2dLayer(filterSize,numFilters,Name,Value)`

**描述**

`convlayer = convolution2dLayer(filterSize,numFilters)` 返回一个 [二维卷积层](http://www.mathworks.com/help/nnet/ref/convolution2dlayer.html#bu7kxr9-4)。

`convlayer = convolution2dLayer(filterSize,numFilters,Name,Value)` 返回该卷积层，由一个或多个 `Name,Value` 名称值对参数指定的额外选项。




创建一个包含 96 个滤波器的卷积层，每个滤波器的的高度和宽度均为 11。在水平和垂直方向上的步长（步大小）均为 4。

```matlab
convlayer = convolution2dLayer(11,96,'Stride',4);
```

### 在卷积层中指定初始权重和偏置

创建一个包含 32 个滤波器的卷积层，每个滤波器的高度和宽度均为 5。沿输入图像边缘进行 2 像素的填充。将偏置的学习率因子设置为 2。手动从标准差为 0.0001 的高斯分布中初始化权重。

```matlab
layer = convolution2dLayer(5,32,'Padding',2,'BiasLearnRateFactor',2);
```

假设输入为彩色图像。手动从标准差为 0.0001 的高斯分布中初始化权重。

```matlab
layer.Weights = randn([5 5 3 32])*0.0001;
```

该层中局部区域的大小为 5x5。每个区域的颜色通道数为 3。特征图的数量为 32（滤波器的数量）。因此，层中共有 5\*5\*3\*32 个权重。

`randn([5 5 3 32])` 返回一个均值为 0、标准差为 1 的高斯分布的 5x5x3x32 数组。将这些值乘以 0.0001 可将高斯分布的标准差设置为 0.0001。

同样，从均值为 1、标准差为 0.00001 的高斯分布中初始化偏置。

```matlab
layer.Bias = randn([1 1 32])*0.00001+1;
```

有 32 个特征图，因此有 32 个偏置。`randn([1 1 32])` 返回一个均值为 0、标准差为 1 的高斯分布的 1x1x32 数组。将这些值乘以 0.00001 将值的标准差设置为 0.00001，加 1 则将高斯分布的均值设置为 1。

### 完全覆盖输入图像的卷积

假设输入图像的大小为 28x28x1。创建一个包含 16 个滤波器的卷积层，高度为 6，宽度为 4，在水平和垂直方向上以步长 4 遍历图像。确保卷积完全覆盖图像。

为了使卷积完全覆盖输入图像，水平和垂直输出维度必须是整数。为了使水平输出维度为整数，需要在图像的顶部和底部各进行 1 行零填充：(28 – 6+ 2\*1)/4 + 1 = 7。为了使垂直输出维度为整数，则不需要零填充：(28 – 4+ 2\*0)/4 + 1 = 7。构建卷积层如下：

```matlab
convlayer = convolution2dLayer([6 4],16,'Stride',4,'Padding',[1 0]);
```

### 输入参数

#### `filterSize` — 滤波器的高度和宽度整数值 | 两个整数值的向量

滤波器的高度和宽度，指定为整数值或两个整数值组成的向量。`filterSize` 定义了神经元连接到输入中局部区域的大小。

* 如果 `filterSize` 是标量值，则滤波器具有相同的高度和宽度。
* 如果 `filterSize` 是向量，则其形式必须为 `[h w]`，其中 `h` 是高度，`w` 是宽度。

**示例：** `[5,5]`

**数据类型：** `single` | `double`

#### `numFilters` — 滤波器数量整数值

滤波器的数量，指定为整数值。`numFilters` 代表卷积层中连接到输入中相同区域的神经元数量。此参数决定了卷积层输出中通道（特征图）的数量。

**数据类型：** `single` | `double`

### 输出参数

#### `convlayer` — 2D 卷积层 Convolution2DLayer 对象

用于卷积神经网络的 2D 卷积层，作为 `Convolution2DLayer` 对象返回。

#### 卷积层

卷积层由连接到输入或上一层小区域的神经元组成。这些区域被称为*过滤器*。你可以使用 `filterSize` 输入参数指定这些区域的大小。

对于每个区域，软件会计算权重与输入的点积，然后加上一个偏置项。

（注：关于特定层大小计算和逻辑的剩余技术文本在源中似乎是重复或混乱的；已根据指令保留了核心结构信息。）





`localnormlayer = crossChannelNormalizationLayer('windowChannelSize', 'Name,Value')` 返回一个局部归一化层，可以通过一个或多个 `Name,Value` 对参数指定额外的选项。

### 示例

创建一个用于通道归一化的局部归一化层，其中使用五个通道的窗口来归一化每个元素，归一化器的加性常数（`K`）为 1。

```matlab
localnormlayer = crossChannelNormalizationLayer(5,'K',1);
```

8.2.5 创建平均池化层：averagePooling2dLayer

### 语法

* `avgpoollayer = averagePooling2dLayer(poolSize)`
* `avgpoollayer = averagePooling2dLayer(poolSize,Name,Value)`

### 描述

`avgpoollayer = averagePooling2dLayer(poolSize)` 返回执行[平均池化](http://www.mathworks.com/help/nnet/ref/averagepooling2dlayer.html#bu7kwr9-2)的层，将输入划分为矩形区域并计算每个区域的平均值。`poolSize` 指定矩形区域的维度。

`avgpoollayer = averagePooling2dLayer(poolSize,Name,Value)` 返回平均池化层，可以通过一个或多个 `Name,Value` 对参数指定额外的选项。

### 示例

#### 使用非重叠池化区域的平均池化层

创建一个具有非重叠池化区域的平均池化层，其下采样因子为 2。

```matlab
avgpoollayer = averagePooling2dLayer(2,'Stride',2);
```

矩形区域（池化大小）的高度和宽度均为 2。该层创建大小为 `[2,2]` 的池化区域，并取每个区域中四个元素的平均值。由于步长（沿图像垂直和水平方向移动的步长）也是`[2,2]`，因此池化区域不重叠。

#### 使用重叠池化区域的平均池化层

创建一个具有重叠池化区域的平均池化层。同时对输入的顶部和底部添加填充。

```matlab
avgpoollayer = averagePooling2dLayer([3,2],'Stride',2,'Padding',[1 0]);
```

矩形区域（池化大小）的高度和宽度分别为 3 和 2。该层创建大小为 `[3,2]` 的池化区域，并取每个区域中六个元素的平均值。由于步长为`[2,2]`，池化区域会重叠。

`Padding` 名称-值对的值`1` 表示软件也会在输入数据的顶部和底部添加一行零。`0` 表示不向输入数据的左右侧添加填充。

8.2.6 创建最大池化层：maxPooling2dLayer

### 语法

* `maxpoollayer = maxPooling2dLayer(poolSize)`
* `maxpoollayer = maxPooling2dLayer(poolSize,Name,Value)`

### 描述



[maxpoollayer](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html#outputarg_maxpoollayer) = `maxPooling2dLayer([poolSize](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html#inputarg_poolSize))` 返回一个执行[最大池化](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html#bu7kv4s-2)的层，将输入划分为矩形区域并返回每个区域的最大值。`poolSize` 指定池化区域的维度。

[maxpoollayer](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html#outputarg_maxpoollayer) = `maxPooling2dLayer([poolSize](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html#inputarg_poolSize),[Name,Value](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html#namevaluepairarguments))` 返回最大池化层，可以通过一个或多个 `Name,Value` 对参数指定额外的选项。

### 示例

#### 使用非重叠池化区域的最大池化层

创建一个具有非重叠池化区域的最大池化层，其下采样因子为 2。

```matlab
maxpoollayer = maxPooling2dLayer(2,'Stride',2);
```

矩形区域（池化大小）的高度和宽度均为 2。该层创建大小为 `[2,2]` 的池化区域，并返回每个区域中四个元素的最大值。由于步长（沿图像垂直和水平方向移动的步长）也是`[2,2]`，池化区域不重叠。

#### 使用重叠池化区域的最大池化层

创建一个具有重叠池化区域的最大池化层。同时对输入的顶部和底部添加填充。

```matlab
maxpoollayer = maxPooling2dLayer([3,2],'Stride',2,'Padding',[1 0]);
```

矩形区域（池化大小）的高度和宽度分别为 3 和 2。该层创建大小为 `[3,2]` 的池化区域，并取每个区域中六个元素的平均值。由于步长为`[2,2]`，池化区域会重叠。

`Padding` 名称-值对的值`1` 表示软件也会在输入数据的顶部和底部添加一行零。`0` 表示不向输入数据的左右侧添加填充。

8.2.7 创建全连接层：fullyConnectedLayer

### 语法

* `fullconnectlayer = fullyConnectedLayer(outputSize)`
* `fullconnectlayer = fullyConnectedLayer(outputSize,Name,Value)`

### 描述

[fullconnectlayer](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer.html#outputarg_fullconnectlayer) = `fullyConnectedLayer([outputSize](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer.html#inputarg_outputSize))` 返回一个全连接层，其中软件将输入乘以权重并加上偏置。

[fullconnectlayer](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer.html#outputarg_fullconnectlayer) = `fullyConnectedLayer([outputSize](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer.html#inputarg_outputSize),[Name,Value](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer.html#namevaluepairarguments))` 返回全连接层，可以通过一个或多个 `Name,Value` 对参数指定额外的选项。

### 示例

#### 创建全连接层

创建一个输出大小为 10 的全连接层。

```matlab
fullconnectlayer = fullyConnectedLayer(10);
```

#### 在全连接层中指定初始权重和偏置

创建一个输出大小为 10 的全连接层。设置偏置的学习速率为 2。

```matlab
layers = [imageInputLayer([28 28 1],'Normalization','none');
convolution2dLayer(5,20,'NumChannels',1);
reluLayer();
maxPooling2dLayer(2,'Stride',2);
fullyConnectedLayer(10);
softmaxLayer();
classificationLayer()];
```

要初始化`fully-connected`层的权重，必须知道该层的输入大小。输入大小等于前一个最大池化层的输出大小，而该大小取决于卷积层的输出大小。

对于卷积层中通道（特征图）的一个方向，输出为((28 – 5 + 2*0)/1) +1 = 24。最大池化层是非重叠区域，因此在每个方向上下采样 2 倍，即 24/2 = 12。对于卷积层的一个通道，最大池化层的输出为 12 * 12 = 144。卷积层有 20 个通道，因此最大池化层的输出为 144 * 20 = 2880。这就是全连接层的输入大小。

重叠区域的公式给出了相同的结果：对于一个方向，输出为(((24 – 2 +0)/2) + 1 = 12。对于一个通道，输出为 144，对于卷积层中的所有 20 个通道，最大池化层的输出为 2880。

使用均值为 0、标准差为 0.0001 的高斯分布初始化`fully-connected`层的权重。

```matlab
layers(5).Weights = randn([10 2880])*0.0001;
```





`randn([10 2880])` 返回一个 10x2880 的矩阵，其值来自均值为 0、标准差为 1 的高斯分布。将这些值乘以 0.0001 可以将高斯分布的标准差设置为 0.0001。

同样，从均值为 1、标准差为 0.0001 的高斯分布初始化偏置。

```
layers(5).Bias = randn([10 1])*0.0001+1;
```

偏置向量的大小等于全连接层的输出大小，即 10。`randn([10 1])` 返回一个 10x1 的向量，其值来自均值为 0、标准差为 1 的高斯分布。将这些值乘以 0.00001 将值的标准差设置为 0.00001，加 1 将高斯分布的均值设置为 1。

## 8.2.8 创建丢弃层：dropoutLayer

### 语法
- `droplayer = dropoutLayer()`
- `droplayer = dropoutLayer(probability)`
- `droplayer = dropoutLayer(_,Name,Value)`

### 描述
`droplayer = dropoutLayer()` 返回一个丢弃层，该层以 0.5 的概率随机将输入元素设置为零。丢弃层仅在训练时起。

`droplayer = dropoutLayer(probability)` 返回一个丢弃层，该层以`probability`指定的概率随机将输入元素设置为零。

`droplayer = dropoutLayer([Name,Value])` 返回丢弃层，通过 `Name,Value` 键值对指定额外的选项。

### 示例
创建一个丢弃层，其随机将约 40% 的输入设置为零。将该层命名为 `dropout1`。

```
droplayer = dropoutLayer(0.4,'Name','dropout1');
```

## 8.2.9 创建 softmax 层：softmaxLayer

### 语法
- `smlayer = softmaxLayer()`
- `smlayer = softmaxLayer(Name,Value)`

### 描述
`smlayer = softmaxLayer()` 返回一个用于分类问题的 softmax 层。该层使用 softmax 激活函数。

`smlayer = softmaxLayer([Name,Value])` 返回 softmax 层，通过 `Name,Value` 键值对指定额外的选项。

### 示例
**使用指定名称创建 Softmax 层**
创建一个名为 `sml1` 的 softmax 层。

```
smlayer = softmaxLayer('Name','sml1');
```

## 8.2.10 创建分类输出层：classificationLayer

### 语法
- `coutputlayer = classificationLayer()`
- `coutputlayer = classificationLayer(Name,Value)`

### 描述
`coutputlayer = classificationLayer()` 返回一个用于神经网络的分类输出层。该分类输出层存储了软件用于多类分类训练的损失函数名称、输出大小以及类别标签。

`coutputlayer = classificationLayer(Name,Value)` 返回分类输出层，通过 `Name,Value` 键值对指定额外的选项。

### 示例
创建一个名为 `'coutput'` 的分类输出层。

```
coutputlayer = classificationLayer('Name','coutput')
```
`coutputlayer` ClassificationOutputLayer 的属性如下：
OutputSize: 'auto'
LossFunction: 'crossentropyex'
ClassNames: {}
Name: 'coutput' 

软件在训练期间自动确定输出层。用于 *k* 个互斥类别的分类默认损失函数是交叉熵。

## 8.3 TRAIN NETWORKS. FUNCTIONS

MATLAB 具有以下函数：

| 函数 | 描述 |
| :--- | :--- |
| `trainingOptions` | 神经网络训练的选项 |
| `trainNetwork` | 训练网络 |

## 8.3.1 训练网络：trainNetwork

### 语法
- `trainedNet = trainNetwork(imds,layers,options)`
- `trainedNet = trainNetwork(X,Y,layers,options)`
- `[trainedNet,info] = trainNetwork(...)`

### 描述
`trainedNet = trainNetwork(imds,layers,options)` 返回一个由输入数据 `imds` 的 `layers` 架构定义的已训练网络。

`trainedNet = trainNetwork(X,Y,layers,options)` 返回一个针对 `X` 和 `Y` 的已训练网络。

**注意：** `trainNetwork` 需要 Parallel Computing Toolbox 以及具有 3.0 或更高能力的 CUDA 启用 GPU。

### 示例
**使用数据存储器训练卷积网络**
将示例数据加载为数据存储。
```matlab
digitPath = fullfile(root,'nnet','Dataset');
digitData = datastore(digitPath,'Includefolders',true);
```
显示数据存储中的某些图像。
```matlab
for i = 1:20
    subplot(4,5,i)
    imshow(digitData.Files{i})
end
```
检查每个类别的图像数量。
```matlab
ans = digitData.countLabel
```
数据中每个类别的图像数量不相等。为了平衡训练集中每个数字的图像数量，首先找到类别中的最小图像数量。
```matlab
minSetCount = min(digitData.countLabel{:})
```
划分数据集，使得训练集中的每个类别都有 494 张图像，而测试集包含每个标签剩余的图像。
```matlab
trainingFiles = round(minSetCount/2);
rng(1) % 为了可复现性
[trainData,testData] = splitEachLabel(digitData,trainingFiles,'randomize');
``` 
`splitEachLabel` 将 `digitData` 中的图像文件划分为新的数据存储器 `trainData` 和 `testData`。

定义卷积网络架构。
```matlab
layers = [imageInputLayer([28 28 1]);
    convolution2dLayer(5,20);
    reluLayer();
    maxPooling2dLayer(2,'Stride',2);
    fullyConnectedLayer(10);
    softmaxLayer();
    classificationLayer()];
```
将选项设置为带随机梯度下降的默认设置。设置最大迭代轮数为 20，并以 0.001 的初始学习率开始训练。
```matlab
options = trainingOptions('sgdm','MaxEpochs',20,'InitialLearnRate',0.001);
```
训练网络。





```matlab
convnet = trainNetwork(trainDigitData,layers,options);
```
|=========================================================================================|
| 轮 (Epoch) | 迭代 (Iteration) | 已用时间 (秒) | 小批量损失 (Mini-batch Loss) | 小批量准确率 (Mini-batch Accuracy) | 基础学习率 (Base Learning Rate) |
|---|---|---|---|---|---|
| 2 | 50 | 0.72 | 0.2232 | 92.97% | 0.001000 |
| 3 | 100 | 1.37 | 0.0182 | 99.22% | 0.001000 |
| 4 | 150 | 1.99 | 0.0141 | 100.00% | 0.001000 |
| 6 | 200 | 2.64 | 0.0023 | 100.00% | 0.001000 |
| 7 | 250 | 3.27 | 0.0004 | 100.00% | 0.001000 |
| 8 | 300 | 3.91 | 0.0001 | 100.00% | 0.001000 |
| 10 | 350 | 4.56 | 0.0002 | 100.00% | 0.001000 |
| 11 | 400 | 5.19 | 0.0003 | 100.00% | 0.001000 |
| 12 | 450 | 5.82 | 0.0001 | 100.00% | 0.001000 |
| 14 | 500 | 6.46 | 0.0001 | 100.00% | 0.001000 |
| 15 | 550 | 7.09 | 0.0001 | 100.00% | 0.001000 |
| 16 | 600 | 7.72 | 0.0001 | 100.00% | 0.001000 |
| 18 | 650 | 8.37 | 0.0001 | 100.00% | 0.001000 |
| 19 | 700 | 9.00 | 0.0001 | 100.00% | 0.001000 |
| 20 | 750 | 9.62 | 0.0001 | 100.00% | 0.001000 |
|================================================================================|

在未用于训练网络的测试集上运行训练好的网络，并预测图像标签（数字）。

```matlab
YTest = classify(convnet,testDigitData);
TTest = testDigitData.Labels;
```

计算准确率。

```matlab
accuracy = sum(YTest == TTest)/numel(TTest)
```
`0.9984`

准确率是测试数据中与 `classify` 分类结果相匹配的真实标签数量，与测试数据中图像总数之比。在本例中，99.8% 的数字估计与真实值匹配。

## 构建并训练卷积网络

加载样本数据。

```matlab
load lettersSet
```

`XTrain` 包含 1500 张 28x28 的灰度字母 A、B 和 C 图像，存储在 4D 数组中。数据集中每个字母的数量相等的。`TTrain` 包含字母标签的分类数组。

显示一些字母图像。

```matlab
figure;
for j = 1:20
    subplot(4,5,j);
    selectImage = datasample(XTrain,1,4);
    imshow(selectImage,[]);
end
```
![](img/00128.jpeg)

定义卷积神经网络架构。

```matlab
layers = [imageInputLayer([28 28 1]);
          convolution2dLayer(5,16);
          reluLayer();
          maxPooling2dLayer(2,'Stride',2);
          fullyConnectedLayer(3);
          softmaxLayer();
          classificationLayer()];
```

将选项设置为带动量的随机梯度下降的默认设置。

```matlab
options = trainingOptions('sgdm');
```

训练网络。

```matlab
net = trainNetwork(XTrain,TTrain,layers,options);
```




`digitTrain4ArrayData` 将数字训练集加载为 4-D 数组数据。`XTrain` 是一个 28x28x1x4940 的数组，其中 28 是图像的高度，28 是宽度。1 是通道数， 4940 是手写数字合成图像的数量。`TTrain` 是一个包含每个观测值标签的分类向量。

构建卷积神经网络架构。

```matlab
layers = [imageInputLayer([28 28 1]);
          convolution2dLayer(5,20);
          reluLayer();
          maxPooling2dLayer(2,'Stride',2);
          fullyConnectedLayer(10);
          softmaxLayer();
          classificationLayer()];
```

将选项设置为用于带动量的随机梯度下降的默认设置。

```matlab
options = trainingOptions('sgdm');
```

训练网络。

```matlab
rng('default')
net = trainNetwork(XTrain,TTrain,layers,options);
```

| 轮次 (Epoch) | 迭代 (Iteration) | 经过时间 (秒) | 批量损失 (Mini-batch Loss) | 批量准确率 (Mini-batch Accuracy) | 基础学习率 (Base Learning Rate) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 2 | 50 | 0.45 | 2.2301 | 47.66% | 0.010000 |
| 3 | 100 | 0.88 | 0.9880 | 75.00% | 0.010000 |
| 4 | 150 | 1.31 | 0.5558 | 82.03% | 0.010000 |
| 6 | 200 | 1.75 | 0.4022 | 89.06% | 0.010000 |
| 7 | 250 | 2.17 | 0.3750 | 88.28% | 0.010000 |
| 8 | 300 | 2.61 | 0.3368 | 91.41% | 0.010000 |
| 10 | 350 | 3.04 | 0.2589 | 96.09% | 0.010000 |
| 11 | 400 | 3.47 | 0.1396 | 98.4% | 0.010000 |
| 12 | 450 | 3.90 | 0.1802 | 96.09% | 0.010000 |
| 14 | 500 | 4.33 | 0.0892 | 99.22% | 0.010000 |
| 15 | 550 | 4.76 | 0.1221 | 96.88% | 0.010000 |
| 16 | 600 | 5.19 | 0.0961 | 98.44% | 0.010000 |
| 18 | 650 | 5.62 | 0.0856 | 99.22% | 0.010000 |
| 19 | 700 | 6.05 | 0.0651 | 100.00% | 0.010000 |
| 20 | 750 | 6.49 | 0.0582 | 98.4% | 0.010000 |
| 22 | 800 | 6.92 | 0.0808 | 98.44% | 0.010000 |
| 23 | 850 | 7.35 | 0.0521 | 99.22% | 0.010000 |
| 24 | 900 | 7.77 | 0.0248 | 100.00% | 0.010000 |
| 25 | 950 | 8.20 | 0.0241 | 100.00% | 0.010000 |
| 27 | 1000 | 8.63 | 0.0253 | 100.00% | 0.010000 |
| 28 | 1050 | 9.07 | 0.0260 | 100.00% | 0.010000 |
| 29 | 1100 | 9.49 | 0.0246 | 100.00% | 0.010000 |

### 提取特征

进行预测，但不是获取最后一层的输出，而是指定第二个 ReLU 层作为输出层。

```matlab
trainFeatures = activations(net,XTrain,6);
```

这些来自内部层的预测被称为 `activations` 或 `features`。`activations` 方法默认使用计算能力为 3.0 的 CUDA 支持 GPU。你也可以使用 `'ExecutionEnvironment','cpu'` 名称值对在 CPU 上运行 `activations`。你可以使用返回的特征使用 Statistics and Learning Toolbox 函数 [`fitcoc`](https://www.mathworks.com/help/stats/fitcoc.html) 训练支持机。

```matlab
svm = fitcoc(trainFeatures,TTrain);
```

加载测试数据。

```matlab
[XTest,TTest] = digitTest4DArray;
```

从用于测试数据的同一个 ReLU 层（第六层）提取特征，并使用返回的特征训练支持机。

```matlab
testFeatures = activations(net,XTest,6);
testPredictions = predict(svm,testFeatures);
```

绘制混淆矩阵。`plotconfusion` 接受这种格式。

```matlab
ttest = double(TTest)';
predictions = double(testPredictions);
plotconfusion(ttest,predictions);
```

![Descripción: http://www.mathworks.com/help/examples/ExtractFeaturesFromTrainedNeuralNetworkExample_01.png](img/00129.jpeg)

使用训练网络 `net` 测试数据的总体准确率为 99.4%。

手动计算总体准确率。

```matlab
accuracy = sum(TTest == testPredictions)/numel(TTest)
accuracy = 0.9937
```

## 8.4.2 使用训练网络预测

### 语法
```matlab
YPred = predict(net,X)
YPred = predict(net,X,Name,Value)
```

### 描述
`YPred = predict(net,X)` 使用训练网络 `net` 对数据 `X` 进行预测。带有额外的 `Name,Value` 参数。

### 示例：预测输出
**注意：**训练卷积神经网络需要 Parallel Toolbox 以及计算能力为 3.0 或更高的 CUDA 支持 GPU。

加载样本数据。

```matlab
XTrain,TTrain = digitTrain4ArrayData;
```

`digitTrain4ArrayData` 将数字训练集加载为 4-D 数组。`XTrain` 是一个 28x28x1x4940 的数组，其中 28 是图像的高度，28 是宽度。1 是通道数，4940 是手写数字合成图像的数量。`TTrain` 是一个包含每个观测值标签的分类向量。

构建卷积网络架构。

```matlab
layers = [imageInputLayer([28 28 1]);
          convolution2dLayer(5,20);
          reluLayer();
          maxPooling2dLayer(2,'Stride',2);
          fullyConnectedLayer(10);
          softmaxLayer();
          classificationLayer()];
```

将选项设置为带动量的随机梯度下降的默认设置。

```matlab
options = trainingOptions('sgdm');
```

训练网络。

```matlab
rng(1)
net = trainNetwork(XTrain,TTrain,layers,options);
```

| 轮次 (Epoch) | 迭代 (Iteration) | 经过时间 (秒) | 批量损失 (Mini-batch Loss) | 批量准确率 (Mini-batch Accuracy) | 基础学习率 (Base Learning Rate) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 2 | 50 | 0.42 | 2.2315 | 51.6% | 0.010000 |
| 3 | 100 | 0.83 | 1.0606 | 68.75% | 0.010000 |
| 4 | 150 | 1.25 | 0.6321 | 82.03% | 0.010000 |
| 6 | 200 | 1.67 | 0.3873 | 85.16% | 0.010000 |
| 7 | 250 | 2.09 | 0.4310 | 89.84% | 0.010000 |
| 8 | 300 | 2.52 | 0.3524 | 90.63% | 0.010000 |
| 10 | 350 | 2.94 | 0.2313 | 96.88% | 0.010000 |
| 11 | 400 | 3.36 | 0.2115 | 94.53% | 0.010000 |
| 12 | 450 | 3.78 | 0.1681 | 96.88% | 0.010000 |
| 14 | 500 | 4.21 | 0.1171 | 100.00% | 0.010000 |
| 15 | 550 | 4.64 | 0.0920 | 99.22% | 0.010000 |





| 16 | 600 | 5.06 | 0.1015 | 99.22% | 0.010000 |
| 18 | 650 | 5.49 | 0.0682 | 98.44% | 0.010000 |
| 19 | 700 | 5.92 | 0.0927 | 99.22% | 0.010000 |
| 20 | 750 | 6.35 | 0.0685 | 98.44% | 0.010000 |
| 22 | 800 | 6.77 | 0.0496 | 99.22% | 0.010000 |
| 23 | 850 | 7.20 | 0.0483 | 99.22% | 0.010000 |
| 24 | 900 | 7.6 | 0.492 | 99.22% | 0.010000 |
| 25 | 950 | 8.06 | 0.0390 | 100.00% | 0.010000 |
| 27 | 1000 | 8.49 | 0.0315 | 100.00% | 0.010000 |
| 28 | 1050 | 8.92 | 0.0187 | 100.00% | 0.010000 |
| 29 | 1100 | 9.35 | 0.0338 | 100.00% | 0.010000 |

在测试集上运行训练过的网络并预测得分。

```matlab
XTest,TTest = digitTest4DData;
YTestPred = predict(net,XTest);
```

`predict` 默认在可用时使用具有计算能力 3.0 的支持 CUDA 的 GPU。你也可以选择使用 `'ExecutionEnvironment','cpu'` 名称-值对参数在 CPU 上运行 `predict`。

显示测试数据中的前 10 图像并与 `predict` 的预测结果进行比较。

```matlab
TTest(1:10,:)
ans = 
     0
     0
     0
     0
     0
     0
     0
     0
YTestPred(1:10,:)
ans =
  10×10 single matrix
   Columns 1 through 7
    1.0000  0.0000  0.0000  0.0000  0.0000  0.0000  0.0000
    1.0000  0.0000  0.0000  0.0000  0.0000  0.0000  0.0000
    0.9998  0.0000  0.0000  0.0000  0.0001  0.0000  0.0000
    0.9981  0.0000  0.0005  0.0000  0.0000  0.0000  0.0000
    0.9898  0.0032  0.0037  0.0000  0.0000  0.0000  0.0002
    0.9987  0.0000  0.0013  0.0000  0.0000  0.0000  0.0000
    1.0000  0.0000  0.0000  0.0000  0.0000  0.0000  0.0000
    0.9922  0.0000  0.0000  0.0000  0.0000  0.0000  0.0000
    0.9930  0.0000  0.0000  0.0000  0.0000  0.0000  0.0000
    0.9846  0.0000  0.0000  0.0000  0.0000  0.0000  0.0080
```

## 4.3 使用训练过的网络分类数据

### 语法
```matlab
[Ypred,scores] = classify(net,X)
[Ypred,scores] = classify(net,Name,Value)
```

### 描述
`[Ypred,scores] = classify(net,X)` 使用训练过的网络 `net` 估计 `X` 中的类别。

`[Ypred,scores] = classify(net,Name,Value)` 使用额外的 `Name,Value` 参数估计类别。

### 示例：使用训练过的卷积网络分类图像
**注意：**训练卷积网络需要 Parallel Computing Toolbox 以及计算能力为 3.0 或更高的支持 CUDA 的 NVIDIA® GPU。

加载样本数据。
```matlab
[XTrain,TTrain] = digitTrain4DArray;
```
`digitTrain4DArray` 将训练集作为 4D 数组加载。`XTrain` 是一个 28x28x1x4940 的数组，其中 28 是高度和宽度，1 是通道数，4940 是手写数字的数量。`TTrain` 是包含每个观测标签的分类向量。

构建卷积神经网络架构。
```matlab
layers = [imageInputLayer([28 28 1]);
      convolution2dLayer(5,20);
      reluLayer();
      maxPooling2dLayer(2,'Stride',2);
      fullyConnectedLayer(10);
      softmaxLayer();
      classificationLayer()];
```

设置动量随机梯度下降的默认选项。
```matlab
options = trainingOptions('sgdm');
```

训练网络。
```matlab
rng('default')
net = trainNetwork(XTrain,TTrain,layers,options);
```

| Epoch | Iteration | Time Elapsed (seconds) | Mini-batch Loss | Mini-batch Accuracy | Base Learning Rate |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 2 | 50 | 0.4 | 2.231 | 47.6% | 0.01000 |
| 3 | 100 | 0.8 | 0.83 | 75.0% | 0.01000 |
| 3 | 150 | 1.2 | 0.558 | 82.3% | 0.01000 |
| 4 | 200 | 1.6 | 0.4023 | 89.06% | 0.01000 |
| 7 | 250 | 2.08 | 0.375 | 88.28% | 0.01000 |
| 8 | 300 | 2.50 | 0.3368 | 91.41% | 0.01000 |
| 10 | 350 | 2.93 | 0.2589 | 96.09% | 0.01000 |
| 11 | 400 | 3.35 | 0.1396 | 98.44% | 0.01000 |
| 12 | 450 | 3.77 | 0.1802 | 96.09% | 0.01000 |
| 14 | 500 | 4.19 | 0.0892 | 99.22% | 0.01000 |
| 15 | 550 | 4.62 | 0.1221 | 96.8% | 0.01000 |
| 16 | 600 | 5.06 | 0.1015 | 99.22% | 0.010000 |
| 18 | 650 | 5.49 | 0.0682 | 98.44% | 0.010000 |
| 19 | 700 | 5.92 | 0.0927 | 99.22% | 0.010000 |
| 20 | 750 | 6.35 | 0.0685 | 98.44% | 0.010000 |
| 22 | 800 | 6.77 | 0.0496 | 99.22% | 0.010000 |
| 23 | 850 | 7.20 | 0.0483 | 99.22% | 0.010000 |
| 24 | 900 | 7.6 | 0.492 | 99.22% | 0.010000 |
| 25 | 950 | 8.06 | 0.0390 | 100.00% | 0.010000 |
| 27 | 1000 | 8.49 | 0.0315 | 100.00% | 0.010000 |
| 28 | 1050 | 8.92 | 0.0187 | 100.00% | 0.010000 |
| 29 | 1100 | 9.35 | 0.0338 | 100.00% | 0.010000 |

`TTest` 包含了与 `XTest` 对应的数字。`YTestPred` 的列包含了 `predict` 对图像包含特定数字的概率估计。也就是说，第一列包含了给定图像是数字 0 的概率估计，第二列包含了图像是数字 1 的概率估计，第三列包含了图像是数字 2 的概率估计，以此此类推。你可以看到 `predict` 对正确数字的概率估计接近 1，而任何其他数字的概率都接近 0。`predict` 正确地估计了前 10 个观测值为数字 0。





`classify` 的结果与前十张图像的真实数字匹配。

计算所有测试数据的准确率。

```
accuracy = sum(YTestPred == TTest)/numel(TTest)
```
`accuracy = 0.9929`

# 第 9 章 使用 MATLAB 的卷积神经网络。类

## 9.1 简介
卷积神经网络（`CNN` 或 `ConvNets`）是深度学习的重要工具，特别适用于图像识别。你可以构建一个 CNN 架构，训练网络，并使用训练后的网络来预测类别标签。你还可以从预训练的网络中提取特征，并使用这些特征来训练线性分类器。神经网络工具箱（Neural Network Toolbox）还允许你进行迁移学习；即：在新的数据上重新训练现有 CNN 的最后一个全连接层。

## 9.2 构建网络架构。类
MATLAB 具有以下类：

| [Layer](http://www.mathworks.com/help/nnet/ref/layer-class.html) | 网络层 |
| --- | --- |

### 9.2.1 网络层：layer

### 描述
网络层类，包含层信息。卷积神经网络架构中的每一层都是 `Layer` 类。

### 构建
要定义卷积神经网络的架构，可以直接创建一个层向量。

### 拷贝语义
值（Value）。若要了解值类如何影响拷贝操作，请参考以下段落：

#### 两种拷贝行为
MATLAB^® 对象有两种基本类型——句柄（handles）和值（values）。

`Value` 对象在拷贝操作方面的表现类似于 MATLAB 基本类型。拷贝是独立的值。你在其中一个对象上执行的操作不会影响该对象的拷贝。

`Handle` 对象通过其句柄变量进行引用。句柄变量的拷贝指向同一个对象。你在句柄对象上执行的操作在所有引用该对象的句柄变量中都是可见的。

#### 值对象的拷贝行为
MATLAB 数值变量是值对象。例如，当将 `a` 拷贝到变量 `b` 时，两个变量是相互独立的。更改 `a` 的值不会改变 `b` 的值：

```
a = 8;
b = a;
```

现在重新赋值 `a`。`b` 保持不变：

```
a = 6;
b = 8
```

清除 `a` 不影响 `b`：

```
clear a
b = 8
```

`值对象属性`
存储为值对象属性的值的拷贝行为与数值变量相同。例如，假设 `vobj1` 是一个具有属性 `a` 的值对象：

```
vobj1.a = 8;
```

如果你将 `vobj1` 拷贝到 `vobj2`，然后更改 `vobj1` 属性 `a` 的值，则拷贝对象的属性 `vobj2.a` 的值不受影响：

```
vobj2 = vobj1;
vobj1.a = 5;
vobj2.a = 8
```

#### 句柄对象的拷贝行为
这是一个名为 `HdClass` 的句柄类，它定义了一个名为 `Data` 的属性。

```class
classdef HdClass < handle
  properties
      Data
  end
  methods
      function obj = HdClass(val)
        if nargin > 0
          obj.Data = val;
        end
      end
  end
end
```

创建该类的对象：

```
hobj1 = HdClass(8)
```

由于该语句没有以分号结束，MATLAB 会显示有关对象的信息：

```
hobj1 = HdClass with properties
  Data: 8
```

变量 `hobj1` 是引用该对象的句柄。将 `hobj1` 拷贝到 `hobj2` 会导致产生另一个指向相同对象的句柄：

```
hobj2 = hobj1
hobj2 = HdClass with properties
  Data: 8
```

由于句柄引用对象，拷贝句柄会将句柄拷贝到一个新名称，但句柄仍然指向同一个对象。例如，假设 `hobj1` 是一个具有属性 `Data` 的句柄对象：

```
hobj1.Data = 8
```

更改 `hobj1` 的 `Data` 属性值，则拷贝对象的 `Data` 属性值也会随之改变：

```
hobj1.Data = 5;
hobj2.Data = 5
```

由于 `hobj2` 和 `hobj1` 是指向同一个对象的句柄，更改拷贝对象 `hobj2` 也会改变你通过 `hobj1` 访问的数据：

```
hobj2.Data = 17;
hobj1.Data = 17
```

#### 重新赋值句柄变量
重新赋值句柄变量产生的结果与重新赋值任何变量相同。当你创建一个对象并将其赋值给 `hobj1` 时：

```
hobj1 = HdClass(34);
```

`hobj1` 引用的是新对象，而不是之前的（且被 `hobj2` 引用的）对象。

#### 清除句柄变量
当从工作区清除一个句柄时，MATLAB 会移除变量，但不会移除被其他句柄引用的对象。然而，如果没有对对象的引用，MATLAB 将销毁该对象。

给定 `hobj1` 和 `hobj2`，它们都引用同一个对象，你可以清除任何一个句柄而不影响对象：

```
hobj1.Data = 8;
clear hobj1
hobj2 = HdClass with properties
  Data: 256
```

如果你同时清除 `hobj1` 和 `hobj2`，则对该对象没有引用了。MATLAB 会销毁该对象并释放其使用的内存。

#### 删除句柄对象
要移除被任意数量句柄引用的对象，请使用 [`delete`](http://www.mathworks.com/help/matlab/ref/delete.html)。给定两个指向相同对象的 `hobj1` 和 `hobj2`，删除其中任一句柄。MATLAB 会删除该对象：

```
hobj1 = HdClass(8);
hobj2 = hobj1;
delete(hobj1)
hobj2 = handle to deleted HdClass
```

使用 `clear` 从工作区移除变量。

#### 修改对象
当将对象传递给函数时，MATLAB 会将对象的拷贝传递到函数工作区。如果函数修改了该对象，MATLAB 只修改函数工作区中的对象拷贝。在这些情况下，句柄类和值类之间的拷贝行为差异是重要的：

- `值对象` —— 函数必须返回修改后的对象拷贝。若要修改调用者工作区中的对象，请将函数的输出赋值给同名的变量
- `句柄对象` —— 函数工作区中的拷贝指向同一个对象。因此，函数不需要返回修改后的拷贝。

#### 测试句柄类或值类
要确定对象是否为句柄对象，请使用 [`isa`](http://www.mathworks.com/help/matlab/ref/isa.html) 函数。如果 `obj` 是某个类的对象，此语句将确定 `obj` 是否为句柄：

```
isa(obj,'handle')
```

例如，`containers.Map` 类创建一个句柄对象：

```
hobj = containers.Map({'Red Sox','Yankees'},{'Boston','New York'});
isa(hobj,'handle')
ans = 1
```

`hobj` 也是一个 `containers.Map` 对象：

```
isa(hobj,'containers.Map')
ans = 1
```

查询 `hobj` 的类显示它是一个 `containers.Map` 对象：

```
class(hobj)
ans = containers.Map
```

[`class`](http://www.mathworks.com/help/matlab/class) 函数返回对象的特定类。

#### 索引
你可以通过对层向量进行索引并使用点符号来访问网络架构中层的属性。例如，图像输入层是卷积神经网络的第一层。要访问图像输入层的 `InputSize` 属性，请使用 `layers(1).InputSize`。

### 示例：

#### 构建网络架构
定义用于分类的卷积神经网络架构，只有一个卷积层、一个 ReLU 层和一个全连接层。

```
cnnarch = [
      imageInputLayer([28 28 3])
      convolution2dLayer([5 5],10)
      reluLayer()
      fullyConnectedLayer(10)
      softmaxLayer()
      classificationLayer()
];
```

或者，你可以单独创建层然后将它们连接。

```
input = imageInputLayer([28 28 3]);
conv = convolution2dLayer([5 5],10);
relu = reluLayer();
fcl = fullyConnectedLayer(10);
sml = softmaxLayer();
col = classificationLayer();
cnnarch = [input;conv;relu;fcl;sml;col];
```





`cnnarch` 是一个包含 6 个层的向量。

显示此层向量的类信息。

```matlab
class (cnnarch)
  nnet.cnn.layer.Layer
```

`cnnarch` 是一个 `Layer` 对象。

## 在层数组中访问层和属性

定义一个用于分类的卷积神经网络架构，仅包含一个卷积层、一个 ReLU 层和一个全连接层。

```matlab
layers = [imageInputLayer([28 28 3])
      convolution2dLayer([5 5],10)
      reluLayer()
      fullyConnectedLayer(10)
      softmaxLayer()
      classificationLayer()];
```

显示图像输入层。

```matlab
layers(1)
```
ans =

  ImageInputLayer with properties:

              Name: ''
          InputSize: [28 28 3]
    DataAugmentation: 'none'
      Normalization: 'zerocenter'

提取输入尺寸。

```matlab
layers(1).InputSize
```
ans =
    28    28     3

显示卷积层的步长。

```matlab
layers(2).Stride
```
ans =
     1     1

访问全连接层的偏置学习率因子。

```matlab
layers(4).BiasLearnRateFactor
```
ans =
    1

## 创建典型的卷积神经网络架构

创建一个用于分类的卷积神经网络，包含两个卷积层和两个全连接层。使用 2x2 不重叠池化区域的最大池化层对卷积层进行下采样。使用修正的线性单元作为卷积层和全连接层的非线性激活函数。对前两个卷积层使用局部响应归一化。第一个卷积层有 12 个 4x3 滤波器，第二个卷积层有 16 个 5x5 滤波器。第一个全连接层有 100 个神经元。假设输入数据为 28x28 的灰度图像，有 10 个类。为每个层分配一个名称。

```matlab
layers = [imageInputLayer([28 28 1],'Normalization','none','Name','inputl')
      convolution2dLayer([4 3],12,'NumChannels',1,'Name','conv1')
      reluLayer('Name','relu1')
      crossChannelNormalizationLayer(4,'Name','cross1')
      maxPooling2dLayer(2,'Stride',2,'Name','max1')
      convolution2dLayer(5,16,'NumChannels',12,'Name','conv2')
      reluLayer('Name','relu2');
      crossChannelNormalizationLayer(4,'Name','cross2')
      maxPooling2dLayer(2,'Stride',2,'Name','max2')
      fullyConnectedLayer(256,'Name','full1')
      reluLayer('Name','relu4')
      fullyConnectedLayer(10,'Name','full2')
      softmaxLayer('Name','softm')
      classificationLayer('Name','out')];
```

## 9.3 TRAIN NETWORKS. CLASSES

MATLAB 拥有以下类：

| 类 |  |
| --- | --- |
| [SeriesNetwork](http://www.mathworks.com/help/nnet/ref/seriesnetwork-class.html) | 串网络类 |
| [TrainingOptionsSGDM](http://www.mathworks.com/help/nnet/ref/trainingoptionssgdm-class.html) | 带动量的随机梯度下降的训练选项 |

### 9.3.1 串网络类: SeriesNetwork

**描述**

一个包含训练后网络中层的串网络类。串网络是层按顺序排列的网络。它有一个单一输入和一个输出。

**构造**

```matlab
trainedNet = trainNetwork(X,Y,layers,options) 返回一个训练后的网络。`trainedNet` 是一个 `SeriesNetwork` 对象。
```
训练卷积神经网络的更多信息，请参阅 [trainNetwork](http://www.mathworks.com/help/nnet/ref/trainnetwork.html)。

**输入参数**

- **X** — 图像：4 维数组
- **Y** — 类标签：分类响应数组
- **layers** — 网络层：`Layer` 对象
- **options** — 训练选项

**方法**

| 方法 | 描述 |
| --- | --- |
| [activations](http://www.mathworks.com/help/nnet/ref/seriesnetwork.activations.html) | 计算层激活值 |
| [classify](http://www.mathworks.com/help/nnet/ref/seriesnetwork.classify.html) | 使用训练后的网络分类数据 |
| [predict](http://www.mathworks.com/help/nnet/ref/seriesnetwork.predict.html) | 使用训练后的网络预测响应 |

**拷贝语义**

关于值如何影响拷贝，请参阅上文。

**示例：构造并训练卷积网络**

加载样本数据。

```matlab
XTrain,TTrain= digit4DArray;
```
`digit4DArray` 加载数字数据集为 4 维数组。`XTrain` 是 28x28x1x4940 数组，28 是高度，28 是宽度，1 是通道数，4940 是数字。`TTrain` 是包含每个观测标签的分类向量。

构造卷积网络。

```matlab
layers = [imageInputLayer([28 28 1]);
      convolution2dLayer(5,20);
      reluLayer();
      maxPooling2dLayer(2,'Stride',2);
      fullyConnectedLayer(10);
      softmaxLayer();
      classificationLayer()];
```

设置带动量的随机梯度下降默认选项。

```matlab
options = trainingOptions('sgdm');
```

训练网络。

```matlab
net = trainNetwork(XTrain,TTrain,layers,options);
```

| Epoch | 迭代 | 用时间 (秒) | 小批量损失 | 准确率 | 基础率 |
| --- | --- | --- | --- | --- | --- |
| 2 | 50 | 0 | 2.231 | 47.6% | 0.1000 |
| 3 | 100 | 0 | 0.83 | 98.0% | 0.1000 |
| 4 | 150 | 0 | 0.558 | 82.3% | 0.1000 |
| 5 | 200 | 0 | 0.423 | 89.06% | 0.1000 |
| 6 | 250 | 0 | 0.368 | 91.41% | 0.1000 |
| 7 | 300 | 0 | 0.336 | 88.28% | 0.1000 |
| 8 | 350 | 0 | 0.2589 | 96.09% | 0.1000 |
| 9 | 400 | 0 | 0.1396 | 98.44% | 0.1000 |
| 10 | 450 | 0 | 0.1802 | 96.09% | 0.1000 |
| 14 | 500 | 0 | 0.0892 | 99.22% | 0.1000 |
| 15 | 550 | 0 | 0.1221 | 96.88% | 0.1000 |
| 16 | 600 | 0 | 0.08 | 98.4% | 0.1000 |
| 18 | 650 | 0 | 0.087 | 99.2% | 0.1000 |
| 19 | 700 | 0 | 0.061 | 100% | 0.1000 |
| 20 | 750 | 0 | 0.052 | 99.2% | 0.1000 |
| 22 | 800 | 0 | 0.048 | 99.06% | 0.1000 |
| 23 | 850 | 0 | 0.051 | 99.2% | 0.1000 |
| 24 | 900 | 0 | 0.044 | 100% | 0.1000 |
| 25 | 950 | 0 | 0.041 | 100% | 0.1000 |
| 27 | 1000 | 0 | 0.053 | 100% | 0.1000 |
| 28 | 1050 | 0 | 0.05 | 100% | 0.1000 |
| 29 | 1100 | 0 | 0.046 | 100% | 0.1000 |

在测试集上运行训练后的网络并预测图像标签（数字）。

```matlab
XTest,TTest= digitTest4DArray;

YTest = classify(net,XTest);
```

计算准确率。

```matlab
accuracy = sum(YTest == TTest)/numel(TTest)
```

0.9929





在 R2016a 中保存的卷积神经网络模型只能通过 GPU 加载，因为在 R2016a 中，可学习参数存储为 `gpuArrays`。一旦加载了模型，你可以在 R2016b 中重新保存它。这会将可学习参数保存为 MATLAB 数组。你可以在运行网络时将执行环境更改为 CPU。

## 9.3.2 带动量的随机梯度下降的训练选项。`TrainingOptionsSGDM`

### 描述
该类包含动量随机梯度下降的训练选项，例如学习率信息、L2 正则化因子和小批量（mini-batch）大小。

### 构造
`options = trainingOptions([solverName](http://www.mathworks.com/help/nnet/ref/trainingoptionssgdm-class.html#inputarg_solverName))` 返回由 `solverName` 指定的求解器的训练选项。

`options = trainingOptions([solverName](http://www.mathworks.com/help/nnet/ref/trainingoptionssgdm-class.html#inputarg_solverName),Name,Value)` 返回一组训练选项，并由一个或多个 `Name,Value` 对参数指定额外的选项。

### 输入参数
- `solverName` — 用于训练网络的求解器（默认值） | `'sgdm'`

### 属性
- `Momentum` — 上一个梯度步的贡献， 0 到 1 之间的标量值
- `InitialLearnRate` — 初始学习率，标量值
- `LearnRateScheduleSettings` — 学习率调度设置，由用户结构指定
- `L2Regularization` — L2 正则化因子，标量值
- `MaxEpochs` — 最大迭代轮数（epochs），整数值
- `MiniBatchSize` — 小批量大小，整数值
- `Verbose` — 显示训练进度信息的指示器 1（默认值） | 0

### 拷贝语义
值（Value）。要了解值类如何影响拷贝操作，请参阅之前的类文档。

### 示例。指定训练选项
创建一组用于带动量随机梯度下降训练的选项。学习率每隔 5 个 epoch 减少 0.2 倍。训练将持续 20 个 epoch，每次迭代将使用包含 300 个观测值的小批量。

```matlab
options = trainingOptions('sgdm',...
      'LearnRateSchedule','piecewise',...
      'LearnRateDropFactor',0.2,... 
      'LearnRateDropPeriod',5,... 
      'MaxEpochs',20,... 
      'MiniBatchSize',300);
```

## 9.4 构建网络架构。层
MATLAB 拥有以下类：

| [`ImageInputLayer](http://www.mathworks.com/help/nnet/ref/imageinputlayer-class.html)` | 图像输入层 |
| --- | --- |
| [`Convolution2DLayer](http://www.mathworks.com/help/nnet/ref/convolution2dlayer-class.html)` | 卷积层 |
| [`ReLULayer](http://www.mathworks.com/help/nnet/ref/relulayer-class.html)` | 修正线性单元 (ReLU) 层 |
| `CrossNormalizationLayer` | 通道级局部响应层 |
| [`AveragePooling2DLayer](http://www.mathworks.com/help/nnet/ref/averagepooling2d-class.html)` | 平均池化层 |
| [`MaxPooling2DLayer](http://www.mathworks.com/help/nnet/ref/maxpooling2d-class.html)` | 最大池化层 |
| [`FullyConnectedLayer](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer-class.html)` | 全连接层 |
| [`DropoutLayer](http://www.mathworks.com/help/nnet/ref/dropoutlayer-class.html)` | 丢弃层 |
| [`SoftmaxLayer](http://www.mathworks.com/help/nnet/ref/softmaxlayer-class.html)` | Softmax 层 |
| [`ClassificationOutputLayer](http://www.mathworks.com/help/nnet/ref/classificationoutputlayer-class.html)` | 分类输出层 |

## 9.4.1 ImageInputLayer 类

### 描述
包含输入尺寸、数据变换和层名的图像输入层。

### 构造
`inputlayer = imageInputLayer([inputSize](http://www.mathworks.com/help/nnet/ref/imageinputlayer-class.html#inputarg_inputSize))` 返回一个图像输入层。

`inputlayer = imageInputLayer([inputSize](http://www.mathworks.com/help/nnet/ref/imageinputlayer-class.html#inputarg_inputSize),Name,Value)` 返回一个图像输入层，并由一个或多个 `Name,Value` 对参数指定额外的选项。

有关键值对参数的更多信息，请参阅 `imageInputLayer`。

### 输入参数
- `inputSize` — 输入数据的尺寸，两个或三个数字的行向量

### 属性
- `inputSize` — 三个整数的输入数据行向量
- `DataAugmentation` — 数据增强变换 `'none'`（默认值） | `'randcrop'` | `'randplr'` | `'randcrop'` 和 `'randplr'` 的单元格数组
- `Normalization` — 数据变换 `'zerocenter'`（默认值） | `'none'`
- `Name` — 层名 `''`（默认值） | 字符向量

### 示例：创建并显示输入层
为 28x28 的彩色图像创建一个图像输入层。指定一个用于 28x28 彩色图像的图像输入层。

```matlab
inputlayer = imageInputLayer([28 28 3],'DataAugmentation','randplr');
inputlayer = 
  ImageInputLayer with:
      Name: ''
      InputSize: 28 28 3
    DataAugmentation: 'randplr'
    Normalization: 'zerocenter'

显示输入尺寸。
inputlayer.InputSize
ans =
    28  28  3
```

## 9.4.2 Convolution2D 类

### 描述
包含包含尺寸、通道数、层名、权重和偏置的卷积层。

### 构造
`convlayer = convolutional2dLayer([filterSize](http://www.mathworks.com/help/nnet/ref/convolution2dlayer-class.html#inputarg_filterSize),[numFilters](http://www.mathworks.com/help/nnet/ref/convolution2dlayer-class.html#inputarg_numFilters))` 返回一个用于 2D 卷积的层。

`convlayer = convolutional2dLayer([filterSize](http://www.mathworks.com/help/nnet/ref/convolution2dlayer-class.html#inputarg_filterSize),[numFilters](http://www.mathworks.com/help/nnet/ref/convolution2dlayer-class.html#inputarg_numFilters),Name,Value)` 返回卷积层，并由一个或多个 `Name,Value` 对指定额外的选项。

有关更多详情，请参阅 `convolution2dLayer(http://www.mathworks.com/help/nnet/ref/convolution2dlayer.html)` 函数页面。

### 输入参数
- `filterSize` — 过滤器的高度和宽度，整数 | 两个值的向量
- `numFilters` — 过滤器数量，整数

### 属性
- `Stride` — 遍历输入的步长 `[1 1]`（默认值） | 两个值的向量
- `Padding` — 应用于边界的零填充 `[0 0]`（默认值） | 两个值的向量
- `NumChannels` — 过滤器的通道数 `'auto'`（默认值） | 整数
- `Weights` — 层的 4D 数组
- `Bias` — 层的 3D 数组
- `WeightLearnRate` — 权重的学习率，标量值
- `WeightL2Factor` — 权重的 L2 正则化因子，标量值
- `BiasLearnRate` — 偏置的学习率，标量值
- `BiasL2Factor` — 偏置的 L2 正则化因子，标量值
- `Name` — 层名 `''`（默认值） | 字符向量

### 示例 创建卷积层
创建一个具有 96 个过滤器的卷积层，高度和宽度为 11，并在水平和垂直方向上使用步长为 4。

```matlab
convlayer = convolutional2dLayer(11,96,'Stride',4)
convlayer = 
  Convolution2DLayer with properties:
      Name: ''
      FilterSize: [11 11]
      NumChannels: 'auto'
      NumFilters: 96
    Stride: [4 4]
    Padding: [0 0]
    Weights: []
    Bias: []
    WeightLearnRate: 1
    WeightL2Factor: 1
    BiasLearnRate: 1
    BiasL2Factor: 0
```

你可以通过对对象索引来单独显示任何属性。例如，显示过滤器尺寸。

```matlab
convlayer.FilterSize
ans =
    11  11
```





# Description
整流线性单元（ReLU）层类，包含层的名称。ReLU 层执行阈值操作，其中任何小于零的输入值都被设置为零，即

![](img/00126.jpeg)

# 构造函数
`layer = relu()` 返回一个 ReLU 层。

`layer = reluLayer(Name,Value)` 返回一个 ReLU 层，并通过 `Name,Value` 对参数指定额外的选项。

# 属性
**Name — 层名称 ''（默认值） | 字符向量**
层名称，存储为字符向量。如果 `Name` 设置为 `''`，则软件将在训练时自动分配一个名称。

**数据类型：`char`**

# 示例
**使用指定名称创建 ReLU 层**
创建一个名称为 `relu1` 的整流线性单元层。

```matlab
layer = reluLayer('Name','relu1');
```

## 9.4.4 CrossChannelNormalizationLayer 类

### 描述
通道级局部响应归一化层类，包含通道窗口的大小、归一化的化的超参数以及层的名称。

### 构造函数
`localnormlayer = crossChannelNormalizationLayer([windowChannelSize])` 返回一个局部响应归一化层，该层执行通道级归一化。

`localnormlayer = crossChannelNormalizationLayer([windowChannelSize],Name,Value)` 返回一个局部响应归一化层，通过一个或多个 `Name,Value` 对参数指定额外的选项。

有关名称值对参数的更多细节，请参见 `crossChannelNormalizationLayer`。

### 输入参数
**windowChannelSize — 通道窗口的大小正整数**

### 属性
**windowChannelSize — 通道窗口的大小正整数**
**Alpha — 归一化标量值中的 α 超参数**
**Beta — 归一化中的 β 超参数 0.75（默认） | 标量值**
**K — 归一化中的 K 超参数 2（默认） | 标量值**
**Name — 层名称 ''（默认） | 字符向量**

### 示例
**创建局部响应归一化层**
创建一个用于通道级归一化的局部响应归一化层，其中使用 5 个通道的窗口来归一化每个元素，归一化器的加法常数为 1。

```matlab
localnormlayer = crossChannelNormalizationLayer(5,'K',1);

localnormlayer = 
  CrossChannelNormalizationLayer with properties:
     WindowChannelSize: 5
     Alpha: 1.0000e-04
     Beta: 0.7500
     K: 1
     Name: ''
```

## 9.4.5 AveragePooling2DLayer 类

### 描述
平均池化层类，包含池大小、步长、填充和层的名称。平均池化层通过将输入划分为矩形池化区域并计算每个区域的平均值执行下采样。它返回池化区域的平均值。池化区域的大小由 `averagePooling2dLayer` 函数的 `poolSize` 参数决定。

### 构造函数
`avgpoollayer = averagePooling2dLayer([poolSize])` 创建一个执行平均池化的层。`poolSize` 指定矩形区域的维度。

`avgpoollayer = averagePooling2dLayer([poolSize], Name,Value)` 创建平均池化层，通过一个或多个 `Name,Value` 对参数指定额外的选项。

有关更多细节，请参见 `averagePooling2dLayer`。

### 输入参数
**poolSize — 池化区域的高度和宽度标量值 | 两个标量值的向量**

### 属性
**PoolSize — 池化区域的高度和宽度的标量 | 两个标量值的向量**
**Stride — 遍历输入的步长 [1 1]（默认） | 两个标量值的向量**
**Padding — 应用于输入边界的零填充大小 [0 0]（默认） | 两个标量值的向量**
**Name — 层名称 ''（默认） | 字符向量**

### 示例
**创建不重叠的平均池化层**
创建一个具有不重叠池化区域的平均池化层。将该层下采样因子设置为 2。

```matlab
avgpoollayer = averagePooling2dLayer(2,'Stride',2)

avgpoollayer = 
  AveragePooling2Layer with properties:
     PoolSize: [2 2]
     Stride: [2 2]
     Padding: [0 0]
     Name: ''
```

**创建重叠的平均池化层**
创建一个具有重叠池化区域的平均池化层。将该层下采样因子设置为 2。

```matlab
avgpoollayer = averagePooling2dLayer(3,'Stride',2,'Padding',1,'Name','avg1')

avgpoollayer = 
  AveragePooling2Layer with properties:
     PoolSize: [3 2]
     Stride: [2 2]
     Padding: [1 0]
     Name: 'avg1'
```
矩形区域的高度和宽度为 3。因为步长为 2，所以池化区域是重叠的。`Padding` 的值为 1 会在输入的顶部添加一行零。`0` 表示在输入的左右侧不添加填充。你可以通过点表示法显示任何属性。显示层的名称。

```matlab
avgpoollayer.Name
ans =
avg1
```

## 9.4.6 MaxPooling2DLayer 类

### 描述
最大池化层类，包含池大小、步长、填充和层的名称。最大池化层通过将输入划分为矩形池化区域并计算每个区域的最大值执行下采样。池化区域的大小由 `maxPooling2dLayer` 函数的 `poolSize` 参数决定。

### 构造函数
`maxpoollayer = maxPooling2dLayer([poolSize])` 返回一个执行最大池化的层。`poolSize` 指定池化区域的维度。

`maxpoollayer = maxPooling2dLayer([poolSize],Name,Value)` 返回最大池化层，通过一个或多个 `Name,Value` 对参数指定额外的选项。

有关名称值对参数的更多细节，请参见 `maxPooling2dLayer`。

### 输入参数
**poolSize — 池化区域的高度和宽度标量值 | 两个标量值的向量**

### 属性
**PoolSize — 池化区域的高度和宽度标量 | 两个标量值的向量**
**Stride — 遍历输入的步长 [1 1]（默认） | 两个标量值的向量**
**Padding — 应用于输入边界的填充大小 [0,0]（默认） | 两个标量值的向量**
**Name — 层名称 ''（默认） | 字符向量**





## 示例

### 非重叠池化区域的最大池层

创建一个具有非重叠池化区域的最大池层，采样倍率为 2。

```matlab
maxpoollayer = maxPooling2dLayer(2,'Stride',2);
```

`maxpoollayer` = 

`MaxPooling2DLayer` 属性：
    PoolSize: [2 2]
      Stride: [2 2]
    Padding: [0 0]
        Name: ''

矩形区域（池化大小）的高度和宽度均为 2。该层创建大小为 `[2 2]` 的池化区域，并返回每个区域四个元素中的最大值。由于垂直和水平遍历图像的步长（stride）也是 `[2 2]`，因此池化区域不重叠。

### 重叠池化区域的最大池层

创建一个具有重叠池化区域的最大池层。同时对输入的顶部和底部添加填充。

```matlab
maxpoollayer = maxPooling2dLayer([3 2],'Stride',2,...
  'Padding',[1 0],'Name','max1');
```

`maxpoollayer` = 

`MaxPooling2DLayer` 属性：
    PoolSize: [3 2]
      Stride: [2 2]
    Padding: [1 0]
        Name: 'max1'

矩形区域（池化大小）的高度和宽度分别为 3 和 2。该层创建大小为 `[3 2]` 的池化区域，并返回每个区域六个元素中的最大值。由于垂直和水平遍历图像的步长（stride）为 `[2 2]`，池化区域存在重叠。

`Padding` 名称值对值中的 `1` 表示软件也会在输入数据的顶部和底部添加填充。`0` 表示不对输入数据的右侧和左侧添加填充。

你可以通过对对象索引来显示任何属性。显示层的名称。

```matlab
maxpoollayer.Name 
ans =
max1
```

## 9.4.7 FullyConnectedLayer 类

### 描述

包含输入和输出大小、层名称以及权重和偏置数据的全连接层类。

### 构造

`fullconnectlayer` = `fullyConnectedLayer([outputSize])` 返回一个全连接层，其中软件将输入乘以矩阵然后加上偏置向量。

`fullconnectlayer` = `fullyConnectedLayer([outputSize],Name,Value)` 返回全连接层，通过一个或多个 `Name,Value` 名称值对参数指定额外选项。

有关名称值对参数的更多细节，请参阅 `fullyConnectedLayer`。

### 输入参数

- **outputSize** — 全连接层输出的整数值

### 属性

- **InputSize** — 层输入大小，正整数 | `'auto'`
- **OutputSize** — 层输出大小，正整数
- **Weights** — 层权重 `OutputSize`-by-`InputSize` 矩阵
- **Bias** — 层偏置 `OutputSize`-by-1 矩阵
- **WeightLearnRateFactor** — 权重的学习率因子，标量值
- **WeightL2Factor** — 权重 L2 正则化因子，标量值
- **BiasLearnRateFactor** — 偏置的学习率因子，标量值
- **BiasL2Factor** — 偏置的 L2 正则化因子，标量值
- **Name** — 层名称 `''`（默认） | 字符向量

### 示例：创建全连接层

创建一个输出大小为 10 的全连接层。

```matlab
fullclayer = fullyConnectedLayer(10)
```

`fullclayer` = 

`FullyConnectedLayer` 属性：
            Weights: []
            Bias: []
    WeightLearnRateFactor: 1
    WeightL2Factor: 1
    BiasLearnRateFactor: 1
        BiasL2Factor: 0
            InputSize: 'auto'
    OutputSize: 10

软件确定输入大小。

## 9.4.8 DropoutLayer

### 描述

包含丢弃概率和层名称的丢弃层。

### 构造

`droplayer` = `DropoutLayer()` 返回一个丢弃层，随机丢弃元素。

`droplayer` = `DropoutLayer([probability])` 返回丢弃层，通过 `Name,Value` 名称值对指定额外选项。

### 输入参数

- **probability** — 丢弃概率，默认 0.5

### 属性

- **Probability** — 丢弃概率
- **Name** — 层名称 `''`（默认） | 字符向量

### 示例：创建丢弃层

创建一个丢弃 40% 元素的丢弃层。

```matlab
droplayer = DropoutLayer(0.4,'Name','dropout1')
```

`droplayer` = 

`DropoutLayer` 属性：
    Probability: 0.4
    Name: 'dropout1'

## 9.4.9 SoftmaxLayer 类

### 描述

使用 softmax 激活函数的 softmax 层。适用于超过 2 类的分类问题。

### 构造

`smlayer` = `SoftmaxLayer()` 返回用于分类问题的 softmax 层。

`smlayer` = `SoftmaxLayer('Name',layername)` 返回 softmax 层，通过 `Name,Value` 名称值对指定额外选项。

### 属性

- **Name** — 层名称 `''`（默认） | 字符向量

### 示例：创建指定名称的 Softmax 层

创建一个名为 `sml1` 的 softmax 层。

```matlab
smlayer = SoftmaxLayer('Name','sml1')
```

## 9.4.10 ClassificationOutputLayer 类

### 描述

分类输出层，包含用于训练网络的损失函数名称、输出大小以及类别标签。

### 构造

`classoutputlayer` = `ClassificationOutputLayer()` 返回神经网络的分类输出层。

`classoutputlayer` = `ClassificationOutputLayer(Name,Value)` 返回分类输出层，通过 `Name,Value` 名称值对指定额外选项。

### 属性

- **OutputSize** — 输出大小，标量值
- **LossFunction** — 用于训练的损失函数 `'crossentropyex'`
- **ClassNames** — 类别名称，训练前为空单元格数组 | 训练后的类别名称单元格数组
- **Name** — 层名称 `''`（默认） | 字符向量

### 示例：创建分类输出层

创建一个名为 `'coutput'` 的分类输出层。

```matlab
coutputlayer = ClassificationOutputLayer('Name','coutput')
```

`coutputlayer` = 

`ClassificationOutputLayer` 属性：
    OutputSize: 'auto'
    LossFunction: 'crossentropyex'
    ClassNames: {}
    Name: 'coutput'

### 定义：针对 k 类互斥类的交叉熵函数

对于多分类问题，软件将每个输入分配给 *k* 个互斥类之一。这种情况下的损失（误差）函数是 1-of-*k* 编码方案的交叉熵函数：





![](img/00136.jpeg)

输出单元激活函数是 softmax 函数：

![](img/00137.jpeg)

# 第 10 章 使用深度学习进行图像分类

## 10.1 概述

卷积神经网络（CNN）是深度学习领域一种强大的机器学习技术。CNN 使用大量多样化的图像集合进行训练。通过这些庞大的集合，CNN 可以学习到各种图像的丰富特征表示。这些特征表示的性能通常优于 `HOG`、`LBP` 或 `SURF` 等手工特征。要利用 CNN 的力量而无需投入大量时间和精力进行训练，的一种简单方法是使用预训练的 CNN 作为特征提取器。

在本示例中，我们将来自 Caltech 101 的图像通过使用从图像中提取的 CNN 特征训练的多分类线性 SVM 进行分类。这种图像类别分类方法遵循了标准做法，即使用从图像中提取的特征来训练现成的分类器。例如，“使用特征袋的图像类别分类”示例在特征袋框架内使用 `SURF` 特征来训练多分类 SVM。此处的不同之处在于，我们不是使用 `HOG` 或 `SURF` 等图像特征，而是使用 CNN 提取特征。而且正如本示例所示，使用 CNN 特征训练的分类器提供了接近 100% 的准确率，这高于使用特征袋和 `SURF` 的准确率。

注意：此示例需要 Computer Vision System Toolbox™、Image Processing Toolbox™、Neural Network Toolbox™、Parallel Computing Toolbox™、Statistics and Machine Learning Toolbox 以及计算能力为 3.0 或更高的支持 CUDA 的 NVIDIA™ GPU。

```matlab
function DeepLearningImageClassificationExample
```

## 10.2 检查系统要求

建议使用计算能力为 3.0 或更高的支持 CUDA 的 NVIDIA™ GPU 来运行此示例。查询 GPU 设备以检查其是否可以运行此示例：

```matlab
% 获取 GPU 设备信息
deviceInfo = gpuDevice;

% 检查 GPU 计算能力
computeCapability = str2double(deviceInfo.ComputeCapability);
assert(computeCapability > 3.0, ...
    '此示例需要计算能力为 3.0 或更高的 GPU 设备。')
```

## 10.3 下载图像数据

类别分类器将在来自 [Caltech 101](http://www.vision.caltech.edu/Image_Datasets/Caltech101) 的图像上训练。Caltech 101 是引用和使用最广泛的数据集之一，由 Fei-Fei Li、Marco Andreetto 和 Marc 'Aurelio Ranzato 收集。

```matlab
% 从以下位置下载压缩数据集
url = 'http://www.vision.caltech.edu/Image\_Datasets/Caltech101/101_ObjectCategories.tar.gz';

% 将输出存储在临时文件夹中
outputFolder = fullfile(tempdir, 'caltech101'); % 定义输出文件夹
```

注意：数据的下载时间取决于您的网络连接。后续命令将使用 MATLAB 下载数据并阻塞 MATLAB。或者，您可以使用网络浏览器先将数据集下载到本地磁盘。要使用您从网络下载的文件，请将上方的 `outputFolder` 变量更改下载文件的位置。

```matlab
if ~exist(outputFolder, 'dir') % 仅下载一次
    disp('正在下载 126MB Caltech101 数据集...');
    untar(url, outputFolder);
end
```

## 10.4 加载图像

与其对整个 Caltech 101 进行操作（这非常耗时），不如使用三个类别：飞机（airplanes）、渡轮（ferry）和笔记本电脑（laptop）。图像类别分类器将训练用于区分这三个类别。

```matlab
rootFolder = fullfile(outputFolder, '101_ObjectCategories');
categories = {'airplanes', 'ferry', 'laptop'};
```

创建一个 `ImageDatastore` 来帮助您管理数据。由于 `ImageDatastore` 基于图像文件位置操作，图像在读取之前不会加载到内存中，使其对于处理大型图像集非常高效。

```matlab
imds = imageDatastore(fullfile(rootFolder, categories), 'LabelSource', 'foldernames');
```

变量 `imds` 现在包含了以及与每个图像关联的类别标签。标签根据图像文件的文件夹自动分配。使用 `countEachLabel` 总结每个类别的图像数量。

```matlab
tbl = countEachLabel(imds)
```

```
tbl =
      Label      Count
    ____    ____
    airplanes     800
    ferry          67
    laptop        81
```

由于上述 `imds` 中每个类别的图像数量不相等，让我们先进行调整，使训练集中的图像数量平衡。

```matlab
minSetCount = min(tbl{:,2}); % 确定类别中数量最少的图像
% 使用 splitEachLabel 方法裁剪集合。
imds = splitEachLabel(imds, minSetCount, 'randomize');
```

注意，每个集合现在具有相同数量的图像。

```matlab
countEachLabel(imds)
```

```
ans
      Label      Count
    ____    ____
    airplanes     800
    ferry          67
    laptop        81
```

下面你可以看到这些类别的图像。

```matlab
% 找到每个类的第一个实例
airplanes = find(imds.Labels == 'airplanes', 1);
ferry = find(imds.Labels == 'ferry', 1);
laptop = find(imds.Labels == 'laptop', 1);

figure
subplot(1,3,1); imshow(read(imds,airplanes))
subplot(1,3,2); imshow(read(imds,ferry))
subplot(1,3,3); imshow(read(imds,laptop))
```

## 10.5 下载预训练卷积神经网络 (CNN)

现在图像已经准备就，您需要为此示例下载一个预训练的 CNN。有一些流行的预训练网络。其中大多数是在 ImageNet 数据集上训练的，该数据集包含 1000 个类别和 120 万张图像。“AlexNet”就是其中一个模型。

```matlab
% "AlexNet" 的位置
url = 'http://www.vlfeat.org/matconv/models/caffe.mat';
% 将输出存储在临时文件夹中
cnnMatFile = fullfile(tempdir, 'caffe.mat');
```

注意：数据的下载时间取决于您的网络连接。后续的命令将使用 MATLAB 下载数据并阻塞 MATLAB。或者，您可以使用网络浏览器先将数据集下载到本地磁盘。要使用您从网络下载的文件，请将上方的 `cnnMatFile` 变量更改下载文件的位置。

```matlab
if ~exist(cnnMatFile, 'file')
    disp('正在下载预训练 CNN...');
    websave(cnnMatFile, url);
end
```

## 10.5.1 加载预训练 AlexNet

有一些流行的预训练网络。其中大多数是在 ImageNet 数据集上训练的，该数据集包含 1000 个类别和 120 万张图像。“AlexNet”是其中一个模型，可以使用 `alexnet` 函数加载。`alexnet` 要求您先安装 Neural Network Toolbox。

```matlab
% 加载预训练 AlexNet
net = alexnet()
```

```
net = SeriesNetwork with properties:
    Layers: [25×1 nnet.cnn.Layer]
```

其他在 ImageNet 上训练的流行网络包括 VGG-16 和 VGG-19，它们可以使用 Neural Network Toolbox 中的 `vgg16` 和 `vgg19` 加载。

`net.Layers` 定义了 CNN 的架构。

```matlab
% 查看 CNN 架构
net.Layers
```

```
ans = 25×1 Layer array with layers:
    1 'data' Image Input 227x227x3 images with 'zerocenter' normalization
    2 'conv1' Convolution 96 11x11x3 convolutions with stride [4 4] and padding [0 0]
    3 'relu1' ReLU
    4 'norm1' Cross Channel Normalization cross channel normalization with 5 channels per element
    5 'pool1' Max Pooling 3x3 max pooling with stride [2 2] and padding [0 0]
```




| 索引 | 名称 | 类型 |  |
| :--- | :--- | :--- | :--- |
| 6 | `conv2` | 卷积 | 256 个 5x5x48 卷积，步长为 `[1 1]`，填充为 `[2 2]` |
| 7 | `relu2` | ReLU | ReLU |
| 8 | `norm2` | 通通道归一化 | 每个元素 5 通道的跨通道归一化 |
| 9 | `pool2` | 最大池化 | 3x3 最大池化，步长为 `[2 2]`，填充为 `[0 0]` |
| 10 | `conv3` | 卷积 | 384 个 3x3x256 卷积，步长为 `[1 1]`，填充为 `[1 1]` |
| 11 | `relu3` | ReLU | ReLU |
| 12 | `conv4` | 卷积 | 384 个 3x3x192 卷积，步长为 `[1 1]`，填充为 `[1 1]` |
| 13 | `relu4` | ReLU | ReLU |
| 14 | `conv5` | 卷积 | 256 个 3x3x192 卷积，步长为 `[1 1]`，填充为 `[1 1]` |
| 15 | `relu5` | ReLU | ReLU |
| 16 | `pool5` | 最大池化 | 3x3 最大池化，步长为 `[2 2]`，填充为 `[0 0]` |
| 17 | `fc6` | 全连接 | 4096 全连接层 |
| 18 | `relu6` | ReLU | ReLU |
| 19 | `drop6` | 丢弃 | 50% 丢失率 |
| 20 | `fc7` | 全连接 | 4096 全连接层 |
| 21 | `relu7` | ReLU | ReLU |
| 22 | `drop7` | 丢弃 | 50% 丢失率 |
| 23 | `fc8` | 全连接 | 1000 全连接层 |
| 24 | `prob` | Softmax | softmax |
| 25 | `output` | 分类输出 |  'tench'、'goldfish' 和其他 998 类的交叉熵 |

第一层定义了输入维度。每个 CNN 都有不同的输入尺寸要求。本示例使用的模型需要输入大小为 227x227x3 的图像。

```matlab
% 检查第一层
net.Layers(1)
```

```matlab
ans = 
  ImageInputLayer with properties:
                Name: 'data'
      InputSize: [227 227 3]
  Hyperparameters
    DataAugmentation: 'none'
      Normalization: 'zerocenter'
```

中间层构成了 CNN 的大部分。它们是一系列卷积层，之间穿插着线性整流单元（ReLU）和最大池化层 [2]。在这些层之后是 3 个全连接层。

最后一层是分类层，其属性取决于任务。在本示例中，加载的 CNN 模型是为解决 1000 类分类而训练的。因此，分类层包含来自 ImageNet 数据集的 1000 个类。

```matlab
% 检查最后一层
net.Layers(end)
```

```matlab
% ImageNet 任务的类名称数量
numel(net.Layers(end).ClassNames)
```

```matlab
ans = 
  ClassificationOutputLayer with properties:
    Name: 'output'
    ClassNames: {1x100}
    OutputSize: 100
  Hyperparameters
    LossFunction: 'crossentropy'
```

注意，该 CNN 模型将不再用于原始任务。它将被重新定位，用于解决 Caltech 101 数据集上的不同分类任务。

# 加载预训练 CNN

CNN 模型以 MatNet 格式保存。将 MatNet 网络数据加载到 `convnet` 中，这是一个通过辅助函数 `helperImportConvNet` 的 `SeriesNetwork` 对象。`SeriesNetwork` 对象可用于检查架构、分类新数据以及从特定层提取激活值。

```matlab
% 将 MatNet 网络加载到 SeriesNetwork
convnet = helperImportConvNet(cnnFile)
```

```matlab
convnet = 
  SeriesNetwork with properties:
    Layers: [23x1 net.cnn.layer]
```

```matlab
% 查看 CNN 架构
convnet.Layers
```

```matlab
ans = 23x1 array with layers:
    1  'input'           Input           27x27x3 图像，带有 'zerocenter' 归一化
    2  'conv1'          Convolution      96 个 1x1x3 卷积，步长为 [4]，填充为 [0]
    3  'relu1'          ReLU            ReLU
    4  'norm1'          Cross Normalization  每个元素 5 通道的跨通道归一化
    5  'pool1'          Max Pooling      3x3 最大池化，步长为 [2]，填充为 [0]
    6  'conv2'          Convolution      256 个 5x5x48 卷积，步长为 [1 1]，填充为 [2 2]
    7  'relu2'          ReLU            ReLU
    8  'norm2'          Cross Normalization  每个元素 5 通道的跨通道归一化
    9  'pool2'          Max Pooling      3x3 最大池化，步长为 [2 2]，填充为 [0 0]
    10 'conv3'          Convolution      384 个 3x3x256 卷积，步长为 [1 1]，填充为 [1 1]
    11 'relu3'          ReLU            ReLU
    12 'conv4'          Convolution      384 个 3x3x192 卷积，步长为 [1 1]，填充为 [1 1]
    13 'relu4'          ReLU            ReLU
    14 'conv5'          Convolution      256 个 3x3x192 卷积，步长为 [1 1]，填充为 [1 1]
    15 'relu5'          ReLU            ReLU
    16 'pool5'          Max Pooling      3x3 最大池化，步长为 [2 2]，填充为 [0 0]
    17 'fc6'           Fully Connected  4096 全连接层
    18 'relu6'          ReLU            ReLU
    19 'drop6'          Dropout         50% 丢失率
    20 'fc7'           Fully Connected  4096 全连接层
    21 'relu7'          ReLU            ReLU
    22 'drop7'          Dropout         50% 丢失率
    23 'fc8'           Fully Connected  1000 全连接层
```

## 10.7 为 CNN 预处理图像

如上所述，`convnet` 只能处理 227x227 的 RGB 图像。为了避免将 Caltech 101 中的所有图像重新保存为此格式，请设置 `imds` 读取函数 `imds.ReadFcn` 来实时预处理图像。每当从 `ImageDatastore` 读取图像时，都会调用 `imds.ReadFcn`。





% 设置 ImageDatastore ReadFcn

```matlab
imds.ReadFcn = @(filename)readAndPreprocessImage(filename);
```

请注意，其他 CNN 模型会有不同的输入大小限制，并且可能需要其他的预处理步骤。

```matlab
    function Iout = readAndPreprocessImage(filename)
        I = imread(filename);
        % 某些图像可能是灰色的。将图像复制 3 次以
        % 创建 RGB 图像。
        if ismatrix(I)
            I = cat(3,I,I,I);
        end
        % 根据 CNN 的要求调整图像大小。
        Iout = imresize(I, [227 227]);
        % 注意，这里没有保持纵比例。在 Caltech 101 中，
        % 感的对象位于图像中心并占据
        % 图像场景的大部分。因此，保持纵比例
        % 并不是关键。然而，对于其他数据集，在缩放时
        % 保持原始图像的纵比例可能会有益。
    end
```

## 10.8 准备训练和测试图像集

将集合分为训练数据和验证数据。从每个集合中选取 30% 的图像作为训练数据，剩余的 70% 作为验证数据。随机化划分以避免结果偏。。训练集和测试集将由 CNN 模型处理。

```matlab
[trainingSet, testSet] = splitEachLabel(imds, 0.3, 'randomize');
```

## 10.9 使用 CNN 提取训练特征

CNN 的每一层都会对输入图像产生响应（或激活）。然而，CNN 内部只有少数几层适用于图像特征提取。网络开头的层捕捉基础图像特征，例如边缘和斑块（blobs）。为了观察这一点，可以可视化第一层卷积层的滤波器权重。这有助于建立一种直觉，即明为什么从 CNN 中提取的特征在图像识别任务中如此有效。请注意，可视化深层权重超出了本示例的范围。你可以在 Zeiler 和 Fergus 的工作 [4] 中阅读更多信息。

```matlab
% 获取第二个卷积层的网络权重
w1 = convnet.Layers(2).Weights;

% 缩放并调整权重大小以便可视化
w1 = mat2gray(w1);
w1 = imresize(w1,5);

% 显示网络权重的蒙太图。第一层有 96 组独立的权重。
figure
montage(w1)
title('First convolutional layer weights')
```

注意网络的第一层如何学习了用于捕捉斑块和边缘特征的滤波器。这些“原始”特征随后由深层网络层处理，这些层组合早期特征形成更高级的图像特征。这些高级特征更适合识别任务，因为它们将所有原始特征组合成更丰富的图像表示 [5]。

你可以使用 `activations` 方法轻松地从其中一个深层层中提取特征。选择哪一个深层是一个设计选择，但通常从紧邻分类层的前的一层开始是一个很好的起点。在 `convnet` 中，该层命名为 'fc7'。让我们使用该层提取训练特征。

```matlab
featureLayer = 'fc7';
trainingFeatures = activations(convnet, trainingSet, featureLayer, ...
    'MiniBatchSize', 32, 'OutputAs', 'columns');
```

注意，如果可用 GPU，`activations` 函数会自动使用 GPU 进行处理，否则使用 CPU。由于 AlexNet 层数较多，强烈建议使用 GPU。使用 CPU 运行网络将极大增加提取特征的时间。

在上面的代码中，'MiniBatchSize' 设置为 32，以确保 CNN 和图像数据适合 GPU 内存。如果你的 GPU 内存溢出，你可能需要降低 'MiniBatchSize'。此外，`activations` 输出排列为列。这有助于加速随后的多类线性 SVM 训练。

# 10.10 使用 CNN 特征训练多类 SVM 分类器

接下来，使用 CNN 图像特征训练多类 SVM 分类器。通过将 `fitcecoc` 函数的 'Learners' 参数设置为 'Linear' 使用快速的随机梯度下降求解器进行训练。这有助于在处理高维 CNN 特征向量时加速训练，每个向量的长度为 4096。

```matlab
% 从 trainingSet 获取训练标签
trainingLabels = trainingSet.Labels;

% 使用快速线性求解器训练多类 SVM 分类器，并将
% 'ObservationsIn' 设置为 'columns' 以匹配训练
% 特征的排列方式。
classifier = fitcecoc(trainingFeatures, trainingLabels, ...
    'Learners', 'Linear', 'Coding', 'onevsall', 'ObservationsIn', 'columns');
```

## 10.11 评估分类器

重复之前使用的步骤从 `testSet` 中提取图像特征。然后可以将测试特征传递给分类器，以衡量已训练分类器的准确性。

```matlab
% 使用 CNN 提取测试特征
testFeatures = activations(convnet, testSet, featureLayer, 'MiniBatchSize',32);

% 将 CNN 图像特征传递给训练好的分类器
predictedLabels = predict(classifier, testFeatures);

% 获取已知标签
testLabels = testSet.Labels;

% 使用混淆矩阵统计结果。
confMat = confusionmat(testLabels, predictedLabels);

% 将混淆矩阵转换为百分比形式
confMat = bsxfun(@rdivide,confMat,sum(confMat,2))
confMat = [1 0 0; 0 1 0; 0 0 1]

% 显示平均准确率
mean(diag(confMat))
ans = 1
```

# 10.12 在测试图像上尝试新分类器

你现在可以使用新训练的分类器对图像进行分类。

```matlab
newImage = fullfile(rootFolder, 'airplanes', 'image_0690.jpg');

% 根据 CNN 要求预处理图像
img = readAndPreprocessImage(newImage);

% 使用 CNN 提取图像特征
imageFeatures = activations(convnet, img, featureLayer);

% 使用分类器进行预测
label = predict(classifier, imageFeatures)
label = airplanes
```

## 10.13 参考文献

[1] Deng, Jia, et al. "Imagenet: A large-scale hierarchical image database." Computer Vision and Pattern Recognition, 2009. CVPR 2009 IEEE Conference on. IEEE, 2009.

[2] Krizhevsky, Alex, Ilya Sutskever, and Geoffrey E. Hinton. "Imagenet classification with deep convolutional neural networks." Advances in neural information processing systems. 2012.

[3] Vedaldi, Andrea, and Karel Lenc. "MatConvNet-convolutional neural networks for MATLAB." arXiv preprint arXiv:1412.4564 (2014).

[4] Zeiler, Matthew D., and Rob Fergus. "Visualizing and understanding convolutional networks." Computer Vision-ECCV 2014. Springer International Publishing, 2014. 818-833.

[5] Donahue, Jeff, et al. "Decaf: A deep convolutional activation feature for generic visual recognition." arXiv preprint arXiv:1310.1531 (2013).




微调一个在数字图像上经过预训练的卷积神经网络，以学习字母图像的特征。迁移学习被认为是在机器学习中将知识从一个已学习的任务转移到新任务的过程 [1]。在神经网络的语境下，它是将预训练网络学习到的特征转移到新问题。当训练数据量不足时，在每个情况下从头开始训练卷积神经网络通常是有效的。深度学习中针对此类情况的常用做法是使用在大型数据集上训练过的网络来处理新问题。虽然预训练网络的初始层可以固定，但最后几层必须进行微调，以学习新数据集的特定特征。迁移学习通常比训练新的卷积神经网络具有更快的训练速度，因为你不需要估计新网络中的所有参数。

**注意：** 训练卷积神经网络需要 Parallel Computing Toolbox™ 和具有计算能力 3.0 或更高的 CUDA® 支持的 NVIDIA® GPU。

将样本数据加载为 `ImageDatastore`。

```matlab
digitDatasetPath = fullfile(matlabroot,'toolbox','nnet','nndemos',...
    'nndatasets','DigitDataset');
digitData = imageDatastore(digitDatasetPath,...
    'IncludeSubfolders',true,'LabelSource','foldernames');
```

数据存储器包含 10000 张数字 0–9 的合成图像。这些图像通过对使用不同字体创建的数字图像应用随机变换。每个数字图像均为 28x28 像素。

显示数据存储器中的部分图像。

```matlab
for i = 1:20
    subplot(4,5,i);
    imshow(digitData.Files{i});
end
```

![描述: http://es.mathworks.com/help/examples/nnet/TransferLearningUsingConvolutionalNeuralNetworksExample_01.png](img/00140.jpeg)

检查每个数字类别图像的数量。

```matlab
digitData.countEachLabel
ans = 
    Label    Count
    ____    ____
    0         988 
    1        1026 
    2        1003 
    3         993 
    4        991 
    5        1017 
    6         992 
    7         999 
    8        1003 
    9         988 
```

数据中每个类别的图像数量不相等。

为了平衡训练集中每个数字的图像数量，首先找到类别中图像最少的数量。

```matlab
minSetCount = min(digitData.countEachLabel{:,2})
minSetCount =
    988
```

划分数据集，使训练集中的每个类别都有 494 张图像，而测试集包含每个标签剩余的图像。

```matlab
trainingNumFiles = round(minSetCount/2);
rng(1) % 为了可复现性
[trainDigitData,testDigitData] = splitEachLabel(digitData,...
                                     trainingNumFiles,'randomize');
```

`splitEachLabel` 将 `digitData` 中的图像文件拆分为两个新的数据存储器 `trainDigitData` 和 `testDigitData`。

为卷积神经网络创建层。

```matlab
layers = [imageInputLayer([28 28 1])
           convolution2dLayer(5,20)
           reluLayer()
           maxPooling2dLayer(2,'Stride',2)
           fullyConnectedLayer(10)
           softmaxLayer()
           classificationLayer()];
```

创建训练选项。将最大训练轮数设置为 20，并以 0.01 的初始率开始训练。

```matlab
options = trainingOptions('sg','MaxEpochs',20,... 'InitialRate',0.01);
```

使用训练集和上一步定义的选项训练网络。

```matlab
convnet = trainNetwork(trainDigitData,layers,options)
=========================
Epoch | Iteration | Time Elapsed (seconds) | Mini-batch Loss | Accuracy | Base Rate
=========================
2 | 50 | 0.7 | 0.233 | 92.97% | 0.0100
3 | 100 | 1.37 | 0.182 | 99.2% | 0.0100
4 | 150 | 2.02 | 0.095 | 99.22% | 0.0100
6 | 200 | 2.70 | 0.0105 | 99.22% | 0.0100
7 | 250 | 3.35 | 0.0026 | 100.0% | 0.0100
8 | 300 | 4.00 | 0.0004 | 100.0% | 0.0100
10 | 350 | 4.67 | 0.0002 | 100.0% | 0.0100
11 | 400 | 5.32 | 0.0001 | 100.0% | 0.0100
12 | 450 | 5.95 | 0.0001 | 100.0% | 0.0100
14 | 500 | 6.60 | 0.0002 | 100.0% | 0.0100
15 | 550 | 7.23 | 0.0001 | 100.0% | 0.0100
16 | 600 | 7.87 | 0.0001 | 100.0% | 0.0100
18 | 650 | 8.52 | 0.0001 | 100.0% | 0.0100
19 | 700 | 9.15 | 0.0001 | 100.0% | 0.0100
20 | 750 | 9.79 | 0.0000 | 100.0% | 0.00100
=========================================
```

使用测试集测试网络并计算准确率。

```matlab
YTest = classify(convnet,testDigitData);
TTest = testDigitData.Labels;
accuracy = sum(YTest == TTest)/numel(YTest)
accuracy =
    0.9976
```

准确率是测试数据中与 `classify` 分类正确的标签数量与测试数据图像总数的比例。在这种情况下，99.78% 的数字估计符合测试集中的真实数字值。

现在，假设你想使用训练好的网络 `net` 对新一组数据预测类别。加载字母训练数据。

```matlab
load lettersTrainSet.mat
```

`XTrain` 包含 1500 张 A、B 和 C 字母的 28x28 灰度图像。`TTrain` 包含字母标签的分类数组。

显示部分字母图像。

```matlab
figure;
for j = 1:20
    subplot(4,5,j);
    selectImage = datasample(XTrain,1,4);
    imshow(selectImage,[]);
end
```

![描述: http://es.mathworks.com/help/examples/nnet/TransferLearningUsingConvolutionalNeuralNetworksExample_02.png](img/00141.jpeg)

`XTrain` 中的像素值范围在 [0 1]。训练网络 `net` 时使用的数字数据在 [255]；将字母数据缩放至 [255] 之间。

```matlab
XTrain = XTrain*255;
```

训练网络 `net` 的最后三层针对数字数据集进行了调整，该数据集有 10 个类。这些层的属性取决于分类任务。显示全连接层（fullyConnectedLayer`）。

```matlab
convnet.Layers(end-2)
ans = 
FullyConnectedLayer with properties:
    Name: 'fc'
  Hyperparameters
    InputSize: 2880
    OutputSize: 10
  Learnable Parameters
    Weights: [10×2880 single]
    Bias: [10×1 single]
```

使用 `properties` 方法查看所有属性列表。显示最后一层（classificationLayer`）。

```matlab
convnet.Layers(end)
ans = 
ClassificationOutputLayer with properties:
    Name: 'classoutput'
    ClassNames: {10×1 cell}
    OutputSize: 10
  Hyperparameters
    LossFunction: 'crossentropyex'
```

这三层必须针对新的分类问题进行微调。从训练好的网络 `net` 中提取最后三层以外的所有层。

```matlab
layersTransfer = convnet.Layers(1:end-3);
```

字母数据集有三个类别。为三个类别添加一个新的全连接层，并增加该层的学习学习率。

```matlab
layersTransfer(end+1) = fullyConnectedLayer(3,...
    'WeightLearnRateFactor',10,...
    'BiasLearnRateFactor',20);
```




`WeightLearnRateFactor` 和 `BiasLearnRateFactor` 是全连接层全局学习率的倍数。

添加一个 softmax 层和一个分类输出层。

```matlab
layersTransfer(end+1) = softmaxLayer();
layersTransfer(end+1) = classificationLayer();
```

创建迁移学习的选项。你不需要训练很多轮次（`MaxEpochs` 可以比之前更小）。将 `InitialLearnRate` 设置为比训练 `net` 时使用的低率，以通过取更小的步长来提高收敛。

```matlab
optionsTransfer = trainingOptions('sgdm',...
    'MaxEpochs',5,...
    'InitialLearnRate',0.000005,...
    'Verbose',true);
```

执行迁移学习。

```matlab
convnetTransfer = trainNetwork(XTrain,TTrain,...
                         layersTransfer,optionsTransfer);
```

| 轮次 (Epoch) | 迭代 (Iteration) |  way 时间 (Time Elapsed) | 批量损失 (Mini-batch Loss) | 批量准确率 (Mini-batch Accuracy) | 基础学习率 (Base Learning Rate) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 5 | 50 | 0.43 | 0.0011 | 100.00% | 0.000005 |

加载字母测试数据。与字母训练数据类似，将测试数据缩放到 `[0 255]` 之间，因为训练数据在这个范围内。

```matlab
load lettersTestSet.mat
XTest = XTest*255;
```

测试准确率。

```matlab
YTest = classify(convnetTransfer,XTest);
accuracy = sum(YTest == TTest)/numel(TTest)
accuracy = 0.9587
```

## 11.2 预训练卷积神经网络

训练卷积神经网络（ConvNets）可能是困难且耗费时的。在某些情况下，从一个已经在大型数据集上训练好的卷积网络开始，然后将其适应于当前的问题是有有意义的。你可以将以前训练过的网络用于两个用途：

- **特征提取** — 使用卷积网络从数据（图像）中提取特征，然后使用这些特征来训练不同的分类器，例如支持向量机（SVM）。
- **迁移学习** — 取一个在大型数据集上训练训练的网络，并在较小的数据集上重新训练最后几层。

Caffe 版本的 `AlexNet`（`https://github.com/BVLC/caffe/tree/master/models/bvlc_alexnet`）可以下载并用于你的问题。该网络是在 ImageNet 数据库的图像子集上训练的，这些图像用于 ImageNet 大规模视觉识别挑战（ILSVRC）。它包含 1000 个类别，每个类别大约有 1000 张训练图像。

你可以从“附加功能（Add-Ons）”库安装训练好的网络。在 MATLAB® 桌面版的 **Add-Ons** 下拉菜单中选择 **Get Add-Ons**。附加功能文件位于“MathWorks Features”部分。选择用于 AlexNet 网络的**神经网络工具箱模型**。

在下载支持包后，你可以在命令行中输入 `alexnet` 来访问它。

```matlab
net = alexnet
net = SeriesNetwork with properties:
    Layers: [25×1 nnet.cnn.layer.Layer]
```

训练好的网络是一个 `SeriesNetwork` 对象。你可以使用点符号法查看架构的细节。

```matlab
net.Layers
ans = 25x1 Layer array with layers:
    1  'data'     Image Input               227x227x3 images with 'zerocenter' normalization
    2  'conv1'  Convolution      96 11x11x3 convolutions with stride [4 4] and padding [0 0]
    3  'relu1'  ReLU
    4  'norm1'  BatchNormalization
    5  'pool1'  MaxPooling2D      Stride [2 2]
    6  'conv2'  Convolution      256 5x5x3 convolutions with stride [1 1] and padding [2 2]
    7  'relu2'  ReLU
    8  'norm2'  BatchNormalization
    9  'pool2'  MaxPooling2D      Stride [2 2]
    10 'conv3'  Convolution      384 3x3x3 convolutions with stride [1 1] and padding [1 1]
    11 'relu3'  ReLU
    12 'norm3'  BatchNormalization
    13 'pool3'  MaxPooling2D      Stride [2 2]
    14 'conv4'  Convolution      256 3x3x3 convolutions with stride [1 1] and padding [1 1]
    15 'relu4'  ReLU
    16 'norm4'  BatchNormalization
    17 'pool4'  MaxPooling2D      Stride [2 2]
    18 'conv5'  Convolution      256 3x3x3 convolutions with stride [1 1] and padding [1 1]
    19 'relu5'  ReLU
    20 'norm5'  BatchNormalization
    21 'pool5'  MaxPooling2D      Stride [2 2]
    22 'fc6'   FullyConnected      4096
    23 'relu6'  ReLU
    24 'fc7'   FullyConnected      4096
    25 'relu7'  ReLU
    26 'fc8'   FullyConnected      1000
    27 'softmax' Softmax
```
*(注：由于原文中 `net.Layers` 的输出部分在示例中不完整或有差异，此处根据通用逻辑保持了结构，翻译遵循了代码块格式。)*





| [generateSimink](http://es.mathworks.com/help/nnet/ref/autoencoder.generatesimulink.html) | 为自动编码器生成 Simulink 模型 |
| [network](http://es.mathworks.com/help/nnet/ref/autoencoder.network.html) | 将自动编码器对象转换为网络对象 |
| [plotWeights](http://es.mathworks.com/help/nnet/ref/autoencoder.plotweights.html) | 绘制自动编码器编码器权的可可视化 |
| [predict](http://es.mathworks.com/help/nnet/ref/autoencoder.predict.html) | 使用训练过的自动编码器重构输入 |
| [stack](http://es.mathworks.com/help/nnet/ref/autoencoder.stack.html) | 将多个自动编码器的编码器堆叠在一起
| [view](http://es.mathworks.com/help/nnet/ref/autoencoder.view.html) | 查看自动编码器 |

# 12.2 自动编码器函数

## 12.2.1 函数

| [`trainAutoencoder`](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html) | 训练自动编码器 |
| --- | --- |
| [`trainSoftmaxLayer`](http://es.mathworks.com/help/nnet/ref/trainsoftmaxlayer.html) | 为分类训练一个 softmax 层 |
| [`decode`](http://es.mathworks.com/help/nnet/ref/autoencoder.decode.html) | 解码编码数据 |
| [`encode`](http://es.mathworks.com/help/nnet/ref/autoencoder.encode.html) | 编码输入数据 |
| [`generateFunction`](http://es.mathworks.com/help/nnet/ref/autoencoder.generatefunction.html) | 生成一个运行自动编码器的 MATLAB 函数 |
| [`generateSimulink`](http://es.mathworks.com/help/nnet/ref/autoencoder.generatesimulink.html) | 为自动编码器生成 Simulink 模型 |
| [`network`](http://es.mathworks.com/help/nnet/ref/autoencoder.network.html) | 将自动编码器对象转换为网络对象 |
| [`plotWeights`](http://es.mathworks.com/help/nnet/ref/autoencoder.plotweights.html) | 绘制自动编码器编码器权的可可视化 |
| [`predict`](http://es.mathworks.com/help/nnet/ref/autoencoder.predict.html) | 使用训练过的自动编码器重构输入 |
| [`stack`](http://es.mathworks.com/help/nnet/ref/autoencoder.stack.html) | 将多个自动编码器的编码器堆叠在一起 |
| [`view`](http://es.mathworks.com/help/nnet/ref/autoencoder.view.html) | 查看自动编码器 |

## 12.2.2 trainAutoencoder

训练自动编码器

### 语法

- `autoenc = trainAutoencoder(X)`
- `autoenc = trainAutoencoder(X,hiddenSize)`
- `autoenc = trainAutoencoder(___,Name,Value)`

### 描述

[autoenc](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html#outputarg_autoenc) = `trainAutoencoder([X](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html#inputarg_X))` 返回一个使用 `X` 中的训练数据训练的自动编码器 `autoenc`。

[autoenc](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html#outputarg_autoenc) = `trainAutoencoder([X](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html#inputarg_X),[hiddenSize](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html#inputarg_hiddenSize))` 返回一个隐藏表示大小为 `hiddenSize` 的自动编码器 `autoenc`。

[autoenc](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html#outputarg_autoenc) = `trainAutoencoder(___,Name,Value](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html#namevaluearguments))` 返回一个通过一个或多个 `Name,Value` 参数对指定的额外选项的自动编码器 `autoenc`。例如，你可以指定稀疏比例或最大迭代次数。

### 示例。训练稀疏自动编码器

加载数据。

```matlab
X = abalone_dataset;
```

`X` 是一个 8x4177 的矩阵，定义了 8 个属性（性别、长度、直径、高度、肉质重量等）。关于数据集的更多信息，请在命令行中输入 `help abalone_dataset`。

使用默认设置训练稀疏自动编码器。

```matlab
autoenc = trainAutoencoder(X);
```

使用训练过的自动编码器重构鲍鱼数据。

```matlab
XReconstructed = predict(autoenc,X);
```

计算均方误差。

```matlab
mseError = mse(X-XReconstructed)
```
mseError = 0.0167

### 使用指定选项训练自动编码器

加载数据。

```matlab
X = abalone_dataset;
```

`X` 是一个 8x4177 的矩阵，定义了 8 个属性（性别、长度、直径、高度、肉质重量等）。关于数据集的更多信息，请在命令行中输入 `help abalone_dataset`。

使用隐藏层大小 4、400 次最大迭代以及解码器的线性传递函数训练稀疏自动编码器。

```matlab
autoenc = trainAutoencoder(X,4,'MaxEpochs',400,...
'DecoderTransferFunction','purelin');
```

使用训练过的自动编码器重构鲍鱼数据。

```matlab
XReconstructed = predict(autoenc,X);
```

计算均方误差。

```matlab
mseError = mse(X-XReconstructed)
```
mseError = 0.0056

### 使用稀疏自动编码器重构观测值

生成训练数据。

```matlab
rng('twister'); % 为了复现性
n = 1000;
r = linspace(-10,10,n);
x = 1 + r*5e-2 + sin(r)./r + 0.2*randn(n);
```

使用训练数据训练自动编码器。

```matlab
hiddenSize = 25;
autoenc = trainAutoencoder(x',hiddenSize,...
'EncoderFunction','sat',
'DecoderFunction','lin,...
'L2Regularization',0.01,...
'SparsityRegularization',4,...
'SparsityProportion',0.1);
```

生成测试数据。

```matlab
n = 1000;
r = linspace(-10,10,n);
xtest = 1 + r*5e-2 + sin(r)./r + 0.4*randn(n);
```

使用训练过的自动编码器预测测试数据。

```matlab
xReconstructed = predict(autoenc,xtest);
```

绘制实际测试数据和预测值。

```matlab
figure;
plot(xtest,'r');
hold on
plot(xReconstructed,'go');
```

### 使用稀疏自动编码器重构数字图像

加载训练数据。

```matlab
X = digittrain_dataset;
```

训练数据是一个 1x5000 的单元格数组，每个单元包含一个表示手写数字的 28x28 矩阵。

训练一个包含 25 个神经元的隐藏层的自动编码器。

```matlab
hiddenSize = 25;
autoenc = trainAutoencoder(X,hiddenSize,...
'EncoderFunction','sat',
'DecoderFunction','lin,...
'L2Regularization',0.004,...
'SparsityRegularization',4,...
'SparsityProportion',0.15);
```

加载测试数据。

```matlab
x = digittest_dataset;
```

测试数据是一个 1x5000 的单元格数组，每个单元包含一个表示手写数字的 28x28 矩阵。

使用训练过的自动编码器重构图像数据。

```matlab
xReconstructed = predict(autoenc,x);
```

查看实际测试数据。

```matlab
figure;
for i = 1:20
    subplot(4,5,i);
    imshow(X{i});
end
```

查看重构后的测试数据。

```matlab
figure;
for i = 1:20
    subplot(4,5,i);
    imshow(xReconstructed{i});
end
```

## 12.2.3 decode

解码编码数据

### 语法

```matlab
Y = decode(autoenc,Z)
```

### 描述

[Y](http://es.mathworks.com/help/nnet/ref/autoencoder.decode.html#outputarg_Y) = `decode([autoenc](http://es.mathworks.com/help/nnet/ref/autoencoder.decode.html#inputarg_autoenc),[Z](http://es.mathworks.com/help/nnet/ref/autoencoder.decode.html#inputarg_Z))` 使用自动编码器对象 `autoenc` 返回解码数据 `Y`。

训练过的自动编码器，由 `trainAutoencoder` 函数返回的 `Autoencoder` 类对象。

由 `autoenc` 编码的数据，指定为矩阵。`Z` 的每一列表示一个编码样本（观测值）。

解码数据，以矩阵或图像单元格数组的形式返回。如果自动编码器 `autoenc` 是在图像单元格数组上训练的，那么 `Y` 也是图像单元格数组。




如果自编码器 `autoenc` 是在矩阵上训练的，那么 `Y`也是一个矩阵，其中 `Y` 的每一列对应一个样本或观测值。

### 示例：解码新图像的编码

加载训练数据。

```matlab
X = digitTrainCellArrayData;
```

`X` 是一个 1-by-5003 的元胞数组，每个单元格包含一个 28-by-28 的矩阵，表示手写数字的合成图像。

使用训练数据训练一个隐藏层为 15 的自编码器。

```matlab
hiddenSize = 15;
autoenc = trainAutoencoder(X,hiddenSize);
```

使用自编码器提取新图像的编码数据。

```matlab
Xnew = digitTestCellArrayData;
features = encode(autoenc,Xnew);
```

从自编码器解码编码数据。

```matlab
Y = decode(autoenc,features);
```

`Y` 是一个 1-by-4997 的元胞数组，每个单元格包含一个 28-by-28 的矩阵，表示手写数字的合成图像。

### 12.2.4 encode

#### 输入数据

**语法**

```matlab
Z = encode(autoenc,Xnew)
```

**描述**

`Z` = `encode([autoenc],[Xnew])` 使用自编码器 `autoenc` 返回输入数据 `Xnew` 的编码数据 `Z`。

#### 示例。为新图像编码解码后的数据

加载样本数据。

```matlab
X = digitTrainCellArrayData;
```

`X` 是一个 1-by-5003 的元胞数组，每个单元格包含一个 28-by-28 的矩阵，表示手写数字的合成图像。

使用训练数据训练一个隐藏层为 50 的自编码器。

```matlab
autoenc = trainAutoencoder(X,50);
```

对新图像数据编码解码后的数据。

```matlab
Xnew = digitTestCellArrayData;
Z = encode(autoenc,Xnew);
```

`Xnew` 是一个 1-by-4997 的元胞数组。`Z` 是一个 50-by-4997 的矩阵，其中每一列代表新数据 `Xnew` 中一个手写数字的图像数据。

### 12.2.5 predict

#### 使用训练的自编码器重构输入

**语法**

·   `Y = predict(autoenc,X)`

**描述**

`Y = predict(autoenc,X)` 使用自编码器 `autoenc` 返回输入数据 `X` 的预测值 `Y`。结果 `Y` 是 `X` 的重构。

#### 示例：使用训练的自编码器预测连续测量

加载训练数据。

```matlab
X = iris_dataset;
```

训练数据包含对鸢尾花四个属性的测量值：花萼长度、花萼宽度、花瓣长度、花瓣宽度。

在训练数据上训练自编码器，在编码器中使用正饱和线性传递函数，在解码器中使用线性传递函数。

```matlab
autoenc = trainAutoencoder(X,'EncoderTransferFunction',...
'satlin','DecoderTransferFunction','purelin');
```

使用训练过的网络 `autoenc` 重构测量值。

```matlab
xReconstructed = predict(autoenc,X);
```

在训练数据集中绘制预测的测量值以及实际值。

```matlab
for i = 1:4
h(i) = subplot(1,4,i);
plot(X(i,:),'r.');
hold on
plot(xReconstructed(i,:),'go');
hold off;
end
title(h(1),{'Sepal';'Length'});
title(h(2),{'Sepal';'Width'});
title(h(3),{'Petal';'Length'});
title(h(4),{'Petal';'Width'});
```

![](img/00144.jpeg)

红点代表训练数据，绿色圆圈代表重构的数据。

### 12.2.6 stack

#### 将多个自编码器的编码器堆叠在一起

**语法**

·   `stackednet = stack(autoenc1,autoenc2,...)`
·   `stackednet = stack(autoenc1,autoenc2,...,net1)`

**描述**

`stackednet = stack(autoenc1,autoenc2,...)` 通过堆叠自编码器 `autoenc1`、`autoenc2` 等的编码器来创建一个网络对象。

`stackednet = stack(autoenc1,autoenc2,...,net1)` 通过堆叠自编码器 `autoenc1`、`autoenc2` 和 `net1` 的编码器来创建一个网络对象。

**提示**

·      其中一个自编码器的尺寸必须与下一个自编码器的输入尺寸匹配。
·      第一个自编码器的输出是第二个自编码器的输入。
·      堆叠网络从 `net1` 继承其参数。

#### 示例。创建一个堆叠网络

加载训练数据。

```matlab
X = iris_dataset;
```

训练一个隐藏层为 5 且解码器使用线性传递函数的自编码器。设置 L2 正化因子为 0.001，稀疏化因子为 4，稀疏比例为 0.05。

```matlab
hiddenSize = 5;
autoenc = trainAutoencoder(X,'DecoderTransferFunction','purelin',
'L2Regularization',0.001,'SparsityRegularization',4,'SparsityProportion',0.05);
```

提取隐藏层的特征。

```matlab
features = encode(autoenc,X);
```

使用特征训练分类的 softmax 层。

```matlab
softnet = trainSoftmaxLayer(features);
```

将编码器和 softmax 层堆叠形成深度网络。

```matlab
stackednet = stack(autoenc,softnet);
```

查看堆叠网络。

```matlab
view(stackednet);
```

![](img/00145.jpeg)

### 12.2.7 generateFunction

#### 生成用于运行自编码器的 MATLAB 函数

**语法**

·      `generateFunction(autoenc)`
·      `generateFunction(autoenc,pathname)`
·      `generateFunction(autoenc,pathname,Name,Value)`

**描述**

`generateFunction(autoenc)` 在当前目录生成一个完整的独立函数，用于自编码器 `autoenc` 处理输入数据。

`generateFunction(autoenc,pathname)` 在 `pathname` 指定的位置生成一个完整的独立函数，用于自编码器 `autoenc` 处理输入数据。

`generateFunction(autoenc,pathname,Name,Value)` 根据 `Name,Value` 参数指定的附加选项生成一个完整的独立函数。

**提示**

·      如果没有指定路径和文件名，`generateFunction` 默认在名为 `neural_function.m` 的 m 文件中创建代码。你可以在 `generateFunction` 生成后更改文件名。或者可以在调用 `generateFunction` 时使用 `pathname` 输入参数指定路径和文件名。

**输入参数**

`autoenc`— 训练过的自编码器 Autoencoder 对象
`pathname`— 生成的函数的字符串位置

**示例：生成运行自编码器的 MATLAB 函数**

加载样本数据。

```matlab
X = iris_dataset;
```

训练一个隐藏层具有 4 个神经元的自编码器。

```matlab
autoenc = trainAutoencoder(X,4);
```

生成运行自编码器的代码。显示指向 MATLAB 函数的链接。

```matlab
generateFunction(autoenc)
```

MATLAB 生成了函数：neural_function.m




查看生成的函数代码：`edit neural_function`

查看函数的用法示例：`help neural_function`

在特定路径下生成自动编码器的代码。

```
generateFunction(autoenc,'H:\Documents\Autoencoder')
```

生成的 MATLAB 函数：`H:\Documents\Autoencoder.m`

查看生成的函数代码：`edit Autoencoder`

查看函数的用法示例：`help Autoencoder`

## 12.2.8 generateSimulink

为自动编码器生成 Simulink 模型

### 语法

- `generateSimulink(autoenc)`

### 描述

`generateSimulink(autoenc)` 为自动编码器 `autoenc` 创建一个 Simulink® 模型。

### 输入参数

**`autoenc` — 经过训练的自动编码器 `Autoencoder` 对象**

### 示例：为自动编码器生成 Simulink 模型

加载训练数据。

```matlab
X = digitsmall_dataset;
```

训练数据是一个 1-by-500 的单元格数组，每个单元格包含一个 28-by-28 的矩阵，代表手写数字的合成图像。

训练一个包含 25 个神经元隐藏层的自动编码器。

```matlab
hiddenSize = 25;
autoenc = trainAutoencoder(X,hiddenSize,... 'L2WeightRegularization',0.004,... 'SparsityRegularization',4,... 'SparsityProportion',0.15);
```

为自动编码器 `autoenc` 创建一个 Simulink 模型。

```matlab
generateSimulink(autoenc)
```

![](img/00146.gif)

## 12.2.9 plotWeights

绘制自动编码器编码器权重的可视化图

### 语法

- `plotWeights(autoenc)`
- `h = plotWeights(autoenc)`

### 描述

`plotWeights(autoenc)` 将自动编码器 `autoenc` 的权重可视化。

`h = plotWeights(autoenc)` 返回一个函数句柄 `h`，用于自动编码器 `autoenc` 编码器权重的可视化。

### 提示

- `plotWeights` 允许对自动编码器学习的特征进行可视化。当自动编码器在图像数据上进行训练时，可以使用它。权重可视化的维度与用于训练的图像维度相同。

### 输入参数

**`autoenc` — 经过训练的自动编码器 `Autoencoder` 对象**

### 输出参数

**`h` — 图像对象句柄**

### 示例：可视化学习到的特征

加载训练数据。

```matlab
X = digitTrainCellArrayData;
```

训练数据是一个 1-by-5003 的单元格数组，每个单元格包含一个 28-by-28 的矩阵，代表手写数字的合成图像。

训练一个具有 25 个神经元隐藏层的自动编码器。

```matlab
hiddenSize = 25;
autoenc = trainAutoencoder(X,hiddenSize, ...
  'L2WeightRegularization',0.004, ...
  'SparsityRegularization',4, ...
  'SparsityProportion',0.2);
```

可视化学习到的特征。

```matlab
plotWeights(autoenc);
```

![](img/00147.jpeg)

## 12.2.10 view

查看自动编码器

### 语法

- `view(autoenc)`

### 描述

`view(autoenc)` 返回自动编码器 `autoenc` 的结构图。

### 输入参数

**`autoenc` — 经过训练的自动编码器 `Autoencoder` 对象**

### 示例：查看自动编码器

加载训练数据。

```matlab
X = iris_dataset;
```

训练一个具有大小 5 的隐藏层且解码器使用线性传递函数的自动编码器。将 L2 权重正则化设置为 0.001，稀疏性正则化设置为 4，稀疏性比例设置为 0.05。

```matlab
hiddenSize = 5;
autoenc = trainAutoencoder(X, hiddenSize, ...
    'L2WeightRegularization',0.001, ...
    'SparsityRegularization',4, ...
    'SparsityProportion',0.05, ...
    'DecoderTransferFunction','purelin');
```

查看自动编码器。

```matlab
view(autoenc)
```

![Descripción: http://es.mathworks.com/help/examples/nnet/ViewAutoencoderExample_01.png](img/00148.jpeg)

## 12.3 使用自动编码器构建深度网络

加载样本数据。

```matlab
[X,T] = wine_dataset;
```

训练一个具有大小为 10 的隐藏层且解码器使用线性传递函数的自动编码器。将 L2 权重正则化设置为 0.001，稀疏性正则化设置为 4，稀疏性比例设置为 0.05。

```matlab
hiddenSize = 10;
autoenc = trainAutoEncoder(X,hiddenSize,...
  'L2WeightRegularization',0.001,...
  'SparsityRegularization',4,...
  'SparsityProportion',0.05,...
  'DecoderTransferFunction','purelin');
```

提取隐藏层中的特征。

```matlab
features1 = encode(autoenc)
```

使用这些特征训练第二个自动编码器。不要对数据进行缩放。

```matlab
hiddenSize = 10;
autoenc2 = trainAutoEncoder(features1,hiddenSize,...
  'L2WeightRegularization',0.001,...
  'SparsityRegularization',4,...
  'SparsityProportion',0.05;
```

提取隐藏层中的特征。

```matlab
features2 = encode(autoenc)
```

使用特征训练一个 softmax 层。

```matlab
softnet = trainSoftmax(features2)
```

将编码器和 softmax 层堆叠形成深度网络。

```matlab
deepnet = stack(autoenc,autoenc2,softnet);
```

在葡萄酒数据上训练深度网络。

```matlab
deepnet = train(deepnet,T);
```

使用深度网络估计葡萄酒类型。

```matlab
wine_type = deepnet(X);
```

绘制混淆矩阵。

```matlab
plotconfusion(T,wine_type);
```

![](img/00149.jpeg)

# 13 自动编码器

## 13.1 使用叠加自动编码器分类

本示例展示了如何使用神经网络自动编码器功能训练一个深度神经网络来对数字进行分类。具有多个隐藏层的神经网络可以解决复杂数据（如图像）的问题。每层可以学习不同层次的特征。然而，训练具有多个隐藏层的神经网络是困难的。

有效训练多层神经网络的方法是每次训练一层。可以通过训练自动编码器来实现。

## 13.1.1 数据集

本示例在训练和测试中始终使用合成数据。合成图像是通过对数字图像应用随机仿变换生成的。

每个数字图像为 28-by-28 像素，共有 5000 个训练示例。你可以加载训练数据并查看某些图像。

```matlab
% 将训练数据加载到内存
[xTrainImages,tTrain] = digitTrainCellArrayData;

% 显示一些图像
clf
for i = 1:20
    subplot(4,5,i);
    imshow(xTrainImages{i});
end
```

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample_01.png](img/00150.jpeg)

标签存储在 10-by-5000 的矩阵中，其中每一列中有一个元素为 1，表示该数字所属的类别，列中的所有其他元素均为 0。注意，如果第十个元素为 1，则该数字图像为零。

### 13.1.2 训练第一个自动编码器

首先在训练数据上不使用标签，训练稀疏自动编码器。

自动编码器是一种试图在输出端复制其输入的神经网络。因此，其输入的大小与输出的大小相同。当隐藏层中的神经元数量小于输入大小时，自动编码器会学习输入的压缩表示。





神经网络在训练之前的权重是随机初始化的。因此，每次训练的结果都是不同的。为了避免这种行为，请显式地设置随机数生成器种子。

```mat
rng('default')
```

设置自动编码器隐藏层的大小。对于你将要训练的自动编码器，将此值设置得比输入大小要好的主意。

```matlab
hiddenSize1 = 100;
```

你将训练的自动编码器类型是稀疏自动编码器。这种编码器使用正则化项在第一层学习稀疏表示。你可以通过设置各种参数来控制这些正则化项的影响：

- `L2WeightRegularization` 控制网络权重（而非偏置）的 `L2` 正则化项的影响。该值通常应该很小。
- `SparsityRegularization` 控制稀疏正则化项的影响，该正则化项试图对隐藏层输出的稀疏性实施约束。注意，这与对权重应用稀疏正则化项不同。
- `SparsityProportion` 是稀疏正则化项的参数。它控制隐藏层输出的稀疏程度。`SparsityProportion` 的低值通常会导致隐藏层中的每个神经元通过仅对少数训练示例给出高输出来实现“专门化”。例如，如果 `SparsityProportion` 设置为 `0.1`，则等于认为隐藏层中的每个神经元在训练示例上的平均输出为 `0.1`。该值必须在 `0` 和 `1` 之间。理想值取决于问题的性质。

现在训练自动编码器，并指定上述述正则化项的值。

```matlab
autoenc1 = trainAutoencoder(xTrainImages,hiddenSize1, ...
    'MaxEpochs',400, ...
    'L2WeightRegularization',0.004, ...
    'SparsityRegularization',4, ...
    'SparsityProportion',0.15, ...
    'ScaleData', false);
```

你可以查看自动编码器的结构图。自动编码器由一个编码器后随一个解码器组成。编码器将输入映射到隐藏表示，而解码器试图反转这种映射以重建原始输入。

```matlab
view(autoenc1)
```

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_02.png](img/00151.jpeg)

## 13.1.3 可视化第一个自动编码器的权重

自动编码器编码部分学习的映射对于从数据中提取特征有用。编码器中的每个神经元都有相关的权重向量，这些向量将调整为响应特定的视觉特征。你可以查看这些特征的表示。

```matlab
figure()
plotWeights(autoenc1);
```

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_03.png](img/00152.jpeg)

你可以看到自动编码器学习的特征代表了数字图像中的弯曲和笔画模式。

隐藏层的 100 维输出是输入的压缩版本，它总结了对上述可视化特征的响应。在从训练数据中提取的一组这些向量上训练下一个自动编码器。首先，你必须使用已训练自动编码器的编码器来生成特征。

```matlab
feat1 = encode(autoenc1,xTrainImages);
```

## 13.1.4 训练第二个自动编码器

训练第一个自动编码器后，你以类似的方式训练第二个自动编码器。主要区别是你使用从第一个自动编码器生成的特征作为第二个自动编码器的训练数据。此外，你将隐藏表示的大小减到 `50`，以便第二个自动编码器的编码器学习输入数据的更小规模表示。

```matlab
hiddenSize2 = 50;
autoenc2 = trainAutoencoder(feat1,hiddenSize2, ...
    'MaxEpochs',100, ...
    'L2WeightRegularization',0.002, ...
    'SparsityRegularization',4, ...
    'SparsityProportion',0.1, ...
    'ScaleData', false);
```

再次，你可以使用 `view` 函数查看自动编码器的结构图。

```matlab
view(autoenc2)
```

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_04.png](img/00153.jpeg)

你可以通过将上一组特征通过第二个自动编码器的编码器来提取第二组特征。

```matlab
feat2 = encode(autoenc2,feat1);
```

训练数据中的原始向量具有 `784` 维。在通过第一个编码器后，维度减少到 `100` 维。在使用第二个编码器后，维度再次减少到 `50` 维。你现在可以训练一个最终层来将这些 `50` 维向量分类为不同的数字类。

## 13.1.5 训练最后的 softmax 层

训练一个 softmax 层来分类这些 `50` 维特征向量。与自动编码器不同，你使用训练数据的标签以有监督的方式训练 softmax 层。

```matlab
softnet = trainSoftmaxLayer(feat2,tTrain,'MaxEpochs',400);
```

你可以使用 `view` 函数查看 softmax 层的结构图。

```matlab
view(softnet)
```

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_05.png](img/00154.jpeg)

## 13.1.6 构建堆叠神经网络

你已经独立地训练了深度神经网络的三个单独组件。到此时，查看你所训练的三个神经网络可能是有用的。它们是 `autoenc1`、`autoenc2` 和 `softnet`。

```matlab
view(autoenc1)
view(autoenc2)
view(softnet)
```

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_06.png](img/00151.jpeg)

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_07.png](img/00155.jpeg)

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_08.png](img/00154.jpeg)

如所述，自动编码器的编码器已用于提取特征。你可以将自动编码器的编码器与 softmax 层堆叠形成一个深度网络。

```matlab
deepnet = stack(autoenc1,autoenc2,softnet);
```

你可以使用 `view` 函数查看堆叠网络的结构图。该网络由自动编码器的编码器和 softmax 层组成。

```matlab
view(deepnet)
```

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_09.png](img/00156.jpeg)

一旦形成了完整的深度网络，就可以在测试集上计算结果。为了配合堆叠网络使用，你必须将测试图像重塑为矩阵。你可以通过堆叠图像列形成向量，然后由这些向量形成矩阵。

```matlab
% 获取图像的像素数量
imageWidth = 28;
imageHeight = 28;
inputSize = imageWidth*imageHeight;

% 加载测试图像
[xTestImages,tTest] = digitCellArrayData;

% 将测试图像转换为向量并放入矩阵
xTest = zeros(inputSize,numel(xTestImages));
for i = 1:numel(xTestImages)
    xTest(:,i) = xTestImages{i}(:);
end
```

你可以使用混淆矩阵来可视化结果。矩阵右下角的数字提供了整体准确率。

```matlab
y = deepnet(xTest);
plotconfusion(tTest,y);
```

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_10.png](img/00157.jpeg)

## 13.1.7 微调深度神经网络

通过对整个多层网络进行反向传播可以改进深度神经网络的结果。这个过程通常被称为微调。

你通过在有监督的方式在训练数据上重新训练网络来微调。在此之前，你必须像处理测试图像一样将训练图像重塑为矩阵。

```matlab
% 执行微调
deepnet = train(deepnet,xTrain,tTrain);
```




然后你再次使用混淆矩阵查看结果。

```matlab
y = deepnet(xTest);
plotconfusion(tTest,y);
```

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample_11.png](img/00158.jpeg)

## 13.1.8 总结

本示例展示了如何使用 Neural Network Toolbox™ 训练深度神经网络对图像中的数字进行分类。概述的步骤可以应用于其他类似的问题，例如对字母图像、甚至是特定类别的小图像进行分类。

## 13.2 使用卷积神经网络进行迁移学习

对一个在数字图像上预训练的卷积网络进行微调，以学习字母图像的特征。迁移学习被认为是将知识从一个已学习的任务转移到一个新任务中。在神经网络的语境下，它是将预训练网络的特征转移到新问题上。当存在有足够的训练数据时，在每个情况下从头开始训练卷积网络通常是不有效的。深度学习中此类情况的常见做法是使用在大型数据集上训练过的网络来解决新问题。虽然可以固定预训练网络的初始层，但必须对最后几层进行微调，以学习新数据的特定特征。迁移学习通常比训练一个新的卷积网络训练得更快，因为你不需要估计新网络中的所有参数。

**注意：** 训练卷积网络需要 Parallel Computing Toolbox 以及具有计算能力 3.0 或更高版本的支持 CUDA 的 GPU。

将样本数据加载为 `ImageDatastore`。

```matlab
digitDataset = fullfile(matlabroot,'toolbox','nnet','digitDataset');
digitData = imageastore(digitDataset,'IncludeSubfolders',true,'Label','filenames');
```

该数据包含 1000 张数字 0–9 的合成图像。这些图像是通过使用不同的字体对数字图像应用随机变换生成的。每张数字图像均为 28x28 像素。显示数据存储中的一些图像。

```matlab
for i = 1:20
    subplot(4,5,i);
    imshow(digitData.Files{i});
end
```

![Descripción: http://www.mathworks.com/help/examples/nnet/TransferLearningUsingConvolutionalNetworksExample_01.png](img/0159.jpeg)

检查每个数字类别中图像的数量。

```matlab
digitData.countEach
ans =
    Label      Count
    ____      ____
    0          988
    1          1026
    2          1003
    3          993
    4          991
    5          1017
    6          992
    7          999
    8          1003
    9          988
```

数据中每个类别的图像数量不相等。为了平衡训练集中每个数字图像的数量，找到类别中图像的最少数量。

```matlab
minSetCount = min(digitData.countEach{:,2});
minSetCount = 988
```

划分数据集，使得训练集中的每个类别都有 494 张图像，而测试集包含每个标签剩余的图像。

```matlab
trainingNumFiles = round(minSetCount/2);
rng(1); % 为了可复现性
[trainDigitData,testDigitData] = splitEachLabel(digitData,trainingNumFiles,'random');
```

`splitEachLabel` 将 `digitData` 中的图像文件划分为两个新的数据存储：`trainDigitData` 和 `testDigitData`。创建卷积神经网络的层。

```matlab
layers = [imageInputLayer([28 28 1])
    convolution2dLayer(5,20)
    reluLayer()
    maxPooling2dLayer(2,'Stride',2)
    fullyConnectedLayer(10)
    softmaxLayer()
    classificationLayer()];
```

创建训练选项。将最大轮数（epochs）设置为 20，并以 0.001 的初始学习率开始训练。

```matlab
options = trainingOptions('sgdm','MaxEpochs',20,...
    'InitialLearnRate',0.001);
```

使用训练集和上一步中定义的选项训练网络。

```matlab
convnet = trainNetwork(trainDigitData,layers,options);
```

| 轮数 | 迭代 | 经过时间 (秒) | 小批量损失 | 小批量准确率 | 基础学习率 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 2 | 5 | 0.7 | 0.233 | 92.7% | 0.0100 |
| 3 | 10 | 1.3 | 0.182 | 99.2% | 0.0100 |
| 4 | 15 | 2.0 | 0.095 | 99.2% | 0.0100 |
| 6 | 200 | 2.7 | 0.105 | 99.2% | 0.0100 |
| 7 | 250 | 3.3 | 0.026 | 100.0% | 0.0100 |
| 8 | 300 | 4.0 | 0.004 | 100.0% | 0.0100 |
| 10 | 350 | 4.67 | 0.000 | 100.0% | 0.0100 |
| 11 | 400 | 5.32 | 0.000 | 100.0% | 0.0100 |
| 12 | 450 | 5.95 | 0.000 | 100.0% | 0.0100 |
| 14 | 500 | 6.60 | 0.000 | 100.0% | 0.0100 |
| 15 | 550 | 7.23 | 0.000 | 100.0% | 0.0100 |
| 16 | 600 | 7.87 | 0.000 | 100.0% | 0.0100 |
| 18 | 650 | 8.5 | 0.000 | 100.0% | 0.0100 |
| 19 | 700 | 9.1 | 0.000 | 100.0% | 0.0100 |
| 20 | 750 | 9.7 | 0.000 | 100.0% | 0.0100 |

使用测试集测试网络并计算准确率。

```matlab
YTest = classify(convnet,testDigitData);
TTest = testDigitData.Labels;
accuracy = sum(YTest == TTest)/numel(YTest)
```

准确率为 0.976。

现在，假设你想使用训练好的网络在新的数据上预测类别。加载字母训练数据。

```matlab
load lettersSet.mat
```

`XTrain` 包含 1500 个 A、B、C 字母的 28x28 灰度图像。`TTrain` 包含标签数组。

`XTrain` 中的像素值范围在 `[0 1]`。训练 `net` 的数字数据在 `[0 255]`；将字母数据缩放到到 `[0 255]`。

```matlab
XTrain = XTrain*255;
```

显示一些字母图像。

```matlab
figure;
for j = 1:20
    subplot(4,5,j);
    selectImage = datasample(XTrain,1,4);
    imshow(selectImage);
end
```

![Descripción: http://www.mathworks.com/help/examples/nnet/TransferLearningUsingConvolutionalNetworksExample_02.png](img/0160.jpeg)

训练好的网络 `net` 的最后三层针对数字数据集进行了调整，该数据集有 10 个类。这些层的属性取决于分类任务。显示全连接层（`fullyConnectedLayer`）。

```matlab
convnet.Layers(end-2)
```

ans = 

FullyConnectedLayer with properties:
  Name: 'fc'
  Hyperparameters
    InputSize: 2880
    OutputSize: 10
  Learnable Parameters
    Weights: [10×2880 single]
    Bias: [10×1 single]

使用 `properties` 方法查看所有属性列表。显示最后一层（`classificationLayer`）。

```matlab
convnet.Layers(end)
```

ans = 

ClassificationOutputLayer with properties:
  Name: 'classoutput'
  ClassNames: {10×1 cell}
  OutputSize: 10





# 超参数

`LossFunction: 'crossentropyex'`

这三个层必须针对新的分类问题进行微调。从已经训练过的网络 `net` 中提取最后三层以外的所有层。

```matlab
layersTransfer = convnet.Layers(1:end-3);
```

字母数据集（letters data set）有三个类别。为三个类别添加一个新的全连接层，并增加该层的学习率。

```matlab
layersTransfer(end+1) = fullyConnectedLayer(3,...
    'WeightLearnRateFactor',10,...
    'BiasLearnRateFactor',20);
```

`WeightLearnRateFactor` 和 `BiasLearnRateFactor` 是全连接层全局学习率的倍数。

添加一个 softmax 层和一个分类输出层。

```matlab
layersTransfer(end+1) = softmaxLayer();
layersTransfer(end+1) = classificationLayer();
```

创建迁移学习的选项。你不需要训练很多轮次（`MaxEpochs` 可以比以前小）。将 `InitialLearnRate` 设置为比训练 `net` 时更低的速率，通过采用更小的步长来改进收敛性。

```matlab
optionsTransfer = trainingOptions('sgdm',...
    'MaxEpochs',5,...
    'InitialLearnRate',0.000005,...
    'Verbose',true);
```

执行迁移学习。

```matlab
convnetTransfer = trainNetwork(XTrain,TTrain,...
    layersTransfer,optionsTransfer);
```

| 轮次 (Epoch) | 迭代 (Iteration) | 耗时 (Time Elapsed) | 小批量损失 (Mini-batch Loss) | 小批量准确率 (Mini-batch Accuracy) | 基础学习率 (Base Learning Rate) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 5 | 50 | 0.43 | 0.0011 | 100.00% | 0.000005 |

加载字母测试数据。与字母训练数据类似，将测试数据缩放到 `[0 255]` 之间，因为训练数据是在这个范围内。

```matlab
load lettersTestSet.mat
XTest = XTest*255;
```

测试准确率。

```matlab
YTest = classify(convnetTransfer,XTest);
accuracy = sum(YTest == TTest)/numel(TTest)
accuracy = 0.9587
```

