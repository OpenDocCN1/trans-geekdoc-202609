

# CML 自动化与 IaC 集成

如前所述，为了在 CI 中正确利用 CML，我们需要能够通过 IaC 对其进行自动化。CML 可以通过多种方式实现自动化，包括 CLI (`cmlutils`)、Ansible 模块和 API。然而，使用 CML 实现 IaC 最简单的方法是利用其使用 YAML 文件创建模拟的功能，并结合 CML Ansible 模块。

## YAML 模拟文件

CML 允许你导出任何模拟文件，其中包括拓扑以及每个节点的配置，格式为 YAML。这意味着我们可以使用 CML Workbench 以可视化方式创建或修改网络拓扑，然后将其导出为 YAML 文件，如 [清单 5-2](#ch05.xhtml#ch5list2) 所示。

### 清单 5-2 CML YAML 文件

[单击此处查看代码图像](Images/ch05_images.xhtml#plist5-2)

```yaml
lab:
  description: ''
  notes: ''
  timestamp: 1618933269.4613173
  title: Test Simulation
  version: 0.0.4
nodes:
  - id: n0
    label: iosv-0
    node_definition: iosv
    x: -500
    y: -50
    configuration: ''
    image_definition: iosv-158-3
    tags: []
    interfaces:
      - id: i0
        label: Loopback0
        type: loopback
      - id: i1
        slot: 0
        label: GigabitEthernet0/0
        type: physical
      - id: i2
        slot: 1
        label: GigabitEthernet0/1
        type: physical
  - id: n1
    label: iosv-1
    node_definition: iosv
    x: -50
    y: -50
    configuration: ''
    image_definition: iosv-158-3
    tags: []
    interfaces:
      - id: i0
        label: Loopback0
        type: loopback
      - id: i1
        slot: 0
        label: GigabitEthernet0/0
        type: physical
      - id: i2
        slot: 1
        label: GigabitEthernet0/1
        type: physical
links:
  - id: l0
    i1: i1
    n1: n0
    i2: i1
    n2: n1
```

[清单 5-2](#ch05.xhtml#ch5list2) 显示了一个示例 CML YAML 文件，用于描述一个简单的双节点拓扑。此 YAML 文件中有三个主要块：

*   `lab`：包含标题和时间戳等内容的块。

*   `nodes`：包含拓扑中节点列表的块，以及它们的名称、节点类型和接口。在此示例中，我们有两个分别标记为 `iosv-0` 和 `iosv-1`、ID 为 `n0` 和 `n1` 的 IOSv 节点。

*   `links`：包含节点之间连接列表的块。在此示例中，我们有一个单个连接（id: 10），它将节点 `n0` 的接口 `i1` 连接到节点 `n2` 的接口 `i1`。

CML YAML 格式对人类和机器来说都相对容易操作。人类可以编辑此文件，且不需太多努力即可添加和删除节点和/或链接。机器可以完全从头生成此文件，可能使用某些描述网络（即真理源数据）的现有数据，或来自其他工具（例如 Microsoft Visio）的数据。无论 YAML 是如何生成的，现在都可以使用它来通过 IaC 自动化拓扑的模拟。

## Ansible 模块

CML Ansible 模块是创建、启动、停止和删除 CML 模拟的便捷方式。这些模块旨在从 YAML 文件（[清单 5-2](#ch05.xhtml#ch5list2)）在 CML 服务器上创建模拟，可选地向每个节点传递第 0 天配置，启动和停止节点，并删除模拟。[清单 5-3](#ch05.xhtml#ch5list3) 显示了一个相对简单的 Ansible playbook，用于创建模拟并启动模拟中的所有节点。

### 清单 5-3 Ansible Playbook

[单击此处查看代码图像](Images/ch05_images.xhtml#plist5-3)

```yaml
- name: Create the topology
  hosts: localhost
  gather_facts: no
  tasks:
    - name: Check for the lab file
      stat:
        path: "{{ cml_lab_file }}"
      register: stat_result
      delegate_to: localhost
      run_once: yes
 
    - name: Create the lab
      cisco.cml.cml_lab:
        host: "{{ cml_host }}"
        user: "{{ cml_username }}"
        password: "{{ cml_password }}"
        lab: "{{ cml_lab }}"
        state: present
        file: "{{ cml_lab_file }}"
      register: results
 
    - name: Refresh Inventory
      meta: refresh_inventory
 
- name: Start the nodes
  hosts: cml_hosts
  connection: local
  gather_facts: no
  tasks:
    - name: Start node
      cisco.cml.cml_node:
        name: "{{ inventory_hostname }}"
        host: "{{ cml_host }}"
        user: "{{ cml_username }}"
        password: "{{ cml_password }}"
        lab: "{{ cml_lab }}"
        state: started
```

将 CML YAML 文件（[清单 5-2](#ch05.xhtml#ch5list2)）和 Ansible playbook（[清单 5-3](#ch05.xhtml#ch5list3)）都签入版本控制，为我们提供了一种使用 IaC 构建测试环境并在 CI 中利用它的简便方法。

## API

虽然在使用 CML 时，YAML 和 Ansible playbook 是通往 IaC 的最简单路径，但可能会有时你需要自动化当前 CML Ansible 模块不支持的内容。在这种情况下，CML 公开了一套功能齐全的 API，允许你创建模拟、动态添加节点和/或链接、更新节点类型等。GUI 中可执行的大多数操作也可以通过 API 实现。

# 测试与验证

CI/CD 流程中的一个关键步骤是在合并或部署之前测试更改。此外，我们越快发现更改中的缺陷，网络管理员就能越快修复该更改中的错误并提交更正后的请求。出于这个原因，我们通常执行几种不同类型的测试，并且我们按特定顺序执行这些测试，以便我们可以 `fail faster` 并提高测试效率。

## Linting

最简单的测试类型通常被称为 `linting`。在模型驱动开发的上下文中，当我们说 linting 时，是指检查代码和真理源的语法正确性。大多数语言都有某种形式的 linting 程序可用；你永远不应该自己编写。例如，`ansible-lint` 可用于 lint Ansible 数据，`jq` 可用于 JSON 数据，而 `yamllint` 对 YAML 数据也做同样的事情。这些程序检查 playbook、`.json` 文件或 `.yaml` 文件的结构，并报告发现的任何错误。通常错误是简单的事情，例如遗漏逗号或不正确的缩进。请考虑 [清单 5-4](#ch05.xhtml#ch5list4) 中显示的 OpenConfig YAML 输入。

### 清单 5-4 错误的 YAML

[单击此处查看代码图像](Images/ch05_images.xhtml#plist5-4)

```yaml
openconfig-system:
  system:
    dns:
      servers:
        - address: 192.168.0.2
          config:
            address: 192.168.0.2
            port 53
```

乍一看，这个示例可能看起来是一个有效的 YAML 文档，但让我们通过 linter 运行它以确保万无一失：

[单击此处查看代码图像](Images/ch05_images.xhtml#ppg98-1)

```
$ yamllint bad.yaml
bad.yaml
  1:1       warning  missing document start “---”  (document-start)
  9:1        error    syntax error: could not find expected ‘:’ (syntax)
```

如您所见，我们的 YAML 存在一些问题。Linters 通常将问题分类为警告或错误。警告通常更多是样式问题，不会导致解析数据时出错，而错误会产生严格无效的文档。在此示例中，以“---”开头 YAML 文档是良好的做法，但即使没有它们也可以解析，而遗漏键和值之间的“:”会生成无法正确解析的文档。我们可以对 JSON 做同样的事情。请考虑 [清单 5-5](#ch05.xhtml#ch5list5) 中显示的 OpenConfig JSON 输入。

### 清单 5-5 错误 JSON 示例

[单击此处查看代码图像](Images/ch05_images.xhtml#plist5-5)

