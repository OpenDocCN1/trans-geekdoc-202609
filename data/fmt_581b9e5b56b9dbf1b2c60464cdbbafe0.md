
- 请求类型（Request Type）——当你从“请求实例”页面配置请求时，系统会提供三种请求类型：请求（Request，一次性实例请求）、请求并维护（Request And Maintain，使用阵队维护目标容量）以及按时长预留（Reserve For Duration，请求持续六小时或数月的无间断实例）。

你可以从 EC2 控制板配置你的竞价实例请求。使用“请求实例”页面设置详细信息，例如你的总容量（你运行的最大实例数或 vCPUs）、你启动的 AMI 和实例类型、你是否需要负载均衡，以及你希望在启动时传递给实例的任何用户数据。

你可以通过使用你为任务构建的私有 AMI 或通过传递数据来定义你的工作流。

竞价实例建议器（Spot Advisor）可以帮助你根据需求推荐合适的配置。竞价实例建议器（位于 EC2 控制板中）可以帮助你找到合适的配置。

为什么不使用 AWS CLI 配合一个 `Config.json` 文件来请求竞价实例阵队呢？

# 练习 12.3 使用 AWS CLI 请求竞价实例阵队

1. 创建一个名为 `Config.json` 的文件，内容如下：

```json
{
  "SpotPrice": "0.04",
  "TargetCapacity": 2,
  "IamFleetRole": "arn:aws:iam::123456789012:role/my-fleet-role",
  "LaunchSpecifications": [
    {
      "ImageId": "ami-1a2b3c4d",
      "SecurityGroups": [
        {"GroupId": "sg-1a2b3c4d"}
      ],
      "InstanceType": "t2-micro",
      "SubnetId": "subnet-1a2b3c4d,subnet-3c4d5e6"
    }
  ]
}
```

现在运行指向你创建的 `Config.json` 文件的命令：

`aws ec2 request-spot-fleet --spot-fleet-request-config file://Config.json`

AWS CLI 可能会报错，请仔细阅读信息并找出问题所在。当命令返回类似输出示例的竞价阵队 ID 时，你就知道成功了：

```json
{
  "SpotFleetRequestId": "sfr-6b8225fe-b6d2-4c58-94d7-d14fdd787be"
}
```

# 练习 12.3（续）

9. 仅凭该 ID 并不能证明一切运行正常。你应该前往 EC2 控制板的竞价页面，选择你的阵队条目。点击页面下半部分的“历史”选项卡并查看消息。纠正可能出现的错误，并在必要时取消请求并使用修正后的配置重新启动。

10. 在完成任务后，不要忘记关闭你的资源。

# 自动缩放

你已经学习了如何使用自动缩放高效地扩展计算资源以满足需求。但不要忘记，自动缩放也应该缩小。你可以使用自动缩放来寻找最有效的配置。

# 块存储生命周期管理器

附加到 EC2 的 EBS 卷受到 Lifecycle Manager 的良好保护。管理器（通过控制台访问）允许你创建策略来保留新的快照。

## 总结

可以在账户使用量接近阈值时创建 AWS 预算以触发警报。你可以使用成本分配标签来关注资源子集。你可以使用成本分析器（Cost Explorer）和成本与使用报告（Cost and Usage Reports）跟踪历史账单、费率和产品属性。然而，报告是为大数据分析设计的。

### 复习题

1. 下列哪项最符合 AWS 免费层（Free Tier）？

A. 新账户第一个月可以免费访问 AWS 服务

B. 新账户可以免费访问所有类型的 AWS EC2 实例

C. 新账户第一年可以免费访问 AWS 基础级别的的服务

D. 大多数 AWS 服务的“免费层”是无限且开放的

2. 下列哪种存储类型提供了最廉价的存储和传输率？

A. Amazon Glacier

B. Amazon S3 Standard-Infrequent Access

C. Amazon S3 Standard

D. Amazon S3 One Zone-Infrequent Access

3. 哪种 AWS 服务最适合通过发送电子邮件警报来控制您的？

A. Cost Explorer

