
对于这个示例，我为路由器创建了一个组，并将该组命名为 `GNS-3_Routers`（如果可能，你应该避免在名称中使用空格）。我在名为 `GNS-3_Routers` 的组下还有两个不同的条目。Ansible 以其扩展功能而闻名，这是其实现该功能的方式之一。任何由 Ansible 调用并使用我在 hosts 文件中定义的这些特定组名的 playbook 都将知道要引用哪些系统。在我的示例中，我只有两个主机，但 Ansible 组包含数千个主机的情况并不少见。此时，你的基本 Ansible 安装已完成，你已准备好创建第一个 playbook。

#### Ansible Playbooks

填充 Ansible hosts 文件后，你就可以创建第一个 Ansible playbook 了。请记住，Ansible playbook 是一个采用 YAML 格式的配置文件，表示你想要执行的一组任务。自动化工作流所需的第一个也是最常见的任务是访问系统。SOC 通常会为 Ansible 设置 SSH 数字证书，以便在自动化工作流步骤中向其访问的设备进行身份验证。你也可以使用用户名和密码，但证书更常见。这可以利用 YAML 编程语言来实现。

为了了解其工作原理，让我们检查一个基本的 Ansible playbook，它允许我备份我在示例 Ansible hosts 文件中已定义的 Cisco 路由器。以下代码是实现此目标的 playbook 示例。如果 YAML 格式看起来令人困惑，难以理解或遵循，请回顾本章前面我对 YAML 的简要概述，其中解释了 YAML 文件中核心组件的预期内容。

[点击此处查看代码图像](Images/ch10_images.xhtml#p599pro01a)

```
---
- hosts: Router1
  gather_facts: true
  connection: local
  tasks:
   - name: show run 
     ios_command:
       commands:
         - show run 
         host: "{{ ansible_host }}"
         username: admin
         password: cisco
         register: config
     
   - name: save output to /etc/ansible/router_backups/
     copy: 
       content: "{{ config.stdout[0] }}"
       dest: "/etc/ansible/router_backups/show_run_{{ inventory_hostname }}.txt"
```

查看此示例，首先要注意到的是文件以三个破折号开头。请记住，每个 YAML 文件都以三个破折号开头，以告知计算机这是一个 YAML 文件。接下来是一个破折号，后跟一个空格和单词 `hosts`。这是输入 Ansible 清单中引用的主机名称的地方。`connection: local` 行表示 SSH 连接从此服务器发起，即运行 Ansible 的服务器。当你运行更大规模的 Ansible 部署时，你可能希望从不同的地理区域发起连接以提高效率。这是一个关键点。回想本章前面的内容，SOAR 的一个关键价值是通过利用更有效的搜索来减少任务开销。这是通过内置于自动化中的战术设备访问来节省时间的一个示例。

前一个配置文件中的 `tasks` 和 `commands` 部分是配置文件最关键的部分，因为它包含我想要运行的实际命令。当你看到括号或双括号中的内容时，它们代表变量。你可以用你要连接的系统名称替换这些变量。例如，你可能决定在一百个主机上运行此 playbook，但希望 Ansible 自动将备份配置文件命名为与正在评估的主机相同的名称。**图 10-26** 显示了 Nano 文本编辑器中的示例 playbook 文件。

![图 10-26 执行的 Ansible Playbook 示例](Images/10fig26.jpg)

**图 10-26** 执行的 Ansible Playbook 示例

有许多资源可供你访问以获取更多 Ansible playbook 示例。演练 Ansible 的目的是让你熟悉使用开源 SOAR 设置和开发基本 playbook，以自动化备份路由器配置等简单任务。如果你需要复习 YAML 编程技能，请回顾本章中的 YAML 部分，其中提供了 Ansible 创建者提供的 YAML 教程参考。

> **注意**
>
> Colin McCarthy 在他的 GitHub 存储库 [https://github.com/colin-mccarthy/ansible-playbooks-for-cisco-ios](https://github.com/colin-mccarthy/ansible-playbooks-for-cisco-ios) 上提供了许多有用的 Ansible playbook 示例。

现在你有了一个可用于练习 DevOps 概念的 SOAR 实验室，你需要一个要自动化的任务。一个非常流行的自动化任务是蓝图化端点，即提取关于端点的详细信息。此任务对于各种 SOC 服务极其有用，包括漏洞管理（以便你知道要扫描哪些漏洞）以及事件响应（以便你知道受事件影响的系统上发生了什么）。接下来，我将讲解如何使用 Osquery 执行端点蓝图化。你可以使用你的 Ansible 实验室来自动化此过程。

### 使用 Osquery 进行蓝图化

诸如 NIST 800-53 Rev4 CM-11 之类的指南概述了识别组织内系统上安装和运行内容的必要性。识别主机系统上安装和运行的内容有时被称为建立该系统的蓝图。蓝图查询你环境中的硬件和软件，并尝试了解与收集内容相关的功能。这与本书前面提到的*基线化* 概念略有不同，后者旨在建立对什么被视为正常的理解，并寻找异常值。编译组织托管端点的蓝图使 SOC 能够深入了解端点，从而可以监控和强制执行对安全标准的合规性。

蓝图化的目标是识别不符合企业安全标准的系统，主动解决漏洞，了解环境中运行的内容（包括系统上安装的应用程序），并梳理出与组织内连接内容相关的风险概览。安全工具（如漏洞扫描器、SIEM/SOAR 和 NAC 技术）通常包含蓝图功能的变体。

本节中的用例介绍了 Osquery，这是一个用于调查端点元数据的开源工具。如果你想查询某个操作（例如特定的 PowerShell 命令），Osquery 允许你构建预定义规则来搜索此类功能。许多 EDR 产品提供类似的功能。Osquery 提供的价值包括其可定制性、可扩展性选项、通用语言的使用以及行业支持。

为了使 Osquery 能够运行，组织必须控制网络上的系统，包括拥有管理权限并有能力安装软件。组织通常使用编排工具（如 Ansible、Puppet 和 Chef）来推送和部署 Osquery，这使得 Osquery 成为一个很棒的用例，可以用你的 Ansible 实验室来理解和测试。Osquery 可以提供事件信息，例如系统上新建的账户、登录失败事件、文件创建以及正在运行的进程。然而，Osquery 可见性的真正力量在于将所见内容归类为潜在风险，例如在执行 Excel 文件后启动 PowerShell 时进行标记。接下来，我将演示一个简单的 Osquery 安装，以便你可以将此工具添加到你的实验室中。

> **注意**
