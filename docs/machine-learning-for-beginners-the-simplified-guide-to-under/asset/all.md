   

![](images/00001.jpeg)

 

 

 

 

 

 

INTRODUCTION

Thank you for downloading the book “Machine learning for beginners” The purpose of this book is to teach you about how machine learning works easily, using step by step approach and without mathematics or computer language-- Deep Neural Networks

This book is about guiding the complete beginners how Machine Learning works using perceptron which is similar to neurons in the human brain with the basic knowledge to know in order to study Machine Learning easily.

ML is a tricky subject but this book seeks to introduce the subject matter to complete beginners such that the basics and theory of ML  as to its operation and uses can easily be comprehended by complete beginners.  This book will break to small bits the essentials of ML to facilitate the easy understanding of Machine Learning.

The benefits of Machine Learning 

Here are some benefits of Machine Learning.  We shall deal more exhaustively with these benefits under another chapter on the application of Machine Learning

   Machine Learning helps in managing massive and multidimensional data of different types in a particular environment.  It makes computer handling of assorted information from different origin to be easy such that they can be stockpiled and arranged in such a manner to give fast outcomes for different searches.

   Machine Learning makes information processing very fast, diverse, multidimensional, accurate and cheap while dissecting on a large scale mind-blowing and massive information. 

   By gathering information and feeding it into the computer, Machine Learning can be used to forecast and to make the high precision prediction on available opportunities as well as warnings that can lead to abstaining from potential dangers in the business world. This kind of information gathering and computing can give a business a competitive edge over a stiff contender.

   It helps in the financial world with critical decisions on two core areas which are, when to venture into a business or forestall extortion which may help to make the decision on when to exchange or abstain from the business.

   It can help in limiting of data fraud in security outfits of government or privately owned ones. Hence Machine Learning is of top use in security systems.

   Machine Learning can be of tremendous use in healthcare by reason of data input.  The machine can be used to make a precise and accurate diagnosis.

   It is becoming the future of retail by virtue of your past buying the computer can elucidate the product the individual may likely be interested in.  That is the new port of the retail world.  Machine Learning can now process the history of former purchases and predict what the client is likely going to be interested in.

   It has a huge usage in oil and gas where Machine Learning is used to process available data into intelligent information streamlining oil dissemination to make it more productive and precise. The usage is still expanding in this area.

   It’s of huge importance in transportation businesses.  It helps to distinguish between patterns which are of great benefit in transportation.  Efficient use of Machine Learning can help to expand benefits.

 

  

CHAPTER 1

WHAT IS MACHINE LEARNING?

Machine Learning is an arm of artificial intelligence which is a relatively new form of computer programming that allows the computer to access massive data which also allows the machine to learn on its own through the experience without the machine being programmed as such.  The machine learns on its own.  Through different input data and through experience it is able to do certain tasks which were not pre-programmed.  It is basically the analysis and interpretation of patterns of information supplied to the computer.

Machine Learning otherwise known as ML is a growing subject which can play key roles in a wide range of conditions from language to lineage recognition to data mining.

The mainstay here is automatic learning of computers due to experience on data provided.  It puts the computer in a self-learning mode as the computer is fed with new data, it readjusts, grows and develop itself irrespective of the fact that it was not programmed explicitly. It gains from examples and information fed it and comes to a resolution with little no human aid

 

THE TYPICAL TASKS ENTRUSTED TO MACHINE LEARNING

Machine Learning tasks can be classified into many broad categories.  Under Machine Learning tasks we have supervised learning and semi-supervised learning.  Supervised learning is built around mathematical models which can be derived from a set of data input and desired output. So we have under this category of training data.

 Semi-supervised learning is the mathematical model built around incomplete data training.  That means some of the input data do not have labels attached to them.

There are many types of tasks that are associated with Machine Learning but the key ones are: 

   Feature selection

   Regression

   Classification

   Clustering 

   Testing and matching

   Density estimation

   Dimension reduction

   Multivariate querying

Of all these tasks associated with Machine Learning, we will like to concentrate on regression and classification.  Regression and classification tasks are basically supervised learning. While output for classification is discrete in nature regression is a prediction of continuous quantities. 

REGRESSION TASK

This task under Machine Learning has to do with numerical estimation and data that are continuous in nature which can otherwise be known as continuous variables. Under this task, we have things like 

   Estimation price for a housing unit

   Product price

   Stock price etc

This task has to do with the financial world of buying and selling and accounting procedures associated with numerical data.

