
### 4.1.3.1 Language-agnostic BERT Sentence Embedding (LaBSE)

Language-agnostic BERT Sentence Embedding (`LaBSE`) \[88\] 是一种用于训练跨语言句子表示的架构，结合了 XLM 中的 Masked Language Model (`MLM`) 和 Translation Language Model (`TLM`) 预训练任务，并通过双向双编码器的 additive margin softmax loss 进行翻译排序任务 \[146, 283\]。如 `Fig. 4.6` 所示，双编码器由两个配对的 `mBERT` 编码器组成，两个编码器的 `[CLS]` token 句子表示分别输入到评分函数中。`Fig. 4.6` 为 `LaBSE` 架构提供了示意图。

![Figure 4.6 Illustration of Language-agnostic BERT Sentence Embedding (LaBSE) architecture \[88\].](images/fig4_6.jpg)

Figure 4.6 Illustration of Language-agnostic BERT Sentence Embedding (LaBSE) architecture \[88\].

**Bidirectional Dual Encoder with Additive Margin Softmax** 双编码器架构 \[283\] 在排序任务（如 `LaBSE` 用于跨语言嵌入的翻译检索）中表现出色。形式上，对于平行句子对 (*x*[*i*], *y*[*i*])，翻译检索是一个排名问题，目标是将 *y*[*i*]（ *x*[*i*] 的真实翻译）在所有可能的翻译 𝒴 中排在更高的位置。

$$\begin{array}{l} {P({y_{i}\mid x_{i}}) = \frac{e^{\phi({x_{i},y_{i}})}}{\sum\limits_{\overline{y} \in \mathcal{Y}}e^{\phi({x_{i},\overline{y}})}} } \\ \end{array}$$

(4.11)

其中 *ϕ* 是 *x*[*i*] 与 *y*[*i*] 表示之间相似度的评分函数。

在训练时，P(*y*[*i*] ∣ *x*[*i*]) 通过从同一批次的翻译对中采样负样本 *y*[*n*] 来近似：

$$\begin{array}{l} {P_{\text{approx~}}({y_{i}\mid x_{i}}) = \frac{e^{\phi({x_{i},y_{i}})}}{e^{\phi({x_{i},y_{i}})} + {\sum\limits_{n = 1,n \neq i}^{N}e^{\phi({x_{i},y_{n}})}}}} \\ \end{array}$$

(4.12)

因此，对于源句 *x*[*i*] 与目标句 *y*[*i*] 的平行对，模型可通过以下对数似然目标进行优化 \[283\]：

