
HuBERT 使用 `k-means` 对 `MFCC` 特征 \[[279](#refbib.xhtml#refbib_279)\] 进行聚类，以在原始语音信号中找到非平凡的离散隐藏单元 \[[290](#refbib.xhtml#refbib_290)\]。它称这些 \[*z*[1], …, *z*[*T*]\]，其中 *z*[*t*] ∈ \[*C*] 是 *C* 类别的类别变量。这些 *z*[*t*] 作为 BERT 预训练所需的输出“token”，用于准确预测。

Hsu 等人还尝试在单个 k-means 之外使用聚类模型的集合，随后进行产品量化 \[[99](#refbib.xhtml#refbib_99)\]。

在预训练之后，HuBERT 使用标准的连接式时序分类（CTC）损失，利用标记音频数据微调模型。注意，在微调过程中，CNN 特征编码器保持冻结。

## 6.4 Multimodal And Multitasking Transformer

在证明在许多 NLP 任务中极为有效后，transformers 也展现出在包含多种模态（如图像、文本、视频）的综合任务中的效果。尤其是围绕图像与文本的任务，许多 transformer 架构被提出，将基础 BERT 模型扩展以同时处理视觉输入和语言输入 \[[123](#refbib.xhtml#refbib_123), [173](#refbib.xhtml#refbib_173)\]。本节将介绍几个更通用、被广泛采用的架构。

### 6.4.1 Vision-And-Language Bert (Vilbert)

Vision-and-Language BERT (VilBERT) 是一个用于学习图像和文本任务无关表示的联合模型 \[[173](#refbib.xhtml#refbib_173)\]。图像首先通过物体检测网络转换为一系列映射到特征向量的区域流。文本则遵循常规的 token 流，映射到位置嵌入和词嵌入，形成序列流。如图 \[Fig. 6.1](#ch6.xhtml#fig6_1) 所示，VilBERT 使用标准的变换器块（TRM）以及一种提供两种模态之间稀疏交互的协同变换器块（Co-TRM）。Co‑TRM 与标准变换器块类似，计算查询、键和值矩阵，用于视觉和语言表示在任意中间层。不同之处在于，来自每种模态的键和值会作为输入提供给另一种模态的多头注意力块。因此，Co‑TRM 的多头注意力块会生成对每种模态的注意力聚合特征，并基于另一种模态进行条件，从而实现联合学习。该架构支持多层 TRM 和 Co‑TRM 的堆叠，以进行细化，且高度依赖任务。输出为任务而定，可简单为多层感知器（MLP）后接 soft‑max 层，计算图像与文本相似度的得分；也可对应多个任务，所有任务并行学习。

![Figure 6.1 ViLBERT processing text and image for learning joint representation for multi-modal tasks.](images/fig6_1.jpg)

[Figure 6.1](#ch6.xhtml#b6fig6_1) ViLBERT processing text and image for learning joint representation for multi-modal tasks.

VilBERT 的训练过程类似于 inception 网络的训练。首先，文本和图像分别独立训练。BERT 模型在大规模语料上端到端训练，完成两项任务：掩码语言模型（MLM）和下一句预测（NSP）。基于更快 R-CNN 的预训练对象检测网络从图像中提取边界框及其视觉特征，并将其送入网络。随后，使用 Conceptual Captions 数据集（包含大量图像及其说明）进行联合学习，实现图像区域与文本的对应以及图像中被掩码词的预测。最后，模型在具体的视觉与文本任务上进行训练，如视觉问答（VQA）、视觉常识推理（VCR）、图像检索和区域锚定。研究表明，VilBERT 在这四项任务上均实现最新状态，优于现有专任模型。

### 6.4.2 Unified Transformer (UniT)

在 *Transformer is All You Need: Multimodal Multitask Learning with a Unified Transformer* \[[123](#refbib.xhtml#refbib_123)\] 论文中，Hu 和 Singh 提出 Unified Transformer (UniT)，能够在文本和图像两种模态上共同学习并执行七项任务。

如图 \[Fig. 6.2](#ch6.xhtml#fig6_2) 所示，每种模态都有一个编码器网络，其输出被拼接形成联合表示。拼接后的编码器输出随后进入解码器网络，利用多头跨注意力块对任务特定的输入嵌入进行处理，输出结果到各任务特定的头部，如对象类别检测、视觉问答、情感分类等。

![Figure 6.2 UniT processing text and image for learning joint representation for multi-modal tasks.](images/fig6_2.jpg)

[Figure 6.2](#ch6.xhtml#b6fig6_2) UniT processing text and image for learning joint representation for multi-modal tasks.

在训练视觉-only 与视觉语言特定任务时，图像首先经过卷积神经网络块，再进入变换器编码器，得到隐藏的视觉表示。由于不同视觉相关任务（如对象检测、VQA）可能需要任务特定信息，会在变换器编码器中加入任务嵌入向量。文本编码器使用预训练的 BERT，结合文本嵌入和任务特定嵌入向量，与图像编码器结构相同。解码器是模态无关的，它接收来自不同模态的拼接输入，并将任务特定的查询送入解码器的多头注意力块。训练采用多任务联合方式，每次迭代随机选择一个任务和对应的数据集来构建 batch。UniT 模型在八个数据集上七项任务上表现可比且稳健，与各领域已有的代表性工作相媲美，同时保持参数规模相近。

## 6.5 Video Processing With Timesformer

变换器可以以多种方式应用于视频。本节讨论一种应用方式：视频分类/动作识别。

TimeSformer \[[29](#refbib.xhtml#refbib_29)\] 回答了是否可以使用自注意力而非卷积实现高性能视频分类或动作识别的问题。TimeSformer 采用修改后的注意力机制，并以 Vision Transformer 将二维图像划分为 patch 序列的方式作为起点。

### 6.5.1 Patch Embeddings

TimeSformer 将视频片段分割为一系列图像 patch，类似于在 \[section 6.2](#ch6.xhtml#sec6_2) 中将二维图像划分为 patch 序列。输入是包含 *F* 帧的 RGB 视频，分辨率为 *H* × *W*，可表示为四维矩阵 **X** ∈ ℝ^(*H* × *W* × 3 × *F*)。每个帧（ℝ^(*H* × *W* × 3)）随后被分解为 N 个不相交的大小为 *P* × *P* 的 patch，其中 *N* = *H* W / *P*²。每个 patch 被转换为长度为 3*P*² 的向量 **x**[(*p*, *t*)] ∈ ℝ^(3*P*²)，其中 *p* = 1,…, *N* 为 patch 索引，*t* = 1,…, *F* 为时间/帧索引。

下一步是为每个 patch 生成嵌入向量 **z**[(*p*, *t*)]^((0)) ∈ ℝ^(*D*)，其中 *D* 为 Transformer 的隐藏尺寸：

``` 
z_(p,t)^(0) = x_(p,t)E + e_(p,t)^pos,
``` 
(6.7)
