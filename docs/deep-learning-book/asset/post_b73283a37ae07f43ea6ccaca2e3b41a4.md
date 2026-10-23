
![](img/e7937519e1e39a29aca97c7de303ca30_479_0.png)

Figure 12.4: Illustration of a simple hierarchy of word categories, with 8 words $w_0$, $\ldots$, $w_7$ organized into a three-level hierarchy. The leaves of the tree represent actual specific words. Internal nodes represent groups of words. Any node can be indexed by the sequence of binary decisions ($0 =$ left, $1 = $ right) to reach the node from the root. Super-class $(0)$ contains the classes $(0,0)$ and $(0,1)$, which respectively contain the sets of words $\{w_0, w_1\}$ and $\{w_2, w_3\}$, and similarly super-class $(1)$ contains the classes $(1,0)$ and $(1,1)$, which respectively contain the words $(w_4, w_5)$ and $(w_6, w_7)$. If the tree is sufficiently balanced, the maximum depth (number of binary decisions) is on the order of the logarithm of the number of words $|\mathcal{V}|$: the choice of one out of $|\mathcal{V}|$ words can be obtained by doing $O(\log |\mathcal{V}|)$ operations (one for each of the nodes on the path from the root). In this example, computing the probability of a word $y$ can be done by multiplying three probabilities, associated with the binary decisions to move left or right at each node on the path from the root to a node $y$. Let $b_i(y)$ be the $i$-th binary decision when traversing the tree toward the value $y$. The probability of sampling an output $y$ decomposes into a product of conditional probabilities, using the chain rule for conditional probabilities, with each node indexed by the prefix of these bits. For example, node $(1,0)$ corresponds to the prefix $(b_0(w_4) = 1, b_1(w_4) = 0)$, and the probability of $w_4$ can be decomposed as follows:

$$P(y = w_4) = P(\mathrm{b}_0 = 1, \mathrm{b}_1 = 0, \mathrm{b}_2 = 0) \tag{12.11}$$
$$= P(\mathrm{b}_0 = 1) P(\mathrm{b}_1 = 0 \mid \mathrm{b}_0 = 1) P(\mathrm{b}_2 = 0 \mid \mathrm{b}_0 = 1, \mathrm{b}_1 = 0). \tag{12.12}$$

The number of bits required to identify a word, with the weighting given by the frequency of these words. In this example, the number of operations needed to compute the hidden activations grows as $O(\ln n_h^2)$, while the output computations grow as $O(n_h n_b)$. As long as $n_b \leq \ln n_h$, we can reduce computation more by shrinking $n_h$ than by shrinking $n_b$. Indeed, $n_b$ is often small. Because the size of the vocabulary rarely exceeds a million words and $\log_2(10^6) \approx 20$, it is possible to reduce $n_b$ to about 20, but $n_h$ is often much larger, around $10^3$ or more. Rather than carefully optimizing a tree with a branching factor of 2, one can instead define a tree with depth two and a branching factor of $\sqrt{|\mathbb{V}|}$. Such a tree corresponds to simply defining a set of mutually exclusive word classes. The simple approach based on a tree of depth two captures most of the computational benefit of the hierarchical strategy.

One question that remains somewhat open is how to best define these word classes, or how to define the word hierarchy in general. Early work used existing hierarchies (Morin and Bengio, 2005), but the hierarchy can also be learned, ideally jointly with the neural language model. Learning the hierarchy is difficult. An exact optimization of the log-likelihood appears intractable because the choice of a word hierarchy is a discrete one, not amenable to gradient-based optimization. However, one could use discrete optimization to approximately optimize the partition of words into word classes.

An important advantage of the hierarchical softmax is that it brings computational benefits both at training time and at test time, if at test time we want to compute the probability of specific words.

Of course, computing the probability of all $|\mathbb{V}|$ words will remain expensive even with the hierarchical softmax. Another important operation is selecting the most likely word in a given context. Unfortunately the tree structure does not provide an efficient and exact solution to this problem.

A disadvantage is that in practice the hierarchical softmax tends to give worse test results than sampling-based methods, which we describe next. This may be due to a poor choice of word classes.

### 12.4.3.3 Importance Sampling

One way to speed up the training of neural language models is to avoid explicitly computing the contribution of the gradient from all the words that do not appear in the next position. Every incorrect word should have low probability under the model. It can be computationally costly to enumerate all these words. Instead, it is possible to sample only a subset of the words. Using the notation introduced in equation 12.8, the gradient can be written as follows:

