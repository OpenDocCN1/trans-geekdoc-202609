
PWCCA enjoys somewhat widespread use in representational similarity literature, but it has potentially undesirable properties. First, it is asymmetric; its value depends on which of the two representations is used for the weighting. Second, it is unclear why weightings should be determined using the $L^1$ norm, which is not invariant to rotations of the representation. It is arguably more intuitive to weight the correlations directly by the amount of variance in the representation that the canonical component explains, which corresponds to replacing the $L^1$ norm with the squared $L^2$ norm. The resulting similarity measure is

```
$R^2_{\text{LR}}(\mathbf{X}, \mathbf{Y}) = \frac{\sum_{i=1}^p \alpha'_i \rho_i^2}{\sum_{i=1}^p \alpha'_i}, \qquad \alpha'_i = \sum_{j=1}^{p_2} \|(\mathbf{Y} \mathbf{w}'_i)^\top \mathbf{Y}\|_2^2. \quad (32.8)$
```

As shown by Kornblith et al. [Kor+19], when $p_2 \ge p_1$, this alternative similarity measure is equivalent to the overall variance explained by using linear regression to fit every neuron in $\tilde{\mathbf{Y}}$ using the representation $\tilde{\mathbf{X}},$

```
$R^2_{\text{LR}}(\mathbf{X}, \mathbf{Y}) = 1 - \sum_{i=1}^{p_2} \min_\beta \|\tilde{\mathbf{Y}}_{:,i} - \tilde{\mathbf{X}} \beta\|^2 / \|\tilde{\mathbf{Y}}\|_\text{F}^2. \quad (32.9)$
```

Finally, there is also a close relationship between CCA and linear CKA. This relationship can be clarified by writing similarity indexes directly in terms of the singular value decompositions $\tilde{\mathbf{X}} = \mathbf{U} \mathbf{\Sigma} \mathbf{V}^\top$ and $\tilde{\mathbf{Y}} = \mathbf{U}' \mathbf{\Sigma}' \mathbf{V}'^\top$. The left-singular vectors $\mathbf{u}_i = \mathbf{U}_{:,i}$ correspond to the principal components of $\mathbf{X}$ normalized to unit length, and the squared singular values $\lambda_i = \Sigma_{ii}^2$ are the amount of variance that those principal components explain (up to a factor of $1/n$). Given these singular value decompositions, $R^2_{\text{CCA}}$, $R^2_{\text{LR}}$, and linear CKA become:

```
$R^2_{\text{CCA}}(\mathbf{X}, \mathbf{Y}) = \sum_{i=1}^{p_1} \sum_{j=1}^{p_2} (\mathbf{u}_i^\top \mathbf{u}'_j)^2 / p_1 \quad (32.10)$
```

```
$R^2_{\text{LR}}(\mathbf{X}, \mathbf{Y}) = \sum_{i=1}^{p_2} \sum_{j=1}^{p_2} \lambda'_j (\mathbf{u}_i^\top \mathbf{u}'_j)^2 \big/ \sum_{j=1}^{p_2} \lambda'_j \quad (32.11)$
```

```
$\text{CKA}_\text{linear}(\mathbf{X}, \mathbf{Y}) = \frac{\sum_{i=1}^{p_1} \sum_{j=1}^{p_2} \lambda_i \lambda'_j (\mathbf{u}_i^\top \mathbf{u}'_j)^2}{\sqrt{\sum_{i=1}^{p_1} \lambda_i^2} \sqrt{\sum_{j=1}^{p_2} \lambda'_j^2}}. \quad (32.12)$
```

Thus, these similarity indexes all involve the similarities between all pairs of principal components from $\mathbf{X}$ and $\mathbf{Y}$, but place different weightings on these similarities according to the fraction of variance that these principal components explain.

### 32.2.2.3 Comparing representational similarity measures

What properties are desirable in a representational similarity measure is an open question, and this question may not have a unique answer. Whereas evaluations of downstream accuracy approximate real-world use cases for neural network representations, the goal of representational similarity is instead to develop understanding of how representations evolve across neural networks, or how they differ between neural networks with different architectures or training settings.

