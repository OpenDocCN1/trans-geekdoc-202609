
# THE advent of Bidirectional Encoder Representations from Transformer (BERT) \[[72](#refbib.xhtml#refbib_72)\] is considered the onset of a revolution in the field of Natural Language Processing (NLP). BERT uses unlabeled text to pre-train deep bidirectional contextual representations. This resulted in rich pre-trained language models that can be fine-tuned with a simple additional output layer and a reasonably sized labeled dataset to produce state-of-the-art performance in a broad range of NLP tasks. These developments lowered the barrier of entry for the wide adoption of these powerful pre-trained models. It is now common practice in the artificial intelligence field to share pre-trained models and fine-tune them with minimal cost as opposed to the old paradigm of designing task-specific architectures. In this chapter, we cover BERT's basic design concepts, developments, and applications.

## 3.1 bert

### 3.1.1 Architecture

**Core layers** One of the major contributions of BERT is the simplicity of design and the diversity of covered downstream tasks. BERT's architecture consists of multi-layers of the bidirectional transformer encoder \[[253](#refbib.xhtml#refbib_253)\]. The capacity of the BERT architecture is characterized by (i) the number of transformer layers *L*, (ii) the size of hidden representations *H*, and the number of bidirectional self-attention heads *A*.

**Input and Output Representations** Given the simplicity of the BERT's core architecture, just a stack of bidirectional transformer encoders, the ingenuity of BERT lies in the design of input and output representations that can be used to train many downstream NLP tasks with the same architecture. To that end, BERT's input is designed to distinctly represent NLP downstream tasks involving a single or a pair of sentences using the same input representation design. Most major NLP downstream tasks can be covered using a single sentence (e.g., text classification, sequence tagging, summarization, etc.) or paired sentences (e.g., question answering, natural language inference, etc.).

For any input sequence, BERT prefixes a special \[CLS\] token. The hidden vector of this token in the last BERT layer will be used as an aggregate representation for the entire input sequence and usually used for classification tasks. For NLP tasks with paired sentences, BERT concatenates the sentences into one sequence with a separator token \[SEP\] in between, which serves as one way BERT uses to distinguish the two sentences. BERT also uses a learned segment embedding to indicate to which sentence a token belongs. BERT employs WordPiece \[[272](#refbib.xhtml#refbib_272)\] to tokenize and embed input sequences. Finally, BERT uses position embedding layer to encode the order of tokens within the input. The input to BERT is the sum of the aforementioned token embedding, segment embedding, and positional embedding for each token as illustrated in [Fig. 3.1](#ch3.xhtml#fig3_1).

![Figure 3.1 BERT input configuration \[71\].](images/fig3_1.jpg)

[Figure 3.1](#ch3.xhtml#b3fig3_1) BERT input configuration \[[71](#refbib.xhtml#refbib_71)\].

### 3.1.2 Pre-Training

**Masked Language Model (MLM)** The idea is to randomly mask-out a percentage of the input sequence tokens, replacing them with the special \[MASK\] token. During pre-training, the modified input sequence is run through BERT and the output representations of the masked tokens are then fed into a softmax layer over the WordPiece vocabulary as practiced in standard language models pre-training. The bidirectional attention of the transformer encoder forces the \[MASK\] prediction task to use the context provided by the other non-masked tokens in the sequence. BERT is pre-trained with a 15% mask-out rate. This simple MLM task has a downside where a mismatch is created between pre-training and fine-tuning tasks as the special \[MASK\] token does not appear during fine-tuning. To overcome this issue, every token in the 15% masked-out tokens is subjected to the following heuristic:

*   With a probability of 80%, the token is replaced with the special \[MASK\] token.

*   With a probability of 10%, the token is replaced with a random token.

*   With a probability of 10%, the token is left unchanged.

The occasional insertion of random tokens (i.e., noise) pushes BERT to be less biased towards the masked token, especially when the masked token is left unchanged, in its bidirectional context attention. The MLM task uses cross-entropy loss only over the masked tokens and ignores the prediction of all non-masked ones.

**Next Sentence Prediction (NSP)** Many downstream NLP tasks require understanding the relationship between two sentences, such as Question Answering (QA) and Natural Language Inference (NLI). Standard language models do not pick up this type of knowledge. This motivates the NSP task, where BERT is fed pairs of sentences and pre-trained to predict if the second sentence should follow the first one in a continuous context. As discussed earlier, the first sentence is prefixed with the \[CLS\] token, then the two sentences are delimited by the special token \[SEP\]. During NSP task pre-training, the model is given sentence pairs where 50% of the time the second sentence comes after the first sentence and the other 50% the second sentence is a random sentence from the full training corpus. The self-attention of Transformer layers encourages the BERT representation of \[CLS\] token to encode both input sentences. Therefore, NSP pre-training is performed by adding a single layer MLP with softmax atop the \[CLS\] token representation to predict the binary NSP label. BERT pre-training involves combined training with both MLM and NSP tasks by optimizing the model parameters over their combined loss function. [Fig. 3.2](#ch3.xhtml#fig3_2) illustrates BERT's pre-training tasks.

![Figure 3.2 BERT pre-training architecture \[71\].](images/fig3_2.jpg)

[Figure 3.2](#ch3.xhtml#b3fig3_2) BERT pre-training architecture \[[71](#refbib.xhtml#refbib_71)\].

### 3.1.3 Fine-Tuning

With BERT simple and yet versatile design, fine-tuning a pre-trained model for many downstream tasks is a straightforward task that involves simply plugging in the proper inputs and outputs and fine-tuning all the model's parameters end-to-end. As discussed earlier many NLP tasks can be modeled using two sentences input to BERT. For tasks like Question Answering (QA) and Natural Language Inference (NLI), the input to BERT is a concatenated question-answer sentence pair and the hypothesis-premise sentence pair, respectively. Other tasks with single input sentence, such as text classification and sequence tagging (e.g., POS, NER), the input to BERT is modeled again as concatenated sentences but with one of them empty. For token level tasks (e.g., QA, POS, and NER), BERT output tokens representations are fed into an output layer for token tagging. [Fig. 3.3](#ch3.xhtml#fig3_3) provides an illustration for the BERT fine-tuning for token level tasks. For tasks like text classification and NLI, the output representation of the special token \[CLS\] is used as input to an output layer to produce a label. [Figs. 3.4](#ch3.xhtml#fig3_4) and [3.5](#ch3.xhtml#fig3_5) depict BERT fine-tuning architectures for single sequence and paired-sequences classification tasks.

![Figure 3.3 BERT fine-tuning architecture for token tagging tasks (e.g., POS, NER, and QA) \[71\].](images/fig3_3.jpg)

[Figure 3.3](#ch3.xhtml#b3fig3_3) BERT fine-tuning architecture for token tagging tasks (e.g., POS, NER, and QA) \[[71](#refbib.xhtml#refbib_71)\].

![Figure 3.4 BERT fine-tuning architecture for single sequence classification tasks \[71\].](images/fig3_4.jpg)

[Figure 3.4](#ch3.xhtml#b3fig3_4) BERT fine-tuning architecture for single sequence classification tasks \[[71](#refbib.xhtml#refbib_71)\].
