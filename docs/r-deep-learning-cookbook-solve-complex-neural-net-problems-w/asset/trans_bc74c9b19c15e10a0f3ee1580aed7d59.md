

## 下载本书的彩色图像

我们还为您提供一份包含本书中使用的屏幕截图/图表彩色图像的 PDF 文件。彩色图像将帮助您更好地理解输出的变化。您可以从 https://www.packtpub.com/sites/default/files/downloads/RDeepLearningCookbook_ColorImages.pdf 下载此文件。

## 勘误

虽然我们已竭力确保内容的准确性，但难免会出现错误。如果您在我们的某本书中发现错误——可能是文本或代码中的错误——我们将不胜感激，如果您能将其报告给我们。这样一来，您可以避免其他读者感到沮丧，并帮助我们改进本书的后续版本。如果您发现任何勘误，请访问 http://www.packtpub.com/submit-errata，选择您的书，单击 Errata Submission Form 链接，并输入勘误详细信息。一旦您的勘误得到验证，您的提交将被接受，勘误将上传到我们的网站，或添加到该书名下 Errata 部分的任何现有勘误列表中。

要查看先前提交的勘误，请访问 https://www.packtpub.com/books/content/support，并在搜索字段中输入书名。所需信息将出现在该书名下的 Errata 部分。

## 盗版

互联网上受版权保护材料的盗版是所有媒体中持续存在的问题。在 Packt，我们非常重视对我们版权和许可的保护。如果您在互联网上以任何形式发现我们作品的非法副本，请立即向我们提供位置地址或网站名称，以便我们可以追究责任。

请通过 copyright@packtpub.com 与我们联系，并附上疑似盗版材料的链接。

感谢您帮助保护我们的作者以及我们为您提供有价值内容的能力。

## 问题

如果您对本书的任何方面有任何问题，可以通过 questions@packtpub.com 联系我们，我们将尽力解决该问题。

## 开始使用

在本章中，我们将介绍以下主题：

- 在 IDE 中安装 R
- 安装 Jupyter Notebook 应用程序
- 从 R 中机器学习的基础知识入手
- 在 R 中设置深度学习工具/包
- 在 R 中安装 MXNet
- 在 R 中安装 TensorFlow
- 在 R 中安装 H2O
- 使用 Docker 一次性安装所有三个包

### 简介

本章将帮助您入门深度学习，并协助您搭建系统以开发深度学习模型。本章更侧重于向读者介绍本书的预期内容以及阅读本书所需的先决条件。当前本书面向希望快速建立深度学习应用背景的学生或专业人士。本书将更加注重实践和应用，以 R 作为构建深度学习模型的工具。

> 有关深度学习的详细理论，请参阅 Goodfellow 等人 2016 年的 Deep Learning。有关机器学习背景，请参阅 S. Raschka 2015 年的 Python Machine Learning。

我们将使用 R 编程语言来演示深度学习的应用。在整本书中，您应具备以下先决条件：

- 基本的 R 编程知识
- 对 Linux 的基本了解；我们将使用 Ubuntu (16.04) 操作系统
- 对机器学习概念的基本了解
- 对于 Windows 或 macOS，对 Docker 的基本了解

### 在 IDE 中安装 R

在开始之前，让我们先为 R 安装一个 IDE。对于 R，最流行的 IDE 是 RStudio 和 Jupyter。RStudio 专为 R 设计，而 Jupyter 则提供包括 R 在内的多语言支持。Jupyter 还提供交互式环境，允许您将代码、文本和图形合并到一个笔记本中。

### 准备工作

R 支持 Windows、macOS 和 Linux 等多种操作系统。R 的安装文件可以从 Comprehensive R Archive Network (CRAN) 的 https://cran.r-project.org/ 任意镜像站点下载。CRAN 也是 R 包的主要存储库。R 编程语言同时提供 32 位和 64 位架构版本。

### 操作步骤

1. 还强烈建议安装 r-base-dev，因为它包含许多内置函数。它还启用 `install.packages()` 命令，该命令用于通过 **R 控制台** 直接从 CRAN 编译和安装新的 R 包。默认的 **R 控制台** 如下所示：

