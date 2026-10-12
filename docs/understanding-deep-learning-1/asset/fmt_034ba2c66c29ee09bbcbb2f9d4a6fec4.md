
It has recently become possible to train deeper graph neural networks using various forms of residual connection (Xu et al., 2018; Li et al., 2020a; Gong et al., 2020; Chen et al., 2020b; Xu et al., 2021a). Li et al. (2021a) train a state-of-the-art model with more than 1000 layers using an invertible network to reduce the memory requirements of training (see chapter 16).

## Problems

**Problem 13.1** Write out the adjacency matrices for the two graphs in [figure 13.14](#c013.xhtml#c13-fig-0014).

![Figure 13.14 Graphs for problems 13.1, 13.3, and 13.8.](images/c13-fig-0014.jpg)

[Figure 13.14](#c013.xhtml#c13-fig-0014a) Graphs for problems 13.1, 13.3, and 13.8.

**Problem 13.2\*** Draw graphs that correspond to the following adjacency matrices:

![](images/c13-fig-5032.jpg)

**Problem 13.3\*** Consider the two graphs in [figure 13.14](#c013.xhtml#c13-fig-0014). How many ways are there to walk from node one to node two in (i) three steps and (ii) seven steps?

**Problem 13.4** The diagonal of **A**² in [figure 13.4c](#c013.xhtml#c13-fig-0004) contains the number of edges that connect to each corresponding node. Explain this phenomenon.

**Problem 13.5** What permutation matrix is responsible for the transformation between the graphs in [figures 13.5a–c](#c013.xhtml#c13-fig-0005) and [figure 13.5d–f](#c013.xhtml#c13-fig-0005)?

* * *

Appendix B.4.4

Permutation matrix

* * *

**Problem 13.6** Prove that:

![c13-fig-5033.jpg](images/c13-fig-5033.jpg)

 (13.27)

where **P** is an *N* × *N* permutation matrix (a matrix that is all zeros except for exactly one entry in each row and each column, which is one), and **1** is an *N* × 1 vector of ones.

**Problem 13.7\*** Consider the simple GNN layer:

![c13-fig-5034.jpg](images/c13-fig-5034.jpg)

 (13.28)

where **H** is a *D* × *N* matrix containing the *N* node embeddings in its columns, **A** is the *N* × *N* adjacency matrix, **β** is the bias vector, and **Ω** is the weight matrix. Show that this layer is equivariant to permutations of the node order so that:

![c13-fig-5035.jpg](images/c13-fig-5035.jpg)

 (13.29)

where **P** is an *N* × *N* permutation matrix.

**Problem 13.8** What is the degree matrix **D** for each graph in [figure 13.14](#c013.xhtml#c13-fig-0014)?

**Problem 13.9** The authors of GraphSAGE (Hamilton et al., 2017a) propose a pooling method in which the node embedding is averaged together with its neighbors so that:

![c13-fig-5036.jpg](images/c13-fig-5036.jpg)

 (13.30)

Show how this operation can be computed simultaneously for all node embeddings in the *D* × *N* embedding matrix **H** using linear algebra. You will need to use both the adjacency matrix **A** and the degree matrix **D**.

**Problem 13.10\*** Devise a graph attention mechanism based on dot-product self-attention and draw its mechanism in the style of [figure 13.12](#c013.xhtml#c13-fig-0012).

**Problem 13.11\*** Draw the edge graph associated with the graph in [figure 13.15a](#c013.xhtml#c13-fig-0016).

![Figure 13.15 Graphs for problems 13.11–13.13.](images/c13-fig-0015.jpg)

[Figure 13.15](#c013.xhtml#c13-fig-0016a) Graphs for problems 13.11–13.13.

**Problem 13.12\*** Draw the node graph corresponding to the edge graph in [figure 13.15b](#c013.xhtml#c13-fig-0016).

**Problem 13.13** For a general undirected graph, describe how the adjacency matrix of the node graph relates to the adjacency matrix of the corresponding edge graph.

**Problem 13.14\**** Design a layer that updates a node embedding **h**[n] based on its neighboring node embeddings ![c13-fig-5037.jpg](images/c13-fig-5037.jpg) and neighboring edge embeddings ![c13-fig-5038.jpg](images/c13-fig-5038.jpg). You should consider the possibility that the edge embeddings are not the same size as the node embeddings.

# Chapter 14 Unsupervised learning

Chapters 2–9 walked through the *supervised learning* pipeline. We defined models that mapped observed data **x** to output values **y** and introduced loss functions that measured the quality of that mapping for a training dataset {**x**[i], **y**[i]}. Then we discussed how to fit and measure the performance of these models. Chapters 10–13 introduced more sophisticated model architectures incorporating parameter sharing and allowing parallel computational paths.

The defining characteristic of *unsupervised learning models* is that they are learned from a set of observed data {**x**[i]} in the absence of labels. All unsupervised models share this property, but they have diverse goals. They may be used to generate plausible new samples from the dataset or to manipulate, denoise, interpolate between, or compress examples. They can also be used to reveal the internal structure of a dataset (e.g., by dividing it into coherent clusters) or to distinguish whether new examples belong to the same dataset or are outliers.

This chapter introduces a taxonomy of unsupervised learning models and then discusses the desirable properties of models and how to measure their performance. The four subsequent chapters discuss four particular models: generative adversarial networks (GANs), variational autoencoders (VAEs), normalizing flows, and diffusion models.[¹](#c014.xhtml#c14-fn-0001)

## 14.1 Taxonomy of unsupervised learning models

A common strategy in unsupervised learning is to define a mapping between the data examples **x** and a set of unseen *latent* variables **z**. These latent variables capture underlying structure in the dataset and usually have a lower dimension than the original data; in this sense, a latent variable **z** can be considered a compressed version of a data example **x** that captures its essential qualities (figures 1.9–1.10).

In principle, the mapping between the observed and latent variables can be in either direction. Some models map from the data **x** to latent variables **z**. For example, the famous *k-means* algorithm maps the data **x** to a cluster assignment *z* ∈{1, 2, …, *K*}. Other models map from the latent variables **z** to the data **x**. Consider defining a distribution *Pr*(**z**) over the latent variable **z** in these models. New examples can now be *generated* by (i) drawing from this distribution and (ii) mapping the sample to the data space **x**. Accordingly, these are termed *generative models* (see [figure 14.1](#c014.xhtml#c14-fig-0001)).

![Figure 14.1 Taxonomy of unsupervised learning models. Unsupervised learning refers to any model trained on datasets without labels. Generative models can synthesize (generate) new examples with similar statistics to the training data. A subset of these are probabilistic and define a distribution over the data. We draw samples from this distribution to generate new examples. Latent variable models define a mapping between an underlying explanatory (latent) variable and the data. They may fall into any of the above categories.](images/c14-fig-0001.jpg)

[Figure 14.1](#c014.xhtml#c14-fig-0001a) Taxonomy of unsupervised learning models. Unsupervised learning refers to any model trained on datasets without labels. Generative models can synthesize (generate) new examples with similar statistics to the training data. A subset of these are probabilistic and define a distribution over the data. We draw samples from this distribution to generate new examples. Latent variable models define a mapping between an underlying explanatory (latent) variable and the data. They may fall into any of the above categories.

The four models in chapters 15 to 18 are all generative models that use latent variables. *Generative adversarial networks* (chapter 15) learn to generate data examples **x**\* from latent variables **z**, using a loss that encourages the generated samples to be indistinguishable from real examples ([figure 14.2a](#c014.xhtml#c14-fig-0002)).
