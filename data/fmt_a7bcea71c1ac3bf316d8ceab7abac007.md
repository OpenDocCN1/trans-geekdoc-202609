
```
hw = dhdl.Workflow('Network', snet, 'Bitstream', 'zcu102 single', 'Target', hTarget)
hw
```

具有属性的 `Workflow`：

`Network`: [1x1 DAGNetwork]

`Bitstream`: ['zcu102_single']

`ProcessorConfig`: []

`Target`: [1x1 dhdl.Target]

# 编译 YOLO v2 对象检测器

要编译 `snet` 系列网络，运行 `dhdl.Workflow` 对象的函数。

```
dn = hw.compile
```

正在为深度学习 FPGA 原型编译 ...

目标 FPGA 位流 `zcu102 single` ...

网络包含以下层：

| 'data' | 图像输入 | 224x224x3 使用'zscore' 归一化的图像 |
|---|---|---|

| 'conv1' | 卷积 | 64 7x7 卷积，步长 [2] |
| 'bn conv1' | 批量归一化 | 64 通道的批量归一化 |
| 'conv1_relu' | ReLU | ReLU |
| 'pool1' | 最大池化 | 3x3 最大池化，步长 [2] |
| 'res2a_branch2a' | 卷积 | 64 3x6 卷积，步长 |
| 'res2a_branch2a' | 批量归一化 | 64 通道的批量归一化 |
| 'res2a_branch2a_relu' | ReLU | ReLU |
| 'res2a_branch2b' | 卷积 | 64 3x6 卷积，步长 |

## 10 个特色示例

| ID | 名称 | 类型 | 描述 |
| :--- | :--- | :--- | :--- |
| 10 | 'bn2a branch2b' | 批归一化 | 6 通道的批归一化 |
| 11 | 'res2a' | 加法 | 2 个输入的逐元素相加 |
| 12 | 'res2a relu' | ReLU | ReLU |
| 13 | 'res2b branch2a' | 卷积 | 64 个 3x3 卷积，步长为 1 |
| 14 | 'bn2b branch2a' | 批归一化 | 6 通道的批归一化 |
| 15 | 'res2b branch2a_relu' | ReLU | ReLU |
| 16 | 'res2b branch2b' | 卷积 | 64 个 3x3 卷积，步长为 1 |
| 17 | 'bn2b branch2b' | 批归一化 | 64 通道的批归一化 |
| 18 | 'res2b' | 加法 | 2 个输入的逐元素相加 |
| 19 | 'res2b relu' | 卷积 | 128 个 3x3 卷积，步长为 stride |
| 20 | 'res3a branch2a' | 批归一化 | 128 通道的批归一化 |
| 21 | 'res3a branch2a_relu' | ReLU | ReLU |
| 22 | 'res3a branch2b' | 卷积 | 128 个 3x2 卷积，步长为 stride |
| 23 | 'bn3b branch2b' | 批归一化 | 128 通道的批归一化 |
| 24 | 'res3b' | 加法 | 2 个输入的逐元素相加 |
| 25 | 'res3a relu' | 卷积 | 128 个 1x4 卷积，步长为 stride |
| 26 | 'bn3a branch1' | 批归一化 | 128 通道的批归一化 |
| 27 | 'res3b branch2a' | 卷积 | 128 个 3x3 卷积，步长为 stride |
| 28 | 'bn3b branch2b' | 批归一化 | 128 通道的批归一化 |
| 29 | 'res3b branch2b' | 卷积 | 256 个 3x2 卷积，步长为 stride |
| 30 | 'res4b' | 加法 | 2 个输入的逐元素相加 |
| 31 | 'res4a relu' | 卷积 | 256 个 1x1 卷积，步长为 stride |
| 32 | 'bn4a branch2a' | 批归一化 | 256 通道的批归一化 |
| 33 | 'res4a branch2a_relu' | ReLU | ReLU |
| 34 | 'res4a branch2b' | 卷积 | 256 个 3x2 卷积，步长为 stride |
| 35 | 'bn4a branch2b' | 批归一化 | 256 通道的批归一化 |
| 36 | 'res4b relu' | 加法 | 2 个输入的逐元素相加 |
| 37 | 'res4a' | 卷积 | 256 个 1x4 卷积，步长为 stride |
| 38 | 'bn4a branch1' | 批归一化 | 256 通道的批归一化 |
| 39 | 'res4b branch2a' | 卷积 | 256 个 3x3 卷积，步长为 stride |
| 40 | 'bn4b branch2a' | 批归一化 | 256 通道的批归一化 |
| 41 | 'res4b branch2_relu' | ReLU | ReLU |
| 42 | 'res4b' | 加法 | 2 个输入的逐元素相加 |
| 43 | 'res4b relu' | 卷积 | 42 个 1x1 卷积，步长为 stride |
| 44 | 'yolov2conv1' | ReLU | ReLU |
| 45 | 'yolov2batch1' | 批归一化 | 256 个 3x2 卷积，步长为 stride |
| 46 | 'yolov2relu1' | ReLU | 256 通道的批归一化 |
| 47 | 'yolov2conv2' | 卷积 | ReLU |
| 48 | 'yolov2batch2' | 批归一化 | 256 通道的批归一化 |
| 49 | 'yolov2relu2' | ReLU | ReLU |
| 50 | 'yolov2ClassConv' | 卷积 | 42 个 1x1 卷积，步长为 stride |
| 51 | 'yolov2Transform' | YOLO v2 变换层 | 带有 7 个锚 的 YOLO v2 变换层 |
| 52 | 'yolov2OutputLayer' | YOLO v2 输出 | 带有 7 个锚的 YOLO v2 输出 |

