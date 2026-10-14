
We can see that “positive” attends to “nice” in three heads of the encoder attention. These are shown in Fig. 5.16. In five heads of the cross-attention mechanism, “positive” and “nice” both attend to “person”. These are shown in Fig. 5.17.

![Figure 5.16 Encoder attention heads from layers 3 (head 5), 4 (head 11), and 6 (head 11), from left to right.](img/fig5_16.jpg)

Figure 5.16 Encoder attention heads from layers 3 (head 5), 4 (head 11), and 6 (head 11), from left to right.

![Figure 5.17 Cross-attention heads from layers 8, 9, and 10. The top row shows heads 1, 2, and 11 of layer 8 (left to right). The bottom row shows head 0 of layer 9 and head 1 of layer 10.](img/fig5_17.jpg)

Figure 5.17 Cross-attention heads from layers 8, 9, and 10. The top row shows heads 1, 2, and 11 of layer 8 (left to right). The bottom row shows head 0 of layer 9 and head 1 of layer 10.

#### 5.5.3.2 Analysis

While there are 11 attention heads (out of 432) that show strong attention between “positive” and attention, there are even more that do not. Many of the other attention heads in the span extraction model fall into the type of attention patterns shown in [57], particularly the broad attention where each token attends to nearly every other token and the type where each token attends to the following token.

The analysis above calls into question the ability to use attention weights themselves to explain predictions. And recently, [143] found the attention weight analysis shown above to be a poor method for analyzing an attention mechanism. There are several papers that suggest other analysis methods. We'll describe one of them below.

**Attention mechanism output norm** Analyzing an attention mechanism using the norm of the components of its output was suggested by [143]. Recall (5.29), which shows how self-attention is defined in the standard transformer, for a single attention head. As shown in (2.19), after the attention heads are concatenated, we apply a linear layer to obtain the output of the attention mechanism. The linear layer has weights **W**[*O*], giving the mechanism the following output:

$$\\begin{array}{ll} \\mathbf{y}\_{i} & {= \\left( {{\\sum\\limits\_{j = 1}^{L}A\_{ij}}\\mathbf{v}(\\mathbf{x}\_{j})} \\right)\\mathbf{W}\_{O}} \\\\ \\end{array}$$  

(5.76)

$$\\begin{array}{ll} \\ & {= {\\sum\\limits\_{j = 1}^{L}A\_{ij}}\\mathbf{f}(\\mathbf{x}\_{j})} \\\\ \\end{array}$$  

(5.77)

where *A*[*i**j*] are the attention weights from (5.27), **v**(**x**[*j*]) is a value vector from 5.25, and *f*(**x**[*j*]) = **v**(**x**[*j*])**W**[*O*]. *f*(**x**[*j*]) is the output of the attention mechanism corresponding to the *j*^(*t**h*) input token **x**[*j*].

In [143], Kobayashi et al. specifically suggest using ||*A*[*i**j**]*f*(**x**[*j*])|| as it's the degree to which token *i* attends to token *j*. They also show that ||*f*(**x**[*j*])|| and *A*[*i**j*] are meaningful quantities and sometimes play opposing roles in determining model behavior.

# CHAPTER 6 Pre-trained and Application-Specific Transformers

