
This chapter covers the state-of-the-art developments in multilingual transformer architectures. A multilingual transformer architecture is fully defined using:

`* Model Architecture (layers and components)`

`* Pre-training Tasks`

`* Pre-training Data`

`* Fine-tuning Tasks and Benchmarks`

The chapter starts with different multilingual transformer architecture for Natural Language Understanding (NLU) and Natural Language Generation (NLG). [Section 4.2](#ch4.xhtml#sec4_2) proceeds by describing the state-of-the-art in multilingual data, this includes unlabeled pre-training data and fine-tuning benchmarks for downstream NLP tasks. [Section 4.3](#ch4.xhtml#sec4_3) provides some insights into the inner workings of multilingual transformer models. Finally, [Section 4.4](#ch4.xhtml#sec4_4) provides a practical case study on zero-shot multilingual sentiment classification.

## 4.1 Multilingual Transformer Architectures

This section discusses the different architectural designs for multilingual Transformers. We divide multilingual transformers into (i) Natural Language Understanding (NLU) architectures and (ii) Natural Language Generation (NLG) architectures. [Table 4.1](#ch4.xhtml#tbl4_1)\[[74](#refbib.xhtml#refbib_74)\] provides a summary of the impactful multilingual transformer models available at the time of publishing this book.

 [TABLE 4.1](#ch4.xhtml#b4tbl4_1) Summary of multilingual language models \[[74](#refbib.xhtml#refbib_74)\] 

| **Model** || Architecture || pre-training || #Langs. || Ref. |

| --- | --- | --- | --- | --- |

| **# Parmas.** || **Objective Function** || **Mono.** || **Parallel** ||  ||  |

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

### 4.1.1 Basic Multilingual Transformer

Multilingual transformer models are typically based on the mBERT architecture \[[72](#refbib.xhtml#refbib_72)\]. In this section, we describe the basic components of a multilingual transformer architecture.

**Input Layer** A series of tokens is provided as input to the multilingual transformer. The token input is derived from a one-shot representation of a limited vocabulary, often a subword vocabulary. Typically, this vocabulary is learned by concatenating monolingual data from several languages using algorithms such as BPE \[[223](#refbib.xhtml#refbib_223)\], WordPiece \[[273](#refbib.xhtml#refbib_273)\], or SentencePiece \[[144](#refbib.xhtml#refbib_144)\]. To guarantee that diverse languages and scripts are well represented in the vocabulary, data may be sampled using exponential weighted smoothing or distinct vocabularies for clusters of languages can be learned \[[55](#refbib.xhtml#refbib_55)\] by dividing the vocabulary size.

**Transformer Layers** Typically a multilingual Language Model (mLM) makes up the encoder of a multilingual transformer. It consists of a stack of *N* layers, each of which has *k* attention heads followed by a feed-forward neural network. An attention head computes an embedding for each token in the input sequence by combining the representations of all other tokens in the sentence using an attention weighted linear combination. Concatenating the embeddings from all the attention heads and passing them through a feed-forward network generates a *d*‑dimensional embedding for each input word.

**Output Layer** Typically, the outputs of the final transformer layer are utilized as contextual representations for each token, while the embedding associated with the \[CLS\] token is considered to be the embedding of the entire input text. Alternatively, the text embedding may be generated by pooling the token embeddings together. The output layer has a basic linear transformation followed by a Softmax that accepts a token embedding from the previous transformer layer as an input and produces a probability distribution over the vocabulary's tokens.
