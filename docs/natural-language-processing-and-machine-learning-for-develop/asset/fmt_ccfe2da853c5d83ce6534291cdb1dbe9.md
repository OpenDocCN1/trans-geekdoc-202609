
## A Brief Comparison of Popular Python-Based NLP Libraries

This section contains information that you have seen in earlier sections and chapters, which is provided in a consolidated manner for your convenience.

Natural language toolkit `NLTK` is used for such tasks as tokenization, lemmatization, stemming, parsing, POS tagging, and so on. This library has tools for almost all NLP tasks.

`SpaCy` is the main competitor of the `NLTK`. These two libraries can be used for the same tasks.

`Gensim` is the package for topic and vector space modeling, document similarity.

`Sklearn` provides a large library for machine learning. The tools for text preprocessing are also presented here.

The general mission of the `Pattern` library is to serve as the Web mining module. So, it supports NLP only as a side task.

`Polyglot` is yet another Python package for NLP. It is not very popular but also can be used for a wide range of the NLP tasks.

## Miscellaneous Libraries

This section contains task-specific libraries that can be used in NLP as well as non-NLP projects.

*[https://www.kdnuggets.com/2020/04/five-cool-python-libraries-data-science.html](https://www.kdnuggets.com/2020/04/five-cool-python-libraries-data-science.html)* 1\. `numerizer`

*[https://github.com/jaidevd/numerizer](https://github.com/jaidevd/numerizer)*

This library converts text numerics into int and float, and is installed via:

pip3 install `numerizer` 

A simple example is shown here:

from `numerizer` import `numerize` print(`numerize`('Eight fifty million')) print(`numerize`('one two three')) print(`numerize`('Fifteen hundred')) print(`numerize`('Three hundred and Forty five')) print(`numerize`('Six and one quarter')) print(`numerize`('Jack is having fifty million')) print(`numerize`('Three hundred billion')) 

2\. `missingno`

This library provides a way to visualize missing values from an Excel spreadsheet, and is installed via:

pip3 install `missingno` 

A simple example is shown here:

import pandas as pd import `missingno` as mi   \# reading the dummy dataset data = pd.read\_excel("dummy.xlsx")   \# checking missing values data.isnull().sum()   #Visualizing using missingno print("Visualizing missing value using bar graph") mi.bar(data, figsize = (10,5)) print("Visualizing missing value using matrix") mi.matrix(data, figsize = (10,5)) 

3\. `Faker`

This library generates various types of test data, and is installed via:

pip3 install `faker` 

A simple example is shown here:

\# Generating fake email print (`fake.email()`) \# Generating fake country name print(`fake.country()`) \# Generating fake name print(`fake.name()`) \# Generating fake text print(`fake.text()`) \# Generating fake lat and lon print(`fake.latitude()`, fake.longitude()) \# Generating fake url print(`fake.url()`) \# Generating fake profile print(`fake.profile()`) \# Generating random number print(`fake.random\_number()`) 

4\. `EMOT`

This library can collect emojis (small images) and emoticons (keyboard-based characters), and then perform a sentiment-like analysis. Install this library via this command:

pip3 install `emot` 

A simple example is shown here:

import re   \# Function for converting emojis into word from emot.emo\_unicode import UNICODE\_EMO, EMOTICONS   def convert\_emojis(text):   for emot in UNICODE\_EMO:     text = text.replace(emot, "\_".join(UNICODE\_EMO\[emot\].replace(",","").replace(":","").split()))   return text# Example   text1 = "Awesome ☐üòÇ. The exhilaration from successfully completing my project ☐üòé, The euphoria is wonderfuls ☐üòí" convert\_emojis(text1) 

5\. `Chartify`

`Chartify` is a user-friendly visualization library for charts, and is installed via:

pip3 install `chartify`   A simple example is shown here: import numpy as np import pandas as pd import `chartify`   #loading example dataset from `chartify` data = `chartify`.examples.example\_data() data.head()   \# Calculating total quantity for each fruits quantity\_by\_fruit = (data.groupby('fruit')\['quantity'\].sum().reset\_index()) ch = `chartify`.Chart(blank\_labels=True, x\_axis\_type='categorical') ch.set\_title("Vertical bar plot.") ch.set\_subtitle("Automatically sorts by value counts.")   ch.plot.bar(  data\_frame=quantity\_by\_fruit,  categorical\_columns='fruit',  numeric\_column='quantity') ch.show() 

## Summary

This chapter introduced you to `NLTK`, along with code samples of using `NLTK` with `lxml`, XPath, stemmers, lemmatization, and stop words. Then you learned about some of the features of Wordnet, such as finding synonyms and antonyms of words. You also learned about `NLTK` with POS (parts of speech), along with various tokenizers.

Next you learned how define a grammar in `NLTK` and determine whether or not a given sentence can be parsed with that grammar. Finally, you learned about `gensim` and its core concepts, with code samples that illustrate how to calculate tf-idf values in `gensim`, and how to save a word2vec model in `gensim`.

# CHAPTER 7

# INTRODUCTION TO MACHINE LEARNING

This chapter introduces numerous concepts in machine learning, such as feature selection, feature engineering, data cleaning, training sets, and test sets.

The first part of this chapter briefly discusses machine learning and the sequence of steps that are typically required in order to prepare a dataset. These steps include “feature selection” or “feature extraction” that can be performed using various algorithms.

The second section describes the types of data that you can encounter, issues that can arise with the data in datasets, and how to rectify them. You will also learn about the difference between “hold out” and “k-fold” when you perform the training step.

The third part of this chapter briefly discusses the basic concepts involved in linear regression. Although linear regression was developed more than 200 years ago, this technique is still one of the “core” techniques for solving (albeit simple) problems in Statistics and machine learning. In fact, the technique known as “mean squared error” (MSE) for finding a best-fitting line for data points in a 2D plane (or a hyperplane for higher dimensions) is implemented in Python and TensorFlow in order to minimize so-called “loss” functions.

The fourth section in this chapter contains additional code samples involving linear regression tasks using standard techniques in NumPy. Hence, if you are comfortable with this topic, you can probably skim quickly through the first two sections of this chapter. This section shows you how to solve linear regression using Keras.

One point to keep in mind is that some algorithms are mentioned without delving into details about them. For instance, the section pertaining to supervised learning contains a list of algorithms that appear later in the chapter in the section that pertains to classification algorithms. The algorithms that are displayed in bold in a list are the algorithms that are of greater interest for this book. In some cases the algorithms are discussed in greater detail in the next chapter; otherwise, you can perform an online search for additional information about the algorithms that are not discussed in detail in this book.

## What is Machine Learning?

In high-level terms, machine learning is a subset of AI that can solve tasks that are infeasible or too cumbersome with traditional programming languages. A spam filter for email is an early example of machine learning. Machine learning generally supersedes the accuracy of older algorithms.
