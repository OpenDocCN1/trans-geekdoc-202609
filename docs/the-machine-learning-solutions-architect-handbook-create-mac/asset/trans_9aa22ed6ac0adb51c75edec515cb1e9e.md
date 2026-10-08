

# 使用 Lake Formation 创建数据湖

我们将使用 AWS Lake Formation 构建数据湖架构。登录 AWS 管理控制台后，创建一个名为 `MLSA-DataLake-<你的首字母缩写>` 的 S3 桶。我们将用它作为数据湖的存储介质。如果收到桶名称已被占用的消息，请尝试在名称中添加一些随机字符以确保唯一性。如果您不熟悉如何创建 S3 桶，请按照以下链接中的说明操作：

```
https://docs.aws.amazon.com/AmazonS3/latest/user-guide/create-bucket.html
```

桶创建完成后，按照以下步骤开始创建数据湖：

- **注册 Lake Formation 管理员**：我们需要向数据湖添加 Lake Formation 管理员。管理员将具有全权限管理数据湖的所有方面。要执行此操作，请导航到 Lake Formation 管理控制台，点击 **Admin and data creators**（管理员和数据创建者）链接，点击 **Data lake administrator**（数据湖管理员）部分的 **Grant**（授予）按钮，并将您自己的 IAM 用户 ID 添加到列表中（您当前登录 AWS 管理控制台时使用的用户 ID）。您可以在 AWS 管理控制台横幅的右上部分找到用户 ID。请注意，您需要使用具有管理员权限的用户 ID 登录 AWS 管理控制台以注册新的 Lake Formation 管理员。

- **注册 S3 存储**：接下来我们需要在 Lake Formation 中注册之前创建的 S3 桶（`MLSA-DataLake-<你的首字母缩写>`），以便通过 Lake Formation 进行管理和访问。要执行此操作，点击 **Dashboard**（仪表板）链接，然后点击 **Register Location**（注册位置）。浏览并选择您创建的桶，然后点击 **Register Location**。Lake Formation 将使用此 S3 桶来存储数据库数据并管理其访问权限。

- **创建数据库建立库**：现在，我们准备好为零售客户设置名为 `bank_customer_db` 的数据库。在注册数据库之前，让我们先在 `MLSA-DataLake-<你的首字母缩写>` 桶下创建一个名为 `bank_customer_db` 的文件夹。该文件夹将用于存储与数据库关联的数据文件。要执行此操作，请点击 Lake Formation 仪表板上的 **Create database**（创建数据库）按钮，并按照屏幕上的说明创建数据库。

您已成功创建了一个由 Lake Formation 驱动的数据湖，并创建了一个用于数据管理的数据库。接下来，让我们创建一个数据摄取管道将文件移动到数据湖中。

# 创建数据摄取管道

数据库准备好后，我们现在可以将数据摄取到新数据库中。如前面的节所述，可能有许多不同的数据源，如其他 S3 桶、数据库（例如 Amazon RDS）、流数据（例如社交媒体馈）和日志（CloudTrail）。还有许多用于构建数据摄取管道的不同服务，例如 AWS Glue、Amazon Kinesis 和 AWS Lambda。在本次练习中，我们将构建一个 Amazon Lambda 函数任务，该任务将数据从其他 S3 桶摄取到此新数据库：

- 1. 创建源 S3 桶并下载数据文件：

让我们创建另一个名为 `customer-data-source` 的 S3 桶，代表我们将摄取数据的数据源。现在，从以下链接下载示例数据文件：

https://github.com/PacktPublishing/The-Machine-Learning-Solutions-Architect-Handbook/tree/main/Chapter04/Archive。

然后，将其保存到本地机器。解压压缩文件并将其上传到 `customer-data-source` 桶中。应该有两个文件（`customer_data.csv` 和 `churn_list.csv`）。

- 2. 创建 Lambda 函数：

现在，我们将创建一个 Lambda 函数，将数据从 `customer-data-source` 桶摄取到 `MLSA-DataLake-<你的首字母缩写>` 桶：

