

虽然 AI 服务可以提供一种快速构建支持 ML 的产品的经济高效方式，但它们确实存在局限性。主要局限性在于缺乏针对特定功能和技术要求的定制灵活性。AI 服务通常专注于特定的 ML 任务，并使用一组预定义的算法，因此你通常没有灵活性来更改 AI 服务的功能。使用 AI 服务时，你通常无法访问底层模型，从而限制了你将模型部署到其他地方的能力。

近年来，AI 服务的数量大幅增长，我们预计这一趋势将以加速的速度继续下去。让我们将重点转移，讨论几种 AWS AI 服务。

# AWS AI 服务概述

AWS 在多个 ML 领域提供 AI 服务，例如文本和视觉，以及用于工业用例的 AI 服务，例如制造异常检测和预测性维护。在本节中，我们将介绍 AWS AI 服务的一个子集。本节的目标不是深入探讨单个服务，而是让你了解这些 AI 服务提供的基本功能。这将让你知道这些服务可以在哪里以及如何集成到你的应用程序中。

## Amazon Comprehend

NLP 在不同行业中引起了广泛关注，用于解决一系列业务问题，例如自动文档处理、文本摘要、文档理解以及文档管理和检索。`Amazon Comprehend` 是一项 AI 服务，可对非结构化文本文档执行 NLP 分析。其核心，Amazon Comprehend 提供以下主要功能：

*   `Entity recognition`：实体是文本分析中的谁、什么、哪里和何时。实体可以是句子中最重要的部分，因为它们识别文本中的关键组件。实体的示例包括人名、地点或产品等专有名词。实体可用于创建文档搜索索引，并识别文档间的关键信息或关系。Comprehend 提供 API（例如 `DetectEntities`）用于使用其内置实体识别模型检测实体。它可以从输入文本中检测人物、地点、组织和日期等实体。如果内置模型不满足你的要求，你还可以使用 Comprehend 为自定义实体训练自定义实体识别器。要训练自定义实体识别器，你可以使用 `CreateEntityRecognizer` API，并使用以下两种格式之一的训练数据：

    1.  `Annotation`：你提供文档中实体的位置（目标字符的起始和结束偏移量），以及每对偏移量的实体类型。这有助于 Comprehend 同时训练实体及其所处的上下文。

    2.  `Entity list`：你以纯文本形式提供实体列表及其实体类型，Comprehend 将训练以检测这些特定实体。你可以使用 Comprehend 自定义模型训练作业发出的指标来评估自定义模型。示例评估指标包括精确率、召回率和 F1 分数。 

    有关 Comprehend 评估指标的更多详细信息，请参阅 [https://docs.aws.amazon.com/comprehend/latest/dg/cer-metrics.html](https://docs.aws.amazon.com/comprehend/latest/dg/cer-metrics.html)。模型训练完成后，你可以选择将模型部署在私有预测端点后面以提供预测服务。

*   `Sentiment analysis`：Comprehend 可以使用其 `DetectSentiment` API 检测文本中的情感。情感分析广泛应用于许多业务用例，例如分析客户支持通话中的客户情感，或了解客户在评论中对产品和服务的看法。

*   `Topic modeling`：主题建模具有广泛的用途，包括文档理解、文档分类和组织、信息检索以及内容推荐。Comprehend 可以使用其 `StartTopicsDetectionJob` API 发现文档之间的共同主题。

*   `Language detection`：Comprehend 可以使用其 `DetectDominantLanguage` API 检测文本中使用的主导语言。此功能可以帮助处理诸如根据语言将来电客户支持呼叫路由到正确渠道或按不同语言对文档进行分类等用例。

*   `Syntax analysis`：Comprehend 可以使用其 `DetectSyntax` API 对句子执行 `part-of-speech` (`POS`) 分析。示例 POS 包括句子中的名词、代词、动词、副词、连词和形容词。POS 分析可以帮助处理诸如检查书面文本中语法和句法的正确性等用例。

*   `Event detection`：Comprehend 可以检测预定义的金融事件列表，例如 IPO、股票拆分和破产。它还检测与事件相关的增强项，例如申请破产的个人或公司。这种关系有助于构建知识图谱，以帮助我们了解不同事件的“谁做了什么”。你可以在 [https://docs.aws.amazon.com/comprehend/latest/dg/cer-doc-class.html](https://docs.aws.amazon.com/comprehend/latest/dg/cer-doc-class.html) 上找到事件和增强类型的完整列表。

*   `Text classification`：你可以使用 Comprehend 和训练数据训练自定义文本分类器。Comprehend 允许你通过其 `CreateDocumentClassifier` API 训练多类和多标签分类器。多类为文本分配单个标签，而多标签为文本分配多个标签。要评估自定义分类器的性能，Comprehend 提供一系列指标，包括准确率、召回率和 F1 分数。你可以在 [https://docs.aws.amazon.com/comprehend/latest/dg/cer-doc-class.html](https://docs.aws.amazon.com/comprehend/latest/dg/cer-doc-class.html) 上找到指标的完整列表。

*   `Personally identifiable information (PII) detection`：你可以检测英语或西班牙语文本文档中的 PII。PII 检测过程提供定位或编辑文本中 PII 实体的选项。对于定位 PII 实体，可以使用实时分析或异步批处理作业。另一方面，编辑 PII 实体特别需要使用异步批处理作业。

*   `Key phrase detection`：Amazon Comprehend 中的关键短语功能使用 ML 模型分析输入文本并提取最重要的短语或主题。这些关键短语可以提供简洁的摘要，或突出显示文本中存在的主要思想和概念。

飞轮是 Comprehend 的一项功能，它为持续改进自定义自然语言处理模型提供托管工作流。飞轮在 AWS 托管的数据湖中存储所有模型数据和版本。当新的带标签数据集可用时，你可以创建飞轮迭代，使用最新数据重新训练和评估新模型版本。根据性能指标，最佳新版本可以被提升为提供推理的活动模型。这种迭代过程允许模型准确性随时间推移而提高，因为定期模型重新训练会纳入新数据。

Comprehend API 可以使用 `boto3` 库和 AWS `command-line interface` (`CLI`) 调用。你可以在 [https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/comprehend.html](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/comprehend.html) 上找到 Comprehend 支持的 `boto3` 方法的完整列表。以下显示了调用 Comprehend 实体检测功能的 Python 语法：

```
import boto3
client = boto3.client('comprehend')
response = client.detect_entities(Text='<input text>')
```

