

```python
import boto3

# Create an EventBridge client
client = boto3.client('events')

# Create an EventBridge rule
response = client.put_rule(
    Name='MyMLPipelineRule',
    EventPattern='{\n  "source": ["aws.s3"],\n  "detail-type": ["AWS API Call via CloudTrail"],\n  "detail": {\n    "eventSource": ["s3.amazonaws.com"],\n    "eventName": ["PutObject"]\n  }\n}',
    State='ENABLED',
    Description='Rule to trigger MyMLPipeline when a new object is uploaded to S3'
)

# Add targets to the rule
response = client.put_targets(
    Rule='MyMLPipelineRule',
    Targets=[
        {
            'Id': '1',
            'Arn': 'arn:aws:states:us-east-1:123456789012:stateMachine:MyMLPipeline'
        }
    ]
)
```

### 执行管道

或者，您也可以使用 Amazon SageMaker SDK 手动启动管道执行。如果管道内的步骤之间没有依赖关系，也可以并发执行，从而实现更高效的处理并缩短总运行时间：

```python
pipeline.start()
```

### 关键考量

使用 Amazon SageMaker Pipelines 时，可扩展性是一大显著优势，因为它会自动管理并扩展所需基础设施，确保您的 ML 工作流高效可靠地运行。但是，实施稳健的监控和日志记录以跟踪管道性能并排查可能出现的任何问题，是您作为 ML 工程师的责任。这种集成有助于维护管道的健康状况并确保操作顺畅。错误处理是另一个需要考虑的关键方面。Amazon SageMaker Pipelines 提供内置的错误处理功能，如果任何步骤发生错误，将暂停流程，并发送通知以提醒相关团队成员。这确保了错误能得到及时处理，维护工作流的完整性。

并发性也是 Amazon SageMaker Pipelines 中的一个重要考量因素。如果管道内的步骤之间没有依赖关系，则可以并发执行，从而优化处理时间和效率。这种并发执行允许更高效地利用资源并缩短总运行时间。通过自动化这些关键方面——可扩展性、监控、错误处理和并发性——您可以确保 ML 流程不仅有效，而且具有弹性，能够适应不断变化的需求。

## 模型部署深度示例

在本节中，我们将扩展 [第 5 章](#c005.xhtml#c005) 中的模型调优深度示例，通过无服务器推理终端节点暴露最佳模型。我们还将通过创建一个简单的推理请求来测试已部署的终端节点，并让无服务器终端节点根据该请求生成预测。

为求简单、降低成本和节省时间，我们将使用 3 个作业（而不是 20 个）来选择最佳模型：即准确率最高的模型。

作为一个快速提醒，[第 5 章](#c005.xhtml#c005) 末尾的深度示例旨在使用 Amazon SageMaker AI 自动模型调优 (AMT) 和贝叶斯优化策略，评估 XGBoost 算法在 Digits 数据集上的性能。

本示例的预期结果是一个以无服务器推理终端节点形式运行的模型部署，它能够接收推理请求并生成准确的预测。推理请求是手写数字的 CSV 表示，由已部署的模型处理以预测相应的数字类别。

我使用 Amazon SageMaker Studio 的代码编辑器功能运行了此 Python 程序：