B. Budgets

C. Organizations

D. TCO Calculator

4. 哪种 AWS 服务最适合大规模分析账户使用数据？

A. Trusted Advisor

B. Cost Explorer

C. Budgets

D. Cost and Usage Reports

5. 您的公司想要紧密协调其多个 AWS 账户的管理，AWS Organizations 可以帮助其实现这一点。这将如何改变您的安全状况？（选择三项）。

A. 组织级管理账户分支可能会产生更大的损害。

B. 可以在组织级别上集中控制用户权限。

C. 您应该升级到仅使用特殊加固的组织级 VPC。

D. 使用 MFA 和强密码的标准安全最佳实践变得更加本质。

6. 下列哪些资源状态受 AWS Trusted Advisor 监控？（选择两项）。

A. Route 53 路由失败

B. 正在运行但空闲的 EC2 实例

C. 开放权限的 S3 桶

D. 允许 root 账户 SSH 访问的 EC2 Linux实例

# 复习题 291

7. 您正在计划一次新的 AWS 部署，您的团队正在讨论使用 RDS 数据库还是运行在 EC2 实例上的数据库更好。以下哪些工具将最有帮助？

A. TCO Calculator

B. Simple Monthly Calculator

C. Trusted Advisor

D. Cost and Usage Reports

8. 下列哪项不是您可以配置 AWS 预算进行跟踪的指标？

A. EBS卷容量

B. 资源使用情况

C. 预留实例覆盖率

D. 资源成本

9. 下列哪些关于成本分配标签（cost allocation tags）的描述是正确的？（选择两项。）

A. 标签可能需要 24 小时才会出现在成本管理仪表板中。

B. 标签无法应用于标签创建之前启动的资源。

C. 每个账户允许五个预算。

D. 您可以从标签编辑器页面激活并管理成本分配标签。

10. 您的在线商店通常需要三个 EC2 实例来处理流量，但在夏季两个月的负载会翻倍。以下哪种方法最合理？

A. 每年运行 12 个月三个按需实例，并为夏季预留六个预留实例。

B. 夏季内运行三个竞价实例，并每年运行 12 个月三个预留实例。

C. 每年运行 12 个月九个预留实例。

D. 每年运行 12 个月三个预留实例，并为夏季预留六个预留实例。

11. 在配置预留实例时，您**不需要**提供以下哪些设置？

A. 支付选项

B. 标准或可转换 RI

C. 中断策略

D. 租用类型

12. 在配置预留实例时，以下哪种支付选项最贵？

A. 全额预付

B. 部分预付

C. 无预付

D. 月付

13. 下列哪些如 Docker 等容器的益处可以显著减少您的 AWS 计算成本？（选择两项）。

A. 容器可以快速启动。

B. 容器可以提高服务器密度。

C. 容器可以轻松可靠地复制服务器环境。

D. 容器运行所需的内存比物理机更少。

14. 下列哪个 EC2 实例使用场景最适合预留实例的用例？

A. 一个将连续运行六个月的应用

B. 一个将连续运行 36 个月的应用程序

C. 一个仅在当地办公时间内运行的应用

D. 一个运行时间不可预测且能够从意外关机的应用程序

15. 下列哪项描述了“匹配特定启动规格的未使用 EC2 实例”？

A. 请求类型

B. 竞价中断

C. 竞价实例 de队

D. 竞价实例池

16. 下列哪项描述了竞价实例中断？

A. 当竞价价格高于您的最高价格时，会发生竞价实例中断。

B. 竞价实例中断是在负载完成时终止竞价实例。

C. 当手动重启竞价请求时，会发生竞价实例中断。

D. 竞价实例中断是 AWS 数据中心临时停机的结果。

17. 下列哪项描述了您想要运行的最大实例或 vCPU？

A. 竞价实例池

B. 目标容量

C. 竞价

D. 最大

18. 下列哪项描述了 Advisor 的功能？

A. 为常用任务提供示例配置

B. 帮助您选择亚马逊镜像 (AMI)

C. 引导您设置 EBS 卷

D. 最大

