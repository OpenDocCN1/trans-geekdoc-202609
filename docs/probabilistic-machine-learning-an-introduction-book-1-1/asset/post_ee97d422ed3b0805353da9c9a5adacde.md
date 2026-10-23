
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_623_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_623_1.png)

Figure 19.5: Visualization of SimCLR training. Each input image in the minibatch is randomly modified in two different ways (using cropping (followed by resize), flipping, and color distortion), and then fed into a Siamese network. The embeddings (final layer) for each pair derived from the same image is forced to be close, whereas the embeddings for all other pairs are forced to be far. From https://ai.googleblog.com/2020/04/advancing-self-supervised-and-semi.html. Used with kind permission of Ting Chen.

Define the similarity between a pair of inputs as follows:

```
S_{ij} = \frac{\mathbf{z}_i^T \mathbf{z}_j}{||\mathbf{z}_i|| \ ||\mathbf{z}_j||} 
(19.4)
```

We now define the loss function for a positive pair (i, j) to be the normalized temperature cross-entropy (NT-Xent) loss, defined as follows:

```
\ell_{ij}(\theta) = - \log \frac{\exp(S_{ij}/\tau)}{\sum_{k=1}^{2N} \mathbb{I}(k \neq i) \exp(S_{ik}/\tau)} 
(19.5)
```

where \tau > 0 is a temperature parameter. (This is identical to the N-pairs loss discussed in Sec. 16.2.4.3, apart from the temperature term.) The final loss for a minibatch is given by

```
\mathcal{L}(\theta) = \sum_{i=1}^N \ell_{i, \text{pos}(i)}(\theta) 
(19.6)
```

The net effect is to pull similar pairs close together, and to force dissimilar pairs far apart, as illustrated in Fig. 19.5.

A critical ingredient to the success of SimCLR is the choice of data augmentation methods. By using random cropping, they can force the model to predict local views from global views, as well as to predict adjacent views of the same image (see Fig. 19.4). (After cropping, all images are resized back to the same size.) In addition, they randomly flip the image some fraction of the time.

However, it turns out that distinguishing positive pairs (from the same image) from negative crops (from different images) is often easy to do just based on color histograms. To prevent this kind of “cheating”, they also apply a random color distortion, thus cutting off this “short circuit”. The combination of random cropping and color distortion is found to work better than either method alone.

After training, the final $g$ mapping (known as the **projection head**) is thrown away, and we use $\mathbf{h}_i = f(\mathbf{x}_i)$ as our representation in downstream tasks. The reason this can help is that the mapping $\mathbf{z}_i = g(\mathbf{h}_i)$ might throw away information that is not necessary for the contrastive task, such as the color or orientation of objects. However, such information may be useful for downstream tasks, so it is better to keep it. (In [Che+20c], they propose SimCLR2, in which they take the middle of the projection head as their final representation layer; this is a “compromise” between using $f$ and $g \circ f$.)

SimCLR relies on large batch training, in order to ensure a sufficiently diverse set of negatives. When this is not possible, we can use a memory bank of past (negative) embeddings, which can be updated using exponential moving averaging (Sec. 4.6.2). This is known as **momentum contrastive learning** or MoCo [He+20].

## 19.2.4 Domain adaptation

Consider a problem in which we have inputs from different domains, such as a **source domain** $\mathcal{X}_s$ and **target domain** $\mathcal{X}_t$, but a common set of output labels, $\mathcal{Y}$. (This is the “dual” of transfer learning, since the input domains are different, but the output domains the same.) For example, the domains might be images from a computer graphics system and real images, or product reviews and movie reviews. We assume we do not have labeled examples from the target domain. Our goal is to fit the model on the source domain, and then modify its parameters so it works on the target domain. This is called (unsupervised) **domain adaptation** (see e.g., [KL19] for a review).

A common approach to this problem is to train the source classifier in such a way that it cannot distinguish whether the input is coming from the source or target distribution; in this case, it will only be able to use features that are common to both domains. This is called **domain adversarial learning** [Gan+16]. More formally, let $d_n \in \{s,t\}$ be a label that specifies if the data example $n$ comes from domain $s$ or $t$. We want to optimize

