

# 10 个特色示例

![](img/747bfd4f288a7e0917a1f27637cc5c2d_113_0.png)

# 量化并部署训练好的 BlemNet 网络

训练好的 BlemNet 网络将性能提升至每秒 45 帧。部署网络的目标性能为每秒 100 帧，同时保持在目标资源利用预算内。资源利用预算考虑了内存大小、板载 IO 等参数。增加资源利用可能意味着选择更大的板卡，从而增加成本。通过量化网络提高部署网络的性能并保持在资源利用预算内。要量化并部署训练好的 BlemNet：

- 将数据集加载为 imageastore。imageData 根据文件夹名称对图像进行标记并存储数据。将数据分为校准集和验证集。使用 50% 的图像进行校准，50% 用于验证。使用校准和验证图像子集来加速校准和验证过程。

```matlab
if -isfile 'dataset.zip'
  url = 'https://www.mathworks.com/supportfiles/dlhdl/dataset.zip';
  websave('dataset.zip',url)
end
unzip('dataset.zip')
imageData = imageDatastorefullfile('dataset',
    'IncludeFolders',true, 'FileExtensions',''.PNG', 'LabelSource','foldernames'),
[calibrationData, validationData] = splitLabel(imageData, 0.5, 'randomized');
calibrationData_reduced = calibrationData.subset(1:20);
validationData_reduced = validationData.subset(1:1);
```

- 使用 dlquantizer 对象创建量化网络。将目标执行环境设置为 FPGA。

```matlab
dlQuantObj = dlquantizer(snet_blemdenet, 'ExecutionEnvironment', 'FPGA')
```

# 缺陷检测

dlQuantObj =
具有属性的 dlquantizer：

NetworkObject: [1xSeriesNetwork]
ExecutionEnvironment: 'FPGA'

- 使用 calibrate 函数使用样本输入执行网络并收集信息。calibrate 函数运行网络，并收集卷积和全连接层中权重和偏置的动态范围，以及网络所有层中激活值的动态范围。calibrate 函数返回一个表格。表格的每行包含量化网络中可学习参数的范围信息。

```matlab
dlQuantObj.calibrate(calibrationData_reduced)
```

| ans=21x5 table | 网络层名称 | 可学习 / 激活值 | 最小值 |
| :--- | :--- | :--- | :--- |
| 'conv1 Weights' } | { 'conv1' } | "Weights" | -0.29022 |
| 'conv1 Bias' } | { 'conv1' } | "Bias" | -0.02187 |
| 'conv2 Weights' } | { 'conv2' } | "Weights" | -0.10499 |
| 'conv2 Bias' } | { 'conv2' } | "Bias" | -0.01018 |
| 'fc1 Weights' } | { 'fc1' } | "Weights" | -0.05159 |
| 'fc1 Bias' } | { 'fc1' } | "Bias" | -0.004897 |
| 'fc2 Weights' } | { 'fc2' } | "Weights" | -0.07156 |
| 'fc2 Bias' } | { 'fc2' } | "Bias" | -0.06286 |
| 'imageinput' } | { 'imageinput' } | "Activations" | 0 |
| 'imageinput_normalization' } | { 'imageinput' } | "Activations" | -184.37 |
| 'relu1' } | { 'relu1' } | "Activations" | -112.18 |
| 'maxpool1' } | { 'maxpool1' } | "Activations" | 0 |
| 'crossnorm' } | { 'crossnorm' } | "Activations" | 0 |
| 'conv2' } | { 'conv2' } | "Activations" | 0 |
| 'relu2' } | { 'relu2' } | "Activations" | -117.79 |

- 创建 dlhdl.Workflow 类的对象。在创建对象时，指定网络和比特流。指定预训练的 dberDetObject dlQuantObj 为网络。确保比特流与你目标的的数据类型和目标 FPGA 板卡匹配。在此示例中，目标 FPGA 是 Xilinx ZCU102 SOC。比特流使用 int8 数据类型。

```matlab
hw = dlhdl.Workflow('Network', dlQuantObj, 'Bitstream', 'zcu102_int8', 'Target', hT);
```

- 要编译量化网络，运行 dlhdl.Workflow 对象的 compile 函数。

```matlab
hw.compile(InputFrameLength,.30)
```

### 正在为深度学习 FPGA 原型编译网络...
### 目标 FPGA 比特流 zcu102_int8 *
### 网络包含以下层：
1 'imageinput' 图像输入 128x128x1 图像，带有 'zerocenter' 归一化
2 'conv1' 卷积 20x5x5 卷积，步长为 1
3 'relu2' ReLU
4 'maxpool1' 最大池化 2x2，步长为 2
5 'crossnorm' 归一化，步长为 5
6 'conv_2' 卷积 20x5x20 卷积，步长为 1
7 'relu_2' ReLU
8 'maxpool_2' 最大池化 2x2，步长为 2
9 'fc_1' 全连接层
10 'fc_2' 全连接层
11 'softmax' Softmax
12 'classout' 输出，类别为 'ng' 和 'ok'

