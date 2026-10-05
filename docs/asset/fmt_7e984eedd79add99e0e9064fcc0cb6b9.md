
从上述图像，我们可以为模拟定义：主要的水平运动（`x` 或 `y` 轴）应与“陆路类”相关，垂直运动（`z` 轴）与“叉车类”相关，无活动对应“闲置类”，而三个轴上的运动则对应[海上类](https://www.containerhandbuch.de/chb_e/stra/index.html?/chb_e/stra/stra_02_03_03.htm)。

`(media/file581.jpg)`

`(media/file582.jpg)`

对于数据收集，我们有多种选择。在实际案例中，我们可以让设备（例如）直接连接到一个容器上，并将数据收集在文件中（例如 `.CSV`），然后存储在 SD 卡上（通过 `SPI` 连接）或计算机上的离线仓库中。数据也可以通过蓝牙远程发送到附近的仓库，例如手机（正如在本项目中所的那样：[传感器数据日志记录器](https://www.hackster.io/mjrobot/sensor-datalogger-50e44d)）。一旦数据集被收集并存储为 `.CSV` 文件，就可以使用 [CSV 向导工具](https://docs.edgeimpulse.com/docs/edge-impulse-studio/data-acquisition/csv-wizard) 上传到 Studio。

> 在此[视频](https://youtu.be/2KBPq_82WM)中，你可以学习发送数据到 Edge Impulse Studio 的其他方法。

## 将设备连接到 Edge Impulse

我们将 `Nicla` 直接连接到 Edge Impulse Studio，它也将被用于数据预处理、模型训练、测试和部署。为此，你有两个选择：

1. 下载最新的固件并将其直接连接到 `Data Collection` 部分。
2. 使用 [CLI Data Forwarder](https://docs.edgeimpulse.com/docs/edge-impulse-cli/cli-data-forwarder) 工具从传感器捕获数据并将其发送到 Studio。

选项 1 更直观，正如我们在 *Setup Nicla Vision* 动手操作中看到的，但选项 2 将在采集数据方面提供更高的灵活性，例如采样频率的定义。让我们使用最后一种方法。

请在 Edge Impulse Studio (EIS) 上创建一个新项目并按照以下步骤将 `Nicla` 连接到它：

1. 在计算机上安装 [Edge Impulse CLI](https://docs.edgeimpulse.com/docs/edge-impulse-cli/cli-installation) 和 [Node.js](https://nodejs.org/en/)。
2. 上传一个用于数据采集的 `sketch`（在本教程之前讨论过的那个）。
3. 使用 [CLI Data Forwarder](https://docs.edgeimpulse.com/docs/edge-impulse-cli/cli-data-forwarder) 捕获 `Nicla` 加速度计的数据并发送到 Studio，如图所示：

`![](img/file583.jpg)`

在终端上启动 [CLI Data Forwarder](https://docs.edgeimpulse.com/docs/edge-impulse-cli/cli-data-forwarder)，并（如果是第一次运行）输入以下命令：

```bash
$ edge-impulse-data-forwarder --clean
```

接下来，输入你的 EI 凭据并选择你的项目、变量（例如 `accX`、`accY` 和 `accZ`）以及设备名称（例如 `NiclaV`）：

`![](img/file584.jpg)`

进入 EI 项目的 `Devices` 部分，验证设备是否已连接（圆点应该是绿色的）：

`![](img/file585.jpg)`

> 你可以克隆此实验开发的项目：[NICLA 运动分类](https://studio.edgeimpulse.com/public/302078/latest)。

## 数据收集

在 `Data Acquisition` 部分，你应该看到你的开发板 `[NiclaV]` 已连接。传感器可用：`[3 轴传感器 (accX, accY, accZ)]`，采样频率为 `[50 Hz]`。Studio 建议采样长度为 `[10000]` ms（10 秒）。最后剩下就是定义样本标签。让我们从 `[terrestrial]`（陆路）开始：

`![](img/file586.jpg)`

**Terrestrial**（陆路，卡车或火车上的托盘），水平移动。点击 `[Start Sample]` 并水平移动你的设备，在桌子上保持一个方向。10 秒后，你的数据将上传到 studio。以下是样本的采集方式：

`![](img/file587.jpg)`

正如预期的，运动主要在 `Y` 轴上被捕获（绿色）。在蓝色部分，我们看到 `Z` 轴，约为 `-10 m/s²`（`Nicla` 的相机朝上）。

如之前讨论的，我们应该捕获所有四个运输类别（Transportation Classes）的数据。想象一下你有一个内置加速度计的容器，面临以下情况：

**Maritime**（海运，愤怒的海中船上的托盘）。运动在三个轴上都被捕获了：

`![](img/file588.jpg)`

**Lift**（起重，叉车垂直处理托盘）。运动仅在 `Z` 轴上被捕获：

`![](img/file589.jpg)`

**Idle**（闲置，仓库中的托盘）。加速度计未检测到运动：

`![](img/file590.jpg)`

你可以为这四个类别中的每个类别采集 2 分钟（十二个 10 秒的样本，总共 8 分钟的数据）。在每个样本后使用 `三个点` 菜单，选择其中 2 个，将其留给测试集。或者，你可以使用 `Dashboard` 标签页中 `Danger Zone` 部分的自动 `Train/Test Split tool`。在下方你可以看到结果数据集：

`![](img/file591.jpg)`

一旦捕获了数据集，你可以使用 [Data Explorer](https://docs.edgeimpulse.com/docs/edge-impulse-studio/data-acquisition) 进行更详细的探索，它是一个寻找异常值或标记错误的数据的工具。它首先通过信号处理提取这些特征，然后使用 [PCA](https://en.wikipedia.org/wiki/Principal_component_analysis) 或 [t-SNE](https://en.wikipedia.org/wiki/T-distributed_stochastic_neighbor_embedding) 等降维算法将其映射到 2D 空间。这让你对整个数据集有一个概览。

`![](img/file592.jpg)`

在我们的案例中，数据集看起来良好（分离）。但 PCA 显示海运（绿色）和起重（橙色）之间存在问题。这是预期的，一旦在船上，运动有时是垂直的。

## Impulse Design

下一步是定义我们的 `Impulse`，它接收原始数据并使用信号处理提取特征，将其作为学习块的输入。进入 `Impulse Design` 并点击 `Create Impulse`。Studio 将建议基础设计。让我们为 `Anomaly Detection` 添加第二个学习块。

`![](img/file593.jpg)`

第二个模型使用 `KMeans` 模型。如果我们假设已知类别为聚类，任何无法拟合的样本都可能是异常值、异常，例如容器从船上滚落或从叉车掉落。

`![](img/file594.jpg)`

采样频率应该是自动捕获的，如果没有，请输入：`[50]` Hz。Studio 建议窗口大小（Window Size）为 2 秒（`[2000]` ms），滑动窗口（sliding window）为 `[20]` ms。我们在这一步中定义的是我们将预处理捕获的数据（时间序列数据），创建一个表格数据集特征，作为神经网络分类器（`DNN`）和异常检测模型（`K-Means`）的输入，如下：

`![](img/file595.jpg)`

让我们深入这些步骤和参数，以更好地理解我们正在做什么。

### 数据预处理概述

数据预处理是从加速度计采集的数据集中提取特征，涉及对原始数据进行处理和分析。加速度计测量沿一个或多个轴（通常为三个，标记为 *X*、*Y* 和 *Z*）的加速度。这些测量可以了解各个方面，例如运动模式和振动。

原始加速度数据可能包含噪声、错误或无关信息。预处理步骤（如过滤和标准化）可以清理并标准化数据，使其更适合特征提取。在我们的情况下，我们应该将数据分为更小的段或**窗口**。这有助于关注特定的事件或活动，使特征提取更具可靠性和意义。**窗口大小**和重叠（窗口增加）的选择取决于应用程序以及感兴趣事件的频率。作为一个经验法则，我们应该尝试捕捉几个“数据周期”。

> 使用 50 Hz 的采样率 (`SR`) 和 2 秒的窗口大小，每个轴将获得 100 个样本，总共 300 个（3 轴 × 2 秒 × 50 样本）。我们将每隔 200 毫秒滑动一次窗口，创建一个更大的数据集，每个实例都具有 300 个原始特征。

`![](img/file596.jpg)`

一旦数据完成预处理和分段，就可以提取描述运动特征的特征。从加速度计数据中提取的一些典型特征包括：

* **时域**特征描述每个分段内数据的统计属性，如平均值、中位数、标准差、偏度、峰度和过零率。
* **频域**特征通过快速傅里叶变换 (`FFT`) 等技术将数据转换到频域获得。一些典型的频域特征包括功率谱、频谱能量、主频（幅和频率）以及谱熵。
* **时频域**特征结合了时域和频域信息，例如短时傅里叶变换 (`STFT`) 或离散小波变换 (`DWT`)。它们可以更详细地理解信号频率内容随时间变化的情况。

在许多情况下，提取的特征数量可能很大，这会导致过拟合或增加计算复杂度。特征选择技术（如互信息、基于相关的方法或主成分分析 (`PCA`)）可以帮助识别特定应用最相关的特征并降低数据集的维度。Studio 可以帮助此类特征重要性的计算。

## EI Studio 频谱特征

数据预处理是嵌入式机器学习领域的一个挑战性领域，但 Edge Impulse 通过其数字信号处理 (`DSP`) 预处理步骤帮助克服这一问题，特别是[频谱特征模块](https://docs.edgeimpulse.com/docs/edge-impulse-studio/processing-blocks/spectral-features)。

在 Studio 中，收集到的原始数据集将作为频谱分析模块的输入，它非常适合分析重复运动，例如来自加速度计的数据。该模块将执行 `DSP`（数字信号处理），提取如 [FFT](https://en.wikipedia.org/wiki/Fast_Fourier_transform) 或 [Wavelets](https://en.wikipedia.org/wiki/Digital_signal_processing#Wavelet) 等特征。

对于我们的项目，一旦时间信号是连续的，我们应该使用 `FFT`，例如长度为 `[32]`。

每个轴/通道的**时域统计特征**是：

* [RMS](https://en.wikipedia.org/wiki/Root_mean_square): 1 个特征
* [Skewness](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FSkewness): 1 个特征
* [Kurtosis](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FKurtosis): 1 个特征

每个轴/通道的**频域频谱特征**是：

* [Spectral Power](https://en.wikipedia.org/wiki/Spectral_density): 16 个特征 (`FFT` 长度/2)
* Skewness: 1 个特征
* Kurtosis: 1 个特征

在许多情况下，提取的特征数量可能很大，这会导致过拟合或增加计算复杂度。特征选择技术（如互信息、基于相关的方法或主成分分析 (`PCA`)）可以帮助识别特定应用最相关的特征并降低数据集的维度。Studio 可以帮助此类特征重要性的计算。

[Spectral Power](https://en.wikipedia.org/wiki/Spectral_density): 16 个特征 (`FFT` 长度/2)

* Skewness: 1 个特征
* Kurtosis: 1 个特征

每个轴/通道的**时域统计特征**是：

* [RMS](https://en.wikipedia.org/wiki/Root_mean_square): 1 个特征
* [Skewness](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FSkewness): 1 个特征
* [Kurtosis](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FKurtosis): 1 个特征

每个轴/通道的**频域频谱特征**是：

* [Spectral Power](https://en.wikipedia.org/wiki/Spectral_density): 16 个特征 (`FFT` 长度/2)
* Skewness: 1 个特征
* Kurtosis: 1 个特征

每个轴/通道的**时域统计特征**是：

* [RMS](https://en.wikipedia.org/wiki/Root_mean_square): 1 个特征
* [Skewness](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FSkewness): 1 个特征
* [Kurtosis](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FKurtosis): 1 个特征

每个轴/通道的**频域频谱特征**是：

* [Spectral Power](https://en.wikipedia.org/wiki/Spectral_density): 16 个特征 (`FFT` 长度/2)
* Skewness: 1 个特征
* Kurtosis: 1 个特征

每个轴/通道的**时域统计特征**是：

* [RMS](https://en.wikipedia.org/wiki/Root_mean_square): 1 个特征
* [Skewness](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FSkewness): 1 个特征
* [Kurtosis](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FKurtosis): 1 个特征

每个轴/通道的**频域频谱特征**是：

* [Spectral Power](https://en.wikipedia.org/wiki/Spectral_density): 16 个特征 (`FFT` 长度/2)
* Skewness: 1 个特征
* Kurtosis: 1 个特征

每个轴/通道的**时域统计特征**是：

* [RMS](https://en.wikipedia.org/wiki/Root_mean_square): 1 个特征
* [Skewness](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FSkewness): 1 个特征
* [Kurtosis](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FKurtosis): 1 个特征

每个轴/通道的**频域频谱特征**是：

* [Spectral Power](https://en.wikipedia.org/wiki/Spectral_density): 16 个特征 (`FFT` 长度/2)
* Skewness: 1 个特征
* Kurtosis: 1 个特征

每个轴/通道的**时域统计特征**是：

* [RMS](https://en.wikipedia.org/wiki/Root_mean_square): 1 个特征
* [Skewness](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FSkewness): 1 个特征
* [Kurtosis](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FKurtosis): 1 个特征

每个轴/通道的**频域频谱特征**是：

* [Spectral Power](https://en.wikipedia.org/wiki/Spectral_density): 16 个特征 (`FFT` 长度/2)
* Skewness: 1 个特征
* Kurtosis: 1 个特征