The following methods can be used to achieve the objectives of this task which can be subdivided into two groups.

High accuracy method: 

*   Kernel regression
*   Gaussian process regression

Not so high accurate method

*   Regression trees
*   Linear regression
*   Support vector regression
*   LASSO.

The other branch of Machine Learning we will like to treat is 

CLASSIFICATION TASK

This is otherwise known as discrete variables.  It is about predicting a category of data. Example of this is predicting whether a mail is a spam or not.  It is also used highly in the area of healthcare. That is, predicting whether or not a person is suffering from one disease or not. It is also used in the financial world to determine whether a transaction is fraudulent or not.

This task can also be divided into two broad branches namely the high accuracy and the not so accurate.

Under high accuracy tasks, the following methods could be used to solve the problems of this task

*   K – Nearest Neighbours 
*   Artificial neural networks (ANN) 
*   Support vector machine (SVM) 
*   Random forest  

Not so accurate method 

*   Decision trees
*   Boosted trees
*   Logistic regression
*   Naive Bayes
*   Deep learning.

Under the topic Regression we will like to expatiate on the following:

KERNEL REGRESSION

This is an estimation technique to fit data.  It is categorized as a non – parametric technique.  It is different from linear regression which is based on the assumption of normal distribution because it does not assume any distribution to estimate the regression function.

What kernel regression does is to put a set of the identical function called kernel local to each observation data point. It is a superset of other weighted regression and it is closely related to Moving Average (MA), K nearest Neighbour (KNN), Radial Basis Function (RBF), neural network (NN) and Support Vector Machine (SVM)

We shall define these parameters before going on

MA – MOVING AVERAGE

This is average derived from various statistical data that are not related.  it is a technical analysis that helps to make sense of various random data.  The example is making sense out of price fluctuations to see whether the price is increasing or lagging.  This type of parameter is what is used to forecast in the stock exchange.  It helps in forecasting based on the past prices trend.  There are two moving averages in use which are the simple moving average – SMA and the exponential moving average – EMA.  

The simple moving average – SMA is the data obtained by examining the trend over a defined period of time while exponential moving average – EMA gives greater weight to the more recent data. That is the more recent data is what is considered in EMA so one can conclude that SMA is analysis data over a very long time while EMA is consideration of data over a short period of time.

These two parameters can now be used to generate other technical indicators such as Moving Average Convergence Divergence – MACD   

Application of moving average in real life is predicting the stock. Exchange.   If properly utilized it can predict whether the market is bullish that is uptrend or bearish that is a downtrend.   

 

Gaussian process regression

This is a distribution over functions and inferences taking place in the space of functions. They have parameters that can be changed by setting certain parameters.  That means the properties begin to change as parameters are changed or varied.  A sharp example is the GP model which takes the form of full predictive distribution. Also, the learning of inverse dynamics of a robot is a practical example.

All these models have so many statistical and mathematical functions but we do not intend to bore you with these things at this beginning.  All we want is to give you familiarization tour around the topic in layman language for easy comprehension.  

This model utilizes the weight – space view which is a simple linear regression model where the output is linear combinations of the inputs.  This means the main virtue of the model is the simplicity of implementation and interpretation while the drawback is that if the output cannot be reasonably approximated, the linear function will give poor predictions.

 

Under classification we will like to treat the following models:

KNN – K NEAREST NEIGHBOUR

This parameter is part of supervised learning which has been used in many applications successfully.  It has been used in the field of statistical pattern recognition like speech and handwriting recognition, data mining, etc.  The purpose of this is to classify a new object based on previous training samples.  It does not use any model but only uses memory. For a query, we find k number of objects or training points that are closest to the query point. It is using majority votes among the k objects. It uses neighborhood classification to predict the value of the new query. 

Example of this parameter is predicting the quality outcome of a new product from the same company but with different properties from the former ones using the outcome of data obtained from questionnaires survey asking people about their opinion of the product whether it is good or not using four training samples namely data of acid durability and strength.

Acid durabilitystrengthclassification

66bad

64bad

34good

14good

Using this data it is possible to determine without another survey whether another product which has acid durability 3 and strength 2 from the laboratory test can be classified as good or as bad. Its application in real life is marketing. It can be used to deduce whether a product will be seen as good or not.

RBF – RADIAL BASIS FUNCTION

This function has the real value which depends on the distance from the origin or a centre.  Origin in geometry is a fixed special point of reference denoted as O used as a reference point in relation to the surrounding area.  This function is used to build up the approximation of a given function or data called multivariate. Because it is radial it can be used in more than one dimension;   therefore a radial function is a function paired in a vector or metric space having a centre C.  This function is associated with what is called radial kernels.  Hence radial kernels are the basis for radial basis functions.

