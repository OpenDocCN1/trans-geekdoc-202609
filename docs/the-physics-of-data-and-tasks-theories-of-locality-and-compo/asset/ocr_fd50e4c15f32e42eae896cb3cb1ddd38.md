# INTRODUCTION

This chapter establishes the vocabulary and the open questions that will shape the remainder of the thesis. It first sketches the basics of machine learning and neural networks. It explains why the striking empirical success of these networks is unexpected, reviews the main present theories, and pinpoints remaining gaps. The chapter concludes with a brief overview of the thesis's contributions.

# 1.1 INTRODUCTION TO DEEP LEARNING

# 1.1.1 Supervised learning with deep neural networks

The most basic setting in machine learning is supervised learning, where a model learns a mapping from inputs to labels using examples. For instance, in the task of classifying animal species from a picture, the model is trained on examples of images with their correct labels, with the goal of accurately classifying new, unseen images.

Formally, each input $x_i \in \mathcal{X}$ is paired with a label $y_i \in \mathcal{Y}$. The input space $\mathcal{X}$ is often high-dimensional (e.g., $\mathcal{X} = \mathbb{R}^d$ where $d \gg 1$ represents the number of pixels in an image). The output space can represent real values $\mathcal{Y} \in \mathbb{R}$ (for regression) or class labels $\mathcal{Y} = \{1, \dots, C\}$ (for classification, such as the animal species above). The learner is given $P$ examples $(x_i, y_i)_{i \in P}$, the training set, where $(x_i, y_i)$ are assumed to be drawn i.i.d. from a joint distribution $p$ over $\mathcal{X} \times \mathcal{Y}$.

In deep learning, the class of models used to learn this mapping is represented by deep neural networks. In their most basic form, fully connected neural networks (FCNs), these models consist of successive layers of linear transformations interspersed with nonlinearities. A network with $L$ hidden transforms an input $x$ into an output $f(x, \theta)$ through the following equations:

```
$z^{(1)} = \sigma^{(1)}(w_h^{(1)T}x + b^{(1)}) \text{ for } h \in [H]$$
$$z^{(l)} = \sigma^{(l)}(w_h^{(l)T}z^{(l-1)} + b^{(l)}) \text{ for } h \in [H], l \in [2, \dots, L]$$
$$
f(x, \theta) = z^{(L+1)},\$$ $
```

> Fully connected networks are the simplest neural architectures.

$	heta$ denotes a vector with all parameters (i.e., weights $w_h^{(l)}$ and biases $b^{(l)}$) at layers $l \in [L + 1]$ that are learned from data. The functions $\sigma^{(l)}$ are scalar activation functions, applied element-wise,