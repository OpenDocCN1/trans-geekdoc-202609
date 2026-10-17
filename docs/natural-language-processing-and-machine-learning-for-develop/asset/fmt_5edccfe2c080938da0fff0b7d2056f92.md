
The next portion of [Listing 10.15](#ch10.xhtml#list10.15) initializes the variable model, which is a Keras-based neural network consisting of various layers. If you are unfamiliar with Keras, Appendix D contains the details regarding the construction of neural networks in Keras.

After the model is compiled via model.compile() and trained via model.fit(), the score variable is initialized with the result of invoking the model.evaluate() on the test data contained in x_test and y_test. Please refer to Appendix D for more details regarding these methods.

The final section of [Listing 10.15](#ch10.xhtml#list10.15) displays the test score and the test accuracy. Launch the code in [Listing 10.15](#ch10.xhtml#list10.15) and you will see the following output:

Loading data... 8982 train sequences 2246 test sequences 46 classes   Vectorizing sequence data... x_train shape: (8982, 1000) x_test shape: (2246, 1000)   Convert class vector to binary class matrix (for use with categorical_crossentropy)   y_train shape: (8982, 46) y_test shape: (2246, 46)   Building Keras-based model...   Compilation step...   Training step... Train on 8083 samples, validate on 899 samples Epoch 1/5 8083/8083 \[==============================\] - 2s 254us/sample - loss: 1.4200 - accuracy: 0.6850 - val_loss: 1.0709 - val_accuracy: 0.7686 Epoch 2/5 8083/8083 \[==============================\] - 1s 180us/sample - loss: 0.7741 - accuracy: 0.8212 - val_loss: 0.9344 - val_accuracy: 0.7964 Epoch 3/5 8083/8083 \[==============================\] - 2s 189us/sample - loss: 0.5363 - accuracy: 0.8668 - val_loss: 0.8815 - val_accuracy: 0.7953 Epoch 4/5 8083/8083 \[==============================\] - 1s 179us/sample - loss: 0.4098 - accuracy: 0.9005 - val_loss: 0.8717 - val_accuracy: 0.8087 Epoch 5/5 8083/8083 \[==============================\] - 2s 187us/sample - loss: 0.3241 - accuracy: 0.9167 - val_loss: 0.9160 - val_accuracy: 0.8031 Evaluation step... 2246/2246 \[==============================\] - 0s 99us/sample - loss: 0.8997 - accuracy: 0.7916   Test score:    0.8997269553577698 Test accuracy: 0.79162955 

## **Summary**

This chapter introduced you to NLP and TF2/Keras, with code samples that illustrate various topics that were introduced in Chapter [3](#ch03.xhtml).

You saw an example of using the kNN algorithm to perform text classification on a set of documents (albeit very short documents). In addition, you saw how to modify the kNN code sample to solve the same task using decision trees, random forests, SVC, Naïve Bayes, and the kMeans algorithm. These code samples illustrated the fact that the accuracy can vary substantially among different machine learning algorithms.

Next, you saw several TensorFlow code samples for performing some NLP-related tasks. Finally, you saw an example of a Keras-based neural network that performed text summarization on the Reuters dataset.

# CHAPTER 11

# TRANSFORMER, BERT, AND GPT

This chapter covers the concept of attention, the transformer architecture, the pretrained BERT model and its variants, and features of GPT-2 and GPT-3 from OpenAI. If you are familiar with some of these topics, feel free to skim through the material in this chapter and peruse the Python-based code samples.

The first part of this chapter contains a brief introduction to the concept of attention, which is a powerful mechanism for generating word embeddings that contain context-specific information for words in sentences. The concept of attention is a key aspect of the transformer architecture. This section also contains a summary of the distinguishing characteristics of three types of word embeddings, in which the most powerful technique is the attention-based approach.

The second part of this chapter provides an overview of the transformer architecture that was developed by Google and released in late 2017. This section also discusses the T5 (text-to-text transfer transformer) model that converts all NLP tasks into a text-to-text format.

The third part of this chapter introduces you to BERT, along with various code samples that illustrate how to invoke some of the BERT APIs. Note that this section relies on the installation of the HuggingFace transformers Python library.

The fourth part of this chapter contains a list of several BERT-based trained models, along with brief description of their functionality. Some of the models that are discussed include DistilledBERT, CamemBERT, and FlauBERT. The final part of this chapter introduces you to the GPT-based models from OpenAI, along with some of the amazing features in GPT-3.

## **What is Attention?**

*Attention* is a mechanism by which contextual word embeddings are determined for words in a corpus. Unlike word2vec or gloVe, the attention mechanism takes into account *all* the words in a sentence during the process of creating a word embedding for a given word. As a result, the same word that is used in multiple sentences will have a different word embedding in each of those sentences.

Prior to the attention mechanism, popular architectures were based on RNNs, LSTMs, or bi-LSTMs. In fact, the attention mechanism was first used in conjunction with RNNs or LSTMs. However, the Google team performed some experiments involving machine translation tasks on models that relied on the attention mechanism and the transformer architecture, and discovered that those models achieved higher performance that models that included CNNs, RNNs, or LSTMs. This result led to the expression “attention is all you need.” The seminal paper regarding the transformer architecture is here:

*[https://papers.nips.cc/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf](https://papers.nips.cc/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf%20)*

As a quick review, and before delving into details of the attention mechanism, let’s look at a summary of the main types of word embeddings that we have encountered in this book, as discussed in the next section.

### **Types of Word Embeddings**

This section contains a summary of the main features of three types of word embeddings. The first group consists of the simplest algorithms for word embeddings that have been discussed in previous chapters. The second group consists of the earliest algorithms that use neural networks (word2vec and fasttext) or matrix factorization (gloVe) for generating word embeddings. The third group involves contextual algorithms for creating contextual word representations, which are essentially state of the art algorithms. Here is the summary:

1.  Discrete word embeddings (BoW, tf, and tf-idf):

    Word vectors consist of integers, decimals, and decimals, respectively

    Key point: word embedding have zero context

2.  Distributional word embeddings (word2vec, GloVe, fasttext):

    Based on shallow NN, MF, and NN, respectively

    Two words on the left and the right (bi-grams) for word2vec

    Key point: a single word embedding for each word that is used for every occurrnence of that word, regardless of its context.

3.  Contextual word representations (BERT et al):

    Transformer architecture (no CNNs/RNNs/LSTMs required)

    Pays “attention” to ALL words in a sentence

    Key point: words can have multiple embeddings (depending on the context)

### **Types of Attention and Algorithms**

There are several types of attention mechanisms, three of which are listed here:

1.  self-attention

2.  global/soft

3.  local/hard

*Self-attention* tries to determine how words in a sentence are interconnected with each other. Multiheaded attention uses a block of multiple self-attention instead of just one self-attention. However, each head processes a different section of the embedding vector.

In addition to the preceding attention mechanisms, there are also several attention algorithms available:

*   additive

*   content-based

*   dot product

*   general

*   location-based

*   scaled dot product <= transformer uses this technique
