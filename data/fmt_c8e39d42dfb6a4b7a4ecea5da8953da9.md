
绘制每个 ECG 类别的代表性图。辅助函数 `helperPlotReps` `ECGData` 作为输入。你可以在此示例末的“辅助函数”部分找到该辅助函数的源代码。

```matlab
helperPlotReps(ECGData)
```

# 10 个特色示例

![](img/747bfd4f288a7e0917a1f27637cc5c2d_237_0.png)

## 创建时频表示

创建文件夹后，创建 ECG 信号的时频表示。这些表示被称为尺度图（scalograms）。尺度图是信号的 CWT 系数的绝对值。

要创建尺度图，请预先计算 CWT 滤波器组。当在使用相同参数对多个信号进行 CWT 时，预计算 CWT 滤波器组是首选方法。

在生成尺度图之前，检查其中一个。使用 `cfilterbank` 为具有 1000 个样本的信号创建一个 CWT 滤波器组。使用该滤波器组对信号的前 1000 个样本进行 CWT，并从系数获取尺度图。

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

使用辅助函数 `helperCreateRGBfromTF` 将尺度图创建为 RGB 图像，并将它们写入 `dataDir` 中相应的子目录。该辅助函数的源代码位于此示例末尾的辅助函数中。为了兼容 GoogLeNet 架构，每个 RGB 图像都是大小为 224-by-224-by-3 的数组。

```matlab
helperCreateRGBfromTF(ECListData,parentDir,dataDir)
```

### 划分训练和验证数据

将尺度图加载为 image datastore。`imageDatastore` 函数通过文件夹名称自动标记图像并存储为 image datastore 对象。image datastore 允许存储无法内存的大型图像，并在训练期间高效读取批量图像。

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

`SqueezeNet` 是一个深度 CNN，支持尺寸为 227-by-227-by-3 的图像。尽管维度与 GoogleLeNet 不同，但不需要生成新的 RGB 图像。加载自定义的 SqueezeNet 网络。

```matlab
sqz = squeeze;
```

从网络中提取图。确认 SqueezeNet 的层数比 GoogleLeNet 少。

```matlab
graphSqz = layerGraph(sqz);
disp('Number of Layers: ',numel(graphSqz.Layers));
disp(graphSqz.Layers(end).InputSize)
```

