

# 模型实现和用户验收测试报告

ML 平台在 ML 治理文档中的作用通常是提供数据点，以供正式风险管理文档使用，或生成一些现成可用的报告。具体来说，ML 平台应能够跟踪、存储和报告以下数据点：

* `Data quality metrics`，例如数据描述、统计信息、偏差和错误
* `Model metrics` 和开发及测试中的验证结果
* `Model bias` 和可解释性报告
* `Model performance monitoring` 在生产环境中的结果
* `Model description` 和预期用途
* `Risk rating` 和分类详情

不同的 ML 平台在支持 AI 治理文档要求方面具有不同的能力。这里，我们将讨论 SageMaker 支持这些要求的各种能力。SageMaker 可以生成可纳入模型风险文档的数据和文档。这包括跟踪和生成与 AI 治理文档相关的信息，例如：

* **`Model metrics`**：SageMaker 训练服务跟踪模型指标，例如训练错误和验证错误。
* **`Data and model bias reports`**：SageMaker Clarify 是 SageMaker 中的偏差检测组件。如果启用 SageMaker Clarify，您可以获取训练数据和训练模型的数据和模型偏差报告。数据和模型偏差报告包含详细信息，例如训练数据中的不平衡情况以及不同年龄组和性别的预测行为。
* **`Model explainability reports`**：SageMaker Clarify 还提供模型可解释性功能。它使用 SHAP 来解释每个输入对最终决策的贡献。您可以在 [https://shap.readthedocs.io/en/latest/index.html](https://shap.readthedocs.io/en/latest/index.html) 上了解有关 SHAP 的更多详细信息。
* **`Model Card`**：SageMaker Model Card 可用于记录 ML 模型的关键信息，例如模型的预期用途、风险评级以及模型训练和性能的详细描述。

开源和托管模型注册表平台均可用于管理模型注册表。例如，MLflow Model Registry 是一个开源选项，而 Amazon SageMaker 提供托管模型注册表服务。SageMaker Model Registry 具有几个关键功能，可帮助进行 ML 治理活动和流程：

* **`Model inventory`**：SageMaker Model Registry 中的不同模型的所有版本都属于各自的模型组。您可以在此处查看所有模型组和模型的不同版本。模型指标、训练作业详情、训练使用的超参数和训练数据源等元数据是模型审查和模型审计流程的重要数据点。根据特定业务要求，您可以为单个企业视图设置中央模型注册表，或者如果满足治理和审计要求，可以设置分布式模型注册表。
* **`Model approval and lifecycle tracking`**：您可以直接在 SageMaker Model Registry 中跟踪模型和模型阶段的审批情况。此详细信息有助于业务运营和审计，以确保遵循适当的流程。

部署后监控模型对于识别任何潜在故障并采取及时补救措施来降低风险至关重要。为了确保平稳运行，必须监控模型的系统可用性和错误，以及数据和模型漂移和预测失败。Amazon SageMaker 提供模型监控功能，可以检测数据漂移和模型漂移。SageMaker Model Monitor 提供以下功能：

* **`Data drift`**：使用 SageMaker Model Monitor，您可以监控生产环境中的数据质量问题和数据分布偏差（即数据漂移）。要使用此功能，您需要使用基准数据集（例如模型训练数据集）创建基准，以获取数据统计信息和数据类型，并建议监控约束。SageMaker Model Monitor 可以捕获实时推理流量，计算数据统计信息，检查数据类型，根据约束进行验证，并触发警报。例如，如果某个特征的均值和标准偏差与基准相比发生显著变化，可以触发警报。
* **`Model performance drift`**：您可以使用 SageMaker Model Monitor 检测生产环境中的模型性能变化。要使用此功能，您需要使用包含输入和标签的基准数据集创建模型性能基准作业。基准作业将建议约束，这些约束是模型监控将与使用生产环境中收集的真实数据计算的指标进行比较的指标阈值。指标可以选择发送到 CloudWatch 以进行可视化。
* **`Feature attribution drift`**：当与 SageMaker Clarify 结合使用时，SageMaker Model Monitor 可以报告特征归因漂移。特征归因是特征对预测输出重要性的指标。与数据和模型漂移类似，您需要使用基准数据创建 SHAP 基准作业以生成约束建议。然后将安排单独的监控作业，以监控生产环境中的预测与基准的对比情况。

## 血缘和可重复性

MRM 要求在数据和模型之间建立血缘关系，以确保可重复性。血缘是对数据的来源、转换和依赖关系以及 ML 模型的开发和演变进行系统跟踪和文档记录，在整个过程中提供透明度和问责制。血缘信息包括训练数据源、算法选择、超参数配置和模型训练脚本。SageMaker 提供多种有助于建立血缘关系的功能：

* SageMaker 训练作业保留血缘数据，例如训练数据源、训练作业容器（包含算法和训练脚本）、超参数配置和模型工件位置。出于记录保留目的，SageMaker 环境中的历史训练作业数据是不可更改的。
* SageMaker Experiments 和 ML Lineage Tracking 可以包含其他组件详细信息，例如数据处理，以进行更完整的血缘跟踪。
* SageMaker 托管包含有关原始模型工件位置和推理容器的信息，以追踪从模型到端点的血缘关系。

这些血缘数据点（例如训练数据源和训练配置）可以通过调用 SageMaker API 获取；外部应用程序可以直接调用 SageMaker API 以提取这些数据用于审查目的。或者，可以开发数据提取作业来提取这些数据点并将其加载到专门构建的风险管理存储中以进行分析。

ML 隐私在 ML 系统实施中的重要性正在迅速增长。为了遵守数据隐私法规或内部数据隐私控制，ML 系统必须具有基本的基础架构安全功能，例如数据加密、网络隔离、计算隔离和私有连接。通过使用基于 SageMaker 的 ML 平台，您可以启用以下基本安全控制：

* **`Private networking`**：由于 SageMaker 是完全托管的服务，它在 AWS 拥有的账户中运行。默认情况下，您自己 AWS 账户中的资源通过公共互联网与 SageMaker API 通信。要从您自己的 AWS 环境启用到 SageMaker 组件的私有连接，您可以将它们附加到您自己的 `virtual private cloud` (`VPC`) 中的子网。
* **`Storage encryption`**：在创建 SageMaker 笔记本、训练作业、处理作业或托管端点时，通过提供加密密钥可以启用静态数据加密。

