

# Vertex AI Workbench

借助 Vertex AI Workbench，用户可以在单一开发环境中完成完整的数据科学流程。用户可以利用 Vertex AI Workbench 提供的基于笔记本的环境来执行诸如查询和探索数据、开发和训练模型，以及将代码作为流水线的一部分运行等任务。Vertex AI Workbench 提供托管笔记本和用户管理的笔记本。

在 Vertex AI Workbench 的托管笔记本选项的帮助下，用户可以构建一个端到端的基于笔记本的生产环境，该选项为了方便用户内置了多种集成。对于需要完全掌控其工作环境的用户，Vertex AI Workbench 中提供了用户管理的笔记本选项。

这两种可用的笔记本替代方案均预配置了 `JupyterLab`，并拥有一整套深度学习软件包，包括对 `TensorFlow` 和 `PyTorch` 框架的支持。用户可以选择使用配备 CPU 或 GPU 的实例。Vertex AI Workbench 提供的笔记本实例现已与 `GitHub` 交互，允许用户将笔记本与托管在 `GitHub` 上的代码库同步。

如果用户想要使用笔记本进行数据探索、分析或建模，或者想要将笔记本作为端到端数据科学流程的一部分，托管笔记本通常是一个值得考虑的绝佳选项。用户可以使用托管笔记本实例执行面向工作流的操作，而无需离开 `JupyterLab` 界面。此外，它们还提供了各种连接器和工具，用于实现数据科学流程的自动化。

当用户创建用户管理的笔记本实例时，系统会提示用户对将要使用的虚拟机 (VM) 进行一些选择。例如，当用户创建用户管理的笔记本实例时，系统会提示用户选择机器类型和将要使用的框架。用户可以在实例创建后更改其机器类型；但这样做需要重启实例。用户可以在正在使用的用户管理的笔记本实例上进行手动更改，例如更改软件和软件包版本。更改实例上使用的框架是一个需要额外工作量的过程。

## Vertex AI Workbench 的创建与使用

请按照以下步骤创建 Vertex AI Workbench：

### 步骤 1：Vertex AI 的登录页面

