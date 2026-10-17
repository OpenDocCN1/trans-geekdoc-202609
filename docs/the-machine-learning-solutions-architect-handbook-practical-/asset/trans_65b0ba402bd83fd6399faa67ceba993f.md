

数据科学家的主要 SageMaker 用户界面是 SageMaker Studio，这是一个数据科学 `integrated development environment` (`IDE`)。它提供核心功能，例如用于运行实验的托管笔记本，以及从单个用户界面访问不同后端服务（如数据整理、模型训练和模型托管服务）。它是数据科学家与 SageMaker 大部分功能交互的主要界面。它还提供一个 Python SDK，用于从 Python 笔记本或脚本以编程方式与其后端服务进行交互。下图显示了 SageMaker Studio 的关键组件：

![](OEBPS/Images/B20836_08_03.png)

图 8.3：SageMaker Studio 架构

SageMaker Studio 实现了域的概念，以隔离用户环境。域代表一组用户配置文件，每个配置文件都配备了特定的配置，例如运行 Jupyter 笔记本时使用的 AWS IAM 角色、标签以及对 SageMaker Canvas 的访问权限。在每个域中，Studio 用户可以通过用户配置文件访问不同的 Studio 应用程序，例如 JupyterLab、Code Editor 或 Canvas。

要运行某些 Studio 应用程序（例如 JupyterLab 和 Code Editor），您需要创建 SageMaker Studio 空间。SageMaker Studio 空间用于管理这些应用程序的存储和资源需求。每个空间与应用程序的一个实例具有 1:1 关系，并由存储卷、应用程序类型以及应用程序基于的镜像等资源组成。空间可以是私有的，也可以是共享的。

要开始使用 SageMaker，初始步骤是将用户加入 SageMaker Studio。加入流程从创建 SageMaker 域开始（如果域不存在）。对于单用户场景，SageMaker 提供快速域设置选项。使用快速设置选项，SageMaker 会使用默认设置自动配置新域，以便快速设置。对于高级多用户场景，SageMaker 提供高级域设置选项。使用高级设置，您可以为企业采用配置域的各个方面，例如身份验证方法、对不同服务的访问、网络配置和数据加密密钥。随后，在域中创建用户配置文件，并向用户授予对这些配置文件的访问权限。设置用户配置文件后，用户可以通过在域中选择其各自的用户配置文件来启动 Studio 环境。这样，他们就可以开始在 SageMaker Studio 中工作。

## 启动 Studio 应用程序

Studio 内有多个应用程序可用，包括 JupyterLab、RStudio、Canvas 和 Code Editor。您还可以选择启动之前的 Studio Classic 体验。

在 SageMaker Studio 环境中，启动 Jupyter 笔记本是一个简单的过程。首先选择 JupyterLab 应用程序，然后创建 JupyterLab 空间。空间作为一个命名的、自包含的且持久的存储容器，可以附加到 JupyterLab 应用程序。在空间创建期间，您可以灵活选择 JupyterLab 的服务器实例类型和 Docker 镜像。空间成功创建后，您可以继续启动 JupyterLab 应用程序并在其中启动笔记本。JupyterLab 笔记本现在具有一个 AI 驱动的编程助手（Jupyternaut）功能，您可以使用它来提出编程问题。例如，您可以提出诸如“如何导入 Python 库？”或“如何使用 SageMaker 训练模型？”之类的问题。

同样，启动 Canvas 应用程序涉及在 SageMaker Studio 环境中选择它。作为一种无代码 ML 工具，Canvas 提供数据准备、模型训练、推理和工作流自动化等功能。虽然主要面向数据科学和 ML 背景有限的数据分析师设计，但它也对希望为多样化数据集快速建立基线模型的经验丰富的数据科学家很有价值。用户可以利用 Canvas 的现成模型进行预测，无需构建模型，也可以选择创建针对特定业务问题定制的自定义模型。现成模型涵盖语言检测和文档分析等各种用例。对于自定义模型，Canvas 支持使用表格数据和图像数据构建多种模型类型，以进行个性化预测。

支持导入数据，无论来自本地还是外部来源（如 S3、Amazon Redshift 或 Databricks）。此外，Canvas 通过 Data Wrangler 促进数据准备，并提供生成式 AI 基础模型以启动对话式聊天。

Code Editor 基于 Code-OSS 和 Visual Studio Code Open Source 构建，用于编写、测试、调试和运行分析和 ML 代码。要启动 Code Editor，只需在 Studio 中选择该应用程序并创建一个专用的私有空间。该空间在单个 `Amazon Elastic Compute Cloud` (`Amazon EC2`) 实例上运行以进行计算，并在相应的 `Amazon Elastic Block Store` (`Amazon EBS`) 卷上进行存储。空间内的所有元素，包括代码、Git 配置文件和环境变量，都存储在这个统一的 Amazon EBS 卷上。

## 准备数据

为模型训练准备和处理数据是 ML 生命周期中优化模型性能的关键步骤。要在 Studio 环境中执行此操作，您可以直接在 Studio 笔记本中安装和使用您首选的库包。SageMaker 还提供多种数据整理和处理服务，以协助数据准备，包括 SageMaker Data Wrangler，以及与 Amazon EMR 和 Glue 集成的数据准备，用于大规模数据准备和处理。

## 使用 SageMaker Data Wrangler 交互式准备数据

SageMaker Data Wrangler 是一项完全托管的服务，可帮助数据科学家和工程师为 ML 准备和分析数据。通过图形用户界面，它便于执行数据准备任务，例如数据清洗、特征工程、特征选择和可视化。

要使用 Data Wrangler，您需要构建一个数据流，这是一个连接数据集、转换和分析的管道。当您创建并运行数据流时，Data Wrangler 会启动一个 EC2 实例来运行转换和分析。每个数据流都与一个 EC2 实例相关联。数据流通常从数据导入步骤开始。Data Wrangler 允许您从多个数据源导入数据，包括 Amazon S3、Athena、Amazon Redshift、Amazon EMR、Databricks、Snowflake，以及 `Software-as-a-Service` (`SaaS`) 平台，例如 Datadog、GitHub 和 Stripe。

数据导入后，您可以使用 Data Wrangler 清洗和探索数据，并使用内置转换执行特征工程。您还可以使用预配置的可视化模板来了解数据并检测异常值。

您可以使用内置报告评估数据质量。下图显示了 Data Wrangler 的流程和架构：

![](OEBPS/Images/B20836_08_04.png)

图 8.4：SageMaker Data Wrangler 架构

使用 Data Wrangler 时，第一步是从各种数据源导入示例数据以执行数据处理和转换。完成必要的转换步骤后，您可以选择导出配方。然后，SageMaker Processing 可以执行此配方，根据定义的转换处理整个数据集。

此外，您还可以选择将转换步骤导出为笔记本文件。此笔记本文件可用于启动 SageMaker Processing 作业，从而对数据进行处理和转换。生成的输出可以定向到 SageMaker Feature Store，或存储在 Amazon S3 中以供进一步使用和分析。

## 交互式大规模准备数据