19. 这些 AWS CLI 命令将启动竞价实例？

A. `aws ec2 request-fleet`

B. `aws ec2 spot-fleet`

C. `aws ec2 launch-fleet`

D. `aws ec2 request-fleet`

20. 下列哪些元素不是您在竞价实例中包含的内容？

A. 可用区

B. 目标容量

C. 平台 (操作系统)

D. AMI

# 第 13 章：卓越运营支柱

在认证解决方案架构师级考试目标中，本章涵盖的范围可能但不限于以下内容：

领域 5：定义卓越运营的架构

- 5.1 选择能够实现卓越运营的设计特性。

## 引言

运营包括保持应用程序顺畅安全运行所需的持续活动。实现卓越运营需要自动化支持组织工作负载、目标和合规要求的某些或全部任务。

自动化的关键是将基础设施和操作定义为代码。与手动任务耗时且容易出错不同，嵌入代码的任务是重复的，并且可以快速执行。跟踪代码也更容易。

在本章中，您将学习如何利用以下 AWS 服务来实现 AWS 资源的部署和操作：

- CloudFormation

- AWS 开发者工具，包括：

  - CodeCommit

  - CodeDeploy

  - CodePipeline

- AWS Systems Manager

# CloudFormation

在第十章“性能效率支柱”中学过，CloudFormation 使用模板让您能够作为代码同时部署、配置和记录您的基础设施。因为 CloudFormation 模板是代码，您可以像存储其他代码一样将它们存储在版本控制库中。由模板定义的资源组成一个栈。创建栈时，必须为它指定一个在账户内唯一的名称。

CloudFormation 的一个优势是您可以使用相同的模板构建多个相同的环境。例如，您可以使用单个模板来定义并部署为应用程序准备两个不同的栈（stack），一个用于生产环境，另一个用于开发环境。

这将确保两个环境尽可能相似。

在本节中，我们将考虑两个模板：`network-stack.json` 和 `web-stack.json`。

要下载这些模板，请访问 https://www.wiley.com/go/sybesttestprep，按照指令登录，然后点击进入本书的资源页面。

# 创建栈

在 CloudFormation 模板中，你可以在模板的 `Resources` 部分定义资源。

我们为每个资源分配了一个称为逻辑 ID（logical ID）的标识符。例如，以下 `network-stack.json` 模板的片段代码定义了一个逻辑 ID 为 `PublicVPC` 的 VPC：

```json
"Resources": {
  "PublicVPC": {
    "Type": "AWS::EC2::VPC",
    "Properties": {
      "EnableDnsSupport": "true",
      "EnableDnsHostnames": "true",
      "CidrBlock": "10.0.0.0/16"
    }
  }
}
```

逻辑 ID（有时也称为逻辑名称）在模板内必须是唯一的。CloudFormation 创建的 VPC 将有一个 VPC ID，例如 `VPC-038049405677fb48`，也称为物理 ID。

CloudFormation 只能从 S3 存储桶读取模板。你可以将模板放在任何地方，但对于 CloudFormation 来说，它们必须位于 S3 存储桶中。要使用存储在 S3 存储桶中的模板创建名为 `Network` 的栈，可以使用以下格式的 AWS 命令行界面 (CLI) 命令：

```
aws cloudformation create-stack --stack-name Network --template-url https://s3.amazonaws.com/cf-templates-c23z8b2yvbmp-us-east-1/network-stack.json
```

你可以可选地在模板中定义参数。参数允许你在创建栈时向栈传递自定义值，而不是将值硬编码到模板中。

例如，与其在创建 VPC 的模板中硬编码无类网间路由 (CIDR) 块，不如你可以定义一个参数，在创建栈时提示输入 CIDR。

> 栈名称和逻辑 ID 是区分大小的。

# 删除栈

你可以从 Web 控制台或 AWS 命令行界面 (CLI) 删除栈。例如，要删除名为 `Network` 的栈，请执行以下命令：

```
aws cloudformation delete-stack --stack-name Network
```