如 [图 4.1](#ch04.xhtml#fig4-1) 所示，Workbench 将列在 Vertex AI 的登录页面中：

![](images/Figure_4.1.png)

**图 4.1：** GCP Vertex AI 的登录页面

1. 点击 **Workbench**。

### 步骤 2：Workbench 的登录页面

Workbench 的登录页面如 [图 4.2](#ch04.xhtml#fig4-2) 所示：

![](images/Figure_4.2.png)

**图 4.2：** Vertex AI Workbench 的登录页面

1. 点击 **ENABLE NOTEBOOKS API**（每个项目只需启用一次笔记本 API。笔记本 API 也可以从 GCP 的 API 和服务中启用）。
2. 创建 **Managed Notebooks**（托管笔记本）的选项。
3. 创建 **User-Managed Notebooks**（用户管理的笔记本）的选项，点击它（我们将在大多数练习中使用用户管理的笔记本）。
4. 创建 **New Instance**（新实例）的选项。

### 步骤 3：新笔记本选择

用户将获得创建实例的选项，如 [图 4.3](#ch04.xhtml#fig4-3) 所示：

![](images/Figure_4.3.png)

**图 4.3：** 新笔记本选择（用户管理）

1. 点击 **NEW NOTEBOOK**。
2. 选择 **Tensorflow Enterprise**。
3. 选择 **Tensorflow Enterprise 2.6**（我们将使用 TensorFlow 2.6 开发模型）。
4. 选择 **Without GPUs**（无 GPU）。

### 步骤 4：TensorFlow 笔记本创建

选择 TensorFlow 后，将显示新建笔记本弹出窗口，如 [图 4.4](#ch04.xhtml#fig4-4) 所示：

![](images/Figure_4.4.png)

**图 4.4：** 笔记本创建

1. 提供 **Notebook Name**（笔记本名称）。
2. 选择 **US-central** 作为 Region（区域）。
3. 选择 **us-central1-a** 作为 Zone（可用区）。
4. **ADVANCED OPTIONS**（高级选项）为用户提供选择机器类型、磁盘大小以及网络选项的选择（在我们的示例中可以忽略）。
5. 点击 **CREATE**（创建）。

### 步骤 5：笔记本创建完成

完成笔记本和 `Jupyter lab` 实例的创建需要几分钟时间。创建完成后，笔记本将列在 Workbench 的用户管理的笔记本部分下，如 [图 4.5](#ch04.xhtml#fig4-5) 所示：

![](images/Figure_4.5.png)

**图 4.5：** 列在 Workbench 下的笔记本

1. 列出已创建的笔记本。
2. 点击 **OPEN JUPYTERLAB**。

### 步骤 6：打开 JupyterLab

点击 `JupyterLab` 后，将在新标签页中打开一个会话，如 [图 4.6](#ch04.xhtml#fig4-6) 所示：

![](images/Figure_4.6.png)

**图 4.6：** JupyterLab 的登录页面

1. 打开启动器的按钮（图中右侧窗口）。
2. 创建文件夹的选项。
3. 从本地系统上传文件的选项。
4. 刷新选项。
5. 克隆 Git 代码库的选项。
6. 查看 Kernels（内核）和 Terminals（终端）的选项。
7. 连接到 Git 代码库的更多选项。
8. 可用于创建新文件的启动器。
9. 创建 Python 笔记本的选项。
10. 启动 Python 笔记本控制台的选项。
11. 启动终端的选项。
12. 创建文本文件的选项。
13. 创建 Markdown 文件（`.md` 文件）的选项。
14. 创建 Python 文件（`.py` 文件）的选项。
15. 显示上下文帮助的选项。

## 构建自定义模型的数据

对于本练习，数据是从 Kaggle 下载的（链接如下），该数据集列在 CC0：公共领域许可下。数据包含数据中心的电力价格及可能影响价格的因素。

[https://www.kaggle.com/datasets/salilchoubey/electrity-prices](https://www.kaggle.com/datasets/salilchoubey/electrity-prices)

`custom_model_ele_prices` 存储桶在 `us-centra1`（单一区域）下创建，并将 `.csv` 文件上传到该存储桶，如 [图 4.7](#ch04.xhtml#fig4-7) 所示：

![](images/Figure_4.7.png)

**图 4.7：** CSV 数据上传到 Cloud Storage

自定义模型构建活动分多个步骤完成：

1. 创建 `Dockerfile`。
2. 构建用于 ML 模型构建的 Python 代码。
3. 使用 `Dockerfile` 创建 docker 并将 Python 代码推送到 docker 中。
4. 在 Workbench 环境中测试 docker。
5. 将 docker 推送到注册表。
6. 使用创建的 docker 提交训练作业。

## 容器和 Docker 简介

容器虚拟化主机操作系统（或内核），并将应用程序的需求与其他容器隔离开来。在容器出现之前，在同一虚拟机上运行许多应用程序有时会产生异常行为，因此“每个虚拟机运行一个应用程序”曾很常见。每个虚拟机运行一个应用程序解决了依赖冲突隔离问题，但会浪费资源（CPU 和内存）。虚拟机运行您的程序和一个完整的操作系统，导致您的应用程序可用资源减少。

容器通过使用容器引擎和容器镜像（即应用程序的依赖项）来解决此问题。容器引擎通过在容器中执行应用程序来隔离它们。这消除了为每个应用程序运行单独操作系统的需求，提高了资源利用率并降低了成本。

Docker 于 2013 年发布，通过允许用户快速构建程序的容器镜像，彻底改变了容器技术。Docker 是一款开源虚拟化软件，旨在帮助开发人员。它是一款 PaaS 软件，可隔离虚拟环境，以部署、创建和测试与当前操作系统不兼容的应用程序。

### Docker 的组件

* **Dockerfile：** `Dockerfile` 是每个容器的起点。此文本文件包含构建 Docker 镜像的说明，包括操作系统、语言、环境变量、文件位置、网络端口和其他组件。

