# Chapter 14. Neural networks for images



In semantic segmentation, we attach a label to each pixel, but we do not group the pixels into objects. Thus the output has the same size as the input. By contrast, in instance segmentation, the goal is to predict the label and 2d shape of each object instance in the image, as illustrated in Fig. 14.23b. In this case there are a variable number of outputs. We can combine semantic segmentation of “stuff” and instance segmentation of “things” into a coherent framework called “panoptic segmentation” [Kir+19].





We can define a joint distribution over images and labels using p(x,y) = p(x)p(y|x), where p(y|x) is the CNN classifier, and p(x) is some prior over images. If we then clamp the class label to a specific value, we can create a conditional generative model using p(x|y = c) ∝ p(x)p(y = c|x). Note that the discriminative classifier p(y|x) was trained to “throw away” information, so p(y|x) is not an invertible function. Thus the prior term p(x) will play an important role in regularizing this process, as we see in Sec. 14.5.2.

One way to sample from this model is to use the Metropolis Hastings algorithm (Sec. 7.7.4), treating E_c(x) = log p(y = c|x) + log p(x) as the energy function. Since gradient information is available, we can use a proposal of the form q(x'|x) = N(μ(x), cI), where μ(x) = x + (ε/2) ∇ log E_c(x). This is called the Metropolis-adjusted Langevin algorithm (MALA). As an approximation, we can ignore the rejection step, and accept every proposal. This is called the unadjusted Langevin algorithm. In addition, we can scale the gradient of the log prior and log likelihood independently. Thus we get an update over the space of images that looks like a noisy version of SGD, except we take derivatives wrt the input pixels (using Eq. (13.49)), instead of the parameters:

```
x_{t+1} = x_t + \epsilon_1 \frac{\partial \log p(x_t)}{\partial x_t} + \epsilon_2 \frac{\partial \log p(y = c|x_t)}{\partial x_t} + \mathcal{N}(0, \epsilon_3 I) \quad (14.21)
```

We can interpret each term in this equation as follows: the \epsilon_1 term ensures the image is plausible under the prior, the \epsilon_2 term ensures the image is plausible under the likelihood, and the \epsilon_3 term is a noise term, in order to generate diverse samples. If we set \epsilon_3 = 0, the method becomes a deterministic algorithm to (approximately) generate the “most likely image” for this class.



In this section, we discuss various kinds of image priors that we can use to regularize the ill-posed problem of inverting a classifier. These priors, together with the image that we start the optimization