
## 20.4 How to Develop and Use a Bayesian Network

Designing a Bayesian Network requires defining at least three things: Random Variables. What are the random variables in the problem? Conditional Relationships. What are the conditional relationships between the variables? Probability Distributions. What are the probability distributions for each variable? It may be possible for an expert in the problem domain to specify some or all of these aspects in the design of the model. In many cases, the architecture or topology of the graphical model can be specified by an expert, but the probability distributions must be estimated from data from the domain.

Both the probability distributions and the graph structure itself can be estimated from data, although it can be a challenging process. As such, it is common to use learning algorithms for this purpose; for example, assuming a Gaussian distribution for continuous random variables and using gradient ascent for estimating the distribution parameters. Once a Bayesian Network has been prepared for a domain, it can be used for reasoning, e.g. making decisions. Reasoning is achieved via inference with the model for a given situation. For example, the outcome for some events is known and plugged into the random variables. The model can be used to estimate the probability of causes for the events or possible further outcomes.

Reasoning (inference) is then performed by introducing evidence that sets variables in known states, and subsequently computing probabilities of interest, conditioned on this evidence.

> — Page 13, *Bayesian Reasoning and Machine Learning*, 2012.

Practical examples of using Bayesian Networks in practice include medicine (symptoms and diseases), bioinformatics (traits and genes), and speech recognition (utterances and time).

## 20.5 Example of a Bayesian Network

We can make Bayesian Networks concrete with a small example. Consider a problem with three random variables: A, B, and C. A is dependent upon B, and C is dependent upon B. We can state the conditional dependencies as follows:

- A is conditionally dependent upon B, e.g. P(A|B)
- C is conditionally dependent upon B, e.g. P(C|B)

We know that C and A have no effect on each other. We can also state the conditional independencies as follows:

- A is conditionally independent from C: P(A|B,C)
- C is conditionally independent from A: P(C|B,A)

Notice that the conditional dependence is stated in the presence of the conditional independence. That is, A is conditionally independent of C, or A is conditionally dependent upon B in the presence of C. We might also state the conditional independence of A given C as the conditional dependence of $A$ given $B$, as $A$ is unaffected by $C$ and can be calculated from $A$ given $B$ alone.

$$P(A|C,B)=P(A|B)$$

We can see that $B$ is unaffected by $A$ and $C$ and has no dependencies or parents; we can simply state the conditional independence of $B$ from $A$ and $C$ as $P(B, P(A|B), P(C|B))$ or $P(B)$. We can also write the joint probability of $A$ and $C$ given $B$ or conditioned on $B$ as the product of two conditional probabilities, for example:

$$P(A,C|B)=P(A|B)\times P(C|B)$$

The model summarizes the joint probability of $P(A,B,C)$, calculated as:

$$P(A,B,C)=P(A|B)\times P(C|B)\times P(B)$$

We can draw the graph as follows:

![](img/6ef657cfead7281442f755181c4f6e50_201_0.png)

Figure 20.1: Example of a Simple Bayesian Network.

Notice that the random variables are each assigned a node, and the conditional probabilities are stated as directed connections between the nodes. Also notice that it is not possible to navigate the graph in a cycle, e.g. no loops are possible when navigating from node to node via the edges. Also notice that the graph is useful even at this point where we don’t know the probability distributions for the variables. You might want to extend this example by using contrived probabilities for discrete events for each random variable and practice some simple inference for different scenarios.

## 20.6 Bayesian Networks in Python

Bayesian Networks can be developed and used for inference in Python. A popular library for this is called PyMC and provides a range of tools for Bayesian modeling, including graphical models like Bayesian Networks. The most recent version of the library is called PyMC3, named for Python version 3, and was developed on top of the Theano mathematical computation library that offers fast automatic differentiation.

PyMC3 is a new open source probabilistic programming framework written in Python that uses Theano to compute gradients via automatic differentiation as well as compile probabilistic programs on-the-fly to C for increased speed.

