

要为新的用户启动 Studio 环境，请点击 Launch app 下拉菜单并选择 Studio。Studio 环境需要几分钟才能出现。一旦准备就绪，你将看到一个类似下面的屏幕：

![](img/bd21298357d8484151447cff0b2f138b_262_0.png)

现在我们已经配置了 Studio 环境，让我们设置一个 Amazon CodeCommit 仓库用于源码版本控制。

## 设置 CodeCommit

导航到 AWS CodeCommit 管理控制台，点击左窗格中的 Repositories 链接，并点击 Create repositories 开始创建 CodeCommit 仓库。为仓库提供名称并选择 Create。

现在我们已经创建了一个新仓库，让我们配置新创建的 Studio 环境使用此仓库。我们有几种方法可以设置 CodeCommit 仓库的身份验证凭据：

- IAM 用户凭据：要执行此操作，请创建一个新的 IAM 用户并为其附加 AWSCodeCommitPowerUser 策略以简化操作。将 AWS 凭据下载到本地机器，并在文件中查找 IAM 凭据。接下来，通过从下拉菜单选择 File > New > Terminal 在 Studio 中打开 Terminal。一旦新的 Terminal 窗口打开，运行 AWS Config 命令来设置 IAM 凭据。

## 动手实践——使用 AWS 服务构建数据科学环境

- Studio Notebook 执行角色：你可以将 AWSCodeCommitPowerUser 策略附加到上一会话创建的 Studio notebook 执行角色。要执行此操作，请在 Studio 控制面板中使用正在使用的 Studio 名称下的 SageMaker Execution role。然后，使用 AWS IAM 服务将策略附加到该角色。

你可以使用上述两种方法之一来配置 CodeCommit 的身份验证。完成后，你就可以克隆之前创建的 CodeCommit 仓库。要执行此操作，在 Studio UI 中选择 **Git** 下拉菜单，选择 **Clone a Repository** 选项（见下截图），并粘贴 CodeCommit 管理控制台中仓库的 HTTPS URL：

![](img/bd21298357d8484151447cff0b2f138b_263_0.png)

完成后，你应该会在文件夹视图中看到一个新的文件夹。现在我们已经创建了数据科学环境，让我们用它来进行一些实验并构建一个 ML 模型。

## 在 Jupyter Notebook 中训练 BERT 模型

在本部分的实践练习中，我们将使用 BERT transformer 训练一个金融情感分析 NLP 模型，这是我们在*第 3 章，机器学习算法*中学习过的。开始之前，双击新克隆的文件夹视图，并从文件夹中的下拉菜单选择 **File** > **New** > **Notebook** 创建一个新的 notebook 来编写代码。当提示选择内核时，选择 **Python 3 (PyTorch Python 3.6 GPU Optimized)**。你可以通过从菜单选择 **File** > **Rename Notebook** 来重命名文件，使其更有意义。

我们将使用金融新闻情感数据集进行模型训练。从 Kaggle 的 https://www.kaggle.com/ankursing/sentiment-analysis-for-financial-news 下载数据集。你需要一个 Kaggle 账户才能下载它。下载完成后，你应该将其保存为 archive.zip 文件。

接下来，将 archive.zip 文件上传到 Studio notebook。在新建 notebook 所在的相同目录下创建一个名为 data 的新文件夹，并使用 Studio UI 中的 File Upload 工具（向上箭头图标）将其上传到 data 目录，或直接将其拖入文件夹。你可以使用 Terminal 窗口中的 unzip 工具解压 ZIP 文件。请注意，Amazon Linux 环境默认不带 unzip 工具。要安装此工具，请在 Terminal 窗口中运行 yum install unzip。你会在文件夹中看到多个文件。你会看到文件夹内名为 all_data.csv 的文件。

现在，让我们为练习安装一些额外的包。在 notebook 单元格中运行以下代码块来安装 transformer 包。transformer 提供了一系列如 BERT 之类的预训练 transformers。你将使用这些 transformers 来微调 ML 任务。注意，某些代码示例是不完整的。你可以在 https://github.com/PacktPublishing/The-Machine-Learning-Solutions-Architect-Handbook/blob/main/Chapter08/bert-financial-sentiment.ipynb 找到完整的代码示例。

