
# 使用简单通知服务的通知

`Simple Notification Service` (SNS) 允许应用程序、用户和设备从 AWS 发送和接收通知。SNS 使用发布-订阅模型，其中发布者（例如 AWS 服务）生成通知，订阅者（例如终端用户）接收它。SNS 用来映射发布者和订阅者的通信通道称为 `topic`。SNS 可以通过多种协议向订阅者发送通知，包括以下内容：

* `HTTP(S)`
* `Simple Queue Service (SQS)`
* `Lambda`
* `移动推送通知`
* `Email`
* `Email-JSON`
* `短信服务 (SMS)` 文本消息

# 自动扩展操作

通过指定 EC2 自动扩展操作，EC2 自动扩展服务可以根据需求的变化添加或删除 EC2 实例。例如，如果一个指标显示实例过载，您可以让 EC2 自动扩展通过添加更多实例来响应。

# EC2 操作

如果您正在监控出现问题的特定实例，您可以使用 EC2 操作来停止、终止或恢复该实例。恢复实例会将实例迁移到新的 EC2 主机，这在出现物理硬件问题时可能是必须的。

## CloudWatch Dashboards

CloudWatch Dashboards 是您的一站式商店，用于监控所有重要指标。您可以创建多个仪表板，并向其中添加指标图表、指标的最新值以及 CloudWatch 警报。您可以保存仪表板以供将来使用，并与他人共享。仪表板还可以可视化多个 AWS 区域的指标，因此您可以监控基础设施的全局健康状况。请查看 [Figure 6.17](#c06.xhtml#figure6-17) 查看示例 CloudWatch 仪表板。

![FIGURE 6.17 A CloudWatch dashboard ](images/c06f017.jpg)

[**FIGURE 6.17**](#c06.xhtml#figureanchor6-17) A CloudWatch dashboard 

## CloudWatch Logs

CloudWatch Logs 收集并存储来自 AWS 和非 AWS 来源的日志文件，并使其轻松查看、搜索和从中提取自定义指标。

### 日志事件、流和组

您可以配置您的应用程序和 AWS 服务发送日志事件到 CloudWatch Logs。日志事件类似于日志文件中的一行，始终包含时间戳和事件消息。许多 AWS 服务会生成自己的日志，称为 `vended logs`，您可以将这些日志流式传输到 CloudWatch Logs。这些日志包括 Route 53 DNS 查询日志、VPC 流量日志和 CloudTrail 日志。CloudWatch Logs 还可以接收来自您的应用程序的自定义日志，例如 Web 服务器访问日志。

CloudWatch Logs 通过将来自同一来源的日志事件存储在同一个日志流中来组织日志事件。例如，特定 EC2 实例的 Web 服务器访问日志会存储在一个日志流中，而 Route 53 DNS 查询日志则存储在另一个日志流中。

CloudWatch 进一步通过将日志流组织到日志组来实现进一步的组织。为了组织相关的日志流，您可以将它们放入同一个日志组中。例如，如果您有多个日志流收集来自多台 Web 服务器的 Web 服务器日志事件，您可以将所有这些日志流放入一个日志组中。

CloudWatch Logs 默认无限期存储日志事件，但您可以配置日志组的保留设置来自动删除事件。保留设置范围从 1 天到 10 年。您也可以通过将日志导出到 S3 桶来存档日志。

### 指标过滤器

指标过滤器从日志组中的日志事件中提取数据并将其存储为自定义 CloudWatch 指标。例如，假设数据库服务器的日志事件包含查询运行的时间（毫秒），您可以提取该值并将其作为 CloudWatch 指标存储，以便绘制图表并创建警报，当其超过特定阈值时发送通知。

您也可以使用指标过滤器来跟踪特定字符串出现的次数。这对于统计日志中特定事件（如错误代码）出现的次数很有用。例如，您可能想跟踪 403 Forbidden 错误在 Web 服务器日志中出现的次数。您可以配置指标过滤器在给定时间段（例如五分钟）内统计该错误的出现次数，并将该值记录到 CloudWatch 自定义指标中。

![Metric filters let you extract or derive quantitative data from log events, so metric values will always be numeric. You can’t store a non-numeric string such as an IP address in a metric.](images/note.jpg) Metric filters let you extract or derive quantitative data from log events, so metric values will always be numeric. You can’t store a non-numeric string such as an IP address in a metric.

### CloudWatch Events

CloudWatch Events 让您能够持续监控代表 AWS 资源变更的特定事件（特别是只写 API 操作），并在发生时采取行动。例如，EC2 实例从运行状态转到停止状态的事件就是一个事件。IAM 用户登录 AWS 管理控制台也是一个事件。CloudWatch Events 可以自动且立即响应这些事件。

您首先创建一个规则，以定义要监控的事件以及在响应这些事件时要执行的操作。您通过选择目标来定义要执行的操作，目标是 AWS 资源。可选的目标包括以下内容：

* `Lambda` 函数
* `EC2` 实例
* `SQS` 队列
* `SNS` 主题
* `ECS` 任务

CloudWatch 实时响应事件，即时生效。与 CloudWatch 警报不同，后者在指标跨越并保持跨越数值阈值时才采取行动，CloudWatch 事件在发生时立即触发。例如，您可以创建一个 CloudWatch 事件，当 EC2 实例终止时发送 SNS 通知。或者，您可以在 S3 桶收到图像文件时触发 Lambda 函数来处理该文件。

或者，您可以创建一个计划，在定期间隔内自动执行操作。例如，为了节省费用，您可以创建一个计划，在每天下午 7 点关闭开发实例，此时开发人员理想情况下已经停止工作。

## CloudTrail

CloudTrail 记录对 AWS 资源的每项操作的详细事件日志。CloudTrail 记录的每个事件都包含以下参数：

* 服务。具体指服务的全局终端地址，例如 IAM 的 `iam.amazonaws.com`。
* 执行的 API 操作名称，例如 `RunInstances`、`CreateUser` 或 `PutObject`。
* 资源所在的区域。对于全局服务，这总是 `us-east-1`。
* 响应元素。对于修改或创建资源的 API 操作，此字段包含操作结果信息。例如，`RunInstances` 操作启动 EC2 实例的响应元素会包含实例 ID 和私有 IP 地址等信息。
* 发起请求的主体。这可能包括主体类型（IAM 用户或角色）、其 Amazon 资源名称 (ARN) 和名称。
* 请求的日期和时间，以协调世界时 (UTC) 表示。
* 请求者的 IP 地址。

### API 和非 API 事件

CloudTrail 记录的事件分为两种操作：API 操作和非 API 操作。API 操作包括启动实例、创建 S3 桶、创建新 IAM 用户或拍摄 EBS 快照等。需要注意的是，术语 *API action* 与操作的执行方式无关。例如，无论通过 AWS 管理控制台、AWS 命令行工具还是 AWS 软件开发套件，终止 EC2 实例都是 API 事件。

非 API 操作包括其他所有操作，例如登录管理控制台。

### 管理事件和数据事件

CloudTrail 还将事件分为管理事件和数据事件两个维度。