![](img/88a9c35e3059565190fbb6413f1ca217_24_0.png)

2. 出于编程目的，建议使用集成开发环境 (IDE)，因为它有助于提高生产力。R 最流行的开源 IDE 之一是 RStudio。RStudio 还为您提供 RStudio Server，从而便于在基于 Web 的环境中进行 R 编程。RStudio IDE 的界面如下截图所示：

![](img/88a9c35e3059565190fbb6413f1ca217_25_0.png)

R 用的 RStudio 集成开发环境

### 安装 Jupyter Notebook 应用程序

如今另一款著名的编辑器是 Jupyter Notebook 应用程序。该应用程序生成的笔记本文档将文档、代码和分析整合在一起。它支持包括 R 在内的许多计算内核。它是一种服务器、客户端、基于 Web 的应用程序，可以通过浏览器访问。

### 操作步骤

Jupyter Notebook 可以按以下步骤安装：

1. 可以使用 pip 安装 Jupyter Notebook：

```
pip3 install --upgrade pip
pip3 install jupyter
```

2. 如果您已安装 Anaconda，则默认安装的计算内核是 Python。要在 Jupyter 中在同一环境下安装 R 计算内核，请在终端中输入以下命令：

```
conda install -c r r-essentials
```

3. 要在 conda 中名为 new-env 的新环境中安装 R 计算内核，请输入以下内容：

```
conda create -n new-env -c r r-essentials
```

4. 将 R 计算内核包含在 Jupyter Notebook 中的另一种方法是使用 IRkernel 包。要通过此过程进行安装，请启动 R IDE。第一步是安装 IRkernel 安装所需的依赖项：

```
chooseCRANmirror(ind=55) # choose mirror for installation
install.packages(c('repr', 'IRdisplay', 'crayon', 'pbdZMQ',
'devtools'), dependencies=TRUE)
```

5. 所有依赖项均从 CRAN 安装完成后，请从 GitHub 安装 IRkernel 包：

```
library(devtools)
library(methods)
options(repos=c(CRAN='https://cran.rstudio.com'))
devtools::install_github('IRkernel/IRkernel')
```

6. 所有要求均满足后，可以使用以下脚本在 Jupyter Notebook 中设置 R 计算内核：

```
library(IRkernel)
IRkernel::installspec(name = 'ir32', displayname = 'R 3.2')
```

7. 打开 shell/终端即可启动 Jupyter Notebook。运行以下命令在浏览器中启动 Jupyter Notebook 界面，如此代码后的截图所示：

```
jupyter notebook
```

![](img/88a9c35e3059565190fbb6413f1ca217_27_0.png)

带有 R 计算引擎的 Jupyter Notebook

### 更多内容

R 与本书中使用的大多数包一样，受大多数操作系统支持。不过，您可以使用 Docker 或 VirtualBox 设置类似于本书中使用的工作环境。

有关 Docker 安装和设置信息，请参阅 https://docs.docker.com/ 并选择适合您操作系统的 Docker 镜像。同样，VirtualBox 二进制文件可以在 https://www.virtualbox.org/wiki/Downloads 下载和安装。

## 从 R 中机器学习的基础知识入手

深度学习是机器学习的一个子类别，灵感来源于人类大脑的结构和功能。近年来，深度学习主要由于计算能力更强、数据集更大以及算法更好（具有（人工）智能学习能力和对数据驱动洞察的更强求知欲）而获得了广泛关注。在深入探讨深度学习的细节之前，让我们先了解一些机器学习的基本概念，这些概念构成了大多数分析解决方案的基础。

机器学习是一个开发算法的领域，这些算法能够从数据中挖掘自然模式，从而利用预测洞察做出更好的决策。这些洞察与一系列现实应用息息相关，从医学诊断（使用计算生物学）到实时股票交易（使用计算金融），从天气预报到自然语言处理，从预测性维护（在自动化和制造领域）到处方性建议（在电子商务和电子零售领域），等等。

以下图表阐述了机器学习的两种主要技术，即监督学习和无监督学习：

![](img/88a9c35e3059565190fbb6413f1ca217_28_0.png)

机器学习中不同技术的分类

