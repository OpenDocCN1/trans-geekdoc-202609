
A `vector space model` (VSM) is based on a mathematical model called a `vector space`, in order to represent text documents as vectors of identifiers (for example, using tf-idf weights). If you are unfamiliar with vector spaces, there is a brief introduction to vector spaces in one of the appendices, and if need be, you can find additional information through an online search.

A `VSM` consists of a two-dimensional array of (usually) numeric values that are based on `frequencies`. The latter restriction on the data values creates a “link” between a `VSM` and the distributional hypothesis. A `VSM` whose values are based on sophisticated algorithms can overcome the shortcomings of losing semantics and feature sparsity in BoWs: *[https://en.wikipedia.org/wiki/Vector_space_model](https://en.wikipedia.org/wiki/Vector_space_model)*

As a point of clarification, the following matrices do *not* represent vector space models:

*   an arbitrary matrix

*   an adjacency matrix for a tree or graph

*   a feature matrix

*   a covariance matrix

*   a correlation matrix

*   a recommender system

Recommender systems are included in the preceding list because they populate a user-item matrix whose cells contain a numeric rating of items; however, the data in such a matrix is *not* derived from event frequencies, which explains why recommender systems are not VSMs.

Now that you have seen examples of matrices that are not VSMs, the following list contains some examples of vector space models:

*   a term-document matrix (discussed later)

*   a context-document matrix

*   a matrix based on word2vec

*   the latent semantic analysis (LSA) algorithm

*   a pair-pattern matrix

With the preceding in mind, here is a short list of some models that are based on (or extend) the VSM model:

*   generalized vector space model

*   latent semantic analysis (LSA)

*   term discrimination

*   Rocchio classification

*   random indexing

### **Term-Document Matrix**

A `term-document` matrix `M` is an `mxn` matrix where `n` is the number of documents and `m` is the number of unique words in the `n` documents. The value in a cell `(i,j)` in a term-document matrix `M` equals the number of times that the term `i` appears in document `j`. Moreover, the value in a cell `(i,j)` can be based on other calculations, such as tf (term frequency) or tf-idf values. Note that for a large corpus, the matrix `M` contains mainly zero values, which means that `M` is a sparse matrix (and operations are less efficient). Also keep in mind that a tf-idf vector is a vector representation of a *document* whereas a `word2vec` vector is a vector representation of a *word*.

There are two more points of interest regarding a term-document matrix `M`. First, if two documents are similar, then the two corresponding columns in `M` will tend to have similar patterns of numbers, which in turn means that their cosine similarity will be closer to 1. Second, instead of focusing on column vectors we can examine row vectors in order to measure word similarity.

We can also generalize the concept of a term-document matrix by expanding the meaning of a document to include phrases, sentences, paragraphs, and so forth. After doing so, the result is a `word-context` matrix.

### **Tradeoffs of the VSM**

VSMs are not a perfect solution: some of the advantages and disadvantages of a VSM are related to the advantages and disadvantages of the algorithms that are used to compute the values in the cells of a VSM.

One advantage of a `VSM` model is because it’s based on linear algebra. In addition, it’s possible to compute a degree of similarity between queries and documents in a continuous fashion, which then enables you to rank documents according to their possible relevance. Furthermore, `VSM` models support partial matching.

However, long documents are poorly represented because they have poor similarity values (a small scalar product and a large dimensionality). Word substrings can result in a “false positive match,” which means that search keywords must match document terms. Unfortunately, documents with similar context and also different term vocabulary won’t be associated, which results in a “false negative match.”

In addition, the order in which the terms appear in the document is not tracked in the vector space representation, along with the assumption that terms are statistically independent. Even so, some of the disadvantages can be ameliorated by using techniques such as singular value decomposition (SVD).

## **NLP and Text Mining**

In high-level terms, text mining performs an analysis of large amounts of unstructured data in order to find patterns in that data. Text mining tasks involve finding keywords, topics, and patterns. The general sequence of steps (tasks) is shown here:

*   preprocessing

*   text transformation

*   attribute selection

*   visualization

*   evaluation

Text mining also involves document classification whereby similar documents are placed in the same group. Text mining is useful for extracting product-related details, such as customer reviews, product issues, and so forth. Applications of text mining include spam detection, sentiment analysis, e-commerce and customer segmentation. The NLTK (Natural Language ToolKit) library is well-suited for text mining tasks, and you will see code samples in Chapter [6](#ch06.xhtml).

### **Text Extraction Preprocessing and N-Grams**

As you learned earlier in this chapter n-grams are one type of language model that assigns numeric probabilities to word sequences. For example the 3-grams of a sentence is a set of tuples of length 3, where a tuple consists of three consecutive words in that sentence. Note that the terms unigram, bigram, and trigram are often used when n is 1, 2, or 3, respectively.

## **Relation Extraction and Information Extraction**

In simplified terms, *relation extraction* (RE), *information extraction* (IE), and *relation classification* involve various aspects of searching a corpus to find subsets of text that describe relationships between words in those subsets of text. Relation extraction is a key component of NLU (Natural Language Understanding), and in general, relation extraction involves extracting relational triplets of text, such as (founder, steve_jobs, apple).

Although these three concepts overlap, they have significant differences. Relation extraction involves finding semantic relationships in a corpus. In addition, relation extraction is a subfield of information extraction, where the latter involves extracting structured information from natural language text. However, relation extraction differs in one important respect from IE: the latter also performs disambiguation. The `sense2vec` algorithm is one algorithm for word sense disambiguation that can be used with SpaCy:

*[https://github.com/explosion/sense2vec](https://github.com/explosion/sense2vec)*

As an example: if you have ever summarized a text document, you probably searched for the most important words (typically nouns) and the relationship between those words: this task is a form of IE. In fact, IE is relevant for multiple NLP tasks, including text summarization and question–answering systems.

On the other hand, *relation classification* is the task of identifying the semantic relation between two nominal entities in text. As you might have surmised, there is no one-size-fits-all solution that works for multiple domains (e.g., healthcare, biology, and chemistry).

One more point of interest is the “Never Ending Language Learning” (NELL) semantic machine learning system from Carnegie Mellon University that extracts relationships from the open Web:

*[https://en.wikipedia.org/wiki/Never-Ending_Language_Learning](https://en.wikipedia.org/wiki/Never-Ending_Language_Learning)*

## **What is a BLEU Score?**
