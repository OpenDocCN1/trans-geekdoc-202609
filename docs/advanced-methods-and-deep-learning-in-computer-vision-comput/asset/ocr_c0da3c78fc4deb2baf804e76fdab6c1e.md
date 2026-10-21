contrastive learning is employed to cluster features according to their semantics while tearing apart those of different classes.

# 8.3.3.4 New directions

Other novel ideas have been proposed in the continual learning literature both for dense and sparse tasks. Here, we present and discuss some of the most promising research directions.

**Weights Initialization** has been employed in Cermelli et al. (2020) to deal with the atypical behavior of the background class in the *disjoint* and *overlapped* scenarios. The authors initialize the classifier’s parameters for the novel classes in such a way that the probability of the background is uniformly spread among the novel classes, preventing the model to be biased toward the background class when dealing with unseen classes.

**Generative Replay** methods train generative models on the current data distribution; afterwards, it is possible to sample data from past experience when learning on new data. By learning on actual data mixed with artificially generated past data, they try to preserve past knowledge while learning the new task. The generative model is generally a GAN (Goodfellow et al., 2014) as in Wu et al. (2018) and Shin et al. (2017) or an auto-encoder as in Draelos et al. (2017) and Kamra et al. (2017). Notice that only the weak classification labeling is available for generated data and some pseudo-labels need to be estimated for segmentation.

**Webly-based Learning** models (Hou et al., 2018; Modolo and Ferrari, 2017), *i.e.*, models that learn from samples acquired via web searches, could be an extremely powerful tool to retrieve faithful past examples using as queries the label names of the old classes to preserve. Also in this case, only weak classification labels are available and some pseudo-labeling scheme need to be introduced.

# 8.4 Conclusion

Semantic image segmentation is an active research field aiming at detailed and accurate scene understanding. Being a dense labeling task, it brings additional complexity with respect to classical image classification problems. To solve this task many deep learning models have been proposed, however such architectures require large labeled training datasets and show bad adaptation capabilities to unseen domains or unseen tasks. To tackle these two aspects, a large research activity has been conducted on both domain adaptation and continual learning in the past few years. In this chapter, we discuss domain adaptation in its unsupervised form (*i.e.*, when no labeled data of the target domain is used for training) applied to the dense semantic segmentation task. Then, we showed that continual learning can be achieved in this task in various possible ways.

The algorithms developed so far are able to greatly alleviate the degradation even if they still need to acquire greater maturity before being applied in delicate real-world scenarios (such as in autonomous driving). Indeed, there still remain many challenges to address as regards both the adaptation of complex deep learning architectures across different tasks and domains and their ability to learn new concepts over time without forgetting previous knowledge.