   

![](main-1.jpg)

Deep Learning with Python

A Hands-on Introduction

Nikhil Ketkar

![](main-2.jpg)

Deep Learning with Python

A Hands-on Introduction

Nikhil Ketkar

Apress

Deep Learning with Python: A Hands-on Introduction

Nikhil Ketkar

Bangalore, Karnataka, India

ISBN-13 (pbk): 978-1-4842-2765-7            ISBN-13 (electronic): 978-1-4842-2766-4

DOI 10.1007/978-1-4842-2766-4

Library of Congress Control Number: 2017939734

Copyright © 2017 by Nikhil Ketkar

This work is subject to copyright. All rights are reserved by the Publisher, whether the whole or part of the material is concerned, specifically the rights of translation, reprinting, reuse of illustrations, recitation, broadcasting, reproduction on microfilms or in any other physical way, and transmission or information storage and retrieval, electronic adaptation, computer software, or by similar or dissimilar methodology now known or hereafter developed.

Trademarked names, logos, and images may appear in this book. Rather than use a trademark symbol with every occurrence of a trademarked name, logo, or image we use the names, logos, and images only in an editorial fashion and to the benefit of the trademark owner, with no intention of infringement of the trademark.

The use in this publication of trade names, trademarks, service marks, and similar terms, even if they are not identified as such, is not to be taken as an expression of opinion as to whether or not they are subject to proprietary rights.

While the advice and information in this book are believed to be true and accurate at the date of publication, neither the authors nor the editors nor the publisher can accept any legal responsibility for any errors or omissions that may be made. The publisher makes no warranty, express or implied, with respect to the material contained herein.

Managing Director: Welmoed Spahr

Editorial Director: Todd Green

Acquisitions Editor: Celestin Suresh John

Development Editor: Matthew Moodie and Anila Vincent

Technical Reviewer: Jojo Moolayail Coordinating Editor: Prachi Mehta Copy Editor: Larissa Shmailo Compositor: SPi Global Indexer: SPi Global

Artist: SPi Global

Cover image designed by Freepik

Distributed to the book trade worldwide by Springer Science+Business Media New York,

