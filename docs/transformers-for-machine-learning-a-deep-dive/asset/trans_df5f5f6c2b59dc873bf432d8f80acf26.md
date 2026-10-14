
INFOXLM是基于XLM-R模型参数初始化，然后使用结合mMLM、TLM和XLCO任务的相互信息最大化任务进行预训练；单语言序列互信息（MMLM）、跨语言序列互信息（TLM）和跨语言序列级互信息（XLCO）。

### 4.1.2.7 Aligned Multilingual Bidirectional EncodeR (AMBER)

Aligned Multilingual Bidirectional EncodeR (AMBER) \[[121](#refbib.xhtml#refbib_121)\] 是一种利用平行数据（具有词级和句级对齐预训练任务，即跨语言词对齐（CLWA）和跨语言句子对齐（CLSA）任务）来创建跨语言表示的技术。

**跨语言词对齐（CLWA）** 类似于CLWR，CLWA \[[121](#refbib.xhtml#refbib_121)\] 也旨在利用平行语料库学习不同语言之间的词对齐。CLWA 使用两种不同的注意力面具作为输入到变换器模型。训练完成后，在顶层变换器层中得到两个注意力矩阵，即源到目标注意力 *A*[*x* → *y*] 和目标到源注意力 *A*[*y* → *x*]。由于 *A*[*x* → *y*] 衡量源到目标转换的对齐，反之亦然，因此希望在 *A*[*x* → *y*] 或 *A*[*y* → *x*] 注意力矩阵中对词的对齐相似。为此，训练过程中鼓励最小化 *A*[*x* → *y*] 与 *A*[*y* → *x*] 之间的距离。

**跨语言句子对齐（CLSA）** CLSA \[[121](#refbib.xhtml#refbib_121)\] 旨在通过平行数据强制跨语言句子表示对齐。设 ℳ 和 𝒫 分别为单语言数据和平行数据，对于每个平行句子对 (*x*, *y*)，分别为 *x* 和 *y* 生成独立的句子嵌入，即 *c*[*x*] 和 *c*[*y*]。 *c*[*x*] 与 *c*[*y*] 通过编码器最后一层的嵌入求平均得到。对齐通过以下损失函数实现，该函数利用输入句子 *x* 的正确翻译 *y* 进行预测：

$$\\begin{array}{l} {\\mathcal{L}\_{CLSA}^{(x,y)} = - \\log\\frac{e^{\\mathbf{c}\_{x}^{T}\\mathbf{c}\_{y}}}{\\sum\\limits\_{y^{\\prime} \\in \\mathcal{M} \\cup \\mathcal{P}}e^{\\mathbf{c}\_{x}^{T}\\mathbf{c}\_{y^{\\prime}}}}} \\\\ \\end{array}$$  

(4.9)

其中 *y*^′ 在 ℒ[*C**L**S**A*]^((*x*, *y*)) 中可以是任意句子，且不受语言限制。

AMBER 采用 MLM、TLM、CLWA、CLSA 任务的组合进行训练，并在 XTREME 基准上评估，表现优于 XLM-R 和 Unicoder。

### 4.1.2.8 ERNIE-M

许多技术表明，利用平行语料和单语言语料可以获得更好的跨语言表示。然而，平行语料始终比单语言数据规模有限，除非收集大量平行语料，否则进展受限。ERNIE-M \[[194](#refbib.xhtml#refbib_194)\] 使用大规模单语言语料和有限的平行语料来生成跨语言表示。为增强表示，ERNIE-M 通过单语言语料生成伪平行句子，并将其与平行数据一起用于提升跨语言表示的对齐。ERNIE-M 提出了两个预训练任务：跨注意力掩码语言模型（CAMLM）和回译掩码语言模型（BTMLM）。

**跨注意力掩码语言模型（CAMLM）** CAMLM \[[194](#refbib.xhtml#refbib_194)\] 是一种与 TLM 密切相关的平行语料预训练任务。如前所述，对于给定的平行句子对 (*x*, *y*)，被掩盖的 token 在 *x* 中可以访问并可能关注 *x* 的上下文以及 *y* 的上下文，同理，被掩盖的 token 在 *y* 中也如此。然而，CAMLM 限制了 TLM，仅保留对应平行句子的上下文。因此，被掩盖的 token 在 *x* 只能利用 *y* 的上下文进行预测，反之亦然。禁止同句上下文的关注迫使算法学习对应语言的表示；否则，算法可能更倾向于使用同句上下文进行预测。使用与 TLM 相同的设置，令 (*x*, *y*) 的掩盖位置集合分别为 *M*[*x*] 与 *M*[*y*]，则 *x*[ ∖ *M*[*x*] ] 与 *y*[ ∖ *M*[*y*] ] 表示掩码后的 *x* 与 *y*。CAMLM 的损失函数定义为：

$$\\begin{array}{l} {\\mathcal{L}\_{CAMLM}^{(x,y)} = - \\frac{1}{|M\_{x}|}{\\sum\\limits\_{i \\in M\_{x}}}l}ogP(x\_{i}|y\_{\\smallsetminus M\_{y}}) - \\frac{1}{|M\_{y}|}{\\sum\\limits\_{i \\in M\_{y}}}l}ogP(y\_{i}|x\_{\\smallsetminus M\_{x}})} \\\\ \\end{array}$$  

(4.10)

图 4.4 说明了 CAMLM 的跨语言注意。如图所示，token *h*2 只关注句子 *y* 的 token，而 *h*5 与 *h*6 仅关注句子 *x* 的 token。

![Figure 4.4 Cross-attention Masked LM (CAMLM) where a masked token can only attend to the opposite sentences for prediction \[194\].](images/fig4_4.jpg)

[Figure 4.4](#ch4.xhtml#b4fig4_4) Cross-attention Masked LM (CAMLM) where a masked token can only attend to the opposite sentences for prediction \[[194](#refbib.xhtml#refbib_194)\].

**回译掩码语言模型（BTMLM）** BTMLM \[[194](#refbib.xhtml#refbib_194)\] 利用回译 \[[222](#refbib.xhtml#refbib_222)\] 来缓解平行语料不足的问题，从而学习跨语言表示。它包含两个步骤：第一步从给定的单语言语料生成伪平行数据；第二步对原单语言句子的 token 进行掩码，并将其与生成的伪平行句子拼接。模型最后预测被掩盖的 token。[Fig. 4.5](#ch4.xhtml#fig4_5) 展示了 BTMLM 的两个步骤。

![Figure 4.5 Illustration of BTMLM \[194\] pre-training task. The first step on the left is where a pre-trained CAMLM is used to generate pseudo-parallel sentences. The second step on the right is where the generated pseudo-parallel sentences are then used to further train the CAMLM.](images/fig4_5.jpg)

[Figure 4.5](#ch4.xhtml#b4fig4_5) Illustration of BTMLM \[[194](#refbib.xhtml#refbib_194)\] pre-training task. The first step on the left is where a pre-trained CAMLM is used to generate pseudo-parallel sentences. The second step on the right is where the generated pseudo-parallel sentences are then used to further train the CAMLM.

由于在 XLM 架构中 mMLM 和 TLM 预训练任务表现优异，ERNIE-M 在训练时同样采用这两项任务。ERNIE-M 使用 96 种语言的单语言和平行语料进行训练，并初始化为 XLM-R 权重。ERNIE-M 在多个下游任务（包括命名实体识别、跨语言问答、跨语言句子相似度判别和跨语言句子检索）上展现出最先进的性能。

### 4.1.2.9 Hierarchical Contrastive Learning (HICTL)

Hierarchical Contrastive Learning (HICTL) \[[266](#refbib.xhtml#refbib_266)\] 是另一种跨语言预训练任务，使用基于 InfoNCE 的损失函数。虽然 XLCO 是基于句子的，HICTL 同时提供句子级和词级跨语言表示。

