
如果您想运行此 YAML 示例或 Ansible 中的任何 Playbook，您需要使用命令 `ansible-playbook playbook.yml -f 10`。我建议在尝试开发自己的代码之前，先查看 YAML 教程并尝试非常简单的程序示例。在本章后面，您将学习如何使用 Ansible 构建您自己的 SOAR 实验室。Ansible 基于 YAML，这意味着它是一个在您使用时构建 YAML 文件的应用程序。这也意味着如果您计划使用 Ansible，则需要能够用 YAML 编程。

> **注意**
>
> Ansible 在 [https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html](https://docs.ansible.com/ansible/latest/reference_appendices/YAMLSyntax.html) 提供了了解 YAML 的教程。

目前理解此 YAML 程序或前面示例的细节并不重要。这三个 YAML 示例旨在向您展示，无论您的编程背景如何，YAML 都易于阅读和理解；让您大致了解 YAML 的结构；并使您能够识别 YAML 代码，因为随着您对 DevOps 了解的深入，您很可能会遇到 YAML 代码。

> **注意**
>
> 互联网上有许多优秀的免费 YAML 编程教程。例如 Tutorials Point 的教程，网址为 [https://www.tutorialspoint.com/yaml/index.htm](https://www.tutorialspoint.com/yaml/index.htm)。

## 数据建模

另一个重要的 DevOps 概念是数据建模，这不同于 YAML、JSON 和 XML 作为数据格式所提供的内容。YANG 被视为一种数据建模语言，用于对配置数据和状态数据进行建模。这意味着 YANG 定义了 JSON 或 XML 必须遵循的数据模式。可以将 YANG 视为护栏以及设定允许规则并将允许内容转换为可理解格式的翻译器。任何超出护栏范围的内容都将被拒绝，从而强制仅翻译、发送或接收经过批准格式的数据。这对于 SOC 适应其在利用不同内部和外部数据库数据时将遇到的各种数据格式至关重要。

当使用支持 YANG 数据存储的设备时，特定的 XML 或 JSON 编码消息将根据 YANG 模型被视为有效或无效。YANG 可与其他协议一起使用；但是，它最常与网络配置协议 (NETCONF) 一起使用。原因在于 YANG 提供了一种展示配置如何建模的方法，而 NETCONF 是一种可以修改配置的协议。

[图 10-22](#ch10.xhtml#ch10fig22) 提供了 YANG 序列化器将任意结构编码和解码为 XML 或 JSON 等格式的数据流示例。对于解码，YANG 将数据拉入内存并将其解码为数据节点。一旦数据准备好进行编码，它就会从数据节点编码回数据流，例如 XML 或 JSON。正如您从该示例中所见，数据建模允许将数据转换为所需的数据格式，如 JSON 或 XML。

![FIGURE 10-22 YANG Serializer Flowchart](Images/10fig22.jpg)

**图 10-22** YANG 序列化器流程图

### NETCONF

为了最好地解释 NETCONF，首先考虑简单网络管理协议 (SNMP)，它一直是网络管理员用于监控和修改配置的传统方法。使用 SNMP 的一个示例是从运行中的设备拉取状态，或推送更改（如更改接口 VLAN）。某些旧版 NAC 技术版本会使用 SNMP 作为向交换机端口推送更改的方式。SNMP 短期内不会消失；但是，SNMP 未针对自动化进行优化，这导致网络管理员想要探索 DevOps 概念时，需要一个更可编程的 SNMP 版本。NETCONF 基于简单、基于标准且稳健的 API 提供可编程性，用于读取和修改配置，非常适合编排。

NETCONF 遵循使用远程过程调用 (RPC) 的传统客户端/服务器模型。服务器配置存储在遵循 YANG 定义的数据格式的 NETCONF 配置数据存储中。要查询或修改数据，客户端通过受支持的安全传输方法之一发送基于 XML 的 RPC，服务器使用 XML 编码的数据进行回复。您可以参考 RFC 6241 以更好地了解由 YANG 定义的 NETCONF 操作。[图 10-23](#ch10.xhtml#ch10fig23) 表示 YANG NETCONF 过程。

![FIGURE 10-23 Example DevOps Communication with YANG and NETCONF](Images/10fig23.jpg)

**图 10-23** 使用 YANG 和 NETCONF 进行 DevOps 通信的示例

### RESTCONF

一种类似于 NETCONF（而非替代品）的协议是 RESTCONF。RESTCONF 使用 RESTful HTTP 接口，可用于查询和配置具有 NETCONF 配置数据存储的设备。RESTCONF 是一种基于 HTTP 的协议，支持 JSON 和 XML，而 NETCONF 仅使用 XML。当您利用 Python 等脚本语言配合 RESTCONF 时，可以自动执行各种网络管理任务。

要查看配合 YANG 使用 NETCONF 和 RESTCONF 的示例，请查看 Cisco DevNet GitHub：[https://github.com/CiscoDevNet](https://github.com/CiscoDevNet)。其中一个示例是一个脚本，可在连接到上游交换机并使用 802.1Q 中继的现有接口上配置或删除 VLAN 接口。（您可以在 [https://github.com/CiscoDevNet/restconf-examples/tree/master/restconf-samplecode/vlans](https://github.com/CiscoDevNet/restconf-examples/tree/master/restconf-samplecode/vlans) 找到此示例脚本。）

# DevOps 工具

到目前为止，您已经学习了许多通用的 DevOps 基本概念，包括文件格式和数据建模。现在让我们看看不同类型的 DevOps 工具，它们可帮助您在 SOC 服务中创建编排和自动化。DevOps 是实现 SOAR 能力的基本组成部分。

通常，开始 DevOps 之旅的常见方式是创建 Playbook，并根据期望的结果将各种 DevOps 技术应用于工作流的不同步骤。也许您希望在事件发生时向交换机推送更改。也许您希望在安全工具识别出潜在恶意软件爆发时向特定团队成员发送警报。您如何利用 DevOps 开发 SOAR 能力（从案例管理到自动响应）取决于您拥有什么工具，以及什么选项最适合适应您的工作流。

## DevOps 目标

以下列表重点介绍了 Playbook 中适合应用[第 9 章](#ch09.xhtml#ch09)涵盖的 DevOps 概念的方面。还有许多其他好的用例；但是，这些用例是将 DevOps 编程应用于简化常见工作流程元素的非常常见的领域。

*   **代码和配置分析：** 分析代码或配置，以便团队能够快速识别潜在漏洞或问题
*   **提交更改：** 允许任何人提交更改以提高生产力，同时确保所有更改均符合合规性要求
*   **监控合规性：** 持续验证 SOC 是否遵循所有策略和程序，并在需要时收集数据以证明合规性
*   **调查威胁：** 收集分析师或自动化系统为事件提供最快且最有效响应所需的信息
*   **漏洞管理：** 识别和管理组织中的 IT 相关漏洞
*   **培训和强制执行安全性：** 确保执行安全实践，并提供通知以鼓励更安全的行为