如果栈未启用保护（termination protection），CloudFormation 将立即删除该栈以及其创建的所有资源。

# 使用多个栈

你不需要将所有的 AWS 基础设施都定义在一个栈中。相反，你可以将基础设施拆分到不同的栈中。最佳实践是根据生命周期和所有权来组织栈。例如，网络团队可能会创建一个名为 `Network` 的栈，以为基于 Web 的应用程序定义基础设施。网络基础设施将包括私有虚拟云 (VPC)、子网、互联网网关和路由表。开发团队可能会创建一个名为 `Web` 的栈，以定义运行时环境，包括启动模板、自动扩展组、应用程序负载均衡器、IAM 角色、实例配置文件和安全组。这些团队中的每个团队都可以维护自己的栈。

当使用具有相关资源的多个栈时，将值从一个栈传递到另一个栈是常见的。例如，`Web` 栈中的应用程序负载器需要 `Network` 栈中 VPC 的逻辑 ID。因此，你需要将 VPC 的逻辑 ID 从 `Network` 栈传递到 `Web` 栈。实现此点的有两种方法：使用嵌套栈（nested stacks）和导出栈输出值。

# 嵌套栈

由于 CloudFormation 栈是 AWS 资源，你可以配置模板来创建额外的栈。这些额外的栈被称为嵌套栈，创建它们的栈被称为父栈。为了了解它是如何运作的，我们将考虑 `network-stack.json` 和 `web-stack.json` 模板。

在 `Web` 栈 (`web-stack.json`) 的模板中，你会将 `Network` 栈的模板定义为一个资源，如下片段所示：

```json
"Resources": {
  "NetworkStack": {
    "Type": "AWS::CloudFormation::Stack",
    "Properties": {
      "TemplateURL": "https://s3.amazonaws.com/cf-templates-c23z8b2yvbmp-us-east-1/network-stack.json"
    }
  }
}
```

栈的逻辑 ID 是 `NetworkStack`，`TemplateURL` 指示模板在 S3 中的位置。当你创建 `Web` 栈时，CloudFormation 也会创建 `Network` 栈。

你的嵌套栈模板可以包含一个 `Outputs` 部分，在其中定义你想传递给父栈的值。你可以在父栈的模板中引用这些值。例如，`network-stack.json` 模板定义了一个带有 `VPCID` 和物理 ID 值的输出，如下所示：

```json
"Outputs": {
  "VPCID": {
    "Description": "VPC ID",
    "Value": {
      "Ref": "PublicVPC"
    }
  }
}
```

`Ref` 内置函数返回 VPC 的 ID。父栈 `web-stack.json` 模板可以使用 `Fn::Att` 内置函数引用此值，如 `Resources` 部分所示：

```json
"ALTargetGroup": {
  "Type": "AWS::ElasticLoadBalancingV2::TargetGroup",
  "Properties": {
    "VpcId": { "Fn::Att": ["NetworkStack", "Outputs.VPCID"] }
  }
}
```

按照练习 13.1 中的步骤创建嵌套栈。

# 练习 13.1：创建嵌套栈

在本次练习中，你将创建一个嵌套栈，该栈创建一个 EC2 自动扩展组和支持性基础设施。要完成此练习，你需要知道你正在使用的区域中的 SSH 密钥对名称。

1. 访问 https://www.wiley.com/go/sybesttestprep 并点击 Resources。下载 `web-stack.json` 和 `network-stack.json` 模板。

2. 创建一个 S3 存储桶并上传 `network-stack.json` 模板。

3. 编辑 `web-stack.json` 模板并找到 `NetworkStack` 资源。将 `TemplateURL` 值更改为 S3 中 `network-stack.json` 模板的 URL。

4. 将 `web-stack.json` 模板上传到步骤 2 中使用的 S3 存储桶中。

# 练习 13.1（续）

5. 运行以下 AWS CLI 命令：

```
aws cloudformation create-stack --stack-name Web --template-url [web-stack.json 的 URL] --parameters KeyName=[名称] --capabilities CAPABILITY_IAM
```

6. 为了查看栈，执行以下命令：
