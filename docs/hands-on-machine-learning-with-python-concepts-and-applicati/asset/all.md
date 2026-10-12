   

 

 

 

HANDS ON MACHINE LEARNING WITH PYTHON

Concepts and Applications

 

 

 

John Anderson & Peter Morgan

 

 

 

 

 

 

 

 

![C:\\Users\\CHADAD\\Downloads\\intelligent.png](images/00001.jpeg)

  

How to contact us

If you find any damage, editing issues or any other issues in this book please immediately notify our customer service by email at:

[contact@aisciences.net](mailto:contact@aisciences.net)

 

 

 

 

 

 

 

 

Our goal is to provide high-quality books for your technical learning in computer science subjects.

 

Thank you so much for buying this book.

 

 

![C:\\Users\\CHADAD\\Downloads\\intelligent.png](images/00002.jpeg)

  

 

Table of Contents

[Table of Contents](#part0000_split_002.html#_Toc521008050)

[Authors Biography](#part0000_split_006.html#_Toc521008051)

[From AI Sciences Publisher](#part0000_split_007.html#_Toc521008052)

[Preface](#part0000_split_009.html#_Toc521008053)

[Why Read This Book](#part0000_split_009.html#_Toc521008054)

[Who This Book is For](#part0000_split_009.html#_Toc521008055)

[Overview of what you’ll learn](#part0000_split_009.html#_Toc521008056)

[Installation & Setup](#part0000_split_011.html#_Toc521008057)

[Download Anaconda](#part0000_split_011.html#_Toc521008058)

[Running Jupyter Notebook](#part0000_split_011.html#_Toc521008059)

[Python Crash Course](#part0000_split_012.html#_Toc521008060)

[Strings, Lists, Functions, and More](#part0000_split_012.html#_Toc521008061)

[Jupyter Notebook](#part0000_split_012.html#_Toc521008062)

[Numpy, Pandas, Scipy , Matplotlib, Scikit-learn](#part0000_split_012.html#_Toc521008063)

[Numerical Python (Numpy)](#part0000_split_012.html#_Toc521008064)

[Pandas](#part0000_split_012.html#_Toc521008065)

[Scientific Python (Scipy)](#part0000_split_012.html#_Toc521008066)

[Matplotlib](#part0000_split_012.html#_Toc521008067)

[Scikit-Learn](#part0000_split_012.html#_Toc521008068)

[About Google TensorFlow](#part0000_split_012.html#_Toc521008069)

[Your First Machine Learning Project](#part0000_split_013.html#_Toc521008070)

[Titanic Survival Prediction](#part0000_split_013.html#_Toc521008071)

[Implications & Possibilities](#part0000_split_013.html#_Toc521008072)

[The General Workflow](#part0000_split_013.html#_Toc521008073)

[General Machine Learning Concepts](#part0000_split_014.html#_Toc521008074)

[What is Machine Learning](#part0000_split_014.html#_Toc521008075)

[Supervised Learning](#part0000_split_014.html#_Toc521008076)

[Unsupervised Learning](#part0000_split_014.html#_Toc521008077)

[Semi-supervised Learning Algorithms](#part0000_split_014.html#_Toc521008078)

[Reinforcement Learning Algorithms](#part0000_split_014.html#_Toc521008079)

[Deep Learning](#part0000_split_014.html#_Toc521008080)

[Overfitting and Underfitting](#part0000_split_014.html#_Toc521008081)

[Correctness](#part0000_split_014.html#_Toc521008082)

[The Bias-Variance Trade-off](#part0000_split_014.html#_Toc521008083)

[Feature Extraction and Selection](#part0000_split_014.html#_Toc521008084)

[Why Machine Learning is Popular](#part0000_split_014.html#_Toc521008085)

[Regression](#part0000_split_015.html#_Toc521008086)

[Simple and Multiple Linear Regression](#part0000_split_015.html#_Toc521008087)

[Logistic Regression](#part0000_split_015.html#_Toc521008088)

[Generalized Linear Models](#part0000_split_015.html#_Toc521008089)

[A Regression Example: Predicting Boston Housing Prices](#part0000_split_015.html#_Toc521008090)

[Steps To Carry Out Analysis](#part0000_split_015.html#_Toc521008091)

[Import Libraries:](#part0000_split_015.html#_Toc521008092)

[How to forecast and Predict](#part0000_split_015.html#_Toc521008093)

[K-Nearest Neighbors](#part0000_split_016.html#_Toc521008094)

[Introduction to K Nearest Neighbors](#part0000_split_016.html#_Toc521008095)

[How to create and test the K Nearest Neighbor classifier](#part0000_split_016.html#_Toc521008096)

[Another Application](#part0000_split_016.html#_Toc521008097)

[Calculating Similarity](#part0000_split_016.html#_Toc521008098)

[Locating Neighbors](#part0000_split_016.html#_Toc521008099)

[Generating Response](#part0000_split_016.html#_Toc521008100)

[Evaluating Accuracy](#part0000_split_016.html#_Toc521008101)

[The Curse of Dimensionality](#part0000_split_016.html#_Toc521008102)

[Naive Bayes](#part0000_split_017.html#_Toc521008103)

[Applications of Naive Bayes](#part0000_split_017.html#_Toc521008104)

[How to Build a Basic Model Using Naive Bayes in Python](#part0000_split_017.html#_Toc521008105)

[Decision Trees and Random Forest](#part0000_split_018.html#_Toc521008106)

[The Entropy of a Partition](#part0000_split_018.html#_Toc521008107)

[Creating a Decision Tree](#part0000_split_018.html#_Toc521008108)

[Random Forests](#part0000_split_018.html#_Toc521008109)

[Neural Networks](#part0000_split_019.html#_Toc521008110)

[Perceptrons](#part0000_split_019.html#_Toc521008111)

[Backpropagation](#part0000_split_019.html#_Toc521008112)

[How to run the Neural Network using TensorFlow](#part0000_split_019.html#_Toc521008113)

[How to get our data](#part0000_split_019.html#_Toc521008114)

[How to train and test the data](#part0000_split_019.html#_Toc521008115)

[Clustering](#part0000_split_020.html#_Toc521008116)

[Introduction to Clustering](#part0000_split_020.html#_Toc521008117)

[Example of Clustering](#part0000_split_020.html#_Toc521008118)

[Running K-means with Scikit-Learn](#part0000_split_020.html#_Toc521008119)

[Implementation of the Model](#part0000_split_020.html#_Toc521008120)

[Bottom-up Hierarchical Clustering](#part0000_split_020.html#_Toc521008121)

[K-means Clustering](#part0000_split_020.html#_Toc521008122)

[Network Analysis](#part0000_split_021.html#_Toc521008123)

[Betweenness centrality](#part0000_split_021.html#_Toc521008124)

[Eigenvector Centrality](#part0000_split_021.html#_Toc521008125)

[Recommender Systems](#part0000_split_021.html#_Toc521008126)

[Classification](#part0000_split_022.html#_Toc521008127)

[Multi-Class Classification](#part0000_split_022.html#_Toc521008128)

[Popular Classification Algorithms](#part0000_split_022.html#_Toc521008129)

[Support Vector Machine](#part0000_split_023.html#_Toc521008130)

[How to create and test the Support Vector Machine (SVM) classifier](#part0000_split_023.html#_Toc521008131)

[Deep Learning using TensorFlow](#part0000_split_024.html#_Toc521008132)

[Deep Learning Compared to Other Machine Learning Approaches](#part0000_split_024.html#_Toc521008133)

[Applications of Deep Learning](#part0000_split_024.html#_Toc521008134)

[Python Deep Learning Frameworks](#part0000_split_024.html#_Toc521008135)

[Install TensorFlow](#part0000_split_024.html#_Toc521008136)

[Installing TensorFlow on Windows](#part0000_split_024.html#_Toc521008137)

[Installing TensorFlow on Linux](#part0000_split_024.html#_Toc521008138)

[Installing TensorFlow on macOS](#part0000_split_024.html#_Toc521008139)

[How to Create a Neural Network Model](#part0000_split_024.html#_Toc521008140)

[Deep Learning Case Studies](#part0000_split_025.html#_Toc521008141)

[Bank Churn Modelling](#part0000_split_025.html#_Toc521008142)

[Sentiment Analysis](#part0000_split_025.html#_Toc521008143)

[Thank you !](#part0000_split_026.html#_Toc521008144)

[Sources & References](#part0000_split_027.html#_Toc521008145)

[Software, libraries, & programming language](#part0000_split_027.html#_Toc521008146)

[Datasets](#part0000_split_027.html#_Toc521008147)

[Online books, tutorials, & other references](#part0000_split_027.html#_Toc521008148)

[Thank you !](#part0000_split_028.html#_Toc521008149)

 

 

 

 

© Copyright 2018 by AI Sciences

All rights reserved.

First Printing, 2018

 

 

 

Edited by Davies Company

Ebook Converted and Cover by Pixels Studio 

Publised by AI Sciences LLC

 

ISBN-13: 978-1724731968 

ISBN-10: 1724731963

 

The contents of this book may not be reproduced, duplicated or transmitted without the direct written permission of the author.

Under no circumstances will any legal responsibility or blame be held against the publisher for any reparation, damages, or monetary loss due to the information herein, either directly or indirectly. 

 

 

 

 

 

 

 

 

  

 

Legal Notice:

You cannot amend, distribute, sell, use, quote or paraphrase any part or the content within this book without the consent of the author. 

Disclaimer Notice:

Please note the information contained within this document is for educational and entertainment purposes only. No warranties of any kind are expressed or implied. Readers acknowledge that the author is not engaging in the rendering of legal, financial, medical or professional advice. Please consult a licensed professional before attempting any techniques outlined in this book.

 

By reading this document, the reader agrees that under no circumstances is the author responsible for any losses, direct or indirect, which are incurred as a result of the use of information contained within this document, including, but not limited to, errors, omissions, or inaccuracies.

 

 

 

 

 

 

 

 

  

 

 

 

 

 

 

 

To my Wife Chelsea

 

 

 

 

 

 

 

 

 

 

 

 

  

 

Authors Biography

 

John Anderson is a data science researcher and expert in machine learning. After finishing his undergraduate degree in computer science at 2007, he went on to do data analysis in California. He's now an active data scientist researcher in social media, finance, and statistical computing applications.

 

 

 

 

 

 

 

 

 

 

  

From AI Sciences Publisher

 

 
| [![C:\\Users\\CHADAD\\Dropbox\\Electro\_books\\Covers\\dlf-as-CP-100-front.jpg](images/00003.jpeg)](https://www.amazon.com/Deep-Learning-Python-Guide-Pytorch-ebook/dp/B07DRGJNW7/ref=pd_sbs_351_2?_encoding=UTF8&pd_rd_i=B07DRGJNW7&pd_rd_r=22374875-7fd5-11e8-9d30-79f90a35b456&pd_rd_w=HTcS1&pd_rd_wg=buQSL&pf_rd_i=desktop-dp-sims&pf_rd_m=ATVPDKIKX0DER&pf_rd_p=5825442648805390339&pf_rd_r=YSH10PQYV367HCX3EZ0V&pf_rd_s=desktop-dp-sims&pf_rd_t=40701&psc=1&refRID=YSH10PQYV367HCX3EZ0V) || [![C:\\Users\\CHADAD\\Dropbox\\Electro\_books\\Covers\\dlwp-as-CP-130-front.jpg](images/00004.jpeg)](https://www.amazon.com/dp/B07DRGJNW7) |
| --- | --- |
| [![C:\\Users\\gchadad\\Downloads\\Covers\\dsfswp-ai-PM-115-front.jpg](images/00005.jpeg)](https://www.amazon.com/dp/B07F7QC635/ref=sspa_dk_detail_5?psc=1) || [![C:\\Users\\gchadad\\Dropbox\\Electro\_books\\Covers\\dafswp-ai-PM-115-front.jpg](images/00006.jpeg)](https://www.amazon.com/Data-Analysis-Scratch-Python-Guide-ebook/dp/B07F193447/ref=pd_rhf_dp_p_img_2?_encoding=UTF8&psc=1&refRID=JA8R5MVZ8GY1B12GB1DC) |

  

 

[WWW.AISCIENCES.NET](http://WWW.aisciences.net)

EBooks, free offers of ebooks and online learning courses.

Did you know that AI Sciences offers free eBooks versions of every books published? Please suscribe to our email list to be aware about our free ebook promotion. Get in touch with us at contact@aisciences.net for more details.

 

![C:\\Users\\CHADAD\\Downloads\\AI SCIENCES BOOKS (1).png](images/00007.jpeg)

At [www.aisciences.net](http://www.aisciences.net) , you can also read a collection of free books and received exclusive free ebooks.

 

 

 

 

 

  

Preface

 

“Machine learning will automate jobs that most people thought could only be done by people.” ”

―— Dave Waters

Why Read This Book

Machine learning is now changing how business, science, and engineering are done. Today machine learning might have already affected you. If you used a search engine or looked for products machine learning could be there in the background that made the results come out faster or personalized.

Machine learning has been directly or indirectly transforming our lives. Many experts even say that we’re just scratching the surface. We haven’t yet taken full advantage of what machine learning can bring.

So if you want to take advantage of machine learning and recognize the opportunities, it’s best to have a working knowledge about it. Aside from learning the field and positioning yourself to become more valuable in your organization (or start a business focused in machine learning), studying machine learning can become an amazing experience for you. It’s not easy and it will take a lot of time. Even if you read this book 5 times, it won’t be enough to really explore the potential and current capabilities of machine learning. This is just the start of your journey.

Who This Book is For

Well, first you should now be at least comfortable with programming and Python. We’ll give a crash course here and discuss the most important things about Python and programming. And you can always do a Google search whenever you’re stuck or unfamiliar with something (Stack Overflow and Stack Exchange are really good resources and communities).

Many other readers picked up this book because they want to shift to a new career (data scientist and machine learning engineer are the hottest jobs right now and the pay’s just incredible). Aside from awesome financial incentives (including a very cool tech office), machine learning engineers have the chance of working with the brightest minds from different fields. In fact, some who have PhDs in physics and statistics applied their expertise in tackling machine learning challenges.

There are also other readers who are just curious about machine learning. What is it and does it have the potential to wipe out humans? We can’t give a definitive answer to that because even experts are clueless of what the potential opportunity and threat machine learning can really bring. If you want to figure it out yourself and satisfy your curiosity, read on and hopefully search for other resources so you can learn more.

Overview of what you’ll learn

Our goal here is to show you examples and insights on how to do machine learning (step by step as promised) so in the near future, you can initiate and handle projects on your own. More importantly, we’ll focus on how to think properly about machine learning (gaining the understanding). Tools and techniques come and go but if you have a solid foundation, you’ll always be in a position to take advantage of this yet developing technology.

To start, we’ll download and install the necessary tools to get you going. Here we’ll be using mostly Python, Anaconda, Jupyter Notebook, and TensorFlow. Next is you’ll get a Python crash course so you can quickly review the most important concepts and dive straight to machine learning next.

To motivate you, we’ll quickly explore a simple (and popular) example of the use of machine learning (Titanic Survival Prediction). It’s a general example that has wide applications and implications. Once you understand how to predict survival rates, you’ll be half-ready to tackle many machine learning projects.

It was just half of the battle. You should then get a solid foundation about machine learning (Supervised Learning, Unsupervised Learning, Deep Learning). We’ll explore several examples so you can really see the potential and current applications of machine learning. Then also in the succeeding chapters we’ll discuss each one of those in detail. 

Near the end we’ll discuss how to improve our machine learning model. We’ll try to improve the accuracy and performance of our model so it can be more useful for predictions, optimizations, and other applications.

After reading this book and following through the examples, you’ll be in a better position to know whether machine learning is just hype or not. But this is just the beginning. Although this is a step-by-step machine learning guide using Python 3, it’s always good to continue the journey and stay curious about what the field and future holds.

Why this book?

This book is written to help you learn machine learning using Python programming. If you are an absolute beginner in this field, you’ll find that this book explains complex concepts in an easy to understand manner without math or complicated theorical elements. If you are an experienced data scientist, this book gives you a good base from which to explore machine learning application.

 

Topics are carefully selected to give you a broad exposure to machine learning application. While not overwhelming you with information overload. 

 

The example and cases studies are carefully chosen to demonstrate each algorithm and model so that you can gain a deeper understand of machine learning. Inside the book and in the appendices at the end of the book we provide you a convenient references.

 

You can download the source code for the project and other free books at:

[http://aisciences.net/](http://aisciences.net/code)book5 

  

Your Free Gift

As a way of saying thanks you for your purchase, AI Sciences Publishing Company offering you a free eBook in Machine Learning with Python written by the data scientist Alain Kaufmann.

[![C:\\Users\\gchadad\\Dropbox\\Electro\_books\\Covers\\bribes\_mlfs\_ai.jpg](images/00008.jpeg)](http://aisciences.net/free-books/)

It is a full book that contains useful machine learning techniques using python. It is 100 pages book with one bonus chapter focusing in Anaconda Setup & Python Crash Course.  AI Sciences encourage you to print, save and share. [You can download it by going to the link below](http://aisciences.net/free-books/) or by clicking in the book cover above.

[http://aisciences.net/free-books/](http://aisciences.net/free-books/)

 

[If you want to help us produce more material like this, then please leave an honest review on amazon. It really does make a difference.](https://www.amazon.com/dp/B07FTPKJMM)

  

Installation & Setup

Are you excited on machine learning? We’ll get into that later. But first, we have to set up everything. We’ll use the most popular and convenient tools so you can focus more on the machine learning itself.

### Download Anaconda

If you don’t yet have Anaconda installed, go to [https://www.anaconda.com/download/](https://www.anaconda.com/download/), download the installer and double click it (mostly it’s just standard installation). Choose Python 3+ version so the results will be consistent and you won’t run to much problem. Also, Python 3 is where everything goes (Python 2 will retire in year 2020).

Anyway, why Anaconda? It’s a popular choice among many data scientists and machine learning engineers worldwide (over 6 million users already). It already includes Python 3 and many of the libraries and packages useful for machine learning, which is why the installer is a sizable file (500+ MB).

Some of the most awesome packages that you’ll encounter again and again in this book are:

*   Numpy
*   Scipy
*   Matplotlib
*   Pandas
*   Scikit-learn
*   NLTK (Natural Language Toolkit)
*   Jupyter Notebook

If you quickly want to get familiar with Anaconda, here’s a PDF cheat sheet (which you can also use as reference in the future):

[https://docs.anaconda.com/\_downloads/Anaconda-Starter-Guide-Cheat-Sheet.pdf](https://docs.anaconda.com/_downloads/Anaconda-Starter-Guide-Cheat-Sheet.pdf)

### Running Jupyter Notebook

By this time you should now have Anaconda installed. The next step is to run Jupyter Notebook. It’s a browser-based notebook where you can add code, text, and notes. Literally we can think of it as a notebook, which is why many university professors and researchers use it.

If you have the Anaconda installed already, find the Anaconda Prompt from your installed programs. Open it and then type “jupyter notebook” (without the quotes) and this will launch the notebook into your default browser. You can see your files and folders there. You can navigate to your target folder and create new notebooks there.

It’s very intuitive to use and you’ll learn how to use it as you read along through our examples later. You can also explore more about Jupyter Notebook by reading their Quick Start Guide:

[http://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/](http://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/)

Anyway, here’s the Zen of Python (guiding principles for Python’s design found at [https://www.python.org/dev/peps/pep-0020/](https://www.python.org/dev/peps/pep-0020/)). We included it here as a reminder of excellent coding and work practices:

Beautiful is better than ugly.  
Explicit is better than implicit.  
Simple is better than complex.  
Complex is better than complicated.  
Flat is better than nested.  
Sparse is better than dense.  
Readability counts.  
Special cases aren't special enough to break the rules.  
Although practicality beats purity.  
Errors should never pass silently.  
Unless explicitly silenced.  
In the face of ambiguity, refuse the temptation to guess.  
There should be one-- and preferably only one --obvious way to do it.  
Although that way may not be obvious at first unless you're Dutch.  
Now is better than never.  
Although never is often better than \*right\* now.  
If the implementation is hard to explain, it's a bad idea.  
If the implementation is easy to explain, it may be a good idea.  
Namespaces are one honking great idea -- let's do more of those!

 

 

 

 

 

 

  

Python Crash Course

Now you’ve installed the necessary tools and packages. The next step is to quickly review Python so you can keep up with the discussions and examples later.

This won’t be the most comprehensive guide about Python. But this might be enough to keep you going because we’ll cover the basics and the most important things you can use for machine learning later. And because of Python’s intuitive syntax, you can still follow along with the lessons in the succeeding chapters.

Strings, Lists, Functions, and More

We can assign values (strings, integers, and floats) to variables and access them later (and do a bunch of other things to them). Here’s an example:

yourName = ‘Felicity’

print(yourName)

Returns ‘Felicity’

print(yourName\[0\])

This prints ‘F’, the first letter of ‘Felicity.’ Indexing starts at zero in Python.

print(yourName\[0:3\])

Result would be ‘Fel’. Starts at zero index but excludes index 3.

print(len(yourName))

Counts the number of letters or finds out the “length” of the string. So the result here would be 8.

Speaking of numbers, we can also assign numeric values to variables:

yourAge = 22

print(yourAge)  #This is a comment. Anyway, this prints ‘22’

print(yourAge \* 2)   #Prints 22\*2 which is 44

yourAge = 25   #We can also reassign values to variables. 

Let’s now talk about Lists (one of the most useful and popular data structures in Python:

myList = \[1,2,3,4\]

myList.append(5)   #myList then becomes \[1,2,3,4,5\]

myList\[0\]   #this returns the first value in the list, which is 1. Remember indexing in Python starts at zero.

print(len(myList))   #Prints the “length” of the list, which in this case 5.

Now let’s get into Functions and Flow Control (If, Elif, and Else statements):

def add\_numbers(a,b):

return a + b

print(add\_numbers(3,4))

#First we define a function and include an instruction. 

#Then we call or test it but this time include the numbers.

#The function add\_numbers will add 3 and 4, and print 7.

def if\_even(num):

if num % 2 == 0:

print(“Number is even.”)

else:

print(“It’s odd.”)

if\_even(24)   #This returns “Number is even.”

if\_even(25)   #This returns “It’s odd.”

Well, that’s the end of our Python crash course. Next is let’s discuss how to use Modules.

Jupyter Notebook

Data science is an experimental endeavour as hypothesis needs to be tested out to see whether the data upholds them. Jupyter notebook is an interactive web application that bundles an IPython shell, which is an enhanced shell for Python computations. Code, text and visualizations can be written alongside each other and stored in a special notebook format. This means that projects can be shared easily across teams and code can be easily reproduced as every functionality that is required to execute a project is bundled in the notebook. Jupyter notebooks supports many programming languages like R, Julia, Python etc. Jupyter in Python are powered by the IPython shell which provides additional “magic” functions that are not available in Python but are generally useful for interactive computation.

 

Jupyter notebooks also supports Latex and as a result mathematical equations can be written inline in cell blocks. Data visualization is also possible inline and detailed documentation or explanations can be incorporated in a notebook by using markdown syntax.

 

IPython and Jupyter notebook are automatically installed with Anaconda. To access the Jupyter notebook interface run the following command from a terminal.

$ jupyter notebook \# command to launch jupyter notebook web interface

The command above, opens a window in a browser session containing the Jupyter notebook web interface. The Jupyter notebook session is opened in the same directory where the command is run.

 

![](images/00009.jpeg)

 

You can navigate to a notebook file and click on it to run it or a create a new notebook from the interface.

 

![](images/00010.jpeg)

 

Once a new notebook is created, it launches a new instance from which coding can be carried out interactively.

![](images/00011.jpeg)

 

Jupyter notebooks are very popular in the fields of data science and machine learning as they offer a specialized format that encapsulates coding, visualization and documentation.

 

Numpy, Pandas, Scipy , Matplotlib, Scikit-learn

Conveniently we’ll use modules and libraries for our machine learning examples and projects. These contain pre-built code so we don’t have to write everything from scratch. Often these are not loaded by default so we first have to “import” them so we can use them.

That’s what we’ll do when using numpy, pandas, matplotlib, and scikit-learn. Here are examples of how to import them:

import numpy as np

import pandas as pd

import matplotlib.pyplot as plt

#Importing datasets, classifiers, and metrics

from sklearn import datasets, svm, metrics

Anyway, why use numpy and the other modules? NumPy is the fundamental package for scientific computing with Python. Also, using numpy allows for faster access of items compared to traditional Lists.

What about pandas? Here in this book pandas will be used to import and read data. From their website ([https://pandas.pydata.org/](https://pandas.pydata.org/)):

“pandas is an open source, BSD-licensed library providing high-performance, easy-to-use data structures and data analysis tools for the Python programming language.”

Aside from accessing the data, often we also have to visualize it. That’s where matplotlib comes in ([https://matplotlib.org/](https://matplotlib.org/)):

“Matplotlib is a Python 2D plotting library which produces publication quality figures in a variety of hardcopy formats and interactive environments across platforms.”

There are other data visualization libraries such as Bokeh and seaborn. These can produce more awesome visuals but for this book we’ll mostly use matplotlib.

And finally, let’s talk about scikit-learn. From their website ([http://scikit-learn.org/stable/index.html](http://scikit-learn.org/stable/index.html)):

scikit-learn

Machine Learning in Python

*   Simple and efficient tools for data mining and data analysis
*   Accessible to everybody, and reusable in various contexts
*   Built on NumPy, SciPy, and matplotlib
*   Open source, commercially usable - BSD license

With scikit-learn you can perform the following machine learning tasks:

*   Classification (which category an item belongs to?)
*   Regression (predicting a value)
*   Clustering (reveal subgroups in the data)
*   Dimensionality Reduction (reduce number of random variables to consider for easier visualization)
*   Model Selection (choose and compare models and their accuracies)
*   Preprocessing (standardization of datasets and feature extraction)

In short, scikit-learn is a convenient and powerful tool to do machine learning in Python. It may not be the best or most efficient, but it’s good enough for most purposes especially for studying machine learning.

Numerical Python (Numpy)

Numpy is the main numerical computing library in Python. It provides access to a multidimensional array object and exposes several methods through which operations can be done on these arrays. It features support for linear algebra operations such as matrix multiplication, inner product, identity operations etc. Numpy interfaces with low level libraries written in C and Fortran and passes off actual computation to these faster and more efficient libraries. As a result, vanilla Python control structures like loops are never used when performing numerical computation because they are significantly slower. Numpy can be seen as providing a set of Python APIs which enables efficient scientific computing.

 

Numpy arrays can be initiated by nested Python lists. The level of nesting specifies the rank of the array.

 

import numpy as np

 

a = np.array(\[\[1, 2, 3\], \[4, 5, 6\]\])   # create a rank 2 array

print(type(a))

print(a.shape)

 

![](images/00012.jpeg)

 

The array created is of rank 2 which means that it is a matrix. We can see this clearly from the size of the array printed. It contains 2 rows and 3 columns hence size (m, n).

 

Arrays can also be initialized randomly from a distribution such as the normal distribution. Trainable parameters of a model such as the weights are usually initialized randomly.

 

b = np.random.random((2,2))  # create an array filled with random values

print(b)

print(b.shape)

 

![](images/00013.jpeg)

 

Numpy contains many methods for manipulation of arrays, one of such is matrix product. Let us look at an example of matrix product using Numpy.

 

![](images/00014.jpeg)

 

x = np.array(\[\[1,2\],\[3,4\]\])

y = np.array(\[\[5,6\],\[7,8\]\])

 

\# matrix product

print(np.dot(x, y))

 

The example above is computed almost instantly and shows the power of Numpy.

Pandas

Pandas is a data manipulation library written in Python which features high performance data structures for table and time series data. Pandas is used extensively for data analysis and most data loading, cleaning and transformation tasks are performed in Pandas. Pandas is an integral part of the Python data science ecosystem as data is rarely in a form that can be fed directly into machine learning models. Data from the real world is usually messy, contains missing values and in need of transformation. Pandas supports many file types like CSV, Excel spreadsheets, Python pickle format, JSON, SQL etc.

 

There are two main types of Pandas data structures - series and dataframe. Series is the data structure for a single column of data while a dataframe stores 2-dimensional data analogous to a matrix. In other words, a dataframe contains data stored in many columns.

 

The code below shows how to create a Series object in Pandas.

 

import pandas as pd

 

s = pd.Series(\[1,3,5,np.nan,6,8\])

 

print(s)

 

To create a dataframe, we can run the following code.

 

df = pd.DataFrame(np.random.randn(6,4), columns=list('ABCD'))

 

print(df)

 

Pandas loads the file formats it supports into a dataframe and manipulation on the dataframe can then occur using Pandas methods.

Scientific Python (Scipy)

Scipy is a scientific computing library geared towards the fields of mathematics, science and engineering. It is built on top of Numpy and extends it by providing additional modules for optimization, technical computing, statistics, signal processing etc. Scipy is mostly used in conjunction with other tools in the ecosystem like Pandas and matplotlib.

 

Here is a simple usage of scipy that finds the inverse of a matrix.

 

from scipy import linalg

z = np.array(\[\[1,2\],\[3,4\]\])

 

print(linalg.inv(z))

 

![](images/00015.gif)

Matplotlib

Matplotlib is a plotting library that integrates nicely with Numpy and other numerical computation libraries in Python. It is capable of producing quality plots and is widely used in data exploration where visualization techniques are important. Matplotlib exposes an object oriented API making it easy to create powerful visualizations in Python. Note that to see the plot in Jupyter notebooks you must use the matplotlib inline magic command.

 

Here is an example that uses Matplotlib to plot a sine waveform.

 

\# magic command for Jupyter notebooks

%matplotlib inline

 

import matplotlib.pyplot as plt

 

\# compute the x and y coordinates for points on a sine curve

x = np.arange(0, 3 \* np.pi, 0.1)

y = np.sin(x)

 

\# plot the points using matplotlib

plt.plot(x, y)

plt.show()  # Show plot by calling plt.show()

 

![](images/00016.jpeg)

Scikit-Learn

Scikit-Learn is the most popular machine learning library in the Python ecosystem. It is a very mature library and contains several algorithms for classification, regression and clustering. Many common algorithms are available in Scikit-Learn and it exposes a consistent interface to access them, therefore learning how to work with one classifier in Scikit-Learn means that you would be able to work with others as the names of the methods that are called to train a classifier are the same regardless of the underlying implementation.

 

We would rely heavily on Scikit-Learn for our modelling tasks as we dive deeper into data science in the following sections of this book. Here is a simple example of creating a classifier and training it on one of the bundled datasets.

 

\# sample decision tree classifier

from sklearn import datasets

from sklearn import metrics

from sklearn.tree import DecisionTreeClassifier

 

\# load the iris datasets

dataset = datasets.load\_iris()

 

\# fit a CART model to the data

model = DecisionTreeClassifier()

model.fit(dataset.data, dataset.target)

print(model)

 

\# make predictions

expected = dataset.target

predicted = model.predict(dataset.data)

 

\# summarize the fit of the model

print(metrics.classification\_report(expected, predicted))

print(metrics.confusion\_matrix(expected, predicted))

 

Here is the output. Do not worry if you do not understand the code. We would go through each part of the code in more detail in subsequent sections.

 

![](images/00017.jpeg)

 

About Google TensorFlow

TensorFlow is “An open source machine learning framework for everyone.” Also,

…”it comes with strong support for machine learning and deep learning and the flexible numerical computation core is used across many other scientific domains.”

In other words, if your project is mainly about machine learning and deep learning then TensorFlow can make it a bit easier and more efficient for you. But why not use scikit-learn instead?

Scikit-learn comes with ready off-the-shelf algorithms which means you’ll only require a few lines of code to do machine learning. On the other hand, TensorFlow shines if you want to focus on Deep Learning.

In this modern era of machine learning it’s good to learn both TensorFlow and scikit-learn. Also, the latter is still useful for many data preprocessing task before using TensorFlow. So in general, it’s good to be familiar with the most popular tools out there. Don’t worry and just focus on the basics and principles. Once you’ve done that, you’ll have a solid knowledge base you can take anywhere you go.

 

 

 

 

 

 

  

Your First Machine Learning Project

Show, don’t tell.

It’s still the best way to explain and illustrate something. Instead of writing another 1,000 words to explain what machine learning is, let’s just dive straight into an example.

Titanic Survival Prediction

The sinking of Titanic on April 1912 is one of the most devastating maritime disasters in history. Over 1,500 lives were lost. Fortunately, there were more than 700 survivors (last living survivor of Titanic has died at age 97).

For the purpose of learning, our goal here is to apply machine learning in survival prediction. Take note that we already have labelled data (person and whether he or she had survived or not). The goal here is to learn from data (the training data) and apply that learning into new or unseen data (test set).

In other words, our computer and model will derive patterns and “insights” from data so it can make predictions. In this case here, the goal is to predict who would be the survivors based on available data. As described in Kaggle ([https://www.kaggle.com/c/titanic](https://www.kaggle.com/c/titanic)), here’s the problem definition:

“Knowing from a training set of samples listing passengers who survived or did not survive the Titanic disaster, can our model determine based on a given test dataset not containing the survival information, if these passengers in the test dataset survived or not.”

It’s true that luck plays a huge role in survival. But other factors can also affect the survival probability. For instance, if the passenger was a child or in the upper class, he or she had better chances of surviving.

Anyway, let’s just start with the machine learning so we can better explain this (Source: [https://www.kaggle.com/startupsci/titanic-data-science-solutions/notebook](https://www.kaggle.com/startupsci/titanic-data-science-solutions/notebook)):

The first step is to focus on the problem and then look at the data. We must not get excited with implementing sophisticated algorithms. Often, the non-machine learning tasks are more important in defining and solving a problem.

To access the data, we start by using pandas:

import pandas as pd

Next step is to access the data and get it ready for later processing and analyzing:

train\_df = pd.read\_csv('../input/train.csv')  
test\_df = pd.read\_csv('../input/test.csv')  
combine = \[train\_df, test\_df\]

Remember that the process is to first learn from training (train\_df) and then test that learning into test\_df and see how good are our predictions.

Once our data’s ready, let’s take a peek:

train\_df.head(10)

![](images/00018.jpeg)

print(train\_df.columns.values)

![](images/00019.jpeg)

Notice that there are Categorical, Ordinal (Passenger Class), and Numerical features. Also it’s possible that there are a lot of blank, null, and empty values (e.g. some Cabin values for passengers are NaN) both in training and test data. We should correct them first before the machine learning proper:

train\_df.info()  
print('\_'\*40)  
test\_df.info()

<class 'pandas.core.frame.DataFrame'>  
RangeIndex: 891 entries, 0 to 890  
Data columns (total 12 columns):  
PassengerId    891 non-null int64  
Survived       891 non-null int64  
Pclass         891 non-null int64  
Name           891 non-null object  
Sex            891 non-null object  
Age            714 non-null float64  
SibSp          891 non-null int64  
Parch          891 non-null int64  
Ticket         891 non-null object  
Fare           891 non-null float64  
Cabin          204 non-null object  
Embarked       889 non-null object  
dtypes: float64(2), int64(5), object(5)  
memory usage: 83.6+ KB  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
<class 'pandas.core.frame.DataFrame'>  
RangeIndex: 418 entries, 0 to 417  
Data columns (total 11 columns):  
PassengerId    418 non-null int64  
Pclass         418 non-null int64  
Name           418 non-null object  
Sex            418 non-null object  
Age            332 non-null float64  
SibSp          418 non-null int64  
Parch          418 non-null int64  
Ticket         418 non-null object  
Fare           417 non-null float64  
Cabin          91 non-null object  
Embarked       418 non-null object  
dtypes: float64(2), int64(4), object(5)  
memory usage: 36.0+ KB

Notice there there are many null objects for the values in different features. Next step is to further explore the data for early insights and general ideas:

![](images/00020.jpeg)

Here are a few of the most notable things from that data summary:

*   891 or 40% of the actual number of passengers on board the Titanic (2,224).
*   Nearly 30% of the passengers had siblings and/or spouse aboard (in the SibSp column).

Most passengers (> 75%) did not travel with parents or children (in the Parch column).

Now we got warmed up with the data. The next step is to eliminate obvious Features that have nothing to do with survival. This is an important step. Before applying sophisticated algorithms, it’s always good to eliminate first the unnecessary.

Does a person’s name have anything to do with survival? Safe to say the answer is no. So we drop the Name and exclude it from our model later.

What about a person’s ticket number? Which person gets a particular number is random. So it’s safe to exclude the Ticket feature from our data. It’s also the case with PassengerId.

Finally, notice that the Cabin feature has a lot of null values (only 204 are non-null objects out of 891, it means a large percentage of the values are null).

Aside from elimination, we also have to make a few assumptions. This is a natural part of data analysis and machine learning. We start with a few assumptions and then figure out if they make sense in the end.

Our first assumption is that Women (in our dataset it’s Sex = female) were more likely to have survived (e.g. they’re priorities in emergencies in rescues). Children and upper class passengers (Pclass = 1) also had better survival chances.

Good news is we can actually test those assumptions and see early if they make sense:

train\_df\[\['Pclass', 'Survived'\]\].groupby(\['Pclass'\], as\_index=False).mean().sort\_values(by='Survived', ascending=False)

![](images/00021.jpeg)

Notice that Pclass = 1 (upper class passengers) had the highest survival rate. Let’s look at Gender next:

train\_df\[\["Sex", "Survived"\]\].groupby(\['Sex'\], as\_index=False).mean().sort\_values(by='Survived', ascending=False)

![](images/00022.jpeg)

Over 74% was the survival rate among women.

What about passengers with Siblings and/or Spouses with them:

train\_df\[\["SibSp", "Survived"\]\].groupby(\['SibSp'\], as\_index=False).mean().sort\_values(by='Survived', ascending=False)

![](images/00023.jpeg)

And let’s also look at the survival rate of passengers with Parents and/or Children with them:

train\_df\[\["Parch", "Survived"\]\].groupby(\['Parch'\], as\_index=False).mean().sort\_values(by='Survived', ascending=False)

![](images/00024.jpeg)

The Features mentioned could somehow affect survival chances of passengers (but remember luck still had a role, so 100% correct predictions might be impossible to achieve).

For further analysis, let’s visualize the data (this could be much easier to interpret). First, let’s import the necessary libraries and packages:

import seaborn as sns  
import matplotlib.pyplot as plt  
%matplotlib inline   #so that plots will show in our notebook inline

Then, we set up the visuals (starting with Age):

g = sns.FacetGrid(train\_df, col='Survived')  
g.map(plt.hist, 'Age', bins=20)

![](images/00025.jpeg)

Notice in the right histogram (shows frequency of values) that many Infants survived (look at near 0 age). Also note that some old passengers (near age 80) survived. This confirms our earlier assumption that Age is a relevant feature for our later analysis.

Let’s also visualize Pclass (Passenger class) and whether they survived (1) or not (0):

grid = sns.FacetGrid(train\_df, col='Survived', row='Pclass', size=2.2, aspect=1.6)  
grid.map(plt.hist, 'Age', alpha=.5, bins=20)  
grid.add\_legend();

![](images/00026.jpeg)

Notice that the upper right corner (Pclass = 1 | Survived = 1) where the survivors of first class are located is quite thick (high density). Also notice the bottom left corner (Pclass = 3 | Survived = 0) or the non-survivors with 3rd passenger class is also dense. In other words, Passenger Class is correlated with survival (e.g. 1st class passengers have better chances).

Let’s explore further. If a passenger embarked in a different location, does it affect his/her chances? It’s quite tricky but let’s explore anyway:

grid = sns.FacetGrid(train\_df, row='Embarked', size=2.2, aspect=1.6)  
grid.map(sns.pointplot, 'Pclass', 'Survived', 'Sex', palette='deep')  
grid.add\_legend()

![](images/00027.jpeg)

Embarked (S = Southampton; C = Cherbourg; Q = Queenstown)

Note that males who embarked on Cherbourg (Embarked = C) had higher survival rates. Does this mean the Embarked feature has an effect on survival? One possible cause is that males who embarked on Cherbourg were in Pclass = 1 or 2. In other words, survival rate had more to do with Pclass, than with Embarked feature. But how do we confirm this? Here’s one way:

grid = sns.FacetGrid(train\_df, row='Embarked', col='Survived', size=2.2, aspect=1.6)  
grid.map(sns.barplot, 'Sex', 'Fare', alpha=.5, ci=None)  
grid.add\_legend()

![](images/00028.jpeg)

We also considered an additional feature here (Fare). Notice that passengers who paid higher fares had better survival chances. Also note there’s a correlation between port of embarkation and survival rates. As a result, it’s good to include Fare in our analysis later.

The next step then is to exclude the irrelevant features and include the relevant ones.

print("Before", train\_df.shape, test\_df.shape, combine\[0\].shape, combine\[1\].shape)  
  
train\_df = train\_df.drop(\['Ticket', 'Cabin'\], axis=1)  
test\_df = test\_df.drop(\['Ticket', 'Cabin'\], axis=1)  
combine = \[train\_df, test\_df\]  
  
"After", train\_df.shape, test\_df.shape, combine\[0\].shape, combine\[1\].shape

Here are the results:

Before (891, 12) (418, 11) (891, 12) (418, 11)  
After (891, 10) (418, 9) (891, 10) (418, 9)

There are fewer features because we dropped ‘Ticket’ and ‘Cabin’ from our training and test data.

Remember earlier that we also have to remove Name and PassengerId because they seem to have nothing to do with survival rates. But the Name could actually be a “signal” for the person’s survival. For instance, if there’s a “Miss” or “Mrs.” in the person’s indicated name, most likely it’s a she (which means higher survival rates because female).

As a consequence, perhaps it’s good to create a new feature (“Title”) because this may correlate with survival rates. We can accomplish that through the following code (you should be familiar with Regular Expressions in Python):

for dataset in combine:  
    dataset\['Title'\] = dataset.Name.str.extract(' (\[A-Za-z\]+)\\.', expand=False)  
  
pd.crosstab(train\_df\['Title'\], train\_df\['Sex'\])

![](images/00029.jpeg)

There are just too many titles. Perhaps it’s good to group most of the titles into “Rare” for convenience and then view the Title and corresponding survival percentage:

for dataset in combine:  
    dataset\['Title'\] = dataset\['Title'\].replace(\['Lady', 'Countess','Capt', 'Col',\\  
 'Don', 'Dr', 'Major', 'Rev', 'Sir', 'Jonkheer', 'Dona'\], 'Rare')  
  
    dataset\['Title'\] = dataset\['Title'\].replace('Mlle', 'Miss')  
    dataset\['Title'\] = dataset\['Title'\].replace('Ms', 'Miss')  
    dataset\['Title'\] = dataset\['Title'\].replace('Mme', 'Mrs')  
      
train\_df\[\['Title', 'Survived'\]\].groupby(\['Title'\], as\_index=False).mean()

![](images/00030.jpeg)

Notice that Miss and Mrs have the highest survival rates (even a lot higher than the Rare titles combined). In other words, the Title from the Name (but not the name itself) correlates with survival rates.

Again, for convenience let’s convert those Titles (categorical features) into ordinal features (just like Pclass).

title\_mapping = {"Mr": 1, "Miss": 2, "Mrs": 3, "Master": 4, "Rare": 5}  
for dataset in combine:  
    dataset\['Title'\] = dataset\['Title'\].map(title\_mapping)  
    dataset\['Title'\] = dataset\['Title'\].fillna(0)  
  
train\_df.head()

![](images/00031.jpeg)

Now that we have extracted useful information (Title) from the Name and made it into a new feature, we can then safely drop the Name feature. We should also then drop the PassengerId.

train\_df = train\_df.drop(\['Name', 'PassengerId'\], axis=1)  
test\_df = test\_df.drop(\['Name'\], axis=1)  
combine = \[train\_df, test\_df\]  
train\_df.shape, test\_df.shape

((891, 9), (418, 9))

train\_df.head()

![](images/00032.jpeg)

It’s a lot cleaner now and we ended up with a lot fewer features. This will make analysis our much easier and faster later on.

Also, we have to convert features that contain strings (Sex = female or male) into numerical values. This is often a requirement for most machine learning algorithms. After all, processing text data vs numerical values require different approaches (more on this later when we mention Natural Language Processing).

Converting categorical feature into numeric values:

for dataset in combine:  
    dataset\['Sex'\] = dataset\['Sex'\].map( {'female': 1, 'male': 0} ).astype(int)  
  
train\_df.head()

![](images/00033.jpeg)

There you have it. It’s all numeric and we’ve excluded the irrelevant features. 

Special note: And notice that we haven’t done any machine learning yet. Well, that’s because most data science and machine learning projects will involve a lot of thinking and preprocessing first. Before using scikit-learn or TensorFlow, you will have to spend a lot of time in the fundamentals of real data analysis.

But that doesn’t stop there. Before doing any real exciting machine learning, remember the null values mentioned before. Somehow we have to make them “not null” by injecting new values. But we don’t have to inject any value, the values we add have to be reasonable. 

One way to accomplish this is by using other correlated features (e.g. noting correlation among Age, Gender, and Pclass). Here’s how to do it in code:

  
grid = sns.FacetGrid(train\_df, row='Pclass', col='Sex', size=2.2, aspect=1.6)  
grid.map(plt.hist, 'Age', alpha=.5, bins=20)  
grid.add\_legend()

![](images/00034.jpeg)

Next is prepare an empty array (using numpy). This is where we’ll put the Age values that will replace the null values. The guesses will be based on Pclass x Gender combinations:

import numpy as np

guess\_ages = np.zeros((2,3))  
guess\_ages

![](images/00035.jpeg)

Then we iterate over Pclass (1, 2, 3) and Sex (0 or 1) so we can calculate the guessed Age values for 6 combinations. We can do that through the following code:

for dataset in combine:  
    for i in range(0, 2):  
        for j in range(0, 3):  
            guess\_df = dataset\[(dataset\['Sex'\] == i) & \\  
                                  (dataset\['Pclass'\] == j+1)\]\['Age'\].dropna()  
  
            age\_guess = guess\_df.median()  
  
            guess\_ages\[i,j\] = int( age\_guess/0.5 + 0.5 ) \* 0.5  
              
    for i in range(0, 2):  
        for j in range(0, 3):  
            dataset.loc\[ (dataset.Age.isnull()) & (dataset.Sex == i) & (dataset.Pclass == j+1),\\  
                    'Age'\] = guess\_ages\[i,j\]  
  
    dataset\['Age'\] = dataset\['Age'\].astype(int)  
  
train\_df.head()

![](images/00036.jpeg)

Now we’ve taken care of missing values. Next is we create Age bands (range of age) and put them side by side with Survived:

![](images/00037.jpeg)

For convenience and neatness, we can then transform those Age Bands into ordinals:

for dataset in combine:      
    dataset.loc\[ dataset\['Age'\] <= 16, 'Age'\] = 0  
    dataset.loc\[(dataset\['Age'\] > 16) & (dataset\['Age'\] <= 32), 'Age'\] = 1  
    dataset.loc\[(dataset\['Age'\] > 32) & (dataset\['Age'\] <= 48), 'Age'\] = 2  
    dataset.loc\[(dataset\['Age'\] > 48) & (dataset\['Age'\] <= 64), 'Age'\] = 3  
    dataset.loc\[ dataset\['Age'\] > 64, 'Age'\]  
train\_df.head()

![](images/00038.jpeg)

The Age feature is now ordinal (instead of a wide numeric range). And we can now “drop” the AgeBand feature (because after all we already extracted the important info from it and put it in the Age feature):

train\_df = train\_df.drop(\['AgeBand'\], axis=1)  
combine = \[train\_df, test\_df\]  
train\_df.head()

![](images/00039.jpeg)

Let’s go back to Parch (parents and children) and SibSp (siblings and spouse). Actually we can combine them into one feature (for convenience) which we’ll name as “FamilySize” (and let’s put it side by side with Survived for an insight:

for dataset in combine:  
    dataset\['FamilySize'\] = dataset\['SibSp'\] + dataset\['Parch'\] + 1  
  
train\_df\[\['FamilySize', 'Survived'\]\].groupby(\['FamilySize'\], as\_index=False).mean().sort\_values(by='Survived', ascending=False)

![](images/00040.jpeg)

We might also want to know the correlation of survival rate and whether a passenger is alone or not:

![](images/00041.jpeg)

This tells us that if a passenger had companion/s, he or she had better chances. So let’s just discard Parch, SibSp, and FamilySize and focus on the isAlone:

train\_df = train\_df.drop(\['Parch', 'SibSp', 'FamilySize'\], axis=1)  
test\_df = test\_df.drop(\['Parch', 'SibSp', 'FamilySize'\], axis=1)  
combine = \[train\_df, test\_df\]  
  
train\_df.head()

![](images/00042.jpeg)

We’re not into the actual machine learning yet. Most of what we did so far is just about data transformation and manipulation. Many of the previous steps were actually optional. You might even come up with new ways of discarding or creating new features. You might also discard most features but our model won’t be learning optimally from available resources.

Also, remember that we made assumptions. Good thing is we’re able to test them early and see whether they’re valid or not.

Let’s move forward. We’re not done yet with data transformation and manipulation (I know you’re really excited diving into Machine Learning). We can create an artificial feature that combines Pclass and Age (for further simplification and reduction of number of features):

for dataset in combine:  
    dataset\['Age\*Class'\] = dataset.Age \* dataset.Pclass  
  
train\_df.loc\[:, \['Age\*Class', 'Age', 'Pclass'\]\].head(10)

![](images/00043.jpeg)

Also notice earlier that a categorical feature (Embarked) has two missing values in the dataset. For speed and convenience, we can simply fill it out with the value with the highest frequency (or what we call the mode):

freq\_port = train\_df.Embarked.dropna().mode()\[0\]  
freq\_port

‘S’

for dataset in combine:  
    dataset\['Embarked'\] = dataset\['Embarked'\].fillna(freq\_port)  
      
train\_df\[\['Embarked', 'Survived'\]\].groupby(\['Embarked'\], as\_index=False).mean().sort\_values(by='Survived', ascending=False)

![](images/00044.jpeg)

As you might have realised already, we need to convert the values in the categorical feature (Embarked) into numeric ones. Here’s how to do it through mapping (similar to what we did in Gender):

for dataset in combine:  
    dataset\['Embarked'\] = dataset\['Embarked'\].map( {'S': 0, 'C': 1, 'Q': 2} ).astype(int)  
  
train\_df.head()

![](images/00045.jpeg)

We can also complete the missing values in the Fare feature as we did with Embarked. This is often a requirement so our model or algorithm will really work well:

test\_df\['Fare'\].fillna(test\_df\['Fare'\].dropna().median(), inplace=True)  
test\_df.head()

![](images/00046.jpeg)

Then we create a FareBand for simplicity:

train\_df\['FareBand'\] = pd.qcut(train\_df\['Fare'\], 4)  
train\_df\[\['FareBand', 'Survived'\]\].groupby(\['FareBand'\], as\_index=False).mean().sort\_values(by='FareBand', ascending=True)

![](images/00047.jpeg)

We then convert it into ordinal values (similar to what we did in AgeBand).

for dataset in combine:  
    dataset.loc\[ dataset\['Fare'\] <= 7.91, 'Fare'\] = 0  
    dataset.loc\[(dataset\['Fare'\] > 7.91) & (dataset\['Fare'\] <= 14.454), 'Fare'\] = 1  
    dataset.loc\[(dataset\['Fare'\] > 14.454) & (dataset\['Fare'\] <= 31), 'Fare'\]   = 2  
    dataset.loc\[ dataset\['Fare'\] > 31, 'Fare'\] = 3  
    dataset\['Fare'\] = dataset\['Fare'\].astype(int)  
  
train\_df = train\_df.drop(\['FareBand'\], axis=1)  
combine = \[train\_df, test\_df\]  
      
train\_df.head(10)

![](images/00048.jpeg)

That’s the test set. Let’s also take a peek at the test dataset:

test\_df.head(10)

![](images/00049.jpeg)

Whew! Finally we’re done with the rigorous part of data analysis and machine learning. Note that we haven’t done any machine learning yet. Also note that in almost every step we took a peek at the dataset and see how the values transformed. This is for sanity check and ensuring we’re doing the right thing.

Now for the most awaited part. We’re now ready to train a model/s. Always keep in mind that our goal here is to learn from the data and then make predictions on unseen data based on that previous learning. But first there are dozens of predictive algorithms to choose from. Let’s try the following 6 algorithms because they’re popular in Classification tasks (we’ll discuss them again later in detail):

1.  Logistic Regression
2.  K-nearest neighbors or KNN
3.  Support Vector Machine (SVM)
4.  Naive Bayes Classifier
5.  Decision Tree
6.  Random Forest

First, we define the independent variables (X\_train) and the target (Y\_train) in our training set (we similarly do this in the test set):

X\_train = train\_df.drop("Survived", axis=1)  
Y\_train = train\_df\["Survived"\]  
X\_test  = test\_df.drop("PassengerId", axis=1).copy()  
X\_train.shape, Y\_train.shape, X\_test.shape

((891, 8), (891,), (418, 8))

Let’s then train our model using the first option (Logistic Regression):

from sklearn.linear\_model import LogisticRegression

logreg = LogisticRegression()  
logreg.fit(X\_train, Y\_train)  
Y\_pred = logreg.predict(X\_test)  
acc\_log = round(logreg.score(X\_train, Y\_train) \* 100, 2)  
acc\_log

80.36

80.36% is the accuracy of the Logistic Regression when predicting whether a passenger survived or not. Let’s try another model (Random Forest Classifier):

from sklearn.ensemble import RandomForestClassifier

random\_forest = RandomForestClassifier(n\_estimators=100)  
random\_forest.fit(X\_train, Y\_train)  
Y\_pred = random\_forest.predict(X\_test)  
random\_forest.score(X\_train, Y\_train)  
acc\_random\_forest = round(random\_forest.score(X\_train, Y\_train) \* 100, 2)  
acc\_random\_forest

86.76

This is the accuracy level if you use Random Forest. Notice that it’s significantly higher than what we obtained from Logistic Regression.

This is natural because different algorithms have different mechanisms and yield different accuracy levels. One good approach then is to choose the one with highest accuracy or use all the appropriate algorithms and average the results.

Implications & Possibilities

That’s how machine learning works roughly in real life. We get the data, perform data manipulation and transformation, finally apply a few lines of code (the actual machine learning part) and then we can make predictions.

The example earlier (Titanic Survival Prediction) is an excellent one because we already get an idea of the different aspects of a typical machine learning project. Well, notice that most of it is far from machine learning but more about making assumptions and manipulating the data.

It’s an excellent and yet as simple example. But the potential is enormous if we apply the concepts similarly to other problems. In fact, many real-world business and scientific challenges can be represented in a binary way (Survived or Not Survived).

Will a person purchase a certain product (Purchased or Not Purchased)? Is a tumor benign or malignant (0 for benign, 1 for malignant)? Is an email spam or not? Will a certain person pay her loan (based on other customers’ records and payment tendencies)? Based on 12 variables, should a person be brought to an intensive care unit?

It’s just the beginning and this is just one subset of Machine Learning. That’s why many experts say that we’ve barely just scratched the surface. And as we get increasing computational powers and massive datasets, we’ll then be able to dig deeper and apply machine learning to almost all fields.

The General Workflow

No matter the field or complexity of the subject, there are always few adhering principles common to all of them. It’s a similar case with machine learning wherein the general principles stay the same.

First, we have to get quality data with sufficient values. If it’s a messy set, we would spend extra time cleaning and tidying it up. The second step is to take a look at the data itself and visualize it. This allows us to quickly derive insights from the data. In fact, even if don’t use machine learning we’ll quickly get insights just through visualization and viewing the data summary (mean, median, mode, standard deviation, etc.).

Third step could involve a lot of data transformation and manipulation as we did earlier. We might need to discard a few irrelevant features. We could also combine features into one for simplicity. We could also create new features that model algorithms can work on.

And for the most awaited part, we now choose a model and algorithm and start learning from data. With scikit-learn, we already have pre-built code for us so we don’t have to write anything from scratch. It’s the reason why we only spent 1% of our time on the actual machine learning. But if we’re writing everything from scratch, it will take us a really long time.

You can always dig deeper on how the models and algorithms work. The behind-the-scenes are often complex because of the mathematics. But if you still choose to learn all that, you’ll get an edge over the rest.

Anyway, let’s focus on the fundamentals first. After all, “first principles” are always here to stay. Let’s begin.

  

General Machine Learning Concepts

In the previous chapter we discussed an example of how machine learning is applied on a real dataset. This is to quickly show and illustrate the power of machine learning.

But before going any deeper, let’s explore the fundamentals first. This way you’ll have a mental framework where pieces will fall together. This allows for a more solid learning and firm grounding on what machine learning truly is. Tools and techniques will always change. But with the right fundamentals you’ll always be able to adjust along the way.

So let’s start with the main “categories” of machine learning. The number is debatable but these are the most important things you’ll encounter most as you read other resources about machine learning and data science: Supervised Learning, Unsupervised Learning, and Deep Learning.

What is Machine Learning

Machine learning has recently been attracting attention in the media for several reasons, mainly because it has achieved impressive results in various cognitive tasks such as image classification, natural language understanding, customer churn prediction etc. However, it has been regarded as some sort of magic formula that is capable of predicting the future, but what really is machine learning. Machine learning at its simplest form is all about making computers learn from data by improving their performance at a specific task through experience. Similar to the way humans learn by trying out new things and learning from the experience, machine learning algorithms improve their capability by learning patterns from lots of examples. The performance of these algorithms, generally improves as they are exposed to more data (experience). Machine learning is therefore a branch of artificial intelligence that aims to make machines capable of performing specific tasks without being explicitly programmed. What this means is that these algorithms are not rule-based, the entire learning process is constructed in such a way as to minimize or completely eliminate human intervention.

 

Machine learning algorithms are typically used for a wide range of learning problems such as classification, regression, clustering, similarity detection etc. Many applications used in the real world today are powered by machine learning. Applications such as personal assistants on mobile phones use machine learning algorithms to understand voice commands spoken in natural language, mobile keyboards predict the next word a user is typing based on previous words, email clients offer a smart reply feature whereby the content of an email is scanned and appropriate responses are generated, e-commerce applications offer recommendation to users based on previous purchases and spending habits etc. Nearly every industry would be impacted by machine learning as most processes can be automated given that there is enough training data available. Machine learning algorithms mostly excel in tasks where there is a clear relationship between a set of inputs and outputs which can be modelled by training data. Although machine learning is a rapidly improving field, there is as of now no notion of general intelligence of the form displayed by humans. This is because models trained on one task cannot generalize the knowledge gleaned to perform another task, that is machine learning algorithms learn narrow verticals of tasks.

 

There are three main branches of machine learning namely - supervised learning, unsupervised learning and reinforcement learning. In some cases a fourth branch is mentioned - semi-supervised learning but this is really just a special instance of supervised learning as we would see in the explanations below.

 

Supervised Learning

It’s about learning from labelled data (e.g. Survived or Not Survived) and then applying that learning into “unseen” data. As you might have realized already, Titanic Survival Prediction falls into this category.

In particular, that example falls in Classification. In other words, this Supervised Learning task focused on “classifying.” Another subcategory aside from Classification is Regression. In Regression, the goal is to predict a value based on the relationship among variables (e.g. What is the cost of a house given how large it is in terms of square meter?). Regression is still about learning from “labelled” data because the model learns from A corresponds to B, C corresponds to D, and so on (this is just an illustration). It’s still learning from previous data and applying that learning to predict a value.

Anyway, if you pursue a machine learning career or build a startup with a heavy focus on this exciting field, you might do a lot of Supervised Learning. Keep in mind that it’s about prediction, whether predicting which category should an item belong to (Classification) or predicting a numerical value based on the relationship between the variables and the target (Regression).

 

Unsupervised Learning

In contrast, Unsupervised Learning is about learning from unstructured data (no labels). We can think of it as allowing the model to freely learn from and work on the data (no supervision or training as opposed to Supervised Learning wherein there are training sets and test sets).

Often the goal in Unsupervised Learning is to find hidden patterns and reveal the organic clusters that formed among the data points. This is the essence of Clustering (we’ll also discuss this in a separate chapter) where the goal is to reveal the natural aggregation of data points. This is very useful in data visualization and discovering the intrinsic structures in the data set. 

 

Semi-supervised Learning Algorithms

Semi-supervised learning algorithms are a special case of supervised learning algorithms. In semi-supervised learning, while there isn’t an explicit label, there exist an implicit heuristic which serves as a supervisor in the training loop. Semi-supervised models do not contain any external source of labels but only rely on input features. However, the learning task is set up in such a way that supervision still takes place in the form of extraction of pseudo-labels from inputs through a heuristic algorithm. A popular example of semi-supervised learning algorithms are autoencoders. Let us look at an example to expand our understanding.

 

![](images/00050.jpeg)

 

 

In the autoencoder above, the learning task is to reduce the dimensions of the input into a smaller latent space representing the most important hidden features, then reconstruct the input from this lower dimensional space. So given an input, example an image, an autoencoder shrinks the image into a smaller latent representation that still contains most of the information about the image, then reconstructs the original input image from this low dimensional space. Even if there are no explicit labels, it would be observed that the input serves as the supervisor since the learning task is to reconstruct the input. Once such a model is trained to compress features into a smaller dimension, the compressed features can serve as the starting point of a supervised learning algorithm similar to dimensionality reduction using PCA. The first part of the network that reduces the dimensions of the input is called an encoder while the second part that scales the encoded features back to the full size input is called the decoder.

Reinforcement Learning Algorithms

In reinforcement learning there are three main components, an agent, an environment and actions. The goal of reinforcement learning is to train an intelligent agent that is capable of navigating its environment and performing actions that maximizes its chances of arriving at some end goal. Actions carried out by the agent change the state of the environment and rewards or punishment may be issued based on the actions taken by the agent. The challenge is for the agent to maximize the accumulated rewards at the end of a specific period so that it can actualize an end goal (objective).

 

![](images/00051.jpeg)

 

In the schematic diagram of reinforcement learning above, an agent (the reinforcement learning) interacts with the world (environment) through actions. The environment provides observations and rewards to the agent based on the kind of action taken by the agent. The agent uses this feedback to improve its decision making process by learning to carry out actions associated with positive outcomes.

 

Deep Learning

Actually, Deep Learning can cover both Supervised Learning and Unsupervised Learning. That’s because with Deep Learning you can do Regression, Classification, and Clustering.

What’s the difference then? Deep Learning really shines if you’re analyzing massive datasets especially those that contain text, image, audio, and even video data. Remember that in Titanic Survival Prediction we mostly worked on numerical values. But when the data we’re dealing with is composed of text, we will take a different approach.

It’s possible to use traditional machine learning techniques for massive and complex datasets. But for large scale analysis and projects, Deep Learning is still the most popular approach whether in academics or business.

Deep Learning is inspired by how our brains work. That’s why in Deep Learning you’ll encounter the term “neural networks.” We still don’t have a complete understanding of how the brain really works. But based on the prevailing model, it could be very helpful in machine learning. In a later chapter we’ll go deeper into this.

Anyway, no matter which you choose (either traditional machine learning or deep learning), you still have to go through most of the processes discussed in Titanic Survival Prediction. Most of your time might actually be spent on data manipulation and transformation instead of the actual exciting machine learning aspect. Often you might need to examine the features (discard or create new ones) and look at the data. Often you’ll also have to visualize the data points for quick insights and detection of outliers.

In other words, machine learning (no matter what model or approach you choose) could be more about the processes outside of it (data visualization, manipulation, transformation, domain knowledge). That’s why it’s always good to focus on the fundamentals. Soon, new tools will sprout that will make machine learning quick and intuitive (e.g. drag and drop or just giving a voice command). But most of the hard work would still be about preparing the data and acquiring the required domain knowledge so we can effectively take advantage of the power of machine learning.

In the succeeding chapters let’s explore more of those essential fundamentals. We’ll also explore more examples of how machine learning is applied in different projects and domains.

Overfitting and Underfitting

Overfitting and underfitting jointly form the central problem of machine learning. When training a model we want to improve its optimization by attaining better performance on the training set. However, once the model is trained, what we care about is generalization. Generalization in a nutshell deals with how well a trained machine learning model would perform on new data which it has not seen, that is data it was not trained on. In other words, how well can a model generalize the patterns it learnt on the training set to suit real world examples, so that it can achieve similar or better performance. This is the crux of learning. A model should be able to actually learn useful representations from data that improves test time performance and not merely memorize features as memorization is not learning.

 

We say a model has overfit to a training set when it has failed to learn only useful representations in the data but has also adjusted itself to learn noise in order to get an artificially high training set accuracy. Underfitting means that the model has not used the information available to it but has only learnt a small subset of representations and has thrown away majority of useful information, thereby making it to make unfounded assumptions. The ideal situation is to find a model that neither underfitts nor overfitts but exhibits the right balance between optimization and generalization. This can be done by maintaining a third set of examples known as the validation set. The validation set is used to tune (improve) the performance of the model without overfitting the model to the training set. Other techniques for tackling overfitting includes applying regularization which punishes more complicated models and acquiring more training examples. Underfitting can be stymied by increasing the capacity of the learning algorithm so that it can take advantage of available features.

 

![](images/00052.jpeg)

 

 

The plots above show three simple line based classification models. The first plot separates classes by using a straight line. However, a straight line is an overly simplistic representation for the data distribution and as a result it misclassified many examples. The straight line model is clearly underfitting as it has failed to use majority of the information available to it to discover the inherent data distribution.

 

The second plot shows an optimal case where the optimization objective has been balanced by generalization criterion. Even though the model misclassified some points in the training set, it was still able to capture a valid decision boundary between both classes. Such a classifier is likely to generalize well to examples which it was not trained on as it has learnt the discriminative features that drive prediction. The last plot illustrates a case of overfitting. The decision boundary is convoluted because the classifier is responding to noise by trying to correctly classify every data point in the training set. The accuracy of this classifier would be perfect on the training set but it would perform horribly on new examples because it optimized its performance only for the training set. The trick is to always choose the simplest model that achieves the greatest performance.

Correctness

To evaluate a machine learning algorithm, we always specific measures of predictive performance. These metrics allow us to judge the performance of a model in an unbiased fashion. It should be noted that the evaluation metric chosen depends on the type of learning problem. Accuracy is a popular evaluation metric but it is not suitable for all learning problems. Other measures for evaluation include recall, precision, sensitivity, specificity, true positive rate, false positive rate etc. The evaluation used should be in line with the goals of the modelling problem.

 

To ensure fidelity of reported metrics, a rule of thumb is that models should never be trained on the entire dataset as any evaluation reported by metrics is likely skewed because the model’s performance when exposed to new data is unascertained. The dataset should be divided into train, validation and test splits. The model is trained on the training set, the validation set is reserved for hyperparameter tuning for best performing models and the test set is only used once at the conclusion of all experimentation.

 

A confusion matrix is widely used as a simple visualization technique to access the performance of classifiers in a supervised learning task. It is a table where the rows represent the instances in the actual class (ground truth) while the columns represents predictions. The order may be reversed in some cases. It is called a confusion matrix because it makes it easy to see which classes the model is misclassifying for another, that is which classes confuse the model.

 

![](images/00053.jpeg)

The examples which the model correctly classified are on the diagonal from the top left to bottom right. False negatives are positive classes which the classified wrongly predicted as negatives while false positives are negative instances which the classifier wrongly thought were positives. Several metrics like true positive rate, false positive rate, precision etc are derived from items in the confusion matrix.

The Bias-Variance Trade-off

The bias of a model is defined as the assumptions made by the model to simplify the learning task. A model with high bias makes assumptions which are not correlated by the data. This lead to errors because predictions are usually some way off from actuals. Variance on the other hand is how susceptible a model is to noise in the training data. How widely does the performance on the model vary based on the data it is evaluated on. A good machine learning algorithm should strive to achieve low bias and low variance. Bias and variance are related to overfitting and underfitting earlier encountered. A model with high bias is underfitting the training data because it has made simplistic assumptions instead of learning from information available. Similarly, a model with high variance is overfitting, because it has modelled noise and as a result, its performance would vary widely across the training set, validation set and test set.

 

Let us look use a dart analogy to further explain these concepts.

 

![](images/00054.jpeg)

The top left image represents a model that has low bias and low variance. This is the ideal model as it has learnt to hit the target (produce correct classification) and usually hits the target most of the time (does not vary with each throw). The image at the top right shows a model that exhibits high variance and low bias. Even if it does not make a lot of assumptions, its predictions are spread all over the board which means its performance varies widely (high variance). The image on the bottom left depicts a model with high bias and low variance. The shots are not all over the board but in a specific location. This location is however far from the target meaning the model is biased because of simplistic assumptions. Finally, the image on the bottom right shows a model with high bias and high variance. The shots on the board vary widely and are far away from the target. This is the worst kind of model as it hasn’t learnt any useful representation.

Feature Extraction and Selection

Feature extraction involves performing transformation on input features that produce other features that are more analyzable and informative. Feature extraction may occur by combining original features to create new features which are better suited for the modelling problem. This is similar to feature engineering where we create new features to fed into a model. An example of feature extraction is Principal Component Analysis (PCA).

 

Feature selection is choosing a subset of features from the original input features. The features selected are those that show the most correlation with the target variable, that is those features that drive the predictive capability of the model. Both feature extraction and feature selection leads to dimensionality reduction. The main difference between them is that feature extraction is a transformation that creates new features whereas feature selection chooses only a subset of available features. Since feature selection removes certain features, it is always advisable to first do feature extraction on a dataset, then select the most important predictors via feature selection.

Why Machine Learning is Popular

The popularity of machine learning in the artificial intelligence community and society in general is mainly because machine learning techniques have proven to be highly successful in various niches providing business value for a slew of operations from fraud detection to speech recognition to recommender systems. It is embedded in products we use every day. When you buy a product from Amazon and you are given a list of suggestions of other products that go with it, that’s machine learning in action. When you open your mailbox and emails are automatically classified into folders based on their similarity, those are machine learning models doing the work behind the scenes. Even when you use your credit card online and your transaction is successful, a machine learning model approved your transaction as being normal and not fraudulent.

 

In light of all these, companies and organizations have poured in more money into developing better performing models through research and collaboration between industry and academia.

 

It wasn’t always the case that machine learning was the darling of the computer science community, however in recent years three factors have conspired to give it an exalted place.

●    With the dawn of the internet, more data was being collected and this lead to the age of big data.

●    Computational resources became faster and cheaper with the arrival of Graphics Processing Units (GPUs), which were originally developed by the gaming industry to render graphics but are well suited for parallel computation.

●    Better algorithms were developed which lead to better accuracy of models.

  

 

Regression

It’s time to review some of your high school algebra. Because the truth is this subcategory of Supervised Learning doesn’t look like machine learning at all.

y = mx + b

That’s the equation of the straight line. This simply means that if you know the value of x, you’ll also know the value of y (m and b are constants). Once we’ve determined these constants and we have a value of x, we’ll also predict the value of y.

It’s similar here in Regression in the context of machine learning. For instance, we might predict housing prices based on the given number of rooms or how large each house is (how many square meters). This is a form of Supervised Learning because first we have the number of rooms or the number of square meters (the independent variables) and the corresponding housing price (the target).

Simple and Multiple Linear Regression

Regression can come in many forms. In the example above, there are only two sets of quantitative values. First is the number of rooms or square meters. The second (which is the target) is the corresponding housing price. We can plot those data points and perhaps fit a straight line that best approximates the relationship between the two.

Of course, the straight line won’t touch all the points. It’s just an approximation of how the two sets of values are related. Here’s an illustration:

![](images/00055.jpeg)

Intuitively, we can see that the line attempts to minimise its distance between all the points. But well, no one can please everybody so instead the straight line is actually the result of minimizing the sum of squared errors (least squares solution) between a line and all the points.

 

In multiple linear regression, there are two or more independent variables, that is the number of predictors which determine the outcome y, are more than one. The relationship is still linear but y is dependent on more variables.

 

![](images/00056.jpeg)

 

Let us now look at a practical example. We would use the regression techniques explained above to predict the price of a house in a neighborhood given information about the house in the form of features. The dataset we would use is the Boston house pricing dataset and it contains 506 observations. The dataset can be downloaded from this URL ([https://forge.scilab.org/index.php/p/rdataset/source/file/master/csv/MASS/Boston.csv](https://forge.scilab.org/index.php/p/rdataset/source/file/master/csv/MASS/Boston.csv)).

First we import relevant libraries and load the dataset using Pandas.

 

import numpy as np

import pandas as pd

import matplotlib.pyplot as plt

\# matplotlib magic command for Jupyter notebook

%matplotlib inline

 

dataset = pd.read\_csv('Boston.csv')

dataset.head()

 

![](images/00057.jpeg)

 

The dataset has 13 predictors such as the number of rooms in the house, age of house, pupil-teacher ratio in the town etc.

 

Let us plot the relationship between one of the predictors and the price of a house to see whether we can come up with any explanation from the visualization. The predictor we would use is the per capita crime rate by town which captures the rate of crime in the neighborhood.

 

plt.scatter(dataset\['crim'\], dataset\['medv'\])

plt.xlabel('Per capita crime rate by town')

plt.ylabel('Price')

plt.title("Prices vs Crime rate")

 

![](images/00058.jpeg)

 

We can see that for towns with very low crime rates (at the beginning of the plot), there are houses for the full range of prices, both cheap and expensive. This is denoted by the vertical spread of points across the y axis. If we exclude the first 10 units on the x-axis, we notice that there is a negative correlation between price and the crime rate. This is hardly surprising as we would expect the price of houses to drop as the crime rate in the neighborhood increases.

 

Next we split our dataset into predictors and targets. Then we create a training and test set.

 

X = dataset.drop(\['Unnamed: 0', 'medv'\], axis=1)

y = dataset\['medv'\]

 

from sklearn.model\_selection import train\_test\_split

x\_train, x\_test, y\_train, y\_test = train\_test\_split(X, y, test\_size=0.3)

 

The next step involves importing the linear regression classifier from Scikit-Learn, initializing it and fitting the classifier on data.

 

\# import linear regression classifier, initialize and fit the model

from sklearn.linear\_model import LinearRegression

 

regressor = LinearRegression()

regressor.fit(x\_train,y\_train)

 

Having fit the classifier, we can use it to predict house prices using features in the test set.

 

y\_pred = regressor.predict(x\_test)

 

The next step is to evaluate the classifier using metrics such as the mean square error and the coefficient of determination  R square.

 

from sklearn.metrics import mean\_squared\_error, r2\_score

 

\# The coefficients

print('Coefficients: \\n', regressor.coef\_)

\# The mean squared error

print('Mean squared error: {:.2f}'.format(mean\_squared\_error(y\_test, y\_pred)))

\# Explained variance score: 1 is perfect prediction

print('Variance score: {:.2f}'.format(r2\_score(y\_test, y\_pred)))

 

![](images/00059.jpeg)

 

The coefficients are the learnt parameters for each predictor, the mean square error represents how far off our predictions are from the actual values and variance score is the coefficient of determination which gives the overall performance of the model. A variance score of 1 is a perfect model, so it is clear that with a score of 0.72, the model has learnt from the data.

 

Finally, we can plot the predicted prices from the model against the ground truth (actual prices).

 

plt.scatter(y\_test, y\_pred)

plt.xlabel("Prices: $Y\_i$")

plt.ylabel("Predicted prices: $\\hat{Y}\_i$")

plt.title("Prices vs Predicted prices: $Y\_i$ vs $\\hat{Y}\_i$")

 

![](images/00060.jpeg)

 

The scatter plot above shows a positive relationship between the predicted prices and actual prices. This indicates that our model has successfully captured the underlying relationship and can map from input features to output prices.

 

Here is the code in its entirety.

 

\# import libraries

import numpy as np

import pandas as pd

import matplotlib.pyplot as plt

%matplotlib inline

 

\# load dataset

dataset = pd.read\_csv('Boston.csv')

dataset.head()

 

\# plot crime vs price

plt.scatter(dataset\['crim'\], dataset\['medv'\])

plt.xlabel('Per capita crime rate by town')

plt.ylabel('Price')

plt.title("Prices vs Crime rate")

 

\# separate predictors and targets

X = dataset.drop(\['Unnamed: 0', 'medv'\], axis=1)

y = dataset\['medv'\]

 

from sklearn.model\_selection import train\_test\_split

x\_train, x\_test, y\_train, y\_test = train\_test\_split(X, y, test\_size=0.3)

 

\# import linear regression classifier, initialize and fit the model

from sklearn.linear\_model import LinearRegression

 

regressor = LinearRegression()

regressor.fit(x\_train,y\_train)

 

y\_pred = regressor.predict(x\_test)

 

from sklearn.metrics import mean\_squared\_error, r2\_score

 

\# The coefficients

print('Coefficients: \\n', regressor.coef\_)

\# The mean squared error

print('Mean squared error: {:.2f}'.format(mean\_squared\_error(y\_test, y\_pred)))

\# Explained variance score: 1 is perfect prediction

print('Variance score: {:.2f}'.format(r2\_score(y\_test, y\_pred)))

 

\# plot predicted prices vs actual prices

plt.scatter(y\_test, y\_pred)

plt.xlabel("Prices: $Y\_i$")

plt.ylabel("Predicted prices: $\\hat{Y}\_i$")

plt.title("Prices vs Predicted prices: $Y\_i$ vs $\\hat{Y}\_i$")

Logistic Regression

Logistic regression despite its name is a classification algorithm. Logistic regression is used when the dependent variable is binary in nature, that is when it can be either one of two values (categories) example true or false. It is a linear combination of weighted input features applied to the sigmoid function. The logit or sigmoid function is at the heart of logistic regression and models data along the range of 0 to 1. 

 

![](images/00061.jpeg)

 

In the image above, z represents the weighted input features. What this means is that z is a linear addition of input features and the importance of input features (how large they are), is influenced by their weights (coefficients). A threshold is usually set to separate samples into classes. The threshold can be seen as the decision boundary. After the linear computation and the application of the sigmoid or logit function, the resultant value is compared to the threshold value. If it is equal to or larger than the threshold value, then the sample under consideration belongs to the positive class else it belongs to the negative class. The threshold value is usually set to 0.5.

 

Outputs from logistic regression can be interpreted as probabilities that show how likely a data point belongs to a category. The formula for the logistic function is shown below.

 

![](images/00062.gif)

 

The main difference between logistic regression and simple regression is that logistic regression is used for classification when there can only be two classes (negative or positive) while simple regression is used to predict an actual value like a continuous number and not classes or categories.

 

We would now apply logistic regression to a binary classification problem. The dataset we would leverage is the Pima Indian Diabetes Database which is a dataset from the National Institute of Diabetes and Digestive and Kidney Diseases. The dataset contains a target variable that is used to indicate whether a patient developed diabetes or not. Our task is therefore to use diagnostic measurements as predictors to determine the diabetes status of a patient.

 

The dataset can be downloaded at: [https://www.kaggle.com/uciml/pima-indians-diabetes-database/data](https://www.kaggle.com/uciml/pima-indians-diabetes-database/data)

 

Let us import relevant libraries and load the dataset to have a sense of what it contains.

 

import numpy as np

import pandas as pd

import matplotlib.pyplot as plt

 

dataset = pd.read\_csv('diabetes.csv')

dataset.head(5)

 

![](images/00063.jpeg)

The dataset has 8 predictors such as  glucose level of patient, age, skin thickness, body mass index, insulin level, age etc. These form the features for our model or in regression speak, the independent variables.

 

Next we separate the columns in the dataset into features and labels. The labels or class are represented by the “Outcome” column.

 

features = dataset.drop(\['Outcome'\], axis=1)

labels = dataset\['Outcome'\]

 

from sklearn.model\_selection import train\_test\_split

features\_train, features\_test, labels\_train, labels\_test = train\_test\_split(features, labels, test\_size=0.25)

 

The next step is to initialize a logistic regression model and fit it to the Pima Indians diabetes data.

 

\# Training the model

from sklearn.linear\_model import LogisticRegression

classifier = LogisticRegression()

 

classifier.fit(features\_train, labels\_train)

 

The trained model can now be evaluated on the test set.

 

pred = classifier.predict(features\_test)

 

from sklearn.metrics import accuracy\_score

accuracy = accuracy\_score(labels\_test, pred)

print('Accuracy: {:.2f}'.format(accuracy))

 

![](images/00064.jpeg)

 

The trained logistic regression model attains an accuracy of 72% on the test set.

Generalized Linear Models

Generalized linear models are an extension of linear models where the dependent variable does not belong to a normal or Gaussian distribution. Generalized linear models are capable of modelling more complicated relationships between the independent and dependent variables. GLMs can often model various probability distributions as such poisson, binomial, multinomial distributions etc. Logistic regression is an example of a generalized linear model where the dependent variable is modelled using a binomial distribution. This enables it to create a mapping from inputs to outputs, where the outputs are binary in nature.

 

Poisson regression is a generalized linear model that is used for modelling count data. Count data are integer values that can only be positive. Poisson regression assumes that the independent variable y, belongs to a Poisson distribution, which is a type of exponential probability distribution. The main difference between Poisson regression and linear regression is that linear regression assumes the outputs are drawn from a normal distribution whereas Poisson distribution assumes y comes from a Poisson distribution. The outputs in Poisson regression are modelled as shown below.

![](images/00065.gif)

 

Generalized linear models are made up of three components, the random components which are the probability distribution of the output, the systematic component which describes the explanatory variables (X) or predictors and the link function, which specifies the relationship between explanatory variables and the random component.

Since the hyperparameters (weights) of Poisson regression cannot take negative values, they are transformed using natural logarithm to ensure they are always positive. The mean of Poisson distribution is stated mathematically as:

 

![](images/00066.gif)

 

The objective function or loss function that is used to train the model in order to discover learnable parameters is shown below:

 

![](images/00067.gif)

For our hands on example, we would use the statsmodels package that provides various functions and classes for statistical modelling, statistical data exploration etc. We would use a bundled dataset from statsmodels, the Scottish vote dataset that contains records from the 1997 vote to give the Scottish parliament the rights to collect taxes. The dataset contains 8 explanatory variables (predictors) and 32 observations, one for each district.

 

First we import the Statsmodels package as shown below.

 

import statsmodels.api as sm

 

Next we load the dataset and extract the explanatory variable (X).

 

data = sm.datasets.scotland.load()

\# data.exog is the independent variable X

data.exog = sm.add\_constant(data.exog)

 

Similar to Scikit-Learn, we import the appropriate model and instantiate an object from it. In this case we specify a generalized linear model and set the distribution family to Poisson.

 

\# Instantiate a poisson family model with the default link function.

poisson\_model = sm.GLM(data.endog, data.exog, family=sm.families.Poisson())

 

We then fit the model on the data.

 

poisson\_results = poisson\_model.fit()

 

We can now print a summary of results to better understand the trained model.

 

print(poisson\_results.summary())

 

![](images/00068.jpeg)

 

The summary contains values like the coefficients or weights for independent variables, standard error and z scores.

 

A Regression Example: Predicting Boston Housing Prices

To get a good understanding of the concepts discussed so far, we would introduce a running example in which we are faced with a regression problem, predict the price of houses in the Boston suburbs given information about such houses in the form of features.

The dataset we would use can be found at: [https://forge.scilab.org/index.php/p/rdataset/source/file/master/csv/MASS/Boston.csv](https://forge.scilab.org/index.php/p/rdataset/source/file/master/csv/MASS/Boston.csv)

Steps To Carry Out Analysis

To carry out analysis and build a model we first need to identify the problem, perform exploratory data analysis to get a better sense of what is contained in our data, choose a machine learning algorithm, train the model and finally evaluate its performance. The following steps would be carried out in a hands on manner below, so the reader is encouraged to follow along.

 

Import Libraries:

import numpy as np

import pandas as pd

import matplotlib.pyplot as plt

 

Numpy is a popular Python numerical computing library which supports vectorized implementation of calculations and significantly speeds up computation time. Pandas is a library used to manipulate data in data frames while Matplotlib is used for plotting graphs and data visualizations.

Let’s load the data by using the read\_csv method on the Pandas library and passing it the location of our data.

 

dataset = pd.read\_csv('Boston.csv')

 

The next step is to look at what our data contains

 

dataset.head(5)

 

![](images/00069.jpeg)

This shows individual observations as rows. A row represents a single data point while columns represent features. There are 13 features because the last column medv is the regression value that we are to predict (median value of owner-occupied homes in $1000s) and Unmamed:0 column is a sort of identifier and is  not informative. Each feature represents a subset of information example crim means per capita crime rate by town while rm average number of rooms per dwelling.

Next we run

 

dataset.shape

 

This gives the shape of dataset which contains 506 observations. We first need to separate our columns into our independent and dependent variables

 

X = dataset.drop(\['Unnamed: 0', 'medv'\], axis=1)

y = dataset\['medv'\]

 

We would need to split our dataset into train and test splits as we want to train our model on the train split, then evaluate its performance on the test split.

 

from sklearn.model\_selection import train\_test\_split

x\_train, x\_test, y\_train, y\_test = train\_test\_split(X, y, test\_size=0.3)

 

x\_train, x\_test contains our features while y\_train, y\_test are the prediction targets for the train split and test splits respectively. test\_size=0.3 means we want 70% of data to be used for training and 30% for the testing phase.

The next step is to import a linear regression model from the Scikit-Learn library. Scikit-Learn is the defacto machine learning library in Python and contains out of the box many machine learning models and utilities.

Linear regression uses equation of a straight line to fit our parameters.

 

\# importing the model

from sklearn.linear\_model import LinearRegression

regressor = LinearRegression()

 

The above code imports the linear regression model and instantiates an object from it.

 

regressor.fit(x\_train,y\_train)

 

This line of code fits the data using the fit method. What that means is that it finds appropriate values for the independent parameters that explains the data.

How to forecast and Predict

To evaluate our model, we use the test set to know whether our model can generalize well to data it wasn’t trained on.

 

y\_pred = regressor.predict(x\_test,y\_test)

from  sklearn.metrics import mean\_squared\_error

mse = mean\_squared\_error(y\_test, y\_pred)

 

The predict method called on the regressor object returns predictions which we use to evaluate the error of our model. We use mean squared error as our metric. Mean Squared Error (MSE) measures how far off our predictions are from the real (actual) values. The model obtains an MSE of 20.584.

Finally, we plot a graph of our output to get an idea of the distribution.

 

plt.scatter(y\_test, y\_pred)

plt.xlabel("Prices: $Y\_i$")

plt.ylabel("Predicted prices: $\\hat{Y}\_i$")

plt.title("Prices vs Predicted prices: $Y\_i$ vs $\\hat{Y}\_i$")

 

![](images/00070.jpeg)

 

We can see from the scatter plot above that predictions from our model are close to the actual house prices hence the concentration of points.

 

 

# K-Nearest Neighbors

Introduction to K Nearest Neighbors

To understand the k-nearest neighbor algorithm, we first need to understand nearest neighbor. Nearest neighbor algorithm is an algorithm that can be used for regression and classification tasks but is usually used for classification because it is simple and intuitive.

At training time, the nearest neighbor algorithm simply memorizes all values of data for inputs and outputs. During test time when a data point is supplied and a class label is desired, it searches through its memory for any data point that has features which are most similar to the test data point, then it returns the label of the related data point as its prediction. A Nearest neighbor classifier has very quick training time as it is just storing all samples. At test time however, its speed is slower because it needs to search through all stored examples for the closest match. The time spent to receive a classification prediction increases as the dataset increases.

The k-nearest neighbor algorithm is a modification of the nearest neighbor algorithm in which a class label for an input is voted on by the k closest examples to it. That is the predicted label would be the label with the majority vote from the delegates close to it. So a k value of 5 means, get the five most similar examples to an input that is to be classified and choose the class label based on the majority class label of the five examples.

Let us now look at an example image to hone our knowledge:

 

![](images/00071.jpeg)

The new example to be classified is placed in the vector space, when k = 1, the label of the closest example to it is chosen as its label. In this case, the new example is categorized as belonging to class 1. When k = 1, k-nearest neighbor algorithm is reduced to nearest neighbor algorithm.

From the image, when k = 3, we choose the 3 closest examples to the new example using a similarity metric known as the distance measure. We see that two close examples predict the class as being class 2 (red triangle) while the remaining example predicts the class to be class 1 (blue square). The predicted class of the new data point is therefore class 2 because it has the majority vote.

The distance metric used to measure proximity of examples may be L1 or L2 distance. L1 distance is the sum of the absolute of the difference between two points and is given by:

 

![<math xmlns="http://www.w3.org/1998/Math/MathML"><msub><mi>d</mi><mn>1</mn></msub><mfenced><mrow><mi>P</mi><mo>,</mo><mi>q</mi></mrow></mfenced><mo>=</mo><munderover><mo>&#x2211;</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><mn>1</mn><msub><mi>P</mi><mi>i</mi></msub><mo>-</mo><msub><mi>q</mi><mi>i</mi></msub><mn>1</mn></math>](images/00072.jpeg)

L1 distance is sometimes referred to as the Manhattan distance.

L2 is an alternative distance measure that may be used. It is the Euclidean distance between two points using a straight line. It is given as:

![<math xmlns="http://www.w3.org/1998/Math/MathML"><msub><mi>d</mi><mn>2</mn></msub><mfenced><mrow><mi>p</mi><mo>,</mo><mi>q</mi></mrow></mfenced><mo>=</mo><msqrt><munderover><mo>&#x2211;</mo><mrow><mi>i</mi><mo>=</mo><mn>1</mn></mrow><mi>n</mi></munderover><msup><mfenced><mrow><msub><mi>q</mi><mi>i</mi></msub><mo>-</mo><msub><mi>P</mi><mi>i</mi></msub></mrow></mfenced><mn>2</mn></msup></msqrt></math>](images/00073.jpeg)

A value of k = 1 would classify all training examples correctly since the most similar example to a point would be itself. This would be a sub-optimal approach as the classifier would fail to learn anything and would have no power to generalize to data that it was not trained on. A better solution is to choose a value of k in a way that it performs well on the validation set. The validation set is normally used to tune the hyperparameter k. Higher values of k has a smoothing effect on the decision boundaries because outlier classes are swallowed up by the voting pattern of the majority. Increasing the value of k usually leads to greater accuracy initially before the value becomes too large and we reach the point of diminishing returns where accuracy drops and validation error starts rising.

 

![](images/00074.gif)

 

The optimal value for k is the point where the validation error is lowest.

How to create and test the K Nearest Neighbor classifier

We would now apply what we have learnt so far to a binary classification problem. The dataset we would use is the Pima Indian Diabetes Database which is a dataset from the National Institute of Diabetes and Digestive and Kidney Diseases. The main purpose of this dataset is to predict whether a patient has diabetes or not based on diagnostic measurements carried out on patients. The patients in this study were female, of Pima Indian origin and at least 21 years old.

The dataset can be found at:

[https://www.kaggle.com/uciml/pima-indians-diabetes-database/data](https://www.kaggle.com/uciml/pima-indians-diabetes-database/data)

Since we are dealing with two mutually exclusive classes, a patient either has diabetes or not, this can be modelled as a binary classification task and for the purpose of our example we would use the k-nearest neighbor classifier for classification.

The first step is to import the libraries that we would use.

 

import numpy as np

import pandas as pd

import matplotlib.pyplot as plt

 

Next we load the data using Pandas.

 

dataset = pd.read\_csv('diabetes.csv')

 

As always what we should do is get a feel of our dataset and the features that are available.

 

dataset.head(5)

 

![](images/00075.jpeg)

We see that we have 8 features and 9 columns with Outcome  being the binary label that we want to predict.

 

To know the number of observations in the dataset we run

 

dataset.shape

 

This shows dataset contains 768 observations. 

 

Let’s now get a summary of the data so that we can have an idea of the distribution of attributes.

 

dataset.describe()

 

![](images/00076.jpeg)

The count row shows a constant value of 768.0 across features, it would be remembered that this is the same number of rows in our dataset. It signifies that we do not have any missing values for any features. The quantities mean, std gives the mean and standard deviation respectively across attributes in our dataset. The mean is the average value of that feature while the standard deviation measures the variation in the spread of values.

 

Before going ahead with classification, we check for correlation amongst our features so that we do not have any redundant features

corr = dataset.corr()    # data frame correlation function

fig, ax = plt.subplots(figsize=(13, 13))

ax.matshow(corr)   # color code the rectangles by correlation value

plt.xticks(range(len(corr.columns)), corr.columns)  # draw x tick marks

plt.yticks(range(len(corr.columns)), corr.columns)  # draw y tick marks

 

![](images/00077.jpeg)

The plot does not indicate any 1 to 1 correlation between features, so all features are informative and provide discriminability.

We need to separate our columns into features and labels

 

features = dataset.drop(\['Outcome'\], axis=1)

labels = dataset\['Outcome'\]

 

We would once again split our dataset into training set and test set as we want to train our model on the train split, then evaluate its performance on the test split.

 

from sklearn.model\_selection import train\_test\_split

features\_train, features\_test, labels\_train, labels\_test = train\_test\_split(features, labels, test\_size=0.25)

 

features\_train, features\_test contains the attributes while labels\_train, labels\_test are the discrete class labels for the train split and test splits respectively. We use a test\_size of 0.25 which indicates we want to use 75% of observations for training and reserve the remaining 25% for testing.

The next step is to use the k-nearest neighbor classifier from Scikit-Learn machine learning library.

 

\# importing the model

from sklearn.neighbors import KNeighborsClassifier

classifier = KNeighborsClassifier()

 

The above code imports the k-nearest neighbor classifier and instantiates an object from it.

 

classifier.fit(features\_train, labels\_train)

 

We fit the classifier using the features and labels from the training set. To get predictions from the trained model we use the predict method on the classifier, passing in features from the test set.

 

pred = classifier.predict(features\_test)

 

In order to access the performance of the model we use accuracy as a metric. Scikit-Learn contains a utility to enable us easily compute the accuracy of a trained model. To use it we import accuracy\_score from metrics module.

 

from sklearn.metrics import accuracy\_score

accuracy = accuracy\_score(labels\_test, pred)

print('Accuracy: {}'.format(accuracy))

 

We obtain an accuracy of 0.74, which means the predicted label was the same as the true label for 74% of examples.

 

Here is the code in full:

 

\# import libraries

import numpy as np

import pandas as pd

import matplotlib.pyplot as plt

 

\# read dataset from csv file

dataset = pd.read\_csv('diabetes.csv')

 

\# display first five observations

dataset.head(5)

 

\# get shape of dataset, number of observations, number of features

dataset.shape

 

\# get information on data distribution

dataset.describe()

 

\# plot correlation between features

corr = dataset.corr()    # data frame correlation function

fig, ax = plt.subplots(figsize=(13, 13))

ax.matshow(corr)   # color code the rectangles by correlation value

plt.xticks(range(len(corr.columns)), corr.columns)  # draw x tick marks

plt.yticks(range(len(corr.columns)), corr.columns)  # draw y tick marks

 

\# create features and labels

features = dataset.drop(\['Outcome'\], axis=1)

labels = dataset\['Outcome'\]

 

\# split dataset into training set and test set

from sklearn.model\_selection import train\_test\_split

features\_train, features\_test, labels\_train, labels\_test = train\_test\_split(features, labels, test\_size=0.25)

 

\# import nearest neighbor classifier

from sklearn.neighbors import KNeighborsClassifier

classifier = KNeighborsClassifier()

 

\# fit data

classifier.fit(features\_train, labels\_train)

 

\# get predicted class labels

pred = classifier.predict(features\_test)

 

\# get accuracy of model on test set

from sklearn.metrics import accuracy\_score

accuracy = accuracy\_score(labels\_test, pred)

print('Accuracy: {}'.format(accuracy))

 

Another Application

The dataset we would use for this task is the Iris flower classification dataset. The dataset contains 150 examples of 3 classes of species of Iris flowers namely Iris Setosa, Iris Versicolor and Iris Virginica. The dataset can be downloaded from Kaggle ([https://www.kaggle.com/saurabh00007/iriscsv/downloads/Iris.csv/1](https://www.kaggle.com/saurabh00007/iriscsv/downloads/Iris.csv/1)).

 

The first step of the data science process is to acquire data, which we have done. Next we need to handle the data or preprocess it into a suitable form before passing it off to a machine learning classifier.

 

To begin let’s import all relevant libraries.

 

import numpy as np

import pandas as pd

import matplotlib.pyplot as plt

import scipy as sp

 

Next we use Pandas to load the dataset which is contained in a CSV file and print out the first few rows so that we can have a sense of what is contained in the dataset.

 

dataset = pd.read\_csv('Iris.csv')

dataset.head(5)

 

![](images/00078.jpeg)

 

As we can see, there are 4 predictors namely sepal length, sepal width, petal length and petal width. Species is the target variable that we are interested in predicting. Since there are 3 classes what we have is a multi-classification problem.

 

In line with our observations, we separate the columns into features (X) and targets (y).

 

X = dataset.iloc\[:, 1:5\].values # select features ignoring non-informative column Id

y = dataset.iloc\[:, 5\].values # Species contains targets for our model

 

Our targets are currently stored as text. We need to transform them into categorical variables. To do this we leverage Scikit-Learn label encoder.

 

from sklearn.preprocessing import LabelEncoder

le = LabelEncoder()

y = le.fit\_transform(y) # transform species names into categorical values

 

Next we split our dataset into a training set and a test set so that we can evaluate the performance of our trained model appropriately.

 

from sklearn.model\_selection import train\_test\_split

X\_train, X\_test, y\_train, y\_test = train\_test\_split(X, y, test\_size = 0.3)

Calculating Similarity

In the last section, we successfully prepared our data and explained  the inner workings of the K-NN algorithm at a high level. We would now implement a working version in Python. The most important part of K-NN algorithm is the similarity metric which in this case is a distance measure. There are several distance metrics but we would use Euclidean distance which is the straight line distance between two points in a Euclidean plane. The plane may be 2-dimensional, 3-dimensional etc. Euclidean distance is sometimes referred to as L2 distance. It is given by the formula below.

 

![](images/00079.gif)

 

The L2 distance is computed from the test sample to every sample in the training set to determine how close they are. We can implement L2 distance in Python using Numpy as shown below.

 

def euclidean\_distance(training\_set, test\_instance):

    # number of samples inside training set

    n\_samples = training\_set.shape\[0\]

 

    # create array for distances

    distances = np.empty(n\_samples, dtype=np.float64)

 

    # euclidean distance calculation

    for i in range(n\_samples):

        distances\[i\] = np.sqrt(np.sum(np.square(test\_instance - training\_set\[i\])))

 

    return distances

Locating Neighbors

Having implemented the similarity metric, we can build out a full fledged class that is capable of identifying nearest neighbors and returning a classification. It should be noted that the K-Nearest Neighbor algorithm has no training phase. It simply stores all data points in memory. It only performs computation during test time when it is calculating distances and returning predictions. Here is an implementation of the K-NN algorithm that utilizes the distance function defined above.

 

class MyKNeighborsClassifier():

    """

    Vanilla implementation of KNN algorithm.

    """

 

    def \_\_init\_\_(self, n\_neighbors=5):

        self.n\_neighbors=n\_neighbors

 

    def fit(self, X, y):

        """

        Fit the model using X as array of features and y as array of labels.

        """

        n\_samples = X.shape\[0\]

        # number of neighbors can't be larger then number of samples

        if self.n\_neighbors > n\_samples:

            raise ValueError("Number of neighbors can't be larger then number of samples in training set.")

 

        # X and y need to have the same number of samples

        if X.shape\[0\] != y.shape\[0\]:

            raise ValueError("Number of samples in X and y need to be equal.")

 

        # finding and saving all possible class labels

        self.classes\_ = np.unique(y)

 

        self.X = X

        self.y = y

 

    def pred\_from\_neighbors(self, training\_set, labels, test\_instance, k):

        distances = euclidean\_distance(training\_set, test\_instance)

 

        # combining arrays as columns

        distances = sp.c\_\[distances, labels\]

        # sorting array by value of first column

        sorted\_distances = distances\[distances\[:,0\].argsort()\]

        # selecting labels associeted with k smallest distances

        targets = sorted\_distances\[0:k,1\]

 

        unique, counts = np.unique(targets, return\_counts=True)

        return(unique\[np.argmax(counts)\])

 

 

    def predict(self, X\_test):

 

        # number of predictions to make and number of features inside single sample

        n\_predictions, n\_features = X\_test.shape

 

        # allocationg space for array of predictions

        predictions = np.empty(n\_predictions, dtype=int)

 

        # loop over all observations

        for i in range(n\_predictions):

            # calculation of single prediction

            predictions\[i\] = self.pred\_from\_neighbors(self.X, self.y, X\_test\[i, :\], self.n\_neighbors)

 

        return(predictions)

The workflow of the class above is that during test time, a test sample (instance) is supplied and the Euclidean distance to every sample in the entire training set is calculated. Depending on the value of nearest neighbors to consider, the labels of those neighbors participate in a vote to determine the class of the test sample.

Generating Response

In order to generate a response or create a prediction, we first have to initialize our custom classifier. The value of k, cannot exceed the number of samples in our dataset. This is to be expected because we cannot compare with a greater number of neighbors than what we have available in the training set.

 

\# instantiate learning model (k = 3)

my\_classifier = MyKNeighborsClassifier(n\_neighbors=3)

 

Next we can train our model on the data. Remember in K-NN no training actually takes place.

 

\# fitting the model

my\_classifier.fit(X\_train, y\_train)

 

Evaluating Accuracy

To evaluate the accuracy of our model, we test its performance on examples which it has not seen such as those contained in the test set.

 

\# predicting the test set results

my\_y\_pred = my\_classifier.predict(X\_test)

 

We then check the predicted classes against the ground truth labels and use Scikit-Learn accuracy module to calculate the accuracy of our classifier.

 

from sklearn.metrics import confusion\_matrix, accuracy\_score

accuracy = accuracy\_score(y\_test, my\_y\_pred)\*100

print('Accuracy: ' + str(round(accuracy, 2)) + ' %.')

 

![](images/00080.jpeg)

 

Our model achieves an accuracy of 97.8% which is impressive for such a simple and elegant model.

The Curse of Dimensionality

The K-Nearest Neighbor algorithm performs optimally when the dimension of the input space is small as in this example. We had four predictors (sepal length, sepal width, petal length, petal width) going into the algorithm. K-NN struggles in high dimensional input spaces like those encountered in images. This is because the similarity measure as expressed by the distance metric is very limited and cannot properly model this high dimensional space. In general, machine learning algorithms try to reduce the number of dimensions so that intuitions we have about low dimensional spaces would still hold true. The accuracy or performance of algorithms usually suffer when the number of dimensions increase. This is known as the curse of dimensionality.

 

# Naive Bayes

Applications of Naive Bayes

Naive Bayes algorithm is an eager learning algorithm based on Bayes theorem with the assumption that all features are independent given the class label. Naive Bayes algorithm is well suited to text classification as its test time prediction is quick and as a result it can be deployed on a large dataset for inference.

 

Naive Bayes is usually used in applications where predictions are desired in real time such as fraud detection on credit card transactions. In these applications, a classifier that is capable of performing almost instantaneously is desired. Naive Bayes is also used extensively in text classification, spam filtering and sentiment analysis. In spam filtering, the words of an email or text message serve as the input features to the model, with each word assumed to be independent of others. Naive Bayes usually produces good results when this independent assumption holds true and coupled with its short inference time is sometimes preferred over more complicated classifiers.

Another area where Naive Bayes algorithm is widely used is in multi-class classification. In this domain, multiple classes or categories can be predicted given input features, with probabilities assigned to the predicted classes.

How to Build a Basic Model Using Naive Bayes in Python

For our hands on example we would build a Naive Bayes model in Python to tackle a spam classification problem. We would use the SMS spam collection dataset which is a set of 5,574 English text messages annotated to indicate the category. There are two categories - ham or legitimate messages and spam. The dataset can be downloaded from the following URL ([https://www.kaggle.com/uciml/sms-spam-collection-dataset/downloads/spam.csv/1](https://www.kaggle.com/uciml/sms-spam-collection-dataset/downloads/spam.csv/1)).

 

We would use the multinomial Naive Bayes classifier from Scikit-Learn machine learning library. As always, we begin by importing the libraries we would utilize.

 

import numpy as np

import pandas as pd

import matplotlib.pyplot as plt

\# comment the magic command below if not running in Jupyter notebook

%matplotlib inline

 

Next we load the dataset using Pandas and display the first 5 rows.

 

data = pd.read\_csv('spam.csv', encoding='latin-1')

data.head(5)

 

![](images/00081.jpeg)

 

The column “v1” contains the class labels while “v2” are the contents of the SMS which we would use as the features of our model.

 

Let us plot a bar chart to visualize the distribution of legitimate and spam messages.

 

count\_class = pd.value\_counts(data\['v1'\], sort= True)

count\_class.plot(kind='bar', color=\[\['blue', 'red'\]\])

plt.title('Bar chart')

plt.show()

 

![](images/00082.gif)

 

The words cannot be fed directly into the model as the features, so we have to vectorize them to create new features. We do this by considering the frequency of words after removing words that commonly appear in English sentences like “the”, “a”, “of” etc. We can do this feature extraction easily by using Scikit-Learn.

 

from sklearn.feature\_extraction.text import CountVectorizer

 

f = CountVectorizer(stop\_words = 'english')

X = f.fit\_transform(data\["v2"\])

print(np.shape(X))

 

![](images/00083.jpeg)

 

After vectorization, 8,404 new features are created.

 

Next we map our target variables into categories and split the dataset into train and test sets.

 

from sklearn.model\_selection import train\_test\_split

 

data\["v1"\]=data\["v1"\].map({'spam':1,'ham':0})

X\_train, X\_test, y\_train, y\_test = train\_test\_split(X, data\['v1'\], test\_size=0.25, random\_state=42)

 

The next step involves initializing the Naive Bayes model and training it on the data.

 

from sklearn.naive\_bayes import MultinomialNB

 

clf = MultinomialNB()

clf.fit(X\_train, y\_train)

 

Finally, we gauge the model performance on the test set.

 

score = clf.score(X\_test, y\_test)

print('Accuracy: {}'.format(score))

 

![](images/00084.jpeg)

 

The Naive Bayes classifier attains an accuracy of 0.976, which means that it predicted the correct class for 97.6% of samples.

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

# Decision Trees and Random Forest

The Entropy of a Partition

Entropy can be defined as the measure of uncertainty in a sequence of random events. It is the rate of disorderliness in a sample space and is directly opposed to knowledge. When the entropy of a system is high, the knowledge that can be derived from the system is low and vice versa. An intuitive understanding of entropy is thinking of it as the amount of questions required to ask to arrive at some knowledge. For example, if I picked a random number and you were trying to guess what number it is. Asking a question like, “Is it an odd number”, reduces the possibilities space by half. This means that the entropy or the degree of uncertainty in trying to determine which number I choose is reduced. In the same vein, the amount of information gain is large because the question moved you closer to the answer by dividing the sample space. Entropy usually ranges from 0 to 1. A system with an entropy of 0 is highly stable and the knowledge that can be derived from such a system is high. In general terms, low entropy in a system indicates high knowledge while high entropy indicates low knowledge or instability.

 

Entropy can be represented mathematically as:

 

![](images/00085.jpeg)

 

The formula above is the negative sum of log probabilities of an event happening. Remember that probability indicates the confidence we have in an event occurring, therefore entropy is how surprising it would be, for a sequence of events to occur together.

 

In machine learning as we would see later with decision trees, the entropy of two or more attributes of a classifier is defined by:

 

![](images/00086.jpeg)

 

Decision trees are a machine learning algorithm that rely heavily on the entropy of an attribute and the information gain to determine how to classify samples in a classification problem. Let us look at decision trees in depth in the next section.

 

Creating a Decision Tree

A decision tree is a machine learning algorithm which is mainly used for classification that constructs a tree of possibilities where the branches in the tree represents decisions and the leaves represents label classification. The purpose of a decision tree is to create a structure where samples in each branch are homogenous or of the same type. It does this by splitting samples in the training data according to specific attributes that increase homogeneity in branches. These attributes form the decision node along which samples are separated. The process continues until all sample are correctly predicted as represented by the leaves of the tree.

 

To explain the concept of a decision tree further, let us look at a toy example below that demonstrates its capability.

 

![](images/00087.jpeg)

 

Let us assume that we are a laptop manufacturer and we want to predict which customers from an online store are likely to buy our new top of the range laptop, so that we can focus our marketing efforts accordingly. This problem can be modelled using a decision tree with two classes (yes or no), for whether a person is likely to purchase or not.

 

At the root of the tree, we want to choose an attribute about customers that reduces entropy the most. As we saw in the last section, by reducing the entropy, we increase the amount of knowledge that is contained in the system. We choose the appropriate attribute by calculating the entropy of each branch and the entropy of the targets (yes or no). The information gain is closely related to the entropy and is defined as the difference in entropy of the targets (final entropy) and the entropy given a particular attribute was chosen as the root node.

 

![](images/00088.jpeg)

 

The formula above is used to calculate the decrease in entropy. The attribute with the largest information gain or decrease in entropy is chosen as the root node. This means that the attribute reduces the decision space the most when compared to other attributes. The process is repeated to find other decision nodes via attributes until all samples are correctly classified through the leaves of the decision tree.

 

In  the example above, age is the attribute that offers the most information gain so samples are split on that decision node. If the customer is middle aged, then they are likely to purchase a new laptop as they are probably working and have higher spending power. If the customer is a youth this brings us to another decision node. The attribute used is whether the youth is a student or not. If the youth is a student, they are likely to buy else they are not. That brings us to the leaves (classes) of the node following the youth branch of the tree. For the senior branch, we again split samples on an informative attribute, in this case credit rating. If the senior has an excellent credit rating that means they are likely to buy, else the leaf or classification for that sample along this branch of the tree is no.

 

Let us now work on an example using Python, Scikit-Learn and decision trees. We would tackle a multi-class classification problem where the the challenge is to classify wine into three types using features such as alcohol, color intensity, hue etc. The data we would use comes from the wine recognition dataset by UC Irvine. It can be downloaded at [https://gist.github.com/tijptjik/9408623/archive/b237fa5848349a14a14e5d4107dc7897c21951f5.zip](https://gist.github.com/tijptjik/9408623/archive/b237fa5848349a14a14e5d4107dc7897c21951f5.zip)

 

First, lets load the dataset and use Pandas head method to have a look at it.

 

import numpy as np

import pandas as pd

import matplotlib.pyplot as plt

\# comment the magic command below if not running in Jupyter notebook

%matplotlib inline

 

dataset = pd.read\_csv('wine.csv')

dataset.head(5)

 

![](images/00089.jpeg)

 

There are 13 predictors and the first column “wine” contains the targets. The next thing we do is split the dataset into predictors and targets, sometimes referred to as features and labels respectively.

 

features = dataset.drop(\['Wine'\], axis=1)

labels = dataset\['Wine'\]

 

As is the custom to ensure good evaluation of our model, we divide the dataset into a train and test split.

 

from sklearn.model\_selection import train\_test\_split

features\_train, features\_test, labels\_train, labels\_test = train\_test\_split(features, labels, test\_size=0.25)

 

All that is left is for us to import the decision tree classifier and fit it to our data.

 

from sklearn.tree import DecisionTreeClassifier

classifier = DecisionTreeClassifier()

 

classifier.fit(features\_train, labels\_train)

 

We can now evaluate the trained model on the test set and print out the accuracy.

 

pred = classifier.predict(features\_test)

 

from sklearn.metrics import accuracy\_score

accuracy = accuracy\_score(labels\_test, pred)

print('Accuracy: {:.2f}'.format(accuracy))

 

![](images/00090.jpeg)

 

We achieve an accuracy of 0.91 which is very impressive. It means that 91% of samples in our test set were correctly classified.

Random Forests

Random forests are a type of ensemble model. An ensemble model is one which is constructed from other models. This means that it is a combination of several weak learners to form a strong learner. The prediction of an ensemble model may be the average or weighted average of all learners that it is comprised of.

 

Random forests are an extension of decision trees whereby several decision trees are grown to form a forest. The final prediction of a random forest model is a combination of all component decision trees. For regression it may be a simple average of outputs or a label vote in the case of classification. Though random forest are made of several decision trees, each decision tree is trained on a subset of data that is randomly selected hence the name random forest. The other trick of random forest is that unlike a decision tree where the best attribute is chosen in order to split samples at a decision node from all available attributes, random forest only picks the best attribute from a subset of randomly chosen attributes for each decision node. As a result, each node in a tree is not deterministic, that is for each time we run the algorithm, we are likely to end up with different tree structures. However, the most informative attributes still find their way to trees in the forest and are present across many trees. This makes the results of the random forest algorithm to be less prone to errors due to variations in the input data.

 

The subset of data on which a decision tree that makes up a random forest is trained on is called bagged data and is usually around 60% of the entire dataset. The remainder on which the performance of individuals trees are tested on is known as the out-of-bag data. Therefore each tree in the forest is trained and evaluated on a different subset of data through the randomization process.

![](images/00091.jpeg)

 

The image above shows a pictorial representation of random forests. It is made up of several trees trained on different instances of the dataset. The attributes in each decision node are also randomized. Finally, the output prediction is an ensemble of the classification of each decision tree.

 

We would now try out a random forest classifier on the wine dataset and compare its performance on the test set to the decision tree model in the previous section. The beautiful thing about using machine learning models from Scikit-Learn is that the APIs to train and test a model are the same regardless of the algorithm being used. So you would notice that we only need to import the correct classifier, initialize it and all other portions of code would remain unchanged. We are already familiar with how parts of the code works so here is the code for random forest in full.

 

import numpy as np

import pandas as pd

 

\# load dataset

dataset = pd.read\_csv('wine.csv')

 

\# separate features and labels

features = dataset.drop(\['Wine'\], axis=1)

labels = dataset\['Wine'\]

 

\# split dataset into train and test sets

from sklearn.model\_selection import train\_test\_split

features\_train, features\_test, labels\_train, labels\_test = train\_test\_split(features, labels, test\_size=0.25)

 

\# import random forest classifier from sklearn

from sklearn.ensemble import RandomForestClassifier

classifier = RandomForestClassifier()

 

\# fit classifier on data

classifier.fit(features\_train, labels\_train)

 

\# predict classes of test set samples

pred = classifier.predict(features\_test)

 

\# evaluate classifier performance using accuracy metric

from sklearn.metrics import accuracy\_score

accuracy = accuracy\_score(labels\_test, pred)

print('Accuracy: {:.2f}'.format(accuracy))

 

![](images/00092.jpeg)

 

We achieve an accuracy of 98% on the test set which is a massive jump from 91% when we used a decision tree classifier. We can see that the randomization approach of random forest enables the algorithm to generalize better hence higher accuracy is recorded on the test set.

 

 

 

 

 

 

 

 

 

 

 

 

# Neural Networks

Perceptrons

The perceptron is a binary linear classifier that is only capable of predicting classes of samples if those samples can be separated via a straight line. The perceptron algorithm was introduced by Frank Rosenblatt in 1957. It classifies samples using hand crafted features which represents information about the samples, weighs the features on how important they are to the final prediction and the resulting computation is compared against a threshold value.

![](images/00093.gif)

 

In the image above, X represents the inputs to the model and W represents the weights (how important are individual features). A linear computation of the weighted sum of features is carried out during the formula below:

 

![](images/00094.gif)

 

The value of z is then passed through a step function to predict the class of the sample. A step function is an instant transformation of a value from 0 to 1. What this means is that if z is greater than or equal to 0, its predicts one class, else it predicts the other.  The step function can be represented mathematically as:

 

![](images/00095.gif)

 

At each iteration, the predicted class gets compared to the actual class and the weights gets updated if the prediction was wrong else it is left unchanged in the case of a correct prediction. Updates of weights continue until all samples are correctly predicted, at which point we can say that the perceptron classifier has found a linear decision boundary that perfectly separates all samples into two mutually exclusive classes.

 

During training the weights are updated by adding a small value to the original weights. The amount added is determined by the perceptron learning rule. The weight update process can be experienced mathematically as shown below.

 

![](images/00096.gif)

 

The amount by which weights are updated is given by the perceptron learning rule below.

 

![](images/00097.gif)

 

The first coefficient on the right hand side of the equation is called the learning rate and acts as a scaling factor to increase or decrease the extent of the update. The intuitive understanding of the above equation is that with each pass through the training set, the weights of misclassified examples are nudged in the correct direction so that the value of z can be such that the step function correctly classifies the sample. It should be noted that the perceptron learning algorithm described is severely limited as it can only learn simple functions that have a clear linear boundary. The perceptron is almost never used in practice but served as an integral building block during the earlier development of artificial neural networks.

 

Modern iterations are known as multi-layer perceptrons. Multi-layer perceptrons are feed forward neural networks that have several nodes in the structure of a perceptron. However, there are important differences. A multilayer perceptron is made up of multiple layers of neurons stacked to form a network. The activation functions used are non-linear unlike the perceptron model that uses a step function. Nonlinear activations are capable of capturing more interesting representations of data and as such do not require input data to be linearly separable. The other important difference is that multi-layer perceptrons are trained using a different kind of algorithm called backpropagation which enables training across multiple layers.

 

Backpropagation

Backpropagation is an algorithm technique that is used to solve the issue of credit assignment in artificial neural networks. What that means is that it is used to determine how much an input’s features and weights contribute to the final output of the model. Unlike the perceptron learning rule, backpropagation is used to calculate the gradients, which tell us how much a change in the parameters of the model affects the final output. The gradients are used to train the model by using them as an error signal to indicate to the model how far off its predictions are from the ground truth. The backpropagation algorithm can be thought of as the chain rule of derivatives applied across layers.

 

Let us look at a full fledged illustration of a multi-layer perceptron to understand things further.

 

![](images/00098.gif)

 

The network above is made up of three layers, the input layer which are the features fed into the network, the hidden layer which is so called because we cannot observe what goes on inside and the output layer, through which we get the prediction of the model. During training, in order to calculate by how each node contributes to the final prediction and adjust them accordingly to yield a higher accuracy across samples, we need to change the weights using the backpropagation algorithm. It is the weights that are learned during the training process hence they are sometimes referred to as the learnable parameters of the model. To visually understand what goes on during backpropagation, lets us look at the image of a single node below.

 

![](images/00099.jpeg)

 

 

In the node above x and y are the input features while f is the nonlinear activation function. During training computations are calculated in a forward fashion from the inputs, across the hidden layers, all the way to the output. This is known as the forward pass denoted by green arrows in the image. The prediction of the model is then compared to the ground truth and the error is propagated backwards. This is known as the backward pass and assigns the amount by which every node is responsible for the computed error through the backpropagation algorithm. It is depicted with red arrows in the image above. This process continues until the model finds a set of weights that captures the underlying data representation and correctly predicts majority of samples.

How to run the Neural Network using TensorFlow

For our hands on example, we would do image classification using the MNIST handwritten digits database which contains pictures of handwritten digits ranging from 0 to 9 in black and white. The task is to train a neural network that given an input digit image, it can predict the class of the number contained therein.

How to get our data

TensorFlow includes several preloaded datasets which we can use to learn or test out our ideas during experimentation. The MNIST database is one of such cleaned up datasets that is simple and easy to understand. Each data point is a black and white image with only one color channel. Each pixel in the image denotes the brightness of that point with 0 indicating black and 255 white. The numbers range from 0 to 255 for 784 points in a 28 × 28 grid.

Let’s go ahead and load the data from TensorFlow along with importing other relevant libraries.

 

\# Import MNIST data

from tensorflow.examples.tutorials.mnist import input\_data

mnist = input\_data.read\_data\_sets("/tmp/data/", one\_hot=True)

 

import numpy as np

import tensorflow as tf

import matplotlib.pyplot as plt

 

Let us use the matplotlib library to display an image to see what it looks like by running the following lines of code.

 

plt.imshow(np.reshape(mnist.train.images\[8\], \[28, 28\]), cmap='gray')

plt.show()

 

![](images/00100.gif)

The displayed image is a handwritten digit of number 9.

How to train and test the data

In order to train an artificial neural network model on our data, we first need to define the parameters that describe the computation graph such as number of neurons in each hidden layer, number of hidden layers, input size, number of output classes etc. Each image in the dataset is 28 by 28 pixels therefore, the input shape is 784 which is 28 × 28.

 

\# Parameters

learning\_rate = 0.1

num\_steps = 500

batch\_size = 128

display\_step = 100

 

\# Network Parameters

n\_hidden\_1 = 10 # 1st layer number of neurons

n\_hidden\_2 = 10 # 2nd layer number of neurons

num\_input = 784 # MNIST data input (img shape: 28\*28)

num\_classes = 10 # MNIST total classes (0-9 digits)

 

\# tf Graph input

X = tf.placeholder("float", \[None, num\_input\])

Y = tf.placeholder("float", \[None, num\_classes\])

 

We then declare weights and biases which are trainable parameters and initialise them randomly to very small values. The declarations are stored in a Python dictionary.

 

\# Store layers weight & bias

weights = {

    'h1': tf.Variable(tf.random\_normal(\[num\_input, n\_hidden\_1\])),

    'h2': tf.Variable(tf.random\_normal(\[n\_hidden\_1, n\_hidden\_2\])),

    'out': tf.Variable(tf.random\_normal(\[n\_hidden\_2, num\_classes\]))

}

biases = {

    'b1': tf.Variable(tf.random\_normal(\[n\_hidden\_1\])),

    'b2': tf.Variable(tf.random\_normal(\[n\_hidden\_2\])),

    'out': tf.Variable(tf.random\_normal(\[num\_classes\]))

}

 

We are would then describe a 3-layer neural network with 10 units in the output for each of the class digits and define the model by creating a function which forward propagates the inputs through the layers. Note that we are still describing all these operations on the computation graph.

 

\# Create model

def neural\_net(x):

    # Hidden fully connected layer with 10 neurons

    layer\_1 = tf.add(tf.matmul(x, weights\['h1'\]), biases\['b1'\])

    # Hidden fully connected layer with 10 neurons

    layer\_2 = tf.add(tf.matmul(layer\_1, weights\['h2'\]), biases\['b2'\])

    # Output fully connected layer with a neuron for each class

    out\_layer = tf.matmul(layer\_2, weights\['out'\]) + biases\['out'\]

    return out\_layer

 

Next we call our function, define the loss objective, choose the optimizer that would be used to train the model and initialise all variables.

 

\# Construct model

logits = neural\_net(X)

 

\# Define loss and optimizer

loss\_op = tf.reduce\_mean(tf.nn.softmax\_cross\_entropy\_with\_logits(

    logits=logits, labels=Y))

optimizer = tf.train.AdamOptimizer(learning\_rate=learning\_rate)

train\_op = optimizer.minimize(loss\_op)

 

\# Evaluate model (with test logits, for dropout to be disabled)

correct\_pred = tf.equal(tf.argmax(logits, 1), tf.argmax(Y, 1))

accuracy = tf.reduce\_mean(tf.cast(correct\_pred, tf.float32))

 

\# Initialize the variables (i.e. assign their default value)

init = tf.global\_variables\_initializer()

 

Finally, we create a session, supply images in batches to the model for training and print the loss and accuracy for each mini-batch.

 

\# Start training

with tf.Session() as sess:

 

    # Run the initializer

    sess.run(init)

 

    for step in range(1, num\_steps+1):

        batch\_x, batch\_y = mnist.train.next\_batch(batch\_size)

        # Run optimization op (backprop)

        sess.run(train\_op, feed\_dict={X: batch\_x, Y: batch\_y})

        if step % display\_step == 0 or step == 1:

            # Calculate batch loss and accuracy

            loss, acc = sess.run(\[loss\_op, accuracy\], feed\_dict={X: batch\_x,

                                                                 Y: batch\_y})

            print("Step " + str(step) + ", Minibatch Loss= " + \\

                  "{:.4f}".format(loss) + ", Training Accuracy= " + \\

                  "{:.3f}".format(acc))

 

    print("Optimization Finished!")

 

    # Calculate accuracy for MNIST test images

    print("Testing Accuracy:", \\

        sess.run(accuracy, feed\_dict={X: mnist.test.images,

                                      Y: mnist.test.labels}))

 

The session was created using with, so it automatically closes after executing. This is the recommended way of running a session as we would not need to manually close it. Below is the output

 

![](images/00101.jpeg)

The loss drops to 0.4863 after training for 500 steps and we achieve an accuracy of 85% on the test set.

Here is the code in full:

 

\# Parameters

learning\_rate = 0.1

num\_steps = 500

batch\_size = 128

display\_step = 100

 

\# Network Parameters

n\_hidden\_1 = 10 # 1st layer number of neurons

n\_hidden\_2 = 10 # 2nd layer number of neurons

num\_input = 784 # MNIST data input (img shape: 28\*28)

num\_classes = 10 # MNIST total classes (0-9 digits)

 

\# tf Graph input

X = tf.placeholder("float", \[None, num\_input\])

Y = tf.placeholder("float", \[None, num\_classes\])

 

\# Store layers weight & bias

weights = {

    'h1': tf.Variable(tf.random\_normal(\[num\_input, n\_hidden\_1\])),

    'h2': tf.Variable(tf.random\_normal(\[n\_hidden\_1, n\_hidden\_2\])),

    'out': tf.Variable(tf.random\_normal(\[n\_hidden\_2, num\_classes\]))

}

biases = {

    'b1': tf.Variable(tf.random\_normal(\[n\_hidden\_1\])),

    'b2': tf.Variable(tf.random\_normal(\[n\_hidden\_2\])),

    'out': tf.Variable(tf.random\_normal(\[num\_classes\]))

}

 

\# Create model

def neural\_net(x):

    # Hidden fully connected layer with 10 neurons

    layer\_1 = tf.add(tf.matmul(x, weights\['h1'\]), biases\['b1'\])

    # Hidden fully connected layer with 10 neurons

    layer\_2 = tf.add(tf.matmul(layer\_1, weights\['h2'\]), biases\['b2'\])

    # Output fully connected layer with a neuron for each class

    out\_layer = tf.matmul(layer\_2, weights\['out'\]) + biases\['out'\]

    return out\_layer

 

\# Construct model

logits = neural\_net(X)

 

\# Define loss and optimizer

loss\_op = tf.reduce\_mean(tf.nn.softmax\_cross\_entropy\_with\_logits(

    logits=logits, labels=Y))

optimizer = tf.train.AdamOptimizer(learning\_rate=learning\_rate)

train\_op = optimizer.minimize(loss\_op)

 

\# Evaluate model (with test logits, for dropout to be disabled)

correct\_pred = tf.equal(tf.argmax(logits, 1), tf.argmax(Y, 1))

accuracy = tf.reduce\_mean(tf.cast(correct\_pred, tf.float32))

 

\# Initialize the variables (i.e. assign their default value)

init = tf.global\_variables\_initializer()

 

\# Start training

with tf.Session() as sess:

 

    # Run the initializer

    sess.run(init)

 

    for step in range(1, num\_steps+1):

        batch\_x, batch\_y = mnist.train.next\_batch(batch\_size)

        # Run optimization op (backprop)

        sess.run(train\_op, feed\_dict={X: batch\_x, Y: batch\_y})

        if step % display\_step == 0 or step == 1:

            # Calculate batch loss and accuracy

            loss, acc = sess.run(\[loss\_op, accuracy\], feed\_dict={X: batch\_x,

                                                                 Y: batch\_y})

            print("Step " + str(step) + ", Minibatch Loss= " + \\

                  "{:.4f}".format(loss) + ", Training Accuracy= " + \\

                  "{:.3f}".format(acc))

 

    print("Optimization Finished!")

 

    # Calculate accuracy for MNIST test images

    print("Testing Accuracy:", \\

        sess.run(accuracy, feed\_dict={X: mnist.test.images,

                                      Y: mnist.test.labels}))

# Clustering

Clustering is the most common form of unsupervised learning. Clustering involves grouping objects or entities into clusters (groups) based on a similarity metric. What clustering algorithms aim to achieve is to make all members of a group as similar as possible but make the cluster dissimilar to other clusters. At first glance clustering looks a lot like classification since we are putting data points into categories, while that may be the case, the main difference is that in clustering we are creating categories without the help of a human teacher. Whereas, in classification, objects were assigned to categories based on the domain knowledge of a human expert. That is in classification we had human labelled examples which means the labels acted as a supervisor teaching the algorithm how to recognise various categories.

 

In clustering, the clusters or groups that are discovered are purely dependent on the data itself. The data distribution is what drives the kind of clusters that are found by the algorithm. There are no labels so clustering algorithms are forced to learn representations in an unsupervised manner devoid of direct human intervention.

 

Clustering algorithms are divided into two main groups - hard clustering algorithms and soft clustering algorithms. Hard clustering algorithms are those clustering algorithms that find clusters from data such that a data point can only belong to one cluster and no more. Soft clustering algorithms employ a technique whereby a data point may belong to more than one cluster, that is the data point is represented across the distribution of clusters using a probability estimate that assigns how likely the point belongs to one cluster or the other.

![](images/00102.jpeg)

From the data distribution of the image above, we can deduce that a clustering algorithm has been able to find 5 clusters using a distance measure such as Euclidean distance. It would be observed that data points close to cluster boundaries are equally likely to fall into any neighboring cluster. Some clustering algorithms are deterministic meaning that they always produce the same set of clusters regardless of initialization conditions or how many times they are run. Other clustering algorithms produce a different cluster collection everytime they are run and as such it may not be easy to reproduce results.

 

Introduction to Clustering

The most important input to a clustering algorithm is the distance measure. This is so because it is used to determine how similar two or more points are to each other. It forms the basis of all clustering algorithms since clustering is inherently about discriminating entities based on similarity.

Another way clustering algorithms are categorized is using the relationship structure between clusters. There are two subgroups - flat clustering and hierarchical clustering algorithms. In flat clustering, the clusters do not share any explicit structure so there is no definite way of relating one cluster to the other. A very popular implementation of a flat clustering algorithm is K-means algorithm which we would use as a case study.

Hierarchical clustering algorithms first starts with each data point belonging to its own cluster, then similar data points are merged into a bigger cluster and the process continues until all data points are part of one big cluster. As a result of the process of finding clusters, there is a clear hierarchical relationship between discovered clusters.

There are advantages and disadvantages to the flat and hierarchical approach. Hierarchical algorithms are usually deterministic and do not require us to supply the number of clusters beforehand. However, this leads to computational inefficiency as we suffer from quadratic cost. The time taken to discover clusters by an hierarchical clustering algorithm increases as the size of the data increases.

 

Flat clustering algorithms are intuitive to understand and feature linear complexity, therefore the time taken to run the algorithm increases linearly with the number of data points and because of this flat clustering algorithms scale well to massive amounts of data. As a rule of thumb, flat clustering algorithms are generally used for large datasets where a distance metric can capture similarity while hierarchical algorithms are used for smaller datasets.

Example of Clustering

We would have a detailed look at an example of a flat clustering algorithm, K-means. We would also use it on a dataset to see its performance.

K-means is an iterative clustering algorithm that seeks to assign data points to clusters. To run K-means algorithm, we first need to supply the number of clusters we desire to find. Next, the algorithm randomly assigns each point to a cluster and computes the cluster centroids (center of cluster). At this stage points are reassigned to new clusters based on how close they are to cluster centroids. We again recompute the cluster centroids. Finally we repeat the last two steps until no data points are being reassigned to new clusters. The algorithm has now converged and we have our final clusters.

Running K-means with Scikit-Learn

For our hands on example we would use K-means algorithm to find clusters in the Iris dataset. The Iris dataset is a classic in the machine learning community. It contains 4 attributes (sepal length, sepal width, petal length, petal width) used to describe 3 species of the Iris plant. The dataset can be found at:

[https://www.kaggle.com/saurabh00007/iriscsv/downloads/Iris.csv/1](https://www.kaggle.com/saurabh00007/iriscsv/downloads/Iris.csv/1)

The first step is to load the data and run the head method on the dataset to know our features

 

\# import libraries

import numpy as np

import pandas as pd

import matplotlib.pyplot as plt

 

\# read dataset from csv file

dataset = pd.read\_csv('Iris.csv')

 

\# display first five observations

dataset.head(5)

 

![](images/00103.jpeg)

We have 4 informative features and 6 columns. Id is an identifier while Species column contains the label. Since this is a clustering task, we do not need labels as we would find clusters in an unsupervised manner.

 

x = dataset.drop(\['Id', 'Species'\], axis=1)

x = x.values # select values and convert dataframe to numpy array

 

The above line of code selects all our features into x dropping Id and Species.

As was earlier discussed, because K-means is a flat clustering algorithm we need to specify the value of k (number of clusters) before we run the algorithm. However, we do not know the optimal value for k, so we use a technique known as the elbow method. The elbow method plots the percentage of variance explained as a result of number of clusters. The optimal value of k from the graph would be the point where the sum of squared error (SSE) does not improve significantly with increase in the number of clusters.

Let’s take a at look at these concepts in action

 

\# finding the optimum number of clusters for k-means classification

from sklearn.cluster import KMeans

wcss = \[\] # array to hold sum of squared distances within clusters

 

for i in range(1, 11):

    kmeans = KMeans(n\_clusters = i, init = 'k-means++', max\_iter = 300, n\_init = 10, random\_state = 0)

    kmeans.fit(x)

    wcss.append(kmeans.inertia\_)

 

\# plotting the results onto a line graph, allowing us to observe 'The elbow'

plt.plot(range(1, 11), wcss)

plt.title('The elbow method')

plt.xlabel('Number of clusters')

plt.ylabel('Within Cluster Sum of Squares') # within cluster sum of squares

plt.show()

 

![](images/00104.jpeg)

The k-means algorithm is run for 10 iterations, with n\_clusters ranging from 1 to 10. At each iteration the sum of squared error (SSE) is recoded. The sum of squared distances within each cluster configuration is then plotted against the number of clusters. The “elbow” from the graph is 3 and this is the optimal value for k.

Now that we know that the optimal value for k is 3, we create a K-means object using Scikit-Learn and set the parameter of n\_clusters (number of clusters to generate) to 3.

 

\# creating the kmeans object

kmeans = KMeans(n\_clusters = 3, init = 'k-means++', max\_iter = 300, n\_init = 10, random\_state = 0)

 

Next we use the fit\_predict method on our object. This returns a computation of cluster centers and cluster predictions for each sample.

 

y\_kmeans = kmeans.fit\_predict(x)

 

We then plot the predictions for clusters using a scatter plot of the first two features.

 

\# visualising the clusters

plt.scatter(x\[y\_kmeans == 0, 0\], x\[y\_kmeans == 0, 1\], s = 100, c = 'red', label = 'Iris-setosa')

plt.scatter(x\[y\_kmeans == 1, 0\], x\[y\_kmeans == 1, 1\], s = 100, c = 'blue', label = 'Iris-versicolour')

plt.scatter(x\[y\_kmeans == 2, 0\], x\[y\_kmeans == 2, 1\], s = 100, c = 'green', label = 'Iris-virginica')

 

\# plotting the centroids of the clusters

plt.scatter(kmeans.cluster\_centers\_\[:, 0\], kmeans.cluster\_centers\_\[:,1\], s = 100, c = 'yellow', label = 'Centroids')

 

plt.legend()

 

![](images/00105.jpeg)

The plot shows 3 clusters - red, blue, green representing types of Iris plant, setosa, versicolour and virginica respectively. The yellow point indicates the centroids which is at the center of each cluster.

Our K-means algorithm was able to find the correct number of clusters which is 3 because we used the elbow method. It would be observed that the original dataset had three types (classes) of Iris plant. Iris setosa, Iris versicolour and Iris virginica. If this were posed as a classification problem we would have had 3 classes into which we would have classified data points. However, because it was posed as a clustering problem, we were still able to find the optimum number of clusters - 3, which is equal to the number of classes in our dataset.

What this teaches us is that most classification problems and datasets can be used for unsupervised learning particularly for clustering tasks. The main intuition to take out of this is that if we want to use a classification dataset for clustering, we must remove labels, that is we remove the component of the data that was annotated by a human to enable supervision. We then train on the raw dataset to discover inherent patterns contained in the data distribution.

 

While we have only touched on a portion of unsupervised learning, it is important to note that it is a vital branch of machine learning with lots of real world applications. Clustering as an example can be used to discover data groups and get a unique perspective of data before feeding it into traditional supervised learning algorithms.

 

 

Implementation of the Model

Clustering is a type of unsupervised learning technique in which there are no explicit labels. Clustering is used to discover groups of data points in a dataset. A group or cluster is made up of members that are similar to each other but are collectively different from other clusters. A good clustering algorithm must have the ability to discover some or all hidden clusters in a dataset, should exhibit in cluster similarity but different clusters should be dissimilar or far from each other. The clustering algorithm should also be scalable to larger datasets and should be able to handle noisy data points and outliers.

 

There are two main categories of clustering algorithms - hierarchical clustering algorithms and partitive clustering algorithms. In hierarchical clustering, there is a clear relationship between discovered clusters. This can take the form of a hierarchy or order. Whereas in partitive algorithms, the relationship between clusters is not clear and it is sometimes referred to as having a flat structure. Clustering algorithms can also be seen from another perspective. Algorithms that allow a data point to belong to more than one cluster are known as soft clustering algorithms. In such a process, probabilities are assigned to each data point to indicate how likely it belongs to any particular cluster. Hard clustering algorithms on the other hand, require that data points only belong to exactly one cluster.

 

Hierarchical clustering algorithms are deterministic, which means that each time the algorithm is deployed on a dataset, we are bound to find the same clusters. This enables reproducibility of results. Partitive algorithms are non-deterministic and would produce a slightly different cluster representation with every run through the dataset.

 

Bottom-up Hierarchical Clustering

Bottom-up hierarchical clustering is a type of hierarchical clustering technique whereby every data point begins in a cluster of its own. A distance measure such as Euclidean distance is then used to calculate the distance of all points from one another. The points with the shortest distance are merged to form a cluster of their own. The process continues until all points belong to one big cluster. The intuition is that data points which are similar are likely to be separated by a small distance in the feature space.

 

A popular type of bottom-up clustering is the hierarchical agglomerative clustering algorithm. Here the distance measure may be Euclidean, Manhattan or Minkowski distance. When clusters are created, the distance between clusters may be the shortest distance between any two points in both clusters, known as single linkage, the farthest distance between two points, referred to as complete linkage or it may be an average of the distance of all data points in both clusters (average linkage).

 

Below is the mathematical expression for single linkage as described above.

 

![](images/00106.jpeg)

 

Where D is the distance measure example Manhattan distance. Manhattan distance can be expressed mathematically as:

 

![](images/00107.gif)

 

Let us look at an image of a dendrogram, which is just the way clusters are represented when using an hierarchical agglomerative clustering algorithm.

 

![](images/00108.gif)

 

In the dendrogram, each point (A through G) starts in a cluster of their own. Then they are merged into clusters with other points which they are not far away from. The process proceeds in a bottom-up fashion and the height represents the similarity between clusters at the point they were merged. After all data points are grouped as one cluster, a threshold value may be passed to trace back any number of clusters that is desired. This is represented as the horizontal line. There are therefore three clusters in the dendrogram above.

 

K-means Clustering

K-means is a partitive clustering algorithm that assigns data points into a predetermined number of clusters. The number of clusters must be passed as a metric to the algorithm. K-means works by randomly choosing centroids in a data distribution and assigning data points to centroids that they are closest to. The number of centroids is the same as the number of clusters to be determined. The centroids are then recomputed by taking the mean of all data points assigned to that centroid’s  cluster. The process is iterative. Data points are reassigned to centroids they are now closest to and the centroids are updated for each cluster. Convergence is achieved when data points are no longer reassigned to new clusters.

 

![](images/00109.gif)

 

The above image shows an example of a converged dataset. There are two clusters and data points belongs to the cluster they are closest to. The center of each cluster is represented by its centroid. K-means algorithm is sensitive to the number of clusters and the initialization of centroids. Depending on how centroids are initialized, we would end up with different data points in various clusters. Since K-means requires that the number of clusters be passed as a metric, it is desirable to know what the optimum  number of clusters would be for a dataset. This can be done using the elbow technique. Generally speaking, the error rate goes down rapidly as we increase the number of clusters until it saturates at a certain point where an increase in cluster size does not bring about a proportionate reduction in error. The elbow method tells us to choose as the optimum number of clusters the number of clusters for which the error rate has not plateaued.

 

 

 

 

 

 

# Network Analysis

Betweenness centrality

Graphs are a  type of data structure used to represent data that features high connectivity, that is the data has relationships that makes it connected. Network theory is the study of graphs as a way to understand the relationships between entities that made up a graph. Many kinds of analytical problems can be modelled as a graph problem, however it is best to use graphs when the data increases in complexity because of its interconnectedness. A very popular example of this kind of data is social media data which can be argued to possess an inherent network structure. Analysis of such data would not be well suited to traditional techniques as found in relational databases. Social media data can therefore be modelled as a graph network where vertices or nodes are connected to each other. Nodes could represent entities like people and edges could represent relationships. Modelling the data this way enables us to answer important questions about the nature of relationships between people and how people are likely to react to events given the reaction of their inner circle.

 

This brings us to the notion of centrality in network analysis. Centrality can be defined as determining which nodes or in our case people, are important to a particular network. Another way of framing this is, what node or entity is central to the way a network operates. There are many ways in which importance can be calculated in a network and these are known as centrality measures. Some of them are degree centrality, closeness centrality, betweenness centrality and eigenvector centrality.

 

![](images/00110.jpeg)

 

The image above is a network showing a graph representation of friends in a social context. The nodes represents individuals while the edges represents relationships. This is an example of an undirected graph. What that means is that the connections (edges) has no sense of direction. If we want to find out who is important in this network, we would use any of the centrality measures listed above.

 

Degree centrality is the number of edges connected to a node, it can be thought of as popularity or the exposure to the network. Even Though it is a very simple metric, it can be effective in some cases. Closeness centrality measures the average distance between a node and all other nodes in a network. It can be seen as having indirect influence on a network or the point through which information can be disseminated easily through a network.

 

Betweenness centrality measures how often a node is between the shortest path to any two randomly chosen nodes. In other words, betweenness is a measure of how many times a node acts as a bridge between the shortest path of any two nodes in the network. Betweenness centrality can be seen as conferring informal power on a node in terms of a node being a sort of gatekeeper or broker between parts of the network. Betweenness centrality of a node v can be expressed mathematically as:

 

![](images/00111.jpeg)

 

Where the denominator is the total number of the shortest paths from nodes s to t and the numerator is the number of those shortest paths that go through node v.

 

Eigenvector Centrality

Eigenvector centrality is a centrality measure that not only considers how many nodes a particular node is connected to, but factors in the quality or importance of such nodes in its calculation. Intuitively, eigenvector centrality measures “not what you know but who you know”. So the centrality of every node is calculated based on the quality of its connections and not just the number of connections as is the case in degree centrality. Eigenvector centrality can be seen as a measure of the extent to which a node is connected to other influential nodes.

 

Google at its core uses the Pagerank algorithm which is a variant of eigenvector centrality to rank the relevancy of results based on users search queries. The intuition is that websites are modelled as nodes on a network and the entire world wide web is represented as one big network. Nodes (websites) would be ranked higher based on the quality or reputation of other websites that point to them. Merely increasing the number of links that point to a site does not increase its influence in terms of how it is ranked in search results. Links that point to a website have to come from important websites for the ranking of a particular website to increase. This is sensible as popular websites are more likely to point to the most relevant content. Eigenvector centrality is a powerful metric that is used in analyzing networks.

 

Recommender Systems

The information overload as occasioned by the internet has lead to a paralysis of sorts as users are overwhelmed with variety of choices. Recommender systems are a way through which information is filtered so that the most relevant content are shown to users. Recommender systems seek to predict the preference a user would give to an item or product in light of their past interaction or behaviors on a platform. It is one of the most commercially viable use cases of machine learning as companies from Amazon to Netflix all have a business model that benefits enormously from showing relevant content to users in order to increase sales or interaction with their platforms.

 

Recommender systems are divided into three broad categories based on the techniques they employ. There are content based filtering, collaborative filtering and hybrid recommender systems. Content based filtering relies on the features of an item and a user’s profile. Items are recommended based on how similar they are to a user’s tastes. A movie for example may have features such as actors, genre, director etc. A user with particular preferences would get recommendations of movies whose features match the user’s information.

Collaborative filtering makes use of a user’s past behavior, preferences etc  in combination with the preferences of other users to determine items that are recommended. Users are likely to appreciate items that are liked by other users with similar preferences.

Hybrid recommender systems combines approaches from content based filtering and collaborative filtering. They may  be used to manage the shortcomings of any particular approach example when a new item is added and we do not yet have enough information about that item or when users have not had many interactions on the platform to be able to accurately gauge their preferences.

  

Classification

In machine learning most learning problems can be modelled as a classification problem. A classification problem is one whose core objective is to learn a mapping function from a set of inputs to one or more discrete classes. Discrete classes are sometimes referred to as labels and both terms are often used interchangeably.

A class or label can be understood as a category that represents a particular quantity, therefore what classification algorithms do is to identify the category that an example fits into. If the classification problem is posed in such a way that there are two distinct classes, we have a binary classification problem. In a case where we have more than two classes (labels), the learning problem is referred to as multi-class classification indicating that observations could fall into any of the n classes. The final type of classification is where a sample may belong to several categories that is it has more than one label and in such a situation we would be dealing with a multi-label classification task.

To get a better mental picture of classification let's look at the image below:

 

![](images/00112.jpeg)

From the plot above we can see that there are two features that describe the data X1 and X2 . What a classification task seeks to do is divide the data into distinct categories such that there is a decision boundary that best separates classes. In this example we have two classes - falling companies and surviving companies, a data point which represents a company can only belong to one of those categories, falling or surviving. It is as a result clear that this is a binary classification example because there are only two classes.

Another point to note from the diagram is that the classes are linearly separable, that is they can be separated by a straight line. In other problems, this might not be possible and there are more robust machine learning algorithms that handle such instances.

Multi-Class Classification

It is important that we have a good understanding of classification based on the number of classes that we want to predict as classification has many real world applications. To further improve our intuition let us analyse the image below:

 

![](images/00113.jpeg)

The data is projected onto a two dimensional plane to enable visualization. There are three classes represented by red squares, blue triangles and green circles. There are also three decision boundaries that separates the data points into three sections with the color of the class projected on the background. What we have is a classic multi-class classification example with three classes (0, 1, 2), there are also some misclassified points however these are few and appear mostly close to the decision boundaries. 

To evaluate this model, we would use accuracy as our evaluation metric. The accuracy of our model is determined by the number of samples our classifier predicted corrected to the number of samples it misclassified. Accuracy is usually a good metric for classification tasks but bear in mind that there are other metrics such as precision and recall that we may wish to explore based on how we intend to model our learning task.

Popular Classification Algorithms

Some machine learning models deliver excellent results with classification tasks, in the next section we would have an indepth look at a couple of them. The process involved in running classification tasks are fairly standard across models.

First, we need to have a dataset that has a set of inputs and a corresponding set of labels. The reason this is important is because classification is a supervised learning task where we need access to the ground truth (actual classes) of observations in order to minimize the error in misclassification from our models. So to end up with a good model, we train the classifier on samples and provide the true values in a feedback mechanism forcing the classifier to learn and reduce its error rate on each iteration or pass through the training set (epoch).

Examples of models used for classification are logistic regression, decision trees, random forests, k-nearest neighbor, support vector machine etc. We use the last two models as case studies to practice classification.

 

 

 

 

  

Support Vector Machine

Support vector machines also known as support vector networks is a popular machine learning algorithm used for classification. The main intuition behind support vector machines is that it tries to locate an optimal hyperplane which separates data into correct classes making use of only those data points close to the hyperplane. The data points closest to the hyperplane are called support vectors.

There may be several hyperplanes that correctly separates classes but support vector machine algorithm chooses the hyperplane that has the largest distance (margin) from the support vectors (data points close to the hyperplane). The benefit of selecting a hyperplane with the widest margin is because this reduces the chance of mistakenly misclassifying a data point during test time.

 

![](images/00114.jpeg)

Support vector machine algorithm is robust to the presence of outliers in class distributions and works in a way that ignores outliers while finding the best hyperplane with a good margin width.

However, it is not in all cases that a data distribution may be linearly separable. Support vector machine (SVM) transforms the features that represents the data from a lower dimension into a higher dimension by introducing new features which are based on the original features found in the data. It does this automatically using a kernel. Some examples of kernels in SVM are linear kernel, polynomial kernel, Radial Basis Function (RBF) kernel etc.

Support vector machine has some advantages compared to other machine learning models. It is particularly potent in high dimensional spaces and because it only relies on a subset of data points for classification (the support vectors), it consumes less memory resulting in efficiency. It is also effective because we can pick different kernels based on the data representation at hand.

How to create and test the Support Vector Machine (SVM) classifier

For this section we would use a support vector machine classifier on the Pima Indian Diabetes Database and compare its results with the k-nearest neighbor classifier.

Here is the full code:

 

\# import libraries

import numpy as np

import pandas as pd

import matplotlib.pyplot as plt

 

\# read dataset from csv file

dataset = pd.read\_csv('diabetes.csv')

 

 

\# create features and labels

features = dataset.drop(\['Outcome'\], axis=1)

labels = dataset\['Outcome'\]

 

\# split dataset into training set and test set

from sklearn.model\_selection import train\_test\_split

features\_train, features\_test, labels\_train, labels\_test = train\_test\_split(features, labels, test\_size=0.25)

 

\# import support vector machine classifier

from sklearn.svm import SVC

classifier = SVC()

 

\# fit data

classifier.fit(features\_train, labels\_train)

 

\# get predicted class labels

pred = classifier.predict(features\_test)

 

\# get accuracy of model on test set

from sklearn.metrics import accuracy\_score

accuracy = accuracy\_score(labels\_test, pred)

print('Accuracy: {}'.format(accuracy))

 

We get an accuracy of 0.66 which is worse than 0.74 which we got for k-nearest neighbor classifier. There are many hyperparameters that we could try such as changing the type of kernel used.

 

from sklearn.svm import SVC

classifier = SVC(kernel='linear')

 

When we use a linear kernel our accuracy jumps to 0.76. This is an important lesson in machine learning as often times we do not know beforehand what the best hyperparameters are. So we need to experiment with several values before we can settle on the best performing hyperparameters.

 

 

 

 

 

 

 

 

 

 

 

  

Deep Learning using TensorFlow

Deep learning is a subfield of machine learning that makes use of algorithms which carry out feature learning to automatically discover feature representations in data. The “deep” in deep learning refers to the fact that this kind of learning is done across several layers, with higher level feature representations composed of simpler features detected earlier in the chain. The primary algorithm used in deep learning is a deep neural network composed of multiple layers. Deep learning is also known as hierarchical learning because it learns a hierarchy of features. The complexity of learned features increases as we move deeper in the network.

Deep learning techniques are loosely inspired by what is currently known about how the brain functions. The main idea is that the brain is composed of billions of neurons which interact with each other in some way through the use of electrical signals from chemical reactions. This interaction between neurons in conjunction with other organs helps humans to perform cognitive tasks such as seeing, hearing, taking decisions etc. What deep learning algorithms do is to arrange a network of neurons in a structure known as an Artificial Neural Network (ANN) to learn a mapping function from inputs directly to outputs. The difference between deep learning and a classical artificial neural network is that the layers of the network are several orders of magnitude larger hence it is commonly called a Deep Neural Network (DNN) or feedforward neural network.

 

To get a well-grounded understanding, it is important for us to take a step back and try to understand the concept of a single neuron. 

 

![](images/00115.jpeg)

First let us develop simple intuitions about a biological neuron. The image of a biological neuron above shows a single neuron made up of different parts. The brain consists of billions of similar neurons connected together to form a network. The dendrites are the components that carry information signals from other neurons earlier in the network into a particular neuron. It is helpful to think of this in the context of machine learning as features that have so far been learned by other neurons about our data. The cell body which contains the nucleus is where calculations that would determine whether we have identified the presence of a characteristic we are interested in detecting would take place. Generally, if a neuron is excited by its chemical composition as a result of inflowing information, it can decide to send a notification to a connected neuron in the form of an electrical signal. This electrical signal is sent through the axon. For our artificial use case, we can think of an artificial neuron firing a signal only when some condition has been met by its internal calculations. Finally, this network of neurons learn representations in such a way that connections between them are either strengthened or weakened depending on the current task at hand. The connections between biological neurons are called synapses and we would see an analogy of synapses in artificial neural networks known as weights which are parameters we would train to undertake a learning problem.

 

![](images/00116.jpeg)

Let us now translate what we know so far into an artificial neuron implemented as a computation unit. From the diagram, we can envisage X1, X2, to Xn as the features that are passed into the neuron. A feature represents a dimension of data from a data point. The combination of features completely describe that data point as captured by the data. W1 to Wn, are the weights and their job is to tell use how highly we should rank a feature. That is lower values for the weight means that the connected feature is not as important and higher values signify greater significance. All inputs to the artificial neural network are then summed linearly (added side by side). It is at this point that we determine whether to a send signal to the next neuron or not using a condition as a threshold. If the result of the linear calculation is greater than or equal to the threshold value, we send a signal else we don’t.

 

From the explanation, it is now plain to see why these techniques are loosely based on the operation of a biological neuron. However, it must be noted that deep learning beyond this point does not depend on neuroscience as a complete understanding of the way the brain functions is not known.

 

In deep neural networks, the activation criterion (whether we decide to fire a signal or not) is usually replaced with non-linear activation functions such as sigmoid, tanh or Rectified Linear Unit (ReLU). The reason a non-linear activation function is used is so that the artificial neural network can break linearity in order to enable it learn more complicated representations. If there were no non-linear activation functions, regardless of the depth of the network (number of layers), what it would learn is still a linear function which is severely limiting.

 

Let us now look at how we can arrange these neurons into an artificial neural network using the image below to explain the concepts.

 

![](images/00117.jpeg)

In the example, Variable 1 through 4 represents an input to the network in the form of features. An input may be an image, text or sequential data. The input layer which contains the variables (features) are connected to neurons in the hidden layer. The hidden layer is so called because we cannot directly inspect what goes on inside unlike the input or output layer which we have direct access to. There are 3 units or neurons in the hidden layer. The last layer is the output layer. This is where we get our predictions. In this case it is made up of a single neuron which suggests that it renders a single output. Such a neuron may be used to get a single real valued number in a regression problem or a class in a binary classification problem.

It would be observed that neurons in one layer are connected to all neurons in the next layer, because of this kind of configuration, we say that it is a fully connected layer. The strength of connections between neurons are governed by the weights. Finally, the above network is said to be a 2-layer neural network as the input layer is not counted when describing the number of layers contained in a network.

 

There are various architectures of deep neural networks, some architectures make assumptions about the type of data that the model expects. Those assumptions usually improve the performance of such models at the tasks which they were designed for. Convolutional Neural Networks (CNN) are designed with the assumption that they would be dealing with 2-dimensional data such as images and are the de-facto standard for computer vision tasks like image detection, image classification, image segmentation, object recognition etc. Recurrent Neural Networks (RNN) on the other hand are specially suited for handling sequential and temporal data like text and time series. Each of these architectures have further variants that are modifications to suit a particular learning problem.

Deep Learning Compared to Other Machine Learning Approaches

The popularity of deep learning is mainly based on the fact that it has achieved impressive results in diverse fields and is beginning to surpass humans in certain tasks such as object recognition. Compared to other machine learning techniques, it has been able to achieve state of the art results on many benchmarks and is applicable with slight modifications to a wide range of learning problems. The reason is that not only have artificial neural networks been shown to be capable of learning any function as illustrated by the universal approximation theorem, deep neural networks seem to improve their performance with more data. They are free from the plateau effect that traditional machine learning algorithms suffer from, whereby at some point the performance of the algorithm does not improve with the availability of additional data.

 

![](images/00118.jpeg)

 

Deep learning algorithms are seen as being data intensive because they need enormous amounts of data to achieve high accuracies and more data always appear to help performance. Deep learning is quickly becoming the go to solution for many machine learning problems where vast data is available occasioned by the advent of the internet.

Applications of Deep Learning

Deep learning has been applied to solve many problems which have real world applications and are now being transitioned into commercial products. In the field of computer vision, deep learning techniques are used for automatic colorization to transform old black and white photos, automatic tagging of friends in photos as seen in social networks and grouping of photos based on content into folders.

In Natural Language Processing (NLP), these algorithms are used for speech recognition in digital assistants, smart home speakers etc. With advances in Natural Language Understanding (NLU), chatbots are being deployed as customer service agents and machine translation has enabled real time translations from one language to the other.

Another prominent area is recommender systems, where users are offered personalized suggestions based on their preferences and previous spending habits. Simply put, deep learning algorithms are wildly beneficial and learning them is a quality investment of time and resources.

Python Deep Learning Frameworks

Python has a mature ecosystem with several production ready deep learning frameworks. Some of them are Pytorch, Chainer, MXNet Keras, TensorFlow etc. We would concentrate on using TensorFlow in this book as it is an extremely popular and supported deep learning framework open sourced by Google in 2015. TensorFlow uses the concept of a computation graph to construct a model. Nodes and operations are declared on the graph beforehand then at training time the model is compiled. In the next section we would see how to install TensorFlow and use it to perform deep learning tasks through a hands on example.

Install TensorFlow

TensorFlow is cross platform and can be installed on various operating systems. In this section we would see how it can be installed on the three widely used operating systems - Linux, macOS and Windows. TensorFlow can be installed using pip which is the native Python package manager, virtualenv - which creates a virtual environment or through a bundled scientific computation distribution like Anaconda. For the purpose of this book we would use pip.

Installing TensorFlow on Windows

For TensorFlow to be installed on Windows, you need to first install Python which comes bundled with pip as the package manager. Python can be downloaded as an executable at [https://www.python.org/downloads/windows](https://www.python.org/downloads/windows)

Once you have it installed, start a terminal and run the following command:

C:\\> pip3 install --upgrade tensorflow

 

Installing TensorFlow on Linux

For Linux distributions like Ubuntu and its variants, pip is usually already installed. To check which version of pip is installed, from the terminal run

$ pip -V

or

$ pip3 -V

This depends on the version of Python you have, pip for version 2.7 and pip3 for version 3.x

If you do not have pip installed, run the appropriate command for your Python version below:

$ sudo apt-get install python-pip python-dev   # for Python 2.7  
$ sudo apt-get install python3-pip python3-dev # for Python 3.n

It is recommended that your version of pip or pip3 is 8.1 or greater. Now you can install TensorFlow with the following command

$ pip install tensorflow      # Python 2.7  
$ pip3 install tensorflow     # Python 3.x

Installing TensorFlow on macOS

To install TensorFlow on macOS, you need to have Python installed as it is a prerequisite. To check if you have pip installed run

 

$ pip -V

or

$ pip3 -V

This depends on the version of Python you have, pip for version 2.7 and pip3 for version 3.x

If you do not have pip installed, or you have a version lower than 8.1, run the commands to install or upgrade:

$ sudo easy\_install --upgrade pip

$ sudo easy\_install --upgrade six

Now you can install TensorFlow with the following command

$ pip install tensorflow      # Python 2.7

$ pip3 install tensorflow     # Python 3.x

How to Create a Neural Network Model

In order to create a neural network in TensorFlow it is important to understand how TensorFlow works. The following steps would help us understand what we need to do:

 

1.  Build a Computation Graph: First we need to define mathematical operations which would be carried out on tensors. We can think of tensors as a higher order matrix. A matrix is an array containing numbers arranged in rows and columns. Data structures such as images can be represented as matrices and since deep learning uses geometric transformations, the input to any model must be numeric.
2.  Initialisation of Variables: All previously declared variables have to be initialised before we can train the model. In TensorFlow, variables are usually declared using placeholders which register on the computation graph but the values are actually supplied later.
3.  Creation of Session: After we have described the computation graph and initialised variables, the next step is to create a session within which the computation graph would be executed.
4.  Running of Graph in Session: The complete graph along with values for placeholders is passed to the session for execution. This is when the mathematical operations defined in the graph takes place.
5.  Close Session: When the graph and related computations have finished executing, we need to shutdown or end the session.

 

![](images/00119.jpeg)

 

 

The diagram above shows a simple computation graph for a function. Using TensorFlow we would describe something similar that defines a neural network in the next chapter.

  

Deep Learning Case Studies

In this chapter we would work with data that can be used for real world applications. Two case studies would be performed, the first involves predicting customer churn which means how likely is a customer to stop patronage to a business and switch to its competitor. The second study would involve automatic sentence classification which can be used by reviews sites to detect users sentiments based on their review.

To enable us develop models quickly and test our hypothesis, it is reasonable for us to use TensorFlow’s higher level APIs which are exposed through TFLearn. TFLearn has bundled components which are similar to Scikit-Learn but for building deep neural networks. TFLearn is just a convenience wrapper for TensorFlow’s lower level computation graph components. As such TensorFlow is a dependency for TFLearn, that is to say to use or install TFLearn, you first need to have TensorFlow installed.

Since we have Tensorflow already installed from the previous chapter, we can go ahead to install TFLearn. TFLearn can be installed across the three major operating systems we covered in the last chapter by using Python’s native package manager pip. To install TFLearn we run the following command in a terminal:

 

$ pip install tflearn

Bank Churn Modelling

Here we are presented with a case whereby a bank wants to use data collected from its customers over several years to predict which customers are likely to stop using the bank’s services by switching to a competing bank. The rewards of such an analysis to the bank is profound as it can target dissatisfied customers with incentives which would reduce the churn ratio helping the bank to grow its customer base and solidify its position.

The dataset contains many informative attributes such as account balance, number of products subscribed to, credit card status, estimated customer salary etc. The target variable is whether or not the customer left the bank, so this is a binary classification task. There are also some categorical features such as gender and geography which we would need to transform before feeding them into a neural network.

The churn modelling dataset can be downloaded at:

[https://www.kaggle.com/aakash50897/churn-modellingcsv/data](https://www.kaggle.com/aakash50897/churn-modellingcsv/data)

 

As always we first import all relevant libraries, load the dataset using Pandas and call the head method on the dataset to see what is contained inside.

 

\# import all relevant libraries

import numpy as np

import matplotlib.pyplot as plt

import pandas as pd

import tensorflow as tf

import tflearn

 

\# load the dataset

dataset = pd.read\_csv('Churn\_Modelling.csv')

 

\# get first five rows (observations)

dataset.head()

 

![](images/00120.jpeg)

The dataset contains 14 columns, the first 3 columns are uninformative namely RowNumber, CustomerId and Surname. Those three columns can be seen as identifiers as they do not provide any information which would give insights to whether a customer would stay or leave. They would be removed before we perform analysis. The last column - Exited is the class label which our model would learn to predict.

The next step having gotten an overview of the dataset is to split the columns into features and labels. We do this using Pandas slicing operation which selects information form specified indexes. In our case, features start from the 3rd column and ends in the 12th column. Remember that array indexing starts at 0 not 1.

 

X = dataset.iloc\[:, 3:13\].values

y = dataset.iloc\[:, 13\].values

 

Since we have categorical features in the dataset (Geography and Gender), we have to convert them into a form that a deep learning algorithm can process. We do that using a one-hot representation. One-hot representation creates a sparse matrix with zeros in all positions and a 1 at the position representing the category under evaluation. We use Scikit-Learn’s preprocessing model to first create a label encoder, then create a one-hot representation from it.

 

\# encoding categorical data

from sklearn.preprocessing import LabelEncoder, OneHotEncoder

labelencoder\_X\_1 = LabelEncoder()

X\[:, 1\] = labelencoder\_X\_1.fit\_transform(X\[:, 1\])

labelencoder\_X\_2 = LabelEncoder()

X\[:, 2\] = labelencoder\_X\_2.fit\_transform(X\[:, 2\])

onehotencoder = OneHotEncoder(categorical\_features = \[1\])

X = onehotencoder.fit\_transform(X).toarray()

X = X\[:, 1:\]

 

We split our data into training and test set. One would be used to train the model while the other would be use to test performance.

 

\# spliting the dataset into the training set and test set

from sklearn.model\_selection import train\_test\_split

X\_train, X\_test, y\_train, y\_test = train\_test\_split(X, y, test\_size = 0.2, random\_state = 0)

y\_train = np.reshape(y\_train, (-1, 1)) # reshape y\_train to \[None, 1\]

y\_test = np.reshape(y\_test, (-1, 1)) # reshape y\_test to \[None, 1\]

 

The features as currently contained in X are not in the same scale so we apply standard scaling which makes all features to have a mean of 0 and a standard deviation of 1.

 

\# feature scaling

from sklearn.preprocessing import StandardScaler

sc = StandardScaler()

X\_train = sc.fit\_transform(X\_train)

X\_test = sc.transform(X\_test)

 

We start creating a deep neural network by describing it using TFLearn API.

 

\# build the neural network

net = tflearn.input\_data(shape=\[None, 11\])

net = tflearn.fully\_connected(net, 6, activation='relu')

net = tflearn.dropout(net, 0.5)

net = tflearn.fully\_connected(net, 6, activation='relu')

net = tflearn.dropout(net, 0.5)

net = tflearn.fully\_connected(net, 1, activation='tanh')

net = tflearn.regression(net)

 

The network has 11 input features and there are 3 fully connected layers. We also use dropout as the regularizer in order to prevent the model from overfitting. Next we define the model using DNN from TFLearn.

 

\# define model

model = tflearn.DNN(net)

\# we start training by applying gradient descent algorithm

model.fit(X\_train, y\_train, n\_epoch=10, batch\_size=16, validation\_set=(X\_test, y\_test),

          show\_metric=True, run\_id="dense\_model")

 

![](images/00121.jpeg)

We train the model for 10 epochs with a batch size of 16. The model achieves an accuracy of 0.7885 on the test set which we used to validate the performance of the model.

Sentiment Analysis

For this real world use case we tackle a problem from the field of Natural Language Processing (NLP). The task is to classify movie reviews into classes expressing positive sentiment about a movie or negative sentiment. To perform a task like this, the model must be able to understand natural language, that is it must know the meaning of an entire sentence as expressed by its class prediction. Recurrent Neural Networks (RNNs) are usually well suited for tasks involving sequential data like sentences however, we would apply a 1-dimensional Convolutional Neural Network (CNN) model to this task as it is easier to train and produces comparable results.

The dataset we would use is the IMDB sentiment database which contains 25,000 movie reviews in the training set and 25,000 reviews in the test set. TFLearn bundles this dataset alongside others so we would access it from the datasets module.

 

First we import the IMDB sentiment dataset module and other relevant components from TFLearn such as convolutional layers, fully connected layers, data utilities etc.

 

import tensorflow as tf

import tflearn

from tflearn.layers.core import input\_data, dropout, fully\_connected

from tflearn.layers.conv import conv\_1d, global\_max\_pool

from tflearn.layers.merge\_ops import merge

from tflearn.layers.estimator import regression

from tflearn.data\_utils import to\_categorical, pad\_sequences

from tflearn.datasets import imdb

 

The next step is to actually load the dataset into the train and test splits

 

\# load IMDB dataset

train, test, \_ = imdb.load\_data(path='imdb.pkl', n\_words=10000,

                                valid\_portion=0.1)

trainX, trainY = train

testX, testY = test

 

The next phase involves preprocessing the data where we pad sequences which means we set a maximum sentence length and for sentences less than the maximum sentence length we add zeros to them. The reason is to make sure that all sentences are of the same length before they are passed to the neural network model. The labels in the train and test sets are also converted to categorical values.

 

\# data preprocessing

\# sequence padding

trainX = pad\_sequences(trainX, maxlen=100, value=0.)

testX = pad\_sequences(testX, maxlen=100, value=0.)

\# converting labels to binary vectors

trainY = to\_categorical(trainY, nb\_classes=2)

testY = to\_categorical(testY, nb\_classes=2)

 

As we saw in the previous example, the next step is to describe a 1-dimensional Convolutional Neural  Network model using the building blocks provided to us by TFLearn.

 

\# building the convolutional network

network = input\_data(shape=\[None, 100\], name='input')

network = tflearn.embedding(network, input\_dim=10000, output\_dim=128)

branch1 = conv\_1d(network, 128, 3, padding='valid', activation='relu', regularizer="L2")

branch2 = conv\_1d(network, 128, 4, padding='valid', activation='relu', regularizer="L2")

branch3 = conv\_1d(network, 128, 5, padding='valid', activation='relu', regularizer="L2")

network = merge(\[branch1, branch2, branch3\], mode='concat', axis=1)

network = tf.expand\_dims(network, 2)

network = global\_max\_pool(network)

network = dropout(network, 0.5)

network = fully\_connected(network, 2, activation='softmax')

network = regression(network, optimizer='adam', learning\_rate=0.001,

                     loss='categorical\_crossentropy', name='target')

 

The network contains 3 1-dimensional convolutional layers, a global max pooling layer used to reduce the dimension of convolutions, a dropout layer used for regularization and a fully connected layer. Finally, we declare the model and call fit method on it to begin training.

 

\# training

model = tflearn.DNN(network, tensorboard\_verbose=0)

model.fit(trainX, trainY, n\_epoch=5, shuffle=True, validation\_set=(testX, testY), show\_metric=True, batch\_size=32)

 

![](images/00122.jpeg)

The trained model achieves an accuracy of 0.80 on the test set which is to say it correctly classified the sentiment expressed in 80% of sentences.

Here is the code used for training the model in full:

 

\# import tflearn, layers and data utilties

import tensorflow as tf

import tflearn

from tflearn.layers.core import input\_data, dropout, fully\_connected

from tflearn.layers.conv import conv\_1d, global\_max\_pool

from tflearn.layers.merge\_ops import merge

from tflearn.layers.estimator import regression

from tflearn.data\_utils import to\_categorical, pad\_sequences

from tflearn.datasets import imdb

 

\# load IMDB dataset

train, test, \_ = imdb.load\_data(path='imdb.pkl', n\_words=10000,

                                valid\_portion=0.1)

trainX, trainY = train

testX, testY = test

 

\# data preprocessing

\# sequence padding

trainX = pad\_sequences(trainX, maxlen=100, value=0.)

testX = pad\_sequences(testX, maxlen=100, value=0.)

\# converting labels to binary vectors

trainY = to\_categorical(trainY, nb\_classes=2)

testY = to\_categorical(testY, nb\_classes=2)

 

\# building the convolutional network

network = input\_data(shape=\[None, 100\], name='input')

network = tflearn.embedding(network, input\_dim=10000, output\_dim=128)

branch1 = conv\_1d(network, 128, 3, padding='valid', activation='relu', regularizer="L2")

branch2 = conv\_1d(network, 128, 4, padding='valid', activation='relu', regularizer="L2")

branch3 = conv\_1d(network, 128, 5, padding='valid', activation='relu', regularizer="L2")

network = merge(\[branch1, branch2, branch3\], mode='concat', axis=1)

network = tf.expand\_dims(network, 2)

network = global\_max\_pool(network)

network = dropout(network, 0.5)

network = fully\_connected(network, 2, activation='softmax')

network = regression(network, optimizer='adam', learning\_rate=0.001,

                     loss='categorical\_crossentropy', name='target')

 

\# training

model = tflearn.DNN(network, tensorboard\_verbose=0)

model.fit(trainX, trainY, n\_epoch=5, shuffle=True, validation\_set=(testX, testY), show\_metric=True, batch\_size=32)

 

  

Thank you ! 

Thank you for buying this book! It is intended to help you understanding machine learning using Python. If you enjoyed this book and felt that it added value to your life, we ask that you please take the time to review it.

Your honest feedback would be greatly appreciated. It really does make a difference.

 

![C:\\Users\\CHADAD\\Downloads\\intelligent.png](images/00123.jpeg)

 

We are a very small publishing company and our survival depends on your reviews. Please, take a minute to write us your review.

 

 

 

 

 

  

Sources & References

Software, libraries, & programming language

●    Python ([https://www.python.org/](https://www.python.org/))

●    Anaconda ([https://anaconda.org/](https://anaconda.org/))

●    Virtualenv ([https://virtualenv.pypa.io/en/stable/](https://virtualenv.pypa.io/en/stable/))

●    Numpy ([http://www.numpy.org/](http://www.numpy.org/))

●    Pandas ([https://pandas.pydata.org/](https://pandas.pydata.org/))

●    Matplotlib ([https://matplotlib.org/](https://matplotlib.org/))

●    Scikit-learn ([http://scikit-learn.org/](http://scikit-learn.org/))

●    TensorFlow ([https://www.tensorflow.org/](https://www.tensorflow.org/))

●    TFLearn ([http://tflearn.org/](http://tflearn.org/))

Datasets

●    Kaggle ([https://www.kaggle.com/datasets](https://www.kaggle.com/datasets))

●    Boston Housing Dataset ([https://forge.scilab.org/index.php/p/rdataset/source/file/master/csv/MASS/Boston.csv](https://forge.scilab.org/index.php/p/rdataset/source/file/master/csv/MASS/Boston.csv))

●    Pima Indians Diabetes Database ([https://www.kaggle.com/uciml/pima-indians-diabetes-database/data](https://www.kaggle.com/uciml/pima-indians-diabetes-database/data))

●    Iris Dataset ([https://www.kaggle.com/saurabh00007/iriscsv/downloads/Iris.csv/1](https://www.kaggle.com/saurabh00007/iriscsv/downloads/Iris.csv/1))

●    Bank Churn Modelling ([https://www.kaggle.com/aakash50897/churn-modellingcsv/data](https://www.kaggle.com/aakash50897/churn-modellingcsv/data))

Online books, tutorials, & other references

●    Coursera Deep Learning Specialization ([https://www.coursera.org/specializations/deep-learning](https://www.coursera.org/specializations/deep-learning))

●    fast.ai - Deep Learning for Coders (http://course.fast.ai/)

●    Overfitting ([https://en.wikipedia.org/wiki/Overfitting](https://en.wikipedia.org/wiki/Overfitting))

●    A Neural Network Program ([https://playground.tensorflow.org/](https://playground.tensorflow.org/))

●    TensorFlow Examples ([https://github.com/aymericdamien/TensorFlow-Examples](https://github.com/aymericdamien/TensorFlow-Examples))

●    TFLearn Examples ([https://github.com/tflearn/tflearn/tree/master/examples](https://github.com/tflearn/tflearn/tree/master/examples))

●    Machine Learning Crash Course by Google ([https://playground.tensorflow.org/](https://playground.tensorflow.org/))

●    Choosing the Right Estimator ([http://scikit-learn.org/stable/tutorial/machine\_learning\_map/index.html](http://scikit-learn.org/stable/tutorial/machine_learning_map/index.html))

●    Cross-validation: evaluating estimator performance ([http://scikit-learn.org/stable/modules/cross\_validation.html](http://scikit-learn.org/stable/modules/cross_validation.html))

 

 

 

 

 

 

 

  
Thank you ! 

Thank you for buying this book! It is intended to help you understanding machine learning using Python. If you enjoyed this book and felt that it added value to your life, we ask that you please take the time to review it.

[Your honest feedback would be greatly appreciated. It really does make a difference.](https://www.amazon.com/dp/B07FTPKJMM)

 

![C:\\Users\\CHADAD\\Downloads\\intelligent.png](images/00123.jpeg)

 

[We are a very small publishing company and our survival depends on your reviews. Please, take a minute to write us your review.](https://www.amazon.com/dp/B07F193447)

[https://www.amazon.com/dp/B07FTPKJMM](https://www.amazon.com/dp/B07FTPKJMM)

 

 

 

 

 

 

 

 

 

 

 

 

![C:\\Users\\CHADAD\\Downloads\\intelligent.png](images/00124.jpeg)