# Deep Neural Networks-Enabled Intelligent Fault Diagnosis of Mechanical Systems

Updating model parameters based on the objective function is to train GAN stochastic gradient descent (SGD) and achieve proper pair of discriminator and generator.

# Auxiliary Generative Adversarial Networks

A variant architecture of the regular GAN is achieved by leveraging additional class labels for both discriminator and generator, as show in Figure 5.1(b). Class conditional generation process is able to improve the quality of generated data. In addition, the discriminator is combined with an auxiliary part to output specific class so that the improved discriminator can not only recognize data source, but also differentiate among classes. This variant that combines class conditional architecture and auxiliary network for classification is called auxiliary generative adversarial network (ACGAN).

Compared with regular GANs, ACAGANS are able to generate high-quality data and provide label information simultaneously. Mathematically, generator leverages both noise z and label l to produce artificial samples $x_{generated}=G(z, l)$, and discriminator outputs probability over data sources and labels. the objective function contains two pair-likelihoods corresponding to correct data source and correct class label, as follows:

```
$L_{Source}=E_{x_{real}}[\log p(s|x_{real})]+E_{P(z)}[\log p(s|x_{generated})]$ (5.3)
```

```
$L_{Class}=E_{x_{real}}[\log p(c|x_{real})]+E_{P(z)}[\log p(c|x_{generated})]$ (5.4)
```

For discriminator, training goal is to maximize both-likelihood $L_{Source}+L_{Class}$, while generator is trained to maximize $L_{Class}-L_{Source}$.

The improved architecture ACAGANS can generate data samples with better quality owing to additional class label information, so that it is suitable for supervised classification tasks.

# Similarity Evaluation Criteria

The goal of using GAN architecture is to generating convincing samples to realize data augmentation, therefore, the quality of generated data samples is significant. It is important to evaluate the similarity between generated data and the real data. Evaluation for GAN architecture is still an open issue and several evaluation metrics are to provide quantitative assessment, including inception score (IS) (Salimans et al. 2016), the Frechet inception distance (FID) (Heusel et al. 2017), and Wasserstein distance (SWD) (Peyré and Curhoy 2019). For conventional image generation tasks, it is also possible to conduct visual evaluation. However, for time-series signals, especially mechanical sensor signals, it is not suitable to directly calculate the score using model pre-trained on natural images, and considering the inherent property of sensor data, time domain features and frequency distribution is able to reflect signal characteristics to some degree. Hence, the evaluation is designed based on these statistical characteristics. In this chapter, we demonstrate two types of approaches to assess the performance of generative model: statistical indicators and experimental verification.

For the statistical features, Euclidean distance (ED), Pearson correlation coefficient (PCC), and Kullback-Leibler (K-L) divergence are introduced here to evaluate the similarity