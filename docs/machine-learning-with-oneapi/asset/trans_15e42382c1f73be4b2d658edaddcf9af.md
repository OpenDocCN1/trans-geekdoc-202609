
### Intel® C++ 编译器 Classic

安装程序几乎与前面讨论的 Intel oneAPI Base Toolkit 相同。但是，可安装程序需从链接 [https://www.intel.com/content/www/us/en/developer/tools/oneapi/iot-toolkit-download.html](https://www.intel.com) 下载。

### Intel oneAPI 渲染工具包

此工具包面向创意人士。是的，从事可视化及相关领域的工作人员可以使用此工具包创建性能卓越、高保真度的可视化应用。该工具包对开发者使用和开发出惊艳成果非常有趣，并且包含以下列出的一些工具：
* Embree
* Implicit SPMD Program Compiler
* Open Volume Kernel Library
* Open Image Denoise
* OpenSWR
* OSPRay
* OSPRay Studio
* OSPRay for Hydra
* Rendering Toolkit Utilities

安装程序所需时间几乎与 Intel oneAPI Base Toolkit 相同。但是，可安装程序需从以下链接下载：[https://www.intel.com/content/www/us/en/developer/tools/oneapi/rendering-toolkit-download.html](https://www.intel.com)。

### Intel AI 分析工具包

这是最好的工具包之一，业界已纷纷对该工具包给予赞誉。有了此工具包，可以使用经过优化的 DL（深度学习）框架和高性能 Python 库加速机器学习和数据科学管道。此工具包功能强大且资源丰富。工具包包含以下工具：
* Intel Optimization for TensorFlow
* Intel Optimization for PyTorch
* Intel Distribution for Python*
* Intel Distribution of Modin (available through Anaconda only)
* Model Zoo for Intel Architecture
* Intel Low-Precision Optimization Tool

可以在以下链接下载 AI Analytics Toolkit：[https://www.intel.com/content/www/us/en/developer/tools/oneapi/ai-analytics-toolkit-download.html?operatingsystem=linux&distributions=zypperpackagemanager](https://www.intel.com)。

### Intel OpenVINO

这是最出色的工具包之一。它是开放视觉推理和神经网络优化。用户可以使用 OpenVINO 开发和部署从边缘到云的高性能推理和应用。OpenVINO 可以通过以下提供的指南和可安装程序无缝下载和安装：[https://www.intel.com/content/www/us/en/developer/tools/openvino-toolkit/overview.html](https://www.intel.com)。

![图 2.15 oneAPI 工具包（部分由 oneAPI 提供支持）。](images/fig2.15.jpg)

**图 2.15** oneAPI 工具包（部分由 oneAPI 提供支持）。

所有这些工具包的最大优势在于它们免费使用且易于学习。工具包可为 Windows、Linux 或 Mac OS 安装。此外，如果开发者希望使用 DevCloud，也是可能的，并且无需安装或任何额外下载。开发很容易，结果立即可用。

另一个值得称赞的优势是，为初学者提供了大量教程和学习材料。还提供了许多案例研究以确保循序渐进的学习。

好吧，我们衷心希望读者能喜欢探索这些工具包。让我们继续下一章，了解有关 DevCloud 的更多详细信息，包括其功能、性能等。

## 资源
* [https://www.intel.com/content/www/us/en/developer/tools/oneapi/overview.html#gs.3otusu](https://www.intel.com)
* [https://www.intel.com/content/www/us/en/developer/tools/oneapi/toolkits.html#gs.kfp7z3](https://www.intel.com)
* [https://youtu.be/FdntPy1cCKo](https://youtu.be)
* [https://youtu.be/_y4bPjj8Gv4](https://youtu.be)

## 2.2 需要记住的关键点
1. 每个 oneAPI 工具包都包含一套工具。
2. oneAPI 工具包可以直接按照提供的指南安装到机器上，或者可以使用 DevCloud 开发应用程序。
3. DevCloud 使开发者能够在无需任何安装或配置的情况下轻松开发应用程序。
4. oneAPI Base Toolkit 拥有用于使用 C++、DPC++ 构建应用程序的高性能工具包。
5. 使用 oneAPI HPC Toolkit，可以构建和交付快速的 Fortran、OpenMP 和 MPI 应用程序，将高性能计算应用与前沿技术相结合。
6. 可视化及相关领域可以使用 oneAPI Rendering Toolkit 创建性能卓越、高保真度的可视化应用。
7. 有了 AI Analytics Toolkit，可以使用经过优化的 DL 框架和高性能 Python 库加速机器学习和数据科学管道。
8. 可以使用 OpenVINO Toolkit 开发和部署从边缘到云的高性能推理和应用。

## 测验
1. 解释某人选择 Intel oneAPI Base Toolkit 的需求。
2. 选择 Intel IoT Toolkit 可以获得哪些功能？
3. 列出随 Intel oneAPI AI analytics toolkit 提供的库/包名称。
4. 哪个工具包对从事可视化应用开发的开发者最有帮助？
5. 如果有人从事 HPC 应用开发，哪个工具包对他们最有帮助？

# 3 Intel DevCloud 与 Jupyter Notebook

DOI: [10.1201/9781003393122-3](https://doi.org/10.1201/9781003393122-3)

## 学习目标

阅读本章后，读者应能够理解以下内容：
* DevCloud 的强大功能
* 注册流程
* Jupyter Notebook 与 DevCloud
* DevCloud 命令

## 3.1 引言

本章将提供有关 Intel DevCloud 基础知识的诸多见解。此外，Jupyter Notebook 已与 DevCloud 集成，使得软件开发人员的学习和使用变得更加容易。预计读者应创建 Intel DevCloud 账户，以尝试本章讨论的所有要点。

## 3.2 什么是 Intel DevCloud？

DevCloud 是一个有趣且功能强大的沙箱，使某人能够使用 Intel oneAPI 软件堆栈在包括 Intel CPU、GPU 和 FPGA 在内的多种加速器上开发、测试和运行工作负载。

它拥有众多功能且功能强大。[图 3.1](#c3.xhtml#f3.1) 展示了 Intel DevCloud 的功能。使用 DevCloud 编码很容易，无需担心硬件采购；更重要的是，无需安装或配置。它还为开发者提供了出色且易于理解的教程。最重要的是，对 Jupyter Notebook 和 Visual Studio Code 的支持使其比最受欢迎的云平台更胜一筹。

![图 3.1 汇总的 Intel DevCloud 功能。](images/fig3.1.jpg)

[**图 3.1**](#c3.xhtml#re_f3.1) Intel DevCloud 功能汇总。

可以从网站 software.intel.com/devcloud/oneapi 找到有关 Intel DevCloud 的大量有用信息

### 3.2.1 如何创建 DevCloud 账户？

可以按照下面介绍的逐步流程创建 DevCloud 账户/访问权限。
1. 访问 software.intel.com/devcloud/oneapi 网站。

它会提示您填写某些基本信息，这不会花费太多时间。下面在 [图 3.2](#c3.xhtml#f3.2) 中展示的屏幕截图揭示了所需的信息。
2. 完成上述信息后，将向您提出另外两个问题，邀请您做出回应，如 [图 3.3](#c3.xhtml#f3.3) 所示。可以选择适当的答案。

完成此操作后，就完成了。
3. 然后需要同意条款和条件。可以阅读条款和条件并通过点击复选框同意。一旦完成，点击提交按钮，账户即完成（[图 3.4](#c3.xhtml#f3.4)）。

