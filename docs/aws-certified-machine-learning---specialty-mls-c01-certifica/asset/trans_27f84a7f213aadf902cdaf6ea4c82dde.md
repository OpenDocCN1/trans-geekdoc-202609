

在本节中，你将通过将 AWS Lambda 与 Amazon Rekognition、Amazon Comprehend 和 Amazon Translate 集成，构建一个产品来读取存储在 S3 存储桶中的图像文件。然后，你将检测从图像中提取的文本的语言，以便将其翻译成英文。你还将使用 CloudWatch 打印翻译输出。以下是我们用例的图示：

![](img/87c29232224b00f5a8bba6a66a391700_222_0.png)

图 8.17 – 所需用例的架构图

让我们从创建 IAM 角色开始：

- 1. 导航到 IAM 控制台页面。
- 2. 从左侧菜单中选择 **角色**。
- 3. 选择 **创建角色**。
- 4. 将 **Lambda** 选择为可信实体。
- 5. 添加以下托管策略：
  - AmazonS3ReadOnlyAccess
  - AmazonRekognitionFullAccess
  - ComprehendFullAccess
  - CloudWatchFullAccess
  - TranslateFullAccess
- 6. 将角色保存为 `language-translation-from-image`。
- 7. 下一步是创建 Lambda 函数。导航到 Lambda > 函数 > 创建函数。
- 8. 将函数命名为 `language-detection-from-image`。
- 9. 将运行时设置为 **Python 3.6**。
- 10. 使用现有角色，即 `language-detection-from-image-role`。
- 11. 粘贴 [https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/blob/main/Chapter08/Amazon%20Translate%20Demo/lambda_function/lambda_function.py](https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/blob/main/Chapter08/Amazon%20Translate%20Demo/lambda_function/lambda_function.py) 中的代码，然后单击 **部署**。你将使用 `translate_text` API 来翻译输入文本。

- 12. 下一步是创建名为 `language-translation-from-image` 的存储桶。

创建名为 `image` 的文件夹。然后，导航到 **属性** > **事件** > **添加通知**。

- 13. 填写所需字段，如所示，然后单击保存（请确保将 `.jpg` 选择为后缀；否则，它将对任何对象创建过程触发 Lambda 函数）：
  - * 名称：`translate-language-image`
  - * 事件：所有对象创建事件
  - * 前缀：`image/`
  - * 后缀：`.jpg`
  - * 发送至：Lambda 函数
  - * Lambda：`language-translation-from-image`

- 14. 导航到 **Amazon S3** > `language-detection-image` > `input-image`。将 `sign-image.jpg` 图像上传到文件夹中。此文件可在本书的 GitHub 仓库中找到：https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/tree/main/Chapter08/Amazon%20Translate%20Demo/input_image。

- 15. 上传此图像将触发 Lambda 函数。你可以通过转到 **CloudWatch** > **CloudWatch 日志** > **日志组** > `/aws/lambda/language-translation-from-image` 来监控日志。

- 16. 单击流并选择最新的一个。它将如下所示：

![](img/87c29232224b00f5a8bba6a66a391700_223_0.png)

图 8.18 – 用于验证输出的 CloudWatch 日志

翻译如下：

```
Translation of the text from the Image :
{'PREVENCION DEL COVID-19' : 'PREVENTION OF COVID-19',
'LAVATE LAS MANOS EVITA EL CONTACTO NO TE TOQUES OJOS,
EVITA': 'WASH HANDS AVOID CONTACT DO NOT TOUCH EYES',
'60 SEGUNDOS CON CONTAGIADOS NARIZ O BOCA
AGLOMERACIONES': '60 SECONDS WITH CONTAGIOUS NOSE OR
MOUTH AGGLOMERATIONS', 'NO COMPARTAS NO VIAJES A MENOS
SI TE PONES ENFERMO': "DON'T SHARE NOT TRAVEL UNLESS
YOU GET SICK", 'CUBIERTOS NI COMIDA QUE SEA NECESARIO
BUSCA AYUDA MEDICA': 'CUTLERY OR FOOD NEEDED SEEK
MEDICAL HELP' }
```

