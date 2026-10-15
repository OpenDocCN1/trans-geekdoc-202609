
-   [动态缩放](https://link.example.com/dynamic_scaling)会在需求增加时使用 `scaling out` 过程来启动新实例，也可以在需求减少时 `scale in`，即终止实例。你可以根据度量（例如实例的平均 CPU 利用率）或基于并发应用用户数量来 `scale in` 或 `scale out`。

#### Scheduled Scaling

除了或在 addition to 动态缩放，Auto Scaling 可以根据时间表来 `scale in` 或 `scale out`。这在需求具有可预测的高峰和低谷时特别有用。

Predictive scaling 是一个功能，它查看历史使用模式并预测未来的高峰。随后会自动创建计划缩放操作以匹配。它需要至少一天的流量数据来创建缩放计划。

![](images/note.jpg) EC2 Auto Scaling 体现了云架构设计的核心原则之一：不要猜测你的容量需求。Auto Scaling 可以在不需要容量时降低成本，在需要时提升性能。

## Configuration Management

Configuration management 是一种确保系统配置准确且一致的方法。虽然自动化关注执行任务，配置管理主要关注强制并监控实例的内部配置状态，以确保它们是你期望的样子。这些配置状态主要包括但不限于操作系统配置和已安装的软件。

与一般的自动化一样，配置管理工具使用要么 imperative 要么 declarative 方法。AWS 通过两种工具提供这两种方法，帮助你实现 EC2 及本地实例的配置管理：Systems Manager 和 OpsWorks。

### Systems Manager

Systems Manager 使用 imperative 方法，使你的实例和 AWS 环境达到你想要的状态。

#### Command Documents

Command documents 是脚本，可一次性或定期运行，使系统达到你想要的状态。

使用 Command documents，你可以在实例上安装软件、安装最新的安全补丁，或查看实例上安装的所有软件。你可以使用与 Linux 或 Windows 实例相同的 Bash 或 PowerShell 命令。Systems Manager 可以定期运行这些命令，或在触发时（如新实例启动）执行。Systems Manager 需要在你希望管理的实例上安装代理。

#### Configuration Compliance

Configuration Compliance 是 Systems Manager 的一个功能，用于显示实例是否符合你期望的配置状态——比如某个特定版本的应用是否已安装，或操作系统是否已更新到最新的安全补丁。

#### Automation Documents

除了提供实例的配置管理外，Systems Manager 还允许你执行使用 AWS Management Console 或 AWS CLI 完成的众多管理任务。这些操作通过 Automation documents 定义。例如，你可以使用 Systems Manager 自动创建 Elastic Block Store (EBS) 卷的快照、启动或终止实例、创建 CloudFormation 堆栈，甚至从已有的 EBS 卷创建 AMI。

#### Distributor

使用 Systems Manager Distributor，你可以将安装包部署到实例。你创建一个包含可安装或可执行软件包的 `.zip` 存档，放入 S3 桶中，并告诉 Distributor 其位置。Distributor 会处理部署和安装过程。Distributor 特别适用于部署已经是安装程序或可执行文件的标准软件包集。

### OpsWorks

OpsWorks 是三种不同服务的集合，让你能够使用声明式方法进行配置管理。正如本章前文所述，使用声明式方法需要一定的智能来将声明式代码转换为 imperative 操作。OpsWorks 使用两个流行的配置管理平台来满足这一需求：Chef（https://www.chef.io）和 Puppet Enterprise（https://puppet.com）。

Puppet 和 Chef 是流行的配置管理平台，能够配置操作系统、部署应用、创建数据库，并几乎完成你能想象的所有配置任务，全部使用代码。它们广泛用于本地部署，OpsWorks 将它们的能力带到 AWS 作为托管服务。

正如自动化一般，配置管理不是全有或全无的决定。好在 OpsWorks 提供了三种不同的选项，以满足各种配置管理需求。

AWS OpsWorks for Puppet Enterprise 和 AWS OpsWorks for Chef Automate 是强大且可扩展的选项，让你可以在 AWS 上运行托管的 Puppet 或 Chef 服务器。这适合希望在所有实例上使用配置管理的场景。

AWS OpsWorks Stacks 提供一种简单且灵活的方式，仅用于部署应用。它不要求你全盘使用配置管理，而是仅用于部署和配置应用。OpsWorks Stacks 会自行处理所需的基础设施。

#### AWS OpsWorks for Puppet Enterprise and AWS OpsWorks for Chef Automate

AWS OpsWorks for Puppet Enterprise 与 Chef Automate 的高层架构相似。它们至少包含一个 Puppet 主服务器或 Chef 服务器，用于与受管理节点（EC2 或本地实例）通信，并需安装代理。

你使用 Puppet 模块或 Chef 配方来定义实例的配置状态（如操作系统配置、应用安装）。这些模块或配方包含声明式代码，使用平台的域特定语言编写，指定要 provision 的资源。代码存储在中央位置，如 CodeCommit Git 仓库或 S3 桶。

OpsWorks 管理服务器，但你需要了解并操作 Puppet 或 Chef 软件，因此需要了解它们的工作原理和管理方法。别担心，Chef 和 Puppet 都拥有庞大的生态系统，提供大量现成代码，可用于各种常见场景。

#### AWS OpsWorks Stacks

如果你喜欢基础设施即代码 (IaC) 的概念，但不熟悉管理 Puppet 或 Chef 服务器，可以使用 AWS OpsWorks Stacks。

OpsWorks Stacks 让你可以在 **stacks**（堆栈）中构建应用基础设施。一个 *stack* 是应用所需的所有资源的集合：EC2 实例、数据库、应用负载均衡等。每个 stack 包含至少一个 **layer**（层），层是用于包含应用的某个组件的容器。

下面是一个典型的数据库驱动应用的三层结构示例：

*   **应用层**：包含 EC2 实例或容器  
*   **数据库层**：包含自托管或关系型数据库服务 (RDS) 的数据库实例  
*   **应用负载均衡层**：将流量分发到应用层  

OpsWorks 使用两种基本类型的层：**OpsWorks 层** 和 **service 层**。

![](images/note.jpg) 尽管名称如此，OpsWorks stack 与 CloudFormation stack 不同，也不使用 CloudFormation 模板。