$$\frac{\partial \log P(y \mid C)}{\partial \theta} = \frac{\partial \log \text{softmax}_y(\mathbf{a})}{\partial \theta} \tag{12.13}$$
$$= \frac{\partial}{\partial \theta} \log \frac{e^{a_y}}{\sum_i e^{a_i}} \tag{12.14}$$
$$= \frac{\partial}{\partial \theta} \left(a_y - \log \sum_i e^{a_i}\right) \tag{12.15}$$
$$= \frac{\partial a_y}{\partial \theta} - \sum_i P(y = i \mid C) \frac{\partial a_i}{\partial \theta}, \tag{12.16}$$

where $\mathbf{a}$ is the vector of pre-softmax activations (or scores), with one element per word. The first term is the **positive phase** term, pushing $a_y$ up, while the second term is the **negative phase** term, pushing $a_i$ down for all $i$, with weight $P(i \mid C)$. Since the negative phase term is an expectation, we can estimate it with a Monte Carlo sample. However, that would require sampling from the model itself. Sampling from the model requires computing $P(i \mid C)$ for all $i$ in the vocabulary, which is precisely what we are trying to avoid.

Instead of sampling from the model, we can sample from another distribution, called the proposal distribution (denoted $q$), and use appropriate weights to correct for the bias introduced by sampling from the wrong distribution (Bengio and Sénécal, 2003; Bengio and Sénécal, 2008). This is an application of a more general technique called **importance sampling**, which we describe in more detail in section 17.2. Unfortunately, even exact importance sampling is not efficient because it requires computing weights $p_i/q_i$, where $p_i = P(i \mid C)$, which can only be computed if all the scores $a_i$ are computed. The solution adopted for this application is called **biased importance sampling**, where the importance weights are normalized to sum to 1. When negative word $n_i$ is sampled, the associated gradient is weighted by

$$w_i = \frac{p_{n_i}/q_{n_i}}{\sum_{j=1}^N p_{n_j}/q_{n_j}}. \tag{12.17}$$

These weights are used to give the appropriate importance to the $m$ negative samples from $q$ used to form the estimated negative phase contribution to the gradient:

$$\sum_{i=1}^{|\mathbb{V}|} P(i \mid C) \frac{\partial a_i}{\partial \theta} \approx \frac{1}{m} \sum_{i=1}^m w_i \frac{\partial a_{n_i}}{\partial \theta}. \tag{12.18}$$

A unigram or a bigram distribution works well as the proposal distribution $q$. It is easy to estimate the parameters of such a distribution from data. After estimating the parameters, it is also possible to sample from such a distribution very efficiently.

Importance sampling is not only useful for speeding up models with large softmax outputs. More generally, it is useful for accelerating training with large sparse output layers, where the output is a sparse vector rather than a 1-of-$n$ choice. An example is a **bag of words**. A bag of words is a sparse vector $v$ where $v_i$ indicates the presence or absence of word $i$ from the vocabulary in the document. Alternatively, $v_i$ can indicate the number of times that word $i$ appears. Machine learning models that emit such sparse vectors can be expensive to train for a variety of reasons. Early in learning, the model may not actually choose to make the output truly sparse. Moreover, the loss function we use for training might most naturally be described in terms of comparing every element of the output to every element of the target. This means that it is not always clear that there is a computational benefit to using sparse outputs, because the model may choose to make the majority of the output nonzero, and all these non-zero values need to be compared to the corresponding training target, even if the training target is zero. *Dauphin et al.* (2011) demonstrated that such models can be accelerated using importance sampling. The efficient algorithm minimizes the loss reconstruction for the “positive words” (those that are nonzero in the target) and an equal number of “negative words.” The negative words are chosen randomly, using a heuristic to sample words that are more likely to be mistaken. The bias introduced by this heuristic oversampling can then be corrected using importance weights.

In all these cases, the computational complexity of gradient estimation for the output layer is reduced to be proportional to the number of negative samples rather than proportional to the size of the output vector.

### 12.4.3.4 Noise-Contrastive Estimation and Ranking Loss

Other approaches based on sampling have been proposed to reduce the computational cost of training neural language models with large vocabularies. An early example is the ranking loss proposed by *Collobert and Weston* (2008a), which views the output of the neural language model for each word as a score and tries to make the score of the correct word $a_y$ be ranked high in comparison to the other scores $a_i$. The ranking loss proposed then is

$$L = \sum_i \max(0, 1 - a_y + a_i). \tag{12.19}$$