Commonly used types are shape parameters that can be used to scale the input of the radial kernel. It is used highly in Neural Networks and learning theory. One unique application of Radial Basis Function is in mechanical fault diagnosis. This function has been used to develop models for dehydration of plant materials and the vast area of science and technology. 

NN – NEURAL NETWORKS

This is the model that uses perceptron to operate.  Single layer operation of a linear model is called Perceptron and multiples of these single-layer modes when combined together form what is known as Neural Networks.   

This is a computer program modeled after the human brain and nervous system. For example, a neural network can use examples to infer rules for recognition of handwritten digits.  This model works like our brain. It tries to decipher digits and make inferences just like our eyes will do.  

 

 It takes a large number of handwritten digits known as examples and then develops a model that can learn from these training examples.  That is, it uses examples to automatically build up rules for recognizing handwritten digits. By increasing the number of learning examples the skill of the model can predict handwriting with high accuracy.  

Accuracy is a function of the degree of learning examples this network is exposed to.  The more the learning examples the more accurate the network prediction will be.  Application of this model will be handwritten recognition, speech recognition

 

SVM – SUPPORT VECTOR MACHINE

This is a supervised learning model in Machine Learning. They analyze data used for classification and regression.  It produces significant accuracy with less computation power.   It can be used for both classification and regression tasks. It helps to separate two classes of data points where there are several of them. These two classes should have maximum distances between the data points such that in the future, data points that fall within the model can be classified with more confidence and accuracy.  This maximizes the margin of the classifier.

Application of this model can be found in the field of hydrology. It is used in flood routing.  It is used in face detection, text and hypertext categorization, classification of images, bioinformatics, handwriting recognition, and Generalized Predictive Control GPC

  

CHAPTER 2

ARTIFICIAL NEURAL NET: PERCEPTRON

Artificial Neural Networks has a unique capacity to learn from examples and training data hence it is able to adapt to the changing environment. It is able to deal with very approximate and uncertain data known as a noisy environment and has been the focus in various fields of science and technology.  

1.  PERCEPTRON

1.         Linear function
2.         Activation function

What is perceptron?

 

Perceptron is a word coined out of perception which is a concept built around the way the eye sees an object and able to come to conclusion about it.  Perception uses neurons in the human brain while perceptron uses artificial neuron to do its work.  Perceptron is a single layer neural network while multilayer perceptron is known as Neural Networks.  Therefore multilayer perceptron form Neural Network.

 

It works by taking several binary inputs and producing a single binary output

![](images/00002.jpeg)

![](images/00003.jpeg) 

![](images/00004.jpeg)![](images/00005.jpeg)INPUTSOUTPUT

 

 

![](images/00006.jpeg)

In this example, the perceptron has three inputs and one output.  The more the number of inputs the more accurate the output result after processing through the perceptron.

 

It is a model that makes decisions based on weighing all the evidence before it. The first layer of perceptron is based on making three simple decisions by considering the input data. The second layer perceptron is making decisions based on weighing the decisions of the first layer perceptron. Therefore the second layer can make a decision at a more abstract and complex level than perceptron at first layer.

 

Perceptron of the third layer will thereby make much more complex decisions than the second layer thereby from the foregoing multiple layer perceptron can make sophisticated decisions from complex data before it. Although in the computer the output looks like they are many but in the real sense there is only one output because one output may be the input for another layer of perceptron.

 

2.            HOW CAN A MACHINE LEARN USING PERCEPTRON

1.         Supervised learning

Perceptron is used in supervised learning. It helps in classifying the data inputs into it.  The machine learns through four layers consisting in

*   Input data 
*   Weight and bias
*   Net sum 
*   Activation function

That means the input data is subjected to a set of weight and biases. The weight shows the strength of the function while the biases allow for the up and down shift within the activation function.  The activation function determines the output of the neural network as in either yes or no.

In Machine Learning, the algorithm for supervised learning is perceptron.  It is binary and linear classifiers.  That is, it makes is predictions based on a linear predictor function.

The machines learn by writing a Machine Learning algorithm. Some are more complex than others but the simplest is single layer perceptron.

2.         Unsupervised learning

This type of learning has another nomenclature called Hebbian Learning.  It is a method of machine learning without supervision or teacher.  It is like to teach yourself procedure.  This is based on cluster and probability and density of data input that is before it.  This model recognizes common variables in the data and reacts based on the absence or presence of the common variables

