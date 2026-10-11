
The probabilistic view of linear, logistic, and Poisson regression helps us reduce the classification and regression problem as a convex optimization problem that can be solved by iterative gradient-based optimization methods.

The interpretability of linear models makes them more useful for solving business problems. Testing of the statistical hypothesis for whether the coefficient is actually zero helps analyze the significance of the coefficients. Lower p-value indicates low chances of rejecting the hypothesis that the coefficient is zero, and hence, the corresponding feature must be an important feature.

## Further Reading

*   *Fundamentals of mathematical statistics*, *S C Gupta*, *V K Kapoor* Publisher: New Delhi: *Sultan Chand & Sons*.
*   *Chris Bishop*, *Pattern Recognition and Machine Learning*, [Chapter 3](#c03.xhtml) and [4](#c04.xhtml).
*   Unbiased Estimator: **[https://dawenl.github.io/files/mle_biased.pdf](https://dawenl.github.io/files/mle_biased.pdf)**.
*   Student’s t-distribution: **[https://en.wikipedia.org/wiki/Student%27s_t-distribution](https://en.wikipedia.org/wiki/Student%27s_t-distribution)**.
*   MLE for multivariate Gaussian: **[https://people.eecs.berkeley.edu/~jordan/courses/260-spring10/other-readings/chapter13.pdf](https://people.eecs.berkeley.edu/~jordan/courses/260-spring10/other-readings/chapter13.pdf)**.
*   **[https://web.njit.edu/~wguo/Math644_2012/Math644_Chapter%201_part4.pdf](https://web.njit.edu/~wguo/Math644_2012/Math644_Chapter%201_part4.pdf)**
*   *Applied Regression Analysis: A Research Tool by Rawlings*, *John O.*, *Pantula*, *Sastry G.*, *Dickey*, *David A*
*   Hessian of log likelihood of logistic regression is positive definite: **[https://www.cs.mcgill.ca/~dprecup/courses/ML/Lectures/ml-lecture05.pdf](https://www.cs.mcgill.ca/~dprecup/courses/ML/Lectures/ml-lecture05.pdf)**
*   **[https://www.statsmodels.org/stable/glm.html](https://www.statsmodels.org/stable/glm.html)**

# CHAPTER 6

# Neural Networks

In the previous chapter, we discussed that with a clever choice of basis functions and using linear models alone, we can solve a wide range of ML problems. So, it appears that linear basis function models constitute a general-purpose framework for solving ML problems. However, there are certain limitations:

1.  These non-linear basis functions need to be defined before training, that is, we must carefully perform feature engineering, which is a time-consuming, manual effort and demands sound knowledge of the domain.
2.  The number of basis functions grow rapidly, often exponentially with data dimension, that is, the curse of dimensionality (discussed in Overview of AI chapter) problem arises. Hence, we need to look for alternative models.

**Neural network** models are inspired by the way biological neural systems in human brain processes information. Neural networks solve these problems by choosing fixed but adaptive basis functions. These are parametrized non-linear basis functions whose parameters can be learned from the data during training of the neural network model. This is called the training of the network. Also, we can create a hierarchy of these parametrized basis functions. Each level in the hierarchy is called a layer of the network. A layer consists of fixed number of basis functions, which takes the output of the previous layer as input. The arrangement of these layers and connections among them in a particular form is called the *architecture* or *topology of the neural network*. We will see how the knowledge of the problem domain can be easily incorporated in the neural network architecture through choices in number of layers, units per layer, connections between layers, and so on. Now, the challenge of careful feature engineering is transformed to network architectural engineering. For training these networks, the most popular method is gradient descent – the back-propagation algorithm. However, for training deep networks, that is, networks with a large number of layers, simple gradient descent may not give us the best solution, so many modifications of that algorithm are suggested, which we will discuss in this chapter.

## Structure

In this chapter, we will cover the following topics:

*   **Single neuron**: An adaptive basis function
*   Multiple stacked layers or hierarchy of neurons
*   **Training hierarchy of neurons**: Back propagation algorithm
*   **Basic neural network architectures**: DNN, CNN, RNN, Transformers, Autoencoders

## Objectives

After studying this chapter, you will be familiar with the fundamental concepts behind deep neural networks and state-of-the-art AI models. These concepts will be applied in the subsequent chapters, where specific deep neural network models will be discussed for solving AI problems like speech recognition, handwriting recognition, language translation, image classification and generation.

## Artificial neuron: An adaptive basis function

The fundamental building block of a neural network is called a *neuron*. This term is borrowed from biology. where a neuron is a nerve cell that is the basic building block of the nervous system. A single neuron may be connected to many other neurons such that the information transmitted is consumed by these connected neurons. The biological neuron consists of three main parts: *dendrites* (the receivers), the cell body, and *axon* (the transmitter). Neurons communicate with one another at junctions called *synapses*, where one neuron sends a message to a target neuron, that is, another neuron cell. These are chemical messengers or ions. An artificial neuron closely mimics this structure comprising of a set of dendrite-like connections, each taking an input and multiplying it by a (synaptic) weight (weight indicates strength of synaptic connection) associated with that edge. These weights are learnt in the learning phase. These weighted inputs are summed up after going through a *summation unit*. The result is subsequently fed to an *activation unit* whose output is then transmitted to the outside via an axon-like projection. The structure of a single biological and artificial neuron is depicted in *[Figure 6.1](#c06.xhtml#fig6_1)*:

![](images/figure-6.1.jpg)

**Figure 6.1:** *Biological neuron and artificial neuron*

Given an input vector `x`, the computation in an artificial neuron can be written in the form of a basis function `y = f(w^T x + b)`, as follows:

```
y = f(w^T x + b)
```

Here, `f` is a non-linear activation function. *[Table 6.1](#c06.xhtml#tab6_1)* shows some common activation functions. Also refer to the following figure:

![](images/figure-6.2.jpg.jpg)

**Figure 6.2:** *Different basis functions created by various activations: first row shows various sigmoid activations, second row shows various tanh activations, and the last row shows relu activations*

![](images/6.1.jpg)

**Table 6.1:** *Activation functions*

For a fixed set of weights `w`, this basis function `y = f(w^T x + b)` is a fixed function, like the one we have in linear basis function model, studied in the previous chapter. Now, let’s see how we can get a family of basis functions by varying these weights. For example, we take a single variable input `x` and make an adaptive basis function with two weights `w` and `b`. *[Figure 6.2](#c06.xhtml#fig6_2)* shows how setting the weight parameters randomly gives each basis function a distinct shape.

## Feed Forward neural network
