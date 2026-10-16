
-   [使用无服务器设计的另一种方法](https://example.org) 这可能意味着仅使用函数而非虚拟化应用。没有应用。没有容器。没有操作系统。只有一个函数。这并不消除整体应用被入侵的潜在风险。请记住，攻击者的目标不总是，甚至通常也不是 shell 访问，尽管这是常见的误解。他们传统上（即很久以前）的工作方式是这样。今天，攻击者可能只是在寻找可以出售的数据。这意味着对数据的访问，无论是通过利用应用漏洞获得的非授权访问，还是通过 stolen credentials 获得的授权访问。函数无法防止这种类型的攻击。函数可以让获得系统级别的入侵变得更加困难，但无法阻止应用或数据访问。

服务器无函数是事件驱动的，这意味着没有单一的应用决定哪个函数会被调用。相反，调用函数可能更容易触发，因为它取决于事件。其中一个事件可能是整体应用使用发布/订阅模型。整个应用有一个事件总线。函数通过发布消息到总线来发送。其他函数可以通过订阅来接收消息。如果一个服务器无函数订阅的消息被放到总线上，该函数就会被调用。另一种触发服务器无函数的方式是使用 HTTP 方法，如 GET、POST、PUT 或 DELETE。当整体 Web 应用收到这些 HTTP 请求时，服务器无函数可能会被调用。此外，某些特定的 HTTP 头部的存在也可能导致函数被调用。

由于可能有大量服务在运行，每个都能在消息总线上发布方法，因此获取这些函数的调用方式可能有很多种。这实际上扩大了攻击面，因为可能没有单一的入口点来针对潜在的脆弱代码。这些多个入口点也可能导致认证问题。与其依赖整体应用进行认证，每个函数都必须假设请求可能直接到达该函数，而无需经过任何认证。

尽管服务器无函数可能不让攻击者轻易获得底层操作系统的访问，但 OWASP Top 10 漏洞列表中的风险仍然适用。这尤其适用于配置错误或弱第三方组件导致的漏洞。即使使用云原生设计、微服务和无服务器基础设施，敏感数据仍可能被暴露。

### 部署

目前的部署通常是自动化的。无论目标是 VMware ESXi 服务器上的虚拟机，还是 Microsoft Hyper‑V 服务器，亦或是云提供商的容器，系统资产的部署都可以自动化。虽然自动化的实现方式各有不同，但常见的做法是使用编排平台。使用编排系统通常被称为 *infrastructure as code*（IaC），因为部署是通过脚本语言或客户端‑服务器软件以及定义部署的配置文件来完成。

Ansible 是常用的 IaC 软件包之一。它使用一个存放配置文件的服务器以及一个可在运行系统中执行额外配置的软件代理。下面的示例展示了 Ansible 在 VMware ESXi 服务器上创建现有模板的新实例。Ansible 服务器通过在指定地址使用的凭据与 VMware 服务器通信，并发送命令让模板克隆，从而创建一个新的 Web 服务器实例。这里展示的配置文件采用 Yet Another Markup Language（YAML）格式，这与 Salt 等类似软件包也常用。虽然此示例展示了在 VMware 服务器上创建虚拟机，但你可以使用任何云提供商执行类似操作。

**Salt 配置**

```
- name: Clone existing template
  hosts: localhost
  connection: local
  gather_facts: no
  tasks:
  - name: Create new instance of web server
    vmware_guest:
      hostname: 192.168.3.5
      username: root@192.168.3.5
      password: P4$$w0rd!
      validate_certs: False
      name: webserver_vm
      template: webserver_template
      datacenter: DC1
      folder: /VMs/templates
      state: poweredon
      wait_for_ip_address: yes
```

创建任何虚拟资源实例的另一种方法是使用脚本语言。其中一种是 Terraform，它是用于以代码方式构建环境的语言。从名字就能看出其含义——转换环境。它常在科幻作品中出现，用于把其他星球改造成类似地球或更适合人类居住的环境。不过，你不必局限于 Terraform 这种特定语言。也可以使用通用语言如 PowerShell。下面的示例演示了如何在 Microsoft Azure 中创建虚拟机实例：

```
$resourceGroup = "OurGroup"
$location = "westus"
$adminName = "powershell-user"
$adminPass = "P4$$w0rd!"
$dnsName = Read-Host -Prompt "DNS name for the IP"
 
New-AzResourceGroup -Name $resourceGroup -Location "$location"
New-AzResourceGroupDeployment `
    -ResourceGroupName $resourceGroup `
    -TemplateUri "https://myhost.onmicrosoft.com/azuretemplate.json" `
    -adminUsername $adminUser`
    -adminPassword $adminPass `
    -dnsLabelPrefix $dnsName
 
 (Get-AzVm -ResourceGroupName $resourceGroup).name
```

此代码示例需要 Azure PowerShell 模块。你也可以在 Azure Cloud Shell 中运行此代码，它提供了 PowerShell 界面，用于向 Azure 发送程序化命令。这并不意味着你必须使用 Azure 才能执行程序化功能。其他大型云提供商，如 Amazon 和 Google，也提供类似的功能，包括对其 API 的命令行接口。这些是可以在本地机器上安装的软件包，让你能够使用可能被脚本化的命令直接向所选云提供商发送请求。

在 PowerShell 示例中，你可能注意到有一个模板的引用。这是一个可以在 Azure 中创建并使用 JavaScript Object Notation（JSON）格式存储的配置文件。脚本中引用的就是一个 JSON 文件，它可能是在 Azure 中构建虚拟机时生成的。当你完成所有想要的设置（包括磁盘和内存大小以及想要使用的操作系统）后，可以将配置保存为 JSON 文件，以便以后每次需要创建相同设置的新实例时直接使用。