

![image](d2d_images/image002.png)

––––––––

![image](d2d_images/scene_break.png)

![image](d2d_images/image074.png)

![image](d2d_images/image060.png)

图 5.4 机器学习算法比较

![image](d2d_images/image071.png)![image](d2d_images/image051.png)之前的工作现在可以用于进行预测。我们将选择 `NB` 算法进行预测，因为它是两个最佳算法之一。我们将在验证集上应用 `NB` 算法以检查其准确性。建议设置验证集，以检查训练集是否出现过拟合或滑拟合情况。当运行以下代码中的 `NB` 算法时，将打印出准确率得分、混淆矩阵和分类报告，以指示验证结果。

预测输出如下：

![image](d2d_images/image086.png)

可以看出准确率为 0.928。混淆矩阵显示有三个错误，最后分类报告按精确率、召回率、F1 分数和支持度显示了每个类别的细分情况。

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 附录 A：平台和软件包安装

![image](d2d_images/chapter_title_below.png)

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# A.1 平台安装

![image](d2d_images/chapter_title_below.png)

Python 是一种用于通用编程的解释型高级编程语言。其应用现已无法枚举。例如，它被用于 Web 和互联网开发、数据库访问、GUI、科学与数值计算、教育、网络编程、软件与游戏开发。

有多个平台可用于开始使用 Python 进行编程。它还支持不同的操作系统。Python 常见平台的最新版本可通过以下链接访问：

[https://www.python.org/downloads/](https://www.python.org/downloads/)

您还可以选择适合您使用的操作系统的平台，无论是 Windows、Linux/UNIX、Mac OS X 还是其他系统。

下载安装文件后，您可以运行它，为了继续进行软件包安装的后续步骤，重要的是要确保勾选“将 Python X.XX 添加到路径”复选框，如下图所示：

![image](d2d_images/image101.png)

然后，您可以进行常规安装过程。

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# A.2 软件包安装

![image](d2d_images/chapter_title_below.png)

为了能够追踪本书中所示的示例，您需要安装一些软件包。但首先，需要执行一些检查步骤，如下所示：

1- 运行 Windows 系统自带的 `cmd` 控制台。这可以通过单击“Windows 键 + R”轻松完成，然后在出现的小窗口中输入：`cmd` 并按 Enter。

2- 我们要检查系统是否识别已安装的 Python 平台。因此，在 `cmd` 黑色窗口中输入：

![image](d2d_images/image078.png)

3- 现在我们需要确保您有 `pip` 可用。这可以通过运行以下命令完成：

![image](d2d_images/image114.png)

4- 确保您拥有 `setuptools` 和 `wheel` 项目的最新版本很有用。这使您能够从源存档安装：

![image](d2d_images/image037.png)

在之前的步骤期间和之后，预计您将看到以下 `cmd` 屏幕：

![image](d2d_images/image066.png)

现在，我们可以继续安装必要的软件包，以便为本书中的示例准备好 Python。我们需要的主要软件包是 Pandas。但是，为了使其正常工作，有一些依赖项需要先安装：

✓ `setuptools`: 24.2.0 或更高版本

✓ `NumPy`: 1.9.0 或更高版本

✓ `python-dateutil`: 2.5.0 或更高版本

✓ `pytz`

✓ `scipy`

✓ `scikit-learn`

✓ `Matplotlib`

我们已经检查了第一个 `setuptools`。因此，我们可以继续处理下一个软件包。您需要依次输入以下命令，并等待每个软件包安装完成。

![image](d2d_images/image121.png)

您必须检查是否有互联网连接，因为如果没有连接，所有之前的安装都无法工作。如果安装成功，您预计将看到类似以下截图的 `cmd` 屏幕：

![image](d2d_images/image062.png)

![image](d2d_images/image038.png)

![image](d2d_images/image030.png)

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# 附录 B. 资源、期刊和免费数据集

![image](d2d_images/chapter_title_below.png)

随着存储变得几乎无限，连接变得更加便捷和无缝，互联网上可用的数据集变得巨大。加上机器强大的计算能力，这使得在广泛的可用数据集上应用机器学习算法成为可能。曾经有一种观点认为，为了跨越通往人工智能的道路，科学家必须创造一种新的思维方式或神秘模式。然而，考虑到机器学习算法在不同领域取得的成功，问题更简单。我们需要大量的示例数据集，以便机器能够学习。当然，我们还需要在计算能力方面拥有强大的机器，以便将算法应用于如此大量的数据。

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# B.1 会议和期刊

![image](d2d_images/chapter_title_below.png)

有几种研究资源对有兴趣进行高级学习和研究工作的人很有用。大量参考文献分布在不同领域的期刊和会议中。重要期刊示例包括：

\- 机器学习研究杂志。

\- IEEE 神经网络汇刊

\- 神经计算。

\- 统计期刊。

\- 统计年鉴。

\- 机器智能。

\- 模式识别。

\- IEEE 知识与数据工程汇刊。

\- 数据挖掘与知识发现。

\- 数据挖掘探索。

著名的机器学习会议包括：

\- 神经信息处理系统 (NIPS)。

\- 人工智能中的不确定性。

\- 国际机器学习会议 (ICML)。

\- 欧洲机器学习会议 (ECML)。

\- 国际人工智能联合会议 (IJCAI)。

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |

| --- | --- | --- |

![image](d2d_images/chapter_title_above.png)

# B.2 免费数据集

![image](d2d_images/chapter_title_below.png)

互联网上有多个免费可用的数据集。这些数据集可供数据科学家和数据研究人员用于测试和训练他们的算法。一些非常有用的链接如下：

\- UCI 机器学习库是最流行的库：

[http://www.ics.uci.edu](http://www.ics.uci.edu)/∼mlearn/MLRepository.html

或：[http://mlr.cs.umass.edu/ml/index.html](http://mlr.cs.umass.edu/ml/index.html)

