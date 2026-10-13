
DevOps 认证项目要求学习编程概念，但也非常重视应用程序编程接口（API），它们使机器能够与机器对话。在 DevOps 领域，这意味着允许 Ansible 等工具拥有访问权限，以网络管理员相同的方式对网络交换机进行更改。API 附带一组要求，规定了一个应用程序如何与另一个应用程序对话，这就是 YANG 等工具存在的原因，它们旨在确保满足 API 规范。许多供应商遵循行业规范，使 API 支持能够跨多个供应商产品工作。一个很好的类比是考虑电源插头。理论上，您家的电源插座可以塑造插头上的孔的形状或调整输送的电量；然而，插头的制造商决定这对其用途没有用处。相反，对于插头上孔的外观和产生的电量，存在普遍预期的通用标准。供应商 API 规则非常相似，因为它们可以按供应商认为合适的方式设计，但通常遵循行业对支持内容的预期。这对开发人员来说非常好，因为通用的 API 结构意味着脚本和编程可以跨许多供应商平台工作。

## API

在非 DevOps 世界中，网络管理员使用图形用户界面（GUI）或通过命令行界面（CLI）连接到系统来与网络设备通信。为了简化任务，网络运维经理可以使用脚本通过 CLI 传递多行配置。从本质上讲，这是将 CLI 当作 API 使用，但它是用户推送代码，而不是一个系统将配置推送到另一个系统。关于 GUI，SOAP 是一种为 Web 服务执行类 API 命令的方式；然而，后来开发了表述性状态传递（REST）标准，以提供一种基于类 API 概念构建 Web 服务的更简单方法。SOAP 和 REST 专注于 HTTP，而 XML 和 JSON 具有远程过程调用（RPC）API 功能，意味着一个系统请求另一个系统执行某项操作并返回值。对于以网络为中心的任务，可以使用 SNMP，但更新且更适合 DevOps 的选择是 NETCONF 和 RESTCONF，它们提供与网络的类 REST API 接口。这些本质上是您可以用来允许工具相互通信的不同类 API 协议示例。

## NetDevOps 示例

为了将使用 API 自动执行任务的概念联系起来，我将使用 Cisco 提供的免费实验室 DevNet Sandbox（`https://developer.cisco.com/site/sandbox`）向您展示如何测试 API 的工作原理。如果 API 概念对您来说是新的，我鼓励您执行相同的练习。当您访问 Cisco DevNet Sandbox 实验室资源中心时，您会发现它提供许多始终开放和预留实验室，允许您测试本章中的许多概念。图 10-32 是 Cisco DevNet Sandbox 实验室目录的屏幕截图。带有“Reserve”按钮的实验室要求您安排实验室时间，而带有“Always On”按钮的实验室可立即使用。请注意，“always on”意味着实验室是只读的，因为任何人都可以随时访问它，而预留实验室允许您进行配置，如果您愿意，甚至可以“破坏”环境。

![图 10-32 Cisco DevNet Sandbox 免费实验室目录](Images/10fig32.jpg)

**图 10-32** Cisco DevNet Sandbox 免费实验室目录

下一个练习演示名为“Cisco IOS XE on CSR Latest Code AlwaysOn”的始终开放实验室。该实验室提供对运行 IOS XE 代码的 Cisco 云服务路由器（CSR）的访问权限，这意味着我可以尝试使用 API 调用向该系统推送配置更改。为了简化发送 API 命令，我将使用 Postman。

> **注意**
>
> 您可以从 `https://www.postman.com/downloads/` 下载 Postman。提供免费版和商业版。您需要创建一个帐户，这将是安装过程的一部分。

### NetDevOps 示例第 1 部分：使用 Postman

Postman 是一种工具，可让您向任何类型的端点发送 REST API 调用。Postman 还允许您保存调用，称为 Postman 集合，它们代表您经常使用并想要加书签的示例 API 调用。API 请求基于 GET、POST、PATCH、PUT 和 DELETE 等 HTTP 方法。图 10-33 显示了在 Mac 上运行的 Postman 界面。您可以使用 Postman 将命令从本地设备推送到外部 DevNet 实验室环境，这代表了 SOC 管理员如何从世界任何地方向其组织的网络设备推送命令。

![图 10-33 Postman 仪表板](Images/10fig33.jpg)

**图 10-33** Postman 仪表板

在 DevOps 环境中，包含等待我发送 API 命令的 Cisco CSR 路由器的详细信息。以下信息来自始终开放实验室，展示了如何访问 Cisco CSR 路由器。

### 访问详情

开发人员和网络工程师使用以下信息直接访问“Cisco IOS XE on CSR Latest Code Always On Sandbox”：

*   **CSR1000V 主机**：`ios-xe-mgmt-latest.cisco.com`
    *   **SSH 端口**：`8181`
    *   **NETCONF 端口**：`10000`
    *   **RESTCONF 端口**：`9443` (HTTPS)
*   **用户名**：`developer`
*   **密码**：`C1sco12345`

### NetDevOps 示例第 2 部分：捕获配置

此练习使用 Postman 通过 RESTCONF 捕获 Cisco CSR 路由器的配置。首先转到 Postman 并单击左上角的“New”按钮（如图 10-34 所示）以打开新工作区。在工作区中，“GET”字段是您输入要让 Postman 通信的设备地址和接口的地方。由于 Cisco 路由器位于 `ios-xe-mgmt-latest.cisco.com`，您将需要使用 HTTPS、Cisco 路由器的地址、`:9443`（因为这是为 RESTCONF 开放的端口）以及 `restconf/data/ietf-interfaces:interfaces`。您还需要单击“Authorization”选项卡并输入用户名和密码。然后，单击“Send”以收集配置。图 10-34 显示了在 Postman 中的样子。

![图 10-34 配置 Postman 以与 Cisco 路由器通信](Images/10fig34.jpg)

**图 10-34** 配置 Postman 以与 Cisco 路由器通信

成功运行的结果将显示在您运行命令的窗口下方的配置中。请注意，您可以通过单击格式下拉菜单来更改格式；图 10-35 显示了我以 JSON 格式拉取的配置。因为这是一个共享实验室，您会发现其他人推送并标记的各种配置更改。唯一不能更改的配置是接口的配置（如图 10-35 中的“DON'T TOUCH ME”所示），因为这是 Cisco 路由器公开可用所必需的。修改它可能会为所有人关闭实验室。

![图 10-35 拉取到 Postman 的配置示例](Images/10fig35.jpg)

**图 10-35** 拉取到 Postman 的配置示例
