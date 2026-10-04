

# 另请

参见第 4-4 页“FPGA 深度学习解决方案与工作流”

# FPGA 深度学习解决方案与工作流

图展示了在 FPGA 上实现深度学习的 MATLAB 解决方案。

![](img/747bfd4f288a7e0917a1f27637cc5c2d_23_0.png)

FPGA 深度学习解决方案提供了端到端的解决方案，允许您对自定义的预训练系列网络进行估计、编译、分析和调试。您还可以生成自定义的深度学习处理器 IP。估算器用于估计深度学习框架在速度方面的性能。编译器将预训练的深度学习网络转换为当前应用程序，以便将其部署到目标 FPGA 板卡上。

要了解更多关于深度学习处理器 IP 的信息，请参第 12-2 页的“深度学习处理器 IP 核心”。

FPGA 具有以下优势：

- 高性能
- 灵活的接口
- 数据并行
- 模型并行
- 流水线并行

# FPGA 深度学习工作流

要运行某些 FPGA 深度学习任务，请参考下表列出的信息。

| 任务 | 工作流 |
|---|---|
| 在您的目标 FPGA 板卡上运行预训练系列网络。 | 第 5-2 页“FPGA 和 SoC 上的深度学习网络原型工作流” |
| 为预配置的深度学习处理器获取您的预训练系列网络的性能。 | 第 8-3 页“估计深度学习网络的性能” |
| 自定义深度学习处理器以满足您的面积资源约束。 | 第 8-9 页“估算自定义处理器配置的资源利用率” |
| 为您的 FPGA 生成自定义的深度学习处理器。 | 第 9-2 页“生成自定义位流” |
| 了解量化您的预训练系列网络的处。 | 第 11-2 页“深度神经网络的量化” |
| 比较量化后的预训练系列网络与单数据类型预训练系列网络的准确性。 | 第 11-14 页“验证” |
| 在您的目标 FPGA 板卡上运行量化的预训练系列网络。 | 第 11-17 页“代码生成与部署” |

# 工作流与 API

- 第 5-2 页“FPGA 和 SoC 上的深度学习网络原型工作流”
- 第 5-4 页“分析推理运行”
- 第 5-6 页“多帧支持”

# FPGA 和 SoC 上的深度学习网络原型工作流

要原型化并部署您的自定义系列深度学习网络，请创建一个 `dlhdl.Workflow` 类的对象。使用此对象完成以下任务：

- 使用 `deploy` 函数在指定的目标 FPGA 或 SoC 板卡上编译并部署深度学习网络。
- 使用 `getBuildInfo` 函数检索位流资源利用率。
- 使用 `predict` 函数执行部署的深度学习网络并预测输入图像的分类。
- 使用 `predict` 函数计算部署的深度学习网络的速度并进行分析。将 `Profile` 参数设置为 `on`。

此图展示了将深度学习网络部署到 FPGA 板卡的工作流。

![](img/747bfd4f288a7e0917a1f27637cc5c2d_27_0.png)

# 另请

dldl.Target | dldl.Workflow

# 更多关于

- 第 10-5 页“在 Xilinx ZCU102 SoC 上开始深度学习 FPGA 部署”

分析推理运行

通过我们的预训练系列网络查看层、卷积模块和全连接模块的网络预测和性能数据。示例展示了如何获取 ResNet-18 网络的预测和分析结果。

1. 使用 `dhdl.Workflow` 类创建 `Workflow` 类对象。
2. 为工作流对象设置预训练的深度学习网络和位流。
3. 创建 `dhdl.Target` 类对象并指定目标向量和接口。
4. 若要在指定的目标 FPGA 板卡上部署网络，调用工作流对象的 `deploy` 方法。
5. 调用工作流对象的 `predict` 函数。提供图像数组作为 `InputImageParameter`。提供参数以开启分析器。

分类图像的标签存储在结构体 `struct` 中并显示在屏幕上。速度和延迟的性能参数在结构体 `struct` 中返回。

使用此图像运行代码：

![](img/747bfd4f288a7e0917a1f27637cc5c2d_29_0.png)

```
snet = resnet18;
ht = dhdl.Target('Xilinx', 'Interface', 'Ethernet');
hw = dhdl.Workflow('Net', snet, 'Bitstream', 'zcu102_single', 'Target',ht);
hw.deploy;
image = read('zebra.jpg');
inputImg = resize(image, [224, 224]);
nimshow(inputImg);
[prediction, speed] = nw.predict(single(inputImg), 'Profile', 'on');
val, idx = max(prediction);
snet.Layers(end).ClassNames(idx)
```

```
### Finished writing input activations.
### Running simple input activations.
```

深度学习处理器 | 性能结果

| 末帧延迟(Cycles) | 末帧延迟(秒) | 帧数 | 总延迟 | 帧/秒 |
| --- | --- | --- | --- | --- |
| Network | 23659630 | 0.10754 | 1 | 23659630 | 9.3 |
| convl | 2224115 | 0.01011 | | | |
| pool | 572867 | 0.00260 | | | |
| res2a branch2a | 972699 | 0.00442 |
| res2a branch2b | 972568 | 0.00442 |
| res2a | 209312 | 0.00095 |
| res2b branch2a | 972723 | 0.00442 |
| res2b branch2b | 973082 | 0.00442 |
| res2b | 209756 | 0.00095 |
| res3a branch2a | 747587 | 0.00340 |
| res3a branch2b | 904291 | 0.00411 |
| res3a branch3 | 537603 | 0.00435 |
| res3b branch2a | 104750 | 0.00411 |
| res3b branch2b | 904389 | 0.00411 |
| res3b | 904367 | 0.00408 |
| res4a | 104886 | 0.00221 |
| res4a branch2b | 485602 | 0.00400 |
| res4a branch1 | 800081 | 0.00221 |
| res4b branch2a | 486429 | 0.00224 |
| res5a branch2a | 747587 | 0.00340 |
| res5a branch2b | 904291 | 0.00411 |
| res5a branch3 | 537603 | 0.00435 |
| res5b branch2a | 104750 | 0.00411 |
| res5b branch2b | 904389 | 0.00411 |
| res5b | 904367 | 0.00408 |

