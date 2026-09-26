![](image_rsrc9SD.jpg)

   

![](image_rsrc9SE.jpg)

© Copyright 2021 - All rights reserved. The content contained within this book may not be reproduced, duplicated, or transmitted without direct written permission from the author or the publisher. Under no circumstances will any blame or legal responsibility be held against the publisher, or author, for any damages, reparation, or monetary loss due to the information contained within this book, either directly or indirectly. Legal Notice: This book is copyright protected. It is only for personal use. You cannot amend, distribute, sell, use, quote or paraphrase any part, or the content within this book, without the consent of the author or publisher. Disclaimer Notice: Please note the information contained within this document is for educational and entertainment purposes only. All effort has been executed to present accurate, up to date, reliable, complete information. No warranties of any kind are declared or implied. Readers acknowledge that the author is not engaging in the rendering of legal, financial, medical, or professional advice. The content within this book has been derived from various sources. Please consult a licensed professional before attempting any techniques outlined in this book. By reading this document, the reader agrees that under no circumstances is the author responsible for any losses, direct or indirect, that are incurred as a result of the use of the information contained within this document, including, but not limited to, errors, omissions, or inaccuracies. 

Table of Contents ![](image_rsrc9SF.jpg)[TENSORFLOW MACHINE LEARNING](#part0004.xhtml)  
[A Comprehensive Beginner's Guide to Learn About  
the Realms of TensorFlow Machine Learning From A-Z](#part0004.xhtml#a9AB) [Introduction](#part0005.xhtml) [Chapter 1](#part0006.xhtml) : [What is Deep Learning?](#part0006.xhtml#a9AE) [How Does Deep Learning Work?](#part0006.xhtml#a9AF) [Different Deep Learning Networks](#part0006.xhtml#a9AG) [Reinforcement Learning](#part0006.xhtml#a9AH) [Deep Learning Applications](#part0006.xhtml#a9AJ) [Deep Learning Limitations](#part0006.xhtml#a9AK) [In Summary](#part0006.xhtml#a9AM) [Chapter 2](#part0007.xhtml) : [Machine Learning vs. Deep Learning](#part0007.xhtml#a9AP) [What is Machine Learning?](#part0007.xhtml#a9AR) [What is Deep Learning?](#part0007.xhtml#a9AS) [How is Machine Learning Done?](#part0007.xhtml#a9AT) [How is Deep Learning Done?](#part0007.xhtml#a9AU) [Chapter 3](#part0009.xhtml) : [What is TensorFlow?](#part0009.xhtml#a9AW) [TensorFlow History](#part0009.xhtml#a9AX) [Simple Example](#part0009.xhtml#a9AY) [How to Create a TensorFlow Pipeline](#part0009.xhtml#a9AZ) [Chapter 4](#part0010.xhtml) : [Installing TensorFlow on Windows and Mac](#part0010.xhtml#a9B1) [Chapter 5](#part0011.xhtml) : [A Deeper Dig Into TensorFlow](#part0011.xhtml#a9B3) [Tensor Representation](#part0011.xhtml#a9B4) [Tensor Types](#part0011.xhtml#a9B5) [Creating an Operator](#part0011.xhtml#a9B6) [Variables](#part0011.xhtml#a9B7) [Chapter 6](#part0012.xhtml) : [An Overview of TensorBoard](#part0012.xhtml#a9B9) [Chapter 7](#part0013.xhtml) :  [NumPy](#part0013.xhtml#a9BB) [Why NumPy?](#part0013.xhtml#a9BC) [Mathematical Operations on Arrays](#part0013.xhtml#a9BD) [Shape of The Array](#part0013.xhtml#a9BE) [np.zeros and np.ones](#part0013.xhtml#a9BF) [Reshaping and Flattening the Data](#part0013.xhtml#a9BG) [hstack and vstack](#part0013.xhtml#a9BH) [Generating Random Numbers](#part0013.xhtml#a9BJ) [Arange](#part0013.xhtml#a9BK) [Linspace](#part0013.xhtml#a9BM) [Statistical Functions](#part0013.xhtml#a9BN) [Chapter 8](#part0014.xhtml) : [Pandas](#part0014.xhtml#a9BR) [Why Pandas?](#part0014.xhtml#a9BS) [Installing Pandas](#part0014.xhtml#a9BT) [Create a Data Frame](#part0014.xhtml#a9BU) [Concatenation](#part0014.xhtml#a9BV) [Chapter 9](#part0015.xhtml) : [Scikit-Learn](#part0015.xhtml#a9BX) [Download Scikit-Learn](#part0015.xhtml#a9BY) [Machine Learning With Scikit-Learn](#part0015.xhtml#a9BZ) [XGBoost Model Using Scikit-Learn](#part0015.xhtml#a9C0) [Creating a DNN Using MLPClassifier in Scikit-Learn](#part0015.xhtml#a9C1) [Trusting Your Model With LIME](#part0015.xhtml#a9C2) [Chapter 10](#part0016.xhtml) : [Linear Regression](#part0016.xhtml#a9C4) [Training a Linear Regression Model](#part0016.xhtml#a9C5) [Using TensorFlow to Train Linear Regression](#part0016.xhtml#a9C6) [Using TensorFlow Only](#part0016.xhtml#a9C7) [Chapter 11](#part0017.xhtml) : [Linear Regression - A Case Study](#part0017.xhtml#a9C9) [Summary Statistics](#part0017.xhtml#a9CA) [Facets Overview](#part0017.xhtml#a9CB) [Facets Deep Dive](#part0017.xhtml#a9CC) [Installing Facet](#part0017.xhtml#a9CD) [Facet Overview](#part0017.xhtml#a9CE) [Graph](#part0017.xhtml#a9CF) [Facets Deep Dive](#part0017.xhtml#a9CG) [TensorFlow](#part0017.xhtml#a9CH) [Chapter 12](#part0018.xhtml) : [Kernel Methods](#part0018.xhtml#a9CK) [Why You Need Kernel Methods](#part0018.xhtml#a9CM) [Different Kernel Methods](#part0018.xhtml#a9CN) [Using TensorFlow to Train a Gaussian Kernel Classifier](#part0018.xhtml#a9CP) [Chapter 13](#part0019.xhtml) : [Using TensorFlow to Build an ANN](#part0019.xhtml#a9CS) [Neural Network Architecture](#part0019.xhtml#a9CT) [Neural Network Limitations](#part0019.xhtml#a9CU) [Network Size](#part0019.xhtml#a9CV) [Using TensorFlow to Train a Neural Network](#part0019.xhtml#a9CW) [Chapter 14](#part0020.xhtml) : [Using TensorFlow for ConvNet Image Classification](#part0020.xhtml#a9CY) [Architecture of a ConvNet](#part0020.xhtml#a9CZ) [The Convolutional Operation](#part0020.xhtml#a9D0) [ConvNet Components](#part0020.xhtml#a9D1) [Convolution](#part0020.xhtml#a9D2) [Chapter 15](#part0021.xhtml) : [Autoencoders with TensorFlow](#part0021.xhtml#a9D4) [Building a Stacked Autoencoder Using TensorFlow](#part0021.xhtml#a9D5) [Preprocessing the Images](#part0021.xhtml#a9D6) [Conclusion](#part0022.xhtml) [References](#part0023.xhtml) [TENSORFLOW MACHINE LEARNING](#part0024.xhtml)  
[Simple and Effective Tips and Tricks to Learn  
Machine Learning with Scikit-Learn, Keras and Tensorflow](#part0024.xhtml#a9DA) [Introduction](#part0025.xhtml) [Chapter 1](#part0026.xhtml) : [Introduction to Machine Learning](#part0026.xhtml#a9DD) [What Is Machine Learning?](#part0026.xhtml#a9DE) [Examples of Machine Learning](#part0026.xhtml#a9DF) [Different Types of Machine Learning](#part0026.xhtml#a9DG) [Supervised and Unsupervised Learning](#part0026.xhtml#a9DH) [Online and Batch Learning](#part0026.xhtml#a9DJ) [Hindering Factors For Machine Learning](#part0026.xhtml#a9DK) [Chapter 2](#part0027.xhtml) : [Perform Regression Tasks Using Scikit-Learn](#part0027.xhtml#a9DN) [Gathering the Data](#part0027.xhtml#a9DP) [Choosing a Regression Task](#part0027.xhtml#a9DR) [Choosing the Appropriate Performance Measure](#part0027.xhtml#a9DS) [Getting Started with the Practical Work](#part0027.xhtml#a9DT) [Creating a Testing Set Using Random Sampling](#part0027.xhtml#a9DU) [Preparing the Data](#part0027.xhtml#a9DV) [Creating, Training and Evaluating the Model](#part0027.xhtml#a9DW) [Using the Testing Dataset to Evaluate the Model](#part0027.xhtml#a9DX) [Chapter 3](#part0028.xhtml) : [Creating a Classification Model with Scikit-Learn](#part0028.xhtml#a9DZ) [The MNIST Dataset](#part0028.xhtml#a9E0) [Training a Binary Classifier](#part0028.xhtml#a9E1) [Measuring the Performance](#part0028.xhtml#a9E2) [Chapter 4](#part0029.xhtml) : [Using Keras to Work With Artificial Neural Networks](#part0029.xhtml#a9E4) [Using the Keras API](#part0029.xhtml#a9E5) [Using a Sequential API to Create an Image Classifier](#part0029.xhtml#a9E6) [Creating a Regression MLP Using Sequential API](#part0029.xhtml#a9E7) [Chapter 5](#part0030.xhtml) : [Addressing the Problems Faced When Training Deep Neural Networks](#part0030.xhtml#a9E9) [Dealing with the Vanishing and Exploding Gradients Problem](#part0030.xhtml#a9EA) [Dealing with Problem of Data Shortage When Training Deep Neural Networks](#part0030.xhtml#a9EB) [Dealing with the Problem of Slow Training](#part0030.xhtml#a9EC) [Dealing with the Risk of Overfitting of Deep Neural Networks](#part0030.xhtml#a9ED) [Conclusion](#part0031.xhtml) [References](#part0032.xhtml) [TENSORFLOW MACHINE LEARNING](#part0033.xhtml)  
[Advanced Guide to Learn Machine Learning  
With Scikit-Learn, Keras and TensorFlow](#part0033.xhtml#a9EH) [Introduction](#part0034.xhtml) [Part One](#part0035.xhtml) : [An Introduction to Machine Learning](#part0035.xhtml#a9EM) [What is Machine Learning?](#part0036.xhtml) [Machine Learning Methods](#part0036.xhtml#a9EP) [Supervised Learning](#part0036.xhtml#a9ER) [Unsupervised Learning](#part0036.xhtml#a9ES) [Reinforcement Learning](#part0036.xhtml#a9ET) [Machine Learning Approaches](#part0036.xhtml#a9EU) [Programming Languages](#part0036.xhtml#a9EV) [Deep Learning](#part0037.xhtml) [Deep Learning Vs. Machine Learning](#part0037.xhtml#a9EX) [Part Two](#part0038.xhtml) : [An Introduction to TensorFlow](#part0038.xhtml#a9EZ) [What is TensorFlow?](#part0039.xhtml#a9F0) [TensorFlow History](#part0039.xhtml#a9F1) [TensorFlow Architecture](#part0039.xhtml#a9F2) [Where Can TensorFlow Run?](#part0039.xhtml#a9F3) [TensorFlow Components](#part0039.xhtml#a9F4) [Simple Example of TensorFlow](#part0040.xhtml) [Loading the Data into TensorFlow](#part0040.xhtml#a9F6) [Building a TensorFlow Pipeline](#part0040.xhtml#a9F7) [Installing TensorFlow](#part0041.xhtml) [Install Anaconda](#part0041.xhtml#a9F9) [Install TensorFlow](#part0041.xhtml#a9FA) [Launching Jupyter Notebook](#part0041.xhtml#a9FB) [TensorFlow Basics](#part0042.xhtml) [What is a Tensor?](#part0042.xhtml#a9FD) [Tensor("Const\_6:0", shape=(1, 3, 2), dtype=int16)](#part0043.xhtml) [Tensor("ones\_3:0", shape=(3, 2), dtype=float32)](#part0044.xhtml) [Useful TensorFlow Operators](#part0044.xhtml#a9FG) [Tensor("Mul:0", shape=(1, 2), dtype=int32)](#part0045.xhtml) [Variables](#part0045.xhtml#a9FJ) [Placeholders](#part0045.xhtml#a9FK) [TensorBoard Graph Visualization Example](#part0046.xhtml) [Using TensorBoard](#part0046.xhtml#a9FN) [Part Three](#part0047.xhtml) : [An Introduction to Keras](#part0047.xhtml#a9FR) [What is Keras?](#part0048.xhtml) [What is a Backend?](#part0048.xhtml#a9FT) [Keras vs. TensorFlow](#part0048.xhtml#a9FU) [How to Install Keras on  Windows and Mac OS](#part0049.xhtml) [Direct Install or Virtual Environment](#part0049.xhtml#a9FW) [Install Keras](#part0049.xhtml#a9FX) [Install Keras](#part0049.xhtml#a9FY) [Keras Fundamentals for Deep Learning](#part0050.xhtml) [Compilation, Training and Evaluation](#part0050.xhtml#a9G0) [Fine-Tuning and Using Pre-Trained Keras Models](#part0050.xhtml#a9G1) [Face Recognition Neural  Network with Keras](#part0051.xhtml) [Network Model](#part0051.xhtml#a9G3) [Using a Live Cam for the Prediction](#part0051.xhtml#a9G4) [Keras or TensorFlow? Which One is Best?](#part0051.xhtml#a9G5) [Keras Tutorial](#part0052.xhtml) [Part Four](#part0053.xhtml) : [An Introduction to Scikit-Learn](#part0053.xhtml#a9G8) [What is Scikit-Learn?](#part0054.xhtml) [Classification and Regression Trees](#part0054.xhtml#a9GA) [Download and Install Scikit-Learn](#part0054.xhtml#a9GB) [Machine Learning With Scikit-Learn](#part0055.xhtml) [XGBoost Model](#part0056.xhtml) [Using the MLPClassifier to Create a DNN](#part0056.xhtml#a9GE) [Using LIME to Trust Your Model](#part0056.xhtml#a9GF) [Building a Random Forest Model  To Predict Wine Quality](#part0057.xhtml) [Top 12 Python Libraries for  Machine and Deep Learning](#part0058.xhtml) [PyTorch](#part0058.xhtml#a9GJ) [Scikit-Learn](#part0058.xhtml#a9GK) [Pandas](#part0058.xhtml#a9GM) [NLTK](#part0058.xhtml#a9GN) [Theano](#part0058.xhtml#a9GP) [MXNet](#part0058.xhtml#a9GR) [SciPy](#part0058.xhtml#a9GS) [NumPy](#part0058.xhtml#a9GT) [Matplotlib](#part0058.xhtml#a9GU) [Conclusion](#part0059.xhtml) [References](#part0060.xhtml) 

TensorFlow  
Machine Learning ![](image_rsrc9SG.jpg)A Comprehensive Beginner's Guide  
to Learn About the Realms of  
TensorFlow Machine Learning  
From A-Z ![](image_rsrc9SF.jpg)Benjamin Smith 

Introduction ![](image_rsrc9SG.jpg)Machine learning is one of the most complex disciplines, but it isn’t as difficult as people think it is. Not anymore, anyway, and that is down to the implementation of a series of machine learning frameworks, helping us acquire data, train our models, serve our predictions and refine results, much easier than ever before. One of those frameworks is TensorFlow. TensorFlow is a Google Brain Team creation and is an open-source library that assists with machine learning and numerical computation. TensorFlow brings us a whole bundle of machine and deep learning algorithms and models, all in one easy-to-use place. If you have no background in computer programming, specifically in Python, then you need to turn back now – this book is written for those with some programming experience and who understand Python and all it entails. We can use TensorFlow for training neural networks and running them for classification of handwritten digits, image recognition, RNNs (Recurrent Neural Networks), NLP (Natural Language Processing), and much more. About This Book I have laid this book out in a logical way that you can easily follow, including lots of code examples that will help you understand the concepts better. As mentioned before, you need to have experience in programming with Python because I will not be giving any background on the programming language needed. This book is arranged like this: 

*   Chapter One – an overview and introduction to deep learning 
*   Chapter Two –  the difference between machine and deep learning 
*   Chapter Three – an introduction to TensorFlow 
*   Chapter Four – downloading TensorFlow on Mac and Windows 
*   Chapter Five – the basics of TensorFlow 
*   Chapter Six – using TensorBoard for graph visualization 
*   Chapter Seven – an introduction to NumPy 
*   Chapter Eight – an introduction to Pandas 
*   Chapter Nine – an introduction to Scikit-Learn 
*   Chapter Ten – Linear Regression 
*   Chapter Eleven – a Linear Regression case study 
*   Chapter Twelve – a look at kernel methods 
*   Chapter Thirteen – Artificial Neural Networks (ANNs) with TensorFlow 
*   Chapter Fourteen – Convolutional Neural Networks and image classification with TensorFlow 
*   Chapter Fifteen – TensorFlow autoencoders 

By the time you reach the end of this guide, you will have an excellent idea of the way that TensorFlow works and how to use it in your machine learning endeavors. So, let’s not waste any more time and dive straight in. Note – Code in this book comes from https://www.guru99.com and is wholly owned by them. Public use permission. 

Chapter  1 What is Deep Learning? ![](image_rsrc9SG.jpg)Before we dive into TensorFlow, it makes sense to take a look at deep learning and machine learning. Deep learning is software that imitates the neuron network in the human brain and is a subset of machine learning. Each algorithm is built using connected layers: 

*   Top Layer – the input layer 
*   Bottom Layer – the output layer 
*   The In-Between Layers – these are all known as Hidden Layers – “deep” means that more than two layers are involved 

The hidden layers are each made up of neurons that are connected to one another. Each will process the input signal it gets from the layer above and propagate it. The signal strength passed to the next layer down is determined by the activation function, bias, and weight. The network consumes vast amounts of input data, and multiple layers are used, ensuring that the deeper it goes, the more complex the features learned become. How Does Deep Learning Work? DNNs, or Deep Neural Networks, are incredibly accurate for most tasks and can learn automatically – they do not need the programmer to code the knowledge in. Let’s say that we have a family of three – two parents, one child. N  matter what object the child points at, he always calls it “dog.” His parents tell him that yes, that is a dog or no, it isn’t. Over time, the child becomes better at identifying dogs, but he doesn’t know why he can say whether it is or isn’t a dog. What the child has learned is the complex, hierarchical features – he can identify a dog by looking at the object and focusing on details that belong to a dog. If those features are not present, it cannot be a dog. Neural networks are much the same, with each layer representing an ever-deeper knowledge level – the hierarchy. Networks with more layers learn more than networks with fewer layers. There are two phases to the learning: 

1.  The input’s nonlinear transformation is applied, and a statistical model created as the output 
2.  A mathematical model, called a derivative, is applied to improve the model 

These phases are repeated over and over until a good accuracy level is reached – each repeat is called an iteration. How Neural Networks are Classified Neural networks are classified in two ways: 

*   Shallow – An input and an output layer with one hidden layer 
*   Deep – An input and an output layer with many hidden layers. Google LeNet, for example, contains 22 layers for image recognition. 

Different Deep Learning Networks There are three primary types of deep learning network: Feed-Forward The simplest network, information can only flow one way – forward – from the input layer, through the hidden layers to the output layer. There is no loop. RNN The recurrent neural network uses context nodes to store information. It can learn sequences of data, and the output is a sequence or a number. There are loops between the neurons. Let’s say, for example, that you want the next word in this sentence predicted – “Would you like some …?” 

*   The neurons get a signal pointing to the sentence beginning. 
*   The input sent to the network is the word “would” – a number vector is produced and sent back to the neuron. This provides the network with a memory, thus helping the network to remember what it received and what position it was in, i.e., first. 
*   The network moves to the next words, “you” and “like,” and processes them, in the same way, updating the neuron state after each one. 
*   The last stage is the word “some,” at which point, the network gives a probability for the words that could finish the sentence – the more relevant it is, the higher the probability. 

Common RNN Uses 

*   Producing analytic reports for securities traders 
*   Finding abnormalities in financial statements 
*   Detecting fraud with credit cards 
*   Providing image captions 
*   Powering chatbots 

CNN Convolutional neural networks contain several layers, each uniquely designed with the extraction of complex features in mind – the deeper the layer, the more complex the features. CNN’s tend to be used mostly with data sets that have no structure, such as image sets, and when information is required from those data sets. For example, with image caption prediction: 

*   An image of a dog is given to the CNN – this is just a bunch of pixels to the computer. There are three layers in color images and one in grayscale images. 
*   As it goes through the hidden layers, the CNN identifies unique features. 
*   Once learning is complete, the CNN can provide a give a probability for every image it is given – the one with the highest probability is the network prediction 

Reinforcement Learning This is  machine learning subfield, where a reward or punishment system is used to train a system by trial and error. DeepMind, created by Google, used reinforcement learning to beat the human GO game champion, and video games also use this type of learning to provide a better gaming experience. The best known RL algorithms are: 

*   DDPG – Deep Deterministic Policy Gradient 
*   Deep Q network 
*   Q-Learning 
*   SARSA – State-Action-Reward-State-Action 

Deep Learning Applications Artificial intelligence (AI) is used in these ways: 

*   Finance –  AI is used all over the financial sector for reducing costs, saving time, and adding value. The lending industry is being changed by deep learning by providing a better system of credit scoring, with lenders able to get accurate, faster risk assessment, using machine intelligence to factor in applicant capacity and character. One example is a Fintech company called Underwrite, which uses AI for detecting the customers more likely to not default on loans. 
*   HR – A sportswear company called Under Armour uses AI to make hiring faster, and better hiring time has been reduced for their retail stores by around 35%. At one time, the company was receiving 30,000+ applications per month, and it was taking too long to screen and interview candidates. Despite having all the technology in place in their HR departments, they ended up choosing an AI HR solution called HireVue, resulting in aster hiring times and better quality staff. 
*   Marketing – AI is one of better customer service and management tools, providing better speech recognition for call routing and call management. For example, audio systems can be analyzed to assess emotions in customers – if a poor response is received to chatbot systems, the call can be routed to a human operator. 

Why Deep Learning is Important The simple explanation is that it is one of the most powerful tools for making predictions actionable. Deep learning is top of the class in pattern recognition and making predictions based on knowledge. Big data fuels it, and a combination of both bring massive results in terms of management, productivity, sales, and innovation. Deep Learning far outperforms the traditional methods of learning. In image classification, the algorithms exhibit 41% more accuracy, 27% in facial recognition, and, in voice recognition, 25%. Deep Learning Limitations Like anything, deep learning does have its limitations: 

*   Data Labeling – typically, supervised learning is used to train AI models, meaning that the underlying data must be labeled and categorized by humans first – this comes with its own set of errors. As an example, self-drive vehicle tech companies are hiring people to take the video feeds from the prototypes and annotate it manually to train the systems on. 
*   Obtaining Massive Training Datasets – Some of the simpler deep learning techniques, such as the CNN, can replicate expert knowledge in many fields, such as medical. However, with the huge growth in machine learning, these days, training sets are required to be labeled, universal and broad – in other words, massive. Accuracy requires that deep learning methods have thousands upon thousands of models to train on for classification and, to perform at the human level, they may require millions. Some of the largest tech companies in the world accumulate massive amounts of data by using deep learning. In some cases, they accumulate petabyte after petabyte, which allows them to create accurate models. 
*   Problem Explanations – It isn’t easy to explain some of the more complex models in human terms. For example, we can’t always say why a model reached a decision, and it is widely accepted that, in areas where we need interpretability, some AI models are just too slow. And as AI applications grow, we could end up with regulatory requirements driving the requirement for models that can easily be explained. 

In Summary Deep learning is, with a doubt, the state-of-the-art for AI. The architecture consists of an input and output layer with two or more  hidden layers in between – “deep” means that there are at least two layers that are fully connected. There are lots of neural networks, each designed around a specific task. The CNN, for example, is best for images, while the RNN is excellent with text analysis and time series. Deep learning can be found in many different fields – medical, finance, marketing, and so on, with the largest firms using deep learning before any other, sensible given that they have the amounts of data needed for an extensive training set to be built. In the next chapter, we’ll look at the difference between machine and deep learning. 

Chapter 2 Machine Learning vs. Deep Learning ![](image_rsrc9SG.jpg)First, AI is the act of giving a machine the ability to think, and the benchmark is human intelligence, such as vision, speech, and reasoning – we won't see that for some time though. There are three levels of AI: 

*   Narrow – when the machine is better than a human at a task 
*   General – when the machine is performing at the same accuracy as humans 
*   Active – when the machine beats humans at multiple tasks 

What is Machine Learning? Machine learning is one of the best analysis tools we have in pattern identification. The primary idea is that a machine can be taught (trained) in automating repetitive tasks or those that are not possible for humans to do. Machine learning can make decisions with little intervention from a human. Data is fed to an algorithm that understands the input/output relationship, leading to the machine learning to make predictions. What is Deep Learning? Deep learning is software that imitates the neuron network in the human brain and is a machine learning subset. It uses deep neural networks (DNNs) to learn data from layers – the deeper the network, the more layers there are, and the more complex the features learned. How is Machine Learning Done? Let’s say that you have been tasked with building an object recognition program. The model is trained using a classifier that uses an object’s features to identify which class the object should be in. Let’s use an example of four objects to train a classifier in detecting: 

*   Plane 
*   Ship 
*   Car 
*   Bicycle 

These are the four classes the classifier must be trained to accept. A classifier is constructed using data for the input with each data given a label. The data is given to the algorithm, which then identifies a pattern and classifies it into the right class. This is known as supervised learning – all data used in supervised learning is labeled. These steps are required to train the algorithm: 

1.  The data is collected 
2.  The classifier is trained 
3.  The model makes predictions 

Step one is critical as the algorithm depends on the right data to succeed or fail. The data is known as features, and, in our example above, the objects are groups of pixels that make up an image. Each image is one data row, and each pixel is a data column. Assuming that you have images of 28x28 pixels, the dataset would consist of 784 columns. The images are transformed into feature vectors and labeled, telling the machine what object it is. These data should be used to train the classifier on the object type. First, the feature columns are created. Then the right algorithm for  training the model is selected, and when the training is finished, the model makes predictions about which object a picture corresponds to. Once that has been done, the model can easily be used for predicting new images. As each image is fed into the model, a prediction is made on the class that the object should be in. Let’s say we give the model an unlabeled image; humans can easily see what the image is, but the machine will need to use what it learned previously to predict what it is. How is Deep Learning Done? Deep learning uses neural networks to do the learning. Using the same object example, in deep learning, the training dataset is given to a neural network. Each individual input is passed to a neuron, and a weight is used to multiply it. The result is then sent as an input to the next layer, and this continues for every layer in the network. The last layer is the output layer, and this is where the value is provided, along with a probability for each class in the task. The network updates all the neuron weights using a mathematical algorithm. It is considered to be fully trained when the value of those weights provides an output that is as near as possible to the reality. As an example, a fully trained neural network recognizes objects with a far higher level of accuracy than standard neural nets can Automatic Feature Extraction A dataset can have anywhere from a small handful to hundreds, even thousands of features, and the model will learn from how relevant each feature is. However, some of those features will mean nothing to the algorithm, and one of the most important parts to successful machine learning is to find the right feature set to ensure that the model actually learns. One way to do this is to use something called feature extractions.  This takes all the existing features and combines them, making a feature set that has more relevance. This is typically done with a dimensionality reduction algorithm, such as T-SNE or PCA. Take image processing, for example. The features must be manually extracted from the image, features such as eyes, ears, wheels, etc. Those features are then given to the classification model. With deep learning, there is no need for this, particularly when you use a CNN (Convolutional Neural Network.) The first network layer learns a few minor details from the image, and each successive layer will learn a little bit more. CNN's use filters to do the feature extraction; these filters are applied to the images to look for a match, for example, that the feature shape matches a bit of the image. If the match exists, that particular filter is used. As such, feature extraction is automatic in deep learning. The following table shows you the differences between deep and machine learning at a glance: 

|  || Machine Learning  || Deep Learning  |
| --- | --- | --- |
| Data Dependencies  || Works well on small and medium datasets  || Works well on large datasets  |
| Hardware Dependencies  || Works on the lower-end, not so powerful machines  || Needs a very powerful machine, preferably one with a GPU, because deep learning needs to do a lot of matrix multiplication  |
| Feature Engineering  || A requirement to have an understanding of the features representing the data  || No requirement to understand the best feature for representing the data  |
| Execution Time  || Anywhere from minutes to hours  || It can take many weeks as neural  networks have a lot of weight computations to do  |
| Interpretability  || Some of the algorithms are easier to interpret, such as the decision tree and logistic algorithms. Others, like XGBoost and SVM, are just about impossible  || Difficult to interpret, in some cases, impossible  |

When to  Use Machine Learning or Deep Learning? The table below gives you a summary of the differences: 

|  || Machine Learning  || Deep Learning  |
| --- | --- | --- |
| Training Dataset  || Small  || Large  |
| Choose Features  || Yes  || No  |
| Number of Algorithms  || Many  || Few  |
| Training Time  || Short  || Long  |

Machine learning algorithms don’t need as much data as deep learning algorithms for training purposes. With deep learning, you need a diverse and huge dataset to find the underlying structure—machine learning results in models being trained much faster, whereas deep learning models can take weeks. The high level of accuracy is the biggest advantage of using deep learning over machine learning. There is no need to understand the best features for data representation because the neural network does it automatically; machine learning requires you to do the feature extraction manually. Now you have an overview of machine learning and deep learning, and it’s time to move on to TensorFlow. In the next chapter, we will look at the basics. 

Chapter 3 What is TensorFlow? ![](image_rsrc9SG.jpg)TensorFlow is one of the primary deep learning libraries in the world and is owned by Google. Google uses machine learning in many of its products to make them better, such as recommendations, translation, search engines, image captioning, and so on.  Google has some of the largest datasets in the world, and machine learning is the best way for them to take advantage of this. Data scientists, researchers, and programmers alike all use machine learning, on their own, or as a collaboration to improve productivity and efficiency. TensorFlow was built to handle one of the largest computers in the world – Google. Built by Google Brain Team, the TensorFlow library was developed to accelerate deep neural network and machine learning research. It runs on mobile operating systems, multiple CPs, and multiple GPUs; it also supports multiple computer programming languages, like Java, C++, and Python, through the use of wrappers. TensorFlow History It is only in the last few years that deep learning has begun to outperform almost every other ML algorithm with huge amounts of data. Google spotted that and determined that deep neural networks could be used for improving their own services, such as their search engine, Google Photos, Gmail, and so on. To facilitate this, they built the TensorFlow framework, allowing developers and researchers to collaborate on AI models. Once it had been built and scaled, many more people could use it. TensorFlow first saw the light of day in 2015, but it was 2017 before a stable version was released. TensorFlow is open-source and released under the Apache Open Source license, and can be redistributed, used and modified without the need to purchase it first. Architecture The architecture has three parts to it: 

1.  The data is preprocessed 
2.  The model is built 
3.  The model is trained and estimated 

The name came about because TensorFlow takes multi-dimensional arrays as inputs, otherwise known as tensors, and an operational flowchart, called a graph, can be constructed for the input. The input starts at one end, flows through all the operations in the system, and exits as an output. We can classify the software and hardware requirements for TensorFlow into the following phases: 

*   Development – the model is trained, usually on a laptop or desktop computer 
*   Run/Interference – when the training is complete, you can run TensorFlow on multiple platforms, including Linux, macOS, Windows, iOS, Android, and as a web service in the cloud. 

You can also train the model and use it on GPUs. These were, to begin with, designed purely for video gaming. However, Stanford researchers discovered in 2010 that GPUs were also excellent at algebra and matrix calculations. Deep learning is reliant on matrix multiplication, and TensorFlow can compute these fast because C++ was used to write it. However, although C++ was used to implement  TensorFlow, it is easily accessible and controllable by other computer languages, the primary one being Python. Lastly, TensorBoard is a significant feature, enabling users to visually and graphically monitor what is being done by TensorFlow. TensorFlow Components TensorFlow has several components: 

*   Tensor - the name, TensorFlow, is derived directly from Tensor, the core framework. Every computation in TensorFlow involves tensors, which are matrices or vectors of n-dimensions, representing all data types. Every value in a tensor shares an identical datatype with a known or partly known shape. And the data shape is the array or matrix dimensionality. 

Tensors can come from the input data, or they may be a result of a computation. Every operation in TensorFlow happens in a graph, which is a series of successive computations, All operations are known as op nodes, and they are all connected.  A graph outlines the ops and the node connections, but this will not show the values. The node edge is called the tensor, i.e., a method of using data to populate the operation. 

*   Graphs – TensorFlow uses a graph framework to gather in all the series computations done through the training and describe them. There are several advantages to the graph: 

*   It can run on multiple GPUs, CPUs, or mobile OS 
*   The graph is portable, which means the computations can be preserved for using now or later 
*   To do the computations, the tensors are connected. Tensors have an edge, and a node – the mathematical operation is carried by the node, producing the  endpoint output, while the edges are used for explaining the IO relationship between the nodes. 

Why TensorFlow is so Popular Simply because it is a library built to be so accessible by everyone. Incorporated into the library are different APIs used to build architectures such as an RNN or a CNN. The graph computation lets developers use TensorBoard to see how their neural network is constructed and can help with debugging too. Plus, TensorFlow is deployable at scale and will run on CPUs and GPUs. Supported Algorithms TensorFlow includes APIs for the following: 

*   Boosted tree classification: tf.estimator.BoostedTreesClassifier
*   Booster tree regression: tf.estimator.BoostedTreesRegressor
*   Classification:tf.estimator.LinearClassifier
*   Deep learning classification: tf.estimator.DNNClassifier
*   Deep learning wipe and deep: tf.estimator.DNNLinearCombinedClassifier
*   Linear regression: tf.estimator.LinearRegressor

Simple Example Here’s a simple example of TensorFlow: import numpy as np import tensorflow as tf In these code lines, TensorFlow has been imported as tf. When you use Python, common practice dictates that short names are used for libraries. This carries the advantage that you don’t have to type in complete library names so, once TensorFlow has been imported as  tf, whenever you need to use it, you simply call tf. Let’s see an example of how the TensorFlow workflow works. We’ll create a graph for multiplying numbers, in the case of our example, X\_1 by X\_2. The operation is connected via a node created by TensorFlow, and that node is named ‘multiply.’ At the point where the graph gets determined, X\_1 and X\_2 will be multiplied together by TensorFlow. Lastly, a TensorFlow session is run, showing the graph with X\_1 and X\_2 values, and results will be printed. First, the X\_1 and X\_2 input nodes need to be defined. When a TensorFlow node is created, we must determine the kind of node we want to be created. X1 and X2 will be what is known as ‘placeholders,’ and these assign new values whenever a calculation is made. In our example, these placeholder nodes will be TF dot. Step One – Variable Definition X\_1 = tf.placeholder(tf.float32, name = "X\_1") X\_2 = tf.placeholder(tf.float32, name = "X\_2") When the placeholder node is created, a data type must be passed in; because we are using numbers, we used the floating-point type – tf.float32. The node also needs to be named and, when a graphical visualization of this model is looked up, that name will be seen. We’ll call our node X\_1, and we do this by passing an argument or parameter that is named ‘name’ and contains the X\_1 value. X\_2 is defined in the same way. Step Two – Computation Definition multiply = tf.multiply(X\_1, X\_2, name = "multiply") The next step is defining the node responsible for the multiplication. We do that using a tf.multiply node. X\_1 and X\_2 nodes get passed into this node, letting TensorFlow know that the nodes should be linked in the graph – it needs to get the x and y values and then multiply them. We call our multiplication node by the name of ‘multiply,’ and that sums up the whole definition of the graph. Step Three – Operation Execution Executing graph operations requires that a session is created and, in TensorFlow, this is done by using tf.Session(). Once a session has been created, we can ask it to run selected operations on the graph just by calling that session and using run to run our computations. When we run the addition operation, it will see that it has to get the X\_1 and X\_2 node values – for that, we have to provide those values. This is done by passing a parameter named feed\_dict and, for our example, the value of 1, 2, 3 is passed in for X\_1 and 4, 5, 6 for X\_2. We use print(result) to print the results: X\_1 = tf.placeholder(tf.float32, name = "X\_1") X\_2 = tf.placeholder(tf.float32, name = "X\_2") multiply = tf.multiply(X\_1, X\_2, name = "multiply") with tf.Session() as session: result = session.run(multiply, feed\_dict={X\_1:\[1,2,3\], X\_2:\[4,5,6\]}) print(result) \[ 4. 10. 18.\] Operations Required For Loading TensorFlow with Data Before you can even think about training an algorithm, you have to provide it with some data, and there are two primary ways of doing this: Loading data into memory – this is the easiest method; all data is loaded in one array to the memory, and this can be done with a simple code written in Python – this code is NOT related to TensorFlow. Using a data pipeline – there is an API built into TensorFlow to help you with loading data, performing operations, and easily providing  the machine learning algorithm with what it needs. This is the best method for when you are working with big datasets, for example, image datasets – these are known to be huge and not fit well into memory. The pipeline is equipped to manage memory n its own. Loading Data into Memory If you don’t have a very big dataset, say under 10 GB in size, this is the best method to use as the dataset fits easily into memory. One of the best libraries to use for importing CSV files in Pandas, and we will be looking at that in more detail soon. Using the Data Pipeline This method is best for the larger datasets, i.e., 50 GB, and your setup has only 8 or 18 GB of memory – in this scenario, your system would simply crash. For this, you need a TensorFlow pipeline – this helps you load in the data in batches. Each batch is sent to the pipeline and made ready for the algorithm to train on it. This is one of the best solutions because it means you can use parallel computing. In essence, the model will be trained by TensorFlow across more than one CPU, allowing for incredibly powerful neural networks to be trained. How to Create a TensorFlow Pipeline In our earlier example, we add three values manually for X\_1 and X\_2. In this tutorial, we will look at getting the data into TensorFlow. Step One – Creating the Data The first step is to generate a pair of random values using NumPy, another useful library you will learn more about later. import numpy as np x\_input = np.random.sample((1,2)) print(x\_input) \[\[0.8835775 0.23766977\]\] Step Two – Creating the Placeholder As we did in our first example, we need a placeholder created, and we will name it X. We also need to ensure that the tensor shape is explicitly specified. An array containing just two values will be loaded and the shape written as shape=\[1,2\]: \# using a placeholder x = tf.placeholder(tf.float32, shape=\[1,2\], name = 'X') Step Three – Defining the Dataset Method Next, the dataset needs to be defined so that we can populate the placeholder called X with a value. To do this, we use a method called tf.data.Dataset.from\_tensor\_slices. dataset = tf.data.Dataset.from\_tensor\_slices(x) Step 4: Creating the Pipeline In the penultimate step, the pipeline needs to be initialized. An iterator is created using make\_initializable\_iterator, and we name it ‘iterator.’ The iterator must then be called so the next batch of data can be fed in using get\_next. We only have one data batch in our example containing two values: iterator = dataset.make\_initializable\_iterator() get\_next = iteraror.get\_next() Step 5: Executing the Operation This final step is much like the final step in our first example. A session is initiated, and the operation iterator is run. We pass the NumPy generated value to feed\_dict, and, together, the two values are used to populate X (our placeholder) with a value. Last, the result is printed by using get\_next. with tf.Session() as sess: \# feed the placeholder with data sess.run(iterator.initializer, feed\_dict={ x: x\_input }) print(sess.run(get\_next)) # output \[ 0.52374458  0.71968478\] \[0.8835775  0.23766978\] Before we go any further, we need to look at how to install TensorFlow on Windows and Mac operating systems. 

Chapter 4 Installing TensorFlow on Windows and Mac ![](image_rsrc9SG.jpg)Before we look any deeper into TensorFlow, we should talk about how to install it using Anaconda. Versions: TensorFlow has support for computations over multiple GPUs and CPUs, which means that we can distribute the computations across devices to make training faster. Parallelization means you no longer have to wait weeks on end for algorithm training results. There are two TensorFlow versions for use with Windows: 

*   CPU Only Support – if your computer doesn’t have an NVIDIA GPU, this is the only version you can use 
*   GPU Support – this version provides speedier computations but should only be used where you require a strong capacity for computations. 

We are only going to use the basic version, and it is worth noting that there is no GPU support from TensorFlow for Mac users. Mac 

1.  Install Anaconda 
2.  Install TensorFlow and its dependencies by creating a .yml file 
3.  Open Jupyter Notebook 

Windows 

1.  Install Anaconda 
2.  Install the dependencies by creating a .yml file 
3.  Add TensorFlow using pip 
4.  Open Jupyter Notebook 

An Anaconda environment must be created to run TensorFlow using Jupyter. This means installing Jupyter, IPython, and TensorFlow into the right folder on your machine. You will also need to install Pandas to help with data frame manipulation. Step One - Install anaconda (the latest version for Python 3.6) on your Mac or Windows system. Step Two -  Create the .yml file. Locate the Anaconda path. Create a conda environment that has the libraries you will need: Windows: Open the Anaconda prompt and type in C:\\>where anaconda We need to know where Anaconda is because our environment will be created in this path. Mac Open a terminal and type in which anaconda Inside Anaconda, create a brand new file where you will install TensorFlow, Jupyter, and IPython. Step Three – set the working directory Here, the working directory must be specified for creating the yml file. Mac The Mac terminal will set the directory to the default Users/USERNAME . The latest folder is always shown before the $ sign on the terminal, and all libraries will be installed in this directory. If the text editor path is not the same as the working directory, use the command cd PATH at the terminal prompt. For PATH, use the path that was pasted into the text editor and do not forget to wrap it with ‘PATH,’ so the working directory is changed. In the terminal type cd anaconda3 If you are using Windows, ensure that the right folder is listed before Anaconda3, i.e. cd C:\\Users\\Admin\\Anaconda3 Step Four – create the yml file. We do this inside the new directory, and it is done to make sure the TensorFlow dependencies are installed. Here is the code to do this: Mac touch hello-tf.yml This should create a new file in anaconda3, named hello-tf.yml. Windows echo.>hello-tf.yml Again, you should see a new file called hello-tf.yml. Step Five - edit the file. Mac To do this, type the following into the terminal – this uses vim: vi hello-tf.yml After pressing the ESC button, you can use the following: 

*   Edit – press i 
*   Save – press w 
*   Quit – press q! 

Once you are in edit mode, add the following code, taking care to note that the file is both intend and case sensitive. You must include two spaces after every intend: name: hello-tfdependencies: \- python=3.6 \- jupyter \- ipython \- pandas \- pip:      \- https://storage.googleapis.com/tensorflow/MacOS/cpu/tensorflow-1.5.0-py3-none-any.whl  
  To quit, press ESC and then q! Windows There is no vim for Windows, so use Notepad: notepad hello-tf.yml Type the following in the file that opens: name: hello-tfdependencies: \- python=3.6 \- jupyter \- ipython \- pandas In this step, only the conda environment is being prepared for Windows; TensorFlow is installed in the next step. Step Six – compiling the file Use the following code to compile the file (Mac and Windows): conda env create -f hello-tf.yml Step Seven – activating your conda environment Nearly there. You should have two conda environments, including an isolated one with all the libraries you will need going forward.  To activate the environment, switch to hello-tf: Mac source activate hello-tf Windows activate hello-tf An important thing to do here is to ensure all the dependencies are together in the environment, allowing them to use each other from within a single environment. If any are missing, you need to go back and start again. To do this: Mac which python which jupyter which ipython As an optional step, you can also see if there are any updates: pip install –upgrade tensorflow Windows Only – Install TensorFlow: where python where jupyter where ipython Now you have two Python environments – the primary one and the new one you create using hello-tf. Note that TensorFlow is only installed on hello-tf, not in the primary environment. Windows users can install TensorFlow using this command: pip install tensorflow Open Jupyter Notebook This is the same for both operating systems; TensorFlow can be opened with Jupyter: Step One - activate conda Mac source activate hello-tf Windows conda activate hello-tf Step Two – open Jupyter jupyter notebook The Jupyter Notebook should show you every file in your working directory. Creating a new Notebook is as simple as clicking New>Python 3. New Notebooks are saved to the working directory automatically. TensorFlow can be imported from within Jupyter, using the alias tf. Click Run and a new cell is created: import tensorflow as tf Let’s use TensorFlow to write some code: hello = tf.constant(‘Hello, everyone!’) hello You have created a new tensor. Step Three – deleting the file Now the file in Jupyter, called Untitled.ipynb, can be deleted. Step Four – Closing Jupyter You can close Jupyter in two ways – from the Notebook or using the terminal or prompt. From Jupyter: From the main Jupyter panel, click on Logout, and you will be sent to the logout page. From the Terminal/Prompt: From the terminal or the prompt, run CTRL+C twice. After the first time, you will be asked whether you want the Notebook shut down; press CTRL+C again, and you will be logged out. In the next chapter, we’ll dig deeper into the TensorFlow basics. 

Chapter 5 A Deeper Dig Into TensorFlow ![](image_rsrc9SG.jpg)In TensorFlow, every computation involves one or more tensors, which are matrices or vectors of n-dimensions, representing every different data type. Every value inside a tensor shares a data type with a shape that is known or partially known. The data shape is the array or matrix dimensionality. Tensors can come from computation results or the input data; graphs are used for every operation, and each graph contains successive computations. The operations are all connected and are known as op nodes. While a graph will show the ops and the node connections, it will not show any values. The node edges are the tensors and are the way the operation is populated with data. With machine learning, we feed feature vectors (object lists) to the models. They can be of any data type but will typically be the primary method of populating tensors. The values ‘flow’ through the tensor into the op node, resulting in a new tensor; this then gets used in another operation, and all of this can be seen in the graph. Tensor Representation Tensors are feature vector collections, or arrays, of n-dimensions.  Let’s say, for example, that we have a matrix of 2x3, containing values 1 through 6. We would write it like this: ![](image_rsrc9SH.jpg)This would be represented in TensorFlow as: \[\[1, 2, 3\], \[4, 5, 6\]\]                   If we were to go further and use the values 1 through 8 for creating a three-dimensional matrix, we would have this: ![](image_rsrc9SJ.jpg)And TensorFlow represents this as: \[ \[\[1, 2\], \[\[3, 4\], \[\[5, 6\], \[\[7,8\] \]                 Tensor Types Every computation in TensorFlow goes through at least one tensor, which is simply an object that has three properties: 

*   Name – Label (unique) 
*   Shape – dimension 
*   dtype – data type 

Every TensorFlow operation requires you to manipulate a tensor, and there are four primary ones you can create: 

*   tf.Variable 
*   tf.constant 
*   tf.placeholder 
*   tf.SparseTensor 

We will be looking at how to create the first two of those. Before we start, make sure the conda environment has been activated with TensorFlow (see last chapter) – once done, import TensorFlow like this: \# Import tf import tensorflow as tf Create an n-dimension Tensor We start by creating a scalar, a single dimension tensor, and we use tf.constant() to do this: tf.constant(value, dtype, name = "") arguments \- \`value\`: n dimension value for defining the tensor. Optional \- \`dtype\`: Define the data type:    \- \`tf.string\`: String variable    \- \`tf.float32\`: Float variable    \- \`tf.int16\`: Integer variable \- "name": Name of the tensor. Optional. By default, \`Const\_1:0\`                   The code below will let you create a 0-dimension tensor:      \## rank 0 \# Default name r1 = tf.constant(1, tf.int16) print(r1)             Output Tensor("Const:0", shape=(), dtype=int16)                    And \# Named my\_scalar r2 = tf.constant(1, tf.int16, name = "my\_scalar") print(r2)                       Output Tensor("my\_scalar:0", shape=(), dtype=int16)                     Tensor names are used on each tensor and every tensor object has a name, a dimension, and a data type. We can change the type of the data to define different tensors, i.e. decimal values or strings: \# Decimal r1\_decimal = tf.constant(1.12345, tf.float32) print(r1\_decimal) \# String r1\_string = tf.constant("Hi everyone", tf.string) print(r1\_string)                        Output Tensor("Const\_1:0", shape=(), dtype=float32) Tensor("Const\_2:0", shape=(), dtype=string)           And the following code can be used to create a one dimension tensor:          \## Rank 1r1\_vector = tf.constant(\[1,3,5\], tf.int16)  
print(r1\_vector)  
r2\_boolean = tf.constant(\[True, True, False\], tf.bool)  
print(r2\_boolean)  
  Output Tensor("Const\_3:0", shape=(3,), dtype=int16)  
Tensor("Const\_4:0", shape=(3,), dtype=bool)                       
  You would see that the shape has just one column. If you wanted two dimensions, the brackets must be closed after every row: \## Rank 2  
r2\_matrix = tf.constant(\[ \[1, 2\],  
                          \[3, 4\] \],tf.int16)  
print(r2\_matrix)                         
  Output Tensor("Const\_5:0", shape=(2, 2), dtype=int16)                   The resulting matrix has two rows and two columns, populated with the values 1 through 4. Another level is added with the brackets to create a three-dimension matrix: \## Rank 3  
r3\_matrix = tf.constant(\[ \[\[1, 2\],  
                           \[3, 4\],  
                           \[5, 6\]\] \], tf.int16)  
print(r3\_matrix)                        Output Tensor("Const\_6:0", shape=(1, 3, 2), dtype=int16) Tensor Shape When the tensor is printed, the shape is guessed, but you can use the shape property to get the tensor shape. The code below builds a matrix with numbers 10 through 15 and checks the m\_shape shape: \# Shape of tensor  
m\_shape = tf.constant(\[ \[10, 11\],  
                        \[12, 13\],  
                        \[14, 15\] \]                        
                     )  
m\_shape.shape                 Output TensorShape(\[Dimension(3), Dimension(2)\])      The resulting matrix consists of three rows, two columns. In TensorFlow, you will find several useful commands for creating matrices or vectors filled with 1 or 0. Let’s say, for example, that you wanted a one-dimension tensor, filled with 0, with a shape of 10 – this code would do that:    \# Create a vector of 0  
print(tf.zeros(10))                     Output Tensor("zeros:0", shape=(10,), dtype=float32)               A given matrix shape can be used to create a vector of ones. The m\_shape is 3x2, and a tensor can be created with three rows filled with ones like this: \# Create a vector of ones with the same number of rows as m\_shape  
print(tf.ones(m\_shape.shape\[0\]))                       Output Tensor("ones\_1:0", shape=(3,), dtype=float32)      If 1 is passed as a value into the bracket, a vector of ones can be created as equal to the columns in the m\_shape matrix: \# A vector of ones is created with the same number of columns  as m\_shape  
print(tf.ones(m\_shape.shape\[1\]))                        Output Tensor("ones\_2:0", shape=(2,), dtype=float32)                    Lastly, a 3x2 matrix may be created with just ones: print(tf.ones(m\_shape.shape))                    Output Tensor("ones\_3:0", shape=(3, 2), dtype=float32)                  Data Types The data type is another tensor property. Tensors are only allowed one data type at a time, and you can use dtype to return the type: print(m\_shape.dtype)                     Output <dtype: 'int32'>                   On occasion, you may want the data type changed, and this is done using the tf.cast method. For example, we could convert a float tensor to an integer, like this: \# Change type of data  
type\_float = tf.constant(3.123456789, tf.float32) type\_int = tf.cast(type\_float, dtype=tf.int32) print(type\_float.dtype) print(type\_int.dtype)                   Output <dtype: 'float32'> <dtype: 'int32'>                  The data type is automatically chosen by TensorFlow if you don’t  specify the argument when you create the tensor. If, for example, you passed text, TensorFlow would assume it is a string, and that is what would be passed. Creating an Operator Now you know how a tensor is created, we should look at mathematical operations and how to perform them. All of the basic operations are included in TensorFlow, and, starting simple, we’ll compute a specified number’s square. The tensor is created using one argument, and we use tf.sqrt(x) to construct the square – x is a floating-point number: x = tf.constant(\[2.0\], dtype = tf.float32) print(tf.sqrt(x))                       Output Tensor("Sqrt:0", shape=(1,), dtype=float32)                      Note We got a tensor object as the output, not, as we expected, the square of 2. In this example, the tensor definition was printed, rather than the operation evaluation. Later, we will look at how to use TensorFlow for executing the operations. Here are the most common operations, each of which requires at least one argument: 

*   tf.add(a, b) 
*   tf.substract(a, b) 
*   tf.multiply(a, b) 
*   tf.div(a, b) 
*   tf.pow(a, b) 
*   tf.exp(a) 
*   tf.sqrt(a) 

Here’s an example: \# Add tensor\_a = tf.constant(\[\[1,2\]\], dtype = tf.int32) tensor\_b = tf.constant(\[\[3, 4\]\], dtype = tf.int32) tensor\_add = tf.add(tensor\_a, tensor\_b)print(tensor\_add) Output Tensor("Add:0", shape=(1, 2), dtype=int32)                       What we did was created two tensors, one containing 1 and 2, the other containing 3 and 4, and then the tensors were added. Note that both tensors must be of the same shape, and a multiplication can be executed over both. \# Multiply tensor\_multiply = tf.multiply(tensor\_a, tensor\_b) print(tensor\_multiply)                  Output Tensor("Mul:0", shape=(1, 2), dtype=int32)                       Variables The constant tensors we have created so far are not of much use. All data have different values, but you can use the variable class to capture this. Creating a variable requires the use of the method called tf.get\_variable(): tf.get\_variable(name = "", values, dtype, initializer) argument \- \`name = ""\`: Name of the variable \- \`values\`: Dimension of the tensor \- \`dtype\`: Type of data. Optional \- \`initializer\`: How to initialize the tensor. Optional If we specify the initializer, we do not need to add the values in; the initializer shape is used instead. For example, the next code will create a variable with two dimensions and two random values. A random value is returned by TensorFlow by default, and the variable is named var: \# Create a Variable \## Create 2 Randomized values var = tf.get\_variable("var", \[1, 2\]) print(var.shape)                        Output (1, 2)                   You can also create variables with one row and two columns and the variable dimension is created using \[1,2\]. The tensor’s initial values are zero; when a model is trained, we need the initial values so the feature weights can be computed. This is how the initial value is set to zero: var\_init\_1 = tf.get\_variable("var\_init\_1", \[1, 2\], dtype=tf.int32, initializer=tf.zeros\_initializer) print(var\_init\_1.shape)                 Output (1, 2)                   A constant tensor’s values can also be passed in a variable by using the tf.constant() method to create the constant tensor. The initial values are 10, 20, 30, and 40 and the shape will be 2x2: \# Create a 2x2 matrixtensor\_const = tf.constant(\[\[10, 20\], \[30, 40\]\]) \# Initialize the first value of the tensor equals to tensor\_const var\_init\_2 = tf.get\_variable("var\_init\_2", dtype=tf.int32,  initializer=tensor\_const) print(var\_init\_2.shape)                 Output (2, 2)                   Placeholders Placeholders feed tensors; they are used for initializing the data, so it flows in the tensors. The method feed\_dict is used to supply a placeholder within a session. This example shows you how to create the placeholder: tf.placeholder(dtype,shape=None,name=None ) arguments: \- \`dtype\`: Type of data \- \`shape\`: dimension of the placeholder. Optional. By default, shape of the data \- \`name\`: Name of the placeholder. Optional                     data\_placeholder\_a = tf.placeholder(tf.float32, name = "data\_placeholder\_a") print(data\_placeholder\_a)                       Output Tensor("data\_placeholder\_a:0", dtype=float32)                    Sessions There are three main components that TensorFlow works around: 

*   Graph – all math ops are done in the graph; the ops are represented by nodes, and they can create new tensors 
*   Tensor -  representative of the data that goes between the operations 
*   Session – used for executing the graph operations. A session must be opened to provide the tensor values to the graph, and the operator must be run for an output to be created. 

Session and graphs are independent; a session can be run, and you  can use the values for later computations. Here’s an example. Step One – Create the x and y tensors \## Create, run  and evaluate a session x = tf.constant(\[2\]) y = tf.constant(\[4\])                    Step Two – multiply x and y to create the operator:  
\## Create operator multiply = tf.multiply(x, y)                    Step Three – open a session so all the computations can be done and then close it when you are finished. \## Create a session to run the code sess = tf.Session()result\_1 = sess.run(multiply) print(result\_1) sess.close()                    Output \[8\]                      Sessions can also be created inside blocks with the advantage that sessions are closed automatically. with tf.Session() as sess:    result\_2 = multiply.eval() print(result\_2)                         Output \[8\]                      This example shows you how to see the tensor values after creating a session: \## Check the tensors created before sess = tf.Session() print(sess.run(r1)) print(sess.run(r2\_matrix)) print(sess.run(r3\_matrix))                      Output 1 \[\[1 2\] \[3 4\]\] \[\[\[1 2\] \[3 4\] \[5 6\]\]\]                       By default, variables are empty, even when a tensor has been created. To use a variable, it has to be initialized using the tf.global\_variable\_initializer() object. You can also check the variable values created earlier, using the run() method: sess.run(tf.global\_variables\_initializer()) print(sess.run(var)) print(sess.run(var\_init\_1)) print(sess.run(var\_init\_2))                     Output \[\[-0.05356491  0.75867283\]\] \[\[0 0\]\] \[\[10 20\] \[30 40\]\]                       The placeholder created earlier can be fed with a real value, and the data passed to the feed\_dict() method. Here’s how to take the data\_placeholder\_a power of 2: import numpy as np power\_a = tf.pow(data\_placeholder\_a, 2) with tf.Session() as sess:  data = np.random.rand(1, 10)  print(sess.run(power\_a, feed\_dict={data\_placeholder\_a: data}))  # Will succeed.                 Output \[\[0.05478134 0.27213147 0.8803037  0.0398424  0.21172127 0.01444725  0.02584014 0.3763949  0.66022706 0.7565559 \]\]                       Graphs A dataflow scheme is used to represent the computations, and the graph shows each operation’s data dependencies. Algorithms consist of successive operations and are one of the more convenient ways to see the coordination of the computations. Graphs show both nodes and edges – the former represents an operation, and the latter is the tensor. Dependent on the dependencies between operations, the tensor can create new tensors or take in the input data. The graph structure connects the nodes and the way the operations are fed, but all you see are the node connections, not the outputs. In the next chapter, we’ll look at TensorBoard. 

Chapter 6 An Overview of TensorBoard ![](image_rsrc9SG.jpg)TensorBoard is the graph visualization interface for TensorFlow and is also a way for other tools to understand their model, debug it, and optimize it. Have a look at the image below – this is the main TensorBoard panel from the graph that you will be generating in this chapter. ![](image_rsrc9SK.jpg)As you can see at the top of the image, there are several tabs on the main screen, each linked to the specific information you might want added when your model is run: 

*   Scalars – this shows all sorts of useful information you might want to see while your model is being trained 
*   Graphs – this shows you your model 
*   Histogram – this shows you a histogram with the weights displayed 
*   Distribution –  this shows how the weights are distributed 
*   Projector – this shows the T-SNE algorithm and PCA (Principal Component Analysis) and is used for dimensionality reduction. 

Throughout this chapter, you are going to learn how to train a machine/deep learning model, and, in a later chapter, we’ll see how it works. The graph tells you all you need to know about the way the model works: 

1.  The data is enqueued to the model – data equivalent to the batch size is fed to the model 
2.  The data is fed to the tensors 
3.  The model is trained 
4.  The number of batches used during training is displayed 
5.  The model is saved to disk 

We can imagine a neural network as being a dark box, and TensorBoard is the inspection tool we need to see what is inside it. The tool lets us see and understand the operation’s dependencies, shows us the weight computations, the loss function, and lots of other information critical to understanding what is going on. Once you can bring it all together, you get to see the bigger picture, have a better way of debugging, and find ways of making improvements. Neural networks determine the best way of connecting the neurons and the number of layers a model needs before the best outcomes can be predicted. Once the architecture has been defined, you need to do more than just train your model – you also need some metrics that help you compute how accurate the predictions are. We call this metric a loss function, and your object is to minimize that loss function as much as possible. In simple terms, the smaller the loss  function, the fewer errors are being made by your model. Every machine learning algorithm will repeat the computations as many times as needed to bring the loss down to the minimum, and doing this requires that a learning rate is defined. The learning rate is the speed you expect your model to learn at – set it too high, and your model will have so little time, it won't be able to learn. TensorBoard is one of the best tools for seeing these metrics and spotting any issues that could potentially arise. Neural networks may not find a solution for many weeks, and TensorBoard keeps the metrics updated constantly. Because of this, you can see how well the model is working without needing to wait until the end, and that means you can make changes where you need to, and at the time you need to. In this chapter, we are going to look at how you open TensorBoard in both Windows and Mac – don’t worry about the code, for now, we’ll focus on that later. Step One – importing the right training libraries \## Import the library import tensorflow as tf import numpy as n Step Two – creating the data – an array containing five columns, and 10,000 rows: X\_train = (np.random.sample((10000,5))) y\_train =  (np.random.sample((10000,1))) X\_train.shape Output (10000, 5) The codes you will see in a minute are going to transform your data and then create the learning model. Note that our learning rate is  equal to 0.1 – make that rate higher, and your model will fail to find a solution. Throughout many of the tutorials on using TensorFlow, we will make use of the TensorFlow estimator, an API with the mathematical computations you need. Step Three – creating log files Creating log files requires the path to be specified, using the model\_dir argument. In the next example, your model will be stored where you store your Python file or Notebook, i.e., the working directory. TensorFlow creates a folder in this path, names it ‘train,’ and gives it a child folder named ‘linreg.’ feature\_columns = \[ tf.feature\_column.numeric\_column('x', shape=X\_train.shape\[1:\])\] DNN\_reg = tf.estimator.DNNRegressor(feature\_columns=feature\_columns, \# Indicate where to store the log file    model\_dir='train/linreg',    hidden\_units=\[500, 300\],   optimizer=tf.train.ProximalAdagradOptimizer(      learning\_rate=0.1,      l1\_regularization\_strength=0.001    ) ) Output INFO:tensorflow:Using default config. INFO:tensorflow:Using config: {'\_model\_dir': 'train/linreg', '\_tf\_random\_seed': None, '\_save\_summary\_steps': 100, '\_save\_checkpoints\_steps': None, '\_save\_checkpoints\_secs': 600, '\_session\_config': None, '\_keep\_checkpoint\_max': 5, '\_keep\_checkpoint\_every\_n\_hours': 10000, '\_log\_step\_count\_steps': 100, '\_train\_distribute': None, '\_service': None, '\_cluster\_spec': <tensorflow.python.training.server\_lib.ClusterSpec object at 0x1818e63828>, '\_task\_type': 'worker', '\_task\_id': 0, '\_global\_id\_in\_cluster': 0, '\_master': '', '\_evaluation\_master': '', '\_is\_chief': True, '\_num\_ps\_replicas': 0, '\_num\_worker\_replicas': 1} Step Four – training the model In this final step, the information is written to the model directory by TensorFlow: \# Train the estimator train\_input = tf.estimator.inputs.numpy\_input\_fn(    x={"x": X\_train},    y=y\_train, shuffle=False,num\_epochs=None) DNN\_reg.train(train\_input,steps=3000) Output INFO:tensorflow:Calling model\_fn.  
INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Create CheckpointSaverHook.  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Saving checkpoints for 1 into train/linreg/model.ckpt.  
INFO:tensorflow:loss = 40.060104, step = 1  
INFO:tensorflow:global\_step/sec: 197.061  
INFO:tensorflow:loss = 10.62989, step = 101 (0.508 sec)  
INFO:tensorflow:global\_step/sec: 172.487  
 INFO:tensorflow:loss = 11.255318, step = 201 (0.584 sec)  
INFO:tensorflow:global\_step/sec: 193.295  
INFO:tensorflow:loss = 10.604872, step = 301 (0.513 sec)  
INFO:tensorflow:global\_step/sec: 175.378  
INFO:tensorflow:loss = 10.090343, step = 401 (0.572 sec)  
INFO:tensorflow:global\_step/sec: 209.737  
INFO:tensorflow:loss = 10.057928, step = 501 (0.476 sec)  
INFO:tensorflow:global\_step/sec: 171.646  
INFO:tensorflow:loss = 10.460144, step = 601 (0.583 sec)  
INFO:tensorflow:global\_step/sec: 192.269  
INFO:tensorflow:loss = 10.529617, step = 701 (0.519 sec)  
INFO:tensorflow:global\_step/sec: 198.264  
INFO:tensorflow:loss = 9.100082, step = 801 (0.504 sec)  
INFO:tensorflow:global\_step/sec: 226.842  
INFO:tensorflow:loss = 10.485607, step = 901 (0.441 sec)  
INFO:tensorflow:global\_step/sec: 152.929  
INFO:tensorflow:loss = 10.052481, step = 1001 (0.655 sec)  
INFO:tensorflow:global\_step/sec: 166.745  
INFO:tensorflow:loss = 11.320213, step = 1101 (0.600 sec)  
INFO:tensorflow:global\_step/sec: 161.854  
INFO:tensorflow:loss = 9.603306, step = 1201 (0.619 sec)  
INFO:tensorflow:global\_step/sec: 179.074  
INFO:tensorflow:loss = 11.110269, step = 1301 (0.556 sec)  
INFO:tensorflow:global\_step/sec: 202.776  
INFO:tensorflow:loss = 11.929443, step = 1401 (0.494 sec)  
INFO:tensorflow:global\_step/sec: 144.161  
INFO:tensorflow:loss = 11.951693, step = 1501 (0.694 sec)  
INFO:tensorflow:global\_step/sec: 154.144  
INFO:tensorflow:loss = 8.620987, step = 1601 (0.649 sec)  
INFO:tensorflow:global\_step/sec: 151.094  
INFO:tensorflow:loss = 10.666125, step = 1701 (0.663 sec)  
INFO:tensorflow:global\_step/sec: 193.644  
INFO:tensorflow:loss = 11.0349865, step = 1801 (0.516 sec)  
INFO:tensorflow:global\_step/sec: 189.707  
 INFO:tensorflow:loss = 9.860596, step = 1901 (0.526 sec)  
INFO:tensorflow:global\_step/sec: 176.423  
INFO:tensorflow:loss = 10.695, step = 2001 (0.567 sec)  
INFO:tensorflow:global\_step/sec: 213.066  
INFO:tensorflow:loss = 10.426752, step = 2101 (0.471 sec)  
INFO:tensorflow:global\_step/sec: 220.975  
INFO:tensorflow:loss = 10.594796, step = 2201 (0.452 sec)  
INFO:tensorflow:global\_step/sec: 219.289  
INFO:tensorflow:loss = 10.4212265, step = 2301 (0.456 sec)  
INFO:tensorflow:global\_step/sec: 215.123  
INFO:tensorflow:loss = 9.668612, step = 2401 (0.465 sec)  
INFO:tensorflow:global\_step/sec: 175.65  
INFO:tensorflow:loss = 10.009649, step = 2501 (0.569 sec)  
INFO:tensorflow:global\_step/sec: 206.962  
INFO:tensorflow:loss = 10.477722, step = 2601 (0.483 sec)  
INFO:tensorflow:global\_step/sec: 229.627  
INFO:tensorflow:loss = 9.877638, step = 2701 (0.435 sec)  
INFO:tensorflow:global\_step/sec: 195.792  
INFO:tensorflow:loss = 10.274586, step = 2801 (0.512 sec)  
INFO:tensorflow:global\_step/sec: 176.803  
INFO:tensorflow:loss = 10.061047, step = 2901 (0.566 sec)  
INFO:tensorflow:Saving checkpoints for 3000 into train/linreg/model.ckpt.  
INFO:tensorflow:Loss for final step: 10.73032. <tensorflow.python.estimator.canned.dnn.DNNRegressor at 0x1818e63630>  
  With the log events in place, we can now launch TensorBoard. While Jupyter is on port 8888, TensorBoard will run on port 6006. Mac users should use the terminal to open TensorBoard while Windows users should use the Anaconda prompt. Mac \# not the same for all  
cd /Users/hello/tuto\_TF  
source activate hello-tf! Windows cd C:\\Users\\Admin\\Anaconda3  
activate hello-tf Make sure the path matches where your Notebook or code is stored. Top open TensorBoard, use the relevant code below: Mac tensorboard --logdir=./train/linreg Windows tensorboard --logdir=.\\train\\linreg  
  TensorBoard should be found at http://localhost:6006, so paste the URL into your browser. If you get a message that looks similar to the one below, the log file cannot be found. Ensure that cd has been pointed to the correct path or make sure that the log event was created – if not, run the code again. ![](image_rsrc9SM.jpg)You can use CTRL+C to close TensorBoard. We’re going to take a short break from TensorFlow and look at three important libraries, starting with NumPy. 

Chapter 7 NumPy ![](image_rsrc9SG.jpg)NumPy is one of the most important open-source libraries in Python for data science, mathematical, engineering and scientific programming and is one of the best tools for performing statistical and mathematical operations. That is why it works very well with multiplication for matrices and multi-dimensional arrays. The library was specifically built to work with random numbers, linear algebra, Fourier transformations, N-dimensional arrays, and so on, and is easily integrated into Fortran, C, and C++. In this chapter, we will look at the important NumPy functions you need for working with TensorFlow. Why NumPy? NumPy is highly memory-efficient, which means it is well-equipped to handle large amounts of data. When it comes to reshaping and matric multiplication, NumPy is convenient and fast, and TensorFlow makes good use of it in the backend for matrix multiplications. Installing NumPy Most of the time, NumPy is automatically installed when you install TensorFlow but, if for some reason it isn’t, you can install it in two ways: Using Anaconda Prompt conda install -c anaconda numpy Using Jupyter Notebook import sys  
 !conda install --yes --prefix {sys.prefix} numpy To import NumPy and check you have the right version, use the following command: import numpy as np                       By doing this, the NumPy namespace is renamed as np, and this means we can prefix methods, functions, and methods using ‘np’ rather than ‘numpy.’ To check which version you have, use this command: print (np.\_\_version\_\_) Creating a NumPy Array The easiest way to create a NumPy array is with a Python list: myPythonList = \[1,7,9,2\] Python lists can be converted to arrays using the np.array object: numpy\_array\_from\_list = np.array(myPythonList) And to show the list contents: numpy\_array\_from\_list Output array(\[1,7,9,2\])  
In practical terms, we don’t need to declare a list; we can combine the operation: In practice, there is no need to declare a Python List. The operation can be combined. a  = np.array(\[1,7,9,2\])                         Mathematical Operations on Arrays There are several mathematical operations you can perform on arrays, including subtraction, addition, multiplication, and division. The syntax used is the name of the array, the operation you want  done, and the operation, for example: numpy\_array\_from\_list + 10 Output: array(\[11, 17, 19, 12\]) That example adds 10 to every element in the array. Shape of The Array It is also possible to check the array shape using the array name followed by the object shape. You can also use dtypes to check the type in the same way: import numpy as np  
a  = np.array(\[1,2,3\])  
print(a.shape)  
print(a.dtype)  
(3)  
int64 Integers are whole numbers, i.e., without a decimal place. If an array is created using decimals, the type will change from int to float: \#### Different type  
b  = np.array(\[1.1,2.0,3.2\])  
print(b.dtype)  
float64  
   Two-Dimension Arrays Dimensions can be added using a comma (,) but it must be included inside the brackets: \### two-dimension  
c = np.array(\[(1,2,3),  
              (4,5,6)\])  
print(c.shape)  
(2, 3) Three-Dimension Arrays And you can add even more dimensions, like this: \### three-dimension  
d = np.array(\[  
    \[\[1, 2,3\],  
        \[4, 5, 6\]\],  
    \[\[7, 8,9\],  
        \[10, 11, 12\]\]  
\])  
print(d.shape)  
(2, 2, 3)  
  np.zeros and np.ones It is possible to create and fill a matrix with ones and zeroes and use it when the weights are initialized at the first TensorFlow iteration. The syntax: numpy.zeros(shape, dtype=float, order='C') numpy.ones(shape, dtype=float, order='C') In the syntax, ‘shape’ is the array shape, dtype is the datatype and is optional with a default value of float64, and order defaults to C, one of the vital row styles. For example: np.zeros((2,2)) Output array(\[\[0., 0.\],  
          \[0., 0.\]\]) Another example: np.zeros((2,2), dtype=np.int16)  
  Output : array(\[\[0, 0\],  
         \[0, 0\]\], dtype=int16) \## Create 1  
np.ones((1,2,3), dtype=np.int16)                          
array(\[\[\[1, 1, 1\],          
       \[1, 1, 1\]\]\], dtype=int16)                        Reshaping and Flattening the Data Sometimes, the data needs to be reshaped – it may be too wide, and it needs to be long: e  = np.array(\[(1,2,3), (4,5,6)\])  
print(e)  
e.reshape(3,2) Output \[\[1 2 3\]  
\[4 5 6\]\]                         
array(\[\[1, 2\],         
        \[3, 4\],         
        \[5, 6\]\])                         Some neural networks, such as convnets, require that the array be flattened and we can do this using the flatten() method: e.flatten()                 
array(\[1, 2, 3, 4, 5, 6\])                         hstack and vstack The NumPy library contains two very good functions that allow you to append data vertically or horizontally. Let’s see how they work with an example: \## Stack  
f = np.array(\[1,2,3\])  
g = np.array(\[4,5,6\])  
print('Horizontal Append:', np.hstack((f, g)))  
print('Vertical Append:', np.vstack((f, g)))  
Horizontal Append: \[1 2 3 4 5 6\]  
Vertical Append: \[\[1 2 3\]  
\[4 5 6\]\] Generating Random Numbers If you wanted a random number generated for a Gaussian distribution, you would use: numpy .random.normal(loc, scale, size) Breaking this down: 

*   Loc : this is the mean, the distribution center 
*   Scale : the standard deviation. 
*   Size : the number of returns 

\## Generate a random number from a normal distribution  
normal\_array = np.random.normal(5, 0.5, 10)  
print(normal\_array)                       
\[5.56171852 4.84233558 4.65392767 4.946659   4.85165567 5.61211317 4.46704244 5.22675736 4.49888936 4.68731125\]                   
  Asarray Have a look at the two-dimensional matrix below; it has four columns and four rows filled by ones: A = np.matrix(np.ones((4,4)))                    You cannot change the matrix value, even if you wanted to because a copy cannot be changed. np.array(A)\[2\]=2  
print(A)                          
\[\[1. 1. 1. 1.\]  
\[1. 1. 1. 1.\]  
\[1. 1. 1. 1.\]  
\[1. 1. 1. 1.\]\] A matrix is not mutable. You can add some modification to the matrix with asarray though; the example below shows using asarray to change the third-row value with 2: np.asarray(A)\[2\]=2  
print(A) The first line is converting a matrix called A into an array and chooses the third rows: \[\[1. 1. 1. 1.\]  
      \[1. 1. 1. 1.\]  
      \[2. 2. 2. 2.\] # new value  
      \[1. 1. 1. 1.\]\] Arange Sometimes you might want a value to be spaced evenly across a specified interval. Let’s say that you want values created from 1 through 10; you would use arange for this: numpy.arange(start, stop, step) Start and Stop are the start and end of the interval, while Step  indicates the spaces between each value – the default is 1. Here’s an example: np.arange(1, 11)                   
array(\[ 1,  2,  3,  4,  5,  6,  7,  8,  9, 10\])                   If you wanted the step changed, a third number would need to be added inside the parenthesis: np.arange(1, 14, 4)                        
array(\[ 1,  5,  9, 13\])                   Linspace Linspace is used to provide samples that are evenly spaced: numpy.linspace(start, stop, num, endpoint) Start and Stop are the start and end of the sequences, Num indicates how many samples are to be generated (50 is the default), and Endpoint is the final value if it is True but, if it is False, there will not be a stop value. You could, for example, create 10 values, evenly spaced, from 1 to 5: np.linspace(1.0, 5.0, num=10)                      
array(\[1.        , 1.44444444, 1.88888889, 2.33333333, 2.77777778,       3.22222222, 3.66666667, 4.11111111, 4.55555556, 5.        \])                    The endpoint can be set as false if you don’t want a final digit included in the interval: np.linspace(1.0, 5.0, num=5, endpoint=False)                       
array(\[1. , 1.8, 2.6, 3.4, 4.2\]) LogSpace This will return numbers evenly spaced on a log scale, and it shares the same parameters that np.linspace has: np.logspace(3.0, 4.0, num=4)                       
array(\[ 1000. ,  2154.43469003,  4641.58883361, 10000.        \])                         Lastly, use itemsize to check what size an array is: x = np.array(\[1,2,3\], dtype=np.complex128)  
x.itemsize                      Indexing and Slicing NumPy makes it trivial to slice data, and, in our example, we are going to slice the matrix called e. Python requires you to use brackets to return columns or rows: \## Slice  
e  = np.array(\[(1,2,3), (4,5,6)\])  
print(e)  
\[\[1 2 3\]  
\[4 5 6\]\] The array or column must start at 0 in NumPy: \## First column  
print('First row:', e\[0\])  
\## Second col  
print('Second row:', e\[1\])  
First row: \[1 2 3\]  
Second row: \[4 5 6\] Much like other languages, in Python, the values that come before commas are rows, while the values to the right are columns. A : must be added before the index if you want to choose a specific column,  and using : also indicates that you want every row from the chosen column. print('Second column:', e\[:,1\])                    
  Second column: \[2 5\]                       
If you want the first pair of values from row 2, you will use : to choose all columns up to number two: ##  
  print(e\[1, :2\])                         
  \[4 5\]                   
  Statistical Functions NumPy offers some of the best statistical functions: 

| Function  || NumPy  |
| --- | --- |
| Min  || np.min()  |
| Max  || np.max()  |
| Mean  || np.mean()  |
| Median  || np.median()  |
| Standard deviation  || np.stdt()  |

Examples of these Functions: \## Statistical function \### Min print(np.min(normal\_array)) \### Max print(np.max(normal\_array)) \### Mean print(np.mean(normal\_array)) \### Median print(np.median(normal\_array)) \### Sd print(np.std(normal\_array)) 4.467042435266913 5.612113171990201 4.934841002270593 4.846995625786663 0.3875019367395316 Dot Product NumPy also allows you to use np.dot to compute dot products: \## Linear algebra  
\### Dot product: product of two arrays  
f = np.array(\[1,2\])  
g = np.array(\[4,5\])  
\### 1\*4+2\*5  
np.dot(f, g)  
  14 Matrix Multiplication In much the same way, np.matmul can be used for computing matrices multiplication: \### Matmul: matruc product of two arrays  
h = \[\[1,2\],\[3,4\]\]  
i = \[\[5,6\],\[7,8\]\]  
\### 1\*5+2\*7 = 19  
np.matmul(h, i)  
array(\[\[19, 22\],         
            \[43, 50\]\])             Determinant Finally, np.linalg.det() can be used for computing determinants – the dimension is taken care of by NumPy \## Determinant 2\*2 matrix  
\### 5\*8-7\*6np.linalg.det(i)                       
\-2.000000000000005                        

Chapter 8 Pandas ![](image_rsrc9SG.jpg)Pandas is another critical open-source library that lets you manipulate Python data. It is built on NumPy, which means it cannot operate without NumPy. With Pandas, you get an easy way to create data, manipulate it, and wrangle it, and it is perfect for time series data. Why Pandas? Pandas offers the following benefits: 

*   Handles missing data easily 
*   It makes use of DataFrame for data structures that are multi-dimensional and Series of data structures that are one-dimensional 
*   It slices data efficiently 
*   It allows for flexibility in merging, concatenating and reshaping data 
*   It offers a very powerful tool for working with time series 

As you can see, Pandas is one of the most data analysis libraries, useful for analyzing and manipulating data. It gives us powerful, easy-to-use data structures and easy ways to operate on them. Installing Pandas Pandas is typically installed by default when you install TensorFlow but, if for some reason it isn’t, you can install it in the following ways: Mac Using Jupyter Notebook, type: import sys  
!conda install --yes --prefix {sys.prefix} pandas                       Windows At the Anaconda prompt, type: conda install -c anaconda pandas What is a Data Frame? Data frames are two-dimensional arrays, standard data storage structures; the columns and rows (axes) are labeled, and they store data in a tabular format – data is stored in the rows and the names in the columns. What is a Series? A series is also a data structure, this time one-dimensional. Series can be of any data structure, such as a string, float, or integer, and are useful for doing computations or when you want a one-dimensional array returned. Series cannot have more than one column and has just one parameter – data, which could be a scalar value, a dictionary, or a list: pd.Series(\[1., 2., 3.\])                    
0    1.0  
1    2.0  
2    3.0  
dtype: float64                   The index can be added using ‘index’ and is useful to help you give the rows names. The length and the column size should be equal: pd.Series(\[1., 2., 3.\], index=\['a', 'b', 'c'\]) Now, we are going to create a series in Pandas, and the third rows  will have missing values. In Python, missing values are known as NaN – Not a Number –, and the missing value will be created by NumPy: np.nan artificially pd.Series(\[1,2,np.nan\]) Output 0    1.0  
1    2.0  
2    NaN  
dtype: float64 Create a Data Frame A NumPy array can be converted to a Pandas data frame just by using pd.DataFrame(). You can also convert it the other way, too, using np.array(). \## Numpy to pandas  
import numpy as np  
h = \[\[1,2\],\[3,4\]\]  
df\_h = pd.DataFrame(h)  
print('Data Frame:', df\_h)  
\## Pandas to numpy  
df\_h\_n = np.array(df\_h)  
print('Numpy array:', df\_h\_n)  
Data Frame:    0  1  
0  1  2  
1  3  4  
Numpy array: \[\[1 2\]  
\[3 4\]\] Pandas DataFrames can also be created by using a dictionary: dic = {'Name': \["James", "Green"\], 'Age': \[40, 50\]}  
pd.DataFrame(data=dic)                          

|  || Age  || Name  |
| --- | --- | --- |
| 0  || 40  || James  |
| 1  || 50  || Green  |

Range Data In Pandas, you will also find a useful API that lets you create a date range: pd.data\_range(date,period,frequency) There are three parameters – the start date, how many periods there are (optional if you specify an end date), and the frequency – D (day), M (month), and Y (year). \## Create date  
\# Days  
dates\_d = pd.date\_range('20200101', periods=6, freq='D')  
print('Day:', dates\_d) Output Day: DatetimeIndex(\['2020-01-01', '2020-01-02', '2020-01-03', '2020-01-04', '2020-01-05', '2020-01-06'\], dtype='datetime64\[ns\]', freq='D') \# Months  
dates\_m = pd.date\_range('20200101', periods=6, freq='M')  
print('Month:', dates\_m) Output Month: DatetimeIndex(\['2020-01-31', '2020-02-28', '2020-03-31', '2020-04-30','2020-05-31', '2020-06-30'\], dtype='datetime64\[ns\]', freq='M') Inspecting the Data The dataset head or tail can be checked by using the DataFrame name and head() or tail(). Step One – use NumPy for creating a random sequence with four columns and six rows. random = np.random.randn(6,4)    Step Two – Next, use Pandas to create a DataFrame with an index of dates\_m. Every row will be provided with an index or name that corresponds to a date. Lastly, the four columns are named as the argument columns: \# Create data with date  
df = pd.DataFrame(random,  
                  index=dates\_m,  
                  columns=list('ABCD'))  
  Step Three – use the head() function df.head(3) 

|  || A  || B  || C  || D  |
| --- | --- | --- | --- | --- |
| 2020-01-31  || 1.139433  || 1.318510  || \-0.181334  || 1.615822  |
| 2020-02-28  || \-0.081995  || \-0.063582  || 0.857751  || \-0.527374  |
| 2020-03-31  || \-0.519179  || 0.080984  || \-1.454334  || 1.314947  |

Step Four – use the tail function: df.tail(3)  
  

|  || A  || B  || C  || D  |
| --- | --- | --- | --- | --- |
| 2020-04-30  || \-0.685448  || \-0.011736  || 0.622172  || 0.104993  |
| 2020-05-31  || \-0.935888  || \-0.731787  || \-0.558729  || 0.768774  |
| 2020-06-30  || 1.096981  || 0.949180  || \-0.196901  || \-0.471556  |

Step Five –  one of the best ways to learn about the data is using describe(), as it gives you several pieces of information about the dataset – counts, std, means, max, min, and percentile: df.describe()  
  

|  || A  || B  || C  || D  |
| --- | --- | --- | --- | --- |
| count  || 6.000000  || 6.000000  || 6.000000  || 6.000000  |
| mean  || 0.002317  || 0.256928  || \-0.151896  || 0.467601  |
| std  || 0.908145  || 0.746939  || 0.834664  || 0.908910  |
| min  || \-0.935888  || \-0.731787  || \-1.454334  || \-0.527374  |
| 25%  || \-0.643880  || \-0.050621  || \-0.468272  || \-0.327419  |
| 50%  || \-0.300587  || 0.034624  || \-0.189118  || 0.436883  |
| 75%  || 0.802237  || 0.732131  || 0.421296  || 1.178404  |
| max  || 1.139433  || 1.318510  || 0.857751  || 1.615822  |

Slice the Data To finish this short tutorial, here’s how to slice DataFrames. The easiest way is to extract data from a specified column, using the name of the column: \## Slice  
\### Using name  
df\['A'\]  
2020-01-31   -0.168655  
2020-02-28    0.689585  
2020-03-31    0.767534  
2020-04-30    0.557299  
2020-05-31   -1.547836  
2020-06-30    0.511551  
Freq: M, Name: A, dtype: float64 If you want more than one column, you need to double up on the brackets – \[\[..,..\]\]. The first pair indicates that you want columns selected, and the second pair specifies the columns you want returned. df\[\['A', 'B'\]\].                          

|  || A  || B  |
| --- | --- | --- |
| 2020-01-31  || \-0.168655  || 0.587590  |
| 2020-02-28  || 0.689585  || 0.998266  |
| 2020-03-31  || 0.767534  || \-0.940617  |
| 2020-04-30  || 0.557299  || 0.507350  |
| 2020-05-31  || \-1.547836  || 1.276558  |
| 2020-06-30  || 0.511551  || 1.572085  |

You can also slice the rows, for example, to return three rows: \### using slice for row  
df\[0:3\] 

|  || A  || B  || C  || D  |
| --- | --- | --- | --- | --- |
| 2020-01-31  || \-0.168655  || 0.587590  || 0.572301  || \-0.031827  |
| 2020-02-28  || 0.689585  || 0.998266  || 1.164690  || 0.475975  |
| 2020-03-31  || 0.767534  || \-0.940617  || 0.227255  || \-0.341532  |

You can select columns by their names using the loc function. The values that precede the comma are the rows, and those after are the columns. Brackets are required if you want two or more columns: \## Multi col  
df.loc\[:,\['A','B'\]\]     

|  || A  || B  |
| --- | --- | --- |
| 2020-01-31  || \-0.168655  || 0.587590  |
| 2020-02-28  || 0.689585  || 0.998266  |
| 2020-03-31  || 0.767534  || \-0.940617  |
| 2020-04-30  || 0.557299  || 0.507350  |
| 2020-05-31  || \-1.547836  || 1.276558  |
| 2020-06-30  || 0.511551  || 1.572085  |

Pandas offers another way of selecting more than one row or column – iloc(). Instead of the name of the columns, it uses the index – the example below would give you the same DataFrame you saw above: df.iloc\[:, :2\] 

|  || A  || B  |
| --- | --- | --- |
| 2020-01-31  || \-0.168655  || 0.587590  |
| 2020-02-28  || 0.689585  || 0.998266  |
| 2020-03-31  || 0.767534  || \-0.940617  |
| 2020-04-30  || 0.557299  || 0.507350  |
| 2020-05-31  || \-1.547836  || 1.276558  |
| 2020-06-30  || 0.511551  || 1.572085  |

Dropping a Column Columns can be dropped using pd.drop(): df.drop(columns=\['A', 'C'\])          

|  || B  || D  |
| --- | --- | --- |
| 2020-01-31  || 0.587590  || \-0.031827  |
| 2020-02-28  || 0.998266  || 0.475975  |
| 2020-03-31  || \-0.940617  || \-0.341532  |
| 2020-04-30  || 0.507350  || \-0.296035  |
| 2020-05-31  || 1.276558  || 0.523017  |
| 2020-06-30  || 1.572085  || \-0.594772  |

Concatenation Two Pandas DataFrames can be concatenated using pd.concat(). First, you need to create both the DataFrames: import numpy as np  
df1 = pd.DataFrame({'name': \['James', 'Green','Phillip'\],  
                      'Age': \['25', '30', '50'\]},  
                    index=\[0, 1, 2\])  
df2 = pd.DataFrame({'name': \['Andrew', 'Green' \],  
                     'Age': \['26', '11'\]},  
                    index=\[3, 4\]) Lastly, the wo are concatenated: df\_concat = pd.concat(\[df1,df2\])  
df\_concat 

|  || Age  || name  |
| --- | --- | --- |
| 0  || 25  || James  |
| 1  || 30  || Green  |
| 2  || 50  || Phillip  |
| 3  || 26  || Andrew  |
| 4  || 11  || Green  |

Drop\_duplicates If there is duplicate data in a dataset, drop\_duplicates is the easiest way of excluding any rows of duplicate data. As you can see, we have duplicate information in the ‘name’ column – Green is there twice: df\_concat.drop\_duplicates('name')  
  

|  || Age  || name  |
| --- | --- | --- |
| 0  || 25  || James  |
| 1  || 30  || Green  |
| 2  || 50  || Phillip  |
| 3  || 26  || Andrew  |

Sort Values We can also sort the values using sort\_values: df\_concat.sort\_values('Age') 

|  || Age  || name  |
| --- | --- | --- |
| 4  || 11  || Green  |
| 0  || 25  || James  |
| 3  || 26  || Andrew  |
| 1  || 30  || Green  |
| 2  || 50  || Phillip  |

Rename: Changing the Index Columns can be renamed using rename(); value one is the name of the current column while value two is the new name: df\_concat.rename(columns={"name": "Surname", "Age": "Age\_ppl"})  
  

|  || Age\_ppl  || Surname  |
| --- | --- | --- |
| 0  || 25  || James  |
| 1  || 30  || Green  |
| 2  || 50  || Phillip  |
| 3  || 26  || Andrew  |
| 4  || 11  || Green  |

Importing CSV Files We’ll be making use of the adult dataset for our TensorFlow tutorial, a common dataset for classification tasks – you can find it at https://archive.ics.uci.edu/ml/machine-learning-databases/adult/adult.data, and the data is in the CSV format. The dataset has the following categorical values: 

*   education 
*   marital 
*   native\_country 
*   occupation 
*   race 
*   relationship 
*   sex 
*   workclass 

And these continuous variables: 

*   age 
*   capital\_gain 
*   capital\_loss 
*   education\_num 
*   fnlwgt 
*   hours\_week 

Importing a CSV dataset is done using pd.read\_csv() with this syntax: pandas.read\_csv(filepath\_or\_buffer,sep=', ',\`names=None\`,\`index\_col=None\`,\`skipinitialspace=False\`) Have a look at this example:  
  \## Import csv  
import pandas as pd  
\## Define path data  
COLUMNS = \['age','workclass', 'fnlwgt', 'education', 'education\_num', 'marital',  
           'occupation', 'relationship', 'race', 'sex', 'capital\_gain', 'capital\_loss',  
           'hours\_week', 'native\_country', 'label'\]  
PATH = "https://archive.ics.uci.edu/ml/machine-learning-databases/adult/adult.data"  
df\_train = pd.read\_csv(PATH,  
                       skipinitialspace=True,  
                       names = COLUMNS,  
                       index\_col=False)  
df\_train.shape Output (32561, 15) Groupby The groupby() method is the easiest way of seeing the data, and it can help provide a summary of the data in groups. The methods in groupby() include: 

*   count: count 
*   max: max 
*   mean: mean 
*   median: median 
*   min: min 
*   standard deviation: sdt 

In groupby(), you use the specific column you want the method applied to. Here’s an example, using the adult dataset, of a single grouping. This gives you the mean of every continuous variable by revenue type – over or under $50k. df\_train.groupby(\['label'\]).mean()                       

|  || age  || fnlwgt  || education \_num  || capital\_ gain  || capital\_ loss  || hours\_ week  |
| --- | --- | --- | --- | --- | --- | --- |
| label  ||  ||  ||  ||  ||  ||  |
| <=50K  || 36.783738  || 190340.86517  || 9.595065  || 148.752468  || 53.142921  || 38.840210  |
| \>50K  || 44.249841  || 188005.00000  || 11.611657  || 4006.142456  || 195.001530  || 45.473026  |

You can also obtain the age minimum by household type: df\_train.groupby(\['label'\])\['age'\].min() label  
<=50K    17  
\>50K     19  
Name: age, dtype: int64        And it is also possible to do the grouping using more than one column. For example, you can use both marital status and household type to get the max capital: df\_train.groupby(\['label', 'marital'\])\['capital\_gain'\].max()     
label  marital                
<=50K  Divorced                 34095  
       Married-AF-spouse         2653  
       Married-civ-spouse       41310  
       Married-spouse-absent     6849  
       Never-married            34095  
       Separated                 7443  
       Widowed                   6849  
\>50K   Divorced                 99999  
       Married-AF-spouse         7298  
       Married-civ-spouse       99999  
        Married-spouse-absent    99999  
       Never-married            99999  
       Separated                99999  
       Widowed                  99999  
Name: capital\_gain, dtype: int64 In the next chapter, we will look at Scikit-Learn. 

Chapter 9 Scikit-Learn ![](image_rsrc9SG.jpg)Scikit-learn is one of the more popular Python libraries used for machine learning. The open-source library, built on NumPy,  supports some of the top algorithms, such as random forest, XGBoost, KNN, SVM, and others. It is used for dimensionality reduction, preprocessing, regression, classification, model selection, and clustering. It isn’t hard to use, and it gives great results, but it doesn’t have any support for parallel computing; while it can be used for deep learning, it isn’t the best, particularly once you learn to use TensorFlow. Download Scikit-Learn Downloading Scikit-learn is not difficult. You may already have installed it using conda, but you will likely need to update it: Step One – Activate the TensorFlow environment: source activate hello-tf Step Two – Use the conda command to remove Scikit-learn: conda remove scikit-learn Step Three – Install the developer version of Scikit-learn and all the libraries you need: conda install -c anaconda git  
pip install Cython  
pip install h5py  
pip install git+git://github.com/scikit-learn/scikit-learn.git Machine Learning With Scikit-Learn I have divided this into two – machine learning and using LIME to trust the model. In the first part, we will see how a pipeline is built, a model created and the hyperparameters tuned while in the second part, we will look at the model selection. Step One – Importing the Data We are going to import the adult dataset using Pandas – the continuous variable type must be converted to float format. There are eight categorical variables: 

*   education 
*   marital 
*   native\_country 
*   occupation 
*   race 
*   relationship 
*   sex 
*   workclass 

And six continuous variables: 

*   age 
*   capital\_gain 
*   capital\_loss 
*   education\_num 
*   fnlwgt 
*   hours\_week 

The list will be manually filled, so you understand the columns we will use. Constructing a variable list could be done faster, using the following: \## List Categorical  
CATE\_FEATURES = df\_train.iloc\[:,:-1\].select\_dtypes('object').columns  
print(CATE\_FEATURES)  
\## List continuous  
CONTI\_FEATURES =  df\_train.\_get\_numeric\_data()  
print(CONTI\_FEATURES)  
  Import the data using the following: \# Import dataset  
import pandas as pd  
\## Define the path data  
COLUMNS = \['age','workclass', 'fnlwgt', 'education', 'education\_num', 'marital',  
           'occupation', 'relationship', 'race', 'sex', 'capital\_gain', 'capital\_loss',  
           'hours\_week', 'native\_country', 'label'\] \### Define the continuous list  
CONTI\_FEATURES  = \['age', 'fnlwgt','capital\_gain', 'education\_num', 'capital\_loss', 'hours\_week'\] \### Define the categorical list  
CATE\_FEATURES = \['workclass', 'education', 'marital', 'occupation', 'relationship', 'race', 'sex', 'native\_country'\]  
  \## Prepare data  
features = \['age','workclass', 'fnlwgt', 'education', 'education\_num', 'marital',  
           'occupation', 'relationship', 'race', 'sex', 'capital\_gain', 'capital\_loss',  
            'hours\_week', 'native\_country'\]  
  PATH = "https://archive.ics.uci.edu/ml/machine-learning-databases/adult/adult.data"  
  df\_train = pd.read\_csv(PATH, skipinitialspace=True, names = COLUMNS, index\_col=False)  
df\_train\[CONTI\_FEATURES\] =df\_train\[CONTI\_FEATURES\].astype('float64')  
df\_train.describe()  
  

|  || age  || fnlwgt  || Education\_ num  || capital\_ gain  || capital\_ loss  || hours\_ week  |
| --- | --- | --- | --- | --- | --- | --- |
| count  || 32561.000000  || 3.256100e+04  || 32561.000000  || 32561.000000  || 32561.000000  || 32561.000000  |
| mean  || 38.581647  || 1.897784e+05  || 10.080679  || 1077.648844  || 87.303830  || 40.437456  |
| std  || 13.640433  || 1.055500e+05  || 2.572720  || 7385.292085  || 402.960219  || 12.347429  |
| min  || 17.000000  || 1.228500e+04  || 1.000000  || 0.000000  || 0.000000  || 1.000000  |
| 25%  || 28.000000  || 1.178270e+05  || 9.000000  || 0.000000  || 0.000000  || 40.000000  |
| 50%  || 37.000000  || 1.783560e+05  || 10.000000  || 0.000000  || 0.000000  || 40.000000  |
| 75%  || 48.000000  || 2.370510e+05  || 12.000000  || 0.000000  || 0.000000  || 45.000000  |
| max  || 90.000000  || 1.484705e+06  || 16.000000  || 99999.000000  || 4356.000000  || 99.000000  |

The unique values for the native\_country features can be counted – you will see that there is just one household from Holland, in the Netherlands. While we won't get any useful information from this, we get an error thrown during the training: df\_train.native\_country.value\_counts()          United-States                 29170  
Mexico                          643  
?                               583  
Philippines                     198  
Germany                         137  
Canada                          121  
Puerto-Rico                     114  
 El-Salvador                     106  
India                           100  
Cuba                             95  
England                          90  
Jamaica                          81  
South                            80  
China                            75  
Italy                            73  
Dominican-Republic               70  
Vietnam                          67  
Guatemala                        64  
Japan                            62  
Poland                           60  
Columbia                         59  
Taiwan                           51  
Haiti                            44  
Iran                             43  
Portugal                         37  
Nicaragua                        34  
Peru                             31  
France                           29  
Greece                           29  
Ecuador                          28  
Ireland                          24  
Hong                             20  
Cambodia                         19  
Trinidad & Tobago                  19  
Thailand                         18  
Laos                             18  
Yugoslavia                       16  
Outlying-US(Guam-USVI-etc)       14  
Honduras                         13  
Hungary                          13  
Scotland                         12  
 Holland-Netherlands                1  
Name: native\_country, dtype: int64 The following can be removed, as it offers no real use: \## Drop Netherland, it is only one row  
df\_train = df\_train\[df\_train.native\_country != "Holland-Netherlands"\] Next, the continuous features position is stored in a list – this will be required shortly. The next code loops over every column name stored in CONTI\_FEATURES; I will obtain the location (number) and append it to the conti\_features list: \## Get the column index of the categorical features  
conti\_features = \[\]  
for i in CONTI\_FEATURES:  
    position = df\_train.columns.get\_loc(i)  
    conti\_features.append(position)  
print(conti\_features)   
\[0, 2, 10, 4, 11, 12\]                             The next code does exactly the same for the categorical variable: \## Get the column index of the categorical features  
categorical\_features = \[\]  
for i in CATE\_FEATURES:  
    position = df\_train.columns.get\_loc(i)  
    categorical\_features.append(position)  
print(categorical\_features)    
  \[1, 3, 5, 6, 7, 8, 9, 13\]                                  
  Last, look at the dataset, and you will see that every categorical  feature is actually a string. Models cannot be given string values; they must be transformed, using: dummy variable.df\_train.head(5)                         You will need a column for every feature group. The code below will compute how many columns you need in total: print(df\_train\[CATE\_FEATURES\].nunique(),  
      'There are',sum(df\_train\[CATE\_FEATURES\].nunique()), 'groups in the entire dataset') workclass          9  
education         16  
marital            7  
occupation        15  
relationship       6  
race               5  
sex                2  
native\_country    41  
  dtype: int64 There are 101 groups in the entire dataset  
  As you can see, there are 101 groups; the codes below can be used to visualize these: unique() return the unique values of each categorical feature. for i in CATE\_FEATURES:  
    print(df\_train\[i\].unique())  
\['State-gov' 'Self-emp-not-inc' 'Private' 'Federal-gov' 'Local-gov' '?'  
'Self-emp-inc' 'Without-pay' 'Never-worked'\]  
\['Bachelors' 'HS-grad' '11th' 'Masters' '9th' 'Some-college' 'Assoc-acdm'  
'Assoc-voc' '7th-8th' 'Doctorate' 'Prof-school' '5th-6th' '10th'  
 '1st-4th' 'Preschool' '12th'\]  
\['Never-married' 'Married-civ-spouse' 'Divorced' 'Married-spouse-absent'  
'Separated' 'Married-AF-spouse' 'Widowed'\]  
\['Adm-clerical' 'Exec-managerial' 'Handlers-cleaners' 'Prof-specialty'  
'Other-service' 'Sales' 'Craft-repair' 'Transport-moving'  
'Farming-fishing' 'Machine-op-inspct' 'Tech-support' '?'  
'Protective-serv' 'Armed-Forces' 'Priv-house-serv'\]  
\['Not-in-family' 'Husband' 'Wife' 'Own-child' 'Unmarried' 'Other-relative'\]  
\['White' 'Black' 'Asian-Pac-Islander' 'Amer-Indian-Eskimo' 'Other'\]  
\['Male' 'Female'\]  
\['United-States' 'Cuba' 'Jamaica' 'India' '?' 'Mexico' 'South'  
'Puerto-Rico' 'Honduras' 'England' 'Canada' 'Germany' 'Iran'  
'Philippines' 'Italy' 'Poland' 'Columbia' 'Cambodia' 'Thailand' 'Ecuador'  
'Laos' 'Taiwan' 'Haiti' 'Portugal' 'Dominican-Republic' 'El-Salvador'  
'France' 'Guatemala' 'China' 'Japan' 'Yugoslavia' 'Peru'  
'Outlying-US(Guam-USVI-etc)' 'Scotland' 'Trinidad & Tobago' 'Greece'  
'Nicaragua' 'Vietnam' 'Hong' 'Ireland' 'Hungary'\]  
  The training set will have 101 columns plus seven more for the continuous features. Scikit-learn does the conversion: 

*   The string is converted to ID; the LabelEncoder function does this. 
*   Each ID is transposed into a column – 101 columns will capture the groups in the categorical features, done by the  OneHotEncoder function. 

Step Two – Creating the Training and Test Sets Now we need to split our dataset into two – 80% for training 20% for testing. Use train\_test\_split for this, passing two arguments – the feature’s DataFrame and the label’s dataframe. And test\_size will help you specify the test set size: from sklearn.model\_selection import train\_test\_split  
X\_train, X\_test, y\_train, y\_test = train\_test\_split(df\_train\[features\],  
                                                    df\_train.label,  
                                                    test\_size = 0.2,  
                                                    random\_state=0)  
X\_train.head(5)  
print(X\_train.shape, X\_test.shape)  
  (26048, 14) (6512, 14)                     
  Step Three – Building the Pipeline The pipeline is how we give consistent data to the model. In our example, we need the continuous variables standardized and the categorical data converted. Any operation may be done in the pipeline, including creating new variables. from sklearn.preprocessing import StandardScaler, OneHotEncoder, LabelEncoder  
from sklearn.compose import ColumnTransformer, make\_column\_transformer  
from sklearn.pipeline import make\_pipeline  
from sklearn.linear\_model import LogisticRegression The pipeline performs two operations before the logistic classifier is fed: 

1.  The variable is standardized – \`StandardScaler()\`\` 
2.  The categorical features are converted - OneHotEncoder(sparse=False)

We can do this using make\_column\_transformer. The columns you want to be transformed and the transformations you want must be defined; i.e., continuous standardization can be done with: conti\_features, StandardScaler() inside make\_column\_transformer. The OneHotEncoder object encodes the label automatically: preprocess = make\_column\_transformer(  
    (conti\_features, StandardScaler()),  
    ### Must be numeric, not a string, for specifying  the column name  
    (categorical\_features, OneHotEncoder(sparse=False))  
) And fit\_transform will let you test the pipeline: preprocess.fit\_transform(X\_train).shape       Output (26048, 107)                       
  Your data transformer is now ready; we can use make\_pipeline to build the pipeline, transform the data, and feed it to the logistic regression: model = make\_pipeline(  
    preprocess,  
    LogisticRegression())  
  To train a model using Scikit-learn, you will use the pipeline, followed by the fit object and the score object will print the model accuracy: model.fit(X\_train, y\_train)  
print("logistic regression score: %f" % model.score(X\_test, y\_test)) logistic regression score: 0.850891                        
  Lastly, predict\_proba is used for the class predictions, returning each class’s probability: model.predict\_proba(X\_test)                      array(\[\[0.83576663, 0.16423337\],  
       \[0.94582765, 0.05417235\],  
       \[0.64760587, 0.35239413\],  
       ...,  
       \[0.99639252, 0.00360748\],  
       \[0.02072181, 0.97927819\],  
       \[0.56781353, 0.43218647\]\]) Step Four – The Pipeline and Grid Searches Hyperparameter tuning is a tedious job. You could evaluate the model by changing the training set size and evaluating performance and, to see the score metrics, repeat ten times. That is too time-consuming. Scikit-learn has a useful function for tuning and cross-validation: Cross-Validation This means that, while the training is ongoing, the training set slips in folds n times, evaluating the model n times. Let’s say we have cv=10  – the set would be trained and then evaluated ten times. Each time, nine folds are chosen at random for training, and the last is for evaluation. Grid Search Every classifier has one or more hyperparameters that need training. You could try some different values, or you could use a parameter grid. The object called GridSearchCV can be used with a dictionary you create to store the hyperparameters for tuning. The hyperparameters are listed with the values. For example, the following would help you with tuning the C parameter: 'logisticregression\_\_C': \[0.1, 1.0, 1.0\]: The name goes first, in lowercase, two underscores and the parameter. The model attempts these four values – 0.001, 0.01, 0.1, 1 Ten folds are used to train the model: from sklearn.model\_selection import GridSearchCV  
\# Construct parameter grid  
param\_grid = {  
    'logisticregression\_\_C': \[0.001, 0.01,0.1, 1.0\],  
    }  
  GridSearchCV is used to train the model, using cv and the parameter grid: \# Train model  
grid\_clf = GridSearchCV(model,  
                        param\_grid,  
                        cv=10,  
                        iid=False)  
grid\_clf.fit(X\_train, y\_train)  
  Output GridSearchCV(cv=10, error\_score='raise-deprecating',  
       estimator=Pipeline(memory=None,  
     steps=\[('columntransformer', ColumnTransformer(n\_jobs=1, remainder='drop', transformer\_weights=None,  
         transformers=\[('standardscaler', StandardScaler(copy=True, with\_mean=True, with\_std=True), \[0, 2, 10, 4, 11, 12\]), ('onehotencoder', OneHotEncoder(categorical\_features=None, categories=None,...ty='l2', random\_state=None, solver='liblinear', tol=0.0001,  
          verbose=0, warm\_start=False))\]),  
       fit\_params=None, iid=False, n\_jobs=1,  
       param\_grid={'logisticregression\_\_C': \[0.001, 0.01, 0.1, 1.0\]},  
       pre\_dispatch='2\*n\_jobs', refit=True, return\_train\_score='warn',  
       scoring=None, verbose=0)  
  Use best\_params\_ to get the best parameters: grid\_clf.best\_params\_                      
  Output {'logisticregression\_\_C': 1.0}                     
  Once the model is trained on four regularization values, you see the optimal parameter: print("best logistic regression from grid search: %f" % grid\_clf.best\_estimator\_.score(X\_test, y\_test))  
  best logistic regression from grid search: 0.850891 To get the probability predictions: grid\_clf.best\_estimator\_.predict\_proba(X\_test)                   array(\[\[0.83576677, 0.16423323\],  
       \[0.9458291 , 0.0541709 \],  
       \[0.64760416, 0.35239584\],  
       ...,  
       \[0.99639224, 0.00360776\],  
       \[0.02072033, 0.97927967\],  
       \[0.56782222, 0.43217778\]\])  
  XGBoost Model Using Scikit-Learn XGBoost is one of the top classifiers, better than random forest. It is a challenging classifier because many parameters need tuning – GridSearchCV could choose the right parameter, but we’re going to look at another, faster way. RandomizedSearchCV lets you choose each hyperparameter value randomly following each iteration. For example, if 1,000 iterations are used for training, 1,000 combinations need evaluating. XGBoost must be imported. Use pip3 or do the following: use import sys  
!{sys.executable} -m pip install xgboost  
  In Jupyter: import xgboost  
from sklearn.model\_selection import RandomizedSearchCV  
from sklearn.model\_selection import StratifiedKFold  
  Next, you need to specify which parameters you need to tune. For  now, we are only going to tune two, each with two values; it is worth noting that XGBoost takes a while to train and too many hyperparameters costs dearly in time: params = {  
        'xgbclassifier\_\_gamma': \[0.5, 1\],  
        'xgbclassifier\_\_max\_depth': \[3, 4\]  
        }  
Using the XGBoost classifier, we build a new pipeline. Up to 600 estimators can be defined. Note that you can tune n\_estimators. model\_xgb = make\_pipeline(  
    preprocess,  
    xgboost.XGBClassifier(  
                          n\_estimators=600,  
                          objective='binary:logistic',  
                          silent=True,  
                          nthread=1)  
) The Stratified K-Folds cross-validator may be used for improving cross-validations. Constructing three folds will speed the computation up, but the quality will be lower. You can improve this by choosing five or ten folds: Four iterations are used for training the model: skf = StratifiedKFold(n\_splits=3,  
                      shuffle = True,  
                      random\_state = 1001)  
random\_search = RandomizedSearchCV(model\_xgb,  
                                   param\_distributions=params,  
                                   n\_iter=4,  
                                   scoring='accuracy',  
                                   n\_jobs=4,  
                                    cv=skf.split(X\_train, y\_train),  
                                   verbose=3,  
                                   random\_state=1001)  
   Now the model can be trained: #grid\_xgb = GridSearchCV(model\_xgb, params, cv=10, iid=False)  
random\_search.fit(X\_train, y\_train)              Fitting 3 folds for each of 4 candidates, totaling 12 fits  
\[CV\] xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=0.5 ............  
\[CV\] xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=0.5 ............  
\[CV\] xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=0.5 ............  
\[CV\] xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=0.5 ............  
\[CV\]  xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=0.5, score=0.8759645283888057, total= 1.0min  
\[CV\] xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=0.5 ............  
\[CV\]  xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=0.5, score=0.8729701715996775, total= 1.0min  
\[CV\]  xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=0.5, score=0.8706519235199263, total= 1.0min  
\[CV\] xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=0.5 ............  
\[CV\] xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=1 ..............  
 \[CV\]  xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=0.5, score=0.8735460094437406, total= 1.3min  
\[CV\] xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=1 ..............  
\[CV\]  xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=1, score=0.8722791661868018, total=  57.7s  
\[CV\] xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=1 ..............  
\[CV\]  xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=1, score=0.8753886905447426, total= 1.0min  
\[CV\] xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=1 ..............  
\[CV\]  xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=0.5, score=0.8697304768486523, total= 1.3min  
\[CV\] xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=1 ..............  
\[CV\]  xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=0.5, score=0.8740066797189912, total= 1.4min  
\[CV\] xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=1 ..............  
\[CV\]  xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=1, score=0.8707671043538355, total= 1.0min  
\[CV\]  xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=1, score=0.8729701715996775, total= 1.2min  
\[Parallel(n\_jobs=4)\]: Done  10 out of  12 | elapsed:  3.6min remaining:   43.5s  
\[CV\]  xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=1, score=0.8736611770125533, total= 1.2min  
\[CV\]  xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=1, score=0.8692697535130154, total= 1.2min \[Parallel(n\_jobs=4)\]: Done  12 out of  12 | elapsed:  3.6min finished  
/Users/Thomas/anaconda3/envs/hello-tf/lib/python3.6/site-packages/sklearn/model\_selection/\_search.py:737: DeprecationWarning: The default of the \`iid\` parameter will change from True to False in version 0.22 and will be removed in 0.24. This will change numeric results when test-set sizes are unequal. DeprecationWarning)  
  RandomizedSearchCV(cv=<generator object \_BaseKFold.split at 0x1101eb830>,  
          error\_score='raise-deprecating',  
          estimator=Pipeline(memory=None,  
     steps=\[('columntransformer', ColumnTransformer(n\_jobs=1, remainder='drop', transformer\_weights=None,  
         transformers=\[('standardscaler', StandardScaler(copy=True, with\_mean=True, with\_std=True), \[0, 2, 10, 4, 11, 12\]), ('onehotencoder', OneHotEncoder(categorical\_features=None, categories=None,...  
       reg\_alpha=0, reg\_lambda=1, scale\_pos\_weight=1, seed=None,  
       silent=True, subsample=1))\]),  
          fit\_params=None, iid='warn', n\_iter=4, n\_jobs=4,  
          param\_distributions={'xgbclassifier\_\_gamma': \[0.5, 1\], 'xgbclassifier\_\_max\_depth': \[3, 4\]},  
          pre\_dispatch='2\*n\_jobs', random\_state=1001, refit=True,  
          return\_train\_score='warn', scoring='accuracy', verbose=3)  
  XGBoost clearly has a much better score than the last regression: print("Best parameter", random\_search.best\_params\_)  
 print("best logistic regression from grid search: %f" % random\_search.best\_estimator\_.score(X\_test, y\_test))  
Best parameter {'xgbclassifier\_\_max\_depth': 3, 'xgbclassifier\_\_gamma': 0.5}  
best logistic regression from grid search: 0.873157  
random\_search.best\_estimator\_.predict(X\_test)                      
array(\['<=50K', '<=50K', '<=50K', ..., '<=50K', '>50K', '<=50K'\],      dtype=object)                     
   Creating a DNN Using MLPClassifier in Scikit-Learn Lastly, Scikit-learn can be used for training deep learning algorithms – the classifier can be found at MLPClassifier: from sklearn.neural\_network import MLPClassifier                 The algorithm is defined as: 

*   Adam solver 
*   ReLu activation function 
*   Alpha = 0.0001 
*   batch size 150 
*   Two hidden layers, one with 100 and one with 50 neurons 

model\_dnn = make\_pipeline(  
    preprocess,  
    MLPClassifier(solver='adam',  
                  alpha=0.0001,  
                  activation='ReLu',  
                     batch\_size=150,  
                    hidden\_layer\_sizes=(200, 100),  
                    random\_state=1))  
  The number of layers can be changed to make improvements: model\_dnn.fit(X\_train, y\_train)  
  print("DNN regression score: %f" % model\_dnn.score(X\_test, y\_test))                     
  DNN regression score: 0.821253 Trusting Your Model With LIME You now need to use a tool to trust your model, and the best one is called LIME – Local Interpretable Model-Agnostic Explanations. In the same way that a doctor cannot trust a diagnosis made by a computer, you cannot always trust your model; to do that, you need to understand the features used to make predictions – LIME can tell you want those features are. Data Preparation Before you can run LIME, you need to do a couple of things, not least, installing lime – use pip to do this. To locally approximate a model, LIME uses an object called LimeTabularExplainer. This needs: 

*   A NumPy format dataset 
*   The feature names – feature\_names 
*   The class names – class\_names 
*   The categorical feature column index – categorical\_features 
*   The categorical feature group names –  categorical\_names 

Creating a NumPy Training Set df\_train may be copied from Pandas and converted to NumPy: df\_train.head(5)  
\# Create numpy data  
df\_lime = df\_train  
df\_lime.head(3) The unique() object allows you to get to the label \# Get class name  
class\_names = df\_lime.label.unique()  
class\_names  
array(\['<=50K', '>50K'\], dtype=object)                       
  Categorical Features Column Index: You used a method earlier to get the group name, and you can use the same one now; LabelEncoder is used to encode the label and repeated on every categorical feature: ##  
import sklearn.preprocessing as preprocessing  
categorical\_names = {}  
for feature in CATE\_FEATURES:  
    le = preprocessing.LabelEncoder()  
    le.fit(df\_lime\[feature\])  
    df\_lime\[feature\] = le.transform(df\_lime\[feature\])  
    categorical\_names\[feature\] = le.classes\_  
print(categorical\_names)      
{'workclass': array(\['?', 'Federal-gov', 'Local-gov', 'Never-worked', 'Private',  
       'Self-emp-inc', 'Self-emp-not-inc', 'State-gov', 'Without-pay'\],  
       dtype=object), 'education': array(\['10th', '11th', '12th', '1st-4th', '5th-6th', '7th-8th', '9th',  
       'Assoc-acdm', 'Assoc-voc', 'Bachelors', 'Doctorate', 'HS-grad',  
       'Masters', 'Preschool', 'Prof-school', 'Some-college'\],  
      dtype=object), 'marital': array(\['Divorced', 'Married-AF-spouse', 'Married-civ-spouse',  
       'Married-spouse-absent', 'Never-married', 'Separated', 'Widowed'\],  
      dtype=object), 'occupation': array(\['?', 'Adm-clerical', 'Armed-Forces', 'Craft-repair',  
       'Exec-managerial', 'Farming-fishing', 'Handlers-cleaners',  
       'Machine-op-inspct', 'Other-service', 'Priv-house-serv',  
       'Prof-specialty', 'Protective-serv', 'Sales', 'Tech-support',  
       'Transport-moving'\], dtype=object), 'relationship': array(\['Husband', 'Not-in-family', 'Other-relative', 'Own-child',  
       'Unmarried', 'Wife'\], dtype=object), 'race': array(\['Amer-Indian-Eskimo', 'Asian-Pac-Islander', 'Black', 'Other',  
       'White'\], dtype=object), 'sex': array(\['Female', 'Male'\], dtype=object), 'native\_country': array(\['?', 'Cambodia', 'Canada', 'China', 'Columbia', 'Cuba',  
       'Dominican-Republic', 'Ecuador', 'El-Salvador', 'England',  
       'France', 'Germany', 'Greece', 'Guatemala', 'Haiti', 'Honduras',  
       'Hong', 'Hungary', 'India', 'Iran', 'Ireland', 'Italy', 'Jamaica',  
       'Japan', 'Laos', 'Mexico', 'Nicaragua',  
       'Outlying-US(Guam-USVI-etc)', 'Peru', 'Philippines', 'Poland',  
       'Portugal', 'Puerto-Rico', 'Scotland', 'South', 'Taiwan',  
       'Thailand', 'Trinidad & Tobago', 'United-States', 'Vietnam',  
       'Yugoslavia'\], dtype=object)}  
df\_lime.dtypes                    
age               float64  
workclass           int64  
fnlwgt            float64  
 education           int64  
education\_num     float64  
marital             int64  
occupation          int64  
relationship        int64  
race                int64  
sex                 int64  
capital\_gain      float64  
capital\_loss      float64  
hours\_week        float64  
native\_country      int64  
label              object  
dtype: object  
   Your dataset is ready, and you can now construct a new one. To steer clear of LIME errors, the data is transformed externally to the pipeline. The LimeTabularExplainer training set should be a NumPy array but without a string. Using the method above, your training dataset has already been converted: from sklearn.model\_selection import train\_test\_split  
X\_train\_lime, X\_test\_lime, y\_train\_lime, y\_test\_lime = train\_test\_split(df\_lime\[features\],  
                                                    df\_lime.label,  
                                                    test\_size = 0.2,  
                                                    random\_state=0)  
X\_train\_lime.head(5)  
  The XGBoost optional parameters can be used to make the pipeline: model\_xgb = make\_pipeline(  
    preprocess,  
    xgboost.XGBClassifier(max\_depth = 3,  
                          gamma = 0.5,  
                           n\_estimators=600,  
                          objective='binary:logistic',  
                          silent=True,  
                          nthread=1))  
model\_xgb.fit(X\_train\_lime, y\_train\_lime) /Users/Thomas/anaconda3/envs/hello-tf/lib/python3.6/site-packages/sklearn/preprocessing/\_encoders.py:351: FutureWarning: The handling of integer data will change in version 0.22. Currently, the categories are determined based on the range \[0, max(values)\], while in the future, they will be determined based on the unique values. If you want the future behavior and silence this warning, you can specify "categories='auto'."In case you used a LabelEncoder before this OneHotEncoder to convert the categories to integers, then you can now use the OneHotEncoder directly. warnings.warn(msg, FutureWarning)  
Pipeline(memory=None,  
     steps=\[('columntransformer', ColumnTransformer(n\_jobs=1, remainder='drop', transformer\_weights=None,  
         transformers=\[('standardscaler', StandardScaler(copy=True, with\_mean=True, with\_std=True), \[0, 2, 10, 4, 11, 12\]), ('onehotencoder', OneHotEncoder(categorical\_features=None, categories=None,...  
       reg\_alpha=0, reg\_lambda=1, scale\_pos\_weight=1, seed=None,  
       silent=True, subsample=1))\])  
   You will see a warning telling you that the label encoder does not  need creating before the pipeline. If you are using LIME, stick with this method; otherwise, use the previous method. print("best logistic regression from grid search: %f" % model\_xgb.score(X\_test\_lime, y\_test\_lime))                      
best logistic regression from grid search: 0.873157                       model\_xgb.predict\_proba(X\_test\_lime)                   array(\[\[7.9646105e-01, 2.0353897e-01\],  
       \[9.5173013e-01, 4.8269872e-02\],  
       \[7.9344827e-01, 2.0655173e-01\],  
       ...,  
       \[9.9031430e-01, 9.6856682e-03\],  
       \[6.4581633e-04, 9.9935418e-01\],  
       \[9.7104281e-01, 2.8957171e-02\]\], dtype=float32)  
  Before we set LIME free to do its job, we need a NumPy array, containing the incorrect classification features. That list can be used later to see what put the classifier wrong: temp = pd.concat(\[X\_test\_lime, y\_test\_lime\], axis= 1)  
temp\['predicted'\] = model\_xgb.predict(X\_test\_lime)  
temp\['wrong'\]=  temp\['label'\] != temp\['predicted'\]  
temp = temp.query('wrong==True').drop('wrong', axis=1)  
temp= temp.sort\_values(by=\['label'\])  
temp.shape  
  (826, 16) A Lambda function is required to get the prediction: predict\_fn = lambda x:  model\_xgb.predict\_proba(x).astype(float)  
X\_test\_lime.dtypes  
  age               float64  
workclass           int64  
fnlwgt            float64  
education           int64  
education\_num     float64  
marital             int64  
occupation          int64  
relationship        int64  
race                int64  
sex                 int64  
capital\_gain      float64  
capital\_loss      float64  
hours\_week        float64  
native\_country      int64  
dtype: object  
  predict\_fn(X\_test\_lime)                    
array(\[\[7.96461046e-01, 2.03538969e-01\],  
       \[9.51730132e-01, 4.82698716e-02\],  
       \[7.93448269e-01, 2.06551731e-01\],  
       ...,  
       \[9.90314305e-01, 9.68566816e-03\],  
       \[6.45816326e-04, 9.99354184e-01\],  
       \[9.71042812e-01, 2.89571714e-02\]\])  
   The Pandas dataframe is converted to a NumPy array: X\_train\_lime = X\_train\_lime.values  
X\_test\_lime = X\_test\_lime.values  
 X\_test\_lime array(\[\[4.00000e+01, 5.00000e+00, 1.93524e+05, ..., 0.00000e+00,  
        4.00000e+01, 3.80000e+01\],  
       \[2.70000e+01, 4.00000e+00, 2.16481e+05, ..., 0.00000e+00,  
        4.00000e+01, 3.80000e+01\],  
       \[2.50000e+01, 4.00000e+00, 2.56263e+05, ..., 0.00000e+00,  
        4.00000e+01, 3.80000e+01\],  
       ...,  
       \[2.80000e+01, 6.00000e+00, 2.11032e+05, ..., 0.00000e+00,  
        4.00000e+01, 2.50000e+01\],  
       \[4.40000e+01, 4.00000e+00, 1.67005e+05, ..., 0.00000e+00,  
        6.00000e+01, 3.80000e+01\],  
       \[5.30000e+01, 4.00000e+00, 2.57940e+05, ..., 0.00000e+00,  
        4.00000e+01, 3.80000e+01\]\])  
model\_xgb.predict\_proba(X\_test\_lime)                       
array(\[\[7.9646105e-01, 2.0353897e-01\],  
       \[9.5173013e-01, 4.8269872e-02\],  
       \[7.9344827e-01, 2.0655173e-01\],  
       ...,  
       \[9.9031430e-01, 9.6856682e-03\],  
       \[6.4581633e-04, 9.9935418e-01\],  
       \[9.7104281e-01, 2.8957171e-02\]\], dtype=float32)  
print(features,  
      class\_names,  
       categorical\_features,  
      categorical\_names)  
\['age', 'workclass', 'fnlwgt', 'education', 'education\_num', 'marital', 'occupation', 'relationship', 'race', 'sex', 'capital\_gain', 'capital\_loss', 'hours\_week', 'native\_country'\] \['<=50K' '>50K'\] \[1, 3, 5, 6, 7, 8, 9, 13\] {'workclass': array(\['?', 'Federal-gov', 'Local-gov', 'Never-worked', 'Private',  
       'Self-emp-inc', 'Self-emp-not-inc', 'State-gov', 'Without-pay'\],  
      dtype=object), 'education': array(\['10th', '11th', '12th', '1st-4th', '5th-6th', '7th-8th', '9th',  
       'Assoc-acdm', 'Assoc-voc', 'Bachelors', 'Doctorate', 'HS-grad',  
       'Masters', 'Preschool', 'Prof-school', 'Some-college'\],  
      dtype=object), 'marital': array(\['Divorced', 'Married-AF-spouse', 'Married-civ-spouse',  
       'Married-spouse-absent', 'Never-married', 'Separated', 'Widowed'\],  
      dtype=object), 'occupation': array(\['?', 'Adm-clerical', 'Armed-Forces', 'Craft-repair',  
       'Exec-managerial', 'Farming-fishing', 'Handlers-cleaners',  
       'Machine-op-inspct', 'Other-service', 'Priv-house-serv',  
       'Prof-specialty', 'Protective-serv', 'Sales', 'Tech-support',  
       'Transport-moving'\], dtype=object), 'relationship': array(\['Husband', 'Not-in-family', 'Other-relative', 'Own-child',  
       'Unmarried', 'Wife'\], dtype=object), 'race': array(\['Amer-Indian-Eskimo', 'Asian-Pac-Islander', 'Black', 'Other',  
       'White'\], dtype=object), 'sex': array(\['Female', 'Male'\], dtype=object), 'native\_country': array(\['?', 'Cambodia', 'Canada', 'China', 'Columbia', 'Cuba',  
       'Dominican-Republic', 'Ecuador', 'El-Salvador', 'England',  
       'France', 'Germany', 'Greece', 'Guatemala', 'Haiti', 'Honduras',  
       'Hong', 'Hungary', 'India', 'Iran', 'Ireland', 'Italy', 'Jamaica',  
       'Japan', 'Laos', 'Mexico', 'Nicaragua',  
       'Outlying-US(Guam-USVI-etc)', 'Peru', 'Philippines', 'Poland',  
        'Portugal', 'Puerto-Rico', 'Scotland', 'South', 'Taiwan',  
       'Thailand', 'Trinidad & Tobago', 'United-States', 'Vietnam',  
       'Yugoslavia'\], dtype=object)}  
import lime  
import lime.lime\_tabular  
\### Train should be label encoded not one hot encoded  
explainer = lime.lime\_tabular.LimeTabularExplainer(X\_train\_lime ,  
                                                   feature\_names = features,  
                                                   class\_names=class\_names,  
                                                   categorical\_features=categorical\_features,  
                                                   categorical\_names=categorical\_names,  
                                                   kernel\_width=3)  
   We’ll pick a household randomly from the test set and have a look at the prediction, and how the computer arrived at it: import numpy as np  
np.random.seed(1)  
i = 100  
print(y\_test\_lime.iloc\[i\])  
\>50K  
  X\_test\_lime\[i\]                     
  array(\[4.20000e+01, 4.00000e+00, 1.76286e+05, 7.00000e+00, 1.20000e+01,  
       2.00000e+00, 4.00000e+00, 0.00000e+00, 4.00000e+00, 1.00000e+00,  
       0.00000e+00, 0.00000e+00, 4.00000e+01, 3.80000e+01\])  
  You can see the model explanation using explainer\_instance: exp = explainer.explain\_instance(X\_test\_lime\[i\], predict\_fn, num\_features=6)  
exp.show\_in\_notebook(show\_all=False)  
  The classifier was correct in its prediction. What we can say is that the classifier is not entirely certain about the predictions. The prediction about the household income has a 64% probability, made up of Marital and Capital Gain. The confusion arises here because the household Capital Gain is Null – this tends to be an excellent wealth predictor. Plus, less than 40 hours per week are worked across the household – however, positive contributions are sex, occupation, and age. In the next chapter, we move onto Linear Regression. 

Chapter 10 Linear Regression ![](image_rsrc9SG.jpg)In this chapter, we are going to look at the principles behind machine learning and linear regression. TensorFlow gives you everything you need to control your computations, using low-level APIs. The library also offers you many more high-level APIs for performing other algorithms, known as estimators: 

*   Low-Level – these APIs help you build and optimize models – not easy for beginners 
*   High-Level – these APIs are user-friendly. With an estimator, you can build, train, and evaluate your model before getting predictions. 

We are going to concentrate on estimators – they offer fast computations and are user-friendly. First, we look at training a linear regression model using gradient descent, and then we use the Boston dataset to make housing price predictions. Training a Linear Regression Model Before we start, we need to understand what linear regression is. Let’s say that we have a pair of variables, named x and y. You want a prediction of what the value is of knowing the value of something else. When the data is plotted, there is a clear relationship between x (independent) and y (dependent.) ![](image_rsrc9SN.jpg)If x=1, then y is approximately 6; if x=2, y is approximately 8.5. This is an inaccurate, error-prone way of doing this, especially when your dataset contains thousands of points. Equations are used to evaluate linear regression. One or more covariates are used to explain the y variable. We only have a single dependent variable, and the equation looks like: ![](image_rsrc9SP.jpg)This means: 

*   ![](image_rsrc9SR.jpg)\- the bias. i.e. if x=0, y=![](image_rsrc9SR.jpg)
*   ![](image_rsrc9SS.jpg)\- the weight associated with x 
*   ![](image_rsrc9ST.jpg)\- the mode residual/error, including what can’t be learned by the model 

Let’s say that the model is fit and we get a solution for: 

*   ![](image_rsrc9SR.jpg)\= 3.8 
*   ![](image_rsrc9SS.jpg)\= 2.78 

The equation numbers can be substituted, becoming: y= 3.8 + 2.78x That is a better way of finding y’s values. X can be replaced with the value for predicting y. The image below shows x replaced with all the dataset values: ![](image_rsrc9SU.jpg)The red line is the fitted value (y values for each x value.) Predicting y does not require that you see every x value. You can extend this to include more covariates, simply by adding extra variables. The difference between linear regression and traditional analysis model is that the former examines the way y reacts for each independent variable x. We can see this better with an example. Let’s assume you are predicting an ice cream shop’s sales. In the dataset, we have data on  weather and customer data. With traditional analysis, we try to make the prediction by computing each variable’s average and estimating sales for multiple scenarios. This is restrictive and provides poor results. Using linear regression, we could use this equation: ![](image_rsrc9SV.jpg)The algorithm above searches for the best solution for each weight, minimizing the cost – the difference between the data points and the fitted line. How Does The Algorithm Work? It picks a number a random for β and α, replacing x’s value to get a prediction for y. If there are 100 observations in the dataset, there will be 100 predicted values. The error, Є, can be computed – this is the difference between the real and predicted values. If the error is positive, the y prediction has been underestimated; a negative error indicates an overestimation: ![](image_rsrc9SW.jpg)Your aim? To minimize the error’s square. The algorithm will compute the mean in a step known as error minimization. In linear regression, this is known as MSE (Mean Squared Error): ![](image_rsrc9SX.jpg)In this: 

*   ![](image_rsrc9SY.jpg)is – weights. ![](image_rsrc9SZ.jpg)references the predicted value 
*   y - the real values 
*   m – how many observations there are 

![](image_rsrc9T0.jpg)indicates the matrices transpose is used, and the mean mathematical notation is ![](image_rsrc9T1.jpg). Your goal is to minimize MSE with the best ϴ. If you have a large average error, the model is not performing very well, with poorly chosen weights. An optimizer is required for correcting the weights, and the best-known one is gradient descent. This optimizer increases or decreases the weight – where you have a positive derivative, there is a decrease in weight, while a negative causes an increase.  The weights are updated, and the model computes the error again. This is repeated until the error stays the same. A learning rate is used to multiply the gradients, indicating the learning speed. If the rate is small, the algorithm takes many iterations to converge while, if it is too high, there is a chance it might not converge. Using TensorFlow to Train Linear Regression Now you have seen what’s going on, we can get on with training a linear regression model using TensorFlow’s estimator API. The Boston dataset that we are going to use has these variables: 

| crim  || per capita crime rate by town  |
| --- | --- |
| zn  || Residential land plots zoned for 25,000 sq. Ft+.  |
| indus  || Non-retail acres for business in each town.  |
| nox  || The concentration of nitric oxide.  |
| rm  || Rooms/dwelling - average  |
| age  || Owner-occupied built prior to 1940  |
| dis  || Weighted distances for five employment centers in Boston  |
| tax  || Full-value of the property tax rates per $10,000  |
| ptratio  || The ratio of pupils to teachers per town  |
| medv  || Median value of owner-occupied homes in $1,000  |

We are going to create three separate datasets: 

| dataset  || objective  || shape  |
| --- | --- | --- |
| Training  || For training the model and getting the weights  || 400, 10  |
| Evaluation  || For evaluating the model performance on unseen data  || 100, 10  |
| Predict  || Predicting house values using new data  || 6, 10  |

We will look at three ways TensorFlow can be used to import data: 

*   Pandas 
*   NumPy 
*   TensorFlow only 

You will get the same result with each one. Using Pandas First, the libraries must be imported: import pandas as pd  
from sklearn import datasets  
import tensorflow as tf  
import itertools                          
  Step One – Importing the Data The column names are defined  and stored in COLUMNS. The data is  imported using pd.read\_csv(): COLUMNS = \["crim", "zn", "indus", "nox", "rm", "age",  
           "dis", "tax", "ptratio", "medv"\]  
  training\_set = pd.read\_csv("E:/boston\_train.csv", skipinitialspace=True,skiprows=1, names=COLUMNS) test\_set = pd.read\_csv("E:/boston\_test.csv", skipinitialspace=True,skiprows=1, names=COLUMNS) prediction\_set = pd.read\_csv("E:/boston\_predict.csv", skipinitialspace=True,skiprows=1, names=COLUMNS) The data shape can be printed: print(training\_set.shape, test\_set.shape, prediction\_set.shape)      Output (400, 10) (100, 10) (6, 10) The label (y) is in the dataset so we need two more lists defined. One will have the features, one will have the label name. These will inform the estimator what the features and the label name are: FEATURES = \["crim", "zn", "indus", "nox", "rm",                            
                 "age", "dis", "tax", "ptratio"\]  
LABEL = "medv"                    
  Step Two – Converting the Data The numerical variables must be converted to the right format, using tf.feature\_column.numeric\_column() Earlier, we defined a list of features we wanted in our model. We can now use this to convert the variables We are going to use Python list comprehension, using the list called FEATURES, to come up with  another list called feature\_cols. This will cut down on the amount of code you need to write. feature\_cols = \[tf.feature\_column.numeric\_column(k) for k in FEATURES\]         Step Three – Defining the Estimator Now we can define our estimator. In TensorFlow, there are six built-in estimators, three each for regression and classification: Regression: 

*   DNNRegressor 
*   LinearRegessor 
*   DNNLinearRegressor 

Classification: 

*   DNNClassifier 
*   LinearClassifier 
*   DNNLinearClassifier 

We will use LinearRegressor, accessing it using tf.estimator. Two arguments are required by the function: 

*   feature\_columns: has the variable to be included in the model 
*   model\_dir: the path where the graph is stored and the model parameters are saved, etc. 

TensorFlow automatically creates a file in the working directory, naming it ‘train’ – this is the file path you need for accessing TensorBoard. estimator = tf.estimator.LinearRegressor(      
        feature\_columns=feature\_cols,     
        model\_dir="train")                      Output INFO:tensorflow:Using default config.  
INFO:tensorflow:Using config: {'\_model\_dir': 'train', '\_tf\_random\_seed': None, '\_save\_summary\_steps': 100, '\_save\_checkpoints\_steps': None, '\_save\_checkpoints\_secs': 600, '\_session\_config': None, '\_keep\_checkpoint\_max': 5, '\_keep\_checkpoint\_every\_n\_hours': 10000, '\_log\_step\_count\_steps': 100, '\_train\_distribute': None, '\_service': None, '\_cluster\_spec': <tensorflow.python.training.server\_lib.ClusterSpec object at 0x1a215dc550>, '\_task\_type': 'worker', '\_task\_id': 0, '\_global\_id\_in\_cluster': 0, '\_master': '', '\_evaluation\_master': '', '\_is\_chief': True, '\_num\_ps\_replicas': 0, '\_num\_worker\_replicas': 1}  
  The hardest part is how the model is fed. The TensorFlow design is such that it works with large datasets and parallel computing. Limitations in computing resources dictate that the model must be fed the data in batches – more so when you are using millions of records; not using batches will result in memory errors. When all the data has been fed to the model, one epoch is complete. An epoch is a definition of the number of times the model sees the data. The best option is to set this as None. You could also add an instruction to shuffle the data ahead of each iteration. This is important as it stops the model learning a specific pattern. This could lead to predictions being generalized on unseen data, a process known as overfitting. While the model gives good  performance on training data, the unseen data predictions will be incorrect. These two steps are easily done with TensorFlow. When the data enters the pipeline, it will already know the number of observations needed and whether the data needs to be shuffled. We use pandas\_input\_fn to do this, giving the object the following five parameters: 

*   x: feature data 
*   y: label data 
*   batch\_size: batch size - 128, by default 
*   num\_epoch: epoch number – 1 by default 
*   shuffle: whether the data should be shuffled or not – none, by default. 

The model needs to be fed multiple times, so a function must be defined to ensure the process is repeated – get\_input\_fn: def get\_input\_fn(data\_set, num\_epochs=None, n\_batch = 128, shuffle=True):      
         return tf.estimator.inputs.pandas\_input\_fn(         
         x=pd.DataFrame({k: data\_set\[k\].values for k in FEATURES}),         
         y = pd.Series(data\_set\[LABEL\].values),         
         batch\_size=n\_batch,            
         num\_epochs=num\_epochs,         
         shuffle=shuffle)                       Typically, we evaluate a model’s performance with three steps: 

*   Train 
*   Evaluate 
*   Predict 

With the TensorFlow estimator, we get three functions for carrying these steps out. Step Four – Training the Model The estimator called ‘train’ may be used for model evaluation. This requires input\_fn, along with a few steps. Feed the model using your previously created function and then tell the model you want 1,000 iterations. There is no need to specify how many epochs you want.  If, for example, you were to set epochs to 1, you would get four iterations – the training set has 400 records and a batch size of 128. 

*   128 rows 
*   128 rows 
*   128 rows 
*   16 rows 

As such, setting the epoch to None and defining the iterations is best: estimator.train(input\_fn=get\_input\_fn(training\_set,    
                                           num\_epochs=None,    
                                           n\_batch = 128,      
                                           shuffle=False),    
                                           steps=1000)           Output INFO:tensorflow:Calling model\_fn.  
INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Create CheckpointSaverHook.  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Saving checkpoints for 1 into train/model.ckpt.  
 INFO:tensorflow:loss = 83729.64, step = 1  
INFO:tensorflow:global\_step/sec: 238.616  
INFO:tensorflow:loss = 13909.657, step = 101 (0.420 sec)  
INFO:tensorflow:global\_step/sec: 314.293  
INFO:tensorflow:loss = 12881.449, step = 201 (0.320 sec)  
INFO:tensorflow:global\_step/sec: 303.863  
INFO:tensorflow:loss = 12391.541, step = 301 (0.327 sec)  
INFO:tensorflow:global\_step/sec: 308.782  
INFO:tensorflow:loss = 12050.5625, step = 401 (0.326 sec)  
INFO:tensorflow:global\_step/sec: 244.969  
INFO:tensorflow:loss = 11766.134, step = 501 (0.407 sec)  
INFO:tensorflow:global\_step/sec: 155.966  
INFO:tensorflow:loss = 11509.922, step = 601 (0.641 sec)  
INFO:tensorflow:global\_step/sec: 263.256  
INFO:tensorflow:loss = 11272.889, step = 701 (0.379 sec)  
INFO:tensorflow:global\_step/sec: 254.112  
INFO:tensorflow:loss = 11051.9795, step = 801 (0.396 sec)  
INFO:tensorflow:global\_step/sec: 292.405  
INFO:tensorflow:loss = 10845.855, step = 901 (0.341 sec)  
INFO:tensorflow:Saving checkpoints for 1000 into train/model.ckpt.  
INFO:tensorflow:Loss for final step: 5925.9873. Use the command below to look at the TensorBoard: activate hello-tf  
\# For MacOS  
tensorboard --logdir=./train  
\# For Windows  
tensorboard --logdir=train    Step Five – Evaluating the Model The model fit can be evaluated on the test dataset, using the following code: ev = estimator.evaluate(      
          input\_fn=get\_input\_fn(test\_set,                            
          num\_epochs=1,                            
          n\_batch = 128,                            
          shuffle=False))                  Output INFO:tensorflow:Calling model\_fn.  
INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Starting evaluation at 2018-05-13-01:43:13  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Restoring parameters from train/model.ckpt-1000  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Finished evaluation at 2018-05-13-01:43:13  
INFO:tensorflow:Saving dict for global step 1000: average\_loss = 32.15896, global\_step = 1000, loss = 3215.896 The loss is printed using the following code: loss\_score = ev\["loss"\]  
print("Loss: {0:f}".format(loss\_score))                 Output Loss: 3215.895996 We can see a loss of 3215; to see how big this error is, look at the summary statistics: training\_set\['medv'\].describe() Output count    400.000000  
mean      22.625500  
std        9.572593  
min        5.000000  
25%       16.600000  
50%       21.400000  
75%       25.025000  
max       50.000000  
Name: medv, dtype: float64                      From this, you can see that the average house price is $22,000. We have a minimum of $9,000 and a maximum of $50,000. The typical error made was $3,000. Step Six – Making the Prediction At last, the ‘predict’ estimator can be used for estimating the value of six houses in Boston: y = estimator.predict(      
         input\_fn=get\_input\_fn(prediction\_set,                            
         num\_epochs=1,                            
         n\_batch = 128,                            
         shuffle=False))           The following code will let you print those values:             predictions = list(p\["predictions"\] for p in itertools.islice(y, 6))print("Predictions: {}".format(str(predictions)))           Output INFO:tensorflow:Calling model\_fn.  
INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Restoring parameters from train/model.ckpt-1000  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
Predictions: \[array(\[32.297546\], dtype=float32), array(\[18.96125\], dtype=float32), array(\[27.270979\], dtype=float32), array(\[29.299236\], dtype=float32), array(\[16.436684\], dtype=float32), array(\[21.460876\], dtype=float32)\] Using NumPy Now, we can use a NumPy estimator to train our model. This is exactly the same as Pandas, with the exception of using the numpy\_input\_fn estimator: training\_set\_n = pd.read\_csv("E:/boston\_train.csv").values test\_set\_n = pd.read\_csv("E:/boston\_test.csv").values prediction\_set\_n = pd.read\_csv("E:/boston\_predict.csv").values Step One – Importing the Data First, we need the feature variables differentiated from the label and this has to be done for training data and for evaluations. The easiest way is to split our data by defining a function: def prepare\_data(df):       
        X\_train = df\[:, :-3\]      
        y\_train = df\[:,-3\]      
        return X\_train, y\_train                   
  This function will help split the features and the label in the training and evaluation dataset: X\_train, y\_train = prepare\_data(training\_set\_n)  
X\_test, y\_test = prepare\_data(test\_set\_n)       You should leave out the final column in the prediction dataset as it only has NaN: x\_predict = prediction\_set\_n\[:, :-2\]                     Next, the array shape can be confirmed – there should be no dimension for the label: print(X\_train.shape, y\_train.shape, x\_predict.shape)            Output (400, 9) (400,) (6, 9)                   The feature columns can be constructed like this: feature\_columns = \[      tf.feature\_column.numeric\_column('x', shape=X\_train.shape\[1:\])\]      Define the estimator as you did before, instructing the feature columns and indicating where the graph is saved:           estimator = tf.estimator.LinearRegressor(      
         feature\_columns=feature\_columns,      
         model\_dir="train1")        Output INFO:tensorflow:Using default config.  
INFO:tensorflow:Using config: {'\_model\_dir': 'train1', '\_tf\_random\_seed': None, '\_save\_summary\_steps': 100, '\_save\_checkpoints\_steps': None, '\_save\_checkpoints\_secs':  600, '\_session\_config': None, '\_keep\_checkpoint\_max': 5, '\_keep\_checkpoint\_every\_n\_hours': 10000, '\_log\_step\_count\_steps': 100, '\_train\_distribute': None, '\_service': None, '\_cluster\_spec': <tensorflow.python.training.server\_lib.ClusterSpec object at 0x1a218d8f28>, '\_task\_type': 'worker', '\_task\_id': 0, '\_global\_id\_in\_cluster': 0, '\_master': '', '\_evaluation\_master': '', '\_is\_chief': True, '\_num\_ps\_replicas': 0, '\_num\_worker\_replicas': 1}        The NumPy estimator feeds the model with the data and trains it. \# Train the estimatortrain\_input = tf.estimator.inputs.numpy\_input\_fn(     
           x={"x": X\_train},      
           y=y\_train,      
           batch\_size=128,      
           shuffle=False,      
           num\_epochs=None)  
           estimator.train(input\_fn = train\_input,steps=5000)       Output INFO:tensorflow:Calling model\_fn.  
INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Create CheckpointSaverHook.  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Saving checkpoints for 1 into train1/model.ckpt.  
INFO:tensorflow:loss = 83729.64, step = 1  
INFO:tensorflow:global\_step/sec: 490.057  
INFO:tensorflow:loss = 13909.656, step = 101 (0.206 sec)  
INFO:tensorflow:global\_step/sec: 788.986  
 INFO:tensorflow:loss = 12881.45, step = 201 (0.126 sec)  
INFO:tensorflow:global\_step/sec: 736.339  
INFO:tensorflow:loss = 12391.541, step = 301 (0.136 sec)  
INFO:tensorflow:global\_step/sec: 383.305  
INFO:tensorflow:loss = 12050.561, step = 401 (0.260 sec)  
INFO:tensorflow:global\_step/sec: 859.832  
INFO:tensorflow:loss = 11766.133, step = 501 (0.117 sec)  
INFO:tensorflow:global\_step/sec: 804.394  
INFO:tensorflow:loss = 11509.918, step = 601 (0.125 sec)  
INFO:tensorflow:global\_step/sec: 753.059  
INFO:tensorflow:loss = 11272.891, step = 701 (0.134 sec)  
INFO:tensorflow:global\_step/sec: 402.165  
INFO:tensorflow:loss = 11051.979, step = 801 (0.248 sec)  
INFO:tensorflow:global\_step/sec: 344.022  
INFO:tensorflow:loss = 10845.854, step = 901 (0.288 sec)  
INFO:tensorflow:Saving checkpoints for 1000 into train1/model.ckpt.  
INFO:tensorflow:Loss for final step: 5925.985.  
Out\[23\]:  
<tensorflow.python.estimator.canned.linear.LinearRegressor at 0x1a1b6ea860> Use another estimator to replicate the step for evaluation: eval\_input = tf.estimator.inputs.numpy\_input\_fn(      
       x={"x": X\_test},      
       y=y\_test,  
       shuffle=False,      
       batch\_size=128,      
       num\_epochs=1)  
   estimator.evaluate(eval\_input,steps=None)         Output INFO:tensorflow:Calling model\_fn.  
 INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Starting evaluation at 2018-05-13-01:44:00  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Restoring parameters from train1/model.ckpt-1000  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Finished evaluation at 2018-05-13-01:44:00  
INFO:tensorflow:Saving dict for global step 1000: average\_loss = 32.158947, global\_step = 1000, loss = 3215.8945  
Out\[24\]:  
{'average\_loss': 32.158947, 'global\_step': 1000, 'loss': 3215.8945} Lastly, the prediction can be computed – this will be much the same as Pandas: test\_input = tf.estimator.inputs.numpy\_input\_fn(      
        x={"x": x\_predict},      
        batch\_size=128,      
        num\_epochs=1,     
        shuffle=False)  
        y = estimator.predict(test\_input)                         
predictions = list(p\["predictions"\] for p in itertools.islice(y, 6))  
print("Predictions: {}".format(str(predictions)))                       Output INFO:tensorflow:Calling model\_fn.  
INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Restoring parameters from train1/model.ckpt-1000  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
 Predictions: \[array(\[32.297546\], dtype=float32), array(\[18.961248\], dtype=float32), array(\[27.270979\], dtype=float32), array(\[29.299242\], dtype=float32), array(\[16.43668\], dtype=float32), array(\[21.460878\], dtype=float32)\] Using TensorFlow Only This is a little more complicated but TensorFlow contains a useful tool for passing the data to a pipeline. With this method, you will be building the input\_fn function by yourself. Note – if you are using Jupyter Notebook, Restart, and then clean the kernel before starting this new session. Step One – Defining the Path and Data Format First, we need a pair of variables declared with the CSV file path. You will have two files – training and testing: import tensorflow as tf df\_train = "E:/boston\_train.csv" df\_eval = "E:/boston\_test.csv" Next, the columns you want from the csv file must be defined. We are going to use them all – that is followed by the variable declaration. \[0.0\] indicates float variable definitions: COLUMNS = \["crim", "zn", "indus", "nox", "rm", "age",    
                "dis", "tax", "ptratio", "medv"\]RECORDS\_ALL = \[\[0.0\], \[0.0\], \[0.0\], \[0.0\],\[0.0\],\[0.0\],\[0.0\],\[0.0\],\[0.0\],\[0.0\]\] Step Two – Defining the Function – input\_fn We can break the function into three: 

*   Data import 
*   Iterator creation 
*   Data consumption 

The following code shows the function definition: def input\_fn(data\_file, batch\_size, num\_epoch = None):  
       # Step 1                           
          def parse\_csv(value):          
          columns = tf.decode\_csv(value, record\_defaults= RECORDS\_ALL)          
          features = dict(zip(COLUMNS, columns))    
          #labels = features.pop('median\_house\_value')          
          labels =  features.pop('medv')          
          return features, labels            
           \# Extract the lines from the input files using the  
          Dataset API.    dataset = (tf.data.TextLineDataset(data\_file) # Read text file         
          .skip(1) # Skip header row         
          .map(parse\_csv))                           
           dataset = dataset.repeat(num\_epoch)      
          dataset = dataset.batch(batch\_size)        
          # Step 3      
          iterator = dataset.make\_one\_shot\_iterator()      
          features, labels = iterator.get\_next()      
          return features, labels                         
   \*\* Import the data\*\* In CSV files, the lines are read one at a time by the dataset method. The object called TextLineDataset is used to build the dataset. Because there is a header in the dataset, the first line is skipped,  using skip(1) – the data is read into the pipeline, excluding the header. The features and the label must be separated for the model to be fed, and we use the map() method to apply data transformation. 

*   tf.data.TextLineDataset(data\_file) reads the CSV file. 
*   The header is skipped using .skip(1) 
*   The records are parsed into the tensors using .map(parse\_csv). A function, named parse\_csv, must be defined for instructing the map object. 

The CSV file is parsed using tf.decode\_csv, and the label and features declared as either a tuple or a dictionary. The dictionary method is far more convenient: 

*   The decode\_sv method read the CSV file using the TextLineDataset output, while record\_defaults tells TensorFlow what type the columns are. 
*   The dictionary is populated with the columns that were extracted, using dict(xip(\_CSV\_COLUMNS, columns)). 
*   The target variable is excluded from the feature variable, and a label variable is created using features.pop(‘median\_house\_value’). 

For the tensors to be iteratively fed, we need to add more elements into the dataset. The method repeat must be added so the model can continue feeding the model indefinitely; if you omit this, you only get one model iteration, followed by an error because the pipeline has not received any more data. Once that is done, the batch method can be used to control the size of the batch – simply, you are instructing the dataset on the number of data the pipeline needs for every iteration. The larger the batch size, the slower the model. Step Three – Creating the Iterator The easiest way to create the operator is to use the make\_one\_shot\_iterator method, and then the iterator can be used to create the labels and features. Step Four – Consuming the Data The input\_fn function can be used to see what happens. The function must be called within a session for the data to be consumed – we start with a batch size equal to 1. The dictionary features will be printed, along with the label (in array form). The first line from the CSV file is shown. Try this using different sizes for the batch: next\_batch = input\_fn(df\_train, batch\_size = 1, num\_epoch = None)  
with tf.Session() as sess:      
     first\_batch  = sess.run(next\_batch)      
     print(first\_batch)               Output ({'crim': array(\[2.3004\], dtype=float32), 'zn': array(\[0.\], dtype=float32), 'indus': array(\[19.58\], dtype=float32), 'nox': array(\[0.605\], dtype=float32), 'rm': array(\[6.319\], dtype=float32), 'age': array(\[96.1\], dtype=float32), 'dis': array(\[2.1\], dtype=float32), 'tax': array(\[403.\], dtype=float32), 'ptratio': array(\[14.7\], dtype=float32)}, array(\[23.8\], dtype=float32)) Step Four – Defining Feature Columns The numeric columns need to be defined like this: X1= tf.feature\_column.numeric\_column('crim')  
X2= tf.feature\_column.numeric\_column('zn')  
X3= tf.feature\_column.numeric\_column('indus')  
X4= tf.feature\_column.numeric\_column('nox')  
X5= tf.feature\_column.numeric\_column('rm')  
X6= tf.feature\_column.numeric\_column('age')  
X7= tf.feature\_column.numeric\_column('dis')  
X8= tf.feature\_column.numeric\_column('tax')  
X9= tf.feature\_column.numeric\_column('ptratio')     Be aware that all the variables must be confined in a bucket       base\_columns = \[X1, X2, X3,X4, X5, X6,X7, X8, X9\]         Step Five – Training the Model We can use the LinearRegressor estimator to train our model:  
model = tf.estimator.LinearRegressor(feature\_columns=base\_columns, model\_dir='train3')         Output INFO:tensorflow:Using default config. INFO:tensorflow:Using config: {'\_model\_dir': 'train3', '\_tf\_random\_seed': None, '\_save\_summary\_steps': 100, '\_save\_checkpoints\_steps': None, '\_save\_checkpoints\_secs': 600, '\_session\_config': None, '\_keep\_checkpoint\_max': 5, '\_keep\_checkpoint\_every\_n\_hours': 10000, '\_log\_step\_count\_steps': 100, '\_train\_distribute': None, '\_service': None, '\_cluster\_spec': <tensorflow.python.training.server\_lib.ClusterSpec object at  0x1820a010f0>, '\_task\_type': 'worker', '\_task\_id': 0, '\_global\_id\_in\_cluster': 0, '\_master': '', '\_evaluation\_master': '', '\_is\_chief': True, '\_num\_ps\_replicas': 0, '\_num\_worker\_replicas': 1} A Lambda function is required to include the argument in the input\_fn function – omit this and the model cannot be trained: \# Train the estimatormodel.train(steps =1000,      
          input\_fn= lambda : input\_fn(df\_train,batch\_size=128, num\_epoch = None)) Output INFO:tensorflow:Calling model\_fn.  
INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Create CheckpointSaverHook.  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Saving checkpoints for 1 into train3/model.ckpt.  
INFO:tensorflow:loss = 83729.64, step = 1  
INFO:tensorflow:global\_step/sec: 72.5646  
INFO:tensorflow:loss = 13909.657, step = 101 (1.380 sec)  
INFO:tensorflow:global\_step/sec: 101.355  
INFO:tensorflow:loss = 12881.449, step = 201 (0.986 sec)  
INFO:tensorflow:global\_step/sec: 109.293  
INFO:tensorflow:loss = 12391.541, step = 301 (0.915 sec)  
INFO:tensorflow:global\_step/sec: 102.235  
INFO:tensorflow:loss = 12050.5625, step = 401 (0.978 sec)  
INFO:tensorflow:global\_step/sec: 104.656  
INFO:tensorflow:loss = 11766.134, step = 501 (0.956 sec)  
INFO:tensorflow:global\_step/sec: 106.697  
INFO:tensorflow:loss = 11509.922, step = 601 (0.938 sec)  
 INFO:tensorflow:global\_step/sec: 118.454  
INFO:tensorflow:loss = 11272.889, step = 701 (0.844 sec)  
INFO:tensorflow:global\_step/sec: 114.947  
INFO:tensorflow:loss = 11051.9795, step = 801 (0.870 sec)  
INFO:tensorflow:global\_step/sec: 111.484  
INFO:tensorflow:loss = 10845.855, step = 901 (0.897 sec)  
INFO:tensorflow:Saving checkpoints for 1000 into train3/model.ckpt.  
INFO:tensorflow:Loss for final step: 5925.9873.  
Out\[8\]:  
<tensorflow.python.estimator.canned.linear.LinearRegressor at 0x18225eb8d0> The model fit can be evaluated using the following code on the test set: results = model.evaluate(steps =None,input\_fn=lambda: input\_fn(df\_eval, batch\_size =128, num\_epoch = 1))  
for key in results:     
print("   {}, was: {}".format(key, results\[key\]))              Output INFO:tensorflow:Calling model\_fn.  
INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Starting evaluation at 2018-05-13-02:06:02  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Restoring parameters from train3/model.ckpt-1000  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Finished evaluation at 2018-05-13-02:06:02  
INFO:tensorflow:Saving dict for global step 1000: average\_loss = 32.15896, global\_step = 1000, loss = 3215.896  
   average\_loss was: 32.158958435058594  
   loss was: 3215.89599609375  
   global\_step was: 1000 Step Six – Predicting the Value As last, we can predict the value – this is based on the feature matrices values. A dictionary can be written to include the values you want to predict. Our model has nine features, so we need nine values, and you will get a prediction from the model for each of them. In the next code, the feature values from df\_predict are written. A new input\_fn function must be written because the dataset has no label. The from\_tensor API can be used: prediction\_input = {                               
          'crim': \[0.03359,5.09017,0.12650,0.05515,8.15174,0.24522\],    
          'zn': \[75.0,0.0,25.0,33.0,0.0,0.0\],    
          'indus': \[2.95,18.10,5.13,2.18,18.10,9.90\],      
          'nox': \[0.428,0.713,0.453,0.472,0.700,0.544\],    
          'rm': \[7.024,6.297,6.762,7.236,5.390,5.782\],    
          'age': \[15.8,91.8,43.4,41.1,98.9,71.7\],      
          'dis': \[5.4011,2.3682,7.9809,4.0220,1.7281,4.0317\],      
          'tax': \[252,666,284,222,666,304\],    
          'ptratio': \[18.3,20.2,19.7,18.4,20.2,18.4\]  
     }  
     def test\_input\_fn():      
     dataset = tf.data.Dataset.from\_tensors(prediction\_input)      
     return dataset  
      \# Predict all our prediction\_inputpred\_results = model.predict(input\_fn=test\_input\_fn)         Lastly, the predictions are printed: for pred in enumerate(pred\_results):      
print(pred)               Output INFO:tensorflow:Calling model\_fn.  
INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Restoring parameters from train3/model.ckpt-1000  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
(0, {'predictions': array(\[32.297546\], dtype=float32)})  
(1, {'predictions': array(\[18.96125\], dtype=float32)})  
(2, {'predictions': array(\[27.270979\], dtype=float32)})  
(3, {'predictions': array(\[29.299236\], dtype=float32)})  
(4, {'predictions': array(\[16.436684\], dtype=float32)})  
(5, {'predictions': array(\[21.460876\], dtype=float32)})  
INFO:tensorflow:Calling model\_fn. INFO:tensorflow:Done calling model\_fn. INFO:tensorflow:Graph was finalized. INFO:tensorflow:Restoring parameters from train3/model.ckpt-5000 INFO:tensorflow:Running local\_init\_op. INFO:tensorflow:Done running local\_init\_op. (0, {'predictions': array(\[35.60663\], dtype=float32)}) (1, {'predictions': array(\[22.298521\], dtype=float32)}) (2, {'predictions': array(\[25.74533\], dtype=float32)}) (3, {'predictions': array(\[35.126694\], dtype=float32)}) (4, {'predictions': array(\[17.94416\], dtype=float32)}) (5, {'predictions': array(\[22.606628\], dtype=float32)}) That gave you an idea of how TensorFlow and linear regression work; in the next chapter, we will look deeper into this, using a case study to understand linear regression better. 

Chapter 11 Linear Regression - A Case Study ![](image_rsrc9SG.jpg)Continuing our study on linear regression, in this chapter, we will look at checking and preparing data for linear regression. In the first part, you will learn about looking for interaction, and, in the second part, you will learn how to test your model. In chapter 10, we used the Boston dataset, building a model to estimate median house prices. This dataset has just 506 observations and is the best place for training new algorithms for linear regression. Refer to the previous chapter for the variables in the dataset. We are going to use a linear regressor to estimate median prices but will focus on data preparation, just one part of the machine learning process. Models generalize pattern data, and to capture these patterns, you must first find them. The best practice is to analyze the data before you run the algorithm. To get the best out of your model, you need to pick the right features. Let’s say you are estimating wages; if you omit the covariate of gender, the results will be poor. You could improve the model by examining the independent variable correlation. Going back to our wages, one of the best ways to predict both wages and occupation is to use education. Obviously, occupation is related to education – the higher the level, the better the occupation. Generalizing this would tell us that the correlation between explanatory and dependent variables may be magnified using another variable – an explanatory one. An interaction term is required to see the limited effect education has on the occupation. The wage equation would be: ![](image_rsrc9T2.jpg)If ![](image_rsrc9T3.jpg)were positive, the implication would be that, the higher the education level, the higher the median house value increase for higher levels of occupation is. Simply put, education and occupation have an interaction effect. What we want to do here is to find the best variables for interaction terms, and we will be testing to see if this information would give us a better prediction for the house prices. Summary Statistics Before you get to the model, there are a couple of things you should do. As you know, the model generalizes the data, and the best way to proceed is to make sure you understand the data before you make the prediction. Step One – Loading the Data The data needs to be loaded as a Pandas DataFrame, followed by training and testing datasets being created. You will need to have Seaborn and Matplotlib installed, and these can easily be installed: import sys  
!{sys.executable} -m pip install matplotlib # Already installed  
!{sys.executable} -m pip install seaborn  
  You only need to do this if the packages are not installed already. Matplotlib is a Python library for creating graphs, while Seaborn provides statistical visualizations and is built on Matplotlib. Import the libraries like this: import pandas as pd  
from sklearn import datasets  
import tensorflow as tf  
from sklearn.datasets import load\_boston  
import numpy as np The Boston dataset is in the Sklearn library, and you import the data by calling the API: boston = load\_boston()  
df = pd.DataFrame(boston.data)            An array, stored in the features\_names object, is where you store the feature names: boston.feature\_names Output array(\['CRIM', 'ZN', 'INDUS', 'CHAS', 'NOX', 'RM', 'AGE', 'DIS', 'RAD','TAX', 'PTRATIO', 'B', 'LSTAT'\], dtype='<U7')                  The columns can be renamed: df.columns = boston.feature\_names  
df\['PRICE'\] = boston.target  
df.head(2) The variable called CHAS is converted to a string variable and labeled – if CHAS=1, the label is yes and, if CHAS=0 the label is no. df\['CHAS'\] = df\['CHAS'\].map({1:'yes', 0:'no'})  
df\['CHAS'\].head(5)  
0    no  
1    no  
2    no  
3    no  
4    no  
 Name: CHAS, dtype: object Pandas makes it easy to split a dataset; the dataset is randomly divided 80/20 – 80% training and 20% test. Pandas provides a function to do this. The first parameter, called frac, has a value of 0 to 1. We will set it as 0.8 to split 80% of the dataset for training. To make sure everyone returns the same DataFrame, we use random\_state: \### Create train/test set  
df\_train=df.sample(frac=0.8,random\_state=200)  
df\_test=df.drop(df\_train.index) The data shape should be: 

*   Train set: 506\*0.8 = 405 
*   Test set: 506\*0.2 = 101 

And we can get it like this: print(df\_train.shape, df\_test.shape) Output (405, 14) (101, 14)        df\_test.head(5) Output 

|  || CRIM  || ZN  || INDUS  || CHAS  || NOX  || RM  || AGE  || DIS  || RAD  || TAX  || PTRATIO  || B  || LSTAT  || PRICE  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 0  || 0.00632  || 18.0  || 2.31  || no  || 0.538  || 6.575  || 65.2  || 4.0900  || 1.0  || 296.0  || 15.3  || 396.90  || 4.98  || 24.0  |
| 1  || 0.02731  || 0.0  || 7.07  || no  || 0.469  || 6.421  || 78.9  || 4.9671  || 2.0  || 242.0  || 17.8  || 396.90  || 9.14  || 21.6  |
| 3  || 0.03237  || 0.0  || 2.18  || no  || 0.458  || 6.998  || 45.8  || 6.0622  || 3.0  || 222.0  || 18.7  || 394.63  || 2.94  || 33.4  |
| 6  || 0.08829  || 12.5  || 7.87  || no  || 0.524  || 6.012  || 66.6  || 5.5605  || 5.0  || 311.0  || 15.2  || 395.60  || 12.43  || 22.9  |
| 7  || 0.14455  || 12.5  || 7.87  || no  || 0.524  || 6.172  || 96.1  || 5.9505  || 5.0  || 311.0  || 15.2  || 396.90  || 19.15  || 27.1  |

This should tell you that data is somewhat messy, out of balance, and with outlier values that throw the analysis and learning off-kilter. Thanks to the Google Research team, we now have a tool that makes this easy. It’s called Facets, and it helps you to visualize and slice the data in multiple ways. You can use Facets to find where data doesn’t look quite rights, and Google has made it so you can easily embed Facets into a Jupyter Notebook. Facets Overview Facets Overview lets you see the dataset overview, splitting the data columns into rows of important information. This information shows: 

*   Percentage of observations missing 
*   The min and max values 
*   Data statistics, such as standard deviation, mean, and median. 
*   A new column showing the percentage of zero values 
*   A way of seeing the distributions on the test and training set for every feature. This lets you check that the test and training sets have a similar distribution. 

Facets Deep Dive Deep Dive is another great tool that lets you understand your dataset better and zoom in to see individual data. The data can be faceted by columns and rows across any dataset feature. Both of these tools will be used with our Boston dataset, but you cannot use them together. The Notebook must be cleared between tools. Installing Facet To do this, you need nbextensions installed, using the code below: pip install jupyter\_contrib\_nbextensions                 Now you must clone your computer repositories. First, go to https://git-scm.com/download/win and install Git on your computer. Now open your terminal or Anaconda prompt and type the following code: git clone https://github.com/PAIR-code/facets             The following command will let you see where Facets has been stored: echo \`pwd\`/\`ls facets.\`          Now you can install Facets in Jupyter Notebook, and this requires you to set your working directory, so it is the path to where Facets is. The directory needs to be pointed to Facet: cd facets You now have two choices for installing Facets in Jupyter. If you used conda to install Jupyter, use this code: can use jupyter nbextension install facets-dist/ jupyter nbextension install facets-dist/ If you didn’t use conda, use this code: jupyter nbextension install facets-dist/ --user Time to launch Facet Overview. Facet Overview Overview computes statistics using a Python script called generic\_feature\_statistics\_generator, and this needs to be imported to Jupyter. First, open Facets and open the facets\_overview file. From there, open Python and copy the path. Now go back into Jupyter and input the following code, using your own path: \# Add facets overview python code to python path# Add t  
 import sys  
sys.path.append(/Users/yourfile/facets/facets\_overview/python) The following command will import the script: from generic\_feature\_statistics\_generator import  
GenericFeatureStatisticsGenerator The code is as follows in Windows: import sys  
sys.path.append(r"C:\\Users\\Admin\\Anaconda3\\facets-master\\facets\_overview\\python")  
from generic\_feature\_statistics\_generator import GenericFeatureStatisticsGenerator Calculating the feature statistics requires the function called GenericFeatureStatisticsGenerator() and the ProtoFromDataFrames object. The DataFrame can be passed in a dictionary. For example, to create a train set summary statistics, the information could be stored in a dictionary, which would then be used in the ProtoFromDataFrames object. 'name': 'train,' 'table': df\_train        ‘name’ is the table display name, and, to compute the summary, you need to use the table name. In our example, df\_train is the name of the table with the data. \# Calculate feature statistics proto from datasets and stringify it to use in facets overview  
import base64  
gfsg = GenericFeatureStatisticsGenerator()  
proto = gfsg.ProtoFromDataFrames(\[{'name': 'train', 'table': df\_train},  
                                  {'name': 'test', 'table': df\_test}\])  
#proto = gfsg.ProtoFromDataFrames(\[{'name': 'train', 'table': df\_train}\])  
protostr = base64.b64encode(proto.SerializeToString()).decode("utf-8") Finally, copy the code below and paste it – this is GitHub code \# Display facets overview visualization for data# Displ  
from IPython.core.display import display, HTML  
HTML\_TEMPLATE = """<link rel="import" href="/nbextensions/facets-dist/facets-jupyter.html" >  
        <facets-overview id="elem"></facets-overview>  
        <script>  
          document.querySelector("#elem").protoInput = "{protostr}";  
        </script>"""  
html = HTML\_TEMPLATE.format(protostr=protostr)  
display(HTML(html)) Graph Once the data and the distribution has been checked, a correlation matrix can be plotted for computing the Pearson coefficient. This is bonded between 1 and -1; a positive correlation is indicated by positive values and negative correlations by negative values. You want to see which are the best variables for interaction terms: \## Choose an important feature and check with Dive  
%matplotlib inline   
import matplotlib.pyplot as plt  
import seaborn as sns  
 sns.set(style="ticks")  
\# Compute the correlation matrix  
corr = df.corr('pearson')  
\# Generate a mask for the upper triangle  
mask = np.zeros\_like(corr, dtype=np.bool)  
mask\[np.triu\_indices\_from(mask)\] = True  
\# Set up the matplotlib figure  
f, ax = plt.subplots(figsize=(11, 9))  
\# Generate custom diverging colormap  
cmap = sns.diverging\_palette(220, 10, as\_cmap=True)  
\# Draw heatmap with mask and correct aspect ratio  
sns.heatmap(corr, mask=mask, cmap=cmap, vmax=.3, center=0,annot=True,  
            square=True, linewidths=.5, cbar\_kws={"shrink": .5}) Output <matplotlib.axes.\_subplots.AxesSubplot at 0x1a184d6518>  
  Png The matrix shows that there is a strong correlation between PRICE and LSTAT and RM. You can also see a positive correlation between INDUS and NOX – both variables are going the same way. Plus, both of those have a correlation with PRICE, and there also exists a correlation between DIS and NOX and IND. All this tells you that NOX and IND could be good interaction term candidates, and DIS is worth a look too. We could take things further with a pair grid. We are going to compose one as follows: 

*   Top – scatter plot, fitted line 
*   Diagonal –  kernel density 
*   Bottom – multivariate kernel density 

Our focus will be on four independent variables, the ones with the strongest correlation to PRICE: 

*   INDUS 
*   LSTAT 
*   NOX 
*   RM 

By default, the standard error is added to the scatter plot: attributes = \["PRICE", "INDUS", "NOX", "RM", "LSTAT"\]  
g = sns.PairGrid(df\[attributes\])  
g = g.map\_upper(sns.regplot, color="g")  
g = g.map\_lower(sns.kdeplot,cmap="Reds", shade=True, shade\_lowest=False)  
g = g.map\_diag(sns.kdeplot) Top 

*   PRICE has a negative correlation with NOX, LSTAT, and INDUS and a positive one with RM 
*   PRICE and LSTAT show a small amount of non-linearity 
*   When PRICE equals 50, you see a straight line. The dataset description tells us PRICE is truncated to 50 

Diagonal 

*   There appears to be two clusters for NOX – 0.5 and 0.85 

If you wanted more information, you would look at the bottom. The multivariate kernel density shows us where most of the points accumulate; the stronger the color, the more points there are. Look at the NOX and INDUS multivariate density; you should see the two clusters and the positive correlation. When the industry share is over 18, we get a concentration of nitric oxide of more than 0.6. ![](image_rsrc9T4.jpg)If you want, you could consider putting an interaction term between NOX and INDUS. Lastly, we can use Deep Dive. When you open it, you will see four sections on the interface. In the center, you can zoom in on data; at the top is a drop-down menu for changing the data arrangement to control color, position, and facets. To the right, you can see a detailed look at a given data row; you can click any data dot in the center part, and it will show up in detail on the right. When you do the data visualization, you want to see the pairwise correlation between variables (independent) on house price. This requires a minimum of three variables, and 3D plots are notoriously tricky to work with. One way you could do this is by creating a categorical variable. This means creating a 2D plot. PRICE can be divided into four, each being a quartile, and we name the variable Q\_PRICE. \## Check the non-linearity with important features  
df\['Q\_PRICE'\] =  pd.qcut(df\['PRICE'\], 4, labels=\["Lowest", "Low", "Upper", "upper\_plus"\])  
\## Show the non-linearity between RM and LSTAT  
ax = sns.lmplot(x="DIS", y="INDUS", hue="Q\_PRICE", data=df, fit\_reg = False,palette="Set3") ![](image_rsrc9T5.jpg)Facets Deep Dive The data must be transformed into JSON format to open Deep Dive, and Pandas provides us with a useful object. After the Pandas dataset, use to\_json. The first code line deals with the dataset size: df\['Q\_PRICE'\] =  pd.qcut(df\['PRICE'\], 4, labels=\["Lowest", "Low", "Upper", "upper\_plus"\])  
sprite\_size = 32 if len(df.index)>50000 else 64  
jsonstr = df.to\_json(orient='records') The next code has been taken from GitHub: \# Display Dive visualization for data  
from IPython.core.display import display, HTML  
\# Create Facets template    
HTML\_TEMPLATE = """<link rel="import" href="/nbextensions/facets-dist/facets-jupyter.html">  
        <facets-dive sprite-image-width="{sprite\_size}" sprite-image-height="{sprite\_size}" id="elem" height="600"></facets-dive>  
        <script>  
          document.querySelector("#elem").data = {jsonstr};  
        </script>"""  
\# Load json dataset and sprite\_size into template  
html = HTML\_TEMPLATE.format(jsonstr=jsonstr, sprite\_size=sprite\_size)  
\# Display the template  
display(HTML(html)) You want to know if the industry rate, house price, distance to the job center, and oxide concentration are connected. To do that, we  need the data split by color and industry range, using the price quartile: 

*   Choose Faceting X and then INDUS 
*   Choose Display, and then DIS – the dots that have the house price quartile are colored. 

The darker the color, the further away the first job center is. So, what we see from this is what we know already – a low industry rate means a higher price. What we do now is examine the breakdown by NOX and INDUX. Choose Faceting Y and then NOX. You should see that the furthest house from the first job center has a low industry share and a low concentration of oxide. You now have another indication that IND, DIS, and NOX have a good interaction and can be used to improve your model. TensorFlow Now we will use the estimators API in TensorFlow to estimate our linear classifier. Preparing the Data Most of the time, your data will need to be transformed, and Facets Overview is perfect for this. We could see that we had outliers, values that have a negative effect on the estimates because they look nothing like the data you want to analyze. We can get around this by standardizing the variable. This means that we get a standard deviation of one, with a mean of zero. There are two steps to this – first, the variable’s mean value is subtracted, and, second, it is divided by the variance to provide the distribution with unit variance. The best library for this is Sklearn and the preprocessing module. The function below helps you scale your dataset – note that the categorical variables and label column are not scaled. from sklearn import preprocessing  
def standardize\_data(df):  
    X\_scaled = preprocessing.scale(df\[\['CRIM', 'ZN', 'INDUS', 'NOX', 'RM', 'AGE', 'DIS', 'RAD',  
       'TAX', 'PTRATIO', 'B', 'LSTAT'\]\])  
    X\_scaled\_df = pd.DataFrame(X\_scaled, columns = \['CRIM', 'ZN', 'INDUS', 'NOX', 'RM', 'AGE', 'DIS', 'RAD',  
       'TAX', 'PTRATIO', 'B', 'LSTAT'\])  
    df\_scale = pd.concat(\[X\_scaled\_df,  
                       df\['CHAS'\],  
                       df\['PRICE'\]\],axis=1, join='inner')  
    return df\_scale The function below constructs the scaled training and test set: df\_train\_scale = standardize\_data(df\_train)  
df\_test\_scale = standardize\_data(df\_test)                Basic Regression - Benchmark The first thing to do is to train the model and test it with no interaction to see how the model performs. You saw how to do this earlier with the high-level API. We will use the LinearRegressor estimator from TensorFlow. To remind you, you must: 

*   Choose the model features 
*   Transform them 
*   Construct your linear regressor 
*   Construct the function, input\_fn 
*   Train your model 
*   Test it 

The model is trained using all of the dataset variables – one categorical and eleven continuous: \## Add features to bucket:  
\### Define continuous list  
CONTI\_FEATURES  = \['CRIM', 'ZN', 'INDUS', 'NOX', 'RM', 'AGE', 'DIS', 'RAD','TAX', 'PTRATIO', 'B', 'LSTAT'\]  
CATE\_FEATURES = \['CHAS'\] The features are converted to a categorical or numeric column: continuous\_features = \[tf.feature\_column.numeric\_column(k) for k in CONTI\_FEATURES\]  
#categorical\_features = tf.feature\_column.categorical\_column\_with\_hash\_bucket(CATE\_FEATURES, hash\_bucket\_size=1000)  
categorical\_features = \[tf.feature\_column.categorical\_column\_with\_vocabulary\_list('CHAS', \['yes','no'\])\] The model is created using the LinearRegressor and stored in a folder called train\_Boston: model = tf.estimator.LinearRegressor(      
        model\_dir="train\_Boston",       
    feature\_columns=categorical\_features + continuous\_features) Output INFO:tensorflow:Using default config.  
INFO:tensorflow:Using config: {'\_model\_dir': 'train\_Boston', '\_tf\_random\_seed': None, '\_save\_summary\_steps': 100, '\_save\_checkpoints\_steps': None, '\_save\_checkpoints\_secs': 600, '\_session\_config': None, '\_keep\_checkpoint\_max': 5, '\_keep\_checkpoint\_every\_n\_hours': 10000, '\_log\_step\_count\_steps': 100, '\_train\_distribute': None, '\_service': None, '\_cluster\_spec': <tensorflow.python.training.server\_lib.ClusterSpec object at  0x1a19e76ac8>, '\_task\_type': 'worker', '\_task\_id': 0, '\_global\_id\_in\_cluster': 0, '\_master': '', '\_evaluation\_master': '', '\_is\_chief': True, '\_num\_ps\_replicas': 0, '\_num\_worker\_replicas': 1}  
All columns inside the training or test data are converted to Tensors using get\_input\_fn: FEATURES = \['CRIM', 'ZN', 'INDUS', 'NOX', 'RM', 'AGE', 'DIS', 'RAD','TAX', 'PTRATIO', 'B', 'LSTAT', 'CHAS'\]  
LABEL= 'PRICE'  
def get\_input\_fn(data\_set, num\_epochs=None, n\_batch = 128, shuffle=True):  
    return tf.estimator.inputs.pandas\_input\_fn(  
       x=pd.DataFrame({k: data\_set\[k\].values for k in FEATURES}),  
       y = pd.Series(data\_set\[LABEL\].values),  
       batch\_size=n\_batch,     
       num\_epochs=num\_epochs,  
       shuffle=shuffle)  
  The training data is used for estimating the model. model.train(input\_fn=get\_input\_fn(df\_train\_scale,  
                                      num\_epochs=None,  
                                      n\_batch = 128,  
                                      shuffle=False),  
                                      steps=1000) Output INFO:tensorflow:Calling model\_fn.  
INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Create CheckpointSaverHook.  
INFO:tensorflow:Graph was finalized.  
 INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Saving checkpoints for 1 into train\_Boston/model.ckpt.  
INFO:tensorflow:loss = 56417.703, step = 1  
INFO:tensorflow:global\_step/sec: 144.457  
INFO:tensorflow:loss = 76982.734, step = 101 (0.697 sec)  
INFO:tensorflow:global\_step/sec: 258.392  
INFO:tensorflow:loss = 21246.334, step = 201 (0.383 sec)  
INFO:tensorflow:global\_step/sec: 227.998  
INFO:tensorflow:loss = 30534.78, step = 301 (0.439 sec)  
INFO:tensorflow:global\_step/sec: 210.739  
INFO:tensorflow:loss = 36794.5, step = 401 (0.477 sec)  
INFO:tensorflow:global\_step/sec: 234.237  
INFO:tensorflow:loss = 8562.981, step = 501 (0.425 sec)  
INFO:tensorflow:global\_step/sec: 238.1  
INFO:tensorflow:loss = 34465.08, step = 601 (0.420 sec)  
INFO:tensorflow:global\_step/sec: 237.934  
INFO:tensorflow:loss = 12241.709, step = 701 (0.420 sec)  
INFO:tensorflow:global\_step/sec: 220.687  
INFO:tensorflow:loss = 11019.228, step = 801 (0.453 sec)  
INFO:tensorflow:global\_step/sec: 232.702  
INFO:tensorflow:loss = 24049.678, step = 901 (0.432 sec)  
INFO:tensorflow:Saving checkpoints for 1000 into train\_Boston/model.ckpt.  
INFO:tensorflow:Loss for final step: 23228.568. <tensorflow.python.estimator.canned.linear.LinearRegressor at 0x1a19e76320>  
  Finally, the test set is used to estimate the model performance: model.evaluate(input\_fn=get\_input\_fn(df\_test\_scale,  
                                       num\_epochs=1,  
                                      n\_batch = 128,  
                                      shuffle=False),  
                                      steps=1000) Output INFO:tensorflow:Calling model\_fn.  
INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Starting evaluation at 2018-05-29-02:40:43  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Restoring parameters from train\_Boston/model.ckpt-1000  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Finished evaluation at 2018-05-29-02:40:43  
INFO:tensorflow:Saving dict for global step 1000: average\_loss = 86.89361, global\_step = 1000, loss = 1650.9785 {'average\_loss': 86.89361, 'global\_step': 1000, 'loss': 1650.9785} The loss here is 1650 – this is what we want to beat. Improving the Model – Interaction Terms Earlier, we saw some good relationships between our variables, and, by using visualization, we can see that NOS and INDUS are linked, magnifying the price effect. And when DIS comes into the interaction, the effect is even stronger. The next step is to improve the predictions using a generalization. For this, the train and test sets each need an additional two columns. We need two new functions – one for computing the interaction term and the other for the triple interaction term. Each of these functions produces one column. Once you have created the variables, they can be concatenated to each dataset. First, the NOX and INDUS interaction variable must be created. The function will return DataFrames called train and test, and the interactions are between var\_ 1 and var\_2 – NOX and INDUS. def interaction\_term(var\_1, var\_2, name):  
    t\_train = df\_train\_scale\[var\_1\]\*df\_train\_scale\[var\_2\]  
    train = t\_train.rename(name)  
    t\_test = df\_test\_scale\[var\_1\]\*df\_test\_scale\[var\_2\]  
    test = t\_test.rename(name)  
    return train, test The new columns are stored: interation\_ind\_ns\_train, interation\_ind\_ns\_test= interaction\_term('INDUS', 'NOX', 'INDUS\_NOS')  
interation\_ind\_ns\_train.shape  
(325,) Another function is created for computing the triple interaction term: def triple\_interaction\_term(var\_1, var\_2,var\_3, name):  
    t\_train = df\_train\_scale\[var\_1\]\*df\_train\_scale\[var\_2\]\*df\_train\_scale\[var\_3\]  
    train = t\_train.rename(name)  
    t\_test = df\_test\_scale\[var\_1\]\*df\_test\_scale\[var\_2\]\*df\_test\_scale\[var\_3\]  
    test = t\_test.rename(name)  
    return train, test  
interation\_ind\_ns\_dis\_train, interation\_ind\_ns\_dis\_test= triple\_interaction\_term('INDUS', 'NOX', 'DIS','INDUS\_NOS\_DIS') You can now add the columns to the train dataset and test dataset – we name them df\_train\_new and df\_test\_new. df\_train\_new = pd.concat(\[df\_train\_scale,  
                           interation\_ind\_ns\_train,  
                          interation\_ind\_ns\_dis\_train\],  
                         axis=1, join='inner')  
df\_test\_new = pd.concat(\[df\_test\_scale,  
                         interation\_ind\_ns\_test,  
                         interation\_ind\_ns\_dis\_test\],  
                         axis=1, join='inner')  
df\_train\_new.head(5) Output ![](image_rsrc9T6.jpg)Now, the new model can be estimated using the interaction terms and you can see the performance metric: CONTI\_FEATURES\_NEW  = \['CRIM', 'ZN', 'INDUS', 'NOX', 'RM', 'AGE', 'DIS', 'RAD','TAX', 'PTRATIO', 'B', 'LSTAT',  
                       'INDUS\_NOS', 'INDUS\_NOS\_DIS'\]  
\### Define categorical list  
continuous\_features\_new = \[tf.feature\_column.numeric\_column(k) for k in CONTI\_FEATURES\_NEW\]  
model = tf.estimator.LinearRegressor(  
    model\_dir="train\_Boston\_1",  
    feature\_columns= categorical\_features + continuous\_features\_new) Output INFO:tensorflow:Using default config.  
INFO:tensorflow:Using config: {'\_model\_dir': 'train\_Boston\_1', '\_tf\_random\_seed': None, '\_save\_summary\_steps': 100,  '\_save\_checkpoints\_steps': None, '\_save\_checkpoints\_secs': 600, '\_session\_config': None, '\_keep\_checkpoint\_max': 5, '\_keep\_checkpoint\_every\_n\_hours': 10000, '\_log\_step\_count\_steps': 100, '\_train\_distribute': None, '\_service': None, '\_cluster\_spec': <tensorflow.python.training.server\_lib.ClusterSpec object at 0x1a1a5d5860>, '\_task\_type': 'worker', '\_task\_id': 0, '\_global\_id\_in\_cluster': 0, '\_master': '', '\_evaluation\_master': '', '\_is\_chief': True, '\_num\_ps\_replicas': 0, '\_num\_worker\_replicas': 1}  
  CODE FEATURES = \['CRIM', 'ZN', 'INDUS', 'NOX', 'RM', 'AGE', 'DIS', 'RAD','TAX', 'PTRATIO', 'B', 'LSTAT','INDUS\_NOS', 'INDUS\_NOS\_DIS','CHAS'\]  
LABEL= 'PRICE'  
def get\_input\_fn(data\_set, num\_epochs=None, n\_batch = 128, shuffle=True):  
    return tf.estimator.inputs.pandas\_input\_fn(  
       x=pd.DataFrame({k: data\_set\[k\].values for k in FEATURES}),  
       y = pd.Series(data\_set\[LABEL\].values),  
       batch\_size=n\_batch,     
       num\_epochs=num\_epochs,  
       shuffle=shuffle)  
  model.train(input\_fn=get\_input\_fn(df\_train\_new,  
                                      num\_epochs=None,  
                                      n\_batch = 128, shuffle=False),  
                                      steps=1000) Output INFO:tensorflow:Calling model\_fn.  
INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Create CheckpointSaverHook.  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Saving checkpoints for 1 into train\_Boston\_1/model.ckpt.  
INFO:tensorflow:loss = 56417.703, step = 1  
INFO:tensorflow:global\_step/sec: 124.844  
INFO:tensorflow:loss = 65522.3, step = 101 (0.803 sec)  
INFO:tensorflow:global\_step/sec: 182.704  
INFO:tensorflow:loss = 15384.148, step = 201 (0.549 sec)  
INFO:tensorflow:global\_step/sec: 208.189  
INFO:tensorflow:loss = 22020.305, step = 301 (0.482 sec)  
INFO:tensorflow:global\_step/sec: 213.855  
INFO:tensorflow:loss = 28208.812, step = 401 (0.468 sec)  
INFO:tensorflow:global\_step/sec: 209.758  
INFO:tensorflow:loss = 7606.877, step = 501 (0.473 sec)  
INFO:tensorflow:global\_step/sec: 196.618  
INFO:tensorflow:loss = 26679.76, step = 601 (0.514 sec)  
INFO:tensorflow:global\_step/sec: 196.472  
INFO:tensorflow:loss = 11377.163, step = 701 (0.504 sec)  
INFO:tensorflow:global\_step/sec: 172.82  
INFO:tensorflow:loss = 8592.07, step = 801 (0.578 sec)  
INFO:tensorflow:global\_step/sec: 168.916  
INFO:tensorflow:loss = 19878.56, step = 901 (0.592 sec)  
INFO:tensorflow:Saving checkpoints for 1000 into train\_Boston\_1/model.ckpt.  
INFO:tensorflow:Loss for final step: 19598.387. <tensorflow.python.estimator.canned.linear.LinearRegressor at 0x1a1a5d5e10> model.evaluate(input\_fn=get\_input\_fn(df\_test\_new,  
                                      num\_epochs=1,  
                                       n\_batch = 128,  
                                      shuffle=False),  
                                      steps=1000) Output INFO:tensorflow:Calling model\_fn.  
INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Starting evaluation at 2018-05-29-02:41:14  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Restoring parameters from train\_Boston\_1/model.ckpt-1000  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Finished evaluation at 2018-05-29-02:41:14  
INFO:tensorflow:Saving dict for global step 1000: average\_loss = 79.78876, global\_step = 1000, loss = 1515.9863 {'average\_loss': 79.78876, 'global\_step': 1000, 'loss': 1515.9863} We now have a loss of 1515, a decrease from before, just by adding two more variables. Your model can now make much better predictions. Next, we turn our attention to kernel methods. 

Chapter 12 Kernel Methods ![](image_rsrc9SG.jpg)We’re going to look at how to linearly separate a dataset; we’ll look at feature transformation before using TensorFlow to train kernel classifiers using the adult dataset to classify revenue above and below $50k, based on household behavior. Why You Need Kernel Methods Every classifier has one aim – to correctly predict classes. To do that, you need a separable dataset. Have a look at the simple plot below. The points on top of the black line go in the first class, and the ones below go in the second class. Typically, though, datasets are rarely that simple and, most of the time, the data is not separable, and this proves challenging to logistic regression and other naïve classifiers: import numpy as np  
  import matplotlib.pyplot as plt  
  from mpl\_toolkits.mplot3d import Axes3D   x\_lin = np.array(\[1,2,3,4,5,6,7,8,9,10\])  
  y\_lin = np.array(\[2,2,3,2,2,9,6,8,8,9\])  
  label\_lin = np.array(\[0,0,0,0,0,1,1,1,1,1\])  
  fig = plt.figure()  
  ax=fig.add\_subplot(111)  
  plt.scatter(x\_lin, y\_lin, c=label\_lin, s=60)  
  plt.plot(\[-2.5, 10\], \[12.5, -2.5\], 'k-', lw=2)  
  ax.set\_xlim(\[-5,15\])  
  ax.set\_ylim(\[-5,15\])plt.show()                         Next, we plot a non-linearly separable dataset, which shows, if a  straight line were drawn, most points wouldn’t be correctly classified. We could tackle this by transforming the data in a separate feature map, which means we transform the data, using a function, in a linear plan: x = np.array(\[1,1,2,3,3,6,6,6,9,9,10,11,12,13,16,18\])  
y = np.array(\[18,13,9,6,15,11,6,3,5,2,10,5,6,1,3,1\])  
label = np.array(\[1,1,1,1,0,0,0,1,0,1,0,0,0,1,0,1\])    fig = plt.figure()  
plt.scatter(x, y, c=label, s=60)  
plt.show()               ![](image_rsrc9T7.jpg)The figure above shows a 2D, non-separable plan. You could attempt to transform the data in 3D, creating a 3-axis figure. We’re going to do this using polynomial mapping, using the following formula: ![](image_rsrc9T8.jpg)The function is defined to create the new maps in Python, and the formula can be coded using NumPy: 

| Formula  || Equivalent Code in NumPy  |
| --- | --- |
| x  || x\[:,0\]\*\*  |
| y  || x\[:,1\]  |
| x2  || x\[:,0\]\*\*2  |
| ![](image_rsrc9T9.jpg) || np.sqrt(2)\*  |
| xy  || x\[:,0\]\*x\[:,1\]  |
| y2  || x\[:,1\]\*\*2  |

\### for illustration  
def mapping(x, y):      
        x = np.c\_\[(x, y)\]                                 
    if len(x) >      2:          
        x\_1 = x\[:,0\]\*\*2          
        x\_2 = np.sqrt(2)\*x\[:,0\]\*x\[:,1\]          
        x\_3 = x\[:,1\]\*\*2                                                           
    else:              
        x\_1 = x\[0\]\*\*2          
        x\_2 = np.sqrt(2)\*x\[0\]\*x\[1\]          
        x\_3 = x\[1\]\*\*2                         
   trans\_x = np.array(\[x\_1, x\_2, x\_3\])                            
   return trans\_x                       The resultant map should be 3D and have 16 points: x\_1  = mapping(x, y)  
x\_1.shape                       (3, 16)           Let’s try a 3-axis plot, with x, y, and z:         
  \# plot  
fig = plt.figure()  
ax = fig.add\_subplot(111, projection='3d')  
ax.scatter(x\_1\[0\], x\_1\[1\], x\_1\[2\], c=label, s=60)  
ax.view\_init(30, 185)ax.set\_xlabel('X Label')  
ax.set\_ylabel('Y Label')  
ax.set\_zlabel('Z Label')  
plt.show()                        
  ![](image_rsrc9TA.jpg)There is a small improvement and, changing the plot orientation shows us we now have a separable dataset: \# plot  
fig = plt.figure()  
ax = fig.add\_subplot(111, projection='3d')  
ax.scatter(x\_1\[0\], x\_1\[1\], x\_1\[1\], c=label, s=60)  
 ax.view\_init(0, -180)ax.set\_ylim(\[150,-50\])  
ax.set\_zlim(\[-10000,10000\])  
ax.set\_xlabel('X Label')  
ax.set\_ylabel('Y Label')  
ax.set\_zlabel('Z Label')plt.show()                        
  ![](image_rsrc9TB.jpg)You would struggle with the above dataset if you needed to manipulate a big dataset that needed at least two dimensions. Every data point would need to be transformed, and this clearly isn’t sustainable – it would take forever, and your computer may not have enough resources. The easiest way is to use a kernel. What is a Kernel? To make the data as near to linearly separable as possible, we need a higher-dimension feature space, and there are a lot of them – polynomial mapping, for a start. We also showed that transformation is not the best way with large amounts of data. What you can do is modify the data using a kernel function without needing a new feature plan. The kernel’s magic is in finding the right function that doesn’t get into the trouble caused by the high-dimensional computation. Kernel results are scalar, i.e., one-dimensional space. Once that function has been located, it can be plugged into the linear classifier. Here’s an example. We have a pair of vectors, x1 and x2. We will use polynomial mapping to get the higher dimension, and the output will be equal to the new feature product’s dot map.  

*   X1 and x2 need to be transformed to a new dimension 
*   The dot product must be computed 
*   X1 and x2 need to be transformed to a new dimension 

The function created earlier can do the higher dimension computation \## Kernel  
x1 = np.array(\[3,6\])  
x2 = np.array(\[10,10\])                    
x\_1 = mapping(x1, x2)  
print(x\_1)               Output \[\[  9.         100.        \]  
      \[ 25.45584412 141.42135624\]  
      \[ 36.         100.        \]\]                        
  Computing The Dot Product The NumPy object, dot, can be used to this between the first and second vectors in x\_1: print(np.dot(x\_1\[:,0\], x\_1\[:,1\]))         You get an output of 8100. You can see what the problem is – a new feature map has to be stored in memory so the dot product can be computed. If your dataset is massive, it simply isn’t effective. The polynomial kernel is better because it doesn’t transform the vector. The function effectively computes the x1 and x2 dot product as if the vectors had already been transformed to a higher dimension. The kernel function can be written in Python like this: def polynomial\_kernel(x, y, p=2):                                  
        return (np.dot(x, y)) \*\* p             The result is the power of the dot product. In the next example, the second degree of the kernel is returned, with an output equal to the first method – the real magic of a kernel:         polynomial\_kernel(x1, x2, p=2)                     
8100           Different Kernel Methods There are quite a few kernels, the simplest being the linear kernel, ideal for text classification. Other kernels include Gaussian and Polynomial. In the TensorFlow example, we’ll use Random Fourier. An estimator is built into TensorFlow for computing feature space and is a Gaussian kernel function approximation: ![](image_rsrc9TC.jpg)The function computes data point similarities in high dimension space. Using TensorFlow to Train a Gaussian Kernel  Classifier We want our algorithm to classify household earnings of above or below $50k. A logistic regression will be evaluated to provide a benchmark model, and then a kernel classifier is trained to improve the results. The following adult dataset variables are used: 

*   age 
*   capital\_gain 
*   capital\_loss 
*   education 
*   education\_num 
*   fnlwgt 
*   hours\_week 
*   label 
*   marital 
*   native\_country 
*   occupation 
*   race 
*   relationship 
*   sex 
*   workclass 

Step One – Importing the Libraries We need Pandas, TensorFlow and NumPy: #import numpy as np  
from sklearn.model\_selection  
import train\_test\_split  
 import tensorflow as tf  
import pandas as pd  
import numpy as np Step Two – Importing the Data Download the data and import it as a Pandas DataFrame \## Define path data  
COLUMNS = \['age','workclass', 'fnlwgt', 'education', 'education\_num', 'marital', 'occupation', 'relationship', 'race', 'sex', 'capital\_gain', 'capital\_loss', 'hours\_week', 'native\_country', 'label'\]  
PATH = "https://archive.ics.uci.edu/ml/machine-learning-databases/adult/adult.data"  
PATH\_test ="https://archive.ics.uci.edu/ml/machine-learning-databases/adult/adult.test  
"## Import                        
df\_train = pd.read\_csv(PATH, skipinitialspace=True, names = COLUMNS, index\_col=False)  
df\_test = pd.read\_csv(PATH\_test,skiprows = 1, skipinitialspace=True, names = COLUMNS, index\_col=False)                  The train and test sets are defined, now the column label can be changed to an integer from a string: label = {'<=50K': 0,'>50K': 1}  
df\_train.label = \[label\[item\] for item in df\_train.label\]  
label\_t = {'<=50K.': 0,'>50K.': 1}  
df\_test.label = \[label\_t\[item\] for item in df\_test.label\]   
df\_train.shape     
(32561, 15)                       
   Step Three – Data Preparation There are both categorical and continuous features in the dataset, and best practice says we should standardize the continuous variable values. The Scikit-learn function, StandardScaler, will do this, along with a user-defined function to convert the training and test sets easier.  The categorical and continuous values are concatenated to a dataset, and you should have a float32 type array: COLUMNS\_INT = \['age','fnlwgt','education\_num','capital\_gain', 'capital\_loss', 'hours\_week'\]  
CATE\_FEATURES = \['workclass', 'education', 'marital', 'occupation', 'relationship', 'race', 'sex', 'native\_country'\]  
from sklearn.preprocessing import StandardScaler  
from sklearn import preprocessing                         
def prep\_data\_str(df):                        
        scaler = StandardScaler()      
    le = preprocessing.LabelEncoder()         
    df\_toscale = df\[COLUMNS\_INT\]      
    df\_scaled = scaler.fit\_transform(df\_toscale.astype(np.float64))      
    X\_1 = df\[CATE\_FEATURES\].apply(le.fit\_transform)      
    y = df\['label'\].astype(np.int32)      
    X\_conc = np.c\_\[df\_scaled, X\_1\].astype(np.float32)  
    return X\_conc, y     You can now use the transformer function to convert your dataset and create the function called input\_fn X\_train, y\_train = prep\_data\_str(df\_train)  
X\_test, y\_test = prep\_data\_str(df\_test)  
print(X\_train.shape)                      
(32561, 14)             Next we are going to train our logistic regression to get a baseline accuracy. What we want to do is use a kernel classifier to beat the  baseline. Step Four – Constructing the Logistic Model – the Baseline The feature column is constructed with the real\_value\_column object, ensuring the variables are all dense data (numeric): feat\_column = tf.contrib.layers.real\_valued\_column('features', dimension=14)          We use the TensorFlow estimator to define the estimator, passing instruction to the feature columns, and state where the graph should be saved:          estimator = tf.estimator.LinearClassifier(feature\_columns=\[feat\_column\],  
                                          n\_classes=2,  
                                          model\_dir = "kernel\_log"  
                                         )        
INFO:tensorflow:Using default config.INFO:tensorflow:Using config: {'\_model\_dir': 'kernel\_log', '\_tf\_random\_seed': None, '\_save\_summary\_steps': 100, '\_save\_checkpoints\_steps': None, '\_save\_checkpoints\_secs': 600, '\_session\_config': None, '\_keep\_checkpoint\_max': 5, '\_keep\_checkpoint\_every\_n\_hours': 10000, '\_log\_step\_count\_steps': 100, '\_train\_distribute': None, '\_service': None, '\_cluster\_spec': <tensorflow.python.training.server\_lib.ClusterSpec object at 0x1a2003f780>, '\_task\_type': 'worker', '\_task\_id': 0, '\_global\_id\_in\_cluster': 0, '\_master': '', '\_evaluation\_master': '', '\_is\_chief': True, '\_num\_ps\_replicas': 0, '\_num\_worker\_replicas': 1}                 The logistic regression is trained on mini batches of 200: \# Train the model  
train\_input\_fn = tf.estimator.inputs.numpy\_input\_fn(      
        x={"features": X\_train},      
    y=y\_train,      
    batch\_size=200,      
    num\_epochs=None,      
    shuffle=True)                       A 1.000 iteration can be used to train the model: estimator.train(input\_fn=train\_input\_fn, steps=1000) INFO:tensorflow:Calling model\_fn.  
INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Create CheckpointSaverHook.  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Saving checkpoints for 1 into kernel\_log/model.ckpt.  
INFO:tensorflow:loss = 138.62949, step = 1  
INFO:tensorflow:global\_step/sec: 324.16  
INFO:tensorflow:loss = 87.16762, step = 101 (0.310 sec)  
INFO:tensorflow:global\_step/sec: 267.092  
INFO:tensorflow:loss = 71.53657, step = 201 (0.376 sec)  
INFO:tensorflow:global\_step/sec: 292.679  
INFO:tensorflow:loss = 69.56703, step = 301 (0.340 sec)  
INFO:tensorflow:global\_step/sec: 225.582  
INFO:tensorflow:loss = 74.615875, step = 401 (0.445 sec)  
INFO:tensorflow:global\_step/sec: 209.975  
INFO:tensorflow:loss = 76.49044, step = 501 (0.475 sec)  
INFO:tensorflow:global\_step/sec: 241.648  
INFO:tensorflow:loss = 66.38373, step = 601 (0.419 sec)  
 INFO:tensorflow:global\_step/sec: 305.193  
INFO:tensorflow:loss = 87.93341, step = 701 (0.327 sec)  
INFO:tensorflow:global\_step/sec: 396.295  
INFO:tensorflow:loss = 76.61518, step = 801 (0.249 sec)  
INFO:tensorflow:global\_step/sec: 359.857  
INFO:tensorflow:loss = 78.54885, step = 901 (0.277 sec)  
INFO:tensorflow:Saving checkpoints for 1000 into kernel\_log/model.ckpt.  
INFO:tensorflow:Loss for final step: 67.79706. <tensorflow.python.estimator.canned.linear.LinearClassifier at 0x1a1fa3cbe0> Step Six – Evaluating the Model The model is evaluated, on the entire dataset, using the NumPy estimator: \# Evaluation  
test\_input\_fn = tf.estimator.inputs.numpy\_input\_fn(  
    x={"features": X\_test},  
    y=y\_test,  
    batch\_size=16281,  
    num\_epochs=1,  
    shuffle=False)  
estimator.evaluate(input\_fn=test\_input\_fn, steps=1) INFO:tensorflow:Calling model\_fn.  
WARNING:tensorflow:Trapezoidal rule is known to produce incorrect PR-AUCs; please switch to "careful\_interpolation" instead.  
WARNING:tensorflow:Trapezoidal rule is known to produce incorrect PR-AUCs; please switch to "careful\_interpolation" instead.  
INFO:tensorflow:Done calling model\_fn.  
 INFO:tensorflow:Starting evaluation at 2018-07-12-15:58:22  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Restoring parameters from kernel\_log/model.ckpt-1000  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Evaluation \[1/1\]  
INFO:tensorflow:Finished evaluation at 2018-07-12-15:58:23  
INFO:tensorflow:Saving dict for global step 1000: accuracy = 0.82353663, accuracy\_baseline = 0.76377374, auc = 0.84898686, auc\_precision\_recall = 0.67214864, average\_loss = 0.3877216, global\_step = 1000, label/mean = 0.23622628, loss = 6312.495, precision = 0.7362797, prediction/mean = 0.21208474, recall = 0.39417577  
  {'accuracy': 0.82353663,  
'accuracy\_baseline': 0.76377374,  
'auc': 0.84898686,  
'auc\_precision\_recall': 0.67214864,  
'average\_loss': 0.3877216,  
'global\_step': 1000,  
'label/mean': 0.23622628,  
'loss': 6312.495,  
'precision': 0.7362797,  
'prediction/mean': 0.21208474,  
'recall': 0.39417577} The accuracy is 82% so, next, we want to use a Kernel classifier to beat it. Step Seven – Constructing the Kernel Classifier This isn’t much different to a standard linear classifier. We require a pair of pre-defined estimators from TensorFlow: 

*   RandomFourierFeatureMapper 
*   KernelLinearClassifier 

We’re going to use the Random Fourier to transform low to high dimension with the kernel function and you can find the right function in TensorFlow, RandomFourierFeatureMapper. We can train the model using the KernelLinearClassifer estimator. Step One – Setting the Kernel Function (High Dimension) We have 14 features in the dataset that need transforming to 5.000-dimension vectors, using the features in Random Fourier. If you recall, you need to define a parameter for the standard deviation; this is for controlling the similarity measure the classification uses. All the parameters can be tuned in the RandomFourierFeatureMapper using: 

*   input\_dim = 14 
*   output\_dim= 5000 
*   stddev=4 

\### Prep Kernel  
kernel\_mapper = tf.contrib.kernel\_methods.RandomFourierFeatureMapper(input\_dim=14, output\_dim=5000, stddev=4, name='rffm')          The kernel mapper must be constructed using the previously created feature columns.       feat\_column \### Map Kernel  
kernel\_mappers = {feat\_column: \[kernel\_mapper\]}  
  Step Two – Setting the L2 Hyperparameter The loss function must be penalized to avoid overfitting; this is done with the L2 regularizer, setting L2 to 0.1, and the learning rate as 5. optimizer = tf.train.FtrlOptimizer(learning\_rate=5, l2\_regularization\_strength=0.1)     Step Three – Building the Model This is much like the linear classification; KernelLinearClassifier is used, along with the previously defined kernel mapper, and the model directory is changed: \### Prep estimator  
estimator\_kernel = tf.contrib.kernel\_methods.KernelLinearClassifier(  
    n\_classes=2,  
    optimizer=optimizer,  
    kernel\_mappers=kernel\_mappers,  
    model\_dir="kernel\_train")  
  WARNING:tensorflow:From /Users/Thomas/anaconda3/envs/hello-tf/lib/python3.6/site-packages/tensorflow/contrib/kernel\_methods/python/kernel\_estimators.py:305: multi\_class\_head (from tensorflow.contrib.learn.python.learn.estimators.head) is deprecated and will be removed in a future version.  
Instructions for updating:  
Please switch to tf.contrib.estimator.\*\_head.  
WARNING:tensorflow:From /Users/Thomas/anaconda3/envs/hello-tf/lib/python3.6/site-packages/tensorflow/contrib/learn/python/learn/estimators/estimator.py:1179: BaseEstimator.\_\_init\_\_ (from tensorflow.contrib.learn.python.learn.estimators.estimator) is  deprecated and will be removed in a future version.  
Instructions for updating:  
Please replace uses of any Estimator from tf.contrib.learn with an Estimator from tf.estimator.\*  
WARNING:tensorflow:From /Users/Thomas/anaconda3/envs/hello-tf/lib/python3.6/site-packages/tensorflow/contrib/learn/python/learn/estimators/estimator.py:427: RunConfig.\_\_init\_\_ (from tensorflow.contrib.learn.python.learn.estimators.run\_config) is deprecated and will be removed in a future version.  
Instructions for updating:  
When switching to tf.estimator.Estimator, use tf.estimator.RunConfig instead.  
INFO:tensorflow:Using default config.  
INFO:tensorflow:Using config: {'\_task\_type': None, '\_task\_id': 0, '\_cluster\_spec': <tensorflow.python.training.server\_lib.ClusterSpec object at 0x1a200ae550>, '\_master': '', '\_num\_ps\_replicas': 0, '\_num\_worker\_replicas': 0, '\_environment': 'local', '\_is\_chief': True, '\_evaluation\_master': '', '\_train\_distribute': None, '\_tf\_config': gpu\_options {  
  per\_process\_gpu\_memory\_fraction: 1.0  
}  
, '\_tf\_random\_seed': None, '\_save\_summary\_steps': 100, '\_save\_checkpoints\_secs': 600, '\_log\_step\_count\_steps': 100, '\_session\_config': None, '\_save\_checkpoints\_steps': None, '\_keep\_checkpoint\_max': 5, '\_keep\_checkpoint\_every\_n\_hours': 10000, '\_model\_dir': 'kernel\_train'} Step Four – Training the Model We are now ready to train the model, iterating it 2,000 times:  
\### estimate  
 estimator\_kernel.fit(input\_fn=train\_input\_fn, steps=2000)  
  WARNING:tensorflow:Casting <dtype: 'int32'> labels to bool.  
WARNING:tensorflow:Casting <dtype: 'int32'> labels to bool.  
WARNING:tensorflow:Trapezoidal rule is known to produce incorrect PR-AUCs; please switch to "careful\_interpolation" instead.  
WARNING:tensorflow:Trapezoidal rule is known to produce incorrect PR-AUCs; please switch to "careful\_interpolation" instead.  
WARNING:tensorflow:From /Users/Thomas/anaconda3/envs/hello-tf/lib/python3.6/site-packages/tensorflow/contrib/learn/python/learn/estimators/head.py:678: ModelFnOps.\_\_new\_\_ (from tensorflow.contrib.learn.python.learn.estimators.model\_fn) is deprecated and will be removed in a future version.  
Instructions for updating:  
When switching to tf.estimator.Estimator, use tf.estimator.EstimatorSpec. You can use the \`estimator\_spec\` method to create an equivalent one.  
INFO:tensorflow:Create CheckpointSaverHook.  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Saving checkpoints for 1 into kernel\_train/model.ckpt.  
INFO:tensorflow:loss = 0.6931474, step = 1  
INFO:tensorflow:global\_step/sec: 86.6365  
INFO:tensorflow:loss = 0.39374447, step = 101 (1.155 sec)  
INFO:tensorflow:global\_step/sec: 80.1986  
INFO:tensorflow:loss = 0.3797774, step = 201 (1.247 sec)  
INFO:tensorflow:global\_step/sec: 79.6376  
INFO:tensorflow:loss = 0.3908726, step = 301 (1.256 sec)  
INFO:tensorflow:global\_step/sec: 95.8442  
 INFO:tensorflow:loss = 0.41890752, step = 401 (1.043 sec)  
INFO:tensorflow:global\_step/sec: 93.7799  
INFO:tensorflow:loss = 0.35700393, step = 501 (1.066 sec)  
INFO:tensorflow:global\_step/sec: 94.7071  
INFO:tensorflow:loss = 0.35535482, step = 601 (1.056 sec)  
INFO:tensorflow:global\_step/sec: 90.7402  
INFO:tensorflow:loss = 0.3692882, step = 701 (1.102 sec)  
INFO:tensorflow:global\_step/sec: 94.4924  
INFO:tensorflow:loss = 0.34746957, step = 801 (1.058 sec)  
INFO:tensorflow:global\_step/sec: 95.3472  
INFO:tensorflow:loss = 0.33655524, step = 901 (1.049 sec)  
INFO:tensorflow:global\_step/sec: 97.2928  
INFO:tensorflow:loss = 0.35966292, step = 1001 (1.028 sec)  
INFO:tensorflow:global\_step/sec: 85.6761  
INFO:tensorflow:loss = 0.31254214, step = 1101 (1.167 sec)  
INFO:tensorflow:global\_step/sec: 91.4194  
INFO:tensorflow:loss = 0.33247527, step = 1201 (1.094 sec)  
INFO:tensorflow:global\_step/sec: 82.5954  
INFO:tensorflow:loss = 0.29305756, step = 1301 (1.211 sec)  
INFO:tensorflow:global\_step/sec: 89.8748  
INFO:tensorflow:loss = 0.37943482, step = 1401 (1.113 sec)  
INFO:tensorflow:global\_step/sec: 76.9761  
INFO:tensorflow:loss = 0.34204718, step = 1501 (1.300 sec)  
INFO:tensorflow:global\_step/sec: 73.7192  
INFO:tensorflow:loss = 0.34614792, step = 1601 (1.356 sec)  
INFO:tensorflow:global\_step/sec: 83.0573  
INFO:tensorflow:loss = 0.38911164, step = 1701 (1.204 sec)  
INFO:tensorflow:global\_step/sec: 71.7029  
INFO:tensorflow:loss = 0.35255936, step = 1801 (1.394 sec)  
INFO:tensorflow:global\_step/sec: 73.2663  
INFO:tensorflow:loss = 0.31130585, step = 1901 (1.365 sec)  
INFO:tensorflow:Saving checkpoints for 2000 into kernel\_train/model.ckpt.  
INFO:tensorflow:Loss for final step: 0.37795097.  
KernelLinearClassifier(params={'head': <tensorflow.contrib.learn.python.learn.estimators.head.\_BinaryLogisticHead object at 0x1a2054cd30>, 'feature\_columns': {\_RealValuedColumn(column\_name='features\_MAPPED', dimension=5000, default\_value=None, dtype=tf.float32, normalizer=None)}, 'optimizer': <tensorflow.python.training.ftrl.FtrlOptimizer object at 0x1a200aec18>, 'kernel\_mappers': {\_RealValuedColumn(column\_name='features', dimension=14, default\_value=None, dtype=tf.float32, normalizer=None): \[<tensorflow.contrib.kernel\_methods.python.mappers.random\_fourier\_features.RandomFourierFeatureMapper object at 0x1a200ae400>\]}})       Step Five – Evaluating the Model Finally, we can evaluate the model performance:               
\# Evaluate and report metrics.  
eval\_metrics = estimator\_kernel.evaluate(input\_fn=test\_input\_fn, steps=1)  
  WARNING:tensorflow:Casting <dtype: 'int32'> labels to bool.  
WARNING:tensorflow:Casting <dtype: 'int32'> labels to bool.  
WARNING:tensorflow:Trapezoidal rule is known to produce incorrect PR-AUCs; please switch to "careful\_interpolation" instead.  
WARNING:tensorflow:Trapezoidal rule is known to produce incorrect PR-AUCs; please switch to "careful\_interpolation" instead.  
INFO:tensorflow:Starting evaluation at 2018-07-12-15:58:50  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Restoring parameters from kernel\_train/model.ckpt-2000  
INFO:tensorflow:Running local\_init\_op.  
 INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Evaluation \[1/1\]  
INFO:tensorflow:Finished evaluation at 2018-07-12-15:58:51  
INFO:tensorflow:Saving dict for global step 2000: accuracy = 0.83975184, accuracy/baseline\_label\_mean = 0.23622628, accuracy/threshold\_0.500000\_mean = 0.83975184, auc = 0.8904007, auc\_precision\_recall = 0.72722375, global\_step = 2000, labels/actual\_label\_mean = 0.23622628, labels/prediction\_mean = 0.23786618, loss = 0.34277728, precision/positive\_threshold\_0.500000\_mean = 0.73001117, recall/positive\_threshold\_0.500000\_mean = 0.5104004 The final result is 84%, better than the logistic regression. In the next chapter, we are going to build an artificial neural network using TensorFlow. 

Chapter 13 Using TensorFlow to Build an ANN ![](image_rsrc9SG.jpg)Artificial Neural Networks consist of four primary principles: 

*   Layers – all learning happens inside the layers, and there are three – input, output, and hidden. 
*   Feature and label – the features are the network input data, and the labels are the network output 
*   Loss function – this metric is used for estimating the learning phase performance 
*   Optimizer – this updates the network knowledge, thus improving learning 

The program will take in the input data, pushing it to two layers (fully connected.) Let’s say that you have a math problem. First, you would learn about the problem and then apply the knowledge to help solve the problem. It is unlikely you will score well, and the same applies to neural networks – when it first sees data, it is unlikely the prediction will be accurate. The optimizer, in our case, re-reading the information on the math problem, helps you get more insights. In the same way, the network optimizer provides new knowledge, used by the network to test how much it must still learn. This step is repeated until the network gets the lowest possible error. If you re-read the math information repeatedly, until you have learned it, but still make errors, you have reached the end of the potential learning with this material and must find new material. The neural network works the same way; if it cannot learn any more with  the current knowledge but still needs to be improved, the network needs more optimization. Neural Network Architecture Layers All the learning happens in the layers. Each layer has many neurons (weights), and typical networks often use densely connected layers for processing. That means all inputs have a connection to the output. Typical networks will take a vector (the input) and a scalar with the labels. The input is sent to the connected nodes, and an activation function is used to compute the signal. 

1.  Node one contains the input values 
2.  We decompose the neuron to input and activation function. The input is received from the previous layer, summed, and passed to an activation function. 
3.  The output is computed using the hidden layers, and a prediction is made. In classification tasks, the prediction is equal to how many classes there are, while in regression, we only get a single value. 

Activation Function The activation function is used to define the output of a specified set of inputs. This allows networks to learn non-linear patterns. The most commonly used activation function is the Rectified Linear Unit or ReLu – this function provides zero for any negative value. Other common activation functions include: 

*   Leaky ReLu 
*   Piecewise Linear 
*   Sigmoid 
*   Tanh 

When you build a neural network, there are two critical decisions to make: 

*   The number of layers 
*   The number of hidden units in each layer 

If a network has multiple layers and multiple hidden units, it is capable of learning complex data representations, but the computation cost is expensive. Loss Function Once the layers and activation function are defined, the loss function must be specified, along with the optimizer. In binary classification tasks, we typically use a binary cross-entropy function while in linear regression, the MSE is used. Loss functions are an important part of estimating the optimizer performance, and, during training, it is minimized. Be careful when you choose the quantity – it must reflect the problem type. Optimizer Loss functions measure performance, and the optimizer improves the network weights to minimize the loss. The common optimizer is Stochastic Gradient, but others include: 

*   AdaGrad, 
*   Adam optimization 
*   Momentum optimization, 
*   Nesterov Accelerated Gradient, 

Neural Network Limitations Overfitting One of the most common problems associated with complex neural  networks is the generalization of unseen data. A network with many weights can identify training set details but tends to result in overfitting. If we have an imbalance of data within the groups (more in some than others), the network learns during the training session but cannot generalize patterns to unseen data. In machine learning, there is a trade-off between generalization and optimization, where the latter needs to find the optimum parameters to minimize loss, the former instructs the model on how it should act with unseen data. There are techniques we can use to stop a model from getting unwanted patterns or specific details from the training set, and the best way is to ensure the data is balanced with enough data. Regularization reduces overfitting, so let’s look at some techniques. Network Size If a network has many layers and units, it is considered sophisticated. The easiest way of reducing complexity is quite simple to reduce the size. Start with a small number of layers and increase until the model overfits. Weight Regularization Another standard method of stopping overfitting is to constrain the network weights, ensuring the network takes only smaller values. The constraint is placed in the error loss function; there are two regularization types: 

1.  L1: Lasso – the cost is proportionate to the weight coefficient absolute values 
2.  L2: Ridge – the cost is proportionate to the weight coefficient value squares 

Dropout This is a useful if odd technique. When a network has dropout, random weights are set as zero. Let’s say that you have an array  containing weights – \[0.1, 1.5, 0.8, -0.6\]. If there is a dropout, the array becomes \[0.1, 0.0, -0.6\] with zeroes distributed randomly. The dropout rate is the parameter controlling the dropout, and it defines the number of weights that should be set as zero. It is common to have a rate of 0.2 to 0.5. Using TensorFlow to Train a Neural Network Now we get practical and look at using the DNNClassifier estimator in TensorFlow to train a neural network using the MNIST dataset. This is not hard to do and is similar to the other tutorials we have gone through: Step One – Importing the Data First, we need the right library and the MNIST dataset, which you can download from http://yann.lecun.com/exdb/mnist/.  This is one of the most common datasets to test algorithms and techniques. It contains a series of images, 28x28 pixels, each with a digit from 0 to 9 handwritten on it. The lowest test error currently stands at 0.27%, using seven CNNs. import numpy as np  
import tensorflow as tf  
np.random.seed(1337) Next, download Scikit-learn – copy/paste the dataset into a folder and use fetch\_mldata in Scikit-learn to import the data. The file path, which will be your file path, is pasted into fetch\_mldata:  
from sklearn.datasets import fetch\_mldata  
mnist = fetch\_mldata(' /Users/yourname/yourfilepath/tuto\_TF/data/mldata/MNIST original')  
print(mnist.data.shape)  
print(mnist.target.shape) Now the data can be imported, and we can see the dataset shapes. from sklearn.model\_selection import train\_test\_split  
X\_train, X\_test, y\_train, y\_test = train\_test\_split(mnist.data, mnist.target, test\_size=0.2, random\_state=42)  
y\_train  = y\_train.astype(int)  
y\_test  = y\_test.astype(int)  
batch\_size =len(X\_train)  
print(X\_train.shape, y\_train.shape,y\_test.shape ) Step Two – Transforming the Data We are going to use the min-max scaler to transform our data, with the following formula: (X-min\_x)/(max\_x - min\_x) We use the MinMaxScaler() function from Scikit-learn: \## resclae  
from sklearn.preprocessing import MinMaxScaler  
scaler = MinMaxScaler()  
\# Train  
X\_train\_scaled = scaler.fit\_transform(X\_train.astype(np.float64))  
\# test  
X\_test\_scaled = scaler.fit\_transform(X\_test.astype(np.float64)) Step Three – Constructing the Tensor You already know how to do this in TensorFlow. The training set can be converted into a numeric column: feature\_columns = \[tf.feature\_column.numeric\_column('x', shape=X\_train\_scaled.shape\[1:\])\]            Step Four – Building the Model Our neural network has two hidden layers; in the first layer, we have 300 units, and, in the second layer, we have 100 units.  The DNNClassifier estimator is used for building the model. In the arguments for feature\_columns, you can define the number of layers, and the number of classes must be set to 10 – this is how many classes are in the training dataset.  Refer back to the previous tutorial to see what the feature columns for the arguments are, along with model\_dir and the class number – they are the same. We have a new argument named hidden\_unit, and this is for controlling how many layers there are and the numbers of nodes that are connected in the network. The estimator is built using tf.estimator.DNNClassifier and it has these parameters: 

*   feature\_columns:  how many columns are needed 
*   hidden\_units: how many hidden neurons there are 
*   n\_classes: how many classes will be predicted 
*   model\_dir: the TensorBoard Path 

estimator = tf.estimator.DNNClassifier(  
    feature\_columns=feature\_columns,  
    hidden\_units=\[300, 100\],  
    n\_classes=10,  
    model\_dir = '/train/DNN') Step Five – Training and Evaluating The NumPy method is used for this: \# Train the estimator  
 train\_input = tf.estimator.inputs.numpy\_input\_fn(  
    x={"x": X\_train\_scaled},  
    y=y\_train,  
    batch\_size=50,  
    shuffle=False,  
    num\_epochs=None)  
estimator.train(input\_fn = train\_input,steps=1000)  
eval\_input = tf.estimator.inputs.numpy\_input\_fn(  
    x={"x": X\_test\_scaled},  
    y=y\_test,  
    shuffle=False,  
    batch\_size=X\_test\_scaled.shape\[0\],  
    num\_epochs=1)  
estimator.evaluate(eval\_input,steps=None) Output {'accuracy': 0.9637143,  
'average\_loss': 0.12014342,  
'loss': 1682.0079,  
'global\_step': 1000} We get a 96% accuracy on evaluation Step Six – Improving the Model We could add some regularization parameters to see if we can improve things. The Adam optimizer will help, with a 0.3 dropout rate, and L1 is X, and L2 is y. Controlling the optimizer is done by using the optimizer name and the train object. In TensorFlow, you will find an API for the Proximal AdaGrad optimizer and tf.train.ProximalAdagradOptimizer is used to add the regularization, using these parameters: 

*   learning\_rate 
*   l1\_regularization\_strength 
*   l2\_regularization\_strength 

estimator\_imp = tf.estimator.DNNClassifier(  
    feature\_columns=feature\_columns,  
    hidden\_units=\[300, 100\],  
    dropout=0.3,  
    n\_classes = 10,  
    optimizer=tf.train.ProximalAdagradOptimizer(  
      learning\_rate=0.01,  
      l1\_regularization\_strength=0.01,  
      l2\_regularization\_strength=0.01  
    ),  
    model\_dir = '/train/DNN1')  
estimator\_imp.train(input\_fn = train\_input,steps=1000)  
estimator\_imp.evaluate(eval\_input,steps=None) Output {'accuracy': 0.95057142,  
'average\_loss': 0.17318928,  
'loss': 2424.6499,  
'global\_step': 2000} We did not manage to improve the accuracy by choosing different values. In fact, we made it worse – the first model had a 96% accuracy, this one 95%. Use some different values to play around with this and see the effects on the accuracy. In the next chapter, we will look at image classification with a Convnet. 

Chapter 14 Using TensorFlow for  
ConvNet Image Classification ![](image_rsrc9SG.jpg)ConvNets are otherwise known as convolutional neural networks or CNNS and are typically used for image classification tasks. We’re going to learn how to build one and then use it, with TensorFlow, on the MNIST dataset. Architecture of a ConvNet Many Facebook users will likely remember that, in the early days, they had to manually tag people in images they uploaded to the social network. Now it’s all done automatically using a convnet. These are pretty easy to understand – an image is processed as the input, and later given a label. Typically, an image is passed as an input; it goes through a number of steps, and then the network can make a prediction about the image. Each image is made up of arrays of pixels, having a width and a height. If the image is grayscale, it has only one channel, while color images have three – red, green, and blue – stacked on top of one another. The pixels are each given a value from 0 to 255; the lower the value, the lighter it is, and vice versa. The Convolutional Operation The convolutional layer is the most important part of a model, and its aim is to reduce the image size for faster weight computations and to make the generalization better. During this part of the process, the network will retain the  important  features in the image, cutting out unwanted noise, i.e., features that are meaningless and can skew the results. Instead, convnets extract only the pixels that are relevant by using a mathematical technique known as convolution. This lets networks learn features that increase in complexity at every layer; each matrix is divided into smaller parts so the essential bits can be learned in each part. ConvNet Components ConvNets have four stages or components: 

*   Convolution 
*   Non Linearity - ReLu 
*   Pooling/Sub-Sampling 
*   Classification - Fully Connected Layer 

Convolution The convolution layer has one purpose – to locally extract the image features. This means the network learns relevant patterns in the image so it can recognize them anywhere in the image Convolution is a type of multiplication done element-wise. It is easy enough to understand – a section of the image is scanned by the computer, usually a 3x3 dimension, which is then multiplied to a filter. The output is called a feature map, and this gets repeated until the entire image has been scanned. Once this is done, the image size is smaller. So, how does it work? In this stage, a filter is applied to a small pixel array from the image. This filter moves about the image in a 3x3 or 5x5 shape, computing the convolution. You will notice that the width and height of the output may not be the same as the input, and this is down to the  border effect. Let’s say that you have a feature map of 5x5 and a filter of 3x3. In the center is a single window that can screen a grid size of 3x3. The feature map that is output from this will be two tiles smaller, a dimension of 3x3. If you want the same input and output dimensions, padding needs to be added. This means that you add the correct number of columns and rows on every side of your matrix, ensuring the convolution fits all of the input tiles. When the network is defined, there are three parameters that control the convolved features: 

*   Depth :  defines how many filters should be applied in the convolution 
*   Stride : defines the jump number between two sliced. If you have a stride of 1, the windows move one pixel; the higher the stride, the smaller the feature map 
*   Zero-Padding : padding adds rows and columns on each side of the map, making the input and the output dimensions the same. 

Non Linearity – ReLu When the convolution process is finished, an activation function is used on the output to provide non-linearity. ReLu is the typical activation function, and all negative value pixels are replaced with zero. Max Pooling Pooling is designed to reduce the input image dimensionality, reducing the operation’s complexity. By reducing dimensionality, there are fewer weights that need computing; thus, overfitting is prevented. In pooling, the stride and size must be defined. The standard method is to use the feature map’s maximum value. The result is that the feature map size is significantly reduced. Fully Connected Layers The final stage is where the artificial neural network is built. All the neurons from each layer are connected to the next layer, and the input image number is classified using a SoftMax activation function. Training a  CNN Using TensorFlow Now it’s time to build a CNN using TensorFlow; we are using the MNIST dataset. Step One – Uploading the Dataset You can download the MNIST dataset from http://yann.lecun.com/exdb/mnist/.  Store it in your Downloads folder, and then we will use fetch\_mldata(‘MNIST original’) to upload it. Next, use train\_test\_split to divide the dataset into training and test sets. This is followed by using MinMaxScalar to scale the features. import numpy as np  
import tensorflow as tf  
from sklearn.datasets import fetch\_mldata  
#Change USERNAME to your computer username  
\## Windows USER  
mnist = fetch\_mldata('C:\\\\Users\\\\USERNAME\\\\Downloads\\\\MNIST original')  
\## Mac User  
mnist = fetch\_mldata('/Users/USERNAME/Downloads/MNIST original')  
print(mnist.data.shape)  
 print(mnist.target.shape)  
from sklearn.model\_selection import train\_test\_split  
X\_train, X\_test, y\_train, y\_test = train\_test\_split(mnist.data, mnist.target, test\_size=0.2, random\_state=42)  
y\_train  = y\_train.astype(int)  
y\_test  = y\_test.astype(int)  
batch\_size =len(X\_train)  
print(X\_train.shape, y\_train.shape,y\_test.shape )  
\## rescale  
from sklearn.preprocessing import MinMaxScaler  
scaler = MinMaxScaler()  
\# Train  
X\_train\_scaled = scaler.fit\_transform(X\_train.astype(np.float64))  
\# test  
X\_test\_scaled = scaler.fit\_transform(X\_test.astype(np.float64))  
feature\_columns = \[tf.feature\_column.numeric\_column('x', shape=X\_train\_scaled.shape\[1:\])\]  
X\_train\_scaled.shape\[1:\]  
  Defining the CNN Constructing a CNN requires: 

*   Convolutional Layer – n filters are applied to the feature map and, once the convolution is done a ReLu activation function is applied to provide the network with non-linearity 
*   Pooling Layer – the feature map needs to be downsampled; this reduces the feature map dimensionality, improves speed, and stops overfitting. Max pooling is the typical one, dividing maps into 2x2 subregions and retaining the max values 
*   Fully Connected Layers –  neurons are connected to the next layer, and the label is classified per the features that result from the convolutional process; the pooling layer reduces those results. 

CNN Architecture 

*   Convolutional Layer : 14 filters of 5x5 are applied, extracting subregions of 5x5, with ReLu 
*   Pooling Layer : a 2x2 filter is used with a stride of 2 to do the max pooling 
*   Convolutional Layer : 36 filters of 5x5 are applied with ReLu 
*   Pooling Layer : as above, filter of2x2 and stride of 2 
*   1,764 neurons: with a 0.4 dropout rate 
*   Dense Layer: one neuron for each of the target digit classes 0 to 9 = 10 neurons 

CNN's require three critical modules: 

*   conv2d() . To build a 2D layer, passing as arguments  how many filters, the size of the filter kernel, the padding, and the chosen activation function. 
*   max\_pooling2d(). To build a 2D layer with the ma-pooling algorithm. 
*   dense(). To build the dense layer containing units and hidden layers. 

Now we are going to build our CNN, so let’s delve into each building block before we pull it all together with the function. Step Two – The Input Layer def cnn\_model\_fn(features, labels, mode):  
    input\_layer = tf.reshape(tensor = features\["x"\],shape =\[-1, 28, 28, 1\]) We need a tensor defined with the data shape and we use the tf.reshape module to do that. The initial argument is the data features, defined in the function argument. The MNIST dataset contains monochronic images, size 28x28. Inside the shape argument, the batch size is set to -1, allowing it to take the features shape. Step Three – The Convolutional Layer \# first Convolutional Layer  
  conv1 = tf.layers.conv2d(  
      inputs=input\_layer,  
      filters=14,  
      kernel\_size=\[5, 5\],  
      padding="same",  
      activation=tf.nn.ReLu) There are 14 filters in the first layer with a 5x5 kernel size. Using the same padding ensures that the input and output tensors are the same height and width; TensorFlow does this by adding zeros to both the columns and rows. Then the ReLu function is used, resulting in an output size of \[28, 28, 14\]. Step Four – The Pooling Layer Once the convolution layer is finished, the pooling layer comes in. The computation reduces the data dimensionality, using the max\_pooling2d module with a 2x2 size and stride of 2. The previous layer is the input, and the size of the output should be \[batch\_size, 14, 14, 14\]. \# first Pooling Layer  
pool1 = tf.layers.max\_pooling2d(inputs=conv1, pool\_size=\[2, 2\], strides=2) Step Five – Second Round – Convolution and Pooling There are 32 filters on the next convolution layer and the size of the output is \[batch\_size, 14, 14, 32\]. The pooling layer is the same size as the last one and the output size is \[batch\_size, 14, 14, 18\]. conv2 = tf.layers.conv2d(  
      inputs=pool1,  
      filters=36,  
      kernel\_size=\[5, 5\],  
      padding="same",  
      activation=tf.nn.ReLu)  
pool2 = tf.layers.max\_pooling2d(inputs=conv2, pool\_size=\[2, 2\], strides=2) Step Six – The Dense Layer Next, the fully connected or dense layer is defined. We need the feature map to be flattened before it can be connected to the dense layer, and this is done using the reshape module, size 7\*7\*36. There are 1,764 neurons in the dense layer, and a ReLu function is added too. The dropout is set as 0.3, with 30% of the weights set as 0. Dropout only happens during training. In the cnn\_mode\_fn model, you can find an argument mode that lets you declare whether training or evaluation is required. pool2\_flat = tf.reshape(pool2, \[-1, 7 \* 7 \* 36\])  
dense = tf.layers.dense(inputs=pool2\_flat, units=7 \* 7 \* 36, activation=tf.nn.ReLu)  
dropout = tf.layers.dropout(  
      inputs=dense, rate=0.3, training=mode == tf.estimator.ModeKeys.TRAIN) Step Seven – The Logit Layer Lastly, the logit layer is defined with the model prediction, and the shape of the output is equal to the size of the batch and to 10, the number of images. \# Logits Layer  
logits = tf.layers.dense(inputs=dropout, units=10)       A dictionary can be created with the classes and the class probability. The tf-argmax() module returns the logit layer’s highest value and the class probabilities are returned by the SoftMax function. predictions = {                            
        # Generate predictions                            
    "classes": tf.argmax(input=logits, axis=1),                           
    "probabilities": tf.nn.softmax(logits, name="softmax\_tensor")  }                 The dictionary prediction should be returned only when the mode has been set as prediction and the following code will display them:   if mode == tf.estimator.ModeKeys.PREDICT:  
    return tf.estimator.EstimatorSpec(mode=mode, predictions=predictions)  
  Next, the model loss must be computed. We already know that we can use the cross-entropy loss function, and the following code will calculate the loss: \# Calculate Loss (for both TRAIN and EVAL modes)  
loss = tf.losses.sparse\_softmax\_cross\_entropy(labels=labels,  logits=logits) Lastly, the model must be optimized to find the best weight values. The gradient descent optimizer is useful for that, with a 0.1 learning rate, to try to minimize the loss. optimizer = tf.train.GradientDescentOptimizer(learning\_rate=0.001)  
train\_op = optimizer.minimize(  
        loss=loss,  
        global\_step=tf.train.get\_global\_step()) The CNN is finished, but we want the performance metrics displayed during evaluation. This is the accuracy of the model, and there is a module in TensorFlow called accuracy that can help us – it contains a pair of arguments, labels, and the predicted values. eval\_metric\_ops = {  
      "accuracy": tf.metrics.accuracy(labels=labels, predictions=predictions\["classes"\])}  
return tf.estimator.EstimatorSpec(mode=mode, loss=loss, eval\_metric\_ops=eval\_metric\_ops)  
  That is the CNN finished, and we can now pull it all together in a function to do the training and evaluation. def cnn\_model\_fn(features, labels, mode):  
  """Model function for CNN."""  
  # Input Layer  
  input\_layer = tf.reshape(features\["x"\], \[-1, 28, 28, 1\])  
\# Convolutional Layer  
  conv1 = tf.layers.conv2d(  
      inputs=input\_layer,  
      filters=32,  
      kernel\_size=\[5, 5\],  
       padding="same",  
      activation=tf.nn.ReLu)  
\# Pooling Layer  
  pool1 = tf.layers.max\_pooling2d(inputs=conv1, pool\_size=\[2, 2\], strides=2)  
\# Convolutional Layer #2 and Pooling Layer  
  conv2 = tf.layers.conv2d(  
      inputs=pool1,  
      filters=36,  
      kernel\_size=\[5, 5\],  
      padding="same",  
      activation=tf.nn.ReLu)  
  pool2 = tf.layers.max\_pooling2d(inputs=conv2, pool\_size=\[2, 2\], strides=2)  
\# Dense Layer  
  pool2\_flat = tf.reshape(pool2, \[-1, 7 \* 7 \* 36\])  
  dense = tf.layers.dense(inputs=pool2\_flat, units=7 \* 7 \* 36, activation=tf.nn.ReLu)  
  dropout = tf.layers.dropout(  
      inputs=dense, rate=0.4, training=mode == tf.estimator.ModeKeys.TRAIN)  
\# Logits Layer  
  logits = tf.layers.dense(inputs=dropout, units=10)  
predictions = {  
      # Generate predictions (for PREDICT and EVAL mode)  
      "classes": tf.argmax(input=logits, axis=1),  
      "probabilities": tf.nn.softmax(logits, name="softmax\_tensor")  
  }  
if mode == tf.estimator.ModeKeys.PREDICT:  
    return tf.estimator.EstimatorSpec(mode=mode, predictions=predictions)  
\# Calculate Loss  
  loss = tf.losses.sparse\_softmax\_cross\_entropy(labels=labels, logits=logits)  
\# Configure the Training Op (for TRAIN mode)  
  if mode == tf.estimator.ModeKeys.TRAIN:  
    optimizer = tf.train.GradientDescentOptimizer(learning\_rate=0.001)  
    train\_op = optimizer.minimize(  
        loss=loss,  
        global\_step=tf.train.get\_global\_step())  
    return tf.estimator.EstimatorSpec(mode=mode, loss=loss, train\_op=train\_op)  
\# Add evaluation metrics Evaluation mode  
  eval\_metric\_ops = {  
      "accuracy": tf.metrics.accuracy(  
          labels=labels, predictions=predictions\["classes"\])}  
  return tf.estimator.EstimatorSpec(  
      mode=mode, loss=loss, eval\_metric\_ops=eval\_metric\_ops)  
   Next, we use the CNN model to define the estimator: \# Create the Estimator  
mnist\_classifier = tf.estimator.Estimator(  
    model\_fn=cnn\_model\_fn, model\_dir="train/mnist\_convnet\_model") CNNs can take multiple iterations to train them so we need a Logging hook; this stores the SoftMax layer values after each set of 50  iterations. \# Set up logging for predictions  
tensors\_to\_log = {"probabilities": "softmax\_tensor"}  
logging\_hook = tf.train.LoggingTensorHook(tensors=tensors\_to\_log, every\_n\_iter=50) The model can now be estimated. The batch size is set to 100, and the data is shuffled. The training steps are set to 16.000; now you need some patience as this may take a while: \# Train the model  
train\_input\_fn = tf.estimator.inputs.numpy\_input\_fn(  
    x={"x": X\_train\_scaled},  
    y=y\_train,  
    batch\_size=100,  
    num\_epochs=None,  
    shuffle=True)  
mnist\_classifier.train(  
    input\_fn=train\_input\_fn,  
    steps=16000,  
    hooks=\[logging\_hook\]) Once the training is completed, we can evaluate the model and print out the results: \# Evaluate model and print results  
eval\_input\_fn = tf.estimator.inputs.numpy\_input\_fn(  
    x={"x": X\_test\_scaled},  
    y=y\_test,  
    num\_epochs=1,  
    shuffle=False)  
eval\_results = mnist\_classifier.evaluate(input\_fn=eval\_input\_fn)  
print(eval\_results)  
  INFO:tensorflow:Calling model\_fn.  
INFO:tensorflow:Done calling model\_fn.  
INFO:tensorflow:Starting evaluation at 2018-08-05-12:52:41  
INFO:tensorflow:Graph was finalized.  
INFO:tensorflow:Restoring parameters from train/mnist\_convnet\_model/model.ckpt-15652  
INFO:tensorflow:Running local\_init\_op.  
INFO:tensorflow:Done running local\_init\_op.  
INFO:tensorflow:Finished evaluation at 2018-08-05-12:52:56  
INFO:tensorflow:Saving dict for global step 15652: accuracy = 0.9589286, global\_step = 15652, loss = 0.13894269  
{'accuracy': 0.9689286, 'loss': 0.13894269, 'global\_step': 15652} This CNN architecture will provide a 97% accuracy. Changing the architecture, playing around with batch size, and iteration number may improve accuracy. In our final chapter, we will take a look at autoencoders with TensorFlow. 

Chapter 15 Autoencoders with TensorFlow ![](image_rsrc9SG.jpg)Autoencoders are the best tools for recreating inputs. The machine will take an input – an image, for example – and it will produce something closely related. This is classed as an unlabeled input, which means the network makes use of unsupervised learning. To be more precise, the network encodes the input, focusing only on the feature that is the most critical. This is why autoencoders are great for dimensionality reduction. Typically, autoencoders are defined with: 

*   Input 
*   Internal representation 
*   Output 

The layers are in two primary blocks, looking much like a standard neural network. There is a small difference in that the layer where the output is, and the input must be equal. The first block is called the encoder, and the original input is passed into it. The input is then compressed or reduced by the internal representation, and, in the second block, the input is reconstructed in a phase known as decoding. The loss function is minimized, so the weights are updated, but if the output (reconstructed) is not the same as the input, the model will be penalized. Let’s say that we have a size 50x50 image – it has 250 pixels. We also have a neural network that has a single hidden layer containing 100 neurons. The feature map, where the learning is done, is smaller than the input image by two times, meaning the network must now reconstruct those 250 pixels with just a single  neuron vector that equals 100. Building a Stacked Autoencoder Using TensorFlow We are going to build a stacked autoencoder. You will find it is similar in architecture to a standard neural network – the input is pushed into a hidden layer so its size can be reduced, before going for reconstruction. We want an output that is as near as possible to the input, and the model needs to learn how to do this while working with a lower dimension. We are going to use the CIFAR-0 dataset. It has 60,000 images, each 32x32, and the dataset has already been divided for us, with 50,000 images in the training dataset and 10,000 for testing. There can be a maximum of ten classes: 

*   Airplane 
*   Automobile 
*   Bird 
*   Cat 
*   Deer 
*   Dog 
*   Frog 
*   Horse 
*   Ship 
*   Truck 

The images may be downloaded from [https://www.cs.toronto.edu/~kriz/cifar.html](https://www.cs.toronto.edu/~kriz/cifar.html) . Unzip the images. You will find a folder called for-10-batches-py; this contains five batches, each with 10,000 randomly ordered images. Preprocessing the Images Step One – Importing the Data The official website tells us that we can use the following code for uploading the data. The code will go to a dictionary with the label and the data – this code is actually a function: import numpy as np  
import tensorflow as tf  
import pickle  
def unpickle(file):  
    import pickle  
    with open(file, 'rb') as fo:  
        dict = pickle.load(fo, encoding='latin1')  
    return dict Step Two – Converting the Data To keep things simple, we will convert the data to a black and white (grayscale) format, so it has just one dimension (the color images have three). def grayscale(im):  
    return im.reshape(im.shape\[0\], 3, 32, 32).mean(1).reshape(im.shape\[0\], -1) Step Three – Appending the Batches We have now created our functions and loaded the dataset. Now, a loop is required to append all the data into memory. The unzip file containing the data is called data\_batch> and is numbered one through five – these files can be looped over to append them. Once this is done, the color's data is converted to grayscale. The data shape is 50000 and 1024; flattening reduces the 32x32 pixels to  2014. \# Load data into memory  
data, labels = \[\], \[\]  
\## Loop over the b  
for i in range(1, 6):  
    filename = './cifar-10-batches-py/data\_batch\_' + str(i)  
    open\_data = unpickle(filename)  
    if len(data) > 0:  
        data = np.vstack((data, open\_data\['data'\]))  
        labels = np.hstack((labels, open\_data\['labels'\]))  
    else:  
        data = open\_data\['data'\]  
        labels = open\_data\['labels'\]  
data = grayscale(data)  
x = np.matrix(data)  
y = np.array(labels)  
print(x.shape)  
(50000, 1024) Step Four – Constructing the Training Set We want our training to be fast and easy, so we are only going to use the bird images. These are the third class, and there are 5,000 images in each class. The data shape can be printed to confirm that the class has 5,000 images and 1,024 columns: bird\_i = np.where(y == 3)\[0\]  
bird\_x = x\[bird\_i\]  
print(np.shape(bird\_x))  
(5000, 1024) Step Five – Constructing the Image Visualizer Lastly, we can plot those images by constructing the function that is required for the reconstructed image to be printed. The easiest way to do this is to use a Matplotlib library object called imshow. The data shape must be converted; it is 1,024, and it needs to be 32\*32, which is an image shape: \# To plot nice figures  
%matplotlib inline  
import matplotlib  
import matplotlib.pyplot as plt  
def plot\_image(image, shape=\[32, 32\], cmap = "Greys\_r"):  
    plt.imshow(image.reshape(shape), cmap=cmap,interpolation="nearest")  
    plt.axis("off")   There are three arguments in the function: 

*   The input, which is the image 
*   The shape, which is a list and the image dimension 
*   Cmap, where we choose the color map, gray by default. 

Try plotting the first dataset image: plot\_image(bird\_x\[1\], shape=\[32, 32\], cmap = "Greys\_r")         Step Six – Setting the Dataset Estimator Our dataset is now ready, so we can start using TensorFlow. Before the model is built, we need to feed our network using the TensorFlow dataset estimator. This is done sing from\_tensor\_sliced, repeat, and batch. Here’s the full code: dataset = tf.data.Dataset.from\_tensor\_slices(x).repeat().batch(batch\_size)           The placeholder, x, has this shape: 

*   \[None, n\_inputs\] – this is set as None because we have an equal size of image feed and batch size 

Next, we need an iterator; if we don’t have this code, nine of the data can go into the pipeline: iter = dataset.make\_initializable\_iterator() # create the iterator features = iter.get\_next()             Our pipeline is now ready, so let’s see if the initial image is as it was before. The batch size is set as 1 because only one image is being fed to the network. The data dimension can be seen using print(sess.run(features).shape) and it equals (1, 1024). This means that one image with a size of 1024 is fed. If we had the batch size set to 2, then there would be two images fed to the pipeline. It is important that you leave the batch as size 1; otherwise, an error will be thrown – the plot\_image() function can take only one image at any one time. \## Parameters  
n\_inputs = 32 \* 32  
BATCH\_SIZE = 1  
batch\_size = tf.placeholder(tf.int64)  
\# using placeholder  
x = tf.placeholder(tf.float32, shape=\[None,n\_inputs\])  
\## Dataset  
dataset = tf.data.Dataset.from\_tensor\_slices(x).repeat().batch(batch\_size)  
iter = dataset.make\_initializable\_iterator() # create the iterator  
features = iter.get\_next()  
\## Print image  
 with tf.Session() as sess:  
    # feed the placeholder with data  
    sess.run(iter.initializer, feed\_dict={x: bird\_x,  
                                         batch\_size: BATCH\_SIZE})  
    print(sess.run(features).shape)  
    plot\_image(sess.run(features), shape=\[32, 32\], cmap = "Greys\_r")  
(1, 1024) Building the Network We now come to building our network, and we will be training a stacked autoencoder. There will be one input layer in the network with 1024 points – the image shape of 32\*32. In the encoder block, there is a single hidden layer at the top, containing 300 neurons. There is also a layer in the middle, containing 150 neurons, and the decoder block and encoder are symmetric. The central and hidden layer values can be changed. Constructing an autoencoder is not much different from constructing any deep learning model. We learned earlier how a pipeline is created so the model can be fed – that means we don’t need to create the dataset again. We will build an autoencoder using four layers. We will be using a technique called the Xavier initialization; this allows us to set the weights as equal to the input and output variance. Lastly, ReLu is used, and an L2 regularizer ensures the loss function is regularized. Step One – Parameter Definition This is where we define how many neurons each layer holds, what the learning rate is, and the regularizer’s hyperparameter. Before we  do that, the function is partially imported. This is a better way of defining the dense layer parameters. The following code is the definition of the autoencoder architecture values. There are two layers – 300 neurons and 150 neurons, respectively – and n\_hidden\_1 and n\_hidden\_2 are where the values are stored. The learning rate must be defined, with the value stored in learning\_rate; we also define the L2 hyperparameter, storing the value in l2\_reg from functools import partial  
\## Encoder  
n\_hidden\_1 = 300  
n\_hidden\_2 = 150  # codings  
\## Decoder  
n\_hidden\_3 = n\_hidden\_1  
n\_outputs = n\_inputs  
learning\_rate = 0.01  
l2\_reg = 0.0001 We use the xavier\_initializer object to call Xavier initialization from the contrib estimator. We can also use l2\_regularizer to add the regularizer into the same estimator \## Define Xavier initialization  
xav\_init =  tf.contrib.layers.xavier\_initializer()  
\## Define L2 regularizer  
l2\_regularizer = tf.contrib.layers.l2\_regularizer(l2\_reg) Step Two – Defining the Layers We have now set all the dese layer parameters. Everything can be packed up into the dense\_layer variable using the partial. dense\_layer object; this uses ELU activation, L2 regularization, and the Xavier initialization. \## Create dense layer  
dense\_layer = partial(tf.layers.dense,  
                         activation=tf.nn.elu,  
                         kernel\_initializer=xav\_init,  
                         kernel\_regularizer=l2\_regularizer) Step Three – Defining the Architecture You can see from the architecture that there are three layers stacked by the network, with an output layer. In the next code, the right layers are connected: 

*   Layer one – the dot product is computed between the matrices features for the input and the matrices that have 300 neurons/weights. 
*   ELU Activation – once the computation has been done, the output is given to the ELU 

Each layer output is given to the next layer as an input, which is why it is used for computing hidden\_2, etc. Each layer has the same matrices multiplication because the same activation function is used. There is no activation function applied in the final outputs layer because this is the reconstruction of the input. \## Make mat mul  
hidden\_1 = dense\_layer(features, n\_hidden\_1)  
hidden\_2 = dense\_layer(hidden\_1, n\_hidden\_2)  
hidden\_3 = dense\_layer(hidden\_2, n\_hidden\_3)  
outputs = dense\_layer(hidden\_3, n\_outputs, activation=None) Step Four – Defining the Optimization Finally, we need our optimizer constructed. The MSE loss function is used – remember; we use the difference between the real label and the predicted output for the MSE computation. Our model is trying to reconstruct the input, so the feature is the label. As such, we want the mean sum of the squared difference between the input and the predicted output. Using TensorFlow, the loss function is coded like this loss = tf.reduce\_mean(tf.square(outputs - features))       Next, the loss function must be optimized, with the gradients computed using the Adam optimizer – the objective is loss minimization      \## Optimize  
loss = tf.reduce\_mean(tf.square(outputs - features))  
optimizer = tf.train.AdamOptimizer(learning\_rate)  
train  = optimizer.minimize(loss) Before the model can be trained, we need to do one more thing – set the batch size to 150. That way, 150 images are sent through the pipeline on every iteration, and those iterations must be manually computed. BATCH\_SIZE = 150  
\### Number of batches :  length dataset / batch size  
n\_batches = bird\_x.shape\[0\] // BATCH\_SIZE  
print(n\_batches)  
33 Step Five – Running our Model Finally, the model is trained with 100 epochs. You already know how a model is trained in TensorFlow; there is a small difference here in that the data is piped before the training is run – this enables faster training. We want the loss printed at the end of 10 epochs so  we can see if our model is learning; depending on your computer hardware, training can take up to five minutes \## Set params  
n\_epochs = 100  
\## Call Saver to save model and use it again during evaluation  
saver = tf.train.Saver()  
with tf.Session() as sess:  
    sess.run(tf.global\_variables\_initializer())  
    # initialize iterator with train data  
    sess.run(iter.initializer, feed\_dict={x: bird\_x,  
                                          batch\_size: BATCH\_SIZE})  
    print('Training...')  
    print(sess.run(features).shape)  
    for epoch in range(n\_epochs):         
        for iteration in range(n\_batches):  
            sess.run(train)  
        if epoch % 10 == 0:  
            loss\_train = loss.eval()   # not shown  
            print("\\r{}".format(epoch), "Train MSE:", loss\_train)  
        #saver.save(sess, "./my\_model\_all\_layers.ckpt")  
    save\_path = saver.save(sess, "./model.ckpt")      
    print("Model saved in path: %s" % save\_path)    
Training...  
(150, 1024)  
0 Train MSE: 2934.455  
10 Train MSE: 1672.676  
20 Train MSE: 1514.709  
30 Train MSE: 1404.3118  
40 Train MSE: 1425.058  
50 Train MSE: 1479.0631  
60 Train MSE: 1609.5259  
70 Train MSE: 1482.3223  
 80 Train MSE: 1445.7035  
90 Train MSE: 1453.8597  
Model saved in path: ./model.ckpt Step Six – Evaluating the Model Our model is trained, now we can evaluate it. To do this, test sert needs to be imported from the /cifar-10-batches-py/ file test\_data = unpickle('./cifar-10-batches-py/test\_batch')  
test\_x = grayscale(test\_data\['data'\])  
#test\_labels = np.array(test\_data\['labels'\]) On Windows, the code is: test\_data = unpickle(r"E:\\cifar-10-batches-py\\test\_batch") Try printing the image, number 13: plot\_image(test\_x\[13\], shape=\[32, 32\], cmap = "Greys\_r")         Evaluating the model requires that we use this image’s pixel value to check if the same image can be reconstructed after 1024 pixels are shrunk. We need a function defined for model evaluation on different images, and the function has two arguments: 

*   df – this imports the test data 
*   image\_number – defines which image is to be imported 

We divide the function into three: 

*   getting the image reshaped to the right dimension – 1024 
*   the unseen image is fed to the model, and the image is encoded and decoded 
*   the constructed and real image is printed 

def reconstruct\_image(df, image\_number = 1):  
     ## Part 1: Reshape image to the right dimension i.e 1, 1024  
    x\_test = df\[image\_number\]  
    x\_test\_1 = x\_test.reshape((1, 32\*32))  
     \## Part 2: Feed model with unseen image, encode and decode the image  
    with tf.Session() as sess:       
        sess.run(tf.global\_variables\_initializer())  
        sess.run(iter.initializer, feed\_dict={x: x\_test\_1,  
                                      batch\_size: 1})  
    ## Part 3:  Print real and reconstructed image  
      # Restore variables from disk.  
        saver.restore(sess, "./model.ckpt")    
        print("Model restored.")  
      # Reconstruct image  
        outputs\_val = outputs.eval()  
        print(outputs\_val.shape)  
        fig = plt.figure()  
      # Plot real  
        ax1 = fig.add\_subplot(121)  
        plot\_image(x\_test\_1, shape=\[32, 32\], cmap = "Greys\_r")  
      # Plot estimated  
        ax2 = fig.add\_subplot(122)  
        plot\_image(outputs\_val, shape=\[32, 32\], cmap = "Greys\_r")  
        plt.tight\_layout()  
        fig = plt.gcf() The evaluation function has been defined so now we can see the reconstructed version of image 13 reconstruct\_image(df =test\_x, image\_number = 13)         INFO:tensorflow:Restoring parameters from ./model.ckpt  
Model restored.  
(1, 1024) That concludes both our tutorial on using TensorFlow to build a stacked encoder and, sadly, this book. 

Conclusion ![](image_rsrc9SG.jpg)Thank you for taking the time to read my guide. I hope you now have a better understanding of how important TensorFlow is in machine and deep learning. This is by no means an in-depth guide, but it is an excellent basis for you to improve your learning. From here, you can go further in-depth into each of the topics covered and cement your learning into something concrete. I also gave you an overview of NumPy, Pandas, and Scikit-Learn. Now, you might wonder why I did this when this book is meant to be about TensorFlow. Although all of them are very different libraries and frameworks, as you have seen, they are all used in conjunction with one another to provide you with a full picture of your model. To learn TensorFlow means you need to have some understanding of the other libraries, and that is what I have tried to provide you here. I want to wish you luck in your data science journey and hope that I have given you a good grounding in TensorFlow as a springboard to go further. 

References ![](image_rsrc9SG.jpg)[https://www.tensorflow.org/](https://www.tensorflow.org/) [https://www.infoworld.com/](https://www.infoworld.com/) [https://machinelearningmastery.com/](https://machinelearningmastery.com/) [https://hackernoon.com/](https://hackernoon.com/) [https://www.zendesk.com/](https://www.zendesk.com/) [https://stackabuse.com/](https://stackabuse.com/) [https://www.guru99.com/](https://www.guru99.com/) [https://medium.com/](https://medium.com/) [https://www.datacamp.com/](https://www.datacamp.com/) [https://towardsdatascience.com/](https://towardsdatascience.com/) [https://www.geeksforgeeks.org/](https://www.geeksforgeeks.org/) [https://numpy.org/](https://numpy.org/) [https://pandas.pydata.org/](https://pandas.pydata.org/) [https://scikit-learn.org/stable/](https://scikit-learn.org/stable/) [https://adventuresinmachinelearning.com/](https://adventuresinmachinelearning.com/) [https://www.sciencedirect.com/](https://www.sciencedirect.com/) [https://missinglink.ai/](https://missinglink.ai/) 

TensorFlow  
Machine Learning ![](image_rsrc9SG.jpg)Simple and Effective Tips and Tricks to Learn Machine Learning with Scikit-Learn, Keras and Tensorflow ![](image_rsrc9SF.jpg)Benjamin Smith 

Introduction ![](image_rsrc9SG.jpg)There’s no denying that machine learning is the upcoming talk of the century in mankind’s journey with computers. Conventionally, computers were seen as instruments that need to be told specifically what to do. The notion of training the computer and making it learn certain patterns that allow it to make decisions on its own would be categorized as science-fiction in the previous decade. Although the struggle to create intelligent and self-functioning computers that can understand and distinguish data was already underway in the dawn of the 2nd millennium, the efforts were not as effective. This was due to the lack of computational resources and the infancy of the very field itself. Looking back, innovations in machine-learning were mostly coincidences. In a few cases, bright minds paved the way for machine-learning to prosper by pouring their genius intellect into exploring the secrets that lied in the mathematical aspect of computers. Now, the influence of machine-learning has become undeniable. We are seeing self-driving cars implementing the concept of machine learning in unison with artificial intelligence. We are building intelligent systems that can scavenge through insurmountable data and produce results that would otherwise be impossible. We are seeing machine-learning being implemented as a core feature in all smart appliances and voice assistants. This is only the beginning of a new age. Being one of the people that pioneered this revolution in human life is something that only comes once in every lifetime. As such, the popularity of learning machine learning and being adept at it has become a very sought after goal and this book will honor this goal. 

Chapter 1 Introduction to Machine Learning ![](image_rsrc9SG.jpg)Machine Learning, what was thought to be an innovation worth a hundred years of progress a few years ago, has already been achieved by mankind in the contemporary era. Optical Character Recognition (OCR) has been one of the many useful products of this innovation has provided us. The first of its uses, quite common now, appeared back in the 90s: the spam filter. Other numerous examples of ML which are working right now in every smartphone and any computer are: 

*   Voice searches 
*   Recommendation mechanisms 

This subject stands to explore the uniqueness of this innovation. It has made us question the very basics of learning. Does saving a file in your computer with philosophical contents make it wonder about the truths of life? Will saving a copy of the Critique of pure reason make it explore the valleys of moral ethics? And the most crucial question of all, does the data saved into the computer make it a more learned entity than before? In this chapter, the primary theme will be exploring the wonderful world of Machine Learning and the intricacies involved in incorporating machine learning in the program design. Furthermore we will look at the advantages of using machine learning. We will look at some important areas and parts that are important to understand the workings of ML. For instance, the different categories of machine learning software based on how they learn i.e. unsupervised or supervised, instance-based vs. model-based, etc. Following this brief introduction, we will observe the model of a machine learning software and observe how it  functions while also paying attention to the main impediments of the process, and look at the solutions of solving such problems.  We will learn how to judge and evaluate a model and the methods to fine-tune a Machine Learning system. Besides, we will also go through the important techniques and practices that essentially allow us to, not only assess and appraise a machine learning model, but we will also learn the way to improve the model effectively. To work on Machine Learning or by using it, a data scientist should know the technical terms and jargon of the model and the terms used in ML, and this is what we will focus on in the first chapter. It will be kind of a comprehensive overview, but it will stand as a foundation stone for building on in the entire chapters after this. What Is Machine Learning? Programming computers so that they can learn from data that is fed to them is commonly accepted as Machine Learning. In the year 1959, Arthur Michel defined machine learning as “The field of study that gives computers the ability to learn without being explicitly programmed” (Arthur Michel, 1959). One of the most simple and arguably widely used programs that incorporate machine learning is a ‘Spam Filter.’ This program checks the incoming emails in the user’s inbox and automatically filters out the ones that look like spam. Let’s understand this working in a more detailed manner. Machine learning programs have special algorithms that are taught to identify patterns through training. For this reason, we need to make the algorithm of the spam filter program become familiar with patterns of a typical spam mail. To do this, we will have to train the algorithm by giving it data (that corresponds to the emails that have been marked as spammed by users) and highlighting the characteristics of a standard spam mail. The data that we are providing to the program through which it will learn a specific pattern is known as the ‘training set.’ In this case, the examples of spam mail we are using to train the program will be collectively referred to as the training set. A common phrase you  will come across through the upcoming chapters of this book is ‘Training Instance”. This phrase refers to a single ‘entity’ within the training set, for instance, in the data of spam email examples, each ‘example’ is also known as a ‘training instance.’ So, the main goal of this program’s algorithm is to identify those emails that are most likely spam. This will be done by leveraging the pattern the algorithm learned during training. Also, the algorithm will consider the characteristics defined by the user as well. To improve the performance of the program, we can optionally tune some hyperparameters (but that’s an advanced task). To evaluate the performance of the program, we can do so by taking a look at the performance measures (such as accuracy, precision, recall, etc.). However, we need to carefully pick out the appropriate performance measured depending on the nature of the task. We will talk in more detail about the accuracy, precision, and recall in the 3rd chapter. For now, since we are dealing with a classification task (classifying emails as ‘spam’ or ‘not spam’), the performance measure we should be using is ‘accuracy.’ From here, we can gather how well the model performance with regards to the accuracy of its predictions, in response, we will have the ability to either tune the algorithm and hyperparameters if the accuracy is unsatisfactory. The lesson to learn from here is that downloading data onto the computer doesn’t necessarily mean that it will change the overall capabilities of the machine itself. Simply storing a philosophical book on a computer will give it the ability to debate with the user on such topics. Hence, storing data has no relation to the functionalities of a computer. We need first to design a program that can leverage this stored data and produce a useful output. In other words, if you just download a copy of the ‘Critique of pure reason,’ the machine indeed holds more data than before. However, the computer will not be blessed with the ability to debate the contradictions of categorical imperatives out of nowhere. Thus, it will make it store more data but not make it smarter than it was  before. Reasons to Use Machine Learning Let’s observe the programming approach traditionally taken to create a simple bot incorporating machine learning so that it can filter through spam mail: 

1.  First, we need to have an idea of the structural arrangement of a standard spam email (in most cases, spam emails share many similarities). For example, a common trait among spam emails is that \[there are certain distinct words and phrases that pop up in the email’s subject line. One of the most common examples of such phrases is ‘absolutely free, no credit card, limited-time offer, etc. Other than these linguistic cues, once you go through a bunch of spam emails by yourself, you will come to notice a distinct pattern of words being used in the body of the email. In this way, you can set up additional parameters that will consider these external factors as well, improving the accuracy of the program. 
2.  One of the most important elements of the spam filter is the algorithm being used. This algorithm is responsible for learning and familiarizing itself with the patterns of spam. Once the algorithm notices this pattern in an email, it will simply flag it as spam automatically. 
3.  Finally, we need to take the spam bot program out for a test drive. If the performance is lackluster and the spam detection functionality is not efficient enough, then we go back to the first two steps and improve it, not everybody can make a program, even if it’s simple. It incorporates machine learning extremely well so it’s okay to accept that program is lacking and work on improving it until it’s up to your standards. 

A spam filter learns which words and phrases are good clues for identifying the characteristic of ‘spam’ by detecting recurring patterns of words that are only observed in those emails that have  been labeled as ‘spam.’ The patterns of words and phrases observed in those emails not labeled as ‘spam’ are not considered by the program. Due to the usage of ML, the program tends to become relatively brief and easier to maintain (as compared to traditional programs) and generally far more accurate because of its self-learning processes and independent nature. When using a traditional program (let’s say a standard bot) that uses a standard detection algorithm, if the spammers start using words such as “night” instead of “9it”, then we would be forced to update the detection algorithms accordingly. This is because such traditional programs are based on a set of rules. So, if spammers notice that the target is using a traditional spam-bot program, then they can simply take advantage of the loopholes in the program’s structure and work their way around the detection algorithms. As such, you will be forced to keep updating the rules of your program every time the spammer figures out another loophole. However, if the same spam filter program were to use machine-learning, then there would be no hassle in tackling the annoying spam attacks that are updated frequently. Such a program that uses machine learning algorithms would automatically familiarize itself with the patterns and commonly used phrases and keep itself updated. All we would have to do is update the model’s training by providing it with new batches of data in which emails have been labeled as ‘spam,’ and it would learn the new patterns by itself. This approach is way more reliable and more convenient. When we are faced with a problem that is non-traditional or has no formulated algorithm, we turn towards the Machine Learning algorithms for solutions. For example, consider speech recognition as an example. You start by writing a program that can differentiate between the sounds of one and two. The word “two” begins with a high-pitch sound (“T”), so you can code an algorithm that calculates the intensity and pitch of the observed sounds and make use of the calculated measurements to distinguish between ‘ones’ and ‘twos.’ However, this program cannot hold a candle against complex data  which includes phrases from different languages and thousands of words, and every word spoken in an environment that has considerable background noise. What we do in such a case is to simply scavenge for examples of the words we are looking for in different environments so we can feed them to the algorithm for it to learn by itself and recognize the corresponding speech. Just as how we can see the progress bar of how much data we have downloaded as compared to the total size of the data we are downloading, we can also check the machine-learning algorithms and see how much they have learned so far. However, some algorithms are inherently complex and too advanced to the point where it becomes really tricky even to carry out such an inspection. For instance, once our program responsible for filtering spam emails has been trained on enough data, we can check out the list of words. Along with that, we check specific clusters of words that it has detected and accumulated over time to see which words are the best detectors of spam emails. In this manner, we, humans, can learn from ML. This inspection will reveal unsuspected correlations or undetected new trends which can help us form better performance measures for future algorithms. One such example that uses this technique is data mining, which incorporates ML algorithms to dig into enormous sets of data to detect the patterns mentioned above.  Examples of Machine Learning Following is a list that demonstrates the use of machine learning in specialized programs: 

*   Images of products on a production line being analyzed to classify them are called image classification, and this task is performed by using convolutional neural networks (CNNs). 
*   Semantic segmentation is used to detect tumors in the brain, to do this each pixel in the image is differentiated as our goal is to detect the exact location of the tumor along with its size, this task is performed using CNNs as well. 
*   Natural language processing (NLP) is used to classify news articles, more precisely known as text classification, this task is tackled by using CNNs, recurrent neural networks (RNNs) and Transformers. 
*   Discussion forums are often subject to abusive content and inappropriate content. These comments are automatically picked out, and this is text classification by using the same NLP tools. 
*   Very lengthy documents take up a lot of time when they are required to be sorted through. Natural Language Processing provides a tool which is known as ‘text summarization’ that automates this arduous task. 
*   A personal chatbot is created by incorporating different tools such as natural language understanding (NLU) and question-answering modules. Typically it answers all the queries in a short period when the actual authorities are not around. 
*   Big Corporations and Organizations can predict or gather a general idea of how well the company will perform in the coming term by using a machine learning regression model. Such a model specializes in generating predictions about values. Moreover, the model can be made unique considering the corporation or organization developing it by utilizing any of the regression types (for example, linear, polynomial, or even SVM regression). 
*   Speech recognition is used to make the applications react to voice commands. In order for the applications to work, audio samples are processed, and since such a type of data features lengthy and complex sequences, RNNs, CNNs, or Transformers are used to process them. 
*   Anomaly detection is used to alert the user upon any credit  card fraudulence. 
*   Clients are separated into segments based on their purchases so that we can formulate a separate marketing strategy for each category of clients. This segmentation on the basis of different client requirements is called ‘clustering.’ 
*   Data visualization is used in presenting a complex, high-dimensional dataset with clarity by an insightful diagram; it often involves dimensionality reduction techniques. 
*   A program can be developed that incorporates machine learning to consider the purchase history of a client and recommend products accordingly. To create a program that can perform such a task, we will need to procure the data of the client’s purchase history along with the purchase data of similar clients and use it to train the artificial neural network. Once the model has been adequately trained, it will be capable of predicting the purchase the client will most likely make when they visit the shop the next time. 

This list could go on, but the main point here is to demonstrate how broad the scope of machine learning is in the real world. Different Types of Machine Learning There are various types of machine learning available nowadays. The most popular types of machine learning along with their characteristics have been listed below: 

*   If a machine learning model is being overlooked by an external user (i.e., the tuning of hyperparameters, cycling through different activation functions to choose the best one, etc.) and the development and training of the model on labeled data is guided by the user as well. Such a model is categorized under a supervised learning system . 
*   If a machine learning model is not supervised by an external  user and the data on which the model is trained on is unlabeled. Such a machine learning model is categorized as an unsupervised learning system . Similarly, if the model is trained on a dataset that is partially labeled, then it is referred to as a semi-supervised learning system . A machine learning system that is conditioned to certain responses and then learns how to analyze its surrounding environment to determine the best course of action is categorized as a reinforced learning system . 
*   A machine learning system that can only be trained by feeding it complete batches of data is known as a batch learning system . On the other hand, a machine learning system that can be trained by using data instances (mini-batches) in sequences is known as an online learning system . 

You can apply these criteria in any way possible, and there are no steadfast rules about exclusively applying them. Supervised and Unsupervised Learning Systems that incorporate machine learning can be classified into different categories based on several factors. One such factor is the type of data (labeled or unlabeled) on which the model is being trained. Another factor is if the model’s training is being closely observed and managed by a user or not. In this section, we will discuss the major categories of machine learning based on the aforementioned factors: Supervised Learning Just as the name suggests, in supervised machine learning, we create a training set from a dataset we choose and train the model using it. The data within the training set is labeled. Labeled data means that within a particular dataset, all of the classes or data instances are marked as to what they actually represent. For instance, in the MNIST dataset (which we will soon discuss), the entire data  comprises instances of handwritten digits. If each of the data instances (handwritten digit) is labeled with the number they represent (a handwritten digit ‘3’ is explicitly labeled as ‘3’), then we say that the dataset is labeled. Supervised learning is most commonly seen in tasks that require the model to classify objects (also known as classification tasks). To keep things simple, let’s consider the example of the spam filtering program we discussed in the preceding sections. We can say that such a program incorporates the use of supervised learning. Not only do we train the model using labeled data (emails within the dataset have been categorized and marked as ‘spam’ and ‘not spam’) but the nature of the problem is essentially a ‘classification task’ as well (classifying emails as spam or not spam). Another task for which we use supervised learning is ‘Linear Regression.’ Unlike ‘Classification’ in which the model generates predictions regarding the correct class for a data instance, in ‘Linear Regression’ the model is required to generate predictions of values. In linear regression, we basically give the model a list that contains features about something and then train the model to predict a value according to the aforementioned features. For example, we can provide the model with a list of features such as total mileage, fuel capacity, engine type, and then ask the model to predict the value of the car based on these features. However, the process will still include training the model by using a training set that consists of both predictors (the list of features) and labels (the prices of the cars). We will talk about Linear regression more in the upcoming chapter. Whenever we talk in the context of Machine Learning, it is important to know the difference between an attribute and a feature. An attribute basically refers to the type assigned to a data (for instance, ‘mileage’ is data whose type is different from ‘engine type’ or even ‘fuel capacity’). In contrast, when any value accompanies an attribute, then it is referred to as a ‘feature’ (for instance, if we say  that ‘fuel capacity’ = 30L, then it is a feature). Algorithms are one of the most important components within a machine learning system. Each task requires a specific type of algorithm to be used for optimal performance, hence knowing about the different algorithms used in models is also important. Following is a list of some of the most commonly used algorithms used in supervised learning : •        k-Nearest Neighbors •        Linear Regression •        Logistic Regression •        Support Vector Machines (SVMs) •        Decision Trees and Random Forests •        Neural networks Unsupervised Learning Unsupervised learning is basically the opposite of supervised learning. Unlike its counterpart, in unsupervised learning, the data on which the model is being trained is unlabeled. This means that the data instances are not marked as to which class do each of them belongs to. Moreover, the model is not under the supervision of a user (hence the name, unsupervised learning). The following is a list of the most commonly used algorithms in unsupervised learning models: • Clustering ​ — K-Means ​ — Hierarchical Cluster Analysis (HCA) • Anomaly detection and novelty detection ​ — One-class SVM ​  — Isolation Forest • Visualization and dimensionality reduction ​ — Principal Component Analysis (PCA) ​ — Locally Linear Embedding (LLE) ​ — t-Distributed Stochastic Neighbor Embedding (t-SNE) • Association rule learning ​ — Apriori ​ — Eclat Let’s understand unsupervised learning with the help of an example. Let’s consider that we are running a blog that is quite popular, so much so that it generates consistent traffic of visitors. Since user traffic is always good for blogs, we can improve the reachability of our blog by identifying what our visitors search for before visiting this website. To do this, we will have to use some sort of algorithm that can identify the visitors and then classify them into categories based on how similar each visitor’s search query is. Such a task generally comes under the domain of unsupervised learning. Notice that if we were to create a model and train it on this anonymously collected data, it wouldn’t have labels and we won’t necessarily be supervising it either. Let’s say we do create such a model. To perform the required classification, we would need to use a ‘Clustering algorithm.’ When we implement this algorithm, we will not need to tell the algorithm that a certain visitor (data instance) belongs to this particular group (data class). The algorithm will learn the similarities in the visitor’s search queries and then categorize them accordingly all by itself. For instance, let’s say that through some clever trick, the algorithm concludes that about 70% of the visitors that come to the blog are women while the rest are men. Based on the time these visitors access the blog (recorded in the website’s traffic history), the algorithm concludes that the majority  of the viewers tend to visit the blog around evening during the weekdays while the rest tend to access the sci-fi portion of the blog only on weekends. Depending on the clustering algorithm used, the model can even incorporate this detail into the classification as well. For example, by using the HCA (Hierarchical Cluster Analysis) algorithm, the model will be capable of dividing the categories into sub-categories as well (if there’s enough information to allow it). In this way, we can identify the topics we need to discuss which will attract a large portion of our audience and boost the user traffic. Before we move on to the next topic, let’s briefly discuss Visualization and Dimensionality reduction algorithms. Visualization Algorithm Just as the name suggests, a visualization algorithm is generally concerned with graphically representing complex data in either two-dimensional plots or three-dimensional plots. For example, the Principle Component Analysis (PCA) algorithm is commonly used in unsupervised learning to represent unlabeled and complex data visually. Moreover, visualization algorithms prioritize the preservation of the data structure when it is visualized. The reason behind this is to allow for a much easier analysis of the visualized data and most importantly, enable the user to look for anomalies in the data patterns. Dimensionality Reduction Algorithms Just as how the PCA algorithm simplifies complex data, similarly, the main purpose of dimensionality reduction algorithms is to reduce the complexity of input data while prioritizing the preservation of the inherent information (keeping information loss to a   minimum). Generally, the way dimensionality algorithms simplify data is by merging the features that are somewhat related to each other together. In this way, the number of features is reduced. This means, the number of dimensions in the data is reduced. Let’s take a look at a simple example that we discussed in the section  of ‘Linear Regression’ as well. Let’s consider the following list of features according to which we need to predict the price of the car; these features will be: 

*   Fuel Capacity 
*   Mileage 
*   Period of use 
*   Date of Manufacturing 
*   The model’s popularity, etc. 

From these five features, we can see that a car’s mileage and the period of time for which it has been used prior to being sold are similar features. So if we apply a dimensionality reduction algorithm here, the ‘mileage’ and ‘period of use’ features will be merged into a single feature, hence reducing the original number of features. This process of feature merging is commonly referred to as ‘Feature extraction.’ Here's a cool tip. Consider that you created a model for classification or a linear regression task. Hence, it’s a given that you will be using supervised learning algorithms. However, if you apply the dimensionality reduction algorithm on the training set before you train the supervised learning algorithms, then you will improve upon the following aspects: 

*   The training speed will be improved. 
*   The memory and storage requirements of the dataset will be reduced. 
*   The overall performance of the model will also be improved. 

Semi-Supervised Learning Consider that you downloaded a dataset from any repository of your choice so that you can train your machine learning model. Unlike popular datasets (like the MNIST dataset), not many are completely  labeled, especially ones that are particularly large. Even if you scavenge through multiple repositories, you will only find a dataset that is partially labeled at best. Moreover, labeling data by yourself takes up too much time which you could spend tuning the model. Even if you hire a company or an organization to label it, the cost would be very high as well. In such cases where we are working with a partially labeled dataset, we can use specific algorithms. Such algorithms handle the labeled part of such datasets. This approach is known as semi-supervised learning . We can even see semi-supervised machine learning being applied in online services as well. Take Google Photos for instance. If we upload a family album on their server through the cloud, this means that the server is essentially being fed unseen and unlabeled data. Through machine learning, the server can identify that a particular person in a photo is showing up in other photos of the album as well. If we label this data instance (i.e., specify the name of the person) then the server can automatically label the rest of the photos in which this person appears as well. Reinforcement Learning Unlike the different types of machine learnings we have discussed so far, reinforcement learning is radically different. The system using reinforcement learning is known as the ‘Agent’ and the specialty of such a system is that it is capable of computing an appropriate action by observing its surroundings. If the agent chooses the correct response, then it is given a ‘reward.’ This reward can be easily programmed or it can be improvised depending on the choice of the developer. The distinctive feature of reinforcement learning is that the system tries to identify the most optimal strategy within a confined space. This means that the machine is given a specific environment with specific stimuli; the system carefully observes it’s surrounding and then develops an optimal strategy according to which it makes decisions. The strategy formulated by the machine is known as its ‘policy.’ The best examples which showcase the full potential of reinforcement learning are robots and AI bots. Majority of the robots that have been designed incorporate reinforcement learning in order to learn how to manipulate their limbs to enable them to walk. Similarly, AlphaGo, which is an AI bot designed to play the board game ‘Go.’ The bot incorporated reinforcement learning and was trained by allowing it to analyze large amounts of professional ‘Go’ matches. Once it was done with analyzing, it played the game with itself and in the end, it beat the board game’s world champion in an official match based on the policy it formulated on its own. Online and Batch Learning Batch Learning A model using batch learning does not allow data to be fed into the system in sequences or in the form of instances. The model is trained by using the entire dataset, i.e., the entire batch of data is fed to the system at once, hence the name ‘batch learning.’ Since the model is dealing with an entire dataset (for comparison, MNIST being a standard dataset consists of about 70 thousand images), the obvious consequence is that we cut back on the training speed. Since the training speed is slower than usual, batch learning is usually incorporated when want to train the model locally (offline). One drawback of batch learning is that the model will only be able to perform tasks for which it has been specifically trained for (i.e., it will only be able to perform actions that it already knows). It does not adapt or learn anymore unless it is trained again using the entire dataset; this means that if you have new data instances, then they will first have to be included in the original dataset and trained from scratch once again. Hence, batch learning is also referred to as ‘offline learning.’ However, the process of training, evaluation, and testing can be automated. So after the initialization of the model, you can simply automate these processes to be performed automatically and all you will need to do is simply load the dataset onto the model. Online Learning Online learning is simply the complete opposite of batch learning (also known as offline learning). In online learning, the model is provided with training data in sequences. This means that the model can be trained with separate data instances or a bunch of data instances (which are known as mini-batches). Since the quantity of training data is exponentially smaller as compared to batch learning, it is a given that the training speed of the model will be fast and produce less strain on the computational resources as well. In this way, the system can easily adapt whenever new data instances arrive. Online learning becomes a plausible option when we are dealing with data that has a continuous flow (for instance, stock market data has an uninterrupted flow). Our tasks require the model to adapt to the changes without too much delay. Moreover, if we are using a system that lacks behind others in terms of raw power, then the online learning system is a perfect choice since it is not that resource-hungry. Another good feature of online learning is that once it has been trained on new instances of data, the user can then delete these data instances from the system, hence saving storage space as well. In online learning, some algorithms are capable of handling large datasets as well. So if we have a dataset that does not fit our system’s main memory, then we can use online learning to train our model on this dataset. Training a model without using the system’s main memory is known as ‘out-of-core learning.’ The way online learning algorithms are capable of doing this is by simply loading mini-batches from the dataset and then training the model on this data for one epoch. Then the algorithm proceeds to load the next mini-batch of data and train the model. This process is repeated until the model has been trained on the entire dataset. Hindering Factors For Machine Learning When creating and developing a machine learning model, the most important contribution of the user is providing the model with the optimal algorithm as well as adequate data to train the model.  However, the creation and development of a machine learning model is essentially a process of trial and error. We simply cannot get everything right when developing a new machine learning model from the ground up on our first try. There’s always something that needs to be changed, tuned, or even re-designed. In this section, we will discuss two of the major factors that hinder the progress of a machine learning model: 

*   Bad data 
*   Bad Algorithms 

Here’s a list of some examples demonstrating the encounter of ‘bad data’ when dealing with machine-learning models. Insufficient Quantity Of Data In machine learning, nothing is as simple as showing it a picture of your favorite cat and then expecting the program to recognize a cat whenever it sees one. We are essentially teaching a machine that perceives the world as one-dimensional binary digits to recognize three-dimensional objects. For the computer to perform such tasks, it needs to be trained with a large amount of data. Since this is an important requirement in machine-learning, insufficient quantities of data are an example of ‘bad data’). Non-Representative Training Data For the machine learning model to generalize the patterns and other things it learned from the training data on unseen data (that the model has never come across), the model must be trained with data that somewhat represents the unseen data. We cannot train a model to recognize handwritten digits and then expect it to predict the price of houses in the upcoming years. If we want the model to recognize handwritten digits, then we must train with data that actually represents handwritten digits. To further elaborate, if we want to create a model that predicts the general happiness of the population for each country, then we need  to train it on data that represents the country’s status for which we expect the predictions. If the model is trained only on data that shows declining happiness and prosperity in 3rd world countries, then it won’t perform as we want to when we test it on data that requires it to predict the prosperity and happiness of developed countries. The training data does not represent the case we are testing the model on, and it is missing a lot of countries. Unless we include countries from every category (rich, moderately rich, and poor countries), the model will not generalize well because the training data is not truly representative of what we want it to work with. Poor Quality Data Just as how the name suggests, datasets that are lacking in quality are a prime example of ‘bad data’ that hinders the progress, development, and most importantly, the performance of the machine learning model. By poor quality, we basically mean a dataset that has: 

*   Common errors 
*   Outlying data instances (those instances that do not belong in any class within the dataset) 
*   Low clarity (commonly referred to as ‘noise’). 
*   Incomplete or Missing features 

These are some of the issues that can be commonly observed in poorly compiled datasets. The leading reason through which data has the aforementioned faults is the use of inaccurate measurements when recording the data. Using data that has poor quality will make it nearly impossible for the model to learn the proper patterns. In simpler terms, using a dataset that has poor quality will only lead to the model showcasing poor performance in the result as well. This is also one of the main reasons why data scientists allocate a  huge portion of their time improving the quality of the data and refining it; otherwise the rest of their efforts will be laid to waste. So, if you ever decide to create a machine learning model and have to look for a good dataset, you should always check it thoroughly to see if there aren’t any problems (especially the ones mentioned above). Let’s say that you notice that the dataset you have chosen has some outlying data instances. You can eliminate these instances themselves or if possible, you can fix these instances as well (whichever seems feasible at the time). Similarly, if you notice that there are data instances that are not accompanied by all of the instances they should have (for example a bunch of data instances in which the client has not mentioned their age), then you have several options. Firstly, you can choose to neglect the missing attribute (the specific feature) entirely. Secondly, you can choose to neglect these particular data instances and eliminate them from the dataset. Thirdly, you can specify the missing information by yourself (in this case, you would calculate the average age of the customer list and guess it). Finally, we can create two separate models, where one is trained with these erroneous instances and one where these incomplete instances have been omitted to see if there’s any noticeable difference in performance. Irrelevant Data It doesn’t require much thought to figure out that if we use data that is completely irrelevant to the task the model is supposed to perform, then the model will absolutely fail. If we train the model on the wrong dataset, then the model will be incapable of doing anything when faced with unseen data. It will not be able to see any relevance to the patterns it learned on the training set to the structure and type of data being presented in the testing phase or even in real-life applications. Hence, it is important to make sure that even if the dataset we are using is relevant to the model’s assigned task, it does not have any insignificant or unnecessary  features as well. Overfitting The Training Data To understand the concept of overfitting, we can relate it to ‘overgeneralizing.’ In overgeneralizing, we take an isolated observation and make a general assumption. For example, let’s consider a theoretical scenario where a person visits another city and since it’s his first time there, he asks a pedestrian for directions. Instead of responding to his request for guidance, the pedestrian scoffs and ignores him. After such an encounter, the person assumes that everybody in this city is as rude as this stranger. This is known as overgeneralization and the concept of ‘overfitting’ means the same for computers. If the user is not vigilant and experienced, the model can overfit on the training data. This means that the model will learn the patterns from the training set pretty well but when it comes to the testing set, the model will assume that the same pattern must hold true for the unseen data as well. In other words, the model fails to generalize well on unseen data even though its performance is satisfactory on the training data. Underfitting The Data From the name, it is obvious that underfitting is a phenomenon observed in machine learning that is the complete opposite of overfitting. When a machine learning model underfits on training data, this means that the structure of the data is just too plain for the model even to start detecting and learning any patterns. In other words, data on which the model is trained with is too unrealistic as compared to the problems that occur in the real world, in this way, the predictions generated by the model will always be inaccurate. For example, if we take the example of the happiness of the populations for different countries, the model trained on such data has a higher risk of underfitting. This is because the observations in the data do not accurately represent real life. Simply living in a rich country won’t necessarily make you happy. To reduce underfitting, we can do so by: 

*   Using a model that is comparatively more capable and boasts a wider range of premises. 
*   Using better and more refined features with the selected algorithm (this process is known as ‘feature engineering’). 
*   Using lesser constraints with the model, i.e., scaling down the use of regularizers and using lesser hyperparameters. 

Chapter 2 Perform Regression  
Tasks Using Scikit-Learn ![](image_rsrc9SG.jpg)In this chapter, we will be focusing our discussion towards creating a machine learning project to perform a standard regression task by utilizing the Scikit-Learn library. It is important to note that the nature of the task is similar to what a data scientist would focus on. Hence, to keep the discussion as realistic as possible, we will approach the project with the mindset of a data scientist as well. Don’t worry; we will only explore only those aspects of the projects that refer to data science, as discussing anything more would be out of the context of this book. In this chapter, our main focus will be to obtain a dataset that is up to the standards of the project, then analyzing the data in order to gain insights that will guide us through tuning and improving the performance of the model itself. Once we have explored the data and have obtained a satisfactory understanding of it, we will proceed to create a machine learning model and use appropriate algorithms to train it. Once the model has been trained, we will go through the standard practices to evaluate and test the model. With this, we will have a good idea of the areas in which the model is still lacking. In this way, we can tune and refine the model to bring it as close to perfection as possible. Gathering the Data As discussed in the previous chapter, using unrealistic data will only lead to unrealistic predictions and such results are practically useless in the real-world application of machine learning models. So, theoretical datasets are out of the question. However, procuring  datasets is not as difficult as one may think. The machine learning community has very useful repositories that feature datasets of good quality allowing for users to create projects by themselves or even help people practice so that they can improve their model-creating and developing skills. Here’s a list of some of the most common repositories that host datasets. If you’re looking for a specific dataset for your machine learning project, chances are you will find what you’re looking for on one of these domains: 

*   Reputable open data repositories : UC Irvine Machine Learning Repository, Kaggle Datasets, and Amazon’s AWS datasets. 
*   Meta Portals which redirect to other open data repositories : Data Portals, OpenDataMonitor, and Quandl. 
*   Websites that can direct you to various open data repositories : Wikipedia’s list of Machine Learning datasets, Quora, and The datasets subreddit. 

Since the major focus of this topic is linear regression, hence we will need to get a dataset that is relevant to this task. Otherwise, there will be no point creating a linear regression model while using a classification dataset. One of the most popular choices for Linear Regression tasks (where the model predicts values) which are also completely labeled is the California Housing Dataset. This dataset can be obtained from the StatLib repository. Although this dataset consists of the housing prices in California from the 90s, it has several qualities that make it more than suitable for training a linear regression model. For this project, we will ignore the date for which the data was recorded since it will not impact the performance of the model itself. Choosing a Regression Task There is a variety of regressions tasks to choose from. For instance,  you can choose to create a model to predict the pricing trends in the stock market. However, we will be choosing the California Housing price prediction task as the data can be easily acquired and it is error-free along with being completely labeled. The data covers the pricing for every block in the state of California (at that time) along with few extra metrics as well (for instance, average income and population). In the California Housing dataset, we can see that houses have been grouped into ‘blocks.’ This in accordance with the standard defined by the Census Bureau of the United States where each block (a geographical unit) consists of a population of anywhere between six hundred to three thousand civilians. To keep things simple and easy to understand, we will refer to ‘blocks’ as ‘districts’ as this is a more contextually accurate term to use. The goal of our machine learning model will be to predict the average price of housing for a particular district. Choosing the Appropriate Performance Measure One of the most important steps in creating a model is to select the most optimal performance measure for the task at hand. We will explore performance measures with more details and depth in the upcoming chapters. In this section, we will only discuss the characteristics of the popular performance measures used in supervised learning, these are: 

*   Root Mean Square Error (also known as RMSE) 
*   Mean Absolute Error (also known as MAE) 

Root Mean Square Error Once we have chosen the task we want the model to perform, (in this case it would be linear regression on the California Housing Dataset) the next plan of action is to pick a performance measure that suits our task. RMSE is a popular choice for models where we want to calculate the effectiveness of the model when it deals with regression problems. RMSE is important when creating linear regression models. If we do not implement any performance measure, then we won’t be able to have an idea of the overall errors the model makes when generating predictions. This will consequently snatch away the ability to pre-emptively tune model before we proceed any further as we will only know about the model’s lackluster performance when we actually test it and see that the predictions are somewhat off. RMSE calculates and displays the average error being made in the model’s predictions and depending on the size and significance of the error; it allocates them with corresponding weights. So an error with larger weight immediately signals the user that this error is pretty significant. Similarly, an error with a small weight will immediately let the user know that the error is not that significant. Although many regression tasks prefer the implementation of the Root Mean Square Error function as the performance measure, there are always cases where you need to make an exception, simply because some regression tasks might just prefer a different function entirely. Mean Absolute Error When you encounter such exceptional cases (such as districts within the data that are ‘outliers’) where using the RMSE function is not a viable option, the Mean Absolute Error function becomes the next best choice. Let’s try to understand the purpose of RMSE and MAE functions within a model. To keep it simple and easy to comprehend, the core concept of both RMSE and MAE functions is that they are a type of independent navigator. To elaborate, these functions calculate the direction of two particular vectors, the prediction vector, and the target value vector. Just as the name suggests, the prediction vector defines the pathway of the model’s predictions and the target vector defines the destination of the corresponding predictions. By  calculating their directions, the functions can tell us whether the model’s predictions are correct or incorrect based on the fact if the prediction vector converges with the target vector. The Mean Absolute Error is particularly useful for handling outlier data instances. For now, we will not dive any further into the performance measure functions as entire sections have been designated for this discussion only in the last two chapters. Getting Started with the Practical Work Once we have chosen the regression task we want the model to perform and the appropriate performance measure (either RMSE or MAE), it is finally time to start working on the project. Creating the Workspace First things first, we need to get every tool and every part into order and organize them accordingly. We absolutely do not want any distractions to hinder the work just because we forgot to download something. For any machine learning project, there are two essential tools that you must always have: 

*   Python IDE 
*   Jupyter Notebook 
*   NumPy 
*   Pandas 
*   Matplotlib 
*   Scikit-Learn 

The very first and basic requirement for any machine learning project is installing Python. By executing the commands shown below, we will be able to install Python on our system. Once we have python installed on our system, we will now proceed to create a  separate directory on the system’s storage where we will keep all the files that are necessary for our project. It is important to be as organized as possible because searching for something in the computer’s file directory will not only disrupt the tempo but it will also prove to be practically inefficient. $ export ML\_PATH="$HOME/ml" #   You can change the path if you prefer $ mkdir -p $ML\_PATH The most important tool is ‘Python.’ Python serves as the host for important machine learning modules such as NumPy, Pandas, the Matplotlib Library (Visually plots data into graphs), and the Scikit-Learn library. Jupyter notebook is a text editor where we can edit the python scripts and save them for later use. Regarding the Operating System, it is recommended to use popular distributions of Linux such as Ubuntu but you can also use MacOS or Windows as well. If you are using windows, then you can install a virtual environment and install Linux on that virtual box. However, for now, we will be working with this project with reference to the Linux Operating System as it offers more control and direct access to system functionality. There are several ways to install these tools on the system: 

*   Through the OS’s packaging system (for instance, using the apt-get command in Ubuntu). 
*   Through Anaconda (a scientific Python distro that provides its own packaging system. This method is recommended if you’re using windows). 
*   Through the native packaging system of Python (using the pip command). 

For now, we will be using the third method for installing these tools. Note that you might have to make small changes to the commands you are about to see depending on your system. The version of ‘pip’  depends on the version of Python installed. To double-check if ‘pip’ is currently installed on the system, we can do so by executing the following command: $ python3 -m pip --version pip 19.3.1 from \[...\]/lib/python3.7/site-packages/pip (python 3.7) Now that we know for sure that ‘pip’ is indeed installed and available to use on the system, we should check to see whether it’s the latest version or if it’s outdated. If you are indeed running an older version of the pip module, then you can upgrade it by executing the command shown below (this is the latest version of the pip module at the time of writing) : $ python3 -m pip install --user -U pip Collecting pip \[...\] Successfully installed pip-19.3.1 We are now equipped with the latest version of our preferred packaging system. After installing the latest version of the pip module, we can begin installing the rest of the tools and modules on the system as well so that we can proceed with the project. We can specify all the tools we want to install within a single command as shown below (pretty convenient) : $ python3 -m pip install -U jupyter matplotlib numpy pandas scipy scikit-learn Collecting jupyter Downloading https://\[...\]/jupyter-1.0.0-py2.py3-none-any.whl Collecting matplotlib \[...\] However, if you are using a virtual environment on your system for this project, then the first thing you need to do is provide the  necessary credentials of the virtual environment to the jupyter program. The reason why this is important is that you will not be able to proceed any further with the project when your system does not recognize the user accessing the administrator tools. The registration in jupyter can be done by executing the following command: $ python3 -m ipykernel install --user --name=python3 Now that this problem has been dealt with, you can now proceed to start up the jupyter program. To do so, you will have to enter a command into the system’s command line terminal: $ jupyter notebook \[...\] Serving notebooks from local directory: \[...\]/ml \[...\] The Jupyter Notebook is running at: \[...\] http://localhost:8888/?token=60995e108e44ac8d8865a\[...\] \[...\] or http://127.0.0.1:8889/?token=60995e108e44ac8d8865a\[...\] \[...\] Use Control-C to stop this server and shut down all kernels \[...\] The Jupyter notebook program is now running successfully. From the information provided when we executed the command, we can see that the program has initiated its server on your system’s terminal and is connected to the “port 8888”. The cool thing about this feature of the Jupyter notebook is that we can put the localhost website in our internet browser and we will be able to access the Jupyter server online as well. Now that Jupyter is fully functional, we can finally proceed to work on the actual project. In the Jupyter notebook window, look for the ‘New’ button and use it to create a separate python notebook file. Notice that whenever you create a new file in Jupyter, the program will ask you to specify the version of Python you want to use, in our case, we will be using Python 3. The default name of newly created  files is ‘Untitled.’ Once the python notebook file has been created, we put it into the separate directory we made for the project and then rename the notebook file to ‘Housing.’ If you have never used a Jupyter notebook, then it might be a good idea for you to learn the basics of how to use this program before proceeding any further. There’s an option in the Jupyter program help menu that will give the user a complete guide of the program features and how to use it. Download the Data Typically, when you work with linear regression datasets, the data is either in the form of tables, documents, or even files. Similarly, you will find that this data is stored in a database or any other form of data storage. This is because data scientists use software that can access the relational databases and process the data conveniently. However, to access the database, one would need to enter the appropriate credentials in order to authorize the access. In this project, things are not that complicated. To access and load the data onto our system for use, we simply need to download the required file (which will be compressed) on to our machine. The file we will need for this project is the ‘housing.tgz ’ compressed file. Once the file is downloaded, we need to decompress it. To do that, we can use any decompression software tool of our choice. Once the file has been decompressed, we will end up with a CSV file named ‘housing.csv.’ CSV files consist of data where the values are separated from each other through commas. We can also create a short python script that automates the process of downloading the dataset, decompressing, and extracting it. The following lines of code demonstrate how to do that: import os import tarfile import urllib DOWNLOAD\_ROOT =  "https://raw.githubusercontent.com/ageron/handson-ml2/master/" HOUSING\_PATH = os.path.join("datasets", "housing" ) HOUSING\_URL = DOWNLOAD\_ROOT + "datasets/housing/housing.tgz" def fetch\_housing\_data(housing\_url=HOUSING\_URL,     housing\_path=HOUSING\_PATH): os.makedirs(housing\_path, exist\_ok=True) tgz\_path = os.path.join(housing\_path, "housing.tgz") urllib.request.urlretrieve(housing\_url, tgz\_path) housing\_tgz = tarfile.open(tgz\_path) housing\_tgz.extractall(path=housing\_path) housing\_tgz.close() By using this script, we make the process of downloading the dataset more convenient and easy. Also, whenever we fetch the data (by using the fetch\_housing\_data() argument) a separate file directory will be generated within our workspace directory and the compressed file will be downloaded and put in this directory automatically. Once the file has been downloaded, the script will decompress and extract the housing.tgz file on its own as well, saving us the trouble of doing so. Now that we have the necessary data for the machine learning model, all that’s left to do is load it onto the system’s memory using the ‘Pandas’ tool we installed earlier. Just as how we used a script to download, decompress, and extract the compressed data file, we can also use a script to load the data using the Pandas tool as well: import pandas as pd def load\_housing\_data(housing\_path=HOUSING\_PATH): csv\_path = os.path.join(housing\_path, "housing.csv") return pd.read\_csv(csv\_path) Quickly Analyzing the Data Before we go any further, it’s always a good idea to quickly glance  over the structure of the data and understand how it’s organized. This practice will prove to be incredibly useful in other machine learning projects as there are times when we need to specify the data structure to the model and resize it according to the layers we are using. By using the head() method from DataFrame, we can display the data that is stored in tables within the California Housing dataset. The following figure demonstrates this: ![](image_rsrc9TD.jpg)In the figure shown above, we have only displayed the first five rows in the California Housing dataset. Within this table, each row (o to 4) represents a separate district (blocks). Moreover, by looking at the arrangement and features of the table, we can see that there are a total of ten attributes (the data’s features). These attributes are the following: 

*   California Housing Dataset Attributes: longitude, latitude, housing\_median\_age, total\_rooms, total\_bedrooms, population, households, median\_income, median\_house-value, ocean\_proximity . 

There are times when we do not want to observe data in tabular form. Instead, we prefer data to be shown in descriptive form. For such cases, we can use the info() method . This method returns a detailed description of the data which includes a summary of the features as well. For instance, when we use the info() method on the California Housing dataset, we will be greeted with a summary (how  many rows and columns there are in the dataset, what’s the data type of each attribute, etc.) as shown in the figure below: ![](image_rsrc9TE.jpg)By looking at the summarized description, we can instantly comprehend that the entire dataset has a total of 20,640 instances. Although the number of instances is lower as compared to the other standard machine learning datasets, this is still more than enough for our project. Now here’s where analyzing the data before using it on the machine learning model becomes useful. Carefully look at the non-null values shown in the info() method’s description of the data. We can see that the fifth attribute (total\_bedroom) has a total of 204333 non-null values. While on the surface, this may not seem as something significant, but if you look around, you’ll see that while the total\_bedroom attribute has 20433 non-null values, the other attributes have 20640 non-null values. If we subtract the two numbers, then we get a remainder of 207. This means the total\_bedroom attribute is missing from 207 districts in the dataset; the other attributes are included in every district. Now that we know there’s a discrepancy and what it is, we can make adjustments but we will do that later. Another place where things seem to be amiss is the data types of the attributes. The first nine attributes are all floating-point types while only the last attribute (ocean\_proximity) is an object type. Since  this attribute is an object, this means it can be used as an object in the project as well. However, the dataset is in the form of Comma Separated Values, and this tells us that it should have been a textual attribute. If we use the head() method to display the tabular form of the California Housing dataset, we will see that the 10th attribute (ocean\_proximity) has values that reiterate. If we consider this aspect, this would mean that the attribute is a categorical type. If we go through this assumption, then we can use the value\_counts() method to compute the total number of existing categories along with the number of districts that are linked to these aforementioned categories: \>>> housing\["ocean\_proximity"\].value\_counts() We now have a good understanding of the dataset and now, we can proceed to the next step which will be to divide the dataset into a training set and a testing set. Creating a Testing Set Using Random Sampling Generally, we do not have ample resources to gather a separate dataset just to test the capabilities of a machine learning model. This is because data needs to be cleaned, refined, and error-free, and searching for such a dataset to test our model can often be like looking for a needle in a haystack. For the sake of convenience (and mostly because we don’t have a choice), we separate a portion from the dataset we are training the model on and treat it as an independent dataset. In this way, we now have a dataset that will be used primarily for training the model and another dataset which the model has never seen to test how well the model has learned and how well it performs in real-world tasks. But there are sometimes human errors (albeit it might be unintentional). Let’s discuss this aspect briefly before we move on to the next topic. By quickly analyzing the data in the California Housing set, we came to understand the structure of the dataset more intricately. This allowed us to implement better algorithms, performance measures, and activation functions, etc. In the same  way,  looking through the testing set will also give us similar insight. If we know the data structure of the testing set, then we can purposefully design and choose the most optimal settings for the model according to the testing set. This creates a bias where we are giving more importance to the data we are training the model on rather than preparing it to tackle real-world problems. The end result of this bias would be that the model performs spectacularly on the training and testing set, but its performance lacks significantly when it tries to solve real-world problems. Thus showing us that the efforts we made to make a good linear regression machine learning model did not reciprocate as we would expect. This bias is generally referred to as ‘data snooping bias ’ and it would be recommended that if you know that you will end up using a portion from the original dataset as the training set, then you shouldn’t go through the entire dataset. Now let’s move on to the part where we actually separate a portion from the California Housing set to make a testing set. Generally, the process of picking out data instances from the set is random, but you can also choose to only use the last portion of the dataset as your testing set as well. However, in this case, the testing set will be created by choosing random instances from the dataset and the size of the relative size of the testing set will be 20% of the original dataset. The following lines of code demonstrate how to create a testing set. First, we will have to specify the random shuffling of the original dataset and then create the testing set while leveraging the shuffling we defined: import numpy as np def split\_train\_test(data, test\_ratio): shuffled\_indices = np.random.permutation(len(data)) test\_set\_size = int(len(data) \* test\_ratio) test\_indices = shuffled\_indices\[:test\_set\_size\] train\_indices = shuffled\_indices\[test\_set\_size:\] return data.iloc\[train\_indices\], data.iloc\[test\_indices\] Now to create the testing set: 13 >>> train\_set, test\_set = split\_train\_test(housing, 0.2) \>>> len(train\_set) 16512 \>>> len(test\_set) 4128 Although this approach towards creating a testing set indeed does the job, however, it’s not necessarily the best solution. There are other ways of doing it as well which we will see when we discuss deep neural networks in this book. For now, let’s focus on why this approach is not devoid of any flaws. The thing is, even though a testing set has been created using these lines of code, we cannot omit them from the program once we have saved the testing set. So, whenever the program is executed, a testing set that is completely distinct from the previous one will be created. This defeats the entire purpose of testing sets; at some point, the model will be familiar with the entire dataset, except for the separate portion. When the next testing set is generated, the instances being used there are likely the instances that the model has already gone through. So here’s the gist of the problem we are currently facing. We cannot omit this particular method of creating a testing set, but we also want testing set to be generated for our use as well. The only logical solution is to find a way in which the testing set that is randomly generated by this function is always the same. This would mean that no matter how many times we execute the program, we won’t need to worry about the model being falsely tested. Here is the aforementioned solution to the testing set problem: 

*   If you’re working with a dataset where each instance is accompanied by a marker that acts as its identifier, then we can leverage this aspect. Luckily, the California Housing set has instances that are marked. As such, we can use these identifiers to judge whether this instance should be included in the testing set or not. This can be done by specifying a threshold. Each identifier has a hash value and this makes for  a good threshold. We can set up the threshold in a way that if the hash value of an instance’s identifier is less than 20% of the maximum hash value, then it is allowed to be picked for the testing set. Otherwise, this specific instance is not considered suitable to be used in the testing set. 
*   There are cases where not every dataset has instances accompanied by identifiers. In such a scenario, an easy solution is to simply generate the testing set when the model is executed for the first time and then save it. Afterward, you can omit the function that generates the testing set along with the portion of the dataset which was used in the testing set. So, when you start up the model again, you can load up this testing set only then and everything will go smoothly. 

To implement the first solution with the identifiers as the deciding factor for each instance’s involvement in the testing set, use the following lines of code: from zlib import crc32 def test\_set\_check(identifier, test\_ratio): return crc32(np.int64(identifier)) & 0xffffffff < test\_ratio \* 2\*\*32 def split\_train\_test\_by\_id(data, test\_ratio, id\_column): ids = data\[id\_column\] in\_test\_set = ids.apply(lambda id\_: test\_set\_check(id\_, test\_ratio)) return data.loc\[~in\_test\_set\], data.loc\[in\_test\_set\] Since we are dealing with data that is originally in tabular form, this means that the index (rows and column) of each data instance is unique. The data instances in row 2 cannot be the same instance in row 3 and vice versa and same is the case for columns. Generally, we would prefer to use columns as the identifiers for each data instance but unfortunately, in the California Housing set, the columns are not unique but the rows are. So we will be using the rows as the unique  identifiers for each data instance: housing\_with\_id = housing.reset\_index() # adds an \`index\` column train\_set, test\_set = split\_train\_test\_by\_id(housing\_with\_id, 0.2, "index") Since we are using rows as the identifiers for data instances, there is a possible scenario that might risk disrupting the very solution itself. Let’s say that we want to add new data to the original dataset. If we do so carelessly, we might mess up the arrangement of the rows (corresponding to each data instance) which would, in turn, mess up the whole identifier set up as well. Thus, we need to make sure that even if new data does get added, it is placed at the end of the table only leaving the rest of the index arrangement untouched. If you cannot control the placement of new data, then we simply need to find another element that can serve as a unique identifier for the data instances. Using the attributes of the dataset is a good option as well. However, it is important to remember that if you are using an attribute as a unique identifier, then the attribute itself must be stable. This means that when the data is updated or new data is added, the attributes of the existing instances should not be affected and must not clash with the attributes of the new data instances. In this case, if we were to use attributes as the unique identifiers, then the most suitable option would be the geographical attributes (longitudes and latitudes) for very obvious reasons. The use of attributes as unique identifiers has been demonstrated in the following lines of code: 15 housing\_with\_id\["id"\] = housing\["longitude"\] \* 1000 + housing\["latitude"\] train\_set, test\_set = split\_train\_test\_by\_id(housing\_with\_id, 0.2, "id") Preparing the Data Now that we have split the data into two sets, we are now ready to prepare it so that the algorithms can use it. By saying we need to prepare the data, we actually mean that we need to transform it so that it becomes usable for the algorithms. This is because algorithms need to be fed data in a specific format and type. We cannot use the original structure of the data. There are two ways to prepare the data, we can either do it manually or we can use functions to automate the process. You might think that if you have ample time, doing it manually would be preferable but on the contrary, using functions has better advantages. Some of these perks have been listed below: 

1.  In some cases, there are times when you need to perform the data transformations again (for instance, when adding new data or loading an updated dataset). If you used a function to do the data transformation, then doing it again will be very easy. However, if you did it manually, then a simple task will become quite arduous and time-consuming. 
2.  Each algorithm requires data to be transformed differently before it can use it. So, for different tasks, different datasets, and different algorithms, you will steadily build up a collection of transformation functions. At that point, not only will you be familiar with the functions but also, you can reuse them as well. 
3.  Functions can be used to transform the data as it is being streamed to the memory, in turn, maximizing the efficiency of your model. 
4.  Using functions allow for easy and quick data transformations. This enables the user to try out different data transformations with different algorithms to see what suits your model the best. 

For now, we will create a copy of the training set and omit the labels and predictors within it. If we do not do this, then the function will  also transform the predictors and labels as well. This can be done by using the copy() and drop() methods as shown in the following lines of code: housing = strat\_train\_set.drop("median\_house\_value", axis=1) housing\_labels = strat\_train\_set\["median\_house\_value"\].copy() Data Cleaning Generally, it is recommended to understand and learn about the algorithms first before trying to do a machine learning project on your own. This is because algorithms play a major role in how the model learns patterns. Since algorithms are in the driving seat of the model’s journey towards learning, using data that is incomplete or noisy will badly affect the patterns the algorithm learns as well. This is why many of the algorithms used in machine learning (with a few exceptions) are designed so that they do not function if the data being fed to them has incomplete attributes (features). At the beginning of this project, while analyzing the dataset we came to know that 207 districts were missing the fifth attribute (total\_bedroom) and the attribute itself is short of some values as well. So before we go any further, we must patch up this problem. There are three ways we can do that: 

*   We can simply ignore those districts which are missing the attributes and omit them from the dataset altogether. This can be done by using the dropna() method of DataFrame as shown below: 

housing.dropna(subset=\["total\_bedrooms"\]) 

*   We can omit the attribute from every data instance so we don’t have to deal with it. This can be done by using the drop() method of DataFrame as shown below: 

housing.drop("total\_bedrooms", axis=1) 

*   We can assign a value of our own choice to the missing  values in the attribute. Although this will be based on the user’s intuition, so the performance of the model might get affected based on which value you choose. This can be done by using the fillna() method of DataFrame as shown below: 

median = housing\["total\_bedrooms"\].median() housing\["total\_bedrooms"\].fillna(median, inplace=True) Choosing option three is more logical as the impact of either omitting those districts or omitting the attribute from the entire dataset can have a huge impact on the model’s performance as well. So if you choose the third method as well, then it is recommended that you use the median value (calculating the average value of all the other values of the same attribute) to replace the missing values in the attribute. Once you have calculated the median value, you should save it since you will also need to use it to replace the missing values in the testing set later on as well. Here’s a handy dandy tip regarding Scikit-Learn when you encounter missing values. The Scikit-Learn library features a special class which is known as ‘SimpleImputer .’ By using this class, we can easily calculate the median value in a particular attribute and then use it to fill in the missing values. The reason why using this class from Scikit-Learn is preferred is because it automates the calculation of medians and the replacement of values in a simple manner. Using the SimpleImputer class is pretty simple. Here’s a chronological explanation of how to implement the SimpleImputer class from Scikit-Learn: from sklearn.impute import SimpleImputer imputer = SimpleImputer(strategy=" median") Median is the calculation of the average of several values (that are of the same type). Since this calculation is done on numbers, it makes no sense for us to include an attribute that is not a floating-point type or any numerical data type. From analyzing the data, we know that the last attribute (ocean\_proximity) is not a floating-point type  like the rest of the attributes, hence we need to drop it before we can use the SimpleImputer. To do this, we will simply create a copy of the dataset which does not have the ocean\_proximity attribute: housing\_num = housing.drop("ocean\_proximity", axis=1) We will now use the fit() method to make sure that the training set allows for the imputer instance to fit. To do this, we use the following statement: imputer.fit(housing\_num) At this point, the SimpleImputer class from the Scikit-Library should be done with its job, i.e., the median value of all nine attributes in the dataset (remember that we omitted the 10th attribute ocean\_proximity) has been calculated and is stored within the class’s corresponding variable. But we shouldn’t be relaxed right now. Right now, we know that in the current version of the California Housing dataset we are using, the 5th attribute has missing values. However, there’s no guarantee that when the model is executed, the newly generated values won’t have any missing values as well. So, it’s better not to take chances. That’s why all the attributes (except for the 10th attribute) will be used in the SimpleImputer class and not just the 5th attribute (total\_bedrooms) : \>>> imputer.statistics\_ array (\[ -118.51 , 34.26 , 29. , 2119.5 , 433. , 1164. , 408. , 3.5409\]) \>>> housing\_num.median().values array (\[ -118.51 , 34.26 , 29. , 2119.5 , 433. , 1164. , 408. , 3.5409\]) The imputer is now familiar with the medians of every attribute. We can implement this imputer to convert the training set and fill in any values that might be missing: X = imputer.transform(housing\_num) The output is a standard NumPy array that features attributes that have been transformed by the imputer. Converting array back to its  original form so that it can be used in Pandas is not that difficult as well. All you have to do is use the following statement: housing\_tr = pd.DataFrame(X, columns=housing\_num.columns, index=housing\_num.index) Creating, Training and Evaluating the Model The process of training a machine learning model is not that difficult. On the contrary, if you have understood the concepts which have been elaborated in the previous sections of this book, then you will find that the training process comparatively simple. To train the model, we must first create the model itself. To do this, we will first import the LinearRegression library which will contain all of the algorithms, tools, and activation functions necessary to train the model. Moreover, we also load the dataset we have prepared along with the corresponding labels. This has been demonstrated below: from sklearn.linear\_model import LinearRegression lin\_reg = LinearRegression() lin\_reg.fit(housing\_prepared, housing\_labels) We have now successfully created a machine learning model specifically for performing Linear Regression tasks. We will now proceed to train the model on the testing dataset: \>>> some\_data = housing.iloc\[:5\] \>>> some\_labels = housing\_labels.iloc\[:5\] \>>> some\_data\_prepared = full\_pipeline.transform(some\_data) \>>> print("Predictions:", lin\_reg.predict(some\_data\_prepared)) Predictions: \[ 210644.6045 317768.8069 210956.4333 59218.9888 189747.5584\] \>>> print("Labels:", list(some\_labels)) Labels: \[286600.0, 340600.0, 196900.0, 46300.0, 254500.0\] The model works properly but the predictions are not exactly  accurate. For instance, the first prediction generated by the model after training is inaccurate by a measure of 40% (meaning the value predicted deviates from the target value by a margin of 40%). The Linear Regression Model’s RMSE can be assessed on the complete training set with the help of Scikit-Learn’s mean\_squared\_error() function: \>>> from sklearn.metrics import mean\_squared\_error \>>> housing\_predictions = lin\_reg.predict(housing\_prepared) \>>> lin\_mse = mean\_squared\_error(housing\_labels, housing\_predictions) \>>> lin\_rmse = np.sqrt(lin\_mse) \>>> lin\_rmse 68628.19819848922 The result clearly is unsatisfactory and it proves as an example of a model underfitting the training data. The obtained result suggests that either the information provided by the features is not sufficient, or that the model is not very strong. Underfitting can be fixed by: 

*   Choosing a powerful model 
*   Inputting the training algorithm with better features 
*   Reducing constraints on the model. 

The last option can be eliminated here because the model is non-regularized. Before trying out the addition of more features like the log of population, choose to work with a more complex model such as the DecisionTreeRegressor. This strong model is capable of searching for more complex nonlinear relationships in the data. The following lines of code demonstrate this. from sklearn.tree import DecisionTreeRegressor tree\_reg = DecisionTreeRegressor() tree\_reg.fit(housing\_prepared, housing\_labels) After finishing the training of the model, evaluate it on the training  set as shown below: \>>> housing\_predictions = tree\_reg.predict(housing\_prepared) \>>> tree\_mse = mean\_squared\_error(housing\_labels, housing\_predictions) \>>> tree\_rmse = np.sqrt(tree\_mse) \>>> tree\_rmse 0.0 The code doesn’t seem to display any error which may lead to the conclusion that the model is absolutely perfect. But the more likely assumption would be that the model has overfitted to the data in a terrible way leading to the given result. To make sure of this, do not interfere with the test set until the model is prepared to be launched with confidence. One part of the training set is used to train the model while the other part is used for validation of the model. Using the Testing Dataset to Evaluate the Model Before testing the model, we would usually tune the hyperparameters to improve the overall performance of the model; this is done using techniques such as cross-validation etc. However, these topics have been discussed in detail in the upcoming chapters. For now, we will focus on evaluating and testing the model. So, the next step for this project will include evaluating the final model on the test set. The process is simple and involves acquiring predictors and the labels from the test set, executing the full\_pipeline.transform() method to transform the data and evaluating the final model on the test set. The entire process has been demonstrated below: final\_model = grid\_search.best\_estimator\_ X\_test = strat\_test\_set.drop("median\_house\_value", axis=1) y\_test = strat\_test\_set\["median\_house\_value"\].copy () X\_test\_prepared = full\_pipeline.transform(X\_test) final\_predictions = final\_model.predict(X\_test\_prepared) final\_mse = mean\_squared\_error(y\_test, final\_predictions) final\_rmse = np.sqrt(final\_mse) # => evaluates to 47,730.2 Although the performance of the model is not that spectacular, once you have understood the concept of hyperparameter tuning, which has been explained in detail in upcoming chapters, you will be capable of boosting your model’s performance by a sizable margin. This will serve as a good exercise, i.e., improving a model you have already created when you learn something new. However, before you get excited about the potential benefits of hyperparameter tuning, you must understand one thing. If hyperparameters are excessively tuned, the working of the model turns out to be somewhat worse than described by cross-validation. This is because the system is set to work better with validation data instead of unknown datasets. If such a problem occurs, it is recommended not to recalibrate the hyperparameters to get values that look good on the test set but cannot generally work with new data. 

Chapter 3 Creating a Classification Model  
with Scikit-Learn ![](image_rsrc9SG.jpg)In the first chapter, we learned that in a supervised machine learning model, the most common task performed is either a regression task (the model generates predictions for values) or a classification task (the model generates predictions for classes). Similarly, in the previous chapter, we explored how to build a machine learning model and train it for a regression task. In this chapter, we will now put our focus towards building a model to predict classes. The MNIST Dataset For any task, the machine learning model needs data to be trained with the appropriate data so it can become familiar with the job that’s being assigned to it. Since we are creating a model that can perform classification for the first time (in this book anyway), we will be using a dataset that is the most popular for such an adventure, the MNIST dataset. The MNIST dataset can be seen as the ‘hello world!’ equivalent in machine learning. Beginners becoming familiar with the field of machine learning are often guided through the basics with important tips and tricks using datasets like these. The MNIST dataset is a collection of images depicting handwritten digits. The set contains a total of 70,000 images (small in resolution and size). The reason why this dataset is being used as the forefront for first machine learning projects because the goal of the model is simple and the dataset is fairly large and is completely labeled. Labeled data means that every element of the dataset has been  marked with appropriate classes and such. For the MNIST dataset, each image has been labeled with a number that corresponds to the digit being portrayed by the image. All 70,000 images are labeled under a total of 10 classes. Each of the images belongs to either one of these classes (class digit 1, class digit 2, and class digit 3, etc.). Since the MNIST dataset is the best option for learning the building and training of machine learning models to perform classification, many people also use this dataset to try out new algorithms and new techniques seeing how the model performs. Even if we don’t talk about this dataset in this book, you are bound to come across MNIST sooner or later in your journey of exploring machine learning. Downloading the MNIST Dataset We will be using Scikit-Learn to create the machine learning model and train it. Downloading and fetching the MNIST dataset for the model is pretty straightforward with Scikit-Learn’s helper functions. These functions allow the users to download and fetch pretty much any popular dataset in the community (and as we discussed before, MNIST is one such dataset). The following lines of code demonstrate the use of Scikit-Learn’s fetch() function to download the MNIST dataset: \>>> from sklearn.datasets import fetch\_openml \>>> mnist = fetch\_openml('mnist\_784', version=1) \>>> mnist.keys() dict\_keys(\['data', 'target', 'feature\_names', 'DESCR', 'details', 'categories', 'url'\]) Whenever we use Scikit-Learn for fetching, the datasets obtained typically feature a standard ‘dictionary structure’ which include aspects such as: 

*   A key that is used to describe the dataset itself (DESCR key). 
*   A key that features an array that has per instance, one row and per feature, one column (data key). 
*   An array that has labels in it (target  key). 

Let’s check out the array shown below: \>>> X, y = mnist\["data"\], mnist\["target"\] \>>> X.shape (70000, 784) \>>> y.shape (70000,) From this array, we can clearly see that the dataset has a total of 70,000 images and each of these images has a total of 784 features. The reason behind this exact number of features is simple, every image in the dataset has a resolution of 28 by 28 pixels and each feature of these images represents their corresponding pixel intensity (0 which means white to 255 which means black). Let’s take a look at a digit from the MNIST dataset. To display the image, we have to specify the feature vector of our particular instance, then reshape its size to an array of 28 by 28 (or 28x28). Finally, we use the imshow() function from the Matplotlib library (remember to import it) to display the image. The whole process has shown below: import matplotlib as mpl import matplotlib.pyplot as plt some\_digit = X\[0\] some\_digit\_image = some\_digit.reshape(28, 28) plt.imshow(some\_digit\_image, cmap="binary") plt.axis("off") plt.show()  
![](image_rsrc9TF.jpg)This handwritten image looks familiar to the digit ‘5’. By checking the label of this image, we can confirm that is indeed the case: \>>> y\[0\] '5' If we carefully look at the labels included in the dataset, we will notice that they are strings. We cannot ignore this aspect as the majority of the Machine Learning algorithms want numbers instead of characters. Hence, we will need to cast the ‘y’ object as an integer as shown below: \>>> y = y.astype(np.uint8) If you think that classification tasks are simple to be dealt with, then you have underestimated the complexity of the task. To elaborate on the point being made here, take a look at the figure shown below that depicts a cluster of images from the MNIST dataset. ![](image_rsrc9TG.jpg)Now before we move on and start working with the dataset and train the machine learning model with it, we must always make sure that we take a chunk from the dataset and keep it aside (not used in training). This is important because we need data that is unfamiliar for the model (the data that the model is familiar with is only the data it trains on) to test its capabilities properly and have an accurate gauge of its performance. Thus, we will be splitting the dataset into a training set and a testing set. The training set is made up of the first 60 thousand images of the dataset and the testing set is made up of the last 10 thousand images of the dataset. X\_train, X\_test, y\_train, y\_test = X\[:60000\], X\[60000:\], y\[:60000\], y\[60000:\] In this case, the training set has already been shuffled but you should make sure that the sets you are working with are shuffled as well. This will ensure that every cross-validation fold in the later stages will be somewhat identical. Also, certain algorithms can be easily affected by order of the instances they receive during training. For example, if an algorithm receives a bunch of similar training instances, then it will end up with a poor performance later on. However, it’s not always a good idea to shuffle the sets. If you are working with data that has a proper order to its entries (like stock market price data etc.), then shuffling might disrupt the integrity of the dataset. So be careful of the context as well. Training a Binary Classifier For now, we will tone down the complexity of the problem and only stick with a basic approach as there’s no need to spend too much exploring every aspect of classification in this book. We will simplify the problem of classifying every digit separately (multi-classification) to only classifying a single digit (binary classification) by training the machine learning model to identify the digit ‘5’ only. In this way, the model will be able to detect whether the digit in front of it is ‘5’ or it isn’t. To start the project, we will first need to generate the necessary target vectors to handle the task of binary classification: y\_train\_5 = (y\_train == 5)       # True for all 5s, False for all other digits y\_test\_5 = (y\_test == 5) Now the target vectors are ready, we simply need to select and train a suitable classifier. One of the standard classifiers that perform well with simple tasks such as this is the Stochastic Gradient Descent classifier, also known as the SGD classifier. The reason behind this is simple, SGD is known to have the ability to handle large datasets (such as the MNIST dataset) capably and efficiently. The ability of the SGD classifier to handle each instance of training independently is also what makes it a desirable option. To use this classifier, we will implement the SGDClassifier class from Scikit-Learn. We will now proceed to implement SGDClassifier and then train the model using the training set. The process has been demonstrated below: from sklearn.linear\_model import SGDClassifier sgd\_clf = SGDClassifier(random\_state=42) sgd\_clf.fit(X\_train, y\_train\_5) Once the training is complete, it is now ready to distinguish the digit 5 from the rest of the handwritten digits in the dataset. We can also test it by asking it to predict whether an image specified is the digit 5 or not: \>>> sgd\_clf.predict(\[some\_digit\]) array(\[ True\]) When we ask the classifier to generate a prediction corresponding to the image we show it (in this case, it would be an image of the handwritten digit 5), the classifier produces an output that accurately classifies the image to the digit it represents. This means that we are done with training and now it’s time to move to the next  step, which is to measure the model’s performance. Measuring the Performance In comparison to a regressor, a classifier is significantly more difficult (or more accurately, trickier) to evaluate. Since this is an important step and not so simple, we will largely focus our discussion on this aspect. There are several different measures for evaluating a classifier’s performance and each measure has its own way of doing it. Using Cross-Validation to Measure the Accuracy Cross-validation is a really good approach towards measuring the accuracy of a model. We have already explored it in the previous chapter as well. One of the most common complaints users have with cross-validation is that it does not provide much control over the process itself. The workaround for this is to just implement every step of the cross-validation process by yourself. The following code demonstrates the manual implementation of the cross\_val\_score() in Scikit-Learn. from sklearn.model\_selection import StratifiedKFold from sklearn.base import clone skfolds = StratifiedKFold(n\_splits=3, random\_state=42) for train\_index, test\_index in skfolds.split(X\_train, y\_train\_5): clone\_clf = clone(sgd\_clf) X\_train\_folds = X\_train\[train\_index\] y\_train\_folds = y\_train\_5\[train\_index\] X\_test\_fold = X\_train\[test\_index\] y\_test\_fold = y\_train\_5\[test\_index\] clone\_clf.fit(X\_train\_folds, y\_train\_folds) y\_pred = clone\_clf.predict(X\_test\_fold) n\_correct = sum(y\_pred == y\_test\_fold) print(n\_correct / len(y\_pred))                  # prints 0.9502,  0.96565, and 0.96495 Now let’s get back to using the standard cross\_val\_score() function from Scikit-Learn for the model using SGDClassifier . We will be using the K-fold-cross-validation approach and set the total number of folds to 3. \>>> from sklearn.model\_selection import cross\_val\_score \>>> cross\_val\_score(sgd\_clf, X\_train, y\_train\_5, cv=3, scoring="accuracy") array(\[0.96355, 0.93795, 0.95615\]) We can see that by evaluating the model using K-Fold validation, we get a whopping 93% accuracy. Now let’s use a relatively simple classifier which basically classifies every image from the training set into the class ‘not a 5 digit’. from sklearn.base import BaseEstimator class Never5Classifier(BaseEstimator): def fit(self, X, y=None): ​ return self def predict(self, X): ​ return np.zeros((len(X), 1), dtype=bool) Now let’s check the accuracy of the model using this primitive classifier. \>>> never\_5\_clf = Never5Classifier() \>>> cross\_val\_score(never\_5\_clf, X\_train, y\_train\_5, cv=3, scoring="accuracy") array(\[0.91125, 0.90855, 0.90915\]) You might be confused that why does a model that only classifies images into the ‘not a 5 digit’ class end up with a 90% accuracy. Well, the reason behind this is simple. In reality, only 10% of the images are handwritten 5 digits. So if the model simply predicts that the image in front of it isn’t ‘5’, then it will be correct about 90% of the time. Since the digit is scarce, to begin with, it is less likely for it to  show up and guessing that the image isn’t ‘5’ will end up as a correct prediction most of the time. The purpose of this demonstration was to explain how unreliable the accuracy parameter is when measuring the performance of a classifier. This is even more obvious for datasets that have unequal occurrences of classes (in this case, the occurrence of the digit 5 is relatively less than the other ones). Confusion Matrix Other performance measures have an element of uncertainty and bias within them (even if it’s extremely small) or we just simply do not find their measurements as reliable. In such cases, the best way to check how well the classifier performs is by seeing how confused it gets when making predictions. This performance measure creates a matrix and it highlights how many times the classifier got confused and made a wrong prediction and how many times it clearly made the correct prediction. To use the confusion matrix, we would first require predictions generated by the model. This is necessary as the matrix will consider these predictions and compare them to their corresponding targets. Using the testing set to generate predictions is also an option but it is not recommended. Instead, you should always save this dataset for the testing phase. We will be using Scikit-Learn’s cross\_val\_predict() function to generate the necessary predictions to use the confusion matrix. from sklearn.model\_selection import cross\_val\_predict y\_train\_pred = cross\_val\_predict(sgd\_clf, X\_train, y\_train\_5, cv=3) The cross\_val\_predict­() function uses K-fold-cross-validation to generate and display predictions made by the classifier on each fold. In this way, we save the testing set for the end of the project and get a good set of predictions as well. Now that the requirement has been fulfilled, we can no proceed to use the confusion matrix. To do this, we will be employing the confusion\_matrix() function by passing the original target classes (which are referred to as y\_train\_5 ) and prediction classes we just generated (which are referred to as y\_train\_pred ). \>>> from sklearn.metrics import confusion\_matrix \>>> confusion\_matrix(y\_train\_5, y\_train\_pred) array(\[\[53057, 1522\], \[ 1325, 4096\]\]) Note that every row in the confusion matrix is actually a representation of a class and each column is a representation of the predicted class . While using the confusion matrix, you need to become familiar with some key terms, which are; true negatives, false negatives, true positives, and false positives. These key terms tell us what the numbers are representing. If a number is labeled as ‘true positive’ in the array of a confusion matrix, then it means the classifier was able to classify the image as a ‘5’ correctly. Similarly, a number labeled as ‘false positive’ means that the classifier wrongly classified some other number in the category of ‘5’. Same is the case for true negative and false negative, true negative means the number was correctly classified as a non-5 digit and false negative means that the digit 5 was wrongly classified into the non-5 digit class. Now we can proceed to study the confusion matrix of the classifier we are using. The first row represents the negative class while the second row represents the positive class. In the matrix, the left diagonal (1522, and 1325) represent wrong predictions while the right diagonal represents correct predictions. Using the terms we learned before, you can interpret what the matrix means very easily now. From this result obtained from the confusion matrix, we can now conclude that the classifier we are using is good but it is not completely perfect. This is because the perfect classifier’s confusion  matrix would tell us that it only has true positives and true negatives, giving the array a diagonal of non-zero values. But this is an ideal scenario as no classifier can give 100% correct predictions. Here’s an example of how a perfect classifier’s confusion matrix would look like: \>>> y\_train\_perfect\_predictions = y\_train\_5 \>>> confusion\_matrix(y\_train\_5, y\_train\_perfect\_predictions) array(\[\[54579, 0\], \[ 0, 5421\]\]) Although the confusion matrix gives a better understanding of the classifier’s performance as compared to the accuracy metric, still, there is room to use a metric that is even more concise, i.e., precision and recall. Precision and Recall Apart from the cross-validation and confusion matrix, Scikit-Learn also provides multiple functions that allow users to prevent other classifier metrics as well. This includes precision and recall metrics. The following lines of code demonstrate the use of these two metrics and their corresponding results: \>>> from sklearn.metrics import precision\_score, recall\_score \>>> precision\_score(y\_train\_5, y\_train\_pred) # == 4096 / (4096 + 1522) 0.7290850836596654 \>>> recall\_score(y\_train\_5, y\_train\_pred) # == 4096 / (4096 + 1325) 0.7555801512636044 From these metrics, we can clearly note that the model using the classifier does not perform as well as we were led to believe when evaluating the model’s performance using the accuracy metric. From the precision and recall metrics, we can see that when the  classifier predicts that an image represents the digit 5, the chance of it being correct is only 72.9%. In addition, the classifier can only identify about 75.6% of the total images of the digit 5. It is common practice to unite the precision and recall metrics. Doing so results in a single metric which is then referred to as ‘F1 score’. The reason why we do this is that it makes it easier to contrast different classifiers. However, since the F1 score metric is basically a cocktail of precision and recall metrics, the value of the F1 score reflects the values of both precision and recall (in other words, if precision and recall is low, the F1 score is low and vice versa). We can easily calculate the F1 score as well by using Scikit-Learn’s f1\_score() function. The process of doing so has been demonstrated below: \>>> from sklearn.metrics import f1\_score \>>> f1\_score(y\_train\_5, y\_train\_pred) 0.7420962043663375 Since we have established the fact that a high F1 score is only possible with both precision and recall to have similarly high values. However, this can be misleading as there are cases where we prefer one metric over the other. For instance, if we create a machine learning model and train the classifier to identify videos that are safe for kids, then we would want the classifier to dismiss those videos that are unsafe. This means the classifier will have low recall and will only approve those videos that are safe for kids to watch, meaning it must have high precision. In such a context, we wouldn’t want such a classifier to have a high recall as this would mean that there’s a good chance for some really disturbing videos for children would slip past it. Similarly, let’s say that we build a model and the classifier is trained to look through various images obtained from surveillance cameras and identify shoplifters. In such a context, it is absolutely fine for the classifier to have low precision (even if it’s 30% it doesn’t matter) as  long as the classifier is measured to have a high recall of 99%. Even though some predictions might be false alerts, but it’s almost certain that the security of the shop will be able to catch all of the shoplifters. However, even though we can combine these two metrics into one, we cannot increase the potency of one metric without sacrificing the quality of the other metric. In other words, we increase the precision of the classifier without reducing its recall and we cannot increase the recall without reducing the precision. This aspect is commonly referred to as ‘Precision/Recall trade-off’ and this is our next topic of discussion. The Balance between Precision and Recall In this section, we will explore the unbreakable balance of ‘precision’ and ‘recall.’ The reason as to why we say ‘the unbreakable balance’ is because whenever we increase one metric, the other metric’s value is decreased accordingly (in other words, maintaining balance). However, this explanation is too vague and needs more clarification, and to do this; we will first need to understand how decisions are made by the ‘SGDClassifier.’ To decide what predictions to make, the classifier first computes a value for each data instance. This value basically represents the idea of what the classifier thinks is the most likely option. For example, once the decision function ‘translates’ the value mentioned above into a meaningful entity (let’s call it a score), it then generates a prediction regarding this specific data instance based on this score. In other words, if the score ends up being higher, then for the classifier, this means that the data instance is more likely to belong to the ‘positive class’ and vice versa. However, to make the process of making the decision more solid, the classifier employs a defines a fine line between the positive and negative class. If the score isn’t high enough to cross this line into the positive class, then the classifier will decide to predict that the data instance belongs to the negative class. Generally, this line between two decisions is commonly referred to as the ‘Threshold.’  To understand this better, let’s look at the figure shown below: ![](image_rsrc9TH.jpg)(Picture Illustrated by Aurélien Géron in the book Hands-On Machine Learning with Scikit-Learn, Keras and TensorFlow) In Scikit-Learn, there’s no way to tweak the settings of the threshold of a classifier; we can simply use a different threshold altogether. In order to decide which threshold to use, we simply look at the score values and decide based on this information. The following code demonstrates the use of the decision\_function() to do this: \>>> y\_scores = sgd\_clf.decision\_function(\[some\_digit\]) \>>> y\_scores array(\[2412.53175101\]) \>>> threshold = 0 \>>> y\_some\_digit\_pred = (y\_scores > threshold) array(\[ True\]) As we can see, upon calling the decision\_function() method, we are provided with information regarding the score and the threshold being used by the SGDClassifier. By default, the threshold of this classifier is set to 0. Thus, if we use this same threshold, the result we would get will be the same as we would get when using the predict() method. Now let’s bring the threshold up a notch and see what happens: \>>> threshold = 8000 \>>> y\_some\_digit\_pred = (y\_scores > threshold) \>>> y\_some\_digit\_pred array(\[False\]) The image that is identified by the classifier as false when the threshold is ‘8000’ is actually incorrect as it represents the digit ‘5’. By increasing the threshold we can now confirm that the recall of the classifier is decreased significantly. This is the part where inexperienced and beginners who have only explored the basics of machine learning will struggle, and that is identifying what threshold is the best option for the time being. Luckily, there’s a simple and comprehensive way of finding out. To do this, we would need to use cross-validation, but differently. Normally, we would generate predictions from using the cross-validation function (cross\_val\_predict())  but since that’s not what we came for, we will ask it to specify each data instance’s ‘decision score.’ Here’s a demonstration on how to do this: y\_scores = cross\_val\_predict(sgd\_clf, X\_train, y\_train\_5, cv=3, method="decision\_function") Once we get the scores from the cross-validation function, we use another function precision\_recall\_curve() which will calculate the two metrics of precision and recall for every threshold that is possible by using these decision scores as the precursor: from sklearn.metrics import precision\_recall\_curve precisions, recalls, thresholds = precision\_recall\_curve(y\_train\_5, y\_scores) Now, all that’s left to do is to make use of the Matplotlib library and graphically plot the precision and recall metrics of the threshold values as demonstrated in the lines of code shown below: def plot\_precision\_recall\_vs\_threshold(precisions, recalls, thresholds): plt.plot(thresholds, precisions\[:-1\], "b--", label="Precision") plt.plot(thresholds, recalls\[:-1\], "g-", label="Recall" ) \[...\] # highlight the threshold and add the legend, axis label, and grid plot\_precision\_recall\_vs\_threshold(precisions, recalls, thresholds) plt.show() ![](image_rsrc9TJ.jpg)From this visual representation of how each threshold affects the precision and recall of the classifier, you can then make the final decision based on the metric that is preferred more for the task to be performed by the classifier. Let’s say that we want the classifier to have at least 90% precision. By looking at the data plotted in the graph shown above, we can easily understand that to do that, we would need to use a threshold of at least 8000. Alternatively, we can also use np.argmax() to search for the threshold that at the lowest level, will provide 90% precision. The use of np.argmax() has been shown below: threshold\_90\_precision = thresholds\[np.argmax(precisions >= 0.90)\]       # ~7816 We now know that the lowest threshold needs to be 7816 to obtain a precision of 90% for the classifier. Instead of using the predict() method of the classifier, we can also  generate predictions by using the following line of code: y\_train\_pred\_90 = (y\_scores >= threshold\_90\_precision) Now with the tweaks that have been made to the precision and recall of the classifier, let’s now check what the metrics are for the predictions obtained: \>>> precision\_score(y\_train\_5, y\_train\_pred\_90) 0.9000380083618396 \>>> recall\_score(y\_train\_5, y\_train\_pred\_90) 0.4368197749492714 We now finally have a classifier that features 90% precision. By following this method, we can easily create a classifier with any precision we want easily: all we have to do is just adjust the threshold. If we want to increase the recall of the classifier, all we have to do is lower the threshold to the point where the recall is maximum. And that’s it! 

Chapter 4 Using Keras to Work  
With Artificial Neural Networks ![](image_rsrc9SG.jpg)The majority of the revolutionary human inventions are primarily inspired by nature itself. For instance, the concept of flying was inspired by birds which led to the invention of airplanes. At some point in your life, you might have come across a discussion comparing the human brain to a computer. Although it might seem absurd at first, it’s not completely heretical. The structure of the human brain is so amazing and complex that it can serve as the foundation for the most successful structural network designed for machine-learning as well as deep learning. A machine learning model whose structure is inspired by the arrangement of biological neurons themselves is known as an artificial neural network. However, there’s no need to worry as we will not start discussing biological neurons to explain the similarities featured in artificial neural networks. Instead, we will be directly discussing the implementation of artificial neural networks in a machine learning model by using the Keras API. Using the Keras API Unlike tensor-flow and scikit-learning, Keras is a comparatively more advanced and capable API that is mostly used for deep learning models. Using the Keras API, we can not only effectively execute neural networks in our models but also create our own custom neural networks using the lower-level API. However, in this section, we will focus our discussion only on implementing neural networks in our machine learning model using the Keras API. Keras was first released in 2015 as an open-source project; as such, the field of deep learning and machine learning using artificial neural networks is still developing. The success of a model depends on the ingenuity of the user, the quality of the data available for training, and the way artificial neural networks have been implemented. Artificial neural networks generally perform tasks that require heavy computational resources; as such, the Keras API relies on a backend to handle this computing requirement. At the time of writing of this book, the most popular open-source deep-learning backend libraries which can be used with the Keras API are the following: 

*   TensorFlow 
*   Microsoft Cognitive Toolkit (also referred to as CNTK) 
*   Theano 

We can also use different implementations to run the Keras API. For instance, Keras can be implemented on: 

*   Apache MXNet 
*   Apple’s Core ML 
*   JavaScript or TypeScript (Allows Keras code to be executed in a web-browser) 
*   PlaidML (Runs Keras code on a Graphical Processing Unit such as those from Nvidia) 

These different implementations of Keras offer this API a wider scope of use. Back to the main discussion, out of the three popular backend libraries for Keras, TensorFlow is the most preferred library. If you wish to use the TensorFlow, then you will be happy to find out that the TensorFlow library itself now features its own implementation with Keras (tf.keras ). However, the only drawback is that this  implementation only supports one backend library and that library is none other than TensorFlow. Even so, some major advantages can be leveraged from the TensorFlow library in the form of some very useful and constructive features. For example, this particular implementation features TensorFlow’s Data API that makes loading data easier and more effective while also providing an efficient way of pre-processing data as well. As such, we will be using the tf.keras implementation of the Keras API in this book as well. However, to make the code being used in this chapter compatible with other Keras implementations (for instance, Python), we will refrain from using features that are specific to the TensorFlow library. In this way, by making small changes in the code (like changing the import) readers can use it on their own preferred Keras implementation as well. The following figure demonstrates two different Keras implementations. On the left, you can see a multi backend Keras implementation and on the right, you can see the TensorFlow Keras implementation. ![](image_rsrc9TK.jpg)Right now, there’s a newer version of the TensorFlow backend which is known as TensorFlow 2. This version of the deep-learning library improves on the weaknesses and grey areas in the 1.x version of the TensorFlow library. Moreover, TensorFlow 2 has officially adopted the Keras API and developers have cleaned other APIs in this  library. Hence, we will start learning about using Keras by installing TensorFlow 2. Installing TensorFlow 2 In the beginning chapters of this book, we learned the proper steps towards installing an open-source text editor ‘Jupyter’ along with the machine learning library ‘Scikit-learn.’ We will follow the same procedure to install the TensorFlow library using ‘pip.’ If you are using a virtual environment, then be sure to turn it on before following the instructions. You can activate the virtual environment by using the following commands in the command-line interface: $ cd $ML\_PATH # Your ML working directory (e.g., $HOME/ml) $ source my\_env/bin/activate              # on Linux or macOS $ .\\my\_env\\Scripts\\activate                 # on Windows If you are not using a virtual environment, then you will have to run the command line using administrator rights. To install TensorFlow 2, we need to use the following command. $ python3 -m pip install -U tensorflow If you are using a GPU and CPU system, then you’ll have to install other libraries in addition to the TensorFlow library as well (a detailed explanation for GPU systems has been given on TensorFlow’s official website [https://tensorflow.org/install](https://tensorflow.org/install) ). Now that TensorFlow 2 has been installed on our system, we need to check if it is working properly and it is not missing any dependencies. To do this, open the Python shell or the Jupyter notebook (whichever you prefer using) and import the libraries as shown below: \>>> import tensorflow as tf \>>> from tensorflow import keras \>>> tf.\_\_version\_\_ '2.0.0' \>>> keras.\_\_version\_\_ '2.2.4-tf' These lines of code confirm the version of TensorFlow installed (2.0.0) on your system along with the version of the Keras API (2.2.4) being implemented by TensorFlow. We will now proceed to use the Keras API and the TensorFlow library to create a model that can classify images. Using a Sequential API to Create an Image Classifier The very first step of building an image classifier model is to choose a dataset and then acquire it for the model. For this demonstration, we will be using a Fashion MNIST dataset. This is a replacement to the generally used MNIST dataset (the dataset used to train a machine learning model to classify handwritten digits). The only difference in this dataset is that it features popular fashion items instead of handwritten digits. The format for both datasets is the same, i.e., a total of 70,000 grayscale images (resolution of 28x28 pixels) and 10 classes. Since the Fashion MNIST dataset features fashion items instead of handwritten digits, each class is consequently more diverse. Hence, the dataset is more challenging for the model to classify as compared to the standard MNIST dataset. For comparative purposes, if we used a standard linear machine learning model on the MNIST dataset (handwritten digits), then we can obtain a maximum accuracy of 92%. However, if we used the same model with the Fashion MNIST dataset, the maximum accuracy we can obtain is only 83%. Loading the Fashion MNIST Dataset Using Keras The Keras API features several functions that allow users to load some of the most common datasets used in the machine-learning community, such as the MNIST dataset, the Fashion MNIST dataset. Even the housing dataset that has been used in the second chapter of this book (the California housing dataset) can be loaded by using the  utility functions of Keras. We will now proceed to load the Fashion MNIST dataset using Keras. We can do this by executing the following lines of code: fashion\_mnist = keras.datasets.fashion\_mnist (X\_train\_full, y\_train\_full), (X\_test, y\_test) = fashion\_mnist.load\_data() The process of loading datasets is radically different in Keras as compared to Scikit-Learn. This is because of the difference in the model’s structure. Scikit-Learn uses a basic machine learning structure so a dataset is converted into one-dimensional arrays. However, since we are implementing many layers in a deep neural network, the fundamental structure is completely different. Hence, data needs to be transformed in a different manner (that’s why we convert every instance in a dataset into 28 by 28 array so that a deep neural network can use it) Keeping the following differences in mind, let’s observe the two characteristics of the Fashion MNIST dataset, i.e., the shape and structure. \>>> X\_train\_full.shape (60000, 28, 28) \>>> X\_train\_full.dtype dtype('uint8') The dataset features training and a testing set but no validation set, so we will have to make one before going any further. Since we are using an SGDClassifier with this model, we will need to scale the attributes of the input data (because this is a deep neural network model). Here’s what we are going to do: 

*   Take the original range of pixel intensity of each data instance and scale the range down to 0 to 1. To do this, we will take the maximum value of the pixel intensity and divide it with itself (in this case, it would be 255.0). The  following lines of code demonstrate this: 

X\_valid, X\_train = X\_train\_full\[:5000\] / 255.0, X\_train\_full\[5000:\] / 255.0 y\_valid, y\_train = y\_train\_full\[:5000\], y\_train\_full\[5000:\] Unlike the MNIST dataset where the label represented the handwritten digit itself, we need to label the Fashion MNIST dataset in a slightly different manner. We will need to create a list of all of the class items to know what item the model is being trained on. A list can be created as follows: class\_names = \["T-shirt/top", "Trouser", "Pullover", "Dress", "Coat", "Sandal", "Shirt", "Sneaker", "Bag", "Ankle boot"\] Now, if we check what item does the very first image from the dataset represent, we will the item’s correct name: \>>> class\_names\[y\_train\[0\]\] 'Coat' Using the Sequential API to Build the Model Now that we have acquired the dataset and loaded it using the Keras API, we now need to build a model with a neural network that is capable of processing this data. For this purpose, we will be creating a ‘Classification MLP (Multilayer Perceptron)’ that features a total of 2 hidden layers. This has been demonstrated in the following lines of code: model = keras.models.Sequential() model.add(keras.layers.Flatten(input\_shape=\[28, 28\])) model.add(keras.layers.Dense(300, activation="relu")) model.add(keras.layers.Dense(100, activation="relu")) model.add(keras.layers.Dense(10, activation="softmax")) Before we proceed any further, let’s understand how these lines of code actually work step by step. 

1.  The very first line of code simply generates a sequential model  . This type of model is practically the most simple and basic type of machine learning model using artificial neural networks. This is because a sequential model’s structure only consists of one stack of layers. These layers are sequentially connected; hence the API is known as Sequential API. Up till this point, the model is still empty, i.e., it does not consist of any layers. 
2.  In the next line, the process of adding additional layers to the neural network begins. We start by adding a ‘Flatten Layer’ to the network. The purpose of this layer is to transform the dimensional features of its inputs. This means that any image that is passed through the ‘Flatten Layer’ will be reshaped into a one-dimensional image. Similarly, note that unlike the rest of the layers, the second layer does not have any parameters assigned to it. The reason behind this is because the only job of this layer is to convert the dimensions of the inputs (which is basically just processing data). Moreover, the shape of the data that is supposed to be input to the neural network must always be specified on the very first layer. Since the ‘Flatten Layer’ is the network’s first layer, we can see that an argument specifying the shape of the images is also being used (input\_shape=\[28, 28\]) 
3.  In the third line of code, we begin implementing ‘dense hidden layers’ within the neural network. When we define layers that actually employ algorithms to learn patterns, this means that they use neurons. As such, when defining such layers in code, we must also specify the number of neurons this layer will feature as well. As you can see, the first numerical value within the parenthesis corresponds to the neurons the first hidden dense layer will feature. After specifying the number of neurons, the last thing to wrap up the layer definition is to define the activation function the layer will use to handle its weight matrices. In this case, the  activation function defined for this layer is the ‘ReLU’ activation function. 
4.  In the fourth line of code, we are adding in another dense hidden layer. However, this layer consists of only 100 neurons. The activation function that is used in this layer is the same, i.e., ReLU. 
5.  In the final line of this code block, we are adding a dense layer but this time, it is a Dense output layer consisting of only 10 neurons. Moreover, the activation function sequence is also different. This layer uses the softmax activation function . 

There’s a different method through which we can insert additional layers into a sequential model. This method is pretty simple and straight-forward. All you have to do is list all of the layers you want the model to have at the time the model is being generated. The following lines of code show how to do this: model = keras.models.Sequential(\[ keras.layers.Flatten(input\_shape=\[28, 28\]), keras.layers.Dense(300, activation="relu"), keras.layers.Dense(100, activation="relu"), keras.layers.Dense(10, activation="softmax") \]) If you want to double-check and see the layers currently being used in your model, then you can do so by using the method ‘model.summary()’ as shown below: \>>> model.summary() Model: "sequential" \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ Layer (type) Output Shape Param # \================================================ flatten (Flatten) (None, 784) 0 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ dense (Dense) (None, 300) 235500 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ dense\_1 (Dense) (None, 100) 30100 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ dense\_2 (Dense) (None, 10) 1010 \================================================ Total params: 266,610 Trainable params: 266,610 Non-trainable params: 0 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ By using this method, we can not only see the name of each layer, but the method also provides us with the total number of parameters being used by the layers. To summarize, the method model.summary() provides the user with: 

*   The name of every layer in the model. 
*   The output shape of each layer. 
*   The total parameters of every layer. 
*   The total number of trainable and non-trainable parameters. 

From the above model summary, note that the dense layer  is particularly rich in parameters. The very first dense hidden layer has a total of 235,500 parameters alone. Although it may seem like a very impressive feat, however, it has its pros and cons. The good thing about a layer having so many parameters is that it gives the model as a whole, better flexibility when fitting to the training dataset. On the other hand, this also means that there’s a higher chance of the model overfitting and the chances increase when we do not have enough training data to use with the model. We can also fetch the entire list of layers being used by the model. This fetching can be done either according to the index or according to the names of the layers. \>>> model.layers \[<tensorflow.python.keras.layers.core.Flatten at 0x132414e48>, <tensorflow.python.keras.layers.core.Dense at 0x1324149b0>, <tensorflow.python.keras.layers.core.Dense at 0x1356ba8d0>, <tensorflow.python.keras.layers.core.Dense at 0x13240d240>\] \>>> hidden1 = model.layers\[1\] \>>> hidden1.name 'dense' \>>> model.get\_layer('dense') is hidden1 True If you want to access any parameter or all of the parameters of a specific layer, then you can do so by using the weight methods which are; get\_weights() and set\_weights() . If the parameters you are accessing are of a dense layer, then you will also have access to both weights of the layer’s connections along with the bias terms as well: \>>> weights, biases = hidden1.get\_weights() \>>> weights array(\[\[ 0.02448617, -0.00877795, -0.02189048, ..., -0.02766046, 0.03859074, -0.06889391\], ..., \[-0.06022581, 0.01577859, -0.02585464, ..., -0.00527829, 0.00272203, -0.06793761\]\], dtype=float32) \>>> weights.shape (784, 300) \>>> biases array(\[0., 0., 0., 0., 0., 0., 0., 0., 0., ..., 0., 0., 0.\], dtype=float32) \>>> biases.shape (300,) We can see that the dense layer has randomly initialized the connection weights while the biases, on the other hand, were initialized from zero. This is because the random initialization is the key to breaking the symmetry in connection weights. Moreover, the biases being initialized from zero is fine as well. But this is not the only method through which you can initialize the parameters when making layers. The kernel\_initializer method as well as the bias\_initializer are alternatives that work just as well. Compiling The Machine Learning Model Once you finish with the initial steps of creating a model, it is still missing the loss function and optimizer. The same is this case for this particular model. We must use the compile­() method in order to set the appropriate loss function and the optimizer to be used with the model. In addition, you can also direct the model to compute a bunch of other metrics during the training and evaluation phase by simply listing the metrics. The following lines of code demonstrate the specification of a loss function, an optimizer, and an extra metric. model.compile(loss="sparse\_categorical\_crossentropy", optimizer="sgd", metrics=\["accuracy"\]) Before proceeding with the training and evaluation of the model, let’s first understand what this block of code is doing. In the very first line, we are specifying a loss function for our model. Since we are dealing with scattered labels (meaning that each instance is simply represented by a class index which ranges from 0 to 9 for this specific dataset), hence we are using the sparse\_categorical\_crossentropy loss function. Note that if we were dealing with even a single target probability within each class for each instance (for example, \[0., 1., 0., 0., 0., 0., 0., 0., 0., 0.\] representing a class), then we would be using the categorical\_crossentropy loss function instead of the sparse one. Similarly, if we were dealing with a simple binary classification problem, then instead of using the softmax activation function, we would have used the sigmoid activation function. Consequently, the loss function in such a scenario would’ve been binary\_crossentroy . In the second line of code, we are specifying the optimizer. This specifies the way we are going to train the machine-learning model. In this case, it is ‘sgd.’ This tells the system that we want to perform a standard Stochastic Gradient Descent for the training process. Also, it is important to specify the learning rate when using an SGD optimizer. The statement optimizer=“sgd” defaults the learning rate of the model to ‘0.01’. If you want to specify it, then you can do so by using the following statement instead: optimizer=keras.optimizers.SGD(lr=insert value here ) In the final line of code, we are specifying the calculation of the ‘Accuracy’ metric because we are performing a classification task.  Hence, the measure of this metric is very relevant to the performance of the model. Training and Evaluation of the Machine Learning Model We are now finally set up to train the model. To start the training, we use the fitting method known as fit() as shown below: \>>> history = model.fit(X\_train, y\_train, epochs=30, ... validation\_data=(X\_valid, y\_valid)) ... Train on 55000 samples, validate on 5000 samples Epoch 1/30 55000/55000 \[======\] - 3s 49us/sample - loss: 0.7218 - accuracy: 0.7660 \- val\_loss: 0.4973 - val\_accuracy: 0.8366 Epoch 2/30 55000/55000 \[======\] - 2s 45us/sample - loss: 0.4840 - accuracy: 0.8327 \- val\_loss: 0.4456 - val\_accuracy: 0.8480 \[...\] Epoch 30/30 55000/55000 \[======\] - 3s 53us/sample - loss: 0.2252 - accuracy: 0.9192 \- val\_loss: 0.2999 - val\_accuracy: 0.8926 For training the model, we simply specify the corresponding input features (X\_train) of the dataset and the relevant target classes (y\_train). Moreover, always remember to specify the number of epochs you want the training to iterate for the model. If you do not specify the epochs, then it will just default to 1 epoch (and that is  certainly not enough to create a good model). The next step is optional, but still a good practice nonetheless. Along with the training dataset, we are also providing the model with a validation dataset as well. Once a training epoch is completed, Keras consults the validation dataset to firstly measure the loss, then the additional metric specified in the compilation step, which would be ‘accuracy’ in this case. These values give us an idea of how good the model will actually perform. For instance, if the model performs relatively better on the training dataset as compared to the validation dataset, then this means that the model is in fact, overfitting to the training dataset. Once all of the training epochs have been completed, the neural network is fully trained. If we look at the actual training process shown by the system above, we can notice that the training loss decreased after each epoch. This tells us that the model is fitted to the training dataset very well. Similarly, the final accuracy of the model on the validation dataset is 89.26% while the final accuracy on the training dataset is 91.92%. The difference is not that big and this tells us that the model is not overfitting. Here’s a cool trick for you guys to use, if you do not have a validation set created before-hand, then you can simply split the training set into training as well as a validation set. For instance, you can reserve the last 20% of the total data in the training set to be used as a validation set before the entire dataset is shuffled. This can be done by using the following argument: validation\_split=0.2 Another tip to remember is that if you notice your training set having varying weights, it means that some classes of the set are ‘underrepresented’ and some classes of the set are ‘overrepresented,’ and you should adjust this and train the model again. This can be done by using the argument class\_weight when calling the fit() method. We can also visually represent the training and validation data given by the fit() method to evaluate the model more easily. The fit() method returns the following: 

*   A history object that features all of the defined training parameters. This is history.params . 
*   The total number of epochs the model trained for. This is the history.epoch. 
*   A dictionary that features not only the loss but also the metrics specified by the user measured at the end of each epoch for the training set as well as the validation set. This is history.history . 

We can use the ‘history.history’ dictionary to generate a ‘pandas DataFrame.’ Once the DataFrame has been generated, we use a plotting method known as plot() and get a visual representation of the model’s learning progress. The entire process has been demonstrated below: import pandas as pd import matplotlib.pyplot as plt pd.DataFrame(history.history).plot(figsize=(8, 5)) plt.grid(True) plt.gca().set\_ylim(0, 1) # set the vertical range to \[0-1\] plt.show() The output of this block of code is as follows: ![](image_rsrc9TM.jpg)With visual cues and graphical representation of data, we can perform a much better evaluation of the model. From this graph, we can understand that the metric of accuracy for both training and validation sets increases steadily over each epoch. On the other hand, the loss measured for the training set and validation set decreases over each epoch. This indicates that training is going well for the neural networks. Similarly, judging from the proximity of the training and validation curves, we can easily deduce that there isn’t much overfitting to worry about. However, there are times when a user is just not satisfied with the performance of his machine learning model. If you come across such a scenario, then the first thing you can do is tweaking the hyperparameters. For instance, you can try to tune the learning rate of the model. If tuning the hyperparameters does not make any difference in the performance of the model, then you should try using some other optimizer. However, if you change the optimizer, you should also tune the hyperparameters as well. If you still do not see any satisfactory change in the model’s performance, then you can go ahead and change the hyperparameters of the model itself. Here is a list of some of the hyperparameters that can have a greater  impact on the performance of your model when tuned: 

*   The total number of layers in the machine learning model. 
*   The total amount of neurons that each layer contains. 
*   The type of activation sequences being used for each of the hidden layers in the model. 

You can also focus on tuning hyperparameters of the dataset itself such as the batch size (you can specify a batch size when calling the fit() method by using the argument batch\_size , the default value of this argument is 32). Once you have gained the desired accuracy on the validation set and the performance is satisfactory, it is time to test how the model actually performs in the real-word by generating predictions on unseen data (the testing dataset). By doing this, we can get an idea of how well does the model generalizes what it learned to data that it has never come across before. To test the model, we will use a method known as evaluate() as shown below: \>>> model.evaluate(X\_test, y\_test) 10000/10000 \[==========\] - 0s 29us/sample - loss: 0.3340 - accuracy: 0.8851 \[0.3339798209667206, 0.8851\] Getting decreased performance margins on testing sets as opposed to validation sets is pretty common. This is because, on validation sets, we tune the hyperparameters to get the maximum accuracy and performance. By contrast, the hyperparameters of the testing set are not tuned in any way. The reason why we do not perform any hyperparameter tuning of the testing set is that the results which we will obtain the real-time performance of the model in the real-world. If we tune the hyperparameters, the results will be optimistic rather than realistic, and we will not get an accurate generalization error. Using the Model to Make Predictions At this stage, the model has been trained, validated, and evaluated on unseen data as well. If the model passes all these steps, it is finally time to take it out and put it to use in the real world, which is to generate predictions when seeing data. Since we do not have any new data instances to use the model on, we will be using the first three instances of the testing set instead. We will be using the prediction method which is ‘predict()’ to generate the predictions regarding the data as shown below: \>>> X\_new = X\_test\[:3\] \>>> y\_proba = model.predict(X\_new) \>>> y\_proba.round(2) array(\[\[0. , 0. , 0. , 0. , 0. , 0.03, 0. , 0.01, 0. , 0.96\], \[0. , 0. , 0.98, 0. , 0.02, 0. , 0. , 0. , 0. , 0.    \], \[0. , 1. ,  0. ,0. , 0. , 0. , 0. , 0. , 0. ,0.              \]\], dtype=float32) From the resulting array, we can clearly see that the machine learning model generates one prediction per class, i.e., from the classes 0 to 9, the model gives one probability per class for each instance. To elaborate, we can see that in the first array, the model predicts that the data instance has a 96% chance of being the class 9 item (which are ankle boots), a 3% chance of being the class 5 item (which are sandals) and a 1% chance of being the class 7 item (which are sneakers). Similarly, in the second data instance, the model predicts that the figure is actually the item represented by class 3. In the third instance, the model predicts that the figure is the item represented by class 2. In other words, the model ‘supposes’ that the image represented by the first data instance, it belongs to the ‘footwear’ category of fashion items. The model believes that the item in the image is ankle boots, but there’s a slight possibility that the item can be a sneaker or sandals instead, although that is unlikely. If you want the model to only display the class which is predicted to  have the highest probability, then we can use the ‘predict\_classes() ’ method as shown below: \>>> y\_pred = model.predict\_classes(X\_new) \>>> y\_pred array(\[9, 2, 1\]) \>>> np.array(class\_names)\[y\_pred\] array(\['Ankle boot', 'Pullover', 'Trouser'\], dtype='<U11') We can see that the classifier has been successful in accurately classifying all of the images represented by the first three data instances correctly. \>>> y\_new = y\_test\[:3\] \>>> y\_new array(\[9, 2, 1\]) ![](image_rsrc9TN.jpg)Creating a Regression MLP Using Sequential API Up to this point, we have discussed how to create, train, evaluate, and test the predictions of a machine learning model using the Sequential API with classification MLP. We can also the Sequential API to build a model based on the Regression MLP which will be the main point of discussion of this section. To make things simple, brief, and interesting, let’s use the California housing dataset (a regression task) and build a regression neural network to make predictions regarding housing prices. In order to keep it simple, we will reuse the function fetch\_california\_housing() from the Scikit-Learn toolkit, and in  this way, we can easily load the dataset. However, keep in mind that this particular dataset is comparatively simpler than the one we used in the second chapter of this book. This is because the dataset doesn’t have any ocean\_proximity feature and only has numerical features. Similarly, there are no values that are missing from the dataset so the task is relatively easy and simple, thus we won’t have to broaden our discussion too much. Once we have loaded the dataset, we need to slice it up into three portions, a training set for training the model, a validation set for validating the training, and a testing set to test the actual performance of the model. After that, we need to go ahead and scale the features as well: from sklearn.datasets import fetch\_california\_housing from sklearn.model\_selection import train\_test\_split from sklearn.preprocessing import StandardScaler housing = fetch\_california\_housing() X\_train\_full, X\_test, y\_train\_full, y\_test = train\_test\_split( housing.data, housing.target) X\_train, X\_valid, y\_train, y\_valid = train\_test\_split( X\_train\_full, y\_train\_full) scaler = StandardScaler() X\_train = scaler.fit\_transform(X\_train) X\_valid = scaler.transform(X\_valid) X\_test = scaler.transform(X\_test)  
For most of the process in building a model that has a regression MLP by using the Sequential API, the steps are essentially the same as for building a model that uses Classification MLPs. In other words, the process of training, evaluating, and testing the model is the same as what we have done in the previous sections. But not everything’s the same, here’s a list of some of the major differences: 

*   The output layer of a model using Regression MLPs only consists of a single neuron (this is because the model is  supposed to predict only one value). 
*   The output layer of such a model does not use any activation function. 
*   The loss function used in this model is MSE (Mean Square Error). 

Since we are dealing with a dataset that has a lot of useless information and data we do not need (such types of datasets are known as “noisy”), we have to clean it before we can use it with the model. This can be done by using a hidden layer that doesn’t necessarily have too many neurons so that we also avoid any overfitting. This process has been shown below along with the compilation and testing steps as well: model = keras.models.Sequential(\[ keras.layers.Dense(30, activation="relu", input\_shape=X\_train.shape\[1:\]), keras.layers.Dense(1) \]) model.compile(loss="mean\_squared\_error", optimizer="sgd") history = model.fit(X\_train, y\_train, epochs=20, validation\_data=(X\_valid, y\_valid)) mse\_test = model.evaluate(X\_test, y\_test) X\_new = X\_test\[:3\]                              # pretend these are new instances y\_pred = model.predict(X\_new) 

Chapter 5 Addressing the Problems Faced When Training Deep Neural Networks ![](image_rsrc9SG.jpg)In the previous chapter, we learned how to use Keras with TensorFlow in creating a model based on Artificial Neural Networks. However, we didn’t create a simple machine-learning model. Instead, it was a deep learning model, albeit shallow. This model only consisted of a handful of hidden layers making such a model unsuitable for large and complex problems. In this chapter, we will take things a little further and explore how we can create deep neural networks and solve problems with them. However, there’s a reason why not everybody is adopting deep neural networks in their models and that’s because such a model comes with its own problems. But in this case, the problems are very hard to deal with and often discourage computer and data scientists, the main one’s being: 

*   The vanishing gradients or the exploding gradients problem. There’s a chance that the user will be faced with a complication where the gradients of the model either continuously grow smaller or continuously grow larger during the training process when they flow backward through the Deep Neural Network. This problem makes it very difficult to train the layers. 
*   One of the most common problems is the shortage of training data that can properly train a large network such as this one. Even if we gather enough data, there’s still the problem of labeling it. It either becomes too costly to label the data or we simply cannot do it because of the sheer  volume. 
*   The process of training is exponentially slow. 
*   A model such as this generally has a very large amount of parameters, typically millions. With so many parameters, the risk for the model overfitting on the training dataset rises immensely. The chances of risk are further increased when the training set does not have an adequate number of data instances or if the data within the set is noisy. 

Hence, we will also be addressing how to tackle these problems and create a model that uses deep neural networks. Dealing with the Vanishing and Exploding Gradients Problem Before we discuss the vanishing and exploding gradient problem, we must first understand the backpropagation algorithm. The working of this algorithm involves traveling from two major types of layers, the output layer to the input layer. As it travels between these layers, the backpropagation algorithm ‘propagates’ the corresponding error gradient as well. The algorithm basically considers each individual parameter of the network and calculates the gradient of the cost function accordingly. After the calculations have been done, each parameter is then updated using a ‘Gradient descent step’ by the algorithm by factoring in the computed gradients. Generally, when the algorithm moves to the lower level layers, the gradients tend to shrink, becoming smaller with each passing layer. So, the lower level layers which are supposed to be updated through the Gradient Descent step, are left unchanged (their connection weights in particular). This, in turn, results in the training of the neural network without any satisfactory results. This phenomenon is commonly referred to as the ‘vanishing gradients problem .’ There are times when the gradients moving through layers, instead  of shrinking, keep on increasing in size, becoming larger and larger. At some point, the weights of the layers start to receive an unreasonably big gradient update by the algorithm, leading it to diverge. This phenomenon is known as the ‘exploding gradients problem ’ and is more common in recurrent neural networks. In this way, neural networks that are large and deep have their performance and capabilities compromised by having unstable gradients causing some layers to learn faster, and some to learn very sluggishly. This results in the uneven training speed for the model. This gradient problem isn’t something that surfaced recently; on the contrary, the gradient problem was observed way back in the early days of artificial neural networks. It was due to this that deep neural networks were largely abandoned and dismissed in the 2000s. At first, nobody could give a solid reason as to why this problem arises in deep neural networks. Still, in 2010, a paper published by ‘Xavier Glorot’ and ‘Yoshua Benigo’ attempted to explain this bizarre behavior. According to the authors of this paper, they brought the attention of the community towards two aspects: 

*   The combination of logic sigmoid activation function that was popular at that time. 
*   The weight initialization technique (using a mean of 0 for the normal distribution and the mean of 1 for standard deviation). 

They stated that by using this particular initialization technique and activation function, each layer has a higher variance in their corresponding outputs as compared to the variance observed in the inputs of the same layers. This trend of increasing output variance is observed as we go further into each layer of the neural network and only stops once the activation function finally saturates at the top-most layers of the network. Moreover, the activation function saturation is also negatively affected by the logistic function which features a mean of 0.5 (instead of 0). This is because, in deep neural  networks, a logistic function having a mean of 0.5 is slightly outperformed in terms of both behavior and effects by a ‘hyperbolic tangent function’ that features a mean of 0. Here’s a visual representation of the saturation of the logistic function activation. ![](image_rsrc9TP.jpg)From this graphical representation, we can easily understand that whenever the input enlarges either positively or negatively, it results in the saturation of the logistic function at 1 (for positive enlargement) and 0 (for negative enlargement) along with a derivative which is very close to 0 but not actually 0. So, when the phenomenon of backpropagation is triggered, there is no gradient for it even to propagate. Even if there is a small gradient available to propagate, it will just get diluted as the backpropagation gradient descent moves to the top layers. Hence, despite the presence of gradients, they will not be propagated through the lower layers. Glorot and He Initialization In this section, we will discuss the method which was proposed by ‘Glorot’ and ‘Bengio’ that can have a significant impact on mitigating the gradients problem in deep neural networks. The method proposed by these people details the need to use a signal to indicate  a proper flow through the neural network in both directions (forward direction for generating predictions and the backward directions for backpropagation of gradients). The important thing is here is to maintain the integrity of the signal such that it does not become too weak and disappear or becomes too loud causing explosion and saturation of gradients. To ensure the integrity and proper flow of the signal, according to the authors of the paper, each layer’s output variance needs to be equal to the variance in the inputs of the same layer. Moreover, the variance of the gradients when they are in a state of movement in the forward direction should also be equal to the variance of the same gradients when they are in a state of flowing backward through the layers. But this requirement cannot be guaranteed (to be more precise, the equal variance in both states cannot be guaranteed) unless the layer in question features the same number of inputs as its total neurons. In light of this restriction, the authors of the paper have devised a practically feasible solution. According to them, we need to simply initialize the connection weights of each layer randomly by using the following equation (which is commonly known as Glorot Initialization) : ![](image_rsrc9TR.jpg)(where  fanavg = (fanin + fanout )/2) This is one of the tricks that brought deep learning back from its place of abandonment to a state where it can be utilized. The Glorot Initialization technique not only speeds up the process of training of the deep neural network but it also erases the vanishing and exploding gradient problems. Using the ReLU activation function with an initialization strategy is known as ‘He Initialization.’ Here’s a table showcasing the appropriate activation functions for different initialization strategies: 

| Initialization Strategy  || Activation Function  || Normal Variance (σ²)  |
| --- | --- | --- |
| Glorot Initialization  || None, tanh activation function, logistic activation function, softmax activation function  || 1/fan­avg  |
| He Initialization  || ReLu activation function and other variants such as ELU activation function  || 2/fan­in  |
| LeCun Initialization  || SELU activation function  || 1/fanin  |

In keras, the initialization strategy used by default is the ‘Glorot Initialization’ with a uniform distribution (that can be easily calculated by simply computing r = √3σ2 ). However, when we create a new layer, we can also change the initialization strategy being used by it, for instance, from Glorot initialization to He initialization. To do this, we will need to use the following statement: kernel\_initializer="he\_uniform" or kernel\_initializer="he\_normal" The way we would use this statement in the line of code detailing the creation of a new layer has been demonstrated below: keras.layers.Dense(10, activation="relu", kernel\_initializer="he\_normal") In this example, we are using the He initialization strategy with a uniform distribution formula based on fan avg . We can change the variable the uniform distribution formula depends on as well; for instance, instead of uniform distribution being based on the variable ‘fan avg ,’ we can base it on ‘fan in .’ To make this, we will need to use an initializer known as ‘VariableScaling’ as shown in the following lines of code: he\_avg\_init = keras.initializers.VarianceScaling(scale=2., mode='fan\_avg', distribution='uniform') keras.layers.Dense(10, activation="sigmoid", kernel\_initializer=he\_avg\_init) Using Keras to Implement Batch Normalization The methods we have discussed so far to deal with vanishing and exploding gradients are not perfect. This is because even if we use the He initialization strategy with a ReLU activation or even an ELU activation function, it will not guarantee that the gradient problem will come not come back and plague the neural network during training. As such, we need to discuss extra measures to deal with the gradient problem once and for all. In the year 2015, two notable figures in the field of Computer Vision Learning, Sergey Ioffe and Christian Szegedy proposed a method to deal with the gradient problem in deep neural networks, this method (or more accurately, technique) is known as ‘Batch Normalization.’ In the Batch Normalization technique, we basically use a specific operation in the deep learning model either before or after a layer’s activation function sequence. The purpose of this operation is to: 

*   Zero-center the inputs 
*   Normalize each of the inputs 
*   On each layer, employ two vector parameters, one parameter performs scaling and the other parameter performs shifting of the layer’s result (output). 

To put it in simple terms, the operation enables the deep learning model to identify the optimal scale and mean elements for each of its layer’s inputs. Let’s stop the theoretical discussion here and get straight on with implementing batch normalization with Keras. Just as how the Keras API simplifies the implementation of techniques, Batch Normalization is no exception. As we discussed, we need to implement operation either before or after the target layer’s activation function. In order to do this, we have to add a BatchNormalization layer just before the activation function of the target hidden layer or after the activation function of this hidden layer. Here’s a quick demonstration of a model in which, after converting the input images to 1D (flattening) a BatchNormalization layer has been included after every layer: model = keras.models.Sequential(\[ keras.layers.Flatten(input\_shape=\[28, 28\]), keras.layers.BatchNormalization(), keras.layers.Dense(300, activation="elu", kernel\_initializer="he\_normal"), keras.layers.BatchNormalization(), keras.layers.Dense(100, activation="elu", kernel\_initializer="he\_normal"), keras.layers.BatchNormalization(), keras.layers.Dense(10, activation="softmax") \]) We have only used a simple and small model to implement batch normalization. Although it won’t make much of a difference in the performance of this specific model, for larger and deeper neural network models, the difference will be immense. For now, let’s check a model summary of this example using the summary method model.summary() : \>>> model.summary() Model: "sequential\_3" \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ Layer (type) Output Shape Param # \================================================ flatten\_3 (Flatten) (None, 784) 0 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ batch\_normalization\_v2 (Batc (None, 784) 3136 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ dense\_50 (Dense) (None, 300) 235500 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ batch\_normalization\_v2\_1 (Ba (None, 300) 1200 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ dense\_51 (Dense) (None, 100) 30100 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ batch\_normalization\_v2\_2 (Ba (None, 100) 400 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ dense\_52 (Dense) (None, 10) 1010 \================================================ Total params: 271,346 Trainable params: 268,978 Non-trainable params: 2,368 From this model summary, we can see that each of the BatchNormalization layers basically provide additional parameters to the model. These are a total of four parameters (γ, β, μ, and σ) for each input. Interestingly enough, the μ and σ parameters are essentially ‘moving averages’ and backpropagation does not affect these particular parameters. This is why Keras classifies these parameters as non-trainable parameters. If we focus our attention on the first BatchNormalization layer only, then we will notice that only two of its parameters are affected by backpropagation during training while the other two are not, as shown below: \>>> \[(var.name, var.trainable) for var in model.layers\[1\].variables\] \[('batch\_normalization\_v2/gamma:0', True), ('batch\_normalization\_v2/beta:0', True), ('batch\_normalization\_v2/moving\_mean:0', False), ('batch\_normalization\_v2/moving\_variance:0', False)\] Whenever we create a BatchNormalization layer and add it to the model, the layer is accompanied by two operations as well that is called upon by the Keras API during each epoch of the training process. The purpose of these operations is the updating of the last two parameters of the BN layer (the ‘moving averages’ parameters). Moreover, we are using Keras specifically with the TensorFlow backend. Hence the operations that are generated by the BN layers are essentially TensorFlow operations. \>>> model.layers\[1\].updates \[<tf.Operation 'cond\_2/Identity' type=Identity>, <tf.Operation 'cond\_3/Identity' type=Identity>\] In the paper published that highlighted the importance of the Batch Normalization technique, an interesting topic was the position at which the batch normalization layers were implemented. The authors considered that implementing the batch normalization layers before the layer’s activation function was better than implementing it after the activation function (we implemented the BN layer after). However, this topic is still debated upon and is considered as a preference rather than an optimizing approach. Moreover, the effectiveness of the BN layer’s position of implementation can depend on the circumstances in which it is being used, the specific model, and the task at hand. If you want to follow the approach used by the authors of this paper, i.e., implementing the BN layer before the hidden layer’s activation function, then you will first have to take out the hidden layer’s activation function. After removing them, you need to add these as distinct layers after the implementation of the BN layers. In addition, the BN layer features an offset parameter for each input, hence you might need to scratch the previous layer’s bias term as well. To do this, you can use the following statement when adding the hidden layer: use\_bias=False The following lines of code demonstrate the proper way to implement a BatchNormalization layer using Keras before a hidden layer’s activation function: model = keras.models.Sequential(\[ keras.layers.Flatten(input\_shape=\[28, 28\]), keras.layers.BatchNormalization(), keras.layers.Dense(300, kernel\_initializer="he\_normal", use\_bias=False), keras.layers.BatchNormalization() , keras.layers.Activation("elu"), keras.layers.Dense(100, kernel\_initializer="he\_normal", use\_bias=False), keras.layers.BatchNormalization(), keras.layers.Activation("elu"), keras.layers.Dense(10, activation="softmax") \])  
Dealing with Problem of Data Shortage When Training Deep Neural Networks So despite the challenges, hurdles, and other difficulties, you have managed to create a model that has a deep neural network. You have also addressed the gradient problems so you’re good to go and want to proceed with training the model. But here’s the next problem you will most likely face, and that is procuring enough data to train the model from scratch. In reality, we cannot gather enough data that is adequate to train the model completely. Even if we do have a sizable amount of data, labeling it will cost too much or it is just impossible with human resources alone. In this section, we will discuss a potential workaround for the problem of training deep neural networks. Using Layers That Have Been Already Trained You should carefully consider the nature of the task you want the model to handle. Once you have gotten a good understanding of what problems you want your model to solve, you can find another neural network already trained on similar tasks and leverage its functionality. In other words, we are reusing the lower-level layers of an already trained neural network for our model. This particular technique is commonly referred to as “Transfer Learning .” Using the transfer learning technique will not help make the training process relatively easier; it will also speed it up considerably. Moreover, the volume of data required to train a deep neural network that employs the transfer learning technique is significantly  lower than the original requirement. Let’s say that we want to create a deep neural network whose job would be to handle a classification task, particularly one where it has to classify through a stream of images into a specific category of vehicles. Since we are going to be using the transfer learning technique, let’s say that we have also found another existing deep neural network that was trained to perform the same type of classification task but more diverse. For example, it can classify images into a hundred different categories of everyday objects. Since the tasks are fairly similar to each other, we can use some parts of this deep neural network and use it for our particular model. Before we dive into more details, let’s first take a look at the figure shown below to develop a basic understanding of the process works: ![](image_rsrc9TS.jpg)We should always replace the output layer of the model that has already been trained because this layer is useless to us. Similarly, the upper layers of the pre-trained model are also likely to be useless. This is because the features of these parts of a model are designed and tuned to get the desired results for a particular task, hence making it useless for any other task. So, the only thing we can use is the lower layers of the pre-trained model since their features  are likely to be useful for our model considering the similarity of the task (classification). Hence, the first thing to remember when using the transfer learning technique is to find out the optimum number of layers that you can reuse. Also, the number of layers you can probably reuse depends on how similar the two tasks are. If the tasks are incredibly similar or very closely related, then you can probably reuse all of the hidden layers while excluding the output layer. Let’s say that based on your judgment, you have chosen the number of layers that you think are safe to reuse, but still, the performance of your model remains lackluster and you don’t have a huge amount of training data either. At this point, we use the trial and error approach. Eliminate the top-most hidden layers you reused in your model and freeze the remaining ones, then try again. We can repeat this process until we find out the number of layers that, when reused, provided optimal performance. However, if you access to a sizable amount of training data, then instead of eliminating the top-most hidden layers of the model, you should consider replacing them with newly trained ones or even consider adding more hidden layers on top. Performing Transfer Learning Using Keras Now let’s understand how to implement transfer learning using an example we are already familiar with, the Fashion MNIST dataset. Let’s consider that instead of 10 classes, the Fashion MNIST dataset only contained eight classes (to be precise, we are excluding the class representing sandals and the class representing shirts). Someone used this dataset to train their neural network model using Keras and surprisingly got an accuracy of about 90%. For now, we will be referring to this model as ‘Model X.’ Now let’s say that we are supposed to deal with a task similar to what Model A was designed to handle. In this case, we want our model to distinguish sandals and shirts from the images we give them into  separate categories. We want the model to perform a binary classification task which is similar to the classification task performed by Model X. However, we are short on data required to train our neural network, to be precise, our dataset consists of a total of 200 images that are labeled. Let’s name the model we want to train from scratch to perform binary classification as ‘Model Y.’ Theoretically, if Model Y is trained with the same parameters and overall architecture as Model X, the resulting performance would be surprisingly good (about 92.7% accuracy. However, Model Y is only dealing with the classification of 2 classes as opposed to Model X classifying eight separate classes. So it only makes sense that we expect the performance to be even better considering the simplicity of the task. Since we took the same blueprints of Model X for Model Y and seeing how it performed so well, we can only conclude that the tasks are strikingly similar to each other. Thus, the technique of transfer learning is applicable here. So let’s proceed with transferring the pre-trained layers of Model X and reuse them in Model Y. First things first, we need to load up Model X and proceed to build a new model by taking Model X’s layers. In this case, since the nature of the tasks are very similar, we can reuse every layer of Model X for Model Y except for the output layer (as explained in the previous section) : model\_X = keras.models.load\_model("my\_model\_X.h5") model\_Y\_on\_X = keras.models.Sequential(model\_X.layers\[:-1\]) model\_Y\_on\_X.add(keras.layers.Dense(1, activation="sigmoid")) From the lines of code shown above, it is easily understood that ‘model\_X’ and ‘model\_Y\_on\_X ’ now have a common denominator. That is, they share layers. So, when we train model\_Y\_on\_X , the layers on the original model\_X will be  affected by the training as well. If you want the model from where you are siphoning the layers to remain unaffected by the training and retain its original state, then you will have to clone the Model X before reusing the layers. Cloning is pretty simple and straightforward. The two main things we have to clone are the model’s architecture and then its connection weights. To do this, we will be using the clone method which is clone\_model() . The cloning of model\_X ’s architecture and weights has been demonstrated below: model\_A\_clone = keras.models.clone\_model(model\_A) model\_A\_clone.set\_weights(model\_A.get\_weights()) Now that we are finished with cloning the pre-trained model, we can proceed to train the Model Y for its task of binary classification. However, before we proceed, we need to be careful of the initialization of our output layer. In this case, the output layer was initialized randomly, so there are high chances that the result displayed by the model will contain errors. In turn, this might lead to the spawning of big error gradients that will eventually destroy the weights we have reused. A simple and effective way to tackle this problem is just to freeze the layers we have reused for a duration of few epochs during training. This will give the newly created layers of the model some time to learn weights. To freeze the layers, we just need to set the attribute of trainable to a value of 0, i.e., False, and then proceed to compile the model. The entire process has been shown below: for layer in model\_B\_on\_A.layers\[:-1\]: layer.trainable = False model\_B\_on\_A.compile(loss="binary\_crossentropy", optimizer="sgd", metrics=\["accuracy"\]) When freezing and unfreezing the layers, always remember to  compile the model afterward every time. Now we let the model train for a couple of epochs and then unfreeze the layers by switching their trainable attribute to ‘True.’ After we unfreeze the layers, we must compile the model then let it continue its training. In this way, it can tune the layers which have been transferred from Model X to perform the task (binary classification) of the new Model, i.e., Model Y. In addition, to mitigate the chances of failure or errors, we should always lower the rate of learning whenever we unfreeze models. If the layers are being trained at a normal pace, this might cause a discrepancy in the learning rates of the reused layers and the new layers, so it’s best to lower the learning rate so that we can avoid wounding the reused weights. history = model\_B\_on\_A.fit(X\_train\_B, y\_train\_B, epochs=4, validation\_data=(X\_valid\_B, y\_valid\_B)) for layer in model\_B\_on\_A.layers\[:-1\]: layer.trainable = True optimizer = keras.optimizers.SGD(lr=1e-4)                # the default lr is 1e-2 model\_B\_on\_A.compile(loss="binary\_crossentropy", optimizer=optimizer, metrics=\["accuracy"\]) history = model\_B\_on\_A.fit(X\_train\_B, y\_train\_B, epochs=16, validation\_data=(X\_valid\_B, y\_valid\_B)) Let’s evaluate how the model performs after using the transfer learning technique. \>>> model\_B\_on\_A.evaluate(X\_test\_B, y\_test\_B) \[0.06887910133600235, 0.9925\] From the above evaluation result, we can see that the overall  accuracy of the model on the testing set data is a whopping 99.25%. If we consider the accuracy of the model before the use of transfer learning, then we have successfully reduced the rate of error from 2.8% to about 0.7% which is a very big improvement. However, it is advised that the transfer learning technique be only used for large and deep neural networks because small neural networks can only learn a handful of very specific patterns. Hence, the layers used from such models would be practically useless for other small neural networks. Dealing with the Problem of Slow Training It’s no surprise that building a deep neural network with many connections and weights will also exponentially increase the time required to train it fully. Let’s say that you have successfully built a deep neural network by overcoming the gradient problem. Next, you resolved the lack of adequate training data by using transfer learning, but the next problem you’ll face is very slow training speeds. You might not have noticed it but there are four techniques discussed in the previous sections that also have an effect of increasing the training speed of deep neural networks. To be specific, these techniques are: 

*   Employing a good initialization strategy 
*   Choosing and using the most suitable activation function 
*   Batch Normalization 
*   Transfer Learning 

While these four techniques are primarily used to solve some other problems plaguing deep neural networks, they also positively affect the speed at which the network trains itself. In this section, we will be discussing a method that is concerned with  primarily boosting the overall training speed of the deep neural network. This method involves using an optimizer that is faster and more efficient than the standard Gradient Descent optimizer we are used to seeing. The identity and properties of an optimizer depend on the algorithm it uses. In this section, we will discuss four of the most popular and most effective algorithms (except for AdaGrad) for optimizers: 

1.  Momentum Optimization 
2.  Nesterov Accelerated Gradient 
3.  AdaGrad 
4.  RMSProp 

Momentum Optimization The core concept of momentum optimization was first introduced in the year 1964, but let’s leave the boring history stuff for now and get straight into how it works. By the name itself, we can get a rough idea that the fundamental working of this algorithm has something to do with momentum. Let us look at an analogy to understand momentum optimization. Let’s say a bowling ball is rolling down a sloped surface that is smooth. During the time the ball rolls, the initial momentum will be considerably slower. Still, as it keeps on rolling down the sloped surface, the ball will gain momentum at a considerably fast pace until it is bound by the terminal velocity which is due to any type of resistance (rolling friction and air resistance). Momentum optimization works in the same way; it starts slow but gains speed quickly until it reaches the maximum limit to where it can speed up the training process. In comparison, the way Gradient Descent works is by taking short steps at regular intervals down the same smooth sloped surface. This means that momentum optimization will be the first to complete training the entire network as opposed to gradient descent. Hence,  momentum optimization will work considerably faster than Gradient Descent for deep neural networks. Now let’s move on to the mathematical aspect of these two algorithms and understand how they work. First off, Gradient Descent is an algorithm that primarily works by performing updates on the weights (denoted by θ) and so does momentum optimization. But in Gradient Descent, the update is calculated in a series of arithmetical operations. Firstly, the algorithm multiplies the weights ∇ θJ(θ) with the defined learning rate (denoted by ‘η’) and then directly subtracts it with the cost function’s gradient ‘J(θ).’ The resulting equation is as follows: θ ← θ – η∇ θJ(θ) However, the major flaw of this algorithm is that it does not consider the values of the preceding gradients. This is exactly the reason as to why using Gradient Descent results in an exponentially slow training process. On to momentum optimization which, unlike Gradient Descent, gives due importance to the preceding gradients (which would be ignored by Gradient Descent). To elaborate, on every iteration, it takes the ‘momentum vector (which is denoted by m )’ and subtracts the local gradient from it. Then it updates the weights by simply adding the new value of the momentum vector to them. In simpler terms, the gradients are accelerating (not to be confused with speed). The resulting mathematical equation is as follows: 

1.  Subtracting the local gradient from momentum: 

m ←βm − η∇ θJ(θ) 

2.  Updating the weights by adding the resulting momentum to it: 

θ← θ + m However, if we let things be, the momentum will eventually become larger and uncontrollable. Thus, the algorithm also employs a kind of mechanism to stimulate friction to keep the momentum in check by using a hyperparameter ‘β’. This hyperparameter is referred to as ‘momentum ’ and it can be set to any value between 0 (which indicates maximum friction) and 1 (which indicates no friction). Generally, the value of this hyperparameter is set to 0.9. So, the bigger the momentum, the larger the weight update. This can also be seen as ‘terminal velocity’ referred to in the analogy. Keras makes it very easy and simple for users to implement momentum optimization into deep neural networks. The following line demonstrates how it can be implemented: optimizer = keras.optimizers.SGD(lr=0.001, momentum=0.9) Momentum optimization does have a drawback but it’s not that dire which might require careful consideration before use. When we use momentum optimization, we are also using a hyperparameter along with it. This means that we now have an additional hyperparameter that needs to be tuned, but it has been observed that by keeping it at 0.9, the optimizer works pretty well. Nesterov Accelerated Gradient Notice that momentum and acceleration are concepts that are closely related to each other. The same is the case with the Nesterov Accelerated Gradient; it is very similar to momentum optimization but has some key changes which make it perform even better. To be more precise, the Nesterov Accelerated Gradient method is an optimizer which is basically a variant of momentum optimization. The Nesterov Gradient Method (some might even refer to this as Nesterov momentum optimization) works by calculating the cost function’s gradient and performs the same arithmetic operations as momentum optimization. But the difference here is that instead of calculating the cost function’s gradient at its local position (this is  referred to as θ), it considers the position ahead in the same direction as that of the momentum. Mathematically, this new position of the cost function’s gradient can be expressed as θ + βm. Here’s the mathematical expression: 

1.  Subtracting the gradient at a position in the direction of momentum: 

m  ← mβ - η∇ θJ(θ) 

2.  Adding the resulting momentum to the weights: 

θ ← θ + m This change might seem insignificant or just underwhelming but in reality, the difference in training speed is monumental as compared to momentum optimization. The reason behind this is that at any given moment, the momentum vector will be directly pointing towards the optimum point. This makes the gradient updates more accurate as compared to momentum optimization and in essence, less time consuming for the gradients to come back in the right direction. The following figure demonstrates how the Nesterov momentum optimization updates the gradients as compared to the updates done by standard momentum optimization. ![](image_rsrc9TT.jpg)On the surface, this might look like a small change with no big impact. But the thing is, these small changes in the direction of the  gradient updates towards the optimum eventually add up and then affect the training speed monumentally. This is why Nesterov momentum optimization is faster and more efficient than standard momentum optimization. The implementation of the Nesterov Accelerated Gradient method is the same as momentum optimization in Keras, all you need to do is just add a small statement, i.e., nesterov=True when you define the SGD optimizer and you’re done. The following line of code demonstrates the implementation of the Nesterov Accelerated Gradient: optimizer = keras.optimizers.SGD(lr=0.001, momentum=0.9, nesterov=True) AdaGrad To understand the AdaGrad optimizer, we must first understand which deficiency of Gradient Descent does it rectify or improve. The elongated bowl problem is a popular analogy used to describe the shortcomings of Gradient Descent in a manner that is easy to understand so let’s use this. Instead of explaining the whole scenario, we will only stick to the important parts. The elongated bowl problem explains that Gradient Descent will aim to find the steepest slope and quickly go down. However, this slope does not direct the gradient updates in the right direction (the optimum), but once it reaches the end of the steepness, it then moves slowly with small steps towards the bottom of the valley. AdaGrad uses an algorithm that can change the direction of Gradient Descent towards the optimum a bit earlier. It does this by simply taking the gradient vectors and then downscale them according to the dimensions that are the steepest. The AdaGrad optimizer also has a hyperparameter which is the learning rate. The mathematical explanation of AdaGrad is too quirky and complex for this discussion so we will leave it out. However, if you’re  interested in how it works, then you can always look it up on the internet and you’ll find more than enough information. One thing you must remember when using AdaGrad is that the learning rate of the neural network using this optimizer seems to diminish over time (i.e., decay). This learning rate decay is harsher for steep dimensions as compared to other dimensions that have a relatively gentler slope. Moreover, AdaGrad is known for its risk of slowing down considerably after only a short amount of time before even reaching the global optimum. But this doesn’t make it particularly bad. For instance, the hyperparameter used by the AdaGrad optimizer doesn’t need much tuning. However, the overall trend in the impactfulness of optimizers dictates that AdaGrad does more harm than good. It can be very useful for shallow neural networks or small neural networks performing Linear Regression tasks, but it is not recommended to be used to train deep neural networks. RMSProp In AdaGrad, we learned that the algorithm is unsuitable for use in large and deep neural networks because of how quickly it starts to slow down never seems to converge to the optimum. RMSProp is a better and usable variant of the AdaGrad optimizer as it eliminates the flaws AdaGrad has. The way RMSProp tackles the flaw of slowing too quickly and never converging to the optimum is by considering only those gradients from the most recent iterations (unlike AdaGrad which considered all of the gradients from the beginning of the network’s training). The algorithm accomplishes this by employing exponential decay. The decay rate is a hyperparameter for the RMSProp optimizer but it does not need much tuning. Although you can set it to any value between 0 and 1, the default value (0.9) has been seen to work quite well, and often, you will not need to tune the hyperparameter even if it’s at the default value. Implementing an RMSProp optimizer using Keras is very simple and easy. The correct way has been demonstrated below: optimizer = keras.optimizers.RMSprop(lr=0.001, rho=0.9) In the line of code shown above, the argument at the end (rho=0.9) refers to the hyperparameter of exponential decay. Apart from tasks that are basic and simple, the RMSProp optimizer is observed to perform way better than AdaGrad for complex tasks and deep neural networks. Dealing with the Risk of Overfitting of Deep Neural Networks We have now come down to the last major problem faced in using deep neural networks, the risk of overfitting the model when the network has so many parameters. In standard deep neural networks, you will find that most of them generally have hundreds of thousands of parameters and some may even feature more than a million parameters. Although this gives the model an insane amount of capacity for performing very complex tasks and processes highly complex datasets, the problem of overfitting still looms around. In other words, the flexibility that arises with using so many parameters comes at a price, a higher chance for the network to overfit to the dataset. One of the most commonly used methods for tackling this problem is ‘Regularization .’ In the previous chapter, we discussed some techniques and methods that can be used as regularizers too. Even the technique of ‘Batch Normalization’ is somewhat for a good regularizer (although the main purpose of creating this method was to handle the gradient problems). However, we will now shift our focus to techniques that are dedicated to regularization and are currently popular for their functionality. These regularization techniques are as follows: 

*   l1 and l2 regularization 
*   Dropout regularization 
*   Max-norm regularization 

l 1 and l 2 Regularization This type of regularization is mainly used to constrain the connection weights of the network in which it is being used (l2 regularization) or to create a sparse model with most of the weights set to 0 (l1 regularization). You can also use both of these regularizations together as well. For demonstration purposes, let’s implement the l2 regularization on some connection weights of a dense layer in Keras while keeping the ‘regularization factor’ to a value of 0.01: layer = keras.layers.Dense(100, activation="elu", kernel\_initializer="he\_normal", kernel\_regularizer=keras.regularizers.l2(0.01)) In the last line, we can see that the regularization method has been specified by using the kernel\_regularizer argument. The argument is followed by the l2() function detailing the use of l2 regularization. When we train the model, the function will return the l­2 regularizer on every training epoch. This way, the regularizer will be able to calculate the regularization loss. Once it has the value of the regularization loss, it then adds it to the concluding loss. To use l1 regularization, we simply need to replace the last argument with ‘keras.regularizers.l1() ’. This will return the l1 regularizer. If you want to use both l1 ­ and l2 regularization, we can do so by using the following argument ‘keras.regularizers.l1\_l2() ’. However, you must specify the regularization factors for both regularizers since we are using two regularizations. Usually, when applying regularizations to layers, the trend leans  towards applying this regularizer to every layer in the model’s neural network. But this trend is not for regularizers only, applying the same initialization strategy and the same activation function throughout the hidden layers is what you will end up doing in a deep neural network. But to do this, the approach a beginner or somebody with not much experience working with deep neural networks will simply repeat the arguments for the regularizer, activation function, and initialization strategy for every layer in the network. But this approach is not practical. Instead, it makes the resulting code more prone to error and unnecessarily lengthy. To avoid repeating the arguments over and over, we can either just use loops to refactor the code itself, or use the Python function ‘functools.partial() ’ as demonstrated below: from functools import partial RegularizedDense = partial(keras.layers.Dense, activation="elu", kernel\_initializer="he\_normal", kernel\_regularizer=keras.regularizers.l2(0.01)) model = keras.models.Sequential(\[ keras.layers.Flatten(input\_shape=\[28, 28\]), RegularizedDense(300), RegularizedDense(100), RegularizedDense(10, activation="softmax", kernel\_initializer="glorot\_uniform") \]) Dropout This is arguably the most popular and widely used regularizer specifically for deep neural networks due to how successful it is when implemented in a model. To get an idea of its practicality and its usefulness, consider this. If we use the dropout regularizer in a neural network that has been built by professionals with state-of-the-art architecture and resources, we can easily expect a 1% to 2%  increase in the model’s accuracy. At first glance, many people might consider this boost in accuracy as insignificant, but it’s quite the contrary. If the best deep neural network model features an accuracy of 96%, then a 2% boost would be really huge (this also means that the error rate of the model has dropped by 50%, i.e., from 4% error to 2% error). You might think that since the regularizer is good, there must be a very complex working it has to follow to get such results. But to the contrary, the dropout regularizer actually works in a pretty simple manner. When the dropout regularizer is implemented in a neural network, all of the neurons (input neurons), except for the output neurons, have a chance to be completely ignored during training. In other words, there’s a chance that any neuron can be dropped from the training process. The probability variable p specifies this chance. However, dropping a neuron does not mean that it is eliminated from the model. When a neuron is dropped, it will not be included in the current training epoch, but when the next epoch starts, the previously ignored neuron will be trained as well, and in its place, some other neuron will be dropped. This process of dropping during training keeps happening until the training ends. The probability p according to which each neuron has a chance of being dropped is actually the hyperparameter of the dropout regularizer itself. This hyperparameter is referred to as the ‘dropout rate .’ Generally, the hyperparameter is set to a value between 10% to 50% for the best results. However, it has been observed that if the regularizer is used in a recurrent neural network, the best value for the hyperparameter is between 20% to 30%. Similarly, if the regularizer is used in a convolutional neural network, it’s best to set the hyperparameter to a value between 40% to 50%.  The following figure demonstrates the process of dropping neurons: ![](image_rsrc9TU.jpg)It is a common question as to how does such a destructive and unconventional approach boosts the accuracy of a neural network. Let’s explore an analogy (although it might not be fully practical, the concept is well-delivered). Consider a company that follows the same routine happening in a neural network using the dropout regularizer. Each day, every employee has to toss a coin to decide if they are supposed to show up in the office or take the day off. Theoretically, such a company would have to adapt it’s working infrastructure accordingly. Every employee would have to be efficient in every expertise required in the organization. This means that there will be no longer a person who is designated solely for a critical task; every employee would be required to be capable of performing the same task as well. Moreover, employees would also have to extend their scope of cooperation to not just a handful of people but everyone in the organization. In such a way, even if one person who has expertise in the company’s critical tasks quits, the company wouldn’t be affected in any major way. On the contrary, the company would become quite resilient. Although this analogy is not very practical in real life, the theoretical results of such an approach are very much true for neural networks. To be more precise, in a neural network using the dropout regularizer, each neuron has no choice but to learn patterns as much as possible as it cannot rely on the neighboring neurons since they  can be dropped at any point. Moreover, excessive reliance on a handful of neurons to perform major tasks is also eliminated. So, even if there is a slight change in the inputs, the neurons will not be affected as much (they would become less sensitive). In conclusion, the resulting neural network is stern and robust that can generalize fairly well. We have kept the concept simple enough but there is one detail that cannot be simplified. Let’s say that we keep the hyperparameter p at 50%. This means that in the training phase, a neuron will end up being connected to double the input neurons as opposed to the validation phase or even generating predictions. This creates a disparity in what the connection weights would be during training and what they would be during actual testing. If we leave it be, then during testing, every neuron in the network will receive an input signal that is two times as big compared to what the neural network was trained with. This will lead to the poor performance of the model. To compensate this disparity, we have to take each connection weight of the neurons in the network and multiply it by a factor of 0.5. The dropout regularizer can be implemented in the neural network during its training phase by using Keras. For implementing the regularization technique, we will need to add a layer by using the ‘keras.layers.Dropout ’ statement. When the training process starts, random inputs will be dropped (i.e., set to 0) by the regularizer and the remaining inputs will be divided according to the probability set. Once the training is over, the job of the regularizer is also over. It simply gives the input to the succeeding layer. The following lines of code demonstrate the implementation of the dropout regularization just before each of the dense layers. The rate of the dropout has also been specified using the ‘rate= ’ argument (0.2). model = keras.models.Sequential(\[ keras.layers.Flatten(input\_shape=\[28, 28\]) , keras.layers.Dropout(rate=0.2), keras.layers.Dense(300, activation="elu", kernel\_initializer="he\_normal"), keras.layers.Dropout(rate=0.2), keras.layers.Dense(100, activation="elu", kernel\_initializer="he\_normal"), keras.layers.Dropout(rate=0.2), keras.layers.Dense(10, activation="softmax") \]) The dropout rate can be adjusted according to the overfitting observed on the training set. If the model overfits on the training set, then you can increase the dropout rate until its overfitting is eliminated. Similarly, if you set the dropout rate high from the start, then the neural network will most likely underfit on the training set. You will need to adjust the dropout rate by decreasing it until the neural network does not underfit. You will need to tune the dropout rate until you find the right value for your network. A cool trick is to note the size of your layers and then adjust the dropout rate for each layer separately according to their sizes. For instance, for large layers, you can increase the dropout rate and for layers that are small in size, you can decrease the dropout rate. In deep learning models that have been made with state-of-the-art resources and architectural skills, the dropout rate is primarily used only after the final hidden layer in the neural network. So if you think that a full dropout results in adverse effects for your model’s neural network, then you can try this trick as well. Max-Norm Regularization Max-Norm is another regularization technique that is fairly popular for deep neural networks. The way the Max-Norm regularization technique works is by intercepting the input connections for each neuron in the neural network and constraining their weights (w ) accordingly. Like the rest of the regularization techniques, to implement the Max-Norm regularization technique using Keras, we need to use the ‘kernel\_constraint ’ argument of the hidden layers;  we want to implement it to max\_norm() . After specifying an appropriate value to max\_norm() , the implementation process will be completed. The following lines of code demonstrate the implementation of Max-Norm regularization along with the specification of a value for max\_norm() : keras.layers.Dense(100, activation="elu", kernel\_initializer="he\_normal", kernel\_constraint=keras.constraints.max\_norm(1.)) 

Conclusion ![](image_rsrc9SG.jpg)We have successfully ended our journey here and we hope that it was as interesting and enjoyable for you as it was for the writer. We started by discussing the very basics of machine-learning and detailing some cool tips and tricks improving the quality of learning as compared to a standard guide book. Every chapter was structured and designed in a way that would not only ease the readability experience for the reader but also address topics that are of the utmost importance in the modern-day and age of machine learning. In the first half, we discussed techniques, projects, and demonstrations by primarily using Scikit-Learn. While in the later parts of the book, we shifted towards using Keras and TensorFlow for large and deep neural networks that are capable of handling very complex tasks. Throughout this transition between API’s several important tips and tricks have also been given to improve the user’s understanding of the concepts and also increasing the effectiveness when practicing what they learned. The book has pertained to providing only the best content with explanations that do not rely much on jargon but easy to understand analogies, especially in the last two chapters. Moreover, the way the chapters and the contents have been strategically placed, we effectively ensured that the reader would not get lost or overwhelmed by certain topics. The priority was to explain the background concepts earlier and then move on to the foreground discussing difficult concepts. 

References ![](image_rsrc9SG.jpg)Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow (2nd Edition) by Aurélien Géron 

TensorFlow  
Machine Learning ![](image_rsrc9SG.jpg)Advanced Guide to Learn Machine Learning With Scikit-Learn, Keras and TensorFlow ![](image_rsrc9SF.jpg)Benjamin Smith 

Introduction ![](image_rsrc9SG.jpg)How often do you sit there and wonder just what your computer is capable of? Are there any limits to what it can do? These days, computers do far more than we give them credit for, far more than just solving a few mathematical equations. In the last 50 years or so, computer programming has advanced to a level where it is now one of the top tools to help us save time and automate tasks, but that leads to another question – just how much can be automated? And how do we do it? Could a computer look at an image and identify, say, two people walking together along a beach? Does software have the ability to make accurate medical decisions, like trained medical professionals do? And can software make stock market predictions better than any human can? Some time ago, we would have been laughed at for asking questions like this, but now, given the advancements we’ve seen, these questions can easily be answered positively, and each of those questions, an implementation if you like, has one strategy in common. In recent times, we have seen plenty of theoretical advances. Add these to the latest technologies, and it’s easy to see why it is easy for anyone with a decent computer system to try to solve these hard problems. Well, okay, not anyone can do it but, at the end of the day, that’s what you want to do, and that’s why you are reading my book. Right? These days, programmers don’t need to know all the tiny details of a problem to solve it. Think about the conversion of text into speech. Traditionally, we would need to understand how the human vocal cords were structured, biologically speaking, and we would need to use code that was not generalized, was domain-specific, and had-designed if we wanted to understand what was being said. Now, we  can just write a piece of code that looks at multiple examples and works out the solution to the problem, provided it had sufficient examples and time. Another example would be identifying the sentiment in a Tweet or a piece of text as negative or positive. Perhaps you want a more granular look at the text, looking for specifics that indicate what the writer loves, hates, or likes, whether they are sad, angry, or happy. We would have scanned the text in the past, trying to locate specific words or punctuation that would indicate the sentiment. Now we use algorithms. Algorithms learn from the data they are given in much the same way as humans learn from their experiences.  We learn by reading books, seeing things, studying, talking to others, and from looking at the internet, among many other things. But how can a computer learn to think the same way a human does? While that cannot be definitively answered, the world’s best researchers have come up with lots of different intelligent programs.  In amongst all these programs, one thing has come to light – recurring patterns – and these have led to what we now call machine learning, a standardized field used for all sorts of problems. And that is what we are going to discuss here. The book is split into four distinct sections: 

1.  An introduction to machine learning, where you will learn what machine learning is, how it works, and the different approaches. We’ll talk about programming languages and also discuss deep learning and how it differs from machine learning. 
2.  TensorFlow, where you will learn everything you need to learn about the popular machine learning package. You will learn what it is, its architecture, the TensorFlow components, and finish with a couple of practical examples showing how it works. 
3.  Keras,  where you will learn what Keras is, what backends are, and how it compares to TensorFlow. You will also learn how to install it, learn how it relates to deep learning, and see a couple of practical examples. 
4.  Scikit-learn, where you will learn what it is about, how it works, installing it, and two projects for you to follow. 

The idea is to give you complete examples of how all three work and, throughout, you will also start to see who they work together. There are full installation instructions and full projects for you to follow along with so if you ready to start your machine learning journey, let’s dive in. 

Part One An Introduction to Machine Learning ![](image_rsrc9SG.jpg)

What is Machine Learning? ![](image_rsrc9TV.jpg)Most of us have heard of machine learning, but the vast majority still do not know what it is. I’m sure you do as you wouldn’t have picked up this book otherwise, but as a recap, here goes. Machine learning is an Artificial Intelligence subfield. Its primary goal is to learn to understand how data is structured and then get that data into a model that humans can understand and use. That’s it, really. Except there is far more to it than that, of course. Machine learning is a part of the computer science domain, but it has many differences from the traditional approaches. Traditional computing algorithms are made up of explicitly programmed instructions that computers use to solve problems or calculations. Machine learning differs because the algorithms are used to let the computer train on a set of data before using statistical analysis to get output values within a given range. This helps computers to use sample data to build models so that the decision-making process can be automated. That process is based entirely on data input. Anybody who uses technology today, no matter what it is, has used machine learning. Take facial recognition, for example. By using this, Facebook and other social media platforms make it possible to tag people in photos. OCR (optical character recognition) is used to convert text images into movable text. Recommendation engines make recommendations on purchases (Amazon, eBay, etc.), on movies to watch (Amazon, Netflix, etc.), and on music (Spotify). And then we have the self-drive vehicles and even your email inbox spam filter. All of these are powered by machine learning. This section will look at the more common methods of machine learning and common approaches. We’ll also take a quick look at the best programming languages to use. Lastly, we’ll look at deep  learning and how it differs from machine learning. This will not be a long section because I want to move on to the real focus of this book – using TensorFlow, Scikit-Learn, and Keras for machine and deep learning. Machine Learning Methods Machine learning tasks are classified quite broadly. The classification categories depend on the method of learning or how the learning feedback is passed to the system that needs it. Although two are used more than the third, there are three main categories – they are supervised learning, unsupervised learning, and reinforcement learning. Supervised Learning With supervised learning, the computer is given a set of input data. Each input has a label that states the desired output.  The idea behind supervised learning is that the model learns from the supplied data to provide predictions on unseen data. Learning data patterns on one set, it can compare the actual output with what it was taught to spot errors so that the model can be modified as needed. As such, supervised learning is all about finding patterns and using them to predict labels on unlabeled data. Here's an example. A supervised learning algorithm is given images containing sharks and oceans. The shark images are labeled "fish," and the ocean images are labeled "water." When the supervised learning algorithm is trained on this data, it should then be able to identify unlabeled images of sharks and oceans correctly. One of the commonest use cases for supervised learning is predicting a future event's probability using historical data. For example, it could use historical data from the stock market to predict future fluctuations or, one of the more popular uses, for filtering out spam emails. Or the machine can be fed labeled images of dogs to learn how to classify unlabeled images. Unsupervised Learning Unsupervised learning uses unlabeled data, which means the algorithm has to find the common patterns in the input data by itself. There is far more unlabeled data in the world than there is labeled, so the unsupervised learning methods have a much higher value than the supervised methods. The primary function of unsupervised learning could be as simple as finding hidden patterns in data, or it could be more complex, like learning features. This allows the computer to find the representations needed for classifying the raw data. Typically, unsupervised learning is used for transactional data. Let's say that you have a large dataset containing information about customers and their purchases. Humans are unlikely to be able to make any sense out of the data in terms of similar attributes but, when you feed the data into an unsupervised learning algorithm, it can find those attributes, such as women who purchase one item are likely to purchase some other item. In that way, businesses can draw up targeted ad campaigns to increase customer purchases. Unsupervised learning methods are not given answers like supervised methods are. That means they can examine much more complex datasets containing apparently unrelated data and organize it meaningfully.  We often use unsupervised learning methods to detect anomalies, such as identifying fraudulent card purchases. Or recommender systems that provide suggestions on what a customer should consider buying. Going back to the example of dogs' images, an unsupervised method could take unlabeled images and classify similar images together. Reinforcement Learning The final learning method is reinforcement learning, which isn't used anywhere near as much as supervised or unsupervised learning. Reinforcement learning is about taking actions to ensure maximum rewards in each given situation and is used to find the best path for  machines or software to take in that situation. Like unsupervised learning,  reinforcement learning is not provided with the answers upfront. Instead, the model has to learn what to do; bad decisions penalize the machine while good ones reward it, and that is how the model learns – from experience. Machine Learning Approaches Images from https://morioh.com/ The field of machine learning has a close relationship to computational statistics, making a background in statistics useful for those who want to understand how to use the algorithms. If you are not familiar with statistics, perhaps your starting point should be to understand the difference between regression and correlation, as they are two of the most common machine learning techniques used for investigating relationships between variables. At its most basic, regression looks at relationships between independent and dependent variables. Regression statistics are used to predict dependent variables when the independent ones are known, meaning regression is useful for prediction tasks. Correlation measures the association between variables that are not labeled as dependent or independent. Machine learning approaches are continuously evolving, and new ones are being developed all the time. We’ll look at a couple of the more popular ones in use today. K-Nearest Neighbor K-nearest neighbor, otherwise known as KNN, is used in both regression and classification problems for pattern recognition. The K is a positive integer, usually quite small, and, in regression and classification, the input is the K number of nearest training examples in the given space. We’ll look at classification as this is the most common use, with an  output of class membership. A new object is assigned to the most common class among the nearest neighbors. So, for k = 1, the object will be assigned to the nearest neighbor class.  If it were k = 3, the object would be assigned to the three nearest classes. The diagram below shows two types of objects – blue diamonds and orange stars. Both belong in separate classes, labeled “diamond” and “star.” ![](image_rsrc9TW.jpg)When we add another object, say a green heart, the algorithm needs to work out what class it belongs to – in other words, it has to classify it. ![](image_rsrc9TX.jpg)When k = 3 is chosen, the algorithm locates the three neighbors closes to the green heart and chooses which class it belongs to. In the diagram below, you can see that there are two stars and one diamond nearest to the heart. That means the heart is classified to the star class. ![](image_rsrc9TY.jpg)KNN is one of the most basic of all the algorithms and is classed as a “lazy learner.” This is because it will not generalize past the training data unless the system is given a specific query. Decision Tree Learning Decision trees are used to provide visual representations of decisions and to show the decision-making process.  They are used for predictive purposes in data mining and machine learning, mapping data observations and information about the data's target value. Decision tree learning is used to create models for predicting a target’s value based on the input variable values.  In predictive models, the attributes determined via data observation are represented by the tree branches and the conclusions by the tree leaves. When the source data is tasked with learning the tree, it is divided into multiple subsets based on attribute value tests. The tests are recursively repeated on each subset and, once a node subset has a  value equivalent to the target value, the process is done. Here’s an example of some of the conditions that determine whether someone should go fishing, including barometric pressure and weather conditions. ![](image_rsrc9TZ.jpg)This is a simplified tree where we classify examples by sorting them through the decision tree to the right node. The classification associated with that node or leaf is then returned – in our case, it’s just a Yes or No. The tree is used to classify the daily conditions in terms of whether they are right for fishing. A more complex tree would have more features in the dataset than this one, but it is still pretty straightforward to determine the relationships.  Decision trees require that a number of determinations must be made, such as the features needed, the conditions required for splitting the data, and understanding when the tree has reached the end and provides a clear answer. Programming Languages There are several computer programming languages suitable for machine learning, and when you choose one to specialize in, you should consider the current job adverts and what they list as required skills.  Indeed.com is a popular place for machine learning  job ads, and the data indicates that the most popular language is Python, followed by Java, R, and then C++. Python is undoubtedly the most popular, and much of that is down to the recent development of different deep learning frameworks, including Keras, TensorFlow, and so on. Python’s syntax is already easy to learn and read, and it can also be used for scripting as well as programming. That makes it one of the more powerful languages and the most straightforward for working directly with and pre-processing data.  Scikit-learn is one of the popular machine learning libraries and is built on Python packages such as Matplotlib, SciPy, and NumPy. Java tends to be more used in enterprise programming, typically by developers for front-end desktop applications who are also working on enterprise-level machine learning. It doesn’t tend to be the primary language chosen by beginners to programming or for those looking to learn about machine learning, but those with a Java background do use it in machine learning applications. In terms of industry applications of machine learning, Java is used for network security more than Python is, including fraud detection and cyber-attacks. Some of the popular Java machine learning libraries are an open-source deep learning library called Deplearning4j, a machine learning language toolkit called MALLET for use with text applications such as NLP (natural language processing,) classifying documents, clustering and topic modeling, and Weka, which is a collection of data mining algorithms. R is another open-source language typically used in statistical computing. It has become more popular over time and tends to be used more by academics. It isn’t usually used for industrial environments, but recent advances in data science have lifted its popularity. Some of its more popular machine learning packages include caret (Classification and Regression Training,) for predictive  models, e1071, which contains statistical and probability theory functions, and randomForest, used for regression and classification. Lastly, C++ is typically used in AI and ML for robotic or gaming applications. It is favored by electronics engineers and developers of embedded computing hardware for machine learning because they have a high level of proficiency in the language. Some of the top C++ machine learning libraries are mlpack, Dlib, which offers lots of algorithms, and Shark, which is modular and open-source. 

Deep Learning ![](image_rsrc9SG.jpg)Deep learning tries to imitate the way the human brain works to process information, such as light stimuli into vision and sound stimuli into hearing. The architecture is based on the neural networks in the human brain and they are made up of layers in an ANN (Artificial Neural Network) that consists of GPUs and hardware. Deep learning makes use of nonlinear processing units for the extraction or transformation of the data features. The output from one layer goes to the next layer as its input, and so on until the final layer. Deep learning algorithms can be supervised for classification or unsupervised for pattern recognition and analysis. Out of all the algorithms used and developed for machine learning, deep learning ones take in more data and have even beaten humans in some tasks. That is why deep learning is now the go-to approach with the most potential in artificial intelligence. Deep learning has also produced significant advances in speech recognition and computer vision, with one of the most popular examples being IBM Watson. Deep Learning Vs. Machine Learning One of the easiest ways of understanding the difference between the two is this  - deep learning IS machine learning. To be more specific, it is a machine learning evolution, using neural networks we can program so that machines can make more accurate decisions without human intervention. The most basic definition of machine learning is: "Algorithms that parse data, learn from that data, and then apply what they've learned to make informed decisions." On-demand music or video streaming services are easy machine learning examples. The services use algorithms to recommend movies and music to users based on their listening or viewing activity. They also associate yours with other users' preferences, too, marching you with those who have similar tastes. We often hear this technique called AI, and it is used in lots of services that provided automatic recommendations – Amazon, eBay, Netflix, Spotify, and more. Machine learning is the power behind many automated tasks across many industries, including finance companies, data security, healthcare, and more. The algorithms are being constantly programmed to learn to simulate human thinking – virtual personal assistants if you like. Machine learning also involves a ton of complex coding and mathematics. When it comes down to it, these power mechanical functions in the same way that a car, a flashlight, or a computer screen does. When you hear someone say that something is "capable of machine learning," they mean that it can take the data provided to it, perform a function, and gradually get better at it. However, things get really interesting in terms of machine learning when we bring deep learning into the equation, especially deep neural networks. How Deep Learning and Machine Learning Differ Practically speaking, like machine learning is a subset of AI, so deep learning is a subset of machine learning. In technical terms, it IS machine learning, and it works in much the same way. That's why people tend to use the two terms interchangeably, but there are differences in their capabilities. A basic machine learning model can progressively improve its function, and that means it still needs guidance. When an AI algorithm returns a wrong prediction, a data engineer must make the required adjustments.  Deep learning algorithms can work alone to  see if predictions are right or not, using their own neural networks. Let's use a flashlight as an example. We could program it to turn itself on whenever it hears the word "dark" given as a command. In time, it could learn to switch on whenever it hears the word in any phrase. That's machine learning. In deep learning, the flashlight would work out that it could turn itself on when it hears something like "the light switch has stopped working" or "I can't see." In short, deep learning models learn through their own computing methods, making it look as though it has a brain. How Deep Learning Works Deep learning models are continually analyzing logically structured data in the same way that a human draws conclusions about things. This is done via a structure of layered algorithms known as an artificial neural network. The ANN design is based on the human brain's neural network, and it allows for a learning process that is way more capable than your average machine learning algorithm. Making sure a deep learning model doesn't make the wrong predictions is not easy, as it requires a great deal of training to get the process right. But when it is right deep, when it does do what it was intended for, deep learning is seen as a marvel, one that many see as AIs true backbone. One of the best examples of deep learning is AlphaGo. It's a Google-created program with a neural network, trained to play Go, an abstract board game known for needing intuition and intellect.  The program was pitted against professional human players and learned how to play at a high level, higher than anything ever seen in AI before. It also learned without being told when to make a move – most machine learning models would need to be told when to do it.  When AlphaGo beat several professional Go masters, it caused something of a stir. Not only had a machine learned the complex aspects and techniques of the game, but it had also become one of the best players in the world. As a recap, the differences are: 

*   Machine learning algorithms are used for parsing data. They learn from it and make decisions based on their learning. 
*   Deep learning algorithms are structured in layers, creating an ANN or artificial neural network that learns on its own and can make intelligent decisions. 
*   Deep learning is a machine learning subset and, while they both fall under AI, deep learning is the power behind the human-like AI. 

Here we reviewed what machine learning and deep learning are, common approaches, programming languages and more. You need to keep in mind that machine learning is a continuous innovation and the methods, approaches and algorithms are continually changing. Let’s move on to looking at TensorFlow in depth. 

Part Two An Introduction to TensorFlow ![](image_rsrc9SG.jpg)

[What is TensorFlow ?](#part0038.xhtml#a9M5) ![](image_rsrc9SG.jpg)Images from https://guru99.com TensorFlow is the most famous and most popular library worldwide for deep learning. Developed by Google, it is used in all Google products to improve translation, searches, recommendations, image captioning and more. Take the Google search engine, for example. Powered by AI, it returns speedy results and also suggests search terms. I.e. if you type in “data” it will predict that you want to look for “data science.” Google incorporates machine learning because they have humongous databases that they can use to provide their users with the best possible experience. Three primary groups of people use machine learning: 

*   Researchers 
*   Data scientists 
*   Programmers. 

Each group can share data toolsets, collaborating to improve their efficiency. It’s fair to say that Google has the biggest computer in the world, jam-packed with data, so they built TensorFlow to scale. Developed by the Google Brain Team, it is a library designed to make machine learning faster, along with deep neural network research. It runs on multiple GPUs or CPUs, works on mobile systems, and has a number of wrappers in different languages, such as Python, Java and C++. TensorFlow History In the last couple of years, deep learning has massively outperformed any other machine learning algorithm that works on huge amounts of data. Google saw this and discovered that it could use this to make improvements to its services, including the Google search engine, Google Photo and Gmail. To facilitate this, they built the TensorFlow framework, allowing developers and researchers to collaborate on an artificial intelligence model. It was late in 2015 before it was first made public, but it was 2017 before the first properly stable version was released. TensorFlow is an open-source library distributed under an Apache Open Source License, which means anyone can use it, redistribute it and modify it, all free. TensorFlow Architecture There are three parts to the TensorFlow architecture: 

*   Data pre-processing 
*   Model building 
*   Training and estimating the model 

The reason it was called TensorFlow is that it can take a tensor as its input. A tensor is a multi-dimensional array and operational flowcharts, otherwise known as graphs, can be constructed to perform on the tensor. The input is fed in at one end, flows through the multiple operations and then exits as an output at the other end. In short, the tensor flows through the system, hence the name. Where Can TensorFlow Run? We can classify the TensorFlow software and hardware requirements into two phases. The first is the development phase, where the model is trained and this is typically on a laptop or computer. The second phase is the interference or run phase where, once it has been trained, TensorFlow can run on different platforms, including: 

*   Desktops or laptops on macOS, Windows or Linux 
*   Cloud as a Web Service 
*   Mobile devices 

TensorFlow can be trained on more than one machine, and then the trained model can be run on a completely different machine, including GPUs and CPUs. The GPU was originally designed to be used with video games, but in 2010, Stanford researchers discovered that it was also suitable for algebra and matrix operations. That meant the GPU was incredibly fast and idea for these types of calculation, especially as deep learning has a strong reliance on matrix multiplication.  TensorFlow is written in C++, which makes it incredibly fast for matrix computations and, although C++ is used for the implementation, other languages, typically Python, can access and control it. The last main feature is the TensorBoard, which enables the user to graphically visualize TensorFlow at work. TensorFlow Components The two primary components of TensorFlow are: Tensor The tensor is the main framework of TensorFlow, and every computation in it will involve these tensors. So, what is a tensor? It is a matric or a vector with n-dimensions representing all data types. All the tensor’s values have the same data type with a shape that is known or at least partly known, and that data shape is array or matrix’s dimensionality. Tensors can originate from two places – the input data or as the result of a computation. All TensorFlow operations take place inside a graph, which is a computation set where all operations are successive. The operations are connected and are known as op nodes. The graph outlines the ops and the node connections, but the values  are not displayed. The tensor is the edge of the nodes and is a way of populating the operation with all the data. Graphs TensorFlow also uses a graph framework, and this is where the sequence of the computations carried out during training are gathered together and described. The graph is highly portable, which means the computations can be preserved for immediate use or kept for later. Tensors consist of nodes and edges. The node is where the mathematical operation is and where we get the output from the endpoints. The edges explain the input and the output relationships between each node. Why TensorFlow is So Popular TensorFlow is popular because it is accessible by anyone and everyone. It has multiple APIs built to scale ANNs, CNNs and other deep learning architectures. Plus, because TensorFlow is based on graphs, the developer can use TensorBoard to see how the neural networks are constructed and this also helps with debugging. Top TensorFlow Algorithms TensorFlow has APIs built-in for the following algorithms: 

*   Boosted tree classification: tf.estimator.BoostedTreesClassifier
*   Booster tree regression: tf.estimator.BoostedTreesRegressor
*   Classification:tf.estimator.LinearClassifier
*   Deep learning classification: tf.estimator.DNNClassifier
*   Deep learning wipe and deep: tf.estimator.DNNLinearCombinedClassifier

Linear regression: tf.estimator.LinearRegressor 

Simple Example of TensorFlow ![](image_rsrc9SG.jpg)import numpy as np import tensorflow as tf It really couldn’t be simpler. In those two simple code lines, we imported TensorFlow as tf. In Python, you will note that we commonly shorten the library names and the only advantage to that is to avoid having to type the full library name when we want to use it. For example, TensorFlow is imported as tf and when we want a TensorFlow function, we can simply call tf. The same goes for NumPy, another popular Python machine learning library. Let’s see another simple example that shows you how TensorFlow works. We want to multiply two numbers and we need a computational graph to do that. In the example, X\_1 will be multiplied with X\_2. TensorFlow will connect the operation by creating a node and we’ve called it “multiply.” Once the graph has been determined, the computational engines in TensorFlow will multiply those numbers for us. The last thing we need to do is get a TensorFlow session running a computational graph with those values and print the multiplication result. We need to define our input nodes. Whenever a node is created in TensorFlow, we much choose the node type to create. X1 and X2 are going to be placeholders and, whenever a new calculation is made, the placeholders assign new values. Our placeholders are going to be created as TF dot placeholder nodes. Step One – Defining the Variable When the placeholder node is created, we need to pass the data type in. As we are using numbers, we use the floating-point type, which  you can see as tf.float32. The node also needs to be named. When we examine a graphical representation of the model, those are the names we see.  So we named ours X\_1 and X\_2 by passing parameters with the name values into each one.  X\_1 = tf.placeholder(tf.float32, name = "X\_1") X\_2 = tf.placeholder(tf.float32, name = "X\_2") Step Two – Defining the Computation Next, we define the node responsible for doing the multiplication, and that is done in TensorFlow with a tf.multiply node. X\_1 and X\_2 are passed to the multiplication node, which tells TensorFlow that the nodes need to be linked in the graph. In short, we are requesting that it gets the values from the two specified nodes and then multiply them. We also need to name the multiplication node; we called ours “multiply.” All of this defines the computational graph. multiply = tf.multiply(X\_1, X\_2, name = "multiply") Step Three – Executing the Operation For graph operations to be executed, a session must be created, and this is done by using tf.session. Once the session has been created, we can call session – this tells it we want the operations run on the graph, using the run command. When we run the addition operation, it will see that the X\_1 and X\_2 node values are required, which means we need to give it the values using the feed.dict command, passing the X\_1 value as 1,2,3 and the X\_2 value as 4,5,6. Finally, the results are printed. The multiplication operations are 1x4, 2x5 and 3x6 so we should see an output of 4, 10, 18. Here’s the whole code from start to finish: multiply = tf.multiply(X\_1, X\_2, name = "multiply") with tf.Session() as session: result = session.run(multiply, feed\_dict={X\_1:\[1,2,3\], X\_2: \[4,5,6\]}) print(result) \[ 4. 10. 18.\] Loading the Data into TensorFlow Before you can even think about training any machine learning algorithm, the data needs to be loaded and there are two ways to do this: 

1.  Load into Memory is the simplest and most common method where all the data is fed as one array into memory. This is done by writing a short code in Python which is not related to TensorFlow. 
2.  Use a TensorFlow Pipeline – In TensorFlow, there is an API for helping load data, carry out the operation and feed the algorithm, all rolled into one. This is a good method to use when working with huge datasets, such as image datasets, which are often too large to go into memory. The pipeline will do the memory management for you. 

So, which one should you use? 

1.  Loading the data in memory – this is the best method to use if your dataset is small, less than 10 GB in size, as the data easily fits into memory. One of the best libraries to use is Pandas as this helps you import the CSV files. 
2.  Using the TensorFlow pipeline – if your dataset is huge, use this method. For example, if your computer has 16 GB of memory and you are trying to import 50 GB of data, it won’t work; all you succeed in doing is crashing your computer. 

For the latter method you would need to build a pipeline and use it to load small batches of the data at a time. Each batch goes into the pipeline and is gotten ready for training on. This is a great solution  because you can use something called parallel computing, which means TensorFlow trains the model across several CPUs. This helps in training very powerful neural nets. Now we’ll look at how to build a pipeline. Building a TensorFlow Pipeline In our earlier example, we added the X\_1 and X\_2 values manually. Now we need to see how a pipeline is built to load the data into TensorFlow. Step One – Creating the data First, we can use NumPy to generate a pair of random values: import numpy as np x\_input = np.random.sample((1,2)) print(x\_input) \[\[0.8835775 0.23766977\]\] Step Two – Creating the Placeholder As in our first example, the placeholder is created and named X. The Tensor shape must be explicitly specified so we load an array containing just two values and the shape is written as shape=\[1,2\]. \# use placeholder x = tf.placeholder(tf.float32, shape=\[1,2\], name = 'X') Step Three – Defining the Dataset Method Next, the dataset needs to be defined, and this is where the placeholder value will be populated. To do this, we use the following method: dataset = tf.data.Dataset.from\_tensor\_slices(x) Step Four – Creating the Pipeline Now the pipeline needs to be initialized. This is where the data flows, so we need an iterator. We use make\_initializable\_iterator and give it the name of “iterator.” This iterator is called to feed in the data  batches, one at a time, so we use get\_next. This is just a simple example, using one data batch containing two values. iterator = dataset.make\_initializable\_iterator() get\_next = iterator.get\_next() Step Five – Executing the Operation This is much like our first example. A session is initiated and the operation iterator is run. We give feed\_dict the NumPy-generated values, which then populate the placeholder. Lastly, we print the result using get\_next: with tf.Session() as sess: \# feed placeholder with data sess.run(iterator.initializer, feed\_dict={ x: x\_input }) print(sess.run(get\_next)) # output \[ 0.52374458  0.71968478\] \[0.8835775  0.23766978\] That was just a simple example of how TensorFlow works. Things will get a little more complicated, but first, we need to take time out to show you how to install TensorFlow on your Windows or Mac computer. 

Installing TensorFlow ![](image_rsrc9SG.jpg)The easiest way to install TensorFlow is to use a Python distribution called Anaconda. Once we have installed it, we will look at how to use it with Jupyter, a popular notebook viewer. First, TensorFlow will work across multiple GPUs and CPUs which means we can distribute the computations across multiple devices, thus speeding up the training. By using parallelization, you eliminate the need to wait days or weeks for the algorithm results. There are two Windows version of TensorFlow: 

*   CPU Support Only – this is the only version you can use if your computer does not have a NVIDIA GPU. 
*   GPU Support – if you do have a NVIDIA GPU and you need the capacity for strong computation, this version is much faster. 

We will be using the first, the CPU support version, as it is more than sufficient for the purposes of this tutorial. Also, there is no GPU Support version for the Mac. Here goes – read through this first, before you start following it, as some is theory and some is practical instruction. Install Anaconda We’re going to look first at how to install Anaconda on Windows and macOS. Windows 

1.  Go to [https://www.anaconda.com/download/#windows](https://www.anaconda.com/download/#windows) and download the Anaconda installer and save it to your desktop 
2.  Find and double-click on the installer to launch it – do NOT  do this from your favorites folder as it will cause permission errors 
3.  Click on Next on the launcher window 
4.  Read and click I Agree on the terms and conditions 
5.  Unless you are installing for all system users, choose to install for Just Me on the next window and choose where it will be installed 
6.  Click on Next 
7.  On the next window, you have two boxes you can potentially check – the first asks if you want Anaconda added to your PATH environment variable. We don’t recommend this as it tends to interfere with some other software on your computer, so don’t check this box. Instead, you should use Anaconda by using the Start Menu prompt or Anaconda Navigator. 
8.  The second check box asks if you want Anaconda registered as the default Python. Check this box unless you are intending to run more than one version of Python or Anaconda. 
9.  Now click on Install. If you want to see which packages are being installed, click on Show Details, or just leave it to install by itself 
10.  Click on Next and you get the option of installing PyCharm; for now just click Next on this window 
11.  Once Anaconda is installed, you get a dialog box thanking you for installing it.  Click on Finish. 

Now you need to verify your installation and there are two ways to do this – using Anaconda Navigator or conda. Navigator This is a GUI (graphical user interface) that gets installed alongside Anaconda. Go to your Start menu and type in Anaconda Navigator.  If it opens, Anaconda was successfully installed. If it doesn’t, the installation was not successful. In that case, temporarily disable your antivirus software and run through the steps above again. Don’t forget to re-enable it again afterward. Conda This one is for those of you who like to use the CLI (command-line interface). Click on your Start menu and type in Anaconda Prompt. From here, you have a choice of methods to check the installation. At the command prompt: 

*   Type in conda list.  If the installation was successful, you will see the installed packages listed along with their version numbers; OR 
*   Type python at the prompt. The Python shell should run if Anaconda is installed, and you should see information about the version. Enter quit() to close the shell; OR 
*   Type anaconda-navigator at the prompt to open Anaconda; it will only open if the installation was successful. 

Mac You have a choice of two methods to install Anaconda on Mac – the graphical installer or command line. If you are not sure which one to use, go for the graphical installer. Graphical Install 

1.  Go to [https://www.anaconda.com/downloads#macos](https://www.anaconda.com/downloads#macos) and download the correct installer for the Python version you want 
2.  Double-click the file icon and start the installation by clicking on Continue 
3.  Click through the screens for Introduction, Read Me and License, agreeing to each one 
4.  Click Install on the next window – this will install Anaconda into the ~/opt directory, which is the recommended one 
5.  A Destination Select screen opens, click on Install for Me Only 
6.  Click on Continue  and then click Continue on the PyCharm screen 
7.  You will be greeted with the Thank You For Installing screen when Anaconda is installed. 

Command-Line Install This is for those who prefer using the terminal window 

1.  Open your browser and go to [https://www.anaconda.com/downloads#macos](https://www.anaconda.com/downloads#macos)
2.  Download the command-line version
3.  Open your terminal and type in the following command, replacing filename with your own path and filename:

shasum -a 256 /path/filename 

4.  Now decide whether you are installing Python 3.7 or 2.7. For 3.7, type in the following command: 

bash ~/Downloads/Anaconda3-2020.02-MacOSX-x86\_64.sh and for 2.7, type in this command: bash ~/Downloads/Anaconda2-2019.10-MacOSX-x86\_64.sh Make sure, in both cases, that you replace Downloads with your own path and Anaconda3-2020.02-MacOSX-x86\_64.sh with the name of the file that was downloaded. 

5.  You will now see an installer prompt asking you to look at the  license terms – click Enter, scroll down to the bottom and then click on Yes 
6.  Now the installer requests that you confirm the location by pressing the enter key. You have two choices – agree to the default, in which case you will see PREFIX=/home/<user>/anaconda<2 or 3>. If you want to change the default, press CTRL+C and input the new directory. The former is recommended. 
7.  The installer will now ask you if you want to run conda init to initialize Anaconda3 – click on Yes 
8.  Wait for the installation to finish and you will see the “thank you for installing” window. 
9.  Close the installer and open the terminal window so the installation can come into effect. 

Now decide if you want each shell session to have an activated base environment. If you do, run the following command at the prompt: conda config --set auto\_activate\_base False or True If you prefer conda to run from anywhere, without the base activated, type in this: conda init conda config --set auto\_activate\_base False Lastly, the installation must be verified, using Anaconda Navigator or conda. Navigator 

*   Click on Launchpad and pick Anaconda Navigator; OR  
    press CMD+Space to launch Spotlight Search; type in Navigator and the program opens 

Conda 

*   Press CMD+Space to launch Spotlight Search and type  Navigator 

Now use one of the following to verify the installation: 

*   Type in conda list.  If the installation was successful, you will see the installed packages listed along with their version numbers; OR 
*   Type python at the prompt. The Python shell should run if Anaconda is installed, and you should see information about the version. Enter quit() to close the shell; OR 
*   Type anaconda-navigator at the prompt to open Anaconda; it will only open if the installation as successful. 

Install TensorFlow Step One – Locate Anaconda Windows The first step is to find the Anaconda path. We need a conda environment where all the required libraries will reside. Open the Anaconda prompt and type in: C:\\>where anaconda We want to know the folder name where we installed Anaconda because that path is where the new environment will be installed. Mac OS Open your Terminal and type the following at the command prompt: which anaconda Step Two – Setting the Working Directory We want to create a folder in Anaconda where TensorFlow, Jupyter and IPython will be installed and the quickest way to do this is to create a .yml file. First, the working directory must be specified where you want the file created. Mac OS The terminal will automatically set the default working directory as Users/USERNAME and, typically, the working directory and anaconda3 paths are identical. You will see a $ sign – the folder before this is the latest one, and the terminal installs the libraries here. If the text editor path isn’t the same as the working directory, change it by going to the terminal and typing cd anaconda3 Windows Type in cd C:\\Users\\Admin\\Anaconda3 or the path that the "where anaconda" command provides. Please note that, where it says Admin in the above command, you should insert the folder it is in on your system. Step Three- Creating the .yml File The .yml file can be created in the working directory and will be responsible for installing the dependencies needed for TensorFlow: Mac OS Type this command in the terminal: touch hello-tf.yml You should see the new file, called hello-tf.yml, in anaconda3. Windows Type this command at the prompt: echo.>hello-tf.yml and you will see the new file appear Step Four – Editing the .yml File Mac OS Now we can edit the .yml file, using vim. Type this in the terminal: vi hello-tf.yml This will put you into edit mode and once you press the esc key, you can do any of the following: 

*   Press the i key to edit 
*   Press the w key to save 
*   Press the q key to quit. 

Write the code below in edit mode and then press the esc key and the w key. Be aware that everything is intend and case sensitive and there must be two spaces are each intend: name: hello-tfdependencies: \- python=3.6 \- jupyter \- ipython \- pandas \- pip:      \- [https://storage.googleapis.com/tensorflow/MacOS/cpu/tensorflow-1.5.0-py3-none-any.whl](https://storage.googleapis.com/tensorflow/MacOS/cpu/tensorflow-1.5.0-py3-none-any.whl) Don’t forget to press the esc key and then w to save it; then press esc and q to quit. Windows As Windows has no vim program, you can use Notepad for this: notepad hello-tf.yml Type this into the file: name: hello-tfdependencies: \- python=3.6 \- jupyter \- ipython \- pandas Step Five – Compiling the .yml File Type the following at the prompt: conda env create -f hello-tf.yml The environment will be created in the current directory. Step Six – Activating Conda We are nearly there. You should now have two conda environments – an isolated one for the libraries and a default one. Every machine learning project you do will require different libraries so it is good practice to set up an isolated one. Once your project is done, you can choose whether to keep the isolated environment or delete it. conda env list When you run that, the default environment is indicated by the asterisk and, to activate it, you must switch to hello-tf: Mac OS source activate hello-tf Windows activate hello-tf When you do this, make sure all the dependencies are listed where they should be in the same environment. This is an important point – Python needs to be able to use TensorFlow and Jupyter from the same environment and if all three are not listed together, you have to start over. Mac OS which python which jupyter which ipython You can also check to see if TensorFlow needs updating by inputting the following command: pip install --upgrade tensorflow Windows where python where jupyter where ipython Now we have two Python environments – the primary environment and the one we just created as hello-tf. In the main conda environment, you will only find the heel-tf environment, not the primary one. To install TensorFlow on Windows, use the following command: pip install tensorflow Launching Jupyter Notebook This is the same for both Windows and Mac OS. Be aware that, when you want TensorFlow opened, the environment must be initialized. This is what we are going to do: 

*   Activate hello-tf conda environment 
*   Open Jupyter 
*   Import tensorflow 
*   Delete Notebook 
*   Close Jupyter 

Step One – Activating Conda Type the following commands at the respective prompts: Mac source activate hello-tf Windows conda activate hello-tf Step Two – Opening Jupyter Now, Jupyter can be opened. At the prompt, type in: jupyter notebook If your browser doesn’t automatically open, copy the URL you see at the prompt and paste it into your browser. It should start with http://localhost.8888 When the Jupyter Notebook opens, you will see the working directory and all its files. Creating a new notebook is as simple as clicking the New button, followed by Python 3. All new notebooks are saved in the working directory. Step Three – Importing TensorFlow TensorFlow can now be imported in Jupyter using the tf alias. Click on Run and a new cell gets created, where you type: import tensorflow as tf Time to write a line of code using TensorFlow. Type in the following: hello = tf.constant('Hello, HappyMonday!') hello Here, we created a tensor – you have successfully installed TensorFlow through Jupyter on your computer. Step Four – Deleting the File If you want, the file called Untitled.ipynb can be deleted from Jupyter. Just check the box next to it and click the delete button. Step Five – Closing Jupyter You can close Jupyter in two ways. First, you can do it from the Notebook and, second, by using the Anaconda prompt or the terminal. Jupyter From the main screen in the Jupyter click the  Logout button and  you will be taken to the logout page. Terminal/Anaconda Prompt From the prompt or terminal, run CTRL+C twice. On the first time, you need to confirm that you want the Notebook shut down. The second CTRL+C confirms it. 

TensorFlow Basics ![](image_rsrc9SG.jpg)Now you know how to get TensorFlow on your computer, let’s take a look at some of the basics of the library. We’ll give you a recap on what TensorFlow is and then go into detail about how it works and what it can do. What is a Tensor? TensorFlow gets its name from the tensor, which is the core framework of the library. Tensors are involved in every TensorFlow computation but what is a tensor? As we explained earlier, it is a matrix or vector of n-dimensions representing all data types. Every tensor value has the same data type as a known or partly known shape and the data shape is the array or matrix’s dimensionality. Tensors can come from two places – a computation’s result or the input data. All TensorFlow operations take place in a graph which is a series of successive computations. Each TensorFlow operation is an op node and these are all connected. The graph shows the ops and their connections but it won’t show you their values. The node edge is the tensor and is a way of populating the operation with the data. In machine learning, we feed models with feature vectors, which are lists of objects. These vectors may be of any data type but they are the primary method of input for populating tensors. The object values flow through the tensor to the op node and a new tensor is created as a result of the computation. The new tensor will then get used in a new operation and all of these can be visualized in the graph. How Tensors are Represented We already know that a tensor is an array or matrix of feature vectors of n-dimensions. So, if our matrix was 2x3, and it contained the values 1 through 6, we would write it as: [![](image_rsrc9U0.jpg)](https://www.guru99.com/images/1/080418_1250_WhatisaTens111.png) It would be represented in TensorFlow as: \[\[1, 2, 3\], \[4, 5, 6\]\] If we had a 3-dimensional matrix containing the values 1 through 8, we would have: ![](image_rsrc9U1.jpg)And TensorFlow would represent it as: \[ \[\[1, 2\], \[\[3, 4\], \[\[5, 6\], \[\[7,8\] \] It’s worth bearing in mind that tensors may use scalars to represent them or their shape may be four or more dimensions but it is far harder for higher-dimensions levels to be visualized. Tensor Types Every TensorFlow computation flows through at least one tensor and each tensor has three properties: 

*   Name – a unique label 
*   Shape – its dimension 
*   dtype – its data type 

Each TensorFlow operation requires a tensor to be manipulated and you can create four primary tensors: 

*   tf.Variable 
*   tf.constant 
*   tf.placeholder 
*   tf.SparseTensor 

We’re going to look at creating two of those – the tf.Variable and tf.constant. Before we start, you need to ensure that the conda environment has been activated with TensorFlow. Don’t forget; we named it hello-tf. Here’s how to activate it: Mac source activate hello-tf Windows activate hello-tf Now we can import TensorFlow: \# Import tf import tensorflow as tf Step One – Creating a Tensor of n-dimension We start by creating one tensor with a single dimension, otherwise known as a scalar. We do this using tf.constant(): tf.constant(value, dtype, name = "") arguments \- \`value\`: Value of n dimension to define the tensor. Optional \- \`dtype\`: Define data type:    \- \`tf.string\`: String variable    \- \`tf.float32\`: Flot variable    \- \`tf.int16\`: Integer variable \- "name": Name of the tensor. Optional. By default, \`Const\_1:0\` The following code will help you create a tensor with a dimension of 0: \## rank 0 \# Default name r1 = tf.constant(1, tf.int16) print(r1) Output Tensor("Const:0", shape=(), dtype=int16) \# Named my\_scalar r2 = tf.constant(1, tf.int16, name = "my\_scalar") print(r2) Output Tensor("my\_scalar:0", shape=(), dtype=int16) The tensor name is used to display each one and we define the tensor objects with the name, shape and dtype. Tensors can be defined with a string or decimal values by changing the data type. \# Decimal r1\_decimal = tf.constant(1.12345, tf.float32) print(r1\_decimal) \# String r1\_string = tf.constant("HappyMonday", tf.string) print(r1\_string) Output Tensor("Const\_1:0", shape=(), dtype=float32) Tensor("Const\_2:0", shape=(), dtype=string) A tensor of dimension 1 can be created as follows: \## Rank 1r1\_vector = tf.constant(\[1,3,5\], tf.int16) print(r1\_vector) r2\_boolean = tf.constant(\[True, True, False\], tf.bool) print(r2\_boolean) Output Tensor("Const\_3:0", shape=(3,), dtype=int16) Tensor("Const\_4:0", shape=(3,), dtype=bool) You can notice the shape is only composed of 1 column. If you want an array with 2 dimensions, the brackets at the end of each row must be closed. Here are some examples: \## Rank 2 r2\_matrix = tf.constant(\[ \[1, 2\], \[3, 4\] \],tf.int16) print(r2\_matrix) Output Tensor("Const\_5:0", shape=(2, 2), dtype=int16) Our matrix now has 2 columns and 2 rows and the values of 1, 2, 3, 4. TO make a 3-dimensional matrix, we add another level, not forgetting to use the brackets: \## Rank 3 r3\_matrix = tf.constant(\[ \[\[1, 2\], \[3, 4\], \[5, 6\]\] \], tf.int16) print(r3\_matrix) Output 

Tensor("Const\_6:0", shape=(1, 3, 2), dtype=int16) ![](image_rsrc9SG.jpg)Tensor Shapes When the tensor is printed, TensorFlow will guess what the shape is but you can use the shape property to get the actual shape. Here, we are going to build a matrix with the values 10 through 15 and then check the m\_shape shape: \# Shape of tensor m\_shape = tf.constant(\[ \[10, 11\], \[12, 13\], \[14, 15\] \]                      ) m\_shape.shape Output TensorShape(\[Dimension(3), Dimension(2)\]) Our matrix has 2 columns and 3 rows. TensorFlow contains so commands that help you create a matrix or an array filled with 1 or 0. For example, if you wanted a 1-d tensor with a shape of 10 and filled with 0, you would use this code: \# Create a vector of 0 print(tf.zeros(10)) Output Tensor("zeros:0", shape=(10,), dtype=float32) The shape property will also work with matrices too, so here’s how to create a matrix of 10x10, filled with 1: \# Create a vector of 1 print(tf.ones(\[10, 10\])) Output Tensor("ones:0", shape=(10, 10), dtype=float32) The shape of any specified matrix can be used to create a vector of one. The m\_shape of the matrix is 3x2 and the tensor will have 3 rows filled with 1 – this is the code: \# Create a vector of ones with the same number of rows as m\_shape print(tf.ones(m\_shape.shape\[0\])) Output Tensor("ones\_1:0", shape=(3,), dtype=float32) If the value 1 is passed to the bracket, we can create a vector of ones that equals how many columns are in m\_shape for the matrix: \# Create vector of ones with the same number of column as m\_shape print(tf.ones(m\_shape.shape\[1\])) Output Tensor("ones\_2:0", shape=(2,), dtype=float32) Lastly, you can also create a 3x2 matrix filled with one’s: print(tf.ones(m\_shape.shape)) Output 

Tensor("ones\_3:0", shape=(3, 2), dtype=float32) ![](image_rsrc9SG.jpg)Data Types Another property of a tensor is the data type and each tensor can only hold one data type at any time. We use the dtype property to return the data type: print(m\_shape.dtype) Output <dtype: 'int32'> Sometimes, you may need to change the data type and we can do that in TensorFlow using the tf.cast method: Here’s an example: In the code below, we convert a float tensor into an integer using tf.cast \# Change type of data type\_float = tf.constant(3.123456789, tf.float32) type\_int = tf.cast(type\_float, dtype=tf.int32) print(type\_float.dtype) print(type\_int.dtype) Output <dtype: 'float32'> <dtype: 'int32'> TensorFlow automatically picks the data type if we don’t specify the argument when the tensor is created. It will guess at the likely data type, for example, if text is passed, it guesses it is a string and converts it as such. Useful TensorFlow Operators Now we know how to create tensors, we should turn our attention to mathematical operations. You can find all the basic ones in TensorFlow ad we’ll start with an easy one, using TensorFlow to work out the square of a given number. This is easy because the tensor is constructed with just one argument. We use tf.sqrt(x) and x represents a floating number. x = tf.constant(\[2.0\], dtype = tf.float32) print(tf.sqrt(x)) Output Tensor("Sqrt:0", shape=(1,), dtype=float32) Note that the output is not what you would expect – you think it would the square of 2 result but it is a tensor object. What the example has printed is the tensor definition and not the operation evaluation. Shortly, we will look at how TensorFlow executes the operations but, first, here’s a list of the common operations, each requiring at least one argument: 

*   tf.add(a, b) 
*   tf.div(a, b) 
*   tf.exp(a) 
*   tf.multiply(a, b) 
*   tf.pow(a, b) 
*   tf.sqrt(a) 
*   tf.substract(a, b) 

Here’s an example: \# Add tensor\_a = tf.constant(\[\[1,2\]\], dtype = tf.int32) tensor\_b = tf.constant(\[\[3, 4\]\], dtype = tf.int32) tensor\_add = tf.add(tensor\_a, tensor\_b)print(tensor\_add) Output Tensor("Add:0", shape=(1, 2), dtype=int32) What we did here was created two tensors, one containing 1 and 2 and one containing 3 and 4. Then we added the two tensors together. Keep in mind that, when you do this, all the tensors you are adding must be the same shape. We can also do multiplication operations on two tensors: \# Multiply tensor\_multiply = tf.multiply(tensor\_a, tensor\_b) print(tensor\_multiply) Output 

Tensor("Mul:0", shape=(1, 2), dtype=int32)              ![](image_rsrc9SG.jpg)Variables Up to now, we have concentrated on constant tensors but, to be fair, these are not always of the best use. That is because data comes in all kinds of types and values and capturing that requires us to use the Variable class. This represents nodes where values are always changing. We need to use the tf.get\_variable method to do this: tf.get\_variable(name = "", values, dtype, initializer) argument \- \`name = ""\`: Variable name \- \`values\`: Tensor dimension \- \`dtype\`: Optional – data type \- \`initializer\`: Optional – initializing the tensor If we specify the initializer, we don’t need to add the values because the initializer’s shape is used instead. For example, below we create a 2-d variable that contains a pair of random values. TensorFlow will return a random value by default. The variable is named as var: \# Create Variable \## Create 2 Randomized values var = tf.get\_variable("var", \[1, 2\]) print(var.shape) Output (1, 2) Next, we will create a variable that has two columns and one row and, to create the variable’s dimension, we use \[1,2\]. This tensor has  an initial value of zero. When a model is trained, you must provide the initial values so the weight of the features can be computed. In this case, we set them to zero: var\_init\_1 = tf.get\_variable("var\_init\_1", \[1, 2\], dtype=tf.int32,  initializer=tf.zeros\_initializer) print(var\_init\_1.shape) Output (1, 2) A constant tensor’s values can be passed in a variable and a constant tensor is created using the tf.constant() method. This tensor can be used for the variable initialization. The first of the variable’s values are 10, 20, 30, 40 and the shape of the new tensor is 2x2: \# Create 2x2 matrixtensor\_const = tf.constant(\[\[10, 20\], \[30, 40\]\]) \# Initialize the first value of the tensor equals to tensor\_const var\_init\_2 = tf.get\_variable("var\_init\_2", dtype=tf.int32,  initializer=tensor\_const) print(var\_init\_2.shape) Output (2, 2) Placeholders Placeholders have one simple job – feeding the tensor. We use them to initialize the data we want flowing in the tensors. Supplying a placeholder requires that you use the feed\_dict method, and each tensor is only fed within the session they are created in. The syntax you need to use is: tf.placeholder(dtype,shape=None,name=None ) arguments: \- \`dtype\`: Data type \- \`shape\`: Optional – placeholder dimension. By default, it is  the data shape. \- \`name\`: Optional – placeholder name​ ​               data\_placeholder\_a = tf.placeholder(tf.float32, name = "data\_placeholder\_a") print(data\_placeholder\_a)​ Output Tensor("data\_placeholder\_a:0", dtype=float32)​               Session TensorFlow has three primary components that it works around: 

*   Graph 
*   Session 
*   Tensor 

The following table describes these three components: 

| Components  || Description  |
| --- | --- |
| Graph  || A fundamental part of TensorFlow, every mathematical operation is done in a graph. We can see the graph as the project containing all the operations, each represented by a node that can absorb new tensors or create them.  |
| Tensor  || Tensors represent the data that goes between the operations. We already looked at initializing tensors and the difference between variables and constants is that, with a variable, the initial values will change; with a constant, they stay the same.  |
| Session  || Sessions execute the graph operations. A session must be opened to feed the tensor values to the graph and, in the session, an output can only be created with the use of an operator.  |

Graphs and sessions remain independent of one another; a session can be run, and the values obtained can be used in later computations. In our next example, we will do the following: 

*   Create a pair of tensors 
*   Create one operation 
*   Open a session 
*   Print result 

Step One – Creating the Tensors First, we want to create two tensors called x and y: \## Create, run  and evaluate a session x = tf.constant(\[2\]) y = tf.constant(\[4\]) Step Two – Creating the Operator The operator is created by multiplying the tensors, x and y: \## Create operator multiply = tf.multiply(x, y) Step Three – Opening a Session Now we need to open a session so all the computation can take place. Then you must remember to close that session: \## Create session to run code sess = tf.Session()result\_1 = sess.run(multiply) print(result\_1) sess.close()​ Output \[8\]​ Let’s break that code down: 

*   sess = tf.session opens the session so that all the operations can flow 
*   run(multiply) executes the operation we created earlier in step two 
*   print(result\_1) prints the result 
*   close() closes the session 
*   The output is 8, a result of x and y being multiplied 

We can also create sessions inside blocks and the advantage of this is that it doesn’t matter if you forget to close the session as it will be automatically done for you: with tf.Session() as sess:    result\_2 = multiply.eval() print(result\_2) ​ Output \[8\]​ The eval() method can be used to execute operations and is much the same as using the run() method. It just makes the code easier to read. A session can also be created to see the values of tensors you already created: \## Check tensors already created sess = tf.Session() print(sess.run(r1)) print(sess.run(r2\_matrix)) print(sess.run(r3\_matrix))​ Output 1 \[\[1 2\] \[3 4\]\] \[\[\[1 2\] \[3 4\] \[5 6\]\]\] By default, variables are empty, even when a tensor has been created. The variable must be initialized if you want to use it and initializing a variable’s values is done using the tf.global\_variables\_initialzer() object. Using this explicitly initializes every variable, a helpful thing to do before training a model. Like the tensors, you can also create a session to check on the variables you already created and run() is required for the tensor evaluation: sess.run(tf.global\_variables\_initializer()) print(sess.run(var)) print(sess.run(var\_init\_1)) print(sess.run(var\_init\_2))​ Output \[\[-0.05356491  0.75867283\]\] \[\[0 0\]\] \[\[10 20\] \[30 40\]\]​ The placeholder you created earlier can also be used and fed with the value. The data must be passed in the feed\_dict method. For example, we have a placeholder called data\_placeholder\_a and we  want the power of 2 of the placeholder: import numpy as np power\_a = tf.pow(data\_placeholder\_a, 2) with tf.Session() as sess:  data = np.random.rand(1, 10)  print(sess.run(power\_a, feed\_dict={data\_placeholder\_a: data}))  # Will succeed.              Breaking this code down: 

*   import numpy as np: imports the numpy library so we can create the data. 
*   tf.pow(data\_placeholder\_a, 2): creates the operations (ops) 
*   np.random.rand(1, 10): creates a random data array 
*   feed\_dict={data\_placeholder\_a: data}: feeds the data to the placeholder. 

Output \[\[0.05478134 0.27213147 0.8803037  0.0398424  0.21172127 0.01444725  0.02584014 0.3763949  0.66022706 0.7565559 \]\]              Graphs Rendering operations in TensorFlow requires that a dataflow scheme is used to represent the computations. To help with that, the dataflow graph was developed so we could see each operation’s data dependencies. Mathematical algorithms consist of a series of operations in succession and a graph conveniently shows us the coordination between the computations. On a TensorFlow graph, you will see an edge and a node. The edge represents the tensor and can produce new ones or take the input data, while the node represents the operations. Whether a tensor produces new tensors or takes input data is entirely dependent on the individual operation dependencies. A graph is structured to connect the nodes and show how they are feed. What you won’t see on a graph is the operation’s outputs. Let’s see this better with an example. Let’s say that we want the following function evaluated: f(x, z) = xz + x 2 \+ z + 5 TensorFlow executes this function by creating a graph which looks like this: ![](image_rsrc9U2.jpg)This clearly shows which path is taken by the tensors to get to the end. The graph is telling you that the order of operations is: 

*   add 1) together 
*   add to 2) 
*   add 3) to 

x = tf.get\_variable("x", dtype=tf.int32,  initializer=tf.constant(\[5\])) z = tf.get\_variable("z", dtype=tf.int32,  initializer=tf.constant(\[6\])) c = tf.constant(\[5\], name =​ "constant")square = tf.constant(\[2\],  name =              "square") f = tf.multiply(x, z) + tf.pow(x, square) + z + c​ ​               Breaking this code down: 

*   x: Initializes the variable called x with 5, which is a constant value 
*   z: Initializes the variable called z with 6, which is a constant value 
*   c: Initializes the constant tensor called c with 5, which is a constant value 
*   square: Initializes the constant tensor called square with 2, which is a constant value 
*   f: Constructs the operator 

We have chosen to keep out variable values fixed in this example and we also created c, a constant tensor which is also the f function’s constant parameter taking a fixed, or constant, value of 5. The graph shows this tensor parameter as constant.   We also did something else that wasn’t really necessary – built a constant tensor for the power in the tf.pow() operator. We only did this so you could see it visually in the graph as the circle named square. The next code will evaluate the function inside a session: init = tf.global\_variables\_initializer() # prepare to initialize all variables with tf.Session() as sess:    ​ init.run() # Initialize x and y    function\_result = f.eval() print(function\_result) Output \[66\] To summarize what you learned here, TensorFlow works three  components: 

*   Graphs - where all the operations and tensors are computed 
*   Tensors – representing the data that flows through the graphs. These are the graph edges 
*   Sessions – where all the operations are executed 

Creating Constant Tensors 

| Constant  || Object  |
| --- | --- |
| D0  || tf.constant(1, tf.int16)  |
| D1  || tf.constant(\[1,3,5\], tf.int16)  |
| D2  || tf.constant(\[ \[1, 2\], \[3, 4\] \],tf.int16)  |
| D3  || tf.constant(\[ \[\[1, 2\],\[3, 4\], \[5, 6\]\] \], tf.int16)  |

Creating Operators 

| Creating Operator  || Object  |
| --- | --- |
| a+b  || tf.add(a, b)  |
| a\*b  || tf.multiply(a, b)  |

Creating Variable Tensors 

| Creating Variable  || Object  |
| --- | --- |
| randomized value  || tf.get\_variable("var", \[1, 2\])  |
| initialized first value  || tf.get\_variable("var\_init\_2", dtype=tf.int32, initializer=\[ \[1, 2\], \[3, 4\] \])  |

Opening a Session 

| Session  || Object  |
| --- | --- |
| Create session  || tf.Session()  |
| Run session  || tf.Session.run()  |
| Evaluate tensor  || Variable\_name.eval()  |
| Close session  || Sess.Close()  |
| Session by block  || with tf.Session() as sess:  |

TensorBoard Graph Visualization Example ![](image_rsrc9SG.jpg)First off, what is TensorBoard? It is an interface used for visualizing the graph, and also provides other tools that help us understand the model, debug it and optimize it. The picture below is from the graph that you will be generating and it shows the main panel: ![](image_rsrc9U3.jpg)The image below shows the TensorBoard panel where you can see different tabs linked to the information added when the model is run: ![](image_rsrc9U4.jpg)Those tabs are: 

*   Scalars – this tab shows lots of different information that is useful in the training 
*   Graphs – this shows the model 
*   Histogram – this helps us display the weights 
*   Distribution –  this helps us display the weight distribution 
*   Projector – this shows the PCS (principal component analysis) and the T-SNE algorithm which is used for dimensionality reduction 

What we are going to do is take a simple deep learning model and train it. Take a look at the graph below; it shows you how the model works: ![](image_rsrc9U5.jpg)

1.  The data is enqueued to the model which means we push an equal amount of data to the batch size to our model, indicating the data foods that follow each iteration. 
2.  The data is fed to the tensors 
3.  The model is trained 
4.  The number of baches used during training is displayed. 
5.  The model is saved to disk. 

So, what is the idea behind TensorBoard? It is simple; it helps us inspect the neural network. It helps us understand dependencies between each operation, how weights are computed and it also shows us the loss function, among other information. Bringing all of this together gives us the best tool to debug the model and figure out how to make it better. The image below will give you an idea of the usefulness of the graph: ![](image_rsrc9U6.jpg)Neural networks determine the best way to connect the neurons and the number of layers needed to predict the outcome.  Once the architecture has been defined, the model needs to be trained but we also need the metrics to help us compute how accurate the prediction is. This is the loss function and our objective is to minimize it, i.e. ensure fewer errors from the model. Every algorithm, regardless of what it is, will repeat the computations over and again until the loss is reduced to a flatter line. A learning rate must be defined to help minimize the loss, indicating the speed you want the model learning at. If the rate is set too high,  the model will not have enough time to do any learning, which is what you can see on the left of the picture above. The line moves up and down, which means the predictions are pure guesswork. The right side of the  image indicates a decrease in the loss over each iteration until the line flattens. At that point, a solution has been found. TensorBoard helps us see these metrics and shows where they may be any issues. Neural networks can take weeks in some cases to get to a solution and TensorBoard frequently updates the metrics. By using TensorBoard, you no longer have to wait to see if the model is training properly. Instead, just open the tool and you can see what’s going on and where changes need to be made. Using TensorBoard Now we are going to look at how to use TensorBoard. The first thing you need to do is import the required libraries for the training: \## Import library import tensorflow as tf import numpy as np Next, the data must be created; ours is an array containing five columns and 10,000 rows: X\_train = (np.random.sample((10000,5))) y\_train =  (np.random.sample((10000,1))) X\_train.shape Output (10000, 5) The codes you see below are going to transform our data and create our model. Note that we have set the learning rates as equal to 0.1. If this were higher, the models would fail to find a solution, which is what we saw in the earlier image. Most of our TensorFlow tutorials use a TensorFlow API called the TensorFlow estimator to hold the mathematical computations. Creating log files requires that the path is specified and we use the argument called model\_dir for this. In our example,  the model will  be stored in the working directory where your Python file or notebook are stored. TensorFlow creates a folder in this path and names it train, giving it a child folder called linreg: feature\_columns = \[ tf.feature\_column.numeric\_column('x', shape=X\_train.shape\[1:\])\] DNN\_reg = tf.estimator.DNNRegressor(feature\_columns=feature\_columns, \# Indicate where the log file should be stored model\_dir='train/linreg',    hidden\_units=\[500, 300\],    optimizer=tf.train.ProximalAdagradOptimizer(      learning\_rate=0.1,      l1\_regularization\_strength=0.001    ) ) Output INFO:tensorflow:Using default config. INFO:tensorflow:Using config: {'\_model\_dir': 'train/linreg', '\_tf\_random\_seed': None, '\_save\_summary\_steps': 100, '\_save\_checkpoints\_steps': None, '\_save\_checkpoints\_secs': 600, '\_session\_config': None, '\_keep\_checkpoint\_max': 5, '\_keep\_checkpoint\_every\_n\_hours': 10000, '\_log\_step\_count\_steps': 100, '\_train\_distribute': None, '\_service': None, '\_cluster\_spec': <tensorflow.python.training.server\_lib.ClusterSpec object at 0x1818e63828>, '\_task\_type': 'worker', '\_task\_id': 0, '\_global\_id\_in\_cluster': 0, '\_master': '', '\_evaluation\_master': '', '\_is\_chief': True, '\_num\_ps\_replicas': 0, '\_num\_worker\_replicas': 1} The final step trains the model and, throughout training, information is written by TensorFlow into the model directory: \# Train estimator train\_input = tf.estimator.inputs.numpy\_input\_fn(    x={"x": X\_train},    y=y\_train, shuffle=False,num\_epochs=None) DNN\_reg.train(train\_input,steps=3000) Output INFO:tensorflow:Calling model\_fn. INFO:tensorflow:Done calling model\_fn. INFO:tensorflow:Create CheckpointSaverHook. INFO:tensorflow:Graph was finalized. INFO:tensorflow:Running local\_init\_op. INFO:tensorflow:Done running local\_init\_op. INFO:tensorflow:Saving checkpoints for 1 into train/linreg/model.ckpt. INFO:tensorflow:loss = 40.060104, step = 1 INFO:tensorflow:global\_step/sec: 197.061 INFO:tensorflow:loss = 10.62989, step = 101 (0.508 sec) INFO:tensorflow:global\_step/sec: 172.487 INFO:tensorflow:loss = 11.255318, step = 201 (0.584 sec) INFO:tensorflow:global\_step/sec: 193.295 INFO:tensorflow:loss = 10.604872, step = 301 (0.513 sec) INFO:tensorflow:global\_step/sec: 175.378 INFO:tensorflow:loss = 10.090343, step = 401 (0.572 sec) INFO:tensorflow:global\_step/sec: 209.737 INFO:tensorflow:loss = 10.057928, step = 501 (0.476 sec) INFO:tensorflow:global\_step/sec: 171.646 INFO:tensorflow:loss = 10.460144, step = 601 (0.583 sec) INFO:tensorflow:global\_step/sec: 192.269 INFO:tensorflow:loss = 10.529617, step = 701 (0.519 sec) INFO:tensorflow:global\_step/sec: 198.264 INFO:tensorflow:loss = 9.100082, step = 801 (0.504 sec) INFO:tensorflow:global\_step/sec: 226.842 INFO:tensorflow:loss = 10.485607, step = 901 (0.441 sec) INFO:tensorflow:global\_step/sec: 152.929 INFO:tensorflow:loss = 10.052481, step = 1001 (0.655 sec) INFO:tensorflow:global\_step/sec: 166.745 INFO:tensorflow:loss = 11.320213, step = 1101 (0.600 sec) INFO:tensorflow:global\_step/sec: 161.854 INFO:tensorflow:loss = 9.603306, step = 1201 (0.619 sec) INFO:tensorflow:global\_step/sec: 179.074 INFO:tensorflow:loss = 11.110269, step = 1301 (0.556 sec) INFO:tensorflow:global\_step/sec: 202.776 INFO:tensorflow:loss = 11.929443, step = 1401 (0.494 sec) INFO:tensorflow:global\_step/sec: 144.161 INFO:tensorflow:loss = 11.951693, step = 1501 (0.694 sec) INFO:tensorflow:global\_step/sec: 154.144 INFO:tensorflow:loss = 8.620987, step = 1601 (0.649 sec) INFO:tensorflow:global\_step/sec: 151.094 INFO:tensorflow:loss = 10.666125, step = 1701 (0.663 sec) INFO:tensorflow:global\_step/sec: 193.644 INFO:tensorflow:loss = 11.0349865, step = 1801 (0.516 sec) INFO:tensorflow:global\_step/sec: 189.707 INFO:tensorflow:loss = 9.860596, step = 1901 (0.526 sec) INFO:tensorflow:global\_step/sec: 176.423 INFO:tensorflow:loss = 10.695, step = 2001 (0.567 sec) INFO:tensorflow:global\_step/sec: 213.066 INFO:tensorflow:loss = 10.426752, step = 2101 (0.471 sec) INFO:tensorflow:global\_step/sec: 220.975 INFO:tensorflow:loss = 10.594796, step = 2201 (0.452 sec) INFO:tensorflow:global\_step/sec: 219.289 INFO:tensorflow:loss = 10.4212265, step = 2301 (0.456 sec) INFO:tensorflow:global\_step/sec: 215.123 INFO:tensorflow:loss = 9.668612, step = 2401 (0.465 sec) INFO:tensorflow:global\_step/sec: 175.65 INFO:tensorflow:loss = 10.009649, step = 2501 (0.569 sec) INFO:tensorflow:global\_step/sec: 206.962 INFO:tensorflow:loss = 10.477722, step = 2601 (0.483 sec) INFO:tensorflow:global\_step/sec: 229.627 INFO:tensorflow:loss = 9.877638, step = 2701 (0.435 sec) INFO:tensorflow:global\_step/sec: 195.792 INFO:tensorflow:loss = 10.274586, step = 2801 (0.512 sec) INFO:tensorflow:global\_step/sec: 176.803 INFO:tensorflow:loss = 10.061047, step = 2901 (0.566 sec) INFO:tensorflow:Saving checkpoints for 3000 into train/linreg/model.ckpt. INFO:tensorflow:Loss for final step: 10.73032. <tensorflow.python.estimator.canned.dnn.DNNRegressor at 0x1818e63630> All of this information can be seen in TensorBoard. Now the log events are written, TensorBoard can be opened. It runs on port 6006, while Jupyter runs on port 8888. Mac OS \# Different for you cd /Users/HappyMonday/tuto\_TF source activate hello-tf! The notebook is stored in /Users/HappyMonday/tuto\_TF Windows cd C:\\Users\\Admin\\Anaconda3 activate hello-tf The notebook is stored in C:\\Users\\Admin\\Anaconda3 The following code will launch TensorBoard: Mac OS tensorboard --logdir=./train/linreg Windows tensorboard --logdir=.\\train\\linreg TensorBoard is located at URL: http://localhost:6006 Copy the URL and paste it into your browser and you should see the  graph. If you see this, or something like it, instead, it means that TensorBoard cannot locate the log file. Check that cd pointed to the correct path and also make sure that the log file has actually been created. If not, the code needs to be rerun: ![](image_rsrc9U7.jpg)I’m going to end this here. I could go on for much longer about TensorFlow and TensorBoard but I need to move on to Keras. You should now have a good idea of how it all works though. 

Part Three An Introduction to Keras ![](image_rsrc9SG.jpg)

What is Keras? ![](image_rsrc9TV.jpg)Keras is an incredibly popular open-source Python library for neural networks. It runs on TensorFlow or Theano and was designed as a modular library by Francis Chollet, an engineer for Google. It is one of the fastest and most user-friendly of all the Python libraries. We don’t use Keras for low-level computation. Instead, Keras uses a different library called the Backend to do it. In short, Keras is a high-level API wrapper for low-level APIs that can run on Theano, TensorFlow and even CNTK. It handles how we make models.  It handles how we define layers and how we set multiple input models up. It also helps us compile the model with loss functions and optimizer functions and the training process with a fit function. As we said, forget using it to handle low-level API stuff like making graphs, tensors and variables; it all that gets done by the backend engine. So, what will you learn here? You will learn: 

*   What Keras is 
*   What the backend is, including the TensorFlow, Theano and CNTK backends 
*   Keras vs. TensorFlow 
*   The advantages of using Keras 
*   How to install it 
*   The fundamentals of Keras for deep learning 
*   How to fine-tune and use pre-trained Keras models 
*   Facial recognition 

You will find plenty of practical examples along the way to help you understand how Keras works. What is a Backend? It is a Keras term, the part of Keras the performs the lower-level computations like creating the tensors, convolutions, and lots of other stuff, using libraries like TensorFlow to help. The backend engine is responsible for computing and developing the models. The default backend is TensorFlow, which suits our purposes, but there are other backends that we can change to within the configuration. Theano, TensorFlow, and CNTK Backends Theano was developed at the University of Montreal in Quebec, Canada by the MILA group. An open-source project, it was the very first framework to be widely used. Theano is one of the popular Python libraries that helps us with mathematical operations in multi-dimensional arrays using SciPy or NumPy. Theano makes use of GPUs for much faster computation and it can produce symbolic graphs for gradient computations automatically. The official Theano website claims that the library recognizes expressions that are numerically unstable and computes them using algorithms that are stable. TensorFlow is fast rising in deep learning and was developed by Google Brain. It is one of the more popular tools for deep learning with plenty of features, which we already discussed in the previous section. The final backend engine is CNTK (Microsoft Cognitive Toolkit,) an open-source framework for deep learning developed by Microsoft. CNTK is capable of running on multiple GPUs to train models on huge scales. In some cases, CNTK beat Theano and TensorFlow in terms of the reporting speed. Keras vs. TensorFlow The best way to show you how Keras and TensorFlow compare is  this: 

| Parameters  || Keras  || TensorFlow  |
| --- | --- | --- |
| Type  || High-level API wrapper  || Low-level API  |
| Complexity  || Easy if you use Python  || Some TensorFlow syntaxes must be learned  |
| Purpose  || Fast to deploy and used to make standard-layered models  || Used for making computational graphs or model layers  |
| Tools  || Makes use of other API debugging tools like TDBG  || Provides you with visualization tools in TensorBoard  |
| Community  || Backed by a large and active community  || Backed by a large and active community and lots of shared resources.  |

Keras Advantages Keras offers several advantages: 

*   Quick to deploy and user-friendly – Keras is one of the quickest ways of creating network models and you can create a simple one with just a few lines of code. Have a look at this example: 

from keras.models import Sequential from keras.layers import Dense, Activation model = Sequential() model.add(Dense(64, activation='relu', input\_dim=50)) #input  shape of 50 model.add(Dense(28, activation='relu')) #input shape of 50 model.add(Dense(10, activation='softmax')) And because the API is user-friendly, the process is easily understood. The code can be written using a simple function and we don’t need to think about setting multiple parameters. 

*   Backed by a large community – Multiple AI communities use Keras for deep learning and many publish codes and tutorials that are freely available to the public. 
*   Multiple Backends – you can choose between TensorFlow, Theano or CNTK to use as your Keras backend. Different backends suit different projects so which one you choose will depend entirely on your needs and each has its own advantages.  
*   Works cross-platform and makes model deployment easy – Keras can be deployed on multiple platforms, including iOS devices with CoreML, a web browser using .js support, Android devices using TensorFlow \\android, Raspberry Pi and cloud engines, to name a few. 

Support for multiple GPUs – Keras can be trained on one GPU or you can use it on several at once. It has support built-in for data parallelism which means large amounts of data can be processed at the same time and the data can be trained much quicker. 

How to Install Keras on  
Windows and Mac OS ![](image_rsrc9TV.jpg)Before we go any further, we should look at how to install Keras on your Windows or Mac OS computer. First, we need to look at the different ways it can be installed. Direct Install or Virtual Environment So, which is best? Installing it directly to your current Python distribution or using a virtual environment? A virtual environment is probably your best bet if you are running lots of projects because each project may require a different version of any one of the libraries Python offers. Let’s say that your project requires Python 3.5 with OpenCV 3.3 and uses an old Keras-Theano backend. But you have another project that you need to use Keras for and it needs the latest version of Keras, a backend of TensorFlow and support for Python 3.6.6. You can see how difficult it would be if you used a direct install method. Because we don’t want conflicts between the libraries, a virtual environment is the best bet. We can also use other platforms to do the computation, such as Amazon Web Services. Amazon Web Services (AWS) The AWS platform offers a cloud computing service alongside lots of other products for use by researchers. They ensure that we can use their products straight from the internet by renting networking, hardware, databases, and more. One of the most popular of their deep learning services is the Amazon Machine Image Deep Learning Service, better known as DL. AWS also offers a virtual environment in the AWS EC2 service. It’s called AWS Deep Learning AMI and is useful for helping researchers  with deep learning. DLAMI provides services to suit both small SPU engines right up to the most powerful multiple GPU systems with cuDNN and CUDA preconfigures and offering several deep learning frameworks. Amazon SageMaker SageMaker is another Amazon dee learning platform that helps with training deep learning models with the best algorithm and deploying it. This is the easiest method for using Keras: 

1.  Set up an [Amazon SageMaker](https://console.aws.amazon.com/sagemaker/) account 
2.  Open the console and click the option to Create Notebook Instance 
3.  Type in your Notebook name 
4.  Now you need to create an IAM role which makes an AMI role in the AmazonSageMaker-Executionrole-YYYYMMDD|HHmmSS format 
5.  Click on Create Notebook Instance again and SageMaker will launch the new instance – this may take a few moments 

If you want to use your VPC to access resources, you need to enable the Direct Internet Access option. If you don’t, the notebook will not have access to the internet and, as such, will not be able to host or train any models. 

6.  Launch the notebook instance by clicking on Open 
7.  Click New>conda\_tensorflow\_p36 in Jupyter and you can begin coding. 

Install Keras Before TensorFlow and Keras can be installed, you need to install pip, Python and virtualenv, if you haven’t already. These instructions work for both Mac and Windows systems: 

1.  Install Python from  [https://python.org/downloads](https://python.org/downloads) 
2.  pip should already be installed by default with Python so open the command or terminal prompt and type int eh following commands to check it is there: 

Mac OS $ python -m pip –version Windows C:\\> py -m pip –version 

3.  Next use the following command to install virtualenv 

pip3 install –U pip virtualenv Install Microsoft Visual C++ 2015 Redistributable Update 3 

4.  [Download Visual Studio](https://www.microsoft.com/en-us/download/details.aspx?id=53587) onto your computer 
5.  Open it and click on Redistributables>Build Tools 
6.  Download Microsoft Visual C++ Redistributable Update 3 and install it 

Now you can run the following script pip3 install virtualenv Virtual Environment The virtual environment helps to isolate the working system from the main one so type in this command virtualenv –-system-site-packages –p python3 ./venv And this code activates the environment .\\venv\\Scripts\\activate Once the environment is prepared, we need to enable TENSORFLOW AS THE Keras backend. We do that with this command: pip install --upgrade tensorflow If TensorFlow needs GPU support, use the following command: pip install --upgrade tensorflow-gpu Now we need to make sure the installation worked so type in the following: user@user:~$ python Python 3.6.4 (default, Mar 20 2018, 11:10:20) \[GCC 5.4.0 20160609\] on linux Type "help", "copyright", "credits" or "license" for more information. \>>> import tensorflow \>>> If you don’t see any error messages, it all worked okay. Install Keras Now we can install Keras by typing in the following command: pip install keras Keras will be installed with all necessary dependencies. Before we can begin to use it, we need to check that Keras uses Tensorflow as the backend so type the following, which will open the configuration file: gedit ~/.keras/keras.json You should see something similar to this on your screen: { "floatx": "float32", "epsilon": 1e-07, "backend": "tensorflow", "image\_data\_format": "channels\_last" } If you see this, TensorFlow is in use as the backend, exactly as we  wanted. Now you can type in the following to run it: user@user:~$ python3 Python 3.6.4 (default, Mar 20 2018, 11:10:20) \[GCC 5.4.0 20160609\] on linux Type "help", "copyright", "credits" or "license" for more information. \>>> import keras Using TensorFlow backend. \>>> 

Keras Fundamentals for Deep Learning ![](image_rsrc9TV.jpg)The primary Keras structure is the model, and this is responsible for defining a network’s graph. Layers can be added to models already created to make a custom model that fits your specific project. Let’s look at a sequential model and the common deep learning layers: Sequential Model from keras.models import Sequential from keras.layers import Dense, Activation,Conv2D,MaxPooling2D,Flatten,Dropout model = Sequential() Convolutional Layer This shows an input layer as a convolutional layer. Its shape is 320x320x3, and it has 48 3x3 filters. The activation function used is ReLU. input\_shape=(320,320,3) #this is the input shape of an image 320x320x3 model.add(Conv2D(48, (3, 3), activation='relu', input\_shape= input\_shape)) another type is model.add(Conv2D(48, (3, 3), activation='relu')) MaxPooling Layer MaxPool2d is used for downsampling the input representation and you must specify the size of the kernel. model.add(MaxPooling2D(pool\_size=(2, 2))) Dense Layer Here, you can add a Dully Connected layer and just specify what size output you want. model.add(Dense(256, activation='relu')) Dropout Layer Here, you can a dropout layer with a probability of 50%. model.add(Dropout(0.5)) Compilation, Training and Evaluation Once the model has been defined, we can begin training it. First, the network must be compiled with the optimizer and loss functions so that the network can change the weights and minimize the loss. model.compile(loss='mean\_squared\_error', optimizer='adam') Now, we can begin training. The training and validation data are fed to the model using the fit function. This lets the network train the data in batches and we can also set the epochs. model.fit(X\_train, X\_train, batch\_size=32, epochs=10, validation\_data=(x\_val, y\_val)) The last step is to use the test data to evaluate our model. score = model.evaluate(x\_test, y\_test, batch\_size=32) Simple Linear Regression This is a simple linear regression model: import keras from keras.models import Sequential from keras.layers import Dense, Activation import numpy as np import matplotlib.pyplot as plt x = data = np.linspace(1,2,200) y = x\*4 + np.random.randn(\*x.shape) \* 0.3 model = Sequential() model.add(Dense(1, input\_dim=1, activation='linear')) model.compile(optimizer='sgd', loss='mse', metrics=\['mse'\]) weights = model.layers\[0\].get\_weights() w\_init = weights\[0\]\[0\]\[0\] b\_init = weights\[1\]\[0\] print('Linear regression model initialized with weights w: %.2f, b: %.2f' % (w\_init, b\_init)) model.fit(x,y, batch\_size=1, epochs=30, shuffle=False) weights = model.layers\[0\].get\_weights() w\_final = weights\[0\]\[0\]\[0\] b\_final = weights\[1\]\[0\] print('Linear regression model trained with weight w: %.2f, b: %.2f' % (w\_final, b\_final)) predict = model.predict(data) plt.plot(data, predict, 'b', data , y, 'k.') plt.show() Once the data is trained, you should see an output similar to this: ![](image_rsrc9U8.jpg)The initial weight is: Linear regression model is initialized with weights w: 0.37, b: 0.00 And the final weight is: Linear regression model is trained to have weight w: 3.70, b: 0.61 Fine-Tuning and Using Pre-Trained Keras Models When we fine-tune, we are tweaking models that have already been trained in a way that the parameters work for the new model. Training from scratch on new models requires vast amounts of data to ensure the network can find all the parameters. In our case, we are using a pre-trained model – the parameters have already been learned and we have the weights. Let’s say, for example, that we want a model trained to deal with a classification problem but we don’t have much data. Solving it is much easier if we use the Transfer Learning and Fine-Tuning method.  By using a network that has already been trained and has  weights, there is no need to go down the route of training the entire network. All we need to do is train the final layer as that is what will solve the problem. Note – the following tutorial is for information only. Later, there will be a practical example you can follow along. Preparing the Network Model Keras comes pre-loaded with lots of different pre-trained models, such as: 

*   InceptionResNetV2 
*   InceptionV3 
*   MobileNet 
*   ResNet 
*   VGG16 
*   Xception 

We will use the VGG16 model and, for the model weight, we will use imageNet. The network will be fine-tuned to classify no less than eight class types using some images taken from the Kaggle Natural Images Dataset. Upload Data to AWS S3 Bucket We are going to use natural images from eight classes to train the model but first, the data needs to be uploaded to Amazon S3 Bucket. 

1.  Set up and log in to SW3 
2.  Click on Create Bucket, choose a Bucket name and set your region; click on Create 
3.  Your bucket is now ready to use but you can see that the access is set to Private. That’s fine if you want to keep it that way but if the Bucket needs public access, you can change it in Bucket Properties. 
4.  Now you are ready to upload the training data into the bucket. Click the Upload button and click on the file name; copy the link so it can be downloaded. 

Preparing the Data Next, we use the Keras ImageDataGenerator to get our training data. 

1.  First, the data needs to be downloaded so, using the link you copied earlier, use the following code – change the image file to match your own:

!wget https://s3.us-east-2. amazonaws.com/naturalimages02/images.tar.gz !tar -xzf images.tar.gz Once the data is downloaded, the training process can begin: from keras.preprocessing.image import ImageDataGenerator import numpy as np import matplotlib.pyplot as plt train\_path = 'images/train/' test\_path = 'images/test/' batch\_size = 16 image\_size = 224 num\_class = 8 train\_datagen = ImageDataGenerator(validation\_split=0.3, shear\_range=0.2, zoom\_range=0.2, horizontal\_flip=True) train\_generator = train\_datagen.flow\_from\_directory( directory=train\_path, target\_size=(image\_size,image\_size) , batch\_size=batch\_size, class\_mode='categorical', color\_mode='rgb', shuffle=True) ImageDataGenerator creates X\_training data from a directory and the subdirectory is used as each object’s class. The image is loaded with the color mode RGB, the Y\_training data is given the categorical class mode and we have a batch of 16. The data can now be shuffled. We can use matplotlib to plot the images and show them to us randomly: x\_batch, y\_batch = train\_generator.next() fig=plt.figure() columns = 4 rows = 4 for i in range(1, columns\*rows): num = np.random.randint(batch\_size) image = x\_batch\[num\].astype(np.int) fig.add\_subplot(rows, columns, i) plt.imshow(image) plt.show() Output ![](image_rsrc9U9.jpg)After that, VGG16 can be used to create the model with pre-trained imageNet weights. The layers are frozen so they cannot be trained, which helps to reduce the time take for the computation. Creating VGG16 Model This is how the model is created: import keras from keras.models import Model, load\_model from keras.layers import Activation, Dropout, Flatten, Dense from keras.preprocessing.image import ImageDataGenerator from keras.applications.vgg16 import VGG16 #Load the VGG model base\_model = VGG16(weights='imagenet', include\_top=False, input\_shape=(image\_size, image\_size, 3)) print(base\_model.summary() ) \# Freeze the layers for layer in base\_model.layers: layer.trainable = False \# # Create the model model = keras.models.Sequential() \# # Add the vgg convolutional base model model.add(base\_model) \# # Add new layers model.add(Flatten()) model.add(Dense(1024, activation='relu')) model.add(Dense(1024, activation='relu')) model.add(Dense(num\_class, activation='softmax')) \# # Show a summary of the model. Check the number of trainable parameters    print(model.summary()) The model summary looks like this: Layer (type)                 Output Shape              Param #   \================================================================= vgg16 (Model)                (None, 7, 7, 512)         14714688 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ flatten\_1 (Flatten)          (None, 25088)             0         \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ dense\_1 (Dense)              (None, 1024)              25691136 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ dense\_2 (Dense)              (None, 1024)              1049600   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ dense\_3 (Dense)              (None, 8)                 8200      \================================================================= Total params: 41,463,624 Trainable params: 26,748,936 Non-trainable params: 14,714,688 From the VGG16 Layers, we have the input, then 2 Fully Connected layers are added. These extract 1024 features along with an output layer. The output layer uses the SoftMax activation function to compute the classes. Training This is how the model is trained: \# # Compile the model from keras.optimizers import SGD model.compile(loss='categorical\_crossentropy', optimizer=SGD(lr=1e-3), metrics=\['accuracy'\]) \# # Start the training process \# model.fit(x\_train, y\_train, validation\_split=0.30, batch\_size=32, epochs=50, verbose=2) \# # #save the model \# model.save('catdog.h5') history = model.fit\_generator( train\_generator, steps\_per\_epoch=train\_generator.n/batch\_size, epochs=10) model.save('fine\_tune.h5') \# summarize history for accuracy import matplotlib.pyplot as plt plt.plot(history.history\['loss'\]) plt.title('loss') plt.ylabel('loss') plt.xlabel('epoch') plt.legend(\['loss'\], loc='upper left') plt.show() Results Epoch 1/10 432/431 \[==============================\] - 53s 123ms/step - loss: 0.5524 - acc: 0.9474 Epoch 2/10 432/431 \[==============================\] - 52s 119ms/step - loss: 0.1571 - acc: 0.9831 Epoch 3/10 432/431 \[==============================\] - 51s 119ms/step - loss: 0.1087 - acc: 0.9871 Epoch 4/10 432/431 \[==============================\] - 51s 119ms/step - loss: 0.0624 - acc: 0.9926 Epoch 5/10 432/431 \[==============================\] - 51s 119ms/step - loss: 0.0591 - acc: 0.9938 Epoch 6/10 432/431 \[==============================\] - 51s 119ms/step - loss: 0.0498 - acc: 0.9936 Epoch 7/10 432/431 \[==============================\] - 51s 119ms/step - loss: 0.0403 - acc: 0.9958 Epoch 8/10 432/431 \[==============================\] - 51s 119ms/step - loss: 0.0248 - acc: 0.9959 Epoch 9/10 432/431 \[==============================\] - 51s 119ms/step - loss: 0.0466 - acc: 0.9942 Epoch 10/10 432/431 \[==============================\] - 52s 120ms/step - loss: 0.0338 - acc: 0.9947 ![](image_rsrc9UA.jpg)You can see from the results that the losses are significantly reduced and the model accuracy is nearly 100%. As you can see, our losses are dropped significantly and the accuracy is almost 100%. For testing our model, we randomly picked images over the internet and put them in the test folder with a different class to test Testing Our Model To test the model, random images were chosen from the internet and  placed into the test folder with another class. model = load\_model('fine\_tune.h5') test\_datagen = ImageDataGenerator() train\_generator = train\_datagen.flow\_from\_directory( directory=train\_path, target\_size=(image\_size,image\_size), batch\_size=batch\_size, class\_mode='categorical', color\_mode='rgb', shuffle=True) test\_generator = test\_datagen.flow\_from\_directory( directory=test\_path, target\_size=(image\_size, image\_size), color\_mode='rgb', shuffle=False, class\_mode='categorical', batch\_size=1) filenames = test\_generator.filenames nb\_samples = len(filenames) fig=plt.figure() columns = 4 rows = 4 for i in range(1, columns\*rows -1): x\_batch, y\_batch = test\_generator.next() name = model.predict(x\_batch) name = np.argmax(name, axis=-1) true\_name = y\_batch true\_name = np.argmax(true\_name, axis=-1 ) label\_map = (test\_generator.class\_indices) label\_map = dict((v,k) for k,v in label\_map.items()) #flip k,v predictions = \[label\_map\[k\] for k in name\] true\_value = \[label\_map\[k\] for k in true\_name\] image = x\_batch\[0\].astype(np.int) fig.add\_subplot(rows, columns, i) plt.title(str(predictions\[0\]) + ':' + str(true\_value\[0\])) plt.imshow(image) plt.show() And from the results, out of 14 images, only one was incorrectly classified. ![](image_rsrc9UB.jpg)

Face Recognition Neural  
Network with Keras ![](image_rsrc9TV.jpg)Facial recognition is growing in popularity and is widely used by systems that need to identify specific people, as well as estimating their age and learning facial expressions. Whenever you tag a friend in a Facebook photo, for example, facial recognition has been used to do it. So, how does it all work? Using Facebook as an example, whenever a person is tagged in an image, Facebook learns it using artificial intelligence. From then on, it will try to predict that name and will continue until it gets it right. When it's right, you won’t have to tag your friends yourself anymore, as Facebook will do it for you. We’re going to build our own facial recognition system using Keras and deep learning. Network Model For this, we will use the VGG16 model and add a VGGFace weight. VGGFace is Keras’s Deep Face Recognition and the network architecture is VGG16. VGGFace can be freely downloaded from [GitHub](https://github.com/rcmalli/keras-vggface) so go ahead and do that now. Here’s the code you need: from keras.applications.vgg16 import VGG16 from keras\_vggface.vggface import VGGFace face\_model = VGGFace(model='vgg16', weights='vggface', input\_shape=(224,224,3)) face\_model.summary() The network summary looks like this: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ Layer (type)                 Output Shape              Param #   \================================================================= input\_1 (InputLayer)         (None, 224, 224, 3)       0         \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv1\_1 (Conv2D)             (None, 224, 224, 64)      1792      \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv1\_2 (Conv2D)             (None, 224, 224, 64)      36928     \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ pool1 (MaxPooling2D)         (None, 112, 112, 64)      0         \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv2\_1 (Conv2D)             (None, 112, 112, 128)     73856     \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv2\_2 (Conv2D)             (None, 112, 112, 128)     147584    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ pool2 (MaxPooling2D)         (None, 56, 56, 128)       0         \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv3\_1 (Conv2D)             (None, 56, 56, 256)       295168    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv3\_2 (Conv2D)             (None, 56, 56, 256)       590080    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv3\_3 (Conv2D)             (None, 56, 56, 256)       590080    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ pool3 (MaxPooling2D)         (None, 28, 28, 256)       0         \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv4\_1 (Conv2D)             (None, 28, 28, 512)       1180160   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv4\_2 (Conv2D)             (None, 28, 28, 512)       2359808   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv4\_3 (Conv2D)             (None, 28, 28, 512)       2359808   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ pool4 (MaxPooling2D)         (None, 14, 14, 512)       0         \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv5\_1 (Conv2D)             (None, 14, 14, 512)       2359808   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv5\_2 (Conv2D)             (None, 14, 14, 512)       2359808   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv5\_3 (Conv2D)             (None, 14, 14, 512)       2359808   \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ pool5 (MaxPooling2D)         (None, 7, 7, 512)         0         \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ flatten (Flatten)            (None, 25088)             0         \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ fc6 (Dense)                  (None, 4096)              102764544 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ fc6/relu (Activation)        (None, 4096)              0         \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ fc7 (Dense)                  (None, 4096)              16781312 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ fc7/relu (Activation)        (None, 4096)              0         \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ fc8 (Dense)                  (None, 2622)              10742334 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ fc8/softmax (Activation)     (None, 2622)              0         \================================================================= Total params: 145,002,878 Trainable params: 145,002,878 Non-trainable params: 0 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ Traceback (most recent call last): To speed up the training, we’ll do what we discussed earlier –Transfer Learning and Fine-Tuning. First, we need to freeze the model’s base layers so we don’t train them: for layer in face\_model.layers: layer.trainable = False Then, so the model recognizes the test faces, we need to add layers. We’ll add in two Fully Connected layers and one output layer with five faces for detection. from keras.models import Model, Sequential from keras.layers import Input, Convolution2D, ZeroPadding2D, MaxPooling2D, Flatten, Dense, Dropout, Activation person\_count = 5 last\_layer = face\_model.get\_layer('pool5').output x = Flatten(name='flatten')(last\_layer) x = Dense(1024, activation='relu', name='fc6')(x) x = Dense(1024, activation='relu', name='fc7')(x) out = Dense(person\_count, activation='softmax', name='fc8')(x) custom\_face = Model(face\_model.input, out) The network summary looks like this: Layer (type)                 Output Shape              Param # \================================================================= input\_1 (InputLayer)         (None, 224, 224, 3)       0 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv1\_1 (Conv2D)             (None, 224, 224, 64)      1792 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv1\_2 (Conv2D)             (None, 224, 224, 64)      36928 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ pool1 (MaxPooling2D)         (None, 112, 112, 64)      0 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv2\_1 (Conv2D)             (None, 112, 112, 128)     73856 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv2\_2 (Conv2D)             (None, 112, 112, 128)     147584 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ pool2 (MaxPooling2D)         (None, 56, 56, 128)       0 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv3\_1 (Conv2D)             (None, 56, 56, 256)       295168 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv3\_2 (Conv2D)             (None, 56, 56, 256)       590080 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv3\_3 (Conv2D)             (None, 56, 56, 256)       590080 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ pool3 (MaxPooling2D)         (None, 28, 28, 256)       0 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv4\_1 (Conv2D)             (None, 28, 28, 512)       1180160 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv4\_2 (Conv2D)             (None, 28, 28, 512)       2359808 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv4\_3 (Conv2D)             (None, 28, 28, 512)       2359808 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ pool4 (MaxPooling2D)         (None, 14, 14, 512)       0 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv5\_1 (Conv2D)             (None, 14, 14, 512)       2359808 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv5\_2 (Conv2D)             (None, 14, 14, 512)       2359808 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ conv5\_3 (Conv2D)             (None, 14, 14, 512)       2359808 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ pool5 (MaxPooling2D)         (None, 7, 7, 512)         0 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ flatten (Flatten)            (None, 25088)             0 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ fc6 (Dense)                  (None, 1024)              25691136 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ fc7 (Dense)                  (None, 1024)              1049600 \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ fc8 (Dense)                  (None, 5)                 5125 \================================================================= Total params: 41,460,549 Trainable params: 26,745,861 Non-trainable params: 14,714,688 So, following the pool5 layer, you can see that it is flattened down to one feature vector and the dense layer uses this for the final recognition. Prepare the Faces The next step is to prepare the faces and we’ll use a directory that consists of images of five well-known people: 

*   Pink 
*   Colin Firth 
*   Tom Hiddleston 
*   Hugh Grant 
*   Stephen Fry 

Each folder has ten images in it for the training and the evaluation. Sure, it’s not much data but isn’t that half the challenge? Keras is going to help us prepare our data, iterating over the dataset folder and then preparing the data for use in the training process. from keras.preprocessing.image import ImageDataGenerator batch\_size = 5 train\_path = 'data/' eval\_path = 'eval/' train\_datagen = ImageDataGenerator(rescale=1./255, shear\_range=0.2, zoom\_range=0.2, horizontal\_flip=True) valid\_datagen = ImageDataGenerator(rescale=1./255, shear\_range=0.2, zoom\_range=0.2, horizontal\_flip=True) train\_generator = train\_datagen.flow\_from\_directory( train\_path, target\_size=(image\_size,image\_size), batch\_size=batch\_size, class\_mode='sparse', color\_mode='rgb') valid\_generator = valid\_datagen.flow\_from\_directory( directory=eval\_path, target\_size=(224, 224), color\_mode='rgb', batch\_size=batch\_size , class\_mode='sparse', shuffle=True, ) Training the Model We’ll begin training by compiling the network with the optimizer function and the loss function. The loss function we are using is sparse\_categorical\_crossentropy and the learning optimizer is SGD. from keras.optimizers import SGD custom\_face.compile(loss='sparse\_categorical\_crossentropy', optimizer=SGD(lr=1e-4, momentum=0.9), metrics=\['accuracy'\]) history = custom\_face.fit\_generator( train\_generator, validation\_data=valid\_generator, steps\_per\_epoch=49/batch\_size, validation\_steps=valid\_generator.n, epochs=50) custom\_face.evaluate\_generator(generator=valid\_generator) custom\_face.save('vgg\_face.h5') Epoch 25/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.4882 - acc: 0.8998 - val\_loss: 1.5659 - val\_acc: 0.5851 Epoch 26/50 10/9 \[==============================\] - 59s 6s/step - loss: 1.4882 - acc: 0.8998 - val\_loss: 1.5638 - val\_acc: 0.5809 Epoch 27/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.4779 - acc: 0.8597 - val\_loss: 1.5613 - val\_acc: 0.5477 Epoch 28/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.4755 - acc: 0.9199 - val\_loss: 1.5576 - val\_acc: 0.5809 Epoch 29/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.4794 - acc: 0.9153 - val\_loss: 1.5531 - val\_acc: 0.5892 Epoch 30/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.4714 - acc: 0.8953 - val\_loss: 1.5510 - val\_acc: 0.6017 Epoch 31/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.4552 - acc: 0.9199 - val\_loss: 1.5509 - val\_acc: 0.5809 Epoch 32/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.4504 - acc: 0.9199 - val\_loss: 1.5492 - val\_acc: 0.5975 Epoch 33/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.4497 - acc: 0.8998 - val\_loss: 1.5490 - val\_acc: 0.5851 Epoch 34/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.4453 - acc: 0.9399 - val\_loss: 1.5529 - val\_acc: 0.5643 Epoch 35/50 10/9 \[==============================\] - 60s  6s/step - loss: 1.4399 - acc: 0.9599 - val\_loss: 1.5451 - val\_acc: 0.5768 Epoch 36/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.4373 - acc: 0.8998 - val\_loss: 1.5424 - val\_acc: 0.5768 Epoch 37/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.4231 - acc: 0.9199 - val\_loss: 1.5389 - val\_acc: 0.6183 Epoch 38/50 10/9 \[==============================\] - 59s 6s/step - loss: 1.4247 - acc: 0.9199 - val\_loss: 1.5372 - val\_acc: 0.5934 Epoch 39/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.4153 - acc: 0.9399 - val\_loss: 1.5406 - val\_acc: 0.5560 Epoch 40/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.4074 - acc: 0.9800 - val\_loss: 1.5327 - val\_acc: 0.6224 Epoch 41/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.4023 - acc: 0.9800 - val\_loss: 1.5305 - val\_acc: 0.6100 Epoch 42/50 10/9 \[==============================\] - 59s 6s/step - loss: 1.3938 - acc: 0.9800 - val\_loss: 1.5269 - val\_acc: 0.5975 Epoch 43/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.3897 - acc: 0.9599 - val\_loss: 1.5234 - val\_acc: 0.6432 Epoch 44/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.3828 - acc: 0.9800 - val\_loss: 1.5210 - val\_acc: 0.6556 Epoch 45/50 10/9 \[==============================\] - 59s 6s/step - loss: 1.3848 - acc: 0.9599 - val\_loss: 1.5234 - val\_acc: 0.5975 Epoch 46/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.3716 - acc: 0.9800 - val\_loss: 1.5216 - val\_acc: 0.6432 Epoch 47/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.3721 - acc: 0.9800 - val\_loss: 1.5195 - val\_acc: 0.6266 Epoch 48/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.3622 - acc: 0.9599 - val\_loss: 1.5108 - val\_acc: 0.6141 Epoch 49/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.3452 - acc: 0.9399 - val\_loss: 1.5140 - val\_acc: 0.6432 Epoch 50/50 10/9 \[==============================\] - 60s 6s/step - loss: 1.3387 - acc: 0.9599 - val\_loss: 1.5100 - val\_acc: 0.6266 Right now, the validation accuracy is standing at around 64% which, for such a small training dataset, is pretty good. However, it can be improved and we do that adding layers or adding extra training images. We can now use a test picture to test the model with: from keras.models import load\_model from keras.preprocessing.image import load\_img, save\_img, img\_to\_array from keras\_vggface.utils import preprocess\_input test\_img = image.load\_img('test.jpg', target\_size=(224, 224)) img\_test = image.img\_to\_array(test\_img) img\_test = np.expand\_dims(img\_test, axis=0) img\_test = utils.preprocess\_input(img\_test) predictions = model.predict(img\_test) predicted\_class=np.argmax(predictions,axis=1) labels = (train\_generator.class\_indices) labels = dict((v,k) for k,v in labels.items()) predictions = \[labels\[k\] for k in predicted\_class\] print(predictions) \[‘HughGrant’\] When we used an image of Hugh Grant as the test picture, the result shows that it was predicted correctly. Using a Live Cam for the Prediction What about using a webcam input for the implementation? If we used OpenCV and Haar Face cascade to locate the face, our network model would be able to recognize the image. Again, this section is purely for information, not as a practical follow-on. First, prepare your training images – the more you have, the better the result will be. Prepare your network and train it like you did earlier and then add the following code to get an input image from a webcam: #Load trained model from keras.models import load\_model from keras\_vggface import utils import cv2 image\_size = 224 device\_id = 0 #camera\_device id model = load\_model('my faces.h5') #make labels according to your dataset folder labels = dict(firstname=0,secondname=1) #and so on print(labels) cascade\_classifier = cv2.CascadeClassifier('haarcascade\_frontalface\_default.xml') camera = cv2.VideoCapture(device\_id) while camera.isOpened(): ok, cam\_frame = camera.read() if not ok: break gray\_img=cv2.cvtColor(cam\_frame, cv2.COLOR\_BGR2GRAY) faces= cascade\_classifier.detectMultiScale(gray\_img, minNeighbors=5) for (x,y,w,h) in faces: cv2.rectangle(cam\_frame,(x,y),(x+w,y+h),(255,255,0),2) roi\_color = cam\_frame \[y:y+h, x:x+w\] roi color = cv2.cvtColor(roi\_color, cv2.COLOR\_BGR2RGB) roi\_color = cv2.resize(roi\_color, (image\_size, image\_size)) image = roi\_color.astype(np.float32, copy=False) image = np.expand\_dims(image, axis=0) image = preprocess\_input(image, version=1) # or version=2 preds = model.predict(image) predicted\_class=np.argmax(preds,axis=1 ) labels = dict((v,k) for k,v in labels.items()) name = \[labels\[k\] for k in predicted\_class\] cv2.putText(cam\_frame,str(name), (x + 10, y + 10), cv2.FONT\_HERSHEY\_SIMPLEX, 1, (255,0,255), 2) cv2.imshow('video image', cam\_frame) key = cv2.waitKey(30) if key == 27: # press 'ESC' to quit break camera.release() cv2.destroyAllWindows() Keras or TensorFlow? Which One is Best? When you are writing a script, Keras provides the simplicity, allowing us to understand everything straight away. It is a user-friendly library and dead simple to implement, with no need to create multiple variables for the model to run. That means there is no real need for us to understand all the backend details fully. TensorFlow is a low-level program that offers advanced operations and flexibility to help us create models or computational graphs. It also offers us TensorFlow which helps us visualize everything, and a debugger tool that helps us find and fix errors. Summary To summarize this part: 

*   Keras is one of the high-level APIs used for making deep learning networks easier to create and use with the help of a backend engine. 
*   It is user-friendly and easy to understand, with full Python support which makes it feel natural to use. It is one of the  best libraries for beginners who want to learn deep learning and for researchers that are looking for an easy API to use. 
*   Keras is simple to install and can be used with a virtual environment or AWS or other external platforms. 

Keras also offers multiple network models built-in so you can choose to fine-tune a pre-trained model rather than building one from scratch. 

Keras Tutorial ![](image_rsrc9TV.jpg)We don’t need too much code here but I will walk you through this final Keras model one step at a time so you know how to do it in the future. Here’s what this tutorial will teach you: 

*   Loading data 
*   Defining the Keras model 
*   Compiling the model 
*   Fitting the model 
*   Evaluating the model 
*   Bringing it all together 
*   Making the predictions 

There are a few things that must be installed and configured on your system before you start the tutorial: 

*   Python 2 or 3+ 
*   SciPy and NumPy 
*   Keras and a backend, TensorFlow or Theano 

Before you begin, create a file and call it keras\_first\_network.py – this is where the code will go. Step One – Loading the Data First, we need to define the classes and the functions we want to use. We’re going to load the dataset using NumPy and then define the models using a couple of Keras classes. We require the following imports: \# first neural network with keras tutorial from numpy import loadtxt from keras.models import Sequential from keras.layers import Dense ... Now the dataset can be loaded. We will use a popular dataset called Pima Indians, containing data regarding diabetes onset. It is a standard library available in the UCI Machine Learning repository, describing the Pima Indians patient data and whether diabetes onset in a five-year period. That makes it a binary classification problem as the values are simple – 1 for diabetes onset, 0 for none. The input variables used for describing the patients are numerical, making it simple to use on neural networks that require numerical input and a numerical output. It is perfect for this tutorial.  You can download the CSV file from: 

*   [Dataset CSV File (pima-indians-diabetes.csv)](https://raw.githubusercontent.com/jbrownlee/Datasets/master/pima-indians-diabetes.data.csv) 
*   [Dataset Details](https://raw.githubusercontent.com/jbrownlee/Datasets/master/pima-indians-diabetes.names) 

Go ahead and download it, putting it in your local working directory – where your Python file is. Name it pima-indians-diabetes.csv and save it. When you look in the file, you should see several data rows, looking something like this: 6,148,72,35,0,33.6,0.627,50,1 1,85,66,29,0,26.6,0.351,31,0 8,183,64,0,0,23.3,0.672,32,1 1,89,66,23,94,28.1,0.167,21,0 0,137,40,35,168,43.1,2.288,33,1 The file can now be loaded as a matrix of numbers and we use a function called loadtxt() from NumPy. The data has eight input variables and the last column is the single output variable. The  model we are learning will map input variables (X) in rows to one output variable (y) and this is typically written as y = f(X). We can summarize the variables like this: Input Variables (X): 

1.  How many times the patient has been pregnant 
2.  Concentration of plasma glucose after a 2-hour test for oral glucose tolerance 
3.  Diastolic blood pressure (mm Hg) 
4.  Triceps skin fold thickness (mm) 
5.  2-Hour serum insulin (mu U/ml) 
6.  Body mass index (weight in kg/(height in m)^2) 
7.  Diabetes pedigree function 
8.  Age (in years) 

Output Variables (y): 

1.  Class variable (0 or 1) 

When the CSV file has been loaded to memory, the data columns can be split into input variables and output variables. We store the data in a 2D array; the rows are the first dimension and the columns are the second dimension – written as \[rows, columns\]. Splitting the data into two arrays requires that subsets of columns are chosen using the slice operator in NumPy. The first eight columns, index 0 to index 7, are selected using the 0:8 slice. Then the output column, which is the 9th variable, is selected using index 8. \# load the dataset dataset = loadtxt('pima-indians-diabetes.csv', delimiter=',') \# split into input (X) and output (y) variables X = dataset\[:,0:8\] y = dataset\[:,8\] ... Now the neural network model is ready for defining Note that we nine columns in our dataset and the 0:8 range selects the columns indexed 0 to 7. If you have not come across this before, the simplest way to explain this is that Python indexing begins at 0 – index 0 indicates the first column, index 1 indicates the second column, and so on. Step Two – Defining Our Model Keras models are defined as sequences of layers.  We are going to create a sequential model and the layers will be added one by one until the architecture is how we want it. The first thing that must be correct is making sure the input layer has the number of input features needed. When we create the first layer, we can specify the number of layers using the input\_dim argument. We set it to 8 as we have eight variables. I can hear you asking how we know how many layers we need and what their types are. That is not an easy question to answer and there are a few heuristics that could help us. More often than not, though, the best network tends to be found through experimentation. In general, your network needs to be big enough to capture the problem’s structure. We are using a Fully Connected structure that has three layers. We use the Dense class to define the Fully Connected layers and the number of nodes or neurons in the layer is specified as the first argument. The activation argument is used to specify which activation function we are using.  We will use ReLU or Rectified Linear Unit for our activation function on layers one and two and the output layer will have the Sigmoid function. At one time, the Tanh and Sigmoid functions were the preferred activation functions for every layer but now the ReLU function gives us much better performance. We use the Sigmoid function on our output layer so that we can make sure the network output is somewhere between 0 and 1. We also want to ensure it can easily be mapped to a probability of class 1 or snapped to a classification of one or the other class with 0.5 as the default threshold. We can pull it together when each layer is added: 

*   Our model will expect data rows containing eight variables – input\_dim=8 argument 
*   Hidden layer one contains 12 nodes and the ReLU activation function is used 
*   Hidden layer two contains eight nodes and the ReLU activation function is used 
*   The output layer contains a single node and the Sigmoid activation function is used 

... \# define the keras model model = Sequential() model.add(Dense(12, input\_dim=8, activation='relu')) model.add(Dense(8, activation='relu')) model.add(Dense(1, activation='sigmoid')) ... One of the most confusing things is that shape of the model input has been defined in the initial hidden layer as an argument. This means that the code adding the first Dense layer does two things – it defines the visible layer, which is the input layer and defines the first of the hidden layers. Step Three – Compiling the Model We’ve defined the model, now it’s time to compile it. Model compilation requires good numerical libraries to be used  under the hood. This is the backend and is where we use TensorFlow or Theano. The backend makes an automatic selection on how the network should be represented for training and to make predictions and chooses the best way to run it on your GPU, CPU, or distributed. When we compile the model, we need to specify some properties that we need to train the network. Remember, when we train a network, we are trying to find the optimum set of weights for mapping the inputs to the output. The loss function we want to use for evaluating the set of weights must be specified, along with the optimizer we want to use to look through the network weights and any other metrics we might want to collect and report on throughout training. The loss argument we are using is cross-entropy, a binary classification loss function defined as binary\_crossentropy in Keras. The optimize will be defined as adam, the stochastic gradient descent algorithm which is surprisingly efficient. This is the most popular and commonly used gradient descent version. It tunes itself and provides the best results in lots of different problems. Lastly, because we are trying to solve a classification problem, we also want to collect the accuracy of the classification and report it; we use the metrics argument to define this. ... \# compile the keras model model.compile(loss='binary\_crossentropy', optimizer='adam', metrics=\['accuracy'\]) ... Step Four – Fitting the Model Now that the model has been defined and compiled, it is now time to execute it on a set of data. We call the fit() function to train (fit) our model on the data. All the training will take place over a specified number of epochs and each of those is split down into batches.  One epoch is a pass through the training dataset rows while a batch is a  number of samples the model looks at in each epoch before updating the weights. The training will take place over a specified number of iterations or epochs and we use the epochs argument to specify how many there will be. We also need to specify how many dataset rows the training will consider before updating the weights at the end of each epoch. This is the batch size and we use the batch\_size argument to set this. We are going to run quite a small number of epochs, 150, with a batch size of just 10. We can choose these just by using trial and error; the model needs to be trained enough to learn the input row data mappings to the output classifications. The model will have a certain amount of error but that levels out after a point depending on the model configuration and this is known as model convergence. ... \# fit the keras model on the dataset model.fit(X, y, epochs=150, batch\_size=10) ... At this point, the work is happening on your GPU or CPU. We are only using a CPU for this model. Step Five – Evaluating the Model The neural network has now been trained on our dataset and we can use that dataset to evaluate how the network performs. But this only provides an idea of how the algorithm might work on unseen data. We did it this way for the sake of simplicity but, if you wanted to, the data could be split into two sets – training and testing. The model is evaluated on the training set by using the function called evaluate() – the same inputs and outputs that were used to train the model are passed to this function. This results in new predictions for each pair of inputs and outputs being generated and the scores are collected. This includes the metrics you might have included, like accuracy, along with the average loss. A list is returned by the evaluate() function containing two values. The first is the model’s loss on the dataset, while the second is the model’s accuracy on the dataset. We can ignore the loss because we only want to know the model accuracy: ... \# evaluate the keras model \_, accuracy = model.evaluate(X, y) print('Accuracy: %.2f' % (accuracy\*100)) Step Six – Bringing it Together That wasn’t too bad, was it? You’ve now built a neural network using Keras so let’s put it all together in a single code: \# first neural network with keras tutorial from numpy import loadtxt from keras.models import Sequential from keras.layers import Dense \# load the dataset dataset = loadtxt('pima-indians-diabetes.csv', delimiter=',') \# split into input (X) and output (y) variables X = dataset\[:,0:8\] y = dataset\[:,8\] \# define the keras model model = Sequential() model.add(Dense(12, input\_dim=8, activation='relu')) model.add(Dense(8, activation='relu')) model.add(Dense(1, activation='sigmoid')) \# compile the keras model model.compile(loss='binary\_crossentropy', optimizer='adam', metrics=\['accuracy'\]) \# fit the keras model on the dataset model.fit(X, y, epochs=150, batch\_size=10) \# evaluate the keras model \_, accuracy = model.evaluate(X, y) print('Accuracy: %.2f' % (accuracy\*100)) If you want to do things the easy way, simply copy and paste the code into the file you created and save it where your CSV file is saved. Then it can be run from the command-line using the following command: python keras\_first\_network.py When you do this, there should be one message for each epoch, showing the accuracy and loss for the model, and you should also see an evaluation of the model after training on the dataset. In an ideal world, we would want to see a loss of zero and accuracy of 1.0, indicating 100% but we don’t live in an ideal world and that never happens unless you are working on a trivial problem. You will always see a certain level of error and the idea is to choose the configuration and training that will give us the least loss and the most accuracy on the dataset. ... 768/768 \[==============================\] - 0s 63us/step - loss: 0.4817 - acc: 0.7708 Epoch 147/150 768/768 \[==============================\] - 0s 63us/step - loss: 0.4764 - acc: 0.7747 Epoch 148/150 768/768 \[==============================\] - 0s 63us/step - loss: 0.4737 - acc: 0.7682 Epoch 149/150 768/768 \[==============================\] - 0s 64us/step - loss: 0.4730 - acc: 0.7747 Epoch 150/150 768/768 \[==============================\] - 0s 63us/step - loss: 0.4754 - acc: 0.7799 768/768 \[==============================\] - 0s 38us/step Accuracy: 76.56 If you attempt to run this in a Jupyter or IPython notebook, chances are you will see an error. This is because of the output progress bars in the training but these can be turned off; just set verbose=0 in the evaluate() and fit() function calls. For example: ... \# fit model on dataset without progress bars model.fit(X, y, epochs=150, batch\_size=10, verbose=0) \# evaluate the keras model \_, accuracy = model.evaluate(X, y, verbose=0) ... You may see different results, given that the algorithm is stochastic, or because of the evaluation or even numerical precision differences. The best thing to do is run it a few times and find the average outcome. Neural networks are stochastic which means you can use the same algorithm to train the same data on different models with different skills every time you run the code. This is not a bug, it is a feature of the algorithm. Because the model performance varies, you may need to fit it multiple times and average the results to get an idea of your model’s performance. For example, running the network five times gives us these accuracy scores: Accuracy: 75.00 Accuracy: 77.73 Accuracy: 77.60 Accuracy: 78.12 Accuracy: 76.17 All the scores are about 77% and the average works out at 76.924%. Step Seven - Making Predictions Your model is trained but how do you use it on new data to make predictions? The model can be adapted and used for generating predictions on your training data, as if it were a brand-new set of data not seen before. Making a prediction is simple – just call predict() on the model. Because the activation function in our output layer is Sigmoid, we can expect to see predictions of a probability from 0 to 1. Our task is one of classification so we can convert the predictions to binary by rounding them. For example: ... \# make probability predictions with model predictions = model.predict(X) \# round predictions rounded = \[round(x\[0\]) for x in predictions\] We could also call a function named predict\_classes(), which would give us crisp classes, like this: ... \# make class predictions with model predictions = model.predict\_classes(X) Below, you can see an entire example with predictions for each dataset example, followed by the input data being printed along with the predicted and expected classes for the first five dataset examples: \# first neural network with keras make predictions from numpy import loadtxt from keras.models import Sequential from keras.layers import Dense \# load the dataset dataset = loadtxt('pima-indians-diabetes.csv', delimiter=',') \# split into input (X) and output (y) variables X = dataset\[:,0:8\] y = dataset\[:,8\] \# define the keras model model = Sequential() model.add(Dense(12, input\_dim=8, activation='relu')) model.add(Dense(8, activation='relu')) model.add(Dense(1, activation='sigmoid')) \# compile the keras model model.compile(loss='binary\_crossentropy', optimizer='adam', metrics=\['accuracy'\]) \# fit the keras model on the dataset model.fit(X, y, epochs=150, batch\_size=10, verbose=0) \# make class predictions with the model predictions = model.predict\_classes(X) \# summarize the first 5 cases for i in range(5): ​ print('%s => %d (expected %d)' % (X\[i\].tolist(), predictions\[i\], y\[i\])) When you run the example, the progress bar has disappeared because we set verbose=0. Once the model has been fit, we get predictions for every dataset example with the predicted class value for five examples printed; these are compared with the expected class values. Most rows were predicted correctly and, based on the estimated model performance, we would expect to see 76.9% accuracy \[6.0, 148.0, 72.0, 35.0, 0.0, 33.6, 0.627, 50.0\] => 0 (expected 1) \[1.0, 85.0, 66.0, 29.0, 0.0, 26.6, 0.351, 31.0\] => 0 (expected 0) \[8.0, 183.0, 64.0, 0.0, 0.0, 23.3, 0.672, 32.0\] => 1 (expected 1) \[1.0, 89.0, 66.0, 23.0, 94.0, 28.1, 0.167, 21.0\] => 0 (expected 0) \[0.0, 137.0, 40.0, 35.0, 168.0, 43.1, 2.288, 33.0\] => 1 (expected 1) Summary Disadvantages of Keras Earlier we discussed the advantages of Keras so it seems only fair to tell you about the disadvantages too – in fact, there is only one: 

*   Can’t handle low-level APIs – Keras can only handle the high-level APIs, those that run on TensorFlow, CNTK, Theano, and other backend engines or frameworks. In that sense, if you want to make abstract layers, it isn’t very useful because Keras contains pre-configured layers. 

That completes our look at machine learning with Keras; time for the final section, Scikit-Learn. 

Part Four An Introduction to Scikit-Learn ![](image_rsrc9SG.jpg)

What is Scikit-Learn? ![](image_rsrc9TV.jpg)Originally developed in 2007 by David Cournapeau, Scikit-Learn started life as a Google Summer of Code project. Matthieu Brucher then joined and began using Scikit-Learn for his thesis work. INRIA became involved in 2010 and Scikit-Learn was released to the public, in beta format, late in January the same year. Scikit-Learn provides users with both unsupervised and supervised learning algorithms through Python.  You must install SciPy before you using Scikit-Learn and the entire stack gives you: 

*   NumPy 
*   SciPy 
*   Matplotlib 
*   IPython 
*   Sympy 
*   Pandas 

Scikit-Learn is made of SciPy modules or extensions and provides users with a ton of useful algorithms. It is simple to use, contains high-quality, readable code, plenty of documentation, and is high performance. The Scikit-Learn library focuses primarily on data modeling, not on loading or manipulating the data and definitely not summarizing it; Pandas and NumPy provide those features. Some of the more popular models Scikit-Learn provides are: 

*   Clustering : used to group unlabeled data 
*   Cross Validation : used to estimate how supervised models perform on unseen data. 
*   Datasets  : used for test datasets and to generate datasets containing properties that help investigate how a model behaves. 
*   Dimensionality Reduction : used to reduce how many attributes are in the data for the purposes of summarization, feature selection and visualization. 
*   Ensemble Methods : used to combine predictions from two or more supervised learning models. 
*   Feature Extraction : used to define the attributes found in text and image data. 
*   Feature Selection : used to identify the meaningful attributes used for creating supervised learning models. 
*   Parameter Tuning : used to ensure supervised models perform at their best. 
*   Manifold Learning : used to summarize and visualize multi-dimensional data. 
*   Supervised Models : includes linear models, Naïve Bayes, discriminate analysis, lazy learning, support vector machines, neural networks and decision trees, to name a few. 

Classification and Regression Trees I want you to see just how easy Scikit-learn is to use so here is an example of a CART (classification and regression trees) algorithm modeling the popular Iris flower dataset. The Iris dataset is included with Scikit-Learn; we fit the classifier on the data and make predictions using the training data.  Lastly, we print the classification accuracy and confusion matrix: \# Sample Decision Tree Classifier from sklearn import datasets from sklearn import metrics from sklearn.tree import DecisionTreeClassifier \# load the iris datasets dataset = datasets.load\_iris() \# fit a CART model to the data model = DecisionTreeClassifier() model.fit(dataset.data, dataset.target) print(model) \# make predictions expected = dataset.target predicted = model.predict(dataset.data) \# summarize the fit of the model print(metrics.classification\_report(expected, predicted)) print(metrics.confusion\_matrix(expected, predicted)) When you run this, you should see an output like the following. It shows you the trained model details, the model skills based on common metrics and also a confusion matrix: DecisionTreeClassifier(class\_weight=None, criterion='gini', max\_depth=None, max\_features=None, max\_leaf\_nodes=None, min\_samples\_leaf=1, min\_samples\_split=2, min\_weight\_fraction\_leaf=0.0, presort=False, random\_state=None, splitter='best') precision    recall  f1-score   support 0       1.00      1.00      1.00        50 1       1.00      1.00      1.00        50 2       1.00      1.00      1.00        50 avg / total       1.00      1.00      1.00       150 \[\[50  0  0\] \[ 0 50  0\] \[ 0  0 50\]\] That shows you how easy using Scikit-Learn is. This chapter will cover several things, including: 

*   What Scikit-Learn is 
*   How to download and install it 
*   A discussion on Scikit-Learn machine learning 
*   How to import data and create training and test datasets 
*   How to build a pipeline 
*   How to use the pipeline in a grid search, a look at the XGBoost algorithm 
*   How to create a DNN using MLPClassifier 
*   How to use LIME to trust the model 

And more. Download and Install Scikit-Learn At some point during the previous tutorials, you will have downloaded Scikit-Learn using a conda environment. There is now a much better version, the developer's version and this is the one we are going to use.  First, you need to remove the original version: Activate the TensorFlow environment using the following command: source activate hello-tf Then remove Scikit-Learn using this command: conda remove scikit-learn Now install the correct version and the libraries you need: conda install -c anaconda git pip install Cython pip install h5py pip install git+git://github.com/scikit-learn/scikit-learn.git 

Machine Learning With Scikit-Learn ![](image_rsrc9TV.jpg)I have divided this tutorial into two – first the machine learning and second, using LIME to trust your model. Step One – Importing the Data We are going to use the Adult dataset for this tutorial. It shows details of adult income and the problem revolves around predicting income levels for individuals as below or above $50,000, using features such as education and relationship. First, the dataset needs to be imported and we do that with Pandas. Be aware that the continuous variable type needs to be converted to float format. In the dataset, you will find a file named CATE\_FEATURES, which includes eight categorical variables:                                workclass education marital occupation relationship race sex native\_country There are also six continuous variables listed in CONTI\_FEATURES age fnlwgt education\_num capital\_gain capital\_loss hours\_week The list is going to be populated manually so you understand the columns we are using. One of the fastest ways of constructing a list of continuous or categorical features is: \## List Categorical CATE\_FEATURES = df\_train.iloc\[:,:-1\].select\_dtypes('object').columns print(CATE\_FEATURES) \## List continuous CONTI\_FEATURES =  df\_train.\_get\_numeric\_data() print(CONTI\_FEATURES) Importing the data is done like this: \# Import dataset import pandas as pd \## Define path data COLUMNS = \['age','workclass', 'fnlwgt', 'education', 'education\_num', 'marital', 'occupation', 'relationship', 'race', 'sex', 'capital\_gain', 'capital\_loss', 'hours\_week', 'native\_country', 'label'\] \### Define continuous list CONTI\_FEATURES  = \['age', 'fnlwgt','capital\_gain', 'education\_num', 'capital\_loss', 'hours\_week'\] \### Define categorical list CATE\_FEATURES = \['workclass', 'education', 'marital', 'occupation', 'relationship', 'race', 'sex', 'native\_country'\] \## Prepare the data features = \['age','workclass', 'fnlwgt', 'education', 'education\_num', 'marital', 'occupation', 'relationship', 'race', 'sex', 'capital\_gain', 'capital\_loss', 'hours\_week', 'native\_country'\] PATH = "https://archive.ics.uci.edu/ml/machine-learning-databases/adult/adult.data" df\_train = pd.read\_csv(PATH, skipinitialspace=True, names = COLUMNS, index\_col=False) df\_train\[CONTI\_FEATURES\] =df\_train\[CONTI\_FEATURES\].astype('float64') df\_train.describe() The unique values count for the native\_country features show us that Holland-Netherlands has just one household. While this household will not give us any information, it will kick up a training error: df\_train.native\_country.value\_counts() United-States                 ​ ​ 29170 Mexico                          ​ ​ 643 ?                               ​ ​ 583 Philippines                     ​ ​ 198 Germany                         ​ ​ 137 Canada                          ​ ​ 121 Puerto-Rico                    ​ ​ 114 El-Salvador                     ​ ​ 106 India                           ​ ​ 100 Cuba                             ​ ​ 95 England                          ​ ​ 90 Jamaica                          ​ ​ 81 South                            ​ ​ 80 China                            ​ ​ 75 Italy                            ​ ​ 73 Dominican-Republic           ​ ​ 70 Vietnam                          ​ ​ 67 Guatemala                        ​ ​ 64 Japan                            ​ ​ 62 Poland                           ​ ​ 60 Columbia                         ​ ​  59 Taiwan                           ​ ​ 51 Haiti                            ​ ​ 44 Iran                            ​ ​ 43 Portugal                         ​ ​ 37 Nicaragua                        ​ ​ 34 Peru                             ​ ​ 31 France                           ​ ​ 29 Greece                           ​ ​ 29 Ecuador                          ​ ​ 28 Ireland                          ​ ​ 24 Hong                             ​ ​ 20 Cambodia                         ​ ​ 19 Trinadad&Tobago                ​ ​ 19 Thailand                         ​ ​ 18 Laos                             ​ ​ 18 Yugoslavia                       ​ ​ 16 Outlying-US(Guam-USVI-etc)       14 Honduras                         ​ ​ 13 Hungary                          ​ ​ 13 Scotland                         ​ ​ 12 Holland-Netherlands                ​ 1 Name: native\_country, dtype: int64 That row can be removed from the dataset because it won’t give us anything except trouble: \## Remove Netherland, only one row df\_train = df\_train\[df\_train.native\_country != "Holland-Netherlands"\] Next, the continuous feature positions can be stored in a list that you will require when you create the pipeline. The next code loops over the names of the columns in CONTI\_FEATURES and retrieves the locations (numbers), which are then appended to a list named conti\_features: \## Get column index of categorical features conti\_features = \[\] for i in CONTI\_FEATURES: position = df\_train.columns.get\_loc(i) conti\_features.append(position) print(conti\_features) \[0, 2, 10, 4, 11, 12\]​ The next code does the same for the categorical features in CATE\_FEATURES: \## Get column index of categorical features categorical\_features = \[\] for i in CATE\_FEATURES: position = df\_train.columns.get\_loc(i) categorical\_features.append(position) print(categorical\_features) \[1, 3, 5, 6, 7, 8, 9, 13\] Now you can look at the dataset and you will see that the categorical features are all strings. Models cannot be fed with string values so the dataset needs to be transformed; we do this with a dummy variable: df\_train.head(5)​ You need to create an individual column for each of the feature’s groups – first, the code below computes how many columns you need: print(df\_train\[CATE\_FEATURES\].nunique(), 'There are',sum(df\_train\[CATE\_FEATURES\].nunique()), 'groups in the whole dataset') workclass         ​ 9 education         ​ 16 marital           ​ ​ 7 occupation        ​ 15 relationship       ​  6 race               ​ ​ 5 sex                ​ ​ 2 native\_country    ​ 41 dtype: int64 There are 101 groups in the whole dataset As you can see, there are 101 groups in this dataset. The workclass feature has 9 groups, the occupation one has 15 groups, and so on. The next code helps you visualize the group names: unique() returns the unique values of the categorical features. for i in CATE\_FEATURES: print(df\_train\[i\].unique()) \['State-gov' 'Self-emp-not-inc' 'Private' 'Federal-gov' 'Local-gov' '?' 'Self-emp-inc' 'Without-pay' 'Never-worked'\] \['Bachelors' 'HS-grad' '11th' 'Masters' '9th' 'Some-college' 'Assoc-acdm' 'Assoc-voc' '7th-8th' 'Doctorate' 'Prof-school' '5th-6th' '10th' '1st-4th' 'Preschool' '12th'\] \['Never-married' 'Married-civ-spouse' 'Divorced' 'Married-spouse-absent' 'Separated' 'Married-AF-spouse' 'Widowed'\] \['Adm-clerical' 'Exec-managerial' 'Handlers-cleaners' 'Prof-specialty' 'Other-service' 'Sales' 'Craft-repair' 'Transport-moving' 'Farming-fishing' 'Machine-op-inspect' 'Tech-support' '?' 'Protective-serv' 'Armed-Forces' 'Priv-house-serv'\] \['Not-in-family' 'Husband' 'Wife' 'Own-child' 'Unmarried' 'Other-relative'\] \['White' 'Black' 'Asian-Pac-Islander' 'Amer-Indian-Eskimo' 'Other'\] \['Male' 'Female'\] \['United-States' 'Cuba' 'Jamaica' 'India' '?' 'Mexico' 'South' 'Puerto-Rico' 'Honduras' 'England' 'Canada' 'Germany' 'Iran' 'Philippines' 'Italy' 'Poland' 'Columbia' 'Cambodia' 'Thailand' 'Ecuador' 'Laos' 'Taiwan' 'Haiti' 'Portugal' 'Dominican-Republic' 'El-Salvador' 'France' 'Guatemala' 'China' 'Japan' 'Yugoslavia' 'Peru' 'Outlying-US(Guam-USVI-etc)' 'Scotland' 'Trinadad&Tobago' 'Greece' 'Nicaragua' 'Vietnam' 'Hong' 'Ireland' 'Hungary'\] The training dataset will have 101 + 7 columns, the 7 being the continuous features. Scikit-Learn can do the conversion for you and it will take two steps: 

1.  The string must be converted to ID. For example, State-gov gets ID1, Self-emp-not-inc gets ID2 and so on. This is all done by the LabelEncoder function. 
2.  Then each ID has to be transposed into a new column. As you know, there are 101 IDs so that equates to 101 columns for the categorical feature groups. The OneHotEncoder function in Scikit-Learn does this. 

Step Two – Creating the Training and Test Sets The dataset is now ready to split into the training and test sets. We’re going to split it into 80% for training and 20% for testing. We do this with train\_test\_split with two arguments. The first is a data frame containing all the features and the second is the data frame with the labels. We use test\_size to specify the test set size. from sklearn.model\_selection import train\_test\_split X\_train, X\_test, y\_train, y\_test = train\_test\_split(df\_train\[features\], df\_train.label, test\_size = 0.2, random\_state=0) X\_train.head(5) print(X\_train.shape, X\_test.shape) (26048, 14) (6512, 14) Step Three – Building the Pipeline We use a pipeline to ensure we can easily feed consistent data to the model. The idea is to feed raw data into the pipeline so it can perform the operations. For example, with our dataset, the continuous variables need to be standardized and the categorical data needs to be converted. Any operation can be done in a pipeline so, for example, if your dataset contains NA’s, you can replace them with the median or the mean and new variables can be created too. Obviously, you can choose to hardcode both these processes but, over time, that will lead to inconsistencies and data leakage. The best way is to create a pipeline: from sklearn.preprocessing import StandardScaler, OneHotEncoder, LabelEncoder from sklearn.compose import ColumnTransformer, make\_column\_transformer from sklearn.pipeline import make\_pipeline from sklearn.linear\_model import LogisticRegression The pipeline will perform two operations before feeding the logistic classifier: Standardize the variable: \`StandardScaler()\`\` Convert the categorical features: OneHotEncoder(sparse=False) The two steps can be done using the make\_column\_transformer function. It is worth telling you now that you cannot get this function to perform onehotencoder or labelencoder in the pipeline with the older version of Scikit-Learn you removed; this is why we prefer using the developer version. You will find make\_column\_transfer dead simple to use. All you need to do is define the columns that need transforming and what  transformation to apply. For example, if you want the continuous standardized, you would do this: conti\_features, StandardScaler() inside make\_column\_transformer. conti\_features: list with the continuous variable StandardScaler: standardize the variable The object OneHotEncoder inside make\_column\_transformer automatically encodes the label. preprocess = make\_column\_transformer( (conti\_features, StandardScaler()), \### Must be numeric not string to specify column name (categorical\_features, OneHotEncoder(sparse=False)) ) And to make sure the pipeline works, we use fit\_transform. You should get an output of 26048, 107 – this is the shape of the data: preprocess.fit\_transform(X\_train).shape (26048, 107)​ You can now use the data transformer. The pipeline is created using make\_pipeline and, once you have transformed the data, you can feed it to the logistic regression: model = make\_pipeline( preprocess, LogisticRegression()) Using Scikit-Learn to train models is trivial; all you need is the pipeline or model, followed by the fit object. The accuracy can be printed using the score object, found in Scikit-Learn: model.fit(X\_train, y\_train) print("logistic regression score: %f" % model.score(X\_test, y\_test)) logistic regression score: 0.850891​ Lastly, we can use predict\_proba to predict the classes and return each class’s probability. Be aware that it will sum to one: model.predict\_proba(X\_test)​ array(\[\[0.83576663, 0.16423337\], \[0.94582765, 0.05417235\], \[0.64760587, 0.35239413\], ..., \[0.99639252, 0.00360748\], \[0.02072181, 0.97927819\], \[0.56781353, 0.43218647\]\]) Step Four – Using the Pipeline in Grid Searches Hyperparameters are variables used for determining the network structure, such as the hidden units and these need to be tuned but doing so can take a lot of time and effort.  We could evaluate our model by changing the training dataset size and evaluating how it performs and you could do that ten times and average the score metrics. That, too, takes a lot of time. With Scikit-Learn, you get an easy way, a function that helps you tune the parameters and do cross-validation. 

*   Cross-Validation – with cross-validation, the training dataset is split into folds and the model evaluated. You have to specify the number of folds and how many times the model gets evaluated. For example, if you set cross-validation to 10, the training set will be evaluated ten times and, after each time, a random nine-fold is chosen to train the model – the 10th fold is for the evaluation. 
*   Grid Search – every classifier has hyperparameters that need tuning and you can try with different values but the easiest way is setting a parameter grid. Simply choose which parameter you want to be tuned; for example, there are multiple parameters in the Scikit-Learn logistic classifier.  Choosing the C parameter would speed up the training as it controls the regularization parameter. The value should be a positive one and the smaller the value, the more weight the regularizer has. 

To create a grid search, we use the GridSearchCD object and create a dictionary that has all the hyperparameters that need tuning. The hyperparameters are listed with the values we want to try. The C parameter, for example, would be tuned with this: 'logisticregression\_\_C': \[0.1, 1.0, 1.0\]: The classifier name in lower case and two underscores followed by the parameter. The model will now try the values of 0.001, 0.01, 0.1 and 1 The model is trained with 10 folds from sklearn.model\_selection import GridSearchCV \# Construct parameter grid param\_grid = { 'logisticregression\_\_C': \[0.001, 0.01,0.1, 1.0\], } The model is trained with GridSearchCV, using two parameters – cv and gri. \# Train model grid\_clf = GridSearchCV(model, param\_grid, cv=10, iid=False) grid\_clf.fit(X\_train, y\_train) OUTPUT GridSearchCV(cv=10, error\_score='raise-deprecating', estimator=Pipeline(memory=None, steps=\[('columntransformer', ColumnTransformer(n\_jobs=1, remainder='drop', transformer\_weights=None, transformers=\[('standardscaler',  StandardScaler(copy=True, with\_mean=True, with\_std=True), \[0, 2, 10, 4, 11, 12\]), ('onehotencoder', OneHotEncoder(categorical\_features=None, categories=None,...ty='l2', random\_state=None, solver='liblinear', tol=0.0001, verbose=0, warm\_start=False))\]), fit\_params=None, iid=False, n\_jobs=1, param\_grid={'logisticregression\_\_C': \[0.001, 0.01, 0.1, 1.0\]}, pre\_dispatch='2\*n\_jobs', refit=True, return\_train\_score='warn', scoring=None, verbose=0) To access the best parameters, you use best\_params\_ grid\_clf.best\_params\_ OUTPUT {'logisticregression\_\_C': 1.0} Once the model is trained on four regularization values, we get the optimal value: print("best logistic regression from grid search: %f" % grid\_clf.best\_estimator\_.score(X\_test, y\_test)) best logistic regression from grid search: 0.850891 And to get the predicted probabilities: grid\_clf.best\_estimator\_.predict\_proba(X\_test)​               array(\[\[0.83576677, 0.16423323\], \[0.9458291 , 0.0541709 \], \[0.64760416, 0.35239584\], ..., \[0.99639224, 0.00360776\], \[0.02072033, 0.97927967\], \[0.56782222, 0.43217778\]\]) 

XGBoost Model ![](image_rsrc9TV.jpg)Now we’re going to have a go at training the XGBoost classifier, one of the very best and a definite improvement over the random forest classifier. I won’t go into detail about the classifier because that is outside the scope of this book. I will ask you to keep in mind that XGBoost has won lots of competitions, particularly the Kaggle competitions. On average-sized datasets, it is just as good, if not better, than many of the deep learning algorithms. However, I will say that XGBoost is somewhat challenging to tune because of the sheer number of parameters that need tuning. Of course, GridSearchCV can always pick the parameters for you. We want to use another better way of finding the best parameters. While GridSearchCV works, it is time-consuming, especially where multiple values have been passed. The more parameters there are, the bigger the search space and the better solution lies in using RandomizedSearchCV. This method involves choosing each hyperparameter’s value randomly after an iteration. For example,  if we trained the classifier over, say, 1000 iterations, 1000 combinations would be evaluated. It works like GridSearchCV but is better for our purposes. First things first, let’s import xgboost. If you don’t already have it, you can use pip to install it or do this: use import sys !{sys.executable} -m pip install xgboost Next, in the Jupyter environment, we do this: import xgboost from sklearn.model\_selection import RandomizedSearchCV from sklearn.model\_selection import StratifiedKFold Now we must specify which parameters we want tuning. The official  documentation tells you all of the parameters that can be tunes, but we are only going to choose two that have two values for this tutorial. XGBoost is time-consuming to train so the more hyperparameters you put in the grid, the longer it is going to take: params = { 'xgbclassifier\_\_gamma': \[0.5, 1\], 'xgbclassifier\_\_max\_depth': \[3, 4\] } Next, the XGBoost classifier is used to construct a pipeline, defining 600 estimators. It’s worth knowing that n\_estimators is a tunable hyperparameter. Too high a value and you run the risk of over-fitting the models. Do try different values but don’t forget that it can take a long time. The default values are used for the rest of the parameters: model\_xgb = make\_pipeline( preprocess, xgboost.XGBClassifier( n\_estimators=600, objective='binary:logistic', silent=True, nthread=1) ) The cross-validation can be significantly improved if we use the Stratified K-Folds cross validator. With this one, we speed up the computation by only constructing three folds but the trade-off is lower quality. If you want better quality results, the value could be increased to 5 or 10. We’re going to train our model over four iterations: skf = StratifiedKFold(n\_splits=3, shuffle = True, random\_state = 1001) random\_search = RandomizedSearchCV(model\_xgb, param\_distributions=params, n\_iter=4, scoring='accuracy', n\_jobs=4, cv=skf.split(X\_train, y\_train), verbose=3, random\_state=1001) Now the randomized search is ready, the model can be trained: #grid\_xgb = GridSearchCV(model\_xgb, params, cv=10, iid=False) random\_search.fit(X\_train, y\_train) Fitting 3 folds for each 4 candidates, totaling 12 fits \[CV\] xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=0.5 ............ \[CV\] xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=0.5 ............ \[CV\] xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=0.5 ............ \[CV\] xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=0.5 ............ \[CV\]  xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=0.5, score=0.8759645283888057, total= 1.0min \[CV\] xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=0.5 ............ \[CV\]  xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=0.5, score=0.8729701715996775, total= 1.0min \[CV\]  xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=0.5, score=0.8706519235199263, total= 1.0min \[CV\] xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=0.5  ............ \[CV\] xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=1 .............. \[CV\]  xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=0.5, score=0.8735460094437406, total= 1.3min \[CV\] xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=1 .............. \[CV\]  xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=1, score=0.8722791661868018, total=  57.7s \[CV\] xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=1 .............. \[CV\]  xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=1, score=0.8753886905447426, total= 1.0min \[CV\] xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=1 .............. \[CV\]  xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=0.5, score=0.8697304768486523, total= 1.3min \[CV\] xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=1 .............. \[CV\]  xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=0.5, score=0.8740066797189912, total= 1.4min \[CV\] xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=1 .............. \[CV\]  xgbclassifier\_\_max\_depth=3, xgbclassifier\_\_gamma=1, score=0.8707671043538355, total= 1.0min \[CV\]  xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=1, score=0.8729701715996775, total= 1.2min \[Parallel(n\_jobs=4)\]: Done  10 out of  12 | elapsed:  3.6min remaining:   43.5s \[CV\]  xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=1, score=0.8736611770125533, total= 1.2min \[CV\]  xgbclassifier\_\_max\_depth=4, xgbclassifier\_\_gamma=1, score=0.8692697535130154, total= 1.2min \[Parallel(n\_jobs=4)\]: Done  12 out of  12 | elapsed:  3.6min finished /Users/Thomas/anaconda3/envs/hello-tf/lib/python3.6/site-packages/sklearn/model\_selection/\_search.py:737: DeprecationWarning: The default of the \`iid\` parameter will change from True to False in version 0.22 and will be removed in 0.24. This will change numeric results when test-set sizes are unequal. DeprecationWarning) RandomizedSearchCV(cv=<generator object \_BaseKFold.split at 0x1101eb830>, error\_score='raise-deprecating', estimator=Pipeline(memory=None, steps=\[('columntransformer', ColumnTransformer(n\_jobs=1, remainder='drop', transformer\_weights=None, transformers=\[('standardscaler', StandardScaler(copy=True, with\_mean=True, with\_std=True), \[0, 2, 10, 4, 11, 12\]), ('onehotencoder', OneHotEncoder(categorical\_features=None, categories=None,... reg\_alpha=0, reg\_lambda=1, scale\_pos\_weight=1, seed=None, silent=True, subsample=1))\]), fit\_params=None, iid='warn', n\_iter=4, n\_jobs=4, param\_distributions={'xgbclassifier\_\_gamma': \[0.5, 1\], 'xgbclassifier\_\_max\_depth': \[3, 4\]}, pre\_dispatch='2\*n\_jobs', random\_state=1001, refit=True, return\_train\_score='warn', scoring='accuracy', verbose=3) You can see from the results that XGBoost produces a much better score than the logistic regression we did. print("Best parameter", random\_search.best\_params\_) print("best logistic regression from grid search: %f" % random\_search.best\_estimator\_.score(X\_test, y\_test)) Best parameter {'xgbclassifier\_\_max\_depth': 3, 'xgbclassifier\_\_gamma': 0.5} best logistic regression from grid search: 0.873157 random\_search.best\_estimator\_.predict(X\_test)​                             array(\['<=50K', '<=50K', '<=50K', ..., '<=50K', '>50K', '<=50K'\],      dtype=object)              Using the MLPClassifier to Create a DNN Lastly, we can use Scikit-Learn for training deep learning algorithms. This method works the same as the other classifiers and can be found at MLPClassifier: from sklearn.neural\_network import MLPClassifier The deep learning algorithm below is now defined: 

*   Adam solver 
*   Relu activation function 
*   Alpha = 0.0001 
*   batch size of 150 
*   Two hidden layers containing 100 and 50 neurons respectively 

model\_dnn = make\_pipeline( preprocess, MLPClassifier(solver='adam', alpha=0.0001, activation='relu', batch\_size=150, hidden\_layer\_sizes=(200, 100) , random\_state=1)) The number of layers can be changed to improve how the model works” model\_dnn.fit(X\_train, y\_train) print("DNN regression score: %f" % model\_dnn.score(X\_test, y\_test)) DNN regression score: 0.821253 Using LIME to Trust Your Model You have a good performing model now so you need to be able to trust it and for that, you need the right tool. Thanks to three intrepid researchers, we have an algorithm  called Local Interpretable Model-Agnostic Explanations, or LIME for short. For example, you don’t always know if you can trust the predictions your machine learning model provides. In the same way, a doctor won’t necessarily trust a specific diagnosis just because a computer told him that was what it was. You need to know that your model is trusted before you can put it to use. Just think, if we could understand exactly why a classifier made a specific prediction, even the most complex models like the neural networks, SVMs, Random Forests, any that have a kernel, will become much easier to trust. Going back to our doctor and his computer making the diagnoses, if he had a computer model that told him the essential symptoms for a disease, he would be more likely to place some trust in it. That’s where LIME steps in as it can tell you which features affect the classifier’s decisions. Preparing the Data Running LIME with Python requires a couple of changes, not least, installing it on the terminal: pip install lime LIME needs to approximate the model locally and it does this using an object called LimeTabularExplainer. The object needs the following: 

*   A dataset formatted to NumPy 
*   The feature names (feature\_name) 
*   The class names (class\_names) 
*   The column index for the categorical features (categorical\_features) 
*   The group name for each categorical feature (categorical\_names)

Create the NumPy Training Set Copying and converting df\_train to NumPy from Panda is simple: df\_train.head(5) \# Create numpy data df\_lime = df\_train df\_lime.head(3) Getting the Class Name We use the unique() object for this and you should see: 

*   '<=50K' 
*   '>50K' 

\# Get the class name class\_names = df\_lime.label.unique() class\_names array(\['<=50K', '>50K'\], dtype=object) Getting the Categorical Feature Column Index The method we used for getting the group names can be used here. LabelEncoder is used to encode the label and the operation is repeated on each categorical feature: \## import sklearn.preprocessing as preprocessing categorical\_names = {} for feature in CATE\_FEATURES: le = preprocessing.LabelEncoder() le.fit(df\_lime\[feature\]) df\_lime\[feature\] = le.transform(df\_lime\[feature\]) categorical\_names\[feature\] = le.classes\_ print(categorical\_names)    {'workclass': array(\['?', 'Federal-gov', 'Local-gov', 'Never-worked', 'Private', 'Self-emp-inc', 'Self-emp-not-inc', 'State-gov', 'Without-pay'\], dtype=object), 'education': array(\['10th', '11th', '12th', '1st-4th', '5th-6th', '7th-8th', '9th', 'Assoc-acdm', 'Assoc-voc', 'Bachelors', 'Doctorate', 'HS-grad', 'Masters', 'Preschool', 'Prof-school', 'Some-college'\], dtype=object), 'marital': array(\['Divorced', 'Married-AF-spouse', 'Married-civ-spouse', 'Married-spouse-absent', 'Never-married', 'Separated', 'Widowed'\], dtype=object), 'occupation': array(\['?', 'Adm-clerical', 'Armed-Forces', 'Craft-repair', 'Exec-managerial', 'Farming-fishing', 'Handlers-cleaners', 'Machine-op-inspect', 'Other-service', 'Priv-house-serv', 'Prof-specialty', 'Protective-serv', 'Sales', 'Tech-support', 'Transport-moving'\], dtype=object), 'relationship': array(\['Husband', 'Not-in-family', 'Other-relative', 'Own-child', 'Unmarried', 'Wife'\], dtype=object), 'race': array(\['Amer-Indian-Eskimo', 'Asian-Pac-Islander', 'Black', 'Other', 'White'\], dtype=object), 'sex': array(\['Female', 'Male'\], dtype=object), 'native\_country': array(\['?', 'Cambodia', 'Canada', 'China', 'Columbia', 'Cuba', 'Dominican-Republic', 'Ecuador', 'El-Salvador', 'England', 'France', 'Germany', 'Greece', 'Guatemala', 'Haiti', 'Honduras' , 'Hong', 'Hungary', 'India', 'Iran', 'Ireland', 'Italy', 'Jamaica', 'Japan', 'Laos', 'Mexico', 'Nicaragua', 'Outlying-US(Guam-USVI-etc)', 'Peru', 'Philippines', 'Poland', 'Portugal', 'Puerto-Rico', 'Scotland', 'South', 'Taiwan', 'Thailand', 'Trinadad&Tobago', 'United-States', 'Vietnam', 'Yugoslavia'\], dtype=object)} df\_lime.dtypes​ age               ​ ​ float64 workclass           ​ int64 fnlwgt            ​ ​ float64 education           ​ int64 education\_num     ​ float64 marital             ​ int64 occupation          ​ int64 relationship        ​ int64 race               ​ ​ int64 sex                ​ ​ int64 capital\_gain      ​ float64 capital\_loss      ​ float64 hours\_week        ​ float64 native\_country     ​ int64 label              ​ ​ object dtype: object Our dataset is now ready so we can build a different one. The data is transformed outside the pipeline – we do this to avoid any errors or complications with LIME. In LimeTabularExplainer, the training dataset should be a NumPy array and not contain any strings.  Using the above method has provided us with a converted training dataset: from sklearn.model\_selection import train\_test\_split X\_train\_lime, X\_test\_lime, y\_train\_lime, y\_test\_lime = train\_test\_split(df\_lime\[features\], df\_lime.label , test\_size = 0.2, random\_state=0) X\_train\_lime.head(5) We use XGBoost, with its optimal parameters, to build the pipeline: model\_xgb = make\_pipeline( preprocess, xgboost.XGBClassifier(max\_depth = 3, gamma = 0.5, n\_estimators=600, objective='binary:logistic', silent=True, nthread=1)) model\_xgb.fit(X\_train\_lime, y\_train\_lime) /Users/xxxxxx/anaconda3/envs/hello-tf/lib/python3.6/site-packages/sklearn/preprocessing/\_encoders.py:351: FutureWarning: The handling of integer data will change in version 0.22. The categories are currently determined based on the range \[0, max(values)\], while in the future, they will be determined based on the unique values. If you want to use the future behavior and get rid of that warning you see, categories=auto must be specified. If a LabelEncoder was used before the OneHotEncoder to turn the categories into integers, the OneHotEncoder can now be used directly: warnings.warn(msg, FutureWarning) Pipeline(memory=None, steps=\[('columntransformer', ColumnTransformer(n\_jobs=1, remainder='drop', transformer\_weights=None, transformers=\[('standardscaler', StandardScaler(copy=True, with\_mean=True, with\_std=True), \[0, 2, 10, 4, 11, 12\]), ('onehotencoder',  OneHotEncoder(categorical\_features=None, categories=None,... reg\_alpha=0, reg\_lambda=1, scale\_pos\_weight=1, seed=None, silent=True, subsample=1))\]) You will see a warning message telling you that a label encoder does not need to be created before the pipeline. If you are not fussed about LIME, use the first bit of the tutorial. If you do want LIME, stick with creating the encoded dataset and setting the OneHotEncoder in the pipeline. print("best logistic regression from grid search: %f" % model\_xgb.score(X\_test\_lime, y\_test\_lime))                                          best logistic regression from grid search: 0.873157                                          model\_xgb.predict\_proba(X\_test\_lime)​ ​               array(\[\[7.9646105e-01, 2.0353897e-01\], \[9.5173013e-01, 4.8269872e-02\], \[7.9344827e-01, 2.0655173e-01\], ..., \[9.9031430e-01, 9.6856682e-03\], \[6.4581633e-04, 9.9935418e-01\], \[9.7104281e-01, 2.8957171e-02\]\], dtype=float32) Before we put LIME to work, we need a NumPy array containing the features for the incorrect classification. That list can then be used later to determine what made the classifier go awry. temp = pd.concat(\[X\_test\_lime, y\_test\_lime\], axis= 1) temp\['predicted'\] = model\_xgb.predict(X\_test\_lime) temp\['wrong'\]=  temp\['label'\] != temp\['predicted'\] temp = temp.query('wrong==True').drop('wrong', axis=1) temp= temp.sort\_values(by=\['label'\]) temp.shape (826, 16) A Lambda function is then created to get the model’s prediction on the new data – you are going to need this pretty soon: predict\_fn = lambda x: model\_xgb.predict\_proba(x).astype(float) X\_test\_lime.dtypes age               ​ ​ float64 workclass          ​ int64 fnlwgt            ​ ​ float64 education           ​ int64 education\_num     ​ float64 marital             ​ int64 occupation          ​ int64 relationship        ​ int64 race               ​ ​ int64 sex                ​ ​ int64 capital\_gain      ​ float64 capital\_loss      ​ float64 hours\_week        ​ float64 native\_country      ​ int64 dtype: object predict\_fn(X\_test\_lime)​ array(\[\[7.96461046e-01, 2.03538969e-01\], \[9.51730132e-01, 4.82698716e-02\], \[7.93448269e-01, 2.06551731e-01\], ..., \[9.90314305e-01, 9.68566816e-03\], \[6.45816326e-04, 9.99354184e-01\], \[9.71042812e-01, 2.89571714e-02\]\]) The Pandas data frame is them converted to a NumPy array: X\_train\_lime = X\_train\_lime.values X\_test\_lime = X\_test\_lime.values X\_test\_lime array(\[\[4.00000e+01, 5.00000e+00, 1.93524e+05, ..., 0.00000e+00, 4.00000e+01, 3.80000e+01\], \[2.70000e+01, 4.00000e+00, 2.16481e+05, ..., 0.00000e+00, 4.00000e+01, 3.80000e+01\], \[2.50000e+01, 4.00000e+00, 2.56263e+05, ..., 0.00000e+00, 4.00000e+01, 3.80000e+01\], ..., \[2.80000e+01, 6.00000e+00, 2.11032e+05, ..., 0.00000e+00, 4.00000e+01, 2.50000e+01\], \[4.40000e+01, 4.00000e+00, 1.67005e+05, ..., 0.00000e+00, 6.00000e+01, 3.80000e+01\], \[5.30000e+01, 4.00000e+00, 2.57940e+05, ..., 0.00000e+00, 4.00000e+01, 3.80000e+01\]\]) model\_xgb.predict\_proba(X\_test\_lime)​ ​               array(\[\[7.9646105e-01, 2.0353897e-01\], \[9.5173013e-01, 4.8269872e-02\], \[7.9344827e-01, 2.0655173e-01\], ..., \[9.9031430e-01, 9.6856682e-03\], \[6.4581633e-04, 9.9935418e-01\], \[9.7104281e-01, 2.8957171e-02\]\], dtype=float32) print(features, class\_names, categorical\_features, categorical\_names) \['age', 'workclass', 'fnlwgt', 'education', 'education\_num',  'marital', 'occupation', 'relationship', 'race', 'sex', 'capital\_gain', 'capital\_loss', 'hours\_week', 'native\_country'\] \['<=50K' '>50K'\] \[1, 3, 5, 6, 7, 8, 9, 13\] {'workclass': array(\['?', 'Federal-gov', 'Local-gov', 'Never-worked', 'Private', 'Self-emp-inc', 'Self-emp-not-inc', 'State-gov', 'Without-pay'\], dtype=object), 'education': array(\['10th', '11th', '12th', '1st-4th', '5th-6th', '7th-8th', '9th', 'Assoc-acdm', 'Assoc-voc', 'Bachelors', 'Doctorate', 'HS-grad', 'Masters', 'Preschool', 'Prof-school', 'Some-college'\], dtype=object), 'marital': array(\['Divorced', 'Married-AF-spouse', 'Married-civ-spouse', 'Married-spouse-absent', 'Never-married', 'Separated', 'Widowed'\], dtype=object), 'occupation': array(\['?', 'Adm-clerical', 'Armed-Forces', 'Craft-repair', 'Exec-managerial', 'Farming-fishing', 'Handlers-cleaners', 'Machine-op-inspct', 'Other-service', 'Priv-house-serv', 'Prof-specialty', 'Protective-serv', 'Sales', 'Tech-support', 'Transport-moving'\], dtype=object), 'relationship': array(\['Husband', 'Not-in-family', 'Other-relative', 'Own-child', 'Unmarried', 'Wife'\], dtype=object), 'race': array(\['Amer-Indian-Eskimo', 'Asian-Pac-Islander', 'Black', 'Other', 'White'\], dtype=object), 'sex': array(\['Female', 'Male'\], dtype=object), 'native\_country': array(\['?', 'Cambodia', 'Canada', 'China', 'Columbia', 'Cuba', 'Dominican-Republic', 'Ecuador', 'El-Salvador', 'England', 'France', 'Germany', 'Greece', 'Guatemala', 'Haiti', 'Honduras', 'Hong', 'Hungary', 'India', 'Iran', 'Ireland', 'Italy', 'Jamaica', 'Japan', 'Laos', 'Mexico', 'Nicaragua', 'Outlying-US(Guam-USVI-etc)', 'Peru', 'Philippines', 'Poland', 'Portugal', 'Puerto-Rico', 'Scotland', 'South', 'Taiwan', 'Thailand', 'Trinadad&Tobago', 'United-States', 'Vietnam', 'Yugoslavia'\], dtype=object)} import lime import lime.lime\_tabular \### Train should be label encoded not one hot encoded explainer = lime.lime\_tabular.LimeTabularExplainer(X\_train\_lime , feature\_names = features, class\_names=class\_names, categorical\_features=categorical\_features, categorical\_names=categorical\_names, kernel\_width=3) Now we can pick a household at random from the test dataset and see what the model predicts and how it came to that conclusion: import numpy as np np.random.seed(1) i = 100 print(y\_test\_lime.iloc\[i\]) \>50K X\_test\_lime\[i\]​ array(\[4.20000e+01, 4.00000e+00, 1.76286e+05, 7.00000e+00, 1.20000e+01, 2.00000e+00, 4.00000e+00, 0.00000e+00, 4.00000e+00, 1.00000e+00, 0.00000e+00, 0.00000e+00, 4.00000e+01, 3.80000e+01\]) The explainer can be used by calling explain\_instance – this will tell you why the model made the prediction: exp = explainer.explain\_instance(X\_test\_lime\[i\], predict\_fn, num\_features=6) exp.show\_in\_notebook(show\_all=False) The output shows you the correct prediction so, what can we say about this? First, we can say that the classifier wasn’t overly certain about the probabilities being predicted. The predictions state a probability of 64% that the household has an income of more than 50k. That 64% comes from two features – marital and capital gain. You will see two colors on the output – blue and orange. Blue is a negative contribution to the positive class while orange is a positive contribution. Why is the classifier so confused? This is because we have null as a value for the household’s capital gain and this is one of the best wealth predictor features. Add to that the fact that the household working hours are less than 40 and it explains some of the confusion. The features that affect the classifier positively are occupation, age and sex. If the householder were single we would have got a prediction of less than 50k – 0.64-0.18=0.46 Let’s try it again with an incorrectly classified household: temp.head(3) temp.iloc\[1,:-2\] age                  ​ ​ 58 workclass             ​ 4 fnlwgt            ​ ​ 68624 education            ​ 11 education\_num         9 marital               ​ 2 occupation            ​ 4 relationship          ​ 0 race                  ​ 4 sex                   ​ 1 capital\_gain          ​ 0 capital\_loss          ​ 0 hours\_week           ​ 45 native\_country       ​ 38 Name: 20931, dtype: object i = 1 print('This observation is', temp.iloc\[i,-2:\]) This observation is label        <=50K predicted     >50K Name: 20931, dtype: object exp = explainer.explain\_instance(temp.iloc\[1,:-2\], predict\_fn, num\_features=6) exp.show\_in\_notebook(show\_all=False) We got a prediction of a more than 50k income even though that is clearly untrue. This is a strange household – it has no values for capital gain or loss, the householder is a divorced, 60-year-old male who is educated. The overall pattern dictates that the income would be less than 50k, as the classifier explains. Have a play around with LIME; you will notice some pretty big mistakes made by the classifier! 

Building a Random Forest Model  
To Predict Wine Quality ![](image_rsrc9TV.jpg)This is our final Scikit-Learn tutorial. We’ll be using the library to build the random forest supervised learning model and tune it to predict wine quality, based on features such as residual sugar, acidity, and alcohol concentration, and so on. Here’s what we will cover: 

1.  Setting up your environment 
2.  Importing the required libraries and modules 
3.  Loading the red wine data 
4.  Splitting the dataset into train and test sets 
5.  The data pre-processing steps 
6.  Declaring the hyperparameters, we want to tune         
7.  Using a cross-validation pipeline to tune the model 
8.  Refitting the data on the whole training dataset 
9.  Using the test data to evaluate the model pipeline 

Lastly, we save the model so we can use it later and, at the end, I will give you the entire code, from start to finish. Let’s get on. Step One – Setting Up Your Environment The first step is to ensure that you have these on your computer: 

*   Python 2.7+ or Python 3+ 
*   Pandas 
*   NumPy 
*   Scikit-Learn (otherwise called sklearn) 

If you haven’t already got all of this, install Anaconda as it comes with all those required packaged pre-installed. If any of your packages require an update simply type the following, with the relevant package name, at the command prompt: $ conda update <package name> To confirm that you scikit-learn properly installed on your system, type the following: $ python -c "import sklearn; print sklearn.\_\_version\_\_" 0.18.1 Your version number may be different. Now create a new file and call it sklearn\_ml\_example.py Step Two – Importing the Required Libraries and Modules First, we should import NumPy as this gives us great support for numerical computations: import numpy as np Next, Pandas, one of the best libraries with support for data frames. Technically, this is an optional install because Scikit-Learn has the ability to deal with numerical matrices, but it does make things easier for us: import pandas as pd Now, we can import the functions we need. First, we want the function called train\_test\_split(), which is found in the module called model\_selection. The name says it all – the module has loads of utilities that help us choose the right model: from sklearn.model\_selection import train\_test\_split Next, we want the pre-processing module, all of it, not just a couple  of functions. This module has everything we need to scale the data, transform it, and wrangle it. from sklearn import preprocessing Now we want some families of models and these differ from actual models. Families are broad model types, like the SVMs, random forests, linear regression, etc. Once the parameters have been fit and tuned to the data, each family gives us an actual model. Don’t worry about this at the moment; it will all become clear later in the tutorial. We want the random forest family: from sklearn.ensemble import RandomForestRegressor The next step involves importing the tools we need to do the cross-validation: from sklearn.pipeline import make\_pipeline from sklearn.model\_selection import GridSearchCV Now some metrics for evaluating how the model performs: from sklearn.metrics import mean\_squared\_error, r2\_score And lastly, we want to be able to persist the model so we can use it in the future: from sklearn.externals import joblib If you are wondering what joblib is, it is an efficient way of storing the bigger NumPy arrays and is an alternative to pickle in Python. Step Three – Loading the Wine Data We are now at a point where we can load the dataset and, in Pandas, you will find plenty of useful import and output tools. These help us to read data from Excel, CSV, SQL, SAS and many more. We are going to use a tool named read\_csv() to help us load the file. dataset\_url = 'http://mlr.cs.umass.edu/ml/machine-learning-databases/wine-quality/winequality-red.csv' data = pd.read\_csv(dataset\_url) Now we can check the data by looking at the first five rows: print data.head() \# fixed acidity;"volatile acidity";"citric acid"... \# 0   7.4;0.7;0;1.9;0.076;11;34;0.9978;3.51;0.56... \# 1   7.8;0.88;0;2.6;0.098;25;67;0.9968;3.2;0.68... \# 2   7.8;0.76;0.04;2.3;0.092;15;54;0.997;3.26;0... \# 3   11.2;0.28;0.56;1.9;0.075;17;60;0.998;3.16;... \# 4   7.4;0.7;0;1.9;0.076;11;34;0.9978;3.51;0.56... Now, that looks a bit of a mess and, when you look closer, you can see that semicolons have been used for separating the data. Annoying but easily fixed: data = pd.read\_csv(dataset\_url, sep=';') print data.head() #    fixed acidity  volatile acidity  citric acid... \# 0            7.4              0.70         0.00... \# 1            7.8              0.88         0.00... \# 2            7.8              0.76         0.04... \# 3           11.2              0.28         0.56... \# 4            7.4              0.70         0.00... That looks better and is much easier to read. Now let’s look at the data: print data.shape \# (1599, 12) We can see that there are 1599 data samples and 12 features, which includes the target feature. Now let’s print a few summary statistics: print data.describe() #        ​ ​ fixed acidity  ​ ​ volatile acidity                citric acid... \# count    ​ 1599.000000       ​  1599.000000  ​ 1599.000000... \# mean       ​ 8.319637          ​ 0.527821     ​               0.270976... \# std        ​ 1.741096          ​ 0.179060     ​               0.194801... \# min         ​ 4.600000          ​ 0.120000     ​               0.000000... \# 25%         ​ 7.100000          ​ 0.390000     ​               0.090000... \# 50%         ​ 7.900000          ​ 0.520000     ​               0.260000... \# 75%         ​ 9.200000          ​ 0.640000    ​               0.420000... \# max        ​ 15.900000          ​ 1.580000     ​               1.000000... These are the features: 

*   Quality – our target feature 
*   Alcohol 
*   Chlorides 
*   Citric acid 
*   Density 
*   Fixed acidity 
*   Free sulfur dioxide 
*   Ph 
*   Residual sugar 
*   Sulfates 
*   Total sulfur dioxide 
*   Volatile acidity 

Conveniently, the features are all numeric ones but their scales are very different. Mentally remind yourself that the data must be standardized later. Be aware that, for the purposes of this tutorial, we are not doing anywhere near as much exploratory analysis as would normally be recommended. Next, we want to split the data. Step Four – Splitting the Data This step is critical for obtaining a proper estimate of how the model performs and the first thing we need to do is split the target feature (y) from the input features (x): y = data.quality X = data.drop('quality', axis=1) Now we can use a useful feature in Scikit-Learn, a function called train\_test\_split: X\_train, X\_test, y\_train, y\_test = train\_test\_split(X, y, test\_size=0.2, random\_state=123, stratify=y) You can see from this that we split the model 80/20. 80% is the training data and 20% is the testing data. We also set a seed, a random state that allows our results to be reproduced. Lastly, good practice dictates that the sample should be stratified by the target variable, thus ensuring that the training and test sets look similar. This will ensure we get more reliable evaluation metrics: Step Six – Declaring the Pre-Processing Steps In step three, we mentioned having to standardize the data features because their scales were different. So, what is standardization? It is a process whereby the means are subtracted from each feature and then divide by standard deviations of the features. This is common  for pretty much all machine learning problems because most algorithms assume that the features have been centered around zero and have roughly the same variance. First, a look at a piece of code we will NOT be using.  With Scikit-Learn, pre-processing is easy. This is how a dataset is scaled, for example: X\_train\_scaled = preprocessing.scale(X\_train) print X\_trained\_scaled \# array(\[\[ 0.51358886,  2.19680282, -0.164433  , ...,  1.08415147, #         -0.69866131, -0.58608178\], #        \[-1.73698885, -0.31792985, -0.82867679, ...,  1.46964764, #          1.2491516 ,  2.97009781\], #        \[-0.35201795,  0.46443143, -0.47100705, ..., -0.13658641, \# ... And confirming that our newly scaled dataset is centered at zero is done with unit variance: print X\_train\_scaled.mean(axis=0) \# \[ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.\] print X\_train\_scaled.std(axis=0) \# \[ 1.  1.  1.  1.  1.  1.  1.  1.  1.  1.  1.\] Well, that all looks good so why can’t we use this if it’s so easy? The answer to that is because we cannot transform the test set in the same way. We can scale it separately but the means and the standard deviations we used for the training set can’t be used on the test set. That would mean the way the pipeline represents everything, and that includes our pre-processing, would not be a fair representation  of how it would be done new data. Instead, we are going to use a different code for the pre-processing. Rather than invoking the scale function directly, we will use another Scikit-Learn function, this one called the Transformer API. This lets the pre-processing step be fit on the training data the same way that model is fit. That way, the transformation can be used on other datasets. The process looks like this: 

1.  The transformer is fit on the training dataset, retaining the standard deviations and means 
2.  The transformer is applied to the training dataset, which scales the training data 
3.  The transformer is applied to the test dataset with the standard deviations and means from the first step. 

In this way, we get a more realistic estimate of the performance and means our pre-processing steps can be put into the cross-validation pipeline – more on that in a bit. Here’s how we do it: scaler = preprocessing.StandardScaler().fit(X\_train) Our scaler object now has the standard deviations and means for every training data feature. We can make sure that it all worked like this: X\_train\_scaled = scaler.transform(X\_train) print X\_train\_scaled.mean(axis=0) \# \[ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.  0.\] print X\_train\_scaled.std(axis=0) \# \[ 1.  1.  1.  1.  1.  1.  1.  1.  1.  1.  1.\] Note that the scalar object is used for transforming our training dataset. Later on, the test dataset will be transformed with the same standard deviations and means. X\_test\_scaled = scaler.transform(X\_test) print X\_test\_scaled.mean(axis=0) \# \[ 0.02776704  0.02592492 -0.03078587 -0.03137977 -0.00471876 -0.04413827 #  -0.02414174 -0.00293273 -0.00467444 -0.10894663  0.01043391\] print X\_test\_scaled.std(axis=0) \# \[ 1.02160495  1.00135689  0.97456598  0.91099054  0.86716698  0.94193125 #  1.03673213  1.03145119  0.95734849  0.83829505  1.0286218 \] Did you spot something? We haven’t got our features perfectly centered at zero with the unit variance but that is what should have happened. Why? Because the test set is being transformed with the training set’s standard deviations means and not those from the test dataset. When it comes time to set the cross-validation pipeline up, the Transformer API will not need to be fit manually. All we will do is declare the class object like this: pipeline = make\_pipeline(preprocessing.StandardScaler(), RandomForestRegressor(n\_estimators=100)) What we have here is a model pipeline. First, it uses StandardScaler() to transform the data and then a random forest regressor is used to  fit the model. Step Six – Declaring the Hyperparameters for Tuning Now we need to think about the hyperparameters that need tuning for the model. We need to consider two types – the model parameters and the hyperparameters. The difference is that, while the model parameters are learned from the data (regression coefficients), the hyperparameters are not. Instead, they express the model’s high-level structural information and should be set before the model is trained. Let’s use our random forest regression model as an example. In each of the decision trees, the computer makes an empirical decision on where the branches should be created. This is based on MSE (mean-squared-error) OR on MAE (mean-absolute-error) so the locations of the branches are classed as the model parameters. What the algorithm doesn’t know is which criteria – MSE or MAE – to use and it doesn’t know the number of trees that should din the forest, either. Those are good examples of the required hyperparameters. The tunable hyperparameters can be listed like this: print pipeline.get\_params() \# ... \# 'randomforestregressor\_\_criterion': 'mse', \# 'randomforestregressor\_\_max\_depth': None, \# 'randomforestregressor\_\_max\_features': 'auto', \# 'randomforestregressor\_\_max\_leaf\_nodes': None, \# ... Be aware that, when you tune a hyperparameter through a pipeline, you need to prepend the hyperparameter name with randomforestregressor\_, as you can see in the code above. Now we should declare all the hyperparameters that we tuned  through the cross-validation: hyperparameters = { 'randomforestregressor\_\_max\_features' : \['auto', 'sqrt', 'log2'\], 'randomforestregressor\_\_max\_depth': \[None, 5, 3, 1\]} You can see the format – a Python dictionary. This is a data structure that contains pairs of keys/values. The keys are the names of the hyperparameters and the values are the settings we want to try. Step Seven – Tuning the Model with a Cross-Validation Pipeline We are nearly there, nearly at the time when we can fit the model but first, a bit about cross-validation. This is a critical machine learning skill to learn because this is how we maximize the performance of our model while, at the same time, reducing the potential for overfitting. The cross-validation process helps us to get a reliable estimation of how a method performs in the model building. It’s done by using the same method to train the model repeatedly. The method is nothing more than a set of hyperparameters and these are the steps we take: 

1.  The data is split into k parts (equal) or folds. The typical split is k=10. 
2.  The model is trained on k-1 folds – the first 9 folds 
3.  The last fold is used to evaluate it 
4.  The second and third steps are repeated k number of times, but with a different fold held out for evaluation each time. 
5.  The performance across all the folds is aggregated and that becomes the performance metric. 

Why Cross-Validation is So Important Let’s say, like we are here, that we want a random forest regressor  trained. One hyperparameter that absolutely has to be tuned is the maximum allowable depth for each tree in the forest. How do you decide?  
That is where cross-validation steps in. With just your training dataset, cross-validation can evaluate lots of different hyperparameters and estimate how effective they are. In this way, the test set is kept clean and saved for the proper hold-out evaluation when the time comes to choose a model. For example, cross-validation can be used to tune linear regression, random forest, and K-Nearest models with only your training dataset, leaving your test set clean to choose the model family you want. Cross-Validation Pipeline When you perform cross-validation, your data pre-processing steps should go in the cross-validation loop, thus stopping your training folds from becoming sullied with influential testing data. The pipeline will look like this once all the pre-processing steps are included: 

1.  The data is split into k parts (equal) or folds. The typical split is k=10. 
2.  Do the pre-processing on k-1 training folds 
3.  The model is trained on the same k-1 folds 
4.  The hold-out is pre-processed using the transformations we use in step 2 
5.  The last fold is used to evaluate it 
6.  The second to fifth steps are repeated k number of times, but with a different fold held out for evaluation each time. 
7.  The performance across all the folds is aggregated and that becomes the performance metric. 

That might all look complicated but Scikit-Learn makes it dead simple: clf = GridSearchCV(pipeline, hyperparameters, cv=10) \# Fit and tune model clf.fit(X\_train, y\_train) It really is as simple as that. With GridSearchCV, cross-validation can be done over the entire grid, which is pretty much every possible permutation of the hyperparameters. The model or the pipeline is taken by GridSearchCV, along with the hyperparameters for tuning and how many folds are to be created. Now we can look at the hyperparameters G=cross-validation chose as the best ones: print clf.best\_params\_ \# {'randomforestregressor\_\_max\_depth': None, 'randomforestregressor\_\_max\_features': 'auto'} In our cases, the default parameters turned out to be the best ones. Step Eight – Refitting on the Training Dataset Once cross-validation has been used to tune the hyperparameters, refitting the model on the whole training dataset typically provides a small improvement in model performance. GridSearchCV can do this for you using the best hyperparameters it chose/ By default, this is already enabled but you should confirm it by doing this: print clf.refit \# True Now the clf object can be used as the model when we want to apply it to other datasets, which is what we will do next. Step Nine – Using the Test Data to Evaluate the Model Pipeline Now, we are getting to the end and this is one of the most straightforward of all the steps, provided you grasp one thing – the clf object used for tuning the hyperparameters may be used as if we were a model object. Now we can predict a new dataset: y\_pred = clf.predict(X\_test) Remember the metrics we imported a while back? We can use those to evaluate how the model is performing: print r2\_score(y\_test, y\_pred) \# 0.45044082571584243 print mean\_squared\_error(y\_test, y\_pred) \# 0.35461593750000003 So now we have to ask ourselves a question – is the performance good? Is it what we want? Typically, it is unlikely that your first model will be the best one but it is recommended to combine three separate strategies to determine if the model performance is good enough: 

1.  Begin with your model’s goal. Has the model solved the problem it set out to do? 
2.  Do some research, check out the academic literature to get an idea of the performance benchmarks you should consider for different data types, specifically, the type used in your model. 
3.  Look for low-hanging fruit to see how your model could be improved. 

The low-hanging fruit are the goals, measures, tasks, etc., that easily achievable. There are a few ways you can go about improving a model and a few things you can try are: 

1.  Use different regression model families, such as boosted trees or regularized regression, for example. 
2.  If the cost is not too much, collect some more data 
3.  Spend time doing exploratory data analysis and engineer better features 

Finally, when you try the first one, using different model families, stick to using the same training and test sets you trained the random forest model on.  That is the only way to compare performance on different models. Step 10 – Saving the Model to Use in the Future Well done for making it this far but we’re not quite finished yet. First, you need to save everything so you can reuse this model later on. It is simple enough to do: joblib.dump(clf, 'rf\_regressor.pkl') That’s all. If you need the model again in the future, just call this function: clf2 = joblib.load('rf\_regressor.pkl') \# Predict data set using loaded model clf2.predict(X\_test) And that, my friends, is a simplified way of building a random forest supervised learning model using Scikit-Learn. Here, for your information, is all the code we used: \# 2. Import libraries and modules import numpy as np import pandas as pd from sklearn.model\_selection import train\_test\_split from sklearn import preprocessing from sklearn.ensemble import RandomForestRegressor from sklearn.pipeline import make\_pipeline from sklearn.model\_selection import GridSearchCV from sklearn.metrics import mean\_squared\_error, r2\_score from sklearn.externals import joblib \# 3. Load red wine data. dataset\_url = 'http://mlr.cs.umass.edu/ml/machine-learning-databases/wine-quality/winequality-red.csv' data = pd.read\_csv(dataset\_url, sep=';') \# 4. Split data into training and test sets y = data.quality X = data.drop('quality', axis=1) X\_train, X\_test, y\_train, y\_test = train\_test\_split(X, y, test\_size=0.2, random\_state=123, stratify=y) \# 5. Declare data preprocessing steps pipeline = make\_pipeline(preprocessing.StandardScaler(), RandomForestRegressor(n\_estimators=100)) \# 6. Declare hyperparameters to tune hyperparameters = { 'randomforestregressor\_\_max\_features' : \['auto', 'sqrt', 'log2'\], 'randomforestregressor\_\_max\_depth': \[None, 5, 3, 1\]} \# 7. Tune model using cross-validation pipeline clf = GridSearchCV(pipeline, hyperparameters, cv=10) clf.fit(X\_train, y\_train) \# 8. Refit on the entire training set \# No additional code needed if clf.refit == True (default is True) \# 9. Evaluate model pipeline on test data pred = clf.predict(X\_test) print r2\_score(y\_test, pred) print mean\_squared\_error(y\_test, pred) \# 10. Save model for future use joblib.dump(clf, 'rf\_regressor.pkl') \# To load: clf2 = joblib.load('rf\_regressor.pkl') 

Top 12 Python Libraries for  
Machine and Deep Learning ![](image_rsrc9TV.jpg)Once upon a time, in the early days of machine learning, tasks were complete through manual algorithm coding, and annual coding of the statistical and mathematical formulae. Of course, this took vast amounts of time and was never that efficient but today we don’t have to do any of that. Today, we have plenty of machine learning libraries to call on and Python, being the most popular machine learning library, offers some of the very best libraries. These are the best ones. TensorFlow TensorFlow is, hands down, one of the very best machine learning libraries ever built. Designed by Google, it is an open-source library providing high-level numerical computation. The TensorFlow framework allows us to define and run computations using tensors. It is used for training and running DNNs (deep neural networks) for the development of artificial intelligence applications. A few of the TensorFlow benefits for machine and deep learning include: 

*   The ability to handle deep neural networks 
*   NLP – Natural Language Processing 
*   Partial Differential Equation 
*   Abstraction 
*   Text, speech and image recognition 
*   Easy way to collaborate code and ideas. 

Keras Keras is another highly popular library, an open-source one that focuses on neural networks. A Google engineer initially designed it for ONEIROS, or Open-Ended Neuro Electronic Intelligent Robot Operating System, but It was soon given full support in TensorFlow. It is one of the highest-level neural network APIs that can run on Theano, CNTK and TensorFlow and it can run on both CPUs and GPUs.  Keras makes building neural networks easy for both beginners and professionals, allowing for easy, fast prototyping. Some of the best tools and building blocks available in Keras include: 

*   Activation functions 
*   Cost functions 
*   Neural layers 
*   Batch normalization 
*   Dropout 
*   Objectives 
*   Pooling 

Using these features, Keras can extend TensorFlow’s usability for machine and deep learning. Backed up by a dedicated slack channel and a helpful community, it is easy to get all the support you need. Keras includes full support for standard neural networks, convolutional neural networks and recurrent neural networks. PyTorch PyTorch was developed by Facebook and offers support for Python, and C++/C++ Interface. Considered one of the best machine learning and deep learning frameworks, it is up against TensorFlow for the top spot. It is an open-source library based on another open-source library called Torch. Torch is a C library with a Lua wrapper. PyTorch offers tons of libraries and tools for NLP, Computer Vision and lots of other machine learning programs, and lets developers do  computations on tensors using GPE acceleration and helps create computational graphs. Some of its top features include: 

*   Tensor computations with GPU accelerated processing 
*   Easy to learn and use and integrates with the Python ecosystem easily 
*   Supports tape-based auto diff neural networks 

Scikit-Learn Highly active in machine learning, scikit-Learn is commonly used in machine learning and is easily integrated with Pandas, NumPy and other machine learning libraries. It is one of the top libraries for classical machine learning algorithms and is built on SciPy and NumPy. It has support for nearly all unsupervised and supervised machine learning algorithms and can be used for data analysis and data mining, which makes it the perfect tool for beginners. Scikit-Learn supports the following algorithms: 

*   Classification 
*   Clustering 
*   Dimensionality Reduction 
*   Model Selection 
*   Preprocessing 
*   Regression 

Pandas Pandas is one of the top data analysis libraries in Python and is used before preparing a dataset for training. It enables easy working with structured multidimensional data and time-series. Pandas has no direct relation to machine learning; instead it deals with data  extraction and data preparation. It offers high-level data structures and lots of data analysis tools, along with plenty of data groping, data combining and data filtering tools. Some of the top Pandas features are: 

*   Reshaping and pivoting data 
*   Merging and joining datasets 
*   Handling data alignment and missing data 
*   Fancy Indexing, Hierarchical Indexing, and many other indexing options 
*   Data filtration 

Pandas uses data frames, which are nothing more than 2D data representations. NLTK NLTK, or Natural Language Toolkit, is a library that works with NLP, one of the most popular human language data libraries. It provides simple, user-friendly interfaces with plenty of lexical resources, such as WordNet, FrameNet, and Word2Vec, among others. Some of its best features include: 

*   Searching for specific keywords in documents 
*   Text classification and tokenization 
*   Voice and handwriting recognition 
*   Word lemmatization and word stemming 

Spark MLlib MLlib was developed by Apache Spark and is a machine learning library designed to help scale computations. It is user-friendly and integrates smoothly with many other tools and is one of the best tools to develop machine learning applications and algorithms. Spark MLlib offers programmers the ability to work with these  algorithms: 

*   Basic Statistics 
*   Classification 
*   Clustering 
*   Dimensional Reduction 
*   Feature Extraction 
*   Optimization 
*   Regression 

Theano Theano is one of the most powerful libraries, helping us define, optimize and evaluate mathematical expressions that use multi-dimensional arrays. Machine learning is pretty much made up of statistics and mathematics and, with Theano,  we can optimize the GPU and CPU to make things more efficient. Theano is used for self-verification and unit-testing to help us find and diagnose various errors. It has long been used in some of the largest scale projects, some of the most computationally intensive projects but remains simple to use. A few of the features that make Theano capable of doing that are: 

*   Support to enable better GPU performance over CPUs in heavy-duty, intensive computations 
*   Support for strong integration NumPy 
*   Can evaluate any variables, even the tricky one, in a fast and stable way. 
*   Helps you create customized C code for math operations. 

MXNet MXNet is one of the most efficient and flexible machine learning libraries, especially for deep learning. Used for the training and deployment for deep neural networks, it is scalable and has support for quick training.  Built by Apache, it works with multiple programming languages, including Python, Scala, R. Julia, Perl, C++, Go and more. Its scalability and portability enable easy movement between platforms and the ability to scale it as per your requirements. It is used by some of the biggest tech names, including MIT, Intel and Microsoft. SciPy SciPy is another popular machine learning library that offers linear algebra, optimizations, statistics, and integration modules. Do not confuse it with the SciPy Stack – the SciPy library is a part of the Stack and is also incredibly useful for manipulating images. NumPy NumPy is responsible for handling multi-dimensional data and some of the more complex mathematical functions that operate on the data. It is also popular for processing matrices using some of the most high-level mathematical functions. NumPy is commonly used for scientific computations and is very useful for linear algebra, random number and Fourier transform. TensorFlow and other high-end libraries use NumPy to manipulate tensors. It Provides fast computation and fast execution of some of the more complicated array functions and some of its best points include: 

*   Supports logical and mathematical operations 
*   Shape manipulation 
*   Select and Sort capabilities 
*   Discrete Fourier Transformations 
*   Random simulations 
*   Linear algebra 
*   Statistical operations 
*   N-dimensional array support 

Matplotlib Matplotlib is one of the most popular data visualization libraries in Python but is not related directly to machine learning. It is useful for allowing us to visualize data patterns and is a library for 2D plotting, creating plots and graphs. Plotting is made easy with PyPlot, a useful module containing features that let us control font properties, line styles, format axes, and so on. It offers lots of plots and graphs, including bar charts, histograms, and more. 

Conclusion ![](image_rsrc9SG.jpg)It’s great to see you here, I’m glad you made it through these tutorials. Right now, you probably think you are ready to start predicting all sorts of things, even who you think the next US president might be.  Luckily, there are plenty of frameworks and libraries that can help you along your way, not least the three we discussed here – TensorFlow, Keras, and Scikit-Learn. Before you get stuck into machine learning, before you start picking libraries at random, there are a few things you should consider. What is Your Goal? This is something you need to consider with every project because the models and the framework you use will depend entirely on the nature of that project. If you are looking for a model that predicts movie review opinions, for example, you want a deep learning approach that uses PyTorch or Keras. If you wanted to predict the future prices of a major league baseball game’s tickets, you would use Scikit-Learn’s ability with structured data. Both Keras and Scikit-Learn offer the ability to build no-nonsense, minimal structures that can be built, trained and deployed in minutes, while PyTorch and TensorFlow are for more complex modeling. Start Simple When you look for machine learning tutorials online, you might find that you are duped straight in at the deep end, coding complicated regularization functions, for example. That’s not the best place to start but the point is, the frameworks are all different and not all of them are easy to learn off the bat. Take Scikit-Learn, for example. Just three lines of code let you build and train the simplest of models : from sklearn.svm import SVC model = SVC() model.fit(X, y)             While you may not get the best results, starting simple is the best way to learning properly. Only then can you move on to more complex models to build something more challenging. By contrast, if you step straight into building end-to-end models with PyTorch or TensorFlow, you are likely to find it somewhat overwhelming. Don’t Try Learning it All Sure, this might seem obvious but many beginners believe that they should learn every single framework thoroughly to get a job as a data scientist or a machine learning engineer.  Don’t try to learn too much – you will find it much harder to figure it all out. The best way is to start with one framework and learn the fundamental concepts. Along the way, you will learn about other frameworks because most of them use each other to work. Pick a problem and try to solve it with a framework – that way, you will gain a better understanding of how it works. Takeaways 

*   Explore all your options and weigh them up before you commit to an in-depth look at any specific framework. You might find something else is more worthwhile learning. 
*   If you can’t pull off a spectacular model straight away, so what? Half the fun of learning is starting from the bottom and building up, seeing your knowledge grow as you do. 
*   Don’t try to learn too much in one go. Confidence is valuable but trying to learn absolutely every single minute detail about a framework is more likely to see you fail. You don’t need to know everything to learn how to solve a problem. 

Hopefully, with all the practical examples included in the book, I have been able to give you a decent grounding in all three machine  learning frameworks. Yes, I could have done an end-to end problem that encompassed all three but I felt it was better to look at them all individually. I hope you enjoyed this book and good luck on your machine learning journey. 

References ![](image_rsrc9SG.jpg)An Introduction to Machine Learning. (n.d.). DigitalOcean. https://www.digitalocean.com/community/tutorials/an-introduction-to-machine-learning https://www.facebook.com/jason.brownlee.39. (2019, July 4). Keras Tutorial: Develop Your First Neural Network in Python Step-By-Step. Machine Learning Mastery. https://machinelearningmastery.com/tutorial-first-neural-network-python-keras/ Keras Tutorial for Beginners with Python: Deep Learning EXAMPLE. (n.d.). Www.Guru99.com. Retrieved from https://www.guru99.com/keras-tutorial.html Pant, A. (2019, January 22). Introduction to Machine Learning for Beginners. Medium. https://towardsdatascience.com/introduction-to-machine-learning-for-beginners-eed6024fdb08 Scikit-Learn Tutorial: Machine Learning in Python Examples. (n.d.). Www.Guru99.com. Retrieved from https://www.guru99.com/scikit-learn-tutorial.html Tensorboard Tutorial: Graph Visualization with Example. (n.d.). Www.Guru99.com. Retrieved from https://www.guru99.com/tensorboard-tutorial.html TensorFlow Basics: Tensor, Shape, Type, Graph, Sessions & Operators. (n.d.). Www.Guru99.com. Retrieved from https://www.guru99.com/tensor-tensorflow.html What is TensorFlow? Introduction, Architecture & Example. (2019, June 29). Guru99.com. https://www.guru99.com/what-is-tensorflow.html Yegulalp, S. (2019, June 18). What is TensorFlow? The machine learning library explained. InfoWorld. https://www.infoworld.com/article/3278008/what-is-tensorflow-the-machine-learning-library-explained.html