Unsupervised learning is the model used in density estimation in statistics. It tends to infer on priority probability while supervised learning is based on conditional probability producing conditional probability distribution. This model tends to mimic human logic because it searches for indirect or hidden structures or patterns to analyze new data.

Common models or algorithm used in unsupervised learning are 

 Clustering

 Anomaly detection

 Neural networks

 Latent variable models

These models can be subdivided into smaller subsets. 

 

 

3.                  Reinforcement learning

 

There are three paradigms in machine learning which are supervised learning, unsupervised learning and reinforcement learning.  Reinforcement learning is a special area of machine learning wherein software agents seeks to take action in an environment so as to maximize some notions to give a cumulative reward. It is goal oriented algorithm which learns how to attain a complex objective or goal over many steps. It can start from a blank point to achieve a superhuman performance when under the right condition.

 

For example Reinforcement algorithm incorporating deep learning can beat world champions at the game as well as a human expert.  It is state of the art computer program that is progressing rapidly. A precise example is ALPHAGO which is a computer program that defeated world champion at the ancient Chinese game of Go.  Zero is also another program that is even stronger than Alphago and it is the strongest player GO in history.

 

  
CHAPTER 3 

 

DEEP NEURAL NETWORK: REGRESSION

 

This is an artificial neural network ANN with multiple layers between the input and output layers.  It seeks to find the correct mathematical manipulation to turn the input into the output whether it has a linear or non-linear relationship.  The following topics will be considered in this chapter. 

 

1Feed forward neural networks 

This is an artificial neural network where the connection between the data does not form a cycle. Therefore it is different from recurrent neural networks.  This network was the simplest and was the first artificial network. In this network information only moves in one direction from the input layer to the output layer with or without passing through hidden layers.  In this network, there are no cycles or loops.

 

Deep feed forward networks are also known as multilayer perceptrons.  They are the foundation of most deep learning models.  Therefore CNN and RNN are based on feed forward networks.  The network is used for supervised Machine Learning.  The prime goal of feed forward networks is to approximate some regression functions and map them with output function. When this is done properly through mathematical computation it results in best approximation.  The reason it is called feed forward is that the flow of information moves in a forward direction only.

 

Feed forward network is a better model than linear models because linear models are limited to only linear functions whereas neural networks are not. Linear model faces serious problems if the data is not linearly separable.  It faces problems in approximation which in neural networks is very easy. Under this heading, we will discuss a little about the following functions.

 

1.                   Linear function

A linear function is a function that produces a straight line graph if plotted on the graph mathematically.   It is a function that has one or more variables without exponents or powers.  These variables must be constant or known to continue to remain as a linear function.  The checklist to identifying a linear function is as follows:  first, it must have two variables and if it has a third one, the third must be a constant. Secondly, none of the variables should have an exponent and thirdly it must always give a straight line curve at all times.  Any shift from these three has disqualified the function; it is no longer a linear function.

 

2.   Activation function

The activation function is artificial neurons that deliver an output based on inputs.  The visual model of the artificial neuron best explains this function. It is the end of the neural structure.  It is modeled after the axon of a biological neuron. It is a function that is based on binary inputs of 0 or 1 or a function that connects a range of outputs based on inputs.

Activation function otherwise known as transfer function is often associated with a graph that involves so many outputs.  An activation function can be linear or non – linear while the linear function maintains constant output non – linear activation function is able to create more variables which can be used to build a neural network.  Examples are sigmoid and ReLU functions used by neural networks to build working models.

3.                   Error functions

This is also known as Gauss error function.  It is a special function of sigmoid shape that one can find in probability, statistics, and partial differential equations.  There are other closely related functions like complementary error function and imaginary error function.  It is used to describe the bit error rate of a digital communication system.

4.   Optimizer

 

Optimizer or optimization algorithm has two types, first-order optimization algorithm, and second-order optimization algorithm.  An optimizer is used to minimize the cost function which thereby updates the values of weight and biases after every training section until the cost function reaches global optimum.

First order optimization either minimizes or maximizes the cost function using its gradient values with respect to the parameters.   This tends to inform us whether the function is decreasing or increasing at a given point.  

 

Second order optimization uses second order derivatives to do what the first order does.   This second derivative is called Hessian.   The second derivate is very costly to compute hence it is rarely used. The second order seeks to inform whether or not the first derivative is increasing or decreasing,  it provides information about quadratic surface which touches the curvature of the error surface.

 