## 重要说明

对于生产用例，如果你有依赖服务或服务链，建议将 AWS Lambda 与 AWS Step Functions 配合使用。

不建议使用同一 S3 存储桶来存储输入和输出对象。在同一存储桶中创建输出对象可能会触发递归 Lambda 调用。如果你使用同一存储桶，则建议使用前缀和后缀来触发事件。同样，建议使用前缀来存储输出对象。

在本节中，你学习了如何结合多种服务并链接它们的输出以实现特定用例结果。你学习了如何集成 Amazon Rekognition 以检测图像中的文本。然后可以使用 Amazon Comprehend 检测语言。接着，你使用相同的输入并借助 Amazon Translate 将其翻译成英文。然后将翻译输出打印到 CloudWatch 日志中进行验证。在下一节中，你将学习 Amazon Textract，它可以用于从文档中提取文本。

## 使用 Amazon Textract 从文档中提取文本

手动从文档中提取信息既缓慢又昂贵，且容易出错。传统的光学字符识别软件需要大量定制，且仍然会输出错误结果。为避免此类手动流程和错误，你应使用 Amazon Textract。通常，你需要将文档转换为图像，以检测图像中文本周围的边界框。然后应用字符识别来读取其中的文本。Textract 会为你完成所有这些工作，并且只需付出最小努力即可提取文本、表格、表单和其他数据。如果从 Amazon Textract 获得低置信度结果，则 Amazon A2I 是最佳解决方案。

Textract 减少了从数百万页扫描文档中提取文本的手动工作量。一旦信息被捕获，就可以对文本执行操作，例如将其存储在不同的数据存储中、分析情感或搜索关键字。以下图示说明了 Amazon Textract 的工作原理：

![](img/87c29232224b00f5a8bba6a66a391700_225_0.png)

图 8.19 – Amazon Textract 及其输出存储方式的框图表示

Amazon Textract 的一些常见用途包括：

- 用于提取表格或表单的文档处理工作流
- 使用 Amazon Elasticsearch 从文档中创建搜索索引
- 在工作流中删除个人身份信息；Textract 会自动识别数据类型和表单标签

接下来，你将探索 Amazon Textract 的优势。

## 探索 Amazon Textract 的优势

使用 Textract 有以下几个原因：

- 零基础设施成本
- 完全托管的服务（降低开发和管理开销）
- 帮助你提取结构化和非结构化数据
- 可以分析手写的评论
- Amazon Textract 的性能优于使用扁平词袋的 OCR 应用
- 接下来，你将实际操作 Amazon Textract。

## 实际操作 Amazon Textract

在本节中，你将使用 Amazon Textract API 从我们的 S3 存储桶中读取图像文件，并将表单详细信息打印到 CloudWatch。同样，可以将其以所需格式存储在 S3 中以供进一步使用，或作为键值对存储在 DynamoDB 中。让我们开始吧：

- 1. 首先，创建一个名为 `textrract-use-case-role` 的 IAM 角色，并附加以下策略。这将允许 Lambda 函数执行，以便它可以从 S3 读取、使用 Amazon Textract 并在 CloudWatch 日志中打印输出：
  - CloudWatchFullAccess
  - AmazonTextractFullAccess
  - AmazonS3ReadOnlyAccess

- 2. 让我们创建一个名为 `textrract-document-analysis` 的 S3 存储桶，并上传 `receipt.png` 图像文件。这将用于包含将要提取的表单详细信息。该图像文件可在以下网址找到：https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/tree/main/Chapter08/Amazon%20Textrract%20Demo/input_doc：

![](img/87c29232224b00f5a8bba6a66a391700_226_0.png)

图 8.20 – 已将图像 (.png) 文件上传到输入文件夹的 S3 存储桶

- 3. 下一步是创建名为 `read-scanned-doc` 的 Lambda 函数，如图 8.21 所示，使用名为 `textrract-use-case-role` 的现有执行角色：

