

![](img/747bfd4f288a7e0917a1f27637cc5c2d_118_0.png)

为了测试量化网络能够识别所有测试用例，请部署额外的图像，调整图像大小以匹配网络的图像输入维度，并运行 `dhldl.Workflow` 对象的 `predict` 函数以检索并显示来自 FPGA 的缺陷预测。

```matlab
wi = uint32(328);
he = uint32(240);
ch = uint32(3);
```

```matlab
filename = fullfile(pwd,'okng.png');
img=imread(filename);
img = imresize(img, [he, wi]);
img = mat2ocv(img);
```

```matlab
% 提取预处理的 ROI
Iori, imgPacked, num, bbox = myNNDet_preprocess(img);
```

```matlab
% 行优先到列优先的转换
imgPacked2 = zeros([128,128,4],'uint8);
for c = 1:4
    for i = 1:128
        for j = 1:128
            imgPacked2(i,j,c) = imgPacked(i-1)*128 + (j-1) + (c-1)*128*128;
        end
    end
end
```

```matlab
% 使用 CNN 分类检测到的节点
scores = zeros(2,4);
for i = 1:num
    scores(:,i, speed) = hW.predict(single(imgPacked2(:,:,i)), 'Profile','on');
end
```

### 完成输入激活写入。
### 正在运行单输入激活。

# 10 个特色示例

深度学习处理器分析器性能结果

| 网络 | 上次延迟(周期) | 上次延迟(秒) | 帧数 |
|---|---|---|---|
| conv 1 | 1754614 | 0.00798 | 1 |
| maxpool 1 | 271184 | 0.00123 | | |
| crossnorm | 87557 | 0.00040 | | |
| conv 2 | 125768 | 0.00057 | | |
| maxpool 2 | 149819 | 0.00008 | | |
| fc 1 | 199602 | 0.00009 | | |
| fc 2 | 1085664 | 0.00493 | | |
| * DL 处理器的时钟为: 220MHz | 14930 | 0.00007 | | |

```matlab
### 完成输入激活写入。
### 正在运行单输入激活。
```

深度学习处理器分析器性能结果

| 网络 | 上次延迟(周期) | 上次延迟(秒) | 帧数 |
|---|---|---|---|
| conv 1 | 1754486 | 0.00797 | 1 |
| maxpool 1 | 271014 | 0.00123 | | |
| crossnorm | 87662 | 0.00040 | | |
| conv 2 | 125835 | 0.00057 | | |
| maxpool 2 | 149789 | 0.00068 | | |
| fc 1 | 199661 | 0.00009 | | |
| fc 2 | 1085505 | 0.00493 | | |
| * DL 处理器的时钟为: 220MHz | 14930 | 0.00007 | | |

```matlab
Iori = reshape(Iori, [1, we*ch]);
bbox = reshape(bbox, [1, 16]);
scores = reshape(scores, [1, 8]);
```

```matlab
% 为后处理插入注释
out = myDNNet_Postprocess(Iori, num, bbox, scores, wi, he, ch);
```

```matlab
sz = [he wi ch];
out = cv2mat(out,sz);
imshow(out)
```

10-40

![](img/747bfd4f288a7e0917a1f27637cc5c2d_120_0.png)

量化网络将性能从每秒 45 帧提高到每秒 125 帧，并将部署的网络从 88 MB 减少到 72 MB。

# 为了性能改进分析网络

此示例展示了如何通过分析结果识别瓶颈层来改进部署的深度学习网络的性能。

# 前提条件

- Xilinx ZCU102 SoC 开发套。
- 适用于 Xilinx FPGA 和 SoC 的 Deep Learning HDL Toolbox™ 支持包
- Deep Learning Toolbox™
- Deep Learning HDL Toolbox™

# 加载预训练的 SeriesNetwork

对于预训练的 digits 系列网络，输入：

```matlab
snet = getDigitsNetwork();
```

```matlab
% 查看预训练系列网络的层，
snet.Layers
```

15x1 数组，包含层：

