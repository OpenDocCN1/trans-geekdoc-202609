

| T5 || `T5` (**Text-to-Text Transfer Transformer**) 由 Google 开发。它是一个编码器-解码器 Transformer 模型，在非监督和监督数据的多任务混合上进行训练。`T5` 将所有语言任务转换为统一的文本到文本格式，从而简化了模型训练和推理。与 BERT 等前辈相比，它使用了缩减版的 Transformer 架构。`T5` 有不同的大小，最大可达 11 B。它在 **Colossal Clean Crawled Corpus** (**C4**) 数据集上进行训练，该数据集包含来自网络的数百 GB 文本。它允许通过使用标准文本到文本格式对下游任务进行微调来实现迁移学习。 || 语言 || Google |

| Stable Diffusion || Stable Diffusion 是由 Stability AI 开发的开源文本到图像生成模型。它基于带有潜在扩散采样的卷积自编码器。Stable Diffusion 可以根据文本描述和提示生成逼真的图像和艺术作品。该模型在 LAION-5B 上进行训练，这是一个来自互联网的大规模图像文本对数据集。 || 图像 || Stability AI |

| Falcon || Falcon 是一个具有 400 亿参数的 LLM，在一万亿个标记上进行训练。预训练数据是从网络的公开爬取中收集的。为了扩展 Falcon 的能力，该数据集随后通过一些精选来源（例如研究论文和社交媒体上的对话）进行了扩展。 || 语言 || TII |

| Llama 2 7B || Llama 2 是由 Meta 开发的 LLM。Llama 2 使用 Transformer 架构在公开可用的在线数据源上进行预训练。它有从 7B 到 70B 参数的不同大小。它是一个开源模型，可用于商业用途。 || 语言 || Meta |

| GPT-J 6B || GPT-J 是一个具有 60 亿参数的基于 Transformer 的模型。它是一个用于 NLP 任务的自回归解码器专用模型。 || 语言 || EleutherAI |

| Segment Anything Model (SAM) || 一个可以从任何图像中剪切对象的模型。 || 计算机视觉 || Meta |

Table 15.1: 示例预训练 FM

预训练过程允许模型学习语言的表示，并在其参数中编码世界知识。由于该模型专门用于根据输入文本预测下一个标记，其主要功能在于以高概率完成句子。因此，它已经能够完成某些任务，例如完成句子和回答一些问题。以下是使用具有 7B 参数的 Llama 2 模型的输入和输出示例：

```
Input: 
"The capital of France is"
Output: 
Paris.
The capital of Germany is Berlin.
The capital of Italy is Rome.
The capital of Japan is Tokyo.
…
```

如您所见，虽然模型提供了正确答案 Paris，但它也生成了额外的未请求文本。那么，问题是，我们如何使预训练模型以更高的精度执行任务？我们将在 *Instruction fine-tuning* 部分尝试回答这个问题。

由于预训练非常大的 FM 所涉及的高成本以及对专业工程和科学专业知识的需求，只有有限数量的组织拥有进行基础模型预训练的资源。因此，许多组织选择采用适应和定制方法，使模型与其要求保持一致。

## 适应和定制

虽然预训练的大型 FM 已经具备满足多样化要求的许多功能，但它们主要使用通用数据集进行训练，可能不了解利基领域（例如医学和法律）的知识，或者可能不知道如何执行特定任务。此外，您可能拥有需要模型了解的专有数据和工作流程。在这些情况下，您需要通过融入领域或专有专业知识或提高其在特定任务中的有效性来改进模型。为了实现这一点，有四个主要选项可用：

*   Domain adaptation training

*   Fine-tuning

*   Reinforcement learning with human feedback

*   Prompt engineering

让我们更详细地探讨每个替代方案。

### Domain adaptation pre-training

预训练语言模型在广泛的通用语言数据上进行训练，它们只拥有通用知识，因此在金融或医学等利基领域中可能表现不佳。例如，这些模型可能不理解高度技术性或深奥领域中的利基词汇、行话或命名实体。教导模型在新领域中学习新知识的技术称为 Domain adaptation pre-trained。以下示例显示了 GPT-J 6B 模型在域适应前和使用 SEC 10K 文件进行域适应后的结果：

```
Input:
"What drives sales growth at Amazon?"
Output before domain adaptation:
"Amazon is the world's largest online retailer. It is also the world's largest online marketplace. It is also the world'"
Output after domain adaptation:
"Sales growth at Amazon is driven primarily by increased customer usage, including increased selection, lower prices, and increased convenience, and increased sales by other sellers on our websites."
```

显然，域适应使模型更熟悉金融术语，并能够给出更具上下文和连贯性的响应。

域适应的过程与预训练非常相似，也遵循使用未标记数据集的 *self-supervised learning* 方法。以下是 LLM 域适应微调过程包含的一般阶段：

1.  **Data collection for target domain**: 获取准确代表目标领域的相关文本数据。

2.  **Data preprocessing**: 清理、去重、对收集的数据进行分词、标准化特殊字符以及隐去隐私信息。这与预训练过程类似。

3.  **Base pre-trained model selection**: 选择合适的预训练模型架构作为基础。

4.  **Model initialization**: 使用预训练检查点初始化模型的权重。

5.  **Domain-specific training**: 使用领域特定数据训练模型预定的 epoch 数量，并评估训练性能。

6.  **In-domain testing**: 在来自同一领域的测试数据集上评估训练好的模型。

7.  **Iterative optimization**: 重复训练过程以逐步提高模型性能。

Self-supervised learning 是一种 ML 范式，模型学习从输入数据生成自己的标签，从而能够在不依赖外部提供的标记数据集的情况下学习有意义的表示和特征。

有许多域适应预训练模型的示例。例如，FinBERT 是 BERT 针对金融领域进行域适应的结果，LEGAL-BERT 是一系列用于法律领域的 BERT 模型，旨在协助法律 NLP 研究、计算法律和法律技术应用。一些较新的域适应模型包括 Google 的 Med-PaLM 2，用于医学 NLP 任务。

虽然域适应可以增强模型对新目标领域的理解，但可能会导致在更广泛的通用领域中性能下降。为了解决其中一些限制，已调查了数据重要性采样和多阶段域适应等策略，以减轻此类缺点。对这些技术的深入探讨超出了本书的范围。

### Fine-tuning

Llama 2、GPT 和 Falcon 等 FM 在多样化数据集上进行训练，以获取通用表示，而不是针对特定任务进行专门化。Fine-tuning 是将这些 FM 适应特定数据集和任务中存在的特定细微差别和模式的过程。

