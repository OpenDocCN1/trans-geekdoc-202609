

考虑到这些功能需求，以下架构图展示了一个使用 Amazon Personalize 作为推荐引擎的电子商务架构：

![](OEBPS/Images/B20836_11_03.png)

图 11.3：电子商务网站和推荐架构

在此架构中，我们使用 Personalize 作为推荐引擎，为在线用户体验和目标用户营销体验提供支持。

RDS 数据库、DynamoDB 和 Elasticsearch 是项目、用户和交互数据的主要数据源。Glue ETL 作业用于将源数据转换为构建 Personalize 解决方案所需的数据集。

一旦 Personalize 解决方案经过评估并满足所需标准，它将作为 Personalize 部署活动部署，以服务访问电子商务网站的客户的推荐请求。

Amazon Pinpoint 是一项托管的目标营销服务。您可以使用 Pinpoint 来管理用户细分并发送电子邮件和 SMS 营销活动。在此架构中，Pinpoint 服务会为一组目标客户获取推荐产品列表，并向这些用户发送带有个性化推荐的电子邮件或 SMS 营销活动。

## 使用智能搜索实现客户自助服务自动化

良好的客户服务可以提高客户满意度并建立长期的客户忠诚度。然而，客户支持非常耗费人力，并且由于长时间的等待时间和缺乏知识的支持代理，可能会导致客户满意度低下。客户自助服务功能已被不同行业的组织广泛采用，以减少客户支持呼叫量并提高客户满意度。

在客户自助服务场景中，我们可以识别出以下机器学习问题：

*   `Automatic speech recognition` (`ASR`): 此机器学习任务识别人类语音并将其转换为文本，然后使用 NLU 来理解文本的含义。

*   `Natural language understanding` (`NLU`): NLU 是 NLP 的一个子领域，它处理意图理解和阅读理解。NLU 关注文本的含义和意图。例如，如果文本是 `Can I get the cash balance in my savings account?`，那么这里的意图是 `get account balance`。NLU 的另一个示例是根据问题和文本的语义含义来理解文本并从中提取特定信息。

*   `Text to speech`: 此机器学习任务将文本转换为自然的人类声音。

以下图示展示了一个示例架构，用于为客户实现自助聊天功能，以便客户查询客户相关详细信息，以及一般信息和常见问题解答：

![](OEBPS/Images/B20836_11_04.png)

图 11.4：带有智能虚拟助手的自助服务聊天门户

在此架构中，Amazon Lex 机器人用于为客户互动提供基于文本的对话界面。客户使用自助服务聊天门户发起对话，聊天门户通过 Lex API 与 Lex 机器人集成。

Lex 机器人支持多种不同的意图，例如 `look up account info`、`update customer profile` 和 `How do I return a purchase?`。

根据意图，Lex 机器人会将执行请求路由到不同的后端。对于客户账户相关的查询，它将使用 Lambda 函数进行执行。对于信息搜索相关的问题，Lex 机器人会将查询发送到 Kendra 索引以进行执行。

在探索了各种 AI 服务及其实际业务应用之后，后续部分将重点介绍与采用这些服务相关的运营考量。这包括深入探讨 MLOps、代码提升和监控流程，以提升 AI 实现的运营效率。

# 为 AI 服务设计 MLOps 架构

实现自定义 AI 服务模型需要一个数据工程、模型训练和模型部署管道。此过程与使用 ML 平台构建、训练和部署模型的过程类似。因此，我们也可以在大规模运行 AI 服务时采用 MLOps 实践。

从根本上讲，AI 服务的 MLOps 旨在提供与 ML 平台的 MLOps 类似的优势，包括流程一致性、工具可重用性、可重现性、交付可扩展性和可审计性。在架构上，我们可以为 AI 服务实现类似的 MLOps 模式。

## AI 服务和 MLOps 的 AWS 账户设置策略

为了隔离不同的环境，我们可以采用多账户策略来配置 AI 服务的 MLOps 环境。以下图示展示了多账户 AWS 环境的设计模式。根据您组织对职责分离和控制的要求，您也可以考虑将这些整合到更少的环境中：

![](OEBPS/Images/B20836_11_05.png)

图 11.5：AWS 上 AI 服务的 MLOps 架构

在此多账户 AWS 环境中，开发人员使用自定义模型开发环境来构建和测试数据工程、模型训练和模型部署的管道。准备就绪后，管道将被提升到模型开发环境中，使用生产训练数据进行正式的模型构建和测试。由于训练好的 AI 服务模型通常无法导出，我们需要在生产环境中复制模型训练工作流以进行模型部署。

共享服务环境托管 CI/CD 工具，例如 AWS CodePipeline 和 AWS CodeBuild。您使用 CI/CD 工具为在不同环境中运行的数据工程、模型构建和模型部署构建不同的管道。例如，UAT 环境的管道可能包含以下组件和步骤：

*   `CodePipeline definition`: 此定义将包含一个 CodeBuild 步骤、一个 CloudFormation 执行步骤和一个 Step Functions 工作流执行步骤。

*   `CodeBuild step`: CodeBuild 步骤会丰富 CloudFormation 模板，添加创建 Step Functions 工作流所需的额外输入，该工作流用于编排数据工程、数据集创建、数据摄取、模型训练和模型部署。

*   `CloudFormation execution step`: 此步骤执行 CloudFormation 模板以创建 Step Functions 工作流。

*   `Step Functions workflow execution step`: 此步骤启动 Step Functions 工作流以运行工作流中的各种步骤，例如数据工程和模型训练。例如，如果我们为 Personalize 模型训练和部署构建一个 Step Functions 工作流，该工作流将包含六个步骤：创建数据集组、创建数据集、导入数据集、创建解决方案、创建解决方案版本和创建活动。

在多账户环境中，还可能存在用于数据管理、监控和安全性的其他专用账户。

## 环境间的代码提升

与我们用于 ML 平台的模式类似，我们可以使用代码仓库作为将代码提升到不同环境的机制。例如，在代码开发期间，开发人员会创建代码工件，例如 Glue ETL 作业的数据工程脚本、CloudFormation 模板骨架，以及构建规范文件，供 CodeBuild 运行不同的命令。一旦代码被认为已准备好提升到正式模型构建和测试，开发人员就会将代码检入代码仓库的发布分支中。代码检入事件可以触发 CodePipeline 作业，在共享服务中运行 CodeBuild 步骤，然后在模型开发环境中运行 Step Functions 工作流步骤。当准备好进行生产发布时，可以在共享服务环境中触发部署 CodePipeline 作业，以执行 CloudFormation 模板并在生产环境中部署模型。

## 监控 AI 服务的运营指标