### 优化系列网络：将 'nn.cnn.layer.BatchNormalization' 合并到 'nn.cnn.layer'
创建了 5 个内存区域。

```
Skipping: data

Compiling: conv1->pool

Compiling: conv1->pool      complete.
```

编译分支: `res2a_branch2>>res2a_branch2`...
编译分支: `res2a_branch2>>res2a_branch2` ... complete.
编译分支: `res2b_branch2>>res2b_branch2` ... complete.
编译分支: `res2a_branch2>>res2b_branch2`...
编译分支: `res3a_branch1` ... complete.
编译分支: `res3a_branch1>>res3a_branch2`...
编译分支: `res3a_branch2>>res3a_branch2` ... complete.
编译分支: `res3b_branch2>>res3b_branch2`...
编译分支: `res3b_branch2>>res3b_branch2` ... complete.
编译分支: `res4a_branch1` ... complete.
编译分支: `res4a_branch2>>res4a_branch2`...
编译分支: `res4a_branch2>>res4a_branch2` ... complete.
编译分支: `res4b_branch2>>res4b_branch2`...
编译分支: `res4b_branch2>>res4b_branch2` ... complete.
编译分支: `yolov2Conv1>>yolov2ClassConv` ... complete.
跳过: `yolov2Conv1>>yolov2ClassConv`
跳过: `yolov2OutputLayer`
正在创建调度...

正在创建调度...完成。
正在创建状态表...。

### 正在分配外部内存：

| 偏移名称 | 偏移地址 | 分配空间 |
| :--- | :--- | :--- |
| InputDataOffset | 0x0000000 | 24.0 MB |
| OutputResultOffset | 0x0180000 | 4.0 MB |
| SchedulerDataOffset | 0x03c0000 | 4.0 MB |
| SystemBufferOffset | 0x0200000 | 20.0 MB |
| InstructionDataOffset | 0x03c0000 | 4.0 MB |
| ConvDataOffset | 0x0400000 | 20.0 MB |
| EndOffset | 0x0540000 | 总计: 84.0 MB |

### 网络完成字段：
`instructions`: [1x1]
`weights`: [1x1]
`registers`: [1x1]
`syncInstructions`: [1x1]

### 特色示例
要在 Zynq UltraScale+ MPSoC 上部署网络，请使用位流运行 `deploy` 函数。该函数还会下载权重偏置。Xilinx Vivado 工具随后使用位流启动 FPGA 设备，并显示部署网络所需的时间。

### 正在向 FPGA 位流...
通过 SD 卡下载目标设备配置。将 `/tmp/hdlcoder_rd` 复制到 `/mnt/hdlcoder_rd`。将 `hdlcoder_system.bit` 复制到 `/mnt/hdlcoder_rd`。设置位流到 `hdlcoder_rd/hdlcoder_system.bit`。将 `devicetree.dt` 复制到 `/mnt/hdlcoder_rd/devicetree.dt`。设置参考设计：'AXI-Stream DDR'：系统正在重启...FPGA 位流已成功完成。权重加载。当前时间为 2021年1月4日 15:59:03

### 加载示例并运行预测
在硬件上执行 `predict` 函数并显示结果：
`prediction, speed = HW.predict(I_re, 'Profile');`

### 完成写入激活。正在运行单个输入激活。

### 深度学习分析器性能结果

