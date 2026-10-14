
不同方式。对于基础层，该方案将 VCL（视频编码层）NALU（网络抽象层单元）加密为 SEI（补充增强信息）NALU 或 PACSI（负载内容可扩展性信息）NALU。对于增强层，该方案用 PACSI NALU 的加密替换可扩展扩展 NALU 中的编码切片。因此，所提出的加密方案保留了 SVC 可扩展性和格式合规性。它生成的加密码流具有原始的 SVC 结构，且对任何标准解码器都没有仿真标记或非法码字。分析和实验表明，当前算法具有成本效益，并且能够抵御选择明文攻击。

## 7.3.1.1 NALU 结构

SVC 码流被划分为 NALU。每个 NALU 都有一个头，包括一个禁止零位（F）、一个 3 位字段表示 NALU 的重要性（NRI）和一个 NUT。如图 7.10 所示，NALU 可分为 Non-VCL NALU 和 VCL NALU。Non-VCL NALU 具有用于

| NALU 类型 | 描述 | SVC 类别 |
|---|---|---|
| 0 | 未指定 | Non-VCL |
| 1 | 非 IDR 图像的编码切片 | VCL |
| 2-4 | 编码切片数据分区 A、B、C | VCL |
| 5 | IDR 图像的编码切片 | VCL |
| 6 | 补充增强信息 | Non-VCL |
| 7 | 序列参数集 | Non-VCL |
| 8 | 图像参数集 | Non-VCL |
| 9 | 访问单元定界符 | Non-VCL |
| 10 | 序列结束 | Non-VCL |
| 11 | 流结束 | Non-VCL |
| 12 | 填充数据 | Non-VCL |
| 13 | 序列参数集扩展 | Non-VCL |
| 14 | 前缀 NALU | Non-VCL |
| 15 | 子集序列参数集 | Non-VCL |
| 16-18 | 保留 | Non-VCL |
| 19 | 辅助编码图像的编码切片 | Non-VCL |
| 20 | 可扩展扩展中的编码切片 | VCL |
| 21-23 | 保留 | Non-VCL |
| 24-27 | STAP-A、STAP-B、STAP-16、STAP-24 聚合 | Non-VCL |
| 28, 29 | FU-A、FU-B 分片单元 | Non-VCL |
| 30 | PACSI：负载内容可扩展性信息 | Non-VCL |
| 31 | 子类型=0 空；子类型=1 NI-MTAP | Non-VCL |

图 7.10 可扩展视频编码的 NALU 类型。

解码（例如前缀 NALU 中的 SVC 头）或便于某些系统操作（例如补充增强信息 [SEI]），而 VCL NALU 具有用于压缩视觉数据的负载字段。VCL NALU 有两种结构。一种本身具有 SVC 头，另一种必须与前缀 Non-VCL NALU 配对，其辅助负载为 SVC 头。SVC 头包括 PRID（优先级 id）、DID（依赖 id）、QID（质量 id）、TID（时间 id）分别表示三个可扩展性维度，从而决定 NALU 的层级。通过以不同方式对 NALU 按 PRID、DID、QID 和 TID 排序，SVC 码流可以具有同一视觉内容的不同表示。我们关注类型为 6、14、30 的 Non-VCL NALU 以及类型为 1、5、20 的 VCL NALU。用 NALU_i^(n) 表示码流中第 i^th 个 NALU，其类型为 n。如果 NALU 位置不重要，可省略下标。

SVC 码流的 VCL NALU 被划分为一个基础层和若干增强层。对于基础层，非 VCL NALU_i^(14) 用于携带每个后续 VCL NALU_{i+1}^(1) 或 NALU_{i+1}^5 的 SVC 头信息，如图 7.11a 所示。也就是说，一对 (NALU_i^(14), NALU_{i+1}^(1)) 或 (NALU_i^(14), NALU_{i+1}^(5)) 一起使用以表示基础层的视觉内容。

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_214_0.png)

图 7.11 基础层 (a)、增强层 (b) 和 PACSI NALU (c) 的结构。