233 Spring Street, 6th Floor, New York, NY 10013. Phone 1-800-SPRINGER, fax (201) 348-4505, e-mail [orders-ny@springer-sbm.com](mailto:orders-ny@springer-sbm.com), or visit [www.springeronline.com](http://www.springeronline.com). Apress Media, LLC is a California LLC and the sole member (owner) is Springer Science + Business Media Finance Inc (SSBM Finance Inc). SSBM Finance Inc is a Delaware corporation.

For information on translations, please e-mail [rights@apress.com](mailto:rights@apress.com), or visit [http://www.apress.com/](http://www.apress.com/rights-permissions) [rights-permissions](http://www.apress.com/rights-permissions).

Apress titles may be purchased in bulk for academic, corporate, or promotional use. eBook versions and licenses are also available for most titles. For more information, reference our Print and eBook Bulk Sales web page at [http://www.apress.com/bulk-sales](http://www.apress.com/bulk-sales).

Any source code or other supplementary material referenced by the author in this book is available to readers on GitHub via the book's product page, located at [www.apress.com/9781484227657](http://www.apress.com/9781484227657). For more detailed information, please visit [http://www.apress.com/source-code](http://www.apress.com/source-code).

Printed on acid-free paper

To Aditi.

*   [Contents at a Glance](#main-1.xhtml)
*   [About the Author](#main-2.xhtml)
*   [About the Technical Reviewer](#main-3.xhtml)
*   [Acknowledgments](#main-4.xhtml) 
    *   [Regularization](#main-5.xhtml)
    *   [Types of Units/Activation Functions/Layers](#main-6.xhtml)
    *   [Summary](#main-7.xhtml)
    *   [Bidirectional RNNs](#main-8.xhtml)
    *   [Summary](#main-9.xhtml)
    *   [Parallel and Distributed SGD](#main-10.xhtml)
    *   [Hands-on Automatic Differentiation with Autograd](#main-11.xhtml)
*   [Index](#main-12.xhtml)

# Contents at a Glance

# Contents

■ Contents

■ Contents

# About the Author

![](main-3.jpg)

Nikhil Ketkar currently leads the Machine Learning Platform team at Flipkart, India's largest e-commerce company. He received his PhD from Washington State University. Following that, he conducted postdoctoral research at University of North Carolina at Charotte, which was followed by a brief stint in high frequency trading at TransMarket in Chicago. More recently, he led the data mining team in Guavus, a startup doing big data analytics in the telecom domain and Indix, a startup doing data science in the e-commerce domain. His research interests include machine learning and graph theory.

# About the Technical Reviewer

Jojo Moolayil is a data scientist and author of Smarter Decisions—The Intersection of Internet of Things and Decision Science. With over four years of industrial experience in data science, decision science, and IoT, he has worked with industry leaders on high-impact and critical projects across multiple verticals. He is currently associated with General Electric, a pioneer and leader in data science for industrial IoT, and lives in Bengaluru, the Silicon Valley of India.

He was born and raised in Pune, India and graduated from the University of Pune with a major in information technology engineering. He started his career with Mu Sigma, the world's largest pure play analytics provider, and worked with the leaders of many Fortune 50 clients. One of the early enthusiasts to venture into IoT analytics, he now focuses on solving decision science problems for industrial IoT use cases. As a part of his role at GE, he also develops data science and decision science products and platforms for industrial IoT.

# Acknowledgments

I would like to thank my colleagues at Flipkart and Indix, and the technical reviewers for their feedback and comments.

CHAPTER 1

Introduction to Deep Learning

![](main-4.png)

This chapter gives a broad overview and a historical context around the subject of deep learning. It also gives the reader a roadmap for navigating the book, the prerequisites, and further reading to dive deeper into the subject matter.

## Historical Context

The field of Artificial Intelligence (AI), which can definitely be considered to be the parent field of deep learning, has a rich history going back to 1950. While we will not cover this history in much detail, we will go over some of the key turning points in the field, which will lead us to deep learning.

Tasks that AI focused on in its early days were tasks that could be easily described formally, like the game of checkers or chess. This notion of being able to easily describe the task formally is at the heart of what can or cannot be done easily by a computer program. For instance, consider the game of chess. The formal description of the game of chess would be the representation of the board, a description of how each of the pieces move, the starting configuration, and a description of the configuration wherein the game terminates.

With these notions formalized, it's relatively easy to model a chess-playing AI program as a search and, given sufficient computational resources, it's possible to produces a relatively good chess-playing AI.

The first era of AI focused on such tasks with a fair amount of success. At the heart of the methodology was a symbolic representation of the domain and the manipulation of symbols based on given rules (with increasingly sophisticated algorithms for searching the solution space to arrive at a solution).

It must be noted that the formal definitions of such rules were done manually. However, such early AI systems were fairly general purpose task/problem solvers in the sense that any problem that could be described formally could be solved with the generic approach.

The key limitation about such systems is that the game of chess is a relatively easy problem for AI simply because the problem setting is relatively simple and can be easily formalized. This is not the case with many of the problems human beings solve on a day-to-day basis (natural intelligence). For instance, consider diagnosing a disease (as a physician does) or transcribing human speech to text. These tasks, like most other tasks human beings master easily, are hard to describe formally and presented a challenge in the early days of AI.

Human beings address such tasks by leveraging a large amount of knowledge about the task/problem domain. Given this observation, subsequent AI systems relied on a large knowledge base which captured the knowledge about the problem/task domain. One point to be noted is the term used here is knowledge, not information or data. By knowledge we simply mean data/information that a program/algorithm can reason about. An example of this could be a graph representation of a map with edges labeled with distances and about traffic (which is being constantly updated), which allows a program to reason about the shortest path between points.

© Nikhil Ketkar 2017

N. Ketkar, Deep Learning with Python, DOI 10.1007/978-1-4842-2766-4\_1

Chapter 1 ■ IntroduCtIon to deep LearnIng

Such knowledge-based systems wherein the knowledge was compiled by experts and represented in a way which allowed algorithms/programs to reason about it represent the second generation of AI. At the heart of such approaches were increasingly sophisticated approaches for representing and reasoning about knowledge to solve tasks/problems which required such knowledge. Examples of such sophistication include the use of first order logic to encode knowledge and probabilistic representations to capture and reason where uncertainty is inherent to the domain.

One of the key challenges that such systems faced and addressed to some extent was the uncertainty inherent in many domains. Human beings are relatively good at reasoning in environments with unknowns and uncertainty. One key observation here is that even the knowledge we hold about a domain is not black or white but gray. A lot of progress was made in this era on representing and reasoning about unknowns and uncertainty. There were some limited successes in tasks like diagnosing a disease, which relied on leveraging and reasoning using a knowledge base in the presence of unknowns and uncertainty.

The key limitation of such systems was the need to hand compile the knowledge about the domain from experts. Collecting, compiling, and maintaining such knowledge bases rendered such systems unpractical. In certain domains, it was extremely hard to even collect and compile such knowledge (for instance, transcribing speech to text or translating documents from one language to another). While human beings can easily learn to do such tasks, it's extremely challenging to hand compile and encode the knowledge related to the tasks (for instance, the knowledge of the English language and grammar, accents, and subject matter).

Human beings address such tasks by acquiring knowledge about a task/problem domain, a process which is referred to as learning. Given this observation, the focus of subsequent work in AI shifted over a decade or two to algorithms that improved their performance based on data provided to them. The focus of this subfield was to develop algorithms that acquired relevant knowledge for a task/problem domain given data. It is important to note that this knowledge acquisition relied on labeled data and a suitable representation of labeled data as defined by a human being.

For instance, consider the problem of diagnosing a disease. For such a task, a human expert would collect a lot of cases where a patient had and did not have the disease in question. Then, the human expert would identify a number of features that would aid making the prediction like, say, the age of the patient, the gender, and results from a number of diagnostic tests like blood pressure, blood sugar, etc. The human expert would compile all this data and represent it in a suitable way like scaling/normalizing the data, etc. Once this data was prepared, a machine learning algorithm can learn how to infer whether the patient has the disease or not by generalizing from the labeled data. Note that the labeled data consisted of patients that both have and do not have the disease. So, in essence, the underlying ML algorithm is essentially doing the job of finding a mathematical function that can produce the right outcome (disease or no disease) given the inputs (features like age, gender, data from diagnostic tests, etc.). Finding the simplest mathematical function that predicts the outputs with required level of accuracy is at the heart of the field of ML. Specific questions like how many examples are required to learn a task or the time complexity of the algorithm, etc., are specific questions on which the field of ML has provided answers with theoretical justification. The field has matured to a point where, given enough data, computer resources, and human resources to engineer features, a large class of problems are solvable.

The key limitation of mainstream ML algorithms is that applying them to a new problem domain requires a massive amount of feature engineering. For instance, consider the problem of recognizing objects in images. Using traditional ML techniques, such a problem will require a massive feature engineering effort wherein experts would identify and generate features which would be used by the ML algorithm. In a sense, the true intelligence is in the identification of features and what the ML algorithm is doing is simply learning how to combine these features to arrive at the correct answer. This identification of features or the representation of data which domain experts do before ML algorithms are applied is both a conceptual and practical bottleneck in AI.

It's a conceptual bottleneck because if features are being identified by domain experts, and the ML algorithm is simply learning to combine and draw conclusions from this, is this really AI? It's a practical bottleneck because the process of building models via traditional ML is bottlenecked by the amount of feature engineering required; there are limits to how much human effort can be thrown at the problem.

Human beings learn concepts starting from raw data. For instance, a child shown a few examples/ instances of a particular animal (like, say, cats) will soon learn to identify cats. The learning process does not involve a parent identifying features like does it have whiskers or does it have fur or does it have a tail. Human learning goes from raw data to a conclusion without the explicit step where features are identified and provided to the learner. In a sense, human beings learn the appropriate representation of data from the data itself. Furthermore, they organize concepts as a hierarchy where complicated concepts are expressed using primitive concepts.

The field of deep learning has its primary focus on learning appropriate representations of data such that these could be used to draw conclusions. The word deep in deep learning refers to the idea of learning the hierarchy of concepts directly from raw data. A more technically appropriate term for deep learning would be representation learning, and a more practical term for the same would be automated feature engineering.

## Advances in Related Fields

It is important to make a note of advances in other fields that have played a key role in the recent interest and success of deep learning. The following points are to be noted.

*   1\. The ability to collect, store, and operate over large amounts of data has greatly advanced over the last decade (for instance, the Apache Hadoop Ecosystem).
    
*   2\. The ability to generate supervised training data (which is basically data with labels—an example of this would be pictures annotated with the objects in the picture) has improved a lot with the availability of crowd-sourcing services (like Amazon Mechanical Turk).
    
*   3\. The massive improvements in computational horsepower brought about by Graphical Processor Units.
    
*   4\. The advances in both theory and software implementation of automatic differentiation (like Theano).
    

While these advancements are peripheral to deep learning, they have played a big role in enabling advances in deep learning.

## Prerequisites

The key prerequisites for reading this book are a working knowledge of Python and some course work on linear algebra, calculus, and probability. It is recommended that readers refer to the following in case they need to cover these prerequisites.

*   1\. Dive Into Python by Mark Pilgrim for Python.
    
*   2\. Linear Algebra by Gilbert Strang for linear algebra.
    
*   3\. Calculus by Gilbert Strang for calculus.
    
*   4\. All of Statistics by Larry Wasserman for probability (Section 1, Chapters [1](http://dx.doi.org/10.1007/978-1-4842-2766-4_1)\-[5](http://dx.doi.org/10.1007/978-1-4842-2766-4_5)).
    

Chapter 1 ■ IntroduCtIon to deep LearnIng

## Overview of Subsequent Chapters

We now provide an overall outline of the subsequent chapters for the reader. It is important to note that each of the chapters covers either the concepts or the skills (or in certain cases both) with respect to deep learning. We highlight these below so that the readers can ensure that they have internalized these concepts and skills. It is highly recommended that the readers not only read the chapters but also work out the mathematical details (using pen and paper) and play with the source code provided in each of the chapters.

*   1\. Chapter [2](http://dx.doi.org/10.1007/978-1-4842-2766-4_2) covers the basics of Machine Learning. The key take home point for this chapter is the concept of generalizing over unseen examples, the ideas of over-fitting and under-fitting the training data, the capacity of the model, and the notion of regularization.
    
*   2\. Chapter [3](http://dx.doi.org/10.1007/978-1-4842-2766-4_3) covers Feed Forward Neural Networks and serves as the conceptual foundation for the entire book. Concepts like the overall structure of the neural network, the input, hidden and output layers, cost functions and their basis on the principle of Maximum Likelihood are the important concepts in this chapter.
    
*   3\. Chapter [4](http://dx.doi.org/10.1007/978-1-4842-2766-4_4) provides a hands-on introduction to the Theano library. It covers how to define networks as computational graphs, automatically derive gradients for complicated networks, and train neural networks.
    
*   4\. Chapter [5](http://dx.doi.org/10.1007/978-1-4842-2766-4_5) covers Convolutional Neural Networks, which are perhaps the most successful application of deep learning.
    
*   5\. Chapter [6](http://dx.doi.org/10.1007/978-1-4842-2766-4_6) covers Recurrent Neural Networks and Long Short Term Memory (LSTM) networks, which are another successful application of deep learning.
    
*   6\. Chapter [7](http://dx.doi.org/10.1007/978-1-4842-2766-4_7) provides a hands-on introduction to the Keras library. The Keras library provides a number of high-level abstractions over the Theano library and is probably the ideal go-to tool when it comes to building deep learning applications.
    
*   7\. Chapter [8](http://dx.doi.org/10.1007/978-1-4842-2766-4_8) introduces the reader to Stochastic Gradient Descent (SGD), which is the most common procedure used to train Neural Networks. This chapter also covers the shortcomings of SGD and a number of variations to SGD that address these shortcomings.
    
*   8\. Chapter [9](http://dx.doi.org/10.1007/978-1-4842-2766-4_9) introduces the reader to Automatic Differentiation (commonly referred to as backpropagation), which is a standard technique used to derive gradients (required for SGD) for arbitrarily complicated networks.
    
*   9\. Chapter [10](http://dx.doi.org/10.1007/978-1-4842-2766-4_10) introduces the reader to Graphical Processing Units (GPUs) and GPU-based computation, which has acted as a key enabling technology for deep learning.
    

## Installing the Required Libraries

There are a number of libraries that the reader will need to install in order to run the source code for the examples in the chapters. We recommend that the reader install Anaconda Python Distribution ([https://www.continuum.io/downloads](https://www.continuum.io/downloads)), which would make the process of installing the required packages significantly easy (using either conda or pip). The list of packages the reader would need includes Scikit-learn, Theano, Autograd, Keras, and PyOpenCL.

CHAPTER 2

Machine Learning Fundamentals

![](main-5.png)

Deep Learning is a branch of Machine Learning and in this chapter we will cover the fundamentals of Machine Learning. While machine learning as a subject is inherently mathematical in nature, we will keep mathematics to the basic minimum required to develop intuition about the subject. Prerequisites for the subject matter covered in this chapter would be linear algebra, multivariable calculus, and basic probability theory.

## Intuition

As human beings we are intuitively aware of the concept of learning: it simply means to get better at a task over a period of time. The task could be physical (like learning to drive a car) or intellectual (like learning a new language). The subject of machine learning focuses on development of algorithms that can learn as humans do; that is, they get better at a task over a period over time, with experience.

The first question to ask is why we would be interested in development of algorithms that improve their performance over time, with experience. After all, there are many algorithms that are developed and implemented to solve real world problems that don't improve over time, they simply are developed by humans and implemented in software and they get the job done. From banking to e-commerce and from navigation systems in our cars to landing a spacecraft on the moon, algorithms are everywhere, and, a majority of them do not improve over time. These algorithms simply perform the task they are intended to perform, with some maintenance required from time to time. Why do we need machine learning?

The answer to this question is that for certain tasks it is easier to develop an algorithm that learns/ improves its performance with experience than to develop an algorithm manually. While this might seem unintuitive to the reader at this point, we will build intuition for this during the course of this chapter.

## Binary Classification

In order to further discuss the matter at hand, we need to be precise about some of the terms we have been intuitively using, like task, learning, experience, and improvement. We will start with the task of binary classification.

Consider an abstract problem domain where we have data of the form

D = {(x[p] y,), (x[v] y[2]), ... X y)}

where x e R" and y = ±1. We do not have access to all such data but only a subset S e D. Using S, our task is to generate a computational procedure that implements the function f:x®y such that we can use f to make predictions over unseen data (x[i],y[t])zS that are correct, f (x[i]) = y[i]. Let us denote UeD as the set of

© Nikhil Ketkar 2017

N. Ketkar, Deep Learning with Python, DOI 10.1007/978-1-4842-2766-4\_2

unseen data, that is, (, y[i]) g S and (, y[i]) e U. We measure performance over this task as the error over unseen data,

We now have a precise definition of the task, which is to categorize data into one of two categories (y = ±1) based on some seen data S by generating f. We measure performance (and improvement in performance) using the error E (f, D, U) over unseen data U. The size of the seen data |S| is the conceptual equivalent of experience. In this context, we want to develop algorithms that generate such functions f (which are commonly referred to as a model). In general, the field of machine learning studies the development of such algorithms that produce models that make predictions over unseen data for such algorithms, and other formal tasks (we will be introducing multiple such tasks later in the chapter). Note that the x is commonly referred to as the input/input variable and y is referred to as the output/output variable.

As with any other discipline in computer science, the computational characteristics of such algorithms is an important facet, but in addition to that we also would like to have a model f that achieves a lower error E (f, D, U) with as small a |S| as possible.

Let us now relate this abstract but precise definition to a real world problem so that our abstractions are grounded. Let us say an e-commerce web site wants to customize the landing page for registered users to show them the products the users might be interested in buying. The web site has historical data on users and would like to implement this as a feature so as to increase sales. Let us now see how this real world problem maps onto the abstract problem of binary classification we described earlier.

The first thing that one might notice is that given a particular user and a particular product, one wants to predict whether the user will buy the product. Since this is the value to be predicted, it maps onto y = ±1, where we will let the value of y = +1 denote the prediction that the user will buy the product and we will denote y = -1 as the prediction that the user does not buy the product. Note that that there is no particular reason for picking these values; we could have swapped this (let y = +1 denote the does not buy case and y = -1 denote the buy case) and there would be no difference. We just use y = ±1 to denote the two classes of interest to categorize data. Next, let us assume that we can somehow represent the attributes of the product and the user's buying and browsing history as x e R". This step is referred to as feature engineering in machine learning and we will cover it later in the chapter. For now, it suffices to say that we are able to generate such a mapping. Thus, we have historical data of what the users browsed and bought, attributes of a product and whether the user bought the product or not mapped onto {(x[p] yj, (x[2],y[2]), ... (x[n],y[n])}. Now, based on this data, we would like to generate a function or a model f:x®y which we can use to determine which products a particular user will buy and use this to populate the landing page for users. We can measure how well the model is doing on unseen data by populating the landing page for users and see whether they buy the products or not and evaluate the error E (f, D, U).

## Regression

Let us introduce another task, namely regression. Here, we have data of the form D = {x[1], y[1] ),(x[2],y[2] )...(x[n] ,y[n] )) where x e R" and y e R and our task is to generate a computational procedure that implements the function f:x®y. Note that instead of the prediction being a binary class label y = ±1 like in binary classification, we have real valued prediction. We measure performance over this task as the root mean squared error (RMSE) over unseen data,

1

(

E (f, D ,U ) =

Z (- f ([t]) )

( St )^U\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

U|

■ Note that the rMse is simply taking the difference between the predicted and actual value, squaring it so as to account for both positive and negative differences, taking the mean so as to aggregate over all the unseen data and, finally, taking the square root so as to counterbalance the square operation.

A real world problem that corresponds to the abstract task of regression is to predict the credit score for an individual based on their financial history, which can be used by a credit card company to extend the line of credit.

## Generalization

Let us now cover what is the single most important intuition in machine leaning, which is that we want to develop/generate models that have good performance over unseen data. In order to do that, let us introduce a toy data set for a regression task first.

We generate the toy dataset by generating 100 values equidistantly between -1 and 1 as the input variable (a). We generate the output variable (y) based on y = 2 + x+2x² + e where e ~N(0,0.1) is noise (random variation) from a normal distribution with 0 mean and 0.1 being the standard deviation. Code for this is presented in Listing [2-1](#main-4.xhtml#bookmark22) and the data is plotted in Figure [2-1](#main-4.xhtml#bookmark23).

Listing 2-1. Generalization vs. Rote Learning

#Generate Toy Dataset

import pylab

import numpy

x = numpy.linspace(-1,1,100) signal = 2 + x + 2 \* x \* x noise = numpy.random.normal(0, 0.1, 100) y = signal + noise pylab.plot(signal,'b');

pylab.plot(y,'g') pylab.plot(noise, 'r') pylab.xlabel("x") pylab.ylabel("y") pylab.legend(\["Without Noise", "With Noise", "Noise"\], loc = 2) x\_train = x\[0:80\] y\_train = y\[0:80\]

\# Model with degree 1 pylab.figure() degree = 2

X\_train = numpy.column\_stack(\[numpy.power(x\_train,i) for i in xrange(0,degree)\]) model = numpy.dot(numpy.dot(numpy.linalg.inv(numpy.dot(X\_train.transpose(),X\_train)),X train.transpose()),y\_train)

pylab.plot(x,y,'g') pylab.xlabel("x") pylab.ylabel("y") predicted = numpy.dot(model, \[numpy.power(x,i) for i in xrange(0,degree)\]) pylab.plot(x, predicted,'r')

pylab.legend(\["Actual", "Predicted"\], loc = 2)

train\_rmse1 = numpy.sqrt(numpy.sum(numpy.dot(y\[0:80\] - predicted\[0:80\], y\_train -predicted\[0:80\])))

test\_rmse1 = numpy.sqrt(numpy.sum(numpy.dot(y\[80:\] - predicted\[80:\], y\[80:\] -predicted\[80:\])))

print("Train RMSE (Degree = 1)", train\_rmse1) print("Test RMSE (Degree = 1)", test\_rmse1)

\# Model with degree 2 pylab.figure() degree = 3

X\_train = numpy.column\_stack(\[numpy.power(x\_train,i) for i in xrange(0,degree)\])

model = numpy.dot(numpy.dot(numpy.linalg.inv(numpy.dot(X\_train.transpose(),X\_train)), X\_train.transpose()),y\_train)

pylab.plot(x,y,'g') pylab.xlabel("x") pylab.ylabel("y") predicted = numpy.dot(model, \[numpy.power(x,i) for i in xrange(0,degree)\]) pylab.plot(x, predicted,'r')

pylab.legend(\["Actual", "Predicted"\], loc = 2) train\_rmse1 = numpy.sqrt(numpy.sum(numpy.dot(y\[0:80\] - predicted\[0:80\], y\_train - predicted\[0:80\])))

test\_rmse1 = numpy.sqrt(numpy.sum(numpy.dot(y\[80:\] - predicted\[80:\], y\[80:\] - predicted\[80:\])))

print("Train RMSE (Degree = 2)", train\_rmse1) print("Test RMSE (Degree = 2)", test\_rmse1)

\# Model with degree 8 pylab.figure() degree = 9

X\_train = numpy.column\_stack(\[numpy.power(x\_train,i) for i in xrange(0,degree)\])

model = numpy.dot(numpy.dot(numpy.linalg.inv(numpy.dot(X\_train.transpose(),X\_train)), X\_train.transpose()), y\_train)

pylab.plot(x, y,'g') pylab.xlabel("x") pylab.ylabel("y")

predicted = numpy.dot(model, \[numpy.power(x,i) for i in xrange(0,degree)\]) pylab.plot(x, predicted,'r')

pylab.legend(\["Actual", "Predicted"\], loc = 3) train\_rmse2 = numpy.sqrt(numpy.sum(numpy.dot(y\[0:80\] - predicted\[0:80\], y\_train - predicted\[0:80\])))

test\_rmse2 = numpy.sqrt(numpy.sum(numpy.dot(y\[80:\] - predicted\[80:\], y\[80:\] - predicted\[80:\])))

print("Train RMSE (Degree = 8)", train\_rmse2) print("Test RMSE (Degree = 8)", test\_rmse2)

\# Output

Train RMSE (Degree = 1) 3.50756834691 Test RMSE (Degree = 1) 7.69514326946

Train RMSE (Degree = 2) 0.91896252959 Test RMSE (Degree = 2) 0.446173435392

Train RMSE (Degree = 8) 0.897346255079 Test RMSE (Degree = 8) 14.1908525449

![](main-6.jpg)

In order to simulate seen and unseen data, we use the first 80 data points as seen data and the rest we treat as unseen data. That is, we build the model using only the first 80 data points and use the rest for evaluating the model.

Next, we use a very simple algorithm to generate a model, commonly referred to as Least Squares. Given a data set of the form D = {{,{[1] ),(x[2],y[2])...(x[n],y[n])) where xeR" and y eR, the least squares model takes the form y = bx where b is a vector such that ||Xb -y||2 is minimized. Here Xis a matrix where each row is an x, thus X e R“^x^n with m being the number of examples (in our case 80). The value of b can be derived using the closed form b\=(X^TX)X^Ty. We are glossing over a lot of important details of the least squares method but those are secondary to the current discussion. The more pertinent detail is how we transform the input variable to a suitable form. In our first model, we will transform x to be a vector of values \[x⁰, x¹, x²\]. That is, if x = 2, it will be transformed to \[1, 2, 4\]. Post this transformation, we can generate a least squares model b using the formula described above. What is happening under the hood is that we are approximating the given data with a second order polynomial (degree = 2) equation, and the least squares algorithm is simply curve fitting or generating the coefficients for each of \[x⁰, x¹, x² \].

We can evaluate the model on the unseen data using the RMSE metric. We can also compute the RMSE metric on the training data. The actual and predicted values are plotted in Figure [2-2](#main-4.xhtml#bookmark24) and listing [2-1](#main-4.xhtml#bookmark22) shows the source code for generating the model.

![](main-7.jpg)

Next, we generate another model with the least squares algorithm but we will transform a to \[a⁰, a¹, a² , a³, a⁴, a⁵, a⁶, a⁷, a⁸\]. That is, we are approximating the given data with a polynomial with degree = 8. The actual and predicted values are plotted in Figure [2-3](#main-4.xhtml#bookmark25) and listing [2-1](#main-4.xhtml#bookmark22) shows the source code for generating the model. As the last step we generate a model with degree = 1.

![](main-8.jpg)

The actual and predicted values are plotted in Figure [2-4](#main-4.xhtml#bookmark26) and listing [2-1 ](#main-4.xhtml#bookmark22)shows the source code for generating the model.

![](main-9.jpg)

Figure 2-4. Actual and predicted values for model with degree = 1

We now have all the details in place to discuss the core concept of generalization. The key question to ask is which is the better model? The one with degree = 2 or the one with degree = 8 or the one with degree = 1?

Let us start by making a few observations about the three models. The model with degree = 1 performs poorly on both the seen as well as unseen data as compared to the other two models. The model with degree = 8 performs better on seen data as compared to the model with degree = 2. The model with degree = 2 performs better than the model with degree = 8 on unseen data. Table [2-1](#main-4.xhtml#bookmark27) visualizes this in table form for easy interpretation.

Table 2-1. Comparing the performance of the 3 different models

 
| Degree || 1 || 2 || 8 |
| --- | --- | --- | --- |
| Seen Data || Worst || Worst || Better |
| Unseen Data || Worst || Better || Worst |

Let us now understand the important concept of model capacity, which corresponds to the degree of the polynomial in this example. The data we generated was using a second order polynomial (degree = 2) with some noise. Then, we tried to approximate the data using three models of degree: 1, 2, and 8, respectively. The higher the degree, the more expressive is the model. That is, it can accommodate more variation. This ability to accommodate variation corresponds to the notion of capacity. That is, we say that the model with degree = 8 has a higher capacity that the model with degree = 2, which in turn has a higher capacity than the model with degree = 1. Isn't having higher capacity always a good thing? It turns out it is not, when we consider that all real world datasets contain some noise and a higher capacity model will end up just fitting the noise in addition to the signal in the data. This is why we observe that the model with degree = 2 does better on the unseen data as compared to the model with degree = 8. In this example, we knew how the data was generated (with a second order polynomial (degree = 2) with some noise); hence, this observation is quite trivial. However, in the real world, we don't know the underlying mechanism by which the data is generated. This leads us to the fundamental challenge in machine learning, which is, does the model truly generalize? And the only true test for that is the performance over unseen data.

In a sense the concept of capacity corresponds to the simplicity or parsimony of the model. A model with high capacity can approximate more complex data. This is how many free variables/coefficients the model has. In our example, the model with degree = 1 does not have capacity sufficient to approximate the data and this is commonly referred to as under fitting. Correspondingly, the model with degree = 8 has extra capacity and it over fits the data.

As a thought experiment, consider what would happen if we had a model with degree equal to 80. Given that we had 80 data points as training data, we would have an 80-degree polynomial that would perfectly approximate the data. This is the ultimate pathological case wherein there is no learning at all. The model has 80 coefficients and can simply memorize the data. This is referred to as rote learning, the logical extreme of overfitting. This is why the capacity of the model needs to be tuned with respect to the amount of training data we have. If the dataset is small, we are better off training models with lower capacity.

## Regularization

Building on the idea of model capacity, generalization, over fitting, and under fitting, let us now cover the idea of regularization. The key idea here is to penalize complexity of the model. A regularized version of least squares takes the form y = ft a, where b is a vector such that ||Xb - y||2 +^||b||2 is minimized and X is a user-defined parameter that controls the complexity. Here, by introducing the term A||b|| 2, we are penalizing complex models. To see why this is the case, consider fitting a least square model using a polynomial of degree 10, but the values in the vector b has 8 zeros; 2 are non-zeros. Against this, consider the case where all values in the vector b are non-zeros. For all practical purposes, the former model is a model with degree = 2 and has a lower value of A||^||2. The A term allows us to balance accuracy over the training data with the complexity of the model. Lower values of A imply a simpler model.

We can compute the value of b using the closed form b\=[(]X^TX\-lI[)]^(\-1)X^Ty. We illustrate keeping the degree fixed at a value of 80 and varying the value of A in listing[ 2-2](#main-5.xhtml#bookmark2).

Listing 2-2. Regularization

import pylab

import numpy

x = numpy.linspace(-1,1,100)

signal = 2 + x + 2 \* x \* x

noise = numpy.random.normal(0, 0.1, 100)

y = signal + noise

x\_train = x\[0:80\]

y\_train = y\[0:80\]

train\_rmse = \[\]

test\_rmse = \[\]

degree = 80 lambda\_reg\_values = numpy.linspace(0.01,0.99,100)

for lambda\_reg in lambda\_reg\_values:

X\_train = numpy.column\_stack(\[numpy.power(x\_train,i) for i in xrange(0,degree)\]) model = numpy.dot(numpy.dot(numpy.linalg.inv(numpy.dot(X\_train.transpose(),X\_train) + lambda\_reg \* numpy.identity(degree)),X\_train.transpose()),y\_train)

predicted = numpy.dot(model, \[numpy.power(x,i) for i in xrange(0,degree)\]) train\_rmse.append(numpy.sqrt(numpy.sum(numpy.dot(y\[0:80\] - predicted\[0:80\], y\_train - predicted\[0:80\]))))

test\_rmse.append(numpy.sqrt(numpy.sum(numpy.dot(y\[80:\] - predicted\[80:\], y\[80:\] - predicted\[80:\]))))

pylab.plot(lambda\_reg\_values, train\_rmse) pylab.plot(lambda\_reg\_values, test\_rmse) pylab.xlabel(r"$\\lambda$") pylab.ylabel("RMSE")

pylab.legend(\["Train", "Test"\], loc = 2)

The training RMSE (seen data) and test RMSE (unseen data) is plotted in Figure [2-5](#main-5.xhtml#bookmark3).

![](main-10.jpg)

Figure 2-5. Regularization

## Summary

In this chapter we covered the basics of Machine Learning. The key take-home points for this chapter are the concepts of generalizing over unseen examples, over-fitting and under-fitting the training data, the capacity of the model, and the notion of regularization. The reader is encouraged to try out the examples (in the source code listings). In the next chapter, we will build on these concepts and cover neural networks.

CHAPTER 3

Feed Forward Neural Networks

![](main-11.png)

In this chapter we will cover some key concepts around feedforward neural networks. These concepts will serve as a foundation as we cover more technical topics in depth.

At an abstract level, a Neural Network can be thought of as a function

f[q]: x ® y, which takes an input x e R" and produces an output y e R", and whose behavior is parameterized by q eR^p. So for instance, f[q] could be simply y = f[q](x)=0-x.

We will start by looking at the structure of a neural network, followed by how they are trained and used for making predictions.

## Unit

A unit is the basic building of a neural network; refer to Figure [3-1](#main-5.xhtml#bookmark9). The following points should be noted:

*   1\.   A unit is a function that takes as input a vector x e R" and produces a scalar.
    
*   2\.  A unit is parameterized by a weight vector w e R" and a bias term denoted by b.
    
*   3\.  The output of the unit can be described as
    

^f \[E^xi ' ^w^+ ^b)

where f :R®R is referred to as an activation function.

*   4\.   A variety of activation functions may be used, as we shall see later in the chapter; generally, it's a non-linear function.
    

© Nikhil Ketkar 2017

N. Ketkar, Deep Learning with Python, DOI 10.1007/978-1-4842-2766-4\_3

 
| XX\\ X || e R^n        input2           %n |
| --- | --- |
|  || / |
| \\wi || w[2].......f^n      ^(Weights) |
|  || j we R^n |
| ■2j> /   \\ || /            Product of Inputs and/                  Weights/      AjJ t¹ft'O' |
| X || \\                          Function |
| /(f>i=l || Outputj • Wj + 6) |

Figure 3-1. A unit in a neural network

### Overall Structure of a Neural Network

Neural Networks are constructed using the unit as a basic building block (introduced earlier); refer to Figure [3-2](#main-5.xhtml#bookmark12).

![](main-12.jpg)

Figure 3-2. Structure of a Neural Network

The following points are to be noted:

*   1\. Units are organized as layers, with every layer containing one or more units.
    
*   2\. The last layer is referred to as the output layer.
    
*   3\. All layers before the output layers are referred to as hidden layers.
    
*   4\. The number of units in a layer is referred to as the width of the layer.
    
*   5\. The width of each layer need not be the same, but the dimension should be aligned, as we shall see later in the chapter.
    
*   6\. The number of layers is referred to as the depth of the network. This is where the notion of deep (as in deep learning) comes from.
    
*   7\. Every layer takes as input the output produced by the previous layer, except for the first layer, which consumes the input.
    
*   8\. The output of the last layer is the output of the network and is the prediction generated based on the input.
    
*   9\. As we have seen earlier, a neural network can be seen as a function f[q] :x® y , which takes as input x e R" and produces as output y e R“ and whose behavior is parameterized by q e R^p. We can now be more precise about 9; it's simply a collection of all the weights w for all the units in the network.
    
*   10\. Designing a neural network involves, amongst other things, defining the overall structure of the network, including the number of layers and the width of these layers.
    

### Expressing the Neural Network in Vector Form

Let us now take a look at the layers of a Neural Network and their dimensions in a bit more detail. Refer to Figure [3-3](#main-5.xhtml#bookmark15); the following points should be noted:

*   1\.  If we assume that the dimensionality of the input is xeR^" and the first layer has p[1 ]units, then each of the units has weR^n weights associated with them. That is, the weights associated with the first layer are a matrix of the form w[1] e R^n^x^P¹. While this is not shown in the diagram, each of the p[1] units also has a bias term associated with it.
    
*   2\.   The first layer produces an output o[1] e R^P¹ where o[i] \= f    x[k] ■ w[k] + b[i]0\. Note
    

that the index kcorresponds to each of the inputs/weights (going from 1 ... n) and the index i corresponds to the units in the first layer (going from 1.. p[1]).

*   3\.   Let us now look at the output of the first layer in a vectorised notation. By vectorised notation we simply mean linear algebraic operations like vector matrix multiplications and computation of the activation function on a vector producing a vector (rather than scalar to scalar). The output of the first layer can be represented as f (x ■w[1] + b[1] )Here we are treating the input x e R" to be of dimensionality 1 x n, the weight matrix w[1] to be of dimensionality n x p[x], and the bias term to be a vector of dimensionality 1 x p[f] Notice then that x ■w[1] + b produces a vector of dimensionality 1 x p[1] and the function f simply transforms each element of the vector to produce o[1]eR^P¹.
    
*   4\.   A similar process follows for the second layer that goes from o[1]eR^(P1) to o[2]eR^P². This can be written in vectorised form as f (o[1] w[2] + b[2] )We can also write the entire computation up to layer 2 in vectorised form as f (f (x ■w[1] + b[1] )-w[2] \+ b[2]).
    
    ![](main-13.jpg)
    
    Figure 3-3. Expressing the Neural Network in Vector Form
    

### Evaluating the output of the Neural Network

Now that we have looked at the structure of a Neural Network, let's look at how the output of the neural network can be evaluated against labeled data. Refer to Figure [3-4](#main-5.xhtml#bookmark18). The following points are to be noted:

*   1\.  We can assume that our data has the form D = {x[p] { {(x[2],y[2] )...(x[n] ,y[n] )) where x e R" and y e{0,1}, which is the target of interest (currently this is binary, but it may be categorical or real valued depending on whether we are dealing with a multi-class or regression problem, respectively).
    
*   2\.  For a single data point we can compute the output of the Neural Network, which we denote as y.
    
*   3\.  Now we need to compute how good the prediction of our Neural Network y is as compared to y. Here comes the notion of a loss function.
    
*   4\.  A loss function measures the disagreement between y and y which we denote by
    

*   l. There are a number of loss functions appropriate for the task at hand: binary classification, multi-classification, or regression, which we shall cover later in the chapter (typically derived using Maximum Likelihood).
    

*   5\.  A loss function typically computes the disagreement between y and y over a number of data points rather than a single data point.
    
    Training Batch
    
    ![](main-14.jpg)
    
    Ky,y)
    
    Neural Network
    
    Cost/Loss
    
    Function
    
    Actual Target Label from Data
    
    \>.\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_J
    
    Figure 3-4. Loss/Cost function and the computation of cost/loss w.r.t, a neural network
    

### Training the Neural Network

Let us now look at how the Neural Network is Trained. Refer to Figure [3-5](#main-5.xhtml#bookmark21). The following points are to be noted:

*   1\.   Assuming the same notation as earlier, we denote by 9 the collection of all the weights and bias terms of all the layers of the network. Let us assume that 9 has been initialized with random values. We denote by f[NN] the overall function representing the Neural Network.
    
*   2\.  As we have seen earlier, we can take a single data point and compute the output of the Neural Network y. We can also compute the disagreement with the actual output y using the loss function l( y, y) that is l(f[NN](x, 9), y).
    
*   3\.  Let us now compute the gradient of this loss function and denote it by
    

^V^Z ( (^(x ,q))y).

*   4\.  We can now update 9 using steepest descent as q[s] =0[s-1] -a-l    (x,q) y)
    

where s denotes a single step (we can take many such steps over different data points in our training set over and over again until we have a reasonably good value for l(f[NN](x, 9), y).

■ Note For now, we will stay away from the computation of gradients of loss functions Vl(f[NN](x,q),y). these can be generated using automatic differentiation (covered elsewhere in the book) quite easily (even for arbitrary complicated loss functions) and need not be derived manually. also, the method of steepest descent and stochastic gradient descent is covered in a separate chapter.

![](main-15.jpg)

Figure 3-5. Training a Neural Network

## Deriving Cost Functions using Maximum Likelihood

We will now look into how loss functions are derived using Maximum Likelihood. Specifically, we will see how commonly used loss functions in deep learning like binary cross entropy, cross entropy, and squared error can be derived using the Maximum Likelihood principle.

### Binary Cross Entropy

Instead of starting with the general idea of Maximum Likelihood, let's directly jump to the binary classification problem. We have some data consisting of D = {x[p]{{(x[2],y[2]),...(x[n],y[n]))where xeR" and y e{0,1}, which is the target of interest (currently this is binary, but it may be categorical or real valued depending on whether we are dealing with a multi-class or regression problem, respectively).

Let us assume that we have somehow generated a model that predicts the probability of y given x. Let us denote this model by f (x, 9) where 9 represents the parameters of the model. The idea behind Maximum Likelihood is to find a 9 that maximizes P (D |q). Assuming a Bernoulli distribution and given that each of the examples {(x[1], y[1]), (x[2], y[2]), . (x[n], y[n])} are independent, we have the following expression:

p (Diq)=n/ ( ,q) ■( - f (^xi ,q))^)

i\=1

We can take a logarithm operation on both sides to arrive at the following:

log P (D |0)=log n f (Xi ,qy-(i - f (Xi q))

i\=i

which simplifies to the expression below:

log P (D\\q) = £ y[t] log f (Xi ,q)+(1 - y[t] )log (1 - f (q)) i\=1

Instead of maximizing the RHS, we minimize its negative value as follows:

^(\- io)g^p (D\\^q)=^(\-)X y[t] ^(lo)g^f (^xi ^,^q)^+0 ^(\-) yi )^(lo)g (i^(\-) ^f (^xi^(,q)) i\=1

This leads us to the binary cross entropy function as below:

^(\-)E yi ^(lo)g^f (^xi ^,^q)^+(^(1 -) yi )^(lo)g (^(\-) ^f (^xi^(,q)) i\=1

The idea of Maximum Likelihood thus allows us to derive the binary cross entropy function which can be used as a loss function in the context of binary classification.

### Cross Entropy

Building on the idea of binary cross entropy, let us now consider deriving the cross entropy loss function to be used in the context of multi-classification. Let us assume in this case that y e   1,..fc}, which are the

k

classes. We also denote n[1],n[2] ■■■n[k] to be the observed counts of each of the k classes. Observe that   n[i] = n.

i\=1

In this case, too, let us assume that we have somehow generated a model that predicts the probability of y given x. Let us denote this model by f (x, 9) where 9 represents the parameters of the model. Let us again use the idea behind Maximum Likelihood, which is to find a 9 that maximizes P (D |q). Assuming a Multinomial distribution and given that each of the examples {(x[1], y[1]), (x[2], y[2]), . (x[n], y[n])} are independent, we have the following expression:

^ni^!\-n[2]l ■■■^nk^!

n f (Xi^(,q))

i=1

We can take a logarithm operation on both sides to arrive at the following:

log P (D |G) = log n! - log nJ. ■ nJ. -n! + log f (x[t],q)

i=1

This can be simplified to the following:

log P (D |0) = log n! - log nJ. ■ nJ. ■■■nk! +£ y[t] log f (x[t] ,0)

i=1

The terms log n ! and log nJ. ■ nJ. ■■■n[k]! are not parameterized by 9 and can be safely ignored as we try to find a 9 that maximizes P(D10). Thus we have the following:

log P (D |0) = £ y[t] log f (Xi ,q)

i\=1

As before, instead of maximizing the RHS we minimize its negative value as follows:

\- logP(D |0) = -£ yi log f (Xi ,q)

i\=1

This leads us to the binary cross entropy function as below:

^(\-)E yi ^(lo)g ^f (^xi^,^q)

i\=1

The idea of Maximum Likelihood thus allows us to derive the cross entropy function, which can be used as a loss function in the context of multi-classification.

### Squared Error

Let us now look into deriving the squared error to be used in the context of regression using Maximum Likelihood. Let us assume in this case that y e R. Unlike the previous cases where we assumed that we had a model that predicted a probability, here we will assume that we have a model that predicts the value of y. To apply the Maximum Likelihood idea, we assume that the difference between the actual y and the predicted y has a Gaussian distribution with zero mean and a variance of a². Then it can be shown that minimizing

L (y \- y )²

i\=1

leads to the minimization of - log P(D |q).

### Summary of Loss Functions

We now summarize three key points with respect to loss functions and the appropriateness of a particular loss function given the problem at hand.

*   1\. The Binary Cross entropy given by the expression
    

^(\-)E yi ^(lo)g^f (x ^,^q)^+(^(1 -) yi )^(lo)g (^(\-) ^f (x^,^q))

i\=1

is the recommended loss function for binary classification. This loss function should typically be used when the Neural Network is designed to predict the probability of the outcome. In such cases, the output layer has a single unit with a suitable sigmoid as the activation function.

*   2\. The Cross entropy function given by the expression
    

^(\-)E yi ^(lo)g^f (x^,^q)

i\=1

is the recommended loss function for multi-classification. This loss function should typically be used with the Neural Network and is designed to predict the probability of the outcomes of each of the classes. In such cases, the output layer has softmax units (one for each class).

^n2

*   3\. The squared loss function given by ^(y -y ) should be used for regression
    

i\=1

problems. The output layer in this case will have a single unit.

## Types of Units/Activation Functions/Layers

We will now look at a number of Units/Activation Functions/Layers commonly used for Neural Networks. Let's start by enumerating a few properties of interest for activation functions.

*   1\.  In theory, when an activation function is non-linear, a two-layer Neural Network can approximate any function (given a sufficient number of units in the hidden layer). Thus, we do seek non-linear activation functions in general.
    
*   2\.   A function that is continuously differentiable allows for gradients to be computed and gradient-based methods to be used for finding the parameters that minimize our loss function over the data. If a function is not continuously differentiable, gradient-based methods cannot make progress.
    
*   3\.   A function whose range is finite (as against infinite) leads to a more stable performance w.r.t gradient-based methods.
    
*   4\.  Smooth functions are preferred (empirical evidence) and Monolithic functions for a single layer lead to convex error surfaces (this is typically not a consideration w.r.t deep learning).
    
*   5\.  Are symmetric around the origin and behave like identity functions near the origin ( f(x)=x).
    

### Linear Unit

The Linear unit is the simplest unit which transforms the input as y\=w.x+b. As the name indicates, the unit does not have a non-linear behavior and is typically used to generate the mean of a conditional Gaussian distribution. Linear units make gradient-based learning a fairly straightforward task.

### Sigmoid Unit

The Sigmoid unit transforms the input as follows:

[y] = 1 ^y = 1 \+ e

The underlying activation function (refer to Figure [3-6](#main-6.xhtml#bookmark6)) is given by

f(x)=

Sigmoid units can be used in the output layer in conjunction with binary cross entropy for binary classification problems. The output of this unit can model a Bernoulli distribution over the output y conditioned over x.

![](main-16.jpg)

### Softmax Layer

The Softmax layer is typically used as an output layer for multi-classification tasks in conjunction with the Cross Entropy loss function. Refer to Figure [3-7](#main-6.xhtml#bookmark9). The Softmax layer normalizes outputs of the previous layer so that they sum up to one. Typically, the units of the previous layer model an un-normalized score of how likely the input is to belong to a particular class. The softmax layer normalized this so that the output represents the probability for every class.

![](main-17.jpg)

### Rectified Linear Unit (ReLU)

Rectified Linear Unit used in conjunction with a linear transformation transforms the input as

f(x)=max(0,wx +b).

The underlying activation function is f(x)=max(0,x); refer to Figure [3-8](#main-6.xhtml#bookmark12). The ReLU unit is more commonly used as a hidden unit in recent times. Results show that ReLU units lead to large and consistent gradients, which helps gradient-based learning.

![](main-18.jpg)

### Hyperbolic Tangent

The Hyperbolic Tangent unit transforms the input (used in conjunction with a linear transformation) as follows:

y = tanh(wx + b).

The underlying activation function (refer to Figure [3-9](#main-6.xhtml#bookmark15)) is given by

f(x)= tanh(x ).

The hyperbolic tangent unit is also commonly used as a hidden unit.

![](main-19.jpg)

Listing 3-1. A 2-Layer Neural Network for Regression

import autograd.numpy as np

import autograd.numpy.random as npr from autograd import grad import sklearn.metrics

import pylab

\# Generate Dataset examples = 1000 features = 100

D = (npr.randn(examples, features), npr.randn(examples))

\# Specify the network layer1\_units = 10 layer2\_units = 1 w1 = npr.rand(features, layer1\_units) b1 = npr.rand(layer1\_units) w2 = npr.rand(layer1\_units, layer2\_units) b2 = 0.0 theta = (w1, b1, w2, b2)

\# Define the loss function

def squared\_loss(y, y\_hat):

return np.dot((y - y\_hat),(y - y\_hat))

\# Output Layer

def binary\_cross\_entropy(y, y\_hat):

return np.sum(-((y \* np.log(y\_hat)) + ((1-y) \* np.log(1 - y\_hat)))) # Wraper around the Neural Network def neural\_network(x, theta):

w1, b1, w2, b2 = theta return np.tanh(np.dot((np.tanh(np.dot(x,w1) + b1)), w2) + b2)

\# Wrapper around the objective function to be optimised def objective(theta, idx):

return squared\_loss(D\[1\]\[idx\], neural\_network(D\[0\]\[idx\], theta))

\# Update def update\_theta(theta, delta, alpha):

w1, b1, w2, b2 = theta w1\_delta, b1\_delta, w2\_delta, b2\_delta = delta

 
| w1\_ || new = w1 || \- alpha || [\*] || w1 || delta |
| --- | --- | --- | --- | --- | --- |
| b1\_ || new = b1 || \- alpha || [\*] || b1 || delta |
| w2\_ || new = w2 || \- alpha || [\*] || w2 || delta |
| b2\_ || new = b2 || \- alpha || [\*] || b2 || delta |

new\_theta = (w1\_new,b1\_new,w2\_new,b2\_new) return new\_theta

\# Compute Gradient grad\_objective = grad(objective)

\# Train the Neural Network

epochs = 10

print "RMSE before training:", sklearn.metrics.mean\_squared\_error(D\[1\],neural\_network(D\[0\], theta)) rmse = \[\]

for i in xrange(0, epochs):

for j in xrange(0, examples):

delta = grad\_objective(theta, j)

theta = update\_theta(theta,delta, 0.01)

rmse.append(sklearn.metrics.mean\_squared\_error(D\[1\],neural\_network(D\[0\], theta)))

print "RMSE after training:", sklearn.metrics.mean\_squared\_error(D\[1\],neural\_network(D\[0\], theta))

pylab.plot(rmse)

pylab.show()

#Output

#RMSE before training: 1.88214665439

#RMSE after training: 0.739508975012

![](main-20.jpg)

Figure 3-10. RMSE over training steps

## Neural Network Hands-on with AutoGrad

We will now build a simple Neural Network from scratch (refer to Listing [3-1](#main-6.xhtml#bookmark16)). The only external library we will be using is Autograd. Autograd is an automatic differentiation library that will allow us to compute gradients for arbitrary functions written with Numpy.

■ Note autograd is covered in more detail in the chapter on automatic differentiation.

## Summary

In this chapter we covered feed forward neural networks, which will serve as the conceptual foundation for the rest of the chapters. The key concepts we covered were the overall structure of the neural network, the input, hidden and output layers, cost functions, and their basis on the principle of Maximum Likelihood. We encourage the reader to try out the example in the source code listing; although it is a toy example, it will help reinforce the concepts. The next chapter will provide a hands-on introduction to the reader on Theano, which will enable the reader to implement full-fledged neural networks.

CHAPTER 4

Introduction to Theano

![](main-21.png)

In this chapter we introduce the reader to Theano, which is a Python library for defining mathematical functions (operating over vectors and matrices), and computing the gradients of these functions. Theano is the foundational layer on which many deep learning packages like Keras are based.

## What is Theano

As we have seen before, building deep learning models fundamentally involves optimizing loss functions using stochastic gradient descent (SGD), requiring the computation of the gradient of loss function. As loss functions in deep learning are complicated, it is not convenient to manually derive such gradients. This is where Theano comes in handy. Theano allows the user to define mathematical expressions that encode loss functions and, once these are defined, Theano allows the user to compute the gradients of these expressions.

A typical workflow for using Theano is as follows:

*   1\. Write symbolic expressions in Python that implement the loss function of the model to be built. This usually amounts to only a few lines of code because of the expressiveness of the Python language and a tight integration with Numpy that allows the user to quickly and elegantly define mathematical expressions involving vectors and matrices.
    
*   2\. Use the symbolic/automatic differentiation capabilities in Theano to generate an expression that produces the gradient of the loss function.
    
*   3\. Pass this gradient function as a parameter to a SGD optimization routine to optimize the loss function.
    

Theano allows a user to focus on the model rather than on the mechanics of deriving the gradient. The specific capabilities of Theano that make it a great toolbox for building deep learning models are as follows:

*   1\. a very seamless integration with Numpy that allows the user to use Numpy objects (vectors and matrices) in the definition of loss functions
    
*   2\. Theano can generate optimized code for both CPU as well as GPU under the hood without the user having to rewrite the code, which defines the loss function.
    
*   3\. optimized automatic/symbolic differentiation
    
*   4\. numerical stability for the generated code via automatic/symbolic differentiation
    

© Nikhil Ketkar 2017

N. Ketkar, Deep Learning with Python, DOI 10.1007/978-1-4842-2766-4\_4

## Theano Hands-On

Let us now start getting our hands dirty with Theano. We will start with simple examples, which will serve as conceptual building blocks for more complicated examples. It is recommended that the reader go over the source code listing and corresponding computational graph for each example and give careful consideration to how the source code translates to the computational graph.

In our first example in Listing [4-1](#main-6.xhtml#bookmark26) (and the corresponding computational graph in Figure [4-1](#main-6.xhtml#bookmark27)) we will define a simple function with scalars. The reader should note the following:

*   1\. Scalars are defined before they can be used in a mathematical expression.
    
*   2\. Every scalar is given a unique name.
    
*   3\. Once defined, the scalar can be operated upon with operations like +, -, \* and /.
    
*   4\. The function construct in Theano allows one to relate inputs and outputs. So, in the example from Listing [4-1](#main-6.xhtml#bookmark26), we have defined a function with the name g, which takes a, b, c, d, and e as input and produces f as the output.
    
*   5\. We can now compute the result of the function g given the input and check that it evaluates exactly as the non-Theano expression.
    
*   6\. While this seems like a trivial example, the non-trivial bit is that now we will be able to easily compute the gradient of such a function g quite easily using Theano, as we will see soon.
    

Listing 4-1. Functions with Scalars import theano.tensor as T from theano import function a = T.dscalar('a') b = T.dscalar('b') c = T.dscalar('c') d = T.dscalar('d') e = T.dscalar('e')

f = ((a - b + c) \* d )/e

g = function(\[a,

b, c, d, e\], f)

print "Expected: ((1 - 2

print "Via Theano: ((1 -

\+ 3) \* 4)/5.0 = ", ((1 - 2 + 3) \* 4)/5.0

2 + 3) \* 4)/5.0 = ", g(1, 2, 3, 4, 5)

\# Expected: ((1 -

\# Via Theano: ((1

2 + 3) \* 4)/5.0 =

\- 2 + 3) \* 4)/5.0

1.6

\= 1.6

![](main-22.jpg)

Figure 4-1. Functions with scalars

In our second example in Listing [4-2](#main-6.xhtml#bookmark28) (and the corresponding computational graph in Figure [4-2](#main-6.xhtml#bookmark29)) we will define a simple function with vectors. The reader should note the following:

*   1\. Vectors/Matrices are defined before they can be used in a mathematical expression.
    
*   2\. Every Vector/Matrix is given a unique name.
    
*   3\. The dimensions of the Vectors/Matrices are not specified.
    
*   4\. Once Vectors/Matrices are defined, the user can define operations like matrix addition, subtraction, and multiplication. The user should take care that vector/ matrix operations respect the intended dimensionality.
    
*   5\. As before, the user can define a function based on the defined expressions. In this case we define a function f that takes a, b, c, and d as input and produces e as output.
    
*   6\. The use can pass Numpy arrays to the function and compute the output. The user should take care that vector/matrix inputs respect the intended dimensionality.
    

Listing 4-2. Functions with Vectors

import numpy

import theano.tensor as T from theano import function

a = T.dmatrix('a')

b = T.dmatrix('b')

c = T.dmatrix('c')

d = T.dmatrix('d')

e = (a + b - c) \* d

f = function(\[a,b,c,d\], e)

a\_data = numpy.array(\[\[1,1\],\[1,1\]\]) b\_data = numpy.array(\[\[2,2\],\[2,2\]\]) c\_data = numpy.array(\[\[5,5\],\[5,5\]\]) d\_data = numpy.array(\[\[3,3\],\[3,3\]\]) print "Expected:", (a\_data + b\_data - c\_data) \* d\_data print "Via Theano:", f(a\_data,b\_data,c\_data,d\_data) # Expected: \[\[-6 -6\]

\# \[-6 -6\]\]

\# Via Theano: \[\[-6. -6.\]

\# \[-6. -6.\]\]

![](main-23.jpg)

Figure 4-2. Functions with Vectors

In our next example in Listing [4-3](#main-6.xhtml#bookmark30) (and the corresponding computational graph in Figure [4-3](#main-6.xhtml#bookmark31)) we will define a function with both scalars and vectors. The reader should note the following:

*   1\. Scalars and vectors/matrices can be used together in expressions.
    
*   2\. The user needs to take care that vector/matrices respect the dimensionality both while defining the expressions as well as passing inputs to the expressions.
    

Listing 4-3. Functions with Scalars and Vectors import numpy

import theano.tensor as T

from theano import function

a = T.dmatrix('a')

b = T.dmatrix('b')

c = T.dmatrix('c')

d = T.dmatrix('d')

p = T.dscalar('p')

q = T.dscalar('q')

r = T.dscalar('r')

s = T.dscalar('s')

u = T.dscalar('u')

e = (((a \* p) + (b - q) - (c + r )) \* d/s) \* u

f = function(\[a,b,c,d,p,q,r,s,u\], e)

a\_data = numpy.array(\[\[1,1\],\[1,1\]\])

b\_data = numpy.array(\[\[2,2\],\[2,2\]\])

c\_data = numpy.array(\[\[5,5\],\[5,5\]\])

d\_data = numpy.array(\[\[3,3\],\[3,3\]\]) print "Expected:", (((a\_data \* 1.0) + (b\_data - 2.0) - (c\_data + 3.0 )) \* d\_data/4.0) \* 5.0 print "Via Theano:", f(a\_data,b\_data,c\_data,d\_data,1,2,3,4,5) # Expected: \[\[-26.25 -26.25\]

\# \[-26.25 -26.25\]\]

\# Via Theano: \[\[-26.25 -26.25\]

\# \[-26.25 -26.25\]\]

![](main-24.jpg)

Ucbv wl) pel UmiM. CTrw.Trw))

~\*\*’\*1^(\_)  ««nuMC<Co^>r»fc{«(«(O • il) ♦ «2 - □» - M ♦ iS»

Figure 4-3. Functions with Scalars and Vectors

In our next example in Listing [4-4](#main-6.xhtml#bookmark32) (and the corresponding computational graph in Figure [4-4](#main-6.xhtml#bookmark33)) we will define a few activation functions with Theano. The nnet package in Theano defines a number of common activation functions.

Listing 4-4. Activiation Functions

import theano.tensor as T

from theano import function

\# sigmoid

a = T.dmatrix('a')

f\_a = T.nnet.sigmoid(a)

f\_sigmoid = function(\[a\],\[f\_a\])

print "sigmoid:", f\_sigmoid(\[\[-1,0,1\]\])

\# tanh

b = T.dmatrix('b')

f\_b = T.tanh(b)

f\_tanh = function(\[b\],\[f\_b\])

print "tanh:", f\_tanh(\[\[-1,0,1\]\])

\# fast sigmoid

c = T.dmatrix('c')

f\_c = T.nnet.ultra\_fast\_sigmoid(c) f\_fast\_sigmoid = function(\[c\],\[f\_c\])

print "fast sigmoid:", f\_fast\_sigmoid(\[\[-1,0,1\]\])

\# softplus

d = T.dmatrix('d')

f\_d = T.nnet.softplus(d)

f\_softplus = function(\[d\],\[f\_d\])

print "soft plus:",f\_softplus(\[\[-1,0,1\]\])

\# relu

e = T.dmatrix('e')

f\_e = T.nnet.relu(e)

f\_relu = function(\[e\],\[f\_e\])

print "relu:",f\_relu(\[\[-1,0,1\]\])

\# softmax

f = T.dmatrix('f')

f\_f = T.nnet.softmax(f)

f\_softmax = function(\[f\],\[f\_f\])

print "soft max:",f\_softmax(\[\[-1,0,1\]\])

![](main-25.jpg)

lgmoid

Elcmwise{tanhjio\_inplace}

ultra\_fast\_sigmoid

Softmax

Elemwise{Composite{(iO \* (i 1 + Abs(il)))}}

val=|| 0.5\]\] TensorType(float64. (True. True))

TensorTv pe( float64. matrix)

Tensor Iy pe(float64. matrix)

TensorType(Iloat64, matrix)

TensorTypetfloat64, matrix)

TensorType(lloat64. matrix)

TensorType(float64, matrix)

softplus

Figure 4-4. Activation Functions

In our next example in Listing [4-5](#main-6.xhtml#bookmark34) (and the corresponding computational graph in Figure [4-5](#main-6.xhtml#bookmark35)) we will define a function with internal state. The reader should note the following:

1\. All models (deep learning or otherwise) will involve defining functions with internal state, which will typically be weights that need to be learned or fitted.

*   2\. A shared variable is defined using the shared construct in Theano.
    
*   3\. A shared variable can be initialized with Numpy constructs.
    
*   4\. Once the shared variable is defined and initialized, it can be used in the definition of expressions and functions in a manner similar to scalars and vectors/matrices, as we have seen earlier.
    
*   5\. A user can get the value of the shared variable using the get\_value method.
    
*   6\. A user can set the value for the shared variable using the set\_value method.
    
*   7\. A function defined using the shared variable computes its output based on the current value of the shared variable. That is, as soon as the shared variable updates, a function defined using the shared variable will produce a different value for the same input.
    
*   8\. A shared variable allows a user to define a function with internal state, which can be updated arbitrarily without needing to redefine the function defined using the shared variable.
    

Listing 4-5. Shared Variables

import theano.tensor as T

from theano import function

from theano import shared

import numpy

x = T.dmatrix('x')

y = shared(numpy.array(\[\[4, 5, 6\]\]))

z = x + y

f = function(inputs = \[x\], outputs = \[z\])

print "Original Shared Value:", y.get\_value() print "Original Function Evaluation:", f(\[\[1, 2, 3\]\])

y.set\_value(numpy.array(\[\[5, 6, 7\]\]))

print "Original Shared Value:", y.get\_value() print "Original Function Evaluation:", f(\[\[1, 2, 3\]\])

\# Couldn't import dot\_parser, loading of dot files will not be possible.

\# Original Shared Value: \[\[4 5 6\]\]

\# Original Function Evaluation: \[array(\[\[ 5., 7., 9.\]\])\]

\# Original Shared Value: \[\[5 6 7\]\]

\# Original Function Evaluation: \[array(\[\[ 6., 8., 10.\]\])\]

![](main-26.jpg)

Figure 4-5. Shared Variables

In our next example in Listing [4-6](#main-6.xhtml#bookmark36) (and the corresponding computational graph in Figure [4-6](#main-6.xhtml#bookmark37)) we will define a function and generate a function that computes its gradient. The reader should note the following:

1\. A function needs to be defined using expressions before the gradient of the function can be generated.

2\. The grad construct in Theano allows the user to generate the gradient of a function (as an expression). Users can then define a function over the expression, which gives them the gradient function.

*   3\. Gradients can be computed for any set of expressions/functions as in the earlier examples. So, for instance, we could generate gradients for functions with a shared state. As the shared state updates, so do the function and the gradient function.
    

Listing 4-6. Gradients

import theano.tensor as T from theano import function from theano import shared

import numpy

x = T.dmatrix('x')

y = shared(numpy.array(\[\[4, 5, 6\]\]))

z = T.sum(((x \* x) + y) \* x)

f = function(inputs = \[x\], outputs = \[z\])

g = T.grad(z,\[x\]) g\_f = function(\[x\], g) print "Original:", f(\[\[1, 2, 3\]\])

print "Original Gradient:", g\_f(\[\[1, 2, 3\]\]) y.set\_value(numpy.array(\[\[1, 1, 1\]\]))

print "Updated:", f(\[\[1, 2, 3\]\])

print "Updated Gradient", g\_f(\[\[1, 2, 3\]\]) # Original: \[array(68.0)\]

\# Original Gradient: \[array(\[\[ 7., 17., 33.\]\])\]

\# Updated: \[array(42.0)\]

\# Updated Gradient \[array(\[\[ 4., 13., 28.\]\])\]

![](main-27.jpg)

Figure 4-6. Computing Gradients

In our next example in Listing [4-7](#main-6.xhtml#bookmark38) (and the corresponding computational graph in Figure [4-7 (a)](#main-6.xhtml#bookmark39) and Figure [4-7 (b)](#main-6.xhtml#bookmark40)) we will define a few loss functions using Theano. The nnet package in Theano implements many standard loss functions.

Listing 4-7. Loss Functions import theano.tensor as T from theano import function

\# binary cross entropy a1 = T.dmatrix('a1') a2 = T.dmatrix('a2') f\_a = T.nnet.binary\_crossentropy(a1, a2).mean() f\_sigmoid = function(\[a1, a2\],\[f\_a\]) print "Binary Cross Entropy \[\[0.01,0.01,0.01\]\],\[\[0.99,0.99,0.01\]\]:", f\_sigmoid(\[\[0.01,0.01,0.01\]\],\[\[0.99,0.99,0.01\]\])

\# categorical cross entropy

b1 = T.dmatrix('b1')

b2 = T.dmatrix('b2')

f\_b = T.nnet.categorical\_crossentropy(b1, b2) f\_sigmoid = function(\[b1, b2\],\[f\_b\]) print "Categorical Cross Entropy \[\[0.01,0.01,0.01\]\],\[\[0.99,0.99,0.01\]\]:", f\_sigmoid(\[\[0.01,0.01,0.01\]\],\[\[0.99,0.99,0.01\]\])

\# squared error

def squared\_error(x,y):

return (x - y) \*\* 2

c1 = T.dmatrix('b1')

c2 = T.dmatrix('b2')

f\_c = squared\_error(c1, c2) f\_squared\_error = function(\[c1, c2\],\[f\_c\]) print "Squared Error \[\[0.01,0.01,0.01\]\],\[\[0.99,0.99,0.01\]\]:", f\_sigmoid(\[\[0.01,0.01,0.01\]\],\[\[0.99,0.99,0.01\]\]) # Binary Cross Entropy \[\[0.01,0.01,0.01\]\],\[\[0.99,0.99,0.01\]\]: \[array(3.058146503109446)\]

\# Categorical Cross Entropy \[\[0.01,0.01,0.01\]\],\[\[0.99,0.99,0.01\]\]: \[array(\[ 9.16428867\])\]

\# Squared Error \[\[0.01,0.01,0.01\]\],\[\[0.99,0.99,0.01\]\]: \[array(\[ 9.16428867\])\]

![](main-28.jpg)

IcnsorTypctfloat64. matrix)

TcnsorTypct int64. scalaryO TcnsorTypct int64. scalar)

MakcVector{dtype=\*int64\*}

rensorType(int64. vector)

Elemwise{Cast{ float64}}

Subtensor {inl64}

Subtensor{int64} id=7

Elcmwisc{Compositc{(((-iO) / i 1) / i 2) > } | (0.0)\]

Elcmwisc{ Composite {((iO • log(il)) + ((i2 - iOl \* Iog((i2 \* il))))}}

TcnsorTypc(float64. scalar) S\\ TcnsorTypct floal64. scalar)

.0 TensorTypc(float64. scalar III /0 Tenso<Type(float64. vector) V) TensorType(float64, sector)S\\

Figure 4-7 (a). Loss Functions - Binary Cross Entropy

 
| al ||  || val=|\[ 1.\]\] TcnsorTypct Hoat64. {True. True)) ||  || a2 |
| --- | --- | --- | --- | --- |

![](main-29.jpg)

Elemwise{Composite{(iO \* log(il))}}

Elemwise{Neg}\[(0,0)\]

rensorTypc(float64, matrix)

\_

Elemwise{Composite{sqr((iO - il))}}

TensorType) float64, matrix)

TensorType(float64, vector)

TensorType(float64, vector)

Figure 4-7 (b). Loss Functions - Categorical Cross Entropy and Squared Error

In our next example in Listing [4-8](#main-6.xhtml#bookmark41) (and corresponding computational graph in Figure [4-8](#main-6.xhtml#bookmark42)) we will define L1 and L2 regularization using Theano.

Listing 4-8. Regularization

import theano.tensor as T from theano import function

\# L1 Regularization def l1(x):

return T.sum(abs(x))

\# L2 Regularization def l2(x):

return T.sum(x\*\*2)

a = T.dmatrix('a') f\_a = l1(a) f\_l1 = function(\[a\], f\_a) print "L1 Regularization:", f\_l1(\[\[0,1,3\]\])

b = T.dmatrix('b') f\_b = l2(b) f\_l2 = function(\[b\], f\_b) print "L2 Regularization:", f\_l2(\[\[0,1,3\]\])

\# L1 Regularization: 4.0

\# L2 Regularization: 10.0

![](main-30.jpg)

Figure 4-8. Regularization

In our next example in Listing [4-9](#main-6.xhtml#bookmark43) (and corresponding computational graph in Figure [4-9](#main-6.xhtml#bookmark44)) we will define a function with a random variable. The reader should note the following:

*   1\. There are cases/situations where we want to define functions having a random variable (for instance introducing minor corruptions in inputs).
    
*   2\. Such a random element in the function is different from having an internal state, like in the case of shared variables.
    
*   3\. Basically, the desired outcome in such cases/situations is that the user wants to define a function with a random variable with a particular distribution.
    
*   4\. Theano provides a construct called RandomStreams, which allows the user to define functions with a random variable. RandomStreams is initialized with a seed.
    
*   5\. The user defines a variable using RandomStreams and specifies a distribution by calling the appropriate function (in our case, normal).
    
*   6\. Once defined, the random variable can be used in the definition of expression or functions in a manner similar to scalars and vectors/matrices.
    
*   7\. Every invocation of the function defined with a random variable will internally draw a sample point from the set distribution (in our case, normal).
    

Listing 4-9. Random Streams

import theano.tensor as T

from theano import function

from theano.tensor.shared\_randomstreams import RandomStreams import numpy

random = RandomStreams(seed=42)

a = random.normal((1,3))

b = T.dmatrix('a')

f1 = a \* b

g1 = function(\[b\], f1)

print "Invocation 1:",

print "Invocation 2:",

print "Invocation 3:",

g1(numpy.ones((1,3)))

g1(numpy.ones((1,3)))

g1(numpy.ones((1,3)))

\# Invocation 1:

\# Invocation 2:

\# Invocation 3:

\[\[ 1.25614218

\[\[ 0.66992188

\[\[ 0.0724739

\-0.53793023

\-0.70813926

\-0.66508406

\-0.10434045\]\]

0.99601177\]\]

0.93707751\]\]

![](main-31.jpg)

Figure 4-9. Random Streams

In our next example in Listing [4-10](#main-6.xhtml#bookmark45) (and corresponding computational graph in Figure [4-10](#main-6.xhtml#bookmark46)) we will build a model for Logistic regression. The reader should note the following:

*   1\. The example generates some artificial/toy data, fits a logistic regression model and computes the accuracy before and after training. This is a toy dataset for the purposes of illustration; the model is not generalizing/learning, as the data is generated randomly.
    
*   2\. We define a function to compute L2 regularization as covered in listing [4-8](#main-6.xhtml#bookmark41) earlier.
    
*   3\. We generate input data, which consists of 1000 vectors of dimensionality 100. Basically, 1000 examples with 100 features.
    
*   4\. We generate random target/output labels as zeros and ones.
    
*   5\. We define the expressions for logistic regression involving the data (denoted by x), the outputs (denoted by y), the bias term (denoted by b), and the weight vector (denoted by w). The weight vector and the bias term are shared variables.
    
*   6\. We compute the prediction, the error, and the loss using binary cross entropy as introduced in listing [4-7](#main-6.xhtml#bookmark38) earlier.
    
*   7\. Having defined these expressions, we can now use the grad construct in Theano (introduced in listing ([4-6](#main-6.xhtml#bookmark36))) to compute the gradient.
    
*   8\. We define a train function based on the gradient function. The train function defines the inputs, outputs, and how the internal state (shared variables) are to be updated.
    
*   9\. The train function is invoked for 1000 steps; in each step the gradient is computed internally and the shared variables are updated.
    
*   10\. Accuracy is computed before and after the training steps using sklearn.metrics
    

Listing 4-10. Logistic Regression

import numpy

import theano

import theano.tensor as T

import sklearn.metrics

def l2(x):

return T.sum(x\*\*2)

examples = 1000

features = 100

D = (numpy.random.randn(examples, features), numpy.random.randint(size=examples, low=0, high=2)) training\_steps = 1000

x = T.dmatrix("x")

y = T.dvector("y")

w = theano.shared(numpy.random.randn(features), name="w")

b = theano.shared(0., name="b")

p = 1 / (1 + T.exp(-T.dot(x, w) - b))

error = T.nnet.binary\_crossentropy(p,y)

loss = error.mean() + 0.01 \* l2(w)

prediction = p > 0.5

gw, gb = T.grad(loss, \[w, b\])

train = theano.function(inputs=\[x,y\],outputs=\[p, error\], updates=((w, w - 0.1 \* gw), (b, b - 0.1 \* gb)))

predict = theano.function(inputs=\[x\], outputs=prediction)

print "Accuracy before Training:",sklearn.metrics.accuracy\_score(D\[1\], predict(D\[0\])) for i in range(training\_steps):

prediction, error = train(D\[0\], D\[1\])

print "Accuracy before Training:", sklearn.metrics.accuracy\_score(D\[1\], predict(D\[0\]))

\# Accuracy before Training: 0.481

\# Accuracy before Training: 0.629

![](main-32.jpg)

'Ten'iorType(in(64. scalar)

AllocEmpty{dtype='float64'}

J) Tensor!^-pc(float64. vector)

val»( 03\] TensorType(float32. (True.))

InplaceDimShufflefx)

() TenMxl\\pe(float64. vector)

TensorType(floal64. (True.))

Elcmwisc(Compositc{GT(scalar\_sigmoid((-((-iO) - il))). i2)}}

TensorType(int8. vector)

Figure 4-10. Logistic Regression

 
| val=l .0 TensocType( float 64. scalar) ||  || w ||  || va 1=0.0 TensorType(float64. scalar) ||  || b |
| --- | --- | --- | --- | --- | --- | --- |

In our next example in Listing [4-11](#main-6.xhtml#bookmark47) (and corresponding computational graph in Figure [4-11](#main-6.xhtml#bookmark48)) we will build a model for Linear regression. The reader should note the following:

*   1\. The example generates some artificial/toy data, fits a linear regression model and computes the accuracy before and after training. This is a toy dataset for the purposes of illustration, the model is not generalizing/learning as the data is generated randomly.
    
*   2\. We define a function to compute L2 regularization as covered in listing [4-8](#main-6.xhtml#bookmark41) earlier.
    
*   3\. We define a function for squared error as covered in listing [4-7](#main-6.xhtml#bookmark38).
    
*   4\. We generate input data, which consists of 1000 vectors of dimensionality 100. Basically, 1000 examples with 100 features.
    
*   5\. We generate random target/output labels values between 0 and 1.
    
*   6\. We define the expressions for linear regression involving the data (denoted by x), the outputs (denoted by y), the bias term (denoted by b) and the weight vector (denoted by w). The weight vector and the bias term are shared variables.
    
*   7\. We compute the prediction, the error and the loss using squared error as introduced in listing [4-7](#main-6.xhtml#bookmark38) earlier.
    
*   8\. Having defined these expressions, we can now use the grad construct in Theano (introduced in listing ([4-6](#main-6.xhtml#bookmark36)) to compute the gradient.
    
*   9\. We define a train function based on the gradient function. The train function defines the inputs, outputs and how the internal state (shared variables) are to be updated.
    
*   10\. The train function is invoked for a 1000 steps, in each step the gradient is computed internally and the shared variables are updated.
    
*   11\. Root mean squared error (RMSE) is computed before and after the training steps using sklearn.metrics
    

Listing 4-11. Linear Regression

import numpy

import theano

import theano.tensor as T

import sklearn.metrics

def l2(x):

return T.sum(x\*\*2)

def squared\_error(x,y):

return (x - y) \*\* 2

examples = 1000

features = 100

D = (numpy.random.randn(examples, features), numpy.random.randn(examples)) training\_steps = 1000

x = T.dmatrix("x")

y = T.dvector("y")

w = theano.shared(numpy.random.randn(features), name="w")

b = theano.shared(0., name="b")

p = T.dot(x, w) + b

error = squared\_error(p,y)

loss = error.mean() + 0.01 \* l2(w)

gw, gb = T.grad(loss, \[w, b\])

train = theano.function(inputs=\[x,y\],outputs=\[p, error\], updates=((w, w - 0.1 \* gw), (b, b - 0.1 \* gb)))

predict = theano.function(inputs=\[x\], outputs=p)

print "RMSE before training:", sklearn.metrics.mean\_squared\_error(D\[1\],predict(D\[0\]))

for i in range(training\_steps):

prediction, error = train(D\[0\], D\[1\])

print "RMSE after training:", sklearn.metrics.mean\_squared\_error(D\[1\],predict(D\[0\]))

\# RMSE before training: 90.4707491496

\# RMSE after training: 0.915701676631

![](main-33.jpg)

rensorType(int64. scalar) \\2

AllocEmpty {dty pc«’float64'}

CGcmv {inplace}

InplaceDimShuf lie {x}

Elcmwisc{ Add} |(0,0)\]

7----

\\0 TensorT\\pe(float64. vector)

val« 1.0 Tensoriy pe(float64. scalar)

0TensorType(floai64. vector)

TensorTypei Iloal64. < True.))

TensorTy pet float64, vector)

vaMJjO TensorType(floai64. scalar) 1^

T

Figure 4-11. Linear Regression

In our next example in Listing [4-12](#main-6.xhtml#bookmark49) (and corresponding computational graph in Figure [4-12](#main-6.xhtml#bookmark50)) we will build a neural network model with 2 layers. The reader should note the following:

*   1\. The example generates some artificial/toy data, fits a logistic regression model and computes the accuracy before and after training. This is a toy dataset for the purposes of illustration; the model is not generalizing/learning, as the data is generated randomly.
    
*   2\. We define a function to compute L2 regularization as covered in listing [4-8](#main-6.xhtml#bookmark41) earlier.
    
*   3\. We generate input data, which consists of 1000 vectors of dimensionality 100. Basically, 1000 examples with 100 features.
    
*   4\. We generate random target/output labels as zeros and ones.
    
*   5\. We define the expressions for the 2-layer neural network involving the data (denoted by x), the outputs (denoted by y), the bias term of the first layer (denoted by b1), the weight vector of the first layer (denoted by w1), the bias term of the second layer (denoted by b2), and, the weight vector of the second layer (denoted by w2). The weight vectors and the bias terms are shared variables.
    
*   6\. We use the tanh activation function as covered in listing [4-4](#main-6.xhtml#bookmark32) to encode the neural network.
    
*   7\. We compute the prediction, the error, and the loss using binary cross entropy as introduced in listing [4-7](#main-6.xhtml#bookmark38) earlier.
    
*   8\. Having defined these expressions, we can now use the grad construct in Theano (introduced in listing ([4-6](#main-6.xhtml#bookmark36))) to compute the gradient.
    
*   9\. We define a train function based on the gradient function. The train function defines the inputs, outputs, and how the internal state (shared variables) are to be updated.
    
*   10\. The train function is invoked for 1000 steps; in each step the gradient is computed internally and the shared variables are updated.
    
*   11\. Accuracy is computed before and after the training steps using sklearn.metrics
    

Listing 4-12. Neural Network

import numpy

import theano

import theano.tensor as T

import sklearn.metrics

def l2(x):

return T.sum(x\*\*2)

examples = 1000

features = 100

hidden = 10

D = (numpy.random.randn(examples, features), numpy.random.randint(size=examples, low=0, high=2)) training\_steps = 1000

x = T.dmatrix("x")

y = T.dvector("y")

w1 = theano.shared(numpy.random.randn(features, hidden), name="w1")

b1 = theano.shared(numpy.zeros(hidden), name="b1")

w2 = theano.shared(numpy.random.randn(hidden), name="w2")

b2 = theano.shared(0., name="b2")

p1 = T.tanh(T.dot(x, w1) + b1)

p2 = T.tanh(T.dot(p1, w2) + b2)

prediction = p2 > 0.5

error = T.nnet.binary\_crossentropy(p2,y)

loss = error.mean() + 0.01 \* (l2(w1) + l2(w2))

gw1, gb1, gw2, gb2 = T.grad(loss, \[w1, b1, w2, b2\])

train = theano.function(inputs=\[x,y\],outputs=\[p2, error\], updates=((w1, w1 - 0.1 \* gw1), (b1, b1 - 0.1 \* gb1), (w2, w2 - 0.1 \* gw2), (b2, b2 - 0.1 \* gb2))) predict = theano.function(inputs=\[x\], outputs=\[prediction\])

print "Accuracy before Training:", sklearn.metrics.accuracy\_score(D\[1\], numpy. array(predict(D\[0\])).ravel())

for i in range(training\_steps):

prediction, error = train(D\[0\], D\[1\])

print "Accuracy after Training:", sklearn.metrics.accuracy\_score(D\[1\], numpy.array(predict(D\[0\])).ravel()) # Accuracy before Training: 0.51

\# Accuracy after Training: 0.716

![](main-34.jpg)

Figure 4-12. Neural Network

In our next example in Listing [4-13](#main-6.xhtml#bookmark51) (and corresponding computational graphs in Figures [4-13 (a)](#main-6.xhtml#bookmark52), [4-13 (b)](#main-6.xhtml#bookmark53) and [4-13 (c)](#main-6.xhtml#bookmark54)) we will define a function using the if-else and switch construct. The reader should note the following:

*   1\. Certain functions need an if-else (or switch) clause for their evaluation. For such cases Theano provides an if-else and switch constructs.
    
*   2\. Expressions and functions can be defined using the if-else and switch constructs and gradients can be generated as with other expressions/constructs.
    
*   3\. In the example we demonstrate the computation of the hinge lose using the if-else and switch construct and verify that it matches to the one defined with max.
    

Listing 4-13. Switch/If-Else

import numpy

import theano

import theano.tensor as T from theano.ifelse import ifelse

def hinge\_a(x,y): return T.max(\[0 \* x, 1-x\*y\])

def hinge\_b(x,y):

return ifelse(T.lt(1-x\*y,0), 0 \* x, 1-x\*y)

def hinge\_c(x,y):

return T.switch(T.lt(1-x\*y,0), 0 \* x, 1-x\*y) x = T.dscalar('x') y = T.dscalar('y') z1 = hinge\_a(x, y) z2 = hinge\_b(x, y) z3 = hinge\_b(x, y) f1 = theano.function(\[x,y\], z1)

f2 = theano.function(\[x,y\], z2)

f3 = theano.function(\[x,y\], z3) print "f(-2, 1) =",f1(-2, 1), f2(-2, 1), f3(-2, 1) print "f(-1,1 ) =",f1(-1, 1), f2(-1, 1), f3(-1, 1) print "f(0,1) =",f1(0, 1), f2(0, 1), f3(0, 1) print "f(1, 1) =",f1(1, 1), f2(1, 1), f3(1, 1) print "f(2, 1) =",f1(2, 1), f2(2, 1), f3(2, 1) # f(-2, 1) = 3.0 3.0 3.0

\# f(-1,1 ) = 2.0 2.0 2.0

\# f(0,1) = 1.0 1.0 1.0

\# f(1, 1) = 0.0 0.0 0.0

\# f(2, 1) = 0.0 0.0 0.0

![](main-35.jpg)

Figure 4-13 (a). Hinge implemented using Max

Figure [4-13 (a)](#main-6.xhtml#bookmark52) illustrates the implementation of the hinge loss using the max operation that is l(y) = max(0,1 -x ■ y) where x is the correct/actual output and y is the output produced by the model. The computational graph closely corresponds to the formula/equation for hinge loss.

![](main-36.jpg)

Figure 4-13 (b). Hinge implemented using ifelse

Figure [4-13 (b)](#main-6.xhtml#bookmark53) illustrates the implementation of the hinge loss using the ifelse construct. Note how the computational graph implements the condition and the intended out for each of the condition.

![](main-37.jpg)

Figure 4-13 (c). Hinge implemented using switch

In our next example in listing [4-14](#main-6.xhtml#bookmark55) (and the corresponding computational graph in Figure [4-14](#main-6.xhtml#bookmark56)) we illustrate the scan construct that allows the user to define functions involving iterative computation. The reader should note the following.

*   1\. Computation of certain functions requires iterative constructs for which Theano provides the scan construct.
    
*   2\. In our example we compute the power operation with the scan construct and match the output with using the standard operator for power.
    
*   3\. Expressions and functions can be defined using the scan construct and gradients can be generated as with other expressions/constructs.
    

Listing 4-14. Scan

import theano import theano.tensor as T import theano.printing k = T.iscalar("k") a = T.dscalar("a") result, updates = theano.scan(fn=lambda prior\_result, a: prior\_result \* a, outputs\_info=a, non\_sequences=a, n\_steps=k-1) final\_result = result\[-1\] a\_pow\_k = theano.function(inputs=\[a,k\], outputs=final\_result, updates=updates) print a\_pow\_k(2,5), 2 \*\* 5 print a\_pow\_k(2,5), 2 \*\* 5

\# 32.0 32

![](main-38.jpg)

Figure 4-14. Scan Operation

## Summary

In this chapter we covered the basics of Theano which is a low level library for building and training neural networks. Theano allows users to build computational graphs and compute gradients and is the ideal tool when it comes to building new architectures/networks as it gives the user a very fine grained control over the computational graph. A number of libraries like Keras (covered in Chapter [7](http://dx.doi.org/10.1007/978-1-4842-2766-4_7)) and Lasagne are built over Theano and provide higher level abstractions so that users need not build networks using computational graphs themselves. Such higher level libraries make the user much more productive, but the user does not have precise control over the network/architecture. In general, higher level libraries are recommended when the higher library provides a close enough implementation of the network/ architecture the user wants to build. In case, this is not available, it is recommended that the user build the network using Theano which will give him complete control. Basically using such high level libraries versus Theano is a tradeoff between productivity and control, much similar to programming in Python vs. programming in C.

CHAPTER 5

Convolutional Neural Networks

![](main-39.png)

Convolution Neural Networks (CNNs) in essence are neural networks that employ the convolution operation (instead of a fully connected layer) as one of its layers. CNNs are an incredibly successful technology that has been applied to problems wherein the input data on which predictions are to be made has a known grid like topology like a time series (which is a 1-D grid) or an image (which is a 2-D grid).

## Convolution Operation

Let us start developing intuition for the convolution operation in one dimension. Given an input I(t) and a kernel K(a) the convolution operation is given by

s(f) = ^f (a) • K(t - a)

a

An equivalent form of this operation given commutativity of the convolution operation is as follows:

s(t) = ^I(t - a) • K(a)

a

Furthermore, the negative sign (flipping) can be replaced to get cross-correlation given as follows:

s(t) = ^I(t+a) • K(a)

a

© Nikhil Ketkar 2017

N. Ketkar, Deep Learning with Python, DOI 10.1007/978-1-4842-2766-4\_5

In deep learning literature and software implementations, convolution and cross-correlation are used interchangeably. The essence of the operation is that the Kernel is a much shorter set of data points as compared to the input, and the output of the convolution operation is higher when the input is similar to the kernel. Figures [5-1](#main-7.xhtml#bookmark5) and [5-2](#main-7.xhtml#bookmark6) illustrate this key idea. We take an arbitrary input and an arbitrary kernel, perform the convolution operation, and the highest value is achieved when the kernel is similar to a particular portion of the input.

![](main-40.jpg)

Figure 5-1. Convolution operation - Intuition

![](main-41.jpg)

Figure 5-2. Convolution operation - One Dimension

Let us strengthen our intuition about convolution by observing Figures [5-1](#main-7.xhtml#bookmark5) and [5-2](#main-7.xhtml#bookmark6) and noting the following points:

*   1\. The input is an arbitrary large set of data points.
    
*   2\. The Kernel is a set of data points smaller in number to the input.
    
*   3\. The convolution operation in a sense slides the kernel over the input and computes how similar the kernel is with the portion of the input.
    
*   4\. The convolution operation produces the highest value where the Kernel is most similar with a portion of the input.
    

The convolution operation can be extended to two dimensions. Given an input I(m, n) and a kernel K(a, b) the convolution operation is given by

s (t ) = -£^i (a ,b) • K(m - a, n - b)

ab

An equivalent form of this operation given commutativity of the convolution operation is as follows:

s(t) = ££l(m - a,n - b) • K(a, b)

ab

Furthermore, the negative sign (flipping) can be replaced to get cross-correlation given as follows:

s(t) = ££l(m + a,n+b) • K(a, b)

ab

Figure [5-3](#main-7.xhtml#bookmark7) illustrates the convolution operation in two dimensions. Note that this is simply extending the idea of convolution to two dimensions.

![](main-42.jpg)

Having introduced the convolution operation, we can now dive deeper into the key constituent parts of a CNN, were a convolution layer is used instead of a fully connected layer which involves a matrix multiplication. So, a fully connected layer can be described as y = f (x ■ w) where x is the input vector, y is the output vector, w is a set of weights, and f is the activation function. Correspondingly, a convolution layer can be described as y = f (s(x ■ w)) where s denotes the convolution operation between the input and the weights.

Let us now contrast the fully connected layer with the convolution layer. Figure [5-4](#main-7.xhtml#bookmark8) illustrates a fully connected layer and Figure [5-5](#main-7.xhtml#bookmark9) illustrates a convolution layer, schematically. Figure [5-6](#main-7.xhtml#bookmark10) illustrates parameter sharing in a convolution layer and the lack of it in a fully connected layer. The following points should be noted:

*   1\. For the same number of inputs and outputs, the fully connected layer has a lot more connections, and correspondingly weights that a convolution layer.
    
*   2\. The interactions amongst inputs to produce outputs are fewer in convolution layers as compared to many interactions in the case of a fully connected layer. This is referred to as sparse interactions.
    
*   3\. Parameters/weights are shared across the convolution layer, given that the kernel is much smaller than the input and the kernel slides across the input. Thus, there are a lot fewer unique parameters/weights in a convolution layer.
    
    ![](main-43.jpg)![](main-44.jpg)![](main-45.jpg)
    
    Figure 5-4. Dense Interactions in Fully Connected Layers
    
    ![](main-46.jpg)![](main-47.jpg)
    
    Figure 5-6. Parameter Sharing Tied Weights
    

## Pooling Operation

Let us now look at the pooling operation which is almost always used in CNNs in conjunction with convolution. The intuition behind the pooling operation is that the exact location of the feature is not a concern if in fact it has been discovered. It simply provides translation invariance. So, for instance, assume that the task at hand is to learn to detect faces in photographs. Let us also assume that the faces in the photograph are tilted (as they generally are) and suppose that we have a convolution layer that detects the eyes. We would like to abstract the location of the eyes in the photograph from their orientation. The pooling operation achieves this and is an important constituent of CNNs.

Figure [5-7](#main-7.xhtml#bookmark13) illustrates the pooling operation for a two-dimensional input. The following points are to be noted:

*   1\. Pooling operates over a portion of the input and applies a function f over this input to produce the output.
    
*   2\. The function f is commonly the max operation (leading to max pooling), but other variants such as average or L[2] norm can be used as an alternative.
    
*   3\. For a two-dimensional input, this is a rectangular portion.
    
*   4\. The output produced as a result of pooling is much smaller in dimensionality as compared to the input.
    
    ![](main-48.jpg)

## Convolution-Detector-Pooling Building Block

Let us now look at the Convolution-Detector-Pooling block, which can be thought of as a building block of the CNN.

Let us now look at how all the operations we have covered earlier work in conjunction. Refer to Figure [5-8](#main-7.xhtml#bookmark16) and Figure [5-9](#main-7.xhtml#bookmark17). The following points are to be noted:

*   1\. The detector stage is simply a non-linear activation function.
    
*   2\. The convolution, detector, and pooling operations are applied in sequence to transform the input to the output. The output is referred to as a feature map.
    
*   3\. The output typically is passed on to other layers (convolution or fully connected).
    
*   4\. Multiple Convolution-Detector-Pooling blocks can be applied in parallel, consuming the same input and producing multiple outputs or feature maps.
    
    ![](main-49.jpg)
    
    Figure 5-8. Convolution followed by detector stage and pooling
    
    ![](main-50.jpg)
    
    Figure 5-9. Multiple Filters/Kernels giving Multiple Feature Maps
    

In the case of image inputs, which consist of 3 channels, a separate convolution operation is applied to each channel and then outputs post the convolution are added up. This is illustrated in Figure [5-10](#main-7.xhtml#bookmark18).

![](main-51.jpg)

Figure 5-10. Convolution with Multiple Channels

Having covered all the constituent elements of CNNs, we can now look at an exemplar CNN in its entirety as illustrated in Figure [5-11](#main-7.xhtml#bookmark19). The CNN consists of two stages of convolution-detector-pooling blocks with multiple filters/kernels at each stage producing multiple feature maps. Post these two stages we have a fully connected layer which produces the output. In general, a CNN may have multiple stages of convolution-detector-pooling blocks (employing multiple filters) typically followed by a fully connected layer.

![](main-52.jpg)

Figure 5-11. A Complete Convolution Neural Network Architecture

## Convolution Variants

We will now cover some variations of convolution, illustrated in Figure [5-12](#main-7.xhtml#bookmark22). Strided convolution is a variant of the standard convolution where the kernel slides over the input by moving at a predefined stride. An alternative way of looking at this is that the standard convolution operated at a stride size equal to one. Another variation is tiled convolution where there are actually multiple kernels that are convolved with the input alternately.

![](main-53.jpg)

Figure 5-12. Convolution, variation on the theme

Another variation on the theme is locally connected layers which basically employ sparsity of interactions but do not employ parameter/weight sharing. This is illustrated in Figure [5-13](#main-7.xhtml#bookmark23).

Locally Connected Unique Weights

![](main-54.jpg)![](main-55.jpg)![](main-56.jpg)![](main-57.jpg)

Figure 5-13. Locally Connected Weights

![](main-58.jpg)

## Intuition behind CNNs

So far in this chapter we have covered the key constituent concepts behind the CNN, namely the convolution operation, the pooling operation, and how they are used in conjunction. Let us now take a step back to internalize the intuition behind CNNs using these building blocks.

The first idea to consider is the capacity of CNNs (refer to Chapter [2](http://dx.doi.org/10.1007/978-1-4842-2766-4_2) on the capacity of a machine learning model). CNNs, which replace at least one of the fully connected layers of a neural network by the convolution operation, have less capacity than a fully connected network. That is, there exist data sets that a fully connected network will be able to model that a CNN will not be. So, the first point to note is that CNNs achieve more by limiting the capacity, hence making the training efficient.

The second idea to consider is that learning the filters driving the convolution operation is, in a sense, representation learning. For instance, the learned filters might learn to detect edges, shapes, etc. The important point to consider here is that we are not manually describing the features to be extracted from the input data, but are describing an architecture that learns to engineer the features/representations.

The third idea to consider is the location invariance introduced by the pooling operation. The pooling operation separates the location of the feature from the fact that it is detected. A filter detecting straight lines might detect this filter in any portion of the image, but the pooling operation picks the fact that the feature is detected (max pooling).

The fourth idea is that of hierarchy. A CNN may have multiple convolution and pooling layers stacked up followed by a fully connected network. This allows the CNN to build a hierarchy of concepts wherein more abstract concepts are based on simpler concepts (refer to Chapter [1](http://dx.doi.org/10.1007/978-1-4842-2766-4_1)).

The fifth and last idea is the presence of a fully connected layer at the end of a series convolution and pooling layers. The idea is that the series of convolution and pooling layers generates the features and a standard neural network learns the final classification/regression function. It is important to distinguish this aspect of the CNN from traditional machine learning. In traditional machine learning, an expert would hand engineer features and feed them to a neural network. In the case of CNNs, these features/representations are being learned from data.

## Summary

In this chapter we covered the basics of CNNs. The key takeaway points are the convolution operation, the pooling operation, how they are used in conjunction, and how features are not hand engineered but learned. CNNs are the most successful application of deep learning and embody the idea of learning features/ representations rather than hand engineering them.

CHAPTER 6

Recurrent Neural Networks

![](main-59.png)

Recurrent Neural Networks (RNNs) in essence are neural networks that employ recurrence, which is basically using information from a previous forward pass over the neural network. Essentially, all RNN's can be described as a recurrence relationship. RNNs are suited and have been incredibly successful when applied to problems wherein the input data on which the predictions are to be made is in the form of a sequence (series of entities where order is important).

## RNN Basics

Let us start by describing the moving parts of a RNN. First, we introduce some notation.

*   1\.   We will assume that input consists of a sequence of entities x^((1)), X²\\..., X^T\\
    
*   2\.  Corresponding to this input we either need to produce a sequence y^((1)), y®,  yW
    

or just one output for the entire input sequence y

*   3\.  To distinguish between what the RNN produces and what it is ideally expected to
    

produce we will denote by y^((1)), y^((2)),   y ^(^t^) or y the output the RNN produces.

Note that this is distinct from what the RNN should ideally produce, which is denoted by y^((1)), y^((2)),   y^((T)) or y.

RNNs either produce an output for every entity in the input sequence or produce a single output for the entire sequence. Let us consider the case where an RNN produces one output for every entity in the input. The RNN can be described using the following equations:

h^(^t^)\=tanh[(]Ux^(^t^)+Wh^(^t^(\-1))+b[)]

The following points about the RNN equations should be noted:

*   1\.  The RNN computation involves first computing the hidden state for an entity in the sequence. This is denoted by h^(^t^).
    
*   2\.   The computation of h^(^t^) uses the corresponding input at entity x^(^t^) and the previous hidden state h^(^t^(\-1)).
    
*   3\.   The output y^(^t^) is computed using the hidden state h^((t)\\
    
*   4\.  There are weights associated with the input and the previous hidden state while computing the current hidden state. This is denoted by U and W respectively. There is also a bias term denoted by b.
    

© Nikhil Ketkar 2017

N. Ketkar, Deep Learning with Python, DOI 10.1007/978-1-4842-2766-4\_6

*   5\. There are weights associated with the hidden state while computing the output; this is denoted by V. There is also a bias term, which is denoted by c.
    
*   6\. The tanh activation function (introduced in earlier chapters) is used in the computation of the hidden state.
    
*   7\. The softmax activation function is used in the computation of the output.
    
*   8\. The RNN as described by the equations can process an arbitrarily large input sequence.
    
*   9\. The parameters of the RNN, namely, U,W,V,b,c, etc. are shared across the computation of the hidden layer and output value (for each of the entities in the sequence).
    

Figure [6-1](#main-7.xhtml#bookmark31) illustrates an RNN. Note how the illustration depicts the recurrence relation with the self-loop at the hidden state.

![](main-60.jpg)

Figure 6-1. RNN (Recurrence using the previous hidden state)

The figure also depicts a loss function associated with each output associated with each input. We will refer back to it when we cover how RNNs are trained.

Presently, it's essential to internalize how an RNN is different from all the feedforward neural networks (including convolution networks) we have seen earlier. The key difference is the hidden state, which represents a summary of the entities seen in the past (for the same sequence).

Ignoring for the time being how RNNs are trained, it should be clear to the reader how a trained RNN could be used. For a given sequence of inputs, an RNN would produce an output for each entity in the input.

Let us now consider a variation in the RNN wherein instead of the recurrence using the hidden state, we have recurrence using the output produced in the previous state (refer to Figure [6-2](#main-7.xhtml#bookmark32)).

![](main-61.jpg)

Figure 6-2. RNN (Recurrence using the previous output)

The equations describing such an RNN are as follows:

h^((t) > \= tanh (UX^((t)\> \+ Wy^(G-1)) + b)

![](main-62.jpg)

The following points are to be noted:

*   1\. The RNN computation involves first computing the hidden state for an entity in the sequence. This is denoted by h^(^t^).
    
*   2\. The computation of h^(^t^) uses the corresponding input at entity x^(^t^) and the previous output y^((-1)).
    
*   3\.  The output y® is computed using the hidden state h^((t)\\
    
*   4\.  There are weights associated with the input and the previous output while computing the current hidden state. This is denoted by U and W respectively. There is also a bias term denoted by c.
    
*   5\.  There are weights associated with the hidden state while computing the output; this is denoted by V. There is also a bias term, which is denoted by c.
    
*   6\.   The tanh activation function (introduced in earlier chapters) is used in the computation of the hidden state.
    

The softmax activation function is used in the computation of the output.

Let us now consider a variation in the RNN where only a single output is produced for the entire sequence (refer to Figure [6-3](#main-7.xhtml#bookmark33)). Such an RNN is described using the following equations:

h^) \= tanh(Ux^((()^) \+ Wy'^(^,^(\-1)) + b)

![](main-63.jpg)![](main-64.jpg)

Figure 6-3. RNN (Producing a single output for the entire input sequence)

The following points are to be noted:

*   1\.  The RNN computation involves computing the hidden state for an entity in the
    

sequence. This is denoted by h^(^t^).

*   2\.  The computation of h^(^t^) uses the corresponding input at entity x^(^t^) and the
    

previous hidden state h^(^t ^(\-1)).

*   3\.  The computation of h^(^t^) is done for each entity in the input sequence
    

xW x^((2)) ... X^T\\

*   4.  The output y is computed only using the last hidden state
    
*   5.  There are weights associated with the input and the previous hidden state while computing the current hidden state. This is denoted by U and W respectively. There is also a bias term denoted by b.
    
*   6.  There are weights associated with the hidden state while computing the output; this is denoted by V. There is also a bias term, which is denoted by c.
    
*   7.   The tanh activation function (introduced in earlier chapters) is used in the computation of the hidden state.
    
*   8.  The softmax activation function is used in the computation of the output.
    

## Training RNNs

Let us now look at how RNNS are trained. To do this, we first need to look at how the RNN looks when we unroll the recurrence relation which is at the heart of the RNN.

L

![](main-65.jpg)

O^¹’ □«^((2>) n»^(<3)) c«^(<4)\>

![](main-66.jpg)![](main-67.jpg)![](main-68.jpg)![](main-69.jpg)

Figure 6-4. Unrolling the RNN corresponding to Figure [6-1](#main-7.xhtml#bookmark31)

Unrolling the recurrence relation corresponding to RNN is simply writing out the equations by recursively substituting the value on which recurrence relation is defined. In the case of the RNN in Figure [6-1](#main-7.xhtml#bookmark31), this is h^(^t^). That is, the value of h^(^t^) is defined in terms of h^(^t^(\-1)), which in turn is defined in terms of h^(^t ^(\-2)) and so on till h^((0)).

![](main-70.jpg)![](main-71.jpg)

We will assume that h^((0)) is either predefined by the user, set to zero, or learned as another parameter/ weight (learned like W, V, or b). Unrolling simply means writing out the equations describing the RNN in terms of h^((0)). Of course, in order to do so, we need fix the length of the sequence, which is denoted by t. Figure [6-4](#main-7.xhtml#bookmark36) illustrates the unrolled RNN corresponding to the RNN in Figure [6-1](#main-7.xhtml#bookmark31) assuming an input sequence of size 4. Similarly, Figure [6-5](#main-7.xhtml#bookmark37) and [6-6](#main-7.xhtml#bookmark38) illustrate the unrolled RNNs corresponding to the RNNs in Figure [6-2](#main-7.xhtml#bookmark32) and [6-3](#main-7.xhtml#bookmark33) respectively. The following points are to be noted:

*   1\.  The unrolling process operates on the assumption that the length of the input sequence is known beforehand and based on the recurrence is unrolled.
    
*   2\.  Once unrolled, we essentially have a non-recurrent neural network.
    
*   3\.  The parameters to be learned, namely, U,W,V,b,c, etc. (denoted in dark in the
    

diagram) are shared across the computation of the hidden layer and output value. We have seen such parameter sharing earlier in the context of CNNs.

*   4\.  Given an input and output of a given size, say t (assumed to be 4 in Figures[ 6-4](#main-7.xhtml#bookmark36),
    

[6-5](#main-7.xhtml#bookmark37), [6-6](#main-7.xhtml#bookmark38)), we can unroll an RNN and compute gradients for the parameters to be learned with respect to a loss function (as we have seen in earlier chapters).

*   5\.  Thus, training an RNN is simply unrolling the RNN for a given size of input (and, correspondingly, the expected output) and training the unrolled RNN via computing the gradients and using stochastic gradient descent.
    

As mentioned earlier in the chapter, RNNs can deal with arbitrarily long inputs and correspondingly, they need to be trained on arbitrarily long inputs. Figure [6-7](#main-7.xhtml#bookmark39) illustrates how an RNN is unrolled for different sizes of inputs. Note that once the RNN is unrolled, the process of training the RNN is identical to training a regular neural network which we have covered in earlier chapters. In Figure [6-7](#main-7.xhtml#bookmark39) the RNN described in Figure [6-1](#main-7.xhtml#bookmark31) is unrolled for input sizes of 1,2,3 and 4.

![](main-72.jpg)

Figure 6-7. Unrolling the RNN corresponding to Figure [6-1](#main-7.xhtml#bookmark31) for different sizes of inputs

Given that the data set to be trained on consists of sequences of varying sizes, the input sequences are grouped so that the sequences of the same size fall in one group. Then for a group, we can unroll the RNN for the sequence length and train. Training for a different group will require the RNN to be unrolled for a different sequence length. Thus, it is possible to train the RNN on inputs of varying sizes by unrolling and training with the unrolling done based on the sequence length.

![](main-73.jpg)

Figure 6-8. Teacher Forcing (Top - Training, Bottom - Prediction)

It must be noted that training the unrolled RNN (illustrated in Figure [6-1](#main-7.xhtml#bookmark31)) is essentially a sequential process, as the hidden states are dependent on each other. In the case of RNNs wherein the recurrence is over the output instead of the hidden state (Figure [6-2](#main-7.xhtml#bookmark32)), it is possible to use a technique called teacher forcing as illustrated in Figure [6-8](#main-7.xhtml#bookmark40). The key idea here is to use y^(^t^(\-1)) instead of y^((-1)) in the computation of h® while training. While making predictions (when the model is deployed for usage), however, y‘^(\-1)) is used.

## Bidirectional RNNs

Let us now take a look at another variation on RNNs, namely, the bidirectional RNN. The key intuition behind a bidirectional RNN is to use the entities that lie further in the sequence to make a prediction for the current entity. For all the RNNs we have considered so far we have been using the previous entities (captured by the hidden state) and the current entity in the sequence to make the prediction. However, we have not been using information concerning the entities that lie further in the sequence to make predictions. A bidirectional RNN leverages this information and can give improved predictive accuracy in many cases.

A bidirectional RNN can be described using the following equations:

h^([f]^t^)\=tanh[(]U[f]x^(^t^)+W[f]h^(^t^(+1))+b[f] [)]

h[b]^(^t^) =tanh[(]U[b]x^(^t^)+W[b]h^(^t^(\-1))+b[b] [)]

y ^v^) = softmax ((^) + V[f]hf^) + c )

The following points are to be noted:

*   1\.  The RNN computation involves first computing the forward hidden state and backward hidden state for an entity in the sequence. This is denoted by h[f]^(^t^) and h[b]^(^t^) respectively.
    
*   2\.   The computation of h[f]^(^t^) uses the corresponding input at entity x^(^t^) and the previous hidden state h^([f]^t^(\-1)).
    
*   3\.   The computation of h[b]^(^t^) uses the corresponding input at entity x^(^t^) and the previous hidden state h[b]^(^t^(\-1)).
    
*   4\.   The output y^(^t^) is computed using the hidden state h® and h[b]^((t)^)
    
*   5\.  There are weights associated with the input and the previous hidden state while computing the current hidden state. This is denoted by U[f] , W[f], U[b] , and W[b ]respectively. There is also a bias term denoted by b[f] and b[b].
    
*   6\.  There are weights associated with the hidden state while computing the output; this is denoted by V[b] and V[f] . There is also a bias term, which is denoted by c.
    
*   7\.   The tanh activation function (introduced in earlier chapters) is used in the computation of the hidden state.
    
*   8\.  The softmax activation function is used in the computation of the output.
    
*   9\.  The RNN as described by the equations can process an arbitrarily large input sequence.
    
*   10\. The parameters of the RNN, namely, U[f], U[b], Wf, W[b], V[b], V[f], b[f], b[b], c, etc. are shared across the computation of the hidden layer and output value (for each of the entities in the sequence).
    
    ![](main-74.jpg)
    
    Figure 6-9. Bidirectional RNN
    

## Gradient Explosion and Vanishing

Training RNNs suffers from the challenges of vanishing and explosion of gradients. Vanishing gradients means that, when computing the gradients on the unrolled RNNs, the value of the gradients can drop to a very small value (close to zero). Similarly, the gradients can increase to a very high value which is referred to as the exploding gradient problem. In both cases, training the RNN is a challenge.

Let us relook at the equations describing the RNN.

h^(^t^) = tanh[(]Ux^(^t^) +Wh^(^t^(\-1))+b

y ^v^) = softmax (h^v^) + c )

dL

Let us derive the expression for the by applying the chain rule. This is illustrated in Figure [6-10](#main-8.xhtml#bookmark4). fIV

dL = [z] dl!‘^)

SW = ^tsh^

 
|  || r       dh°'^(+i))l || dh^(^) |
| --- | --- | --- |
| zl<k< t || \_ JJi dh(^((j) \_ || dll' |

Let us now focus on the part of the expression

dh^((+i))

XL \\

which involves a repeated matrix

multiplication of W which contributes to both the vanishing and exploding gradient problems. Intuitively, this is similar to multiplying a real valued number over and over again, which might lead to the product shrinking to zero or exploding to infinity.

## Gradient Clipping

One simple technique to deal with exploding gradients is to rescale the norm of gradient whenever it goes A QL          I Al                    A C A

over a user-defined threshold. Specifically, if the gradient denoted by g =     and if g > c then we set g =   g.

5W      ^(11)                 gg

This technique is both simple and computationally efficient but does introduce an extra hyperparameter.

![](main-75.jpg)

Figure 6-10. Vanishing and Exploding Gradients

## Long Short Term Memory

Let us now take a look at another variation on RNNs, namely, the Long Short Term Memory (LSTM) Network. An LSTM can be described with the following set of equations. Note that the symbol © . notes pointwise multiplication of two vectors (if a = \[1,1,2\] and b = \[0.5,0.5,0.5\], then aQb = \[0.5,0.5,1\], the functions c, g and h are non-linear activation functions, all W and R are weight matrices, and all the b terms are bias terms).

^Z^)\= g((^()+) ^Rz ^y' ^bz )

i^w^) \=s(w[t]x^) + R[t] y^((t-1>) + p[t] Q c^(^t^(\-1)) + b[t])

f^w^) = s(w[f]x‘ + R[f] w[(]^(\-1)) + p[f] © c^(^t^(\-1)) + b[f] )

c^()= i^(^) © z^(^) + f ^(^) © c^((-1))

^) = s (x^(^t^) + R[o] y^(^t^(\-1)) + p[o] © c^) + b[o])

y^(^)\= o^(^) © h((^))

The following points are to be noted:

*   1\.  The most important element of the LSTM is the cell state denoted by
    

c^(^) = i^(^) ©z^(^t\*+f^(^) ©c^(^(\-1)). The cell state is updated based on the block input z® and the previous cell state c^(^t^(\-1)). The input gate i^(^t^) determines what fraction of the block input makes it into the cell state (hence called a gate). The forget gate f ^(^t^() )determines how much of the previous cell state to retain.

*   2\.   The output y^((t)^) is determined based on the cell state c^(^t^) and the output gate o^(^t^), which determines how much the cell state affects the output.
    
*   3\.   The z^(^t^) term is referred to as the block input and it produces a value based on the current input and the previous output.
    
*   4\.   The i^(^t^) term is referred to as the input gate. It determines how much of the input to retain in the cell state c^(^t^).
    
*   5\.  All the p terms are peephole connections, which allow for a faction of the cell state to factor into the computation of the term in question.
    
*   6\.   The computation of the cell state c^(^i^) does not encounter the issue of the vanishing gradient (this is referred to as the constant error carousal). However, LSTMs are affected by exploding gradients and gradient clipping is used while training.
    
    ![](main-76.jpg)
    
    Figure 6-11. Long Short Term Memory
    

## Summary

In this chapter we covered the basics of Recurrent Neural Networks (RNN). The key take-home points from this chapter are the notion of the hidden state, training RNNs via unrolling (backpropagation through time), the problem of vanishing and exploding gradients, and long short term memory networks. It is important to internalize how RNNs contain internal/hidden states that allow them to make predictions on a sequence of inputs, an ability that goes beyond conventional neural networks.

CHAPTER 7

Introduction to Keras

![](main-77.png)

This chapter introduces the reader to Keras, which is a library that provides highly powerful and abstract building blocks to build deep learning networks. The building blocks Keras provides are built using Theano (covered earlier) as well as TensorFlow (which is an alternative to Theano for building computational graphs, automatically deriving gradients, etc.). Keras supports both CPU and GPU computation and is a great tool for quickly prototyping ideas.

We will introduce a number of key building blocks Keras provides, and then build a CNN and LSTM using Keras.

Let us start with a simple, single layer neural network. Listing [7-1](#main-8.xhtml#bookmark12) provides the code and Figure [7-1](#main-8.xhtml#bookmark13) gives the computational graph. The following points are to be noted:

*   1\. A model is defined using the Sequential construct, which allows the user to add/configure layers.
    
*   2\. Using this functionality, a user can add one or more layers and build the network. The Dense layer is basically a fully connected layer (leading to a vector-matrix or vector-vector product), which we have seen earlier.
    
*   3\. The input and output dimensionality needs to be specified when the first layer is defined. In this case the model will take an input of dimensionality 500 and produce an output of dimensionality 1.
    
*   4\. After this layer we add an activation function, in this case a sigmoid.
    
*   5\. The model once defined needs to be explicitly compiled and, at this time, we provide the loss function, the optimization algorithm, and other metrics we want to calculate.
    
*   6\. An appropriate loss function needs to be picked given the task at hand; in this case, given that we have a binary classification problem, we select binary cross-entropy.
    
*   7\. An appropriate optimization algorithm needs to be picked, which typically is a variant of Stochastic Gradient Descent (coved in later chapters).
    
*   8\. Once compiled we can fit the model by providing the data and evaluate the model.
    

© Nikhil Ketkar 2017

N. Ketkar, Deep Learning with Python, DOI 10.1007/978-1-4842-2766-4\_7

Listing 7-1. Single Layer Neural Network

import numpy as np

from keras.models import Sequential

from keras.layers import Dense, Activation

from keras.utils.visualize\_util import plot

model = Sequential()

model.add(Dense(1, input\_dim=500)) model.add(Activation(activation='sigmoid')) model.compile(optimizer='rmsprop', loss='binary\_crossentropy', metrics=\['accuracy'\])

data = np.random.random((1000, 500))

labels = np.random.randint(2, size=(1000, 1))

score = model.evaluate(data,labels, verbose=0)

print "Before Training:", zip(model.metrics\_names, score)

model.fit(data, labels, nb\_epoch=10, batch\_size=32, verbose=0)

score = model.evaluate(data,labels, verbose=0)

print "After Training:", zip(model.metrics\_names, score)

plot(model, to\_file='s1.png', show\_shapes=True)

\# Before Training: \[('loss', 0.76832762384414677), ('acc', 0.50700000000000001)\]

\# After Training: \[('loss', 0.67270196056365972), ('acc', 0.56299999999999994)\]

![](main-78.jpg)

Figure 7-1. Single Layer Neural Network (Binary Classification)

Listing 7-2. Two Layer Neural Network

import numpy as np

from keras.models import Sequential

from keras.layers import Dense, Activation from keras.utils.visualize\_util import plot

model = Sequential() model.add(Dense(32, input\_dim=500)) model.add(Activation(activation='sigmoid')) model.add(Dense(1))

model.add(Activation(activation='sigmoid')) model.compile(optimizer='rmsprop', loss='binary\_crossentropy', metrics=\['accuracy'\])

data = np.random.random((1000, 500)) labels = np.random.randint(2, size=(1000, 1))

score = model.evaluate(data,labels, verbose=0) print "Before Training:", zip(model.metrics\_names, score)

model.fit(data, labels, nb\_epoch=10, batch\_size=32, verbose=0)

score = model.evaluate(data,labels, verbose=0) print "After Training:", zip(model.metrics\_names, score)

plot(model, to\_file='s2.png', show\_shapes=True)

\# Before Training: \[('loss', 0.73012506151199341), ('acc', 0.51200000000000001)\] # After Training: \[('loss', 0.6588478517532349), ('acc', 0.52700000000000002)\]

Let us now look at a two-layer neural network. Listing [7-2](#main-8.xhtml#bookmark14) provides the code and Figure [7-2](#main-8.xhtml#bookmark15) gives the computational graph. The following points are to be noted:

*   1\. A model is defined using the Sequential construct.
    
*   2\. We add the first layer, using Dense, and specify the input dimensionality. In this case the model will take an input of dimensionality 500 and produce an output of dimensionality 32.
    
*   3\. We define an activation function, selecting sigmoid.
    
*   4\. We then define the second layer using Dense. Here we define the output dimensionality to be 1. Note, however, that we do not need to define the input dimensionality, as it is the same as the dimensionality of the output of the previous layer.
    
*   5\. As before, we define the optimize and loss function, compile, train, and evaluate.
    
    ![](main-79.jpg)
    
    Figure 7-2. Double Layer Neural Network (Binary Classification)
    

Let us now look at a two-layer neural network for multiclass classification. Listing [7-3](#main-8.xhtml#bookmark16) provides the code and Figure [7-3](#main-8.xhtml#bookmark17) gives the computational graph. The following points are to be noted:

*   1\. A model is defined using the Sequential construct.
    
*   2\. We add the first layer, using Dense, and specify the input dimensionality. In this case the model will take an input of dimensionality 500 and produce an output of dimensionality 32.
    
*   3\. We define an activation function, selecting sigmoid.
    
*   4\. We then define the second layer using Dense. Here we define the output dimensionality to be 10. Note that this is exactly equal to the number of classes we have in our dataset.
    
*   5\. Next we use the softmax activation and the categorical entropy as the loss function (an earlier chapter covers why this is a good choice).
    
*   6\. We compile, train, and evaluate the model as before.
    

Listing 7-3. Multiclass Classification

import numpy as np

from keras.models import Sequential

from keras.layers import Dense, Activation

from keras.utils.np\_utils import to\_categorical

from keras.utils.visualize\_util import plot

model = Sequential()

model.add(Dense(32, input\_dim=500)) model.add(Activation(activation='relu'))

model.add(Dense(10)) model.add(Activation(activation='softmax')) model.compile(optimizer='rmsprop', loss='categorical\_crossentropy', metrics=\['categorical accuracy'\])

data = np.random.random((1000, 500))

labels = to\_categorical(np.random.randint(10, size=(1000, 1)))

score = model.evaluate(data,labels, verbose=0)

print "Before Training:", zip(model.metrics\_names, score)

model.fit(data, labels, nb\_epoch=10, batch\_size=32, verbose=0)

score = model.evaluate(data,labels, verbose=0)

print "After Training:", zip(model.metrics\_names, score)

plot(model, to\_file='s3.png', show\_shapes=True)

\# Before Training: \[('loss', 2.4697211952209472), ('categorical\_accuracy', 0.092999999999999999)\]

\# After Training: \[('loss', 2.1891849689483642), ('categorical\_accuracy', 0.19400000000000001)\]

![](main-80.jpg)

Figure 7-3. Multiclass Classification

Let us now look at a two-layer neural network for regression. Listing [7-4](#main-8.xhtml#bookmark18) provides the code and Figure [7-4](#main-8.xhtml#bookmark19) gives the computational graph. The following points are to be noted:

*   1\. A model is defined using the Sequential construct.
    
*   2\. We add the first layer, using Dense, and specify the input dimensionality. In this case the model will take an input of dimensionality 500 and produce an output of dimensionality 32.
    
*   3\. We define an activation function, selecting sigmoid.
    
*   4\. We then define the second layer using Dense, producing an output of dimensionality 1.
    
*   5\. We select the activation as sigmoid and select mean squared error, which is appropriate for regression.
    
*   6\. We compile, train, and evaluate the model.
    

Listing 7-4. Regression

import numpy as np

from keras.models import Sequential

from keras.layers import Dense, Activation

from keras.utils.visualize\_util import plot

model = Sequential()

model.add(Dense(32, input\_dim=500)) model.add(Activation(activation='sigmoid'))

model.add(Dense(1)) model.add(Activation(activation='sigmoid')) model.compile(optimizer='rmsprop', loss='mse', metrics=\['mean\_squared\_error'\])

data = np.random.random((1000, 500))

labels = np.random.randint(2, size=(1000, 1))

score = model.evaluate(data,labels, verbose=0)

print "Before Training:", zip(model.metrics\_names, score)

model.fit(data, labels, nb\_epoch=10, batch\_size=32, verbose=0)

score = model.evaluate(data,labels, verbose=0)

print "After Training:", zip(model.metrics\_names, score)

plot(model, to\_file='s4.png', show\_shapes=True)

\# Before Training: \[('loss', 0.26870122766494753), ('mean\_squared\_error', 0.26870122766494753)\]

\# After Training: \[('loss', 0.22180086207389832), ('mean\_squared\_error', 0.22180086207389832)\]

Let us now take a pause and look at how Keras allows for quick iteration of ideas.

*   1\. New models can be quickly defined, trained, and evaluated using the sequential construct.
    
*   2\. The parameters of the layers input/output dimensionality can be easily modified.
    
*   3\. We can compare multiple choices of activation functions easily. Listing [7-6](#main-8.xhtml#bookmark20) illustrates how we can compare the effects of activation functions.
    
*   4\. We can compare multiple choices of optimization algorithms easily. Listing [7-5](#main-8.xhtml#bookmark21) illustrates how we can compare the effects of different choices of activation algorithms.
    
    ![](main-81.jpg)
    
    Figure 7-4. Regression
    

Listing 7-5. Optimisers

import numpy as np

from keras.models import Sequential

from keras.layers import Dense, Activation

def train\_given\_optimiser(optimiser):

model = Sequential() model.add(Dense(1, input\_dim=500)) model.add(Activation(activation='sigmoid')) model.compile(optimizer=optimiser, loss='binary\_crossentropy', metrics=\['accuracy'\])

data = np.random.random((1000, 500))

labels = np.random.randint(2, size=(1000, 1))

score = model.evaluate(data,labels, verbose=0)

print "Optimiser: ", optimiser

print "Before Training:", zip(model.metrics\_names, score)

model.fit(data, labels, nb\_epoch=10, batch\_size=32, verbose=0)

score = model.evaluate(data,labels, verbose=0)

print "After Training:", zip(model.metrics\_names, score) train\_given\_optimiser("sgd") train\_given\_optimiser("rmsprop") train\_given\_optimiser("adagrad") train\_given\_optimiser("adadelta") train\_given\_optimiser("adam") train\_given\_optimiser("adamax") train\_given\_optimiser("nadam") # Optimiser: sgd

\# Before Training: \[('loss', 0.76416229248046874), ('acc', 0.51800000000000002)\]

\# After Training: \[('loss', 0.6759231286048889), ('acc', 0.56899999999999995)\]

\# Optimiser: rmsprop

\# Before Training: \[('loss', 0.77773557662963866), ('acc', 0.52600000000000002)\]

\# After Training: \[('loss', 0.727150842666626), ('acc', 0.53500000000000003)\]

\# Optimiser: adagrad

\# Before Training: \[('loss', 0.9275067367553711), ('acc', 0.49099999999999999)\]

\# After Training: \[('loss', 0.66770141410827633), ('acc', 0.57599999999999996)\]

\# Optimiser: adadelta

\# Before Training: \[('loss', 0.76523585319519039), ('acc', 0.48799999999999999)\]

\# After Training: \[('loss', 0.70753741836547857), ('acc', 0.51700000000000002)\]

\# Optimiser: adam

\# Before Training: \[('loss', 0.76974405097961429), ('acc', 0.51100000000000001)\]

\# After Training: \[('loss', 0.66079518222808842), ('acc', 0.59399999999999997)\]

\# Optimiser: adamax

\# Before Training: \[('loss', 0.76244759178161625), ('acc', 0.49399999999999999)\]

\# After Training: \[('loss', 0.67273861455917361), ('acc', 0.58499999999999996)\]

\# Optimiser: nadam

\# Before Training: \[('loss', 0.71690645027160649), ('acc', 0.50600000000000001)\]

\# After Training: \[('loss', 0.62006913089752203), ('acc', 0.68799999999999994)\]

Keras implements a number of optimisers, namely Stocastic Gradient Descent (SGD), RMSProp, AdaGrad, AdataDelta, Adam, Adamax, and Nadam. Chapter [8](http://dx.doi.org/10.1007/978-1-4842-2766-4_8) covers these (SGD and its variants) in much detail, explaining the intuition for each. For the context of this chapter it suffices to say that Keras makes it easy for users to experiment with these optimisers with very little coding effort.

Listing 7-6. Activation Functions

import numpy as np

from keras.models import Sequential

from keras.layers import Dense, Activation

def train\_given\_activation(activation):

model = Sequential() model.add(Dense(1, input\_dim=500)) model.add(Activation(activation=activation)) model.compile(optimizer="sgd", loss='binary\_crossentropy', metrics=\['accuracy'\])

data = np.random.random((1000, 500))

labels = np.random.randint(2, size=(1000, 1))

score = model.evaluate(data,labels, verbose=0)

print "Activation: ", activation

print "Before Training:", zip(model.metrics\_names, score)

model.fit(data, labels, nb\_epoch=10, batch\_size=32, verbose=0)

score = model.evaluate(data,labels, verbose=0)

print "After Training:", zip(model.metrics\_names, score)

train\_given\_activation("relu")

train\_given\_activation("tanh") train\_given\_activation("sigmoid") train\_given\_activation("hard\_sigmoid") train\_given\_activation("linear")

\# Activation: relu

\# Before Training: \[('loss', 2.6973885402679443), ('acc', 0.48899999999999999)\]

\# After Training: \[('loss', 7.7373054656982418), ('acc', 0.505)\]

\# Activation: tanh

\# Before Training: \[('loss', 5.0640698051452633), ('acc', 0.41699999999999998)\]

\# After Training: \[('loss', 7.6523446731567386), ('acc', 0.52000000000000002)\]

\# Activation: sigmoid

\# Before Training: \[('loss', 0.70816111516952518), ('acc', 0.52500000000000002)\]

\# After Training: \[('loss', 0.67464308834075926), ('acc', 0.58199999999999996)\]

\# Activation: hard\_sigmoid

\# Before Training: \[('loss', 0.70220352411270137), ('acc', 0.52100000000000002)\]

\# After Training: \[('loss', 0.67294596910476689), ('acc', 0.58099999999999996)\]

\# Activation: linear

\# Before Training: \[('loss', 3.5439299507141113), ('acc', 0.47799999999999998)\]

\# After Training: \[('loss', 8.2581552581787108), ('acc', 0.0)\]

Keras implements a number of activation functions, namely, tanh, sigmoid, hard\_sigmoid, linear, and relu (rectified linear unit). Activation functions and their appropriateness given a task (classification, multiclassification, regression, etc.) are covered in much detail in Chapter [3](http://dx.doi.org/10.1007/978-1-4842-2766-4_3). For the context of this chapter, it suffices to say that Keras makes it easy for users to experiment with these activation functions with very little coding effort.

Let us now look at the constructs Keras provides to build the Convolution Neural Networks introduced in Chapter [5](http://dx.doi.org/10.1007/978-1-4842-2766-4_5). The data set we will be using is the MNIST data set, which is a commonly used benchmark data set for deep learning. The data set consists of handwritten digits (60,000 training examples and 10,000 test examples). The task at hand is to predict the digit given the image, so this is a multiclassifcation problem with ten classes.

Listing 7-7. CNN

import numpy as np

from keras.datasets import mnist

from keras.models import Sequential

from keras.layers import Dense, Dropout, Activation, Flatten from keras.layers import Convolution2D, MaxPooling2D from keras.utils import np\_utils

from keras.utils.visualize\_util import plot

\# Image Size

img\_rows, img\_cols = 28, 28

\# Filter

nb\_filters = 32

\# Pooling

pool\_size = (2, 2)

\# Kernel kernel\_size = (3, 3)

\# Prepare dataset

(X\_train, y\_train), (X\_test, y\_test) = mnist.load\_data()

X\_train = X\_train.reshape(X\_train.shape\[0\], img\_rows, img\_cols, 1)

X\_test = X\_test.reshape(X\_test.shape\[0\], img\_rows, img\_cols, 1)

input\_shape = (img\_rows, img\_cols, 1)

X\_train = X\_train.astype('float32')

X\_test = X\_test.astype('float32')

X\_train /= 255

X\_test /= 255

nb\_classes = 10

Y\_train = np\_utils.to\_categorical(y\_train, nb\_classes)

Y\_test = np\_utils.to\_categorical(y\_test, nb\_classes)

\# CNN

model = Sequential() model.add(Convolution2D(nb\_filters, kernel\_size\[0\], kernel\_size\[1\], border\_mode='valid', input\_shape=input\_shape))

model.add(Activation('relu')) model.add(Convolution2D(nb\_filters, kernel\_size\[0\], kernel\_size\[1\])) model.add(Activation('relu'))

model.add(MaxPooling2D(pool\_size=pool\_size))

model.add(Dropout(0.25)) model.add(Flatten()) model.add(Dense(128))

model.add(Activation('relu')) model.add(Dropout(0.5)) model.add(Dense(nb\_classes)) model.add(Activation('softmax'))

\# Compilation model.compile(loss='categorical\_crossentropy', optimizer='adadelta', metrics=\['accuracy'\])

\# Training

batch\_size = 128

nb\_epoch = 1

model.fit(X\_train, Y\_train, batch\_size=batch\_size, nb\_epoch=nb\_epoch, verbose=1, validation data=(X\_test, Y\_test))

\# Evaluation

score = model.evaluate(X\_test, Y\_test, verbose=0)

print "Test Metrics:", zip(model.metrics\_names, score) plot(model, to\_file='s7.png', show\_shapes=True)

\# Output

\# Train on 60000 samples, validate on 10000 samples

\# Epoch 1/1

\# 60000/60000 \[==============================\] - 128s - loss: 0.3964 - acc: 0.8776 - val loss: 0.0929 - val\_acc: 0.9712

\# Test Metrics: \[('loss', 0.092853568810969594), ('acc', 0.97119999999999995)\]

 
|  || input: || (None. 128) |
| --- | --- | --- |
|  || output: || (None. 128) |

output:

r

| dense\_2; Dense || input: || (None. 128) |
| --- | --- | --- |
| output. || (None. 10) |

| convolulion2d\_input\_ 1: InputLaycr || input: || (None. 28. 28. 1) |
| --- | --- | --- |
| output || (None. 28.28. 1) |
|  ||  |
| convolution2d\_l: Convolution2D || input: || (None. 28. 28. 1) |
| output: || (None. 26. 26. 32) |

| activation. 1: Activation || input || (None. 26. 26. 32) |
| --- | --- | --- |
| output' || (None. 26. 26.32) |

| convolution2d\_2" Convolution2D || input: || (None.26.26.32) |
| --- | --- | --- |
| output- || (None. 24. 24. 32) |

| activation.?: Activation || input: || (None. 24.24.32) |
| --- | --- | --- |
| output\* || (None. 24. 24. 32) |

| max pool i ng 2d. 1: Max Pooh ng 2D || input: || (None. 24. 24. 32) |
| --- | --- | --- |
| output: || (None. 12. 12. 32) |

| dropout. 1: Dropout || input: || (None. 12.12.32) |
| --- | --- | --- |
| output: || (None. 12. 12.32) |
|  ||  |
|  || input: || (None. 12.12.32) |
|  || output: || (None. 4608) |

| dense.1: Dense || input: || (None. 4608) |
| --- | --- | --- |
| output: || (None. 128) |

| activation\_3: Activation || input. || (None. 128) |
| --- | --- | --- |
| output: || (None. 128) |

| activation\_4: Activation || input: || (None. 10) |
| --- | --- | --- |
| output. || (None. 10) |

Figure 7-5. CNN

Listing [7-7](#main-8.xhtml#bookmark22) presents the source code for the convolution neural network and Figure [7-5](#main-8.xhtml#bookmark23) illustrates the computation graph. The following points are to be noted:

*   1\. The overall network consists of two convolution-detector blocks, followed by a max pooling layer which in turn is followed by a two layer fully connected network (refer to Chapter [5](http://dx.doi.org/10.1007/978-1-4842-2766-4_5)).
    
*   2\.   The size of the kernel is 3 x 3.
    
*   3\.  The pooling operation is done over sections of dimensionality 2 x 2.
    
*   4\.  There are a number of dropout layers, which are basically a form of regularization (refer to Chapter [1](http://dx.doi.org/10.1007/978-1-4842-2766-4_1)) and operate by randomly turning off a certain number of units. The parameter 0.25 indicates the faction of inputs that will be randomly dropped.
    
*   5\.   The flatten layers convert the input of any dimensionality to a dimensionality of 1 x n. So, for instance, an input of dimensionality 2 x 2 x 3 gets converted to a directionality of 1 x 12.
    
*   6\.   The output layer is softmax and the loss function is categorical entropy, as is appropriate for a multiclassification problem (refer to Chapter [3](http://dx.doi.org/10.1007/978-1-4842-2766-4_3)).
    
*   7\.  The model is fit using adadelta (refer to Chapter [8](http://dx.doi.org/10.1007/978-1-4842-2766-4_8)) and, for the purposes of illustration, we set the epochs to 1 (ideally it's set to much more than that).
    

Listing 7-8. LSTM

import numpy as np

from keras.preprocessing import sequence from keras.utils import np\_utils from keras.models import Sequential from keras.layers import Dense, Dropout, Activation, Embedding from keras.layers import LSTM from keras.datasets import imdb

from keras.utils.visualize\_util import plot

max\_features = 20000 maxlen = 80 batch\_size = 32

\# Prepare dataset (X\_train, y\_train), (X\_test, y\_test) = imdb.load\_data(nb\_words=max\_features) X\_train = sequence.pad\_sequences(X\_train, maxlen=maxlen) X\_test = sequence.pad\_sequences(X\_test, maxlen=maxlen)

\# LSTM model = Sequential() model.add(Embedding(max\_features, 128, dropout=0.2)) model.add(LSTM(128, dropout\_W=0.2, dropout\_U=0.2)) model.add(Dense(1))

model.add(Activation('sigmoid'))

\# Compile model.compile(loss='binary\_crossentropy', optimizer='adam', metrics=\['accuracy'\])

\# Training

model.fit(X\_train, y\_train, batch\_size=batch\_size, verbose=1, nb\_epoch=1, validation\_ data=(X\_test, y\_test))

\# Evalaution

score = model.evaluate(X\_test, y\_test, batch\_size=batch\_size) print "Test Metrics:", zip(model.metrics\_names, score) plot(model, to\_file='s8.png', show\_shapes=True)

\# Output

\# Train on 25000 samples, validate on 25000 samples

\# Epoch 1/1

\# 25000/25000 \[==============================\] - 165s - loss: 0.5286 - acc: 0.7347 - val loss: 0.4391 - val\_acc: 0.8076

\# 25000/25000 \[==============================\] - 33s

\# Test Metrics: \[('loss', 0.43908300422668456), ('acc', 0.80759999999999998)\]

![](main-82.jpg)

Figure 7-6. LSTM

Let us now look at the construct Keras provides to build LSTM Networks, introduced in Chapter [6](http://dx.doi.org/10.1007/978-1-4842-2766-4_6) (refer to Listing [7-8](#main-8.xhtml#bookmark24) and Figure [7-6](#main-8.xhtml#bookmark25)). The data set we will be using is from IMDB and represents 25,000 reviews from IMDD categorized as positive or negative, making this a binary sequence classification problem. The data is preprocessed to contain only frequent words (the words are actually represented as integers). Listing [7-8](#main-8.xhtml#bookmark24) presents the source code and Figure [7-6](#main-8.xhtml#bookmark25) illustrates the computational graph. Keras provides a fairly high-level construct for LSTMs, which allows users to construct LSTM models.

## Summary

In this chapter we covered the basics of using Keras, using a number of small and simple examples. We encourage the reader to experiment with the examples. Keras has extensive documentation, which is recommended further reading.

CHAPTER 8

Stochastic Gradient Descent

![](main-83.png)

An essential step in building a deep learning model is solving the underlying optimization problem, as defined by the loss function. This chapter covers Stochastic Gradient Descent (SGD), which is the most commonly used algorithm for solving such optimization problems. We also cover a breadth of algorithmic variations published in academic literature which improve on the performance of SGD, and present a bag of largely undocumented tricks which will allow the user to go an extra mile. Lastly, we cover some ground on parallel/distributed SGD and touch on Second Order Methods for completeness.

Most of the examples presented in the accompanying code for this chapter are based on a Python package called downhill. Downhill implements SGD with many of its variations and is an excellent choice for experimenting.

## Optimization Problems

Simply put, an optimization problem involves finding the parameters which minimize a mathematical function. For example, given the function f(x)= 2 x, finding the value of x which minimizes the function is an optimization problem (refer to Figure [8-1](#main-9.xhtml#bookmark5)).

![](main-84.jpg)

Figure 8-1. An optimization problem involves finding the parameters that minimize a given function

© Nikhil Ketkar 2017

N. Ketkar, Deep Learning with Python, DOI 10.1007/978-1-4842-2766-4\_8

While the functions we want to minimize while building deep learning models are way more complicated (involving multiple parameters which may be scalars, vectors, or matrices), conceptually it's simply finding the parameters that minimize the function.

The function one wants to optimize for while building a deep learning model is referred to as the loss function. The loss function may have a number of scalar/vector/matrix-valued parameters but always has a scalar output. This scalar output represents the goodness of the model. Goodness, typically, means a combination of how well the model predicts and how simple the model is.

■ Note For now, we will stay away from the statistical/machine learning aspects of a loss function (covered elsewhere in the book) and focus purely on solving such optimization problems. that is, we assume that we have been presented with a loss function L(x ) where x represents the parameters of the model and the job at hand is to find the values for x which minimize L(x ).

## Method of Steepest Descent

Let us now look at a simple mathematical idea, which is the intuition behind SGD. For the sake of simplicity, let us assume that x is just one vector. Given that we want to minimize L(x), we want to change or update x such that L ( x ) reduces. Let u represent the unit vector or direction in which x should be ideally changed and let a denote the magnitude (scalar) of this step. A higher value of a implies a larger step in the direction u, which is not desired. This is because u is evaluated for the current value of x and it will be different for a different x.

Thus, we want to find a u such that

limL(x+au)

a®0

is minimized. It follows that

limL(x+«u) = u^T V[x]L(x).

Thus, we basically want to find a u such that

U VxL(x)

is minimized. Note that V[x] L (x) is the gradient of L(x).

Given that both u^T and V[x]L(x) are vectors, it follows that

u^T V[x]L(x) = |u|-|V[x]L(x)cosfl,

where 9 is the angle between the two vectors (refer to Figure[ 8-2](#main-9.xhtml#bookmark8)).

![](main-85.jpg)

The value of cos 0 would be minimized at q \= p, that is to say the vectors are pointing in the opposite direction. Thus, it follows that setting the direction u = - V[x]L(x) would achieve our desired objective. This leads to a simple iterative algorithm as follows:

Input: a, n

Initialize x to a random value.

For n steps do:

Update x = x-aV[x] L (x)

Output: x

## Batch, Stochastic (Single and Mini-batch) Descent

So far, we were denoting our loss function as L(x). The training data (examples) were implicit in this notation. For the purpose of this discussion, we need to make them explicit. Let us denote our training data as D = {{,d.-,,...d[n]}. Our loss function should now be denoted as LD(x). This simply means that the loss function is being evaluated with parameters x and with respect to a set of data points D. Let T be a subset of examples in D; then L[T](x) denotes the loss function evaluated over the set of examples T. Similarly, V[x]L[D][(]x[)]and V[x]L[T] (x) denote the gradients of the loss function L(x) computed over the sets of training data D and T, respectively.

■ Note For now, we will stay away from the computation of gradients of loss functions over subsets of data. these can be generated using automatic differentiation (covered elsewhere in the book) quite easily (even for arbitrary complicated loss functions) and need not be derived manually.

Armed with this notation, we can now discuss three variants of the steepest descent approach we discussed earlier.

### Batch

In this approach, the entire dataset D is used in the update step. That is, x is updated as x = x - V[x] LD (x). Two things are apparent about this approach. First, that it is expensive as it requires a computation over the entire dataset. Second, the update direction is the most accurate one, given our entire dataset.

### Stochastic Single Example

In this approach, only a single example from D is used in the update step. That is, x is updated as

x = x - V [x] L[S] (x) where |S| = 1. Note that we use a different example in each iteration chosen randomly (hence the term stochastic, which simply means having a random nature). Two things are apparent about this approach, too. First, that it is quite cheap as it requires a computation of the gradient over only a single example. Second, the update direction is not as accurate as we are only using a very small fraction of the training dataset.

### Stochastic Mini-batch

In this approach, only a small subset of examples from D is used in the update step. That is, x is updated as x = x - V[x] L[S] (x) where |S| < |\_D|. Note that we use a different set of examples in each iteration chosen randomly (hence the term stochastic).

### Batch vs. Stochastic

In practice, stochastic approaches dominate over batch approaches and are much more commonly used. A seemingly nonintuitive fact about stochastic approaches is that not only is the gradient over few examples cheaper to compute, not getting the exact direction (using only a small number of examples) actually leads to better solutions. This is particularly true for large datasets with redundant information wherein the examples are not too different from each other. Another reason for stochastic approaches performing better is the presence of multiple local minima with different depths. In a sense, the noise in the direction allows for jumping across the trenches while a batch approach will converge in the trench it started with.

## Challenges with SGD

Having covered the conceptual description of SGD, let us now consider the challenges of applying it to solving real world problems while build deep learning models.

### Local Minima

Local minima are suboptimal solutions (refer to Figure [8-3](#main-9.xhtml#bookmark23)) that trap any steepest descent approach and prevent the iterative procedure for making progress towards a better solution.

![](main-86.jpg)

### Saddle Points

Saddle points are points (refer to Figure[ 8-4](#main-9.xhtml#bookmark26)) where the gradient evaluates to zero but the point is not a local minimum. Saddle points are any steepest descent approach and prevent the iterative procedure for making progress towards a better solution. There is good empirical evidence that saddle points are much more common than local minima when it comes to optimization problems in a high number of dimensions (which is always the case when it comes to building deep learning models).

![](main-87.jpg)

### Selecting the Learning Rate

The a is the earlier discussion which represents the magnitude (scalar) of the step (in the direction u) is taken in each iteration so as to update x. This a is commonly referred to as the learning rate and it has a big impact on finding good solutions to the optimization problem (refer to Figure [8-5](#main-9.xhtml#bookmark29)). Too high a learning rate can cause the solution to bounce around and too low a learning rate means slow convergence (implying not getting to a good solution in a given number of iterations). When it comes to loss functions with many parameters trained on sparse datasets, a single global learning rate for all parameters makes the problem of choosing a learning rate even more challenging.

Too High

![](main-88.jpg)

Just Right

![](main-89.jpg)

Too Low

![](main-90.jpg)

Figure 8-5. Learning rate needs to be set properly

### Slow Progress in Narrow Valleys

Another problem inherent to steepest descent is the slow progress in narrow valleys generated due to badly scaled datasets. Progress slows down drastically as we get closer to the solution (refer to Figure[ 8-6](#main-9.xhtml#bookmark32)).

![](main-91.jpg)

Figure 8-6. Slow progress in narrow valleys

## Algorithmic Variations on SGD

We will now cover a number of algorithmic variations for SGD proposed in academic literature that address the challenges discussed earlier.

### Momentum

Consider the update step for SGD described earlier,

x = x\-a V[x]L(x).

The intuition behind momentum is to use a fraction of the previous update for the current update. That is, let u[s] denote the update to the parameters x in step s. Similarly, let u[s-1] denote the update in the previous step. Now, let us update x with

^Us \= Y^Us-1 +^a^Vx^L (\*).

That is, we update

x=x-us

instead of

x = x\-a V[x]L(x).

x — a\\7L(x)

![](main-92.jpg)

Figure 8-7. Momentum steering

Simply put, we have used a faction of the update in the previous step for the current update. This idea is referred to as momentum, as it is akin to the momentum acquired by a ball rolling downhill. A ball that has picked up momentum will bounce out of small ditches (local minima) along the way and reach the bottom of the hill. It will also keep up somewhat with the speed of previous downhill movement even if the hill has a much reduced slope (because it has picked up momentum). The momentum term basically causes new step direction to be biased by the step previous direction (refer to Figure [8-7](#main-9.xhtml#bookmark37)). Use of momentum has been empirically shown to cause reduced oscillation and faster convergence.

### Nesterov Accelerated Gradient (NAS)

Using the same notation as before, the Nesterov accelerated gradient is basically updating x with

^Us \= g^Us-1 ^+^a^V x^L (^(\-)g^Us-1).

That is, we update x=x-u[s].

The intuition behind this is looking one step ahead. That is, we first take a step in the direction of the accumulated gradient and do an adaptation. The intuition behind NAS is looking ahead and anticipating, which leads to better solutions (refer to Figure [8-8](#main-9.xhtml#bookmark40)).

![](main-93.jpg)

### Annealing and Learning Rate Schedules

When gradient descent approaches a minimum, we have seen how a bad learning rate can cause it to oscillate around the minima (see Figure [8-5](#main-9.xhtml#bookmark29)). Annealing refers to reducing the learning rate as it approaches the minima. This can be done manually (stopping the gradient descent and restarting from the same point with a reduced learning rate) or via learning rate schedules which introduce a number of user-controlled hyper parameters which dictate how the learning rate is reduced based on the number of steps taken. However, it must be noted that we are using the same learning rate for all the parameters, which may not be appropriate; a per-parameter learning rate adjustment is desired.

### Adagrad

The Adagrad algorithm adjusts the learning rate for each parameter. So far, we have been denoting the parameters of the loss function as x. Note that x is actually a large number of parameters, each of which is being updated with the same learning rate. Let x[i] denote one of the parameters and let g[i]^s denote the gradient for x. at step s. For steps 0,1,...,S\-1 we have a corresponding series of gradients g0,g0,^,g[t]^s.

Let

G = (gi )² + (g1 )² +...+((“ )

which is basically the sum of squares of the gradients for each step up to the previous step. The update rule in Adagrad is

^aS

^xi = ^xi -  1 gi.

G²

The a term is the global learning rate, which gets adapted for each parameter based on the previous gradients. It must also be noted that as G accumulates, the learning rate slows down for each parameter and eventually no progress can be made, which is a weakness of Adagrad.

### RMSProp

The RMSProp algorithm improves on the Adagarad algorithm's weakness of completely halted progress beyond a certain number of iterations. The intuition here is to use a window of fixed size over the gradients computed at each step rather than use the full set of gradients. That is, compute G over only the past W steps. Now, it's conceptually equivalent but computationally cheaper to treat the computation of

[n]                   +^+((S^(\-1))²

G =----------------------

W

as the accumulation of exponentially decaying average of square of gradients rather than store all values of

g-, gr¹,., g\-² g\-¹

and compute G at each step. That is, we compute

^E \[te^()2 \]) \=r^E \[te^()2 \] +()i^(\-)r)^)g'i)

where p is the decay.

Now, note that in Adagrad we were computing the update as

1

x[t] = x[i] - i gf. Consider the value of G². We can see that this is simply the root-mean-square of g, that is G G

RMS \[&\] = G² \=\\ E \[(&)² J.

Thus, we can compute the update as

^aS

^x\=^x ^(\-       )^g.

### Adadelta

The intuition behind Adadelta is to consider whether the unit of the parameter and the update to the parameter is the same. The author of the Adadelta argues that this is not the same in the case of any first order methods like steepest descent (but is the same in the case of second order methods like Newton's method). In order to fix this issue, the proposed update rule of Adadelta is

[x] = [x] ^(RMS) \[Dx, \]^S^(\-1)

'  ■^(\-) RMS \[rf \*

where RMS\[Dx\]^S^(\-1) is the root-mean-square of the actual updates to x. Note that RMS\[Dx[i]\]^S^(\-1) lags behind RMS\[g[i]\]^S by one step.

### Adam

Adam computes the updates by maintaining the exponentially weighted averages of both g[i] and (g[i])² for each parameter (denoted by the subscript i). The update rule for Adam is

![](main-94.jpg)

It is important to note that E\[g^f^(\-1) J and E\[(gf^(\-1)) \] are biased towards zero in the initial steps for small decay rates (there are two decay rates here—one for E \[gf^(\-1) J and one for E \[(gf^(\-1)) \] —which we denote by p[1] and p[2] respectively). This bias can be corrected by computing

![](main-95.jpg)

and

![](main-96.jpg)

respectively.

### Resilient Backpropagation

The intuition behind Resilient Backpropagation is that the sign of the gradient switches back and forth between positive and negative when the learning rate is too high (refer to Figure [7](http://dx.doi.org/10.1007/978-1-4842-2766-4_5%23Fig8)). The key idea is to keep track of the sign of the previous gradient and match it with the current gradient. If the sign is the same, use a higher learning rate and, if different, use a lower learning rate. Note that this is done for every parameter. The hyper parameters include the amounts to increase and decrease the learning rate (in case the sign matches or does not match, respectively).

### Equilibrated SGD

Equilibrated SGD aims to address issues SGD experiences with saddle points. The key idea here is that we need second order information (second derivatives of the loss function) to get out of the trap of a saddle point. The update rule for Equilibrated SGD is given by x[t] = x[t] —gi where D? = p D ¹ +(1 \-p}(H[d])²

ii[S] i i i d

(exponentially weighted average) and H[d] is the diagonal of the Hessian matrix of L(x) (computed symbolically) evaluated at x e N(0,1) (normal distribution with 0 mean and standard deviation of 1).

## Tricks and Tips for using SGD

We will now cover a number of tricks and tips for SGD proposed in academic literature that address the challenges discussed earlier.

### Preprocessing Input Data

It is of utmost importance that data is scaled well so as to ease the optimization (refer to Figure [8-6](#main-9.xhtml#bookmark32)). A good rule of thumb is to standardize the data by subtracting the mean and divide by the standard deviation to scale the data. So, if X = { [1], X[2] ...X[n] } is one of the input variables, we transform the data so that

Xi =        .

s

In case of sparse data (most of X[i] are equal to zero), the standardization process will cause the data to become dense, max-abs scaling where

[X]. = N .

^i max (X )

Scaling the feature to have a unit norm is another approach to scaling data.

It is also a good practice to remove linear correlations amongst input variables from input data using Principal Component Analysis.

### Choice of Activation Function

Common examples of activation function are the standard logistic function f (x) =—¹— and the

[1+] [e]^(\-)^x

hyperbolic tangent function f (x )= tanh(x ). A recommended approach is to use an activation function that is symmetrical around 0 (rather than only positive or negative), for instance, f (x ) \= 1.7159tanh 2 [x] 0. It is also recommended that a small linear term be added to prevent flat sports, f(x)= tanh(x)+ax.

### Preprocessing Target Value

While target values can be binary (0,1) in many cases, it is advisable to transform the target variable to values that lie within the range (not asymptotically, but practically) of the activation functions used to define the loss function. Not doing so leads to parameters being updated to higher and higher values without achieving any effect (on the output label). However, if the value of the target label is being used as a measure of confidence, then the labels which have been unnecessarily pushed to higher values are bad estimates of the confidence. While 0 and 1 may be extreme values for the activation function, it is also important not to choose targets that lie in the linear region of the activation function. A recommended approach is to choose values that maximize the second derivative of the activation function, for instance, ±1 for f (x) = 1.7159tanh| ²x

### Initializing Parameters

It is a recommended practice to initialize parameters randomly (normal distribution, zero-mean, unit variance). Another recipe for neural networks where the activation function is f (x) \= 1.7159tanh 2 [x]

(and the data is standardized) is to set weights to m ² where m is the fan-in (the number of connections feeding into the node).

### Shuffling Data

It is recommended practice to shuffle input data, as it may be in a particular order and hence might bias the SGD. A rare exception to this is Curriculum Learning wherein examples are presented in a meaningful order (increasing difficulty of prediction).

### Batch Normalization

While our parameters are initialized in a way such that they are normalized (set randomly, normal distribution, zero-mean, and unit variance), they do not remain normalized over the update steps. Batch normalization renormalizes parameters after each batch (refer to batch SGD).

### Early Stopping

Early stopping basically involves measuring the loss on an unseen (unused for SGD) subset of training data (called validation data) and stopping when there is no change observed in the loss. Typically, there are two hyper parameters introduced: one which determines whether the change is significant (any change in loss less than this value is treated as not a change) and a patience parameter, which is the number of times a no change step can be taken before the iterative procedure terminates.

### Gradient Noise

The gradient noise trick introduces a mean centered noise, N(0,s) in every update step. Here, a is a hyper parameter and the gradient is computed as g[i] = g[i] + N (0,ct).

## Parallel and Distributed SGD

We now cover two parallel and distributed approaches for SGD. SGD in its basic form is a sequential algorithm and convergence can be very slow on large data sets and models with a large number of parameters. Parallel and distributed approaches have a great impact when it comes to dealing with large volumes of training data (in the order of billions) and a large number of model parameters (in the order of millions).

### Hogwild

Consider the update step of the SGD procedure. What makes the algorithm inherently sequential is update step x = x\-a V[x]L(x). Let's say that we want to employ multiple threads of computation to make the iteration faster. Since we want only one thread to do this (do the update one step at a time), we would place a lock around this step (to prevent a race condition). Once we do that, this essentially becomes a sequential algorithm; no matter how many cores and threads we devote to the process, only one thread is actually doing the work, while all others are waiting on a lock.

The intuition behind Hogwild is that the race condition caused by not placing a lock on the update step does not lead to much inconsistency in updates when the optimization problem is sparse. This is simply because each update step touches only a few parameters. The authors of Hogwild provide strong theoretical and empirical evidence for this finding and the gains on large datasets are significant. Hogwild is easy to implement on multi-core CPUs and GPUs.

### Downpour

Downpour is a distributed algorithm for SGD that consists of two key moving parts: model replica and parameter server (refer to Figure [8-9](#main-10.xhtml#bookmark6)). A model replica is a set of machines that operates on a subset of data, where every machine operates only on a subset of parameters. There are many such model replicas, each operating on a different subset of a large dataset. The parameter server is a set of machines that maintains a common global state of the model. Model replicas retrieve the global state from the parameter server, update the model based on the subset of data and update the global state. Note that the fetch and update of the global state does not happen at every iteration. There are two levels of distribution with Downpour. First, the model parameters (what we have been denoting as x so far) are split across multiple machines in each model replica. Second, the data is split amongst model replicas. So, essentially, each machine is doing the gradient update step on a subset of model parameters, using a subset of data. The global state is updated asynchronously. In spite of the apparent inconsistencies introduced by Downpour, it has been found to be very effective when it comes to training a large model with large amounts of data.

![](main-97.jpg)

Figure 8-9. Downpour

## Hands-on SGD with Downhill

We will now a hands-on exercise with SGD using a Python package called Downhill. Downhill implements SGD with many of its variants. It operates on loss functions defined in Theano, which makes it a very convenient tool to play with SGD variants on arbitrary loss functions defined in Theano. Let us start with generating a dataset for our exercise (Listing [8-1](#main-10.xhtml#bookmark9), Figure [8-10](#main-10.xhtml#bookmark10)).

Listing 8-1. Generating data for our excercise

#Specifiy the number of examples we need (5000) and the noise level train\_X, train\_y = sklearn.datasets.make\_moons(5000, noise=0.1)

#One hot encode the target values train\_y\_onehot = numpy.eye(2)\[train\_y\]

#Plot the data pylab.scatter(train\_X\[:-1000, 0\], train\_X\[:-1000, 1\], c=train\_y\[:-1000\], cmap=pylab. cm.Spectral)

This should produce a plot of the dataset we generated. The objective at hand is to train a model to distinguish between the red and blue dots.

![](main-98.jpg)

Figure 8-10. Dataset for our experiments

Next let's define a loss function with Theano.

Listing 8-2. Defining the loss function

#Set Seed numpy.random.seed(0)

num\_examples = len(train\_X)

#Our Neural Network nn\_input\_dim = 2 nn\_hdim = 1000 nn\_output\_dim = 2

#Regularization

reg\_lambda = numpy.float64(0.01)

#Weights and bias terms

W1\_val = numpy.random.randn(nn\_input\_dim, nn\_hdim) b1\_val = numpy.zeros(nn\_hdim)

W2\_val = numpy.random.randn(nn\_hdim, nn\_output\_dim) b2\_val = numpy.zeros(nn\_output\_dim)

X = T.matrix('X')

y = T.matrix('y')

W1 = theano.shared(W1\_val, name='W1')

b1 = theano.shared(b1\_val, name='b1')

W2 = theano.shared(W2\_val, name='W2') b2 = theano.shared(b2\_val, name='b2') batch\_size = 1 #Our Loss function

z1 = X.dot(W1) + b1

a1 = T.tanh(z1)

z2 = a1.dot(W2) + b2

y\_hat = T.nnet.softmax(z2)

loss\_reg = 1./batch\_size \* reg\_lambda/2 \* (T.sum(T.sqr(W1)) + T.sum(T.sqr(W2))) loss = T.nnet.categorical\_crossentropy(y\_hat, y).mean() + loss\_reg prediction = T.argmax(y\_hat, axis=1) predict = theano.function(\[X\], prediction)

■ Note For now, we will stay away from the details of defining loss functions with theano (covered elsewhere in the book).

Next we set up a simple SGD using Downhill. We use all default parameters and want do 10K iterations. The patience parameter is set to 10K also so that early stopping (described earlier in the chapter) does not kick in.

Listing 8-3. SGD

#Store the training and vlidation loss train\_loss = \[\] validation\_loss = \[\]

opt = downhill.build('sgd', loss=loss)

#Set up training and validation dataset splits, use only one example in a batch #and use only one batch per step/epoc

#Use everything except last 1000 examples for training

train = downhill.Dataset(\[train\_X\[:-1000\], train\_y\_onehot\[:-1000\]\], batch\_size=batch\_size, iteration\_size=1)

#Use last 1000 examples for valudation valid = downhill.Dataset(\[train\_X\[-1000:\], train\_y\_onehot\[-1000:\]\])

#SGD iterations = 0 for tm, vm in opt.iterate(train, valid, patience=10000):

iterations += 1

\# Record the training and validation loss train\_loss.append(tm\['loss'\]) validation\_loss.append(vm\['loss'\])

if iterations > 10000: break

We can now visualize the decision boundary over the training (Figure [8-11](#main-10.xhtml#bookmark11)) and validation (Figure [8-12](#main-10.xhtml#bookmark12)) sets, and the loss (Figure [8-13](#main-10.xhtml#bookmark13)).

![](main-99.jpg)

Figure 8-11. Decision boundary over training set

![](main-100.jpg)

Figure 8-12. Decision boundary over validaton set

![](main-101.jpg)

Listing 8-4. Using SGD variants implemented in Downhill

def build\_model(algo): loss\_value = \[\]

W1.set\_value(W1\_val)

b1.set\_value(b1\_val)

W2.set\_value(W2\_val)

b2.set\_value(b2\_val)

opt = downhill.build(algo, loss=loss)

train = downhill.Dataset(\[train\_X\[:-1000\], train\_y\_onehot\[:-1000\]\], batch\_size=1, iteration\_size=1)

valid = downhill.Dataset(\[train\_X\[-1000:\], train\_y\_onehot\[-1000:\]\]) iterations = 0

for tm, vm in opt.iterate(train, valid, patience=1000): iterations += 1 loss\_value.append(vm\['loss'\]) if iterations > 1000:

break return loss\_value

algo\_names = \['adadelta', 'adagrad', 'adam', 'nag', 'rmsprop', 'rprop', 'sgd'\] losses = \[\]

for algo\_name in algo\_names:

print algo\_name

vloss = build\_model(algo\_name) losses.append(numpy.array(vloss))

1-------------------------

*   \-  adadelta
    
*   \-  adagrad
    
*   \- adam
    

nag rmsprop rprop sgd

0          200         400         600

Figure 8-14. Learning curves (over validation data)

800

1000

Let us now try out a number of SGD variants implemented in Downhill (Listing [8-4](#main-10.xhtml#bookmark14)) and visualize the learning curves (Figure [8-14](#main-10.xhtml#bookmark15)). We will be running Adadelta, Adagrad, Adam, Nesterov Accelerated Gradient (NAG), RMSProp, Resilient Backpropagation, and vanilla SGD as before. We run all these algorithms with default parameters for 1000 steps.

## Summary

In this chapter we covered Stochastic Gradient Descent (SGD), the weaknesses of SGD, a number of algorithmic variations to address these weaknesses, and a number of tricks to make SGD effective. SGD is the most common approach to train deep learning models. The reader is advised to go over the examples in the source code listings and also look at the implementations of SGD and its variants in the Downhill package for further clarity and perspective.

One important aspect that we did not cover in this chapter is how gradients for arbitrary loss functions (required for SGD) are computed. This is covered in the next chapter on automatic differentiation.

CHAPTER 9

Automatic Differentiation

![](main-102.png)

In the chapter on Stochastic Gradient Descent, we treated the computation of gradients of the loss function V[x] L (x) as a black box. In this chapter we open this black box and cover the theory and practice of automatic differentiation. Automatic differentiation is a mature technology that allows for the effortless and efficient computation of gradients of arbitrarily complicated loss functions. This is critical when it comes to minimizing loss functions of interest; at the heart of building any deep learning model lies an optimization problem, which is invariably solved using stochastic gradient descent, which in turn requires one to compute gradients.

Most of the applications in this chapter are based on the Python package Autograd, which provides a mature set of capabilities for automatic differentiation.

Automatic differentiation is distinct from both numerical and symbolic differentiation, and we start by covering enough about both of these so that distinction becomes clear. For the purposes of illustration, assume that our function of interest is f: R ® R and we intend to find the derivative off denoted by f (x).

## Numerical Differentiation

Numerical differentiation in its basic form follows from the definition of derivative/gradient. So, given that

we can compute the f (x) using the forward difference method as

f ■(«)= D+<J,) = ^f^(^X^+\>')^f <^X\>,

setting a suitably small value for h. Similarly, we can compute f(x) using the backward difference method as

f  ) = D \_ (h ) = ^f ^(^X^()-)(^(^X ^(\-) ^h >,

© Nikhil Ketkar 2017

N. Ketkar, Deep Learning with Python, DOI 10.1007/978-1-4842-2766-4\_9

again by setting a suitably small value for h. A more symmetric form is the central difference approach, which computes f as

![](main-103.jpg)

2h

A further development over this idea is Richardson's extrapolation

f '([x]) \= ⁴D^((h)^) Do^((2)^h^)

The approximation errors for forward and backward differences are in the order of h, that is, O(h), while those for central difference and Richardson's approximation are O(h²) and O(h⁴) respectively.

The key problems with numerical differentiation are the computational cost, which grows with the number of parameters in the loss function, the truncation errors, and the round off errors. The truncation error is the inaccuracy we have in the computation off(x) due to h not being zero. The round off error is inherent to using floating point numbers and floating point arithmetic (as against using infinite precision numbers, which would be prohibitive expensive).

Numerical differentiation is thus not a feasible approach for computing gradients while building deep learning models. The only place where numerical differentiation comes in handy is quickly checking if gradients are being computed correctly. This is highly recommended when you have computed gradients manually or with a new/unknown automatic differentiation library. Ideally, this check should be put in as an automated check/assertion before staring SGD.

■ Note numerical differentiation is implemented in a python package called Scipy. We do not cover it here, as it is not directly relevant to deep learning.

## Symbolic Differentiation

Symbolic differentiation in its basic form is a set of symbol rewriting rules applied to the loss function to arrive at the derivatives/gradients. Consider two of such simple rules:

![](main-104.jpg)

and

![](main-105.jpg)

dx

Now, given a function like f(x)=2x³+x², we can successively apply the symbol writing rules to first arrive at

![](main-106.jpg)

by applying the first rewriting rule and f '(x) = 6x² + 2x by applying the second rule. Symbolic differentiation is thus automating what we do when we derive gradients manually. Of course, the number of such rules can be large, and more sophisticated algorithms can be leveraged to make this symbol rewriting more efficient. However, in its essence, symbolic differentiation is simply the application of a set of symbol rewriting rules. The key advantage of symbolic differentiation is that it generates a legible mathematical expression for the derivative/gradient that can be understood and analyzed.

The key problem with symbolic differentiation is that it is limited to the symbolic differentiation rules already defined, which can cause us to hit roadblocks when trying to minimize complicated loss functions. An example of this is when your loss function involves an if-else clause or a for/while loop. In a sense, symbolic differentiation is differentiating a (closed form) mathematical expression; it is not differentiating a given computational procedure.

Another problem with automatic differentiation is that a naive application of symbol rewriting rules, in some cases, can lead to an explosion of symbolic terms (expression swell) and make the process computationally unfeasible. Typically, a fair amount of compute effort is required to simplify such expressions and produce a closed form expression of the derivative.

■ Note Symbolic differentiation is implemented in a python package called Sympy. We do not cover it here, as it is not directly relevant to deep learning.

## Automatic Differentiation Fundamentals

The first key intuition behind automatic differentiation is that all functions of interest (which we intend to differentiate) can be expressed as compositions of elementary functions for which corresponding derivative functions are known. Composite functions, thus can be differentiated by applying the chain rule for derivatives. This intuition is also at the basis of symbolic differentiation.

The second key intuition behind automatic differentiation is that, rather than storing and manipulating intermediate symbolic forms of derivatives of primitive functions, one can simply evaluate them (for a specific set of input values) and thus address the issue of expression swell. Since intermediate symbolic forms are being evaluated, we do not have the burden of simplifying the expression. Note that this prevents us from getting a closed form mathematical expression of the derivate like the one symbolic differentiation gives us; what we get via automatic differentiation is the evaluation of the derivative for a given set of values.

The third key intuition behind automatic differentiation is that, because we are evaluating derivatives of primitive forms, we can deal with arbitrary computational procedures and not just closed form mathematical expressions. That is, our function can contain if-else statements, for-loops, or even recursion. The way automatic differentiation deals with any computational procedure is to treat a single evaluation of the procedure (for a given set of inputs) as a finite list of elementary function evaluations over the input variables to produce one or more output variables. While there might be control flow statements (if-else statements, for-loops, etc.), ultimately, there is a specific list of function evaluations that transform the given input to the output. Such a list/evaluation trace is referred to as a Wengert list.

Let us set the stage for discussing automatic differentiation by introducing a simple function

1

f (Xj, x[2])=(² + x[2]²).Figure[ 9-1 ](#main-10.xhtml#bookmark25)shows the computational graph for the function. Note that we also introduce some intermediate variables for convenience.

![](main-107.png)

(X

Square

s\_\_\_\_\_\_\_\_\_\_\_J

\---------------------->1

Square

v\_\_\_\_\_\_\_\_/

![](main-108.png)

f(x-i,X2) = (xf +X%)1

Plus

I

V[3] = Vl + V2

£

Sqrt

Figure 9-1. A simple function and its computational graph

### Forward/Tangent Linear Mode

The forward mode (also called tangent linear mode) of automatic differentiation associates each

dv

intermediate variable in the computational graph with a derivative. More formally, we have V =—for all ' dx

values of i where v[t] is the derivative of the intermediate variable v. with respect to an input variable/other intermediate variable x. Figure[ 9-2](#main-10.xhtml#bookmark28) illustrates this for the example function we introduced earlier.

X2 x[2]

I

vi = xi ■ —— = xi • 2xi Vl — oxi

\\

/                -S

Square

f^x[1],x[2]) = (z? + ^2)2

9   .     . dv[2]

V[2]^x[2] V2 = X[2].^

— X[2] \* 2^2

![](main-109.png)![](main-110.png)

f 3 = Vi + V 2  ^3 = Vi + V2

I

/        \\

Sqrt

\\\_\_\_\_\_\_\_\_\_/

Given such an augmented computational graph, we can evaluate the value of the (partial) derivative of the given function with respect to a particular variable (and a set of inputs) by evaluating the expressions associated with the augmented computational graph. For this evaluation, we have values for all the input variables and we set all the values of the derivatives of the input variables to 0, except for the variable for which we intend to evaluate the partial derivative, which we set to 1. Figures [9-3](#main-10.xhtml#bookmark29) and [9-4](#main-10.xhtml#bookmark30) illustrate such an evaluation of the computational graph.

I

Vl = xf

\\

![](main-111.png)

V[2] = 4

t>2 = 0

/(^1,^2) = +^)2

\= rri(a?i \+ x%)~^

 
| ±1 = 1        x[2] = 2Input£1 = 1      ±2=0 |
| --- |

V4 = V3 i>4 = 2.23

output                 -y[4] = 0.44

Figure 9-3. Computing the derivative (partial with respect to x[1]) for a particular set of values of x[1] and x[2]

![](main-112.jpg)

f(x[1],x[2]) = (xl +a?l)2 ^x[1]f(.Xl,X[2]) = X!(X1 +x%)~%

<------------

Output

/---------\\

Plus

I\_\_\_\_\_\_\_\_\_\_/

1

v[3] = Vi + v[2]

1

f 3 = 5

V3 = 4

Sqrt

I\_\_\_\_\_\_\_\_\_/

![](main-113.png)

v[4] = 2.23

i>4 = 0.89

Figure 9-4. Computing the derivative (partial with respect to x[2]) for a particular set of values of x[1] and x[2]

It must be noted that with forward mode automatic differentiation we need to perform one evaluation of the augmented computational graph for computing the partial derivative with respect to each input variable. It follows that for computing the gradient for a function with respect to n input variable we would require n evaluations. Thus, forward mode automatic differentiation is expensive when it comes to computing gradients for functions with a lot of input variables, which is a common case in deep learning where loss functions consist of many input variables and a single output variable.

It is also clear that forward mode automatic differentiation is a fairly straightforward application of the chain rule and can be implemented easily using operator overloading. Forward mode automatic differentiation is often implemented by the use of dual numbers, which are defined as a truncated Taylor series of the form v + ve. Arithmetic on dual numbers can be defined using e² = 0 and treating a non-dual number as v+0v. Dual numbers, in a sense, carry the derivative with them throughout their lifetime. Thus, given that we have a complete implementation of dual numbers, the derivatives can simply be computed as a side/parallel effect of the operations on the dual component.

### Reverse/Cotangent/Adjoint Linear Mode

The reverse mode (also called cotangent linear mode or adjoint mode) of automatic differentiation also associates each intermediate variable in the computational graph with a derivative computed backward \_ dy[i]

from the output. This bears a striking resemblance to backpropagation. More formally, we have v[i] =^-^L for \_                                                                 dV

all values of i where v[i] is the derivative of the output/intermediate variable y. for all values of i. Figure[ 9-5](#main-10.xhtml#bookmark33) illustrates this for the example function we introduced earlier.

To evaluate the derivative, we first do a forward pass over the augmented computational graph as shown in Figure [9-6](#main-10.xhtml#bookmark34). This is followed by a reverse pass in which the derivatives are computed, which is illustrated in Figure [9-7](#main-10.xhtml#bookmark35).

Reverse mode automatic differentiation computes all the partial derivatives in a single forward pass and a single reverse pass and thus scales well with respect to functions with many input variables common to loss functions in deep learning.

![](main-114.jpg)

X[2]

X2 =        = V[2] - 2x[2]

0X2

\_    \_   0v[3]   \_  -

Vl = V3 •     = V3 • 1

OV1

f(xi,x[2]) = (xi + X&

I

Vi = xf

\\

I

V2 = xl

\-    \_  &v[3]

«2 = V[3] ■     = V[3] ■ 1

OV2

Plus

1

V[3] = Vl + V[2]

![](main-115.jpg)

I

Z         X

Sqrt

x.\_\_\_\_\_\_\_\_\_\_\_\_z

I

1 \_

«4 =

Figure 9-5. Associating every intermediate variable with a derivative in reverse mode automatic differentiation

| / ||  |
| --- | --- |
| Xi = 1X || X2 = 2 || Input || y |

Z--------X

Square

.\_\_\_\_\_\_\_\_\_\_\_\_\_.

Square

x\_\_\_\_\_\_\_\_J

/Oi, rr[2]) = (xl + x^)?

![](main-116.png)![](main-117.png)

Figure 9-6. Forward pass of reverse mode automatic differentiation

![](main-118.jpg)

r         \\

Square

I\_\_\_\_\_\_\_\_\_J

|  ||  ||  ||  ||  |
| --- | --- | --- | --- | --- |
| xi = 0.44 a?i || x[2]$2 = 0.89 || Output |
|  ||  ||  ||  ||  |

![](main-119.png)

®i = 0.22

V1 = T?

V[2] = i>2 ^(\=) 0.22

![](main-120.jpg)![](main-121.jpg)![](main-122.jpg)

«3 = fl + f 2 S3 = 0.22

\= («? +^2)"

V[xi]/(xi,a:2) = X!(x^+x^)~i

V[X2]f(xi,X2) = x[2](x^ + x%)~i

Sqrt

I\_\_\_\_\_\_\_\_J

Input

«4 — 1

Figure 9-7. Backward pass of reverse mode automatic diffrentiation

### Implementation of Automatic Differentiation

Let us now take a look at how Automatic Differentiation is commonly implemented. The three key approaches are using source code transformation and operator overloading (explicit or implicit dual number implementation).

#### Source Code Transformation

The source code transformation approach involves the user implementing the loss function in a regular programming language and then using an automatic differentiation tool to generate the corresponding gradient function. These two can then be compiled by the standard build tool chain to be used as part of a larger application. Refer to Figure [9-8](#main-10.xhtml#bookmark40).

![](main-123.png)

Figure 9-8. Source Code Transformation

#### Operator Overloading

The operator overloading approach basically is an explicit/implicit implementation of the dual number approach wherein the corresponding differentiation operation is implemented for every primitive operation of interest. Users implement their loss functions using the primitive operations and the computation of the gradients happen by the invocation of the overloaded method implementing the differentiation operation. Refer to Figure [9-9](#main-10.xhtml#bookmark43).

2x

![](main-124.png)

Invoke for gradient function computation

![](main-125.png)

Operator Implementation

Invoke for loss function computation

X.

![](main-126.png)

Square Operation

![](main-127.png)

Figure 9-9. Operator Overloading

■ Note one key implementation detail surrounding the operator overloading approach is whether the operators in question are those already implemented in established library/core language or if the automatic differentiation tool provides its own operators. autograd is an example an automatic differentiation tool that overloads the established numpy Library whereas theano provides its own operators for which corresponding differential operations are implemented.

## Hands-on Automatic Differentiation with Autograd

We will now do a hands-on exercise with Automatic Differentiation using a Python package called Autograd. Autograd implements Reverse mode automatic differentiation and can compute derivatives for arbitrary Python and Numpy code.

Listing9-1. Finding gradient for f (, x[2])=( + x2)²

#Wrapper Around Numpy

import autograd.numpy as numpy

#Function to generate gradients

from autograd import grad

#Define the function

def f(x1, x2): return numpy.sqrt(x1 \* x1 + x2 \* x2)

#Compute the gradient w.r.t the first input variable x1 g\_x1\_f = grad(f,0)

#Compute the gradient w.r.t the second input variable x2 g\_x2\_f = grad(f,1)

#Evaluate and print the value of the function at x1=1, x2=2 print f(1,2)

#Produces 2.23

#Evaluate and print the value of the gradient w.r.t x1 at x1=1, x2=2 print g\_x1\_f(1,2)

#Produces 0.44

#Evaluate and print the value of the gradient w.r.t x2 at x1=1, x2=2 print g\_x2\_f(1,2)

#Produces 0.89

Let us get started by taking the function that we have used for discussion throughout this chapter,

J.

f (x[1], x[2])=( + x2)²,and finding the gradient. As will be apparent, Autograd makes this really easy. Listing [9-1](#main-11.xhtml#bookmark2) illustrates this.

Autograd provides a utility function to check the correctness of the computed gradients. Listing [9-2](#main-11.xhtml#bookmark3) illustrates this. It is a good idea to conduct such checks, especially when we are computing gradients for complicated loss functions involving control flow statements.

Listing9-2. Checking the gradient for f (x[1], x[2])=( + x²[2] )²

from autograd.util import quick\_grad\_check

#Define the function

def f(x1, x2): return numpy.sqrt(x1 \* x1 + x2 \* x2)

#Computes and checks the gradient for the given values

quick\_grad\_check(f,1.0,extra\_args=\[2.0\])

#Output

#

#Checking gradient of <function f at 0x10504bed8> at 1.0

#Gradient projection OK

#(numeric grad: 0.447213595409, analytic grad: 0.4472135955)

Listing 9-3. Logistic Regression using Autograd

import pylab

import sklearn.datasets import autograd.numpy as np from autograd import grad

\# Generate the data

train\_X, train\_y = sklearn.datasets.make\_moons(500, noise=0.1)

\# Define the activation, prediction and loss functions for Logistic Regression def activation(x):

return 0.5\*(np.tanh(x) + 1)

def predict(weights, inputs):

return activation(np.dot(inputs, weights))

def loss(weights):

preds = predict(weights, train\_X) label\_probabilities = preds \* train\_y + (1 - preds) \* (1 - train\_y) return -np.sum(np.log(label\_probabilities))

\# Compute the gradient of the loss function gradient\_loss = grad(loss)

\# Set the initial weights weights = np.array(\[1.0, 1.0\])

\# Steepest Descent loss\_values = \[\] learning\_rate = 0.001 for i in range(100):

loss\_values.append(loss(weights))

step = gradient\_loss(weights) weights -= step \* learning\_rate

\# Plot the decision boundary

x\_min, x\_max = train\_X\[:, 0\].min() - 0.5, train\_X\[:, 0\].max() + 0.5 y\_min, y\_max = train\_X\[:, 1\].min() - 0.5, train\_X\[:, 1\].max() + 0.5 x\_mesh, y\_mesh = np.meshgrid(np.arange(x\_min, x\_max, 0.01), np.arange(y\_min, y\_max, 0.01)) Z = predict(weights, np.c\_\[x\_mesh.ravel(), y\_mesh.ravel()\])

Z = Z.reshape(x\_mesh.shape)

cs = pylab.contourf(x\_mesh, y\_mesh, Z, cmap=pylab.cm.Spectral) pylab.scatter(train\_X\[:, 0\], train\_X\[:, 1\], c=train\_y, cmap=pylab.cm.Spectral) pylab.colorbar(cs)

\# Plot the loss over each step pylab.figure() pylab.plot(loss\_values) pylab.xlabel("Steps") pylab.ylabel("Loss") pylab.show()

Let us now compute gradient for something a bit more complicated, the loss function for logistic regression. Let's also fit the model using steepest descent. Listing [9-1](#main-11.xhtml#bookmark4) shows the code for the same, and Figures [9-10](#main-11.xhtml#bookmark5) and [9-11](#main-11.xhtml#bookmark6) show the decision boundary and the loss over the steepest descent steps.

![](main-128.jpg)

Figure 9-10. Decision boundary and training data for Logistic Regression

![](main-129.jpg)

Figure 9-11. Loss over steps for Logistic Regression

## Summary

In this chapter we covered the basics of Automatic Differentiation, which is commonly referred to as backpropagation in the Neural Network Community. The key take-away for the reader in this chapter is that automatic differentiation enables the computation of gradients for arbitrarily complex loss functions and is one of the key enabling technologies for deep learning. The reader should also internalize the concepts of automatic differentiation and how it is different from both symbolic and numerical differentiation.

CHAPTER 10

Introduction to GPUs

![](main-130.png)

This chapter introduces the reader to GPU (Graphics Processing Unit)-based computation, which has played and will continue to play a big role in the successful application of Deep Learning in a variety of application domains. Typically, a deep learning practitioner is working with high-level libraries like Keras or Theano, which automatically translates the computation to be performed seamlessly to CPU or GPU. While in a majority of the cases, a practitioner of deep learning is not required to understand the internal workings of the GPU (as many high-level libraries are available), it is essential to be aware of the basics.

The essence of GPU-based computation is the notion of Single Instruction, Multiple Data (SIMD), wherein the same computation is being performed in parallel (over may cores) on multiple data points. This computational paradigm is very suitable for compute heavy linear algebra operations. As we have seen in earlier chapters, the core computation involved in training deep learning models is the computation of gradients and updating the parameters based on these gradients. At the heart of this lie basic linear algebraic operations (dot products, vector matrix multiplications, etc.) and this GPU-based computation is quite suitable for training (and making predictions) using the same.

Let us start by describing the key elements of such a GPU-based computation. Figure [10-1](#main-11.xhtml#bookmark10) schematically illustrates these key elements.

© Nikhil Ketkar 2017

N. Ketkar, Deep Learning with Python, DOI 10.1007/978-1-4842-2766-4\_10

![](main-131.jpg)

Figure 10-1. GPU-based Computation

The following points are to be noted:

*   1\. Deep learning-related computation involves some code to be executed sequentially and some compute-intensive code which can be parallelized.
    
*   2\. Typically, the sequential code involves loading the data from disk, etc., which is handled by the CPU.
    
*   3\. The computationally heavy code typically involves computing the gradients and updating the parameters. Data for this computation is first transferred to the GPU memory, and this computation then happens on the GPU.
    
*   4\. Next, the results are brought back to the main memory for further sequential processing.
    
*   5\. There might be multiple blocks of such computationally heavy code interlaced with sequential code.
    

■ Note there are two main ecosystems built around Gpus: one is Cuda, which is specific to nvidia, and openCL, which is vendor-neutral. We will be covering concepts around Gpu computation in the context of openCL.

Let us start by looking at the overall programming model for GPU-based computation as described by OpenCL. OpenCL is a vendor neural framework for heterogeneous computation involving CPUs, GPUs, DSPs (Digital Signal Processors), and FPGAs (Field Programmable Gate Arrays), etc. Figure [10-2](#main-11.xhtml#bookmark11) illustrates the physical view of the system.

![](main-132.png)

Figure 10-2. OpenCL System Physical View

![](main-133.png)

The following points are to be noted:

*   1\. The overall system consists of the Host and a number of OpenCL devices.
    
*   2\. The host refers to the CPU running the OS, which can communicate with a number of OpenCL devices.
    
*   3\. OpenCL devices are heterogeneous, as in, different. They might be involving CPUs, GPUs, DSPs (Digital Signal Processors), and FPGAs (Field Programmable Gate Arrays), etc.
    
*   4\. OpenCL devices contain one or more compute units.
    

Let's now look at the logical view of an OpenCL system illustrated in Figure [10-3](#main-11.xhtml#bookmark12).

![](main-134.png)

Figure 10-3. OpenCL System Logical View

The following points are to be noted:

*   1\. An OpenCL program runs on the host system.
    
*   2\. The OpenCL program communicates with OpenCL devices using command queues. Each OpenCL device has a separate command queue.
    
*   3\. Each OpenCL device houses data in its memory, sent to it by the program running on the host.
    
*   4\. Each OpenCL device runs code sent to it by the host program, referred to as the kernel.
    
*   5\. The host program, the command queues, the data, and the kernels together constitute an execution context.
    
*   6\. The execution context essentially is the logical envelopment of the heterogeneous computation. The host program orchestrates this computation by sending data and code to be executed to the OpenCL devices and getting the results.
    

Let's now take a look at the logical memory layout on an OpenCL device. Figure [10-4](#main-11.xhtml#bookmark13) illustrates the same.

| Global |
| --- |
| rConstant |
|  || Work Group ||  |
|  || Local MemoryI                                               > ||  |
|  ||  ||  |
|  ||  || Private Memory ||  ||  |
|  || Work Item |
|  ||  ||  |
|  ||  || Private Memory ||  ||  |
|  || Work Item |
|  ||  ||  |
|  ||  || zPrivate Memory ||  ||  |
|  || Work Item |
|  ||  ||  |
|  || Work Group ||  |
|  || Local Memory ||  |
|  ||  ||  |
|  ||  || Private Memory ||  ||  |
|  || Work Item |
|  ||  ||  |
|  ||  || Private Memory ||  ||  |
|  || Work Item |
|  ||  ||  |
|  ||  || Private Memory ||  ||  |
|  || Work Item |
| \_ ||  ||  |

| Memory |
| --- |
| Memory |
|  || Work Group ||  |
|  || Local Memory ||  |
|  ||  ||  |
|  ||  || Private Memory ||  ||  |
|  || Work Item |
|  ||  ||  |
|  ||  || Private Memory ||  ||  |
|  || Work Item |
|  ||  ||  |
|  ||  || Private Memory ||  ||  |
|  || Work Item |
|  ||  || \- |
|  || Work Group ||  |
|  || Local Memory ||  |
|  ||  ||  |
|  ||  || Private Memory ||  ||  |
|  || Work Item |
|  ||  ||  |
|  ||  || Private Memory ||  ||  |
|  || Work Item |
|  ||  ||  |
|  ||  || Private Memory ||  ||  |
|  || Work Item |
|  ||  || \_ |

Figure 10-4. Device Memory

The following points are to be noted:

1\. An OpenCL device has a global memory, which is accessible to the host program as well as all the running kernels on the device.

*   2\. An OpenCL device has a constant memory, which is just like global memory but it is read-only for an executing kernel.
    
*   3\. A Work Item is the logical unit of parallelism and it has its own private memory. Only the kernel code corresponding to this particular work item is aware of this memory.
    
*   4\. A Work Group is the logical unit of synchronization and it contains a number of Work Items. Note that any synchronization can only be done within a Work Group.
    
*   5\. A Work group has its own Local Memory that can only be accessed from within the Work Group.
    

Let us now take a look at the programming model with respect to an OpenCL Device (Figure [10-5](#main-11.xhtml#bookmark14)).

Global Identifier

Count

![](main-135.png)

| uu□ □□ □ || ULI no oi ri □ □ || □□□□ □□□□ □□□□ □□□□ || □ □□□□ □□□□ □□□□ □□□ || O ODO Cl D D IO |
| --- | --- | --- | --- | --- |
| DODD O u D O |
| □ □ || □n || □□□□ ||  || □ □□□ |
| □ □ || □□ || □□□□ || □ □□□ || □ □□□ |
|  || O LI OI oGOO d || □ □□□□ □□□ || O o LI OO LI O O |
| □ □ || □□ || □ □□□ || □ □□□ || □ □□□ |
| □ □ || □□ || □ □□□ || □ □□□ || □ □□□ |
|  || □□ || □ □□□ || □ □□□ || □ □□□ |
|  || □□ || □ □□□ || □ □□□1 ||  |
| □ □ || □□ || □ □□□ ||  || □□□□ |
| □ □ □ □ || □□□□ || ci O D ID || ODDO |
| □ □ || □□ || □ □□□ || □ □□□ || O u LI Li |
|  || □□1 || DDDol || □ □□□ || □□□□ |

![](main-136.png)

Workgroup

Figure 10-5. Two-Dimensional NDRange Index Space

Count

s[y]

Local Identifier

, Sy)

The following points are to be noted:

*   1\. An OpenCL kernel is launched to perform work on data already transferred to the device memory. While launching, the number of work groups and the numbers of work items in each work group is logically specified.
    
*   2\. The kernel is invoked in parallel for each work item in a work group. Work groups execute in no particular order and a kernel can find out the current work item identifier and work group identifier.
    
*   3\. Synchronization can happen only within a work group.
    
*   4\. A work item identifier can be 1-, 2-, or 3- dimensional (NDRange). This basically makes it easy to write kernels for 1-D (time series), 2-D (images), and 3-D (volumes) data sets.
    

Let us now introduce some notation that will allow us to describe the indexing. We will assume the indexing is 2-D, but the same reasoning applies to 1-D or 3-D data. We denote by (G[x] , G[y]) the global indexing space. Let us now look at how this global indexing space gets broken into work groups and work items. For convenience, we define offsets (F[x] , F[y]) which define the portion of the indexing that is not broken into work items and work groups. Let (S[x] , S[y]) define the size of the work group and (W[x] , W[y]) define the number of work groups. Along similar lines, let (g[x] , g[y]) denote the global identifiers, (s[x] , s[y]) denote the local identifiers, and let (w[x] , w[y]) denote the work group identifiers. Then, the relationship between local and global identifiers is described as (g , g ) = (w S + s + F , w S + s + F ).

x y x x x x y y y y

Writing a kernel for a given computation basically involves leveraging this identifier mechanism and the parallel invocations of the kernels over work items and work groups to perform the task at hand. Listings 10-2 and 10-3 illustrate this for vector addition and matrix multiplication, respectively. Listing [10-1](#main-11.xhtml#bookmark15) simply prints out the details of the OpenCL system that the reader can use to determine the details of their system.

Listing 10-1. Getting Information on GPUs

import pyopencl as cl

print "OpenCL Platforms and Devices" for platform in cl.get\_platforms():

print "Platform print "Platform print "Platform print "Platform for device in platform.get\_devices(): print print print print print print print size/1024.0) print

Name: " Vendor" Version Profile

, platform.name

^,

platform.vendor

, platform.version

platform.profile

II

II

",

II

II

II

II

II

II

II

\\n"

\\tDevice \\tDevice \\tDevice \\tDevice \\tDevice \\tDevice

Name ", device.name

Type ", cl.device\_type.to\_string(device.type) Max Clock Speed Compute Units ", Local Memory ", Constant Memory

II

\\tDevice

(1024\*1024\*1024.0))

II

Global Memory "

, "{0} Mhz".format(device.max\_clock\_frequency)

"{0}".format(device.max\_compute\_units)

{0:.0f} KB".format(device.local\_mem\_size/1024.0)

, "{0:.0f} KB".format(device.max\_constant\_buffer\_

II

II

II

{0:.0f} GB".format(device.global\_mem\_size/

\# OpenCL Platforms and Devices

\# Platform Name: Apple

\# Platform Vendor Apple

\# Platform Version: OpenCL 1.2 (Nov 18 2015 20:45:47)

\# Platform Profile: FULL\_PROFILE

#

#

\# Device Name Intel(R) Core(TM) i7-4770HQ CPU @ 2.20GHz

\#      Device Type CPU

\#      Device Max Clock Speed 2200 Mhz

\#      Device Compute Units 8

\#      Device Local Memory 32 KB

\# Device Constant Memory 64 KB

\# Device Global Memory 16 GB

#

#

\#      Device Name Iris Pro

\#      Device Type GPU

\#      Device Max Clock Speed 1200 Mhz

\#      Device Compute Units 40

\#      Device Local Memory 64 KB

\# Device Constant Memory 64 KB

\# Device Global Memory 2 GB

Listing 10-2. Vector Addition

import numpy as np

import pyopencl as cl

import time

vector1 = np.random.random(5000000).astype(np.float32)

vector2 = np.random.random(5000000).astype(np.float32)

cl\_context = cl.create\_some\_context()

queue = cl.CommandQueue(cl\_context)

mf = cl.mem\_flags

vector1\_in\_gpu = cl.Buffer(cl\_context, mf.READ\_ONLY | mf.COPY\_HOST\_PTR, hostbuf=vector1) vector2\_in\_gpu = cl.Buffer(cl\_context, mf.READ\_ONLY | mf.COPY\_HOST\_PTR, hostbuf=vector2) result\_in\_gpu = cl.Buffer(cl\_context, mf.WRITE\_ONLY, vector1.nbytes)

cl\_program = cl.Program(cl\_context, """

\_\_kernel void sum(

\_\_global const float \*vector1, \_\_global const float \*vector2, \_\_global float \*result) {

int i = get\_global\_id(0);

result\[i\] = vector1\[i\] + vector2\[i\];

}

""").build()

t0 = time.time()

cl\_program.sum(queue, vector1.shape, None, vector1\_in\_gpu, vector2\_in\_gpu, result\_in\_gpu) t1 = time.time()

gpu\_time = t1 - t0

print "GPU Time", gpu\_time

result\_in\_numpy = np.empty\_like(vector1)

cl.enqueue\_copy(queue, result\_in\_numpy, result\_in\_gpu)

t0 = time.time() cpu\_result = vector1 + vector2

t1 = time.time()

cpu\_time = t1 - t0 print "CPU Time", cpu\_time

print "Norm of Difference", np.linalg.norm(result\_in\_numpy - cpu\_result)

\# GPU Time 0.00202608108521

\# CPU Time 0.00995397567749

\# Norm of Difference 0.0

Listing 10-3. Matrix Multiplication

import numpy as np

import pyopencl as cl

import time

matrix1 = np.random.random((500,500)).astype(np.float32)

matrix2 = np.random.random((500,500)).astype(np.float32)

cl\_context = cl.create\_some\_context()

queue = cl.CommandQueue(cl\_context)

mf = cl.mem\_flags

matrix1\_in\_gpu = cl.Buffer(cl\_context, mf.READ\_ONLY | mf.COPY\_HOST\_PTR, hostbuf=matrix1)

matrix2\_in\_gpu = cl.Buffer(cl\_context, mf.READ\_ONLY | mf.COPY\_HOST\_PTR, hostbuf=matrix2) result\_in\_gpu = cl.Buffer(cl\_context, mf.WRITE\_ONLY, matrix1.nbytes)

cl\_program = cl.Program(cl\_context, """

\_\_kernel void product(

int size, \_\_global const float \*matrix1, \_\_global const float \*matrix2, \_\_global float \*result)

{

int i = get\_global\_id(0);

int j = get\_global\_id(1); result\[i + size \* j\] = 0;

for (int k = 0; k < size; k++)

{

result\[i + size \* j\] += matrix1\[k + size \* i\] \* matrix2\[j + size \* k\];

}

}

""").build()

t0 = time.time()

cl\_program.product(queue, matrix1.shape, None, np.int32(len(matrix1)), matrix1\_in\_gpu, matrix2\_in\_gpu, result\_in\_gpu)

t1 = time.time() gpu\_time = t1 - t0 print "GPU Time", gpu\_time

result\_in\_numpy = np.empty\_like(matrix1) cl.enqueue\_copy(queue, result\_in\_numpy, result\_in\_gpu)

t0 = time.time()

cpu\_result = np.dot(matrix1, matrix2)

t1 = time.time() cpu\_time = t1 - t0 print "CPU Time", cpu\_time

print "Norm of Difference", np.linalg.norm(result\_in\_numpy - cpu\_result.T)

\# GPU Time 0.00202608108521

\# CPU Time 0.00995397567749

\# Norm of Difference 0.0

## Summary

In this chapter we have introduced the reader to GPU-based computation, which is one of the key enabling technologies for Deep Learning.

One key point to note is that, in this chapter, we have covered the basics of GPU computation using OpenCL, which is vendor-neutral. The concepts apply with minor variation to other vendor-specific GPU computation libraries like CUDA, which is both older and popular as compared to OpenCL. The reader is advised to try out the examples in the source code listings in the chapter following, while reading up on the documentation of CUDA, which would be much easier to follow given that the reader has internalized the foundations. Libraries like cuDNN, which is a CUDA-based library for deep learning, is recommended further reading. It must be noted, however, that in many cases, when it comes to applying deep learning to a real-world problem, it suffices to use high-level libraries like Theano and Keras, which generate GPU code.

The second key point to note is the importance of GPU-based computation for Deep Learning. The single instruction, multiple data paradigm (SIMD) is ideal for deep learning, as most of computation with respect to deep learning boils down to stochastic gradient descent (SGD). At the heart of SGD we have the computation of gradients, which are essentially linear algebraic (vector/matrix) operations. As data sets and the sizes of the parameters grow, it becomes essential to perform SGD in a scalable way, and GPUs currently are the best suited computational paradigm.

# Index

A

Activation functions, 25-27, 29-31

Adadelta, 121 Adagrad algorithm, 120

Adam, 121

Adjointmode. See Reverse mode

Artificial Intelligence (AI), 1

methodology, 1

ML algorithms, 2 problem/task domain, 1

Autograd, 31, 143-144, 146 Automatic differentiation fundamentals, 133 forward mode, 134-138 implementation, 141 operator overloading, 142 reverse mode, 138-139, 141 source code transformation, 141-142 hands-on with Autograd, 143-144, 146 numerical differentiation, 131-132 symbolic differentiation, 132-133

B

Backward difference method, 131

Bernoulli distribution, 23, 26 Bidirectional RNN, 89-90 Binary classification, 5-6 Binary cross entropy, 23, 25

■ C

Central difference approach, 132

Composite functions, 133 Computational graph, 135-136, 138 Computationally heavy code, 148 Compute-intensive code, 148 Constant error carousal, 93 Convolution-detector-pooling blocks, 70, 72, 73 Convolution neural networks (CNNs) convolution-detector-pooling blocks, 70, 72, 73 intuition, 75-76 operation, 61

fully connected layers, 66 intuition, 62, 64 one dimension, 63 pooling operation, 68-69 sparse interactions in layer, 67 tied weights, 68

two dimensions, 64-65 variants, 74-75

Cost functions computation of, 20 using Maximum Likelihood binary cross entropy, 23 cross entropy, 23-24 squared error, 24

Cotangent linearmode. See Reverse mode

Cross-correlation, 61, 64 Cross entropy, 23-25

■ D

Deep learning

advances in related fields, 3 artificial intelligence, 1 historical context, 1-3 installing libraries, 4 prerequisites, 3

Depth of network, 18

Device memory, 153

Digital Signal Processors (DSPs), 148

Downpour, 125

E

Equilibrated SGD, 122

Exploding gradient, 90-91

© Nikhil Ketkar 2017

N. Ketkar, Deep Learning with Python, DOI 10.1007/978-1-4842-2766-4

■ INDEX

F

Feedforward neural networks, 19 function, 15

hands-on with Autograd, 31 for regression, 29-30

structure, 17-18 training, 21-22 unit, 15 vector form, 18-19

Field Programmable Gate Arrays (FPGAs), 148

Forward mode, 134-138

Fully connected layer, 66, 73, 75

*   ■ G
    

Generalization, 7, 12 actual and predicted values, 10-11 dataset for regression, 9 least squares, 9 model capacity, 12 RMSE metric, 10 vs. rote learning, 7-9

Global indexing space, 153

Global memory, 151

Gradient-based methods, 25

Graphics Processing Unit (GPU) computationally heavy code, 148 compute-intensive code, 148 key elements, 148 sequential code, 148

SIMD, 147

Keras, 95 activation function, 97-98, 100, 103-104 Adadelta, 107 building blocks, 95 computational graph, 95 convolution neural networks, 104-105, 107 dropout layers, 107 flatten layers, 107 functionality, 95

IMDB, 109

IMDD, 109

input and output dimensionality, 95, 97-98 loss function, 95, 97

LSTM, 95, 107, 109 multiclass classification, 99-100 optimisers, 102-103 optimization algorithm, 95 pooling operation, 107 regression, 100-102 sequential construct, 95, 97-98, 100 single layer neural network, 96 softmax activation, 98, 107 theano, 95 two convolution-detector, 107 two layer neural network, 97

L

Linear unit, 26

Logistic regression, 146 Long short term memory (LSTM), 93 Loss functions, 20, 21, 25

M

Machine learning binary classification, 5-6 generalization, 7-12 intuition, 5 regression, 6-7 regularization, 12-14

Matrix multiplication, 155-156

Maximum Likelihood

cost functions, 22 binary cross entropy, 23 cross entropy, 23-24 squared error, 24

principle, 4 Multinomial distribution, 23

N

Nesterov accelerated gradient (NAS), 119 Numerical differentiation, 131-132

Numpy Library, 143

O

OpenCL, 148 command queues, 150 defined, 148 device memory, 151 global memory, 151 GPUs, 153-154 heterogeneous, 149

kernel, 150

private memory, 152 system logical view, 150 system physical view, 149 two-dimensional NDRange index

space, 152

work groups, 152, 153

Operator overloading, 142

Output layer, 17

*   ■ P, Q
    

Pooling operation, 68, 76

Private memory, 152

*   ■ R
    

RandomStreams, 47

Random variation, 7

Rectified Linear Unit (ReLU), 27

Recurrent Neural Networks (RNNs)

basics, 77-80, 82 bidirectional, 89-90 equations, 77-78, 80 gradient clipping, 91-92 gradient explosion, 90-91

LSTM, 93

notation, 77 points to be remembered, 82 recurrence using output, 79 teacher forcing, 89 training, 82-86, 88 unrolling, 83-85, 87 vanishing gradients, 90-92

Regression, 6-7

Regularization, 12-14

Resilient Backpropagation, 122 Reverse mode, 138-141, 143 RMSProp algorithm, 120-121

Root mean squared error (RMSE), 6-7 Rote learning, 12

*   ■ S
    

Scipy, 132

Sequential code, 148

Sigmoid unit, 26

Simple function, 134

Single instruction, multiple data

(SIMD), 147

Softmax activation function, 89

Softmax layer, 27

Softmax units, 25

Source code transformation, 141-142

Squared error, 24

Stochastic gradient descent (SGD), 111 algorithmic variations, 118

Adadelta, 121

Adagrad algorithm, 120

Adam, 121

annealing and learning rate schedules, 120

Equilibrated SGD, 122

momentum, 118-119

NAS, 119

Resilient Backpropagation, 122

RMSProp, 120-121

batch, 114

batch vs. stochastic, 114

challenges, 114

local minima, 115

saddle points, 115-116

selecting learning rate, 116-117 slow progress in narrow valleys, 118

with Downhill, 126-127

generating data, 126

loss function, 127

training and validation, 129

variants, 130

method of steepest descent, 112-113 optimization problems, 111-112 stochastic mini-batch, 114 stochastic single example, 114 tricks and tips

activation function, choice of, 123

batch normalization, 123

Downpour, 125

early stopping, 124

gradient noise, 124

Hogwild, 124 initializing parameters, 123 parallel and distributed SGD, 124 preprocessing input data, 122 preprocessing target value, 123 shuffling data, 123

Symbolic differentiation, 132-133

SymPy, 133

T

Tangent linearmode. See Forward mode

Tanh activation function, 78, 80, 89

Teacher forcing, 88-89

TensorFlow, 95

Theano, 95, 143

definition, 33

hands-on, 34

activation functions, 37, 39

computing gradients, 42

functions with scalars and vectors, 34-37 gradients, 41

■ INDEX

 
| Theano (cont.)Hinge implemented using Max, 55linear regression, 51-52 logistic regression, 49-50 loss functions, 42-43 neural network, 53-54 random streams, 47-48 regularization, 45-46 shared variable, 40-41 switch/if-else, 54 workflow for using, 33 || linear unit, 26ReLU, 27Sigmoid unit, 26Softmax layer, 27Unrolling process, 83-85, 87VVanishing gradients, 90-93 Vector addition, 154-155 Vector form, 18-19 |
| --- | --- |
| UUnits, 15, 17hyperbolic tangent, 28 || W, X, Y, ZWidth of layer, 17Work groups, 152, 153 |