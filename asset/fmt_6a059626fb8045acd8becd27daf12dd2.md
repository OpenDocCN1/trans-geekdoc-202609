
# 概览 (Overview)

这些实验室提供了一个获取机器学习（ML）系统实践经验的独特机会。与需要数据中心级资源的大模型不同，这些练习使你能够使用 TinyML 直接与硬件和软件交互。这种实操方法让你直观地理解部署 AI 的挑战与机遇，尽管其规模较小。然而，其原理与你在处理更大型系统时遇到的原理大部分是相同的。

![](img/file609.png)

## 前提条件 (Pre-requisites)

* **XIAOML 工具包**：
  * **XIAO ESP32S3 Sense** 开发板
  * 带有 6 轴 IMU 和 0.42 英寸 OLED 显示屏的**扩展板**
  * **SD 卡工具包**：
    * 用于存储数据的 SD 卡和 USB 适配器
    * 用于连接板到电脑的 USB-C 线
* **网络**：需要访问互联网以下载软件。

## 设置 (Setup)

* 设置 XIAOML Kit

## 练习 (Exercises)

| 模态 | 任务 |  | 链接 |
| --- | --- | --- | --- |
| **视觉** | 图像分类 | 学习分类图像 | 链接 |
| **视觉** | 目标检测 | 实现目标检测 | 链接 |
| **音频** | 关键词识别 | 探索语音识别系统 | 链接 |
| **IMU** | 运动分类与异常检测 | 分类运动数据并检测异常 | 链接 |

# 安装

![DALL·E prompt - 一幅 1950 年卡通风格的画，描绘了一个 XIAO ESP32S3 开发板，带有独特的摄像头模块，如提供的图像所示。开发板放置在经典的实验台上，周围有各种传感器，包括一个麦克风。开发板后面，一台复古电脑屏幕显示着色彩柔和的 Arduino IDE，代码侧重于 LED 引脚设置和用于语音命令的机器学习推理。IDE 串口监视器显示了检测到“yes”和“no”等语音命令的输出。该场景将中世纪实验室的复古魅力与现代电子产品融合。](img/file610.jpg)

*DALL·E prompt - 一幅 1950 年卡通风格的画，描绘了一个 XIAO ESP32S3 开发板，带有独特的摄像头模块，如提供的图像所示。开发板放置在经典的实验台上，周围有各种传感器，包括一个麦克风。开发板后面，一台复古电脑屏幕显示着色彩柔和的 Arduino IDE，代码侧重于 LED 引脚设置和用于语音命令的机器学习推理。IDE 串口监视器显示了检测到“yes”和“no”等语音命令的输出。该场景将中世纪实验室的复古魅力与现代电子产品融合。*

## 概述

