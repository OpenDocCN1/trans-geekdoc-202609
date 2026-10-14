

## 6. D
`inf1.2xlarge` 实例类型专为高性能推理工作负载设计。它提供高吞吐量和低延迟，使其成为实时应用程序的理想选择。此外，`Inf1` 实例针对机器学习推理进行了优化，并由 AWS Inferentia 芯片提供支持，这些芯片是专为深度学习工作负载定制的。这确保了高效且具有成本效益的推理。`Inf1` 实例在性能和成本之间取得了平衡，与基于 GPU 的实例相比，为推理任务提供了显著的成本节约。答案 A（`t3.medium`）和 B（`r5.4xlarge`）不正确，因为前者计算能力有限，后者是内存优化型，使它们不适合高性能推理。答案 C 不是最佳选项，因为 `g4dn.xlarge` 实例对于大规模推理工作负载可能不如 `Inf1` 实例具有成本效益，尽管 `g4dn` 实例基于 GPU，适合训练和推理。

## 7. B
Amazon SageMaker Serverless Inference 会根据传入请求的量自动扩展资源。这使其成为处理间歇性或不可预测流量模式的理想选择，确保您仅在使用计算容量时为其付费。虽然 Amazon SageMaker Serverless Inference 可以处理实时预测，但低延迟要求可能更适合由 Amazon SageMaker Real-time Inference 端点和自动扩展来服务。Amazon SageMaker Serverless Inference 不适合高吞吐量批处理。对于此用例，您应考虑使用 Amazon SageMaker Batch Transform。大负载和长处理时间可能受益于能更有效地处理资源密集型工作负载的专用实例，而不是 Amazon SageMaker Serverless Inference。因此，答案 A、C、D 不正确。

## 8. B
AWS Step Functions 非常适合编排涉及条件逻辑、错误处理、并行处理等的复杂工作流。这使其成为管理具有各种步骤和依赖关系的复杂 ML 工作流的稳健选择。虽然 AWS Step Functions 可以自动化 ETL 任务，但它功能更强大且更适合复杂工作流。对于简单的 ETL 任务，AWS Glue 或 Amazon MWAA 等服务可能更合适。AWS Step Functions 不为 ML 项目提供预构建模板，也不执行偏差检测和模型预测解释。要利用 ML 项目的预构建模板，应使用 Amazon SageMaker Pipelines。要执行偏差检测和解释模型预测，应使用 Amazon SageMaker Clarify。因此，答案 A、C、D 不正确。

## 9. B
Amazon SageMaker Model Registry 提供模型版本控制等功能，允许您跟踪模型的不同版本；审批工作流，使您能够控制和管理模型在不同阶段之间的转换；以及部署自动化，简化将模型部署到生产环境的过程。这些功能使其成为在 CI/CD 管道中高效管理和部署模型的理想选择。Amazon SageMaker Model Registry 不提供模型监控和偏差检测功能。前者由 Amazon SageMaker Model Monitor 提供，后者由 Amazon SageMaker Clarify 提供。它不简化数据预处理和特征工程。Amazon SageMaker Data Wrangler 和 Amazon SageMaker Feature Store 等服务适合这些功能。虽然 Amazon SageMaker Model Registry 可以成为包含 AWS Step Functions 的更广泛工作流的一部分，但其主要功能不涉及编排 ML 工作流。因此，答案 A、C、D 不正确。

## 10. B
Amazon Bedrock Converse API 专为实时处理自然语言理解（NLU）和自然语言生成（NLG）任务而设计。该 API 可以处理和生成类人文本，使其适用于聊天机器人、虚拟助手和其他对话式 AI 系统等应用。管理和部署 ML 模型通常由 Amazon SageMaker Model Registry、Amazon SageMaker Endpoints 和 Amazon SageMaker Pipelines 等服务处理。Amazon Bedrock Converse API 专注于 NLU 和 NLG 任务。数据预处理和特征工理由 Amazon SageMaker Data Wrangler 和 Amazon SageMaker Feature Store 等服务处理。针对不同硬件平台优化模型通常使用 Amazon SageMaker Neo 等工具完成。Bedrock Converse API 不执行模型优化任务。因此，答案 A、C、D 不正确。

# 第 7 章：模型监控与成本优化

## 1. C
模型漂移会导致模型做出不准确的预测，进而可能导致糟糕的决策。此外，在受监管的行业中，未能维持模型准确性可能导致不合规，从而带来潜在的法律和财务后果。忽略模型漂移不会提高计算效率。相反，由于预测不准确，它可能会降低模型效率。模型漂移会导致随着时间推移预测变得不准确，因为模型的性能会随着其不再与当前数据分布一致而下降。不解决模型漂移不会提高模型可解释性。它实际上会恶化模型的性能和可靠性，使结果更难以信任和解释。因此，答案 A、B、D 不正确。

## 2. C
Amazon SageMaker Model Monitor 专为持续监控机器学习模型的数据质量问题、概念漂移和异常而设计。它可以自动检测与预期基线的偏差，并在检测到异常时发送警报。AWS Glue 主要用于提取、转换、加载（ETL）任务，以准备和转换数据供分析，但它不提供实时异常检测和监控功能。AWS Step Functions 是一种工作流服务，可将多个 AWS 服务协调到无服务器工作流中。虽然它可以帮助编排任务，但它不提供对实时数据中异常的持续监控。AWS CodePipeline 是一种持续集成/持续交付（CI/CD）服务，用于自动化应用程序的构建、测试和部署。它不提供实时异常检测和监控。因此，答案 A、B、D 不正确。

## 3. A
平均绝对误差（MAE）、均方根误差（RMSE）和接收者操作特征（ROC）曲线等指标直接与评估机器学习模型的性能相关。MAE 和 RMSE 是回归任务的常用指标，分别测量平均误差和平均平方误差的平方根。ROC 曲线用于分类任务，提供模型真正例率与假正例率的图形表示。选项 B、C、D 中指定的指标都与模型性能无关，因此不正确。

## 4. C
数据质量差可能会引入偏差并导致模型预测不准确。如果输入数据不具代表性、包含错误或存在偏差，模型将学习并传播这些问题，导致不可靠的预测和潜在的不公平结果。未能监控数据质量不会增强模型可扩展性。监控数据质量不会直接影响特征工程的需求。数据质量不会直接影响模型训练的速度。因此，答案 A、B、D 不正确。

