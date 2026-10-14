
本章涵盖了多语言 Transformer 架构的最新发展。多语言 Transformer 架构完全由以下几项定义：

`* 模型架构（层和组件）`

`* 预训练任务`

`* 预训练数据`

`* 微调任务和基准`

本章首先介绍不同的多语言 Transformer 架构用于自然语言理解（NLU）和自然语言生成（NLG）。[第 4.2 节](#ch4.xhtml#sec4_2) 接着描述多语言数据的最新状态，包括用于下游 NLP 任务的无标签预训练数据和微调基准。[第 4.3 节](#ch4.xhtml#sec4_3) 提供对多语言 Transformer 模型内部工作机制的一些见解。最后，[第 4.4 节](#ch4.xhtml#sec4_4) 提供一个零射多语言情感分类的实践案例研究。

## 4.1 多语言 Transformer 架构

本节讨论多语言 Transformer 的不同结构设计。我们将多语言 Transformer 划分为 (i) 自然语言理解（NLU）架构和 (ii) 自然语言生成（NLG）架构。[表 4.1](#ch4.xhtml#tbl4_1)\[[74](#refbib.xhtml#refbib_74)\] 提供了本书出版时可用的具有影响力的多语言 Transformer 模型的摘要。

[TABLE 4.1](#ch4.xhtml#b4tbl4_1) 多语言语言模型摘要 \[[74](#refbib.xhtml#refbib_74)\]

| **模型** || 架构 || 预训练 || # 语言 || Ref. |

| --- | --- | --- | --- | --- |

| **# 参数** || **目标函数** || **单语** || **平行** ||  ||  |

| IndicBERT || 33M || MLM || IndicCorp || ✗ || 12 || \[[137](#refbib.xhtml#refbib_137)\] |

| --- | --- | --- | --- | --- | --- | --- |

| mBERT || 172M || MLM || [Wikipedia](http://Wikipedia) || ✗ || 104 || \[[72](#refbib.xhtml#refbib_72)\] |

| Amber || 172M || MLM, TLM, CLWA, CLSA || [Wikipedia](http://Wikipedia) || ✓ || 104 || \[[121](#refbib.xhtml#refbib_121)\] |

| MuRIL || 236M || MLM, TLM || CommonCrawl + [Wikipedia](http://Wikipedia) || ✓ || 17 || \[[141](#refbib.xhtml#refbib_141)\] |

| VECO-small || 247M || MLM, CS-MLM || CommonCrawl || ✓ || 50 || \[[175](#refbib.xhtml#refbib_175)\] |

| Unicoder || 250M || MLM, TLM, CLWR, CLPC, CLMLM || [Wikipedia](http://Wikipedia) || ✓ || 15 || \[[125](#refbib.xhtml#refbib_125)\] |

| XLM-15 || 250M || MLM, TLM || [Wikipedia](http://Wikipedia) || ✓ || 15 || \[[63](#refbib.xhtml#refbib_63)\] |

| InfoXLM-base || 270M || MLM, TLM, XLCO || CommonCrawl || ✓ || 94 || \[[48](#refbib.xhtml#refbib_48)\] |

| XLM-R-base || 270M || MLM || CommonCrawl || ✗ || 100 || \[[61](#refbib.xhtml#refbib_61)\] |

| HiCTL-base || 270M || MLM, TLM, HICTL || CommonCrawl || ✓ || 100 || \[[266](#refbib.xhtml#refbib_266)\] |

| Ernie-M-base || 270M || MLM, TLM, CAMLM, BTMLM || CommonCrawl || ✓ || 100 || \[[194](#refbib.xhtml#refbib_194)\] |

| HiCTL-Large || 559M || MLM, TLM, HICTL || CommonCrawl || ✓ || 100 || \[[266](#refbib.xhtml#refbib_266)\] |

| Ernie-M-Large || 559M || MLM, TLM, CAMLM, BTMLM || CommonCrawl || ✓ || 100 || \[[194](#refbib.xhtml#refbib_194)\] |

| InfoXLM-Large || 559M || MLM, TLM, XLCO || CommonCrawl || ✓ || 94 || \[[48](#refbib.xhtml#refbib_48)\] |

| XLM-R-Large || 559M || MLM || CommonCrawl || ✗ || 100 || \[[61](#refbib.xhtml#refbib_61)\] |

| RemBERT || 559M || MLM || CommonCrawl + [Wikipedia](http://Wikipedia) || ✗ || 110 || \[[54](#refbib.xhtml#refbib_54)\] |

| X-STILTS || 559M || MLM || CommonCrawl || ✗ || 100 || \[[198](#refbib.xhtml#refbib_198)\] |

| XLM-17 || 570M || MLM, TLM || [Wikipedia](http://Wikipedia) || ✓ || 17 || \[[63](#refbib.xhtml#refbib_63)\] |

| XLM-100 || 570M || MLM, TLM || [Wikipedia](http://Wikipedia) || ✗ || 100 || \[[63](#refbib.xhtml#refbib_63)\] |

| VECO-Large || 662M || MLM, CS-MLM || CommonCrawl || ✓ || 50 || \[[175](#refbib.xhtml#refbib_175)\] |

### 4.1.1 基础多语言 Transformer

多语言 Transformer 模型通常基于 mBERT 架构 \[[72](#refbib.xhtml#refbib_72)\]。本节描述多语言 Transformer 架构的基本组件。

**输入层** 输入是一系列 token，它们来自有限词汇表的一对一热表示，通常是子词库。该词汇表一般通过拼接多个语言的单语言数据，使用诸如 BPE \[[223](#refbib.xhtml#refbib_223)\]、WordPiece \[[273](#refbib.xhtml#refbib_273)\] 或 SentencePiece \[[144](#refbib.xhtml#refbib_144)\] 等算法学习。为确保不同语言和脚本在词汇表中得到良好表示，可采用指数加权抽样，或为语言簇学习独立的词汇表，从而分割词汇表大小 \[[55](#refbib.xhtml#refbib_55)\]。

**Transformer 层** 多语言语言模型（mLM）通常构成 Transformer 的编码器。它由 *N* 层组成，每层包含 *k* 个注意力头，随后是前馈神经网络。注意力头通过对输入序列中所有其他 token 的表示，使用加权线性组合计算每个 token 的嵌入。将所有注意力头的嵌入拼接后，再经过前馈网络，得到每个输入词的 *d* 维嵌入。

**输出层** 通常，最终 Transformer 层的输出被用作每个 token 的上下文表示，而 \[CLS\] token 对应的嵌入被视为整个输入文本的嵌入。也可以通过对 token 嵌入进行池化来生成文本嵌入。输出层包含一次线性变换，随后是 Softmax，它以前一层的 token 嵌入为输入，并产生词汇表中 token 的概率分布。

