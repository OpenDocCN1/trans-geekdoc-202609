![](images/cover.jpg)

![Cover: Supervised Machine Learning for Text Analysis in R, Data Science Series, written by Emil Hvitfeldt, Julia Silge, published by CRC Press, Taylor and Francis Group, Boca Raton, London, New York. CRC Press is an imprint of Taylor and Francis Group, an Informa business, A Chapman & Hall Book.](images/cover.jpg)

First edition published 2022

by CRC Press

6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742

and by CRC Press

2 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

© 2022 Taylor & Francis Group, LLC

CRC Press is an imprint of Taylor & Francis Group, LLC

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](http://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact [mpkbookspermissions@tandf.co.uk](mailto:mpkbookspermissions@tandf.co.uk)

*Trademark notice:* Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

ISBN: 978-0-367-55418-7 (hbk)

ISBN: 978-0-367-55419-4 (pbk)

ISBN: 978-1-003-09345-9 (ebk)

DOI: [10.1201/9781003093459](http://doi.org/10.1201/9781003093459)

Typeset in LMR10 font

by KnowledgeWorks Global Ltd.

In loving memory of my mother-in-law Lisa, who was the first soul to hear about and fully encourage the idea that eventually became this book —E.H.

For Grace, Violet, and Lewis, who (thanks to the pandemic and remote school) had a front row seat to most of my work on this book —J.S.

# *Preface*

Modeling as a statistical practice can encompass a wide variety of activities. This book focuses on *supervised or predictive modeling for text*, using text data to make predictions about the world around us. We use the tidymodels[¹](#fn1)

Supervised machine learning using text data involves building a statistical model to estimate some output from input that includes language. The two types of models we train in this book are regression and classification. Think of regression models as predicting numeric or continuous outputs, such as predicting the year of a United States Supreme Court opinion from the text of that opinion. Think of classification models as predicting outputs that are discrete quantities or class labels, such as predicting whether a GitHub issue is about documentation or not from the text of the issue. Models like these can be used to make predictions for new observations, to understand what features or characteristics contribute to differences in the output, and more. We can evaluate our models using performance metrics to determine which are best, which are acceptable for our specific context, and even which are fair.

Natural language that we as speakers and/or writers use must be dramatically transformed to a machine-readable, numeric representation to be ready for computation. In this book, we explore typical text preprocessing steps from the ground up and consider the effects of these steps. We also show how to fluently use the **textrecipes** R package ([Hvitfeldt, 2020a](#bib.xhtml#refbib_50)) to prepare text data within a modeling pipeline.

[Silge and Robinson (2017)](#bib.xhtml#refbib_105) provides a practical introduction to text mining with R using tidy data principles, based on the **tidytext** package. If you have already started on the path of gaining insight from your text data, a next step is using that text directly in predictive modeling. Text data contains within it latent information that can be used for insight, understanding, and better decision-making, and predictive modeling with text can bring that information and insight to light. If you have already explored how to analyze text as demonstrated in Silge and Robinson (2017), this book will move one step further to show you how to *learn and make predictions* from that text data with supervised models. If you are unfamiliar with this previous work, this book will still provide a robust introduction to how text can be represented in useful ways for modeling and a diverse set of supervised modeling approaches for text.

## **Outline**

The book is divided into three sections. We make a (perhaps arbitrary) distinction between *machine learning methods* and *deep learning methods* by defining deep learning as any kind of multilayer neural network (LSTM, bi-LSTM, CNN) and machine learning as anything else (regularized regression, naive Bayes, SVM, random forest). We make this distinction both because these different methods use separate software packages and modeling infrastructure, and from a pragmatic point of view, it is helpful to split up the chapters this way.

*   **Natural language features:** How do we transform text data into a representation useful for modeling? In these chapters, we explore the most common preprocessing steps for text, when they are helpful, and when they are not.
    
*   **Machine learning methods:** We investigate the power of some of the simpler and more lightweight models in our toolbox.
    
*   **Deep learning methods:** Given more time and resources, we see what is possible once we turn to neural networks.
    

Some of the topics in the second and third sections overlap as they provide different approaches to the same tasks.

Throughout the book, we will demonstrate with examples and build models using a selection of text data sets. A description of these data sets can be found in [Appendix B](#Appendix02.xhtml).

## **Topics this book will not cover**

This book serves as a thorough introduction to prediction and modeling with text, along with detailed practical examples, but there are many areas of natural language processing we do not cover. The *CRAN Task View on Natural Language Processing[²](#fn2)*

*   **Reading text data into memory:** Text data may come to a data practitioner in any of a long list of heterogeneous formats. Text data exists in PDFs, databases, plain text files (single or multiple for a given project), websites, APIs, literal paper, and more. The skills needed to access and sometimes wrangle text data sets so that they are in memory and ready for analysis are so varied and extensive that we cannot hope to cover them in this book. We point readers to R packages such as **readr ([Wickham and Hester, 2020](#bib.xhtml#refbib_111))**, **pdftools ([Ooms, 2020a](#bib.xhtml#refbib_86))**, and **httr (Wickham, 2020)**, which we have found helpful in these tasks.
    
*   **Unsupervised machine learning for text: Silge and Robinson (2017)** provide an introduction to one method of unsupervised text modeling, and [Chapter 5](#06chap_05.xhtml) does dive deep into word embeddings, which learn from the latent structure in text data. However, many more unsupervised machine learning algorithms can be used for the goal of learning about the structure or distribution of text data when there are no outcome or output variables to predict.
    
*   **Text generation:** The deep learning model architectures we discuss in [Chapters 8](#13chap_10.xhtml), [9](#14chap_11.xhtml), and [10](#15chap_12.xhtml) can be used to generate new text, as well as to model existing text. [Chollet and Allaire (2018)](#bib.xhtml#refbib_23) provide details on how to use neural network architectures and training data for text generation.
    
*   **Speech processing:** Models that detect words in audio recordings of speech are typically based on many of the principles outlined in this book, but the training data is *audio* rather than written text. R users can access pre-trained speech-to-text models via large cloud providers, such as Google Cloud's Speech-to-Text API accessible in R through the **googleLanguageR** package ([Edmondson, 2020](#bib.xhtml#refbib_24)).
    
*   **Machine translation:** Machine translation of text between languages, based on either older statistical methods or newer neural network methods, is a complex, involved topic. Today, the most successful and well-known implementations of machine translation are proprietary, because large tech companies have access to both the right expertise and enough data in multiple languages to train successful models for general machine translation. Google is one such example, and Google Cloud's Translation API is again available in R through the **googleLanguageR** package.
    

## **Who is this book for?**

This book is designed to provide practical guidance and directly applicable knowledge for data scientists and analysts who want to integrate text into their modeling pipelines.

We assume that the reader is somewhat familiar with R, predictive modeling concepts for non-text data, and the **tidyverse[³](#fn3)**

We don't assume an extensive background in text analysis, but *Text Mining with R[⁴](#fn4)*

## **Acknowledgments**

We are so thankful for the contributions, help, and perspectives of people who have supported us in this project. There are several we would like to thank in particular.

We would like to thank Max Kuhn and Davis Vaughan for their investment in the **tidymodels** packages, David Robinson for his collaboration on the **tidytext** package, and Yihui Xie for his work on **knitr**, **bookdown**, and the R Markdown ecosystem. Thank you to Desirée De Leon for the site design of the online work and to Sarah Lin for the expert creation of the published work's index. We would also like to thank Carol Haney, Kasia Kulma, David Mimno, Kanishka Misra, and an additional anonymous technical reviewer for their detailed, insightful feedback that substantively improved this book, as well as our editor John Kimmel for his perspective and guidance during the process of writing and publishing.

This book was written in the open, and multiple people contributed via pull requests or issues. Special thanks goes to the four people who contributed via GitHub pull requests (in alphabetical order by username): [@fellennert](mailto:@fellennert), Riva Quiroga ([@rivaquiroga](mailto:@rivaquiroga)), Darrin Speegle ([@speegled](mailto:@speegled)), Tanner Stauss ([@tmstauss](mailto:@tmstauss)).

Note box icons by Smashicons from [flaticon.com](http://flaticon.com).

## **Colophon**

This book was written in RStudio[⁵](#fn5)

This version of the book was built with R version 4.1.0 (2021-05-18) and the following packages:

 
| package || version || source |
| --- | --- | --- |
| bench || 1.1.1 || CRAN (R 4.1.0) |
| bookdown || 0.23 || CRAN (R 4.1.0) |
| broom || 0.7.9 || CRAN (R 4.1.0) |
| corpus || 0.10.2 || CRAN (R 4.1.0) |
| dials || 0.0.9 || CRAN (R 4.1.0) |
| discrim || 0.1.1 || CRAN (R 4.1.0) |
| doParallel || 1.0.16 || CRAN (R 4.1.0) |
| glmnet || 4.1-1 || CRAN (R 4.1.0) |
| gt || 0.3.1 || CRAN (R 4.1.0) |
| hcandersenr || 0.2.0 || CRAN (R 4.1.0) |
| htmltools || 0.5.1.1 || CRAN (R 4.1.0) |
| htmlwidgets || 1.5.3 || CRAN (R 4.1.0) |
| hunspell || 3.0.1 || CRAN (R 4.1.0) |
| irlba || 2.3.3 || CRAN (R 4.1.0) |
| jiebaR || 0.11 || CRAN (R 4.1.0) |
| jsonlite || 1.7.2 || CRAN (R 4.1.0) |
| kableExtra || 1.3.4 || CRAN (R 4.1.0) |
| keras || 2.4.0 || CRAN (R 4.1.0) |
| klaR || 0.6-15 || CRAN (R 4.1.0) |
| LiblineaR || 2.10-12 || CRAN (R 4.1.0) |
| lime || 0.5.2 || CRAN (R 4.1.0) |
| lobstr || 1.1.1 || CRAN (R 4.1.0) |
| naivebayes || 0.9.7 || CRAN (R 4.1.0) |
| parsnip || 0.1.6 || CRAN (R 4.1.0) |
| prismatic || 1.0.0 || CRAN (R 4.1.0) |
| quanteda || 3.1.0 || CRAN (R 4.1.0) |
| ranger || 0.13.1 || CRAN (R 4.1.0) |
| recipes || 0.1.16 || CRAN (R 4.1.0) |
| remotes || 2.4.0 || CRAN (R 4.1.0) |
| reticulate || 1.20 || CRAN (R 4.1.0) |
| rsample || 0.1.0 || CRAN (R 4.1.0) |
| rsparse || 0.4.0 || CRAN (R 4.1.0) |
| scico || 1.2.0 || CRAN (R 4.1.0) |
| scotus || 1.0.0 || Github (EmilHvitfeldt/scotus) |
| servr || 0.23 || CRAN (R 4.1.0) |
| sessioninfo || 1.1.1 || CRAN (R 4.1.0) |
| slider || 0.2.2 || CRAN (R 4.1.0) |
| SnowballC || 0.7.0 || CRAN (R 4.1.0) |
| spacyr || 1.2.1 || CRAN (R 4.1.0) |
| stopwords || 2.2 || CRAN (R 4.1.0) |
| styler || 1.5.1 || CRAN (R 4.1.0) |
| text2vec || 0.6 || CRAN (R 4.1.0) |
| textdata || 0.4.1 || CRAN (R 4.1.0) |
| textfeatures || 0.3.3 || CRAN (R 4.1.0) |
| textrecipes || 0.4.1 || CRAN (R 4.1.0) |
| tfruns || 1.5.0 || CRAN (R 4.1.0) |
| themis || 0.1.4 || CRAN (R 4.1.0) |
| tidymodels || 0.1.3 || CRAN (R 4.1.0) |
| tidytext || 0.3.1 || CRAN (R 4.1.0) |
| tidyverse || 1.3.1 || CRAN (R 4.1.0) |
| tokenizers || 0.2.1 || CRAN (R 4.1.0) |
| tokenizers.bpe || 0.1.0 || CRAN (R 4.1.0) |
| tufte || 0.10 || CRAN (R 4.1.0) |
| tune || 0.1.5 || CRAN (R 4.1.0) |
| UpSetR || 1.4.0 || CRAN (R 4.1.0) |
| vip || 0.3.2 || CRAN (R 4.1.0) |
| widyr || 0.1.4 || CRAN (R 4.1.0) |
| workflows || 0.2.3 || CRAN (R 4.1.0) |
| yardstick || 0.0.8 || CRAN (R 4.1.0) |

# Part I Natural Language Features

# 1Language and modeling

DOI: [10.1201/9781003093459-1](https://doi.org/10.1201/9781003093459-1)

Machine learning and deep learning models for text are executed by computers, but they are designed and created by human beings using language generated by human beings. As natural language processing (NLP) practitioners, we bring our assumptions about what language is and how language works into the task of creating modeling features from natural language and using those features as inputs to statistical models. This is true *even when* we don't think about how language works very deeply or when our understanding is unsophisticated or inaccurate; speaking a language is not the same as having an explicit knowledge of how that language works. We can improve our machine learning models for text by heightening that knowledge.

Throughout the course of this book, we will discuss creating predictors or features from text data, fitting statistical models to those features, and how these tasks are related to language. Data scientists involved in the everyday work of text analysis and text modeling typically don't have formal training in how language works, but there is an entire field focused on exactly that, *linguistics*.

## 1.1 Linguistics for text analysis

[Briscoe (2013)](#bib.xhtml#refbib_18) provides helpful introductions to what linguistics is and how it intersects with the practical computational field of natural language processing. The broad field of linguistics includes subfields focusing on different aspects of language, which are somewhat hierarchical, as shown in [Table 1.1](#02chap_01.xhtml#t1_1).

These fields each study a different level at which language exhibits organization. When we build supervised machine learning models for text data, we use these levels of organization to create *natural language features*, i.e., predictors or inputs for our models. These features often depend on the morphological characteristics of language, such as when text is broken into sequences of characters for a recurrent neural network deep learning model. Sometimes these features depend on the syntactic characteristics of language, such as when models use part-of-speech information. These roughly hierarchical levels of organization are key to the process of transforming unstructured language to a mathematical representation that can be used in modeling.

At the same time, this organization and the rules of language can be ambiguous; our ability to create text features for machine learning is constrained by the very nature of language. Beatrice Santorini, a linguist at the University of Pennsylvania, compiles examples of linguistic ambiguity from news headlines[⁶](#fn6)

*   Include Your Children When Baking Cookies
    
*   March Planned For Next August
    
*   Enraged Cow Injures Farmer with Ax
    
*   Wives Kill Most Spouses In Chicago
    

If you don't have knowledge about what linguists study and what they know about language, these news headlines are just hilarious. To linguists, these are hilarious because they exhibit certain kinds of semantic ambiguity.

Notice also that the first two subfields on this list are about sounds, i.e., speech. Most linguists view speech as primary, and writing down language as text as a technological step.

Written text is typically less creative and further from the primary language than we would wish. This points out how fundamentally limited modeling from written text is. Imagine that the abstract language data we want exists in some high-dimensional latent space; we would like to extract that information using the text somehow, but it just isn't completely possible. Any features we create or model we build are inherently limited.

## 1.2 A glimpse into one area: morphology

How can a deeper knowledge of how language works inform text modeling? Let's focus on **morphology**, the study of words' internal structures and how they are formed, to illustrate this. Words are medium to small in length in English; English has a moderately low ratio of morphemes (the smallest unit of language with meaning) to words while other languages like Turkish and Russian have a higher ratio of morphemes to words ([Bender, 2013](#bib.xhtml#refbib_6)). Related to this, languages can be either more analytic (like Mandarin or modern English, breaking up concepts into separate words) or synthetic (like Hungarian or Swahili, combining concepts into one word).

Morphology focuses on how morphemes such as prefixes, suffixes, and root words come together to form words. Some languages, like Danish, use many compound words. Danish words such as “brandbil” (fire truck), “politibil” (police car), and “lastbil” (truck) all contain the morpheme “bil” (car) and start with prefixes denoting the type of car. Because of these compound words, some nouns seem more descriptive than their English counterpart; “vaskebjørn” (raccoon) splits into the morphemes “vaske” and “bjørn,” literally meaning “washing bear”[⁷](#fn7)

The morphological characteristics of a text data set are deeply connected to preprocessing steps like tokenization ([Chapter 2](#03chap_02.xhtml)), removing stop words ([Chapter 3](#04chap_03.xhtml)), and even stemming ([Chapter 4](#05chap_04.xhtml)). These preprocessing steps for creating natural language features, in turn, can have significant effects on model predictions or interpretation.

## 1.3 Different languages

We believe that most of the readers of this book are probably native English speakers, and certainly most of the text used in training machine learning models is English. However, English is by no means a dominant language globally, especially as a native or first language. As an example close to home for us, of the two authors of this book, one is a native English speaker and one is not. According to the comprehensive and detailed Ethnologue project[⁸](#fn8)

[Bender (2011)](#bib.xhtml#refbib_5) provides guidance to computational linguists building models for text, for any language. One specific point she makes is to name the language being studied.

This idea is simple (acknowledge that the models we build are typically language-specific) but the #BenderRule[⁹](#fn9)

## 1.4 Other ways text can vary

The concept of differences in language is relevant for modeling beyond only the broadest language level (for example, English vs. Danish vs. German vs. Farsi). Language from a specific dialect often cannot be handled well with a model trained on data from the same language but not inclusive of that dialect. One dialect used in the United States is African American Vernacular English (AAVE). Models trained to detect toxic or hate speech are more likely to falsely identify AAVE as hate speech ([Sap et al., 2019](#bib.xhtml#refbib_97)); this is deeply troubling not only because the model is less accurate than it should be, but because it amplifies harm against an already marginalized group.

Language is also changing over time. This is a known characteristic of language; if you notice the evolution of your own language, don't be depressed or angry, because it means that people are using it! Teenage girls are especially effective at language innovation and have been for centuries ([McCulloch, 2015](#bib.xhtml#refbib_77)); innovations spread from groups such as young women to other parts of society. This is another difference that impacts modeling.

Consider two bodies of text, both mostly standard written English, but one made up of tweets and one made up of medical documents. If an NLP practitioner trains a model on the data set of tweets to predict some characteristics of the text, it is very possible (in fact, likely, in our experience) that the model will perform poorly if applied to the data set of medical documents[^(10)](#fn10)

## 1.5 Summary

Linguistics is the study of how language works, and while we don't believe real-world NLP practitioners must be experts in linguistics, learning from such domain experts can improve both the accuracy of our models and our understanding of why they do (or don't!) perform well. Predictive models for text reflect the characteristics of their training data, so differences in language over time, between dialects, and in various cultural contexts can prevent a model trained on one data set from being appropriate for application in another. A large amount of the text modeling literature focuses on English, but English is not a dominant language around the world.

### 1.5.1 In this chapter, you learned:

*   that areas of linguistics focus on topics from sounds to how language is used
    
*   how a topic like morphology is connected to text modeling steps
    
*   to identify the language you are modeling, even if it is English
    
*   about many ways language can vary and how this can impact model results
    

# 2Tokenization

DOI: [10.1201/9781003093459-2](https://doi.org/10.1201/9781003093459-2)

To build features for supervised machine learning from natural language, we need some way of representing raw text as numbers so we can perform computation on them. Typically, one of the first steps in this transformation from natural language to feature, or any of kind of text analysis, is *tokenization*. Knowing what tokenization and tokens are, along with the related concept of an n-gram, is important for almost any natural language processing task.

## 2.1 What is a token?

In R, text is typically represented with the *character* data type, similar to strings in other languages. Let's explore text from fairy tales written by Hans Christian Andersen, available in the **hcandersenr** package ([Hvitfeldt, 2019a](#bib.xhtml#refbib_48)). This package stores text as lines such as those you would read in a book; this is just one way that you may find text data in the wild and does allow us to more easily read the text when doing analysis. If we look at the first paragraph of one story titled “The Fir-Tree,” we find the text of the story is in a character vector: a series of letters, spaces, and punctuation stored as a vector.

![](images/pg9_1.jpg)![](images/pg10_1.jpg)

The first nine lines stores the first paragraph of the story, each line consisting of a series of character symbols. These elements don't contain any metadata or information to tell us which characters are words and which aren't. Identifying these kinds of boundaries between words is where the process of tokenization comes in.

In tokenization, we take an input (a string) and a token type (a meaningful unit of text, such as a word) and split the input into pieces (tokens) that correspond to the type ([Manning, Raghavan, and Schütze 2008](#bib.xhtml#refbib_76)). [Figure 2.1](#03chap_02.xhtml#f2_1) outlines this process.

![FIGURE 2.1: A black box representation of a tokenizer. The text of these three example text fragments has been converted to lowercase and punctuation has been removed before the text is split.](images/fig2_1.jpg)

**FIGURE 2.1:** A black box representation of a tokenizer. The text of these three example text fragments has been converted to lowercase and punctuation has been removed before the text is split.

Most commonly, the meaningful unit or type of token that we want to split text into units of is a **word**. However, it is difficult to clearly define what a word is, for many or even most languages. Many languages, such as Chinese, do not use white space between words at all. Even languages that do use white space, including English, often have particular examples that are ambiguous ([Bender, 2013](#bib.xhtml#refbib_6)). Romance languages like Italian and French use pronouns and negation words that may better be considered prefixes with a space, and English contractions like “didn't” may more accurately be considered two words with no space.

To understand the process of tokenization, let's start with a overly simple definition for a word: any selection of alphanumeric (letters and numbers) symbols. Let's use some regular expressions (or regex for short, see [Appendix A](#Appendix01.xhtml)) with strsplit() to split the first two lines of “The Fir-Tree” by any characters that are not alphanumeric.

![](images/pg11_1.jpg)

At first sight, this result looks pretty decent. However, we have lost all punctuation, which may or may not be helpful for our modeling goal, and the hero of this story ("fir-tree") was split in half. Already it is clear that tokenization is going to be quite complicated. Luckily for us, a lot of work has been invested in this process, and typically it is best to use these existing tools. For example, **tokenizers([Mullen et al., 2018](#bib.xhtml#refbib_83))** and **spaCy ([Honnibal et al., 2020](#bib.xhtml#refbib_43))** implement fast, consistent tokenizers we can use. Let's demonstrate with the **tokenizers** package.

![](images/pg12_1.jpg)

We see sensible single-word results here; the tokenize\_words() function uses the **stringi** package ([Gagolewski, 2020](#bib.xhtml#refbib_35)) and C++ under the hood, making it very fast. Word-level tokenization is done by finding word boundaries according to the specification from the International Components for Unicode (ICU). How does this word boundary algorithm[^(11)](#fn11)

*   Break at the start and end of text, unless the text is empty.
    
*   Do not break within CRLF (new line characters).
    
*   Otherwise, break before and after new lines (including CR and LF).
    
*   Do not break within emoji zwj sequences.
    
*   Keep horizontal whitespace together.
    
*   Ignore Format and Extend characters, except after sot, CR, LF, and new lines.
    
*   Do not break between most letters.
    
*   Do not break letters across certain punctuation.
    
*   Do not break within sequences of digits, or digits adjacent to letters (“3a,” or “A3”).
    
*   Do not break within sequences, such as “3.2” or “3,456.789.”
    
*   Do not break between Katakana.
    
*   Do not break from extenders.
    
*   Do not break within emoji flag sequences.
    
*   Otherwise, break everywhere (including around ideographs).
    

While we might not understand what each and every step in this algorithm is doing, we can appreciate that it is many times more sophisticated than our initial approach of splitting on non-alphanumeric characters. In most of this book, we will use the **tokenizers** package as a baseline tokenizer for reference. Your choice of tokenizer will influence your results, so don't be afraid to experiment with different tokenizers or, if necessary, to write your own to fit your problem.

## 2.2 Types of tokens

Thinking of a token as a word is a useful way to start understanding tokenization, even if it is hard to implement concretely in software. We can generalize the idea of a token beyond only a single word to other units of text. We can tokenize text at a variety of units including:

*   characters,
    
*   words,
    
*   sentences,
    
*   lines,
    
*   paragraphs, and
    
*   n-grams.
    

In the following sections, we will explore how to tokenize text using the **tokenizers** package. These functions take a character vector as the input and return lists of character vectors as output. This same tokenization can also be done using the **tidytext ([Silge and Robinson, 2016](#bib.xhtml#refbib_104))** package, for workflows using tidy data principles where the input and output are both in a dataframe.

![](images/pg14_1.jpg)

The tokenization achieved by using tokenize\_words() on sample\_vector:

![](images/pg14_2.jpg)

will yield the same results as using unnest\_tokens() on sample\_tibble; the only difference is the data structure, and thus how we might use the result moving forward in our analysis.

![](images/pg14_3.jpg)![](images/pg15_1.jpg)

Arguments used in tokenize\_words() can be passed through unnest\_tokens() using the “the dots”[^(12)](#fn12)

![](images/pg15_2.jpg)

### 2.2.1 Character tokens

Perhaps the simplest tokenization is character tokenization, which splits texts into characters. Let's use tokenize\_characters() with its default parameters; this function has arguments to convert to lowercase and to strip all non-alphanumeric characters. These defaults will reduce the number of different tokens that are returned. The tokenize\_\*() functions by default return a list of character vectors, one character vector for each string in the input.

![](images/pg16_1.jpg)

What do we see if we take a look?

![](images/pg16_2.jpg)

We don't have to stick with the defaults. We can keep the punctuation and spaces by setting strip\_non\_alphanum = FALSE, and now we see that spaces and punctuation are included in the results too.

![](images/pg16_3.jpg)![](images/pg17_1.jpg)

The results have more elements because the spaces and punctuation have not been removed.

Depending on the format you have your text data in, it might contain ligatures. Ligatures are when multiple graphemes or letters are combined as a single character The graphemes “f” and “l” are combined into “ﬂ,” or “f” and “f” into “ff.” When we apply normal tokenization rules the ligatures will not be split up.

![](images/pg17_2.jpg)

We might want to have these ligatures separated back into separate characters, but first, we need to consider a couple of things. First, we need to consider if the presence of ligatures is a meaningful feature to the question we are trying to answer. Second, there are two main types of ligatures: stylistic and functional. Stylistic ligatures are when two characters are combined because the spacing between the characters has been deemed unpleasant. Functional ligatures like the German Eszett (also called the scharfes S, meaning sharp s) ß, is an official letter of the German alphabet. It is described as a long S and Z and historically has never gotten an uppercase character. This has led the typesetters to use SZ or SS as a replacement when writing a word in uppercase. Additionally, ß is omitted entirely in German writing in Switzerland and is replaced with ss. Other examples include the “W” in the Latin alphabet (two “v” or two “u” joined together), and æ, ø, and å in the Nordic languages. Some place names for historical reasons use the old spelling “aa” instead of å. In [Section 6.7.1](#09chap_07.xhtml#sec6_7_1) we will discuss text normalization approaches to deal with ligatures.

### 2.2.2 Word tokens

Tokenizing at the word level is perhaps the most common and widely used tokenization. We started our discussion in this chapter with this kind of tokenization, and as we described before, this is the procedure of splitting text into words. To do this, let's use the tokenize\_words() function.

![](images/pg18_1.jpg)

The results show us the input text split into individual words.

![](images/pg18_2.jpg)

We have already seen lowercase = TRUE, and strip\_punct = TRUE and strip\_numeric = FALSE control whether we remove punctuation and numeric characters, respectively. We also have stopwords = NULL, which we will talk about in more depth in [Chapter 3](#04chap_03.xhtml).

Let's create a tibble with two fairy tales, “The Fir-Tree” and “The Little Mermaid.” Then we can use unnest\_tokens() together with some **dplyr** verbs to find the most commonly used words in each.

![](images/pg18_3.jpg)![](images/pg19_1.jpg)

The five most common words in each fairy tale are fairly uninformative, with the exception being "tree" in the “The Fir-Tree.”

### 2.2.3 Tokenizing by n-grams

An n-gram (sometimes written “ngram”) is a term in linguistics for a contiguous sequence of *n* items from a given sequence of text or speech. The item can be phonemes, syllables, letters, or words depending on the application, but when most people talk about n-grams, they mean a group of *n* words. In this book, we will use n-gram to denote word n-grams unless otherwise stated.

Some example n-grams are:

*   **unigram:** “Hello,” “day,” “my,” “little”
    
*   **bigram:** “fir tree,” “fresh air,” “to be,” “Robin Hood”
    
*   **trigram:** “You and I,” “please let go,” “no time like,” “the little mermaid”
    

The benefit of using n-grams compared to words is that n-grams capture word order that would otherwise be lost. Similarly, when we use character n-grams, we can model the beginning and end of words, because a space will be located at the end of an n-gram for the end of a word and at the beginning of an n-gram of the beginning of a word.

To split text into word n-grams, we can use the function tokenize\_ngrams(). It has a few more arguments, so let's go over them one by one.

![](images/pg20_1.jpg)

We have seen the arguments lowercase, stopwords, and simplify before; they work the same as for the other tokenizers. We also have n, the argument to determine which degree of n-gram to return. Using n = 1 returns unigrams, n = 2 bigrams, n = 3 gives trigrams, and so on. Related to n is the n\_min argument, which specifies the minimum number of n-grams to include. By default both n and n\_min are set to 3 making tokenize\_ngrams() return only trigrams. By setting n = 3 and n\_min = 1, we will get all unigrams, bigrams, and trigrams of a text. Lastly, we have the ngram\_delim argument, which specifies the separator between words in the n-grams; notice that this defaults to a space.

Let's look at the result of n-gram tokenization for the first line of “The Fir-Tree.”

![](images/pg20_2.jpg)

Notice how the words in the trigrams overlap so that the word “down” appears in the middle of the first trigram and beginning of the second trigram. N-gram tokenization slides along the text to create overlapping sets of tokens.

It is important to choose the right value for n when using n-grams for the question we want to answer. Using unigrams is faster and more efficient, but we don't capture information about word order. Using a higher value for n keeps more information, but the vector space of tokens increases dramatically, corresponding to a reduction in token counts. A sensible starting point in most cases is three. However, if you don't have a large vocabulary in your data set, consider starting at two instead of three and experimenting from there. [Figure 2.2](#03chap_02.xhtml#f2_2) demonstrates how token frequency starts to decrease dramatically for trigrams and higher-order n-grams.

![FIGURE 2.2: Using longer n-grams results in a higher number of unique tokens with fewer counts. Note that the color maps to counts on a logarithmic scale.](images/fig2_2.jpg)

**FIGURE 2.2:** Using longer n-grams results in a higher number of unique tokens with fewer counts. Note that the color maps to counts on a logarithmic scale.

We are not limited to use only one degree of n-grams. We can, for example, combine unigrams and bigrams in an analysis or model. Getting multiple degrees of n-grams is a little different depending on what package you are using; using tokenize\_ngrams() you can specify n and n\_min.

![](images/pg21_1.jpg)![](images/pg22_1.jpg)

Combining different degrees of n-grams can allow you to extract different levels of detail from text data. Unigrams tell you which individual words have been used a lot of times; some of these words could be overlooked in bigram or trigram counts if they don't co-appear with other words often. Consider a scenario where every time the word “dog” was used it came after an adjective: “happy dog,” “sad dog,” “brown dog,” “white dog,” “playful dog,” etc. If this is fairly consistent and the adjectives varied enough, then bigrams would not be able to detect that this story is about dogs. Similarly “very happy” and “not happy” will be recognized as different from bigrams and not with unigrams alone.

### 2.2.4 Lines, sentence, and paragraph tokens

Tokenizers to split text into larger units of text like lines, sentences, and paragraphs are rarely used directly for modeling purposes, as the tokens produced tend to be fairly unique. It is very uncommon for multiple sentences in a text to be identical! However, these tokenizers are useful for preprocessing and labeling.

For example, Jane Austen's novel *Northanger Abbey* (as available in the **janeaustenr** package) is already preprocessed with each line being at most 80 characters long. However, it might be useful to split the data into chapters and paragraphs instead.

Let's create a function that takes a dataframe containing a variable called text and turns it into a dataframe where the text is transformed into paragraphs. First, we can collapse the text into one long string using collapse = ”\\ n” to denote line breaks, and then next we can use tokenize\_paragraphs() to identify the paragraphs and put them back into a dataframe. We can add a paragraph count with row\_number().

![](images/pg22_2.jpg)

Now we take the raw text data and add the chapter count by detecting when the characters "CHAPTER" appears at the beginning of a line. Then we nest() the text column, apply our add\_paragraphs() function, and then unnest() again.

![](images/pg23_1.jpg)

Now we have 1020 separate paragraphs we can analyze. Similarly, we could go a step further to split these chapters into sentences, lines, or words.

It can be useful to be able to reshape text data to get a different observational unit. As an example, if you wanted to build a sentiment classifier that would classify sentences as hostile or not, then you need to work with and train your model on sentences of text. Turning pages or paragraphs into sentences is a necessary step in your workflow.

Let us look at how we can turn the\_fir\_tree from a “one line per element” vector to a “one sentence per element.” the\_fir\_tree comes as a vector so we start by using paste() to combine the lines back together. We use a space as the separator, and then we pass it to the tokenize\_sentences() function from the **tokenizers** package, which will perform sentence splitting.

![](images/pg23_2.jpg)![](images/pg24_1.jpg)

If you have lines from different categories as we have in the hcandersen\_en dataframe, which contains all the lines of the fairy tales in English, then we would like to be able to turn these lines into sentences while preserving the book column in the data set. To do this we use nest() and map\_chr() to create a dataframe where each fairy tale is its own element and then we use the unnest\_sentences() function from the tidytext package to split the text into sentences.

![](images/pg24_2.jpg)

Now that we have turned the text into “one sentence per element,” we can analyze on the sentence level.

## 2.3 Where does tokenization break down?

Tokenization will generally be one of the first steps when building a model or any kind of text analysis, so it is important to consider carefully what happens in this step of data preprocessing. As with most software, there is a trade-off between speed and customizability, as demonstrated in [Section 2.6](#03chap_02.xhtml#sec2_6). The fastest tokenization methods give us less control over how it is done.

While the defaults work well in many cases, we encounter situations where we want to impose stricter rules to get better or different tokenized results. Consider the following sentence.

This sentence has several interesting aspects that we need to decide whether to keep or to ignore when tokenizing. The first issue is the contraction in "Don", which presents us with several possible options. The fastest option is to keep this as one word, but it could also be split up into "do" and "n".

The next issue at hand is how to deal with "$1"; the dollar sign is an important part of this sentence as it denotes a kind of currency. We could either remove or keep this punctuation symbol, and if we keep the dollar sign, we can choose between keeping one or two tokens, "$1" or "$" and "1". If we look at the default for tokenize\_words(), we notice that it defaults to removing most punctuation including $.

![](images/pg25_1.jpg)

We can keep the dollar sign if we don't strip punctuation.

![](images/pg25_2.jpg)

When dealing with this sentence, we also need to decide whether to keep the final period as a token or not. If we remove it, we will not be able to locate the last word in a sentence using n-grams.

Information lost to tokenization (especially default tokenization) occurs more frequently in online and more casual text. Multiple spaces, extreme use of exclamation characters, and deliberate use of capitalization can be completely lost depending on our choice of tokenizer and tokenization parameters. At the same time, it is not always worth keeping that kind of information about how text is being used. If we are studying trends in disease epidemics using Twitter data, the style the tweets are written in is likely not nearly as important as what words are used. However, if we are trying to model social groupings, language style and how individuals use language toward each other becomes much more important.

Another thing to consider is the degree of compression each type of tokenization provides. The choice of tokenization results in a different pool of possible tokens and can influence performance. By choosing a method that gives fewer possible tokens you allow later computational tasks to be performed faster. However, that comes with the risk of collapsing together categories of a different meaning. It is also worth noting that the spread of the number of different tokens varies with your choice of tokenizer.

[Figure 2.3](#03chap_02.xhtml#f2_3) illustrates these points. Each of the fairy tales from **hcandersenr** has been tokenized in five different ways and the number of distinct tokens has been plotted along the x-axis (note that the x-axis is logarithmic). We see that the number of distinct tokens decreases if we convert words to lowercase or extract word stems (see [Chapter 4](#05chap_04.xhtml) for more on stemming). Second, notice that the distributions of distinct tokens for character tokenizers are quite narrow; these texts use all or most of the letters in the English alphabet.

![FIGURE 2.3: The number of distinct tokens can vary enormously for different tokenizers](images/fig2_3.jpg)

**FIGURE 2.3:** The number of distinct tokens can vary enormously for different tokenizers

## 2.4 Building your own tokenizer

Sometimes the out-of-the-box tokenizers won't be able to do what you need them to do. In this case, we will have to wield **stringi**/**stringr** and regular expressions (see [Appendix A](#Appendix01.xhtml)).

There are two main approaches to tokenization.

1.  *Split* the string up according to some rule.
    
2.  *Extract* tokens based on some rule.
    

The number and complexity of our rules are determined by our desired outcome. We can reach complex outcomes by chaining together many smaller rules. In this section, we will implement a couple of specialty tokenizers to showcase these techniques.

### 2.4.1 Tokenize to characters, only keeping letters

Here we want to modify what tokenize\_characters() does, such that we only keep letters. There are two main options. We can use tokenize\_characters() and remove anything that is not a letter, or we can extract the letters one by one. Let's try the latter option. This is an **extract** task, and we will use str\_extract\_all() as each string has the possibility of including more than one token. Since we want to extract letters we can use the letters character class \[:alpha:\] to match letters and the quantifier 1 to only extract the first one.

![](images/pg27_1.jpg)![](images/pg28_1.jpg)

We may be tempted to specify the character class as something like \[a-zA-Z\]1. This option would run faster, but we would lose non-English letter characters. This is a design choice we have to make depending on the goals of our specific problem.

![](images/pg28_2.jpg)

### 2.4.2 Allow for hyphenated words

In our examples so far, we have noticed that the string “fir-tree” is typically split into two tokens. Let's explore two different approaches for how to handle this hyphenated word as one token. First, let's split on white space; this is a decent way to identify words in English and some other languages, and it does not split hyphenated words as the hyphen character isn't considered a white-space. Second, let's find a regex to match words with a hyphen and extract those.

Splitting by white space is not too difficult because we can use character classes, as shown in [Table A.2](#Appendix01.xhtml#tblappA_2). We will use the white space character class \[:space:\] to split our sentence.

![](images/pg29_1.jpg)

This worked pretty well. This version doesn't drop punctuation, but we can achieve this by removing punctuation characters at the beginning and end of words.

![](images/pg29_2.jpg)

This regex used to remove the punctuation is a little complicated, so let's discuss it piece by piece.

*   The regex ^\[:punct:\]+ will look at the beginning of the string (^) to match any punctuation characters (\[:punct:\]), where it will select one or more (+).
    
*   The other regex \[:punct:\]+$ will look for punctuation characters (\[:punct:\]) that appear one or more times (+) at the end of the string ($).
    
*   These will alternate (|) so that we get matches from both sides of the words.
    
*   The reason we use the quantifier + is that there are cases where a word is followed by multiple characters we don't want, such as "okay..." and "Really?!!!".
    

We are using map() since str\_split() returns a list, and we want str\_remove\_all() to be applied to each element in the list. (The example here only has one element.)

Now let's see if we can get the same result using extraction. We will start by constructing a regular expression that will capture hyphenated words; our definition here is a word with one hyphen located inside it. Since we want the hyphen to be inside the word, we will need to have a non-zero number of characters on either side of the hyphen.

![](images/pg30_1.jpg)

Wait, this only matched the hyphenated word! This happened because we are only matching words with hyphens. If we add the quantifier ? then we can match 0 or 1 occurrences.

![](images/pg30_2.jpg)

Now we are getting more words, but the ending of "isn" is not there anymore and we lost the word "a". We can get matches for the whole contraction by expanding the character class \[:alpha:\] to include the character . We do that by using \[\[:alpha:\]\].

![](images/pg30_3.jpg)

Next, we need to find out why "a" wasn't matched. If we look at the regular expression, we remember that we imposed the restriction that a non-zero number of characters needed to surround the hyphen to avoid matching words that start or end with a hyphen. This means that the smallest possible pattern matched is two characters long. We can fix this by using an alternation with | . We will keep our previous match on the left-hand side, and include \[:alpha:\]1 on the right-hand side to match the single length words that won't be picked up by the left-hand side. Notice how we aren't using \[\[:alpha:\]\] since we are not interested in matching single characters.

![](images/pg31_1.jpg)

That is getting to be quite a complex regex, but we are now getting the same answer as before.

### 2.4.3 Wrapping it in a function

We have shown how we can use regular expressions to extract the tokens we want, perhaps to use in modeling. So far, the code has been rather unstructured. We would ideally wrap these tasks into functions that can be used the same way tokenize\_words() is used.

Let's start with the example with hyphenated words. To make the function a little more flexible, let's add an option to transform all the output to lowercase.

![](images/pg31_2.jpg)![](images/pg32_1.jpg)

Notice how we transformed to lowercase first because the rest of the operations are case insensitive.

Next let's turn our character n-gram tokenizer into a function, with a variable n argument.

![](images/pg32_2.jpg)

We can use paste0() in this function to construct an actual regex.

## 2.5 Tokenization for non-Latin alphabets

Our discussion of tokenization so far has focused on text where words are separated by white space and punctuation. For such text, even a quite basic tokenizer can give decent results. However, many written languages don't separate words in this way.

One of these languages is Chinese where each “word” can be represented by one or more consecutive characters. Splitting Chinese text into words is called “word segmentation” and is still an active area of research ([Ma, Ganchev, and Weiss 2018](#bib.xhtml#refbib_75); [Huang et al., 2020](#bib.xhtml#refbib_45)).

We are not going to go into depth in this area, but we want to showcase that word segmentation is indeed possible with R as well. We use the **jiebaR** package ([Wenfeng and Yanyi, 2019](#bib.xhtml#refbib_109)). It is conceptually similar to the **tokenizers** package, but we need to create a worker that is passed into segment() along with the string we want to segment.

![](images/pg33_1.jpg)

## 2.6 Tokenization benchmark

Not all tokenization packages are the same. Most open-source tokenizers in R are well-designed, but they are designed to serve different purposes. Some have a multitude of arguments to allow you to customize your tokenizer for greater flexibility, but this flexibility comes at a price; they tend to have relatively slower performance.

While we can't easily quantify flexibility, it is straightforward to benchmark some of the tokenizers available in R so you can pick the one that best suits your needs.

![](images/pg34_1.jpg)![](images/pg35_1.jpg)

The corpus package ([Perry, 2020](#bib.xhtml#refbib_90)) offers excellent performance for tokenization, and other options are not much worse. One exception is using a base R function as a tokenizer; you will see significant performance gains by instead using a package built specifically for text tokenization.

## 2.7 Summary

To build a predictive model, text data needs to be split into meaningful units, called tokens. These tokens range from individual characters to words to n-grams and even more complex structures, and the particular procedure used to identify tokens from text can be important to your results. Fast and consistent tokenizers are available, but understanding how they behave and in what circumstances they work best will set you up for success. It's also possible to build custom tokenizers when necessary. Once text data is tokenized, a common next preprocessing step is to consider how to handle very common words that are not very informative— stop words. [Chapter 3](#04chap_03.xhtml) examines this in detail.

### 2.7.1 In this chapter, you learned:

*   that tokens are meaningful units of text, such as words or n-grams
    
*   to implement different kinds of tokenization, the process of splitting text into tokens
    
*   how different kinds of tokenization affect the distribution of tokens
    
*   how to build your own tokenizer when the fast, consistent tokenizers that are available are not flexible enough
    

# 3Stop words

DOI: [10.1201/9781003093459-3](https://doi.org/10.1201/9781003093459-3)

Once we have split text into tokens, it often becomes clear that not all words carry the same amount of information, if any information at all, for a predictive modeling task. Common words that carry little (or perhaps no) meaningful information are called *stop words*. It is common advice and practice to remove stop words for various NLP tasks, but the task of stop word removal is more nuanced than many resources may lead you to believe. In this chapter, we will investigate what a stop word list is, the differences between them, and the effects of using them in your preprocessing workflow.

The concept of stop words has a long history with Hans Peter Luhn credited with coining the term in 1960 ([Luhn, 1960](#bib.xhtml#refbib_74)). Examples of these words in English are “a,” “the,” “of,” and “didn't.” These words are very common and typically don't add much to the meaning of a text but instead ensure the structure of a sentence is sound.

Historically, one of the main reasons for removing stop words was to decrease the computational time for text mining; it can be regarded as a dimensionality reduction of text data and was commonly-used in search engines to give better results ([Huston and Croft, 2010](#bib.xhtml#refbib_46)).

Stop words can have different roles in a corpus. We generally categorize stop words into three groups: global, subject, and document stop words.

Global stop words are words that are almost always low in meaning in a given language; these are words such as “of” and “and” in English that are needed to glue text together. These words are likely a safe bet for removal, but they are low in number. You can find some global stop words in pre-made stop word lists ([Section 3.1](#04chap_03.xhtml#sec3_1)).

Next up are subject-specific stop words. These words are uninformative for a given subject area. Subjects can be broad like finance and medicine or can be more specific like obituaries, health code violations, and job listings for librarians in Kansas. Words like “bath,” “bedroom,” and “entryway” are generally not considered stop words in English, but they may not provide much information for differentiating suburban house listings and could be subject stop words for certain analysis. You will likely need to manually construct such a stop word list ([Section 3.2](#04chap_03.xhtml#sec3_2)). These kinds of stop words may improve your performance if you have the domain expertise to create a good list.

Lastly, we have document-level stop words. These words do not provide any or much information for a given document. These are difficult to classify and won't be worth the trouble to identify. Even if you can find document stop words, it is not obvious how to incorporate this kind of information in a regression or classification task.

## 3.1 Using premade stop word lists

A quick option for using stop words is to get a list that has already been created. This is appealing because it is not difficult, but be aware that not all lists are created equal. [Nothman, Qin, and Yurchak (2018)](#bib.xhtml#refbib_84) found some alarming results in a study of 52 stop word lists available in open-source software packages. Among some of the more grave issues were misspellings (“fify” instead of “fifty”), the inclusion of clearly informative words such as “computer” and “cry,” and internal inconsistencies, such as including the word “has” but not the word “does.” This is not to say that you should never use a stop word list that has been included in an open-source software project. However, you should always inspect and verify the list you are using, both to make sure it hasn't changed since you used it last, and also to check that it is appropriate for your use case.

There is a broad selection of stop word lists available today. For the purpose of this chapter, we will focus on three of the lists of English stop words provided by the **stopwords** package ([Benoit, Muhr, and Watanabe 2021s](#bib.xhtml#refbib_10)). The first is from the SMART (System for the Mechanical Analysis and Retrieval of Text) Information Retrieval System, an information retrieval system developed at Cornell University in the 1960s ([Lewis et al., 2004](#bib.xhtml#refbib_70)). The second is the English Snowball stop word list ([Porter, 2001](#bib.xhtml#refbib_93)), and the last is the English list from the Stopwords ISO[^(13)](#fn13)

Before we start delving into the content inside the lists, let's take a look at how many words are included in each.

![](images/pg39_1.jpg)

The lengths of these lists are quite different, with the longest list being over seven times longer than the shortest! Let's examine the overlap of the words that appear in the three lists in an UpSet plot in [Figure 3.1](#04chap_03.xhtml#f3_1). An UpSet plot ([Lex et al., 2014](#bib.xhtml#refbib_71)) visualizes intersections and aggregates of intersections of sets using a matrix layout, presenting the number of elements as well as summary statistics.

![FIGURE 3.1: Set intersections for three common stop word lists visualized as an UpSet plot](images/fig3_1.jpg)

**FIGURE 3.1:** Set intersections for three common stop word lists visualized as an UpSet plot

The UpSet plot in Figure 3.1 shows us that these three lists are almost true subsets of each other. The only exception is a set of 10 words that appear in Snowball and ISO but not in the SMART list. What are those words?

![](images/pg39_2.jpg)

All these words are contractions. This is *not* because the SMART lexicon doesn't include contractions; if we look, there are almost 50 of them.

![](images/pg40_1.jpg)

We seem to have stumbled upon an inconsistency: why does SMART include "he" but not "she"? It is hard to say, but this could be worth rectifying before applying these stop word lists to an analysis or model preprocessing. This stop word list was likely generated by selecting the most frequent words across a large corpus of text that had more representation for text about men than women. This is once again a reminder that we should always look carefully at any pre-made word list or another artifact we use to make sure it works well with our needs[^(14)](#fn14)

When you select a stop word list, it is important that you consider its size and breadth. Having a small and concise list of words can moderately reduce your token count while not having too great of an influence on your models, assuming that you picked appropriate words. As the size of your stop word list grows, each word added will have a diminishing positive effect with the increasing risk that a meaningful word has been placed on the list by mistake. In [Section 6.4](#09chap_07.xhtml#sec6_4), we show the effects of different stop word lists on model training.

### 3.1.1 Stop word removal in R

Now that we have seen stop word lists, we can move forward with removing these words. The particular way we remove stop words depends on the shape of our data. If you have your text in a tidy format with one word per row, you can use filter() from **dplyr** with a negated %in% if you have the stop words as a vector, or you can use anti\_join() from **dplyr** if the stop words are in a tibble(). Like in our previous chapter, let's examine the text of “The Fir-Tree” by Hans Christian Andersen, and use **tidytext** to tokenize the text into words.

![](images/pg41_1.jpg)

Let's use the Snowball stop word list as an example. Since the stop words return from this function as a vector, we will use filter().

![](images/pg42_1.jpg)

If we use the get\_stopwords() function from **tidytext** instead, then we can use the anti\_join() function.

![](images/pg42_2.jpg)

The result of these two stop word removals is the same since we used the same stop word list in both cases.

## 3.2 Creating your own stop words list

Another way to get a stop word list is to create one yourself. Let's explore a few different ways to find appropriate words to use. We will use the tokenized data from “The Fir-Tree” as a first example. Let's take the words and rank them by their count or frequency.

![FIGURE 3.2: Words from ”The Fir Tree” ordered by count or frequency](images/fig3_2.jpg)

**FIGURE 3.2:** Words from ”The Fir Tree” ordered by count or frequency

We recognize many of what we would consider stop words in the first column here, with three big exceptions. We see "tree" at 3, "fir" at 12, and "little" at 22. These words appear high on our list, but they do provide valuable information as they all reference the main character. What went wrong with this approach? Creating a stop word list using high-frequency words works best when it is created on a **corpus** of documents, not an individual document. This is because the words found in a single document will be document-specific and the overall pattern of words will not generalize that well.

The word "tree" does seem important as it is about the main character, but it could also be appearing so often that it stops providing any information. Let's try a different approach, extracting high-frequency words from the corpus of *all* English fairy tales by H.C. Andersen.

![FIGURE 3.3: Words in all English fairy tales by Hans Christian Andersen ordered by count or frequency](images/fig3_3.jpg)

**FIGURE 3.3:** Words in all English fairy tales by Hans Christian Andersen ordered by count or frequency

This list is more appropriate for our concept of stop words, and now it is time for us to make some choices. How many do we want to include in our stop word list? Which words should we add and/or remove based on prior information? Selecting the number of words to remove is best done by a case-by-case basis as it can be difficult to determine a priori how many different “meaningless” words appear in a corpus. Our suggestion is to start with a low number like 20 and increase by 10 words until you get to words that are not appropriate as stop words for your analytical purpose.

It is worth keeping in mind that such a list is not perfect. Depending on how your text was generated or processed, strange tokens can surface as possible stop words due to encoding or optical character recognition errors. Further, these results are based on the corpus of documents we have available, which is potentially biased. In our example here, all the fairy tales were written by the same European white man from the early 1800s.

Easy examples are to include the complements to the words in the list if they are not already present. Include “big” if “small” is present, “old” if “young” is present. This example list has words associated with women often listed lower in rank than words associated with men. With "man" being at rank 79 but "woman" at rank 179, choosing a threshold of 100 would lead to only one of these words being included. Depending on how important you think such nouns are going to be in your texts, consider either adding "woman" or deleting "man".[^(15)](#fn15)

[Figure 3.4](#04chap_03.xhtml#f3_4) shows how the words associated with men have a higher rank than the words associated with women. By using a single threshold to create a stop word list, you would likely only include one form of such words.

![FIGURE 3.4: Tokens ranked according to total occurrences, with rank 1 having the most occurrences](images/fig3_4.jpg)

**FIGURE 3.4:** Tokens ranked according to total occurrences, with rank 1 having the most occurrences

Imagine now we would like to create a stop word list that spans multiple different genres, in such a way that the subject-specific stop words don't overlap. For this case, we would like words to be denoted as a stop word only if it is a stop word in all the genres. You could find the words individually in each genre and use the right intersections. However, that approach might take a substantial amount of time.

Below is a bad approach where we try to create a multi-language list of stop words. To accomplish this we calculate the *inverse document frequency[^(16)](#fn16)*

  
$$\\begin{array}{l} {idf(\\text{term}) = \\ln\\left( \\frac{n\_{\\text{documents}}}{n\_{\\text{documents~containing~term}}} \\right)} \\\\ \\end{array}$$  

If the word “dog” appears in 4 out of 100 documents then it would have an idf("dog") = log(100/4) = 3.22, and if the word “cat” appears in 99 out of 100 documents then it would have an idf("cat") = log(100/99) = 0.01. Notice how the idf values goes to zero (as a matter of fact when a term appears in all the documents then the idf of that word is 0 log(100/100) = log(1) = 0), the more documents it is contained in. What happens if we create a stop word list based on words with the lowest IDF? The following function takes a tokenized dataframe and returns a dataframe with a column for each word and a column for the IDF.

![](images/pg46_1.jpg)

Here is the result when we try to create a cross-language list of stop words, by taking each fairy tale as a document. It is not very good!

![FIGURE 3.5: Words from all of H.C. Andersen's fairy tales in Danish, English, French, German, and Spanish, counted and ordered by IDF](images/fig3_5.jpg)

**FIGURE 3.5:** Words from all of H.C. Andersen's fairy tales in Danish, English, French, German, and Spanish, counted and ordered by IDF

![FIGURE 3.6: Words from all of H.C. Andersen's fairy tales in English, counted and ordered by IDF](images/fig3_6.jpg)

**FIGURE 3.6:** Words from all of H.C. Andersen's fairy tales in English, counted and ordered by IDF

This time we get better results. The list starts with “a,” “the,” “and,” and “to” and continues with many more reasonable choices of stop words. We need to look at these results manually to turn this into a list. We need to go as far down in rank as we are comfortable with. You as a data practitioner are in full control of how you want to create the list. If you don't want to include “little” you are still able to add “are” to your list even though it is lower on the list.

## 3.3 All stop word lists are context-specific

Context is important in text modeling, so it is important to ensure that the stop word lexicon you use reflects the word space that you are planning on using it in. One common concern to consider is how pronouns bring information to your text. Pronouns are included in many different stop word lists (although inconsistently), but they will often *not* be noise in text data. Similarly, [Bender et al. (2021)](#bib.xhtml#refbib_8) discuss how a list of about 400 “Dirty, Naughty, Obscene or Otherwise Bad Words” were used to filter and remove text before training a trillion parameter large language model, to protect it from learning offensive language, but the authors point out that in some community contexts, such words are reclaimed or used to describe marginalized identities.

On the other hand, sometimes you will have to add in words yourself, depending on the domain. If you are working with texts for dessert recipes, certain ingredients (sugar, eggs, water) and actions (whisking, baking, stirring) may be frequent enough to pass your stop word threshold, but you may want to keep them as they may be informative. Throwing away “eggs” as a common word would make it harder or downright impossible to determine if certain recipes are vegan or not while whisking and stirring may be fine to remove as distinguishing between recipes that do and don't require a whisk might not be that big of a deal.

## 3.4 What happens when you remove stop words

We have discussed different ways of finding and removing stop words; now let's see what happens once you do remove them. First, let's explore the impact of the number of words that are included in the list. [Figure 3.7](#04chap_03.xhtml#f3_7) shows what percentage of words are removed as a function of the number of words in a text. The different colors represent the three different stop word lists we have considered in this chapter.

![FIGURE 3.7: Proportion of words removed for different stop word lists and different document lengths](images/fig3_7.jpg)

**FIGURE 3.7:** Proportion of words removed for different stop word lists and different document lengths

We notice, as we would predict, that larger stop word lists remove more words than shorter stop word lists. In this example with fairy tales, over half of the words have been removed, with the largest list removing over 80% of the words. We observe that shorter texts have a lower percentage of stop words. Since we are looking at fairy tales, this could be explained by the fact that a story has to be told regardless of the length of the fairy tale, so shorter texts are going to be denser with more informative words.

Another problem you may face is dealing with misspellings.

Handling misspellings when using premade lists can be done by manually adding common misspellings. You could imagine creating all words that are a certain string distance away from the stop words, but we do not recommend this as you would quickly include informative words this way.

One of the downsides of creating your own stop word lists using frequencies is that you are limited to using words that you have already observed. It could happen that “she'd” is included in your training corpus but the word “he'd” did not reach the threshold. This is a case where you need to look at your words and adjust accordingly. Here the large premade stop word lists can serve as inspiration for missing words.

In [Section 6.4](#09chap_07.xhtml#sec6_4), we investigate the influence of removing stop words in the context of modeling. Given the right list of words, we see no harm to the model performance, and sometimes find improvement due to noise reduction ([Feldman, and Sanger 2007](#bib.xhtml#refbib_28)).

## 3.5 Stop words in languages other than English

So far in this chapter, we have focused on English stop words, but English is not representative of every language. The notion of “short” and “long” lists we have used so far are specific to English as a language. You should expect different languages to have a different number of “uninformative” words, and for this number to depend on the morphological richness of a language; lists that contain all possible morphological variants of each stop word could become quite large.

Different languages have different numbers of words in each class of words. An example is how the grammatical case influences the articles used in German. The following tables show the use of definite and indefinite articles in German[^(17)](#fn17)

Building lists of stop words in Chinese has been done both manually and automatically ([Zou, Wang, Deng, Han, and Wang 2006](#bib.xhtml#refbib_114)) but so far none has been accepted as a standard (Zou, Wang, Deng, and Han 2006). A full discussion of stop word identification in Chinese text would be out of scope for this book, so we will just highlight some of the challenges that differentiate it from English.

The main difference from English is the use of logograms instead of letters to convey information. However, Chinese characters should not be confused with Chinese words. The majority of words in modern Chinese are composed of multiple characters. This means that inferring the presence of words is more complicated, and the notion of stop words will affect how this segmentation of characters is done.

## 3.6 Summary

In many standard NLP workflows, the removal of stop words is presented as a default or the correct choice without comment. Although removing stop words can improve the accuracy of your machine learning using text data, choices around such a step are complex. The content of existing stop word lists varies tremendously, and the available strategies for building your own can have subtle to not-so-subtle effects on your model results.

### 3.6.1 In this chapter, you learned:

*   what a stop word is and how to remove stop words from text data
    
*   how different stop word lists can vary
    
*   that the impact of stop word removal is different for different kinds of texts
    
*   about the bias built in to stop word lists and strategies for building such lists
    

# 4Stemming

DOI: [10.1201/9781003093459-4](https://doi.org/10.1201/9781003093459-4)

When we deal with text, often documents contain different versions of one base word, often called a *stem*. “The Fir-Tree,” for example, contains more than one version (i.e., inflected form) of the word "tree".

![](images/pg53_1.jpg)

Trees, we see once again, are important in this story; the singular form appears 76 times and the plural form appears 12 times. (We'll come back to how we might handle the apostrophe in "tree" later in this chapter.)

What if we aren't interested in the difference between "trees" and "tree"and we want to treat both together? That idea is at the heart of *stemming*, the process of identifying the base word (or stem) for a data set of words. Stemming is concerned with the linguistics subfield of morphology, how words are formed. In this example, "trees" would lose its letter "s" while "tree" stays the same. If we counted word frequencies again after stemming, we would find that there are 88 occurrences of the stem "tree" (89, if we also find the stem for "tree").

## 4.1 How to stem text in R

There have been many algorithms built for stemming words over the past half century or so; we'll focus on two approaches. The first is the stemming algorithm of [Porter (1980)](#bib.xhtml#refbib_92), probably the most widely used stemmer for English. Porter himself released the algorithm implemented in the framework Snowball[^(18)](#fn18) ![](images/pg54_1.jpg)

Take a look at those stems. Notice that we do now have 88 incidences of "tree". Also notice that some words don't look like they are spelled as real words; this is normal and expected with this stemming algorithm. The Porter algorithm identifies the stem of both "story" and "stories" as "stori", not a regular English word but instead a special stem object.

Does Porter stemming only work for English? Far from it! We can use the language argument to implement Porter stemming in multiple languages. First we can tokenize the text and nest() into list-columns.

![](images/pg55_1.jpg)

Then we can remove stop words (using get\_stopwords(language = "da") and similar for each language) and stem with the language-specific Porter algorithm. What are the top-20 stems for “The Fir-Tree” in each of these five languages, after removing the Snowball stop words for that language?

![](images/pg55_2.jpg)![](images/pg56_1.jpg)

[Figure 4.1](#05chap_04.xhtml#f4_1) demonstrates some of the challenges in working with languages other than English; the stop word lists may not be even from language to language, and tokenization strategies that work for a language like English may struggle for a language like French with more stop word contractions. Given that, we see here words about little fir trees at the top for all languages, in their stemmed forms.

![FIGURE 4.1: Porter stemming results in five languages](images/fig4_1.jpg)

**FIGURE 4.1:** Porter stemming results in five languages

The Porter stemmer is an algorithm that starts with a word and ends up with a single stem, but that's not the only kind of stemmer out there. Another class of stemmer are dictionary-based stemmers. One such stemmer is the stemming algorithm of the Hunspell[^(19)](#fn19)

![](images/pg56_2.jpg)![](images/pg58_1.jpg)

Notice that the code here is a little different (we had to use unnest()) and that the results are a little different. We have only real English words, and we have more total rows in the result. What happened?

![](images/pg58_2.jpg)

We have *two* stems! This stemmer works differently; it uses both morphological analysis of a word and existing dictionaries to find possible stems. It's possible to end up with more than one, and it's possible for a stem to be a word that is not related by meaning to the original word. For example, one of the stems of “number” is “numb” with this library. The Hunspell library was built to be a spell checker, so depending on your analytical purposes, it may not be an appropriate choice.

## 4.2 Should you use stemming at all?

You will often see stemming as part of NLP pipelines, sometimes without much comment about when it is helpful or not. We encourage you to think of stemming as a preprocessing step in text modeling, one that must be thought through and chosen (or not) with good judgment.

Why does stemming often help, if you are training a machine learning model for text? Stemming *reduces the feature space* of text data. Let's see this in action, with a data set of United States Supreme Court opinions available in the **scotus** package, discussed in more detail in [Section B.2](#Appendix02.xhtml#secB_2). How many words are there, after removing a standard data set of stopwords?

![](images/pg59_1.jpg)

There are 167,879 distinct words in this data set we have created (after removing stopwords) but notice that even in the most common words we see a pair like "state" and "states". A common data structure for modeling, and a helpful mental model for thinking about the sparsity of text data, is a matrix. Let's cast() this tidy data to a sparse matrix, technically, a document-feature matrix object from the **quanteda ([Benoit et al., 2018](#bib.xhtml#refbib_11))** package.

![](images/pg59_2.jpg)

Look at the sparsity of this matrix. It's high! Think of this sparsity as the sparsity of data that we will want to use to build a supervised machine learning model.

What if instead we use stemming as a preprocessing step here?

![](images/pg60_1.jpg)

We reduced the number of word features by many thousands, although the sparsity did not change much. Why is it possibly helpful to reduce the number of features? Common sense says that reducing the number of word features in our data set so dramatically will improve the performance of any machine learning model we train with it, *assuming that we haven't lost any important information by stemming*.

There is a growing body of academic research demonstrating that stemming can be counterproductive for text modeling. For example, [Schofield and Mimno (2016)](#bib.xhtml#refbib_98) and related work explore how choices around stemming and other preprocessing steps don't help and can actually hurt performance when training topic models for text. From Schofield and Mimno (2016) specifically,

Topic modeling is an example of unsupervised machine learning for text and is not the same as the predictive modeling approaches we'll be focusing on in this book, but the lesson remains that stemming may or may not be beneficial for any specific context. As we work through the rest of this chapter and learn more about stemming, consider what information we lose when we stem text in exchange for reducing the number of word features. Stemming can be helpful in some contexts, but typical stemming algorithms are somewhat aggressive and have been built to favor sensitivity (or recall, or the true positive rate) at the expense of specificity (or precision, or the true negative rate).

Most common stemming algorithms you are likely to encounter will successfully reduce words to stems (i.e., not leave extraneous word endings on the words) but at the expense of collapsing some words with dramatic differences in meaning, semantics, use, etc. to the same stems. Examples of the latter are numerous, but some include:

*   meaning and mean
    
*   likely, like, liking
    
*   university and universe
    

In a supervised machine learning context, this affects a model's positive predictive value (precision), or ability to not incorrectly label true negatives as positive. In [Chapter 7](#10chap_08.xhtml), we will train models to predict whether a complaint to the United States Consumer Financial Protection Bureau was about a mortgage or not. Stemming can increase a model's ability to find the positive examples, i.e., the complaints about mortgages. However, if the complaint text is over-stemmed, the resulting model loses its ability to label the negative examples, the complaints *not* about mortgages, correctly.

## 4.3 Understand a stemming algorithm

If stemming is going to be in our NLP toolbox, it's worth sitting down with one approach in detail to understand how it works under the hood. The Porter stemming algorithm is so approachable that we can walk through its outline in less than a page or so. It involves five steps, and the idea of a word **measure**.

Think of any word as made up alternating groups of vowels *V* and consonants *C*. One or more vowels together are one instance of *V*, and one or more consonants togther are one instance of *C*. We can write any word as

  
$$\\begin{array}{l} {\\lbrack C\\rbrack{(VC)}^{m}\\lbrack V\\rbrack} \\\\ \\end{array}$$  

where *m* is called the “measure” of the word. The first *C* and the last *V* in brackets are optional. In this framework, we could write out the word "tree" as

  
$$\\begin{array}{l} {CV} \\\\ \\end{array}$$  

with *C* being “tr” and *V* being “ee”; it's an m = 0 word. We would write out the word "algorithms" as

  
$$\\begin{array}{l} {VCVCVC} \\\\ \\end{array}$$  

and it is an m = 3 word.

*   The first step of the Porter stemmer is (perhaps this seems like cheating) actually made of three substeps working with plural and past participle word endings. In the first substep (1a), “sses” is replaced with “ss,” “ies” is replaced with “i,” and final single “s” letters are removed. The second substep (1b) depends on the measure of the word m but works with endings like “eed,” “ed,” “ing,” adding “e” back on to make endings like “ate,” “ble,” and “ize” when appropriate. The third substep (1c) replaces “y” with “i” for words of a certain m.
    
*   The second step of the Porter stemmer takes the output of the first step and regularizes a set of 20 endings. In this step, “ization” goes to “ize,” “alism” goes to “al,” “aliti” goes to “al” (notice that the ending “i” there came from the first step), and so on for the other 17 endings.
    
*   The third step again processes the output, using a list of seven endings. Here, “ical” and “iciti” both go to “ic,” “ful” and “ness” are both removed, and so forth for the three other endings in this step.
    
*   The fourth step involves a longer list of endings to deal with again (19), and they are all removed. Endings like “ent,” “ism,” “ment,” and more are removed in this step.
    
*   The fifth and final step has two substeps, both which depend on the measure m of the word. In this step, depending on m, final “e” letters are sometimes removed and final double letters are sometimes removed.
    

This algorithm was first published in Porter (1980) and is still broadly used; read [Willett (2006)](#bib.xhtml#refbib_112) for background on how and why it has become a stemming standard. We can reach even *further* back and examine what is considered the first ever published stemming algorithm in [Lovins (1968)](#bib.xhtml#refbib_72). The domain Lovins worked in was engineering, so her approach was particularly suited to technical terms. This algorithm uses much larger lists of word endings, conditions, and rules than the Porter algorithm and, although considered old-fashioned, is actually faster!

# 5Word Embeddings

DOI: [10.1201/9781003093459-5](https://doi.org/10.1201/9781003093459-5)