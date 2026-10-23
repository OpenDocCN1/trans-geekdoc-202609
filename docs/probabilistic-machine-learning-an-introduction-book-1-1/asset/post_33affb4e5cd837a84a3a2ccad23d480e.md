
where $\hat{e}_i = \hat{e}_\theta(x_i)$, etc. Using the triangle inequality we have

$$\|\hat{e}_i - \hat{e}_j\| \leq \|\hat{e}_i - c_{y_i}\| + \|\hat{e}_j - c_{y_i}\| \tag{16.18}$$

$$\|\hat{e}_i - \hat{e}_k\| \geq \|\hat{e}_i - c_{y_k}\| - \|\hat{e}_k - c_{y_k}\| \tag{16.19}$$

Hence

$$\ell_t(x_i,x_j,x_k) \leq \ell_u(x_i,x_j,x_k) \triangleq \|\hat{e}_i-c_{y_i}\| - \|\hat{e}_k-c_{y_k}\| + \|\hat{e}_j-c_{y_i}\| + \|\hat{e}_k-c_{y_k}\| \tag{16.20}$$

We can use this to derive a tractable upper bound on the triplet loss as follows:

$$\mathcal{L}_t(\mathcal{D},\mathcal{S}) = \sum_{(i,j)\in\mathcal{S},(i,k)\notin\mathcal{S},i,j,k\in\{1,\ldots,N\}} \ell_t(x_i,x_j,x_k) \leq \sum_{(i,j)\in\mathcal{S},(i,k)\notin\mathcal{S},i,j,k\in\{1,\ldots,N\}} \ell_u(x_i,x_j,x_k) \tag{16.21}$$

$$= C'\sum_{i=1}^{N}\left(\|x_i-c_{y_i}\| - \frac{1}{3(C-1)}\sum_{m=1,m\neq y_i}^{C}\|x_i-c_m\|\right) \triangleq \mathcal{L}_u(\mathcal{D},\mathcal{S}) \tag{16.22}$$

where $C' = 3(C-1)\left(\frac{N}{C}-1\right)\frac{N}{C}$ is a constant. It is clear that $\mathcal{L}_u$ can be computed in $O(NC)$ time. See Fig. [16.6b](#) for an illustration.

In [Do+19], they show that $0 \leq \mathcal{L}_t - \mathcal{L}_u \leq \frac{N^3}{C^2}K$, where $K$ is some constant that depends on the spread of the centroids. To ensure the bound is tight, the centroids should be as far from each other as possible and the distances between them should be as similar as possible. An easy way to ensure this is to define the $c_m$ vectors to be one-hot vectors, one per class. These vectors already have unit norm, and are orthogonal to each other. The distance between each pair of centroids is $\sqrt{2}$, which ensures the upper bound is fairly tight.

The downside of this approach is that it assumes the embedding layer is $L=C$ dimensional. There are two solutions to this. First, after training, we can add a linear projection layer to map from $C$ to $L \neq C$, or we can take the second-to-last layer of the embedding network. The second approach is to sample a large number of points on the $L$-dimensional unit hyper-sphere (which we can do by sampling from the standard normal, and then normalizing [Mar+72]), and then running K-means clustering (Sec. [2.13](#)) with $K=C$. In the experiments reported in [Do+19], these two approaches give similar results.

Interestingly, in [Rot+20], they show that increasing $\pi_{\mathrm{intra}}/\pi_{\mathrm{inter}}$ results in improved downstream performance on various retrieval tasks, where

$$\pi_{\mathrm{intra}} = \frac{1}{Z_{\mathrm{intra}}}\sum_{c=1}^{C}\sum_{i\neq j:y_i=y_j=c} d(x_i,x_j) \tag{16.23}$$

is the average intra-class distance, and

$$\pi_{\mathrm{inter}} = \frac{1}{Z_{\mathrm{inter}}}\sum_{c=1}^{C}\sum_{c'=1}^{C} d(\mu_c,\mu_{c'}) \tag{16.24}$$

is the average inter-class distance, where $\mu_c = \frac{1}{Z_c}\sum_{i:y_i=c}\hat{e}_i$ is the mean embedding for examples from class $c$. This suggests that we should not only keep the centroids far apart (in order to maximize the numerator), but we should also prevent examples from getting too close to their centroids (in order to minimize the denominator); this latter term is not captured in the method of [Do+19].

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_539_0.png)

*Figure 16.7: Adding spherical embedding constraint to a deep metric learning method. Used with kind permission of Dingyi Zhang.*

## 16.2.6 Other training tricks for DML

