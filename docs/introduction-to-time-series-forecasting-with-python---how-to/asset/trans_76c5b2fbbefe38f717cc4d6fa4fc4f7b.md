
- 用于估计模型在未见数据上表现的重新采样方法，特别是 `TimeSeriesSplit` 类（在第 16 章中介绍）。

有关 scikit-learn 的更多信息，请参见：

- Scikit-learn 主页：`http://scikit-learn.org/`

## 1.3 Python 生态系统安装

本节将为您提供有关设置用于时间序列预测的 Python 环境的通用建议。我们将涵盖：

1.  使用 Anaconda 进行自动安装。
2.  使用您平台的包管理工具进行手动安装。
3.  确认已安装的环境。

如果您已经拥有一个可正常运行的 Python 环境，请跳到确认步骤以检查您的软件库是否已更新。让我们开始吧。

### 1.3.1 自动安装

如果您不擅长在机器上安装软件，或者您使用的是 Microsoft Windows，那么有一个简单的选项适合您。有一个名为 Anaconda Python 的发行版，您可以免费下载并安装。它支持三大主要平台：Microsoft Windows、Mac OS X 和 Linux。它包含 Python、SciPy 和 scikit-learn：您学习、练习和使用 Python 环境进行时间序列预测所需的一切。

您可以从这里开始使用 Anaconda Python：

- Anaconda 安装：`https://docs.continuum.io/anaconda/install`

### 1.3.2 手动安装

有多种方法可以安装特定于您平台的 Python 生态系统。在本节中，我们介绍如何安装用于时间序列预测的 Python 生态系统。

#### 如何安装 Python

第一步是安装 Python。我更喜欢使用并推荐 Python 2.7 或 Python 3.5。Python 的安装将特定于您的平台。有关说明，请参见：

- 在 Python 初学者指南中下载 Python：`https://wiki.python.org/moin/BeginnersGuide/Download`

在带有 `macports` 的 Mac OS X 上，您可以输入：

```text
sudo port install python35
sudo port select --set python python35
sudo port select --set python3 python35
```

列表 1.1：macports 在 Mac OS X 上安装 Python 3 的命令。

#### 如何安装 SciPy

安装 SciPy 的方法有很多种。例如，两种流行的方法是使用您平台上的包管理工具（如 RedHat 上的 dnf 或 OS X 上的 macports），或者使用 Python 包管理工具，如 pip。SciPy 文档非常出色，并在官方 SciPy 主页上涵盖了在许多不同平台上的操作说明：

