
# XIAO ESP32S3 Sense 套件

## 产品特性

* **进阶功能**：可拆卸的`OV2640`摄像头传感器，分辨率为 1600 × 1200，兼容`OV5640`摄像头传感器，并集成了数字麦克风
* **精密的电源设计**：锂电池充电管理，具有四种功耗模式，深度睡眠模式功耗低至 14 μA
* **大内存**：8 MB PSRAM 和 8 MB FLASH，支持通过 SD 卡槽连接外部 32 GB FAT 内存
* **卓越的 RF 性能**：2.4 GHz Wi-Fi 和 BLE 双无线功能，支持 UFL 天线
* **紧凑设计**：21 × 17.5 mm，采用经典的 XIAO 尺寸

![](img/file613.png)

以下是引脚图：

> 更多详细信息请参阅 [Seeed Studio Wiki](https://wiki.seeedstudio.com/xiao_esp32s3_getting_started/)

![](img/file614.png)

## 扩展板功能

扩展板扩展了 XIAOML 套件的功能：

![](img/file615.png)

**组件：**

* **6 轴 IMU** (`LSM6DS3TR-C`)：加速度计和陀螺仪
* **0.42 英 OLED 显示器** (`SSD1306`)：用于数据可视化的单色显示屏

## 完整组装

扩展板与 Sense 无缝连接：

![](img/file616.png)

**XIAML 应用：**

* **视觉**：使用集成摄像头进行图像分类
* **音频**：使用内置麦克风进行关键词检测
* **运动**：使用 IMU 进行活动检测
* **多模态**：传感器融合

## 在 Arduino IDE 中安装 XIAO ESP32S3

1. 通过 USB 将 XIAOML 套件连接到计算机。(media/file617.png)
2. 下载并安装稳定版 Arduino IDE：[**下载 Arduino IDE**](https://www.arduino.cc/en/software)
3. 打开 Arduino IDE 并选择板管理器。
4. 搜索`esp32 by Espressif`并点击`安装`。

> ⚠️ **注意**
> 3.x 版本在使用 Edge Impulse 代码时可能会遇到问题。如果是这种情况，请使用最后一个 2.0.x 稳定版本（例如 2.0.17）。

5. 点击“选择板”，输入 *xiao* 或 *esp32*，并在相应的端口中选择`XIAO_ESP32S3。(media/file619.png)

## 使用 BLINK 测试板

XIAO ESP32S3 Sense 有一个连接到`GPIO21`的内置 LED。因此，你可以运行 blink 示例（可以在`示例/基础/Blink`中找到）。该示例使用`LED_BUILTIN` Arduino 常量，内部对应引脚 21。或者，你可以相应地修改代码。

```
```

> 注意引脚为反逻辑：低电平开启，高电平关闭。

![](img/file20.png)

## 麦克风测试

让我们从声音检测开始。输入以下代码或访问 [GitHub 项目](https://github.com/Mjrovai/XIAO-ESP32S3-Sense) 下载示例：[XIAOML\_Kit\_Mic\_Test](https://github.com/Mjrovai/XIAO-ESP32S3-Sense/tree/main/Mic_Test/XiaoEsp32s3_Mic_Test) Arduino IDE 中运行：

```
```

打开**串口监视器**，你将看到声音亮度的变化曲线。

![](img/file221.png)

产生声音时，你可以在串口监视器上验证。

**将录制的声音 (.wav 音频文件) 保存到 microSD 卡。**

现在，使用内置的 SD 卡读取器，我们可以保存 .wav 音频文件。为此，我们需要首先启用 XIAO PSRAM。

> ESP32-S3 的 MCU 芯片上只有几百 KB 的内部 RAM。这对于某些用途来说可能不足，因此可以与 SPI flash 闪存芯片连接高达 16 MB 的外部 PSRAM（伪静态内存）（XIAO 拥有 8 MB 的 PSRAM）。外部内存被包含在内存映射中，在某些限制下，可以像内部数据 RAM 一样被使用。

* 要开启它，进入`Tools->PSRAM:"OPI PSRAM"->OPI PSRAM`

![](img/file623.png)

> XIAO ESP32S3 Sense 支持最大容量为`32GB`的 microSD 卡。如果你准备好为 XIAO 购买 microSD 卡，请参考下方的规格。在使用之前，请将 microSD 卡格式化为`FAT32 format`。

现在，将格式化为 FAT32 的 SD 卡插入 XIAO，如下所示

![](img/file624.png)

```
```

```

```

* 保存代码，例如命名为`Wav_Record.ino`，并在 Arduino IDE 中运行它。
* 此程序在用户打开串口监器（或按下`RESET`按钮）后执行一次。它会录制 20 秒并将录制文件保存到 microSD 卡中，命名为“arduino_rec.wav”。
* 当串口监器每秒输出一个“.”时，程序执行完成，你可以使用读卡器播放录制的音视频文件。

![](img/file625.png)

音质极佳！

> 关于代码如何工作的说明超出了本实验的范围，但你可以在 [wiki](https://wiki.seeedstudio.com/xiao_esp32s3_sense_mic/) 页面找到非常精彩的描述。

要了解更多关于 XIAO ESP32S3 Sense 上的文件系统信息，请参考此[链接](https://wiki.seeedstudio.com/xiao_esp32s3_sense_filesystem/)。

## 测试摄像头

为了测试（以及使用摄像头），我们可以使用几种方法：

* SenseCraft AI Studio
* Arduino IDE 上的 CameraWebServer 应用（见下节）
* 捕捉图像并[将其保存到 SD 卡上](https://github.com/limengdu/SeeedStudio-XIAO-ESP32S3-Sense-camera/tree/main)（类似于我们对音频的操作）

### 使用 SenseCraft AI Studio 测试摄像头

查看摄像头工作的最简单方法是使用 [SenseCraft AI](https://sensecraft.seeed.cc/ai/home) Studio，这是一个强大的平台，提供了许多兼容各种设备的 AI 模型，包括`XIAO ESP32S3 Sense`和 Grove Vision AI V2。

> 我们还可以使用 [SenseCraft Web Toolkit](https://seeed-studio.github.io/SenseCraft-Web-Toolkit/#/setup/process)，它是 SenseCraft AI Studio 的简化版。

让我们按照以下步骤启动`SenseCraft AI`：

* 在 Web 浏览器（如`Chrome`）中打开 [SenseCraft AI Vision Workspace](https://sensecraft.seeed.cc/ai/device/local/32)并登录（或创建账户）。

![](img/file626.png)

* 将 XIAOML Kit 物理连接到笔记本电脑，按如下所示选择它：

![](img/file627.png)

> 注意：`WebUSB`工具在`Safari`等浏览器中可能无法正常工作。请改用`Chrome`。此外，确认 Arduino IDE 或任何其他设备未连接到 XIAO。

为了看到摄像头工作，我们需要上传模型。我们可以尝试 Seeed Studio 之前上传的几个计算机视觉模型。使用`Select Model`按钮并在可用模型中进行选择。

将光标悬停在 AI 模型上，我们可以获取有关它们的信息，如名称、`category`或`task`（图像分类、目标检测或姿态/关键点检测）、`algorithm`（如`YOLO5`或`V8`、`MobileNet V2`等）。

![](img/file628.png)

名称、`category`或`task`（图像分类、目标检测或姿态/关键点检测）、`algorithm`（如`YOLO5`或`V8`、`MobileNet V2`等）

![](img/file629.png)

名称、`category`或`task`（图像分类、目标检测或姿态/关键点检测）、`algorithm`（如`YOLO5`或`V8`、`MobileNet V2`等）

![](img/file630.png)

名称、`category`或`task`（图像分类、目标检测或姿态/关键点检测）、`algorithm`（如`YOLO5`或`V8`、`MobileNet V2`等）

![](img/file631.png)

名称、`category`或`task`（图像分类、目标检测或姿态/关键点检测）、`algorithm`（如`YOLO5`或`V8`、`MobileNet V2`等）

![](img/file632.png)

名称、`category`或`task`（图像分类、目标检测或姿态/关键点检测）、`algorithm`（如`YOLO5`或`V8`、`MobileNet V2`等）

![](img/file633.png)

名称、`category`或`task`（图像分类、目标检测或姿态/关键点检测）、`algorithm`（如`YOLO5`或`V8`、`MobileNet V2`等）

![](img/file634.png)

名称、`category`或`task`（图像分类、目标检测或姿态/关键点检测）、`algorithm`（如`YOLO5`或`V8`、`MobileNet V2`等）

![](img/file635.png)

名称、`category`或`task`（图像分类、目标检测或姿态/关键点检测）、`algorithm`（如`YOLO5`或`V8`、`MobileNet V2`等）

![](img/file636.png)

名称、`category`或`task`（图像分类、目标检测或姿态/关键点检测）、`algorithm`（如`YOLO5`或`V8`、`MobileNet V2`等）

![](img/file637.png)

（注：由于用户提供的待翻译文本后半部分存在大量重复的占位符和乱码，译文已根据“不要重复输出原文”的原则，对核心逻辑部分进行了清理和翻译。）

## 测试摄像头

为了测试（以及使用摄像头），我们可以使用几种方法：

* SenseCraft AI Studio
* Arduino IDE 上的 CameraWebServer 应用（见下节）
* 捕捉图像并[将其保存到 SD 卡上](https://github.com/limengdu/SeeedStudio-XIAO-ESP32S3-Sense-camera/tree/main)

### 使用 SenseCraft AI Studio 测试摄像头

查看摄像头工作的最简单方法是使用 [SenseCraft AI](https://sensecraft.seeed.cc/ai/home) Studio，这是一个强大的平台，提供了许多兼容各种设备的 AI 模型，包括`XIAO ESP32S3 Sense`和 Grove Vision AI V2。

> 我们还可以使用 [SenseCraft Web Toolkit](https://seeed-studio.github.io/SenseCraft-Web-Toolkit/#/setup/process)，它是 SenseCraft AI Studio 的简化版。

让我们按照以下步骤启动`SenseCraft AI`：

* 在 Web 浏览器（如`Chrome`）中打开 [SenseCraft AI Vision Workspace](https://sensecraft.seeed.cc/ai/device/local/32)并登录（或创建账户）。

![](img/file626.png)

* 将 XIAOML Kit 物理连接到笔记本电脑，按如下所示选择它：

![](img/file627.png)

> 注意：`WebUSB`工具在`Safari`等浏览器中可能无法正常工作。请改用`Chrome`。此外，确认 Arduino IDE 或任何其他设备未连接到 XIAO。

为了看到摄像头工作，我们需要上传模型。我们可以尝试 Seeed Studio 之前上传的几个计算机视觉模型。使用`Select Model`按钮并在可用模型中进行选择。

将光标悬停在 AI 模型上，我们可以获取有关它们的信息，如名称、`category`或`task`（图像分类、目标检测或姿态/关键点检测）、`algorithm`（如`YOLO5`或`V8`、`MobileNet V2`等）。

![](img/file628.png)

（注：后续文本因原文存在重复乱码，已按指令要求进行处理。）

* **三轴陀螺仪**：测量绕 X、Y、Z 轴的角速度（旋转速率）

### 技术规格

* **通信**：地址为`0x6A`的`I2C`接口
* **加速度范围**：`±2/±4/±8/±16 g`（默认使用`±2g`）
* **陀螺仪范围**：`±125/±250/±500/±1000/±2000 dps`（默认使用`±250 dps`）
* **分辨率**：`16-bit ADC`
* **功耗**：超低功耗设计

### 坐标系

该传感器遵循右手坐标系。当从点标记可见的角度观察 IMU 传感器（扩展板底部）时：

![](img/file638.png)

* **X 轴**：指向右侧
* **Y 轴**：指向前方（远离你）
* **Z 轴**：指向上方（垂直出板外）

![](img/file639.png)

### 所需库

在上传代码之前，请安装所需的库：

1. 打开`Arduino IDE`并选择`Manage Libraries`（由`书籍图标`表示）。
2. 对于 IMU 库，输入`LSM6DS3`，并选择`Seeed Arduino LSM6DS3 by Seeed`。你可以`INSTALL`或`UPDATE`开发板支持包。

![](img/file640.png)

⚠️ **重要**：不要安装`Arduino_LSM6DS3 by Arduino` - 那是给不同板使用的！

### 测试代码

在 Arduino IDE 中输入以下代码并将其上传到 Kit 中：

```
```

```

```

串口监视器（Serial monitor）将显示这些值，绘图器（plotter）将显示它们随时间的变化。例如，通过移动 Kit 跨越`y-axis`，我们将看到数值 2（红线）发生相应的变化。注意`z-axis`由数值 3（绿线）表示，其接近`1.0g`。蓝线（数值 1）与`x-axis`相关。

![](img/file641.png)

你可以选择数值 4 到 6 来观察陀螺仪的行为。

### 测试 OLED 显示屏 (SSD1306)

OLED（有机发光二极管）显示屏是自光屏幕，每个像素都能产生自己的光。XIAO ML 套件配备一个紧凑的 0.42 英寸单色 OLED 显示屏，非常适合显示传感器数据、状态信息和简单图形。

### 技术规格

* **尺寸**：0.42 英寸对角线
* **分辨率**：`72 × 40 像素`
* **控制器**：`SSD1306`
* **接口**：地址为`0x3C`的`I2C`
* **颜色**：单色（白色背景上的黑色像素，或反之）
* **可视性**：高对比度，在强光下可见
* **功耗**：低功耗，无需背光

### 显示特性

* **像素级精准**：2,880 个像素 (72×40) 中的每一个像素都可以被独立控制
* **快速刷新**：适用于动画和实时数据
* **无拖影**：像素级瞬时响应
* **宽视角**：从多个位置均清晰

### 所需库

在上传代码之前，请安装所需的库：

1. 打开`Arduino IDE`并选择`Manage Libraries`（由`书籍图标`表示）。
2. 输入`u8g2`并选择`U8g2 by oliver`。你可以`install`或`update`开发板支持包。

ℹ️ **注意**：`U8g2`是一个强大的图形库，支持许多显示类型![](img/file642.png)

`U8g2`库具有以下单色图形功能：

* 支持许多类型显示器（包括`SSD1306`）
* 使用各种字体进行文本渲染
* 绘制基础几何图形（线、圆）
* 内存高效的分页渲染
* 硬件和软件`I2C`支持

### 测试代码

在 Arduino IDE 中输入以下代码并将其上传到 Kit 中：

```
```

```

```

如果一切运行正常，你应该能看到显示屏上矩形框内的“Hello World”。

![](img/file643.jpg)

### OLED - 文本尺寸与定位

注意文本位置是通过`setCursor(x, y)`设置的，在此情况下：

```
```

```

```

代码中使用的字体是中号。但还有其他尺寸可用：

* `u8g2_font_4x6_tr`:极小字体（4×6 像素）
* `u8g2_font_6x10_tr`:小字体（6×10 像素）
* `u8g2_font_ncenB08_tr`:中等粗体字体
* `u8g2_font_ncenB14_tr`:大粗体字体

### 形状

代码添加了一个简单的装饰，在文本周围画了一个框：

```
```

```

```

但其他形状可用：
