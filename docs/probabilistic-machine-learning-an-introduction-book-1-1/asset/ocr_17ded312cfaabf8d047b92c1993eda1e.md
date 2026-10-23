![](bbox=[0.38, 0.11, 0.68, 0.28])

Figure 19.2: Illustration of transfer learning from dataset D_p to D_q using a neural network, in which the feature extractor is shared, but the final layer is domain specific. The parameters θ_1 are first trained on D_p, and then optionally fine-tuned on D_q. Thus the information in D_p is used to help the model work well on D_q, but not vice versa.

# 19.2 Transfer learning

Many data-poor tasks have some high-level structural similarity to other data-rich tasks. For example, consider the task of fine-grained visual classification of endangered bird species. Given that endangered birds are by definition rare, it is unlikely that a large quantity of diverse labeled images of these birds exist. However, birds bear many structural similarities across species - for example, most birds have wings, feathers, beaks, claws, etc. We therefore might expect that first training a model on a large dataset of non-endangered bird species and then continuing to train it on a small dataset of endangered species could produce better performance than training on the small dataset alone.

This is called transfer learning, since we are transferring information from one dataset to another, via a shared set of parameters. More precisely, we first perform a pre-training phase, in which we train a model with parameters θ on a large dataset D_p; this may be labeled or unlabeled. We then perform a second fine-tuning phase on the small labeled dataset D_q of interest. (The fact that the pre-training and fine-tuning tasks differ means that transfer learning is slightly different from semi-supervised learning, which we discuss in Sec. 19.6.) We discuss these two phases in more detail below, but for more information, see e.g., [Tan+18; Zhu+19] for recent surveys.

# 19.2.1 Fine-tuning

Suppose, for now, that we already have a pretrained classifier, p(y|x, θ_p), such as a CNN, that works well for inputs x ∈ X_p (e.g. natural images) and outputs y ∈ Y_p (e.g., ImageNet labels), where the data comes from a distribution p(x, y) similar to the one used in training. Now we want to create a new model q(y|x, θ_q) that works well for inputs x ∈ X_q (e.g. bird images) and outputs y ∈ Y_q (e.g., fine-grained bird labels). where the data comes from a distribution q(x, y) which may be different from p.

2. This section was coauthored with Colin Raffel.