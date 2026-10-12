
# 12.7 解码器模型示例：GPT3

本节将对 GPT3 进行高层描述，它是解码器模型的一个示例。其基本架构与编码器模型极其相似，由一系列作用于学习到的词嵌入的 Transformer 组成。然而，其目标截然不同。编码器旨在构建文本的表示，以便微调来解决各种更具体的 NLP 任务。相反，解码器只有一个目的：生成序列中的下一个 token。通过将扩展后的序列反馈回模型，它可以生成连贯的文本段落。

## 12.7.1 语言建模

GPT3 构建了一个自回归语言模型。通过一个具体的例子最容易理解这一点。请考虑句子 "It takes great courage to let yourself appear weak." 为简单起见，假设 token 为完整的单词。整个句子的概率为：

![c12-fig-5014.jpg](images/c12-fig-5014.jpg)

(12.14)

更正式地说，自回归模型将观测到的 `N` 个 token 的联合概率 `Pr(t[1], t[2], …, t[N])` 分解为一个自回归序列：

![c12-fig-5015.jpg](images/c12-fig-5015.jpg)

(12.15)

自回归公式揭示了损失函数中最大化 token 对数概率与下一个 token 预测任务之间的联系。

## 12.7.2 掩码自注意力

为了训练解码器，我们在自回归模型下最大化输入文本的对数概率。理想情况下，我们会输入整个句子，并同时计算所有的对数概率和梯度。然而，这会带来一个问题；如果我们输入完整的句子，计算 log `Pr(great|It takes)` 这一项时，将同时获得答案 `great` 和右侧上下文 `courage to let yourself appear weak`。因此，系统可以“作弊”而不是学习预测后续单词，导致无法正常训练。

幸运的是，token 在 Transformer 网络中仅在自注意力层进行交互。因此，可以通过确保对答案和右侧上下文的注意力为零来解决该问题。这可以通过在自注意力计算（公式 12.5）中将对应的点积在传入 `softmax[•]` 函数之前设置为负无穷大来实现。这被称为*掩码自注意力*。其效果是使[图 12.1](#c012.xhtml#c12-fig-0001)中所有向上倾斜箭头的权重归零。

整个解码器网络的运作如下。输入文本被分词，并将 token 转换为嵌入。嵌入被传入 Transformer 网络，但现在 Transformer 使用掩码自注意力，因此它们只能关注当前和之前的 token。每个输出嵌入可以被视为代表一个部分句子，对于每一个嵌入，目标都是预测序列中的下一个 token。因此，在 Transformer 之后，一个线性层将每个词嵌入映射到词汇表大小，随后通过 `softmax[•]` 函数将这些值转换为概率。在训练期间，我们旨在使用标准的多类交叉熵损失，最大化每个位置上真实序列中下一个 token 的对数概率之和（[图 12.12](#c012.xhtml#c12-fig-0012)）。

![Figure 12.12 Training GPT3-type decoder network. The tokens are mapped to word embeddings with a special <start> token at the beginning of the sequence. The embeddings are passed through a series of transformers that use masked self-attention. Here, each position in the sentence can only attend to its own embedding and the embeddings of tokens earlier in the sequence (orange connections). The goal at each position is to maximize the probability of the following ground truth token in the sequence. In other words, at position one, we want to maximize the probability of the token It; at position two, we want to maximize the probability of the token takes; and so on. Masked self-attention ensures the system cannot cheat by looking at subsequent inputs. The autoregressive task has the advantage of making efficient use of the data since every word contributes a term to the loss function. However, it only exploits the left context of each word.](images/c12-fig-0012.jpg)

[图 12.12](#c012.xhtml#c12-fig-0012a) 训练 GPT3 类型的解码器网络。Token 被映射为词嵌入，并在序列开头添加一个特殊的 `<start>` token。嵌入通过一系列使用掩码自注意力的 Transformer。在此，句子中的每个位置只能关注其自身的嵌入以及序列中较早 token 的嵌入（橙色连线）。每个位置的目标都是最大化序列中下一个真实 token 的概率。换句话说，在位置一，我们希望最大化 token `It` 的概率；在位置二，我们希望最大化 token `takes` 的概率；以此类推。掩码自注意力确保系统无法通过查看后续输入来“作弊”。自回归任务的优势在于高效利用数据，因为每个词都为损失函数贡献了一项。然而，它仅利用了每个词的左侧上下文。

## 12.7.3 从解码器生成文本
