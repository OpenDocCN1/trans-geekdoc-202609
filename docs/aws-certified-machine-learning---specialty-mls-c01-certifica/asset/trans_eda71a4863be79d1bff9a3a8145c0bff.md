

在本节中，你学习并应用了 Amazon Transcribe 将语音转换为文本。在下一节中，你将了解一种最强大的 AWS AI 服务，可用于从我们的文本数据中获得最大洞察。

## 使用 Amazon Comprehend 实现自然语言处理

此服务可帮助你从非结构化文本中提取洞察。非结构化文本信息呈指数级增长。部分数据源示例如下：

- 客户互动：呼叫中心、问题分类、客户调查和产品评论
- 业务流程：客户/供应商电子邮件、产品支持消息和运营支持反馈
- 记录和研究：白皮书和医疗记录
- 新闻和社交媒体：社交媒体分析、品牌趋势和相关事件

现在的问题是，你可以对这些数据做什么？如何分析它们并提取任何价值？答案是 Amazon Comprehend，用于从非结构化数据中获取洞察。

Amazon Comprehend 的一些常见用途包括以下内容：

- 信息管理系统
- 用于有组织主题的更准确搜索系统
- 用户情感分析
- 支持工单分类
- 从文档中检测语言，然后使用 Amazon Translate 将其翻译成英语
- 创建一个系统来为非结构化临床数据打标签，以协助研究和分析目的
- 从保存的公司会议或电视新闻音频文件中提取主题

接下来，你将探索 Amazon Comprehend 的优势。

## 探索 Amazon Comprehend 的优势

使用 Comprehend 的一些优势可以在下图中看到：

![](img/87c29232224b00f5a8bba6a66a391700_218_0.png)

图 8.14 – 显示 Amazon Comprehend 功能的框图

让我们更详细地了解这些内容：

- 它检测文本语言并提取关键短语。Amazon Comprehend 还可用于情感分析和主题建模。
- Amazon Comprehend Medical 可用于提取医疗信息。
- 由于这是一项完全托管的服务，你按使用量付费；无需为基础设施付费。你无需训练、开发和部署自己的模型。
- 主题建模服务通过提取最多 100 个主题来工作。主题是关键词集合，因此你可以查看实际文档库中包含的内容。
- 它准确、持续训练且易于使用。

接下来，你将动手实践 Amazon Comprehend。

## 动手实践 Amazon Comprehend

在本节中，你将构建一个管道，将 AWS Lambda 与 Amazon Rekognition 和 Amazon Comprehend 集成。然后，你将读取存储在 S3 存储桶中的图像文件，并检测从图像中提取的文本的语言。你还将使用 CloudWatch 打印输出。以下是我们用例的图表：

![](img/87c29232224b00f5a8bba6a66a391700_219_0.png)

图 8.15 – 所需用例的架构图

## 首先创建一个 IAM 角色：

- 1. 导航到 IAM 控制台页面。
- 2. 从左侧菜单中选择 Roles。
- 3. 选择 Create role。
- 4. 将 Lambda 选为受信任实体。
- 5. 添加以下托管策略：
    - AmazonS3ReadOnlyAccess
    - AmazonRekognitionFullAccess
    - ComprehendFullAccess
    - CloudWatchFullAccess
- 6. 将角色保存为 language-detection-from-image-role。
- 7. 现在，让我们创建 Lambda 函数。导航到 Lambda > Functions > Create Function。
- 8. 将函数命名为 language-detection-from-image。
- 9. 将运行时设置为 Python 3.6。
- 10. 使用我们现有的角色；即，language-detection-from-image-role。
- 11. 从 https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/tree/main/Chapter08/Amazon%20Transcribe%20Demo/lambda_function 下载代码，将其粘贴到函数中，然后单击 Deploy。

此代码将读取你上传的图像中的文本并检测文本的语言。你已使用 Amazon Rekognition 的 detect_text API 从图像中检测文本，并使用 Amazon Comprehend 的 batch_detect_dominant_language API 检测文本的语言。

- 12. 现在，前往 AWS S3 控制台并创建名为 language-detection-image 的存储桶。
- 13. 创建一个名为 input-image 的文件夹（在此示例中，你只会上传 .jpg 文件）。
- 14. 导航到 Properties > Events > Add notification。
- 15. 在 Events 部分填写所需字段，使用以下信息；然后，单击 Save：
    - Name: image-upload-event
    - Events: All object create events
    - Prefix: input-image/
    - Suffix: .jpg
    - Send to: Lambda Function
    - Lambda: language-detection-from-image
- 16. 导航到 Amazon S3 > language-detection-image > input-image。在文件夹中上传 sign-image.jpg 图像。（此文件可在此书的 GitHub 仓库中找到 https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/tree/main/Chapter08/Amazon%20Comprehend%20Demo/input_image）。
- 17. 此文件上传将触发 Lambda 函数。你可以从 CloudWatch > CloudWatch Logs > Log groups > /aws/lambda/language-detection-from-image 监控日志。
- 18. 单击流并选择最新的流。检测到的语言将打印在日志中，如图 8.16 所示：

![](img/87c29232224b00f5a8bba6a66a391700_220_0.png)

图 8.16 – CloudWatch 中用于验证输出的日志

## 重要提示

建议在生产环境中使用批量操作，例如 BatchDetectSentiment 和 BatchDetectDominantLanguage。这是因为单个 API 操作可能导致 API 级别限流。更多详情请参阅：https://docs.aws.amazon.com/comprehend/latest/dg/functionality.html。

在本节中，你学习了如何使用 Amazon Comprehend 检测文本的语言。文本通过 Amazon Rekognition 提取到我们的 Lambda 函数中。在下一节中，你将学习如何通过 Amazon Translate 将相同文本翻译成英语。

## 使用 Amazon Translate 翻译文档

大多数时候，人们即使在数字平台上也更喜欢使用自己的语言进行交流。Amazon Translate 是一项文本翻译服务。你可以提供多种语言的文档或文本字符串，并以不同的语言获取结果。它使用预训练的深度学习技术，因此你无需担心模型及其管理方式。你可以发出 API 请求并获取结果。

Amazon Translate 的一些常见用途包括以下内容：

- 如果组织范围内有以不同语言准备文档的要求，则 Translate 是将一种语言转换为多种语言的解决方案。
- 在线聊天应用程序可以实时翻译，以提供更好的客户体验。
- 以更快、更实惠的方式将网站内容本地化为更多语言。
- 翻译后，可以将情感分析应用于不同语言。
- 为新闻发布网站提供非英语语言支持。

接下来，你将探索 Amazon Translate 的优势。

## 探索 Amazon Translate 的优势

使用 Amazon Translate 的一些优势包括以下内容：

- 它使用神经机器翻译，模仿人脑的工作方式。
- 你无需为翻译操作维护资源或基础设施。
- 生成高质量结果并保持其一致性。
- 你可以自定义品牌名称和模型名称。其他独特术语也可以使用自定义术语功能进行翻译。
- 可以通过 API 轻松与应用程序集成。
- 当你需要做更多工作时，Amazon Translate 会自行扩展。

接下来，你将动手实践 Amazon Translate。

## 动手实践 Amazon Translate

