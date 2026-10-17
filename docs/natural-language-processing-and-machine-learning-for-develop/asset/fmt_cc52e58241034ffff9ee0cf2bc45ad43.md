
An underlying assumption of word2vec is that the meaning of words can be inferred from their surrounding words. Suppose that two words have similar neighbors (meaning: the context in which it’s used is about the same), then these words are probably quite similar in meaning or are at least related. For example, the words shocked, appalled and astonished are usually used in a similar context. As you saw earlier in this chapter:

"The meaning of a word can be inferred by the company it keeps."

Word2vec is well-suited for sentiment analysis based on a corpus of user-based reviews (such as movies, books, and so forth). This type of data is unstructured because there are almost no restrictions on the content of reviews (beyond a profanity rule). Other use cases for word2vec include:

* genes, code, likes, playlists, social media graphs

* other verbal or symbolic series in which patterns may be discerned

Word2vec can also be used for labeled data as well as unlabeled data. Keep in mind that algorithms which are designed to work with supervised data tend to require a large set of examples.

### The Word2vec Architecture

The word2vec architecture options are skip-gram (default) or continuous bag of words. The training algorithm involves hierarchical softmax (default) or negative sampling.

*Minimum word count*: This helps limit the size of the vocabulary to meaningful words. Any word that does not occur at least this many times across all documents is ignored.

Reasonable values could be between 10 and 100. Suppose a set of movie titles occur 30 times: then set the minimum word count to 40, to avoid attaching too much importance to individual movie titles. Higher values also help limit run time.

The following link contains information about backward error propagation in word2vec, with details for CBoW and skip-grams:

*[http://www.claudiobellei.com/2018/01/06/backprop-word2vec/](http://www.claudiobellei.com/2018/01/06/backprop-word2vec/)*

### Limitations of Word2vec

Word2vec provides only one word embedding per word. Moreover, a word embedding can only store one vector for each word. Other limitations of word2vec are listed below:

difficult to train on large datasets

fine tuning is not possible

training models is a domain-specific task

trained on a shallow neural network with one hidden layer

As you will see in Chapter [11](#ch11.xhtml), the attention-based mechanism overcomes the limitations of word2vec.

## The CBoW Architecture

Given a set of words, the CBoW model architecture starts with a set of surrounding words and then attempts to predict the target word (which is the center word). The CBoW model (which is one type of word2vec model) involves a feed forward neural network that determines word embeddings. The neural network consists of the following:

* an input layer

* a hidden layer (no activation function)

* an output layer (softmax activation function)

In addition, the input layer and output layer have the same size. Hence, this neural network resembles an autoencoder, which (in case you don’t already know) “squashes” the input values into a smaller vector to obtain a more compact representation of the input data.

[Figure 4.1](#ch04.xhtml#fig4.1) displays the CBoW architecture and [Figure 4.2](#ch04.xhtml#fig4.2) in the next section displays the skip-grams architecture, both of which are shallow neural networks.

![Figure 4.1 ¶ The CBoW Architecture.](images/fig4.1.jpg)

Figure 4.1 ¶ The **CBoW** Architecture.

*Source*: “Efficient Estimation of Word Representations in Vector Space.” Tomas Mikolov, Kai Chen, Greg Corrado, Jeffrey Dean. \[arXiv:1301.3781v2 \[cs.CL\] (CC BY 4.0)\]

## What are Skip-grams?

As you learned in the previous section, n-grams infer a missing word from the words that appear on both sides of the word, whereas skip-grams start with the “missing” word and attempt to infer the words that are most likely to appear on both sides of that missing word. In a sense, the key idea of skip-grams is sort of like an “inversion” of n-grams.

Skip-gram models predict the surrounding context words of a target word, and they are based on a neural network architecture that is discussed later in this chapter. In a sense, the skip-gram model works in the opposite manner of the CBoW model: skip-gram attempts to predict the surrounding words of a target word instead of a missing center word.

In slightly more detailed terms, the following sequence of steps provides a high-level description of the skip-gram algorithm:

* Treat the target word and a neighboring context word as positive examples.

* Randomly sample other words in the lexicon to get negative samples.

* Use logistic regression to train a classifier to distinguish those two cases.

* Use the weights as the embeddings.

Later you will see a diagram that displays the skip-gram architecture, right after you see an example of finding skip-grams, which is discussed in the next section.

### Skip-gram Example

A skip-gram is a tuple that contains words before and after a given word. The size of the type is an integer, which can be as small as 1. In particular, 1-grams, 2-grams, and 3-grams are also called unigrams, bigrams, and trigrams.

Let’s consider the following sentence (taken from the previous section):

'the big mouse **ate** the cheese' 

The set of 1-grams for “ate” is here:

\[mouse, the\] 

The set of 2-grams is here:

\[(ate,the), (ate,big), (ate,mouse), (ate, the), (ate,cheese)\] 

The set of 3-grams is here:

\[(ate,the,big), (ate,big,mouse), (ate,the,cheese)\] 

### The Skip-gram Architecture

[Figure 4.2](#ch04.xhtml#fig4.2) displays the skip-gram architecture that is based on a shallow neural network.

In order to fully understand this architecture, you need some familiarity with basic neural networks, the softmax activation function, and the concept of backward error propagation. In essence, the skip-gram architecture (along with the n-gram architecture) is based on machine learning concepts. If need be, you can read the relevant appendix that discusses neural networks.

As you can see from [Figure 4.2](#ch04.xhtml#fig4.2), the skip-gram architecture consists of the following components:

* the input layer is a single word

* a hidden layer

* an output layer (predicted context words)

Each word from the corpus is processed through the neural network, and after the model has been trained, the hidden layer contains the word embeddings. The concept of skip-grams is probably less intuitive than n-grams: how can we guess at the words that surround a single word?

![Figure 4.2 ¶ The Skip-gram Architecture.](images/fig4.2.jpg)

Figure 4.2 ¶ The Skip-gram Architecture.

An interesting point: although the skip-gram model has a larger memory requirement, its word embeddings are better than those generated by an n-gram model.

Keep in mind the following details regarding the shallow network for the skip-gram model:

* There is no bias term.

* There is no activation function between the input layer and the hidden layer.

* There is a softmax activation function from the hidden layer to the output layer.

* The input layer and the output layer have the same size.

If you are familiar with convolutional neural networks (CNNs), then you already know that the softmax activation function is applied between the right-most hidden layer and the output layer because it generates a set of positive numbers whose sum equals one. Thus, that set of output numbers is a probability distribution, and the index position with the highest probability value is compared with the index of the number 1 in the one-hot encoding of the input data: if the index values are equal, then it’s a match (otherwise it’s not a match).
