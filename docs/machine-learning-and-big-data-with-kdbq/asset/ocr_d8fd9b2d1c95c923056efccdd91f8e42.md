# Neural Networks 445

weights. For this, not only a huge data set is needed, but also proper training techniques and regularisations have to be well thought out.

For the case of one hidden layer, the question is what should be the dimension of the hidden layer, N. Since the dimension of the input (features) is $M$, we compare the dimension of the hidden layer relative to the size of the input. In the case of $N < M$, there is information suppression in the hidden layer as we aim to represent $M$-dimensional input through $N$-dimensional variables. Thus, it is recommended to use $N > M$ so that we can model nonlinear dependencies in the features.

There is, in fact, a reason to use $N < M$. Imagine the case when $Y = X$ and thus $L = M$. Such a setup allows to model the input variables and use the features to explain themselves. If we use $N < M$, the role of the hidden layer is to compress the input such that we can recover the input as much as possible. This is nothing but dimensional reduction, given we use the hidden layer to represent the input data. It can be shown that this is equivalent to the PCA. Then we can obtain PCA without the need to perform advanced matrix multiplications. The extreme case of $N=1$ means we want to compress the input into a single scalar factor.

# 22.2 IMPLEMENTATION OF NEURAL NETWORKS

In this section, we turn the theory of the previous paragraphs into functional code. We implement a function which can perform either classification or regression. It is further convenient to split the classification of the binary variable and general classification for $M > 2$.

First, we define some useful routines and functions, which will be wrapped into the function comprehending the neural network training. We aim to add a few extra features into learner functions in order to achieve various functionalities. All will be wrapped in a user-friendly interface with several options to choose from using a simple set of switches.

# 22.2.1 Multivariate Encoder

It is convenient to map the $M$-class classification problem, where the dependent variable can take $M$ discrete values into an $M$-dimensional variable where every individual component is a binary variable. Such a transformation is not the most economical; we waste at least one dimension. Models are conveniently simple ones, and the extra dimension of the dependent variable does not cause in most of the situations during learning.

To implement the multivariate classifier, we need to use the $M$-class discrete binary into $M$ binary variables. The function encoderMulti takes as an argument ($M$ discrete cases of the dependent variable) and returns a dictionary, which can be used as a function to create a list of binary variables:

```
.quantQn.encoderMulti:[arg]
  // arg -- list of classes to be encoded
  :arg!floatarg=$:arg;
```