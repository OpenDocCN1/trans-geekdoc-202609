
人脸分析与识别：人脸分析与识别适用于视频监控和安全、图像和视频中的自动人员标记（用于内容搜索）以及人口统计理解等用例。

Rekognition 可以识别并分析图像和视频中的人脸。例如，你可以对人脸进行分析以检测性别、年龄和情感。你还可以建立人脸索引并为其分配名称。如果找到匹配项，Rekognition 可以将检测到的人脸映射到索引中的人脸。

人脸分析与识别的主要 API 有 DetectFaces、SearchFaces、IndexFaces 和 CompareFaces。

内容审核：Rekognition 提供了 API (StartContentModeration)，用于检测包含显内容和场景（如暴力）的图像和视频。组织可以使用此功能在将内容提供给消费者之前过滤掉不当和攻击性的内容。

短文本检测：Rekognition 可以检测图像中的短文本，并使用 `DetectText` 和 `StartTextDetection` API 在检测到的文本周围提供边界框。此功能可用于检测街名、商店名称和车牌号。

个人防护装备 (PPE) 检测：Rekognition 提供了一个内置功能，可以使用 `DetectProtectedEquipment` API 检测图像和视频中的 PPE。此功能可用于自动 PPE 合规性监控。

名人识别：Rekognition 还维护了一个名人数据库，用于识别图像和视频中的已知名人。它为此功能提供了一系列 API：RecognizeCelebrities 和 GetCelebrityInfo。

你可以使用 boto3 库访问这些 API。以下代码段显示了标签检测功能的语法。Rekognition 的完整 boto3 API 列表可以在 https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/rekognition.html 处找到：

```python
import boto3
client = boto3.client('rekognition')
response = client.detect_labels(
    'Bytes': b'imagebytes',
    'S3Object': {
        'Bucket': '<S3 bucket name>',
        'Name': '<file name>'
    })
```

Rekognition 还与 Amazon Kinesis Video（AWS 的的一项视频流服务）具有原生集成。你可以构建解决方案来检测实时视频流中的人脸。

# Amazon Transcribe

Amazon Transcribe (Transcribe) 是一种语音转文本的 AI 服务。它可以将视频和音频文件及流转为文本，适用于多种用例，例如媒体内容和会议字幕、通话分析以及将医疗对话转换为电子健康记录。

Amazon Transcribe 支持实时转录和批处理转录，并具有以下能力：

- **媒体转录：** Transcribe 拥有预训练模型，可以将媒体文件或流转换为不同的语言（如英语、中文和西班牙语）。它还会添加标点和大写字母，使转录的文本更具读性。要启动转录，你可以使用 StartTranscriptionJob 和 StartMedicalTranscriptionJob API 进行转录，使用 StartTranscriptionAPI 进行流转录，以及使用 StartMedicalTranscriptionAPI 进行流医疗输入。

- **自定义模型：** 你可以提供训练数据来创建自定义语言模型，以提高对特定行业术语或缩写的转录准确性。创建自定义模型的 API 是 CreateLanguageModel。

- **通话分析：** Transcribe 为通话提供了构建分析的能力。通话转录以逐轮对话的格式显示。支持的分析示例包括情感分析、通话分类、问题检测（通话背后的原因）和通话指标（非说话时间、音量、中断）。启动通话分析作业的 API 是 StartCallAnalyticsJob。

- **脱敏：** Transcribe 可以自动从转录中掩盖或移除敏感身份识别信息 (PII) 以保护隐私。在带有脱敏的转录时，Transcribe 将转录中的 PII 信息替换为 [PII]。要启用脱敏，你可以在批处理转录作业中配置 ContentRedaction 参数。

- **字幕：** Transcribe 可以生成 WebVTT 和 SubRip 格式的开箱可用字幕文件用于视频字幕。要启用字幕文件生成，你可以为转录作业配置 Subtitles 参数。

Transcribe 拥有一组这些不同操作的 API。以下代码示例显示了如何使用 boto3 库启动转录作业：

```python
import boto3
transcribe_client = boto3.client('transcribe')
transcribe_job = transcribe_client.start_transcription_job(**job_args)
```

你可以在 https://amazonaws.com/v1/documentation/api/latest/reference/services/transcribe.html 找到 Transcribe 的完整 boto3 API 列表。

# Amazon Personalize

个性化推荐可以帮助许多业务（如电子商务、金融产品推荐和媒体内容传递）优化用户参与度和收入。**Amazon Personalize** 允许你使用自己的数据构建个性化推荐模型。你可以将 Personalize 作为推荐引擎，根据个人喜好和行为驱动产品和内容推荐。从高层面上说，Personalize 服务提供了以下三个核心功能：

- **用户个性化：** 预测用户将交互或探索的项目
- **相似项目：** 根据项目和项目元数据的共同出现情况计算相似项目
- **个性化重排序：** 为给定的用户对输入的项目列表进行重排序

Amazon Personalize 不提供用于推荐的预训练模型。相反，你需要使用 Personalize 提供的内置算法使用你的数据来训练自定义模型。要训练个性化模型，你需要提供三个数据集：

- **项目数据集 (Item dataset)：** 项目数据集包含你想要推荐的项目属性。该数据集帮助 Personalize 学习有关项目的上上下文信息。此数据集是可选的。

- **用户数据集 (User dataset)：** 用户数据集包含关于用户的属性。这使得 Personalize 能够更好地表示每个用户，以提供高度个性化的推荐。此数据集是可选的。

- **用户-项目交互数据集 (User-item interaction dataset)：** 这是一个必需的数据集，提供了用户和项目之间的历史交互，例如观看电影或购买产品。Personalize 使用这些数据学习个人用户对不同项目的行为。

为了帮助理解 Personalize 是如何工作的，让我们回顾一些 Personalize 概念：

- **数据集组 (Dataset group)：** 数据集组包含用于模型训练的相关数据集（项目、用户和交互数据集）。

- **配方 (Recipe)：** 配方是用于模型训练的 ML 算法。Personalize 为主要功能提供了多种配方。

- **解决方案 (Solution)：** 解决方案代表一个已过的 Personalize 模型。

- **活动 (Campaign)：** Personalize 活动是已训练 Personalize 模型的托管节点，用于处理推荐和请求。

要使用 Personalize 训练并部署自定义模型，必须遵循以下步骤：

1. **准备并摄入数据集：** 在此步骤中，你按所需的格式准备数据集并存储在 S3 中，然后将数据集加载到 Personalize。此步骤涉及三个 API 操作——`CreateDatasetGroup`、`CreateDataset` 和 `CreateDatasetJob`。`CreateDatasetGroup` 创建空的数据集组。`CreateDataset` 将数据集（例如项目数据集和交互数据集）添加到数据集组，`CreateDatasetJob` 启动数据摄入作业，将数据从 S3 加载到 Personalize 仓库供后续模型训练。

2. **为模型训练选择配方：** 在此步骤中，你选择用于不同模型训练过程的配方（ML 算法）。Personalize 为用户个性化、相关项目和个性化排序提供了多种配方。你可以使用 ListRecipes API 获取完整的配方列表。

3. **创建解决方案：** 在此步骤中，你使用 `CreateSolution` API 通过数据集组和配方为模型训练作业配置解决方案。然后，你使用 `CreateSolutionVersion` API 启动训练作业。