- 安装 SciPy 软件栈：[https://www.scipy.org/install.html](https://www.scipy.org/install.html)

安装 SciPy 时，请确保您至少安装了以下软件包：

- SciPy
- NumPy
- Matplotlib
- Pandas
- Statmodels

在带有 **macports** 的 Mac OS X 上，您可以输入：

```text
sudo port install py35-numpy py35-scipy py35-matplotlib py35-pandas py35-statmodels
py35-pip
sudo port select --set pip pip35
```

列表 1.2：macports 在 Mac OS X 上安装 Python 3 SciPy 库的命令。

在带有 **dnf** 的 Fedora Linux 上，您可以输入：

```text
sudo dnf install python3-numpy python3-scipy python3-pandas python3-matplotlib
python3-statmodels
```

列表 1.3：dnf 在 Fedora Linux 上安装 Python 3 SciPy 库的命令。

#### 如何安装 scikit-learn

scikit-learn 库必须单独安装。我建议安装 scikit-learn 时使用与安装 SciPy 相同的方法。有关安装 scikit-learn 的说明仅限于使用 Python **pip** 包管理器。在所有支持 **pip** 的平台（Windows、OS X 和 Linux）上，我通过输入以下内容来安装 scikit-learn：

```text
sudo pip install -U scikit-learn
```

列表 1.4：pip 安装 scikit-learn 的命令。

### 1.3.3 确认您的环境

一旦您设置好环境，您必须确认其按预期工作。让我们首先检查 Python 是否安装成功。打开命令行并输入：

```
python -V
```

列表 1.5：检查 Python 版本的命令行参数。

您应该看到如下响应：

```
Python 2.7.12
```

列表 1.6：Python 2 的示例 Python 版本。

或

```
Python 3.5.3
```

列表 1.7：Python 3 的示例 Python 版本。

现在，确认库是否安装成功。创建一个名为 *versions.py* 的新文件，并将以下代码片段复制粘贴到其中，然后将文件保存为 *versions.py*。

```python
# 检查关键 Python 库的版本
# scipy
import scipy
print('scipy: %s' % scipy.__version__)
# numpy
import numpy
print('numpy: %s' % numpy.__version__)
# matplotlib
import matplotlib
print('matplotlib: %s' % matplotlib.__version__)
# pandas
import pandas
print('pandas: %s' % pandas.__version__)
# statsmodels
import statsmodels
print('statsmodels: %s' % statsmodels.__version__)
# scikit-learn
import sklearn
print('sklearn: %s' % sklearn.__version__)
```

列表 1.8：检查所需 Python 库版本的脚本。

在命令行或您喜欢的 Python 编辑器中运行该文件。例如，输入：

```
python versions.py
```

列表 1.9：运行 versions.py 脚本的命令行参数示例。

这将打印出您所需的每个关键库的版本。例如，在我撰写本文时的系统中，我得到了以下结果：

```
scipy: 1.3.1
numpy: 1.17.2
matplotlib: 3.1.1
pandas: 0.25.1
statsmodels: 0.10.1
sklearn: 0.21.3
```

列表 1.10：运行 versions.py 脚本的示例输出。

如果您遇到错误，请现在停止并修复它。您可能需要查阅特定于您平台的文档。

### 1.4 总结

在本课中，您了解了用于时间序列预测的 Python 生态系统。您学习了：

- Pandas、Statsmodels 和 scikit-learn，它们是用于时间序列预测的顶级 Python 库。
- 如何自动和手动设置 Python SciPy 环境以用于开发。
- 如何确认您的环境已正确安装，并且您已经准备好开始开发模型。
- 您还学习了如何在工作站上安装用于机器学习的 Python 生态系统。

#### 1.4.1 下一步

在下一课中，您将了解时间序列数据集以及讨论时间序列问题时使用的标准术语。

# 第 2 章

## 什么是时间序列预测？

时间序列预测是机器学习中一个重要的领域，通常被忽视。它之所以重要，是因为有许多预测问题涉及时间要素。这些问题被忽视，是因为正是这个时间要素使得时间序列问题更难以处理。在本课中，您将了解时间序列预测。读完本课后，您将知道：

- 时间序列、时间序列分析和时间序列预测的标准定义。
- 时间序列数据中需要考虑的重要组件。
- 时间序列的示例，以使您的理解具体化。

让我们开始吧。

### 2.1 时间序列

普通的机器学习数据集是观察值的集合。例如：

```
观察值 #1
观察值 #2
观察值 #3
```

列表 2.1：观察值集合的示例。

时间在普通的机器学习数据集中确实扮演着一个角色。预测是针对新数据做出的，而实际结果可能直到未来某个日期才可知。我们在预测未来，但所有先前的观察值都被同等对待。也许带有一些非常轻微的时间动态来克服*概念漂移*的想法，例如仅使用最后一年的观察值而不是所有可用数据。

时间序列数据集是不同的。时间序列在观察值之间添加了显式的顺序依赖关系：一个时间维度。这个额外的维度既是一个约束，也是一个结构，提供了额外信息的来源。

时间序列是按时间顺序依次获取的观察值序列。

> — 出自 *Time Series Analysis: Forecasting and Control*（时间序列分析：预测与控制）第 1 页。