- I. 为了开始，导航到 AWS Lambda 管理控制台，点击左侧面板中的 **Functions**（函数）链接，点击右侧面板中的 **Create Function**（创建函数）按钮。选择 **Author from scratch**（从零开始），输入函数名称 `datalake-s3-ingest`，并选择 **Python 3.8** 作为运行时。

- II. 在下一个屏幕，点击 **Add trigger**（添加触发器），选择 **S3** 作为触发器，并选择 **customer-data-source** 桶作为源。对于 **Event Type**（事件类型），选择 **Put** 事件并点击 **Add**（添加）按钮完成此步骤。此触发器将允许发生 S3 桶事件（如向桶中保存文件）时调用 Lambda 函数。

# 机器学习的数据管理

III. 接下来，通过用以下创建代码块替换默认函数模板来创建函数。将 `desBucket` 变量替换为实际的名称：

```python
import json
import boto3
def lambda_handler(event, context):
    s3 = boto3.resource('s3')
    for record in event['Records']:
        srcBucket = record['s3']['bucket']['name']
        srckey = record['s3']['object']['key']
        desBucket = "MLSA-DataLake-your initials"
        desFolder = srckey[0:srckey.find('/') + ""] + srckey
        desKey = "bank_customer_db/" + desFolder
        source = {'Bucket': srcBucket, 'Key': srckey}
        dest = {'Bucket': desBucket, 'Key': desKey}
        s3.meta.client.copy(source, dest)
    return {
        'statusCode': 200,
        'body': json.dumps('files ingested')
    }
```

IV. 新函数还需要 S3 权限来从一个桶复制文件到另一个桶。

- 3. 触发数据摄取：

通过将 `customer_data.csv` 和 `churn_list.csv` 上传到 `customer-data-source` 桶来触发数据摄取，并通过 `MLSA-DataLake-<你的首字母缩写>/bank_customer_db` 文件夹验证该过程。您已成功创建了基于 AWS Lambda 的数据管道，将数据从源 S3 桶移动到目标 S3 桶。接下来，让我们创建一个 AWS Glue Catalog。

# 创建 Glue Catalog

为了允许 `bank_customer_db` 中的数据进行发现和查询，我们需要创建一个目录。在这里我们将使用 AWS Glue Crawler：

- 1. 为 Glue 授予权限：

- I. 首先授予 Glue 访问 `bank_customer_db` 数据库的权限。我们将为 Glue 服务创建一个 IAM 角色。创建一个名为 `AWSGlueServiceRole_data_lake` 的新角色，并附加 AWSGlueServiceRole 和 AmazonS3FullAccess 策略。如果您熟悉如何创建角色和附加策略，请参考以下链接中的说明：https://docs.aws.amazon.com/IAM/latest/

- II. 角色创建后，在 Lake Formation 管理控制台的左侧面板点击 **Data permission**，然后点击右侧的 **Grant**。

- III. 在新的弹出窗口中，选择 `AWSGlueServiceRole_data_lake` 和 `bank_customer_db` 并点击 Grant。

- 2. 配置 Glue 爬虫任务：

通过点击 Lake Formation 管理控制台中的 Crawler 链接启动 Glue 爬虫。一个新的浏览器标签页将打开。点击 **Add Crawler** 开始。输入 `bank_customer_db` 作为爬虫名称并点击 Next。在下一个屏幕上，保持勾选 Data store 和 Crawl all folders。在 Add data store 屏幕上，选择 S3 并在 include path 字段中输入 `s3://MLSA-DataLake-<你的首字母缩写>/bank_customer_db/list/`。

在下一个 Add data store 屏幕上，为 S3 选择 Yes，并输入 `s3://MLSA-DataLake-<你的首字母缩写>/bank_customer_db/data/`。

在 Choose an IAM role 屏幕上，选择 Choose existing IAM role，并选择之前使用的 `AWSGlueServiceRole_data_lake`。

在 Create scheduler for 屏幕上选择 Run on demand 作为频率，然后点击 Finish。