Besides the speedup tricks in Sec. 16.2.5, there are a lot of other details that are important to get right in order to ensure good DML performance. Many of these details are discussed in [MBL20; Rot+20]. Here we just briefly mention a few.

One important issue is how the minibatches are created. In classification problems (at least with balanced classes), selecting examples at random from the training set is usually sufficient. However, for DML, we need to ensure that each example has some other examples in the minibatch that are similar to it, as well as some others that are dissimilar to it. One approach is to use hard mining techniques (Sec. 16.2.5.1). Another idea is to use coreset methods applied to previously learned embeddings to select a diverse minibatch at each step [Sin+20]. However, [Rot+20] show that the following simple strategy also works well for creating each batch: pick $B/n$ classes, and then pick $N_c$ examples randomly from each class, where $B$ is the batch size, and $N_c = 2$ is a tuning parameter.

Another important issue is avoiding overfitting. Since most datasets used in the DML literature are small, it is standard to use an image classifier, such as GoogLeNet (Sec. 14.3.2.3) or ResNet (Sec. 14.3.2.4), which has been pre-trained on ImageNet, and then to fine-tune the model using the DML loss. (See Sec. 19.2 for more details on this kind of transfer learning.) In addition, it is standard to use data augmentation (see Sec. 19.1). (Indeed, with some self-supervised learning methods, data aug is the only way to create similar pairs.)

In [ZLZ20], they propose to add a spherical embedding constraint (SEC), which is an additional batchwise regularization term, which encourages all the examples to have the same norm. That is, the regularizer is just the empirical variance of the norms of the (unnormalized) embeddings in that batch. See Fig. 16.7 for an illustration. This regularizer can be added to any of the existing DML losses to modestly improve training speed and stability, as well as final performance, analogously to how batchnorm (Sec. 13.4.5) is used.

## 16.3 Kernel density estimation (KDE)

In this section, we consider a form of non-parametric density estimation known as kernel density estimation or KDE. This is a form of generative model, since it defines a probability distribution $p(x)$ that can be evaluated pointwise, and which can be sampled from to generate new data.

### 16.3.1 Density kernels

Before explaining KDE, we must define what we mean by a “kernel”. This term has several different meanings in machine learning and statistics.¹ In this section, we use a specific kind of kernel which we refer to as a **density kernel**. This is a function $\mathcal{K} : \mathbb{R} \to \mathbb{R}_+$ such that $\int \mathcal{K}(x)dx = 1$ and $\mathcal{K}(-x) = \mathcal{K}(x)$. This latter symmetry property implies the $\int x\mathcal{K}(x)dx = 0$, and hence

$\displaystyle \int x\mathcal{K}(x - x_n)dx = x_n$  (16.25)

A simple example of such a kernel is the **boxcar kernel**, which is the uniform distribution within the unit interval around the origin:

$\displaystyle \mathcal{K}(x) \triangleq 0.5\,\mathbb{I}(|x| \le 1)$  (16.26)

Another example is the **Gaussian kernel**:

$\displaystyle \mathcal{K}(x) = \frac{1}{(2\pi)^{1/2}} e^{-x^2/2}$  (16.27)

We can control the width of the kernel by introducing a **bandwidth** parameter $h$:

$\displaystyle \mathcal{K}_h(x) \triangleq \frac{1}{h}\mathcal{K}\left(\frac{x}{h}\right)$  (16.28)

We can generalize to vector valued inputs by defining a **radial basis function** or **RBF** kernel:

$\displaystyle \mathcal{K}_h(\mathbf{x}) \propto \mathcal{K}_h(\|\mathbf{x}\|)$  (16.29)

In the case of the Gaussian kernel, this becomes

$\displaystyle \mathcal{K}_h(\mathbf{x}) = \frac{1}{h^D (2\pi)^{D/2}} \prod_{d=1}^{D} \exp\left(-\frac{1}{2h^2} x_d^2\right)$  (16.30)

Although Gaussian kernels are popular, they have unbounded support. Some alternative kernels, which have compact support (which can be computationally faster), are listed in Table 16.1. See Fig. 16.8 for a plot of these kernel functions.

### 16.3.2 Parzen window density estimator

To explain how to use kernels to define a nonparametric density estimate, recall the form of the Gaussian mixture model from Sec. 3.7.1. If we assume a fixed spherical Gaussian covariance and uniform mixture weights, we get

$\displaystyle p(\mathbf{x}|\boldsymbol{\theta}) = \frac{1}{K} \sum_{k=1}^{K} \mathcal{N}(\mathbf{x}|\boldsymbol{\mu}_k, \sigma^2\mathbf{I})$  (16.31)
