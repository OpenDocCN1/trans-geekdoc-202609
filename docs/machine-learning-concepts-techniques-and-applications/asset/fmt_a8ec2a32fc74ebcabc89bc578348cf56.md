
## 2.4.1 The Process of Design

### Choose the Training Experience

The choice of training experience depends on the learning paradigm that is chosen, such as supervised learning, unsupervised learning, reinforcement learning, and so on. In this chapter we will be considering the context of supervised learning. These learning paradigms will be discussed in detail in [Chapter 4](#ch4.xhtml). In addition, this choice also depends on the availability of data and whether we are considering online or offline examples.

In addition, we need to know training experience will provide *direct* or *indirect* feedback. In the case of direct feedback, the system learns from examples of individual checkerboard states and the correct move for each. On the other hand, in the case of indirect feedback the move sequences and final outcomes of various games played are made available and credit assignment must be calculated where the value of early states must be inferred from the outcome.

We also need to understand the degree to which the learner controls the sequence of training examples. In some cases, the teacher selects appropriate informative boards and gives the correct move. In other cases the learner requests the teacher to provide correct moves for some board states which they find confusing. Finally, the learner controls the board states as well as the training classifications.

It is also important that the training experience represents the distribution of examples over which the final system performance `P` will be measured. In the case of training the checkers program, if we consider only experiences played against itself, then crucial board states that are likely to be played by the human checkers champion will never be encountered. Most machine learning systems assume that the distribution of training examples is identical to the distribution of test examples.

### Choose the Target Function

The choice of the target function is possibly one of the most important aspects of the design. The model we choose must be as simple as possible. This is in keeping with the principle of Occam’s razor, which states that we need to prefer a simpler hypothesis that best fits the data. However, we need to ensure that all the prior information is considered and integrated, and we learn only the aspect that is the goal of the learning task.

### Choose a Representation

The representation of the input data should integrate all the relevant features only and not include what is not affecting the learning. If too many features are chosen, then we will encounter the curse of dimensionality, which we will discuss later. The other aspect is the representation of the target function and model to be used. There are different types of function such as classification, regression, density estimation, novelty detection, and visualization, which to a large extent depends on how we look at the machine learning task. Then we need to decide on the model that is to be used, whether symbolic, such as logical rules, decision trees, and so on, or sub-symbolic, such as neural networks or a number of other models which we will discuss in detail in other chapters.

### Choose the Parameter Fitting Algorithm

This is the step where we estimate the parameters to optimize some error or objective on the given data. There are many such parameter estimation techniques such as linear/quadratic optimization and gradient descent greedy algorithm, which also will be discussed later.

### Evaluation

Evaluation needs to determine whether the system behaves well in practice and whether the system works for data that is not used for training; that is, whether generalization occurs. In other words, the system finds the underlying regularity and does not work only for the given data.

### 2.4.2 Illustrative Examples of the Process of Design

Before we proceed, let us understand the meaning of learning in this context. We will explain learning using the examples of handwriting recognition ([Nkengsa, 2018](#ch2.xhtml#ref2_6)) and checkers learning problems.

#### 2.4.2.1 Recognition of Handwritten Characters

We can define the handwriting recognition problem as:

*   **Task `T`:** Recognizing handwritten characters
*   **Performance measure `P`:** Percentage of characters correctly classified
*   **Training experience `E`:** A database of handwritten characters with given correct labels

This example will now be used to explain the design steps. We use handwriting character recognition ([Figure 2.12](#ch2.xhtml#fig2_12)) as an illustrative example to explain the design issues and approaches.

![Figure 2.12 Set of handwritten characters.](images/fig2_12_B.jpg)

[Figure 2.12 Set of handwritten characters.](#ch2.xhtml#R_fig2_12)

We explain learning to perform a task from experience. Therefore, let us understand the meaning of the task. The task can often be expressed through a mathematical function. In this case input can be `x`, output `y`, and `w` the parameters that are learned. In case of classification, output `y` will be discrete, such as class membership, posterior probability, and so on. For regression, `y` will be continuous. For the character recognition, the output `y` will be as shown in [Figure 2.13](#ch2.xhtml#fig2_13).

![Figure 2.13 Character recognition task.](images/fig2_13_B.jpg)

[Figure 2.13 Character recognition task.](#ch2.xhtml#R_fig2_13)

The following are the steps in the design process for character recognition.

##### Step 0

Let us treat the learning system as a black box ([Figure 2.14](#ch2.xhtml#fig2_14)).

![Figure 2.14 Learning system as a black box.](images/fig2_14_B.jpg)

[Figure 2.14 Learning system as a black box.](#ch2.xhtml#R_fig2_14)

##### Step 1

Next we collect training examples (experience). Without examples, our system will not learn as we are learning from examples ([Figure 2.15](#ch2.xhtml#fig2_15)).

![Figure 2.15 Collection of training data.](images/fig2_15_B.jpg)

[Figure 2.15 Collection of training data.](#ch2.xhtml#R_fig2_15)

##### Step 2: Representing Experience

The next step is to choose a scheme for representing the experience/examples. In our example the sensor input can represented by an `n`-dimensional vector, called the feature vector, `X = (x[1], x[2], x[3], …, x[n])`. We can assume a 64-dimensional vector to represent the 8 × 8 matrix of pixels ([Figure 2.16](#ch2.xhtml#fig2_16)).

![Figure 2.16 Representation of data.](images/fig2_16_B.jpg)

[Figure 2.16 Representation of data.](#ch2.xhtml#R_fig2_16)

In order to represent the experience, we need to know what `X` is. Therefore, we need a corresponding vector `D`, which will record our knowledge (experience) about `X`. The experience `E` is a pair of vectors `E = (X, D)`. Now the question is how to represent `D`. Assuming our system is to recognise 10 digits only, then `D` can be a 10-dimensional binary vector, with each dimension corresponding to one of the digits ([Figure 2.17](#ch2.xhtml#fig2_17)).

![Figure 2.17 10-dimensional binary vector.](images/fig2_17_B.jpg)

[Figure 2.17 10-dimensional binary vector.](#ch2.xhtml#R_fig2_17)

##### Step 3: Choosing a Representation for the Black Box

The next step is the choice of a representation for the black box. Here we need to choose a function `F` to approximate the black box, and for a given `X`, the value of `F` would give the classification of `X` ([Figure 2.18](#ch2.xhtml#fig2_18)).

![Figure 2.18 Choosing function F.](images/fig2_18_B.jpg)

[Figure 2.18 Choosing function `F`.](#ch2.xhtml#R_fig2_18)

##### Step 4: Learning/Adjusting the Weights
