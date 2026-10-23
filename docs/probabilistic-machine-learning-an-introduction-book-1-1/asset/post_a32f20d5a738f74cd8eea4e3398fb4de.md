
## Chapter 16. Exemplar-based methods

Distance between two points using the normalized Euclidean distance

$$d(\mathbf{x}_i, \mathbf{x}_j; \boldsymbol{\theta}) = \|\hat{\mathbf{e}}_i - \hat{\mathbf{e}}_j\|_2^2$$ (16.7)

where smaller values mean more similar, or the cosine similarity

$$d(\mathbf{x}_i, \mathbf{x}_j; \boldsymbol{\theta}) = \hat{\mathbf{e}}_i^\top \hat{\mathbf{e}}_j$$ (16.8)

where larger values mean more similar. (Cosine similarity measures the angle between the two vectors, as illustrated in Fig. 19.9.) These quantities are related via

$$\|\hat{\mathbf{e}}_i - \hat{\mathbf{e}}_j\|_2^2 = (\hat{\mathbf{e}}_i - \hat{\mathbf{e}}_j)^\top (\hat{\mathbf{e}}_i - \hat{\mathbf{e}}_j) = 2 - 2\hat{\mathbf{e}}_i^\top \hat{\mathbf{e}}_j$$ (16.9)

This overall approach is called deep metric learning or DML. The basic idea in DML is to learn the embedding function such that similar examples are closer than dissimilar examples. More precisely, we assume we have a labeled dataset, $\mathcal{D} = \{( \mathbf{x}_i, y_i ) : i = 1 : N \}$, from which we can derive a set of similar pairs, $\mathcal{S} = \{ (i, j) : y_i = y_j \}$. If $(i, j) \in \mathcal{S}$ but $(i, k) \notin \mathcal{S}$, then we assume that $\mathbf{x}_i$ and $\mathbf{x}_j$ should be close in embedding space, whereas $\mathbf{x}_i$ and $\mathbf{x}_k$ should be far. We discuss various ways to enforce this property below. Note that these methods also work when we do not have class labels, provided we have some other way of defining similar pairs. For example, in Sec. 19.2.3.3, we discuss self-supervised approaches to representation learning, that automatically create semantically similar pairs, and learn embeddings to force these pairs to be closer than unrelated pairs.

Before discussing DML in more detail, it is worth mentioning that many recent approaches to DML are not as good as they claim to be, as pointed out in [MBL20; Rot+20]. (The claims in some of these papers are often invalid due to improper experimental comparisons, a common flaw in contemporary ML research, as discussed in e.g., [BLV19; LS19d].) We therefore focus on (slightly) older and simpler methods, that tend to be more robust.

### 16.2.3 Classification losses

Suppose we have labeled data with C classes. Then we can fit a classification model in O(NC) time, and then reuse the hidden features as an embedding function. (It is common to use the second-to-last layer, since it generalizes better to new classes than the final layer.) This approach is simple and scalable. However, it only learns to embed examples on the correct side of a decision boundary, which does not necessarily result in similar examples being placed close together and dissimilar examples being placed far apart. In addition, this method cannot be used if we do not have labeled training data.

### 16.2.4 Ranking losses

In this section, we consider minimizing ranking loss, to ensure that similar examples are closer than dissimilar examples. Most of these methods do not need class labels (although we sometimes assume that labels exist as a notationally simple way to define similarity).

#### 16.2.4.3 N-pairs loss

One problem with the triplet loss is that each anchor is only compared to one negative example at a time. This might not provide a strong enough learning signal. One solution to this is to create a multi-class classification problem in which we create a set of N − 1 negatives and 1 positive for every anchor. This is called the N-pairs loss [Soh16]. More precisely, we define the following loss for each set:

$$\mathcal{L}(\theta;\mathbf{x}_i,\mathbf{x}_j^+,\{\mathbf{x}_k^-\}_{k=1}^{N-1}) = \log\left(1 + \sum_{k=1}^{N-1} \exp\big(\hat{\mathbf{e}}_\theta(\mathbf{x}_i)^\top \hat{\mathbf{e}}_\theta(\mathbf{x}_k^-) - \hat{\mathbf{e}}_\theta(\mathbf{x}_i)^\top \hat{\mathbf{e}}_\theta(\mathbf{x}_j^+)\big)\right)$$ (16.12)