```
!pip install transformers
!pip install ipywidgets
```

安装 ipywidgets 后重启 notebook 的内核。接下来，将一些库导入 notebook 并设置 logger 用于日志记录目的：

```python
import logging
import os
import sys
import numpy as np
import pandas as pd
import torch
from torch.utils.data import DataLoader, TensorDataset
from transformers import AdamW, BertForSequenceClassification, BertTokenizer
from sklearn.preprocessing import OrdinalEncoder
from sklearn.model_selection import train_test_split
from types import SimpleNamespace
logger = logging.getLogger(__name__)
```

```
logger.setLevel(logging.DEBUG)
logger.addHandler(logging.StreamHandler(sys.stdout))
```

现在，我们准备好加载数据文件并处理它。以下代码块读取文件并将数据拆分为训练数据集。我们将从文件中选择前两列并将其命名为 sentiment 和 article。sentiment 是标签列，它包含三个唯一值（negative, neutral 和 positive）。由于它们是字符串值，我们将使用 scikit-library 中的 OrdinalEncoder 将它们转换为整数（0,1）。我们还需要确定 article 列的最大长度。该最大长度用于准备 transformer 的输入，因为 transformer 需要固定长度：

```python
filepath = './data/all-data-v1.csv'
data = pd.read_csv(filepath)
```

```python
ord_enc = OrdinalEncoder()
data['sentiment'] = ord_enc.fit_transform(data["sentiment"])
data = data.astype({'sentiment':int})
```

```python
train, test = train_test_split(data)
train.to_csv("./data/train.csv", index=False)
test.to_csv("./data/test.csv", index=False)
```

```python
MAX_LEN = data.article.str.len().max() # 这是句子的最大
#长度
```

现在，我们将构建一个工具函数列表以支持数据加载和模型训练。我们需要分批将数据馈给 transformer 模型。以下 get_loader() 函数根据指定的批次大小（batch size）将数据集加载到 PyTorch DataLoader 类中。注意，我们还使用 BertTokenizer 将文章编码为标记（tokens）：

```python
def get_loader(batch_size, training_dir, filename):
    logger.info("Get data loader")
    tokenizer = BertTokenizer.from_pretrained("bert-base-uncased", do_lower_case=True)
    dataset = pd.read_csv(os.path.join(training_dir, filename))
    articles = dataset.article.values
    sentiments = dataset.sentiment.values
    input_ids = []
    for sent in articles:
        encoded_articles = tokenizer.encode(sent, add_special_tokens=True)
        input_ids.append(encoded_articles)
```

接下来的 train() 函数将使用 BertForSequenceClassification 类运行训练循环。我们将使用预训练的 BERT 模型进行微调，而不是从头训练。我们将每次向 BERT 模型馈送一批数据。注意，我们还会检查服务器上是否有 GPU 设备。如果有，我们将使用 cuda 设备进行 GPU 训练，而不是使用 cpu 进行 CPU 训练。我们需要使用 .to(device) 函数将数据和 BERT 模型移动到相同的目标设备，以便训练就可以在目标设备上进行，且数据驻留在同一设备的内存中。我们在这里使用的优化器是 AdamW，它是梯度下降优化算法的一种变体。训练循环将运行指定的 epoch 次数（epochs）。一个 epoch 运行一遍整个训练数据集：

```python
def train(args):
    use_cuda = args.gpu > 0
    device = torch.device("cuda" if use_cuda else "cpu")
    # 设置生成随机数的种子
    torch.manual_seed(args.seed)
    if use_cuda:
        torch.manual_seed(args.seed)
    train_loader = get_data_loader(args.batch_size, args.data_dir, args.train_file)
    test_loader = get_data_loader(args.test_batch_size, args.data_dir, args.test_file)
    model = BertForSequenceClassification.from_pretrained(
        "bert-base-uncased",
        num_labels=args.num_labels,
        output_attentions=False,
        output_hidden_states=False,
    )
    return model
```
