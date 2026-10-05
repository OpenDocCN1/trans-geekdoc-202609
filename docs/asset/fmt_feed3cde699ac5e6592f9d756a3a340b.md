
有时，调试机器学习实验需要与计算实例进行更直接的交互。`SSH`（安全外壳）访问允许你登录计算实例，为诊断和解决无法从日志和指标立即看出的问题提供了强大的方法。这种直接访问对于理解代码运行的环境、调查资源利用情况以及进行实时调整至关重要。

一旦启用了 `SSH`，获取必要的连接详情就非常简单。导航到 `Azure ML Studio` 中的 `Compute` 选项卡，可以在那里找到你的计算目标的公共 IP 地址和端口号。这些细节是从你的本地机器建立 `SSH` 连接所所需的。有了这些信息，你可以使用任何 `SSH` 客户端连接到你的计算实例，为你提供一个命令行界面，以执行深度诊断、检查运行中的进程并直接与文件和目录进行交互。这种动手方法对于解决需要仔细检查计算环境的复杂问题是非常有价值的。

`SSH` 协议用于安全地连接到远程服务器和设备，为可能不安全的网络上的通信提供安全通道。`SSH` 依赖于公钥加密进行身份验证，确保客户端和服务器之间传输的数据经过加密且安全。这使得 `SSH` 成为管理服务器、传输文件和调试远程计算实例等任务的有用工具，特别是在 `Azure Machine Learning` 这样的环境中。

使用以下命令 `SSH` 进入你的计算实例：

```
ssh azureuser@<public-ip> -p <port-number>
```

在此命令中，`azureuser` 是为你的计算实例配置的用户名，`<public-ip>` 是你计算目标的 IP 地址，`<port-number>` 是 `SSH` 服务监听的端口。默认情况下，`SSH` 使用端口 `22`，但自定义配置可能会使用不同的端口以通过隐蔽性来增强安全性。

为了获得更安全的访问，强烈建议设置 `SSH` 公钥/私钥密钥对。这涉及在你的本地机器上生成密钥对，然后将公钥放置在计算实例上。这种设置确保只有拥有相应私钥的人才能身份验证并访问实例。以下是设置 `SSH` 密钥对的基本步骤概述：

1. 在你的本地机器上生成 `SSH` 密钥对：

   ```
   ssh-keygen -t rsa -b 4096 -C your_email@example.com
   ```

   此命令创建一个具有 4096 位加密的新 RSA 密钥对，你可以按照提示将密钥保存到安全位置，并可选地添加密码短以增加额外安全性。

2. 将公钥复制到你的 `Azure ML` 计算实例：

   ```
   ssh-copy-id azureuser@<public-ip> -p <port-number>
   ```

3. 或者，你可以手动将公钥添加到远程实例上的 `~/.ssh/authorized_keys` 文件中。

在更复杂的网络环境（例如具有多层安全的环境）中工作时通常会使用跳板机（堡垒机）。跳板机作为你的本地机器和目标计算实例之间的中介。这意味着你首先 `SSH` 进入跳板机，然后从跳板机连接到目标实例。例如：

```
ssh -J jumpuser@<jump-server-ip> azureuser@<compute-public-ip>
```

### 为作业配置环境

在 `Azure Machine Learning` 中，配置和提交作业涉及设置环境和参数。以下是关于配置 `environment` 的摘要：

1. **创建实验**：`Azure Machine Learning` 中的 `experiment` 是组织训练运行的逻辑容器。

2. **选择计算目标**：`compute target` 指定了训练发生的地方。它可以是你的本地机器或 `Compute Cluster`（计算集群）。

