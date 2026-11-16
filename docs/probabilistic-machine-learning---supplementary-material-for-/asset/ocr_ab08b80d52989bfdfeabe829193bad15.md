# Chapter 28

# Latent variable models

# 28.1 Topic models

In this section, we show how to modify the multinomial PCA model of **??** to handle variable-sized observations, such as text documents. The basic idea is to assume each observation **_x_**_<sub>l</sub>_ is generated independently of all the others conditional on the shared latent factors **_z_**; the likelihood is categorical, with shared parameters, and the prior is Dirichlet distribution. This is called a **topic model**, since the **_z_** variables can be interpreted as a mixture of different topics that are present in document **_x_**.

# 28.1.1 Latent Dirichlet Allocation (LDA)

The most common kind of topic model is called **latent Dirichlet allocation (LDA)** [BNJ03; Ble12; BGHM17]. (This usage of the term “LDA” is not to be confused with linear discriminant analysis.)

# 28.1.1.1 Model definition

We can define the LDA model as follows. Let $x_{nl} \in \{1, \dots, V\}$ be the identity of the $l$’th word in document $n$, where $l$ can now range from 1 to $L_n$, the length of the document, and $V$ is the size of the vocabulary. The probability of word $v$ at location $l$ is given by

$p(x_{nl} = v | z_n) = \sum_k z_{nk} w_{kv}$ (28.1)

where $0 \le z_{nk} \le 1$ is the proportion of “topic” $k$ in document $n$, and $z_n \sim \text{Dir}(\alpha)$.

We can rewrite this model by associating a discrete latent variable $c_{nl} \in \{1, \dots, N_z\}$ with each word in each document, with distribution $p(c_{nl} | z_n) = \text{Cat}(c_{nl} | z_n)$. Thus $c_{nl}$ specifies the topic to use for word $l$ in document $n$. The full joint model becomes

$p(x_n, z_n, c_n) = \text{Dir}(z_n | \alpha) \prod_{l=1}^{L_n} \text{Cat}(c_{nl} | z_n) \text{Cat}(x_{nl} | W[c_{nl}, :])$ (28.2)

where **W**[$k$, :] = **_w_**_<sub>k</sub>_ is the distribution over words for the $k$’th topic. See Figure 28.1 for the corresponding PGM-D.

We typically use a Dirichlet prior the topic parameters, $p(w_k) = \text{Dir}(w_k | \beta 1_V)$; by setting $\beta$ small enough, we can encourage these topics to be sparse, so that each topic only predicts a subset of the words. In addition, we use a Dirichlet prior on the latent factors, $p(z_n) = \text{Dir}(z_n | \alpha 1_{N_z})$. If we set $\alpha$ small enough, we can encourage the topic distribution for each document to be sparse, so that each document only contains a subset of the topics. See Figure 28.2 for an illustration.