

# 通用基础模型

通用基础模型是多功能模型，可处理文本生成、翻译、摘要等多种任务。这些模型适用于不同行业的广泛应用场景。通过单一 API，开发者可以尝试不同的模型，使用微调和检索增强生成 (RAG) 等技术利用自己的数据对模型进行定制，并安全地将其部署在应用程序中。Amazon Bedrock 的无服务器架构消除了管理基础设施的需求，使开发者能够专注于创新并为用户创造价值。作为 Amazon Bedrock 一部分的 `Converse API`，为开发者提供了一个一致且简化的接口来与这些基础模型交互，从而轻松地将对话式 AI 功能集成到应用程序中，以增强用户体验并实现自然交互。

# 专用基础模型和模型市场

Amazon Bedrock 的一大亮点是其模型市场，该市场提供了广泛的专用基础模型选择，适用于各种用例。专用基础模型针对特定任务或领域进行了定制，为特定应用提供了更准确、更高效的性能。这些模型对于医疗保健、金融和娱乐等行业极具价值，在这些行业中，专业知识和精确度至关重要。模型市场使开发者能够无缝地发现、测试并将这些专用模型集成到其机器学习工作流中。无论是文本生成、图像创建还是复杂的多模态任务，Amazon Bedrock 都提供了构建强大生成式 AI 应用程序所需的工具和灵活性。通过利用 Amazon Bedrock，企业可以保持在 AI 创新的前沿，确保其应用程序既尖端又安全。`Converse API` 通过提供一种与这些模型交互的直接方式，进一步增强了这一能力，使集成过程变得无缝且高效。

# 选择基础模型

选择基础模型时，必须考虑应用程序所需的特定功能。如果您的任务主要涉及文本生成、分析或翻译，`Amazon Titan Text G1 – Premier`、`Amazon Titan Text G1 – Express` 和 `Amazon Titan Text G1 – Lite` 等模型是理想选择。这些模型与 Amazon Bedrock 集成，支持广泛的文本相关任务，包括开放式问答、代码生成、摘要和对话聊天。对于创意应用，`Amazon Nova Canvas` 等模型擅长根据文本描述生成详细图像，非常适合艺术和设计任务。对于多模态功能，`Amazon Nova Lite` 和 `Amazon Nova Pro` 等模型可以同时处理文本和图像输入，提供通用的解决方案。对于简单用例和低预算场景，`Amazon Nova Micro` 是一个纯文本模型，适用于需要低延迟文本处理且无需多模态输入的场景。结合应用程序的具体需求评估这些模型的能力，将有助于您选择最高效的基础模型。

## 区域可用性

选择模型时要考虑的另一个标准是，该模型在您的生成式 AI 应用程序运行区域中的可用性。这可确保最佳性能、符合当地法规并降低延迟，从而提供无缝的用户体验。

考试提示：请注意，某些模型可能在您的区域不可用，但如果您的区域支持`跨区域推理`功能，仍可使用该功能来调用这些模型。跨区域推理使您能够利用不同 AWS 区域的算力，从而无缝管理突发的非计划流量。通过跨区域推理，您可以将流量分发到多个 AWS 区域，在峰值需求期间实现更高的吞吐量和增强的弹性。要使用跨区域推理，您需要创建一个跨区域推理配置文件。要了解更多信息，请访问 `https://docs.aws.amazon.com/bedrock/latest/userguide/inference-profiles-support.html`。

## 定价

最后，就像任何设计良好的架构应用程序一样（生成式 AI 应用程序在这方面也不例外），您需要考虑定价。Amazon Bedrock 定价基于两种主要模式：

*   按需和批处理
*   预置吞吐量

采用按需和批处理模式，您需为处理的输入和输出令牌数量付费，其中 `token`（令牌）是模型将其解释为单个含义单位的字符序列。对于预置吞吐量，您需承诺在一段时间内使用特定水平的吞吐量，对于使用量稳定的应用程序，这可能更具成本效益。有关更多信息，请访问 `https://aws.amazon.com/bedrock/pricing`。

# 使用 Nova Canvas 生成图像

Nova 基础模型最近在 AWS re:Invent 2024 大会上发布。在本用例中，我们将使用 Nova Canvas——一种最先进的图像生成模型——根据文本提示生成图像。本示例将向您展示如何以编程方式实现此用例。

作为一个设计考量，我的 AWS 账户默认区域为 `us-east-2`（俄亥俄州）。由于 Nova Canvas 在我的默认区域不受原生支持（且我不想实现跨区域推理），我将在 `us-east-1`（弗吉尼亚北部）——该模型目前受原生支持的区域——创建我的 Python 客户端。在 AWS 控制台中，我们打开 Amazon Bedrock 并选择 `us-east-1`（弗吉尼亚北部）作为工作区域。然后我们请求访问该模型，如[图 4.2](#c004.xhtml#c04-fig-2)所示。

![图 4.2 请求访问 Nova Canvas。](images/c04f002.png)

[图 4.2](#c004.xhtml#rc04-fig-2) 请求访问 Nova Canvas。

以下 Python 程序使用 `boto3` 模块在 `us-east-1` 中创建 Amazon Bedrock 客户端，并随后与 Nova Canvas 基础模型交互以请求生成图像。我们在 `us-east-1` 的 Amazon SageMaker Studio 中使用 Code Editor 应用程序运行此程序。

要开始使用 Amazon SageMaker Studio，您需要在程序将运行的区域（在本例中为 `us-east-1`）创建一个域。域可用后，您可以打开 Amazon SageMaker Studio，如[图 4.3](#c004.xhtml#c04-fig-3)所示。[图 4.4](#c004.xhtml#c04-fig-4) 展示了 Studio 主页，您可以在其中创建空间。空间是 Amazon SageMaker Studio 用于启动 Code Editor 应用程序的托管实例。在[图 4.4](#c004.xhtml#c04-fig-4)中，我启动了一个名为 `dario-ai-space` 的空间，该空间使用实例类型 `ml.t3.medium` 并具有 5 GB 存储空间。要开发您的 ML 应用程序，您需要创建并启动您的空间，如[图 4.5](#c004.xhtml#c04-fig-5)所示。您的空间附带一个弹性文件系统 (EFS)，您的应用程序代码和其他工件将保存在此处。为避免产生不必要的费用，请确保在编码完成后停止您的空间。

![图 4.3 Amazon SageMaker Studio。](images/c04f003.png)

[图 4.3](#c004.xhtml#rc04-fig-3) Amazon SageMaker Studio。

![图 4.4 Amazon SageMaker Studio 空间。](images/c04f004.png)

[图 4.4](#c004.xhtml#rc04-fig-4) Amazon SageMaker Studio 空间。

![图 4.5 Amazon SageMaker Studio Code Editor。](images/c04f005.png)

[图 4.5](#c004.xhtml#rc04-fig-5) Amazon SageMaker Studio Code Editor。