## 修改 SqueezeNet 参数

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
```

与 GoogleLeNet 不同，SqueezeNet 中的可学习层是 1-by-1 卷积层 'conv10$，而不是全连接。将 'conv10' 替换为数量等于类别数量的卷积层。像 GoogleLeNet 一样，增加新层的学习率。

```matlab
numClasses = numel(categories(imgsTrain.Labels));
tmpLayer = graphSqz.Layers(end-4);
```

使用部署到 FPGA 的 DAG 网络对 ECG 信号进行分类

```matlab
newLearnableLayer = convolution2dLayer(1,numClasses, ...
'Name', 'new conv', ...
'WeightLearnRateFactor',10, ...
'BiasLearnRateFactor',10)
graphSqz = replaceLayer(graphSqz,tmpLayer.Name,newLearnableLayer);
```

将该层替换为没有类别标签的新层。

```matlab
tmpLayer = graphSqz.Layers(end)
newClassLayer = classificationLayer('Name','newclassout')
graphSqz = replaceLayer(graphSqz,tmpLayer.Name,newClassLayer);
```

检查网络最后已更改的 dropout、卷积和输出层。

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

RGB 图像具有适用于 GoogleNet 架构的维度。创建 augmented image datastore 自动调整现有 RGB 图像以适应 SqueezeNet 架构。更多信息请参见 `augmentedImageDatastore`。

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

# 初始化输入数据归一化。

| Epoch | 迭代 | 已用时间 (hh:mm:ss) | 批量准确率 | 验证准确率 | 批量损失值 |
|---|---|---|---|---|---|
| 1 | 1 | 00:00:06 | 60.00% | 53.12% | 4.2000 |
| 1 | 13 | 00:00:16 | 60.00% | 62.50% | 0.9170 |
| 2 | 26 | 00:00:25 | 60.00% | 59.38% | 0.7670 |
| 3 | 39 | 00:00:35 | 60.00% | 62.50% | 0.7033 |
| 4 | 50 | 00:00:42 | 70.00% | 81.25% | 0.5941 |
| 4 | 52 | 00:00:44 | 70.00% | | 0.4883 |
| 5 | 65 | 00:00:53 | 90.00% | 84.38% | 0.3627 |
| 6 | 78 | 00:01:02 | 90.00% | 84.38% | 0.3157 |
| 8 | 100 | 00:01:11 | 90.00% | 87.50% | 0.2145 |
| 8 | 104 | 00:01:20 | 90.00% | 84.38% | 0.2166 |
| 10 | 117 | 00:01:29 | 100.00% | 90.62% | 0.0720 |
| 10 | 130 | 00:01:38 | 90.00% | 90.62% | 0.0643 |
| 11 | 143 | 00:01:41 | 100.00% | 93.75% | 0.0443 |
| 12 | 150 | 00:01:51 | 100.00% | | 0.1377 |
| 12 | 156 | 00:01:56 | 90.00% | 90.62% | 0.1190 |
| 13 | 169 | 00:02:04 | 80.00% | 87.50% | 0.4859 |
| 14 | 182 | 00:02:13 | 100.00% | 87.50% | 0.0395 |
| 15 | 195 | 00:02:22 | 100.00% | 84.38% | 0.0399 |

![](img/747bfd4f288a7e0917a1f27637cc5c2d_241_0.png)
![](img/747bfd4f288a7e0917a1f27637cc5c2d_241_1.png)
![](img/747bfd4f288a7e0917a1f27637cc5c2d_241_2.png)
![](img/747bfd4f288a7e0917a1f27637cc5c2d_241_3.png)
![](img/747bfd4f288a7e0917a1f27637cc5c2d_241_4.png)

检查网络的最后一层。确认分类输出层包含这三个类。

# trainedSN.Layers(end)

ans = 
ClassificationOutputLayer 属性:

```
Name: 'new classout'
Classes: [ARR CHF NSR]
ClassWeights: 'none'
OutputSize: 3
```

超参数
LossFunction: 'crossentropy' 

# 评估 SqueezeNet 准确率

使用验证数据评估网络。
`[Ypred,probs] = classify(trainedSN,augimgsValidation)`
`accuracy = mean(Ypred=ImgsValidation.Labels)`
`disp('SqueezeNet Accuracy:', num2str(100*accuracy),'%')`

SqueezeNet 准确率: 84.375%

## 创建目标对象

使用 `dhdl.Target` 为你的目标设备创建一个自定义名称的目标对象，并创建一个连接目标设备到主机计算机的接口。接口选项有 JTAG 和以太网。要使用 JTAG，请安装 Xilinx™ Vivado Design Suite 2019.2。设置 Xilinx Vivado 工具路径，输入：

```matlab
% dhdlsetuppath('TargetName', 'Xilinx', 'ToolPath', 'C:\Xilinx\Vivado\2019.2\bin\vivado.exe')
```

```matlab
hTarget = dhdl.Target('Xilinx', 'Interface', 'Ethernet');
```

## 创建 Workflow 对象

使用 `dhdl.Workflow` 创建对象。创建对象时，指定网络、位流和目标 FPGA 板。在此示例中，目标 FPGA 板是 Xilinx ZCU102 SoC 板。位流使用单一类型

```matlab
hw = dhdl.Workflow('Network', trainedSN, 'Bitstream', 'zcu102_single', 'Target',hTarget)
```

Workflow 属性：

```
Network: [1x DAG]
Bitstream: 'zcu102_single'
ProcessorConfig: []
Target: [1x dhdl.Target]
```

# 编译修改后的 SqueezeNet DAG 网络

要编译训练好的 SN DAG 网络，运行 `dhdl.Workflow` 对象的 compile 方法。

```matlab
dn = hw.compile
```