[XIAOML 套件](https://www.seeedstudio.com/The-XIAOML-Kit.html) 设计旨在提供 TinyML 应用的动手体验。该套件包含强大的 [XIAO ESP32S3 Sense](https://www.seeedstudio.com/XIAO-ESP32S3-Sense-p-5639.html) 开发板以及一个为机器学习项目添加必要传感器的扩展板。

**完整的 XIAOML 套件组件：**

* **XIAO ESP32S3 Sense**：主开发板，集成了摄像头传感器、数字麦克风并支持 SD 卡
* **扩展板**：配备了 6 轴 IMU（`LSM6DS3TR-C`）和 0.42 英寸 OLED 显示器，用于运动感知和数据可视化
* **SD 卡工具箱**：包含 SD 卡和 USB 适配器，用于数据存储和模型部署
* **USB-C 线**：用于将开发板连接到计算机
* **天线和散热器**

> ⚠️ **注意**
>
> 如果您想使用 XIAO ML 套件扩展板，请**不要在 XIAO ESP32S3 上安装散热器**（或请小心地移除它们）。请参阅附录获取更多信息。

![](img/file611.png)

### XIAO ESP32S3 Sense - 核心板级特性

[XIAO ESP32S3 Sense](https://www.seeedstudio.com/XIAO-ESP32S3-Sense-p-5639.html) 是 XIAOML 套件的核心，将嵌入式 ML 计算能力与摄影和音频功能相结合，使其成为智能语音和视觉 AI 中 TinyML 应用的理想平台。

![](img/file612.png)

**主要特性**

* **强大的 MCU**：`ESP32S3` 32 位、双核、Xtensa 处理器，运行频率高达 240 MHz，支持 Arduino / MicroPython

# EI Studio 频谱特征

数据预处理是嵌入式机器学习领域的一个挑战性领域，但 Edge Impulse 通过其数字信号处理（`DSP`）预处理步骤帮助克服这一问题，特别是[频谱特征模块](https://docs.edgeimpulse.com/docs/edge-impulse-studio/processing-blocks/spectral-features)。

在 Studio 中，收集到的原始数据集将作为频谱分析模块的输入，它非常适合分析重复运动，例如来自加速度计的数据。该模块将执行 `DSP`（数字信号处理），提取如 [FFT](https://en.wikipedia.org/wiki/Fast_Fourier_transform) 或 [Wavelets](https://en.wikipedia.org/wiki/Digital_signal_processing#Wavelet) 等特征。

对于我们的项目，一旦时间信号是连续的，我们应该使用 `FFT`，例如长度为 `[32]`。

每个轴/通道的**时域统计特征**是：

* [RMS](https://en.wikipedia.org/wiki/Root_mean_square)：1 个特征
* [Skewness](https://colab.research.google.com/corgiredirector?site=https%3A%2F%Fen.wikipedia.org%2Fwiki%2FSkewness)：1 个特征
* [Kurtosis](https://colab.research.google.com/corgiredirector?site=https%3A%2F%Fen.wikipedia.org%2Fwiki%2FKurtosis)：1 个特征

每个轴/通道的**频域频谱特征**是：

* [Spectral Power](https://en.wikipedia.org/wiki/Spectral_density)：16 个特征（FFT 长度/2）
* Skewness：1 个特征
* Kurtosis：1 个特征

在许多情况下，提取的特征数量可能很大，这会导致过拟合或增加计算复杂度。特征选择技术（如互信息、基于相关的方法或主成分分析（`PCA`））可以帮助识别特定应用最相关的特征并降低数据集的维度。Studio 可以帮助计算此类特征重要性。

请注意，Edge Impulse 创建的代码采用了 `sensor fusion`（传感器融合）方法，其中使用了 `IMU`（加速度计和陀螺仪）和 `ToF`。在代码开头，你包含了与我们项目相关的库：`IMU` 和 `ToF`：

```
```

> 你在测试期间，你可以保持代码不变，因为训练好的模型将仅使用从加速度计中预处理的特征。但请考虑，在实际项目中，你将只使用所需的库编写代码。

就这些了！

你现在可以将代码上传到你的设备并进行推理了。按两次 Nicla 的 `[RESET]` 按钮使其进入启动模式（如果仍连接到 Studio，请断开连接），并将 Sketch 上传到你的开发板上。

现在，你应该尝试用开发板进行不同的动作（与数据采集期间进行的动作类似），并在串口监视器（Serial Monitor）上观察每个类的推理结果：

* **空闲和抬起类（Idle and lift classes）**：

![](img/file605.jpg)

* **海洋和陆地（Maritime and terrestrial）**：

![](img/file606.jpg)

注意，在上述所有情况下，`anomaly score`（异常评分）的值都小于 0.0。尝试一个不在原始数据集中的新动作，例如，“翻转”Nicla 使其倒朝相机，就像从船上掉落的集装箱或船难一样：

* **异常检测（Anomaly detection）**：

![](img/file607.jpg)

在这种情况下，异常值大得多，超过了 1.00

## 后处理 (Post-processing)

既然我们知道模型可以正常工作（因为它能检测到动作），我们建议你修改代码以便在 `NiclaV` 完全离线的情况下查看结果（断开与 PC 连接并使用电池、充电宝或独立的 5 V 电源供电）。

其思路与 KWS 项目相同：如果检测到特定的动作，则亮起特定的 LED。例如，如果检测到 `terrestrial`（陆地），绿色 LED 会亮；如果检测到 `maritime`（海洋），红色 LED 会亮；如果是 `lift`（抬起），蓝色 LED 会亮；如果没有检测到任何动作（`idle`，空闲），则所有 LED 熄灭。你还可以在检测到异常时添加一个条件，在这种情况下，例如可以使用白色（所有 LED 同时亮起）。

## 总结 (Summary)

> 本实操教程中使用的笔记本和代码可以在 [GitHub](https://github.com/Mjrovai/Arduino_Nicla_Vision/tree/main/Motion_Classification) 仓库中找到。

在我们结束之前，请考虑动作分类（Movement Classification）和目标检测（Object Detection）可以应用于许多领域的许多场景。以下是一些潜在的应用场景：

### 案例应用 (Case Applications)

#### 工业与制造业

* **预测性维护**：检测机器运动中的异常，以便在故障发生前进行预测。
* **质量控制**：监控流水线或机械臂的运动，进行精确评估并检测偏离标准运动模式的偏差。
* **仓库物流**：使用自动化系统管理和跟踪货物移动，分类不同类型的运动并检测处理过程中的异常。

#### 医疗健康

* **患者监控**：检测老年人或行动不便人士的跌倒或异常动作。
* **康复**：通过分类物理治疗期间的运动模式，监测受伤患者的康复进展。
* **活动识别**：为健身应用或患者监控对身体活动类型进行分类。

#### 消费电子

* **手势控制**：解释特定动作以控制设备，例如通过挥手开灯。
* **游戏**：通过运动控制的输入增强游戏体验。

#### 交通与物流

* **车辆遥测**：监控车辆运动，以检测异常行为，如急制动、急转或事故。
* **货物监控**：通过检测可能指示篡改或处理不当的异常运动，确保货物在运输过程中的完整性。

#### 智能城市与基础设施

* **结构健康监测**：检测结构内的振动或运动，这些可能预示着潜在的故障或维护需求。
* **交通管理**：分析行人和车辆流量，以提高城市流动性和安全性。

#### 安全与监控

* **入侵者检测**：检测典型的未经授权访问或其他安全违规的运动模式。
* **野生动物监控**：检测保护区内的盗猎者或异常动物运动。

#### 农业

* **设备监控**：跟踪农业机械的性能和使用情况。
* **动物行为分析**：监控牲畜运动，以检测指示健康问题或压力的行为。

#### 环境监测

* **地震活动**：检测地震或其他地质相关事件之前的不规则运动模式。
* **海洋学**：为了研究和安全目的，研究波浪模式或海洋运动。

### Nicla 3D 案例

对于实际应用（如之前描述的某些情况），我们可以为设备添加一个外壳。来自 Edge Impulse 的 Eoin Jordan 为 Nicla 系列开发板开发了一个非常棒的可穿戴和机器健康外壳。它适用于 10mm 磁铁、M2 螺丝和 16mm 表带，适用于人体和机器健康使用场景。链接在此处：[Arduino Nicla Voice and Vision Wearable Case](https://www.thingiverse.com/thing:5923305)。

![](img/file608.jpg)

动作分类和异常检测的应用非常广泛，Arduino Nicla Vision 非常适合低功耗和边缘处理具有优势的场景。其微小的外形和高效的处理能力使其成为部署实时处理至关重要且连接可能受限的便携远程应用的理想选择。

## 资源 (Resources)

* [Arduino 代码](https://github.com/Mjrovai/Arduino_Nicla_Vision/tree/main/Motion_Classification/Niclav_Acc_Data_Capture)
* [Edge Impulse 频谱特征 Colab 笔记本](https://colab.research.google.com/github/Mjrovai/Arduino_Nicla_Vision/blob/main/Motion_Classification/Edge_Impulse_Spectral_Features_Block.ipynb)
* [Edge Impulse 项目](https://studio.edgeimpulse.com/public/302078/latest)

此处用于确保在某个部分开始之前正确插入测验。
