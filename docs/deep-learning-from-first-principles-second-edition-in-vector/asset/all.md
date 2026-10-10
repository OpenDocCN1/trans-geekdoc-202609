   

![Image 1](index-1_1.jpg)

Deep Learning from first principles –

Second Edition

In vectorized Python, R and Octave

This book is dedicated to the memory of my late Mom and Dad who continue to be the force behind all my actions

This book is also dedicated to my wife Shanthi for her support and for giving me the space to work, and finally to my daughter, Shreya, for bringing joy to my life.

Table of Contents

[Preface](#index_split_000.html#p6)

[Introduction](#index_split_000.html#p10)

[1\. Logistic Regression as a Neural Network](#index_split_000.html#p13)

[2\. Implementing a simple Neural Network](#index_split_000.html#p36)

[3\. Building a L- Layer Deep Learning Network](#index_split_000.html#p79)

[4\. Deep Learning network with the Softmax](#index_split_000.html#p134)

[5\. MNIST classification with Softmax](#index_split_001.html#p161)

[6\. Initialization, regularization in Deep Learning](#index_split_001.html#p194)

[7\. Gradient Descent Optimization techniques](#index_split_001.html#p262)

[8\. Gradient Check in Deep Learning](#index_split_002.html#p313)

[1\. Appendix A](#index_split_002.html#p347)

[2\. Appendix 1 – Logistic Regression as a Neural Network](#index_split_002.html#p356)

[3\. Appendix 2 - Implementing a simple Neural Network](#index_split_002.html#p369)

[4\. Appendix 3 - Building a L- Layer Deep Learning Network](#index_split_002.html#p391)

[5\. Appendix 4 - Deep Learning network with the Softmax](#index_split_003.html#p424)

[6\. Appendix 5 - MNIST classification with Softmax](#index_split_003.html#p441)

[7\. Appendix 6 - Initialization, regularization in Deep Learning](#index_split_004.html#p495)

[8\. Appendix 7 - Gradient Descent Optimization techniques](#index_split_005.html#p564)

[9\. Appendix 8 – Gradient Check](#index_split_006.html#p662)

[References](#index_split_007.html#p774)

**Preface**

*You don’t understand anything until you learn it more than one* *way.* Marvin Minsky

The last decade and some, has witnessed some remarkable

advancements in the area of Deep Learning. This area of AI has proliferated into many branches - Deep Belief Networks, Recurrent Neural Networks, Convolution Neural Networks, Adversorial

Networks, Reinforcement Learning, Capsule Networks and the list goes on. These years have also resulted in Deep Learning to move from the research labs and closer to the home, thanks to progress in hardware, strorage and cloud technology.

One common theme when you listen to Deep Learning pundits, is that in order to get a good grasp of the Deep Learning domain, it is essential that you learn to build such a network from scratch. It is towards that end that this book was written.

In this book, I implement Deep Learning Networks from the basics.

Each successive chapter builds upon the implementations of the previous chapters so that by chapter 7, I have a full-fledged, generic L-Layer Deep Learning network, with all the bells and whistles. All the necessary derivations required for implementing a multi-layer Deep Learning network is included in the chapters. Detailed

derivations for forward propagation and backward propagation cycles with relu, tanh and sigmoid hidden layer units, and sigmoid and softmax output activation units are included. These may serve to jog your memory of all those whose undergrad calculus is a little rusty.

The first chapter derives and implements logisitic regression as a neural network in Python, R and Octave. The second chapter deals with the derivation and implementation of the most primitive neural network, one with just one hidden layer. The third chapter extends on the principles of the 2nd chapter and implements a L-Layer Deep

Learning network with the sigmoid activation in vectorized Python, R

and Octave. This implementation can include an arbitrary number of hidden units and any number of hidden layers for the sigmoid

activation output layer. The fourth chapter introduces the Softmax function required for multi-class classification. The Jacobian of the Softmax and cross-entropy loss is derived and then this implemented to demonstrate multi-class classification of a simple spiral data set.

The fifth chapter incorporates the softmax implementation of the fourth chapter into the L-Layer implementation in the 3rd chapter.

With this enhancement, the fifth chapter classifies MNIST digits using Softmax output activation unit in a generic L-Layer implementation.

The sixth chapter addresses different initialization techniques like He and Xavier. Further, this chapter also discusses and implements L2

regularization and random dropout technique. The seventh chapter looks at gradient descent optimization techniques like learning rate decay, momentum, rmsprop, and adam. The eight chapter discusses a critical technique, that is required to ensure the correctness of the backward propagation implementation. Specifically this chapter discusses and implements ‘gradient checking’ and also demonstrates how to find bugs in your implementation.

All the chapters include vectorized implementations in Python, R and Octave. The implementations are identical. So, if your are conversant in any one of the languages you can look at the implementations in any other language. It should be a good way to learn the other language.

**Note**: The functions that are invoked in each of the chapters are included in Appendix 1-Appendix 8.

Feel free to check out the implementations by playing around with the hyper-parameters. A good way to learn is to take the code apart. You could also try to enhance the implementation to include other activation functions like the leaky relu, parametric relu etc. Maybe, you could work on other regularization or gradient descent

optimization methods. There may also be opportunities to optimize my code with further vectorization of functions.

This course is largely based on Prof Andrew Ng’s Deep Learning

[Specialization (https://www.coursera.org/specializations/deep-](https://www.coursera.org/specializations/deep-learning)

[learning).](https://www.coursera.org/specializations/deep-learning)

I would like to thank Prof Andrew Ng and Prof Geoffrey Hinton for making the apparent complexity of the Deep Learning subject into remarkably simple concepts through their courses.

I hope this book sets you off on a exciting and challenging journey into the Deep Learning domain

Tinniam V Ganesh

16 May 2018

**Introduction**

This is the second edition of my book ‘Deep Learning from first principles: Second Edition – In vectorized Python, R and Octave’.

Since this book has about 70% code, I wanted to make the code more readable. Hence, in this second edition, I have changed all the code to use the fixed-width font Lucida Console. This makes the code more organized and can be more easily absorbed. I have also included line numbers for all functions and code snippets. Finally, I have corrected some of the typos in the book.

Other books by the author (available on Amazon in paperback and kindle versions)

1\. Practical Machine Learning with R and Python: Second Edition

– Machine Learning in stereo

2\. Beaten by sheer pace: Third Edition – Cricket analytics with yorkr

3\. Cricket analytics with cricketr:Third Edition

**1.**

**Logistic Regression as a Neural**

**Network**

*“You don’t perceive objects as they are. You perceive them as you* *are.”*

*“Your interpretation of physical objects has everything to do with the* *historical trajectory of your brain – and little to do with the objects* *themselves.”*

*“The brain generates its own reality, even before it receives* *information coming in from the eyes and the other senses. This is* *known as the internal model”*

David Eagleman - The Brain: The Story of You

This chapter deals with the implementation of Logistic regression as a 2-layer Neural Network i.e. a Neural Network that just has an input layer and an output layer and with no hidden layer. This 2-layer network is implemented in Python, R and Octave languages. I have included Octave, into the mix, as Octave is a close cousin of Matlab.

These implementations in Python, R and Octave are equivalent

vectorized implementations. Therefore, if you are familiar in any one of the languages, you should be able to look at the corresponding code in the other two. The implementations of the functions invoked in this chapter are in Appendix 1 – Logistic Regression as a Neural Network.

You can also clone/download the vectorized code in Pythin, R and Octave from Github at DeepLearningFromFirstPrinciples

’(https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/master/Chap1-LogisticRegressionAsNeuralNetwork). To start with, Logistic

Regression is performed using sklearn’s logistic regression package, for the cancer data set also from sklearn. This is shown below

**1.Logistic Regression**

import numpy as np

import pandas as pd

import os

import matplotlib.pyplot as plt

from sklearn.model\_selection import train\_test\_split

from sklearn.linear\_model import LogisticRegression

from sklearn.datasets import make\_classification, make\_blobs

from sklearn.metrics import confusion\_matrix

from matplotlib.colors import ListedColormap

from sklearn.datasets import load\_breast\_cancer

\# Load the cancer data

(X\_cancer, y\_cancer) = load\_breast\_cancer(return\_X\_y = True)

X\_train, X\_test, y\_train, y\_test = train\_test\_split(X\_cancer, y\_cancer, random\_state = 0)

\# Call the Logisitic Regression function

clf = LogisticRegression().fit(X\_train, y\_train)

#Print accuracy of training and test set

print('Accuracy of Logistic regression classifier on training set: {:.2f}'

.format(clf.score(X\_train, y\_train)))

print('Accuracy of Logistic regression classifier on test set: {:.2f}'

.format(clf.score(X\_test, y\_test)))

\## Accuracy of Logistic regression classifier on training set: 0.96

\## Accuracy of Logistic regression classifier on test set: 0.96

![Image 2](index-15_1.jpg)

![Image 3](index-15_2.jpg)

**2.Logistic Regression as a 2-layer Neural**

**Network**

In the following section, Logistic Regression is implemented as a 2-layer Neural Network in Python, R and Octave. The same cancer data set from sklearn is used to train and test the Neural Network in Python, R and Octave. This can be represented diagrammatically as below

The cancer data set has 30 input features, and the target variable

‘output’ is either 0 or 1. Hence, the sigmoid activation function will be used in the output layer for classification.

This simple 2-layer Neural Network is shown below.

At the input layer, there are 30 features and the corresponding weights of these inputs which are initialized to small random values.

where ‘b’ is the bias term

![Image 4](index-16_1.jpg)

![Image 5](index-16_2.jpg)

The Activation function is the sigmoid function which is given by The Loss, when the sigmoid function is used in the output layer, is given by

(1)

![Image 6](index-17_1.jpg)

![Image 7](index-17_2.jpg)

![Image 8](index-17_3.jpg)

**3.Gradient Descent**

**3.1 Forward propagation**

The forward propagation cycle of the Neural Network computes the output Z and the activation the sigmoid activation function. Then using the output ‘y’ for the given features, the ‘Loss’ is computed using equation (1) above.

**3.2 Backward propagation**

The backward propagation cycle determines how the ‘Loss’ is

impacted for small variations from the previous layers up to the input layer. In other words, backward propagation computes the changes in the weights at the input layer, which will minimize the loss at the output layer. Several cycles of gradient descent are performed in the path of steepest descent to find the local minima. In other words, the set of weights and biases, at the input layer, which will result in the lowest loss, is computed by gradient descent. The weights at the input layer are decreased by a parameter known as the ‘learning rate’. Too big a ‘learning rate’ can overshoot the local minima, and too small a

‘learning rate’ can take a long time to reach the local minima.

Gradient Descent iterated through this forward propagation and backward propagation cycle until the loss is minimized. This is done for ‘m’ training examples.

**3.3Chain rule of differentiation**

Let y=f(u)

and u=g(x) then by chain rule

**3.4Derivative of sigmoid**

Let 

 then

![Image 9](index-18_1.jpg)

![Image 10](index-18_2.jpg)

![Image 11](index-18_3.jpg)

![Image 12](index-18_4.jpg)

![Image 13](index-18_5.jpg)

![Image 14](index-18_6.jpg)

![Image 15](index-18_7.jpg)

![Image 16](index-18_8.jpg)

![Image 17](index-18_9.jpg)

![Image 18](index-18_10.jpg)

![Image 19](index-18_11.jpg)

![Image 20](index-18_12.jpg)

![Image 21](index-18_13.jpg)

![Image 22](index-18_14.jpg)

![Image 23](index-18_15.jpg)

![Image 24](index-18_16.jpg)

![Image 25](index-18_17.jpg)

 and

Using the chain rule of differentiation we get

Therefore 

 -(2)

The 3 equations for the 2 layer Neural Network representation of Logistic Regression are

\-(a)

\-(b)

\-

(c)

Where L is the loss for the sigmoid output activation function The back-propagation step requires the computation of

and

. In the case of regression it would be

and

where dE is the Mean Squared Error function.

Computing the derivatives for the Loss function we have

\-(d)

because

Also from equation (2) we can write

– (e)

By chain rule

therefore substituting the results of (d) & (e) into the equation above

![Image 26](index-19_1.jpg)

![Image 27](index-19_2.jpg)

![Image 28](index-19_3.jpg)

![Image 29](index-19_4.jpg)

![Image 30](index-19_5.jpg)

![Image 31](index-19_6.jpg)

![Image 32](index-19_7.jpg)

![Image 33](index-19_8.jpg)

![Image 34](index-19_9.jpg)

![Image 35](index-19_10.jpg)

![Image 36](index-19_11.jpg)

![Image 37](index-19_12.jpg)

we get

(f)

Finally

\-(g)

– (h)

and from (f) we have

Therefore (g) reduces to

\-(i)

Also

\-(j)

Since

and using (f) in (j) we get

The gradient computes the weights at the input layer and the

corresponding bias by using the values

of

and

The computation graph representation in the book Deep Learning

[(http://www.deeplearningbook.org/)](http://www.deeplearningbook.org/) : Ian Goodfellow, Yoshua Bengio, Aaron Courville, is very useful to visualize and compute the backward propagation. For the 2-layer Neural Network of Logistic Regression the computation graph is shown below

![Image 38](index-20_1.jpg)

**4\. Neural Network for Logistic**

**Regression -Python code**

import numpy as np

import pandas as pd

import os

import matplotlib.pyplot as plt

from sklearn.model\_selection import train\_test\_split

\# Define the sigmoid function

def sigmoid(z):

a=1/(1+np.exp(-z))

return a

\# Initialize weights and biases

def initialize(dim):

w = np.zeros(dim).reshape(dim,1)

b = 0

return w

\# Compute the loss

def computeLoss(numTraining,Y,A):

loss=-1/numTraining \*np.sum(Y\*np.log(A) + (1-Y)\*(np.log(1-A))) return(loss)

\# Execute the forward propagation

def forwardPropagation(w,b,X,Y):

\# Compute Z

Z=np.dot(w.T,X)+b

\# Determine the number of training samples

numTraining=float(len(X))

\# Compute the output of the sigmoid activation function

A=sigmoid(Z)

#Compute the loss

loss = computeLoss(numTraining,Y,A)

\# Compute the gradients dZ, dw and db

 dZ=A-Y

dw=1/numTraining\*np.dot(X,dZ.T)

db=1/numTraining\*np.sum(dZ)

\# Return the results as a dictionary

gradients = {"dw": dw,

"db": db}

loss = np.squeeze(loss)

return gradients,loss

\# Compute Gradient Descent

def gradientDescent(w, b, X, Y, numIerations, learningRate):

losses=\[\]

idx =\[\]

\# Iterate

for i in range(numIerations):

gradients,loss=forwardPropagation(w,b,X,Y)

#Get the derivates

dw = gradients\["dw"\]

db = gradients\["db"\]

w = w-learningRate\*dw

b = b-learningRate\*db

\# Store the loss

if i % 100 == 0:

idx.append(i)

losses.append(loss)

\# Set params and grads

params = {"w": w,

"b": b}

grads = {"dw": dw,

"db": db}

return params, grads, losses,idx

\# Predict the output for a training set

def predict(w,b,X):

size=X.shape\[1\]

yPredicted=np.zeros((1,size))

 Z=np.dot(w.T,X)

\# Compute the sigmoid

A=sigmoid(Z)

for i in range(A.shape\[1\]):

#If the value is > 0.5 then set as 1

if(A\[0\]\[i\] > 0.5):

yPredicted\[0\]\[i\]=1

else:

\# Else set as 0

yPredicted\[0\]\[i\]=0

return yPredicted

#Normalize the data

def normalize(x):

x\_norm = None

x\_norm = np.linalg.norm(x,axis=1,keepdims=True)

x= x/x\_norm

return x

\# Run the 2-layer Neural Network on the cancer data set

from sklearn.datasets import load\_breast\_cancer

\# Load the cancer data

(X\_cancer, y\_cancer) = load\_breast\_cancer(return\_X\_y = True)

\# Create train and test sets

X\_train, X\_test, y\_train, y\_test = train\_test\_split(X\_cancer, y\_cancer, random\_state = 0)

\# Normalize the data for better performance

X\_train1=normalize(X\_train)

\# Create weight vectors of zeros. The size is the number of features in the data set=30

w=np.zeros((X\_train.shape\[1\],1))

#w=np.zeros((30,1))

b=0

#Normalize the training data so that gradient descent performs better

X\_train1=normalize(X\_train)

#Transpose X\_train so that we have a matrix as (features, numSamples) X\_train2=X\_train1.T

\# Reshape to remove the rank 1 array and then transpose

y\_train1=y\_train.reshape(len(y\_train),1)

y\_train2=y\_train1.T

\# Run gradient descent for 4000 times and compute the weights parameters, grads, costs,idx = gradientDescent(w, b, X\_train2, y\_train2, numIerations=4000, learningRate=0.75)

w = parameters\["w"\]

b = parameters\["b"\]

\# Normalize X\_test

X\_test1=normalize(X\_test)

#Transpose X\_train so that we have a matrix as (features, numSamples) X\_test2=X\_test1.T

#Reshape y\_test

y\_test1=y\_test.reshape(len(y\_test),1)

y\_test2=y\_test1.T

\# Predict the values for

yPredictionTest = predict(w, b, X\_test2)

yPredictionTrain = predict(w, b, X\_train2)

\# Print the accuracy

print("train accuracy: {} %".format(100 - np.mean(np.abs(yPredictionTrain -

y\_train2)) \* 100))

print("test accuracy: {} %".format(100 - np.mean(np.abs(yPredictionTest -

y\_test)) \* 100))

\# Plot the Costs vs the number of iterations

fig1=plt.plot(idx,costs)

fig1=plt.title("Gradient descent-Cost vs No of iterations") fig1=plt.xlabel("No of iterations")

fig1=plt.ylabel("Cost")

![Image 39](index-25_1.jpg)

fig1.figure.savefig("fig1", bbox\_inches='tight')

\## train accuracy: 90.3755868545 %

\## test accuracy: 89.5104895105 %

**Note**: The Accuracy on the training and test set is 90.37% and 89.51%. This is comparatively poorer than the 96%, which the logistic regression of sklearn achieves! But, this is mainly because of the absence of hidden layers which is the real power of neural networks .

**5\. Neural Network for Logistic**

**Regression -R code**

source("RFunctions-1.R")

\# Define the sigmoid function

sigmoid <- function(z){

a <- 1/(1+ exp(-z))

a

}

\# Compute the loss

computeLoss <- function(numTraining,Y,A){

loss <- -1/numTraining\* sum(Y\*log(A) + (1-Y)\*log(1-A))

return(loss)

}

\# Compute forward propagation

forwardPropagation <- function(w,b,X,Y){

\# Compute Z

Z <- t(w) %\*% X +b

#Set the number of samples

numTraining <- ncol(X)

\# Compute the activation function

A=sigmoid(Z)

#Compute the loss

loss <- computeLoss(numTraining,Y,A)

\# Compute the gradients dZ, dw and db

dZ<-A-Y

dw<-1/numTraining \* X %\*% t(dZ)

db<-1/numTraining\*sum(dZ)

fwdProp <- list("loss" = loss, "dw" = dw, "db" = db) return(fwdProp)

}

\# Perform one cycle of Gradient descent

gradientDescent <- function(w, b, X, Y, numIerations, learningRate){

losses <- NULL

idx <- NULL

\# Loop through the number of iterations

for(i in 1:numIerations){

fwdProp <-forwardPropagation(w,b,X,Y)

#Get the derivatives

dw <- fwdProp$dw

db <- fwdProp$db

#Perform gradient descent

w = w-learningRate\*dw

b = b-learningRate\*db

l <- fwdProp$loss

\# Stoe the loss

if(i %% 100 == 0){

idx <- c(idx,i)

losses <- c(losses,l)

}

}

\# Return the weights and losses

gradDescnt <-

list("w"=w,"b"=b,"dw"=dw,"db"=db,"losses"=losses,"idx"=idx) return(gradDescnt)

}

\# Compute the predicted value for input

predict <- function(w,b,X){

m=dim(X)\[2\]

\# Create a ector of 0's

yPredicted=matrix(rep(0,m),nrow=1,ncol=m)

Z <- t(w) %\*% X +b

\# Compute sigmoid

A=sigmoid(Z)

for(i in 1:dim(A)\[2\]){

\# If A > 0.5 set value as 1

if(A\[1,i\] > 0.5)

 yPredicted\[1,i\]=1

else

\# Else set as 0

yPredicted\[1,i\]=0

}

return(yPredicted)

}

\# Normalize the matrix

normalize <- function(x){

#Create the norm of the matrix.Perform the Frobenius norm of the matrix n<-as.matrix(sqrt(rowSums(x^2)))

#Sweep by rows by norm. Note '1' in the function which performing on every row

normalized<-sweep(x, 1, n, FUN="/")

return(normalized)

}

\# Run the 2 layer Neural Network on the cancer data set

\# Read the data (from sklearn)

cancer <- read.csv("cancer.csv")

\# Rename the target variable

names(cancer) <- c(seq(1,30),"output")

\# Split as training and test sets

train\_idx <- trainTestSplit(cancer,trainPercent=75,seed=5) train <- cancer\[train\_idx, \]

test <- cancer\[-train\_idx, \]

\# Set the features

X\_train <-train\[,1:30\]

y\_train <- train\[,31\]

X\_test <- test\[,1:30\]

y\_test <- test\[,31\]

\# Create a matrix of 0's with the number of features

w <-matrix(rep(0,dim(X\_train)\[2\]))

b <-0

X\_train1 <- normalize(X\_train)

X\_train2=t(X\_train1)

\# Reshape then transpose

y\_train1=as.matrix(y\_train)

y\_train2=t(y\_train1)

\# Perform gradient descent

gradDescent= gradientDescent(w, b, X\_train2, y\_train2, numIerations=3000, learningRate=0.77)

\# Normalize X\_test

X\_test1=normalize(X\_test)

#Transpose X\_train so that we have a matrix as (features, numSamples) X\_test2=t(X\_test1)

#Reshape y\_test and take transpose

y\_test1=as.matrix(y\_test)

y\_test2=t(y\_test1)

\# Use the values of the weights generated from Gradient Descent yPredictionTest = predict(gradDescent$w, gradDescent$b, X\_test2) yPredictionTrain = predict(gradDescent$w, gradDescent$b, X\_train2) sprintf("Train accuracy: %f",(100 - mean(abs(yPredictionTrain - y\_train2)) \*

100))

\## \[1\] "Train accuracy: 90.845070"

sprintf("test accuracy: %f",(100 - mean(abs(yPredictionTest - y\_test)) \* 100))

\## \[1\] "test accuracy: 87.323944"

df <-data.frame(gradDescent$idx, gradDescent$losses)

names(df) <- c("iterations","losses")

ggplot(df,aes(x=iterations,y=losses)) + geom\_point() + geom\_line(col="blue") +

ggtitle("Gradient Descent - Losses vs No of Iterations") +

xlab("No of iterations") + ylab("Losses")

![Image 40](index-30_1.jpg)

**6.Neural Network for Logistic**

**Regression -Octave code**

1;

\# Define sigmoid function

function a = sigmoid(z)

a = 1 ./ (1+ exp(-z));

end

\# Compute the loss

function loss=computeLoss(numtraining,Y,A)

loss = -1/numtraining \* sum((Y .\* log(A)) + (1-Y) .\* log(1-A)); end

\# Perform forward propagation

function \[loss,dw,db,dZ\] = forwardPropagation(w,b,X,Y)

\# Compute Z

Z = w' \* X + b;

numtraining = size(X)(1,2);

\# Compute sigmoid

A = sigmoid(Z);

#Compute loss. Note this is element wise product

loss =computeLoss(numtraining,Y,A);

\# Compute the gradients dZ, dw and db

dZ = A-Y;

dw = 1/numtraining\* X \* dZ';

db =1/numtraining\*sum(dZ);

end

\# Compute Gradient Descent

function \[w,b,dw,db,losses,index\]=gradientDescent(w, b, X, Y, numIerations, learningRate)

#Initialize losses and idx

losses=\[\];

index=\[\];

\# Loop through the number of iterations

 for i=1:numIerations,

\[loss,dw,db,dZ\] = forwardPropagation(w,b,X,Y);

\# Perform Gradient descent

w = w - learningRate\*dw;

b = b - learningRate\*db;

if(mod(i,100) ==0)

\# Append index and loss

index = \[index i\];

losses = \[losses loss\];

endif

end

end

\# Determine the predicted value for dataset

function yPredicted = predict(w,b,X)

m = size(X)(1,2);

yPredicted=zeros(1,m);

\# Compute Z

Z = w' \* X + b;

\# Compute sigmoid

A = sigmoid(Z);

for i=1:size(X)(1,2),

\# Set predicted as 1 if A > 0,5

if(A(1,i) >= 0.5)

yPredicted(1,i)=1;

else

yPredicted(1,i)=0;

endif

end

end

\# Normalize by dividing each value by the sum of squares

function normalized = normalize(x)

\# Compute Frobenius norm. Square the elements, sum rows and then find square root

a = sqrt(sum(x .^ 2,2));

\# Perform element wise division

normalized = x ./ a;

end

\# Split into train and test sets

function \[X\_train,y\_train,X\_test,y\_test\] = trainTestSplit(dataset,trainPercent)

\# Create a random index

ix = randperm(length(dataset));

\# Split into training

trainSize = floor(trainPercent/100 \* length(dataset));

train=dataset(ix(1:trainSize),:);

\# And test

test=dataset(ix(trainSize+1:length(dataset)),:);

X\_train = train(:,1:30);

y\_train = train(:,31);

X\_test = test(:,1:30);

y\_test = test(:,31);

end

\# Read the data

cancer=csvread("cancer.csv");

\# Split as train and test

\[X\_train,y\_train,X\_test,y\_test\] = trainTestSplit(cancer,75);

#Initialize w and b

w=zeros(size(X\_train)(1,2),1);

b=0;

#Normalize training

X\_train1=normalize(X\_train);

X\_train2=X\_train1';

y\_train1=y\_train';

#Perform gradient descent

\[w1,b1,dw,db,losses,idx\]=gradientDescent(w, b, X\_train2, y\_train1, numIerations=3000, learningRate=0.75);

\# Normalize X\_test

X\_test1=normalize(X\_test);

#Transpose X\_train so that we have a matrix as (features, numSamples) X\_test2=X\_test1';

![Image 41](index-34_1.jpg)

y\_test1=y\_test';

\# Use the values of the weights generated from Gradient Descent yPredictionTest = predict(w1, b1, X\_test2);

yPredictionTrain = predict(w1, b1, X\_train2);

#Compute Accouracy

trainAccuracy=100-mean(abs(yPredictionTrain - y\_train1))\*100

testAccuracy=100- mean(abs(yPredictionTest - y\_test1))\*100

trainAccuracy = 90.845

testAccuracy = 89.510

graphics\_toolkit('gnuplot')

plot(idx,losses);

title ('Gradient descent- Cost vs No of iterations');

xlabel ("No of iterations");

ylabel ("Cost");

**Conclusion**

This chapter starts with a simple 2-layer Neural Network implementation of Logistic Regression. Clearly, the performance of this simple Neural Network is comparatively poor to the highly optimized sklearn’s Logistic Regression. This is because the above neural network did not have any hidden layers. Deep Learning & Neural Networks achieve extraordinary performance because of the presence of deep hidden layers

**2.**

**Implementing a simple Neural**

**Network**

*“What does the world outside your head really ‘look’ like? Not only is* *there no color, there’s also no sound: the compression and expansion* *of air is picked up by the ears and turned into electrical signals. The* *brain then presents these signals to us as mellifluous tones and* *swishes and clatters and jangles. Reality is also odorless: there’s no* *such thing as smell outside our brains. Molecules floating through the* *air bind to receptors in our nose and are interpreted as different* *smells by our brain. The real world is not full of rich sensory events;* *instead, our brains light up the world with their own sensuality.”*

The Brain: The Story of You” by David Eagleman

“*The world is Maya, illusory. The ultimate reality, the Brahman, is all-pervading and all-permeating, which is colourless, odourless,* *tasteless, nameless and formless*“

Bhagavad Gita

**1.Introduction**

In the first chapter, I implemented Logistic Regression, in vectorized Python, R and Octave, with a wannabe Neural Network (a Neural Network with no hidden layers). In this second chapter, I implement a regular, but somewhat primitive Neural Network, (a Neural Network with just 1 hidden layer). This chapter implements classification of manually created datasets, where the different clusters of the 2 classes are not linearly separable.

Neural Network perform well in learning all sorts of non-linear boundaries between classes. Initially logistic regression is used to perform the classification. A simple 3-layer Neural Network is then used on the same data set and the decision boundary plotted. Vanilla logistic regression performs quite poorly. Using SVMs with a radial basis kernel would have performed much better in creating non-linear boundaries. The implementations of the functions invoked in this chapter are in Appendix 2 - Implementing a simple Neural Network You can clone and fork the vectorized implementations of the 3 layer Neural Network for Python, R and Octave from Github at

DeepLearningFromFirstPrinciples

[(https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/m](https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/master/Chap2-SimpleNeuralNetwork)aster/Chap2-

[SimpleNeuralNetwork)](https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/master/Chap2-SimpleNeuralNetwork)

![Image 42](index-39_1.jpg)

![Image 43](index-39_2.jpg)

![Image 44](index-39_3.jpg)

![Image 45](index-39_4.jpg)

**2.The 3 layer Neural Network**

A simple representation of a 3 layer Neural Network (NN) with 1

hidden layer is shown below .

In the above Neural Network, there are two input features at the input layer, three hidden units at the hidden layer and one output layer as it deals with binary classification. The activation unit at the hidden layer can be a tanh, sigmoid, relu etc. At the output layer, the activation is a sigmoid to handle binary classification

\# Superscript indicates layer ‘1’

![Image 46](index-40_1.jpg)

![Image 47](index-40_2.jpg)

![Image 48](index-40_3.jpg)

![Image 49](index-40_4.jpg)

![Image 50](index-40_5.jpg)

![Image 51](index-40_6.jpg)

![Image 52](index-40_7.jpg)

![Image 53](index-40_8.jpg)

![Image 54](index-40_9.jpg)

![Image 55](index-40_10.jpg)

![Image 56](index-40_11.jpg)

![Image 57](index-40_12.jpg)

![Image 58](index-40_13.jpg)

![Image 59](index-40_14.jpg)

![Image 60](index-40_15.jpg)

![Image 61](index-40_16.jpg)

![Image 62](index-40_17.jpg)

Also

\# Superscript indicates layer ‘2’

Hence

And

Similarly

and

These equations can be written as

**I)** Some important results (a memory refresher!)

and

\-(a) and

and

Using (a) we can shown that

and

(b)

Now

![Image 63](index-41_1.jpg)

![Image 64](index-41_2.jpg)

![Image 65](index-41_3.jpg)

![Image 66](index-41_4.jpg)

![Image 67](index-41_5.jpg)

![Image 68](index-41_6.jpg)

![Image 69](index-41_7.jpg)

![Image 70](index-41_8.jpg)

![Image 71](index-41_9.jpg)

![Image 72](index-41_10.jpg)

![Image 73](index-41_11.jpg)

![Image 74](index-41_12.jpg)

![Image 75](index-41_13.jpg)

![Image 76](index-41_14.jpg)

![Image 77](index-41_15.jpg)

![Image 78](index-41_16.jpg)

![Image 79](index-41_17.jpg)

![Image 80](index-41_18.jpg)

![Image 81](index-41_19.jpg)

![Image 82](index-41_20.jpg)

\-(c)

Since

and using (c) we get

Using the values of the derivatives of sinhx and coshx from (b) above we get

Since

\-(d)

**II) Derivatives**

The log loss is given below

Since

therefore

see

equation (2) Chapter 1

Therefore

and (e)

(f) and

and

from (d)

(g)

(h)

**III) Back propagation**

Using the derivatives from II) we can derive the following results using Chain Rule

(i)

![Image 83](index-42_1.jpg)

![Image 84](index-42_2.jpg)

![Image 85](index-42_3.jpg)

![Image 86](index-42_4.jpg)

![Image 87](index-42_5.jpg)

![Image 88](index-42_6.jpg)

![Image 89](index-42_7.jpg)

![Image 90](index-42_8.jpg)

![Image 91](index-42_9.jpg)

![Image 92](index-42_10.jpg)

![Image 93](index-42_11.jpg)

![Image 94](index-42_12.jpg)

Using the results of (i) and (e ) we get

\-(j)

\-(k)

And

Simplifying we get

\-(l) and

\-(m)

**IV) Gradient Descent**

The key computations in the backward cycle are based on the gradient computed above in equations (h), (i),(j) and (k)

The weights and biases (W1,b1,W2,b2) are updated for each iteration thus minimizing the loss/cost.

These derivations can be represented pictorially using the computation graph (from the book Deep Learning

[(http://www.deeplearningbook.org/)](http://www.deeplearningbook.org/) by Ian Goodfellow, Joshua Bengio and Aaron Courville)

![Image 95](index-43_1.jpg)

**1.Manually create a data set that is not**

**linearly separable**

Initially I create a dataset with 2 classes which has around 9 clusters that cannot be separated by linear boundaries. **Note**: *This data set is* *also saved as data.csv and is used for the R and Octave Neural* *networks to see how they perform on the same dataset.*

import numpy as np

import matplotlib.pyplot as plt

import matplotlib.colors

import sklearn.linear\_model

from sklearn.model\_selection import train\_test\_split

from sklearn.datasets import make\_classification, make\_blobs

from matplotlib.colors import ListedColormap

import sklearn

import sklearn.datasets

colors=\['black','gold'\]

cmap = matplotlib.colors.ListedColormap(colors)

X, y = make\_blobs(n\_samples = 400, n\_features = 2, centers = 7, cluster\_std = 1.3, random\_state = 4)

#Create 2 classes

y=y.reshape(400,1)

y = y % 2

#Plot the figure

plt.figure()

plt.title('Non-linearly separable classes')

plt.scatter(X\[:,0\], X\[:,1\], c=y,

marker= 'o', s=50,cmap=cmap)

plt.savefig('fig1.png', bbox\_inches='tight')

![Image 96](index-45_1.jpg)

**2.Logistic Regression**

When classification with logistic regression is performed on the above data set, and the decision boundary is plotted it can be seen that logistic regression performs quite poorly

import numpy as np

import matplotlib.pyplot as plt

import matplotlib.colors

import sklearn.linear\_model

from sklearn.model\_selection import train\_test\_split

from sklearn.datasets import make\_classification, make\_blobs

from matplotlib.colors import ListedColormap

import sklearn

import sklearn.datasets

#from DLfunctions import plot\_decision\_boundary

execfile("./DLfunctions.py") # Since import does not work in Rmd!!!

colors=\['black','gold'\]

cmap = matplotlib.colors.ListedColormap(colors)

X, y = make\_blobs(n\_samples = 400, n\_features = 2, centers = 7, cluster\_std = 1.3, random\_state = 4)

#Create 2 classes

y=y.reshape(400,1)

y = y % 2

\# Train the logistic regression classifier

clf = sklearn.linear\_model.LogisticRegressionCV();

clf.fit(X, y);

\# Plot the decision boundary for logistic regression

plot\_decision\_boundary\_n(lambda x: clf.predict(x), X.T, y.T,"fig2.png")

![Image 97](index-47_1.jpg)

 

**5.1 The 3 layer Neural Network in Python (vectorized)**

The vectorized implementation is included below. Note that in the case of Python a learning rate of 0.5 and 3 hidden units performs very well.

\## Random data set with 9 clusters

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import sklearn.linear\_model

import pandas as pd

from sklearn.datasets import make\_classification, make\_blobs

execfile("./DLfunctions.py") # Since import does not work in Rmd!!!

X1, Y1 = make\_blobs(n\_samples = 400, n\_features = 2, centers = 9, cluster\_std = 1.3, random\_state = 4)

#Create 2 classes

Y1=Y1.reshape(400,1)

Y1 = Y1 % 2

X2=X1.T

Y2=Y1.T

\# Execute the 3 layer Neural Network

parameters,costs = computeNN(X2, Y2, numHidden = 4, learningRate=0.5, numIterations = 10000)

#Plot the decision boundary

plot\_decision\_boundary(lambda x: predict(parameters, x.T), X2, Y2,str(4),str(0.5),"fig3.png")

\## Cost after iteration 0: 0.692669

\## Cost after iteration 1000: 0.246650

\## Cost after iteration 2000: 0.227801

\## Cost after iteration 3000: 0.226809

![Image 98](index-49_1.jpg)

\## Cost after iteration 4000: 0.226518

\## Cost after iteration 5000: 0.226331

\## Cost after iteration 6000: 0.226194

\## Cost after iteration 7000: 0.226085

\## Cost after iteration 8000: 0.225994

\## Cost after iteration 9000: 0.225915

It can be seen the the 3 layer Neural Network with a single hidden layer is able to create the non-linear boundary separating the classes **5.2 The 3 layer Neural Network in R (vectorized)**

This the dataset created by Python was saved as data.csv. The R code reads this data to see how R performs on the same dataset. The vectorized implementation of a Neural Network in R, was just a little more interesting as R does not have a similar package like ‘numpy’.

While numpy handles broadcasting implicitly, in R, I had to use the

‘sweep’ command to broadcast. The implementation is included

below. Note that since the initialization with random weights is slightly different, R performs best with a learning rate of 0.1 and with 6 hidden units

source("DLfunctions2\_1.R")

z <- as.matrix(read.csv("data.csv",header=FALSE)) #

x <- z\[,1:2\]

y <- z\[,3\]

x1 <- t(x)

y1 <- t(y)

\# Execute the 3 layer Neural Network

nn <-computeNN(x1, y1, 6, learningRate=0.1,numIterations=10000) # Good

\## \[1\] 0.7075341

\## \[1\] 0.2606695

\## \[1\] 0.2198039

\## \[1\] 0.2091238

\## \[1\] 0.211146

\## \[1\] 0.2108461

\## \[1\] 0.2105351

\## \[1\] 0.210211

\## \[1\] 0.2099104

\## \[1\] 0.2096437

\## \[1\] 0.209409

![Image 99](index-51_1.jpg)

![Image 100](index-51_2.jpg)

plotDecisionBoundary(z,nn,6,0.1)

R is also able to create the non-linear boundary.

**5.3 The 3 layer Neural Network in Octave (vectorized)**

This uses the same dataset (data.csv) that was generated using Python code.

source("DL-function2.m")

\# Read the data

data=csvread("data.csv");

X=data(:,1:2);

Y=data(:,3);

\# Make sure that the model parameters are correct. Take the transpose of X & Y

\# Execute the 3 layer Neural Network and plot decision boundary

\[W1,b1,W2,b2,costs\]= computeNN(X', Y',4, learningRate=0.5, numIterations =

10000);

![Image 101](index-53_1.jpg)

The above plot shows the non-linear boundary created by Octave.

**6.1a Performance for different learning rates (Python)**

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import sklearn.linear\_model

import pandas as pd

from sklearn.datasets import make\_classification, make\_blobs

execfile("./DLfunctions.py") # Since import does not work in Rmd!!!

\# Create data

X1, Y1 = make\_blobs(n\_samples = 400, n\_features = 2, centers = 9, cluster\_std = 1.3, random\_state = 4)

#Create 2 classes

Y1=Y1.reshape(400,1)

Y1 = Y1 % 2

X2=X1.T

Y2=Y1.T

\# Create a list of learning rates

learningRate=\[0.5,1.2,3.0\]

df=pd.DataFrame()

#Compute costs for each learning rate

for lr in learningRate:

\# Execute the 3 layer Neural Network

parameters,costs = computeNN(X2, Y2, numHidden = 4, learningRate=lr, numIterations = 10000)

print(costs)

df1=pd.DataFrame(costs)

df=pd.concat(\[df,df1\],axis=1)

#Set the iterations

iterations=\[0,1000,2000,3000,4000,5000,6000,7000,8000,9000\]

#Create data frame

#Set index

df1=df.set\_index(\[iterations\])

df1.columns=\[0.5,1.2,3.0\]

\# Plot cost vs number of iterations for different learning rates fig=df1.plot()

fig=plt.title("Cost vs No of Iterations for different learning rates") plt.savefig('fig4.png', bbox\_inches='tight')

![Image 102](index-55_1.jpg)

**6.1b Performance for different hidden units (Python)**

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import sklearn.linear\_model

import pandas as pd

from sklearn.datasets import make\_classification, make\_blobs

execfile("./DLfunctions.py") # Since import does not work in Rmd!!!

#Create data set

X1, Y1 = make\_blobs(n\_samples = 400, n\_features = 2, centers = 9, cluster\_std = 1.3, random\_state = 4)

#Create 2 classes

Y1=Y1.reshape(400,1)

Y1 = Y1 % 2

X2=X1.T

Y2=Y1.T

\# Make a list of hidden unis

numHidden=\[3,5,7\]

df=pd.DataFrame()

#Compute costs for different hidden units

for numHid in numHidden:

\# Execute the 3 layer Neural Network

parameters,costs = computeNN(X2, Y2, numHidden = numHid,

learningRate=1.2, numIterations = 10000)

print(costs)

df1=pd.DataFrame(costs)

df=pd.concat(\[df,df1\],axis=1)

#Set the iterations

iterations=\[0,1000,2000,3000,4000,5000,6000,7000,8000,9000\]

#Set index

df1=df.set\_index(\[iterations\])

#Plot the cost vs iterations for different number of hidden units df1.columns=\[3,5,7\]

#Plot

fig=df1.plot()

fig=plt.title("Cost vs No of Iterations for different no of hidden units") plt.savefig('fig5.png', bbox\_inches='tight')

![Image 103](index-57_1.jpg)

**6.2a Performance for different learning rates (R)**

source("DLfunctions2\_1.R")

\# Read data

z <- as.matrix(read.csv("data.csv",header=FALSE)) #

x <- z\[,1:2\]

y <- z\[,3\]

x1 <- t(x)

y1 <- t(y)

#Loop through learning rates and compute costs

learningRate <-c(0.1,1.2,3.0)

df <- NULL

for(i in seq\_along(learningRate)){

\# Execute the 3 layer Neural Network

nn <- computeNN(x1, y1, 6,

![Image 104](index-58_1.jpg)

learningRate=learningRate\[i\],numIterations=10000)

cost <- nn$costs

df <- cbind(df,cost)

}

#Create dataframe

df <- data.frame(df)

iterations=seq(0,10000,by=1000)

df <- cbind(iterations,df)

names(df) <- c("iterations","0.5","1.2","3.0")

\# Reshape the data

library(reshape2)

df1 <- melt(df,id="iterations") # Melt the data

#Plot the cost vs iterations for different learning rates

ggplot(df1) + geom\_line(aes(x=iterations,y=value,colour=variable),size=1) +

xlab("Iterations") +

ylab('Cost') + ggtitle("Cost vs No iterations for different learning rates")

![Image 105](index-59_1.jpg)

**6.2b Performance for different hidden units (R)**

source("DLfunctions2\_1.R")

\# Loop through number of hidden units

numHidden <-c(4,6,9)

df <- NULL

for(i in seq\_along(numHidden)){

\# Execute the 3 layer Neural Network

nn <- computeNN(x1, y1, numHidden\[i\],

learningRate=0.1,numIterations=10000)

![Image 106](index-60_1.jpg)

cost <- nn$costs

df <- cbind(df,cost)

}

#Create a dataframe

df <- data.frame(df)

iterations=seq(0,10000,by=1000)

df <- cbind(iterations,df)

names(df) <- c("iterations","4","6","9")

#Reshape the dataframe

library(reshape2)

\# Melt

df1 <- melt(df,id="iterations")

\# Plot cost vs iterations for different number of hidden units ggplot(df1) + geom\_line(aes(x=iterations,y=value,colour=variable),size=1) +

xlab("Iterations") +

ylab('Cost') + ggtitle("Cost vs No iterations for different number of hidden units")

![Image 107](index-61_1.jpg)

**6.3a Performance of the Neural Network for different**

**learning rates (Octave)**

source("DL-function2.m")

#Plot cost vs iterations for different learning rates

plotLRCostVsIterations()

print -djph figa.jpg

![Image 108](index-63_1.jpg)

**6.3b Performance of the Neural Network for different**

**number of hidden units (Octave)**

source("DL-function2.m")

#Plot cost vs Iterations for different number of hidden units plotHiddenCostVsIterations()

print -djph figa.jpg

![Image 109](index-64_1.jpg)

**7.Turning the heat on the Neural**

**Network**

In this 2nd part, I create a central region of positives and an outside region as negatives. The points are generated using the equation of a circle (x – a)2 + (y -b)2 = R2 . How does the 3-layer Neural Network perform on this? Here’s a look! **Note**: *R and Octave Neural Network* *constructions also use the same data set.*

**8.Manually creating a circular central**

**region**

import numpy as np

import matplotlib.pyplot as plt

import matplotlib.colors

import sklearn.linear\_model

from sklearn.model\_selection import train\_test\_split

from sklearn.datasets import make\_classification, make\_blobs

from matplotlib.colors import ListedColormap

import sklearn

import sklearn.datasets

colors=\['black','gold'\]

cmap = matplotlib.colors.ListedColormap(colors)

x1=np.random.uniform(0,10,800).reshape(800,1)

x2=np.random.uniform(0,10,800).reshape(800,1)

X=np.append(x1,x2,axis=1)

X.shape

\# Create the data set with (x-a)^2 + (y-b)^2 = R^2

\# Create a subset of values where squared is <0,4. Perform ravel() to flatten this vector

a=(np.power(X\[:,0\]-5,2) + np.power(X\[:,1\]-5,2) <= 6).ravel() Y=a.reshape(800,1)

cmap = matplotlib.colors.ListedColormap(colors)

#Plot the dataset

plt.figure()

plt.title('Non-linearly separable classes')

plt.scatter(X\[:,0\], X\[:,1\], c=Y,

marker= 'o', s=15,cmap=cmap)

plt.savefig('fig6.png', bbox\_inches='tight')

![Image 110](index-68_1.jpg)

**8.1a Decision boundary with hidden units=4 and**

**learning rate = 2.2 (Python)**

With the above hyper-parameters, the decision boundary is triangular import numpy as np

import matplotlib.pyplot as plt

import matplotlib.colors

import sklearn.linear\_model

execfile("./DLfunctions.py")

x1=np.random.uniform(0,10,800).reshape(800,1)

x2=np.random.uniform(0,10,800).reshape(800,1)

X=np.append(x1,x2,axis=1)

X.shape

\# Create a subset of values where squared is <0,4. Perform ravel() to flatten this

vector

a=(np.power(X\[:,0\]-5,2) + np.power(X\[:,1\]-5,2) <= 6).ravel() Y=a.reshape(800,1)

X2=X.T

Y2=Y.T

\# Execute the 3 layer Neural network

parameters,costs = computeNN(X2, Y2, numHidden = 4, learningRate=2.2, numIterations = 10000)

#Plot the decision boundary

plot\_decision\_boundary(lambda x: predict(parameters, x.T), X2, Y2,str(4),str(2.2),"fig7.png")

\## Cost after iteration 0: 0.692836

\## Cost after iteration 1000: 0.331052

\## Cost after iteration 2000: 0.326428

\## Cost after iteration 3000: 0.474887

\## Cost after iteration 4000: 0.247989

\## Cost after iteration 5000: 0.218009

\## Cost after iteration 6000: 0.201034

\## Cost after iteration 7000: 0.197030

\## Cost after iteration 8000: 0.193507

\## Cost after iteration 9000: 0.191949

![Image 111](index-70_1.jpg)

**8.1b Decision boundary with hidden units=12 and**

**learning rate = 2.2 (Python)**

Increasing the number of hidden units makes the decision boundary much more circular

import numpy as np

import matplotlib.pyplot as plt

import matplotlib.colors

import sklearn.linear\_model

execfile("./DLfunctions.py")

x1=np.random.uniform(0,10,800).reshape(800,1)

x2=np.random.uniform(0,10,800).reshape(800,1)

X=np.append(x1,x2,axis=1)

X.shape

\# Create a subset of values where squared is <0,4. Perform ravel() to flatten this vector

a=(np.power(X\[:,0\]-5,2) + np.power(X\[:,1\]-5,2) <= 6).ravel() Y=a.reshape(800,1)

X2=X.T

Y2=Y.T

\# Execute the 3 layer Neural network

parameters,costs = computeNN(X2, Y2, numHidden = 12, learningRate=2.2, numIterations = 10000)

#Plot the decision boundary

plot\_decision\_boundary(lambda x: predict(parameters, x.T), X2, Y2,str(12),str(2.2),"fig8.png")

\## Cost after iteration 0: 0.693291

\## Cost after iteration 1000: 0.383318

\## Cost after iteration 2000: 0.298807

\## Cost after iteration 3000: 0.251735

\## Cost after iteration 4000: 0.177843

\## Cost after iteration 5000: 0.130414

\## Cost after iteration 6000: 0.152400

\## Cost after iteration 7000: 0.065359

\## Cost after iteration 8000: 0.050921

\## Cost after iteration 9000: 0.039719

![Image 112](index-72_1.jpg)

**8.2a Decision boundary with hidden units=9 and**

**learning rate = 0.5 (R)**

When the number of hidden units is 6 and the learning rate is 0.5, is also a triangular shape in R

source("DLfunctions2\_1.R")

z <- as.matrix(read.csv("data1.csv",header=FALSE)) # N

x <- z\[,1:2\]

y <- z\[,3\]

x1 <- t(x)

y1 <- t(y)

\# Execute the 3 layer Neural network

nn <-computeNN(x1, y1, 9, learningRate=0.5,numIterations=10000) #

Triangular

![Image 113](index-73_1.jpg)

\## \[1\] 0.8398838

\## \[1\] 0.3303621

\## \[1\] 0.3127731

\## \[1\] 0.3012791

\## \[1\] 0.3305543

\## \[1\] 0.3303964

\## \[1\] 0.2334615

\## \[1\] 0.1920771

\## \[1\] 0.2341225

\## \[1\] 0.2188118

\## \[1\] 0.2082687

#Plot the decision boundary

plotDecisionBoundary(z,nn,6,0.1)

![Image 114](index-74_1.jpg)

**8.2b Decision boundary with hidden units=8 and**

**learning rate = 0.1 (R)**

With 8 hidden units the decision boundary is quite circular.

source("DLfunctions2\_1.R")

z <- as.matrix(read.csv("data1.csv",header=FALSE)) # N

x <- z\[,1:2\]

y <- z\[,3\]

x1 <- t(x)

![Image 115](index-75_1.jpg)

y1 <- t(y)

\# Execute the 3 layer Neural network

nn <-computeNN(x1, y1, 8, learningRate=0.1,numIterations=10000) #

Hemisphere

\## \[1\] 0.7273279

\## \[1\] 0.3169335

\## \[1\] 0.2378464

\## \[1\] 0.1688635

\## \[1\] 0.1368466

\## \[1\] 0.120664

\## \[1\] 0.111211

\## \[1\] 0.1043362

\## \[1\] 0.09800573

\## \[1\] 0.09126161

\## \[1\] 0.0840379

#Plot the decision boundary

plotDecisionBoundary(z,nn,8,0.1)

**8.3a Decision boundary with hidden units=12 and** **learning rate = 1.5 (Octave)**

source("DL-function2.m")

\# Read the data

data=csvread("data1.csv");

X=data(:,1:2);

Y=data(:,3);

\# Make sure that the model parameters are correct. Take the transpose of X & Y

\# Execute the 3 layer Neural network

\[W1,b1,W2,b2,costs\]= computeNN(X', Y',12, learningRate=1.5, numIterations =

10000);

#Plot the decision boundary

plotDecisionBoundary(data, W1,b1,W2,b2)

print -djpg fige.jpg

![Image 116](index-77_1.jpg)

**9.** Conclusion

This chapter implemented a 3-layer Neural Network to create non-linear boundaries while performing classification. Clearly, the Neural Network performs very well when the number of hidden units and learning rate are varied.

**3.**

**Building a L- Layer Deep**

**Learning Network**

*“Once upon a time, I, Chuang Tzu, dreamt I was a butterfly, fluttering* *hither and thither, to all intents and purposes a butterfly. I was* *conscious only of following my fancies as a butterfly, and was* *unconscious of my individuality as a man. Suddenly, I awoke, and* *there I lay, myself again. Now I do not know whether I was then a man* *dreaming I was a butterfly, or whether I am now a butterfly dreaming* *that I am a man.”*

from The Brain: The Story of you – David Eagleman

*“Thought is a great big vector of neural activity”*

Prof Geoffrey Hinton

**1.Introduction**

This is the third chapter in my series on Deep Learning from first principles in Python, R and Octave. In this third chapter, I implement a multi-layer, Deep Learning (DL) network of arbitrary depth (any number of hidden layers), and arbitrary height (any number of activation units in each hidden layer). The implementation in the 3rd part is for an L-layer Deep Network, but without any regularization, early stopping, momentum or learning rate adaptation techniques.

However even this barebones multi-layer DL, is a handful and has enough hyper-parameters to fine-tune and adjust.

The implementation of the vectorized L-layer Deep Learning network in Python, R and Octave is quite challenging, as we need to keep track of the indices, layer number and matrix dimensions. Some challenges because of the differences in the languages

1\. Python and Octave allow multiple return values to be unpacked in a single statement. With R, unpacking multiple return values from a list, requires the entire to be list returned, and then unpacked separately. I did see that there is a package gsubfn

[(https://stackoverflow.com/questions/1826519/how-to-assign-from-a-](https://stackoverflow.com/questions/1826519/how-to-assign-from-a-function-which-returns-more-than-one-value)

[function-which-returns-more-than-one-value), which does this.](https://stackoverflow.com/questions/1826519/how-to-assign-from-a-function-which-returns-more-than-one-value)

2\. Python and R can save and return dissimilar elements from functions using dictionaries or lists respectively. However, there is no real equivalent in Octave. The closest I got to this functionality in Octave, was the ‘cell array’. But, the cell array can be accessed only by the index, and not with the key as in a Python dictionary or R list.

This makes things just a bit more difficult in Octave.

3\. Python and Octave include implicit broadcasting. In R,

broadcasting is not implicit, but R has a nifty function, the sweep(), with which we can broadcast either by columns or by rows

4\. The closest equivalent of Python’s dictionary, or R’s list, in Octave is the cell array. However I had to manage separate cell arrays for

weights and biases and during gradient descent and separate gradients dW and dB

5\. In Python, the rank-1 numpy arrays can be annoying at times. This issue is not present in R and Octave.

The current vectorized implementation supports the relu, sigmoid and tanh activation functions.

While testing with different hyper-parameters namely i) the number of hidden layers, ii) the number of activation units in each layer, iii) the activation function and iv) the number iterations, I found the L-layer Deep Learning Network to be very sensitive to these hyperparameters. It is not easy to tune the parameters. Adding more hidden layers, or more units per layer, does not help always, and sometimes results in gradient descent getting stuck in some local minima. It does take a fair amount of trial and error and very close observation on how the Deep Learning network performs for logical changes. We then can zero in on the most the optimal solution. A much more detailed approach for tuning hyper-paramaters is discussed in chapter 8. The Python,R and Octave functions used in this chapter are implemented in Appendix 3 - Building a L- Layer Deep Learning Network

Feel free to download/fork my code from

Github DeepLearningFromFirstPrinciples

(https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/master/Chap3-L-LayerDeepLearningNetwork) and play around with the hyper-

parameters for your own problems.

![Image 117](index-82_1.jpg)

![Image 118](index-82_2.jpg)

![Image 119](index-82_3.jpg)

![Image 120](index-82_4.jpg)

![Image 121](index-82_5.jpg)

![Image 122](index-82_6.jpg)

![Image 123](index-82_7.jpg)

![Image 124](index-82_8.jpg)

![Image 125](index-82_9.jpg)

![Image 126](index-82_10.jpg)

![Image 127](index-82_11.jpg)

![Image 128](index-82_12.jpg)

**2.Derivation of a Multi Layer Deep**

**Learning Network**

Let’s take a simple 3 layer Neural network with 3 hidden layers and an output layer

In the forward propagation cycle the equations are

and

and

and

The loss function is given by

and

For a binary classification, the output activation function is the sigmoid function given by

. Hence

see equation (2) in chapter 1

see equation (f) in

chapter 1

![Image 129](index-83_1.jpg)

![Image 130](index-83_2.jpg)

![Image 131](index-83_3.jpg)

![Image 132](index-83_4.jpg)

![Image 133](index-83_5.jpg)

![Image 134](index-83_6.jpg)

![Image 135](index-83_7.jpg)

![Image 136](index-83_8.jpg)

![Image 137](index-83_9.jpg)

![Image 138](index-83_10.jpg)

![Image 139](index-83_11.jpg)

![Image 140](index-83_12.jpg)

![Image 141](index-83_13.jpg)

![Image 142](index-83_14.jpg)

![Image 143](index-83_15.jpg)

![Image 144](index-83_16.jpg)

![Image 145](index-83_17.jpg)

and since

because

\-(1a)

and

\-

(1b)

\-(1c)

since

and

\-(1d)

because

Also

– (2a)

–

(2b)

– (2c)

– (2d)

Inspecting the above equations (1a – 1d & 2a-2d), we can discern a pattern in these equations and we can write the equations for any layer

‘l’ as

and

The equations for the backward propagation have the general form

![Image 146](index-84_1.jpg)

![Image 147](index-84_2.jpg)

![Image 148](index-84_3.jpg)

![Image 149](index-84_4.jpg)

![Image 150](index-84_5.jpg)

![Image 151](index-84_6.jpg)

![Image 152](index-84_7.jpg)

![Image 153](index-84_8.jpg)

![Image 154](index-84_9.jpg)

**Other important results**

The derivatives of the activation functions in the implemented Deep Learning network

g(z) = sigmoid(z) =

\= a g’(z) = a(1-a) – See equation (2)

chapter 1

g(z) = tanh(z) = a g’(z) =

See equation (d) chapter 2

g(z) = relu(z) = z when z>0 and 0 when z 0 and 0 when z <= 0

The implementation of the multi-layer vectorized Deep Learning Network for Python, R and Octave is included below. For all these implementations, initially I create the size and configuration of the Deep Learning network with the layer dimensions. So, for example layersDimension Vector ‘V’ of length L indicating ‘L’ layers where V (in Python) =

…

V (in R) =

…

V (in Octave) = \[

…

In all of these implementations, the first element is the number of input features to the Deep Learning network and the last element is always a ‘sigmoid’ activation function since all the problems deal with binary classification.

The number of elements between the first and the last element are the number of hidden layers and the magnitude of each is the number of activation units in each hidden layer, which is specified while actually executing the Deep Learning network using the function L\_Layer\_DeepModel(), in all the implementations Python, R and Octave

**2.1a Classification with Multi-layer**

**Deep Learning Network – Relu**

**activation(Python)**

In the code below a 4-layer Neural Network is trained to generate a non-linear boundary between the classes. In the code below the ‘Relu’

Activation function is used. The number of activation units in each layer is 9. The cost vs iterations is plotted. In addition to the decision boundary. Further, the accuracy, precision, recall and F1 score are also computed

import os

import numpy as np

import matplotlib.pyplot as plt

import matplotlib.colors

import sklearn.linear\_model

from sklearn.model\_selection import train\_test\_split

from sklearn.datasets import make\_classification, make\_blobs

from matplotlib.colors import ListedColormap

import sklearn

import sklearn.datasets

#from DLfunctions import plot\_decision\_boundary

execfile("./DLfunctions34.py") #

\# Create clusters of 2 classes

X1, Y1 = make\_blobs(n\_samples = 400, n\_features = 2, centers = 9, cluster\_std = 1.3, random\_state = 4)

#Create 2 classes

Y1=Y1.reshape(400,1)

Y1 = Y1 % 2

X2=X1.T

Y2=Y1.T

\# Set the dimensions of DL Network

\# Below we have

\# 2 - 2 input features

\# 9,9 - 2 hidden layers with 9 activation units per layer and

\# 1 - 1 sigmoid activation unit in the output layer as this is a binary classification

\# The activation in the hidden layer is the 'relu' specified in L\_Layer\_DeepModel

layersDimensions = \[2, 9, 9,1\] # 4-layer model

\# Execute the L-layer Deep Learning network

\# Hidden layer activation unit – relu

\# Learning rate – 0.3

parameters = L\_Layer\_DeepModel(X2, Y2,

layersDimensions,hiddenActivationFunc='relu', learning\_rate =

0.3,num\_iterations = 2500, fig="fig1.png")

#Plot the decision boundary

plot\_decision\_boundary(lambda x: predict(parameters, x.T),

X2,Y2,str(0.3),"fig2.png")

\# Compute the confusion matrix

yhat = predict(parameters,X2)

from sklearn.metrics import confusion\_matrix

a=confusion\_matrix(Y2.T,yhat.T)

#Print the output

from sklearn.metrics import accuracy\_score, precision\_score, recall\_score, f1\_score

print('Accuracy: {:.2f}'.format(accuracy\_score(Y2.T, yhat.T))) print('Precision: {:.2f}'.format(precision\_score(Y2.T, yhat.T))) print('Recall: {:.2f}'.format(recall\_score(Y2.T, yhat.T)))

print('F1: {:.2f}'.format(f1\_score(Y2.T, yhat.T)))

\## Accuracy: 0.90

\## Precision: 0.91

\## Recall: 0.87

\## F1: 0.89

![Image 155](index-87_1.jpg)

![Image 156](index-88_1.jpg)

**2.1b Classification with Multi-layer**

**Deep Learning Network – Relu**

**activation(R)**

In the code below, binary classification is performed on the same dataset (data.csv) as above using the Relu activation function. The DL

network is same as above

library(ggplot2)

\# Read the data

z <- as.matrix(read.csv("data.csv",header=FALSE)) x <- z\[,1:2\]

y <- z\[,3\]

X1 <- t(x)

Y1 <- t(y)

\# Set the dimensions of the Deep Learning network

\# 2 - No of input features

\# 9,9 - 2 hidden layers with 9 activation units

\# 1 - 1 sigmoid activation unit at output layer

layersDimensions = c(2, 9, 9,1)

\# Execute the L-layer Deep Learning Neural Network

\# Hidden layer activation unit – relu

\# Learning rate – 0.3

retvals = L\_Layer\_DeepModel(X1, Y1, layersDimensions,

hiddenActivationFunc='relu',

learningRate = 0.3,

numIterations = 5000,

print\_cost = True)

library(ggplot2)

source("DLfunctions33.R")

![Image 157](index-90_1.jpg)

\# Get the computed costs

costs <- retvals\[\['costs'\]\]

\# Create a sequence of iterations

numIterations=5000

iterations <- seq(0,numIterations,by=1000)

df <-data.frame(iterations,costs)

\# Plot the Costs vs number of iterations

ggplot(df,aes(x=iterations,y=costs)) + geom\_point() +geom\_line(color="blue")

\+ xlab('No of iterations') + ylab('Cost') + ggtitle("Cost vs No of iterations")

![Image 158](index-91_1.jpg)

![Image 159](index-91_2.jpg)

\# Plot the decision boundary

plotDecisionBoundary(z,retvals,hiddenActivationFunc="relu",0.3)

![Image 160](index-92_1.jpg)

library(caret)

\# Predict the output for the data values

yhat <-predict(retvals$parameters,X1,hiddenActivationFunc="relu") yhat\[yhat==FALSE\]=0

yhat\[yhat==TRUE\]=1

\# Compute the confusion matrix

confusionMatrix(yhat,Y1)

\## Confusion Matrix and Statistics

##

\## Reference

\## Prediction 0 1

\## 0 201 10

\## 1 21 168

##

\## Accuracy : 0.9225

\## 95% CI : (0.8918, 0.9467)

\## No Information Rate : 0.555

\## P-Value \[Acc > NIR\] : < 2e-16

##

\## Kappa : 0.8441

\## Mcnemar's Test P-Value : 0.07249

##

\## Sensitivity : 0.9054

\## Specificity : 0.9438

\## Pos Pred Value : 0.9526

\## Neg Pred Value : 0.8889

\## Prevalence : 0.5550

\## Detection Rate : 0.5025

\## Detection Prevalence : 0.5275

\## Balanced Accuracy : 0.9246

##

\## 'Positive' Class : 0

##

**2.1c Classification with Multi-layer**

**Deep Learning Network – Relu**

**activation(Octave)**

Included below is the code for performing classification. Incidentally, Octave does not seem to have implemented the confusion matrix.

\# Read the data

data=csvread("data.csv");

X=data(:,1:2);

Y=data(:,3);

\# Set layer dimensions

\# 2 – 2 input features

\# 9 7 – 2 hidden layers with 9 and 7 hidden units

\# 1 – 1 sigmoid activation unit at output layer

layersDimensions = \[2 9 7 1\]

\# Execute the L-Layer Deep Network

\# Hidden unit – relu

#learning rate – 0.1

\[weights biases costs\]=L\_Layer\_DeepModel(X', Y', layersDimensions, hiddenActivationFunc='relu',

learningRate = 0.1,

numIterations = 10000);

#Plot cost vs iterations

plotCostVsIterations(10000,costs);

#Plot the decision boundary

plotDecisionBoundary(data,weights, biases,hiddenActivationFunc="tanh")

![Image 161](index-95_1.jpg)

![Image 162](index-96_1.jpg)

**2.2a Classification with Multi-layer**

**Deep Learning Network – Tanh**

**activation(Python)**

The code below uses the tanh activation function to perform the same classification. I found the Tanh activation required a simpler Neural Network of 3 layers.

\# Tanh activation

import os

import numpy as np

import matplotlib.pyplot as plt

import matplotlib.colors

import sklearn.linear\_model

from sklearn.model\_selection import train\_test\_split

from sklearn.datasets import make\_classification, make\_blobs

from matplotlib.colors import ListedColormap

import sklearn

import sklearn.datasets

execfile("./DLfunctions34.py")

\# Create the dataset

X1, Y1 = make\_blobs(n\_samples = 400, n\_features = 2, centers = 9, cluster\_std = 1.3, random\_state = 4)

#Create 2 classes

Y1=Y1.reshape(400,1)

Y1 = Y1 % 2

X2=X1.T

Y2=Y1.T

\# Set the dimensions of the Neural Network

\# 2 – input featues

\# 4 – 1 hidden layer with 4 units

\# 1 – 1 sigmoid activation unit at output layer layersDimensions = \[2, 4, 1\] # 3-layer model

\# Execute the L-layer Deep Learning network

\# hidden layer activation function – tanh

\# learning rate – 0.5

parameters = L\_Layer\_DeepModel(X2, Y2, layersDimensions,

hiddenActivationFunc='tanh', learning\_rate = .5,num\_iterations =

2500,fig="fig3.png")

#Plot the decision boundary

plot\_decision\_boundary(lambda x: predict(parameters, x.T),

X2,Y2,str(0.5),"fig4.png")

![Image 163](index-99_1.jpg)

![Image 164](index-100_1.jpg)

**2.2b Classification with Multi-layer**

**Deep Learning Network – Tanh**

**activation(R)**

R performs better with a Tanh activation than the Relu as can be seen below

#Set the dimensions of the Neural Network

library(ggplot2)

\# Read the data

z <- as.matrix(read.csv("data.csv",header=FALSE)) x <- z\[,1:2\]

y <- z\[,3\]

![Image 165](index-101_1.jpg)

X1 <- t(x)

Y1 <- t(y)

\# Set layer dimensions

\# 2 – 2 inputr features

\# 9, 9 – 2 hidden layers with 9 activation units

\# 1 – 1 sigmoid output activation unit

layersDimensions = c(2, 9, 9,1)

\# Execute the L-layer Deep Model

\# Hidden layer activation function – tanh

\# learning rate – 0.3

retvals = L\_Layer\_DeepModel(X1, Y1, layersDimensions,

hiddenActivationFunc='tanh',

learningRate = 0.3,

numIterations = 5000,

print\_cost = True)

\# Get the costs

costs <- retvals\[\['costs'\]\]

\# Set iterations

iterations <- seq(0,numIterations,by=1000)

df <-data.frame(iterations,costs)

\# Plot Cost vs number of iterations

ggplot(df,aes(x=iterations,y=costs)) + geom\_point() +geom\_line(color="blue")

\+ xlab('No of iterations') + ylab('Cost') + ggtitle("Cost vs No of iterations")

![Image 166](index-102_1.jpg)

![Image 167](index-102_2.jpg)

#Plot the decision boundary

plotDecisionBoundary(z,retvals,hiddenActivationFunc="tanh",0.3)

![Image 168](index-103_1.jpg)

**2.2c Classification with Multi-layer Deep** **Learning Network – Tanh**

**activation(Octave)**

The code below uses the Tanh activation in the hidden layers for Octave

\# Read the data

data=csvread("data.csv");

X=data(:,1:2);

Y=data(:,3);

\# Set layer dimensions

\# 2 - input features

\# 9 7 – 2 hidden layers with 9 and 7 hidden units

\# 1 – 1 sigmoid unit at output layer

layersDimensions = \[2 9 7 1\] #tanh=-0.5(ok), #relu=0.1 best!

\# Execute the L-Layer Deep Learning Network

\# hidden layer activation function – tanh

\# Learning rate – 0.1

\[weights biases costs\]=L\_Layer\_DeepModel(X', Y', layersDimensions, hiddenActivationFunc='tanh',

learningRate = 0.1,

numIterations = 10000);

#Plot cost vs iterations

plotCostVsIterations(10000,costs);

#Plot the decision boundary

plotDecisionBoundary(data,weights, biases,hiddenActivationFunc="tanh")

![Image 169](index-105_1.jpg)

![Image 170](index-106_1.jpg)

![Image 171](index-107_1.jpg)

![Image 172](index-107_2.jpg)

![Image 173](index-107_3.jpg)

**3\. Bernoulli’s Lemniscate**

To make things more interesting, I create a 2D figure of the

Bernoulli’s lemniscate to perform non-linear classification. The Lemniscate is given by the equation

\=

**3a. Classifying a lemniscate with Deep**

**Learning Network – Relu**

**activation(Python)**

import os

import numpy as np

import matplotlib.pyplot as plt

os.chdir("C:\\\\software\\\\DeepLearning-Posts\\\\part3") execfile("./DLfunctions33.py")

\# Create data set

x1=np.random.uniform(0,10,2000).reshape(2000,1)

x2=np.random.uniform(0,10,2000).reshape(2000,1)

X=np.append(x1,x2,axis=1)

X.shape

\# Create a subset of values where squared is <0.4. Perform ravel() to flatten this vector

\# Create the equation

\# (x^{2} + y^{2})^2 - 2a^2\*(x^{2}-y^{2}) <= 0

a=np.power(np.power(X\[:,0\]-5,2) + np.power(X\[:,1\]-5,2),2)

b=np.power(X\[:,0\]-5,2) - np.power(X\[:,1\]-5,2)

c= a - (b\*np.power(4,2)) <=0

Y=c.reshape(2000,1)

\# Create a scatter plot of the lemniscate

plt.scatter(X\[:,0\], X\[:,1\], c=Y, marker= 'o', s=15,cmap="viridis") Z=np.append(X,Y,axis=1)

plt.savefig("fig50.png",bbox\_inches='tight')

plt.clf()

\# Set the data for classification

X2=X.T

Y2=Y.T

\# These settings work the best

\# Set the Deep Learning layer dimensions for a Relu activation

\# 2 - input features

\# 7,4 – 2 hidden layers with 7 and 4 hidden units

\# 1 – 1 sigmoid activation unit at output layer

layersDimensions = \[2,7,4,1\]

#Execute the L-layer DL network

\# hidden layer activation function – relu

\# learning rate – 0.5

parameters = L\_Layer\_DeepModel(X2, Y2, layersDimensions,

hiddenActivationFunc='relu', learning\_rate = 0.5,num\_iterations = 10000, fig="fig5.png")

#Plot the decision boundary

plot\_decision\_boundary(lambda x: predict(parameters, x.T), X2, Y2,str(2.2),"fig6.png")

\# Compute the Confusion matrix

yhat = predict(parameters,X2)

from sklearn.metrics import confusion\_matrix

a=confusion\_matrix(Y2.T,yhat.T)

#Print accuracy,precision, recall and F1 score

from sklearn.metrics import accuracy\_score, precision\_score, recall\_score, f1\_score

print('Accuracy: {:.2f}'.format(accuracy\_score(Y2.T, yhat.T))) print('Precision: {:.2f}'.format(precision\_score(Y2.T, yhat.T))) print('Recall: {:.2f}'.format(recall\_score(Y2.T, yhat.T)))

print('F1: {:.2f}'.format(f1\_score(Y2.T, yhat.T)))

\## Accuracy: 0.93

\## Precision: 0.77

\## Recall: 0.76

\## F1: 0.76

![Image 174](index-110_1.jpg)

![Image 175](index-111_1.jpg)

We could get better performance by tuning further. Do play around with the code.

**Note:**: The lemniscate data is saved as a CSV and then read in R and also in Octave.

**3b. Classifying a lemniscate with Deep**

**Learning Network – Relu activation(R**

**code)**

The R decision boundary for the Bernoulli’s lemniscate is shown below

\# Read lemniscate data

Z <- as.matrix(read.csv("lemniscate.csv",header=FALSE)) Z1=data.frame(Z)

\# Create a scatter plot of the lemniscate

ggplot(Z1,aes(x=V1,y=V2,col=V3)) +geom\_point()

#Set the data for the DL network

X=Z\[,1:2\]

Y=Z\[,3\]

X1=t(X)

Y1=t(Y)

\# Set the layer dimensions for the tanh activation function

\# 2 – No of input features

#5, 4 – 2 hidden layers with 5 and 4 hidden units

\# 1 – 1 sigmoid output activation function in output layer

layersDimensions = c(2,5,4,1)

\# Execute the L layer Deep Learning network

\# Activation function in hidden layer - Tanh activation

\# learning rate=0.3

retvals = L\_Layer\_DeepModel(X1, Y1, layersDimensions,

hiddenActivationFunc='tanh',

learningRate = 0.3,

numIterations = 20000, print\_cost = True)

![Image 176](index-113_1.jpg)

\# Plot cost vs iteration

costs <- retvals\[\['costs'\]\]

numIterations = 20000

iterations <- seq(0,numIterations,by=1000)

df <-data.frame(iterations,costs)

ggplot(df,aes(x=iterations,y=costs)) + geom\_point() +geom\_line(color="blue")

\+ xlab('No of iterations') + ylab('Cost') + ggtitle("Cost vs No of iterations")

![Image 177](index-114_1.jpg)

![Image 178](index-114_2.jpg)

#Plot the decision boundary

plotDecisionBoundary(Z,retvals,hiddenActivationFunc="tanh",0.3)

![Image 179](index-115_1.jpg)

**3c. Classifying a lemniscate with Deep**

**Learning Network – Relu activation**

**(Octave code)**

Octave is used to generate the non-linear lemniscate boundary.

\# Read the data

data=csvread("lemniscate.csv");

X=data(:,1:2);

Y=data(:,3);

\# Set the dimensions of the layers

\# 2 – no of input features

\# 9 7 – 2 hidden layers with 9 and 7 activation units respectively

\# 1 – 1 activation unit in output layer (sigmoid)

layersDimensions = \[2 9 7 1\]

\# Execute the L-layer the DL network

#hidden activation function – relu

\# learning rate- 0.20

\[weights biases costs\]=L\_Layer\_DeepModel(X', Y', layersDimensions, hiddenActivationFunc='relu',

learningRate = 0.20,

numIterations = 10000);

#Plot the cost vs iterations

plotCostVsIterations(10000,costs);

#Plot the descion boundary

plotDecisionBoundary(data,weights, biases,hiddenActivationFunc="relu")

![Image 180](index-117_1.jpg)

![Image 181](index-118_1.jpg)

![Image 182](index-119_1.jpg)

**4a. Binary Classification using MNIST –**

**Python code**

Finally, I perform a simple classification using the MNIST

handwritten digits, which according to Prof Geoffrey Hinton is “the Drosophila of Deep Learning”.

The Python code for reading the MNIST data is taken from Alex Kesling’s github link MNIST

(https://gist.github.com/akesling/5358964)

In the Python code below, I perform a simple binary classification between the handwritten digit ‘5’ and ‘not 5’ which is all other digits.

I perform the proper classification of all digits using the Softmax classifier in chapter 5.

import os

import numpy as np

import matplotlib.pyplot as plt

execfile("./DLfunctions34.py")

#Load MNIST

execfile("./load\_mnist.py")

\# Set the training and test data and labels

training=list(read(dataset='training',path="./mnist")) test=list(read(dataset='testing',path="./mnist"))

lbls=\[\]

pxls=\[\]

print(len(training))

\# Select the first 10000 training data and the labels

for i in range(10000):

l,p=training\[i\]

lbls.append(l)

pxls.append(p)

labels= np.array(lbls)

pixels=np.array(pxls)

\# Set y=1 when labels == 5 and 0 otherwise

y=(labels==5).reshape(-1,1)

X=pixels.reshape(pixels.shape\[0\],-1)

\# Create the necessary feature and target variable

X1=X.T

Y1=y.T

\# Create the layer dimensions. The number of features are 28 x 28 = 784 since the 28 x 28

\# pixels is flattened to single vector of length 784.

\# 784 – No of input features = 28 x28

\# 15, 9 – 2 hidden layers with 15 and 9 hidden activation units

\# 1 – 1 activation unit in the output layer (sigmoid)

layersDimensions=\[784, 15,9,7,1\] #

#Execute the L-Layer Deep Learning Network

\# hidden activation function – relu

#learning reate – 0.1

parameters = L\_Layer\_DeepModel(X1, Y1, layersDimensions,

hiddenActivationFunc='relu', learning\_rate = 0.1,num\_iterations = 1000, fig="fig7.png")

\# Read the Test data and labels

lbls1=\[\]

pxls1=\[\]

for i in range(800):

l,p=test\[i\]

lbls1.append(l)

pxls1.append(p)

testLabels=np.array(lbls1)

testData=np.array(pxls1)

ytest=(testLabels==5).reshape(-1,1)

Xtest=testData.reshape(testData.shape\[0\],-1)

Xtest1=Xtest.T

Ytest1=ytest.T

\# Predict based on test data

yhat = predict(parameters,Xtest1)

from sklearn.metrics import confusion\_matrix

#Compute the confusion matrix

a=confusion\_matrix(Ytest1.T,yhat.T)

#Print accuracy, precision, recall and F! score

from sklearn.metrics import accuracy\_score, precision\_score, recall\_score, f1\_score

print('Accuracy: {:.2f}'.format(accuracy\_score(Ytest1.T, yhat.T))) print('Precision: {:.2f}'.format(precision\_score(Ytest1.T, yhat.T))) print('Recall: {:.2f}'.format(recall\_score(Ytest1.T, yhat.T))) print('F1: {:.2f}'.format(f1\_score(Ytest1.T, yhat.T)))

\# Plot the Precision-Recall curve

probs=predict\_proba(parameters,Xtest1)

from sklearn.metrics import precision\_recall\_curve

precision, recall, thresholds = precision\_recall\_curve(Ytest1.T, probs.T) closest\_zero = np.argmin(np.abs(thresholds))

closest\_zero\_p = precision\[closest\_zero\]

closest\_zero\_r = recall\[closest\_zero\]

#Plot precision-recall curve

plt.xlim(\[0.0, 1.01\])

plt.ylim(\[0.0, 1.01\])

plt.plot(precision, recall, label='Precision-Recall Curve')

plt.plot(closest\_zero\_p, closest\_zero\_r, 'o', markersize = 12, fillstyle = 'none', c='r', mew=3)

plt.xlabel('Precision', fontsize=16)

plt.ylabel('Recall', fontsize=16)

plt.savefig("fig8.png",bbox\_inches='tight')

\## Accuracy: 0.99

\## Precision: 0.96

\## Recall: 0.89

\## F1: 0.92

![Image 183](index-123_1.jpg)

![Image 184](index-124_1.jpg)

In addition to plotting the Cost vs Iterations, I also plot the Precision-Recall curve to show how the Precision and Recall, which are

complementary to each other, vary with respect to the other.

**4b. Binary Classification using MNIST –**

**R code**

In the R code below the same binary classification of the digit ‘5’ and the ‘not 5’ is performed. The code to read and display the MNIST data is taken from Brendan O’ Connor’s github link

at MNIST(https://gist.github.com/brendano/39760)

source("mnist.R")

#Load the MNIST data

load\_mnist()

#show\_digit(train$x\[2,\]

#Set the layer dimensions

\# 784 – no of input features = 28 x 28

\# 7, 7, 3 – 3 hidden layers with 7,7,3 activation units

\# 1 - 1 sigmoid activation unit at output layer

layersDimensions=c(784, 7,7,3,1) # Works at 1500

x <- t(train$x)

\# Choose only 5000 training data

x2 <- x\[,1:5000\]

\# Classify the data

y <-train$y

\# Set labels for all digits that are 'not 5' to 0

y\[y!=5\] <- 0

\# Set labels of digit 5 as 1

y\[y==5\] <- 1

\# Set the data

y1 <- as.matrix(y)

y2 <- t(y1)

![Image 185](index-126_1.jpg)

\# Choose the 1st 5000 data

y3 <- y2\[,1:5000\]

#Execute the L-Layer Deep Learning Model

\# hidden activation function – relu

\# learning rate – 0.3

retvals = L\_Layer\_DeepModel(x2, y3, layersDimensions,

hiddenActivationFunc='tanh',

learningRate = 0.3,

numIterations = 3000, print\_cost = True)

\# Setup costs and iterations

costs <- retvals\[\['costs'\]\]

numIterations = 3000

iterations <- seq(0,numIterations,by=1000)

df <-data.frame(iterations,costs)

\# Plot cost vs iterations

ggplot(df,aes(x=iterations,y=costs)) + geom\_point() +geom\_line(color="blue")

\+ xlab('No of iterations') + ylab('Cost') + ggtitle("Cost vs No of iterations")

![Image 186](index-127_1.jpg)

\# Compute probability scores

scores <- computeScores(retvals$parameters, x2,hiddenActivationFunc='relu') a=y3==1

b=y3==0

\# Compute probabilities of class 0 and class 1

class1=scores\[a\]

class0=scores\[b\]

![Image 187](index-128_1.jpg)

\# Plot ROC curve

pr <-pr.curve(scores.class0=class1,

scores.class1=class0,

curve=T)

plot(pr)

![Image 188](index-129_1.jpg)

The AUC curve hugs the top left corner and hence the performance of the classifier is quite good.

**4c. Binary Classification using MNIST –**

**Octave code**

This code to load MNIST data was taken from Daniel E blog

(http://daniel-e.github.io/2017-10-20-loading-mnist-handwritten-digits-with-octave-or-matlab/)

Precision recall curves are available in Matlab, but are yet to be implemented in Octave’s statistics package.

\# Load the MNIST data

load('./mnist/mnist.txt.gz');

\# Classify digits as 5 and not 5

\# Subset the 'not 5' digits

a=(trainY != 5);

\# Subset '5'

b=(trainY == 5);

#make a copy of trainY

#Set 'not 5' as 0 and '5' as 1

y=trainY;

y(a)=0;

y(b)=1;

X=trainX(1:5000,:);

Y=y(1:5000);

\# Set the dimensions of layer

\# 784 – number of input features = 28 x 28

\# 7, 7, 3 – 3 hidden layers with 7,7, 3 hidden activation units respectively

\# 1 - 1 sigmoid activation unit at output layer

layersDimensions=\[784, 7,7,3,1\];

\# Execute the L-Layerthe DL network

\# hidden activation function – relu

#learning rate – 0.1

\[weights biases costs\]=L\_Layer\_DeepModel(X', Y', layersDimensions, hiddenActivationFunc='relu',

![Image 189](index-131_1.jpg)

learningRate = 0.1,

numIterations = 5000);

**5.Conclusion**

It was quite a challenge coding a Deep Learning Network in Python, R and Octave. The Deep Learning network implementation, in this chapter is the ‘no-frills’ Deep Learning network. It does not include initialization techniques, regularization or gradient optimizations methods. These will be discussed in chapter 6 and chapter 7. This L-layer Deep Learning network will be enhanced in the later chapters.

Here are some key learning that I got while playing with different multi-layer networks on different problems

a. Deep Learning Networks come with many levers, the hyper-

parameters,

– learning rate

– activation unit

– number of hidden layers

– number of units per hidden layer

– number of iterations while performing gradient descent

b. Deep Networks are very sensitive. A change in any of the hyperparameter makes it perform very differently

c. Initially I thought adding more hidden layers, or more units per hidden layer will make the DL network better at learning. On the contrary, there is a performance degradation after the optimal DL

configuration

d. At a sub-optimal number of hidden layers or number of hidden units, gradient descent seems to get stuck at a local minima

e. There were occasions when the cost came down, only to increase slowly as the number of iterations were increased. Probably early stopping would have helped.

f. I also did come across situations of ‘exploding/vanishing gradient’; cost went to Inf/-Inf.

Feel free to fork/clone the code from

Github DeepLearningFromFirstPrinciples

(https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/master/Chap3-L-LayerDeepLearningNetwork) and take the DL network apart and play around with it.

[UPGRADE NOW](https://wordpress.com/plans/14647342/?feature=no-adverts&utm_campaign=removeadsnotive) [DISMISS MESSAGE](https://gigadom.wordpress.com/2018/01/11/deep-learning-from-first-principles-in-python-r-and-octave-part-2/)

![Image 190](index-134_1.jpg)

**4.**

**Deep Learning network with the**

**Softmax**

In this fourth chapter I explore the details of creating a multi-class classifier using the Softmax activation unit in a neural network. This fourth chapter takes a swing at multi-class classification and uses the Softmax as the activation unit in the output layer. Inclusion of the Softmax activation unit in the activation layer requires us to compute the derivative of Softmax, or rather the “Jacobian” of the Softmax function, besides also computing the log loss for this Softmax activation during backward propagation. Since the derivation of the Jacobian of a Softmax and the computation of the Cross Entropy/log loss is very involved, I have implemented a basic neural network with just 1 hidden layer with the Softmax activation at the output layer. I also perform multi-class classification based on the ‘spiral’ data set from CS231n Convolutional Neural Networks

(http://cs231n.github.io/neural-networks-case-study/) Stanford course, to test the performance and correctness of the implementations in Python, R and Octave. The vectorized implementations of the

functions in this chapter are at Appendix 4 - Deep Learning network with the Softmax

You can clone download the code for the Python, R and Octave

implementations from Github at DeepLearningFromFirstPrinciples (https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/master/Chap4-MulticlassDeepLearningNetwork)

The Softmax function takes an N dimensional vector as input and generates a N-dimensional vector as output.

The Softmax function is given by (4a) below

\- (4a)

There is a probabilistic interpretation of the Softmax, since the sum of

![Image 191](index-135_1.jpg)

![Image 192](index-135_2.jpg)

![Image 193](index-135_3.jpg)

![Image 194](index-135_4.jpg)

![Image 195](index-135_5.jpg)

the Softmax values of a set of vectors will always add up to 1, given that each Softmax value is divided by the total of all values.

As mentioned earlier, the Softmax takes a vector input and returns a vector of outputs. For e.g. the Softmax of a vector a= \[1, 3, 6\], is another vector S= \[0.0063, 0.0471, 0.9464\]. Notice that vector output is proportional to the input vector. Also, taking the derivative of a vector by another vector, is known as the Jacobian. By the way, The Matrix Calculus You Need For Deep

Learning (https://arxiv.org/pdf/1802.01528.pdf ) by Terence Parr and Jeremy Howard, is very good paper that distills all the main

mathematical concepts for Deep Learning in one place.

Let us take a simple 2 layered neural network with just 2 activation units in the hidden layer is shown below

and

where g'() is the activation unit in the hidden layer which can be a relu, sigmoid or a

![Image 196](index-136_1.jpg)

![Image 197](index-136_2.jpg)

![Image 198](index-136_3.jpg)

![Image 199](index-136_4.jpg)

![Image 200](index-136_5.jpg)

![Image 201](index-136_6.jpg)

![Image 202](index-136_7.jpg)

![Image 203](index-136_8.jpg)

![Image 204](index-136_9.jpg)

![Image 205](index-136_10.jpg)

tanh function

**Note**: The superscript denotes the layer. The equations are applicable for layer 1

of the neural network. For layer 2 with the Softmax activation, the equations are

and

where S is the Softmax activation function and using equation (4a) above

The Jacobian of the softmax ‘S’ is given by

Now the ‘division-rule’ of derivatives is as follows. If u and v are functions of x, then

Using this we can compute each element of the above Jacobian matrix It can be seen that

when i=j we have

and when

![Image 206](index-137_1.jpg)

![Image 207](index-137_2.jpg)

![Image 208](index-137_3.jpg)

![Image 209](index-137_4.jpg)

![Image 210](index-137_5.jpg)

![Image 211](index-137_6.jpg)

![Image 212](index-137_7.jpg)

![Image 213](index-137_8.jpg)

![Image 214](index-137_9.jpg)

![Image 215](index-137_10.jpg)

![Image 216](index-137_11.jpg)

![Image 217](index-137_12.jpg)

![Image 218](index-137_13.jpg)

This is of the general form

when i=j

and

when

**Note**: Since the Softmax essentially gives the probability the following

notation is also used

when i=j

and

If you throw the “Kronecker delta” into the equation, then the above equations can be expressed even more concisely as

where

when i=j and 0 when

This reduces the Jacobian of the simple 2 output softmax vectors equation (A) as

The loss of Softmax is given by

For the 2 valued Softmax output this is

![Image 219](index-138_1.jpg)

![Image 220](index-138_2.jpg)

![Image 221](index-138_3.jpg)

![Image 222](index-138_4.jpg)

![Image 223](index-138_5.jpg)

![Image 224](index-138_6.jpg)

![Image 225](index-138_7.jpg)

![Image 226](index-138_8.jpg)

![Image 227](index-138_9.jpg)

![Image 228](index-138_10.jpg)

![Image 229](index-138_11.jpg)

![Image 230](index-138_12.jpg)

![Image 231](index-138_13.jpg)

![Image 232](index-138_14.jpg)

Using the chain rule we can write

(1)

In expanded form this is

Also

Therefore

Since

when i=j

and

when

which simplifies to

Since

Similarly

In general this is of the form

\- (A)

For e.g. if the probabilities computed were p=\[0.1, 0.7, 0.2\] then this

![Image 233](index-139_1.jpg)

![Image 234](index-139_2.jpg)

![Image 235](index-139_3.jpg)

![Image 236](index-139_4.jpg)

![Image 237](index-139_5.jpg)

implies that the class with probability 0.7 is the likely class. This would imply that the ‘One hot encoding’ for yi would be yi=\[0,1,0\]

therefore the gradient pi-yi = \[0.1, -0.3, 0.2\]

**Note**: Further, we could extend this derivation for a Softmax activation output that outputs 3 classes

We could derive

which similarly reduces to

interestingly, despite the lengthy derivations the final result is simple and intuitive!

As seen in in chapter 3, the key equations for forward and backward propagation are

**Forward propagation equations layer 1**

![Image 238](index-140_1.jpg)

![Image 239](index-140_2.jpg)

![Image 240](index-140_3.jpg)

![Image 241](index-140_4.jpg)

![Image 242](index-140_5.jpg)

![Image 243](index-140_6.jpg)

![Image 244](index-140_7.jpg)

![Image 245](index-140_8.jpg)

![Image 246](index-140_9.jpg)

and

**Forward propagation equations layer 1**

and

Using the result (A) in the back propagation equations below we have **Backward propagation equations layer 2**

**Backward propagation equations layer 1**

**2\. Spiral data set**

As I mentioned earlier, I will be using the ‘spiral’ data from CS231n

[Convolutional Neural Networks (http://cs231n.github.io/neural-](http://cs231n.github.io/neural-networks-case-study/)

[networks-case-study/) to ensure that my vectorized implementat](http://cs231n.github.io/neural-networks-case-study/)ions in Python, R and Octave are correct. Here is the ‘spiral’ data set.

import numpy as np

import matplotlib.pyplot as plt

exec(open("././DLfunctions41.py").read())

\# Create an input data set - Taken from CS231n Convolutional Neural networks

\# http://cs231n.github.io/neural-networks-case-study/

N = 100 # number of points per class

D = 2 # dimensionality

K = 3 # number of classes

X = np.zeros((N\*K,D)) # data matrix (each row = single example) y = np.zeros(N\*K, dtype='uint8') # class labels

for j in range(K):

ix = range(N\*j,N\*(j+1))

r = np.linspace(0.0,1,N) # radius

t = np.linspace(j\*4,(j+1)\*4,N) + np.random.randn(N)\*0.2 # theta X\[ix\] = np.c\_\[r\*np.sin(t), r\*np.cos(t)\]

y\[ix\] = j

\# Plot the data

plt.scatter(X\[:, 0\], X\[:, 1\], c=y, s=40, cmap=plt.cm.Spectral) plt.savefig("fig1.png", bbox\_inches='tight')

![Image 247](index-142_1.jpg)

The implementations of the vectorized Python, R and Octave code are shown diagrammatically below

![Image 248](index-143_1.jpg)

**2.1 Multi-class classification with**

**Softmax – Python code**

A simple 2-layer Neural network with a single hidden layer, with 100

Relu activation units in the hidden layer and the Softmax activation unit in the output layer is used for multi-class classification. This Deep Learning Network, plots the non-linear boundary of the 3

classes as shown below

import numpy as np

import matplotlib.pyplot as plt

import os

os.chdir("C:/junk/dl-4/dl-4")

exec(open("././DLfunctions41.py").read())

\# Read the input data

N = 100 # number of points per class

D = 2 # dimensionality

K = 3 # number of classes

X = np.zeros((N\*K,D)) # data matrix (each row = single example) y = np.zeros(N\*K, dtype='uint8') # class labels

#Loop

for j in range(K):

ix = range(N\*j,N\*(j+1))

r = np.linspace(0.0,1,N) # radius

t = np.linspace(j\*4,(j+1)\*4,N) + np.random.randn(N)\*0.2 # theta X\[ix\] = np.c\_\[r\*np.sin(t), r\*np.cos(t)\]

y\[ix\] = j

\# Set the number of features, hidden units in hidden layer and number of classess numHidden=100 # No of hidden units in hidden layer

numFeats= 2 # dimensionality

numOutput = 3 # number of classes

\# Initialize the model

parameters=initializeModel(numFeats,numHidden,numOutput) W1= parameters\['W1'\]

b1= parameters\['b1'\]

W2= parameters\['W2'\]

b2= parameters\['b2'\]

\# Set the learning rate

learningRate=0.6

\# Initialize losses

losses=\[\]

\# Perform Gradient descent

for i in range(10000):

\# Forward propagation through hidden layer with Relu units

A1,cache1= layerActivationForward(X.T,W1,b1,'relu')

\# Forward propagation through output layer with Softmax

A2,cache2 = layerActivationForward(A1,W2,b2,'softmax')

\# No of training examples

numTraining = X.shape\[0\]

\# Compute log probs. Take the log prob of correct class based on output y correct\_logprobs = -np.log(A2\[range(numTraining),y\])

\# Compute loss

loss = np.sum(correct\_logprobs)/numTraining

\# Print the loss

if i % 1000 == 0:

print("iteration %d: loss %f" % (i, loss))

losses.append(loss)

dA=0

\# Backward propagation through output layer with Softmax

dA1,dW2,db2 = layerActivationBackward(dA, cache2, y,

activationFunc='softmax')

\# Backward propagation through hidden layer with Relu unit

dA0,dW1,db1 = layerActivationBackward(dA1.T, cache1, y,

activationFunc='relu')

#Update paramaters with the learning rate

W1 += -learningRate \* dW1

b1 += -learningRate \* db1

W2 += -learningRate \* dW2.T

b2 += -learningRate \* db2.T

#Plot losses vs iterations

i=np.arange(0,10000,1000)

plt.plot(i,losses)

plt.xlabel('Iterations')

plt.ylabel('Loss')

plt.title('Losses vs Iterations')

plt.savefig("fig2.png", bbox="tight")

#Compute the multi-class Confusion Matrix

from sklearn.metrics import confusion\_matrix

from sklearn.metrics import accuracy\_score, precision\_score, recall\_score, f1\_score

\# We need to determine the predicted values from the learnt data

\# Forward propagation through hidden layer with Relu units

A1,cache1= layerActivationForward(X.T,W1,b1,'relu')

\# Forward propagation through output layer with Softmax

A2,cache2 = layerActivationForward(A1,W2,b2,'softmax')

#Compute predicted values from weights and biases

yhat=np.argmax(A2, axis=1)

\# Compute the confusion matrix

a=confusion\_matrix(y.T,yhat.T)

print("Multi-class Confusion Matrix")

print(a)

\## iteration 0: loss 1.098507

\## iteration 1000: loss 0.214611

\## iteration 2000: loss 0.043622

\## iteration 3000: loss 0.032525

\## iteration 4000: loss 0.025108

![Image 249](index-147_1.jpg)

\## iteration 5000: loss 0.021365

\## iteration 6000: loss 0.019046

\## iteration 7000: loss 0.017475

\## iteration 8000: loss 0.016359

\## iteration 9000: loss 0.015703

\## Multi-class Confusion Matrix

\## \[\[ 99 1 0\]

\## \[ 0 100 0\]

\## \[ 0 1 99\]\]

![Image 250](index-148_1.jpg)

**2.2 Multi-class classification with**

**Softmax – R code**

The spiral data set created with Python was saved (spiral.csv), and is used as the input with R code. To compute the softmax derivative I create matrices for the One Hot Encoded yi and then stack them before subtracting pi-yi.

library(ggplot2)

library(dplyr)

library(RColorBrewer)

source("DLfunctions41.R")

\# Read the spiral dataset

Z <- as.matrix(read.csv("spiral.csv",header=FALSE)) Z1=data.frame(Z)

#Plot the dataset

ggplot(Z1,aes(x=V1,y=V2,col=V3)) +geom\_point() +

scale\_colour\_gradientn(colours = brewer.pal(10, "Spectral"))

![Image 251](index-150_1.jpg)

\# Setup the data

X <- Z\[,1:2\]

y <- Z\[,3\]

X1 <- t(X)

Y1 <- t(y)

\# Initialize number of features, number of hidden units in hidden layer and

\# number of classes

numFeats<-2 # No features

numHidden<-100 # No of hidden units

numOutput<-3 # No of classes

\# Initialize model

parameters <-initializeModel(numFeats, numHidden,numOutput)

\# Get the parameters

W1 <-parameters\[\['W1'\]\]

b1 <-parameters\[\['b1'\]\]

W2 <-parameters\[\['W2'\]\]

b2 <-parameters\[\['b2'\]\]

\# Set the learning rate

learningRate <- 0.5

\# Initialize losses

losses <- NULL

\# Perform gradient descent

for(i in 0:9000){

\# Forward propagation through hidden layer with Relu units

retvals <- layerActivationForward(X1,W1,b1,'relu')

A1 <- retvals\[\['A'\]\]

cache1 <- retvals\[\['cache'\]\]

forward\_cache1 <- cache1\[\['forward\_cache1'\]\]

activation\_cache <- cache1\[\['activation\_cache'\]\]

\# Forward propagation through output layer with Softmax units retvals = layerActivationForward(A1,W2,b2,'softmax')

A2 <- retvals\[\['A'\]\]

cache2 <- retvals\[\['cache'\]\]

forward\_cache2 <- cache2\[\['forward\_cache1'\]\]

activation\_cache2 <- cache2\[\['activation\_cache'\]\]

\# No of training examples

numTraining <- dim(X)\[1\]

dA <-0

\# Select the elements where the y values are 0, 1 or 2 and make a vector a=c(A2\[y==0,1\],A2\[y==1,2\],A2\[y==2,3\])

\# Compute probabalities

correct\_probs = -log(a)

\# Compute loss

loss= sum(correct\_probs)/numTraining

if(i %% 1000 == 0){

sprintf("iteration %d: loss %f",i, loss) print(loss)

}

\# Backward propagation through output layer with Softmax units retvals = layerActivationBackward(dA, cache2, y,

activationFunc='softmax')

dA1 = retvals\[\['dA\_prev'\]\]

dW2= retvals\[\['dW'\]\]

db2= retvals\[\['db'\]\]

\# Backward propagation through hidden layer with Relu units

retvals = layerActivationBackward(t(dA1), cache1, y,

activationFunc='relu')

dA0 = retvals\[\['dA\_prev'\]\]

dW1= retvals\[\['dW'\]\]

db1= retvals\[\['db'\]\]

\# Update parameters

W1 <- W1 - learningRate \* dW1

b1 <- b1 - learningRate \* db1

W2 <- W2 - learningRate \* t(dW2)

b2 <- b2 - learningRate \* t(db2)

}

\## \[1\] 1.212487

\## \[1\] 0.5740867

\## \[1\] 0.4048824

\## \[1\] 0.3561941

\## \[1\] 0.2509576

\## \[1\] 0.7351063

\## \[1\] 0.2066114

\## \[1\] 0.2065875

\## \[1\] 0.2151943

\## \[1\] 0.1318807

#Create iterations

iterations <- seq(0,10)

df=data.frame(iterations,losses)

![Image 252](index-153_1.jpg)

![Image 253](index-153_2.jpg)

\# Plot cost vs iterations

ggplot(df,aes(x=iterations,y=losses)) + geom\_point() + geom\_line(color="blue")

+

ggtitle("Losses vs iterations") + xlab("Iterations") + ylab("Loss")

#Plot the decision boundary

plotDecisionBoundary(Z,W1,b1,W2,b2)

![Image 254](index-154_1.jpg)

**Multi-class Confusion Matrix**

library(caret)

library(e1071)

\# Forward propagation through hidden layer with Relu units

retvals <- layerActivationForward(X1,W1,b1,'relu')

A1 <- retvals\[\['A'\]\]

\# Forward propagation through output layer with Softmax units retvals = layerActivationForward(A1,W2,b2,'softmax')

A2 <- retvals\[\['A'\]\]

yhat <- apply(A2, 1,which.max) -1

Confusion Matrix and Statistics

Reference

Prediction 0 1 2

0 97 0 1

1 2 96 4

2 1 4 95

Overall Statistics

Accuracy : 0.96

95% CI : (0.9312, 0.9792)

No Information Rate : 0.3333

P-Value \[Acc > NIR\] : <2e-16

Kappa : 0.94

Mcnemar's Test P-Value : 0.5724

Statistics by Class:

Class: 0 Class: 1 Class: 2

Sensitivity 0.9700 0.9600 0.9500

Specificity 0.9950 0.9700 0.9750

Pos Pred Value 0.9898 0.9412 0.9500

Neg Pred Value 0.9851 0.9798 0.9750

Prevalence 0.3333 0.3333 0.3333

Detection Rate 0.3233 0.3200 0.3167

Detection Prevalence 0.3267 0.3400 0.3333

Balanced Accuracy 0.9825 0.9650 0.9625

**2.3 Multi-class classification with**

**Softmax – Octave code**

A 2-layer neural network with the Softmax activation unit in the output layer is constructed in Octave. The same spiral data (spiral.csv) set is used for Octave also

source("DL41functions.m")

\# Read the spiral data

data=csvread("spiral.csv");

\# Setup the data

X=data(:,1:2);

Y=data(:,3);

\# Set the number of features, number of hidden units in hidden layer and number of classes

numFeats=2; #No features

numHidden=100; # No of hidden units

numOutput=3; # No of classes

\# Initialize model

\[W1 b1 W2 b2\] = initializeModel(numFeats,numHidden,numOutput);

\# Initialize losses

losses=\[\]

#Initialize learningRate

learningRate=0.5;

for k =1:10000

\# Forward propagation through hidden layer with Relu units

\[A1,cache1 activation\_cache1\]=

layerActivationForward(X',W1,b1,activationFunc ='relu');

\# Forward propagation through output layer with Softmax units

\[A2,cache2 activation\_cache2\] =

layerActivationForward(A1,W2,b2,activationFunc='softmax');

 # No of training examples

numTraining = size(X)(1);

\# Select rows where Y=0,1,and 2 and concatenate to a long vector a=\[A2(Y==0,1) ;A2(Y==1,2) ;A2(Y==2,3)\];

#Select the correct column for log prob

correct\_probs = -log(a);

#Compute log loss

loss= sum(correct\_probs)/numTraining;

if(mod(k,1000) == 0)

disp(loss);

losses=\[losses loss\];

endif

dA=0;

\# Backward propagation through output layer with Softmax units

\[dA1 dW2 db2\] = layerActivationBackward(dA, cache2,

activation\_cache2,Y,activationFunc='softmax');

\# Backward propagation through hidden layer with Relu units

\[dA0,dW1,db1\] = layerActivationBackward(dA1', cache1, activation\_cache1, Y, activationFunc='relu');

#Update parameters

W1 += -learningRate \* dW1;

b1 += -learningRate \* db1;

W2 += -learningRate \* dW2';

b2 += -learningRate \* db2';

endfor

\# Plot Losses vs Iterations

iterations=0:1000:9000

plotCostVsIterations(iterations,losses)

\# Plot the decision boundary

plotDecisionBoundary( X,Y,W1,b1,W2,b2)

![Image 255](index-158_1.jpg)

![Image 256](index-159_1.jpg)

The code for the Python, R and Octave implementations can be

downloaded from Github at DeepLearningFromFirstPrinciples

(https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/master/Chap4-MulticlassDeepLearningNetwork)

**Conclusion**

In this chapter, I implemented a 2 layer Neural Network with the Softmax classifier. In chapter 3, I implemented a multi-layer Deep Learning Network. The Softmax activation unit is included into into the generalized multi-layer Deep Network along with the other activation units of sigmoid,tanh and relu in chapter 5.

**5.**

**MNIST classification with**

**Softmax**

a. *A robot may not injure a human being or, through inaction, allow a* *human being to come to harm.*

*b. A robot must obey orders given it by human beings except where* *such orders would conflict with the First Law.*

*c. A robot must protect its own existence as long as such protection* *does not conflict with the First or Second Law.*

Isaac Asimov's Three Laws of Robotics

*Any sufficiently advanced technology is indistinguishable from magic.*

Arthur C Clarke.

![Image 257](index-162_1.jpg)

**1.Introduction**

In this 5th chapter on Deep Learning from first Principles in Python, R and Octave, I solve the MNIST data set of handwritten digits (shown below), from the basics. To do this, I construct a L-Layer, vectorized Deep Learning implementation in Python, R and Octave from scratch and classify the MNIST data set. The MNIST training data set contains 60000 handwritten digits from 0-9, and a test set of 10000 digits. MNIST, is a popular dataset for running Deep Learning tests, and has been rightfully termed as the ‘drosophila’ of Deep Learning, by none other than the venerable Prof Geoffrey Hinton.

This chapter largely builds upon chapter 3, in which I implemented a multi-layer Deep Learning network, with an arbitrary number of hidden layers and activation units per hidden layer and with the sigmoid output layer. To this, I add the derivation of the Jacobian of a Softmax, the Cross entropy loss and the computations of gradient

equations for a multi-class Softmax classifier which I had done in chapter 4

By combining the implementations of chapter 3 & 4 I build a generic, L-layer Deep Learning network, with arbitrary number of hidden layers and hidden units, which can do both binary (sigmoid) and multi-class (softmax) classification. The implementations of the functions invoked in this chapter are in Appendix 5 - MNIST

classification with Softmax

The generic, vectorized L-Layer Deep Learning Network

implementations in Python, R and Octave can be cloned/downloaded from GitHub at DeepLearningFromFirstPrinciples

(https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/master/Chap5-MNISTMultiClassDLNetwork). This implementation allows for

arbitrary number of hidden layers and hidden layer units. The activation function at the hidden layers can be one of sigmoid, relu and tanh. The output activation can do binary classification with the

‘sigmoid’, function or multi-class classification with ‘softmax’. Feel free to download and play around with the code!

Since regular gradient descent on 60,000 training samples on a laptop will result in memory problem on such a large dataset. So, this chapter also implements Stochastic Gradient Descent (SGD) for Python, R

and Octave. This chapter also includes the implementation of a numerically stable version of Softmax, to prevent the softmax and its derivative resulting in NaNs.

![Image 258](index-164_1.jpg)

![Image 259](index-164_2.jpg)

![Image 260](index-164_3.jpg)

![Image 261](index-164_4.jpg)

**2.Numerically stable Softmax**

The Softmax function

can be numerically unstable

because of the division of large exponentials. To handle this problem we have to implement stable Softmax function as below

Therefore

Here ‘D’ can be anything. A common choice is

Here is the stable Softmax implementation in Python

\# A numerically stable Softmax implementation

def stableSoftmax(Z):

#Compute the softmax of vector x in a numerically stable way.

shiftZ = Z.T - np.max(Z.T,axis=1).reshape(-1,1)

exp\_scores = np.exp(shiftZ)

\# Normalize them for each example

A = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

cache=Z

return A,cache

While trying to create an L-Layer generic Deep Learning network in the 3 languages, I found it useful to ensure that the model executed correctly on smaller datasets. You can run into numerous problems while setting up the matrices, which becomes extremely difficult to debug. So in this post, I run the model on 2 smaller data for sets used in my earlier posts (chapter 3 & chapter 4) , in each of the languages,

before running the generic model on MNIST.

Here is a fair warning: - if you think you can dive directly into Deep Learning, with just some basic knowledge of Machine Learning, you are bound to run into serious issues. Moreover, your knowledge will be incomplete. It is essential that you have a good grasp of Machine and Statistical Learning, the different algorithms, the measures and metrics for selecting the models etc. It would help to be conversant with all the ML models, ML concepts, validation techniques,

classification measures etc. Check out the internet/books for background.

**3.1a Random dataset with sigmoid**

**activation – Python**

This random data with 9 clusters, used in chapter 3 was used to test the complete L-layer Deep Learning network with Sigmoid activation.

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import pandas as pd

from sklearn.datasets import make\_classification, make\_blobs

exec(open("DLfunctions51.py").read()) # Cannot import in Rmd

\# Create a random data set with 9 centeres

X1, Y1 = make\_blobs(n\_samples = 400, n\_features = 2, centers = 9,cluster\_std =

1.3, random\_state =4)

#Create 2 classes

Y1=Y1.reshape(400,1)

Y1 = Y1 % 2

X2=X1.T

Y2=Y1.T

\# Set the dimensions of L -layer DL network

\# 2 – number of input features

\# 9,9 – 2 hidden layers with 9 activation units

\# 1 – 1 activation unit in the output layer

layersDimensions = \[2, 9, 9,1\] # 4-layer model

\# Execute the L-Layer DL network with hidden activation=relu and sigmoid output function

parameters = L\_Layer\_DeepModel(X2, Y2, layersDimensions,

hiddenActivationFunc='relu', outputActivationFunc="sigmoid",learningRate =

0.3,num\_iterations = 2500, print\_cost = True)

![Image 262](index-167_1.jpg)

**3.1b Spiral dataset with Softmax**

**activation – Python**

The Spiral data of chapter 4 was used to test the correct functioning of the complete L-layer Deep Learning network for multi-class

classification with Softmax activation.

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import pandas as pd

from sklearn.datasets import make\_classification, make\_blobs

exec(open("DLfunctions51.py").read())

\# Create an input data set - Taken from CS231n Convolutional Neural networks

\# http://cs231n.github.io/neural-networks-case-study/

N = 100 # number of points per class

D = 2 # dimensionality

K = 3 # number of classes

X = np.zeros((N\*K,D)) # data matrix (each row = single example) y = np.zeros(N\*K, dtype='uint8') # class labels

\# Loop over K

for j in range(K):

ix = range(N\*j,N\*(j+1))

r = np.linspace(0.0,1,N) # radius

t = np.linspace(j\*4,(j+1)\*4,N) + np.random.randn(N)\*0.2 # theta X\[ix\] = np.c\_\[r\*np.sin(t), r\*np.cos(t)\]

y\[ix\] = j

X1=X.T

Y1=y.reshape(-1,1).T

Set the parameters of the DL network

numHidden=100 # No of hidden units in hidden layer

numFeats= 2 # dimensionality

numOutput = 3 # number of classes

\# Set the dimensions of the layers

![Image 263](index-169_1.jpg)

layersDimensions=\[numFeats,numHidden,numOutput\]

\# Execute the L-layer DL network with hidden activation=relu and softmax output function

parameters = L\_Layer\_DeepModel(X1, Y1, layersDimensions,

hiddenActivationFunc='relu', outputActivationFunc="softmax",learningRate =

0.6,num\_iterations = 9000, print\_cost = True)

\## Cost after iteration 0: 1.098759

\## Cost after iteration 1000: 0.112666

\## Cost after iteration 2000: 0.044351

\## Cost after iteration 3000: 0.027491

\## Cost after iteration 4000: 0.021898

\## Cost after iteration 5000: 0.019181

\## Cost after iteration 6000: 0.017832

\## Cost after iteration 7000: 0.017452

\## Cost after iteration 8000: 0.017161

**3.1c MNIST dataset with Softmax**

**activation – Python**

In the code below, I execute Stochastic Gradient Descent on the MNIST training data of 60000. I used a mini-batch size of 1000.

Python takes about 40 minutes to crunch the data. In addition, I also compute the Confusion Matrix and other metrics like Accuracy, Precision and Recall for the MNIST data set. I get an accuracy of 0.93

on the MNIST test set. This accuracy can be improved by choosing more hidden layers or more hidden units and possibly tweaking the learning rate and the number of epochs.

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import pandas as pd

import math

from sklearn.datasets import make\_classification, make\_blobs

from sklearn.metrics import confusion\_matrix

from sklearn.metrics import accuracy\_score, precision\_score, recall\_score, f1\_score

exec(open("DLfunctions51.py").read())

exec(open("load\_mnist.py").read())

\# Read the MNIST training and test sets

training=list(read(dataset='training',path=".\\\\mnist")) test=list(read(dataset='testing',path=".\\\\mnist"))

\# Create labels and pixel arrays

lbls=\[\]

pxls=\[\]

print(len(training))

#for i in range(len(training)):

for i in range(60000):

l,p=training\[i\]

lbls.append(l)

 pxls.append(p)

labels= np.array(lbls)

pixels=np.array(pxls)

y=labels.reshape(-1,1)

X=pixels.reshape(pixels.shape\[0\],-1)

X1=X.T

Y1=y.T

\# Set the dimensions of the layers. The MNIST data is 28x28 pixels= 784

\# Hence input layer is 784. For the 10 digits the Softmax classifier

\# has to handle 10 outputs

\# 784 – No of input features- 28 x27

\# 15,9 – 2 hidden layers with 15 & 9 hidden units

#10 – 10 outputs at the output layer for 10 digits

layersDimensions=\[784, 15,9,10\] # Works very well,lr=0.01,mini\_batch =1000, total=20000

np.random.seed(1)

costs = \[\]

\# Execute the L-Layer Deep Learning network with Stochastic Gradient Descent

\# with Learning Rate=0.01, mini batch size=1000

\# number of epochs=3000

\# hidden units= relu

\# output activation unit =softmax

parameters = L\_Layer\_DeepModel\_SGD(X1, Y1, layersDimensions,

hiddenActivationFunc='relu', outputActivationFunc="softmax",learningRate =

0.01 ,mini\_batch\_size =1000, num\_epochs = 3000, print\_cost = True)

\# Compute the Confusion Matrix on Training set

\# Compute the training accuracy, precision and recall

proba=predict\_proba(parameters, X1,outputActivationFunc="softmax")

#A2, cache = forwardPropagationDeep(X1, parameters)

#proba=np.argmax(A2, axis=0).reshape(-1,1)

a=confusion\_matrix(Y1.T,proba)

print(a)

from sklearn.metrics import accuracy\_score, precision\_score, recall\_score, f1\_score

print('Accuracy: {:.2f}'.format(accuracy\_score(Y1.T, proba))) print('Precision: {:.2f}'.format(precision\_score(Y1.T, proba,average="micro")))

print('Recall: {:.2f}'.format(recall\_score(Y1.T, proba,average="micro")))

\# Read the test data

lbls=\[\]

pxls=\[\]

print(len(test))

\# Loop

for i in range(10000):

l,p=test\[i\]

lbls.append(l)

pxls.append(p)

testLabels= np.array(lbls)

testPixels=np.array(pxls)

ytest=testLabels.reshape(-1,1)

Xtest=testPixels.reshape(testPixels.shape\[0\],-1)

X1test=Xtest.T

Y1test=ytest.T

\# Compute the Confusion Matrix on Test set

\# Compute the test accuracy, precision and recall

probaTest=predict\_proba(parameters, X1test,outputActivationFunc="softmax")

#A2, cache = forwardPropagationDeep(X1, parameters)

#proba=np.argmax(A2, axis=0).reshape(-1,1)

a=confusion\_matrix(Y1test.T,probaTest)

\# Print accuracy, recall, precison and the 10-digit confusion matrix from sklearn.metrics import accuracy\_score, precision\_score, recall\_score, f1\_score

print('Accuracy: {:.2f}'.format(accuracy\_score(Y1test.T, probaTest))) print('Precision: {:.2f}'.format(precision\_score(Y1test.T,

probaTest,average="micro")))

print('Recall: {:.2f}'.format(recall\_score(Y1test.T, probaTest,average="micro")))

##1. Confusion Matrix of Training set

0 1 2 3 4 5 6 7 8 9

\## \[\[5854 0 19 2 10 7 0 1 24 6\]

\## \[ 1 6659 30 10 5 3 0 14 20 0\]

\## \[ 20 24 5805 18 6 11 2 32 37 3\]

\## \[ 5 4 175 5783 1 27 1 58 60 17\]

\## \[ 1 21 9 0 5780 0 5 2 12 12\]

\## \[ 29 9 21 224 6 4824 18 17 245 28\]

\## \[ 5 4 22 1 32 12 5799 0 43 0\]

\## \[ 3 13 148 154 18 3 0 5883 4 39\]

\## \[ 11 34 30 21 13 16 4 7 5703 12\]

\## \[ 10 4 1 32 135 14 1 92 134 5526\]\]

##2. Accuracy, Precision, Recall of Training set

\## Accuracy: 0.96

\## Precision: 0.96

\## Recall: 0.96

##3. Confusion Matrix of Test set

0 1 2 3 4 5 6 7 8 9

\## \[\[ 954 1 8 0 3 3 2 4 4 1\]

\## \[ 0 1107 6 5 0 0 1 2 14 0\]

\## \[ 11 7 957 10 5 0 5 20 16 1\]

\## \[ 2 3 37 925 3 13 0 8 18 1\]

\## \[ 2 6 1 1 944 0 7 3 4 14\]

\## \[ 12 5 4 45 2 740 24 8 42 10\]

\## \[ 8 4 4 2 16 9 903 0 12 0\]

\## \[ 4 10 27 18 5 1 0 940 1 22\]

\## \[ 11 13 6 13 9 10 7 2 900 3\]

\## \[ 8 5 1 7 50 7 0 20 29 882\]\]

##4. Accuracy, Precision, Recall of Training set

\## Accuracy: 0.93

\## Precision: 0.93

\## Recall: 0.93

![Image 264](index-174_1.jpg)

**3.2a Random dataset with sigmoid**

**activation – R code**

The random data set used in the Python code above which was saved as a csv(data.csv). The code is used to test the L -Layer DL network with sigmoid Activation in R.

source("DLfunctions5.R")

\# Read the random data set

z <- as.matrix(read.csv("data.csv",header=FALSE)) x <- z\[,1:2\]

y <- z\[,3\]

X <- t(x)

Y <- t(y)

\# Set the dimensions of the layers

\# 2 – number of input features\]

#9, 9 – 2 hidden layers with 9 hidden units each

\# 1 – 1 activation unit in the output layer

layersDimensions = c(2, 9, 9,1)

\# Execute a L-Layer DL network on the data set with relu hidden unit activation

\# sigmoid activation unit in the output layer

retvals = L\_Layer\_DeepModel(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",

learningRate = 0.3,

numIterations = 5000,

print\_cost = True)

#Plot the cost vs iterations

iterations <- seq(0,5000,1000)

costs=retvals$costs

df=data.frame(iterations,costs)

ggplot(df,aes(x=iterations,y=costs)) + geom\_point() + geom\_line(color="blue")

![Image 265](index-176_1.jpg)

\+ ggtitle("Costs vs iterations") + xlab("Iterations") + ylab("Loss")

**3.2b Spiral dataset with Softmax**

**activation – R**

The spiral data set used in the Python code above(spiral.csv) , is reused to test multi-class classification with Softmax.

source("DLfunctions5.R")

Z <- as.matrix(read.csv("spiral.csv",header=FALSE))

\# Setup the data

X <- Z\[,1:2\]

y <- Z\[,3\]

X <- t(X)

Y <- t(y)

\# Initialize number of features, number of hidden units in hidden layer and

\# number of classes

numFeats<-2 # No features

numHidden<-100 # No of hidden units

numOutput<-3 # No of classes

\# Set the layer dimensions

layersDimensions = c(numFeats,numHidden,numOutput)

\# Execute the L-Layer Deep Learning network with relu activation unit for hidden layer

\# and softmax activation in the output

retvals = L\_Layer\_DeepModel(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc="softmax",

learningRate = 0.5,

numIterations = 9000,

print\_cost = True)

#Plot cost vs iterations

iterations <- seq(0,9000,1000)

costs=retvals$costs

df=data.frame(iterations,costs)

ggplot(df,aes(x=iterations,y=costs)) + geom\_point() + geom\_line(color="blue")

\+ ggtitle("Costs vs iterations") + xlab("Iterations") + ylab("Costs")

**3.2c MNIST dataset with Softmax**

**activation – R**

The code below executes a L –Layer Deep Learning network with Softmax output activation, to classify the 10 handwritten digits from MNIST with Stochastic Gradient Descent. The 32768 random

samples from the data set was used to train the data.

Having said that, the Confusion Matrix in R dumps a lot of interesting statistics! There is a bunch of statistical measures for each class. For e.g. the Balanced Accuracy for the digits ‘6’ and ‘9’ is around 50%.

Looks like, the classifier is confused by the fact that 6 is inverted 9

and vice-versa. The accuracy on the Test data set is just around 75%. I could have played around with the number of layers, number of hidden units, learning rates, epochs etc to get a much higher accuracy.

But since each test took about 8+ hours, I may work on this, some other day!

source("DLfunctions5.R")

source("mnist.R")

#Load the mnist data

load\_mnist()

show\_digit(train$x\[2,\])

#Set the layer dimensions

layersDimensions=c(784, 15,9, 10) # Works at 1500

x <- t(train$x)

X <- x\[,1:60000\]

y <-train$y

y1 <- y\[1:60000\]

y2 <- as.matrix(y1)

Y=t(y2)

\# Subset 32768 random samples from MNIST

![Image 266](index-180_1.jpg)

permutation = c(sample(2^15))

\# Randomly shuffle the training data

X1 = X\[, permutation\]

y1 = Y\[1, permutation\]

y2 <- as.matrix(y1)

Y1=t(y2)

\# Execute Stochastic Gradient Descent on the entire training set

\# with ‘relu’ activiation in the hidden layer ‘softmax’ activation and

\# learning rate =0.05

retvalsSGD= L\_Layer\_DeepModel\_SGD(X1, Y1, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc="softmax",

learningRate = 0.05,

mini\_batch\_size = 512,

num\_epochs = 1,

print\_cost = True)

\# Compute the Confusion Matrix

library(caret)

library(e1071)

predictions=predictProba(retvalsSGD\[\['parameters'\]\],

X,hiddenActivationFunc='relu',

 outputActivationFunc="softmax") confusionMatrix(predictions,Y)

\# Confusion Matrix on the Training set

\> confusionMatrix(predictions,Y)

Confusion Matrix and Statistics

Reference

Prediction 0 1 2 3 4 5 6 7 8 9

0 5738 1 21 5 16 17 7 15 9 43

1 5 6632 21 24 25 3 2 33 13 392

2 12 32 5747 106 25 28 3 27 44 4779

3 0 27 12 5715 1 21 1 20 1 13

4 10 5 21 18 5677 9 17 30 15 166

5 142 21 96 136 93 5306 5884 43 60 413

6 0 0 0 0 0 0 0 0 0 0

7 6 9 13 13 3 4 0 6085 0 55

8 8 12 7 43 1 32 2 7 5703 69

9 2 3 20 71 1 1 2 5 6 19

Overall Statistics

Accuracy : 0.777

95% CI : (0.7737, 0.7804)

No Information Rate : 0.1124

P-Value \[Acc > NIR\] : < 2.2e-16

Kappa : 0.7524

Mcnemar's Test P-Value : NA

Statistics by Class:

Class: 0 Class: 1 Class: 2 Class: 3 Class: 4 Class: 5 Class: 6

Sensitivity 0.96877 0.9837 0.96459 0.93215 0.97176 0.97879

0.00000

Specificity 0.99752 0.9903 0.90644 0.99822 0.99463 0.87380

1.00000

Pos Pred Value 0.97718 0.9276 0.53198 0.98348 0.95124 0.43513

NaN

Neg Pred Value 0.99658 0.9979 0.99571 0.99232 0.99695 0.99759

0.90137

Prevalence 0.09872 0.1124 0.09930 0.10218 0.09737 0.09035

0.09863

Detection Rate 0.09563 0.1105 0.09578 0.09525 0.09462 0.08843

0.00000

Detection Prevalence 0.09787 0.1192 0.18005 0.09685 0.09947 0.20323

0.00000

Balanced Accuracy 0.98314 0.9870 0.93551 0.96518 0.98319 0.92629

0.50000

Class: 7 Class: 8 Class: 9

Sensitivity 0.9713 0.97471 0.0031938

Specificity 0.9981 0.99666 0.9979464

Pos Pred Value 0.9834 0.96924 0.1461538

Neg Pred Value 0.9967 0.99727 0.9009521

Prevalence 0.1044 0.09752 0.0991500

Detection Rate 0.1014 0.09505 0.0003167

Detection Prevalence 0.1031 0.09807 0.0021667

Balanced Accuracy 0.9847 0.98568 0.5005701

\# Confusion Matrix on the Training set xtest <- t(test$x) Xtest <- xtest\[,1:10000\]

ytest <-test$y ytest1 <- ytest\[1:10000\] ytest2 <- as.matrix(ytest1) Ytest=t(ytest2) Confusion Matrix and Statistics

Reference

Prediction 0 1 2 3 4 5 6 7 8 9

0 950 2 2 3 0 6 9 4 7 6

1 3 1110 4 2 9 0 3 12 5 74

2 2 6 965 21 9 14 5 16 12 789

3 1 2 9 908 2 16 0 21 2 6

4 0 1 9 5 938 1 8 6 8 39

5 19 5 25 35 20 835 929 8 54 67

6 0 0 0 0 0 0 0 0 0 0

7 4 4 7 10 2 4 0 952 5 6

8 1 5 8 14 2 16 2 3 876 21

9 0 0 3 12 0 0 2 6 5 1

Overall Statistics

Accuracy : 0.7535

 95% CI : (0.7449, 0.7619)

No Information Rate : 0.1135

P-Value \[Acc > NIR\] : < 2.2e-16

Kappa : 0.7262

Mcnemar's Test P-Value : NA

Statistics by Class:

Class: 0 Class: 1 Class: 2 Class: 3 Class: 4 Class: 5 Class: 6

Sensitivity 0.9694 0.9780 0.9351 0.8990 0.9552 0.9361 0.0000

Specificity 0.9957 0.9874 0.9025 0.9934 0.9915 0.8724 1.0000

Pos Pred Value 0.9606 0.9083 0.5247 0.9390 0.9241 0.4181 NaN

Neg Pred Value 0.9967 0.9972 0.9918 0.9887 0.9951 0.9929 0.9042

Prevalence 0.0980 0.1135 0.1032 0.1010 0.0982 0.0892 0.0958

Detection Rate 0.0950 0.1110 0.0965 0.0908 0.0938 0.0835 0.0000

Detection Prevalence 0.0989 0.1222 0.1839 0.0967 0.1015 0.1997

0.0000

Balanced Accuracy 0.9825 0.9827 0.9188 0.9462 0.9733 0.9043

0.5000

Class: 7 Class: 8 Class: 9

Sensitivity 0.9261 0.8994 0.0009911

Specificity 0.9953 0.9920 0.9968858

Pos Pred Value 0.9577 0.9241 0.0344828

Neg Pred Value 0.9916 0.9892 0.8989068

Prevalence 0.1028 0.0974 0.1009000

Detection Rate 0.0952 0.0876 0.0001000

Detection Prevalence 0.0994 0.0948 0.0029000

Balanced Accuracy 0.9607 0.9457 0.4989384

**3.3a Random dataset with sigmoid**

**activation – Octave**

The Octave code below uses the random data set used by

Python(data.csv). The code below implements a L-Layer Deep

Learning with Sigmoid Activation.

source("DL5functions.m")

\# Read the data

data=csvread("data.csv");

#Set up the data

X=data(:,1:2);

Y=data(:,3);

#Set the layer dimensions

\# 2 – 2 input features

\# 9 7 – 2 hidden layers with 9 and 7 activation units

\# 1 – 1 sigmoid activation at output layer

layersDimensions = \[2 9 7 1\]; #tanh=-0.5(ok),

\# Execute L-layer Deep Learning Network

\# with relu as hidden unit and sigmoid as output activation and

\# learning rate 0.1

\[weights biases costs\]=L\_Layer\_DeepModel(X', Y', layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",

learningRate = 0.1,

numIterations = 10000);

\# Plot cost vs iterations

plotCostVsIterations(10000,costs);

![Image 267](index-185_1.jpg)

**3.3b Spiral dataset with Softmax**

**activation – Octave**

The code below uses the spiral data set used by Python

above(spiral.csv). The code below implements a L-Layer Deep

Learning with Softmax Activation.

\# Read the data

data=csvread("spiral.csv");

\# Setup the data

X=data(:,1:2);

Y=data(:,3);

\# Set the number of features, number of hidden units in hidden layer and number of classess

numFeats=2; #No features

numHidden=100; # No of hidden units

numOutput=3; # No of classes

\# Set the layer dimensions

layersDimensions = \[numFeats numHidden numOutput\];

#Execute the L-Layer Deep Learning network with ‘relu’ activation

\# in the hidden layer and softmax activation unit at the output layer

\# with learning rate=0.1

\[weights biases costs\]=L\_Layer\_DeepModel(X', Y', layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="softmax",

learningRate = 0.1,

numIterations = 10000);

![Image 268](index-187_1.jpg)

**3.3c MNIST dataset with Softmax**

**activation – Octave**

The code below implements a L-Layer Deep Learning Network in

Octave with Softmax output activation unit, for classifying the 10

handwritten digits in the MNIST dataset. Unfortunately, Octave can only index to around 10000 training at a time, and I was getting an error ‘ *error: out of memory or dimension too large for Octave’s index* *type error: called from…*’, when I tried to create a batch size of 20000. So, I had to come with a work around to create a batch size of 10000 (randomly) and then use a mini-batch of 1000 samples and execute Stochastic Gradient Descent. The performance was good.

Octave takes about 15 minutes, on a batch size of 10000 and a mini batch of 1000.

\# Pseudo code that could be used since Octave only allows 10K batches

\# at a time

\# Randomly create weights

\[weights biases\] = initialize\_weights()

for i=1:k

\# Create a random permutation and create a random batch

permutation = randperm(10000);

X=trainX(permutation,:);

Y=trainY(permutation,:);

\# Compute weights from SGD and update weights in the next batch update

\[weights biases

costs\]=L\_Layer\_DeepModel\_SGD(X,Y,mini\_bactch=1000,weights, biases,...);

...

Endfor

\# Load the MNIST data

load('./mnist/mnist.txt.gz');

#Create a random permutatation from 60K

permutation = randperm(10000);

disp(length(permutation));

\# Use this 10K as the batch

X=trainX(permutation,:);

Y=trainY(permutation,:);

\# Set layer dimensions

\# 784 – Number of input features – 28 x28

\# 15 9 – 2 hidden layers with 15 and 9 activation units

\# 10 – 10 activation units at the output layer

layersDimensions=\[784, 15, 9, 10\];

\# Run Stochastic Gradient descent with batch size=10K and

mini\_batch\_size=1000

\# with ‘relu’ activation in hidden layer and ‘softmax’ activation at the output layer

\[weights biases costs\]=L\_Layer\_DeepModel\_SGD(X', Y', layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="softmax",

learningRate = 0.01,

mini\_batch\_size = 2000, num\_epochs = 5000);

![Image 269](index-190_1.jpg)

**4.Final thoughts**

Here are some of my final thoughts after working on Python, R and Octave in this series and in other projects

1\. Python, with its highly optimized numpy library, is ideally suited for creating Deep Learning Models, which have a lot of matrix manipulations. Python is a real workhorse when it comes to Deep Learning computations.

2\. R is somewhat clunky in comparison to its cousin Python in handling matrices or in returning multiple values. But R’s statistical libraries, dplyr, and ggplot are really superior to the Python peers.

Also, I find R handles dataframes, much better than Python.

3\. Octave is a no-nonsense, minimalist language which is very efficient in handling matrices. It is ideally suited for implementing Machine Learning and Deep Learning from scratch. But, Octave has its problems and cannot handle large matrix sizes, and also lacks the statistical libaries of R and Python. They possibly exist in its sibling, Matlab

**5.Conclusion**

Building a Deep Learning Network from scratch is quite challenging, time-consuming but nevertheless an exciting task. While the

statements in the different languages for manipulating matrices, summing up columns, finding columns which have ones don’t take more than a single statement, extreme care has to be taken to ensure that the statements work well for any dimension. The lessons learnt from creating L -Layer Deep Learning network are many and well worth it. Give it a try!

**6.**

**Initialization, regularization in**

**Deep Learning**

*“ Today you are You, that is truer than true. There is no one alive who* *is Youer than You.”*

Dr. Seuss

*“Explanations exist; they have existed for all time; there is always a* *well-known solution to every human problem — neat, plausible, and* *wrong.”*

H L Mencken

 

**1.Introduction**

In this 6th chapter of ‘Deep Learning from first principles’, I look at a couple of different initialization techniques used in Deep Learning, L2

regularization and the ‘dropout’ method. Specifically, I implement

“He” initialization” & “Xavier” Initialization.

In addition I also implement L2 regularization and finally dropout.

Hence, my generic L-Layer Deep Learning network includes these additional enhancements for enabling/disabling initialization methods, regularization or dropout in the algorithm. It already included sigmoid

& softmax output activation for binary and multi-class classification, besides allowing relu, tanh and sigmoid activation for hidden units.

The Python,R and Octave functions used in this chapter are

implemented in Appendix 6 - Initialization, regularization in Deep Learning

This code for Python, R and Octave can be cloned/downloaded

from Github at DeepLearningFromFirstPrinciples

(https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/master/Chap6-DLInitializationRegularization)

**2.Initialization techniques**

The usual initialization technique is to generate Gaussian or uniform random numbers and multiply it by a small value like 0.01. Two techniques which are used to speed up convergence is the ‘He’

[(https://www.cv-](https://www.cv-foundation.org/openaccess/content_iccv_2015/papers/He_Delving_Deep_into_ICCV_2015_paper.pdf)

[foundation.org/openaccess/content\_iccv\_2015/papers/He\_Delving\_De](https://www.cv-foundation.org/openaccess/content_iccv_2015/papers/He_Delving_Deep_into_ICCV_2015_paper.pdf)ep\_into\_ICCV\_2015\_paper.pdf

[initialization or Xavier (https://www.cv-](https://www.cv-foundation.org/openaccess/content_iccv_2015/papers/He_Delving_Deep_into_ICCV_2015_paper.pdf)

[foundation.org/openaccess/content\_iccv\_2015/papers/He\_Delving\_De](https://www.cv-foundation.org/openaccess/content_iccv_2015/papers/He_Delving_Deep_into_ICCV_2015_paper.pdf)ep\_into\_ICCV\_2015\_paper.pdf

. These initialization techniques enable gradient descent to converge faster.

**1.1a Default initialization – Python**

This technique just initializes the weights to small random values based on Gaussian or uniform distribution

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import sklearn.linear\_model

import pandas as pd

import sklearn

import sklearn.datasets

exec(open("DLfunctions61.py").read())

#Load the data

train\_X, train\_Y, test\_X, test\_Y = load\_dataset()

\# Set the layers dimensions

\# 2 – number of input features

\# 7 – 1 hidden layer 7 hidden units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = \[2,7,1\]

\# Train a L-layer deep learning network with random initialization

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.6

parameters = L\_Layer\_DeepModel(train\_X, train\_Y, layersDimensions, hiddenActivationFunc='relu', outputActivationFunc="sigmoid",learningRate =

0.6, num\_iterations = 9000, initType="default", print\_cost =

True,figure="fig1.png")

\# Clear the plot

plt.clf()

plt.close()

\# Plot the decision boundary

![Image 270](index-198_1.jpg)

![Image 271](index-198_2.jpg)

plot\_decision\_boundary(lambda x: predict(parameters, x.T), train\_X, train\_Y,str(0.6),figure1="fig2.png")

![Image 272](index-199_1.jpg)

**1.1b He initialization – Python**

[‘He’ initialization attributed to ‘He et al’ (https://www.cv-](https://www.cv-foundation.org/openaccess/content_iccv_2015/papers/He_Delving_Deep_into_ICCV_2015_paper.pdf)

[foundation.org/openaccess/content\_iccv\_2015/papers/He\_Delving\_De](https://www.cv-foundation.org/openaccess/content_iccv_2015/papers/He_Delving_Deep_into_ICCV_2015_paper.pdf)ep\_into\_ICCV\_2015\_paper.pdf

, multiplies the random weights by

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import sklearn.linear\_model

import pandas as pd

import sklearn

import sklearn.datasets

exec(open("DLfunctions61.py").read())

#Load the data

train\_X, train\_Y, test\_X, test\_Y = load\_dataset()

\# Set the layers dimensions

\# 2 – number of input features

\# 7 – 1 hidden layer 7 hidden units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = \[2,7,1\]

\# Train a L-layer deep learning network with He initialization

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.6

parameters = L\_Layer\_DeepModel(train\_X, train\_Y, layersDimensions, hiddenActivationFunc='relu', outputActivationFunc="sigmoid", learningRate

\=0.6, num\_iterations = 10000,initType="He",print\_cost =

True, figure="fig3.png")

\# Clear plot

plt.clf()

plt.close()

![Image 273](index-200_1.jpg)

\# Plot the decision boundary

plot\_decision\_boundary(lambda x: predict(parameters, x.T), train\_X, train\_Y,str(0.6),figure1="fig4.png")

![Image 274](index-201_1.jpg)

![Image 275](index-202_1.jpg)

**1.1c Xavier initialization – Python**

‘Xavier’ [(http://proceedings.mlr.press/v9/glorot10a/glorot10a.pdf](http://proceedings.mlr.press/v9/glorot10a/glorot10a.pdf)) initialization multiply the random weights by

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import sklearn.linear\_model

import pandas as pd

import sklearn

import sklearn.datasets

exec(open("DLfunctions61.py").read())

#Load the data

train\_X, train\_Y, test\_X, test\_Y = load\_dataset()

\# Set the layers dimensions

\# 2 – number of input features

\# 7 – 1 hidden layer 7 hidden units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = \[2,7,1\]

\# Train a L-layer Deep Learning network with Xavier initialization

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.6

parameters = L\_Layer\_DeepModel(train\_X, train\_Y, layersDimensions, hiddenActivationFunc='relu', outputActivationFunc="sigmoid", learningRate = 0.6,num\_iterations = 10000,

initType="Xavier",print\_cost = True,

figure="fig5.png")

\# Plot the decision boundary

plot\_decision\_boundary(lambda x: predict(parameters, x.T), train\_X,

![Image 276](index-203_1.jpg)

train\_Y,str(0.6),figure1="fig6.png")

![Image 277](index-204_1.jpg)

**1.2a Default initialization – R**

source("DLfunctions61.R")

#Load the data

z <- as.matrix(read.csv("circles.csv",header=FALSE)) x <- z\[,1:2\]

y <- z\[,3\]

X <- t(x)

Y <- t(y)

#Set the layer dimensions

\# 2 – number of input features

\# 11 – 1 hidden layer 11 hidden units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = c(2,11,1)

\# Train a L-layer deep learning network

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.5

retvals = L\_Layer\_DeepModel(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",

learningRate = 0.5,

numIterations = 8000,

initType="default",

print\_cost = True)

#Plot the cost vs iterations

iterations <- seq(0,8000,1000)

\# Plot cost vs iterations

costs=retvals$costs

df=data.frame(iterations,costs)

ggplot(df,aes(x=iterations,y=costs)) + geom\_point() + geom\_line(color="blue")

\+ ggtitle("Costs vs iterations") + xlab("No of iterations") + ylab("Cost")

![Image 278](index-206_1.jpg)

![Image 279](index-206_2.jpg)

\# Plot the decision boundary

plotDecisionBoundary(z,retvals,hiddenActivationFunc="relu",lr=0.5)

**1.2b He initialization – R**

The code for ‘He’ initialization in R is included below

\# He Initialization model for L layers

\# Input: List of units in each layer

\# Returns: Initial weights and biases matrices for all layers

\# He initialization multiplies the random numbers with

sqrt(2/layerDimensions\[previouslayer\])

HeInitializeDeepModel <- function(layerDimensions){

set.seed(2)

\# Initialize empty list

layerParams <- list()

\# Note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Indices in R start from 1

for(l in 2:length(layersDimensions)){

\# Initialize a matrix of small random numbers of size l x l-1

\# Create random numbers of size l x l-1

w=rnorm(layersDimensions\[l\]\*layersDimensions\[l-1\])

\# Create a weight matrix of size l x l-1 with this initial weights and

\# Add to list W1,W2... WL

\# He initialization - Divide by sqrt(2/layerDimensions\[previous layer\]) layerParams\[\[paste('W',l-1,sep="")\]\] =

matrix(w,nrow=layersDimensions\[l\],

ncol=layersDimensions\[l-

1\])\*sqrt(2/layersDimensions\[l-1\])

layerParams\[\[paste('b',l-1,sep="")\]\] = matrix(rep(0,layersDimensions\[l\]), nrow=layersDimensions\[l\],ncol=1)

}

 return(layerParams)

}

The code in R below uses He initialization to learn the data

source("DLfunctions61.R")

\# Load the data

z <- as.matrix(read.csv("circles.csv",header=FALSE)) x <- z\[,1:2\]

y <- z\[,3\]

X <- t(x)

Y <- t(y)

\# Set the layer dimensions

\# 2 – number of input features

\# 11 – 1 hidden layer 11 hidden units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = c(2,11,1)

\# Train a L-layer Deep learning network with He initialization

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.5

retvals = L\_Layer\_DeepModel(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",

learningRate = 0.5,

numIterations = 9000,

initType="He",

print\_cost = True)

#Plot the cost vs iterations

iterations <- seq(0,9000,1000)

costs=retvals$costs

df=data.frame(iterations,costs)

![Image 280](index-209_1.jpg)

ggplot(df,aes(x=iterations,y=costs)) + geom\_point() + geom\_line(color="blue")

\+ ggtitle("Costs vs iterations") + xlab("No of iterations") + ylab("Cost")

\# Plot the decision boundary

plotDecisionBoundary(z,retvals,hiddenActivationFunc="relu",0.5,lr=0.5)

![Image 281](index-210_1.jpg)

**1.2c Xavier initialization – R**

\## Xav initialization

\# Set the layer dimensions

\# 2 – number of input features

\# 11 – 1 hidden layer 11 hidden units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = c(2,11,1)

\# Train a deep learning network with Xavier initialization

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.5

retvals = L\_Layer\_DeepModel(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",

learningRate = 0.5,

numIterations = 9000,

initType="Xav",

print\_cost = True)

#Plot the cost vs iterations

iterations <- seq(0,9000,1000)

costs=retvals$costs

df=data.frame(iterations,costs)

ggplot(df,aes(x=iterations,y=costs)) + geom\_point() + geom\_line(color="blue")

\+ ggtitle("Costs vs iterations") + xlab("No of iterations") + ylab("Cost")

![Image 282](index-212_1.jpg)

\# Plot the decision boundary

plotDecisionBoundary(z,retvals,hiddenActivationFunc="relu",0.5)

![Image 283](index-213_1.jpg)

**1.3a Default initialization – Octave**

source("DL61functions.m")

\# Read the data

data=csvread("circles.csv");

X=data(:,1:2);

Y=data(:,3);

\# Set the layer dimensions

\# 2 – number of input features

\# 11 – 1 hidden layer 11 hidden units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = \[2 11 1\];

\# Train a L-layer deep learning network with deafault initialization

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.5

\[weights biases costs\]=L\_Layer\_DeepModel(X', Y', layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",

learningRate = 0.5,

lambd=0,

keep\_prob=1,

numIterations = 10000,

initType="default");

\# Plot cost vs iterations

plotCostVsIterations(10000,costs)

#Plot decision boundary

plotDecisionBoundary(data,weights, biases,keep\_prob=1,

hiddenActivationFunc="relu")

 

![Image 284](index-216_1.jpg)

![Image 285](index-217_1.jpg)

**1.3b He initialization – Octave**

source("DL61functions.m")

#Load data

data=csvread("circles.csv");

X=data(:,1:2);

Y=data(:,3);

\# Set the layer dimensions

\# 2 – number of input features

\# 11 – 1 hidden layer 11 hidden units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = \[2 11 1\];

\# Train a L-layer deep learning network with He initialization

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.5

\[weights biases costs\]=L\_Layer\_DeepModel(X', Y', layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",

learningRate = 0.5,

lambd=0,

keep\_prob=1,

numIterations = 8000,

initType="He");

\# Plot cost vs iterations

plotCostVsIterations(8000,costs)

#Plot decision boundary

plotDecisionBoundary(data,weights,

biases,keep\_prob=1,hiddenActivationFunc="relu")

![Image 286](index-219_1.jpg)

![Image 287](index-220_1.jpg)

**1.3c Xavier initialization – Octave**

The code snippet for Xavier initialization in Octave is shown below source("DL61functions.m")

\# Xavier Initialization for L layers

\# Input: List of units in each layer

\# Returns: Initial weights and biases matrices for all layers function \[W b\] = XavInitializeDeepModel(layerDimensions)

rand ("seed", 3);

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Create cell arrays for Weights and biases

for l =2:size(layerDimensions)(2)

W{l-1} = rand(layerDimensions(l),layerDimensions(l-1))\*

sqrt(1/layerDimensions(l-1)); # Multiply by .01

b{l-1} = zeros(layerDimensions(l),1);

endfor

end

The Octave code below uses Xavier initialization

source("DL61functions.m")

#Load data

data=csvread("circles.csv");

X=data(:,1:2);

Y=data(:,3);

#Set layer dimensions

\# 2 – number of input features

\# 11 – 1 hidden layer 11 hidden units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = \[2 11 1

\# Train a L-layer deep learning network with Xavier initialization

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.5

\[weights biases costs\]=L\_Layer\_DeepModel(X', Y', layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",

learningRate = 0.5,

lambd=0,

keep\_prob=1,

numIterations = 8000,

initType="Xav");

#Plot cost vs iterations

plotCostVsIterations(8000,costs)

\# Plot decision boundary

plotDecisionBoundary(data,weights,

biases,keep\_prob=1,hiddenActivationFunc="relu")

![Image 288](index-223_1.jpg)

![Image 289](index-224_1.jpg)

![Image 290](index-225_1.jpg)

**2.1a Regularization : Circles data –**

**Python**

The cross-entropy cost for Logistic classification is given as import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import sklearn.linear\_model

import pandas as pd

import sklearn

import sklearn.datasets

exec(open("DLfunctions61.py").read())

#Load the data

train\_X, train\_Y, test\_X, test\_Y = load\_dataset()

\# Set the layers dimensions

\# 2 – number of input features

\# 7 – 1 hidden layer 7 hidden units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = \[2,7,1\]

\# Train a L-layer deep learning network with default initialization

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.6

\# lambd=0.1

parameters = L\_Layer\_DeepModel(train\_X, train\_Y, layersDimensions, hiddenActivationFunc='relu', outputActivationFunc="sigmoid",learningRate =

0.6, lambd=0.1, num\_iterations = 9000, initType="default", print\_cost =

True,figure="fig7.png")

\# Clear the plot

![Image 291](index-226_1.jpg)

![Image 292](index-226_2.jpg)

plt.clf()

plt.close()

\# Plot the decision boundary

plot\_decision\_boundary(lambda x: predict(parameters, x.T), train\_X, train\_Y,str(0.6),figure1="fig8.png")

plt.clf()

plt.close()

**2.1b Regularization: Spiral data –**

**Python**

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import sklearn.linear\_model

import pandas as pd

import sklearn

import sklearn.datasets

exec(open("DLfunctions61.py").read())

N = 100 # number of points per class

D = 2 # dimensionality

K = 3 # number of classes

X = np.zeros((N\*K,D)) # data matrix (each row = single example) y = np.zeros(N\*K, dtype='uint8') # class labels

for j in range(K):

ix = range(N\*j,N\*(j+1))

r = np.linspace(0.0,1,N) # radius

t = np.linspace(j\*4,(j+1)\*4,N) + np.random.randn(N)\*0.2 # theta X\[ix\] = np.c\_\[r\*np.sin(t), r\*np.cos(t)\]

y\[ix\] = j

\# Plot the data

plt.scatter(X\[:, 0\], X\[:, 1\], c=y, s=40, cmap=plt.cm.Spectral) plt.clf()

plt.close()

#Set layer dimensions

\# 2 – number of input features

\# 100 – 1 hidden layer 100 hidden units

\# 3 –3 classes with softmax unit at the output layer

layersDimensions = \[2,100,3\]

y1=y.reshape(-1,1).T

![Image 293](index-228_1.jpg)

\# Train a L-layer deep learning network

\# hidden Activation function – relu

\# output activation function – softmax

\# learning rate – 1

\# lambd=1e-3

parameters = L\_Layer\_DeepModel(X.T, y1, layersDimensions,

hiddenActivationFunc='relu', outputActivationFunc="softmax", learningRate =

1,lambd=1e-3, num\_iterations = 5000, print\_cost = True,figure="fig9.png") plt.clf()

plt.close()

\# Plot decision boundary

W1=parameters\['W1'\]

b1=parameters\['b1'\]

W2=parameters\['W2'\]

b2=parameters\['b2'\]

plot\_decision\_boundary1(X, y1,W1,b1,W2,b2,figure2="fig10.png")

![Image 294](index-229_1.jpg)

**2.2a Regularization: Circles data – R**

source("DLfunctions61.R")

#Load data

df=read.csv("circles.csv",header=FALSE)

z <- as.matrix(read.csv("circles.csv",header=FALSE)) x <- z\[,1:2\]

y <- z\[,3\]

X <- t(x)

Y <- t(y)

#Set layer dimensions

\# 2 – number of input features

\# 11 – 1 hidden layer 11 hidden units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = c(2,11,1)

\# Train a L-layer deep learning network

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.6

\# lambd=0.1

retvals = L\_Layer\_DeepModel(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",

learningRate = 0.5,

lambd=0.1,

numIterations = 9000,

initType="default",

print\_cost = True)

#Plot the cost vs iterations

iterations <- seq(0,9000,1000)

costs=retvals$costs

df=data.frame(iterations,costs)

ggplot(df,aes(x=iterations,y=costs)) + geom\_point() + geom\_line(color="blue")

\+ ggtitle("Costs vs iterations") + xlab("No of iterations") + ylab("Cost")

![Image 295](index-231_1.jpg)

\# Plot the decision boundary

plotDecisionBoundary(z,retvals,hiddenActivationFunc="relu",0.5)

![Image 296](index-232_1.jpg)

**2.2b Regularization:Spiral data – R**

\# Read the spiral dataset

#Load the data

source("DLfunctions61.R")

Z <- as.matrix(read.csv("spiral.csv",header=FALSE))

\# Setup the data

X <- Z\[,1:2\]

y <- Z\[,3\]

X <- t(X)

Y <- t(y)

\# Set layer dimensions

layersDimensions = c(2, 100, 3)

\# 2 – number of input features

\# 100 – 1 hidden layer 100 hidden units

\# 3 – 3 softmax classes at the output layer

\# Train a L-layer deep learning network

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.5

\# lambd=0.01

retvals = L\_Layer\_DeepModel(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc="softmax",

learningRate = 0.5,

lambd=0.01,

numIterations = 9000,

print\_cost = True)

parameters<-retvals$parameters

#Plot decision boundary

plotDecisionBoundary1(Z,parameters)

![Image 297](index-234_1.jpg)

**2.3a Regularization: Circles data –**

**Octave**

#

source("DL61functions.m")

#Load data

data=csvread("circles.csv");

X=data(:,1:2);

Y=data(:,3);

\# Set layer dimensions

\# 2 – number of input features

\# 11 – 1 hidden layer 11 hidden units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = \[2 11 1\]; #tanh=-0.5(ok), #relu=0.1 best!

\# Train a L-layer deep learning network

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.5

\# lambd=0.2

\[weights biases costs\]=L\_Layer\_DeepModel(X', Y', layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",

learningRate = 0.5,

lambd=0.2,

keep\_prob=1,

numIterations = 8000,

initType="default");

#Plot cost vs iterations

plotCostVsIterations(8000,costs)

#Plot decision boundary

plotDecisionBoundary(data,weights,

biases,keep\_prob=1,hiddenActivationFunc="relu")

![Image 298](index-236_1.jpg)

![Image 299](index-237_1.jpg)

**2.3b Regularization:Spiral data 2 –**

**Octave**

#

source("DL61functions.m")

data=csvread("spiral.csv");

\# Setup the data

X=data(:,1:2);

Y=data(:,3);

\# Set layer dimensions

\# 2 – number of input features

\# 100 – 1 hidden layer 100 hidden units

\# 3 –3 classes with softmax activation unit at the output layer layersDimensions = \[2 100 3\]

\# Train a L-layer deep learning network

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.6

\# lambd=0.2

\[weights biases costs\]=L\_Layer\_DeepModel(X', Y', layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="softmax",

learningRate = 0.6,

lambd=0.2,

keep\_prob=1,

numIterations = 10000);

#Plot cost vs iterations

plotCostVsIterations(10000,costs)

#Plot decision boundary

plotDecisionBoundary1(data,weights,

biases,keep\_prob=1,hiddenActivationFunc="relu")

![Image 300](index-240_1.jpg)

![Image 301](index-241_1.jpg)

**3.1a Dropout: Circles data – Python**

The ‘dropout’ regularization technique was used with great

effectiveness, to prevent overfitting by Alex Krizhevsky, Ilya Sutskever and Prof Geoffrey E. Hinton in the ‘Imagenet classification with Deep Convolutional Neural Networks’

(https://www.nvidia.cn/content/tesla/pdf/machine-learning/imagenet-classification-with-deep-convolutional-nn.pdf)

The technique of dropout works by dropping a random set of

activation units in each hidden layer, based on a ‘keep\_prob’ criteria in the forward propagation cycle. Here is the code for Octave. A

‘dropoutMat’ is created for each layer which specifies which units to drop **Note**: The same ‘dropoutMat has to be used which computing the gradients in the backward propagation cycle. Hence the dropout matrices are stored in a cell array.

for l =1:L-1

...

D=rand(size(A)(1),size(A)(2));

D = (D < keep\_prob) ;

\# Zero out some hidden units

A= A .\* D;

\# Divide by keep\_prob to keep the expected value of A the

same

A = A ./ keep\_prob;

\# Store D in a dropoutMat cell array

dropoutMat{l}=D;

...

endfor

In the backward propagation cycle we have

for l =(L-1):-1:1

...

D = dropoutMat{l};

\# Zero out the dAl based on same dropout matrix

dAl= dAl .\* D;

\# Divide by keep\_prob to maintain the expected

value

dAl = dAl ./ keep\_prob;

...

endfor

#

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import sklearn.linear\_model

import pandas as pd

import sklearn

import sklearn.datasets

exec(open("DLfunctions61.py").read())

#Load the data

train\_X, train\_Y, test\_X, test\_Y = load\_dataset()

\# Set the layers dimensions

\# 2 – number of input features

\# 7 – 1 hidden layer 7 hidden units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = \[2,7,1\]

\# Train a L-layer deep learning network

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.6

#keep\_prob=0.7

parameters = L\_Layer\_DeepModel(train\_X, train\_Y, layersDimensions, hiddenActivationFunc='relu', outputActivationFunc="sigmoid",learningRate =

0.6, keep\_prob=0.7, num\_iterations = 9000, initType="default", print\_cost =

True,figure="fig11.png")

\# Clear the plot

plt.clf()

plt.close()

\# Plot the decision boundary

plot\_decision\_boundary(lambda x: predict(parameters, x.T,keep\_prob=0.7), train\_X, train\_Y,str(0.6),figure1="fig12.png")

![Image 302](index-245_1.jpg)

![Image 303](index-246_1.jpg)

**3.1b Dropout: Spiral data – Python**

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import sklearn.linear\_model

import pandas as pd

import sklearn

import sklearn.datasets

exec(open("DLfunctions61.py").read())

\# Create an input data set - Taken from CS231n Convolutional Neural networks,

\# http://cs231n.github.io/neural-networks-case-study/

N = 100 # number of points per class

D = 2 # dimensionality

K = 3 # number of classes

X = np.zeros((N\*K,D)) # data matrix (each row = single example) y = np.zeros(N\*K, dtype='uint8') # class labels

for j in range(K):

ix = range(N\*j,N\*(j+1))

r = np.linspace(0.0,1,N) # radius

t = np.linspace(j\*4,(j+1)\*4,N) + np.random.randn(N)\*0.2 # theta X\[ix\] = np.c\_\[r\*np.sin(t), r\*np.cos(t)\]

y\[ix\] = j

\# Plot the data

plt.scatter(X\[:, 0\], X\[:, 1\], c=y, s=40, cmap=plt.cm.Spectral) plt.clf()

plt.close()

#Set layer dimensions

\# 2 – number of input features

\# 100 – 1 hidden layer 100 hidden units

\# 3 –3 classes with softmax activation unit at the output layer layersDimensions = \[2,100,3\]

![Image 304](index-248_1.jpg)

y1=y.reshape(-1,1).T

\# Train a L-layer deep learning network

\# hidden Activation function – relu

\# output activation function – softmax

\# learning rate – 1

#keep\_prob=0.9

parameters = L\_Layer\_DeepModel(X.T, y1, layersDimensions,

hiddenActivationFunc='relu', outputActivationFunc="softmax", learningRate =

1,keep\_prob=0.9, num\_iterations = 5000, print\_cost = True,figure="fig13.png") plt.clf()

plt.close()

W1=parameters\['W1'\]

b1=parameters\['b1'\]

W2=parameters\['W2'\]

b2=parameters\['b2'\]

#Plot decision boundary

plot\_decision\_boundary1(X, y1,W1,b1,W2,b2,figure2="fig14.png")

![Image 305](index-249_1.jpg)

**3.2a Dropout: Circles data – R**

source("DLfunctions61.R")

#Load data

df=read.csv("circles.csv",header=FALSE)

z <- as.matrix(read.csv("circles.csv",header=FALSE)) x <- z\[,1:2\]

y <- z\[,3\]

X <- t(x)

Y <- t(y)

\# Set layer dimensions

\# 2 – number of input features

\# 11 – 1 hidden layer 11 hidden units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = c(2,11,1)

\# Train a L-layer deep learning network

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.5

\# keep\_prob=0.8

retvals = L\_Layer\_DeepModel(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",

learningRate = 0.5,

keep\_prob=0.8,

numIterations = 9000,

initType="default",

print\_cost = True)

\# Plot the decision boundary

plotDecisionBoundary(z,retvals,keep\_prob=0.6,

hiddenActivationFunc="relu",0.5)

![Image 306](index-251_1.jpg)

**3.2b Dropout: Spiral data – R**

\# Read the spiral dataset

source("DLfunctions61.R")

\# Load data

Z <- as.matrix(read.csv("spiral.csv",header=FALSE))

\# Setup the data

X <- Z\[,1:2\]

y <- Z\[,3\]

X <- t(X)

Y <- t(y)

\# Train a L-layer deep learning network

\# hidden Activation function – relu

\# output activation function – softmax

\# learning rate – 0.1

#keep\_prob=0.9

retvals = L\_Layer\_DeepModel(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc="softmax",

learningRate = 0.1,

keep\_prob=0.90,

numIterations = 9000,

print\_cost = True)

parameters<-retvals$parameters

#Plot decision boundary

plotDecisionBoundary1(Z,parameters)

![Image 307](index-253_1.jpg)

**3.3a Dropout: Circles data – Octave**

data=csvread("circles.csv");

X=data(:,1:2);

Y=data(:,3);

\# Set layer dimensions

\# 2 – number of input features

\# 11 – 1 hidden layer 11 hidden units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = \[2 11 1\];

\# Train a L-layer deep learning network

\# hidden Activation function – relu

\# output activation function – sigmoid

\# learning rate – 0.5

\# keep\_prob=0.8

\[weights biases costs\]=L\_Layer\_DeepModel(X', Y', layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",

learningRate = 0.5,

lambd=0,

keep\_prob=0.8,

numIterations = 10000,

initType="default");

#Plot cost vs iterations

plotCostVsIterations(10000,costs)

#Plot decision boundary

plotDecisionBoundary1(data,weights, biases,keep\_prob=1,

hiddenActivationFunc="relu")

![Image 308](index-256_1.jpg)

![Image 309](index-257_1.jpg)

**3.3b Dropout Spiral data – Octave**

source("DL61functions.m")

data=csvread("spiral.csv");

\# Setup the data

X=data(:,1:2);

Y=data(:,3);

\# Set layer dimensions

layersDimensions = \[numFeats numHidden numOutput\];

\# Train a L-layer deep learning network

\# hidden Activation function – relu

\# output activation function – softmax

\# learning rate – 0.1

#keep\_prob=0.8

\[weights biases costs\]=L\_Layer\_DeepModel(X', Y', layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="softmax",

learningRate = 0.1,

lambd=0,

keep\_prob=0.8,

numIterations = 10000);

#Plot cost vs iterations

plotCostVsIterations(10000,costs)

#Plot decision boundary

plotDecisionBoundary1(data,weights, biases,keep\_prob=1,

hiddenActivationFunc="relu")

![Image 310](index-259_1.jpg)

![Image 311](index-260_1.jpg)

**4\. Conclusion**

This post further enhances my earlier L-Layer generic implementation of a Deep Learning network to include options for initialization techniques, L2 regularization or dropout regularization

**7.**

Gradient Descent Optimization

techniques

*Artificial Intelligence is the new electricity. –* Prof Andrew Ng *Most of human and animal learning is unsupervised learning. If* *intelligence was a cake, unsupervised learning would be the cake,* *supervised learning would be the icing on the cake, and reinforcement* *learning would be the cherry on the cake. We know how to make the* *icing and the cherry, but we don’t know how to make the cake. We* *need to solve the unsupervised learning problem before we can even* *think of getting to true AI. –* Yann LeCun, March 14, 2016

(Facebook)

**1.Introduction**

In this chapter 7 of ‘Deep Learning from first principles, I implement optimization methods used in Stochastic Gradient Descent (SGD) to speed up the convergence. Specifically, I discuss and implement the following gradient descent optimization techniques

a. Vanilla Stochastic Gradient Descent

b. Learning rate decay

c. Momentum method

d. RMSProp

e. Adaptive Moment Estimation (Adam)

This chapter, further enhances my generic L-Layer Deep Learning Network implementations in vectorized Python, R and Octave to also include the Stochastic Gradient Descent optimization techniques.

These vectorized implementation are in Appendix 7 - Gradient

Descent Optimization techniques

You can clone/download the code from Github

at DeepLearningFromFirstPrinciples

(https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/master/Chap7-DLGradientDescentOptimization) Incidentally, a good discussion of the various optimizations methods used in Stochastic Gradient Optimization techniques can be seen at Sebastian Ruder’s blog

[(http://ruder.io/optimizing-gradient-descent/)](http://ruder.io/optimizing-gradient-descent/)

**Note**: The vectorized Python, R and Octave implementations in this chapter, only a 1024 random training samples were used. This was to reduce the computation time. You are free to use the entire data set (60000 training data) for the computation.

This chapter is largely based of on Prof Andrew Ng’s Deep Learning

![Image 312](index-264_1.jpg)

![Image 313](index-264_2.jpg)

![Image 314](index-264_3.jpg)

![Image 315](index-264_4.jpg)

![Image 316](index-264_5.jpg)

![Image 317](index-264_6.jpg)

![Image 318](index-264_7.jpg)

![Image 319](index-264_8.jpg)

![Image 320](index-264_9.jpg)

![Image 321](index-264_10.jpg)

![Image 322](index-264_11.jpg)

![Image 323](index-264_12.jpg)

![Image 324](index-264_13.jpg)

![Image 325](index-264_14.jpg)

![Image 326](index-264_15.jpg)

![Image 327](index-264_16.jpg)

[Specialization (https://www.coursera.org/specializations/deep-](https://www.coursera.org/specializations/deep-learning)

[learning). All the optimization techniques discussed here use](https://www.coursera.org/specializations/deep-learning)

Stochastic Gradient Descent and are based on the technique of exponentially weighted average method. So, for example if we had some time series data

then we can represent the

exponentially average value at time ‘t’ as a sequence of the previous value

and as shown below

Here represent the average of the data set over

By choosing

different values of , we can average over a larger or smaller number of the data points.

We can write the equations as follows

and

By substitution we have

Hence it can be seen that the is the weighted sum over the previous values

, which is an exponentially decaying function.

**1.1a. Stochastic Gradient Descent**

**(Vanilla) – Python**

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import sklearn.linear\_model

import pandas as pd

import sklearn

import sklearn.datasets

exec(open("DLfunctions7.py").read())

exec(open("load\_mnist.py").read())

\# Read the MNIST training data and labels

training=list(read(dataset='training',path=".\\\\mnist")) test=list(read(dataset='testing',path=".\\\\mnist"))

lbls=\[\]

pxls=\[\]

#Loop

for i in range(60000):

l,p=training\[i\]

lbls.append(l)

pxls.append(p)

labels= np.array(lbls)

pixels=np.array(pxls)

y=labels.reshape(-1,1)

X=pixels.reshape(pixels.shape\[0\],-1)

X1=X.T

Y1=y.T

\# Create a list of 1024 random numbers.

permutation = list(np.random.permutation(2\*\*10))

\# Subset 1024 training samples from the data

X2 = X1\[:, permutation\]

![Image 328](index-266_1.jpg)

Y2 = Y1\[:, permutation\].reshape((1,2\*\*10))

\# Set the layer dimensions

\# 784 – number of input features (28 x28)

\# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively

\# 10 – 10 output classes with softmax activation unit at the output layer layersDimensions=\[784, 15,9,10\]

\# Execute the L-Layer Deep Network to perform SGD with regular gradient descent

\# hidden Activation function – relu

\# output activation function – softmax

\# learning rate – 0.01

\# optimizer="gd" # gradient descent

\# mini\_batch\_size = 512

parameters = L\_Layer\_DeepModel\_SGD(X2, Y2, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc="softmax",learningRate = 0.01 , optimizer="gd", mini\_batch\_size =512, num\_epochs =

1000, print\_cost = True,figure="fig1.png")

**1.1b. Stochastic Gradient Descent**

**(Vanilla) – R**

source("mnist.R")

source("DLfunctions7.R")

#Load and read MNIST data

load\_mnist()

x <- t(train$x)

X <- x\[,1:60000\]

y <-train$y

y1 <- y\[1:60000\]

y2 <- as.matrix(y1)

Y=t(y2)

\# Subset 1024 random samples from MNIST

permutation = c(sample(2^10))

\# Randomly shuffle the training data

X1 = X\[, permutation\]

y1 = Y\[1, permutation\]

y2 <- as.matrix(y1)

Y1=t(y2)

\# Set layer dimensions

\# 784 – number of input features (28 x28)

\# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively

\# 10 – 10 output classes with softmax activation unit at the output layer layersDimensions=c(784, 15,9, 10)

\# Execute the L-Layer Deep Network to perform SGD with regular gradient descent

\# hidden Activation function – tanh

\# output activation function – softmax

\# learning rate – 0.05

\# optimizer="gd" # gradient descent

![Image 329](index-268_1.jpg)

\# mini\_batch\_size = 512

retvalsSGD= L\_Layer\_DeepModel\_SGD(X1, Y1, layersDimensions,

hiddenActivationFunc='tanh',

outputActivationFunc="softmax",

learningRate = 0.05,

optimizer="gd",

mini\_batch\_size = 512,

num\_epochs = 5000,

print\_cost = True)

#Plot the cost vs number of epochs

iterations <- seq(0,5000,1000)

costs=retvalsSGD$costs

df=data.frame(iterations,costs)

ggplot(df,aes(x=iterations,y=costs)) + geom\_point() + geom\_line(color="blue")

\+ ggtitle("Costs vs no of epochs") + xlab("No of epochss") + ylab("Cost")

**1.1c. Stochastic Gradient Descent**

**(Vanilla) – Octave**

source("DL7functions.m")

#Load and read MNIST

load('./mnist/mnist.txt.gz');

#Create a random permutatation from 1024

permutation = randperm(1024);

disp(length(permutation));

\# Use this 1024 as the mini-batch

X=trainX(permutation,:);

Y=trainY(permutation,:);

\# Set layer dimensions

\# 784 – number of input features (28 x28)

\# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively

\# 10 – 10 output classes with softmax activation unit at the output layer layersDimensions=\[784, 15, 9, 10\];

\# Execute the L-Layer Deep Network to perform SGD with regular gradient descent

\# hidden Activation function – relu

\# output activation function – softmax

\# learning rate – 0.005

\# optimizer="gd" # gradient descent

\# mini\_batch\_size = 512

\[weights biases costs\]=L\_Layer\_DeepModel\_SGD(X', Y', layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="softmax",

learningRate = 0.005,

lrDecay=true,

decayRate=1,

lambd=0,

keep\_prob=1,

optimizer="gd",

beta=0.9,

beta1=0.9,

beta2=0.999,

epsilon=10^-8,

mini\_batch\_size = 512,

num\_epochs = 5000);

#Plot cost vs number epochs

plotCostVsEpochs(5000,costs);

![Image 330](index-271_1.jpg)

![Image 331](index-272_1.jpg)

![Image 332](index-272_2.jpg)

![Image 333](index-272_3.jpg)

**2.1. Stochastic Gradient Descent with**

**Learning rate decay**

Since in Stochastic Gradient Descent, with each epoch, we use slight different samples, the gradient descent algorithm, oscillates across the ravines and wanders around the minima, when a fixed learning rate is used. In this technique of ‘learning rate decay’ the learning rate is slowly decreased with the number of epochs and becomes smaller and smaller, so that gradient descent can take smaller steps towards the minima.

There are several techniques employed in learning rate decay

a) Exponential decay:

b) 1/t decay:

c)

In my implementation I have used the ‘exponential decay’. The code snippet for Python is shown below

if lrDecay == True:

#decay the learning rate exponentially

learningRate = np.power(decayRate,(num\_epochs/1000)) \* learningRate

**2.1a. Stochastic Gradient Descent with**

**Learning rate decay – Python**

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import sklearn.linear\_model

import pandas as pd

import sklearn

import sklearn.datasets

exec(open("DLfunctions7.py").read())

exec(open("load\_mnist.py").read())

\# Read the MNIST data

training=list(read(dataset='training',path=".\\\\mnist")) test=list(read(dataset='testing',path=".\\\\mnist"))

lbls=\[\]

pxls=\[\]

for i in range(60000):

l,p=training\[i\]

lbls.append(l)

pxls.append(p)

labels= np.array(lbls)

pixels=np.array(pxls)

y=labels.reshape(-1,1)

X=pixels.reshape(pixels.shape\[0\],-1)

X1=X.T

Y1=y.T

\# Create a list of random numbers of 1024

permutation = list(np.random.permutation(2\*\*10))

\# Subset 1024 from the data

X2 = X1\[:, permutation\]

Y2 = Y1\[:, permutation\].reshape((1,2\*\*10))

![Image 334](index-274_1.jpg)

\# Set layer dimensions

\# 784 – number of input features (28 x28)

\# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively

\# 10 – 10 output classes with softmax activation unit at the output layer layersDimensions=\[784, 15,9,10\]

\# Execute the L-layer Deep Learning network using SGD with learning rate decay

\# hidden Activation function – relu

\# output activation function – softmax

\# learning rate – 0.01

\# lrDecay=True

\# decayRate=0.9999

\# optimizer="gd" # gradient descent

\# mini\_batch\_size = 512

parameters = L\_Layer\_DeepModel\_SGD(X2, Y2, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc="softmax", learningRate = 0.01 , lrDecay=True, decayRate=0.9999, optimizer="gd", mini\_batch\_size =512, num\_epochs = 1000, print\_cost =

True,figure="fig2.png")

**2.1b. Stochastic Gradient Descent with**

**Learning rate decay – R**

source("mnist.R")

source("DLfunctions7.R")

\# Read and load MNIST

load\_mnist()

x <- t(train$x)

X <- x\[,1:60000\]

y <-train$y

y1 <- y\[1:60000\]

y2 <- as.matrix(y1)

Y=t(y2)

\# Subset 1024 random samples from MNIST

permutation = c(sample(2^10))

\# Randomly shuffle the training data

X1 = X\[, permutation\]

y1 = Y\[1, permutation\]

y2 <- as.matrix(y1)

Y1=t(y2)

\# Set layer dimensions

\# 784 – number of input features (28 x28)

\# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively

\# 10 – 10 output classes with softmax activation unit at the output layer layersDimensions=c(784, 15,9, 10)

\# Execute the L-layer Deep Learning network using SGD with learning rate decay

\# hidden Activation function – tanh

\# output activation function – softmax

\# learning rate – 0.05

\# lrDecay=TRUE

\# decayRate=0.9999

\# optimizer="gd" # gradient descent

\# mini\_batch\_size = 512

retvalsSGD= L\_Layer\_DeepModel\_SGD(X1, Y1, layersDimensions,

hiddenActivationFunc='tanh',

outputActivationFunc="softmax",

learningRate = 0.05,

lrDecay=TRUE,

decayRate=0.9999,

optimizer="gd",

mini\_batch\_size = 512,

num\_epochs = 5000,

print\_cost = True)

#Plot the cost vs number of epochs

iterations <- seq(0,5000,1000)

costs=retvalsSGD$costs

df=data.frame(iterations,costs)

ggplot(df,aes(x=iterations,y=costs)) + geom\_point() + geom\_line(color="blue")

\+ ggtitle("Costs vs number of epochs") + xlab("No of epochs") + ylab("Cost")

![Image 335](index-277_1.jpg)

**2.1c. Stochastic Gradient Descent with**

**Learning rate decay – Octave**

source("DL7functions.m")

#Load and read MNIST

load('./mnist/mnist.txt.gz');

#Create a random permutatation from 1024

permutation = randperm(1024);

disp(length(permutation));

\# Use this 1024 as the batch

X=trainX(permutation,:);

Y=trainY(permutation,:);

\# Set layer dimensions

\# 784 – number of input features (28 x28)

\# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively

\# 10 – 10 output classes with softmax activation unit at the output layer layersDimensions=\[784, 15, 9, 10\];

\# Execute the L-layer Deep Learning network using SGD with learning rate decay

\# hidden Activation function – relu

\# output activation function – softmax

\# learning rate – 0.01

\# lrDecay=true

\# decayRate=0.999

\# optimizer="gd" # gradient descent

\# mini\_batch\_size = 512

\[weights biases costs\]=L\_Layer\_DeepModel\_SGD(X', Y', layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="softmax",

learningRate = 0.01,

lrDecay=true,

decayRate=0.999,

lambd=0,

keep\_prob=1,

optimizer="gd",

beta=0.9,

beta1=0.9,

beta2=0.999,

epsilon=10^-8,

mini\_batch\_size = 512,

num\_epochs = 5000);

\# Plot cost vs number of epochs

plotCostVsEpochs(5000,costs)

![Image 336](index-280_1.jpg)

![Image 337](index-281_1.jpg)

![Image 338](index-281_2.jpg)

![Image 339](index-281_3.jpg)

![Image 340](index-281_4.jpg)

![Image 341](index-281_5.jpg)

![Image 342](index-281_6.jpg)

**3.1. Stochastic Gradient Descent with**

**Momentum**

Stochastic Gradient Descent with Momentum uses the exponentially weighted average method discussed above and hence moves faster into the ravine than across it. The equations are

where

and

are the momentum terms which are exponentially

weighted with the corresponding gradients ‘dW’ and ‘db’ at the corresponding layer ‘l’ The code snippet for Stochastic Gradient Descent with momentum in R is shown below

\# Perform Gradient Descent with momentum

\# Input : Weights and biases

\# : beta

\# : gradients

\# : learning rate

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

#output : Updated weights after 1 iteration

gradientDescentWithMomentum <- function(parameters, gradients,v, beta, learningRate,outputActivationFunc="sigmoid"){

L = length(parameters)/2 # number of layers in the neural network

\# Update rule for each parameter. Use a for loop.

for(l in 1:(L-1)){

\# Compute velocities

\# v\['dWk'\] = beta \*v\['dWk'\] + (1-beta)\*dWk

v\[\[paste("dW",l, sep="")\]\] = beta\*v\[\[paste("dW",l, sep="")\]\] +

 (1-beta) \* gradients\[\[paste('dW',l,sep="")\]\]

v\[\[paste("db",l, sep="")\]\] = beta\*v\[\[paste("db",l, sep="")\]\] +

(1-beta) \* gradients\[\[paste('db',l,sep="")\]\]

#Update parameters with velocities

parameters\[\[paste("W",l,sep="")\]\] = parameters\[\[paste("W",l,sep="")\]\] -

learningRate\* v\[\[paste("dW",l, sep="")\]\]

parameters\[\[paste("b",l,sep="")\]\] = parameters\[\[paste("b",l,sep="")\]\] -

learningRate\* v\[\[paste("db",l, sep="")\]\]

}

\# Compute for the Lth layer if output activation is sigmoid

if(outputActivationFunc=="sigmoid"){

v\[\[paste("dW",L, sep="")\]\] = beta\*v\[\[paste("dW",L, sep="")\]\] +

(1-beta) \* gradients\[\[paste('dW',L,sep="")\]\]

v\[\[paste("db",L, sep="")\]\] = beta\*v\[\[paste("db",L, sep="")\]\] +

(1-beta) \* gradients\[\[paste('db',L,sep="")\]\]

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* v\[\[paste("dW",l, sep="")\]\]

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* v\[\[paste("db",l, sep="")\]\]

}else if (outputActivationFunc=="softmax"){ #If output activation is Softmax v\[\[paste("dW",L, sep="")\]\] = beta\*v\[\[paste("dW",L, sep="")\]\] +

(1-beta) \* t(gradients\[\[paste('dW',L,sep="")\]\])

v\[\[paste("db",L, sep="")\]\] = beta\*v\[\[paste("db",L, sep="")\]\] +

(1-beta) \* t(gradients\[\[paste('db',L,sep="")\]\])

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* t(gradients\[\[paste("dW",L,sep="")\]\]) parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* t(gradients\[\[paste("db",L,sep="")\]\])

}

return(parameters)

}

**3.1a. Stochastic Gradient Descent with**

**Momentum- Python**

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import sklearn.linear\_model

import pandas as pd

import sklearn

import sklearn.datasets

\# Read and load data and labels

exec(open("DLfunctions7.py").read())

exec(open("load\_mnist.py").read())

training=list(read(dataset='training',path=".\\\\mnist")) test=list(read(dataset='testing',path=".\\\\mnist"))

lbls=\[\]

pxls=\[\]

for i in range(60000):

l,p=training\[i\]

lbls.append(l)

pxls.append(p)

labels= np.array(lbls)

pixels=np.array(pxls)

y=labels.reshape(-1,1)

X=pixels.reshape(pixels.shape\[0\],-1)

X1=X.T

Y1=y.T

\# Create a list of random numbers of 1024

permutation = list(np.random.permutation(2\*\*10))

\# Subset 1024 random samples from the data

X2 = X1\[:, permutation\]

Y2 = Y1\[:, permutation\].reshape((1,2\*\*10))

\# Set layer dimensions

![Image 343](index-285_1.jpg)

\# 784 – number of input features (28 x28)

\# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively

\# 10 – 10 output classes with softmax activation unit at the output layer layersDimensions=\[784, 15,9,10\]

\# Execute the L-Layer Deep Learning network using SGD with momentum

\# hidden Activation function – relu

\# output activation function – softmax

\# learning rate – 0.01

\# optimizer="momentum”

\# beta =0.9

\# mini\_batch\_size = 512

parameters = L\_Layer\_DeepModel\_SGD(X2, Y2, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc="softmax",learningRate = 0.01 , optimizer="momentum", beta=0.9, mini\_batch\_size =512, num\_epochs = 1000, print\_cost = True,figure="fig3.png")

**3.1b. Stochastic Gradient Descent with**

**Momentum- R**

source("mnist.R")

source("DLfunctions7.R")

load\_mnist()

x <- t(train$x)

X <- x\[,1:60000\]

y <-train$y

y1 <- y\[1:60000\]

y2 <- as.matrix(y1)

Y=t(y2)

\# Subset 1024 random samples from MNIST

permutation = c(sample(2^10))

\# Randomly shuffle the training data

X1 = X\[, permutation\]

y1 = Y\[1, permutation\]

y2 <- as.matrix(y1)

Y1=t(y2)

\# Set layer dimensions

\# 784 – number of input features (28 x28)

\# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively

\# 10 – 10 output classes with softmax activation unit at the output layer layersDimensions=c(784, 15,9, 10)

\# Execute the L-Layer Deep Learning network using SGD with momentum

\# hidden Activation function – tanh

\# output activation function – softmax

\# learning rate – 0.05

\# optimizer="momentum”

\# beta =0.9

\# mini\_batch\_size = 512

retvalsSGD= L\_Layer\_DeepModel\_SGD(X1, Y1, layersDimensions,

![Image 344](index-287_1.jpg)

hiddenActivationFunc='tanh',

outputActivationFunc="softmax",

learningRate = 0.05,

optimizer="momentum",

beta=0.9,

mini\_batch\_size = 512,

num\_epochs = 5000,

print\_cost = True)

#Plot the cost vs number of epochs

iterations <- seq(0,5000,1000)

costs=retvalsSGD$costs

df=data.frame(iterations,costs)

ggplot(df,aes(x=iterations,y=costs)) + geom\_point() + geom\_line(color="blue")

\+ ggtitle("Costs vs number of epochs") + xlab("No of epochs") + ylab("Cost")

**3.1c. Stochastic Gradient Descent with**

**Momentum- Octave**

source("DL7functions.m")

#Load and read MNIST

load('./mnist/mnist.txt.gz');

#Create a random permutatation from 60K

permutation = randperm(1024);

disp(length(permutation));

\# Use this 1024 as the batch

X=trainX(permutation,:);

Y=trainY(permutation,:);

\# Set layer dimensions

\# 784 – number of input features (28 x28)

\# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively

\# 10 – 10 output classes with softmax activation unit at the output layer layersDimensions=\[784, 15, 9, 10\];

\# Execute the L-Layer Deep Learning network using SGD with momentum

\# hidden Activation function – relu

\# output activation function – softmax

\# learning rate – 0.01

\# optimizer="momentum”

\# beta =0.9

\# mini\_batch\_size = 512

\[weights biases costs\]=L\_Layer\_DeepModel\_SGD(X', Y', layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="softmax",

learningRate = 0.01,

lrDecay=false,

decayRate=1,

lambd=0,

keep\_prob=1,

optimizer="momentum",

beta=0.9,

beta1=0.9,

beta2=0.999,

epsilon=10^-8,

mini\_batch\_size = 512,

num\_epochs = 5000);

#Plot the cost vs number of epochs

plotCostVsEpochs(5000,costs)

![Image 345](index-290_1.jpg)

![Image 346](index-291_1.jpg)

![Image 347](index-291_2.jpg)

![Image 348](index-291_3.jpg)

![Image 349](index-291_4.jpg)

![Image 350](index-291_5.jpg)

![Image 351](index-291_6.jpg)

**4.1. Stochastic Gradient Descent with**

**RMSProp**

Stochastic Gradient Descent with RMSProp tries to move faster towards the minima while dampening the oscillations across the ravine.

The equations are

where

and

are the RMSProp terms which are exponentially

weighted with the corresponding gradients ‘dW’ and ‘db’ at the corresponding layer ‘l’

The code snippet in Octave is shown below

\# Update parameters with RMSProp

\# Input : parameters

\# : gradients

\# : s

\# : beta

\# : learningRate

#output : Updated parameters RMSProp

function \[weights biases\] = gradientDescentWithRMSProp(weights, biases,gradsDW,gradsDB, sdW, sdB, beta1, epsilon,

learningRate,outputActivationFunc="sigmoid")

L = size(weights)(2); # number of layers in the neural network

\# Update rule for each parameter.

 for l=1:(L-1)

sdW{l} = beta1\*sdW{l} + (1 -beta1) \* gradsDW{l} .\* gradsDW{l}; sdB{l} = beta1\*sdB{l} + (1 -beta1) \* gradsDB{l} .\* gradsDB{l}; weights{l} = weights{l} - learningRate\* gradsDW{l} ./ sqrt(sdW{l} +

epsilon);

biases{l} = biases{l} - learningRate\* gradsDB{l} ./ sqrt(sdB{l} + epsilon); endfor

#Update for Lth layer is output is sigmoid

if (strcmp(outputActivationFunc,"sigmoid"))

sdW{L} = beta1\*sdW{L} + (1 -beta1) \* gradsDW{L} .\* gradsDW{L}; sdB{L} = beta1\*sdB{L} + (1 -beta1) \* gradsDB{L} .\* gradsDB{L}; weights{L} = weights{L} -learningRate\* gradsDW{L} ./ sqrt(sdW{L}

+epsilon);

biases{L} = biases{L} -learningRate\* gradsDB{L} ./ sqrt(sdB{L} +

epsilon);

elseif (strcmp(outputActivationFunc,"softmax")) #Update for Lth layer is output is softmax

sdW{L} = beta1\*sdW{L} + (1 -beta1) \* gradsDW{L}' .\* gradsDW{L}'; sdB{L} = beta1\*sdB{L} + (1 -beta1) \* gradsDB{L}' .\* gradsDB{L}'; weights{L} = weights{L} -learningRate\* gradsDW{L}' ./ sqrt(sdW{L}

+epsilon);

biases{L} = biases{L} -learningRate\* gradsDB{L}' ./ sqrt(sdB{L} +

epsilon);

endif

end

**4.1a. Stochastic Gradient Descent with**

**RMSProp – Python**

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import sklearn.linear\_model

import pandas as pd

import sklearn

import sklearn.datasets

exec(open("DLfunctions7.py").read())

exec(open("load\_mnist.py").read())

\# Read and load MNIST

training=list(read(dataset='training',path=".\\\\mnist")) test=list(read(dataset='testing',path=".\\\\mnist"))

lbls=\[\]

pxls=\[\]

for i in range(60000):

l,p=training\[i\]

lbls.append(l)

pxls.append(p)

labels= np.array(lbls)

pixels=np.array(pxls)

y=labels.reshape(-1,1)

X=pixels.reshape(pixels.shape\[0\],-1)

X1=X.T

Y1=y.T

print("X1=",X1.shape)

print("y1=",Y1.shape)

\# Create a list of random numbers of 1024

permutation = list(np.random.permutation(2\*\*10))

\# Subset 1024 from the data

X2 = X1\[:, permutation\]

![Image 352](index-294_1.jpg)

Y2 = Y1\[:, permutation\].reshape((1,2\*\*10))

\# Set layer dimensions

\# 784 – number of input features (28 x28)

\# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively

\# 10 – 10 output classes with softmax activation unit at the output layer layersDimensions=\[784, 15,9,10\]

\# Execute the L-layer Deep learning network using SGD with RMSProp

\# hidden Activation function – relu

\# output activation function – softmax

\# learning rate – 0.01

\# optimizer=”rmsprop”

\# beta1 =0.7

\# epsilon=1e-8

\# mini\_batch\_size = 512

parameters = L\_Layer\_DeepModel\_SGD(X2, Y2, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc="softmax",learningRate = 0.01 , optimizer="rmsprop", beta1=0.7, epsilon=1e-8,

mini\_batch\_size =512, num\_epochs = 1000, print\_cost =

True,figure="fig4.png")

**4.1b. Stochastic Gradient Descent with**

**RMSProp – R**

source("mnist.R")

source("DLfunctions7.R")

load\_mnist()

x <- t(train$x)

X <- x\[,1:60000\]

y <-train$y

y1 <- y\[1:60000\]

y2 <- as.matrix(y1)

Y=t(y2)

\# Subset 1024 random samples from MNIST

permutation = c(sample(2^10))

\# Randomly shuffle the training data

X1 = X\[, permutation\]

y1 = Y\[1, permutation\]

y2 <- as.matrix(y1)

Y1=t(y2)

\# Set layer dimensions

\# 784 – number of input features (28 x28)

\# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively

\# 10 – 10 output classes with softmax activation unit at the output layer layersDimensions=c(784, 15,9, 10)

\# Execute the L-layer Deep learning network using SGD with RMSProp

\# hidden Activation function – tanh

\# output activation function – softmax

\# learning rate – 0.001

\# optimizer=”rmsprop”

\# beta1 =0.9

\# epsilon=1e-8

\# mini\_batch\_size = 512

![Image 353](index-296_1.jpg)

retvalsSGD= L\_Layer\_DeepModel\_SGD(X1, Y1, layersDimensions,

hiddenActivationFunc='tanh',

outputActivationFunc="softmax",

learningRate = 0.001,

optimizer="rmsprop",

beta1=0.9,

epsilon=10^-8,

mini\_batch\_size = 512,

num\_epochs = 5000 ,

print\_cost = True)

#Plot the cost vs number of epochs

iterations <- seq(0,5000,1000)

costs=retvalsSGD$costs

df=data.frame(iterations,costs)

ggplot(df,aes(x=iterations,y=costs)) + geom\_point() + geom\_line(color="blue")

\+ ggtitle("Costs vs number of epochs") + xlab("No of epochs") + ylab("Cost")

**4.1c. Stochastic Gradient Descent with**

**RMSProp – Octave**

source("DL7functions.m")

load('./mnist/mnist.txt.gz');

#Create a random permutatation from 1024

permutation = randperm(1024);

\# Use this 1024 as the batch

X=trainX(permutation,:);

Y=trainY(permutation,:);

\# Set layer dimensions

\# Set layer dimensions

\# 784 – number of input features (28 x28)

\# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively

\# 10 – 10 output classes with softmax activation unit at the output layer layersDimensions=\[784, 15, 9, 10\];

\# Execute the L-layer Deep learning network using SGD with RMSProp

\# hidden Activation function – relu

\# output activation function – softmax

\# learning rate – 0.005

\# optimizer=”rmsprop”

\# beta1 =0.9

\# epsilon=1

\# mini\_batch\_size = 512

\[weights biases costs\]=L\_Layer\_DeepModel\_SGD(X', Y', layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="softmax",

learningRate = 0.005,

lrDecay=false,

decayRate=1,

lambd=0,

keep\_prob=1,

optimizer="rmsprop",

beta=0.9,

beta1=0.9,

beta2=0.999,

epsilon=1,

mini\_batch\_size = 512,

num\_epochs = 5000);

#Plot cost vs number of epochs

plotCostVsEpochs(5000,costs)

![Image 354](index-299_1.jpg)

![Image 355](index-300_1.jpg)

![Image 356](index-300_2.jpg)

![Image 357](index-300_3.jpg)

![Image 358](index-300_4.jpg)

![Image 359](index-300_5.jpg)

![Image 360](index-300_6.jpg)

![Image 361](index-300_7.jpg)

![Image 362](index-300_8.jpg)

![Image 363](index-300_9.jpg)

![Image 364](index-300_10.jpg)

**5.1. Stochastic Gradient Descent with**

**Adam**

Adaptive Moment Estimate is a combination of the momentum (1st moment) and RMSProp (2nd moment). The equations for Adam are

below

The moving average for the 1st moment

The bias corrections for the 1st moment

Similarly, the moving average for the 2nd moment- RMSProp

The bias corrections for the 2nd moment

The Adam Gradient Descent is given by

The code snippet of Adam in R is included be

\# Perform Gradient Descent with Adam

\# Input : Weights and biases

\# : beta1

\# : epsilon

\# : gradients

\# : learning rate

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

#output : Updated weights after 1 iteration

gradientDescentWithAdam <- function(parameters, gradients,v, s, t, beta1=0.9, beta2=0.999, epsilon=10^-8,

learningRate=0.1,outputActivationFunc="sigmoid"){

L = length(parameters)/2 # number of layers in the neural network v\_corrected <- list()

s\_corrected <- list()

\# Update rule for each parameter.

for(l in 1:(L-1)){

\# v\['dWk'\] = beta \*v\['dWk'\] + (1-beta)\*dWk

v\[\[paste("dW",l, sep="")\]\] = beta1\*v\[\[paste("dW",l, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('dW',l,sep="")\]\]

v\[\[paste("db",l, sep="")\]\] = beta1\*v\[\[paste("db",l, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('db',l,sep="")\]\]

\# Compute bias-corrected first moment estimate.

v\_corrected\[\[paste("dW",l, sep="")\]\] = v\[\[paste("dW",l, sep="")\]\]/(1-beta1^t)

v\_corrected\[\[paste("db",l, sep="")\]\] = v\[\[paste("db",l, sep="")\]\]/(1-beta1^t)

\# Element wise multiply of gradients

s\[\[paste("dW",l, sep="")\]\] = beta2\*s\[\[paste("dW",l, sep="")\]\] +

(1-beta2) \* gradients\[\[paste('dW',l,sep="")\]\] \*

gradients\[\[paste('dW',l,sep="")\]\]

s\[\[paste("db",l, sep="")\]\] = beta2\*s\[\[paste("db",l, sep="")\]\] +

(1-beta2) \* gradients\[\[paste('db',l,sep="")\]\] \*

gradients\[\[paste('db',l,sep="")\]\]

\# Compute bias-corrected second moment estimate.

 s\_corrected\[\[paste("dW",l, sep="")\]\] = s\[\[paste("dW",l, sep="")\]\]/(1-beta2^t)

s\_corrected\[\[paste("db",l, sep="")\]\] = s\[\[paste("db",l, sep="")\]\]/(1-beta2^t)

\# Update parameters.

d1=sqrt(s\_corrected\[\[paste("dW",l, sep="")\]\]+epsilon) d2=sqrt(s\_corrected\[\[paste("db",l, sep="")\]\]+epsilon) parameters\[\[paste("W",l,sep="")\]\] = parameters\[\[paste("W",l,sep="")\]\] -

learningRate \* v\_corrected\[\[paste("dW",l, sep="")\]\]/d1

parameters\[\[paste("b",l,sep="")\]\] = parameters\[\[paste("b",l,sep="")\]\] -

learningRate\*v\_corrected\[\[paste("db",l, sep="")\]\]/d2

}

\# Compute for the Lth layer for sigmoid activation

if(outputActivationFunc=="sigmoid"){

v\[\[paste("dW",L, sep="")\]\] = beta1\*v\[\[paste("dW",L, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('dW',L,sep="")\]\]

v\[\[paste("db",L, sep="")\]\] = beta1\*v\[\[paste("db",L, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('db',L,sep="")\]\]

\# Compute bias-corrected first moment estimate.

v\_corrected\[\[paste("dW",L, sep="")\]\] = v\[\[paste("dW",L, sep="")\]\]/(1-beta1^t)

v\_corrected\[\[paste("db",L, sep="")\]\] = v\[\[paste("db",L, sep="")\]\]/(1-beta1^t)

\# Element wise multiply of gradients

s\[\[paste("dW",L, sep="")\]\] = beta2\*s\[\[paste("dW",L, sep="")\]\] +

(1-beta2) \* gradients\[\[paste('dW',L,sep="")\]\] \*

gradients\[\[paste('dW',L,sep="")\]\]

s\[\[paste("db",L, sep="")\]\] = beta2\*s\[\[paste("db",L, sep="")\]\] +

(1-beta2) \* gradients\[\[paste('db',L,sep="")\]\] \*

gradients\[\[paste('db',L,sep="")\]\]

\# Compute bias-corrected second moment estimate.

s\_corrected\[\[paste("dW",L, sep="")\]\] = s\[\[paste("dW",L, sep="")\]\]/(1-beta2^t)

s\_corrected\[\[paste("db",L, sep="")\]\] = s\[\[paste("db",L, sep="")\]\]/(1-beta2^t)

\# Update parameters.

d1=sqrt(s\_corrected\[\[paste("dW",L, sep="")\]\]+epsilon) d2=sqrt(s\_corrected\[\[paste("db",L, sep="")\]\]+epsilon) parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate \* v\_corrected\[\[paste("dW",L, sep="")\]\]/d1

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\*v\_corrected\[\[paste("db",L, sep="")\]\]/d2

}else if (outputActivationFunc=="softmax"){ #Compute for the Lth layer for softmax activation

v\[\[paste("dW",L, sep="")\]\] = beta1\*v\[\[paste("dW",L, sep="")\]\] +

(1-beta1) \* t(gradients\[\[paste('dW',L,sep="")\]\])

v\[\[paste("db",L, sep="")\]\] = beta1\*v\[\[paste("db",L, sep="")\]\] +

(1-beta1) \* t(gradients\[\[paste('db',L,sep="")\]\])

\# Compute bias-corrected first moment estimate.

v\_corrected\[\[paste("dW",L, sep="")\]\] = v\[\[paste("dW",L, sep="")\]\]/(1-beta1^t)

v\_corrected\[\[paste("db",L, sep="")\]\] = v\[\[paste("db",L, sep="")\]\]/(1-beta1^t)

\# Element wise multiply of gradients

s\[\[paste("dW",L, sep="")\]\] = beta2\*s\[\[paste("dW",L, sep="")\]\] +

(1-beta2) \* t(gradients\[\[paste('dW',L,sep="")\]\]) \*

t(gradients\[\[paste('dW',L,sep="")\]\])

s\[\[paste("db",L, sep="")\]\] = beta2\*s\[\[paste("db",L, sep="")\]\] +

(1-beta2) \* t(gradients\[\[paste('db',L,sep="")\]\]) \*

t(gradients\[\[paste('db',L,sep="")\]\])

\# Compute bias-corrected second moment estimate.

s\_corrected\[\[paste("dW",L, sep="")\]\] = s\[\[paste("dW",L, sep="")\]\]/(1-beta2^t)

s\_corrected\[\[paste("db",L, sep="")\]\] = s\[\[paste("db",L, sep="")\]\]/(1-beta2^t)

\# Update parameters.

d1=sqrt(s\_corrected\[\[paste("dW",L, sep="")\]\]+epsilon)

 d2=sqrt(s\_corrected\[\[paste("db",L, sep="")\]\]+epsilon) parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate \* v\_corrected\[\[paste("dW",L, sep="")\]\]/d1

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\*v\_corrected\[\[paste("db",L, sep="")\]\]/d2

}

return(parameters)

}

**5.1a. Stochastic Gradient Descent with**

**Adam – Python**

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

import sklearn.linear\_model

import pandas as pd

import sklearn

import sklearn.datasets

exec(open("DLfunctions7.py").read())

#Load MNIST

exec(open("load\_mnist.py").read())

training=list(read(dataset='training',path=".\\\\mnist")) test=list(read(dataset='testing',path=".\\\\mnist"))

lbls=\[\]

pxls=\[\]

print(len(training))

#for i in range(len(training)):

for i in range(60000):

l,p=training\[i\]

lbls.append(l)

pxls.append(p)

labels= np.array(lbls)

pixels=np.array(pxls)

y=labels.reshape(-1,1)

X=pixels.reshape(pixels.shape\[0\],-1)

X1=X.T

Y1=y.T

\# Create a list of random numbers of 1024

permutation = list(np.random.permutation(2\*\*10))

\# Subset 1024 from the data

![Image 365](index-306_1.jpg)

X2 = X1\[:, permutation\]

Y2 = Y1\[:, permutation\].reshape((1,2\*\*10))

\# Set layer dimensions

\# 784 – number of input features (28 x28)

\# 15, 9 – 2 hidden layers with 15, 9 hidden units respectively

\# 10 – 10 output classes with softmax activation unit at the output layer layersDimensions=\[784, 15,9,10\]

#Execute a L-layer Deep Learning network using SGD with Adam optimization

\# hidden Activation function – relu

\# output activation function – softmax

\# learning rate – 0.01

\# optimizer=”adam”

\# beta1 =0.9

\# beta2=0.9

\# epsilon=1e-8

\# mini\_batch\_size = 512

parameters = L\_Layer\_DeepModel\_SGD(X2, Y2, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc="softmax",learningRate = 0.01 , optimizer="adam", beta1=0.9, beta2=0.9, epsilon = 1e-8, mini\_batch\_size =512, num\_epochs = 1000, print\_cost = True,

figure="fig5.png")

**5.1b. Stochastic Gradient Descent with**

**Adam – R**

source("mnist.R")

source("DLfunctions7.R")

load\_mnist()

x <- t(train$x)

X <- x\[,1:60000\]

y <-train$y

y1 <- y\[1:60000\]

y2 <- as.matrix(y1)

Y=t(y2)

\# Subset 1024 random samples from MNIST

permutation = c(sample(2^10))

\# Randomly shuffle the training data

X1 = X\[, permutation\]

y1 = Y\[1, permutation\]

y2 <- as.matrix(y1)

Y1=t(y2)

\# Set layer dimensions

\# 784 – number of input features (28 x28)

\# 15, 9 – 2 hidden layers with 15,9 hidden units respectively

\# 10 – 10 output classes with softmax activation unit at the output layer layersDimensions=c(784, 15,9, 10)

#Execute a L-layer Deep Learning network using SGD with Adam optimization

\# hidden Activation function – tanh

\# output activation function – softmax

\# learning rate – 0.005

\# optimizer=”adam”

\# beta1 =0.7

\# beta2=0.9

\# epsilon=1e-8

\# mini\_batch\_size = 512

![Image 366](index-308_1.jpg)

retvalsSGD= L\_Layer\_DeepModel\_SGD(X1, Y1, layersDimensions,

hiddenActivationFunc='tanh',

outputActivationFunc="softmax",

learningRate = 0.005,

optimizer="adam",

beta1=0.7,

beta2=0.9,

epsilon=10^-8,

mini\_batch\_size = 512,

num\_epochs = 5000 ,

print\_cost = True)

#Plot the cost vs number of epochs

iterations <- seq(0,5000,1000)

costs=retvalsSGD$costs

df=data.frame(iterations,costs)

ggplot(df,aes(x=iterations,y=costs)) + geom\_point() + geom\_line(color="blue")

\+ ggtitle("Costs vs number of epochs") + xlab("No of epochs") + ylab("Cost")

**5.1c. Stochastic Gradient Descent with**

**Adam – Octave**

source("DL7functions.m")

load('./mnist/mnist.txt.gz');

#Create a random permutatation from 1024

permutation = randperm(1024);

disp(length(permutation));

\# Use this 1024 as the batch

X=trainX(permutation,:);

Y=trainY(permutation,:);

\# Set layer dimensions

\# 784 – number of input features (28 x28)

\# 15, 9 – 2 hidden layers with 15,9 hidden units respectively

\# 10 – 10 output classes with softmax activation unit at the output layer layersDimensions=\[784, 15, 9, 10\];

\# Note the high value for epsilon.

#Otherwise GD with Adam does not seem to converge

#Execute a L-layer Deep Learning network using SGD with Adam optimization

\# hidden Activation function – relu

\# output activation function – softmax

\# learning rate – 0.01

\# optimizer=”adam”

\# beta1 =0.9

\# beta2=0.9

\# epsilon=100

\# mini\_batch\_size = 512

\[weights biases costs\]=L\_Layer\_DeepModel\_SGD(X', Y', layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="softmax",

learningRate = 0.1,

lrDecay=false,

decayRate=1,

lambd=0,

 keep\_prob=1,

optimizer="adam",

beta=0.9,

beta1=0.9,

beta2=0.9,

epsilon=100,

mini\_batch\_size = 512,

num\_epochs = 5000);

#Plot cost vs number of epochs

plotCostVsEpochs(5000,costs)

![Image 367](index-311_1.jpg)

**6.Conclusion**

In this chapter I discuss and implement several Stochastic Gradient Descent optimization methods. The implementation of these methods enhance my already existing generic L-Layer Deep Learning Network implementation in vectorized Python, R and Octave.

![Image 368](index-313_1.jpg)

![Image 369](index-313_2.jpg)

![Image 370](index-313_3.jpg)

![Image 371](index-313_4.jpg)

![Image 372](index-313_5.jpg)

![Image 373](index-313_6.jpg)

![Image 374](index-313_7.jpg)

**8.**

**Gradient Check in Deep**

**Learning**

*You don’t understand anything until you learn it more than one* *way.* Marvin Minsky

*No computer has ever been designed that is ever aware of what it’s* *doing; but most of the time, we aren’t either.* Marvin Minsky *A wealth of information creates a poverty of attention.* Herbert Simon In this final chapter, I discuss and implement a key functionality needed while building Deep Learning networks viz. ‘Gradient

Checking’. Gradient Checking is an important method to check the correctness of your implementation, specifically the forward

propagation and the backward propagation cycles of an

implementation. In addition, I also discuss some tips for tuning hyperparameters of a Deep Learning network based on my experience.

This chapter implements a critical function for ensuring the

correctness of a L-Layer Deep Learning network implementation using Gradient Checking

Gradient Checking is based on the following approach. One iteration of Gradient Descent computes and updates the parameters by doing

.

To minimize the cost we will need to minimize

Let

be a function that computes the derivative

. Gradient

Checking allows us to numerically evaluate the implementation of the function

and verify its correctness.

We know the derivative of a function is given by

**Note**: The above derivative is based on the 2-sided derivative. The 1-

![Image 375](index-314_1.jpg)

![Image 376](index-314_2.jpg)

![Image 377](index-314_3.jpg)

![Image 378](index-314_4.jpg)

![Image 379](index-314_5.jpg)

![Image 380](index-314_6.jpg)

![Image 381](index-314_7.jpg)

![Image 382](index-314_8.jpg)

![Image 383](index-314_9.jpg)

![Image 384](index-314_10.jpg)

![Image 385](index-314_11.jpg)

![Image 386](index-314_12.jpg)

![Image 387](index-314_13.jpg)

![Image 388](index-314_14.jpg)

![Image 389](index-314_15.jpg)

![Image 390](index-314_16.jpg)

![Image 391](index-314_17.jpg)

![Image 392](index-314_18.jpg)

![Image 393](index-314_19.jpg)

![Image 394](index-314_20.jpg)

![Image 395](index-314_21.jpg)

![Image 396](index-314_22.jpg)

![Image 397](index-314_23.jpg)

sided derivative is given by

Gradient Checking is based on the 2-sided derivative because the error is of the order

as opposed

for the 1-sided derivative.

Hence Gradient Check uses the 2-sided derivative as follows.

In Gradient Check the following is done

A) Run one normal cycle of your implementation by doing the

following

a) Compute the output activation by running 1 cycle of forward propagation

b) Compute the cost using the output activation

c) Compute the gradients using backpropagation (grad)

B) Perform gradient check steps as below

a) Set . Flatten all ‘weights’ and ‘bias’ matrices and vectors to a column vector.

b) Initialize

by nudging up by adding (

)

c) Perform forward propagation with

d) Compute cost with

i.e.

e) Initialize

by nudging down by subtracting

f) Perform forward propagation with

g) Compute cost with

i.e.

h) Compute

or ‘gradapprox’ as

using the 2 sided

derivative.

i) Compute L2norm or the Euclidean distance between ‘grad’ and

‘gradapprox’.

If the difference is of the order of

or

the implementation is

correct. In the Deep Learning

![Image 398](index-315_1.jpg)

![Image 399](index-315_2.jpg)

[Specialization (https://www.coursera.org/specializations/deep-](https://www.coursera.org/specializations/deep-learning)

[learning) Prof Andrew Ng mentions that if the difference is of](https://www.coursera.org/specializations/deep-learning) the order of

then the implementation is correct. A difference of

is also ok. Anything more than that is a cause of worry and you should look at your code more closely. To see more details

click [Gradient checking and advanced optimization](http://ufldl.stanford.edu/wiki/index.php/Gradient_checking_and_advanced_optimization)

[(http://ufldl.stanford.edu/wiki/index.php/Gradient\_checking\_and\_adva](http://ufldl.stanford.edu/wiki/index.php/Gradient_checking_and_advanced_optimization)nced\_optimization The implementations of the functions invoked in this chapter are in Appendix 8 – Gradient Check

You can clone/download the code from Github

at DeepLearningFromFirstPrinciples

(https://github.com/tvganesh/DeepLearningFromFirstPrinciples/tree/master/Chap8-DLGradientCheck)

After spending a better part of 3 days, I now realize how critical Gradient Check is for ensuring the correctness of your

implementation. Initially I was getting very high difference and did not know how to understand the results or debug my implementation.

After many hours of staring at the results, I was able to finally arrive at a way, to localize issues in the implementation. In fact, I did catch a small bug in my Python code, which did not exist in the R and Octave implementations. I will demonstrate this below

**1.1a Gradient Check – Sigmoid**

**Activation – Python**

import numpy as np

import matplotlib

exec(open("DLfunctions8.py").read())

exec(open("testcases.py").read())

#Load the circles data set

train\_X, train\_Y, test\_X, test\_Y = load\_dataset()

#Set layer dimensions

\# 2 – number of input features

\# 4 – 1 hidden layer with 4 activation units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = \[2,4,1\]

\# Initialize parameters

parameters = initializeDeepModel(layersDimensions)

#Perform forward propagation

AL, caches, dropoutMat = forwardPropagationDeep(train\_X, parameters, keep\_prob=1, hiddenActivationFunc="relu",outputActivationFunc="sigmoid")

#Compute cost

cost = computeCost(AL, train\_Y, outputActivationFunc="sigmoid") print("cost=",cost)

#Perform backprop and get gradients

gradients = backwardPropagationDeep(AL, train\_Y, caches, dropoutMat, lambd=0, keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc="sigmoid")

\# Set values

epsilon = 1e-7

outputActivationFunc="sigmoid"

\# Set-up variables

\# Flatten parameters to a vector

parameters\_values, \_ = dictionary\_to\_vector(parameters)

#Flatten gradients to a vector

grad = gradients\_to\_vector(parameters,gradients)

num\_parameters = parameters\_values.shape\[0\]

#Initialize J\_plus, J\_minus and gradapprox

J\_plus = np.zeros((num\_parameters, 1))

J\_minus = np.zeros((num\_parameters, 1))

gradapprox = np.zeros((num\_parameters, 1))

\# Compute gradapprox using 2-sided derivative

for i in range(num\_parameters):

\# Compute J\_plus\[i\].

thetaplus = np.copy(parameters\_values)

thetaplus\[i\]\[0\] = thetaplus\[i\]\[0\] + epsilon

AL, caches, dropoutMat = forwardPropagationDeep(train\_X,

vector\_to\_dictionary(parameters,thetaplus), keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc) J\_plus\[i\] = computeCost(AL, train\_Y,

outputActivationFunc=outputActivationFunc)

\# Compute J\_minus\[i\].

thetaminus = np.copy(parameters\_values)

thetaminus\[i\]\[0\] = thetaminus\[i\]\[0\] - epsilon

AL, caches, dropoutMat = forwardPropagationDeep(train\_X,

vector\_to\_dictionary(parameters,thetaminus),

keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc) J\_minus\[i\] = computeCost(AL, train\_Y,

outputActivationFunc=outputActivationFunc)

 # Compute gradapprox\[i\]

gradapprox\[i\] = (J\_plus\[i\] - J\_minus\[i\])/(2\*epsilon)

\# Compare gradapprox to gradients from backprop by computing euclidean difference.

numerator = np.linalg.norm(grad-gradapprox)

denominator = np.linalg.norm(grad) +

np.linalg.norm(gradapprox)

difference = numerator/denominator

#Check the difference

if difference > 1e-5:

print ("\\033\[93m" + "There is a mistake in the backward propagation!

difference = " + str(difference) + "\\033\[0m")

else:

print ("\\033\[92m" + "Your backward propagation works perfectly fine!

difference = " + str(difference) + "\\033\[0m")

print(difference)

print("\\n")

\# The technique below can be used to identify

\# which of the parameters are in error

\# Covert grad to dictionary

m=vector\_to\_dictionary2(parameters,grad)

print("Gradients from backprop")

print(m)

print("\\n")

\# Convert gradapprox to dictionary

n=vector\_to\_dictionary2(parameters,gradapprox)

print("Gradapprox from gradient check")

print(n)

\## (300, 2)

\## (300,)

\## cost= 0.6931455556341791

\## \[Your backward propagation works perfectly fine! difference =

1.1604150683743381e-06\[0m

\## 1.1604150683743381e-06

##

##

\## Gradients from backprop

\## {'dW1': array(\[\[-6.19439955e-06, -2.06438046e-06\],

\## \[-1.50165447e-05, 7.50401672e-05\],

\## \[ 1.33435433e-04, 1.74112143e-04\],

\## \[-3.40909024e-05, -1.38363681e-04\]\]), 'db1': array(\[\[ 7.31333221e-07\],

\## \[ 7.98425950e-06\],

\## \[ 8.15002817e-08\],

\## \[-5.69821155e-08\]\]), 'dW2': array(\[\[2.73416304e-04, 2.96061451e-04, 7.51837363e-05, 1.01257729e-04\]\]), 'db2': array(\[\[-7.22232235e-06\]\])}

##

##

\## Gradapprox from gradient check

\## {'dW1': array(\[\[-6.19448937e-06, -2.06501483e-06\],

\## \[-1.50168766e-05, 7.50399742e-05\],

\## \[ 1.33435485e-04, 1.74112391e-04\],

\## \[-3.40910633e-05, -1.38363765e-04\]\]), 'db1': array(\[\[ 7.31081862e-07\],

\## \[ 7.98472399e-06\],

\## \[ 8.16013923e-08\],

\## \[-5.71764858e-08\]\]), 'dW2': array(\[\[2.73416290e-04, 2.96061509e-04, 7.51831930e-05, 1.01257891e-04\]\]), 'db2': array(\[\[-7.22255589e-06\]\])}

**1.1b Gradient Check – Softmax**

**Activation – Python (Error!!)**

In the code below I show, how I managed to spot a bug in your implementation

import numpy as np

exec(open("DLfunctions8.py").read())

\# Create spiral dataset

N = 100 # number of points per class

D = 2 # dimensionality

K = 3 # number of classes

X = np.zeros((N\*K,D)) # data matrix (each row = single example) y = np.zeros(N\*K, dtype='uint8') # class labels

for j in range(K):

ix = range(N\*j,N\*(j+1))

r = np.linspace(0.0,1,N) # radius

t = np.linspace(j\*4,(j+1)\*4,N) + np.random.randn(N)\*0.2 # theta X\[ix\] = np.c\_\[r\*np.sin(t), r\*np.cos(t)\]

y\[ix\] = j

\# Plot the data

#plt.scatter(X\[:, 0\], X\[:, 1\], c=y, s=40, cmap=plt.cm.Spectral)

\# Set layer dimensions

\# 2 – number of input features

\# 3 – 1 hidden layer with 3 activation units

\# 3 – 3 classes with softmax activation unit at the output layer layersDimensions = \[2,3,3\]

\# Set params

y1=y.reshape(-1,1).T

train\_X=X.T

train\_Y=y1

\# Initialize the model

parameters = initializeDeepModel(layersDimensions)

#Compute forward prop

AL, caches, dropoutMat = forwardPropagationDeep(train\_X, parameters, keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc="softmax")

#Compute cost

cost = computeCost(AL, train\_Y, outputActivationFunc="softmax") print("cost=",cost)

#Compute gradients from backprop

gradients = backwardPropagationDeep(AL, train\_Y, caches, dropoutMat, lambd=0, keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc="softmax")

\# Note the transpose of the gradients for Softmax has to be taken L= len(parameters)//2

print(L)

gradients\['dW'+str(L)\]=gradients\['dW'+str(L)\].T

gradients\['db'+str(L)\]=gradients\['db'+str(L)\].T

\# Perform gradient check

gradient\_check\_n(parameters, gradients, train\_X, train\_Y, epsilon = 1e-7,outputActivationFunc="softmax")

cost= 1.0986187818144022

There is a mistake in the backward propagation! difference =

0.7100295155692544

0.7100295155692544

Gradients from backprop

{'dW1': array(\[\[ 0.00050125, 0.00045194\],

\[ 0.00096392, 0.00039641\],

 \[-0.00014276, -0.00045639\]\]), 'db1': array(\[\[ 0.00070082\],

\[-0.00224399\],

\[ 0.00052305\]\]), 'dW2': array(\[\[-8.40953794e-05, -9.52657769e-04,

\-1.10269379e-04\],

\[-7.45469382e-04, 9.49795606e-04, 2.29045434e-04\],

\[ 8.29564761e-04, 2.86216305e-06, -1.18776055e-04\]\]),

'db2': array(\[\[**\-0.00253808**\],

\[**\-0.00505508**\],

\[ **0.00759315**\]\])}

Gradapprox from gradient check

{'dW1': array(\[\[ 0.00050125, 0.00045194\],

\[ 0.00096392, 0.00039641\],

\[-0.00014276, -0.00045639\]\]), 'db1': array(\[\[ 0.00070082\],

\[-0.00224399\],

\[ 0.00052305\]\]), 'dW2': array(\[\[-8.40960634e-05, -9.52657953e-04,

\-1.10268461e-04\],

\[-7.45469242e-04, 9.49796908e-04, 2.29045671e-04\],

\[ 8.29565305e-04, 2.86104473e-06, -1.18776100e-04\]\]),

'db2': array(\[\[-8.46211989e-06\],

\[-1.68487446e-05\],

\[ 2.53108645e-05\]\])}

Gradient Check gives a high value of the difference of 0.7100295.

Inspecting the Gradients and Gradapprox we can see there is a very big discrepancy in db2. After I went over my code I discovered that my computation in the function layerActivationBackward for Softmax was

\# **Erroneous code**

if activationFunc == 'softmax':

dW = 1/numtraining \* np.dot(A\_prev,dZ)

db = np.sum(dZ, axis=0, keepdims=True)

dA\_prev = np.dot(dZ,W)

instead of

\# **Fixed code**

if activationFunc == 'softmax':

dW = 1/numtraining \* np.dot(A\_prev,dZ)

db = **1/numtraining \*** np.sum(dZ, axis=0, keepdims=True) dA\_prev = np.dot(dZ,W)

After fixing this error when I ran the Gradient Check as shown below

**1.1c Gradient Check – Softmax**

**Activation – Python (Corrected!!)**

import numpy as np

exec(open("DLfunctions8.py").read())

\# Create Spiral dataset

N = 100 # number of points per class

D = 2 # dimensionality

K = 3 # number of classes

X = np.zeros((N\*K,D)) # data matrix (each row = single example) y = np.zeros(N\*K, dtype='uint8') # class labels

for j in range(K):

ix = range(N\*j,N\*(j+1))

r = np.linspace(0.0,1,N) # radius

t = np.linspace(j\*4,(j+1)\*4,N) + np.random.randn(N)\*0.2 # theta X\[ix\] = np.c\_\[r\*np.sin(t), r\*np.cos(t)\]

y\[ix\] = j

\# Plot the data

#plt.scatter(X\[:, 0\], X\[:, 1\], c=y, s=40, cmap=plt.cm.Spectral)

\# Set layer dimensions

\# 2 – number of input features

\# 3 – 1 hidden layer with 3 activation units

\# 3 – 3 classes with softmax activation unit at the output layer layersDimensions = \[2,3,3\]

y1=y.reshape(-1,1).T

train\_X=X.T

train\_Y=y1

\# Initialize model

parameters = initializeDeepModel(layersDimensions)

#Perform forward prop

AL, caches, dropoutMat = forwardPropagationDeep(train\_X, parameters,

keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc="softmax")

#Compute cost

cost = computeCost(AL, train\_Y, outputActivationFunc="softmax") print("cost=",cost)

#Compute gradients from backprop

gradients = backwardPropagationDeep(AL, train\_Y, caches, dropoutMat, lambd=0, keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc="softmax")

\# Note the transpose of the gradients for Softmax has to be taken L= len(parameters)//2

print(L)

gradients\['dW'+str(L)\]=gradients\['dW'+str(L)\].T

gradients\['db'+str(L)\]=gradients\['db'+str(L)\].T

#Perform gradient check

gradient\_check\_n(parameters, gradients, train\_X, train\_Y, epsilon = 1e-7,outputActivationFunc="softmax")

\## cost= 1.0986193170234435

\## 2

\## \[92mYour backward propagation works perfectly fine! difference =

5.268804859613151e-07\[0m

\## 5.268804859613151e-07

##

##

\## Gradients from backprop

\## {'dW1': array(\[\[ 0.00053206, 0.00038987\],

\## \[ 0.00093941, 0.00038077\],

\## \[-0.00012177, -0.0004692 \]\]), 'db1': array(\[\[ 0.00072662\],

\## \[-0.00210198\],

\## \[ 0.00046741\]\]), 'dW2': array(\[\[-7.83441270e-05, -9.70179498e-04,

\-1.08715815e-04\],

\## \[-7.70175008e-04, 9.54478237e-04, 2.27690198e-04\],

\## \[ 8.48519135e-04, 1.57012608e-05, -1.18974383e-04\]\]), 'db2':

array(\[\[-8.52190476e-06\],

\## \[-1.69954294e-05\],

\## \[ 2.55173342e-05\]\])}

##

##

\## Gradapprox from gradient check

\## {'dW1': array(\[\[ 0.00053206, 0.00038987\],

\## \[ 0.00093941, 0.00038077\],

\## \[-0.00012177, -0.0004692 \]\]), 'db1': array(\[\[ 0.00072662\],

\## \[-0.00210198\],

\## \[ 0.00046741\]\]), 'dW2': array(\[\[-7.83439980e-05, -9.70180603e-04,

\-1.08716369e-04\],

\## \[-7.70173925e-04, 9.54478718e-04, 2.27690089e-04\],

\## \[ 8.48520143e-04, 1.57018842e-05, -1.18973720e-04\]\]), 'db2': array(\[\[-8.52096171e-06\],

\## \[-1.69964043e-05\],

\## \[ 2.55162558e-05\]\])}

**1.2a Gradient Check – Sigmoid**

**Activation – R**

source("DLfunctions8.R")

z <- as.matrix(read.csv("circles.csv",header=FALSE)) x <- z\[,1:2\]

y <- z\[,3\]

X <- t(x)

Y <- t(y)

#Set layer dimensions

layersDimensions = c(2,5,1)

#Initialize model

parameters = initializeDeepModel(layersDimensions)

#Perform forward prop

retvals = forwardPropagationDeep(X, parameters,keep\_prob=1,

hiddenActivationFunc="relu",

outputActivationFunc="sigmoid")

AL <- retvals\[\['AL'\]\]

caches <- retvals\[\['caches'\]\]

dropoutMat <- retvals\[\['dropoutMat'\]\]

#Compute cost

cost <- computeCost(AL, Y,outputActivationFunc="sigmoid", numClasses=layersDimensions\[length(layersDimensions)\])

print(cost)

\## \[1\] 0.6931447

\# Perform backward propagation and get gradients

gradients = backwardPropagationDeep(AL, Y, caches, dropoutMat, lambd=0, keep\_prob=1, hiddenActivationFunc="relu",

outputActivationFunc="sigmoid",numClasses=layersDimensions\[length(layersDimensions)\])

\# Set values

epsilon = 1e-07

outputActivationFunc="sigmoid"

#Convert parameter list to vector

parameters\_values = list\_to\_vector(parameters)

#Convert gradient list to vector

grad = gradients\_to\_vector(parameters,gradients)

num\_parameters = dim(parameters\_values)\[1\]

#Initialize J\_plus, J\_minus and gradapprox

J\_plus = matrix(rep(0,num\_parameters),

nrow=num\_parameters,ncol=1)

J\_minus = matrix(rep(0,num\_parameters),

nrow=num\_parameters,ncol=1)

gradapprox = matrix(rep(0,num\_parameters),

nrow=num\_parameters,ncol=1)

\# Compute J\_plus, J\_minus and

for(i in 1:num\_parameters){

\# Compute J\_plus\[i\].

thetaplus = parameters\_values

thetaplus\[i\]\[1\] = thetaplus\[i\]\[1\] + epsilon

retvals = forwardPropagationDeep(X, vector\_to\_list(parameters,thetaplus), keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc) AL <- retvals\[\['AL'\]\]

J\_plus\[i\] = computeCost(AL, Y,

outputActivationFunc=outputActivationFunc)

\# Compute J\_minus\[i\].

thetaminus = parameters\_values

thetaminus\[i\]\[1\] = thetaminus\[i\]\[1\] - epsilon

retvals = forwardPropagationDeep(X, vector\_to\_list(parameters,thetaminus),

keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc) AL <- retvals\[\['AL'\]\]

J\_minus\[i\] = computeCost(AL, Y,

outputActivationFunc=outputActivationFunc)

\# Compute gradapprox\[i\]

gradapprox\[i\] = (J\_plus\[i\] - J\_minus\[i\])/(2\*epsilon)

}

\# Compare gradapprox to backprop gradients by computing Euclidean difference.

#Compute L2Norm

numerator = L2NormVec(grad-gradapprox)

denominator = L2NormVec(grad) +

L2NormVec(gradapprox)

difference = numerator/denominator

\# Output difference

if(difference > 1e-5){

cat("There is a mistake, the difference is too high",difference)

} else{

cat("The implementations works perfectly", difference)

}

\## The implementations works perfectly 1.279911e-06

\# Technique to check gradients

print("Gradients from backprop")

\## \[1\] "Gradients from backprop"

vector\_to\_list2(parameters,grad)

\## $dW1

\## \[,1\] \[,2\]

\## \[1,\] -7.641588e-05 -3.427989e-07

\## \[2,\] -9.049683e-06 6.906304e-05

\## \[3,\] 3.401039e-06 -1.503914e-04

\## \[4,\] 1.535226e-04 -1.686402e-04

\## \[5,\] -6.029292e-05 -2.715648e-04

##

\## $db1

\## \[,1\]

\## \[1,\] 6.930318e-06

\## \[2,\] -3.283117e-05

\## \[3,\] 1.310647e-05

\## \[4,\] -3.454308e-05

\## \[5,\] -2.331729e-08

##

\## $dW2

\## \[,1\] \[,2\] \[,3\] \[,4\] \[,5\]

\## \[1,\] 0.0001612356 0.0001113475 0.0002435824 0.000362149 2.874116e-05

##

\## $db2

\## \[,1\]

\## \[1,\] -1.16364e-05

print("Grad approx from gradient check")

\## \[1\] "Grad approx from gradient check"

vector\_to\_list2(parameters,gradapprox)

\## $dW1

\## \[,1\] \[,2\]

\## \[1,\] -7.641554e-05 -3.430589e-07

\## \[2,\] -9.049428e-06 6.906253e-05

\## \[3,\] 3.401168e-06 -1.503919e-04

\## \[4,\] 1.535228e-04 -1.686401e-04

\## \[5,\] -6.029288e-05 -2.715650e-04

##

\## $db1

\## \[,1\]

\## \[1,\] 6.930012e-06

\## \[2,\] -3.283096e-05

\## \[3,\] 1.310618e-05

\## \[4,\] -3.454237e-05

\## \[5,\] -2.275957e-08

##

\## $dW2

\## \[,1\] \[,2\] \[,3\] \[,4\] \[,5\]

\## \[1,\] 0.0001612355 0.0001113476 0.0002435829 0.0003621486 2.87409e-05

##

\## $db2

\## \[,1\]

\## \[1,\] -1.16368e-05

**1.2b Gradient Check – Softmax**

**Activation – R**

source("DLfunctions8.R")

Z <- as.matrix(read.csv("spiral.csv",header=FALSE))

\# Setup the data

X <- Z\[,1:2\]

y <- Z\[,3\]

X <- t(X)

Y <- t(y)

\# Set layer dimensions

\# 2 – number of input features

\# 3 – 1 hidden layer with 3 activation units

\# 3 – 3 classes with softmax activation unit at the output layer layersDimensions = c(2, 3, 3)

#Initialize model

parameters = initializeDeepModel(layersDimensions)

#Perform forward propagation

retvals = forwardPropagationDeep(X, parameters,keep\_prob=1,

hiddenActivationFunc="relu",

outputActivationFunc="softmax")

AL <- retvals\[\['AL'\]\]

caches <- retvals\[\['caches'\]\]

dropoutMat <- retvals\[\['dropoutMat'\]\]

#Compute cost

cost <- computeCost(AL, Y,outputActivationFunc="softmax", numClasses=layersDimensions\[length(layersDimensions)\])

print(cost)

\## \[1\] 1.098618

\# Perform Backward propagation.

gradients = backwardPropagationDeep(AL, Y, caches, dropoutMat, lambd=0, keep\_prob=1, hiddenActivationFunc="relu",

outputActivationFunc="softmax",numClasses=layersDimensions\[length(layersDimensions)\])

\# Need to take transpose of the last layer for Softmax

L=length(parameters)/2

gradients\[\[paste('dW',L,sep="")\]\]=t(gradients\[\[paste('dW',L,sep="")\]\]) gradients\[\[paste('db',L,sep="")\]\]=t(gradients\[\[paste('db',L,sep="")\]\])

#Perform gradient check

gradient\_check\_n(parameters, gradients, X, Y,

epsilon = 1e-7,outputActivationFunc="softmax")

\## The implementations works perfectly 3.903011e-07\[1\] "Gradients from backprop"

\## $dW1

\## \[,1\] \[,2\]

\## \[1,\] 0.0007962367 -0.0001907606

\## \[2,\] 0.0004444254 0.0010354412

\## \[3,\] 0.0003078611 0.0007591255

##

\## $db1

\## \[,1\]

\## \[1,\] -0.0017305136

\## \[2,\] 0.0005393734

\## \[3,\] 0.0012484550

##

\## $dW2

\## \[,1\] \[,2\] \[,3\]

\## \[1,\] -3.515627e-04 7.487283e-04 -3.971656e-04

\## \[2,\] -6.381521e-05 -1.257328e-06 6.507254e-05

\## \[3,\] -1.719479e-04 -4.857264e-04 6.576743e-04

##

\## $db2

\## \[,1\]

\## \[1,\] -5.536383e-06

\## \[2,\] -1.824656e-05

\## \[3,\] 2.378295e-05

##

\## \[1\] "Grad approx from gradient check"

\## $dW1

\## \[,1\] \[,2\]

\## \[1,\] 0.0007962364 -0.0001907607

\## \[2,\] 0.0004444256 0.0010354406

\## \[3,\] 0.0003078615 0.0007591250

##

\## $db1

\## \[,1\]

\## \[1,\] -0.0017305135

\## \[2,\] 0.0005393741

\## \[3,\] 0.0012484547

##

\## $dW2

\## \[,1\] \[,2\] \[,3\]

\## \[1,\] -3.515632e-04 7.487277e-04 -3.971656e-04

\## \[2,\] -6.381451e-05 -1.257883e-06 6.507239e-05

\## \[3,\] -1.719469e-04 -4.857270e-04 6.576739e-04

##

\## $db2

\## \[,1\]

\## \[1,\] -5.536682e-06

\## \[2,\] -1.824652e-05

\## \[3,\] 2.378209e-05

**1.3a Gradient Check – Sigmoid**

**Activation – Octave**

source("DL8functions.m")

\# Read circles data

data=csvread("circles.csv");

X=data(:,1:2);

Y=data(:,3);

#Set layer dimensions

\# 2 – number of input features

\# 5 – 1 hidden layer with 5 activation units

\# 1 – 1 sigmoid activation unit at the output layer

layersDimensions = \[2 5 1\];

#Initialize model

\[weights biases\] = initializeDeepModel(layersDimensions);

#Perform forward prop

\[AL forward\_caches activation\_caches droputMat\] =

forwardPropagationDeep(X', weights, biases,keep\_prob=1,

hiddenActivationFunc="relu", outputActivationFunc="sigmoid");

#Compute cost

cost = computeCost(AL,

Y',outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));

disp(cost);

#Compute gradients from cost

\[gradsDA gradsDW gradsDB\] = backwardPropagationDeep(AL, Y',

activation\_caches,forward\_caches, droputMat, lambd=0, keep\_prob=1, hiddenActivationFunc="relu",

outputActivationFunc="sigmoid",

numClasses=layersDimensions(size(layersDimensions)

(2)));

#Set values

epsilon = 1e-07;

outputActivationFunc="sigmoid";

\# Convert paramters cell array to vector

parameters\_values = cellArray\_to\_vector(weights, biases);

#Convert gradient cell array to vector

grad = gradients\_to\_vector(gradsDW,gradsDB);

num\_parameters = size(parameters\_values)(1);

#Initialize J\_plus, J\_minus and gradapprox

J\_plus = zeros(num\_parameters, 1);

J\_minus = zeros(num\_parameters, 1);

gradapprox = zeros(num\_parameters, 1);

\# Compute gradapprox

for i = 1:num\_parameters

\# Compute J\_plus\[i\].

thetaplus = parameters\_values;

thetaplus(i,1) = thetaplus(i,1) + epsilon;

\[weights1 biases1\] =vector\_to\_cellArray(weights, biases,thetaplus);

\[AL forward\_caches activation\_caches droputMat\] =

forwardPropagationDeep(X', weights1, biases1,

keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc); J\_plus(i) = computeCost(AL, Y',

outputActivationFunc=outputActivationFunc);

\# Compute J\_minus\[i\].

thetaminus = parameters\_values;

thetaminus(i,1) = thetaminus(i,1) - epsilon ;

\[weights1 biases1\] = vector\_to\_cellArray(weights, biases,thetaminus);

\[AL forward\_caches activation\_caches droputMat\] =

forwardPropagationDeep(X',weights1, biases1, keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc); J\_minus(i) = computeCost(AL, Y',

outputActivationFunc=outputActivationFunc);

\# Compute gradapprox\[i\]

gradapprox(i) = (J\_plus(i) - J\_minus(i))/(2\*epsilon);

endfor

#Compute L2Norm or the Euclidean distance between gradients and gradapprox numerator = L2NormVec(grad-gradapprox);

denominator = L2NormVec(grad) +

L2NormVec(gradapprox);

difference = numerator/denominator;

disp(difference);

#Check difference

if difference > 1e-04

printf("There is a mistake in the implementation "); disp(difference);

else

printf("The implementation works perfectly");

disp(difference);

endif

\# Technique to compare the weights and biases and localize issue

\# Convert grad to cell Array

\[weights1 biases1\] = vector\_to\_cellArray(weights, biases,grad); printf("Gradients from back propagation");

disp(weights1);

disp(biases1);

\# Convert gradapprox to cell array

\[weights2 biases2\] = vector\_to\_cellArray(weights, biases,gradapprox); printf("Gradients from gradient check");

\# Display

disp(weights2);

disp(biases2);

0.69315

1.4893e-005

The implementation works perfectly 1.4893e-005

Gradients from back propagation

{

\[1,1\] =

5.0349e-005 2.1323e-005

8.8632e-007 1.8231e-006

9.3784e-005 1.0057e-004

1.0875e-004 -1.9529e-007

5.4502e-005 3.2721e-005

\[1,2\] =

1.0567e-005 6.0615e-005 4.6004e-005 1.3977e-004 1.0405e-004

}

{

\[1,1\] =

\-1.8716e-005

1.1309e-009

4.7686e-005

1.2051e-005

\-1.4612e-005

\[1,2\] = 9.5808e-006

}

Gradients from gradient check

{

\[1,1\] =

5.0348e-005 2.1320e-005

8.8485e-007 1.8219e-006

9.3784e-005 1.0057e-004

1.0875e-004 -1.9762e-007

5.4502e-005 3.2723e-005

\[1,2\] =

\[1,2\] =

1.0565e-005 6.0614e-005 4.6007e-005 1.3977e-004 1.0405e-004

}

{

\[1,1\] =

\-1.8713e-005

1.1102e-009

4.7687e-005

1.2048e-005

\-1.4609e-005

\[1,2\] = 9.5790e-006

}

 

**1.3b Gradient Check – Softmax**

**Activation – Octave**

source("DL8functions.m")

data=csvread("spiral.csv");

\# Setup the data

X=data(:,1:2);

Y=data(:,3);

\# Set the layer dimensions

\# 2 – number of input features

\# 3 – 1 hidden layer with 3 activation units

\# 3 – 3 classes with softmax activation unit at the output layerlayersDimensions

\= \[2 3 3\];

\[weights biases\] = initializeDeepModel(layersDimensions);

\# Run forward prop

\[AL forward\_caches activation\_caches droputMat\] =

forwardPropagationDeep(X', weights, biases,keep\_prob=1,

hiddenActivationFunc="relu", outputActivationFunc="softmax");

\# Compute cost

cost = computeCost(AL,

Y',outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));

disp(cost);

\# Perform backward prop

\[gradsDA gradsDW gradsDB\] = backwardPropagationDeep(AL, Y',

activation\_caches,forward\_caches, droputMat, lambd=0, keep\_prob=1, hiddenActivationFunc="relu",

outputActivationFunc="softmax",

numClasses=layersDimensions(size(layersDimensions)

(2)));

#Take transpose of last layer for Softmax

L=size(weights)(2);

gradsDW{L}= gradsDW{L}';

gradsDB{L}= gradsDB{L}';

#Perform gradient check

difference= gradient\_check\_n(weights, biases, gradsDW,gradsDB, X, Y, epsilon

\= 1e-7,

outputActivationFunc="softmax",numClasses=layersDimensions(size(layersDimensions) (2)));

1.0986

The implementation works perfectly! 2.0021e-005

Gradients from back propagation

{

\[1,1\] =

\-7.1590e-005 4.1375e-005

\-1.9494e-004 -5.2014e-005

\-1.4554e-004 5.1699e-005

\[1,2\] =

3.3129e-004 1.9806e-004 -1.5662e-005

\-4.9692e-004 -3.7756e-004 -8.2318e-005

1.6562e-004 1.7950e-004 9.7980e-005

}

{

\[1,1\] =

\-3.0856e-005

\-3.3321e-004

\-3.8197e-004

\[1,2\] =

1.2046e-006

2.9259e-007

\-1.4972e-006

}

Gradients from gradient check

{

\[1,1\] =

 -7.1586e-005 4.1377e-005

\-1.9494e-004 -5.2013e-005

\-1.4554e-004 5.1695e-005

3.3129e-004 1.9806e-004 -1.5664e-005

\-4.9692e-004 -3.7756e-004 -8.2316e-005

1.6562e-004 1.7950e-004 9.7979e-005

}

{

\[1,1\] =

\-3.0852e-005

\-3.3321e-004

\-3.8197e-004

\[1,2\] =

1.1902e-006

2.8200e-007

\-1.4644e-006

}

![Image 400](index-343_1.jpg)

![Image 401](index-343_2.jpg)

![Image 402](index-343_3.jpg)

![Image 403](index-343_4.jpg)

![Image 404](index-343_5.jpg)

![Image 405](index-343_6.jpg)

![Image 406](index-343_7.jpg)

![Image 407](index-343_8.jpg)

![Image 408](index-343_9.jpg)

![Image 409](index-343_10.jpg)

**2.Tip for tuning hyperparameters**

Deep Learning Networks come with a large number of hyper

parameters which require tuning. The hyper parameters are

1\. -learning rate

2\. Number of layers

3\. Number of hidden units

4\. Number of iterations

5\. Momentum – – 0.9

6\. RMSProp –

– 0.9

7\. Adam –

,

and

8\. learning rate decay

9\. mini batch size

10\. Initialization method – He, Xavier

11\. Regularization

– Among the above the most critical learning rate . Rather than just trying out random values, it may help to try out values on a

logarithmic scale. So, we could try out values -0.01,0.1,1.0,10 etc. If we find that the cost is between 0.01 and 0.1 we could use the bisection technique so we can try 0.05. If we need to be bigger than 0.01 and 0.05 we could try 0.03 and then keep halving the distance etc.

– The performance of Momentum and RMSProp are very good and

work well with values 0.9. Even with this, it is better to try out values of 1- in the logarithmic range. So, 1- could 0.001,0.01,0.1 and hence would be 0.999,0.99 or 0.9

– Increasing the number of hidden units or number of hidden layers needs to be done gradually. I have noticed that increasing number of hidden layers heavily does not improve performance and sometimes degrades it.

– Sometimes, I tend to increase the number of iterations if I think I see

a steady decrease in the cost for a certain learning rate

– It may also help to add learning rate decay if you see there is an oscillation while it decreases.

– Xavier and He initializations also help in a fast convergence and are worth trying out.

**3.Final thoughts**

As I come to a close in this Deep Learning Series from first principles in Python, R and Octave, I must admit that I learnt a lot in the process.

\* Building a L-layer, vectorized Deep Learning Network in Python, R

and Octave was extremely challenging but very rewarding

\* One benefit of building vectorized versions in Python, R and Octave was that I was looking at each function that I was implementing thrice, and hence I was able to fix any bugs in any of the languages

\* In addition since I built the generic L-Layer DL network with all the bells and whistles, layer by layer I further had an opportunity to look at all the functions in each successive post.

\* Each language has its advantages and disadvantages. From the performance perspective I think Python is the best, followed by Octave and then R

\* Interesting, I noticed that even if small bugs creep into your implementation, the DL network does learn and does generate a valid set of weights and biases, however this may not be an optimum solution. In one case of an inadvertent bug, I was not updating the weights in the final layer of the DL network. Yet, using all the other layers, the DL network was able to come with a reasonable solution (maybe like random dropout, remaining units can still learn the data!)

\* Having said that, the Gradient Check method discussed and

implemented in this post can be very useful in ironing out bugs.

**4.Conclusion**

These months when I was writing the chapters and the also churning up the code in Python, R and Octave were very hectic. There have been times when I found that implementations of some function to be extremely demanding and I almost felt like giving up. There have been other times when I had to spend quite some time on an

intractable DL network which would not respond to changes in hyperparameters. All in all, it was a great learning experience.

Hope you enjoyed this detailed derivations and the implementation!!!

![Image 410](index-347_1.jpg)

![Image 411](index-347_2.jpg)

![Image 412](index-347_3.jpg)

![Image 413](index-347_4.jpg)

![Image 414](index-347_5.jpg)

![Image 415](index-347_6.jpg)

**1.**

**Appendix A**

**Neural NetworksThe mechanics of**

**backpropagation**

The initial work in the ‘Backpropagation Algorithm’ started in the 1980’s and led to an explosion of interest in Neural Networks and the application of backpropagation

The ‘Backpropagation’ algorithm computes the minimum of an error function with respect to the weights in the Neural Network. It uses the method of gradient descent. The combination of weights in a multi-layered neural network, which minimizes the error/cost function, is considered a solution of the learning problem.

In the Neural Network above

Perceptrons and single layered neural networks can only classify, if

the sample space is linearly separable. For non-linear decision boundaries, a multi layered neural network with backpropagation is required to generate more complex boundaries.The backpropagation algorithm, computes the minimum of the error function in weight space using the method of gradient descent. This computation of the gradient requires the activation function to be both differentiable and continuous. Hence, the sigmoid or logistic function is typically chosen as the activation function at every layer.

This post looks at a 3 layer neural network with 1 input, 1 hidden and 1 output. To a large extent this post is based on Matt Mazur’s detailed

“A step by step backpropagation example“

(https://www.coursera.org/learn/neural-networks/home), and Prof Hinton’s “Neural Networks for Machine Learning”(

https://www.coursera.org/learn/neural-networks/home/welcome) at Coursera and a few other sources.

While Matt Mazur’s post uses example values, I generate the formulas for the gradient derivatives for each weight in the hidden and input layers. I intend to implement a vector version of backpropagation in Octave, R and Python. Therefore, this post is a prequel to that.

The 3-layer neural network is as below

![Image 416](index-349_1.jpg)

![Image 417](index-349_2.jpg)

![Image 418](index-349_3.jpg)

![Image 419](index-349_4.jpg)

![Image 420](index-349_5.jpg)

![Image 421](index-349_6.jpg)

![Image 422](index-349_7.jpg)

![Image 423](index-349_8.jpg)

![Image 424](index-349_9.jpg)

![Image 425](index-349_10.jpg)

Some basic derivations which are used in backpropagation

**Chain rule of differentiation**

Let y=f(u)

and u=g(x) then

**An important result**

Let

then

Using the chain rule of differentiation we get

Therefore

**\-(A)**

**1) Feed forward network**

![Image 426](index-350_1.jpg)

![Image 427](index-350_2.jpg)

![Image 428](index-350_3.jpg)

![Image 429](index-350_4.jpg)

![Image 430](index-350_5.jpg)

![Image 431](index-350_6.jpg)

![Image 432](index-350_7.jpg)

![Image 433](index-350_8.jpg)

![Image 434](index-350_9.jpg)

![Image 435](index-350_10.jpg)

![Image 436](index-350_11.jpg)

![Image 437](index-350_12.jpg)

The net output at the 1st hidden layer

The sigmoid/logistic function function is used to generate the activation outputs for each hidden layer. The sigmoid is chosen because it is continuous and has a continuous derivative

The net output at the output layer

**Total error**

**2) The backwards pass**

In the backward pass we need to compute how the squared error changes with changing weight. i.e we compute

for each

weight

. This is shown below

A squared error is assumed

**Error gradient with**

![Image 438](index-351_1.jpg)

![Image 439](index-351_2.jpg)

![Image 440](index-351_3.jpg)

![Image 441](index-351_4.jpg)

![Image 442](index-351_5.jpg)

![Image 443](index-351_6.jpg)

![Image 444](index-351_7.jpg)

![Image 445](index-351_8.jpg)

![Image 446](index-351_9.jpg)

**\-(B)**

Since

Now considering the 2nd term in (B)

Using result (A)

The 3rd term in (B)

![Image 447](index-352_1.jpg)

![Image 448](index-352_2.jpg)

![Image 449](index-352_3.jpg)

![Image 450](index-352_4.jpg)

![Image 451](index-352_5.jpg)

![Image 452](index-352_6.jpg)

![Image 453](index-352_7.jpg)

Having computed

, we now perform gradient descent, by

computing a new weight, assuming a learning rate

If we do this for

we would get

**3) Hidden layer**

![Image 454](index-353_1.jpg)

![Image 455](index-353_2.jpg)

![Image 456](index-353_3.jpg)

![Image 457](index-353_4.jpg)

![Image 458](index-353_5.jpg)

![Image 459](index-353_6.jpg)

We now compute how the total error changes for a change in weight

– (C)

Using

we get

\-(D)

Considering the 1st term in (C)

![Image 460](index-354_1.jpg)

![Image 461](index-354_2.jpg)

![Image 462](index-354_3.jpg)

![Image 463](index-354_4.jpg)

![Image 464](index-354_5.jpg)

![Image 465](index-354_6.jpg)

![Image 466](index-354_7.jpg)

![Image 467](index-354_8.jpg)

![Image 468](index-354_9.jpg)

![Image 469](index-354_10.jpg)

![Image 470](index-354_11.jpg)

Now

– (E)

– (F)

which gives the following

Combining (D), (E) & (F) we get

This can be represented as

With this derivative a new value of

is computed

Hence there are 2 important results

At the output layer we have

a)

At each hidden layer we compute

b)

Backpropagation was very successful in the early years, but the

algorithm does have its problems for e.g the issue of the ‘vanishing’

and ‘exploding’ gradient. Yet it is a key development in Neural Networks, and the issues with the backprop gradients have been addressed through techniques such as the momentum method and

adaptive learning rate etc.

In this post. I derive the weights at the output layer and the hidden layer. As I already mentioned above, I intend to implement a vector version of the backpropagation algorithm in Octave, R and Python in the days to come.

**2.**

**Appendix 1 – Logistic Regression**

**as a Neural Network**

**1.1 Python functions**

##############################################################################################

#

\# Created by: Tinniam V Ganesh

\# Date : 4 Jan 2018

\# File: DLfunctions1.py

#

##############################################################################################

import numpy as np

import pandas as pd

import os

import matplotlib.pyplot as plt

from sklearn.model\_selection import train\_test\_split

\# Define the sigmoid function

def sigmoid(z):

a=1/(1+np.exp(-z))

return a

\# Initialize weights and biases

def initialize(dim):

w = np.zeros(dim).reshape(dim,1)

b = 0

return w

\# Compute the loss

\# Inputs: numTraining

\# : Y

\# : A

\# Ouputs : loss

def computeLoss(numTraining,Y,A):

 loss=-1/numTraining \*np.sum(Y\*np.log(A) + (1-Y)\*(np.log(1-A))) return(loss)

\# Execute the forward propagation

\# Inputs: w

\# : b

\# : X

\# : Y

\# Ouputs : gradients, loss (dict)

def forwardPropagation(w,b,X,Y):

\# Compute Z

Z=np.dot(w.T,X)+b

\# Determine the number of training samples

numTraining=float(len(X))

\# Compute the output of the sigmoid activation function

A=sigmoid(Z)

#Compute the loss

loss = computeLoss(numTraining,Y,A)

\# Compute the gradients dZ, dw and db

dZ=A-Y

dw=1/numTraining\*np.dot(X,dZ.T)

db=1/numTraining\*np.sum(dZ)

\# Return the results as a dictionary

gradients = {"dw": dw,

"db": db}

loss = np.squeeze(loss)

return gradients,loss

\# Compute Gradient Descent

\# Inputs: w

\# : b

\# : X

\# : Y

\# : numIerations

\# : learningRate

\# Ouputs : params, grads, losses,idx

def gradientDescent(w, b, X, Y, numIerations, learningRate):

losses=\[\]

 idx =\[\]

\# Iterate

for i in range(numIerations):

gradients,loss=forwardPropagation(w,b,X,Y)

#Get the derivates

dw = gradients\["dw"\]

db = gradients\["db"\]

w = w-learningRate\*dw

b = b-learningRate\*db

\# Store the loss

if i % 100 == 0:

idx.append(i)

losses.append(loss)

\# Set params and grads

params = {"w": w,

"b": b}

grads = {"dw": dw,

"db": db}

return params, grads, losses,idx

\# Predict the output for a training set

\# Inputs: w

\# : b

\# : X

\# Ouputs : yPredicted

def predict(w,b,X):

size=X.shape\[1\]

yPredicted=np.zeros((1,size))

Z=np.dot(w.T,X)

\# Compute the sigmoid

A=sigmoid(Z)

for i in range(A.shape\[1\]):

#If the value is > 0.5 then set as 1

if(A\[0\]\[i\] > 0.5):

yPredicted\[0\]\[i\]=1

else:

\# Else set as 0

 yPredicted\[0\]\[i\]=0

return yPredicted

#Normalize the data

\# Predict the output for a training set

\# Inputs: x

\# Ouputs : x (normalized)

def normalize(x):

x\_norm = None

x\_norm = np.linalg.norm(x,axis=1,keepdims=True)

x= x/x\_norm

return x

**1.2 R**

##################################################################################

#

\# Created by: Tinniam V Ganesh

\# Date : 4 Jan 2018

\# File: DLfunctions1.py

#

##################################################################################

source("RFunctions-1.R")

\# Define the sigmoid function

sigmoid <- function(z){

a <- 1/(1+ exp(-z))

a

}

\# Compute the loss

\# Inputs: numTraining

\# : Y

\# : A

\# Ouputs : loss

computeLoss <- function(numTraining,Y,A){

loss <- -1/numTraining\* sum(Y\*log(A) + (1-Y)\*log(1-A))

return(loss)

}

\# Compute forward propagation

\# Inputs: w

\# : b

\# : X

\# : Y

\# Ouputs : fwdProp (list)

forwardPropagation <- function(w,b,X,Y){

\# Compute Z

Z <- t(w) %\*% X +b

 #Set the number of samples

numTraining <- ncol(X)

\# Compute the activation function

A=sigmoid(Z)

#Compute the loss

loss <- computeLoss(numTraining,Y,A)

\# Compute the gradients dZ, dw and db

dZ<-A-Y

dw<-1/numTraining \* X %\*% t(dZ)

db<-1/numTraining\*sum(dZ)

fwdProp <- list("loss" = loss, "dw" = dw, "db" = db) return(fwdProp)

}

\# Perform one cycle of Gradient descent

\# Compute Gradient Descent

\# Inputs: w

\# : b

\# : X

\# : Y

\# : numIerations

\# : learningRate

\# Ouputs : gradDescnt (list)

gradientDescent <- function(w, b, X, Y, numIerations, learningRate){

losses <- NULL

idx <- NULL

\# Loop through the number of iterations

for(i in 1:numIerations){

fwdProp <-forwardPropagation(w,b,X,Y)

#Get the derivatives

dw <- fwdProp$dw

db <- fwdProp$db

#Perform gradient descent

w = w-learningRate\*dw

b = b-learningRate\*db

l <- fwdProp$loss

 # Stoe the loss

if(i %% 100 == 0){

idx <- c(idx,i)

losses <- c(losses,l)

}

}

\# Return the weights and losses

gradDescnt <-

list("w"=w,"b"=b,"dw"=dw,"db"=db,"losses"=losses,"idx"=idx) return(gradDescnt)

}

\# Compute the predicted value for input

\# Predict the output for a training set

\# Inputs: w

\# : b

\# : X

\# Ouputs : yPredicted

predict <- function(w,b,X){

m=dim(X)\[2\]

\# Create a ector of 0's

yPredicted=matrix(rep(0,m),nrow=1,ncol=m)

Z <- t(w) %\*% X +b

\# Compute sigmoid

A=sigmoid(Z)

for(i in 1:dim(A)\[2\]){

\# If A > 0.5 set value as 1

if(A\[1,i\] > 0.5)

yPredicted\[1,i\]=1

else

\# Else set as 0

yPredicted\[1,i\]=0

}

return(yPredicted)

}

\# Normalize the matrix

\# Predict the output for a training set

\# Inputs: x

\# Ouputs : normalized

normalize <- function(x){

#Create the norm of the matrix.Perform the Frobenius norm of the matrix n<-as.matrix(sqrt(rowSums(x^2)))

#Sweep by rows by norm. Note '1' in the function which performing on every row

normalized<-sweep(x, 1, n, FUN="/")

return(normalized)

**1.3 Octave**

##############################################################################################

#

\# Created by: Tinniam V Ganesh

\# Date : 4 Jan 2018

\# File: DLfunctions.m

#

##############################################################################################

1;

\# Define sigmoid function

function a = sigmoid(z)

a = 1 ./ (1+ exp(-z));

end

\# Compute the loss

\# Inputs: numTraining

\# : Y

\# : A

\# Ouputs : loss

function loss=computeLoss(numtraining,Y,A)

loss = -1/numtraining \* sum((Y .\* log(A)) + (1-Y) .\* log(1-A)); end

\# Perform forward propagation

\# Inputs: w

\# : b

\# : X

\# : Y

\# Ouputs : loss,dw,db,dZ

function \[loss,dw,db,dZ\] = forwardPropagation(w,b,X,Y)

% Compute Z

Z = w' \* X + b;

numtraining = size(X)(1,2);

\# Compute sigmoid

A = sigmoid(Z);

 #Compute loss. Note this is element wise product loss =computeLoss(numtraining,Y,A);

\# Compute the gradients dZ, dw and db

dZ = A-Y;

dw = 1/numtraining\* X \* dZ';

db =1/numtraining\*sum(dZ);

end

\# Compute Gradient Descent

\# Inputs: w

\# : b

\# : X

\# : Y

\# : numIerations

\# : learningRate

\# Ouputs : w,b,dw,db,losses,index

function \[w,b,dw,db,losses,index\]=gradientDescent(w, b, X, Y, numIerations, learningRate)

#Initialize losses and idx

losses=\[\];

index=\[\];

\# Loop through the number of iterations

for i=1:numIerations,

\[loss,dw,db,dZ\] = forwardPropagation(w,b,X,Y);

\# Perform Gradient descent

w = w - learningRate\*dw;

b = b - learningRate\*db;

if(mod(i,100) ==0)

\# Append index and loss

index = \[index i\];

losses = \[losses loss\];

endif

end

end

\# Determine the predicted value for dataset

\# Inputs: w

\# : b

\# : X

\# Ouputs : yPredicted

function yPredicted = predict(w,b,X)

m = size(X)(1,2);

yPredicted=zeros(1,m);

\# Compute Z

Z = w' \* X + b;

\# Compute sigmoid

A = sigmoid(Z);

for i=1:size(X)(1,2),

\# Set predicted as 1 if A > 0,5

if(A(1,i) >= 0.5)

yPredicted(1,i)=1;

else

yPredicted(1,i)=0;

endif

end

end

\# Normalize by dividing each value by the sum of squares

\# Predict the output for a training set

\# Inputs: x

\# Ouputs : normalized

function normalized = normalize(x)

\# Compute Frobenius norm. Square the elements, sum rows and then find square root

a = sqrt(sum(x .^ 2,2));

\# Perform element wise division

normalized = x ./ a;

end

\# Split into train and test sets

\# Predict the output for a training set

\# Inputs: dataset

\# :trainPercent

\# Ouputs : X\_train,y\_train,X\_test,y\_test

function \[X\_train,y\_train,X\_test,y\_test\] =

trainTestSplit(dataset,trainPercent)

 # Create a random index

ix = randperm(length(dataset));

\# Split into training

trainSize = floor(trainPercent/100 \* length(dataset));

train=dataset(ix(1:trainSize),:);

\# And test

test=dataset(ix(trainSize+1:length(dataset)),:);

X\_train = train(:,1:30);

y\_train = train(:,31);

X\_test = test(:,1:30);

y\_test = test(:,31);

end

**3.**

**Appendix 2 - Implementing a**

**simple Neural Network**

**2.1 Python**

##############################################################################################

#

\# Created by: Tinniam V Ganesh

\# Date : 11 Jan 2018

\# File: DLfunctions.py

#

##############################################################################################

import numpy as np

import matplotlib

import matplotlib.pyplot as plt

\# Conmpute the sigmoid of a vector

\# Inputs: z

\# Ouputs : a

def sigmoid(z):

a=1/(1+np.exp(-z))

return a

\# Compute the model shape given the dataset

\# Input : X

\# Y

\# Returns: modelParams

def getModelShape(X,Y):

numTraining= X.shape\[1\] # No of training examples

numFeats=X.shape\[0\] # No of input features

numHidden=4 # No of units in hidden layer

numOutput=Y.shape\[0\] # No of output units

\# Create a dcitionary of values

modelParams=

{"numTraining":numTraining,"numFeats":numFeats,"numHidden":numHidden,"numOutput":numOutput}

return(modelParams)

\# Initialize the model

\# Input : number of features

\# number of hidden units

\# number of units in output

\# Returns: Weight and bias matrices and vectors

def initializeModel(numFeats,numHidden,numOutput):

np.random.seed(2)

W1=np.random.randn(numHidden,numFeats)\*0.01 # Multiply by .01

b1=np.zeros((numHidden,1))

W2=np.random.randn(numOutput,numHidden)\*0.01

b2=np.zeros((numOutput,1))

\# Create a dictionary of the neural network parameters

nnParameters={'W1':W1,'b1':b1,'W2':W2,'b2':b2}

return(nnParameters)

\# Compute the forward propoagation through the neural network

\# Input : X

\# nnParameters

\# Returns : The Activation of 2nd layer

\# : Output and activation of layer 1 & 2

def forwardPropagation(X,nnParameters):

\# Get the parameters

W1=nnParameters\["W1"\]

b1=nnParameters\["b1"\]

W2=nnParameters\["W2"\]

b2=nnParameters\["b2"\]

\# Compute Z1 of the input layer

Z1=np.dot(W1,X)+b1

\# Compute the output A1 with the tanh activation function. The tanh activation function

\# performs better than the sigmoid function

A1=np.tanh(Z1)

\# Compute Z2 of the 2nd layer

Z2=np.dot(W2,A1)+b2

 # Compute the output A1 with the tanh activation function. The tanh activation function

\# performs better than the sigmoid function

A2=sigmoid(Z2)

cache={'Z1':Z1,'A1':A1,'Z2':Z2,'A2':A2}

return A2,cache

\# Compute the cost

\# Input : A2

\# :Y

\# Output: cost

def computeCost(A2,Y):

m= float(Y.shape\[1\])

\# Element wise multiply for logprobs

cost=-1/m \*np.sum(Y\*np.log(A2) + (1-Y)\*(np.log(1-A2)))

cost = np.squeeze(cost)

return cost

\# Compute the backpropoagation for 1 cycle

\# Input : Neural Network parameters - weights and biases

\# # Z and Activations of 2 layers

\# # Input features

\# # Output values Y

\# Returns: Gradients

def backPropagation(nnParameters, cache, X, Y):

numtraining=float(X.shape\[1\])

\# Get parameters

W1=nnParameters\["W1"\]

W2=nnParameters\["W2"\]

#Get the NN cache

A1=cache\["A1"\]

A2=cache\["A2"\]

\# Compute gradients

dZ2 = A2 - Y

dW2 = 1/numtraining \*np.dot(dZ2,A1.T)

db2 = 1/numtraining \*np.sum(dZ2,axis=1,keepdims=True)

dZ1 = np.multiply(np.dot(W2.T,dZ2), (1 - np.power(A1, 2)))

 dW1 = 1/numtraining\* np.dot(dZ1,X.T)

db1 = 1/numtraining \*np.sum(dZ1,axis=1,keepdims=True)

\# Create a dictionary

gradients = {"dW1": dW1,

"db1": db1,

"dW2": dW2,

"db2": db2}

return gradients

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients

\# : learning rate

#output : Updated weights after 1 iteration

def gradientDescent(nnParameters, gradients, learningRate):

W1 = nnParameters\['W1'\]

b1 = nnParameters\['b1'\]

W2 = nnParameters\['W2'\]

b2 = nnParameters\['b2'\]

dW1 = gradients\["dW1"\]

db1 = gradients\["db1"\]

dW2 = gradients\["dW2"\]

db2 = gradients\["db2"\]

W1 = W1-learningRate\*dW1

b1 = b1-learningRate\*db1

W2 = W2-learningRate\*dW2

b2 = b2-learningRate\*db2

\# Update the Neural Network parametrs

updatedNNParameters = {"W1": W1,

"b1": b1,

"W2": W2,

"b2": b2}

return updatedNNParameters

\# Compute the Neural Network by minimizing the cost

\# Input : Input data X,

\# Output Y

\# No of hidden units in hidden layer

\# No of iterations

\# Returns Updated weight and bias vectors of the neural network def computeNN(X, Y, numHidden, learningRate, numIterations = 10000): np.random.seed(3)

modelParams = getModelShape(X, Y)

numFeats=modelParams\['numFeats'\]

numOutput=modelParams\['numOutput'\]

costs=\[\]

nnParameters = initializeModel(numFeats,numHidden,numOutput)

W1 = nnParameters\['W1'\]

b1 = nnParameters\['b1'\]

W2 = nnParameters\['W2'\]

b2 = nnParameters\['b2'\]

\# Perform gradient descent

for i in range(0, numIterations):

\# Evaluate forward prop to compute activation at output layer A2, cache = forwardPropagation(X, nnParameters)

\# Compute cost from Activation at output and Y

cost = computeCost(A2, Y)

\# Perform backprop to compute gradients

gradients = backPropagation(nnParameters, cache, X, Y)

\# Use gradients to update the weights for each iteration.

nnParameters = gradientDescent(nnParameters, gradients,learningRate)

\# Print the cost every 1000 iterations

if i % 1000 == 0:

costs.append(cost)

print ("Cost after iteration %i: %f" %(i, cost))

return nnParameters,costs

\# Compute the predicted value for a given input

\# Input : Neural Network parameters

\# : Input data

def predict(nnParameters, X):

A2, cache = forwardPropagation(X, nnParameters)

predictions = (A2>0.5)

return predictions

\# Plot a decision boundary

\# Input : Input Model,

\# X

\# Y

\# Fig to be saved as

\# Returns Null

def plot\_decision\_boundary\_n(model, X, y,fig):

\# Set min and max values and give it some padding

x\_min, x\_max = X\[0, :\].min() - 1, X\[0, :\].max() + 1

y\_min, y\_max = X\[1, :\].min() - 1, X\[1, :\].max() + 1

colors=\['black','gold'\]

cmap = matplotlib.colors.ListedColormap(colors)

h = 0.01

\# Generate a grid of points with distance h between them

xx, yy = np.meshgrid(np.arange(x\_min, x\_max, h), np.arange(y\_min, y\_max, h))

\# Predict the function value for the whole grid

Z = model(np.c\_\[xx.ravel(), yy.ravel()\])

Z = Z.reshape(xx.shape)

\# Plot the contour and training examples

plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral)

plt.ylabel('x2')

plt.xlabel('x1')

plt.scatter(X\[0, :\], X\[1, :\], c=y, cmap=cmap)

plt.title("Decision Boundary for logistic regression") plt.savefig(fig, bbox\_inches='tight')

\# Plot a decision boundary

\# Input : Input Model,

\# X

\# Y

\# sz - Num of hiden units

\# lr - Learning rate

\# Fig to be saved as

\# Returns Null

def plot\_decision\_boundary(model, X, y,sz,lr,fig):

\# Set min and max values and give it some padding

x\_min, x\_max = X\[0, :\].min() - 1, X\[0, :\].max() + 1

 y\_min, y\_max = X\[1, :\].min() - 1, X\[1, :\].max() + 1

colors=\['black','gold'\]

cmap = matplotlib.colors.ListedColormap(colors)

h = 0.01

\# Generate a grid of points with distance h between them

xx, yy = np.meshgrid(np.arange(x\_min, x\_max, h), np.arange(y\_min, y\_max, h))

\# Predict the function value for the whole grid

Z = model(np.c\_\[xx.ravel(), yy.ravel()\])

Z = Z.reshape(xx.shape)

\# Plot the contour and training examples

plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral)

plt.ylabel('x2')

plt.xlabel('x1')

plt.scatter(X\[0, :\], X\[1, :\], c=y, cmap=cmap)

plt.title("Decision Boundary for hidden layer size:" + sz +" and learning rate:"+lr)

plt.savefig(fig, bbox\_inches='tight')

**2.2 R**

##############################################################################################

#

\# Created by: Tinniam V Ganesh

\# Date : 11 Jan 2018

\# File: DLfunctions2\_1.R

#

##############################################################################################

library(ggplot2)

\# Sigmoid function

sigmoid <- function(z){

a <- 1/(1+ exp(-z))

a

}

\# Compute the model shape given the dataset

\# Input : X - features

\# Y - output

#

\# Returns: no of training samples, no features, no hidden, no output getModelShape <- function(X,Y){

numTraining <- dim(X)\[2\] # No of training examples

numFeats <- dim(X)\[1\] # No of input features

numHidden<-4 # No of units in hidden layer

\# If Y is a row vector set numOutput as 1

if(is.null(dim(Y)))

numOutput <-1 # No of output units

else

numOutput <- dim(Y)\[1\]

\# Create a list of values

modelParams <-

list("numTraining"=numTraining,"numFeats"=numFeats,"numHidden"=numHidden,

"numOutput"=numOutput)

return(modelParams)

}

\# Initialize the model

\# Input : number of features

\# number of hidden units

\# number of units in output

\# Returns: Weight and bias matrices and vectors

initializeModel <- function(numFeats,numHidden,numOutput){

set.seed(2)

w= rnorm(numHidden\*numFeats)\*0.01

W1<-matrix(w,nrow=numHidden,ncol=numFeats) # Multiply by .01

b1<-matrix(rep(0,numHidden),nrow=numHidden,ncol=1)

w= rnorm(numOutput\*numHidden)

W2<-matrix(w,nrow=numOutput,ncol=numHidden)

b2<- matrix(rep(0,numOutput),nrow=numOutput,ncol=1)

\# Create a list of the neural network parameters

nnParameters<- list('W1'=W1,'b1'=b1,'W2'=W2,'b2'=b2)

return(nnParameters)

}

#Compute the forward propagation through the neural network

\# Input : Features

\# Weight and bias matrices and vectors

\# Returns : The Activation of 2nd layer

\# : Output and activation of layer 1 & 2

forwardPropagation <- function(X,nnParameters){

\# Get the parameters

W1<-nnParameters$W1

b1<-nnParameters$b1

W2<-nnParameters$W2

b2<-nnParameters$b2

z <- W1 %\*% X

\# Broadcast the bias vector for each row. Use 'sweep' The value '1' for MARGIN

 # indicates sweep each row by this value( add a column vector to each row).

\# If we want to sweep by column use '2'for MARGIN. Here a row vector is added to

\# column (braodcasting!)

Z1 <-sweep(z,1,b1,'+')

\# Compute the output A1 with the tanh activation function. The tanh activation function

\# performs better than the sigmoid function

A1<-tanh(Z1)

\# Compute Z2 of the 2nd layer

z <- W2 %\*% A1

\# Broadcast the bias vector for each row. Use 'sweep'

Z2 <- sweep(z,1,b2,'+')

\# Compute the output A1 with the tanh activation function. The tanh activation function

\# performs better than the sigmoid function

A2<-sigmoid(Z2)

cache <- list('Z1'=Z1,'A1'=A1,'Z2'=Z2,'A2'=A2)

return(list('A2'=A2, 'cache'=cache))

}

\# Compute the cost

\# Input : Activation of 2nd layer

\# : Output from data

\# Output: cost

computeCost <- function(A2,Y){

m= length(Y)

cost=-1/m\*sum(Y\*log(A2) + (1-Y)\*log(1-A2))

#cost=-1/m\*sum(a+b)

return(cost)

}

\# Compute the backpropoagation for 1 cycle

\# Input : Neural Network parameters - weights and biases

\# # Z and Activations of 2 layers

\# # Input features

\# # Output values Y

\# Returns: Gradients

backPropagation <- function(nnParameters, cache, X, Y){

numtraining<- dim(X)\[2\]

\# Get parameters

W1<-nnParameters$W1

W2<-nnParameters$W2

#Get the NN cache

A1<-cache$A1

A2<-cache$A2

dZ2 <- A2 - Y

dW2 <- 1/numtraining \* dZ2 %\*% t(A1)

db2 <- 1/numtraining \* rowSums(dZ2)

dZ1 <- t(W2) %\*% dZ2 \* (1 - A1^2)

dW1 = 1/numtraining\* dZ1 %\*% t(X)

db1 = 1/numtraining \* rowSums(dZ1)

gradients <- list("dW1"= dW1, "db1"= db1, "dW2"= dW2, "db2"= db2) return(gradients)

}

\# Gradient descent

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients

\# : learning rate

#output : Updated weights after 1 iteration

gradientDescent <- function(nnParameters, gradients, learningRate){

W1 <- nnParameters$W1

b1 <- nnParameters$b1

W2 <- nnParameters$W2

b2 <- nnParameters$b2

dW1<-gradients$dW1

 db1 <- gradients$db1

dW2 <- gradients$dW2

db2 <-gradients$db2

W1 <- W1-learningRate\*dW1

b1 <- b1-learningRate\*db1

W2 <- W2-learningRate\*dW2

b2 <- b2-learningRate\*db2

updatedNNParameters <- list("W1"= W1, "b1"= b1, "W2"= W2, "b2"= b2) return(updatedNNParameters)

}

\# Compute the Neural Network by minimizing the cost

\# Input : Input data X,

\# Output Y

\# No of hidden units in hidden layer

\# No of iterations

\# Returns Updated weight and bias vectors of the neural network computeNN <- function(X, Y, numHidden, learningRate, numIterations =

10000){

modelParams <- getModelShape(X, Y)

numFeats<-modelParams$numFeats

numOutput<-modelParams$numOutput

costs=NULL

nnParameters <- initializeModel(numFeats,numHidden,numOutput) W1 <- nnParameters$W1

b1<-nnParameters$b1

W2<-nnParameters$W2

b2<-nnParameters$b2

\# Perform gradient descent

for(i in 0: numIterations){

\# Evaluate forward prop to compute activation at output layer

#print("Here")

fwdProp = forwardPropagation(X, nnParameters)

\# Compute cost from Activation at output and Y

cost = computeCost(fwdProp$A2, Y)

\# Perform backprop to compute gradients

gradients = backPropagation(nnParameters, fwdProp$cache, X, Y)

 # Use gradients to update the weights for each iteration.

nnParameters = gradientDescent(nnParameters, gradients,learningRate)

\# Print the cost every 1000 iterations

if(i%%1000 == 0){

costs=c(costs,cost)

print(cost)

}

}

nnVals <- list("nnParameter"=nnParameters,"costs"=costs) return(nnVals)

}

\# Predict the output

predict <- function(parameters, X){

fwdProp <- forwardPropagation(X, parameters)

predictions <- fwdProp$A2>0.5

return (predictions)

}

\# Plot a decision boundary

\# This function uses the contour method

drawBoundary <- function(z,nn){

\# Find the minimum and maximum of the 2 fatures

xmin<-min(z\[,1\])

xmax<-max(z\[,1\])

ymin<-min(z\[,2\])

ymax<-max(z\[,2\])

a=seq(xmin,xmax,length=100)

b=seq(ymin,ymax,length=100)

grid <- expand.grid(x=a, y=b)

grid1 <-t(grid)

q <-predict(nn$nnParameter,grid1)

\# Works

contour(a, b, z=matrix(q, nrow=100), levels=0.5,

col="black", drawlabels=FALSE, lwd=2,xlim=range(2,10)) points(z\[,1\],z\[,2\],col=ifelse(z\[,3\]==1, "coral", "cornflowerblue"),pch=18)

}

\# Plot a decision boundary

\# This function uses ggplot2

plotDecisionBoundary <- function(z,nn,sz,lr){

xmin<-min(z\[,1\])

xmax<-max(z\[,1\])

ymin<-min(z\[,2\])

ymax<-max(z\[,2\])

a=seq(xmin,xmax,length=100)

b=seq(ymin,ymax,length=100)

grid <- expand.grid(x=a, y=b)

colnames(grid) <- c('x1', 'x2')

grid1 <-t(grid)

q <-predict(nn$nnParameter,grid1)

q1 <- t(data.frame(q))

q2 <- as.numeric(q1)

grid2 <- cbind(grid,q2)

colnames(grid2) <- c('x1', 'x2','q2')

z1 <- data.frame(z)

names(z1) <- c("x1","x2","y") atitle=paste("Decision boundary for hidden layer size:",sz,"learning rate:",lr) ggplot(z1) +

geom\_point(data = z1, aes(x = x1, y = x2, color = y)) +

stat\_contour(data = grid2, aes(x = x1, y = x2, z = q2,color=q2), alpha =

0.9)+

ggtitle(atitle)

}

\# Plot a decision boundary

\# This function uses ggplot2 and stat\_contour

plotBoundary <- function(z,nn){

xmin<-min(z\[,1\])

xmax<-max(z\[,1\])

ymin<-min(z\[,2\])

ymax<-max(z\[,2\])

a=seq(xmin,xmax,length=100)

b=seq(ymin,ymax,length=100)

grid <- expand.grid(x=a, y=b)

colnames(grid) <- c('x1', 'x2')

grid1 <-t(grid)

q <-predict(nn$nnParameter,grid1)

q1 <- t(data.frame(q))

q2 <- as.numeric(q1)

grid2 <- cbind(grid,q2)

colnames(grid2) <- c('x1', 'x2','q2')

z1 <- data.frame(z)

names(z1) <- c("x1","x2","y") data.plot <- ggplot() +

geom\_point(data = z1, aes(x = x1, y = x2, color = y)) +

coord\_fixed() +

xlab('x1') +

ylab('x2')

print(data.plot)

data.plot + stat\_contour(data = grid2, aes(x = x1, y = x2, z = q2), alpha = 0.9)

}

**2.3 Octave**

##############################################################################################

#

\# Created by: Tinniam V Ganesh

\# Date : 11 Jan 2018

\# File: DLfunctions2.m

#

##############################################################################################

1;

\# Define sigmoid function

function a = sigmoid(z)

a = 1 ./ (1+ exp(-z));

end

\# Compute the loss

\# Inputs: numTraining

\# : Y

\# : A

\# Ouputs : loss

function loss=computeLoss(numtraining,Y,A)

loss = -1/numtraining \* sum((Y .\* log(A)) + (1-Y) .\* log(1-A)); end

\# Compute the model shape given the dataset

\# Inputs: X

\# : Y

\# Ouputs : n\_x,m,n\_h,n\_y

function \[n\_x,m,n\_h,n\_y\] = getModelShape(X,Y)

m= size(X)(2);

n\_x=size(X)(1);

n\_h=4;

n\_y=size(Y)(1);

end

\# Initialize model

\# Inputs: n\_x

\# : n\_h

\# : n\_y

\# Ouputs : W1,b1,W2,b2

function \[W1,b1,W2,b2\] = modelInit(n\_x,n\_h,n\_y)

rand ("seed", 2);

W1=rand(n\_h,n\_x)\*0.01; # Set the initial values to a small number b1=zeros(n\_h,1);

W2=rand(n\_y,n\_h)\*0.01;

b2=zeros(n\_y,1);

end

\# Compute the forward propoagation through the neural network

\# Input : Features

\# Weight and bias matrices and vectors

\# Returns : The Activation of 2nd layer

\# : Output and activation of layer 1 & 2

function \[Z1,A1,Z2,A2\]= forwardPropagation(X,W1,b1,W2,b2)

\# Get the parameters

\# Determine the number of training samples

m=size(X)(2);

\# Compute Z1 of the input layer

\# Octave also handles broadcasting like Python!!

Z1=W1 \* X +b1;

\# Compute the output A1 with the tanh activation function. The tanh activation function

\# performs better than the sigmoid function

A1=tanh(Z1);

\# Compute Z2 of the input layer

Z2=W2 \* A1+b2;

\# Compute the output A1 with the tanh activation function. The tanh activation function

\# performs better than the sigmoid function

A2=sigmoid(Z2);

end

\# Compute the cost

\# Input : Activation of 2nd layer

\# : Output from data

\# Output: cost

function \[cost\] = computeCost(A,Y)

numTraining= size(Y)(2);

\# Element wise multiply for logprobs

cost = -1/numTraining \* sum((Y .\* log(A)) + (1-Y) .\* log(1-A)); end

\# Compute the backpropoagation for 1 cycle

\# Input : Neural Network parameters - weights and biases

\# # Z and Activations of 2 layers

\# # Input features

\# # Output values Y

\# Returns: Gradients

function \[dW1,db1,dW2,db2\]= backPropagation(W1,W2,A1,A2, X, Y) numTraining=size(X)(2);

dZ2 = A2 - Y;

dW2 = 1/numTraining \* dZ2 \* A1';

db2 = 1/numTraining \* sum(dZ2);

dZ1 = W2' \* dZ2 .\* (1 - power(A1, 2));

dW1 = 1/numTraining \* dZ1 \* X';

\# Note the '2' in the next statement indicates that a row sum has to done , 2nd dimension

db1 = 1/numTraining \* sum(dZ1,2);

end

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients

\# : learning rate

#output : Updated weights after 1 iteration

function \[W1,b1,W2,b2\]= gradientDescent(W1,b1,W2,b2, dW1,db1,dW2,db2, learningRate)

 W1 = W1-learningRate\*dW1;

b1 = b1-learningRate\*db1;

W2 = W2-learningRate\*dW2;

b2 = b2-learningRate\*db2;

end

\# Compute the Neural Network by minimizing the cost

\# Input : Input data X,

\# Output Y

\# No of hidden units in hidden layer

\# No of iterations

\# Returns Updated weight and bias vectors of the neural network function \[W1,b1,W2,b2,costs\]= computeNN(X, Y,numHidden, learningRate, numIterations = 10000)

\[numFeats,numTraining,n\_h,numOutput\] = getModelShape(X, Y);

costs=\[\];

\[W1,b1,W2,b2\] = modelInit(numFeats,numHidden,numOutput) ;

#W1 =\[-0.00416758, -0.00056267; -0.02136196, 0.01640271; -0.01793436,

\-0.00841747; 0.00502881 -0.01245288\];

#W2=\[-0.01057952, -0.00909008, 0.00551454, 0.02292208\];

#b1=\[0;0;0;0\];

#b2=\[0\];

\# Perform gradient descent

for i =0:numIterations

\# Evaluate forward prop to compute activation at output layer

\[Z1,A1,Z2,A2\] = forwardPropagation(X, W1,b1,W2,b2);

\# Compute cost from Activation at output and Y

cost = computeCost(A2, Y);

\# Perform backprop to compute gradients

\[dW1,db1,dW2,db2\] = backPropagation(W1,W2,A1,A2, X, Y);

\# Use gradients to update the weights for each iteration.

\[W1,b1,W2,b2\] = gradientDescent(W1,b1,W2,b2,

dW1,db1,dW2,db2,learningRate);

\# Print the cost every 1000 iterations

 if ( mod(i,1000) == 0)

costs =\[costs cost\];

#disp ("Cost after iteration"), disp(i),disp(cost); endif

endfor

end

\# Compute the predicted value for a given input

\# Input : Neural Network parameters

\# : Input data

\# Output : predictions

function \[predictions\]= predict(W1,b1,W2,b2, X)

\[Z1,A1,Z2,A2\] = forwardPropagation(X, W1,b1,W2,b2);

predictions = (A2>0.5);

end

\# Plot the decision boundary

function plotDecisionBoundary(data,W1,b1,W2,b2)

%Plot a non-linear decision boundary learned by the SVM

colormap ("default");

% Make classification predictions over a grid of values

x1plot = linspace(min(data(:,1)), max(data(:,1)), 400)';

x2plot = linspace(min(data(:,2)), max(data(:,2)), 400)';

\[X1, X2\] = meshgrid(x1plot, x2plot);

vals = zeros(size(X1));

\# Plot the prediction for the grid

for i = 1:size(X1, 2)

gridPoints = \[X1(:, i), X2(:, i)\];

vals(:, i)=predict(W1,b1,W2,b2,gridPoints');

endfor

scatter(data(:,1),data(:,2),8,c=data(:,3),"filled");

% Plot the boundary

hold on

#contour(X1, X2, vals, \[0 0\], 'LineWidth', 2);

contour(X1, X2, vals);

title ({"3 layer Neural Network decision boundary"}); hold off;

end

\# Plot the cost vs iterations

function plotLRCostVsIterations()

data=csvread("data.csv");

X=data(:,1:2);

Y=data(:,3);

lr=\[0.5,1.2,3\]

col='kbm'

for i=1:3

\[W1,b1,W2,b2,costs\]= computeNN(X', Y',4, learningRate=lr(i),

numIterations = 10000);

iterations = 1000\*\[0:10\];

hold on;

plot(iterations,costs,color=col(i),"linewidth", 3); hold off;

title ("Cost vs no of iterations for different learning rates"); xlabel("No of iterations")

ylabel("Cost")

legend('0.5','1.2','3.0')

endfor

end

\# Plot the cost vs number of hidden units

function plotHiddenCostVsIterations()

data=csvread("data1.csv");

X=data(:,1:2);

Y=data(:,3);

hidden=\[4,9,12\]

col='kbm'

for i=1:3

\[W1,b1,W2,b2,costs\]= computeNN(X', Y',hidden(i), learningRate=1.5, numIterations = 10000);

iterations = 1000\*\[0:10\];

hold on;

plot(iterations,costs,color=col(i),"linewidth", 3);

 hold off;

title ("Cost vs no of iterations for different number of hidden units"); xlabel("No of iterations")

ylabel("Cost")

legend('4','9','12')

endfor

end

**4.**

**Appendix 3 - Building a L- Layer**

**Deep Learning Network**

**3.1 Python**

\# -\*- coding: utf-8 -\*-

"""

############################################################################################################

#

\# File: DLfunctions34.py

\# Developer: Tinniam V Ganesh

\# Date : 30 Jan 2018

#

##########################################################################################################

@author: Ganesh

"""

import numpy as np

import matplotlib.pyplot as plt

import matplotlib

import matplotlib.pyplot as plt

from matplotlib import cm

\# Conmpute the sigmoid of a vector. Also return Z

def sigmoid(Z):

A=1/(1+np.exp(-Z))

cache=Z

return A,cache

\# Conmpute the Relu of a vector

def relu(Z):

A = np.maximum(0,Z)

cache=Z

return A,cache

\# Conmpute the tanh of a vector

def tanh(Z):

A = np.tanh(Z)

cache=Z

return A,cache

\# Compute the detivative of Relu

\# g'(z) = 1 if z >0 and 0 otherwise

def reluDerivative(dA, cache):

Z = cache

dZ = np.array(dA, copy=True) # just converting dz to a correct object.

\# When z <= 0, you should set dz to 0 as well.

dZ\[Z <= 0\] = 0

return dZ

\# Compute the derivative of sigmoid

\# Derivative g'(z) = a\* (1-a)

def sigmoidDerivative(dA, cache):

Z = cache

s = 1/(1+np.exp(-Z))

dZ = dA \* s \* (1-s)

return dZ

\# Compute the derivative of tanh

\# Derivative g'(z) = 1- a^2

def tanhDerivative(dA, cache):

Z = cache

a = np.tanh(Z)

dZ = dA \* (1 - np.power(a, 2))

return dZ

\# Initialize the model

\# Input : number of features

\# number of hidden units

\# number of units in output

\# Returns: Weight and bias matrices and vectors

def initializeModel(numFeats,numHidden,numOutput):

 np.random.seed(1)

W1=np.random.randn(numHidden,numFeats)\*0.01 # Multiply by .01

b1=np.zeros((numHidden,1))

W2=np.random.randn(numOutput,numHidden)\*0.01

b2=np.zeros((numOutput,1))

\# Create a dictionary of the neural network parameters

nnParameters={'W1':W1,'b1':b1,'W2':W2,'b2':b2}

return(nnParameters)

\# Initialize model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers def initializeDeepModel(layerDimensions):

np.random.seed(3)

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L. Initialize an empty dictionary layerParams = {}

for l in range(1,len(layerDimensions)):

\# Append to dictionary

layerParams\['W' + str(l)\] =

np.random.randn(layerDimensions\[l\],layerDimensions\[l-1\])\*0.01 # Multiply by

.01

layerParams\['b' + str(l)\] = np.zeros((layerDimensions\[l\],1))

return(layerParams)

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prec - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : The Activation of this layer

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

def layerActivationForward(A\_prev, W, b, activationFunc):

\# Compute Z

Z = np.dot(W,A\_prev) + b

forward\_cache = (A\_prev, W, b)

\# Compute the activation for sigmoid

if activationFunc == "sigmoid":

A, activation\_cache = sigmoid(Z)

\# Compute the activation for Relu

elif activationFunc == "relu":

A, activation\_cache = relu(Z)

\# Compute the activation for tanh

elif activationFunc == 'tanh':

A, activation\_cache = tanh(Z)

\# Cache the forward-cache and activation\_cache

cache = (forward\_cache, activation\_cache)

return A, cache

\# Compute the forward propagation for layers 1..L

\# Input : X - Input Features

\# paramaters: Weights and biases

\# hiddenActivationFunc - Activation function at hidden layers Relu/tanh

\# Returns : AL

\# caches

\# The forward propagtion uses the Relu/tanh activation from layer 1..L-1 and sigmoid actiovation at layer L

def forwardPropagationDeep(X, parameters,hiddenActivationFunc='relu'): caches = \[\]

\# Set A to X (A0)

A = X

L = int(len(parameters)/2) # number of layers in the neural network

\# Loop through from layer 1 to upto layer L

for l in range(1, L):

A\_prev = A

A, cache = layerActivationForward(A\_prev, parameters\['W'+str(l)\], parameters\['b'+str(l)\], activationFunc = hiddenActivationFunc) caches.append(cache)

\# Since this is binary classification use the sigmoid activation function in

\# last layer

AL, cache = layerActivationForward(A, parameters\['W'+str(L)\], parameters\['b'+str(L)\], activationFunc = "sigmoid") caches.append(cache)

return AL, caches

\# Compute the cost

\# Input : Activation of last layer

\# : Output from data

\# Output: cost

def computeCost(AL,Y):

m= float(Y.shape\[1\])

\# Element wise multiply for logprobs

cost=-1/m \*np.sum(Y\*np.log(AL) + (1-Y)\*(np.log(1-AL)))

cost = np.squeeze(cost)

return cost

\# Compute the backpropoagation for tnrough 1 layer

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# # Input features

\# # Output values Y

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

def layerActivationBackward(dA, cache, activationFunc):

forward\_cache, activation\_cache = cache

\# Compute derivative based on activation function

if activationFunc == "relu":

dZ = reluDerivative(dA, activation\_cache)

elif activationFunc == "sigmoid":

dZ = sigmoidDerivative(dA, activation\_cache)

elif activationFunc == "tanh":

 dZ = tanhDerivative(dA, activation\_cache)

\# Compute gradients

A\_prev, W, b = forward\_cache

numtraining = float(A\_prev.shape\[1\])

dW = 1/numtraining \*(np.dot(dZ,A\_prev.T))

db = 1/numtraining \* np.sum(dZ, axis=1, keepdims=True)

dA\_prev = np.dot(W.T,dZ)

return dA\_prev, dW, db

\# Compute the backpropoagation for 1 cycle, through all layers

\# Input : AL: Output of L layer Network - weights

\# # Y Real output

\# # caches -- list of caches containing:

\# every cache of layerActivationForward() with "relu"/"tanh"

\# #(it's caches\[l\], for l in range(L-1) i.e l = 0...L-2)

\# #the cache of layerActivationForward() with "sigmoid" (it's caches\[L-1\])

\# hiddenActivationFunc - Activation function at hidden layers

#

\# Returns:

\# gradients -- A dictionary with the gradients

\# gradients\["dA" + str(l)\] = ...

\# gradients\["dW" + str(l)\] = ...

def backwardPropagationDeep(AL, Y, caches,hiddenActivationFunc='relu'):

#initialize the gradients

gradients = {}

\# Set the number of layers

L = len(caches)

m = float(AL.shape\[1\])

Y = Y.reshape(AL.shape) # after this line, Y is the same shape as AL

\# Initializing the backpropagation

\# dl/dAL= -(y/a + (1-y)/(1-a)) - At the output layer

dAL = - (np.divide(Y, AL) - np.divide(1 - Y, 1 - AL))

\# Since this is a binary classification the activation at output is sigmoid

\# Get the gradients at the last layer

 current\_cache = caches\[L-1\]

gradients\["dA" + str(L)\], gradients\["dW" + str(L)\], gradients\["db" + str(L)\] =

layerActivationBackward(dAL, current\_cache, activationFunc = "sigmoid")

\# Traverse in the reverse direction

for l in reversed(range(L-1)):

\# Compute the gradients for L-1 to 1 for Relu/tanh

current\_cache = caches\[l\]

dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackward(gradients\['dA'+str(l+2)\], current\_cache, activationFunc = hiddenActivationFunc)

gradients\["dA" + str(l + 1)\] = dA\_prev\_temp

gradients\["dW" + str(l + 1)\] = dW\_temp

gradients\["db" + str(l + 1)\] = db\_temp

return gradients

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients

\# : learning rate

#output : Updated weights after 1 iteration

def gradientDescent(parameters, gradients, learningRate):

L = len(parameters) / 2

\# Update rule for each parameter.

for l in range(L):

parameters\["W" + str(l+1)\] = parameters\['W'+str(l+1)\] -learningRate\*

gradients\['dW' + str(l+1)\]

parameters\["b" + str(l+1)\] = parameters\['b'+str(l+1)\] -learningRate\*

gradients\['db' + str(l+1)\]

return parameters

\# Execute a L layer Deep learning model

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu /tanh

\# : learning rate

\# : num of iterations

#output : Updated weights and biases

def L\_Layer\_DeepModel(X, Y, layersDimensions, hiddenActivationFunc='relu', learning\_rate = .3, num\_iterations = 10000, fig="figx.png"):#lr was 0.009

np.random.seed(1)

costs = \[\]

#Initialize paramaters

parameters = initializeDeepModel(layersDimensions)

\# Perform gradient descent

for i in range(0, num\_iterations):

\# Perform one cycle of forward propagation

AL, caches = forwardPropagationDeep(X,

parameters,hiddenActivationFunc)

\# Compute cost.

cost = computeCost(AL, Y)

\# Compute gradients through 1 cycle of backprop

gradients = backwardPropagationDeep(AL, Y,

caches,hiddenActivationFunc)

\# Update parameters.

parameters = gradientDescent(parameters, gradients, learning\_rate)

\# Store the costs

if i % 100 == 0:

print ("Cost after iteration %i: %f" %(i, cost))

if i % 100 == 0:

costs.append(cost)

\# plot the cost

 fig1=plt.plot(np.squeeze(costs))

fig1=plt.ylabel('cost')

fig1=plt.xlabel('No of iterations(per 100)')

fig1=plt.title("Learning rate =" + str(learning\_rate))

#plt.show()

fig1.figure.savefig(fig,bbox\_inches='tight')

plt.clf()

return parameters

\# Plot a decision boundary

\# Input : Input Model,

\# X

\# Y

\# sz - Num of hiden units

\# lr - Learning rate

\# Fig to be saved as

\# Returns Null

def plot\_decision\_boundary(model, X, y,lr,fig):

\# Set min and max values and give it some padding

x\_min, x\_max = X\[0, :\].min() - 1, X\[0, :\].max() + 1

y\_min, y\_max = X\[1, :\].min() - 1, X\[1, :\].max() + 1

colors=\['black','yellow'\]

cmap = matplotlib.colors.ListedColormap(colors)

h = 0.01

\# Generate a grid of points with distance h between them

xx, yy = np.meshgrid(np.arange(x\_min, x\_max, h), np.arange(y\_min, y\_max, h))

\# Predict the function value for the whole grid

Z = model(np.c\_\[xx.ravel(), yy.ravel()\])

Z = Z.reshape(xx.shape)

\# Plot the contour and training examples

fig2=plt.contourf(xx, yy, Z, cmap="coolwarm")

fig2=plt.ylabel('x2')

fig2=plt.xlabel('x1')

fig2=plt.scatter(X\[0, :\], X\[1, :\], c=y, s=7,cmap=cmap)

fig2=plt.title("Decision Boundary for learning rate:"+lr) fig2.figure.savefig(fig, bbox\_inches='tight')

 plt.clf()

\# Predict the output for given input

\# Input : parameters

\# : X

\# Output: predictions

def predict(parameters, X):

A2, cache = forwardPropagationDeep(X, parameters)

predictions = (A2>0.5)

return predictions

\# Predict the probability scores for given data

\# Input : parameters

\# : X

\# Output: probability of output

def predict\_proba(parameters, X):

A2, cache = forwardPropagationDeep(X, parameters)

proba=A2

return proba

\# Plot a decision boundary

\# Input : Input Model,

\# X

\# Y

\# sz - Num of hiden units

\# lr - Learning rate

\# Fig to be saved as

\# Returns Null

def plot\_decision\_surface(model, X, y,sz,lr,fig):

\# Set min and max values and give it some padding

x\_min, x\_max = X\[0, :\].min() - 1, X\[0, :\].max() + 1

y\_min, y\_max = X\[1, :\].min() - 1, X\[1, :\].max() + 1

z\_min, z\_max = X\[2, :\].min() - 1, X\[2, :\].max() + 1

colors=\['black','gold'\]

cmap = matplotlib.colors.ListedColormap(colors)

h = 3

\# Generate a grid of points with distance h between them

xx, yy, zz = np.meshgrid(np.arange(x\_min, x\_max, h), np.arange(y\_min,

y\_max, h), np.arange(z\_min, z\_max, h))

\# Predict the function value for the whole grid

a=np.c\_\[xx.ravel(), yy.ravel(), zz.ravel()\]

Z = predict(parameters,a.T)

Z = Z.reshape(xx.shape)

\# Plot the contour and training examples

#plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral)

ax = plt.axes(projection='3d')

ax.contour3D(xx, yy, Z, 50, cmap='binary')

#plt.ylabel('x2')

#plt.xlabel('x1')

plt.scatter(X\[0, :\], X\[1, :\], c=y, cmap=cmap)

plt.title("Decision Boundary for hidden layer size:" + sz +" and learning rate:"+lr)

plt.show()

def plotSurface(X,parameters):

#xx, yy, zz = np.meshgrid(np.arange(10), np.arange(10), np.arange(10)) x\_min, x\_max = X\[0, :\].min() - 1, X\[0, :\].max() + 1

y\_min, y\_max = X\[1, :\].min() - 1, X\[1, :\].max() + 1

z\_min, z\_max = X\[2, :\].min() - 1, X\[2, :\].max() + 1

colors=\['red'\]

cmap = matplotlib.colors.ListedColormap(colors)

h = 1

xx, yy, zz = np.meshgrid(np.arange(x\_min, x\_max, h), np.arange(y\_min, y\_max, h),

np.arange(z\_min, z\_max, h))

\# For the meh grid values predict a model

a=np.c\_\[xx.ravel(), yy.ravel(), zz.ravel()\]

Z = predict(parameters,a.T)

r=Z.T

r1=r.reshape(xx.shape)

\# Find teh values for which the repdiction is 1

xx1=xx\[r1\]

yy1=yy\[r1\]

zz1=zz\[r1\]

\# Plot these values

 ax = plt.axes(projection='3d')

#ax.plot\_trisurf(xx1, yy1, zz1, cmap='bone', edgecolor='none'); ax.scatter3D(xx1, yy1,zz1, c=zz1,s=10,cmap=cmap)

#ax.plot\_surface(xx1, yy1, zz1, 'gray')

**3.2 R**

############################################################################################################

#

\# File : DLfunctions33.R

\# Author : Tinniam V Ganesh

\# Date : 30 Jan 2018

#

##########################################################################################################

library(ggplot2)

library(PRROC)

library(dplyr)

\# Compute the sigmoid of a vector

sigmoid <- function(Z){

A <- 1/(1+ exp(-Z))

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the Relu of a vector

relu <-function(Z){

A <- apply(Z, 1:2, function(x) max(0,x))

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the tanh activation of a vector

tanhActivation <- function(Z){

A <- tanh(Z)

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the detivative of Relu

\# g'(z) = 1 if z >0 and 0 otherwise

reluDerivative <-function(dA, cache){

Z <- cache

dZ <- dA

\# Create a logical matrix of values > 0

a <- Z > 0

\# When z <= 0, you should set dz to 0 as well. Perform an element wise multiple

dZ <- dZ \* a

return(dZ)

}

\# Compute the derivative of sigmoid

\# Derivative g'(z) = a\* (1-a)

sigmoidDerivative <- function(dA, cache){

Z <- cache

s <- 1/(1+exp(-Z))

dZ <- dA \* s \* (1-s)

return(dZ)

}

\# Compute the derivative of tanh

\# Derivative g'(z) = 1- a^2

tanhDerivative <- function(dA, cache){

Z = cache

a = tanh(Z)

dZ = dA \* (1 - a^2)

return(dZ)

}

\# Initialize model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers initializeDeepModel <- function(layerDimensions){

set.seed(2)

\# Initialize empty list

 layerParams <- list()

\# Note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Indices in R start from 1

for(l in 2:length(layersDimensions)){

\# Initialize a matrix of small random numbers of size l x l-1

\# Create random numbers of size l x l-1

w=rnorm(layersDimensions\[l\]\*layersDimensions\[l-1\])\*0.01

\# Create a weight matrix of size l x l-1 with this initial weights and

\# Add to list W1,W2... WL

layerParams\[\[paste('W',l-1,sep="")\]\] =

matrix(w,nrow=layersDimensions\[l\],

ncol=layersDimensions\[l-1\])

layerParams\[\[paste('b',l-1,sep="")\]\] = matrix(rep(0,layersDimensions\[l\]), nrow=layersDimensions\[l\],ncol=1)

}

return(layerParams)

}

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prec - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns(list) : The Activation of this layer

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

layerActivationForward <- function(A\_prev, W, b, activationFunc){

\# Compute Z

z = W %\*% A\_prev

\# Broadcast the bias 'b' by column

Z <-sweep(z,1,b,'+')

 forward\_cache <- list("A\_prev"=A\_prev, "W"=W, "b"=b)

\# Compute the activation for sigmoid

if(activationFunc == "sigmoid"){

vals = sigmoid(Z)

} else if (activationFunc == "relu"){ # Compute the activation for relu vals = relu(Z)

} else if(activationFunc == 'tanh'){ # Compute the activation for tanh vals = tanhActivation(Z)

}

\# Create a list of forward and activation cache

cache <- list("forward\_cache"=forward\_cache, "activation\_cache"=vals\[\['Z'\]\]) retvals <- list("A"=vals\[\['A'\]\],"cache"=cache) return(retvals)

}

\# Compute the forward propagation for layers 1..L

\# Input : X - Input Features

\# paramaters: Weights and biases

\# Returns (list) : AL

\# caches

\# The forward prooagtion uses the Relu/tanh activation from layer 1..L-1 and sigmoid actiovation at layer L

forwardPropagationDeep <- function(X,

parameters,hiddenActivationFunc='relu'){

caches <- list()

\# Set A to X (A0)

A <- X

L <- length(parameters)/2 # number of layers in the neural network

\# Loop through from layer 1 to upto layer L

for(l in 1:(L-1)){

A\_prev <- A

\# Zi = Wi x Ai-1 + bi and Ai = g(Zi)

\# Set W and b for layer 'l'

\# Loop throug from W1,W2... WL-1

W <- parameters\[\[paste("W",l,sep="")\]\]

b <- parameters\[\[paste("b",l,sep="")\]\]

\# Compute the forward propagation through layer 'l' using the activation function

 actForward <- layerActivationForward(A\_prev, W,

b,

activationFunc = hiddenActivationFunc)

A <- actForward\[\['A'\]\]

\# Append the cache A\_prev,W,b, Z

caches\[\[l\]\] <-actForward

}

\# Since this is binary classification use the sigmoid activation function in

\# last layer

\# Set the weights and biases for the last layer

W <- parameters\[\[paste("W",L,sep="")\]\]

b <- parameters\[\[paste("b",L,sep="")\]\]

\# Compute the sigmoid activation

actForward = layerActivationForward(A, W, b, activationFunc = "sigmoid") AL <- actForward\[\['A'\]\]

\# Append the output of this forward propagation through the last layer caches\[\[L\]\] <- actForward

\# Create a list of the final output and the caches

fwdPropDeep <- list("AL"=AL,"caches"=caches) return(fwdPropDeep)

}

\# Compute the cost

\# Input : Activation of last layer

\# : Output from data

\# Output: cost

computeCost <- function(AL,Y){

\# Element wise multiply for logprobs

m= length(Y)

cost=-1/m\*sum(Y\*log(AL) + (1-Y)\*log(1-AL))

#cost=-1/m\*sum(a+b)

return(cost)

}

\# Compute the backpropagation through a layer

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# # Input features

\# # Output values Y

\# Returns: Gradients as list

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

layerActivationBackward <- function(dA, cache, activationFunc){

\# Get A\_prev,W,b

forward\_cache <-cache\[\['forward\_cache'\]\]

\# Get Z

activation\_cache <- cache\[\['activation\_cache'\]\]

if(activationFunc == "relu"){

dZ <- reluDerivative(dA, activation\_cache)

} else if(activationFunc == "sigmoid"){

dZ <- sigmoidDerivative(dA, activation\_cache)

} else if(activationFunc == "tanh"){

dZ <- tanhDerivative(dA, activation\_cache)

}

A\_prev <- forward\_cache\[\['A\_prev'\]\]

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

numtraining = dim(A\_prev)\[2\]

dW = 1/numtraining \* dZ %\*% t(A\_prev)

db = 1/numtraining \* rowSums(dZ)

dA\_prev = t(W) %\*% dZ

retvals <- list("dA\_Prev"=dA\_prev,"dW"=dW,"db"=db) return(retvals)

}

\# Compute the backpropagation for 1 cycle through all layers

\# Input : AL: Output of L layer Network - weights

\# # Y Real output

\# # caches -- list of caches containing:

\# every cache of layerActivationForward() with "relu"/"tanh"

\# #(it's caches\[l\], for l in range(L-1) i.e l = 0...L-2)

\# #the cache of layerActivationForward() with "sigmoid" (it's caches\[L-1\])

\# hiddenActivationFunc - Activation function at hidden layers

#

\# Returns:

\# gradients -- A list with the gradients

\# gradients\["dA" + str(l)\] = ...

#

backwardPropagationDeep <- function(AL, Y,

caches,hiddenActivationFunc='relu'){

#initialize the gradients

gradients = list()

\# Set the number of layers

L = length(caches)

numTraining = dim(AL)\[2\]

\# Initializing the backpropagation

\# dl/dAL= -(y/a) - ((1-y)/(1-a)) - At the output layer

dAL = -( (Y/AL) -(1 - Y)/(1 - AL))

\# Since this is a binary classification the activation at output is sigmoid

\# Get the gradients at the last layer

\# Inputs: "AL, Y, caches".

\# Outputs: "gradients\["dAL"\], gradients\["dWL"\], gradients\["dbL"\]

\# Start with Layer L

\# Get the current cache

current\_cache = caches\[\[L\]\]$cache

#gradients\["dA" + str(L)\], gradients\["dW" + str(L)\], gradients\["db" + str(L)\] =

layerActivationBackward(dAL, current\_cache, activationFunc = "sigmoid") retvals <- layerActivationBackward(dAL, current\_cache, activationFunc =

"sigmoid")

\# Create gradients as lists

gradients\[\[paste("dA",L,sep="")\]\] <- retvals\[\['dA\_Prev'\]\]

gradients\[\[paste("dW",L,sep="")\]\] <- retvals\[\['dW'\]\]

gradients\[\[paste("db",L,sep="")\]\] <- retvals\[\['db'\]\]

\# Traverse in the reverse direction

for(l in (L-1):1){

\# Compute the gradients for L-1 to 1 for Relu/tanh

\# Inputs: "gradients\["dA" + str(l + 2)\], caches".

 # Outputs: "gradients\["dA" + str(l + 1)\] , gradients\["dW" + str(l + 1)\] , gradients\["db" + str(l + 1)\]

current\_cache = caches\[\[l\]\]$cache

retvals = layerActivationBackward(gradients\[\[paste('dA',l+1,sep="")\]\], current\_cache,

activationFunc = hiddenActivationFunc)

gradients\[\[paste("dA",l,sep="")\]\] <-retvals\[\['dA\_Prev'\]\]

gradients\[\[paste("dW",l,sep="")\]\] <- retvals\[\['dW'\]\]

gradients\[\[paste("db",l,sep="")\]\] <- retvals\[\['db'\]\]

}

return(gradients)

}

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients

\# : learning rate

#output : Updated weights after 1 iteration as a list

gradientDescent <- function(parameters, gradients, learningRate){

L = length(parameters)/2 # number of layers in the neural network

\# Update rule for each parameter. Use a for loop.

for(l in 1:L){

parameters\[\[paste("W",l,sep="")\]\] = parameters\[\[paste("W",l,sep="")\]\] -

learningRate\* gradients\[\[paste("dW",l,sep="")\]\]

parameters\[\[paste("b",l,sep="")\]\] = parameters\[\[paste("b",l,sep="")\]\] -

learningRate\* gradients\[\[paste("db",l,sep="")\]\]

}

return(parameters)

}

\# Execute a L layer Deep learning model

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu /tanh

\# : learning rate

\# : num of iterations

#output : Updated weights and biases

L\_Layer\_DeepModel <- function(X, Y, layersDimensions,

hiddenActivationFunc='relu',

learningRate = .3,

numIterations = 10000, print\_cost=False){

#Initialize costs vector as NULL

costs <- NULL

\# Parameters initialization.

parameters = initializeDeepModel(layersDimensions)

\# Loop (gradient descent)

for( i in 0:numIterations){

\# Forward propagation: \[LINEAR -> RELU\]\*(L-1) -> LINEAR -> SIGMOID.

retvals = forwardPropagationDeep(X, parameters,hiddenActivationFunc) AL <- retvals\[\['AL'\]\]

caches <- retvals\[\['caches'\]\]

\# Compute cost.

cost <- computeCost(AL, Y)

\# Backward propagation.

gradients = backwardPropagationDeep(AL, Y,

caches,hiddenActivationFunc)

\# Update parameters.

parameters = gradientDescent(parameters, gradients, learningRate) if(i%%1000 == 0){

costs=c(costs,cost)

print(cost)

}

}

retvals <- list("parameters"=parameters,"costs"=costs) return(retvals)

}

\# Predict the output for given input

\# Input : parameters

\# : X

\# Output: predictions

predict <- function(parameters, X,hiddenActivationFunc='relu'){

fwdProp <- forwardPropagationDeep(X, parameters,hiddenActivationFunc) predictions <- fwdProp$AL>0.5

return (predictions)

}

\# Plot a decision boundary

\# This function uses ggplot2

plotDecisionBoundary <- function(z,retvals,hiddenActivationFunc,lr){

\# Find the minimum and maximum for the data

xmin<-min(z\[,1\])

xmax<-max(z\[,1\])

ymin<-min(z\[,2\])

ymax<-max(z\[,2\])

\# Create a grid of values

a=seq(xmin,xmax,length=100)

b=seq(ymin,ymax,length=100)

grid <- expand.grid(x=a, y=b)

colnames(grid) <- c('x1', 'x2')

grid1 <-t(grid)

\# Predict the output for this grid

q <-predict(retvals$parameters,grid1,hiddenActivationFunc) q1 <- t(data.frame(q))

q2 <- as.numeric(q1)

grid2 <- cbind(grid,q2)

colnames(grid2) <- c('x1', 'x2','q2')

z1 <- data.frame(z)

names(z1) <- c("x1","x2","y") atitle=paste("Decision boundary for learning rate:",lr)

\# Plot the contour of the boundary

ggplot(z1) +

geom\_point(data = z1, aes(x = x1, y = x2, color = y)) +

stat\_contour(data = grid2, aes(x = x1, y = x2, z = q2,color=q2), alpha =

0.9)+

ggtitle(atitle)

}

\# Predict the probability scores for given data set

\# Input : parameters

\# : X

\# Output: probability of output

computeScores <- function(parameters, X,hiddenActivationFunc='relu'){

fwdProp <- forwardPropagationDeep(X, parameters,hiddenActivationFunc) scores <- fwdProp$AL

return (scores)

}

 

**3.3 Octave**

############################################################################################################

#

\# File: DLfunctions3.m

\# Developer: Tinniam V Ganesh

\# Date : 30 Jan 2018

#

##########################################################################################################

1;

\# Define sigmoid function

function \[A,cache\] = sigmoid(Z)

A = 1 ./ (1+ exp(-Z));

cache=Z;

end

\# Define Relu function

function \[A,cache\] = relu(Z)

A = max(0,Z);

cache=Z;

end

\# Define Relu function

function \[A,cache\] = tanhAct(Z)

A = tanh(Z);

cache=Z;

end

\# Define Relu Derivative

function \[dZ\] = reluDerivative(dA,cache)

Z = cache;

dZ = dA;

\# Get elements that are greater than 0

a = (Z > 0);

\# Select only those elements where Z > 0

 dZ = dZ .\* a;

end

\# Define Sigmoid Derivative

function \[dZ\] = sigmoidDerivative(dA,cache)

Z = cache;

s = 1 ./ (1+ exp(-Z));

dZ = dA .\* s .\* (1-s);

end

\# Define Tanh Derivative

function \[dZ\] = tanhDerivative(dA,cache)

Z = cache;

a = tanh(Z);

dZ = dA .\* (1 - a .^ 2);

end

\# Initialize the model

\# Input : number of features

\# number of hidden units

\# number of units in output

\# Returns: Weight and bias matrices and vectors

\# Initialize model for L layers

\# Input : Vector of units in each layer

\# Returns: Initial weights and biases matrices for all layers as a cell array function \[W b\] = initializeDeepModel(layerDimensions)

rand ("seed", 3);

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Create cell arrays for Weights and biases

for l =2:size(layerDimensions)(2)

W{l-1} = rand(layerDimensions(l),layerDimensions(l-1))\*0.01; #

Multiply by .01

b{l-1} = zeros(layerDimensions(l),1);

endfor

end

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prec - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : A, forward\_cache, activation\_cache

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

function \[A forward\_cache activation\_cache\] = layerActivationForward(A\_prev, W, b, activationFunc)

\# Compute Z

Z = W \* A\_prev +b;

\# Create a cell array

forward\_cache = {A\_prev W b};

\# Compute the activation for sigmoid

if (strcmp(activationFunc,"sigmoid"))

\[A activation\_cache\] = sigmoid(Z);

elseif (strcmp(activationFunc, "relu")) # Compute the activation for Relu

\[A activation\_cache\] = relu(Z);

elseif(strcmp(activationFunc,'tanh')) # Compute the activation for tanh

\[A activation\_cache\] = tanhAct(Z);

endif

end

\# Compute the forward propagation for layers 1..L

\# Input : X - Input Features

\# paramaters: Weights and biases

\# hiddenActivationFunc - Activation function at hidden layers Relu/tanh

\# Returns : AL, forward\_caches, activation\_caches as a cell array

\# The forward propoagtion uses the Relu/tanh activation from layer 1..L-1 and sigmoid actiovation at layer L

function \[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights,biases, hiddenActivationFunc='relu')

 # Create an empty cell array

forward\_caches = {};

activation\_caches = {};

\# Set A to X (A0)

A = X;

L = length(weights); # number of layers in the neural network

\# Loop through from layer 1 to upto layer L

for l =1:L-1

A\_prev = A;

\# Zi = Wi x Ai-1 + bi and Ai = g(Zi)

W = weights{l};

b = biases{l};

\[A forward\_cache activation\_cache\] = layerActivationForward(A\_prev, W,b, activationFunc=hiddenActivationFunc);

forward\_caches{l}=forward\_cache;

activation\_caches{l} = activation\_cache;

endfor

\# Since this is binary classification use the sigmoid activation function in

\# last layer

W = weights{L};

b = biases{L};

\[AL, forward\_cache activation\_cache\] = layerActivationForward(A, W,b, activationFunc = "sigmoid");

forward\_caches{L}=forward\_cache;

activation\_caches{L} = activation\_cache;

end

\# Compute the cost

\# Input : Activation of last layer

\# : Output from data

\# Output: cost

function \[cost\]= computeCost(AL,Y)

numTraining= size(Y)(2);

\# Element wise multiply for logprobs

cost = -1/numTraining \* sum((Y .\* log(AL)) + (1-Y) .\* log(1-AL)); end

\# Compute the layerActivationBackward

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# Returns: dA\_prev, dW, db

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

function \[dA\_prev dW db\] = layerActivationBackward(dA, forward\_cache, activation\_cache, activationFunc)

if (strcmp(activationFunc,"relu"))

dZ = reluDerivative(dA, activation\_cache);

elseif (strcmp(activationFunc,"sigmoid"))

dZ = sigmoidDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "tanh"))

dZ = tanhDerivative(dA, activation\_cache);

endif

A\_prev = forward\_cache{1};

W =forward\_cache{2};

b = forward\_cache{3};

numTraining = size(A\_prev)(2);

dW = 1/numTraining \* dZ \* A\_prev';

db = 1/numTraining \* sum(dZ,2);

dA\_prev = W'\*dZ;

end

\# Compute the backpropoagation for 1 cycle

\# Input : AL: Output of L layer Network - weights

\# # Y Real output

\# # activation\_caches

\# # forward\_caches

\# every cache of layerActivationForward() with "relu"/"tanh"

\# #(it's caches\[l\], for l in range(L-1) i.e l = 0...L-2)

\# #the cache of layerActivationForward() with "sigmoid" (it's caches\[L-1\])

\# hiddenActivationFunc - Activation function at hidden layers

#

\# Returns (cell array): gradsDA,gradsDW, gradsDB

function \[gradsDA gradsDW gradsDB\]= backwardPropagationDeep(AL, Y,

activation\_caches,forward\_caches,hiddenActivationFunc='relu')

\# Set the number of layers

L = length(activation\_caches);

m = size(AL)(2);

\# Initializing the backpropagation

\# dl/dAL= -(y/a + (1-y)/(1-a)) - At the output layer

dAL = -((Y ./ AL) - (1 - Y) ./ ( 1 - AL));

\# Since this is a binary classification the activation at output is sigmoid

\# Get the gradients at the last layer

\# Inputs: "AL, Y, caches".

\# Outputs: "gradients\["dAL"\], gradients\["dWL"\], gradients\["dbL"\]

activation\_cache = activation\_caches{L};

forward\_cache = forward\_caches(L);

\# Note the cell array includes an array of forward caches. To get to this we need to include the index {1}

\[dA dW db\] = layerActivationBackward(dAL, forward\_cache{1},

activation\_cache, activationFunc = "sigmoid");

gradsDA{L}= dA;

gradsDW{L}= dW;

gradsDB{L}= db;

\# Traverse in the reverse direction

for l =(L-1):-1:1

\# Compute the gradients for L-1 to 1 for Relu/tanh

\# Inputs: "gradients\["dA" + str(l + 2)\], caches".

\# Outputs: "gradients\["dA" + str(l + 1)\] , gradients\["dW" + str(l + 1)\] , gradients\["db" + str(l + 1)\]

activation\_cache = activation\_caches{l};

forward\_cache = forward\_caches(l);

#dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackward(gradients\['dA'+str(l+1)\], current\_cache, activationFunc = "relu")

\# dAl the dervative of the activation of the lth layer,is the first element dAl= gradsDA{l+1};

 \[dA\_prev\_temp, dW\_temp, db\_temp\] = layerActivationBackward(dAl, forward\_cache{1}, activation\_cache, activationFunc = hiddenActivationFunc); gradsDA{l}= dA\_prev\_temp;

gradsDW{l}= dW\_temp;

gradsDB{l}= db\_temp;

endfor

end

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients

\# : learning rate

#output : Updated weights and biases after 1 iteration

function \[weights biases\] = gradientDescent(weights, biases,gradsW,gradsB, learningRate)

L = size(weights)(2); # number of layers in the neural network

\# Update rule for each parameter.

for l=1:L

weights{l} = weights{l} -learningRate\* gradsW{l};

biases{l} = biases{l} -learningRate\* gradsB{l};

endfor

end

\# Execute a L layer Deep learning model

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu /tanh

\# : learning rate

\# : num of iterations

#output : Updated weights and biases

function \[weights biases costs\] = L\_Layer\_DeepModel(X, Y, layersDimensions, hiddenActivationFunc='relu', learning\_rate = .3, num\_iterations = 10000)#lr was 0.009

rand ("seed", 1);

costs = \[\] ;

\# Parameters initialization.

\[weights biases\] = initializeDeepModel(layersDimensions);

\# Loop (gradient descent)

for i = 0:num\_iterations

\# Forward propagation: \[LINEAR -> RELU\]\*(L-1) -> LINEAR -> SIGMOID.

\[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights, biases,hiddenActivationFunc);

\# Compute cost.

cost = computeCost(AL, Y);

\# Backward propagation.

\[gradsDA gradsDW gradsDB\] = backwardPropagationDeep(AL, Y,

activation\_caches,forward\_caches,hiddenActivationFunc);

\# Update parameters.

\[weights biases\] = gradientDescent(weights,biases,

gradsDW,gradsDB,learning\_rate);

\# Print the cost every 1000 iterations

if ( mod(i,1000) == 0)

costs =\[costs cost\];

#disp ("Cost after iteration"), disp(i),disp(cost); printf("Cost after iteration i=%i cost=%d\\n",i,cost); endif

endfor

end

#Plot cost vs iterations

function plotCostVsIterations(maxIterations,costs)

iterations=\[0:1000:maxIterations\];

 plot(iterations,costs);

title ("Cost vs no of iterations for different learning rates"); xlabel("No of iterations");

ylabel("Cost");

end;

\# Compute the predicted value for a given input

\# Input : Neural Network parameters

\# : Input data

function \[predictions\]= predict(weights, biases, X,hiddenActivationFunc="relu")

\[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights, biases,hiddenActivationFunc);

predictions = (AL>0.5);

end

\# Plot the decision boundary

function plotDecisionBoundary(data,weights,

biases,hiddenActivationFunc="relu")

%Plot a non-linear decision boundary learned by the SVM

colormap ("summer");

% Make classification predictions over a grid of values

x1plot = linspace(min(data(:,1)), max(data(:,1)), 400)';

x2plot = linspace(min(data(:,2)), max(data(:,2)), 400)';

\[X1, X2\] = meshgrid(x1plot, x2plot);

vals = zeros(size(X1));

\# Plot the prediction for the grid

for i = 1:size(X1, 2)

gridPoints = \[X1(:, i), X2(:, i)\];

vals(:, i)=predict(weights,

biases,gridPoints',hiddenActivationFunc=hiddenActivationFunc); endfor

scatter(data(:,1),data(:,2),8,c=data(:,3),"filled");

% Plot the boundary

hold on

#contour(X1, X2, vals, \[0 0\], 'LineWidth', 2);

contour(X1, X2, vals,"linewidth",4);

title ({"3 layer Neural Network decision boundary"});

 hold off;

end

\# Compute scores

function \[AL\]= scores(weights, biases, X,hiddenActivationFunc="relu")

\[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights, biases,hiddenActivationFunc);

end

**5.**

**Appendix 4 - Deep Learning**

**network with the Softmax**

**4.1 Python**

\# -\*- coding: utf-8 -\*-

"""

############################################################################################################

#

\# File: DLfunctions41.py

\# Developer: Tinniam V Ganesh

\# Date : 26 Feb 2018

#

##########################################################################################################

@author: Ganesh

"""

import numpy as np

import matplotlib.pyplot as plt

import matplotlib

import matplotlib.pyplot as plt

from matplotlib import cm

\# Conmpute the Relu of a vector

def relu(Z):

A = np.maximum(0,Z)

cache=Z

return A,cache

\# Conmpute the softmax of a vector

def softmax(Z):

\# get unnormalized probabilities

exp\_scores = np.exp(Z.T)

\# normalize them for each example

A = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

cache=Z

 return A,cache

\# Compute the derivative of Relu

def reluDerivative(dA, cache):

Z = cache

dZ = np.array(dA, copy=True) # just converting dz to a correct object.

\# When z <= 0, you should set dz to 0 as well.

dZ\[Z <= 0\] = 0

return dZ

\# Compute the derivative of softmax

def softmaxDerivative(dA, cache,y,numTraining):

\# Note : dA not used. dL/dZ = dL/dA \* dA/dZ = pi-yi

Z = cache

\# Compute softmax

exp\_scores = np.exp(Z.T)

\# normalize them for each example

probs = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

\# compute the gradient on scores

dZ = probs

\# dZ = pi- yi

dZ\[range(int(numTraining)),y\] -= 1

return(dZ)

\# Initialize the model

\# Input : number of features

\# number of hidden units

\# number of units in output

\# Returns: Weight and bias matrices and vectors

def initializeModel(numFeats,numHidden,numOutput):

np.random.seed(1)

W1=np.random.randn(numHidden,numFeats)\*0.01 # Multiply by .01

b1=np.zeros((numHidden,1))

W2=np.random.randn(numOutput,numHidden)\*0.01

b2=np.zeros((numOutput,1))

 # Create a dictionary of the neural network parameters nnParameters={'W1':W1,'b1':b1,'W2':W2,'b2':b2}

return(nnParameters)

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prec - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : A, cache

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

def layerActivationForward(A\_prev, W, b, activationFunc):

\# Compute Z

Z = np.dot(W,A\_prev) + b

forward\_cache = (A\_prev, W, b)

\# Compute the activation for sigmoid

if activationFunc == "sigmoid":

A, activation\_cache = sigmoid(Z)

\# Compute the activation for Relu

elif activationFunc == "relu":

A, activation\_cache = relu(Z)

\# Compute the activation for tanh

elif activationFunc == 'tanh':

A, activation\_cache = tanh(Z)

\# Compute the activation for softmax

elif activationFunc == 'softmax':

A, activation\_cache = softmax(Z)

cache = (forward\_cache, activation\_cache)

return A, cache

\# Compute the backpropoagation for 1 cycle

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# # y

\# # activationFunc

\# Returns: dA\_prev, dW, db

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

def layerActivationBackward(dA, cache, y, activationFunc):

forward\_cache, activation\_cache = cache

A\_prev, W, b = forward\_cache

numtraining = float(A\_prev.shape\[1\])

if activationFunc == "relu":

dZ = reluDerivative(dA, activation\_cache)

elif activationFunc == "sigmoid":

dZ = sigmoidDerivative(dA, activation\_cache)

elif activationFunc == "tanh":

dZ = tanhDerivative(dA, activation\_cache)

elif activationFunc == "softmax":

dZ = softmaxDerivative(dA, activation\_cache,y,numtraining)

if activationFunc == 'softmax':

dW = 1/numtraining \* np.dot(A\_prev,dZ)

db = np.sum(dZ, axis=0, keepdims=True)

dA\_prev = np.dot(dZ,W)

else:

#print(numtraining)

dW = 1/numtraining \*(np.dot(dZ,A\_prev.T))

#print("dW=",dW)

db = 1/numtraining \* np.sum(dZ, axis=1, keepdims=True)

#print("db=",db)

dA\_prev = np.dot(W.T,dZ)

return dA\_prev, dW, db

\# Plot a decision boundary

\# Input : Input Model,

\# X

\# Y

\# W1

\# b1

\# W2

\# fig

\# Returns Null

def plot\_decision\_boundary(X, y,W1,b1,W2,b2,fig1):

#plot\_decision\_boundary(lambda x: predict(parameters, x.T),

x1,y1.T,str(0.3),"fig2.png")

h = 0.02

x\_min, x\_max = X\[:, 0\].min() - 1, X\[:, 0\].max() + 1

y\_min, y\_max = X\[:, 1\].min() - 1, X\[:, 1\].max() + 1

xx, yy = np.meshgrid(np.arange(x\_min, x\_max, h),

np.arange(y\_min, y\_max, h))

Z = np.dot(np.maximum(0, np.dot(np.c\_\[xx.ravel(), yy.ravel()\], W1.T) +

b1.T), W2.T) + b2.T

Z = np.argmax(Z, axis=1)

Z = Z.reshape(xx.shape)

fig = plt.figure()

plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral, alpha=0.8)

plt.scatter(X\[:, 0\], X\[:, 1\], c=y, s=40, cmap=plt.cm.Spectral) plt.xlim(xx.min(), xx.max())

plt.ylim(yy.min(), yy.max())

**4.2 R**

############################################################################################################

#

\# File: DLfunctions41.R

\# Developer: Tinniam V Ganesh

\# Date : 26 Feb 2018

#

##########################################################################################################

\# Compute the Relu of a vector

relu <-function(Z){

A <- apply(Z, 1:2, function(x) max(0,x))

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the softmax of a vector

softmax <- function(Z){

\# get unnormalized probabilities

exp\_scores = exp(t(Z))

\# normalize them for each example

A = exp\_scores / rowSums(exp\_scores)

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the detivative of Relu

reluDerivative <-function(dA, cache){

Z <- cache

dZ <- dA

\# Create a logical matrix of values > 0

a <- Z > 0

\# When z <= 0, you should set dz to 0 as well. Perform an element wise multiple

 dZ <- dZ \* a

return(dZ)

}

\# Compute the detivative of softmax

softmaxDerivative <- function(dA, cache ,y,numTraining){

\# Note : dA not used. dL/dZ = dL/dA \* dA/dZ = pi-yi

Z <- cache

\# Compute softmax

exp\_scores = exp(t(Z))

\# normalize them for each example

probs = exp\_scores / rowSums(exp\_scores)

\# Get the number of 0, 1 and 2 classes and store in a,b,c

a=sum(y==0)

b=sum(y==1)

c=sum(y==2)

\# Create a yi matrix based on yi for each class

m= matrix(rep(c(1,0,0),a),nrow=a,ncol=3,byrow=T)

n= matrix(rep(c(0,1,0),b),nrow=b,ncol=3,byrow=T)

o= matrix(rep(c(0,0,1),c),nrow=c,ncol=3,byrow=T)

\# Stack them vertically

yi=rbind(m,n,o)

dZ = probs-yi

return(dZ)

}

\# Initialize the model

\# Input : number of features

\# number of hidden units

\# number of units in output

\# Returns: list of Weight and bias matrices and vectors

initializeModel <- function(numFeats,numHidden,numOutput){

set.seed(2)

a<-rnorm(numHidden\*numFeats)\*0.01 # Multiply by .01

W1 <- matrix(a,nrow=numHidden,ncol=numFeats)

a<-rnorm(numHidden\*1)

b1 <- matrix(a,nrow=numHidden,ncol=1)

a<-rnorm(numOutput\*numHidden)\*0.01

 W2 <- matrix(a,nrow=numOutput,ncol=numHidden) a<-rnorm(numOutput\*1)

b2 <- matrix(a,nrow=numOutput,ncol=1)

parameters <- list("W1"=W1,"b1"=b1,"W2"=W2,"b2"=b2) return(parameters)

}

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prev - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : A list of forward\_cache, activation\_cache, cache

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

layerActivationForward <- function(A\_prev, W, b, activationFunc){

\# Compute Z

z = W %\*% A\_prev

Z <-sweep(z,1,b,'+')

forward\_cache <- list("A\_prev"=A\_prev, "W"=W, "b"=b)

\# Compute the activation for sigmoid

if(activationFunc == "sigmoid"){

vals = sigmoid(Z)

} else if (activationFunc == "relu"){ # Compute the activation for relu vals = relu(Z)

} else if(activationFunc == 'tanh'){ # Compute the activation for tanh vals = tanhActivation(Z)

} else if(activationFunc == 'softmax'){

vals = softmax(Z)

}

cache <- list("forward\_cache"=forward\_cache, "activation\_cache"=vals\[\['Z'\]\]) retvals <- list("A"=vals\[\['A'\]\],"cache"=cache) return(retvals)

}

\# Compute the backpropagation for 1 cycle

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# # y

\# # activationFunc

\# Returns: Gradients - a list of dA\_prev, dW, db

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

layerActivationBackward <- function(dA, cache, y, activationFunc){

\# Get A\_prev,W,b

forward\_cache <-cache\[\['forward\_cache'\]\]

activation\_cache <- cache\[\['activation\_cache'\]\]

A\_prev <- forward\_cache\[\['A\_prev'\]\]

numtraining = dim(A\_prev)\[2\]

\# Get Z

if(activationFunc == "relu"){

dZ <- reluDerivative(dA, activation\_cache)

} else if(activationFunc == "sigmoid"){

dZ <- sigmoidDerivative(dA, activation\_cache)

} else if(activationFunc == "tanh"){

dZ <- tanhDerivative(dA, activation\_cache)

} else if(activationFunc == "softmax"){

dZ <- softmaxDerivative(dA, activation\_cache,y,numtraining)

}

\# Check if softmax

if (activationFunc == 'softmax'){

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

dW = 1/numtraining \* A\_prev%\*%dZ

db = 1/numtraining\* matrix(colSums(dZ),nrow=1,ncol=3)

dA\_prev = dZ %\*%W

} else {

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

numtraining = dim(A\_prev)\[2\]

dW = 1/numtraining \* dZ %\*% t(A\_prev)

 db = 1/numtraining \* rowSums(dZ)

dA\_prev = t(W) %\*% dZ

}

retvals <- list("dA\_prev"=dA\_prev,"dW"=dW,"db"=db) return(retvals)

}

\# Plot a decision boundary for Softmax output activation

\# This function uses ggplot2

plotDecisionBoundary <- function(Z,W1,b1,W2,b2){

xmin<-min(Z\[,1\])

xmax<-max(Z\[,1\])

ymin<-min(Z\[,2\])

ymax<-max(Z\[,2\])

\# Create a grid of points

a=seq(xmin,xmax,length=100)

b=seq(ymin,ymax,length=100)

grid <- expand.grid(x=a, y=b)

colnames(grid) <- c('x1', 'x2')

grid1 <-t(grid)

\# Predict the output based on the grid of points

retvals <- layerActivationForward(grid1,W1,b1,'relu')

A1 <- retvals\[\['A'\]\]

cache1 <- retvals\[\['cache'\]\]

forward\_cache1 <- cache1\[\['forward\_cache1'\]\]

activation\_cache <- cache1\[\['activation\_cache'\]\]

retvals = layerActivationForward(A1,W2,b2,'softmax')

A2 <- retvals\[\['A'\]\]

cache2 <- retvals\[\['cache'\]\]

forward\_cache2 <- cache2\[\['forward\_cache1'\]\]

activation\_cache2 <- cache2\[\['activation\_cache'\]\]

 # From the softmax probabilities pick the one with the highest probability q= apply(A2,1,which.max)

q1 <- t(data.frame(q))

q2 <- as.numeric(q1)

grid2 <- cbind(grid,q2)

colnames(grid2) <- c('x1', 'x2','q2')

z1 <- data.frame(Z)

names(z1) <- c("x1","x2","y") atitle=paste("Decision boundary")

ggplot(z1) +

geom\_point(data = z1, aes(x = x1, y = x2, color = y)) +

stat\_contour(data = grid2, aes(x = x1, y = x2, z = q2,color=q2), alpha =

0.9)+

ggtitle(atitle) + scale\_colour\_gradientn(colours = brewer.pal(10,

"Spectral"))

}

\# Predict the output

computeScores <- function(parameters, X,hiddenActivationFunc='relu'){

fwdProp <- forwardPropagationDeep(X, parameters,hiddenActivationFunc) scores <- fwdProp$AL

return (scores)

}

**4.3 Octave**

############################################################################################################

#

\# File: DLfunctions41.m

\# Developer: Tinniam V Ganesh

\# Date : 26 Feb 2018

#

##########################################################################################################

1;

\# Define Relu function

function \[A,cache\] = relu(Z)

A = max(0,Z);

cache=Z;

end

\# Define Softmax function

function \[A,cache\] = softmax(Z)

\# get unnormalized probabilities

exp\_scores = exp(Z');

\# normalize them for each example

A = exp\_scores ./ sum(exp\_scores,2);

cache=Z;

end

\# Define Relu Derivative

function \[dZ\] = reluDerivative(dA,cache)

Z = cache;

dZ = dA;

\# Get elements that are greater than 0

a = (Z > 0);

\# Select only those elements where Z > 0

dZ = dZ .\* a;

end

\# Define Softmax Derivative

function \[dZ\] = softmaxDerivative(dA,cache,Y)

Z = cache;

\# get unnormalized probabilities

exp\_scores = exp(Z');

\# normalize them for each example

probs = exp\_scores ./ sum(exp\_scores,2);

\# dZ = pi- yi

a=sum(Y==0);

b=sum(Y==1);

c=sum(Y==2);

m= repmat(\[1 0 0\],a,1);

n= repmat(\[0 1 0\],b,1);

o= repmat(\[0 0 1\],c,1);

yi=\[m;n;o\];

dZ=probs-yi;

end

\# Initialize the model

\# Input : number of features

\# number of hidden units

\# number of units in output

\# Returns: Weight and bias matrices and vectors

function \[W1 b1 W2 b2\] = initializeModel(numFeats,numHidden,numOutput) rand ("seed", 3);

W1=rand(numHidden,numFeats)\*0.01; # Multiply by .01

b1=zeros(numHidden,1);

W2=rand(numOutput,numHidden)\*0.01;

b2=zeros(numOutput,1);

end

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prev - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : A, forward\_cache, activation\_cache

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

function \[A forward\_cache activation\_cache\] = layerActivationForward(A\_prev, W, b, activationFunc)

\# Compute Z

Z = W \* A\_prev +b;

\# Create a cell array

forward\_cache = {A\_prev W b};

\# Compute the activation for sigmoid

if (strcmp(activationFunc,"sigmoid"))

\[A activation\_cache\] = sigmoid(Z);

elseif (strcmp(activationFunc, "relu")) # Compute the activation for Relu

\[A activation\_cache\] = relu(Z);

elseif(strcmp(activationFunc,'tanh')) # Compute the activation for tanh

\[A activation\_cache\] = tanhAct(Z);

elseif(strcmp(activationFunc,'softmax')) # Compute the activation for softmax

\[A activation\_cache\] = softmax(Z);

endif

end

\# Compute the backpropoagation for 1 cycle

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# # Input features

\# # Output values Y

\# Returns: dA\_prev, dW, db

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

function \[dA\_prev dW db\] = layerActivationBackward(dA, forward\_cache,

activation\_cache, Y, activationFunc)

if (strcmp(activationFunc,"relu"))

dZ = reluDerivative(dA, activation\_cache);

elseif (strcmp(activationFunc,"sigmoid"))

dZ = sigmoidDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "tanh"))

dZ = tanhDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "softmax"))

dZ = softmaxDerivative(dA, activation\_cache,Y);

endif

A\_prev = forward\_cache{1};

numTraining = size(A\_prev)(2);

\# If activation is softmax

if(strcmp(activationFunc, "softmax"))

W =forward\_cache{2};

b = forward\_cache{3};

dW = 1/numTraining \* A\_prev \* dZ;

db = 1/numTraining \* sum(dZ,1);

dA\_prev = dZ\*W;

else

W =forward\_cache{2};

b = forward\_cache{3};

dW = 1/numTraining \* dZ \* A\_prev';

db = 1/numTraining \* sum(dZ,2);

dA\_prev = W'\*dZ;

endif

end

\# Plot cost vs iterations

function plotCostVsIterations(iterations,costs)

plot(iterations,costs);

title ("Cost vs no of iterations for different learning rates"); xlabel("No of iterations");

ylabel("Cost");

print -dpng "figo2.png"

end;

\# Plot softmax decision boundary

function plotDecisionBoundary( X,Y,W1,b1,W2,b2)

% Make classification predictions over a grid of values

x1plot = linspace(min(X(:,1)), max(X(:,1)), 400)';

x2plot = linspace(min(X(:,2)), max(X(:,2)), 400)';

\[X1, X2\] = meshgrid(x1plot, x2plot);

vals = zeros(size(X1));

for i = 1:size(X1, 2)

gridPoints = \[X1(:, i), X2(:, i)\];

\[A1,cache1 activation\_cache1\]=

layerActivationForward(gridPoints',W1,b1,activationFunc ='relu');

\[A2,cache2 activation\_cache2\] =

layerActivationForward(A1,W2,b2,activationFunc='softmax');

\[l m\] = max(A2, \[ \], 2);

vals(:, i)= m;

endfor

scatter(X(:,1),X(:,2),8,c=Y,"filled");

% Plot the boundary

hold on

contour(X1, X2, vals,"linewidth",4);

print -dpng "fig-o1.png"

end

**6.**

**Appendix 5 - MNIST**

**classification with Softmax**

**5.1 Python**

\# -\*- coding: utf-8 -\*-

"""

############################################################################################################

#

\# File: DLfunctions41.py

\# Developer: Tinniam V Ganesh

\# Date : 23 Mar 2018

#

##########################################################################################################

@author: Ganesh

"""

import numpy as np

import matplotlib.pyplot as plt

import matplotlib

import matplotlib.pyplot as plt

from matplotlib import cm

import math

\# Conmpute the sigmoid of a vector

def sigmoid(Z):

A=1/(1+np.exp(-Z))

cache=Z

return A,cache

\# Conmpute the Relu of a vector

def relu(Z):

A = np.maximum(0,Z)

cache=Z

return A,cache

\# Conmpute the tanh of a vector

def tanh(Z):

A = np.tanh(Z)

cache=Z

return A,cache

\# Conmpute the softmax of a vector

def softmax(Z):

\# get unnormalized probabilities

exp\_scores = np.exp(Z.T)

\# normalize them for each example

A = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

cache=Z

return A,cache

\# Conmpute the Stable Softmax of a vector

def stableSoftmax(Z):

#Compute the softmax of vector x in a numerically stable way.

shiftZ = Z.T - np.max(Z.T,axis=1).reshape(-1,1)

exp\_scores = np.exp(shiftZ)

\# normalize them for each example

A = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

cache=Z

return A,cache

\# Compute the derivative of Relu

def reluDerivative(dA, cache):

Z = cache

dZ = np.array(dA, copy=True) # just converting dz to a correct object.

\# When z <= 0, you should set dz to 0 as well.

dZ\[Z <= 0\] = 0

return dZ

\# Compute the derivative of Sigmoid

def sigmoidDerivative(dA, cache):

Z = cache

s = 1/(1+np.exp(-Z))

 dZ = dA \* s \* (1-s)

return dZ

\# Compute the derivative of tanh

def tanhDerivative(dA, cache):

Z = cache

a = np.tanh(Z)

dZ = dA \* (1 - np.power(a, 2))

return dZ

\# Compute the derivative of Softmax

def softmaxDerivative(dA, cache,y,numTraining):

\# Note : dA not used. dL/dZ = dL/dA \* dA/dZ = pi-yi

Z = cache

\# Compute softmax

exp\_scores = np.exp(Z.T)

\# normalize them for each example

probs = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

\# compute the gradient on scores

dZ = probs

\# dZ = pi- yi

dZ\[range(int(numTraining)),y\[:,0\]\] -= 1

return(dZ)

\# Compute the derivative of Stable Softmax

def stableSoftmaxDerivative(dA, cache,y,numTraining):

\# Note : dA not used. dL/dZ = dL/dA \* dA/dZ = pi-yi

Z = cache

\# Compute stable softmax

shiftZ = Z.T - np.max(Z.T,axis=1).reshape(-1,1)

exp\_scores = np.exp(shiftZ)

\# normalize them for each example

probs = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

#print(probs)

\# compute the gradient on scores

dZ = probs

 # dZ = pi- yi

dZ\[range(int(numTraining)),y\[:,0\]\] -= 1

return(dZ)

\# Initialize the model

\# Input : number of features

\# number of hidden units

\# number of units in output

\# Returns: nnParameters dict

def initializeModel(numFeats,numHidden,numOutput):

np.random.seed(1)

W1=np.random.randn(numHidden,numFeats)\*0.01 # Multiply by .01

b1=np.zeros((numHidden,1))

W2=np.random.randn(numOutput,numHidden)\*0.01

b2=np.zeros((numOutput,1))

\# Create a dictionary of the neural network parameters

nnParameters={'W1':W1,'b1':b1,'W2':W2,'b2':b2}

return(nnParameters)

\# Initialize model for L layers

\# Input : List of units in each layer

\# Returns: Z, cache

def initializeDeepModel(layerDimensions):

np.random.seed(3)

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

layerParams = {}

for l in range(1,len(layerDimensions)):

layerParams\['W' + str(l)\] =

np.random.randn(layerDimensions\[l\],layerDimensions\[l-1\])\*0.01 # Multiply by

.01

layerParams\['b' + str(l)\] = np.zeros((layerDimensions\[l\],1))

return(layerParams)

return Z, cache

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prev - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : A, cache

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

def layerActivationForward(A\_prev, W, b, activationFunc):

\# Compute Z

Z = np.dot(W,A\_prev) + b

forward\_cache = (A\_prev, W, b)

\# Compute the activation for sigmoid

if activationFunc == "sigmoid":

A, activation\_cache = sigmoid(Z)

\# Compute the activation for Relu

elif activationFunc == "relu":

A, activation\_cache = relu(Z)

\# Compute the activation for tanh

elif activationFunc == 'tanh':

A, activation\_cache = tanh(Z)

elif activationFunc == 'softmax':

A, activation\_cache = stableSoftmax(Z)

cache = (forward\_cache, activation\_cache)

return A, cache

\# Compute the forward propagation for layers 1..L

\# Input : X - Input Features

\# paramaters: Weights and biases

\# hiddenActivationFunc - Activation function at hidden layers Relu/tanh

\# outputActivationFunc - Activation function at output - sigmoid/softmax

\# Returns : AL

\# caches

\# The forward propoagtion uses the Relu/tanh activation from layer 1..L-1 and sigmoid actiovation at layer L

def forwardPropagationDeep(X,

parameters,hiddenActivationFunc='relu',outputActivationFunc='sigmoid'): caches = \[\]

\# Set A to X (A0)

A = X

L = int(len(parameters)/2) # number of layers in the neural network

\# Loop through from layer 1 to upto layer L

for l in range(1, L):

A\_prev = A

\# Zi = Wi x Ai-1 + bi and Ai = g(Zi)

#A, cache = layerActivationForward(A\_prev, parameters\['W'+str(l)\], parameters\['b'+str(l)\], activationFunc = "relu")

A, cache = layerActivationForward(A\_prev, parameters\['W'+str(l)\], parameters\['b'+str(l)\], activationFunc = hiddenActivationFunc) caches.append(cache)

#print("l=",l)

#print(A)

\# Since this is binary classification use the sigmoid activation function in

\# last layer

AL, cache = layerActivationForward(A, parameters\['W'+str(L)\], parameters\['b'+str(L)\], activationFunc = outputActivationFunc) caches.append(cache)

return AL, caches

\# Compute the cost

\# Input : AL-Activation of last layer

\# : Y

\# :outputActivationFunc - Activation function at output - sigmoid/softmax

\# Output: cost

def computeCost(AL,Y,outputActivationFunc="sigmoid"): if outputActivationFunc=="sigmoid":

m= float(Y.shape\[1\])

\# Element wise multiply for logprobs

cost=-1/m \*np.sum(Y\*np.log(AL) + (1-Y)\*(np.log(1-AL)))

cost = np.squeeze(cost)

 elif outputActivationFunc=="softmax":

\# Note:Take transpose of Y for softmax

Y=Y.T

m= float(len(Y))

\# Compute log probs. Take the log prob of correct class based on output y correct\_logprobs = -np.log(AL\[range(int(m)),Y.T\])

\# Conpute loss

cost = np.sum(correct\_logprobs)/m

return cost

\# Compute the backpropoagation for 1 cycle

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# # Y

\# # activationFunc # relu, tanh, sigmoid,softmax

\# Returns: dA\_prev, dW, db

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

def layerActivationBackward(dA, cache, Y, activationFunc):

forward\_cache, activation\_cache = cache

A\_prev, W, b = forward\_cache

numtraining = float(A\_prev.shape\[1\])

#print("n=",numtraining)

#print("no=",numtraining)

if activationFunc == "relu":

dZ = reluDerivative(dA, activation\_cache)

elif activationFunc == "sigmoid":

dZ = sigmoidDerivative(dA, activation\_cache)

elif activationFunc == "tanh":

dZ = tanhDerivative(dA, activation\_cache)

elif activationFunc == "softmax":

dZ = stableSoftmaxDerivative(dA, activation\_cache,Y,numtraining) if activationFunc == 'softmax':

dW = 1/numtraining \* np.dot(A\_prev,dZ)

db = 1/numtraining \* np.sum(dZ, axis=0, keepdims=True)

dA\_prev = np.dot(dZ,W)

else:

 #print(numtraining)

dW = 1/numtraining \*(np.dot(dZ,A\_prev.T))

#print("dW=",dW)

db = 1/numtraining \* np.sum(dZ, axis=1, keepdims=True)

#print("db=",db)

dA\_prev = np.dot(W.T,dZ)

return dA\_prev, dW, db

\# Compute the backpropoagation for 1 cycle

\# Input : AL: Output of L layer Network - weights

\# # Y Real output

\# # caches -- list of caches containing:

\# every cache of layerActivationForward() with "relu"/"tanh"

\# #(it's caches\[l\], for l in range(L-1) i.e l = 0...L-2)

\# #the cache of layerActivationForward() with "sigmoid" (it's caches\[L-1\])

\# hiddenActivationFunc - Activation function at hidden layers -

relu/sigmoid/tanh

\# outputActivationFunc - Activation function at output - sigmoid/softmax

#

\# Returns:

\# gradients -- A dictionary with the gradients

\# gradients\["dA" + str(l)\] = ...

\# gradients\["dW" + str(l)\] = ...

\# gradients\["db" + str(l)\]

def backwardPropagationDeep(AL, Y,

caches,hiddenActivationFunc='relu',outputActivationFunc="sigmoid"):

#initialize the gradients

gradients = {}

\# Set the number of layers

L = len(caches)

m = float(AL.shape\[1\])

if outputActivationFunc == "sigmoid":

Y = Y.reshape(AL.shape) # after this line, Y is the same shape as AL

\# Initializing the backpropagation

\# dl/dAL= -(y/a + (1-y)/(1-a)) - At the output layer

dAL = - (np.divide(Y, AL) - np.divide(1 - Y, 1 - AL))

 else:

dAL =0

Y=Y.T

\# Since this is a binary classification the activation at output is sigmoid

\# Get the gradients at the last layer

\# Inputs: "AL, Y, caches".

\# Outputs: "gradients\["dAL"\], gradients\["dWL"\], gradients\["dbL"\]

current\_cache = caches\[L-1\]

gradients\["dA" + str(L)\], gradients\["dW" + str(L)\], gradients\["db" + str(L)\] =

layerActivationBackward(dAL, current\_cache, Y, activationFunc =

outputActivationFunc)

\# Note dA for softmax is the transpose

if outputActivationFunc == "softmax":

gradients\["dA" + str(L)\] = gradients\["dA" + str(L)\].T

\# Traverse in the reverse direction

for l in reversed(range(L-1)):

\# Compute the gradients for L-1 to 1 for Relu/tanh

\# Inputs: "gradients\["dA" + str(l + 2)\], caches".

\# Outputs: "gradients\["dA" + str(l + 1)\] , gradients\["dW" + str(l + 1)\] , gradients\["db" + str(l + 1)\]

current\_cache = caches\[l\]

#dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackward(gradients\['dA'+str(l+2)\], current\_cache, activationFunc = "relu")

dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackward(gradients\['dA'+str(l+2)\], current\_cache, Y, activationFunc = hiddenActivationFunc)

gradients\["dA" + str(l + 1)\] = dA\_prev\_temp

gradients\["dW" + str(l + 1)\] = dW\_temp

gradients\["db" + str(l + 1)\] = db\_temp

return gradients

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients

\# : learning rate

\# : outputActivationFunc - Activation function at output - sigmoid/softmax

#return : parameters

def gradientDescent(parameters, gradients,

learningRate,outputActivationFunc="sigmoid"):

L = int(len(parameters) / 2)

\# Update rule for each parameter.

for l in range(L-1):

parameters\["W" + str(l+1)\] = parameters\['W'+str(l+1)\] -learningRate\*

gradients\['dW' + str(l+1)\]

parameters\["b" + str(l+1)\] = parameters\['b'+str(l+1)\] -learningRate\*

gradients\['db' + str(l+1)\]

if outputActivationFunc=="sigmoid":

parameters\["W" + str(L)\] = parameters\['W'+str(L)\] -learningRate\*

gradients\['dW' + str(L)\]

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] -learningRate\*

gradients\['db' + str(L)\]

elif outputActivationFunc=="softmax":

parameters\["W" + str(L)\] = parameters\['W'+str(L)\] -learningRate\*

gradients\['dW' + str(L)\].T

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] -learningRate\*

gradients\['db' + str(L)\].T

return parameters

\# Execute a L layer Deep learning model

\# Input : X1 - Input features

\# : Y1 output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu

/tanh/sigmoid

\# : outputActivationFunc - sigmoid/softmax

\# : learning rate

\# : num of iteration

\# output : parameters

def L\_Layer\_DeepModel(X1, Y1, layersDimensions,

hiddenActivationFunc='relu', outputActivationFunc="sigmoid", learningRate =

.3, num\_iterations = 10000, print\_cost=False):#lr was 0.009

np.random.seed(1)

costs = \[\]

\# Parameters initialization.

parameters = initializeDeepModel(layersDimensions)

\# Loop (gradient descent)

for i in range(0, num\_iterations):

\# Forward propagation: \[LINEAR -> RELU\]\*(L-1) -> LINEAR -> SIGMOID.

#AL, caches = forwardPropagationDeep(X,

parameters,hiddenActivationFunc)

\# Compute cost.

#cost = computeCost(AL, Y)

\# Backward propagation.

#gradients = backwardPropagationDeep(AL, Y,

caches,hiddenActivationFunc)

\## Update parameters.

#parameters = gradientDescent(parameters, gradients, learning\_rate) AL, caches = forwardPropagationDeep(X1,

parameters,hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc)

\# Compute cost

cost = computeCost(AL, Y1,outputActivationFunc=outputActivationFunc)

#print("Y1=",Y1.shape)

\# Backward propagation.

gradients = backwardPropagationDeep(AL, Y1,

caches,hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc)

 # Update parameters.

parameters = gradientDescent(parameters, gradients,

learningRate=learningRate,outputActivationFunc=outputActivationFunc)

\# Print the cost every 100 training example

if print\_cost and i % 1000 == 0:

print ("Cost after iteration %i: %f" %(i, cost))

if print\_cost and i % 1000 == 0:

costs.append(cost)

\# plot the cost

plt.plot(np.squeeze(costs))

plt.ylabel('cost')

plt.xlabel('No of iterations (x100)')

plt.title("Learning rate =" + str(learningRate))

#plt.show()

plt.savefig("fig1",bbox\_inches='tight')

return parameters

\# Execute a L layer Deep learning model Stoachastic Gradient Descent

\# Input : X1 - Input features

\# : Y1- output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu

/tanh/sigmoid

\# : outputActivationFunc - Activation function at output - sigmoid/softmax

\# : learning rate

\# : mini\_batch\_size

\# : num\_epochs

#output : parameters

def L\_Layer\_DeepModel\_SGD(X1, Y1, layersDimensions,

hiddenActivationFunc='relu', outputActivationFunc="sigmoid",learningRate =

.3, mini\_batch\_size = 64, num\_epochs = 2500, print\_cost=False):#lr was 0.009

np.random.seed(1)

costs = \[\]

 # Parameters initialization.

parameters = initializeDeepModel(layersDimensions)

seed=10

\# Loop for number of epochs

for i in range(num\_epochs):

\# Define the random minibatches. We increment the seed to reshuffle differently the dataset after each epoch

seed = seed + 1

minibatches = random\_mini\_batches(X1, Y1, mini\_batch\_size, seed) batch=0

\# Loop through each mini batch

for minibatch in minibatches:

#print("batch=",batch)

batch=batch+1

\# Select a minibatch

(minibatch\_X, minibatch\_Y) = minibatch

\# Perfrom forward propagation

AL, caches = forwardPropagationDeep(minibatch\_X,

parameters,hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc)

\# Compute cost

cost = computeCost(AL,

minibatch\_Y,outputActivationFunc=outputActivationFunc)

#print("minibatch\_Y=",minibatch\_Y.shape)

\# Backward propagation.

gradients = backwardPropagationDeep(AL, minibatch\_Y,

caches,hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc)

\# Update parameters.

parameters = gradientDescent(parameters, gradients,

learningRate=learningRate,outputActivationFunc=outputActivationFunc)

\# Print the cost every 1000 epoch

if print\_cost and i % 100 == 0:

print ("Cost after epoch %i: %f" %(i, cost))

if print\_cost and i % 100 == 0:

costs.append(cost)

\# plot the cost

plt.plot(np.squeeze(costs))

plt.ylabel('cost')

plt.xlabel('No of iterations')

plt.title("Learning rate =" + str(learningRate))

#plt.show()

plt.savefig("fig1",bbox\_inches='tight')

return parameters

\# Create random mini batches

\# Input : X - Input features

\# : Y- output

\# : miniBatchSizes

\# : seed

#output : mini\_batches

def random\_mini\_batches(X, Y, miniBatchSize = 64, seed = 0):

np.random.seed(seed)

\# Get number of training samples

m = X.shape\[1\]

\# Initialize mini batches

mini\_batches = \[\]

\# Create a list of random numbers < m

permutation = list(np.random.permutation(m))

\# Randomly shuffle the training data

shuffled\_X = X\[:, permutation\]

shuffled\_Y = Y\[:, permutation\].reshape((1,m))

\# Compute number of mini batches

numCompleteMinibatches = math.floor(m/miniBatchSize)

\# For the number of mini batches

for k in range(0, numCompleteMinibatches):

\# Set the start and end of each mini batch

 mini\_batch\_X = shuffled\_X\[:, k\*miniBatchSize : (k+1) \* miniBatchSize\]

mini\_batch\_Y = shuffled\_Y\[:, k\*miniBatchSize : (k+1) \* miniBatchSize\]

mini\_batch = (mini\_batch\_X, mini\_batch\_Y)

mini\_batches.append(mini\_batch)

#if m % miniBatchSize != 0:. The batch does not evenly divide by the mini batch

if m % miniBatchSize != 0:

l=math.floor(m/miniBatchSize)\*miniBatchSize

\# Set the start and end of last mini batch

m=l+m % miniBatchSize

mini\_batch\_X = shuffled\_X\[:,l:m\]

mini\_batch\_Y = shuffled\_Y\[:,l:m\]

mini\_batch = (mini\_batch\_X, mini\_batch\_Y)

mini\_batches.append(mini\_batch)

return mini\_batches

\# Plot a decision boundary

\# Input : Input Model,

\# X

\# Y

\# lr - Learning rate

\# Fig to be saved as

\# Returns Null

def plot\_decision\_boundary(model, X, y,lr,fig):

\# Set min and max values and give it some padding

x\_min, x\_max = X\[0, :\].min() - 1, X\[0, :\].max() + 1

y\_min, y\_max = X\[1, :\].min() - 1, X\[1, :\].max() + 1

colors=\['black','yellow'\]

cmap = matplotlib.colors.ListedColormap(colors)

h = 0.01

\# Generate a grid of points with distance h between them

xx, yy = np.meshgrid(np.arange(x\_min, x\_max, h), np.arange(y\_min, y\_max, h))

\# Predict the function value for the whole grid

 Z = model(np.c\_\[xx.ravel(), yy.ravel()\]) Z = Z.reshape(xx.shape)

\# Plot the contour and training examples

plt.contourf(xx, yy, Z, cmap="coolwarm")

plt.ylabel('x2')

plt.xlabel('x1')

plt.scatter(X\[0, :\], X\[1, :\], c=y, s=7,cmap=cmap)

plt.title("Decision Boundary for learning rate:"+lr)

#plt.show()

plt.savefig(fig, bbox\_inches='tight')

def predict(parameters, X):

A2, cache = forwardPropagationDeep(X, parameters)

predictions = (A2>0.5)

return predictions

def predict\_proba(parameters, X,outputActivationFunc="sigmoid"): A2, cache = forwardPropagationDeep(X, parameters)

if outputActivationFunc=="sigmoid":

proba=A2

elif outputActivationFunc=="softmax":

proba=np.argmax(A2, axis=0).reshape(-1,1)

print("A2=",A2.shape)

return proba

\# Plot a decision boundary

\# Input : Input Model,

\# X

\# Y

\# sz - Num of hiden units

\# lr - Learning rate

\# Fig to be saved as

\# Returns Null

def plot\_decision\_surface(model, X, y,sz,lr,fig):

\# Set min and max values and give it some padding

x\_min, x\_max = X\[0, :\].min() - 1, X\[0, :\].max() + 1

y\_min, y\_max = X\[1, :\].min() - 1, X\[1, :\].max() + 1

z\_min, z\_max = X\[2, :\].min() - 1, X\[2, :\].max() + 1

 colors=\['black','gold'\]

cmap = matplotlib.colors.ListedColormap(colors)

h = 3

\# Generate a grid of points with distance h between them

xx, yy, zz = np.meshgrid(np.arange(x\_min, x\_max, h), np.arange(y\_min, y\_max, h), np.arange(z\_min, z\_max, h))

\# Predict the function value for the whole grid

a=np.c\_\[xx.ravel(), yy.ravel(), zz.ravel()\]

Z = predict(parameters,a.T)

Z = Z.reshape(xx.shape)

\# Plot the contour and training examples

#plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral)

fig = plt.figure()

ax = plt.axes(projection='3d')

ax.contour3D(xx, yy, Z, 50, cmap='binary')

#plt.ylabel('x2')

#plt.xlabel('x1')

plt.scatter(X\[0, :\], X\[1, :\], c=y, cmap=cmap)

plt.title("Decision Boundary for hidden layer size:" + sz +" and learning rate:"+lr)

plt.show()

def plotSurface(X,parameters):

#xx, yy, zz = np.meshgrid(np.arange(10), np.arange(10), np.arange(10)) x\_min, x\_max = X\[0, :\].min() - 1, X\[0, :\].max() + 1

y\_min, y\_max = X\[1, :\].min() - 1, X\[1, :\].max() + 1

z\_min, z\_max = X\[2, :\].min() - 1, X\[2, :\].max() + 1

colors=\['red'\]

cmap = matplotlib.colors.ListedColormap(colors)

h = 1

xx, yy, zz = np.meshgrid(np.arange(x\_min, x\_max, h), np.arange(y\_min, y\_max, h),

np.arange(z\_min, z\_max, h))

\# For the meh grid values predict a model

a=np.c\_\[xx.ravel(), yy.ravel(), zz.ravel()\]

Z = predict(parameters,a.T)

r=Z.T

 r1=r.reshape(xx.shape)

\# Find teh values for which the repdiction is 1

xx1=xx\[r1\]

yy1=yy\[r1\]

zz1=zz\[r1\]

\# Plot these values

ax = plt.axes(projection='3d')

#ax.plot\_trisurf(xx1, yy1, zz1, cmap='bone', edgecolor='none'); ax.scatter3D(xx1, yy1,zz1, c=zz1,s=10,cmap=cmap)

#ax.plot\_surface(xx1, yy1, zz1, 'gray')

 

**5.2 R**

############################################################################################################

#

\# File : DLfunctions5.R

\# Author : Tinniam V Ganesh

\# Date : 22 Mar 2018

#

##########################################################################################################

library(ggplot2)

library(PRROC)

library(dplyr)

\# Compute the sigmoid of a vector

sigmoid <- function(Z){

A <- 1/(1+ exp(-Z))

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the Relu(old) of a vector (performance hog!)

reluOld <-function(Z){

A <- apply(Z, 1:2, function(x) max(0,x))

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the Relu (current) of a vector (much better performance!) relu <-function(Z){

\# Perform relu. Set values less that equal to 0 as 0

Z\[Z<0\]=0

 A=Z

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the tanh activation of a vector

tanhActivation <- function(Z){

A <- tanh(Z)

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Conmpute the softmax of a vector

softmax <- function(Z){

\# get unnormalized probabilities

exp\_scores = exp(t(Z))

\# normalize them for each example

A = exp\_scores / rowSums(exp\_scores)

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the detivative of Relu

\# g'(z) = 1 if z >0 and 0 otherwise

reluDerivative <-function(dA, cache){

Z <- cache

dZ <- dA

\# Create a logical matrix of values > 0

a <- Z > 0

\# When z <= 0, you should set dz to 0 as well. Perform an element wise multiple

dZ <- dZ \* a

return(dZ)

}

\# Compute the derivative of sigmoid

\# Derivative g'(z) = a\* (1-a)

sigmoidDerivative <- function(dA, cache){

Z <- cache

s <- 1/(1+exp(-Z))

dZ <- dA \* s \* (1-s)

return(dZ)

}

\# Compute the derivative of tanh

\# Derivative g'(z) = 1- a^2

tanhDerivative <- function(dA, cache){

Z = cache

a = tanh(Z)

dZ = dA \* (1 - a^2)

return(dZ)

}

\# This function is used in computing the softmax derivative

\# Populate a matrix of 1s in rows where Y==1

\# This may need to be extended for K classes. Currently

\# supports K=3 & K=10

popMatrix <- function(Y,numClasses){

a=rep(0,times=length(Y))

Y1=matrix(a,nrow=length(Y),ncol=numClasses)

#Set the rows and columns as 1's where Y is the class value

if(numClasses==3){

Y1\[Y==0,1\]=1

Y1\[Y==1,2\]=1

Y1\[Y==2,3\]=1

} else if (numClasses==10){

Y1\[Y==0,1\]=1

Y1\[Y==1,2\]=1

Y1\[Y==2,3\]=1

Y1\[Y==3,4\]=1

Y1\[Y==4,5\]=1

Y1\[Y==5,6\]=1

Y1\[Y==6,7\]=1

Y1\[Y==7,8\]=1

Y1\[Y==8,9\]=1

Y1\[Y==9,0\]=1

 }

return(Y1)

}

\# Compute the softmax derivative

softmaxDerivative <- function(dA, cache ,y,numTraining,numClasses){

\# Note : dA not used. dL/dZ = dL/dA \* dA/dZ = pi-yi

Z <- cache

\# Compute softmax

exp\_scores = exp(t(Z))

\# normalize them for each example

probs = exp\_scores / rowSums(exp\_scores)

\# Create a matrix of zeros

Y1=popMatrix(y,numClasses)

dZ = probs-Y1

return(dZ)

}

\# Initialize model for L layers

\# Input : Vector of units in each layer

\# Returns: Initial weights and biases matrices for all layers initializeDeepModel <- function(layerDimensions){

set.seed(2)

\# Initialize empty list

layerParams <- list()

\# Note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Indices in R start from 1

for(l in 2:length(layersDimensions)){

\# Initialize a matrix of small random numbers of size l x l-1

\# Create random numbers of size l x l-1

w=rnorm(layersDimensions\[l\]\*layersDimensions\[l-1\])\*0.01

\# Create a weight matrix of size l x l-1 with this initial weights and

 # Add to list W1,W2... WL

layerParams\[\[paste('W',l-1,sep="")\]\] = matrix(w,nrow=layersDimensions\[l\], ncol=layersDimensions\[l-1\])

layerParams\[\[paste('b',l-1,sep="")\]\] = matrix(rep(0,layersDimensions\[l\]), nrow=layersDimensions\[l\],ncol=1)

}

return(layerParams)

}

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prev - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : forward\_cache,activation\_cache,cache

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

layerActivationForward <- function(A\_prev, W, b, activationFunc){

\# Compute Z

z = W %\*% A\_prev

\# Broadcast the bias 'b' by column

Z <-sweep(z,1,b,'+')

forward\_cache <- list("A\_prev"=A\_prev, "W"=W, "b"=b)

\# Compute the activation for sigmoid

if(activationFunc == "sigmoid"){

vals = sigmoid(Z)

} else if (activationFunc == "relu"){ # Compute the activation for relu vals = relu(Z)

} else if(activationFunc == 'tanh'){ # Compute the activation for tanh vals = tanhActivation(Z)

} else if(activationFunc == 'softmax'){

vals = softmax(Z)

}

\# Create a list of forward and activation cache

cache <- list("forward\_cache"=forward\_cache, "activation\_cache"=vals\[\['Z'\]\]) retvals <- list("A"=vals\[\['A'\]\],"cache"=cache)

 return(retvals)

}

\# Compute the forward propagation for layers 1..L

\# Input : X - Input Features

\# parameters: Weights and biases

\# hiddenActivationFunc - relu/sigmoid/tanh

\# outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# Returns : AL

\# caches

\# The forward propagtion uses the Relu/tanh activation from layer 1..L-1 and sigmoid actiovation at layer L

forwardPropagationDeep <- function(X,

parameters,hiddenActivationFunc='relu',

outputActivationFunc='sigmoid'){

caches <- list()

\# Set A to X (A0)

A <- X

L <- length(parameters)/2 # number of layers in the neural network

\# Loop through from layer 1 to upto layer L

for(l in 1:(L-1)){

A\_prev <- A

\# Zi = Wi x Ai-1 + bi and Ai = g(Zi)

\# Set W and b for layer 'l'

\# Loop throug from W1,W2... WL-1

W <- parameters\[\[paste("W",l,sep="")\]\]

b <- parameters\[\[paste("b",l,sep="")\]\]

\# Compute the forward propagation through layer 'l' using the activation function

actForward <- layerActivationForward(A\_prev,

W,

b,

activationFunc = hiddenActivationFunc)

A <- actForward\[\['A'\]\]

\# Append the cache A\_prev,W,b, Z

caches\[\[l\]\] <-actForward

}

 # Since this is binary classification use the sigmoid activation function in

\# last layer

\# Set the weights and biases for the last layer

W <- parameters\[\[paste("W",L,sep="")\]\]

b <- parameters\[\[paste("b",L,sep="")\]\]

\# Compute the sigmoid activation

actForward = layerActivationForward(A, W, b, activationFunc =

outputActivationFunc)

AL <- actForward\[\['A'\]\]

\# Append the output of this forward propagation through the last layer caches\[\[L\]\] <- actForward

\# Create a list of the final output and the caches

fwdPropDeep <- list("AL"=AL,"caches"=caches) return(fwdPropDeep)

}

\# Function pickColumns(). This function is in computeCost()

\# Pick columns

\# Input : AL

\# : Y

\# : numClasses

\# Output: a

pickColumns <- function(AL,Y,numClasses){

if(numClasses==3){

\# Select the elements where the y values are 0, 1 or 2 and make a vector a=c(AL\[Y==0,1\],AL\[Y==1,2\],AL\[Y==2,3\])

}

else if (numClasses==10){

\# Select the elements where the y values are 0,1,2..,9

a=c(AL\[Y==0,1\],AL\[Y==1,2\],AL\[Y==2,3\],AL\[Y==3,4\],AL\[Y==4,5\],

AL\[Y==5,6\],AL\[Y==6,7\],AL\[Y==7,8\],AL\[Y==8,9\],AL\[Y==9,10\])

}

return(a)

}

\# Compute the cost

\# Input : AL

\# : Y

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : numClasses

\# Output: cost

computeCost <-

function(AL,Y,outputActivationFunc="sigmoid",numClasses=3){

if(outputActivationFunc=="sigmoid"){

m= length(Y)

cost=-1/m\*sum(Y\*log(AL) + (1-Y)\*log(1-AL))

}else if (outputActivationFunc=="softmax"){

\# Pick columns

m= length(Y)

a =pickColumns(AL,Y,numClasses)

\# Take log

correct\_probs = -log(a)

\# Compute loss

cost= sum(correct\_probs)/m

}

#cost=-1/m\*sum(a+b)

return(cost)

}

\# Compute the backpropagation through a layer

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# # Output values Y

\# # activationFunc

\# # numClasses

\# Returns: Gradients - dA\_prev, dW,db

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

layerActivationBackward <- function(dA, cache, Y, activationFunc,numClasses)

{

\# Get A\_prev,W,b

forward\_cache <-cache\[\['forward\_cache'\]\]

 activation\_cache <- cache\[\['activation\_cache'\]\]

A\_prev <- forward\_cache\[\['A\_prev'\]\]

numtraining = dim(A\_prev)\[2\]

\# Get Z

activation\_cache <- cache\[\['activation\_cache'\]\]

if(activationFunc == "relu"){

dZ <- reluDerivative(dA, activation\_cache)

} else if(activationFunc == "sigmoid"){

dZ <- sigmoidDerivative(dA, activation\_cache)

} else if(activationFunc == "tanh"){

dZ <- tanhDerivative(dA, activation\_cache)

} else if(activationFunc == "softmax"){

dZ <- softmaxDerivative(dA, activation\_cache,Y,numtraining,numClasses)

}

\# Check if softmax

if (activationFunc == 'softmax'){

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

dW = 1/numtraining \* A\_prev%\*%dZ

db = 1/numtraining\* matrix(colSums(dZ),nrow=1,ncol=numClasses) dA\_prev = dZ %\*%W

} else {

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

numtraining = dim(A\_prev)\[2\]

dW = 1/numtraining \* dZ %\*% t(A\_prev)

db = 1/numtraining \* rowSums(dZ)

dA\_prev = t(W) %\*% dZ

}

retvals <- list("dA\_prev"=dA\_prev,"dW"=dW,"db"=db) return(retvals)

}

\# Compute the backpropagation for 1 cycle through all layers

\# Input : AL: Output of L layer Network - weights

\# # Y Real output

\# # caches -- list of caches containing:

\# every cache of layerActivationForward() with "relu"/"tanh"

\# #(it's caches\[l\], for l in range(L-1) i.e l = 0...L-2)

\# #the cache of layerActivationForward() with "sigmoid" (it's caches\[L-1\])

\# hiddenActivationFunc - Activation function at hidden layers -

relu/tanh/sigmoid

\# outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# numClasses

\# Returns:

\# gradients -- listwith the gradients

\# gradients\["dA" + str(l)\]

\# gradients\["dW" + str(l)\]

\# gradients\["db" + str(l)\]

backwardPropagationDeep <- function(AL, Y,

caches,hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",numClasses){

#initialize the gradients

gradients = list()

\# Set the number of layers

L = length(caches)

numTraining = dim(AL)\[2\]

if(outputActivationFunc == "sigmoid")

\# Initializing the backpropagation

\# dl/dAL= -(y/a) - ((1-y)/(1-a)) - At the output layer

dAL = -( (Y/AL) -(1 - Y)/(1 - AL))

else if(outputActivationFunc == "softmax"){

dAL=0

Y=t(Y)

}

\# Get the gradients at the last layer

\# Inputs: "AL, Y, caches".

\# Outputs: "gradients\["dAL"\], gradients\["dWL"\], gradients\["dbL"\]

\# Start with Layer L

\# Get the current cache

current\_cache = caches\[\[L\]\]$cache

#gradients\["dA" + str(L)\], gradients\["dW" + str(L)\], gradients\["db" + str(L)\] =

layerActivationBackward(dAL, current\_cache, activationFunc = "sigmoid") retvals <- layerActivationBackward(dAL, current\_cache, Y, activationFunc =

outputActivationFunc,numClasses)

 # Create gradients as lists

#Note: Take the transpose of dA

if(outputActivationFunc =="sigmoid")

gradients\[\[paste("dA",L,sep="")\]\] <- retvals\[\['dA\_prev'\]\]

else if(outputActivationFunc =="softmax")

gradients\[\[paste("dA",L,sep="")\]\] <- t(retvals\[\['dA\_prev'\]\]) gradients\[\[paste("dW",L,sep="")\]\] <- retvals\[\['dW'\]\]

gradients\[\[paste("db",L,sep="")\]\] <- retvals\[\['db'\]\]

\# Traverse in the reverse direction

for(l in (L-1):1){

\# Compute the gradients for L-1 to 1 for Relu/tanh

\# Inputs: "gradients\["dA" + str(l + 2)\], caches".

\# Outputs: "gradients\["dA" + str(l + 1)\] , gradients\["dW" + str(l + 1)\] , gradients\["db" + str(l + 1)\]

current\_cache = caches\[\[l\]\]$cache

retvals = layerActivationBackward(gradients\[\[paste('dA',l+1,sep="")\]\], current\_cache,

activationFunc = hiddenActivationFunc)

gradients\[\[paste("dA",l,sep="")\]\] <-retvals\[\['dA\_prev'\]\]

gradients\[\[paste("dW",l,sep="")\]\] <- retvals\[\['dW'\]\]

gradients\[\[paste("db",l,sep="")\]\] <- retvals\[\['db'\]\]

}

return(gradients)

}

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients

\# : learning rate

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# output : parameters

gradientDescent <- function(parameters, gradients,

learningRate,outputActivationFunc="sigmoid"){

L = length(parameters)/2 # number of layers in the neural network

\# Update rule for each parameter. Use a for loop.

for(l in 1:(L-1)){

parameters\[\[paste("W",l,sep="")\]\] = parameters\[\[paste("W",l,sep="")\]\] -

learningRate\* gradients\[\[paste("dW",l,sep="")\]\]

parameters\[\[paste("b",l,sep="")\]\] = parameters\[\[paste("b",l,sep="")\]\] -

learningRate\* gradients\[\[paste("db",l,sep="")\]\]

}

if(outputActivationFunc=="sigmoid"){

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* gradients\[\[paste("dW",L,sep="")\]\]

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* gradients\[\[paste("db",L,sep="")\]\]

}else if (outputActivationFunc=="softmax"){

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* gradients\[\[paste("dW",L,sep="")\]\]

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* gradients\[\[paste("db",L,sep="")\]\]

}

return(parameters)

}

\# Execute a L layer Deep learning model

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu

/tanh/sigmoid

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : learning rate

\# : num of iterations

#output : Updated weights after each iteration

L\_Layer\_DeepModel <- function(X, Y, layersDimensions,

 hiddenActivationFunc='relu', outputActivationFunc= 'sigmoid',

learningRate = 0.5,

numIterations = 10000,

print\_cost=False){

#Initialize costs vector as NULL

costs <- NULL

\# Parameters initialization.

parameters = initializeDeepModel(layersDimensions)

\# Loop (gradient descent)

for( i in 0:numIterations){

\# Forward propagation: \[LINEAR -> RELU\]\*(L-1) -> LINEAR -> SIGMOID/SOFTMAX.

retvals = forwardPropagationDeep(X, parameters,hiddenActivationFunc, outputActivationFunc=outputActivationFunc)

AL <- retvals\[\['AL'\]\]

caches <- retvals\[\['caches'\]\]

\# Compute cost.

cost <- computeCost(AL,

Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[3\])

\# Backward propagation.

gradients = backwardPropagationDeep(AL, Y, caches,hiddenActivationFunc, outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[3\])

\# Update parameters.

parameters = gradientDescent(parameters, gradients, learningRate, outputActivationFunc=outputActivationFunc)

if(i%%1000 == 0){

costs=c(costs,cost)

print(cost)

}

 }

retvals <- list("parameters"=parameters,"costs"=costs) return(retvals)

}

\# Execute a L layer Deep learning model with Stochastic Gradient descent

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu

/tanh/sigmoid

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : learning rate

\# : mini\_batch\_size

\# : num of epochs

#output : Updated weights after each iteration

L\_Layer\_DeepModel\_SGD <- function(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc= 'sigmoid',

learningRate = .3,

mini\_batch\_size = 64,

num\_epochs = 2500,

print\_cost=False){

set.seed(1)

#Initialize costs vector as NULL

costs <- NULL

\# Parameters initialization.

parameters = initializeDeepModel(layersDimensions)

seed=10

\# Loop for number of epochs

for( i in 0:num\_epochs){

seed=seed+1

minibatches = random\_mini\_batches(X, Y, mini\_batch\_size, seed)

for(batch in 1:length(minibatches)){

mini\_batch\_X=minibatches\[\[batch\]\]\[\['mini\_batch\_X'\]\]

mini\_batch\_Y=minibatches\[\[batch\]\]\[\['mini\_batch\_Y'\]\]

\# Forward propagation:

retvals = forwardPropagationDeep(mini\_batch\_X,

parameters,hiddenActivationFunc,

outputActivationFunc=outputActivationFunc)

AL <- retvals\[\['AL'\]\]

caches <- retvals\[\['caches'\]\]

\# Compute cost.

cost <- computeCost(AL,

mini\_batch\_Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

\# Backward propagation.

gradients = backwardPropagationDeep(AL, mini\_batch\_Y,

caches,hiddenActivationFunc,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

\# Update parameters.

parameters = gradientDescent(parameters, gradients, learningRate, outputActivationFunc=outputActivationFunc)

}

if(i%%100 == 0){

costs=c(costs,cost)

print(cost)

}

}

retvals <- list("parameters"=parameters,"costs"=costs) return(retvals)

}

\# Predict the output for given input

\# Input : parameters

\# : X

\# : hiddenActivationFunc

\# Output: predictions

predict <- function(parameters, X,hiddenActivationFunc='relu'){

fwdProp <- forwardPropagationDeep(X, parameters,hiddenActivationFunc) predictions <- fwdProp$AL>0.5

return (predictions)

}

\# Predict the output

predictProba <- function(parameters, X,hiddenActivationFunc, outputActivationFunc){

retvals = forwardPropagationDeep(X, parameters,hiddenActivationFunc, outputActivationFunc="softmax")

if(outputActivationFunc =="sigmoid")

predictions <- retvals$AL>0.5

else if (outputActivationFunc =="softmax")

predictions <- apply(retvals$AL, 1,which.max) -1

return (predictions)

}

\# Plot a decision boundary

\# This function uses ggplot2

plotDecisionBoundary <- function(z,retvals,hiddenActivationFunc,lr){

\# Find the minimum and maximum for the data

xmin<-min(z\[,1\])

xmax<-max(z\[,1\])

ymin<-min(z\[,2\])

ymax<-max(z\[,2\])

\# Create a grid of values

a=seq(xmin,xmax,length=100)

b=seq(ymin,ymax,length=100)

grid <- expand.grid(x=a, y=b)

colnames(grid) <- c('x1', 'x2')

 grid1 <-t(grid)

\# Predict the output for this grid

q <-predict(retvals$parameters,grid1,hiddenActivationFunc) q1 <- t(data.frame(q))

q2 <- as.numeric(q1)

grid2 <- cbind(grid,q2)

colnames(grid2) <- c('x1', 'x2','q2')

z1 <- data.frame(z)

names(z1) <- c("x1","x2","y") atitle=paste("Decision boundary for learning rate:",lr)

\# Plot the contour of the boundary

ggplot(z1) +

geom\_point(data = z1, aes(x = x1, y = x2, color = y)) +

stat\_contour(data = grid2, aes(x = x1, y = x2, z = q2,color=q2), alpha = 0.9)+

ggtitle(atitle)

}

\# Predict the probability scores for given data set

\# Input : parameters

\# : X

\# Output: probability of output

computeScores <- function(parameters, X,hiddenActivationFunc='relu'){

fwdProp <- forwardPropagationDeep(X, parameters,hiddenActivationFunc) scores <- fwdProp$AL

return (scores)

}

\# Create random mini batches

\# Input : X - Input features

\# : Y- output

\# : miniBatchSize

\# : seed

#output : mini\_batches

random\_mini\_batches <- function(X, Y, miniBatchSize = 64, seed = 0){

 set.seed(seed)

\# Get number of training samples

m = dim(X)\[2\]

\# Initialize mini batches

mini\_batches = list()

\# Create a list of random numbers < m

permutation = c(sample(m))

\# Randomly shuffle the training data

shuffled\_X = X\[, permutation\]

shuffled\_Y = Y\[1, permutation\]

\# Compute number of mini batches

numCompleteMinibatches = floor(m/miniBatchSize)

batch=0

for(k in 0:(numCompleteMinibatches-1)){

batch=batch+1

\# Set the lower and upper bound of the mini batches

lower=(k\*miniBatchSize)+1

upper=((k+1) \* miniBatchSize)

mini\_batch\_X = shuffled\_X\[, lower:upper\]

mini\_batch\_Y = shuffled\_Y\[lower:upper\]

\# Add it to the list of mini batches

mini\_batch =

list("mini\_batch\_X"=mini\_batch\_X,"mini\_batch\_Y"=mini\_batch\_Y) mini\_batches\[\[batch\]\] =mini\_batch

}

\# If the batch size does not divide evenly with mini batc size if(m %% miniBatchSize != 0){

p=floor(m/miniBatchSize)\*miniBatchSize

\# Set the start and end of last batch

q=p+m %% miniBatchSize

mini\_batch\_X = shuffled\_X\[,(p+1):q\]

mini\_batch\_Y = shuffled\_Y\[(p+1):q\]

}

\# Return the list of mini batches

mini\_batch =

list("mini\_batch\_X"=mini\_batch\_X,"mini\_batch\_Y"=mini\_batch\_Y) mini\_batches\[\[batch\]\]=mini\_batch

return(mini\_batches)

}

**5.3 Octave**

############################################################################################################

#

\# File: DLfunctions5.m

\# Developer: Tinniam V Ganesh

\# Date : 23 Mar 2018

#

##########################################################################################################

1;

\# Define sigmoid function

function \[A,cache\] = sigmoid(Z)

A = 1 ./ (1+ exp(-Z));

cache=Z;

end

\# Define Relu function

function \[A,cache\] = relu(Z)

A = max(0,Z);

cache=Z;

end

\# Define Relu function

function \[A,cache\] = tanhAct(Z)

A = tanh(Z);

cache=Z;

end

\# Define Softmax function

function \[A,cache\] = softmax(Z)

\# get unnormalized probabilities

exp\_scores = exp(Z');

\# normalize them for each example

A = exp\_scores ./ sum(exp\_scores,2);

cache=Z;

end

\# Define Stable Softmax function

function \[A,cache\] = stableSoftmax(Z)

\# Normalize by max value in each row

shiftZ = Z' - max(Z',\[\],2);

exp\_scores = exp(shiftZ);

\# normalize them for each example

A = exp\_scores ./ sum(exp\_scores,2);

#disp("sm")

#disp(A);

cache=Z;

end

\# Define Relu Derivative

function \[dZ\] = reluDerivative(dA,cache)

Z = cache;

dZ = dA;

\# Get elements that are greater than 0

a = (Z > 0);

\# Select only those elements where Z > 0

dZ = dZ .\* a;

end

\# Define Sigmoid Derivative

function \[dZ\] = sigmoidDerivative(dA,cache)

Z = cache;

s = 1 ./ (1+ exp(-Z));

dZ = dA .\* s .\* (1-s);

end

\# Define Tanh Derivative

function \[dZ\] = tanhDerivative(dA,cache)

Z = cache;

a = tanh(Z);

dZ = dA .\* (1 - a .^ 2);

end

\# Populate a matrix with 1s in rows where Y=1

\# This function may need to be modified if K is not 3, 10

\# This function is used in computing the softmax derivative

function \[Y1\] = popMatrix(Y,numClasses)

Y1=zeros(length(Y),numClasses);

if(numClasses==3) # For 3 output classes

Y1(Y==0,1)=1;

Y1(Y==1,2)=1;

Y1(Y==2,3)=1;

elseif(numClasses==10) # For 10 output classes

Y1(Y==0,1)=1;

Y1(Y==1,2)=1;

Y1(Y==2,3)=1;

Y1(Y==3,4)=1;

Y1(Y==4,5)=1;

Y1(Y==5,6)=1;

Y1(Y==6,7)=1;

Y1(Y==7,8)=1;

Y1(Y==8,9)=1;

Y1(Y==9,10)=1;

endif

end

\# Define Softmax Derivative

function \[dZ\] = softmaxDerivative(dA,cache,Y, numClasses)

Z = cache;

\# get unnormalized probabilities

shiftZ = Z' - max(Z',\[\],2);

exp\_scores = exp(shiftZ);

\# normalize them for each example

probs = exp\_scores ./ sum(exp\_scores,2);

\# dZ = pi- yi

yi=popMatrix(Y,numClasses);

dZ=probs-yi;

end

\# Define Stable Softmax Derivative

function \[dZ\] = stableSoftmaxDerivative(dA,cache,Y, numClasses) Z = cache;

 # get unnormalized probabilities

exp\_scores = exp(Z');

\# normalize them for each example

probs = exp\_scores ./ sum(exp\_scores,2);

\# dZ = pi- yi

yi=popMatrix(Y,numClasses);

dZ=probs-yi;

end

\# Initialize model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers function \[W b\] = initializeDeepModel(layerDimensions)

rand ("seed", 3);

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Create cell arrays for Weights and biases

for l =2:size(layerDimensions)(2)

W{l-1} = rand(layerDimensions(l),layerDimensions(l-1))\*0.01; #

Multiply by .01

b{l-1} = zeros(layerDimensions(l),1);

endfor

end

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prev - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : A, forward\_cache, activation\_cache

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

function \[A forward\_cache activation\_cache\] = layerActivationForward(A\_prev, W, b, activationFunc)

\# Compute Z

Z = W \* A\_prev +b;

\# Create a cell array

forward\_cache = {A\_prev W b};

\# Compute the activation for sigmoid

if (strcmp(activationFunc,"sigmoid"))

\[A activation\_cache\] = sigmoid(Z);

elseif (strcmp(activationFunc, "relu")) # Compute the activation for Relu

\[A activation\_cache\] = relu(Z);

elseif(strcmp(activationFunc,'tanh')) # Compute the activation for tanh

\[A activation\_cache\] = tanhAct(Z);

elseif(strcmp(activationFunc,'softmax')) # Compute the activation for tanh

#\[A activation\_cache\] = softmax(Z);

\[A activation\_cache\] = stableSoftmax(Z);

endif

end

\# Compute the forward propagation for layers 1..L

\# Input : X - Input Features

\# paramaters: Weights and biases

\# hiddenActivationFunc - Activation function at hidden layers Relu/tanh

\# outputActivationFunc- sigmoid/softmax

\# Returns : AL, forward\_caches, activation\_caches

\# The forward propoagtion uses the Relu/tanh activation from layer 1..L-1 and sigmoid actiovation at layer L

function \[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights,biases,

hiddenActivationFunc='relu',

outputActivationFunc='sigmoid')

\# Create an empty cell array

forward\_caches = {};

activation\_caches = {};

\# Set A to X (A0)

A = X;

L = length(weights); # number of layers in the neural network

\# Loop through from layer 1 to upto layer L

for l =1:L-1

 A\_prev = A;

\# Zi = Wi x Ai-1 + bi and Ai = g(Zi)

W = weights{l};

b = biases{l};

\[A forward\_cache activation\_cache\] = layerActivationForward(A\_prev, W,b, activationFunc=hiddenActivationFunc);

forward\_caches{l}=forward\_cache;

activation\_caches{l} = activation\_cache;

endfor

\# Since this is binary classification use the sigmoid activation function in

\# last layer

W = weights{L};

b = biases{L};

\[AL, forward\_cache activation\_cache\] = layerActivationForward(A, W,b, activationFunc = outputActivationFunc);

forward\_caches{L}=forward\_cache;

activation\_caches{L} = activation\_cache;

end

\# Pick columns where Y==1

\# This function is used in computeCost

function \[a\] = pickColumns(AL,Y,numClasses)

if(numClasses==3)

a=\[AL(Y==0,1) ;AL(Y==1,2) ;AL(Y==2,3)\];

elseif (numClasses==10)

a=\[AL(Y==0,1) ;AL(Y==1,2) ;AL(Y==2,3);AL(Y==3,4);AL(Y==4,5);

AL(Y==5,6); AL(Y==6,7);AL(Y==7,8);AL(Y==8,9);AL(Y==9,10)\];

endif

end

\# Compute the cost

\# Input : AL

\# : Y

\# : outputActivationFunc- sigmoid/softmax

\# : numClasses

\# Output: cost

function \[cost\]= computeCost(AL, Y,

outputActivationFunc="sigmoid",numClasses) if(strcmp(outputActivationFunc,"sigmoid"))

numTraining= size(Y)(2);

\# Element wise multiply for logprobs

cost = -1/numTraining \* sum((Y .\* log(AL)) + (1-Y) .\* log(1-AL)); elseif(strcmp(outputActivationFunc,'softmax'))

numTraining = size(Y)(2);

Y=Y';

\# Select rows where Y=0,1,and 2 and concatenate to a long vector

#a=\[AL(Y==0,1) ;AL(Y==1,2) ;AL(Y==2,3)\];

a =pickColumns(AL,Y,numClasses);

#Select the correct column for log prob

correct\_probs = -log(a);

#Compute log loss

cost= sum(correct\_probs)/numTraining;

endif

end

\# Compute the backpropoagation for 1 cycle

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# # Input features

\# # Output values Y

\# # activationFunc- sigmoid/softmax/tanh

\# # numClasses

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

function \[dA\_prev dW db\] = layerActivationBackward(dA, forward\_cache, activation\_cache, Y, activationFunc,numClasses)

A\_prev = forward\_cache{1};

W =forward\_cache{2};

b = forward\_cache{3};

numTraining = size(A\_prev)(2);

if (strcmp(activationFunc,"relu"))

dZ = reluDerivative(dA, activation\_cache);

 elseif (strcmp(activationFunc,"sigmoid")) dZ = sigmoidDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "tanh"))

dZ = tanhDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "softmax"))

#dZ = softmaxDerivative(dA, activation\_cache,Y,numClasses);

dZ = stableSoftmaxDerivative(dA, activation\_cache,Y,numClasses); endif

\# Check if softmax

if (strcmp(activationFunc,"softmax"))

W =forward\_cache{2};

b = forward\_cache{3};

dW = 1/numTraining \* A\_prev \* dZ;

db = 1/numTraining \* sum(dZ,1);

dA\_prev = dZ\*W;

else

W =forward\_cache{2};

b = forward\_cache{3};

dW = 1/numTraining \* dZ \* A\_prev';

db = 1/numTraining \* sum(dZ,2);

dA\_prev = W'\*dZ;

endif

end

\# Compute the backpropoagation for 1 cycle

\# Input : AL: Output of L layer Network - weights

\# # Y Real output

\# # caches -- list of caches containing:

\# every cache of layerActivationForward() with "relu"/"tanh"

\# #(it's caches\[l\], for l in range(L-1) i.e l = 0...L-2)

\# #the cache of layerActivationForward() with "sigmoid" (it's caches\[L-1\])

\# # hiddenActivationFunc - Activation function at hidden layers

\# # outputActivationFunc- sigmoid/softmax

\# # numClasses

#

\# Returns:

\# gradients -- A dictionary with the gradients

\# gradients\["dA" + str(l)\] = ...

\# gradients\["dW" + str(l)\] = ...

\# gradients\["db" + str(l)\] = ...

function \[gradsDA gradsDW gradsDB\]= backwardPropagationDeep(AL, Y, activation\_caches,forward\_caches,

hiddenActivationFunc='relu',outputActivationFunc="sigmoid",numClasses)

\# Set the number of layers

L = length(activation\_caches);

m = size(AL)(2);

if (strcmp(outputActivationFunc,"sigmoid"))

\# Initializing the backpropagation

\# dl/dAL= -(y/a + (1-y)/(1-a)) - At the output layer

dAL = -((Y ./ AL) - (1 - Y) ./ ( 1 - AL));

elseif (strcmp(outputActivationFunc,"softmax"))

dAL=0;

Y=Y';

endif

\# Since this is a binary classification the activation at output is sigmoid

\# Get the gradients at the last layer

\# Inputs: "AL, Y, caches".

\# Outputs: "gradients\["dAL"\], gradients\["dWL"\], gradients\["dbL"\]

activation\_cache = activation\_caches{L};

forward\_cache = forward\_caches(L);

\# Note the cell array includes an array of forward caches. To get to this we need to include the index {1}

\[dA dW db\] = layerActivationBackward(dAL, forward\_cache{1},

activation\_cache, Y, activationFunc = outputActivationFunc,numClasses); if (strcmp(outputActivationFunc,"sigmoid"))

gradsDA{L}= dA;

elseif (strcmp(outputActivationFunc,"softmax"))

gradsDA{L}= dA';#Note the transpose

 endif

gradsDW{L}= dW;

gradsDB{L}= db;

\# Traverse in the reverse direction

for l =(L-1):-1:1

\# Compute the gradients for L-1 to 1 for Relu/tanh

\# Inputs: "gradients\["dA" + str(l + 2)\], caches".

\# Outputs: "gradients\["dA" + str(l + 1)\] , gradients\["dW" + str(l + 1)\] , gradients\["db" + str(l + 1)\]

activation\_cache = activation\_caches{l};

forward\_cache = forward\_caches(l);

#dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackward(gradients\['dA'+str(l+1)\], current\_cache, activationFunc = "relu")

\# dAl the dervative of the activation of the lth layer,is the first element dAl= gradsDA{l+1};

\[dA\_prev\_temp, dW\_temp, db\_temp\] = layerActivationBackward(dAl, forward\_cache{1}, activation\_cache, Y, activationFunc =

hiddenActivationFunc,numClasses);

gradsDA{l}= dA\_prev\_temp;

gradsDW{l}= dW\_temp;

gradsDB{l}= db\_temp;

endfor

end

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients

\# : learning rate

\# : outputActivationFunc

#output : weights, biases

function \[weights biases\] = gradientDescent(weights, biases,gradsW,gradsB, learningRate,outputActivationFunc="sigmoid")

 L = size(weights)(2); # number of layers in the neural network

\# Update rule for each parameter.

for l=1:(L-1)

weights{l} = weights{l} -learningRate\* gradsW{l};

biases{l} = biases{l} -learningRate\* gradsB{l};

endfor

if (strcmp(outputActivationFunc,"sigmoid"))

weights{L} = weights{L} -learningRate\* gradsW{L};

biases{L} = biases{L} -learningRate\* gradsB{L};

elseif (strcmp(outputActivationFunc,"softmax"))

weights{L} = weights{L} -learningRate\* gradsW{L}';

biases{L} = biases{L} -learningRate\* gradsB{L}';

endif

end

\# Execute a L layer Deep learning model

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu /tanh

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : learning rate

\# : num of iterations

#output : Updated weights and biases after each iteration

function \[weights biases costs\] = L\_Layer\_DeepModel(X, Y, layersDimensions, hiddenActivationFunc='relu', outputActivationFunc="sigmoid",learning\_rate =

.3, num\_iterations = 10000)#lr was 0.009

rand ("seed", 1);

costs = \[\] ;

\# Parameters initialization.

 \[weights biases\] = initializeDeepModel(layersDimensions);

\# Loop (gradient descent)

for i = 0:num\_iterations

\# Forward propagation: \[LINEAR -> RELU\]\*(L-1) -> LINEAR -> SIGMOID.

\[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights, biases,hiddenActivationFunc,

outputActivationFunc=outputActivationFunc);

\# Compute cost.

cost = computeCost(AL,

Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));

\# Backward propagation.

\[gradsDA gradsDW gradsDB\] = backwardPropagationDeep(AL, Y,

activation\_caches,forward\_caches,hiddenActivationFunc,

outputActivationFunc=outputActivationFunc,

numClasses=layersDimensions(size(layersDimensions)

(2)));

\# Update parameters.

\[weights biases\] = gradientDescent(weights,biases,

gradsDW,gradsDB,learning\_rate,outputActivationFunc=outputActivationFunc);

\# Print the cost every 1000 iterations

if ( mod(i,1000) == 0)

costs =\[costs cost\];

#disp ("Cost after iteration"), disp(i),disp(cost); printf("Cost after iteration i=%i cost=%d\\n",i,cost); endif

endfor

end

\# Execute a L layer Deep learning model with Stochastic Gradient descent

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu /tanh

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : learning rate

\# : mini\_batch\_size

\# : num of epochs

#output : Updated weights and biases after each iteration

function \[weights biases costs\] = L\_Layer\_DeepModel\_SGD(X, Y, layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",learning\_rate = .3,

mini\_batch\_size = 64, num\_epochs = 2500)#lr was 0.009

rand ("seed", 1);

costs = \[\] ;

\# Parameters initialization.

\[weights biases\] = initializeDeepModel(layersDimensions);

seed=10;

\# Loop (gradient descent)

for i = 0:num\_epochs

seed = seed + 1;

\[mini\_batches\_X mini\_batches\_Y\] = random\_mini\_batches(X, Y,

mini\_batch\_size, seed);

minibatches=length(mini\_batches\_X);

for batch=1:minibatches

X=mini\_batches\_X{batch};

Y=mini\_batches\_Y{batch};

\# Forward propagation: \[LINEAR -> RELU\]\*(L-1) -> LINEAR -> SIGMOID/SOFTMAX.

\[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights, biases,hiddenActivationFunc,

outputActivationFunc=outputActivationFunc);

#disp(batch);

#disp(size(X));

#disp(size(Y));

\# Compute cost.

 cost = computeCost(AL,

Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));

#disp(cost);

\# Backward propagation.

\[gradsDA gradsDW gradsDB\] = backwardPropagationDeep(AL, Y,

activation\_caches,forward\_caches,hiddenActivationFunc,

outputActivationFunc=outputActivationFunc,

numClasses=layersDimensions(size(layersDimensions)

(2)));

\# Update parameters.

\[weights biases\] = gradientDescent(weights,biases,

gradsDW,gradsDB,learning\_rate,outputActivationFunc=outputActivationFunc); endfor

\# Print the cost every 1000 iterations

if ( mod(i,1000) == 0)

costs =\[costs cost\];

#disp ("Cost after iteration"), disp(i),disp(cost); printf("Cost after iteration i=%i cost=%d\\n",i,cost); endif

endfor

end

\# Plot cost vs iterations

function plotCostVsIterations(maxIterations,costs)

iterations=\[0:1000:maxIterations\];

plot(iterations,costs);

title ("Cost vs no of iterations ");

xlabel("No of iterations");

ylabel("Cost");

print -dpng figure23.jpg

end;

\# Compute the predicted value for a given input

\# Input : Neural Network parameters

\# : Input data

function \[predictions\]= predict(weights, biases, X,hiddenActivationFunc="relu")

\[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights, biases,hiddenActivationFunc);

predictions = (AL>0.5);

end

\# Plot the decision boundary

function plotDecisionBoundary(data,weights,

biases,hiddenActivationFunc="relu")

%Plot a non-linear decision boundary learned by the SVM

colormap ("summer");

% Make classification predictions over a grid of values

x1plot = linspace(min(data(:,1)), max(data(:,1)), 400)';

x2plot = linspace(min(data(:,2)), max(data(:,2)), 400)';

\[X1, X2\] = meshgrid(x1plot, x2plot);

vals = zeros(size(X1));

\# Plot the prediction for the grid

for i = 1:size(X1, 2)

gridPoints = \[X1(:, i), X2(:, i)\];

vals(:, i)=predict(weights,

biases,gridPoints',hiddenActivationFunc=hiddenActivationFunc); endfor

scatter(data(:,1),data(:,2),8,c=data(:,3),"filled");

% Plot the boundary

hold on

#contour(X1, X2, vals, \[0 0\], 'LineWidth', 2);

contour(X1, X2, vals,"linewidth",4);

title ({"3 layer Neural Network decision boundary"}); hold off;

print -dpng figure32.jpg

end

\# Compute scores

function \[AL\]= scores(weights, biases, X,hiddenActivationFunc="relu")

\[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights, biases,hiddenActivationFunc);

end

\# Create Random mini batches. Return cell arrays with the mini batches

\# Input : X, Y

\# : Size of minibatch

\# : seed

#Output : mini batches X & Y

function \[mini\_batches\_X mini\_batches\_Y\]= random\_mini\_batches(X, Y, miniBatchSize = 64, seed = 0)

rand ("seed", seed);

\# Get number of training samples

m = size(X)(2);

\# Create a list of random numbers < m

permutation = randperm(m);

\# Randomly shuffle the training data

shuffled\_X = X(:, permutation);

shuffled\_Y = Y(:, permutation);

\# Compute number of mini batches

numCompleteMinibatches = floor(m/miniBatchSize);

batch=0;

for k = 0:(numCompleteMinibatches-1)

#Set the start and end of each mini batch

batch=batch+1;

lower=(k\*miniBatchSize)+1;

upper=(k+1) \* miniBatchSize;

mini\_batch\_X = shuffled\_X(:, lower:upper);

mini\_batch\_Y = shuffled\_Y(:, lower:upper);

\# Create cell arrays

mini\_batches\_X{batch} = mini\_batch\_X;

mini\_batches\_Y{batch} = mini\_batch\_Y;

endfor

\# If the batc size does not cleanly divide with number of mini batches if mod(m ,miniBatchSize) != 0

 # Set the start and end of the last mini batch l=floor(m/miniBatchSize)\*miniBatchSize;

m=l+ mod(m,miniBatchSize);

mini\_batch\_X = shuffled\_X(:,(l+1):m);

mini\_batch\_Y = shuffled\_Y(:,(l+1):m);

batch=batch+1;

mini\_batches\_X{batch} = mini\_batch\_X;

mini\_batches\_Y{batch} = mini\_batch\_Y;

endif

end

**7.**

**Appendix 6 - Initialization,**

**regularization in Deep Learning**

**6.1 Python**

\# -\*- coding: utf-8 -\*-

############################################################################################################

#

\# File: DLfunctions61.py

\# Developer: Tinniam V Ganesh

\# Date : 16 Apr 2018

#

##########################################################################################################

import numpy as np

import matplotlib.pyplot as plt

import matplotlib

import matplotlib.pyplot as plt

from matplotlib import cm

import math

import sklearn

import sklearn.datasets

\# Conmpute the sigmoid of a vector

def sigmoid(Z):

A=1/(1+np.exp(-Z))

cache=Z

return A,cache

\# Conmpute the Relu of a vector

def relu(Z):

A = np.maximum(0,Z)

cache=Z

return A,cache

\# Conmpute the tanh of a vector

def tanh(Z):

 A = np.tanh(Z)

cache=Z

return A,cache

\# Conmpute the softmax of a vector

def softmax(Z):

\# get unnormalized probabilities

exp\_scores = np.exp(Z.T)

\# normalize them for each example

A = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

cache=Z

return A,cache

\# Conmpute the Stable Softmax of a vector

def stableSoftmax(Z):

#Compute the softmax of vector x in a numerically stable way.

shiftZ = Z.T - np.max(Z.T,axis=1).reshape(-1,1)

exp\_scores = np.exp(shiftZ)

\# normalize them for each example

A = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

cache=Z

return A,cache

\# Compute the detivative of Relu

def reluDerivative(dA, cache):

Z = cache

dZ = np.array(dA, copy=True) # just converting dz to a correct object.

\# When z <= 0, you should set dz to 0 as well.

dZ\[Z <= 0\] = 0

return dZ

\# Compute the derivative of sigmoid

def sigmoidDerivative(dA, cache):

Z = cache

s = 1/(1+np.exp(-Z))

dZ = dA \* s \* (1-s)

return dZ

\# Compute the derivative of tanh

def tanhDerivative(dA, cache):

Z = cache

a = np.tanh(Z)

dZ = dA \* (1 - np.power(a, 2))

return dZ

\# Compute the derivative of softmax

def softmaxDerivative(dA, cache,y,numTraining):

\# Note : dA not used. dL/dZ = dL/dA \* dA/dZ = pi-yi

Z = cache

\# Compute softmax

exp\_scores = np.exp(Z.T)

\# normalize them for each example

probs = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

\# compute the gradient on scores

dZ = probs

\# dZ = pi- yi

dZ\[range(int(numTraining)),y\[:,0\]\] -= 1

return(dZ)

\# Compute the derivative of Stable Softmax

def stableSoftmaxDerivative(dA, cache,y,numTraining):

\# Note : dA not used. dL/dZ = dL/dA \* dA/dZ = pi-yi

Z = cache

\# Compute stable softmax

shiftZ = Z.T - np.max(Z.T,axis=1).reshape(-1,1)

exp\_scores = np.exp(shiftZ)

\# normalize them for each example

probs = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

#print(probs)

\# compute the gradient on scores

dZ = probs

\# dZ = pi- yi

dZ\[range(int(numTraining)),y\[:,0\]\] -= 1

 return(dZ)

\# Initialize the model

\# Input : number of features

\# number of hidden units

\# number of units in output

\# Returns: Weight and bias matrices and vectors

def initializeModel(numFeats,numHidden,numOutput):

np.random.seed(1)

W1=np.random.randn(numHidden,numFeats)\*0.01 # Multiply by .01

b1=np.zeros((numHidden,1))

W2=np.random.randn(numOutput,numHidden)\*0.01

b2=np.zeros((numOutput,1))

\# Create a dictionary of the neural network parameters

nnParameters={'W1':W1,'b1':b1,'W2':W2,'b2':b2}

return(nnParameters)

\# Initialize model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers def initializeDeepModel(layerDimensions):

np.random.seed(3)

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

layerParams = {}

for l in range(1,len(layerDimensions)):

layerParams\['W' + str(l)\] =

np.random.randn(layerDimensions\[l\],layerDimensions\[l-1\])\*0.01 # Multiply by

.01

layerParams\['b' + str(l)\] = np.zeros((layerDimensions\[l\],1))

return(layerParams)

return Z, cache

\# He Initialization model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers

\# He initilization multiplies the random numbers with sqrt(2/layerDimensions\[l-1\])

def HeInitializeDeepModel(layerDimensions):

np.random.seed(3)

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

layerParams = {}

for l in range(1,len(layerDimensions)):

layerParams\['W' + str(l)\] = np.random.randn(layerDimensions\[l\], layerDimensions\[l-1\])\*np.sqrt(2/layerDimensions\[l-1\])

layerParams\['b' + str(l)\] = np.zeros((layerDimensions\[l\],1))

return(layerParams)

return Z, cache

\# Xavier Initialization model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers

\# Xavier initilization multiplies the random numbers with

sqrt(1/layerDimensions\[l-1\])

def XavInitializeDeepModel(layerDimensions):

np.random.seed(3)

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

layerParams = {}

for l in range(1,len(layerDimensions)):

layerParams\['W' + str(l)\] = np.random.randn(layerDimensions\[l\], layerDimensions\[l-1\])\*np.sqrt(1/layerDimensions\[l-1\])

layerParams\['b' + str(l)\] = np.zeros((layerDimensions\[l\],1))

return(layerParams)

return Z, cache

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prev - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# keep\_prob

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : The Activation of this layer

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

def layerActivationForward(A\_prev, W, b, keep\_prob=1,

activationFunc="relu"):

\# Compute Z

Z = np.dot(W,A\_prev) + b

forward\_cache = (A\_prev, W, b)

\# Compute the activation for sigmoid

if activationFunc == "sigmoid":

A, activation\_cache = sigmoid(Z)

\# Compute the activation for Relu

elif activationFunc == "relu":

A, activation\_cache = relu(Z)

\# Compute the activation for tanh

elif activationFunc == 'tanh':

A, activation\_cache = tanh(Z)

elif activationFunc == 'softmax':

A, activation\_cache = stableSoftmax(Z)

cache = (forward\_cache, activation\_cache)

return A, cache

\# Compute the forward propagation for layers 1..L

\# Input : X - Input Features

\# parameters: Weights and biases

\# keep\_prob

\# hiddenActivationFunc - Activation function at hidden layers Relu/tanh

\# outputActivationFunc - Activation function at output - sigmoid/softmax

\# Returns : AL

\# caches

\# dropoutMat

\# The forward propoagtion uses the Relu/tanh activation from layer 1..L-1 and sigmoid actiovation at layer L

def forwardPropagationDeep(X, parameters,keep\_prob=1,

hiddenActivationFunc='relu',outputActivationFunc='sigmoid'):

caches = \[\]

#initialize the dropout matrix

dropoutMat = {}

\# Set A to X (A0)

A = X

L = int(len(parameters)/2) # number of layers in the neural network

\# Loop through from layer 1 to upto layer L

for l in range(1, L):

A\_prev = A

\# Zi = Wi x Ai-1 + bi and Ai = g(Zi)

A, cache = layerActivationForward(A\_prev, parameters\['W'+str(l)\], parameters\['b'+str(l)\], keep\_prob, activationFunc = hiddenActivationFunc)

\# Randomly drop some activation units

\# Create a matrix as the same shape as A

D = np.random.rand(A.shape\[0\],A.shape\[1\])

D = (D < keep\_prob)

\# We need to use the same 'dropout' matrix in backward propagation

\# Save the dropout matrix for use in backprop

dropoutMat\["D" + str(l)\] =D

A= np.multiply(A,D)

A = np.divide(A,keep\_prob)

caches.append(cache)

\# Since this is binary classification use the sigmoid activation function in

\# last layer

AL, cache = layerActivationForward(A, parameters\['W'+str(L)\], parameters\['b'+str(L)\], activationFunc = outputActivationFunc) caches.append(cache)

return AL, caches, dropoutMat

\# Compute the cost

\# Input : parameters

\# : AL

\# : Y

\# :outputActivationFunc - Activation function at output -

sigmoid/softmax/tanh

\# Output: cost

def computeCost(parameters,AL,Y,outputActivationFunc="sigmoid"): if outputActivationFunc=="sigmoid":

m= float(Y.shape\[1\])

\# Element wise multiply for logprobs

cost=-1/m \*np.sum(Y\*np.log(AL) + (1-Y)\*(np.log(1-AL)))

cost = np.squeeze(cost)

elif outputActivationFunc=="softmax":

\# Take transpose of Y for softmax

Y=Y.T

m= float(len(Y))

\# Compute log probs. Take the log prob of correct class based on output y correct\_logprobs = -np.log(AL\[range(int(m)),Y.T\])

\# Conpute loss

cost = np.sum(correct\_logprobs)/m

return cost

\# Compute the cost with regularization

\# Input : parameters

\# : AL

\# : Y

\# : lambd

\# :outputActivationFunc - Activation function at output -

sigmoid/softmax/tanh

\# Output: cost

def computeCostWithReg(parameters,AL,Y,lambd,

outputActivationFunc="sigmoid"):

if outputActivationFunc=="sigmoid":

m= float(Y.shape\[1\])

\# Element wise multiply for logprobs

cost=-1/m \*np.sum(Y\*np.log(AL) + (1-Y)\*(np.log(1-AL)))

 cost = np.squeeze(cost)

\# Regularization cost

L= int(len(parameters)/2)

L2RegularizationCost=0

for l in range(L):

L2RegularizationCost+=np.sum(np.square(parameters\['W'+str(l+1)\])) L2RegularizationCost = (lambd/(2\*m))\*L2RegularizationCost

cost = cost + L2RegularizationCost

elif outputActivationFunc=="softmax":

\# Take transpose of Y for softmax

Y=Y.T

m= float(len(Y))

\# Compute log probs. Take the log prob of correct class based on output y correct\_logprobs = -np.log(AL\[range(int(m)),Y.T\])

\# Conpute loss

cost = np.sum(correct\_logprobs)/m

\# Regularization cost

L= int(len(parameters)/2)

L2RegularizationCost=0

for l in range(L):

L2RegularizationCost+=np.sum(np.square(parameters\['W'+str(l+1)\])) L2RegularizationCost = (lambd/(2\*m))\*L2RegularizationCost

cost = cost + L2RegularizationCost

return cost

\# Compute the backpropoagation for 1 cycle with dropout included

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# # Input features

\# # keep\_prob

\# # Output values Y

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

def layerActivationBackward(dA, cache, Y, keep\_prob=1,

activationFunc="relu"):

forward\_cache, activation\_cache = cache

A\_prev, W, b = forward\_cache

numtraining = float(A\_prev.shape\[1\])

#print("n=",numtraining)

#print("no=",numtraining)

if activationFunc == "relu":

dZ = reluDerivative(dA, activation\_cache)

elif activationFunc == "sigmoid":

dZ = sigmoidDerivative(dA, activation\_cache)

elif activationFunc == "tanh":

dZ = tanhDerivative(dA, activation\_cache)

elif activationFunc == "softmax":

dZ = stableSoftmaxDerivative(dA, activation\_cache,Y,numtraining) if activationFunc == 'softmax':

dW = 1/numtraining \* np.dot(A\_prev,dZ)

db = 1/numtraining \* np.sum(dZ, axis=0, keepdims=True)

dA\_prev = np.dot(dZ,W)

else:

#print(numtraining)

dW = 1/numtraining \*(np.dot(dZ,A\_prev.T))

#print("dW=",dW)

db = 1/numtraining \* np.sum(dZ, axis=1, keepdims=True)

#print("db=",db)

dA\_prev = np.dot(W.T,dZ)

return dA\_prev, dW, db

\# Compute the backpropoagation with regularization for 1 cycle

\# Input : dA-Neural Network parameters

\# # cache - forward\_cache & activation\_cache

\# # Output values Y

\# # lambd

\# # activationFunc

\# Returns dA\_prev, dW, db

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

def layerActivationBackwardWithReg(dA, cache, Y, lambd, activationFunc): forward\_cache, activation\_cache = cache

A\_prev, W, b = forward\_cache

numtraining = float(A\_prev.shape\[1\])

#print("n=",numtraining)

#print("no=",numtraining)

if activationFunc == "relu":

dZ = reluDerivative(dA, activation\_cache)

elif activationFunc == "sigmoid":

dZ = sigmoidDerivative(dA, activation\_cache)

elif activationFunc == "tanh":

dZ = tanhDerivative(dA, activation\_cache)

elif activationFunc == "softmax":

dZ = stableSoftmaxDerivative(dA, activation\_cache,Y,numtraining) if activationFunc == 'softmax':

\# Add the regularization factor

dW = 1/numtraining \* np.dot(A\_prev,dZ) + (lambd/numtraining) \* W.T

db = 1/numtraining \* np.sum(dZ, axis=0, keepdims=True)

dA\_prev = np.dot(dZ,W)

else:

\# Add the regularization factor

dW = 1/numtraining \*(np.dot(dZ,A\_prev.T)) + (lambd/numtraining) \* W

#print("dW=",dW)

db = 1/numtraining \* np.sum(dZ, axis=1, keepdims=True)

#print("db=",db)

dA\_prev = np.dot(W.T,dZ)

return dA\_prev, dW, db

\# Compute the backpropoagation for 1 cycle

\# Input : AL: Output of L layer Network - weights

\# # Y Real output

\# # caches -- list of caches containing:

\# # dropoutMat

\# # lambd

\# # keep\_prob

\# every cache of layerActivationForward() with "relu"/"tanh"

\# #(it's caches\[l\], for l in range(L-1) i.e l = 0...L-2)

\# #the cache of layerActivationForward() with "sigmoid" (it's caches\[L-1\])

\# # hiddenActivationFunc - Activation function at hidden layers -

relu/sigmoid/tanh

\# #outputActivationFunc - Activation function at output - sigmoid/softmax

#

\# Returns:

\# gradients -- A dictionary with the gradients

\# gradients\["dA" + str(l)\] = ...

\# gradients\["dW" + str(l)\] = ...

def backwardPropagationDeep(AL, Y, caches, dropoutMat, lambd=0, keep\_prob=1, hiddenActivationFunc='relu',outputActivationFunc="sigmoid"):

#initialize the gradients

gradients = {}

\# Set the number of layers

L = len(caches)

m = float(AL.shape\[1\])

if outputActivationFunc == "sigmoid":

Y = Y.reshape(AL.shape) # after this line, Y is the same shape as AL

\# Initializing the backpropagation

\# dl/dAL= -(y/a + (1-y)/(1-a)) - At the output layer

dAL = - (np.divide(Y, AL) - np.divide(1 - Y, 1 - AL))

else:

dAL =0

Y=Y.T

\# Since this is a binary classification the activation at output is sigmoid

\# Get the gradients at the last layer

\# Inputs: "AL, Y, caches".

\# Outputs: "gradients\["dAL"\], gradients\["dWL"\], gradients\["dbL"\]

current\_cache = caches\[L-1\]

if lambd==0:

gradients\["dA" + str(L)\], gradients\["dW" + str(L)\], gradients\["db" + str(L)\]

\= layerActivationBackward(dAL, current\_cache,

 Y, activationFunc = outputActivationFunc) else: #Regularization

gradients\["dA" + str(L)\], gradients\["dW" + str(L)\], gradients\["db" + str(L)\]

\= layerActivationBackwardWithReg(dAL, current\_cache,

Y, lambd, activationFunc = outputActivationFunc)

\# Note dA for softmax is the transpose

if outputActivationFunc == "softmax":

gradients\["dA" + str(L)\] = gradients\["dA" + str(L)\].T

\# Traverse in the reverse direction

for l in reversed(range(L-1)):

\# Compute the gradients for L-1 to 1 for Relu/tanh

\# Inputs: "gradients\["dA" + str(l + 2)\], caches".

\# Outputs: "gradients\["dA" + str(l + 1)\] , gradients\["dW" + str(l + 1)\] , gradients\["db" + str(l + 1)\]

current\_cache = caches\[l\]

#dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackward(gradients\['dA'+str(l+2)\], current\_cache, activationFunc = "relu")

if lambd==0:

\# In the reverse direction use the dame dropout matrix

\# Random dropout

\# Multiply dA'l' with the dropoutMat and divide to keep the expected value same

D = dropoutMat\["D" + str(l+1)\]

\# Drop some dAl's

gradients\['dA'+str(l+2)\]= np.multiply(gradients\['dA'+str(l+2)\],D)

\# Divide by keep\_prob to keep expected value same

gradients\['dA'+str(l+2)\] = np.divide(gradients\['dA'+str(l+2)\],keep\_prob) dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackward(gradients\['dA'+str(l+2)\], current\_cache, Y, keep\_prob=1, activationFunc = hiddenActivationFunc)

else:

dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackwardWithReg(gradients\['dA'+str(l+2)\], current\_cache, Y,

lambd, activationFunc = hiddenActivationFunc) gradients\["dA" + str(l + 1)\] = dA\_prev\_temp

gradients\["dW" + str(l + 1)\] = dW\_temp

gradients\["db" + str(l + 1)\] = db\_temp

return gradients

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients

\# : learning rate

\# : outputActivationFunc - Activation function at output - sigmoid/softmax

#output : Updated weights after 1 iteration

def gradientDescent(parameters, gradients,

learningRate,outputActivationFunc="sigmoid"):

L = int(len(parameters) / 2)

\# Update rule for each parameter.

for l in range(L-1):

parameters\["W" + str(l+1)\] = parameters\['W'+str(l+1)\] -learningRate\*

gradients\['dW' + str(l+1)\]

parameters\["b" + str(l+1)\] = parameters\['b'+str(l+1)\] -learningRate\*

gradients\['db' + str(l+1)\]

if outputActivationFunc=="sigmoid":

parameters\["W" + str(L)\] = parameters\['W'+str(L)\] -learningRate\*

gradients\['dW' + str(L)\]

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] -learningRate\*

gradients\['db' + str(L)\]

elif outputActivationFunc=="softmax":

parameters\["W" + str(L)\] = parameters\['W'+str(L)\] -learningRate\*

gradients\['dW' + str(L)\].T

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] -learningRate\*

gradients\['db' + str(L)\].T

return parameters

\# Execute a L layer Deep learning model

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu

/tanh/sigmoid

\# : outputActivationFunc - Activation function at output layer sigmoid/softmax

\# : learning rate

\# : lambd

\# : keep\_prob

\# : num of iteration

\# : initType

#output : parameters

def L\_Layer\_DeepModel(X1, Y1, layersDimensions,

hiddenActivationFunc='relu', outputActivationFunc="sigmoid", learningRate = .3, lambd=0, keep\_prob=1, num\_iterations =

10000,initType="default", print\_cost=False,figure="figa.png"): np.random.seed(1)

costs = \[\]

\# Parameters initialization.

if initType == "He":

parameters = HeInitializeDeepModel(layersDimensions)

elif initType == "Xavier" :

parameters = XavInitializeDeepModel(layersDimensions)

else: #Default

parameters = initializeDeepModel(layersDimensions)

\# Loop (gradient descent)

for i in range(0, num\_iterations):

AL, caches, dropoutMat = forwardPropagationDeep(X1, parameters, keep\_prob,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc)

 # Regularization parameter is 0

if lambd==0:

\# Compute cost

cost = computeCost(parameters,AL, Y1,

outputActivationFunc=outputActivationFunc)

\# Include L2 regularization

else:

\# Compute cost

cost = computeCostWithReg(parameters,AL, Y1, lambd,

outputActivationFunc=outputActivationFunc)

\# Backward propagation.

gradients = backwardPropagationDeep(AL, Y1, caches, dropoutMat, lambd, keep\_prob,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc)

\# Update parameters.

parameters = gradientDescent(parameters, gradients,

learningRate=learningRate,outputActivationFunc=outputActivationFunc)

\# Print the cost every 100 training example

if print\_cost and i % 1000 == 0:

print ("Cost after iteration %i: %f" %(i, cost))

if print\_cost and i % 1000 == 0:

costs.append(cost)

\# plot the cost

plt.plot(np.squeeze(costs))

plt.ylabel('Cost')

plt.xlabel('No of iterations (x1000)')

plt.title("Learning rate =" + str(learningRate))

plt.savefig(figure,bbox\_inches='tight')

#plt.show()

plt.clf()

plt.close()

 return parameters

\# Execute a L layer Deep learning model Stoachastic Gradient Descent

\# Input : X1 - Input features

\# : Y1- output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu

/tanh/sigmoid

\# : outputActivationFunc - Activation function at output - sigmoid/softmax

\# : learning rate

\# : mini\_batch\_size

\# : num\_epochs

#output : parameters

def L\_Layer\_DeepModel\_SGD(X1, Y1, layersDimensions,

hiddenActivationFunc='relu', outputActivationFunc="sigmoid",learningRate =

.3, mini\_batch\_size = 64, num\_epochs = 2500, print\_cost=False):#lr was 0.009

np.random.seed(1)

costs = \[\]

\# Parameters initialization.

parameters = initializeDeepModel(layersDimensions)

seed=10

\# Loop for number of epochs

for i in range(num\_epochs):

\# Define the random minibatches. We increment the seed to reshuffle differently the dataset after each epoch

seed = seed + 1

minibatches = random\_mini\_batches(X1, Y1, mini\_batch\_size, seed) batch=0

\# Loop through each mini batch

for minibatch in minibatches:

#print("batch=",batch)

batch=batch+1

\# Select a minibatch

(minibatch\_X, minibatch\_Y) = minibatch

 # Perfrom forward propagation

AL, caches = forwardPropagationDeep(minibatch\_X,

parameters,hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc)

\# Compute cost

cost = computeCost(AL,

minibatch\_Y,outputActivationFunc=outputActivationFunc)

#print("minibatch\_Y=",minibatch\_Y.shape)

\# Backward propagation.

gradients = backwardPropagationDeep(AL, minibatch\_Y,

caches,hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc)

\# Update parameters.

parameters = gradientDescent(parameters, gradients,

learningRate=learningRate,outputActivationFunc=outputActivationFunc)

\# Print the cost every 1000 epoch

if print\_cost and i % 100 == 0:

print ("Cost after epoch %i: %f" %(i, cost))

if print\_cost and i % 100 == 0:

costs.append(cost)

\# plot the cost

plt.plot(np.squeeze(costs))

plt.ylabel('cost')

plt.xlabel('No of iterations')

plt.title("Learning rate =" + str(learningRate))

#plt.show()

plt.savefig("fig1",bbox\_inches='tight')

plt.close()

return parameters

\# Create random mini batches

\# Input : X - Input features

\# : Y- output

\# : miniBatchSizes

\# : seed

#output : mini\_batches

def random\_mini\_batches(X, Y, miniBatchSize = 64, seed = 0): np.random.seed(seed)

\# Get number of training samples

m = X.shape\[1\]

\# Initialize mini batches

mini\_batches = \[\]

\# Create a list of random numbers < m

permutation = list(np.random.permutation(m))

\# Randomly shuffle the training data

shuffled\_X = X\[:, permutation\]

shuffled\_Y = Y\[:, permutation\].reshape((1,m))

\# Compute number of mini batches

numCompleteMinibatches = math.floor(m/miniBatchSize)

\# For the number of mini batches

for k in range(0, numCompleteMinibatches):

\# Set the start and end of each mini batch

mini\_batch\_X = shuffled\_X\[:, k\*miniBatchSize : (k+1) \* miniBatchSize\]

mini\_batch\_Y = shuffled\_Y\[:, k\*miniBatchSize : (k+1) \* miniBatchSize\]

mini\_batch = (mini\_batch\_X, mini\_batch\_Y)

mini\_batches.append(mini\_batch)

#if m % miniBatchSize != 0:. The batch does not evenly divide by the mini batch

if m % miniBatchSize != 0:

l=math.floor(m/miniBatchSize)\*miniBatchSize

\# Set the start and end of last mini batch

m=l+m % miniBatchSize

mini\_batch\_X = shuffled\_X\[:,l:m\]

mini\_batch\_Y = shuffled\_Y\[:,l:m\]

mini\_batch = (mini\_batch\_X, mini\_batch\_Y)

mini\_batches.append(mini\_batch)

return mini\_batches

\# Plot a decision boundary

\# Input : Input Model,

\# X

\# Y

\# sz - Num of hiden units

\# lr - Learning rate

\# Fig to be saved as

\# Returns Null

def plot\_decision\_boundary(model, X, y,lr,figure1="figb.png"): print("plot")

\# Set min and max values and give it some padding

x\_min, x\_max = X\[0, :\].min() - 1, X\[0, :\].max() + 1

y\_min, y\_max = X\[1, :\].min() - 1, X\[1, :\].max() + 1

colors=\['black','gold'\]

cmap = matplotlib.colors.ListedColormap(colors)

h = 0.01

\# Generate a grid of points with distance h between them

xx, yy = np.meshgrid(np.arange(x\_min, x\_max, h), np.arange(y\_min, y\_max, h))

\# Predict the function value for the whole grid

Z = model(np.c\_\[xx.ravel(), yy.ravel()\])

Z = Z.reshape(xx.shape)

\# Plot the contour and training examples

plt.contourf(xx, yy, Z, cmap="coolwarm")

plt.ylabel('x2')

plt.xlabel('x1')

x=X.T

y=y.T.reshape(300,)

plt.scatter(x\[:, 0\], x\[:, 1\], c=y, s=20);

print(X.shape)

plt.title("Decision Boundary for learning rate:"+lr) plt.savefig(figure1, bbox\_inches='tight')

#plt.show()

def predict(parameters,

X,keep\_prob=1,hiddenActivationFunc="relu",outputActivationFunc="sigmoid"): A2, cache,dropoutMat = forwardPropagationDeep(X, parameters,

keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc) predictions = (A2>0.5)

return predictions

def predict\_proba(parameters, X,outputActivationFunc="sigmoid"): A2, cache = forwardPropagationDeep(X, parameters)

if outputActivationFunc=="sigmoid":

proba=A2

elif outputActivationFunc=="softmax":

proba=np.argmax(A2, axis=0).reshape(-1,1)

print("A2=",A2.shape)

return proba

\# Plot a decision boundary

\# Input : Input Model,

\# X

\# Y

\# sz - Num of hiden units

\# lr - Learning rate

\# Fig to be saved as

\# Returns Null

def plot\_decision\_boundary1(X, y,W1,b1,W2,b2,figure2="figc.png"):

#plot\_decision\_boundary(lambda x: predict(parameters, x.T),

x1,y1.T,str(0.3),"fig2.png")

h = 0.02

x\_min, x\_max = X\[:, 0\].min() - 1, X\[:, 0\].max() + 1

y\_min, y\_max = X\[:, 1\].min() - 1, X\[:, 1\].max() + 1

xx, yy = np.meshgrid(np.arange(x\_min, x\_max, h),

np.arange(y\_min, y\_max, h))

Z = np.dot(np.maximum(0, np.dot(np.c\_\[xx.ravel(), yy.ravel()\], W1.T) +

b1.T), W2.T) + b2.T

Z = np.argmax(Z, axis=1)

Z = Z.reshape(xx.shape)

fig = plt.figure()

plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral, alpha=0.8)

 print(X.shape)

y1=y.reshape(300,)

plt.scatter(X\[:, 0\], X\[:, 1\], c=y1, s=40, cmap=plt.cm.Spectral) plt.xlim(xx.min(), xx.max())

plt.ylim(yy.min(), yy.max())

plt.savefig(figure2, bbox\_inches='tight')

\# Load the circles data set

def load\_dataset():

np.random.seed(1)

train\_X, train\_Y = sklearn.datasets.make\_circles(n\_samples=300, noise=.05) np.random.seed(2)

test\_X, test\_Y = sklearn.datasets.make\_circles(n\_samples=100, noise=.05)

\# Visualize the data

print(train\_X.shape)

print(train\_Y.shape)

print("load")

#plt.scatter(train\_X\[:, 0\], train\_X\[:, 1\], c=train\_Y, s=40,

cmap=plt.cm.Spectral);

train\_X = train\_X.T

train\_Y = train\_Y.reshape((1, train\_Y.shape\[0\]))

test\_X = test\_X.T

test\_Y = test\_Y.reshape((1, test\_Y.shape\[0\]))

return train\_X, train\_Y, test\_X, test\_Y

**6.2 R**

############################################################################################################

#

\# File : DLfunctions6.R

\# Author : Tinniam V Ganesh

\# Date : 16 Apr 2018

#

##########################################################################################################

library(ggplot2)

library(PRROC)

library(dplyr)

\# Compute the sigmoid of a vector

sigmoid <- function(Z){

A <- 1/(1+ exp(-Z))

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the Relu(old) of a vector (performance hog!)

reluOld <-function(Z){

A <- apply(Z, 1:2, function(x) max(0,x))

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the Relu of a vector (performs better!)

relu <-function(Z){

\# Perform relu. Set values less that equal to 0 as 0

Z\[Z<0\]=0

A=Z

cache<-Z

retvals <- list("A"=A,"Z"=Z)

 return(retvals)

}

\# Compute the tanh activation of a vector

tanhActivation <- function(Z){

A <- tanh(Z)

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Conmpute the softmax of a vector

softmax <- function(Z){

\# get unnormalized probabilities

exp\_scores = exp(t(Z))

\# normalize them for each example

A = exp\_scores / rowSums(exp\_scores)

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the detivative of Relu

\# g'(z) = 1 if z >0 and 0 otherwise

reluDerivative <-function(dA, cache){

Z <- cache

dZ <- dA

\# Create a logical matrix of values > 0

a <- Z > 0

\# When z <= 0, you should set dz to 0 as well. Perform an element wise multiple

dZ <- dZ \* a

return(dZ)

}

\# Compute the derivative of sigmoid

\# Derivative g'(z) = a\* (1-a)

sigmoidDerivative <- function(dA, cache){

Z <- cache

s <- 1/(1+exp(-Z))

 dZ <- dA \* s \* (1-s)

return(dZ)

}

\# Compute the derivative of tanh

\# Derivative g'(z) = 1- a^2

tanhDerivative <- function(dA, cache){

Z = cache

a = tanh(Z)

dZ = dA \* (1 - a^2)

return(dZ)

}

\# This function is used in computing the softmax derivative

\# Populate a matrix of 1s in rows where Y==1

\# This may need to be extended for K classes. Currently

\# supports K=3 & K=10

popMatrix <- function(Y,numClasses){

a=rep(0,times=length(Y))

Y1=matrix(a,nrow=length(Y),ncol=numClasses)

#Set the rows and columns as 1's where Y is the class value

if(numClasses==3){

Y1\[Y==0,1\]=1

Y1\[Y==1,2\]=1

Y1\[Y==2,3\]=1

} else if (numClasses==10){

Y1\[Y==0,1\]=1

Y1\[Y==1,2\]=1

Y1\[Y==2,3\]=1

Y1\[Y==3,4\]=1

Y1\[Y==4,5\]=1

Y1\[Y==5,6\]=1

Y1\[Y==6,7\]=1

Y1\[Y==7,8\]=1

Y1\[Y==8,9\]=1

Y1\[Y==9,0\]=1

}

return(Y1)

}

\# Compute the softmax derivative

softmaxDerivative <- function(dA, cache ,y,numTraining,numClasses){

\# Note : dA not used. dL/dZ = dL/dA \* dA/dZ = pi-yi

Z <- cache

\# Compute softmax

exp\_scores = exp(t(Z))

\# normalize them for each example

probs = exp\_scores / rowSums(exp\_scores)

\# Create a matrix of zeros

Y1=popMatrix(y,numClasses)

#a=rep(0,times=length(Y))

#Y1=matrix(a,nrow=length(Y),ncol=numClasses)

#Set the rows and columns as 1's where Y is the class value

dZ = probs-Y1

return(dZ)

}

\# Initialize model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers initializeDeepModel <- function(layerDimensions){

set.seed(2)

\# Initialize empty list

layerParams <- list()

\# Note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Indices in R start from 1

for(l in 2:length(layersDimensions)){

\# Initialize a matrix of small random numbers of size l x l-1

\# Create random numbers of size l x l-1

w=rnorm(layersDimensions\[l\]\*layersDimensions\[l-1\])\*0.01

\# Create a weight matrix of size l x l-1 with this initial weights and

\# Add to list W1,W2... WL

layerParams\[\[paste('W',l-1,sep="")\]\] = matrix(w,nrow=layersDimensions\[l\],

 ncol=layersDimensions\[l-1\]) layerParams\[\[paste('b',l-1,sep="")\]\] = matrix(rep(0,layersDimensions\[l\]), nrow=layersDimensions\[l\],ncol=1)

}

return(layerParams)

}

\# He Initialization model for L layers

\# Input : Vector of units in each layer

\# Returns: Initial weights and biases matrices for all layers

\# He initilization multiplies the random numbers with

sqrt(2/layerDimensions\[previouslayer\])

HeInitializeDeepModel <- function(layerDimensions){

set.seed(2)

\# Initialize empty list

layerParams <- list()

\# Note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Indices in R start from 1

for(l in 2:length(layersDimensions)){

\# Initialize a matrix of small random numbers of size l x l-1

\# Create random numbers of size l x l-1

w=rnorm(layersDimensions\[l\]\*layersDimensions\[l-1\])

\# Create a weight matrix of size l x l-1 with this initial weights and

\# Add to list W1,W2... WL

\# He initialization - Divide by sqrt(2/layerDimensions\[previous layer\]) layerParams\[\[paste('W',l-1,sep="")\]\] =

matrix(w,nrow=layersDimensions\[l\],

ncol=layersDimensions\[l-

1\])\*sqrt(2/layersDimensions\[l-1\])

layerParams\[\[paste('b',l-1,sep="")\]\] = matrix(rep(0,layersDimensions\[l\]), nrow=layersDimensions\[l\],ncol=1)

}

return(layerParams)

}

\# XavInitializeDeepModel Initialization model for L layers

\# Input : Vrctor of units in each layer

\# Returns: Initial weights and biases matrices for all layers

\# He initilization multiplies the random numbers with

sqrt(1/layerDimensions\[previouslayer\])

XavInitializeDeepModel <- function(layerDimensions){

set.seed(2)

\# Initialize empty list

layerParams <- list()

\# Note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Indices in R start from 1

for(l in 2:length(layersDimensions)){

\# Initialize a matrix of small random numbers of size l x l-1

\# Create random numbers of size l x l-1

w=rnorm(layersDimensions\[l\]\*layersDimensions\[l-1\])

\# Create a weight matrix of size l x l-1 with this initial weights and

\# Add to list W1,W2... WL

\# He initialization - Divide by sqrt(2/layerDimensions\[previous layer\]) layerParams\[\[paste('W',l-1,sep="")\]\] =

matrix(w,nrow=layersDimensions\[l\],

ncol=layersDimensions\[l-

1\])\*sqrt(1/layersDimensions\[l-1\])

layerParams\[\[paste('b',l-1,sep="")\]\] = matrix(rep(0,layersDimensions\[l\]), nrow=layersDimensions\[l\],ncol=1)

}

return(layerParams)

}

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prev - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : The Activation of this layer

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

layerActivationForward <- function(A\_prev, W, b, activationFunc){

\# Compute Z

z = W %\*% A\_prev

\# Broadcast the bias 'b' by column

Z <-sweep(z,1,b,'+')

forward\_cache <- list("A\_prev"=A\_prev, "W"=W, "b"=b)

\# Compute the activation for sigmoid

if(activationFunc == "sigmoid"){

vals = sigmoid(Z)

} else if (activationFunc == "relu"){ # Compute the activation for relu vals = relu(Z)

} else if(activationFunc == 'tanh'){ # Compute the activation for tanh vals = tanhActivation(Z)

} else if(activationFunc == 'softmax'){

vals = softmax(Z)

}

\# Create a list of forward and activation cache

cache <- list("forward\_cache"=forward\_cache, "activation\_cache"=vals\[\['Z'\]\]) retvals <- list("A"=vals\[\['A'\]\],"cache"=cache) return(retvals)

}

\# Compute the forward propagation for layers 1..L

\# Input : X - Input Features

\# parameters: Weights and biases

\# keep\_prob

\# hiddenActivationFunc - relu/sigmoid/tanh

\# outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# Returns : AL

\# caches

\# dropoutMat

\# The forward propoagtion uses the Relu/tanh activation from layer 1..L-1 and sigmoid actiovation at layer L

forwardPropagationDeep <- function(X, parameters,keep\_prob=1, hiddenActivationFunc='relu',

outputActivationFunc='sigmoid'){

caches <- list()

dropoutMat <- list()

\# Set A to X (A0)

A <- X

L <- length(parameters)/2 # number of layers in the neural network

\# Loop through from layer 1 to upto layer L

for(l in 1:(L-1)){

A\_prev <- A

\# Zi = Wi x Ai-1 + bi and Ai = g(Zi)

\# Set W and b for layer 'l'

\# Loop throug from W1,W2... WL-1

W <- parameters\[\[paste("W",l,sep="")\]\]

b <- parameters\[\[paste("b",l,sep="")\]\]

\# Compute the forward propagation through layer 'l' using the activation function

actForward <- layerActivationForward(A\_prev,

W,

b,

activationFunc = hiddenActivationFunc)

A <- actForward\[\['A'\]\]

\# Append the cache A\_prev,W,b, Z

caches\[\[l\]\] <-actForward

\# Randomly drop some activation units

\# Create a matrix as the same shape as A

set.seed(1)

i=dim(A)\[1\]

j=dim(A)\[2\]

a<-rnorm(i\*j)

\# Normalize a between 0 and 1

a = (a - min(a))/(max(a) - min(a))

\# Create a matrix of D

 D <- matrix(a,nrow=i, ncol=j)

\# Find D which is less than equal to keep\_prob

D <- D < keep\_prob

\# Remove some A's

A <- A \* D

\# Divide by keep\_prob to keep expected value same

A <- A/keep\_prob

dropoutMat\[\[paste("D",l,sep="")\]\] <- D

}

\# Since this is binary classification use the sigmoid activation function in

\# last layer

\# Set the weights and biases for the last layer

W <- parameters\[\[paste("W",L,sep="")\]\]

b <- parameters\[\[paste("b",L,sep="")\]\]

\# Compute the sigmoid activation

actForward = layerActivationForward(A, W, b, activationFunc =

outputActivationFunc)

AL <- actForward\[\['A'\]\]

\# Append the output of this forward propagation through the last layer caches\[\[L\]\] <- actForward

\# Create a list of the final output and the caches

fwdPropDeep <- list("AL"=AL,"caches"=caches,"dropoutMat"=dropoutMat) return(fwdPropDeep)

}

\# Function pickColumns(). This function is in computeCost()

\# Pick columns

\# Input : AL

\# : Y

\# : numClasses

\# Output: a

pickColumns <- function(AL,Y,numClasses){

if(numClasses==3){

a=c(AL\[Y==0,1\],AL\[Y==1,2\],AL\[Y==2,3\])

}

else if (numClasses==10){

a=c(AL\[Y==0,1\],AL\[Y==1,2\],AL\[Y==2,3\],AL\[Y==3,4\],AL\[Y==4,5\],

 AL\[Y==5,6\],AL\[Y==6,7\],AL\[Y==7,8\],AL\[Y==8,9\],AL\[Y==9,10\])

}

return(a)

}

\# Compute the cost

\# Input : AL-Activation of last layer

\# : Y-Output from data

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : numClasses

\# Output: cost

computeCost <-

function(AL,Y,outputActivationFunc="sigmoid",numClasses=3){

if(outputActivationFunc=="sigmoid"){

m= length(Y)

cost=-1/m\*sum(Y\*log(AL) + (1-Y)\*log(1-AL))

}else if (outputActivationFunc=="softmax"){

\# Select the elements where the y values are 0, 1 or 2 and make a vector

\# Pick columns

#a=c(AL\[Y==0,1\],AL\[Y==1,2\],AL\[Y==2,3\])

m= length(Y)

a =pickColumns(AL,Y,numClasses)

#a = c(A2\[y=k,k+1\])

\# Take log

correct\_probs = -log(a)

\# Compute loss

cost= sum(correct\_probs)/m

}

#cost=-1/m\*sum(a+b)

return(cost)

}

\# Compute the cost with Regularization

\# Input : parameters

\# : AL-Activation of last layer

\# : Y-Output from data

\# : lambd

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : numClasses

\# Output: cost

computeCostWithReg <- function(parameters, AL,Y,lambd,

outputActivationFunc="sigmoid",numClasses=3){

if(outputActivationFunc=="sigmoid"){

m= length(Y)

cost=-1/m\*sum(Y\*log(AL) + (1-Y)\*log(1-AL))

\# Regularization cost

L <- length(parameters)/2

L2RegularizationCost=0

for(l in 1:L){

L2RegularizationCost = L2RegularizationCost +

sum(parameters\[\[paste("W",l,sep="")\]\]^2)

}

L2RegularizationCost = (lambd/(2\*m))\*L2RegularizationCost

cost = cost + L2RegularizationCost

}else if (outputActivationFunc=="softmax"){

\# Select the elements where the y values are 0, 1 or 2 and make a vector

\# Pick columns

#a=c(AL\[Y==0,1\],AL\[Y==1,2\],AL\[Y==2,3\])

m= length(Y)

a =pickColumns(AL,Y,numClasses)

#a = c(A2\[y=k,k+1\])

\# Take log

correct\_probs = -log(a)

\# Compute loss

cost= sum(correct\_probs)/m

\# Regularization cost

L <- length(parameters)/2

L2RegularizationCost=0

 # Add L2 norm

for(l in 1:L){

L2RegularizationCost = L2RegularizationCost +

sum(parameters\[\[paste("W",l,sep="")\]\]^2)

}

L2RegularizationCost = (lambd/(2\*m))\*L2RegularizationCost

cost = cost + L2RegularizationCost

}

return(cost)

}

\# Compute the backpropagation through a layer

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# # Output values Y

\# # activationFunc

\# # numClasses

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

layerActivationBackward <- function(dA, cache, Y, activationFunc,numClasses)

{

\# Get A\_prev,W,b

forward\_cache <-cache\[\['forward\_cache'\]\]

activation\_cache <- cache\[\['activation\_cache'\]\]

A\_prev <- forward\_cache\[\['A\_prev'\]\]

numtraining = dim(A\_prev)\[2\]

\# Get Z

activation\_cache <- cache\[\['activation\_cache'\]\]

if(activationFunc == "relu"){

dZ <- reluDerivative(dA, activation\_cache)

} else if(activationFunc == "sigmoid"){

dZ <- sigmoidDerivative(dA, activation\_cache)

} else if(activationFunc == "tanh"){

dZ <- tanhDerivative(dA, activation\_cache)

} else if(activationFunc == "softmax"){

dZ <- softmaxDerivative(dA, activation\_cache,Y,numtraining,numClasses)

 }

if (activationFunc == 'softmax'){

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

dW = 1/numtraining \* A\_prev%\*%dZ

db = 1/numtraining\* matrix(colSums(dZ),nrow=1,ncol=numClasses) dA\_prev = dZ %\*%W

} else {

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

numtraining = dim(A\_prev)\[2\]

dW = 1/numtraining \* dZ %\*% t(A\_prev)

db = 1/numtraining \* rowSums(dZ)

dA\_prev = t(W) %\*% dZ

}

retvals <- list("dA\_prev"=dA\_prev,"dW"=dW,"db"=db) return(retvals)

}

\# Compute the backpropagation through a layer with Regularization

\# Input : dA-Neural Network parameters

\# # cache - forward\_cache & activation\_cache

\# # Output values Y

\# # lambd

\# # activationFunc

\# # numClasses

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

layerActivationBackwardWithReg <- function(dA, cache, Y, lambd, activationFunc,numClasses){

\# Get A\_prev,W,b

forward\_cache <-cache\[\['forward\_cache'\]\]

activation\_cache <- cache\[\['activation\_cache'\]\]

A\_prev <- forward\_cache\[\['A\_prev'\]\]

numtraining = dim(A\_prev)\[2\]

 # Get Z

activation\_cache <- cache\[\['activation\_cache'\]\]

if(activationFunc == "relu"){

dZ <- reluDerivative(dA, activation\_cache)

} else if(activationFunc == "sigmoid"){

dZ <- sigmoidDerivative(dA, activation\_cache)

} else if(activationFunc == "tanh"){

dZ <- tanhDerivative(dA, activation\_cache)

} else if(activationFunc == "softmax"){

dZ <- softmaxDerivative(dA, activation\_cache,Y,numtraining,numClasses)

}

if (activationFunc == 'softmax'){

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

\# Add the regularization factor

dW = 1/numtraining \* A\_prev%\*%dZ + (lambd/numtraining) \* t(W) db = 1/numtraining\* matrix(colSums(dZ),nrow=1,ncol=numClasses) dA\_prev = dZ %\*%W

} else {

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

numtraining = dim(A\_prev)\[2\]

\# Add the regularization factor

dW = 1/numtraining \* dZ %\*% t(A\_prev) + (lambd/numtraining) \* W

db = 1/numtraining \* rowSums(dZ)

dA\_prev = t(W) %\*% dZ

}

retvals <- list("dA\_prev"=dA\_prev,"dW"=dW,"db"=db) return(retvals)

}

\# Compute the backpropagation for 1 cycle through all layers

\# Input : AL: Output of L layer Network - weights

\# Y Real output

\# caches -- list of caches containing:

\# every cache of layerActivationForward() with "relu"/"tanh"

\# #(it's caches\[l\], for l in range(L-1) i.e l = 0...L-2)

\# #the cache of layerActivationForward() with "sigmoid" (it's caches\[L-1\])

\# dropoutMat

\# lambd

\# keep\_prob

\# hiddenActivationFunc - Activation function at hidden layers -

relu/tanh/sigmoid

\# outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# numClasses

\# Returns:

\# gradients -- A dictionary with the gradients

\# gradients\["dA" + str(l)\]

\# gradients\["dW" + str(l)\]

\# gradients\["db" + str(l)\]

backwardPropagationDeep <- function(AL, Y, caches,dropoutMat, lambd=0, keep\_prob=0, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",numClasses){

#initialize the gradients

gradients = list()

\# Set the number of layers

L = length(caches)

numTraining = dim(AL)\[2\]

if(outputActivationFunc == "sigmoid")

\# Initializing the backpropagation

\# dl/dAL= -(y/a) - ((1-y)/(1-a)) - At the output layer

dAL = -( (Y/AL) -(1 - Y)/(1 - AL))

else if(outputActivationFunc == "softmax"){

dAL=0

Y=t(Y)

}

\# Get the gradients at the last layer

\# Inputs: "AL, Y, caches".

\# Outputs: "gradients\["dAL"\], gradients\["dWL"\], gradients\["dbL"\]

\# Start with Layer L

\# Get the current cache

current\_cache = caches\[\[L\]\]$cache

if (lambd==0){

retvals <- layerActivationBackward(dAL, current\_cache, Y,

 activationFunc = outputActivationFunc,numClasses)

} else {

retvals = layerActivationBackwardWithReg(dAL, current\_cache, Y, lambd, activationFunc = outputActivationFunc,numClasses)

}

#Note: Take the transpose of dA

if(outputActivationFunc =="sigmoid")

gradients\[\[paste("dA",L,sep="")\]\] <- retvals\[\['dA\_prev'\]\]

else if(outputActivationFunc =="softmax")

gradients\[\[paste("dA",L,sep="")\]\] <- t(retvals\[\['dA\_prev'\]\]) gradients\[\[paste("dW",L,sep="")\]\] <- retvals\[\['dW'\]\]

gradients\[\[paste("db",L,sep="")\]\] <- retvals\[\['db'\]\]

\# Traverse in the reverse direction

for(l in (L-1):1){

\# Compute the gradients for L-1 to 1 for Relu/tanh

\# Inputs: "gradients\["dA" + str(l + 2)\], caches".

\# Outputs: "gradients\["dA" + str(l + 1)\] , gradients\["dW" + str(l + 1)\] , gradients\["db" + str(l + 1)\]

current\_cache = caches\[\[l\]\]$cache

if (lambd==0){

\# Get the dropout matrix

D <-dropoutMat\[\[paste("D",l,sep="")\]\]

\# Multiply gradient with dropout matrix

gradients\[\[paste('dA',l+1,sep="")\]\] = gradients\[\[paste('dA',l+1,sep="")\]\] \*D

\# Divide by keep\_prob to keep expected value same

gradients\[\[paste('dA',l+1,sep="")\]\] =

gradients\[\[paste('dA',l+1,sep="")\]\]/keep\_prob

retvals = layerActivationBackward(gradients\[\[paste('dA',l+1,sep="")\]\], current\_cache, Y,

activationFunc = hiddenActivationFunc)

} else {

retvals =

layerActivationBackwardWithReg(gradients\[\[paste('dA',l+1,sep="")\]\], current\_cache, Y, lambd,

activationFunc = hiddenActivationFunc)

 }

gradients\[\[paste("dA",l,sep="")\]\] <-retvals\[\['dA\_prev'\]\]

gradients\[\[paste("dW",l,sep="")\]\] <- retvals\[\['dW'\]\]

gradients\[\[paste("db",l,sep="")\]\] <- retvals\[\['db'\]\]

}

return(gradients)

}

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients

\# : learning rate

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

#output : Updated weights after 1 iteration

gradientDescent <- function(parameters, gradients,

learningRate,outputActivationFunc="sigmoid"){

L = length(parameters)/2 # number of layers in the neural network

\# Update rule for each parameter. Use a for loop.

for(l in 1:(L-1)){

parameters\[\[paste("W",l,sep="")\]\] = parameters\[\[paste("W",l,sep="")\]\] -

learningRate\* gradients\[\[paste("dW",l,sep="")\]\]

parameters\[\[paste("b",l,sep="")\]\] = parameters\[\[paste("b",l,sep="")\]\] -

learningRate\* gradients\[\[paste("db",l,sep="")\]\]

}

if(outputActivationFunc=="sigmoid"){

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* gradients\[\[paste("dW",L,sep="")\]\]

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* gradients\[\[paste("db",L,sep="")\]\]

}else if (outputActivationFunc=="softmax"){

 parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* t(gradients\[\[paste("dW",L,sep="")\]\]) parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* t(gradients\[\[paste("db",L,sep="")\]\])

}

return(parameters)

}

\# Execute a L layer Deep learning model

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu /tanh

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : learning rate

\# : lambd

\# : keep\_prob

\# : learning rate

\# : num of iterations

\# : initType

#output : Updated weights

L\_Layer\_DeepModel <- function(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc= 'sigmoid',

learningRate = 0.5,

lambd=0,

keep\_prob=1,

numIterations = 10000,

initType="default",

print\_cost=False){

#Initialize costs vector as NULL

costs <- NULL

\# Parameters initialization.

if (initType=="He"){

parameters =HeInitializeDeepModel(layersDimensions)

} else if (initType=="Xav"){

 parameters =XavInitializeDeepModel(layersDimensions)

}

else{

print("Here")

parameters = initializeDeepModel(layersDimensions)

}

\# Loop (gradient descent)

for( i in 0:numIterations){

\# Forward propagation: \[LINEAR -> RELU\]\*(L-1) -> LINEAR -> SIGMOID/SOFTMAX.

retvals = forwardPropagationDeep(X, parameters,keep\_prob,

hiddenActivationFunc,

outputActivationFunc=outputActivationFunc)

AL <- retvals\[\['AL'\]\]

caches <- retvals\[\['caches'\]\]

dropoutMat <- retvals\[\['dropoutMat'\]\]

\# Compute cost.

if(lambd==0){

cost <- computeCost(AL,

Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

} else {

cost <- computeCostWithReg(parameters, AL, Y,lambd,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

}

\# Backward propagation.

gradients = backwardPropagationDeep(AL, Y, caches, dropoutMat, lambd, keep\_prob, hiddenActivationFunc,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

\# Update parameters.

parameters = gradientDescent(parameters, gradients, learningRate, outputActivationFunc=outputActivationFunc)

if(i%%1000 == 0){

costs=c(costs,cost)

 print(cost)

}

}

retvals <- list("parameters"=parameters,"costs"=costs) return(retvals)

}

\# Execute a L layer Deep learning model with Stochastic Gradient descent

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu /tanh

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : learning rate

\# : mini\_batch\_size

\# : num of epochs

#output : Updated weights after each iteration

L\_Layer\_DeepModel\_SGD <- function(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc= 'sigmoid',

learningRate = .3,

mini\_batch\_size = 64,

num\_epochs = 2500,

print\_cost=False){

set.seed(1)

#Initialize costs vector as NULL

costs <- NULL

\# Parameters initialization.

parameters = initializeDeepModel(layersDimensions)

seed=10

\# Loop for number of epochs

for( i in 0:num\_epochs){

seed=seed+1

 minibatches = random\_mini\_batches(X, Y, mini\_batch\_size, seed) for(batch in 1:length(minibatches)){

mini\_batch\_X=minibatches\[\[batch\]\]\[\['mini\_batch\_X'\]\]

mini\_batch\_Y=minibatches\[\[batch\]\]\[\['mini\_batch\_Y'\]\]

\# Forward propagation:

retvals = forwardPropagationDeep(mini\_batch\_X,

parameters,hiddenActivationFunc,

outputActivationFunc=outputActivationFunc)

AL <- retvals\[\['AL'\]\]

caches <- retvals\[\['caches'\]\]

\# Compute cost.

cost <- computeCost(AL,

mini\_batch\_Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

\# Backward propagation.

gradients = backwardPropagationDeep(AL, mini\_batch\_Y,

caches,hiddenActivationFunc,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

\# Update parameters.

parameters = gradientDescent(parameters, gradients, learningRate, outputActivationFunc=outputActivationFunc)

}

if(i%%100 == 0){

costs=c(costs,cost)

print(cost)

}

}

retvals <- list("parameters"=parameters,"costs"=costs) return(retvals)

}

\# Predict the output for given input

\# Input : parameters

\# : X

\# Output: predictions

predict <- function(parameters, X,keep\_prob=1, hiddenActivationFunc='relu'){

fwdProp <- forwardPropagationDeep(X, parameters,keep\_prob, hiddenActivationFunc)

predictions <- fwdProp$AL>0.5

return (predictions)

}

\# Plot a decision boundary

\# This function uses ggplot2

plotDecisionBoundary <-

function(z,retvals,keep\_prob=1,hiddenActivationFunc="sigmoid",lr=0.5){

\# Find the minimum and maximum for the data

xmin<-min(z\[,1\])

xmax<-max(z\[,1\])

ymin<-min(z\[,2\])

ymax<-max(z\[,2\])

\# Create a grid of values

a=seq(xmin,xmax,length=100)

b=seq(ymin,ymax,length=100)

grid <- expand.grid(x=a, y=b)

colnames(grid) <- c('x1', 'x2')

grid1 <-t(grid)

\# Predict the output for this grid

q <-predict(retvals$parameters,grid1,keep\_prob=1, hiddenActivationFunc) q1 <- t(data.frame(q))

q2 <- as.numeric(q1)

grid2 <- cbind(grid,q2)

colnames(grid2) <- c('x1', 'x2','q2')

z1 <- data.frame(z)

names(z1) <- c("x1","x2","y") atitle=paste("Decision boundary for learning rate:",lr)

 # Plot the contour of the boundary

ggplot(z1) +

geom\_point(data = z1, aes(x = x1, y = x2, color = y)) +

stat\_contour(data = grid2, aes(x = x1, y = x2, z = q2,color=q2), alpha = 0.9)+

ggtitle(atitle) + scale\_colour\_gradientn(colours = brewer.pal(10, "Spectral"))

}

\# Predict the probability scores for given data set

\# Input : parameters

\# : X

\# Output: probability of output

computeScores <- function(parameters, X,hiddenActivationFunc='relu'){

fwdProp <- forwardPropagationDeep(X, parameters,hiddenActivationFunc) scores <- fwdProp$AL

return (scores)

}

\# Create random mini batches

\# Input : X - Input features

\# : Y- output

\# : miniBatchSize

\# : seed

#output : mini\_batches

random\_mini\_batches <- function(X, Y, miniBatchSize = 64, seed = 0){

set.seed(seed)

\# Get number of training samples

m = dim(X)\[2\]

\# Initialize mini batches

mini\_batches = list()

\# Create a list of random numbers < m

permutation = c(sample(m))

\# Randomly shuffle the training data

shuffled\_X = X\[, permutation\]

shuffled\_Y = Y\[1, permutation\]

 # Compute number of mini batches

numCompleteMinibatches = floor(m/miniBatchSize)

batch=0

for(k in 0:(numCompleteMinibatches-1)){

batch=batch+1

\# Set the lower and upper bound of the mini batches

lower=(k\*miniBatchSize)+1

upper=((k+1) \* miniBatchSize)

mini\_batch\_X = shuffled\_X\[, lower:upper\]

mini\_batch\_Y = shuffled\_Y\[lower:upper\]

\# Add it to the list of mini batches

mini\_batch =

list("mini\_batch\_X"=mini\_batch\_X,"mini\_batch\_Y"=mini\_batch\_Y) mini\_batches\[\[batch\]\] =mini\_batch

}

\# If the batch size does not divide evenly with mini batc size if(m %% miniBatchSize != 0){

p=floor(m/miniBatchSize)\*miniBatchSize

\# Set the start and end of last batch

q=p+m %% miniBatchSize

mini\_batch\_X = shuffled\_X\[,(p+1):q\]

mini\_batch\_Y = shuffled\_Y\[(p+1):q\]

}

\# Return the list of mini batches

mini\_batch =

list("mini\_batch\_X"=mini\_batch\_X,"mini\_batch\_Y"=mini\_batch\_Y) mini\_batches\[\[batch\]\]=mini\_batch

return(mini\_batches)

}

\# Plot a decision boundary

\# This function uses ggplot2

plotDecisionBoundary1 <- function(Z,parameters,keep\_prob=1){

xmin<-min(Z\[,1\])

xmax<-max(Z\[,1\])

ymin<-min(Z\[,2\])

 ymax<-max(Z\[,2\])

\# Create a grid of points

a=seq(xmin,xmax,length=100)

b=seq(ymin,ymax,length=100)

grid <- expand.grid(x=a, y=b)

colnames(grid) <- c('x1', 'x2')

grid1 <-t(grid)

retvals = forwardPropagationDeep(grid1, parameters,keep\_prob, "relu", outputActivationFunc="softmax")

AL <- retvals$AL

\# From the softmax probabilities pick the one with the highest probability q= apply(AL,1,which.max)

q1 <- t(data.frame(q))

q2 <- as.numeric(q1)

grid2 <- cbind(grid,q2)

colnames(grid2) <- c('x1', 'x2','q2')

Z1 <- data.frame(Z)

names(Z1) <- c("x1","x2","y") atitle=paste("Decision boundary")

ggplot(Z1) +

geom\_point(data = Z1, aes(x = x1, y = x2, color = y)) +

stat\_contour(data = grid2, aes(x = x1, y = x2, z = q2,color=q2), alpha =

0.9)+

ggtitle(atitle) + scale\_colour\_gradientn(colours = brewer.pal(10,

"Spectral"))

}

**6.3 Octave**

############################################################################################################

#

\# File : DLfunctions61.m

\# Author : Tinniam V Ganesh

\# Date : 16 Apr 2018

#

##########################################################################################################

1;

\# Define sigmoid function

function \[A,cache\] = sigmoid(Z)

A = 1 ./ (1+ exp(-Z));

cache=Z;

end

\# Define Relu function

function \[A,cache\] = relu(Z)

A = max(0,Z);

cache=Z;

end

\# Define Relu function

function \[A,cache\] = tanhAct(Z)

A = tanh(Z);

cache=Z;

end

\# Define Softmax function

function \[A,cache\] = softmax(Z)

\# get unnormalized probabilities

exp\_scores = exp(Z');

\# normalize them for each example

A = exp\_scores ./ sum(exp\_scores,2);

cache=Z;

end

\# Define Stable Softmax function

function \[A,cache\] = stableSoftmax(Z)

\# Normalize by max value in each row

shiftZ = Z' - max(Z',\[\],2);

exp\_scores = exp(shiftZ);

\# normalize them for each example

A = exp\_scores ./ sum(exp\_scores,2);

#disp("sm")

#disp(A);

cache=Z;

end

\# Define Relu Derivative

function \[dZ\] = reluDerivative(dA,cache)

Z = cache;

dZ = dA;

\# Get elements that are greater than 0

a = (Z > 0);

\# Select only those elements where Z > 0

dZ = dZ .\* a;

end

\# Define Sigmoid Derivative

function \[dZ\] = sigmoidDerivative(dA,cache)

Z = cache;

s = 1 ./ (1+ exp(-Z));

dZ = dA .\* s .\* (1-s);

end

\# Define Tanh Derivative

function \[dZ\] = tanhDerivative(dA,cache)

Z = cache;

a = tanh(Z);

dZ = dA .\* (1 - a .^ 2);

end

\# Populate a matrix with 1s in rows where Y=1

\# This function may need to be modified if K is not 3, 10

\# This function is used in computing the softmax derivative

function \[Y1\] = popMatrix(Y,numClasses)

Y1=zeros(length(Y),numClasses);

if(numClasses==3) # For 3 output classes

Y1(Y==0,1)=1;

Y1(Y==1,2)=1;

Y1(Y==2,3)=1;

elseif(numClasses==10) # For 10 output classes

Y1(Y==0,1)=1;

Y1(Y==1,2)=1;

Y1(Y==2,3)=1;

Y1(Y==3,4)=1;

Y1(Y==4,5)=1;

Y1(Y==5,6)=1;

Y1(Y==6,7)=1;

Y1(Y==7,8)=1;

Y1(Y==8,9)=1;

Y1(Y==9,10)=1;

endif

end

\# Define Softmax Derivative

function \[dZ\] = softmaxDerivative(dA,cache,Y, numClasses)

Z = cache;

\# get unnormalized probabilities

shiftZ = Z' - max(Z',\[\],2);

exp\_scores = exp(shiftZ);

\# normalize them for each example

probs = exp\_scores ./ sum(exp\_scores,2);

\# dZ = pi- yi

yi=popMatrix(Y,numClasses);

dZ=probs-yi;

end

\# Define Stable Softmax Derivative

function \[dZ\] = stableSoftmaxDerivative(dA,cache,Y, numClasses) Z = cache;

 # get unnormalized probabilities

exp\_scores = exp(Z');

\# normalize them for each example

probs = exp\_scores ./ sum(exp\_scores,2);

\# dZ = pi- yi

yi=popMatrix(Y,numClasses);

dZ=probs-yi;

end

\# Initialize model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers function \[W b\] = initializeDeepModel(layerDimensions)

rand ("seed", 3);

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Create cell arrays for Weights and biases

for l =2:size(layerDimensions)(2)

W{l-1} = rand(layerDimensions(l),layerDimensions(l-1))\*0.01; #

Multiply by .01

b{l-1} = zeros(layerDimensions(l),1);

endfor

end

\# He Initialization for L layers

\# Input : vector of units in each layer

\# Returns: Initial weights and biases matrices for all layers function \[W b\] = HeInitializeDeepModel(layerDimensions)

rand ("seed", 3);

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Create cell arrays for Weights and biases

for l =2:size(layerDimensions)(2)

W{l-1} = rand(layerDimensions(l),layerDimensions(l-1))\*

sqrt(2/layerDimensions(l-1)); # Multiply by .01

b{l-1} = zeros(layerDimensions(l),1);

endfor

end

\# Xavier Initialization for L layers

\# Input : vector of units in each layer

\# Returns: Initial weights and biases matrices for all layers function \[W b\] = XavInitializeDeepModel(layerDimensions)

rand ("seed", 3);

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Create cell arrays for Weights and biases

for l =2:size(layerDimensions)(2)

W{l-1} = rand(layerDimensions(l),layerDimensions(l-1))\*

sqrt(1/layerDimensions(l-1)); # Multiply by .01

b{l-1} = zeros(layerDimensions(l),1);

endfor

end

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prev - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : The Activation of this layer

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

function \[A forward\_cache activation\_cache\] = layerActivationForward(A\_prev, W, b, activationFunc)

\# Compute Z

Z = W \* A\_prev +b;

\# Create a cell array

forward\_cache = {A\_prev W b};

\# Compute the activation for sigmoid

if (strcmp(activationFunc,"sigmoid"))

\[A activation\_cache\] = sigmoid(Z);

elseif (strcmp(activationFunc, "relu")) # Compute the activation for Relu

\[A activation\_cache\] = relu(Z);

elseif(strcmp(activationFunc,'tanh')) # Compute the activation for tanh

\[A activation\_cache\] = tanhAct(Z);

elseif(strcmp(activationFunc,'softmax')) # Compute the activation for tanh

#\[A activation\_cache\] = softmax(Z);

\[A activation\_cache\] = stableSoftmax(Z);

endif

end

\# Compute the forward propagation for layers 1..L

\# Input : X - Input Features

\# paramaters: Weights and biases

\# keep\_prob

\# hiddenActivationFunc - Activation function at hidden layers Relu/tanh/sigmoid

\# outputActivationFunc- sigmoid/softmax

\# Returns : AL

\# caches

\# The forward propoagtion uses the Relu/tanh activation from layer 1..L-1 and sigmoid actiovation at layer L

function \[AL forward\_caches activation\_caches dropoutMat\] =

forwardPropagationDeep(X, weights,biases, keep\_prob=1,

hiddenActivationFunc='relu',

outputActivationFunc='sigmoid')

\# Create an empty cell array

forward\_caches = {};

activation\_caches = {};

droputMat ={};

\# Set A to X (A0)

 A = X;

L = length(weights); # number of layers in the neural network

\# Loop through from layer 1 to upto layer L

for l =1:L-1

A\_prev = A;

\# Zi = Wi x Ai-1 + bi and Ai = g(Zi)

W = weights{l};

b = biases{l};

\[A forward\_cache activation\_cache\] = layerActivationForward(A\_prev, W,b, activationFunc=hiddenActivationFunc);

D=rand(size(A)(1),size(A)(2));

D = (D < keep\_prob) ;

\# Multiply by DropoutMat

A= A .\* D;

\# Divide by keep\_prob to keep expected value same

A = A ./ keep\_prob;

\# Store D

dropoutMat{l}=D;

forward\_caches{l}=forward\_cache;

activation\_caches{l} = activation\_cache;

endfor

\# Since this is binary classification use the sigmoid activation function in

\# last layer

W = weights{L};

b = biases{L};

\[AL, forward\_cache activation\_cache\] = layerActivationForward(A, W,b, activationFunc = outputActivationFunc);

forward\_caches{L}=forward\_cache;

activation\_caches{L} = activation\_cache;

end

\# Pick columns where Y==1

\# This function is used in computeCost

function \[a\] = pickColumns(AL,Y,numClasses)

if(numClasses==3)

a=\[AL(Y==0,1) ;AL(Y==1,2) ;AL(Y==2,3)\];

elseif (numClasses==10)

a=\[AL(Y==0,1) ;AL(Y==1,2) ;AL(Y==2,3);AL(Y==3,4);AL(Y==4,5);

 AL(Y==5,6); AL(Y==6,7);AL(Y==7,8);AL(Y==8,9);AL(Y==9,10)\]; endif

end

\# Compute the cost

\# Input : Activation of last layer

\# : Output from data

\# : outputActivationFunc- sigmoid/softmax

\# : numClasses

\# Output: cost

function \[cost\]= computeCost(AL, Y,

outputActivationFunc="sigmoid",numClasses)

if(strcmp(outputActivationFunc,"sigmoid"))

numTraining= size(Y)(2);

\# Element wise multiply for logprobs

cost = -1/numTraining \* sum((Y .\* log(AL)) + (1-Y) .\* log(1-AL)); elseif(strcmp(outputActivationFunc,'softmax'))

numTraining = size(Y)(2);

Y=Y';

\# Select rows where Y=0,1,and 2 and concatenate to a long vector

#a=\[AL(Y==0,1) ;AL(Y==1,2) ;AL(Y==2,3)\];

a =pickColumns(AL,Y,numClasses);

#Select the correct column for log prob

correct\_probs = -log(a);

#Compute log loss

cost= sum(correct\_probs)/numTraining;

endif

end

\# Compute the cost with regularization

\# Input : weights

\# : AL - Activation of last layer

\# : Output from data

\# : lambd

\# : outputActivationFunc- sigmoid/softmax

\# : numClasses

\# Output: cost

function \[cost\]= computeCostWithReg(weights, AL, Y, lambd,

outputActivationFunc="sigmoid",numClasses)

if(strcmp(outputActivationFunc,"sigmoid"))

numTraining= size(Y)(2);

\# Element wise multiply for logprobs

cost = -1/numTraining \* sum((Y .\* log(AL)) + (1-Y) .\* log(1-AL));

\# Regularization cost

L = size(weights)(2);

L2RegularizationCost=0;

for l=1:L

wtSqr = weights{l} .\* weights{l};

#disp(sum(sum(wtSqr,1)));

L2RegularizationCost+=sum(sum(wtSqr,1));

endfor

L2RegularizationCost = (lambd/(2\*numTraining))\*L2RegularizationCost; cost = cost + L2RegularizationCost ;

elseif(strcmp(outputActivationFunc,'softmax'))

numTraining = size(Y)(2);

Y=Y';

\# Select rows where Y=0,1,and 2 and concatenate to a long vector

#a=\[AL(Y==0,1) ;AL(Y==1,2) ;AL(Y==2,3)\];

a =pickColumns(AL,Y,numClasses);

#Select the correct column for log prob

correct\_probs = -log(a);

#Compute log loss

cost= sum(correct\_probs)/numTraining;

\# Regularization cost

L = size(weights)(2);

L2RegularizationCost=0;

for l=1:L

\# Compute L2 Norm

wtSqr = weights{l} .\* weights{l};

#disp(sum(sum(wtSqr,1)));

L2RegularizationCost+=sum(sum(wtSqr,1));

endfor

 L2RegularizationCost = (lambd/(2\*numTraining))\*L2RegularizationCost; cost = cost + L2RegularizationCost ;

endif

end

\# Compute the backpropoagation for 1 cycle

\# Input : dA- Neural Network parameters

\# # cache - forward\_cache & activation\_cache

\# # Y-Output values

\# # outputActivationFunc- sigmoid/softmax

\# # numClasses

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

function \[dA\_prev dW db\] = layerActivationBackward(dA, forward\_cache, activation\_cache, Y, activationFunc,numClasses)

A\_prev = forward\_cache{1};

W =forward\_cache{2};

b = forward\_cache{3};

numTraining = size(A\_prev)(2);

if (strcmp(activationFunc,"relu"))

dZ = reluDerivative(dA, activation\_cache);

elseif (strcmp(activationFunc,"sigmoid"))

dZ = sigmoidDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "tanh"))

dZ = tanhDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "softmax"))

#dZ = softmaxDerivative(dA, activation\_cache,Y,numClasses);

dZ = stableSoftmaxDerivative(dA, activation\_cache,Y,numClasses); endif

if (strcmp(activationFunc,"softmax"))

W =forward\_cache{2};

b = forward\_cache{3};

\# Add the regularization factor

dW = 1/numTraining \* A\_prev \* dZ;

db = 1/numTraining \* sum(dZ,1);

 dA\_prev = dZ\*W;

else

W =forward\_cache{2};

b = forward\_cache{3};

\# Add the regularization factor

dW = 1/numTraining \* dZ \* A\_prev';

db = 1/numTraining \* sum(dZ,2);

dA\_prev = W'\*dZ;

endif

end

\# Compute the backpropoagation with regularization for 1 cycle

\# Input : dA-Neural Network parameters

\# # cache - forward\_cache & activation\_cache

\# # Y-Output values

\# # lambd

\# # outputActivationFunc- sigmoid/softmax

\# # numClasses

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

function \[dA\_prev dW db\] = layerActivationBackwardWithReg(dA, forward\_cache, activation\_cache, Y, lambd=0, activationFunc,numClasses) A\_prev = forward\_cache{1};

W =forward\_cache{2};

b = forward\_cache{3};

numTraining = size(A\_prev)(2);

if (strcmp(activationFunc,"relu"))

dZ = reluDerivative(dA, activation\_cache);

elseif (strcmp(activationFunc,"sigmoid"))

dZ = sigmoidDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "tanh"))

dZ = tanhDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "softmax"))

#dZ = softmaxDerivative(dA, activation\_cache,Y,numClasses);

dZ = stableSoftmaxDerivative(dA, activation\_cache,Y,numClasses); endif

 if (strcmp(activationFunc,"softmax")) W =forward\_cache{2};

b = forward\_cache{3};

\# Add the regularization factor

dW = 1/numTraining \* A\_prev \* dZ + (lambd/numTraining) \* W'; db = 1/numTraining \* sum(dZ,1);

dA\_prev = dZ\*W;

else

W =forward\_cache{2};

b = forward\_cache{3};

\# Add the regularization factor

dW = 1/numTraining \* dZ \* A\_prev' + (lambd/numTraining) \* W; db = 1/numTraining \* sum(dZ,2);

dA\_prev = W'\*dZ;

endif

end

\# Compute the backpropoagation for 1 cycle

\# Input : AL: Output of L layer Network - weights

\# Y Real output

\# caches -- list of caches containing:

\# every cache of layerActivationForward() with "relu"/"tanh"

\# #(it's caches\[l\], for l in range(L-1) i.e l = 0...L-2)

\# #the cache of layerActivationForward() with "sigmoid" (it's caches\[L-1\])

\# dropoutMat

\# lambd

\# keep\_prob

\# hiddenActivationFunc - Activation function at hidden layers sigmoid/tanh/relu

\# outputActivationFunc- sigmoid/softmax

\# numClasses

#

\# Returns:

\# gradients -- A dictionary with the gradients

\# gradients\["dA" + str(l)\] = ...

\# gradients\["dW" + str(l)\] = ...

function \[gradsDA gradsDW gradsDB\]= backwardPropagationDeep(AL, Y,

activation\_caches,forward\_caches,

dropoutMat, lambd=0, keep\_prob=1,

hiddenActivationFunc='relu',outputActivationFunc="sigmoid",numClasses)

\# Set the number of layers

L = length(activation\_caches);

m = size(AL)(2);

if (strcmp(outputActivationFunc,"sigmoid"))

\# Initializing the backpropagation

\# dl/dAL= -(y/a + (1-y)/(1-a)) - At the output layer

dAL = -((Y ./ AL) - (1 - Y) ./ ( 1 - AL));

elseif (strcmp(outputActivationFunc,"softmax"))

dAL=0;

Y=Y';

endif

\# Since this is a binary classification the activation at output is sigmoid

\# Get the gradients at the last layer

\# Inputs: "AL, Y, caches".

\# Outputs: "gradients\["dAL"\], gradients\["dWL"\], gradients\["dbL"\]

activation\_cache = activation\_caches{L};

forward\_cache = forward\_caches(L);

\# Note the cell array includes an array of forward caches. To get to this we need to include the index {1}

if (lambd==0)

\[dA dW db\] = layerActivationBackward(dAL, forward\_cache{1},

activation\_cache, Y, activationFunc = outputActivationFunc,numClasses); else

\[dA dW db\] = layerActivationBackwardWithReg(dAL, forward\_cache{1}, activation\_cache, Y, lambd, activationFunc =

outputActivationFunc,numClasses);

endif

if (strcmp(outputActivationFunc,"sigmoid"))

gradsDA{L}= dA;

elseif (strcmp(outputActivationFunc,"softmax"))

gradsDA{L}= dA';#Note the transpose

endif

 gradsDW{L}= dW;

gradsDB{L}= db;

\# Traverse in the reverse direction

for l =(L-1):-1:1

\# Compute the gradients for L-1 to 1 for Relu/tanh

\# Inputs: "gradients\["dA" + str(l + 2)\], caches".

\# Outputs: "gradients\["dA" + str(l + 1)\] , gradients\["dW" + str(l + 1)\] , gradients\["db" + str(l + 1)\]

activation\_cache = activation\_caches{l};

forward\_cache = forward\_caches(l);

#dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackward(gradients\['dA'+str(l+1)\], current\_cache, activationFunc = "relu")

\# dAl the dervative of the activation of the lth layer,is the first element dAl= gradsDA{l+1};

if(lambd == 0)

\# Get the dropout mat

D = dropoutMat{l};

#Multiply by the dropoutMat

dAl= dAl .\* D;

\# Divide by keep\_prob to keep expected value same

dAl = dAl ./ keep\_prob;

\[dA\_prev\_temp, dW\_temp, db\_temp\] = layerActivationBackward(dAl, forward\_cache{1}, activation\_cache, Y, activationFunc =

hiddenActivationFunc,numClasses);

else

\[dA\_prev\_temp, dW\_temp, db\_temp\] =

layerActivationBackwardWithReg(dAl, forward\_cache{1}, activation\_cache, Y, lambd, activationFunc = hiddenActivationFunc,numClasses);

endif

gradsDA{l}= dA\_prev\_temp;

gradsDW{l}= dW\_temp;

gradsDB{l}= db\_temp;

endfor

end

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients -gradsW,gradsB

\# : learning rate

\# : outputActivationFunc

#output : Updated weights after 1 iteration

function \[weights biases\] = gradientDescent(weights, biases,gradsW,gradsB, learningRate,outputActivationFunc="sigmoid")

L = size(weights)(2); # number of layers in the neural network

\# Update rule for each parameter.

for l=1:(L-1)

weights{l} = weights{l} -learningRate\* gradsW{l};

biases{l} = biases{l} -learningRate\* gradsB{l};

endfor

if (strcmp(outputActivationFunc,"sigmoid"))

weights{L} = weights{L} -learningRate\* gradsW{L};

biases{L} = biases{L} -learningRate\* gradsB{L};

elseif (strcmp(outputActivationFunc,"softmax"))

weights{L} = weights{L} -learningRate\* gradsW{L}';

biases{L} = biases{L} -learningRate\* gradsB{L}';

endif

end

\# Execute a L layer Deep learning model

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu /tanh

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : learning rate

\# : lambd

\# : keep\_prob

\# : num of iterations

#output : Updated weights and biases after each iteration

function \[weights biases costs\] = L\_Layer\_DeepModel(X, Y, layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",learning\_rate = .3, lambd=0, keep\_prob=1, num\_iterations = 10000,initType="default")#lr was 0.009

rand ("seed", 1);

costs = \[\] ;

if (strcmp(initType,"He"))

\# He Initialization

\[weights biases\] = HeInitializeDeepModel(layersDimensions);

elseif (strcmp(initType,"Xav"))

\# Xavier Initialization

\[weights biases\] = XavInitializeDeepModel(layersDimensions);

else

\# Default initialization.

\[weights biases\] = initializeDeepModel(layersDimensions);

endif

\# Loop (gradient descent)

for i = 0:num\_iterations

\# Forward propagation: \[LINEAR -> RELU\]\*(L-1) -> LINEAR -> SIGMOID.

\[AL forward\_caches activation\_caches droputMat\] =

forwardPropagationDeep(X, weights, biases,keep\_prob, hiddenActivationFunc, outputActivationFunc=outputActivationFunc);

\# Regularization parameter is 0

if (lambd==0)

\# Compute cost.

cost = computeCost(AL,

Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));

else

\# Compute cost with regularization

 cost = computeCostWithReg(weights, AL, Y, lambd, outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));

endif

\# Backward propagation.

\[gradsDA gradsDW gradsDB\] = backwardPropagationDeep(AL, Y,

activation\_caches,forward\_caches, droputMat, lambd, keep\_prob, hiddenActivationFunc, outputActivationFunc=outputActivationFunc, numClasses=layersDimensions(size(layersDimensions)

(2)));

\# Update parameters.

\[weights biases\] = gradientDescent(weights,biases,

gradsDW,gradsDB,learning\_rate,outputActivationFunc=outputActivationFunc);

\# Print the cost every 1000 iterations

if ( mod(i,1000) == 0)

costs =\[costs cost\];

#disp ("Cost after iteration"), L2RegularizationCost(i),disp(cost); printf("Cost after iteration i=%i cost=%d\\n",i,cost); endif

endfor

end

\# Execute a L layer Deep learning model with Stochastic Gradient descent

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu /tanh

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : learning rate

\# : mini\_batch\_size

\# : num of epochs

#output : Updated weights and biases after each iteration

function \[weights biases costs\] = L\_Layer\_DeepModel\_SGD(X, Y, layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",learning\_rate = .3,

 mini\_batch\_size = 64, num\_epochs = 2500)#lr was 0.009

rand ("seed", 1);

costs = \[\] ;

\# Parameters initialization.

\[weights biases\] = initializeDeepModel(layersDimensions);

seed=10;

\# Loop (gradient descent)

for i = 0:num\_epochs

seed = seed + 1;

\[mini\_batches\_X mini\_batches\_Y\] = random\_mini\_batches(X, Y,

mini\_batch\_size, seed);

minibatches=length(mini\_batches\_X);

for batch=1:minibatches

X=mini\_batches\_X{batch};

Y=mini\_batches\_Y{batch};

\# Forward propagation: \[LINEAR -> RELU\]\*(L-1) -> LINEAR -> SIGMOID/SOFTMAX.

\[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights, biases,hiddenActivationFunc,

outputActivationFunc=outputActivationFunc);

#disp(batch);

#disp(size(X));

#disp(size(Y));

\# Compute cost.

cost = computeCost(AL,

Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));

#disp(cost);

\# Backward propagation.

\[gradsDA gradsDW gradsDB\] = backwardPropagationDeep(AL, Y,

activation\_caches,forward\_caches,hiddenActivationFunc,

outputActivationFunc=outputActivationFunc,

numClasses=layersDimensions(size(layersDimensions)

(2)));

 # Update parameters.

\[weights biases\] = gradientDescent(weights,biases,

gradsDW,gradsDB,learning\_rate,outputActivationFunc=outputActivationFunc); endfor

\# Print the cost every 1000 iterations

if ( mod(i,1000) == 0)

costs =\[costs cost\];

#disp ("Cost after iteration"), disp(i),disp(cost); printf("Cost after iteration i=%i cost=%d\\n",i,cost); endif

endfor

end

\# Plot cost vs iterations

function plotCostVsIterations(maxIterations,costs,fig1)

iterations=\[0:1000:maxIterations\];

plot(iterations,costs);

title ("Cost vs no of iterations ");

xlabel("No of iterations");

ylabel("Cost");

print -dpng figReg2-o

end;

\# Compute the predicted value for a given input

\# Input : Neural Network parameters

\# : Input data

function \[predictions\]= predict(weights, biases,

X,keep\_prob=1,hiddenActivationFunc="relu")

\[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights, biases,keep\_prob,hiddenActivationFunc);

predictions = (AL>0.5);

end

\# Plot the decision boundary

function plotDecisionBoundary(data,weights,

biases,keep\_prob=1,hiddenActivationFunc="relu",fig2)

%Plot a non-linear decision boundary learned by the SVM

 colormap ("summer");

% Make classification predictions over a grid of values

x1plot = linspace(min(data(:,1)), max(data(:,1)), 400)';

x2plot = linspace(min(data(:,2)), max(data(:,2)), 400)';

\[X1, X2\] = meshgrid(x1plot, x2plot);

vals = zeros(size(X1));

\# Plot the prediction for the grid

for i = 1:size(X1, 2)

gridPoints = \[X1(:, i), X2(:, i)\];

vals(:, i)=predict(weights, biases,gridPoints',keep\_prob,

hiddenActivationFunc=hiddenActivationFunc);

endfor

scatter(data(:,1),data(:,2),8,c=data(:,3),"filled");

% Plot the boundary

hold on

#contour(X1, X2, vals, \[0 0\], 'LineWidth', 2);

contour(X1, X2, vals,"linewidth",4);

title ({"3 layer Neural Network decision boundary"}); hold off;

print -dpng figReg22-o

end

#Compute scores

function \[AL\]= scores(weights, biases, X,hiddenActivationFunc="relu")

\[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights, biases,hiddenActivationFunc);

end

\# Create Random mini batches. Return cell arrays with the mini batches

\# Input : X, Y

\# : Size of minibatch

#Output : mini batches X & Y

function \[mini\_batches\_X mini\_batches\_Y\]= random\_mini\_batches(X, Y, miniBatchSize = 64, seed = 0)

rand ("seed", seed);

 # Get number of training samples

m = size(X)(2);

\# Create a list of random numbers < m

permutation = randperm(m);

\# Randomly shuffle the training data

shuffled\_X = X(:, permutation);

shuffled\_Y = Y(:, permutation);

\# Compute number of mini batches

numCompleteMinibatches = floor(m/miniBatchSize);

batch=0;

for k = 0:(numCompleteMinibatches-1)

#Set the start and end of each mini batch

batch=batch+1;

lower=(k\*miniBatchSize)+1;

upper=(k+1) \* miniBatchSize;

mini\_batch\_X = shuffled\_X(:, lower:upper);

mini\_batch\_Y = shuffled\_Y(:, lower:upper);

\# Create cell arrays

mini\_batches\_X{batch} = mini\_batch\_X;

mini\_batches\_Y{batch} = mini\_batch\_Y;

endfor

\# If the batc size does not cleanly divide with number of mini batches if mod(m ,miniBatchSize) != 0

\# Set the start and end of the last mini batch

l=floor(m/miniBatchSize)\*miniBatchSize;

m=l+ mod(m,miniBatchSize);

mini\_batch\_X = shuffled\_X(:,(l+1):m);

mini\_batch\_Y = shuffled\_Y(:,(l+1):m);

batch=batch+1;

mini\_batches\_X{batch} = mini\_batch\_X;

mini\_batches\_Y{batch} = mini\_batch\_Y;

endif

end

\# Plot decision boundary

function plotDecisionBoundary1( data,weights, biases,keep\_prob=1, hiddenActivationFunc="relu")

% Make classification predictions over a grid of values

x1plot = linspace(min(data(:,1)), max(data(:,1)), 400)';

x2plot = linspace(min(data(:,2)), max(data(:,2)), 400)';

\[X1, X2\] = meshgrid(x1plot, x2plot);

vals = zeros(size(X1));

for i = 1:size(X1, 2)

gridPoints = \[X1(:, i), X2(:, i)\];

\[AL forward\_caches activation\_caches\] =

forwardPropagationDeep(gridPoints', weights,

biases,keep\_prob,hiddenActivationFunc, outputActivationFunc="softmax");

\[l m\] = max(AL, \[ \], 2);

vals(:, i)= m;

endfor

scatter(data(:,1),data(:,2),8,c=data(:,3),"filled");

% Plot the boundary

hold on

contour(X1, X2, vals,"linewidth",4);

print -dpng "fig-o1.png"

end

 

**8.**

**Appendix 7 - Gradient Descent**

**Optimization techniques**

**7.1 Python**

\# -\*- coding: utf-8 -\*-

############################################################################################################

#

\# File: DLfunctions7.py

\# Developer: Tinniam V Ganesh

\# Date : 16 Apr 2018

#

##########################################################################################################

import numpy as np

import matplotlib.pyplot as plt

import matplotlib

import matplotlib.pyplot as plt

from matplotlib import cm

import math

import sklearn

import sklearn.datasets

\# Conmpute the sigmoid of a vector

def sigmoid(Z):

A=1/(1+np.exp(-Z))

cache=Z

return A,cache

\# Conmpute the Relu of a vector

def relu(Z):

A = np.maximum(0,Z)

cache=Z

return A,cache

\# Conmpute the tanh of a vector

def tanh(Z):

A = np.tanh(Z)

cache=Z

return A,cache

\# Conmpute the softmax of a vector

def softmax(Z):

\# get unnormalized probabilities

exp\_scores = np.exp(Z.T)

\# normalize them for each example

A = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

cache=Z

return A,cache

\# Conmpute the stable softmax of a vector

def stableSoftmax(Z):

#Compute the softmax of vector x in a numerically stable way.

shiftZ = Z.T - np.max(Z.T,axis=1).reshape(-1,1)

exp\_scores = np.exp(shiftZ)

\# normalize them for each example

A = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

cache=Z

return A,cache

\# Compute the derivative of Relu

def reluDerivative(dA, cache):

Z = cache

dZ = np.array(dA, copy=True) # just converting dz to a correct object.

\# When z <= 0, you should set dz to 0 as well.

dZ\[Z <= 0\] = 0

return dZ

\# Compute the derivative of sigmoid

def sigmoidDerivative(dA, cache):

Z = cache

s = 1/(1+np.exp(-Z))

dZ = dA \* s \* (1-s)

return dZ

\# Compute the derivative of tanh

def tanhDerivative(dA, cache):

Z = cache

a = np.tanh(Z)

dZ = dA \* (1 - np.power(a, 2))

return dZ

\# Compute the derivative of softmax

def softmaxDerivative(dA, cache,y,numTraining):

\# Note : dA not used. dL/dZ = dL/dA \* dA/dZ = pi-yi

Z = cache

\# Compute softmax

exp\_scores = np.exp(Z.T)

\# normalize them for each example

probs = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

\# compute the gradient on scores

dZ = probs

\# dZ = pi- yi

dZ\[range(int(numTraining)),y\[:,0\]\] -= 1

return(dZ)

\# Compute the derivative of Stable softmax

def stableSoftmaxDerivative(dA, cache,y,numTraining):

 # Note : dA not used. dL/dZ = dL/dA \* dA/dZ = pi-yi Z = cache

\# Compute stable softmax

shiftZ = Z.T - np.max(Z.T,axis=1).reshape(-1,1)

exp\_scores = np.exp(shiftZ)

\# normalize them for each example

probs = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

#print(probs)

\# compute the gradient on scores

dZ = probs

\# dZ = pi- yi

dZ\[range(int(numTraining)),y\[:,0\]\] -= 1

return(dZ)

\# Initialize the model

\# Input : number of features

\# number of hidden units

\# number of units in output

\# Returns: Weight and bias matrices and vectors

def initializeModel(numFeats,numHidden,numOutput):

np.random.seed(1)

W1=np.random.randn(numHidden,numFeats)\*0.01 # Multiply by .01

b1=np.zeros((numHidden,1))

W2=np.random.randn(numOutput,numHidden)\*0.01

b2=np.zeros((numOutput,1))

\# Create a dictionary of the neural network parameters

nnParameters={'W1':W1,'b1':b1,'W2':W2,'b2':b2}

return(nnParameters)

\# Initialize model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers def initializeDeepModel(layerDimensions):

np.random.seed(3)

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

 # The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

layerParams = {}

for l in range(1,len(layerDimensions)):

layerParams\['W' + str(l)\] =

np.random.randn(layerDimensions\[l\],layerDimensions\[l-1\])\*0.01 # Multiply by

.01

layerParams\['b' + str(l)\] = np.zeros((layerDimensions\[l\],1))

np.savetxt('W' + str(l)+'.csv',layerParams\['W' + str(l)\],delimiter=',') np.savetxt('b' + str(l)+'.csv',layerParams\['b' + str(l)\],delimiter=',') return(layerParams)

return Z, cache

\# He Initialization model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers

\# He initilization multiplies the random numbers with sqrt(2/layerDimensions\[l-1\])

def HeInitializeDeepModel(layerDimensions):

np.random.seed(3)

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

layerParams = {}

for l in range(1,len(layerDimensions)):

layerParams\['W' + str(l)\] = np.random.randn(layerDimensions\[l\], layerDimensions\[l-1\])\*np.sqrt(2/layerDimensions\[l-1\])

layerParams\['b' + str(l)\] = np.zeros((layerDimensions\[l\],1))

return(layerParams)

return Z, cache

\# Xavier Initialization model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers

\# Xavier initilization multiplies the random numbers with

sqrt(1/layerDimensions\[l-1\])

def XavInitializeDeepModel(layerDimensions): np.random.seed(3)

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

layerParams = {}

for l in range(1,len(layerDimensions)):

layerParams\['W' + str(l)\] = np.random.randn(layerDimensions\[l\], layerDimensions\[l-1\])\*np.sqrt(1/layerDimensions\[l-1\])

layerParams\['b' + str(l)\] = np.zeros((layerDimensions\[l\],1))

return(layerParams)

return Z, cache

\# Initialize velocity of

\# Input : parameters

\# Returns: v - Initial velocity

def initializeVelocity(parameters):

L = len(parameters)//2 # Create an integer

v = {}

\# Initialize velocity with the same dimensions as W

for l in range(L):

v\["dW" + str(l+1)\] = np.zeros((parameters\['W' + str(l+1)\].shape\[0\], parameters\['W' + str(l+1)\].shape\[1\]))

v\["db" + str(l+1)\] = np.zeros((parameters\['b' + str(l+1)\].shape\[0\], parameters\['b' + str(l+1)\].shape\[1\]))

return v

\# Initialize RMSProp param

\# Input : List of units in each layer

\# Returns: s - Initial RMSProp

def initializeRMSProp(parameters):

L = len(parameters)//2 # Create an integer

s = {}

\# Initialize velocity with the same dimensions as W

for l in range(L):

s\["dW" + str(l+1)\] = np.zeros((parameters\['W' + str(l+1)\].shape\[0\], parameters\['W' + str(l+1)\].shape\[1\]))

s\["db" + str(l+1)\] = np.zeros((parameters\['b' + str(l+1)\].shape\[0\], parameters\['b' + str(l+1)\].shape\[1\]))

return s

\# Initialize Adam param

\# Input : List of units in each layer

\# Returns: v and s - Adam paramaters

def initializeAdam(parameters) :

L = len(parameters) // 2 # number of layers in the neural networks v = {}

s = {}

\# Initialize v, s.

for l in range(L):

v\["dW" + str(l+1)\] = np.zeros((parameters\['W' + str(l+1)\].shape\[0\], parameters\['W' + str(l+1)\].shape\[1\]))

v\["db" + str(l+1)\] = np.zeros((parameters\['b' + str(l+1)\].shape\[0\], parameters\['b' + str(l+1)\].shape\[1\]))

s\["dW" + str(l+1)\] = np.zeros((parameters\['W' + str(l+1)\].shape\[0\], parameters\['W' + str(l+1)\].shape\[1\]))

s\["db" + str(l+1)\] = np.zeros((parameters\['b' + str(l+1)\].shape\[0\], parameters\['b' + str(l+1)\].shape\[1\]))

return v, s

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prev - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# keep\_prob

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : A, cache

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

def layerActivationForward(A\_prev, W, b, keep\_prob=1,

activationFunc="relu"):

\# Compute Z

Z = np.dot(W,A\_prev) + b

forward\_cache = (A\_prev, W, b)

\# Compute the activation for sigmoid

if activationFunc == "sigmoid":

A, activation\_cache = sigmoid(Z)

\# Compute the activation for Relu

elif activationFunc == "relu":

A, activation\_cache = relu(Z)

\# Compute the activation for tanh

elif activationFunc == 'tanh':

A, activation\_cache = tanh(Z)

elif activationFunc == 'softmax':

A, activation\_cache = stableSoftmax(Z)

cache = (forward\_cache, activation\_cache)

return A, cache

\# Compute the forward propagation for layers 1..L

\# Input : X - Input Features

\# parameters: Weights and biases

\# keep\_prob

\# hiddenActivationFunc - Activation function at hidden layers Relu/tanh

\# outputActivationFunc - Activation function at output - sigmoid/softmax

\# Returns : AL

\# caches

\# dropoutMat

\# The forward propoagtion uses the Relu/tanh activation from layer 1..L-1 and sigmoid actiovation at layer L

def forwardPropagationDeep(X, parameters,keep\_prob=1,

hiddenActivationFunc='relu',outputActivationFunc='sigmoid'):

caches = \[\]

#initialize the dropout matrix

 dropoutMat = {}

\# Set A to X (A0)

A = X

L = len(parameters)//2 # number of layers in the neural network

\# Loop through from layer 1 to upto layer L

for l in range(1, L):

A\_prev = A

\# Zi = Wi x Ai-1 + bi and Ai = g(Zi)

A, cache = layerActivationForward(A\_prev, parameters\['W'+str(l)\], parameters\['b'+str(l)\], keep\_prob, activationFunc = hiddenActivationFunc)

\# Randomly drop some activation units

\# Create a matrix as the same shape as A

D = np.random.rand(A.shape\[0\],A.shape\[1\])

D = (D < keep\_prob)

\# We need to use the same 'dropout' matrix in backward propagation

\# Save the dropout matrix for use in backprop

dropoutMat\["D" + str(l)\] =D

A= np.multiply(A,D)

A = np.divide(A,keep\_prob)

caches.append(cache)

\# last layer

AL, cache = layerActivationForward(A, parameters\['W'+str(L)\], parameters\['b'+str(L)\], activationFunc = outputActivationFunc) caches.append(cache)

return AL, caches, dropoutMat

\# Compute the cost

\# Input : parameters

\# : AL

\# : Y

\# :outputActivationFunc - Activation function at output -

sigmoid/softmax/tanh

\# Output: cost

def computeCost(parameters,AL,Y,outputActivationFunc="sigmoid"):

 if outputActivationFunc=="sigmoid": m= float(Y.shape\[1\])

\# Element wise multiply for logprobs

cost=-1/m \*np.sum(Y\*np.log(AL) + (1-Y)\*(np.log(1-AL)))

cost = np.squeeze(cost)

elif outputActivationFunc=="softmax":

\# Take transpose of Y for softmax

Y=Y.T

m= float(len(Y))

\# Compute log probs. Take the log prob of correct class based on output y correct\_logprobs = -np.log(AL\[range(int(m)),Y.T\])

\# Conpute loss

cost = np.sum(correct\_logprobs)/m

return cost

\# Compute the cost with regularization

\# Input : parameters

\# : AL

\# : Y

\# : lambd

\# :outputActivationFunc - Activation function at output -

sigmoid/softmax/tanh

\# Output: cost

def computeCostWithReg(parameters,AL,Y,lambd,

outputActivationFunc="sigmoid"):

if outputActivationFunc=="sigmoid":

m= float(Y.shape\[1\])

\# Element wise multiply for logprobs

cost=-1/m \*np.sum(Y\*np.log(AL) + (1-Y)\*(np.log(1-AL)))

cost = np.squeeze(cost)

\# Regularization cost

L= int(len(parameters)/2)

L2RegularizationCost=0

for l in range(L):

L2RegularizationCost+=np.sum(np.square(parameters\['W'+str(l+1)\]))

L2RegularizationCost = (lambd/(2\*m))\*L2RegularizationCost

cost = cost + L2RegularizationCost

elif outputActivationFunc=="softmax":

\# Take transpose of Y for softmax

Y=Y.T

m= float(len(Y))

\# Compute log probs. Take the log prob of correct class based on output y correct\_logprobs = -np.log(AL\[range(int(m)),Y.T\])

\# Conpute loss

cost = np.sum(correct\_logprobs)/m

\# Regularization cost

L= int(len(parameters)/2)

L2RegularizationCost=0

for l in range(L):

L2RegularizationCost+=np.sum(np.square(parameters\['W'+str(l+1)\])) L2RegularizationCost = (lambd/(2\*m))\*L2RegularizationCost

cost = cost + L2RegularizationCost

return cost

\# Compute the backpropoagation for 1 cycle with dropout included

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# # Input features

\# # keep\_prob

\# # Output values Y

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

def layerActivationBackward(dA, cache, Y, keep\_prob=1,

activationFunc="relu"):

forward\_cache, activation\_cache = cache

A\_prev, W, b = forward\_cache

 numtraining = float(A\_prev.shape\[1\])

#print("n=",numtraining)

#print("no=",numtraining)

if activationFunc == "relu":

dZ = reluDerivative(dA, activation\_cache)

elif activationFunc == "sigmoid":

dZ = sigmoidDerivative(dA, activation\_cache)

elif activationFunc == "tanh":

dZ = tanhDerivative(dA, activation\_cache)

elif activationFunc == "softmax":

dZ = stableSoftmaxDerivative(dA, activation\_cache,Y,numtraining) if activationFunc == 'softmax':

dW = 1/numtraining \* np.dot(A\_prev,dZ)

db = 1/numtraining \* np.sum(dZ, axis=0, keepdims=True)

dA\_prev = np.dot(dZ,W)

else:

#print(numtraining)

dW = 1/numtraining \*(np.dot(dZ,A\_prev.T))

#print("dW=",dW)

db = 1/numtraining \* np.sum(dZ, axis=1, keepdims=True)

#print("db=",db)

dA\_prev = np.dot(W.T,dZ)

return dA\_prev, dW, db

\# Compute the backpropoagation with regularization for 1 cycle

\# Input : dA- Neural Network parameters

\# # cache - forward\_cache & activation\_cache

\# # Output values Y

\# # lambd

\# # activationFunc

\# Returns dA\_prev, dW, db

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

def layerActivationBackwardWithReg(dA, cache, Y, lambd, activationFunc):

 forward\_cache, activation\_cache = cache

A\_prev, W, b = forward\_cache

numtraining = float(A\_prev.shape\[1\])

#print("n=",numtraining)

#print("no=",numtraining)

if activationFunc == "relu":

dZ = reluDerivative(dA, activation\_cache)

elif activationFunc == "sigmoid":

dZ = sigmoidDerivative(dA, activation\_cache)

elif activationFunc == "tanh":

dZ = tanhDerivative(dA, activation\_cache)

elif activationFunc == "softmax":

dZ = stableSoftmaxDerivative(dA, activation\_cache,Y,numtraining) if activationFunc == 'softmax':

\# Add the regularization factor

dW = 1/numtraining \* np.dot(A\_prev,dZ) + (lambd/numtraining) \* W.T

db = 1/numtraining \* np.sum(dZ, axis=0, keepdims=True)

dA\_prev = np.dot(dZ,W)

else:

\# Add the regularization factor

dW = 1/numtraining \*(np.dot(dZ,A\_prev.T)) + (lambd/numtraining) \* W

#print("dW=",dW)

db = 1/numtraining \* np.sum(dZ, axis=1, keepdims=True)

#print("db=",db)

dA\_prev = np.dot(W.T,dZ)

return dA\_prev, dW, db

\# Compute the backpropoagation for 1 cycle

\# Input : AL: Output of L layer Network - weights

\# # Y Real output

\# # caches -- list of caches containing:

\# # dropoutMat

\# # lambd

\# # keep\_prob

\# every cache of layerActivationForward() with "relu"/"tanh"

\# #(it's caches\[l\], for l in range(L-1) i.e l = 0...L-2)

\# #the cache of layerActivationForward() with "sigmoid" (it's caches\[L-1\])

\# # hiddenActivationFunc - Activation function at hidden layers -

relu/sigmoid/tanh

\# #outputActivationFunc - Activation function at output - sigmoid/softmax

#

\# Returns:

\# gradients -- A dictionary with the gradients

\# gradients\["dA" + str(l)\] = ...

\# gradients\["dW" + str(l)\] = ...

\# gradients\["db" + str(l)\] = ...

def backwardPropagationDeep(AL, Y, caches, dropoutMat, lambd=0, keep\_prob=1, hiddenActivationFunc='relu',outputActivationFunc="sigmoid"):

#initialize the gradients

gradients = {}

\# Set the number of layers

L = len(caches)

m = float(AL.shape\[1\])

if outputActivationFunc == "sigmoid":

Y = Y.reshape(AL.shape) # after this line, Y is the same shape as AL

\# Initializing the backpropagation

\# dl/dAL= -(y/a + (1-y)/(1-a)) - At the output layer

dAL = - (np.divide(Y, AL) - np.divide(1 - Y, 1 - AL))

else:

dAL =0

Y=Y.T

\# Since this is a binary classification the activation at output is sigmoid

\# Get the gradients at the last layer

\# Inputs: "AL, Y, caches".

\# Outputs: "gradients\["dAL"\], gradients\["dWL"\], gradients\["dbL"\]

current\_cache = caches\[L-1\]

if lambd==0:

gradients\["dA" + str(L)\], gradients\["dW" + str(L)\], gradients\["db" + str(L)\]

\= layerActivationBackward(dAL, current\_cache,

Y, activationFunc = outputActivationFunc)

else: #Regularization

gradients\["dA" + str(L)\], gradients\["dW" + str(L)\], gradients\["db" + str(L)\]

\= layerActivationBackwardWithReg(dAL, current\_cache,

 Y, lambd, activationFunc = outputActivationFunc)

\# Note dA for softmax is the transpose

if outputActivationFunc == "softmax":

gradients\["dA" + str(L)\] = gradients\["dA" + str(L)\].T

\# Traverse in the reverse direction

for l in reversed(range(L-1)):

\# Compute the gradients for L-1 to 1 for Relu/tanh

\# Inputs: "gradients\["dA" + str(l + 2)\], caches".

\# Outputs: "gradients\["dA" + str(l + 1)\] , gradients\["dW" + str(l + 1)\] , gradients\["db" + str(l + 1)\]

current\_cache = caches\[l\]

#dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackward(gradients\['dA'+str(l+2)\], current\_cache, activationFunc = "relu")

if lambd==0:

\# In the reverse direction use the dame dropout matrix

\# Random dropout

\# Multiply dA'l' with the dropoutMat and divide to keep the expected value same

D = dropoutMat\["D" + str(l+1)\]

\# Drop some dAl's

gradients\['dA'+str(l+2)\]= np.multiply(gradients\['dA'+str(l+2)\],D)

\# Divide by keep\_prob to keep expected value same

gradients\['dA'+str(l+2)\] = np.divide(gradients\['dA'+str(l+2)\],keep\_prob) dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackward(gradients\['dA'+str(l+2)\], current\_cache, Y, keep\_prob=1, activationFunc = hiddenActivationFunc)

else:

dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackwardWithReg(gradients\['dA'+str(l+2)\], current\_cache, Y, lambd, activationFunc = hiddenActivationFunc)

gradients\["dA" + str(l + 1)\] = dA\_prev\_temp

gradients\["dW" + str(l + 1)\] = dW\_temp

 gradients\["db" + str(l + 1)\] = db\_temp return gradients

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients

\# : learning rate

\# : outputActivationFunc - Activation function at output - sigmoid/softmax

#output : Updated weights after 1 iteration

def gradientDescent(parameters, gradients,

learningRate,outputActivationFunc="sigmoid"):

L = int(len(parameters) / 2)

\# Update rule for each parameter.

for l in range(L-1):

parameters\["W" + str(l+1)\] = parameters\['W'+str(l+1)\] -learningRate\*

gradients\['dW' + str(l+1)\]

parameters\["b" + str(l+1)\] = parameters\['b'+str(l+1)\] -learningRate\*

gradients\['db' + str(l+1)\]

if outputActivationFunc=="sigmoid":

parameters\["W" + str(L)\] = parameters\['W'+str(L)\] -learningRate\*

gradients\['dW' + str(L)\]

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] -learningRate\*

gradients\['db' + str(L)\]

elif outputActivationFunc=="softmax":

parameters\["W" + str(L)\] = parameters\['W'+str(L)\] -learningRate\*

gradients\['dW' + str(L)\].T

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] -learningRate\*

gradients\['db' + str(L)\].T

return parameters

\# Update parameters with momentum

\# Input : parameters

\# : gradients

\# : v

\# : beta

\# : learningRate

\# : outputActivationFunc - softmax/sigmoid

#output : Updated parameters and velocity

def gradientDescentWithMomentum(parameters, gradients, v, beta, learningRate, outputActivationFunc="sigmoid"):

L = len(parameters) // 2 # number of layers in the neural networks

\# Momentum update for each parameter

for l in range(L-1):

\# Compute velocities

\# v\['dWk'\] = beta \*v\['dWk'\] + (1-beta)\*dWk

v\["dW" + str(l+1)\] = beta\*v\["dW" + str(l+1)\] + (1-beta) \* gradients\['dW' +

str(l+1)\]

v\["db" + str(l+1)\] = beta\*v\["db" + str(l+1)\] + (1-beta) \* gradients\['db' +

str(l+1)\]

\# Update parameters with velocities

parameters\["W" + str(l+1)\] = parameters\['W' + str(l+1)\] - learningRate\*

v\["dW" + str(l+1)\]

parameters\["b" + str(l+1)\] = parameters\['b' + str(l+1)\] - learningRate\*

v\["db" + str(l+1)\]

if outputActivationFunc=="sigmoid":

v\["dW" + str(L)\] = beta\*v\["dW" + str(L)\] + (1-beta) \* gradients\['dW' +

str(L)\]

v\["db" + str(L)\] = beta\*v\["db" + str(L)\] + (1-beta) \* gradients\['db' + str(L)\]

parameters\["W" + str(L)\] = parameters\['W'+str(L)\] -learningRate\*

gradients\['dW' + str(L)\]

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] -learningRate\*

gradients\['db' + str(L)\]

elif outputActivationFunc=="softmax":

v\["dW" + str(L)\] = beta\*v\["dW" + str(L)\] + (1-beta) \* gradients\['dW' +

str(L)\].T

v\["db" + str(L)\] = beta\*v\["db" + str(L)\] + (1-beta) \* gradients\['db' +

str(L)\].T

parameters\["W" + str(L)\] = parameters\['W'+str(L)\] -learningRate\*

gradients\['dW' + str(L)\].T

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] -learningRate\*

gradients\['db' + str(L)\].T

return parameters, v

\# Update parameters with RMSProp

\# Input : parameters

\# : gradients

\# : s

\# : beta1

\# : learningRate

\# : outputActivationFunc - sigmoid/softmax

\# output : Updated parameters and RMSProp

def gradientDescentWithRMSProp(parameters, gradients, s, beta1, epsilon, learningRate, outputActivationFunc="sigmoid"):

L = len(parameters) // 2 # number of layers in the neural networks

\# Momentum update for each parameter

for l in range(L-1):

\# Compute RMSProp

\# s\['dWk'\] = beta1 \*s\['dWk'\] + (1-beta1)\*dWk\*\*2/sqrt(s\['dWk'\]) s\["dW" + str(l+1)\] = beta1\*s\["dW" + str(l+1)\] + (1-beta1) \* \\ np.multiply(gradients\['dW' + str(l+1)\],gradients\['dW' + str(l+1)\]) s\["db" + str(l+1)\] = beta1\*s\["db" + str(l+1)\] + (1-beta1) \* \\ np.multiply(gradients\['db' + str(l+1)\],gradients\['db' + str(l+1)\])

\# Update parameters with RMSProp

parameters\["W" + str(l+1)\] = parameters\['W' + str(l+1)\] - \\ learningRate\* gradients\['dW' + str(l+1)\]/np.sqrt(s\["dW" + str(l+1)\] +

epsilon)

parameters\["b" + str(l+1)\] = parameters\['b' + str(l+1)\] - \\ learningRate\* gradients\['db' + str(l+1)\]/np.sqrt(s\["db" + str(l+1)\] +

epsilon)

if outputActivationFunc=="sigmoid":

s\["dW" + str(L)\] = beta1\*s\["dW" + str(L)\] + (1-beta1) \* \\ np.multiply(gradients\['dW' + str(L)\],gradients\['dW' + str(L)\]) s\["db" + str(L)\] = beta1\*s\["db" + str(L)\] + (1-beta1) \* \\ np.multiply(gradients\['db' + str(L)\],gradients\['db' + str(L)\])

 parameters\["W" + str(L)\] = parameters\['W'+str(L)\] - \\ learningRate\* gradients\['dW' + str(L)\]/np.sqrt(s\["dW" + str(L)\] +

epsilon)

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] - \\ learningRate\* gradients\['db' + str(L)\]/np.sqrt(s\["db" + str(L)\] + epsilon) elif outputActivationFunc=="softmax":

s\["dW" + str(L)\] = beta1\*s\["dW" + str(L)\] + (1-beta1) \* \\ np.multiply(gradients\['dW' + str(L)\].T,gradients\['dW' + str(L)\].T) s\["db" + str(L)\] = beta1\*s\["db" + str(L)\] + (1-beta1) \* \\ np.multiply(gradients\['db' + str(L)\].T,gradients\['db' + str(L)\].T) parameters\["W" + str(L)\] = parameters\['W'+str(L)\] - \\ learningRate\* gradients\['dW' + str(L)\].T/np.sqrt(s\["dW" + str(L)\] +

epsilon)

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] - \\ learningRate\* gradients\['db' + str(L)\].T/np.sqrt(s\["db" + str(L)\] +

epsilon)

return parameters, s

\# Update parameters with Adam

\# Input : parameters

\# : gradients

\# : v

\# : s

\# : t

\# : beta1

\# : beta2

\# : epsilon

\# : learningRate

\# : outputActivationFunc - sigmoid/softmax

\# output : Updated parameters and RMSProp

def gradientDescentWithAdam(parameters, gradients, v, s, t,

beta1 = 0.9, beta2 = 0.999, epsilon = 1e-8,

learningRate=0.1, outputActivationFunc="sigmoid"):

L = len(parameters) // 2

\# Initializing first moment estimate, python dictionary

v\_corrected = {}

\# Initializing second moment estimate, python dictionary

 s\_corrected = {}

\# Perform Adam upto L-1

for l in range(L-1):

\# Compute momentum

v\["dW" + str(l+1)\] = beta1\*v\["dW" + str(l+1)\] + \\ (1-beta1) \* gradients\['dW' + str(l+1)\]

v\["db" + str(l+1)\] = beta1\*v\["db" + str(l+1)\] + \\ (1-beta1) \* gradients\['db' + str(l+1)\]

\# Compute bias-corrected first moment estimate.

v\_corrected\["dW" + str(l+1)\] = v\["dW" + str(l+1)\]/(1-np.power(beta1,t)) v\_corrected\["db" + str(l+1)\] = v\["db" + str(l+1)\]/(1-np.power(beta1,t))

\# Moving average of the squared gradients like RMSProp

s\["dW" + str(l+1)\] = beta2\*s\["dW" + str(l+1)\] + \\ (1-beta2) \* np.multiply(gradients\['dW' + str(l+1)\],gradients\['dW' +

str(l+1)\])

s\["db" + str(l+1)\] = beta2\*s\["db" + str(l+1)\] + \\ (1-beta2) \* np.multiply(gradients\['db' + str(l+1)\],gradients\['db' +

str(l+1)\])

\# Compute bias-corrected second raw moment estimate.

s\_corrected\["dW" + str(l+1)\] = s\["dW" + str(l+1)\]/(1-np.power(beta2,t)) s\_corrected\["db" + str(l+1)\] = s\["db" + str(l+1)\]/(1-np.power(beta2,t))

\# Update parameters.

d1=np.sqrt(s\_corrected\["dW" + str(l+1)\]+epsilon)

d2=np.sqrt(s\_corrected\["db" + str(l+1)\]+epsilon)

parameters\["W" + str(l+1)\] = parameters\['W' + str(l+1)\]- \\ (learningRate\* v\_corrected\["dW" + str(l+1)\]/d1)

parameters\["b" + str(l+1)\] = parameters\['b' + str(l+1)\] - \\ (learningRate\* v\_corrected\["db" + str(l+1)\]/d2)

if outputActivationFunc=="sigmoid":

 #Compute 1st moment for L

v\["dW" + str(L)\] = beta1\*v\["dW" + str(L)\] + (1-beta1) \* gradients\['dW'

\+ str(L)\]

v\["db" + str(L)\] = beta1\*v\["db" + str(L)\] + (1-beta1) \* gradients\['db' +

str(L)\]

\# Compute bias-corrected first moment estimate.

v\_corrected\["dW" + str(L)\] = v\["dW" + str(L)\]/(1-np.power(beta1,t)) v\_corrected\["db" + str(L)\] = v\["db" + str(L)\]/(1-np.power(beta1,t))

\# Compute 2nd moment for L

s\["dW" + str(L)\] = beta2\*s\["dW" + str(L)\] + (1-beta2) \* \\ np.multiply(gradients\['dW' + str(L)\],gradients\['dW' + str(L)\]) s\["db" + str(L)\] = beta2\*s\["db" + str(L)\] + (1-beta2) \* \\ np.multiply(gradients\['db' + str(L)\],gradients\['db' + str(L)\])

\# Compute bias-corrected second raw moment estimate.

s\_corrected\["dW" + str(L)\] = s\["dW" + str(L)\]/(1-np.power(beta2,t)) s\_corrected\["db" + str(L)\] = s\["db" + str(L)\]/(1-np.power(beta2,t))

\# Update parameters.

d1=np.sqrt(s\_corrected\["dW" + str(L)\]+epsilon)

d2=np.sqrt(s\_corrected\["db" + str(L)\]+epsilon)

parameters\["W" + str(L)\] = parameters\['W' + str(L)\]- \\ (learningRate\* v\_corrected\["dW" + str(L)\]/d1)

parameters\["b" + str(L)\] = parameters\['b' + str(L)\] - \\ (learningRate\* v\_corrected\["db" + str(L)\]/d2)

elif outputActivationFunc=="softmax":

\# Compute 1st moment

v\["dW" + str(L)\] = beta1\*v\["dW" + str(L)\] + (1-beta1) \* gradients\['dW'

\+ str(L)\].T

v\["db" + str(L)\] = beta1\*v\["db" + str(L)\] + (1-beta1) \* gradients\['db' +

str(L)\].T

\# Compute bias-corrected first moment estimate.

v\_corrected\["dW" + str(L)\] = v\["dW" + str(L)\]/(1-np.power(beta1,t)) v\_corrected\["db" + str(L)\] = v\["db" + str(L)\]/(1-np.power(beta1,t))

#Compute 2nd moment

s\["dW" + str(L)\] = beta2\*s\["dW" + str(L)\] + (1-beta2) \*

np.multiply(gradients\['dW' + str(L)\].T,gradients\['dW' + str(L)\].T) s\["db" + str(L)\] = beta2\*s\["db" + str(L)\] + (1-beta2) \*

np.multiply(gradients\['db' + str(L)\].T,gradients\['db' + str(L)\].T)

\# Compute bias-corrected second raw moment estimate.

s\_corrected\["dW" + str(L)\] = s\["dW" + str(L)\]/(1-np.power(beta2,t)) s\_corrected\["db" + str(L)\] = s\["db" + str(L)\]/(1-np.power(beta2,t))

\# Update parameters.

d1=np.sqrt(s\_corrected\["dW" + str(L)\]+epsilon)

d2=np.sqrt(s\_corrected\["db" + str(L)\]+epsilon)

parameters\["W" + str(L)\] = parameters\['W' + str(L)\]- \\ (learningRate\* v\_corrected\["dW" + str(L)\]/d1)

parameters\["b" + str(L)\] = parameters\['b' + str(L)\] - \\ (learningRate\* v\_corrected\["db" + str(L)\]/d2)

return parameters, v, s

\# Execute a L layer Deep learning model

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu

/tanh/sigmoid

\# : outputActivationFunc - Activation function at output layer sigmoid/softmax

\# : learning rate

\# : lambd

\# : keep\_prob

\# : num of iteration

\# : initType

#output : parameters

def L\_Layer\_DeepModel(X1, Y1, layersDimensions,

hiddenActivationFunc='relu', outputActivationFunc="sigmoid", learningRate = .3, lambd=0, keep\_prob=1, num\_iterations =

10000,initType="default", print\_cost=False,figure="figa.png"): np.random.seed(1)

 costs = \[\]

\# Parameters initialization.

if initType == "He":

parameters = HeInitializeDeepModel(layersDimensions)

elif initType == "Xavier" :

parameters = XavInitializeDeepModel(layersDimensions)

else: #Default

parameters = initializeDeepModel(layersDimensions)

\# Loop (gradient descent)

for i in range(0, num\_iterations):

AL, caches, dropoutMat = forwardPropagationDeep(X1, parameters, keep\_prob,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc)

\# Regularization parameter is 0

if lambd==0:

\# Compute cost

cost = computeCost(parameters,AL, Y1,

outputActivationFunc=outputActivationFunc)

\# Include L2 regularization

else:

\# Compute cost

cost = computeCostWithReg(parameters,AL, Y1, lambd,

outputActivationFunc=outputActivationFunc)

\# Backward propagation.

gradients = backwardPropagationDeep(AL, Y1, caches, dropoutMat, lambd, keep\_prob,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc)

\# Update parameters.

parameters = gradientDescent(parameters, gradients,

learningRate=learningRate,outputActivationFunc=outputActivationFunc)

\# Print the cost every 100 training example

if print\_cost and i % 1000 == 0:

 print ("Cost after iteration %i: %f" %(i, cost)) if print\_cost and i % 1000 == 0:

costs.append(cost)

\# plot the cost

plt.plot(np.squeeze(costs))

plt.ylabel('Cost')

plt.xlabel('No of iterations (x1000)')

plt.title("Learning rate =" + str(learningRate))

plt.savefig(figure,bbox\_inches='tight')

#plt.show()

plt.clf()

plt.close()

return parameters

\# Execute a L layer Deep learning model Stoachastic Gradient Descent

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu

/tanh/sigmoid

\# : outputActivationFunc - Activation function at output - sigmoid/softmax

\# : learning rate

\# : lrDecay

\# : lambd

\# : keep\_prob

\# : optimizer

\# : beta

\# : beta1

\# : beta2

\# : epsilon

\# : mini\_batch\_size

\# : num\_epochs

\# :

#output : Updated weights and biases

def L\_Layer\_DeepModel\_SGD(X1, Y1, layersDimensions,

hiddenActivationFunc='relu', outputActivationFunc="sigmoid", learningRate = .3, lrDecay=False, decayRate=1,

 lambd=0, keep\_prob=1, optimizer="gd",beta=0.9,beta1=0.9, beta2=0.999,

epsilon = 1e-8,mini\_batch\_size = 64, num\_epochs = 2500,

print\_cost=False, figure="figa.png"):

print("lr=",learningRate)

print("lrDecay=",lrDecay)

print("decayRate=",decayRate)

print("lambd=",lambd)

print("keep\_prob=",keep\_prob)

print("optimizer=",optimizer)

print("beta=",beta)

print("beta1=",beta1)

print("beta2=",beta2)

print("epsilon=",epsilon)

print("mini\_batch\_size=",mini\_batch\_size)

print("num\_epochs=",num\_epochs)

print("epsilon=",epsilon)

t =0 # Adam counter

np.random.seed(1)

costs = \[\]

\# Parameters initialization.

parameters = initializeDeepModel(layersDimensions)

#Initialize the optimizer

if optimizer == "gd":

pass # no initialization required for gradient descent

elif optimizer == "momentum":

v = initializeVelocity(parameters)

elif optimizer == "rmsprop":

s = initializeRMSProp(parameters)

elif optimizer == "adam":

v,s = initializeAdam(parameters)

 seed=10

\# Loop for number of epochs

for i in range(num\_epochs):

\# Define the random minibatches. We increment the seed to reshuffle differently the dataset after each epoch

seed = seed + 1

minibatches = random\_mini\_batches(X1, Y1, mini\_batch\_size, seed) batch=0

\# Loop through each mini batch

for minibatch in minibatches:

#print("batch=",batch)

batch=batch+1

\# Select a minibatch

(minibatch\_X, minibatch\_Y) = minibatch

\# Perfrom forward propagation

AL, caches, dropoutMat = forwardPropagationDeep(minibatch\_X,

parameters, keep\_prob,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc)

\# Compute cost

\# Regularization parameter is 0

if lambd==0:

\# Compute cost

cost = computeCost(parameters, AL, minibatch\_Y,

outputActivationFunc=outputActivationFunc)

else: # Include L2 regularization

\# Compute cost

cost = computeCostWithReg(parameters, AL, minibatch\_Y, lambd, outputActivationFunc=outputActivationFunc)

\# Backward propagation.

gradients = backwardPropagationDeep(AL, minibatch\_Y,

caches,dropoutMat, lambd,

keep\_prob,hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc) if optimizer == "gd":

\# Update parameters normal gradient descent

 parameters = gradientDescent(parameters, gradients, learningRate=learningRate,outputActivationFunc=outputActivationFunc) elif optimizer == "momentum":

\# Update parameters for gradient descent with momentum

parameters, v = gradientDescentWithMomentum(parameters, gradients, v, beta, \\

learningRate=learningRate,outputActivationFunc=outputActivationFunc) elif optimizer == "rmsprop":

\# Update parameters for gradient descent with RMSProp

parameters, s = gradientDescentWithRMSProp(parameters, gradients, s, beta1, epsilon, \\

learningRate=learningRate,outputActivationFunc=outputActivationFunc) elif optimizer == "adam":

t = t + 1 # Adam counter

parameters, v, s = gradientDescentWithAdam(parameters, gradients, v, s,

t, beta1, beta2, epsilon,

learningRate=learningRate,outputActivationFunc=outputActivationFunc)

\# Print the cost every 1000 epoch

if print\_cost and i % 100 == 0:

print ("Cost after epoch %i: %f" %(i, cost))

if print\_cost and i % 100 == 0:

costs.append(cost)

if lrDecay == True:

learningRate = np.power(decayRate,(num\_epochs/1000)) \* learningRate

\# plot the cost

plt.plot(np.squeeze(costs))

plt.ylabel('Cost')

plt.xlabel('No of epochs(x100)')

plt.title("Learning rate =" + str(learningRate))

plt.savefig(figure,bbox\_inches='tight')

#plt.show()

plt.clf()

 plt.close()

\# Create random mini batches

\# Input : X - Input features

\# : Y- output

\# : miniBatchSizes

\# : seed

#output : mini\_batches

def random\_mini\_batches(X, Y, miniBatchSize = 64, seed = 0):

np.random.seed(seed)

\# Get number of training samples

m = X.shape\[1\]

\# Initialize mini batches

mini\_batches = \[\]

\# Create a list of random numbers < m

permutation = list(np.random.permutation(m))

\# Randomly shuffle the training data

shuffled\_X = X\[:, permutation\]

shuffled\_Y = Y\[:, permutation\].reshape((1,m))

\# Compute number of mini batches

numCompleteMinibatches = math.floor(m/miniBatchSize)

\# For the number of mini batches

for k in range(0, numCompleteMinibatches):

\# Set the start and end of each mini batch

mini\_batch\_X = shuffled\_X\[:, k\*miniBatchSize : (k+1) \* miniBatchSize\]

mini\_batch\_Y = shuffled\_Y\[:, k\*miniBatchSize : (k+1) \* miniBatchSize\]

mini\_batch = (mini\_batch\_X, mini\_batch\_Y)

mini\_batches.append(mini\_batch)

#if m % miniBatchSize != 0:. The batch does not evenly divide by the mini batch

 if m % miniBatchSize != 0:

l=math.floor(m/miniBatchSize)\*miniBatchSize

\# Set the start and end of last mini batch

m=l+m % miniBatchSize

mini\_batch\_X = shuffled\_X\[:,l:m\]

mini\_batch\_Y = shuffled\_Y\[:,l:m\]

mini\_batch = (mini\_batch\_X, mini\_batch\_Y)

mini\_batches.append(mini\_batch)

return mini\_batches

\# Plot a decision boundary

\# Input : Input Model,

\# X

\# Y

\# sz - Num of hiden units

\# lr - Learning rate

\# Fig to be saved as

\# Returns Null

def plot\_decision\_boundary(model, X, y,lr,figure1="figb.png"): print("plot")

\# Set min and max values and give it some padding

x\_min, x\_max = X\[0, :\].min() - 1, X\[0, :\].max() + 1

y\_min, y\_max = X\[1, :\].min() - 1, X\[1, :\].max() + 1

colors=\['black','gold'\]

cmap = matplotlib.colors.ListedColormap(colors)

h = 0.01

\# Generate a grid of points with distance h between them

xx, yy = np.meshgrid(np.arange(x\_min, x\_max, h), np.arange(y\_min, y\_max, h))

\# Predict the function value for the whole grid

Z = model(np.c\_\[xx.ravel(), yy.ravel()\])

Z = Z.reshape(xx.shape)

\# Plot the contour and training examples

plt.contourf(xx, yy, Z, cmap="coolwarm")

plt.ylabel('x2')

plt.xlabel('x1')

 x=X.T

y=y.T.reshape(300,)

plt.scatter(x\[:, 0\], x\[:, 1\], c=y, s=20);

print(X.shape)

plt.title("Decision Boundary for learning rate:"+lr) plt.savefig(figure1, bbox\_inches='tight')

#plt.show()

\# Predict output

def predict(parameters,

X,keep\_prob=1,hiddenActivationFunc="relu",outputActivationFunc="sigmoid"): A2, cache,dropoutMat = forwardPropagationDeep(X, parameters,

keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc) predictions = (A2>0.5)

return predictions

\# Predict probabilities

def predict\_proba(parameters, X,outputActivationFunc="sigmoid"): A2, cache = forwardPropagationDeep(X, parameters)

if outputActivationFunc=="sigmoid":

proba=A2

elif outputActivationFunc=="softmax":

proba=np.argmax(A2, axis=0).reshape(-1,1)

print("A2=",A2.shape)

return proba

\# Plot a decision boundary

\# Input : Input Model,

\# X

\# Y

\# sz - Num of hiden units

\# lr - Learning rate

\# Fig to be saved as

\# Returns Null

def plot\_decision\_boundary1(X, y,W1,b1,W2,b2,figure2="figc.png"):

#plot\_decision\_boundary(lambda x: predict(parameters, x.T),

x1,y1.T,str(0.3),"fig2.png")

h = 0.02

 x\_min, x\_max = X\[:, 0\].min() - 1, X\[:, 0\].max() + 1

y\_min, y\_max = X\[:, 1\].min() - 1, X\[:, 1\].max() + 1

xx, yy = np.meshgrid(np.arange(x\_min, x\_max, h),

np.arange(y\_min, y\_max, h))

Z = np.dot(np.maximum(0, np.dot(np.c\_\[xx.ravel(), yy.ravel()\], W1.T) +

b1.T), W2.T) + b2.T

Z = np.argmax(Z, axis=1)

Z = Z.reshape(xx.shape)

fig = plt.figure()

plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral, alpha=0.8)

print(X.shape)

y1=y.reshape(300,)

plt.scatter(X\[:, 0\], X\[:, 1\], c=y1, s=40, cmap=plt.cm.Spectral) plt.xlim(xx.min(), xx.max())

plt.ylim(yy.min(), yy.max())

plt.savefig(figure2, bbox\_inches='tight')

\# Load the data set

def load\_dataset():

np.random.seed(1)

train\_X, train\_Y = sklearn.datasets.make\_circles(n\_samples=300, noise=.05) np.random.seed(2)

test\_X, test\_Y = sklearn.datasets.make\_circles(n\_samples=100, noise=.05)

\# Visualize the data

print(train\_X.shape)

print(train\_Y.shape)

print("load")

#plt.scatter(train\_X\[:, 0\], train\_X\[:, 1\], c=train\_Y, s=40,

cmap=plt.cm.Spectral);

train\_X = train\_X.T

train\_Y = train\_Y.reshape((1, train\_Y.shape\[0\]))

test\_X = test\_X.T

test\_Y = test\_Y.reshape((1, test\_Y.shape\[0\]))

return train\_X, train\_Y, test\_X, test\_Y

**7.2 R**

############################################################################################################

#

\# File : DLfunctions7.R

\# Author : Tinniam V Ganesh

\# Date : 16 Apr 2018

#

##########################################################################################################

library(ggplot2)

library(PRROC)

library(dplyr)

\# Compute the sigmoid of a vector

sigmoid <- function(Z){

A <- 1/(1+ exp(-Z))

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# This is the older version. Very performance intensive

\# Compute relu

reluOld <-function(Z){

A <- apply(Z, 1:2, function(x) max(0,x))

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the Relu of a vector (current version)

relu <-function(Z){

\# Perform relu. Set values less that equal to 0 as 0

Z\[Z<0\]=0

A=Z

cache<-Z

 retvals <- list("A"=A,"Z"=Z) return(retvals)

}

\# Compute the tanh activation of a vector

tanhActivation <- function(Z){

A <- tanh(Z)

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the softmax of a vector

softmax <- function(Z){

\# get unnormalized probabilities

exp\_scores = exp(t(Z))

\# normalize them for each example

A = exp\_scores / rowSums(exp\_scores)

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the detivative of Relu

\# g'(z) = 1 if z >0 and 0 otherwise

reluDerivative <-function(dA, cache){

Z <- cache

dZ <- dA

\# Create a logical matrix of values > 0

a <- Z > 0

\# When z <= 0, you should set dz to 0 as well. Perform an element wise multiply

dZ <- dZ \* a

return(dZ)

}

\# Compute the derivative of sigmoid

\# Derivative g'(z) = a\* (1-a)

sigmoidDerivative <- function(dA, cache){

Z <- cache

 s <- 1/(1+exp(-Z))

dZ <- dA \* s \* (1-s)

return(dZ)

}

\# Compute the derivative of tanh

\# Derivative g'(z) = 1- a^2

tanhDerivative <- function(dA, cache){

Z = cache

a = tanh(Z)

dZ = dA \* (1 - a^2)

return(dZ)

}

\# This function is used in computing the softmax derivative

\# Populate a matrix of 1s in rows where Y==1

\# This may need to be extended for K classes. Currently

\# supports K=3 & K=10

popMatrix <- function(Y,numClasses){

a=rep(0,times=length(Y))

Y1=matrix(a,nrow=length(Y),ncol=numClasses)

#Set the rows and columns as 1's where Y is the class value

if(numClasses==3){

Y1\[Y==0,1\]=1

Y1\[Y==1,2\]=1

Y1\[Y==2,3\]=1

} else if (numClasses==10){

Y1\[Y==0,1\]=1

Y1\[Y==1,2\]=1

Y1\[Y==2,3\]=1

Y1\[Y==3,4\]=1

Y1\[Y==4,5\]=1

Y1\[Y==5,6\]=1

Y1\[Y==6,7\]=1

Y1\[Y==7,8\]=1

Y1\[Y==8,9\]=1

Y1\[Y==9,0\]=1

}

return(Y1)

}

\# Compute the softmax derivative

softmaxDerivative <- function(dA, cache ,y,numTraining,numClasses){

\# Note : dA not used. dL/dZ = dL/dA \* dA/dZ = pi-yi

Z <- cache

\# Compute softmax

exp\_scores = exp(t(Z))

\# normalize them for each example

probs = exp\_scores / rowSums(exp\_scores)

\# Create a matrix of zeros

Y1=popMatrix(y,numClasses)

#a=rep(0,times=length(Y))

#Y1=matrix(a,nrow=length(Y),ncol=numClasses)

#Set the rows and columns as 1's where Y is the class value

dZ = probs-Y1

return(dZ)

}

\# Initialize model for L layers

\# Input : Vector of units in each layer

\# Returns: Initial weights and biases matrices for all layers initializeDeepModel <- function(layerDimensions){

set.seed(2)

\# Initialize empty list

layerParams <- list()

\# Note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Indices in R start from 1

for(l in 2:length(layersDimensions)){

\# Initialize a matrix of small random numbers of size l x l-1

\# Create random numbers of size l x l-1

w=rnorm(layersDimensions\[l\]\*layersDimensions\[l-1\])\*0.01

\# Create a weight matrix of size l x l-1 with this initial weights and

\# Add to list W1,W2... WL

 layerParams\[\[paste('W',l-1,sep="")\]\] = matrix(w,nrow=layersDimensions\[l\], ncol=layersDimensions\[l-1\])

layerParams\[\[paste('b',l-1,sep="")\]\] = matrix(rep(0,layersDimensions\[l\]), nrow=layersDimensions\[l\],ncol=1)

}

return(layerParams)

}

\# He Initialization model for L layers

\# Input : Vector of units in each layer

\# Returns: Initial weights and biases matrices for all layers

\# He initilization multiplies the random numbers with

sqrt(2/layerDimensions\[previouslayer\])

HeInitializeDeepModel <- function(layerDimensions){

set.seed(2)

\# Initialize empty list

layerParams <- list()

\# Note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Indices in R start from 1

for(l in 2:length(layersDimensions)){

\# Initialize a matrix of small random numbers of size l x l-1

\# Create random numbers of size l x l-1

w=rnorm(layersDimensions\[l\]\*layersDimensions\[l-1\])

\# Create a weight matrix of size l x l-1 with this initial weights and

\# Add to list W1,W2... WL

\# He initialization - Divide by sqrt(2/layerDimensions\[previous layer\]) layerParams\[\[paste('W',l-1,sep="")\]\] =

matrix(w,nrow=layersDimensions\[l\],

ncol=layersDimensions\[l-

1\])\*sqrt(2/layersDimensions\[l-1\])

layerParams\[\[paste('b',l-1,sep="")\]\] = matrix(rep(0,layersDimensions\[l\]),

 nrow=layersDimensions\[l\],ncol=1)

}

return(layerParams)

}

\# XavInitializeDeepModel Initialization model for L layers

\# Input : Vector of units in each layer

\# Returns: Initial weights and biases matrices for all layers

\# He initilization multiplies the random numbers with

\# sqrt(1/layerDimensions\[previouslayer\])

XavInitializeDeepModel <- function(layerDimensions){

set.seed(2)

\# Initialize empty list

layerParams <- list()

\# Note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Indices in R start from 1

for(l in 2:length(layersDimensions)){

\# Initialize a matrix of small random numbers of size l x l-1

\# Create random numbers of size l x l-1

w=rnorm(layersDimensions\[l\]\*layersDimensions\[l-1\])

\# Create a weight matrix of size l x l-1 with this initial weights and

\# Add to list W1,W2... WL

\# He initialization - Divide by sqrt(2/layerDimensions\[previous layer\]) layerParams\[\[paste('W',l-1,sep="")\]\] =

matrix(w,nrow=layersDimensions\[l\],

ncol=layersDimensions\[l-

1\])\*sqrt(1/layersDimensions\[l-1\])

layerParams\[\[paste('b',l-1,sep="")\]\] = matrix(rep(0,layersDimensions\[l\]), nrow=layersDimensions\[l\],ncol=1)

}

return(layerParams)

}

\# Initialize velocity

\# Input : parameters

\# Returns: v -Initial velocity

initializeVelocity <- function(parameters){

L <- length(parameters)/2

v <- list()

\# Initialize velocity with the same dimensions as W

for(l in 1:L){

\# Get the size of weight matrix

sz <- dim(parameters\[\[paste('W',l,sep="")\]\])

v\[\[paste('dW',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

#Get the size of bias matrix

sz <- dim(parameters\[\[paste('b',l,sep="")\]\])

v\[\[paste('db',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

}

return(v)

}

\# Initialize RMSProp

\# Input : parameters

\# Returns: s - Initial RMSProp

initializeRMSProp <- function(parameters){

L <- length(parameters)/2

s <- list()

\# Initialize velocity with the same dimensions as W

for(l in 1:L){

\# Get the size of weight matrix

sz <- dim(parameters\[\[paste('W',l,sep="")\]\])

s\[\[paste('dW',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

#Get the size of bias matrix

 sz <- dim(parameters\[\[paste('b',l,sep="")\]\]) s\[\[paste('db',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

}

return(s)

}

\# Initialize Adam

\# Input : parameters

\# Returns: (v,s) - Initial Adam parameters

initializeAdam <- function(parameters){

L <- length(parameters)/2

v <- list()

s <- list()

\# Initialize velocity with the same dimensions as W

for(l in 1:L){

\# Get the size of weight matrix

sz <- dim(parameters\[\[paste('W',l,sep="")\]\])

v\[\[paste('dW',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

s\[\[paste('dW',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

#Get the size of bias matrix

sz <- dim(parameters\[\[paste('b',l,sep="")\]\])

v\[\[paste('db',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

s\[\[paste('db',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

}

retvals <- list("v"=v,"s"=s)

return(retvals)

}

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prev - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : The Activation of this layer

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

layerActivationForward <- function(A\_prev, W, b, activationFunc){

\# Compute Z

z = W %\*% A\_prev

\# Broadcast the bias 'b' by column

Z <-sweep(z,1,b,'+')

forward\_cache <- list("A\_prev"=A\_prev, "W"=W, "b"=b)

\# Compute the activation for sigmoid

if(activationFunc == "sigmoid"){

vals = sigmoid(Z)

} else if (activationFunc == "relu"){ # Compute the activation for relu vals = relu(Z)

} else if(activationFunc == 'tanh'){ # Compute the activation for tanh vals = tanhActivation(Z)

} else if(activationFunc == 'softmax'){

vals = softmax(Z)

}

\# Create a list of forward and activation cache

cache <- list("forward\_cache"=forward\_cache, "activation\_cache"=vals\[\['Z'\]\]) retvals <- list("A"=vals\[\['A'\]\],"cache"=cache) return(retvals)

}

\# Compute the forward propagation for layers 1..L

\# Input : X - Input Features

\# parameters: Weights and biases

\# keep\_prob

\# hiddenActivationFunc - relu/sigmoid/tanh

\# outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# Returns : AL

\# caches

\# dropoutMat

\# The forward propoagtion uses the Relu/tanh activation from layer 1..L-1 and sigmoid actiovation at layer L

forwardPropagationDeep <- function(X, parameters,keep\_prob=1, hiddenActivationFunc='relu',

outputActivationFunc='sigmoid'){

caches <- list()

dropoutMat <- list()

\# Set A to X (A0)

A <- X

L <- length(parameters)/2 # number of layers in the neural network

\# Loop through from layer 1 to upto layer L

for(l in 1:(L-1)){

A\_prev <- A

\# Zi = Wi x Ai-1 + bi and Ai = g(Zi)

\# Set W and b for layer 'l'

\# Loop throug from W1,W2... WL-1

W <- parameters\[\[paste("W",l,sep="")\]\]

b <- parameters\[\[paste("b",l,sep="")\]\]

\# Compute the forward propagation through layer 'l' using the activation function

actForward <- layerActivationForward(A\_prev,

W,

b,

activationFunc = hiddenActivationFunc)

A <- actForward\[\['A'\]\]

\# Append the cache A\_prev,W,b, Z

caches\[\[l\]\] <-actForward

\# Randomly drop some activation units

\# Create a matrix as the same shape as A

set.seed(1)

i=dim(A)\[1\]

j=dim(A)\[2\]

a<-rnorm(i\*j)

\# Normalize a between 0 and 1

a = (a - min(a))/(max(a) - min(a))

\# Create a matrix of D

D <- matrix(a,nrow=i, ncol=j)

\# Find D which is less than equal to keep\_prob

 D <- D < keep\_prob

\# Remove some A's

A <- A \* D

\# Divide by keep\_prob to keep expected value same

A <- A/keep\_prob

dropoutMat\[\[paste("D",l,sep="")\]\] <- D

}

\# Since this is binary classification use the sigmoid activation function in

\# last layer

\# Set the weights and biases for the last layer

W <- parameters\[\[paste("W",L,sep="")\]\]

b <- parameters\[\[paste("b",L,sep="")\]\]

\# Last layer

actForward = layerActivationForward(A, W, b, activationFunc =

outputActivationFunc)

AL <- actForward\[\['A'\]\]

\# Append the output of this forward propagation through the last layer caches\[\[L\]\] <- actForward

\# Create a list of the final output and the caches

fwdPropDeep <- list("AL"=AL,"caches"=caches,"dropoutMat"=dropoutMat) return(fwdPropDeep)

}

\# Function pickColumns(). This function is in computeCost()

\# Pick columns

\# Input : AL

\# : Y

\# : numClasses

\# Output: a

pickColumns <- function(AL,Y,numClasses){

if(numClasses==3){

a=c(AL\[Y==0,1\],AL\[Y==1,2\],AL\[Y==2,3\])

}

else if (numClasses==10){

a=c(AL\[Y==0,1\],AL\[Y==1,2\],AL\[Y==2,3\],AL\[Y==3,4\],AL\[Y==4,5\],

AL\[Y==5,6\],AL\[Y==6,7\],AL\[Y==7,8\],AL\[Y==8,9\],AL\[Y==9,10\])

}

 return(a)

}

\# Compute the cost

\# Input : Activation of last layer

\# : Output from data

\# :outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : numClasses

\# Output: cost

computeCost <-

function(AL,Y,outputActivationFunc="sigmoid",numClasses=3){

if(outputActivationFunc=="sigmoid"){

m= length(Y)

cost=-1/m\*sum(Y\*log(AL) + (1-Y)\*log(1-AL))

}else if (outputActivationFunc=="softmax"){

\# Select the elements where the y values are 0, 1 or 2 and make a vector

\# Pick columns

#a=c(AL\[Y==0,1\],AL\[Y==1,2\],AL\[Y==2,3\])

m= length(Y)

a =pickColumns(AL,Y,numClasses)

#a = c(A2\[y=k,k+1\])

\# Take log

correct\_probs = -log(a)

\# Compute loss

cost= sum(correct\_probs)/m

}

return(cost)

}

\# Compute the cost with Regularization

\# Input : parameters

\# : AL-Activation of last layer

\# : Y-Output from data

\# : lambd

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : numClasses

\# Output: cost

computeCostWithReg <- function(parameters, AL,Y,lambd,

outputActivationFunc="sigmoid",numClasses=3){

if(outputActivationFunc=="sigmoid"){

m= length(Y)

cost=-1/m\*sum(Y\*log(AL) + (1-Y)\*log(1-AL))

\# Regularization cost

L <- length(parameters)/2

L2RegularizationCost=0

for(l in 1:L){

L2RegularizationCost = L2RegularizationCost +

sum(parameters\[\[paste("W",l,sep="")\]\]^2)

}

L2RegularizationCost = (lambd/(2\*m))\*L2RegularizationCost

cost = cost + L2RegularizationCost

}else if (outputActivationFunc=="softmax"){

\# Select the elements where the y values are 0, 1 or 2 and make a vector

\# Pick columns

#a=c(AL\[Y==0,1\],AL\[Y==1,2\],AL\[Y==2,3\])

m= length(Y)

a =pickColumns(AL,Y,numClasses)

#a = c(A2\[y=k,k+1\])

\# Take log

correct\_probs = -log(a)

\# Compute loss

cost= sum(correct\_probs)/m

\# Regularization cost

L <- length(parameters)/2

L2RegularizationCost=0

\# Add L2 norm

for(l in 1:L){

 L2RegularizationCost = L2RegularizationCost +

sum(parameters\[\[paste("W",l,sep="")\]\]^2)

}

L2RegularizationCost = (lambd/(2\*m))\*L2RegularizationCost

cost = cost + L2RegularizationCost

}

return(cost)

}

\# Compute the backpropagation through a layer

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# # Input features

\# # Output values Y

\# # activationFunc

\# # numClasses

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

layerActivationBackward <- function(dA, cache, Y, activationFunc,numClasses)

{

\# Get A\_prev,W,b

forward\_cache <-cache\[\['forward\_cache'\]\]

activation\_cache <- cache\[\['activation\_cache'\]\]

A\_prev <- forward\_cache\[\['A\_prev'\]\]

numtraining = dim(A\_prev)\[2\]

\# Get Z

activation\_cache <- cache\[\['activation\_cache'\]\]

if(activationFunc == "relu"){

dZ <- reluDerivative(dA, activation\_cache)

} else if(activationFunc == "sigmoid"){

dZ <- sigmoidDerivative(dA, activation\_cache)

} else if(activationFunc == "tanh"){

dZ <- tanhDerivative(dA, activation\_cache)

} else if(activationFunc == "softmax"){

dZ <- softmaxDerivative(dA, activation\_cache,Y,numtraining,numClasses)

}

if (activationFunc == 'softmax'){

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

dW = 1/numtraining \* A\_prev%\*%dZ

db = 1/numtraining\* matrix(colSums(dZ),nrow=1,ncol=numClasses) dA\_prev = dZ %\*%W

} else {

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

numtraining = dim(A\_prev)\[2\]

dW = 1/numtraining \* dZ %\*% t(A\_prev)

db = 1/numtraining \* rowSums(dZ)

dA\_prev = t(W) %\*% dZ

}

retvals <- list("dA\_prev"=dA\_prev,"dW"=dW,"db"=db) return(retvals)

}

\# Compute the backpropagation through a layer with Regularization

\# Input : dA-Neural Network parameters

\# # cache - forward\_cache & activation\_cache

\# # Output values Y

\# # lambd

\# # activationFunc

\# # numClasses

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

layerActivationBackwardWithReg <- function(dA, cache, Y, lambd, activationFunc,numClasses){

\# Get A\_prev,W,b

forward\_cache <-cache\[\['forward\_cache'\]\]

activation\_cache <- cache\[\['activation\_cache'\]\]

A\_prev <- forward\_cache\[\['A\_prev'\]\]

numtraining = dim(A\_prev)\[2\]

 # Get Z

activation\_cache <- cache\[\['activation\_cache'\]\]

if(activationFunc == "relu"){

dZ <- reluDerivative(dA, activation\_cache)

} else if(activationFunc == "sigmoid"){

dZ <- sigmoidDerivative(dA, activation\_cache)

} else if(activationFunc == "tanh"){

dZ <- tanhDerivative(dA, activation\_cache)

} else if(activationFunc == "softmax"){

dZ <- softmaxDerivative(dA, activation\_cache,Y,numtraining,numClasses)

}

if (activationFunc == 'softmax'){

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

\# Add the regularization factor

dW = 1/numtraining \* A\_prev%\*%dZ + (lambd/numtraining) \* t(W) db = 1/numtraining\* matrix(colSums(dZ),nrow=1,ncol=numClasses) dA\_prev = dZ %\*%W

} else {

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

numtraining = dim(A\_prev)\[2\]

\# Add the regularization factor

dW = 1/numtraining \* dZ %\*% t(A\_prev) + (lambd/numtraining) \* W

db = 1/numtraining \* rowSums(dZ)

dA\_prev = t(W) %\*% dZ

}

retvals <- list("dA\_prev"=dA\_prev,"dW"=dW,"db"=db) return(retvals)

}

\# Compute the backpropagation for 1 cycle through all layers

\# Input : AL: Output of L layer Network - weights

\# Y Real output

\# caches -- list of caches containing:

\# every cache of layerActivationForward() with "relu"/"tanh"

\# #(it's caches\[l\], for l in range(L-1) i.e l = 0...L-2)

\# #the cache of layerActivationForward() with "sigmoid" (it's caches\[L-1\])

\# dropoutMat

\# lambd

\# keep\_prob

\# hiddenActivationFunc - Activation function at hidden layers -

relu/tanh/sigmoid

\# outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# numClasses

\# Returns:

\# gradients -- A dictionary with the gradients

\# gradients\["dA" + str(l)\]

\# gradients\["dW" + str(l)\]

\# gradients\["db" + str(l)\]

backwardPropagationDeep <- function(AL, Y, caches,dropoutMat, lambd=0, keep\_prob=0, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",numClasses){

#initialize the gradients

gradients = list()

\# Set the number of layers

L = length(caches)

numTraining = dim(AL)\[2\]

if(outputActivationFunc == "sigmoid")

\# Initializing the backpropagation

\# dl/dAL= -(y/a) - ((1-y)/(1-a)) - At the output layer

dAL = -( (Y/AL) -(1 - Y)/(1 - AL))

else if(outputActivationFunc == "softmax"){

dAL=0

Y=t(Y)

}

\# Get the gradients at the last layer

\# Inputs: "AL, Y, caches".

\# Outputs: "gradients\["dAL"\], gradients\["dWL"\], gradients\["dbL"\]

\# Start with Layer L

\# Get the current cache

current\_cache = caches\[\[L\]\]$cache

if (lambd==0){

retvals <- layerActivationBackward(dAL, current\_cache, Y,

 activationFunc = outputActivationFunc,numClasses)

} else {

retvals = layerActivationBackwardWithReg(dAL, current\_cache, Y, lambd, activationFunc = outputActivationFunc,numClasses)

}

#Note: Take the transpose of dA

if(outputActivationFunc =="sigmoid")

gradients\[\[paste("dA",L,sep="")\]\] <- retvals\[\['dA\_prev'\]\]

else if(outputActivationFunc =="softmax")

gradients\[\[paste("dA",L,sep="")\]\] <- t(retvals\[\['dA\_prev'\]\]) gradients\[\[paste("dW",L,sep="")\]\] <- retvals\[\['dW'\]\]

gradients\[\[paste("db",L,sep="")\]\] <- retvals\[\['db'\]\]

\# Traverse in the reverse direction

for(l in (L-1):1){

\# Compute the gradients for L-1 to 1 for Relu/tanh

\# Inputs: "gradients\["dA" + str(l + 2)\], caches".

\# Outputs: "gradients\["dA" + str(l + 1)\] , gradients\["dW" + str(l + 1)\] , gradients\["db" + str(l + 1)\]

current\_cache = caches\[\[l\]\]$cache

if (lambd==0){

\# Get the dropout matrix

D <-dropoutMat\[\[paste("D",l,sep="")\]\]

\# Multiply gradient with dropout matrix

gradients\[\[paste('dA',l+1,sep="")\]\] = gradients\[\[paste('dA',l+1,sep="")\]\] \*D

\# Divide by keep\_prob to keep expected value same

gradients\[\[paste('dA',l+1,sep="")\]\] =

gradients\[\[paste('dA',l+1,sep="")\]\]/keep\_prob

retvals = layerActivationBackward(gradients\[\[paste('dA',l+1,sep="")\]\], current\_cache, Y,

activationFunc = hiddenActivationFunc)

} else {

retvals =

layerActivationBackwardWithReg(gradients\[\[paste('dA',l+1,sep="")\]\], current\_cache, Y, lambd,

activationFunc = hiddenActivationFunc)

}

gradients\[\[paste("dA",l,sep="")\]\] <-retvals\[\['dA\_prev'\]\]

gradients\[\[paste("dW",l,sep="")\]\] <- retvals\[\['dW'\]\]

gradients\[\[paste("db",l,sep="")\]\] <- retvals\[\['db'\]\]

}

return(gradients)

}

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients

\# : learning rate

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

#output : Updated weights after 1 iteration

gradientDescent <- function(parameters, gradients,

learningRate,outputActivationFunc="sigmoid"){

L = length(parameters)/2 # number of layers in the neural network

\# Update rule for each parameter. Use a for loop.

for(l in 1:(L-1)){

parameters\[\[paste("W",l,sep="")\]\] = parameters\[\[paste("W",l,sep="")\]\] -

learningRate\* gradients\[\[paste("dW",l,sep="")\]\]

parameters\[\[paste("b",l,sep="")\]\] = parameters\[\[paste("b",l,sep="")\]\] -

learningRate\* gradients\[\[paste("db",l,sep="")\]\]

}

if(outputActivationFunc=="sigmoid"){

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* gradients\[\[paste("dW",L,sep="")\]\]

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* gradients\[\[paste("db",L,sep="")\]\]

}else if (outputActivationFunc=="softmax"){

 parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* t(gradients\[\[paste("dW",L,sep="")\]\]) parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* t(gradients\[\[paste("db",L,sep="")\]\])

}

return(parameters)

}

\# Perform Gradient Descent with momentum

\# Input : Weights and biases

\# : beta

\# : gradients

\# : learning rate

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

#output : Updated weights after 1 iteration

gradientDescentWithMomentum <- function(parameters, gradients,v, beta, learningRate,outputActivationFunc="sigmoid"){

L = length(parameters)/2 # number of layers in the neural network

\# Update rule for each parameter. Use a for loop.

for(l in 1:(L-1)){

\# Compute velocities

\# v\['dWk'\] = beta \*v\['dWk'\] + (1-beta)\*dWk

v\[\[paste("dW",l, sep="")\]\] = beta\*v\[\[paste("dW",l, sep="")\]\] +

(1-beta) \* gradients\[\[paste('dW',l,sep="")\]\]

v\[\[paste("db",l, sep="")\]\] = beta\*v\[\[paste("db",l, sep="")\]\] +

(1-beta) \* gradients\[\[paste('db',l,sep="")\]\]

parameters\[\[paste("W",l,sep="")\]\] = parameters\[\[paste("W",l,sep="")\]\] -

learningRate\* v\[\[paste("dW",l, sep="")\]\]

parameters\[\[paste("b",l,sep="")\]\] = parameters\[\[paste("b",l,sep="")\]\] -

learningRate\* v\[\[paste("db",l, sep="")\]\]

}

\# Compute for the Lth layer

if(outputActivationFunc=="sigmoid"){

 v\[\[paste("dW",L, sep="")\]\] = beta\*v\[\[paste("dW",L, sep="")\]\] +

(1-beta) \* gradients\[\[paste('dW',L,sep="")\]\]

v\[\[paste("db",L, sep="")\]\] = beta\*v\[\[paste("db",L, sep="")\]\] +

(1-beta) \* gradients\[\[paste('db',L,sep="")\]\]

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* v\[\[paste("dW",l, sep="")\]\]

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* v\[\[paste("db",l, sep="")\]\]

}else if (outputActivationFunc=="softmax"){

v\[\[paste("dW",L, sep="")\]\] = beta\*v\[\[paste("dW",L, sep="")\]\] +

(1-beta) \* t(gradients\[\[paste('dW',L,sep="")\]\])

v\[\[paste("db",L, sep="")\]\] = beta\*v\[\[paste("db",L, sep="")\]\] +

(1-beta) \* t(gradients\[\[paste('db',L,sep="")\]\])

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* t(gradients\[\[paste("dW",L,sep="")\]\]) parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* t(gradients\[\[paste("db",L,sep="")\]\])

}

return(parameters)

}

\# Perform Gradient Descent with RMSProp

\# Input : parameters

\# : gradients

\# : s

\# : beta1

\# : epsilon

\# : learning rate

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

#output : Updated weights after 1 iteration

gradientDescentWithRMSProp <- function(parameters, gradients,s, beta1, epsilon, learningRate,outputActivationFunc="sigmoid"){

L = length(parameters)/2 # number of layers in the neural network

\# Update rule for each parameter. Use a for loop.

for(l in 1:(L-1)){

 # Compute RMSProp

\# s\['dWk'\] = beta1 \*s\['dWk'\] + (1-beta1)\*dWk\*\*2/sqrt(s\['dWk'\])

\# Element wise multiply of gradients

s\[\[paste("dW",l, sep="")\]\] = beta1\*s\[\[paste("dW",l, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('dW',l,sep="")\]\] \*

gradients\[\[paste('dW',l,sep="")\]\]

s\[\[paste("db",l, sep="")\]\] = beta1\*s\[\[paste("db",l, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('db',l,sep="")\]\] \*

gradients\[\[paste('db',l,sep="")\]\]

parameters\[\[paste("W",l,sep="")\]\] = parameters\[\[paste("W",l,sep="")\]\] -

learningRate \* gradients\[\[paste('dW',l,sep="")\]\]/sqrt(s\[\[paste("dW",l, sep="")\]\]+epsilon)

parameters\[\[paste("b",l,sep="")\]\] = parameters\[\[paste("b",l,sep="")\]\] -

learningRate\*gradients\[\[paste('db',l,sep="")\]\]/sqrt(s\[\[paste("db",l, sep="")\]\]+epsilon)

}

\# Compute for the Lth layer

if(outputActivationFunc=="sigmoid"){

s\[\[paste("dW",L, sep="")\]\] = beta1\*s\[\[paste("dW",L, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('dW',L,sep="")\]\]

\*gradients\[\[paste('dW',L,sep="")\]\]

s\[\[paste("db",L, sep="")\]\] = beta1\*s\[\[paste("db",L, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('db',L,sep="")\]\] \*

gradients\[\[paste('db',L,sep="")\]\]

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* gradients\[\[paste('dW',l,sep="")\]\]/sqrt(s\[\[paste("dW",L, sep="")\]\]+epsilon)

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* gradients\[\[paste('db',l,sep="")\]\]/sqrt( s\[\[paste("db",L, sep="")\]\]+epsilon)

}else if (outputActivationFunc=="softmax"){

s\[\[paste("dW",L, sep="")\]\] = beta1\*s\[\[paste("dW",L, sep="")\]\] +

(1-beta1) \* t(gradients\[\[paste('dW',L,sep="")\]\]) \*

t(gradients\[\[paste('dW',L,sep="")\]\])

s\[\[paste("db",L, sep="")\]\] = beta1\*s\[\[paste("db",L, sep="")\]\] +

 (1-beta1) \* t(gradients\[\[paste('db',L,sep="")\]\]) \*

t(gradients\[\[paste('db',L,sep="")\]\])

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\*

t(gradients\[\[paste("dW",L,sep="")\]\])/sqrt(s\[\[paste("dW",L, sep="")\]\]+epsilon) parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* t(gradients\[\[paste("db",L,sep="")\]\])/sqrt( s\[\[paste("db",L, sep="")\]\]+epsilon)

}

return(parameters)

}

\# Perform Gradient Descent with Adam

\# Input : parameters

\# : gradients

\# : v

\# : s

\# : t

\# : beta1

\# : beta2

\# : epsilon

\# : learning rate

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

#output : Updated weights after 1 iteration

gradientDescentWithAdam <- function(parameters, gradients,v, s, t, beta1=0.9, beta2=0.999, epsilon=10^-8,

learningRate=0.1,outputActivationFunc="sigmoid"){

L = length(parameters)/2 # number of layers in the neural network v\_corrected <- list()

s\_corrected <- list()

\# Update rule for each parameter. Use a for loop.

for(l in 1:(L-1)){

\# v\['dWk'\] = beta \*v\['dWk'\] + (1-beta)\*dWk

v\[\[paste("dW",l, sep="")\]\] = beta1\*v\[\[paste("dW",l, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('dW',l,sep="")\]\]

 v\[\[paste("db",l, sep="")\]\] = beta1\*v\[\[paste("db",l, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('db',l,sep="")\]\]

\# Compute bias-corrected first moment estimate.

v\_corrected\[\[paste("dW",l, sep="")\]\] = v\[\[paste("dW",l, sep="")\]\]/(1-beta1^t)

v\_corrected\[\[paste("db",l, sep="")\]\] = v\[\[paste("db",l, sep="")\]\]/(1-beta1^t)

\# Element wise multiply of gradients

s\[\[paste("dW",l, sep="")\]\] = beta2\*s\[\[paste("dW",l, sep="")\]\] +

(1-beta2) \* gradients\[\[paste('dW',l,sep="")\]\] \*

gradients\[\[paste('dW',l,sep="")\]\]

s\[\[paste("db",l, sep="")\]\] = beta2\*s\[\[paste("db",l, sep="")\]\] +

(1-beta2) \* gradients\[\[paste('db',l,sep="")\]\] \*

gradients\[\[paste('db',l,sep="")\]\]

\# Compute bias-corrected second moment estimate.

s\_corrected\[\[paste("dW",l, sep="")\]\] = s\[\[paste("dW",l, sep="")\]\]/(1-beta2^t)

s\_corrected\[\[paste("db",l, sep="")\]\] = s\[\[paste("db",l, sep="")\]\]/(1-beta2^t)

\# Update parameters.

d1=sqrt(s\_corrected\[\[paste("dW",l, sep="")\]\]+epsilon) d2=sqrt(s\_corrected\[\[paste("db",l, sep="")\]\]+epsilon) parameters\[\[paste("W",l,sep="")\]\] = parameters\[\[paste("W",l,sep="")\]\] -

learningRate \* v\_corrected\[\[paste("dW",l, sep="")\]\]/d1

parameters\[\[paste("b",l,sep="")\]\] = parameters\[\[paste("b",l,sep="")\]\] -

learningRate\*v\_corrected\[\[paste("db",l, sep="")\]\]/d2

}

\# Compute for the Lth layer

if(outputActivationFunc=="sigmoid"){

v\[\[paste("dW",L, sep="")\]\] = beta1\*v\[\[paste("dW",L, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('dW',L,sep="")\]\]

v\[\[paste("db",L, sep="")\]\] = beta1\*v\[\[paste("db",L, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('db',L,sep="")\]\]

\# Compute bias-corrected first moment estimate.

v\_corrected\[\[paste("dW",L, sep="")\]\] = v\[\[paste("dW",L, sep="")\]\]/(1-beta1^t)

v\_corrected\[\[paste("db",L, sep="")\]\] = v\[\[paste("db",L, sep="")\]\]/(1-beta1^t)

\# Element wise multiply of gradients

s\[\[paste("dW",L, sep="")\]\] = beta2\*s\[\[paste("dW",L, sep="")\]\] +

(1-beta2) \* gradients\[\[paste('dW',L,sep="")\]\] \*

gradients\[\[paste('dW',L,sep="")\]\]

s\[\[paste("db",L, sep="")\]\] = beta2\*s\[\[paste("db",L, sep="")\]\] +

(1-beta2) \* gradients\[\[paste('db',L,sep="")\]\] \*

gradients\[\[paste('db',L,sep="")\]\]

\# Compute bias-corrected second moment estimate.

s\_corrected\[\[paste("dW",L, sep="")\]\] = s\[\[paste("dW",L, sep="")\]\]/(1-beta2^t)

s\_corrected\[\[paste("db",L, sep="")\]\] = s\[\[paste("db",L, sep="")\]\]/(1-beta2^t)

\# Update parameters.

d1=sqrt(s\_corrected\[\[paste("dW",L, sep="")\]\]+epsilon) d2=sqrt(s\_corrected\[\[paste("db",L, sep="")\]\]+epsilon) parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate \* v\_corrected\[\[paste("dW",L, sep="")\]\]/d1

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\*v\_corrected\[\[paste("db",L, sep="")\]\]/d2

}else if (outputActivationFunc=="softmax"){

v\[\[paste("dW",L, sep="")\]\] = beta1\*v\[\[paste("dW",L, sep="")\]\] +

(1-beta1) \* t(gradients\[\[paste('dW',L,sep="")\]\])

v\[\[paste("db",L, sep="")\]\] = beta1\*v\[\[paste("db",L, sep="")\]\] +

(1-beta1) \* t(gradients\[\[paste('db',L,sep="")\]\])

\# Compute bias-corrected first moment estimate.

 v\_corrected\[\[paste("dW",L, sep="")\]\] = v\[\[paste("dW",L, sep="")\]\]/(1-beta1^t)

v\_corrected\[\[paste("db",L, sep="")\]\] = v\[\[paste("db",L, sep="")\]\]/(1-beta1^t)

\# Element wise multiply of gradients

s\[\[paste("dW",L, sep="")\]\] = beta2\*s\[\[paste("dW",L, sep="")\]\] +

(1-beta2) \* t(gradients\[\[paste('dW',L,sep="")\]\]) \*

t(gradients\[\[paste('dW',L,sep="")\]\])

s\[\[paste("db",L, sep="")\]\] = beta2\*s\[\[paste("db",L, sep="")\]\] +

(1-beta2) \* t(gradients\[\[paste('db',L,sep="")\]\]) \*

t(gradients\[\[paste('db',L,sep="")\]\])

\# Compute bias-corrected second moment estimate.

s\_corrected\[\[paste("dW",L, sep="")\]\] = s\[\[paste("dW",L, sep="")\]\]/(1-beta2^t)

s\_corrected\[\[paste("db",L, sep="")\]\] = s\[\[paste("db",L, sep="")\]\]/(1-beta2^t)

\# Update parameters.

d1=sqrt(s\_corrected\[\[paste("dW",L, sep="")\]\]+epsilon) d2=sqrt(s\_corrected\[\[paste("db",L, sep="")\]\]+epsilon) parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate \* v\_corrected\[\[paste("dW",L, sep="")\]\]/d1

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\*v\_corrected\[\[paste("db",L, sep="")\]\]/d2

}

return(parameters)

}

\# Execute a L layer Deep learning model

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu /tanh

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : learning rate

\# : lambd

\# : keep\_prob

\# : learning rate

\# : num of iterations

\# : initType

#output : Updated weights

L\_Layer\_DeepModel <- function(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc= 'sigmoid',

learningRate = 0.5,

lambd=0,

keep\_prob=1,

numIterations = 10000,

initType="default",

print\_cost=False){

#Initialize costs vector as NULL

costs <- NULL

\# Parameters initialization.

if (initType=="He"){

parameters =HeInitializeDeepModel(layersDimensions)

} else if (initType=="Xav"){

parameters =XavInitializeDeepModel(layersDimensions)

}

else{

parameters = initializeDeepModel(layersDimensions)

}

\# Loop (gradient descent)

for( i in 0:numIterations){

\# Forward propagation: \[LINEAR -> RELU\]\*(L-1) -> LINEAR -> SIGMOID/SOFTMAX.

retvals = forwardPropagationDeep(X, parameters,keep\_prob,

hiddenActivationFunc,

outputActivationFunc=outputActivationFunc)

AL <- retvals\[\['AL'\]\]

caches <- retvals\[\['caches'\]\]

 dropoutMat <- retvals\[\['dropoutMat'\]\]

\# Compute cost.

if(lambd==0){

cost <- computeCost(AL,

Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

} else {

cost <- computeCostWithReg(parameters, AL, Y,lambd,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

}

\# Backward propagation.

gradients = backwardPropagationDeep(AL, Y, caches, dropoutMat, lambd, keep\_prob, hiddenActivationFunc,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

\# Update parameters.

parameters = gradientDescent(parameters, gradients, learningRate, outputActivationFunc=outputActivationFunc)

if(i%%1000 == 0){

costs=c(costs,cost)

print(cost)

}

}

retvals <- list("parameters"=parameters,"costs"=costs) return(retvals)

}

\# Execute a L layer Deep learning model with Stochastic Gradient descent

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu /tanh

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : learning rate

\# : lrDecay

\# : decayRate

\# : lambd

\# : keep\_prob

\# : optimizer

\# : beta

\# : beta1

\# : beta2

\# : epsilon

\# : mini\_batch\_size

\# : num of epochs

#output : Updated weights after each iteration

L\_Layer\_DeepModel\_SGD <- function(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc= 'sigmoid',

learningRate = .3,

lrDecay=FALSE,

decayRate=1,

lambd=0,

keep\_prob=1,

optimizer="gd",

beta=0.9,

beta1=0.9,

beta2=0.999,

epsilon=10^-8,

mini\_batch\_size = 64,

num\_epochs = 2500,

print\_cost=False){

\# Check the values

cat("learningRate= ",learningRate)

cat("\\n")

cat("lambd=",lambd)

cat("\\n")

cat("keep\_prob=",keep\_prob)

cat("\\n")

cat("optimizer=",optimizer)

cat("\\n")

cat("lrDecay=",lrDecay)

 cat("\\n")

cat("decayRate=",decayRate)

cat("\\n")

cat("beta=",beta)

cat("\\n")

cat("beta1=",beta1)

cat("\\n")

cat("beta2=",beta2)

cat("\\n")

cat("epsilon=",epsilon)

cat("\\n")

cat("mini\_batch\_size=",mini\_batch\_size)

cat("\\n")

cat("num\_epochs=",num\_epochs)

cat("\\n")

set.seed(1)

#Initialize costs vector as NULL

costs <- NULL

t <- 0

\# Parameters initialization.

parameters = initializeDeepModel(layersDimensions)

#Initialize the optimizer

if(optimizer == "momentum"){

v <-initializeVelocity(parameters)

} else if(optimizer == "rmsprop"){

s <-initializeRMSProp(parameters)

} else if (optimizer == "adam"){

adamVals <-initializeAdam(parameters)

}

seed=10

\# Loop for number of epochs

for( i in 0:num\_epochs){

seed=seed+1

minibatches = random\_mini\_batches(X, Y, mini\_batch\_size, seed)

 for(batch in 1:length(minibatches)){

mini\_batch\_X=minibatches\[\[batch\]\]\[\['mini\_batch\_X'\]\]

mini\_batch\_Y=minibatches\[\[batch\]\]\[\['mini\_batch\_Y'\]\]

\# Forward propagation:

retvals = forwardPropagationDeep(mini\_batch\_X, parameters,keep\_prob, hiddenActivationFunc,

outputActivationFunc=outputActivationFunc)

AL <- retvals\[\['AL'\]\]

caches <- retvals\[\['caches'\]\]

dropoutMat <- retvals\[\['dropoutMat'\]\]

\# Compute cost.

\# Compute cost.

if(lambd==0){

cost <- computeCost(AL,

mini\_batch\_Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

} else {

cost <- computeCostWithReg(parameters, AL, Y,lambd,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

}

\# Backward propagation.

gradients = backwardPropagationDeep(AL, mini\_batch\_Y, caches, dropoutMat, lambd, keep\_prob, hiddenActivationFunc,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\]) if(optimizer == "gd"){

\# Update parameters.

parameters = gradientDescent(parameters, gradients, learningRate, outputActivationFunc=outputActivationFunc)

}else if(optimizer == "momentum"){

\# Update parameters with Momentum

parameters = gradientDescentWithMomentum(parameters,

gradients,v,beta, learningRate,

outputActivationFunc=outputActivationFunc)

} else if(optimizer == "rmsprop"){

\# Update parameters with RMSProp

 parameters = gradientDescentWithRMSProp(parameters, gradients,s,beta1, epsilon,learningRate,

outputActivationFunc=outputActivationFunc)

} else if(optimizer == "adam"){

\# Update parameters with Adam

#Get v and s

t <- t+1

v <- adamVals\[\['v'\]\]

s <- adamVals\[\['s'\]\]

parameters = gradientDescentWithAdam(parameters, gradients,v, s,t, beta1,beta2, epsilon,learningRate,

outputActivationFunc=outputActivationFunc)

}

}

if(i%%1000 == 0){

costs=c(costs,cost)

print(cost)

}

if(lrDecay==TRUE){

learningRate = decayRate^(num\_epochs/1000) \* learningRate

}

}

retvals <- list("parameters"=parameters,"costs"=costs) return(retvals)

}

\# Predict the output for given input

\# Input : parameters

\# : X

\# Output: predictions

predict <- function(parameters, X,keep\_prob=1, hiddenActivationFunc='relu'){

fwdProp <- forwardPropagationDeep(X, parameters,keep\_prob, hiddenActivationFunc)

predictions <- fwdProp$AL>0.5

return (predictions)

}

\# Plot a decision boundary

\# This function uses ggplot2

plotDecisionBoundary <-

function(z,retvals,keep\_prob=1,hiddenActivationFunc="sigmoid",lr=0.5){

\# Find the minimum and maximum for the data

xmin<-min(z\[,1\])

xmax<-max(z\[,1\])

ymin<-min(z\[,2\])

ymax<-max(z\[,2\])

\# Create a grid of values

a=seq(xmin,xmax,length=100)

b=seq(ymin,ymax,length=100)

grid <- expand.grid(x=a, y=b)

colnames(grid) <- c('x1', 'x2')

grid1 <-t(grid)

\# Predict the output for this grid

q <-predict(retvals$parameters,grid1,keep\_prob=1, hiddenActivationFunc) q1 <- t(data.frame(q))

q2 <- as.numeric(q1)

grid2 <- cbind(grid,q2)

colnames(grid2) <- c('x1', 'x2','q2')

z1 <- data.frame(z)

names(z1) <- c("x1","x2","y") atitle=paste("Decision boundary for learning rate:",lr)

\# Plot the contour of the boundary

ggplot(z1) +

geom\_point(data = z1, aes(x = x1, y = x2, color = y)) +

stat\_contour(data = grid2, aes(x = x1, y = x2, z = q2,color=q2), alpha = 0.9)+

ggtitle(atitle) + scale\_colour\_gradientn(colours = brewer.pal(10, "Spectral"))

}

\# Predict the probability scores for given data set

\# Input : parameters

\# : X

\# Output: probability of output

computeScores <- function(parameters, X,hiddenActivationFunc='relu'){

fwdProp <- forwardPropagationDeep(X, parameters,hiddenActivationFunc) scores <- fwdProp$AL

return (scores)

}

\# Create random mini batches

\# Input : X - Input features

\# : Y- output

\# : miniBatchSize

\# : seed

#output : mini\_batches

random\_mini\_batches <- function(X, Y, miniBatchSize = 64, seed = 0){

set.seed(seed)

\# Get number of training samples

m = dim(X)\[2\]

\# Initialize mini batches

mini\_batches = list()

\# Create a list of random numbers < m

permutation = c(sample(m))

\# Randomly shuffle the training data

shuffled\_X = X\[, permutation\]

shuffled\_Y = Y\[1, permutation\]

\# Compute number of mini batches

numCompleteMinibatches = floor(m/miniBatchSize)

batch=0

for(k in 0:(numCompleteMinibatches-1)){

batch=batch+1

\# Set the lower and upper bound of the mini batches

lower=(k\*miniBatchSize)+1

upper=((k+1) \* miniBatchSize)

 mini\_batch\_X = shuffled\_X\[, lower:upper\]

mini\_batch\_Y = shuffled\_Y\[lower:upper\]

\# Add it to the list of mini batches

mini\_batch =

list("mini\_batch\_X"=mini\_batch\_X,"mini\_batch\_Y"=mini\_batch\_Y) mini\_batches\[\[batch\]\] =mini\_batch

}

\# If the batch size does not divide evenly with mini batc size if(m %% miniBatchSize != 0){

p=floor(m/miniBatchSize)\*miniBatchSize

\# Set the start and end of last batch

q=p+m %% miniBatchSize

mini\_batch\_X = shuffled\_X\[,(p+1):q\]

mini\_batch\_Y = shuffled\_Y\[(p+1):q\]

}

\# Return the list of mini batches

mini\_batch =

list("mini\_batch\_X"=mini\_batch\_X,"mini\_batch\_Y"=mini\_batch\_Y) mini\_batches\[\[batch\]\]=mini\_batch

return(mini\_batches)

}

\# Plot a decision boundary

\# This function uses ggplot2

plotDecisionBoundary1 <- function(Z,parameters,keep\_prob=1){

xmin<-min(Z\[,1\])

xmax<-max(Z\[,1\])

ymin<-min(Z\[,2\])

ymax<-max(Z\[,2\])

\# Create a grid of points

a=seq(xmin,xmax,length=100)

b=seq(ymin,ymax,length=100)

grid <- expand.grid(x=a, y=b)

colnames(grid) <- c('x1', 'x2')

 grid1 <-t(grid)

retvals = forwardPropagationDeep(grid1, parameters,keep\_prob, "relu", outputActivationFunc="softmax")

AL <- retvals$AL

\# From the softmax probabilities pick the one with the highest probability q= apply(AL,1,which.max)

q1 <- t(data.frame(q))

q2 <- as.numeric(q1)

grid2 <- cbind(grid,q2)

colnames(grid2) <- c('x1', 'x2','q2')

Z1 <- data.frame(Z)

names(Z1) <- c("x1","x2","y") atitle=paste("Decision boundary")

ggplot(Z1) +

geom\_point(data = Z1, aes(x = x1, y = x2, color = y)) +

stat\_contour(data = grid2, aes(x = x1, y = x2, z = q2,color=q2), alpha =

0.9)+

ggtitle(atitle) + scale\_colour\_gradientn(colours = brewer.pal(10,

"Spectral"))

}

**7.3 Octave**

############################################################################################################

#

\# File : DLfunctions7.R

\# Author : Tinniam V Ganesh

\# Date : 16 Apr 2018

#

##########################################################################################################

1;

\# Define sigmoid function

function \[A,cache\] = sigmoid(Z)

A = 1 ./ (1+ exp(-Z));

cache=Z;

end

\# Define Relu function

function \[A,cache\] = relu(Z)

A = max(0,Z);

cache=Z;

end

\# Define Relu function

function \[A,cache\] = tanhAct(Z)

A = tanh(Z);

cache=Z;

end

\# Define Softmax function

function \[A,cache\] = softmax(Z)

\# get unnormalized probabilities

exp\_scores = exp(Z');

\# normalize them for each example

A = exp\_scores ./ sum(exp\_scores,2);

cache=Z;

end

\# Define Stable Softmax function

function \[A,cache\] = stableSoftmax(Z)

\# Normalize by max value in each row

shiftZ = Z' - max(Z',\[\],2);

exp\_scores = exp(shiftZ);

\# normalize them for each example

A = exp\_scores ./ sum(exp\_scores,2);

#disp("sm")

#disp(A);

cache=Z;

end

\# Define Relu Derivative

function \[dZ\] = reluDerivative(dA,cache)

Z = cache;

dZ = dA;

\# Get elements that are greater than 0

a = (Z > 0);

\# Select only those elements where Z > 0

dZ = dZ .\* a;

end

\# Define Sigmoid Derivative

function \[dZ\] = sigmoidDerivative(dA,cache)

Z = cache;

s = 1 ./ (1+ exp(-Z));

dZ = dA .\* s .\* (1-s);

end

\# Define Tanh Derivative

function \[dZ\] = tanhDerivative(dA,cache)

Z = cache;

a = tanh(Z);

dZ = dA .\* (1 - a .^ 2);

end

\# Populate a matrix with 1s in rows where Y=1

\# This function may need to be modified if K is not 3, 10

\# This function is used in computing the softmax derivative

function \[Y1\] = popMatrix(Y,numClasses)

Y1=zeros(length(Y),numClasses);

if(numClasses==3) # For 3 output classes

Y1(Y==0,1)=1;

Y1(Y==1,2)=1;

Y1(Y==2,3)=1;

elseif(numClasses==10) # For 10 output classes

Y1(Y==0,1)=1;

Y1(Y==1,2)=1;

Y1(Y==2,3)=1;

Y1(Y==3,4)=1;

Y1(Y==4,5)=1;

Y1(Y==5,6)=1;

Y1(Y==6,7)=1;

Y1(Y==7,8)=1;

Y1(Y==8,9)=1;

Y1(Y==9,10)=1;

endif

end

\# Define Softmax Derivative

function \[dZ\] = softmaxDerivative(dA,cache,Y, numClasses)

Z = cache;

\# get unnormalized probabilities

shiftZ = Z' - max(Z',\[\],2);

exp\_scores = exp(shiftZ);

\# normalize them for each example

probs = exp\_scores ./ sum(exp\_scores,2);

\# dZ = pi- yi

yi=popMatrix(Y,numClasses);

dZ=probs-yi;

end

\# Define Stable Softmax Derivative

function \[dZ\] = stableSoftmaxDerivative(dA,cache,Y, numClasses) Z = cache;

 # get unnormalized probabilities

exp\_scores = exp(Z');

\# normalize them for each example

probs = exp\_scores ./ sum(exp\_scores,2);

\# dZ = pi- yi

yi=popMatrix(Y,numClasses);

dZ=probs-yi;

end

\# Initialize model for L layers

\# Input : Vector of units in each layer

\# Returns: Initial weights and biases matrices for all layers function \[W b\] = initializeDeepModel(layerDimensions)

rand ("seed", 3);

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Create cell arrays for Weights and biases

for l =2:size(layerDimensions)(2)

W{l-1} = rand(layerDimensions(l),layerDimensions(l-1))\*0.01; #

Multiply by .01

b{l-1} = zeros(layerDimensions(l),1);

endfor

end

\# He Initialization for L layers

\# Input : Vector of units in each layer

\# Returns: Initial weights and biases matrices for all layers function \[W b\] = HeInitializeDeepModel(layerDimensions)

rand ("seed", 3);

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Create cell arrays for Weights and biases

for l =2:size(layerDimensions)(2)

W{l-1} = rand(layerDimensions(l),layerDimensions(l-1))\*

sqrt(2/layerDimensions(l-1)); # Multiply by .01

b{l-1} = zeros(layerDimensions(l),1);

endfor

end

\# Xavier Initialization for L layers

\# Input : Vector of units in each layer

\# Returns: Initial weights and biases matrices for all layers function \[W b\] = XavInitializeDeepModel(layerDimensions)

rand ("seed", 3);

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Create cell arrays for Weights and biases

for l =2:size(layerDimensions)(2)

W{l-1} = rand(layerDimensions(l),layerDimensions(l-1))\*

sqrt(1/layerDimensions(l-1)); # Multiply by .01

b{l-1} = zeros(layerDimensions(l),1);

endfor

end

\# Initialize velocity

\# Input : weights, biases

\# Returns: vdW, vdB - Initial velocity

function\[vdW vdB\] = initializeVelocity(weights, biases)

L = size(weights)(2) # Create an integer

\# Initialize a cell array

v = {}

\# Initialize velocity with the same dimensions as W

for l=1:L

 sz = size(weights{l});

vdW{l} = zeros(sz(1),sz(2));

sz = size(biases{l});

vdB{l} =zeros(sz(1),sz(2));

endfor;

end

\# Initialize RMSProp

\# Input : weights, biases

\# Returns: sdW, sdB - Initial RMSProp

function\[sdW sdB\] = initializeRMSProp(weights, biases)

L = size(weights)(2) # Create an integer

\# Initialize a cell array

s = {}

\# Initialize velocity with the same dimensions as W

for l=1:L

sz = size(weights{l});

sdW{l} = zeros(sz(1),sz(2));

sz = size(biases{l});

sdB{l} =zeros(sz(1),sz(2));

endfor;

end

\# Initialize Adam

\# Input : parameters

\# Returns: vdW, vdB, sdW, sdB -Initial Adam

function\[vdW vdB sdW sdB\] = initializeAdam(weights, biases)

L = size(weights)(2) # Create an integer

\# Initialize a cell array

s = {}

\# Initialize velocity with the same dimensions as W

for l=1:L

sz = size(weights{l});

vdW{l} = zeros(sz(1),sz(2));

sdW{l} = zeros(sz(1),sz(2));

 sz = size(biases{l});

sdB{l} =zeros(sz(1),sz(2));

vdB{l} =zeros(sz(1),sz(2));

endfor;

end

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prev - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : The Activation of this layer

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

function \[A forward\_cache activation\_cache\] = layerActivationForward(A\_prev, W, b, activationFunc)

\# Compute Z

Z = W \* A\_prev +b;

\# Create a cell array

forward\_cache = {A\_prev W b};

\# Compute the activation for sigmoid

if (strcmp(activationFunc,"sigmoid"))

\[A activation\_cache\] = sigmoid(Z);

elseif (strcmp(activationFunc, "relu")) # Compute the activation for Relu

\[A activation\_cache\] = relu(Z);

elseif(strcmp(activationFunc,'tanh')) # Compute the activation for tanh

\[A activation\_cache\] = tanhAct(Z);

elseif(strcmp(activationFunc,'softmax')) # Compute the activation for tanh

#\[A activation\_cache\] = softmax(Z);

\[A activation\_cache\] = stableSoftmax(Z);

endif

end

\# Compute the forward propagation for layers 1..L

\# Input : X - Input Features

\# parameters: Weights and biases

\# keep\_prob

\# hiddenActivationFunc - Activation function at hidden layers Relu/tanh/sigmoid

\# outputActivationFunc- sigmoid/softmax

\# Returns : AL, forward,\_caches, activation\_caches, dropoutMat

\# The forward propoagtion uses the Relu/tanh activation from layer 1..L-1 and sigmoid actiovation at layer L

function \[AL forward\_caches activation\_caches dropoutMat\] =

forwardPropagationDeep(X, weights,biases, keep\_prob=1,

hiddenActivationFunc='relu',

outputActivationFunc='sigmoid')

\# Create an empty cell array

forward\_caches = {};

activation\_caches = {};

droputMat ={};

\# Set A to X (A0)

A = X;

L = length(weights); # number of layers in the neural network

\# Loop through from layer 1 to upto layer L

for l =1:L-1

A\_prev = A;

\# Zi = Wi x Ai-1 + bi and Ai = g(Zi)

W = weights{l};

b = biases{l};

\[A forward\_cache activation\_cache\] = layerActivationForward(A\_prev, W,b, activationFunc=hiddenActivationFunc);

D=rand(size(A)(1),size(A)(2));

D = (D < keep\_prob) ;

\# Multiply by DropoutMat

A= A .\* D;

\# Divide by keep\_prob to keep expected value same

A = A ./ keep\_prob;

\# Store D

dropoutMat{l}=D;

forward\_caches{l}=forward\_cache;

activation\_caches{l} = activation\_cache;

endfor

\# Since this is binary classification use the sigmoid activation function in

\# last layer

W = weights{L};

 b = biases{L};

\[AL, forward\_cache activation\_cache\] = layerActivationForward(A, W,b, activationFunc = outputActivationFunc);

forward\_caches{L}=forward\_cache;

activation\_caches{L} = activation\_cache;

end

\# Pick columns where Y==1

\# This function is used in computeCost

function \[a\] = pickColumns(AL,Y,numClasses)

if(numClasses==3)

a=\[AL(Y==0,1) ;AL(Y==1,2) ;AL(Y==2,3)\];

elseif (numClasses==10)

a=\[AL(Y==0,1) ;AL(Y==1,2) ;AL(Y==2,3);AL(Y==3,4);AL(Y==4,5);

AL(Y==5,6); AL(Y==6,7);AL(Y==7,8);AL(Y==8,9);AL(Y==9,10)\];

endif

end

\# Compute the cost

\# Input : AL-Activation of last layer

\# : Y-Output from data

\# : outputActivationFunc- sigmoid/softmax

\# : numClasses

\# Output: cost

function \[cost\]= computeCost(AL, Y,

outputActivationFunc="sigmoid",numClasses)

if(strcmp(outputActivationFunc,"sigmoid"))

numTraining= size(Y)(2);

\# Element wise multiply for logprobs

cost = -1/numTraining \* sum((Y .\* log(AL)) + (1-Y) .\* log(1-AL)); elseif(strcmp(outputActivationFunc,'softmax'))

numTraining = size(Y)(2);

Y=Y';

\# Select rows where Y=0,1,and 2 and concatenate to a long vector

#a=\[AL(Y==0,1) ;AL(Y==1,2) ;AL(Y==2,3)\];

 a =pickColumns(AL,Y,numClasses);

#Select the correct column for log prob

correct\_probs = -log(a);

#Compute log loss

cost= sum(correct\_probs)/numTraining;

endif

end

\# Compute the cost with regularization

\# Input : weights

\# : AL - Activation of last layer

\# : Output from data

\# : lambd

\# : outputActivationFunc- sigmoid/softmax

\# : numClasses

\# Output: cost

function \[cost\]= computeCostWithReg(weights, AL, Y, lambd,

outputActivationFunc="sigmoid",numClasses)

if(strcmp(outputActivationFunc,"sigmoid"))

numTraining= size(Y)(2);

\# Element wise multiply for logprobs

cost = -1/numTraining \* sum((Y .\* log(AL)) + (1-Y) .\* log(1-AL));

\# Regularization cost

L = size(weights)(2);

L2RegularizationCost=0;

for l=1:L

wtSqr = weights{l} .\* weights{l};

#disp(sum(sum(wtSqr,1)));

L2RegularizationCost+=sum(sum(wtSqr,1));

endfor

L2RegularizationCost = (lambd/(2\*numTraining))\*L2RegularizationCost; cost = cost + L2RegularizationCost ;

elseif(strcmp(outputActivationFunc,'softmax'))

numTraining = size(Y)(2);

 Y=Y';

\# Select rows where Y=0,1,and 2 and concatenate to a long vector

#a=\[AL(Y==0,1) ;AL(Y==1,2) ;AL(Y==2,3)\];

a =pickColumns(AL,Y,numClasses);

#Select the correct column for log prob

correct\_probs = -log(a);

#Compute log loss

cost= sum(correct\_probs)/numTraining;

\# Regularization cost

L = size(weights)(2);

L2RegularizationCost=0;

for l=1:L

\# Compute L2 Norm

wtSqr = weights{l} .\* weights{l};

#disp(sum(sum(wtSqr,1)));

L2RegularizationCost+=sum(sum(wtSqr,1));

endfor

L2RegularizationCost = (lambd/(2\*numTraining))\*L2RegularizationCost; cost = cost + L2RegularizationCost ;

endif

end

\# Compute the backpropoagation for 1 cycle

\# Input : dA- Neural Network parameters

\# # cache - forward\_cache & activation\_cache

\# # Y-Output values

\# # outputActivationFunc- sigmoid/softmax

\# # numClasses

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

function \[dA\_prev dW db\] = layerActivationBackward(dA, forward\_cache, activation\_cache, Y, activationFunc,numClasses)

A\_prev = forward\_cache{1};

 W =forward\_cache{2};

b = forward\_cache{3};

numTraining = size(A\_prev)(2);

if (strcmp(activationFunc,"relu"))

dZ = reluDerivative(dA, activation\_cache);

elseif (strcmp(activationFunc,"sigmoid"))

dZ = sigmoidDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "tanh"))

dZ = tanhDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "softmax"))

#dZ = softmaxDerivative(dA, activation\_cache,Y,numClasses);

dZ = stableSoftmaxDerivative(dA, activation\_cache,Y,numClasses); endif

if (strcmp(activationFunc,"softmax"))

W =forward\_cache{2};

b = forward\_cache{3};

\# Add the regularization factor

dW = 1/numTraining \* A\_prev \* dZ;

db = 1/numTraining \* sum(dZ,1);

dA\_prev = dZ\*W;

else

W =forward\_cache{2};

b = forward\_cache{3};

\# Add the regularization factor

dW = 1/numTraining \* dZ \* A\_prev';

db = 1/numTraining \* sum(dZ,2);

dA\_prev = W'\*dZ;

endif

end

\# Compute the backpropoagation with regularization for 1 cycle

\# Input : dA-Neural Network parameters

\# # cache - forward\_cache & activation\_cache

\# # Y-Output values

\# # lambd

\# # outputActivationFunc- sigmoid/softmax

\# # numClasses

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

function \[dA\_prev dW db\] = layerActivationBackwardWithReg(dA, forward\_cache, activation\_cache, Y, lambd=0, activationFunc,numClasses) A\_prev = forward\_cache{1};

W =forward\_cache{2};

b = forward\_cache{3};

numTraining = size(A\_prev)(2);

if (strcmp(activationFunc,"relu"))

dZ = reluDerivative(dA, activation\_cache);

elseif (strcmp(activationFunc,"sigmoid"))

dZ = sigmoidDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "tanh"))

dZ = tanhDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "softmax"))

#dZ = softmaxDerivative(dA, activation\_cache,Y,numClasses);

dZ = stableSoftmaxDerivative(dA, activation\_cache,Y,numClasses); endif

if (strcmp(activationFunc,"softmax"))

W =forward\_cache{2};

b = forward\_cache{3};

\# Add the regularization factor

dW = 1/numTraining \* A\_prev \* dZ + (lambd/numTraining) \* W'; db = 1/numTraining \* sum(dZ,1);

dA\_prev = dZ\*W;

else

W =forward\_cache{2};

b = forward\_cache{3};

\# Add the regularization factor

dW = 1/numTraining \* dZ \* A\_prev' + (lambd/numTraining) \* W; db = 1/numTraining \* sum(dZ,2);

dA\_prev = W'\*dZ;

endif

end

\# Compute the backpropoagation for 1 cycle

\# Input : AL: Output of L layer Network - weights

\# Y Real output

\# caches -- list of caches containing:

\# every cache of layerActivationForward() with "relu"/"tanh"

\# #(it's caches\[l\], for l in range(L-1) i.e l = 0...L-2)

\# #the cache of layerActivationForward() with "sigmoid" (it's caches\[L-1\])

\# dropoutMat

\# lambd

\# keep\_prob

\# hiddenActivationFunc - Activation function at hidden layers sigmoid/tanh/relu

\# outputActivationFunc- sigmoid/softmax

\# numClasses

#

\# Returns:

\# gradients -- A dictionary with the gradients

\# gradients\["dA" + str(l)\] = ...

\# gradients\["dW" + str(l)\] = ...

\# gradients\["db" + str(l)\] = ...

function \[gradsDA gradsDW gradsDB\]= backwardPropagationDeep(AL, Y, activation\_caches,forward\_caches,

dropoutMat, lambd=0, keep\_prob=1,

hiddenActivationFunc='relu',outputActivationFunc="sigmoid",numClasses)

\# Set the number of layers

L = length(activation\_caches);

m = size(AL)(2);

if (strcmp(outputActivationFunc,"sigmoid"))

\# Initializing the backpropagation

\# dl/dAL= -(y/a + (1-y)/(1-a)) - At the output layer

dAL = -((Y ./ AL) - (1 - Y) ./ ( 1 - AL));

elseif (strcmp(outputActivationFunc,"softmax"))

dAL=0;

 Y=Y';

endif

\# Since this is a binary classification the activation at output is sigmoid

\# Get the gradients at the last layer

\# Inputs: "AL, Y, caches".

\# Outputs: "gradients\["dAL"\], gradients\["dWL"\], gradients\["dbL"\]

activation\_cache = activation\_caches{L};

forward\_cache = forward\_caches(L);

\# Note the cell array includes an array of forward caches. To get to this we need to include the index {1}

if (lambd==0)

\[dA dW db\] = layerActivationBackward(dAL, forward\_cache{1},

activation\_cache, Y, activationFunc = outputActivationFunc,numClasses); else

\[dA dW db\] = layerActivationBackwardWithReg(dAL, forward\_cache{1}, activation\_cache, Y, lambd, activationFunc =

outputActivationFunc,numClasses);

endif

if (strcmp(outputActivationFunc,"sigmoid"))

gradsDA{L}= dA;

elseif (strcmp(outputActivationFunc,"softmax"))

gradsDA{L}= dA';#Note the transpose

endif

gradsDW{L}= dW;

gradsDB{L}= db;

\# Traverse in the reverse direction

for l =(L-1):-1:1

\# Compute the gradients for L-1 to 1 for Relu/tanh

\# Inputs: "gradients\["dA" + str(l + 2)\], caches".

\# Outputs: "gradients\["dA" + str(l + 1)\] , gradients\["dW" + str(l + 1)\] , gradients\["db" + str(l + 1)\]

activation\_cache = activation\_caches{l};

forward\_cache = forward\_caches(l);

#dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackward(gradients\['dA'+str(l+1)\], current\_cache,

activationFunc = "relu")

\# dAl the dervative of the activation of the lth layer,is the first element dAl= gradsDA{l+1};

if(lambd == 0)

\# Get the dropout mat

D = dropoutMat{l};

#Multiply by the dropoutMat

dAl= dAl .\* D;

\# Divide by keep\_prob to keep expected value same

dAl = dAl ./ keep\_prob;

\[dA\_prev\_temp, dW\_temp, db\_temp\] = layerActivationBackward(dAl, forward\_cache{1}, activation\_cache, Y, activationFunc =

hiddenActivationFunc,numClasses);

else

\[dA\_prev\_temp, dW\_temp, db\_temp\] =

layerActivationBackwardWithReg(dAl, forward\_cache{1}, activation\_cache, Y, lambd, activationFunc = hiddenActivationFunc,numClasses);

endif

gradsDA{l}= dA\_prev\_temp;

gradsDW{l}= dW\_temp;

gradsDB{l}= db\_temp;

endfor

end

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients -gradsW,gradsB

\# : learning rate

\# : outputActivationFunc

#output : Updated weights after 1 iteration

function \[weights biases\] = gradientDescent(weights, biases,gradsW,gradsB, learningRate,outputActivationFunc="sigmoid")

L = size(weights)(2); # number of layers in the neural network

\# Update rule for each parameter.

for l=1:(L-1)

 weights{l} = weights{l} -learningRate\* gradsW{l}; biases{l} = biases{l} -learningRate\* gradsB{l};

endfor

if (strcmp(outputActivationFunc,"sigmoid"))

weights{L} = weights{L} -learningRate\* gradsW{L};

biases{L} = biases{L} -learningRate\* gradsB{L};

elseif (strcmp(outputActivationFunc,"softmax"))

weights{L} = weights{L} -learningRate\* gradsW{L}';

biases{L} = biases{L} -learningRate\* gradsB{L}';

endif

end

\# Update parameters with momentum

\# Input : parameters

\# : gradients -gradsDW,gradsDB

\# : v -vdW, vdB

\# : beta

\# : learningRate

\# : outputActivationFunc

#output : Updated weights, biases

function \[weights biases\] = gradientDescentWithMomentum(weights, biases,gradsDW,gradsDB, vdW, vdB, beta,

learningRate,outputActivationFunc="sigmoid")

L = size(weights)(2); # number of layers in the neural network

\# Update rule for each parameter.

for l=1:(L-1)

\# Compute velocities

\# v\['dWk'\] = beta \*v\['dWk'\] + (1-beta)\*dWk

vdW{l} = beta\*vdW{l} + (1 -beta) \* gradsDW{l};

vdB{l} = beta\*vdB{l} + (1 -beta) \* gradsDB{l};

weights{l} = weights{l} -learningRate\* vdW{l};

biases{l} = biases{l} -learningRate\* vdB{l};

endfor

 if (strcmp(outputActivationFunc,"sigmoid")) vdW{L} = beta\*vdW{L} + (1 -beta) \* gradsDW{L};

vdB{L} = beta\*vdB{L} + (1 -beta) \* gradsDB{L};

weights{L} = weights{L} -learningRate\* vdW{L};

biases{L} = biases{L} -learningRate\* vdB{L};

elseif (strcmp(outputActivationFunc,"softmax"))

vdW{L} = beta\*vdW{L} + (1 -beta) \* gradsDW{L}';

vdB{L} = beta\*vdB{L} + (1 -beta) \* gradsDB{L}';

weights{L} = weights{L} -learningRate\* vdW{L};

biases{L} = biases{L} -learningRate\* vdB{L};

endif

end

\# Update parameters with RMSProp

\# Input : parameters - weights, biases

\# : gradients - gradsDW,gradsDB

\# : s -sdW, sdB

\# : beta1

\# : epsilon

\# : learningRate

\# : outputActivationFunc

#output : Updated weights and biases RMSProp

function \[weights biases\] = gradientDescentWithRMSProp(weights, biases,gradsDW,gradsDB, sdW, sdB, beta1, epsilon,

learningRate,outputActivationFunc="sigmoid")

L = size(weights)(2); # number of layers in the neural network

\# Update rule for each parameter.

for l=1:(L-1)

sdW{l} = beta1\*sdW{l} + (1 -beta1) \* gradsDW{l} .\* gradsDW{l}; sdB{l} = beta1\*sdB{l} + (1 -beta1) \* gradsDB{l} .\* gradsDB{l}; weights{l} = weights{l} - learningRate\* gradsDW{l} ./ sqrt(sdW{l} +

epsilon);

biases{l} = biases{l} - learningRate\* gradsDB{l} ./ sqrt(sdB{l} + epsilon); endfor

if (strcmp(outputActivationFunc,"sigmoid"))

 sdW{L} = beta1\*sdW{L} + (1 -beta1) \* gradsDW{L} .\* gradsDW{L}; sdB{L} = beta1\*sdB{L} + (1 -beta1) \* gradsDB{L} .\* gradsDB{L}; weights{L} = weights{L} -learningRate\* gradsDW{L} ./ sqrt(sdW{L}

+epsilon);

biases{L} = biases{L} -learningRate\* gradsDB{L} ./ sqrt(sdB{L} +

epsilon);

elseif (strcmp(outputActivationFunc,"softmax"))

sdW{L} = beta1\*sdW{L} + (1 -beta1) \* gradsDW{L}' .\* gradsDW{L}'; sdB{L} = beta1\*sdB{L} + (1 -beta1) \* gradsDB{L}' .\* gradsDB{L}'; weights{L} = weights{L} -learningRate\* gradsDW{L}' ./ sqrt(sdW{L}

+epsilon);

biases{L} = biases{L} -learningRate\* gradsDB{L}' ./ sqrt(sdB{L} +

epsilon);

endif

end

\# Update parameters with Adam

\# Input : parameters - weights, biases

\# : gradients -gradsDW,gradsDB

\# : v - vdW, vdB

\# : s - sdW, sdB

\# : t

\# : beta1

\# : beta2

\# : epsilon

\# : learningRate

\# : epsilon

#output : Updated weights and biases

function \[weights biases\] = gradientDescentWithAdam(weights,

biases,gradsDW,gradsDB,

vdW, vdB, sdW, sdB, t, beta1, beta2, epsilon,

learningRate,epsilon="sigmoid")

vdW\_corrected = {};

vdB\_corrected = {};

sdW\_corrected = {};

sdB\_corrected = {};

 L = size(weights)(2); # number of layers in the neural network

\# Update rule for each parameter.

for l=1:(L-1)

vdW{l} = beta1\*vdW{l} + (1 -beta1) \* gradsDW{l};

vdB{l} = beta1\*vdB{l} + (1 -beta1) \* gradsDB{l};

\# Compute bias-corrected first moment estimate.

vdW\_corrected{l} = vdW{l}/(1-beta1^t);

vdB\_corrected{l} = vdB{l}/(1-beta1^t);

sdW{l} = beta2\*sdW{l} + (1 -beta2) \* gradsDW{l} .\* gradsDW{l}; sdB{l} = beta2\*sdB{l} + (1 -beta2) \* gradsDB{l} .\* gradsDB{l};

\# Compute bias-corrected second moment estimate.

sdW\_corrected{l} = sdW{l}/(1-beta2^t);

sdB\_corrected{l} = sdB{l}/(1-beta2^t);

\# Update parameters.

d1=sqrt(sdW\_corrected{l}+epsilon);

d2=sqrt(sdB\_corrected{l}+epsilon);

weights{l} = weights{l} - learningRate\* vdW\_corrected{l} ./ d1; biases{l} = biases{l} -learningRate\* vdB\_corrected{l} ./ d2;

endfor

if (strcmp(outputActivationFunc,"sigmoid"))

vdW{L} = beta1\*vdW{L} + (1 -beta1) \* gradsDW{L};

vdB{L} = beta1\*vdB{L} + (1 -beta1) \* gradsDB{L};

\# Compute bias-corrected first moment estimate.

vdW\_corrected{L} = v{L}/(1-beta1^t);

vdB\_corrected{L} = v{L}/(1-beta1^t);

sdW{L} = beta2\*sdW{L} + (1 -beta2) \* gradsDW{L} .\* gradsDW{L}; sdB{L} = beta2\*sdB{L} + (1 -beta2) \* gradsDB{L} .\* gradsDB{L};

\# Compute bias-corrected second moment estimate.

sdW\_corrected{L} = s{L}/(1-beta2^t);

sdB\_corrected{L} = s{L}/(1-beta2^t);

\# Update parameters.

d1=sqrt(sdW\_corrected{L}+epsilon);

d2=sqrt(sdB\_corrected{L}+epsilon);

weights{L} = weights{L} - learningRate\* vdW\_corrected{L} ./ d1; biases{L} = biases{L} -learningRate\* vdB\_corrected{L} ./ d2;

elseif (strcmp(outputActivationFunc,"softmax"))

vdW{L} = beta1\*vdW{L} + (1 -beta1) \* gradsDW{L}';

vdB{L} = beta1\*vdB{L} + (1 -beta1) \* gradsDB{L}';

\# Compute bias-corrected first moment estimate.

vdW\_corrected{L} = vdW{L}/(1-beta1^t);

vdB\_corrected{L} = vdB{L}/(1-beta1^t);

sdW{L} = beta2\*sdW{L} + (1 -beta2) \* gradsDW{L}' .\* gradsDW{L}'; sdB{L} = beta2\*sdB{L} + (1 -beta2) \* gradsDB{L}' .\* gradsDB{L}';

\# Compute bias-corrected second moment estimate.

sdW\_corrected{L} = sdW{L}/(1-beta2^t);

sdB\_corrected{L} = sdB{L}/(1-beta2^t);

\# Update parameters.

d1=sqrt(sdW\_corrected{L}+epsilon);

d2=sqrt(sdB\_corrected{L}+epsilon);

weights{L} = weights{L} - learningRate\* vdW\_corrected{L} ./ d1; biases{L} = biases{L} -learningRate\* vdB\_corrected{L} ./ d2;

endif

end

\# Execute a L layer Deep learning model

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu /tanh

\# : outputActivationFunc - Activation function at hidden layer

sigmoid/softmax

\# : learning rate

\# : lambd

\# : keep\_prob

\# : num of iterations

#output : Updated weights and biases after each iteration

function \[weights biases costs\] = L\_Layer\_DeepModel(X, Y, layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",learning\_rate = .3, lambd=0, keep\_prob=1, num\_iterations = 10000,initType="default")#lr was 0.009

rand ("seed", 1);

costs = \[\] ;

if (strcmp(initType,"He"))

\# He Initialization

\[weights biases\] = HeInitializeDeepModel(layersDimensions);

elseif (strcmp(initType,"Xav"))

\# Xavier Initialization

\[weights biases\] = XavInitializeDeepModel(layersDimensions);

else

\# Default initialization.

\[weights biases\] = initializeDeepModel(layersDimensions);

endif

\# Loop (gradient descent)

for i = 0:num\_iterations

\# Forward propagation: \[LINEAR -> RELU\]\*(L-1) -> LINEAR -> SIGMOID.

\[AL forward\_caches activation\_caches droputMat\] =

forwardPropagationDeep(X, weights, biases,keep\_prob, hiddenActivationFunc, outputActivationFunc=outputActivationFunc);

\# Regularization parameter is 0

if (lambd==0)

\# Compute cost.

cost = computeCost(AL,

Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));

else

 # Compute cost with regularization cost = computeCostWithReg(weights, AL, Y, lambd,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));

endif

\# Backward propagation.

\[gradsDA gradsDW gradsDB\] = backwardPropagationDeep(AL, Y,

activation\_caches,forward\_caches, droputMat, lambd, keep\_prob, hiddenActivationFunc, outputActivationFunc=outputActivationFunc, numClasses=layersDimensions(size(layersDimensions)

(2)));

\# Update parameters.

\[weights biases\] = gradientDescent(weights,biases,

gradsDW,gradsDB,learning\_rate,outputActivationFunc=outputActivationFunc);

\# Print the cost every 1000 iterations

if ( mod(i,1000) == 0)

costs =\[costs cost\];

#disp ("Cost after iteration"), L2RegularizationCost(i),disp(cost); printf("Cost after iteration i=%i cost=%d\\n",i,cost); endif

endfor

end

\# Execute a L layer Deep learning model with Stochastic Gradient descent

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu

/tanh/sigmoid

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : learning rate

\# : lrDecay

\# : decayRate

\# : lambd

\# : keep\_prob

\# : optimizer

\# : beta

\# : beta1

\# : beta2

\# : epsilon

\# : mini\_batch\_size

\# : num of epochs

#output : Updated weights and biases after each iteration

function \[weights biases costs\] = L\_Layer\_DeepModel\_SGD(X, Y, layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",learningRate = .3,

optimizer lrDecay=false,decayRate=1,

lambd=0, keep\_prob=1,

optimizer="gd", beta=0.9, beta1=0.9,

beta2=0.999,epsilon=10^-8,

mini\_batch\_size = 64, num\_epochs = 2500)

disp("Values");

printf("learningRate=%f ",learningRate);

printf("lrDecay=%d ",lrDecay);

printf("decayRate=%f ",decayRate);

printf("lamd=%d ",lambd);

printf("keep\_prob=%f ",keep\_prob);

printf("optimizer=%s ",optimizer);

printf("beta=%f ",beta);

printf("beta1=%f ",beta1);

printf("beta2=%f ",beta2);

printf("epsilon=%f ",epsilon);

printf("mini\_batch\_size=%d ",mini\_batch\_size);

printf("num\_epochs=%d ",num\_epochs);

t=0;

rand ("seed", 1);

costs = \[\] ;

\# Parameters initialization.

\[weights biases\] = initializeDeepModel(layersDimensions);

if (strcmp(optimizer,"momentum"))

\[vdW vdB\] = initializeVelocity(weights, biases);

 elseif(strcmp(optimizer,"rmsprop"))

\[sdW sdB\] = initializeRMSProp(weights, biases);

elseif(strcmp(optimizer,"adam"))

\[vdW vdB sdW sdB\] = initializeAdam(weights, biases);

endif

seed=10;

\# Loop (gradient descent)

for i = 0:num\_epochs

seed = seed + 1;

\[mini\_batches\_X mini\_batches\_Y\] = random\_mini\_batches(X, Y,

mini\_batch\_size, seed);

minibatches=length(mini\_batches\_X);

for batch=1:minibatches

X=mini\_batches\_X{batch};

Y=mini\_batches\_Y{batch};

\# Forward propagation: \[LINEAR -> RELU\]\*(L-1) -> LINEAR -> SIGMOID/SOFTMAX.

\[AL forward\_caches activation\_caches droputMat\] =

forwardPropagationDeep(X, weights, biases, keep\_prob,hiddenActivationFunc, outputActivationFunc=outputActivationFunc);

#disp(batch);

#disp(size(X));

#disp(size(Y));

if (lambd==0)

\# Compute cost.

cost = computeCost(AL,

Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));

else

\# Compute cost with regularization

cost = computeCostWithReg(weights, AL, Y, lambd,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));

endif

#disp(cost);

\# Backward propagation.

\[gradsDA gradsDW gradsDB\] = backwardPropagationDeep(AL, Y,

activation\_caches,forward\_caches, droputMat, lambd, keep\_prob, hiddenActivationFunc, outputActivationFunc=outputActivationFunc, numClasses=layersDimensions(size(layersDimensions)

(2)));

if (strcmp(optimizer,"gd"))

\# Update parameters.

\[weights biases\] = gradientDescent(weights,biases,

gradsDW,gradsDB,learningRate,outputActivationFunc=outputActivationFunc); elseif (strcmp(optimizer,"momentum"))

\[weights biases\] = gradientDescentWithMomentum(weights,

biases,gradsDW,gradsDB, vdW, vdB, beta,

learningRate,outputActivationFunc);

elseif (strcmp(optimizer,"rmsprop"))

\[weights biases\] = gradientDescentWithRMSProp(weights,

biases,gradsDW,gradsDB, sdW, sdB, beta1, epsilon,

learningRate,outputActivationFunc);

elseif (strcmp(optimizer,"adam"))

t=t+1;

\[weights biases\] = gradientDescentWithAdam(weights,

biases,gradsDW,gradsDB,vdW, vdB, sdW, sdB, t, beta1, beta2, epsilon, learningRate,outputActivationFunc);

endif

endfor

\# Print the cost every 1000 iterations

if ( mod(i,1000) == 0)

costs =\[costs cost\];

#disp ("Cost after iteration"), disp(i),disp(cost); printf("Cost after iteration i=%i cost=%d\\n",i,cost); endif

if(lrDecay==true)

learningRate=decayRate^(num\_epochs/1000)\*learningRate;

endif

endfor

end

\# Plot cost vs iterations

function plotCostVsIterations(maxIterations,costs,fig1) iterations=\[0:1000:maxIterations\];

plot(iterations,costs);

title ("Cost vs no of iterations ");

xlabel("No of iterations");

ylabel("Cost");

print -dpng figReg2-o

end;

\# Plot cost vs epochs

function plotCostVsEpochs(maxEpochs,costs,fig1)

epochs=\[0:1000:maxEpochs\];

plot(epochs,costs);

title ("Cost vs no of epochs ");

xlabel("No of epochs");

ylabel("Cost");

print -dpng fig5-o

end;

\# Compute the predicted value for a given input

\# Input : Neural Network parameters

\# : Input data

function \[predictions\]= predict(weights, biases,

X,keep\_prob=1,hiddenActivationFunc="relu")

\[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights, biases,keep\_prob,hiddenActivationFunc);

predictions = (AL>0.5);

end

\# Plot the decision boundary

function plotDecisionBoundary(data,weights,

biases,keep\_prob=1,hiddenActivationFunc="relu",fig2)

%Plot a non-linear decision boundary learned by the SVM

colormap ("summer");

% Make classification predictions over a grid of values

x1plot = linspace(min(data(:,1)), max(data(:,1)), 400)';

x2plot = linspace(min(data(:,2)), max(data(:,2)), 400)';

\[X1, X2\] = meshgrid(x1plot, x2plot);

 vals = zeros(size(X1));

\# Plot the prediction for the grid

for i = 1:size(X1, 2)

gridPoints = \[X1(:, i), X2(:, i)\];

vals(:, i)=predict(weights, biases,gridPoints',keep\_prob,

hiddenActivationFunc=hiddenActivationFunc);

endfor

scatter(data(:,1),data(:,2),8,c=data(:,3),"filled");

% Plot the boundary

hold on

#contour(X1, X2, vals, \[0 0\], 'LineWidth', 2);

contour(X1, X2, vals,"linewidth",4);

title ({"3 layer Neural Network decision boundary"}); hold off;

print -dpng figReg22-o

end

\# Compute scores

function \[AL\]= scores(weights, biases, X,hiddenActivationFunc="relu")

\[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights, biases,hiddenActivationFunc);

end

\# Create Random mini batches. Return cell arrays with the mini batches

\# Input : X, Y

\# : Size of minibatch

#Output : mini batches X & Y

function \[mini\_batches\_X mini\_batches\_Y\]= random\_mini\_batches(X, Y, miniBatchSize = 64, seed = 0)

rand ("seed", seed);

\# Get number of training samples

m = size(X)(2);

\# Create a list of random numbers < m

permutation = randperm(m);

 # Randomly shuffle the training data

shuffled\_X = X(:, permutation);

shuffled\_Y = Y(:, permutation);

\# Compute number of mini batches

numCompleteMinibatches = floor(m/miniBatchSize);

batch=0;

for k = 0:(numCompleteMinibatches-1)

#Set the start and end of each mini batch

batch=batch+1;

lower=(k\*miniBatchSize)+1;

upper=(k+1) \* miniBatchSize;

mini\_batch\_X = shuffled\_X(:, lower:upper);

mini\_batch\_Y = shuffled\_Y(:, lower:upper);

\# Create cell arrays

mini\_batches\_X{batch} = mini\_batch\_X;

mini\_batches\_Y{batch} = mini\_batch\_Y;

endfor

\# If the batc size does not cleanly divide with number of mini batches if mod(m ,miniBatchSize) != 0

\# Set the start and end of the last mini batch

l=floor(m/miniBatchSize)\*miniBatchSize;

m=l+ mod(m,miniBatchSize);

mini\_batch\_X = shuffled\_X(:,(l+1):m);

mini\_batch\_Y = shuffled\_Y(:,(l+1):m);

batch=batch+1;

mini\_batches\_X{batch} = mini\_batch\_X;

mini\_batches\_Y{batch} = mini\_batch\_Y;

endif

end

\# Plot decision boundary

function plotDecisionBoundary1( data,weights, biases,keep\_prob=1, hiddenActivationFunc="relu")

% Make classification predictions over a grid of values

x1plot = linspace(min(data(:,1)), max(data(:,1)), 400)';

x2plot = linspace(min(data(:,2)), max(data(:,2)), 400)';

 \[X1, X2\] = meshgrid(x1plot, x2plot);

vals = zeros(size(X1));

for i = 1:size(X1, 2)

gridPoints = \[X1(:, i), X2(:, i)\];

\[AL forward\_caches activation\_caches\] =

forwardPropagationDeep(gridPoints', weights,

biases,keep\_prob,hiddenActivationFunc, outputActivationFunc="softmax");

\[l m\] = max(AL, \[ \], 2);

vals(:, i)= m;

endfor

scatter(data(:,1),data(:,2),8,c=data(:,3),"filled");

% Plot the boundary

hold on

contour(X1, X2, vals,"linewidth",4);

print -dpng "fig-o1.png"

end

**9.**

**Appendix 8 – Gradient Check**

**8.1 Python**

\# -\*- coding: utf-8 -\*-

############################################################################################################

#

\# File: DLfunctions8.py

\# Developer: Tinniam V Ganesh

\# Date : 6 May 2018

#

##########################################################################################################

import numpy as np

import matplotlib.pyplot as plt

import matplotlib

import matplotlib.pyplot as plt

from matplotlib import cm

import math

import sklearn

import sklearn.datasets

\# Conmpute the sigmoid of a vector

def sigmoid(Z):

A=1/(1+np.exp(-Z))

cache=Z

return A,cache

\# Conmpute the Relu of a vector

def relu(Z):

A = np.maximum(0,Z)

cache=Z

return A,cache

\# Conmpute the tanh of a vector

def tanh(Z):

 A = np.tanh(Z)

cache=Z

return A,cache

\# Conmpute the softmax of a vector

def softmax(Z):

\# get unnormalized probabilities

exp\_scores = np.exp(Z.T)

\# normalize them for each example

A = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

cache=Z

return A,cache

\# Conmpute the Stable softmax of a vector

def stableSoftmax(Z):

#Compute the softmax of vector x in a numerically stable way.

shiftZ = Z.T - np.max(Z.T,axis=1).reshape(-1,1)

exp\_scores = np.exp(shiftZ)

\# normalize them for each example

A = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

cache=Z

return A,cache

\# Compute the derivative of Relu

def reluDerivative(dA, cache):

Z = cache

dZ = np.array(dA, copy=True) # just converting dz to a correct object.

\# When z <= 0, you should set dz to 0 as well.

dZ\[Z <= 0\] = 0

return dZ

\# Compute the derivative of sigmoid

def sigmoidDerivative(dA, cache):

Z = cache

s = 1/(1+np.exp(-Z))

dZ = dA \* s \* (1-s)

return dZ

\# Compute the derivative of tanh

def tanhDerivative(dA, cache):

Z = cache

a = np.tanh(Z)

dZ = dA \* (1 - np.power(a, 2))

return dZ

\# Compute the derivative of softmax

def softmaxDerivative(dA, cache,y,numTraining):

\# Note : dA not used. dL/dZ = dL/dA \* dA/dZ = pi-yi

Z = cache

\# Compute softmax

exp\_scores = np.exp(Z.T)

\# normalize them for each example

probs = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

\# compute the gradient on scores

dZ = probs

\# dZ = pi- yi

dZ\[range(int(numTraining)),y\[:,0\]\] -= 1

return(dZ)

\# Compute the derivative of Stable softmax

def stableSoftmaxDerivative(dA, cache,y,numTraining):

\# Note : dA not used. dL/dZ = dL/dA \* dA/dZ = pi-yi

Z = cache

\# Compute stable softmax

shiftZ = Z.T - np.max(Z.T,axis=1).reshape(-1,1)

exp\_scores = np.exp(shiftZ)

\# normalize them for each example

probs = exp\_scores / np.sum(exp\_scores, axis=1, keepdims=True)

#print(probs)

\# compute the gradient on scores

dZ = probs

\# dZ = pi- yi

dZ\[range(int(numTraining)),y\[:,0\]\] -= 1

 return(dZ)

\# Initialize the model

\# Input : number of features

\# number of hidden units

\# number of units in output

\# Returns: Weight and bias matrices and vectors

def initializeModel(numFeats,numHidden,numOutput):

np.random.seed(1)

W1=np.random.randn(numHidden,numFeats)\*0.01 # Multiply by .01

b1=np.zeros((numHidden,1))

W2=np.random.randn(numOutput,numHidden)\*0.01

b2=np.zeros((numOutput,1))

\# Create a dictionary of the neural network parameters

nnParameters={'W1':W1,'b1':b1,'W2':W2,'b2':b2}

return(nnParameters)

\# Initialize model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers def initializeDeepModel(layerDimensions):

np.random.seed(3)

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

layerParams = {}

for l in range(1,len(layerDimensions)):

layerParams\['W' + str(l)\] =

np.random.randn(layerDimensions\[l\],layerDimensions\[l-1\])\*0.01 # Multiply by

.01

layerParams\['b' + str(l)\] = np.zeros((layerDimensions\[l\],1))

np.savetxt('W' + str(l)+'.csv',layerParams\['W' + str(l)\],delimiter=',') np.savetxt('b' + str(l)+'.csv',layerParams\['b' + str(l)\],delimiter=',') return(layerParams)

return Z, cache

\# He Initialization model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers

\# He initilization multiplies the random numbers with sqrt(2/layerDimensions\[l-1\])

def HeInitializeDeepModel(layerDimensions):

np.random.seed(3)

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

layerParams = {}

for l in range(1,len(layerDimensions)):

layerParams\['W' + str(l)\] = np.random.randn(layerDimensions\[l\], layerDimensions\[l-1\])\*np.sqrt(2/layerDimensions\[l-1\])

layerParams\['b' + str(l)\] = np.zeros((layerDimensions\[l\],1))

return(layerParams)

return Z, cache

\# Xavier Initialization model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers

\# Xavier initilization multiplies the random numbers with

sqrt(1/layerDimensions\[l-1\])

def XavInitializeDeepModel(layerDimensions):

np.random.seed(3)

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

layerParams = {}

for l in range(1,len(layerDimensions)):

layerParams\['W' + str(l)\] = np.random.randn(layerDimensions\[l\], layerDimensions\[l-1\])\*np.sqrt(1/layerDimensions\[l-1\])

layerParams\['b' + str(l)\] = np.zeros((layerDimensions\[l\],1))

return(layerParams)

 return Z, cache

\# Initialize velocity of

\# Input : parameters

\# Returns: v - Initial velocity

def initializeVelocity(parameters):

L = len(parameters)//2 # Create an integer

v = {}

\# Initialize velocity with the same dimensions as W

for l in range(L):

v\["dW" + str(l+1)\] = np.zeros((parameters\['W' + str(l+1)\].shape\[0\], parameters\['W' + str(l+1)\].shape\[1\]))

v\["db" + str(l+1)\] = np.zeros((parameters\['b' + str(l+1)\].shape\[0\], parameters\['b' + str(l+1)\].shape\[1\]))

return v

\# Initialize RMSProp param

\# Input : List of units in each layer

\# Returns: s - Initial RMSProp

def initializeRMSProp(parameters):

L = len(parameters)//2 # Create an integer

s = {}

\# Initialize velocity with the same dimensions as W

for l in range(L):

s\["dW" + str(l+1)\] = np.zeros((parameters\['W' + str(l+1)\].shape\[0\], parameters\['W' + str(l+1)\].shape\[1\]))

s\["db" + str(l+1)\] = np.zeros((parameters\['b' + str(l+1)\].shape\[0\], parameters\['b' + str(l+1)\].shape\[1\]))

return s

\# Initialize Adam param

\# Input : List of units in each layer

\# Returns: v and s - Adam paramaters

def initializeAdam(parameters) :

L = len(parameters) // 2 # number of layers in the neural networks v = {}

s = {}

\# Initialize v, s.

for l in range(L):

v\["dW" + str(l+1)\] = np.zeros((parameters\['W' + str(l+1)\].shape\[0\], parameters\['W' + str(l+1)\].shape\[1\]))

v\["db" + str(l+1)\] = np.zeros((parameters\['b' + str(l+1)\].shape\[0\], parameters\['b' + str(l+1)\].shape\[1\]))

s\["dW" + str(l+1)\] = np.zeros((parameters\['W' + str(l+1)\].shape\[0\], parameters\['W' + str(l+1)\].shape\[1\]))

s\["db" + str(l+1)\] = np.zeros((parameters\['b' + str(l+1)\].shape\[0\], parameters\['b' + str(l+1)\].shape\[1\]))

return v, s

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prev - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# keep\_prob

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : A, cache

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

def layerActivationForward(A\_prev, W, b, keep\_prob=0,

activationFunc="relu"):

\# Compute Z

Z = np.dot(W,A\_prev) + b

forward\_cache = (A\_prev, W, b)

\# Compute the activation for sigmoid

if activationFunc == "sigmoid":

A, activation\_cache = sigmoid(Z)

\# Compute the activation for Relu

elif activationFunc == "relu":

 A, activation\_cache = relu(Z)

\# Compute the activation for tanh

elif activationFunc == 'tanh':

A, activation\_cache = tanh(Z)

elif activationFunc == 'softmax':

A, activation\_cache = stableSoftmax(Z)

cache = (forward\_cache, activation\_cache)

return A, cache

\# Compute the forward propagation for layers 1..L

\# Input : X - Input Features

\# parameters: Weights and biases

\# keep\_prob

\# hiddenActivationFunc - Activation function at hidden layers Relu/tanh

\# outputActivationFunc - Activation function at output - sigmoid/softmax

\# Returns : AL

\# caches

\# dropoutMat

\# The forward propoagtion uses the Relu/tanh activation from layer 1..L-1 and sigmoid actiovation at layer L

def forwardPropagationDeep(X, parameters,keep\_prob=0,

hiddenActivationFunc='relu',outputActivationFunc='sigmoid'):

caches = \[\]

#initialize the dropout matrix

dropoutMat = {}

\# Set A to X (A0)

A = X

L = len(parameters)//2 # number of layers in the neural network

\# Loop through from layer 1 to upto layer L

for l in range(1, L):

A\_prev = A

\# Zi = Wi x Ai-1 + bi and Ai = g(Zi)

A, cache = layerActivationForward(A\_prev, parameters\['W'+str(l)\], parameters\['b'+str(l)\], keep\_prob, activationFunc = hiddenActivationFunc)

\# Randomly drop some activation units

\# Create a matrix as the same shape as A

D = np.random.rand(A.shape\[0\],A.shape\[1\])

 D = (D < keep\_prob)

\# We need to use the same 'dropout' matrix in backward propagation

\# Save the dropout matrix for use in backprop

dropoutMat\["D" + str(l)\] =D

A= np.multiply(A,D)

A = np.divide(A,keep\_prob)

caches.append(cache)

\# last layer

AL, cache = layerActivationForward(A, parameters\['W'+str(L)\], parameters\['b'+str(L)\], activationFunc = outputActivationFunc) caches.append(cache)

return AL, caches, dropoutMat

\# Compute the cost

\# Input : Activation of last layer

\# : Output from data

\# : Y

\# :outputActivationFunc - Activation function at output - sigmoid/softmax

\# Output: cost

def computeCost(AL,Y,outputActivationFunc="sigmoid"): if outputActivationFunc=="sigmoid":

m= float(Y.shape\[1\])

\# Element wise multiply for logprobs

cost=-1/m \*np.sum(Y\*np.log(AL) + (1-Y)\*(np.log(1-AL)))

cost = np.squeeze(cost)

elif outputActivationFunc=="softmax":

\# Take transpose of Y for softmax

Y=Y.T

m= float(len(Y))

\# Compute log probs. Take the log prob of correct class based on output y correct\_logprobs = -np.log(AL\[range(int(m)),Y.T\])

\# Conpute loss

cost = np.sum(correct\_logprobs)/m

return cost

\# Compute the cost with regularization

\# Input : parameters

\# : AL

\# : Y

\# : lambd

\# :outputActivationFunc - Activation function at output -

sigmoid/softmax/tanh

\# Output: cost

def computeCostWithReg(parameters,AL,Y,lambd,

outputActivationFunc="sigmoid"):

if outputActivationFunc=="sigmoid":

m= float(Y.shape\[1\])

\# Element wise multiply for logprobs

cost=-1/m \*np.sum(Y\*np.log(AL) + (1-Y)\*(np.log(1-AL)))

cost = np.squeeze(cost)

\# Regularization cost

L= int(len(parameters)/2)

L2RegularizationCost=0

for l in range(L):

L2RegularizationCost+=np.sum(np.square(parameters\['W'+str(l+1)\])) L2RegularizationCost = (lambd/(2\*m))\*L2RegularizationCost

cost = cost + L2RegularizationCost

elif outputActivationFunc=="softmax":

\# Take transpose of Y for softmax

Y=Y.T

m= float(len(Y))

\# Compute log probs. Take the log prob of correct class based on output y correct\_logprobs = -np.log(AL\[range(int(m)),Y.T\])

\# Conpute loss

cost = np.sum(correct\_logprobs)/m

 # Regularization cost

L= int(len(parameters)/2)

L2RegularizationCost=0

for l in range(L):

L2RegularizationCost+=np.sum(np.square(parameters\['W'+str(l+1)\])) L2RegularizationCost = (lambd/(2\*m))\*L2RegularizationCost

cost = cost + L2RegularizationCost

return cost

\# Compute the backpropoagation for 1 cycle

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# # Input features

\# # keep\_prob

\# # Output values Y

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

def layerActivationBackward(dA, cache, Y, keep\_prob=1,

activationFunc="relu"):

forward\_cache, activation\_cache = cache

A\_prev, W, b = forward\_cache

numtraining = float(A\_prev.shape\[1\])

if activationFunc == "relu":

dZ = reluDerivative(dA, activation\_cache)

elif activationFunc == "sigmoid":

dZ = sigmoidDerivative(dA, activation\_cache)

elif activationFunc == "tanh":

dZ = tanhDerivative(dA, activation\_cache)

elif activationFunc == "softmax":

dZ = stableSoftmaxDerivative(dA, activation\_cache,Y,numtraining) if activationFunc == 'softmax':

dW = 1/numtraining \* np.dot(A\_prev,dZ)

db = 1/numtraining \* np.sum(dZ, axis=0, keepdims=True)

dA\_prev = np.dot(dZ,W)

 else:

dW = 1/numtraining \*(np.dot(dZ,A\_prev.T))

db = 1/numtraining \* np.sum(dZ, axis=1, keepdims=True)

dA\_prev = np.dot(W.T,dZ)

return dA\_prev, dW, db

\# Compute the backpropoagation with regularization for 1 cycle

\# Input : dA- Neural Network parameters

\# # cache - forward\_cache & activation\_cache

\# # Output values Y

\# # lambd

\# # activationFunc

\# Returns dA\_prev, dW, db

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

def layerActivationBackwardWithReg(dA, cache, Y, lambd, activationFunc): forward\_cache, activation\_cache = cache

A\_prev, W, b = forward\_cache

numtraining = float(A\_prev.shape\[1\])

#print("n=",numtraining)

#print("no=",numtraining)

if activationFunc == "relu":

dZ = reluDerivative(dA, activation\_cache)

elif activationFunc == "sigmoid":

dZ = sigmoidDerivative(dA, activation\_cache)

elif activationFunc == "tanh":

dZ = tanhDerivative(dA, activation\_cache)

elif activationFunc == "softmax":

dZ = stableSoftmaxDerivative(dA, activation\_cache,Y,numtraining) if activationFunc == 'softmax':

\# Add the regularization factor

dW = 1/numtraining \* np.dot(A\_prev,dZ) + (lambd/numtraining) \* W.T

 db = 1/numtraining \* np.sum(dZ, axis=0, keepdims=True) dA\_prev = np.dot(dZ,W)

else:

\# Add the regularization factor

dW = 1/numtraining \*(np.dot(dZ,A\_prev.T)) + (lambd/numtraining) \* W

#print("dW=",dW)

db = 1/numtraining \* np.sum(dZ, axis=1, keepdims=True)

#print("db=",db)

dA\_prev = np.dot(W.T,dZ)

return dA\_prev, dW, db

\# Compute the backpropoagation for 1 cycle

\# Input : AL: Output of L layer Network - weights

\# # Y Real output

\# # caches -- list of caches containing:

\# # dropoutMat

\# # lambd

\# # keep\_prob

\# every cache of layerActivationForward() with "relu"/"tanh"

\# #(it's caches\[l\], for l in range(L-1) i.e l = 0...L-2)

\# #the cache of layerActivationForward() with "sigmoid" (it's caches\[L-1\])

\# # hiddenActivationFunc - Activation function at hidden layers -

relu/sigmoid/tanh

\# #outputActivationFunc - Activation function at output - sigmoid/softmax

#

\# Returns:

\# gradients -- A dictionary with the gradients

\# gradients\["dA" + str(l)\] = ...

\# gradients\["dW" + str(l)\] = ...

\# gradients\["db" + str(l)\] = ...

def backwardPropagationDeep(AL, Y, caches, dropoutMat, lambd=0, keep\_prob=1, hiddenActivationFunc='relu',outputActivationFunc="sigmoid"):

#initialize the gradients

gradients = {}

\# Set the number of layers

L = len(caches)

 m = float(AL.shape\[1\])

if outputActivationFunc == "sigmoid":

Y = Y.reshape(AL.shape) # after this line, Y is the same shape as AL

\# Initializing the backpropagation

\# dl/dAL= -(y/a + (1-y)/(1-a)) - At the output layer

dAL = - (np.divide(Y, AL) - np.divide(1 - Y, 1 - AL))

else:

dAL =0

Y=Y.T

\# Since this is a binary classification the activation at output is sigmoid

\# Get the gradients at the last layer

\# Inputs: "AL, Y, caches".

\# Outputs: "gradients\["dAL"\], gradients\["dWL"\], gradients\["dbL"\]

current\_cache = caches\[L-1\]

if lambd==0:

gradients\["dA" + str(L)\], gradients\["dW" + str(L)\], gradients\["db" + str(L)\]

\= layerActivationBackward(dAL, current\_cache,

Y, activationFunc = outputActivationFunc)

else: #Regularization

gradients\["dA" + str(L)\], gradients\["dW" + str(L)\], gradients\["db" + str(L)\]

\= layerActivationBackwardWithReg(dAL, current\_cache,

Y, lambd, activationFunc = outputActivationFunc)

\# Note dA for softmax is the transpose

if outputActivationFunc == "softmax":

gradients\["dA" + str(L)\] = gradients\["dA" + str(L)\].T

\# Traverse in the reverse direction

for l in reversed(range(L-1)):

\# Compute the gradients for L-1 to 1 for Relu/tanh

\# Inputs: "gradients\["dA" + str(l + 2)\], caches".

\# Outputs: "gradients\["dA" + str(l + 1)\] , gradients\["dW" + str(l + 1)\] , gradients\["db" + str(l + 1)\]

current\_cache = caches\[l\]

#dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackward(gradients\['dA'+str(l+2)\], current\_cache,

activationFunc = "relu")

if lambd==0:

\# In the reverse direction use the dame dropout matrix

\# Random dropout

\# Multiply dA'l' with the dropoutMat and divide to keep the expected value same

D = dropoutMat\["D" + str(l+1)\]

\# Drop some dAl's

gradients\['dA'+str(l+2)\]= np.multiply(gradients\['dA'+str(l+2)\],D)

\# Divide by keep\_prob to keep expected value same

gradients\['dA'+str(l+2)\] = np.divide(gradients\['dA'+str(l+2)\],keep\_prob) dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackward(gradients\['dA'+str(l+2)\], current\_cache, Y, keep\_prob=1, activationFunc = hiddenActivationFunc)

else:

dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackwardWithReg(gradients\['dA'+str(l+2)\], current\_cache, Y, lambd, activationFunc = hiddenActivationFunc)

gradients\["dA" + str(l + 1)\] = dA\_prev\_temp

gradients\["dW" + str(l + 1)\] = dW\_temp

gradients\["db" + str(l + 1)\] = db\_temp

return gradients

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients

\# : learning rate

\# : outputActivationFunc - Activation function at output - sigmoid/softmax

#output : Updated weights after 1 iteration

def gradientDescent(parameters, gradients,

learningRate,outputActivationFunc="sigmoid"):

L = int(len(parameters) / 2)

\# Update rule for each parameter.

for l in range(L-1):

parameters\["W" + str(l+1)\] = parameters\['W'+str(l+1)\] -learningRate\*

gradients\['dW' + str(l+1)\]

parameters\["b" + str(l+1)\] = parameters\['b'+str(l+1)\] -learningRate\*

gradients\['db' + str(l+1)\]

if outputActivationFunc=="sigmoid":

parameters\["W" + str(L)\] = parameters\['W'+str(L)\] -learningRate\*

gradients\['dW' + str(L)\]

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] -learningRate\*

gradients\['db' + str(L)\]

elif outputActivationFunc=="softmax":

parameters\["W" + str(L)\] = parameters\['W'+str(L)\] -learningRate\*

gradients\['dW' + str(L)\].T

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] -learningRate\*

gradients\['db' + str(L)\].T

return parameters

\# Update parameters with momentum

\# Input : parameters

\# : gradients

\# : v

\# : beta

\# : learningRate

\# : outputActivationFunc - softmax/sigmoid

#output : Updated parameters and velocity

def gradientDescentWithMomentum(parameters, gradients, v, beta, learningRate, outputActivationFunc="sigmoid"):

L = len(parameters) // 2 # number of layers in the neural networks

\# Momentum update for each parameter

for l in range(L-1):

\# Compute velocities

\# v\['dWk'\] = beta \*v\['dWk'\] + (1-beta)\*dWk

v\["dW" + str(l+1)\] = beta\*v\["dW" + str(l+1)\] + (1-beta) \* gradients\['dW' +

str(l+1)\]

v\["db" + str(l+1)\] = beta\*v\["db" + str(l+1)\] + (1-beta) \* gradients\['db' +

str(l+1)\]

\# Update parameters with velocities

 parameters\["W" + str(l+1)\] = parameters\['W' + str(l+1)\] - learningRate\*

v\["dW" + str(l+1)\]

parameters\["b" + str(l+1)\] = parameters\['b' + str(l+1)\] - learningRate\*

v\["db" + str(l+1)\]

if outputActivationFunc=="sigmoid":

v\["dW" + str(L)\] = beta\*v\["dW" + str(L)\] + (1-beta) \* gradients\['dW' +

str(L)\]

v\["db" + str(L)\] = beta\*v\["db" + str(L)\] + (1-beta) \* gradients\['db' + str(L)\]

parameters\["W" + str(L)\] = parameters\['W'+str(L)\] -learningRate\*

gradients\['dW' + str(L)\]

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] -learningRate\*

gradients\['db' + str(L)\]

elif outputActivationFunc=="softmax":

v\["dW" + str(L)\] = beta\*v\["dW" + str(L)\] + (1-beta) \* gradients\['dW' +

str(L)\].T

v\["db" + str(L)\] = beta\*v\["db" + str(L)\] + (1-beta) \* gradients\['db' +

str(L)\].T

parameters\["W" + str(L)\] = parameters\['W'+str(L)\] -learningRate\*

gradients\['dW' + str(L)\].T

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] -learningRate\*

gradients\['db' + str(L)\].T

return parameters, v

\# Update parameters with RMSProp

\# Input : parameters

\# : gradients

\# : s

\# : beta1

\# : learningRate

\# : outputActivationFunc - sigmoid/softmax

\# output : Updated parameters and RMSProp

def gradientDescentWithRMSProp(parameters, gradients, s, beta1, epsilon, learningRate, outputActivationFunc="sigmoid"):

L = len(parameters) // 2 # number of layers in the neural networks

\# Momentum update for each parameter

 for l in range(L-1):

\# Compute RMSProp

\# s\['dWk'\] = beta1 \*s\['dWk'\] + (1-beta1)\*dWk\*\*2/sqrt(s\['dWk'\]) s\["dW" + str(l+1)\] = beta1\*s\["dW" + str(l+1)\] + (1-beta1) \* \\ np.multiply(gradients\['dW' + str(l+1)\],gradients\['dW' + str(l+1)\]) s\["db" + str(l+1)\] = beta1\*s\["db" + str(l+1)\] + (1-beta1) \* \\ np.multiply(gradients\['db' + str(l+1)\],gradients\['db' + str(l+1)\])

\# Update parameters with RMSProp

parameters\["W" + str(l+1)\] = parameters\['W' + str(l+1)\] - \\ learningRate\* gradients\['dW' + str(l+1)\]/np.sqrt(s\["dW" + str(l+1)\] +

epsilon)

parameters\["b" + str(l+1)\] = parameters\['b' + str(l+1)\] - \\ learningRate\* gradients\['db' + str(l+1)\]/np.sqrt(s\["db" + str(l+1)\] +

epsilon)

if outputActivationFunc=="sigmoid":

s\["dW" + str(L)\] = beta1\*s\["dW" + str(L)\] + (1-beta1) \* \\ np.multiply(gradients\['dW' + str(L)\],gradients\['dW' + str(L)\]) s\["db" + str(L)\] = beta1\*s\["db" + str(L)\] + (1-beta1) \* \\ np.multiply(gradients\['db' + str(L)\],gradients\['db' + str(L)\]) parameters\["W" + str(L)\] = parameters\['W'+str(L)\] - \\ learningRate\* gradients\['dW' + str(L)\]/np.sqrt(s\["dW" + str(L)\] +

epsilon)

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] - \\ learningRate\* gradients\['db' + str(L)\]/np.sqrt(s\["db" + str(L)\] + epsilon) elif outputActivationFunc=="softmax":

s\["dW" + str(L)\] = beta1\*s\["dW" + str(L)\] + (1-beta1) \* \\ np.multiply(gradients\['dW' + str(L)\].T,gradients\['dW' + str(L)\].T) s\["db" + str(L)\] = beta1\*s\["db" + str(L)\] + (1-beta1) \* \\ np.multiply(gradients\['db' + str(L)\].T,gradients\['db' + str(L)\].T) parameters\["W" + str(L)\] = parameters\['W'+str(L)\] - \\ learningRate\* gradients\['dW' + str(L)\].T/np.sqrt(s\["dW" + str(L)\] +

epsilon)

parameters\["b" + str(L)\] = parameters\['b'+str(L)\] - \\ learningRate\* gradients\['db' + str(L)\].T/np.sqrt(s\["db" + str(L)\] +

epsilon)

return parameters, s

\# Update parameters with Adam

\# Input : parameters

\# : gradients

\# : v

\# : s

\# : t

\# : beta1

\# : beta2

\# : epsilon

\# : learningRate

\# : outputActivationFunc - sigmoid/softmax

\# output : Updated parameters and RMSProp

def gradientDescentWithAdam(parameters, gradients, v, s, t,

beta1 = 0.9, beta2 = 0.999, epsilon = 1e-8,

learningRate=0.1, outputActivationFunc="sigmoid"):

L = len(parameters) // 2

\# Initializing first moment estimate, python dictionary

v\_corrected = {}

\# Initializing second moment estimate, python dictionary

s\_corrected = {}

\# Perform Adam upto L-1

for l in range(L-1):

\# Compute momentum

v\["dW" + str(l+1)\] = beta1\*v\["dW" + str(l+1)\] + \\ (1-beta1) \* gradients\['dW' + str(l+1)\]

v\["db" + str(l+1)\] = beta1\*v\["db" + str(l+1)\] + \\ (1-beta1) \* gradients\['db' + str(l+1)\]

\# Compute bias-corrected first moment estimate.

v\_corrected\["dW" + str(l+1)\] = v\["dW" + str(l+1)\]/(1-np.power(beta1,t)) v\_corrected\["db" + str(l+1)\] = v\["db" + str(l+1)\]/(1-np.power(beta1,t))

 # Moving average of the squared gradients like RMSProp s\["dW" + str(l+1)\] = beta2\*s\["dW" + str(l+1)\] + \\ (1-beta2) \* np.multiply(gradients\['dW' + str(l+1)\],gradients\['dW' +

str(l+1)\])

s\["db" + str(l+1)\] = beta2\*s\["db" + str(l+1)\] + \\ (1-beta2) \* np.multiply(gradients\['db' + str(l+1)\],gradients\['db' +

str(l+1)\])

\# Compute bias-corrected second raw moment estimate.

s\_corrected\["dW" + str(l+1)\] = s\["dW" + str(l+1)\]/(1-np.power(beta2,t)) s\_corrected\["db" + str(l+1)\] = s\["db" + str(l+1)\]/(1-np.power(beta2,t))

\# Update parameters.

d1=np.sqrt(s\_corrected\["dW" + str(l+1)\]+epsilon)

d2=np.sqrt(s\_corrected\["db" + str(l+1)\]+epsilon)

parameters\["W" + str(l+1)\] = parameters\['W' + str(l+1)\]- \\ (learningRate\* v\_corrected\["dW" + str(l+1)\]/d1)

parameters\["b" + str(l+1)\] = parameters\['b' + str(l+1)\] - \\ (learningRate\* v\_corrected\["db" + str(l+1)\]/d2)

if outputActivationFunc=="sigmoid":

#Compute 1st moment for L

v\["dW" + str(L)\] = beta1\*v\["dW" + str(L)\] + (1-beta1) \* gradients\['dW'

\+ str(L)\]

v\["db" + str(L)\] = beta1\*v\["db" + str(L)\] + (1-beta1) \* gradients\['db' +

str(L)\]

\# Compute bias-corrected first moment estimate.

v\_corrected\["dW" + str(L)\] = v\["dW" + str(L)\]/(1-np.power(beta1,t)) v\_corrected\["db" + str(L)\] = v\["db" + str(L)\]/(1-np.power(beta1,t))

\# Compute 2nd moment for L

s\["dW" + str(L)\] = beta2\*s\["dW" + str(L)\] + (1-beta2) \* \\ np.multiply(gradients\['dW' + str(L)\],gradients\['dW' + str(L)\]) s\["db" + str(L)\] = beta2\*s\["db" + str(L)\] + (1-beta2) \* \\ np.multiply(gradients\['db' + str(L)\],gradients\['db' + str(L)\])

\# Compute bias-corrected second raw moment estimate.

s\_corrected\["dW" + str(L)\] = s\["dW" + str(L)\]/(1-np.power(beta2,t))

 s\_corrected\["db" + str(L)\] = s\["db" + str(L)\]/(1-np.power(beta2,t))

\# Update parameters.

d1=np.sqrt(s\_corrected\["dW" + str(L)\]+epsilon)

d2=np.sqrt(s\_corrected\["db" + str(L)\]+epsilon)

parameters\["W" + str(L)\] = parameters\['W' + str(L)\]- \\ (learningRate\* v\_corrected\["dW" + str(L)\]/d1)

parameters\["b" + str(L)\] = parameters\['b' + str(L)\] - \\ (learningRate\* v\_corrected\["db" + str(L)\]/d2)

elif outputActivationFunc=="softmax":

\# Compute 1st moment

v\["dW" + str(L)\] = beta1\*v\["dW" + str(L)\] + (1-beta1) \* gradients\['dW'

\+ str(L)\].T

v\["db" + str(L)\] = beta1\*v\["db" + str(L)\] + (1-beta1) \* gradients\['db' +

str(L)\].T

\# Compute bias-corrected first moment estimate.

v\_corrected\["dW" + str(L)\] = v\["dW" + str(L)\]/(1-np.power(beta1,t)) v\_corrected\["db" + str(L)\] = v\["db" + str(L)\]/(1-np.power(beta1,t))

#Compute 2nd moment

s\["dW" + str(L)\] = beta2\*s\["dW" + str(L)\] + (1-beta2) \*

np.multiply(gradients\['dW' + str(L)\].T,gradients\['dW' + str(L)\].T) s\["db" + str(L)\] = beta2\*s\["db" + str(L)\] + (1-beta2) \*

np.multiply(gradients\['db' + str(L)\].T,gradients\['db' + str(L)\].T)

\# Compute bias-corrected second raw moment estimate.

s\_corrected\["dW" + str(L)\] = s\["dW" + str(L)\]/(1-np.power(beta2,t)) s\_corrected\["db" + str(L)\] = s\["db" + str(L)\]/(1-np.power(beta2,t))

\# Update parameters.

d1=np.sqrt(s\_corrected\["dW" + str(L)\]+epsilon)

d2=np.sqrt(s\_corrected\["db" + str(L)\]+epsilon)

parameters\["W" + str(L)\] = parameters\['W' + str(L)\]- \\ (learningRate\* v\_corrected\["dW" + str(L)\]/d1)

parameters\["b" + str(L)\] = parameters\['b' + str(L)\] - \\ (learningRate\* v\_corrected\["db" + str(L)\]/d2)

return parameters, v, s

\# Execute a L layer Deep learning model

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu

/tanh/sigmoid

\# : outputActivationFunc - Activation function at output layer sigmoid/softmax

\# : learning rate

\# : lambd

\# : keep\_prob

\# : num of iteration

\# : initType

#output : parameters

def L\_Layer\_DeepModel(X1, Y1, layersDimensions,

hiddenActivationFunc='relu', outputActivationFunc="sigmoid", learningRate = .3, lambd=0, keep\_prob=1, num\_iterations =

10000,initType="default", print\_cost=False,figure="figa.png"): np.random.seed(1)

costs = \[\]

\# Parameters initialization.

if initType == "He":

parameters = HeInitializeDeepModel(layersDimensions)

elif initType == "Xavier" :

parameters = XavInitializeDeepModel(layersDimensions)

else: #Default

parameters = initializeDeepModel(layersDimensions)

\# Loop (gradient descent)

for i in range(0, num\_iterations):

AL, caches, dropoutMat = forwardPropagationDeep(X1, parameters, keep\_prob,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc)

 # Regularization parameter is 0

if lambd==0:

\# Compute cost

cost = computeCost(parameters,AL, Y1,

outputActivationFunc=outputActivationFunc)

\# Include L2 regularization

else:

\# Compute cost

cost = computeCostWithReg(parameters,AL, Y1, lambd,

outputActivationFunc=outputActivationFunc)

\# Backward propagation.

gradients = backwardPropagationDeep(AL, Y1, caches, dropoutMat, lambd, keep\_prob,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc)

\# Update parameters.

parameters = gradientDescent(parameters, gradients,

learningRate=learningRate,outputActivationFunc=outputActivationFunc)

\# Print the cost every 100 training example

if print\_cost and i % 1000 == 0:

print ("Cost after iteration %i: %f" %(i, cost))

if print\_cost and i % 1000 == 0:

costs.append(cost)

\# plot the cost

plt.plot(np.squeeze(costs))

plt.ylabel('Cost')

plt.xlabel('No of iterations (x1000)')

plt.title("Learning rate =" + str(learningRate))

plt.savefig(figure,bbox\_inches='tight')

#plt.show()

plt.clf()

plt.close()

return parameters

\# Execute a L layer Deep learning model Stoachastic Gradient Descent

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu

/tanh/sigmoid

\# : outputActivationFunc - Activation function at output - sigmoid/softmax

\# : learning rate

\# : lrDecay

\# : lambd

\# : keep\_prob

\# : optimizer

\# : beta

\# : beta1

\# : beta2

\# : epsilon

\# : mini\_batch\_size

\# : num\_epochs

\# :

#output : Updated weights and biases

def L\_Layer\_DeepModel\_SGD(X1, Y1, layersDimensions,

hiddenActivationFunc='relu', outputActivationFunc="sigmoid", learningRate = .3, lrDecay=False, decayRate=1,

lambd=0, keep\_prob=1, optimizer="gd",beta=0.9,beta1=0.9, beta2=0.999,

epsilon = 1e-8,mini\_batch\_size = 64, num\_epochs = 2500,

print\_cost=False, figure="figa.png"):

print("lr=",learningRate)

print("lrDecay=",lrDecay)

print("decayRate=",decayRate)

print("lambd=",lambd)

print("keep\_prob=",keep\_prob)

print("optimizer=",optimizer)

print("beta=",beta)

print("beta1=",beta1)

print("beta2=",beta2)

 print("epsilon=",epsilon)

print("mini\_batch\_size=",mini\_batch\_size)

print("num\_epochs=",num\_epochs)

print("epsilon=",epsilon)

t =0 # Adam counter

np.random.seed(1)

costs = \[\]

\# Parameters initialization.

parameters = initializeDeepModel(layersDimensions)

#Initialize the optimizer

if optimizer == "gd":

pass # no initialization required for gradient descent

elif optimizer == "momentum":

v = initializeVelocity(parameters)

elif optimizer == "rmsprop":

s = initializeRMSProp(parameters)

elif optimizer == "adam":

v,s = initializeAdam(parameters)

seed=10

\# Loop for number of epochs

for i in range(num\_epochs):

\# Define the random minibatches. We increment the seed to reshuffle differently the dataset after each epoch

seed = seed + 1

minibatches = random\_mini\_batches(X1, Y1, mini\_batch\_size, seed) batch=0

\# Loop through each mini batch

for minibatch in minibatches:

#print("batch=",batch)

batch=batch+1

\# Select a minibatch

(minibatch\_X, minibatch\_Y) = minibatch

\# Perfrom forward propagation

AL, caches, dropoutMat = forwardPropagationDeep(minibatch\_X,

parameters, keep\_prob,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc)

\# Compute cost

\# Regularization parameter is 0

if lambd==0:

\# Compute cost

cost = computeCost(parameters, AL, minibatch\_Y,

outputActivationFunc=outputActivationFunc)

else: # Include L2 regularization

\# Compute cost

cost = computeCostWithReg(parameters, AL, minibatch\_Y, lambd, outputActivationFunc=outputActivationFunc)

\# Backward propagation.

gradients = backwardPropagationDeep(AL, minibatch\_Y,

caches,dropoutMat, lambd,

keep\_prob,hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc) if optimizer == "gd":

\# Update parameters normal gradient descent

parameters = gradientDescent(parameters, gradients,

learningRate=learningRate,outputActivationFunc=outputActivationFunc) elif optimizer == "momentum":

\# Update parameters for gradient descent with momentum

parameters, v = gradientDescentWithMomentum(parameters, gradients, v, beta, \\

learningRate=learningRate,outputActivationFunc=outputActivationFunc) elif optimizer == "rmsprop":

\# Update parameters for gradient descent with RMSProp

parameters, s = gradientDescentWithRMSProp(parameters, gradients, s, beta1, epsilon, \\

learningRate=learningRate,outputActivationFunc=outputActivationFunc) elif optimizer == "adam":

 t = t + 1 # Adam counter

parameters, v, s = gradientDescentWithAdam(parameters, gradients, v, s,

t, beta1, beta2, epsilon,

learningRate=learningRate,outputActivationFunc=outputActivationFunc)

\# Print the cost every 1000 epoch

if print\_cost and i % 100 == 0:

print ("Cost after epoch %i: %f" %(i, cost))

if print\_cost and i % 100 == 0:

costs.append(cost)

if lrDecay == True:

learningRate = np.power(decayRate,(num\_epochs/1000)) \* learningRate

\# plot the cost

plt.plot(np.squeeze(costs))

plt.ylabel('Cost')

plt.xlabel('No of epochs(x100)')

plt.title("Learning rate =" + str(learningRate))

plt.savefig(figure,bbox\_inches='tight')

#plt.show()

plt.clf()

plt.close()

\# Create random mini batches

\# Input : X - Input features

\# : Y- output

\# : miniBatchSizes

\# : seed

#output : mini\_batches

def random\_mini\_batches(X, Y, miniBatchSize = 64, seed = 0):

np.random.seed(seed)

\# Get number of training samples

m = X.shape\[1\]

\# Initialize mini batches

 mini\_batches = \[\]

\# Create a list of random numbers < m

permutation = list(np.random.permutation(m))

\# Randomly shuffle the training data

shuffled\_X = X\[:, permutation\]

shuffled\_Y = Y\[:, permutation\].reshape((1,m))

\# Compute number of mini batches

numCompleteMinibatches = math.floor(m/miniBatchSize)

\# For the number of mini batches

for k in range(0, numCompleteMinibatches):

\# Set the start and end of each mini batch

mini\_batch\_X = shuffled\_X\[:, k\*miniBatchSize : (k+1) \* miniBatchSize\]

mini\_batch\_Y = shuffled\_Y\[:, k\*miniBatchSize : (k+1) \* miniBatchSize\]

mini\_batch = (mini\_batch\_X, mini\_batch\_Y)

mini\_batches.append(mini\_batch)

#if m % miniBatchSize != 0:. The batch does not evenly divide by the mini batch

if m % miniBatchSize != 0:

l=math.floor(m/miniBatchSize)\*miniBatchSize

\# Set the start and end of last mini batch

m=l+m % miniBatchSize

mini\_batch\_X = shuffled\_X\[:,l:m\]

mini\_batch\_Y = shuffled\_Y\[:,l:m\]

mini\_batch = (mini\_batch\_X, mini\_batch\_Y)

mini\_batches.append(mini\_batch)

return mini\_batches

\# Plot a decision boundary

\# Input : Input Model,

\# X

\# Y

\# sz - Num of hiden units

\# lr - Learning rate

\# Fig to be saved as

\# Returns Null

def plot\_decision\_boundary(model, X, y,lr,figure1="figb.png"): print("plot")

\# Set min and max values and give it some padding

x\_min, x\_max = X\[0, :\].min() - 1, X\[0, :\].max() + 1

y\_min, y\_max = X\[1, :\].min() - 1, X\[1, :\].max() + 1

colors=\['black','gold'\]

cmap = matplotlib.colors.ListedColormap(colors)

h = 0.01

\# Generate a grid of points with distance h between them

xx, yy = np.meshgrid(np.arange(x\_min, x\_max, h), np.arange(y\_min, y\_max, h))

\# Predict the function value for the whole grid

Z = model(np.c\_\[xx.ravel(), yy.ravel()\])

Z = Z.reshape(xx.shape)

\# Plot the contour and training examples

plt.contourf(xx, yy, Z, cmap="coolwarm")

plt.ylabel('x2')

plt.xlabel('x1')

x=X.T

y=y.T.reshape(300,)

plt.scatter(x\[:, 0\], x\[:, 1\], c=y, s=20);

print(X.shape)

plt.title("Decision Boundary for learning rate:"+lr) plt.savefig(figure1, bbox\_inches='tight')

#plt.show()

\# Predict output

def predict(parameters,

X,keep\_prob=1,hiddenActivationFunc="relu",outputActivationFunc="sigmoid"): A2, cache,dropoutMat = forwardPropagationDeep(X, parameters,

keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc) predictions = (A2>0.5)

 return predictions

\# Predict probability

def predict\_proba(parameters, X,outputActivationFunc="sigmoid"): A2, cache = forwardPropagationDeep(X, parameters)

if outputActivationFunc=="sigmoid":

proba=A2

elif outputActivationFunc=="softmax":

proba=np.argmax(A2, axis=0).reshape(-1,1)

print("A2=",A2.shape)

return proba

\# Plot a decision boundary

\# Input : Input Model,

\# X

\# Y

\# sz - Num of hiden units

\# lr - Learning rate

\# Fig to be saved as

\# Returns Null

def plot\_decision\_boundary1(X, y,W1,b1,W2,b2,figure2="figc.png"):

#plot\_decision\_boundary(lambda x: predict(parameters, x.T),

x1,y1.T,str(0.3),"fig2.png")

h = 0.02

x\_min, x\_max = X\[:, 0\].min() - 1, X\[:, 0\].max() + 1

y\_min, y\_max = X\[:, 1\].min() - 1, X\[:, 1\].max() + 1

xx, yy = np.meshgrid(np.arange(x\_min, x\_max, h),

np.arange(y\_min, y\_max, h))

Z = np.dot(np.maximum(0, np.dot(np.c\_\[xx.ravel(), yy.ravel()\], W1.T) +

b1.T), W2.T) + b2.T

Z = np.argmax(Z, axis=1)

Z = Z.reshape(xx.shape)

fig = plt.figure()

plt.contourf(xx, yy, Z, cmap=plt.cm.Spectral, alpha=0.8)

print(X.shape)

y1=y.reshape(300,)

plt.scatter(X\[:, 0\], X\[:, 1\], c=y1, s=40, cmap=plt.cm.Spectral) plt.xlim(xx.min(), xx.max())

 plt.ylim(yy.min(), yy.max())

plt.savefig(figure2, bbox\_inches='tight')

\# Load the circles dataset

def load\_dataset():

np.random.seed(1)

train\_X, train\_Y = sklearn.datasets.make\_circles(n\_samples=300, noise=.05) np.random.seed(2)

test\_X, test\_Y = sklearn.datasets.make\_circles(n\_samples=100, noise=.05)

\# Visualize the data

print(train\_X.shape)

print(train\_Y.shape)

#plt.scatter(train\_X\[:, 0\], train\_X\[:, 1\], c=train\_Y, s=40,

cmap=plt.cm.Spectral);

train\_X = train\_X.T

train\_Y = train\_Y.reshape((1, train\_Y.shape\[0\]))

test\_X = test\_X.T

test\_Y = test\_Y.reshape((1, test\_Y.shape\[0\]))

return train\_X, train\_Y, test\_X, test\_Y

#############

\# Note: Using dictionary\_to\_vector followed by vector\_to\_dictionary => original dictionary

##############

\# Convert a weight,biases dictionary to a vector

\# Input : parameter dictionary

\# Returns : vector

def dictionary\_to\_vector(parameters):

"""

Roll all our parameters dictionary into a single vector satisfying our specific required shape.

"""

keys = \[\]

count = 0

for key in parameters:

\# flatten parameter

new\_vector = np.reshape(parameters\[key\], (-1,1))

keys = keys + \[key\]\*new\_vector.shape\[0\]

 if count == 0:

theta = new\_vector

else:

theta = np.concatenate((theta, new\_vector), axis=0)

count = count + 1

return theta, keys

\# Convert a gradient dictionary to a vector

\# Input : parameter

\# : gradient dictionary

\# Returns : gradient vector

def gradients\_to\_vector(parameters, gradients):

#Roll all our gradients dictionary into a single vector satisfying our specific required shape.

keyvals=\[\]

L=len(parameters)//2

count = 0

for l in range(L):

\# flatten parameter

keyvals.append('dW'+str(l+1))

keyvals.append('db'+str(l+1))

for key in keyvals:

new\_vector = np.reshape(gradients\[key\], (-1,1))

if count == 0:

theta = new\_vector

else:

theta = np.concatenate((theta, new\_vector), axis=0)

count = count + 1

return theta

\# Convert a vector to a dictionary

\# Input : parameter

\# : theta

\# Returns : parameters1 (dictionary)

def vector\_to\_dictionary(parameters,theta):

#Unroll all our parameters dictionary from a single vector satisfying our specific required shape.

start=0

parameters1 = {}

#For key

for key in parameters:

(a,b) = parameters\[key\].shape

\# Create a dictionary

parameters1\[key\]= theta\[start:start+a\*b\].reshape((a,b))

start=start+a\*b

return parameters1

\# Convert a vector to a dictionary

\# Input : parameter

\# : theta

\# Returns : parameters1 (dictionary)

def vector\_to\_dictionary2(parameters,theta):

#Unroll all our parameters dictionary from a single vector satisfying our specific required shape.

start=0

parameters2= {}

\# For key

for key in parameters:

(a,b) = parameters\[key\].shape

\# Create a key value pair

parameters2\['d'+key\]= theta\[start:start+a\*b\].reshape((a,b))

start=start+a\*b

return parameters2

\# Perform a gradient check

\# Input : parameters

\# : gradients

\# : train\_X

\# : train\_Y

\# : epsilon

\# : outputActivationFunc

\# Returns :

def gradient\_check\_n(parameters, gradients, train\_X, train\_Y, epsilon = 1e-7,outputActivationFunc="sigmoid"):

\# Set-up variables

parameters\_values, \_ = dictionary\_to\_vector(parameters)

grad = gradients\_to\_vector(parameters,gradients)

num\_parameters = parameters\_values.shape\[0\]

J\_plus = np.zeros((num\_parameters, 1))

J\_minus = np.zeros((num\_parameters, 1))

gradapprox = np.zeros((num\_parameters, 1))

\# Compute gradapprox using 2 sided derivative

for i in range(num\_parameters):

\# Compute J\_plus\[i\]. Inputs: "parameters\_values, epsilon". Output =

"J\_plus\[i\]".

thetaplus = np.copy(parameters\_values)

thetaplus\[i\]\[0\] = thetaplus\[i\]\[0\] + epsilon

AL, caches, dropoutMat = forwardPropagationDeep(train\_X,

vector\_to\_dictionary(parameters,thetaplus), keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc) J\_plus\[i\] = computeCost(AL, train\_Y,

outputActivationFunc=outputActivationFunc)

\# Compute J\_minus\[i\]. Inputs: "parameters\_values, epsilon". Output =

"J\_minus\[i\]".

thetaminus = np.copy(parameters\_values)

thetaminus\[i\]\[0\] = thetaminus\[i\]\[0\] - epsilon

AL, caches, dropoutMat = forwardPropagationDeep(train\_X,

vector\_to\_dictionary(parameters,thetaminus), keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc) J\_minus\[i\] = computeCost(AL, train\_Y,

outputActivationFunc=outputActivationFunc)

\# Compute gradapprox\[i\]

gradapprox\[i\] = (J\_plus\[i\] - J\_minus\[i\])/(2\*epsilon)

\# Compare gradapprox to backward propagation gradients by computing difference.

numerator = np.linalg.norm(grad-gradapprox)

denominator = np.linalg.norm(grad) +

np.linalg.norm(gradapprox)

difference = numerator/denominator

if difference > 1e-5:

print ("\\033\[93m" + "There is a mistake in the backward propagation!

difference = " + str(difference) + "\\033\[0m")

else:

print ("\\033\[92m" + "Your backward propagation works perfectly fine!

difference = " + str(difference) + "\\033\[0m")

print(difference)

print("\\n")

\# Covert grad to dictionary

m=vector\_to\_dictionary2(parameters,grad)

print("Gradients from backprop")

print(m)

print("\\n")

\# Convert gradapprox to dictionary

n=vector\_to\_dictionary2(parameters,gradapprox)

print("Gradapprox from gradient check")

print(n)

**8.2 R**

############################################################################################################

#

\# File : DLfunctions8.R

\# Author : Tinniam V Ganesh

\# Date : 6 May 2018

#

##########################################################################################################

library(ggplot2)

library(PRROC)

library(dplyr)

\# Compute the sigmoid of a vector

sigmoid <- function(Z){

A <- 1/(1+ exp(-Z))

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# This is the older version. Very performance intensive

reluOld <-function(Z){

A <- apply(Z, 1:2, function(x) max(0,x))

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the Relu of a vector (current version)

relu <-function(Z){

\# Perform relu. Set values less that equal to 0 as 0

Z\[Z<0\]=0

A=Z

cache<-Z

retvals <- list("A"=A,"Z"=Z)

 return(retvals)

}

\# Compute the tanh activation of a vector

tanhActivation <- function(Z){

A <- tanh(Z)

cache<-Z

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Conmpute the softmax of a vector

softmax <- function(Z){

\# get unnormalized probabilities

exp\_scores = exp(t(Z))

\# normalize them for each example

A = exp\_scores / rowSums(exp\_scores)

retvals <- list("A"=A,"Z"=Z)

return(retvals)

}

\# Compute the derivative of Relu

\# g'(z) = 1 if z >0 and 0 otherwise

reluDerivative <-function(dA, cache){

Z <- cache

dZ <- dA

\# Create a logical matrix of values > 0

a <- Z > 0

\# When z <= 0, you should set dz to 0 as well. Perform an element wise multiply

dZ <- dZ \* a

return(dZ)

}

\# Compute the derivative of sigmoid

\# Derivative g'(z) = a\* (1-a)

sigmoidDerivative <- function(dA, cache){

Z <- cache

s <- 1/(1+exp(-Z))

 dZ <- dA \* s \* (1-s)

return(dZ)

}

\# Compute the derivative of tanh

\# Derivative g'(z) = 1- a^2

tanhDerivative <- function(dA, cache){

Z = cache

a = tanh(Z)

dZ = dA \* (1 - a^2)

return(dZ)

}

\# Populate a matrix of 1s in rows where Y==1

\# This may need to be extended for K classes. Currently

\# supports K=3 & K=10

popMatrix <- function(Y,numClasses){

a=rep(0,times=length(Y))

Y1=matrix(a,nrow=length(Y),ncol=numClasses)

#Set the rows and columns as 1's where Y is the class value

if(numClasses==3){

Y1\[Y==0,1\]=1

Y1\[Y==1,2\]=1

Y1\[Y==2,3\]=1

} else if (numClasses==10){

Y1\[Y==0,1\]=1

Y1\[Y==1,2\]=1

Y1\[Y==2,3\]=1

Y1\[Y==3,4\]=1

Y1\[Y==4,5\]=1

Y1\[Y==5,6\]=1

Y1\[Y==6,7\]=1

Y1\[Y==7,8\]=1

Y1\[Y==8,9\]=1

Y1\[Y==9,0\]=1

}

return(Y1)

}

\# Compute the softmax derivative

softmaxDerivative <- function(dA, cache ,y,numTraining,numClasses){

\# Note : dA not used. dL/dZ = dL/dA \* dA/dZ = pi-yi

Z <- cache

\# Compute softmax

exp\_scores = exp(t(Z))

\# normalize them for each example

probs = exp\_scores / rowSums(exp\_scores)

\# Create a matrix of zeros

Y1=popMatrix(y,numClasses)

#a=rep(0,times=length(Y))

#Y1=matrix(a,nrow=length(Y),ncol=numClasses)

#Set the rows and columns as 1's where Y is the class value

dZ = probs-Y1

return(dZ)

}

\# Initialize model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers initializeDeepModel <- function(layerDimensions){

set.seed(2)

\# Initialize empty list

layerParams <- list()

\# Note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Indices in R start from 1

for(l in 2:length(layersDimensions)){

\# Initialize a matrix of small random numbers of size l x l-1

\# Create random numbers of size l x l-1

w=rnorm(layersDimensions\[l\]\*layersDimensions\[l-1\])\*0.01

\# Create a weight matrix of size l x l-1 with this initial weights and

\# Add to list W1,W2... WL

layerParams\[\[paste('W',l-1,sep="")\]\] = matrix(w,nrow=layersDimensions\[l\],

 ncol=layersDimensions\[l-1\]) layerParams\[\[paste('b',l-1,sep="")\]\] = matrix(rep(0,layersDimensions\[l\]), nrow=layersDimensions\[l\],ncol=1)

}

return(layerParams)

}

\# He Initialization model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers

\# He initilization multiplies the random numbers with

sqrt(2/layerDimensions\[previouslayer\])

HeInitializeDeepModel <- function(layerDimensions){

set.seed(2)

\# Initialize empty list

layerParams <- list()

\# Note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Indices in R start from 1

for(l in 2:length(layersDimensions)){

\# Initialize a matrix of small random numbers of size l x l-1

\# Create random numbers of size l x l-1

w=rnorm(layersDimensions\[l\]\*layersDimensions\[l-1\])

\# Create a weight matrix of size l x l-1 with this initial weights and

\# Add to list W1,W2... WL

\# He initialization - Divide by sqrt(2/layerDimensions\[previous layer\]) layerParams\[\[paste('W',l-1,sep="")\]\] =

matrix(w,nrow=layersDimensions\[l\],

ncol=layersDimensions\[l-

1\])\*sqrt(2/layersDimensions\[l-1\])

layerParams\[\[paste('b',l-1,sep="")\]\] = matrix(rep(0,layersDimensions\[l\]), nrow=layersDimensions\[l\],ncol=1)

 }

return(layerParams)

}

\# XavInitializeDeepModel Initialization model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers

\# He initilization multiplies the random numbers with

sqrt(1/layerDimensions\[previouslayer\])

XavInitializeDeepModel <- function(layerDimensions){

set.seed(2)

\# Initialize empty list

layerParams <- list()

\# Note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Indices in R start from 1

for(l in 2:length(layersDimensions)){

\# Initialize a matrix of small random numbers of size l x l-1

\# Create random numbers of size l x l-1

w=rnorm(layersDimensions\[l\]\*layersDimensions\[l-1\])

\# Create a weight matrix of size l x l-1 with this initial weights and

\# Add to list W1,W2... WL

\# He initialization - Divide by sqrt(2/layerDimensions\[previous layer\]) layerParams\[\[paste('W',l-1,sep="")\]\] =

matrix(w,nrow=layersDimensions\[l\],

ncol=layersDimensions\[l-

1\])\*sqrt(1/layersDimensions\[l-1\])

layerParams\[\[paste('b',l-1,sep="")\]\] = matrix(rep(0,layersDimensions\[l\]), nrow=layersDimensions\[l\],ncol=1)

}

return(layerParams)

}

\# Initialize velocity

\# Input : parameters

\# Returns: v -Initial velocity

initializeVelocity <- function(parameters){

L <- length(parameters)/2

v <- list()

\# Initialize velocity with the same dimensions as W

for(l in 1:L){

\# Get the size of weight matrix

sz <- dim(parameters\[\[paste('W',l,sep="")\]\])

v\[\[paste('dW',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

#Get the size of bias matrix

sz <- dim(parameters\[\[paste('b',l,sep="")\]\])

v\[\[paste('db',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

}

return(v)

}

\# Initialize RMSProp

\# Input : parameters

\# Returns: s - Initial RMSProp

initializeRMSProp <- function(parameters){

L <- length(parameters)/2

s <- list()

\# Initialize velocity with the same dimensions as W

for(l in 1:L){

\# Get the size of weight matrix

sz <- dim(parameters\[\[paste('W',l,sep="")\]\])

s\[\[paste('dW',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

#Get the size of bias matrix

sz <- dim(parameters\[\[paste('b',l,sep="")\]\])

 s\[\[paste('db',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

}

return(s)

}

\# Initialize Adam

\# Input : parameters

\# Returns: (v,s) - Initial Adam parameters

initializeAdam <- function(parameters){

L <- length(parameters)/2

v <- list()

s <- list()

\# Initialize velocity with the same dimensions as W

for(l in 1:L){

\# Get the size of weight matrix

sz <- dim(parameters\[\[paste('W',l,sep="")\]\])

v\[\[paste('dW',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

s\[\[paste('dW',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

#Get the size of bias matrix

sz <- dim(parameters\[\[paste('b',l,sep="")\]\])

v\[\[paste('db',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

s\[\[paste('db',l,sep="")\]\] = matrix(rep(0,sz\[1\]\*sz\[2\]), nrow=sz\[1\],ncol=sz\[2\])

}

retvals <- list("v"=v,"s"=s)

return(retvals)

}

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prev - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : The Activation of this layer

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

layerActivationForward <- function(A\_prev, W, b, activationFunc){

\# Compute Z

z = W %\*% A\_prev

\# Broadcast the bias 'b' by column

Z <-sweep(z,1,b,'+')

forward\_cache <- list("A\_prev"=A\_prev, "W"=W, "b"=b)

\# Compute the activation for sigmoid

if(activationFunc == "sigmoid"){

vals = sigmoid(Z)

} else if (activationFunc == "relu"){ # Compute the activation for relu vals = relu(Z)

} else if(activationFunc == 'tanh'){ # Compute the activation for tanh vals = tanhActivation(Z)

} else if(activationFunc == 'softmax'){

vals = softmax(Z)

}

\# Create a list of forward and activation cache

cache <- list("forward\_cache"=forward\_cache, "activation\_cache"=vals\[\['Z'\]\]) retvals <- list("A"=vals\[\['A'\]\],"cache"=cache) return(retvals)

}

\# Compute the forward propagation for layers 1..L

\# Input : X - Input Features

\# parameters: Weights and biases

\# keep\_prob

\# hiddenActivationFunc - relu/sigmoid/tanh

\# outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# Returns : AL

\# caches

\# dropoutMat

\# The forward propoagtion uses the Relu/tanh activation from layer 1..L-1 and

sigmoid actiovation at layer L

forwardPropagationDeep <- function(X, parameters,keep\_prob=1, hiddenActivationFunc='relu',

outputActivationFunc='sigmoid'){

caches <- list()

dropoutMat <- list()

\# Set A to X (A0)

A <- X

L <- length(parameters)/2 # number of layers in the neural network

\# Loop through from layer 1 to upto layer L

for(l in 1:(L-1)){

A\_prev <- A

\# Zi = Wi x Ai-1 + bi and Ai = g(Zi)

\# Set W and b for layer 'l'

\# Loop throug from W1,W2... WL-1

W <- parameters\[\[paste("W",l,sep="")\]\]

b <- parameters\[\[paste("b",l,sep="")\]\]

\# Compute the forward propagation through layer 'l' using the activation function

actForward <- layerActivationForward(A\_prev,

W,

b,

activationFunc = hiddenActivationFunc)

A <- actForward\[\['A'\]\]

\# Append the cache A\_prev,W,b, Z

caches\[\[l\]\] <-actForward

\# Randomly drop some activation units

\# Create a matrix as the same shape as A

set.seed(1)

i=dim(A)\[1\]

j=dim(A)\[2\]

a<-rnorm(i\*j)

\# Normalize a between 0 and 1

a = (a - min(a))/(max(a) - min(a))

\# Create a matrix of D

D <- matrix(a,nrow=i, ncol=j)

\# Find D which is less than equal to keep\_prob

D <- D < keep\_prob

 # Remove some A's

A <- A \* D

\# Divide by keep\_prob to keep expected value same

A <- A/keep\_prob

dropoutMat\[\[paste("D",l,sep="")\]\] <- D

}

\# Since this is binary classification use the sigmoid activation function in

\# last layer

\# Set the weights and biases for the last layer

W <- parameters\[\[paste("W",L,sep="")\]\]

b <- parameters\[\[paste("b",L,sep="")\]\]

\# Last layer

actForward = layerActivationForward(A, W, b, activationFunc =

outputActivationFunc)

AL <- actForward\[\['A'\]\]

\# Append the output of this forward propagation through the last layer caches\[\[L\]\] <- actForward

\# Create a list of the final output and the caches

fwdPropDeep <- list("AL"=AL,"caches"=caches,"dropoutMat"=dropoutMat) return(fwdPropDeep)

}

\# Function pickColumns(). This function is in computeCost()

\# Pick columns

\# Input : AL

\# : Y

\# : numClasses

\# Output: a

pickColumns <- function(AL,Y,numClasses){

if(numClasses==3){

a=c(AL\[Y==0,1\],AL\[Y==1,2\],AL\[Y==2,3\])

}

else if (numClasses==10){

a=c(AL\[Y==0,1\],AL\[Y==1,2\],AL\[Y==2,3\],AL\[Y==3,4\],AL\[Y==4,5\],

AL\[Y==5,6\],AL\[Y==6,7\],AL\[Y==7,8\],AL\[Y==8,9\],AL\[Y==9,10\])

}

return(a)

}

\# Compute the cost

\# Input : Activation of last layer

\# : Output from data

\# :outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : numClasses

\# Output: cost

computeCost <-

function(AL,Y,outputActivationFunc="sigmoid",numClasses=3){

if(outputActivationFunc=="sigmoid"){

m= length(Y)

cost=-1/m\*sum(Y\*log(AL) + (1-Y)\*log(1-AL))

}else if (outputActivationFunc=="softmax"){

\# Select the elements where the y values are 0, 1 or 2 and make a vector

\# Pick columns

#a=c(AL\[Y==0,1\],AL\[Y==1,2\],AL\[Y==2,3\])

m= length(Y)

a =pickColumns(AL,Y,numClasses)

#a = c(A2\[y=k,k+1\])

\# Take log

correct\_probs = -log(a)

\# Compute loss

cost= sum(correct\_probs)/m

}

return(cost)

}

\# Compute the cost with Regularization

\# Input : parameters

\# : AL-Activation of last layer

\# : Y-Output from data

\# : lambd

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : numClasses

\# Output: cost

computeCostWithReg <- function(parameters, AL,Y,lambd,

outputActivationFunc="sigmoid",numClasses=3){

if(outputActivationFunc=="sigmoid"){

m= length(Y)

cost=-1/m\*sum(Y\*log(AL) + (1-Y)\*log(1-AL))

\# Regularization cost

L <- length(parameters)/2

L2RegularizationCost=0

for(l in 1:L){

L2RegularizationCost = L2RegularizationCost +

sum(parameters\[\[paste("W",l,sep="")\]\]^2)

}

L2RegularizationCost = (lambd/(2\*m))\*L2RegularizationCost

cost = cost + L2RegularizationCost

}else if (outputActivationFunc=="softmax"){

\# Select the elements where the y values are 0, 1 or 2 and make a vector

\# Pick columns

#a=c(AL\[Y==0,1\],AL\[Y==1,2\],AL\[Y==2,3\])

m= length(Y)

a =pickColumns(AL,Y,numClasses)

#a = c(A2\[y=k,k+1\])

\# Take log

correct\_probs = -log(a)

\# Compute loss

cost= sum(correct\_probs)/m

\# Regularization cost

L <- length(parameters)/2

L2RegularizationCost=0

\# Add L2 norm

for(l in 1:L){

 L2RegularizationCost = L2RegularizationCost +

sum(parameters\[\[paste("W",l,sep="")\]\]^2)

}

L2RegularizationCost = (lambd/(2\*m))\*L2RegularizationCost

cost = cost + L2RegularizationCost

}

return(cost)

}

\# Compute the backpropagation through a layer

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# # Input features

\# # Output values Y

\# # activationFunc

\# # numClasses

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

layerActivationBackward <- function(dA, cache, Y, activationFunc,numClasses)

{

\# Get A\_prev,W,b

forward\_cache <-cache\[\['forward\_cache'\]\]

activation\_cache <- cache\[\['activation\_cache'\]\]

A\_prev <- forward\_cache\[\['A\_prev'\]\]

numtraining = dim(A\_prev)\[2\]

\# Get Z

activation\_cache <- cache\[\['activation\_cache'\]\]

if(activationFunc == "relu"){

dZ <- reluDerivative(dA, activation\_cache)

} else if(activationFunc == "sigmoid"){

dZ <- sigmoidDerivative(dA, activation\_cache)

} else if(activationFunc == "tanh"){

dZ <- tanhDerivative(dA, activation\_cache)

} else if(activationFunc == "softmax"){

dZ <- softmaxDerivative(dA, activation\_cache,Y,numtraining,numClasses)

}

if (activationFunc == 'softmax'){

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

dW = 1/numtraining \* A\_prev%\*%dZ

db = 1/numtraining\* matrix(colSums(dZ),nrow=1,ncol=numClasses) dA\_prev = dZ %\*%W

} else {

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

numtraining = dim(A\_prev)\[2\]

dW = 1/numtraining \* dZ %\*% t(A\_prev)

db = 1/numtraining \* rowSums(dZ)

dA\_prev = t(W) %\*% dZ

}

retvals <- list("dA\_prev"=dA\_prev,"dW"=dW,"db"=db) return(retvals)

}

\# Compute the backpropagation through a layer with Regularization

\# Input : dA-Neural Network parameters

\# # cache - forward\_cache & activation\_cache

\# # Output values Y

\# # lambd

\# # activationFunc

\# # numClasses

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

layerActivationBackwardWithReg <- function(dA, cache, Y, lambd, activationFunc,numClasses){

\# Get A\_prev,W,b

forward\_cache <-cache\[\['forward\_cache'\]\]

activation\_cache <- cache\[\['activation\_cache'\]\]

A\_prev <- forward\_cache\[\['A\_prev'\]\]

numtraining = dim(A\_prev)\[2\]

\# Get Z

 activation\_cache <- cache\[\['activation\_cache'\]\]

if(activationFunc == "relu"){

dZ <- reluDerivative(dA, activation\_cache)

} else if(activationFunc == "sigmoid"){

dZ <- sigmoidDerivative(dA, activation\_cache)

} else if(activationFunc == "tanh"){

dZ <- tanhDerivative(dA, activation\_cache)

} else if(activationFunc == "softmax"){

dZ <- softmaxDerivative(dA, activation\_cache,Y,numtraining,numClasses)

}

if (activationFunc == 'softmax'){

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

\# Add the regularization factor

dW = 1/numtraining \* A\_prev%\*%dZ + (lambd/numtraining) \* t(W) db = 1/numtraining\* matrix(colSums(dZ),nrow=1,ncol=numClasses) dA\_prev = dZ %\*%W

} else {

W <- forward\_cache\[\['W'\]\]

b <- forward\_cache\[\['b'\]\]

numtraining = dim(A\_prev)\[2\]

\# Add the regularization factor

dW = 1/numtraining \* dZ %\*% t(A\_prev) + (lambd/numtraining) \* W

db = 1/numtraining \* rowSums(dZ)

dA\_prev = t(W) %\*% dZ

}

retvals <- list("dA\_prev"=dA\_prev,"dW"=dW,"db"=db) return(retvals)

}

\# Compute the backpropagation for 1 cycle through all layers

\# Input : AL: Output of L layer Network - weights

\# Y Real output

\# caches -- list of caches containing:

\# every cache of layerActivationForward() with "relu"/"tanh"

\# #(it's caches\[l\], for l in range(L-1) i.e l = 0...L-2)

\# #the cache of layerActivationForward() with "sigmoid" (it's caches\[L-1\])

\# dropoutMat

\# lambd

\# keep\_prob

\# hiddenActivationFunc - Activation function at hidden layers -

relu/tanh/sigmoid

\# outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# numClasses

\# Returns:

\# gradients -- A dictionary with the gradients

\# gradients\["dA" + str(l)\]

\# gradients\["dW" + str(l)\]

\# gradients\["db" + str(l)\]

backwardPropagationDeep <- function(AL, Y, caches,dropoutMat, lambd=0, keep\_prob=0, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",numClasses){

#initialize the gradients

gradients = list()

\# Set the number of layers

L = length(caches)

numTraining = dim(AL)\[2\]

if(outputActivationFunc == "sigmoid")

\# Initializing the backpropagation

\# dl/dAL= -(y/a) - ((1-y)/(1-a)) - At the output layer

dAL = -( (Y/AL) -(1 - Y)/(1 - AL))

else if(outputActivationFunc == "softmax"){

dAL=0

Y=t(Y)

}

\# Get the gradients at the last layer

\# Inputs: "AL, Y, caches".

\# Outputs: "gradients\["dAL"\], gradients\["dWL"\], gradients\["dbL"\]

\# Start with Layer L

\# Get the current cache

current\_cache = caches\[\[L\]\]$cache

if (lambd==0){

retvals <- layerActivationBackward(dAL, current\_cache, Y, activationFunc = outputActivationFunc,numClasses)

 } else {

retvals = layerActivationBackwardWithReg(dAL, current\_cache, Y, lambd, activationFunc = outputActivationFunc,numClasses)

}

#Note: Take the transpose of dA

if(outputActivationFunc =="sigmoid")

gradients\[\[paste("dA",L,sep="")\]\] <- retvals\[\['dA\_prev'\]\]

else if(outputActivationFunc =="softmax")

gradients\[\[paste("dA",L,sep="")\]\] <- t(retvals\[\['dA\_prev'\]\]) gradients\[\[paste("dW",L,sep="")\]\] <- retvals\[\['dW'\]\]

gradients\[\[paste("db",L,sep="")\]\] <- retvals\[\['db'\]\]

\# Traverse in the reverse direction

for(l in (L-1):1){

\# Compute the gradients for L-1 to 1 for Relu/tanh

\# Inputs: "gradients\["dA" + str(l + 2)\], caches".

\# Outputs: "gradients\["dA" + str(l + 1)\] , gradients\["dW" + str(l + 1)\] , gradients\["db" + str(l + 1)\]

current\_cache = caches\[\[l\]\]$cache

if (lambd==0){

cat("l=",l)

\# Get the dropout matrix

D <-dropoutMat\[\[paste("D",l,sep="")\]\]

\# Multiply gradient with dropout matrix

gradients\[\[paste('dA',l+1,sep="")\]\] = gradients\[\[paste('dA',l+1,sep="")\]\] \*D

\# Divide by keep\_prob to keep expected value same

gradients\[\[paste('dA',l+1,sep="")\]\] =

gradients\[\[paste('dA',l+1,sep="")\]\]/keep\_prob

retvals = layerActivationBackward(gradients\[\[paste('dA',l+1,sep="")\]\], current\_cache, Y,

activationFunc = hiddenActivationFunc)

} else {

retvals =

layerActivationBackwardWithReg(gradients\[\[paste('dA',l+1,sep="")\]\], current\_cache, Y, lambd,

activationFunc = hiddenActivationFunc)

}

gradients\[\[paste("dA",l,sep="")\]\] <-retvals\[\['dA\_prev'\]\]

gradients\[\[paste("dW",l,sep="")\]\] <- retvals\[\['dW'\]\]

gradients\[\[paste("db",l,sep="")\]\] <- retvals\[\['db'\]\]

}

return(gradients)

}

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients

\# : learning rate

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

#output : Updated weights after 1 iteration

gradientDescent <- function(parameters, gradients,

learningRate,outputActivationFunc="sigmoid"){

L = length(parameters)/2 # number of layers in the neural network

\# Update rule for each parameter. Use a for loop.

for(l in 1:(L-1)){

parameters\[\[paste("W",l,sep="")\]\] = parameters\[\[paste("W",l,sep="")\]\] -

learningRate\* gradients\[\[paste("dW",l,sep="")\]\]

parameters\[\[paste("b",l,sep="")\]\] = parameters\[\[paste("b",l,sep="")\]\] -

learningRate\* gradients\[\[paste("db",l,sep="")\]\]

}

if(outputActivationFunc=="sigmoid"){

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* gradients\[\[paste("dW",L,sep="")\]\]

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* gradients\[\[paste("db",L,sep="")\]\]

}else if (outputActivationFunc=="softmax"){

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* t(gradients\[\[paste("dW",L,sep="")\]\]) parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* t(gradients\[\[paste("db",L,sep="")\]\])

}

return(parameters)

}

\# Perform Gradient Descent with momentum

\# Input : Weights and biases

\# : beta

\# : gradients

\# : learning rate

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

#output : Updated weights after 1 iteration

gradientDescentWithMomentum <- function(parameters, gradients,v, beta, learningRate,outputActivationFunc="sigmoid"){

L = length(parameters)/2 # number of layers in the neural network

\# Update rule for each parameter. Use a for loop.

for(l in 1:(L-1)){

\# Compute velocities

\# v\['dWk'\] = beta \*v\['dWk'\] + (1-beta)\*dWk

v\[\[paste("dW",l, sep="")\]\] = beta\*v\[\[paste("dW",l, sep="")\]\] +

(1-beta) \* gradients\[\[paste('dW',l,sep="")\]\]

v\[\[paste("db",l, sep="")\]\] = beta\*v\[\[paste("db",l, sep="")\]\] +

(1-beta) \* gradients\[\[paste('db',l,sep="")\]\]

parameters\[\[paste("W",l,sep="")\]\] = parameters\[\[paste("W",l,sep="")\]\] -

learningRate\* v\[\[paste("dW",l, sep="")\]\]

parameters\[\[paste("b",l,sep="")\]\] = parameters\[\[paste("b",l,sep="")\]\] -

learningRate\* v\[\[paste("db",l, sep="")\]\]

}

 # Compute for the Lth layer

if(outputActivationFunc=="sigmoid"){

v\[\[paste("dW",L, sep="")\]\] = beta\*v\[\[paste("dW",L, sep="")\]\] +

(1-beta) \* gradients\[\[paste('dW',L,sep="")\]\]

v\[\[paste("db",L, sep="")\]\] = beta\*v\[\[paste("db",L, sep="")\]\] +

(1-beta) \* gradients\[\[paste('db',L,sep="")\]\]

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* v\[\[paste("dW",l, sep="")\]\]

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* v\[\[paste("db",l, sep="")\]\]

}else if (outputActivationFunc=="softmax"){

v\[\[paste("dW",L, sep="")\]\] = beta\*v\[\[paste("dW",L, sep="")\]\] +

(1-beta) \* t(gradients\[\[paste('dW',L,sep="")\]\])

v\[\[paste("db",L, sep="")\]\] = beta\*v\[\[paste("db",L, sep="")\]\] +

(1-beta) \* t(gradients\[\[paste('db',L,sep="")\]\])

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* t(gradients\[\[paste("dW",L,sep="")\]\]) parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* t(gradients\[\[paste("db",L,sep="")\]\])

}

return(parameters)

}

\# Perform Gradient Descent with RMSProp

\# Input : parameters

\# : gradients

\# : s

\# : beta1

\# : epsilon

\# : learning rate

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

#output : Updated weights after 1 iteration

gradientDescentWithRMSProp <- function(parameters, gradients,s, beta1, epsilon, learningRate,outputActivationFunc="sigmoid"){

L = length(parameters)/2 # number of layers in the neural network

 # Update rule for each parameter. Use a for loop.

for(l in 1:(L-1)){

\# Compute RMSProp

\# s\['dWk'\] = beta1 \*s\['dWk'\] + (1-beta1)\*dWk\*\*2/sqrt(s\['dWk'\])

\# Element wise multiply of gradients

s\[\[paste("dW",l, sep="")\]\] = beta1\*s\[\[paste("dW",l, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('dW',l,sep="")\]\] \*

gradients\[\[paste('dW',l,sep="")\]\]

s\[\[paste("db",l, sep="")\]\] = beta1\*s\[\[paste("db",l, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('db',l,sep="")\]\] \*

gradients\[\[paste('db',l,sep="")\]\]

parameters\[\[paste("W",l,sep="")\]\] = parameters\[\[paste("W",l,sep="")\]\] -

learningRate \* gradients\[\[paste('dW',l,sep="")\]\]/sqrt(s\[\[paste("dW",l, sep="")\]\]+epsilon)

parameters\[\[paste("b",l,sep="")\]\] = parameters\[\[paste("b",l,sep="")\]\] -

learningRate\*gradients\[\[paste('db',l,sep="")\]\]/sqrt(s\[\[paste("db",l, sep="")\]\]+epsilon)

}

\# Compute for the Lth layer

if(outputActivationFunc=="sigmoid"){

s\[\[paste("dW",L, sep="")\]\] = beta1\*s\[\[paste("dW",L, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('dW',L,sep="")\]\]

\*gradients\[\[paste('dW',L,sep="")\]\]

s\[\[paste("db",L, sep="")\]\] = beta1\*s\[\[paste("db",L, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('db',L,sep="")\]\] \*

gradients\[\[paste('db',L,sep="")\]\]

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\* gradients\[\[paste('dW',l,sep="")\]\]/sqrt(s\[\[paste("dW",L, sep="")\]\]+epsilon)

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* gradients\[\[paste('db',l,sep="")\]\]/sqrt( s\[\[paste("db",L, sep="")\]\]+epsilon)

}else if (outputActivationFunc=="softmax"){

s\[\[paste("dW",L, sep="")\]\] = beta1\*s\[\[paste("dW",L, sep="")\]\] +

(1-beta1) \* t(gradients\[\[paste('dW',L,sep="")\]\]) \*

t(gradients\[\[paste('dW',L,sep="")\]\]) s\[\[paste("db",L, sep="")\]\] = beta1\*s\[\[paste("db",L, sep="")\]\] +

(1-beta1) \* t(gradients\[\[paste('db',L,sep="")\]\]) \*

t(gradients\[\[paste('db',L,sep="")\]\])

parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate\*

t(gradients\[\[paste("dW",L,sep="")\]\])/sqrt(s\[\[paste("dW",L, sep="")\]\]+epsilon) parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\* t(gradients\[\[paste("db",L,sep="")\]\])/sqrt( s\[\[paste("db",L, sep="")\]\]+epsilon)

}

return(parameters)

}

\# Perform Gradient Descent with Adam

\# Input : parameters

\# : gradients

\# : v

\# : s

\# : t

\# : beta1

\# : beta2

\# : epsilon

\# : learning rate

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

#output : Updated weights after 1 iteration

gradientDescentWithAdam <- function(parameters, gradients,v, s, t, beta1=0.9, beta2=0.999, epsilon=10^-8,

learningRate=0.1,outputActivationFunc="sigmoid"){

L = length(parameters)/2 # number of layers in the neural network v\_corrected <- list()

s\_corrected <- list()

\# Update rule for each parameter. Use a for loop.

for(l in 1:(L-1)){

\# v\['dWk'\] = beta \*v\['dWk'\] + (1-beta)\*dWk

 v\[\[paste("dW",l, sep="")\]\] = beta1\*v\[\[paste("dW",l, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('dW',l,sep="")\]\]

v\[\[paste("db",l, sep="")\]\] = beta1\*v\[\[paste("db",l, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('db',l,sep="")\]\]

\# Compute bias-corrected first moment estimate.

v\_corrected\[\[paste("dW",l, sep="")\]\] = v\[\[paste("dW",l, sep="")\]\]/(1-beta1^t)

v\_corrected\[\[paste("db",l, sep="")\]\] = v\[\[paste("db",l, sep="")\]\]/(1-beta1^t)

\# Element wise multiply of gradients

s\[\[paste("dW",l, sep="")\]\] = beta2\*s\[\[paste("dW",l, sep="")\]\] +

(1-beta2) \* gradients\[\[paste('dW',l,sep="")\]\] \*

gradients\[\[paste('dW',l,sep="")\]\]

s\[\[paste("db",l, sep="")\]\] = beta2\*s\[\[paste("db",l, sep="")\]\] +

(1-beta2) \* gradients\[\[paste('db',l,sep="")\]\] \*

gradients\[\[paste('db',l,sep="")\]\]

\# Compute bias-corrected second moment estimate.

s\_corrected\[\[paste("dW",l, sep="")\]\] = s\[\[paste("dW",l, sep="")\]\]/(1-beta2^t)

s\_corrected\[\[paste("db",l, sep="")\]\] = s\[\[paste("db",l, sep="")\]\]/(1-beta2^t)

\# Update parameters.

d1=sqrt(s\_corrected\[\[paste("dW",l, sep="")\]\]+epsilon) d2=sqrt(s\_corrected\[\[paste("db",l, sep="")\]\]+epsilon) parameters\[\[paste("W",l,sep="")\]\] = parameters\[\[paste("W",l,sep="")\]\] -

learningRate \* v\_corrected\[\[paste("dW",l, sep="")\]\]/d1

parameters\[\[paste("b",l,sep="")\]\] = parameters\[\[paste("b",l,sep="")\]\] -

learningRate\*v\_corrected\[\[paste("db",l, sep="")\]\]/d2

}

\# Compute for the Lth layer

if(outputActivationFunc=="sigmoid"){

v\[\[paste("dW",L, sep="")\]\] = beta1\*v\[\[paste("dW",L, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('dW',L,sep="")\]\]

 v\[\[paste("db",L, sep="")\]\] = beta1\*v\[\[paste("db",L, sep="")\]\] +

(1-beta1) \* gradients\[\[paste('db',L,sep="")\]\]

\# Compute bias-corrected first moment estimate.

v\_corrected\[\[paste("dW",L, sep="")\]\] = v\[\[paste("dW",L, sep="")\]\]/(1-beta1^t)

v\_corrected\[\[paste("db",L, sep="")\]\] = v\[\[paste("db",L, sep="")\]\]/(1-beta1^t)

\# Element wise multiply of gradients

s\[\[paste("dW",L, sep="")\]\] = beta2\*s\[\[paste("dW",L, sep="")\]\] +

(1-beta2) \* gradients\[\[paste('dW',L,sep="")\]\] \*

gradients\[\[paste('dW',L,sep="")\]\]

s\[\[paste("db",L, sep="")\]\] = beta2\*s\[\[paste("db",L, sep="")\]\] +

(1-beta2) \* gradients\[\[paste('db',L,sep="")\]\] \*

gradients\[\[paste('db',L,sep="")\]\]

\# Compute bias-corrected second moment estimate.

s\_corrected\[\[paste("dW",L, sep="")\]\] = s\[\[paste("dW",L, sep="")\]\]/(1-beta2^t)

s\_corrected\[\[paste("db",L, sep="")\]\] = s\[\[paste("db",L, sep="")\]\]/(1-beta2^t)

\# Update parameters.

d1=sqrt(s\_corrected\[\[paste("dW",L, sep="")\]\]+epsilon) d2=sqrt(s\_corrected\[\[paste("db",L, sep="")\]\]+epsilon) parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate \* v\_corrected\[\[paste("dW",L, sep="")\]\]/d1

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\*v\_corrected\[\[paste("db",L, sep="")\]\]/d2

}else if (outputActivationFunc=="softmax"){

v\[\[paste("dW",L, sep="")\]\] = beta1\*v\[\[paste("dW",L, sep="")\]\] +

(1-beta1) \* t(gradients\[\[paste('dW',L,sep="")\]\])

v\[\[paste("db",L, sep="")\]\] = beta1\*v\[\[paste("db",L, sep="")\]\] +

(1-beta1) \* t(gradients\[\[paste('db',L,sep="")\]\])

\# Compute bias-corrected first moment estimate.

v\_corrected\[\[paste("dW",L, sep="")\]\] = v\[\[paste("dW",L, sep="")\]\]/(1-beta1^t)

v\_corrected\[\[paste("db",L, sep="")\]\] = v\[\[paste("db",L, sep="")\]\]/(1-beta1^t)

\# Element wise multiply of gradients

s\[\[paste("dW",L, sep="")\]\] = beta2\*s\[\[paste("dW",L, sep="")\]\] +

(1-beta2) \* t(gradients\[\[paste('dW',L,sep="")\]\]) \*

t(gradients\[\[paste('dW',L,sep="")\]\])

s\[\[paste("db",L, sep="")\]\] = beta2\*s\[\[paste("db",L, sep="")\]\] +

(1-beta2) \* t(gradients\[\[paste('db',L,sep="")\]\]) \*

t(gradients\[\[paste('db',L,sep="")\]\])

\# Compute bias-corrected second moment estimate.

s\_corrected\[\[paste("dW",L, sep="")\]\] = s\[\[paste("dW",L, sep="")\]\]/(1-beta2^t)

s\_corrected\[\[paste("db",L, sep="")\]\] = s\[\[paste("db",L, sep="")\]\]/(1-beta2^t)

\# Update parameters.

d1=sqrt(s\_corrected\[\[paste("dW",L, sep="")\]\]+epsilon) d2=sqrt(s\_corrected\[\[paste("db",L, sep="")\]\]+epsilon) parameters\[\[paste("W",L,sep="")\]\] = parameters\[\[paste("W",L,sep="")\]\] -

learningRate \* v\_corrected\[\[paste("dW",L, sep="")\]\]/d1

parameters\[\[paste("b",L,sep="")\]\] = parameters\[\[paste("b",L,sep="")\]\] -

learningRate\*v\_corrected\[\[paste("db",L, sep="")\]\]/d2

}

return(parameters)

}

\# Execute a L layer Deep learning model

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu /tanh

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : learning rate

\# : lambd

\# : keep\_prob

\# : learning rate

\# : num of iterations

\# : initType

#output : Updated weights

L\_Layer\_DeepModel <- function(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc= 'sigmoid',

learningRate = 0.5,

lambd=0,

keep\_prob=1,

numIterations = 10000,

initType="default",

print\_cost=False){

#Initialize costs vector as NULL

costs <- NULL

\# Parameters initialization.

if (initType=="He"){

parameters =HeInitializeDeepModel(layersDimensions)

} else if (initType=="Xav"){

parameters =XavInitializeDeepModel(layersDimensions)

}

else{

parameters = initializeDeepModel(layersDimensions)

}

\# Loop (gradient descent)

for( i in 0:numIterations){

\# Forward propagation: \[LINEAR -> RELU\]\*(L-1) -> LINEAR -> SIGMOID/SOFTMAX.

retvals = forwardPropagationDeep(X, parameters,keep\_prob,

hiddenActivationFunc,

outputActivationFunc=outputActivationFunc)

AL <- retvals\[\['AL'\]\]

caches <- retvals\[\['caches'\]\]

dropoutMat <- retvals\[\['dropoutMat'\]\]

\# Compute cost.

if(lambd==0){

cost <- computeCost(AL,

Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

} else {

cost <- computeCostWithReg(parameters, AL, Y,lambd,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

}

\# Backward propagation.

gradients = backwardPropagationDeep(AL, Y, caches, dropoutMat, lambd, keep\_prob, hiddenActivationFunc,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

\# Update parameters.

parameters = gradientDescent(parameters, gradients, learningRate, outputActivationFunc=outputActivationFunc)

if(i%%1000 == 0){

costs=c(costs,cost)

print(cost)

}

}

retvals <- list("parameters"=parameters,"costs"=costs) return(retvals)

}

\# Execute a L layer Deep learning model with Stochastic Gradient descent

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu /tanh

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : learning rate

\# : lrDecay

\# : decayRate

\# : lambd

\# : keep\_prob

\# : optimizer

\# : beta

\# : beta1

\# : beta2

\# : epsilon

\# : mini\_batch\_size

\# : num of epochs

#output : Updated weights after each iteration

L\_Layer\_DeepModel\_SGD <- function(X, Y, layersDimensions,

hiddenActivationFunc='relu',

outputActivationFunc= 'sigmoid',

learningRate = .3,

lrDecay=FALSE,

decayRate=1,

lambd=0,

keep\_prob=1,

optimizer="gd",

beta=0.9,

beta1=0.9,

beta2=0.999,

epsilon=10^-8,

mini\_batch\_size = 64,

num\_epochs = 2500,

print\_cost=False){

print("Values")

cat("learningRate= ",learningRate)

cat("\\n")

 cat("lambd=",lambd)

cat("\\n")

cat("keep\_prob=",keep\_prob)

cat("\\n")

cat("optimizer=",optimizer)

cat("\\n")

cat("lrDecay=",lrDecay)

cat("\\n")

cat("decayRate=",decayRate)

cat("\\n")

cat("beta=",beta)

cat("\\n")

cat("beta1=",beta1)

cat("\\n")

cat("beta2=",beta2)

cat("\\n")

cat("epsilon=",epsilon)

cat("\\n")

cat("mini\_batch\_size=",mini\_batch\_size)

cat("\\n")

cat("num\_epochs=",num\_epochs)

cat("\\n")

set.seed(1)

#Initialize costs vector as NULL

costs <- NULL

t <- 0

\# Parameters initialization.

parameters = initializeDeepModel(layersDimensions)

#Initialize the optimizer

if(optimizer == "momentum"){

v <-initializeVelocity(parameters)

} else if(optimizer == "rmsprop"){

s <-initializeRMSProp(parameters)

} else if (optimizer == "adam"){

adamVals <-initializeAdam(parameters)

}

seed=10

\# Loop for number of epochs

for( i in 0:num\_epochs){

seed=seed+1

minibatches = random\_mini\_batches(X, Y, mini\_batch\_size, seed) for(batch in 1:length(minibatches)){

mini\_batch\_X=minibatches\[\[batch\]\]\[\['mini\_batch\_X'\]\]

mini\_batch\_Y=minibatches\[\[batch\]\]\[\['mini\_batch\_Y'\]\]

\# Forward propagation:

retvals = forwardPropagationDeep(mini\_batch\_X, parameters,keep\_prob, hiddenActivationFunc,

outputActivationFunc=outputActivationFunc)

AL <- retvals\[\['AL'\]\]

caches <- retvals\[\['caches'\]\]

dropoutMat <- retvals\[\['dropoutMat'\]\]

\# Compute cost.

\# Compute cost.

if(lambd==0){

cost <- computeCost(AL,

mini\_batch\_Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

} else {

cost <- computeCostWithReg(parameters, AL, Y,lambd,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\])

}

\# Backward propagation.

gradients = backwardPropagationDeep(AL, mini\_batch\_Y, caches, dropoutMat, lambd, keep\_prob, hiddenActivationFunc,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions\[length(layersDimensions)\]) if(optimizer == "gd"){

\# Update parameters.

parameters = gradientDescent(parameters, gradients, learningRate, outputActivationFunc=outputActivationFunc)

 }else if(optimizer == "momentum"){

\# Update parameters with Momentum

parameters = gradientDescentWithMomentum(parameters,

gradients,v,beta, learningRate,

outputActivationFunc=outputActivationFunc)

} else if(optimizer == "rmsprop"){

\# Update parameters with RMSProp

parameters = gradientDescentWithRMSProp(parameters,

gradients,s,beta1, epsilon,learningRate,

outputActivationFunc=outputActivationFunc)

} else if(optimizer == "adam"){

\# Update parameters with Adam

#Get v and s

t <- t+1

v <- adamVals\[\['v'\]\]

s <- adamVals\[\['s'\]\]

parameters = gradientDescentWithAdam(parameters, gradients,v, s,t, beta1,beta2, epsilon,learningRate,

outputActivationFunc=outputActivationFunc)

}

}

if(i%%1000 == 0){

costs=c(costs,cost)

print(cost)

}

if(lrDecay==TRUE){

learningRate = decayRate^(num\_epochs/1000) \* learningRate

}

}

retvals <- list("parameters"=parameters,"costs"=costs) return(retvals)

}

\# Predict the output for given input

\# Input : parameters

\# : X

\# Output: predictions

predict <- function(parameters, X,keep\_prob=1, hiddenActivationFunc='relu'){

fwdProp <- forwardPropagationDeep(X, parameters,keep\_prob, hiddenActivationFunc)

predictions <- fwdProp$AL>0.5

return (predictions)

}

\# Plot a decision boundary

\# This function uses ggplot2

plotDecisionBoundary <-

function(z,retvals,keep\_prob=1,hiddenActivationFunc="sigmoid",lr=0.5){

\# Find the minimum and maximum for the data

xmin<-min(z\[,1\])

xmax<-max(z\[,1\])

ymin<-min(z\[,2\])

ymax<-max(z\[,2\])

\# Create a grid of values

a=seq(xmin,xmax,length=100)

b=seq(ymin,ymax,length=100)

grid <- expand.grid(x=a, y=b)

colnames(grid) <- c('x1', 'x2')

grid1 <-t(grid)

\# Predict the output for this grid

q <-predict(retvals$parameters,grid1,keep\_prob=1, hiddenActivationFunc) q1 <- t(data.frame(q))

q2 <- as.numeric(q1)

grid2 <- cbind(grid,q2)

colnames(grid2) <- c('x1', 'x2','q2')

z1 <- data.frame(z)

names(z1) <- c("x1","x2","y") atitle=paste("Decision boundary for learning rate:",lr)

\# Plot the contour of the boundary

 ggplot(z1) +

geom\_point(data = z1, aes(x = x1, y = x2, color = y)) +

stat\_contour(data = grid2, aes(x = x1, y = x2, z = q2,color=q2), alpha = 0.9)+

ggtitle(atitle) + scale\_colour\_gradientn(colours = brewer.pal(10, "Spectral"))

}

\# Predict the probability scores for given data set

\# Input : parameters

\# : X

\# Output: probability of output

computeScores <- function(parameters, X,hiddenActivationFunc='relu'){

fwdProp <- forwardPropagationDeep(X, parameters,hiddenActivationFunc) scores <- fwdProp$AL

return (scores)

}

\# Create random mini batches

\# Input : X - Input features

\# : Y- output

\# : miniBatchSize

\# : seed

#output : mini\_batches

random\_mini\_batches <- function(X, Y, miniBatchSize = 64, seed = 0){

set.seed(seed)

\# Get number of training samples

m = dim(X)\[2\]

\# Initialize mini batches

mini\_batches = list()

\# Create a list of random numbers < m

permutation = c(sample(m))

\# Randomly shuffle the training data

shuffled\_X = X\[, permutation\]

shuffled\_Y = Y\[1, permutation\]

\# Compute number of mini batches

 numCompleteMinibatches = floor(m/miniBatchSize) batch=0

for(k in 0:(numCompleteMinibatches-1)){

batch=batch+1

\# Set the lower and upper bound of the mini batches

lower=(k\*miniBatchSize)+1

upper=((k+1) \* miniBatchSize)

mini\_batch\_X = shuffled\_X\[, lower:upper\]

mini\_batch\_Y = shuffled\_Y\[lower:upper\]

\# Add it to the list of mini batches

mini\_batch =

list("mini\_batch\_X"=mini\_batch\_X,"mini\_batch\_Y"=mini\_batch\_Y) mini\_batches\[\[batch\]\] =mini\_batch

}

\# If the batch size does not divide evenly with mini batc size if(m %% miniBatchSize != 0){

p=floor(m/miniBatchSize)\*miniBatchSize

\# Set the start and end of last batch

q=p+m %% miniBatchSize

mini\_batch\_X = shuffled\_X\[,(p+1):q\]

mini\_batch\_Y = shuffled\_Y\[(p+1):q\]

}

\# Return the list of mini batches

mini\_batch =

list("mini\_batch\_X"=mini\_batch\_X,"mini\_batch\_Y"=mini\_batch\_Y) mini\_batches\[\[batch\]\]=mini\_batch

return(mini\_batches)

}

\# Plot a decision boundary

\# This function uses ggplot2

plotDecisionBoundary1 <- function(Z,parameters,keep\_prob=1){

xmin<-min(Z\[,1\])

xmax<-max(Z\[,1\])

ymin<-min(Z\[,2\])

 ymax<-max(Z\[,2\])

\# Create a grid of points

a=seq(xmin,xmax,length=100)

b=seq(ymin,ymax,length=100)

grid <- expand.grid(x=a, y=b)

colnames(grid) <- c('x1', 'x2')

grid1 <-t(grid)

retvals = forwardPropagationDeep(grid1, parameters,keep\_prob, "relu", outputActivationFunc="softmax")

AL <- retvals$AL

\# From the softmax probabilities pick the one with the highest probability q= apply(AL,1,which.max)

q1 <- t(data.frame(q))

q2 <- as.numeric(q1)

grid2 <- cbind(grid,q2)

colnames(grid2) <- c('x1', 'x2','q2')

Z1 <- data.frame(Z)

names(Z1) <- c("x1","x2","y") atitle=paste("Decision boundary")

ggplot(Z1) +

geom\_point(data = Z1, aes(x = x1, y = x2, color = y)) +

stat\_contour(data = grid2, aes(x = x1, y = x2, z = q2,color=q2), alpha =

0.9)+

ggtitle(atitle) + scale\_colour\_gradientn(colours = brewer.pal(10,

"Spectral"))

}

#############

\# Note: Using list\_to\_vector followed by vector\_to\_list => original list

##############

\# Convert a weight,biases as a list to a vector

\# Input : parameter dictionary

\# Returns : vector

list\_to\_vector <- function(parameters){

 vec <- NULL

L=length(parameters)/2

for(l in 1:L){

vec1= as.vector(t(parameters\[\[paste('W',l,sep="")\]\])) #Take transpose vec1=as.matrix(vec1,nrow=length(vec1),ncol=1)

vec2= as.vector(t(parameters\[\[paste('b',l,sep="")\]\])) #Take transpose vec2=as.matrix(vec2,nrow=length(vec2),ncol=1)

vec <- rbind(vec,vec1)

vec <- rbind(vec,vec2)

}

return(vec)

}

\# Convert a list of gradients to a vector

\# Input : parameter

\# : gradient list

\# Returns : gradient vector

gradients\_to\_vector <- function(parameters,gradients){

vec <- NULL

L=length(parameters)/2

for(l in 1:L){

vec1= as.vector(t(gradients\[\[paste('dW',l,sep="")\]\])) #Take transpose vec1=as.matrix(vec1,nrow=length(vec1),ncol=1)

vec2= as.vector(t(gradients\[\[paste('db',l,sep="")\]\])) #Take transpose vec2=as.matrix(vec2,nrow=length(vec2),ncol=1)

vec <- rbind(vec,vec1)

vec <- rbind(vec,vec2)

}

return(vec)

}

\# Convert vector to a list

\# This should be a mirror copy of list\_to\_vector

\# Input : parameters

\# : theta

\# Returns : parameters1 (list)

vector\_to\_list <- function(parameters,theta){

L<-length(parameters)/2

start<-1

 parameters1 <- list()

for(l in 1:L){

m = dim(parameters\[\[paste('W',l,sep="")\]\])

a = theta\[start:(start+m\[1\]\*m\[2\]-1),1\]

parameters1\[\[paste('W',l,sep="")\]\] = t(matrix(a,nrow=m\[2\],ncol=m\[1\])) start=start+m\[1\]\*m\[2\]

n = dim(parameters\[\[paste('b',l,sep="")\]\])

b= theta\[start:(start+n\[1\]\*n\[2\]-1),1\]

parameters1\[\[paste('b',l,sep="")\]\]=t(matrix(b,nrow=n\[2\],ncol=n\[1\])) start=start+n\[1\]\*n\[2\]

}

return(parameters1)

}

\# Convert vector of gradients to list of gradients

\# Input : parameters

\# : grads

\# Returns : gradients1 (list)

vector\_to\_list2 <- function(parameters,grads){

L<-length(parameters)/2

start<-1

gradients1 <- list()

for(l in 1:L){

m = dim(parameters\[\[paste('W',l,sep="")\]\])

a = grads\[start:(start+m\[1\]\*m\[2\]-1),1\]

gradients1\[\[paste('dW',l,sep="")\]\] = matrix(a,nrow=m\[1\],ncol=m\[2\]) start=start+m\[1\]\*m\[2\]

n = dim(parameters\[\[paste('b',l,sep="")\]\])

b= grads\[start:(start+n\[1\]\*n\[2\]-1),1\]

gradients1\[\[paste('db',l,sep="")\]\]=matrix(b,nrow=n\[1\],ncol=n\[2\]) start=start+n\[1\]\*n\[2\]

}

return(gradients1)

}

\# Compute L2Norm

L2NormVec <- function(x) {

 sqrt(sum(x^2))

}

\# Perform Gradient check

\# Input : parameters

\# : gradients

\# : X

\# : Y

\# : epsilon

\# : outputActivationFunc

\# Returns :

gradient\_check\_n <- function(parameters, gradients, X, Y,

epsilon = 1e-7,outputActivationFunc="sigmoid"){

\# Convert parameters to a vector

parameters\_values = list\_to\_vector(parameters)

\# Convert gradients to a vector

grad = gradients\_to\_vector(parameters,gradients)

num\_parameters = dim(parameters\_values)\[1\]

#Initialize

J\_plus = matrix(rep(0,num\_parameters),

nrow=num\_parameters,ncol=1)

J\_minus = matrix(rep(0,num\_parameters),

nrow=num\_parameters,ncol=1)

gradapprox = matrix(rep(0,num\_parameters),

nrow=num\_parameters,ncol=1)

\# Compute gradapprox

for(i in 1:num\_parameters){

\# Compute J\_plus\[i\].

thetaplus = parameters\_values

thetaplus\[i\]\[1\] = thetaplus\[i\]\[1\] + epsilon

retvals = forwardPropagationDeep(X, vector\_to\_list(parameters,thetaplus), keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc) AL <- retvals\[\['AL'\]\]

J\_plus\[i\] = computeCost(AL, Y,

outputActivationFunc=outputActivationFunc)

\# Compute J\_minus\[i\].

thetaminus = parameters\_values

thetaminus\[i\]\[1\] = thetaminus\[i\]\[1\] - epsilon

retvals = forwardPropagationDeep(X,

vector\_to\_list(parameters,thetaminus), keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc) AL <- retvals\[\['AL'\]\]

J\_minus\[i\] = computeCost(AL, Y,

outputActivationFunc=outputActivationFunc)

\# Compute gradapprox\[i\]

gradapprox\[i\] = (J\_plus\[i\] - J\_minus\[i\])/(2\*epsilon)

}

\# Compare gradapprox to backward propagation gradients by computing difference.

numerator = L2NormVec(grad-gradapprox)

denominator = L2NormVec(grad) +

L2NormVec(gradapprox)

difference = numerator/denominator

if(difference > 1e-5){

cat("There is a mistake, the difference is too high",difference)

} else{

cat("The implementations works perfectly", difference)

}

\# This can be used to check the structure of gradients and gradapprox print("Gradients from backprop")

m=vector\_to\_list2(parameters,grad)

print(m)

print("Grad approx from gradient check")

n=vector\_to\_list2(parameters,gradapprox)

print(n)

}

**8.3 Octave**

############################################################################################################

#

\# File : DLfunctions8.R

\# Author : Tinniam V Ganesh

\# Date : 6 May 2018

#

##########################################################################################################

1;

\# Define sigmoid function

function \[A,cache\] = sigmoid(Z)

A = 1 ./ (1+ exp(-Z));

cache=Z;

end

\# Define Relu function

function \[A,cache\] = relu(Z)

A = max(0,Z);

cache=Z;

end

\# Define Relu function

function \[A,cache\] = tanhAct(Z)

A = tanh(Z);

cache=Z;

end

\# Define Softmax function

function \[A,cache\] = softmax(Z)

\# get unnormalized probabilities

exp\_scores = exp(Z');

\# normalize them for each example

A = exp\_scores ./ sum(exp\_scores,2);

cache=Z;

end

\# Define Stable Softmax function

function \[A,cache\] = stableSoftmax(Z)

\# Normalize by max value in each row

shiftZ = Z' - max(Z',\[\],2);

exp\_scores = exp(shiftZ);

\# normalize them for each example

A = exp\_scores ./ sum(exp\_scores,2);

#disp("sm")

#disp(A);

cache=Z;

end

\# Define Relu Derivative

function \[dZ\] = reluDerivative(dA,cache)

Z = cache;

dZ = dA;

\# Get elements that are greater than 0

a = (Z > 0);

\# Select only those elements where Z > 0

dZ = dZ .\* a;

end

\# Define Sigmoid Derivative

function \[dZ\] = sigmoidDerivative(dA,cache)

Z = cache;

s = 1 ./ (1+ exp(-Z));

dZ = dA .\* s .\* (1-s);

end

\# Define Tanh Derivative

function \[dZ\] = tanhDerivative(dA,cache)

Z = cache;

a = tanh(Z);

dZ = dA .\* (1 - a .^ 2);

end

\# Populate a matrix with 1s in rows where Y=1

\# This function may need to be modified if K is not 3, 10

\# This function is used in computing the softmax derivative

function \[Y1\] = popMatrix(Y,numClasses)

Y1=zeros(length(Y),numClasses);

if(numClasses==3) # For 3 output classes

Y1(Y==0,1)=1;

Y1(Y==1,2)=1;

Y1(Y==2,3)=1;

elseif(numClasses==10) # For 10 output classes

Y1(Y==0,1)=1;

Y1(Y==1,2)=1;

Y1(Y==2,3)=1;

Y1(Y==3,4)=1;

Y1(Y==4,5)=1;

Y1(Y==5,6)=1;

Y1(Y==6,7)=1;

Y1(Y==7,8)=1;

Y1(Y==8,9)=1;

Y1(Y==9,10)=1;

endif

end

\# Define Softmax Derivative

function \[dZ\] = softmaxDerivative(dA,cache,Y, numClasses)

Z = cache;

\# get unnormalized probabilities

shiftZ = Z' - max(Z',\[\],2);

exp\_scores = exp(shiftZ);

\# normalize them for each example

probs = exp\_scores ./ sum(exp\_scores,2);

\# dZ = pi- yi

yi=popMatrix(Y,numClasses);

dZ=probs-yi;

end

\# Define Stable Softmax Derivative

function \[dZ\] = stableSoftmaxDerivative(dA,cache,Y, numClasses) Z = cache;

 # get unnormalized probabilities

exp\_scores = exp(Z');

\# normalize them for each example

probs = exp\_scores ./ sum(exp\_scores,2);

\# dZ = pi- yi

yi=popMatrix(Y,numClasses);

dZ=probs-yi;

end

\# Initialize model for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers function \[W b\] = initializeDeepModel(layerDimensions)

rand ("seed", 3);

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Create cell arrays for Weights and biases

for l =2:size(layerDimensions)(2)

W{l-1} = rand(layerDimensions(l),layerDimensions(l-1))\*0.01; #

Multiply by .01

b{l-1} = zeros(layerDimensions(l),1);

endfor

end

\# He Initialization for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers function \[W b\] = HeInitializeDeepModel(layerDimensions)

rand ("seed", 3);

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Create cell arrays for Weights and biases

for l =2:size(layerDimensions)(2)

W{l-1} = rand(layerDimensions(l),layerDimensions(l-1))\*

sqrt(2/layerDimensions(l-1)); # Multiply by .01

b{l-1} = zeros(layerDimensions(l),1);

endfor

end

\# Xavier Initialization for L layers

\# Input : List of units in each layer

\# Returns: Initial weights and biases matrices for all layers function \[W b\] = XavInitializeDeepModel(layerDimensions)

rand ("seed", 3);

\# note the Weight matrix at layer 'l' is a matrix of size (l,l-1)

\# The Bias is a vectors of size (l,1)

\# Loop through the layer dimension from 1.. L

\# Create cell arrays for Weights and biases

for l =2:size(layerDimensions)(2)

W{l-1} = rand(layerDimensions(l),layerDimensions(l-1))\*

sqrt(1/layerDimensions(l-1)); # Multiply by .01

b{l-1} = zeros(layerDimensions(l),1);

endfor

end

\# Initialize velocity

\# Input : weights, biases

\# Returns: vdW, vdB - Initial velocity

function\[vdW vdB\] = initializeVelocity(weights, biases)

L = size(weights)(2) # Create an integer

\# Initialize a cell array

v = {}

\# Initialize velocity with the same dimensions as W

for l=1:L

 sz = size(weights{l});

vdW{l} = zeros(sz(1),sz(2));

sz = size(biases{l});

vdB{l} =zeros(sz(1),sz(2));

endfor;

end

\# Initialize RMSProp

\# Input : weights, biases

\# Returns: sdW, sdB - Initial RMSProp

function\[sdW sdB\] = initializeRMSProp(weights, biases)

L = size(weights)(2) # Create an integer

\# Initialize a cell array

s = {}

\# Initialize velocity with the same dimensions as W

for l=1:L

sz = size(weights{l});

sdW{l} = zeros(sz(1),sz(2));

sz = size(biases{l});

sdB{l} =zeros(sz(1),sz(2));

endfor;

end

\# Initialize Adam

\# Input : parameters

\# Returns: vdW, vdB, sdW, sdB -Initial Adam

function\[vdW vdB sdW sdB\] = initializeAdam(weights, biases)

L = size(weights)(2) # Create an integer

\# Initialize a cell array

s = {}

\# Initialize velocity with the same dimensions as W

for l=1:L

sz = size(weights{l});

vdW{l} = zeros(sz(1),sz(2));

sdW{l} = zeros(sz(1),sz(2));

 sz = size(biases{l});

sdB{l} =zeros(sz(1),sz(2));

vdB{l} =zeros(sz(1),sz(2));

endfor;

end

\# Compute the activation at a layer 'l' for forward prop in a Deep Network

\# Input : A\_prec - Activation of previous layer

\# W,b - Weight and bias matrices and vectors

\# activationFunc - Activation function - sigmoid, tanh, relu etc

\# Returns : The Activation of this layer

\# :

\# Z = W \* X + b

\# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)

function \[A forward\_cache activation\_cache\] = layerActivationForward(A\_prev, W, b, activationFunc)

\# Compute Z

Z = W \* A\_prev +b;

\# Create a cell array

forward\_cache = {A\_prev W b};

\# Compute the activation for sigmoid

if (strcmp(activationFunc,"sigmoid"))

\[A activation\_cache\] = sigmoid(Z);

elseif (strcmp(activationFunc, "relu")) # Compute the activation for Relu

\[A activation\_cache\] = relu(Z);

elseif(strcmp(activationFunc,'tanh')) # Compute the activation for tanh

\[A activation\_cache\] = tanhAct(Z);

elseif(strcmp(activationFunc,'softmax')) # Compute the activation for tanh

#\[A activation\_cache\] = softmax(Z);

\[A activation\_cache\] = stableSoftmax(Z);

endif

end

\# Compute the forward propagation for layers 1..L

\# Input : X - Input Features

\# parameters: Weights and biases

\# keep\_prob

\# hiddenActivationFunc - Activation function at hidden layers Relu/tanh/sigmoid

\# outputActivationFunc- sigmoid/softmax

\# Returns : AL, forward,\_caches, activation\_caches, dropoutMat

\# The forward propoagtion uses the Relu/tanh activation from layer 1..L-1 and sigmoid actiovation at layer L

function \[AL forward\_caches activation\_caches dropoutMat\] =

forwardPropagationDeep(X, weights,biases, keep\_prob=1,

hiddenActivationFunc='relu',

outputActivationFunc='sigmoid')

\# Create an empty cell array

forward\_caches = {};

activation\_caches = {};

droputMat ={};

\# Set A to X (A0)

A = X;

L = length(weights); # number of layers in the neural network

\# Loop through from layer 1 to upto layer L

for l =1:L-1

A\_prev = A;

\# Zi = Wi x Ai-1 + bi and Ai = g(Zi)

W = weights{l};

b = biases{l};

\[A forward\_cache activation\_cache\] = layerActivationForward(A\_prev, W,b, activationFunc=hiddenActivationFunc);

D=rand(size(A)(1),size(A)(2));

D = (D < keep\_prob) ;

\# Multiply by DropoutMat

A= A .\* D;

\# Divide by keep\_prob to keep expected value same

A = A ./ keep\_prob;

\# Store D

dropoutMat{l}=D;

forward\_caches{l}=forward\_cache;

activation\_caches{l} = activation\_cache;

endfor

\# Since this is binary classification use the sigmoid activation function in

\# last layer

W = weights{L};

 b = biases{L};

\[AL, forward\_cache activation\_cache\] = layerActivationForward(A, W,b, activationFunc = outputActivationFunc);

forward\_caches{L}=forward\_cache;

activation\_caches{L} = activation\_cache;

end

\# Pick columns where Y==1

\# This function is used in computeCost

function \[a\] = pickColumns(AL,Y,numClasses)

if(numClasses==3)

a=\[AL(Y==0,1) ;AL(Y==1,2) ;AL(Y==2,3)\];

elseif (numClasses==10)

a=\[AL(Y==0,1) ;AL(Y==1,2) ;AL(Y==2,3);AL(Y==3,4);AL(Y==4,5);

AL(Y==5,6); AL(Y==6,7);AL(Y==7,8);AL(Y==8,9);AL(Y==9,10)\];

endif

end

\# Compute the cost

\# Input : AL-Activation of last layer

\# : Y-Output from data

\# : outputActivationFunc- sigmoid/softmax

\# : numClasses

\# Output: cost

function \[cost\]= computeCost(AL, Y,

outputActivationFunc="sigmoid",numClasses)

if(strcmp(outputActivationFunc,"sigmoid"))

numTraining= size(Y)(2);

\# Element wise multiply for logprobs

cost = -1/numTraining \* sum((Y .\* log(AL)) + (1-Y) .\* log(1-AL));

#disp(cost);

elseif(strcmp(outputActivationFunc,'softmax'))

numTraining = size(Y)(2);

Y=Y';

\# Select rows where Y=0,1,and 2 and concatenate to a long vector

#a=\[AL(Y==0,1) ;AL(Y==1,2) ;AL(Y==2,3)\];

 a =pickColumns(AL,Y,numClasses);

#Select the correct column for log prob

correct\_probs = -log(a);

#Compute log loss

cost= sum(correct\_probs)/numTraining;

endif

end

\# Compute the cost with regularization

\# Input : weights

\# : AL - Activation of last layer

\# : Output from data

\# : lambd

\# : outputActivationFunc- sigmoid/softmax

\# : numClasses

\# Output: cost

function \[cost\]= computeCostWithReg(weights, AL, Y, lambd,

outputActivationFunc="sigmoid",numClasses)

if(strcmp(outputActivationFunc,"sigmoid"))

numTraining= size(Y)(2);

\# Element wise multiply for logprobs

cost = -1/numTraining \* sum((Y .\* log(AL)) + (1-Y) .\* log(1-AL));

\# Regularization cost

L = size(weights)(2);

L2RegularizationCost=0;

for l=1:L

wtSqr = weights{l} .\* weights{l};

#disp(sum(sum(wtSqr,1)));

L2RegularizationCost+=sum(sum(wtSqr,1));

endfor

L2RegularizationCost = (lambd/(2\*numTraining))\*L2RegularizationCost; cost = cost + L2RegularizationCost ;

elseif(strcmp(outputActivationFunc,'softmax'))

numTraining = size(Y)(2);

 Y=Y';

\# Select rows where Y=0,1,and 2 and concatenate to a long vector

#a=\[AL(Y==0,1) ;AL(Y==1,2) ;AL(Y==2,3)\];

a =pickColumns(AL,Y,numClasses);

#Select the correct column for log prob

correct\_probs = -log(a);

#Compute log loss

cost= sum(correct\_probs)/numTraining;

\# Regularization cost

L = size(weights)(2);

L2RegularizationCost=0;

for l=1:L

\# Compute L2 Norm

wtSqr = weights{l} .\* weights{l};

#disp(sum(sum(wtSqr,1)));

L2RegularizationCost+=sum(sum(wtSqr,1));

endfor

L2RegularizationCost = (lambd/(2\*numTraining))\*L2RegularizationCost; cost = cost + L2RegularizationCost ;

endif

end

\# Compute the backpropoagation for 1 cycle

\# Input : Neural Network parameters - dA

\# # cache - forward\_cache & activation\_cache

\# # Input features

\# # Output values Y

\# # outputActivationFunc- sigmoid/softmax

\# # numClasses

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

function \[dA\_prev dW db\] = layerActivationBackward(dA, forward\_cache, activation\_cache, Y, activationFunc,numClasses)

 A\_prev = forward\_cache{1};

W =forward\_cache{2};

b = forward\_cache{3};

numTraining = size(A\_prev)(2);

if (strcmp(activationFunc,"relu"))

dZ = reluDerivative(dA, activation\_cache);

elseif (strcmp(activationFunc,"sigmoid"))

dZ = sigmoidDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "tanh"))

dZ = tanhDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "softmax"))

#dZ = softmaxDerivative(dA, activation\_cache,Y,numClasses);

dZ = stableSoftmaxDerivative(dA, activation\_cache,Y,numClasses); endif

if (strcmp(activationFunc,"softmax"))

W =forward\_cache{2};

b = forward\_cache{3};

\# Add the regularization factor

dW = 1/numTraining \* A\_prev \* dZ;

db = 1/numTraining \* sum(dZ,1);

dA\_prev = dZ\*W;

else

W =forward\_cache{2};

b = forward\_cache{3};

\# Add the regularization factor

dW = 1/numTraining \* dZ \* A\_prev';

db = 1/numTraining \* sum(dZ,2);

dA\_prev = W'\*dZ;

endif

end

\# Compute the backpropoagation for 1 cycle

\# Input : dA- Neural Network parameters

\# # cache - forward\_cache & activation\_cache

\# # Y-Output values

\# # outputActivationFunc- sigmoid/softmax

\# # numClasses

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

function \[dA\_prev dW db\] = layerActivationBackwardWithReg(dA, forward\_cache, activation\_cache, Y, lambd=0, activationFunc,numClasses) A\_prev = forward\_cache{1};

W =forward\_cache{2};

b = forward\_cache{3};

numTraining = size(A\_prev)(2);

if (strcmp(activationFunc,"relu"))

dZ = reluDerivative(dA, activation\_cache);

elseif (strcmp(activationFunc,"sigmoid"))

dZ = sigmoidDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "tanh"))

dZ = tanhDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "softmax"))

#dZ = softmaxDerivative(dA, activation\_cache,Y,numClasses);

dZ = stableSoftmaxDerivative(dA, activation\_cache,Y,numClasses); endif

if (strcmp(activationFunc,"softmax"))

W =forward\_cache{2};

b = forward\_cache{3};

\# Add the regularization factor

dW = 1/numTraining \* A\_prev \* dZ + (lambd/numTraining) \* W'; db = 1/numTraining \* sum(dZ,1);

dA\_prev = dZ\*W;

else

W =forward\_cache{2};

b = forward\_cache{3};

\# Add the regularization factor

dW = 1/numTraining \* dZ \* A\_prev' + (lambd/numTraining) \* W; db = 1/numTraining \* sum(dZ,2);

dA\_prev = W'\*dZ;

endif

end

\# Compute the backpropoagation with regularization for 1 cycle

\# Input : dA-Neural Network parameters

\# # cache - forward\_cache & activation\_cache

\# # Y-Output values

\# # lambd

\# # outputActivationFunc- sigmoid/softmax

\# # numClasses

\# Returns: Gradients

\# dL/dWi= dL/dZi\*Al-1

\# dl/dbl = dL/dZl

\# dL/dZ\_prev=dL/dZl\*W

function \[dA\_prev dW db\] = layerActivationBackwardWithReg(dA, forward\_cache, activation\_cache, Y, lambd=0, activationFunc,numClasses) A\_prev = forward\_cache{1};

W =forward\_cache{2};

b = forward\_cache{3};

numTraining = size(A\_prev)(2);

if (strcmp(activationFunc,"relu"))

dZ = reluDerivative(dA, activation\_cache);

elseif (strcmp(activationFunc,"sigmoid"))

dZ = sigmoidDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "tanh"))

dZ = tanhDerivative(dA, activation\_cache);

elseif(strcmp(activationFunc, "softmax"))

#dZ = softmaxDerivative(dA, activation\_cache,Y,numClasses);

dZ = stableSoftmaxDerivative(dA, activation\_cache,Y,numClasses); endif

if (strcmp(activationFunc,"softmax"))

W =forward\_cache{2};

b = forward\_cache{3};

\# Add the regularization factor

dW = 1/numTraining \* A\_prev \* dZ + (lambd/numTraining) \* W'; db = 1/numTraining \* sum(dZ,1);

dA\_prev = dZ\*W;

else

 W =forward\_cache{2};

b = forward\_cache{3};

\# Add the regularization factor

dW = 1/numTraining \* dZ \* A\_prev' + (lambd/numTraining) \* W; db = 1/numTraining \* sum(dZ,2);

dA\_prev = W'\*dZ;

endif

end

\# Compute the backpropoagation for 1 cycle

\# Input : AL: Output of L layer Network - weights

\# Y Real output

\# caches -- list of caches containing:

\# every cache of layerActivationForward() with "relu"/"tanh"

\# #(it's caches\[l\], for l in range(L-1) i.e l = 0...L-2)

\# #the cache of layerActivationForward() with "sigmoid" (it's caches\[L-1\])

\# dropoutMat

\# lambd

\# keep\_prob

\# hiddenActivationFunc - Activation function at hidden layers sigmoid/tanh/relu

\# outputActivationFunc- sigmoid/softmax

\# numClasses

#

\# Returns:

\# gradients -- A dictionary with the gradients

\# gradients\["dA" + str(l)\] = ...

\# gradients\["dW" + str(l)\] = ...

\# gradients\["db" + str(l)\] = ...

function \[gradsDA gradsDW gradsDB\]= backwardPropagationDeep(AL, Y, activation\_caches,forward\_caches,

dropoutMat, lambd=0, keep\_prob=1,

hiddenActivationFunc='relu',outputActivationFunc="sigmoid",numClasses)

\# Set the number of layers

L = length(activation\_caches);

 m = size(AL)(2);

if (strcmp(outputActivationFunc,"sigmoid"))

\# Initializing the backpropagation

\# dl/dAL= -(y/a + (1-y)/(1-a)) - At the output layer

dAL = -((Y ./ AL) - (1 - Y) ./ ( 1 - AL));

elseif (strcmp(outputActivationFunc,"softmax"))

dAL=0;

Y=Y';

endif

\# Since this is a binary classification the activation at output is sigmoid

\# Get the gradients at the last layer

\# Inputs: "AL, Y, caches".

\# Outputs: "gradients\["dAL"\], gradients\["dWL"\], gradients\["dbL"\]

activation\_cache = activation\_caches{L};

forward\_cache = forward\_caches(L);

\# Note the cell array includes an array of forward caches. To get to this we need to include the index {1}

if (lambd==0)

\[dA dW db\] = layerActivationBackward(dAL, forward\_cache{1},

activation\_cache, Y, activationFunc = outputActivationFunc,numClasses); else

\[dA dW db\] = layerActivationBackwardWithReg(dAL, forward\_cache{1}, activation\_cache, Y, lambd, activationFunc =

outputActivationFunc,numClasses);

endif

if (strcmp(outputActivationFunc,"sigmoid"))

gradsDA{L}= dA;

elseif (strcmp(outputActivationFunc,"softmax"))

gradsDA{L}= dA';#Note the transpose

endif

gradsDW{L}= dW;

gradsDB{L}= db;

\# Traverse in the reverse direction

for l =(L-1):-1:1

\# Compute the gradients for L-1 to 1 for Relu/tanh

 # Inputs: "gradients\["dA" + str(l + 2)\], caches".

\# Outputs: "gradients\["dA" + str(l + 1)\] , gradients\["dW" + str(l + 1)\] , gradients\["db" + str(l + 1)\]

activation\_cache = activation\_caches{l};

forward\_cache = forward\_caches(l);

#dA\_prev\_temp, dW\_temp, db\_temp =

layerActivationBackward(gradients\['dA'+str(l+1)\], current\_cache, activationFunc = "relu")

\# dAl the dervative of the activation of the lth layer,is the first element dAl= gradsDA{l+1};

if(lambd == 0)

\# Get the dropout mat

D = dropoutMat{l};

#Multiply by the dropoutMat

dAl= dAl .\* D;

\# Divide by keep\_prob to keep expected value same

dAl = dAl ./ keep\_prob;

\[dA\_prev\_temp, dW\_temp, db\_temp\] = layerActivationBackward(dAl, forward\_cache{1}, activation\_cache, Y, activationFunc =

hiddenActivationFunc,numClasses);

else

\[dA\_prev\_temp, dW\_temp, db\_temp\] =

layerActivationBackwardWithReg(dAl, forward\_cache{1}, activation\_cache, Y, lambd, activationFunc = hiddenActivationFunc,numClasses);

endif

gradsDA{l}= dA\_prev\_temp;

gradsDW{l}= dW\_temp;

gradsDB{l}= db\_temp;

endfor

end

\# Perform Gradient Descent

\# Input : Weights and biases

\# : gradients -gradsW,gradsB

\# : learning rate

\# : outputActivationFunc

#output : Updated weights after 1 iteration

function \[weights biases\] = gradientDescent(weights, biases,gradsW,gradsB, learningRate,outputActivationFunc="sigmoid")

L = size(weights)(2); # number of layers in the neural network

\# Update rule for each parameter.

for l=1:(L-1)

weights{l} = weights{l} -learningRate\* gradsW{l};

biases{l} = biases{l} -learningRate\* gradsB{l};

endfor

if (strcmp(outputActivationFunc,"sigmoid"))

weights{L} = weights{L} -learningRate\* gradsW{L};

biases{L} = biases{L} -learningRate\* gradsB{L};

elseif (strcmp(outputActivationFunc,"softmax"))

weights{L} = weights{L} -learningRate\* gradsW{L}';

biases{L} = biases{L} -learningRate\* gradsB{L}';

endif

end

\# Update parameters with momentum

\# Input : parameters

\# : gradients -gradsDW,gradsDB

\# : v -vdW, vdB

\# : beta

\# : learningRate

\# : outputActivationFunc

#output : Updated weights, biases

function \[weights biases\] = gradientDescentWithMomentum(weights, biases,gradsDW,gradsDB, vdW, vdB, beta,

learningRate,outputActivationFunc="sigmoid")

L = size(weights)(2); # number of layers in the neural network

\# Update rule for each parameter.

for l=1:(L-1)

 # Compute velocities

\# v\['dWk'\] = beta \*v\['dWk'\] + (1-beta)\*dWk

vdW{l} = beta\*vdW{l} + (1 -beta) \* gradsDW{l};

vdB{l} = beta\*vdB{l} + (1 -beta) \* gradsDB{l};

weights{l} = weights{l} -learningRate\* vdW{l};

biases{l} = biases{l} -learningRate\* vdB{l};

endfor

if (strcmp(outputActivationFunc,"sigmoid"))

vdW{L} = beta\*vdW{L} + (1 -beta) \* gradsDW{L};

vdB{L} = beta\*vdB{L} + (1 -beta) \* gradsDB{L};

weights{L} = weights{L} -learningRate\* vdW{L};

biases{L} = biases{L} -learningRate\* vdB{L};

elseif (strcmp(outputActivationFunc,"softmax"))

vdW{L} = beta\*vdW{L} + (1 -beta) \* gradsDW{L}';

vdB{L} = beta\*vdB{L} + (1 -beta) \* gradsDB{L}';

weights{L} = weights{L} -learningRate\* vdW{L};

biases{L} = biases{L} -learningRate\* vdB{L};

endif

end

\# Update parameters with RMSProp

\# Input : parameters - weights, biases

\# : gradients - gradsDW,gradsDB

\# : s -sdW, sdB

\# : beta1

\# : epsilon

\# : learningRate

\# : outputActivationFunc

#output : Updated weights and biases RMSProp

function \[weights biases\] = gradientDescentWithRMSProp(weights, biases,gradsDW,gradsDB, sdW, sdB, beta1, epsilon,

learningRate,outputActivationFunc="sigmoid")

L = size(weights)(2); # number of layers in the neural network

\# Update rule for each parameter.

for l=1:(L-1)

 sdW{l} = beta1\*sdW{l} + (1 -beta1) \* gradsDW{l} .\* gradsDW{l}; sdB{l} = beta1\*sdB{l} + (1 -beta1) \* gradsDB{l} .\* gradsDB{l}; weights{l} = weights{l} - learningRate\* gradsDW{l} ./ sqrt(sdW{l} +

epsilon);

biases{l} = biases{l} - learningRate\* gradsDB{l} ./ sqrt(sdB{l} + epsilon); endfor

if (strcmp(outputActivationFunc,"sigmoid"))

sdW{L} = beta1\*sdW{L} + (1 -beta1) \* gradsDW{L} .\* gradsDW{L}; sdB{L} = beta1\*sdB{L} + (1 -beta1) \* gradsDB{L} .\* gradsDB{L}; weights{L} = weights{L} -learningRate\* gradsDW{L} ./ sqrt(sdW{L}

+epsilon);

biases{L} = biases{L} -learningRate\* gradsDB{L} ./ sqrt(sdB{L} +

epsilon);

elseif (strcmp(outputActivationFunc,"softmax"))

sdW{L} = beta1\*sdW{L} + (1 -beta1) \* gradsDW{L}' .\* gradsDW{L}'; sdB{L} = beta1\*sdB{L} + (1 -beta1) \* gradsDB{L}' .\* gradsDB{L}'; weights{L} = weights{L} -learningRate\* gradsDW{L}' ./ sqrt(sdW{L}

+epsilon);

biases{L} = biases{L} -learningRate\* gradsDB{L}' ./ sqrt(sdB{L} +

epsilon);

endif

end

\# Update parameters with Adam

\# Input : parameters - weights, biases

\# : gradients -gradsDW,gradsDB

\# : v - vdW, vdB

\# : s - sdW, sdB

\# : t

\# : beta1

\# : beta2

\# : epsilon

\# : learningRate

\# : epsilon

#output : Updated weights and biases

function \[weights biases\] = gradientDescentWithAdam(weights, biases,gradsDW,gradsDB,

vdW, vdB, sdW, sdB, t, beta1, beta2, epsilon,

learningRate,outputActivationFunc="sigmoid")

vdW\_corrected = {};

vdB\_corrected = {};

sdW\_corrected = {};

sdB\_corrected = {};

L = size(weights)(2); # number of layers in the neural network

\# Update rule for each parameter.

for l=1:(L-1)

vdW{l} = beta1\*vdW{l} + (1 -beta1) \* gradsDW{l};

vdB{l} = beta1\*vdB{l} + (1 -beta1) \* gradsDB{l};

\# Compute bias-corrected first moment estimate.

vdW\_corrected{l} = vdW{l}/(1-beta1^t);

vdB\_corrected{l} = vdB{l}/(1-beta1^t);

sdW{l} = beta2\*sdW{l} + (1 -beta2) \* gradsDW{l} .\* gradsDW{l}; sdB{l} = beta2\*sdB{l} + (1 -beta2) \* gradsDB{l} .\* gradsDB{l};

\# Compute bias-corrected second moment estimate.

sdW\_corrected{l} = sdW{l}/(1-beta2^t);

sdB\_corrected{l} = sdB{l}/(1-beta2^t);

\# Update parameters.

d1=sqrt(sdW\_corrected{l}+epsilon);

d2=sqrt(sdB\_corrected{l}+epsilon);

weights{l} = weights{l} - learningRate\* vdW\_corrected{l} ./ d1; biases{l} = biases{l} -learningRate\* vdB\_corrected{l} ./ d2;

endfor

if (strcmp(outputActivationFunc,"sigmoid"))

vdW{L} = beta1\*vdW{L} + (1 -beta1) \* gradsDW{L};

vdB{L} = beta1\*vdB{L} + (1 -beta1) \* gradsDB{L};

\# Compute bias-corrected first moment estimate.

vdW\_corrected{L} = v{L}/(1-beta1^t);

 vdB\_corrected{L} = v{L}/(1-beta1^t); sdW{L} = beta2\*sdW{L} + (1 -beta2) \* gradsDW{L} .\* gradsDW{L}; sdB{L} = beta2\*sdB{L} + (1 -beta2) \* gradsDB{L} .\* gradsDB{L};

\# Compute bias-corrected second moment estimate.

sdW\_corrected{L} = s{L}/(1-beta2^t);

sdB\_corrected{L} = s{L}/(1-beta2^t);

\# Update parameters.

d1=sqrt(sdW\_corrected{L}+epsilon);

d2=sqrt(sdB\_corrected{L}+epsilon);

weights{L} = weights{L} - learningRate\* vdW\_corrected{L} ./ d1; biases{L} = biases{L} -learningRate\* vdB\_corrected{L} ./ d2;

elseif (strcmp(outputActivationFunc,"softmax"))

vdW{L} = beta1\*vdW{L} + (1 -beta1) \* gradsDW{L}';

vdB{L} = beta1\*vdB{L} + (1 -beta1) \* gradsDB{L}';

\# Compute bias-corrected first moment estimate.

vdW\_corrected{L} = vdW{L}/(1-beta1^t);

vdB\_corrected{L} = vdB{L}/(1-beta1^t);

sdW{L} = beta2\*sdW{L} + (1 -beta2) \* gradsDW{L}' .\* gradsDW{L}'; sdB{L} = beta2\*sdB{L} + (1 -beta2) \* gradsDB{L}' .\* gradsDB{L}';

\# Compute bias-corrected second moment estimate.

sdW\_corrected{L} = sdW{L}/(1-beta2^t);

sdB\_corrected{L} = sdB{L}/(1-beta2^t);

\# Update parameters.

d1=sqrt(sdW\_corrected{L}+epsilon);

d2=sqrt(sdB\_corrected{L}+epsilon);

weights{L} = weights{L} - learningRate\* vdW\_corrected{L} ./ d1; biases{L} = biases{L} -learningRate\* vdB\_corrected{L} ./ d2;

endif

end

\# Execute a L layer Deep learning model

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu /tanh

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : learning rate

\# : lambd

\# : keep\_prob

\# : num of iterations

#output : Updated weights and biases after each iteration

function \[weights biases costs\] = L\_Layer\_DeepModel(X, Y, layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",learning\_rate = .3, lambd=0, keep\_prob=1, num\_iterations = 10000,initType="default")#lr was 0.009

rand ("seed", 1);

costs = \[\] ;

if (strcmp(initType,"He"))

\# He Initialization

\[weights biases\] = HeInitializeDeepModel(layersDimensions);

elseif (strcmp(initType,"Xav"))

\# Xavier Initialization

\[weights biases\] = XavInitializeDeepModel(layersDimensions);

else

\# Default initialization.

\[weights biases\] = initializeDeepModel(layersDimensions);

endif

\# Loop (gradient descent)

for i = 0:num\_iterations

\# Forward propagation: \[LINEAR -> RELU\]\*(L-1) -> LINEAR -> SIGMOID.

\[AL forward\_caches activation\_caches droputMat\] =

forwardPropagationDeep(X, weights, biases,keep\_prob, hiddenActivationFunc, outputActivationFunc=outputActivationFunc);

\# Regularization parameter is 0

if (lambd==0)

\# Compute cost.

cost = computeCost(AL,

Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));

else

\# Compute cost with regularization

cost = computeCostWithReg(weights, AL, Y, lambd,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));

endif

\# Backward propagation.

\[gradsDA gradsDW gradsDB\] = backwardPropagationDeep(AL, Y,

activation\_caches,forward\_caches, droputMat, lambd, keep\_prob, hiddenActivationFunc, outputActivationFunc=outputActivationFunc, numClasses=layersDimensions(size(layersDimensions)

(2)));

\# Update parameters.

\[weights biases\] = gradientDescent(weights,biases,

gradsDW,gradsDB,learning\_rate,outputActivationFunc=outputActivationFunc);

\# Print the cost every 1000 iterations

if ( mod(i,1000) == 0)

costs =\[costs cost\];

#disp ("Cost after iteration"), L2RegularizationCost(i),disp(cost); printf("Cost after iteration i=%i cost=%d\\n",i,cost); endif

endfor

end

\# Execute a L layer Deep learning model with Stochastic Gradient descent

\# Input : X - Input features

\# : Y output

\# : layersDimensions - Dimension of layers

\# : hiddenActivationFunc - Activation function at hidden layer relu

/tanh/sigmoid

\# : outputActivationFunc - Activation function at hidden layer sigmoid/softmax

\# : learning rate

\# : lrDecay

\# : decayRate

\# : lambd

\# : keep\_prob

\# : optimizer

\# : beta

\# : beta1

\# : beta2

\# : epsilon

\# : mini\_batch\_size

\# : num of epochs

#output : Updated weights and biases after each iteration

function \[weights biases costs\] = L\_Layer\_DeepModel\_SGD(X, Y, layersDimensions, hiddenActivationFunc='relu',

outputActivationFunc="sigmoid",learningRate = .3,

lrDecay=false,decayRate=1,

lambd=0, keep\_prob=1,

optimizer="gd", beta=0.9, beta1=0.9,

beta2=0.999,epsilon=10^-8,

mini\_batch\_size = 64, num\_epochs = 2500)

disp("here");

printf("learningRate=%f ",learningRate);

printf("lrDecay=%d ",lrDecay);

printf("decayRate=%f ",decayRate);

printf("lamd=%d ",lambd);

printf("keep\_prob=%f ",keep\_prob);

printf("optimizer=%s ",optimizer);

printf("beta=%f ",beta);

printf("beta1=%f ",beta1);

printf("beta2=%f ",beta2);

printf("epsilon=%f ",epsilon);

printf("mini\_batch\_size=%d ",mini\_batch\_size);

printf("num\_epochs=%d ",num\_epochs);

t=0;

 rand ("seed", 1);

costs = \[\] ;

\# Parameters initialization.

\[weights biases\] = initializeDeepModel(layersDimensions);

if (strcmp(optimizer,"momentum"))

\[vdW vdB\] = initializeVelocity(weights, biases);

elseif(strcmp(optimizer,"rmsprop"))

\[sdW sdB\] = initializeRMSProp(weights, biases);

elseif(strcmp(optimizer,"adam"))

\[vdW vdB sdW sdB\] = initializeAdam(weights, biases);

endif

seed=10;

\# Loop (gradient descent)

for i = 0:num\_epochs

seed = seed + 1;

\[mini\_batches\_X mini\_batches\_Y\] = random\_mini\_batches(X, Y,

mini\_batch\_size, seed);

minibatches=length(mini\_batches\_X);

for batch=1:minibatches

X=mini\_batches\_X{batch};

Y=mini\_batches\_Y{batch};

\# Forward propagation: \[LINEAR -> RELU\]\*(L-1) -> LINEAR -> SIGMOID/SOFTMAX.

\[AL forward\_caches activation\_caches droputMat\] =

forwardPropagationDeep(X, weights, biases, keep\_prob,hiddenActivationFunc, outputActivationFunc=outputActivationFunc);

#disp(batch);

#disp(size(X));

#disp(size(Y));

if (lambd==0)

\# Compute cost.

cost = computeCost(AL,

Y,outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));

else

 # Compute cost with regularization cost = computeCostWithReg(weights, AL, Y, lambd,

outputActivationFunc=outputActivationFunc,numClasses=layersDimensions(size(layersDimensions) (2)));

endif

#disp(cost);

\# Backward propagation.

\[gradsDA gradsDW gradsDB\] = backwardPropagationDeep(AL, Y,

activation\_caches,forward\_caches, droputMat, lambd, keep\_prob, hiddenActivationFunc, outputActivationFunc=outputActivationFunc, numClasses=layersDimensions(size(layersDimensions)

(2)));

if (strcmp(optimizer,"gd"))

\# Update parameters.

\[weights biases\] = gradientDescent(weights,biases,

gradsDW,gradsDB,learningRate,outputActivationFunc=outputActivationFunc); elseif (strcmp(optimizer,"momentum"))

\[weights biases\] = gradientDescentWithMomentum(weights,

biases,gradsDW,gradsDB, vdW, vdB, beta,

learningRate,outputActivationFunc);

elseif (strcmp(optimizer,"rmsprop"))

\[weights biases\] = gradientDescentWithRMSProp(weights,

biases,gradsDW,gradsDB, sdW, sdB, beta1, epsilon,

learningRate,outputActivationFunc);

elseif (strcmp(optimizer,"adam"))

t=t+1;

\[weights biases\] = gradientDescentWithAdam(weights,

biases,gradsDW,gradsDB,vdW, vdB, sdW, sdB, t, beta1, beta2, epsilon, learningRate,outputActivationFunc);

endif

endfor

\# Print the cost every 1000 iterations

if ( mod(i,1000) == 0)

costs =\[costs cost\];

#disp ("Cost after iteration"), disp(i),disp(cost); printf("Cost after iteration i=%i cost=%d\\n",i,cost); endif

 if(lrDecay==true)

learningRate=decayRate^(num\_epochs/1000)\*learningRate;

endif

endfor

end

\# Plot cost vs iterations

function plotCostVsIterations(maxIterations,costs,fig1)

iterations=\[0:1000:maxIterations\];

plot(iterations,costs);

title ("Cost vs no of iterations ");

xlabel("No of iterations");

ylabel("Cost");

print -dpng figReg2-o

end;

\# Plot cost vs number of epochs

function plotCostVsEpochs(maxEpochs,costs,fig1)

epochs=\[0:1000:maxEpochs\];

plot(epochs,costs);

title ("Cost vs no of epochs ");

xlabel("No of epochs");

ylabel("Cost");

print -dpng fig5-o

end;

\# Compute the predicted value for a given input

\# Input : Neural Network parameters

\# : Input data

function \[predictions\]= predict(weights, biases,

X,keep\_prob=1,hiddenActivationFunc="relu")

\[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights, biases,keep\_prob,hiddenActivationFunc);

predictions = (AL>0.5);

end

\# Plot the decision boundary

function plotDecisionBoundary(data,weights,

biases,keep\_prob=1,hiddenActivationFunc="relu",fig2)

%Plot a non-linear decision boundary learned by the SVM

colormap ("summer");

% Make classification predictions over a grid of values

x1plot = linspace(min(data(:,1)), max(data(:,1)), 400)';

x2plot = linspace(min(data(:,2)), max(data(:,2)), 400)';

\[X1, X2\] = meshgrid(x1plot, x2plot);

vals = zeros(size(X1));

\# Plot the prediction for the grid

for i = 1:size(X1, 2)

gridPoints = \[X1(:, i), X2(:, i)\];

vals(:, i)=predict(weights, biases,gridPoints',keep\_prob,

hiddenActivationFunc=hiddenActivationFunc);

endfor

scatter(data(:,1),data(:,2),8,c=data(:,3),"filled");

% Plot the boundary

hold on

#contour(X1, X2, vals, \[0 0\], 'LineWidth', 2);

contour(X1, X2, vals,"linewidth",4);

title ({"3 layer Neural Network decision boundary"}); hold off;

print -dpng figReg22-o

end

\# Compute scores

function \[AL\]= scores(weights, biases, X,hiddenActivationFunc="relu")

\[AL forward\_caches activation\_caches\] = forwardPropagationDeep(X, weights, biases,hiddenActivationFunc);

end

\# Create Random mini batches. Return cell arrays with the mini batches

\# Input : X, Y

\# : Size of minibatch

#Output : mini batches X & Y

function \[mini\_batches\_X mini\_batches\_Y\]= random\_mini\_batches(X, Y, miniBatchSize = 64, seed = 0)

rand ("seed", seed);

\# Get number of training samples

m = size(X)(2);

\# Create a list of random numbers < m

permutation = randperm(m);

\# Randomly shuffle the training data

shuffled\_X = X(:, permutation);

shuffled\_Y = Y(:, permutation);

\# Compute number of mini batches

numCompleteMinibatches = floor(m/miniBatchSize);

batch=0;

for k = 0:(numCompleteMinibatches-1)

#Set the start and end of each mini batch

batch=batch+1;

lower=(k\*miniBatchSize)+1;

upper=(k+1) \* miniBatchSize;

mini\_batch\_X = shuffled\_X(:, lower:upper);

mini\_batch\_Y = shuffled\_Y(:, lower:upper);

\# Create cell arrays

mini\_batches\_X{batch} = mini\_batch\_X;

mini\_batches\_Y{batch} = mini\_batch\_Y;

endfor

\# If the batc size does not cleanly divide with number of mini batches if mod(m ,miniBatchSize) != 0

\# Set the start and end of the last mini batch

l=floor(m/miniBatchSize)\*miniBatchSize;

m=l+ mod(m,miniBatchSize);

mini\_batch\_X = shuffled\_X(:,(l+1):m);

mini\_batch\_Y = shuffled\_Y(:,(l+1):m);

batch=batch+1;

mini\_batches\_X{batch} = mini\_batch\_X;

mini\_batches\_Y{batch} = mini\_batch\_Y;

 endif

end

\# Plot decision boundary

function plotDecisionBoundary1( data,weights, biases,keep\_prob=1, hiddenActivationFunc="relu")

% Make classification predictions over a grid of values

x1plot = linspace(min(data(:,1)), max(data(:,1)), 400)';

x2plot = linspace(min(data(:,2)), max(data(:,2)), 400)';

\[X1, X2\] = meshgrid(x1plot, x2plot);

vals = zeros(size(X1));

for i = 1:size(X1, 2)

gridPoints = \[X1(:, i), X2(:, i)\];

\[AL forward\_caches activation\_caches\] =

forwardPropagationDeep(gridPoints', weights,

biases,keep\_prob,hiddenActivationFunc, outputActivationFunc="softmax");

\[l m\] = max(AL, \[ \], 2);

vals(:, i)= m;

endfor

scatter(data(:,1),data(:,2),8,c=data(:,3),"filled");

% Plot the boundary

hold on

contour(X1, X2, vals,"linewidth",4);

print -dpng "fig-o1.png"

end

#############

\# Note: Using cellArray\_to\_vector followed by vector\_to\_cellArray => original cellArray

##############

\# Convert a weight,biases as a cell array to a vector

\# Input : weight and biases cell array

\# Returns : vector

function \[vec\] = cellArray\_to\_vector(weights,biases)

vec=\[\];

for i = 1: size(weights)(2)

w= weights{i};

sz=size(w);

 # Take transpose before reshaping l=reshape(w',sz(1)\*sz(2),1);

b=biases{i};

sz1=size(b);

m=reshape(b',sz1(1)\*sz1(2),1);

#Concatenate

vec=\[vec;l;m\];

endfor

end

\# Convert gradients cell array to a vector

\# Input : gradients cell array

\# Returns : vector

function \[vec\] = gradients\_to\_vector(gradsDW,gradsDB)

vec=\[\];

for i = 1: size(gradsDW)(2)

gW= gradsDW{i};

sz=size(gW);

\# Take transpose before reshaping

l=reshape(gW',sz(1)\*sz(2),1);

gB=gradsDB{i};

sz1=size(gB);

m=reshape(gB',sz1(1)\*sz1(2),1);

#Concatenate

vec=\[vec;l;m\];

endfor

end

\# Convert a vector to a cell array

\# Input : vector

\# Returns : cell array

function \[weights1 biases1\] = vector\_to\_cellArray(weights, biases,params) vec=\[\];

weights1 = {};

biases1 ={};

start=1;

for i = 1: size(weights)(2)

 w= weights{i};

sz=size(w);

\# Take transpose before reshaping

a = params(start:start+sz(1)\*sz(2)-1,1);

b = reshape(a,sz(2),sz(1));

weights1{i}= b';

start=start+sz(1)\*sz(2);

b=biases{i};

sz=size(b);

c = params(start:start+sz(1)\*sz(2)-1,1);

d = reshape(c,sz(2),sz(1));

biases1{i}= d';

start=start+sz(1)\*sz(2);

endfor

end

\# Convert a vector to a cell array

\# Input : vector

\# Returns : cell array

function \[weights1 biases1\] = vector\_to\_cellArray1(weights, biases,gradients) vec=\[\];

weights1 = {};

biases1 ={};

start=1;

for i = 1: size(weights)(2)

w= weights{i};

sz=size(w);

\# Take transpose before reshaping

a = grads(start:start+sz(1)\*sz(2)-1,1);

b = reshape(a,sz(2),sz(1));

weights1{i}= b';

start=start+sz(1)\*sz(2);

b=biases{i};

sz=size(b);

c = grads(start:start+sz(1)\*sz(2)-1,1);

d = reshape(c,sz(2),sz(1));

biases1{i}= d';

start=start+sz(1)\*sz(2);

endfor

end

\# Perform Gradient check

\# Input : weights,biases

\# : gradsDW,gradsDB

\# : X

\# : Y

\# : epsilon

\# : outputActivationFunc

\# : numClasses

\# Returns :

function \[difference\]= gradient\_check\_n(weights,biases,gradsDW,gradsDB, X, Y, epsilon = 1e-7,outputActivationFunc="sigmoid",numClasses)

\# Convert cell array to vector

parameters\_values = cellArray\_to\_vector(weights, biases);

\# Convert gradient cell array to vector

grad = gradients\_to\_vector(gradsDW,gradsDB);

num\_parameters = size(parameters\_values)(1);

#Initialize

J\_plus = zeros(num\_parameters, 1);

J\_minus = zeros(num\_parameters, 1);

gradapprox = zeros(num\_parameters, 1);

\# Compute gradapprox

for i = 1:num\_parameters

\# Compute J\_plus\[i\]. Inputs: "parameters\_values, epsilon". Output =

"J\_plus\[i\]".

thetaplus = parameters\_values;

thetaplus(i,1) = thetaplus(i,1) + epsilon;

\[weights1 biases1\] =vector\_to\_cellArray(weights, biases,thetaplus);

\[AL forward\_caches activation\_caches droputMat\] =

forwardPropagationDeep(X', weights1, biases1, keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc); J\_plus(i) = computeCost(AL, Y',

outputActivationFunc=outputActivationFunc,numClasses);

\# Compute J\_minus\[i\]. Inputs: "parameters\_values, epsilon". Output =

"J\_minus\[i\]".

thetaminus = parameters\_values;

thetaminus(i,1) = thetaminus(i,1) - epsilon ;

\[weights1 biases1\] = vector\_to\_cellArray(weights, biases,thetaminus);

\[AL forward\_caches activation\_caches droputMat\] =

forwardPropagationDeep(X',weights1, biases1, keep\_prob=1,

hiddenActivationFunc="relu",outputActivationFunc=outputActivationFunc); J\_minus(i) = computeCost(AL, Y',

outputActivationFunc=outputActivationFunc,numClasses);

\# Compute gradapprox\[i\]

gradapprox(i) = (J\_plus(i) - J\_minus(i))/(2\*epsilon);

endfor

\# Compute L2Norm

numerator = L2NormVec(grad-gradapprox);

denominator = L2NormVec(grad) +

L2NormVec(gradapprox);

difference = numerator/denominator;

;

if difference > 1e-04

printf("There is a mistake in the implementation "); disp(difference);

else

printf("The implementation works perfectly");

disp(difference);

endif

\# This can be used to compare the gradients from backprop and gradapprox

\[weights1 biases1\] = vector\_to\_cellArray(weights, biases,grad); printf("Gradients from back propagation");

disp(weights1);

disp(biases1);

\[weights2 biases2\] = vector\_to\_cellArray(weights, biases,gradapprox);

 printf("Gradients from gradient check"); disp(weights2);

disp(biases2);

end

\# Compute L2Norm

function \[l2norm\] = L2NormVec(x)

l2norm=sqrt(sum(x .^ 2));

end

 **References**

1\. Deep Learning Specialization -

https://www.coursera.org/specializ[ations/deep-learning](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

2\. Neural Networks for Machine Lea[rning -](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

https://www.coursera.org/learn/ne[ural-networks](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

3\. Deep Learning by Ian Goodfellow[, Yoshua Bengio and Aaron](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

Courville - http://www.deeplearni[ngbook.org/](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

4\. Neural Networks: The mechanics [of backpropagation -](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

https://gigadom.wordpress.com/20[17/01/21/neural-networks-the-](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

mechanics-of-backpropagation/

5\. Machine Learning - https://www.c[oursera.org/learn/machine-](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

learning

6\. CS231n Convolutional Neural Net[works for Visual Recognition](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

\-http://cs231n.github.io/neural-net[works-case-study/](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

7\. The Softmax function and its deri[vative -](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

https://eli.thegreenplace.net/2016/t[he-softmax-function-and-its-](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

derivative/

8\. Cross Validated -

https://stats.stackexchange.com/qu[estions/235528/backpropagatio](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)n-with-softmax-cross-entropy

9\. CS231n: How to calculate gradien[t for Softmax loss function? -](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

https://stackoverflow.com/questio[ns/41663874/cs231n-how-to-](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

calculate-gradient-for-softmax-los[s-function](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

10\. Derivative of Softmax loss functio[n -](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

https://math.stackexchange.com/q[uestions/945871/derivative-of-](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

softmax-loss-function

11\. The Matrix Calculus You Need Fo[r Deep Learning -](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

[https://arxiv.org/abs/1802.01528](https://arxiv.org/abs/1802.01528)

12\. A Step by Step Backpropagation [Example -](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

[https://mattmazur.com/2015/03/17/a-step-by-step-](https://mattmazur.com/2015/03/17/a-step-by-step-backpropagation-example/)

[backpropagation-example/](https://mattmazur.com/2015/03/17/a-step-by-step-backpropagation-example/)

13\. The Backpropagation Algorithm - [https://page.mi.fu-](https://page.mi.fu-berlin.de/rojas/neural/chapter/K7.pdf)

berlin.de/rojas/neural/chapter/K7.pdf

14\. Backpropagation Learning-

[https://www.cs.cmu.edu/afs/cs/academic/class/15883-](https://www.cs.cmu.edu/afs/cs/academic/class/15883-f15/slides/backprop.pdf)

[f15/slides/backprop.pdf](https://www.cs.cmu.edu/afs/cs/academic/class/15883-f15/slides/backprop.pdf)

15\. Practical Machine Learning with R and Python – Machine

Learning in stereo -https://www.amazon.com/dp/1973443503

# Document Outline

*   [Preface](#index_split_000.html#p6)
*   [Introduction](#index_split_000.html#p10)
*   [1.Logistic Regression as a Neural Network](#index_split_000.html#p13)
*   [2.Implementing a simple Neural Network](#index_split_000.html#p36)
*   [3.Building a L- Layer Deep Learning Network](#index_split_000.html#p79)
*   [4.Deep Learning network with the Softmax](#index_split_000.html#p134)
*   [5.MNIST classification with Softmax](#index_split_001.html#p161)
*   [6.Initialization, regularization in Deep Learning](#index_split_001.html#p194)
*   [7.Gradient Descent Optimization techniques](#index_split_001.html#p262)
*   [8.Gradient Check in Deep Learning](#index_split_002.html#p313)
*   [1.Appendix A](#index_split_002.html#p347)
*   [2.Appendix 1 – Logistic Regression as a Neural Network](#index_split_002.html#p356)
*   [3.Appendix 2 - Implementing a simple Neural Network](#index_split_002.html#p369)
*   [4.Appendix 3 - Building a L- Layer Deep Learning Network](#index_split_002.html#p391)
*   [5.Appendix 4 - Deep Learning network with the Softmax](#index_split_003.html#p424)
*   [6.Appendix 5 - MNIST classification with Softmax](#index_split_003.html#p441)
*   [7.Appendix 6 - Initialization, regularization in Deep Learning](#index_split_004.html#p495)
*   [8.Appendix 7 - Gradient Descent Optimization techniques](#index_split_005.html#p564)
*   [9.Appendix 8 – Gradient Check](#index_split_006.html#p662)
*   [References](#index_split_007.html#p774)