> — *Probabilistic programming in Python using PyMC3*, 2016.

More generally, the use of probabilistic graphical models in computer software used for inference is referred to as *probabilistic programming*.

This type of programming is called probabilistic programming, [...] it is probabilistic in the sense that we create probability models using programming variables as the model’s components. Model components are first-class primitives within the PyMC framework.

> — *Bayesian Methods for Hackers: Probabilistic Programming and Bayesian Inference*, 2015.

## 20.7 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

### 20.7.1 Books

- *Bayesian Reasoning and Machine Learning*, 2012.
  https://amzn.to/2YoHbgV
- *Bayesian Methods for Hackers: Probabilistic Programming and Bayesian Inference*, 2015.
  https://amzn.to/2Khk3bq

### 20.7.2 Book Chapters

- Chapter 6: Bayesian Learning, *Machine Learning*, 1997.
  https://amzn.to/2jWd51p
- Chapter 8: Graphical Models, *Pattern Recognition and Machine Learning*, 2006.
  https://amzn.to/2JwHE7I
- Chapter 10: Directed graphical models (Bayes nets), *Machine Learning: A Probabilistic Perspective*, 2012.
  https://amzn.to/2xKSTCP
- Chapter 14: Probabilistic Reasoning, *Artificial Intelligence: A Modern Approach*, 3rd edition, 2009.
  https://amzn.to/2Y7yCp0

### 20.7.3 Papers

- *Probabilistic programming in Python using PyMC3*, 2016.
  https://peerj.com/articles/cs-55/

### 20.7.4 Code

- PyMC3, Probabilistic Programming in Python.
  https://docs.pymc.io/
- Variational Inference: Bayesian Neural Networks
  https://docs.pymc.io/notebooks/bayesian_neural_network_advi.html

### 20.7.5 Articles

- Graphical model, Wikipedia.
  https://en.wikipedia.org/wiki/Graphical_model
- Hidden Markov model, Wikipedia.
  https://en.wikipedia.org/wiki/Hidden_Markov_model
- Bayesian network, Wikipedia.
  https://en.wikipedia.org/wiki/Bayesian_network
- Conditional independence, Wikipedia.
  https://en.wikipedia.org/wiki/Conditional_independence

## 20.8 Summary

In this tutorial, you discovered a gentle introduction to Bayesian Networks. Specifically, you learned:

- Bayesian networks are a type of probabilistic graphical model comprised of nodes and directed edges.
- Bayesian network models capture both conditionally dependent and conditionally independent relationships between random variables.
- Models can be prepared by experts or learned from data, then used for inference to estimate the probabilities for causal or subsequent events.

### 20.8.1 Next

This was the final tutorial in this Part. In the next Part, you will discover important probabilistic tools from the field of information theory.

## Part VII: Information Theory

## Chapter 21: Information Entropy

Information theory is a subfield of mathematics concerned with transmitting data across a noisy channel. A cornerstone of information theory is the idea of quantifying how much information there is in a message. More generally, this can be used to quantify the information in an event and a random variable, called entropy, and is calculated using probability. Calculating information and entropy is a useful tool in machine learning and is used as the basis for techniques such as feature selection, building decision trees, and, more generally, fitting classification models. As such, a machine learning practitioner requires a strong understanding and intuition for information and entropy. In this tutorial, you will discover a gentle introduction to information entropy. After reading this tutorial, you will know:

- Information theory is concerned with data compression and transmission and builds upon probability and supports machine learning.
- Information provides a way to quantify the amount of surprise for an event measured in bits.
- Entropy provides a measure of the average amount of information needed to represent an event drawn from a probability distribution for a random variable.

Let’s get started.

### 21.1 Tutorial Overview

This tutorial is divided into three parts; they are:

- 1. What Is Information Theory?
- 2. Calculate the Information for an Event
- 3. Calculate the Information for a Random Variable
