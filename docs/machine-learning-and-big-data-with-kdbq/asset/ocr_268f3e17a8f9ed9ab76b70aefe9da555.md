# CHAPTER 27

# Processing Information

We have so far solely on numerical time series and devoted most of our time to analysing numbers. Recently, however, processing of non-numerical data, namely written text, has become an essential part of machine learning and data science. In this chapter, we introduce some concepts from the data processing field, which are motivated by how search engines assign importance to documents.

# 27.1 INFORMATION RETRIEVAL

The first method we review is from the information retrieval toolbox. The motivation is as follows. We have a set of basic building blocks, words, and a document composed of a subset of words. We want to assign a measure for the word how important it is for a given document. Since some words are more frequent than others, the natural frequency of words within the entire corpus of all has to be taken into account, and the measure has to be corrected for it.

Imagine we have a document, and we want to understand whether its content is relevant for a reader or not. The relevancy means that it is not just "another" permutation of words, but it contains unique words. Let us stress that we base our analysis on the uniqueness of words and not how they are structured within a sentence. Such an idea, if expressed using common words, cannot be captured with analytics we are building now and is beyond the aim of this book.

In this section, we first discuss the corpus we use for examples and two approaches for information retrieval: intuitive frequency counting and tf-idf method.

# 27.1.1 Corpus: Leonardo da Vinci

In order to illustrate the concept of information retrieval, we need a sample text. We will use a text by Leonardo da Vinci Thoughts on Art and Life, translated in 1906. We have accessed the text using Project Gutenberg; daV. We focus on the third section titled "Thoughts on Science". We exclude side notes and page numbers. The text is stored on the local drive in a text file.

We filter the text as follows. We read the text into memory:

```
daVinci:"vs" sv read0 "C:\daVinciThoughtsOnArtAndLife_ChapterScience.txt"
```

523

Machine Learning and Big Data with kdb+/q, First Edition. Jan Novnoty, Paul A. Bilikon, Ari Galios and Frédéric Delèze.
© 2020 Jan Novnoty, Paul A. Bilikon, Ari Galios and Frédéric Delèze. Published 2020 by John Wiley & Sons, Ltd.