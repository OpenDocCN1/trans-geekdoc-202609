

# 使用部署到 FPGA 的 DAG 网络对 ECG 信号进行分类

在 physionet-ECG data-master 中解压 ECGData.zip。将数据文件加载到你的 MATLAB 工作区。

```matlab
unzip(fullfile(tempdir, 'physionet ECG data-master','ECGData.zip'),..
    fullfile(tempdir, 'physionet ECG data-master'))
load(fullfile(tempdir, 'physionet ECG data-master','ECGData.mat'))
```

ECGData 是一个包含两个字段的结构体数组：Data 和 Labels。Data 字段是一个 162-65536 的矩阵，其中每行都是一个采样频率为 128 Hz 的 ECG 记录。Labels 对应 Data 的每一行。三个诊断类别为：'ARR'、'CHF', 'NSR'。

为了存储每个类别的预处理数据，在 tempdir 内部创建一个名为 dataDir 的 ECG 数据目录。然后并在 'data' 中创建以每个 ECG 类别命名的子目录。辅助函数 helperCreateECGdirectories 可以实现此操作。helperCreateECGdirectories  ECGData、ECG 数据目录名称和父目录名称作为输入参数。你可以将 tempdir 替换为你有权限的其他目录。你可以在此示例末的“辅助函数”部分找到该辅助函数的源代码。

```matlab
%parentDir = tempdir;
parentDir = pwd;
dataDir = 'data';
helperCreateECGdirectories(ECGData,parentDir,dataDir)
```

绘制每个 ECG 类别的代表性图。辅助函数 helperPlotReps  ECGData 作为输入。你可以在此示例末的“辅助函数”部分找到该辅助函数的源代码。

```matlab
helperPlotReps(ECGData)
```

# 10 个特色示例

![](img/747bfd4f288a7e0917a1f27637cc5c2d_237_0.png)

### ### 创建时频表示

创建文件夹后，创建 ECG 信号的时频表示。这些表示被称为尺度图（scalograms）。尺度图是信号的 CWT 系数的绝对值。

要创建尺度图，请预先计算 CWT 滤波器组。当在使用相同参数对多个信号进行 CWT 时，预计算 CWT 滤波器组是首选方法。

在生成尺度图之前，检查其中一个。使用 cfilterbank 为具有 1000 个样本的信号创建一个 CWT 滤波器组。使用该滤波器组对信号的前 1000 个样本进行 CWT，并从系数获取尺度图。

```matlab
Fs = 120;
fb = cfilterbank('Signallength',1000,...
    'SamplingFrequency',Fs,...
    'VoicesPerOctave',12);
sig = ECGData.Data(1:1000);
[cfs,frq] = wt(fb,sig);
t = (0:999)/Fs;figure;pcolor(t,frq,abs(cfs))
set(gca,'yscale','log');shading,interp;axis tight
title('Scalogram');xlabel('Time (s)');ylabel('Frequency (Hz)')
```

![](img/747bfd4f288a7e0917a1f27637cc5c2d_238_0.png)

使用辅助函数 helperCreateRGBfromTF 将尺度图创建为 RGB 图像，并将它们写入 dataDir 中相应的子目录。该辅助函数的源代码位于此示例末尾的辅助函数中。为了兼容 GoogLeNet 架构，每个 RGB 图像都是大小为 224-by-224-by-3 的数组。

```matlab
helperCreateRGBfromTF(ECListData,parentDir,dataDir)
``` 划分训练和验证数据

将尺度图加载为 image datastore。imageDatastore 函数通过文件夹名称自动标记图像并存储为 image datastore 对象。image datastore 允许存储无法内存的大型图像，并在训练期间高效读取批量图像。

```matlab
allImages = imageDatastore(fullfile(parentDir,dataDir),
    'IncludeSubfolders',true);
```

随机将图像随机划分为两组，一组用于训练，另一组用于验证。使用 80% 的图像进行训练，剩余部分用于验证。为了具有可重复性，将随机种子设置为默认值。

```matlab
rng default
[imgsTrain,imgsValidation] = splitEachLabel(allImages,0.8);
disp(['Number of training images: ',num2str(numel(imgsTrain.Files))]);
disp(['Number of validation images: ',num2str(numel(imgsValidation.Files))]);
```