2 Back propagation

This is also known as backward propagation of errors.  Errors are computed and distributed backward throughout the layers of the network.  It is used to train deep neural networks. This function helps fast resolution by the neural network of previously unsolvable problems. In today's world, it is the workhorse of learning in neural networks.  It helps in fast learning and much more it gives detailed insight into how weight and biases change the overall output. 

 

  
 

 

CHAPTER 4 

DEEP NEURAL NETWORKS: CLASSIFICATION

In classification, data are divided into two sets, one set designated as training set while the other set is designated as a testing set. According to Han et al, the two steps of classification task are model construction and model usage.  The model is built using a set of the trained dataset which in turn becomes a trained model and it is used to allocate as precisely as possible the hidden layer.  Training data is used to build and train the model; the other set called testing data is used for validating the training that means to check the accuracy of the training.

In classification, you deal with image classification.  It uses deep learning model called convolutional neural network – CNN. The recurrent neural network – RNN is not capable of dealing with images while CNN handles images in different ways from NN but still follows the same general concept. 

It is the default model for anything dealing with image recognition.  Using CNN reduces the number of parameters required for image compared to the one under RNN. 

1.  FEED FORWARD

Feed forward helps to solve binary classification problem, in ML classification is a type of supervised learning method where the task is divided into data sample and it is predefined by Decision Function; which when there are only two groups it is called Binary Classification.  The decision function is learned from a set of labeled samples which are called training data and that process of learning is what is known as Training.

1.  LINEAR FUNCTION

This is known as a linear classifier. It is also known as binary classification.  It is an example of pattern recognition. This is a function that makes decisions based on linear predictor combining with sets of weight and feature vector inputted.  This helps to establish a decision boundary which is either a line or a plane. It is also used in medical diagnosis to predict whether a patient has a disease or not.  This classifier corresponds to a decision boundary where positive examples are on one side while the negative examples are on the other side.

This function basically makes a decision or distinguishes between two categories or object.

This function is used in the financial world and in statistical computation, it can help comparison of variable costs and rates, helps with budgeting and making a useful prediction based on the past learning inputted into it.

2.  ACTIVATION FUNCTION

This function is used as a decision making port at the output of a neuron. This neuron learns from linear and non-linear decision-making boundaries. Learning function based on linear or non-linear decision boundaries is known as the activation function. It also helps to compute and normalizes the output neurons after passing through several layers of decision making which tends to be chaotic and very large due to the cascading effect of the multilayer decision making.

The function is monotonic while the output is not. It can be linear or non-linear.  Linear is rigid and does not help with the complex input data fed to Neural Network so its use is limited. The nonlinear is the mostly used activation functions.  It makes it easy to work with generalization and variable data and to differentiate between the outputs.

Examples of the nonlinear activation function are

 A sigmoid or logistic activation function

 Tahn or hyperbolic tangent Activation Function

 ReLU  (Rectified Linear Unit) Activation Function

 Leaky ReLU

 

3.  ERROR FUNCTION

An error function is also known as Gauss error function in Mathematics. It is a function that is found in statistics, probability and differential equations. The error function is closely connected with probability. It approximates the result that has a high probability. 

 

 

4.  OPTIMIZER

 

Optimizers are used to produce better and faster results by updating the model parameters such as weight and Bias values.  There are two types of optimization – stochastic gradient descent or Adam gradient descent. Optimization helps to minimize or maximize an objective function which is another name for error function.

 

Neural Network utilizes the following optimization types

Gradient descent

Variants of Gradient Descent

Stochastic gradient descent

Mini-batch gradient descent

 

 

2.            BACK PROPAGATION – BP

Classification model by training a multilayer feed forward neural network is called Back Propagation. It has only one input layer with some hidden layers and one output layer. Each layer is made up of perceptron which can be linked to other weighted connections. It is a faster means of training machine learning and gives detailed insights into how changing biases and weights can change the overall output of the network. 

Back Propagation we need to have two main assumptions which help to allow computing partial derivatives. BP utilizes four basic equations which are  

*   The equation for the error in the output layer
*   The equation for the error in terms of the next layer
*   The equation for the rate of change of the cost with respect to any bias in the network
*   The equation for the rate of change of the cost with respect to any weight in the network.

Applications of Back Propagation are as follows:

 Classification problems

 Function approximation

 Time series prediction

 

BP is also known as Back Propagation or errors.

  

CHAPTER 5

APPLICATION OF MACHINE LEARNING

