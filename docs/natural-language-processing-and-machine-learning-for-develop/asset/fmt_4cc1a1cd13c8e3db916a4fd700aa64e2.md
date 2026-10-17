
Two words on the left and the right (bigrams) for word2vec

*Key point: only one embedding for each word (regardless of its context)*

Group 3—Contextual word representation (BERT et al):

transformer architecture (no CNNs/RNNs/LSTMs)

Pays “attention” to ALL words in a sentence

*Key point: words can have multiple embeddings (depending on the context)*

As you can see, algorithms in group 1 provide one word embedding per word but no context is captured in the word embedding. Group 2 algorithms are an improvement because they provide context for word embeddings. Finally, group 3 algorithms generate multiple word embeddings for the same word that appears in multiple sentences. This feature is a significant improvement over group 2 algorithms, which in turn are a significant improvement over group 1 algorithms.

## What is Topic Modeling?

Topic modeling is a technique for finding topics in one or more documents, and it’s also a form of “dimensionality reduction.” There are two underlying assumptions:

Each document consists of a mixture of topics.

Each topic consists of a collection of words.

Topic models assume that the semantics of a document are governed by so-called latent variables that are not immediately observable, which are topics that tend to be more abstract than the actual text. The goal of topic modeling is to uncover these latent variables (topics) that can reveal the primary content of a document or corpus.

Determining the main topics in documents can be performed in various ways, which is the topic of the next section.

### Topic Modeling Algorithms

There are several well-known algorithms for topic modeling, some of which are listed below:

Latent dirichlet analysis (LDA)

Latent semantic indexing (LSI)

Latent semantic analysis (LSA)

More details regarding LDA are in the next section, and you can perform an Internet search for details regarding LSI and LSA.

### LDA and Topic Modeling

LDA is a dimensionality reduction technique that is well-suited for topic modeling. LDA is a generative model that assigns topic distributions to documents. Each document is described by a distribution of topics, and each topic is described by a distribution of words. Please keep in mind that the rest of this section contains a high-level description of LDA, which in turn involves concepts such as KL Divergence and the JS metric that are discussed in Appendix A.

LDA starts with a fixed set of topics, where each topic represents a set of words. Next, LDA maps documents to a set of topics, and document words are mapped to those topics.

LDA is also a clustering method that supports the concept of soft-clustering, which allows different cluster to overlap (so words can belong to multiple clusters). Soft clustering is advantageous because it’s simpler to find similar words; however, it’s more difficult to determine distinct clusters in LDA.

Note that LDA differs from the kMeans algorithm because the latter is based on hard-clustering, which means that each word belongs to a single cluster.

An LDA model assumes that documents contain several overlapping topics, along with the following:

Topics are based on the words in each document.

The actual topics may not be known in advance.

The actual topics do not need to be specified.

The number of topics must be specified in advance.

Recall that LDA supports soft clustering, and therefore the same word can appear in multiple topics (i.e., a topic has the role of a cluster). In addition, the LDA model is called “latent” because LDA generates the following latent (hidden) variables:

a distribution over topics for each document

a distribution over words for each topics

LDA uses the JS (Jenson-Shannon) metric, which is based on JS divergence, and the latter is based on KL divergence (more information about these topics in an appendix). Since JS divergence is a metric, it’s also symmetric, which means that the similarity of two documents Doc1 and Doc2 is the same as the similarity of Doc2 and Doc1 (which is obviously a desirable property).

LDA uses the JS metric to determine which documents in a corpus are the most similar to document D by comparing the topic distribution of document D to the topic distributions of the documents in the corpus. As you might have already surmised, a smaller JS value for a pair of documents indicates greater similarity between the documents.

LDA is related to ANOVA as well as PCA (discussed in an appendix), but there are some differences. For instance, ANOVA uses categorical independent variables and a continuous dependent variable. By contrast, LDA involves the “reverse” of ANOVA: it uses continuous independent variables and a categorical dependent variable. Another key point: LDA assumes that the independent variables are normally distributed.

LDA and PCA share one particular aspect: both involve calculating linear combinations of variables. However, LDA tries to model the difference between the classes of data, whereas PCA ignores the difference in class.

### Text Classification versus Topic Modeling

Text classification involves supervised learning on documents or articles with a known set of labels and classifies text into a single class. By contrast, topic modeling involves unsupervised learning, and it’s a process of analyzing documents/articles. Topic modeling finds groups of co-occurring words in text documents, and co-occurring related words are “topics.” In cases where the set of possible topics is unknown, topic modeling can be used to solve text classification problems to identify the topics in a document.

### Language Models and NLP

In brief, a language model is a probability distribution (which is discussed in Appendix A) for sequences of words. Statistical language modeling refers to the creation of probabilistic models that predict the next word in a sequence based on the words that precede the predicted word. Calculating the probability of word occurrences involves examples of text. Models can be based on individual words, short sequences, sentences, or paragraphs.

Language models are used in machine learning and unsupervised learning (search/IR and clustering/topic modeling). A language model also tries to distinguish between similar sounding words. However, language models face some challenges, such as data sparsity and determining the likelihood of different phrases. One approach involves the use of n-gram models (described elsewhere in this chapter).

According to some NLP experts, language models learn only from co-occurrence patterns in the streams of symbols that they are trained on. Furthermore, there are at least two issues pertaining to language models:

Symbol streams lack crucial information.

Language models lack communicative intent.

Although pure language models do not have a counterpart to machine learning models that are trained via labeled datasets, some NLP experts believe that it’s possible for language models to achieve language understanding.

### How to Create a Language Model

There are three main ways to create a new language model in NLP for a given task:

Create a new model “from scratch.”

Transfer learning (use a pretrained model).

Transfer learning plus vocabulary enhancement.

Language models can also be classified into different subtypes. For example, neural language models (also called continuous space language models) are based on neural networks. Such models use continuous representations or embeddings of words to make their predictions. More details regarding language models are here:

[https://en.wikipedia.org/wiki/Language_model](https://en.wikipedia.org/wiki/Language_model)

Language models are the intuition behind vector space models, which is the topic of the next section.

## Vector Space Models
