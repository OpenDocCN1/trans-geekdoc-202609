
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_738_0.png)

There are many forms of side information we can use. For items, we often have rich meta-data, such as text (e.g., title), images (e.g., cover), high-dimensional categorical variables (e.g., location), or just scalars (e.g., price). For users, the side information available depends on the specific form of the interactive system. For search engines, it is the list of queries the user has issued, and (if they are logged in), information derived from websites they have visited (which is tracked via cookies). For online shopping sites, it is the list of searches plus past viewing and purchasing behavior. For social networking sites, there is information about the friendship graph of each user.

It is very easy to capture this side information in the factorization machines framework, by expanding our definition of x beyond the two one-hot vectors, as illustrated in Fig. 22.6. The same input encoding can of course be fed into other kinds of models, such as deepFM or neuralMF.

In addition to features about the user and item, there may be other contextual features, such as the time of the interaction (e.g., the day or evening). The order (sequence) of the most recently viewed items is often also a useful signal. The “Convolutional Sequence Embedding Recommendation” or Caser model proposed in [TW18] captures this by embedding the last M items, and then treating the M × K input as an image, by using a convolutional layer as part of the model.

Many other kinds of neural models can be designed for the recommender task. See e.g., [Zha+19] for a review.

An interesting “twist” to recommender systems that does not arise in other kinds of prediction problems is the fact that the data that the system is trained on is a consequence of recommendations made by earlier versions of the system. Thus there is a feedback loop [Bot+13]. For example, consider the YouTube video recommendation system [CAS16]. There are millions of videos on the site, so the system must come up with a shortlist, or “slate”, of videos to show the user, to help them find what they want (see e.g., [Ie+19]). If the user watches one of these videos, the system can consider this positive feedback that it made a good recommendation, and it can update the model parameters accordingly. However, maybe there was some other video that the user would have liked even more? It is impossible to answer this counterfactual unless the system takes a chance and shows some items for which the user response is uncertain. This is an example of the exploration-exploitation tradeoff that we introduced in Sec. 8.3.3. In addition to needing to explore, the system may have to wait for a long time until it can detect if a change it made to its recommendation policies was beneficial. It is common to use **reinforcement learning** to learn policies which optimize long-term reward. See the sequel to this book, [Mur22], for details.

## 23 Graph embeddings¹
### 23.1 Introduction

We now turn our focus to data which has semantic relationships between training samples {x_n}_{n=1}^N. The relationships (known as edges) connect training samples (nodes) with an application specific meaning (commonly similarity). Graphs provide the mathematical foundations for reasoning about these kinds of relationships

Graphs are universal data structures that can represent complex relational data (composed of nodes and edges), and appear in multiple domains such as social networks, computational chemistry [Gil+17], biology [Sta+06], recommendation systems [KSJ09], semi-supervised learning [GB18], and others.

Let A ∈ {0,1}^{N×N} be the adjacency matrix, where N is the number of nodes, and let W ∈ ℝ^{N×N} be a weighted version. In the methods we discuss below, some set W = A while others set W to a transformation of A, such as row-wise normalization. Finally, let X ∈ ℝ^{N×D} be a matrix of node features.

When designing and training a neural network model over graph data, we desire the designed method be applicable to nodes which participate in different graph settings (e.g. have differing connections and community structure). Contrast this with a neural network model designed for images, where each pixel (node) has the same neighborhood structure. By contrast, an arbitrary graph has no specified alignment of nodes, and further, each node might have a different neighborhood structure. See Fig. 23.1 for a comparison. Consequently, operations like Euclidean spatial convolution cannot be directly applied on irregular graphs: Euclidean convolutions strongly rely on geometric priors (such as shift invariance), which don’t generalize to non-Euclidean domains.

These challenges led to the development of Geometric Deep Learning (GDL) research [Bro+17b], which aims at applying deep learning techniques to non-Euclidean data. In particular, given the widespread prevalence of graphs in real-world applications, there has been a surge of interest in applying machine learning methods to graph-structured data. Among these, Graph Representation Learning (GRL) [Cha+20] methods aim at learning low-dimensional continuous vector representations for graph-structured data, also called embeddings.

We divide GRL here into two classes of problems: unsupervised and supervised (or semi-supervised) GRL. The first class aims at learning low-dimensional Euclidean representations optimizing an objective, e.g. one that preserves the structure of an input graph. The second class also learns low-dimensional Euclidean representations but for a specific downstream prediction task such as

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_742_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_742_1.png)

(a) Grid (Euclidean).

(b) Arbitrary graph (Non-Euclidean).

Figure 23.1: An illustration of Euclidean vs. non-Euclidean graphs. Used with permission from [Cha+20].

node or graph classification. Further, the graph structure can be fixed throughout training and testing, which is known as the **transductive** learning setting (e.g. predicting user properties in a large social network), or alternatively the model is expected to answer questions about graphs not seen during training, known as the **inductive** learning setting (e.g. classifying molecular structures). Finally, while most supervised and unsupervised methods learn representations in Euclidean vector spaces, there recently has been interest for **non-Euclidean representation learning**, which aims at learning non-Euclidean embedding spaces such as hyperbolic or spherical spaces. The main motivations for this body of work are to use a continuous embedding space that resembles the underlying discrete structure of the input data it tries to embed (e.g. the hyperbolic space is a continuous version of trees [Sar11]).

### 23.2 Graph Embedding as an Encoder/Decoder Problem

While there are many approaches to GRL, many methods follow a similar pattern. First, the network input (node features **X** ∈ ℝ^{N×D} and graph edges in **A** or **W** ∈ ℝ^{N×N}) is encoded from the discrete domain of the graph into a continuous representation (embedding), **Z** ∈ ℝ^{N×L}. Next, the learned representation **Z** is used to optimize a particular objective (such as reconstructing the links of the graph). In this section we will use the graph encoder-decoder model (**GRAPHEDM**) proposed by Chami et al. [Cha+20] to analyze popular families of GRL methods.

The **GRAPHEDM** framework (Figure 23.2, [Cha+20]) provides a general framework that encapsulates a wide variety of supervised and unsupervised graph embedding methods: including ones utilizing the graph as a regularizer (e.g. [ZG02]), positional embeddings (e.g. [PARS14]), and graph neural networks such as ones based on message passing [Gil+17; Sca+09] or graph convolutions [Bru+14; KW16a]).

The **GRAPHEDM** framework takes as input a weighted graph **W** ∈ ℝ^{N×N}, and optional node