$$\begin{array}{l} {\mathcal{L}_{s} = - \frac{1}{N}{\sum\limits_{i = 1}^{N}\frac{e^{\phi({x_{i},y_{i}})}}{e^{\phi({x_{i},y_{i}})} + {\sum\limits_{n = 1,n \neq i}^{N}e^{\phi({x_{i},y_{n}})}}}} \\ \end{array}$$

(4.13)

该损失 ℒ[*s*] 旨在识别正确的 *y*[*i*]，因此使用 ℒ[*s*] 会导致 *x*[*i*] 与 *y*[*i*] 表示之间的不对称关系。为解决这一问题，Yand 等人 \[283\] 引入了双向学习目标 ${\overline{\mathcal{L}}}_{s}$，显式优化平行对 (*x*[*i*], *y*[*i*]) 的正向和逆向排序：

$$\begin{matrix} {{\mathcal{L}^{\prime}}_{s} = - \frac{1}{N}{\sum\limits_{i = 1}^{N}\frac{e\phi(yi,xi)}{e\phi(yi,xi) + \sum_{n = 1,n \neq i}^{N}e^{\phi}(yi.x_{n})}}} \\ {{\overline{\mathcal{L}}}_{\mathcal{S}} = \mathcal{L}_{\mathcal{S}} + {\mathcal{L}^{\prime}}_{\mathcal{S}}} \\ \end{matrix}$$

(4.14)

为了进一步区分正确的翻译和最接近但非翻译的句子，评分函数 *ϕ* 通过 additive margin softmax 扩展，在正样本 (*x*[*i*], *y*[*i*]) 周围加入 margin *m*：

$$\phi^{\prime}(x_{i},y_{j}) = \begin{cases} {\phi(x_{i},y_{j}) - m} & {~if~i = j} \\ {\phi(x_{i},y_{j})} & {~if~i \neq j} \\ \end{cases}$$

(4.15)

将 *ϕ*^′(*x*[*i*], *y*[*j*]) 代入双向损失 ${\overline{\mathcal{L}}}_{s}$，得到 additive margin 双向损失：

$$\begin{array}{ll} {\mathcal{L}_{ams} = - \frac{1}{N}} & {\sum\limits_{i = 1}^{N}\frac{e^{\phi({x_{i},y_{i}}) - m}}{e^{\phi({x_{i},y_{i}}) - m} + {\sum\limits_{n = 1,n \neq i}^{N}e^{\phi({x_{i},y_{n}})}}}} \\ & {{\overline{\mathcal{L}}}_{ams} = \mathcal{L}_{ams} + \mathcal{L}_{ams}^{\prime}} \\ \end{array}$$

(4.16)

如前所述，`LaBSE` 使用单语言和平行语料库分别对 `mBERT` 编码器进行 Masked Language Model (`MLM`) 和 Translation Language Model (`TLM`) 预训练。`LaBSE` 采用三阶段渐进堆叠的方式训练变换器编码器：对于 *L* 层编码器，先训练 *fracL*4 层，再训练 *fracL*2 层，最后训练全部 *L* 层。后续训练步骤中，前一阶段模型的参数会复制到后一阶段。

### 4.1.3.2 Multilingual Universal Sentence Encoders (mUSE)

Multilingual Universal Sentence Encoders (`mUSE`) \[49, 284\] 提出了一种通过结合单语言句子表示的多任务学习与用于平行文检索的双编码器的方法，实现跨语言句子嵌入。通过将两种方法结合，`mUSE` 将在单语言任务上学到的强性能转移到其他语言的零样本学习中。基本上，对于某一语言对（源语言、目标语言），模型使用多任务架构学习以下三类任务：(i) 源语言单语言任务， (ii) 目标语言单语言任务， (iii) 源语言到目标语言的翻译任务，作为桥梁任务，以鼓励所有已训练任务之间的跨语言表示对齐。`Fig. 4.7` 展示了用于 QA、NLI 以及桥接翻译任务的架构示意图。

![Figure 4.7 Illustration of mUSE architecture for QA, NLI and the bridging translation tasks \[284\].](images/fig4_7.jpg)

Figure 4.7 Illustration of mUSE architecture for QA, NLI and the bridging translation tasks \[284\].

`mUSE` 使用双编码器对可以表示为输入‑响应句子对的任务进行多任务学习。某些任务（如 QA、翻译）自然符合该框架，而其他任务（如 NLI）则需要特殊的 reformulation。输入‑响应排序可形式化为：对于输入‑响应对 (*s*[*i*]^(*I*), *s*[*i*]^(*R*))，目标是使 *s*[*i*]^(*R*) 高于所有可能的响应 *s*[*j*]^(*R*) ∈ 𝒮^(*R*)。换句话说，条件概率 *P*(*s*[*i*]^(*R*) ∣ *s*[*i*]^(*I*)) 应该被定义为：

$$\begin{array}{ll} {P({s_{i}^{R}\mid s_{i}^{I}})} & {= \frac{e^{\phi({s_{i}^{I},s_{i}^{R}})}}{\sum\limits_{s_{j}^{R} \in \mathcal{S}^{R}}e^{\phi({s_{i}^{R},s_{j}^{R}})}} } \\ {\phi({s_{i}^{I},s_{j}^{R}})} & {= g^{I}{(s_{i}^{I})}^{\top}g^{R}(s_{j}^{R})} \\ \end{array}$$

(4.17)

where `g`^(`I`) is the input sentence encoding function and `g`^(`R`) is response sentence encoding function, `g`^(`I`) and `g`^(`R`) make up the dual-encoder. Both `g`^(`I`) and `g`^(`R`) are implemented using transformers and are trained with the log-likelihood loss function, $\overset{\sim}{P}(s_{i}^{R} \mid s_{i}^{I})$, for each task.

As illustrated in Fig. 4.7, `mUSE` uses a single shared encoder supporting multiple downstream tasks. The training tasks include: QA prediction task, NLI task, and translation ranking. Task-specific layers for the QA and NLI tasks are added after the shared encoder to help accommodating representational needs for each task.

### 4.1.4 Multilingual Natural Language Generation (Multilingual NLG)

All cross-lingual pre-training tasks discussed in the previous section are used for Natural Language Understanding (NLU) tasks only. This section discusses a few of the pre-training tasks used by generative multilingual models such as `MASS` \[231\], `BART` \[155\], `mBART` \[169\], and `XNLG` \[46\].

**Sequence-to-Sequence LM (Seq2SeqLM)** As discussed earlier, Masked Language Model (`MLM`) is handled as a token-level classification problem over the masked tokens, in which the original words are predicted by feeding the masked token vectors to a Softmax layer over the vocabulary. `MLM` also is used to pre-train encoder-only transformer architectures which are then used for NLU tasks. `Seq2SeqLM` extends conventional `MLM` to pre-train encoder-decoder transformer models such as `T5`\[205\], `mT5` \[281\], and `MASS` \[231\]. While the context of `MLM` includes all tokens in the input sequence, the context of `Seq2SeqLM` includes all tokens in the input masked sequence and the left side tokens in the predicted target sequence. With the encoder's masked sequence as input, the decoder predicts the masked words sequentially from left to right. This allows transformer architectures pre-trained with `Seq2SeqLM` to be used for NLG tasks. For a given input sequence of tokens *x*, let *x̂* be the masked version of *x*, that is *x* with masked n-gram span. With *l*[*s*] defined as the length of masked n-gram span, then `Seq2SeqLM` loss is defined as

$$\begin{array}{l} {\mathcal{L}_{Seq2SeqLM}^{(x)} = - \frac{1}{l_{s}}{\sum\limits_{s = i}^{j}l}ogP(x_{s}|\hat{x},x_{i:s - 1})} \\ \end{array}$$

(4.18)

**Denoising Auto-Encoder (DAE)** Similar to `Seq2SeqLM`, `DAE` \[155, 169\] is a pre-training task for encoder-decoder transformer architectures. While `Seq2SeqLM` is based on predicting masked tokens, `DAE` does not mask textual elements but rather corrupts them and then reconstructs the original values. `DAE` corrupts text at the token level by token deletion and token masking, at the sentence level by sentence permutation, at a text span level by text infilling, or at the document level by document rotation. `DAE` is more sample efficient than `Seq2SeqLM` since it provides more signals for model training. `DAE` generates more training signal since it reconstructs the complete original text, while `Seq2SeqLM` reconstructs just the masked tokens. `BART` \[155\] encodes corrupted input sequences using a bidirectional encoder and reconstructs the original text using a left-to-right decoder. Similar to `Seq2SeqLM` definition, for a given input text *x* , let *x̂* be the corrupted version of *x*, then `DAE` loss is defined as

$$\begin{array}{l} {\mathcal{L}_{DAE}^{(x)} = - \frac{1}{|x|}{\sum\limits_{i = 1}^{|x|}l}ogP(x_{i}|\hat{x},x_{< i})} \\ \end{array}$$

(4.19)
