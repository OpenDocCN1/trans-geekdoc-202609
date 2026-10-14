
给定一个分辨率为 *H* × *W*、 *C* 通道的图像，图像可以用 **x** ∈ ℝ<sup>(*H* × *W* × *C*)</sup> 表示。ViT 首先将二维图像划分为 *N* 个图像补片，**x**[*p*] ∈ ℝ<sup>(*N* × (*P*² ⋅ *C*)</sup>，补片分辨率为 *P* × *P*，其中 *N* = *H* **W** /*P*²。图像补片序列类似于标准 transformer 中的 token 序列 \[[254](#refbib.xhtml#refbib_254)\]。

在将补片序列送入嵌入层之前，会在每个补片向量前预置一个可学习的嵌入，类似于 BERT 中的 \[*CLS*] token，即 **x**[*cls*]。因此 **x**[*p*] → [**x**[*cls*];**x**[*p*]]。利用嵌入层 **E** ∈ ℝ<sup>((*P*² ⋅ *C*) × *D*)</sup>，以及一维位置编码 **E**[*pos*] ∈ ℝ<sup>((*N* + 1) × *D*)</sup>，我们得到 Transformer 的输入。 *D* 为 Transformer 的隐藏维度。

$$\begin{array}{l} \mathbf{z}\_{0} = [\mathbf{x}\_{cls}; \mathbf{x}\_{p}^{(1)}\mathbf{E}; \cdots; \mathbf{x}\_{p}^{(N)}\mathbf{E}] + \mathbf{E}\_{pos} \end{array}$$  

(6.3)

在此之后，\\(\\mathbf{z}[0]\\) 进入一个基本的 transformer 编码器结构，包含 *L* 个编码层：

$$\begin{array}{ll} \mathbf{z}^{\\prime}\_{l} & = \\text{MultiHeadAttn}(\\text{LayerNorm}(\\mathbf{z}\_{l-1}) + \\mathbf{z}\_{l-1}) \\\\ \mathbf{z}\_{l} & = \\text{FeedFwd}(\\text{LayerNorm}(\\mathbf{z}\_{l}) + \\mathbf{z}^{\\prime}\_{l}) \end{array}$$  

(6.4)  

(6.5)

$$\\begin{array}{ll} \\mathbf{y} & = \\text{LayerNorm}(\\mathbf{z}\_{L}^{0}), \\\\ \\end{array}$$  

(6.6)

其中 *l* = 1,…, *L*，\\(\\mathbf{z}[L]^{0}\\) 是最终编码层的分类嵌入。Feed‑forward 层包含两个全连接层，随后使用 GELU 激活函数。

ViT 与标准 transformer 的一个区别在于，ViT 在残差连接之前对前一层的输出应用 LayerNorm；而在标准 transformer \[[254](#refbib.xhtml#refbib_254)\\) 中，残差连接是在 LayerNorm 之前进行。

通过一系列实验，\[[78](#refbib.xhtml#refbib_78)\\) 表明，卷积神经网络（CNN）引入的先验偏置对小数据集有用，但对大数据集则不然。随着数据规模增大，模型能够自行学习相关关联，这一点在各种 Transformer 中均已得到验证。ViT 还表明，补片之间的空间关系（距离）是通过位置编码学习的。相邻的补片会得到相似的位置编码；二维空间相关性同样由位置编码学习，即同一行或同一列的补片具有相似的位置编码。实验还表明，将图像补片的二维结构硬编码到位置编码中并不会提升质量。这可能是因为在结构多变的 transformer 中加入先验偏置限制了模型自行学习何为重要、何为不重要的能力。

最后，Vision Transformer 探索了一种对自注意力机制的修改——轴向注意力 \[[114](#refbib.xhtml#refbib_114), [126](#refbib.xhtml#refbib_126)\\)。轴向注意力是指注意力在同一行或同一列的补片之间进行。ViT 实际上创建了轴向 transformer 块，先进行行注意力，再进行列注意力。

### 6.3 自动语音识别

自动语音识别（ASR）是指系统自动将语音音频信号转换为文本，这一挑战在计算机视觉和 NLP 任务中并不存在。音频信号是连续值的序列，而不是像图像或文本那样的离散值。这意味着不能像在计算机视觉或 NLP 中那样进行预训练。例如，在 NLP 中，输入信号本身定义了离散的词或子词单元；在计算机视觉中，输入信号包含像素等子单元。音频信号中没有天然的子单元。这使得预训练变得困难，无论是掩码还是不掩码。本节介绍了三种 transformer 在 ASR 中的应用方式。

#### 6.3.1 Wav2vec 2.0

wav2vec 2.0 的第一步 \[[16](#refbib.xhtml#refbib_16)\\) 使用卷积特征编码器（即 CNN）将输入的语音音频 **X** 转换为一系列表示 (**z**[1], …, **z**[*T*])。序列长度 *T* 表示音频的时间步数。随后，音频表示的某些时间段会被掩码。

这些编码能够被学习，因为语音被分解为类似于 WordPiece 子词的离散 speech units。这些 speech units 是有限的离散单元集合，长度短于音素（约 25 ms）。隐含的 speech 编码类似于文本 transformer 初始嵌入层学习的嵌入。这些被掩码的编码随后送入 transformer，以构建上下文化的表示。对比损失函数 \[[219](#refbib.xhtml#refbib_219), [250](#refbib.xhtml#refbib_250)\\) 使 wav2vec 2.0 transformer 能够学习各个 speech units 的相对重要性。

注意，离散 speech units 使得跨语言训练成为可能，模型能够学习哪些单元仅用于特定语言、哪些单元在多种语言之间共享。

**训练过程** 正如本书前面所述，transformer 可以在大语料上进行预训练，学习自然语言的各种特征，然后在特定任务上微调。wav2vec 2.0 的做法类似，只是它结合了非监督和自监督预训练，只需要少量标记数据进行微调。

#### 6.3.2 Speech2Text2

Speech2Text2 \[[258](#refbib.xhtml#refbib_258)\\) 是另一种利用 transformer 非监督预训练进行 ASR 的强大应用，它在 wav2vec 2.0 编码器之上加入了一个解码块。预训练完成后，模型使用 CTC 损失进行微调。解码块仅在微调阶段训练，不在预训练阶段。

由于 Speech2Text2 使用解码块，它还可以结合机器翻译与 ASR，即音频为英语，转录为法语。Wang 等人还对 Speech2Text 进行了微调，实现了若干语言对的最新状态。

#### 6.3.3 HuBERT: Hidden Units BERT

为了解决缺乏预定义 speech units 的问题，Hsu 等人提出了 HuBERT（Hidden Units BERT） \[[120](#refbib.xhtml#refbib_120)\\)。HuBERT 通过聚类生成噪声的 speech 子单元，这些子单元随后被视作可以像子词一样进行 BERT 预训练。

HuBERT 将噪声标签作为序列输入，并对其进行掩码，以进行 BERT 预训练。正如 BERT 学习未掩码文本以正确预测掩码 token，HuBERT 学习未掩码、噪声 speech 子单元以正确预测掩码 speech unit。

在 HuBERT 中，原始语音信号先通过 CNN 编码器得到编码信号 *X* = [*x*[1], …, *x*[*T*]]，长度为 *T*，与 wav2vec 2.0 类似。随后，对编码信号 *X* 中的某些索引进行掩码。掩码后的序列作为 BERT‑like transformer 的输入。HuBERT 也与 wav2vec 2.0 采用相同的掩码方式。