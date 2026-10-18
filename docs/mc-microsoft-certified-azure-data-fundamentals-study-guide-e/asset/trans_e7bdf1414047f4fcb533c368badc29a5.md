

* `Soft delete` 保护数据免遭意外删除。启用此功能后，在指定的保留期内，存储资源可以被恢复。在保留期内，已删除的存储资源可以恢复到删除时的状态。可以为文件共享、容器和 Blob 配置软删除。

* `Blob versioning` 捕获 Blob 在特定时间点的状态。启用此功能后，Azure Blob Storage 在创建 Blob 以及每次修改 Blob 时都会创建新版本。此功能不适用于 ADLS 或 Azure 文件。

* `Immutability policies` 使用户能够限制数据一旦写入 Azure Blob Storage 后即无法被修改或删除。使用此功能，数据可以按需多次读取，但在用户指定的时间间隔内永远不会被修改或删除。

Azure Blob 存储支持两种不可变性策略：基于时间的策略和法律保留策略。基于时间的保留策略允许用户定义数据不可变的天数，范围在 1 到 146,000 天之间。法律保留策略限制数据在明确移除法律保留之前无法被修改或删除。

## Azure 存储常见连接问题

与 Azure 存储交互的应用程序需要穿越多个安全级别才能建立成功的连接。虽然这对于在 Azure 中安全存储数据至关重要，但可能会导致一些连接中断。这些中断可能是预期的或意外的，通常与授权问题、资源不可用或网络故障有关。以下部分描述了一些常见的 Azure 存储连接问题及其修复方法。

### 禁止异常

当应用程序尝试使用不具有存储帐户适当访问权限的访问密钥、SAS 或 Azure AD 标识进行身份验证时，通常会发生禁止异常。遇到此问题的客户端应用程序会抛出 403 异常，以指示请求未获授权。

如果客户端应用程序使用访问密钥进行身份验证，请验证访问密钥是否仍然有效。密钥可能已被重新生成，但未在应用程序中更改。如果应用程序使用 Azure AD 标识访问存储帐户，请验证该标识是否具有执行应用程序尝试的操作所需的正确权限。

虽然访问密钥或 Azure AD 的身份验证问题可能发生，但 403 禁止异常通常是由无效或过期的 SAS 导致的。使用以下规则来最大限度地减少此问题发生的可能性：

* 初始设置 SAS 时，不要设置未来的开始时间。如果客户端应用程序向存储帐户发送请求的时间与 SAS 开始时间之间存在时钟差异，则 SAS 可能无效。

* 不要在 SAS 上设置短过期时间。

* 确保 SAS 中的版本参数与客户端应用程序使用的 Azure 存储客户端库版本匹配。始终使用最新版本的 Azure 存储客户端库来缓解此问题。

### 资源未找到

资源未找到错误意味着客户端应用程序尝试连接的资源不存在。遇到此问题的客户端应用程序会抛出 404 异常。此错误有几种可能的原因：

* 应用程序尝试访问的对象已被先前的操作删除。

* 应用程序使用的 SAS 不包含执行尝试操作所需的所有权限。

* 意外的网络故障。

## 管理工具

Microsoft 提供多种用于上传和管理 Azure 存储中数据的工具。这些工具还包括可用于将数据从旧版存储解决方案迁移到 Azure 存储的工具。以下部分描述了一些用于与 Azure 存储交互的最流行工具。

### AzCopy

AzCopy 是一个命令行工具，可用于将数据迁移到 Azure 存储中或从中迁移出去。它包含一组命令，用户可以利用这些命令将数据从本地文件共享、Amazon S3、Google Cloud Storage 或另一个 Azure 存储帐户移动到 Azure 存储帐户。

从以下链接下载最新版本的 AzCopy 以开始使用：`https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10#download-azcopy`。安装后，您将能够通过本地命令提示符运行 AzCopy 命令。

使用 AzCopy 将数据移动到存储帐户或从中移出需要授权连接。[表 4.4](#c04.xhtml#c04-tbl-0004) 列出了 AzCopy 连接到 Azure 存储时可以使用的授权方法：

[TABLE 4.4](#c04.xhtml#R_c04-tbl-0004) 支持的 AzCopy 授权方法

| 存储服务 || 支持的授权方法 |
| --- | --- |
| Azure Blob 存储 || Azure AD 和 SAS |
| ADLS || Azure AD 和 SAS |
| Azure 文件 || SAS |

所有 AzCopy 语句都以 `azcopy` 关键字开头，以指示该语句使用 AzCopy 可执行文件。大多数 AzCopy 语句使用以下格式来执行操作：

```
azcopy [command] [source-file-path] [destination-storage-account] --[optional-flag]
```

例如，以下语句使用此格式将本地目录中的数据上传到 Azure Blob 存储：

```
azcopy copy 'C:\myDirectory' 'https://dp900stracct001.blob.core.windows.net/dp900container01' --recursive=true
```

此示例假设该语句使用有权在存储帐户中创建数据的 Azure AD 标识运行。要使用 SAS 而不是 Azure AD 来对存储帐户进行身份验证，只需将 SAS 令牌添加到 Blob URL 的末尾（例如，`https://dp900stracct001.blob.core.windows.net/dp900container01<SAS-Token>`）。

### Azure 存储资源管理器

Azure 存储资源管理器是一个免费的桌面应用程序，可用于跨 Azure 订阅管理 Azure 存储资源。该应用程序使用 AzCopy 执行资源管理和数据移动操作，允许用户在易于使用的 GUI 中利用 AzCopy 的性能优势。

您可以通过从 `https://azure.microsoft.com/en-us/features/storage-explorer` 下载最新版本来开始使用 Azure 存储资源管理器。在这里，您将找到适用于 Windows、macOS 和 Linux 设备的下载选项。安装后，用户可以利用 Azure 存储资源管理器执行以下任务：

* 连接到并管理多个 Azure 订阅中的 Azure 存储帐户。

* 创建、管理和删除 Blob 容器、ADLS 目录和文件共享。

* 上传、管理、下载和删除数据及虚拟硬盘。

使用以下步骤登录到您的 Azure 帐户并列出您有权访问的订阅和存储帐户：

1. 打开 Azure 存储资源管理器并单击 `Connect to Azure Storage` 按钮。[图 4.23](#c04.xhtml#c04-fig-0023) 说明了可以在哪里找到此按钮。

![FIGURE 4.23 Connect to Azure Storage button](images/c04f023.png)

[FIGURE 4.23](#c04.xhtml#R_c04-fig-0023) Connect to Azure Storage button

2. Connect to Azure Storage 弹出窗口提供 Azure 订阅、存储帐户和存储服务级别的连接选项。单击 `Subscription` 按钮并按照提示登录到您的 Azure 帐户。

3. 成功登录到 Azure 帐户后，该帐户及其关联的订阅将出现在帐户管理页面下。选择托管您要管理的存储帐户的订阅，然后单击 `Open Explorer`。

