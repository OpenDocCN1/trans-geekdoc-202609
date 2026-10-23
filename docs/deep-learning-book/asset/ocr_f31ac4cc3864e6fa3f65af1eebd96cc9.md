modeling $p({\bf{x}})$ by splitting it into $n$ supervised learning problems. Alternatively, we can solve the supervised learning problem of learning $p(y \mid {\bf{x}})$ by using traditional unsupervised learning technologies to learn the joint distribution $p({\bf{x}}, y)$, then inferring

```
$p(y \mid {\bf{x}}) = \frac{p({\bf{x}}, y)}{\sum_{y'} p({\bf{x}}, y')}. $  (5.2)
```

Though unsupervised learning and supervised learning are not completely formal or distinct concepts, they do help roughly categorize some of the things we do with machine learning algorithms. Traditionally, people refer to regression, classification and structured output problems as supervised learning. Density estimation in support of other tasks is usually considered unsupervised learning.

Other variants of the learning paradigm are possible. For example, in semi-supervised learning, some examples include a supervision target but others do not. In multi-instance learning, an entire collection of examples is labeled as containing or not containing an example of a class, but the individual members of the collection are not labeled. For a recent example of multi-instance learning with deep models, see *Kotzias et al. (2015)*.

Some machine learning algorithms do not just experience a fixed dataset. For example, **reinforcement learning** algorithms interact with an environment, so there is a feedback loop between the learning system and its experiences. Such algorithms are beyond the scope of this book. Please see *Sutton and Barto (1998)* or *Bertsekas and Tsitsiklis (1996)* for information about reinforcement learning, and *Mnih et al. (2013)* for the deep learning approach to reinforcement learning.

Most machine learning algorithms simply experience a dataset. A dataset can be described in many ways. In all cases, a dataset is a collection of examples, which are in turn collections of features.

One common way of describing a dataset is with a **design matrix**. A design matrix is a matrix containing a different example in each row. Each column of the matrix corresponds to a different feature. For instance, the *Iris* dataset contains 150 examples with four features for each example. This means we can represent the dataset with a design matrix $\mathbf{X} \in \mathbb{R}^{150 \times 4}$, where $X_{i,1}$ is the sepal length of plant $i$, $X_{i,2}$ is the sepal width of plant $i$, *etc*. We describe most of the learning algorithms in this book in terms of how they operate on design matrix datasets.

Of course, to describe a dataset as a design matrix, it must be possible to describe each example as a vector, and each of these vectors must be the same size. This is not always possible. For example, if you have a collection of photographs with different widths and heights, then different photographs will contain different numbers of pixels, so not all the photographs may be described with the same