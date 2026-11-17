

## 批量转换作业

在此 **场景** 中，您拥有一个大型数据集，并希望使用训练好的模型对整个数据集进行批量推理。

## 解决方案

使用 SageMaker 批量转换来以批处理方式处理整个数据集。

## 步骤

- 1. 创建 SageMaker 转换器。
- 2. 启动批量转换作业。

## 示例代码片段

```
from sagemaker.transformer import Transformer
transformer = Transformer(model_name='your-model-name',
                        instance_count=1,
                        instance_type='ml.m4.xlarge',
                        strategy='SingleRecord',
                        assemble_with='Line',
                        output_path='s3://your-s3-bucket/output')
transformer.transform('s3://your-s3-bucket/input/data.csv', content_type='text/csv')
transformer.wait()
```

## 多模型端点部署

在此 **场景** 中，您有多个模型版本，并希望将它们部署到单个端点上以进行 A/B 测试或逐步发布。

## 解决方案

使用 SageMaker 多模型端点在单个端点上部署和管理多个模型。

## 步骤

- 1. 创建并训练多个模型。
- 2. 创建 SageMaker 多模型。
- 3. 将多模型部署到端点。

## 示例代码片段

```
from sagemaker.multimodel import MultiModel
multi_model = MultiModel(model_data_prefix='s3://your-s3-bucket/multi-models')
predictor = multi_model.deploy(instance_type='ml.m4.xlarge', endpoint_name='multi-model-endpoint')
```

## 端点自动缩放

在此场景中，您的应用程序经历不同的工作负载，并希望根据流量自动调整实例数量。

## 解决方案

为 SageMaker 端点启用自动缩放。

## 步骤

- 1. 配置 SageMaker 端点以使用自动缩放。
- 2. 根据预期工作负载设置最小和最大实例数量。

## 示例代码片段

```
from sagemaker.predictor import Predictor
predictor = Predictor(endpoint_name='your-endpoint-name',
                      sagemaker_session=sagemaker_session)
predictor.predict('input_data')
```

## 使用 AWS Lambda 和 SageMaker 构建无服务器 API

在此场景中，您希望使用 AWS Lambda 创建无服务器 API 以与您的 SageMaker 模型交互。

## 解决方案

使用 AWS Lambda 调用 SageMaker 端点。

## 步骤

- 1. 创建 AWS Lambda 函数。
- 2. 将 Lambda 函数与 SageMaker 端点集成。

## 示例代码片段

```
import boto3
import json
def lambda_handler(event, context):
    # Perform preprocessing on input data
    input_data = event['input_data']
    # Call SageMaker endpoint
    # ...
    return {
        'statusCode': 200,
        'body': json.dumps('Inference successful!')
    }
```

在部署机器学习模型的领域中，Amazon SageMaker 成为一个强大的选择。其托管环境、可扩展性功能以及与其他 AWS 服务的无缝集成，使其成为企业应对多样化部署场景的高效可靠解决方案。无论您是预期高流量还是需要轻松的部署体验，SageMaker 都是您在模型部署卓越之旅中的盟友。在下一节中，您将学习如何使用 Lambda 函数创建管道。

## 使用 Lambda 函数创建替代管道

确实，SageMaker 是一个很棒的平台，您可以用它来创建训练和推理管道。但是，您始终可以使用不同的服务来实现类似的解决方案。其中一项您将在接下来了解的服务，被称为 **Lambda 函数**。

AWS Lambda 是一个无服务器计算服务，您可以在其中以服务形式运行函数。换句话说，您可以专注于编写函数。然后，您只需告诉 AWS 如何运行它（即环境和资源配置），所有必要的资源都将被分配来运行您的代码，并在完成后停止。

在 *第 3 章，用于数据迁移和处理的 AWS 服务* 中，您探索了 Lambda 函数如何与许多不同的服务（如 Kinesis 和 AWS Batch）集成。确实，AWS 在将 Lambda 与 140 多个服务（且列表不断增加）集成方面做得非常好。这意味着，当您使用特定的 AWS 服务时，您会记得它很可能与 Lambda 集成。

