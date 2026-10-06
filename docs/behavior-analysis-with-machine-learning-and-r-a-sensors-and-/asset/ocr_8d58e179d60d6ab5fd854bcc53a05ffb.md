# CHAPTER 7. ENCODING BEHAVIORAL DATA

# 7.6 Bag-of-Words

The main idea of the Bag-of-Words (BoW) encoding is to represent a complex entity as a set of its constituent parts. It is called Bag-of-Words because one of the first applications was in natural language processing. Say there is a set of documents about different topics such as medicine, arts, engineering, etc. and you would like to classify them automatically based on their words. In BoW, each document is represented as a table that contains the unique words across all documents and their respective counts for each document. With this representation, one may see that documents about medicine will contain higher counts of words like treatment, diagnosis, health, compared to documents about art or engineering. Figures 7.13 and 7.14 show the conceptual view and the table view, respectively.

From these representations, it is now easy to build a document classifier. The word-counts table can be used as an input feature vector. That is, each position in the feature vector represents a word and its value is an integer representing the total count for that word.

> Note that in practice documents will differ in length, thus, it is a good idea to use percentages instead of total counts. This can be achieved by dividing each word count by the total number of counts. Also note that frequent words like 'the', 'is', 'it' can cause problems, so some extra preprocessing is needed. This was a simple example but if you are interested in more advanced text processing techniques I refer you to the book “Text Mining with R: A Tidy Approach” by Silge and Robinson (2017).

BoW can also be used for image classification in complex scenarios. For example dealing with composed scenes like classrooms, parks, shops, streets, etc. First, the scene

![](bbox=[0.085, 0.633, 0.915, 0.873])

Figure 7.13: Conceptual view of two documents as BoW.