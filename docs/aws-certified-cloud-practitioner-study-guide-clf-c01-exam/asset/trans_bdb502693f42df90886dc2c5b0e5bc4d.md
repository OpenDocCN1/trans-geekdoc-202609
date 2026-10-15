
同样，您可以在 Amazon 的 Relational Database Service (RDS) 下，以任何组合运行轻量级关系型数据库工作负载，每月最多可使用 750 小时，并且可以在 Simple Storage Service (S3) 桶中存储最高 5 GB 的数据。

如果您在任何时刻超过限额，您将按照正常的 AWS 计费费率为超出部分进行计费。为了让您了解实际费用，Free Tier–eligible t2.micro 实例（使用 Linux）在 EC2 上运行于美国东部区域，如果在一个月内使用 850 小时，仅需 $1.16 USD（$0.0116/小时）即可。这是因为您只需为超过 Free Tier 最大值的使用小时数进行计费。

### 监控您的 Free Tier 使用量

当然，不小心让 AWS 资源一直运行——无论是否在使用 Free Tier——都可能花费您远超过 $1.16 的费用。启动一个同步复制的 RDS 数据库实例来测试您新网站的后端，然后忘记它，可能会让您每月花费数千美元。您一定要时刻关注账户。

在本章后面，我们将在讨论成本管理时，向您展示更多关于如何解决此问题的方法。但目前，我们将向您展示两种专门针对 Free Tier 限额的使用监控方式。

第一种方法仅需等待电子邮件消息的到达即可。默认情况下，Free Tier 相关的电子邮件警报会在账户活动接近或已超过 Free Tier 限额时自动发送。除了在 Billing Dashboard（位于 AWS 管理控制台）的 Preferences 页面上关闭这些提醒外，您能做的唯一事情是选择一个不同的电子邮件地址。您可以通过控制台右上角的账户下拉菜单（如图 2.1 所示）访问 Billing Dashboard。

![FIGURE 2.1 The account drop-down menu that includes a link to your Billing Dashboard](images/c02f001.jpg)

[**FIGURE 2.1**](#c02.xhtml#figureanchor2-1) 账户下拉菜单包含指向您 Billing Dashboard 的链接

第二种监控工具会在 Billing Dashboard 的底部出现，适用于任何仍处于 Free Tier 资格的账户。图 2.2 展示了该工具的外观。该账户中使用最频繁的服务目前并不活跃，但您可以看到 Amazon S3 *存储*（当前仅占 0.06%）是被跟踪的多个使用指标之一；此外，S3 桶的 Put 和 Get 请求的数量也有各自的限额。

![FIGURE 2.2 The Free Tier usage tracking table displaying an account’s busiest AWS services](images/c02f002.jpg)

[**FIGURE 2.2**](#c02.xhtml#figureanchor2-2) 显示账户中使用最频繁 AWS 服务的 Free Tier 使用量跟踪表

点击 **View All** 按钮将带您到当前所有 Free Tier 使用情况的页面。即使您目前对账户的使用不多，也可能会惊讶于背后已经发生了多少活动。不过请放心，这只是几条监控通知在来回传递。

![](images/note.jpg) 在您主动启动服务之前，不会发生会产生可计费事件的情况。

### 免费服务有哪些？

实际上有两类免费服务：

*   新 AWS 账户的首 12 个月内，大多数 AWS 服务的轻量实现形式

*   对于某些 AWS 服务，即使超过首 12 个月，仍然始终可用的轻量使用

您可以在 [https://aws.amazon.com/free](https://aws.amazon.com/free) 获取这两类服务的详细清单。为了让您对可用内容有初步了解，以下是一些亮点。

#### 12 个月免费服务

我们已经讨论了在 Free Tier 下运行低功耗 EC2 和 RDS 实例以及使用 5 GB S3 存储的情况。其他免费服务特性还包括：

*   30 GB 磁盘或固态盘（SSD）卷的 Amazon Elastic Block Storage (EBS)。EBS 卷通常作为 EC2 实例的主数据盘。以 8 GB 为例，这足以运行驱动繁忙的 Web 服务器的 Linux 系统。

*   每月 500 MB 的 Amazon Elastic Container Registry (ECR) 免费存储。ECR 用于存储和管理 Docker 容器镜像。500 MB 足以满足几乎所有使用场景的需求。

*   50 GB 的出站数据传输和 200 万次 HTTP 或 HTTPS 请求的 Amazon CloudFront 分发。这些是年度而非月度额度。CloudFront 是 Amazon 的内容分发网络，可用于以低延迟向远程用户提供缓存内容。

*   每月 100 万次 API 调用的 Amazon API Gateway。API Gateway 是管理组织 API 的工具，API 让用户和应用能够与移动或 Web 资源进行连接。

#### 永久免费服务

即使消耗量如此低以至于不需要计费，某些 AWS 服务仍可持续使用。AWS 会在任何时间段内提供这些低消耗水平的服务。常见的使用场景包括：

*   在 Amazon CloudWatch 中最多可有 10 个自定义监控指标和 10 个告警同时处于活动状态。您可以直接使用 CloudWatch，或将其与其他工具结合，以监控资源性能和成本。

*   每月 10 GB 从 Amazon Glacier 中检索的数据。Glacier 是一种低成本的长期存储服务，适合不常需要快速访问数据的场景。

*   使用 Amazon Simple Email Service (SES) 每月最多发送 62,000 封邮件。SES 是面向大规模发送邮件的企业级邮件服务。

*   AWS Lambda 每月 100 万次请求和 320 万秒的计算时间。Lambda 让您在响应网络触发时运行代码，无需自行管理底层服务器基础设施。

关于 Free Tier 的另一条注意：AWS Free Tier 优惠不适用于在 GovCloud (US) 区域或通过 AWS Organizations 成员账户创建的资源。（本章后面将介绍 AWS Organizations。）

## 产品定价

在规划、启动和管理 AWS 部署时，保持组织预算内将是您需要投入大量精力的任务。您需要了解每项服务的计费方式，并知道如何快速获取准确的定价信息。

### 查找 AWS 定价文档

我们很快将深入说明如何获取准确的定价信息，但现在我们可以帮助您立即获得这些信息。每项 AWS 服务都有专门的定价页面。例如，S3 服务的概览网址是 [https://aws.amazon.com/s3](https://aws.amazon.com/s3)，要进入定价页面，只需在网址后加上斜杠和 "pricing"，即 [https://aws.amazon.com/s3/pricing](https://aws.amazon.com/s3/pricing)。

在页面上，您会看到易于阅读的表格，列出了按小时、按月或其他适当计量单位计费的价格级别。定价会因 AWS 区域而异，通常会有下拉菜单让您仅查看所需的细节。

