

ans = 'espresso maker'

# 对多个图像进行预测

使用多帧支持功能加载多张图像并检索它们的预测结果。更多信息请参阅第 5-6 页的“多帧支持”。

demoOnImage 函数加载多张图像并检索它们的预测结果。annotatorults会将图像预测结果显示在组合成 3x5 数组的图像上方。

```
imshow(inputImg)
```

![](img/747bfd4f288a7e0917a1f27637cc5c2d_101_0.png)

demoOnImage;

### 完成输入激活写入。
### 正在运行单个输入激活。

- FPGA 预测: 信封
- FPGA 预测: 文件
- FPGA 预测: 折叠椅
- FPGA 预测: 混合盆
- FPGA 预测: 马桶桶盖
- FPGA 预测: 餐桌
- FPGA 预测: 信封
- FPGA 预测: 咖啡机
- FPGA 预测: 电脑键盘
- FPGA 预测: 显示器
- FPGA 预测: 鼠标
- FPGA 预测: 圆珠笔
- FPGA 预测: 开信刀
- FPGA 预测: 模拟钟
- FPGA 预测: 灰桶

![](img/747bfd4f288a7e0917a1f27637cc5c2d_102_0.png)

# 缺陷检测

此示例展示了如何部署自定义训练的系列网络来检测六角螺母等对象的缺陷。自定义网络是使用迁移学习训练的。迁移学习常用于深度学习应用。你可以取一个预训练的网络并将其作为起点来学习新任务。使用迁移学习对网络进行微调，通常比从头开始使用随机初始权重训练网络要快且容易。你可以通过较少的训练信号将学习到的特征迁移到新任务。此示例使用了两个训练好的系列网络 DefNet.mat 和 trainedBlemDefNet.mat。

# 前提条件

- Xilinx ZCU102 SoC 开发套
- 用于 Xilinx FPGA 和 SoC 的 Deep Learning HDL Toolbox™ 支持包
- Deep Learning Toolbox™
- Deep Learning HDL Toolbox™

# 加载预训练网络

要下载并加载自定义的预训练系列网络 trainedDefNet 和 trainedBlemDefNet，请输入：

```matlab
if isfile('trainedDefNet.mat')
 url = 'https://www.mathworks.com/supportfiles/dlhdl/trainedDefNet.mat';
 websave('trainedDefNet.mat',url);
end
net1 = load('trainedDefNet.mat');
snet_defnet = net1.custom_alexnet
```

snet_defnet = 
具有属性的 SeriesNetwork：

```
Layers: {25x1 nnet.cnn.layer.Layer}
InputNames: {'data'}
OutputNames: {'output'}
```

分析 snet_defnet 层。

```matlab
analyzeNetwork(snet_defnet)
```

# 缺陷检测

深度学习网络分析器

snet_defnet
分析日期: 2020-7-12 14:16:16

![](img/747bfd4f288a7e0917a1f27637cc5c2d_104_0.png)

```matlab
if isfile('trainedBlemDetNet.mat')
    url = 'https://www.mathworks.com/supportfiles/dlhdl/trainedBlemDetNet.mat';
    websave('trainedBlemDetNet.mat', url);
end
net2 = load('trainedBlemDetNet.mat');
net_blemdetnet = net2.convnet
snet_blemdetnet = 
具有属性的 SeriesNetwork：
    Layers: {1x1 nnet.cnn.layer.Layer}
    InputNames: {'imageinput'}
    OutputNames: {'classoutput'}
```

```matlab
analyzeNetwork(snet_blemdetnet)
```

# 10 个特色示例

![](img/747bfd4f288a7e0917a1f27637cc5c2d_105_0.png)

# 创建目标对象

创建一个为你的目标设备创建自定义名称的对象以及一个将目标设备连接到主机计算机的接口。接口选项使用 JTAG 和以太网。要使用 JTAG 连接，请安装 Xilinx™ Vivado™ Design Suite 2020。

要设置 Xilinx Vivado 工具路径：

```matlab
# hdlsetutoolpath('ToolName', 'Xilinx', 'Vivado', 'ToolPath', 'C:\Xilinx\Vivado\2020.1\bin\vivado.')
hT = dhdl.Target('Xilinx', 'Interface', 'Ethernet')
```

hT =
具有属性的 Target：

- 厂商: 'Xilinx'
Interface: Ethernet
IPAddress: '192.168.1.101'
Username: 'root'
Port: 22

# 为 trainedDefNet 网络创建工作流对象

创建一个 dhdl.Workflow 类对象。创建对象时，指定网络和位流名称。将保存的预训练 trainedDefNet 指定为网络。确保位流与你的目标数据类型和 FPGA 板板匹配。在此示例中，目标 FPGA 板板是 Xilinx ZCU102 SOC 板。该位流使用单一数据类型。

hW = dhldl.Workflow('Network', .snet_defnet, 'Bitstream', 'zcu102_single', 'Target',hT)

hW =
具有属性的 Workflow：

```
Network: [1x1 SeriesNetwork]
Bitstream: 'zcu102_single'
ProcessorConfig: []
Target: [1x1 dhldl.Target]
```

# 编译 trainedDefnet 系列网络

要编译 trainedDefnet 系列网络，请运行 dhldl.Workflow 对象的 compile 函数。

```matlab
hW.compile
```

### 正在为深度学习 FPGA 原型编译网络 ...
### 正在目标 FPGA 位流 zcu102_single ...
### 网络包含以下层：

| 层 | 类型 | 详情 |
| :--- | :--- | :--- |
| 'data' | 图像输入 | 128x128x1 图像，带有 'zerocenter' 归一化 |
| 'conv1' | 卷积 | 96 个 11x11 卷积，步长为 [4 和 4] |
| 'relu' | ReLU | ReLU |
| 'norm4' | 跨通道归一化 | 每个通道 5 的归一化 |
| 'pool5' | 最大池化 | 步长为 [ 2 ] 的最大池化 |
| 'conv2' | 分组卷积 | 2 组 128 5x48 卷积 |
| 'relu' | ReLU | ReLU |
| 'norm2' | 跨通道归一化 | 每个通道 5 的归一化 |
| 'pool7' | 最大池化 | 步长为 [ 2 ] 的最大池化 |
| 'conv3' | 卷积 | 384 个 3x3x256 卷积，步长为 [1 ] |
| 'relu' | ReLU | ReLU |
| 'conv4' | 分组卷积 | 2 组 192 3x3x192 卷积 |
| 'relu4' | ReLU | ReLU |
| 'norm4' | 跨通道归一化 | 每个通道 5 的归一化 |
| 'pool5' | 最大池化 | 步长为 [ 2 ] 的最大池化 |
| 'conv2' | 分组卷积 | 2 组 128 5x48 卷积 |
| 'relu' | ReLU | ReLU |
| 'norm2' | 跨通道归一化 | 每个通道 5 的归一化 |
| 'pool7' | 最大池化 | 步长为 [ 2 ] 的最大池化 |
| 'conv3' | 卷积 | 384 个 3x3x256 卷积，步长为 [1 ] |
| 'relu' | ReLU | ReLU |
| 'conv4' | 分组卷积 | 2 组 192 3x3x192 卷积 |
| 'relu4' | ReLU | ReLU |

### 正在为深度学习 FPGA 原型编译网络 ...
### 正在目标 FPGA 位流 zcu102_single ...
### 网络包含以下层：

![](img/747bfd4f288a7e0917a1f27637cc5c2d_107_0.png)

