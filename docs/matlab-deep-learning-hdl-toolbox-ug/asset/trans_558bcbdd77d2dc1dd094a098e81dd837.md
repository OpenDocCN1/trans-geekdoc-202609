

# 使用部署到 FPGA 的 DAG 网络进行图像分类

| ID | 名称 | 类型 | 描述 |
| :--- | :--- | :--- | :--- |
| 48 | res4b_branch2b | 卷积 | 带步长的 256 3x3x256 卷积 |
| 49 | bn4b branch2b | 批归一化 | 256 通道的批归一化 |
| 50 | res4b* | 加法 | 2 个输入的逐元素相加 |
| 51 | res4a relu | ReLU | ReLU |
| 52 | res5a branch2a | 卷积 | 带步长的 512 3x3x256 卷积 |
| 53 | bn5a branch2a | 批归一化 | 512 通道的批归一化 |
| 54 | res5a branch2a_relu | ReLU | ReLU |
| 55 | res5a branch2b | 卷积 | 带步长的 512 3x3x256 卷积 |
| 56 | bn5a branch2b | 批归一化 | 512 通道的批归一化 |
| 57 | res5a* | 加法 | 2 个输入的逐元素相加 |
| 58 | res5a relu | ReLU | ReLU |
| 59 | res5a branch1 | 卷积 | 带步长的 512 1x1x256 卷积 |
| 60 | bn5a branch1 | 批归一化 | 512 通道的批归一化 |
| 61 | res5b branch2a | 卷积 | 带步长的 512 3x3x256 卷积 |
| 62 | bn5b branch2a | 批归一化 | 512 通道的批归一化 |
| 63 | res5b branch2a_relu | ReLU | ReLU |
| 64 | res5b branch2b | 卷积 | 带步长的 512 3x3x256 卷积 |
| 65 | bn5b branch2b | 批归一化 | 512 通道的批归一化 |
| 66 | res5b* | 加法 | 2 个输入的逐元素相加 |
| 67 | res5b relu | ReLU | 全局平均池化 |
| 68 | pool5* | 全连接 | 5 连接层 |
| 69 | new_fc | Softmax | softmax |
| 70 | prob* | | |
| 71 | new_classout | 分类输出 | 与 'MathWorks' Cap 的交叉熵 |

```
### Optimizing series network: fused 'resnet.cnn.layer.BatchNormalizationLayer into 'resnet.cnn..
Skipping data:
Compiling leg: conv1->pool1 ... complete.
Compiling leg: conv1->pool1 ... complete.
Compiling leg: res2a branch2a->res2a branch2b...
Compiling leg: res2a branch2a->res2a branch2b ... complete.
Compiling leg: res2b branch2a->res2b branch2b...
Compiling leg: res2b branch2a->res2b branch2b ... complete.
Compiling leg: res3a branch1 ... complete.
Compiling leg: res3a branch1 ... complete.
Compiling leg: res3a branch2a->res3a branch2b...
Compiling leg: res3a branch2a->res3a branch2b ... complete.
Compiling leg: res3b branch2a->res3b branch2b...
Compiling leg: res3b branch2a->res3b branch2b ... complete.
Compiling leg: res4a branch1 ... complete.
Compiling leg: res4a branch1 ... complete.
Compiling leg: res4a branch2a->res4a branch2b...
Compiling leg: res4a branch2a->res4a branch2b ... complete.
Compiling leg: res4b branch2a->res4b branch2b...
Compiling leg: res4b branch2a->res4b branch2b ... complete.
Compiling leg: res5a branch1 ... complete.
Compiling leg: res5a branch1 ... complete.
Compiling leg: res5a branch2a->res5a branch2b...
Compiling leg: res5a branch2a->res5a branch2b ... complete.
Compiling leg: res5b branch2a->res5b branch2b...
Compiling leg: res5b branch2a->res5b branch2b ... complete.
Compiling leg: pool5 ... complete.
Compiling leg: pool5 ... complete.
Compiling leg: new_fc ... complete.
Compiling leg: new_fc ... complete.
Skipping: prob
```

10-143

# 10 个特色示例

Skipping: new_classout
Creating Schedule...
. . . . .

Creating Schedule..complete.
Creating Status Table...
. . . .

Creating Status Table..complete.
Emitting Schedule...
. . . . .

Emitting Schedule..complete.
Emitting Status Table...
. . . .

Emitting Status Table..complete.

### 分配外部内存缓冲区：

| 偏移量名称 | 偏移地址 | 分配空间 |
| :--- | :--- | :--- |
| "InputDataOffset" | "0x00000000" | "12.0 MB" |
| "OutputResultOffset" | "0x00c00000" | "4.0 MB" |
| "SchedulerDataOffset" | "0x01000000" | "4.0 MB" |
| "SystemBufferOffset" | "0x01400000" | "28.0 MB" |
| "InstructionDataOffset" | "0x02800000" | "4.0 MB" |
| "ConvWeightDataOffset" | "0x03400000" | "52.0 MB" |
| "FCWeightDataOffset" | "0x06800000" | "4.0 MB" |
| "EndOffset" | "0x06c00000" | "Total: 108.0 MB" |

### 网络编译完成。

```
dn = struct fields:
	weights: [1x struct]
	instructions: [1x struct]
	registers: [1x struct]
	nSyncInstructions: [1x struct];
```

# 将比特流程序到 FPGA 并下载网络权重

