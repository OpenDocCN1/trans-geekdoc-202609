

![](img/87c29232224b00f5a8bba6a66a391700_227_0.png)

### 图 8.21 – AWS Lambda 创建函数对话框

4. 创建函数后，粘贴以下代码并部署它。向下滚动到“基本设置”，将默认超时更改为更高的值（40 秒），以防止超时错误。您已使用 Amazon Textract 的 analyze_document API，并通过 API 的 FeatureTypes 参数获取表格和表单详细信息：

```python
import boto3
import time
from trp import Document
textract_client = boto3.client('textract')
def lambda_handler(event, context):
    print("- - - Amazon Textract Demo - - -")
    # read the bucket name from the event
    name_of_the_bucket = event['Records'][0]['s3']['bucket']['name']
    # read the object from the event
    name_of_the_doc = event['Records'][0]['s3']['object']['key']
    print(name_of_the_bucket)
    print(name_of_the_doc)
    response = textract_client.analyze_document(Document={'S3Object': {'Bucket': name_of_the_bucket, 'Name': name_of_the_doc}}, FeatureTypes=["TABLES", "FORMS"])
    print(str(response))
    doc = Document(response)
    for page in doc.pages:
        # Print tables
        for table in page.tables:
            for r, row in enumerate(table.rows):
                for c, cell in enumerate(row.cells):
                    print("Table[{}{}][{}{}] = ".format(r, c, cell.text))
    for page in doc.pages:
        # Print fields
        print("Fields: ")
        for field in page.form.fields:
            print("Key: {}, Value: ".format(field.key, field.value))
```

与之前的示例不同，您将创建测试配置来运行代码。

- 5. 单击“测试”按钮左侧的下拉列表。
- 6. 选择“配置测试事件”，然后选择“创建新测试事件”。
- 7. 从“事件模板”下拉列表中选择“Amazon S3 Put”。
- 8. 在 JSON 正文中，根据我们的存储桶名称和键更改高亮显示的值，如下所示：

```json
{
  "x-amz-id-2": "EXAMPLE123/5678abcdefghijklambdaisawesome/",
  "s3": {
    "s3SchemaVersion": "1.0",
    "configurationId": "testConfigRule",
    "bucket": {
      "name": "textract-document-analysis",
      "ownerIdentity": {
        "principalId": "EXAMPLE"
      },
      "arn": "arn:aws:s3:::textract-document-analysis"
    },
    "object": {
      "key": "receipt.png",
      "size": 1024,
      "eTag": "0123456789abcdef0123456789abcdef",
      "sequencer": "0A1B2C3D4E5F678901"
    }
  }
}
```

### 图 8.22 – 用于测试 Lambda 函数的事件模板

- 9. 在“事件名称”字段中，将测试配置命名为 TextractDemo。
- 10. 单击“保存”。
- 11. 选择您的测试配置 (TextractDemo)，然后单击“测试”：

![](img/87c29232224b00f5a8bba6a66a391700_229_0.png)

### 图 8.23 – 运行测试前选择测试配置

12. 这将触发 Lambda 函数。您可以从 CloudWatch > CloudWatch 日志 > 日志组 > /aws/lambda/ read-scanned-doc 监控日志。

13. 单击流并选择最新的一个。它将如下所示；键值对可在图 8.24 中查看：

![](img/87c29232224b00f5a8bba6a66a391700_229_1.png)

### 图 8.24 – CloudWatch 中用于验证输出的日志

## 重要提示

通过 Lambda 异步调用下游 AI 工作流以生成 S3 PUT 事件，最具可扩展性且成本效益最高的方法是生成 AWS 预签名 URL，然后将其提供给移动或 Web 应用程序用户。许多用户可以通过此方法同时得到服务，并且这可能会提高性能和吞吐量。

将 AWS AI 服务和 S3 存储桶置于同一区域可能会提高性能并降低网络延迟。AWS VPC 端点可在不使用公共互联网的情况下提供增强的安全性。您可以将 AWS AI 结果存储在 AWS S3 存储桶中，并对其余内容进行加密，以获得更好的安全性。

