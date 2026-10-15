
# 追踪堆栈更改

每个堆栈都包含一个带时间戳的事件记录，记录堆栈内部发生的变更，包括资源何时创建、更新或删除。这使得查看对堆栈所做的所有更改变得轻松。

需要注意的是，CloudFormation 堆栈中的资源可以手动更改，而 CloudFormation 并不阻止这种操作。例如，你可以手动删除堆栈中的 VPC。漂移检测是一项监控堆栈的功能，它会在发生此类更改时发出警报。

## CloudFormation 与 AWS CLI 的对比

你可以编写 AWS CLI 命令来快速自动创建资源，但这些资源不会被保存在堆栈中，因此无法获得堆栈提供的相同优势。

当使用 AWS CLI 时，更新资源不如使用 CloudFormation 方便。使用 CloudFormation，你只需调整模板或参数即可更改资源，CloudFormation 会自动确定如何执行这些更改。而使用 AWS CLI，你需要自行理解如何更改每个资源，并确保对一个资源的更改不会影响到其他资源。

## AWS 开发者工具

AWS 开发者工具是一组设计用于帮助应用开发者开发、构建、测试和部署其应用到 EC2 以及本地服务器的工具。这些工具简化并自动化了将新应用版本发布到生产环境所需执行的任务。

然而，AWS 开发者工具的功能不仅限于应用开发。你可以将它们作为任何基础设施即服务（IaC）方法的一部分，用于自动化 AWS 基础设施的部署和配置。

在本节中，你将了解以下 AWS 开发者工具：

*   CodeCommit

*   CodeBuild

*   CodeDeploy

*   CodePipeline

### CodeCommit

CodeCommit 让你可以创建私有 Git 仓库，并且能够轻松与其他 AWS 服务集成。Git（https://git-scm.com）是一种版本控制系统，你可以使用它来存储源代码、CloudFormation 模板、文档或任意文件——即使是像 Amazon Machine Images（AMI）和 Docker 容器这类二进制文件。这些文件存储在仓库中，通俗地称为 *repo*。

Git 采用一种称为 *versioning* 的过程，所有对仓库的更改或提交都会被永久保留，因此如果需要，你可以随时回退到文件的旧版本。

CodeCommit 对需要在同一组文件上协作的团队很有用，例如协作开发共享应用源代码基的开发者。CodeCommit 允许用户通过复制或克隆将代码检出到本地机器。他们在本地进行修改后，再将代码检回到仓库。

Git 通过差异分析（differencing）来识别不同版本文件之间的差异。如果开发者的代码更改导致应用出错，差异分析可以让开发者精确看到发生了什么变化，从而回退到之前正常工作的版本。

![](images/note.jpg) 差异分析是版本控制系统（如 Git）与像 S3 这样的文件存储系统之间的根本区别之一。

### CodeBuild

CodeBuild 是一个完全托管的构建服务。一次 *构建* 是一系列在源代码上执行的操作，用于将其准备就绪进行部署。构建过程可能包括对代码进行错误检测或将其转换为机器可读语言，但具体的构建操作取决于应用。

#### 构建操作

构建过程的主要目的之一是运行测试，以确保新代码能够正常工作。这可能包括验证源代码格式是否正确、是否不含语法错误的测试，也可能涉及通过模拟用户使用方式来测试功能性。

自动化测试是持续集成（continuous integration，CI）这一软件开发实践的核心部分。在 CI 中，开发者会多次将新代码或修改后的代码提交到共享仓库。像 CodeBuild 这样的构建提供商会对这些代码执行测试。这种快速的测试反馈能够及早发现错误，让开发者即时修复。

构建过程也可以包括将源代码编译成二进制文件，如可执行文件或安装包。你甚至可以使用 CodeBuild 来创建 Docker 容器和 Amazon Machine Images（AMI）。

你需要在构建规范文件中定义具体的任务，该文件必须随源代码一起提供。CodeBuild 可以从 CodeCommit、GitHub、Bitbucket 仓库，或 S3 桶中获取源代码。

CodeBuild 可以同时执行多个构建。构建产生的所有输出或 artifact 都会存储在 S3 桶中，从而使其在整个 AWS 环境中可访问。

#### 构建环境

CodeBuild 在一个独立的构建环境中执行构建，该环境基于一个计算实例。它在每次构建之前创建构建环境，构建完成后则删除该环境。这种隔离确保构建过程始终一致，不会受到前一次构建左overs 的影响。

构建环境始终包含一个操作系统和一个 Docker 镜像，镜像可以包含编程语言运行时和工具。AWS 提供针对 Java、Ruby、Python、Go、Node.js、Android、.NET Core、PHP 和 Docker 的预配置构建环境。你也可以自定义构建环境。

你可以从以下三种计算类型中选择构建环境：

*   `build.general1.small`——3 GB 内存和 2 个 vCPU

*   `build.general1.medium`——7 GB 内存和 4 个 vCPU

*   `build.general1.large`——15 GB 内存和 8 个 vCPU

所有计算类型均支持 Linux，而中等和大型类型还支持 Windows。

### CodeDeploy

CodeDeploy 可以自动将应用部署到 EC2 实例、弹性容器服务（ECS）、Lambda，甚至本地服务器。

CodeDeploy 通过从 S3 桶，或 GitHub、Bitbucket 仓库中拉取源文件来工作。除了应用的源文件外，你还需要提供一个应用规范文件，其中包含部署应用所需的信息。

![](images/note.jpg) CodeDeploy 服务不支持从 CodeCommit 仓库进行部署。不过，CodePipeline 可以实现此功能。我们将在本章后面介绍 CodePipeline。

#### 部署到 EC2 或本地服务器

CodeDeploy 可以将应用、脚本、配置文件以及几乎任何其他文件部署到 EC2 实例或本地服务器上。要将应用部署到实例，必须先安装 CodeDeploy Agent。Agent 使得 CodeDeploy 服务能够将文件复制到实例上并在此上执行部署任务。Agent 已经过测试，兼容以下操作系统的当前版本：

*   Amazon Linux

*   Ubuntu Server

*   Microsoft Windows Server

*   Red Hat Enterprise Linux (RHEL)

CodeDeploy 提供多种部署方式。你可以根据资源标签、Auto Scaling Group 成员或手动选择实例进行部署。你还可以通过一次性部署全部实例、逐个实例部署、一半实例部署或介于两者之间的方式控制部署节奏。

在升级部署方面，CodeDeploy 支持两种部署类型：

**In-place deployment** 这种部署方式在现有实例上直接部署应用。如果应用正在运行，CodeDeploy 可以停止它，执行所需的清理，部署新版本，然后重新启动应用。
