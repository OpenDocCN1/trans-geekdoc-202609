

Transformers 已成为 NLP 中的主导模型，是 BERT、生成式预训练 Transformer（GPT）、T5 等模型的基础，展示了其在翻译之外的多种任务（包括文本生成、摘要和问答）中的多功能性和有效性。

要在 PyTorch 中使用预训练 Transformer 模型进行语言翻译，我们可以利用 `transformers` 库，该库提供了多种预训练模型。在此示例中，让我们使用 Helsinki-NLP 或 `opus-mt-en-fr` 模型，该模型专门用于从英语翻译成法语。

1. 安装所需库：首先，确保已安装 PyTorch 和 `transformers` 库。如果未安装，可以使用以下 pip 进行安装：

```
pip install torch transformers
```

2. 加载预训练模型和分词器：以下是加载模型及其对应分词器的方法：

```
from transformers import MarianMTModel, MarianTokenizer

def load_model_and_tokenizer(model_name):
    tokenizer = MarianTokenizer.from_pretrained(model_name)
    model = MarianMTModel.from_pretrained(model_name)
    return tokenizer, model

model_name = 'Helsinki-NLP/opus-mt-en-fr'
tokenizer, model = load_model_and_tokenizer(model_name)
```

3. 翻译文本：定义一个函数，以英文文本作为输入并返回法语翻译：

```
def translate(text, tokenizer, model):
    # Tokenize the input text and convert to tensor
    input_ids = tokenizer.encode(text, return_tensors="pt")

    # Generate translation using model
    translated = model.generate(input_ids)

    # Decode the output tokens
    translated_text = tokenizer.decode(translated[0], skip_special_tokens=True)
    return translated_text

# Example usage
english_text = "Good morning! How are you?"
french_translation = translate(english_text, tokenizer, model)
print(f"English: {english_text}\nFrench: {french_translation}")
```

4. 代码说明：以下是代码描述：

a. 加载模型和分词器：`load_model_and_tokenizer` 函数根据模型标识符 `model_name` 加载分词器和模型。该标识符指定了模型的架构及其所接受的特定训练。

5. 翻译函数：神经网络中的翻译函数通常遵循结构化过程，将输入文本从一种语言转换为另一种语言，利用 Transformer 等高级模型架构。以下是该函数的逐步分解：

a. 分词：文本首先使用 `tokenizer.encode` 进行分词，将输入文本转换为模型所期望的 token ID 序列。`return_tensors="pt"` 参数确保输出为 PyTorch 张量。

b. 模型预测：`model.generate` 接收分词后的文本并运行模型，以预测翻译文本的输出 token ID。

c. 解码：`tokenizer.decode` 将预测的 token ID 转换回可读文本。`skip_special_tokens=True` 参数会移除训练期间使用但输出中不需要的 token（如 EOS）。

## [结论](#toc.xhtml#zh92)

在本章中，我们讨论了 TA、分类和语言翻译的复杂过程，强调了它们在各个领域中的关键作用。我们探讨了文本预处理、分词和特征提取等基础技术，这些技术对于将原始文本转换为可供分析的结构化数据至关重要。本章还涵盖了高级 ML 和深度学习模型，包括二分类和多类分类、主题建模、情感分析以及注意力机制的使用。通过实现 seq2seq 模型并利用 Transformer，我们展示了如何有效地实现语言翻译。本章中提供的实际示例和案例研究强调了这些技术的现实适用性。随着你继续探索这些方法，你将能够将 TA 和语言翻译模型应用于解决从 NLP 到多语言沟通等各个领域的复杂问题。

在下一章中，我们将学习如何使用文本数据进行摘要、情感分析和问答。

**加入本书的 Discord 空间**

加入本书的 Discord 工作区，获取最新动态、优惠、全球科技动态、新书发布以及与作者的交流会议：

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/Discord.png)

# 第 9 章

## 文本摘要与情感分析

### 简介

文本摘要、情感分析和问答（QA）是自然语言处理（NLP）的关键技术，能够从海量文本中提取有意义的信息。

文本摘要旨在将冗长的文档浓缩为简洁的摘要，同时保留最重要的信息。它可以通过提取式方法实现，即选取关键句子；也可以通过抽象式方法实现，即生成捕捉文本精髓的新摘要。

情感分析侧重于确定文本的情感基调，识别表达的情感是积极、消极还是中性。该技术广泛应用于社交媒体监控和客户反馈分析等场景，用于衡量公众舆论并改善用户体验。

问答是根据给定的上下文或数据集自动提供准确答案的过程。它涉及理解上下文、理解问题，并检索或生成最相关的答案，通常使用 BERT（基于 Transformer 的双向编码器表示）和 Transformer 等高级模型。

### 结构

本章将涵盖以下内容：

• 文本分析简介

• 文本摘要

• 情感分析

• 问答模型

### 目标

本章结束时，我们将探索高级文本分析技术，包括使用 PyTorch 进行文本摘要、情感分析和问答。本章旨在深入理解提取式和抽象式摘要方法，指导读者使用神经网络构建情感分类器，并演示基于 Transformer 的问答模型实现。此外，本章还将介绍使用 BERT 和 GPT 等预训练语言模型针对特定任务进行微调，并提供实际示例和案例研究来说明这些技术的现实应用。总体目标是使读者掌握在各个领域有效分析和解释文本数据所需的知识和技能。

### 文本分析简介

在当今数据驱动的世界中，理解并从文本数据中提取洞察的能力在各个领域都至关重要。文本分析是理解人类沟通、情感和信息的核心。从社交媒体帖子到科学文章，文本数据无处不在。

本章将探讨 PyTorch（一种多功能的深度学习库）如何使我们能够从文本内容中提取有价值的洞察。文本分析使我们能够从非结构化文本中得出有意义的信息，无论是情感分析、摘要还是问答。

本章将涵盖以下场景，演示如何使用 PyTorch 从文本内容中提取有价值的洞察：

• 情感分析：这是评估和确定各种形式文本（如客户反馈、评论或推文）中表达情感的过程。它涉及使用 NLP 和机器学习（ML）技术来识别文本的情感，无论是积极、消极还是中性。