# SqueezeNet

SqueezeNet 是一个深度 CNN，支持尺寸为 227-by-227-by-3 的图像。尽管维度与 GoogleLeNet 不同，但不需要生成新的 RGB 图像。加载自定义的 SqueezeNet 网络。

```matlab
sqz = squeeze;
``` 从网络中提取图。确认 SqueezeNet 的层数比 GoogleLeNet 少。

```matlab
graphSqz = layerGraph(sqz);
disp('Number of Layers: ',numel(graphSqz.Layers));
disp(graphSqz.Layers(end).InputSize)
``` 修改 SqueezeNet 参数

为了保留 SqueezeNet 以分类新图像，进行与 GoogleLeNet 类似的更改。检查网络的最后六层。

```matlab
graphSqz.Layers(end-5:end)
```

ans =
| 'new dropout' | Dropout | 60% dropout |
| 'new conv' | Convolution | 1x1 convolutions with stride [1 1] |
| 'relu_conv10' | ReLU | ReLU |
| 'pool10' | Global Average Pooling | Global pooling |
| 'prob' | Softmax | softmax |
| 'newclassout' | Classification Output | |

将网络中的最后一个 'dropout' 层替换为概率为 0.6 的 dropout 层。

```matlab
tmpLayer = graphSqz.Layers(end);
newDropoutLayer = dropoutLayer(0.6,'Name','new dropout');
graphSqz = replaceLayer(graphSqz,tmpLayer.Name,newDropoutLayer);
``` 与 GoogleLeNet 不同，SqueezeNet 中的可学习层是 1-by-1 卷积层 'conv10$，而不是全连接。将 'conv10' 替换为数量等于类别数量的卷积层。像 GoogleLeNet 一样，增加新层的学习率。

```matlab
numClasses = numel(categories(imgsTrain.Labels));
tmpLayer = graphSqz.Layers(end-4);
``` 使用部署到 FPGA 的 DAG 网络对 ECG 信号进行分类

```matlab
newLearnableLayer = convolution2dLayer(1,numClasses, ...
'Name', 'new conv', ...
'WeightLearnRateFactor',10, ...
'BiasLearnRateFactor',10)
graphSqz = replaceLayer(graphSqz,tmpLayer.Name,newLearnableLayer);
``` 将该层替换为没有类别标签的新层。

```matlab
tmpLayer = graphSqz.Layers(end)
newClassLayer = classificationLayer('Name','newclassout')
graphSqz = replaceLayer(graphSqz,tmpLayer.Name,newClassLayer);
``` 检查网络最后已更改的 dropout、卷积和输出层。

```matlab
ans =
6x1 Layer array with arrays:
| 'new dropout' | Dropout | 60% dropout |
| 'new conv' | Convolution | 1x1 convolutions with stride [1 1] |
| 'relu10' | ReLU | ReLU |
| 'pool10' | Global Average Pooling | Global average pooling |
| 'prob' | Softmax | softmax |
| 'newclassout' | Classification Output | |
```

# 为 SqueezeNet 准备数据

RGB 图像具有适用于 GoogleNet 架构的维度。创建 augmented image datastore 自动调整现有 RGB 图像以适应 SqueezeNet 架构。更多信息请参见 augmentedImageDatastore。

```matlab
augimsTrain = augmentedImageDatastore({227 227},imgsTrain);
augimsValidation = augmentedImageDatastore({227 227},imgsValidation);
```

# 设置训练选项并训练 SqueezeNet

创建一个用于 SqueezeNet 的训练选项。将随机设置为默认值并训练网络。训练过程在桌面 CPU 上通常 1-5 分钟。

```matlab
ilr = 3e-4;
miniBatchSize = 10;
maxEpochs = 15;
valFreq = floor(numel(augimsTrain.Files)/miniBatchSize);
opts = trainingOptions('sgdm',
'MiniBatchSize',miniBatchSize,
'MaxEpochs',maxEpochs,
'InitialLearnRate',ilr,
'ValidationData',augimsValidation,
'ValidationFrequency',valFreq,
'Verbose',1,
'ExecutionEnvironment','cpu',
'Plots','training-progress');
```

```matlab
rng default
trainedSN = trainNetwork(augimsTrain,graphSqz,opts);
```