| | |
|---|---|---|
| 'imageinput' | 图像输入 | 带有'zero'归一化的 28x28x1 图像 |
| 'conv_1' | 卷积 | 步长为 [1] 并填充的 8x3x1 卷积 |
| 'batchnorm_1' | 批量归一化 | 8 通道 |
| 'relu' | ReLU | |
| 'maxpool_1' | 最大池化 | 步长为 [2] 并填充的 2x2 最大池化 |
| 'conv_2' | 卷积 | 步长为 [1] 并填充的 16x3x8 卷积 |
| 'batchnorm_2' | 批量归一化 | 16 通道 |
| 'relu_2' | ReLU | |
| 'maxpool_2' | 最大池化 | 步长为 [2] 并填充的 2x2 最大池化 |
| 'conv_10' | 卷积 | 步长为 [1] 并填充的 32x3x16 卷积 |
| 'batchnorm_3' | 批量归一化 | 32 通道 |
| 'relu_3' | ReLU | |
| 'fc' | 全连接 | 10 个全连接层 |
| 'softmax' | softmax | |
| 'classout' | 分类输出 | 'entropy' 和 9 类 |

# 创建目标对象

创建一个具有设备自定义名称以及连接目标设备到计算机接口的目标对象。使用 JTAG 和以太网。对于以太网接口，输入：

```matlab
hTarget = dlhad.Target('Xilinx', 'Ethernet');
```

使用 JTAG 接口，安装 Xilinx "Vivado" 设计套件 2019。如果未设置，请指向安装的 Xilinx Vivado 可执行文件路径。例如，设置工具路径，

```matlab
% settoolpath('ToolName', 'Xilinx Vivado', 'ToolPath', 'C:\Xilinx\Vivado\2019\bin\vivado.')
```

对于 JTAG 接口，输入：

```matlab
% hTarget = dlhad.Target('Xilinx', 'JTAG');
```

# 创建工作流对象

创建 `dhldl.Workflow` 类的对象。当创建对象时，指定网络和位流名称。使用预训练的神经网络 `snet` 作为网络。确保位流名称与数据类型匹配。在本例中，目标板卡是 ZCU102。位流使用单类型（`zcu102`）。

```matlab
% 如果在 ZCU76 板上运行，而不是上面的命令，
% 请取消下面的注释。
% hw = dhldl.Workflow('snet', 'z706', 'Target', hTarget);
```

# 编译 MNIST 系列网络

要编译 MNIST 系列网络，运行 `dhldl.Workflow` 的 `compile` 函数。
dn = hw.compile;

```matlab
### 初始化系列网络：融合 .net.cnn.layer
    offset_address allocated_space
```

| | |
|---|---|
| 输入数据偏移 | 0x00000000 | 4.0 MB |
| 输出结果偏移 | 0x00400000 | 4.0 MB |
| 系统缓冲区偏移 | 0x00800000 | 28.0 MB |
| 指令数据偏移 | 0x02040000 | 4.0 MB |
| 卷积权重数据偏移 | 0x02080000 | 4.0 MB |
| 全连接权重数据偏移 | 0x02c80000 | 4.0 MB |
| 结束偏移 | 0x03080000 | 总计 48.0 MB |

# 将位流到 FPGA 并下载网络权重

要在 Xilinx ZCU102 SoC 硬件上部署网络，运行 `dhldl.Workflow` 对象的 `deploy` 函数。该函数使用编译输出通过编程文件编程 FPGA。还会下载权重和偏置。

```matlab
hw.deploy;
```

### 正在通过以太网编程 FPGA 位流...
正在通过以太网下载目标 FPGA 配置到 SD 卡 ...
% 已将 /tmp/hdlcoder_rd 复制到 /mnt/hdlcoder_rd
% 正在拷贝位流 hdlcoder.bit 到 /mnt/hdlcoder_rd
% 设置位流为 hdlcoder_rd/hdlcoder.system.bit
% 正在拷贝设备树 dhldl.dtb 到 /mnt/hdlcoder_rd
% 设置设备树为 hdlcoder_rd/devicree_dtb/devicree_dhldl
% 为参考设计启动：'AXI-Stream DDR内存访问 : 3-AXIM'

系统显示 FPGA 位流编程已完成。
### 正在将权重加载到 FC 处理器。
### FC 权重已加载。当前时间为 2020-06-28 12:24:21