$$\min_{\phi} \max_{\theta} \frac{1}{N_s + N_t} \sum_{n \in \mathcal{D}_s,\mathcal{D}_t} \ell(d_n, f_{\theta}(\mathbf{x}_n)) + \frac{1}{N_s} \sum_{m \in \mathcal{D}_s} \ell(y_m, g_{\phi}(f_{\theta}(\mathbf{x}_m))) \tag{19.7}$$

where $N_s = |\mathcal{D}_s|$, $N_t = |\mathcal{D}_t|$, $f$ maps $\mathcal{X}_s \cup \mathcal{X}_t \to \mathcal{H}$, and $g$ maps $\mathcal{H} \to \mathcal{Y}_t$. The objective in Eq. (19.7) minimizes the loss on the desired task of classifying $y$, but *maximizes* the loss on the auxiliary task of classifying the source domain $d$. This can be implemented by the **gradient sign reversal** trick, and is related to GANs (generative adversarial networks). See e.g., [Csu17; Wu+19] for some other approaches to domain adaptation.

## 19.3 Meta-learning

The field of **meta learning**, also called **learning to learn** [TP97], is concerned with learning multiple related functions (often called “**tasks**”). For example, suppose we have a set of $J$ related datasets, $\{\mathcal{D}^j : j = 1 : J\}$, where $\mathcal{D}^j = \{(\mathbf{x}_n^j, y_n^j) : n = 1 : N_j\}$, $\mathbf{x}_n^j \sim p(\mathbf{x})$, and $y_n^j = f^j(\mathbf{x}_n^j)$. (For example, $p(\mathbf{x})$ could be a distribution over images, $f^1$ could be a function mapping images to dog breeds, $f^2$ could be a function mapping images to car types, etc.) We can apply this inner algorithm to generate a labeled set D_meta = {(D^j, f^j) : j = 1 : J}, which we can use to learn an outer or "meta" algorithm or function M̂ that maps a dataset to a prediction function, f̂^j = M̂(D^j) (c.f., [Min99]). By contrast, conventional supervised learning learns a function f̂ that maps a single example to a label, ŷ_n = f̂(x_n).

There are many other approaches to meta-learning (see e.g., [Van18] for a survey). In Sec. 19.3.1, we discuss one popular approach, known as MAML, which can be thought of as an approximate form of empirical Bayes in a hierarchical Bayesian model.

There are also many applications of meta-learning. We discuss one of the most popular examples in Sec. 19.4.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_625_0.png)

Figure 19.6: Graphical model corresponding to MAML. Left: generative model. Right: During meta-training, each of the task parameters θ_j's are updated using their local datasets. The indices j are over tasks (meta datasets), and i are over instances within each task. Solid shaded nodes are always observed; semi-shaded (striped) nodes are only observed during meta training time (i.e., not at test time). From Figure 1 of [FXL18]. Used with kind permission of Chelsea Finn.

### 19.3.1 Model-agnostic meta-learning (MAML)

A natural approach to meta learning is to use a hierarchical Bayesian model, as illustrated in Fig. 19.6. The parameters for each task θ_j are assumed to come from a common prior, p(θ_j|φ), which can be used to help pool statistical strength from multiple data-poor problems.

We could perform Bayesian inference for the task parameters θ_j and the shared hyper-parameters φ, but a more efficient approach is to use the following empirical Bayes (Sec. 7.5) approximation:

φ* = argmax_φ 1/J Σ_{j=1}^J log p(D_valid^j | θ̂_j(φ, D_train^j)) (19.8)

where θ̂_j = θ̂(φ, D_train^j) is a point estimate of the parameters for task j based on D_train^j and prior φ, and where we use a cross-validation approximation to the marginal likelihood (Sec. 7.6.4).

To compute the point estimate of the task parameters, θ̂_j, we use K steps of a gradient ascent procedure starting at φ with a learning rate of η. This can be shown to be equivalent to an
