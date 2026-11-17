

## AWS 应用服务用于 AI/ML

在本章中，你将学习 AWS AI 服务，用于构建聊天机器人、高级文本分析、文档分析、语音转录等。本章的设计旨在让你通过集成 AWS AI 服务来解决不同的用例，并了解它们的工作原理。AWS 每天都在增长，并且会定期添加新的 AI 服务。

在本章中，你将以编程方式或从控制台处理不同的用例。这将帮助你理解不同的 API 及其使用方法。你将使用 S3 进行存储，并使用 AWS Lambda 执行任何代码。本章中的示例使用 Python，但你可以使用其他受支持的语言，如 Java、Node.js、.NET、PowerShell、Ruby 等。

你将涵盖以下主题：

- 使用 Amazon Rekognition 分析图像和视频
- 使用 Amazon Polly 将文本转换为语音
- 使用 Amazon Transcribe 将语音转换为文本
- 使用 Amazon Comprehend 实现自然语言处理
- 使用 Amazon Translate 翻译文档
- 使用 Amazon Textract 从文档中提取文本
- 在 Amazon Lex 上创建聊天机器人
- 使用 Amazon Forecast 进行时间序列预测

## 技术要求

本章你只需要一个 AWS 账户。

你可以从 GitHub 下载本章的代码示例，网址为：

https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/tree/main/Chapter08.

## 使用 Amazon Rekognition 分析图像和视频

如果你需要为应用程序添加强大的视觉分析功能，那么 Amazon Rekognition 是首选服务。Rekognition Image 让你可以轻松构建强大的应用程序来搜索、验证和组织数百万张图像。它让你从存储的或实时流媒体视频中提取基于运动的上下文，并帮助你分析它们。Rekognition Video 还允许你索引元数据，例如对象、活动、场景、名人和面部，从而轻松进行视频搜索。Rekognition Image 使用深度神经网络模型来检测和标记图像中的众多对象和场景。它可以帮助你捕获图像中的文本，有点像**光学字符识别（OCR）**。一个完美的例子是印有引语的 T 恤。如果你拍摄一张照片并要求 Amazon Rekognition 从中提取文本，它就能告诉你文本的内容。你也可以使用 Amazon Rekognition 进行名人识别。不是名人的人不会为其面部使用名人识别 API；相反，他们会使用面部比较 API。

官方文档，位于 [https://aws.amazon.com/rekognition/faqs/](https://aws.amazon.com/rekognition/faqs/)，指出：

> "With Rekognition Image, you only pay for the images you analyze and the face metadata you store. You will not be charged for the compute resources if, at any point of time, your training fails."

> "使用 Rekognition Image，你只需为分析的图像和存储的面部元数据付费。如果在任何时间训练失败，你不会被收取计算资源费用。"

Amazon Rekognition 的一些常见用例包括：

- 图像和视频分析
- 可搜索的图像库
- 基于面部的用户验证
- 情感分析
- 图像中的文本
- 面部识别
- 图像审核
- 视频档案的搜索索引
- 视频中露骨和暗示性内容的轻松过滤
- 露骨裸露示例 – 性活动、图形裸露、成人玩具等
- 暗示性内容示例 – 部分裸露、泳装或内衣等

## 探索 Amazon Rekognition 的优势

使用 Amazon Rekognition 的一些优势如下：

- AWS 管理其运行的基础设施。简而言之，只需为图像分析使用 API。你只需专注于构建和管理深度学习流水线。

无论是否了解图像处理知识，你都可以通过使用 Amazon Rekognition 提供的 API 来执行图像和视频分析，这些 API 可用于多个平台上的任何应用程序或服务。

- Labels API 的响应将通过 DetectLabels API 识别图像中的现实世界实体。这些标签包括城市、城镇、表格、家庭、花园、动物、宠物、食物、饮料、电子产品、花卉等。实体根据其置信度分数进行分类，该分数表示给定预测正确的可能性——分数越高越好。同样，你可以使用 DetectText API 提取图像中的文本。Amazon Rekognition 可能会根据单词之间的间隙检测多行。句号不代表行尾。

- Amazon Rekognition 可以与 AWS Kinesis Video Stream、AWS S3 和 AWS Lambda 集成，实现无缝且经济高效的图像和视频分析。借助 AWS IAM 服务，Amazon Rekognition API 调用可以轻松地进行保护和控制。

- 低成本：你只需为分析的图像和视频付费。

- 通过 AWS CloudTrail，Amazon Rekognition 的所有 API 调用都可以作为事件捕获。它捕获从控制台、CLI 或 API 代码调用发起的所有调用，这进一步使用户能够根据 CloudTrail 事件创建 Amazon SNS 通知。

- 你可以为特定 API 调用创建 VPC 端点策略，以在你的 VPC 和 Amazon Rekognition 之间建立私有连接。这有助于你利用增强的安全性。根据 AWS 共同责任模型，AWS 负责基础设施和软件的安全，而你需要负责云中内容的安全。

## 使用 Amazon Rekognition 进行实操

在本节中，你将学习如何将 AWS Lambda 与 Amazon Rekognition 集成，以检测图像中的标签（图像上传于 https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/tree/main/Chapter08/Amazon%20Rekognition%20Demo/images），并在 CloudWatch 控制台中打印检测到的对象。你将在代码中使用 Amazon Rekognition 的 `detect_labels` API。

你将首先为 Lambda 创建一个 IAM 角色：

1. 导航到 IAM 控制台页面。
2. 从左侧菜单中选择 Roles。
3. 选择 Create role。
4. 在 Choose a use case 部分中选择 Lambda。
5. 添加以下托管策略：
   - AmazonS3ReadOnlyAccess
   - AmazonRekognitionFullAccess
   - CloudWatchLogsFullAccess
6. 将角色命名为 rekognition-lambda-role：

![](img/87c29232224b00f5a8bba6a66a391700_203_0.png)

### 图 8.1 – 创建角色对话框

接下来，你将创建一个 Lambda 函数。

7. 导航到 AWS Lambda 控制台页面。
8. 选择 **创建函数**。
9. 创建函数：
   - 选择 **从头创作**。
   - 为函数命名，例如 `lambda-rekognition`。
   - 从 **运行时** 下拉列表中选择 **Python 3.6**。
   - 选择 **使用现有角色**。添加先前创建的角色名称，即 `rekognition-lambda-role`：

### 基本信息

### 图 8.2 – 创建 Lambda 函数

10. 在 lambda_function.py 中输入以下代码：

```
from __future__ import print_function
import boto3
def lambda_handler(event, context):
    print("=======lambda_handler started=======")
    # read the bucket name (key) from the event
    name_of_the_bucket=event['Records'][0]['s3']['bucket']['name']
    # read the object from the event
    name_of_the_photo=event['Records'][0]['s3']['object']['key']
    detect_labels(name_of_the_photo,name_of_the_bucket)
    print("Labels detected Successfully")
def detect_labels(photo, bucket):
    client=boto3.client('rekognition')
    response=client.detect_labels(Image={'S3Object':{'Bucket':bucket,'Name':photo}})
    print('Detected labels for ' + photo)
    print('===================================================')
    for label in response['Labels']:
        print ("Label: " + label['Name'])
        print ("Confidence: " + str(label['Confidence']))
        print ("Instances:")
        for instance in label['Instances']:
            print (" Bounding box")
            print ("Top:" + str(instance['BoundingBox']['Top']))
            print ("Left:" + str(instance['BoundingBox']['Left']))
```

