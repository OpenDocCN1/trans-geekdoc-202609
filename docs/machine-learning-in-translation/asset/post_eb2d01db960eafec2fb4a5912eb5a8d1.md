
word occurs near a target word, which is the term-term matrix solution, word2vec trains a classifier on a binary prediction task to answer the question *Is word w likely to show up near the target word*? In word2vec, what is more important is not the prediction task itself, but rather the resulting learned classifier weights, which are used as the word embeddings.

There are two related models for computing continuous vector representations of words from very large data sets: continuous bag-of-words (CBOW) and continuous Skip-gram model architectures. The CBOW architecture predicts the current word based on the context, and the Skip-gram model predicts surrounding words given the current word. CBOW and Skip-gram models are shallow, two-layer neural networks that are trained to reconstruct linguistic contexts of words.

## The word2vec tool

takes a text corpus as input and produces the word vectors as output. It first constructs a vocabulary from the training text data and then learns vector representation of words. The resulting word vector file can be used as features in many natural language processing and machine learning applications.

> (Word2vec, 2013, n.p.)

Mikolov, Chen, et al. (2013) provide an example of word pair relationships using the Skip-gram model trained on 783 million words with 300 dimensionality.³ Their research result shows that word vectors can capture a range of syntactic and semantic regularities; for example, Paris – France + Italy = Rome, and Miami – Florida + Baltimore = Maryland (p. 10).

Word2vec methods are fast, efficient to train, and easily available online with code and pre-trained embeddings. Word2vec embeddings (2022) are static embeddings, meaning that the method learns one fixed embedding for each word in the vocabulary. Other methods for learning dynamic contextual embeddings include the popular BERT (Bidirectional Encoder Representations from Transformers) and ELMO (Embeddings from Language Models) representations, in which the vectors for each word vary across contexts. The basic principles of word2vec underlie these more powerful dynamic or contextualized embeddings, which are beyond the scope of this book.

## 3.4 Predicative LMs and translation

Predicative LMs offer a new dimension of to linguistic data.
- NMT architecture differs from SMT, as NMT models take the form of neural networks composed of a large number of simple components wired together.
- Fundamentally, MT aims to solve a human problem. In this sense, MT can learn from the human approach to translation and become an instantiation of human translation processes with its own characteristics.

### 4.1 Introduction

This chapter adopts a holistic approach to machine translation (MT) for three main reasons. First, when discussing machine translation with a focus on its impact on the human translation process, it makes sense to broaden attention to the entire localization process, rather than limiting it to activities involving the conversion of meaning from one language to another in the narrow sense. While localization may sound to the layperson like a strictly linguistic process, identical or similar to translation, it is much broader. The Localization Industry Standards Association¹ defines localization as “the process of modifying products or services to account for differences in distinct markets” (LISA, 2003, p. 34), and it has been investigated in both study and practice. While Pym (2014) considers localization as a paradigm of
