
FOMO 是一种创新的目标检测机器学习模型，其消耗的能量和内存比 `Mobilenet SSD` 和 `YOLOv5` 等传统模型少多 30 倍。FOMO 可以在内存小于 200 KB 的微控制器上运行。这种可能的主要原因是：其他模型通过在物体周围画正方形（边界框）来计算物体的大小，而 FOMO 忽略了图像的大小，仅通过其质心坐标提供物体在图像中位置的信息。

## FOMO 如何工作？

FOMO 接收灰度图像并使用 8 倍因子将其划分为像素块。对于 96×96 的输入，网格将是 12×12 (96/8=12)。接下来，FOMO 将通过每个像素块运行分类器，计算每个块中存在框或轮子的概率，随后确定包含物体概率最高的区域（如果像素块没有物体，将被归类为 `background`）。通过最终区域的重叠，FOMO 提供该区域质心的坐标（与图像尺寸相关）。

![](img/file710.png)

对于训练，我们需要选择一个预训练模型。让我们使用 `FOMO (Faster Objects, More Objects) MobileNetV2`。该模型使用大约 250 KB 的 RAM 和 80 KB 的 ROM (Flash)，非常适合我们的开发板。

- 训练轮数（Epochs）：60
- 批量大小（Batch size）：32
- 学习率（Learning Rate）：0.001

在训练期间，我们将应用数据增强（Data Augmentation），它会随机翻转、改变图像大小和亮度并裁剪，人为增加样本量。

## 使用“实时分类”测试模型

一旦模型训练完成，我们可以使用“Live Classification”工具进行测试。在相应部分，点击连接开发板（一个微型控制器）并用手机扫描二维码。

![](img/file713.png)

连接后，你可以使用手机捕捉真实图像供 Edge Impulse Studio 上的模型进行测试。

![](img/file714.png)

需要注意的是，模型可能会产生假阳性和假阴性。通过定义合理的 `Confidence Threshold`（置信度阈值，使用三点菜单设置）可以减少这种情况。尝试 0.8 或更高。

## 部署模型 (Deploying the Model - Arduino IDE)

选择 Arduino 库和量化 (int8) 模型，在 Deploy 标签上启用 EON 编译器，然后点击 `Build`（编译）。

![](img/file715.png)

打开 Arduino IDE，在 Sketch（项目）下选择 Include Library（包含库）> Add ZIP Library（添加 ZIP 库）。选择从 Edge Impulse Studio 下载的文件，就搞定了！

![](img/file716.png)

