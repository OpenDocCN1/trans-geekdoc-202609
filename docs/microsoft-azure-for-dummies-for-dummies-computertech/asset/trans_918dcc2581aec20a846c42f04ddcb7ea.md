
## 部署容器实例

*   **Image Registry:** 添加登录服务器、用户名和密码。
*   **OS Type:** 选择正在使用的操作系统。

3. **单击“Review + Create”，然后单击“Create”提交部署。**

    无需担心网络、标记等问题。

4. **如果部署失败，请阅读操作详细信息。**

    ARM 可能通过验证但仍导致部署失败。如果发生这种情况，与任何失败的部署一样，请阅读 Azure 提供的所有操作详细信息。

[图 6-6](#c06.xhtml#c06-fig-0006) 显示了失败的 ACI 部署。横幅用通俗易懂的英语解释了问题。在本例中，容器类型指定为 Linux 而非 Windows。也可以单击“Operation Details”以获取来自 ARM 的更详细反馈。

失败的部署并非大问题。可以根据需要多次重新运行部署模板，直到成功为止。只需单击 [图 6-6](#c06.xhtml#c06-fig-0006) 中所示的“Redeploy”按钮。默认情况下，部署不会删除现有资源。相反，模板会从中断处继续，直到部署与底层模板定义匹配。

![图 6-6：Azure 部署失败时不要恐慌。阅读错误消息，从中吸取教训。](images/9781119612148-fg0606.png)

[图 6-6：](#c06.xhtml#rc06-fig-0006) Azure 部署失败时不要恐慌。阅读错误消息，从中吸取教训。

![Technical stuff](images/technicalstuff.png)研究部署详细信息（成功或失败）的另一个位置是 Azure 门户中的“Resource Groups”边栏选项卡。打开一个资源组，导航到“Deployments”边栏选项卡。Azure 中的每个部署都会被记录下来，供参考和/或故障排除。

我所解释的关于 Azure 中容器支持的一切都很好，但坦率地说，ACI 存在一个致命缺陷：它没有编排功能。开发人员很可能需要同时部署多个容器并将它们作为一个组进行管理。业务可能还要求容器能够水平扩展以适应用户负载，并具有高可用性。换句话说，ACI 服务适用于相对简单的容器部署，但在业务中除最基本的容器用例外，都需要容器编排平台。

为了满足这些要求及更多需求，需要一个容器编排平台，例如 AKS。

## Azure Kubernetes Service 简介

AKS 最初是 Azure Container Service (ACS)，支持包括 Kubernetes、Swarm 和 DC/OS 在内的多个容器编排平台。ACS 的缺点是其复杂性，以及大多数客户仅想要对 Kubernetes 的第一方支持。因此，尽管可能在 Azure 门户或其他地方偶尔看到对 ACS 的引用，但请忽略它们，专注于 AKS。

我没有足够的篇幅演示如何部署和管理 AKS 群集。相反，我将描述 AKS 架构，解释其部分优势，并提供在 Azure 中使用 AKS 的宏观视角。

![Remember](images/remember.png)开发人员启动容器并非因为它们好玩，而是因为它们实用。容器托管应用程序组件（如 Web 服务器或数据库服务器），进而形成应用程序解决方案。因此，从现在开始，请将“container”（容器）和“application”（应用程序）这两个词联系起来。

### AKS 架构

[图 6-7](#c06.xhtml#c06-fig-0007) 显示了 AKS 的基本元素：

*   **Master node（主节点）：** Microsoft 抽象了控制平面（在 Kubernetes 命名法中称为 *master node*），以便专注于工作节点和 Pod。这种托管的平台即服务 (PaaS) 平台是许多企业喜爱 AKS 的原因之一。主节点负责调度 Kubernetes 与底层群集之间的所有通信。
*   **Worker node（工作节点）：** 在 AKS 中，工作节点是构成群集的 VM。群集提供大量并行计算、在节点间轻松移动 Pod、在不关闭整个群集的情况下对节点执行滚动更新等能力。一种选择是使用 ACI 作为工作节点。

    [图 6-7](#c06.xhtml#c06-fig-0007) 还显示了 ACR，AKS 可以从中拉取存储的映像。这种 Azure 集成难道不引人注目吗？

*   **Pod：** Pod 是 AKS 生态系统中最小的可部署单元。一个 Pod 可能包含一个 Docker 容器，也可能包含一组需要在一起、相互通信并作为一个内聚单元运行的容器。

跟上思路了吗？

![图 6-7：AKS 高级架构。](images/9781119612148-fg0607.png)

[图 6-7：](#c06.xhtml#rc06-fig-0007) AKS 高级架构。

### AKS 管理说明

在继续之前，我将回顾开发人员和管理员如何与 AKS 交互。从控制平面角度来看，有 AZR，可用于通过基于角色的访问控制保护 AKS 群集、升级 Kubernetes 版本、横向扩展群集、添加或删除工作节点等。

从应用程序平面角度来看，Microsoft 希望确保客户无需学习新工具集即可在 AKS 中使用容器。

#### `kubectl` 命令行工具

大多数 Kubernetes 专业人员使用 `kubectl`（通常发音为 *KOOB-see-tee-el*、*KOOB-control* 或 *KOOB-cuttle*）以编程方式与其 Kubernetes 群集及其 Pod 交互。如果工作站上安装了 Azure CLI，可以通过发出以下命令轻松安装 `kubectl`：

```
az aks install-cli
```

事实上，Azure CLI 在应用上下文命令工作流方面似乎大量借用了 `kubectl` 语法。例如，要使用 `kubectl` 列出正在运行的 Pod（容器），请运行：

```
$ kubectl get pods
READY STATUS RESTARTS AGE
azure-database-3406967446-nmpcf 1/1 Running 0 25m
azure-web-3309479140-3dfh0 1/1 Running 0 13m
```

#### Kubernetes Web UI

Kubernetes Web UI 是一个图形化仪表板，为管理员和开发人员提供强大的控制界面。[图 6-8](#c06.xhtml#c06-fig-0008) 显示了该界面。

![图 6-8：Kubernetes Web UI 仪表板。](images/9781119612148-fg0608.png)

[图 6-8：](#c06.xhtml#rc06-fig-0008) Kubernetes Web UI 仪表板。

同样，应使用 Azure CLI 连接到仪表板；无法从 Azure 门户进行连接。相关命令如下：

```
az aks browse --resource-group myResourceGroup --name myAKSCluster
```

![Technical stuff](images/technicalstuff.png)`az aks browse` 命令在工作站和 Azure 中运行的 AKS 群集之间创建一个代理；它在输出中提供连接 URL。典型的连接 URL 为 `http://127.0.0.1:8001`。

## 将容器与 Azure App Service 配合使用

我将通过展示如何将容器与 Azure App Service 结合使用来结束本章。（第 7 章 [Chapter 7](#c07.xhtml) 深入探讨 Azure App Service。）

Azure Web App for Containers 允许将现有的基于容器的应用插入 Azure App Service 应用中。对于未使用 AKS 等编排/缩放平台的企业，此功能是一种无需额外投资和复杂性即可自动缩放应用的绝佳方式。

“你无法在 App Service 中托管非 .NET 应用，对吧？”你问道。我很高兴地报告，这是不正确的。容器可以使用任何受支持的运行时环境，包括：

*   .NET Core
*   Node.js
*   PHP
*   Java
*   Python
*   Ruby

此过程使用 Azure 门户中的 Cloud Shell。要创建一个使用从 Docker Hub 拉取的 Linux 容器作为代码库的新 Azure App Service Web 应用，请执行以下步骤：

1. **在 Azure 门户中启动 Cloud Shell，并选择 Bash 环境。**

    选择哪种 Shell 无关紧要，因为 Azure CLI 在两者中均可用。
