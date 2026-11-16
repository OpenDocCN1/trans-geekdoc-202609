
![](img/c73db5a1f734ebb7c0655f19e5bc9daa_174_0.png)

Figure 31.12: Part of a hierarchical latent tree learned from the 20-newsgroup data. From Figure 2 of [HW11]. Used with kind permission of Stefan Harmeling.

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_174_1.png)

Figure 31.13: A partially latent tree learned from the 20-newsgroup data. Note that some words can have multiple meanings, and get connected to different latent variables, representing different “topics”. For example, the word “win” can refer to a sports context (represented by h5) or the Microsoft Windows context (represented by h25). From Figure 12 of [Cho+11]. Used with kind permission of Jin Choi.

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_175_0.png)

Figure 31.14: Google's Rephil model. Leaves represent presence or absence of words. Internal nodes represent clusters of co-occurring words, or “concepts”. All nodes are binary, and all CPDs are noisy-OR. The model contains 12 million word nodes, 1 million latent cluster nodes, and 350 million edges. Used with kind permission of Brian Milch.

An alternative approach is proposed in [Cho+11], in which the observed data is not constrained to be at the leaves. This method starts with the Chow-Liu tree on the observed data, and then adds hidden variables to capture higher-order dependencies between internal nodes. This results in much more compact models, as shown in Figure 31.13. This model also has better predictive accuracy than other approaches, such as mixture models, or trees where all the observed data is forced to be at the leaves. Interestingly, one can show that this method can recover the exact latent tree structure, providing the data is generated from a tree. See [Cho+11] for details. Note, however, that this approach, unlike [Zha04; HW11], requires that the cardinality of all the variables, hidden and observed, be the same. Furthermore, if the observed variables are Gaussian, the hidden variables must be Gaussian also.

## 31.2.8.8 Example: Google's Rephil

In this section, we describe a huge DGM called **Rephil**, which was automatically learned from data.² The model is widely used inside Google for various purposes, including their famous AdSense system.³

The model structure is shown in Figure 31.14. The leaves are binary nodes, and represent the presence or absence of words or compounds (such as “New York City”) in a text document or query. The latent variables are also binary, and represent clusters of co-occurring words. All CPDs are noisy-OR, since some leaf nodes (representing words) can have many parents. This means each edge can be augmented with a hidden variable specifying if the link was activated or not; if the link is not active, then the parent cannot turn the child on. (A very similar model was proposed independently in [SH06].)

Parameter learning is based on EM, where the hidden activation status of each edge needs to be inferred [MH97]. Structure learning is based on the old neuroscience idea that “**nodes that fire together should wire together**”. To implement this, we run inference and check for cluster-word and cluster-cluster pairs that frequently turn on together. We then add an edge from parent to child if the link can significantly increase the probability of the child. Links that are not activated very often are pruned out. We initialize with one cluster per “document” (corresponding to a set of semantically related phrases). We then merge clusters A and B if A explains B’s top words and vice versa. We can also discard clusters that are used too rarely.

²The original system, called “Phil”, was developed by Georges Harik and Noam Shazeer. It has been published as US Patent #8024372, “Method and apparatus for learning a probabilistic generative model for text”, filed in 2004. Rephil is a more probabilistically sound version of the method, developed by Uri Lerner et al. The summary below is based on notes by Brian Milch (who also works at Google).

³AdSense is Google's system for matching web pages with content-appropriate ads in an automatic way, by extracting semantic keywords from web pages. These keywords play a role analogous to the words that users type in when searching; this latter form of information is used by Google's AdWords system. The details are secret, but [Lev11] gives an overview.

The model was trained on about 100 billion text snippets or search queries; this takes several weeks, even on a parallel distributed computing architecture. The resulting model contains 12 million word nodes and about 1 million latent cluster nodes. There are about 350 million links in the model, including many cluster-cluster dependencies. The longest path in the graph has length 555, so the model is quite deep.

Exact inference in this model is obviously infeasible. However note that most leaves will be off, since most words do not occur in a given query; such leaves can be analytically removed. We can also prune out unlikely hidden nodes by following the strongest links from the words that are up to their parents to get a candidate set of concepts. We then perform iterative conditional modes (ICM) to form approximate inference. (ICM is a deterministic version of Gibbs sampling that sets each node to its most probable state given the values of its neighbors in its Markov blanket.) This continues until it reaches a local maximum. We can repeat this process a few times from random starting configurations. At Google, this can be made to run in 15 milliseconds!

## 31.2.8.9 Spectral methods

Recently, various methods have been developed that can recover the exact structure of the DAG, even in the presence of (a known number of) latent variables, under certain assumptions. In particular, identifiability results have been obtained for the following cases:

- If x contains 3 or more independent views of z [Goo74; AMR09; AHK12; HKZ12], sometimes called the triad constraint.

- If z is categorical, and x is a GMM with mixture components which depend on z [Ana+14].

- If z is composed of binary variables, and x is a set of noisy-OR CPDs [JHS13; Aro+16].

In terms of algorithms, most of these methods are not based on maximum likelihood, but instead use the method of moments and spectral methods. For details, see [Ana+14].

## 31.2.8.10 Constraint-based methods for learning ADMGs

An alternative to explicitly modeling latent variables is to marginalize them out, and work with acyclic directed mixed graphs (??). It is possible to perform Bayesian model selection for ADMGs, although the method is somewhat slow and complicated [SG09]. Alternatively, one can modify the PC/IC algorithm to learn an ADMG. This method is known as the IC* algorithm [Pea09, p52]: one can speed it up to get the FCI algorithm (FCI stands for “fast causal inference”) [SGS00, p144].

Since there will inevitably be some uncertainty about edge orientations, due to Markov equivalence, the output of IC*/ FCI is not actually an ADMG, but is a closely related structure called a partially oriented inducing path graph [SGS00, p135] or a marked pattern [Pea09, p52]. Such a graph has 4 kinds of edges:

- A marked arrow a *-> b signifying a directed path from a to b.

- An unmarked arrow a -> b signifying a directed path from a to b or a latent common cause a <- L -> b.

- A bidirected arrow a <- b signifying a latent common causes a <- L -> b.

- An undirected edge a - b signifying a <- b or a -> b or a latent common causes a <- L -> b.

IC*/ FCI is faster than Bayesian inference, but suffers from the same problems as the original IC/PC algorithm (namely, the need for a CI testing oracle, problems due to multiple testing, no probabilistic representation of uncertainty, etc.) Furthermore, by not explicitly representing the latent variables, the resulting model cannot be used for inference and prediction.

## 31.3 Learning undirected graph structures

In this section, we discuss how to learn the structure of undirected graphical models. On the one hand, this is easier than learning DAG structure because we don't need to worry about acyclicity. On the other hand, it