在 Arduino IDE 的 Examples（示例）选项卡下，你应该可以在项目名称下找到一个示例代码 (`esp32 > esp32_camera`）。

![](img/file717.png)

你需要修改第 32 到 75 行（定义了相机型号和引脚），使用与我们的模型相关的数据。复制并粘贴以下代码替换第 32-75 行：

```

```

将代码上传到你的 XIAO ESP32S3 Sense，你就可以开始检测水果和昆虫了。你可以在串口监视器（Serial Monitor）上查看结果。

### 背景

![](img/file719.png)

### 水果

![](img/file720.png)

### 缺陷 (Bugs)

![](img/file721.png)

请注意，模型延迟为 143 ms，每秒帧率约为 7 fps（与我们在图像分类项目中获得的结果相似）。这是因为 FOMO 是巧妙地构建在 CNN 模型之上的，而不是像 SSD MobileNet 那样使用目标检测模型。例如，在树莓派 4 上运行 MobileNetV2 SSD FPN-Lite 320 × 320 模型时，延迟会高出约五倍（约为 1.5 fps）。

## 部署模型 (SenseCraft-Web-Toolkit)

正如“图像分类”章节中所讨论的，在 Arduino IDE 上使用图像模型对推理进行验证是非常具有挑战性的，因为我们无法看到摄像头的对焦情况。再次，让我们使用 `SenseCraft-Web Toolkit`。

按照以下步骤启动 SenseCraft-Web-Toolkit：

1. 打开 [SenseCraft-Web-Toolkit 网站。](https://seeed-studio.github.io/SenseCraft-Web-Toolkit/#/setup/process)
2. 将 XIAO 连接到你的电脑：

- 连接好 XIAO 后，如下所示选择它：

![](img/file722.jpg)

- 选择设备/端口并按下 `[Connect]`（连接）：

![](img/file723.jpg)

> 你可以尝试 Seeed Studio 之前上传的几个计算机视觉模型。尝试它们并享受其中吧！

在我们的案例中，我们将使用页面底部的蓝色按钮：`[Upload Custom AI Model]`（上传自定义 AI 模型）。

首先，我们必须从 Edge Impulse Studio 下载我们的 `quantized .tflite` 量化模型。

3. 进入 Edge Impulse Studio 中的你的项目，或克隆此项目：

- [XIAO-ESP32S3-CAM-Fruits-vs-Veggies-v1-ESP-NN](https://studio.edgeimpulse.com/public/228516/live)

4. 在 `Dashboard`（仪表板）上，下载模型（块输出”）：`Object Detection model - TensorFlow Lite (int8 quantized)`

![](img/file724.jpg)

5. 在 SenseCraft-Web-Toolkit 上，使用页面底部的蓝色按钮：`[Upload Custom AI Model]`。将弹出一个窗口。输入从 Edge Impulse Studio 下载到电脑的模型文件，选择一个模型名称，并带有标签（ID: 对象）进行输入：

![](img/file725.jpg)

> 注意，你应该使用在 EI Studio 上训练的标签，并按字母顺序输入它们（在我们的案例中，为 background, bug, fruit）。

几秒钟（或几分钟）后，模型将上传到你的设备，摄像头图像将实时显示在预览区域（Preview Sector）：

![](img/file726.jpg)

被检测的物体将被标记（质心）。你可以选择推理光标的置信度 `Confidence` 和 `IoU`（交并比），IoU 用于评估预测边界框与真实边界框相比的准确性。

点击顶部的按钮（Device Log 设备日志），你可以打开串口监视器来跟踪推理过程，就像我们在 Arduino IDE 中做的那样。

![](img/file727.png)

在设备日志上，你将获得如下信息：

- 预处理时间（图像捕获和裁剪）：3 ms，
- 推理时间（模型延迟）：115 ms，
- 后处理时间（图像显示和物体标记）：1 ms。
- 输出张量（框），例如其中一个框：`[[30,150, 20, 20,97, 2]]`；其中 30,150, 20, 20 是框的坐标（位于质心附近）；97 是推理结果，2 是类别（在此例中为 2: fruit 水果）。

> 注意在上面的示例中，我们得到了 5 个框，因为没有一个水果都获得 3 个质心。一种解决方案是后处理，我们可以将接近的质心聚合为了一个。

这里是其他截图：

![](img/file728.jpg)

## 总结

FOMO 是图像处理领域的一次重大飞跃，正如 Louis Moreau 和 Mat Kelcey 在 2022 年发布时所说：

> FOMO 是一项突破性的算法，它首次为微控制器带来了实时目标检测、跟踪和计数功能。

在嵌入式设备上探索目标检测（更准确地说是计数）存在多种可能性。

## 资源

- [Edge Impulse 项目](https://studio.edgeimpulse.com/public/315759/latest)

# 关键词识别 (KWS)

![DALL·E prompt - 1950s style cartoon illustration based on a real image by Marcelo Rovai](img/file729.png)

*DALL·E prompt - 基于 Marcelo Rovai 真实图像的 1950 年风格卡通插图*

## 概览

关键词识别（KWS）是许多语音助手的核心，使设备能够对特定的词或短语做出反应。虽然这项技术支撑了 Google Assistant 或 Amazon Alexa 等流行设备，但它同样适用于更低功耗设备。本实验室将指导你如何在 XIAO ESP32S3 上使用 TinyML 实现 KWS 系统。

XIAO ESP32S3 配备了乐鑫的 ESP32-S3，具有双核 LX7 处理器、集成 Wi-Fi 和蓝牙，其计算能力、能效和多功能连接使其成为 TinyML 应用的极佳平台。我们将使用 [Edge Impulse Studio](https://www.edgeimpulse.com/)，这是一个强大的用户友好平台，简化了在边缘设备上创建和部署机器学习模型。

利用我们在 TensorFlow Lite for Microcontrollers（EI Studio 的底层）方面的经验，我们将在 XIAO ESP32S3 上一步步训练一个能够识别 YES 模型。随着实验室的进行，我们将拆解每个阶段——从数据采集和准备到模型训练和部署——以提供全面的理解。

**学习目标**

- **理解语音助手架构**，包括级联检测系统以及关键词识别作为语音处理的第一阶段。
- **掌握音频数据采集技术**，使用离线方法（带有 SD 卡的 XIAO ESP32S3 麦风）和在线方法（手机集成集成）。
- **实现音频数字信号处理**，包括 I2S 协议基础、16kHz/16bit 音频采样，以及通过 MFCC 将时域音频信号转换为频域。
- **训练音频分类卷积神经网络**，使用迁移学习技术、数据增强策略和针对四分类 (YES, NO, NOISE, UNKNOWN) 的模型优化。
- **在微控制器上部署优化模型**，通过量化 (INT8)、PSRAM 内存管理和嵌入式系统的实时推理优化。
- **开发完整的后处理流水线**，包括置信度阈值、外部设备的 GPIO 控制、OLED 显示集成以及创建独立的 AI 传感器系统。
- **比较开发工作流**，对比无代码平台（Edge Impulse Studio）与传统的嵌入式编程（Arduino IDE）。

## KWS 项目

### 语音助手是如何工作的？

关键词识别（KWS）对于许多语音助手至关重要，使设备能够对特定的词或短语做出反应。首先，必须意识到市场上的语音助手（如 Google Home 或 Amazon Echo-Dot）只有在被特定关键词“唤醒”时（第一个是“Hey Google”，第二个是“Alexa”）才会对人类做出。

换句话说，识别语音命令基于多阶段模型或级联检测。

![](img/file730.png)

![](img/file731.png)

# 第一阶段

Echo Dot 或 Google Home 内部有一个较小的微处理器，它会持续监听声音，等待关键词的出现。对于这种检测，使用了边缘侧的 `TinyML` 模型（KWS 关键词检测应用）。

# 第二阶段

只有当被第 1 阶段的 KWS 应用触发时，数据才会被发送到云端，并在更更大的模型上进行处理。

下方的视频展示了一个示例，我在树莓派上模拟了一个 Google Assistant（第 2 阶段），并使用 `Arduino Nano 33 BLE` 作为 `tinyML` 设备（第 1 阶段）。

[`www.youtube.com/embed/e\_OPgcnsyvM`](https://www.youtube.com/embed/e_OPgcnsyvM)

> 如果你想更深入了解整个项目，请查看我的教程：[从零开始构建智能语音助手](https://www.hackster.io/mjrobot/building-an-intelligent-voice-assistant-from-scratch-2199c3)。

在实验中，我们将关注第 1 阶段（KWS 或关键词检测），我们将使用 `XIAO ESP2S3 Sense`，它带有一个数字麦克风用于识别关键词。

## 推理流水线

下方的图表展示了最终的 KWS 应用应该的工作原理（在推理期间）：

![](img/file732.png)

我们的 KWS 应用将识别四类声音：

- `YES`（关键词 1）
- `NO`（关键词 2）
- `NOISE`（没有说关键词，只有背景噪声）
- `UNKNOWN`（除 YES 和 NO 以外的不同词汇混合）

> 在实际项目中，始终建议包含与关键词不同的词汇，例如“Noise”（噪声，或背景）和“Unknown”（未知）。

## 机器学习工作流

KWS 应用的核心组件是它的模型。因此，我们必须使用特定的关键词、噪声和其他词汇（“未知”词）来训练这样一个模型：

![](img/file733.png)

## 数据集

机器学习工作流中的关键组件是`数据集`。一旦我们决定了特定的关键词（`YES` 和 `NO`），就可以利用 Pete Warden 开发的数据集——[语音命令：用于有限词汇语音识别的数据集](https://arxiv.org/pdf/1804.03209.pdf)。该数据集包含 35 个关键词（每个有 +1,000 个样本），例如 yes、no、stop 和 go。换句话说，我们可以获得 1,500 个 `yes` 和 `no` 样本。

你可以从 Edge Studio 下载数据集的一部分（[关键词检测预构建数据集](https://docs.edgeimpulse.com/docs/pre-built-datasets/keyword-spotting)），其中包含了我们在项目中将使用的四个类别的样本：yes、no、noise 和 background。请按照以下步骤操作：

- 下载[keywords 数据集。](https://cdn.edgeimpulse.com/datasets/keywords2.zip)
- 在你选择的位置解压该文件。

虽然我们从 Pete 的数据集中有很多大量数据，但建议也收集一些我们自己说的话语。在处理加速度计时，创建一个由同一传感器捕获的数据集是关重要的。在 `sound`（声音）的情况下，分类有所不同，因为实际上它涉及到 `audio`（音频）。

声音（sound）和音频（audio）的主要区别在于它们的能量形式。声音是机械波（纵声波），通过介质传播。音频是由代表声音的电能（模拟或数字信号）组成的。

当我们说关键词时，应该将声音转换为音频。这种转换应该通过对麦克风生成的信号进行采样完成，采样频率为 16 kHz，深度为 16-bit。因此，任何可以生成此基本规格（16 kHz/16 bits）音频的设备都可以正常工作。作为设备，我们可以使用合适的 `XIAO ESP32S`、电脑，甚至是你的手机。

![](img/file734.png)

### 使用 Edge Impulse 和智能手机捕获在线数据

在“运动与异常检测”实验中，我们将设备直接连接到 Edge Impulse 进行数据采集（采样频率为 50 Hz 到 100 Hz）。对于如此低的频率，我们可以使用 CLI，但根据 Edge Impulse 的 Jan Jong 的说法，`16 kHz` 对于数据传输器来说太快了。因此，一旦通过麦克风捕获了数字数据，我们将其转换为 `WAV` 文件，通过 Uploader 发送到 Studio。

> 如果我们想直接在 Studio 上收集音频数据，可以使用任何连接到它的智能手机。我们在这里不探索此选项，但你可以轻松参考[文档](https://docs.edgeimpulse.com/docs/development-platforms/using-mobile-phone)。

### 使用 XIAO ESP32S 捕获（离线）音频数据

内置麦克风是`[MSM261D352HCPM`](https://files.seeedstudio.com/...)。在 XIAO ESP32S 情况下，使用 PDM 麦克风![](img/file735.png)通过 I2S 接口连接在 `IO41`。

#### 什么是 I2S？

I2S，即同步时分接口，是一种在设备之间传输数字音频的协议。它最初由 Philips 开发，现在用于数字音频处理器，以及微控制器。

I2S 协议至少包含三根线：![](img/file736.png)

1. 位时钟（Bit clock）：I2S 的时钟线（`BCLK`）。
2. 字选择线（Word select）：指示 I2S 字帧开始（`WS`）。
3. 数据线（Data）：I2S 的数据线（`SD`）。

在 I2S 数据流中，数据以帧的形式传输。对于单声道，每帧包含一个数据位；对于立体，每帧包含两个数据位（左右声道）。

让我们开始理解如何使用麦克风捕获原始数据。

```cpp
// 此处为代码实现示例，保持不翻译
```

- `int sample = I2S.read()`: 这从 I2S 接口读取一个音频采样。

如果采样有效，它将打印在串口监器（Serial Monitor）和绘图器（Plotter）上。

以下是两种音调的“低语”测试。

![](img/file737.png)

## 保存录制的音频样本

让我们使用内置的 SD 卡读取器来保存 `.wav` 音频文件；我们必须先启用 `XIAO PSRAM`。

> ESP32-S3 的 MCU 芯片上只有几百 KB 的内部 RAM。对于某些用途来说这可能不够，因此 ESP32-S3 可以使用与 SPI flash 芯片并行连接的、达 16 MB 外部 PSRAM（伪静态内存）。外部内存被包含在内存映射中，在某些限制下，可以像内部数据 RAM 一样使用。
