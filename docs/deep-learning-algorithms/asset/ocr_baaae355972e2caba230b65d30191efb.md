# DESIGNING THE CLASSIFIER COMBINING UNSUPERVISED AND SUPERVISED LEARNING

Supervised learning systems are domain-specific and annotating a large-scale corpus for each domain is very expensive [46]. Recently, semi-supervised learning, which uses a large amount of unlabeled data together with labeled data to build better learners, has attracted more and more attention in pattern recognition and classification [47]. In the paper we design a novel classifier of semi-supervised learning, namely combining unsupervised and supervised learning—deep belief network embedded with Softmax regress (DBNESR) for FR. DBNESR first learns hierarchical representations of feature by greedy layer-wise unsupervised learning in a feed-forward (bottom-up) and back-forward (top-down) manner [48] and then makes more efficient classification with Softmax regress by supervised learning. Deep belief network (DBN) is a representative deep learning algorithm, has deep architecture that is composed of multiple levels of non-linear operations [49], which is expected to perform well in semi-supervised learning, because of its capability of modeling hard artificial intelligent tasks [50]. Softmax regression is a generalization of the logistic regression in many classification problems.

+   1) **Problem formulation:-** The dataset is represented as a matrix:

![](bbox=[0.1, 0.54, 0.45, 0.61])

where, N is the number of training samples, M is the number of test samples, D is the number of feature values in the dataset. Each column of X corresponds to a sample X. A sample which has all features is viewed as a vector in $\mathbb{R}^D$, where the jth coordinate corresponds to the jth feature.

Let Y be a set of labels correspond to L labeled training samples and is denoted as:

![](bbox=[0.1, 0.76, 0.45, 0.84])

where, C is the number of classes. Each column of Y is a vector in $\mathbb{R}^C$, where, the jth coordinate corresponds to the jth class: