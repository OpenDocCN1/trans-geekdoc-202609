

```yaml
EndpointConfig:
  Type: AWS::SageMaker::EndpointConfig
  Properties:
    ProductionVariants:
      - InitialInstanceCount: 1
        InitialVariantWeight: 1.0
        InstanceType: ml.m4.xlarge
        ModelName: !Ref ModelName
        VariantName: !Ref ModelName
  Outputs:
    EndpointId:
      Value: !Ref Endpoint
    EndpointName:
      Value: !GetAtt Endpoint.EndpointName
```

- 2 使用此文件创建 CloudFormation 栈，并验证 SageMaker 端点是否已创建。现在，将 `mldeployment.yaml` 文件上传到代码仓库目录并将更改提交到 CodeCommit。请注意，该文件将由 CodePipeline 部署流水线使用，我们将在后续步骤中创建它。
- 3 在创建部署流水线之前，我们需要一个模板配置文件，以便在执行部署模板时传递参数。在这里，我们需要将模型名称传递给部署模板。复制以下代码块，将其保存为名为 `mldeployment.json` 的文件，将其上传到 Studio 中的代码仓库目录，并将更改提交到 codecommit。

```json
{
  "Parameters": {
    "ModelName": <name of the financial sentiment model you have trained>
  }
}
```

- 4 现在，我们可以创建一个用于自动模型部署的 CodePipeline 流水线 CloudFormation 模板。该流水线有两个阶段：
    - I. 第一阶段从 CodeCommit 仓库获取源代码（例如我们刚刚创建的配置文件和 `mldeployment.yaml` 模板）。
    - II. 第二阶段为我们之前创建的 `mldeployment.yaml` 文件创建一个 CloudFormation 更改集（更改集是新模板与现有 CloudFormation 栈之间的差异）。它添加了一个手动审批步骤并部署 CloudFormation 模板文件 `mldeployment.yaml`。

此 CloudFormation 模板还会创建辅助资源，包括一个用于存储 CodePipeline 产物的 S3 桶、一个供 CodePipeline 运行的 IAM 角色，以及另一个供 CloudFormation 使用以执行 `mldeployment.yaml` 栈 IAM 角色。

- 5 复制以下代码块并将文件保存为 `mdeployment-pipeline.yaml`。你可以在 https://github.com/PacktPublishing/The-Machine-Learning-Solutions-Architect-Handbook/blob/main/Chapter09/mdeployment-pipeline.yaml 找到完整的代码集。

| Parameters |
| :--- | :--- |
| BranchName: |
| Description: CodeCommit branch name |
| Type: String |
| Default: master |
| RepositoryName: |
| Description: CodeCommit repository name |
| Type: String |
| Default: MLSA-repo |
| ProjectName: |
| Description: ML project name |
| Type: String |
| Default: FinanceSentiment |
| Description: SNS topic for NotificationArn |
| Default: arn:aws:sns:ca-central-1:300165273893:CodePipelineSNSTopicApproval |
| Type: String |
| ProdStackConfig |
| Default: mldeploymentconfig.json |
| Description: The configuration file name for the production WordPress stack |
| Type: String |
| StackName: Default: FinancesSentimentMLStack |
| Description: A name for the production WordPress stack |
| Type: String |
| TemplateFileName: Default: mldeployment.yaml |
| Description: The file name of the WordPress template |
| Type: String |
| ChangeSetName: Default: FinancesSentimentchangeset |
| Description: A name for the production stack change set |
| Type: String |
| Resources: CodePipelineArtifactStoreBucket: Type: 'AWS::S3::Bucket' |
| DeletionPolicy: Delete |
| Pipeline: ... |

- 6 现在，在 CloudFormation 控制台中启动新创建的 `mldeployment-pipeline.yaml` 模板以创建部署流水线，然后从 CodePipeline 控制台运行流水线。

恭喜！你已成功创建并运行了一个 CodePipeline 部署流水线，从 SageMaker 模型注册表部署了一个模型。

# 总结

在本章中，我们讨论了构建企业级 ML 平台的关键需求，以满足端到端 ML 生命周期支持、流程自动化和区分不同环境等等需求。我们还讨论了架构模式以及如何使用 AWS 服务在 AWS 上构建企业级 ML 平台。我们讨论了不同 ML 环境的核心能力，包括训练、托管和共享服务。你现在应该对企业级 ML 平台的构想，以及使用 AWS 服务构建该平台的关键考虑因素有了良好的理解。你还积累了一些构建 MLOps 架构组件以及自动化模型训练和部署的实践经验。在下一章中，我们将通过涵盖大规模分布式训练和实现低延迟推理的核心概念来讨论高级 ML 工程。

# 10
高级 ML 工程

恭喜你走到了这里。到目前，你应该对机器学习（ML）解决方案架构师在 ML 生命周期不同阶段进行有效工作所需的核心基础技能有了良好的理解。在本章中，我们将深入探讨几个高级 ML 主题。特别是，我们将涵盖针对大模型和大数据集的各种分布式模型训练选项。我们还将讨论减少模型推理延迟的各种技术方法。我们将通过一个分布式模型训练的实践实验结束本章。

具体而言，本章将涵盖以下主题：

- 使用分布式训练训练大规模模型
- 实现低延迟模型推理
- 实践实验——使用 PyTorch 运行分布式模型训练

# 技术要求

在本章的实践部分你需要访问你的 AWS 环境。所有的代码示例都位于 https://github.com/PacktPublishing/The-Machine-Learning-Solutions-Architect-Handbook/blob/Chapter10。

# 使用分布式训练训练大规模模型

随着 ML 算法变得越来越复杂，且可用于 ML 的数据变得越来越大，模型训练可能成为 ML 生命周期中的一个巨大瓶颈。在单机上使用大型数据集训练模型可能速度太慢，或者当模型大到无法放入设备内存时，根本无法实现。下面的图显示了近年来语言模型演进的速度以及在模型规模方面的增长情况：

# 语言模型规模的增长

![](img/bd21298357d8484151447ff0b2f138b_320.png)

图 10.1 – 语言模型的增长

为了解决用大数据训练大模型带来的挑战，我们可以转向分布式训练。分布式训练允许你跨节点或多个节点上的多个设备进行模型训练，这样你就可以将数据或模型拆分到这些设备和节点上进行模型训练。分布式训练主要有两种类型：**数据并行**（data parallelism）和**模型并行**（model parallelism）。在进入分布式训练的细节之前，让我们快速回顾一下神经网络是如何训练的：

![](img/bd21298357d8484151447ff0b2f138b_321.png)

图 10.2 – 深度神经网络训练

上图显示了**人工神经网络**（ANN）是如何训练的。训练数据通过正向传播馈给 ANN。在正向传播结束时计算损失（预测值与真实值之间的差异），反向传播则计算所有参数的梯度。这些参数在下一步中更新为新值，直到损失最小化。

在下一节中，我们将查看使用数据并行的分布式模型训练。

# 使用数据并行的分布式模型训练

数据并行分布式训练允许你将大型训练数据集拆分为较小的子集，并在不同的设备和节点上并行训练这些较小的子集。这允许你在可用设备上并行运行多个训练进程以加速训练。使用数据并行分布式训练需要底层的 ML 框架和或算法支持它。

