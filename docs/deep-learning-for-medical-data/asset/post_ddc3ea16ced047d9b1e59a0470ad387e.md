
## 6 | INTRODUCTION

**Research Question 3:** Do medical imaging deep learning models benefit from contrastive predictive coding for self-supervised representation learning?

There is no shortage of medical imaging data, as hospitals around the world capture vast amounts of data on a daily basis. These images are readily available in centralized storage systems called PACS, and modern hospitals have systems in place to process this data in an automated fashion. The challenge in medical data comes from collecting expert labels. This is an expensive process that requires input multiple 'gold standard' experts to reach consensus. Leveraging unlabeled data is thus a promising approach for the field, as the ratio of labeled to unlabeled data is especially lopsided. In the second part of the thesis, we explore a new technique for unsupervised representation learning, enabling the bulk of the deep learning model to be trained without downstream layers in the hopes of increasing label efficiency.

**Research Question 4:** Can we optimize deep learning models effectively without end-to-end backpropagation? Continuing on the topic of unlabeled data, we explore if unsupervised training can be done in a greedy fashion: training individual layers of a neural network without backpropagating through the full network. This form of training is of interest to medical image neural networks in particular. First, unsupervised training eases the labeling burden from medical experts. Second, amount of memory required to train one layer at a time is orders of magnitudes smaller than training a full network. Finally, models can be trained on small crops from large medical imagery, which is especially impactful when working with 3D or 4D data.

**Research Question 5:** Can latent variable quantification yield improved confidence scores? Deep decision making benefits from an accurate representation of the confidence in a certain prediction. As deep learning is prone to overconfidence, studying methods that better capture uncertainty is highly relevant for medical imaging. In the third part, we study the framework of variational inference in deep latent variable models, a form of probabilistic deep learning models. We test an hypothesised assumption that improved flexibility of the variational posterior will lead to better performance, by introducing a highly flexible mean-field posterior that relies on quantizing the latent space.

Before we address these research questions in the main parts of this thesis, we will briefly introduce notation and the core principles of deep learning in the following section. Finally, we will conclude and discuss directions of future work in chapter 7.

## 1.3 NOTATION

Throughout this work we follow the notation as presented in the table below.

| Examples | Description |
| --- | --- |
| a, b, c | Random scalar |
| x, y, z | Random vector |
| x_i | Elements of random vector |
| X, W, Y | Random matrices |
| X_{i,j} | Elements of random matrices |
| p(·) | Distributions (probability density functions) |
| q(·) | Often used for variational approximative distributions |

## 1.4 BASICS OF DEEP LEARNING

Deep Learning refers to the modern practice of machine learning using stacked function approximators and the optimization of those using stochastic gradient descent. The term captures both the techniques as well as a broad spectrum of best practices surrounding the design, optimization and approach of machine learning. In the following parts we will briefly discuss the basic principles and practice of deep learning, which the expert reader can safely skip. The relevant background specific to each research question will be discussed in the following chapters.

### 1.4.1 Data

We start with considering the data. Ideally, we have gathered a large dataset of independently sampled, identically distributed (i.i.d) data points x. We might have an accompanying label y for each datapoint that we aim to predict. This results in a dataset X: {(x_i, y_i | 0 ≤ i ≤ n)} of n datapoints. We divvy this dataset up in three parts: one to optimize our model on $D_{train}$, one to track and tune the performance during training $\mathcal{D}_{valid}$ and finally a set to estimate the expected performance on unseen data $\mathcal{D}_{test}$. This separation ensures our model generalizes to the problem, instead of overfitting to the training data.

### 1.4.2 Model

A deep learning model is simply a parameterized mathematical function that accepts samples in the data space and transforms it into the label space: $f : \mathbb{R}_x \rightarrow \mathbb{R}_y$. Typically, this function is of a form of alternating linear transformations followed by scalar non-linearities (or activation functions): $f_\theta(\chi) = W^3l(W^2h(W^1x))$. This function is what is referred to as the neural network, as it is loosely imposed by the layers of connected neurons found in the brain. The parameters or weights $\theta : \{W^l\}$ are the knobs that we tune to find the optimal model.

### 1.4.3 Optimization

We optimizing the parameters of $f$ by alternately estimating the error that the model makes on the training data, and making small changes to the parameters to reduce this error using the derivative. This is the essence of Gradient Descent, and works as follows. We define a scalar error function (often called the $loss$) on the network $\mathcal{L} : \{X, Y, W\} \rightarrow \mathbb{R}$. To improve the model, we compute the derivative $\nabla L = \frac{d}{dW_{i,j}^l}\mathcal{L}$ for each parameter. We then make a small step in the direction of steepest descent by updating each parameter:

```
$W_{i,j}^l = W_{i,j}^l - \eta\nabla_{W_{i,j}^l}\mathcal{L}$
```

where the step-size, or learning rate, is $\eta$. We apply this algorithm by drawing small random subsets from the training data, called mini-batches. This has been shown to improve the generalization and reduces the computational cost. We refer to this stepwise optimization as Stochastic Gradient Descent (SGD), in contrast to Gradient Descent, which uses the full training datasets to compute the true gradient.

## 1.5 PROBABILISTIC INFERENCE AND DEEP LEARNING

Learning rate

The learning rate $\eta$ is a hyperparameter that determines the size of the update to the weights at each step of the optimization process. If the learning rate is too large, the optimization algorithm overshoots the minimum and leading to instability or diverge. On the other hand, if the learning rate is too small, the optimization algorithm may take a long time to converge. Therefore, choosing an appropriate learning rate is crucial for successful training.

There are few different strategies for choosing the learning rate, including fixed learning rates, learning rate schedules, and adaptive learning rates. Fixed learning rates involve setting a constant learning rate for the entire training process. Learning rate schedules involve gradually decreasing the learning rate over time. Adaptive learning rates involve dynamically adjusting the learning rate during training based on the progress of the optimization process.

There are also various techniques for monitoring the learning rate during training, such as learning rate schedules that reduce the learning rate if the validation loss stops, or methods that monitor the gradient to detect when the learning rate is too high or too low.

Overall, choosing an appropriate learning rate requires some experimentation and tuning, and there is no one-size-fits-all solution.

In high-risk domains, prediction errors come at high costs. Luckily such domains often provide a fail-safe: self-driving cars perform an emergency stop, doctors run another diagnostic test, and industrial processes are temporal. For deep learning models, this can be achieved by rejecting datapoints with a confidence score below a predetermined threshold. This way, a lower error rate can be guaranteed at the cost of rejecting some predictions. However, estimating high quality confidence scores from neural networks, which create well-ordered

![](img/3013a5e7af0c305d337644a32207e3ef_20_0.png)

Figure 1.1: DLVMs layers of stochastic variables.
