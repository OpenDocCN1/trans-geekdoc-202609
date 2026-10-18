

最后，我们需要一种方法来合并各个层级的数据，并生成符合 OpenConfig 数据模型的数据。虽然 Ansible 可以合并库存中重叠的数据结构，但这并不是推荐的设置，并且由于其处理优先级的方式，其行为不利于 OpenConfig。我们仍然利用 Ansible 库存系统，但 MDD 的主要真实来源是一个目录层次结构中的文件集合，该结构的组织方式与我们的网络结构相同。参考实现中使用了以下目录层次结构：

[Click here to view code image](Images/ch06_images.xhtml#ppg125-1)

```
.
└── org
    ├── region1
    │   ├── hq
    │   │   ├── hq-rtr1
    │   │   ├── hq-rtr2
    │   │   ├── hq-sw1
    │   │   └── hq-sw2
    │   └── site1
    │       ├── site1-rtr1
    │       └── site1-sw1
    └── region2
        └── site2
            ├── site2-rtr1
            └── site2-sw1
```

此层次结构为您提供了一个单一的权威结构，其中每个设备仅属于一组组。例如，仅搜索组 `org`、`region1` 和 `hq` 以查找适用于设备 `hq-rtr1` 的数据。要查找特定设备的适用数据，将搜索从最高级别（例如 `org`）到设备本身的直接路径中的所有目录，以查找具有特定模式（例如 `oc-\*.yml`）的文件。对于 `hq-rtr1`，该目录列表将是（根位于文件系统中的 `mdd_root`）：

[Click here to view code image](Images/ch06_images.xhtml#ppg125-2)

```
{{ mdd_root }}/org
{{ mdd_root }}/org/region1
{{ mdd_root }}/org/region1/hq
{{ mdd_root }}/org/region1/hq/hq-rtr1
```

较低级别文件中找到的数据将覆盖较高级别文件中找到的数据，从而提供所需的数据优先级。让我们来看看如何使用 NTP 服务示例来实现这一点。要定义组织级别的默认值，请创建文件 `{{ mdd_root }}/org/oc-ntp.yml`，并包含以下数据：

[Click here to view code image](Images/ch06_images.xhtml#ppg126-1)

```
---
mdd_data:
  openconfig-system:system:
    clock:
      config:
        timezone-name: 'EDT -8 0'
    ntp:
      config:
        enabled: true
      servers:
        server:
          - address: '1.us.pool.ntp.org'
            config:
              address: '1.us.pool.ntp.org'
              association-type: SERVER
              iburst: true
          - address: '2.us.pool.ntp.org'
            config:
              address: '2.us.pool.ntp.org'
              association-type: SERVER
              iburst: true
```

请注意，之前的 OpenConfig 数据被放置在不同的根 `mdd_data` 下。将数据放置在更高级别的数据结构中，不仅可以更轻松地在代码中处理它，还可以允许指定元数据（例如标签）。由于此数据在 org 级别指定，它适用于我们网络中的所有设备。要覆盖 region2 的时区，我们创建文件 `{{ mdd_root }}/org/region2/oc-ntp.yml`，并包含以下数据：

[Click here to view code image](Images/ch06_images.xhtml#ppg126-2)

```
---
mdd_data:
  openconfig-system:system:
    clock:
      config:
        timezone-name: 'EST -5 0
```

我们不再指定 NTP 服务器信息，因为它是从 org 级别数据继承的。当构建 region2 中设备的数据时（例如 `site2-rtr1`），数据结构中的 clock 元素将被覆盖，其余数据将被保留。这是通过我们开发的 Ansible combine 过滤器的衍生品 `mdd_combine` 完成的，它以有利于 OpenConfig 数据模型的方式合并数据。当您对这两个文件中 `mdd_data` 包含的数据使用 `mdd_combine` 时，它将覆盖 `timezone-name` 并为 region2 中的任何设备生成以下内容：

[Click here to view code image](Images/ch06_images.xhtml#ppg127-1)

```
---
mdd_data:
  openconfig-system:system:
    clock:
      config:
        timezone-name: 'EDT -5 0'
    ntp:
      config:
        enabled: true
      servers:
        server:
          - address: '1.us.pool.ntp.org'
            config:
              address: '1.us.pool.ntp.org'
              association-type: SERVER
              iburst: true
          - address: '2.us.pool.ntp.org'
            config:
              address: '2.us.pool.ntp.org'
              association-type: SERVER
              iburst: true
```

除了应用与设备物理位置相关的数据外，我们还希望根据设备的角色应用数据。为此，我们实现了一个标记系统。如果设备具有特定标记，则将应用与该设备标记相关的所有数据。为了演示这一点，以下是将数据仅应用于具有特定角色的设备的示例。文件 `{{ mdd_root }}/org/oc-vlan.yml` 指定了组织中的所有 VLAN（仅两个，为了简洁）。在 org 级别指定 VLAN 数据可以在整个组织中提供一致性，而无需使用任何协议来分发 VLAN。让我们来看看 `oc-vlan.yml` 的内容：

[Click here to view code image](Images/ch06_images.xhtml#ppg127-2)

```
---
mdd_tags:
  - switch
mdd_data:
  openconfig-network-instance:network-instances:
    network-instance:
      - name: 'default'
        config:
          name: 'default'
          type: 'DEFAULT_INSTANCE'
          enabled: true
        vlans:
          vlan:
            - vlan-id: 100
              config:
                vlan-id: 100
                name: 'Corporate'
                status: 'ACTIVE'
            - vlan-id: 101
              config:
                vlan-id: 101
                name: 'Guest'
                status: 'ACTIVE'
```

值得注意的是，添加了元数据 `mdd_tags`，它允许我们指定此数据仅应应用于带有 `switch` 标记的设备。

## 实操代码：探索数据

转到以下 URL 中的“探索数据”练习：

[https://github.com/model-driven-devops/mdd#exercises](https://github.com/model-driven-devops/mdd#exercises)

此练习向您展示了包含数据配置的文件、它们在数据层次结构中的组织方式，以及它们如何组合以创建特定设备的配置数据。此外，您可以在您的环境中运行这些 playbook 并对其进行修改，以更好地了解它们的工作原理。

## 自动化工具

参考实现使用 Ansible，将其结构化为 Ansible collection 以用于所有工具。使用 Ansible collection 有助于保持一致且有版本的代码库，该代码库可以在 MDD 的许多不同应用中用于不同的组织。当为一个组织添加特定功能或特性时，其他组织将继承它（当然，经过适当测试后）。

Ansible Collection 结构化为执行管道各个阶段的角色，以及实现某些特定功能的各种 Ansible 插件。与所展示的管道阶段相对应的三个角色是 `data`、`validate` 和 `check`。

### data 角色

`ciscops.mdd.data` 角色实现了从真实来源构建配置数据的逻辑。然后，这些数据在设备的上下文中作为变量可用。该角色设计为在 playbook 开头调用，以便该 playbook 中的任务可以使用这些数据。例如，以下是一个简单的 playbook，用于显示设备的配置：

[Click here to view code image](Images/ch06_images.xhtml#ppg129-1)

```
- hosts: network
  connection: local
  gather_facts: no
  roles:
    - ciscops.mdd.data
  tasks:
    - debug:
        var: mdd_data
```

