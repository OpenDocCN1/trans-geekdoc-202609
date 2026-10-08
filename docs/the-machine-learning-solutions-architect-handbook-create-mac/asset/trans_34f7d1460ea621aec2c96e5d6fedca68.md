

# ML 流水线监控

需要对 ML 流水线的执行状态和错误进行监控，以便根据需要采取纠正措施。在流水线执行期间，存在流水线层级的状态/事件，以及阶段级和操作层级的状态/事件。你可以使用这些事件和状态来了解每个流水线和阶段的进度，并在出现问题时获取警报。下图显示了 AWS CodePipeline、CodeBuild 和 CodeCommit 如何与 CloudWatch、CloudWatch Logs 和 EventBridge 配合用于通用状态监控、报告以及问题排除：

![](img/bd21298357d48415447ff0b2f138b_303.png)

CodeBuild 可以发送指标，例如成功构建（SucceededBuilds）、失败构建（FailedBuilds）和持续时间（Duration）。这些指标可以通过 CodeBuild 控制台和 CloudWatch 仪表板访问。

CodeBuild、CodeCommit 和 CodePipeline 可以向 EventBridge 发事件以报告状态更改并触发自定义事件处理（例如通知），或将事件记录到另一个存储库进行归档。所有三个服务都可以将详细日志发送到 CloudWatch，以支持故障排除等操作。

Step Functions 为 CloudWatch 提供了一系列指标，例如执行指标（如执行失败、中止、超时）和活动指标（如活动开始、成功）。你可以在管理控制台中查看这些指标，并为警报设置阈值。

# 服务配置

企业级 ML 平台的另一个关键组件是服务配置。对于大规模的配置和部署，应该采用自动化流程。在这里，我们将关注 ML 平台本身的配置，而不是 AWS 账户和网络的配置（这些应作为 ML 平台配置的基础）。对于 ML 平台的配置，主要有两个任务：

- 数据科学环境配置：为科学家配置数据科学环境，主要包括提供实验工具，以及访问预构建的 ML 自动化流水线的权限。
- ML 自动化流水线配置：需要为数据科学家和 MLOps 工程师预配置 ML 自动化流水线，以便他们自动化容器训练和模型部署等任务。

在 AWS 上自动化服务配置有多种技术方法，例如使用脚本、CloudFormation 和 AWS CDK。通过脚本，你可以顺序调用 AWS CLI 命令来配置不同的组件，例如创建 SageMaker notebook。CloudFormation 是用于 AWS 基础设施部署的 IaC（基础设施即代码）服务。通过 CloudFormation，你创建模板来描述要作为单个栈启动所需的资源和依赖项。当模板执行时，栈中指定的所有资源和依赖项将自动部署。以下代码显示了部署 SageMaker domain 的模板：

```yaml
Type: AWS::SageMaker::Domain
Properties:
  NetworkAccessType: String
  AuthMode: String
  UserSettings:
    DomainName: String
  KmsKeyIds: String
  Subnets:
    - String
  VpcId: String
```

AWS CDK 允许你创建部署在 AWS 上的不同产品。这些产品可以包括 SageMaker notebooks、CodeCommit 存储库和 CodePipeline 定义。AWS CDK 使用 CloudFormation 模板来描述产品。通过 AWS CDK，管理员使用模板创建产品，按投资组合（portfolio）组织这些产品，并授予终端用户访问权限。终端用户从 CDK 组合访问这些产品。下图显示了创建 CDK 产品并从 CDK 服务启动它的流程：

![](img/bd21298357d48415447ff0b2f138b_305.png)

对于大规模和受治理的产品管理，CDK 是推荐的方法。CDK 支持多种部署选项，包括单个 AWS 账户和枢纽型（hub-and-spoke）部署。枢纽型部署允许你集中管理所有产品，并使其在不同的账户中可用。在我们的企业参考架构中，我们使用枢纽架构来支持数据科学环境和 ML 流水线的配置，如图所示：

![](img/bd21298357d48415447ff0b2f138b_306.png)

图 9.9 – 用于企业 ML 产品管理的枢纽型架构。在上述架构中，我们使用共享服务账户中的中心组合。所有产品（例如创建 SageMaker domains、用户配置文件、CodePipeline 定义和训练流水线定义）都在枢纽账户中进行集中管理。某些产品共享给不同的数据科学账户，为科学家和团队创建环境。其他产品共享给训练账户，以建立 ML 流水线。

到此，我们已经讨论了企业级 ML 平台的核心组件。接下来，让我们亲自动手构建一个用于自动化模型训练和部署的流水线。

# 实操练习 – 在 AWS 上构建 MLOps 流水线

在本次实操练习中，你将亲手构建一个简化版的企业级 MLOps 流水线。为了简单起见，我们不会使用企业模式的多账户架构。相反，我们将在单个 AWS 账户中构建多个核心功能。下图显示了你将构建的内容：

![](img/bd21298357d48415447ff0b2f138b_307.png)

图 9.10 – 实操练习的架构

在高级别，你将使用 CloudFormation 创建两个流水线：一个用于模型训练，一个用于模型部署。

 为 ML 训练流水线创建 CloudFormation 模板

在本节中，我们将创建两个执行以下操作的 CloudFormation 模板

- 第一个模板为 ML 模型训练工作流创建 AWS Step Functions，用于执行数据处理、模型训练和模型注册。这将训练流水线的一个组件。
- 第二个模板创建一个 CodePipeline ML 模型训练流水线定义，包含两个阶段：
    - 源阶段（source stage）：监听 CodeCommit 存储库的变化，以启动我们创建的 Step Functions 工作流的执行。
    - 部署阶段（deployment stage）：启动 ML 模型训练工作流的执行。

现在，让我们开始编写 Step Functions 工作流的 CloudFormation 模板：

- 创建一个名为 `AmazonSageMaker-StepFunctionsWorkflowExecutionRole` 的 Step Functions 执行角色。然后，创建并将其附加以下 IAM 策略。该角色将被 Step Functions 工作流使用，提供调用 SageMaker API 的权限。请记住新创建的 IAM 角色的 ARN，你将在下一步中需要它。你可以在此处找到完整的代码示例：https://github.com/PacktPublishing/The-Machine-Learning-Solutions-Architect-Handbook/blob/main/Chapter09/AmazonSageMaker-StepFunctionsWorkflowExecution-policy.json:

```json
{
  "Version" : "2012-10-17",
  "Statement": [
    {
      "Effect" : "Allow",
      "Action": [
        "sagemaker:CreateModel",
        "sagemaker:DeleteEndpointConfig",
        "sagemaker:DescribeTrainingJob",
        "sagemaker:CreateEndpoint",
        "sagemaker:StopTrainingJob",
        "sagemaker:CreateTrainingJob",
        "sagemaker:UpdateEndpoint",
        "sagemaker:CreateEndpointConfig",
        "sagemaker:DeleteEndpoint"
      ],
      "Resource" : [
        "arn:aws:sagemaker*:*:*:*"
      ]
    }
  ]
}
```

