# Neural Architecture Search for Intelligent Fault Diagnosis ■ 145

Forward Sampling from the Posterior Distributions Group
By optimizing the sampling distributions group, the posterior is obtained to estimate the uncertainty for model matching. Then the candidate architectures set can be sampled from the posterior via random sampling. There is no time sequence or dependency in the sampling, so it is convenient for parallel acceleration. In fact, strategic sampling approach is allowed, e.g., the margin-focused sampling strategy, but in practice, the random sampling is sufficient to fix the set. Two metrics, accuracy and sparseness, are used to evaluate the sampled architecture, where the accuracy is for the validation dataset, (Hoyer 2004):

```
$$\text{Sparseness}(\Lambda) := \sqrt{m - \frac{\sum_{i,j} (\Lambda_{i,j})^2}{\sqrt{m-1}}} \quad\quad\quad\quad (8.9)$
```

$m$ is the dimensionality of $\Lambda$ and $m$ is equal $14 \times 8$. Sorting by the sparseness of the sampling instance matrix, the deviation caused by sampling from the continuous space is reduced. It is worth pointing out the difference between our method and the stochastic neural architecture search (SNAS (Xie et al. 2018)). The sampling in our work is subject to the $\partial o$ principle where the posterior is Gaussian, and the uncertainty estimation of model matching is also given, whereas sampling in SNAS is realized by a random one-hot mask.

# EXPERIMENTAL STUDIES FOR AEROGENE BEVEL GEAR FAULT DIAGNOSIS

In this section, the aero own bevel dataset is collected and used to verify the performance of BDAS. The comparison experiments are carried out on four widely used models, i.e., the DCNN, VGG11, ResNet18 and Inception. The DCNN has a set of five convolutional layers. The VGG11, ResNet18 and Inception are directly copied from a benchmark study (Zhao et al. 2020). All the experiments are running on the Ubuntu 18.04 GNU/Linux and GeForce TITAN.

Experimental Description
Data Description

The gear is an important part of the aero own transmission system, so it is necessary to monitor its state. In the testing bench, we set up four groups of bevel experiments in different states, as shown in Figure 8.3, healthy state, tooth surface wear, bevel tooth and small collapse. The bevel gears corresponding to these states were manually preprocessed and set. Each of gears was operated over five rotations, respectively, as described in Table 8.1. The vibration signals were acquired by an acceleration sensor.

For each rotational speed, the ratio of training and test set is 2:1, and one sample has 1024 points without data normalization or augmentation. An illustration of the raw vibration signal in time domain is shown in Figure 8.4, and each segment represents a sample with 1024 points. Samples of different speeds in the same mode share the same