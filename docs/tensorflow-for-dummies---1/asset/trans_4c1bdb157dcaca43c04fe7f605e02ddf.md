

我喜欢使用 GCP，因为我的应用程序可以访问 Google 的技术，其中包括 Google 地图、Gmail、YouTube 和 AdSense。本章重点介绍 Google 的机器学习（ML）引擎，它让你能够在 Google Cloud Platform 中执行 `TensorFlow` 应用程序。

## 概述

好消息是，你可以通过将应用程序部署到 Google 的机器学习（ML）引擎来大幅减少机器学习所需的时间。坏消息是，配置和部署应用程序的过程并不容易。涉及五个步骤：

1. **为 Google Cloud Platform（GCP）创建一个项目并将其配置为使用 Cloud Machine Learning API。**
2. **安装 Cloud 软件开发工具包（SDK）。**
3. **将你的 TensorFlow 应用程序结构化为一个包。**
4. **将你的包和处理数据上传到 Google Cloud Storage。**
5. **使用 Cloud SDK 执行训练或预测作业。**

在撰写本章时，我假设你从未听说过 GCP。因此，在我解释如何部署应用程序之前，我先介绍 Cloud 软件开发工具包（SDK）和 Cloud Storage，并解释如何创建一个 GCP 项目。

## 使用 GCP 项目

如果你想利用 GCP 的功能，第一步是创建一个项目。该项目充当你开发工作的中央容器，其中包含所有元数据和配置文件。在你执行代码或启动 Web 应用程序之前，需要将文件上传到你的项目。同样，如果你想要访问特殊功能，需要通过项目提出请求。

要构建可访问 ML Engine 的 GCP 项目，你需要执行三个步骤：

1. **在 Google Developer Console 中创建一个项目。**
2. **为项目启用计费。**
3. **启用项目以访问机器学习引擎。**

![tip](images/tip.png)本书示例代码中的 `ch13` 目录包含两个文件夹：`cloud_mnist` 和 `cluster_mnist`。这些文件夹包含可部署到 ML Engine 的包，但它们不是 GCP 项目。GCP 项目驻留在云中，因此如果你想跟随本章的开发，你需要自行创建和配置一个 GCP 项目。

### 创建新项目

任何拥有有效电子邮件地址的人都可以免费创建 GCP 项目而无需任何费用或义务。该过程涉及五个步骤：

1. **访问 Cloud Console，网址为** [`https://console.cloud.google.com`](https://console.cloud.google.com)**。**
2. **如果这是你第一次访问控制台，请提供联系电子邮件地址和密码。**
3. **在上方的水平栏中，点击 Select a Project。**
4. **在 Select 对话框中，点击右侧的加号按钮。**
5. **在 New Project 页面中，输入项目名称并点击 Create 按钮。**

在使用 GCP 时，你需要理解项目名称和 ID 之间的区别。项目的名称由开发者选择，控制台使用它来显示当前项目。

相比之下，项目的 ID 由 GCP 根据项目名称选择，并且在 GCP 的所有项目中唯一标识该项目。如果你想上传代码或更改项目的配置，你将需要通过其 ID 访问你的项目。因此，了解你的项目的 ID 是一个好主意。

### 计费

机器学习是一种强大的功能，但与 TensorFlow 不同，它不是免费的。Google 对机器学习的费用取决于三个因素：操作类型（训练或预测）、持续时间以及你的位置：

* 训练：美国每小时每个训练单元 0.49 美元，欧洲和亚洲 0.54 美元
* 预测：美国每千次预测 0.10 美元，外加每小时 0.40 美元；欧洲和亚洲每千次预测 0.11 美元，外加每小时 0.44 美元

Google 在你使用 ML Engine 之后收取费用，而不是预先收取。但你需要在使用引擎之前确定付款方式，你可以通过将项目与计费账户关联来配置此项：

1. **访问 Cloud Console 中的项目页面。**
2. **打开左上角的菜单（三条水平线）并选择 Billing 选项。**
3. **点击标题为 Add billing account 的按钮。**
4. **输入你的联系信息和计费信息。**

在页面底部，有一个按钮可让你设置自动付款，这将授权 Google 在使用资源时从账户中提取资金。

### 访问机器学习引擎

在为你的项目设置计费账户后，你可以访问付费功能，如 ML Engine。要启用此功能，请打开项目页面左上角的菜单并选择 APIs & Services。这将打开 APIs & Services 页面，该页面标识项目可以访问的功能。

页面左侧显示三个链接：Dashboard、Library 和 Credentials。Library 链接打开一个页面，列出项目可用的 API。要启用对 ML Engine 的访问，你需要执行五个步骤：

1. **从 APIs & Services 页面，点击左侧的 Library 链接。**
2. **找到 Machine Learning 组并点击右侧的 View All 链接。**
3. **点击标题为 Google Cloud Machine Learning Engine 的链接。**
4. **点击页面顶部的 Enable 链接。**
5. **等待 GCP 授予对新功能的使用权限。**

执行这些步骤后，你可以通过访问 APIs & Services 仪表板来验证你的项目是否可以访问 ML Engine。页面的下半部分列出了项目可以访问的不同 API，其中应包括 Google Cloud Storage 和 Google Cloud Machine Learning Engine。

## Cloud 软件开发工具包（SDK）

在你了解如何创建 GCP 项目并将其配置为访问 ML Engine 后，你就可以与你的项目进行交互了。Google 通过 Google SDK 使此成为可能。

你可以从 [`http://cloud.google.com/sdk`](http://cloud.google.com/sdk) 下载 SDK。点击 Install 按钮会打开一个页面，提供在你的开发系统上下载 SDK 安装程序的说明。我建议安装所有可用的组件。

当你启动安装程序时，它会要求你登录你的账户并授予权限，以便 SDK 可以访问你的 GCP 账户。它还会要求你选择一个云项目作为 SDK 的默认项目。在你选择后，所有后续的 SDK 命令都将影响默认项目。

安装 SDK 后，你就可以访问两个命令行实用程序：

* **`gcloud`：** 提供通用项目交互并访问 Google 的 App Engine、Datastore、DNS 和 ML Engine
* **`gsutil`：** 访问 Google Cloud Storage

如果你运行的是 Windows，可以通过 `gcloud.cmd` 和 `gsutil.cmd` 访问这些实用程序。如果你运行的是 Linux 或 Mac OS，可以通过 `gcloud` 和 `gsutil` 可执行文件访问它们。

在开始使用 SDK 之前，你应该确保可以从命令行提示符访问 `gcloud` 和 `gsutil`。如果输入 `gcloud version` 且看不到任何版本信息，请将 `google-cloud-sdk/bin` 文件夹添加到你的 `PATH` 环境变量中。

## gcloud 实用程序

安装 SDK 后，你可以在命令行上执行 `gcloud` 命令。所有 `gcloud` 命令具有相同的格式：

`gcloud [optional flags] <group | command>`

例如，你可以通过输入以下命令来检查 `gcloud` 的版本：

`gcloud version`

该命令标识 SDK 的版本及其组件的版本。你可以通过输入以下命令安装最新组件：

`gcloud components update`

在此示例中，`components` 是一个 *组名*，因为它需要额外的命令，例如 `update`。你可以将组视为图形用户界面中的子菜单。相比之下，`version` 是一个 *命令名*，因为它不接受进一步的命令。

