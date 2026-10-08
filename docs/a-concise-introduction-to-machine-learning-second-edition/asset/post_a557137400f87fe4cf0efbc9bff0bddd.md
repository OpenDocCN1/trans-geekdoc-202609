
to this data sample, the columns of the $D \times M$ matrix $\mathbf{D}$ represent latent features, and $\mathbf{c}_n$ is the sample specific vector of coefficients.

Commonly, this is represented as

$\mathbf{T} = \mathbf{CD}^T + \mathbf{E},$

where $\mathbf{T}$ is the $N \times D$ matrix of data samples with each row containing one sample, $\mathbf{C}$ is the $N \times M$ matrix of coefficients, and $\mathbf{E}$ is a $N \times D$ matrix with each entry being drawn from a normal distribution with zero mean and variance $\sigma^2$. In this context, $\mathbf{D}$ is the *factor loading matrix* and its columns are the factor loadings, while $\mathbf{C}$ is the *coordinate matrix*.

From the data viewpoint, we allow the number of columns in $\mathbf{D}$, where $M$ is $M$, to be infinite. Infinity is conceptually a difficult concept, it can be dealt with by imposing that only a finite, small number of entries in each row of $\mathbf{C}$ are nonzero. In practical terms, this means that we represent the amount of data and each data sample as a finite linear combination of features. Other features from the infinite set are those we have not yet encountered in our data.

To this end, $\mathbf{C}$ is written in terms of a *binary indicator matrix* $\mathbf{Z}$ and a *weight matrix* $\mathbf{W}$. That is,

$\mathbf{C} = \mathbf{Z} \odot \mathbf{W},$

where $\odot$ denotes the element-wise Hadamard product. Choosing dishes from an Indian buffet, hence the Indian Buffet Process (IBP). The customers are indexed by $1, \dots, N$. There are infinitely many dishes, but not all have been chosen yet. These are the latent features indexed by $m$. $M$ is the number of different dishes chosen so far. The number of dishes the first customer chooses is drawn from a Poisson distribution with rate $\lambda$, which is the expected number of dishes each customer chooses. In $\mathbf{Z}$, the first entry of the first row is set to one and $M = i_1$, where $i_1$ is the number of distinct dishes chosen so far. The amount he takes from each dish is drawn from the first row of $\mathbf{W}$.

The $n^{th}$ customer chooses from $\mathbf{M}$ any of which the previous customers have already chosen with probability $j_m/n$, if dish $m$ $j_m$ times. In other words, $j_m$ is the number of entries in column $m$ above row $n$ in $\mathbf{Z}$. If there is a particular dish $m$, then one is placed in the $m^{th}$ column of the $n^{th}$ row of $\mathbf{Z}$, new dishes, where $i_n$ is drawn from a Poisson distribution with rate $\lambda/n$. These are indicated by columns with numbers $M+1, \dots, M+i_n$, in the $n^{th}$ row. $M$ is updated to $M+i_n$. Since $\lambda/n$ decreases with every new customer, the probability that he will choose a new dish decreases. This means that if our model does not have enough features to explain the data, there is nonzero probability to help explain the data.

In each row, the expected number of nonzero entries is $\lambda$. This is true for the first row, since the expectation of a Poisson distribution is given by $\lambda$. Assume that the expected number of nonzero entries for rows $1, \dots, n-1$ is $\lambda$. The expected number of nonzero entries in the $n^{th}$ row is

$\mathbb{E}\left[\sum_{m=1}^{M} \frac{j_{m}}{n} + \frac{\lambda}{n}\right] = \mathbb{E}\left[\sum_{m=1}^{M} \frac{m-1}{n} + \frac{\lambda}{n}\right] = \mathbb{E}\left[\sum_{k=1}^{n-1} \sum_{m=1}^{M} Z_{km}\right]$

where $Z_{km}$ denotes the $(k, m)$ entry in $Z$. By induction, this proves that the expected number of nonzero entries in each row is $\lambda$. Since the probability of choosing a particular dish depends on the number of times it has been chosen by previous customers, we encounter the rich-get-richer phenomenon. Since the number of customers $N$ is finite, so is the number of possible dishes $M$. Chosen by many customers these relate to features which are common in most of the data samples. These are sometimes referred to as *global features*, while those chosen by a few customers indicate *local features*, which can be used to distinguish between samples.

This process of generating the data is independent of the order in which customers arrive. A different order of customers multiplying $Z$ by a permutation matrix from the left changes the row order. We follow this up with a permutation matrix from the right which swaps columns so that the number of zeros in each column is increasing from left to right, because each subsequent customer can choose new dishes. Such a permutation is equivalent to relabeling the dishes. The weights $W$ are multiplied by the same permutation matrices from left and $Z$. These permutations are not performed explicitly, but explain that the order in which samples are generated does not affect the final outcome. It is known as left-ordering of binary matrices. More specifically, given an order of customers (rows of $Z$), the columns of $Z$ are ordered by their binary nature. Each column is interpreted as a binary number with the most significant bit in the first row and the least significant one in the last. The columns are ordered in decreasing magnitude of these binary numbers. Two columns might represent exactly the same binary. This means two dishes were chosen by exactly the same set of customers. In this case, we have freedom of choice in the order of columns representing the same binary number.

There are $M!$ possible labels of the dishes. We need to divide this by the number of possible equivalences. Let $K$ be the number of distinct columns and $m_{k}$ be the number of occurrences of the distinct column $k$ for $k = 1, 2, \dots, K$. That is,

$M = \sum_{k=1}^{K} m_k.$

The number of possible equivalences in relabelling is

$\prod_{k=1}^{K} m_k!,$

Hence the number of different ways the same data can have been generated

$\frac{M!}{\prod_{k=1}^{K} m_k!}$

The describes a prior distribution $p(Z)$. Also a prior distribution for $\mathbf{W}$ needs to be specified. This is done by specifying distributions for the elements of $\mathbf{W}$. Possible choices are, for example, the normal distribution as seen in Figure 2.2, the Laplace distribution in Figure 2.17. Lastly, prior distributions for each of the columns of $\mathbf{D}$ need to be defined.

The learning process updates the parameters of these distributions according to the data, and specific instances are sampled. More specifically, $\mathbf{D}$ is kept fixed while the distributions of $\mathbf{Z}$ and $\mathbf{W}$ are updated. After instances of $\mathbf{Z}$ and $\mathbf{W}$ are sampled, they are kept fixed and the distributions of $\mathbf{D}$ are updated. Variational passes through the data as necessary.

The process is similar to the Dirichlet process described in Section 6.7. The exact workings are however, beyond the scope of this book. Griffiths & Ghahramani (2011) provides an introduction and review. Zhou et al. (2012) provides an example in image processing, where the blocks building up the image are inferred from the image itself in contrast to engineered blocks as shown in Figure 7.1.

When we infer the underlying process from data, a data sample which does not fit in the probabilistic description of the data so far, is interpreted as a new draw from the base distribution. Outliers can be dealt with in this way.

# Exercises

**Exercise 9.1.** Neural networks are best explored computationally. Experiment with different architecture and investigate what insight different layers and neurons offer.
