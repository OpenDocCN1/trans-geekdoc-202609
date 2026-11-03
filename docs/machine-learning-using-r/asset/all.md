![](images/cover.jpg)

<!DOCTYPE html>![Cover Image](images/cover.jpg)

 

Machine Learning Using R

Authors: Kumar Rahul and U. Dinesh Kumar

Published by Wiley India Pvt. Ltd.,

4436/7, Ansari Road, Daryaganj, New Delhi-110002.

Printed at: Yash Printographic

First Edition

ISBN: 978-93-5424-611-1

ISBN: 978-93-5424-859-7 (ebk)

Copyright © 2022 by Wiley India Pvt. Ltd.

Cover Image: © Shutterstock

All rights reserved. No part of this book may be reproduced, stored in a retrieval system, or transmitted in any form or by any means, electronic, mechanical, photocopying, recording or scanning without the written permission of the publisher.

**Limits of Liability:** While the publisher and the authors have used their best efforts in preparing this book, Wiley and the authors make no representation or warranties with respect to the accuracy or completeness of the contents of this book, and specifically disclaim any implied warranties of merchantability or fitness for any particular purpose. There are no warranties which extend beyond the descriptions contained in this paragraph. No warranty may be created or extended by sales representatives or written sales materials.

**Disclaimer:** The contents of this book have been checked for accuracy. Since deviations cannot be precluded entirely, Wiley or its authors cannot guarantee full agreement. As the book is intended for educational purpose, Wiley or its authors shall not be responsible for any errors, omissions or damages arising out of the use of the information contained in the book. This publication is designed to provide accurate and authoritative information with regard to the subject matter covered. It is sold on the understanding that the Publisher is not engaged in rendering professional services.

**Trademarks:** All brand names and product names used in this book are trademarks, registered trademarks or trade names of their respective holders. Wiley is not associated with any product or vendor mentioned in this book.

**Other Wiley Editorial Offices:**

John Wiley & Sons, Inc. 111 River Street, Hoboken, NJ 07030, USA

Wiley-VCH Verlag GmbH, Pappellaee 3, D-69469 Weinheim, Germany

John Wiley & Sons Australia Ltd, 42 McDougall Street, Milton, Queensland 4064, Australia

John Wiley & Sons (Asia) Pte Ltd, 1 Fusionpolis Walk #07-01 Solaris, South Tower Singapore 138628

John Wiley & Sons Canada Ltd, 22 Worcester Road, Etobicoke, Ontario, Canada, M9W ILI

Edition: 2022

[www.wileyindia.com](http://www.wileyindia.com)

To my parents

*Shri Sanjay Kumar Singh and Smt. Tara Singh*

and

my better half

*Ranjita Gupta*.

—Kumar Rahul

To the one who said

*“You, yourself, as much as anybody in the universe,  
deserve your love and affection”*.

—U. Dinesh Kumar

 

 
| 

## Preface

 || 

##  

 |
| --- | --- |

*Accept both compliments and criticism*.  
*It takes both sun and rain for a flower to grow*.

—Zen Proverb

Artificial Intelligence (AI) has emerged as a decisive expertise, with applications across various industry domains. Machine Learning (ML), which is a subset of AI, is an important set of algorithms used for solving several analytics problems. AI and ML are important skills every graduate in Engineering, Science, and Management will require to advance in their career. Companies across industries such as aerospace, e-commerce, banking and finance, healthcare, manufacturing, and retail are planning to build and offer AI-based solutions to stay competitive. These companies will need a large pool of experts in the field of AI and ML to build products and solutions. According to International Data Corporation (IDC), worldwide revenue for AI market in 2021 was US$327.5 billion. The market is expected to break US$500 billion by 2024.[¹](#05_Preface.xhtml#pre-r-fn1) As per Zita (2021), there has been 650% increase in Data Science jobs.[²](#05_Preface.xhtml#pre-r-fn2)

We have been teaching Business Analytics and Machine Learning at the Indian Institute of Management, Bangalore, for MBA students and several other leading corporates in India for many years. This book brings together our experience of more than 20 years working on several ML projects in corporate and academia and our commitment in making ML concepts simpler for students and practitioners.

The objective of this book is to discuss ML model development using R as a software for statistical computing. R is one of the popular languages used by several organizations to analyze a variety of data and build statistical as well as ML models. Several universities and institutions have started undergraduate and postgraduate programs in Business Analytics, and one of the core offerings is skill development in Data Science and Machine Learning. Though Data Science and Machine Learning are flourishing fields in academia and industry, there is a dearth of practical, structured, and quality content. The complexity of ML increases multifold if we use ML techniques to solve real-life business problems. This book is an attempt to create a structured and quality content which applies a few of the Data Science concepts to practical business use cases. This is a practitioner’s book that both students and industry professionals can use to understand and master skills in Machine Learning using R. The concepts and the examples covered in the book will help intermediate and advanced users strengthen know-how of data preparation, feature engineering and algorithms, as well as application of the algorithms on real-life business problems. Though chapters may be read standalone by seasoned practitioners, each chapter builds upon the concepts covered in previous chapters. The beginners in the field of Data Science may benefit if they pay attention to details in each chapter and are ready to spend time to understand the nuances of business use cases, Data Science concept, and detailed understanding of the functions, and packages in R.

For better understanding, we have reproduced many concepts and examples from the book *Business Analytics: The Science of Data-Driven Decision Making* (authored by U. Dinesh Kumar, published by Wiley in 2017). We recommend the readers read this book along with the book by U. Dinesh Kumar (co-author of this book).

Almost all the datasets used in the chapters are taken from the consulting work carried out by us at IIMB. The details of the dataset used can be obtained by registering on: https://www.wileyindia.com/Instructor\_Manuals/Register/login.php

The exercise problems in the chapters may have datasets which are publicly available. Wherever deemed necessary, we have acknowledged the sources of data used to explain the Data Science concepts. We are thankful to the original creators of the datasets.

### Organization of the Book

The book consists of nine chapters. The sequence of the chapters is designed to create a strong foundation for the learners. The first few chapters provide the foundations in R, Statistics, and ML. The later chapters build on the concepts learnt in the previous chapters. The chapters have been written using R 3.5.1 and tested on R 4.0.1. Mostly, the versions of packages used in the chapters will be upward compatible and will work on newer versions of R. However, given that the readers may want to use the code for hands-on experience, each chapter shows the version of the packages used so that the users employ the right version of the packages for code execution. We suggest readers to read the chapters in sequence for a structured learning. A brief description of each chapter is as follows:

• **[Chapter 1](#09_Chapter01.xhtml)** - Machine Learning and R - This chapter discusses concepts such as AI, ML, and deep learning and a framework for building ML models. We discuss why R has been chosen as the language for ML. Also, it provides a quick guide on installation of R, RStudio, Jupyter Notebook, and how to get started with data analysis using these Integrated Development Environments (IDEs).

• **[Chapter 2](#10_Chapter02.xhtml)** - Data Preprocessing - This chapter introduces data.table package, which provides an efficient implementation of reading huge volume of data to create a data. frame as well as syntax for faster querying on the data through binary search. The chapter also introduces basic operations, such as selecting, filtering, grouping, joining, creating new variables, etc., using the syntax of data.table package itself rather than relying on base packages or dplyr package. Though we use the simple dataset, that is, Indian Premier League (IPL) 2011 data to showcase the use of data.table package, we compare the efficiency of read operation of data.table package with the read operation performed using traditional base package on a dataset with 30 million records.

• **[Chapter 3](#11_Chapter03.xhtml)** - Data Visualization - This chapter presents the grammar of graphics, the building block for visualization, which is fundamental to understand the ggplot2 package. The chapter uses the Indian Premier League (IPL) 2011 data to describe the theory behind various statistical charts, such as histogram, distribution plot, scatter plot, box-plot hexagon plot, etc., and how to derive insights from these plots. The chapter briefly introduces a powerful option provided by ggplot2 package to visualize multiple plots with multiple dimensions in a grid view.

• **[Chapter 4](#12_Chapter04.xhtml)** - Probability and Distributions - This chapter provides an overview of probability distributions, such as binomial distribution, normal distribution, exponential distribution, Poisson distribution, and their applications to real-world problems. The chapter uses the stock price data of two companies to deep dive into normal distribution and apply the concepts of normal distribution to gain insights from the stock data. Central limit theorem - the building block for many statistical analysis - is also demonstrated using the publicly available stock price data of a company. We also discuss hypotheses tests, such as *t*\-test, paired *t*\-test and, ANOVA in this chapter.

• **[Chapter 5](#13_Chapter05.xhtml)** - Supervised Learning Algorithm: Linear Regression - In the field of Data Science, regression is one of the important and popular techniques to analyze a wide variety of problems. In this chapter, we discuss the basic concept behind regression and building regression models. We have used the Indian Premier League (IPL) 2011 data to estimate the sold price of the players. The data is a mix of categorical and numeric features. We will learn how to incorporate categorical (qualitative) variables in a regression model. We will understand the usefulness of splitting the data into train set and test set before building the model. We will build stepwise regression using strategies, such as forward selection and backward elimination. While doing so, we will understand Akaike Information Criteria (AIC) for applying the above strategies as well as understand the techniques used for model validation and gauging model usefulness. We will learn about statistical significance using *t*\-test and *F*\-test, regression model diagnostics and perform tasks such as residual analysis, identification of outliers, and influential observations. We will use caret package to build the linear regression and multiple linear regression models.

• **[Chapter 6](#14_Chapter06.xhtml)** - Classification Problems - In this chapter we discuss various classification problems and basic concepts behind the binary logistic regression to solve classification problems. We use **attrition data** from a company and develop binary logistic regression, stepwise logistic regression with forward selection and backward elimination strategy. The chapter also showcases the use of logistic regression for target marketing. We also discuss the concept behind decision tree, cross-validation, and apply it on attrition dataset. We compare the logistic regression and decision tree models and discuss the multi-model approach to reduce features yet maintain model accuracy. We also show the importance of feature engineering and devise several new features from the raw data. The chapter provides in-depth understanding of evaluating the models using metrics derived from confusion matrix, such as Sensitivity, Specificity, *F*\-score, precision, kappa, McNear test, recall, area under ROC curve (AUC), and finding optimal cut-off for model deployment.

• **[Chapter 7](#15_Chapter07.xhtml)** - Advanced Machine Learning - In this chapter we will understand cost function, regularization, and usage of optimization techniques like gradient descent (GD) in ML algorithms. This chapter introduces the bias-variance concept and its trade-off, with an application on a simple yet real dataset. We will learn the concept behind LASSO, Ridge and ElasticNet and apply them on estimating the sold price of players in **Indian Premier League (IPL) 2011**, with cross-validation strategy. Using **attrition data** from an industry, we also show the application of these algorithms to solve a classification problem. The chapter uses caret package which has standardized framework for model development. We also show the usefulness of glmnet package to fine-tune the hyper-parameters of the algorithms discussed in this chapter. We will compare the results of glmnet with that of caret on the same dataset and understand the nuances of building a Lasso, Ridge, and ElasticNet model.

• **[Chapter 8](#16_Chapter08.xhtml)** - Ensemble Methods - This chapter deep dives into the theory and application of advanced models, such as Random Forest, Gradient boosting machine (GBM), and Xtreme boosting in solving **Net Promoter Score (NPS) problem**. It also provides insights into the usage of ensemble techniques such as GBM and Xtreme boosting to solve for regression problems. We will understand the use of state-of-the-art h2o package for model building and hyper-parameter search using grid search techniques. Given that the search space for hyper-parameters of GBM and Xtreme boosting may get complex, we will understand the sequence of steps to follow to fine-tune these models.

• **[Chapter 9](#17_Chapter09.xhtml)** - Text Analytics - Social media data is a messy data to deal with, particularly so if we use Twitter to express our views. The chapter provides details of setting and authenticating account to scrape twitter data. We then deep dive into the **COVID pandemic data** and use text preprocessing steps, such as regular expressions (regex), stop word removal, stemming, and lemmatization for text clean up, Create Bag of Words (BoW) using basic word embeddings like count, TF, and TF-IDF vectorization. We discuss how to visualize unigrams and bigrams to draw insights and extract user sentiments using three predefined lexicons. Next, we explain how to create document term matrix (DTM) and prepare a dataset with a mix of numeric and categorical feature for further modelling needs. We also discuss the use of topic model to extract themes of discussion in COVID data. Along with ggplot2 and dplyr, the chapter mostly uses tidy text package for analysis in this chapter.

### Features of the Book

Several features are incorporated in the book to make learning effective.

Learning Objectives

Learning objectives provide key takeaways and a summary of key concepts that would be discussed in the chapter.

![](images/pagex-01.png)

Important Concepts

This feature points out additional insights for better understanding and other important truths for readers to take note of. It also provides a clear understanding of the concept that is discussed to make readers think about it.

![](images/pagex-02.png)

Useful Tip

With the objective of strengthening the conceptual understanding, this feature aims to help the readers to infer general idea of the concepts described in the chapter.

![](images/pagex-03.png)

Tables

Using the information provided in the tables, readers can load data using the codes provided.

![](images/pagexi-01.png)

RStudio Console

RStudio is an Integrated Development Environment (IDE). It may be intuitively called as an interface and is language agnostic. One can use RStudio to analyze data using R Script, Python Script, etc.

![](images/pagexi-02.png)

Exercises

The Exercises in the book refer to various datasets, using which readers can answer to the questions.

![](images/pagexi-03.png)

### Supplemental Materials

Instructor Resources

The following resources are available for instructors on request. To register, please log on to https://www.wileyindia.com/Instructor\_Manuals/Register/login.php

• Instructor Solution Manuals

• PowerPoint Lecture Slides

• PDF Lecture Slides

• Dataset

• Code

Student Resources

Students can access the following resources via https://www.wileyindia.com/student-resources

• Student Solution Manuals

• R Codes

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#05_Preface.xhtml#pre-fn1)Anon (2021), “*IDC Forecasts Improved Growth for AI Market in 2021*”, Available at https://www.idc.com/getdoc. jsp?containerId=prUS47482321, accessed on 04 September 2021.

[²](#05_Preface.xhtml#pre-fn1)Zita C (2021), “*Is Data Science Still a Rising Career in 2021 - Examining the Demand, Supply and Growth of the Data Science Industry to See if It’s Still a Rising Career in 2021*”, Available at https://towardsdatascience.com/is-data-science-still-a-rising-career-in-2021-722281f7074c, accessed on 04 September 2021.

 

 
| 

## About the Authors

 || 

##  

 |
| --- | --- |

![](images/pagexiii-01.png)

Kumar Rahul is an Engineering graduate from National Institute of Technology, Jaipur, and an alumnus of Indian Institute of Management Bangalore (IIMB). Currently, he is pursuing PhD in Quantitative Methods and Operations Management at Indian Institute of Management, Kozhikode. His professional career spans more than 16 years in the corporate and academic fields. Rahul is passionate about exploring data using a variety of tools and techniques. He has worked with companies like

Satyam Computers, Nokia Siemens, and Deloitte Consulting and has also been a founding member of a few start-ups. He was a founding member of AwesomeStats Consulting, which primarily focuses on training and consulting in the field of Data Science.

For over 7 years, he has been working as a consultant at Data Centre and Analytics Lab, IIMB. He has executed several analytics projects for large corporates. Few of his assignments in the field of Analytics include (a) predicting credit scoring for cooperative banks of Karnataka, renege/attrition issue for an Indian retail company, net promoter score for a reputed medical equipment manufacturer and design issues for a leading U.S. auto manufacturer; (b) forecasting sales and warranty for a leading auto manufacturer; and (c) detecting anomaly for a paper-based consumer products company based out of the U.S. and fraud in earnings management by companies. Several of these projects have been published as case studies by Harvard Business Publishing.

He has taught Analytics in faculty development programs as well as short- and long-duration programs at IIMB. Few of the prominent corporate clients he has worked with are GE-Wipro, Cisco, Deloitte Consulting, United Health Group, HSBC, Flipkart, Fidelity Investments, General Motors, JP Morgan, TVS Motors, Raukten, Hudson Bay, etc.

![](images/pagexiv-01.png)

Dr. U. Dinesh Kumar is a Professor of Decision Sciences at IIM Bangalore and Chairperson of MBA (Business Analytics). He is also the IIMB Chair of Excellence since January 2020. Dr. Dinesh Kumar has over 25 years of teaching and research experience. He has published more than 70 research articles in leading academic journals. Forty of his case studies on Business Analytics based on Indian and multinational organizations have been published at the Harvard Business Publishing’s (HBP) case portal. Nine of his case studies are best sellers at HBP. He has authored four books; his previous book *Business Analytics: The Science of Data-Driven Decision Making*, published by Wiley in 2017, is an Amazon Best Seller. Dr. Dinesh Kumar has carried out predictive and prescriptive analytics consulting projects for organizations, such as The Boston Consulting Group (India) Private Limited, Kimberly Clark, Cartesian Consulting, GE Healthcare, Group One Holding Pvt Ltd, Hindustan Aeronautics Limited, Qatar Airways, Mission Hospital, Manipal Hospitals, Scalene Works, SMNet Serve, TVS Motors, Wipro Limited, UNIBIC and the World Health Organization, etc.

Dr. Dinesh Kumar has conducted training programs on Analytics for several companies, such as Accenture, Aditya Birla Group, Ashok Leyland, Asian Paints, Bank of America, Blue Ocean Market Intelligence, Cisco, Fidelity, Hindustan Aeronautics Limited, Honeywell, Infosys, ITC Info Tech, Madya Pradesh Agency for Promotion of Information Technology (MAPIT), National Academy for Defence Production, Ocwen financial Services, Sony, etc. He conducts corporate training programs in Analytics and has trained more than 1000 professionals in the field of Analytics. He is the founding President of the Analytics Society of India (ASI). Dr. Dinesh Kumar was awarded the Best Young Teacher Award by the Association of Indian Management Institutions in 2003. He was listed as one of the top 10 analytics academics in India by the *Analytics India Magazine* in 2014. He was awarded the Distinguished Professor award in Data Science by the *Analytics India Magazine* in 2021.

 

 
| 

## Acknowledgments

 || 

##  

 |
| --- | --- |

There could not have been a more conducive and vibrant environment than the one provided by IIMB to put the thoughts together in this textbook. The opportunity to interact with some of the brightest minds from academia and industry helped foster thinking which culminated in knitting decades of consulting work in the form of a book.

Writing this book would not have been possible without the support and encouragement of colleagues and friends at IIMB. We are grateful to have received the assistance of Aayushi Kalra, Abirami B, Gowri K P, Naveen Kumar Bhansali, Purvi Tiwary, Pooja Balasubramanya, Sangeetha A, Satyabala Hariharan, Shailaja Grover, Sharada Sringeswara, Sumithra G, and Sunil S during this journey. We acknowledge the effort of Kavita Kumar and Kaushik in proofreading and editing this book. Last but not the least, special thanks to Manaranjan Pradhan for his invaluable guidance while writing the book.

We would like to thank Meenakshi Sehrawat, Associate Publisher (Wiley India), for her quality inputs for the book. Special thanks to Rupnarayan Das, Developmental Editor (Wiley India), for the overall smooth publication of this book.

**Kumar Rahul  
U. Dinesh Kumar**

 

 
| 

## Machine Learning and R

 || 

## 1

 |
| --- | --- |

*Nothing ever exists entirely alone. Everything is in relation to everything else*.

**—Buddha**

LEARNING OBJECTIVES

After reading this chapter, you would be able to:

• Understand the concept of machine learning and various machine learning algorithms.

• Understand how machine learning algorithms are used to solve problems in real world.

• Learn why R programming language has been widely adopted as a platform for building machine learning models?

• Learn how to get started with setting up the R, RStudio, and/or Anaconda platform. Learn basic features of R language to get started with machine learning tasks.

• Learn key libraries in R and their application in analyzing data.

### 1.1 | Introduction to Analytics and Machine Learning

Analytics is a collection of techniques and tools used to create value from data. Techniques include concepts such as Artificial Intelligence (AI), Machine Learning (ML), Statistical Learning (SL), and Deep Learning (DL) algorithms, which are defined as follows:

**Artificial Intelligence:** Algorithms that exhibit human-like intelligence.

**Machine Learning:** Subset of AI that can learn to perform a task such as prediction and classification and improve its performance with additional data and/or models.

**Statistical Learning:** Algorithms that are used for solving problems through statistical inference.

**Deep Learning:** Subset of machine learning that imitates the functioning of human brain to solve problems.

The relationship among AI, ML, and DL can be visualized as shown in **[Figure 1.1](#09_Chapter01.xhtml#fig1.1)**. This structure is not accepted by everyone in the field of analytics. There is one school which believes AI and ML are different (i.e., ML is not a subset of AI), with some overlap. The key point is all of them are algorithms, which are nothing but sets of instructions used to solve business and social problems. The focus of this book is on machine learning algorithms and the use of R platform to generate solutions for ML problems.

![](images/page2-01.png)

Machine learning is a set of algorithms with the capability of learning to perform tasks such as prediction, forecasting, and classification effectively using data. Learning is achieved using additional data and/or additional models. An algorithm can be called a learning algorithm when it improves on a performance metric while performing a task, for example, accuracy of classification such as fraud and customer churn. In the next few sections, we shall discuss various machine learning algorithms and a series of problems solved using ML algorithms.

Machine learning algorithms are classified into the following four categories (Kumar, 2017):

**1.** Supervised Learning Algorithms: These require the knowledge (or value) of both outcome variable (dependent variable) and the features (independent variable or input variables). The algorithm learns (i.e., estimates the value of the model parameters or feature weights) by defining a loss function which is usually a function of the difference between the predicted value using ML and the actual value of the outcome variable. Algorithms such as linear regression, logistic regression, and discriminant analysis are examples of supervised learning algorithms. In the case of multiple linear regression, the regression parameters are estimated by minimizing the sum of squared errors, which is given by ![](images/pageIn_ch1-01.png)where *y*[*i*] is the actual value of the outcome variable and ![](images/pageIn_ch1-02.png)is the predicted value of the outcome variable. The predicted value can be a linear or non-linear function of the features (independent variables) in the data. The prediction is achieved (by estimating feature weights) with the knowledge of the actual value of the outcome variables, thus called supervised learning algorithms. That is, supervision is achieved using the knowledge of outcome variable values in the training data.

**2.** Unsupervised Learning Algorithms: These are set of algorithms which do not have the knowledge of the outcome variable in the data set. The algorithms must find the possible value of the outcome variable. Algorithms such as clustering and principal component analysis are examples of unsupervised learning algorithms. Since the values of outcome variable values are unknown in the training data, supervision using that knowledge is not possible.

**3.** Reinforcement Learning Algorithms: In many data sets, there could be uncertainty around both input as well as output variables. Consider the case of spell check in various text editors. If a person types ‘buutiful’ in Microsoft Word, the spell check will immediately identify this as a spelling mistake and give options such as ‘beautiful’, ‘bountiful’, and ‘dutiful’. The prediction is not one single value, but a set of values with any of them being the correct word (the word the user wanted to use). Spell check and word prediction used for predicting the next word a person is likely to use while messaging using smartphones are good examples of reinforcement learning algorithms, in which there is an uncertainty about both input and output values. Another definition of reinforcement learning algorithm are algorithms that deal with contexts in which the user has to take sequential actions (decisions) to maximize a cumulative reward. Techniques such as Markov chain and Markov decision process are examples of reinforcement learning algorithms.

**4.** Evolutionary Learning Algorithms: Evolutionary algorithms imitate natural evolution to solve a problem. Techniques such as genetic algorithm and ant colony optimization fall under this category.

In this book, we will discuss several supervised and unsupervised learning algorithms and develop models using R.

### 1.2 | Why Machine Learning Algorithms?

Organizations across the world use performance measures such as return on investment (ROI), market share, customer retention, sales growth, customer satisfaction, and so on, for quantifying, monitoring, benchmarking, and improving. They would like to understand the association between key performance indicators (KPIs) and factors that have a significant impact on the KPIs for effective management. Knowledge of the relationship between KPIs and factors would provide the decision maker with appropriate actionable items (Kumar, 2017). Machine learning algorithms can be used to identify factors influencing the KPIs, which can be further used for decision-making and value creation. Organizations such as Amazon, Apple, Capital One, General Electric, Google, IBM, Facebook, Procter and Gamble, and their kind, use ML algorithms to create new products and solutions. Marshall (2016) and MacKenzie et al. (2013) reported that Amazon’s recommender systems resulted in a sales increase of 35%.

A typical ML algorithm employs the following steps (Pradhan and Kumar, 2019):

**1.** Identify the problem or opportunity for value creation.

**2.** Identify sources of data (primary as well as secondary data sources) and create a data lake (integrated set of raw data from different sources).

**3.** Preprocess the data for issues such as missing and incorrect data. Generate derived variables (feature engineering) and prepare the data for ML model building.

**4.** Divide the data sets into subsets of training and validation data sets.

**5.** Build ML models and identify the best model(s) using model performance in validation data.

**6.** Implement solution/decision/develop product.

### 1.3 | Framework for Development of Machine Learning Algorithms

The framework for ML algorithm development can be divided into five integrated stages: problem and opportunity identification, collection of relevant data, data preprocessing, ML model building, and model deployment. The various activities during these stages are denoted in **[Figure 1.2](#09_Chapter01.xhtml#fig1.2)** (Kumar, 2017). The success of ML projects depends on how innovatively data is used compared to the mechanical use of ML tools. Although several routine ML projects such as customer segmentation, clustering, forecasting, and so on, exist, highly successful companies blend innovation with ML algorithms.

In the next few sections, we will discuss R as a software for ML model development, RStudio, and Anaconda Navigator as Integrated development environment (IDE), which eases scripting, and how to get started with R.

### 1.4 | Introduction to R

As per the comprehensive R archive network (CRAN),[¹](#09_Chapter01.xhtml#ch1-r-fn1) *R is an implementation of the S programming language combined with lexical scoping semantics inspired by Scheme (S language). S was created by John Chambers in 1976, while at Bell Labs. Ross Ihaka and Robert Gentleman created R at the University of Auckland, New Zealand. The project was conceived in 1992, an initial version was released in 1995 and a stable beta version in 2000 (Anon 2021). The name R is partly based on the first names of the first two R authors (Robert Gentleman and Ross Ihaka)*.

![](images/page4-01.png)

R is a programming language and open source software platform designed for statistical computing and graphics. It is supported by the R Foundation, a not-for-profit organization established by the R core development team. The R language is used widely among statisticians and machine learning experts to develop machine learning algorithm-based models. Being an interpreted language, R allows for modular programming using functions, and provides flexibility to the users by abstracting details as in typical programming language.[²](#09_Chapter01.xhtml#ch1-r-fn2)

R has more than 12,000 packages suited for almost any kind of statistical or machine learning analysis. The strong user community continuously keeps updating and creating new libraries.

![](images/page5-01.png)

There are packages which can be used to build deep learning models as well. Some of the useful packages for statistical and machine learning are mentioned in **[Table 1.1](#09_Chapter01.xhtml#tab1.1)**.

This list in [Table 1.1](#09_Chapter01.xhtml#tab1.1) is not exhaustive and readers may find other packages useful for data analysis and building machine learning models.

### 1.5 | Popularity Index for R

The Importance of Being Earnest (TIOBE) programming index is an important measure of the acceptance of programming languages. TIOBE index is created and maintained by the TIOBE Company in Eindhoven, the Netherlands. According to TIOBE (Anon, 2021), “*the index is calculated based on the number of search engine results for queries containing the name of the language (****[Table 1.2](#09_Chapter01.xhtml#tab1.2)****)*”. The popularity of a language is to be understood in line of TIOBE’s disclaimer:

![](images/page6-01.png)

**1.** According to the TIOBE website, TIOBE index is “not about the best programming language or the language in which most lines of code have been written”.

**2.** According to TIOBE website, “the index covers searches in Google, Google Blogs, MSN, Yahoo!, Baidu, Wikipedia, and YouTube, and is updated once a month” (Anon, 2021).

**3.** The site claims that the number of web pages resulting from search may reflect the number of skilled engineers, students, courses offered, and job market for the skill worldwide.

From [Table 1.2](#09_Chapter01.xhtml#tab1.2), we can see that Python is the language of choice, at fourth position compared to the 18th position occupied by R. The latest ranking can be found at the TIOBE site.[³](#09_Chapter01.xhtml#ch1-r-fn3) The latest TIOBE index ranking as on August 2020 puts R at the eighth position.[⁴](#09_Chapter01.xhtml#ch1-r-fn4)

The difference in ranking is also due to the fact that Python is a general-purpose programming language which can be used for other software development tasks, whereas R is more suited as a language for statistical computing and machine learning (Pradhan and Kumar, 2019).

A search on the number of job posts on various languages such as SAS, Python, and R, at a popular site,[⁵](#09_Chapter01.xhtml#ch1-r-fn5) reveals the trend in **[Figure 1.3](#09_Chapter01.xhtml#fig1.3)**. It is clear that R still stands as the second-best language for machine learning, with growing demand since 2016.

![](images/page7-01.png)

### 1.6 | R Installations - Getting Started

In this section, we discuss R installations and getting started with R. R is an open-source (free) software environment for statistical analysis and graphics which can be used on operating systems and platforms such as UNIX, Windows, and MacOS. R provides packages to perform several statistical and machine learning models.

Comprehensive R archival network (CRAN) is a repository which hosts the R software as well as thousands of packages which may be needed to perform statistical computing and graphics. The R home page snapshot is depicted in **[Figure 1.4](#09_Chapter01.xhtml#fig1.4)**.

![](images/page7-02.png)

To download R, carry out the following steps:

**1.** Go to [https://cloud.r-project.org](https://cloud.r-project.org)

**2.** Select the link to download based on the operating system of your machine.

**3.** Click the downloaded file and follow the steps to download a compatible version in your machine.

Working on the R software directly may not be a convenient choice and, thus, interactive development environments (IDEs) provide data scientists with an integrated framework for writing and debugging code in an easier way. IDEs are generally language agnostics, which means the same IDE may give data scientists access to write code in any language IDE supports.

### 1.7 | RStudio

Rstudio is one such IDE which makes R programming language easier to use. Rstudio consists of a console, syntax-highlighting editor for direct code execution, as well as tools for graphics, debugging, and workspace management. The current version of Rstudio (Version 1.2.1335) gives the user flexibility to write an R code or a Python code or execute command line script from the same code editor.

RStudio comes with two options:

**1.** **RStudio desktop version:** This is an open-source edition and provides system to access RStudio locally. It comes with syntax highlighting, code completion, and smart indentation. A few useful features are (*Source*: rstudio.com):

• Ability to execute R code directly from the source editor

• Easy-to-use function definitions

• Convenience of managing multiple working directories using projects

• Integrated R help and documentation

• Interactive and user-friendly debugger to diagnose and fix errors at ease

• Extensive package development tools. This is the version preferred by standalone users to carry out statistical computing.

**2.** **RStudio server version:** This has all the features of the desktop version. It is a commercial license version for organizations not able to use the open-source license version due to internal policies. It provides priority email support and eight-hour response during business hours.

To download RStudio, carry out the following steps:

**1.** Go to [https://www.rstudio.com/products/RStudio](https://www.rstudio.com/products/RStudio)/. The snapshot of RStudio homepage is depicted in **[Figure 1.5](#09_Chapter01.xhtml#fig1.5)**.

**2.** Click the link to download the RStudio desktop version.

**3.** In the subsequent page, click the link to download free desktop version compatible with the operating system of your machine.

**4.** Click the downloaded file and follow the steps to install the compatible version in your machine.

Look for version compatibility between RStudio and R software. Step 3 of the download ‘RStudio’ will mention which version of R needs to be pre-installed before attempting to download RStudio.[⁶](#09_Chapter01.xhtml#ch1-r-fn6)

More information on RStudio can be found at [http://docs.rstudio.com/ide/server-pro](http://docs.rstudio.com/ide/server-pro)/.

![](images/page9-01.png)

### 1.8 | Understanding RStudio IDE

**[Figure 1.6](#09_Chapter01.xhtml#fig1.6)** highlights four main blocks of RStudio:

**1.** Editor

**2.** Console

**3.** Environment manager

![](images/page9-02.png)

**4.** Content viewer

• Files

• Plots

• Packages

• Help

• Viewer

**5.** **Editor** block is used to write R Script. The script can be saved in the directory and opened at a later point for execution. Writing a script in editor does not mean the script is executed. The **Run** command above the script editor can be used to execute an R script.

**6.** **Console** is used to see the outcome of the executed script. Any bug/warning while executing the script also appears in the console. It can be used for writing a few R commands to see the immediate result, or to perform basic code debugging.

You can check the version of R installed in your machine with the following command on console:

![](images/page10-01.png)

This code in this book has been written on R version 3.5.1. You can check the version of specific package, say stats, installed in your R session with the following command on console:

![](images/page10-02.png)

The package version of ‘stats’ is the same as software R. This implies that stats is a base package and gets installed during the installation of R software. We can use sessionInfo() in console to get information about the base packages.

![](images/page10-03.png)![](images/page11-01.png)

The functions within attached base packages, that is, stats, graphics, grDevices, utils, datasets, methods, base can be accessed without explicitly loading these packages. This means the user does not have to explicitly give the command library(stats) or in general library (<package-name>) to use the functions defined in these packages.

By default, base packages are attached in the search path, and thus functions within these packages can be used without invoking these packages. We can type search() in console to know the packages attached in the search path.

![](images/page11-02.png)

From the above output of the search() function, we can see that there are 9 elements in the search path. When a user types a function name or command in the RStudio console, R looks for the same in the global name space, that is, .GlobalEnv. If the function is not found in the .GlobalEnv, then successive elements of search(), that is, “package::stats”, “package::graphics”, etc. are scanned to look for the function definition. If the function/ command is not found in the entire search space, R displays an error message.

RStudio is an Integrated Development Environment (IDE). It may be intuitively called as an interface, and is language agnostic. One can use RStudio to analyze data using R Script, Python Script, etc.

Packages which are not loaded explicitly in the R session can be invoked with the command library(<package-name>). This command prompts R to load the package in memory and attach it in search() path. Ensure that a specific package is installed in your machine before trying to invoke it.

It may be noticed that the search path does not list packages shown as *loaded via a namespace (and not attached)* with the command sessionInfo(). It implies that these packages are loaded in memory but are not attached to search path. So, R software and the base packages can access the functions defined within these packages, but they are not available for users to access.

The user can access the functions of packages loaded via namespace by using <pgk-name>::<function-name>. For example, if we want to access package\_dependencies functions of tools package to check the dependency of package stats on any other package:

![](images/page11-03.png)![](images/page12-01.png)

The output is ‘NULL’, which implies that package stats do not depend on other packages.

**1.** Global environment shows the objects loaded or created in memory while working on any data analysis project. These objects can be termed global variables, and are listed as ‘Data‘, ‘Functions‘, or ‘Values‘ in global environment.

• Data refers to objects created while reading data files from any file format. The objects are created as a data.frame, data.table, tibble, etc.

• Functions refers to objects created as a user-defined function.

• Values refers to objects that are primitive as well as complex data types like int, float, list, matrices, etc.

Installation of R software is a must before using RStudio for writing and executing R Script.

**[Figure 1.7](#09_Chapter01.xhtml#fig1.7)** depicts the global environment which shows ‘Data’ and ‘Values’ snapshot. When we assign a value to a variable ‘age‘ (age = 20) or read a comma-separated value (csv) file from the system (read\_csv= read.csv(<file-name>), the variables age (listed as values), read\_csv (listed as data) are created in global environment.

Environments in R have a deeper meaning as well. Say, **functions** create their own evaluation environment and the objects created during function call are stored in local environments and not in a global environment. Objects in a global environment are available throughout the R session while objects in the local environment are available only in the local environment created by the functions.

**Content viewer** has five basic sub tabs:

**1.** Files: Lists all the files in the current working directory. As a default, the current working directory is the home directory.

**2.** Plots: All the charts while doing data analysis can be viewed in plots tab.

**3.** Packages: The packages in R can be installed using packages tab. **[Figure 1.8](#09_Chapter01.xhtml#fig1.8)** shows a way to install packages by clicking on the install button in ‘package’ tab. We can think of packages as metadata or dictionary or a collection of predefined functions which contains information about the steps to be performed when a function is called.

Say, when we type read.csv, there must be some way for the R interpreter to understand that this function is meant to read a csv file. The package which contains this definition is ‘utils‘. The ‘utils‘ package has a collection of such functions which identifies the logical action to perform when a function is written in editor. In [Figure 1.8](#09_Chapter01.xhtml#fig1.8), we see that the package tab lists all packages installed on the machine. The packages loaded in the current session will have a check mark on the corresponding boxes. installed.packages() command in console will also return all the installed packages in R.

![](images/page13-01.png)

**4.** Help: Help on any function or command can be viewed through help tab. For example, to get a help on read.csv, type ? read.csv on the console. The outcome will appear in help tab as shown in **[Figure 1.9](#09_Chapter01.xhtml#fig1.9)**.

**5.** Viewer: RStudio consists of a Viewer pane that can be used to explore local web content. For example, web graphics and plots generated using packages such as GoogleVis, htmlwidgets, and rCharts, or even a local web application created using packages such as Shiny, Rook, or OpenCPU.

![](images/page13-02.png)

### 1.9 | Anaconda

Anaconda is another integrated development environment which gives data scientists access to the most popular data science distributions in Python and R. In effect, Anaconda is a distribution management system and a collection of over 1,000+ open-source packages. Anaconda distribution uses conda to manage packages, dependencies, and environment.

According to the official website of Conda,[⁷](#09_Chapter01.xhtml#ch1-r-fn7) “It is an open source package management and environment management system that runs on Windows, macOS and Linux. Conda quickly installs, runs, and updates packages and their dependencies. Conda easily creates, saves, loads, and switches between environments on local computer. It was created for Python programs, but it can package and distribute software for any language”. Anaconda IDE, primarily devised for doing data science using Python, provides all the support to perform data analysis using R. Conda is the package manager whereas Anaconda is a collection of around a hundred packages consisting of Conda, Numpy, Scipy, Ipython notebook, and so on.

Anaconda comes with two options:

**1.** Anaconda distribution: This version is an open-source edition and provides access to 1000+ data science packages. This is mostly used by standalone users to carry out statistical computing.

**2.** Anaconda Enterprise[⁸](#09_Chapter01.xhtml#ch1-r-fn8): It is a multi-user collaboration and a one-click deployment of models, notebooks, and dashboards with all the security and governance that IT teams need. It is useful for organizations and for collaborative development.

To download Anaconda, perform the following tasks:

**1.** For Windows, go to [https://docs.anaconda.com/anaconda/install/windows.html](https://docs.anaconda.com/anaconda/install/windows.html)

**2.** For MacOs, go to [https://docs.anaconda.com/anaconda/install/mac-os](https://docs.anaconda.com/anaconda/install/mac-os)

**3.** For Linux, go to [https://docs.anaconda.com/anaconda/install/linux](https://docs.anaconda.com/anaconda/install/linux)

More about Anaconda can be found at [https://docs.anaconda.com](https://docs.anaconda.com)

### 1.10 | | Anaconda Navigator

In this section, we discuss the various features of the Anaconda Navigator. The contents of this section are adopted from the official website of Anaconda. The official website of Anaconda Navigator[⁹](#09_Chapter01.xhtml#ch1-r-fn9) says, “It is a desktop graphical user interface (GUI) included in Anaconda distribution that allows user to launch applications and easily manage conda packages, environments and channels without using command-line commands. It is a GUI to the conda package and environment manager”. Navigator has the capability to search for packages on Anaconda Cloud or in a local Anaconda Repository. It is available for Windows, macOS, and Linux.

The following applications are available by default in Anaconda Navigator:

**1.** Jupyter Lab

**2.** Jupyter Notebook

**3.** Orange App

**4.** QTConsole

**5.** Glueviz

**6.** Vscode

**7.** RStudio

All the above applications are IDEs. However, we will be restricted to RStudio application in this book. After successful installation of Anaconda, launch the Anaconda Navigator and click on the RStudio installation tab. This will install a set of integrated tools including R-essential packages and notebooks for working on the R platform.

Jupyter Notebook is another popular IDE, like R Studio, and can be used to write and execute R Script. Installation of Anaconda framework also installs Jupyter Notebook.

An R code can be written by following either of the two options below:

**1.** Launch the RStudio IDE from the Anaconda Navigator. This will open the RStudio desktop version and can be used to write R scripts.

**2.** Launch Jupyter notebook from the Anaconda Navigator. Jupyter Notebook is a popular system that combines R and Python code, descriptive text, model output, plots, and interactive interfaces into a single notebook file that can be edited and used in a web browser.

However, to use Jupyter notebook for R scripting, we need to point the existing R kernel to the Jupyter notebook IDE. To do so, open R console (or open R through Terminal in Mac). Enter the following command:

**1.** install the package :- ‘IRkernel’: install.packages(‘IRkernel’)

**2.** Invoke the package: - library(IRkernel)

**3.** Make Jupyter Notebook point to the R kernel: - IRkernel::installspec()

**4.** Open Jupyter Notebook and you can write your R script by using R kernel.

installspec() has a ‘USER’ parameter which has the default path to install the IRkernel in Jupyter Notebook. Change the path option if the IRkernel installation is unsuccessful. Prefer the above steps for installation and use of R with Jupyter notebook.

The Rkernel can also be installed by using the command ‘conda install -c r r-irkernel‘[^(10)](#09_Chapter01.xhtml#ch1-r-fn10) on the Anaconda prompt/terminal. Further, install R packages[^(11)](#09_Chapter01.xhtml#ch1-r-fn11) into the current environment by typing the conda command on the terminal: conda install -c r package-name. Note that in the command conda install -c r package-name, one has to replace package-name with actual name of the package. For example, to install package ggplot2, the command should be conda install -c r ggplot2. To search for a package, one can use the command conda search -f EXACTNAME. We have to replace the word EXACTNAME with the desired name of the R package. Many CRAN packages have been rebuilt and made available as conda packages. According to the official website,[^(12)](#09_Chapter01.xhtml#ch1-r-fn12) “Anaconda does not provide builds of the entire CRAN repository, so there are some packages in CRAN that are not available as conda packages. Rather than installing each R language package individually, the R Essentials bundle can be used to install about 100 of the most popular scientific packages for the R programming language”. We can install the R Essentials bundle with the command conda install -c r r-essentials on terminal. Anaconda Navigator[^(13)](#09_Chapter01.xhtml#ch1-r-fn13) documentation provides a lot of details on managing packages as well as creating virtual environments.[^(14)](#09_Chapter01.xhtml#ch1-r-fn14)

One may also install Jupyter Notebook separately, without the need for installing Anaconda, and link it with R Software to write and execute R Script.

### Summary

• R is a robust application for statistical computing. Working on R platform becomes easy with the use of an IDE. RStudio and Anaconda are two of many IDEs available for use. Between RStudio and Anaconda, the choice of the tool is based on user convenience. If you are not development savvy, Anaconda environment usage may become overwhelming to start with. RStudio on its own is user-friendly and convenient for not-so-tech-savvy developers but still gives all the power to work seamlessly.

• The chapters in this book have been written using Jupyter notebook version 5.6.0 as an IDE. The Anaconda Navigator used is version 1.8.7 and the R software version 3.5.1 and 4.0.3. We can use the same script in RStudio IDE and execute them.

### Bibliography

**1.** Anaconda Inc (2020), “*The End to End Data Science Platform*”, Anaconda Inc, Web address: [https://www.anaconda.com/products/enterprise](https://www.anaconda.com/products/enterprise), accessed on 19 November 2020.

**2.** Anon (2021), “*Overview of R*”, Web address: [https://www.datasciencemadesimple.com/learn-r-what-is-r](https://www.datasciencemadesimple.com/learn-r-what-is-r)/, accessed on 11 September 2021.

**3.** Anon (2021), “*TIOBE Index*” Web address: [https://www.tiobe.com/tiobe-index](https://www.tiobe.com/tiobe-index), accessed on 26 January 2021.

**4.** Anon (2020), “*R Documentation*”, Web address: [https://www.rdocumentation.org](https://www.rdocumentation.org), accessed on 19 November 2020.

**5.** Anon (2020), “*The Comprehensive R Archive Network*”, Publisher: Institute of Statistics and Mathematics of WU, Web address: [https://cran.r-project.org](https://cran.r-project.org), accessed on 19 November 2020.

**6.** Anon (2021), “*R Overview*”, Web address: [https://sceweb.sce.uhcl.edu/helm/WEBPAGE-R/my\_files/TableContents/Module-2/module2page.hml](https://sceweb.sce.uhcl.edu/helm/WEBPAGE-R/my_files/TableContents/Module-2/module2page.hml), accessed on 15 January 2021.

**7.** Anon (2014), “*2014 DC AREA TECH STATS*”, Web address: [https://agileengine.com/2014-dc-area-tech-stats](https://agileengine.com/2014-dc-area-tech-stats), accessed on 15 January 2021.

**8.** Anon (2016), “*The current state of swift*”, Web address: [http://www.thomashanning.com/the-current-state-of-swift](http://www.thomashanning.com/the-current-state-of-swift), accessed on 15 January 2021.

**9.** Chollet F and Allair J J (2018), “*Deep Learning with R*”, Manning Publications, United Kingdom.

**10.** Kumar U D (2017), “*Business Analytics - The Science of Data-Driven Decision Making*”, Wiley, New Delhi.

**11.** Finkler S A, Smith D L and Thad D (2018), “*Financial Management for Public, Health, and Not-for-Profit Organizations*” Sage, Los Angeles.

**12.** Pradhan M and Kumar U D (2019), “*Machine Learning Using Python*”, Wiley, New Delhi.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#09_Chapter01.xhtml#ch1-fn1)[https://www.r-project.org](https://www.r-project.org)/

[²](#09_Chapter01.xhtml#ch1-fn2)[https://cran.r-project.org/doc/FAQ/R-FAQ.html#What-is-R\_003f](https://cran.r-project.org/doc/FAQ/R-FAQ.html#What-is-R_003f)

[³](#09_Chapter01.xhtml#ch1-fn3)[https://www.tiobe.com/tiobe-index](https://www.tiobe.com/tiobe-index)/

[⁴](#09_Chapter01.xhtml#ch1-fn4)[https://www.tiobe.com/tiobe-index/r](https://www.tiobe.com/tiobe-index/r)/

[⁵](#09_Chapter01.xhtml#ch1-fn5)[https://blog.revolutionanalytics.com/2017/02/job-trends-for-r-and-python.html](https://blog.revolutionanalytics.com/2017/02/job-trends-for-r-and-python.html)

[⁶](#09_Chapter01.xhtml#ch1-fn6)If you are installing *RStudio Desktop 1.1.442*, it will suggest that ‘RStudio requires R 3.0.1+’ which should already be installed on the desktop. Version incompatibility will affect certain statistical computing or installation of packages.

[⁷](#09_Chapter01.xhtml#ch1-fn7)[https://conda.io/en/latest](https://conda.io/en/latest)/

[⁸](#09_Chapter01.xhtml#ch1-fn8)[https://www.anaconda.com/enterprise](https://www.anaconda.com/enterprise)/

[⁹](#09_Chapter01.xhtml#ch1-fn9)[https://docs.anaconda.com/anaconda/navigator/user-guide](https://docs.anaconda.com/anaconda/navigator/user-guide)

[^(10)](#09_Chapter01.xhtml#ch1-fn10)[https://anaconda.org/r/r-irkernel](https://anaconda.org/r/r-irkernel)

[^(11)](#09_Chapter01.xhtml#ch1-fn11)[http://repo.continuum.io/pkgs/r](http://repo.continuum.io/pkgs/r)/

[^(12)](#09_Chapter01.xhtml#ch1-fn12)Source: [https://docs.anaconda.com/anaconda/packages/r-language-pkg-docs](https://docs.anaconda.com/anaconda/packages/r-language-pkg-docs)/

[^(13)](#09_Chapter01.xhtml#ch1-fn13)[https://docs.anaconda.com/anaconda/navigator](https://docs.anaconda.com/anaconda/navigator)/

[^(14)](#09_Chapter01.xhtml#ch1-fn14)[https://docs.anaconda.com/anaconda/navigator/tutorials](https://docs.anaconda.com/anaconda/navigator/tutorials)/

 

 
| 

## Data Preprocessing

 || 

## 2

 |
| --- | --- |

*The quieter you become, the more you can hear*.

**—Buddha**

LEARNING OBJECTIVES

After reading this chapter, you would be able to:

• Understand the concept of tidy data and its usefulness in data preparation and visualization.

• Understand the concept of data.table and working with data.table in R.

• Learn to load structured data using data.table and perform data query using the syntax of data.table package.

• Learn data preparation activities such as creating new features, sub setting, filtering, grouping, ordering, and joining of datasets.

• Understand why data.table gives faster load and data query time on millions of records over the basic data. frame in R.

• Learn the use of DT (Data Tables) package to render a data.table and data.frame as an HTML table.

### 2.1 | Data Preprocessing and Descriptive Analytics Using data.frame in R

Data preprocessing is a time-consuming activity in the Machine Learning (ML) project life cycle. Anecdotal evidence suggests that as high as 80% of the ML project time is spent on preparing data. Data preprocessing will involve activities such as dealing with integration of data from different sources and handling missing information, incorrect data, and so on. Along with Predictive and Prescriptive, Descriptive Analytics forms the third component of analytics. It is the science of describing past data and capturing ‘what happened’ in the given context. The primary objective of descriptive analytics is comprehension of data using data summarization, basic statistical measures, and visualization.

Data scientists deal with structured data in most data analysis activities, and are familiar with the concept of the Standard Query Language (SQL) table. SQL tables represent data in rows and columns, making it convenient to query and perform operations on the data. The similar structure of presenting data is supported in R through data.frame, which can be imagined as in-memory SQL tables, that is, data in tabular format.

![](images/page18-01.png)

A data.frame is a very efficient two-dimensional data structure, as shown in **[Figure 2.1](#10_Chapter02.xhtml#fig2.1)**. Data.frames are structurally flat in structure, and arranged in rows and columns that can be indexed or named.

A data.frame is called a tidy data.frame if it satisfies the following three interrelated rules:

**1.** Each variable has its own column.

**2.** Each observation (or record) has its own row.

**3.** Each value has its own cell.

It seems obvious that the structure of each data.frame will follow the above three points. However, that is not always the case. A variable might be spread across multiple columns, or an observation may be spread across multiple rows. **[Table 2.1](#10_Chapter02.xhtml#tab2.1)** shows a data.frame which does not follow the tidy data.frame conditions.

Data in **[Table 2.1](#10_Chapter02.xhtml#tab2.1)** represents the attrition rate for companies (ABC, XYZ and DEF) from 2000 to 2018. This is not a tidy data.frame as variable year is spread across multiple columns. Tidy data.frame for the data in **[Table 2.1](#10_Chapter02.xhtml#tab2.1)** is shown in **[Table 2.2](#10_Chapter02.xhtml#tab2.2)**.

When a data.frame satisfies the above three conditions, it becomes easy to perform downstream tasks such as filtering, aggregating, grouping, and plotting data, among other things. To demonstrate the usage of data.frame, we will use the IPL dataset (described in the next section) to load data and perform descriptive analytics, using data.table and ggplot2 to facilitate data wrangling.

### 2.2 | IPL Dataset Description

The Indian Premier League (IPL) is a professional Twenty20 cricket league started by the BCCI (The Board of Control for Cricket in India) in 2008, with eight franchises comprising players from across the world. The first IPL auction was held in 2008 for ownership of teams for 10 years, with a base price of USD 50 million. Franchises acquire players through an English auction conducted every year. However, there were several rules in place, among them a maximum cap on the money each franchise can spend to buy players.

![](images/page18-02.png)![](images/page19-01.png)

Performances of players can be measured through several metrics. Although the IPL is a 20-over tournament, it was possible that performances in the other formats of the game such as Tests and One-Day Internationals could influence pricing. A few players had excellent Test records, but their Twenty20 records were not as impressive. The dataset consists of performances of 130 players measured through various performance metrics such as batting strike rate, bowling economy rate, and so on. The list of features is provided in **[Table 2.3](#10_Chapter02.xhtml#tab2.3)** (Data file name: ipl.csv).

### 2.3 | Loading Dataset to R

The base package, named utils, has the option of reading data as a data.frame in the following file formats:

**1.** read.table( ) - reads a file in table format. It can be used to read file from Uniform Resource Locator (URL) as well.

**2.** read.csv( ) - wrapper function on read.table which reads a ‘ delimited file

**3.** read.csv2( ) - wrapper function on read.table which reads a ; delimited file

**4.** read.delim( ) - wrapper function on read.table which reads a \\t delimited file

**5.** read.ftable( ) - reads ‘flat’ contingency tables

**6.** read.fwf( ) - reads fixed width formatted (fwf) files. It can be used to read fwf file from the URL as well

Function read.table( ) and all related functions such as read.csv( ) etc., read all columns as character column, and convert the column into appropriate data type (logical, numeric, integer, complex, or factor) by using function type.convert( ). Storing every distinct value of a column, which is numeric, as a character string may occupy 14 times more memory space compared to storing it as an integer. Thus, all these functions can be very slow while trying to read a large data file. The function can be used efficiently for large dataset by setting some of the below parameters in read.table():

**TABLE 2.3** | IPL data feature description

| Data Code || Description |
| --- | --- |
| AGE || Age of the player at the time of auction classified into three categories: Category 1 (L25) includes players less than 25 years old; 2 means he is aged between 25 and 35 years (B25-35); and category 3 has 35-plus players (A35) |
| --- | --- |
| RUNS S || Number of runs scored by a player |
| RUNS C || Number of runs conceded by a player |
| HS || Highest score by a batsman in IPL |
| AVE B || Average runs scored by a batsman in IPL |
| AVE BL || Bowling average (number of runs conceded/number of wickets taken) in IPL |
| SR B || Batting strike rate (ratio of the number of runs scored to the number of balls faced) in IPL |
| SR BL || Bowling strike rate (ratio of the number of balls bowled to the number of wickets taken) in IPL |
| SIXERS || Number of sixes struck by a player in IPL |
| WKTS || Number of wickets taken by a player in IPL |
| ECON || Economy rate of a bowler (number of runs conceded by the bowler per over) in IPL |
| CAPTAINCY EXP || Captained either a T20 or a national team |
| ODI SR B || Batting strike rate in One-Day Internationals |
| ODI SR BL || Bowling strike rate in One-Day Internationals |
| ODI RUNS S || Runs scored in One-Day Internationals |
| ODI WKTS || Wickets taken in One-Day Internationals |
| T RUNS S || Runs scored in Test matches |
| T WKTS || Wickets taken in Test matches |
| PLAYER SKILL || Player’s primary skill (batsman, bowler, or all-rounder) |
| COUNTRY || Country of origin of the player (AUS: Australia; IND: India; PAK: Pakistan; SA: South Africa; SL: Sri Lanka; NZ: New Zealand; WI: West Indies; OTH: Other countries) |
| YEAR A || Year of Auction in IPL |
| IPL TEAM || Team(s) for which the player had played in the IPL (CSK: Chennai Super Kings; DC: Deccan Chargers; DD: Delhi Daredevils; KXI: Kings XI Punjab; KKR: Kolkata Knight Riders; MI: Mumbai Indians; PWI: Pune Warriors India; RR: Rajasthan Royals; RCB: Royal Challengers Bangalore). The + sign was used to indicate that the player had played for more than one team. For example, CSK+ would mean that the player had played for CSK as well as for one or more other teams. |

**1.** colClasses: Specify the class of each column. The possible values are logical, integer, numeric, complex, character, raw, factor, date.

**2.** nrows: An estimate of the rows in the data. Mild overestimation may be useful.

**3.** comment.char: The default for this parameter is #. This means while reading the file, if the function encounters # in any of the rows, the entire row will be dropped. Changing the default from # to ““ will make file-read faster.

An extended package data.table, first released in 2006[¹](#10_Chapter02.xhtml#ch2-r-fn1) has become popular for fast and efficient handling of large datasets. fread() from data.table is widely used to read data from a csv or a txt file. The advantage of fread() over the traditional read.table() from utils package is that it offers fast and memory-efficient operations of file read. fread() does so by automatically detecting the colClasses and nrows parameter, thus avoiding the need to read the values as character before converting them to correct datatype. To draw the point on efficiency in handling large dataset, we tested the read operation of data.table fread() function with the read.csv() function from utils package. We used the Seattle Public Library’s collection data[²](#10_Chapter02.xhtml#ch2-r-fn2) which has the dimension of 29,6,28,772 \* 13 (approx. 30 million observations across 13 variables; 9GB size). The read time to load this dataset using fread() was approx. 120 seconds, while the same data on the same machine configuration took approx. 400 seconds to load using the read.csv().

data.table package also allows efficient implementation of write, aggregation, update, equi join, non-equi join, etc., data.table is inherently a data.frame and thus is compatible with the R functions and packages which expects a data.frame. We can convert data.frames and lists to a data.table using setDT() and as.data.table() for other objects.

The data table object is intuitively same as a data frame object created by using native R (using base package) or by using Python (using pandas package) script. However, compared to data frame, the data table is very efficient in handling and querying a large dataset.

#### 2.3.1 Install Packages for Data Wrangling

Let us begin by loading the IPL dataset using fread() and then perform basic data wrangling operations and visualization using package ggplot2. However, before using the functions of package data.table and ggplot2, ensure that the package is installed in your machine. The install\_packages is a user-defined function which may be used to install data.table and ggplot2.

![](images/page21-01.png)

Note that the usage of the function has been described by inserting the comment within double quotes as soon as the function is defined. However, meta data like comment or help can also be written by using the attr() function as used above. The advantage is that these meta data can be highlighted if needed using the attribute(<function-name>) function, for example, attributes(install\_packages). The below code line will use the above-defined function and install the needed packages.

![](images/page21-02.png)

#### 2.3.2 Invoke Packages

Now we are ready to load the packages in memory by using the below code:

![](images/page21-03.png)

The fread() from data.table can be used for loading the file in R platform. The first four parameters of fread() can be used to read files of different types. We have inserted the description (Chomsky and Lifshitz, 2021) of these four parameters from the help section of fread():

• input: A single character string is used. The value is checked and assigned to either file= (if no \\n present), text= (if at least one \\n is present) or cmd= (if no \\n is present, at least one space is present, and it is not a file name).

• file: File name in working directory, or path to file through path.expand or a URL starting http://, file://, etc.

• text: The input data itself as a character vector, for example as returned by readLines().

• cmd: A shell command that preprocesses the file; e.g. fread(cmd=paste(“grep”,word,” filename”)).

Exactly one of input=, file=, text=, or cmd= should be used in the same call. Though most arguments/parameters inside the fread() function are set to default, we have highlighted four parameters whose default setting may require a change:

**1.** **na.strings:** Takes a vector of strings to signify which values should be read as NA. In the below code chunk, single space and #NA should be read as “NA”. We can specify all the strings we want to read as NA. Note that R treats NA as a missing value, hence the need to mark all unwanted values in the dataset as NA.

**2.** **stringsAsFactors:** Whether character columns need to be converted to factors, or read simply as character. The default is set to FALSE. While working with data. frames, for example, using read.csv() function, character columns are read as factors by default.

**3.** **data.table:** Whether the variable created after file is read, is to be treated as a data.table or a data.frame. The default is data.table, and it will remain so as this option helps to treat it both as data.table and data.frame.

**4.** **logical01:** Whether to read columns containing 0s and 1s as logical data type or integer data type. The default is to read as integer.

We can read about all the arguments of fread() by typing ?fread on the R Studio console.

![](images/page22-01.png)

**[Table 2.4](#10_Chapter02.xhtml#tab2.4)** shows the snapshot of the data with the first five observations. Note that **[Table 2.4](#10_Chapter02.xhtml#tab2.4)** does not show all the features of the dataset to maintain readability of the data.

![](images/page22-02.png)

### Useful Tip 1

#### Jupyter Notebook

If we use jupyter notebook, the default print shows 60 rows (first 30 and last 30) and 20 columns (first 10 and last 10). We can check the default option by using getOption(“repr.matrix.max.rows”) and getOption(“repr. matrix.max.cols”) function of R. We can also use .Options or options() without any parameter to get a list of all the possible DEFAULTS.

![](images/page23-01.png)

To show all the rows and columns, we can change the setting by repr.matrix.max.rows=Inf and repr.matrix.max.cols=Inf. We can also pass specific number of rows and columns which we desire to print e.g. repr.matrix.max.rows=100 and repr.matrix.max.cols=16.

### Useful Tip 2

#### RStudio

If we run the above code using RStudio, the default print for data.table is 120 rows. If the number of records in the dataset exceeds 120 rows then the first 5 rows from the top and the last 5 rows from the bottom are displayed.

Here as well, we can check the default option by using getOption() function of R. We can use options() to set these parameters to the value which we desire to display.

![](images/page23-02.png)

We can modify the default options in RStudio by using the options() and passing the required parameter for which we want to change the setting. Say, if we want to print all the rows in ipl\_dt we have to pass “data.table.print.nrows” = 130.

### 2.4 | Operations on data.table

The advantage of working with data.table over a data.frame is that multiple querying is possible from within data.table while data.frame only facilitates the subset of rows and select columns. The basic form of data.table is depicted in **[Figure 2.2](#10_Chapter02.xhtml#fig2.2)**:

![](images/page23-03.png)

In **[Figure 2.2](#10_Chapter02.xhtml#fig2.2)**, ‘DT’ is the name of the variable created using fread() . In our case, we have named it ipl\_dt. We can read **[Figure 2.2](#10_Chapter02.xhtml#fig2.2)** as ‘Take data.table DT, select rows by *i*, then either select column *j* or perform some operations on column j and group by some other columns.

The full description of arguments of data.table can be seen by using ?data.table on the RStudio console. Similar to an SQL statement, the columns in a data.table can be referred to as if they were a variable. Also, note that indexing in R starts at 1 and not 0.

We will perform data wrangling using data.table to understand the teams’ composition based on the players’ statistics. Here is the ranking of the top four teams in IPL 2011 based on their performance:

**1.** CSK

**2.** MI

**3.** KKR

**4.** RCB

While we could have analyzed the composition of all eight teams, we chose to restrict the scope to only the top four during IPL 2011.

**1.** Qualifier 1 between CSK and RCB was won by CSK.

**2.** Eliminator between MI and KKR was won by MI.

**3.** Qualifier 2 between RCB and MI was won by RCB.

**4.** The final between CSK and RCB was won by CSK.

We will analyze the past performance of the players of these four teams and the prices at which they were auctioned. Note that the dataset does not reflect the performance of players in IPL 2011, but in previous contests of T20, One-day, and Test cricket. It is pertinent to note that the dataset consists of players open for auction and sold thereafter. It does not represent players retained by their franchises, and who therefore did not make it to the auction. Before analyzing the teams’ composition, we will get acquainted with basic row and column operation using data.table.

Generically, the syntax for data.table is read as “Select rows and/or columns with or without condition; perform certain computation on column and apply aggregation operations like grouping based on some other column”.

#### 2.4.1 Basic Operations Using R

We will perform a few basic operations on the ipl\_dt. Let us try to print the first six records, the last six records, data types and, summary statistics of ipl\_dt. We will also discuss how to rename a column, drop a column, and add a new feature. To get the first six records, we can write head(ipl\_dt,6). **[Table 2.5](#10_Chapter02.xhtml#tab2.5)** shows the top six observations spanning across the first ten features from the ipl\_dt. **[Table 2.6](#10_Chapter02.xhtml#tab2.6)** shows the bottom six observations spanning the first ten features from the ipl\_dt.

![](images/page24-01.png)

Structure str(), shows data types and the first few observations for each feature in the data set. Dimensions of the data can be obtained using dim(). Let us see the dimensions of ipl\_dt and structure of one of the features from the ipl\_dt.

![](images/page24-02.png)![](images/page25-01.png)![](images/page25-02.png)

The dimension shows that ipl\_dt has 130 observations (records) and 27 features (variables). The structure of the variable ‘AGE’ reveals that the data type is ‘int’, and prints the first 10 observations of ‘AGE’ column.

summary() is used to get the basic summary of the first 5 features in the dataset.

![](images/page25-03.png)

**[Table 2.7](#10_Chapter02.xhtml#tab2.7)** shows the summary statistics of the first five features of ipl\_dt: For numeric features, we get the following summary statistics:

**1.** Numeric feature is summarized with: ‘Min’, ‘1^(st) Quartile’, ‘Median’, ‘Mean’, ‘3^(rd) Quartile’, and ‘Max’.

**2.** Since ‘fread’ method of data.table type casts categorical features as ‘Character column’, the summary statistics contains count of observation only (‘Length’).

We can use setnames() from the data.table package to rename any column. The advantage is that it changes names by reference without copying the whole dataset. We will rename RUNS\_S to PAST\_RUNS\_IPL and WKTS to PAST\_WKT\_IPL.

![](images/page25-04.png)![](images/page26-01.png)

#### 2.4.2 Basic Row Subset Operations

In a data.table, we can create a subset of rows by using logical expressions, row numbers, and order().

For example, the below code snippet creates **[Table 2.8](#10_Chapter02.xhtml#tab2.8)** wherein we can see the fifth and fourth rows and the first ten variables of ipl\_dt.

![](images/page26-02.png)

*ipl\_dt\[5:4,\]* will also result in the above outcome, but with all variables. Comma (,) in *ipl\_dt\[5:4,\]* is optional.

Below code snippet creates **[Table 2.9](#10_Chapter02.xhtml#tab2.9)** wherein we can observe all the rows except row 2:5 and the first ten variables of ipl\_dt.

![](images/page26-03.png)

The below code snippet can also be used to create **[Table 2.9](#10_Chapter02.xhtml#tab2.9)**.

![](images/page26-04.png)

Let us order the dataset by COUNTRY and show the first six records. The following code may be used to arrange records country-wise, and the outcome is shown in **[Table 2.10](#10_Chapter02.xhtml#tab2.10)**.

![](images/page26-05.png)![](images/page26-06.png)![](images/page26-07.png)![](images/page27-01.png)

Calling the order function with decreasing=TRUE in ipl\_dt\[order(COUNTRY, decreasing = TRUE)\] will return a data.table with a country being marked in reverse chronological order.

To select all the rows where Test match runs scored by the player are greater than 5,000, we can use the code snippet provided below to generate output **[Table 2.11](#10_Chapter02.xhtml#tab2.11)**.

![](images/page27-02.png)

The code snippet below selects all rows where Test runs scored by the player is greater than 5,000 and the number of Test wickets is more than 100. As seen in **[Table 2.12](#10_Chapter02.xhtml#tab2.12)**, Jacques Kallis is the only player in IPL 2011 to have achieved this feat.

![](images/page27-03.png)

#### 2.4.3 Basic Column Subset Operations

In data.table, several operations on column can be performed with ease. For example, the below coded chunk will return a column (PLAYING\_ROLE) as a vector.

![](images/page27-04.png)![](images/page27-05.png)![](images/page27-06.png)

**TABLE 2.13** | First six observations of the playing role from IPL data

| ROLE |
| --- |
| Allrounder |
| --- |
| Bowler |
| Bowler |
| Bowler |
| Batsman |
| Batsman |

**[Table 2.13](#10_Chapter02.xhtml#tab2.13)** shows the above result as a data.table by using the following code:

![](images/page28-01.png)

“.()“ in the aforementioned code is just an alias for list. This means we can name columns within .() and have named the list as ‘ROLE’ and show the first six rows with head() . In case the column is not named, it will be named V1, by default.

We can apply certain math operation on the columns from within the data.table. Say, we want to get the total amount spent by all franchises. The below code snippet will help us get the number, which is $6.7 million.

![](images/page28-02.png)

**[Table 2.14](#10_Chapter02.xhtml#tab2.14)** gives the list of countries represented in the IPL and the count of players from each of those countries.

![](images/page28-03.png)

Apart from India - Australia, South Africa, Sri Lanka, and Pakistan were the top four nations with most representation in IPL 2011.

**[Table 2.15](#10_Chapter02.xhtml#tab2.15)** shows the snapshot of the first five rows and the first 10 features of the data.table.

![](images/page28-04.png)

**TABLE 2.14** | Count of players by country

| COUNTRY || Freq |
| --- | --- |
| AUS || 22 |
| --- | --- |
| BAN || 1 |
| ENG || 3 |
| IND || 53 |
| NZ || 7 |
| PAK || 9 |
| SA || 16 |
| SL || 12 |
| WI || 6 |
| ZIM || 1 |

![](images/page29-01.png)![](images/page29-02.png)

The below code can be used to generate **[Table 2.16](#10_Chapter02.xhtml#tab2.16)** which shows the first five rows of the dataset with PLAYER\_NAME, AGE , COUNTRY, and TEAM:

![](images/page29-03.png)

Let us select column PAST\_IPL\_WKTS (wickets taken in IPL) and column T\_WKTS (wickets taken in test cricket) and calculate a new column TOTAL\_WKTS which is the sum of PAST\_ IPL\_WKTS and T\_WKTS. **[Table 2.17](#10_Chapter02.xhtml#tab2.17)** shows the outcome of the below code snippet:

![](images/page29-04.png)

Note that the code snippet created a new data.table but did not insert a new column TOTAL\_WKTS in the ipl\_dt. This also means there was a copy of ipl\_dt created when we wrote the above statement. This is inefficient, and can create a lot of overhead and consume more memory while dealing with a large dataset.

data.table provides := operator can be used to add/update/delete a column. Note that this can be used only on column j but can be combined with the querying syntax of data. table, that is, DT\[i,j, by + other arguments\]. The syntax for ‘:=‘ is LHS := RHS

![](images/page29-05.png)![](images/page30-01.png)

LHS takes a character vector of column names and RHS a list of values.

**[Table 2.18](#10_Chapter02.xhtml#tab2.18)** adds a new column TOTAL\_WKTS in ‘ipl\_dt‘ using the below code.

![](images/page30-02.png)

Note that the **[Table 2.18](#10_Chapter02.xhtml#tab2.18)** does not show the TOTAL\_WKTS as we are showing the first 10 columns of the ‘ipl\_dt‘. **[Table 2.18](#10_Chapter02.xhtml#tab2.18)** can also be obtained by writing the query in a functional form, as shown below:

![](images/page30-03.png)

Let us say we would like to delete column Ln(soldp). **[Table 2.19](#10_Chapter02.xhtml#tab2.19)** will be the outcome from the below code snippet. Column Ln(soldp) will disappear from **[Table 2.19](#10_Chapter02.xhtml#tab2.19)** (**Note:** Variable Ln(soldp) comes after column 10 in the data, and thus does not appear in **[Tables 2.18](#10_Chapter02.xhtml#tab2.18)** and **[2.19](#10_Chapter02.xhtml#tab2.19)**).

![](images/page30-04.png)

We can use : = operator to replace values in a column. Assume that wherever the strike rate of the bowlers in T20 cricket is zero, and we would like to replace that value with the strike rate of the bowlers in ODIs. **[Table 2.20](#10_Chapter02.xhtml#tab2.20)** shows we just have one such case in ipl\_dt.

![](images/page30-05.png)![](images/page30-06.png)![](images/page31-01.png)

Moreover, the strike rate for Abdur Razzak in ODI matches is

![](images/page31-02.png)

For such an operation, if we use := operator, it will make changes in the original ipl\_dt itself. For many reasons, we may not want that in the original data.table. The copy() function can help create a copy of the ipl\_dt on which we will use the := operator.

![](images/page31-03.png)

We can see that the T20 Bowling Strike rate is replaced by the ODI Bowling Strike rate.

![](images/page31-04.png)

Let us add a new column which shows the maximum sold price for each pair of PLAYING\_ ROLE, TEAM combination. **[Table 2.21](#10_Chapter02.xhtml#tab2.21)** shows the outcome of the below code snippet:

![](images/page31-05.png)

#### 2.4.4 Basic Row and Column Select and Compute Operations

In this section, we will understand the use of row and column selection and applying certain computations on the selected rows and columns.

For example, let us create a table of all players from Australia, South Africa, Sri Lanka, and Pakistan in the top four teams of IPL 2011. Remember that the top four teams were CSK, MI, KKR, and RCB.

![](images/page31-06.png)![](images/page32-01.png)

**[Table 2.22](#10_Chapter02.xhtml#tab2.22)** shows the players from CSK whose country of origin was Australia, South Africa, Sri Lanka, or Pakistan.

![](images/page32-02.png)

**[Table 2.23](#10_Chapter02.xhtml#tab2.23)** shows the players from MI whose country of origin was Australia, South Africa, Sri Lanka, or Pakistan.

![](images/page32-03.png)

Readers are encouraged to create similar tables for KKR and RCB.

It is interesting to note from **[Table 2.22](#10_Chapter02.xhtml#tab2.22)** that CSK had six players in their squad from Australia and South Africa but none from Sri Lanka or Pakistan. In data.table, a query like ipl\_dt\[COUNTRY == ‘SA’\] is internally optimized to use binary search and will provide faster results on a large dataset.

However, for more complex queries like the ones used to create **[Table 2.22](#10_Chapter02.xhtml#tab2.22)** and **[Table 2.23](#10_Chapter02.xhtml#tab2.23)**, data.table gives a provision to use a parameter ‘on’. This parameter helps in fast sub setting using joins. The below code snippet implements ‘on’ to query CSK players who are from AUS, SA, SL, and PAK, and will give the output as shown in **[Table 2.24](#10_Chapter02.xhtml#tab2.24)**.

![](images/page32-04.png)

As shown in **[Table 2.24](#10_Chapter02.xhtml#tab2.24)**, the no-match returns NA, implying that there were no players from Sri Lanka and Pakistan who played for CSK. To suppress the no-match result, we can execute the below code snippet, which will result in **[Table 2.25](#10_Chapter02.xhtml#tab2.25)**.

![](images/page32-05.png)![](images/page32-06.png)![](images/page33-01.png)![](images/page33-02.png)

We will now try to get the total number of wickets taken in previous IPL editions by players in the top four teams of the IPL. To do so:

**1.** We will subset rows by that is, C(“CSK’”,MI”,KKR”,RCB’) on TEAM. The use of ‘on’ operator results in binary search and thus is faster compared to writing TEAM == ‘CSK’ & TEAM == ‘MI’ & TEAM == ‘KKR’ & TEAM == ‘RCB’.

**2.** Perform operations on column ‘j’, that is, calculate TOTAL\_WKTS as a sum of PAST\_ IPL\_WKT groupby by TEAM using the following code.

**[Table 2.26](#10_Chapter02.xhtml#tab2.26)** shows the outcome of the below code:

![](images/page33-03.png)

Based on this data, it seems that the previous experience level of bowlers contributed to the teams’ performance in IPL 2011 as well. We can re-write the query which resulted in **[Table 2.26](#10_Chapter02.xhtml#tab2.26)**, by using special keyword .EACHI which will iterate through each subset of i.

![](images/page33-04.png)

**TABLE 2.26** | Total number of wickets taken in previous IPL editions by Team CSK, MI, KKR, and RCB

| TEAM || TOTAL\_WKTS |
| --- | --- |
| CSK || 202 |
| --- | --- |
| MI || 178 |
| KKR || 46 |
| RCB || 58 |

**TABLE 2.27** | Total runs scored in previous IPL editions by various teams

| TEAM || TOTAL\_IPL\_RUNS |
| --- | --- |
| CSK || 8,649 |
| --- | --- |
| CSK+ || 1,118 |
| MI || 3,460 |
| MI+ || 4,855 |
| KKR || 278 |
| KKR+ || 7,322 |
| RCB || 3,952 |
| RCB+ || 7,187 |

**[Table 2.27](#10_Chapter02.xhtml#tab2.27)** shows IPL runs scored by players of the top four teams using the following code:

![](images/page34-01.png)

In **[Table 2.27](#10_Chapter02.xhtml#tab2.27)**, CSK+ implies that the players have played for other teams apart from CSK. Note that the statistics above are just a representation based on the sample of 130 players in this dataset. In reality, the figures may far exceed these statistics. To corroborate this fact, let us look into the batting line-up for MI based on the runs scored by players in past T20 matches (**[Table 2.28](#10_Chapter02.xhtml#tab2.28)**).

![](images/page34-02.png)

The maximum runs scored for MI is by Indian players (**[Table 2.28](#10_Chapter02.xhtml#tab2.28)**). **[Table 2.29](#10_Chapter02.xhtml#tab2.29)** shows the list of players of MI based on COUNTRY, PLAYING\_ROLE, and RUN\_S

![](images/page34-03.png)![](images/page34-04.png)![](images/page35-01.png)

The ‘on’ parameter in data.table can be used for performing efficient conditional filter operation on columns.

The ‘on’ parameter internally uses joins to give faster result on large data sets.

The ‘.EACHI’ which is an inbuilt symbol can be used in ‘by’ operator to perform compute operations on columns for each unique values filtered using ‘on’ operator.

As is evident, this is not the complete list of players who played for MI. We have a team MI+ as well, which contains those who played for other teams in the past.

Let us try to deep dive into the bowling department. How many wickets were taken by players from the top four nations (based on the number of players in the IPL season) representing CSK, MI, KKR, and RCB? **[Table 2.30](#10_Chapter02.xhtml#tab2.30)** shows the wickets taken by the ‘AUS’, ‘SA’, ‘SL’, and ‘PAK’ players for team CSK.

![](images/page35-02.png)

Well!!! Out of the total 202 wickets taken by CSK, 113 came through players from AUS and SA. [Table 2.31](#10_Chapter02.xhtml#tab2.31) shows the list of bowlers from these two nations who played for CSK.

![](images/page35-03.png)

**[Table 2.31](#10_Chapter02.xhtml#tab2.31)** can also be obtained by the below query:

![](images/page35-04.png)![](images/page35-05.png)![](images/page35-06.png)

### 2.5 | Group by Operations

The tabulation of data based on the feature list can be done within the data.table. We will compute the average wicket taken by players in past IPL appearances using the following code.

![](images/page36-01.png)

In the above query, we can use min() , quantile() , mean() , median(), and max() to get a specific summary statistic for a numeric column. **[Table 2.32](#10_Chapter02.xhtml#tab2.32)** shows the average number of T20 wickets taken by players grouped by PLAYING\_ROLE

![](images/page36-02.png)

**[Table 2.33](#10_Chapter02.xhtml#tab2.33)** shows the average number of T20 wickets taken by AGE category (less than 25 years, between 25 and 35 years, and over 35 years) and PLAYING\_ROLE:

![](images/page36-03.png)

To order the results by column, we can use the below query. Note that **[Table 2.33](#10_Chapter02.xhtml#tab2.33)** and **[Table 2.34](#10_Chapter02.xhtml#tab2.34)** are same, but the result is ordered by PLAYING\_ROLE.

![](images/page36-04.png)

**TABLE 2.32** | Average wickets taken by Playing role in past IPL edition

| PLAYING\_ROLE || AVERAGE\_WKT\_T20 |
| --- | --- |
| Allrounder || 19.028571 |
| --- | --- |
| Bowler || 32.818182 |
| Batsman || 3.128205 |
| W. Keeper || 0.000000 |

![](images/page36-05.png)![](images/page37-01.png)

Note that the keyby argument does not only order the data.table but also sets the columns as keys. The concept of keys and its usefulness in fast search will be discussed later.

**[Table 2.35](#10_Chapter02.xhtml#tab2.35)** shows the average number of T20 wickets taken by AGE, COUNTRY, TEAM, and PLAYING\_ROLE.

![](images/page37-02.png)

How many players auctioned in 2009 are still with CSK?

![](images/page37-03.png)

The above query can also be written with .N, which is a built-in symbol and holds the number of observations in the current group.

![](images/page37-04.png)![](images/page37-05.png)![](images/page38-01.png)

**[Table 2.36](#10_Chapter02.xhtml#tab2.36)** shows the total number of players for each country-team pair for a particular playing role ‘Bowler’.

![](images/page38-02.png)

**[Table 2.37](#10_Chapter02.xhtml#tab2.37)** shows **[Table 2.36](#10_Chapter02.xhtml#tab2.36)** in a sorted order. The result is sorted in ascending order for country and decreasing order for team

![](images/page38-03.png)

In the above query, the bowler count was stored in a variable bowler\_count\_dt and then ordered in the next line. We can avoid the temporary variable by chaining the above two queries. The below code snippet will also result in **[Table 2.37](#10_Chapter02.xhtml#tab2.37)**.

![](images/page38-04.png)

The by argument of data.table can take column names as well as expressions. **[Table 2.38](#10_Chapter02.xhtml#tab2.38)** shows the count of players who have taken more than five wickets in T20 cricket, more than 10 wickets in One-Day Internationals, and more than 20 wickets in Test cricket.

![](images/page38-05.png)

In **[Table 2.38](#10_Chapter02.xhtml#tab2.38)**, the first row corresponds to T20\_5W >5 = TRUE , ODI\_10W>10 = FALSE, TEST\_20W>20=FALSE and the total number of records satisfying this criteria is 15 players.

**[Table 2.39](#10_Chapter02.xhtml#tab2.39)** shows the count which satisfies all three conditions at the same time:

![](images/page38-06.png)![](images/page38-07.png)![](images/page39-01.png)

**TABLE 2.39** | Count of players who have taken more than five wickets in T20 cricket, more than 10 wickets in One-Day Internationals, and more than 20 wickets in Test cricket (all conditions satisfied)

| Condition || N |
| --- | --- |
| FALSE || 89 |
| --- | --- |
| TRUE || 41 |

Another useful built-in symbol in data.table is .SD, which stands for subset of data. .SD in itself is a data.table which holds the data of the subset defined using ‘by’ argument of data. table. **[Table 2.40](#10_Chapter02.xhtml#tab2.40)** shows the ipl\_dt, which is printed using the .SD symbol.

![](images/page39-02.png)

.SD symbol can be used with lapply() function to iterate through multiple columns at the same time and compute statistics we are interested in calculating. Let us calculate the average number of wickets taken and average number of runs scored by players in all three formats of the game. For doing this:

**1.** We have used lapply() to iterate through the columns.

**2.** We have grouped the players by AGE, PLAYING\_ROLE. Instead of using by, we have used keyby which returns an ordered set.

**3.** We have passed the column names on which we want to compute the average statistics in .SDcols

**[Table 2.41](#10_Chapter02.xhtml#tab2.41)** shows the outcome of the above steps as applied through the code snippet below:

![](images/page39-03.png)![](images/page39-04.png)![](images/page40-01.png)

The ‘by’ operator can be used to group the compute operation on some column w.r.t. the other columns. This argument can also take conditional expressions.

The ‘.N’ is a built-in symbol and holds the number of observations in the current group. This can be used to get the count of observations based on conditional filter on rows.

The ‘.SD’, which stands for subset of data, along with ‘.SDcols’ is another built-in symbol which can be used to apply compute operations, such as calculating mean, median, standard deviation, etc., on the columns specified under ‘.SDcols‘.

**TABLE 2.42** | T20 wickets and test wickets taken by each player based on the playing role

| PLAYING\_ROLE || WICKETS\_TAKEN |
| --- | --- |
| Allrounder || 15 |
| --- | --- |
| Allrounder || 19 |
| Allrounder || 47 |
| Allrounder || 73 |
| Allrounder || 5 |
| Allrounder || 2 |

.SDcols is optional. However, in this situation, lapply will throw an error as the dataset also contains character columns and computing mean does not hold true for character variables.

The compute operation on columns is very flexible in data.table. An operation to even flatten a column can be done using data.table query syntax. For example, **[Table 2.42](#10_Chapter02.xhtml#tab2.42)** concatenates T20 wickets and test wickets taken by each player based on the playing role:

![](images/page40-02.png)

### 2.6 | Keys and Binary Search-Based Subset

The use of keys in data.table makes it much more efficient in subsetting and in handling subsequent downstream activities. Keys can be intuitively thought of as a row.names of base R data.frame with the exception that:

**1.** Keys can be set on multiple columns and the columns can be of different data types.

**2.** Uniqueness is not enforced in keys

Setting keys in a data.table

**1.** Rearranges the rows based on column names provided as keys. The ordering is always in an ascending order.

**2.** Marks the columns used as key columns by setting an attribute called sorted to the data.table.

![](images/page41-01.png)

A point to note while using keys is that the query structure does not change. This means all the querying syntax discussed in sections 2.4 and 2.5 can still be done using keys, with the advantage of speed and efficiency while dealing with large dataset.

Let us set COUNTRY and TEAM as keys in ipl\_dt (**[Table 2.43](#10_Chapter02.xhtml#tab2.43)**)

![](images/page41-02.png)

We can notice from **[Table 2.43](#10_Chapter02.xhtml#tab2.43)** that ipl\_dt is ordered in ascending order of COUNTRY and then by TEAM. We can subset the ipl\_dt by COUNTRY or TEAM or a combination of both. **[Table 2.44](#10_Chapter02.xhtml#tab2.44)** shows the subset of data by filtering out players from Australia and playing for Chennai Super Kings.

![](images/page41-03.png)

In the above subset query, AUS was looked for in the first key column COUNTRY. Within the matching rows for AUS, CSK is matched against the second key column TEAM. Since we did not provide any operation on j, the query returned all columns corresponding to those row indices.

**[Table 2.45](#10_Chapter02.xhtml#tab2.45)** shows the number of wickets taken by players from Sri Lanka and playing for Mumbai Indians.

![](images/page41-04.png)![](images/page41-05.png)

**TABLE 2.45** | Wickets taken by players of Country SL and playing for Team MI

| PLAYING\_ROLE || WICKETS\_TAKEN |
| --- | --- |
| Allrounder || 13 |
| --- | --- |
| Bowler || 17 |
| Bowler || 83 |

Notice that the key set for ipl\_dt was ‘COUNTRY’ ‘TEAM’

![](images/page42-01.png)

whereas in the above query, the data.table has a key set as ‘PLAYING\_ROLE’

![](images/page42-02.png)

Querying with keys performs a binary search compared to the vector scan. Without setting in key, when we write a query like ipl\_dt\[COUNTRY ==‘AUS’ & TEAM==‘CSK’\], it performs a vector scan.

To understand the point, let us assume that ipl\_dt is a large dataset with one million records. When we write ipl\_dt\[COUNTRY ==‘AUS’ & TEAM==‘CSK’\], the operation, done internally, will be as follows:

**1.** A row by row search performed on Column COUNTRY for a value ‘AUS’. The result will be a logical vector of size one million marking TRUE, FALSE, or NA.

**2.** A row by row search performed on Column TEAM for a value ‘CSK’. The result will be a logical vector of size one million marking TRUE, FALSE, or NA.

**3.** Element wise ‘&’ operation performed on the above two logical vectors returned from step 1 and step 2. Value will be returned wherever the operations on the two logical vectors evaluates to TRUE.

While doing the same query, that is, ipl\_dt\[.(‘AUS’, ‘CSK’)\] by setting COUNTRY and TEAM as keys, the operation will be halved as the data is sorted based on COUNTRY and TEAM. The operation which will be done internally will be:

**1.** Middle element of the sorted column COUNTRY will be compared with the value AUS. Since the value AUS is smaller than the middle element, the search space will be set to the upper half of the column.

**2.** Again, the middle element of the upper half of the column COUNTRY will be compared to the value ‘AUS’ and the iteration will continue till the value ‘AUS’ is found.

**3.** The above two steps will be repeated for column TEAM to find the value for ‘CSK’.

**4.** The & operation on the above two logical vectors returns the value wherever the expression evaluates to TRUE.

Thus, the binary search on a large dataset will be much faster compared to a vector scan. We can see that the binary search reduces the search space by almost half and thus is incredibly fast while querying a large dataset.

### 2.7 | Join operations

We may need to combine columns from multiple data frames into one single data frame. In this case, both data frames need to have a common column. The remaining column values can then be retrieved from both the data frames and joined to create a row in the resulting data frame.

To merge two data frames, data.table querying syntax with ‘on’ argument can be used. It can be called on one of the data frames and the other data frame can be passed as a parameter to it. The argument ‘on’ is the common column or a key in data frames and should be present in both the data frames.

**1.** X\[Y, on=\*\] is a join operation, looking up X’s rows using Y’s column name provided using on=\* or key values of Y, as an index. This returns all the rows from Y with matching records from X.

**2.** Y\[X, on=\*\] is a join operation, looking up Y’s rows using X’s column name provided using on=\* or key values of X, as an index. This returns all the rows from X with matching records from Y.

Data frames can be joined based on multiple common columns. The join type can be of inner, outer, left, or right joins and should be specified in the ‘how’ parameter.

Let us create two data.table representing Chennai Super Kings and Mumbai Indians. We have set COUNTRY and TEAM as keys by using the below code snippet:

![](images/page43-01.png)

Using the below code snippet, **[Table 2.46](#10_Chapter02.xhtml#tab2.46)** shows the players from CSK based on just the key named TEAM.

![](images/page43-02.png)

In **[Table 2.46](#10_Chapter02.xhtml#tab2.46)**, the key for ipl\_csk\_dt will be same as that of ipl\_dt, that is, COUNTRY and TEAM.

In case we want to have a different key for ipl\_csk\_dt, we will have to use the ‘keyby’ argument. However, ‘keyby’ or ‘by’ expects column ‘j’ to be provided. We can use the built-in operator .SD to pass all the columns or provide a specific column name. **[Table 2.47](#10_Chapter02.xhtml#tab2.47)**, generated using the below code snippet, shows all matching rows for TEAM CSK and selects columns TEAM, COUNTRY, and SOLD\_PRICE grouped by AGE and PLAYING\_ROLE:

![](images/page43-03.png)![](images/page43-04.png)![](images/page44-01.png)

**[Table 2.48](#10_Chapter02.xhtml#tab2.48)**, generated using the below code snippet, shows all matching rows for TEAM MI and selects columns TEAM, COUNTRY, and SOLD\_PRICE grouped by AGE and PLAYING\_ROLE:

![](images/page44-02.png)

Let us join ipl\_csk\_dt, that is, **[Table 2.47](#10_Chapter02.xhtml#tab2.47)** with ipl\_mi\_dt, that is, **[Table 2.48](#10_Chapter02.xhtml#tab2.48)** using their keys. When we write ipl\_csk\_dt\[ipl\_mi\_dt\], the join operation is going to look up ipl\_csk\_dt using the AGE and PLAYING\_ROLE keys of ipl\_mi\_dt.

**1.** In **[Table 2.48](#10_Chapter02.xhtml#tab2.48)**, with AGE==2 and PLAYING\_ROLE==BOWLER, the ipl\_mi\_dt has three records. We also see in **[Table 2.47](#10_Chapter02.xhtml#tab2.47)** that there are two records corresponding to AGE==2 and PLAYING\_ROLE==BOWLER. Each of the records of ipl\_csk\_dt will appear in combination with ipl\_mi\_dt. This will make up for the first six records in joined data.table.

**2.** In **[Table 2.48](#10_Chapter02.xhtml#tab2.48)**, with AGE==3 and PLAYING\_ROLE==Allrounder, there are two records. We also see in **[Table 2.47](#10_Chapter02.xhtml#tab2.47)** that there are no records corresponding to AGE==3 and PLAYING\_ROLE==Allrounder. Thus, the join operation will report NA values from the ipl\_csk\_dt and show it in combination with ipl\_mi\_dt. This will make up for the next two records in joined data.table.

![](images/page44-03.png)

**3.** In **[Table 2.48](#10_Chapter02.xhtml#tab2.48)**, with AGE==3 and PLAYING\_ROLE==Batman, the ipl\_mi\_dt has one record. We also see in **[Table 2.47](#10_Chapter02.xhtml#tab2.47)** that there are three records corresponding to AGE==3 and PLAYING\_ROLE==Batsman. Each of the records of ipl\_csk\_dt will appear in combination with ipl\_mi\_dt. This will make up for the last three records in joined data.table.

This is a right join and the output is shown in **[Table 2.49](#10_Chapter02.xhtml#tab2.49)**.

![](images/page45-01.png)

Note, that ipl\_csk\_dt\[ipl\_mi\_dt, on =.(AGE,PLAYING\_ROLE)\] is optional. We did not provide the key, so the join happened on the keys which were set for the ipl\_csk\_dt and ipl\_mi\_dt.

We can suppress the NA records, which will be similar to inner join as shown in **[Table 2.50](#10_Chapter02.xhtml#tab2.50)**:

![](images/page45-02.png)

What if we want to create a join, like ipl\_mi\_dt\[ipl\_csk\_dt\] ? This operation will look up ipl\_mi\_dt using the key values of ipl\_csk\_dt.

**1.** As in **[Table 2.47](#10_Chapter02.xhtml#tab2.47)**, with AGE==1 and PLAYING\_ROLE==Batsman, the ipl\_csk\_dt has one record. There is no record in ipl\_mi\_dt, corresponding to AGE==1 and PLAYING\_ROLE==Batsman (**[Table 2.48](#10_Chapter02.xhtml#tab2.48)**). Thus, the join operation will report NA values from the ipl\_mi\_dt and show it in combination with ipl\_csk\_dt. This will make up for the first records in the joined data.table.

![](images/page45-03.png)![](images/page45-04.png)

**2.** The next three combinations of AGE and PLAYING\_ROLE in ipl\_csk\_dt (**[Table 2.47](#10_Chapter02.xhtml#tab2.47)**), that is,

• AGE==1 and PLAYING\_ROLE==Bowler

• AGE==2 and PLAYING\_ROLE==Allrounder

• AGE==2 and PLAYING\_ROLE==Batsman

also do not have any corresponding match in ipl\_mi\_dt (**[Table 2.48](#10_Chapter02.xhtml#tab2.48)**). So, the next seven records of the resultant data.table will be NA records corresponding to ipl\_mi\_dt and will show up in combination of ipl\_csk\_dt.

**3.** As in **[Table 2.47](#10_Chapter02.xhtml#tab2.47)**, with AGE==2 and PLAYING\_ROLE==BOWLER, the ipl\_csk\_dt has two records. We also see that ipl\_mi\_dt has three records corresponding to AGE==2 and PLAYING\_ROLE==BOWLER (**[Table 2.48](#10_Chapter02.xhtml#tab2.48)**). Each of the records of ipl\_mi\_dt will appear in combination with ipl\_csk\_dt. This will make up for the next six records in joined data.table.

**4.** In **[Table 2.47](#10_Chapter02.xhtml#tab2.47)**, with AGE==2 and PLAYING\_ROLE==W.Keeper, the ipl\_csk\_dt has one record. The ipl\_mi\_dt has no records corresponding to AGE==2 and PLAY-ING\_ROLE==W.Keeper (**[Table 2.48](#10_Chapter02.xhtml#tab2.48)**). Thus, the join operation will report NA values from the ipl\_mi\_dt and show it in combination with ipl\_csk\_dt. This will make up for the next record in joined data.table.

**5.** Finally, With AGE==3 and PLAYING\_ROLE==Batman, the ipl\_csk\_dt has three records as seen in **[Table 2.47](#10_Chapter02.xhtml#tab2.47)**. We also see in **[Table 2.48](#10_Chapter02.xhtml#tab2.48)** that ipl\_mi\_dt has one record corresponding to AGE==3 and PLAYING\_ROLE==Batsman. This record of ipl\_mi\_dt will appear in combination with ipl\_csk\_dt. This will make up for the last three records in joined data.table.

![](images/page46-01.png)

**[Table 2.51](#10_Chapter02.xhtml#tab2.51)** shows the joined table following the above steps:

**[Table 2.52](#10_Chapter02.xhtml#tab2.52)** shows the suppressed table with no match records being removed and making it an inner join (left table having matching rows in right table).

![](images/page46-02.png)

Some more join operations are shown below. **[Table 2.53](#10_Chapter02.xhtml#tab2.53)** shows the join operation of ipl\_mi\_dt on ipl\_csk\_dt and the SOLD\_PRICE for each key:

![](images/page46-03.png)

**[Table 2.54](#10_Chapter02.xhtml#tab2.54)** shows all the records from ipl\_csk\_dt which do not have a matching record in ipl\_mi\_dt. This is as good as looking up the ipl\_csk\_dt for the AGE and PLAYING\_ROLE combination which is not present in ipl\_mi\_dt:

![](images/page46-04.png)![](images/page47-01.png)![](images/page47-02.png)![](images/page47-03.png)

What if we want to join the two data.tables with a column name which is not set as a key? This can be done by explicitly passing the column name in on=\* argument. **[Table 2.55](#10_Chapter02.xhtml#tab2.55)** shows the join of ipl\_csk\_dt with ipl\_mi\_dt based on the country name present in ipl\_mi\_dt.

Join operation can be used to merge data tables by using the syntax ‘Table1\[Table2}‘. The order of the table in this syntax drives whether the resultant table is a left join or a right join. The columns used to perform the match is specified using ‘on’ operation. If ‘on’ operator is not specified, then the join happens based on the table keys.

![](images/page48-01.png)![](images/page48-02.png)![](images/page48-03.png)

### 2.8 | Data Table, Data Frame, and Package DT

Let us see the basic differences between the following:

**1.** data.table and data.frame

**2.** package data.table and package DT

#### 2.8.1 Data Table vs. Data Frame

Experienced users of R understand the advantages of creating a data.table compared to reading as data.frame. Here, we will highlight one important distinction between reading a file using fread() (creates a data.table) and read.table() (creates a data.frame). While reading a file as data.frame using base R read.table(), we will get a rowname which we also refer to as an index column. For demonstration purposes, we have used read.table() to read the ipl.csv file and create a new data.frame as shown in **[Table 2.56](#10_Chapter02.xhtml#tab2.56)**.

![](images/page49-01.png)![](images/page49-02.png)

In the above code chunk, we have used the row.names argument to pass a specific column which we would like to use as rownames. Not using this argument would have led to the rownames being numbered by default.

![](images/page49-03.png)![](images/page50-01.png)

We can subset a row using rownames.

![](images/page50-02.png)

The output of above code snippet is shown in **[Table 2.57](#10_Chapter02.xhtml#tab2.57)**. Thus row.names are like indices to the rows of a data.frame but the limitation is that:

**1.** Each row can be identified by only one row.name.

**2.** row.name expects unique value.

But a player can be uniquely recognized by PLAYER.NAME, COUNTRY, and maybe more attributes. This is where the concept of keys in data.table offers an efficient way of handling such cases. One fundamental difference between rowname/index and key is that rowname has to be unique but uniqueness in keys is not enforced. We can set the keys in data.table by using the key argument of fread() or using setkey() after having read the data using fread().

Since data.table inherits from data.frame, data.table also has rowname attribute but never uses this attribute. We can convert the data.frame to a data.table by using setDT() or as.data.table().

![](images/page50-03.png)![](images/page50-04.png)![](images/page51-01.png)

In **[Table 2.58](#10_Chapter02.xhtml#tab2.58)**, we can see that the rownames have been reset and the original rownames, that is, “PLAYER.NAME” is lost. If one wants to retain the rownames while converting a data. frame to a data.table, they can do so by setting the parameter keep.rownames=TRUE in as.data.table() or in setDT(). This will create a new column called rn which will contain the row names of original data.frame. By default, keep.rownames=FALSE which will reset the rownames to default numbering and any index column information of the original data.frame will be lost.

![](images/page51-02.png)

#### 2.8.2 Data.table Package vs. DT Package

The DT package is different from the data.table package used to read the IPL.csv file. DT package can be used to render the data.tables as well as data.frames on the HTML page with options of filtering, pagination, sorting, etc.

**[Figure 2.3](#10_Chapter02.xhtml#fig2.3)** is the outcome of the below code chunk. It renders the data.table ‘ipl\_dt’ as a DT data table.

![](images/page51-03.png)![](images/page51-04.png)![](images/page52-01.png)

The datatable() function used in the above code snippet is from DT package and should not be confused as from data.table() function, which comes from the data.table package.

**[Figure 2.3](#10_Chapter02.xhtml#fig2.3)** can also be modified to get options to generate in csv, excel, or pdf file. **[Figure 2.4](#10_Chapter02.xhtml#fig2.4)** is generated using the below code snippet which shows these extra options using the extensions = ‘Buttons.

![](images/page52-02.png)

The options parameter gives flexibility to modify the look and feel of the datatable.

![](images/page52-03.png)

### Summary

• Objective of data preprocessing is simple comprehension of data using data summarization, basic statistical measures, and visualization.

• A dataset in tidy format helps in easier processing of data as well as in visualization.

• Data.table, which can be visualized as in-memory structured query language (SQL) tables, are widely used data structured for loading and manipulating structured data.

• Data.table provides excellent support for DataFrame and its operations. Operations like filtering, grouping, aggregations, sorting, joining, and many more are readily available in this library.

• While data querying, Data.table helps in performing binary search rather than a vector scan and thus gives very fast while working on very large dataset.

### Exercise Problems

#### Use the Bollywood Dataset to Answer Questions 1 to 9

The data file *bollywood.csv* (link to the datasets is provided in the Preface) contains box office collection and social media promotion information about movies released in 2013-2015 period. Following are the columns and their descriptions.

• *SlNo* - Release Date

• *MovieName* - Name of the movie

• *ReleaseTime* - Mentions special time of release. LW (Long weekend), FS (Festive Season), HS (Holiday Season), N (Normal)

• *Genre* - Genre of the film such as Romance, Thriller, Action, Comedy, etc.

• *Budget* - Movie creation budget

• *BoxOfficeCollection* - Box office collection

• *YoutubeViews* - Number of views of the YouTube trailers

• *YoutubeLikes* - Number of likes of the YouTube trailers

• *YoutubeDislikes* - Number of dislikes of the YouTube trailers

#### Use R Code to Answer the Following Questions

**1.** How many records are present in the dataset? Print the metadata information of the dataset.

**2.** How many movies got released in each genre? Which genre had the highest number of releases? Sort number of releases in each genre in descending order.

**3.** How many movies in each genre got released in different release times like long weekend, festive season, etc. (Note: Do a cross tabulation between *Genre* and *ReleaseTime*.)

**4.** Which month of the year the maximum number movie releases are seen? (Note: Extract a new column called month from *ReleaseDate* column.)

**5.** Which month of the year typically sees most releases of high-budget movies, that is, movies with budget of 25 crore or more?

**6.** Which are the top 10 movies with maximum return on investment (ROI)? Calculate return on investment (ROI) as (*BoxOfficeCollection - Budget*)/*Budget*.

**7.** Do the movies have higher ROI if they get released on festive seasons or long weekend? Calculate the average ROI for different release times.

**8.** Compare the distribution of ROIs between movies with comedy genre and drama. Which genre typically sees higher ROIs?

#### Use the SAheart Dataset to Answer Questions 9 and 10

The dataset SAheart.data is taken from the following link:

[http://www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data](http://www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data)

The dataset SAheartData.txt contains retrospective sample of males in a heart-disease high-risk region of the Western Cape, South Africa. There are roughly two controls per case of Coronary Heart Disease (CHD). Many of the CHD-positive men have undergone blood pressure reduction treatment and other programs to reduce their risk factors after their CHD event. In some cases, the measurements were made after these treatments. These data are taken from a larger dataset, described in Rousseauw et al. (1983), *South African Medical Journal*. It is a tab-separated file and contains the following columns (source: *[http://www-stat.stanford.edu](http://www-stat.stanford.edu)*)

*sbp* - Systolic blood pressure

*tobacco* - Cumulative tobacco (kg)

*ldl* - Low-density lipoprotein cholesterol

*adiposity*

*famhist* - Family history of heart disease (Present, Absent)

*typea* - Type-A behaviour

*obesity*

*alcohol* - Current alcohol consumption

*age* - Age at onset

*chd* - Response, coronary heart disease

**9.** How many records are present in the dataset? Print the metadata information of the dataset.

**10.** Derive a new column called *age group* from *age* column where persons falling in different age ranges are categorized as follows:

(0-15): young

(15-35): adults

(35-55): mid

(55-): old

### Bibliography

**1.** Anon (2020), “*Data Table Options*”, Web address: [https://rstudio.github.io/DT/options.html](https://rstudio.github.io/DT/options.html), accessed on 9 November 2020.

**2.** Anon (2020), “*DT: An R Interface to the Data Tables Library*”, Web address: [https://rstudio.github.io/DT](https://rstudio.github.io/DT), accessed on 19 November 2020.

**3.** Weschools (2020), “*SQL Joins*”, Publisher: w3schools, Web address: [https://www.w3schools.com/sql/sql\_join.asp](https://www.w3schools.com/sql/sql_join.asp), accessed on 19 November 2020.

**4.** Anon (2020), “*Getting started with package*”, Web address: [https://docs.racket-lang.org/pkg/getting-started.html](https://docs.racket-lang.org/pkg/getting-started.html), accessed on 14 January 2021.

**5.** Anon (2019), “*setuptools*” Web address: [https://github.com/pypa/setuptools/issues/1724](https://github.com/pypa/setuptools/issues/1724), accessed on 14 January 2021.

**6.** Anon (2015), “*The fundamentals of data analysis with R*”, Web address: [https://www.slideshare.net/RsquaredIn/r-programming-importing-data-in-r](https://www.slideshare.net/RsquaredIn/r-programming-importing-data-in-r), accessedon14 January 2021.

**7.** Chomsky E and Lifshitz A (2021), “*Use fread() to read csv/tsv*” Web address: [https://tanaylab.github.io/tgutil/reference/fread\_rownames.html?cv=1](https://tanaylab.github.io/tgutil/reference/fread_rownames.html?cv=1), accessed on 08 September 2021.

**8.** Pradhan M and Kumar UD (2019), “*Machine Learning Using Python*”, Wiley, New Delhi.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#10_Chapter02.xhtml#ch2-fn1)Source: [r-data.table.com](http://www.r-data.table.com)

[²](#10_Chapter02.xhtml#ch2-fn2)Source: [https://www.kaggle.com/city-of-seattle/seattle-library-collection-inventory](https://www.kaggle.com/city-of-seattle/seattle-library-collection-inventory)

 

 
| 

## Data Visualization

 || 

## 3

 |
| --- | --- |

*When the student is ready the teacher will appear. When the student is truly ready the teacher will disappear.*

**—Lao Tzu**

LEARNING OBJECTIVES

After reading this chapter, you would be able to:

• Understand the grammar of visualization and concepts behind various visual plots in R.

• Learn the importance of data visualization and storytelling using data.

• Learn to prepare plots such as bar plot, histogram, distribution plot, box plot, scatter plot, trend plot and heat maps to find insights.

### 3.1 | Data Visualization in R

Data visualization plays an important role in machine learning model building and deployment. It helps data scientists to communicate machine learning model outputs and insights effectively. Visualization helps data scientists build machine learning models by assisting in such model building stages such as feature engineering.

Data visualization is an integral component of business intelligence (BI) too. Innovative visuals are used in dashboards that are a part of reports generated by companies to understand their performance using various key performance indicators.

Package ggplot is a powerful package for visualization in R. The fundamentals of ggplot are based on the grammar of graphics proposed by Wickham (2010).[¹](#11_Chapter03.xhtml#ch3-r-fn1) Grammar of graphics is a tool which helps describe the building blocks of graphics and offers the flexibility to interact with different layers of a graph. The concept of layering of charts gives ggplot an edge over other visualization packages. The ggplot package is based on a solid foundation of grammar of graphics. To demonstrate the usage of ggplot, we will rely on IPL dataset (described in the next section) to load data into data.frame and perform descriptive analytics. We will use data.table and ggplot2 to perform data wrangling.

### 3.2 | IPL Dataset Description

The Indian Premier League (IPL) is a professional Twenty20 cricket league started by the BCCI in 2008, with eight franchises comprising players from across the world. The first IPL auction was held in 2008 for ownership of teams for 10 years, with a base price of USD 50 million.

Franchises acquire players through an English auction conducted every year. However, there were several rules in place, among them a maximum cap on the money a franchise can spend to buy players.

Performances of players can be measured through several metrics. Although the IPL is a 20-over tournament, it was possible that performances in the other formats of the game such as Tests and One-Day Internationals could influence pricing. A few players had excellent Test records, but their Twenty20 records weren’t as impressive. The dataset consists of performances of 130 players measured through various performance metrics such as batting strike rate, bowling economy rate, and so on. The list of features (file name ipl.csv) is provided in **[Table 3.1](#11_Chapter03.xhtml#tab3.1)** (Pradhan and Kumar, 2019).

**TABLE 3.1** | IPL data description

| Data Code || Description |
| --- | --- |
| AGE || Age of the player at the time of auction classified into three categories: category 1 (L25) means the player is less than 25 years old, 2 means the age is between 25 and 35 years (B25-35) and category 3 means the age is more than 35 (A35) |
| --- | --- |
| RUNS S || Number of runs scored by a player |
| RUNS C || Number of runs conceded by a player |
| HS || Highest score by a batsman in IPL |
| AVE B || Average runs scored by a batsman in IPL |
| AVE BL || Bowling average (number of runs conceded/number of wickets taken) in IPL |
| SR B || Batting strike rate (ratio of the number of runs scored to the number of balls faced) in IPL |
| SR BL || Bowling strike rate (ratio of the number of balls bowled to the number of wickets taken) in IPL |
| SIXERS || Number of six runs scored by a player in IPL |
| WKTS || Number of wickets taken by a player in IPL |
| ECON || Economy rate of a bowler (number of runs conceded by the bowler per over) in IPL |
| CAPTAINCY EXP || Captained either an T20 team or a national team |
| ODI SR B || Batting strike rate in One-Day Internationals |
| ODI SR BL || Bowling strike rate in One-Day Internationals |
| ODI RUNS S || Runs scored in One-Day Internationals |
| ODI WKTS || Wickets taken in One-Day Internationals |
| T RUNS S || Runs scored in Test matches |
| T WKTS || Wickets taken in Test matches |
| PLAYER SKILL || Player’s primary skill (batsman, bowler, or all-rounder) |
| COUNTRY || Country of origin of the player (AUS: Australia; IND: India; PAK: Pakistan; SA: South Africa; SL: Sri Lanka; NZ: New Zealand; WI: West Indies; OTH: Other countries) |
| YEAR A || Year of auction in IPL |
| IPL TEAM || Team(s) for which the player had played in the IPL (CSK: Chennai Super Kings; DC: Deccan Chargers; DD: Delhi Daredevils; KXI: Kings XI Punjab; KKR: Kolkata Knight Riders; MI: Mumbai Indians; PWI: Pune Warriors India; RR: Rajasthan Royals; RCB: Royal Challengers Bangalore). A + sign was used to indicate that the player had played for more than one team. For example, CSK+ would mean that the player had played for CSK as well as for one or more other teams. |

### 3.3 | Install Packages

The following codes can be used for installing packages that are used for generating various plots.

![](images/page57-01.png)

### 3.4 | Invoke packages

After installation of packages, we are ready to load the packages in memory and display a snapshot of the data using the code provided below. **[Table 3.2](#11_Chapter03.xhtml#tab3.2)** shows the snapshot of the dataset (10 columns and 6 rows).

![](images/page57-02.png)![](images/page58-01.png)

### 3.5 | Exploration of Data Using Visualization

In this section, we will discuss various plots that can be drawn using ggplot2 package, which implements the grammar of graphics and works seamlessly with data.frame or data.table.

To understand the basics of grammar of graphics, let’s take a simple example of three variables: bowling average (AVE\_BL) in past IPL matches, bowling strike rate (SR\_BL) in past IPL matches, and the team these players belong to (TEAM) for all bowlers from ipl\_dt. Definitions of the features are provided below:

**1.** Bowling average (AVE\_BL) is number of runs conceded/number of wickets taken. The lower the bowling average, the better his performance.

**2.** Bowling strike rate (SR\_BL) is number of balls bowled/number of wickets taken. The lower the strike rate, the better his performance.

The below code snippet selects the bowling average, strike rate, and team from the ipl\_dt, where the playing role is ‘Bowler’. The head() function is used to print the first six observations as shown in **[Table 3.3](#11_Chapter03.xhtml#tab3.3).**

![](images/page58-02.png)

**[Table 3.3](#11_Chapter03.xhtml#tab3.3)** summarizes the AVE\_BL and SR\_BL of bowlers from different TEAMS. Note that, AVE\_BL and SR\_BL may be zero if a bowler is playing the IPL for the first time. If we want to generate a scatter plot between AVE\_BL and SR\_BL from the above data, we will draw a point for each observation. The point will be positioned horizontally (horizontal axis) based on AVE\_BL and vertically (vertical axis) based on SR\_BL. Also, assume that we want to give the points colour (red, green, orange, etc.) based on the TEAM.

To generate a scatter plot, the steps listed below must be followed:

**1.** Create a new dataset that reflects the mapping of AVE\_BL to horizontal axis, SR\_BL to vertical axis, and third dimension ‘TEAM’ can be assigned a shape (such as a point). Horizontal axis, vertical axis, and shape (point) are known as the aesthetics of a graph, that is, things which we see on a graph. Many aesthetics can be generated from the above data. We can draw a line chart, in which case the shape will be a line and not a point. We can also generate a bar chart from the above data (aesthetic will be bar). Thus, point, line, or bar can be termed as geometrical objects.

![](images/page58-03.png)

**2.** Convert the numbers, that is, AVE\_BL and SR\_BL into physical units which can be displayed by the computer. We can do so by linear scaling and by using the cartesian co-ordinate system. These transformations need to be performed for every aesthetic -horizontal axis, vertical axis, and shape. In this case, it applies to TEAM as well (map CSK to green, map DD to red, etc.). These transformations are known as scaling.

**3.** Render the above data to create a graphical object that can be displayed on the screen. This step combines data (represented by geometrical objects), the scales and the co-ordinate system and plot annotations (title, background, axis name, etc).

Based on the type of chart one wishes to generate from transformations/scaling done in step 2, many variations of the plot can be achieved. In the example of scatter plot, it is just an identity transformation where we plot the point as it appears in the data. However, one can bin or aggregate data before plotting, and they can be thought of as statistical transformations (histogram plot, box plot, contour plot, density plot, jitter plot, etc.).

Mapping from variables to aesthetic and geometrical objects, scaling and transformations, and rendering forms one layer of the plot. A plot can have multiple layers. The layer component is the physical representation of data, and is visible on the screen. A layer with a combination of stat and geom defines many familiar graphics and plots such as the scatterplot, histogram, contour plot, bar plot, etc.

ggplot2 helps to implement the grammar of graphics as described below.

The **ggplot package** is based on grammar of graphics and follows the concept of layering of charts. The function ggplot() creates an empty plot section, which intuitively can be thought of as canvas ready to paint.

**1.** ggplot(): It creates a coordinate system (empty graph) to which different layers are added.

**2.** geom\_objects: A geom is the geometrical object that a plot uses to represent data. geom\_point() adds a layer of points which creates a scatter plot.

ggplot2[²](#11_Chapter03.xhtml#ch3-r-fn2) comes with many geom objects that each adds a different type of layer to a plot.

#### 3.5.1 Scatter Plot

Scatter plot is a plot of two variables represented as cloud of points showing a joint distribution of two numerical variables, in which each point denotes an observation from the dataset. Scatter plot assists data scientists in understanding if there is any association relationship between two variables. The relationship could be linear or non-linear. Scatter plot is also useful for assessing the strength of the relationship and to find if there are any outliers in the data. Scatter plots are used during regression model building to decide whether to include a variable in a regression model.

The following code snippet can be used to create a scatter plot between AVE\_BL and SR\_BL using the ggplot package. Since data in **[Table 3.2](#11_Chapter03.xhtml#tab3.2)** is to be plotted without applying transformation, the stat and position parameter takes the value “identity”.

![](images/page59-01.png)![](images/page60-01.png)

In **[Figure 3.1](#11_Chapter03.xhtml#fig3.1)**, the ggplot() created a plot object, to which a layer was then added. In the layer, we specified the data and the mapping. We also specified that the geometrical object is point (which shows various records as a scatter plot).

However, while using the ggplot, many defaults are set in ggplot():

**1.** When we specify the geom, there is no need to specify the stats since the geometrical objects have default transformation already set, and vice versa. The ggplot defines many geometrical functions. Say, for geom=“point”, ggplot has geom\_ point(), for geom=“bar”, ggplot has geom\_bar() , etc.

**2.** The data and aesthetic mapping can be provided in the ggplot() itself. However, not all aesthetic will be applicable to all geometrical functions. While adding multiple layers of geom functions, one needs to be careful about the aesthetic applicable to that layer. If the aesthetic is passed within the geom functions, it overrides the aesthetic passed in ggplot() .

**3.** Default scales will be added according to the type of variables and the aesthetic mapping. It means scale\_x\_continuous() and scale\_y\_continuous() are used by default in the above plot. We can mention scale in case it is needed to change the default. Say, the scaling is logarithmic (scale\_x\_log10() and scale\_y\_ log10()), etc.

**4.** Cartesian co-ordinate system is used by default.

The scatter plot in **[Figure 3.1](#11_Chapter03.xhtml#fig3.1)** can be generated by simplifying the code. We can also specify the colour aesthetic to generate a scatter plot and colour it by TEAM.

![](images/page60-02.png)

Notice that we have used plot annotations to name the horizontal axis, vertical axis, and title (by default is left aligned). From **[Figure 3.2](#11_Chapter03.xhtml#fig3.2)**, we can conclude that there is a positive correlation between these two variables. As the bowling average goes up (i.e. a bowler is conceding more runs per wicket taken), the strike rate also goes up (i.e., he is bowling more balls per wicket taken). We can add another layer with geom\_smooth, which will fit a smooth line to the data. **[Figure 3.3](#11_Chapter03.xhtml#fig3.3)** shows the graph generated by the below code snippet.

![](images/page61-01.png)![](images/page61-02.png)![](images/page61-03.png)

Notice that the aesthetic variable is used in the ggplot() rather than inside geom functions. Since both the geom functions used the *x* and *y* aesthetic, we can employ it at a higher level rather than inside the geom functions. However, there are geom function level aesthetics which cannot be passed at the higher level. Say, geom\_point can have a shape aesthetic to give different shapes to the points based on variable TEAM. However, geom\_line cannot have a shape aesthetic. Thus, shape aesthetic cannot be passed at the higher-level function ggplot() .

Before we proceed with other plots, we will understand the use of theme() function which gives more control over plot annotations. The following code snippet uses theme() to change the text colour of the title, x-axis andy-axis, as well as centre align the title.

![](images/page62-01.png)![](images/page62-02.png)

**[Figure 3.4](#11_Chapter03.xhtml#fig3.4)** shows the scatter plot with changes in the default plot theme of ggplot2. However, the background colour of the graph as well as major and minor axis are present. We can further customize the graph. **[Figure 3.5](#11_Chapter03.xhtml#fig3.5)** shows the outcome using the following code snippet.

![](images/page62-03.png)![](images/page63-01.png)![](images/page63-02.png)

In the above code snippet, the arguments which can be used in element\_text are as follows:

**1.** family: font family

**2.** face: font face. Possible values are ‘plain, ‘italic’, ‘bold’, and ‘bold.italic’

**3.** colour: text colour

**4.** size: text size in pts

**5.** hjust: horizontal justification (between 0 and 1. 0 = left aligned, 0.5 = centre aligned, 1 = right aligned)

**6.** vjust: vertical justification (between 0 and 1. 0 = left aligned, 0.5 = centre aligned, 1 = right aligned)

**7.** lineheight: line height. In multi-line text, the line height argument is used to change the spacing between lines

Get the help on ?ggplot2::theme and ?ggplot2::element\_text, which works in conjunction with theme.

We can remove the title and axis labels by using element\_blank() within the theme(). There are in-built themes such as theme\_bw(), theme\_classic(), theme\_ dark() , theme\_grey() , theme\_light() , theme\_minimal() , etc., which can be directly applied to the plots. The below code snippet is being used to set a custom theme to be used in all code snippets in this chapter.

![](images/page63-03.png)![](images/page64-01.png)

#### 3.5.2 Bar Chart

Bar chart is a frequency chart for qualitative variable (or categorical variable). Histograms (discussed in [Section 3.5.3](#11_Chapter03.xhtml#sec3.5.3)) cannot be used when the variable is qualitative. Bar chart can be used to assess the most-occurring and least-occurring categories within a dataset (Kumar, 2017; Roshan, 2020). To draw a bar chart, we can:

**1.** Use geom\_bar() which makes the height of the bar proportional to the number of cases in each category or group (if the weight aesthetic is supplied, it sums up the weights).

**2.** Use geom\_col, in case we want the height of the bar to represent actual values. The dataframe should be passed in the parameter data. **[Figure 3.6](#11_Chapter03.xhtml#fig3.6)** shows a bar plot created for the count of players for each age category.

geom\_bar() uses stat\_count() by default and thus counts the number of records at each horizonal (x) position. geom\_col() uses stat\_identity() which plots the actual values from the data.

Since AGE is being read as an integer variable by data.table, we will typecast it as a factor variable before proceeding with a plot of bar charts. To get a count of players by age, we can use the following codes:

![](images/page64-02.png)

From **[Figure 3.6](#11_Chapter03.xhtml#fig3.6)**, we can observe that a majority of the players are in the age group of 25-35 (AGE 2). To plot the sum of SOLD\_PRICE for different AGE groups and display the total sold price by each age category, we should pass SOLD PRICE as weight parameter and AGE as *x* parameter (horizontal axis).

Note that to show the vertical axis values in dollars, we have passed labels argument in scale\_y\_continuous function. It can take three values, that is, scales::percent, scales::dollar and scales::comma.

![](images/page64-03.png)![](images/page65-01.png)![](images/page65-02.png)

We can create **[Figure 3.7](#11_Chapter03.xhtml#fig3.7)** by using geom\_col as shown below.

![](images/page65-03.png)

We can also create bar charts which can be grouped by a third variable. In **[Figure 3.8](#11_Chapter03.xhtml#fig3.8)**, we show the total sold price by each age category but grouped by playing roles. The parameter fill takes the third variable as a groupby parameter. In this case, we pass PLAYING ROLE as the fill parameter.

![](images/page66-01.png)![](images/page66-02.png)

In case we want to show the relative proportions at each AGE group, we can use position=position\_fill() which stacks the bars and then standardizes each of them to have the same height.

![](images/page66-03.png)

In **[Figure 3.9](#11_Chapter03.xhtml#fig3.9)**, we can compare the sold price for batsmen in three different age groups and conclude that batsmen were sold for maximum value in AGE group 1, followed by AGE group 3 and AGE group 2. By default, the geom\_bar or geom\_col will give a stacked bar chart. **[Figure 3.10](#11_Chapter03.xhtml#fig3.10)** shows the bars in dodged position. We set the position argument as position = position\_dodge() .

![](images/page66-04.png)![](images/page67-01.png)![](images/page67-02.png)

If we want to show the average sold price for each AGE group, we will first create a data. table with this statistic using the following codes. The average sold price across various age group is shown in **[Table 3.4](#11_Chapter03.xhtml#tab3.4).**

**TABLE 3.4** | Mean sold price by age

| AGE || AVG\_SOLD\_PRICE |
| --- | --- |
| 1 || 720,250.0 |
| --- | --- |
| 2 || 484,534.9 |
| 3 || 520,178.6 |

![](images/page67-03.png)![](images/page68-01.png)

The following code chunk can be used for creating **[Figure 3.11](#11_Chapter03.xhtml#fig3.11):**

![](images/page68-02.png)

From **[Figure 3.11](#11_Chapter03.xhtml#fig3.11)**, we can note that the average sold price is higher for age category 1. Also note that the fill is passed as an aesthetic outside the mapping argument as we wanted to fill the same colour across all age groups.

We can create bar charts which can be grouped by a third variable. In the example below **([Figure 3.12](#11_Chapter03.xhtml#fig3.12))**, we show average sold price by each age category but grouped by playing roles **([Table 3.5](#11_Chapter03.xhtml#tab3.5)).**

![](images/page68-03.png)

The parameter fill takes the third variable as group by variable. In this case, we pass PLAYING ROLE as hue parameter.

![](images/page69-01.png)![](images/page69-02.png)![](images/page69-03.png)

From **[Figure 3.12](#11_Chapter03.xhtml#fig3.12)**, we can see that in age categories 1 and 2, batsmen are paid the most, whereas allrounders attract most money in age category 3.

#### 3.5.3 Histogram

A histogram is a plot that shows the frequency distribution of a set of continuous variables. It gives an insight into the underlying distribution (e.g. normal distribution) of the variables, outliers, skewness, etc. To draw a histogram, we use geom\_histogram() function of ggplot2. The following is an example of how to draw a histogram for SOLD PRICE and understand its distribution **([Figure 3.13](#11_Chapter03.xhtml#fig3.13)).**

![](images/page69-04.png)![](images/page70-01.png)![](images/page70-02.png)

The histogram in **[Figure 3.13](#11_Chapter03.xhtml#fig3.13)** shows SOLD PRICE is right skewed. Most players are auctioned at low price range of 250,000 and 500,000, whereas there are a few players paid very highly, upwards of 1 million dollars. By default, it tries to estimate the bins which cover the range of the data. To create more bins, the bins parameter can be set in the geom\_histogram() method, as shown in **[Figure 3.14](#11_Chapter03.xhtml#fig3.14).**

![](images/page70-03.png)![](images/page71-01.png)![](images/page71-02.png)

We can use the fill aesthetic to show a histogram plot of sold price of players with different playing roles. **[Figure 3.15](#11_Chapter03.xhtml#fig3.15)** represents the same.

![](images/page71-03.png)

Unlike in **[Figure 3.14](#11_Chapter03.xhtml#fig3.14)**, in **[Figure 3.15](#11_Chapter03.xhtml#fig3.15)** fill aesthetic is being passed inside the mapping. This helps map the PLAYING\_ROLE as an aesthetic and gives different colours to the bars by applying different PLAYING\_ROLE.

geom\_histogram displays the counts with bar. However, if we want to display the counts with lines, we can use frequency polygons with the geometrical object named geom\_freqpoly. Frequency polygons are more suitable to compare the distribution across the levels of a categorical variable **([Figure 3.16](#11_Chapter03.xhtml#fig3.16)).**

![](images/page71-04.png)![](images/page72-01.png)![](images/page72-02.png)

Let us say we want to show the relationship between two numeric variables. In [Section 3.5.1](#11_Chapter03.xhtml#sec3.5.1), we saw that scatter plot was the obvious choice to get a plot between two numeric variables. However, when the data size is huge, scatter plot may not help in bringing out any pattern due to overlapping of points and the clutter which will show up.

**[Figure 3.17](#11_Chapter03.xhtml#fig3.17)** shows scatter plot between SOLD\_PRICE and BASE\_PRICE using the geom\_point.

![](images/page73-01.png)

Though the data size is not huge in the current example, **[Figure 3.17](#11_Chapter03.xhtml#fig3.17)** shows overlapping points and does not bring out any relationship between the two variables. This issue can be overcome with 2D histogram.

So far, all the plots in this section have used straight-line segments (bins) to show the count of observations in each bin. This is because, in one-dimension, straight-line segments are the only possible shape for bin in a histogram. However, when we have two dimensions in the data, bins can take a more general shape (rectangular/Hexagon). This brings us to the two-dimensional histogram (2d histogram) implemented via geom\_bin2d or through geom\_hex. It can be useful to show the relationship between two numeric features when the data size is huge.

Imagine the scatter plot in **[Figure 3.17](#11_Chapter03.xhtml#fig3.17)** being filled with rectangular boxes (where the boxes represent the bins in horizontal and vertical directions). The count of values in each of the bins can be coloured with gradient fill.

**[Figure 3.18](#11_Chapter03.xhtml#fig3.18)** depicts the plot SOLD\_PRICE and BASE\_PRICE using the geom\_bin2d. bins define the number of bins in horizontal and vertical direction. Lesser the number of bins, bigger the size of the hexagons. We will also use scale\_fill\_gradient2 which creates a three-colour gradient fill(low-mid-high). In general:

**1.** scale\_\*\_gradient creates a two-colour gradient (low-high). \* can be set as fill or colour.

![](images/page73-02.png)

**2.** scale\_\*\_gradient2 creates a diverging colour gradient (low-mid-high). \* can be set as fill or colour.

**3.** scale\_\*\_gradientn creates an n-colour gradient. \* can be set as fill or colour.

![](images/page74-01.png)

Scatter plot can be represented in a more appealing plot by hexagon shapes, and the count of points falling in each hexagon can be used to fill the shape.

**[Figure 3.19](#11_Chapter03.xhtml#fig3.19)** depicts the plot SOLD\_PRICE and BASE\_PRICE using the geom\_hex. bins define the number of bins in the horizontal and vertical directions. Lesser the number of bins, bigger the size of the hexagons.

![](images/page74-02.png)

The darker shade reflects a count of 10 or more players in the hexagonal bin who were sold at their base price. The lighter shade reflects a count of less than five players in the bin, some of whom were sold for over $150,000, though their base price was approximately $50,000-100,000. below, **[Figure 3.20](#11_Chapter03.xhtml#fig3.20)** represents the same hexagon plot as shown above, but by filling the hexagons based on playing role.

![](images/page74-03.png)![](images/page75-01.png)![](images/page75-02.png)

Allrounders went for much more than their base price, reiterating the importance of that breed in T20 cricket.

#### 3.5.4 Distribution or Density Plot

Before understanding the density plot, we need to understand basic terminology which is used to define the construction of density plot:

**Probability density function (PDF):** PDF is a limiting value of probability that a continuous random variable *X* takes in a small interval *x* and *x* + *8x,* when *8x* -> 0. That is, PDF of a continuous random variable *f(x)* is shown in [Equation 3.1](#11_Chapter03.xhtml#eq3.1).

![](images/page75-03.png)

**1.** PDF satisfies the following properties:

• PDF is non-negative.

• PDF is real-valued.

• Equation 3.2 shows that the value of the function’s definite integral over the support dataset is equal to 1

![](images/page76-01.png)

In machine learning, random variables that follow uniform distribution, normal distributions and exponential distribution are used frequently to model business contexts to gain insights. In this section, we will focus on plotting density plot from IPL data.

A kernel is a special type of PDF with the additional property that it must be even. A kernel is a function with the following properties (Anon, 2020):

• Function is non-negative.

• Function is real-valued.

• Function’s definite integral over the support dataset is equal to 1.

• Function is even *f(x)* = *f(-x),* for example, some theoretical PDFs such as uniform and standard normal distribution satisfy the properties of kernel functions.

**Density plot:** It plots a smooth curve depicting the PDF or distribution of data. The peak of the curve helps in visualizing where the values are concentrated in any given data. Density plots are not affected by the number of bins and discover the distribution shape of the variable from the sample data. They also offer insight into what the distribution shape of the population is. The kernel density plot is arrived at by using kernel density estimation.

**Kernel density estimation (KDE):** It is a non-parametric method which can be used to estimate the PDF of a continuous variable (Anon, 2013). At every data point (observation), a kernel function is created with the observation at its centre. The kernel function generally used is gaussian curve (normal distribution). The observation is kept in the centre to ensure the kernel is symmetric about the observation. The PDF is then estimated by adding all kernel functions and dividing by the number of data points (Anon, 2013). This is done to ensure that the properties of PDF are satisfied.

Intuitively, a KDE can be perceived as a sum of ‘humps’ (bulged point). A ‘hump’ is assigned to every observation, and the size of the ‘hump’ represents the probability assigned at the neighbourhood of values around that observation. In ipl\_dt, the SOLD\_PRICE has six observations at *x* \= $500,000 and one observation at *x* \= $525,000 so the ‘hump’ at *x* \= $500,000 will be six times the ‘hump’ at *x* \= $525,000.

Apart from the observation being treated as the centre of the kernel, each kernel has a parameter called bandwidth( ) . Bandwidth of the kernel determines the range of the neighbourhood values to which probability will be assigned. We can think of bandwidth as the standard deviation of the smoothening kernel which is to be used to estimate the PDF. A bigger bandwidth results in a shorter and wider ‘hump’, which spreads out farther from the centre and assigns more probability to the neighbouring values (Cai, 2013). By default, in density() and stat\_density(), the bandwidth parameter is set to bw.nrd0, and implements a rule-of-thumb for choosing the bandwidth of a Gaussian kernel density estimator. More details on the rule can be found with function ?stats::bw.nrd.

The following steps are used in estimating KDE:

**1.** Replace each observation with a normal (Gaussian) curve with the observation being the centre of the curve.

**2.** Total the individual values of the curves to compute the value of the density at each point of the given dataset. This will result in an overall density curve.

**3.** Normalize the resulting curve, so that the area under it is equal to 1.

**4.** The resulting curve is kernel PDF or density and is depicted by density plot.

To draw the density plot, we can use geom\_density which computes and draws kernel density estimate. geom\_density() internally uses stat\_density() in which some of the parameters playing an important role in estimating the PDF are set by default to:

**1.** kernel=“gaussian”. Type ?density on the console to get the list of all the kernel which can be passed.

**2.** bandwidth=“nrd0”

**3.** adjust = 1. The multiplicative factor by which bandwidth can be adjusted.

**4.** n=512. The number of equally spaced points at which the density is to be estimated, the value of *n* should be a power of two, one can use ?density for additional details.

With the above understanding of the KDE, let us generate some variations of density plots. Density plot for the outcome variable ‘SOLD PRICE’ is shown in **[Figure 3.21](#11_Chapter03.xhtml#fig3.21).**

![](images/page77-01.png)

**[Figure 3.22](#11_Chapter03.xhtml#fig3.22)** shows the density plot of the sold price by each PLAYING\_ROLE.

![](images/page77-02.png)![](images/page77-03.png)![](images/page78-01.png)![](images/page78-02.png)

**[Figure 3.23](#11_Chapter03.xhtml#fig3.23)** depicts the conditional density plot filled by PLAYING\_ROLE by setting the parameter position=“fill”.

![](images/page78-03.png)![](images/page79-01.png)

**Density plot** is a much more reliable visualization tool to understand the distribution of a numeric variable. The distribution is estimated using kernel density estimation technique. The variable can be passed as ‘x’ parameter in aesthetic mapping.

Conditional densities depict conditional distribution of a categorical variable with a numeric variable. In **[Figure 3.23](#11_Chapter03.xhtml#fig3.23)**, the probability that the PLAYING\_ROLE== W.Keeper will be SOLD at $100,000 is approximately 0.14 while that for PLAYING\_ROLE== Bowler is approximately 0.37.

The distribution of two different continuous variables can be shown by layering two geom\_density for the two continuous variables. **[Figure 3.24](#11_Chapter03.xhtml#fig3.24)** shows the density plot for SOLD\_PRICE and BASE\_PRICE.

![](images/page79-02.png)

#### 3.5.5 Box Plot

Box plot (aka Box and Whisker plot) is a graphical representation of numerical data that can be used to understand the variability of the data and the existence of outliers. In this section, we will discuss codes used to generate Box plot. Let us consider the variable SOLD\_ PRICE of the players. The steps which can be used to generate the box plot and identify outliers in data are as follows:

**1.** Arrange data in ascending order. The number of observations in SOLD\_PRICE, arranged in chronological order (ascending) is

![](images/page79-03.png)![](images/page80-01.png)

The count of number of observations in the sorted data is 130.

![](images/page80-02.png)

**2.** Calculate the median of the data. This is called as (quartile 2). If the number of observations in the data is n, then median is calculated using the following logic in which the data is arranged in ascending order:

• If n is odd, then the middle value is observation at (n+1)/2 position in the sorted data.

• If n is even, the middle value is the average of middle two numbers i.e. observation at ‘floor(n+1)/2’ position and ‘ceiling(n+1)/2’ position.

Since the data has 130 observations (even) in SOLD\_PRICE, it falls under the second rule. The middle value is the average of values at index position 65 floor((obs + 1)/2) and index position 66 ceiling((obs + 1)/2).

![](images/page80-03.png)

**3.** Calculate the median of the first half of the data. This is Q1 (quartile 1). In the ipl\_ sorted\_dt the number of observations in the first half is 64. Since this is an even number of observations, the second rule of step 2 applies.

![](images/page80-04.png)![](images/page81-01.png)

**4.** Calculate the median of the second half of the data. This is Q3 (quartile 3). In the ipl\_sorted\_dt the number of observations in second half is 64. Since this is an even number of observations, the second rule of step 2 applies.

![](images/page81-02.png)

**5.** The box joins Q1 to Q3 (contains middle 50% of data). The other statistics calculated are as follows:

**1.** Inter-quartile range (IQR) is the distance (difference) between the 3^(rd) quartile and 1^(st) quartile. The length of the box is equivalent to IQR. IQR is calculated as IQR = Q3 - Q1.

**2.** Lower interval fence which is LIF = Q1 - 1.5\*IQR

**3.** Upper interval fence which is UIF = Q3 + 1.5\*IQR

![](images/page81-03.png)

**6.** In the ipl\_sorted\_dt, the smallest observation greater than or equal to LIF is 20,000 (lower whisker) and the largest observation less than or equal to UIF is 135,000 (upper whisker). The whisker spreads from lower whisker to Q1 and Q3 to upper whisker. All observations outside the lower and upper whiskers are called outliers.

![](images/page82-01.png)

In ipl\_sorted\_dt, there are no outliers on the lower whisker side as there is no point outside the lower whisker. However, there are four unique values which are greater than the upper whisker. They are 1,500,000; 1,550,000; 1,600,000; 1,800,000.

Interpretation of box plot:

**1.** If the plot has wide box and long whiskers, then the data has a lot of variation.

**2.** If box is small and the whiskers are short, then the data has less variation and cluster together.

**3.** If box is small and the whiskers are long, then maybe the data has less variation, but may have some ‘outliers’.

The box plot on ipl\_dt can be created by using geom\_boxplot. **[Figure 3.25](#11_Chapter03.xhtml#fig3.25)** shows the box plot for SOLD\_PRICE. The outliers above the upper whisker are marked with black points.

![](images/page82-02.png)

The box plot can be split by another categorical feature. **[Figure 3.26](#11_Chapter03.xhtml#fig3.26)** shows a box plot by PLAYING\_ROLE.

![](images/page82-03.png)

**[Figure 3.26](#11_Chapter03.xhtml#fig3.26)** suggests that there are three outlier points in PLAYING\_ROLE as Batsman and one outlier in PLAYING\_ROLE as W. Keeper (wicket keeper).

![](images/page83-01.png)

#### 3.5.6 Correlation and Heatmap

In this section, we will discuss correlation and heatmap. The first step is to get the list of all numeric features in the ipl\_dt, which can be obtained using the following code snippet.

![](images/page83-02.png)

**[Table 3.6](#11_Chapter03.xhtml#tab3.6)** shows a 5 by 5 correlation matrix. We can find the correlation amongst the numeric features using the following code snippet:

![](images/page83-03.png)![](images/page83-04.png)

**[Table 3.7](#11_Chapter03.xhtml#tab3.7)** shows a lower triangle matrix by using upper.tri() functions from the base package.

![](images/page84-01.png)![](images/page84-02.png)

**Heatmap**, using tile object of ggplot, can be used to visualize a square matrix of numbers which can be passed a ‘x’ parameter in aesthetic mapping. The color code of the numbers can be in a gradient fill with lower values taking a lighter shade to higher value taking a darker shade of the color.

We can use geom\_tile() to generate a heatmap. As the correlation coefficient ranges from −1 to 1, the argument limit of function scale\_fill\_gradient2 is set as limit = c(-1,1). coord\_fixed() ensures that one unit on the horizontal axis is the same length as one unit on the vertical axis.

![](images/page84-03.png)

**[Figure 3.27](#11_Chapter03.xhtml#fig3.27)** shows the correlation heatmap between all the numeric features in the ipl\_dt. Some features such as total runs scored (TOTAL\_RUNS) are highly correlated with runs scored in Test cricket (T\_RUNS) and in ODIs (ODI\_RUNS\_S).

#### 3.5.7 Trend Plot

Trend plots are used to understand changes in the value over a period of time. Let us plot the average SOLD\_PRICE of players in different years in which auction was held. **[Table 3.8](#11_Chapter03.xhtml#tab3.8)** shows the number of players, in the ipl\_dt, who were auctioned in different years.

![](images/page84-04.png)![](images/page85-01.png)

The average sold price for these players is shown in **[Table 3.9](#11_Chapter03.xhtml#tab3.9):**

![](images/page85-02.png)

**TABLE 3.9** | Average sold price

| AUCTION\_YEAR || AVG\_SOLD\_PRICE |
| --- | --- |
| 2009 || 458,400 |
| --- | --- |
| 2008 || 492,067 |
| 2011 || 604,762 |
| 2010 || 290,000 |

We will use geom\_line() which connects the observations in order of the variable on the *x*\-axis.

**1.** If we use geom\_path(), it connects the observations in the order in which they appear in the data.

**2.** geom\_step() creates a stairstep plot, highlighting exactly when changes occur.

![](images/page85-03.png)![](images/page86-01.png)

**[Figure 3.28](#11_Chapter03.xhtml#fig3.28)** shows the trend for average sold price of players during different years of auction. Note that the data is a sample of players from different years and may not represent the actual trend. **[Figure 3.29](#11_Chapter03.xhtml#fig3.29)** shows the average sold price using geom\_path, which connects the observations in the order in which they appear in the data.

![](images/page86-02.png)![](images/page86-03.png)![](images/page87-01.png)

**[Figure 3.30](#11_Chapter03.xhtml#fig3.30)** shows the average sold price using geom\_step, which creates a stairstep plot and highlights when changes occur.

![](images/page87-02.png)

#### 3.5.8 Lay Out Panels in a Grid

We can create panel of plots using facet\_grid() from ggplot. Facet in general means ‘a particular aspect or feature of something’. When we say we want to create a plot with faceting variable as AGE and PLAYING\_ROLE, it means we want to visualize the plot with AGE and PLAYING\_ROLE as two more dimensions of the data.

facet\_grid(), forms a matrix of panels defined by row and column faceting variables (Anon, 2021). It is most useful when there are two discrete variables in the data and all combinations of the variables also exist. Let’s take the box plot from [Section 3.5.5](#11_Chapter03.xhtml#sec3.5.5) and create a facet grid with AGE and PLAYING\_ROLE as faceting variables.

![](images/page87-03.png)![](images/page88-01.png)

From **[Figure 3.31](#11_Chapter03.xhtml#fig3.31)**, we can see that there are three outliers in age group 2 category (players between 25 and 35 years):

**1.** 1 player with a PLAYING\_ROLE of Allrounder

**2.** 1 player with a PLAYING\_ROLE of Batsman

**3.** 1 player with a PLAYING\_ROLE of W. Keeper

We also have an outlier with age group 3 category (player with age greater than 35) and belongs to PLAYING\_ROLE as Batsman. Let us plot the scatter plot and facet it with AGE and PLAYING\_ROLE.

![](images/page88-02.png)

**[Figure 3.32](#11_Chapter03.xhtml#fig3.32)** shows the scatter plot between bowling average and strike rate for different PLAYING\_ROLE and AGE group. It is interesting to note that the W. Keeper seems to have bowled in some previous matches (bowling average and strike rate as performance measures of a bowler).

![](images/page89-01.png)

### Summary

• The objective of descriptive analytics is simple comprehension of data using data summarization, basic statistical measures, and visualization.

• Grammar of graphics, implemented using ggplot, can be used to create plots like histogram, distribution plots, box plots, scatter plot, heatmap, etc.

### Exercises

#### Use the Bollywood Dataset to Answer Questions 1 to 12

The data file *bollywood.csv* (link to the datasets is provided in the preface) contains box office collection and social media promotion information about movies released in 2013-2015 period. Following are the columns and their descriptions.

• *SlNo* - Release Date

• *MovieName* - Name of the movie

• *ReleaseTime* - Mentions special time of release. LW (Long weekend), FS (Festive season), HS (Holiday season), N (Normal)

• *Genre* - Genre of the film such as Romance, Thriller, Action, Comedy, etc.

• *Budget* - Movie creation budget

• *BoxOfficeCollection* - Box office collection

• *YoutubeViews* - Number of views of the YouTube trailers

• *YoutubeLikes* - Number of likes of the YouTube trailers

• *YoutubeDislikes* - Number of dislikes of the YouTube trailers

#### Use R Code to Answer the Following Questions

**1.** How many records are present in the dataset? Print the structure information (use str()) of the dataset.

**2.** How many movies got released in each genre? Which genre had highest number of releases? Sort number of releases in each genre in descending order.

**3.** How many movies in each genre got released in different release times like long weekend, festive season, etc. (Note: Do a cross tabulation between *Genre* and *ReleaseTime.)*

**4.** Which month of the year the maximum number movie releases are seen? (Note: Extract a new column called month from *ReleaseDate* column.)

**5.** Which month of the year typically sees most releases of high-budgeted movies, that is, movies with budget of 25 crore or more?

**6.** Which are the top 10 movies with maximum return on investment (ROI)? Calculate return on investment (ROI) as *(BoxOfficeCollection - Budget)/Budget.*

**7.** Do the movies have higher ROI if they get released on festive seasons or long weekend? Calculate the average ROI for different release times.

**8.** Draw a histogram and a distribution plot to find out the distribution of movie budgets. Interpret the plot to conclude if the most movies are high- or low-budgeted movies.

**9.** Compare the distribution of ROIs between movies with comedy genre and drama. Which genre typically sees higher ROIs?

**10.** Is there a correlation between box office collection and YouTube likes? Is the correlation positive or negative?

**11.** Which genre of movies typically sees more YouTube likes? Draw box plots for each genre of movies to compare.

**12.** Which of the variables among *Budget, BoxOfficeCollection, YoutubeView, YoutubeLikes, YoutubeDislikes* are highly correlated? Note: Draw pairwise scatter plot.

### Bibliography

**1.** Anon (2020), “A Layered Grammar of Graphics - Hadley WICKHAM”, Web address: [http://vita.had.co.nz/papers/layered-grammar.pdf](http://vita.had.co.nz/papers/layered-grammar.pdf), accessed on 10 May 2021.

**2.** Anon (2021), “kernel density estimation”, Web address: [https://en.wikipedia.org/wiki/Kernel\_density\_estimation](https://en.wikipedia.org/wiki/Kernel_density_estimation), accessed on 2021.

**3.** Anon (2021), “Facet\_wrap labels”, Web address: [https://www.xspdf.com/resolution/52295281.html](https://www.xspdf.com/resolution/52295281.html), accessed on 10 May 2021.

**4.** Cai E (2013), “Exploratory Data Analysis: Kernel Density Estimation - Conceptual Foundations | The Chemical Statistician (wordpress.com)’, Web address: [https://chemicalstatistician.wordpress.com/2013/06/09/exploratory-data-analysis-kernel-density-estimation-in-r-on-ozone-pollution-data-in-new-york-and-ozonopolis](https://chemicalstatistician.wordpress.com/2013/06/09/exploratory-data-analysis-kernel-density-estimation-in-r-on-ozone-pollution-data-in-new-york-and-ozonopolis)/, accessed on 10 May 2021.

**5.** Kumar UD and Ranjan K (2012), “Pricing of Players in the Indian Premier League”, Indian institute of management, Bangalore, available at Harvard Business Publishing Case Portal, Web address: [https://hbsp.harvard.edu/product/IMB379-PDF-ENG?Ntt=Pricing+of+players+in+the+Indian+premier+league&itemFindingMethod=Search](https://hbsp.harvard.edu/product/IMB379-PDF-ENG?Ntt=Pricing+of+players+in+the+Indian+premier+league&itemFindingMethod=Search)”, accessed on 10 May 2021.

**6.** Roshan B (2020), “Data Visualization with R”, available at Part 4: Data Visualization with R | Kaggle, Web address: [https://www.kaggle.com/benroshan/part-4-data-visualization-with-r](https://www.kaggle.com/benroshan/part-4-data-visualization-with-r), accessed on 5 May 2021.

**7.** Pradhan M and Kumar UD (2019), “Machine Learning Using Python”, Wiley, New Delhi.

**8.** Wilkinson L (2005), *“The Grammar of Graphics”* (2^(nd) ed.). Statistics and Computing, Springer, New York.

**9.** Wilkinson L, Anand A and Grossman R (2005), “Graph-Theoretic Scagnostics,” in IEEE Symposium on Information Visualization, 157-164.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#11_Chapter03.xhtml#ch3-fn1)Grammar of Graphics: [http://vita.had.co.nz/papers/layered-grammar.pdf](http://vita.had.co.nz/papers/layered-grammar.pdf)

[²](#11_Chapter03.xhtml#ch3-fn2)Source: [https://r4ds.had.co.nz/data-visualisation.html](https://r4ds.had.co.nz/data-visualisation.html)

 

 
| 

## Probability and Distributions

 || 

## 4

 |
| --- | --- |

*A flower falls, even though we love it; and a weed grows, even though we do not love it.*

**—Dogen Zenji**

LEARNING OBJECTIVES

After reading this chapter, you would be able to:

• Understand basic concepts in probability theory.

• Learn the concept of random variables and probability distributions.

• Understand different probability distributions such as binomial and normal distributions, and their applications in analytics.

• Learn how to derive insights from concepts such as mean, variance, probability distribution functions, confidence interval, etc.

• Learn how to formulate and carry out hypotheses tests such as one-sample Z-test, t-test, two-sample t-test, paired t-test, chi-square tests, and analysis of variance (ANOVA).

### 4.1 | Overview

Probability theory is one of the building blocks of analytics and machine learning algorithms. Analytics applications involve tasks such as the prediction of the probability of occurrence of an event, testing a hypothesis, building models to explain variations in a key performance index (KPI) that is of importance to the business such as profitability, market share, demand, etc. Many important tasks in analytics deal with uncertain events and it is essential to understand probability theory used to measure and predict the occurrence of uncertain events. This chapter introduces the concept of random variables and probability distributions and how they can be applied to solve organizational problems. We will also explore concepts of various discrete and continuous distributions, probability mass function, probability density function, and cumulative distribution functions. Finally, we will discuss hypothesis testing and its importance in feature selection in ML algorithms, understand the concept of significance (a) value, probability value (p-value) and various hypothesis tests such as Z-test, various t-tests, and chi-square goodness of fit tests.

### 4.2 | Probability Theory - Terminology

In this section, we will discuss the various terminologies used in probability theory.

#### 4.2.1 Random Experiment

In machine learning, we mostly deal with uncertain events. Random experiment is a test in which the outcome is not known with certainty. That is, the output of a random experiment cannot be predicted with certainty (Pradhan and Kumar, 2019). Revenue generation from a product, loan default, and the outcome of a sports event are examples of random experiments.

#### 4.2.2 Sample Space

Sample space is the universal set that consists of all possible outcomes of a random experiment. It is usually represented using the letter S and individual outcomes are called the elementary events. Sample space can be finite or infinite. A few random experiments and their sample spaces are described below (Kumar, 2017):

Experiment: Outcome of a college application. The corresponding Sample Space = *S* = {admitted, not admitted}

Experiment: Predicting customer churn at an individual customer level. The corresponding Sample Space = *S* = {Churn, No Churn}

Experiment: Television Rating Point (TRP) for a television program and the corresponding Sample Space = *S \= X* | *X* ∈ *R,0* ≤ *X* ≤ 100; that is, *X* is a real number that can take any value between 0 and 100 percentage.

#### 4.2.3 Event

Event (E) is a subset of a sample space and probability is usually calculated with respect to an event. Examples of events include (Kumar, 2017):

**1.** Percentage of cancellation of orders placed at an e-commerce portal site exceeding 10%.

**2.** Percentage of fraudulent credit card transactions exceeding 1%.

**3.** The life of a capital equipment less than 1 year.

**4.** Number of warranty claims less than 100 for a vehicle manufacturer with a fleet of 2,000 vehicles under warranty period of 2 years.

### 4.3 | Random Variable

Random variables play an important role in describing, measuring, and analysing uncertain events such as customer churn, employee attrition, demand for a product, and so on (Kumar). It is a function that maps every outcome in the sample space to a real number and provides the flexibility to describe an event. Random variables can be classified as discrete or continuous, depending on the values they can take. If the random variable *X* can assume only a finite or countably infinite set of values, then it is called a discrete random variable. Examples of discrete random variables are:

**1.** Credit rating (usually classified into different categories such as low, medium, and high or using labels such as AAA, AA, A, BBB, etc.).

**2.** Number of orders received at an e-commerce retailer which can be countably infinite.

**3.** Customer churn \[the random variables take binary values: (a) Churn and (b) Do not churn\].

**4.** Fraud \[the random variables take binary values: (a) Fraudulent transaction and (b) Genuine transaction\].

A random variable *X* which can take a value from an infinite set of values is called a continuous random variable. Examples of continuous random variables are listed below:

**1.** Market share of a company (which takes any value from an infinite set of values between 0 and 100%).

**2.** Percentage of attrition among employees of an organization.

**3.** Time to failure of an engineering system.

**4.** Time taken to complete an order placed at an e-commerce portal.

Discrete random variables are described using Probability Mass Function (PMF) and Cumulative Distribution Function (CDF). PMF is the probability that a random variable *X* takes a specific value k; for example, the number of fraudulent transactions at an e-commerce platform is equal to 10, written as *P(X* = 10). CDF is the probability of a random variable taking a value less than or equal to 10, which is written as *P(X* ≤ 10).

Continuous random variables are described using Probability Density Function (PDF) and CDF. PDF is the probability that a continuous random variable takes a value in a small neighbourhood of *x* and is given by:

![](images/page93-01.png)

The CDF of a continuous distribution is the probability that the random variable takes a value less than or equal to a value ‘a. Mathematically,

![](images/page93-02.png)

CDF described in [Eq. (4.2)](#12_Chapter04.xhtml#eq4.2) is the area under the PDF curve till value of *X* = a. Note that PDF is not a probability value. Instead, it is a limiting value of probability and thus can take values greater than 1. CDF, on the other hand, is a probability and its value lies between 0 and 1. In the following sections, we will discuss the concepts of various discrete and continuous distributions and how to apply them to real world scenarios.

### 4.4 | Binomial Distribution

Binomial distribution is discrete probability distribution and has several applications in many business contexts. A random variable X is said to follow a binomial distribution when (Kumar, 2017):

**1.** The random variable can have only two outcomes - success and failure (also known as Bernoulli trials).

**2.** The objective is to find the probability of getting *x* successes out of *n* trials.

**3.** The probability of success is*p* and thus the probability of failure is (1 -p).

**4.** The probability *p* is constant and does not change between trials.

Success and failure are generic terminologies used in binomial distribution, we have to infer success and failure based on the context:

**1.** Customer churn where the outcomes are: (a) Customer churn and (b) No customer churn.

**2.** Fraudulent insurance claims where the outcomes are: (a) Fraudulent claim and (b) Genuine claim.

**3.** Loan repayment default by a customer where the outcomes are: (a) Default and (b) No default.

The PMF of the binomial distribution (probability that the number of success will be exactly *x* out of *n* trials) is given by

![](images/page93-03.png)

where,

![](images/page93-04.png)

The cumulative distribution function of a binomial distribution is given by

![](images/page94-01.png)

#### 4.4.1 Example of Binomial Distribution Using R

Fashion Trends Online (FTO) is an e-commerce company selling women’s apparel. It is observed that 10% of its customers return items purchased for many reasons (size, colour, and material mismatch). On a specific day, 20 customers purchased items from FTO. Calculate:

**1.** Probability that exactly five customers will return the items.

We have to use [Eq. (4.3)](#12_Chapter04.xhtml#eq4.3) to calculate this probability. The corresponding R code is

![](images/page94-02.png)

dbinom() takes three parameters:

**1.** expected number of successful trials (5)

**2.** number of trials (20)

**3.** probability of success (0.1)

Note, the values in the bracket indicate the value of the parameters for the above example. The probability that exactly five customers will return the items is approximately 3%.

**2.** Probability that a maximum of five customers will return the items.

We have to use [Eq. (4.4)](#12_Chapter04.xhtml#eq4.4) to calculate this probability and the corresponding R code is

![](images/page94-03.png)

pbinom with lower.tail = TRUE returns *P(X* ≤ x).

**3.** Probability that more than five customers will return the items purchased by them. In this case, we have to calculate 1 - F(x). The corresponding code is

![](images/page94-04.png)

pbinom with lower.tail = FALSE returns *P*(*X > x*).

**4.** Average number of customers who are likely to return the items and the variance and the standard deviation of the number of returns.

**1.** Average of a binomial distribution is given by *n* \* *p*

**2.** Variance of the binomial distribution is given by *n* \* *p* \* (1 - p)

![](images/page95-01.png)

### 4.5 | Poisson Distribution

In many situations, we might be interested in calculating the number of events that may occur over a period. For example, the number of cancellation of orders by customers at an e-commerce portal, number of customer complaints, number of cash withdrawals at an ATM, number of typographical errors in a book, number of potholes on Bengaluru roads, etc., involve counting the events over a period of time (Kumar, 2017). To find the probability of the number of events, we use Poisson distribution. The probability mass function of a Poisson distribution is given by

![](images/page95-02.png)

where λ is the rate of occurrence of the events per unit of measurement (in many situations the unit of measurement is likely to be time).

The corresponding cumulative distribution function *F*(*x*) is given by

![](images/page95-03.png)

#### 4.5.1 Example of Poisson Distribution Using R

The number of calls received by a call centre follows a Poisson distribution at 10 per hour.

**1.** Calculate the probability that the number of calls will be a maximum of five.

We have to use [Eq. (4.6)](#12_Chapter04.xhtml#eq4.6) where *x* = 5 and λ = 10. The corresponding R code is

![](images/page95-04.png)

**2.** Calculate the probability that the number of calls over a three-hour period will exceed 30.

Since the average calls per hour is 10 (λ = 10), and we are interested in calls over a span of 3 hours, the mean number of calls over 3 hours is λ*t* = 30. The probability that the number of calls will be more than 30 is given by

![](images/page95-05.png)

### 4.6 | Exponential Distribution

Exponential distribution is a single-parameter continuous distribution traditionally used for modelling time to failure of electronic components. It represents a process in which events occur continuously and independently at a constant rate (Kumar, 2017).

The probability density function is given by

![](images/page96-01.png)

The cumulative distribution is given by

![](images/page96-02.png)

where,

**1.** The parameter *l* is the scale parameter and represents the rate of occurrence of the event

**2.** Mean of exponential distribution is given by 1/A.

#### 4.6.1 Example of Exponential Distribution Using R

The time to failure of an avionic system follows an exponential distribution with a mean time between failures (MTBF) of 1,000 hours (X *\=* 1/1,000).

**1.** Calculate the probability that the system will fail before 1,000 hours.

We have to calculate F(x), where *x* = 1,000 and λ = 1/1,000. The corresponding R code is

![](images/page96-03.png)

**2.** Calculate the probability that it will not fail up to 2,000 hours.

We have to calculate 1 - F(x), where *x* = 2,000 and λ = 1/1,000. The corresponding R code is

![](images/page96-04.png)

### 4.7 | Normal Distribution

Normal distribution, also known as Gaussian distribution, is one of the most popular continuous distributions in the field of analytics, especially due to its use in multiple contexts. It is popularly known as bell curve. The PDF and CDF of normal distribution are given in equations 4.9 and 4.10.

![](images/page96-05.png)![](images/page96-06.png)

In [Eq. (4.9)](#12_Chapter04.xhtml#eq4.9), µ and σ are mean and standard deviation, respectively.

#### 4.7.1 Example of Normal Distribution

To understand normal distribution and its application, we will use daily returns of stocks traded at the BSE (Bombay Stock Exchange). Imagine a scenario where an investor wants to understand the risks and returns associated with various stocks before investing in them (Pradhan and Kumar, 2019). For this analysis, we will evaluate two stocks:

**1.** Pfizer: [https://in.finance.yahoo.com/quote/PFE](https://in.finance.yahoo.com/quote/PFE)/

**2.** Glaxo: [https://in.finance.yahoo.com/quote/GLAXO.NS](https://in.finance.yahoo.com/quote/GLAXO.NS)/

First, we will load and prepare the data before getting back to the application of normal distribution.

![](images/page97-01.png)

Date column will be treated as a factor (feature) variable. **[Table 4.1](#12_Chapter04.xhtml#tab4.1)** shows Pfizer data witl ‘Date’ column typecast to correct data type. The table also has ‘Month’ and ‘Year’ columi extracted from the Date variable. However, **[Table 4.1](#12_Chapter04.xhtml#tab4.1)** shows only the first five columns from a readability perspective.

![](images/page97-02.png)

Pfizer raw data, has records from June 1972 **([Table 4.1](#12_Chapter04.xhtml#tab4.1))**, whereas Glaxo stock data is available from July 2002. In order to compare both stocks from the same timeline, we will use matching subset from Pfizer dataframe to have stock prices from July 2002. Moreover, our analysis will involve only daily Close prices, so we will select Date and Close columns from the dataframe. Let us perform the below operation to prepare the data:

**1.** Subset raw\_pfizer\_df to get Date and Close price from July 2002 onwards

**2.** Remove rows with NA values

**3.** Rename Close column to pfizer\_close

**4.** Scale the pfizer\_close column

![](images/page97-03.png)![](images/page98-01.png)

**[Table 4.2](#12_Chapter04.xhtml#tab4.2)** gives a snapshot of the four operations applied using the following code snippet:

![](images/page98-02.png)

**[Table 4.3](#12_Chapter04.xhtml#tab4.3)** gives a snapshot of the Glaxo data which was read using the following code:

![](images/page98-03.png)

Let us perform some operations to prepare the data:

**1.** Subset raw\_glaxo\_df to get Date and Close price.

**2.** Remove rows with NA values.

**3.** Rename Close column to glaxo\_close.

**4.** Scale the glaxo\_close column.

**[Table 4.4](#12_Chapter04.xhtml#tab4.4)** shows the dataset after having applied the above four steps:

![](images/page98-04.png)![](images/page98-05.png)

**TABLE 4.4** | Glaxo data

| Date || glaxo\_close |
| --- | --- |
| 2002-07-01 || 182.600 |
| --- | --- |
| 2002-07-02 || 183.000 |
| 2002-07-03 || 183.700 |
| 2002-07-04 || 185.750 |
| 2002-07-05 || 182.375 |

#### 4.7.2 Visualize Data

Visualizing the daily close prices will show how stock prices have moved over time. To show the trend of close price, the records should be ordered by time (Pradhan and Kumar, 2019). As the dataframes have a date column, we will use dplyr package to join the pfizer\_df and glaxo\_df.

![](images/page99-01.png)

dplyr uses SQL style database syntax for join operation. It supports different join operations, and we will use left join operation.

A left join will include everything on the left data frame and all rows that match from the right data frame. If the join columns have the same name, then query is left\_ join(x, y). If columns do not have the same name, then ‘by’ argument is needed, for example, left\_join(x, y, by = c(“df1ColName” = “df2ColName”)). **[Table 4.5](#12_Chapter04.xhtml#tab4.5)** shows the snapshot of the merged dataframe:

![](images/page99-02.png)

We will visualize both stock prices (Pfizer and Glaxo) in the same plot. In order to do so, we will flatten **[Table 4.5](#12_Chapter04.xhtml#tab4.5)** using tidyr package. **[Table 4.6](#12_Chapter04.xhtml#tab4.6)** shows the flattened data with the first five observations.

![](images/page99-03.png)![](images/page99-04.png)![](images/page100-01.png)

We will use ggplot package to visualize data in **[Table 4.6](#12_Chapter04.xhtml#tab4.6).**

![](images/page100-02.png)

It can be observed from **[Figure 4.1](#12_Chapter04.xhtml#fig4.1)** that there is an upward trend in the close price of Glaxo during the 2007-2010 period. Pfizer had a downward trend during the same time, followed by an upward trend since 2011.

#### 4.7.3 Analyze Stock Data

What if I am a short-term (intraday) investor interested in understanding the following characteristics of these stocks?

**1.** What is the expected daily rate of return of these stocks?

**2.** Which stocks have higher risk or volatility as far as daily returns are concerned?

**3.** What is the expected range of return for 95% confidence interval?

![](images/page100-03.png)

**4.** Which stock has a higher probability of making a daily return of 2% or more?

**5.** Which stock has a higher probability of making a loss (risk) of 2% or more?

To answer the above questions, we must find out the behaviour of daily returns (we will refer to this as ‘gain’ henceforth) on these stocks. Using [Eq. 4.11](#12_Chapter04.xhtml#eq4.11), **[Table 4.7](#12_Chapter04.xhtml#tab4.7)** and **[Table 4.8](#12_Chapter04.xhtml#tab4.8)** show the gain calculated as a percentage change in close price, from the previous day’s close price.

![](images/page101-01.png)

The following code snippet was used to generate **[Table 4.7](#12_Chapter04.xhtml#tab4.7)** (Glaxo gain) and **[Table 4.8](#12_Chapter04.xhtml#tab4.8)** (Pfizer gain):

![](images/page101-02.png)

The first-day gain is shown as NA, as there is no previous day to calculate it. We can drop this record using na.omit() method. **[Table 4.9](#12_Chapter04.xhtml#tab4.9)** shows the data after removing NA record and by merging **[Tables 4.7](#12_Chapter04.xhtml#tab4.7)** and **[4.8](#12_Chapter04.xhtml#tab4.8)**. Note, **[Table 4.9](#12_Chapter04.xhtml#tab4.9)** shows only five columns for readability.

![](images/page101-03.png)![](images/page101-04.png)![](images/page101-05.png)![](images/page102-01.png)

**[Table 4.10](#12_Chapter04.xhtml#tab4.10)** is obtained after flattening **[Table 4.9](#12_Chapter04.xhtml#tab4.9). [Table 4.10](#12_Chapter04.xhtml#tab4.10)** has only the gain column for both stocks (note: **[Table 4.10](#12_Chapter04.xhtml#tab4.10)** is a flattened file which shows first five observations). The reason behind flattening **[Table 4.9](#12_Chapter04.xhtml#tab4.9)** was to make it useful for plotting the graph.

![](images/page102-02.png)

We can visualize data in **[Table 4.10](#12_Chapter04.xhtml#tab4.10)** using the ggplot package with the following code snippet.

![](images/page102-03.png)

**[Figure 4.2](#12_Chapter04.xhtml#fig4.2)** shows that the daily gain is highly random and fluctuates around 0.00. The gain remains mostly within a small range.

We can draw distribution plot of gain of both Pfizer and Glaxo stocks to get better insights.

![](images/page102-04.png)

Gain **([Figure 4.3](#12_Chapter04.xhtml#fig4.3))** seems to be normally distributed for both stocks with mean around 0.00. Glaxo seems to have higher variance than Pfizer. (Note: This distribution has a long tail, but we will assume normal distribution for simplicity.)

![](images/page102-05.png)![](images/page103-01.png)![](images/page103-02.png)

#### 4.7.4 Mean and Variance

Normal distribution has two parameters: the mean of the distribution µ and the variance σ². The mean of a normal distribution can be estimated from a sample using [Eq. (4.12)](#12_Chapter04.xhtml#eq4.12).

![](images/page103-03.png)

Variance of a normal distribution from a sample data is given by

![](images/page104-01.png)

Standard deviation is square root of variance and is denoted by σ. Methods mean() and sd() on dataframe columns return mean and standard deviation, respectively.

![](images/page104-02.png)

From **[Figure 4.3](#12_Chapter04.xhtml#fig4.3)**, we can infer that the expected daily rate of return (gain) is around 0% for both stocks. Moreover, from the above code snippet, we see that, Glaxo stock comes with a higher risk as the standard deviation of Glaxo is 4%, whereas the standard deviation for Pfizer is 2%.

#### 4.7.5 Confidence Interval

Confidence interval is the interval in which the average return is likely to lie with a certain probability (usually 95%). To find 95% confidence interval for return, we need to calculate the value gain for two standard deviations away from mean on both sides of the distribution, that is µ ± 2σ. Under a normal distribution, the area under two standard deviations form mean (i.e. µ ± 2σ) is approximately 95%. We can use gmodels package to obtain the confidence interval (install.packages(‘gmodels’)).

![](images/page104-03.png)

Returns for 95% confidence interval gain of Glaxo is between −3.316506 × 10^(−06) and 2.395655 × 10^(−03). Returns for Pfizer for 95% confidence interval is (−0.00051, 0.00098).

![](images/page105-01.png)

#### 4.7.6 Cumulative Probability Distribution

To understand the probability that the gain will be higher than 2% or more, we need to find out probability that gain can take values more than 0.02 (i.e. 2%). The probability density function, *f (x[i]*), is defined as probability that the value of random variable *X* lies between an infinitesimally small interval defined by *x[i]* and *x[i] +* δ*x.* The corresponding equation is given in [Eq. 4.9](#12_Chapter04.xhtml#eq4.9). Cumulative distribution function, F(a), is the area under the probability density function up to *X* = *a* ([Eq. 4.10](#12_Chapter04.xhtml#eq4.10)). The cumulative density function, a normal variable, is as shown in **[Figure 4.4](#12_Chapter04.xhtml#fig4.4).**

To calculate the probability that the stocks gain will be less than or equal to 0.02, cumulative distribution function can be used to calculate the area of the distribution from the extreme left point up to 0.02. pnorm() returns cumulative distribution for a normal distribution. The parameter lower.tail in pnorm is set to TRUE by default. This means the calculated probability is for *P\[X* ≤ x\]. Since we are looking for probability of gain to be more than 0.02, we will set lower.tail = FALSE (implying *P*\[*X* > x\]).

![](images/page105-02.png)

Cumulative distribution function value indicates that Glaxo has a 32% chance, whereas Pfizer has only a 14% chance, of making a gain of 2% or higher.

![](images/page105-03.png)

Probability distributions are fundamental to statistics, just like data structures are to computer science. Apart from the distributions discussed, following are a few other important distributions (Pradhan and Kumar, 2019):

**1.** **Beta Distribution:** It is a continuous distribution which can take values between 0 and 1.

**2.** **Gamma Distribution:** It is used as a sophisticated waiting times models. We can model time until the occurrence of next *n* events using Gamma distribution.

**3.** **Weibull Distribution:** Exponential distribution is a special case of Weibull distribution. In exponential distribution, the rate of occurrence of an event is constant. But using Weibull distribution, we can model increasing (or decreasing) rates of occurrence of an event over time.

**4.** **Geometric Distribution:** If the binomial distribution is about ‘How many successes?’, then the geometric distribution is about ‘How many failures until a success?’

### 4.8 | Central Limit Theorem

The sample mean ![](images/pageIn_ch4-01.png)derived in repeated sampling from a population with mean *m* and standard deviation σ will follow a normal distribution with mean ![](images/pageIn_ch4-02.png)and standard deviation ![](images/pageIn_ch4-03.png)for large sample of size *n* > 30. The distribution of mean values of different samples drawn from a population is called sampling distribution.

Let us demonstrate central limit theorem using the closed price for Pfizer stock data. Let us graph density plot for the closed price.

![](images/page106-01.png)

**[Figure 4.5](#12_Chapter04.xhtml#fig4.5)** is the density plot for the closed price for Pfizer stock data, which does not seem to be normally distributed. Let us compute mean, standard deviation for the closed price from pfizer\_df. The average closing price is 28.065, and the standard deviation is 1.3452.

![](images/page106-02.png)![](images/page107-01.png)

Let us draw 500 random samples of 30 observations (closed price) from the pfizer\_df and store the average of the closed price of the 500 samples generated in samDist:

![](images/page107-02.png)

Next we will compute the sample mean and standard deviation.

![](images/page107-03.png)

We can infer from the output that the mean of sampling distribution is 28.11 and standard deviation is 1.3579. That is, the central limit theorem holds good on the Pfizer stock data. In general, the central limit theorem will hold good on any data when samples generated in repeated sample is >30. As the sample size increases and number of repeated samples increases, the sample mean will approach population mean.

We will plot the samDist.

**Central limit theorem** is the building block for hypothesis testing and lot of other statistical learning algorithms techniques.

![](images/page107-04.png)

From **[Figure 4.6](#12_Chapter04.xhtml#fig4.6)**, we can conclude that the sample mean approximately follows normal distribution.

### 4.9 | Hypothesis Testing

Hypothesis is a claim. The objective of hypothesis testing is to either reject or retain a null hypothesis (existing knowledge or belief) with the help of newly collected evidences or samples. Hypothesis testing consists of two complementary statements called null hypothesis and alternative hypothesis. Null hypothesis stands for no relationship or no difference (that is, it stands for existing knowledge or belief) and alternate hypothesis is what we intend to establish using evidence (samples). Alternative hypothesis is also known as research hypothesis. Hypothesis tests are broadly classified into parametric tests and non-parametric tests. Parametric tests are about population parameters of a distribution such as mean, proportion, standard deviation, etc. Non-parametric tests are not about parameters, but about other characteristics such as independence events or data following certain distribution such as normal distribution. Some examples of null hypothesis are as follows:

![](images/page108-01.png)

**1.** Children who drink the health drink Complan (a health drink owned by Heinz in India) are likely to grow taller.

**2.** Women take more selfies than men (Freier, 2016).

**3.** Vegetarians miss few flights (Siegel, 2016).

**4.** Smokers are better salespeople.

The following steps are used in hypothesis test (Kumar, 2017):

**1.** Define null and alternative hypotheses. Hypothesis is described using a population parameter, that is, mean, standard deviation, etc., in case of parametric hypothesis testing. Normally, *H[0]* is used to denote null hypothesis and *H[a]* hypothesis for alternate.

**2.** Identify the test statistic to be used for testing the validity of the null hypothesis, e.g. *Z*\-test or *t*\-test.

**3.** Decide the criteria for rejection and retention of null hypothesis. This is called significance value or α*.* Typical value used for α is 0.05.

**4.** Calculate the *p*\-value (probability value), which is the conditional probability of observing the test statistic value when the null hypothesis is true. We will use the functions provided in scipy.stats module for this. *P*\-value acts as an index, smaller *p*\-value indicates that there is a strong evidence against null hypothesis.

**5.** Take the decision to reject or retain the null hypothesis based on the *p*\-value and significance value α*.* When the *p*\-value is less than the significance value, null hypothesis is rejected. When the *p*\-value is greater than or equal to the significance value, null hypothesis is retained (failed to reject).

For detailed understanding of hypothesis test, refer to [Chapter 6](#14_Chapter06.xhtml) of the book *Business Analytics: The Science of Data-Driven Decision Making* by U. Dinesh Kumar (2017).

We will be using the following notations:

**1.** *m* - Population mean

**2.** *a* - Population standard deviation

**3.** *X* - Sample mean

**4.** *S* - Sample standard deviation

**5.** *n* - Sample size

In the next few sections, we will use a few examples to conduct hypothesis tests.

#### 4.9.1 One Sample Z-Test

One-sample *Z*\-test is used when:

**1.** Testing the value of population mean, when population standard deviation is known.

**2.** The population is a normal distribution, the assumption of normal distribution can be relaxed for large samples *(n* > 30).

*Z*\-Statistic is calculated as

![](images/page109-01.png)

**Example 4.1**

A passport office claims that passport applications are processed within 30 days of submitting all necessary documents. The file passport.csv **([Table 4.11](#12_Chapter04.xhtml#tab4.11))** contains processing time of 40 passport applicants. The population standard deviation of the processing time is 12.5 days. Conduct a hypothesis test at significance level α = 0.05 to verify the claim made by the passport office.

![](images/page109-02.png)

**TABLE 4.11** | Passport data

| processing\_time |
| --- |
| 16 |
| --- |
| 16 |
| 30 |
| 37 |
| 25 |
| 22 |

Let’s first define the hypothesis, if *m* is population mean, that is, mean processing time of passports, then:

**1.** *H[0]* : µ ≥ 30

**2.** *H[a]* : µ < 30

We will conduct a *Z*\-test for this hypothesis test. *Z*\-test is not available as a function in *r* base and thus below is the custom function to calculate the *Z* statistic value and corresponding *p*\-value.

![](images/page109-03.png)![](images/page110-01.png)

As the *p*\-value is more than 0.05, the null hypothesis is retained, that is, the mean processing time is more than 30 days.

In this example, we see there is a 6.77% probability of observing a random sample at least as extreme as the observed sample. Since 6.77% is greater than significance value 5%, there is not enough evidence to reject null hypothesis. The null hypothesis is retained, and it can be concluded that the average processing time of passports is greater than or equal to 30 days.

#### 4.9.2 One-Sample Mest

The one-sample *t*\-test is used when the population standard deviation is unknown and is estimated from the sample. The *t*\-statistic value is given by:

![](images/page110-02.png)

**Example 4.2**

Aravind Productions (AP) is a newly formed movie production house based out of Mumbai, India. AP was interested in understanding the production cost for a Bollywood movie. The industry believes the production house will require at least INR 500 million (50 crore) on average. It is assumed that the Bollywood movie production cost follows normal distribution. Production costs of 40 Bollywood movies in millions of rupees are given in bollywoodmovies.csv file **([Table 4.12](#12_Chapter04.xhtml#tab4.12)).** Conduct an appropriate hypothesis test at α = 0.05 to check whether the belief about average production cost is correct.

![](images/page110-03.png)

Let’s first define the hypothesis, if *m* is population mean then:

**1.** *H[0]* : */j*≤ 500

**2.** *H[a]* : *v >* 500

We will conduct a *t*\-test for this hypothesis test using *t*\-test function in *r* base.

![](images/page110-04.png)

**TABLE 4.12** | Bollywood data

| production\_cost |
| --- |
| 601 |
| --- |
| 627 |
| 330 |
| 364 |
| 562 |
| 353 |

This returns −2.2845 value for *t*\-statistics and 0.0278 for *p*\-value. This implies the sample mean is less than (to the left of) population mean and has only a 2.7% probability of being part of the distribution with a population mean of 500. As *p*\-value is less than 0.05, we can conclude that sample mean rejects that the production cost is at least 500.

#### 4.9.3 Two-Sample *t*\-Test

Two-sample *t*\-test is used to test the difference between two population means, in which standard deviations of populations are unknown. The parameters are estimated from the samples.

**Example 4.3**

A company makes a claim that children (in the age group 7 to 12) who consume their health drink will grow taller by 1.2 cm more compared to children who don’t. Data in **[Tables 4.13](#12_Chapter04.xhtml#tab4.13)** and **[4.14](#12_Chapter04.xhtml#tab4.14)** shows average increase in height over a 1-year period from two groups: one drinking the health drink, the other not doing so. At α = 0.05, test whether the increase in height for children who drink the health drink is different from those who do not.

Let’s read the files and calculate the average height of children in the two samples.

![](images/page111-01.png)

**TABLE 4.13** | Health drink (yes)

| height\_increase |
| --- |
| 8.6 |
| --- |
| 5.8 |
| 10.2 |
| 8.5 |
| 6.8 |
| 9.4 |

![](images/page111-02.png)

**TABLE 4.14** | Health drink (no)

| height\_increase |
| --- |
| 5.3 |
| --- |
| 9.0 |
| 5.7 |
| 5.5 |
| 5.4 |
| 7.2 |

![](images/page112-01.png)

The height difference in the mean value of the two samples is 1.48. Let us perform a two-sample *t*\-test to understand if they are statistically different. The hypothesis is

**1.** *H*[0]: The average increase in height for children who drink health drink is the same as the average increase in height for children who do not drink health drink, that is, µ[*diff*] = 0

**2.** *H[a]:* The average increase in height for children who drink health drink is different from the average increase in height for children who do not drink health drink, that is, µ[*diff*] ≠ 0

![](images/page112-02.png)

Since the p-value is less than the threshold (0.05), we reject the null hypothesis. Thus, the average increase in height for children who drink health drink is different from the average increase in height for children who do not drink health drink.

#### 4.9.4 Paired Sample t-Test

In many contexts, we would like to analyze whether an intervention (or treatment) such as training programs, marketing promotions, treatment for specific illness, and lifestyle changes may have significantly changed population parameter values such as mean before and after the intervention. The objective in this case is to check whether the difference in the parameter values is statistically significant before and after the intervention or between two different types of interventions. This is called paired sample *t*\-test and is used to compare two different interventions applied on the same samples. Consider the following example for a paired *t*\-test:

The file breakups.csv contains alcohol consumption before and after the break-up **([Table 4.15](#12_Chapter04.xhtml#tab4.15)).** Conduct a paired *t*\-test to check whether alcohol consumption is more after the break-up at 95% confidence (α = 0.05).

![](images/page112-03.png)

**TABLE 4.15** | Breakup data

| Before\_Breakup || After\_Breakup |
| --- | --- |
| 470 || 408 |
| --- | --- |
| 354 || 439 |
| 496 || 321 |
| 351 || 437 |
| 349 || 335 |
| 449 || 344 |

![](images/page113-01.png)

The alcohol consumption difference in the two samples is 11.5. Let’s perform a paired two-sample f-test to understand if they are statistically different. The hypothesis is:

**1.** *H[0]:* The average alcohol consumption before break-up is same as the average alcohol consumption after break-up, that is, µ[*diff = 0*]

**2.** *H[a]:* The average alcohol consumption before break-up is not same as the average alcohol consumption after break-up, that is, µ[*diff*] ≠ 0

![](images/page113-02.png)

Since the *p*\-value is more than the threshold (0.05), we retain the null hypothesis. There is no change in alcohol consumption pattern before and after break-up.

#### 4.9.5 Chi-Square Goodness of Fit Test and Test of Independence

Chi-square goodness of fit test is a non-parametric test used to compare the observed distribution of data with the expected distribution of data to decide whether there is any statistically significant difference between the observed distribution and a theoretical distribution. Chi-square statistics is given by (Kumar, 2017):

![](images/page113-03.png)

where, *O[i]* is observed frequency and *E[i]* is expected frequency of the *i*^(th) category. Expected frequency is calculated based on the hypothesized distribution. Chi-square of independence checks whether two variables dependent or independent **(Example 4.4).**

**Example 4.4**

Hanuman Airlines (HA) operated daily flights to several Indian cities. One of the hypotheses in catering operations is that food preferences of passengers from different zones in India are different. Captain Cook, the operations manager of HA, collected a sample of 2,500 passengers to analyze food preferences **([Table 4.16](#12_Chapter04.xhtml#tab4.16)).**

Conduct a chi-square test to check whether food preferences are statistically different is true at α = 0.05.

![](images/page114-01.png)

Let us frame the null and alternate hypotheses:

**1.** *H[0]*: Food preference does not change with zone, that is, food preference and zone are independent.

**2.** *H[a]*: Food preference is dependent on the zone.

![](images/page114-02.png)

The expected values are computed and stored:

![](images/page114-03.png)

Using [Equation 4.16](#12_Chapter04.xhtml#eq4.16), we can see that the expected number of cases for Veg\_North should be 940\*546/2500 = 205.30. If we want to know the most contributing observation to the overall chi-square value, we can calculate chi-square statistics for each observation:

![](images/page114-04.png)

where *r* is the Pearson residual.

![](images/page114-05.png)![](images/page114-06.png)

A value of 2.9 suggests that South zone’s preference of vegetarian food is higher whereas they do not prefer diabetic food (−2.77). Let us see the final result:

![](images/page115-01.png)

The degree of freedom is calculated as (row-1)\*(col-1). In the meals\_df we have four rows and as many columns. The *p*\-value is less than 0.05, which implies that food preference is dependent on the zone.

### 4.10 | Analysis of Variance (ANOVA)

Sometimes, it may be necessary to conduct a hypothesis test to compare mean values simultaneously for more than two groups (samples) created using a factor (or factors). For example, a marketer might desire to understand the impact of three different discount values (such as 0%, 10%, and 20% discount) on average sales (Kumar, 2017).

ONE-WAY ANOVA (Analysis of Variance) can be used to study the impact of a single treatment (also known as factor) at different levels (thus forming different groups) on a continuous response variable (or outcome variable). The null and alternative hypotheses for one-way ANOVA for comparing three groups are given by

**1.** *H*[0]: *μ*[1] = *μ*[2] = *μ*[3]

**2.** *H[A]*: Not all *m* values are equal

where *µ*[1], *µ*[2], *µ*[3] are mean of each group. Note that the alternative hypothesis, not all *µ* values are equal, implies that some of them could be equal. An important assumption of ANOVA test is that the data is normally distributed and the variance across groups is homogeneous.

**Example 4.5**

Ms Rachael Khanna, the brand manager of ENZO detergent powder at the ‘one stop’ retail, was interested in understanding whether price discounts have any impact on the quantum of sales. To that end, discounts of 0% (no discount), 10%, and 20% were offered on randomly selected days. The quantity (in kilograms) of ENZO sold in a day under different discount levels is shown in **[Table 4.17](#12_Chapter04.xhtml#tab4.17).** Conduct a one-way ANOVA to check whether discount had any significant impact on the average sales quantity at α = 0.05 (file name: onestop.csv).

![](images/page115-02.png)![](images/page115-03.png)

**TABLE 4.18** | Onestop flattened data

| percent\_discount || qty\_sold |
| --- | --- |
| discount\_0 || 39 |
| --- | --- |
| discount\_0 || 32 |
| discount\_0 || 25 |
| discount\_0 || 25 |
| discount\_0 || 37 |
| discount\_0 || 28 |

The below code snippet flattens the **[Table 4.17](#12_Chapter04.xhtml#tab4.17)** which results in **[Table 4.18](#12_Chapter04.xhtml#tab4.18):**

![](images/page116-01.png)

From the plot **([Figure 4.7](#12_Chapter04.xhtml#fig4.7))**, it seems the distributions are not same. But it is not conclusive, and only one-way ANOVA test will ensure if they are same or not. aov() conducts oneway ANOVA and returns *F*\-statistics and *p*\-value. Let us formulate the hypothesis:

**1.** *H[0]:* The average quantity sold is same for different discount percentage.

**2.** *H[a]:* The average quantity sold is different for different discount percentage.

If *p*\-value is less than 0.05, the null hypothesis can be rejected, and we can conclude that the mean of each groups is not the same.

![](images/page116-02.png)

As *p*\-value is less than 0.05, we reject the null hypothesis and conclude that mean sales quantity values under different discounts are different. However, we need to check if the assumption for ANOVA is satisfied. The residual vs. fitted plot can help check that assumption **([Figure 4.8](#12_Chapter04.xhtml#fig4.8)).**

![](images/page116-03.png)![](images/page117-01.png)![](images/page117-02.png)

From **[Figure 4.9](#12_Chapter04.xhtml#fig4.9)**, we see that solid line is close to the dotted horizontal line. Thus, we can conclude that the assumption of “homogeneity of variance” across different groups is satisfied. **[Figure 4.9](#12_Chapter04.xhtml#fig4.9)** shows that the dots are very close to the reference line, and thus normality of data is evident.

In case the assumption gets violated, we could have performed Welch one-way test (which relaxes this assumption). oneway.test from stats package can help implement one-way test when normal distribution assumption is not satisfied.

One-way ANOVA test can only suggest that some discount level leads to significant difference in the average quantity of detergent sold. But we do not know which pair of discount level leads to this change.

Since the ANOVA test is significant, we can compute Tukey HSD (Tukey Honest Significant Differences) for performing multiple pairwise-comparison between the means of groups. The function TukeyHD() from stats package can be used to perform pairwise comparison. It takes the fitted ANOVA as an argument.

![](images/page118-01.png)![](images/page118-02.png)

From the *p*\-value, we can conclude that all three discounts lead to significant changes in the quantity of detergent sold.

### Summary

The chapter introduced the basic concepts of probability distributions, its parameters, and how they can be applied in the real world to solve problems. Some of the distributions explored are normal distribution, exponential distribution, binomial and Poisson distribution, and their applications. The objective of hypothesis testing is to either reject or retain a claim with the help of evidences collected from samples. The existing belief is called null hypothesis and new claim is called alternative hypothesis in a hypothesis test. Z-test can be used when:

• the value of population mean and population standard deviation is known or

• sample size is large *(n* > 30) and population variance is known.

The *t*\-test is used when the population standard deviation is unknown and is estimated from the sample. Chi-square goodness of fit tests are hypothesis tests that are used for comparing the observed distribution of data with expected distribution of the data to decide whether there is any statistically significant difference between the observed distribution and a theoretical distribution. Chi-square test of independence is used for checking independence between two variables.

### Exercises

#### Answer Questions 1-8 by Writing Code in R

**1.** The number of customers’ returns in a retail chain per day follows a Poisson distribution at a rate of 25 returns per day. Write code to answer the following questions:

(a) Calculate the probability that the number of returns exceeds 30 in a day.

(b) If the chance of fraudulent return is 0.05, calculate the probability that there will be at least 2 fraudulent returns in any given day.

**2.** A student is applying for master’s course in eight US universities and believes that she has in each of the eight universities a constant and independent 0.42 probability of getting selected. Write code to answer the following questions:

(a) What is the probability that she will get call from at least three universities?

(b) What is the probability that she will get calls from exactly four universities?

**3.** The time-of-failure of a machine follows exponential distribution with mean time between failures (MTBF) estimated to be 85 hours. Write code to answer the following questions:

(a) Calculate the probability that the system will fail before 85 hours.

(b) Calculate the probability that it will not fail up to 150 hours.

**4.** As per a survey on use of pesticides among 1,000 farmers in grape farming for around 10 acres of grape farmland, it was found that the grape farmers spray 38 litres of pesticides in a week on an average with the corresponding standard deviation of 5 litres. Assume that the pesticide spray per week follows a normal distribution. Write code to answer the following questions:

(a) What proportion of the farmers is spraying more than 50 litres of pesticide in a week?

(b) What proportion of farmers is spraying less than 10 litres?

(c) What proportion of farmers is spraying between 30 litres and 60 litres?

**5.** A bottle-filling machine fills water into 5-litre (5000-cm³) bottles. The company wants to test the null hypothesis that the average amount of water filled by the machine into the bottle is at least 5000 cm³. A random sample of 60 bottles coming out of the machine was selected and the exact contents of the selected bottles are recorded. The sample mean was 4,998.1 cm³. The population standard deviation is known from the experience to be 1.30 cm³. Assume that the population is normally distributed with the standard deviation of 1.30 cm³. Write code to test the hypothesis at *a* of 5%. Explain the results.

**6.** A fabric manufacturer would like to understand the proportion of defective fabrics they produce. His shop floor staff have been stating that the percentage of defective fabrics is not more than 18%. He would like to test whether the claim made by his shop floor staff is correct. He picked up a random sample of 100 fabrics and found 22 defectives. Use *a* = 0.05 and write code to test the hypothesis that the percentage of defective components is less than 18%.

**7.** Suppose that the makers of ABC batteries want to demonstrate that their battery lasts an average of at least 60 min longer than their competitor brand. Two independent random samples of 100 batteries of each kind are selected from both the brands, and the batteries are used continuously. The sample average life of ABC is found to be 450 min. The average life of competitor batteries is 368 min with the sample standard deviation of 82 min and 78 min, respectively. Frame a hypothesis and write the code to test ABC’s claim at 95% significance.

**8.** A training institute would like to check the effectiveness of their training programs and if the scores of the people trained improve post the training. A sample of 30 students was taken and their scores were calculated before and after the training. File *frainingscores.csv* contains scores of the students before and after the training. Frame and write the code to test the hypothesis of training effectiveness for the training institute.

### Bibliography

**1.** Anon (2021), “Pfizer data” available at [https://in.finance.yahoo.com/quote/PFE](https://in.finance.yahoo.com/quote/PFE)/, Yahoo Finance, accessed on 29 January 2021.

**2.** Anon (2021), “Glaxo data” available at [https://in.finance.yahoo.com/quote/GLAXO.NS](https://in.finance.yahoo.com/quote/GLAXO.NS)/, Yahoo Finance, accessed on 29 January 2021.

**3.** Anon (2021), “R Documentation”, Web Address: [https://www.rdocumentation.org/packages/stats/versions/3.6.1](https://www.rdocumentation.org/packages/stats/versions/3.6.1), accessed on 10 May 2021.

**4.** Kumar UD (2017), *“Business Analyfics - The Science of Dafa-Driven Decision Making”,* Wiley, New Delhi.

**5.** Pradhan M and Kumar UD (2019), *“Machine Learning Using Pyfhon”,* Wiley, Indian Institute of Management, Bangalore.

 

 
| 

## Supervised Learning Algorithm: Linear Regression

 || 

## 5

 |
| --- | --- |

*Take risks in your life, if you win, you can lead; if you lose, you can guide.*

**—Swami Vivekananda**

LEARNING OBJECTIVES

After reading this chapter, you would be able to:

• Understand the concept of simple and multiple linear regression and its applications in predictive analytics.

• Learn to build simple linear regression and multiple linear regression models using the caret package in R.

• Learn to perform tasks such as 1. Splitting the dataset into training and validation data, 2. Building regression models using R package on training dataset and test on the validation dataset.

• Learn how to incorporate categorical (qualitative) variables in a regression model.

• Learn about statistical significance using *t*\-test, *F*\-test, and regression model diagnostics; and perform tasks such as residual analysis, identification of outliers, and influential observations.

### 5.1 | Simple Linear Regression

Simple Linear Regression (SLR) is a statistical learning algorithm used to find the existence of an association relationship between a dependent variable (aka response variable or outcome variable) and an independent variable (aka explanatory variable, predictor variable, or feature). Using SLR, we can establish that the change in the value of the outcome variable (*Y*) is associated with a change in the value of feature *X.* That is, regression technique cannot be used for establishing a causal relationship between two variables. It is one of the most popular supervised learning algorithms in predictive analytics. A regression model requires the knowledge of both the outcome and the feature variables in the training dataset. A few examples of simple and multiple regression problems are listed below (Pradhan and Kumar, 2019):

**1.** A hospital may be interested in finding how the total treatment cost of a patient is as-sociated with the patient’s body weight.

**2.** Insurance companies would like to understand the association between healthcare costs and age.

**3.** Relationship between revenue generated from a product and features such as price, money spent on promotion, competitors’ price, and promotion expenses.

**4.** Restaurants would like to understand the relationship between customer wait time after placing an order and revenue.

**5.** E-commerce companies such as Amazon, BigBasket, and Flipkart would like to understand the association relationship between features such as 1. Number of customer visits to their portal, 2. Number of clicks on products, 3. Number of items on sale, and 4. Average discount percentage and the outcome variable revenue.

**6.** Banks and other financial institutions would like to understand the impact of variables such as unemployment rate, marital status, balance in the bank account, rainfall, etc., on percentage of non-performing assets (NPA).

### 5.2 | Steps for Regression Model Building

The following steps are used in building a regression model. Regression model-building is an iterative process; several iterations may be required before arriving at the appropriate model (Kumar 2017; Pradhan and Kumar 2019):

**1.** **Step 1: Collect/Extract Data:** The first step in building a regression model is to collect and/or extract data on dependent (outcome) variable and independent (feature) variables from different data sources. Data collection can be time-consuming and expensive, even when the organization has a well-designed Enterprise Resource Planning (ERP) system.

**2.** **Step 2: Preprocess the Data:** Before the model is built, it is essential to ensure the quality of the data on such issues as reliability, completeness, usefulness, accuracy, missing data, and outliers. Data imputation techniques may be used to deal with missing data. Descriptive statistics and visualization (such as box plot and scatter plot) may be used to identify the existence of outliers and variability in the dataset. Many new variables (such as ratio or product of variables) can be derived (aka feature engineering) and used in model building. Categorical data has to be preprocessed using dummy variables (part of feature engineering) before it can be used in the regression model. Note that, in R, some of the algorithms (such as regression using lm() function from stats package) implicitly carry out dummy variable coding.

**3.** **Step 3: Dividing Data into Training and Validation Datasets:** In this stage, the data is divided into two subsets (sometimes more than two): training dataset and validation or test dataset. The proportion of training dataset is usually between 70% and 80% of the data; the remaining is treated as validation data. Subsets may be created using random/stratified sampling procedure. This is an important step to measure performance of the model outside the data used for model building. It is also essential to check any overfitting of the model. In many cases, multiple training and multiple test data can be used (called k-fold cross-validation).

**4.** **Step 4: Perform Descriptive Analytics or Data Exploration:** It is always a good practice to perform descriptive analytics before moving to predictive analytics model building. Descriptive statistics will help us understand the variability in the features and visualization of the data through, say, a box plot which can be used to identify if there are outliers in the data. Another visualization technique, the scatter plot, may also reveal if there is any obvious relationship between the two variables under consideration. Scatter plot is useful to describe the functional relationship between the dependent or outcome variable and features.

**5.** **Step 5: Build the Model:** Build the model using the training dataset to estimate the regression parameters. The method of Ordinary Least Squares (OLS) is used to estimate the regression parameters. OLS is explained later in the chapter.

**6.** **Step 6: Perform Model Diagnostics:** Regression is often misused since many times necessary diagnostics tests are not performed before applying the model. Before it can be applied, it is necessary that the model is validated for all model assumptions including the definition of the functional form between outcome variable and feature. If model assumptions are violated, remedial measures must be employed.

**7.** **Step 7: Validate the Model and Measure Model Accuracy:** A major concern in ana-lytics is overfitting, that is, the model may perform very well in the training dataset but badly in validation dataset. It is important to ensure that the model performance is as consistent in the validation dataset as it was in the training dataset. In fact, the model may be cross-validated using multiple training and test datasets.

**8.** **Step 8: Decide on Model Deployment:** The final step in the regression model is to develop a deployment strategy in the form of actionable items and business rules that can be used by the organization.

### 5.3 | Building Simple Linear Regression Model

Simple Linear Regression (SLR) is a statistical model in which there is only one independent variable (feature) and the functional relationship between the dependent variable and the regression coefficient is linear (Kumar, 2017). Linear regression implies the function is linear with respect to regression parameters. The relationship between outcome variable and feature can be non-linear. One of the functional forms of SLR is given as follows:

![](images/page123-01.png)

For a dataset with *n* observations *(X[i],Y[i]),* where *i* = 1, 2, *n*, the above functional form can be written as follows:

![](images/page123-02.png)

In [Eq. (5.2)](#13_Chapter05.xhtml#eq5.2)

**1.** *Y[i]* is the value of *i*^(th) observation of the dependent variable (outcome variable) in the sample.

**2.** *X[i]* is the value of *i*^(th) observation of the independent or feature variable in the sample.

**3.** ϵ[*i*] the random error (also known as residuals) in predicting the value of *Y[i]*.

**4.** *β*[0] and *β*[1] are the regression parameters (or regression coefficients).

The regression relationship stated in [Eq. (5.2.)](#13_Chapter05.xhtml#eq5.2) is a statistical relationship, and thus is not exact, unlike a mathematical relationship, and thus the error terms e[;]. [Eq. (5.2)](#13_Chapter05.xhtml#eq5.2) can be written as

![](images/page123-03.png)

Regression parameters *β*[0] and *β*[1] are estimated by minimizing the sum of squared errors (SSE).

![](images/page123-04.png)

The regression parameters are estimated by taking partial derivatives of SSE with respect to *β*[0] and *β*[1] and by solving the equations, we get estimated values of *β*[0] and *β*[1.]

![](images/page123-05.png)![](images/page123-06.png)

where ![](images/pageIn_ch5-01.png)and ![](images/pageIn_ch5-02.png)are the estimated values of the regression parameters *β*[0] and *β*[1] The above procedure is known as method of Ordinary Least Squares (OLS). The estimate using OLS gives the Best Linear Unbiased Estimates (BLUE) of regression parameters. We can also estimate the ![](images/pageIn_ch5-03.png)and ![](images/pageIn_ch5-04.png)by rewriting [Eq. (5.1)](#13_Chapter05.xhtml#eq5.1) in the matrix form as

![](images/page124-01.png)

[Eq. (5.7)](#13_Chapter05.xhtml#eq5.7) can be written as

![](images/page124-02.png)

[Eq. (5.8)](#13_Chapter05.xhtml#eq5.8) can be written as

![](images/page124-03.png)

where ![](images/pageIn_ch5-05.png)is a vector representing ![](images/pageIn_ch5-06.png)and ![](images/pageIn_ch5-07.png)*.*

The following are the assumptions of the linear regression model (Kumar, 2017).

**1.** The errors or residuals ϵ[*i*] are assumed to follow a normal distribution with expected value of error *E*(ϵ[*i*]) = 0.

**2.** The variance of error, VAR(e[;]), is constant for various values of independent variable *X,* known as homoscedasticity. When the variance is not constant, it is called hetero-scedasticity.

**3.** The error and independent variable are uncorrelated.

**4.** The functional relationship between the outcome variable and feature is correctly defined.

Following are the properties of Simple Linear Regression (Kumar, 2017):

**1.** The mean value of *Y[i]* for given *X[i]* is given by ![](images/pageIn_ch5-08.png)

**2.** *Y[i]* is a normal distribution with mean ![](images/pageIn_ch5-09.png)and variance VAR(ϵ[*i*]).

### 5.4 | Example: Predicting MBA Salary from Grades in 10th

**[Table 5.1](#13_Chapter05.xhtml#tab5.1)** contains the salary of 50 graduating MBA students of a business school in 2016 and their corresponding percentage marks in Grade 10 (File Name: MBA Salary.csv). We will develop a Simple Linear Regression (SLR) model to understand and predict salary based on the percentage of marks in Grade 10 (Kumar, 2017).

**Steps for Building Regression Model Using R**

**1.** Import stats and caret package.

**2.** Load the dataset into dataframe.

**3.** Identify and set the *X* (features) and *Y* (outcome) variables for modelling.

**4.** Split the dataset into train and validation set.

**5.** Build the regression model using OLS() method.

**6.** Print model summary and conduct model diagnostics.

#### 5.4.1 Install Packages

Let’s begin by loading the MBA Salary.csv dataset using read.csv() from stats package and then follow the steps for building a regression model. However, before using the functions of package stats and caret, ensure that the package is installed in your computer.

![](images/page125-01.png)![](images/page125-02.png)![](images/page126-01.png)

#### 5.4.2 Data Import and Manipulation

The collected data resides in a csv file. The ‘read.csv’ function is used to read the dataset from the current working directory. If you are not sure of the current working directory from where the file will be read, you can use

**1.** **getwd( )** function to get your working directory and

**2.** **setwd( )** function to set your working directory.

By default, the read.csv file only expects the path to the file name. However, in addition, we use two more arguments:

**1.** **na.strings()** to embed *NA* wherever there is a blank space or NA in the dataset. The blank space or NA values is being found using **c(““**, “ “, “NA”). This operation is being performed as R recognizes *NA* as a missing value and not a blank space. This operation of embedding *NA* can as well be performed after the data is loaded as a data.frame as well. However, it is easier to carry out this step while reading the dataset.

**2.** **check.names()** checks for the syntactically correct name. If there is blank space in column names, it embeds a ‘.‘ in place of a blank space. In the code below, we are over riding the check.names() by setting it to FALSE and then using gsub() to replace the blank spaces in column name. **[Table 5.2](#13_Chapter05.xhtml#tab5.2)** shows the dataset read using read.csv() method.

![](images/page126-02.png)

We can now look into the data types and descriptive statistics of the data by using the below code chunk. The str( ) function shows that the mba\_salary\_df has 50 observations across three variables. The variables are Sl\_No, Percentage\_in\_Grade\_10, and Salary.

![](images/page126-03.png)![](images/page127-01.png)

**[Table 5.3](#13_Chapter05.xhtml#tab5.3)** is generated using the summary( ) function. It summarizes all the variables in the data frame. We will remove Sl. No. from the variable list before further analysis.

The below code chunk uses column subsetting to remove the first column of the data-frame and creates a new\_mba\_df **([Table 5.4](#13_Chapter05.xhtml#tab5.4)).**

![](images/page127-02.png)

In the above code chunk, we also performed an additional task of row-wise deletion of missing values by using na.omit function. Note that the use of embedding *NA* while loading the data was done to enable this step of deleting the rows wherever there is no data available in even one of the columns. In new\_mba\_df, this step does not delete any observation in the data frame as there is no missing value. However, the step is useful while dealing with dataset where there is missing information.

*It should be noted that the row-wise deletion of missing value should be carried out after having tried the imputation techniques to fill up the missing cases.*

![](images/page127-03.png)

**TABLE 5.4** | Clean MBA data

| Percentage\_in\_Grade\_10 || Salary |
| --- | --- |
| 62.00 || 270,000 |
| --- | --- |
| 76.33 || 200,000 |
| 72.00 || 240,000 |
| 60.00 || 250,000 |
| 61.00 || 180,000 |
| 55.00 || 300,000 |

#### 5.4.3 Creating Feature set(x) and Outcome Variable (Y)

Let us write a generic function to extract the predictors and response variable from the data set.

![](images/page128-01.png)

#### 5.4.4 Create Train and Validation Set

**createDataPartition( )** function from caret package provides the ability to split the dataset randomly into training and validation datasets.

**1.** The function expects a vector to be passed and, in our case, we are passing one of the variables named salary to it.

**2.** It also expects the percentage of data that should go into training set which we have set to 0.80.

**3.** Finally, by marking *list* = *FALSE* we expect train\_index to contain a matrix with the number of rows equal to floor(0.80 \* length(Salary)) times number of columns, that is, 2.

However, even before calling createDataPartition( ) we have used set.seed( ) function to maintain repeatability and reproducibility of the results. This is an important step before performing any operation which deals with random partition or random generation of numbers.

*We encourage readers to comment out the sef.seed function from the below code. Observe the records which get into train and test dataframe in each execution.*

![](images/page128-02.png)

#### 5.4.5 Model Building: Using the Caret Package

There are a number of models which can be built using the caret package. However, it should be noted that apart from having specific functions, caret is a wrapper package. This means the developers of caret package have devised a generic framework for model building which call different functions from other R packages.

![](images/page129-01.png)

**1.** To implement linear regression, the method which can be used in caret package is lm( ). However, lm( ) function is built under package stats. But through caret package, we can call lm( ) method and develop regression model.

**2.** To implement random forest, one of the methods which can be used in caret package is rf( ). However, rf( ) function is built under package randomForest. But through caret package, we can call rf( ) method and develop random forest model.

The below code chunk gives the names of all methods implemented through caret package.

**[Table 5.5](#13_Chapter05.xhtml#tab5.5)** shows the first 100 methods from the caret package.

![](images/page129-02.png)

The list is huge and one may not be aware of the purpose of all the methods listed above. So to get info on a specific method, we can run the below code chunk. The below code shows that lm method is for building regression model.

![](images/page130-01.png)

The standardized way of developing a model using the caret package has three main components. These components attempt to streamline the model building and evaluation process.

**1.** **trainControl( )**: This component tries to control the model training environment. The **method** parameter in the trainControl function offers a lot of flexibility of applying various sampling techniques before the model is built. Some of the resampling strategies included currently are ‘boot’, ‘cv, ‘LOOCV’, ‘LGOCV, ‘repeat-edcv’, ‘timeslice’, ‘none’, and ‘oob’. Apart from the **method** parameter, there are several other parameters which can be passed but most of them are optional parameters and have values set by default. The complete parameter list with default setting is as below (Anon, 2020):

trainControl(method = ‘boot’, number = ifelse(grepl(‘cv’, method), 10, 25), repeats = ifelse(grepl(‘cv’, method), 1, number), *p* = 0.75, search = ‘grid’,initialWindow = NULL, horizon = 1, fixedWindow = TRUE, verboseIter = FALSE, returnData = TRUE, returnResamp = ‘final’, savePredictions = FALSE, classProbs = FALSE, summaryFunction = defaultSummary, selectionFunction = ‘best’, preProcOptions = list(thresh = 0.95, ICAcomp = 3, k = 5) , sampling = NULL, index = NULL, indexOut = NULL, indexFinal = NULL, timingSamps = 0, predictionBounds = rep(FALSE, 2), seeds = NA, adaptive = list(min = 5, alpha = 0.05, method = ‘gls’, complete = TRUE), trim = FALSE, allowParallel = TRUE)

**[Table 5.6](#13_Chapter05.xhtml#tab5.6)** shows the description of the various parameters of trainControl function. For model fine-tuning in advanced machine learning, it may be required to change the default values for some of the parameters shown in **[Table 5.6](#13_Chapter05.xhtml#tab5.6).** For the purpose of linear regression, we will set the method = none and proceed.

**2.** **train()**: The train function can be used to

• Evaluate, using resampling, the effect of model tuning parameters on performance.

• Choose the ‘optimal’ model across these parameters.

• Estimate model performance from a training set.

Below is the structure of train function and list of parameters which can be passed on to the train function

**train**(x, y, method = ‘rf’, preProcess = NULL,..., weights = NULL,metric = ifelse(is.factor(y), ‘Accuracy’, ‘RMSE’), maximize = ifelse(metric %in% c(‘RMSE’, ‘logLoss’), FALSE, TRUE), trControl = trainControl(), tuneGrid = NULL, tuneLength = 3)

**[Table 5.7](#13_Chapter05.xhtml#tab5.7)** shows the description of the various parameters of train function.

**3.** **expand.grid( )**: This is an advanced function for fine-tuning some of the hyper parameters for machine learning algorithms. The parameter inside the expand.grid() function varies, according to model.[¹](#13_Chapter05.xhtml#ch5-r-fn1)

**TABLE 5.6** | trainControl() function parameters list (Anon, 2019, 2020, 2021; Source: [https://www.rdocumentation.org](https://www.rdocumentation.org)/)

| Argument || Definition |
| --- | --- |
| method || The resampling method: ‘boot, ‘boot632, ‘cv’, ‘repeatedcv’, ‘LOOCV’, ‘LGOCV’ (for repeated training/test splits), ‘none’ (only fits one model to the entire training set), ‘oob’ (only for random forest, bagged trees, bagged earth, bagged flexible discriminant analysis, or conditional tree forest models), ‘adaptive\_cv’, ‘adaptive\_boot’, or ‘adaptive\_LGOCV’ |
| --- | --- |
| number || Indicates either the number of folds or number of resampling iterations |
| repeats || For repeated k-fold cross-validation only: the number of complete sets of folds to compute |
| verboseIter || A logical for printing a training log. |
| returnData || A logical for saving the data |
| returnResamp || A character string indicating how much of the resampled summary metrics should be saved. Values can be ‘final, ‘all, or ‘none’ |
| savePredictions || An indicator of how much of the hold-out predictions for each resample should be saved. Values can be either ‘all, ‘final’, or ‘none’. A logical value can also be used that converts to ‘all’ (for true) or ‘none’ (for false). ‘final’ saves the predictions for optimal tuning parameters. |
| P || For leave-group out cross-validation: the training percentage |
| search || Either ‘grid’ or ‘random’, describing how the tuning parameter grid is determined. |
| initialWindow, horizon, fixed-Window || Possible arguments to createTimeSlices |
| classProbs || A logical; should class probabilities be computed for classification models (along with predicted values) in each resample? |
| summaryFunction || A function to compute performance metrics across resamples. The arguments to the function should be the same as those in defaultSummary. |
| selectionFunction || The function used to select the optimal tuning parameter. This can be a name of the function or the function itself. See best for details and other options. |
| preProcOptions || A list of options to pass to preProcess. The type of preprocessing (e.g., center, scaling, etc.) is passed in via the preProc option in train. |
| sampling || A single character value describing the type of additional sampling that is conducted after resampling (usually to resolve class imbalances). Values are ‘none’, ‘down’, ‘up’, ‘smote’, or ‘rose’. The latter two values require the DMwR and ROSE packages, respectively. This argument can also be a list to facilitate custom sampling and these details can be found on the caret package website for sampling (link below). |
| index || A list with elements for each resampling iteration. Each list element is a vector of integers corresponding to the rows used for training at that iteration. |
| indexOut || A list (the same length as index) that dictates which data are held-out for each resample (as integers). If NULL, then the unique set of samples not contained in index is used. |
| indexFinal || An optional vector of integers indicating which samples are used to fit the final model after resampling. If NULL, then entire dataset is used. |
| timingSamps || The number of training set samples that will be used to measure the time for predicting samples (zero indicates that the prediction time should not be estimated. |
| predictionBounds || A logical or numeric vector of length 2 (regression only). If logical, the predictions can be constrained to be within the limit of the training set outcomes. For example, a value of c(TRUE, FALSE) would only constrain the lower end of predictions. If numeric, specific bounds can be used. For example, if c(10, NA), values below 10 would be predicted as 10 (with no constraint in the upper side). |
| seeds || An optional set of integers that will be used to set the seed at each resampling iteration. This is useful when the models are run in parallel. A value of NA will stop the seed from being set within the worker processes while a value of NULL will set the seeds using a random set of integers. Alternatively, a list can be used. The list should have B+1 elements, where B is the number of resamples, unless method is ‘boot632’ in which case B is the number of resamples plus 1. The first B elements of the list should be vectors of integers of length M where M is the number of models being evaluated. The last element of the list only needs to be a single integer (for the final model). |
| adaptive || A list used when method is ‘adaptive\_cv, ‘adaptive\_boot, or ‘adaptive\_LGOCV’. |
| trim || A logical. If TRUE, the final model in object$finalModel may have some components of the object removed so reduce the size of the saved object. The predict method will still work, but some other features of the model may not. Trimming will occur only for models where this feature has been implemented. |
| allowParallel || If a parallel backend is loaded and available, should the function use it? |

**TABLE 5.7** | Train function parameter list (Anon 2019, 2020, 2021; Source: [https://www.rdocumentation.org](https://www.rdocumentation.org)/)

| Argument || Description |
| --- | --- |
| x || An object where samples are in rows and features are in columns. This could be a simple matrix, data frame, or any other type (e.g. sparse matrix). |
| --- | --- |
| y || A numeric or factor vector containing the outcome for each sample. |
| weights || A numeric vector of case weights. This argument will only affect models that allow case weights. |
| … || Arguments passed to the classification or regression routine (such as randomForest). Errors will occur if values for tuning parameters are passed here. |
| preProcess || A string vector that defines a preprocessing of the predictor data. Current possibilities are ‘BoxCox’, ‘YeoJohnson, ‘expoTrans, ‘center, ‘scale’, ‘range’, ‘knnImpute, ‘bagImpute, ‘medianImpute’, ‘pca’, ‘ica, and ‘spatialSign’. The default is no preprocessing. See preProcess and trainControl on the procedures and how to adjust them. Preprocessing code is only designed to work when x is a simple matrix or data frame. |
| metric || A string that specifies what summary metric will be used to select the optimal model. By default, possible values are ‘RMSE’ and ‘Rsquared’ for regression and ‘Accuracy’ and ‘Kappa’ for classification. If custom performance metrics are used (via the summaryFunction argument in trainControl), the value of metric should match one of the arguments. If it does not, a warning is issued and the first metric given by the summaryFunction is used. (NOTE: If given, this argument must be named.) |
| maximize || A logical: should the metric be maximized or minimized? |
| trControl || A list of values that define how this function acts. See trainControl and [http://topepo.github.io/caret/training.html#custom](http://topepo.github.io/caret/training.html#custom). (Note: If given, this argument must be named.) |
| tuneGrid || A data frame with possible tuning values. The columns are named the same as the tuning parameters. Use getModelInfo to get a list of tuning parameters for each model or see [http://topepo.github.io/caret/available-models.html](http://topepo.github.io/caret/available-models.html). (NOTE: If given, this argument must be named.) |
| tuneLength || An integer denoting the amount of granularity in the tuning parameter grid. By default, this argument is the number of levels for each tuning parameter that should be generated by train. If trainControl has the option search = ‘random’, this is the maximum number of tuning parameter combinations that will be generated by the random search. (NOTE: If given, this argument must be named.) |

The call to the above three functions happens in the sequence expand.grid(), trainControl(), and train(). The algorithm steps are as follows[²](#13_Chapter05.xhtml#ch5-r-fn2):

**1.** Define set of model parameter values to be evaluated in expand.grid(). For each parameter, set **perform:**

• For each resampling iteration in trainControl() **perform:**

**1.** Hold out specific sample.

**2.** \[Optional\] Preprocess the data using train().

**3.** Fit the model using train() on the remainder.

**4.** Predict the hold-out samples.

• Calculate the average performance across the hold-out prediction

**2.** Determine the optimal parameter set.

**3.** Fit the final model on the training data using the optimal parameter set.

The **caret package**, which is a wrapper package, gives a standardized framework to implement most of the advanced machine learning algorithms.

For simple and multiple linear regression, the only hyperparameter to fine-tune is b[0], that is, make a model with constant term or without constant term. We can check if there are model parameters which can be fine-tuned using caret package by using modelLookup.

The functions **expand.grid(), trainControl()**, and **train()** can be used to implement various sampling strategies as well as apply different machine learning algorithms.

![](images/page133-01.png)

We will not be using expand.grid() in this chapter. We will also set the method=‘none’ in trainControl() function.

![](images/page133-02.png)

#### 5.4.6 Estimating Regression Coefficient

After having understood the methods of the caret package, let’s deep-dive into how regression coefficients are estimated in R. We know from [Eq. (5.9)](#13_Chapter05.xhtml#eq5.9) that we can solve ![](images/pageIn_ch5-10.png)using normal equations method. In R, it can be solved by using two functions, that is crossprod() and solve().

**1.** **crossprod()**: Given matrices *X* and *Y*as arguments, crossprod() returns a matrix cross-product. This is equivalent to the call *t*(*X*) %\*% *Y*. *t*(*X*) stands for transposing the matrix *X*. If the argument *Y* is left blank, the function takes *Y* as the same matrix as *X,* that is, the function will calculate *X^TX.*

**2.** **solve()**: SyAtem of the equations, like [Eq. (5.9)](#13_Chapter05.xhtml#eq5.9), can besolved using this function. Thus ![](images/pageIn_ch5-11.png)can be solved for ![](images/pageIn_ch5-12.png), where *Y* can be either a vector or a matrix. If *Y* is missing, then *Y* is taken to be an identity matrix and solve will return the inverse of X.

So, [Eq. \[5.9\]](#13_Chapter05.xhtml#eq5.9) can be solved by calling

![](images/page133-03.png)

However, solve() is numerically unstable if the number of features is large. Thus, QR decomposition is used to decompose the matrix of variables *X* into an orthonormal matrix *Q* and a non-singular upper-triangular matrix *R.* The QR matrix is then used to estimate the ![](images/pageIn_ch5-13.png)parameters in normal equations method.

Substituting *X = QR* in [Eq. \[5.8\]](#13_Chapter05.xhtml#eq5.8) yields

![](images/page133-04.png)

Re-writing [Eq. \[5.10\]](#13_Chapter05.xhtml#eq5.10) gives

![](images/page133-05.png)

Using the fact that *Q^TQ = I*, we get [Eq. (5.12)](#13_Chapter05.xhtml#eq5.12) as

![](images/page133-06.png)

Multiplying both sides of [Eq. (5.12)](#13_Chapter05.xhtml#eq5.12) with *(R^T*)^(−1) yields

![](images/page133-07.png)

Hence, [Eq. \[5.13\]](#13_Chapter05.xhtml#eq5.13) becomes

![](images/page133-08.png)

Since *R* is an upper-triangular matrix, [Eq. \[5.14\]](#13_Chapter05.xhtml#eq5.14) is easy to solve for ![](images/pageIn_ch5-14.png), by using the function backsolve(R, crossprod(Q,Y)).

In practice, the train() function from the caret package with method=lm uses the QR decomposition technique described above to get the OLS estimate of the parameters and returns model information in the object mba\_reg\_model. The object returned by the train() function contains the estimates of the *β*, accuracy measures, and residual values, among other details.

![](images/page134-01.png)

Printing the estimated parameters can be done using summary() on the mba\_reg\_ model object.

![](images/page134-02.png)

The estimated model can be written as

**MBA Salary = 61234 + 3106 \* (Percentage in Grade 10)**

The equation can be interpreted as follows: for every one-unit increase in Grade 10 percentage, the salary of MBA students will increase by 3,106 units on an average.

### 5.5 | Model Diagnostics

It is important to validate the regression model to ensure its validity and goodness of fit before it can be used for practical applications. The following measures are used to validate the simple linear regression models (Kumar, 2017):

**1.** Coefficient of determination (R-square).

**2.** Hypothesis test to check statistical significance of regression coefficients.

**3.** Analysis of variance for overall model validity (relevant more for multiple linear regression).

**4.** Residual analysis to validate the regression model assumptions such as normality and homoscedasticity.

**5.** Outlier analysis.

#### 5.5.1 Coefficient of Determination (*R*\-Square or *R*²)

The primary objective of regression is to explain the variation in *Y* using the knowledge of *X* (Kumar, 2017). The coefficient of determination (or *R*\-square or *R*²) measures the percentage of variation in *Y* explained by the model (*β*[0] + *β*[1] *X*). The simple linear regression model can be broken into explained variation by the model and unexplained variation as shown in [Eq. (5.15)](#13_Chapter05.xhtml#eq5.15):

![](images/page135-01.png)

The relationship between total variation, explained variation, and unexplained variation is given as follows:

![](images/page135-02.png)

It can be proved mathematically that the sum of squares of total variation is equal to the sum of squares of explained variation plus the sum of squares of unexplained variation (for proof, refer to Kutner *et al.* (2013), page 65):

![](images/page135-03.png)

where SST is the sum of squares of total variation, SSR is the sum of squares of explained variation due to regression model and SSE is the sum of squares of unexplained variation. The coefficient of determination *(R* square) is given by

![](images/page135-04.png)

The coefficient of determination *(R* square) has the following properties (Kumar, 2017):

**1.** The value of *R*\-square lies between 0 and 1.

**2.** Mathematically, *R*\-square *(R²)* is the square of correlation coefficient *(R²* = *r²),* where *r* is the Pearson correlation coefficient.

**3.** Higher *R*\-square indicates better fit. However, one should be careful about a spurious relationship.

#### 5.5.2 Hypothesis Test for the Regression Coeffcient

The regression coefficient (*β*[1]) captures the existence of a linear relationship between the outcome variable and the feature. If *β*[1] = 0, we can conclude that there is no statistically significant linear relationship between the two variables. It can be proved that the sampling distribution of *β*[1] is a *t* distribution (Kutner et al. 2013, Kumar, 2017). The null and alternative hypotheses are

![](images/page135-05.png)

The corresponding test statistic is given by

![](images/page135-06.png)

The standard error of estimate of regression coefficient is given by

![](images/page136-01.png)

where *S[e]* is the standard error of estimated value of *Y[i]* and the residuals and is given by

![](images/page136-02.png)

The hypothesis test is a two-tailed test. [Eq. (5.19)](#13_Chapter05.xhtml#eq5.19) is a *t* distribution with *n* - 2 degrees of freedom (two degrees of freedom are lost due to estimation of two regression parameters *β*[0] and ![](images/pageIn_ch5-15.png)is the standard error of regression coefficient.

#### 5.5.3 Analysis of Variance (ANOVA) in Regression Analysis

We can check the overall validity of the regression model using ANOVA in case of multiple linear regression model with *k* features. The null and alternative hypothesis are given by (Kumar, 2017):

![](images/page136-03.png)

The corresponding *F*\-statistic is given by

![](images/page136-04.png)

Where *MSR* (= *SSR/k)* and *MSE* (= *SSE/(n* - *k* - 1)) are mean square regression and mean square error, respectively. *F*\-test is used for checking whether the overall regression model is statistically significant or not.

#### 5.5.4 Model Diagnostic: Regression Model Summary

The regression model summary helps us validate the above model diagnostics.

![](images/page136-05.png)

From the summary output show, we can infer the following:

**1.** The model *P*\-square value is 0.1344; that is, 13.4% of the variation in salary is explained by the model.

**2.** The *p*\-value for the *t*\-test is 0.01562, which indicates there is a statistically significant relationship between the feature **percentage in Grade 10** and **salary.**

**3.** Also, the probability value of *F*\-statistics of the model is 0.01562, which indicates that the overall model is statistically significant.

Note that in a simple linear regression, the *p*\-value for *t*\-test and *F*\-test will be the same since the hypothesis is the same (*F* *\= t*²).

#### 5.5.5 Residual Analysis

Residuals or errors are the difference between the actual and predicted value of the outcome variable. Residual (error) analysis is important to check whether the assumptions of regression models have been satisfied. It is performed to check the following (Kumar, 2017):

**1.** The residuals are normally distributed.

**2.** The variance of residual is constant (homoscedasticity).

**3.** The functional form of regression is correctly specified.

#### *Check for Normal Distribution of Residual (Normal Q\_Q Plot)*

The normality of residuals can be checked using Quantile-Quantile plot (Q-Q plot) or P-P plot (probability-probability plot). Q-Q plot compares the cumulative distribution function of two probability distributions against each other (Kumar, 2017). In the current context, we use the Q-Q plot to check whether the distribution of the residual matches with that of a normal distribution. The diagonal line in the plot represents the cumulative distribution of a normal distribution.

The **plot()** of the regression object model generates the Q-Q plot. This plot shows whether the errors are normally distributed. In case of normal distribution, the dots should appear close to the diagonal line, with not much deviation.

#### *Test of Homoscedasticity (Scale-Location Plot)*

An important assumption of regression model is that the residuals have constant variance (homoscedasticity) across different values of the predicted value (*Y*). This can be observed by drawing a residual plot, which is a plot between standardized residual and standardized predicted values. If there is heteroscedasticity (non- constant variance of residuals), then a funnel-type shape in the residual plot can be expected when the feature variable is continuous. A non-constant variance of the residuals in known as heteroscedasticity.

The plot() of the regression object model gives Scale-Location plot. It shows whether the residuals are equally spread along the range of feature values. It is desirable to see a horizontal straight line with randomly spread points. This is a visual inspection and even if the line is not completely horizontal but the dots do not appear to show any specific shape, the assumption can be deemed to be satisfied for practical purposes.

#### *Functional Form of Regression (Residual vs. Fitted)*

There could be a nonlinear relationship between predictor variable (*X*s) and the outcome variable (*Y*). This nonlinear relationship can show up in **Residual vs. Fitted Plot** which is generated using the **plot()** of regression object. It is desirable to see a horizontal straight line with randomly spread points. This is a visual inspection and even if the line is not completely horizontal but the dots do not appear to show any specific shape, the assumption can be deemed to be satisfied for practical purposes. **[Figure 5.1](#13_Chapter05.xhtml#fig5.1)** plots the diagnostic metrics discussed in this section.

![](images/page138-01.png)![](images/page138-02.png)

For the MBA salary prediction, the residual plot may be interpreted as:

**1.** From Residual vs. Fitted, we can conclude that the functional form of the regression is correctly specified.

**2.** From the Q-Q plot, we can conclude that the residuals follow an approximate normal distribution (we need only an approximate normal distribution).

**3.** From the Scale-Location plot, the residuals are random and have no funnel shape, which means they have constant variance (homoscedasticity).

**4.** From Residual vs. Leverage, it can be observed that there are no observations which fall outside the Z-Score of 3. However, there are observations number 9, 16, and 25, which seems to give either high leverage or high Cook’s score. Leverage and Cook’s score are discussed in next section.

When data points exceed the Cook’s distance cut-off scores and are to the upper or lower right corner of the Residual vs. Leverage plot (Cook’s distance of 0.5 and above), such data points can be marked as influential to the regression results. Regression results will be altered if such cases are excluded from the training set. In **[Figure 5.1](#13_Chapter05.xhtml#fig5.1)**, none of the observations are to the upper or lower right of the Residual vs. Leverage plot.

#### 5.5.6 Outlier Analysis

Outliers are observations whose values show a large deviation from the mean value. The presence of an outlier can have a significant influence on the values of regression coefficients. Thus, it is important to identify the existence of outliers in the data (Kumar, 2017).

The following distance measures are useful in identifying outlier observations:

**1.** Outlier - Z-score

**2.** High leverage - Leverage values

**3.** Influential - Cook’s distance

#### *Outlier - Z-score*

*Z*\-score is the standardized distance of an observation from its mean value. For the predicted value of the dependent variable Y, the Z-score is given by (Kumar, 2017) as

![](images/page139-01.png)

where

![](images/pageIn_ch5-16.png)is the predicted value of *Y* for *i^(th)* observation,

*Y[i]* is the actual value of *Y,* and

σ[*Y*]\- Standard deviation of Y.

Any observation with a Z-score of more than 3 in absolute value may be flagged an outlier.

#### *Leverage Values*

The regression line can be influenced by extreme values in *Y* (outliers) or by data points with extreme values in *X* (high leverage). The leverage value of an observation measures the influence of that observation on the overall fit of the regression function and is related to the Mahalanobis distance. This statistic is saved as .hat, that is, hat value in regression model object. An observation with .hat value of more than 3(*p* + 1)/n is treated as a highly influential observation, where *p* is the number of features in the model and *n* is the sample size.

The plot() of the regression object model gives the Residual vs. Leverage plot. In the plot, look for outlier values at the upper right corner or at the lower right corner. The high leverage cases will be highlighted in the same plot with the number marked against such cases.

#### *Cook’s Distance and DFBETA*

Even if data has extreme values, it may not be influential enough to change the regression coefficients. On the flip side, some cases could be very influential even if they do not seem to be an outlier (extreme values). Influential cases are identified by Cook’s distance, which combines the information of leverage and residual of the observation.

Cook’s distance measures how far, on an average, the predicted *y* value of the dependent variable changes for all observations in the sample when a particular observation is excluded from the sample for the estimation of regression parameters. This statistic is saved as .cooksd in regression model object.

DFBETA, another statistic for measuring influential cases, determines how much a parameter estimates change if the observation in question is dropped from the dataset.

Cook’s distance is presumably more important while building predictive modelling, whereas dfbeta is more important in explanatory modelling.

A rule of thumb is that an observation has high influence if .cooksd exceeds 4/(n - *p* - 1) (Bruce and Bruce, 2017), where *n* is the number of observations and *p* the number of predictor variables. However, the general consensus is that a Cook’s distance value of more than 1 indicates a highly influential observation but a value above 0.5 should also be relooked at.

**[Figure 5.2](#13_Chapter05.xhtml#fig5.2)** plots the Cook’s distance to visualize the diagnostic metrics discussed in this section.

![](images/page139-02.png)![](images/page139-03.png)

While discussing multiple linear regression, we will revisit the residual and outlier analysis plots and build logic to highlight observations which violate the model diagnostic thresholds.

### 5.6 | Making Predictions and Measuring Accuracy

Ideally, the prediction should be made on the validation (or test) data and the accuracy of prediction should be evaluated (Pradhan and Kumar, 2019).

The predict () is used to get the predicted response on the new dataset (Roshan, 2020). You may get an error message if the test data has any new levels not present in the training set. This generally happens when the data has categorical variables with multiple levels. **[Table 5.8](#13_Chapter05.xhtml#tab5.8)** shows the predicted value (fit), lower range (lwr), and the upper range (upr) of the prediction.

![](images/page140-01.png)

#### 5.6.1 Finding R-Squared and RMSE

Several measures can be used for measuring the accuracy of prediction. Mean Square Error (MSE), Root Mean Square Error (RMSE), and Mean Absolute Percentage Error (MAPE) are the ones frequently used. RMSE shows on an average what error the model makes while making a prediction. The smaller the RMSE value, the better it is.

The below code chunk implements MAPE as a metric to measure the model performance on test set.

![](images/page140-02.png)

### 5.7 | Multiple Linear Regression

Multiple Linear Regression (MLR) is a supervised learning algorithm for finding the existence of an association relationship between a dependent variable (aka response variable or outcome variable) and several independent variables (aka explanatory variables or predictor variable or features).

![](images/page140-03.png)

The functional form of MLR is given by

![](images/page141-01.png)

The regression coefficients *β*[1], *β*[2], ..., *β[k]* are called partial regression coefficients since the relationship between an explanatory variable and the response (outcome) variable is calculated after removing (or controlling) the effect of all other explanatory variables (features) in the model.

The assumptions made in the MLR model are as follows (Kumar, 2017):

**1.** The regression model is linear in regression parameters *(β* values).

**2.** The residuals follow a normal distribution and the expected value (mean) of the residuals is zero.

**3.** In time series data, residuals are assumed to uncorrelated.

**4.** The variance of the residuals is constant for all values of *X[i]*. When the variance of the residuals is constant for different values of *X[i]*, it is called homoscedasticity. A non-constant variance of residuals is called heteroscedasticity.

**5.** There is no high correlation between independent variables in the model (called multicollinearity). Multicollinearity can destabilize the model and result in incorrect estimation of regression parameters.

The partial regression coefficients in this case are again estimated by minimizing the Sum of Square Errors (SSE). We will explain the MLR model by using the example of auction pricing in the Indian Premier League.

### 5.8 | Predicting the SOLD PRICE (Auction Price) of Players in Indian Premier League (Kumar, 2017)

The Indian Premier League (IPL) is a professional Twenty20 cricket league started by the BCCI in 2008, with eight franchises comprising players from across the world. The first IPL auction was held in 2008 for ownership of teams for 10 years, with a base price of USD 50 million. Franchises acquire players through an English auction conducted every year. However, there were several rules in place. For instance, only international players and popular Indian players were auctioned.

Performances of players can be measured through several metrics. Although the IPL is a 20-over tournament, it was possible that performances in the other formats of the game such as Tests and One-Day Internationals could influence pricing. A few players had excellent Test records, but their Twenty20 records were not as impressive. The performances of 130 players who played at least one season of the IPL (2008-2011) measured through various performance metrics are provided in **[Table 5.9](#13_Chapter05.xhtml#tab5.9).**

### 5.9 | Developing Multiple Linear Regression Model

In this section, we will discuss the various steps involved in developing a multiple regression using R (Pradhan and Kumar, 2019).

We will use the **caret** package to demonstrate multiple linear regression.

![](images/page141-02.png)

**TABLE 5.9** | IPL Data description

| Data Code || Description |
| --- | --- |
| AGE || Age of the player at the time of auction classified into three categories. Category 1 (L25) means the player is less than 25 years old, 2 means the age is between 25 and 35 years (B25-35), and 3 means the age is more than 35 (A35). |
| --- | --- |
| RUNS.S || Number of runs scored by a player |
| RUNS.C || Number of runs conceded by a player |
| HS || Highest score by a batsman in IPL |
| AVE.B || Average runs scored by a batsman in IPL |
| AVE.BL || Bowling average (number of runs conceded/number of wickets taken) in IPL |
| SR.B || Batting strike rate (ratio of the number of runs scored to the number of balls faced) in IPL |
| SR.BL || Bowling strike rate (ratio of the number of balls bowled to the number of wickets taken) in IPL |
| SIXERS || Number of six runs scored by a player in IPL |
| WKTS || Number of wickets taken by a player in IPL |
| ECON || Economy rate of a bowler (number of runs conceded by the bowler per over) in IPL |
| CAPTAINCY.EXP || Captained either a T20 team or a national team |
| ODI.SR.B || Batting strike rate in One-Day Internationals |
| ODI.SR.BL || Bowling strike rate in One-Day Internationals |
| ODI.RUNS.S || Runs scored in One-Day Internationals |
| ODI.WKTS || Wickets taken in One-Day Internationals |
| T.RUNS.S || Runs scored in Test matches |
| T.WKTS || Wickets taken in Test matches |
| PLAYER.SKILL || Player’s primary skill (batsman, bowler, or allrounder) |
| COUNTRY || Country of origin of the player (AUS: Australia; IND: India; PAK: Pakistan; SA: South Africa; SL: Sri Lanka; NZ: New Zealand; WI: West Indies; OTH: Other countries) |
| YEAR.A || Year of auction in IPL |
| IPL.TEAM || Team(s) for which the player had played in the IPL (CSK: Chennai Super Kings; DC: Deccan Chargers; DD: Delhi Daredevils; KXI: Kings XI Punjab; KKR: Kolkata Knight Riders; MI: Mumbai Indians; PWI: Pune Warriors India; RR: Rajasthan Royals; RCB: Royal Challengers Bangalore). A + sign was used to indicate that the player had played for more than one teams. For example, CSK+ would mean that the player had played for CSK as well as for one or more other teams. |

#### 5.9.1 Importing a Dataset

The data collected resides in a csv file. The ‘read.csv’ function is used to read the dataset from the current working directory. If you are not sure of the current working directory from where the file will be read, you can use

**1.** getwd( ) function to get your working directory and

**2.** setwd( ) function to set your working directory.

By default, the read.csv file only expects the path to the file name. However, we use an additional argument na.strings( ) to embed *NA* wherever there is a garbage value in the dataset. The garbage value being looked for is c(““, “ “, “NA”). This operation is being performed as **R** recognizes *NA* as a missing value and not a blank space. This operation of embedding *NA* can as well be performed after the data. However, it is much more efficient to carry out this step at the beginning. **[Table 5.10](#13_Chapter05.xhtml#tab5.10)** shows the snapshot of the data.

![](images/page142-01.png)![](images/page143-01.png)

Once the dataset is loaded in a data frame, we can look into the data types by using the below code chunk.

![](images/page143-02.png)

The str( ) function shows that the ipl\_df has 130 observations across 27 variables. The dim(ipl\_df) function can also be used to show the dimension of the dataframe. summary (ipl\_df) will return the summary of the data.

The summary of the ipl\_df reveals that COUNTRY has observations from some of the countries which are less in frequency. Tabulation using table() function reveals more details.

![](images/page144-01.png)

We will merge some of these countries in a new label called OTHERS. The reason for merging the labels will be to avoid issues in train and test data creation (later in the chapter). Lower-frequency count can also lead to issues which create cross-validation (CV) set as there may not be observation corresponding to a few countries in some of the CV sets.

![](images/page144-02.png)

We can build a model to understand which features of the players influence their ‘SOLD PRICE’ and if the players’ prices can be predicted in future. However, all columns in ipl\_df cannot be used for model building. For example, Sl. NO. is an identifier and not a feature!!! Also note that the variable AGE is being recognized as a numeric variable but the meta data definition terms it as a categorical variable. This means that typecasting of variable will be needed to convert into correct data type. The below code chunk does typecasting of AGE and CAPTAINCY\_EXP variable by using the function as.factor( ).

We will remove SL. No. from the variable list before performing any further analysis. We also performed an additional step of row-wise deletion of missing values by using na.omit function. Note that the use of embedding *NA* while loading the data was done to enable this step of deleting the rows wherever there is no data available in even one of the columns. This step does not delete any observation in the data frame as there is no missing value. However, the step is useful while dealing with dataset where there is missing information.

It should be noted that the row-wise deletion of missing value should be carried out after having tried the imputation techniques to fill up the missing cases. **[Table 5.11](#13_Chapter05.xhtml#tab5.11)** shows the prepared data.

![](images/page144-03.png)![](images/page145-01.png)

#### 5.9.2 Creating Feature Set (X) and Outcome Variable (Y)

Let us write a generic function to extract the predictors and response variable from the dataset.

![](images/page145-02.png)

Let us identify the features which we do not want as independent features in model building. Three such features are PLAYER\_NAME, TEAM, and AUCTION\_YEAR. We will also keep BASE\_PRICE outside the features list. The below code chunk removes these features from the predictor list.

![](images/page145-03.png)

We can also get numeric and categorical predictors separately.

![](images/page146-01.png)

Most of the time, R internally performs **encoding** for categorical variables. However, for a few advanced machine learning algorithms, one has to explicitly perform the encoding for categorical variable.

#### 5.9.3 Encoding Categorical Features

The IPL dataset contains both quantitative and qualitative variables. Qualitative or categorical variables need to be encoded using dummy variables before incorporating them in regression model. If a categorical variable has *n* categories, it will need *n* - 1 dummy levels to represent the *n* categories. Dummy variables are binary variables taking values 0 and 1.

The read.csv() method, by default, treats categorical variable as a factor variable. Factor variables are assigned a set of integer codes based on the ordering of the alphabet. R then uses model.matrix() method, creates the dummy variable encoding automatically, and assigns the reference category (base category) to the label which appears first in alphabetical ordering.

Let’s understand the concept of dummy variable coding using the variable PLAYING. ROLE in IPL dataset. Let us say, the ‘PLAYING.ROLE’ variable in the data has four categories (batsman, bowler, wicket keeper, and allrounder).

![](images/page146-02.png)

**[Table 5.12](#13_Chapter05.xhtml#tab5.12)** shows 0-1 coding for all labels of PLAYING.ROLE. In this case, we have four labels, so four columns are created, and one is marked in the column corresponding to the presence of the label.

However, if we drop the column name PLAYING\_ROLE(Allrounder) from **[Table 5.12](#13_Chapter05.xhtml#tab5.12)** and create a new **[Table 5.13](#13_Chapter05.xhtml#tab5.13)**, we are still able to represent all four labels. The label ‘Allrounder’ is depicted by ‘0 0 0’ and is termed as the base category.

**Dummy variable encoding** is a popular technique to represent a categorical variable, before applying any machine learning technique. The flip side of using dummy variable encoding is that it increases the dimensions of the data when the number of labels in categorical variable is large.

![](images/page146-03.png)![](images/page147-01.png)

There are other **advanced encoding techniques** like ordinal encoding, binary encoding, feature hashing, word-to-vec, etc., which may be useful representation of categorical variable when the data size is large and the number of labels in categorical feature is too many.

**Model building** is an iterative process. Selection of right set of features to build the model may need business intervention as well as model selection strategies like Akaike Information Criteria (AIC).

The reason for creating the (n - 1) dummy variable coded column to represent *n* labels is that inclusion of dummy variables for all categories and the constant in the regression equation will create perfect multicollinearity (will be discussed later).

Since R uses model.matrix() method and creates the dummy variable encoding automatically, it marks the label which comes first in alphabetic order as the base category. This means for the PLAYING.ROLE variable, the label *‘Allrounder’* will be treated as the base category.

Note that for some of the algorithms, we may have to explicitly create dummy variable coded columns. We can create dummy variable coded column by using model.matrix() method from the stats package or dummyVars() methods from the caret package.

#### 5.9.4 Create Train and Test Set

createDataPartition( ) function from the caret package provides the ability to split the dataset randomly into training and validation datasets.

**1.** The function expects a vector to be passed and in our case, we are passing one of the variables named salary to it.

**2.** It also expects the percentage of data that should go into training set, which we have set to 0.80.

**3.** Finally, by marking *list = FALSE* we expect train\_index to contain a matrix with the number of rows equal to floor(0.80 \* length(Salary)) times number of columns, that is, two.

However, even before calling createDataPartition( ) we have used set.seed( ) function to maintain repeatability and reproducibility of the results. This is an important step before performing any operation which deals with random partition or the random generation of number.

We encourage you to comment on the set.seed( ) function and run the below code chunk multiple times. Notice the observations which get into train and test dataframe in each execution.

![](images/page147-02.png)

We have created two new dataframes with only the features which will be used for model building.

#### 5.9.5 Model Building: Using the Caret Package

Let us use the caret package described in [Section 5.4.5](#13_Chapter05.xhtml#sec5.4.5) to build the multiple linear regression model.

![](images/page147-03.png)![](images/page148-01.png)

As per the p-value (<0.05), only the feature COUNTRYENG has come out significant. The model interpretation at a p-value of 0.05 suggests that none of the other features influence SOLD PRICE at 5% significance. A closer look at some of the variables suggests interesting insights:

**1.** Batting strike rate comes with a negative estimate (SR\_B with an estimate of −784). This suggests that the SOLD\_PRICE of the player will decrease by 784 units for every unit increase in batting strike rate.

**2.** Bowlers suffer the most as the SOLD\_PRICE for bowlers decreases by 1829 units if the bowling strike rate (ODI\_SR\_BL) improves by one unit.

A similar interpretation can be seen for other variables in the regression results. These results seem counter-intuitive and could be a result of the multicollinearity effect of variables. We will discuss issues arising out of multicollinearity and ways to deal with it. However, the other point to note is that for categorical variables ‘AGE’, ‘COUNTRY’, ‘CAPTAINCY\_EXP’, and ‘PLAYING\_ROLE’, the dummy variable coding was done automatically.

#### 5.9.6 Significance of Multicollinearity

When the dataset has a large number of independent variables (features), it is possible that a few of these independent variables (features) may be highly correlated (Pradhan and Kumar, 2019). The existence of a high correlation between independent variables is called multicollinearity. Presence of multicollinearity can destabilize the multiple regression model. Thus, it is necessary to identify the presence of multicollinearity and take corrective action. Multicollinearity can have the following impact on the model:

**1.** The standard error of estimate, ![](images/pageIn_ch5-17.png), is inflated.

**2.** Statistically significant feature variable may be labelled as statistically insignificant. This is due to the fact that when the standard error of estimate is inflated, it can result in underestimation of the f-statistic value.

**3.** The sign of the regression coefficient may be different, that is, instead of negative value for regression coefficient, we may have a positive regression coefficient and vice versa.

**4.** Adding/removing a variable or even an observation may result in a large variation in regression coefficient estimates.

#### *Variance Inflation Factor (VIF)*

Variance Inflation Factor (VIF) is a measure of how much the variance of the estimated regression coefficients is inflated compared to when the predictor variable is not linearly related. For example, consider two independent variables *X*[1] and *X*[2] and the regression between them.

![](images/page149-01.png)

Let *R*[12] be the R-squared value of this model. Then the VIF, which is a measure of multi-collinearity, can be given by

![](images/page149-02.png)

The higher the VIF, the higher is the collinearity. ![](images/pageIn_ch5-18.png)is the value by which the standard error of regression coefficient is inflated. Say, the square root of the VIF is 2.5. This means the standard error for the coefficient of that predictor variable is 2.5 times as large as it would be if the predictor variable were uncorrelated with the other predictor variables.

A VIF value greater than 4 requires further investigation to assess the impact of multicollinearity.

**1.** ![](images/pageIn_ch5-19.png)Not Correlated

**2.** ![](images/pageIn_ch5-20.png)Moderately Correlated

**3.** ![](images/pageIn_ch5-21.png)Highly Correlated

A VIF is calculated for each explanatory variable and those with high values are removed.

![](images/page150-01.png)

If all terms in an unweighted linear model have 1 *df,* then the usual VIFs are calculated. If any terms in an unweighted linear model have more than 1 df, then the generalized variance-inflation factors (GVIFs) are calculated and adjusted for the degree of freedom. *GVIF^(1/(2\*df))* is the adjusted VIF where *df* denotes the degrees of freedom associated with the term.

#### *Identify Correlated Features*

Generally, the issue of multicollinearity may not arise if the correlation among features has been analyzed before model building and the one among the correlated variables has been dropped from the data. We will build a correlation matrix, **[Table 5.14](#13_Chapter05.xhtml#tab5.14)**, among the numeric variables by using the cor( ) function.

![](images/page150-02.png)

Since the values above and below the diagonal elements in **[Table 5.14](#13_Chapter05.xhtml#tab5.14)** are the same, we can use upper.tri() and lower.tri() function from the base package to return upper-triangle and lower-triangle matrix.

![](images/page150-03.png)![](images/page151-01.png)

Using **[Table 5.14](#13_Chapter05.xhtml#tab5.14)**, we will draw a correlation heatmap.

![](images/page152-01.png)

The diagonal line in **[Figure 5.3](#13_Chapter05.xhtml#fig5.3)** represents the correlation of the feature with itself and can be ignored. For other features, the darker shades reflect features which are highly correlated (positive as well as negative). From **[Figure 5.3](#13_Chapter05.xhtml#fig5.3)**, we can see highly correlated features such as AVE\_BL and SR\_BL.

#### *Handling Multicollinearity*

When the feature set is large, it becomes difficult to read the correlation matrix and find out the variables which are highly corelated. **caret** package has a function findCorrelation( ) which takes correlation matrix as an input. At a user-defined cut-off value, this function will print the names of the variables which are correlated with other variables at the specified cut-off.

![](images/page152-02.png)![](images/page153-01.png)

At a correlation cut-off of 0.6, from **[Table 5.14](#13_Chapter05.xhtml#tab5.14)**, we can conclude that the highest runs scored by a batsman in IPL (HS) is highly correlated with:

**1.** Average runs scored by a batsman in IPL(AVE\_B)

**2.** Number of runs scored by a player in IPL (RUNS\_S)

**3.** Number of sixes (SIXERS) hit in IPL.

However, as can be seen from the outcome of findCorrelation() result, out of the four features which are correlated, the features SIXERS is not printed. This is so as findCorrelation() function looks at the Mean Absolute Correlation (MAC) of each variable and removes the variables with the largest MAC. As an example, the MAC for ‘HS’ from **[Table 5.15](#13_Chapter05.xhtml#tab5.15)** can be calculated as 0.448.

**[Table 5.16](#13_Chapter05.xhtml#tab5.16)** lists the MAC for the four variables.

As can be seen, the variables to be dropped are HS, AVE\_B, and RUNS\_S as they have the highest MAC values. Similarly, from **[Table 5.14](#13_Chapter05.xhtml#tab5.14)**, the number of runs scored by a player in ODIs (ODI\_RUNS\_S) and number of runs scored in Test cricket (T\_RUNS) are highly correlated (>0.60). The MAC values are shown in **[Table 5.17](#13_Chapter05.xhtml#tab5.17):**

So the variable to be dropped is ODI\_RUNS\_S. Similarly,

• **[Table 5.18](#13_Chapter05.xhtml#tab5.18)** shows the MAC among bowling strike rate in IPL (SR\_BL), bowling average (AVE\_BL), and economy rate IPL (ECON).

• Number of wickets taken in IPL (WKTS) is highly correlated with runs conceded in IPL (RUNS\_C). The MAC is shown in **[Table 5.19](#13_Chapter05.xhtml#tab5.19).**

• Wickets taken in ODIs (ODI\_WKTS) is highly correlated with wickets taken in Tests (T\_WKTS). **[Table 5.20](#13_Chapter05.xhtml#tab5.20)** shows the MAC between these variables.

From **[Tables 5.18](#13_Chapter05.xhtml#tab5.18), [5.19](#13_Chapter05.xhtml#tab5.19)**, and **[5.20](#13_Chapter05.xhtml#tab5.20)**, we can conclude that:

**1.** The variable to be dropped in the first case is SR\_BL and AVE\_BL.

**2.** The variable to be dropped in the second case is WKTS.

**3.** The variable to be dropped in the third case is ODI\_WKTS.

Thus ‘HS, ‘AVE\_B, ‘RUNS\_S’, ‘ODI\_RUNS\_S, ‘SR\_BL, ‘WKTS’, AVE\_BL, and ‘ODI\_WKTS’ are the variables identified by findCorrelation( ) function which is marked for removal. Though the above variables have been highlighted by findCorrelation( ) function and it is being suggested that they be removed, the final call on retaining or removing a variable depends on understanding of the data and the domain. In actual business scenarios, it may take multiple iterations before deciding at a final set of variables, which do not have multicollinearity. The final set of variables thus decided were ‘HS’, ‘AVE\_B’, ‘RUNS\_S’, ‘T\_RUNS’, ‘AVE\_BL’, ‘ECON’, ‘RUNS\_C’, ‘T\_WKTS’, ‘SR\_BL’, ‘SR\_B’, and ‘ODI\_SR\_B’.

#### 5.9.7 Rebuild Model: Using the Caret Package

Now we will build a new IPL train and test set by removing the variables identified for exclusion in the above section. Let’s revisit the predictor list created in the previous section and remove some more features.

![](images/page154-01.png)![](images/page155-01.png)

We will run the regression model with the new train set.

![](images/page155-02.png)![](images/page156-01.png)

The *p*\-values of the estimated coefficients show if the variables are statistically significant in influencing response variables or not. If the *p*\-value is less than the significance value (α), then the feature is statistically significant; otherwise it is not. The value of α is usually selected as 0.05. However, it may be chosen based on the context of the problem.

Using the understanding of VIF, we can infer that none of the variables in the ipl\_ new\_reg\_model have multicollinearity and thus can be sure that the standard error of the estimated coefficients will not be inflated.

![](images/page156-02.png)![](images/page156-03.png)

**TABLE 5.17** | MAC value between ODI runs scored and test runs scored

| ODI\_RUNS\_S || T\_RUNS |
| --- | --- |
| 0.371 || 0.331 |
| --- | --- |

![](images/page156-04.png)

**TABLE 5.19** | MAC value between wickets taken and runs conceded in IPL

| WKTS || RUNS\_C |
| --- | --- |
| 0.341 || 0.339 |
| --- | --- |

**TABLE 5.20** | MAC value between ODI wickets taken and test match wickets takes

| ODI\_WKTS || T\_WKTS |
| --- | --- |
| 0.2642 || 0.2628 |
| --- | --- |

#### *Model Selection Using AIC*

Based on the *p*\-values, reported by using ipl\_new\_reg\_model object, only the variables COUNTRYENG and SIXERS have come out statistically significant. The interpretation of these features on the SOLD\_PRICE is as follows:

**1.** On an average, SOLD\_PRICE of player goes up by $562,423 for players from England compared to players from Australia (base category).

**2.** On an average, SOLD\_PRICE of player goes up by $4,683 for every unit increase in the number of sixes hit.

However, there are other variables in the regression result for which the *p*\-value is greater than 0.05. These variables would have impacted the beta coefficient estimate of significant variables as well. We have to remove these insignificant variables and run a regression again to find the true beta estimate of the significant variable. Moreover, removal of an insignificant variable has to be carried out by assessing the impact of its removal on all other variables. This assessment is needed as there will be always a certain degree of correlation among all the independent variables, which will render some significant variables insignificant. Another way to look at it is that every addition or deletion of a variable means creating a new model and thus there are many models from which to select the best model. This seems like an iterative process and may require many steps to remove all insignificant variables.

In order to overcome the issue of running the regression model in iterations, the caret package has a method lmStepAIC() which implements the strategy of variable selection and elimination by looking at **Akaike information criterion** (AIC).

As the name suggests, lmStepAIC() is a step function which uses AIC as a criterion for model selection. AIC estimates the quality of each model, relative to each of the other models, for a given set of variables. Thus, AIC provides a means for making a simple model by retaining fewer predictor variables.

AIC does not provide a test of a model in terms of null hypothesis and thus it does not say anything about the absolute quality of a model but only the quality relative to other models.

Formula to compute AIC is

![](images/page157-01.png)

In [Eq. (5.27)](#13_Chapter05.xhtml#eq5.27),

• *n* is the number of observations in the data.

• *RSS* is the regression sum of squares.

• *k* is the penalizing factor. Usually, *k* = 2 is used for calculating AIC. *k* = log(n) is sometimes referred to as Bayesian Information Criteria (BIC).

• *P* is the number of parameters in the model.

The below code chunk implements the regression model using lmStepAIC() method and backward elimination strategy. lmStepAIC() method calls stepAIC() function from the **MASS** package.

![](images/page157-02.png)![](images/page158-01.png)![](images/page159-01.png)

#### *Understanding AIC Steps*

Let us first calculate the initial AIC value using [Eq. \[5.27\]](#13_Chapter05.xhtml#eq5.27). We will use **ipl\_new\_reg\_model** object which was developed using lm() method from the caret package for calculating the initial AIC.

![](images/page159-02.png)

Let us understand the ipl\_aic\_reg\_model object which is an outcome of the **lmStepAIC** and has resulted in four iterations:

• Iteration 1:

– The start AIC value for ipl\_aic\_reg\_model is 2702.4. This value signifies that all the independent variables were included in the model. We calculated this value manually using the **ipl\_new\_reg\_model** object created by **lm()** method and found this value to be same, that is 2702.4.

– ‘none’ category in ipl\_aic\_reg\_model corresponds to a model that would include all the variables. In other words, none of the variables was removed and the AIC value corresponding to this is 2702.4.

– PLAYING\_ROLE: This builds a model with PLAYING\_ROLE variable removed from the model while retaining all other variables. In ipl\_aic\_reg\_model, the AIC value with PLAYING\_ROLE removed from the model is 2699.7. Let us reproduce this AIC value manually using **lm()** method.

![](images/page159-03.png)![](images/page160-01.png)

We found the AIC value to be same as 2699.7.

• Iteration 1 Continued:

– ODI\_SR\_BL: This builds a model with ODI\_SR\_BL variable removed from the model and retaining all other variables. The AIC value with ODI\_SR\_BL removed from the model is 2700.8. Let us reproduce this AIC value manually using lm() method.

![](images/page160-02.png)

• Iteration 1 Continued

– WKTS: This builds a model with WKTS variable removed from the model and retaining all other variables. The AIC value with WKTS removed from the model is 2701.1. We suggest you check this manually by modifying the code chunk above.

– Step 1 is complete after all variables are individually removed and the model is built with the remaining variables.

– The resulting table in iteration 1 has AIC corresponding to each model.

– In this case, we see that the model with PLAYING\_ROLE excluded from the variable list gives the minimum AIC value (2699.7).

Let’s see Iteration 2.

• Iteration 2:

– The AIC for the starting model is 2699.7. This is the model with PLAYING\_ROLE variable excluded from the model as the starting point.

– ‘none’ category corresponds to a model that would include all variables but PLAY-ING\_ROLE.

– ODI\_SR\_BL: This builds a model with ODI\_SR\_BL variable removed from the model and retaining all other variables. The AIC value with ODI\_SR\_BL removed from the model is 2697.7. Let us reproduce this AIC value manually.

![](images/page161-01.png)

• Iteration 2 continued

– WKTS: This builds a model with WKTS variable removed from the model and retaining all other variables. The AIC value with WKTS removed from the model is 2698.7. We suggest you check this manually by modifying the code chunk above.

– Iteration 2 is complete after all variables are individually removed and the model is built with the remaining variables.

– The resulting table in Step 2 has AIC corresponding to each model. The model which has the lowest AIC value is picked for the third step.

– In this case, we see that the model with ODI\_SR\_BL excluded from the variable list had the lowest AIC value (2697.7).

The model with the minimum AIC value from the previous step becomes the starting model for the subsequent step every sing time. The logic explained in iteration 1 and iteration 2 follows for iteration 3 as well. So, we go to the last iteration, that is, iteration 4.

• Iteration 4:

– The AIC for the starting model is 2696.7. This is the model with WKTS variable excluded from the model as the starting point.

– ‘none’ category corresponds to a model that would include all variables except WKTS.

– CAPTAINCY\_EXP: This builds a model with CAPTAINCY\_EXP variable removed from the model and retaining all other variables. The AIC value with CAPTAIN-CY\_EXP removed from the model is 2696.8. We suggest you check this manually by modifying the code chunk above.

– Iteration 4 is complete after all variables are individually removed and the model is built with the remaining variables.

– The resulting table in iteration 4 has AIC corresponding to each model. The model which has the lowest AIC value is picked for the next step.

– However, in this case, we see that there is no model with a lower AIC value compared to the initial model (AIC: 2697.7)

Thus, the best model is found at iteration 4. The starting point for stepAIC() was a full model and at each step, the model was built using all the variables barring one and the AIC value was calculated for each of these models. The model with the minimum AIC value was selected for the subsequent step.

#### 5.9.8 Model Summary

The object **ipl\_aic\_reg\_model** has the final model. The summary() of this model object shows some of the statistics saved in it.

![](images/page162-01.png)

From the summary output show, we can infer the following:

The model adjusted *R*\-square value is 0.3987, adjusted *R*\-square value is calculated by normalizing SSE and SST by corresponding degrees of freedom. As can be seen from the summary of the **ipl\_aic\_reg\_model** object, the variables retained in the final model are:

**1.** COUNTRY

**2.** ODI\_WKTS

**3.** ODI\_RUNS\_S

**4.** SIXERS

However, the point to note is that the variables retained in the model may still have insignificant variables. This is so because lmstepAIC() selects the model based on AIC, not *p*\-values. The goal is to find the model with the smallest AIC by removing or adding variables in the scope. If AIC has been used for model selection, it is better to consider all the variables retained in the final model even if the *p*\-values are greater than 0.05.

One of the parameters which controls the variables’ selection is a penalizing factor which is set by default to 2 (*k* = 2 in the parameter settings of stepAIC() in MASS package). Since each variable in the model is penalized with a factor of 2, we have some of the variables with *p*\-value > 0.05 in the final model. In order to report only the variables with *p*\-value < 0.05 in the final model, we have to set the *k* parameter in step function to 3.84 (~ 4). However, this change in the value of *k* is generally not done. The sample code change is given below:

ipl\_aic\_k\_3.84\_reg\_model = train(ipl\_train\_df\[new\_predictors\], ipl\_train\_df \[response\], method = “lmStepAIC”, k = 3.84, trControl = obj\_control, metric = “Rsquared”) summary (ipl\_aic\_k\_3.84\_reg\_mo del$finalModel)

### 5.10 | Model Diagnostic

It is important to validate the multiple linear regression model to ensure its validity and goodness of fit before it can be used for practical applications. The following measures are used to validate simple linear regression models:

**1.** Co-efficient of determination (R-square).

**2.** Hypothesis test for the regression coefficient.

**3.** Analysis of variance (ANOVA) for overall model validity (relevant more for multiple linear regression).

**4.** Residual analysis to validate regression model assumptions.

**5.** Outlier analysis.

We discussed the above points in simple linear regression. All the validation checks for simple linear regression model metrics hold good for multiple linear regression as well. We can augment the ipl\_train\_df data to add fitted values and residuals by using augment() from broom package. The resultant data.frame, say diagnostic\_ metrics, contains several metrics useful for model diagnostics. The plot() function when used on the regression object model actually uses diagonstic\_metrics to give various plots useful for residual analysis and outlier analysis.

![](images/page163-01.png)

.outcome is the SOLD\_PRICE in the ipl\_train\_df. The diagonstic\_metrics also contains all features which are a part of the final model. However, not all the columns and rows are shown in **[Table 5.21](#13_Chapter05.xhtml#tab5.21)** (to maintain readability). The other columns in the diagonstic\_metrics are as follows:

![](images/page164-01.png)

**1.** .fitted: fitted values (predicted values)

**2.** .resid: residual errors (.outcome - fitted)

**3.** .hat: to detect high leverage points (or extreme values in the predictors X variables)

**4.** .cooksd: Cook’s distance, used to detect influential values, which can be an outlier or a high leverage point. A Cook’s distance of 0.013 for observation *X*[6] suggests that removing this observation from the training data would have changed the predicted value of *Y* by 0.013 (on an average).

**5.** .std.resid: Standardized residuals. This is arrived at by dividing residuals by their standard errors. .std.resid is used to detect outliers (or extreme values in the outcome *y* variable).

#### 5.10.1 Linearity Assumption

**[Figure 5.4](#13_Chapter05.xhtml#fig5.4)** shows the linearity assumption.

![](images/page164-02.png)

If the red line is approximately horizontal at zero, then the functional form can be assumed to be correctly specified. The presence of a pattern may indicate a problem with some aspect of the linear model.

From residual vs. fitted in ipl\_train\_df, we may conclude that the functional form of the regression (linear relationship between *X* and *Y*) may not be correct.

![](images/page164-03.png)

#### 5.10.2 Normality Assumption

![](images/page165-01.png)

From **[Figure 5.5](#13_Chapter05.xhtml#fig5.5)**, the Q-Q plot, we can conclude that the residuals follow an approximate normal distribution (we need only an approximate normal distribution).

#### 5.10.3 Homogeneity Assumption

![](images/page165-02.png)

From **[Figure 5.6](#13_Chapter05.xhtml#fig5.6)**, the scale-location plot, the residuals are not random and seem to clutter towards the bottom left of the chart, which means the residuals do not have constant variance (homoscedasticity).

#### 5.10.4 Outliers and High Leverage Points

Observations with high Z-score and high leverage points can be identified by inspecting the residuals vs. leverage plot.

![](images/page165-03.png)![](images/page165-04.png)![](images/page166-01.png)

By default, the plot only highlights the top three points which are either high on leverage or have a Z-score greater. To highlight top ten points, we can use id.n=10 in the plot().

![](images/page166-02.png)

In **[Figure 5.7](#13_Chapter05.xhtml#fig5.7)**, the horizontal axis shows the leverage value and the Cook’s distance of the observation *(Xs)* and the vertical axis shows the Z-score.

**[Figure 5.8](#13_Chapter05.xhtml#fig5.8)** highlights top 10 observations with either high Z-score, high leverage, or high Cook’s distance. However, these observations do not necessarily have

**1.** .std.resid (z-score)>3

**2.** .hat (leverage) > = 3(p + 1)/n where*p* is the number of predictors and *n* is the number of observations.

**3.** .cooksd (cook’s distance) > = 0.5 or .cooksd (cook’s distance) > = 4/(n-p-1) where *p* is the number of predictors and *n* is the number of observations.

In mba\_train\_df, none of the observations are to the upper or lower right of the residual vs. leverage plot (dotted region of 0.5 and above in **[Figure 5.7](#13_Chapter05.xhtml#fig5.7)).** Thus, there are no cases influential to the regression results.

![](images/page166-03.png)

Using the leverage threshold calculation formula 3(*p* + 1)/*n*, let us calculate the leverage\_threshold which will be used later.

![](images/page167-01.png)

#### 5.10.5 Influential Values

Outliers based on Cook’s distance threshold can be identified by inspecting the Cook’s distance plot as well as the residuals vs. leverage plot discussed in the previous section.

By default, Cook’s distance plot highlights the top three influential points. To highlight top ten observations, we can use id.n=10 in the plot(). The following plots illustrate Cook’s distance and the leverage of our model:

![](images/page167-02.png)

**[Figure 5.8](#13_Chapter05.xhtml#fig5.8)** highlights the top ten observations with high Cook’s distance score. However, it is not necessary that these observations have a .cooksd value above 4/(*n* - *p* - 1) where *p* is the number of predictors and *n* is the number of observations.

![](images/page167-03.png)

We will use the Cook’s threshold in the next section to identify the influential cases.

#### 5.10.6 Identify Outlier Cases in Dataframe

In sections 5.10.4 and 5.10.5, we looked at the plots to visually identify the cases which may be outliers. But these visuals are limited to identifying the top *n* cases. Let’s try to identify all cases which are either high on Z-score, leverage, or Cook’s distance. We have all the statistics saved in diagonstic\_metrics data.frame **([Table 5.21](#13_Chapter05.xhtml#tab5.21)).** It shows the first 7 columns of this data frame for better readability.

**[Table 5.22](#13_Chapter05.xhtml#tab5.22)** shows all the cases with high Z-score (Z-score > 3). Since **[Table 5.22](#13_Chapter05.xhtml#tab5.22)** has no records, it is evident that none of the cases are above the Z-score threshold.

![](images/page167-04.png)

We calculated the leverage\_threshold in [Section 5.10.4](#13_Chapter05.xhtml#sec5.10.4). **[Table 5.23](#13_Chapter05.xhtml#tab5.23)** shows all the cases with high leverage (.hat>leverage\_threshold)

![](images/page167-05.png)![](images/page168-01.png)![](images/page168-02.png)![](images/page168-03.png)

We calculated the cooks\_threshold in [Section 5.10.5](#13_Chapter05.xhtml#sec5.10.5). However, we will go with the cooks\_threshold of 0.5 and above (generally accepted). Let us get all the cases with high Cook’s distance (.cooksd>cooks\_threshold).

![](images/page169-01.png)

As evident from **[Table 5.24](#13_Chapter05.xhtml#tab5.24)**, there are no cases with Cook’s distance of 0.5 and above, and thus there are no influential cases in the ipl\_train\_df.

We will leave the next steps of building a model after removing the influential observations to the reader to try out themselves for practice.

#### 5.10.7 Transforming Response Variable

Transformation is a process of deriving new dependent and/or independent variables to identify the correct functional form of the regression model (Kumar, 2017). For example, the dependent variable *Y* may be replaced in the model with ln(Y), 1/Y, etc.; similarly, an independent variable *X* may be replaced with ln(X), 1*/X,* etc. Transformation in MLR is used to address the following issues:

**1.** Poor fit (low *R*\-squared value).

**2.** Pattern in residual analysis indicating potential non-linear relationship between the dependent and the independent variables.

**3.** Residuals do not follow a normal distribution.

**4.** Residuals are not homoscedastic.

Transforming and creating a new variable using *R* can be carried out in the dataframe. The below code chunk creates a new variable named SQRT\_SOLD\_PRICE. We will use this variable to create a new model and analyze if the model assumptions are satisfied.

![](images/page169-02.png)![](images/page170-01.png)

#### 5.10.8 Model Summary - Transformed Variable

![](images/page170-02.png)![](images/page171-01.png)

From **[Figure 5.9](#13_Chapter05.xhtml#fig5.9)**, we can conclude that the transformation of the variable seems to improve the model slightly but does not bring about any significant change. We will use this model to make predictions on the test set.

Normality and homoscedasticity of error term, understanding outliers and influential values in data using z-score, Cooks distance, etc., are important diagnostic steps in **model building phase****.**

![](images/page171-02.png)

### 5.11 | Making Predictions and Measuring Accuracy

After the final model is built as per our requirements and the model has passed all diagnostic tests, we can apply it to the validation data to predict the SOLD PRICE (Pradhan and Kumar, 2017). As the model we have built predicts square root of the SOLD PRICE, we need to square the predicted values to get the actual SOLD PRICE of the players.

The **predict** function is used to get the predicted response on the new dataset. You may get an error message if the test data has got any new categories which were not there in the training set. This generally happens when the data has a categorical variable with multiple levels.

![](images/page172-01.png)

**[Table 5.25](#13_Chapter05.xhtml#tab5.25)** shows the outcome for prediction on the test data. There are several measures that can be used for measuring the accuracy of prediction. MLmetrics package gives a collection of evaluation metrics to measure the performance of regression and classification algorithms. caret also has inbuilt evaluation functions like R2() for R-squared, and RMSE() to compute root mean squared error. These functions expect observed and predicted values to be passed as arguments.

![](images/page172-02.png)

The accuracy (*R*\-squared) value on validation set (0.36) is quite low but comparable to the *R*\-squared reported by the model on training dataset (0.39).

![](images/page172-03.png)

### Summary

In this chapter, we learnt how to build, diagnose, understand, and validate simple and multiple linear regression models using R.

**1.** The multiple linear regression model is used to find the existence of association relationship between a dependent variable and more than one independent variables.

**2.** In MLR, the regression coefficients are called partial regression coefficients, since they measure the change in the value of the dependent variable for every one unit change in the value of independent variable, when all other independent variables in the model are kept constant.

**3.** While building the MLR model, the categorical variables with *n* categories should be replaced by (n - 1) dummy (binary) variables to avoid model mis-specification.

**4.** Apart from checking for normality and heteroscedasticity, every MLR model should be checked for presence of mul-ticollinearity, since multicollinearity can destabilize it.

**5.** Transforming variables can be done to improve accuracy or remove heteroscedasticity and enhance the model fit.

### Exercises

#### Answer Questions 1-4 using the following dataset. Develop R code to answer the following questions:

The dataset *country.csv contains* corruption perception index and Gini index of 20 countries. Corruption perception index close to 100 indicates low corruption and close to 0 indicates high corruption. Gini index is a measure of income distribution among citizens of a country (high Gini indicates high inequality). Corruption index is taken from Transparency International, while Gini index is sourced from Wikipedia.

**1.** Develop a simple linear regression model (Y = *b[0]* + *b*[1]*X)* between corruption perception index (*Y*) and Gini index ( *X).* What is the change in the corruption perception index for every one-unit increase in Gini index?

**2.** What proportion of the variation in corruption perception index is explained by Gini index?

**3.** Is there a statistically significant relationship between corruption perception index and Gini index at alpha value 0.1?

**4.** Calculate the 95% confidence interval for the regression coefficient *b*[1].

#### **Answer Questions 5-13 using the following dataset. Develop R code to answer the following questions:**

The dataset DAD hospital (dad\_hospital.csv) contains data about cost of treatment for patients. It also contains information about patient’s demographics and health parameters. The following are the description of the columns in the dataset.

| Sl\_NO || Description |
| --- | --- |
| AGE || Patients’ age |
| --- | --- |
| GENDER || M for Male and F for Female |
| MARITAL\_STATUS || Patient is married or unmarried |
| KEY\_COMPLAINTS\_CODE || Code for patients’ complaint. The key health condition for which the patient was treated. |
| BODY\_HEIGHT || Body height |
| HR\_PULSE || Heart pulse rate |
| BP\_HIGH || Systolic blood pressure |
| BP\_LOW || Diastolic blood pressure |
| RR || Respiratory Rate |
| PAST\_MEDICAL\_HISTORY\_CODE || Code of patients’ medical history, e.g., diabetes, hypertension etc. |
| HB || Hemoglobin Count |
| UREA || Urea Count |
| CREATININE || Creatinine count in blood and urine |
| MODE\_OF\_ARRIVAL || Mode of arrival, e.g., AMBULANCE, WALKED IN |
| STATE\_AT\_THE\_TIME\_OF\_ARRIVAL || Patients’ state at the time of arrival |
| TYPE\_OF\_ADMSN || Type of admission ELECTIVE, EMERGENCY |
| TOTAL\_COST\_TO\_HOSPITAL || Actual cost to the hospital |
| TOTAL\_AMOUNT\_BILLED\_TO\_THE\_PATIENT || Actual amount billed to the patient |
| CONCESSION || Concession given at the time of billing |
| ACTUAL\_RECEIVABLE\_AMOUNT || Actual amount received by the hospital |
| TOTAL\_LENGTH\_OF\_STAY || Number of days patients was admitted to the hospital |
| LENGTH\_OF\_STAY\_ICU || Number of days patients was admitted in the ICU |
| LENGTH\_OF\_STAY\_WARD || Number of days patients was admitted in the hospital’s ward |
| IMPLANT\_USED\_Y\_N || Any implants used |
| COST\_OF\_IMPLANT || Cost of implant used |

**5.** DAD hospital wants to understand the key factors influencing the cost to hospital are. The hospital wants to provide treatment packages (fixed price contract) to the patients at the time of the admission. Can the hospital build a model using the historical data to estimate the cost of treatment?

**6.** Read the DAD hospital data in R as a DataFrame. Build a correlation matrix between all the numeric features in the dataset. Report the features which are correlated at a cut-off of 0.70. What actions will you take on the features which are highly correlated?

**7.** Build a new feature named BMI using body height and body weight (ratio of weight to height). Include this as a part of the DataFrame created in question 6.

**8.** Select the features that can be used to build a model to estimate the cost to the hospital.

**9.** Identify which features are numerical and which are categorical. Create a new DataFrame with the selected numeric features and categorical features.

**10.** Which features have the symptoms of multicollinearity and need to be removed from the model?

**11.** Split the data into training set and test set. Use 80% of data for model training and 20% for model testing.

**12.** Build a regression model with *caret package* to estimate the total cost to hospital. How do you interpret the model outcome?

**13.** Find the outliers in the dataset using *Z*\-score and Cook’s distance. If required, remove the observations from the dataset.

### Bibliography

**1.** A Hayes (2021), “Convert Statistical Objects into Tidy Tibbles”, available at [https://www.rdocumentation.org/packages/broom/versions/0.5.2](https://www.rdocumentation.org/packages/broom/versions/0.5.2), accessed on 21 January 2021.

**2.** Anon (2019), “R caret only specify indexOut in trainCon-trol”, 2021, Web address: R caret only specify indexOut in trainControl - Stack Overflow, accessed on 10 May 2021.

**3.** Anon (2019), “Train: fit predictive models over different tuning parameters”, 2021, Web address: [https://rdrr.io/cran/caret/man/train.html](https://rdrr.io/cran/caret/man/train.html), accessed on 10 May 2021.

**4.** Anon (2020), “TrainControl.R”, 2021, Web Address: caret/ trainControl.R at master topepo/caret GitHub, accessed on 10 May 2021.

**5.** Anon (2021), “Stats v3.6.2”, available at [https://www.rdocumentation.org/packages/stats/versions/3.6.2](https://www.rdocumentation.org/packages/stats/versions/3.6.2), accessed on 21 January 2021.

**6.** Ben Roshan (2020), “Linear regression using R”, 2021, available at Part 7: Linear Regression using R | Kaggle, Web address: [https://www.kaggle.com/benroshan/discussion?sortBy=mostVotes&group=topics](https://www.kaggle.com/benroshan/discussion?sortBy=mostVotes&group=topics), accessed on 10 May 2021.

**7.** Khun M (2021), “The Caret Package”, available at [http://topepo.github.io/caret/index.html](http://topepo.github.io/caret/index.html), accessed on 21 January 2021.

**8.** Khun M (2021), “The Caret Package”, available at [https://www.rdocumentation.org/packages/caret/versions/6.0-84](https://www.rdocumentation.org/packages/caret/versions/6.0-84), accessed on 27 January 2021.

**9.** Kuhn M (2020), “Caret v6.0-86 - Classification and Regression Training”, Web address: [https://cran.r-project.org/web/packages/caret/index.html](https://cran.r-project.org/web/packages/caret/index.html), accessed on 10 May 2021.

**10.** Kumar UD and Ranjan K (2012), “Pricing of Players in the Indian Premier League”, Indian Institute of Management, Bangalore.

**11.** Kutner M H, Nachtsheim C J, Neter J and Li W (2005), “Applied Linear Models” 5th Edition, McGraw Hill, New York.

**12.** Pedersen, “ggplot2 v3.3.3”, available at [https://www.rdocumentation.org/packages/ggplot2/versions/3.2.1](https://www.rdocumentation.org/packages/ggplot2/versions/3.2.1), accessed on 21 January 2021.

**13.** Pradan M and Kumar UD (2019), “Machine Learning Using Python”, Wiley, Indian Institute of Management, Bangalore.

**14.** Wicham H, (2021), “reshape2 v1.4.4 - Flexibly Reshape Data: A Reboot of the Reshape Package”, available at [https://www.rdocumentation.org/packages/reshape2/versions/1.4.3](https://www.rdocumentation.org/packages/reshape2/versions/1.4.3), accessed on 21 January 2021.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#13_Chapter05.xhtml#ch5-fn1)[https://topepo.github.io/caret/available-models.html](https://topepo.github.io/caret/available-models.html).

[²](#13_Chapter05.xhtml#ch5-fn2)[https://topepo.github.io/caret/model-training-and-tuning.html#model-training-and-parameter-tuning](https://topepo.github.io/caret/model-training-and-tuning.html#model-training-and-parameter-tuning)

 

 
| 

## Classification Problems

 || 

## 6

 |
| --- | --- |

*He who knows, does not speak. He who speaks, does not know.*

**—Lao Tzu**

LEARNING OBJECTIVES

After reading this chapter, you would be able to:

• Understand the concept of classification problems and their applications across different industries.

• Learn to build logistic regression and decision tree models using the caret package.

• Learn to perform activities such as

• Splitting the dataset into training and validation,

• Building models using the caret package on training dataset and test on the validation dataset.

• Learn to measure model accuracies using confusion matrix, sensitivity (recall), specificity, precision, Receiver Operating Characteristic (ROC) curve, and Area Under ROC Curve (AUC).

• Learn the statistical significance of features, model diagnostics, and finding the optimal cut-off probabilities for classification in logistic regression.

### 6.1 | Classification Overview

Classification problems are an important category of problems in analytics in which the outcome variable or response variable (*Y*) takes a discrete value (Kumar, 2017). The primary objective of a classification model is to predict the probability of an observation belonging to a class, known as *class probability.* A few examples of classification problems are as follows:

**1.** A bank would like to classify its customers based on risk – low-risk or high-risk customers.

**2.** Organizations would like to predict whether a customer is likely to churn or not.

**3.** Health service providers may classify a patient, based on diagnostic results, as positive (presence of disease) or negative (absence of disease).

**4.** The HR department of a firm may want to predict if an applicant would accept an offer or not.

**5.** Cricket association may want to predict if the outcome of a test match will end in win, lose or draw for the home team.

**6.** Sentiment by customers on a product or service may be classified as positive, negative, neutral, and sarcastic.

**7.** Based on the image of a plant, one can predict whether it is infected with a specific disease.

Classification predictions may have binary or multiple outcomes or classes. Problems with binary outcomes are called binary classifications and problems with multiple class outcomes are called multiclass classifications. Several techniques are used to solve classification problems such as logistic regression, classification trees, discriminant analysis, K nearest neighbours (KNN), neural networks, and support vector machines. In this chapter, we will focus on Logistic Regression and Classification Tree for building and evaluating classification models.

### 6.2 | Binary Logistic Regression

Logistic regression is a statistical learning algorithm in which the outcome variable takes discrete values and the explanatory variables can either be continuous or discrete (Kumar, 2017). If the outcome variable takes only two values, then the problem is called binary class classification and the corresponding logistic regression model is called binary logistic regression model. Assume that the outcome variable values are called positive (usually coded as *Y* = 1) and negative (usually coded as *Y* = 0). Then, the binary logistic regression model is given by

![](images/page176-01.png)

In [Eq. (6.1)](#14_Chapter06.xhtml#eq6.1), the value of *Z* is given by

![](images/page176-02.png)

In [Eq. (6.2)](#14_Chapter06.xhtml#eq6.2), *X*[1]*, X*[2], …, *X*[*m*] are independent variables or features. The logistic function defined in [Eq. (6.1)](#14_Chapter06.xhtml#eq6.1) has an S-shaped curve (also known as Sigmoid function) and gives the class probability of an observation belonging to class labelled as 1 for specific feature variable values, that is, *P*(*Y* = 1|*X*). [Eq. (6.1)](#14_Chapter06.xhtml#eq6.1) can be rewritten as

![](images/page176-03.png)

The left-hand side of [Eq. (6.3)](#14_Chapter06.xhtml#eq6.3), is a log natural of odds and is known as logit function. The right-hand side is a linear function. Such models are called generalized linear models (GLMs). In GLM, the errors may not follow normal distribution and there exists a transformation function of the outcome variable that takes a linear functional form as shown in [Eq. (6.3)](#14_Chapter06.xhtml#eq6.3).

The probability (likelihood) function of binary logistic regression for specific observation *Y*[*i*] (*Y*[*i*] = 0 or *Y*[*i*] = 1) is given by (Kumar, 2017)

![](images/page176-04.png)

If the data has n observations, *Y*[1]*,Y*[2], … *Y*[*n*], then likelihood function, which is a joint probability of observation the outcome *L = P*(*Y*[1]*,Y*[2]*,*…*,Y*[*n*]) for a specific *Z = β*[0] + *β*[1]*\* X*[1] + *β*[2] \* *X*[2] +… + *β*[*m*] *\* X*[*m*], is given by

![](images/page176-05.png)

Taking natural log, [Eq. (6.5)](#14_Chapter06.xhtml#eq6.5) can be rewritten as

![](images/page176-06.png)![](images/page177-01.png)

When we multiply *LL* in [Eq. (6.6)](#14_Chapter06.xhtml#eq6.6) with −2 (that is, −*2LL*), we get Deviance which measures deviation from perfect model. The objective is to find the *β* coefficients which maximize [Eq. (6.6)](#14_Chapter06.xhtml#eq6.6), that is, we need to find the *β* coefficients that maximize the log likelihood function. The loss function for logistic regression is given by

![](images/page177-02.png)

Consider an example of classifying people with heart disease and without heart disease. That is, we are interested in finding the probability of suffering from a heart disease as a function of age. The outcome variable is that either someone suffers from heart disease or not, and the independent variable (feature) is age. Then, a logistic or Sigmoid function can be fit to explain the probability of suffering from heart disease with respect to age, as shown in **[Figure 6.1](#14_Chapter06.xhtml#fig6.1).**

The corresponding logistic regression function is given as

![](images/page177-03.png)

In this chapter, we will use the HR dataset to predict attrition (File HR\_Attrition.csv). The dataset description is provided in the next section. Let us install the relevant packages which will be used for data analysis and model building.

![](images/page177-04.png)![](images/page178-01.png)

### 6.3 | Predicting Which Employee Will Leave the Organization Using Logistic Regression

Attrition of employees in an organization is a big challenge for a Human Resource Department. Retaining talent nurtured in the organization not only leads to doing business efficiently (reduced cost and effort) but also creates a workforce which understands the organization better and delivers value added services to their customers and other stakeholders. However, according to the annual compensation trend survey[¹](#14_Chapter06.xhtml#ch6-r-fn1) conducted by KPMG, the attrition for various sectors is shown in **[Figure 6.2](#14_Chapter06.xhtml#fig6.2).**

We will be using data from one such sector and build a logistic regression model to predict attrition. **[Table 6.1](#14_Chapter06.xhtml#tab6.1)** shows the features available in the dataset (HR\_Attrition.csv).

#### 6.3.1 Data Import and Data Preprocessing

In this section, we will discuss the various steps involved in developing a binary logistic regression using R starting from data importation, data pre-processing, model building, model interpretation, and validation.

![](images/page178-02.png)

**TABLE 6.1** | HR attrition data

| Data Code || Description |
| --- | --- |
| Employee Code || Unique identifier which has been randomized |
| --- | --- |
| Department || Department in which employees are working |
| Employee Category || Role of the employee |
| Current Age || Age of the employee at current time stamp (current date – date of birth) |
| Age During DOJ || Age at the time of joining the company (joining Date – date of birth) |
| Zodiac Sign || Zodiac sign based on date of birth |
| Tenure || No. of years for which employee has been working. For currently working employee: 1. Current date – Joining date. For employees who have left the organisation: 2. Last working date – Joining date. |
| Prior Work Exp || Prior work experience before joining this organization |
| Gender || Male, female |
| Marital Status || Marital status of the employee |
| Avg Weighted Performance || Appraisal rating during the tenure of work with 1 being the highest and 5 being the lowest. 0 means have not fallen in appraisal cycle (new employee) |
| PL, CL, SL || Number of personal leave (PL), casual leave (CL), and sick leave (SL) availed in the last 2 years |
| Days Worked in Last Quarter || Number of days worked in last quarter |
| Paternity\_Maternity Leave Last Quarter || Did employee go on maternity or paternity leave in last quarter |
| CTC 2014\_2015 || Employee salary in 2014–2015 |
| CTC 2015\_2016 || Employee salary in 2015–2016 |
| Joining Bonus || Whether joining bonus given or not (Yes or No) |
| Degree Type || Employee’s qualification |
| Highest Education Degree || Highest education of the employee |
| Working in Native Place || Whether the permanent address of the employee was same as present working address |
| Employment Type || Type of employment: probation, contract, on-roll, permanent |
| Confirmation Status || Employee confirmed by the organization (which mostly happens after the training period) |
| RM Age || Age of the reporting manager (RM) of the employee |
| RM Reportee Count || Count of male reportees to the RM |
| RM Reportee Female || Count of female reportees to the RM |
| Last Working Date || Last working day of the employee. In case the employee is active, the date is mentioned as 31-Dec-68 |
| Working Status || Yes – Employee currently in the organization  
No – Employee left the organization |

#### *Importing a Dataset*

The data collected resides in a csv file. The fread() function from data.table can be used to read the dataset from the current working directory. If you are not sure of the current working directory from where the file will be read, you can use the following code:

**1.** getwd() function to get your working directory and

**2.** setwd() function to set your working directory.

The following code can be used to read the data and display summary data as shown in **[Table 6.2](#14_Chapter06.xhtml#tab6.2).**

![](images/page180-01.png)

summary(raw\_dt) will return the summary of the data. The dim(raw\_dt) function can be used to show the dimension of the dataframe.

![](images/page180-02.png)

The dim() function shows that the raw\_dt has 16,501 observations across 33 variables. Moreover, the str() function shows that the LAST\_WORKING\_DATE is being recognized as a factor variable wherein the data type should be Date.

![](images/page180-03.png)

The following code can be used to change the data type for LAST\_WORKING\_DATE

![](images/page180-04.png)

Note that in the format parameter for as.Date, we passed %d-%b-%y.

**1.** %d is to recognize day of the month 01–31

**2.** %b is to recognize abbreviated month, that is, Jan, Feb, etc.

**3.** %y is to recognize year without century 00–99

![](images/page180-05.png)

However, the date format may take many different shapes. To know more about the options which can be passed, the as.Date function, we can get help using ?as.Date or ?strptime.

We can build a model to understand what features of employees influence their WORKING\_STATUS and whether these features can be used to predict the probability of employees working in the organization in future. But all columns are not features. For example, EMPLOYEE\_CODE is an identifier and not a feature. We can also derive new features based on the features available in raw\_dt.

#### *Feature Engineering*

One of the most important aspects of ML model building is to derive features not available as a part of raw data. In the HR\_Attrition data, we can see that there are many features which are derived features. For example, CURRENT\_AGE is derived based on the Current Date - Date of Birth. Similarly, features such as, ZODIAC\_SIGN, AGE\_DURING\_DOJ, TENURE, AVG\_WEIGHTED\_PERFORMANCE, WORKING\_IN\_NATIVE\_PLACE are derived features which may not be directly present as a part of the raw data. All these features are derived from raw data but not shown here due to the sensitivity (personally identifiable information) of some of the features. However, below are some features which can still be derived from the given features list of raw\_dt:

**1.** CHANGE\_IN\_CTC = (CTC\_CURRENT\_YEAR - CTC\_PREVIOUS\_YEAR)/CTC\_PREVIOUS\_YEAR

**2.** AGE\_DIFFERENCE = RM\_AGE - EMPLOYEE\_AGE\_DURING\_DOJ

**3.** EMPLOYEE\_AGED\_OVER\_MANAGER = ifelse((RM\_AGE - EMPLOYEE\_AGE\_DURING\_DOJ) < 0, “Yes”, “No”)

**4.** LEAVES\_PREVIOUS\_YEAR = PL2014+CL2014+SL2014

**5.** LEAVES\_CURRENT\_YEAR = PL2015+CL2015+SL2015

**6.** LEAVE\_OVER\_LAST\_YEAR = LEAVES\_CURRENT\_YEAR/LEAVES\_PREVIOUS\_YEAR

**7.** FEMALE\_TO\_MALE\_REPORTEE = RM\_REPORTEE\_FEMALE/RM\_REPORTEE\_MALE

As discussed in [Chapter 2](#09_Chapter01.xhtml), we will use data.table’s := operator to add/update/delete a column so as to have these features available as a part of the original raw\_dt. We will also remove EMPLOYEE\_CODE from the feature list before performing further analysis.

![](images/page181-01.png)

**Feature engineering** adds new dimensions to the data and helps reduce the variation and outliers’ effect in the raw data.

The seven new features are appended to the raw\_dt. However, we may want to have the WORKING\_STATUS, that is, the outcome variable as the last column. We can use setcolorder() from the data.table for this purpose. In case we want to move any column, say WORKING\_STATUS as the first column, we could have directly used the below code.

![](images/page182-01.png)

In the above code, we could have passed a vector of column names which we would have liked to move to the front. However, we want to move the WORKING\_STATUS as the last column. We will use the below code to reorder and display summary data **([Table 6.3](#14_Chapter06.xhtml#tab6.3)).**

![](images/page182-02.png)

Let us drop EMPLOYEE\_CODE from the raw\_dt

![](images/page182-03.png)

Creating ratios between numeric features is one of the many ways to apply **feature engineering**. One may also create new features by interaction between categorical and numeric feature.

Let us subset raw\_dt so that the new data.table has all the active employees in the organization and employees who left the organization in the years 2015 and 2016. This is needed as

**1.** Features such as PL2015, CL2015, SL2015, PL2014 CL2014, SL2014, which has the count of leaves taken by the employee, is available only for the years 2014 and 2015.

**2.** DAYS\_WORKED\_IN\_LAST\_QUARTER is zero for all the employees who left the organization before 2014.

**3.** PATERNITY\_MATERNITY\_LEAVE\_LAST\_QUARTER is marked as No for all employees before 2014.

The above features may have led to the issue of reporting near-zero variance features (will be discussed later) and would have resulted in dropping the complete feature.

Thus we create a copy of the raw\_dt which includes active employees as well as employees who left the organization in 2015 and 2016 **([Table 6.4](#14_Chapter06.xhtml#tab6.4)).** The filter\_dt is created as a copy so that, raw data remains intact for further manipulation if needed.

![](images/page182-04.png)![](images/page182-05.png)![](images/page183-01.png)

Binning of numeric features, log transformations of numeric features, scaling numeric features, merging of labels occurring in low frequency in categorical feature are some other ways to **reduce variation in the data** before certain machine learning models are applied.

If we write filter\_dt = raw\_dt, then due to R’s copy-on-modify, filter\_dt will still point to the same location in memory as raw\_dt. Therefore, modifying filter\_dt, say, by adding a new column or setting a new key will also modify raw\_dt. To avoid this, we have to explicitly write: filter\_dt = copy(raw\_dt)

#### *Create Feature Set (X) and Outcome Variable (Y)*

We will use the similar approach as in [Chapter 5](#13_Chapter05.xhtml) to create the feature list

![](images/page183-02.png)![](images/page184-01.png)

We can also get numeric and categorical predictors separately using the following code:

![](images/page184-02.png)![](images/page185-01.png)

Compare and note the difference on how the numeric and categorical feature lists were created in [Chapter 4](#09_Chapter01.xhtml).

#### *Analysing the Feature Set (X)*

The features in the model may lead to several issues while building it. We need to identify the issues in features before proceeding with model building. We will discuss some of the basic issues and ways to identify and remove the issues.

Identification and removal of features which shows near zero variance, linear dependency, and correlation with other features are important considerations in **data pre-processing stage.**

##### Zero and Near-Zero Variance (NZV) Features[²](#14_Chapter06.xhtml#ch6-r-fn2)

**1.** The data generating mechanism can create predictors that can only have a single unique value (i.e., a ‘zero-variance predictor’).

**2.** Predictors might have only a handful of unique values that occur with very low frequencies. These may create a problem when data is split using cross validation (CV)/bootstrap.

To identify these types of predictors, the following two metrics can be calculated (Khun, 2007):

**1.** **Frequency ratio:** The frequency of the most prevalent value over the second most frequent value. The frequency ratio will be near one for well-behaved predictors and very large for highly-imbalanced data.

**2.** **Percentage of unique values:** The number of unique values divided by the total number of samples (times 100). This value will approach zero as the granularity of the data increases.

nearZeroVar()² from the caret package can be used to identify features which show NZV. We may consider a predictor to be near-zero variance:

**1.** If the frequency ratio is greater than a pre-specified threshold (default 95/5 = 19).

**2.** And the unique value percentage is less than a threshold (default 10 per cent).

![](images/page185-02.png)

As can be seen from **[Table 6.5](#14_Chapter06.xhtml#tab6.5)**, the features showing near-zero value issues are as follows:

**1.** PATERNITY\_MATERNITY\_LEAVE\_LAST\_QUARTER and JOINING\_BONUS.

**2.** LAST\_WORKING\_DATE also shows the NZV issue. We will anyways drop the date column before model building.

Let us compute the frequency ratio and per cent of unique values for PATERNITY\_MATERNITY\_LEAVE\_LAST\_QUARTER.

**1.** For PATERNITY\_MATERNITY\_LEAVE\_LAST\_QUARTER, the most prevalent value is *N* and it occurred 7,444 times. The second most prevalent value is *Y* and it occurred 101 times. So, the frequency ratio will be 7,444/101 = 73.70. Also, out of a total of 7,545 observations, the unique values in PATERNITY\_MATERNITY\_LEAVE\_LAST\_QUARTER is 2. Thus, the per cent unique (2/7,545)\*100 = 0.02650762. Since the frequency ratio is greater than 19 (default) and per cent unique is less than 10 per cent, PATERNITY\_MATERNITY\_LEAVE\_LAST\_QUARTER is flagged as an NZV feature.

![](images/page186-01.png)

Had we not created filter\_dt **([Table 6.4](#14_Chapter06.xhtml#tab6.4))** by including records for employees with LAST\_ WORKING\_DATE, for the years 2014, 2016, and 2015; variable SL2015 would also have shown as an NZV feature as:

**2.** In raw\_dt, the most prevalent value for SL2015 is 0 days’ leave and it occurred 11,793 times. The second most prevalent value is 60 days’ leave and it occurred 604 times. So, the frequency ratio will be 19.52. Also, out of a total of 16,501 observations, the unique value in SL2015 is 66. Thus, the per cent unique (66/16,501) = 0.0039. Since the frequency ratio is greater than 19 (default), and per cent unique is less than 10 per cent, SL2015 would have been flagged as an NZV feature.

We will drop all the features showing NZV, before model building.

##### Linear Dependency

One of the common issues is linear dependency between features. A set of features is said to be linearly dependent if there is a set of scalars, not all zero, such that the linear combination is a zero vector. In the attrition data, we have three features, that is, ‘RM\_REPORTEES\_COUNT’, ‘RM\_REPORTEE\_MALE’, ‘RM\_REPORTEE\_FEMALE’ which are linearly dependent.

**1.** ‘RM\_REPORTEES\_COUNT’ - (‘RM\_REPORTEE\_MALE’ + ‘RM\_REPORTEE\_FEMALE’) = 0

While trying to estimate the beta coefficients in regression modelling, linearly dependent features result in a singular matrix and thus the beta coefficients of one of the linearly dependent features may not get estimated.

Note that a matrix is called a singular matrix if the determinant of a matrix is zero and thus the inverse of a matrix cannot be computed. Matrix inverse gets used in estimating beta coefficients. The other issue which may arise from the linearly dependent feature is of multi-collinearity. Multi-collinearity is discussed in the next section.

The function findLinearCombos from the caret package uses the QR decomposition of a matrix to enumerate sets of linear combinations.

![](images/page187-01.png)

There are two feature lists which are linearly dependent.

**1.** Feature number 16, 17, and 18 are ‘RM\_REPORTEES\_COUNT’, ‘RM\_REPORTEE\_MALE’ and ‘RM\_REPORTEE\_FEMALE’.

**2.** Feature number 2, 15, and 20 are ‘EMPLOYEE\_AGE\_DURING\_DOJ’, ‘RM\_AGE’ and AGE\_DIFFERENCE:

**3.** Feature number 23 (LEAVE\_PREVIOUS\_YEAR) is sum of CL2014, PL2014, and SL2014.

**4.** Feature number 24 (LEAVE\_CURRENT\_YEAR) is sum of CL2015, PL2015, and SL2015.

We will have to drop one or more of these features before proceeding with model building.

##### Multi-Collinearity

Let us analyze the correlation between variables and drop features which are highly correlated variables. We will build a correlation matrix **([Table 6.6](#14_Chapter06.xhtml#tab6.6))** amongst the numeric variables by using the cor() function. We will plot the correlation matrix for visual inspection and use findCorrelation function to report feature names which are highly correlated at cut-off of 0.70.

![](images/page188-01.png)

The correlation heatmap is shown in **[Figure 6.3](#14_Chapter06.xhtml#fig6.3).** The diagonal line represents correlation of the feature with itself and can be ignored. For other features, the darker shades reflect features which are highly correlated (positive as well as negative). From **[Figure 6.3](#14_Chapter06.xhtml#fig6.3)**, we can see there are features which are highly correlated.

**1.** AGE\_DIFFERENCE is highly correlated with EMPLOYEE\_CURRENT\_AGE, EM-PLOYEE\_AGE\_DURING\_DOJ, and RM\_AGE

**2.** INCREMENT\_FROM\_LAST\_YEAR seems to be highly correlated with AVG\_WEIGHTED\_PERFORMANCE, PL, CL, SL, and DAYS\_WORKED\_IN\_LAST\_QUARTER

**3.** DAYS\_WORKED\_IN\_LAST\_QUARTER is highly correlated with AVG\_WEIGHT-ED\_PERFORMANCE, PL, CL, and SL

**4.** PL, CL, SL are all highly correlated amongst each other.

**5.** CTC\_CURRENT\_YEAR is highly correlated with CTC\_PREVIOUS\_YEAR

![](images/page188-02.png)![](images/page189-01.png)

There are other features in the heatmap which are highly correlated as well. However, when the feature set is large, it becomes difficult to read the correlation matrix or the heatmap to find out the variables which are highly correlated. **caret** package has a function findCor-relation() which takes correlation matrix as an input. At a user-defined cut-off value, this function will print the names of the variables correlated with other variables at the specified cut-off. Refer to [Chapter 5](#13_Chapter05.xhtml) for a detailed explanation on findCorrelation():

![](images/page189-02.png)

Note that the linear dependency and correlation amongst features are not the same. High correlation amongst features does not necessarily mean that the matrix inverse cannot be found.

The features identified in this section will be removed from the predictor variables. Moreover, features such as AVG\_WEIGHTED\_PERFORMANCE’, ‘MARITAL\_STATUS’, ‘CONFIRMATION\_STATUS, ‘GENDER, and ‘TENURE’ were removed, after having built the first model, due to their insignificance in prediction.

Addition or removal of a feature is an iterative process and may take multiple model runs before having the list of features which will be used in the final model.

![](images/page190-01.png)

#### *Create Train and Test Set*

createDataPartition( ) function from the caret package provides the ability to split the dataset randomly into training and validation datasets. The following code can be used for partitioning the data:

![](images/page190-02.png)

#### *Model Building: Using the caret() Package*

In order to build logistic regression model, the caret package has a method **glmStepAIC** which implements the strategy of variable selection and elimination by looking at Akaike Information Criterion (AIC).

AIC estimates the quality of each model, relative to each of the other models for a given set of variables. Thus, AIC provides a means for making a simple model by retaining fewer predictor variables.

AIC does not provide a test of a model in terms of null hypothesis and thus it does not say anything about the absolute quality of a model but only the quality relative to other models.

Formula to compute AIC is

![](images/page191-01.png)

Since −2 \* *LL* is equal to deviance. The above can be rewritten as

![](images/page191-02.png)

where

• Deviance is −2\* log likelihood estimate, which measures the deviation from a perfect model.

• *k* is the penalising factor. Only *k* = 2 gives AIC, *k* = log(*n*) is sometimes referred to as Bayesian Information Criteria (BIC).

• *P* is the number of parameters in the model.

The below code chunk implements the logistic regression model using glmStepAIC() method. This method calls stepAIC() function from the **MASS** package.

![](images/page191-03.png)![](images/page192-01.png)![](images/page193-01.png)![](images/page194-01.png)

A point to note is that the glmStepAIC used backward elimination (default) strategy for feature selection. In case we want to use forward selection or forward selection and backward elimination strategy, we can specify the direction = forward or direction = both.

##### Understanding AIC Steps

The logistic\_model built using glmStepAIC resulted in seven iterations. The first iteration started with an initial AIC value of 3360.8. Let us calculate the initial AIC value using [Eq. \[6.9\]](#14_Chapter06.xhtml#eq6.9). For the calculation, we will make a full model object using **glm** method.

![](images/page194-02.png)![](images/page195-01.png)

As can be seen, the initial AIC value matches the starting AIC value in iteration 1. Iteration 1 continues further, wherein each of the features was dropped from the feature list and the resulting AIC value was noted for the resulting model. In iteration 1, ZODIAC\_SIGN was dropped. The last iteration resulted in the final model with the minimum AIC value.

Refer to [Chapter 5](#13_Chapter05.xhtml) for a detailed explanation on AIC iterations. Let us build a model using forward selection, backward elimination (direction = both) strategy and use that for model diagnostic. We are also using the argument trace = 0 to suppress the iteration results.

![](images/page195-02.png)

Before proceeding with the model diagnostic, let us look at the Variable Inflation Factor (VIF) which will show if there is any issue of multi-collinearity. Looking at the VIF in step\_logistic\_model, we can infer that none of the variables in the model have multi-collinearity (values close to 1).

![](images/page195-03.png)

#### *Model Summary*

The object step\_logistic\_model has the final model. The summary() of this model object shows some of the statistics required to validate the model.

![](images/page195-04.png)![](images/page196-01.png)

Referring to [Eq. \[6.1\]](#14_Chapter06.xhtml#eq6.1) for the functional form, we know that the logistic regression models the probability of *Y* = 1|*X*, that is, the probability of event which is coded as 1 (positive). In a two-class problem, caret codes the first level as the positive class. In this scenario, ‘levels(train\_dt$WORKING\_STATUS)’ shows two levels for WORKING\_STATUS, that is, ‘No’ and ‘Yes’. The first level (No) will be coded as a positive class, that is, the model outputs probability of an employee leaving the organization.

The summary of step\_logistic\_model prints several details. Let us describe each one of them:

**1.** Deviance residual summarizes the deviance calculated for every data point in the training data.

**2.** The model equation can be written as

![](images/page196-02.png)

where Z = −3.53 + 0.71 \* EMPLOYEECATEGORY[Operations] − 0.21 \* EMPLOYEECA TEGORY[Sales] + − + 0.03 \* AGEDIFFERENCE – 0.06 \* LEAVES\_CURRENT\_YEAR –0.09 \* LEAVE\_OVER\_LAST\_YEAR

**3.** Null deviance corresponds to −2 times log likelihood function (−2*LL*[0]). *LL*[0] corresponds to likelihood function with no independent feature, that is, in the absence of any feature, the probability (likelihood) of observing the outcome. In this data (train\_dt), the total observations are 6,037; the positive cases are 1,649 (Y = 1 means No); and negative cases are 4,388 *(Y* = 0 means Yes).

− *P(Y = 1)* = *π (Z) =* 1649 / 6037 = 0.2731 and

− *P(Y =* 0) = 1 − *π (Z) =* 4388 / 6037 = 0.7268.

Using [Eq. (6.5)](#14_Chapter06.xhtml#eq6.5) for likelihood function and substituting the values of *π (Z*) and 1 − *π (Z),*

![](images/page197-01.png)

**4.** Residual deviance corresponds to −2 times log likelihood function (−2*LL)* after adding features. *LL* corresponds to likelihood function with independent feature, that is, in the presence of the features the probability (likelihood) of observing the outcome. In this scenario, including independent features decreased the deviance to 3,304.4. Residual deviance has reduced by 3,775.4 units (7,079.8 − 3,304.4). While performing model diagnostic, we will use null deviance (−2LL[0]) and residual deviance (−2LL) to perform the likelihood ratio test to find the statistical significance of the model.

**5.** Fisher Scoring is a derivative of the Newton Raphson method to numerically solve the Maximum Likelihood Estimation (MLE) function, that is, finding the best *β* coefficients. The Fisher value of 6 signifies that it took six iterations to find the best beta coefficients, that is, for model to converge. There is no other significance of Fisher statistic in model diagnostic.

The sign of the coefficient can be used in model interpretation.

(a) A positive sign before the estimate means that the probability of event (*Y* = 1) increases, that is, the employee leaving the organization as the value of the feature increases.

(b) A negative sign before the estimate means that the probability of event (*Y* = 1) decreases as the value of the feature increases.

Let us read the model summary of step\_logistic\_model and interpret the outcome for features/levels which are significant (*p*\-value < 0.05). With other features being held constant:

**1.** The probability of employees in Operation role (EMPLOYEE\_CATEGORY), leaving the organization is higher compared to the probability of employees leaving the organization who are in Non Sales role (base category).

**2.** It is more likely that employees with an Under Graduate degree (DEGREE\_TYPE) will leave the organization compared to those with a Graduate degree.

**3.** For every unit increase PRIOR\_WORK\_EXP the probability of an employee leaving the organization goes up. This suggests that experienced employees who join the organization come with good exposure and the demand for them in the market is also higher.

**4.** For every unit increase in salary the previous year (CTC\_PREVIOUS\_YEAR), the chance of an employee leaving the organization goes up. The model may not suggest that salary should not be increased for employees but merely reflects that higher salary is paid to an experienced employee and the chances of an experienced employee leaving the organization are more.

**5.** With every unit change in CTC from previous year to current year (CHANGE\_IN\_CTC), the likelihood of an employee leaving the organization goes up. This is related to the previous statement as well.

**6.** For every unit increase in number of days worked in last quarter (DAYS\_WORKED\_IN\_LAST\_QUARTER), the chance of an employee leaving the organization goes up. This may be due to extra work pressure, which impacts the employee’s work-life balance and prompts him to look for a better opportunity outside. On a lighter note, this conforms to the statement, ‘All work and no play makes Jack a dull boy.

**7.** With every unit increase in leave over last year (LEAVE\_OVER\_LAST\_YEAR) and unit increase in leave taken in current year (LEAVES\_CURRENT\_YEAR), the chance of an employee leaving the organization goes down. This exactly ties back to the previous statement and confirms that work-life balance has an important role to play in keeping employees engaged.

**Model selection strategy** helps select features in the final model. Strategies like forward selection, backward elimination or both, works in such a way that with every iteration of model building stage the AIC or deviance reported decreases. The model converges when the AIC or deviance of the model does not reduce with addition or removal of the features.

**8.** With every unit increase in the number of female reportees to a manager (RM\_REPORTEE\_FEMALE), the probability of an employee leaving the organization goes down. It seems as if diversity in the team has some role to play in employee retention.

**9.** With every unit increase in age difference (AGE\_DIFFERENCE) between manager and employee, the likelihood of an employee leaving the organization goes up. It may have something to do with generation gap and seems to conform to the hypothesis that ‘Employees leave their manager and not the organisation.

### 6.4 | Model Diagnostic

It is important to validate the logistic regression model to ensure its validity and goodness of fit before it can be used for practical applications. The following measures are used to validate a logistic regression model (Pradhan and Kumar, 2019):

**1.** **Wald’s test** for checking statistical significance of individual predictor (feature) variables (equivalent to f-test in MLR model).

The ‘step\_logistic\_model’ returned the set of features which are statistically significant at a significant value of *α* = 0.05. Note that some of the levels within a categorical feature are not significant. However, it may not be required to drop the feature as the feature selection was carried out using AIC. The feature helped in reducing the overall AIC value.

**2.** **Likelihood Ratio (LR)** test is used to check the statistical significance of the overall model. LR test is equivalent to performing a *χ2* test where

(a) Chi -square value is the difference between the model[null deviance] and model[residual deviance] (step\_logistic\_model$finalModel$null.deviance-step\_logis-tic\_mo del$ finalMo del$ deviance)

(b) The corresponding degrees of freedom is the difference between *d*f[null]and df[residual] (step\_logistic\_model$finalModel$df.null-step\_logistic\_model$final-Model$df.residual)

LR test can also be used for variable (feature) selection. The LR test using pchisq() function is as follows:

![](images/page198-01.png)

In this scenario, the *χ2* test results in a *p*\-value of zero, which signifies that a model with predictor variables is significantly different from a model without any predictor. Thus, the overall model equation is valid.

**3.** **Pseudo *R*²:** Pseudo *R*² is a measure of goodness of the model. For binary logistic regression, the Pseudo *R*² value can be derived using

![](images/page198-02.png)

This is known as McFadden Pseudo *R*². The McFadden Pseudo *R*² for the model is 0.53:

![](images/page198-03.png)

It is called pseudo *R*² because it does not have the same interpretation of *R*² as in the MLR model.

#### 6.4.1 Prediction on Test Data

We will use the step\_logistic\_model to predict the outcome on the test data. The type parameter of predict() function can return the predicted probability, predicted probability on logit scale, and the predicted class.

**1.** When type = ‘link’ the predict() returns the predicted probability on logit scale, that is, as per [Eq. (6.3)](#14_Chapter06.xhtml#eq6.3).

![](images/page199-01.png)

**2.** When type = ‘response’ or type = ‘prob’ the predict() returns the predicted probability, that is, as per [Eq. (6.1)](#14_Chapter06.xhtml#eq6.1). **[Table 6.7](#14_Chapter06.xhtml#tab6.7)** shows the predicted probability on the test set.

![](images/page199-02.png)

The outcome of a logistic model is class probability value *P*(*Y* = 1). This probability needs to be converted to a class value in order to understand in how many observations the model has been classified correctly and in how many it has not. In order to convert the probability value into a class, a cut-off probability needs to be assumed. By default, the cut-off probability is assumed to be 0.50. All observations with predicted probability greater than 0.50 will be predicted as positive class (No in this case).

Passing type = ‘raw’ in the predict() returns the predicted class at a cut-off of 0.50 (default).

![](images/page199-03.png)

The first six observations of the test\_predicted\_class will be ‘No’. We will discuss techniques that can be used to find the optimal cut-off probability later in the chapter. However, it can be noticed from actual class (i.e., the outcome feature, WORKING\_STATUS) and predicted class (i.e., the outcome using the predict()) that some classifications are correct and some are wrong. To gain better insight, we will calculate some statistics from classification matrix (also known as confusion matrix). The confusion matrix is a metric to measure true and false classifications.

**TABLE 6.7** | Test predicted prob

| No || Yes |
| --- | --- |
| 0.81 || 0.19 |
| --- | --- |
| 0.80 || 0.20 |
| 0.60 || 0.40 |
| 0.91 || 0.09 |
| 0.86 || 0.14 |
| 0.82 || 0.18 |

#### 6.4.2 Creating a Confusion Matrix

Confusion matrix (also known as error matrix or classification table) is a matrix formed by checking the actual values and predicted values of observations in the data for a specific classification cut-off probability. To create confusion matrix, we will use confusionMatrix function from caret. The functions expect:

**1.** The predicted class and the actual class to be passed as the first two parameters.

**2.** Parameter positive, in confusionMatrix(), is optional and will use the first level from actual class, that is (test\_dt$WORKING\_STATUS) as the positive result (No in this case). We can change it to Yes in case we want to interpret the model with Yes as a positive class.

**3.** mode=everything is to report all the statistics (default is ‘sens\_spec’).

![](images/page200-01.png)

Confusion matrix using confusionMatrix() function returns a matrix where the rows represent the predicted classes, while the columns represent the actual classes. **[Table 6.8](#14_Chapter06.xhtml#tab6.8)** shows the confusion matrix on the test set.

![](images/page201-01.png)

Most of the time, the matrix is inverted, that is, rows represent actual class and columns represent predicted class. Many statistics are reported by the confusionMatrix() which we will discuss in the next section. We can note the following:

**1.** Left-top quadrant represents actual status as ‘No’ (positive class) and correctly classified as ‘No. This is called True Positive (TP).

**2.** Left-down quadrant represents actual status as ‘No’ and incorrectly classified as ‘Yes’. This is called False Negative (FN).

**3.** Right-top quadrant represents actual status as ‘Yes’ and incorrectly classified as ‘No’. This is called False Positive (FP).

**4.** Right-down quadrant represents actual status as ‘Yes’ and correctly classified as ‘Yes’. This is called True Negative (TN).

#### 6.4.3 Measuring Model Accuracies

In classification, model performance is often measured using concepts such as sensitivity, specificity, precision, F-score, etc. We will discuss most of the statistics reported by confusionMatrix() in the section below.

#### *Accuracy*

From the classification matrix, we know that out of412 (304+108) cases where an employee left the organization, 304 cases were correctly classified. We also know that out of 1,096 (53+1043) employees still with the organization, 1,043 cases were classified to be active.

Overall model accuracy measures the total correct classifications out of the total number of cases.

![](images/page201-02.png)

The output of confusionMatrix() reports an overall model accuracy of 89%. It also reports a 95% confidence interval around overall model accuracy as (0.88, 0.91).

#### *No Information Rate*

If we look into the HR Attrition test data, the proportion of ‘Yes’ is (1096/1508) \* 100 = 72.7 and proportion of ‘No’ is (412/1508) \* 100 = 27.3. Let us assume that we were given the test data and asked to predict WORKING\_STATUS for each case, without using any model. Assume that, with human intelligence, we predicted or guessed all cases as Yes. So, the accuracy of the model in such a situation turns out to be 72.7% (not bad). This means that without knowing anything about the data, we were reasonably accurate in prediction. This is called No Information Rate (NIR). NIR refers to the accuracy of a model built without any data (features). In many scenarios, we will want the model built using data to have an accuracy more than NIR. We have a model accuracy of 89% but we also want to test if it is significantly greater than NIR.

**1.** *H*[*o*]: The model accuracy is same as NIR.

**2.** *H*[*a*]: Model accuracy is different from NIR.

Corresponding to the above hypothesis, the jj-value reported by confusionMatrix() is 2.2e-16. Since the 2.2e-16 < 0.05, we can statistically say that ‘the model accuracy is better than NIR’, that is, reject the null hypothesis. Note that the above hypothesis test was as good as performing a two-sample proportion test.

#### *Kappa*

From the classification matrix, we know that TP cases are 304 and TN cases are 1,043. However, these observed TP and TN cases could have happened by chance (by virtue of the test sample). How can we be certain that the correct classification is unlikely to have happened by chance? Kappa is an accuracy measure which accounts for correct classification due to chance. The Kappa value is calculated using observed count and expected count as follows:

![](images/page202-01.png)![](images/page202-02.png)

In [Eq. (6.15)](#14_Chapter06.xhtml#eq6.15), the numerator for the expectation count is

**1.** (TP + FP) \* (TP + FN) = row\_sum \* column\_sum for TP cases in classification matrix

**2.** (TN + FN) \* (TN + FP) = row\_sum \* column\_sum for TN cases in classification matrix

The denominator in [Eq. (6.15)](#14_Chapter06.xhtml#eq6.15) is the sum of all the cases in the classification matrix, that is, TP+FP+TN+FN = margin.

![](images/page202-03.png)

Let us calculate the values of [Eqs. (6.14)](#14_Chapter06.xhtml#eq6.14), [(6.15)](#14_Chapter06.xhtml#eq6.15), and [(6.16)](#14_Chapter06.xhtml#eq6.16) using the confusionMatrix() outcome on test data. The range of kappa value is (−1, 1).

![](images/page202-04.png)

**1.** Kappa value > 0 implies that classification is better than chance classification.

**2.** Kappa value < 0 implies that classification is not better than chance classification.

**3.** Kappa value of 1 is perfect classification.

**4.** Kappa value of 0 implies a pure chance classification.

A Kappa value higher than 0.70 implies good classification accuracy and less than 0.40 implies poor classification accuracy. In this case, a Kappa value of 0.72 on the test data implies that the classification accuracy is reasonable.

#### *McNemar’s Test*

McNemar’s Test is a hypothesis test (*χ*²\-test of independence with *df* = 1) which checks if there is a significant difference between the counts in the misclassified cases (FP and FN). In other words, if the test data changes, will the proportion of misclassified cases (error) remain the same or differ.

**1.** *H*[*o*] = The proportion of misclassified cases will remain the same.

**2.** *H*[*a*] = The proportion of misclassified cases will be different.

The test statistic is given by

![](images/page203-01.png)![](images/page203-02.png)

The calculated p-value using chi-square and McNemar’s test is same. However, the confusionMatrix() function reports McNemar test with continuity correction:

![](images/page203-03.png)

The McNemar’s Test P-value reported by confusionMatrix () is 2.083e-5. It implies that the proportion of misclassified cases will be significantly different if the test data changes (Reject *H*[*o*]). This statistical test may become much more relevant in deep learning models where training and testing time is computational-expensive.

McNemar’s Test can also be used to compare two different binary classification models. The objective will be to test: ‘Is the proportion of misclassified cases (error) by the two models same or different on the same instance of test set’.

#### *Sensitivity (Recall or True Positive Rate)*

Sensitivity (also known as recall or true positive rate) is the conditional probability that the predicted class is positive given that the actual class is positive (Kumar, 2017). Sensitivity and recall are the same statistics. Mathematically, sensitivity is given by

![](images/page203-04.png)

The model reported a sensitivity of 0.74. This means that of all the employees who left the organization, the model classified 74% of them correctly.

#### *Specificity (True Negative Rate)*

Specificity is the conditional probability that the predicted class is negative given that the actual class is negative. Mathematically, sensitivity is given by

![](images/page204-01.png)

The model reported a sensitivity of 0.95. This means that of all the employees who are still working in the organization, the model classified 95% of them correctly. The terminologies sensitivity and specificity originated in medical diagnostics (Kumar, 2017; Anon, 2021).

#### *Precision (Positive Predicted Value)*

Precision, also known as Positive Predicted Value (PPV), is the conditional probability that the actual value is positive given that the prediction by the model is positive (Pradhan and Kumar, 2019).

![](images/page204-02.png)

The model reported a precision of 0.85 which means that of all the positive predictions (‘No’) by the model, 85% were correct.

#### *F-Score*

*F*\-score is a measure that combines precision and recall (harmonic mean between precision and recall). Mathematically, F-score is given by

![](images/page204-03.png)

where *β* = 1 for *F*[1] score (weights precision and recall in the same way). Thus

![](images/page204-04.png)

This model reported a *F*[1] score of 0.79, which also suggests that both precision and recall will be reasonably good. *F*[1] score can be used to compare and select models with higher *F*[1] score.

We will also find reference to *F*[2] and *F*[0.5] score.

**1.** *F*[2] is obtained by setting *β* = 2 (weighs recall higher than precision).

**2.** *F*[0.5] is obtained by setting *β* = 0.5 (weighs precision higher than recall).

*F*[2] or *F*[0.5] scores may be desirable in case of applications where we want a model to have a higher recall compared to precision and vice versa.

#### *Other Measures*

There are more statistics reported in the confusion matrix. We will summarize them here:

**1.** **Prevalence:** Proportion of positive cases in the actual data (test\_dt). In this dataset, we have 412/1,508 = 0.2732.

**2.** **Detection rate:** The predicted positives as a proportion of overall cases. From the classification matrix, the value is 304/1,508 = 0.2016.

**3.** **Detection prevalence:** Total predicted positives (TP and FP) as a proportion of overall cases. The value is 357/1,508 = 0.2367. If detection rate and detection prevalence are close to each other, it means the model has misclassified a smaller number of positive cases.

**4.** **Neg Pred Value (Negative Predicted Value):** Conditional probability that the actual value is negative (TN) given that the prediction by the model is negative (TN+FN). From the classification matrix, the value is 1,043/(1,043+106) = 0.9077.

**5.** **Pos Pred Value:** This is same as precision.

**6.** **Balanced accuracy:** ![](images/pageIn_ch6-01.png). The corresponding value is 0.8448.

#### 6.4.4 Receiver Operating Characteristics (ROC) & Area Under ROC Curve

Receiver Operating Characteristic (ROC) curve can be used to understand the overall performance (worth) of a logistic regression model (and, in general, for binary classification models) and for model selection. The term has its origin in electrical engineering, when electrical signals were used to identify enemy objects (such as submarines and aircraft) during World War-II. ROC curve is a plot between sensitivity (true positive rate) in the vertical axis and 1 – specificity (false positive rate) in the horizontal axis (Kumar, 2017).

ROCR package can be used to evaluate the model performance on the train data. The same package can also be used to get the model performance on the test data. The function prediction and performance from ROCR package is used to get the plot of ROC.

**1.** prediction() expects the prediction object, that is, predicted\_prob (calculated earlier on test\_dt using predict()) and true class label, that is, test\_dt$WORKING\_STATUS as parameters. Note that the function goes with the default label ordering of R (‘No’<‘Yes’), that is, it will treat No = 0 (negative class) and Yes = 1 (positive class). However, the confusionMatrix() function from the caret package marked No =1 (positive class). So, in order to get the correct ROC curve, we will use the parameterlabel.ordering = c(‘Yes’,’No’) to treat ‘No’ as the positive class.

Intuitively, the prediction() function calculates predicted class labels and classification matrix using the input parameter (predicted\_prob, true class label) and a set of 100 cut-off values in the range (0.00, 1.00). For every cut-off value, the function calculates below measures (counts) and stores them as list.

**1.** n.pos and n.neg: number of positive and negative samples in the data

**2.** tp,fp, tn,fn: number of true positive, false positive, true negative, and false negative at a specific cut-off

**3.** n.pos.pred and n.neg.pred: number of samples predicted as positive and negative at a specific cut-off

The cut-offs at which calculated measures are same is removed from the list returned by prediction() function.

Let us get the ROC curve and AUC using the ROCR package. First, we used the prediction function to compute various measures. The data type of rocr\_prediction object is a list which contains various measures discussed above.

![](images/page205-01.png)

These measures are used by performance() function of ROCR package to get various plots like ROC, Gain Chart, Lift Chart, custom charts, etc.

**2.** performance() takes input from the prediction object and uses it to compute various statistics and plots like “auc”, “roc plot”, precision recall plot“,”lift chart”, etc.

We can use the performance() function and pass the test\_rocr\_prediction object as a parameter. Since ROC is a plot between true positive rate (tpr) and false positive rate (fpr), the performance function will calculate the statistics. In order for performance to compute tpr and fpr, we will pass them as parameters as well.

![](images/page205-02.png)![](images/page206-01.png)

In **[Figure 6.4](#14_Chapter06.xhtml#fig6.4)**, the diagonal line represents the case of not using a model (no discrimination between positive and negative classes); the area below the diagonal line is equal to 0.5 (it is a right-angle triangle, area of right-angle triangle is 0.5 *ab*, where *a* and *b* are the length of the sides, which is equal to 1 in this case). Sensitivity and/or specificity is likely to change when the cut-off probability is changed. The line above the diagonal line captures how sensitivity and (1 − specificity) change when the cut-off probability is changed. A Model with a higher AUC is preferred and AUC is frequently used for model selection. Since we also want to report AUC, we will again call the performance function and pass AUC as a parameter to report area under the ROC curve. AUC can be interpreted as the probability of correctly classifying a random pair of positive and negative class records.

![](images/page206-02.png)

As a thumb rule, AUC of at least 0.7 is required for practical application of the model. AUC of greater than 0.9 implies an outstanding model. Caution should be used while selecting models based on AUC, especially when the data is imbalanced (i.e., dataset which has less than 10% positives). In case of imbalanced datasets, the AUC may be very high (greater than 0.9). However, either sensitivity or specificity values may be poor.

For this example, the approximate value of AUC is 0.91 which implies that ‘picked at random, an employee who left the organization and one who is currently working in the organization, the model will be correctly able to classify both of them correctly, 91% of the times.

#### 6.4.5 Finding Optimal Classification Cut-off

While using logistic regression model, one of the decisions a data scientist has to make is to choose the right classification cut-off probability. The overall accuracy, sensitivity, and specificity will depend on the chosen cut-off probability. The following two methods are used for selecting the cut-off probability.

**1.** Youden’s Index

**2.** Cost-based approach

#### *Youden’s Index*

Sensitivity and specificity change when we change the cut-off probability. Youden’s Index (Youden, 1950) is a classification cut-off probability for which the following function is maximized (also known as /-statistic):

![](images/page207-01.png)

That is, select the cut-off probability for which (tpr+tnr−1) is maximum. The tpr is true positive rate and tnr is true negative rate.

Note that while trying to find the optimal cut-off, we will have to use the train\_dt and not the test\_dt. We will create train\_rocr\_prediction object using prediction() and then use the measures needed to compute tpr and tnr.

![](images/page207-02.png)

**[Table 6.9](#14_Chapter06.xhtml#tab6.9)** shows the first six observations from the train\_rocr\_prediction\_measures dataframe.

Let us compute tpr and fpr by passing train\_rocr\_prediction parameter to the performance(). **[Table 6.10](#14_Chapter06.xhtml#tab6.10)** shows the first six observations from the train\_rocr\_performance dataframe.

![](images/page207-03.png)![](images/page207-04.png)

**TABLE 6.10** | Train ROCR performance measures

| Fpr || tpr |
| --- | --- |
| 0.0000000 || 0.0000000 |
| --- | --- |
| 0.0000000 || 0.0042450 |
| 0.0002279 || 0.0806549 |
| 0.0006837 || 0.2395391 |
| 0.0015953 || 0.3917526 |
| 0.0018232 || 0.4863554 |

Let us bind train\_rocr\_prediction\_measures and train\_rocr\_performance\_measures using cbind() function. **[Table 6.11](#14_Chapter06.xhtml#tab6.11)** shows the merged dataframe.

![](images/page208-01.png)

Since false positive rate (fpr) = 1 − true negative rate (tnr), we can calculate Youden’s index as tpr-fpr. **[Table 6.12](#14_Chapter06.xhtml#tab6.12)** shows the Youden’s index calculated using the below code snippet.

![](images/page208-02.png)

**[Table 6.13](#14_Chapter06.xhtml#tab6.13)** shows 0.26 as the cut-off which maximizes the Youden’s Index on the train\_dt. Using predict(), we saved the test\_predicted\_prob on the test\_dt earlier. Let us use best\_cutoff on the test\_dt and build a classification matrix.

![](images/page208-03.png)![](images/page208-04.png)![](images/page209-01.png)![](images/page209-02.png)

We can compare the above outcome at a cut-off of 0.26 with the outcome at default cutoff of 0.50 (in [Section 6.4.2](#14_Chapter06.xhtml#sec6.4.2)). We can conclude that the cut-off of 0.26 has improved the sensitivity.

#### *Cost-Based Approach*

In cost-based approach, we assign penalty cost for misclassification of positives and negatives. Assume that the cost of a false positive rate (FPR) is C1 and the cost of false negative rate (FNR) is C2. Then, the penalty is defined as

![](images/page209-03.png)

The optimal cut-off probability is the one which minimizes the total penalty. Let us build a cost matrix for the HR Attrition problem. Here, the primary objective for HR is to have a model which correctly classifies employees who are likely to leave the organization even if the model misclassifies some of the cases where an employee is still working.

**Fine-tuning the cut-off probability** is an important consideration while deploying the model outcome for decision making. Techniques such as Youden’s Index, Cost of mis-classification are used to fine-tune the cut-off probability of a binary logistic regression model.

![](images/page210-01.png)![](images/page210-02.png)

With the above objective, we can formulate a cost matrix where penalty for misclassi-fying No as Yes is twice as costly compared to misclassifying Yes as No.

![](images/page210-03.png)

Let us use the above cost matrix and optimal\_cutoff\_df to calculate the penalty using the [Eq. (6.23)](#14_Chapter06.xhtml#eq6.23). **[Table 6.14](#14_Chapter06.xhtml#tab6.14)** shows the resultant table with misclassification cost column.

![](images/page210-04.png)

We found out that the best cut-off which will minimize the penalty, on the train\_dt, is 0.16 **([Table 6.15](#14_Chapter06.xhtml#tab6.15)).** Note that the cut-off based on Youden’s Index was found to be 0.26 **([Table 6.13](#14_Chapter06.xhtml#tab6.13)).**

Using predict(), we saved the test\_predicted\_prob on the test\_dt earlier. Let us use best\_cutoff on the test\_dt and build a classification matrix.

![](images/page210-05.png)![](images/page211-01.png)

We can compare the above confusion matrix (at cut-off of 0.16) with the confusion matrix (at Youden’s Index cut-off of 0.26 in [Section 6.4.5](#14_Chapter06.xhtml#sec6.4.5)). We can conclude that a cut-off of 0.16 has improved the sensitivity compared to the sensitivity at a cut-off of 0.26.

### 6.5 | Gain Chart and Lift Chart

Gain chart and lift chart (Kumar, 2017) are two measures used to measure the benefits of using the logistic regression model (in general analytical model) and are used in business contexts such as target marketing. In target marketing or marketing campaigns, customer responses to campaigns are usually very low (in many cases, customers who respond to marketing campaigns are less than 1%). Another example of such low response is advertisement on the internet (such as Google Adwords and mobile advertisements). The organization will incur a cost for each customer contact and hence would like to minimize the cost of the marketing campaign while at the same time hoping to achieve a desired response level from customers. The gain and lift charts are obtained using the following steps:

**1.** Predict the probability of positive response (*Y* = 1) using LR model and arrange the observations in the decreasing order of predicted probability \[i.e., *P*(*Y* = 1)\].

**2.** Divide datasets into deciles. Calculate the number of positives (*Y* = 1) in each decile and the cumulative number of positives up to a decile.

**3.** Gain is the ratio between cumulative number of the positive observations up to a decile to total number of positive observations in the data. Gain chart is a chart drawn between gain on vertical axis and decile on the horizontal axis.

![](images/page212-01.png)

Let us apply the gain chart on the HR attrition data. From the test\_dt, we know that there are 27% positive cases, that is, No (*Y* = 1). The total number of cases in the test\_dt is 1,508. If we use a random model to pick 10% of the cases from 1,508 cases, we will have approximately 41 employees who will be with a WORKING\_STATUS = No, that is, positive cases. We can say that the rate of positive prediction for the random model is 27%. Let us see how much gain the LR model gives over the random model.

![](images/page212-02.png)

At the level where the random model will pick 27% rate of positive prediction *(Y* = ‘No’), the step\_logisitic\_model would give approximately 79% as the rate of positive prediction **([Table 6.16](#14_Chapter06.xhtml#tab6.16)). [Figure 6.5](#14_Chapter06.xhtml#fig6.5)** shows the gain chart plotted using the gain object returned by the performance().

![](images/page212-03.png)

**4.** Lift is the ratio of number of positive observations up to decile *i* using the LR model to the expected number of positives up to that decile *i* based on a random model (not using a model). Lift chart is the chart between lift on the vertical axis and the corresponding decile on the horizontal axis.

![](images/page212-04.png)![](images/page212-05.png)![](images/page213-01.png)

Let us use the lift on the test\_dt.

![](images/page214-01.png)

At the level where the random model will pick 27% rate of positive prediction *(Y* = ‘No’), the step\_logisitic\_model would produce 2.96 times the random model, that is, approximately 79% will be the rate of positive **([Table 6.17](#14_Chapter06.xhtml#tab6.17)). [Figure 6.6](#14_Chapter06.xhtml#fig6.6)** shows the lift chart plotted using the lift object returned by the performance ().

![](images/page214-02.png)![](images/page215-01.png)![](images/page216-01.png)![](images/page216-02.png)

With all the analyses performed on the HR Attrition data, we can come to the conclusion that the logistic regression model will be useful for HR to gain several insights:

**1.** The model may be used to understand the reasons for employees leaving the organization. Decisive action can be taken by HR to retain employees critical to the business.

**2.** The model may be used for predicting employees’ behaviour (WORKING\_STATUS) over a certain time period. The prediction can also lead to building a back-up strategy for employees critical to the business.

**3.** At the organizational level, gain chart and lift chart can be used to understand the employees’ behaviour across various departments. Policy level changes for various departments may be carried out to retain employees (e.g., employees in Sales role to get leaves every quarter, etc.).

Measures like **Gain and lift of the model** is yet another powerful way to understand the efficacy of the model. It helps understand the incremental benefit the model may give in decision making compared to taking a decision without the use of any model.

Binary logistic regression is one of the useful techniques for dealing with classification problems. In the next section, we will discuss Decision Trees, another popular technique to deal with problems of the same type.

### 6.6 | Decision Tree Learning

Decision Tree Learning or Decision Trees is a collection of divide-conquer problem-solving strategies that use a tree-like structure (inverted tree in which the root is at the top) to predict the value of an outcome variable (Kumar, 2017). The tree starts with the root node consisting of the complete data and thereafter uses intelligent strategies to split the nodes (parent node) into multiple branches (thus creating children nodes). The original data is divided into homogeneous subsets. This is done in order to create more homogenous groups at the children nodes. It is one of the most powerful predictive analytics techniques used for generating business rules. Classification and Regression Tree (CART) is a common terminology used for a Classification Tree (used when the dependent variable is discrete) and a Regression Tree (used when the dependent variable is continuous). Classification Tree uses various impurity measures such as the Gini Impurity Index and Entropy to split the nodes in case of classification problems (Kumar, 2017). Regression Tree, on the other hand, splits the node that minimizes the Sum of Squared Errors (SSE). The following steps are used to generate a classification and a regression trees,

**1.** Start with the complete training data in the root node.

**2.** Decide on the measure of impurity, that is, either Gini impurity index or Entropy. Search for a predictor variable that minimizes the impurity when the parent node is split into children nodes. This happens when the original data is divided into two subsets using a predictor variable such that it results in the maximum reduction in the impurity in the case of discrete dependent variable or maximum reduction in SSE in the case of a continuous dependent variable.

**3.** Repeat Step 2 for each subset of the data (for each internal node) using the independent variables until:

(a) All the dependent variables are exhausted.

(b) The stopping criteria are met. A few stopping criteria used are the number of levels of tree from the root node, the minimum number of observations in parent/child node (e.g., 10% of the training data), and the minimum reduction in impurity index.

**4.** Generate business rules (prediction rules) for the leaf (terminal) nodes of the tree. The predicted class is the majority class in the leaf node.

We can build a decision tree model using caret. Through train(), caret provides method = rpart which internally uses rpart() from rpart package. rpart stands for Recursive PARTitioning which is an implementation of CART.

**1.** If the outcome variable (*Y*) is discrete, the rpart() identifies it as a classification problem by internally setting (method = “class”)

**2.** If the outcome feature is numeric, rpart() identifies it as regression problem by internally setting (method = “anova”)

There are various parameters which, when fine-tuned, may lead to a decision tree model with different business rules. In other words, fine-tuning the parameters may lead to a decision tree model which is much more generalizable on the test\_dt. Some of the parameters available through rpart are shown in **[Table 6.18](#14_Chapter06.xhtml#tab6.18).**

rpart continues recursive splitting of the node unless minsplit or minbucket is violated or if the split does not decrease the cost of a tree being evaluated by complexity parameter, cp. The cp (defined in **[Table 6.18](#14_Chapter06.xhtml#tab6.18))** can be a value between (0, ∞). So, we call cp as a fine-tuning parameter (or a hyper-parameter) whose best value for a given train\_dt needs to be figured out from a range of values. In order to find the best value, we will have to create cross-validation sets on which different cp values will be tested and the value which results in minimizing the error (cost) the most will be taken up for model building. This parameter can be fine-tuned with method rpart in caret. Actually, we can also think of minsplit and minbucket as fine-tuning parameters but caret does not give a provision of fine-tuning them unless a custom code is written.

![](images/page217-01.png)![](images/page218-01.png)

As a part of rpart(), there is a set of four more parameters which helps the technique deal with missing value problems. Thus, decision trees may also be used as a technique for performing data imputation. These parameters are shown in **[Table 6.19](#14_Chapter06.xhtml#tab6.19).**

Thus, rpart is more robust in dealing with data, with missing value problem, compared to many other techniques (which choose to ignore the problem). The features with missing observation are classified in a node using surrogate variables.[³](#14_Chapter06.xhtml#ch6-r-fn3) If there is no missing value problem in the data, it will be useful to set the maxsurrogate=0 (saves on the computation time).

![](images/page218-02.png)

Let us understand how the above code line will work. The grid\_params defines a range of cp parameter which needs to be searched. In the control\_params, we define the training environment to be used when model training starts. We have specified the use of 5-cross-validation (5-CV) strategy to fine-tune the complexity parameter cp defined in grid\_params. When the train() is called for model building, control\_params will define a space in which grid\_params (cp in this case) will be fine-tuned.

**[Figure 6.7](#14_Chapter06.xhtml#fig6.7)** depicts a 5-CV strategy. Let us develop an intuition behind it:

**1.** A 5-CV set will divide the train\_dt into five subsets such that each of the subsets will have approximately an equal number of observations. In **[Figure 6.7](#14_Chapter06.xhtml#fig6.7)**, columns ‘Set\_1’, ‘Set\_2’, ‘Set\_3’, ‘Set\_4’, and ‘Set\_5’ represent the five subsets created.

![](images/page218-03.png)

**2.** A value of cp (Say cp = 0.001) from the grid\_params will be picked up.

(a) **Iteration 1:** A decision tree model (say Model\_1) will be developed using (Set\_2 to Set\_5), and its performance will be evaluated on the hold out sample (Set\_1).

(b) **Iteration 2:** A decision tree model (say Model\_2) will be developed using (Set\_1 and Set\_3 to Set\_5), and its performance will be evaluated on the hold out sample (Set\_2).

(c) **Iteration 3:** A decision tree model (say Model\_3) will be developed using (Set\_1 to Set\_2 and Set\_4 to Set\_5), and its performance will be evaluated on the hold out sample (Set\_3).

(d) **Iteration 4:** A decision tree model (say Model\_4) will be developed using (Set\_1 to Set\_3 and Set\_5), and its performance will be evaluated on the hold out sample (Set\_4).

(e) **Iteration 5:** A decision tree model (say Model\_5) will be developed using (Set\_1 to Set\_4), and its performance will be evaluated on the hold out sample (Set\_5).

**3.** Calculate and save the average performance across the five hold out samples. We will define the metric (say Accuracy), based on which the performance of the model will be reported (in train()).

**4.** Repeat Step 2 for every grid\_params value, that is, cp in (0.001 to 0.02).

**5.** Find the grid\_params value which reported the best performance on the hold out sample.

**6.** Use the best parameter value (cp value) to build a decision tree model using the train\_dt.

Note that when we define *k*\-CV set, a total of *k* + 1 model is built. *k* models are built for finding the best parameter combination and (*k* + 1)^(th) model is the final model, which is built using the best parameter values of the *k* models. Generally, the value of *k* is set as 5 or 10 (empirically, these values have shown to result in test error which does not suffer from bias or variance). As *k* gets larger, the difference between training set and cross-validation subsets gets smaller. This is done in order to maintain a subset which is a statistical representative of the training data.

We are now ready to develop a decision tree model. Let us define the train() function to build a decision tree model.

![](images/page219-01.png)

Note that set.seed() is being used prior to train(). This is to ensure that the same cross-validation sets (resamples) are used between calls to train(). However, if parallel processing is involved (not used here), setting the seed prior to train() may not guarantee that the same resamples will be used. We have a seeds parameter in trainControl() which should be set while creating models inside resampling (with parallel processing). We will discuss this option in later chapters.

The params is an optional parameter which has the following default for classification problems:

**1.** Prior is the prior probability of the outcome variable. This gets estimated from the data.

**2.** Loss is the matrix through which we can penalize FPR and FNR, in order to maximize the sensitivity or specificity. Internally, the loss matrix alters the priors which will affect the choice of variable to split the dataset at each node, giving more weight where appropriate (Williams, 2010).

**3.** Split by default is set to gini. We can set information if the criterion for impurity measure is entropy.

Moreover, minsplit and minbucket are the parameters which are applicable when method=rpart (discussed above). trControl and tuneGrid are parameters for train() to which we have passed the objects created from trainControl() and expand.grid(). We can also fine-tune the parameters by using tuneLength parameter of train() (will be discussed in [Chapter 7](#15_Chapter07.xhtml)).

Let us print the decision\_tree\_model.

![](images/page220-01.png)![](images/page221-01.png)

The above output shows the high-level statistics on the input features, the sampling strategy applied, etc. However, the important information is the various cp values which were tried. The final value of cp used was 0.019 as this value resulted in best kappa on the cross-validation set. We will plot the business rules using rpart.plot().

![](images/page221-02.png)

**[Figure 6.8](#14_Chapter06.xhtml#fig6.8)** is a visual representation of the business rules of the decision\_tree\_model. The rules are generated for the terminal (leaf) nodes. Let us understand how to read the node values:

**1.** The first node (node number 1), that is, the starting node has a label of ‘Yes’. This means the maximum number of observations were of type ‘Yes’. The percentage of ‘Yes’ was 73% (‘No’ was 27%). Since this is the starting node, it contains all the observations, that is, 100% of the data was there in this node.

**2.** The first terminal node (labelled 4) is labelled as ‘No’. This means the maximum number of observations were of type ‘No’. The percentage of ‘No’ was 98% (‘Yes’ was 2%). This node contains 18% of the overall observations.

We can get the business rules in text format by print(decision\_tree\_model$-finalModel).

![](images/page221-03.png)![](images/page222-01.png)

Asterisk-marked nodes are the leaf nodes. rpart.plot() used these rules for visualization in **[Figure 6.8](#14_Chapter06.xhtml#fig6.8).** The benefits of Decision Trees are as follows:

**1.** Rules generated are simple and interpretable. Trees can be visualized.

**2.** Works well with both numerical and categorical data. Does not require data to be normalized, or the creation of dummy variables.

**3.** Rules can help create business strategies.

#### 6.6.1 Creating a Confusion Matrix

Let us build a classification (Confusion) matrix to understand the decision tree model. To create confusion matrix, we will use confusion Matrix function from caret. The function expects:

**1.** The predicted class and the actual class to be passed as the first two parameters.

**2.** The parameter positive is optional and it will use the first level from actual class, that is, (test\_dt$WORKING\_STATUS) as the positive result (No in this case). We can change it to Yes in case we want to interpret the model with Yes as a positive result.

**3.** mode=everything is to report all the statistics (default is ‘sens\_spec’).

![](images/page222-02.png)![](images/page223-01.png)

#### 6.6.2 Receiver Operating Characteristic (ROC) and Area Under ROC (AUC) Curve

We had a detailed overview of implementation of ROC and AUC in logistic regression. Let us report the ROC and AUC for decision\_tree\_model.

Let us get the ROC curve and AUC using the ROCR package. First, we used the prediction function to compute various measures. The data type of rocr\_prediction object is a list which contains various measures discussed in the section.

![](images/page223-02.png)

These measures are used by performance() function of ROCR package to get various plots like ROC, Gain Chart, Lift Chart, custom charts, etc.

performance() takes input from the prediction object and uses them to compute various statistics and plots like “auc”, “roc plot”, “precision recall plot” “lift chart”, etc.

Let us use the performance() function and pass the test\_rocr\_prediction object as a parameter. Since ROC is a plot between tpr and fpr, the performance function will calculate the statistics. In order for performance to compute tpr and fpr, we will pass them as parameters as well.

![](images/page223-03.png)

**[Figure 6.9](#14_Chapter06.xhtml#fig6.9)** shows the ROC curve for decision tree model. Sensitivity and/or specificity is likely to change when the cut-off probability is changed. The line above the diagonal line captures how sensitivity and (1 − specificity) change when the cut-off probability is changed. A model with a higher AUC is preferred and is frequently used for model selection. The AUC for the decision\_tree\_model is:

**Cross-validation strategy** helps fine-tune the hyper-parameters of advanced machine learning models. This strategy may become computationally expensive if the number of hyper-parameters and the grid space defined to fine-tune the hyper-parameter is very large.

![](images/page224-01.png)

**Multi-model strategy** may help in reducing the feature space and thus the complexity of the model without any major change in the performance statistics of the final model.

![](images/page224-02.png)

For this example, the AUC is 0.88, which implies that ‘given, at random, an employee who left the organization and one who is currently working in the organization, the model will be correctly able to classify them 88% of the times’.

### 6.7 | Model Selection

One interesting point to note is that of the 17 features passed to the rpart() for model training, the final decision\_tree\_model has only four features. The features are as follows:

**1.** DAYS\_WORKED\_IN\_LAST\_QUARTER

**2.** LEAVES\_CURRENT\_YEAR

**3.** EMPLOYMENT\_TYPE

**4.** LEAVE\_OVER\_LAST\_YEAR

A decision\_tree\_model with these four features helped report a reasonable F1 score, model accuracy, and all the other performance statistics. Of the same 17 features passed to the glmStepAIC for model training, the final step\_logisitic\_regression retained ten features (refer [Section 6.3](#14_Chapter06.xhtml#sec6.3)):

**1.** EMPLOYEE\_CATEGORY

**2.** PRIOR\_WORK\_EXP

**3.** DAYS\_WORKED\_IN\_LAST\_QUARTER

**4.** CTC\_PREVIOUS\_YEAR

**5.** DEGREE\_TYPE

**6.** RM\_REPORTEE\_FEMALE

**7.** CHANGE\_IN\_CTC

**8.** AGE\_DIFFERENCE

**9.** LEAVE\_OVER\_LAST\_YEAR

**10.** LEAVES\_CURRENT\_YEAR

The three features used by the decision tree model are a part of the final logistic regression feature list. Let us compare the F1 statistics and AUC for step\_logistic\_model and decision\_ tree\_model:

**1.** step\_logisitic\_model reported an F1 score of 0.7906 and AUC of 0. 9091 (without optimal cut-off).

**2.** decision\_tree\_model reported an F1 score of 0.8548 and AUC of 0.8898.

Now, which model should we select? We know ROC is built for different levels of threshold (cut-off values). This means the ROC curve inherently has many different F1 score values.

**1.** F1 score will be high when both precision and recall is high at a threshold.

**2.** Wherein AUC for ROC curve averages over all the threshold.

Thus when there is class imbalance in the data, which is the case in HR attrition data as well, it may be useful to select a model which has a better F1 score. Thus, based on F1 score and model simplicity perspective, it seems the decision\_tree\_model is better than the step\_logisitic\_model.

Note that, model selection by considering model simplicity as well as using F1 score may not be the only criteria for selecting the final model. There may be various other business constraints and context which will finally decide which model is to be deployed.

Note that to highlight the multi-model approach, as an exercise, we also rebuilt the step\_logisitic\_regression with the features retained by the decision\_tree\_model. On the test\_dt, the F1 score and AUC for the rebuilt step\_logistic\_regression model were 0.8150 and 0.8810, respectively. It is interesting to note how the feature list of one model was used to simplify an existing model without any major change in the performance statistics. It is left to the reader to rebuild the logistic regression model and verify the results.

### Summary

**1.** In classification problem, the dependent variable *Y* takes finite discrete values. Logistic regression is one of the most popular techniques used for solving classification problems.

**2.** Logistic regression provides the probability of occurrence of the event; final class is usually predicted using a classification cut-off probability.

**3.** Decision trees generate rules that can be interpreted and businesses can create strategies around it.

**4.** The accuracy of an LR model is measured using metrics such as sensitivity, specificity, F-score, precision, and area under the ROC curve. Final model selection may be carried out using any of these metrics.

**5.** The optimal classification cut-off probability is usually calculated using Youden’s Index or cost-based approach.

**6.** Gain and Lift charts are two techniques used to target the positive class while solving classification problems with imbalanced datasets.

### Exercises

#### Answer Questions 1 to 10 using the *SAheart* Dataset.

The dataset SAheart.data is taken from the following link: [http://www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data](http://www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data)

The dataset SAheartrateData.txt contains records of males in a heart-disease high-risk region of the Western Cape, South Africa. There are roughly two controls per case of CHD. Many of the CHD-positive men have undergone blood pressure reduction treatment and other programs to reduce their risk factors after their CHD event. In some cases, the measurements were made after these treatments. These data are taken from a larger dataset, described in Rousseauw et al. (1983), *South African Medical /ournal.* It is a tab-separated file (.csv) and contains the following columns:

• *sbp –* Systolic blood pressure

• *tobacco –* Cumulative tobacco (kg)

• *ldl –* Low-density lipoprotein cholesterol

• *adiposity*

• *famhist –* Family history of heart disease (present, absent)

• *typea –* type-A behaviour

• *obesity*

• *alcohol –* Current alcohol consumption

• *age –* Age at onset

• *chd –* Response, coronary heart disease

**1.** Build a logistic regression model to predict the probability of getting *chd* (coronary heart disease), that is, *P*(*chd* = 1). Use all other columns except *chd* as features to build the model.

**2.** Find out which features are statistically significant in the logistic regression model built in Question 1. Build a new logistic regression model using only the significant features.

**3.** From the logistic regression model parameters, determine which parameters affect the probability of *chd* positively and negatively.

**4.** Calculate Youden’s index for all possible cut-off probabilities ranging from 0.0 to 1.0 with an interval of 0.01. Find the optimal cut-off where Youden’s index is maximum.

**5.** Build a confusion matrix based on the cut-off probability found in Question 4 and report the precision and recall of the model for *chd* cases (i.e., *chd* = 1).

**6.** Find optimal cut-off probability using cost-based approach using the cost of FPs and FNs as defined below.

• Cost of predicting “chd” as “No chd” (FNs) cases is five times more than predicting “No chd” as “chd” (FPs).

• Then find the precision and recall of the model for *chd* = 1.

**7.** Build a decision tree classifier model to predict the probability of *chd* = 1 using Gini index and max depth as 4.

**8.** Compare the decision tree classifier and logistic regression model performance. Explain which accuracy score can be used to find out which model is better in classifying *chd* from *no chd* cases.

**9.** Plot the decision tree and find out the most important splitting criteria at the top node. Explain how the Gini index is derived at the top node of the decision tree classifier.

**10.** Find the optimal *depth* for decision tree classifier if Gini index is used as splitting criteria. Search possible depths ranging from 3 to 10 and use ROC and AUC as scoring to find the optimal *depth.*

#### Answer Questions 11 to 15 using the *HR* Dataset.

The dataset *hrdata.csv* contains samples of candidates that were part of a recruitment process of a particular client of a recruitment firm. The firm supports several information technology (IT) companies in India with their talent acquisition. One of the challenges they face is about 30% of the candidates who accept the jobs offer but do not join the company. This leads to huge loss of revenue and time as the companies initiate the recruitment process again to fill the workforce demand. The firm wants to find out if a model can be built to predict the likelihood of a candidate joining the company. If the likelihood is high, then the company can go ahead and offer the jobs to the candidates.

The dataset contains several attributes about candidates along with a column (or variable) that indicates if the candidate would finally join the company or not. Here is the description of candidate’s attributes:

• *Candidate –* Reference number; it is a unique number to identify the candidate

• *DO/ extended –* Binary variable identifying whether candidate asked for date of joining extension (Yes/No)

• *Duration to accept the offer –* Number of days taken by the candidate to accept the offer (Scale variable)

• *Notice period –* Notice period to be served in the parting company before candidate can join this company (Scale variable)

• *Offered band –* Band offered to the candidate based on experience, performance in interview rounds (C0/C1/C2/C3/C4/C5/C6)

• *Percentage hike expected –* Percentage hike expected by the candidate (Scale variable)

• *Percentage hike offered –* Percentage hike offered by the company (Scale variable)

• *Joining bonus –* Binary variable indicating if joining bonus was given or not (Yes/no)

• *Gender –* Gender of the candidate (Male/Female)

• *Candidate source –* Source from which resume of the candidate was obtained (Employee referral/Agency/ Direct)

• *REX* (in Yrs.) – Relevant years of experience of the candidate for the position offered (Scale variable)

• *LOB –* Line of business for which offer was rolled out (Categorical variable)

• *Date of Birth –* Date of birth of the candidate

• *Joining location –* Company location for which the offer was rolled out for the candidate to join (Categorical variable)

• *Candidate relocation status –* Binary variable indicating whether the candidate has to relocate from one city to another city for joining (Yes/No)

• *HR Status –* Final joining status of the candidate (Joined/Not Joined)

**11.** Build a logistic regression model to predict the probability of a candidate joining the company. Assume “Not Joined” as positive cases and “Joined” as negative cases.

**12.** Find the significant features from the LR model and build another logistic regression model with only the significant features.

**13.** Assume cost of predicting ‘Not Joining’ as ‘Joining’ (FPs) cases is three times more than predicting ‘Joining’ as ‘Not Joining’ (FNs). Find optimal cut-off probability to determine if a candidate will join or not.

**14.** Build a confusion matrix based on the cut-off probability found in Question 13 and report the precision and recall of the model for joining cases.

**15.** HR wants to understand the key parameters effecting the joining of candidates. So, build a decision tree with optimal parameters and provide some rules to HR for building strategies to ensure that candidates offered job will most likely join the company in future.

### Bibliography

**1.** A Janne (2009), *“Determinants of the Volatility Smile: A Study on the German Individuals Stock Options”*, Graduate School of Finance and Financial Accounting, University of Vaasa, Web address: [https://www.docsity.com/en/determinants-of-volatility-smile-study-guide-470-800/6716864](https://www.docsity.com/en/determinants-of-volatility-smile-study-guide-470-800/6716864)/, accessed on 10 May 2021.

**2.** Anon (2018), *“KPMG in India’s Annual Compensation Trends Survey 2018–19”*, Web address: [https://assets.kpmg/content/dam/kpmg/in/pdf/2018/04/KPMG-India-Annual-Compensation-Trends-Survey.pdf](https://assets.kpmg/content/dam/kpmg/in/pdf/2018/04/KPMG-India-Annual-Compensation-Trends-Survey.pdf), accessed on 29 January 2021.

**3.** Anon (2020), *“Model Training and Tuning”*, Web address: [http://topepo.github.io/caret/model-training-and-tuning.html](http://topepo.github.io/caret/model-training-and-tuning.html), accessed on 29 January 2021.

**4.** Anon (2020), *“Zero and near Zero variance predictor”*, Web address: [http://topepo.github.io/caret/pre-processing.html#zero--and-near-zero-variance-predictors](http://topepo.github.io/caret/pre-processing.html#zero--and-near-zero-variance-predictors), accessed on 29 January 2021.

**5.** Anon (2021), *“Sensitivity, Specificity and Precision”*, National Institute of Industrial Engineering, Mumbai, Web address: [https://www.coursehero.com/file/p7md6938/2494-exp-1-e-Male-Single-1-PY-102-1-1102-3580-exp-1-e-Status-Marital-Other-1-PY](https://www.coursehero.com/file/p7md6938/2494-exp-1-e-Male-Single-1-PY-102-1-1102-3580-exp-1-e-Status-Marital-Other-1-PY)/, accessed on 10 May 2021.

**6.** Atkinson B (2021), “rpart.control”, Web address: [https://www.rdocumentation.org/packages/rpart/versions/4.1-15/topics/rpart.control](https://www.rdocumentation.org/packages/rpart/versions/4.1-15/topics/rpart.control), accessed on 10 May 2021.

**7.** Khun M (2007), “Data Sets and Miscellaneous Functions in Caret Package”, Available at [http://ftp.uni-bayreuth.de/math/statlib/R/CRAN/doc/vignettes/caret/caretMisc.pdf](http://ftp.uni-bayreuth.de/math/statlib/R/CRAN/doc/vignettes/caret/caretMisc.pdf), accessed on 24 July 2021.

**8.** Kumar U D (2017), *“Business Analytics – The Science of Data-Driven Decision Making”*, Wiley, New Delhi.

**9.** Pradhan M and Kumar U D (2019), *“Machine Learning Using Python”*, Wiley, New Delhi.

**10.** Rossouw J E, Du Plessis J P, Benade A J, Jordaan P C, Kotze J P, Jooste P L and Ferreira J J (1983), “Coronory Risk Factor Screening in Three Rural Communities – The CORIS Baseline Study, *South African Medical Journal*, 64(12), 430–436.

**11.** Sing T, Sander O, Beerenwinkel N, Lengaur T, Unterthiner T and Ernst F M (2020), *“Package ROCR”*, Web address: [https://cran.r-project.org/web/packages/ROCR/ROCR.pdf](https://cran.r-project.org/web/packages/ROCR/ROCR.pdf), accessed on 29 January 2021.

**12.** Theneau T M and Atkinson E J (2019), *“An Introduction to Recursive Partitioning Using the RPART Routines”*, Web address: [https://cran.r-project.org/web/packages/rpart/vignettes/longintro.pdf](https://cran.r-project.org/web/packages/rpart/vignettes/longintro.pdf), accessed on 29 January 2021.

**13.** Williams G (2010), *“Data Mining”*, available at [http://datamining.togaware.com/survivor/Loss\_Matrix.html](http://datamining.togaware.com/survivor/Loss_Matrix.html), accessed on 10 May 2021.

**14.** Youden W J (1950), “Index for Rating Diagnostic Tests”, *Cancer*, 3, 32–32.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#14_Chapter06.xhtml#ch6-fn1)[https://assets.kpmg/content/dam/kpmg/in/pdf/2018/04/KPMG-India-Annual-Compensation-Trends-Survey.pdf](https://assets.kpmg/content/dam/kpmg/in/pdf/2018/04/KPMG-India-Annual-Compensation-Trends-Survey.pdf)

[²](#14_Chapter06.xhtml#ch6-fn2)[http://topepo.github.io/caret/pre-processing.html#zero--and-near-zero-variance-predictors](http://topepo.github.io/caret/pre-processing.html#zero--and-near-zero-variance-predictors)

[³](#14_Chapter06.xhtml#ch6-fn3)[https://cran.r-project.org/web/packages/rpart/vignettes/longintro.pdf](https://cran.r-project.org/web/packages/rpart/vignettes/longintro.pdf)

 

 
| 

## Advanced Machine Learning

 || 

## 7

 |
| --- | --- |

*Everything we hear is an opinion. Not the fact. Everything we see is a perspective. Not the truth.*

**—Marcus Aurelius**

LEARNING OBJECTIVES

After reading this chapter, you would be able to:

• Understand foundations of machine learning algorithms.

• Learn the difference between supervised and unsuper-vised learning algorithms.

• Understand and develop Gradient Descent optimization algorithm.

• Understand the problems of underfitting and overfit-ting, and use of regularization to control overfitting.

• Understand hyper-parameters and how to search for optimal hyper-parameters

• Apply machine learning algorithms available through the caret package (glmnet) to regression and classification problems.

• Learn features selection using machine learning models.

### 7.1 | Overview

Machine Learning algorithms are a subset of Artificial Intelligence (AI) that imitates the human learning process. Humans learn through multiple experiences to perform a task. Similarly, machine learning algorithms learn using additional data and develop multiple models (usually using multiple datasets), with each model analogous to an experience. For example, consider someone trying to learn tennis. Getting the service right requires a lot of practice, especially learning to serve an ace (serve that is beyond the reach of the opponent). To master the serve in tennis (especially an ace), a player must practice several thousand times; each practice session is a learning. In machine learning algorithms, we develop models which can run into several hundreds, and each model is treated as a learning opportunity (Pradhan and Kumar, 2017). Mitchell (2006) defined Machine Learning as follows:

> *A computer program or an algorithm, learns from Experience (E), with respect to a given Task (T) and Performance Measure (P), if the algorithms performance on Task (T) as measured by Performance Measure (P) improves with experience (E).*

Let the task *T* be a classification problem. To be more specific, consider the customer’s propensity to buy a product. The performance *P* can be measured through several metrics such as overall accuracy, sensitivity, specificity, and Area Under the Receive Operating Characteristic Curve (AUC). The experience *E* is the data through which the learning algorithm tries to learn the task (T). The major difference between statistical learning and machine learning is that statistical learning depends heavily on validation of model assumptions and hypothesis testing, whereas the objective of machine learning is prediction accuracy. For example, while developing a regression model, we check for assumptions such as normality of residuals, significance of regression parameters, and so on. However, in the case of random forest using classification trees, the most important objective is the accuracy/performance of the model. Note that statistical learning techniques such as regression and logistic regression are subsets of machine learning. Machine Learning (ML) tasks are classified into three broad categories:

**1.** **Supervised Learning:** In supervised learning, datasets have the values of input variables (feature values) and the corresponding outcome variable value. The algorithms learn from the training dataset and predicts the outcome variable for a new record for a given input variable value. Regression and logistic regression are examples of supervised learning algorithms. Feature weights in case of supervised learning are estimated by minimizing a loss function.

**2.** **Unsupervised Learning:** In this case, the dataset will have only input variable values, but not outcome variable. The algorithm learns the structure in the inputs. Clustering and factor analysis are examples of unsupervised learning and will be discussed in [Chapter 8](#16_Chapter08.xhtml).

**3.** **Reinforcement Learning:** In this instance, the input and/or output variables are uncertain. Predictive words used in smartphones is an example of reinforcement learning.

### 7.2 | How Do Machines Learn?

In supervised learning, the algorithm learns by minimizing a loss function (also known as cost function or error function), which is a function of predicted output using inputs and the desired output. If *h(X*[*i*]*)* is the predicted output and *y*[*i*] is the desired output, then the loss function is as follows:

![](images/page230-01.png)

where ‘n**’** is the total number of records for which the predictions were made. The function defined in [Eq. (7.1)](#15_Chapter07.xhtml#eq7.1) is sum of squared error, which is a loss function for regression algorithm. The objective is to learn values of parameters (aka feature weights) that minimize loss function. Many existing algorithms can be used to minimize loss function. The most widely used optimization technique is called Gradient Descent. In the next section, we will look at an example of regression problem and understand how Gradient Descent helps learn the function. Apart from loss function defined in [Eq. (7.1)](#15_Chapter07.xhtml#eq7.1), there are other forms of loss functions. For example, deviance is used as loss function in logistic regression.

### 7.3 | Gradient Descent

In this section, we will discuss how Gradient Descent (GD) algorithm can be used to estimate the values of regression parameters (Pradhan and Kumar, 2017), given a dataset with input (X) and output ( Y). The functional form of a simple linear regression model is given by

![](images/page230-02.png)

**1.** h(X) is the predicted value of *Y*

**2.** *β*[0] is called bias or intercept

**3.** *β*[1] is the feature weight or regression coefficient

**4.** ε is the error in prediction

The error is given by

![](images/page230-03.png)![](images/page231-01.png)

The cost function for the Linear Regression model is the Mean Square Error (MSE) across all records and is given by

![](images/page231-02.png)

where *n* is the total number of records or examples in the data. *Y*[*i*] and *X*[*i*] represents the *i*^(th) record in the data. The error is a function of β[0] and β[r] It is a pure convex function with a global minimum as shown in **[Figure 7.1](#15_Chapter07.xhtml#fig7.1).** The GD algorithm starts at a random starting value (for β[0] and *β*[1]) and moves towards the optimal solution as shown in **[Figure 7.1](#15_Chapter07.xhtml#fig7.1).**

GD finds the optimal values of *β*[0] and *β*[1] that minimize the loss function using the following steps:

**1.** Randomly guess the initial values of *β*[0] (bias) and *β*[1] (feature weight)

**2.** Calculate the estimated value of outcome variable for initialized values of bias and weights

**3.** Calculate error function (MSE)

**4.** Adjust *β*[0] and *β*[1] values by calculating the gradients of the error function

![](images/page231-03.png)![](images/page231-04.png)

where, *α* is the learning rate; value of *α* is chosen based on the magnitude of the update which needs to be applied to the bias and weights at each iteration. Intuitively, the learning rate depicts how big or small a step the GD algorithm will take to descend to the minimum value. The learning rate is a hyper-parameter and different values may need to be tested before deciding on the optimal learning rate. Setting this value to small may take the algorithm a longer time to converge. Setting the learning rate to high may lead the algorithm to overshoot the convergence point and keep oscillating but never reach the minima. We may test a set of values, that is, 0.01, 0.03, 0.09, 0.27, etc., before deciding the optimal value.

The partial derivatives of MSE with respect to *β*[0] and *β*[1] are given by

![](images/page231-05.png)![](images/page231-06.png)

**5.** Repeat steps 1-4 until the error stops reducing further or the change in cost is infinitesimally small. *β*[0] and *β*[1] at the minimum cost points are final estimates and the corresponding function is the best model that can be learnt.

#### 7.3.1 Developing a GD Algorithm for Linear Regression Model

For better understanding of the GD algorithm, we will implement it on the IPL dataset **([Table 7.1](#15_Chapter07.xhtml#tab7.1))** discussed in [Chapter 5](#13_Chapter05.xhtml).

Invoke ggplot package for plotting the MSE and load the dataset using read. csv() from utils package.

![](images/page232-01.png)

Applying some basic changes to the ipl\_df which were discussed in [Chapter 5](#13_Chapter05.xhtml).

![](images/page232-02.png)

#### Creating Feature Set (*X*) and Outcome Variable (*Y*)

We can write a generic function to extract the predictors and response variable from the dataset as shown here:

![](images/page232-03.png)

We can identify the features which don’t want as independent features in model building. Three such features are PLAYER\_NAME, TEAM, and AUCTION\_YEAR. We will also keep BASE PRICE outside the feature list. The below code chunk removes these features from the predictor list.

![](images/page233-01.png)![](images/page233-02.png)

#### Encoding Categorical Features

In this section, we will discuss encoding categorical features without the use of the caret package. Note that the numeric features are also being standardized for GD to converge faster.

![](images/page233-03.png)![](images/page234-01.png)

#### Set ***x*** and ***y*** Variable

The processed\_df contains the standardized and dummy variable coded features which will be used for regression modelling. Separating the features as *X* (predictor) and *Y* (outcome) feature. The predictors are shown in **[Table 7.2](#15_Chapter07.xhtml#tab7.2).**

![](images/page234-02.png)

The first five records and first 10 features in *X* are as follows **([Table 7.2](#15_Chapter07.xhtml#tab7.2)):**

![](images/page234-03.png)

The first six records of SOLD PRICE (*Y*) are shown in **[Table 7.3](#15_Chapter07.xhtml#tab7.3):**

![](images/page234-04.png)![](images/page234-05.png)

**TABLE 7.3** | *Y* **features**

| SOLD\_PRICE |
| --- |
| −1.1583445 |
| --- |
| −1.1583445 |
| −0.4208947 |
| 0.8081883 |
| 0.6852800 |
| −1.1583445 |

#### Implementing the GD Algorithm

To implement the steps explained in [Section 7.3](#15_Chapter07.xhtml#sec7.3), a set of following user-defined functions need to be implemented.

**Step 1:** Function to randomly initialize the beta coefficients.

![](images/page235-01.png)

*x* represents the features in the dataset. In the above function, we will initialize betas to zero for all features in the dataset.

**Step 2:** Function to calculate the predicted value of *Y*, that is, *Y* given the bias and weights

![](images/page235-02.png)

%\*% represents matrix multiplication. Thus, the above code is implementing the equation *h*(*x*^(*i*)) = *β*[0] + *β*[1] \* *X*¹ + … + *β*[*m*] \* *X*^(*m*) for all the *m* features in the dataset (*X*^m is the *m*^(*th*) feature).

**Step 3:** Function to calculate the cost function from predicted and actual values of *Y*. Let us put equation \*\* in implementation and define the Mean Squared Error function, that is, Compute Mean Squared Error (MSE) by

**1.** Calculating differences between the calculated *Y* and actual *Y*

**2.** Calculating the square of the above residuals and summing it up

**3.** Dividing it with a number of observations

![](images/page235-03.png)

**Step 4:** Function to calculate the gradients and adjust the bias and weights

This is the most important method, where the bias and weights get adjusted based on the gradient of the cost function. Equations (7.5) and (7.6) are implemented in the update\_beta() as beta= beta – alpha \* delta.

![](images/page235-04.png)

**Step 5:** Updates to the betas need to be done iteratively, until the cost is minimum. It can take several iterations and be time-consuming. There are two approaches to stop the iterations.

**1.** Run a fixed number of iterations and use the betas as optimal values at the end of these iterations.

**2.** Run iterations until the *δ* change in MSE or cost is small, that is, less than the predefined value, for example 0.001.

![](images/page235-05.png)

We will illustrate the first approach to find the optimal beta coefficients. Let us initialize the learning rate, that is, alpha to 0.01. Iteration “iter” is the number of loops defined for the descent.

![](images/page236-01.png)

Later on, we will use the caret package glmnet() function to find the best beta coefficients which minimize the MSE or the cost function.

#### Plot Cost Value

We can plot cost as a function of number of iterations to converge.

![](images/page236-02.png)

In **[Figure 7.2](#15_Chapter07.xhtml#fig7.2)**, we can see that the MSE or the cost does not seem to change as the number of iteration crosses 1,000. By analyzing the cost\_history, we can see that the convergence, that is, *δ* change in MSE has been reached in 1,488 iterations. One can use the above code using do while or while loop rather than restricting the number of iterations. The final weights are stored in beta coefficients.

![](images/page236-03.png)![](images/page237-01.png)

**Gradient descent** is a popular optimization algorithm and is at the core of many advanced Machine Learning algorithm, including neural networks. Gradient descent is used for finding the feature weights in AI and ML algorithms.

The weights are standardized values as we have used standardized values of *Y* and *X.* So, the interpretation the beta coefficients for ODI\_RUNS\_S will change in terms of standard deviations, that is, for one standard deviation change in ODI\_RUNS\_S, the SOLD\_PRICE changes by 0.43 standard deviations.

The above implementation of machine learning algorithm using GD algorithms is important for understanding the estimation of feature weights. In the above implementation, we have not taken care of regularization. Intuitively, we can think of regularization as a technique for performing a trade-off between model overfitting (variance) and model underfitting (bias). The regularization term is added to the MSE or the cost function to penalize the beta coefficients in order to tackle the overfitting issue.

![](images/page237-02.png)

### 7.4 | Bias-Variance Trade-off

Model errors can be decomposed into two components called bias and variance. Understanding these two components is the key to diagnosing model accuracies and avoid model overfitting or underfitting. High bias can lead to building underfitting models, whereas high variance can lead to overfitting models, and thus can result in generalization errors. **[Table 7.4](#15_Chapter07.xhtml#tab7.4)** shows two specific features from a patient’s dataset, that is, weight (X) and height of the patients (*Y*).

**TABLE 7.4** | Patient data

| BODY\_WEIGHT || BODY\_HEIGHT |
| --- | --- |
| 49 || 160 |
| --- | --- |
| 41 || 155 |
| 47 || 164 |
| 80 || 173 |
| 58 || 175 |
| 45 || 140 |

![](images/page238-01.png)

Assume that we want to build a regression model to predict the height of the person given the weight. As there are only two variables, we can observe the relationship by plotting them using scatter plot.

![](images/page238-02.png)

It can be observed from **[Figure 7.3](#15_Chapter07.xhtml#fig7.3)** that the relation between *Y* and *X* is not linear and looks polynomial. But we are not sure of the degree of the polynomial form. We need to try various polynomial forms of *X* and verify which model is the best fit to the data. The poly() function from stats package can be used to create features with varying degrees, that is, 2, 3, 4, etc. If we create a second degree feature using the poly() function, the data will look like what is shown in **[Table 7.5](#15_Chapter07.xhtml#tab7.5):**

**TABLE 7.5** | Polynomial feature

| 1 || 2 |
| --- | --- |
| 49 || 2,401 |
| --- | --- |
| 41 || 1,681 |
| 47 || 2,209 |
| 80 || 6,400 |
| 58 || 3,364 |
| 45 || 2,025 |

![](images/page239-01.png)![](images/page239-02.png)

The first column of **[Table 7.5](#15_Chapter07.xhtml#tab7.5)** is the actual body weight and the second column represents the square of body weight. Using the values in **[Table 7.5](#15_Chapter07.xhtml#tab7.5)** as predictors, the functional form of regression model will be ![](images/pageIn_ch7-01.png). However, before proceeding with model building, let us split the raw\_df to training and test data. We will also write a user-defined function fit\_ploy () to build a polynomial regression model with any degree *n.*

![](images/page239-03.png)

fitted.values function extracts the predicted value of *Y* from the model. Using the fit\_poly() function defined above, let’s create a linear fitted regression model and also create models with second- to tenth-degree polynomial fits and add the fitted values as a part of train df. **[Table 7.6](#15_Chapter07.xhtml#tab7.6)** shows the fitted.values on the train\_df.

![](images/page239-04.png)![](images/page240-01.png)![](images/page240-02.png)

**[Table 7.7](#15_Chapter07.xhtml#tab7.7)** shows the predicted values of the above model on the test\_df. Later on, we will use the result of **[Table 7.7](#15_Chapter07.xhtml#tab7.7).**

![](images/page240-03.png)

Let us plot the various models built using the train df. The model outcomes are stored in **[Table 7.6](#15_Chapter07.xhtml#tab7.6)** and we will use ggplot() to visualize the data.

![](images/page240-04.png)

Linear model (*h*(*x*[*i*]) = *β*[0] + *β*[1] \* *X*[1]) is shown in **[Figure 7.4](#15_Chapter07.xhtml#fig7.4).** It is evident from **[Figure 7.4](#15_Chapter07.xhtml#fig7.4)** that the regression model does not seem to fit the data well. It is not able to learn from data as a simplistic form of model is assumed, thus creating bias. This is a case of underfitting or bias (Pradhan and Kumar, 2017). The model is highly biased. Let us fit a regression model with a polynomial term, that is, square of *X*.

![](images/page240-05.png)![](images/page241-01.png)

**[Figure 7.5](#15_Chapter07.xhtml#fig7.5)** shows the fitted model with a functional form ![](images/pageIn_ch7-02.png). The regression line seems to fit data better than the previous model. But we are not sure if this is the best model. Let us plot the higher-degree models which we have built.

![](images/page241-02.png)![](images/page241-03.png)![](images/page241-04.png)![](images/page242-01.png)

It can be observed from **[Figures 7.6](#15_Chapter07.xhtml#fig7.6)** and **[7.7](#15_Chapter07.xhtml#fig7.7)** that as we build models with more and more polynomial terms, the model starts to fit every data point in the training set (Pradhan and Kumar, 2019). This is a case of overfitting. The model with polynomial terms up to degree 10 will be sensitive to any changes in training examples. Any addition and removal of even a single observation from the dataset can alter the model parameters significantly.

An underfitting model has large error because of high bias, while an overfitting model has large error because of high variance. An optimal model will be somewhere between an underfitting and overfitting model, and will have low bias and low variance. This can be observed by comparing model accuracy in training and test sets. For 10 different polynomial models, let us compute the RMSE on the train\_df and test\_df. Note that the metrics RMSE and MSE are sensitive to outliers (Mean Absolute Error, MAE, may be more robust to outliers in data). However, we will proceed with using RMSE to report the error in this case. Let us store the degree and error details in different columns of a dataframe named error\_df. **[Table 7.8](#15_Chapter07.xhtml#tab7.8)** shows the details of the error\_df.

![](images/page242-02.png)![](images/page242-03.png)

**1.** degree: Degree of the model (number of polynomial terms)

**2.** train\_error: RMSE error on train set

**3.** test\_error: RMSE error on test set

![](images/page243-01.png)![](images/page243-02.png)![](images/page243-03.png)

**[Figure 7.8](#15_Chapter07.xhtml#fig7.8)** was obtained when we did a 60:40 split of data. This random split resulted in 100 records for train\_df and 63 records in test\_df. From **[Figure 7.8](#15_Chapter07.xhtml#fig7.8)**, we can see that

**1.** Polynomial regression model with degree 1 (fit\_1\_degree in **[Table 7.6](#15_Chapter07.xhtml#tab7.6))** shows high error for both train\_df and test\_df (huge gap between the error may or may not be there).

**2.** Polynomial regression model with degree 10 (fit\_10\_degree in **[Table 7.6](#15_Chapter07.xhtml#tab7.6))** shows low error on train\_df but high error on test\_df (and huge gap b etween the error).

![](images/page244-01.png)

**3.** With increase in the polynomial degree, model error on test set reduces initially, but shows an increase after a specific degree.

**4.** As the degree of the polynomial increases, the model error on training set decreases continuously.

We have to decide which model to select as the best model. Intuitively, when we try to select the degree of the polynomial which results in the best model, we are performing hyperparameter fine-tuning. Or, so to say, every addition of a polynomial term is analogous to adding a feature and thus the degree of the polynomial which results in the best model can be thought of as a hyper-parameter fine-tuning.

We can also associate degree of the polynomial to the complexity of the model. From **[Figure 7.8](#15_Chapter07.xhtml#fig7.8)**, it can be observed that as complexity (number of polynomial terms in the model) increases, the model starts to fit train and test data well. But beyond a specific level of complexity (Pradhan and Kumar, 2017), that is, complexity level 3, the train error continues to reduce, but the test error starts to increase again. This is the point where the model starts to overfit the training set and stops generalizing. So, the optimal model complexity is 3, which has low bias and low variance. So, to generalize, we select a degree of the model which satisfies all the following three criteria:

**1.** Reports lowest error on the train set.

**2.** Reports lowest error on the test set.

**3.** Difference between train error and test error is minimum.

However, can we look at just one random split of train and test set to conclude that the polynomial model with degree 3 gives a good generalization (less error on the test data)? We must repeat the process for several training and test data.

### 7.5 | Strategy to Improve ML Models – Bias Variance Trade-off

We often end up in situations where we discuss having more data to make a better model or more features to improve the model performance. Adding more features is synonymous with increasing the complexity of the model (adding high-degree polynomial terms). However, it is to be kept in consideration that the discussion around more data or more features may not make sense unless we have built the first model and evaluated its performance. If the model suffers from the issue of high bias (underfitting):

**1.** Adding more training data may not help.

**2.** Adding more features or using a complex model may help.

Practically, it will be useful to start with a complex model and then reduce the model complexity to come to a model which is much more generalizable. But if we start with a complex model, we may end up with high variance issue. If the model suffers from high variance (overfitting), then:

**1.** Adding more training data may help as overfitting may stem from limited training data.

**2.** Reducing the number of features or regularization may also help in reducing high variance.

#### 7.5.1 Reduce Variance – Adding More Observations

From **[Figure 7.8](#15_Chapter07.xhtml#fig7.8)**, we can conclude that the model with degree 10 results in a high variance issue. Let us try to solve the issue of high variance by adding more data on the training set. **[Figure 7.9](#15_Chapter07.xhtml#fig7.9)** shows the performance of different polynomial models by changing the train and test split to 70:30.

**[Figure 7.8](#15_Chapter07.xhtml#fig7.8)** suggests model with degree 3 is the best. However, **[Figure 7.9](#15_Chapter07.xhtml#fig7.9)** suggests that the model with degree 5 helps reduce the error more on the test set. Splitting the data in 80:20 resulted in a different performance as shown in **[Figure 7.10](#15_Chapter07.xhtml#fig7.10).**

From **[Figure 7.10](#15_Chapter07.xhtml#fig7.10)**, we see that models with any polynomial degree term are reporting less test\_error compared to train\_error. However, as we do a random split of data to increase the train set, the observations in the test data decrease. Though a random split, this small set of observations may also mean there are no outliers (extreme values) in the test data. The RMSE as a metric being sensitive to outliers may have resulted in high error on the train data and model reporting low error on the test set which need not necessarily mean better generalizability of the model. From **[Figure 7.10](#15_Chapter07.xhtml#fig7.10)**, we will still select the model with degree 5 as the best model. However, the takeaway is that

**1.** A single train and test split may not be sufficient to conclude that we have selected a model which trades-off bias and variance.

**2.** Adding more observations in the training set by reducing the number of observations in test set may lead to selecting a model with higher complexity (compare **[Figure 7.8](#15_Chapter07.xhtml#fig7.8)** with **[Figures 7.9](#15_Chapter07.xhtml#fig7.9) and [7.10](#15_Chapter07.xhtml#fig7.10).)**

This is where we may have to use cross validation or repeated cross validation as a strategy to select the best model.

![](images/page245-01.png)![](images/page246-01.png)![](images/page246-02.png)

#### *K*\-Fold Cross Validation

*K*\-fold cross validation is a robust validation approach which can be adopted to verify if the model is overfitting (Pradhan and Kumar, 2019). If the model generalizes well and does not overfit, it should not be very sensitive to any change in underlying training examples. *K*\-fold cross validation can achieve this by building and validating multiple models by resampling multiple training and validation sets from the sample set. The following steps are used in *K*\-fold cross validation:

**1.** Split the training data set into *K* equal subsets. Each subset is called a fold. Let the folds be named as set\_1, set\_2, … set\_*K*. Generally, the value of *K* is taken to be 3, 5, 7, or 10.

**2.** For *i* = 1 to *i* = *K*

(a) Keep the fold set\_ *i* as validation set and all the remaining *K–*1 folds as training set.

(b) Train the machine learning model using the training set and calculate the accuracy of the model with the set\_i which is set aside for validation.

**[Figure 7.11](#15_Chapter07.xhtml#fig7.11)** depicts the process of *K*\-fold cross validation (*K* is taken as 5 in **[Figure 7.11](#15_Chapter07.xhtml#fig7.11)).**

A detailed explanation of CV was given in [Chapter 6](#14_Chapter06.xhtml). Calculate the final accuracy by averaging the accuracies across all *K* models. The average accuracy value shows how the model will behave in the real world. The variance of these accuracies is an indication of the robustness of the model.

#### 7.5.2 | Reduce Variance – Applying Regularization

Another way to deal with overfitting (reduce variance) is to apply regularization. In case of regression, it is observed that overfitting is typically caused by estimation of inflated coefficients (weights) for the parameter. To avoid overfitting, the estimated coefficients (weights) should be regulated by penalizing. Regularization applies penalties on parameters if it becomes too large and keeps them from being weighted too heavily. The coefficients (weights) are penalized by adding the coefficient terms to the cost function. If the coefficients become large, the cost increases significantly. So, the optimizer controls the coefficient values to minimize the cost function. The following two approaches can be used to add penalty to the cost function.

While building a Machine Learning model, **bias-variance trade-off** is an important consideration to generalize the model and make it useful in prediction on unseen/future data points.

**1.** **L1 norm:** Adding summation of the absolute value of the coefficients. This is also called Least Absolute Shrinkage and Selection Operator (LASSO Term). The corresponding cost function is given by

![](images/page247-01.png)

In [Eq. 7.9](#15_Chapter07.xhtml#eq7.9), *n* is the number of records and *m* is the number of features in the data. *a* is a multiplier for which the optimal value needs to be found by hyper-parameter fine-tuning.

In **L1 norm**, by virtue of the penalty being summation of the coefficient terms ![](images/pageIn_ch7-03.png), the shape or the area defined is that of a square. In L2 norm, since the penalty is summation of square of the coefficients ![](images/pageIn_ch7-04.png), the shape/area defined by it is that of a circle.

**2.** **L2 norm:** Adding the squared value of the coefficients. This is called Ridge Term. The cost function is given by

![](images/page247-02.png)

*γ* is a multiplier for which the optimal value needs to be found by hyper-parameter fine-tuning. Note that in both L1 and L2 norms, we are not penalizing the intercept, that is, *β*[0].

Ridge distributes (smoothens) the coefficient values across all the features, whereas LASSO reduces some of the coefficients to zero. Features with coefficient value as zero can be treated as features with no contribution to the model. So, LASSO can also be used for feature selection, that is, remove features with zero coefficients, thereby reducing the number of features. **[Figure 7.12](#15_Chapter07.xhtml#fig7.12)** shows the role of L1 and L2 penalty in regularization.

**3.** **ElasticNet Regression:** ElasticNet regression combines both L1 and L2 regulariza-tion to build a regression model. The corresponding cost function is given by

**MSE** has a convex shape and in 2-dimensional plot, it can be plotted as an elliptical shape (Contour plots). Finding the smallest MSE under L1 norm is intuitively same as finding an elliptical shape which is tangent to the square area. Given the underlying math, the tangent may fall at the vertex of the square at times and thus for some coefficients, estimate comes out to be exactly zero.

![](images/page247-03.png)

While building ElasticNet regression model, both hyper-parameters *σ* (L1) and *γ* (L2) need to be set.

#### Intuition behind Regularization

Consider the patients dataset (height and weight) which was discussed in [Section 7.4](#15_Chapter07.xhtml#sec7.4). Looking at the plots and bias variance trade-off, we conclude that the polynomial with degree 3 seems the best fit to the data. But let us assume that we have made the complex model and have fitted the polynomial model with degree 6. So, the functional form which we have used for modelling is as follows:

![](images/page247-04.png)

Finding the **smallest MSE under L2 norm** is also intuitively same as finding an elliptical shape which is tangent to the circular area. Given the underlying math, it is unlikely that the tangent falls on the axis, though may be possible at times, of the circle and thus the coefficients estimates may come out to be close to zero but not exactly zero.

![](images/page248-01.png)

where *h*(*X*) is the estimated height and *x* represents the weight of the patient. Since we know that the best fit to the data will be a model with degree 3, let us modify the cost function so as to give very high weights to *β*[4], *β*[5], and *β*[6]. Thus, the modified cost function will be as follows:

![](images/page248-02.png)

In [Eq. (7.13)](#15_Chapter07.xhtml#eq7.13), *β*[4], *β*[5], and *β*[6] have been multiplied with a value of 1,500. Since the objective is to find the *βs* which minimize the MSE, we can intuitively think that the cost will be minimum when *β*[4] ≈ 0, *β*[5] ≈ 0, and *β*[6] ≈ 0. When this happens, the functional form will reduce to a polynomial fit with degree 3.

However, in a real-world example, we will not know the features to which we can assign a higher weight to reduce the impact of the feature on the overall outcome. In order to overcome the situation, we penalize all the features. This is achieved by adding L1 or L2 norm which inherently tries to minimize the influence of all the features on the final outcome (*h*(*x*)).

Cross validation technique, along with regularization, may help build a robust machine learning model. Caret provides glmnet method which can be used to apply regularization. We will use glmnet method from the caret package and cv method through trainControl() for building machine learning models. We will also see the direct implementation of cv.glmnet() method from glmnet package to build the regularized regression model.

### 7.6 | Machine Learning – Regression Using glmnet Package

We used the caret package to build statistical models in [Chapter 5](#13_Chapter05.xhtml) (Linear Regression) and [Chapter 6](#14_Chapter06.xhtml) (Classification). Here we will use the glmnet package to fit linear, logistic, multinomial, and many other models. The steps for making a machine learning model using the glmnet package will remain the same.

**1.** Identify the input and output variables.

**2.** Split the dataset into training and test sets.

**3.** Build the model using training set.

**4.** Predict outcome variable using test set.

**5.** Compare the predicted and actual values of the outcome variable in test set and measure accuracy using measures such as Mean Absolute Percentage Error (MAPE) or Root Mean Square Error (RMSE).

One point to note is that the glmnet method expects explicit dummy variable coding. So, we will employ dummy variable coding using dummyVars from the caret package before calling the glmnet method.

The cost function for regression which is actually solved for in glmnet is

![](images/page248-03.png)

where *n* is the number of observations and *m* is the number of features. For Gaussian case, that is, continuous *Y*, the *l*(*y, η*), in [Eq. (7.14)](#15_Chapter07.xhtml#eq7.14), is replaced by ![](images/pageIn_ch7-05.png). So, [Eq. (7.14)](#15_Chapter07.xhtml#eq7.14) for Gaussian case will be as follows:

![](images/page248-04.png)

The elastic-net penalty is controlled by *α.* If more than two predictors correlated with each other, then *α* = 0.5 will select either all the predictors (even if one amongst the predictors have a strong correlation with outcome variable) or it will not select any of the predictors. Some useful points to control the above cost function are as follows:

**1.** Setting (*α* = 0) gives a ridge regression. Ridge penalty shrinks the coefficients of correlated predictors towards each other.

**2.** Setting (*α* = 1, the default) gives a LASSO regression. In case there are two correlated coefficients, LASSO penalty tends to pick one of them and discards the other.

**3.** The tuning parameter *λ* controls the overall strength of the penalty. Setting *λ* = 0 makes an OLS model irrespective of the value set for *α*.

**4.** *α* is a higher-level parameter for which the value can be picked upfront or can be given as a hyper-parameter fine-tuning as well.

Let us apply the above steps to build a regularized regression model to predict the SOLD\_PRICE of the players using the new\_ipl\_df. Using new\_ipl\_df, let us generate ipl\_with\_dummy\_df which is a dummy variable coded data.frame. **[Table 7.9](#15_Chapter07.xhtml#tab7.9)** shows the snapshot of the dummy variable coded data.frame.

![](images/page249-01.png)![](images/page249-02.png)

#### 7.6.1 Create Feature Set (X) and Outcome Variable (V)

Let us get the predictors and outcome features from ipl\_with\_dummy\_df.

![](images/page249-03.png)![](images/page250-01.png)

‘AGE’, ‘COUNTRY’, ‘PLAYING\_ROLE’, ‘T\_RUNS’, ‘T\_WKTS’, ‘ODI\_RUNS\_S’, ‘ODI\_SR\_B’, ‘ODI\_WKTS; ‘ODI\_SR\_BII ‘CAPTAINCY\_EXP, ‘RUNS\_S, ‘HS’, ‘AVE\_B’, ‘SR\_B, ‘SIXERS, ‘RUNS\_C’, ‘WKTS’, ‘AVE\_BII ‘ECON’, ‘SR\_BL’

#### 7.6.2 Create Train and Test Set

createDataPartition() function from the caret package provides the ability to split the dataset randomly into training and validation datasets.

![](images/page250-02.png)

Since glmnet expects *X* features in matrix form, let us typecast the train df as matrix and create *X* (features) and *Y* (outcome) variables.

![](images/page250-03.png)

#### 7.6.3 LASSO Regression Using glmnet

The function glmnet from the glmnet package can be used to make LASSO, ridge, or ElasticNet model. However, this function returns a sequence of models. We are interested in having the best model rather than a sequence of models. Cross validation technique is the simplest and most widely used method for this task. Thus, glmnet also provides cv.glmnet to apply cross validation strategy to select the best model directly.

Let us make a model by directly using the cv.glmnet from the package glmnet. We will also invoke parallel processing using the doMC package. We will engage two cores using registerDoMC function.

![](images/page250-04.png)

Let us build the init\_model invoking parallel processing by registering two cores. We will return the best model using 5-cross validation sets. We will use Mean Squared Error as the metric to report the best model. The nlambda = 100 is a default parameter.

![](images/page251-01.png)

The family parameter for cv.glment() and glmnet(), by default, is set to Gaussian, that is, it deals with continuous outcome (*Y*). The init\_model object contains all the information available to interpret and use the result. However, a few points to note, as listed below:

**1.** type.measure = “mse” implies use of Mean Squared Error for reporting the best model.

**2.** The results of cv.glmnet are random, since the folds are selected at random. This randomness can be reduced by running cv.glmnet many times, and averaging the error curves (average of the lambda values which minimizes the error). We can use set. seed() to have reproducibility in the code.

**3.** cv.glmnet fine-tunes only lambda value. It does not search for values of alpha. A specified value of alpha should be specified, else alpha = 1 is assumed (default, lasso regression). In order to fine-tune both alpha and lambda, use cva.glmnet.

#### Intuition Behind Lambda Sequence

In the cv.glmnet function, we specified the number of lambda values to evaluate as 100. The program internally generates 100 different lambda values and provides the best fit model. The documentation[¹](#15_Chapter07.xhtml#ch7-r-fn1) for glmnet on lambda parameter is as below:

> “Lambda values can be provided, but are typically not, and the program constructs a sequence. When automatically generated, the *λ* sequence is determined by lambda.max and lambda.min.ratio. The latter, that is, lambda.min.ratio is the ratio of the smallest value of the generated *λ* sequence (say lambda.min to lambda.max). The program then generates nlambda values linear on the log scale from lambda.max down to lambda.min”.

lambda.max is not given, but easily computed from the input *X* and *Y* (Anon, 2018); it is the smallest value for **lambda** such that all the coefficients are zero.[²](#15_Chapter07.xhtml#ch7-r-fn2)

![](images/page251-02.png)

In [Eq. (7.16)](#15_Chapter07.xhtml#eq7.16), *m* is the number of observations in the data. Let us create the lambda.max value based on the above equation. We will standardize *X* variables using the my\_scale function. We have also defined a get\_lambda\_max to get the lambda.max.

![](images/page251-03.png)![](images/page252-01.png)

Once the lambda.max is identified, the strategy is to select lambda.min (Friedman, Hastie, & Tibshirani, 2010) and construct a sequence of *K* = 100 values of lambda decreasing from lambda\_max to lambda\_min on the log scale. The formula to select lambda.min is as follows:

![](images/page252-02.png)

Typical values are epsilon = 0.0001 and *K* = 100. To generate the lambda sequence, let us define get lambda seq()

![](images/page252-03.png)

We will call the above function to get the sequence of lambda values:

![](images/page252-04.png)

The sequence of values generated by the cv.glmnet is as follows:

![](images/page252-05.png)![](images/page253-01.png)

Note:

**1.** The manual sequence and the sequence generated by glmnet are exactly the same. In later section, we will use the manual sequence to train the model using the caret package.

**2.** Instead of 100 lambda sequence, the init\_model reported only 81 lambdas. This is so because the model may not have shown improvement in **MSE** with the other lambda sequence along the path.

**3.** For alpha = 0 (ridge) lambda.max would be ∞; hence, for this case, the lambda value is picked up corresponding to alpha value close to zero (alpha = 0.001).

Another useful argument named penalty.factor allows users to apply separate penalty factors to each coefficient. Its default is 1 for each parameter, but other values can also be specified. If we do not want a specific feature to be penalized, then we can change the penalty.factor to zero for such features.

There are several other arguments which can be passed inside glmnet and cv.glmnet but they are mostly set to default. More information about the parameters which can be passed to glmnet can be obtained by passing ?glmnet: :glmnet on the console.

#### 7.6.4 Interpretation of Outcome

In [Section 7.6.3](#15_Chapter07.xhtml#sec7.6.3), we have developed a LASSO regression using glmnet package. Let us understand the outcomes stored as a part of the object, created using cv.glmnet, init\_model. We will print the init\_model using the below code line.

![](images/page253-02.png)![](images/page254-01.png)

The output of init\_model shows the following:

**1.** The number of nonzero coefficients (*Df*).

**2.** The percent (of null) deviance explained (%Dev), that is, how well the outcome variable is predicted by the model with only intercept term.

**3.** The value of lambda. Each row item corresponds to a model for the value of lambda mentioned therein.

By default, glmnet calls for 100 values of lambda. However, the program stops early if “%Dev” does not change sufficiently from one lambda to the next (typically near the end of the path.)

The plot function can be used to plot the above information. Let us plot the init\_model.

![](images/page255-01.png)

The plot in **[Figure 7.13](#15_Chapter07.xhtml#fig7.13)** for init model includes the following:

**1.** The mean cross-validated error (red dotted line which is init\_model$cvm) for each lambda.

**2.** Upper and lower standard deviation curves along the lambda sequence (error bars).

**3.** The two selected lambdas are indicated by the vertical dotted lines.

The first vertical line corresponds to the value of lambda (approx. 10.25 in this case) that gave minimum cross validation error measured by MSE. This value can be obtained by

![](images/page255-02.png)

Note that the plot in **[Figure 7.13](#15_Chapter07.xhtml#fig7.13)** is showing lambda in logarithmic scale. The number of features retained at this lambda value is 11 (secondary *X*\-axis). The second vertical line corresponds to the value of lambda (approx. 11.1 in this case) which gives the most regularized model such that the error is within one standard error of the minimum, that is, the largest *λ* at which the MSE is within one standard error of the minimal MSE. This value can be obtained by

![](images/page255-03.png)![](images/page256-01.png)

The estimated coefficients corresponding to the lambda which gave the minimum MSE can be obtained as

![](images/page256-02.png)

As can be seen, LASSO regression made the coefficients exactly equal to zero for some of the features. Prediction using the init\_model can be done by using the predict function and passing the train\_df or the test\_df along with the parameter ‘s’ which takes the lambda value at which the prediction is to be made.

![](images/page257-01.png)

It is to be noted that while building the model using the ipl\_df with the same set of features, in [Chapter 5](#13_Chapter05.xhtml), we ended up achieving an R-squared of 0.18 on the test set ([Chapter 5](#13_Chapter05.xhtml), [Section 5.11](#13_Chapter05.xhtml#sec5.11)). We can build ridge regression as well as ElasticNet using the cv.glment function. However, fine-tuning the ElasticNet method to test for different values of alpha requires use of an additional parameter named **foldid.** Instead of building the model using **cv.glment** let us proceed with **caret** which we have used on multiple occasions.

### 7.7 | Machine Learning – Regression Using Caret

Directly building a regression model using glmnet package and calling the glmnet through caret leads to some differences in the final lambda values returned for the best model. This may be due to the internal interaction of caret glmnet method and glmnet package. However, the results may not be very different if the tuning of the model through the caret package is carried out properly. In business-critical projects, it may be advisable to fine-tune and build a regression model using glmnet package rather than using the caret package. If business mandates the use of the caret package, then it may be advisable to generate the lambda sequence using the steps shown in [Section 7.6.3](#15_Chapter07.xhtml#sec7.6.3) and perform a grid search over these lambda values using the caret package (glmnet method).

#### 7.7.1 LASSO Regression Using Caret

We will be using the train\_df and test\_df created as a part of [Section 7.6.2](#15_Chapter07.xhtml#sec7.6.2). Let us first get the list of parameters which can be fine-tuned for glmnet through the caret package.

![](images/page257-02.png)

alpha and lambda are the parameters available for fine-tuning, which is exactly the same as we saw in [Section 7.6.3](#15_Chapter07.xhtml#sec7.6.3). Let us use the expand.grid() to pass on different values of alpha and lambda to build a LASSO, ridge, and ElasticNet regression models.

Let us build the model using the caret package which calls the glmnet. The alpha value for LASSO is fixed at 1. We will vary the range of the lambda values we want to fine-tune. We can define any sequence of lambda values which we want to evaluate. However, in [Section 7.6.3](#15_Chapter07.xhtml#sec7.6.3), we manually generated the sequence which glmnet function evaluates internally. Let us use the same sequence to fine-tune lambda.

![](images/page258-01.png)

Refer [Section 7.6.3](#15_Chapter07.xhtml#sec7.6.3) to know more about get\_lambda\_seq(). The control\_params are set using repeatedcv() method. Repeatedcv() also expects the parameter **repeats** to be passed, which defines the number of times we want to repeat the cross validation set.

![](images/page258-02.png)![](images/page259-01.png)![](images/page260-01.png)

The final hyper-parameter or the fine-tuned parameter reported using repeatedcv() with grid search is as follows:

![](images/page260-02.png)

The coefficients at the best lambda value are as follows:

![](images/page260-03.png)![](images/page261-01.png)

The prediction on the train\_df and the test\_df is as follows:

![](images/page261-02.png)

We can also use the abbreviated form to predict, that is, predict(lasso\_model, test\_df). We can note that the results on the test\_df arrived at by using glmnet package in [Section 7.6.3](#15_Chapter07.xhtml#sec7.6.3) and the results here from the caret package are the same.

#### 7.7.2 Ridge Regression Using Caret

The alpha value for ridge is fixed at 0. For alpha = 0 (ridge) lambda.max would be ∞; hence for this case, the lambda value is picked up corresponding to alpha value close to zero (say 0.001). Refer [Section 7.6.3](#15_Chapter07.xhtml#sec7.6.3) for further understanding.

![](images/page261-03.png)![](images/page262-01.png)![](images/page263-01.png)![](images/page264-01.png)

The final hyper-parameter or the fine-tuning parameter reported using repeatedcv with grid search is as follows:

![](images/page264-02.png)

To get the coefficients corresponding to the best alpha and lambda, we will use the coef function.

![](images/page264-03.png)![](images/page265-01.png)

The prediction on the train\_df and the test\_df is as follows:

![](images/page265-02.png)

#### 7.7.3 ElasticNet Regression Using Caret

Let us build an ElasticNet model using glmnet. We will build the ElasticNet model with two different approaches:

**1.** One with tuneGrid parameter, used in Sections 7.6.1 and 7.6.2, which expects an object of expand.grid. We will reuse the lambda\_seq from [Section 7.6.3](#15_Chapter07.xhtml#sec7.6.3).

**2.** Second with tuneLength parameter which randomly searches the parameters.

#### ElasticNet Regression with tuneGrid

Let us get the lambda sequence using the get\_lambda\_seq function defined in [Section 7.6.3](#15_Chapter07.xhtml#sec7.6.3), and pass the same to expand.grid().

![](images/page265-03.png)

The final hyper-parameter or the fine-tuning parameter reported using repeatedcv with grid search is as follows:

![](images/page266-01.png)

The model coefficients for the ElasticNet model are as follows:

![](images/page266-02.png)

The prediction on the train\_df and the test\_df is as follows:

![](images/page266-03.png)![](images/page267-01.png)

#### ElasticNet Regression with tuneLength

Another approach to fine-tune the hyper-parameter is to use the tuneLength parameter of the train function. Using this parameter does not require the use of expand.grid. If we specify tuneLength=10,

**1.** The caret picks alpha = c(0.1 0.2 0.3 0.4 0.5 0.6 0.7 0.8 0.9 1)

**2.** The caret picks up lambda value at an alpha of 0.5 using the glmnet() function from glmnet package. In other words, the user-defined function in [Section 7.6.3](#15_Chapter07.xhtml#sec7.6.3), **get\_lambda\_seq** (x,y, alpha=0.5), can be used to pick the lambda values.

When tuneLength=10 for each alpha, 10 lambda values will be evaluated. Thus, a total of 100 models will be built.

![](images/page267-02.png)![](images/page268-01.png)![](images/page269-01.png)

The reader can use the get\_lambda\_seq(x,y,alpha=0.5) defined in [Section 7.6.3](#15_Chapter07.xhtml#sec7.6.3) to verify that the lambda sequence picked by tuneLength parameter of train() function is exactly the same as shown in the outcome of elasticnet\_model object. The final hyper-parameter or the fine-tuning parameter reported using repeatedcv with tuneLength=10 is as follows:

![](images/page269-02.png)

The model coefficients for the ElasticNet model are as follows:

![](images/page270-01.png)

The prediction on the train\_df and the test\_df is as follows:

![](images/page270-02.png)

### 7.8 | Results summary

**[Table 7.10](#15_Chapter07.xhtml#tab7.10)** summarizes the results of all the models built using glmnet and caret package on the ipl\_df. From **[Table 7.10](#15_Chapter07.xhtml#tab7.10)**, we can see that

**1.** The LASSO regression built using glment and caret reports the same lambda values corresponding to the best model.

**2.** The performance of the ridge model on test set is better than the LASSO regression. The range of lambda values evaluated in ridge regression was obtained using **get\_lambda\_seq**(x,y,alpha=0.001).

**3.** The ElasticNet model outcome using tuneGrid and tuneLength returns almost similar results. The minor difference in result is due to the fact that we created the lambda sequence to be evaluated by using **get\_lambda\_seq**(x,y,alpha=1) and passed it to tuneGrid; however, caret created a range of lambda values **get\_lambda\_seq** (x,y, alpha=0.5) to be used in tuneLength.

The glmnet can be used be build multivariate Gaussian model as well. By setting the fam-ily=mgaussian, the glmnet function can handle multi-task learning problems, that is, when there are a number of (correlated) responses *(Y*s).

![](images/page271-01.png)

### 7.9 | Machine Learning – Logistic Regression Using glmnet

When the response variable (*Y*) is binary, the linear logistic regression model is often used. The logistic regression model represents class-conditional probabilities through a linear function of the predictors. Assume that the outcomes are called positive (usually coded as *Y* = 1) and negative (usually coded as *Y* = 0). The logistic regression model represents the class-conditional probabilities through a linear function of the predictors and is given by

![](images/page271-02.png)

where *Z* = *β*[0] + *β*[1] \* *X*[1] + *β*[2] \* *X*[2] + … + *β*[*m*] \* *X*[*m*]

Here *X*[1], *X*[2], … *X*[*m*] are independent variables or features. If the data has *n* observations, *Y*[1], *Y*[2], … *Y*[*n*], then the likelihood function, which is a joint probability of observing the outcome *L* = P(*Y*[1], *Y*[2], … *Y*[*n*]) for a specific *Z* = *β*[0] + *β*[1] \* *X*[1] + *β*[2] \* *X*[2] + … + *β*[*m*] \* *X*[*m*] is given by (Kumar, 2017)

![](images/page271-03.png)

Taking natural log, [Eq. (7.18)](#15_Chapter07.xhtml#eq7.18) can be re-written as follows:

![](images/page271-04.png)

[Eq. (7.19)](#15_Chapter07.xhtml#eq7.19) can be simplified as follows:

![](images/page272-01.png)

The objective (cost function) is to find the *β* coefficients which maximize [Eq. (7.19)](#15_Chapter07.xhtml#eq7.19), that is, the log likelihood function. In glmnet, the objective function for the penalized logistic regression uses the negative binomial log-likelihood with regularization parameter, and is given by

![](images/page272-02.png)

**[Table 7.11](#15_Chapter07.xhtml#tab7.11)** shows the snapshot of the HR\_Attrition data which we used in classification ([Chapter 6](#14_Chapter06.xhtml)). Refer to [Chapter 6](#14_Chapter06.xhtml) for more details on data processing and feature engineering on HR\_Attrition data. We will use the same data to build the logistic regression model using the glmnet package. The steps to build the logistic regression model will be similar to the steps followed in [Section 7.6](#15_Chapter07.xhtml#sec7.6).

![](images/page272-03.png)![](images/page272-04.png)

#### 7.9.1 Create Feature Set (*X*) and Outcome Variable (*Y*)

Let us get the predictors and outcome feature from attrition\_with\_dummy\_dt which is shown in **[Table 7.11](#15_Chapter07.xhtml#tab7.11).**

![](images/page273-01.png)![](images/page274-01.png)

#### 7.9.2 Create Train and Test Set

createDataPartition() function from the caret package provides the ability to split the dataset randomly into training and validation datasets.

![](images/page274-02.png)

Since glmnet expects *X* features in matrix form, let us typecast the train\_dt as matrix and create *X* (features) and *Y* (outcome) variable.

![](images/page274-03.png)

#### 7.9.3 Classification Model – Logistic Regression Using glmnet

Now, we will build the LASSO logistic regression model by using family=binomial.

![](images/page274-04.png)

Readers are encouraged to use the get\_lambda\_max and get\_lambda\_seq function defined in [Section 7.6.3](#15_Chapter07.xhtml#sec7.6.3) to understand the lambda sequence generated for logistic regression model. Let us get the coefficients for logistic model.

![](images/page274-05.png)![](images/page275-01.png)

As can be seen, the LASSO regression made the coefficients exactly equal to zero for some of the features. Note that we did not remove some of the features which were

**1.** Linearly dependent (RM\_REPORTEES\_COUNT = RM\_REPORTEE\_MALE + RM\_ REPORTEE\_FEMALE), the model dropped on its own.

**2.** Highly correlated, AGE\_DIFFERENCE with RM\_AGE, the model dropped on its own. But if the predictors are correlated in groups, LASSO may not be helpful. ElasticNet with an *α=* 0.5 tends to select the groups in or out together.

Prediction using the init\_model can be done by using the predict function and passing the train\_dt or the test\_dt along with the parameter “s” which takes the lambda value at which the prediction is to be made. We will also pass the argument type = response, which will report the conditional probability for (*Y* = 1). We will convert this probability to class at a default cut-off 0.50. To report the class directly, we can pass type = class.

![](images/page275-02.png)![](images/page276-01.png)![](images/page277-01.png)

#### 7.9.4 Classification Model – Logistic Regression Using Caret

We will use the **tuneLength** parameter of the train function to finetune the ElasticNet model. Refer [Section 7.7.3](#15_Chapter07.xhtml#sec7.7.3) for details about tuneLength.

When tuneLength=10, for each alpha, 10 lambda values will be evaluated. Thus, a total of 100 models will be built.

![](images/page277-02.png)![](images/page278-01.png)![](images/page279-01.png)

The model coefficients for the ElasticNet model are as follows:

![](images/page280-01.png)

The prediction on the train\_dt are as follows:

![](images/page280-02.png)![](images/page281-01.png)

The prediction on the test\_dt are as follows:

![](images/page281-02.png)![](images/page282-01.png)

We have seen the use of glmnet method to solve for regression as well as classification problems.

### Summary

In this chapter, we learnt

**1.** Model building by defining a cost function and using an optimization algorithm to minimize the cost function.

**2.** Implementing a GD algorithm to optimize the cost function for regression-based model.

**3.** Bias and variance trade-off and how to avoid model overfitting using regularization.

**4.** Advanced regression models like LASSO, ridge, and ElasticNet models.

**5.** Building a machine learning model (regression as well as classification) using the glmnet package.

**6.** Building a machine learning model (regression as well as classification) using the caret package.

### Exercise

The dataset SAheart.data is taken from the link given below:

[http://www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data](http://www-stat.stanford.edu/~tibs/ElemStatLearn/datasets/SAheart.data)

The dataset SAheartrateData.txt contains records of males in a heart-disease high-risk region of the Western Cape, South Africa. There are roughly two controls per case of CHD. Many of the CHD-positive men have undergone blood pressure reduction treatment and other programs to reduce their risk factors after their CHD event. In some cases, the measurements were made after these treatments. These data are taken from a larger dataset, described in Rousseauw et al. (1983), *South African Medical Journal.* It is a tab-separated file (.csv) and contains the following columns:

• *sbp* – Systolic blood pressure

• *tobacco* – Cumulative tobacco (kg)

• *ldl* – Low density lipoprotein cholesterol

• *adipos ity*

• *famhist* – Family history of heart disease (Present, Absent)

• *typea* – type-A behavior

• *obesity*

• *alcohol* – Current alcohol consumption

• *age* – Age at onset

• *chd* – Response, coronary heart disease

The *chd* = 1 and *chd* = 0 will be referred to as *chd* and *no chd* cases, respectively.

**1.** Find out the number cases available in the dataset for *chd* and *no chd.* Plot the findings using a bar plot, where *X* is chd or no chd and *Y* gives the count of samples in each group.

**2.** Build a lasso logistic regression model using caret. Use *K*\-fold cross validation (*K* = 5) and ROC AUC score for reporting the best model.

**3.** Build a ridge logistic regression model using caret glm-net method. Use *K*\-fold cross validation (*K* = 5) and ROC AUC score for reporting the best model.

**4.** Build an ElasticNet logistic regression model using caret. Use tuneLength parameter of train() to fine tune the model and ROC AUC score for reporting the best model.

**5.** Build a lasso logistic regression model using glmnet package. Use K-fold cross validation (*K* = 5) to report the best model. Compare and describe the outcome of this model with the model obtained in Question 2.

**6.** Build a ridge logistic regression model using glmnet package. Use *K*\-fold cross validation (*K* = 5) to report the best model. Compare and describe the outcome of this model with the model obtained in Question 3.

**7.** Build an ElasticNet logistic regression model using glmnet package. Use *K*\-fold cross validation (*K* = 5) to report the best model. Compare and describe the outcome of this model with the model obtained in Question 4.

### Bibliography

**1.** Anon (2018), *“Glmnet: How to select Lambda and Alpha”*, Web Address: [https://stats.stackexchange.com/questions/357190/glmnet-how-to-select-lambda-and-alpha](https://stats.stackexchange.com/questions/357190/glmnet-how-to-select-lambda-and-alpha), accessed on 10 May 2021.

**2.** Friedman J and Hastie T, *“Regularisation Paths for Generalized Linear Models via Coordinate Descent”*, Web Address: [https://web.stanford.edu/~hastie/Papers/glmnet](https://web.stanford.edu/~hastie/Papers/glmnet), accessed on 21 January 2021.

**3.** Friedman J, Hastie T, and Tibshirani R (2008), “Regularisation Paths for Generalized Linear Models via Coordinate Descent”, *Journal of Statistical Software*, 33(1), 1–22.

**4.** Hastie T and Qian J (2014), *“Glmnet and Vignette”*, Web Address: [https://web.stanford.edu/~hastie/glmnet/glmnet\_alpha.html](https://web.stanford.edu/~hastie/glmnet/glmnet_alpha.html), accessed on 21 January 2021.

**5.** Hastie T, Qian J and Kenneth Tay (2021), “An *Introduction to Glmnet”*, Web Address: [https://glmnet.stanford.edu/articles/glmnet.html](https://glmnet.stanford.edu/articles/glmnet.html), accessed on 10 May 2021.

**6.** Malviya D (2020), *“Machine Learning”*, Web Address: [https://www.kaggle.com/deepprabhamalviya/ml-day8](https://www.kaggle.com/deepprabhamalviya/ml-day8), accessed on 10 May 2021.

**7.** Mitchell T M (2006), “The Discipline of Machine Learning”, Carnegie Mellon University Report (CMU-ML-06-108), available at [https://www.cs.cmu.edu/~tom/pubs/MachineLearning.pdf](https://www.cs.cmu.edu/~tom/pubs/MachineLearning.pdf), accessed on 02 August 2021.

**8.** Pradhan M and Kumar U D (2019), *“Machine Learning Using Python”*, Wiley, Indian Institute of Management, Bangalore.

**9.** Simon N, Friedman J, and Hastie T (2013), “A Blockwise Descent Algorithm for Group-Penalised Multiresponse and Multinomial Regression, Web Address: [https://arxiv.org/abs/1311.6529](https://arxiv.org/abs/1311.6529), accessed on 10 May 2021.

**10.** Simon N, Friedman J, Hastie T, and Tibshirani T (2011), “Regularisation Paths for Cox’s Proportional Hazards Model via Coordinate Descent”, *Journal of Statistical Software*, 39(5), 1–13.

**11.** Tibshirani R, Bien J, Friedman J, Hastie T, Simon N, Taylor J, Tibshirani R J (2010), “Strong Rules for Discarding Predictors in Lasso-type Problems”, Journal of the Royal Statistical Society: Series B *(Statistical Methodology)*, 74(2), 245–266.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#15_Chapter07.xhtml#ch7-fn1)[https://web.stanford.edu/~hastie/glmnet/glmnet\_alpha.html](https://web.stanford.edu/~hastie/glmnet/glmnet_alpha.html)

[²](#15_Chapter07.xhtml#ch7-fn2)[https://web.stanford.edu/~hastie/Papers/glmnet.pdf](https://web.stanford.edu/~hastie/Papers/glmnet.pdf)

 

 
| 

## Ensemble Methods

 || 

## 8

 |
| --- | --- |

*All know the way; few actually walk it.*

**—Bodhidharma**

LEARNING OBJECTIVES

After reading this chapter, you would be able to:

• Learn the mathematics behind ensemble methods.

• Learn to develop ensemble techniques such as Random Forest, Gradient boosting machine and Xtreme boosting.

• Learn to generate variable importance (feature importance) using ensemble methods.

• Understand hyper-parameters in machine learning algorithms and how to search for optimal hyper-parameters.

### 8.1 | Overview

Ensemble methods are learning algorithms that take a set of estimators or classifiers (models) and classify new data points using strategy such as majority vote. Majority voting could be based on simply counting the vote from each classifier or it could be weighted based on accuracy of classifiers. Ensemble methods are also used for regression problems, where the prediction of new data is simple average or weighted average of all predictions from the set of regression models as shown in **[Figure 8.1](#16_Chapter08.xhtml#fig8.1).**

In **[Figure 8.1](#16_Chapter08.xhtml#fig8.1)**, *K* and *N* are the number of features and records in the original set, while *k* and *n* are the number of features and records in the sampled set. The point to note is that multiple datasets (using different features and records) will be needed to build multiple classifiers (models). But in practice, there is always one training set available. We may have to adopt certain strategies which provide different subsets of training sets (views) to the learning algorithm.

**1.** Strategies such as bootstrap sampling (random samples with replacement of the training data) may be used to create multiple subsets of the training set. Bootstrapping with ‘random subspace method’ is used in the random selection of a subset of features as well. This idea of bootstrapping along with random subspace method was the genesis of the Random Forest algorithm and distinguishes it from the earlier bagging algorithms (which were pruned decision tree classifiers without applying random subspace method).

**2.** The other strategy which may be adopted is by assigning weights to the observations of the training data and providing observations with higher weights to the learning algorithm. In general, boosting algorithms rely on this strategy for the learning process.

![](images/page286-01.png)

Creating different subset views of training data is analogous to creating a different experience for the learning algorithm from which it may learn useful patterns. This notion of creating different subsets of training data ties back to the formal definition of machine learning given in [Chapter 7](#15_Chapter07.xhtml). In this chapter, we will primarily look at Random Forest, adaptive boosting, and xtreme boosting. However, we will also give some insights into the other bagging and boosting algorithms which can be implemented using R.

### 8.2 | Random Forest

Random Forest (often called Bagging) is one of the popular ensemble methods in which several trees (thus the name ‘forest’) are developed using different sampling strategies (Breiman, 1996, 2001).[¹](#16_Chapter08.xhtml#ch8-r-fn1) One of the most frequently used sampling strategies is **Bootstrap Aggregating** (or **Bagging).** Bagging is a random sampling with replacement. Using samples of data and features, Random Forest develops several classification models (usually trees). In case of continuous outcome variable (regression problem), the prediction from various base learners is averaged. In case of discrete outcome variable (classification problem), a new observation is classified by using majority voting. In his seminal work, Breiman (1994, 2001) claimed that Random Forest (RF) resulted in substantial gain in accuracy for both regression and classification problems on real and simulated datasets. Mathematically, RF is a collection of learners {*L*[*k*](*X*, *T*[*k*]}*, k* = 1, 2,…, *N*}. *X*is the set of input and *T*[*k*] is the independent and identically distributed samples on which the learner (or classifier) *L*[*k*](*X, T*[*k*]) is developed.

Random Forests are developed using the following steps (Kumar, 2017):

**1.** Assume that the training data has *N* observations. One needs to generate several samples of size *M* (*M* ≤ *N*) with replacement (Bootstrap Aggregating or Bagging). Let the number of samples based on sampling of the training dataset be *K*, that is, number of trees is *K*.

**2.** If the data has *n* predictors, sample *m* predictors (*m* < *n*). This step is used to make the trees independent.

**3.** Develop trees for each of the samples generated in Step 1 using the sample of predictors from Step 2. Classification trees are developed if the outcome variable is discrete and regression trees are developed when the outcome variable is continuous.

**4.** Repeat Step 3 for all samples generated in Step 1.

**5.** Predict the outcome variable value using majority voting in case of classification and average of prediction for continuous outcome variable.

![](images/page287-01.png)

**[Figure 8.2](#16_Chapter08.xhtml#fig8.2)** shows the structure of the Random Forest model development. The purpose of using different samples of features while developing a base model is to make the base models independent of each other.

#### 8.2.1 Out-of-Bag Data

One advantage of using the Bootstrap Aggregating procedure is that it provides a validation data called **Out-of-Bag (OOB)** data. In a base model, at least (*N-M*) records will not be part of model building; the records that are not part of the base model are called out-of-bag data. Consider a dataset with 20 records labelled 1, 2 onwards, till 20. Let bootstrap samples of size 10 be generated from these 20 records. A few possible samples are shown in **[Table 8.1](#16_Chapter08.xhtml#tab8.1).**

In **[Table 8.1](#16_Chapter08.xhtml#tab8.1)**, sample 1 consists of records {7, 8, 9, 6, 2, 3, 3, 4, 17, 19}, that is, records {1, 5, 10, 11, 12, 13, 14, 15, 16, 18, 20} are not part of sample 1; these records are out-of-bag for sample 1. Record 16 is not present in any of the samples, thus it can be used as a test data for all five base models generated using the samples listed in **[Table 8.1](#16_Chapter08.xhtml#tab8.1).** All such cases that are not part of the training data of a tree can be used as a validation data and such cases are called Out-Of-Bag data. A Random Forest model is validated using **Out-of-Bag (OOB)** data as validation data, and thus no separate validation data is required. Approximately 33% of the data is not part of building the base model in RF. However, many data scientists still create separate validation data.

#### 8.2.2 Predicting Net Promoter Score (NPS) Using Random Forest

We will discuss the Random Forest approach using an example of Net Promoter Score (NPS) prediction. NPS, which can be used as a leading indicator to access customer loyalty, is based on a single question – How likely is it that you would recommend our company or product/service to a friend or colleague?

Customers score their responses on a 0-to-10 (11-point) scale. Highly satisfied customers are likely to provide a score of either 9 or 10, and are called promoters; passive customers provide a score of 7 or 8, while those who respond with a score of 6 or below are detractors.

![](images/page287-02.png)

Subtracting the percentage of detractors from the percentage of promoters yields a single figure – the company’s NPS. Detractors are likely to spread negative sentiments about the organization among their friends and colleagues.

#### Example – Random Forest Model Development

All India Electronics (AIE) is a leading manufacturer of electronic gadgets which operates in the B2B segment. It provides preventive as well as corrective maintenance services for the equipment it sells its customers. Customer satisfaction is key to business growth and the management of AIE would like to improve its current NPS score, which stands at 49%.

Over a period, AIE carried out feedback surveys and obtained NPS rating from its customers. The device\_feedback.csv contains information about customer demographic, customer interaction to resolve any issue faced by them over a period of one year, and finally the rating given by these customers. This feedback was taken as a part of contract renewal for preventive or corrective maintenance service. **[Table 8.2](#16_Chapter08.xhtml#tab8.2)** shows the features available in the dataset in device\_feedback.csv.

Note that most of the features were derived using raw data which mostly consisted of Date columns.

**TABLE 8.2** | Feature list

| Data Code || Description |
| --- | --- |
| Customer ID || Unique customer ID which has been randomized |
| --- | --- |
| Device || Equipment for which the service was taken |
| contract\_renewed || Is it a new contract or a renewal |
| new\_or\_renew || Whether contract was renewed or not |
| Age in Yrs || Number of years for which this customer is with All India Electronic LLP |
| Count of sr after pm || Number of service requests raised after preventive maintenance was carried out |
| days\_to\_report\_first\_issue\_after\_contract\_renewal || Number of days taken to report the first issue after contract renewal |
| days\_to\_resolve\_first\_issue\_after\_contract\_renewal || Number of days taken to resolve the first issue after contract renewal |
| days\_to\_resolve\_last\_issue\_before\_contract\_expiry || Number of days taken to resolve the last issue before contract expiry |
| duration\_between\_report-ed\_issues || Gap between the last issue raised before contract expiry and the first issue raised after contract renewal |
| Zone || Zone to which the customer belongs |
| Location || City of the customer |
| papers\_for\_the\_new\_contracts\_received || Whether the contract papers were received by the customer at the time of feedback |
| inclusions\_exclusions\_explained || Whether inclusion and exclusion terms of the contract were explained during contract renewal |
| services\_in\_contract\_explained || Whether service terms of the contract were explained during contract renewal |
| number\_of\_issue\_reported || Number of issues reported in the last one year |
| service\_agency || Whether the service was being provided by franchise or directly by company |
| rate\_recommend\_products\_services || The rating given by the customer on a scale of 0–10 |
| nps\_classification || NPS class derived based on the rating |
| merged\_nps\_classification || Detractor and passive merged as Detractors. Promoter is kept separate. This is not being used. |

The list of derived features are as follows:

**1.** days\_to\_report\_first\_issue\_after\_contract\_renewal: *(first\_issue\_report\_date\_after\_ contractrenewal) - (contract\_start\_date)*

**2.** days\_to\_resolve\_first\_issue\_after\_contract\_renewal: *(first\_issue\_closed\_date\_after\_contractrenewal) - (first\_issue\_report\_date\_after\_contract\_renewal)*

**3.** days\_to\_resolve\_last\_issue\_before\_contract\_expiry: *(last\_issue\_closed\_date\_before\_contractexpiry) - (last\_issue\_report\_date\_before\_contract\_expiry)*

**4.** duration\_between\_reported\_issues: *(first\_issue\_report\_date\_after\_contract\_renewal) - (last\_issue\_report\_date\_before\_contract\_expiry)*

**5.** number\_of\_issue\_reported:number\_of\_issue\_reported = ZERO if (days\_to\_report\_first\_issue\_after\_contract\_renewal) == 0 & (last\_issue\_report\_date\_before\_contract\_expiry) - (first\_issue\_report\_date\_after\_contract\_renewal) ≥ 365.0

**6.** number\_of\_issue\_reported = ONE if (last\_issue\_report\_date\_before\_contract\_expiry) - (first\_issue\_report\_date\_after\_contract\_renewal) ≤ 0.0 & (contract\_start\_date) - (first\_issue\_report\_date\_after\_contract\_renewal) == 0.

**7.** number\_of\_issue\_reported = ONE if (contract\_start\_date) - (first\_issue\_report\_date\_after\_contract\_renewal) ≤ 0.0 & (last\_issue\_report\_date\_before\_contract\_expiry) - (first\_issue\_report\_date\_after\_contract\_renewal) == 0.0

**8.** number\_of\_issue\_reported = MORE THAN ONE if None of the above condition is satisfied

Feature engineering plays a key role in any machine learning model and so is the case with the Random Forest model too. All the above derived features were duly validated by the business before proceeding with further analysis. We will build an NPS classification model, that is, trying to classify Detractors, Passives, and Promoters, using the RF algorithm.

### 8.3 | Class Imbalance Problem

The device\_feedback.csv has 1,889 observations and 20 features. The outcome variable, that is, NPS\_CLASSIFICATION has following labels:

**1.** Promoter 1,009

**2.** Passive 819

**3.** Detractor 77

This dataset has 53% Promoters, 43% Passives, and only 4% Detractors. From a classification problem perspective, this is a typical case of a class imbalanced data. A dataset is said to be class imbalanced if the proportion of cases (in the outcome feature) is biased towards one of the classes. In an ideal scenario, we may say that a data does have class imbalance issue when the proportion of cases in all the classes is the same (in a binary classification case, this will be 50% for both classes). Such a situation is difficult to find in a real-life use case as most classification problems will have a class imbalance to certain extent. However, the classification problem becomes difficult to solve if the proportion of cases is highly biased (say, 90%–10% scenario in a binary classification problem).

In this data, we observe that the outcome feature, NPS\_CLASSIFICATION, has only 4% of the customers belonging to the Detractor class. Thus, we can mark this as a class imbalance problem. Traditional models may not yield good results in classifying Detractors since only 4% of the records are Detractors. In other words, there is not enough learning opportunity in the data to classify Detractors correctly.

A simple **log transformation of outcome variable**, at times, may help reduce the skewness in continuous outcome variable and help improve the model performance. In extreme cases, the sampling strategies like SMOTER (Smote for Regression) can also be applied to handle extreme numeric values in regression problem.

#### 8.3.1 | Dealing with Class Imbalance – Regrouping Classes

We may have to remove the class imbalance issue before applying any learning algorithm. One of the ways to deal with class imbalance in this data is to merge the classes. The MERGED\_NPS\_CLASSIFICATION column has been created by re-grouping Passive to Detractors. The groups Passive and Detractors are merged for two reasons:

**1.** The model can now be developed to solve for binary classification problem (Promoters vs. Detractors). We will label non-promoters as detractors in binary class classification.

**2.** The data with respect to outcome variable is not showing class imbalance issue.

Now, if we solve this as a binary classification problem, we may get a reasonable correct classification of Detractors and Promoters. Note that such re-grouping should be validated with business.

**Sampling strategies** are important considerations while dealing with a class imbalance issue in a classification problem dataset. However, in regression problem as well, the distribution of continuous outcome variable may be skewed and may lead to high mean squared error.

#### 8.3.2 | Dealing with Class Imbalance – Sampling Strategy

The other way to deal with class imbalance issue is to apply **sampling strategies**. Two commonly used sampling strategies are up-sample and down-sample. Let us understand up-sampling with respect to device\_feedback data. The total count of labels in NPS\_CLASSIFICATION is as follows:

**1.** Promoter: 1,009

**2.** Passive: 819

**3.** Detractor: 77

Let us define the nomenclature ‘majority class’ and ‘minority class’. The majority class refers to the label which has maximum class frequency, that is, Promoter class in this dataset. The minority class refers to the label which has minimum number of cases, that is, Detractor class in this dataset.

**1.** Up-sample strategy is applied on the data in such a way that the number of cases, that is, class frequencies for all the labels which do not belong to majority class, becomes equal to the majority class. One of the ways to achieve this is by performing random sampling with replacement for all the cases which do not belong to the majority class. If we apply up-sample strategy in device\_feedback data, we will have the total count of labels in NPS\_CLASSIFICATION as follows:

– Promoter: 1,009

– Passive: 1,009

– Detractor: 1,009

Up-sampling strategy balances out the class distribution, but since this strategy just duplicates the data (by repetition), it does not provide additional information to improve model performance. Note that the percentage by which to up-sample the other classes need not necessarily be of the magnitude which makes the number of cases equal for all the classes. We can specify the percentage by which to up-sample while using the methods from h2o.

**2.** Down-sample strategy is applied on the data in such a way that the number of cases, that is, class frequencies for all the labels which do not belong to minority class becomes equal to the minority class. One of the ways to achieve this is by performing random sampling with replacement or without replacement for all the cases which do not belong to the minority class. If we apply down-sample strategy in device feedback data, we will have the total count of labels in NPS\_CLASSIFI-CATION as follows:

– Promoter: 77

– Passive: 77

– Detractor: 77

**A simple log transformation of outcome variable**, at times, may help reduce the skewness in continuous outcome variable and help improve the model performance. In extreme cases, the sampling strategies like SMOTER (Smote for Regression) can also be applied to handle extreme numeric values in regression problem.

**UBL package in R** implements SmoteR sampling method (Torgo et al. (2013) using SmoteRegress(). The package also has an implementation of Synthetic Minority Over-Sampling Technique for Regression with Gaussian Noise (SMOGN) through SmognRegress().

Though this strategy reduces the overall number of cases in the data, it removes class imbalance issue and creates a heterogeneous mix from which algorithms can learn useful pattern. Note that the percentage by which to down-sample the other classes need not necessarily be of the magnitude which makes the number of cases equal for all classes. We can specify the percentage by which to down-sample while using the methods from h2o.

**3.** Synthetic Minority Over-sampling Technique (SMOTE) is another strategy suggested by Chawla et al. (2002). This strategy synthesizes new examples for each minority case as follows:

○ In the minority class, find *k* nearest neighbour to a given minority case (say A). Chawla et al. (2002) suggested finding five nearest neighbours to a given case.

○ Draw a line segment which joins any/all of the *k* minority class nearest neighbours to a given minority case (A).

○ Depending on the number of cases to be over-sampled, select, at random, any/all of the *k* neighbours. Say, if amount of over-sampling needed is 300%, then three nearest neighbours from amongst the five neighbours to minority case (A), will be chosen and three random samples will be generated along the three line segments. The samples will be generated as follows:

■ Take the difference between the feature vector (e.g., case A) and one of the randomly selected nearest neighbours’ feature vector (say B).

■ Multiply the difference by a random number between 0 and 1 (Xu et al. 2017). This will result in a new feature vector (say C).

■ Add the new vector C to the feature vector (e.g., case A). This will result in selection of a random case along the line segment joining A and B.

■ Repeat the above steps along the other two line segments to generate two more samples.

SMOTE() method from DMwR package in R implements synthetic sampling of minority class by setting the parameter perc.over. SMOTE() method also supports under sample the majority class by setting the parameter perc.under.

○ perc.over: This parameter by default is set to 200. For each case in the original dataset belonging to the minority class, 200/100, that is, two new examples for each case will be created (Anon, 2018; Torgo, 2010).

○ perc.under: This proportion is calculated with respect to the number of newly generated minority class records. If 200 new records of minority class were generated, a value of perc.under of 200 will randomly select 200 cases belonging to the majority classes. This parameter by default is set to 200 (Anon, 2018; Torgo, 2010).

The method SMOTE () can also be called through trainControl() method of the caret package. More details on SMOTE can be found by ?DMwR::SMOTE.

**4.** Random Over-Sampling Examples (ROSE), proposed by Menardi and Torelli (2014), is yet another sampling technique which removes class imbalance. ROSE as a method is implemented through ROSE package in R and can be used to remove class imbalance in a binary classification problem. To understand ROSE sampling, let us take a generic training dataset *T*[*n*] with *n* observations. Let (*x*[*i*]*,y*[*i*]) denote an observation, where *X* denotes feature vector and *Y*[*i*] belongs to {*C*[0], *C*[1]}, that is, binary class. Let the number of cases in class *C*[*j*], *j* = 0,1 be denoted by *n*[*j*] < *n*. The new sample is generated as follows:

○ Select a class label, *y*\* = *C*[*j*] with probability *P*[*j*] = 0.5. *P*[*j*] = 0.5 ensures that approximately same number of cases belong to th e two classes.

○ Select an observation *(x*[*i*]*, y*[*i*]), with probability ![](images/pageIn_ch8-01.png), from the training set *T*[*n*] such that *y*[*i*]*.* belongs to the class label *y*\*.

○ Generate a new observation *x*\*, with a mean of ![](images/pageIn_ch8-02.png)and variance of *x*[*i*] The mean and variance, for the various features ***x***, is computed with respect to the class labels {*C*[0], *C*[1]} separately.

Essentially, in the above steps, we are randomly picking an observation from the training set and generating a new sample (*x\*, y\**) in its neighbourhood. The shape of the neighbourhood is determined by the mean of the feature and the width is determined by the variance of the feature. It can be easily shown that the generation of new examples according to ROSE corresponds to the generation of data from the kernel density estimate *f*(*x|C*[*j*]) (Menardi and Torelli, 2014). ROSE can be used to generate new samples for categorical features as well. Basically, if one of the features is categorical in (*x*[*i*], *y*[*i*]), the new sample (*x\*, y\**) will have the same value for the categorical feature as of the selected observation *(x*[*i*]*, y*[*i*]).

Unlike SMOTE, which generates a sample by randomly choosing points that sit on the line segment joining the minority case and its nearest neighbours, ROSE uses simulated bootstrap approach (Efron and Tibshirani, 1993) to generate new samples. The method ROSE() can also be called through trainControl() method of the caret package. More details on ROSE can be found by ?ROSE::ROSE.

Note that in subsequent sections, we will demonstrate the use of up-sample and down-sample strategy using h2o package. We encourage the reader to implement SMOTE and ROSE sampling, on the device feedback data, using the caret package.

**UBL package in R** implements SmoteR sampling method (Torgo et al. (2013) using SmoteRegress(). The package also has an implementation of Synthetic Minority Over-Sampling Technique for Regression with Gaussian Noise (SMOGN) through SmognRegress().

### 8.4 | Random Forest Using h2o Package

The model building steps for ensemble model (bagging and boosting using h2o package) are as follows:

**1.** For hyper-parameter fine tuning, define a range of values. This range of values for a hyper-parameter is called as grid space. The hyper-parameters to be fine-tuned may be a subset of all the hyper-parameters for an algorithm.

**2.** Define the search criteria which, along with search strategy (random or Cartesian), will include the metric used to report the best combination of hyper-parameter values/best model.

**3.** Build the model and fine-tune the hyper-parameters using training data and validation/cross-validation data, respectively. Save the values of the hyper-parameters which report the best model.

**4.** Fix the learnt hyper-parameters and iterate through Steps 1 to 3 to see if there are more hyper-parameters to be fine-tuned.

**5.** Evaluate the performance on the test set and save the model for scoring cases in a deployment scenario.

We will use the state-of-the-art package, h2o, for building ensemble models. If the h2o package was installed earlier and there is a latest version available, then initialization of h2o package may give error due to version mismatch. In such a case, re-install the package before proceeding. Run the below two lines in console before proceeding further. Note that, we have we have reproduced the syntax and definitions as per the h2o website available at [https://www.h2o.ai/resources](https://www.h2o.ai/resources)/.

**1.** if (“package:h2o” %in% search()) { detach(“package:h2o”, unload=TRUE)}

**2.** if (“h2o” %in% rownames(installed.packages())) { remove.packages(“h2o”)}

![](images/page293-01.png)

The following code can be used to import data using h2o package:

![](images/page293-02.png)

Initialization of h2o may give error if the Java version is not supported or if your machine has a 32-bit version of Java. Update Java before proceeding further. Also, check if the R environment is pointing to the correct version of Java by typing in console.

\> Sys.getenv(“JAVA\_HOME”)

‘/Library/Java/JavaVirtualMachines/jdk1.7.0\_60.jdk/Contents/Home’

You can change the environment using console:

\>Sys.setenv(JAVA\_HOME = ‘/Library/Java/JavaVirtualMachines/jdk1.8.0\_101.jdk/Contents/Home’)

![](images/page294-01.png)

The information given by the h2o.init is useful to understand the parallel processing initiated by the h2o package:

**3.** Cluster can be thought of as a collection of interconnected computers wherein a node or a machine is a physical machine in the cluster. For an individual machine (personal laptop), the number of nodes and clusters is the same. h2o cluster total nodes: 1 signifies that we are running this program on an individual machine and the memory available (RAM) is 7.94 GB.

**4.** Processor/CPU/Core can be thought of as a physical device in a computer that makes computations. A modern laptop may have anywhere between 4 and 16 cores. We can see that the machine on which we are running the program has eight cores.

**5.** Given a cluster of *n* nodes, where each node has *c* number of CPUs, the number of models would be 2 \* *c*. So, in this machine we can build 16 models in parallel.

**[Table 8.3](#16_Chapter08.xhtml#tab8.3)** shows the snapshot of device\_feedback data.

![](images/page295-01.png)![](images/page295-02.png)

Let us get the descriptive statistics of the raw\_h2f by using the below code snippet. This is a preprocessed data and thus summary statistics may not show any issue with the data.

![](images/page295-03.png)![](images/page296-01.png)

#### 8.4.1 | Feature List in the Data

In this section, we will create a list of numeric and categorical features, and then create another list of all features which will be used for model building. **[Table 8.4](#16_Chapter08.xhtml#tab8.4)** shows the snapshot of filter\_h2f, created as part of the below code snippet.

The numeric features in the dataset are as follows:

![](images/page296-02.png)![](images/page297-01.png)![](images/page297-02.png)

The categorical features in the dataset are as follows:

![](images/page297-03.png)![](images/page298-01.png)

#### 8.4.2 | Model Using h2o

We can split the data into train and test set using h2o splitframe metho d. splitFrame creates subsets, which are always one more than the number specified in the parameter named ‘ratios’. Note that this does not give an exact split. h2o is designed to be efficient on big data context using a probabilistic splitting method rather than an exact split of train and test data.

For example, when specifying a split of c(0.70), h2o will produce a test/train split with an expected value of 0.70/0.30 rather than exactly 0.70/0.30. According to R-documentation, ‘On small datasets, the sizes of the resulting splits will deviate from the expected value more than on big data, where they will be very close to exact (E LeDell, 2020)’.

![](images/page298-02.png)

The dimensions of the train and test dataframe are as follows:

![](images/page299-01.png)

#### 8.4.3 | Random Forest with h2o Package

h2o package has randomForest method which can be directly called to build a Random Forest model. However, since there are hyper-parameters which need to be fine-tuned, we will build the Random Forest model using the grid method. This method will help us fine-tune the hyper-parameters of Random Forest. Note that the implementation of randomForest method in h2o has a subtle difference from the original Random Forest algorithm (Brieman, 2001). h2o’s Random Forest does not perform bootstrapping, as was proposed in original paper by Brieman (2001). For every tree, randomForest method samples observations at a rate of 0.632 (which is the expected value of unique rows in any bootstrapped sample). Moreover, parameters can be used to control the growth of the tree.

#### 8.4.4 | Random Subspace Selection

The parameters which control random feature selection are as follows *(Source:* docs.h2o.ai):

**1.** mtries – This parameter denotes the number of columns to be selected at random at each level of the tree. The valid values which can be passed to this parameter are: −2, −1, and any value ≥1 (Anon, 2016). In classification problems, the default value of −1 signifies the number of columns to be selected as square root of the number of predictors. In a regression problem, the default value of −1 signifies the number of columns to be selected as p/3, where p is the number of predictors. A value of −2 means selecting all the predictors. Any value greater than or equal to 1, signifies randomly selecting those many predictors.

**2.** col\_sample\_rate\_per\_tree – This parameter specifies the proportion of columns to be randomly selected (without replacement) for each tree. This takes any value between 0.0 and 1.0. The default value is 1 (selects all columns for each tree growth).

**3.** col\_sample\_rate\_change\_per\_level – This parameter works in conjunction with col\_sample\_rate\_per\_tree and is used to vary the proportion of columns to be randomly selected, as the depth of the tree increases. The value of this parameter can be between 0 and 2 (default is 1). For example, say the col\_sample\_rate\_change\_per\_level is set as 0.5, then

• level 1: col\_sample\_rate\_per\_tree

• level 2: col\_sample\_rate\_per\_tree \* 0.5

• level 3: col\_sample\_rate\_per\_tree \* 0.5∧2

• level 4: col\_sample\_rate\_per\_tree \* 0.5∧3 so on.

#### 8.4.5 | Class Imbalance

**1.** balance\_classes – This parameter is used to remove the class imbalance in the data. The default value is FALSE. If it is set to TRUE, then it uses up-sampling to remove the class imbalance.

**2.** class\_sampling\_factors – This parameter can be used along with balance\_classes (set to TRUE) to specify how much to up-sample or down-sample the data. It requires us to pass the upsampling or downsampling ratios per class lexicographic order. It is an optional parameter and if we do not pass this parameter, then sampling factors are automatically computed during model training.

**3.** max\_after\_balance\_size – With balance\_classes set to TRUE, this parameter is used to control the relative size of the training data. The value of 1.0 will mean that, after removing class imbalance, set the size of the training data to be the same as the original training set.

#### 8.4.6 | Random Row Selection (Bootstrap)

The following methods are used for sampling records in RF (*Source:* docs.h2o.ai).

**1.** sample\_rate – This parameter specifies the proportion of rows to be randomly selected (without replacement) for each tree. This parameter takes a value between 0.0 and 1.0. The default value is 0.6320000291. A higher value for this parameter may improve training accuracy. This parameter along with col\_sample\_rate\_per\_tree may be used to fine-tune the model.

**2.** sample\_rate\_per\_class – This parameter is optional and is a substitute for sample\_rate (either one can be used). For each tree in the ensemble model, this parameter can be used to control the proportion of rows, which needs to be sampled without replacement for each class. The parameter expects a list to be passed with the value between 0 and 1 (relative fraction of rows). This may be used to remove the class imbalance without using the parameters described in [Section 8.4.5](#16_Chapter08.xhtml#sec8.4.5).

While using sample\_rate\_per\_class parameter, balance\_classes and class\_sampling\_factors may be ignored. In the NPS prediction case, sample\_rate\_per\_class seems to give a better result than using any combination of balance\_classes and class\_sampling\_factors parameters.

#### 8.4.7 | Control Growth

Brieman (2001) suggested that the classifier, that is, decision trees in random forest need not be pruned. However, from implementation perspective, packages give options to limit the growth of the trees. The below parameters can be used to limit the tree growth.

**1.** min\_split\_improvement – This parameter can be used to reduce overfitting by restricting the growth of the tree. The value of this parameter signifies the minimum change in the squared error to split a node into two. The default value is set to 10^(−5). The optimal values for this parameter can be in the range of 10^(−10) to 10^(−3).

**2.** max\_depth – This parameter is used for reduce overfitting. It is used to control the depth to which a tree can grow. A higher value for this parameter will lead to a more complex tree. If the value is set to 0, it will mean no limit to grow the tree (highly complex tree). The default is set to 20.

**3.** min\_rows – This parameter specifies the minimum number of observations to be present in the leaf node. The default is set to 1 which may lead to overfitting issues.

#### 8.4.8 | Random Forest (h2o) – Hyper-parameters

Let us create a list and provide the values for each of the hyper-parameters:

![](images/page300-01.png)

#### 8.4.9 | Random Forest (h2o) – Search Criteria

In previous section, we created a list of values, hyper\_params, for the three parameters from which we want to find the best combination of values. The values in hyper\_params can be searched by adopting the strategy = Cartesian or strategy = RandomDiscrete.

**1.** Specifying search\_criteria = list(strategy = “Cartesian”) will apply Cartesian strategy.

Cartesian will search for all combinations of hyper-parameters. However, RandomDiscrete may be needed in case of infrastructure limitation or if the number of combinations of hyper-parameters is too large. In case of RandomDiscrete strategy, there are three ways of randomly searching the space and specifying when to stop the search:

**2.** max number of models

– search\_criteria = list(strategy = “RandomDiscrete”, max\_runtime\_secs = 600, max\_models = 100, stopping\_metric = “AUTO”, stopping\_tolerance = 0.00001, stopping\_rounds = 5, seed = 123456)

**3.** max time

– search\_criteria = list(strategy = “RandomDiscrete”, max\_models = 42, max\_ runtime\_secs = 28800)

**4.** metric-based early stopping (e.g., stop if AUC has not improved by 0.0001 over the five best models).

– search\_criteria = list(strategy = “RandomDiscrete”, stopping\_metric = “AUC”, stopping\_tolerance = 0.00001, stopping\_rounds = 5)

We can apply early stopping once the validation logloss does not improve by at least 0.01% for five consecutive scoring events.

![](images/page301-01.png)

#### 8.4.10 | Random Forest – Grid Search

While using the caret package in [Chapters 6](#14_Chapter06.xhtml) and [7](#15_Chapter07.xhtml), we discussed expand.grid() method from the base package. The expand.grid() method helps create a data frame from all combinations of the supplied vectors, that is, hyper\_params. The analogous method in h2o is ‘grid’. We will use the grid method of h2o and pass model parameters, search criteria, and list of hyper-parameters. Also pass the train and validate dataframe.

By default, the balance classes parameter of grid method up-samples the cases. To apply down-sampling, let us calculate the proportions by which to down-sample. **[Table 8.5](#16_Chapter08.xhtml#tab8.5)** shows the number of cases in NPS\_CLASSIFICATION in train h2f.

**TABLE 8.5** | The number of cases in NPS\_CLASSIFICATION in train\_h2f

| NPS\_CLASSIFICATION || Count |
| --- | --- |
| Detractor || 59 |
| --- | --- |
| Passive || 573 |
| Promoter || 709 |

In order to down-sample and make observations proportional to Detractor class:

**1.** Down-sample the Passive by 59/573 = 0.102 (approx.)

**2.** Down-sample the Promoter by 59/709 = 0.083 (approx.)

Thus class\_sampling\_factors in grid method may be set as class\_sampling\_factors = *c*(1.0,0.102,0.083). The numbers are written according to the lexical order of the classes.

The other option is to set sample\_rate\_per\_class in the grid method as:

sample\_rate\_per\_class = *c*(1.0,0.102,0.083). The numbers are written according to the lexical order of the classes.

While trying for the above two options for the multiclass classification problem, we found that sample\_rate\_per\_class gives a better outcome compared to using class\_sampling\_factors.

Models with different combinations of hyper-parameters will be validated on the validation\_frame and/or on cross-validation frame (nfolds) using the applicable metrics.

![](images/page302-01.png)

h2o.grid also has parallelism as a parameter, which can be used to define parallel processing while model training.

**1.** A value of 1 means sequential building and is the default for this parameter.

**2.** A value of 0 means adaptive parallelism, that is, the h2o package will decide how to utilize parallel processing.

**3.** A value greater than 1 will mean to build those many models in parallel.

![](images/page303-01.png)

We will use parallelism while building gbm and xgboost model. Note that the grid method also has parameters such as calibrate\_model and calibration\_frame. These are used to improve the performance with respect to probability estimation (platt scaling) of the ensemble models (randomforest, gbm, xgboost). However, currently it works in binary classification problem only.

#### 8.4.11 | Model Diagnostics

In this section, we will discuss model diagnostics. We can sort the model using one of the following metrics:

r2, mean\_per\_class\_accuracy, max\_per\_class\_error, err, total\_rows, rmse, accuracy, err\_count, logloss, mse, mean\_per\_class\_error

For multiclass classification, logloss is a reliable metric to evaluate the performance of the model. Logloss evaluates how close a model’s predicted values (estimated probability) are to the actual values.

In other words, logloss tries to measure if the model tends to assign a high predicted probability, say 0.90 for the positive class, or does it show a poor ability to recognize the positive class and assign a lower predicted probability, say 0.55?

Logloss can take any value greater than 0. A value of 0 implies that the model has correctly assigned a probability of 0% or 100%. **[Table 8.6](#16_Chapter08.xhtml#tab8.6)** shows the sorted table in increasing order of logloss.

![](images/page303-02.png)

Let us select the first model from **[Table 8.6](#16_Chapter08.xhtml#tab8.6)** for further evaluation.

![](images/page303-03.png)

We can look at the training metrics of rf\_model object by using the below code snippet.

![](images/page303-04.png)![](images/page304-01.png)

Note that the Detractor class reports error as NA as the confusion metrics is generated on the OOB observation. We included all the Detractors while generating each of the trees and thus there is no OOB observation for Detractor class. This was done where we specified sample rate per class = *c*(1.0, 0.102, 0.083).

The hit ratio is a table representing the ratio of number of times the prediction was correct out of the total number of predictions.

**1.** *K* = 1 suggests that if we give the model only one chance to estimate the correct class for each of the observations, the model is right 64% of the time. This, in a way, is as good as model accuracy.

**2.** *K* = 2 suggests that if we give the model only two chances to estimate the correct class for each of the observations, the model is right 91% of the time.

**3.** *K* = 3 suggests that if we give model only three chances to estimate the correct class for each of the observations, the model is right 100% of the time (of course, it should be when the number of classes are only three).

We can look at the cross-validation metrics in a similar way:

![](images/page304-02.png)![](images/page305-01.png)

#### 8.4.12 | Model Prediction

Let us use the model for prediction on the test set **([Table 8.7](#16_Chapter08.xhtml#tab8.7)).**

![](images/page305-02.png)![](images/page306-01.png)

Let us see the performance of the model on the test frame.

![](images/page306-02.png)

The objective for building the NPS model is to identify Detractors amongst the customers. With an error of 0.22, the model seems to be doing reasonably well in predicting Detractors correctly. We can build the final model with the set of fine-tuned parameters and using the full dataset, that is, filter\_h2f.

![](images/page306-03.png)![](images/page307-01.png)

Accuracy of the model is 65%.

#### 8.4.13 | Save the model

The model can now be saved with the set of fine-tuned parameters.

![](images/page307-02.png)

After creating a new instance of h2o, this model can be called to score a new customer. Assuming that the test\_h2f is a new set of customers, we can use the saved model to predict the class of these new customers.

![](images/page308-01.png)

### 8.5 | Gradient Boosted Machine – Regression

In this section, we will discuss gradient boosting for regression. To understand the underlying concept of GBM, let us understand the generic framework of boosting with a regression problem.

Let *X,Y =* (*x*[1]*, y*[1]), (*x*[2], *y*[2]), (*x*[3], *y*[3])…(*x*[*m*]*, y*[*m*]) represent a dataset with *m* elements. Let us define the objective to fit a model *f*(*x*) so as to minimize the squared loss. Assume we already have pre-built regression model *f*(*x*) but it is lagging in estimating the outcome (*Y*). With the constraints involved in improvising the existing model *f*(*x*), the task is to add another model *h*(*x*) to the existing model *f*(*x*)) in the hope that it will estimate the *Y* exactly, that is,

![](images/page309-01.png)

The above set of [Eq. (8.1)](#16_Chapter08.xhtml#eq8.1) can be written as follows:

![](images/page309-02.png)

Though we may not be able to build a model which exactly fits the data, we can build a model *h*(*x*) which approximately fits the residual, that is, ![](images/pageIn_ch8-03.png).

*y*[*i*] − *f* (*x*[*i*]) is the residual, and the role of the new model *h*(*x*) is to compensate for the shortcomings of the existing model *f*(*x*). If the new model, *f*(*x*) + *h*(*x*) is still lagging, we can add another model to compensate for the shortcoming. This is the general idea behind the boosting framework.

#### 8.5.1 | Theory behind GBM

Gradient boosting derives its name from ‘Gradient Descent’ + ‘Boosting’. Let us understand how Gradient Descent works in this section. From [Chapter 7](#15_Chapter07.xhtml), we can recollect that the generic Gradient Descent takes the form of [Eq. (8.3)](#16_Chapter08.xhtml#eq8.3).

![](images/page309-03.png)

Unlike the traditional optimization problem where parameters *θ* can be easily learnt using gradient of the loss function, in the tree-based learning, the learning (of course using gradient) of the tree structure will be done using additive strategy.

In the boosting framework, the objective is to fit the model to the data *X, Y* so as to minimize the squared loss. So, we can write the objective in terms of loss function as in [Eq. (8.4)](#16_Chapter08.xhtml#eq8.4).

![](images/page309-04.png)

We will want to minimize ![](images/pageIn_ch8-04.png)by adjusting *f*(*x*). Thus *f*(*x*) can be treated as a parameter and taking derivative with respect to *f*(*x*) will result in the following:

![](images/page309-05.png)

Using above [Eq. (8.5)](#16_Chapter08.xhtml#eq8.5), the residual can be written as negative of gradient as shown in [Eq. (8.6)](#16_Chapter08.xhtml#eq8.6).

![](images/page309-06.png)

Thus, the boosting model update can be written in terms of gradient as follows:

![](images/page309-07.png)

Comparing [Eq. (8.3)](#16_Chapter08.xhtml#eq8.3) with [Eq. (8.7)](#16_Chapter08.xhtml#eq8.7), we can conclude that update to a model can happen with Gradient Descent where *α* is set to 1. The *α* value is the learning rate which also can be finetuned. Thus, in Gradient Boosting, the actual model is built using Gradient Descent wherein:

**1.** Fitting *h*(*x*) to residual is equivalent to fitting *h*(*x*) to negative gradient.

**2.** Updating *f*(*x*) based on residual is equivalent to updating *f*(*x*) based on negative gradient.

So, in general, we can write the steps on Gradient Boosting for regression as:

• Start with initial ![](images/pageIn_ch8-05.png)

– iterate until convergence:

• calculate the negative gradient − *g*(*x*[*i*]) = *y*[*i*] − *f*(*x*[*i*])

• fit a model *h*(*x*) to negative gradient − *g*(*x*[*i*])

• *f(x*) = *f*(*x*) *\+ α* \* *h(x*)

The final prediction is as per [Eq. (8.8)](#16_Chapter08.xhtml#eq8.8).

![](images/page310-01.png)

where *K* is the number of trees, *f*^(*k*) is the set of all possible trees (CART). In the above explanation, we kept *K* = 1 (learning only one tree structure) and thus dropped from the sub-script of *f*(*x*) and *h*(*x*).

One of the drawbacks of squared error loss function is that outliers are heavily penalized and thus the overall model performance may show high bias. However, the benefit of using gradient is that we can incorporate any other loss function like absolute loss or Huber loss, which are more robust to outliers. The key point to note is that the formulation of the objective function as shown in [Eq. (8.9)](#16_Chapter08.xhtml#eq8.9) remains intact, that is,

![](images/page310-02.png)

Ω(*f*^(*k*)) can be considered as a regularization parameter. We can consider learning rate *α* to be one of the regularization parameters, number of trees to grow, that is, *K* as another regularization parameter. There could be several regularization parameters which will control model overfitting and will be discussed while showing the implementation.

#### 8.5.2 | Stochastic Gradient Boosting

Based on the bagging method, Friedman (2001) proposed that at each iteration of the boosting model, the *h*(*x*) should be fit on a subsample of the training set drawn at random without replacement. This modification showed substantial improvement in Gradient Boosting’s accuracy and is known as Stochastic Gradient Boosting.

### 8.6 | Gradient Boosting Machine – Classification

Let us understand how GBM works in classification problem. In the NPS problem, we have to learn the classes y[i], that is, Detractor (*y*[1]), Passive (*y*[2]), Promoter (*y*[3]), that is, multiclass classification. We will have three scoring functions, that is, three models *f*[1], *f*[2], *f*[3] where *f*[1](*x*) assigns a score for Detractor, *f*[2](*x*) assigns a score for Passive, and *f*[3](*x*) assigns a score for Promoter. The scores will be used to calculate the probabilities using SoftMax function, [Eq. (8.10)](#16_Chapter08.xhtml#eq8.10).

![](images/page310-03.png)

The predicted class will be the one with the highest probability. The following steps are used to define the loss function for each data point:

Step 1: Based on the data, convert the label *y*[*i*] into a true probability distribution. *Y*[*c*](*x*[*i*]) For example, if the second observation in the data is Promoter, then. *Y*[1](*x*[2]) = 0,*Y*[2](*x*[2]) = 1,*Y*[3] (*x*[2]) = 0 We can write it as true probability *T*[*p2*] = (0,1,0).

Step 2: Calculate the predicted probability distribution *P*[*c*](*x*[*i*]), where *c* = 1, 2, 3 based on the current model *f*[1], *f*[2], *f*[3]. Assume that the calculated probability is *P*[1](*x*[2]) = 0.60, *P*[2](*x*[2]) = 0.25, *P*[3](*x*[2]) = 0.15. We can write it as calculated probability for the second observation as *C*[*p2*] = (0.6, 0.25, 0.15).

Step 3: Calculate the difference between the true probability distribution and the predicted probability distribution. Kullback–Leibler divergence[²](#16_Chapter08.xhtml#ch8-r-fn2) (KL-divergence) may be used to compute the difference.

KL divergence is a measure of how one probability distribution is different from another (Kullback and Leibler, 1951). A KL divergence value of zero will signify that the two distributions are same. The KL divergence from *C*[*pi*] to *T*[*pi*] can be denoted as *D*[*KL*] (*T*[*pi*] ‖*C*[*pi*]). KL divergence may also be called information gain achieved if is used instead of *T*[*pi*].

The objective of GBM for classification will be to minimize the overall KL divergence,[³](#16_Chapter08.xhtml#ch8-r-fn3) [Eq. (8.11)](#16_Chapter08.xhtml#eq8.11), so that the calculated probability can be used for correct classification.

![](images/page311-01.png)![](images/page311-02.png)

The objective in [Eq. (8.12)](#16_Chapter08.xhtml#eq8.12) can be achieved by adjusting the models, that is, *f*[1], *f*[2], *f*[3], and thus *f*[1], *f*[2], *f*[3], become the parameters to be optimized. ![](images/pageIn_ch8-06.png)is the regularization component in the GBM where *K* is the number of trees in each of the models *f*[*c*]*.*

#### 8.6.1 | GBM – Regression vs. Classification

The difference between GBM for regression and GBM for classification is that

**1.** Instead of one model *f*(*x*) in regression, classification has *f*[1](*x*), *f*[2](*x*), *f*[3](*x*) (in-device feedback data). So, there is a matrix of parameters to optimize

As shown in **[Table 8.9](#16_Chapter08.xhtml#tab8.9)**, there is a matrix of gradients to calculate.

![](images/page311-03.png)![](images/page311-04.png)![](images/page312-01.png)

So, in general, considering the device feedback data, we can write the steps on Gradient Boosting for classification as:

**2.** Start with initial model *f*[1](*x*), *f*[2](*x*), *f*[3](*x*):

– iterate until convergence:

• calculate the negative gradient for detractor -

![](images/page312-02.png)

• calculate the negative gradient for passive -

![](images/page312-03.png)

• calculate the negative gradient for promoter -

![](images/page312-04.png)

• fit a model *h*[1] to negative gradient - *g*[1] (*x*[*i*])

• fit a model *h*[2] to negative gradient - *g*[2](*x*[*i*])

• fit a model *h*[3] to negative gradient - *g*[3] (*x*[*i*])

• update *f*[1] (*x*[*i*]) = *f*[1](*x*[i]) + *α* \* *h*[1] (*x*[*i*])

• update *f*[2](*x*[i]) = *f*[2](*x*[i]) + *α* \* *h*[2](*x*[*i*])

• update *f*[3](*x*) *\= f*[3](*x*) + *α* \* *h*[3](*x*)

### 8.7 | Gradient Boosting Machine using h2o Package

h2o package has gbm method which can be directly called to build a GBM model. Like in randomForest model, here also we will use the grid method to fine-tune the hyper-parameters.

#### 8.7.1 | Random Subspace Selection

The parameters which control the gbm method are as follows (*Source:* docs.h2o.ai):

**1.** col\_sample\_rate - This parameter specifies the proportion of columns to be randomly selected (without replacement). This value of the parameter lies between 0.0 and 1.0. A higher value for this parameter may improve training accuracy. This option helps implement the Stochastic GBM, refer to ‘Stochastic Gradient Boosting’ (Friedman, 2002).

**2.** col\_sample\_rate\_per\_tree - This parameter specifies the proportion of columns to be randomly selected (without replacement). This takes a value between 0.0 and 1.0. The default value is 1 (select all columns for each tree growth).

**3.** col\_sample\_rate\_change\_per\_level - This parameter works in conjunction with col\_sample\_rate\_per\_tree and is used to vary the proportion of columns to be randomly selected, as the depth of the tree increases. The value of this parameter can be between 0 and 2 (default is 1). For example, say the col\_sample\_rate\_change\_per\_level is set as 0.5, then

• level 1: col\_sample\_rate\_per\_tree

• level 2: col\_sample\_rate\_per\_tree \* 0.5

• level 3: col\_sample\_rate\_per\_tree \* 0.5∧2

• level 4: col\_sample\_rate\_per\_tree \* 0.5∧3

#### 8.7.2 | Class Imbalance

**1.** balance\_classes - This parameter is used to remove the class imbalance in the data. The default value is FALSE. If it is set to TRUE, then it uses up-sampling to remove the class imbalance.

**2.** class\_sampling\_factors - This parameter can be used along with balance\_classes to specify how much to up-sample or down-sample the data. It requires us to pass the up-sampling or down-sampling ratios per class lexicographic order. It is an optional parameter and if we do not pass this parameter, then sampling factors are automatically computed during model training.

**3.** max\_after\_balance\_size - With balance\_classes set to TRUE, this parameter is used to control the relative size of the training data. It can take more value than or less than 1.0. The value of 1.0 will mean that, after removing class imbalance, set the size of the training data to be the same as the original training set.

#### 8.7.3 | Random Row Selection (Bootstrap)

**1.** sample\_rate - This parameter specifies the proportion of rows to be randomly selected (without replacement) for each tree. This parameter takes a value between 0.0 and 1.0 (default value is 1). A higher value for this parameter may improve training accuracy.

**2.** sample\_rate\_per\_class: This parameter is optional and is a substitute for sample\_rate (either one can be used). For each tree in the ensemble model, this parameter can be used to control the proportion of rows, which needs to be sampled without replacement for each class. The parameter expects a list to be passed with the value between 0 and 1 (relative fraction of rows). The range for this option is 0.0 to 1.0. Note that this method is sample without replacement (*Source:* docs.h20.ai).

While using sample\_rate\_per\_class parameter, balance\_classes and class\_sampling\_factors may be ignored. In the NPS prediction case, sample\_rate\_per\_class seems to give a better result than using any combination of balance\_classes and class\_sampling\_factors parameter.

#### 8.7.4 | Control Growth

Following are the parameters that can lead to controlling the growth of the tree (*Source:* docs.h2o.ai):

**1.** min\_split\_improvement – This parameter can be used to reduce overfitting by restricting the growth of the tree. The value of this parameter signifies the minimum change in the in squared error to split a node into two. The default value is set to 10^(−5). The optimal values for this parameter can be in the range of 10^(−10) to 10^(−3).

**2.** max\_depth – This is another parameter used to reduce overfitting. It is used to control the depth to which a tree can grow. A higher value for this parameter will lead to a more complex tree. If the value is set to zero mean no limit to grow the tree (highly complex tree). The default is set to 5.

**3.** min\_rows – This parameter specifies the minimum number of observations to be present in the leaf node. The default is set to 1 which may lead to overfitting issues.

**4.** learn\_rate – This parameter takes a value between 0 and 1 and is used to specify the learning rate.

**5.** learn\_rate\_annealing – This parameter works in conjunction with learn\_rate and is used to reduce the learn\_rate by a fixed factor after every tree. If there are *N* trees in the model, then GBM will start with learn\_rate and will end at learn\_ rate\*learn\_rate\_annealing∧N.

#### 8.7.5 | GBM – Create the Dataset

Let us create the dataset for training purposes.

![](images/page314-01.png)

The dimensions of the train, test and validate dataframe are as follows:

![](images/page314-02.png)

#### 8.7.6 | GBM (h2o) – Hyper-parameters

Let us create a grid space to search for the best hyper-parameter.

![](images/page314-03.png)

#### 8.7.7 | GBM (h2o) – Search Criteria

We define a search criterion using Cartesian or DiscreteRandom strategy. Let us implement the ‘RandomDiscrete’ search criteria.

![](images/page314-04.png)

#### 8.7.8 | GBM – Grid Search

We will use the grid method of h2o and pass the model parameters, search criteria, list of hyper-parameters. Models with different combinations of hyper-parameters will be validated on the validation\_frame and/or on cross-validation frame (nfolds) using the applicable metrics. We used 3 - cross-validation strategy for fine-tuning hyper-parameters in random-Forest. Let us use validation frame and parallel model building to fine-tune the gbm model.

![](images/page315-01.png)

In gbm method, the distribution parameter is by default set to AUTO which recognizes a regression or a classification task based on the response column. h2o.grid also has parallelism as a parameter, which can be used to define parallel processing while model training.

**1.** A value of 1 means sequential building and is the default for this parameter.

**2.** A value of 0 means adaptive parallelism, that is, the h2o package will decide how to utilize parallel processing.

**3.** A value greater than 1 will mean to build those many models in parallel.

#### 8.7.9 | Model Diagnostic

Sort the model using one of the metrics:

r2, mean\_per\_class\_accuracy, max\_per\_class\_error, err, total\_rows, rmse, accuracy, err\_count, logloss, mse, mean\_per\_class\_error

For a multiclass classification, logloss is a reliable metric to evaluate the performance of the model. Logloss evaluates proximity of a model’s predicted values (estimated probability) to the actual value.

For example, whether a model assigns a high predicted value like 0.90 for the positive class, or does it show a poor ability to predict the positive class and assign a lower predicted probability like 0.20 (Anon, 2016)?

Logloss can take any value greater than 0. A value of 0 implies that the model has correctly assigned a probability of 0% or 100%.

![](images/page316-01.png)![](images/page316-02.png)

Select the first model from **[Table 8.10](#16_Chapter08.xhtml#tab8.10)** for further evaluation.

![](images/page316-03.png)

We can look at the training metrics as below.

![](images/page316-04.png)![](images/page317-01.png)

The hit ratio is a table representing the number of times the prediction was correct out of the total number of predictions (Anon, 2016 © H2O.ai).

**1.** *K* = 1 suggests that if we give the model only one chance to estimate the correct class for each of the observations, the model is right 79% of the time. This in a way is as good as model accuracy.

**2.** *K* = 2 suggests that if we give the model only two chances to estimate the correct class for each of the observations, the model is right 96% of the time.

**3.** *K* = 3 suggests that if we give the model only three chances to estimate the correct class for each of the observations, the model is right 100% of the time (of course, it should be when the number of classes are only three).

We can look at the validation metrics in a similar way:

![](images/page317-02.png)

#### 8.7.10 | Model Prediction

Let us use the model for prediction on the test set. The result is shown in **[Table 8.11](#16_Chapter08.xhtml#tab8.11).**

![](images/page318-01.png)![](images/page318-02.png)

Let us see the performance of the model on the test frame.

![](images/page318-03.png)

#### 8.7.11 | GBM (h2o) – Result Discussion

Fine-tuning all the parameters at once may increase the time to fine-tune the model. Here are the steps performed to fine-tune the parameter. The values obtained in previous iterations were kept fixed while fine-tuning the parameters in subsequent iterations.

##### **Iteration 0:**

With a datasplit of (0.60,0.25,0.15), the model was built with default parameters but after adjusting sample\_rate\_per\_class = *c*(1.0,0.102,0.083). The performance of the model is reported in **[Table 8.12](#16_Chapter08.xhtml#tab8.12).**

![](images/page319-01.png)

##### **Iteration 1: Fine-tuning ntree, max\_depth and min\_rows**

**1.** ntree = seq(30,100,10)

**2.** max\_depth = seq(2,8,2)

**3.** min\_rows = *c*(1,5,10,15)

The values obtained for sample split of (0.60,0.25,0.15) was (50,6,5). Model performance is reported in **[Table 8.13](#16_Chapter08.xhtml#tab8.13).**

![](images/page319-02.png)

##### **Iteration 2:**

**1.** col\_sample\_rate = *c*(0.6,0.8,0.9,1.0)

**2.** min\_split\_improvement = c(0,0.01,0.001,0.0001,0.00001)

The value obtained for sample split of (0.60,0.25,0.15) was (1.0,0.00001), that is, default. Model performance is reported in **[Table 8.14](#16_Chapter08.xhtml#tab8.14).**

![](images/page319-03.png)

##### **Iteration 3:**

**1.** learn\_rate = *c*(0.1,0.3,0.5,1),

This parameter did not help improve the model. Model performance is reported in **[Table 8.15](#16_Chapter08.xhtml#tab8.15).**

![](images/page320-01.png)

##### **Iteration 4: Fine-tuning ntree, max\_depth and min\_rows**

**1.** ntrees = seq(44,54,2)

**2.** max\_depth = seq(2,8,2)

**3.** min\_rows = *c*(1,5,10,15)

The value obtained for sample split of (0.60,0.25,0.15) was (50,6,5). Model performance is reported in **[Table 8.16](#16_Chapter08.xhtml#tab8.16).**

![](images/page320-02.png)

It is observed from **[Table 8.13](#16_Chapter08.xhtml#tab8.13)** that ntrees, max\_depth and min\_rows lead to a significant improvement in logloss. Though there are other parameters of interest in gbm, they do not seem to improve the logloss in the NPS problem.

The objective in building the NPS model was to identify Detractors amongst the customers. With an error of 0.40, the model seems to be doing not as well as the Random Forest model in predicting Detractors correctly. However, with an overall accuracy of 71% (on test set), the GBM is better than the Random Forest model.

We can build the final model with the set of fine-tuned parameters and using the full dataset, that is, filter\_h2f.

#### 8.7.12 | Final GBM Model

The final model was built with the data split of (0.60,0.25,0.15) with model\_iter4 parameters which resulted in **[Table 8.16](#16_Chapter08.xhtml#tab8.16):**

![](images/page321-01.png)

Accuracy of the model is 82%.

#### 8.7.13 | Save the Model

The model can now be saved with the set of fine-tuned parameters.

![](images/page321-02.png)

After creating a new instance of h2o, this model can be called to score a new customer. Assuming that the test\_h2f is a new set of customers, we can use the saved model to predict the class of these new customers. Refer to [section 8.4.13](#16_Chapter08.xhtml#sec8.4.13) to understand the usage of the saved model in scoring new cases.

### 8.8 | XGBoost using h2o Package

XGBoost is another popular boosting technique which further builds on the Gradient Boosting Machine (GBM) framework and is one of the best GBM frameworks. The objective function for XGBoost is derived using Taylor’s expansion of the loss function.[⁴](#16_Chapter08.xhtml#ch8-r-fn4) XGBoost also places more emphasis on regularization parameters.

The parameters in XGBoost may be categorized as general parameters, booster parameters and task parameters.

#### 8.8.1 | XGBoost with h20 – General Parameters

General parameters relate to the booster which will be used for developing the model. These are generally tree or linear model:

booster: Can be gbtree, gblinear or dart; gbtree and dart use tree-based models while gblinear uses linear functions. Default is gbtree.

Based on the booster selected, other booster parameters become applicable. There are other general parameters as well which h2o XGBoost method handles efficiently.

#### 8.8.2 | XGBoost with H2O – Learning Task Parameters

In h2o, the distribution (i.e., the loss function) parameter decides the learning scenario. The options are AUTO, Bernoulli, multinomial, Gaussian, Poisson, gamma, or Tweedie (Anon, 2016) According to doc.h2o.ai:.

**1.** For Bernoulli distribution, the response column must be 2-class categorical.

**2.** For multinomial distribution, the response column must be categorical.

**3.** For poisson distribution, the response column must be numeric.

**4.** For Tweedie distribution, the response column must be numeric.

**5.** For gaussian distribution, the response column must be numeric.

**6.** For gamma distribution, the response column must be numeric.

As per the site docs.h2o.ai, “AUTO distribution is performed by default. In this case, the algorithm will guess the model type based on the response column type. If the response column type is numeric, AUTO defaults to ‘gaussian’; if categorical, AUTO defaults to binomial or multinomial depending on the number of response categories (Anon, 2016)”.

#### 8.8.3 | XGBoost with h20 – Booster Parameters

This depends on the selected booster. In h2o.xgboost, for booster = gbtree, the following are the booster parameters defined:

#### Random Subspace Selection

The following methods can be used for subspace selection (*Source:* docs.h2o.ai):

**1.** “col\_sample\_rate (colsample\_bylevel) – This parameter specifies the proportion of columns to be randomly selected (without replacement) for each tree. The default value is 1, but it can take any value between 0.0 and 1.0. A higher value for this parameter may improve training accuracy.

**2.** col\_sample\_rate\_per\_tree (colsample\_bytree) – This parameter specifies the proportion of columns to be randomly selected (without replacement) for each tree. This takes a value between 0.0 and 1.0. The default value is 1 which implies to select all columns for each tree growth. This parameter works in conjunction with col\_sample\_rate. Thus setting col\_sample\_rate = 0.7 and col\_sample\_rate\_per\_tree = 0.7 will result in 49% of columns being considered at any given node to split.

#### Random Row Selection (Bootstrap)

sample\_rate (subsample) – According to docs.h2o.ai this parameter, “Specifies the row sampling ratio of the training instance (*x*\-axis). Note that this method is sample without replacement. For example, setting this value to 0.5 makes XGBoost to randomly collect half the data instances to grow trees. The default value is 1, and the range is 0.0 to 1.0. Higher values may improve training accuracy. Test accuracy improves when either columns or rows are sampled. For details, refer to ‘Stochastic Gradient Boosting’ (Friedman, 1999)”.

#### Class Imbalance

max\_abs\_leafnode\_pred (max\_delta\_step): As per docs.h2o.ai, this parameter, “specifies the maximum delta step allowed in each tree’s weight estimation. The default value is 0. Setting this value to 0 specifies no constraint. Setting this value to greater than 0 can make the update step more conservative and reduce overfitting by limiting the absolute value of a leaf node prediction. This option also helps when a class is extremely imbalanced. Setting it to value of 1-10 might help control the update”.

#### Other Booster Parameters

The parameters which can lead to controlling the growth of the tree (*Source:* docs. h2o.ai).

**1.** min\_split\_improvement (gamma) – This parameter can be used to reduce overfitting by restricting the growth of the tree. The value of this parameter signifies the minimum change in the in squared error to split a node into two. The optimal values for this parameter can be in the range of 10^(−10) to 10^(−3).

**2.** max\_depth – This is another parameter to reduce overfitting. It is used to control the depth to which a tree can grow. A higher value for this parameter will lead to a more complex tree. If the value is set to 0, it will mean no limit to grow the tree (highly complex tree). The default is set to 5.

**3.** min\_rows (min\_child\_weight) – Specifies the minimum number of observations for a leaf, defaults to 1.

**4.** learn\_rate (eta) – Specifies the learning rate by which to shrink feature weights. Shrinking feature weights after each boosting step makes the boosting process more conservative and prevents overfitting. The range of learn\_rate is between 0.0 and 1.0. This value defaults to 0.3.

**5.** reg\_lambda (lambda) – L2 regularization term on weights with a default value of 1. Increasing this value will make the model more conservative.

**6.** reg\_alpha (alpha) – L1 regularization term on weights with a default value of 0. Increasing this value will make the model more conservative.

#### 8.8.4 | XGBoost with h2o – Create the Dataset

Let us create the dataset for training purposes. We will also use the columns\_weight parameter for fine-tuning the XGBoost model. To do so, we will create a WEIGHT column as a part of the filter\_h2f dataframe.

![](images/page323-01.png)![](images/page324-01.png)

sample\_rate\_per\_class = c(Detractor = 1.0,passive = 0.102,Promoter 0.083),

![](images/page324-02.png)

The dimensions of the train, test and validate data frame are as follows:

![](images/page324-03.png)

#### 8.8.5 | XGBoost with h2o – Hyper-parameters

h2o package has the XGBoost method which can be directly called to build an XGBoost model. Like in randomForest and gbm model, here also we will use the grid method to fine-tune the hyper-parameters. Let us create a grid space to search for the best hyper-parameter.

![](images/page324-04.png)

#### 8.8.6 | XGBoost with h2o – Search Criteria

We define a search criterion using Cartesian or DiscreteRandom strategy. Let us implement the search criterion as specified in randomForest ([Section 8.4.9](#16_Chapter08.xhtml#sec8.4.9)).

![](images/page324-05.png)

#### 8.8.7 | XGBoost – Grid Search

We will use the grid method of h2o and pass the model parameters, search criteria, list of hyper-parameters. We will train and tune the XGBoost model using the validation frame created for gbm.

![](images/page325-01.png)

#### 8.8.8 | Model Diagnostic

Sort the model using one of the metrics:

r2, mean\_per\_class\_accuracy, max\_per\_class\_error, err, total\_rows, rmse, accuracy, err\_count, logloss, mse, mean\_per\_class\_error

As discussed in [Section 8.4.11](#16_Chapter08.xhtml#sec8.4.11), for a multiclass classification logloss is a reliable metric to evaluate the performance of the model. Logloss can take any value greater than 0. A value of 0 implies that the model has correctly assigned a probability of 0% or 100%.

![](images/page325-02.png)![](images/page325-03.png)![](images/page326-01.png)

Select the first model from **[Table 8.17](#16_Chapter08.xhtml#tab8.17)** for further evaluation.

![](images/page326-02.png)

We can look at the training metrics as below.

![](images/page326-03.png)

We can look at the validation metrics in a similar way:

![](images/page327-01.png)

#### 8.8.9 | Model Prediction

Let us use the model for prediction on the test set **([Table 8.18](#16_Chapter08.xhtml#tab8.18)).**

![](images/page327-02.png)![](images/page327-03.png)

Let us see the performance of the model on the test frame.

![](images/page328-01.png)

#### 8.8.10 | XGBoost with h2o – Result Discussion

Fine-tuning all the parameters at once may increase the time to fine-tune the model. Here are the steps performed to fine-tune the parameter. The values obtained in previous iterations were kept fixed while fine-tuning the parameters in subsequent iterations.

##### **Iteration 0:**

With a datasplit of (0.55,0.25,0.20), the model was built with default parameters but after adjusting the column weight. The performance of the model is reported in **[Table 8.19](#16_Chapter08.xhtml#tab8.19).**

##### **Iteration 1: Fine-tuning ntree, min\_rows and col\_sample\_rate.**

**1.** ntrees = seq(10,100,10),

**2.** min\_rows = seq(1,10,1)

**3.** col\_sample\_rate = seq(0.1,1.0,0.1)

The sample split of (0.55,0.25,0.20) reported (30,2,0.1) as the best combination. **[Table 8.20](#16_Chapter08.xhtml#tab8.20)** has the model performance for this split.

![](images/page328-02.png)![](images/page329-01.png)

##### **Iteration 2:**

**1.** max\_depth = seq(1,10,1)

**2.** learn\_rate = *c*(0.1,0.3,0.5,1), #eta

**3.** sample\_rate = *c*(0.6,0.8,0.9,1.0), #row sampling

**4.** min\_split\_improvement = *c*(0,0.01,0.001,0.0001) #gamma

The sample split of (0.55,0.25,0.20) reported (7,0.3,1.0,0.001) as the best combination. Model performance is reported in **[Table 8.21](#16_Chapter08.xhtml#tab8.21).**

##### **Iteration 3:**

**1.** reg\_lambda = *c*(0.6,0.8,0.9,1.0),

**2.** reg\_alpha = *c*(0,0.1,0.2,0.3,0.5)

**3.** max\_abs\_leafnode\_pred = *c*(0,1,5,10,15)

The default (1.0,0,1) was reported as the best parameter. Either individually or in combination, these parameters did not help improve the model with data split of (0.55,0.25,0.20). Model performance is reported in **[Table 8.22](#16_Chapter08.xhtml#tab8.22).**

The objective in building the NPS model was to identify Detractors amongst the customers. In **[Table 8.22](#16_Chapter08.xhtml#tab8.22)**, with an error of 0.2857, the model seems to be doing not as well as Random Forest or the gbm model in predicting Detractors correctly. However, with an overall accuracy of 70%, XGBoost is better than Random Forest.

![](images/page329-02.png)![](images/page329-03.png)

Note that

**1.** The parameters reported are the ones which give maximum improvement on the logloss.

**2.** Though hyper-parameter fine-tuning was not done in model\_iter0 it is not similar to the base model. We adjusted the weights\_column even before developing the model in any of the iterations.

Fine-tuning the XGBoost model is time-consuming and will need several iterations before the near optimal model can be obtained. It is observed that ntrees, min\_rows and col\_sample\_rate lead to a significant improvement in logloss. Though there are other parameters of interest in XGBoost, they do not seem to improve the logloss in the NPS problem.

Based on the results obtained in the earlier iterations, the final model was built with the grid search of the below parameters:

**1.** ntrees = seq(20,40,5),

**2.** max\_depth = seq(4,8,1),

**3.** min\_rows = seq(1,4,1),

**4.** col\_sample\_rate = seq(0.05,0.15,0.05),

**5.** min\_split\_improvement = *c*(0.01,0.001,0.0001)

The best combination was (30,7,2,0.1,0.001).

#### 8.8.11 | Final XGBoost Model

We can build the final model with the set of fine-tuned parameters and using the full dataset, that is, filter\_h2f.

![](images/page330-01.png)![](images/page331-01.png)

Accuracy of the final XGBoost model is 74%.

#### 8.8.12 | Save the model

The model can now be saved with the set of fine-tuned parameters.

![](images/page331-02.png)

### Summary

In this chapter, we learnt

**1.** Model building by defining a cost function for Random Forest algorithm.

**2.** Model building and fine-tuning for Gradient Boosting machine.

**3.** Model building and fine-tuning the extreme gradient boosting (XGBoost).

**4.** Bias and variance trade-off and how to avoid model overfitting using regularization in bagging and boosting model.

**5.** Dealing with class imbalance issue in multiclass classification models.

### Exercise

#### Answer Questions 1 to 8 using the Earnings Manipulation Dataset.[⁵](#16_Chapter08.xhtml#ch8-r-fn5)

MCA Technology Solutions Private Limited was established in 2015 in Bangalore with an objective to integrate analytics and technology with business. MCA Technology Solutions helped its clients in areas such as customer intelligence, forecasting, optimization, risk assessment, web analytics, text mining, and cloud solutions. Risk assessment vertical at MCA technology solutions focuses on problems such as fraud detection and credit scoring. Sachin Kumar, Director at MCA Technology Solutions, Bangalore, was approached by one of his clients, a commercial bank, to assist them in detecting earning manipulators among the bank’s customers. The bank provided business loans to small and medium enterprises and the value of loan ranged from INR 10 million to 500 million ($1 = INR 66.82, August 16, 2016). The bank suspected that their customers may be involved in earnings’ manipulations to increase their chance of securing a loan.

Saurabh Rishi, the Chief Data Scientist at MCA Technologies, was assigned the task of developing a use case for predicting earning manipulations. He was aware of models such as *Beneish* model that was used for predicting earning manipulations; however, he was not sure of its performance, especially in the Indian context. Saurabh decided to develop his own model for predicting earning manipulations using data downloaded from the Prowess database maintained by the Centre of Monitoring Indian Economy (CMIE). Daniel received information related to earning manipulators from Securities Exchange Board of India (SEBI) and the Lexis Nexis database. Data on 220 companies was collected to develop the model.

The data is available in the file *‘EarningsManipulation220. csv’.* Description of the columns is given in **[Table 8.23](#16_Chapter08.xhtml#tab8.23).** In this table

• netPPE is net Property, Plant, and Equipment. Property, Plant, and Equipment is the value of all buildings, land, furniture, and other physical capital that a business has purchased to run a business.

• Subscript (*t*) means value in the current-year financial statement and subscript (*t* − 1) means the value in the previous-year financial statement.

![](images/page332-01.png)![](images/page333-01.png)

**1.** How many cases of manipulators versus non-manipulators are there in the dataset? Draw a bar plot to depict.

**2.** Create an 80:20 partition, and find how many positives are present in the test data.

**3.** The number of cases of manipulators is very less compared to non-manipulators. Use caret package and build model using up-sampling technique.

• Random Forest

• Gradient Boosting Machine

Compare the accuracies of the models using ROC AUC score as performance metric.

**4.** The number of cases of manipulators is very less compared to non-manipulators. Use down-sampling technique to create a balance dataset. Build the following models using caret package:

• Random Forest

• Gradient Boosting Machine

Compare the accuracies of the models using ROC AUC score as performance metric.

**5.** The number of cases of manipulators is very less compared to non-manipulators. Use SMOTE sampling technique to create a balance dataset. Build the following models using caret package:

• Random Forest

• Gradient Boosting Machine

Compare the accuracies of the models using ROC AUC score as performance metric.

**6.** The number of cases of manipulators is very less compared to non-manipulators. Use rose sampling technique to create a balance dataset. Build the following models using caret package:

• Random Forest

• Gradient Boosting Machine

Compare the accuracies of the models using ROC AUC score as performance metric.

**7.** Compare the results of using up-sampling, down-sampling, SMOTE and rose techniques. Report the best model of all the models. Which sampling technique gives the best result on this dataset.

**8.** Report the features’ importance of the best model using random forest as well as gradient boosting machine. Explain the results.

### Bibliography

**1.** Anon (2016), *“mtries description”*, Web Address: [http://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/al-go-params/mtries.html](http://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/al-go-params/mtries.html), accessed on 01 February 2021.

**2.** Anon (2016), *“Performance and Prediction”*, Web Address: [https://docs.h2o.ai/h2o/latest-stable/h2o-docs/perfor-mance-and-prediction.html](https://docs.h2o.ai/h2o/latest-stable/h2o-docs/perfor-mance-and-prediction.html), accessed on 01 January 2021.

**3.** Anon (2016), *“Performance and Prediction”*, Web Address: [http://h2o-release.s3.amazonaws.com/h2o/rel-yau/6/docs-website/h2o-docs/performance-and-prediction.html](http://h2o-release.s3.amazonaws.com/h2o/rel-yau/6/docs-website/h2o-docs/performance-and-prediction.html), accessed on 01 January 2021.

**4.** Anon (2016), *“Distribution”*, Web Address: [https://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/algo-params/distribution.html](https://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/algo-params/distribution.html), accessed on 01 February 2021.

**5.** Anon (2016),*”GBM”*, Web Address: [https://h2o-release.s3.amazonaws.com/h2o/rel-turing/1/docs-website/h2o-docs/welcome.html](https://h2o-release.s3.amazonaws.com/h2o/rel-turing/1/docs-website/h2o-docs/welcome.html), accessed on 01 February 2021.

**6.** Anon (2019), *“Distribution”*, Web Address [https://h2o-re-lease.s3.amazonaws.com/h2o/rel-yau/3/index.html](https://h2o-re-lease.s3.amazonaws.com/h2o/rel-yau/3/index.html), accessed on 01 February 2021.

**7.** Anon (2018), *“SMOTE – SMOTE Algorithm for Unbalanced Classification Problems”*, Web Address: [https://www.rdocumentation.org/packages/DMwR/versions/0.4.1/top-ics/SMOTE](https://www.rdocumentation.org/packages/DMwR/versions/0.4.1/top-ics/SMOTE), accessed on 01 February 2021.

**8.** Anon (2020), *“Create balanced dataset 1:1 using SMOTE without modifying the observations of the majority class in R”*, Web Address: [https://stackoverflow.com/questions/62871492/create-balanced-dataset-11-us-ing-smote-without-modifying-the-observations-of-th](https://stackoverflow.com/questions/62871492/create-balanced-dataset-11-us-ing-smote-without-modifying-the-observations-of-th), accessed on 01 February 2021.

**9.** Anon (2021), *“Splitting datasets into Training/testing/validating”*, date viewed 2021, Web Address: [https://h2o-re-lease.s3.amazonaws.com/h2o/rel-vajda/1/docs-website/h2o-docs/data-munging/splitting-datasets.html](https://h2o-re-lease.s3.amazonaws.com/h2o/rel-vajda/1/docs-website/h2o-docs/data-munging/splitting-datasets.html), accessed on 01 February 2021.

**10.** Anon (2020), *“Isolation Forest”*, Web Address: [http://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/if.html](http://docs.h2o.ai/h2o/latest-stable/h2o-docs/data-science/if.html), accessed on 01 February 2021.

**11.** Anon (2020), *“Performance and prediction”*, Web Address: [https://docs.h2o.ai/h2o/latest-stable/h2o-docs/performance-and-prediction.html](https://docs.h2o.ai/h2o/latest-stable/h2o-docs/performance-and-prediction.html),, accessed on 01 February 2021.

**12.** Anon (2021), We are improving the predictions of training data but is the procedure also | Course Hero, Web Address: [https://www.coursehero.com/file/puj8l6/What-is-the-process-of-dividing-each-feature-by-its-range-called-fea-ture](https://www.coursehero.com/file/puj8l6/What-is-the-process-of-dividing-each-feature-by-its-range-called-fea-ture)/, accessed on 01 February 2021.

**13.** Beneish M D (1999), “The Detection of Earnings Manipulations”, *Financial Analyst Journal*, **55**(5), 24–36.

**14.** Bernard S, Heutte L, Adam S (2010), “A Study of Strength and Correlation in Random Forests”, *International Conference on Intelligent Computing*, Aug 2010, Changsha, China. pp.186–191, ff10.1007/978-3-642-14831-6\_25ff.ffhal-00598466f.

**15.** Breiman L (1996), “Bagging predictors,” *Machine Learning*, 24 (2), 123–140.

**16.** Breiman L (2001), “Random forests”, *Machine Learning*, **45** (1), 5–32.

**17.** Chawla N V, Bower K W, Hall L O and Kegelmeyer W P (2002), “SMOTE: Synthetic Minority Over-sampling Technique”, *Journal of Artificial Intelligence Research*, **16**, 321–357.

**18.** Kumar U D, Syed T A I and Ganeshan (2016), “Predicting Earnings Manipulations by Indian Firms Using Machine Learning Algorithms”, *Harvard Business Publishing*, available at [https://hbsp.harvard.edu/product/IMB577-PDF-ENG?Ntt=Earnings%20manipulation](https://hbsp.harvard.edu/product/IMB577-PDF-ENG?Ntt=Earnings%20manipulation), accessed on 04 August 2021.

**19.** Friedman J H (2001), *“Greedy Function Approximation: A Gradient Boosting Machine”*, Stanford University Report, Web Address: [https://statweb.stanford.edu/~jhf/ftp/trebst.pdf](https://statweb.stanford.edu/~jhf/ftp/trebst.pdf), accessed on 01 February 2021.

**20.** Friedman J H (2002), “Stochastic Gradient Boosting”, *Computational Statistics and Data Analysis*, **38**(4), 367–378.

**21.** Kullback S and Leibler R A (1951), “On Information and Sufficiency”, *Annals of Mathematical Statistics*, **22** (1), 79–86.

**22.** LeDell L (2020), *“h2o.splitFrame”*, Web Address: [https://www.rdocumentation.org/packages/h2o/ver-sions/3.32.0.1/topics/h2o.splitFrame](https://www.rdocumentation.org/packages/h2o/ver-sions/3.32.0.1/topics/h2o.splitFrame), accessed on 01 February 2021.

**23.** Li C (2018), *“A Gentle Introduction to Gradient Boosting”*, Web Address: [https://www.ccs.neu.edu/home/vip/teach/MLcourse/4\_boosting/slides/gradient\_boosting.pdf](https://www.ccs.neu.edu/home/vip/teach/MLcourse/4_boosting/slides/gradient_boosting.pdf), accessed on 01 February 2021.

**24.** D Li, W Li, X Wang, C T Nguyen and S Lu (2020), “App trajectory recognition over encrypted internet traffic based on deep neural network”, *Computer Networks*, **179**, Web Address: [https://doi.org/10.1016/jxomnet.2020.107372](https://doi.org/10.1016/jxomnet.2020.107372), accessed on 01 February 2021.

**25.** Lunardon N, Menardi G and Torelli N (2014), “ROSE: a Package for Binary Imbalanced Learning” *R Journal*, **6**, 82–92.

**26.** Menardi G and Torelli N (2014), “Training and assessing classification rules with imbalanced data”, *Data Mining and Knowledge Discovery*, **28**, 92–122.

**27.** Torgo L (2010), *“Data Mining Using R: Learning with Case Studies”*, CRC Press., Florida

**28.** Torgo, Luis & Ribeiro, Rita & Pfahringer, Bernhard & Branco, Paula. (2013), “SMOTE for Regression”, 8154. 378–389. 10.1007/978-3-642-40669-0\_33.

**29.** Xu Y, Wu C, Zheng K, Niu X and Yang Y (2017), “Fuzzy-synthetic minority oversampling technique: Oversampling based on fuzzy set theory for Android malware detection in imbalanced datasets”, *International Journal of Distributed Sensor Networks*, **13**(4), Web Address: [https://doi.org/10.1177/1550147717703116](https://doi.org/10.1177/1550147717703116), accessed on 01 February 2021.

**30.** Yang F, Lu W, Luo L and Li T (2012), “Margin Optimization based Pruning for Random Forest”, *Neurocomputing*, **94**, 54–63.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#16_Chapter08.xhtml#ch8-fn1)[https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)

[²](#16_Chapter08.xhtml#ch8-fn2)[http://www.chengli.io/tutorials/gradient\_boosting.pdf](http://www.chengli.io/tutorials/gradient_boosting.pdf)

[³](#16_Chapter08.xhtml#ch8-fn3)Source: [http://www.chengli.io/tutorials/gradient\_boosting.pdf](http://www.chengli.io/tutorials/gradient_boosting.pdf)

[⁴](#16_Chapter08.xhtml#ch8-fn4)Source: [https://xgboost.readthedocs.io/en/latest/tutorials/model.html](https://xgboost.readthedocs.io/en/latest/tutorials/model.html)

[⁵](#16_Chapter08.xhtml#ch8-fn5)*Source:* Kumar U D, Syed T A I and Ganeshan (2016), “Predicting Earnings Manipulations by Indian Firms Using Machine Learning Algorithms”, *Harvard Business Publishing*, available at [https://hbsp.harvard.edu/product/IMB577-PDF-EN-G?Ntt=Earnings%20manipulation](https://hbsp.harvard.edu/product/IMB577-PDF-EN-G?Ntt=Earnings%20manipulation), accessed on 04 August 2021.

 

 
| 

## Text Analytics

 || 

## 9

 |
| --- | --- |

*When our false perception is corrected, misery ends also.*

**—Adi Shankara**

LEARNING OBJECTIVES

After reading this chapter, you would be able to:

• Understand the importance of text analytics.

• Understand challenges associated with handling text data.

• Understand regular expressions and its usefulness in text data preprocessing.

• Learn various preprocessing steps to prepare text data.

• Learn to develop a document term matrix which may be used for sentiment classification.

• Learn to create a dataset which is a mix of numeric features and unstructured text data for modelling purpose.

• Understand topic modelling and apply on a text data.

### 9.1 | Overview

In today’s world, one of the biggest sources of information is text data, which is unstructured – that is, the data which is not in matrix form. Finding customer sentiments from product reviews or feedbacks and extracting opinions from social media data are a few examples of text analytics. Techniques we have learnt so far require data to be available in a structured format (matrix form). The algorithms explored so far such as regression, classification or clustering can be applied to text data once it is cleaned and prepared (Pradhan and Kumar, 2019). A few examples of models on text data are as follows:

**1.** Predicting stock price movements from news articles is an example of regression whose features include positive and negative sentiments about a company.

**2.** Classifying customer sentiment from review comments as positive and negative is an example of classification using text data.

In this chapter, we will use a twitter dataset on the COVID pandemic to show basic textual data visualisation and to build a classification model to classify sentiment. We will employ R version 4.0.3 for this chapter.

### 9.2 | Data Scrapping

In this section, we will discuss the process for scrapping data from twitter. We need to set up our profile on twitter before scrapping data. The following steps can be used for scrapping data from twitter.

**1.** Create a profile on [http://twitter.com/signup](http://twitter.com/signup). Also, provide your mobile number as a part of setting up the twitter profile **([Figure 9.1](#17_Chapter09.xhtml#fig9.1)).**

**2.** After creating a profile, log on to [https://developer.twitter.com/en/apps](https://developer.twitter.com/en/apps) using the credentials. Click on the “create an app” icon and follow the steps to get developer access **([Figure 9.2](#17_Chapter09.xhtml#fig9.2)).**

After filling in the details, you will receive an email verification mail in your inbox.

![](images/page338-01.png)![](images/page338-02.png)![](images/page339-01.png)![](images/page339-02.png)

**3.** Click on the link, which will ask you to provide an app name (provide any name as long as it is available for use). We have decided on “tis\_tweet”, as shown in **[Figure 9.3](#17_Chapter09.xhtml#fig9.3).**

**4.** API Key (oauth\_consumer\_key) and API secret (oauth consumer secret) will be generated once the ‘app name’ is successfully created. Save them, because we will have to use them to make a connection from R platform to twitter. API key and secret – think of these as the user name and password, respectively, which represent your twitter developer app when making API requests (*source:* developer.twitter.com).

**5.** As shown in **[Figure 9.4](#17_Chapter09.xhtml#fig9.4)**, click on ‘Generate/ReGenerate’ Access token and secret. Access token (oauth\_token) and Access secret (oauth\_token\_secret) will be generated. Save them, because we will have to use them to make a connection from R platform to twitter. Access token and access token secret are user-specific credentials used to authenticate OAuth 1.0a API requests (*source:* developer.twitter.com).

We are ready for data scrapping; however, we will get introduced to regular expressions as a language before scrapping twitter data and proceeding with further analysis.

### 9.3 | Regular Expression

Dealing with unstructured data will require additional preprocessing to convert it into structured format. This involves a lot of character manipulation and pattern-matching to keep useful text and remove words without useful information. Regex (regular expression) is a specialized language and many of the programming languages support its use for pattern-matching in text data. We’ll use this language to specify the rules to be used for string-matching in a data and further splitting the data in various ways. Most of the text processing packages in R such as stringr and stringi support the use of **regular expressions**. gsub() and grep() package from base R also support the use of regex for pattern-matching. Advanced packages such as tidytext ease the work of pattern-matching by providing their own functions. These functions internally use regex.

**Regular expressions** is a specialized language and plays an important role in data pre-processing stage of textual information.

#### 9.3.1 Match Characters

In this session, we will discuss function for matching characters and words. Let us take a simple example text shown below:

![](images/page340-01.png)

We will use gsub() function to search and replace all matching patterns in a text. Let us find the word ‘Take’ and replace it with ‘We should take’.

![](images/page340-02.png)

Matching and replacing simple words is straightforward but case sensitive. Regex provides certain metacharacters which do not match themselves but provide a means to search for a pattern in a text. These metacharacters are . ∧ $ \* + ? { } \[ \] \\ | ( ). Let us understand the use of these metacharacters in the next section.

#### Metacharacter: big bracket ‘\[‘and’\]’

‘\[‘and’\]’ are used to specify a set of characters, termed as character class, which we wish to match. The set of characters can be listed individually or as a range. \[abc\] or \[a-c\] will try to match any of the characters ‘a’, ‘b’, or ‘c’. To match any of the characters from a to z, we can write \[a-z\]. Most of the metacharacters are inactive inside a character class. So \[xy\\$z\] will match ‘x’, ‘y, ‘z’ or ‘$’ (though ‘\\’ and ‘$’ are metacharacters on their own). However, ∧ - \] are special inside character classes too. To look for ‘\]’ in text, place it first in the list like, \[\] xyz\]. Similarly, to include a literal ‘∧’, place it anywhere but at the beginning, to insert a literal ‘-’ place it first or last (Silge and Robinson, 2017).

Let us use ‘\[teh|\]’ and replace the match with spaces (‘‘). The pattern ‘\[teh|\]’ looks for ‘t’ or ‘e’ or ‘h’ or ‘|’ in the text and any match is replaced by spaces.

![](images/page341-01.png)

#### Metacharacter: caret ‘∧’

The caret ‘∧’ is used to denote the complement of a character. ‘\[∧th∧\]’ will match any character but not ‘t, not ‘h’, and not ‘∧’. Note that ‘∧’ has a meaning only at the beginning of the character set. The ‘∧’ appearing anywhere else is treated as a normal character to be searched. \[∧a-z\] will match all characters but not those from ‘a’ to ‘z.

Let us use \[∧a-z\] to match the pattern. Notice the replacements in the text.

![](images/page341-02.png)

Use of ‘∧’ used outside the character class represents the search at the beginning of the line. Say, we want to match Festival and replace with spaces. Rather than writing the complete word ‘Festival’, we can do the following:

![](images/page341-03.png)

The above code in gsub() has three components in search pattern:

**1.** ‘∧F’ - looks for word starting with F. We can actually drop ‘∧’ and it will still work.

**2.** ‘\\w’ - looks for any alphanumeric character, that is, \[a-zA-Z0-9\]

**3.** ‘+’ − looks for the preceding value one or more times. The symbol + refers to the value passed inside gsub() in the above code.

The above code snippet can also be rewritten as below:

![](images/page342-01.png)

We can also use the below code snippet to look for any word starting with ‘F’ or ‘f’ and replace it with spaces.

![](images/page342-02.png)

Let us observe the difference in the outcome between the code snippet above and the one used below.

![](images/page342-03.png)

#### Metacharacter: backslash ‘\\’

The backslash ‘\\’ can be followed by various characters to signal special sequence. The ‘\\’ can also be used to skip the metacharacters so that it can be matched in text. \[\\\] will replace newline ‘‘ or ‘\\’ in the text.

![](images/page342-04.png)

There are certain predefined character classes supported by R. These are as follows (Silge and Robinson, 2017):

**1.** \[:alnum:\] – Alphanumeric characters: \[:alpha:\] and \[:digit:\] that is \[a-zA-Z0-9\].

**2.** ∧\[:alnum:\] – Non-Alphanumeric characters: ∧\[:alpha:\] and ∧\[:digit:\] that is ∧\[a-zA-Z0-9\].

**3.** \[:alpha:\] – Alphabetic characters: \[:lower:\] and \[:upper:\] that is \[a-zA-Z\].

**4.** \[:blank:\] – Blank characters: space and tab, and possibly other locale-dependent characters such as non-breaking space.

**5.** \[:cntrl:\] – Control characters. In ASCII, these characters have octal codes 000 through 037, and 177 (DEL).

**6.** \[:digit:\] – Digits: 0 1 2 3 4 5 6 7 8 9.

**7.** \[:graph:\] – Graphical characters

**8.** \[:lower:\] – Lower-case letters in the current locale.

**9.** \[:print:\] – Printable characters

**10.** \[:punct:\] – Punctuation characters: ! “ # $ % & ‘ ( ) \* + , − . / : ; < = > ? @ \[ \] ∧ \_ ‘ { | } ~.

**11.** \[:space:\] – Space characters: tab, newline, vertical tab, form feed, carriage return, space and possibly other locale-dependent characters.

**12.** \[:upper:\] – Upper-case letters in the current locale.

**13.** \[:xdigit:\] – Hexadecimal digits: 0 1 2 3 4 5 6 7 8 9 A B C D E F a b c d e f.

For more help on predefined character class, type ?regex on console. Using the predefined character class, let us remove newline and digits from the text. The original text is as shown below.

![](images/page343-01.png)

The newline and digits can be removed by using the following code chunk:

![](images/page343-02.png)

The above result can also be achieved by using ‘\\d|\\s’ where | is an ‘or’ operator in regex. The code below implements ‘\\d|\\s’ to obtain the same result.

![](images/page343-03.png)

Let us reprint the text and then remove all characters but not digits and spaces.

![](images/page343-04.png)

The below code snippet replaces everything with spaces except the digits and newline ().

![](images/page344-01.png)

Replacing alphabets and digits in a text with spaces can be done using the below code.

![](images/page344-02.png)

Replacing everything with spaces but the alphabets and digits in a text can be done using the below code.

![](images/page344-03.png)

#### Metacharacter: dollar ‘$’

The metacharacter ‘$’ is used to match a pattern at the end of the line. End of line is defined as either end of string or a text just preceding the newline character (\\n). Let us remove the full stop ‘x’ from the end of each sentence shown below.

![](images/page344-04.png)

#### Metacharacter: dot ‘x’

The dot ![](images/pageIn_ch9-01.png)is another metacharacter used to match any character once except for line break. ‘\[a.\]’ will match the character ‘a’ once in the text. However, since we are using ‘gsub()‘ function, we will see the match and replace happening at all places in the text. Thus, we will use sub() function which does the match only once.

![](images/page344-05.png)![](images/page345-01.png)

#### 9.3.2 Repeat Characters

Apart from matching a set of characters defined in the character class, regex can also be used to look for repetition in pattern a certain number of times.

#### Metacharacter: star ‘\*’

The ‘\*’ specifies that the previous character can be repeated zero or more times rather than exactly once. So, *h*\[*t\**\] will look for words starting with *‘h’* and matching occurrence of *‘t’* zero or more times.

![](images/page345-02.png)

#### Metacharacter: plus ‘+’

The ‘+’ specifies that the previous character can be repeated one or more times rather than exactly once. So, *h*\[*t*+\] will look for words starting with *‘h’* and matching occurrence of *‘t’* one or more times.

![](images/page345-03.png)

#### Metacharacter: question mark ‘?’

The ‘?’ specifies that the previous character can be repeated once or zero times. So, covid-?19 will match ‘covid-19’ or ‘covid19.

![](images/page345-04.png)![](images/page346-01.png)

#### 9.3.3 Application of Regex

Let us create the regular expression and use it to remove the newline, the URL as well as the punctuations from the text.

![](images/page346-02.png)

Another way to achieve the above result is as below:

![](images/page346-03.png)

We will now split the text into separate words. The regex “\[∧\[:alnum:\]\]” will look for split point which is not an alphanumeric character. We will use str\_split() function from stringr package to split the data.

![](images/page346-04.png)

Regex and gsub are also useful in the clean-up of data. **[Table 9.1](#17_Chapter09.xhtml#tab9.1)** shows data which is messy. We will name this data as ‘random\_df‘.

![](images/page347-01.png)

**[Table 9.1](#17_Chapter09.xhtml#tab9.1)** shows the following issues:

**1.** The column names have the ‘$’ sign, which may result in issues while referring to the column name. In any other case, the columns could have any punctuation marks which may not be desirable.

**2.** The values in sales unit contain ‘,’ and thus will get recognized as a character variable.

**3.** The values in Gross Margin, Net Sales, etc., contain the ‘$’ sign and other characters, which cause these columns to be recognized with incorrect data type.

These issues can be corrected by using gsub and regex as shown below.

![](images/page347-02.png)

The column names are all in syntactically correct order with no punctuation marks. Let us clean the column values by using the code below.

![](images/page347-03.png)

From **[Table 9.2](#17_Chapter09.xhtml#tab9.2)**, we can see that the unwanted characters in column names are not present. However, the data type for the column values may still not be correct (example, the presence of ‘,’ in the values for SOP units variable would have marked this column as a categorical column). The default parameters of read.csv(), typecast categorical variable as a factor variable. So, we cannot do a direct typecasting of these columns to numeric.

![](images/page348-01.png)

If we do so, the numeric values in the columns will not be correct. Thus, we will first typecast the variables as character variable and then typecast it as a numeric variable. The below function helps achieve this.

![](images/page348-02.png)

From **[Table 9.3](#17_Chapter09.xhtml#tab9.3)**, we can see that the column names and the values in the column are in correct data type. This dataframe can be saved using ‘write.csv()‘ function and can be used in further analysis.

This section gives us some idea about the use of regex in text processing. In the following sections, we will use the advanced packages which abstract regex and provide easy ways to apply it to clean up text data.

### 9.4 | Packages for Text Analytics

We will use state-of-the-art packages such as twitteR, tidyVerse, tidytext, stringr, quanteda, text2vec, and spacyr for preprocessing and analysing text data.

**1.** **twitteR, streamR, and rtweet:** All of them are for building a connection to twitter API and pulling tweets.

**2.** **stringr:** Used for character manipulation, case-sensitive transformation, and pattern-matching using regular expressions (regex). We will use regex with gusb() for text preprocessing.

![](images/page348-03.png)

**3.** **tidytext:** Part of tidyverse family of packages, this package can be used for basic data clean-up, visualization, creating term frequency-inverse document frequency (tf-idf), creating n-grams as well as for topic modelling. This package works seamlessly with dplyr, ggplot for visualization. We will extensively use this package for summarization, visualization, sentiment analysis, creating DTM (document term matrix) and topic modelling.

**4.** **quanteda:** Quantitative text data analysis (quanteda) provides functions for performing basic natural language processing like text preprocessing, tokenization and creating document feature matrix, topic modelling, and other advanced operations. We will not be using this package.

**5.** **text2vec:** This package, inspired by Gensim, allows the construction of a document term matrix or term co-occurrence matrix (tcm) from documents. Using text2vec, we can vectorize text by creating a map from words or n-grams to a vector space. A dtm or tcm is generated based on this vectorized text. Models such as topic modelling (Latent Dirichlet Allocation, Latent Semantic Analysis), word embeddings (GloVe), collocations, similarity searches, etc., can be built on the dtm, tcm (Anon, 2021).

**6.** **spacyr:** Adopted from spacy package in Python, this package can be used for advanced Natural Language Processing (NLP) like preparing data for deep learning, tokenization, parsing, etc. This package seamlessly works with quanteda and tidytext.

Note that in the above-mentioned packages, there are redundant functions and packages. We can use the packages and functions based on the objective to be achieved while analysing text data. However, one of the useful and basic packages which will play a role in text preprocessing is stringr. Stringr uses regular expressions (regex) for pattern-matching within the text and then performs clean-up of text data. In fact, the functions within the tidytext package will internally use regex expressions a lot.

If any of the packages were installed earlier and initialization of packages gives error due to version mismatch, we may have to reinstall the package before proceeding further. Run the below two lines in console before proceeding further.

**1.** if (“package:” %in% search()) { detach(“package:”, unload=TRUE)}

**2.** if (““ %in% rownames(installed.packages())) { remove.packages(““)}

![](images/page349-01.png)![](images/page350-01.png)

### 9.5 | Data Import

We will need to build the connection to twitter and authenticate R to pull tweets. setup\_twitter\_oauth function from twitteR authorizes twitteR session. We will use twitteR to pull request from twitter.

#### 9.5.1 Using twitteR Package

twitteR can be used to pull tweets over a period of time. The searchTwitter function from twitteR package is used to pull the tweets. Since we want to pull tweets related to pandemic updates in India, we will use the following keywords and twitter handle:

**1.** #IndiaFightsCorona – containing hashtag IndiaFightsCorona.

**2.** @COVIDNewsByMIB – mentioning Twitter account “COVIDNewsByMIB”.

**3.** @covid19indiaorg – mentioning Twitter account “covid19indiaorg”.

**4.** @COVID19\_INDIA – mentioning Twitter account “COVID19\_INDIA”.

The guide to writing query is mentioned in twitter app documentation [https://developer.twitter.com/en/docs/twitter-api/v1/tweets/search/guides/standard-operators](https://developer.twitter.com/en/docs/twitter-api/v1/tweets/search/guides/standard-operators). We can also modify the search query to filter or exclude certain types of results by using the below syntax (Anon, 2020):

**1.** Exclude retweets via “-filter:retweets”

**2.** Exclude quotes via “-filter:quote”

**3.** Exclude replies via “-filter:replies”

**4.** Filter (return only) verified via “filter:verified”

**5.** Exclude verified via “-filter:verified”

**6.** Get everything via “-filter:verified OR filter:verified”

**7.** Filter (return only) tweets with links to news articles via “filter:news” Filter (return only) tweets with media “filter:media”

For example, “#IndiaFightsCorona -filter:retweets” will give tweets with retweets excluded. To get more help, on the parameters for searchTwitter function, type in console: ?twitteR::searchTwitter. Twitter API also lists several other parameters which can also be passed to the search\_tweets.[¹](#17_Chapter09.xhtml#ch9-r-fn1) Let us load the twitteR package and authenticate R to pull tweets.

![](images/page351-01.png)![](images/page351-02.png)

Please note that the pull request of 50,000 tweets may not necessarily return the same number of tweets in every run of the script. In the pull request above, the first run returned 25,494 tweets while the second run returned 19,362 tweets.

searchTwitter also has a parameter named geocode, where we can pass the latitude, longitude, and the radius within which we want to search for the users’ tweets. Say, in the above query, if we want to search for tweets from within a 1,000-km radius of Jabalpur, Madhya Pradesh, India, the geocode will be geocode = “23.22321145,79.9811422182487,10 00km”. The query may report 12,353 tweets for this geocode.

The data type for covid\_twitteR object is list. We will convert it into a dataframe using twListToDF function from twitteR.

![](images/page351-03.png)

We will also save the ‘covid\_twitter\_df‘ as a csv file so that we do not have to query twitter API later on.

![](images/page351-04.png)

The dimensions of the data are as follows:

![](images/page352-01.png)

The features returned by the twitter API are as follows.

![](images/page352-02.png)

The ‘text’ feature contains comments by users and is restricted to 280 characters by twitter. This ‘text’ feature will be used for further analysis. Though the longitude and latitude features are present in the feature list, we can see in **[Table 9.4](#17_Chapter09.xhtml#tab9.4)** that they contain NA values for each user. Twitter API does not report the latitude and longitude for users due to privacy concerns. However, we can get the location of the users by using lookupUsers function. These functions will return the details if the user does not have a private account.

![](images/page352-03.png)

The user\_details object is of type list. We will convert it into a dataframe and save as a csv file.

![](images/page352-04.png)![](images/page352-05.png)

Saving the user details to avoid further read from the API.

![](images/page353-01.png)

From the user\_detail\_df, we can get the user location by using print(user\_detail\_df$location).

The covid\_twitter\_df may contain duplicate texts which can be removed before further analysis. We can remove the duplicate text in the covid\_text\_df by using duplicated() from the base package. The function expects a column vector or a dataframe to be passed. If we pass the column vector, say covid\_twitter\_df$text, we will get 7,484 unique texts. However, if we pass the complete dataframe, there is no duplicate record as the same tweet could have been shared by a different user (identified by screenName column). From the dimensions of ‘covid\_twitteR\_unq\_df‘ dataframe, we can conclude that there is no duplicate record.

![](images/page353-02.png)

We will proceed with further analysis using the covid\_twitter\_df. The first five observations are shown in **[Table 9.4](#17_Chapter09.xhtml#tab9.4).**

![](images/page353-03.png)

### 9.6 | Text Prepreprocessing

Before we process the ‘text’ column of covid\_twitter\_df shown in **[Table 9.4](#17_Chapter09.xhtml#tab9.4)**, let us understand some of the basics in text preprocessing. Unlike structured data, features (independent variables) are not explicitly available in text data. Thus, we need to process text data to extract features from it. One way to create a feature is to consider each word as a feature and find a measure to capture whether a word exists or does not exist in a sentence (Pradhan and Kumar, 2019). The row items of the text column in covid\_twitter\_df are sentences and contribute to building Bag-of-Words (BoW). Each sentence (record) is called a document and a collection of all documents is called corpus. Let us define BoW

#### 9.6.1 Bag-of-Words (BoW) Model

Intuitively, BoW is a dictionary/vocabulary of known words from the corpus. A Bag-of-Word (BoW) model consists of the following:

**1.** Vocabulary of words from the corpus, that is, BoW

**2.** Measure which assigns numeric value to words

The measures which attach a numeric value to the words may also be called word embeddings. Word embeddings can be simple frequency-based measures such as count of words in the document or a Boolean value representing presence/absence of the vocabulary in the document.

**Word embeddings**, intuitively, are measures which assigns numeric value to each word. The simplest of measures can be using ‘count’ of words in a document or ‘Boolean’ measure which shows presence or absence of words in a document.

![](images/page354-01.png)

**Word embeddings** in strict sense assigns values (a real valued vector which is in tens or hundreds of dimensions) to a word in such a way that words which are similar are given very similar values. This helps overcome issues with BoW representation (which can represent a word in millions of dimensions in case of huge corpus). BoW is still a useful concept in basic data representation and sentiment analysis.

The first step in creating a BoW model is the creation of a dictionary of all the words used in the corpus. We then select a measure to convert each document to a vector that assigns scores to words available in the document. There are four primitive frequency-based measures, aka word embeddings, which assign importance to the words in a BoW model.

**1.** Binary vector

**2.** Count Vector

**3.** TF Vector

**4.** TF-IDF Vector

#### Binary Vector

Consider the following two documents:

**1.** Document 1 (positive sentiment, coded as *y* = 1): I really really like IPL

**2.** Document 2 (negative sentiment, coded as *y* = 0): I never like IPL Note: IPL stands for the Indian Premier League, which is played every year.

The complete vocabulary set (aka dictionary) for the above two documents will have words **I, really, never, like**, and **IPL.** These words may be considered as features (x1 through x5). The number of words in the vocabulary defines the length of the vector which will be used to score the words in the document. In the above example, we can score the absence or presence of words in the document using 0/1 code as shown in **[Table 9.5](#17_Chapter09.xhtml#tab9.5).**

**[Table 9.5](#17_Chapter09.xhtml#tab9.5)** is called a term-document matrix. Intuitively, the term-document matrix is a bag of words for a set of documents (two documents in this case) where row represents a single document and column represents a single feature.

#### Count Vector

The problem with Boolean representation is that it gives equal weightage to words in a document, irrespective of the number of times they appear in the document. To overcome this issue, we can count the words rather than treating the words as Boolean values. For creating count vectors, we simply score the words in a document by counting the occurrence of each word as shown in **[Table 9.6](#17_Chapter09.xhtml#tab9.6).**

#### Term Frequency (TF) Vector

One of the potential issues with simple count vector is that the count of a word may be much more in a long document compared to the count of the same word in a short document. Thus, the words may get more weightage in analysis just by virtue of the document being long. So, it may be useful to normalize the count of words by dividing it by the count of total words in the document. This is called Term Frequency (TF) vector (Pradhan and Kumar, 2017) and is a measure of how frequently the word/term appears in a document. It is calculated for each document in the corpus by [Eq. (9.1)](#17_Chapter09.xhtml#eq9.1):

![](images/page354-02.png)![](images/page355-01.png)![](images/page355-02.png)

where, *TF.* is the term frequency for word.

Term frequency for the two documents in shown in **[Table 9.7](#17_Chapter09.xhtml#tab9.7).**

#### Term Frequency-Inverse Document Frequency (TF-IDF)

Common words may appear in higher frequency in a document and in the entire corpus. These common words may not be very important in identifying a pattern in the data. Less common words should have more weightage in the corpus. Term Frequency-Inverse Document Frequency (TF-IDF) measures the importance of a word in a document to the same word in the collection of documents (corpus). The importance increases proportional to the number of times a word appears in the document but is offset by the frequency of the word in the corpus. TF-IDF for a word in a document is given by [Eq. (9.2)](#17_Chapter09.xhtml#eq9.2):

![](images/page355-03.png)

where

• *TF*[*i*] is the term frequency for word

• *N* is the total number of documents in the corpus

• *N*[*i*] is the number of documents that contain the word *i*

The IDF value for each word in the above two documents is given in **[Table 9.8](#17_Chapter09.xhtml#tab9.8).**

The TF-IDF values for the two documents are shown in **[Table 9.9](#17_Chapter09.xhtml#tab9.9).**

Though the concept to convert unstructured data to structured data using BoW seems straightforward, we may face many challenges. For a very large corpus, say 500 sci-fi novels in English, the vocabulary set may run into thousands and millions of words.

![](images/page355-04.png)![](images/page355-05.png)

Techniques like feature hashing, word2vec, Glove are algorithms which helps create a **word representation** which reduce the dimensions in which a word is represented.

We may need a one-million feature vector to represent the BoW and then score each of the books using the BoW. This may require more memory for storage and at the same time become computationally expensive for modelling. Thus, we may want to reduce the size of the vocabulary to build the BoWs. Identifying the right set of words which we would like to retain as features in BoWs becomes important. A few approaches used to reduce the vocabulary are listed below:

**1.** Remove unwanted words from the text data. Remove punctuation marks in documents such as ‘,’ ‘,’ and ‘://’. These are generally taken care of by the functions from the tidytext package. In general, we can use regex to remove punctuations and unwanted words (non-contextual words).

**2.** Stemming and lemmatization, which may bring words in their root form, can also be helpful in reducing the BoW. This concept will be discussed in a later section.

**3.** Apart from unwanted words, remove English grammar articles, prepositions, and conjunction words such as ‘the’, ‘of’, ‘to’, ‘an’, ‘a’, and ‘in’. These are termed stop words. Stop words can be removed by creating a dictionary of stop\_words and filtering out these words from the BoWs.

There are several other challenges in cleaning a text data. Apart from implementing the above concepts, let us understand the other potential issues and their remedies using the twitter data in following sections.

### 9.7 | Twitter Data Visualization

We will use the covid\_twitter\_df and analyze the tweets. We would like to understand

**1.** Which users are tweeting the most?

**2.** What users are talking about in general? What specific users are talking about?

**3.** What is the source of information for the tweet? We can get this information by extracting the URLs in the text and performing certain preprocessing.

Let us get the answers to the above queries.

#### 9.7.1 Who Are the People Tweeting the Most?

We can get this information based on the screenName of the users. This is relatively straightforward. However, we can get two different answers to this query – one by including retweets, the other by excluding retweets. Let us plot the users tweeting the most (including retweets). Let us plot the top 40 users sorted by the number of tweets. **[Table 9.10](#17_Chapter09.xhtml#tab9.10)** shows the snapshot of the six users. The data can be represented using a simple bar plot (geom\_bar or geom\_col) from ggplot package. However, we are using a combination of point plot (geom\_point) and segment plot (geom\_segment) from ggplot package. This helps build a fancy chart called lollipop chart.

**TABLE 9.10** | Top six tweeters in covid with tweet count of more than 40

| screenName || *n* |
| --- | --- |
| ROBRAIPUR || 336 |
| --- | --- |
| PIBRaipur || 303 |
| NACOINDIA || 298 |
| BSDhruw2 || 293 |
| COVIDNewsByMIB || 255 |
| PIBKolkata || 253 |

![](images/page357-01.png)

From **[Figure 9.5](#17_Chapter09.xhtml#fig9.5)**, we see that Regional Outreach Bureau (ROB) Raipur, Press Information Bureau (PIB) Raipur, and Field Outreach Bureau (FOB) Bilaspur (BSDhruw2) seem to be very active.

![](images/page357-02.png)![](images/page358-01.png)

The National AIDS Control Organization also seems to be actively tweeting on this topic. Individuals by name kjayesh, vinyksr, and VasGiri are active as well.

Let us plot the top users with at least 100 tweets/retweets. Since the data is sorted based on the count of tweets, **[Figure 9.6](#17_Chapter09.xhtml#fig9.6)** will contain users who are a subset of users from **[Figure 9.5](#17_Chapter09.xhtml#fig9.5).**

![](images/page358-02.png)

Who are the active users if we exclude the retweets? Let us plot the top 40 users sorted by the number of tweets.

![](images/page358-03.png)![](images/page359-01.png)

We can compare **[Figure 9.7](#17_Chapter09.xhtml#fig9.7)** with **[Figure 9.5](#17_Chapter09.xhtml#fig9.5)** and see that there is not much of a retweet by COVIDNewsByMIB, but it is actively tweeting. Interestingly, kjayeshb seems to be actively retweeting rather than tweeting. Let us figure out if this is correct. **[Table 9.11](#17_Chapter09.xhtml#tab9.11)** shows the tweets by this user, and they mostly seem to be retweets with only the twitter handle mentioned in it. While text processing, such tweets will be deleted as they do not contain any textual information.

![](images/page359-02.png)

**TABLE 9.11** | First six tweets by a user kjayeshb

| Text || screenName |
| --- | --- |
| @COVIDNewsByMIB @FinMinIndia @MoHFW\_INDIA @drharshvardhan @PrakashJavdekar @PIBHomeAffairs @ PIB\_India @DDNewslive… [https://t.co/n1EHgJYGdL](https://t.co/n1EHgJYGdL) || kjayeshb |
| --- | --- |
| @COVIDNewsByMIB @FinMinIndia @MoHFW\_INDIA @drharshvardhan @PrakashJavdekar @PIBHomeAffairs @ PIB\_India @DDNewslive… [https://t.co/Tmhvas2TPN](https://t.co/Tmhvas2TPN) || kjayeshb |
| @COVIDNewsByMIB @FinMinIndia @MoHFW\_INDIA @drharshvardhan @PrakashJavdekar @PIBHomeAffairs @ PIB\_India @DDNewslive… [https://t.co/3I0UiT1c81](https://t.co/3I0UiT1c81) || kjayeshb |
| @COVIDNewsByMIB @ICMRDELHI @MoHFW\_INDIA @AyushmanNHA @drharshvardhan @DDNewslive @ airnewsalerts @PIB\_India… [https://t.co/5X0GTppdmG](https://t.co/5X0GTppdmG) || kjayeshb |
| @COVIDNewsByMIB @ICMRDELHI @MoHFW\_INDIA @AyushmanNHA @drharshvardhan @DDNewslive @ airnewsalerts @PIB\_India… [https://t.co/DJK9lodqUM](https://t.co/DJK9lodqUM) || kjayeshb |
| @MoHFW\_INDIA @PMOIndia @drharshvardhan @AshwiniKChoubey @PIB\_India @CovidIndiaSeva @COVID-NewsByMIB @mygovindia… [https://t.co/rA6dnhfEsc](https://t.co/rA6dnhfEsc) || kjayeshb |

![](images/page360-01.png)

In **[Table 9.12](#17_Chapter09.xhtml#tab9.12)**, we see that IndiaCovid19Bot, on the other hand, is giving hourly statistics about active and recovered cases. This textual data contains a lot of emojis as well. In the context of analysis being performed, we do not need digits, emojis, etc., and thus we will drop such words using regex.

![](images/page360-02.png)![](images/page360-03.png)

#### 9.7.2 What People Are Talking About

Getting an answer to this query requires the creation of a BoW data discussed in [Section 9.6.1](#17_Chapter09.xhtml#sec9.6.1). We will create BoW using the covid\_twitter\_df. We will use unnest\_tokens function from tidytext/tokenizer package to split the words of a document. These split words may be termed as tokens. Thus, token is a unit of text, for example, word, which we want to use in analysis. Tokenization is a process of splitting documents/text into tokens. The unnest\_token() expects the below function to be passed as parameters:

**1.** output – the column name to store the output after tokenization.

**2.** input – the input column name which is to be split. In this example, it is the column named ‘text’ in covid\_twitter\_df.

**3.** format – format of the document which is to be split. The default is text document. This supports split of ‘HTML, ‘XML, and ‘latex’ formats as well.

**4.** token – The unit for tokenizing. Default is ‘word’, which means splitting the document with every word.

The other values which can be passed are as follows:

> “characters”, “character shingles”, “ngrams”, “skip ngrams”, “sentences”, “lines”, “paragraphs”, “regex”, “tweets” (tokenization by word that preserves usernames, hashtags, and URLs), and “ptb” (Penn Treebank).

We will use token as ‘tweets’ to split by word but still preserve the usernames, hashtags, and URLs. We will also use strip\_url parameter to further remove the URLs being created as tokens. By default, every word stands individually in a token. However, tokens can also be a combination of words and are then called n-gram token, where *n* is the number of words appearing in combination.

By default, unnest\_tokens() converts the tokens to lowercase and punctuations are stripped. We can use to\_lower and strip\_punct parameters to change the default behaviour.

#### Cleaning the Tweets

Before using the unnest\_tokens() to split the data, let us understand some potential issues to deal with. We will use the below text to highlight all the issues discussed in this section and fix them sequentially.

![](images/page361-01.png)

**1.** One of the issues with twitter data is that most of the tweets will contain the twitter handle. We used #IndiaFightsCorona, @COVIDNewsByMIB, @covid19indiaorg, @ COVID19\_INDIA to pull the tweets. So, the tweets will contain these words a lot, but will not carry much information. The below regex takes care of words starting with ‘#’ or ‘@’. We will drop such words from the tweets.

Regex did the job perfectly.

![](images/page362-01.png)

**2.** The URLs in the tweets may not be needed in analysis and such URLs and unwanted words need to be removed as well. The below regex takes care of URLs and removes them.

![](images/page362-02.png)

**3.** There are certain words which may not be hashtags and URLs but still may not carry much meaning in analysis. We also do not need digits and punctuations in the text data. Let us create an expression to remove such words. We may not be able to identify all the less informative words upfront. It may take several iterations to identify less informative words and remove them.

![](images/page362-03.png)

Most of the expressions were discussed earlier but let us look at the regex “COVID(-?19)?”:

![](images/page362-04.png)

We will apply all three regex on the text simultaneously and see the result.

![](images/page363-01.png)

The above output shows that we have fixed some issues in the text data after applying all regex. However, we see still find some unicode text in the above output. This unicode corresponds to emoji ![](images/pageIn_ch9-02.png)and ![](images/pageIn_ch9-03.png). We also see some text in another language. We will handle these two issues as well.

**4.** A major issue with twitter data or, in general, social media data is the use of glyph/emoticons, for example, ![](images/pageIn_ch9-04.png), etc. These are referred to as Unicode character. Unicode is a character set which aims to define all characters and glyph (graphical representation) from all languages. Based on the purpose of analysis, we may or may not want to keep the glyph in the data. To remove the glyph, we can use Unicode in regex as below:

![](images/page363-02.png)

\\p is used to match emoticons. The character following it denotes the class to which the emoticons belong. Emojis belong to class ‘Other\_Symbol’ (So) and ‘Unassigned’ (Cn) class. ‘Math\_Symbol’ (Sm) and ‘Currency\_Symbol’ (Sc) also may be needed at times. The last expression in the above regex is to take care of emojis which are not being handled by \\p{xx} character class. For example, ![](images/pageIn_ch9-05.png)(question mark within square bracket) has an encoding of ‘\\U0001f3fd’ but is not being removed by \\p{xx}. In order to remove such special characters, we can use a range of Unicode character given by \[\\U{1F000}-\\U{1FFFF}\]. - ..

**5.** Twitter data is messy in terms of how users write the text. We will always see languages mixed up in the tweets. While dealing with the English language, we may need to remove words which are in non-English language. We can do the same by using regex as follows:

![](images/page363-03.png)

In ‘remove\_non\_english\_regex’ the expression “\[∧\\x01-\\x7F\] +”, matches ASCII character set (0-127, i.e., 0x0 to 0x7F). In Unicode, the same expression will be written as “\[∧\\u0000-\\u007F\]+”. This expression not only removes non-English words but also helps remove special/invisible characters and emoticons as well. So, Step 4 may be redundant too.

**6.** The word ‘RT’ also will appear in most of the tweets, which signifies that it is a retweet. We will filter out the retweets by using the filter() and str\_detect() function from dplyr and stringr.

**7.** We will remove these words by using an inbuilt BoW/lexicon of English grammar from the tidytext package by using anti\_join(). anti\_join() returns all rows from the tweet without a match in stop\_words.

The regex used in the above seven steps may need modification based on the text data being analyzed. Let us consider the above seven steps and split the text column in covid\_twitter\_df using the unnest\_token(). **[Table 9.13](#17_Chapter09.xhtml#tab9.13)** shows ten observations from the resulting table.

![](images/page364-01.png)![](images/page364-02.png)![](images/page365-01.png)

The vocabulary contains 4,444 words. Note that not applying regex before creating the token would have resulted in a vocabulary of 7,825 unique words. Thus, it would have created a vector of length 7,825 and consumed more memory.

#### 9.7.3 Visualise – Unigrams/Words

Let us try to understand what the high-frequency words used in the corpus?. **[Table 9.14](#17_Chapter09.xhtml#tab9.14)** shows the top six words occurring the maximum number of times. **[Figure 9.8](#17_Chapter09.xhtml#fig9.8)** shows the plot of the data.

![](images/page365-02.png)

**TABLE 9.14** | High-frequency words

| Word || *n* |
| --- | --- |
| Follow || 316 |
| --- | --- |
| Active || 300 |
| Mask || 261 |
| deaths || 243 |
| Hands || 230 |
| swachhbharat || 228 |

We will plot the top 50 words in the word\_tokens with a token count of more than 40. This slice of data is being pulled from ‘word\_tokens’ by applying filter() and then slice\_max() from dplyr package. Further, while plotting the data, we will show the frequency count of 100+ in the forward direction and a frequency count of less than 100 in the backward direction. This is done by setting the *y* parameter of geom\_segment to 100. **[Figure 9.8](#17_Chapter09.xhtml#fig9.8)** shows the plot of the data.

![](images/page365-03.png)![](images/page366-01.png)

In the above code snippet, the filter() function is redundant as the top 50 words being pulled out using the slice\_max() have all got a count of more than 40. However, this may not be true for any other dataset. From **[Figure 9.8](#17_Chapter09.xhtml#fig9.8)**, we can conclude that

**1.** General perception towards hygiene is evident with the use of words like mask, wear, hands, wash, social, distancing, clean, don’t, etc.

**2.** People seem to be talking a lot about swachh bharat, PM (prime minister).

**3.** People are talking about deaths and recovery. The use of these words in tweets may reflect a general mood of apprehension and a cautious approach while dealing with COVID-19.

**[Figure 9.9](#17_Chapter09.xhtml#fig9.9)** shows the plot of the last 50 words in the token with a count of 40 and more.

![](images/page367-01.png)![](images/page367-02.png)

The plots we saw so far were based on a simple count of words in the BoW (twitter\_words). However, we can take the count of words by each user (screenName) as well. Here, the screenName may be thought of as a document (discussed in [Section 9.6.1](#17_Chapter09.xhtml#sec9.6.1)) by which we will want to get the count. Let us get the users (screenName) who have several tweets (total words in tweet more than 100) and understand the words being used by them. The data can be prepared using the following steps:

**1.** Using twitter\_words dataframe:

– Select screenName and word column and get a count of all the words using count().

– Group the data by screenName using group\_by().

– Create a new column which stores the total words written by the user. This can be done by mutate().

– Filter the tweets with a total word count of more than 100. Use filter() function to achieve this.

– Select the top seven records from every user, using the slice\_max().

– Ungroup the data using ungroup().

– Arrange the data *y* screenName and count of word using arrange().

– Create a column named ‘order’ which keeps track of the order/arrangement done in previous steps.

The last three steps are optional and are carried out to show the plot of words in a sorted order while using the facet\_wrap of ggplot in **[Figure 9.10](#17_Chapter09.xhtml#fig9.10). [Table 9.15](#17_Chapter09.xhtml#tab9.15)** shows the list of users obtained using the above-mentioned steps. This data will give us an idea of what avid twitteratis are talking about.

![](images/page368-01.png)

**[Figure 9.10](#17_Chapter09.xhtml#fig9.10)** shows the plot of the data from **[Table 9.16](#17_Chapter09.xhtml#tab9.16).**

![](images/page368-02.png)![](images/page369-01.png)![](images/page369-02.png)![](images/page370-01.png)![](images/page370-02.png)

From **[Figure 9.10](#17_Chapter09.xhtml#fig9.10)**, we can see that there are

**1.** Many users who have used swachhbharat more than 20 times in their tweets. They may be trying to promote the swachhbharat abhiyaan through the corona handles.

**2.** BaharBharat is mostly talking about flight operations and updates.

**3.** DDIndialive seems to be using words which indicate providing status update on COVID-19. However, DDSaptagirvja seems to be promoting some other content on its channel.

**4.** Most of the users seem to be creating awareness to remain safe during the pandemic times. The users mostly seem to be government or news channel twitter handles.

**5.** IndiaCovidBot seems to be using only a few words very frequently. A look at the data shows that this Bot is tweeting only about the recovery and death numbers on an hourly basis. Since we cleaned up the text (no digits, etc.), we only see the words appearing in the visualization.

**6.** The church seems to be spreading a lot of awareness in Ukhrul district through the PIBImphal twitter handle.

**[Figure 9.11](#17_Chapter09.xhtml#fig9.11)** shows the plot of data from the same **[Table 9.16](#17_Chapter09.xhtml#tab9.16)** but in an unsorted way. Readers are encouraged to compare the differences between **[Figures 9.10](#17_Chapter09.xhtml#fig9.10)** and **[9.11](#17_Chapter09.xhtml#fig9.11)** and find out the reason for the difference in the code snippet.

![](images/page371-01.png)![](images/page372-01.png)

Since we have built the ‘twitter\_word\_count’ dataframe in such a way that it has got information about all the users and words used by them, we can get a view of a different set of users whose tweets contained words between 50 and 100. **[Figure 9.12](#17_Chapter09.xhtml#fig9.12)** shows the plot for such users.

![](images/page372-02.png)

We can see from **[Figure 9.12](#17_Chapter09.xhtml#fig9.12)** that there are a few individual users too who tweet a lot on this topic. This was not the case in **[Figure 9.11](#17_Chapter09.xhtml#fig9.11)** , where it was mostly government agencies or news channels.

#### 9.7.4 Improve the BoW – Stemming and Lemmatization

From **[Figure 9.12](#17_Chapter09.xhtml#fig9.12)**, we see the words used by the users who wrote more than 100 words on the COVID-19 topic. However, we could have done better in the BoW creation had we also taken care of the following:

![](images/page373-01.png)

**1.** Many words appear in multiple forms and hence result in increasing the vocabulary (BoW). If the word has a similar meaning in all its forms, we can use only the root word as a feature or BoW. Stemming and lemmatization are two popular techniques to solve this.

– Words like recovery and recovered appear in the token. These words could have been taken to their root form, that is, recover. This is done through a process of lemmatization.

– Words like distancing and distance also appear in the top 100 words. We could have stemmed these words to root form, that is, distance. This is done through the process of stemming.

**2.** We could have removed words like october, oct, day, days, people, etc. We leave it for the readers to clean such words and visualize the data.

#### Stemming

Stemming removes the differences between inflected forms of a word to reduce each word to its root form (Pradhan and Kumar, 2019). This is done by mostly chopping off the end of words. For instance, ‘distancing’ will be reduced to the root word ‘distance’. The root form of a word may not even be a real word. For example, ‘awesome’ and ‘awesomeness’ will be stemmed to awesom. One problem with stemming is that chopping of words may result in words that are not part of the dictionary (for example, awesom). Porter stemmer and Lancaster stemmer are two popular algorithms for stemming, which have rules on how to chop off a word. library(SnowballC) implements porter stemmer through wordStem().

#### Lemmatization

Lemmatization takes the morphological analysis of the words into consideration. It uses a dictionary to convert the words to the root word (Pradhan and Kumar, 2019). For example, stemming would fail to differentiate between ‘man’ and ‘men, while lemmatization can bring these words to their original form – man. library(textstem) implements lemmatization through lemmatize\_words().

We will implement all the above-mentioned concepts on the covid\_twitter\_df. The following code snippet helps create unigrams shown in **[Table 9.17](#17_Chapter09.xhtml#tab9.17).**

![](images/page374-01.png)

**TABLE 9.17** | Unigram words

| screenName || word |
| --- | --- |
| mygovindia || festiv |
| --- | --- |
| mygovindia || reason |
| mygovindia || forget |
| mygovindia || fight |
| mygovindia || pandem |
| mygovindia || precauti |
| MoHFW\_INDIA || activ |
| MoHFW\_INDIA || fall |
| MoHFW\_INDIA || week |
| MoHFW\_INDIA || continu |

**TABLE 9.18** | Top six observations from twitter word stem dataframe

| word || *n* |
| --- | --- |
| activ || 333 |
| --- | --- |
| follow || 316 |
| hand || 299 |
| mask || 288 |
| death || 266 |
| recoveri || 241 |

![](images/page375-01.png)

We can see that the additional steps of stemming and lemmatization have led to reducing the vocabulary from 4,444 words to 3,562 words. **[Table 9.18](#17_Chapter09.xhtml#tab9.18)** shows the count of words from the ‘twitter\_words\_stem’ dataframe.

![](images/page375-02.png)

#### Visualize – Stemmed and Lemmatized Words

Let us plot the top 50 words in the word\_tokens with a token count of more than 40. This slice of data is being pulled from ‘word\_tokens’ by applying filter() and then slice\_max() from dplyr package. Further, while plotting the data, we are showing a token count of 100+ in the forward direction and a token count of less than 100 in the back-ward direction. This is being done by setting the *y* parameter of geom\_segment to 100.

**[Figure 9.13](#17_Chapter09.xhtml#fig9.13)** shows the plot of the data.

![](images/page375-03.png)

Comparing **[Figure 9.13](#17_Chapter09.xhtml#fig9.13)** with **[Figure 9.9](#17_Chapter09.xhtml#fig9.9)**, we can see that there is a change in the frequency of certain words due to the additional steps of stemming and lemmatization.

Here too, the plots we saw so far were based on the simple count of words in the BoW (twitter\_words). As described in [Section 9.7.3](#17_Chapter09.xhtml#sec9.7.3), we will plot the words by user here also. Let us get the users (screenName) who have several tweets (total words in tweet more than 100) and understand the words being used by them. Data can be prepared using the following steps:

![](images/page376-01.png)

**1.** Using twitter\_word\_stem dataframe:

– Select screenName and word column and get a count of all the words using count()

– Group the data by screenName using group\_by()

– Create a new column which stores the total words written by the user. This can be done by mutate()

– Filter the tweets with a total word count of more than 100. Use filter() function to achieve this.

– Select the top seven records for every user, using the slice\_max()

– Ungroup the data using ungroup().

– Arrange the data by screenName and count of word using arrange().

– Create a column named ‘order’ which keeps track of the order/arrangement done in previous steps.

![](images/page377-01.png)

The last three steps are optional and are being carried out to show the plot of words in a sorted order within the facet\_wrap of ggplot in **[Figure 9.14](#17_Chapter09.xhtml#fig9.14). [Tables 9.19](#17_Chapter09.xhtml#tab9.19)** and **[9.20](#17_Chapter09.xhtml#tab9.20)** show the list of users obtained using the above-mentioned steps.

![](images/page377-02.png)![](images/page378-01.png)![](images/page378-02.png)![](images/page378-03.png)

The word ‘appeal, which did not appear in the word plot for PIBImphal (in **[Figure 9.11](#17_Chapter09.xhtml#fig9.11))**, shows up in **[Figure 9.14](#17_Chapter09.xhtml#fig9.14).** This suggests that stemming and lemmatization helped improve vocabulary counts.

#### 9.7.5 Improve BoW – TF-IDF

So far, we have created word tokens by removing stop words, and used the frequency count of words to visualize the data. In [Section 9.6.1](#17_Chapter09.xhtml#sec9.6.1), we understood the potential issues of using count vector and discussed creating Term Frequency- Inverse Document Frequency (TF-IDF) as a possible resolution. Within a collection of documents (here, screenName), TF-IDF tries to identify words that are important to one document (user/screenName). Let us implement the TF-IDF concept. **[Table 9.21](#17_Chapter09.xhtml#tab9.21)** shows the count of words by screenName.

![](images/page379-01.png)

Here, we use screenName as analogous to a document (as discussed in [Section 9.6.1](#17_Chapter09.xhtml#sec9.6.1)). Multiple tweets from the same user (screenName) create multiple ‘IDs’. In a later section, we will use ‘ID’ column of the ‘covid\_twitter\_df’ to represent a document. The twitter\_words\_tf dataframe thus created has a total of 3,562 unique words tweeted by 1,204 unique users.

![](images/page379-02.png)![](images/page379-03.png)![](images/page380-01.png)

Let us also create a feature which shows the total words used by the users in the tweet. **[Table 9.22](#17_Chapter09.xhtml#tab9.22)** shows the outcome of the below code snippet.

![](images/page380-02.png)

Each row of **[Table 9.22](#17_Chapter09.xhtml#tab9.22)** represents a user-word combination where *n* represents the number of times the word is used by the user and total\_words\_user represents the total number of words used by the user. We can calculate the term frequency as n/total\_words\_user. However, we have bind\_tf\_idf() function from tidytext package which can give us term frequency as well as inverse document frequency. **[Table 9.23](#17_Chapter09.xhtml#tab9.23)** shows the TF-IDF for each token.

![](images/page380-03.png)![](images/page380-04.png)![](images/page380-05.png)

In the below code snippet, we computed the IDF, using [Eq. (9.2)](#17_Chapter09.xhtml#eq9.2), for the word ‘death’ and it matches the value mentioned in **[Table 9.23](#17_Chapter09.xhtml#tab9.23).**

![](images/page381-01.png)

Let us take users who have several tweets (total words in tweet more than 100) and understand the words used by them. From this list of users, we will select the top seven words for each user. The data can be prepared using the following steps:

Using twitter\_word\_tf dataframe:

– Filter the tweets with a total word count of more than 100. Use filter() function to achieve this.

– Select the top seven records for every user, using thee slice\_max()

– Ungroup the data using ungroup().

– Arrange the data by screenName and count of word using arrange ().

– Create a column named ‘order’ which keeps track of the order/arrangement done in previous steps.

**[Table 9.24](#17_Chapter09.xhtml#tab9.24)** shows a subset of users obtained using the above-mentioned steps.

![](images/page381-02.png)![](images/page382-01.png)

The benefits of TF-IDF are evident from **[Table 9.24](#17_Chapter09.xhtml#tab9.24).** Within the group (screenName), we have words whose count is less but their TF-IDF value is high. **[Figure 9.15](#17_Chapter09.xhtml#fig9.15)** shows the plot of the data from **[Table 9.24](#17_Chapter09.xhtml#tab9.24).**

![](images/page382-02.png)

Comparing **[Figure 9.15](#17_Chapter09.xhtml#fig9.15)** with **[Figure 9.14](#17_Chapter09.xhtml#fig9.14)**, we notice that there are some changes in the words getting picked up as high-frequency words.

**1.** From **[Figure 9.14](#17_Chapter09.xhtml#fig9.14)**, we see that for the user BaharBharat, words such as ‘Flights, International, October, Operated, Important’ emerged as the top five words. However, for the same user in **[Figure 9.15](#17_Chapter09.xhtml#fig9.15)**, we see ‘flight, international, operation, travel, announcement’ being shown as the top five words.

![](images/page383-01.png)

**2.** From **[Figure 9.14](#17_Chapter09.xhtml#fig9.14)**, we see that for the user PIBImphal, the top five words were ‘follow, ukhrul, people, baptist, church. However, for the same user in **[Figure 9.15](#17_Chapter09.xhtml#fig9.15)**, ‘ukhrul, baptist, church, pastor, appeal’ are the top five words. Since ‘follow’ is a common word and may have been used many times by several users, the TF-IDF value would have been offset, thus the reason for it being knocked off the list.

#### 9.7.6 Improve BoW – Using n-grams

The analysis so far used each token or word individually. But the meaning of some of the words might be dependent on the words that precede or succeed them, such as, ‘not happy’. It should be considered as one feature and not two different features. n-gram is a contiguous sequence of *n* words. When two consecutive words are treated as one feature, it is called a bigram; three consecutive words is called a trigram and so on (Pradhan and Kumar, 2019). We will use unnest\_token() to create a bigram. Note that while creating bigrams, we have not used the concepts of stemming and lemmatization. **[Table 9.25](#17_Chapter09.xhtml#tab9.25)** shows the output of the below code.

**TABLE 9.25** | Bigram tokens

| screenName || bigram |
| --- | --- |
| \_\_\_\_alpha96 || i think |
| --- | --- |
| \_\_\_\_alpha96 || think i |
| \_\_\_\_alpha96 || i just |
| \_\_\_\_alpha96 || just drew |
| \_\_\_\_alpha96 || drew the |
| \_\_\_\_alpha96 || the future |
| \_\_\_\_alpha96 || future is |
| \_\_\_\_alpha96 || is it |
| \_\_\_\_alpha96 || it or |
| \_ashoka\_tech || hope agrees |

![](images/page384-01.png)

Stemming, lemmatization of words and TF-IDF as a measure of word count may significantly improve the **BoW representation** and in visualizing important words.

**TABLE 9.26** | Bigram after removal of stop words

| screenName || Bigram |
| --- | --- |
| \_ashoka\_tech || hope agrees |
| --- | --- |
| \_ashoka\_tech || awarded hope |
| \_ashoka\_tech || hope agrees |
| \_ashoka\_tech || hope agrees |
| \_ashoka\_tech || hope agrees |
| \_sunnyrai || cover spike |
| 03Rajak || fight coro |
| 03Rajak || simple steps |
| 03Rajak || steps wear |
| 03Rajak || mask wash |

We created bigrams, but they have stop words. We will perform additional processing to remove the stop words and recreate the bigrams. We will follow the below steps to do so:

Using intermediate bigram

– split the bigram into two words. This can be done using separate() from tidyr.

– remove stop words from separated words using stop\_words lexicon from tidy-text.

– merge the two words to form the bigram again. This can be done using unite() from tidyr.

**[Table 9.26](#17_Chapter09.xhtml#tab9.26)** shows the resulting outcome using the above steps.

![](images/page385-01.png)

**TABLE 9.27** | Frequently used bigrams

| bigram || *n* |
| --- | --- |
| active recovered || 105 |
| --- | --- |
| wash hands || 82 |
| social distancing || 81 |
| recovery rate || 67 |
| jan andolan || 66 |
| preventive measures || 64 |

#### 9.7.7 Visualize Bigrams

Let us get the count of bigrams where there are at least 20 occurrences and plot it **([Table 9.27](#17_Chapter09.xhtml#tab9.27)).**

![](images/page386-01.png)

From **[Figure 9.16](#17_Chapter09.xhtml#fig9.16)**, we can see that

**1.** Words like recovery rate, wash hands, social distancing, and preventive measures have been mentioned in many tweets.

**2.** Some of the tweets also mention festive season, mental health, October, and steady.

By now, we have analyzed words by each user (screenName) several times. We will do the same for bigrams as well. Let us get the users (screenName) who have several tweets (total words in tweet more than 100) and understand the bigrams used by them. The data can be prepared using the following steps:

Using twitter\_bigram dataframe:

– Select screenName and word column and get a count of all the words using count()

– Group the data by screenName using group\_by()

– Create a new column which stores the total words written by the user. This can be done by mutate()

– Create a new column which stores the IDF and TF-IDF for the bigrams. This can be done by bind\_tf\_idf().

– Filter the tweets with a total word count of more than 100. Use filter() function to achieve this.

– Select the top seven records for every user, using the slice\_max()

– Ungroup the data using ungroup().

– Arrange the data by screenName and count of word using arrange().

![](images/page387-01.png)

– Create a column named ‘order’ which keeps track of the order/arrangement done in previous steps.

Let us plot the bigrams by user, using count as well as TF-IDF.

![](images/page387-02.png)![](images/page388-01.png)

**[Table 9.28](#17_Chapter09.xhtml#tab9.28)** shows the top seven records based on count (*n*).

![](images/page388-02.png)

**[Figure 9.17](#17_Chapter09.xhtml#fig9.17)** shows the count based on the top seven records for each user based on frequency (variable *‘n’).*

![](images/page388-03.png)

**[Table 9.29](#17_Chapter09.xhtml#tab9.29)** shows the top seven records based on TF-IDF.

![](images/page388-04.png)![](images/page389-01.png)![](images/page389-02.png)

The plot of data from **[Table 9.29](#17_Chapter09.xhtml#tab9.29)** is shown in **[Figure 9.18](#17_Chapter09.xhtml#fig9.18).**

![](images/page389-03.png)![](images/page390-01.png)![](images/page390-02.png)

Comparing **[Figures 9.17](#17_Chapter09.xhtml#fig9.17)** and **[9.18](#17_Chapter09.xhtml#fig9.18)**, we can see that the order of the bigrams has changed for a few users but the overall list remains the same. TF-IDF does not seem to make a difference in the bigrams as it will be rare that two users (screenName) will tweet using the combination of the same two words in the same order. Thus, the count of bigrams may not get offset by the frequency of use of the same bigram by other users (document).

#### 9.7.8 Count Vector vs. Count Vector with Stemming and Lemmatization vs. TF-IDF Vector

Count vector, Count vector with Stemming, and Lemmatization and TF-IDF Vector are three different ways to create word embeddings in a BoW model. These three ways to measure the importance of a word finally help create a word vector for a document. The ranking of the word within the document changes based on the measure selected. Let us deep dive into the tweets from user ‘PIBImphal. For PIBImphal, the count of words in twitter\_word\_count, twitter word stem count and twitter word tf count is 551. For the PIBImphal, let us compare **[Tables 9.30](#17_Chapter09.xhtml#tab9.30)** and **[9.31](#17_Chapter09.xhtml#tab9.31):**

**1.** **[Table 9.30](#17_Chapter09.xhtml#tab9.30)** without stemming and lemmatization shows ‘church’ and ‘urges’ as two words in the first six records sorted by ***‘n’.***

**2.** **[Table 9.31](#17_Chapter09.xhtml#tab9.31)** with stemming and lemmatization shows ‘appeal’ and ‘minist’ as two words in the first six records sorted by *‘n’.*

![](images/page391-01.png)![](images/page391-02.png)![](images/page391-03.png)![](images/page392-01.png)

The stemming and lemmatization process brought words

**1.** ‘appeals’ and ‘appealed’ in their root form ‘appeal’ and thus increased the count of the word ‘appeal’.

**2.** ‘minister’ and ‘ministers’ in their root form ‘minist’, thus showing a count of eight.

This resulted in knocking off the last two records from **[Table 9.30](#17_Chapter09.xhtml#tab9.30)** and offered a clear indication of how word ordering may get changed due to stemming and lemmatization.

The use of TF-IDF helps extract words which are characteristics of a particular user (screenName) within a collection of users who tweeted on the same topic. To validate the statement, let us compare **[Tables 9.30](#17_Chapter09.xhtml#tab9.30)** and **[9.32](#17_Chapter09.xhtml#tab9.32):**

**1.** **[Table 9.30](#17_Chapter09.xhtml#tab9.30)** without stemming and lemmatization shows ‘follow’ and ‘peopl’ as two words in the first seven records sorted by *‘n’.*

**2.** **[Table 9.32](#17_Chapter09.xhtml#tab9.32)** with stemming and lemmatization plus TF-IDF shows ‘church’ and ‘pastor’ as two words in the first seven records sorted by *‘n’.*

Based on TF-IDF, we can see words like ‘church’ and ‘pastor’ in **[Table 9.32](#17_Chapter09.xhtml#tab9.32)** which is much more relevant in tweets from PIBImphal, compared to words like ‘follow’ and ‘people’ which may have been used by many users in the corpus. In **[Table 9.30](#17_Chapter09.xhtml#tab9.30)**, ‘follow’ with a count of13 could not make it to the top seven records in **[Table 9.32](#17_Chapter09.xhtml#tab9.32).** At the same time, ‘pastor’ with just six counts was ranked higher than minist in **[Table 9.32](#17_Chapter09.xhtml#tab9.32)** (table sorted in ascending order of TF-IDF).

![](images/page392-02.png)

The BoW has its own shortcomings but is a useful way for visualization of textual data. The BoW model can also help build basic prediction-based models (discussed in later sections). However, let us continue with the last query on the twitter data.

#### 9.7.9 What Is the Source of Information for the Tweet?

We can get this information by extracting the URLs in the text and performing certain preprocessing. Let us try to understand the source of information for twitter users under the hashtags they use. Since we will filter out the URLs from the tokens, we can remove the regex being used to clean the text.

![](images/page392-03.png)

**TABLE 9.33** | URLs with count more than 8

| short\_url || *n* |
| --- | --- |
| [https://t.co/QdOXQvzaPw](https://t.co/QdOXQvzaPw) || 95 |
| --- | --- |
| [https://t.co/ZaoOX3zu8V](https://t.co/ZaoOX3zu8V) || 65 |
| [https://t.co/PifpGVT6aq](https://t.co/PifpGVT6aq) || 60 |
| [https://t.co/M7AtMQCb4X](https://t.co/M7AtMQCb4X) || 40 |
| [https://t.co/ThENRZufhO](https://t.co/ThENRZufhO) || 37 |
| [https://t.co/4wc8k5IK4Z](https://t.co/4wc8k5IK4Z) || 29 |
| [https://t.co/lz6nVuk49T](https://t.co/lz6nVuk49T) || 26 |
| [https://t.co/ATU35sj129](https://t.co/ATU35sj129) || 18 |
| [https://t.co/4ZLdC85LU0](https://t.co/4ZLdC85LU0) || 17 |
| [https://t.co/4tQTPmvkfZ](https://t.co/4tQTPmvkfZ) || 16 |
| [https://t.co/PQHKrABmiZ](https://t.co/PQHKrABmiZ) || 13 |
| [https://t.co/WZpI4l9ECd](https://t.co/WZpI4l9ECd) || 11 |
| [https://t.co/CdH9aoQMzJ](https://t.co/CdH9aoQMzJ) || 9 |
| [https://t.co/CwXmsvrZHA](https://t.co/CwXmsvrZHA) || 9 |
| [https://t.co/izIfYcXdwh](https://t.co/izIfYcXdwh) || 9 |
| [https://t.co/kF2gyMK8qK](https://t.co/kF2gyMK8qK) || 9 |
| [https://t.co/NTYXhRNfkD](https://t.co/NTYXhRNfkD) || 9 |
| [https://t.co/3xeX1j11z4](https://t.co/3xeX1j11z4) || 8 |
| [https://t.co/HIQ3LxCpJf](https://t.co/HIQ3LxCpJf) || 8 |
| [https://t.co/WRggJbZOda](https://t.co/WRggJbZOda) || 8 |

We will filter out url\_tokens with a count more than eight and extract the actual URL links using httr package. **[Table 9.33](#17_Chapter09.xhtml#tab9.33)** shows the URL with a count more than eight.

![](images/page393-01.png)

The short url in **[Table 9.33](#17_Chapter09.xhtml#tab9.33)** can be expanded using the below code snippet. **[Table 9.34](#17_Chapter09.xhtml#tab9.34)** shows the expanded url.

![](images/page393-02.png)

**TABLE 9.34** | First six observations of expanded URLs

| url || status\_code |
| --- | --- |
| [https://twitter.com/MoHFW\_INDIA/status/1316278631321100289/photo/1](https://twitter.com/MoHFW_INDIA/status/1316278631321100289/photo/1) || 400 |
| --- | --- |
| [https://twitter.com/mygovindia/status/1316602805818257410/photo/1](https://twitter.com/mygovindia/status/1316602805818257410/photo/1) || 400 |
| [https://twitter.com/mygovindia/status/1315610983793008640/photo/1](https://twitter.com/mygovindia/status/1315610983793008640/photo/1) || 400 |
| [https://twitter.com/mygovindia/status/1315616867776491520/photo/1](https://twitter.com/mygovindia/status/1315616867776491520/photo/1) || 400 |
| [https://twitter.com/mygovindia/status/1316596832928055297/photo/1](https://twitter.com/mygovindia/status/1316596832928055297/photo/1) || 400 |
| [https://twitter.com/MoHFW\_INDIA/status/1317424639295909888/photo/1](https://twitter.com/MoHFW_INDIA/status/1317424639295909888/photo/1) || 400 |

Let us bind the URL links with the short URLs. **[Table 9.35](#17_Chapter09.xhtml#tab9.35)** shows the short URL and the corresponding URL link.

![](images/page394-01.png)

We will extract the domain from URL link and count the domains. The use of gsub() and regex explained in previous sections will be used to extract the URL links. **[Table 9.36](#17_Chapter09.xhtml#tab9.36)** shows the domain name and number of times it appeared.

![](images/page394-02.png)

#### 9.7.10 Visualize URL

**[Figure 9.19](#17_Chapter09.xhtml#fig9.19)** shows the plot for common domains in tweets using ggplot.

![](images/page394-03.png)![](images/page394-04.png)

**TABLE 9.36** | Domain count

| domain || domain\_count |
| --- | --- |
| twitter.com || 448 |
| --- | --- |
| pledge.mygov.in || 24 |
| livemint.com || 16 |
| blog.mygov.in || 8 |

![](images/page395-01.png)

**[Figure 9.19](#17_Chapter09.xhtml#fig9.19)** shows that in a majority of the cases, information for tweets link to the twitter source itself. We may also want to understand the hashtags used by users while retweeting. We leave it for the readers to try it out.

### 9.8 | Sentiment Analysis

After having created the BoW model and with the understanding of basic word embed-dings, let us delve into the other topic which is of interest in text analytics. Sentiment of the users regarding a particular topic is of great interest. In this case, we want to know the emotions of the users on topics related to COVID-19. Through human intelligence, one can read through the tweets and get an understanding of the emotion reflected by the user. It could be a positive/negative tweet or a happy/neutral/sad tweet, etc. But it will be overwhelming for a human being to read through all the tweets and tag the tweets to reflect emotional intent.

Tidytext comes with inbuilt lexicon (available through textdata package) which can help categorize the tweet into one of the predefined tags of emotion. Four general-purpose lexicons in tidytext are as follows:

**1.** Afinn – This lexicon from Finn Årup Nielsen (Nielsen, 2011) categorizes 2,477 unique unigrams on a score of −5 (negative sentiment) to 5 (positive sentiment). This is licensed under Open Database License (ODbL) v1.0. **[Table 9.37](#17_Chapter09.xhtml#tab9.37)** shows six observations from afinn lexicon.

![](images/page395-02.png)

**TABLE 9.37** | First six observations from afinn lexicon

| Word || value |
| --- | --- |
| Abandon || −2 |
| --- | --- |
| Abandoned || −2 |
| abandons || −2 |
| abducted || −2 |
| abducted || −2 |
| abducted || −2 |

**TABLE 9.38** | First six words from nrc lexicon

| Word || sentiment |
| --- | --- |
| abacus || trust |
| --- | --- |
| abandon || fear |
| abandon || negative |
| abandon || sadness |
| abandoned || anger |
| abandoned || fear |

**1.** Nrc – This lexicon from Saif Mohammad and Peter Turney (2013) categorizes words under the labels ‘trust’, ‘fear’, ‘negative’, ‘sadness’, ‘anger’, ‘surprise’, ‘positive’, ‘disgust’, ‘joy’, and ‘anticipation’. It is by far the most comprehensive, having categorized 6,468 unigrams under these labels. A word can have a mapping to more than one label. This dataset requires license for commercial use. **[Table 9.38](#17_Chapter09.xhtml#tab9.38)** shows six observations from nrc lexicon.

![](images/page396-01.png)

**2.** Bing – This lexicon from Bing Liu (2015) and collaborators categorizes words in binary fashion, that is, positive/negative, that is, two unique labels. It has categorized 6,783 unigrams under these labels. By default, only this lexicon is available as a part of the tidytext. **[Table 9.39](#17_Chapter09.xhtml#tab9.39)** shows six observations from bing lexicon (S Biguzzi, 2020).

![](images/page396-02.png)

**3.** lougharn – This lexicon from Loughran-McDonald (2019) categorizes words under the labels ‘negative’, ‘positive’, ‘uncertainty’, ‘litigious’, ‘constraining’, and ‘superfluous’. The lexicon has categorized 3,917 English words under these emotional intents. Words may have a mapping under more than one label. This lexicon requires license for commercial use. **[Table 9.40](#17_Chapter09.xhtml#tab9.40)** shows six observations from lougharn lexicon.

![](images/page396-03.png)

We need to install textdata package to access ‘afinn’, ‘nrc’, and ‘loughran’ lexicon. The get\_sentiments() function internally uses textdata::lexicon\_afinn(), tex-tdata::lexicon nrc(), textdata::lexicon loughran() to download these lexicons and make it available for use. All the above lexicons were constructed and validated by the authors of the lexicons, using crowd-sourcing platforms. The advantage of using these lexicons is that we can quickly arrive at the sentiments from a corpus. The disadvantage is that the accuracy of the sentiments may be questionable if the style of writing in a corpus is very different (say, a book which is 100 years old and we use the above lexicon to decide on the sentiments being expressed in the book).

**TABLE 9.39** | First six words from bing lexicon

| Word || sentiment |
| --- | --- |
| 2-faces || negative |
| --- | --- |
| abnormal || negative |
| abolish || negative |
| abominable || negative |
| abominably || negative |
| abominate || negative |

**TABLE 9.40** | First six words from lougharn lexicon

| Word || sentiment |
| --- | --- |
| abandon || negative |
| --- | --- |
| abandoned || negative |
| abandoning || negative |
| abandonment || negative |
| abandonments || negative |
| abandons || negative |

These lexicons are based on unigrams and thus the emotions are at unigram level. The sentiment of the tweet (represented as a BoW) may be arrived at by combining the sentiment of the unigrams. We will use the ‘nrc’ lexicon to perform sentiment analysis on the covid data. We will understand the sentiments expressed by users (screenName) who tweeted multiple times with 50 to 100 words in tweets. The ‘twitter\_word\_count’ object from [Section 9.7.3](#17_Chapter09.xhtml#sec9.7.3) contains the unigrams created using unnest\_token(). **[Table 9.41](#17_Chapter09.xhtml#tab9.41)** shows the top 20 rows by users who tweeted between 50 and 100 words.

![](images/page397-01.png)![](images/page397-02.png)

There are 45 unique users in the tweet sentiment df.

![](images/page398-01.png)

Let us get the emotions of the user. The labels in nrc lexicon are as follows: ‘trust, ‘fear, ‘negative, ‘sadness, ‘anger, ‘surprise, ‘positive, ‘disgust, ‘joy, and ‘anticipation’. Let us look at the tweets which reflect ‘sadness, We will follow the following steps:

**1.** Get words from ‘nrc’ lexicon which reflect sadness and store them in a variable ‘nrc\_sad’.

**2.** Perform an inner\_join of ‘tweet\_sentiment\_df’ with ‘nrc\_sad’ and count the words reflecting sad emotion.

The below code will be used to apply the above-mentioned steps.

![](images/page398-02.png)

The dimension of ‘tweet\_sad’ suggests there are only 41 words which matched the emotion of sadness as in nrc lexicon.

![](images/page398-03.png)

**[Table 9.42](#17_Chapter09.xhtml#tab9.42)** shows the first 10 words.

![](images/page398-04.png)![](images/page398-05.png)

**Pre-built dictionaries** can significantly reduce manual intervention of the labeling of data for performing sentiment analysis. Dictionaries like Afinn, Bing, Nrc, made available through tidytext and textdata package, may be used for understanding the sentiments expressed in a textual information.

**TABLE 9.43** | First 10 observations from modified stop\_words lexicon

| word || lexicon |
| --- | --- |
| music || custom |
| --- | --- |
| feeling || custom |
| lowest || custom |
| a || SMART |
| a’s || SMART |
| able || SMART |
| about || SMART |
| above || SMART |
| according || SMART |
| accordingly || SMART |

Using the nrc lexicon, we can analyze the text for any of the emotional quotient defined by the words in it. We encourage readers to change the above code snippet to try for emotions like ‘anger’, surprise’, and ‘positive’. From **[Table 9.42](#17_Chapter09.xhtml#tab9.42)**, we can see users (screenName) who reflect sad emotions in their tweet.

**1.** Words such as negative, evil, lowest, accident, hospital, etc., show up in the tweets and reflect sad emotions.

**2.** We also see words such as music, feeling, lowest, etc., appearing in the tweets, which may not be a sad emotion in the context of the covid data.

One of the ways to deal with words with misclassified emotion could be as follows:

**1.** Add such words in the stop\_words lexicon.

**2.** Perform an anti\_join() to remove them from unigram.

**3.** Perform an inner\_join() with the sentiment lexicon again.

The code below shows the step to add certain words in the stop\_words lexicon. **[Table 9.43](#17_Chapter09.xhtml#tab9.43)** shows the top 10 observations from the custom stop\_words lexicon.

![](images/page399-01.png)

#### 9.8.1 Sentiment Using Lexicon – Bing

At times, we may be interested in understanding if the tweet by the user reflects an overall positive sentiment or negative sentiment rather than understanding specific emotions through words. We can use ‘bing’ lexicon to get the positive or negative sentiment. The steps to be followed are as follows:

**1.** Get the sentiment score for each word in the tweet (tweet\_sentiment\_df). This can be done using the inner\_join with ‘bing’ lexicon. **[Table 9.44](#17_Chapter09.xhtml#tab9.44)** shows the output of this step.

![](images/page399-02.png)![](images/page400-01.png)![](images/page400-02.png)

**2.** Count the positive and negative sentiments for each user. The code below generates the output shown in **[Table 9.45](#17_Chapter09.xhtml#tab9.45).**

![](images/page400-03.png)

**3.** From **[Table 9.45](#17_Chapter09.xhtml#tab9.45)**, separate the sentiment count for positive and negative in a separate column. This may be performed using spread(). Then, calculate the overall\_sentiment (positive-negative) for each user. We can use mutate() to do so. The below code will help apply the step.

![](images/page400-04.png)![](images/page401-01.png)

**[Table 9.46](#17_Chapter09.xhtml#tab9.46)** shows the first ten observations as obtained from the above code snippet.

![](images/page401-02.png)

Though the original dataframe ‘tweet\_sentiment\_df’ had 45 users, tweet\_sen-timent\_bing shows only 42 unique users. It may be possible that words used in the tweets by the remaining three users did not match any of the words in the ‘bing’ lexicon. The overall\_sentiment column in **[Table 9.46](#17_Chapter09.xhtml#tab9.46)** is the difference between the positive and negative words used by the user in his/her tweets.

**1.** A positive count for overall\_sentiment will mean that the tweet expressed a positive sentiment.

**2.** A count of zero will mean that the tweet was neutral.

**3.** A negative count will mean that the tweet expressed a negative sentiment.

Let us plot the overall sentiment.

![](images/page401-03.png)![](images/page402-01.png)

From **[Figure 9.20](#17_Chapter09.xhtml#fig9.20)**, we can see that most of the official twitter handles of governments reflect a positive sentiment. The words used by these handles may be more of precautions, guidelines, and remedies to be followed during covid times and thus the reason they may be getting marked with a positive sentiment. Interestingly, the tweets by tb9gujarati, LogicalIndians are getting tagged as tweets which reflect negative sentiments.

Let us generate the wordcloud to understand the words in the tweets which reflect positive and negative sentiment. This can be done using the below steps:

**1.** Perform an inner join of tweet\_sentiment\_df with the bing lexicon.

**2.** Count the words and sentiments using the count() function.

![](images/page403-01.png)

**[Table 9.47](#17_Chapter09.xhtml#tab9.47)** shows the outcome of the above-mentioned steps.

![](images/page403-02.png)

We can use comparison.cloud() from wordcloud package to visualize the positive and negative words from **[Table 9.47](#17_Chapter09.xhtml#tab9.47).** However, this function needs a term frequency matrix as an input whose rows represent words and whose columns represent documents (count of positive and negative words). In order to convert sentiment\_word\_cloud to term.matrix we will use ‘acast/dcast’ method to reshape package. ‘acast()’ is similar to ‘speard()’ function from tidyr but can work on matrix/arrays as well (unlike spread). **[Table 9.48](#17_Chapter09.xhtml#tab9.48)** shows the outcome after using acast().

![](images/page403-03.png)![](images/page403-04.png)

In the code snippet above, the arguments on the left side to the ‘~’ that is, ‘word’ refer to the ID variables and the arguments on the right to the ‘~’ (sentiment) refer to the variable to spread into column names. The values to be spread are in variable *‘n’* (value. var=“n”). Now we can use the comparison.cloud() to visualize the positive and negative words.

![](images/page404-01.png)

**[Figure 9.21](#17_Chapter09.xhtml#fig9.21)** shows the negative words used in the tweet in black font (upper half of the **[Figure 9.21](#17_Chapter09.xhtml#fig9.21))** and the positive words in grey font (lower half of **[Figure 9.21](#17_Chapter09.xhtml#fig9.21)).** The more the frequency count of the words in the tweet, the larger the text size. ‘Decline’ may not be a negative word in the context of covid data but that is being shown as a negative word by virtue of the general use of word in English.

#### 9.8.2 Sentiment – Bing vs. Nrc vs. Affin

Of all the lexicons available, how do we decide which one to use for sentiment analysis? We can use all three to compare the results. The final one may be selected after validating the sentiment scores which are different for the three lexicons. The below code chunk uses the bing lexicon as in the previous section. **[Table 9.49](#17_Chapter09.xhtml#tab9.49)** shows the sentiment score using ‘bing’.

![](images/page404-02.png)

**TABLE 9.49** | First 10 users and the sentiment score using Bing

| screenName || sentiment\_bing |
| --- | --- |
| arupwharton || 0 |
| --- | --- |
| CovidPlasmaIn || 1 |
| DistrictAdm\_FBD || 0 |
| Drmubl || 2 |
| Esichq || −1 |
| FOBKeonjhar || 2 |
| FOBSrinagar || 6 |
| FOBUdhampur || 8 |
| HealthwireMedia || 4 |
| IndBloodDonors || 2 |

*Note:* Positive value reflects positive sentiment, negative value reflects negative sentiment, and a value of zero reflects neutral sentiment.

![](images/page405-01.png)

We can create the sentiment score using ‘nrc’ on similar lines to ‘bing’ lexicon. The below code is used to generate **[Table 9.50](#17_Chapter09.xhtml#tab9.50)** for sentiment using ‘nrc’.

![](images/page405-02.png)

**TABLE 9.50** | First 10 users and the sentiment score using nrc

| screenName || sentiment\_nrc |
| --- | --- |
| arupwharton || −2 |
| --- | --- |
| CovidindiaO || 1 |
| CovidPlasmaIn || 1 |
| DistrictAdm\_FBD || 0 |
| drmubl || 3 |
| esichq || 6 |
| FOBKeonjhar || 4 |
| FOBSrinagar || 3 |
| FOBUdhampur || 5 |
| HealthwireMedia || 8 |

*Note:* Positive value reflects positive sentiment, negative value reflects negative sentiment, and a value of zero reflects neutral sentiment.

**TABLE 9.51** | First 10 users and the sentiment score using afinn

| screenName || sentiment\_afinn |
| --- | --- |
| arupwharton || −2 |
| --- | --- |
| CovidindiaO || 1 |
| CovidPlasmaIn || 3 |
| DistrictAdm\_FBD || −1 |
| Drmubl || 8 |
| Esichq || 0 |
| FOBKeonjhar || 4 |
| FOBSrinagar || 6 |
| FOBUdhampur || 10 |
| HealthwireMedia || 6 |

*Note:* Positive value reflects positive sentiment, negative value reflects negative sentiment, and a value of zero reflects neutral sentiment.

**[Table 9.51](#17_Chapter09.xhtml#tab9.51)** for sentiment using ‘afinn’. Note that since the sentiment scores in affin lexicon are on a numeric scale, we did not use spread() and mutate().

![](images/page406-01.png)

We will merge the sentiment scores obtained by bing, nrc, and affin to create **[Table 9.52](#17_Chapter09.xhtml#tab9.52).**

![](images/page406-02.png)![](images/page406-03.png)

**[Table 9.52](#17_Chapter09.xhtml#tab9.52)** shows the sentiment score using the three lexicons. **[Figure 9.22](#17_Chapter09.xhtml#fig9.22)** shows the plot of affin score from **[Table 9.52](#17_Chapter09.xhtml#tab9.52).** If we compare the three scores, the nrc and bing seem to give similar sentiment (either positive or negative) for a user. However, there are instances of afinn sentiment being different to the nrc or bing. We can use either of the scores to access the sentiment of a user. The other option could be to use a voting mechanism (similar to ensemble techniques) and come up with a combined score and sentiment. We encourage readers to try the voting strategy to aggregate the outcome of the three lexicons and plot the same.

![](images/page407-01.png)![](images/page407-02.png)

### 9.9 | Sentiment Analysis with Negative Words

In the previous section, we arrived at the sentiment by counting the positive and negative words. However, one of the drawbacks of counting single words is that words on their own may not convey a positive or negative emotion.

**1.** I am not happy – This sentence may convey a positive emotion if we look at the words in unigram fashion. However, ‘not happy’ means a negative emotion.

One of the ways to deal with such sentiments is to look at the n-gram (bigrams/tri-grams) to arrive at the sentiment score. We already created bigrams (‘separated\_bigram’ variable) in [Section 9.7.6](#17_Chapter09.xhtml#sec9.7.6). Let us look at all the words which were preceded by ‘not.

![](images/page408-01.png)

From **[Table 9.53](#17_Chapter09.xhtml#tab9.53)**, we can see that the most common words used with not were ‘discriminate’, ‘over’, ‘forget, ‘attend, etc. We also see that there are stop\_words (like, to, a, etc.) appearing in the table but which do not convey an emotion. Let us use the AFINN lexicon to identify words preceded with negation words (‘not, ‘no, ‘never, ‘without, ‘dont’) and conveying emotion. **[Table 9.54](#17_Chapter09.xhtml#tab9.54)** shows the words and the sentiment score. Of course, these sentiment scores need to be interpreted in contrary. A negative score denotes a positive sentiment and a positive score denotes a negative sentiment.

![](images/page408-02.png)

From **[Table 9.54](#17_Chapter09.xhtml#tab9.54)**, we see that the most common word associated with not was forget, which actually should have a score of +1 (as it is preceded by ‘not’). We can calculate how much a word has contributed in the wrong direction. We will multiply ‘value’ and *‘n’* columns in **[Table 9.54](#17_Chapter09.xhtml#tab9.54)** to get the contribution. Contribution intuitively suggests that a word with a value of say +2 occurring five times has as much impact as a word with a sentiment value of + 1 occurring 10 times. **[Table 9.55](#17_Chapter09.xhtml#tab9.55)** shows the contribution of each word.

![](images/page408-03.png)![](images/page409-01.png)![](images/page409-02.png)![](images/page409-03.png)![](images/page410-01.png)

**[Figure 9.23](#17_Chapter09.xhtml#fig9.23)** visualizes the sentiment of words with negation aspects.

![](images/page410-02.png)

### 9.10 | | Document Term Matrix

In all the previous sections, we processed and arranged text in a tabular format such that it was ‘one token per document (tweets by a user/screenName here) per row’. The benefit of doing so was a quick summarization and visualization of text data as well as in sentiment analysis. However, this tabular structure of data may not be compatible with packages which apply other NLP models on the data.

One of the most common structures text mining packages work with is the document-term matrix (or DTM). DTM matrix has the following structure (Silge and Robinson, 2017):

**1.** Each row represents one document (such as tweet by the user/screenName).

**2.** Each column represents one token (unigram/bigram, etc.).

**3.** Each value (typically) contains the number of appearances of that term in that document.

This structure is exactly the same as in **[Tables 9.5](#17_Chapter09.xhtml#tab9.5)** and **[9.6](#17_Chapter09.xhtml#tab9.6)** from [Section 9.6.1](#17_Chapter09.xhtml#sec9.6.1). Intuitively, we can visualize that DTM will be a sparse matrix, that is, most pairings of document and word will have a value of zero. However, DTMs are created in efficient ways by different packages. The cast() from tidytext package can be used to convert a tabular data from previous sections in a DTM format. Tidytext provides three variations of cast function:

**1.** cast\_sparse() – converts to a sparse matrix which can be used with Matrix package.

**2.** cast\_dtm() – converts to DTM object to be used in operations from tm package.

**3.** cast\_dfm() – converts to a Document Feature Matrix (DFM) object which can work with quanteda package. DFM is just another name for DTM.

Given a DTM, tidytext also provides tidy() function which will convert the DTM to a tabular format (one token per document per row) for easy summarization and visualization of data.

We will use the cast() to create a DTM and merge it with the original tweet data-frame, that is, covid\_twitter\_df. Before we create the DTM and merge, a few things to keep in mind are as follows:

**1.** We will create twitter\_word dataframe as done in [Section 9.7.2](#17_Chapter09.xhtml#sec9.7.2). However, it will be without deleting the retweets while performing the text preprocessing.

**2.** Rather than using the screenName as a synonym to document ID, we will create a doc\_id to keep track of the individual tweets.

Treating screenName as document ID in all the previous sections was not an issue since we wanted to summarize, visualize and do sentiment analysis for the users, that is, at screenName level. Let us understand why the second point becomes important from a DTM perspective. The covid\_twitter\_df is shown in **[Table 9.56](#17_Chapter09.xhtml#tab9.56).**

![](images/page411-01.png)![](images/page411-02.png)![](images/page412-01.png)

From **[Table 9.56](#17_Chapter09.xhtml#tab9.56)**, we see that there are two tweets by screenName ‘MoHFW\_INDIA’. If we use screenName as document ID, then while creating a DTM, the texts corresponding to both tweets will be shown in one document id itself. Since the idea is to merge the DTM back with the covid\_twitter\_df, we will want to treat these two tweets as two different documents. Thus, the reason for creating a new indicator called doc\_id. The code below creates a new variable called doc\_id. **[Table 9.57](#17_Chapter09.xhtml#tab9.57)** shows the dataframe with doc\_id of the below code snippet.

![](images/page412-02.png)

The following code snippet applies the text processing steps on the text column of **[Table 9.57](#17_Chapter09.xhtml#tab9.57). [Table 9.58](#17_Chapter09.xhtml#tab9.58)** shows the resulting table from the following code.

![](images/page412-03.png)![](images/page413-01.png)![](images/page413-02.png)

Note that removing tweets with hashtags or non-English words or through any of regex, in general, may lead to removing the complete text data from some of the tweets (maybe some user tweeted with just hashtags or non-English words). From **[Table 9.57](#17_Chapter09.xhtml#tab9.57)**, we see observation number 25,492 wherein the text column has only hashtags and URLs. Altogether, in new\_covid\_twitter\_df, remove\_hashtag\_regex and remove\_non\_english\_regex was removing 240 tweets. This will create an issue if we try to column bind the resulting DTM (using twitter\_word variable) with the new\_covid\_twitter\_df. In order to circumvent this, we will store the doc\_ids in a list and use it as a key while merging DTM with the dataframe. The code below stores the doc\_id in unq\_doc\_id.

![](images/page413-03.png)

Let us get the count of words from twitter\_word variable using the below code. **[Table 9.59](#17_Chapter09.xhtml#tab9.59)** from the below code snippet shows the count of words.

![](images/page413-04.png)![](images/page414-01.png)![](images/page414-02.png)

Now we can convert **[Table 9.59](#17_Chapter09.xhtml#tab9.59)** into a DTM. We will use cast\_dtm() and pass the doc\_id, word, and count of words, that is, *‘n’* as parameters to it.

![](images/page414-03.png)

The output of cast\_dtm() shows the following:

**1.** Documents: 24,254, terms: 5,499 :- 24,254 refers to number of documents in DTM, which is exactly the same as the number of tweets/observations in covid\_twitter\_df. 5,499, referred to as terms, is the count of unique words from twitter\_word\_count dataframe.

**2.** Non-/sparse entries: 1,60,584/13,32,12,162. This shows that out of (24,254\*5,499 = 13,33,72,746), there are only 1,60,584 non-zero entries in the DTM. These non-zero entries are the count of words in specific documents. 13,32,12,162 are the count of zero entries in the DTM.

**3.** Sparsity: 100%. This is 13,32,12,162/13,33,72,746, which is approximately 100% zero entries in the DTM.

The row names of the matrix will be same as the doc\_id which we used in cast\_dtm(). The dimension of this matrix is 24,252\*5,499. We will typecast the DTM as a matrix object using the code below. **[Table 9.60](#17_Chapter09.xhtml#tab9.60)** shows the resulting matrix.

![](images/page415-01.png)

In order to merge **[Table 9.57](#17_Chapter09.xhtml#tab9.57)** with **[Table 9.60](#17_Chapter09.xhtml#tab9.60)**, we need to perform the following steps:

**1.** Column bind the twt\_dtm\_matrix and doc\_id. cbind() function can be used.

**2.** Typecast the matrix as dataframe by using as.data.frame().

The below code applies the two steps and creates mod\_twt\_dtm\_df. **[Table 9.61](#17_Chapter09.xhtml#tab9.61)** shows the mod\_twt\_dtm\_df output.

![](images/page415-02.png)![](images/page415-03.png)![](images/page415-04.png)![](images/page416-01.png)

Now, we can use inner\_join () from dplyr package to new\_covid\_twitter\_df **([Table 9.57](#17_Chapter09.xhtml#tab9.57))** and merge mod\_twt\_dtm\_df by doc\_id. The resulting findings are shown in **[Table 9.62](#17_Chapter09.xhtml#tab9.62).**

![](images/page416-02.png)

ncovid\_tweet\_df has the dimension of 25,494\*5,516. If the ncovid\_tweet\_df was a labelled dataset, we could have applied any supervised machine learning algorithm on the ncovid\_tweet\_df. Of course, ncovid\_tweet\_df needs further preprocessing to remove certain features but it is a dataset in which we converted unstructured text data into a structured format.

Document Term Matrix acts as an input to several modelling techniques. Rather than merging the ‘tweet\_dtm’, which is a DTM, with the original dataframe, we can use DTM as an input to Topic Modelling.

### 9.11 | | Topic Modelling

Topic modelling is an unsupervised learning algorithm which tries to extract the topics being discussed in a corpus. It treats

**1.** Every document as a mixture of topic.

**2.** Every topic as a mixture of words.

The number of topics to extract (*k*) from a document is a user-defined input to the topic modelling algorithm. Let us quickly apply the LDA() function from topicmodels package on the tweet\_dtm DTM.

![](images/page416-03.png)

We can extract the per topic per word probability by using a parameter called beta in tidy(). **[Table 9.63](#17_Chapter09.xhtml#tab9.63)** shows the probability of each word coming from the six topics.

![](images/page416-04.png)![](images/page417-01.png)

We can visualize the top 10 words as a part of the six topics.

![](images/page417-02.png)![](images/page418-01.png)

From **[Figure 9.24](#17_Chapter09.xhtml#fig9.24)**, we see the top words being used in each of the topics.

**1.** Words in topic 1 seem to suggest government rules and guidelines.

**2.** Words in topic 2 seem to suggest self-hygiene to be maintained.

**3.** Words in topic 3 seem to be talking about post-recovery support and symptoms.

**4.** Words (like festive, events, season, entertainment) in topic 4 seem to be talking about spreading awareness during festivals, etc.

Let us calculate the per document per topic probabilities by passing parameter ‘gamma’ to tidy().

![](images/page418-02.png)![](images/page419-01.png)

From **[Table 9.64](#17_Chapter09.xhtml#tab9.64)**, we can see document topic probabilities for all documents. If a document shows a probability of 0.166 for all topics, that would mean the word used in that document does not emerge from that document. From **[Table 9.64](#17_Chapter09.xhtml#tab9.64)**, we clearly see that document 10 has 93% of the words belonging to topic 1. We can filter the covid\_documents and understand the topics for each document. **[Table 9.65](#17_Chapter09.xhtml#tab9.65)** shows the topics in document 1 and it seems document 1 mostly belongs to topic 4, that is, personal hygiene.

![](images/page419-02.png)

We briefly discussed topic model in this section. Topic models may become much more useful to apply in documents where the length of the document is not restricted like in tweets. There are other visualization charts which can be prepared from the topic models. We leave it for the readers to try out different visualizations on the topic models.

![](images/page419-03.png)

### Summary

In this chapter, we learnt

**1.** Setting up a system to scrap twitter data and the importance of regular expressions in text preprocessing.

**2.** Text is unstructured data and needs extensive preprocessing before visualization and sentiment analysis. Regular expressions are helpful in text preprocessing.

**3.** Documents or sentences can be tokenized into unigrams or n-grams for building features.

**4.** Documents can be represented as vectors with words or n-grams as features. The vectors can be created using simple counts, TF (Term Frequency), or TF-IDF values.

**5.** A robust set of features can be created by removing stop words and applying stemming or lemmatization. The number of features can also be limited by selecting only features with higher frequencies.

**6.** Inbuilt lexicons such as afinn, nrc, bing, etc., can be used to understand the emotions of a text data. Visualization of unigrams and bigrams may help in getting a contextual understanding of the data.

**7.** Document Term Matrix becomes an input to several modelling techniques. We understood the use of DTM in the context of topic models.

### Exercise

#### Use the dataset *‘Sentiment Labelled Sentences Data Set’* from University of California Irvine Machine Learning Database to answer the following questions. The dataset can be downloaded from *[https://archive.ics.uci.edu/ml/datasets/Sentiment+Labelled+Sentences](https://archive.ics.uci.edu/ml/datasets/Sentiment+Labelled+Sentences)* (data folder) Answer Questions 1-10 using the data file yelp\_labelled.txt. The file has two columns. The first column is the text sentence and the second column is score. Score is either 1 (for positive) or 0 (for negative).

**1.** Load the dataset and find out how many positive and how many negative sentiment documents are available in the dataset. Draw a bar plot to depict the number documents in each sentiment category. Print few samples of positive sentiment and few samples of negative sentiment documents.

**2.** Create count vectors of all the documents.

**a.** Find out how many total words or features exist in the corpus.

**b.** Which are the 10 words with highest frequency or total count?

**c.** How many words or features exist with total frequency less than 3 in the whole corpus?

**3.** Create the count vectors by removing stop words (use stop\_words lexicon from tidytext).

**a.** Find out how many total words or features exist.

**b.** Which are the 10 words with highest frequency or total count?

**c.** Visualize the top 10 words using ggplot?

**4.** Create the tf-idf vectors by removing stop words (use stop\_words lexicon from tidytext).

**a.** Find out how many total words or features exist.

**b.** Which are the 10 words with highest tf-idf?

**c.** Visualize the top 10 words using ggplot?

**5.** Create the bigrams by removing stop words (use stop\_words lexicon from tidytext).

**a.** Find out how many bigrams exist.

**b.** Which are the 10 words with highest frequency or total count?

**c.** Visualize the top 10 words using ggplot?

**6.** Get the sentiment (positive and negative) of the dataset by using bing l exicon. Compare the sentiment score obtained using bing lexicon with the pre-existing sentiment column (i.e., second column Score). Document your findings.

**7.** Create a document term matrix (DTM) using the data. Build a topic model by using *k* = 2 to *k* = 6. What topics emerge from the sentiment data.

**8.** Split the documents into 80:20 ratio. 80% documents being in training set and 20% documents in test set.

**9.** Using the DTM created in Question 7, build a classification model using Logistic Regression to predict the probability of documents being positive. Use the pre-existing label column (i.e., Score as the *Y* feature/variable). Explain why the words have positive and negative coefficients.

**10.** From the model built above, find the optimal cut-off value using Youden’s index. Then classify the documents in the test set using the optimal cut-off value.

**a.** Create the confusion matrix.

**b.** Find out the precision and recall for positive sentiment cases.

### Bibliography

**1.** Anon (2020), *“Search\_Tweets”* available at https://www.rdocumentation.org/packages/rtweet/versions/0.7.0/topics/search\_tweets, accessed on 30 January 2021.

**2.** Anon (2021), *“Word Embedding Tutorial: word2vec using Gensim”*, available at https://www.guru99.com/word-embedding-word2vec.html, accessed on 30 January 2021.

**3.** Biguzzi S (2020), *“Sentiment Analysis”*, available at https://api.rpubs.com/biguzzis/data607assignment10, accessed on 30 January 2021.

**4.** Hu M and Liu B (2004), “Mining and summarizing customer reviews.”, Proceedings of the ACM SIGKDD International Conference on Knowledge Discovery & Data Mining (KDD-2004), Seattle, Washington, USA, Aug 22–25, 2004.

**5.** Jones K S (1972), “A statistical interpretation of term specificity and its application in retrieval”. *Journal of Documentation*, 28 (1), available at https://www.regular-expressions. info/unicode.html, accessed on 30 January 2021.

**6.** Liu B (2015), “Sentiment Analysis: Mining Sentiments, Opinions and Emotions”, Cambridge University Press, London.

**7.** Loughran T and McDonald B (2019), “Textual Analysis in Finance”, available at file:///C:/Users/Dinesh%20kumar/Downloads/SSRN-id3470272.pdf, Accessed on 5 August 2021.

**8.** Mohammad S M and Turney P (2013), “Crowdsourcing a Word-Emotion Association Lexicon.’’ *Computational Intelligence*, 29(3): 436–465, available at https://onlinelibrary.wiley.com/doi/abs/10.1111/j.1467-8640.2012.00460.x, accessed on 30 January 2021.

**9.** Nielsen F A (2011), “A New ANEW: Evaluation of a Word List for Sentiment Analysis for Microblogs”, In Proceedings of the ESWC2011 Workshop on ‘Making Sense of Microposts’: Big Things Come in Small Packages, Heraklion, Crete, Greece, May 30, 2011, pages 93–98.

**10.** Pradhan M and Kumar U D (2019), *“Machine Learning Using Python”*, Wiley, New Delhi.

**11.** Silge J and Robinson D (2017), *“Text Mining Using R – A Tidy Approach”*, O’Reilly Media.

\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

[¹](#17_Chapter09.xhtml#ch9-fn1)[https://developer.twitter.com/en/docs/twitter-api/v1/tweets/search/api-reference/get-search-tweets](https://developer.twitter.com/en/docs/twitter-api/v1/tweets/search/api-reference/get-search-tweets)

 

 
| 

## Further Readings

 || 

##  

 |
| --- | --- |

**1.** Acharya S (2018), *“Data Analytics Using* R”, McGraw Hill Education, New Delhi.

**2.** Anon (2021), “R Interface for the ‘H2O’ Scalable Machine Learning Platform”, available at [https://cran.r-project.org/web/packages/h2o/h2o.pdf](https://cran.r-project.org/web/packages/h2o/h2o.pdf), accessed on 17 June 2021.

**3.** Anon (2021), “Analytics Using R”, available at [https://pubs.wsb.wisc.edu/academics/analytics-using-r/getting-start-ed-with-r.html](https://pubs.wsb.wisc.edu/academics/analytics-using-r/getting-start-ed-with-r.html), accessed on 30 May 2021.

**4.** April S and Wagge J R (2020), “Learning R Programming Language with Psi Chi”, *Psi Chi Journal of Psychological Research* 25(1): 85–87.

**5.** Bach P, Chernozhukov V, Kurz M S and Spindler M (2021), “DoubleML – An Object-Oriented Implementation of Double Machine Learning in R”, available at [https://search-works.stanford.edu/articles/edsarx\_\_edsarx.2103.09603](https://search-works.stanford.edu/articles/edsarx__edsarx.2103.09603), accessed on 06 June 2021.

**6.** Bali R and Sarkar D, (2016), “R Machine Learning By Example”, available at [https://searchworks.stanford.edu/articles/nlebk](https://searchworks.stanford.edu/articles/nlebk) 1215154, accessed on 06 June 2021.

**7.** Bali R (2016), “R Machine Learning by Example”, available at [https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=f7ccefea-ce4b-454f-a91f-ec35aaaa7a21%40pdc-v-sessmgr02&bdata=JnNpdGU9ZWRzLWx-pdmU%3d#AN=ucb.b25657027&db=cat04202a](https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=f7ccefea-ce4b-454f-a91f-ec35aaaa7a21%40pdc-v-sessmgr02&bdata=JnNpdGU9ZWRzLWx-pdmU%3d#AN=ucb.b25657027&db=cat04202a), accessed on 07 June 2021.

**8.** Bell D (2020), “R Programming: A Step-by-Step Guide for Absolute Beginners”, 2^(nd) ed., Independent Publishing, USA.

**9.** Boehmke B and Greenwell BM (2019), “Hands-On Machine Learning with R”, Chapman, Boca Raton.

**10.** Boehmke B (2020), “Hands-on Machine Learning with R”, available at [https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=0a57de82-50f3-4795-b61c-227713deac27%40pdc-v-sessmgr02&bdata=JnNpdGU9ZWR-zLWxpdmU%3d#AN=ucb.b25219259&db=cat04202a](https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=0a57de82-50f3-4795-b61c-227713deac27%40pdc-v-sessmgr02&bdata=JnNpdGU9ZWR-zLWxpdmU%3d#AN=ucb.b25219259&db=cat04202a), accessed on 07 June 2021.

**11.** Boehmke BC (2016), “Data Wrangling with R (Use R!)”, Springer, New York.

**12.** Chang W (2018), “R Graphics Cookbook: Practical Recipes for Visualizing Data”, 2^(nd) ed., O’Reilly, California.

**13.** Chollet F and Allaire JJ (2018), “Deep Learning with R”, Manning, New York.

**14.** Ciaburro G and Venkateswaran B, (2017), “Neural Networks with R”, available at [https://searchworks.stanford.edu/articles/nlebk\_\_1607842](https://searchworks.stanford.edu/articles/nlebk__1607842), accessed on 06 June 2021.

**15.** Claster W B (2020), “Mathematics and R Programming for Machine Learning: From the Ground up”, available at [https://eds.b.ebscohost.com/eds/detail/de-tail?vid=0&sid=c72a0c6b-bac6-4cc1-8f60-904a29710a31%40sessionmgr101&bdata=JnNpdGU9ZWRzLWx-pdmU%3d#AN=ucb.b25808183&db=cat04202a](https://eds.b.ebscohost.com/eds/detail/de-tail?vid=0&sid=c72a0c6b-bac6-4cc1-8f60-904a29710a31%40sessionmgr101&bdata=JnNpdGU9ZWRzLWx-pdmU%3d#AN=ucb.b25808183&db=cat04202a), accessed on 07 June 2021.

**16.** Cotton R (2013), “Learning R: A Step-by-Step Function Guide to Data Analysis”, O’Reilly, California.

**17.** Crawley MJ (2012), “The R Book”, Wiley, Hoboken.

**18.** Daroczi G. (2015), “Mastering Data Analysis with R”, Packt, Birmingham.

**19.** Davies TM (2016), “The Book of R: A First Course in Programming and Statistics”, Wiley, Hoboken.

**20.** De Vries A. (2016), “R Programming For Dummies”, 2^(nd) ed., Wiley, Hoboken.

**21.** Deisenroth MP, Faisal AA and Cheng Soon Ong (2020), “Mathematics for Machine Learning”, Cambridge University Press, Cambridge.

**22.** DT Editorial (2016), “Big Data, Black Book: Covers Hadoop 2, MapReduce, Hive, YARN, Pig, R and Data Visualization”, Dreamtech Press, New Delhi.

**23.** Dunn PK and Smyth GK (2018), “Generalized Linear Models with Examples in R”, Springer, New York.

**24.** Faraway JJ (2014), “Linear Models with R”, Chapman, Florida.

**25.** Faraway JJ (2016), “Extending the Linear Model with R: Generalized Linear, Mixed Effects and Nonparametric Regression Models”, 2^(nd) ed., Chapman, Florida.

**26.** Field A (1900), “Discovering Statistics Using R”, Sage, California.

**27.** Fischetti A (2015), “Data Analysis with R”, Ingram, La Vergne.

**28.** Fischetti A (2015), “Data Analysis with R: Load, Wrangle, and Analyze Your Data Using the World’s Most Powerful Statistical Programming Language”, Packt, Birmingham.

**29.** Forte R M (2015), “Mastering Predictive Analytics with R”, Packt, Birmingham.

**30.** Fox J and Weisberg S (2011), “An R Companion to Applied Regression”, Sage, California.

**31.** Gardener M. (2013), “Beginning R: The Statistical Programming Language”, Wiley, Hoboken.

**32.** Gentleman R (2008), “R Programming for Bioinformatics”, available at [https://books.google.co.in/books?hl=en&lr=&id=34Y6WjJy8zEC&oi=fnd&pg=PP1&dq=articles+on+r+programming&ots=UjRd3t79oM&sig=opJ\_DwAy6-gv6yS7o-qwKbNCrsw#v=onepage&q&f=false](https://books.google.co.in/books?hl=en&lr=&id=34Y6WjJy8zEC&oi=fnd&pg=PP1&dq=articles+on+r+programming&ots=UjRd3t79oM&sig=opJ_DwAy6-gv6yS7o-qwKbNCrsw#v=onepage&q&f=false), accessed on 06 June 2021.

**33.** Gentleman R (2009), “R Programming for Bioinformatics”, available at [https://eds.b.ebscohost.com/eds/detail/detail?Vid=0&sid=ca22a0e3-4e7d-473f-adeb-4f0a365a4316%40pdc-v-sessmgr03&bdata=JnNpdGU9ZWRzLWxpdmU%3d#AN=ucb.b18033964&db=cat04202a](https://eds.b.ebscohost.com/eds/detail/detail?Vid=0&sid=ca22a0e3-4e7d-473f-adeb-4f0a365a4316%40pdc-v-sessmgr03&bdata=JnNpdGU9ZWRzLWxpdmU%3d#AN=ucb.b18033964&db=cat04202a), accessed on 07 June 2021.

**34.** Ghatak A (2017), “Machine Learning with R”, available at [https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=9dad0d55-8330-45a4-8d8b-afd-dc6424ddb%40pdc-v-sessmgr03&bdata=JnNpd-GU9ZWRzLWxpdmU%3d#AN=ucb.b24175802&db=cat04202a](https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=9dad0d55-8330-45a4-8d8b-afd-dc6424ddb%40pdc-v-sessmgr03&bdata=JnNpd-GU9ZWRzLWxpdmU%3d#AN=ucb.b24175802&db=cat04202a), accessed on 07 June 2021.

**35.** Gillespie C (2016), “Efficient R Programming: A Practical Guide to Smarter Programming”, available at [https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=83982043-1eef-43d8-9822-5fa9a8669591%40p-dc-v-sessmgr01&bdata=JnNpdGU9ZWRzLWxpd-mU%3d#AN=ucb.b25641403&db=cat04202a](https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=83982043-1eef-43d8-9822-5fa9a8669591%40p-dc-v-sessmgr01&bdata=JnNpdGU9ZWRzLWxpd-mU%3d#AN=ucb.b25641403&db=cat04202a), accessed on 07 June 2021.

**36.** Hartvigsen G (2014), “A Primer in Biological Data Analysis and Visualization Using R”, Columbia university press, New York.

**37.** Hefin (2020), “Machine Learning with R, the tidyverse, and mlr Rhys”, available at [https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=f1b6523b-f19c-4246-b94b-a7dcf2d4759a%40sessionmgr101&bdata=JnNpd-GU9ZWRzLWxpdmU%3d#AN=ucb.b25764223&db=cat04202a](https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=f1b6523b-f19c-4246-b94b-a7dcf2d4759a%40sessionmgr101&bdata=JnNpd-GU9ZWRzLWxpdmU%3d#AN=ucb.b25764223&db=cat04202a), accessed on 07 June 2021.

**38.** Heiss F (2016), “Using R for Introductory Econometrics”, Createspace, California.

**39.** Hornick M (2013), “Using R to Unlock the Value of Big Data”, McGraw Hill Education, New York.

**40.** Hothorn T (2014), “A Handbook of Statistical Analyses Using R”, Chapman, Boca Raton.

**41.** Jeyaraman and Priyadarshini B (2019), “Practical Machine Learning with R”, available at [https://searchworks.stan-ford.edu/articles/edsvox\_\_edsvox.international.scholar-vox.88874202](https://searchworks.stan-ford.edu/articles/edsvox__edsvox.international.scholar-vox.88874202), accessed on 06 June 2021.

**42.** Kabacoff R L (2015), “R in Action”, 2^(nd) ed. (Manning), Dreamtech Press, New Delhi.

**43.** Kassambara A (2017), “Machine Learning Essentials: Practical Guide in R”, available at [https://books.goo-gle.co.in/books?hl=en&lr=&id=745QDwAAQBA-J&oi=fnd&pg=PP2&dq=articles+on+machine+learn-ing+and+R&ots=5EKqwNRZRt&sig=Ojs-n3Ak-th9g-DpP91B1cRQyLbI#v=onepage&q=articles%20on%20machine%20learning%20and%20R&f=false](https://books.goo-gle.co.in/books?hl=en&lr=&id=745QDwAAQBA-J&oi=fnd&pg=PP2&dq=articles+on+machine+learn-ing+and+R&ots=5EKqwNRZRt&sig=Ojs-n3Ak-th9g-DpP91B1cRQyLbI#v=onepage&q=articles%20on%20machine%20learning%20and%20R&f=false), accessed on 06 June 2021.

**44.** Kruschke JK (2015), “The R Programming Language”, available at [https://www.sciencedirect.com/topics/mathe-matics/r-programming-language](https://www.sciencedirect.com/topics/mathe-matics/r-programming-language)

**45.** Kuhn M (2019), “The caret Package”, available at: [http://topepo.github.io/caret/index.html](http://topepo.github.io/caret/index.html), accessed on 17 June 2021.

**46.** Kun R (2016), “Learning R Programming”, available at [https://searchworks.stanford.edu/articles/nlebk\_\_1409189](https://searchworks.stanford.edu/articles/nlebk__1409189), accessed on 06 June 2021.

**47.** Lai J, Christopher J. Lortie, Robert A. Muenchen, Yang J, Keping Ma (2019), “Evaluating the Popularity of R in Ecology”, *Ecosphere* 10(1): 1–7. [https://doi.org/10.1002/ecs2.2567](https://doi.org/10.1002/ecs2.2567)

**48.** Lander J P (2017), “R for Everyone: Advanced Analytics and Graphics”, Addison-Wesley, Boston.

**49.** Lantz B (2013), “Machine Learning with R”, available at [https://books.google.co.in/books?hl=en&lr=&id=ZQu8AQAAQBAJ&oi=fnd&pg=PT12&dq=articles+on+machine+learning+using+r+program-ming&ots=\_9se\_hak5c&sig=ey7V76BvCd--TYQIYrm-FgOU-dRY#v=onepage&q&f=false](https://books.google.co.in/books?hl=en&lr=&id=ZQu8AQAAQBAJ&oi=fnd&pg=PT12&dq=articles+on+machine+learning+using+r+program-ming&ots=_9se_hak5c&sig=ey7V76BvCd--TYQIYrm-FgOU-dRY#v=onepage&q&f=false), accessed on 06 June 2021.

**50.** Lantz B (2019), “Machine Learning with R: Expert Techniques for Predictive Modeling”, available at [https://books.google.co.in/books?hl=en&lr=&id=iNuS-DwAAQBAJ&oi=fnd&pg=PP1&dq=articles+on+ma-chine+learning+using+r+programming&ots=O83St-beEK2&sig=eEDP\_rvqFwwiJ3TtjvH6W0\_g\_1E#v=onep-age&q&f=false](https://books.google.co.in/books?hl=en&lr=&id=iNuS-DwAAQBAJ&oi=fnd&pg=PP1&dq=articles+on+ma-chine+learning+using+r+programming&ots=O83St-beEK2&sig=eEDP_rvqFwwiJ3TtjvH6W0_g_1E#v=onep-age&q&f=false), accessed on 06 June 2021.

**51.** Lantz B (2015), “Machine Learning with R: Expert Techniques for Predictive Modeling to Solve All Your Data Analysis Problems”, available at [https://searchworks.stan-ford.edu/articles/edsebk\_\_1048220](https://searchworks.stan-ford.edu/articles/edsebk__1048220), accessed on 06 June 2021.

**52.** Lantz B (2019), “Machine Learning with R: Expert Techniques for Predictive Modeling”, 3^(rd) ed., available at [https://searchworks.stanford.edu/articles/edsebk\_\_2106304](https://searchworks.stanford.edu/articles/edsebk__2106304), accessed on 06 June 2021.

**53.** Lantz B (2013), “Machine Learning with R”, available at [https://searchworks.stanford.edu/articles/nlebk\_\_656222](https://searchworks.stanford.edu/articles/nlebk__656222), accessed on 06 June 2021.

**54.** Lanzetta V B and Dasgupta N and Farias R A (2018), “Hands-On Data Science with R”, Packt, Birmingham.

**55.** Larose D T and Larose C D (2019), “Data Science Using Python and R”, Wiley, Hoboken.

**56.** Ledolter J (2013), “Data Mining and Business Analytics with R”, Wiley, Hoboken.

**57.** Lesmeister C (2015), “Mastering Machine Learning with R”, available at [https://searchworks.stanford.edu/articles/nlebk\_1087969](https://searchworks.stanford.edu/articles/nlebk_1087969), accessed on 06 June 2021.

**58.** Lesmeister C (2019), “Advanced Machine Learning with R”, available at [https://searchworks.stanford.edu/articles/edsvox\_\_edsvox.international.scholarvox.88871045](https://searchworks.stanford.edu/articles/edsvox__edsvox.international.scholarvox.88871045), accessed on 06 June 2021.

**59.** Lewis N D (2014), “Visualizing Complex Data Using R: Standard Edition”, Createspace, California.

**60.** Long JD and Teetor P (2019), “R Cookbook: Proven Recipes for Data Analysis, Statistics, and Graphics”, 2^(nd) ed., O’Reilly, California.

**61.** Mailund T (2018), “Domain-Specific Languages in R: Advanced Statistical Programming”, Apress, Birmingham.

**62.** Maindonald J and Braun J (2003), “Data Analysis and Graphics Using R: An Example-based Approach”, Cambridge university press, Cambridge.

**63.** Malik F (2020), “R - Statistical Programming Language”, available at [https://towardsdatascience.com/r-statisti-cal-programming-language-6adc8c0a6e3d](https://towardsdatascience.com/r-statisti-cal-programming-language-6adc8c0a6e3d), accessed on 06 June 2021.

**64.** Matloff and Norman S (2011), “The Art of R Programming: Tour of Statistical Software Design”, available at [https://eds.b.ebscohost.com](https://eds.b.ebscohost.com)/eds/detail/detail?vid=0&sid=3d4e7ca8-80f0-4a92-b8e4-ddeda6c144c8%-40sessionmgr101&bdata=JnNpdGU9ZWRzLWxpdmU%3d#AN=ucb.b25635221&db=cat04202a, accessed on 07 June 2021.

**65.** Mayor E (2015), “Learning Predictive Analytics with R”, Packt, Birmingham.

**66.** Medeiros K (2018), “R Programming Fundamentals: Deal with Data Using Various Modeling Techniques’ available at [https://eds.b.ebscohost.com/eds/detail/de-tail?vid=0&sid=ed4ad89a-fcaf-4768-a5ba-b871369476d7%40pdc-v-sessmgr03&bdata=JnNpdGU9ZWRzLWx-pdmU%3d#AN=ucb.b25657033&db=cat04202a](https://eds.b.ebscohost.com/eds/detail/de-tail?vid=0&sid=ed4ad89a-fcaf-4768-a5ba-b871369476d7%40pdc-v-sessmgr03&bdata=JnNpdGU9ZWRzLWx-pdmU%3d#AN=ucb.b25657033&db=cat04202a), accessed on 07 June 2021.

**67.** Motwani, B (2019), “Data Analytics with R”, Wiley, New Delhi.

**68.** Mueller JP and Massaron L (2016), “Machine Learning (in Python and R) For Dummies”, Wiley, Hoboken.

**69.** Navarro T and Omar (2017), “R Programming by Example: Practical, Hands-on Projects to Help You Get Started with R”, available at [https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=9454f0b4-e27c-49a7-97da-b68d70ef9b0e%40pdc-v-sessmgr02&bdata=JnNpdGU9ZWR-zLWxpdmU%3d#AN=ucb.b25657032&db=cat04202a](https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=9454f0b4-e27c-49a7-97da-b68d70ef9b0e%40pdc-v-sessmgr02&bdata=JnNpdGU9ZWR-zLWxpdmU%3d#AN=ucb.b25657032&db=cat04202a), accessed on 07 June 2021.

**70.** Pacheco E R (2015), “Unsupervised Learning with R”, Packt, Birmingham.

**71.** Pearson R K (2020), “Exploratory Data Analysis Using R”, Chapman, Boca Raton.

**72.** Prajapati V (2013), “Big Data Analytics with R and Hadoop”, Packt, Birmingham.

**73.** Rakshit S (2017), “R Programming for Beginners”, McGraw Hill Education, New York.

**74.** Ratnoo S D and Ratnoo H S (2021), “Essentials of R for Data Analytics”, Wiley, New Delhi.

**75.** Ren K (2016), “Learning R Programming: Become an Efficient Data Scientist with R”, available at [https://eds.b.ebsco-host.com/eds/detail/detail?vid=0&sid=4308291d-6005-422c-b4a1-8c6fb6b1cce1%40sessionmgr101&bdata=JnNpdGU9ZWRzLWxpdmU%3d#AN=ucb.b25649156&db=cat04202a](https://eds.b.ebsco-host.com/eds/detail/detail?vid=0&sid=4308291d-6005-422c-b4a1-8c6fb6b1cce1%40sessionmgr101&bdata=JnNpdGU9ZWRzLWxpdmU%3d#AN=ucb.b25649156&db=cat04202a), accessed on 07 June 2021.

**76.** Ren K. (2016), “Learning R Programming: Language, Tools, and Practical Techniques”, Packt, Birmingham.

**77.** Ren K (2017), “Modern R Programming Cookbook: Recipes to Simplify Your Statistical Applications”, available at [https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=a373153a-b7c5-43fb-b3ea-28dfa2c170e2%40p-dc-v-sessmgr03&bdata=JnNpdGU9ZWRzLWxpd-mU%3d#AN=ucb.b25652445&db=cat04202a](https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=a373153a-b7c5-43fb-b3ea-28dfa2c170e2%40p-dc-v-sessmgr03&bdata=JnNpdGU9ZWRzLWxpd-mU%3d#AN=ucb.b25652445&db=cat04202a), accessed on 07 June 2021.

**78.** Sanz I P (2019), “Machine Learning with R Quick Start Guide: A Beginner’s Guide to Implementing Machine Learning Techniques from Scratch Using R 3.5, available at [https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=44fc693a-873a-4eb1-9eab-57a9e75c1e-c7%40sessionmgr103&bdata=JnNpdGU9ZWRzLWxpd-mU%3d#AN=ucb.b25649967&db=cat04202a](https://eds.b.ebscohost.com/eds/detail/detail?vid=0&sid=44fc693a-873a-4eb1-9eab-57a9e75c1e-c7%40sessionmgr103&bdata=JnNpdGU9ZWRzLWxpd-mU%3d#AN=ucb.b25649967&db=cat04202a), accessed on 07 June 2021.

**79.** Schumacker RE (2015), “Using R With Multivariate Statistics”, Sage, California.

**80.** Sheather S (2008), “A Modern Approach to Regression with R”, Springer, New York.

**81.** Silge J and Robinson D (2017), “Text Mining with R: A Tidy Approach”, available at: [https://www.tidytextmining.com/index.html](https://www.tidytextmining.com/index.html), accessed on 17 June 2021.

**82.** Tattar P N (2018), “Hands-On Ensemble Learning with R”, Packt, Birmingham.

**83.** Trejo O and Figliozzi P C (2017), “R Programming By Example”, available at [https://searchworks.stanford.edu/articles/nlebk\_\_1682395](https://searchworks.stanford.edu/articles/nlebk__1682395), accessed on 06 June 2021.

**84.** Viswa V (2016), “R: Recipes for Analysis, Visualization and Machine Learning”, available at [https://searchworks.stanford.edu/articles/nlebk\_\_1428303](https://searchworks.stanford.edu/articles/nlebk__1428303), accessed on 06 June 2021.

**85.** Wei-Meng Lee (2018), “Introduction to the R Programming Language”, available at [https://www.codemag.com/Article/1803081/Introduction-to-the-R-Program-ming-Language](https://www.codemag.com/Article/1803081/Introduction-to-the-R-Program-ming-Language), accessed on 16 June 2021.

**86.** Wickham H (2015), “R Packages”, O’Reilly, California.

**87.** Wickham H (2019), “Advanced R”, 2^(nd) ed., Chapman, Florida.

**88.** Wicklam H and Grolemund G (2017), “R for Data Science: Import, Tidy, Transform, Visualize, And Model Data”, O’Reilly, California.

**89.** Wiley M and Wiley J F (2019), “Advanced R Statistical Programming and Data Models: Analysis, Machine Learning and Visualization”, available at [https://books.google.co.in/books?hl=en&lr=&id=hBeJDwAAQBAJ&oi=fnd&pg=PR3&dq=articles+on+machine+learning+using+r+programming&ots=F1vOBohYRB&sig=8yVlltpt\_MtRO8OqX6rDgBYxUiME#v=onepage&q=articles%20on%20machine%20learning%20using%20r%20program-ming&f=false](https://books.google.co.in/books?hl=en&lr=&id=hBeJDwAAQBAJ&oi=fnd&pg=PR3&dq=articles+on+machine+learning+using+r+programming&ots=F1vOBohYRB&sig=8yVlltpt_MtRO8OqX6rDgBYxUiME#v=onepage&q=articles%20on%20machine%20learning%20using%20r%20program-ming&f=false), accessed on 06 June 2021.

**90.** Yu-Wei and Chiu D (2015), “Machine Learning with R Cookbook”, available at [https://books.goo-gle.co.in/books?hl=en&lr=&id=iPirBwAAQBAJ&oi=fnd&pg=PP1&dq=articles+on+machine+learn-ing+and+R&ots=\_WV7DFaIre&sig=qGDg3Wz6Sxlq0V4vsPnQVS50yoY#v=onepage&q=articles%20on%20machine%20learning%20and%20R&f=false](https://books.goo-gle.co.in/books?hl=en&lr=&id=iPirBwAAQBAJ&oi=fnd&pg=PP1&dq=articles+on+machine+learn-ing+and+R&ots=_WV7DFaIre&sig=qGDg3Wz6Sxlq0V4vsPnQVS50yoY#v=onepage&q=articles%20on%20machine%20learning%20and%20R&f=false), accessed on 06 June 2021.

**91.** Zhao (2014), “Data Mining Applications with R”, Elsevier, Amsterdam.

**92.** Zumel N and Mount J (2014), “Practical Data Science with R” (Manning), Dreamtech Press, New Delhi.

 

 
| 

## Index

 || 

##  

 |
| --- | --- |

#### **A**

advanced encoding techniques, [147](#13_Chapter05.xhtml#page_147)

akaike information criteria (AIC), [147](#13_Chapter05.xhtml#page_147), [190](#14_Chapter06.xhtml#page_190)

glmStepAIC method, [190](#14_Chapter06.xhtml#page_190)–[194](#14_Chapter06.xhtml#page_194)

model selection using, [157](#13_Chapter05.xhtml#page_157)–[159](#13_Chapter05.xhtml#page_159)

steps in, [159](#13_Chapter05.xhtml#page_159)–[162](#13_Chapter05.xhtml#page_162), [194](#14_Chapter06.xhtml#page_194)–[195](#14_Chapter06.xhtml#page_195)

Anaconda, [3](#09_Chapter01.xhtml#page_3)

distribution, [14](#09_Chapter01.xhtml#page_14)

Anaconda navigator

analysis of variance (ANOVA), [115](#12_Chapter04.xhtml#page_115)–[118](#12_Chapter04.xhtml#page_118)

artificial intelligence, [1](#09_Chapter01.xhtml#page_1)–[2](#09_Chapter01.xhtml#page_2), [229](#15_Chapter07.xhtml#page_229)

#### **B**

bag-of-words (BoW) model

binary vector, [354](#17_Chapter09.xhtml#page_354)

count vector, [354](#17_Chapter09.xhtml#page_354)

defined, [353](#17_Chapter09.xhtml#page_353)

n-grams, [383](#17_Chapter09.xhtml#page_383)–[386](#17_Chapter09.xhtml#page_386)

stemming and lemmatization, [372](#17_Chapter09.xhtml#page_372)–[379](#17_Chapter09.xhtml#page_379)

term frequency-inverse document frequency (TF-IDF), [379](#17_Chapter09.xhtml#page_379)–[383](#17_Chapter09.xhtml#page_383)

term frequency-inverse document frequency (TF-IDF), [355](#17_Chapter09.xhtml#page_355)–[356](#17_Chapter09.xhtml#page_356)

term frequency (TF) vector, [354](#17_Chapter09.xhtml#page_354)–[355](#17_Chapter09.xhtml#page_355)

bandwidth of kernel, [76](#11_Chapter03.xhtml#page_76)

bar chart or plot Beta distribution, [106](#12_Chapter04.xhtml#page_106)

bias-variance trade-off, [238](#15_Chapter07.xhtml#page_238)–[244](#15_Chapter07.xhtml#page_244)

binary encoding, [147](#13_Chapter05.xhtml#page_147)

binary logistic regression model, [176](#14_Chapter06.xhtml#page_176)–[178](#14_Chapter06.xhtml#page_178)

binomial distribution

cumulative distribution function, [94](#12_Chapter04.xhtml#page_94)

discrete probability distribution, [93](#12_Chapter04.xhtml#page_93)

probability mass function, [93](#12_Chapter04.xhtml#page_93)

using R, [94](#12_Chapter04.xhtml#page_94)–[95](#12_Chapter04.xhtml#page_95)

bootstrap sampling, [285](#16_Chapter08.xhtml#page_285)

box plot (aka box and whisker plot)

#### **C**

central limit theorem, [106](#12_Chapter04.xhtml#page_106)–[107](#12_Chapter04.xhtml#page_107)

classification problems (or class probability) binary logistic regression (*see* Binary logistic regression model)

class imbalance problem, [289](#16_Chapter08.xhtml#page_289)

regrouping classes, [290](#16_Chapter08.xhtml#page_290)

sampling strategies, [290](#16_Chapter08.xhtml#page_290)–[292](#16_Chapter08.xhtml#page_292)

comprehensive R archive network (CRAN), [3](#09_Chapter01.xhtml#page_3)–[5](#09_Chapter01.xhtml#page_5)

correlation matrix, [83](#11_Chapter03.xhtml#page_83)–[84](#11_Chapter03.xhtml#page_84)

#### **D**

data.frame, [12](#09_Chapter01.xhtml#page_12), [17](#10_Chapter02.xhtml#page_17)

data.table, [23](#10_Chapter02.xhtml#page_23), [48](#10_Chapter02.xhtml#page_48)–[51](#10_Chapter02.xhtml#page_51)

tidy data.frame, [18](#10_Chapter02.xhtml#page_18)

data import using twitteR package, [350](#17_Chapter09.xhtml#page_350)–[353](#17_Chapter09.xhtml#page_353)

data preprocessing, defined, [17](#10_Chapter02.xhtml#page_17)

data scrapping, steps for data from twitter, [337](#17_Chapter09.xhtml#page_337)–[340](#17_Chapter09.xhtml#page_340)

data.table

basic column subset operations, [27](#10_Chapter02.xhtml#page_27)–[31](#10_Chapter02.xhtml#page_31)

basic operations using R, [24](#10_Chapter02.xhtml#page_24)–[26](#10_Chapter02.xhtml#page_26)

basic row and column select and computation of operations, [31](#10_Chapter02.xhtml#page_31)–[35](#10_Chapter02.xhtml#page_35)

basic row subset operations, [26](#10_Chapter02.xhtml#page_26)–[27](#10_Chapter02.xhtml#page_27)

binary search-based subset, [40](#10_Chapter02.xhtml#page_40)–[42](#10_Chapter02.xhtml#page_42)

data wrangling using, [24](#10_Chapter02.xhtml#page_24)

DT package, [51](#10_Chapter02.xhtml#page_51)–[52](#10_Chapter02.xhtml#page_52)

.EACHI, [35](#10_Chapter02.xhtml#page_35)

group by operations, [36](#10_Chapter02.xhtml#page_36)–[40](#10_Chapter02.xhtml#page_40)

join operations, [42](#10_Chapter02.xhtml#page_42)–[48](#10_Chapter02.xhtml#page_48)

keys, [40](#10_Chapter02.xhtml#page_40)–[42](#10_Chapter02.xhtml#page_42)

data table object, [21](#10_Chapter02.xhtml#page_21)

data visualization in R, [58](#11_Chapter03.xhtml#page_58)–[59](#11_Chapter03.xhtml#page_59)

bar chart or plot (*see* Bar chart or plot)

box plot (aka box and whisker plot) (*see* Box plot (aka box and whisker plot))

correlation matrix (*see* Correlation matrix)

distribution or density plot (*see* Distribution or density plot)

heatmap (*see* Heatmap)

histogram (*see* Histogram)

scatter plot (*see* Scatter plot)

trend plot (*see* trend plot)

decision tree learning (or decision trees)

area under ROC (AUC) curve, [223](#14_Chapter06.xhtml#page_223)–[224](#14_Chapter06.xhtml#page_224)

classification and regression tree (CART), [216](#14_Chapter06.xhtml#page_216)

confusion matrix, creation of, [222](#14_Chapter06.xhtml#page_222)–[223](#14_Chapter06.xhtml#page_223)

receiver operating characteristic (ROC) curve, [223](#14_Chapter06.xhtml#page_223)–[224](#14_Chapter06.xhtml#page_224)

deep learning (DL) algorithm, [1](#09_Chapter01.xhtml#page_1)–[2](#09_Chapter01.xhtml#page_2)

descriptive analytics, using data.frame in R, [17](#10_Chapter02.xhtml#page_17)–[18](#10_Chapter02.xhtml#page_18)

distribution or density plot, [76](#11_Chapter03.xhtml#page_76)

kernel density estimation (KDE) (*see* Kernel density estimation (KDE)), [76](#11_Chapter03.xhtml#page_76)

probability density function (PDF) (*see* Probability density function (PDF)), [75](#11_Chapter03.xhtml#page_75), [93](#12_Chapter04.xhtml#page_93)

document term matrix (DTM)

down-sample strategy, [290](#16_Chapter08.xhtml#page_290)–[291](#16_Chapter08.xhtml#page_291)

DT package, [51](#10_Chapter02.xhtml#page_51)–[52](#10_Chapter02.xhtml#page_52)

#### **E**

ensemble methods, [285](#16_Chapter08.xhtml#page_285)

class imbalance problem (*see* Class imbalance problem)

random forest (*see* Random forest)

exponential distribution, [96](#12_Chapter04.xhtml#page_96)

#### **F**

feature engineering, [3](#09_Chapter01.xhtml#page_3)–[4](#09_Chapter01.xhtml#page_4), [55](#11_Chapter03.xhtml#page_55)

feature extraction, [4](#09_Chapter01.xhtml#page_4)

feature hashing, [147](#13_Chapter05.xhtml#page_147)

feature weights, [2](#09_Chapter01.xhtml#page_2)

#### **G**

gain chart for logistic regression model, [211](#14_Chapter06.xhtml#page_211)–[216](#14_Chapter06.xhtml#page_216)

Gamma distribution, [106](#12_Chapter04.xhtml#page_106)

geometric distribution, [106](#12_Chapter04.xhtml#page_106)

gradient boosted machine (GBM), [308](#16_Chapter08.xhtml#page_308)–[309](#16_Chapter08.xhtml#page_309)

model diagnostic, [315](#16_Chapter08.xhtml#page_315)–[317](#16_Chapter08.xhtml#page_317)

model prediction, [318](#16_Chapter08.xhtml#page_318)

stochastic gradient boosting (*see* Stochastic gradient boosting)

class imbalance, [313](#16_Chapter08.xhtml#page_313)

control growth, [313](#16_Chapter08.xhtml#page_313)–[314](#16_Chapter08.xhtml#page_314)

hyper-parameters, [314](#16_Chapter08.xhtml#page_314)

random row selection (bootstrap), [313](#16_Chapter08.xhtml#page_313)

random subspace selection, [312](#16_Chapter08.xhtml#page_312)–[313](#16_Chapter08.xhtml#page_313)

search criteria, [314](#16_Chapter08.xhtml#page_314)

gradient descent (GD) algorithm, [230](#15_Chapter07.xhtml#page_230)

development for linear regression model creating of feature set (*X*) and outcome variable (*Y*), [232](#15_Chapter07.xhtml#page_232)–[233](#15_Chapter07.xhtml#page_233)

encoding categorical features, [233](#15_Chapter07.xhtml#page_233)–[234](#15_Chapter07.xhtml#page_234)

set x and y variable, [234](#15_Chapter07.xhtml#page_234)

plot cost value, [236](#15_Chapter07.xhtml#page_236)–[238](#15_Chapter07.xhtml#page_238)

#### **H**

heatmap, [83](#11_Chapter03.xhtml#page_83)–[85](#11_Chapter03.xhtml#page_85)

hexagon

plot between sold price and base price, [74](#11_Chapter03.xhtml#page_74)

plot between sold price and base price by playing role, [75](#11_Chapter03.xhtml#page_75)

histogram

2D histogram plot between sold price and base price, [73](#11_Chapter03.xhtml#page_73)

hypothesis testing

alternative hypothesis, [107](#12_Chapter04.xhtml#page_107)–[108](#12_Chapter04.xhtml#page_108)

chi-square goodness of fit test and test of independence, [113](#12_Chapter04.xhtml#page_113)–[115](#12_Chapter04.xhtml#page_115)

non-parametric tests, [108](#12_Chapter04.xhtml#page_108)

null hypothesis, [107](#12_Chapter04.xhtml#page_107)–[108](#12_Chapter04.xhtml#page_108)

one-sample i-test, [110](#12_Chapter04.xhtml#page_110)–[111](#12_Chapter04.xhtml#page_111)

one-sample Z-test, [109](#12_Chapter04.xhtml#page_109)–[110](#12_Chapter04.xhtml#page_110)

paired sample i-test, [112](#12_Chapter04.xhtml#page_112)–[113](#12_Chapter04.xhtml#page_113)

parametric tests, [108](#12_Chapter04.xhtml#page_108)

two-sample *t*\-test, [111](#12_Chapter04.xhtml#page_111)–[112](#12_Chapter04.xhtml#page_112)

#### **I**

Indian Premier League (IPL), [18](#10_Chapter02.xhtml#page_18)–[20](#10_Chapter02.xhtml#page_20)

#### **J**

Jupyter Notebook, [5](#09_Chapter01.xhtml#page_5), [15](#09_Chapter01.xhtml#page_15), [23](#10_Chapter02.xhtml#page_23)

#### **K**

kernel, [76](#11_Chapter03.xhtml#page_76)

kernel density estimation (KDE), [76](#11_Chapter03.xhtml#page_76)

key performance index (KPI), [91](#12_Chapter04.xhtml#page_91)

#### **L**

lift chart for logistic regression model, [211](#14_Chapter06.xhtml#page_211)–[216](#14_Chapter06.xhtml#page_216)

linear dependency, [187](#14_Chapter06.xhtml#page_187) Linear Regression, [121](#13_Chapter05.xhtml#page_121)–[124](#13_Chapter05.xhtml#page_124)

Estimation of regression coefficient, [133](#13_Chapter05.xhtml#page_133)

Model Building, [128](#13_Chapter05.xhtml#page_128)

Model diagnostics, [134](#13_Chapter05.xhtml#page_134)

logistic regression model, [2](#09_Chapter01.xhtml#page_2)

area under ROC curve (AUC), [205](#14_Chapter06.xhtml#page_205)–[206](#14_Chapter06.xhtml#page_206)

binary (*see* Binary logistic regression model)

cost function for, [231](#15_Chapter07.xhtml#page_231)

diagnostic

confusion matrix, creation of, [200](#14_Chapter06.xhtml#page_200)–[201](#14_Chapter06.xhtml#page_201)

likelihood ratio (LR) test, [198](#14_Chapter06.xhtml#page_198)

prediction on test data, [199](#14_Chapter06.xhtml#page_199)–[200](#14_Chapter06.xhtml#page_200)

pseudo *R*², [198](#14_Chapter06.xhtml#page_198)–[199](#14_Chapter06.xhtml#page_199)

Wald’s test, [198](#14_Chapter06.xhtml#page_198)

finding optimal classification cut-off

cost-based approach, [206](#14_Chapter06.xhtml#page_206), [209](#14_Chapter06.xhtml#page_209)–[211](#14_Chapter06.xhtml#page_211)

Youden’s Index, [206](#14_Chapter06.xhtml#page_206)–[209](#14_Chapter06.xhtml#page_209)

gain chart (*see* Gain chart for logistic regression model)

lift chart (*see* Lift chart for logistic regression model)

measuring accuracy of

accuracy, [201](#14_Chapter06.xhtml#page_201)

F-score, [204](#14_Chapter06.xhtml#page_204)

Kappa value, calculation of, [202](#14_Chapter06.xhtml#page_202)

McNemar’s hypothesis test, [203](#14_Chapter06.xhtml#page_203)

no information rate (NIR), [201](#14_Chapter06.xhtml#page_201)–[202](#14_Chapter06.xhtml#page_202)

precision (positive predicted value), [204](#14_Chapter06.xhtml#page_204)

sensitivity (recall or true positive rate), [203](#14_Chapter06.xhtml#page_203)

specificity (true negative rate), [204](#14_Chapter06.xhtml#page_204)

receiver operating characteristics (ROC) curve, [205](#14_Chapter06.xhtml#page_205)–[206](#14_Chapter06.xhtml#page_206)

#### **M**

machine learning (ML) algorithm, [2](#09_Chapter01.xhtml#page_2), [17](#10_Chapter02.xhtml#page_17)

evolutionary learning algorithms, [3](#09_Chapter01.xhtml#page_3)

feature engineering, [181](#14_Chapter06.xhtml#page_181)–[183](#14_Chapter06.xhtml#page_183)

logistic regression using glmnet, [271](#15_Chapter07.xhtml#page_271)–[272](#15_Chapter07.xhtml#page_272)

classification model using glmnet and caret, [274](#15_Chapter07.xhtml#page_274)–[282](#15_Chapter07.xhtml#page_282)

create feature set (*X*) and outcome variable (*Y*), [272](#15_Chapter07.xhtml#page_272)–[274](#15_Chapter07.xhtml#page_274)

create train and test set, [274](#15_Chapter07.xhtml#page_274)

models with glmnet and caret, results of, [271](#15_Chapter07.xhtml#page_271)

regression using caret

elasticnet regression with tuneGrid and tuneLength, [265](#15_Chapter07.xhtml#page_265)–[270](#15_Chapter07.xhtml#page_270)

LASSO regression, [257](#15_Chapter07.xhtml#page_257)–[261](#15_Chapter07.xhtml#page_261)

ridge regression, [261](#15_Chapter07.xhtml#page_261)–[265](#15_Chapter07.xhtml#page_265)

regression using glmnet package, [248](#15_Chapter07.xhtml#page_248)–[249](#15_Chapter07.xhtml#page_249)

create feature set (*X*) and outcome variable (*Y*), [249](#15_Chapter07.xhtml#page_249)–[250](#15_Chapter07.xhtml#page_250)

create train and test set, [250](#15_Chapter07.xhtml#page_250)

interpretation of outcome, [253](#15_Chapter07.xhtml#page_253)–[257](#15_Chapter07.xhtml#page_257)

intuition behind lambda sequence, [251](#15_Chapter07.xhtml#page_251)–[253](#15_Chapter07.xhtml#page_253)

LASSO regression using glmnet, [250](#15_Chapter07.xhtml#page_250)–[251](#15_Chapter07.xhtml#page_251)

reinforcement learning algorithms, [2](#09_Chapter01.xhtml#page_2), [230](#15_Chapter07.xhtml#page_230)

strategies to improve

adding more observations, [245](#15_Chapter07.xhtml#page_245)–[246](#15_Chapter07.xhtml#page_246)

applying regularization, [246](#15_Chapter07.xhtml#page_246)–[248](#15_Chapter07.xhtml#page_248)

*K*\-fold cross validation, [246](#15_Chapter07.xhtml#page_246)

supervised learning algorithms, [2](#09_Chapter01.xhtml#page_2), [230](#15_Chapter07.xhtml#page_230)

unsupervised learning algorithms, [2](#09_Chapter01.xhtml#page_2), [230](#15_Chapter07.xhtml#page_230)

multi-collinearity, [188](#14_Chapter06.xhtml#page_188)–[190](#14_Chapter06.xhtml#page_190)

multiple linear regression (MLR) (aka response variable or outcome

variable) model, [162](#13_Chapter05.xhtml#page_162)–[163](#13_Chapter05.xhtml#page_163)

assumptions in, [141](#13_Chapter05.xhtml#page_141)

building and rebuilding by using caret package, [147](#13_Chapter05.xhtml#page_147)–[149](#13_Chapter05.xhtml#page_149), [153](#13_Chapter05.xhtml#page_153)–[162](#13_Chapter05.xhtml#page_162)

diagnostic, [163](#13_Chapter05.xhtml#page_163)–[164](#13_Chapter05.xhtml#page_164)

homogeneity assumption, [165](#13_Chapter05.xhtml#page_165)

identify outlier cases in dataframe, [167](#13_Chapter05.xhtml#page_167)–[169](#13_Chapter05.xhtml#page_169)

influential values, [167](#13_Chapter05.xhtml#page_167)

linearity assumption, [164](#13_Chapter05.xhtml#page_164)

normality assumption, [165](#13_Chapter05.xhtml#page_165)

outliers and high leverage points, [165](#13_Chapter05.xhtml#page_165)–[167](#13_Chapter05.xhtml#page_167)

transformation of response variable, [169](#13_Chapter05.xhtml#page_169)–[170](#13_Chapter05.xhtml#page_170)

transformed variable, [170](#13_Chapter05.xhtml#page_170)–[171](#13_Chapter05.xhtml#page_171)

methods to develop, [141](#13_Chapter05.xhtml#page_141)–[142](#13_Chapter05.xhtml#page_142)

to create train and test set, [147](#13_Chapter05.xhtml#page_147)

creating feature set (*X*) and outcome variable (*Y*), [145](#13_Chapter05.xhtml#page_145)–[146](#13_Chapter05.xhtml#page_146)

encoding categorical features, [146](#13_Chapter05.xhtml#page_146)–[147](#13_Chapter05.xhtml#page_147)

importing dataset, [142](#13_Chapter05.xhtml#page_142)–[145](#13_Chapter05.xhtml#page_145)

multicollinearity, significance of, [149](#13_Chapter05.xhtml#page_149)–[153](#13_Chapter05.xhtml#page_153)

supervised learning algorithm, [140](#13_Chapter05.xhtml#page_140)–[141](#13_Chapter05.xhtml#page_141)

#### **N**

normal distribution (or Gaussian distribution)

analysis of stock data, [100](#12_Chapter04.xhtml#page_100)–[103](#12_Chapter04.xhtml#page_103)

confidence interval, [104](#12_Chapter04.xhtml#page_104)–[105](#12_Chapter04.xhtml#page_105)

cumulative probability distribution, [105](#12_Chapter04.xhtml#page_105)–[106](#12_Chapter04.xhtml#page_106)

means and variance, [103](#12_Chapter04.xhtml#page_103)–[104](#12_Chapter04.xhtml#page_104)

visualization of data, [99](#12_Chapter04.xhtml#page_99)–[100](#12_Chapter04.xhtml#page_100)

#### **O**

ordinal encoding, [147](#13_Chapter05.xhtml#page_147)

#### **P**

packages for text analytics, [348](#17_Chapter09.xhtml#page_348)–[350](#17_Chapter09.xhtml#page_350)

poisson distribution, [95](#12_Chapter04.xhtml#page_95)

pre-built dictionaries, [399](#17_Chapter09.xhtml#page_399)

probability density function (PDF)

continuous random variable, [75](#11_Chapter03.xhtml#page_75)

kernel, [76](#11_Chapter03.xhtml#page_76)

limiting value of probability, [75](#11_Chapter03.xhtml#page_75)

probability theory, [91](#12_Chapter04.xhtml#page_91)

event, [92](#12_Chapter04.xhtml#page_92)

random experiment, [92](#12_Chapter04.xhtml#page_92)

sample space, [92](#12_Chapter04.xhtml#page_92)

#### **R**

random forest (or bagging)

model development, [287](#16_Chapter08.xhtml#page_287)

out-of-bag data, [287](#16_Chapter08.xhtml#page_287)

prediction of net promoter score (NPS) using, [287](#16_Chapter08.xhtml#page_287)–[289](#16_Chapter08.xhtml#page_289)

using h2o package, [292](#16_Chapter08.xhtml#page_292)–[296](#16_Chapter08.xhtml#page_296)

class imbalance, [299](#16_Chapter08.xhtml#page_299)–[300](#16_Chapter08.xhtml#page_300)

control growth, [300](#16_Chapter08.xhtml#page_300)

criteria for search, [301](#16_Chapter08.xhtml#page_301)

feature list in the data, [296](#16_Chapter08.xhtml#page_296)–[298](#16_Chapter08.xhtml#page_298)

grid search, [301](#16_Chapter08.xhtml#page_301)–[303](#16_Chapter08.xhtml#page_303)

with h2o package, [299](#16_Chapter08.xhtml#page_299)

hyper-parameters, [300](#16_Chapter08.xhtml#page_300)

model diagnostics, [303](#16_Chapter08.xhtml#page_303)–[305](#16_Chapter08.xhtml#page_305)

model prediction, [305](#16_Chapter08.xhtml#page_305)–[307](#16_Chapter08.xhtml#page_307)

row selection (bootstrap), [300](#16_Chapter08.xhtml#page_300)

save the model, [307](#16_Chapter08.xhtml#page_307)–[308](#16_Chapter08.xhtml#page_308)

split of data into train and test set, [298](#16_Chapter08.xhtml#page_298)–[299](#16_Chapter08.xhtml#page_299)

subspace selection, [299](#16_Chapter08.xhtml#page_299)

random over-sampling examples (ROSE), [291](#16_Chapter08.xhtml#page_291)–[292](#16_Chapter08.xhtml#page_292)

random subspace method, [285](#16_Chapter08.xhtml#page_285)

random variables, [91](#12_Chapter04.xhtml#page_91)

continuous, [92](#12_Chapter04.xhtml#page_92)–[93](#12_Chapter04.xhtml#page_93)

discrete, [92](#12_Chapter04.xhtml#page_92)

cumulative distribution function (CDF), [93](#12_Chapter04.xhtml#page_93)

probability mass function (PMF), [93](#12_Chapter04.xhtml#page_93)

regular expression

application of regex, [346](#17_Chapter09.xhtml#page_346)–[348](#17_Chapter09.xhtml#page_348)

match characters, [340](#17_Chapter09.xhtml#page_340)–[345](#17_Chapter09.xhtml#page_345)

repeat characters, [345](#17_Chapter09.xhtml#page_345)–[346](#17_Chapter09.xhtml#page_346)

R programming language, concept of

the importance of being earnest (TIOBE) programming index, [5](#09_Chapter01.xhtml#page_5)–[7](#09_Chapter01.xhtml#page_7)

use of, [4](#09_Chapter01.xhtml#page_4)

Rstudio, [23](#10_Chapter02.xhtml#page_23)

#### **S**

scatter plot

assessing strength of relationship, [59](#11_Chapter03.xhtml#page_59)

between AVE\_BL and SR\_BL, [60](#11_Chapter03.xhtml#page_60)

between bowling average and strike rate, [61](#11_Chapter03.xhtml#page_61)–[63](#11_Chapter03.xhtml#page_63)

between bowling average and strike rate with fitted line, [61](#11_Chapter03.xhtml#page_61)

with facet grid, [89](#11_Chapter03.xhtml#page_89)

with overlapping representation, [72](#11_Chapter03.xhtml#page_72)

sentiment analysis, [395](#17_Chapter09.xhtml#page_395)–[399](#17_Chapter09.xhtml#page_399)

bing ***vs.*** nrc ***vs.*** affin, [404](#17_Chapter09.xhtml#page_404)–[407](#17_Chapter09.xhtml#page_407)

with negative words, [408](#17_Chapter09.xhtml#page_408)–[410](#17_Chapter09.xhtml#page_410)

using bing lexicon, [399](#17_Chapter09.xhtml#page_399)–[404](#17_Chapter09.xhtml#page_404)

simple linear regression (SLR) model

building of, [123](#13_Chapter05.xhtml#page_123)–[124](#13_Chapter05.xhtml#page_124)

caret package, [128](#13_Chapter05.xhtml#page_128)–[133](#13_Chapter05.xhtml#page_133)

create train and validation set, [128](#13_Chapter05.xhtml#page_128)

creating feature set (X) and outcome variable (Y), [128](#13_Chapter05.xhtml#page_128)

data import and manipulation, [126](#13_Chapter05.xhtml#page_126)–[127](#13_Chapter05.xhtml#page_127)

defined, [121](#13_Chapter05.xhtml#page_121)

diagnostics

analysis of variance (ANOVA) in regression analysis, [136](#13_Chapter05.xhtml#page_136)

coefficient of determination (or *R*\-square or *R2*), [135](#13_Chapter05.xhtml#page_135)

hypothesis test for regression coefficient, [135](#13_Chapter05.xhtml#page_135)–[136](#13_Chapter05.xhtml#page_136)

model diagnostic, [136](#13_Chapter05.xhtml#page_136)–[137](#13_Chapter05.xhtml#page_137)

outlier analysis, [138](#13_Chapter05.xhtml#page_138)–[140](#13_Chapter05.xhtml#page_140)

regression coefficient, estimation of, [133](#13_Chapter05.xhtml#page_133)–[134](#13_Chapter05.xhtml#page_134)

residual analysis, [137](#13_Chapter05.xhtml#page_137)–[138](#13_Chapter05.xhtml#page_138)

simple and multiple regression problems, [121](#13_Chapter05.xhtml#page_121)–[122](#13_Chapter05.xhtml#page_122)

simple log transformation of outcome variable, [291](#16_Chapter08.xhtml#page_291)

standard query language (SQL), [17](#10_Chapter02.xhtml#page_17)

statistical learning (SL) algorithm, [2](#09_Chapter01.xhtml#page_2), [230](#15_Chapter07.xhtml#page_230)

defined, [1](#09_Chapter01.xhtml#page_1)

stochastic gradient boosting, [310](#16_Chapter08.xhtml#page_310)

synthetic minority over-sampling technique (SMOTE), [291](#16_Chapter08.xhtml#page_291)–[292](#16_Chapter08.xhtml#page_292)

synthetic minority over-sampling technique for regression with

Gaussian noise (SMOGN), [291](#16_Chapter08.xhtml#page_291)

#### **T**

text prepreprocessing

bag-of-words (BoW) model (*see* Bag-of-words (BoW) model)

topic modelling, [416](#17_Chapter09.xhtml#page_416)–[419](#17_Chapter09.xhtml#page_419)

trend plot, [84](#11_Chapter03.xhtml#page_84)–[87](#11_Chapter03.xhtml#page_87)

stairstep plot, [87](#11_Chapter03.xhtml#page_87)

twitter data visualization

count vector *vs.* count vector with stemming and lemmatization *vs.* TF-IDF vector, [391](#17_Chapter09.xhtml#page_391)–[392](#17_Chapter09.xhtml#page_392)

methods to improve BoW model, [372](#17_Chapter09.xhtml#page_372)–[386](#17_Chapter09.xhtml#page_386)

visualization of

bigrams, [386](#17_Chapter09.xhtml#page_386)–[391](#17_Chapter09.xhtml#page_391)

unigrams and words, [365](#17_Chapter09.xhtml#page_365)–[372](#17_Chapter09.xhtml#page_372)

URL, [394](#17_Chapter09.xhtml#page_394)–[395](#17_Chapter09.xhtml#page_395)

#### **U**

UBL package in R programming language, [291](#16_Chapter08.xhtml#page_291)

up-sample strategy, [290](#16_Chapter08.xhtml#page_290)

#### **V**

variance inflation factor (VIF), [149](#13_Chapter05.xhtml#page_149)–[150](#13_Chapter05.xhtml#page_150)

#### **W**

Weibull distribution, [106](#12_Chapter04.xhtml#page_106)

word embeddings, [353](#17_Chapter09.xhtml#page_353)

word-to-vec, [147](#13_Chapter05.xhtml#page_147)

#### **X**

XGBoost boosting technique

dataset, creation of, [323](#16_Chapter08.xhtml#page_323)–[324](#16_Chapter08.xhtml#page_324)

discussion of results, [328](#16_Chapter08.xhtml#page_328)–[330](#16_Chapter08.xhtml#page_330)

final model, [330](#16_Chapter08.xhtml#page_330)–[331](#16_Chapter08.xhtml#page_331)

grid search, [325](#16_Chapter08.xhtml#page_325)

hyper-parameters, [324](#16_Chapter08.xhtml#page_324)

model diagnostic, [325](#16_Chapter08.xhtml#page_325)–[327](#16_Chapter08.xhtml#page_327)

model prediction, [327](#16_Chapter08.xhtml#page_327)–[328](#16_Chapter08.xhtml#page_328)

parameters in

booster, [322](#16_Chapter08.xhtml#page_322)–[323](#16_Chapter08.xhtml#page_323)

general, [322](#16_Chapter08.xhtml#page_322)

learning task, [322](#16_Chapter08.xhtml#page_322)

saving of model, parameters in, [331](#16_Chapter08.xhtml#page_331)

search criteria, [324](#16_Chapter08.xhtml#page_324)

#### **Z**

zero and near-zero variance (NZV) features, [185](#14_Chapter06.xhtml#page_185)–[187](#14_Chapter06.xhtml#page_187)

<!DOCTYPE html>![Cover Image](images/Backcover.jpg)