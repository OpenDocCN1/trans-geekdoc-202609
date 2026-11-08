
Inspired by similar successes in computer vision with deep learning models such as `CNNs` (e.g., `AlexNet`), which achieved a substantial boost in performance on `ImageNet` benchmark tasks in 2012 via deep learning alone, the NLP field set about developing equally successful deep learning models in their discipline. Although the benefits of deep learning came more slowly than in computer vision, the goal of revolutionizing NLP via deep learning has now been realized. Large neural networks are being applied to tasks ranging from sentiment classification and translation to dialog and question answering, to translating between languages from scratch, and beyond to startlingly realistic chatbots like OpenAI’s `ChatGPT`. Transformer-based language models such as `BERT` and the `generative pretrained transformer` (`GPT`) class of models currently obtain state-of-the-art performance across the vast majority of NLP tasks and have been used to create chatbots such as OpenAI’s `ChatGPT` system, capable of generating fluent human-like text and answering complex questions using inputs and outputs in natural language.

A key benefit of deep learning in NLP is the ability to mine massive quantities of text data to learn as much as possible from scratch, replacing features that have previously been hand-engineered by ones that are learned automatically. It is difficult to overstate the significance of this point, as it has led to a complete reconfiguration of NLP research. Before deep learning, good performance in any NLP task was generally achieved via engineering problem-specific features and/or carefully designed probabilistic models; this required highly specialized domain knowledge for that particular problem. Now, general-purpose models, often based on off-the-shelf models that have been “pretrained” on massive text corpora, are successfully deployed across the spectrum of NLP tasks with little-to-no manual feature-engineering effort. Echoing insights from the computer vision research field, the power and generality of massive (yet generic) text data can be married with curated domain-specific data by “fine-tuning” large pretrained deep neural networks on the more specific datasets, frequently leading to excellent performance.

Much of the recent success in deep learning for NLP is due to advances in `language models`, which are models for computing probabilities of sequences of words. While the modeling of language is intrinsically interesting in its own right, the practical benefit of these models arises from their benefits in solving NLP tasks, frequently due to their production of latent representations (embeddings) of words, sentences, or entire documents that are created during the training process.

A `large language model` (`LLM`) is a deep learning model with many parameters that is trained on massive natural language data, generally in an unsupervised way. Word embedding models such as `word2vec`, discussed later, are an early example of an LLM. While not the first neural language models by any means, the simplicity of these models sped up the training process, enabling them to be trained on internet-scale data, thus revealing the benefits of doing so and beginning the push toward ever-more-powerful LLMs on ever-larger datasets. Some large language models such as the `GPT` series of models from OpenAI, including their `ChatGPT` chatbot, can be used to generate natural language text and can answer complex queries with inputs and outputs in the form of natural language. These sophisticated LLMs make use of word embeddings as a building block in their architecture, so we will begin our discussion with these models.

## Word Embeddings

The goal of word embedding models is to learn vector representations of each word in the dictionary, called “`word embeddings`” (a.k.a. `word vectors`). As such, these word embedding models can be understood as a type of `representation learning`. Word embeddings are intended to capture the semantic meanings of the words and to reveal information about the relationships between the words by way of their relative positions in the embedding space. They can be used as features for downstream NLP tasks such as classifying documents, and they also form the basis for more sophisticated deep neural network language models.

To illustrate the motivation we have just discussed, consider the following short document:

*The quick brown fox jumps over the sly lazy dog*.

Traditional NLP methods would represent each word via their indices in the dictionary. The document could be represented as:

| The || quick || brown || fox || jumps || over || the || sly || lazy || dog |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| 1 || 3 || 37 || 50 || 42 || 2 || 1 || 22 || 58 || 12 |

![Image](images/T000121tabt0020.png)

Here, words are considered to be atomic units, and so their meaning cannot be scrutinized further. If we want to have vector representations for each word instead of a document-level vector representation, the earlier example could be equivalently rewritten with “one-hot encoding” vectors for each word token, with a single one in the entry corresponding to the word’s index and zeros elsewhere ([Table 11.1](#Ch012_433-471_B9780443158889000121.xhtml#t0010)).

Table 11.1

 One-hot encoding representations for words. Each column contains a representation for one of the words in the document, with a single one at the entry corresponding to the index of that word in the dictionary and zeros elsewhere 

|    || Document || The || quick || brown || fox || jumps || over || the || sly || lazy || dog |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| Index || Word ||   ||   ||   ||   ||   ||   ||   ||   ||   ||   |

| 1 || The || 1<mml:math><mml:mn>1</mml:mn></mml:math>![Equation](images/F000121si179.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si180.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si181.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si182.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si183.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si184.png) || 1<mml:math><mml:mn>1</mml:mn></mml:math>![Equation](images/F000121si185.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si186.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si187.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si188.png) |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| 2 || Over || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si189.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si190.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si191.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si192.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si193.png) || 1<mml:math><mml:mn>1</mml:mn></mml:math>![Equation](images/F000121si194.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si195.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si196.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si197.png) || 0<mml:math><mml:mn>0</mml:mn></mml:math>![Equation](images/F000121si198.png) |