内存区域已创建。
跳过: imageinput
编译>>maxpool 2
编译>>pool2 完成。
跳过: softmax
跳过: classoutput
正在计划...
计划...完成。
正在状态表...
状态表...完成。
正在发布计划...
计划...完成。
正在状态表...
状态表...完成。

### 正在分配内存：

| 偏移名称 | 偏移地址 | 分配空间 |
| :--- | :--- | :--- |
| "InputDataOffset" | "0x00000000" | 16.0 MB |
| "OutputOffset" | "0x01000000" | 4.0 MB |
| "SchedulerDataOffset" | "0x0140000" | 4.0 MB |
| "SystemBufferOffset" | "0x01800000" | 28.0 MB |
| "InstructionDataOffset" | "0x0240000" | 4.0 MB |
| "ConvWeightDataOffset" | "0x0380000" | 4.0 MB |
| "FCWeightDataOffset" | "0x03c0000" | 12.0 MB |
| "EndOffset" | "0x0400000" | 总计: 72.0 MB |

### 网络连接完成。

```matlab
ans = struct，字段为：
  weights: [1x struct]
  instructions: [1x struct]
  registers: [1x struct]
  syncInstructions: [1x struct]
```

- 要 Xilinx ZCU102 SoC 上部署网络，运行 dlhdl.Workflow 对象的 deploy 函数。该函数使用 compile 函数的输出对 FPGA 板进行编程。它还会下载网络权重和偏置。

deploy 函数启动 FPGA 设备，显示进度以及部署网络所需的时间。

# HW:deploy

```matlab
### 正在通过以太网编程 FPGA 比特流...
正在通过以太网向 SD 卡传输目标 FPGA 设备配置 ...
# 拷贝 /tmp/hdlcoder_rd 到 /mnt/hdlcoder_rd
# 拷贝 hdlcoder.system.bit 到 /mnt/hdlcoder_rd
# 设置比特流到 hdlcoder/rd/system.bit
# 拷贝设备树到 hdlcoder_rd
# 设置设备树到 hdlcoder_rd/devicree.dtb
# 启动参考设计: 'AXI-Stream DDR Memory Access : 3-AXIM'
```

通过以太网向 SD 卡传输目标 FPGA 设备配置完成。系统现在将

系统正在重启。

![](img/747bfd4f288a7e0917a1f27637cc5c2d_116_0.png)

```matlab
### FPGA 比特流编程已完成。
### 正在加载权重到 Conv Processor。
### 权重已加载。当前时间为 2020-12-16 16:18:03
### 正在加载权重到 FC Processor。
### 权重已加载。当前时间为 2020-12-16 16:18:03
```

- 从 attachedImages 文件夹加载图像，调整图像大小以匹配网络输入层维度，并运行 dlhl.Workflow 对象的 predict 函数从 FPGA 获取并显示缺陷预测。

```matlab
wi = uint32(320);
he = uint32(240);
ch = uint32(3);
```

# 10 个特色示例

```matlab
filename = fullfile(pwd, 'ok1.png');
img = imread(filename);
img = resize(img, [he, wi]);
img = mat2ocv(img);

% 预处理提取 ROI
[Iori, imgPacked, bbox] = myDNNet_Preprocess(img);

% 行优先到列优先转换
imgPacked2 = zeros([128, 128, 4], 'uint8');
for c = 1:4
  for i = 128
    for j = 128
      imgPacked2(i,j,c) = imgPacked((i-1)*128 + (j-1) + (c-1)*128 + 1);
  end
end

% 通过 CNN 分类检测到的对象
scores = zeros(2,4);
for i = 1:num
  [scores(:,i), speed] = HW.predict(single(imgPacked2), 'Profile', 'on');
```

### 激活值写入完成。
正在运行输入激活值。

深度学习处理器分析器结果

| | 上次帧延迟(周期) | 上次帧延迟(秒) | 总计 |
|---|---|---|---|
| Network | 1754969 | 0.00798 | 1 |
| conv_1 | 271340 | 0.00123 | |
| maxpool_1 | 87533 | 0.00040 | |
| crosshorn | 125737 | 0.00057 | |
| conv_2 | 149972 | 0.00068 | |
| maxpool_2 | 19657 | 0.00009 | |
| fc_1 | 108568 | 0.00043 | |
| fc_2 | 14928 | 0.00007 | |

> * 学习处理器的时钟频率为：220MHz

```matlab
% Iori = reshape([Iori, [1, he*wi]);
bbox = reshape(bbox, [1,16]);
scores = reshape(scores, [1, 8]);
```

```matlab
% 为后处理插入注释
out = myDNNet_Postprocess(Iori, num, bbox, wi, he);
```

```matlab
sz = [he wi];
out = ocv2mat(out,sz);
imshow(out)
```

