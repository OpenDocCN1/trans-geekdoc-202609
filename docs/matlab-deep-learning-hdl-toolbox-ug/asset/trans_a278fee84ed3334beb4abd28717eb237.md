

## 第三方合成工具与版本支持

- Xilinx Zynq-7000 ZC706.
- Intel Arria 10 SoC.
- Xilinx Zynq UltraScale+™ MPSoC ZCU102.

深度学习 HDL 工具箱已在以下版本中进行过测试：

- Xilinx Vivado HDL Design Suite 2020.1
- Intel Quartus Prime 18.1

## 另另

## 更多关于

- “配置特定板的设置信息”

## 自定义处理器配置工作流

- 第 8-2 页“自定义处理器配置工作流”
- 第 8-3 页“估计深度学习网络的性能”
- 第 8-9 页“估计自定义处理器配置的资源利用率”
- 第 8-15 页“自定义深度学习处理器参数对性能和资源利用率的影响”

## 自定义处理器配置工作流

通过实验深度学习处理器卷积和全连接模块的设置，估计您的自定义处理器配置的性能和资源利用率。有关深度学习处理器的更多信息，请参阅第 2-2 页的“深度学习处理器架构”。有关卷积和全连接模块参数的信息，请参阅“属性”。

在配置您的自定义深度学习处理器后，您可以构建并生成自定义位流和自定义深度学习处理器 IP 核。有关自定义深度学习处理器 IP 核的更多信息，请参阅第 12-2 页的“深度学习处理器 IP 核”。

图像显示了自定义深度学习处理器、估计自定义深度学习性能和资源利用率，以及构建并生成自定义深度学习处理器 IP 核和位流的工作流。

```
创建一个 ProcessorConfig 对象
hPC = dhdli.ProcessorConfig()
```

```
使用 ProcessorConfig 对象创建一个工作流对象
hW = dhdli.Workflow('Network',snet,ProcessorConfig,hPC)
```

```
为自定义处理器构建并生成代码
dhdli.buildProcessor(hPC)
```

```
估计工作流对象的性能
hW.estimate('Performance')
```

## 另另

estimatePerformance | estimateResources | dhdli.ProcessorConfig | getModuleProperty | setModuleProperty

## 更多关于

- 第 2-2 页“深度学习处理器架构”
- 第 8-3 页“估计深度学习网络的性能”
- 第 8-9 页“估计自定义处理器配置的资源利用率”

## 估计深度学习网络的性能

为了缩短设计满足性能要求的自定义深度学习网络所需的时间，在部署网络之前，请分析层延迟。比较深度学习网络在自定义位流处理器上的性能与在参考（出厂）位流处理器配置上的性能。

要学习如何使用 `estimatePerformance` 函数的表格数据信息来计算您的网络性能，请参阅第 5-4 页的“分析推理运行”。

## 针对自定义处理器配置估计自定义深度学习网络的性能

此示例演示了如何为自定义处理器配置计算深度学习网络的性能。

- 1 在您的工作文件夹中创建一个名为 `getLogonNetwork.m` 的文件。在文件中输入：
```matlab
function net = getLogonNetwork())
if isfile('Logonet.mat')
    url = 'https://www.mathworks.com/supportfiles/pgucoder/cnn_models/logonet.mat';
    webave = load('Logonet.mat').conv;
else
    data = load.convnet;
end
```

调用该函数并保存结果。
snet = getLogonNetwork();

- 2 创建 `dhldl.ProcessorConfig` 对象。
hPC = dhldl.ProcessorConfig;

- 3 使用 `snet` 调用 `estimatePerformance` 以检索 Logonet 网络的层延迟和性能。
hPC.estimatePerformance(snet)

3 创建了 3 个内存区域。

| 网络 | 上次延迟(周期) | 上次延迟(秒) | 帧数 | 总延迟 |
|---|---|---|---|---|
| conv_1 | 39853 | 0.19927 | 1 | 39853 |
| maxpool_1 | 60252 | 0.03013 | 1 | 60252 |
| conv_2 | 37558 | 0.01878 | 1 | 37558 |
| maxpool_2 | 10440 | 0.0052 | 1 | 10440 |
| conv_3 | 14786 | 0.00724 | 1 | 14786 |
| maxpool_3 | 9393 | 0.00469 | 1 | 9393 |
| conv_4 | 17658 | 0.00883 | 1 | 17658 |
| maxpool_4 | 17780 | 0.00885 | 1 | 17780 |
| fc_1 | 20890 | 0.01014 | 1 | 20890 |
| fc_2 | 16925 | 0.00846 | 1 | 16925 |
| fc_3 | 8929 | 0.00445 | 1 | 8929 |

* DL 器的时钟频率为: 200MHz

要了解 `estimatePerformance` 返回的参数，请参见 .

## 自定义处理器配置工作流

在自定义处理器配置上评估深度学习网络的性能

通过将自定义位流处理器与参考（出厂）位流处理器配置的性能进行比较，对深度学习网络进行基准测试。使用比较结果调整您的自定义深度学习处理器参数以获得最佳性能。

在此示例中，我们比较 zcu102_single 位流上的 ResNet-18 网络性能。

## 先决条件

- Xilinx FPGA 和 SoC 深度学习工具箱支持包
- 深度学习工具箱

## ResNet-18 网络

加载预训练网络。

```
snet = resnet18;
```

## 获取 zcu102_single 位流配置

要检索 zcu102_single 位流配置，使用 `dhldl.ProcessorConfig` 对象。有关更多信息，请参见处理器配置的可修改参数，参见 `getModuleProperty` 和 `setModuleProperty`。

```
hPC_shipping = dhldl.ProcessorConfig('Bitstream', 'zcu102_single')
```

```
处理模块: 'conv'
卷积线程数: 16
输入大小: [227 227 3]
输出大小: [227 227 3]
特征大小限制: 2048
数据类型: 'single'
```

```
处理模块: 'fc'
全连接线程数: 4
输入大小: 25088
输出大小: 4096
数据类型: 'single'
```

```
处理模块: 'adder'
输入大小: 40
输出大小: 40
数据类型: 'single'
```

```
系统级属性
目标平台: 'Xilinx Zynq UltraScale+ MPSoC ZCU102 Evaluation K'
目标频率: 220
综合工具: 'Xilinx Vivado'
参考设计: 'AXI-Stream DDR Memory Access : 3-AXIM'
```

8-4

## 深度学习网络的性能

综合芯片族: 'Zynq UltraScale+'
综合设备名称: 'xczu9eg-ffb1156-1'
综合工具名称: ''

## 估计 ResNet-1B zcu102_single 位流

要检索 zcu102_single 位流配置，使用 `dhldl.ProcessorConfig` 对象。有关更多信息，请参见处理器配置的可修改参数，参见 `getModuleProperty` 和 `setModuleProperty`。

```
hPC_custom = dhldl.ProcessorConfig

```

```
hPC_custom = 处理模块 "conv"
```

