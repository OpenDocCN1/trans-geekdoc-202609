
5.  Calculate the cosine similarity of the question with the sentences in the corpus.

6.  Determine which sentence has the highest cosine similarity.

7.  Use the previously selected sentence as a response to users.

As you can see, you already know how to perform all the steps in the preceding pseudo-code.

In case the highest cosine similarity is close to zero, then there is no meaningful response for the query, in which case you can route the users to a human agent. Of course, the threshold value for “close to zero” is a number that you decide in advance, and perhaps it can be determined through experimentation.

### Chatbot Abuses

There have been some well-known cases of attempts to crowd-source the training of chatbots that have gone awry. One such chatbot is Tay from Microsoft, which some users trained to make various types of highly inappropriate remarks about certain groups of people.

Another (more recent) example is the chatbot Lee Luda from Korea, which was designed to emulate a Korean university student. However, this chatbot was removed from Facebook because some users trained the chatbot to make derogatory slurs and hate speech that were directed toward certain groups of people.

Unfortunately, chatbots are likely to encounter these sorts of issues when the enhancement of a chatbot’s capabilities involve crowd-sourced contributions.

### Useful Links

The definition of “useful” and “interesting” obviously varies among people, and you can peruse top-ten lists, which do not provide the breadth and diversity of existing chatbots. If you are unfamiliar with chatbots, navigate to the following link that has thousands of registered chatbots (sort of like a “play store” for chatbots):

*[https://botlist.co](https://botlist.co)*

Regarding specific chatbots: Microsoft developed and open-sourced BlenderBot, which at its peak was the largest state-of-the-art chatbot, which is available here:

*[https://ai.facebook.com/blog/state-of-the-art-open-source-chatbot/](https://ai.facebook.com/blog/state-of-the-art-open-source-chatbot/)*

BlenderBot was benchmarked (and is significantly better) against Google’s Meena chatbot, and the latter is available here:

[https://github.com/google-research/google-research/tree/master/meena](https://github.com/google-research/google-research/tree/master/meena)

If you are interested in chatbots in the health-care field, here are two useful links:

*https://topflightapps.com/ideas/chatbots-in-healthcare">https://github.com/google-research/google-research/tree/master/meena*

If you are interested in chatbots in the health-care field, here are two useful links:

*[https://topflightapps.com/ideas/chatbots-in-healthcare](https://topflightapps.com/ideas/chatbots-in-healthcare)*

*[https://emerj.com/ai-application-comparisons/chatbots-for-healthcare-comparison](https://emerj.com/ai-application-comparisons/chatbots-for-healthcare-comparison)*

If you plan to create a chatbot that is useful, then it probably needs to understand (human) natural language, and also solve a task that might require multiple steps.

Although there are online tools that enable you to create chatbots that connect to an AI backend system (such as IBM Watson), the following link explains how to build a chatbot in Keras:

*[https://www.kdnuggets.com/2019/08/deep-learning-nlp-creating-chatbot-keras.html](https://www.kdnuggets.com/2019/08/deep-learning-nlp-creating-chatbot-keras.html)*

*[https://analyticsindiamag.com/how-does-a-simple-chatbot-with-nltk-work/](https://analyticsindiamag.com/how-does-a-simple-chatbot-with-nltk-work/)*

The following link shows you how to create a chatbot based on a pretrained transformers (discussed in Chapter [11](#ch11.xhtml)) with PyTorch:

*[https://towardsdatascience.com/conversational-ai-chatbot-with-pretrained-transformers-using-pytorch-55b5e8882fd3](https://towardsdatascience.com/conversational-ai-chatbot-with-pretrained-transformers-using-pytorch-55b5e8882fd3)*

Finally, the following list of top chatbots of 2021 might provide ideas and helpful insights: *[https://www.netomi.com/best-ai-chatbot](https://www.netomi.com/best-ai-chatbot)*

## Summary

This chapter started with a description of two types of text recommendation, along with some code samples using gensim and spaCy. Then you got a high-level description of recommendation systems, which are used in online reviews of books, movies, restaurants, and so forth. Next, you learned about sentiment analysis, which is actually a subset of text classification. In essence, sentiment analysis attempts to assess the mood (positive, negative, or neutral) of a document (such as a review). Finally, you saw a Python-based code sample that uses logistic regression to predict spam email messages.

# CHAPTER 10

# NLP AND TF2/KERAS

This chapter contains machine learning Python code samples that involve TF2/Keras. The NLP concepts in the code samples were introduced in Chapter [3](#ch03.xhtml), and also written in various NLP toolkits that are discussed in Chapter [5](#ch05.xhtml) and Chapter [6](#ch06.xhtml).

The first section contains TensorFlow-based code samples that perform tokenization, encoding and word embeddings. The second section contains a Python code sample that uses the kNN machine learning algorithm to predict the category of a set of sentences, where the categories are a subset of a well-known set of 20 categories. This section also shows you how to modify the kNN-based code sample so that you can perform the same task using decision trees, random forests, SVC, and naïve Bayes. These code samples illustrated the fact that the accuracy can vary substantially among algorithms.

The third section contains several TensorFlow code samples for performing some NLP-related tasks. The last code sample in this chapter is an example of a Keras-based neural network that performed text summarization on the Reuters dataset.

One more thing to keep in mind: this chapter does not provide explanations of Tensorflow concepts. If you are unfamiliar with Tensorflow, please read Appendix E, Introduction to TensorFlow 2, so that you will be better prepared for the code samples in this chapter.

## NOTE

1.  *As this book goes to print,* Python *3.7 works with the TF 2 code in this book, whereas Python 3.9.x does not work with TF 2.*

2.  *For the* Python *file* tf2\_basic\_nlp.py*you need to run this command:*

      install tensorflow-text # <= note the "-" instead of "\_" 

## Term-Document Matrix

Suppose that V is a vocabulary of words and D is a set of documents. A *term-document matrix* for D and V is a \[|V|,|D|\] matrix (not the other way around) that contains |V| × |D| elements.

The cell in position (i,j) in D pertains to the ith word vi and the jth document dj. The value in cell (i,j) equals the number of occurrences of word vi in document dj (i.e., the term frequency). Each column in this matrix gives a vector of dimension |V| that represents a document. This matrix is a BoW representation of documents, except that V does not contain all words from the documents in D. In addition to specifying the number of occurrences of a word in cells, you can also use tf-idf values in the cells of this matrix, as well as other weighted scores.

The transpose of a term-document matrix is called a *document-term matrix*, which is a special case of a *document-feature matrix*, where a feature can be a property other than terms in documents. Check the gensim documentation for a description of efficient algorithms that construct term-document matrices.

## Text Classification Algorithms in Machine Learning

There are many text classification algorithms available, some of which are listed here:

*   kMeans (clustering algorithm)

*   Multinomial naive Bayes (multiclass classification)

*   Logistic regression ( sklearn supports multilabel)

*   SVMs (support vector machines)

*   Random forests (ensemble method)