3. **创建环境**：`environment` 定义了软件设置。你可以使用预构建的环境或创建自己的环境。环境完整列表可以在 [`ml.azure.com/registries/azureml/environment`](https://ml.azure.com/registries/azureml/environment) 找到。

当你创建一个 `ScriptRunConfig` 时，该配置指定了计算目标、环境、源目录和运行的脚本。

```
from azureml.core import Environment
myenv = Environment.get(workspace=ws, name="AzureML-Minimal")
```

你还可以使用 `arguments` 参数向你的训练脚本传递额外的参数。

```
from azureml.core import ScriptRunConfig
src = ScriptRunConfig(source_directory=project_folder,
 script='train.py',
 compute_target=my_compute_target,
 environment=myenv)
```

4. **提交实验**：使用 `experiment` 对象的 `submit` 方法来提交训练作业。你可以监控作业的进度，并在作业完成后查看输出。

```
run = experiment.submit(config=src)
run.wait_for_completion(show_output=True)
```

请确保你的训练脚本和任何必要的包在脚本运行的环境中都是可用的。如果在本地运行，你负责配置带有所有所需依赖项的 Python 环境。如果使用远程计算目标，你可以在 `Azure Machine Learning` 环境中指定依赖项。

### 为作业定义参数

在 `Azure Machine Learning` 中，`job` 是训练脚本或流水线的单次执行，通常与训练机器学习模型相关。作业用于自动化和扩展机器学习任务，例如模型训练、超参数调优和模型评估。

为了在 `Azure Machine Learning` 中提交训练作业，你需要设置环境、指定参数并创建一个 `ScriptRunConfig` 对象。假设你正在训练一个机器学习模型来分类图像。你有一个训练脚本 `train.py`，它接受关于学习率和轮数（epochs）的命令行参数：

```python
from azureml.core import ScriptRunConfig

# Define script parameters
script_params = {
   '--learning-rate': 0.01,
   '--epochs': 10
}

# Create a ScriptRunConfig
src = ScriptRunConfig(source_directory='.',
script='train.py',
 arguments=[f'{k} {v}' for k, v in script_params.items()],
 compute_target=compute_target,
environment=env)

#Submit the experiment:
run = experiment.submit(config=src)
run.wait_for_completion(show_output=True)
```

在这种场景下，训练作业被配置为在选定的计算目标上使用定义的环境运行 `train.py` 脚本，并指定的学习率和 `epochs`。通过提交此作业，`Azure Machine Learning` 将使用提供的参数执行脚本，你可以通过查看在本章之前介绍过的作业运行日志，在 `Azure ML Studio` 中监控训练运行的进度和结果。

在开发机器学习模型的过程中，第一步之一是探索和理解你正在处理的数据。`Skill 2.1` 专注于使用 `Azure Machine Learning` 数据资产和数据存储进行数据探索。对于需要访问、整理和为模型训练准备数据的数据科学家和分析师来说，这项技能至关重要。通过掌握这些技术，你将为构建准确高效的机器学习模型建立坚实的基础。

### Skill 3.2：实现训练流水线

在 `Azure Machine Learning` 中实现训练流水线是构建稳健、可扩展且可重复机器学习工作流的关键技能。流水线允许你自动化并调度机器学习过程的不同阶段，从数据准备、训练到验证和部署。通过将工作流结构化为离散的可管理的步骤，你可以增强协作、提高效率，并确保跨项目的一致性。这种结构化方法不仅简化了复杂的工作流，还使它们更容易调试和维护。

在脚本中配置作业运行设置是配置训练流水线的重要过程。这涉及为流水线的每个步骤指定计算资源、环境依赖项和运行时参数。适当的配置可确保流水线的每个组件都能正确且高效地执行，并利用适当的资源和设置。此外，有效设置作业运行设置可以帮助你通过为不同任务选择正确的计算目标来管理成本并优化性能。

在 `Azure ML` 中创建和管理流水线还涉及几项核心任务。这些包括创建流水线本身、在不同步骤之间传递数据，以及运行或调度流水线以在指定时间执行。此外，你可能需要创建自定义组件来处理工作流中的独特任务。使用基于组件的流水线可以进一步模块化并简化你的流程，使得在不破坏整个流水线的情况下，更容易管理和更新单个组件。通过掌握这些技能，你可以构建出灵活且强大的机器学习流水线，支持持续集成和部署，从而提高机器学习项目的整体生产力和可扩展性。

#### 创建流水线

我们能够使用一种名为 `job`（作业）的抽象来创建运行。`job` 用于执行任务，如集成 `MLflow`、设置实验跟踪以及调试和记录运行。你可能会问，为什么还需要另一种抽象——`pipeline`（流水线）。在本章的后面，我们将探索通过 UI 作为一种视觉化创建流水线的方法。那么，什么是流水线？它与 `job` 有何区别？为什么需要它们？

`Azure Machine Learning` 流水线与 `jobs` 的区别在于流水线代表一个完整的工作流，而 `jobs` 是单个任务。事实上，`- a machine into,,,,,,,,,,,,,,,,,,,,,,,.,..........................00000000 an an0 of of a a...

  -44 in the designer](graphics/03fig04.jpg)

**图 3-4** 在在**

考虑到这一点，我们如何与流水线一起工作？

##### 引入用于创建流水线的 YAML

`YAML`（YAML 语言标记语言）是一种人类可读的数据序列化格式，通常用于配置文件以及存储或传输数据的应用程序中。在 `Azure Machine Learning` 的上下文中，YAML 文件被用于定义机器学习流水线和组件的结构。

自定义组件允许你通过包含专门的任务来扩展流水线的功能。这些组件可以涵盖从定制的数据处理步骤到独特的训练算法。通过集成自定义组件，你可以构建出更灵活、更强大的流水线，以满足你数据科学项目的独特需求。

当我们构建自定义组件时（例如，在随后的章节中，你将看到如何构建自定义流水线组件），你的组件应该包含一个定义其元数据、接口和执行细节的 YAML 文件，以及一个包含执行逻辑的 Python 文件（或其他代码文件）——例如用于训练组件的 `train.yml` 和包含训练代码的 `train.py` 文件。

流水线 YAML 文件（`pipeline.yml`）通过将机器学习任务拆分为多个步骤（每个步骤由一个组件表示）来指定工作流。该文件包含：

* `Type`：指定作业是一个流水线。

* `Display Name`：流水线的易可读名称。

* `Description`：流水线的简要描述。

* `Jobs`：作为流水线内步骤运行的单个作业的字典。每个作业都是组件的引用，并包含其输入和输出。

* `Settings`：流水线的配置设置，例如默认计算目标。

现在我们已经定义了 YAML 格式（它与 `JSON`，实际上它是 `JSON` 的超集），我们可以查看一个用 YAML 编写的示例流水线：

```yaml
$schema: https://azuremlschemas.azureedge.net/latest/pipelineJob.schema.json
type: pipeline
display_name: Training Pipeline
description: A pipeline for training a machine learning model.

settings:
  default_compute: azureml:cpu-cluster

jobs:
  data_preprocessing:
    type: command
    component: ./components/data_preprocessing.yml
    inputs:
      raw_data: ./data/raw_data.csv

  model_training:
    type: command
    component: ./components/model_training.yml
    inputs:
      processed_data: ${{parent.jobs.data_preprocessing.outputs.processed_data}}

  model_evaluation:
    type: command
    component: ./components/model_evaluation.yml
    inputs:
      trained_model: ${{parent.jobs.model_training.outputs.trained_model}}
```

YAML 文件中引用的每个组件（例如 `./components/model_training.yml`）定义了该作业特定的命令和配置。这些组件文件链接到执行所需任务的 Python 脚本。以下是如何构建组件 YAML 文件并将其链接到 Python 脚本的方法。

虽然 YAML 是 `Azure Machine Learning` 中定义流水线的流行选择，但也有其他替代方案：

* **Python SDK**：可以使用 `Azure Machine Learning` Python SDK 以编程的方式定义和运行流水线。这种方法提供了更高的灵活性，适用于复杂场景。

* **Azure Machine Learning Designer**：一种无需编写代码即可创建流水线的拖拽界面。它对用户友好，但可能无法像 YAML 或 Python SDK 那样提供同样的定制。

考虑这样一个场景：你正在为销售预测模型构建训练流水线。该流水线包含三个主要步骤：数据预处理、模型训练和模型评估（参见表 3-4）。

**表 3-4** 流水线步骤和组件

| 步骤 | 说明 |
| --- | --- |
| 数据预处理 | 清洗并转换原始销售数据以适用于训练的格式。此步骤在单独的 YAML 文件中定义为独立的组件。 |
| 模型训练 | 使用处理后的数据训练回归模型。此步骤在单独的 YAML 文件中定义为独立的组件。 |
| 模型评估 | 在验证数据集上评估已训练模型的性能。此步骤在单独的 YAML 文件中定义为独立的组件。 |
| 流水线 YAML 文件 | 编排这些组件，指定执行顺序以及它们之间的数据流。 |

之前提供的 YAML 流水线定义了一个包含三个主要步骤的机器学习流水线：数据预处理、模型训练和模型评估。让我们拆解 YAML 文件的每个部分以理解其组件：

* `$schema`：指定用于验证的架构 URL，确保 YAML 文件符合 `Azure Machine Learning` 流水线的正确格式。

* `$type`：指示此 YAML 文件定义了一个流水线作业。这很重要，因为当你提交 YAML 文件时，`Azure Machine Learning` 会识别它定义了一个流水线，并根据你的规范构建训练流水线。

* `Jobs`：定义流水线的步骤（或作业），每个作业代表流水线的一个组件。作业可以拥有以下额外选项，包括输出名称和组件文件：

  * `Name`：第一个作业的名称，负责数据预处理。

  * `Type`：指定作业类型，在此情况下为命令作业（command job）。

  * `Inputs`：例如，`raw_data` 是指向原始数据文件的输入。

  * `Outputs`：指定此作业生成的输出文件或数据集。这些输出对于将数据传递给后续流水线步骤至关重要，并在子级定义。

  * `Component`：引用包含实现的特定组件。流水线可能会变得复杂，但使用 YAML 这样的标准格式允许你处理各种步骤和配置。在下一节中我们将我们将如何运行。

##### 使用 Azure CLI 运行流水线

通过 YAML 定义流水线提供了灵活性和控制。一旦在 YAML 中定义了流水线，可以使用 Azure 命令行界面（CLI）执行它。命令 `az ml job create --file pipeline.yml` 将流水线作业提交到你的 `Azure Machine Learning` 工作区。这允许你管理工作流。该命令指示 `Azure ML` 解析 YAML 文件并按定义启动流水线。

提交流水线作业后，监控其进度对于确保每个步骤按预期执行至关重要。`Azure Machine Learning Studio` 提供了一个用户界面，你可以在其中跟踪流水线的状态、查看日志并调试任何问题。此外，你可以使用额外的 CLI 命令查询状态、检索日志并远程管理作业。这种图形和命令行监控的双重能力确保你对流水线有全面的概述和控制，从而实现机器学习工作流的高效管理和故障排除。

```
az ml job create --file pipeline.yml
```

#### 在流水线步骤之间传递数据
