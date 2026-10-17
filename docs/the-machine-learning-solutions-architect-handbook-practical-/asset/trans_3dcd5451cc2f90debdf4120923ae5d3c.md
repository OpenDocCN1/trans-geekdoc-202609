

使用开源技术构建 ML 平台具有显著优势。但同样需要考虑潜在的缺点。可能会因集成复杂性、缺乏全面支持、安全漏洞以及与商业解决方案相比功能受限等问题而产生挑战。此外，维护开源平台的资源密集型特性，加上团队可能面临的学习曲线，可能会影响效率和总拥有成本。对文档质量的担忧、缺乏标准化，以及对更新和维护的责任，进一步强调了需要谨慎考虑的必要性。在选择开源方案之前，您必须根据具体要求、资源和专业知识，将这些因素与优势进行权衡。

考虑到这些因素，让我们探讨使用开源技术设计核心 ML 平台组件。

## 实现数据科学环境

Kubeflow 是构建在 Kubernetes 之上的开源 ML 平台。它提供了一组专门设计用于简化 ML 工作负载部署、编排和管理的工具和框架。Kubeflow 提供了用于交互式数据探索和实验的 Jupyter 笔记本、分布式训练功能以及模型服务基础设施等功能。

Kubeflow 的核心功能包括：

*   一个中央 UI 仪表板
*   用于代码编写和模型构建的 Jupyter Notebook 服务器
*   用于 ML 管道编排的 Kubeflow 管道
*   `KFServing` 用于模型服务
*   用于模型训练支持的训练操作符

下图说明了 Kubeflow 如何为数据科学环境提供所需的各种组件。具体来说，我们将深入探讨其对 Jupyter Notebook 服务器的支持，因为它是数据科学环境的主要构建块。

![](OEBPS/Images/B20836_07_01.png)

图 7.1: 基于 Kubeflow 的数据科学环境

Kubeflow 提供了一个具有内置身份验证和授权支持的多租户 Jupyter Notebook 服务器环境。让我们详细讨论每个核心组件：

*   **Jupyter Notebook**: 作为数据科学家，您可以利用 Kubeflow Jupyter Notebook 服务器，该服务器提供了一个平台，用于在 Jupyter 笔记本中编写和运行 `Python` 代码以探索数据并构建模型。使用 Kubeflow，您可以生成多个笔记本服务器，每个服务器都与一个单独的 Kubernetes 命名空间相关联，该命名空间对应于团队、项目或单个用户。每个笔记本服务器在 `Kubernetes` `Pod` 内运行一个容器。默认情况下，Kubeflow 笔记本服务器提供一系列托管在公共容器镜像仓库中的笔记本容器镜像供选择。或者，您可以创建自定义笔记本容器镜像以满足特定要求。为了确保标准和一致性，Kubeflow 管理员可以为用户提供一系列标准镜像供使用。创建笔记本服务器时，您选择在其中运行笔记本服务器的命名空间。此外，您指定笔记本服务器的容器镜像的 `Universal Resource Identifier` (`URI`)。您还可以灵活地指定资源要求，例如 CPU/GPU 数量和内存大小。

*   **身份验证和授权**: 您通过 Kubeflow UI 仪表板访问笔记本服务器，该仪表板通过 Dex `OpenID Connect` (`OIDC`) 提供者提供身份验证服务。Dex 是一个身份服务，使用 OIDC 为其他应用程序提供身份验证。Dex 可以与其他身份验证服务（例如 `Active Directory` 服务）联合。每个笔记本都与一个默认的 Kubernetes 服务帐户（`default-editor`）相关联，该帐户可用于授权目的（例如授予笔记本访问 Kubernetes 集群中各种资源的权限）。Kubeflow 使用 Istio `基于角色的访问控制` (`RBAC`) 来控制集群内流量。以下 `YAML` 文件将 `default-editor` 服务帐户（与 Kubeflow 笔记本相关联）通过将 `ml-pipeline-services` 服务角色附加到它，授予访问 Kubeflow 管道服务的权限：

```
apiVersion: rbac.istio.io/v1alpha1
kind: ServiceRoleBinding
metadata:
name: bind-ml-pipeline-nb-admin
namespace: kubeflow
spec:
roleRef:
kind: ServiceRole
name: ml-pipeline-services
subjects:
- properties:
source.principal: cluster.local/ns/admin/sa/default-editor
```

*   **多租户**: Kubeflow 提供了多用户访问共享 Kubeflow 环境的功能，同时确保资源隔离。这是通过为每个用户创建单独的命名空间，并利用 Kubernetes RBAC 和 Istio RBAC 来管理这些命名空间及其关联资源的访问控制来实现的。对于团队内的协作工作，命名空间的所有者可以直接从 Kubeflow 仪表板 UI 授予其他用户访问权限。使用 `Manage Contributor` 功能，命名空间所有者可以指定哪些用户被授予访问命名空间及其资源的权限。

除了上述核心组件外，Kubeflow 还提供了一种机制，用于引导用户访问不同的 Kubeflow 资源。要引导新 Kubeflow 用户，您需要创建一个新用户配置文件，这将自动为配置文件生成一个新命名空间。

以下 YAML 文件，使用 `kubectl` 应用后，将创建一个名为 `test-user` 且电子邮件为 `test-user@kubeflow.org` 的新用户配置文件，并创建一个名为 `test-user` 的新命名空间：

```
apiVersion: kubeflow.org/v1beta1
kind: Profile
metadata:
name: test-user
spec:
owner:
kind: User
name: test-user@kubeflow.org
```

您可以运行 `kubectl get profiles` 和 `kubectl get namespaces` 命令来验证配置文件和命名空间是否已创建。

用户创建并添加到 Kubeflow Dex 身份验证服务后，新用户可以登录 Kubeflow 仪表板并访问新创建的命名空间下的 Kubeflow 资源（例如 Jupyter Notebook 服务器）。

在承诺实施 Kubeflow 之前，必须意识到使用 Kubeflow 构建数据科学环境存在几个关键挑战。无论是在本地还是在 AWS 等云平台上，在 Kubernetes 之上安装 Kubeflow 都可能很复杂，通常需要大量的配置和调试。众多的组件使得安装并非易事。Kubeflow 由许多松散耦合的组件组成，每个组件都有自己的版本。在不同版本之间编排这些多样化的组件以无缝协作为一个集成平台可能会面临困难。Kubeflow 缺乏文档。Kubeflow 文档通常指向旧版本的组件。过时的文档使得采用变得更加困难，因为新 Kubeflow 用户需要与文档和平台版本之间的不匹配作斗争。尽管存在这些限制，由于其对端到端管道的支持、对不同 ML 框架的丰富支持以及可移植性，Kubeflow 仍然是构建 ML 平台的高度推荐技术。

至此，我们已回顾了 Kubeflow 如何用于提供多租户 Jupyter Notebook 环境以进行实验和模型构建。接下来，让我们看看如何构建模型训练环境。

## 构建模型训练环境

如前所述，在 ML 平台中，通常提供专用的模型训练服务和基础设施，以支持 ML 管道中大规模和自动化的模型训练。

该专用训练服务应易于从平台内的不同组件访问，例如实验环境（如 Jupyter 笔记本）以及 ML 自动化管道。

