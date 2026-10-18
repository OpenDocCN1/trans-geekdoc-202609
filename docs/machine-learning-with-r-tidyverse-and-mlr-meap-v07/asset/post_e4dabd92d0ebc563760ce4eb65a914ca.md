
Specifically on machine learning in R? There are modern tools in R designed specifically to make data science tasks simple and human-readable, such as those from the tidyverse (we’ll cover these tools in depth in Chapter 2).

Traditionally, machine learning algorithms in R were scattered across multiple packages, written by different authors. This meant you would need to learn to use new functions with different arguments and implementations, each time you wanted to apply a new algorithm. Proponents of Python could use this as an example of why it was better suited for machine learning, as it has the well-known scikit-learn package which has a plethora of machine learning algorithms built into it. But R has now followed suit, with the caret and mlr packages. While quite similar in purpose and functionality to caret, I believe mlr to be more flexible and intuitive, and so we’ll be using mlr throughout the book.

The mlr package (which stands for machine learning in R) provides an interface for a large number of machine learning algorithms, and allows you to perform extremely complicated machine learning tasks with very little coding. Where possible, we will use the mlr package throughout this book so that, when you’re finished, you’ll be proficient at using one of the most modern machine learning packages available.

### 1.4 Which datasets will we use?

To make your learning process as fun and interesting as possible, we will use real datasets in our machine learning pipelines. R comes with a considerable number of built-in datasets that are supplemented by datasets that come with packages we’ll be loading into our R sessions. I decided to use datasets that come with R or its packages, to make it easier for you to work through the book while offline.

We’ll be using these datasets to help us build our machine learning models and compare how different models perform on different types of data.

> With so many datasets to choose from, after completing each chapter I suggest you apply what you’ve learned to a different dataset.

### 1.5 What will you learn in this book?

This book gives you a hands-on introduction to machine learning with R. To benefit from the book, you should be comfortable with basic R coding, such as loading packages, and working with objects and data structures. You will learn:

- How to use, organize, tidy and plot your data using the tidyverse
- Critical concepts such as overfitting, underfitting, and bias-variance trade-off
- To apply several machine learning algorithms from each of the four classes (classification, regression, dimension reduction, and clustering)
- How to validate model performance and prevent overfitting
- How to compare multiple models to decide on the best

Throughout the book we’ll use fun and interesting examples to learn concepts, and to apply our knowledge to. When possible, we will also apply multiple algorithms to the same dataset so you get a feel for how different algorithms perform under certain situations.

### 1.6 Summary

- Artificial intelligence is the appearance of intelligent behavior by a computer process
- Machine learning is a subfield of artificial intelligence, where the computer learns relationships in data to make predictions on future, unseen data, or to identify meaningful patterns that help us understand our data better
- A machine learning algorithm is the process by which patterns and rules in the data are learned, and the model is the collection of those patterns and rules which accepts new data, applies the rules to it, and outputs an answer
- Deep learning is a subfield of machine learning, which is, itself, a subfield of artificial intelligence
- Machine learning algorithms are categorized as supervised and unsupervised, depending on whether they learn from ground-truth-labeled data (supervised learning) or unlabeled data (unsupervised learning)
- Supervised learning algorithms are divided into classification (if they predict a categorical variable) or regression (if they predict a continuous variable)
- Unsupervised learning algorithms are divided into dimension reduction (if they find a lower-dimensional representation of the data) or clustering (if they identify clusters of cases in the data)
- Along with Python, R is a popular data science language and contains many tools and built-in data that simplify the process of learning data science and machine learning

## Tidying, manipulating and plotting data with the tidyverse

- What the tidyverse is
- What is meant by tidy data
- How to install and load the tidyverse
- How to use the tibble, dplyr, ggplot2, tidyr, and purrr packages of the tidyverse

I'm really excited to start teaching machine learning to you. But before we dive into that, I want to teach you some skills that are going to make your learning experience simpler and more effective. These skills are also going to improve your general data science and R programming skills.

Imagine I asked you to build me a car (a typical request between friends). You could go old-fashioned: you could purchase the metal, glass and all the components, hand cut all the pieces, hammer them into shape and rivet them together. The car may look beautiful and work perfectly, but it would take a very long time, and would be hard for you to remember exactly what you did if you had to make another one.

Instead, you could use a modern approach using robotic arms in your factory. You could program them to cut and bend the pieces to their pre-defined shapes, and have them assemble the pieces for you. In this scenario, building a car would be much faster and simpler for you, and would be easy for you to reproduce the same process in future.

Now imagine I make a more reasonable request of you and ask you to reorganize and plot a dataset, ready for passing it through a machine learning pipeline. You could use base R functions for this, and they would work fine. But the code would be long, wouldn't be very human-readable (so in a month you struggle to remember what you did), and the plots would be cumbersome to produce.

### 2.1 What is the tidyverse and what is tidy data?

The purpose of this book is to give you the skills to apply machine learning approaches to your data. While it isn’t my intention to cover all other aspects of data science (nor could I in a single book), I do want to introduce you to the tidyverse. Before you can input your data into a machine learning algorithm, it needs to be in a format that the algorithm is happy to work with.

The tidyverse is an “opinionated collection of R packages designed for data science”, created for the purpose of making data science tasks in R simpler, more human-readable and more reproducible. The packages are “opinionated” because they are designed to make tasks the package authors consider to be good practice easy, and to make tasks they consider to be bad practice difficult. The name comes from the concept of tidy data, a data structure whereby:

- Each row represents a single observation
- Each column represents a variable.

Take a look at the data in Table 2.1. Imagine we take four runners, and put them on a new training regime. We want to know if the regime is improving their running times, so we record their best times just before the new training starts (Month 0), and for three months after.

This is an example of untidy data. Can you see why? Well, let’s go back to our rules. Does each row represent a single observation? Nope. In fact, we have four observations per row (one for each month). Does each column represent a variable? Nope. There are only three variables in this data: the athlete, the month, and the best time, and yet we have 5 columns!

How would the same data look in tidy format? Table 2.2 shows you.

| Athlete | Month 0 | Month 1 | Month 2 | Month 3 |
|---------|---------|---------|---------|---------|
| Joana | 12.50 | 12.1 | 11.98 | 11.99 |
| Debi | 14.86 | 14.9 | 14.70 | 14.30 |
| Sukhveer | 12.10 | 12.1 | 12.00 | 11.80 |
| Kerol | 19.60 | 19.7 | 19.30 | 19.00 |
