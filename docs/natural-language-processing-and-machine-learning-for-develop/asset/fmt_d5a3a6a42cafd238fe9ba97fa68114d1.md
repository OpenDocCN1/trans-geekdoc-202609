
Since the input layer and the output layer have the same size, this shallow network is very similar to an autoencoder, whose purpose is to compress the one-hot encoded words of a vocabulary into a smaller representation (similar to the purpose of PCA in machine learning).

For example, suppose we have a vocabulary of 10,000 words (assume they’re English words to keep things simple), and we want to find a representation for each word that consists of a 1×300 vector of floating point numbers. Then the weight matrix between the input layer and the hidden layer is a 10,000 × 300 matrix (let’s call it `W1`), and the matrix between the hidden layer and the output layer is a 300 × 10,000 matrix. (Let’s call it `W2`.)

The neural network is “trained,” which means that the weights of the edges in the neural network are updated by a process called “backward error propagation.” When the training process is completed, we discard everything except for the weight matrix `W1`, which consists of 10,000 rows, each of which is a word in the initial vocabulary. Each row is 300 columns wide, and this 1×300 vector of floating point numbers is the encoding for the current word.

### **Neural Network Reduction**

There are two techniques to reduce the size of the weight matrices in the neural network that is described in the previous section:

*   subsample frequent words (which decreases the number of training examples)

*   modify the optimization objective via “negative sampling”

These two techniques reduce the computational complexity and also improve the quality of the results.

The intuition underlying negative sampling is to modify a small portion of the model weights, which involves finding skip-grams for a given word. An earlier section showed you how to find the bigrams of a simple sentence, which is reproduced here:

[(ate,the), (ate,big), (ate,mouse), (ate, the), (ate,cheese)]

As you can see, the previous set of bigrams includes stop words, which you can remove during the cleaning process. Alternatively, there is a formula to calculate the probability of retaining a word that appears in a vocabulary. If `w1` is a word in a vocabulary and `f(w1)` is the frequency of the word in a document, then the probability `P(w1)` that `w1` will be retained is given here:

`P(w1) = [1 + sqrt(f(w1)*1000)] * 0.001/f(w1)`

Another important Python library for generating distributed word embeddings is GloVe, which is the topic of the next section.

##**What is GloVe?**

As you learned earlier in this chapter, word2vec algorithms are based on neural networks. By contrast, GloVe uses *matrix factorization* techniques from linear algebra and word-content matrices. GloVe creates a co-occurrence matrix for a given (local) context, and then decomposes the global matrix.

GloVe is similar to word2vec, with an important difference: Glove exploits the global co-occurrences of words instead of relying on the local context. GloVe proceeds as follows:

1.  construct a co-occurrence matrix of dimensionality words x context

2.  factor the matrix into a matrix of dimensionality word x features

In the initial matrix, the rows are words and the columns are word frequencies in a corpus. The factored matrix has a lower dimensionality, and the rows are the vector representations of the initial words.

GloVe can provide 100-dimensional dense vectors as word embeddings. However, there are two important limitations in GloVe. First, GloVe does not support OOV (Out of vocabulary) words. Second, GloVe does not support polysemy, which refers to words that have multiple meanings, which is determined by the context of the words in a sentence. Consider using models that provide support, such as ELMo and USE (Universal Sentence Encoder).

In case you’re interested in the GloVe approach, the CoVe (McCann, 2017) is based on the GloVe algorithm. CoVe (“contextual vectors”) uses machine translation to generate contextual vectors and does not use language modeling.

##**Working with GloVe**

GloVe is a Python-based library (developed at Stanford University) for word embeddings, and it’s an acronym for “Global Vectors [for word representation]”.

GloVe performs unsupervised learning of word embeddings that is based on co-occurrence matrices. As such, GloVe combines two techniques:

1.  Global Matrix Factorization (GMF)

2.  Local Context Window (LCW)

In brief, *Global Matrix Factorization* uses matrix factorization methods from linear algebra that perform rank reduction on a large term-frequency matrix. Note that the matrices can represent term-document frequencies, in which case matrix rows are words and the matrix columns are documents (or paragraphs). Alternatively, matrices can represent term-term frequencies, with words on both axes and measure co-occurrence.

GMF applied to term-document frequency matrices is called *latent semantic analysis* (LSA), and the high-dimensional matrix in LSA is reduced via *singular value decomposition* (SVD). More details regarding matrix factorization are here:

*[https://machinelearningmastery.com/introduction-to-matrix-decompositions-for-machine-learning/](https://machinelearningmastery.com/introduction-to-matrix-decompositions-for-machine-learning/)*

*Local context window* is a word embedding model that learns semantics by passing a window over the corpus line-by-line. This technique predicts the surroundings of a given word (e.g., skip-gram model) or predicts a word given its surroundings (e.g., CBoW).

The third important Python library for generating distributed word embeddings is fastText, which is the topic of the next section.

##**What is FastText?**

Facebook developed the fastText NLP library, and you can install fastest with the following command:

`pip3 install fasttext`

The fastText library uses unsupervised learning to perform text clustering of data, which means that fastText uses a clustering algorithm. The `train_unsupervised()` method in fastText uses the skip-gram model in order to generate 100-dimensional vectors. In addition, fastText computes the similarity score between words, along with the `get_nearest_neighbors()` method to display the top 10 words that are the most similar to a given word. Similarity scores between pairs of words that are close to 1 indicates that the pair of words are more similar in meaning.

FastText leverages word2vec by learning vector representations for each word and the n-grams in each word. Next, a vector is created whose values are the average values of the representations during each training step. This step enables word embeddings to encode sub-word information. FastText vectors are more accurate than word2vec vectors based on various criteria. Moreover, fastText can handle OOV words, and the sub-word n-grams correspond to “intuition” (shown for multiple languages).

One useful advantage of vector generation techniques such as fastText is that no labeled data is required.

##**Comparison of Word Embeddings**

This section contains a summary of the main features of three types of word embeddings. The first group consists of the simplest algorithms for producing word vectors for words: these algorithms were introduced in this chapter and the previous chapter. The second group consists of the earliest algorithms that use neural networks (i.e., word2vec and fastText) or matrix factorization (gloVe) (such as word2vec) for generating distributional word embeddings. The third group involves contextual algorithms for creating word embeddings, which are essentially state of the art algorithms. For your convenience, a bullet list for each of the three groups is given below:

*   Group 1—Discrete word embeddings (BoW, tf, and tf-idf):

    Word vectors consist of integers, decimals, and decimals, respectively

    *Key point: word embedding have zero context*

*   Group 2—Distributional word embeddings (word2vec, GloVe, fasttext):

    Based on shallow NN, MF, and NN, respectively
