

这个改进的流程催生了一种称为 `test-driven development` 的新开发方法，即在为特定更改创建任何新代码之前，先编写该更改的测试。这种方法解决了传统开发中的一个常见问题：过分强调尽快交付代码，导致编写新代码测试的步骤常常被跳过，从而使未经测试或部分测试的代码被合并到主分支。在自动化网络基础设施时，这是一个值得考虑的重要方法，因为如果自动化基础设施只是为了加快未经测试的更改进入环境的速度，那可能并不是你想要的结果。

现在许多开发者都已采用 CI 和测试驱动开发，GitHub 和 GitLab 等 SCM 平台开始将 CI 服务原生集成到其平台中。因此，与过去需要预置、维护并将 Jenkins 等独立 CI 服务器集成到 SCM 不同，现在你只需在仓库中包含适当的文件，指示 SCM 如何执行 CI 工作流，而无需维护自己的 CI 服务器的额外工作。

## 它们的工作原理

要了解 CI 服务器如何与 SCM 配合工作，有必要思考典型的 SCM 工作流在引入 CI 后如何变化。[图 5-6](#ch05.xhtml#ch5fig6) 说明了 CI 引入到典型的分支-提交-合并 SCM 工作流时的样子。开发者的每次提交都会由 CI 进行测试。请注意，在开发者最初的几次提交中，CI 测试都会失败。只有在开发者提交了能通过 CI 的提交后，才能尝试将更改合并到主分支。在此场景中，主分支存在一些需要解决的冲突，但解决这些冲突且最后一次提交通过 CI 后，开发者便可尝试再次合并。审批人检查更改并确认所有测试均已通过后，批准合并，开发者的 `validated` 更改即被合并到主分支。

![FIGURE 5-6 SCM Workflow with CI](Images/05fig06.jpg)

FIGURE 5-6 SCM Workflow with CI

请记住，要使这一切正常工作，需要两样东西：一种是触发 CI 工作流的方式，另一种是返回 CI 工作流结果的方式。CI 工作流可能以多种潜在方式触发，但最常见的是在提交和/或合并时触发工作流。如果你使用的是外部 CI 服务器（如 Jenkins），则可以配置 SCM，在每次提交或合并请求时向 Jenkins 执行 webhook。如果你使用的是 SCM 的原生 CI 服务，则通常在仓库的适当 CI 文件中指定工作流触发条件。

现在我们可以触发 CI 工作流，需要一种方式将工作流结果传回 SCM，以便用于开发者反馈、变更日志和合并审批流程。如果你使用的是平台的原生 CI 服务，则通常会自动将 CI 工作流反馈附加到每个提交，无需任何额外工作。如果你使用的是外部 CI 服务器，则大多数 SCM 平台都有 API，使 CI 服务器能够将 CI 工作流结果附加到特定提交。

尽可能使用 SCM 平台的原生 CI 功能更为简单。预置、维护和集成自己的 CI 服务器可能很耗时；然而，在某些情况下，这项额外工作可能是必需的。例如，安全策略/法规可能规定任何工作流执行都必须在内部资源上进行，而不是公共资源上。在这种情况下，维护自己的 CI 服务器可能更有优势。需要记住的是，无论你使用的是 SCM 的原生 CI 功能还是维护自己的 CI 服务器，工具和 API 都已就绪，以实现 CI 工作流。

## 示例工作流

[清单 5-1](#ch05.xhtml#ch5list1) 展示了使用 GitHub Actions 为仓库启用 CI 的示例。按照典型的 IaC 方式，GitHub Actions 工作流使用 YAML 编写，这使它们易于阅读和修改。在此示例中，当针对主分支（`branches: main`）提交拉取请求（`on: pull_request`）且更改特定文件（`paths: ['mdd-data/\*\*.yml', 'mdd-data/\*\*.yaml']`）时，我们触发 CI 工作流。

根据特定目录或文件更改限制工作流运行通常是有利的。CI 工作流可能会变得复杂且耗时，尤其是当你拥有完整的测试覆盖率时。在此，我们仅在更改存储在 `mdd-data` 目录中的 YAML 源数据时触发工作流。这样可以避免在修改不需要 CI 的文件时浪费资源。

可用于通过 `on` 触发工作流的其他常见事件包括

*   `push`: 当新提交推送到仓库时运行
*   `schedule`: 按固定计划运行
*   `release`: 当创建新版本时运行
*   `workflow-dispatch`: 通过 GitHub UI 或 API 手动运行

现在我们有了触发 CI 工作流的方式，可以指定工作流触发时要执行的操作。在 GitHub Actions 中，这被称为 `job`。作业使用 `jobs` 键指定。作业包含一系列按顺序执行的步骤。在 [清单 5-1](#ch05.xhtml#ch5list1) 中，我们创建了一个名为 `test` 的作业，用于执行此仓库中 CI 所需的所有测试，主要是通过确保源数据具有正确语法并符合合规标准来验证源数据，并对其进行干运行以应用到网络。CI 所需的详细步骤（如语法验证、数据验证和干运行）将在本章及后续章节中介绍。目前，了解 CI 工作流的基本结构即可。

清单 5-1 GitHub Actions 工作流用于 CI

[单击此处查看代码图像](Images/ch05_images.xhtml#plist5-1)

```
name: CI
on:
  pull_request:
    branches:
      - main
    paths:
      - 'mdd-data/**.yml'
      - 'mdd-data/**.yaml'
 
jobs:
  test:
    environment: mdd-test
    steps:
      - name: Checkout Inventory
        uses: actions/checkout@v2
      - name: Install PIP requirements
        run: pip install -r requirements.txt
      - name: Install Collections
        run: ansible-galaxy collection install -r requirements.yml
      - name: Create Vault Password File
        run: echo ${{ secrets.ANSIBLE_VAULT_PASSWORD }} > vault_pass.txt
      - name: Run YAMLLINT
        run: yamllint mdd-data
      - name: Validate Data
        run: ansible-playbook ciscops.mdd.validate_data --vault-password-file
vault_pass.txt
        env:
          NETBOX_API: ${{ secrets.NETBOX_API }}
          NETBOX_TOKEN: ${{ secrets.NETBOX_TOKEN }}
      - name: Run OC Update Dry Run
        run: ansible-playbook ciscops.mdd.nso_update_oc --vault-password-file
vault_pass.txt
        env:
          NETBOX_API: ${{ secrets.NETBOX_API }}
          NETBOX_TOKEN: ${{ secrets.NETBOX_TOKEN }}
```

需要注意的是，尽管此处展示的是 GitHub 语法，但所有 CI 服务器都有类似的结构，允许你运行由任意步骤序列组成的工作流。因此，尽管工作流的语法可能会有所不同，但这些概念在 SCM 和 CI 服务器之间大多是可迁移的。

## 基础设施模拟工具

