
```
'HTTPHeaders': {'x-amzn-requestid': '74ca4afd-5844-47d8-9664-3660a26965e4', 'content-type': 'application/json', 'content-length': '471', 'date': 'Thu, 24 Sep 2020 18:50:57 GMT', 'RetryAttempts': 0},
'SynthesisTask': {'Engine': 'standard', 'TaskId': '57548c6b-d21a-4885-962f-450952569dc7', 'TaskStatus': 'scheduled', 'OutputUri': 'https://s3.us-east-1.amazonaws.com/polly-test-baba/output-audio/.57548c6b-d21a-4885-962f-450952569dc7.mp3',
'CreationTime': datetime.date(2020, 9, 24), 'RequestCharacters': 59, 'OutputFormat': 'mp3', 'TextType': 'text',
'VoiceId': 'Aditi', 'LanguageCode': 'en-GB'}})
```

日志示例如图 8.8 所示：

| Log Entry | Details |
| :--- | :--- |
| 2020-09-24T19:07:04.054+01:0... | 任务状态为：scheduled |
| 2020-09-24T19:07:04.094+01:0... | 任务状态为：scheduled |
| 2020-09-24T19:07:04.105+01:0... | 任务状态为：scheduled |
| 2020-09-24T19:07:04.184+01:0... | 任务状态为：scheduled |
| 2020-09-24T19:07:04.254+01:0... | 任务状态为：inProgress |
| 2020-09-24T19:07:04.497+01:0... | 任务状态为：completed |
| 2020-09-24T19:07:04.534+01:0... | 音频文件保存成功 |
| 2020-09-24T19:07:04.553+01:0... | 结束 RequestId: 1d57151b-8462-434c-89b4-9b318c2437d8 |
| 2020-09-24T19:07:04.553+01:0... | 报告 RequestId: 1d57151b-8462-434c-89b4-9b318c2437d8 持续时间：15832.73 毫秒 计费持续时间： |
| | 此时没有更新的事件。自动重试已暂停。继续 |

图 8.8 – CloudWatch 控制台中的日志

16. 它将生成 MP3 格式的输出，如图 8.9 所示。下载并收听：

![](img/87c29232224b00f5a8bba6a66a391700_212_0.png)

图 8.9 – 在 S3 存储桶中创建的输出文件

## 重要提示

对于移动应用或 Web 应用，最具可扩展性且成本效益最高的方式是为 S3 存储桶生成 AWS 预签名 URL 并提供给用户。这些 S3 Put 事件会异步调用下游 AI 工作流以生成结果，并向最终用户发送响应。通过此方法，可同时为许多用户提供服务，并可能提升性能和吞吐量。

本节介绍了如何实现文本转语音。在下一节中，您将了解 Amazon Transcribe，这是一项语音转文字 AI 服务。

## 使用 Amazon Transcribe 进行语音转文字

上一节介绍了文本转语音。本节将介绍语音转文字及提供该功能的服务：Amazon Transcribe。它是一项自动语音识别服务，使用预训练的深度学习模型，这意味着您无需在 PB 级数据上训练模型；Amazon 已为我们完成此操作。您只需使用可用的 API 来转录音频文件或视频文件；它还支持多种不同语言和自定义词汇。准确性是关键，通过自定义词汇，您可以根据所需的领域或行业来增强准确性：

![](img/87c29232224b00f5a8bba6a66a391700_213_0.png)

图 8.10 – Amazon Transcribe 输入和输出的框图

Amazon Transcribe 的常见用例包括以下内容：

- 实时音频流与转录
- 转录预录制的音频文件
- 通过结合 AWS Elasticsearch 和 Amazon Transcribe，从媒体文件启用文本搜索
- 对录制的音频文件执行情感分析，用于语音帮助台（联络中心分析）
- 通道识别分离

接下来，您将探索 Amazon Transcribe 的优势。

## 探索 Amazon Transcribe 的优势

让我们看看使用 Amazon Transcribe 的一些优势：

- 内容编辑：通过指示 Amazon Transcribe 从语音转录中识别并编辑个人身份信息 (PII)，可以确保客户隐私。您可以通过提供不需要的单词列表（使用 StartTranscriptionJob 操作提供的 VocabularyFilterName 和 VocabularyFilterMethod）来过滤转录中的不需要的单词。例如，在金融机构中，这可用于编辑来电者的详细信息。

- 语言识别：它可以自动识别音频文件中最常用的语言并生成转录。如果您有多个音频文件，此服务可帮助您按语言对其进行分类。

- 流式转录：您可以将录制的音频文件或实时音频流发送到 Amazon Transcribe，并实时输出文本流。

- 自定义词汇或定制转录：您可以根据自定义需求使用自定义词汇列表来生成准确的转录。

