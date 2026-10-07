

# Google Cloud

日志管理

335

我的第一个项目

云存储 (Cloud Storage)

创建存储桶 (Bucket)

存储桶

监控 新

设置

+ 为存储桶命名
名称：my-log-bucket-for-demo

+ 选择存储数据的位置
位置：us（美国境多个区域）
位置类型：多区域 (Multi-region)

+ 为您的数据选择存储分类
默认存储分类：标准 (Standard)

+ 选择如何控制对对象的访问
防止公共访问：开启
访问控制：统一 (Uniform)

+ 选择如何保护对象数据
您的数据始终受到 Cloud Storage 的保护，但您也可以从这些额外的数据保护选项中选择防止数据丢失。请注意，对象版本控制和保留策略无法同时使用。

+ 保护工具
版本控制（用于数据恢复）
适用于已删除或被覆盖的对象。为了最大限度地降低存储版本的成本，我们建议限制每个对象的非当前版本数量，并安排它们在若干天后过期。了解更多

+ 保留策略（用于合规性）
防止存储桶对象在上传后指定的最小持续时间内的被删除或修改。了解更多

| 持续时间 * | 5 年 |
| :--- | :--- |

数据加密

创建 取

图 12.13 – 为日志创建 Cloud Storage 存储桶

在这一步中，我们创建一个存储桶并根据我们的需求指定细节。参考图 12.13，其中我们选择了一个全局唯一的名称：my-log-bucket-for-demo。

2. 接下来，您可以根据需求指定位置，可以是区域性 (Regional) 或多区域 (Multi-region)。

3. 然后，我们设置默认存储分类，选择统一访问控制，最后设置保留策略（最适用于合规性），这是存储日志时满足合规性的最佳选项。您可以按天、小时、月或年指定保留期。在我们的示例中，我们将其设置为 5 天。

4. 接下来，为 Cloud Storage 存储桶配置对象生命周期管理。

![](img/f681dfc12450e3a4c257352b70dbceca_360_0.png)

一旦创建了存储桶，就可以定义对象生命周期规则。然后您可以切换到 LIFECYCLE（生命周期）选项卡，如图 12.14 所示。

5. 接下来，点击 ADD A RULE（添加规则）并指定您的策略。我们将添加规则：60 天后将日志移至 Nearline 存储，120 天后将日志移至 Coldline 存储。

图 12.14 – LIFECYCLE（生命周期）选项卡

# 日志管理

337

![](img/f681dfc12450e3a4c257352b70dbceca_361_0.png)

![](img/f681dfc12450e3a4c257352b70dbceca_361_1.png)

![](img/f681dfc12450e3a4c257352b70dbceca_361_2.png)

![](img/f681dfc12450e3a4c257352b70dbceca_361_3.png)

![](img/f681dfc12450e3a4c257352b70dbceca_361_4.png)

![](img/f681dfc12450e3a4c257352b70dbceca_361_5.png)

![](img/f681dfc12450e3a4c257352b70dbceca_361_6.png)

# my-bucket-for-demo

| 位置 | 存储分类 | 公共访问 | 保护 |
| :--- | :--- | :--- | :--- |
| us（美国境多个区域） | Standard | 非公开 | 保留 5 年 |

| 对象配置 权限 保护 生命周期 可观测性 资源清清单 报告 新 |

* 在您添加了规则后，可能需要长达 24 小时才能生效。

当满足某些条件时，生命周期规则将适用于存储桶的对象。例如，当对象达到特定年龄时将其移动到更低成本的存储分类。了解更多。

* 如果一个对象符合多个规则条件：
- 删除操作优于更改存储分类。
- 将对象更改为更冷存储存储分类优于更改为更少的存储分类。
- 如果同时存在这些规则，则将对象删除到 Archive 存储分类而非 Cloud。

| 规则 | 添加规则 | 删除所有 |
| 动作 | 对象条件 | 适用范围 |
| :--- | :--- | :--- |
| 设置为 Nearline | 对象创建后 30 天 | ✓ |
| 设置为 Coldline | 对象创建后 120 天 | ✓ |

图 12.15 - 为生命周期管理添加规则

图 12.15 展示了一旦您定义了标准，您的规则将是什么样子。

6. 为所有 Google Cloud 服务开启审核日志。

使用以下内容，您可以为所有服务开启审核日志：

```json
{
  "auditConfigs": [
    {
      "service": "allServices",
      "auditConfigs": [
        { "logType": "ADMIN_READ"},
        { "logType": "DATA_READ"},
        { "logType": "DATA_WRITE" }
      ]
    }
  ]
}
```

# Cloud Logging（云日志）

7. 配置日志导出。

接下来，我们创建聚合导出，并精细调整对审核日志数据、虚拟机数据、存储数据和数据库数据的导出。还存在管理员活动日志和数据访问日志，以及某些特定类型资源的日志：

```sql
logName:"logs/cloudaudit.googleapis.com" OR
resource.type=gcs_bucket OR
resource.type=gcs_bucket OR
resource.type=cloudsql_database OR
resource.type=bigquery_resource
```

您可以使用 Google Cloud CLI 或 Cloud 控制台来创建接收器（sink）。我们之前查看了使用控制台配置接收器和限制性过滤器的选项。现在，我们将查看 Google Cloud CLI 版本，以演示如何创建接收器和过滤器：

```bash
gcloud logging sinks create gcp_logging_sink_gcs \
  storage.googleapis.com/gcp-logging-export-001000011000 \
  --filter='logName: "/logs/cloudaudit.googleapis.com" OR \
  resource.type=gce OR \
  resource.type=gcs_bucket OR \
  resource.type=cloudsql_database OR \
  resource.type=bigquery_resource' \
  --include-children
```

8. 为存储桶设置 IAM 策略和权限。

现在我们将为日志导出添加存储服务账户权限：

- 在控制台中，打开**存储桶**。
- 选择 **my-bucket-for-demo** 存储桶。
- 点击**显示信息面板**，然后选择*存储创建者*(Storage Creator)*权限。

您现在已成功为具有生命周期规则的 Cloud Storage 创建了日志导出。

# 日志合规性

日志合规性是一个重要主题，我们将简要讨论它与认证的相关性。确保日志是集中存储的、安全的，并且仅允许正确的资源访问（通过应用最小权限）。以下是实现合规性的某些方法。

# 职责分离：

- 将聚合导出到由另一个团队拥有的项目
- 归档建议使用 Cloud Storage

# 最小权限：

- 在项目上授予所需的最小权限，使用户无法删除日志
- 强制执行存储桶策略（有效禁用对象级权限）

# 不可否认性：

- 对于 Cloud Storage，配置存储桶锁定（Bucket Lock）以确保存储桶内对象的保留。这防止在所有对象到达保留期之前任何人删除存储桶或底层对象。
- 此外，为存储桶启用版本控制。

Google Cloud 提供了一套解决方案，确保组织的日志安全、受监控并符合行业法规。

# 日志和审计的最佳实践

在本节中，我们将涵盖一些日志和审计的最佳实践。从考试的角度来说，您不会针对这些实践进行直接测试，但可能会发现对它们的间接引用。由于数据访问审核日志默认未启用，因此检查并启用相关服务的数据访问审核日志非常重要。

> 注意
有关如何启用这些日志的更多信息请访问 https://packt.link/w0ZWY。

让我们来看看日志审计的最佳实践：

- 确保指定正确的日志存储目标——Google Cloud Storage 用于归档和保留，BigQuery 用于分析和取证。
- 为日志访问配置适当的权限
- 确保在存储日志之前剥离敏感数据

