

# CI

```yaml
---
name: CI
on:
  workflow_dispatch:
  pull_request:
    branches:
      - main
    paths:
      - 'mdd-data/**.yml'
      - 'mdd-data/**.yaml'
 
jobs:
  test:
    runs-on: self-hosted
    environment: mdd-dev
    concurrency: mdd-dev
    steps:
      - name: Checkout Inventory
        uses: actions/checkout@v2
      - name: Run YAMLLINT
        run: yamllint mdd-data
      - name: Save Rollback
        run: ansible-playbook ciscops.mdd.save_rollback
      - name: Validate Data
        run: ansible-playbook ciscops.mdd.validate
      - name: Deploy Changes
        run: ansible-playbook ciscops.mdd.update -e dry_run=no
 
      - name: Run Checks
        run: ansible-playbook ciscops.mdd.check
      - name: Load Rollback
        run: ansible-playbook ciscops.mdd.load_rollback
```

当系统用户提交 PR 时，他们正在请求将某个更改推送到网络中。此操作会启动 CI 流程以验证数据并测试更改。工作流文件指定，当提交更改 `main` 分支（我们在此保存生产版本的事实来源）的 `mdd-data` 目录中任何以 `.yml` 或 `.yaml` 结尾的文件的 PR 时，应运行该管道。也就是说，我们专门测试对事实来源的更改。我们可能还有其他工作流用于测试实际自动化代码。如果这是仓库中唯一的工作流文件，那么对于不符合这些条件的更改，管道将不会启动。不过，为大多数操作拥有多个工作流是很常见的。

在 `jobs` 部分下，我们指定特定的 GitHub 运行器。GitHub 提供基于云的运行器，但它们通常无法访问组织的内部资源。由于参考实现中使用的 CML 服务器位于组织边界内，因此使用了 GitHub“自托管”运行器。由于自托管运行器在逻辑上位于组织边界内，它可以访问 CML 服务器和管道所需的其他资源（参见 [图 6-8](#ch06.xhtml#ch6fig8)）。`self-hosted` 指令表示工作流将在提供给该仓库或组织的自托管运行器之一上运行。

![FIGURE 6-8 GitHub Self-Hosted Runner](Images/06fig08.jpg)

FIGURE 6-8 GitHub Self-Hosted Runner

接下来，`environment` 指令告诉 GitHub Actions 使用哪个可用环境。环境定义了区分测试环境所需的信息。在我们的情况中，它包括 CML 服务器、事实来源、访问资源的凭据等，并允许我们为不同场景拥有多个测试环境。密切相关的是 `concurrency` 指令，它允许我们定义是否可以在同一环境中同时运行多个测试。同时运行两个操作可能会污染结果，因此参考实现配置为限制并发性。并发性也可以更细粒度地应用于不同类型的操作。例如，你可以限制更改模型特定部分（例如系统、BGP、VLAN）的作业，但允许多个不会相互冲突的整体作业。可以为每个测试周期在 CML 中启动一个新的测试网络，但这样做会为大型架构增加大量开销。此外，测试环境通常会配备物理设备，这些设备比虚拟资源更难以配置和恢复到已知状态。

`jobs` 部分的其余部分执行管道的每个阶段，如 [图 6-9](#ch06.xhtml#ch6fig9) 中直观描绘。

![FIGURE 6-9 CI Pipeline](Images/06fig09.jpg)

FIGURE 6-9 CI Pipeline

管道首先拍摄当前测试环境的快照。许多组织由于使用物理硬件而拥有长期存在的测试环境；因此，需要将测试网络维持在与生产网络相同或尽可能接近的状态。由于 PR 包含可能有效也可能无效，甚至可能被其他运营商拒绝的更改，你不希望在更改与 `main` 分支合并之前将其完全提交到测试网络。通过拍摄环境快照，你可以回到更改推送之前的时间点。

在保存当前网络状态后，管道执行先前描述的 Ansible Collection 角色 `data` 和 `validate`，用于管道的下两个阶段。数据验证后，将其推送到网络。此时，让我们稍作偏离，谈谈我们在环境中使用的平台，Cisco Network Services Orchestrator。

## Hands-on Code: Exercising the Runner

转到以下 URL 的“Exercising the Runner”练习：

[https://github.com/model-driven-devops/mdd#exercises](https://github.com/model-driven-devops/mdd#exercises)

在此练习中，我们向你展示指定工作流 GitHub Actions 配置的文件。如果你的 GitHub 帐户支持，你也可以 fork 仓库并在自己的环境中练习这些运行器。

## Cisco Network Services Orchestrator

本书的主要前提是，标准化单一数据模型大大简化了自动化。你选择哪个模型并不重要，只要它对所有设备都相同，无论模型或供应商如何。当我们调查最佳模型时，OpenConfig 是显而易见的选择，因为它的全面性和跨供应商支持。尽管大多数供应商都支持它，但每个供应商支持的全面性不同，并且几乎总是不完整的。因此，在决定使用 OpenConfig 时，我们知道我们需要在自动化和设备本身之间放置一些东西。我们在前几章中称其为“平台”。我们使用平台的主要原因是为了控制不同供应商和设备型号上 OpenConfig 模型的实现。如果供应商未实现 OpenConfig，我们可以自行实现并确保其满足我们的要求。

我们选择 Cisco Network Services Orchestrator (NSO) 作为参考实现的平台。主要原因是，在撰写本书时，Cisco 是企业和服务提供商领域占主导地位的网络供应商。因此，由于我们主要自动化 Cisco 设备，使用 Cisco 产品作为平台是合理的。选择 NSO 的另一个原因是它对第三方供应商有丰富的支持。事实上，其大部分用户群将其部署用于 Juniper。还有其他平台选项。例如，OpenDaylight 是一个开源 SDN 控制器，Juniper Contrail 是来自 Juniper Networks 的 SDN 控制器。这些解决方案本可以是可行的选择，尽管它们更偏向于更主动的 SDN 控制器功能（例如，在路由协议或分析中活跃）。我们只是想要一个呈现北向 API 抽象的东西，该抽象转换为本地设备特定的南向 API 或 CLI。尽管 NSO 可以做的不仅仅是 API 抽象，它还在简单性、功能性和对基础设施的适用性方面胜出。