- 时间戳生成：如果您想为视频构建或添加字幕，Amazon Transcribe 可以从音频中返回每个单词或短语的时间戳。

- 成本效益：作为托管服务，无需基础设施成本。

现在，让我们开始使用 Amazon Transcribe 进行实践操作。

## 使用 Amazon Transcribe 进行实践操作

在本节中，您将构建一个管道，以集成 AWS Lambda 与 Amazon Transcribe，读取存储在 S3 存储桶文件夹中的音频文件，然后将输出 JSON 文件存储在另一个 S3 存储桶中。您还将在 CloudWatch Logs 中监控任务进度。您将使用 start_transcription_job 异步函数启动作业，并通过 get_transcription_job 持续监控作业，直到其状态变为 COMPLETED。让我们开始吧：

1. 首先，为 Lambda 函数创建一个名为 transcribe-demo-role 的 IAM 角色以供其执行。确保它可以读写 S3、使用 Amazon Transcribe，并在 CloudWatch 日志中打印输出。向 IAM 角色添加以下策略：

   - AmazonS3FullAccess
   - CloudWatchFullAccess
   - AmazonTranscribeFullAccess

2. 现在，您将使用现有的 IAM 角色 transcribe-demo-role 创建一个名为 transcribe-lambda 的 Lambda 函数并保存它。

请确保在 Lambda 函数的 **基本设置** 部分将默认超时更改为更高的值。我已将其设置为 10 分 20 秒，以避免超时错误。您将使用名为 start_transcription_job 的异步 API 调用来启动任务，并通过 get_transcription_job API 进行监控。

3. 粘贴 https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/blob/main/Chapter08/Amazon%20Transcribe%20Demo/lambda_function/lambda_function.py 中提供的代码，然后单击 **部署**。这应该会产生以下输出：

![](img/87c29232224b00f5a8bba6a66a391700_215_0.png)

图 8.11 – 我们创建的 Lambda 函数的基本设置部分

4. 接下来，您将创建一个名为 **transcribe-demo-101** 的 S3 存储桶和一个名为 **input** 的文件夹。转到 **创建事件通知** 部分的 **属性** 选项卡来创建一个事件。输入以下详细信息：

   - 名称：audio-event
   - 事件：所有对象创建事件
   - 前缀：input/
   - 目标：Lambda 函数
   - Lambda：transcribe-lambda

5. 将 .mp4 格式的音频文件上传到 **input** 文件夹。这将触发 Lambda 函数。根据代码，输出将以 JSON 格式存储在 S3 存储桶中，您随后可以使用它来读取文件内容。

6. 导航到 **CloudWatch > CloudWatch Logs > 日志组 > aws/lambda/transcribe-lambda**。从列表中选择最新的流。它将如下所示：

## 日志事件

| Timestamp | Message |
|---|---|
| 2020-09-28T21:10:47.554+01:0... | 启动 RequestId: b5774cde-e65e-4376-a73d-7cf9944c36d4 版本：$LATEST |
| 2020-09-28T21:10:47.554+01:0... | --- 语音转文字 --- |
| 2020-09-28T21:10:48.157+01:0... | 正在检查状态.... 尚未完成 |
| 2020-09-28T21:11:08.242+01:0... | 正在检查状态.... 尚未完成 |
| 2020-09-28T21:11:28.330+01:0... | 正在检查状态.... 尚未完成 |
| 2020-09-28T21:11:48.412+01:0... | 检查您的输出存储桶 |
| 2020-09-28T21:11:48.412+01:0... | 语音转文字完成： |
| 2020-09-28T21:11:48.412+01:0... | 结束 RequestId: b5774cde-e65e-4376-a73d-7cf9944c36d4 |
| 2020-09-28T21:11:48.412+01:0... | 报告 RequestId: b5774cde-e65e-4376-a73d-7cf9944c36d4 持续时间：60857.34 毫秒 计费持续时间：60900 毫秒 |
| | 此时没有更新的事件。自动重试已暂停。继续 |

图 8.12 – CloudWatch 控制台中指定日志组的日志流中的日志

7. 输出已按代码中提到的作业名称以 JSON 格式保存到 S3 存储桶中（您可以使用 S3 getObject API 下载并读取它）：

![](img/87c29232224b00f5a8bba6a66a391700_216_0.png)

图 8.13 – S3 存储桶中的输出 JSON 文件

## 重要提示

不超预配函数的超时设置是最佳实践。始终了解您的代码性能，并相应地设置函数超时。超预配函数超时会导致 Lambda 函数运行时间更长，从而产生意外成本。如果在 Lambda 函数中使用异步 API 调用，则最好在成功后将其写入 SNS 主题，并从此触发另一个 Lambda 函数。如果需要人工干预，则建议使用 AWS Step Functions。
