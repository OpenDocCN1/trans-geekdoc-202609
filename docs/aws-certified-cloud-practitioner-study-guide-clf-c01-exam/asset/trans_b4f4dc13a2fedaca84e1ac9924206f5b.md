
17. “数据量未正确备份”的示例属于以下受信任顾问类别中的哪一个？

     1. `容错性`

     2. `性能`

     3. `安全性`

     4. `成本优化`

18. 运行（主要）空闲的实例应由以下哪个受信任顾问类别识别？

     1. `性能`

     2. `成本优化`

     3. `服务限制`

     4. `复制`

19. 在受信任顾问的上下文中，什么是假阳性？

     1. 一个实际有意的服务状态的警报

     2. 一个显示为绿色 OK 图标的服务状态，但该状态已失败或正在失败

     3. 一个单一的状态图标，指示您的账户完全合规

     4. 文本形式的失败状态指示

20. 下列受信任顾问警报仅适用于企业支持计划或企业支持计划的账户（选择两项）：

     1. `根账户启用 MFA`

     2. `负载均衡器优化`

     3. `服务限制`

     4. `IAM 访问密钥轮换`

# 第 4 章  

## 理解 AWS 环境

**本章涵盖的 AWS 认证云实践考试目标包括，但不限于，以下内容：**

*   `域 2：安全性`

*   `![images](images/correction.png) 3.2 定义 AWS 全球基础设施`

![images](images/clogo.jpg) 

## 介绍

您如何使用 AWS 服务来部署云工作负载，很大程度上取决于 AWS 本身如何组织其硬件、网络和安全基础设施。因此，最有效、最具成本效益的配置方式是深入了解 AWS 基础设施的具体运作方式。

本章将帮助您在脑海中描绘 AWS 环境的“地形”。您将了解 Amazon 全球分布的数百个数据中心是如何被划分为区域（region），再进一步细分为可用区（Availability Zone）。您还将学习如何设计自己的应用，以充分利用这些划分。

此外，您还将了解 AWS 如何通过其全球分布的边缘位置（edge locations）扩展应用的网络覆盖范围，这些位置构成了 CloudFront（Amazon 内容分发网络，CDN）的前端。最后，您将了解使用和依赖 Amazon 资源的方式受 AWS 共享责任模型（AWS Shared Responsibility Model）和 AWS 接受使用政策（AWS Acceptable Use Policy）的约束。未能正确理解这两个框架，最轻的后果是导致昂贵的错误，最严重的后果则可能是灾难性的。

## AWS 全球基础设施：AWS 区域

AWS 通过数十万台服务器在广泛分布的地理区域内的物理数据中心中提供云服务。随着 Amazon 全球布局的扩展，区域的数量也随之增长。您很快会看到，拥有更多区域选择是云计算的一项宝贵特性。

截至本文撰写时，[表 4.1](#c04.xhtml#table4-1) 列出了当前可用的全部区域。但到您阅读本文时，可能已经有更多区域推出。最新的信息请参阅文档页面 [https://aws.amazon.com/about-aws/global-infrastructure](https://aws.amazon.com/about-aws/global-infrastructure)。

[**TABLE 4.1**](#c04.xhtml#tableanchor4-1) 当前 AWS 区域及其设计ations 列表

| 区域 | 设计ation |
| --- | --- |
| US West (Oregon) 区域 | `us-west-2` |
| --- | --- |
| US West (N. California) 区域 | `us-west-1` |
| US East (Ohio) 区域 | `us-east-2` |
| US East (N. Virginia) 区域 | `us-east-1` |
| Asia Pacific (Mumbai) 区域 | `ap-south-1` |
| Asia Pacific (Osaka-Local) | `ap-northeast-3` |
| Asia Pacific (Seoul) 区域 | `ap-northeast-2` |
| Asia Pacific (Singapore) 区域 | `ap-southeast-1` |
| Asia Pacific (Sydney) 区域 | `ap-southeast-2` |
| Asia Pacific (Tokyo) 区域 | `ap-northeast-1` |
| Canada (Central) 区域 | `ca-central-1` |
| China (Beijing) 区域 | `cn-north-1` |
| EU (Frankfurt) 区域 | `eu-central-1` |
| EU (Ireland) 区域 | `eu-west-1` |
| EU (London) 区域 | `eu-west-2` |
| EU (Paris) 区域 | `eu-west-3` |
| South America (São Paulo) 区域 | `sa-east-1` |
| AWS GovCloud (US) | `us-gov-west-1` |

并非所有这些区域都可从普通 AWS 账户访问。将资源部署到政府云（GovCloud）区域（或专为美国情报机构设计的秘密区域）需要特殊权限。

### 区域基于服务

当您请求 AWS 服务的实例时，该实例的底层硬件将仅来自一个区域中的单一服务器。无论是 EC2 虚拟机实例、其 EBS 存储卷、S3 桶，还是 Lambda “无服务器”函数，这些资源的物理主机都只能位于一个区域内。虽然任何人都可以访问您的资源，但其底层物理主机最多只能位于一个区域。

当然，这并不意味着您不能在多个区域并行运行资源，或在某些特例中这样做是合理的。但您必须始终知道正在规划的资源所在的区域。

我们在此强调这一点，因为如果忽略它很容易造成麻烦。由于 AWS 设计者的无意，如果不小心启动新资源到错误的区域，可能导致相互依赖的应用组件无法找到彼此，从而使应用失败。这类误操也会使跟踪运行的资源变得困难，导致因未关闭的闲置实例而产生不必要的费用。正如第 2 章 “了解您的 AWS 账户” 中所述，Billing & Cost Management Dashboard 可以提供有用的洞察。

检查当前区域应成为一种第二 nature 的反射，就像驾车时我们希望定期进行的快速镜子检查一样。[Figure 4.1](#c04.xhtml#figure4-1) 展示了 AWS Management Console 页面右上角如何显示当前活动区域，以及如何通过下拉菜单轻松切换到其他可用区域。

![FIGURE 4.1 AWS Management Console 显示当前活动区域并允许切换到其他可用区域的功能] (images/c04f001.jpg)

[**FIGURE 4.1**](#c04.xhtml#figureanchor4-1) AWS Management Console 显示当前活动区域并允许切换到其他可用区域的功能

这对您有什么意义？在区域之间划分资源可以让您：

*   将基础设施地理位置更靠近用户，从而实现最低延迟访问

*   将基础设施放置在国家边界内，以满足法规合规性（如法律和银行规则）

*   隔离资源组，使其与更大网络分离，提升安全性

### 全局基于服务

请记住我们前面提到的那个绝对、不可变、根本的法则：所有 AWS 资源都只能存在于一个区域内。这一点确实是绝对、不可变且根本真实的。

不过，情况并非总如此。