In the previous chapters, we have defined or described what Machine Learning is all about. We will now go ahead and itemize the unique importance of Machine Learning and what you stand to gain from understanding Machine Learning and its operations.

Machine Learning has many applications in today’s digital world.  The use of Machine Learning span from agriculture to medicine to security, computer games, voice recognition to handwriting recognition.  Just name the area of life you have Machine learning application wildly in use.  

The following are not exclusive but some of the areas where Machine Learning is wildly in use today are:

1.  Social media services

From personal news feed to better advertisement targeting social media all are utilizing Machine Learning to achieve these tasks; some of the examples you will notice on social media accounts are people you may know, face recognition, similar pins which are a technique of obtaining useful information from videos and images. All these usages can be found on Facebook etc

2.  Fraud detection 

Email spam and malware filtering utilize Machine Learning to constantly update the system to achieve this. Multilayer Perceptron, C4.5 Decision Tree induction are some of the models that engage in spam filtering techniques. 

Another issue under fraud detection is online fraud.  Machine Learning makes cyberspace safe and secure.  Tracking monetary fraud is one of its functions. The example is Paypal that uses ML to fight money laundering.  It uses tools that compare millions of transactions taking place within it and differentiating the transactions into legitimate and illegitimate transactions between buyers and sellers.

3.  Search engines

For your information, Google and other search engines use Machine Learning to improve the search results.  The engine learns as searches are conducted. If after querying the client stayed on the page and open the search results, the machine learns that the result matches the search request but it didn't stay on the first page but keep scrolling down the machine learns that the result of the search does not match the query. Hence the machine learns to improve the search result. 

4.  Prediction 

ML is used in GPS navigation services.  The current location and the speed of the vehicle are being saved in the server traffic management. It helps in the estimation of where congestion is most likely based on input experiences stored in time past. 

In the online transportation network, ML is playing a major role in predicting the surge hours to riders demand.  Uber is one transportation system using ML in all the areas of its services.

 

5.  Agriculture & food.

ML has been used in the area of food processing, fermentation, filtration, drying, rheology, and psychrometry.  They are also of use in thermal processing and sensory science. 

Other areas where Machine Learning is used extensively include: 

6.  Analysis of user’s behavior 
7.  Telecommunication
8.  Structural health monitoring
9.  Software engineering
10.                   Insurance
11.                   Machine translation
12.                   Marketing
13.                   Medical diagnosis
14.                   Natural language processing and understanding
15.                   Online advertisement
16.                   Data mining
17.                   Computer networks
18.                   Brain-machine interface
19.                   DNA Sequence
20.                   Data quality
21.                   Economics 
22.                   Financial market analysis
23.                   Security
24.                   General computer games 

6.    
    

CHAPTER 5

TOOLS FOR MAKING MACHINE LEARNING

The following are the best Machine Learning tools and framework for developers.

Google ML kit 

This is a kit that allows developers to use Machine Learning to build features in Android and iOS no matter their level of expertise. This includes text recognition, face recognition, barcode scanning, image labeling, landmark recognition.

Open NN 

This is a programming library with tutorials although this tool is meant for experienced developers 

Apache Mahout

This is a tool for statisticians or data scientist to implement their own algorithm.  It is used for filtering and classification.

Haven On Demand

It provides high-level Machine Learning enterprise developers.  The usage of this model ranges from face detection, image classification, speech and object recognition, etc 

*   APACHE PREDICTION 1O
*   ACCORD .NET
*   AMAZON MACHINE LEARNING
*   AMAZON SAGE MAKER
*   AMAZON API
*   AMAZON'S DEEP SCALABLE SPARSE TENSOR NETWORK ENGINE – DSSTNE
*   AZURE MACHINE LEARNING 
*   AZURE MACHINE LEARNING MANAGEMENT

 

 

  

CONCLUSION

I hope you enjoyed and find a value for your needs.  Before you close out this book, if you find this book is helpful, have any comments or any suggestions, would you be so kind as to leave a review of this book?  With your generous comments, I will continue to develop the book better to the audience.  Thanks again for downloading and reading this book

 

If you find this book helpful, you can also access my other books through the links below.

Book Series #1 [Self-Learning Book: Learn the step-by-step secrets and simple methods of improving Self-Learning skills, inspired by a Korean high-school student](https://www.amazon.com/dp/B07Q857KHM)

Book Series #2 [Social Skills Secrets: Your step-by-step guide to rapidly and easily restart your social life -dedicated to discharged Korean soldiers-](https://www.amazon.com/dp/B07NX9C81R)