One way to taxonomize different similarity measures is through the transformations of a representation that they are invariant to. The minimum form of invariance is invariance to permutation of a representation's constituent neurons, which is needed because neurons in neural networks generally have no canonical ordering: for commonly-used initialization strategies, any permutation of a given initialization is equiprobable, and nearly all architectures and optimizers produce training trajectories that are equivariant under permutation. On the other hand, invariance to arbitrary invertible transformations, as provided by mutual information, is clearly undesirable, since many realistic neural networks are injective functions of the input [Gol+19] and thus there always exists an invertible transformation between any pair of representations. In practice, most similarity measures in common use are invariant to rotations (orthogonal transformations) of representations, which implies invariance to permutation. Similarity measures based solely on CCA correlations, such as \( R^2_{CCA} \) and \( \bar{\rho} \), are invariant to all invertible linear transformations of representations. However, SVCCA and PWCCA are not.

A different way to distinguish similarity measures is to investigate situations where we know the relationships among representations and to empirically evaluate their ability to recover these relationships. Kornblith et al. [Kor+19] propose a simple “sanity check”: Given two architecturally identical networks A and B trained from different random initializations, any layer in network A should be more similar to the architecturally corresponding layer in network B than to any other layer. They show that, when considering flattened representations of CNNs, similarity measures based on centered kernel alignment satisfying this sanity check whereas other similarity measures do not. By contrast, when considering representations of individual tokens in Transformers, all similarity measures perform reasonably well. However, Maheswaranathan et al. [Mah+19] show that both CCA and linear CKA are highly sensitive to seemingly innocuous RNN design choices such as the activation function, even though analysis of the fixed points of the dynamics of different networks suggests they all operate similarly.

## 32.3 Approaches for learning representations

The goal of representation learning is to learn a transformation of the inputs that makes it easier to solve future tasks. Typically the tasks we want the representation to be useful for are not known when learning the representation, so we cannot directly train to improve performance on the task. Learning such generic representations requires collecting large-scale unlabeled or weakly-labeled datasets, and identifying tasks or priors for the representations that one can solve without direct access to the downstream tasks. Most methods focus on learning a parametric mapping \( z = f_\theta(x) \) that takes an input \( x \) and transforms it into a representation \( z \) using a neural network with parameters \( \theta \).

The main challenge in representation learning is coming up with a task that requires learning a good representation to solve. If the task is too easy, then it can be solved without learning an interesting transformation of the inputs, or by learning a _shortcut_. If a task is too different from the downstream task that the representation will be evaluated on, then the representation may also not be useful. For example, if the downstream task is object detection, then the representation needs to encode both the identity and location of objects in the image. However, if we only care about classification, then the representation can discard information about position. This leads to approaches for learning representations that are often not generic: different training tasks may perform better for different downstream tasks.

![](img/ca72c1626f4850f058a9edc138c1ac73_1078_0.png)

Figure 32.2: Approaches for representation learning from images. An input image is encoded through a deep neural network (green) to produce a representation (blue). An additional shallow or deep neural network (yellow) is often used to train the representation, but is thrown out after the representation is learned when solving downstream tasks. In the supervised case, the mapping from the representation to logits is typically linear, while for autoencoders the mapping from representation to images can be highly complex and stochastic. Unlike supervised or generative approaches, contrastive methods rely on other datapoints in the form of positive pairs (often created through data augmentation) and negative pairs (typically other datapoints) to learn a representation.

In Figure 32.2, we outline three approaches we will discuss for representation learning. Supervised approaches train on large-scale supervised or weakly-supervised data using standard supervised losses. Generative approaches aim to learn generative models of the dataset or parts of a dataset. Self-supervised approaches are based on transformation prediction or multi-view learning, where we design a task that where labels can be easily synthesized without needing human input.

### 32.3.1 Supervised representation learning and transfer

The first major successes in visual representation learning with deep learning came from networks trained on large labeled datasets. Following the discovery that supervised deep neural networks could outperform classical computer vision models for natural image classification [KSH12b; CMS12], it became clear that the representations learned by these networks could outperform handcrafted features used across a wide variety of tasks [Don+14; SR+14; Oqu+14; Gir+14]. Although unsupervised visual representation learning has recently achieved competitive results on many domains, supervised representation learning remains the dominant approach.

Larger networks trained on larger datasets generally achieve better performance on both pretraining and downstream tasks. When other design choices are held fixed, architectures that achieve higher accuracy during pretraining on natural image datasets such as ImageNet also learn better representations for downstream natural image tasks, as measured by both linear evaluation and fine-tuned accuracy [KSL19; TL19; Zha+19a; Zha+21; Abn+21]. However, when the domain shift from the pretraining task to the downstream task becomes larger (e.g., from ImageNet to medical imaging), the correlation between pretraining and downstream accuracy can be much lower [Rag+19;