| 层 | 上次延迟 (周期) | 上次延迟 (秒) | 帧数 |
| :--- | :--- | :--- | :--- |
| Network | 16974672 | 0.07716 | 1 |
| conv1 | 2224187 | 0.01011 | |
| pool | 573166 | 0.00821 | |
| res2a_branch2 | 972633 | 0.00442 | |
| res2a_branch2 | 972632 | 0.00442 | |
| res2a | 209363 | 0.00095 | |
| res2b_branch2 | 972674 | 0.00442 | |
| res2b_branch2 | 973107 | 0.00442 | |
| res2b | 209914 | 0.00085 | |
| res3a_1 | 538478 | 0.00245 | |
| res3a_branch2 | 740778 | 0.00340 | |
| res3a_branch2 | 904530 | 0.00411 | |
| res3a | 104830 | 0.00048 | |
| res3b_branch2 | 904548 | 0.00411 | |
| res3b_branch2 | 904278 | 0.00411 | |
| res3b | 104900 | 0.00048 | |

### 使用部署到 FPGA 的 DAG 网络 YOLO v2 进行车辆检测

| 层 | 上次延迟 (周期) | 上次延迟 (秒) | 帧数 |
| :--- | :--- | :--- | :--- |
| res4a branch1 | 485804 | 0.00221 | |
| res4a branch2a | 485923 | 0.00221 | |
| res4a branch2b | 880309 | 0.00400 | |
| res4a | 52446 | 0.00024 | |
| res4b branch2a | 880071 | 0.00400 | |
| res4b branch2b | 880065 | 0.00400 | |
| res4b | 52456 | 0.00024 | |
| yolov2Conv1 | 880210 | 0.00400 | |
| yolov2Conv2 | 880375 | 0.00400 | |
| yolov2ClassConv | 179300 | 0.00081 | |

* DL 处理器的时钟为：220MHz

显示预测结果。

```
[bboxes, scoresn, labelsn] = yolo_post_proc(prediction,I_pre,anchorBoxes,{'Vehicle'});

I_new3 = insertObjectAnnotation(I,rectangle,bboxes,scoresn);

figure

imshow(I_new3)
```

![](img/747bfd4f288a7e0917a1f27637cc5c2d_212_0.png)

# 定制位流配置以满足资源使用需求

用户希望将一个目标性能为每秒 500 帧 (FPS) 的数字识别网络部署到 Xilinx ZCU102 ZU4CG 设备上。目标设备的可资源计数如下：

- 数字信号处理器 (DSP) 切片数量 - 240
- 块随机访问内存 (BRAM) 数量 - 128

参考（出厂）`zcu102_int8` 位流配置是针对 Xilinx ZCU102 ZU9EG 设备的。默认板资源计数为：

- 数字信号处理器 (DSP) 切片数量 - 2520
- 块随机访问内存 (BRAM) 数量 - 9128

默认板计数超过了用户的资源预算，且处于成本光谱的高端。你可以通过对深度学习网络进行量化并自定义默认位流配置，来实现目标性能和资源使用预算。

在本示例中，创建一个自定义位流配置以匹配你的资源预算和性能需求。

# 前提条件

- 用于 Xilinx FPGA 和 SoC 的 Deep Learning HDL Toolbox™ 支持包
- Deep Learning Toolbox™
- Deep Learning HDL Toolbox™
- Deep Learning Toolbox Model Quantization Library

# 加载预训练网络

要加载在修改后的美国标准技术学院 (MNIST) 数据库上训练的预训练系列网络，输入：

```matlab
snet = getDigitsNetwork;
```

# 量化网络

要对基于 MNIST 的进行量化，输入：

```matlab
dquantObj = dquantizer(snet, 'ExecutionEnvironment', 'FPGA');

Image = imageDatastore('five_28_28.png', 'Labels', 'five');

dquantObj.calibrate(Image)
```

| 优化后的层名称 | 网络层名称 | 类型 | 数值 |
|---|---|---|---|
| {conv_1_Weights} | {batchnorm_1} | {Weights} | -0.017061 |
| {conv_1_Bias} | {batchnorm_1} | {Bias} | -0.025344 |
| {conv_2_Weights} | {batchnorm_2} | {Weights} | -0.54744 |
| {conv_2_Bias} | {batchnorm_2} | {Bias} | -1.1787 |
| {conv_3_Weights} | {batchnorm_3} | {Weights} | -0.39927 |
| {conv_3_Bias} | {batchnorm_3} | {Bias} | -0.85118 |

# 定制位流配置以满足资源需求

```matlab
{'fc Weights' } {('fc')} "Weights" -0.2258

{'fc Bias' } {('fc')} "Bias" -0.011837

{'imageinput' } {('imageinput')} "Activations" 0

{'imageinput_normalization' } {('imageinput')} "Activations" -22.566

{'conv_1' } {('batchnorm_1')} "Activations" -7.9196

{'relu_1' } {('relu_1')} "Activations" 0

{'maxpool_1' } {('maxpool_1')} "Activations" 0

{'conv_2' } {('('norm_2')} "Activations" -8.6461

{'relu_2' } {('relu_2')} "Activations" 0

{'maxpool_2' } {('maxpool_2')} "Activations" 0
```
