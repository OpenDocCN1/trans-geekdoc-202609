
Historically, threshold functions were used as activation functions, the effect of which is that the units are activated abruptly, i.e. either they are not activated, or they are activated suddenly. The response can only be black or white, so these functions are suitable for classification and recognition tasks. Over time, activation functions were introduced that allow neurons to gradually activate as the activity level of their inputs increases, rather than their state being only on-off. Specifically, the function proposed is the sigmoidal or logistic function ![image](d2d_images/image079.png), which produces a smoothed sigmoidal response.

If in the expression of ![image](d2d_images/image584.png) we consider ![image](d2d_images/image502.png), we find that ![image](d2d_images/image479.png) corresponds to the binary logit model.

In general, the functions `F` and `G` can take any form in the expression of ![image](d2d_images/image215.png). However, it is common practice to consider either that the activation function of the output and intermediate neurons is identical, ![image](d2d_images/image350.png), and that it corresponds to the sigmoidal function, or that ![image](d2d_images/image315.png) i.e. that it is the identity function and that `G(a)` corresponds to the logistic or sigmoidal function, which is equivalent to considering that there is only an activation function (the sigmoidal one) in the hidden units. This last hypothesis is the one we assume, from now on, in our approach, because in addition to greatly simplifying the notation, it is the one most frequently adopted in the construction of artificial neural networks. We should also point out that we use the sigmoidal function, which is the most commonly used, since its properties allow us to employ learning algorithms such as error backpropagation, which we use in our work. Formally, it is also possible to show that an ANN with a hidden layer and sigmoidal activation function is able to approximate any measurable function.

Assuming, as we have indicated, that there is only an activation function in the intermediate neurons and that this corresponds to the sigmoidal one, we have:

![image](d2d_images/image400.png)

Another possibility, of great utility in econometric applications, is to consider that in the network we represent, a forward-fed artificial neural network with `r` inputs, a single hidden layer, composed of `q` processing elements, and an output unit, there are also direct connections between the input and output layers. In this case, the output of the network is obtained by the following expression:

![image](d2d_images/image045.png) where `α` is a vector of dimension `r×1` representing the weights of the direct connections between the input and output layers. Logically, now `W`, which collects all the weights of the network, is composed of ![image](d2d_images/image204.png).

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |
![image](d2d_images/chapter_title_above.png)

# 6.2 NEURAL NETWORKS AND REGRESSION MODEL FITTING

![image](d2d_images/chapter_title_below.png)

The output function ![image](d2d_images/image215.png) can be broken down into two parts. The first of these, which corresponds to the first two terms, represents a linear model, so that, if we take as input variables `r` lags of the variable `x`, it becomes a linear regression on the lagged input variables, which act as explanatory variables, and a constant ( ![image](d2d_images/image474.png) ).

This first part, as is logical, captures the linear dependencies between the input patterns and the outputs of the network. The second part, which is the third term of the previous formulation, captures, if they exist, the non-linear dependencies between the input variables and the output of the network, given that the function used is non-linear. Concretely, this third term is a composition, weighted with the synaptic weights of the intermediate neurons to the output neurons ![image](d2d_images/image282.png) of sigmoidal functions of the network inputs, the latter weighted by the connection strength of the input units to the intermediate ones. This model can be considered an extension of the well-known and frequently used linear models, since it is composed of a linear model augmented with non-linear terms.

As we can see, the network that we describe by means of the expression of ![image](d2d_images/image577.png), enjoys such a degree of flexibility that it allows all types of functions to be adjusted, which is why artificial neural networks are characterised as "universal approximators". In other words, a neural network is capable of learning any function. The artificial neural network model should be considered as one of a set of non-parametric models to which the results of statistical inference can be applied. Thus, the range of opportunities is not limited to artificial neural networks, but, on the contrary, multiple alternatives such as classification and regression trees (CART) and multivariate adaptive regression splines (Friedman, 1991).

| ![image](d2d_images/chapter_title_corner_decoration_left.png) ||  || ![image](d2d_images/chapter_title_corner_decoration_right.png) |
| --- | --- | --- |
![image](d2d_images/chapter_title_above.png)

# 6.3 LEARNING IN NEURAL NETWORKS

![image](d2d_images/chapter_title_below.png)

After designing an artificial neural network, what we want to achieve with it is that, for certain inputs, or example patterns that we supply to the network, it is capable of generating a desired output. To achieve this, in addition to the topology of the network (understood as the structure of the network) being appropriate, it is required that the network learns to provide correct solutions, i.e., it is necessary to subject the network to a learning or training process. Learning can be understood as a trial and error procedure that allows the statistical estimation of the parameters of the neural network model used.

Three basic types of learning are generally considered to give rise to different types of neural networks. When the trainer provides the network with the desired output, the learning is said to be supervised. Otherwise, it is unsupervised learning. Finally, an intermediate type of learning is reinforcement or hybrid learning, in which the trainer only provides the network with an indication of whether the response to a given input is good or bad.