对于增强层，如图 7.11b 所示的编码切片 NALU^(20) 用于表示视觉内容。图 7.11c 所示的 PACSI NALU^(30) 由 NALU 头、SVC NALU 头、若干标志和 SEI NALU 组成。PACSI NALU 可包含一个或多个 SEI NALU。NALU^(30) 可在单个 NALU 包或聚合包中传输。如果 PACSI NALU^(30) 在单个包中传输，其 SVC 头与非 PACSI NALU_i+1 相同。但如果 PACSI NALU_i^(30) 与其他 NALU 在聚合包中传输，则它必须是聚合包中的第一个 NALU，且其 SVC NALU 头与聚合包中剩余的 NALU 相关。注意 NALU^(30) 必须不被分片为多个包。同时，标志可以决定字段 “TL0PICIDX”、“IDRPICID” 和 “DONC” 是否存在。

## 7.3.1.2 可扩展且格式合规的加密

为了确保格式合规性和安全性，所提出的方案通过调整 NALU 头信息并根据 NALU 类型加密 NALU 视觉数据来创建加密 NALU。

### 7.3.1.2.1 基础层中的“根”VCL NALU

“根”VCL NALU 属于基础层，且其前缀 NALU^(14) 的 TID 为零。由于它用作所有其他增强层的参考层，“根”VCL NALU 必须被加密以提供基本保护。为加密“根”NALU，我们创建一个新的 SEI NALU^(6)，其负载类型为 5（用户数据未注册消息），并用新的 NALU^(6) 替换“根”NALU。原始 VCL NALU 的视觉采样数据的加密作为 SEI NALU^(6) 的负载。

### 7.3.1.2.2 基础层中时域增强层的 NALU

对于基础层中跟随 TID = 0 的前缀 NALU^(14) 的时域增强层 NALU^(1) 或 NALU^(5)，按如下方式构造新的 NALU。新的 PACSI NALU^(30) 包括：
- 与原始前缀 NALU^(14) 相同的 NALU 头。
- 与原始前缀 NALU^(14) 相同的 SVC 头。
- NALU 类型为 6，其负载类型为 5（即用户数据未注册消息）。
- 负载为原始 NALU 的视觉数据的加密。

### 7.3.1.2.3 质量和空间增强层的 NALU

对于 DID = 0 或 QID = 0 的空间（或质量）增强层的 NALU^(20)，创建两个 NALU。新的 PACSI NALU^(30) 包括：
- 与原始 NALU^(20) 相同的 NALU 头。
- 与原始 NALU^(20) 相同的 SVC 头。
- NALU 类型为 6，其负载类型为 5（即用户数据未注册消息）。
- 负载为原始 NALU 的视觉数据的加密。
- 前缀 NALU^(14) 由原始 NALU^(20) 的 SVC 头组成。

### 7.3.1.2.4 现有的 PACSI NALU

根据 SVC 规范，未受保护的 SVC 码流可能具有 PACSI NALU^(30)。对于这些 PACSI NALU 中的任何一个，都以如下方式构造新的 PACSI NALU^(30)，原始 NALU^(30) 是新 NALU^(30) 的负载。

### 7.3.1.2.5 负载加密

使用在安全套接层（SSL, http://www.openssl.org）协议下传输的密钥，采用 RC4 等流密码配合初始化向量（IV）进行加密，其中 IV 应对每个消息唯一，使得即使对应明文相同，密文也不会重复。这确保了加密方案对选择明文攻击（CPA）的安全。在加密方案中，IV 生成为，

IV = F(H_n, H_s) (7.3)

其中 F 是 SHA1 等单向函数，H_n 表示不同可扩展性层中的 SVC NALU 头，如 DID、QID 和 TID，H_s 表示同一可扩展性层中每个 VCL NALU 的切片头。由于所提出的方案仅加密视觉采样数据，而头信息以明文形式存在，因此 IV 可在解码器/解密器端从受保护的码流中推导出来。在实验中，SVC 码流由使用 JSVM 9.19 实现的生成器产生并存储在流媒体服务器 Live555 中，而开放 SVC 解码器用作客户端。服务器和客户端均运行在 PC（2.53 GHz Intel 双核处理器）上。测试视频序列包括 football（249 帧）、soccer（299 帧）、bus（149 帧）、mobile（299 帧）和 foreman（299 帧），其中 B/E 表示基础层 B 和增强层 E。每个 GOP1 包含 16 帧，两帧 I 帧之间相隔 30 帧。此外，基础层的 QP 为 32，空间和质量（CGS/MGS）增强层的 QP 分别为 30 和 24。
