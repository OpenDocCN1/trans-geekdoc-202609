

如果命令无法工作或出现错误，请查看平台的文档以获取帮助。请参阅“进一步阅读”部分中的一些资源。

- 4. 确认您的 conda 环境是最新的，键入：

```
conda update conda
conda update anaconda
```

列表 B.6: 更新 conda 和 anaconda。

您可能需要安装一些包并确认更新。

- 5. 确认您的 SciPy 环境。

下面的脚本将打印机器学习开发所需的关键 SciPy 库的版本号，具体为：SciPy、NumPy、Matplotlib、Pandas、Statsmodels 和 Scikit-learn。您可以键入 python 并直接输入命令。或者，我建议打开文本编辑器并将脚本复制粘贴到编辑器中。

```
# check library version numbers
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

列表 B.7: 检查关键 Python 库是否已安装的代码。

将脚本保存为名为 versions.py 的文件。在命令行上，将目录更改为保存脚本的位置并键入：

```
python versions.py
```

列表 B.8: 从命令行运行脚本。

您应该会看到如下输出：

```
scipy: 1.3.1
numpy: 1.17.2
matplotlib: 3.1.1
pandas: 0.25.1
statsmodels: 0.10.1
sklearn: 0.21.3
```

列表 B.9: versions 脚本的示例输出。

## B.5 安装深度学习库

在此步骤中，我们将安装用于深度学习的 Python 库，具体为：Theano、TensorFlow 和 Keras。注意：我建议使用 Keras 进行深度学习，Keras 只需要安装 Theano 或 TensorFlow 中的一个即可。您不需要两者都安装。在某些 Windows 机器上安装 TensorFlow 可能会出现问题。

- 1. 通过键入以下命令安装 Theano 深度学习库：

```
conda install theano
```

列表 B.10: 使用 conda 安装 Theano。

- 2. 通过键入以下命令安装 TensorFlow 深度学习库：

```
conda install -c conda-forge tensorflow
```

列表 B.11: 使用 conda 安装 TensorFlow。

或者，您可以选择使用 pip 安装适用于您平台的特定版本的 TensorFlow。

- 3. 通过键入以下命令安装 Keras：

```
pip install keras
```

列表 B.12: 使用 pip 安装 Keras。

- 4. 确认您的深度学习环境已正确安装并正常工作。

创建一个打印每个库版本号的脚本，就像我们之前为 SciPy 环境所做的那样。

```
# check deep learning version numbers
# theano
import theano
print('theano: %s' % theano.__version__)
# tensorflow
import tensorflow
print('tensorflow: %s' % tensorflow.__version__)
# keras
import keras
print('keras: %s' % keras.__version__)
```

列表 B.13: 检查关键深度学习库是否已安装的代码。

将脚本保存到文件 deep_versions.py。通过键入以下命令运行脚本：

```
python deep_versions.py
```

列表 B.14: 从命令行运行脚本。

您应该会看到如下输出：

```
theano: 1.0.4
tensorflow: 2.0.0
keras: 2.3.0
```

列表 B.15: 深度学习版本脚本的示例输出。

## B.6 进一步阅读

本节提供了有关 Anaconda 的更多资源。

- Anaconda 主页。
  https://www.continuum.io/

- Anaconda Navigator。
  https://docs.continuum.io/anaconda/navigator.html

- conda 命令行工具。
  http://conda.pydata.org/docs/index.html

- 在 Anaconda 中安装 TensorFlow 的说明。
  https://www.tensorflow.org/get_started/os_setup#anaconda_installation

## B.7 总结

恭喜，您现在拥有一个可用于机器学习和深度学习的 Python 开发环境。您现在可以在工作站上学习和实践机器学习和深度学习。

## 附录 C

### 如何在 GPU 上设置 Amazon EC2 以进行深度学习

大型深度学习模型运行需要大量计算时间。您可以在 CPU 上运行它们，但可能需要数小时或数天才能得到结果。如果您在桌面上可以使用 GPU，可以大幅缩短深度学习模型的训练时间。在本项目中，您将了解如何通过 Amazon Web Service (AWS) 基础设施获取 GPU 访问权限，以加速深度学习模型的训练。每小时不到一美元，通常更便宜，您可以从工作站或笔记本电脑使用此服务。完成本项目后，您将了解：

- 如何创建 Amazon Web Service 账户并登录。
- 如何启动用于深度学习的服务器实例。
- 如何配置服务器实例以在 GPU 上加速深度学习。

让我们开始吧。

### C.1 概述

该过程非常简单，因为大部分工作已经为我们完成。以下是流程概述。

- 设置您的 AWS 账户。
- 启动您的服务器实例。
- 登录并运行您的代码。
- 关闭您的服务器实例。

注意，在 Amazon 上使用虚拟服务器实例需要付费。模型开发的成本较低（例如每小时不到一美元），这就是它如此有吸引力的原因，但并非免费。服务器实例运行 Linux。虽然不是必须的，但最好您了解如何在 Linux 或类 Unix 环境中导航。我们只是运行 Python 脚本，因此不需要高级技能。

注意：由于软件和库经常更新，具体版本可能会有所不同。

### C.2 设置您的 AWS 账户

您需要一个 Amazon Web Services 账户¹。

- 1. 您可以通过 Amazon Web Services 门户创建账户并点击“登录控制台”。从那里，您可以使用现有的 Amazon 账户登录或创建新账户。

![](img/443014fed0f53a293f6ece3b211c1603_641_0.png)

图 C.1: AWS 登录按钮

- 2. 您需要提供详细信息以及 Amazon 可以扣款的有效信用卡。如果您已经是 Amazon 客户并且信用卡已存档，流程会快得多。

¹https://aws.amazon.com

![](img/443014fed0f53a293f6ece3b211c1603_642_0.png)

图 C.2: AWS 登录表单

拥有账户后，您可以登录 Amazon Web Services 控制台。您将看到一系列可以访问的不同服务。

### C.3 启动您的服务器实例

既然您已有 AWS 账户，现在想要启动一个可以运行 Keras 的 EC2 虚拟服务器实例。启动实例就像选择要加载的镜像并启动虚拟服务器一样简单。幸运的是，已经有一个几乎包含我们所需一切的镜像可用，它被称为 Deep Learning AMI (Amazon Linux)，由 Amazon 创建和维护。让我们将其作为实例启动。

- 1. 如果尚未登录，请登录您的 AWS 控制台。
  https://console.aws.amazon.com/console/home

![](img/443014fed0f53a293f6ece3b211c1603_643_0.png)

图 C.3: AWS 控制台

- 2. 点击 EC2 以启动新的虚拟服务器。

- 3. 从右上角的下拉菜单中选择 US West Oregon（美国西部 - 俄勒冈）。这一点很重要，否则您将无法找到我们计划使用的镜像。

- 4. 点击 Launch Instance 按钮。

- 5. 点击 Community AMIs。AMI 是 Amazon 机器镜像。它是服务器的冻结实例，您可以选择并在新的虚拟服务器上实例化。

![](img/443014fed0f53a293f6ece3b211c1603_643_1.png)

图 C.4: Community AMIs

- 6. 在“搜索 Community AMIs”搜索框中输入 Deep Learning AMI 并按回车。

![](img/443014fed0f53a293f6ece3b211c1603_644_0.png)

图 C.5: 选择特定 AMI

- 7. 点击 Select 以选择搜索结果中的 AMI。

- 8. 现在您需要选择运行该镜像的硬件。向下滚动并选择 p3.2xlarge 硬件（我曾推荐过 g2 或 g3 实例以及 p2 实例，但 p3 实例² 更新且更快）。这包括一块 Tesla V100 GPU，我们可以使用它来显著提高模型的训练速度。它还包括 8 个 CPU 核心、61 GB 内存和 16 GB GPU 内存。注意：使用此实例每小时大约花费 3 美元。

![](img/443014fed0f53a293f6ece3b211c1603_644_1.png)

图 C.6: 选择 g2.2xlarge 硬件

- 9. 点击 Review and Launch 以完成服务器实例的配置。

- 10. 点击 Launch 按钮。

- 11. 选择您的密钥对。

如果您之前使用过 EC2 并且已有密钥对，请选择 Choose an existing key pair 并从列表中选择您的密钥对。然后勾选 I acknowledge.... 如果您没有密钥对，请选择 Create a new key pair 选项并输入密钥对名称，例如 keras-keypair。点击 Download Key Pair 按钮。

²https://aws.amazon.com/ec2/instance-types/p3/

