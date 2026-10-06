# CHAPTER 1. INTRODUCTION

![](bbox=[0.227, 0.107, 0.763, 0.393])

Figure 1.3: Machine learning taxonomy.

k-nearest neighbors, etc. Note that some models can be used for both classification and regression. A supervised learning problem be formalized as follows:

$f(x) = y$

$f$ is a function that maps input data $x$ (for example images) to an output $y$ (types of fruits). Usually, an algorithm will try to learn the best model $f$ given data consisting of $n$ pairs $(x, y)$ of examples. During learning, the algorithm has access to the expected output/label $y$ for each input $x$. At inference time, that is, when we want to make predictions for new examples, we can use the learned model $f$ and feed it with a new $x$ to obtain the corresponding predicted value $y$.

+   **Semi-supervised learning.** This is the case when the certainty of the labels is 100% but not all training data are labeled. Usually, this scenario considers the case when only a very small portion of the data is labeled. That is, the dataset contains pairs of examples of the form $(x,y)$ but also examples where $y$ is missing $(x)$. In supervised learning, both $x$ and $y$ must be present. On the other hand, semi-supervised algorithms can learn even if some examples are missing the expected output $y$. This is a common situation in real life since labeling data can be expensive and time-consuming. In the fruits example, someone needs to tag every training image manually before training a model. Semi-supervised learning methods try to extract information also from the