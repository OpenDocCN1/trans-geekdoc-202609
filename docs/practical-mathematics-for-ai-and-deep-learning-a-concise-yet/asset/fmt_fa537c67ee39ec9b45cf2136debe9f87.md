
*   **Convolutional Neural Network** (**CNN**): Mostly used for computer vision problems and image processing, and also used for natural language processing; it will be discussed in *[Chapter 9: Computer Vision](#c09.xhtml).*

*   **Recurrent Neural Nets** (**RNN**): Used for sequential data. We will discuss these in the *[Chapter 10: Sequence to Sequence Models](#c10.xhtml).*

*   **Transformers**: The state-of-the-art text analysis models like BERT are based on transformers. These are also being applied for other tasks like handwriting recognition and speech recognition. We have discussed this in the *[Chapter 11: Natural Language Processing](#c11.xhtml).*

*   **Siamese neural network**: This architecture contains two identical subnetworks that have the same configuration, with the same parameters and weights. It is used to find the similarity of the inputs by comparing their feature vectors.

There are many architectures that combine these basic architectures and build a new architecture. For example, a combination of CNN and RNN can be used to build a cursive handwriting recognizer that reads cursive handwriting from an image using CNN and then converts it into the corresponding text using RNN. The entire architecture is trained end to end using a data set consisting of handwriting images and corresponding text pair.

# [Conclusion](#toc.xhtml#s231a)

In this chapter, we discussed the basic concepts of neural networks. We covered the fundamental back propagation algorithm in detail and how it’s implemented in the automatic differentiation framework available in most deep learning frameworks. We also discussed the challenges of training neural networks with SGD and ways to mitigate it at the high level. These concepts will be revisited in the following chapters on the applications of neural networks to solve specific problems.

In the next chapter, we will introduce one more important topic, that is, unsupervised clustering, and then the following chapters will mostly be applications of the concepts learned so far for solving various AI problems.

# [Points to remember](#toc.xhtml#s232a)

*   A node in a neural network can be viewed as an adaptive basis function.

    Even with fixed non-linear activations changing the weights, we get various basis functions.

*   Each layer in the neural network can be viewed as a vector fields or tensor field that maps an input tensor/vector to the next layer’s input tensor/vector. These vector fields must be differentiable, that is, the activation function used must be differentiable for the network to be trainable using back propagation algorithm. The entire network can be viewed as a composition of a finite sequence of vector fields.

*   Using automatic differentiation technique discussed here, we can train any arbitrary neural network architecture, provided we use functions and operations that are differentiable.

*   Overfitting and under fitting tradeoff are also faced by neural networks, and these are mitigated by proper regularization techniques and adjusting model capacity.

# [Further Reading](#toc.xhtml#s233a)

*   **[http://cs231n.stanford.edu/slides/2018/cs231n\_2018\_ds02.pdf](http://cs231n.stanford.edu/slides/2018/cs231n_2018_ds02.pdf)**

*   **[http://cs231n.stanford.edu/vecDerivs.pdf](http://cs231n.stanford.edu/vecDerivs.pdf)**

*   **[https://www.jeremyjordan.me/neural-networks-training/](https://www.jeremyjordan.me/neural-networks-training/)**

*   **[https://papers.nips.cc/paper/2018/file/d54e99a6c03704e95e6965532dec148b-Paper.pdf](https://papers.nips.cc/paper/2018/file/d54e99a6c03704e95e6965532dec148b-Paper.pdf)**

*   **[https://mi.nemzetilabor.hu/sites/default/files/2020-12/milab\_lipreg.pdf](https://mi.nemzetilabor.hu/sites/default/files/2020-12/milab_lipreg.pdf)**

*   *Deep Learning Book*: *Ian Goodfellow* and *Yoshua Bengio* and *Aaron Courville*

# [CHAPTER 7](#toc.xhtml#c07)

# [Clustering](#toc.xhtml#c07)

**Clustering** is about automatically discovering natural groups/clusters in unlabeled data such that the degree of similarity between samples of the same cluster and the degree of dissimilarity between samples of different clusters is maximized. It is one of the unsupervised learning techniques where learning is based on unlabeled data. Let us understand this with an example.

A company wants to grow its business. To grow the business, the company has decided to group customers so that offers can be fine-tuned to each group. The company doesn’t have specific rules to decide the group of a customer. It wants to find groups that are natural and have similar buying patterns so that the offers can be fine-tuned to enhance the buying experience of their products. The process of finding the groups, also called clusters, by analyzing the unlabeled data to find natural patterns is called **clustering analysis**.

Data samples with similar patterns can form one group called *cluster*. Now, we can rephrase the company’s project as finding clusters among customers so that the offers can be fine-tuned for each cluster to grow the business. There are other areas where clustering analysis brings value, like anomaly detection, genetics, pharmacy, and document information retrieval.

Anomaly detection includes fraud detection of financial transaction, labelling newly produced mechanical item as defective and many others. In genetics, clustering analysis can be used to identify DNA that produces similar behavioral patterns in animals. In turn, it helps to understand the evolution of living things on earth. In pharmacy, proven medicines and newly discovered drugs are clustered. One among the many newly discovered drugs is selected, which is closest to the proven drug cluster. The selected new drug is then used for next stage experimentation. This helps to pick the best suited drug for a disease with less time and resources.

There are numerous clustering algorithms with applications in various domains for analysis. In this chapter, we will discuss popular algorithms belonging to different clustering categories. Along with algorithms, we will discuss cluster evaluation methods necessary for the comparison of clustering algorithms.

# [Structure](#toc.xhtml#s234a)

In this chapter, we will cover the following topics:

*   Defining cluster and approaches to form clusters

*   Similarity and dissimilarity metrics

*   Evaluation of clustering algorithms

*   Categories of clustering algorithms

*   Few popular algorithms in each category

# [Objectives](#toc.xhtml#s235a)

After going through this chapter, you will be able to understand the meaning of a cluster and the domains where clustering algorithms can be applied. You will learn about the different categories of clustering algorithms, along with a few popular algorithms under each category. You will learn about the metric to measure similarity or dissimilarity between data samples. You will also be introduced to various evaluation techniques applicable for clustering algorithms.

# [Forming clusters](#toc.xhtml#s236a)

Clustering is an unsupervised learning technique that identifies natural clusters such that the degree of similarity between samples of the same cluster and the degree of dissimilarity between samples of different clusters is maximized. Similarity and dissimilarity criteria can vary based on the problem statement and the clustering algorithm.

Grouping of data samples result in a cluster. Definition of a cluster varies based on the algorithm due to the similarity/dissimilarity metrics chosen. The objective of all algorithms remains the same: group all the samples that possess similar characteristics into one cluster and those with dissimilar characteristics to different clusters. The approach of forming clusters by assigning data samples can be broadly classified into two categories:
