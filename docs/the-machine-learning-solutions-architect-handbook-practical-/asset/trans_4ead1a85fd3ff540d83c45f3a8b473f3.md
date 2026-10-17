

Amazon Comprehend 可以作为构建智能文档处理解决方案和其他 NLP 产品的不错选择。它还可以作为一个良好的基准工具，用于与自定义 NLP 模型进行比较。

## Amazon Textract

许多业务流程，例如贷款申请处理、费用处理和医疗索赔处理，都需要从图像和文档中提取文本和数字。目前，许多组织在很大程度上手动处理这些流程，而这些流程可能非常耗时且缓慢。

`Amazon Textract` 是一种 `optical character recognition` (`OCR`) AI 服务，主要用于从图像和 PDF 文档中提取印刷文本、手写文本和数字。Textract 通常用作文档分析和数据录入等下游任务的处理步骤。Textract 的核心功能如下：

*   `OCR`: OCR 是一种计算机视觉任务，用于检测和提取 PDF 文档和图像中的文本数据。Textract 中的 OCR 组件从输入文档中提取原始文本，并提供有关文档的额外结构信息。例如，Textract 输出包含文档中不同对象（如页面、段落、句子和单词）的层次结构关系。Textract 还捕获输入文档中不同对象的位置信息。当您需要从文档的不同位置提取特定信息时，层次结构信息和对象位置数据非常有用。OCR API 为 `DetectDocumentText`（用于同步检测文本）和 `StartDocumentTextDetection`（用于异步检测文本）。

*   `Table extraction`: 许多文档包含表格数据结构，需要作为表格进行处理。例如，您可能有一份包含不同列中索赔项目及其详细信息列表的保险索赔文档，并且您可能希望将这些索赔项目录入系统。Textract 中的表格提取组件可以从文档中提取表格和表格中的单元格。要使用表格提取功能，您可以使用 `AnalyzeDocument` API 进行同步操作，并使用 `StartDocumentAnalysis` 进行异步操作。

*   `Form extraction`: 工资单和贷款申请表等文档包含许多名称-值对，在自动处理时需要保留它们的关系。Textract 中的表单提取组件可以检测这些名称-值对及其关系，以便进行下游处理，例如将这些文档中的名称录入系统。表单提取组件与表格提取组件共享相同的 `AnalyzeDocument` 和 `StartDocumentAnalysis` API。

*   `Signature in document analysis`: Textract 可以检测文档中的签名位置，返回指定签名位置的边界框和置信度分数。签名检测可以独立运行，也可以与表单、表格和自定义查询等其他功能一起运行。与表单或表格结合使用时，Textract 会将检测到的签名与相应的单元格或键值对关联起来。

*   `Queries in document analysis:` Textract 允许添加自定义查询，以从文档中提取特定信息。例如，“申请人的地址是什么？”这样的查询将仅在单独的响应结构中返回分析文档中的该数据点。

Textract 还具有用于分析特定类型文档（如发票和身份证件）的功能。例如，Textract 可以从发票或收据中提取供应商和接收者联系信息等相关数据，而无需任何模板或配置。同样，它可以从护照、驾驶执照以及美国政府签发的其他身份证明文件中提取相关信息。

Textract API 在 `boto3` 库中受支持。以下代码示例展示了如何使用 `boto3` 库检测文本。`boto3` 的 Textract API 完整列表可在 [https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/textract.html](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/textract.html) 上找到。

```
import boto3
client = boto3.client('textract')
response = client.detect_document_text(
        Document={
            'Bytes': b'bytes',
            'S3Object': {
                'Bucket': '<S3 bucket name>',
                'Name': '<name of the file>'}
})
```

Textract 还与 `Amazon Augmented AI` (`A2I`) 服务集成，以便为审查 Textract 中低置信度预测结果启用人机交互工作流集成。您可以在 [https://aws.amazon.com/augmented-ai](https://aws.amazon.com/augmented-ai) 上找到有关 A2I 服务的更多信息。

## Amazon Rekognition

`Amazon Rekognition` 是一种视频和图像分析 AI 服务。它支持多种用例，例如从图像和视频中提取元数据、内容审核以及安全和监控。Rekognition 的核心功能如下：

*   `Label or object detection`: 标签检测可应用于搜索和发现的媒体元数据提取、保险索赔处理中的项目识别和计数，以及品牌和徽标检测等用例。Rekognition 可以检测图像和视频中的不同对象、场景和活动，并为其分配标签，例如 `soccer`、`outdoor` 和 `playing soccer`。对于检测到的常见对象，它还提供对象的边界框，以指示它们在图像或视频中的特定位置。要使用 Rekognition 进行标签检测，您可以调用 `DetectLabels` API。如果 Rekognition 无法检测图像中的特定对象，您也可以使用 `CreateProject` API 使用训练数据训练自定义标签检测器。模型训练完成后，您可以选择使用 `StartProjectVersion` API 部署私有预测端点。

*   `Facial analysis and recognition`: 面部分析和识别对于视频监控和安全、图像和视频中自动为人物贴标签以便进行内容搜索以及了解人口统计信息等用例很有用。Rekognition 可以识别和分析图像和视频中的人脸。例如，您可以对人脸进行分析以检测性别、年龄和情感。您还可以构建人脸索引并为其分配名称。如果找到匹配项，Rekognition 可以将检测到的人脸映射到索引中的人脸。面部分析和识别的主要 API 为 `DetectFaces`、`SearchFaces`、`IndexFaces` 和 `CompareFaces`。

*   `Content moderation`: Rekognition 拥有 API（`StartContentModeration`），用于检测包含暴力等露骨内容和场景的图像和视频。组织可以使用此功能在将内容提供给消费者之前过滤掉不当和冒犯性内容。

*   `Short text detection`: Rekognition 可以检测图像中的短文本，并使用其 `DetectText` 和 `StartTextDetection` API 在检测到的文本周围提供边界框。此功能可用于检测街道名称、商店名称和车牌号码。

*   `Personal protection equipment (PPE) detection`: Rekognition 提供了一个内置功能，用于使用 `DetectProtectiveEquipment` API 检测图像和视频中的个人防护装备。此功能可用于自动化个人防护装备合规性监控。

*   `Celebrity identification`: Rekognition 还维护一个名人数据库，可用于识别图像和视频中的知名名人。它为该功能提供了一系列 API，包括 `RecognizeCelebrities` 和 `GetCelebrityInfo`。