务必牢记这一点，因为 Lambda 函数可以真正扩展您创建可扩展和集成架构的可能性。例如，当文件上传到 S3 时，您可以触发 Lambda 函数，以便在将数据加载到 Redshift 之前对其进行预处理。或者，您可以创建一个在每个端点执行时触发 Lambda 函数的 API。同样，借助此强大服务，可能性是无限的。

同样有用的是，您可以使用不同的编程语言编写函数，例如 Node.js、Python、Go、Java 等。您的函数不一定必须由其他 AWS 服务触发——也就是说，您可以例如为 Web 或移动应用程序手动触发它。

谈到部署，您可以将函数作为 ZIP 文件或容器映像上传。虽然这对于自动化部署流程来说并不理想，但直接在 AWS Lambda 控制台中编写代码也是可能的。

与任何其他服务一样，该服务也有一些您应该了解的缺点：

- 您的函数内存分配：范围从 128 MB 到 10,240 MB（AWS 最近已将此限制从 3 GB 提高到 10 GB，如前所述）
- 函数超时：最长为 900 秒（15 分钟）
- 函数层：最多五个层
- 突发并发：根据 AWS 区域不同，范围从 500 到 3,000
- 部署包大小：未压缩时为 250 MB，包括层
- 容器映像代码包大小：10 GB
- /tmp 目录中的可用空间：512 MB

在选择 Lambda 函数之前，请确保这些限制符合您的用例。通过将 Lambda 函数引入您的 SageMaker 替代管道范围，您可以利用 Lambda 的一个潜在用途，即为模型创建推理管道。

如您所知，SageMaker 有一个非常实用的 `.deploy()` 方法，可用于为模型推理创建端点。这样您就可以调用它来传递输入数据并接收预测结果。在此，您可以使用 API 网关和 Lambda 函数创建此推理端点。

如果您不需要推理端点，只想进行预测并将结果存储在某处（以批量方式），那么您只需要一个 Lambda 函数，它能够获取输入数据、实例化模型对象、进行预测，并将结果存储在相应的位置。当然，它会在考虑之前讨论的所有限制的情况下执行此操作。

好了，现在您已经对 Lambda 及其一些用例有了良好了解，您可以查看考试中应了解的最重要配置。

## 创建和配置 Lambda 函数

首先，您应该知道可以通过不同方式创建 Lambda 函数，例如通过 AWS CLI（Lambda API 参考）、AWS Lambda 控制台，甚至部署框架（例如，*无服务器框架*）。

无服务器框架通常与提供商和编程语言无关。也就是说，它们通常允许您从各种云提供商和编程语言列表中选择要部署无服务器基础设施的位置。

## 重要说明

*无服务器架构的概念并非 AWS 特有。事实上，许多云提供商提供与 AWS Lambda 函数类似的其他服务。这就是构建这些无服务器框架的原因——为了帮助开发人员和工程师部署他们的服务，无论他们想在哪里部署，包括 AWS。这不太可能在您的考试中出现，但这是您应该知道的事情，以便作为数据科学家或数据工程师了解解决挑战的不同方式。*

由于您希望通过 AWS 认证机器学习专业考试，在此，您将通过 AWS Lambda 控制台进行操作。这样您就能更熟悉其界面和最重要的配置选项。

当您导航到 Lambda 控制台并请求新的 Lambda 函数时，AWS 将为您提供一些入门选项：

- **从零开始创建**：如果您想从零开始创建函数，请选择此项
- **使用蓝图**：如果您想使用示例代码和常见用例的配置预设创建函数，请选择此项
- **容器映像**：如果您想选择容器映像来部署函数，请选择此项
- **浏览无服务器应用程序库**：如果您想从 AWS 无服务器应用程序库部署示例 Lambda 应用程序，请选择此项

从零开始，下一步是设置 Lambda 配置。AWS 将这些配置分为基本设置和高级设置。在基本配置中，您将设置函数名称、运行时环境和权限。_图 10.1_ 显示了这些配置：

