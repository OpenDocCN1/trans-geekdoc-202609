
contrast, when a translator plays an important role in creating and ensuring the quality of the training data for a model, e.g., the NMT task involves training and testing data for MT, it is primarily an intelligent tool. In other words, the final criterion to decide whether a task is intelligent or not for a translator must be considered on a case-by-case basis. If the translator uses a tool to conduct a NLP task without updating the system with data, it is a facilitation task. In contrast, if there is a two-way relationship between the translator and the NLP model, i.e., the translator performs the NLP task while also training the system, it is an intelligent task.

## 6.2.2 Purposes of neural network models in translation

In machine learning, a translator’s primary task is not model development, but rather manipulating language data as input and output of the model. Nevertheless, knowledge of some basic neural network models and their functioning in a continuous translation process can help the translator better understand relevant NLP tasks as well as the role that the translator does have in model development. Language data produced by the translator can be used to address two general NLP challenges: sequence classification and sequence prediction. Strictly speaking, in machine learning, classification is essentially a predictive modeling problem. But instead of producing another sequence, as is the case in a seq2seq model, in a classification task, a class label is predicted for a given string of input data.

Both prediction and classification are fundamentally sequential problems. As Jurafsky and Martin (2020) state, "Language is an inherently temporal phenomenon" and "this temporal nature is reflected in the algorithms we use to process language" (p. 181). In machine learning, an artificial neural network (ANN) such as Transformer and recurrent neural network (RNN) are able to capture the temporal aspects of language as a powerful sequence learning architecture.

### 6.2.2.1 Sequence prediction

As discussed in Section 4.3.4 of Chapter 4, a Neural MT system is essentially a sequence transduction model with an encoder-decoder structure. In this approach, similar to other sequence transduction models, embeddings are learned from training data so as to convert the input and output tokens to vectors of dimension.

As discussed in Sections 4.3.4.2 and 4.3.4.3 in Chapter 4, RNN-based language models process sequences one word at a time, which may lead to a loss of relevant information and to difficulties in training when passing information forward through an extended series of recurrent connections. Moreover, the inherently sequential nature of recurrent networks inhibits the use of parallel computational resources, preventing them from being trained with large amounts of data (Jurafsky & Martin, 2020, p. 190; Vaswani et al., 2017).

To address this challenge, Vaswani et al. (2017) proposed the Transformer, "a model architecture eschewing recurrences and instead relying entirely on an attention mechanism to draw global dependencies between input and output" (p. 2), which allows the use of parallel computations and a higher training efficiency.

For a sequence prediction task, usually the language data directly created by humans – through human translation, spelling check, and transcription – can be used to train the machine, although additional processing might be needed, such as data cleaning, segmentation, and source-target text alignment. In machine translation, human translation is used to generate parallel corpora to train an NMT engine.

### 6.2.2.2 Sequence classification

The encoder-decoder artificial neural networks such as RNNs can also be used to classify entire sequences rather than the tokens within them. Examples include domain detection, quality estimation, and sentiment analysis. In these applications, sequences of text are classified as belonging to one of a small number of categories.

Classifying documents into different topic categories can be a useful pre-processing step in translation. For example, to apply RNNs in this setting, the text to be classified is passed through the RNN word-by-word, generating a new hidden layer each time. The hidden layer for the final element of the text is taken to constitute a compressed representation of the entire sequence. In the simplest approach to classification, the hidden layer for the final element of the text serves as the input to a subsequent feedforward network, in which the computation proceeds iteratively from one layer of units to the next as discussed in Chapter 3, that chooses a class via a softmax¹ over the possible classes.

Xing et al. (2010) summarize three large categories of sequence classification methods:

- 1. Feature-based classification, which transforms a sequence into a feature vector and then applies conventional classification methods.
- 2. Sequence distance-based classification, which measures the similarity between sequences to determine the quality of the classification.
- 3. Model-based classification, which uses a hidden Markov model (HMM) and other statistical models to classify sequences.

(p. 3)

Classification tasks need category labels, which usually start with human annotation, i.e., human judgments as to the category. However, some unlabeled data share common features with labeled data and also contain additional features that may provide a more comprehensive description of a class. By incorporating unlabeled data, a more accurate classifier may be built under certain circumstances (Xing et al., 2010, p. 5). In this type of NLP task, a translator usually needs to annotate the language data, which means that there is a secondary layer of data interaction on top of the corpora directly generated in a translation process.

## 6.3 Purposes of NLP tasks at each step of a continuous translation process

### 6.3.1 Continuous translation process

In Section 4.5 of Chapter 4, we discussed the translation process in a broad sense, from source content extraction to pre-processing, memory/database check, translation – both human translation (HT) and machine translation (MT) – and publishing. In a continuous translation workflow, there is an extra post-processing step, which accumulates and updates a database (human and/or machine memory) so that it can be leveraged in the next translation task.

In Figure 6.1, we describe some relevant NLP tasks that the translator can conduct at each step of a continuous translation process. For example, NLP technologies such as OCR and document parsing can be used to automatically extract translatable strings from the original content (spoken signals and written text) to produce source text/speech to be further processed. Sequence segmentation from source text/speech to input, and other analytical tasks such as domain detection and quality estimation, can be automated. From input to memory check, functionalities such as terminology extraction and named entity recognition can be used to highlight specific memory. During post-processing, multiple NLP technologies can be used to collect and compile parallel corpora for machine training, including data cleaning using NLP packages, automatic labeling, and automatic alignment. Finally, when the translated content is ready to be published, NLP tasks such as text-to-speech and subtitle synchronization can automate relevant publishing activities.

### 6.3.2 User purposes at each step of a continuous translation process

As mentioned in Section 6.1, NLP tasks in a continuous translation process are driven by the users’ needs, which can be difficult to categorize. The user can always select a particular set of tools, design NLP tasks, and customize these tools according to their purposes, including productivity gains, quality assurance, human value maximization, and continuous machine learning. While human intentions are very individual and difficult to categorize, we can classify them based on shared purposes at each step of a continuous translation process, as shown in the list of examples in Table 6.1.