$$= -\log\frac{\exp\big(\hat{\mathbf{e}}_\theta(\mathbf{x}_i)^\top \hat{\mathbf{e}}_\theta(\mathbf{x}_j^+)\big)}{\exp\big(\hat{\mathbf{e}}_\theta(\mathbf{x}_i)^\top \hat{\mathbf{e}}_\theta(\mathbf{x}_j^+)\big) + \sum_{k=1}^{N-1} \exp\big(\hat{\mathbf{e}}_\theta(\mathbf{x}_i)^\top \hat{\mathbf{e}}_\theta(\mathbf{x}_k^-)\big)}$$ (16.13)

Note that the N-pairs loss is the same as the InfoNCE loss used in the CPC paper [OLV18]. In [Che+20a], they propose a version where they scale the similarities by a temperature term; they call this the NT-Xent (normalized temperature-scaled cross-entropy) loss. We can view the temperature parameter as scaling the radius of the hypersphere on which the data lives.

When N = 2, the loss reduces to the logistic loss

$$\mathcal{L}(\theta;\mathbf{x},\mathbf{x}^+,\mathbf{x}_i) = \log\big(1 + \exp(\hat{\mathbf{e}}_\theta(\mathbf{x})^\top \hat{\mathbf{e}}_\theta(\mathbf{x}_i) - \hat{\mathbf{e}}_\theta(\mathbf{x})^\top \hat{\mathbf{e}}_\theta(\mathbf{x}^+))\big)$$ (16.14)

Compare this to the margin loss used by triplet learning (when m = 1):

$$\mathcal{L}(\theta;\mathbf{x},\mathbf{x}^+,\mathbf{x}^-) = \max\big(0, \hat{\mathbf{e}}(\mathbf{x})^\top \hat{\mathbf{e}}(\mathbf{x}^-) - \hat{\mathbf{e}}(\mathbf{x})^\top \hat{\mathbf{e}}(\mathbf{x}^+) + 1\big)$$ (16.15)

See Fig. 4.2 for a comparison of these two functions.

### 16.2.5 Speeding up ranking loss optimization

The main disadvantage of ranking loss is the O(N²) or O(N³) cost of computing the loss function, due to the need to compare all pairs or triples of examples. In this section, we discuss various speedup tricks.

#### 16.2.5.1 Mining techniques

A key insight is that we don’t need to consider all negative examples for each anchor, since most will be uninformative (i.e., will incur zero loss). Instead we can focus attention on negative examples which are closer to the anchor than its nearest positive example. These are called hard negatives, and are particularly useful for speeding up triplet loss.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_537_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_537_1.png)

Figure 16.6: Speeding up triplet loss minimization. (a) Illustration of hard vs easy negatives. Here a is the anchor point, p is a positive point, and n_i are negative points. Adapted from Figure 4 of [KB19]. (b) Standard triplet loss would take 8 × 3 × 4 = 96 calculations, whereas using a proxy loss (with one proxy per class) takes 8 × 2 = 16 calculations. From Figure 1 of [Do+19]. Used with kind permission of Gustavo Carneiro.

where \(m > 0\) is a margin parameter. See Fig. 16.6a for an illustration. This is the technique used by Google’s FaceNet model [SKP15], which learns an embedding function for faces, so it can cluster similar looking faces together, to which the user can attach a name.

In practice, the hard negatives are usually chosen from within the minibatch. This therefore requires large batch sizes to ensure sufficient diversity. Alternatively, we can have a separate process that continually updates the set of candidate hard negatives, as the distance measure evolves during training.

#### 16.2.5.2 Proxy methods

Triplet loss minimization is expensive even with hard negative mining (Sec. 16.2.5.1). Ideally we can find a method that is O(N) time, just like classification loss.

One such method, proposed in [MA+17], measures the distance between each anchor and a set of P proxies that represent each class, rather than directly measuring distance between examples. These proxies need to be updated online as the distance metric evolves during learning. The overall procedure takes O(NP²) time, where P ~ C.

More recently, [Qia+19] proposed to represent each class with multiple prototypes, while still achieving linear time complexity, using a soft triplet loss.

#### 16.2.5.3 Optimizing an upper bound

[Do+19] proposed a simple and fast method for optimizing the triplet loss. The key idea is to define one fixed proxy or centroid per class, and then to use distance to the proxy as an upper bound on the triplet loss.

More precisely, consider a simplified form of the triplet loss, without the margin term:

$$\ell_t(x_i, x_j, x_k) = \|\hat{\mathbf{e}}_i - \hat{\mathbf{e}}_j\|_2^2 - \|\hat{\mathbf{e}}_i - \hat{\mathbf{e}}_k\|_2^2$$ (16.17)
