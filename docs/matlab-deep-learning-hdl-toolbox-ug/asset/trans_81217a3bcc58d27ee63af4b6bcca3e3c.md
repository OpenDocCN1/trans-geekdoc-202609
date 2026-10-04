

# 10 个精选示例

fc 117059 0.00053
* DL 处理器的时钟频率为：220MHz

深度学习处理器分析器性能结果

| | 上一帧延迟(周期) | 上一帧延迟(秒) | 帧数 |
|---|---|---|--|
| Network | 9008122 | 0.04131 | 1 |
| conv1 | 713003 | 0.00324 | |
| norm1 | 460513 | 0.00209 | |
| pool1 | 890803 | 0.00040 | |
| conv2 | 910726 | 0.00414 | |
| norm2 | 270238 | 0.00123 | |
| pool2 | 92773 | 0.00042 | |
| conv3 | 297151 | 0.00135 | |
| conv4 | 238132 | 0.00108 | |
| conv5 | 166451 | 0.00076 | |
| pool5 | 19561 | 0.00009 | |
| fc6 | 3955517 | 0.01798 | |
| fc7 | 1757860 | 0.00799 | |
| fc | 117054 | 0.00053 | |
* DL 处理器的时钟频率为：220MHz

深度学习处理器分析器性能结果

| | 上一帧延迟(周期) | 上一帧延迟(秒) | 帧数 |
|---|---|---|--|
| Network | 9088305 | 0.04131 | 1 |
| conv1 | 713031 | 0.00324 | |
| norm1 | 460263 | 0.00209 | |
| pool1 | 898948 | 0.00040 | |
| conv2 | 912126 | 0.00414 | |
| norm2 | 270247 | 0.00123 | |
| pool2 | 92514 | 0.00042 | |
| conv3 | 297124 | 0.00135 | |
| conv4 | 238252 | 0.00108 | |
| conv5 | 166320 | 0.00076 | |
| pool5 | 19519 | 0.00009 | |
| fc6 | 3955853 | 0.01798 | |
| fc7 | 1757867 | 0.00799 |
| fc | 117055 | 0.00053 |
* DL 处理器的时钟频率为：220MHz

ans = 'aldi'

label = 'aldi'

### 完成输入激活写入。
### 正在运行简单的输入激活。

# 深度学习处理器分析器性能结果

| 网络 | 上一帧延迟(周期) | 上一帧延迟(秒) | 帧数 |
|---|---|---|--|
| | 9088168 | 0.04131 | 1 |
| conv1 | 713087 | 0.00324 | 9 |
| norm1 | 460226 | 0.00209 | |
| pool1 | 89136 | 0.00041 | |
| conv2 | 910865 | 0.00414 | |
| norm2 | 270243 | 0.00123 | |
| pool2 | 92511 | 0.00042 | |
| conv3 | 297117 | 0.00135 | |
| conv4 | 238363 | 0.00108 | |
| conv5 | 166485 | 0.00076 | |
| pool5 | 19504 | 0.00009 | |
| fc6 | 3955608 | 0.00198 | |
| fc7 | 1757867 | 0.00799 | |
| fc | 117068 | 0.00053 | |
* DL 处理器的时钟频率为：220MHz

ans = 'corona'

label = 'corona'

# ford

# 马

![](img/747bfd4f288a7e0917a1f27637cc5c2d_187_0.png)
![](img/747bfd4f288a7e0917a1f27637cc5c2d_187_1.png)

# aldi

# 冕

![](img/747bfd4f288a7e0917a1f27637cc5c2d_187_2.png)
![](img/747bfd4f288a7e0917a1f27637cc5c2d_187_3.png)

# 另请

- dlquantizer
- 校
- 第1页的“深度神经网络量化”
- 第5页的“FPGA 和 SoC 上的原型深度学习网络”

# 为 FPGA 部署量化网络

此示例展示了如何量化神经网络卷积层中的可学习参数，并验证量化网络。通过 MATLAB 仿真或 FPGA 快速构建量化网络的原型。对于此示例，您需要：

- Deep Learning Toolbox™
- Deep Learning HDL Toolbox
- Deep Learning Model Quantization Library
- 用于 FPGA 和 SoC 设备的 Deep Learning HDL Support Package
- 深度学习库的 MATLAB 接口

# 加载预训练网络

要加载预训练的 AlexNet 网络并分析架构：

```matlab
snet = getNetwork;
analyzeNetwork(snet)
```
![](img/747bfd4f288a7e0917a1f27637cc5c2d_188_0.png)

# 定义校准和验证集

此示例使用最新数据集。数据集包含 320 张图像。每张图像的大小为 227x227，并具有三个通道（RGB）。使用数据数据集进行校准和验证。通过将验证数据减少到 20 张来快速构建量化网络的原型。FPGA 工作流具有 5 张图像。将验证数据减少到单张图像。

```matlab
curDir = pwd;
newDir = fullfile(curDir,'examples','deeplearning_shared');
copyfile(newDir,curDir,'f');
unzip('dataset.zip');
imageData = datastore('*.JPG','LabelSource','fold');
calibrationData,validationData = split(imageData,0.5,randomize);
validationDataReduced = validationData.subset(20);
validationDataSimulation = validationData.subset(1);
```

# 创建量化对象

创建一个 dlquantizer 对象并指定要量化的网络。为 FPGA 指定执行环境。在第二个量化对象上使用 MATLAB 仿真：

```matlab
dQuantObj_simulation = dlquantizer(net,'ExecutionEnvironment','FPGA','Simulation','on');
dQuantObj_FPGA = dlquantizer(net,'ExecutionEnvironment','FPGA');
```

# 校准量化网络

使用 calibrate 函数输入输入运行网络并收集范围。calibrate 执行网络并收集权重和偏置的动态范围。calibrate 返回一个表格。表格中的每行对应量化网络中的一个参数。

```matlab
dQuantObj_simulation.calibrate(calibrationData_reduced)
```

| 优化层名称 | 层名称 | 可学习参数/激活值 | 最小值 |
|---|---|---|---|
| conv_1 Weights | conv_1 | Weights | -0.0489 |
| conv_1 Bias | conv_1 | Bias | 0.9999 |
| conv_2 Weights | conv_2 | Weights | -0.0551 |
| conv_2 Bias | conv_2 | Bias | -0.000617 |
| conv_3 Weights | conv_3 | Weights | -0.0459 |
| conv_3 Bias | conv_3 | Bias | -0.0852 |
| conv_4 Weights | conv_4 | Weights | 0.0456 |
| conv_4 Bias | conv_4 | Bias | -0.0016 |
| fc_1 Weights | fc_1 | Weights | -0.0539 |
| fc_1 Bias | fc_1 | Bias | -0.080523 |
| fc_2 Weights | fc_2 | Weights | -0.0215 |
| fc_2 Bias | fc_2 | Bias | -0.001756 |
| fc_3 Weights | fc_3 | Weights | -0.0507 |
| fc_3 Bias | fc_3 | Bias | -0.0295 |
| imageinput | imageinput | Activations | |
| imageinput_normalization | imageinput | Activations | -139.34 |

# 为 FPGA 部署量化网络

dlQuantObj_FPGA.calibrate(calibrationData_reduced)

