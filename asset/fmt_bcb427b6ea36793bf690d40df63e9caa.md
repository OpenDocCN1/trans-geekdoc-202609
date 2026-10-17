
结果，我们将收到一个分数和一个类别作为输出。

![](img/file830.png)

例如，`[99, 1]` 意味着类别：1（人员），分数为 0.99。一旦此模型变为二分类，类别 0 将是“无人员”。推理延迟为 `15ms` 或约 70fps。

### 功耗

为了运行 `Mobilenet V2 0.35`，`Grove Vision AI V2` 在 `5.24V` 下的峰值电流为 `80mA`，导致功耗为 `420mW`。

在 `XIAO ESP2S3 Sense` 上运行相同的模型，功耗为 `523mW`，延迟为 `291ms`。

![](img/file831.png)

## 在 SenseCraft AI 上探索其他模型

多个公共 AI 模型也可以从 [SenseCraft 网页](https://sensecraft.seeed.cc/ai/model) 下载。例如，你可以运行 `Swift-YOLO` 模型，如所示[检测交通灯](https://sensecraft.seeed.cc/ai/view-model/60281-traffic-light-detection?tab=public)：

![](img/file832.png)

该模型的延迟约为 `86 ms`，平均功耗为 `420 mW`。

## 图像分类项目

让我们使用 SenseCraft AI Studio 创建一个完整的图像分类项目。

![](img/file833.png)

在 SenseCraft AI 上：让我们打开 [Training](https://sensecraft.seeed.cc/ai/training) 标签页：

![](img/file834.png)

默认使用 `WebCam` 训练 `Classification` 模型。让我们改为选择 `Grove Vision AI V2`。按下绿色按钮 `[Connect]`，将弹出一个窗口。选择相应的端口并按蓝色按钮 `[Connect]`。

![](img/file835.png)

来自 `Grove Vision AI V2` 的视频流将显示。

### 目标

第一步始终是定义目标。例如，让我们对两个简单物体进行分类——比如一个玩具 `box` 和一个玩具轮子 `wheel`。我们还应该包含第三类图像，即 `background`，即场景中没有任何物体。

![](img/file836.png)

## 数据收集

让我们按照字母顺序创建这些类别：

* 类别 1：`background`
* 类别 2：`box`
* 类别 3：`wheel`

![](img/file837.png)

选择一个类别并持续点击预览区域下方的绿色按钮。收集的图像将出现在图像样本屏幕上。

![](img/file838.png)

收集图像后，检查它们并删除任何错误的图像。

![](img/file839.png)

每个类别收集大约 50 张图像，然后进入训练步骤：

## 训练

确认已选择正确的设备（`Grove Vision AI V2`）并点击 `[Start Training]`。

![](img/file840.png)

## 测试

训练完成后，可以预览推理结果。

> 注意，模型并未运行在设备上。事实上，我们只是在使用设备捕捉图像，并使用运行在 Studio 中的训练模型进行实时预览。

![](img/file841.png)

现在是时候将模型真正部署到设备上了：

## 部署

在 `[Deploy to device]` 上选择训练好的模型，选择 Grove Vision AI V2：

![](img/file842.png)

Studio 将我们重定向到 `Vision Workplace` 标签页。确认部署，选择合适的端口并连接：

![](img/file843.png)

模型将刷入设备。在自动重置后，模型将在设备上开始运行。在设备日志上，我们可以看到推理的 `latency 约为 8 ms`，对应于 `每秒 125 帧 (FPS)`。

此外，请注意可以调整模型的置信度。

![](img/file844.png)

> 运行图像分类模型时，Grove Vision AI V2 在 5.24V 下的峰值电流为 80mA，导致 `功耗为 420mW`。

## 保存模型

可以在 SenseCraft AI Studio 中保存模型。Studio 将保留我们所有的模型，以便稍后部署。为此，返回 `Training` 标签页并选择按钮 `[Save to SenseCraft]`：

![](img/file845.png)

## 总结

在本次实验中，我们利用 [Seeed Studio Grove Vision AI Module V2](https://wiki.seeedstudio.com/grove_vision_ai_v2/) 探索了多种计算机视觉 (CV) 应用，展示了其作为专为嵌入式机器学习应用设计的强大且紧凑的设备的卓越能力。

**卓越性能**：Grove Vision AI V2 在多个计算机视觉任务中表现出了惊人的性能。凭借其 `Himax WiseEye2 chip`（具有 `双核 Arm Cortex-M55` 和集成的 `ARM Ethos-U55 神经网络单元`），该设备实现了：

* **图像分类**：`15 ms` 推理时间 (67 FPS)
* **物体检测（人员）**：`48 ms 到 76 ms` 推理时间 (21 FPS 到 13 FPS)
* **姿态检测**：`121 ms` 实时关键点检测，支持 17 关节跟踪 (8 FPS)

**能效领先**：Grove Vision AI V2 最具吸引力的优势之一是其卓越的能效。对比测试显示，它比传统的嵌入式平台有显著改进：

* **Grove Vision AI V2**：80 mA (`410 mW`) 峰值功耗 (60+ FPS)
* **XIAO ESP32S3**：执行类似的 CV 任务（图像分类）消耗 `523 mW` (3+ FPS)

**实际实现**：通过涵盖数据集创建、模型训练、部署和离线推理的完整端到端项目，证明了该设备的通用性。

**开发者友好生态系统**：SenseCraft AI Studio 具有无代码部署和自定义应用程序集成功能，使得初学者和高级开发者都能轻松上手。广泛的预训练模型库以及对自定义模型部署的支持为多样化应用提供了灵活性。

Grove Vision AI V2 代表了边缘 AI 硬件的重要进步，在紧凑、高效的封装内提供了专业级的计算机视觉能力，使工业、物联网和教育领域嵌入式应用的 AI 部署变得大众化。

**核心要点**

本实验表明，复杂的计算机视觉应用并不限于云端解决方案或像树莓派或 Jetson Nano 那样的高功耗硬件——它们现在可以以极高的效率和性能有效地部署在边缘。

可选，我们可以使用 [XIAO Vision AI Camera](https://www.seeedstudio.com/XIAO-Vision-AI-Camera-p-6450.html)。这种创新的视觉解决方案无缝结合了 Grove Vision AI V2 模块、`XIAO ESP32-C3` 控制器和 `OV5647 camera`，全部封装在自定义的 3D 打印壳壳：

![](img/file846.png)

## 资源

[SenseCraft AI Studio Instructions](https://wiki.seeedstudio.com/sensecraft_ai_pretrained_models_for_grove_visionai_v2/)。

[SenseCraft-Web-Toolkit 网站。](https://www.seeedstudio.com/)。

# 使用 SenseCraft AI Studio 收集数据

在 SenseCraft AI Studio 上：打开 [Training](https://sensecraft.seeed.cc/ai/training) 标签页。

默认情况下，如果可用 `WebCam`，将训练一个 `Classification`（分类）模型。让我们改选择 `Grove Vision AI V2`。点击绿色按钮 `[Connect]` (1)，将弹出一个窗口。选择相应的端口 (2) 并点击蓝色按钮 `[Connect]` (3)。

![](img/file851.png)

将显示从 `Grove Vision AI V2` 传输的图像。

## 图像采集

让我们创建类别，例如，按照字母顺序顺序：

* 类 1: background（背景）
* 类 2: periquito（小鹦鹉）
* 类 3: robot（机器人）

![](img/file852.png)

选择一个类别（注意窗口周围会出现一条绿线），并持续点击预览区域下方的绿色按钮。收集到的图像将出现在图像样本（Image Samples）屏幕上。

![](img/file853.png)

收集完图像后，对它们进行检查，如有必要，删除任何错误的图像。

![](img/file854.png)

每个类别收集大约 50 张图像。在收集完三个类别后，打开每个类别的菜单并选择 `Export Data`（导出数据）。

![](img/file855.png)

在计算机的下载区域，我们将获得三个 zip 文件，每个文件对应一个类名称。每个 Zip 文件都包含一个带有图像的文件夹。

## 将数据集上传到 Edge Impulse Studio

我们将使用 `Edge Impulse Studio` 来训练我们的模型。[Edge Impulse](https://www.edgeimpulse.com/) 是一个用于边缘设备机器学习的领先开发平台。

* 在 `Edge Impulse` 中输入您的账户凭据（或创建一个免费账户）。
* 接下来，创建一个新项目：

![](img/file856.png)

> 数据集每个标签包含约 50 张图像，其中 40 张用于训练，10 张用于测试。

## 脉冲设计与预处理

### 脉冲设计 (Impulse Design)

脉冲（Impulse）接收原始数据（在本例中为图像），提取特征（调整图片大小），然后使用学习块对新数据进行分类。

图像分类是深度学习最常见的应用，但完成此任务需要大量数据。我们每个类别大约有 50 张图像。这个数量足够吗？完全不够！我们需要数千张图像来“教导”或“建模”每个类别，以便我们能够区分它们。然而，我们可以通过使用数千张图像重新训练之前训练过的模型来解决这个问题。我们将这种技术称为“迁移学习”（Transfer Learning, TL）。通过迁移学习，我们可以在我们的数据上对预训练的图像分类模型进行微调，即使对于像我们这样较小的图像数据集，也能获得良好的性能。

![](img/file857.jpg)

因此，从原始图像开始，我们将它们调整为（96x96）像素，并将其输入我们的迁移学习块：

![](img/file858.png)

> 为了进行比较，我们将图像大小保持为 96 x 96。但请注意，使用 `Grove Vision AI Module V2` 及其内部 2.4 MB 的 `SRAM`，可以使用更大的图像（例如 160 x 160）。同时在右上角选择目标（`Target`）设备（`Himax WiseEye2 (M55 400 MHz)`）。

### 预处理（特征生成）

除了调整图像大小外，我们还可以将其转换为灰度模式或保留其原始 RGB 深度。让我们在 `Image` 部分选择 `[RGB]`。这样做，每个数据样本的维度将为 27648 (96x96)。点击 `[Save Parameters]` 将打开一个新的标签页，`Generate Features`（生成特征）。

### 模型设计、训练与测试

图像分类是深度学习最常见的应用……（此处省略部分重复逻辑，保持翻译一致）edgeimpulse.com 2017 

在 2017 年，Google 引入了 MobileNet，而 [2018 年 MobileNetV2](https://arxiv.org/abs/1804.04715) 引入了倒置残差和线性瓶颈……（此处省略部分重复逻辑，保持翻译一致）

![](img/file863.png)

这里是其他截图：

![](img/file864.png)

该模型的功耗约为 70 mA，相当于 0.4 W。

### 图像分类（非官方）基准测试

若干开发板可用于嵌入式机器学习（tinyML），目前用于计算机视觉应用（低功耗）最常见的开发板有 `ESP32 CAM`、`Seeed XIAO ESP32S3 Sense` 以及 Arduino `Nicla Vision`。

利用这一机会，一个经过相似训练的、alpha 值为 `0.1` 的 `MobilenetV2 96x96` 模型也被部署在了 `ESP-CAM`、`XIAO` 和 `Raspberry Pi Zero W2` 上。结果如下：

![](img/file865.png)

> 带有 `ARM Ethus-U55` 的 Grove Vision AI V2 速度大约是带有 `ARM-M7` 设备的 14 倍，并且比 `Xtensa LX6` (`ESP-CAM`) 快 100 倍以上。即使与 CPU 强大强大的树莓派相比，U55 也降低了近一半的延迟。此外，其功耗低于其他设备（功耗对比请参见[此处](https://www.hackster.io/limengdu0117/2024-mcu-ai-vision-boards-performance-comparison-998505) 文章）。

### 后处理

现在模型已经上传到开发板并正常工作，对图像进行分类，让我们连接一个主设备（Master Device）将推理结果导出，并查看完全离线的运行（断开电脑连接，例如由电池供电）。

> 注意，我们可以使用任何微控制器作为主控制器，例如 `XIAO`、`Arduino` 或树莓派。

#### 获取视频流

图像处理和模型推理在 Grove Vision AI (V2) 中本地处理，我们希望结果通过 `IIC` 输出到 `XIAO`（主控制器）。为此，我们将使用 `Arduino SSMA library`。该库的主要用途是处理 Grove Vision AI 的数据流，这不涉及模型推理。

> Grove Vision AI (V2) 通过 `IIC` 与 `XIAO` 通信（推理结果）；设备的 `IIC` 地址为 `0x62`。图像信息的传输通过 USB 串口完成。

**步骤 1**：从 GitHub 下载压缩包格式 [Arduino SSMA](https://github.com/Seeed-Studio/Seeed_Arduino_SSCMA/) 库：

![](img/file866.png)

**步骤 2**：在 Arduino IDE 中安装（`sketch > Include Library > Add .Zip Library`）。

**步骤 3**：安装 `ArduinoJSON` 库。

![](img/file867.png)

**步骤 4**：安装 `Eigen` 库

![](img/file868.png)

**步骤 3**：现在，通过设备背部的插座（一排针）连接 `XIAO` 和 Grove Vision AI (V2)。

![](img/file869.jpg)

> **注意**：请注意连接方向，Grove Vision AI 的 Type-C 接口方向应与 `XIAO` 的 Type-C 接口一致。

**步骤 5**：将 `XIAO USB-C` 端口连接到电脑

![](img/file870.png)

**步骤 6**：在 Arduino IDE 中选择 `Xiao` 开发板和相应的 USB 端口。

如果我们想将视频流到网页，将使用 `XIAO ESP32S3`，它带有 wifi 和足够的内存来处理图像。选择 `XIAO_ESP32S3` 和相应的 USB 端口：

![](img/file871.png)

默认情况下，PSRAM 是禁用的。打开 `Tools` 菜单，在 PSRAM 上：选择 `"OPI PSRAM"` 选择 `OPI PSRAM`。

![](img/file872.png)

**步骤 7**：在 Arduino IDE 中打开示例：

`File` -> `Examples` -> `Seeed_Arduino_SSCMA` -> `camera_web_server`。

并在 `camera_web_server.ino` 脚本中编辑 `ssid` 和 `password` 以匹配 Wi-Fi 网络。

**步骤 8**：将脚本上传到开发板并打开串口监视器（Serial Monitor）。连接到 Wi-Fi 网络后，将显示开发板的 IP 地址。

![](img/file873.png)

使用浏览器打开该地址。将出现一个视频应用。要**仅**查看来自 Grove Vision AI V2 的视频流，按下 `[Sample Only]` 和 `[Start Stream]`。

![](img/file874.png)

如果你想创建一个图像数据集，可以使用此应用保存设备生成的视频帧。按下 `[Save Frame]`，图像将保存到桌面的下载区域。

![](img/file850.png)

在**不**选择 `[Sample Only]` 的情况下打开应用，推理结果应该出现在视频屏幕上，但对于图像分类（Image Classification）并不会发生。对于目标检测或姿态估计，结果是嵌入在视频流中的。

例如，如果模型是使用 `YoloV8` 的人体检测模型：

![](img/file875.png)

#### 获取推理结果

* `File` -> `Examples` -> `Seeed_Arduino_SSCMA` -> `inference`。
* 将脚本上传到开发板并打开串口监视器。连接到 Wi-Fi 网络后，将显示开发板的 IP 地址。
* 将摄像头对准物体，串口监视器将显示结果。

![](img/file873.png)