在本节中，您学习了如何从扫描文档中提取文本并打印其中的表单数据。与其他章节不同，您通过创建包含事件模板的测试配置，使用了 Lambda 函数的测试功能。在下一节中，您将了解如何为组织创建聊天机器人并学习如何使用它。

## 在 Amazon Lex 上创建聊天机器人

Alexa 中的大多数功能均由 Amazon Lex 提供支持。您可以使用 Amazon 轻松构建聊天机器人。它在后台使用自然语言理解和自动语音识别。Amazon Lex 机器人可以通过控制台或 API 创建。其基本要求将在即将显示的图中展示。

Amazon Lex 的一些常见用途包括：

- 既能听取输入又能接受文本输入的应用
- 聊天机器人
- 用于提供更好客户和销售体验的对话式 AI 产品
- 用于通过 AWS Lambda 函数提供协助的自定义业务机器人
- 用于呼叫中心的语音助手，可与用户交谈、安排会议或请求您的账户详细信息
- 通过与 Amazon Cognito 集成，可以控制用户管理、身份验证和跨所有设备同步等几个方面

接下来，您将探索 Amazon Lex 的优势。

## 探索 Amazon Lex 的优势

使用 Lex 的一些理由包括：

- 聊天机器人可以直接从 AWS 管理控制台构建和测试。这些聊天机器人可以通过其丰富的格式化功能轻松集成到 Facebook Messenger、Slack 和 Twilio SMS 中。
- 会话日志可以存储在 Amazon CloudWatch 中以便进一步分析。您可以使用它们来监控机器人并获得洞察，以改善用户体验。

- Amazon Lex 可以与其他 AWS 服务（如 Amazon Cognito、AWS Lambda、Amazon DynamoDB、Amazon CloudWatch 和 AWS Mobile Hub）集成，以便在 AWS 平台上利用应用程序安全性、监控、用户身份验证、业务逻辑、存储和移动应用程序开发。
- Amazon Lex 聊天机器人也可以集成到您的自定义 Web 应用程序中。您只需构建一个聊天机器人小部件并将其集成到 UI 中即可。

接下来，您将动手实践 Amazon Lex。

## 动手实践 Amazon Lex

让我们开始吧：

- 1. 登录 https://console.aws.amazon.com/lex/。
- 2. 单击 **Get Started** 并选择 **Custom bot**。
- 3. 填写以下详细信息并单击 **Create**：

| 功能 | 值 |
| :--- | :--- |
| **机器人名称** | MovieBot |
| **语言** | English (US) |
| **输出语音** | 无。这仅是一个基于文本的应用程序。 |
| **会话超时** | 5 min |
| **情感分析** | 否 |
| **IAM 角色** | AWSServiceRoleForLexBots 将以您的名义自动创建 |
| **COPPA** | 请指示您对此机器人的使用是否受《儿童在线隐私保护法》(COPPA) 约束。了解更多 否 |
| **高级选项** | 启用精度改进和 ML 功能。了解更多 是 |
| **置信度分数阈值** | 0.4 (默认值) |

### 图 8.25 – Amazon Lex 的创建对话框

- 4. 单击 **Create Intent**。将出现一个对话框。选择 **Create Intent**。

5. 将新意图命名为 `MovieIntent`，然后单击 `Add`。

6. 转到 `Slots` 部分并使用以下详细信息：

- 名称：`movie_type`
- 插槽类型：`AMAZON.Genre`
- 提示：您喜欢哪部电影？

7. 在 `Settings` 中单击 `+`。

可在图 8.26 中查看一些示例语句。在此示例中，`movie_type` 是我的变量：

### MovieIntent 最新

### 示例语句

- 例如 我想预订一张机票。
- 在 Amazon Prime 中搜索 {movie_type}
- 我喜欢 {movie_type} 电影
- 是看电影的时候了。
- 我想看电影。

### Lambda 初始化和验证

[ ] 初始化和验证代码挂钩

### 插槽

| 优先级 | 必需 | 名称 | 插槽类型 | 版本 |
| :--- | :--- | :--- | :--- | :--- |
| 1. | ✓ | movie_type | AMAZON.Genre | 内置 |

### 图 8.26 – 示例语句部分

8. 向下滚动到 `Response` 部分以添加消息：