DOI: [10.1201/9781003170082-6](https://doi.org/10.1201/9781003170082-6)

THE transformer architecture was introduced as a language model that transformed text in one language into text in another language [254]. Since that initial application to machine translation, the transformer architecture has been applied to computer vision, audio processing, and video processing, as well as other problems in NLP. The transformer architecture has been shown to be a somewhat reliable way of taking in an input sequence and converting it into something else.

## 6.1 Text Processing

This section describes some of the ways that transformers have been applied to domain-specific text processing and a recent advancement made in text sequence to text sequence processing.

### 6.1.1 Domain-Specific Transformers

Transformers have been made for domain-specific applications by fine-tuning pre-trained models like `BERT`. We'll look at a few.

#### 6.1.1.1 BioBERT

`BioBERT` [152] is domain-specific language model constructed by fine-tuning `BERT` on a large collection of biomedical text. `BioBERT` was created because `ELMo` and `BERT` did not perform well on biomedical text because their training data did not include it. `BioBERT` outperformed previous models on three NLP tasks useful for biomedical text mining: named entity recognition (NER), relationship extraction, and question answering (QA).

There are three steps to go from a pre-trained `BERT` model to a `BioBERT` model. The starting point is a pre-trained `BERT` model. The next step is to pre-train the model on PubMed abstracts and PubMed Central full-text articles. Finally, after the pre-training is over, `BioBERT` is further fine-tuned on the NER, relationship extraction, and question answering tasks, using task-specific datasets.

`BioBERT` used the cased `BERT` vocabulary, unchanged. Had they not done this, they would not have been able to start with a pre-trained `BERT` model. `BioBERT` was trained in 23 days, on eight NVIDIA Volta V100 GPUs.

#### 6.1.1.2 SciBERT

`SciBERT` [24] is a language model built to process scientific text. It uses the `BERT` architecture, but was trained on the full text and abstracts of 1.4 million papers from the Semantic Scholar website ([semanticscholar.org](http://semanticscholar.org)).

- 与 `BERT` 相比，`SciBERT` 使用 `WordPiece` 词元化方式，词表大小为 30,000 个词，但它不使用 `BERT` 的词表。相反，`SciBERT` 的词表是基于 Semantic Scholar 语料库构建的。`SciBERT` 在五个自然语言处理任务上进行了评估：命名实体识别（NER）、临床试验 PICO 提取、文本分类、关系提取和依存分析。PICO 提取是一种序列标记任务，用于临床试验论文，模型会提取提及试验参与者、干预措施、对比组或结果的跨度。训练过程在单台 8 核 TPU 上耗时一周。

#### 6.1.1.3 FinBERT

- 利用 `ULMFit` 模型 [119]，Howard 和 Ruder 表明，在目标域语料上对已预训练语言模型进行微调可以提升分类指标。`FinBERT` [7] 是验证该思想是否同样适用于 `BERT`、甚至取得更好效果的结果。`FinBERT` 通过以下两种方式实现：(1) 在大规模金融语料上进一步预训练；(2) 仅在金融情感分析语料的句子上进行预训练。预训练时，`FinBERT` 使用经过过滤金融关键词的 Reuters TRC2 数据子集。该语料包含超过 2900 万词，涵盖 46,143 篇文档。情感分析则使用 Financial Phrasebank 数据集，包含来自 LexisNexis 的 4845 条句子。

### 6.1.2 Text-to-Text Transformers

- 如在第 5.3 节 [205] 讨论，Raffel 等人提出的 `T5` 模型将标准 NLP 任务重新框架为文本到文本的转换，输入和输出均为字符串。`T5` 问世后出现了两项重要进展：一种是支持 101 种语言的多语言版本 `mT5` [281]，另一种是直接在 `UTF-8` 字节上运行的无 token 变体 `ByT5` [280]。本节讨论 `ByT5`。

#### 6.1.2.1 ByT5

- `ByT5` [280] 是基于字节的模型，利用字符串以 `UTF-8` 字节序列的形式存储。其动机之一是字节级（token-free）模型对未登录词、拼写错误、大小写和形态变化更具鲁棒性。字节级模型不依赖固定词表将测试数据映射到 token，只需要 256 个嵌入向量，而使用固定词表时则需要更大量的嵌入向量。词表规模的大幅下降使得模型的其余参数可以用于其他位置。

- 由于字节序列比 token 序列更长，而 transformer 的计算复杂度（除线性注意力外）随序列长度的平方增长，早期工作尝试通过各种方式降低字节级和字符级序列带来的计算开销。`ByT5` 以 `mT5` 架构为起点，但在以下几点上与 `mT5` 有所不同：(1) rid of `SentencePiece` tokenization；(2) 直接使用原始 `UTF-8` 字节作为输入，并为每个字节学习嵌入；(3) 在词表中加入三个特殊 token：`padding`、`EOS`（结束）和未知（`UNK`）；(4) 调整预训练任务，使得被掩码的输入跨度长度大于 `T5` 中的长度；(5) 移除 encoder 与 decoder 层数相同的限制，encoder 层数为 decoder 的三倍；(6) 在输出时剔除非法 `UTF-8` 字节。

- 如前所述，使用字节而非 token 的鲁棒性是假设的主要好处之一。为验证这一假设，作者在数据上加入了六种噪声类型并观察对性能的影响：

  1. 以 10% 的概率删除每个字符。
  2. 以 10% 的概率对每个字符进行添加、删除或修改（三者等概率）。
  3. 以 20% 的概率将字符复制 1-3 次。
  4. 对每个字符大写并用空格填充。
  5. 将每个字符转为大写（仅在语言使用大小写的情况下）。
  6. 对每个字符随机设置大小写（仅在语言使用大小写的情况下）。

- 噪声可以以两种方式注入：在微调和评估数据中，或仅在评估数据中。对于问答任务，噪声仅加在上下文中，不影响问题或答案；对于句子蕴涵训练任务，噪声加在前提和假设上。无论哪种噪声类型，论文均表明 `ByT5` 在噪声抵抗方面优于 `mT5`。

### 6.1.3 Text Generation

- 变换器语言模型最著名的成功之一是文本生成，`GPT-2` 与 `GPT-3` 是典型代表，它们由多层 transformer-decoder 堆叠而成。

#### 6.1.3.1 GPT: Generative pre-training

- 生成式预训练模型属于语言模型范畴，首先在无监督数据上进行通用训练，随后在特定任务上进行微调。`GPT` 这一家族的首个模型，即同名的 `GPT` [202]，先在大量未标记文本上训练一堆 transformer decoder 层，随后在有标签的任务数据上微调。`GPT` 是自回归模型，意味着它利用序列前面的输入来预测后面的值。`GPT` 在四类自然语言理解任务上进行了评估：自然语言推理、问答、语义相似度和文本分类。

**Unsupervised pre-training**

在该阶段，`GPT` 从标记为 *U* = (*w*[1], …, *w*[*n*]) 的语料库开始，逐句学习预测下一个 token，给定前面的上下文。形式上，模型学习在给定前 *k* 个 token 的条件下预测 token *w*[*t*] 的概率

$$P(w_t \mid w_{t-1}, \ldots, w_{t-k})$$

并通过最小化负对数似然

$$L_1(U) = -\sum_t \log P(w_t \mid w_{t-1}, \ldots, w_{t-k}; \Theta)$$

(6.1)

其中 Θ 为模型参数。优化采用随机梯度下降。

**Supervised fine-tuning**

在微调阶段，模型在标记数据集 *C* 上进行训练，每个样本为 token 序列 **x** = (*x*[1], …, *x*[*m*]) 与类别标签 *y*。预训练的解码器被用作特征生成器，随后在其上附加一个全连接线性层（`softmax` 激活）并训练最小化第二个负对数似然
