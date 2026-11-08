
# Deep Learning

## Introduction and Motivation

In recent years, so-called “deep learning” approaches to machine learning (ML) have had a major impact on speech recognition, computer vision, natural language processing, and beyond. The term “deep learning” is essentially a rebranding of neural networks, with an emphasis on architectures that have many layers, in contrast to “shallow” architectures such as the perceptron and support vector machines. A critical ingredient is the use of much larger quantities of data than has heretofore been possible. Recent successes have arisen in settings involving *high-capacity* models—ones with many parameters. These flexible models exploit information buried in massive data sets more effectively than traditional ML techniques using hand-engineered features.

## Chapter Overview

This chapter begins by discussing the notion of deep learning and why it is effective. We then introduce key innovations, along with some specific results and experiments. We present the main approaches associated with deep learning, and we also discuss common practical issues and aspects of training contemporary deep network architectures. We focus on the fundamentals here, and we describe more recent and advanced deep learning technologies in the next chapter. Before reading this chapter, we recommend first reading [Section 4.6](#Ch004_91-164_B9780443158889000054_a.xhtml#s0095), Linear Models, and [Section 9.2](#Ch010_347-389_B9780443158889000108.xhtml#s0050), Extending Linear Models, which lay the foundations for the present material.

## Prediction Approaches

There are three approaches to making predictions from data based on ML:

* *Classical ML* techniques, which make predictions directly from a set of features that have been prespecified by the user
* *Representation learning* techniques, which transform features into some intermediate representation prior to mapping them to final predictions
* *Deep learning* techniques, a form of representation learning that uses multiple transformation steps to create very complex features.

## Representation Learning and Deep Architectures

We have seen many ways of transforming features into an intermediate representation before applying ML. A classic example is principal component analysis followed by nearest-neighbor learning. Fisher’s linear discriminant analysis is another example of representation learning; a discriminative objective is used to adapt the learned representation using labeled data. The result can be used to make classifications directly or to serve as input to a more flexible, nonlinear classifier.

In contrast, a simple three-layer perceptron learns a representation by adapting the hidden layer to the task of interest, jointly training it and the output layer so that the hidden-layer parameters coadapt to the output-layer parameters. Making a network “deep” by adding further hidden layers subjects features to a sequence of transformations. Each layer’s transformation is a form of inference, and one can imagine how complex inferences might be more easily modeled as a sequence of computational steps. Deep *recurrent* neural networks, which we will also discuss, include feedback loops, and their depth is related to the complexity of the underlying algorithm being learned, as opposed to an iterative procedure of feature aggregation and abstraction.

Deep multilayer perceptrons, deep convolutional neural networks (CNNs), and recurrent neural networks are central to the current wave of interest in deep learning. However, other methods can also be characterized as instances of deep learning, as we will see later. Most deep learning methods use multilayer perceptrons as building blocks.

## Theoretical and Empirical Motivations

This chapter highlights some notable empirical successes where deep learning methods have out-performed state-of-the-art alternatives. The main reason for using deep learning is its empirical effectiveness compared to alternative approaches. But there are other, more theoretical, motivations. There are analogies at a conceptual level between neural networks and circuit analysis that lead to theoretical results in complexity theory. Some neural networks implement soft variants of logical functions, and under certain parameter settings they can behave exactly like logic gates, as we saw in [Section 9.2](#Ch010_347-389_B9780443158889000108.xhtml#s0050). Functions that can be compactly represented by multilevel networks may require far more elements when expressed as shallower architectures.

## Training and Regularization

Deep learning formulates the underlying problem as a network architecture whose output layer defines a loss function needed for learning. The output units can be formulated as probabilistic predictions, and if these predictions are parameterized one can simply define the loss to be the negative log-likelihood under the model—the negative of the logarithm of the probability of the data based on the model’s current estimated parameters ([Section 13.1](#Ch014_485-514_B9780443158889000145.xhtml#s0010)). Parameters are typically regularized by adding regularization terms to the loss function. An approach from Bayesian statistics, placing priors on the parameters, is often equivalent to using such regularization terms ([Section 13.1](#Ch014_485-514_B9780443158889000145.xhtml#s0010)). We also discuss some newer approaches to regularization.

Deep learning methods are frequently based upon networks for which the backpropagation algorithm serves to compute the gradients required for learning (see [Section 9.2](#Ch010_347-389_B9780443158889000108.xhtml#s0050) for an elementary treatment and [Appendix D.1](#FigD1_687-703_B9780443158889000248.xhtml#s0010) for the complete derivation). A variation of stochastic gradient descent (SGD) is frequently used that computes gradients and updates model parameters from small “mini-batches” of examples—subsets of the training set. We will also discuss more sophisticated extensions to stochastic gradient descent that have proved effective, such as SGD with momentum and Adam.

## Applications and Impact

Deep learning has sparked a renaissance of neural network research and applications. Many high-profile media (e.g., *The New York Times*) have documented striking successes of deep learning techniques on key benchmark problems. Starting around 2012, impressive results were achieved on long-standing problems in speech recognition and computer vision and in competitive challenges such as the ImageNet *Large Scale Visual Recognition Challenge* and the *Labeled Faces in the Wild* evaluation. In speech processing, computer vision, and even in the neural networks community itself the impact was substantial. Now, deep neural networks are entering the public consciousness and even our daily lives, in a very visible way due to systems such as OpenAI’s ChatGPT chatbot and AI art platforms such as Dall-E, Midjourney, and Stable Diffusion. Deep learning enabled the success of Google DeepMind’s AlphaGo system, which defeated the world champion at the game of Go, and is crucial for autonomous vehicles, better known as self-driving cars. For more information, see the *Further Reading* section at the end of the chapter.

## Computational Infrastructure

The easy availability of high-speed computation in the form of graphics processing units has been critical to the success of deep learning techniques. When formulated in matrix-vector form, computation can be accelerated using optimized graphics libraries and hardware. As network models become more complex, some quantities can only be represented using multidimensional arrays of numbers—sometimes referred to as tensors, a generalization of matrices that permit an arbitrary number of indices. Software for deep learning supporting tensors is invaluable for accelerating the creation of complex network structures and making it easier to learn them. We introduce some software packages at the end of this chapter.
