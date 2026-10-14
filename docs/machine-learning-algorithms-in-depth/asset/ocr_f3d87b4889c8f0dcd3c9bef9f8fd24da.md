factored representation of the joint posterior distribution. This factorization significantly speeds up computation.

Next, we introduce the Kullback-Leibler (KL) divergence and use it to measure the proximity of our approximate distribution to the true posterior. Figure 1.7 shows the two versions of KL divergence.

![](bbox=[0.17, 0.22, 0.82, 0.36])

Figure 1.7 Forward KL (left) and reverse KL (right) approximate distribution q(x) fit to Gaussian mixture p(x)

The original distribution p(x) is a bimodal Gaussian distribution (aka Gaussian mixture with two components), while the approximating distribution q(x) is a unimodal Gaussian. As we can see from figure 1.7, we can approximate the distribution with two peaks either at the center with q(x) that has high variance, to capture the support of the bimodal distribution, or at one of its modes, as shown on the right. This is a result of forward and reverse KL divergence definitions in equation 1.7. As we’ll see in later chapters, by minimizing KL divergence, we effectively convert VI into an optimization problem.

KL(p||q) = Σ p(x) log p(x)/q(x)      KL(q||p) = Σ q(x) log q(x)/p(x)      (1.7)

# 1.4.2 Modern deep learning algorithms

Over the years, deep learning architecture has evolved from the basic building blocks of the LeNet CNN to visual transformer architectures. Certain architectural design themes, such as residual connections in the ResNet model, which became the standard architectural choice of modern neural networks of arbitrary depth, began to emerge. In the later chapters of this book, we’ll take a look at modern deep learning algorithms, including self-attention based transformers; generative models, such as variational autoencoders; and graph neural networks.

We will also discuss amortized variational inference, which is an interesting research area, as it combines the expressiveness and representation learning of deep neural networks with domain knowledge of probabilistic graphical models. We will see one such