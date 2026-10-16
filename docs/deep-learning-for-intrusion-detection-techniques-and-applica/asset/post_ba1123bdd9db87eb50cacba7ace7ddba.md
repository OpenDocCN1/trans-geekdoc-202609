
suspicious activities. In fact, for the purpose of predicting the data labels specific to any particular application, the training phase is generalized and it makes use of subject matter experts to learn their labeling behavior. The common supervised ML algorithms are as follows:

- K-nearest neighbors
- Local outlier factor
- Bayesian
- Support vector machines (SVMs), and
- Decision trees

Unsupervised learning aims to reduce dimensions by similarity-based data separation, extracting features, and clustering. Some of the unsupervised AD algorithms are as follows:

- K-means
- Autoencoders
- Gaussian mixture models
- Principal component analysis, and
- Hypothesis tests-based analysis

In RL, an intelligent agent interacts with the environment and is trained to learn optimal policy by performing optimal action and receiving maximized long-term cumulative reward. Performances of unsupervised ML algorithms [7] are limited by the massive volume of unlabelled datasets. Hence, in recent years, deep reinforcement learning (DRL) has been trending for AD as it outperforms ML and DL techniques in many ways.

Some of the most common recently used AI-based AD methods are as follows:

- AEs
- GANs
- OCC
- DRL
- RNN
- Transfer learning, and so on

The following subsections elaborate on the above-mentioned popular AI-based AD methods tried for AD in various application domains.

## 8.2 Autoencoder-Based Anomaly Detection

Autoencoder (AE) is a powerful technique that combines generative and probabilistic variational modeling with deep architecture. An AE aims to learn the underlying data distribution to generate consequential sample data [8]. A standard AE has encoder and decoder parts that can be either recurrent neural networks (RNNs) when dealing with time series sequential datasets or convolutional neural networks (CNNs) when dealing with image datasets. The encoder part has an input layer and a hidden layer with bottleneck a.k.a latent space layer as the final hidden layer. The raw input data is given to the input layer and the hidden layer progressively compresses the dimensionality of the input and captures important features and patterns. The decoder reconstructs the input by demapping the code to an output [9].

The AE’s representation learning strategy can be used for dimensionality reduction, denoising, or even generative applications. The architecture is generally trained end-to-end by optimizing the input reconstruction, i.e., by minimizing a loss that measures a difference between the model’s output and the input. It can be trained with any unlabeled data. AEs can be used as techniques for unsupervised or semi-supervised AD. The AE has a very high receiver operating characteristic area under the curve (AUC ROC) without making any use of labeled datasets during training [10].

### 8.2.1 Types of Autoencoders

- Classical AE
- Denoising AE (DAE)
- Stacked convolutional AE (scAE)
- Robust deep AE (RDA)
- Variational AE (VAE)

### Classical Autoencoder Models

The input and output layers are of the same dimension as the data, while intermediate layers introduce smaller dimensions to create a bottleneck. This bottleneck forces the network to learn a compressed representation of the input data, capturing its essential features.

### Denoising Autoencoder (DAE)

Denoising AEs are designed to reconstruct clean data from corrupted inputs, making them robust to noise and enhancing their generalization capabilities.

### Stacked Convolutional Autoencoder (scAE)

It uses convolutional layers to capture spatial dependencies and hierarchical features in the input data, making them particularly effective for image-related tasks.

### Robust Deep Autoencoder (RDA)

An RDA aims to enhance the robustness of AE models to outliers and anomalies in the input data.

### Variational Autoencoder (VAE)

A VAE represents a class of generative probabilistic models that extend the functionality of classical AEs and offer an elegant solution by simultaneously compressing data into a latent space and reconstructing it from its compressed form, effectively capturing tangled data distributions while maintaining interpretability. A VAE operates by encoding input data into a latent space and then reconstructing it. Variational AEs introduce a probabilistic interpretation of the latent space, enabling them to generate new data samples by sampling from the learned latent distribution [11].

A VAE with GAN has a remarkable ability to learn complex latent representations and reconstruct original inputs using the principles of generative modeling. Variational AEs can learn latent representation and thereby reconstruct data samples accurately. Variational AEs are robust and versatile in handling complex datasets and data distribution. They are easier to train and do not suffer from the mode collapse phenomenon. But they may be less accurate than GANs.

## 8.3 Generative Adversarial Networks Anomaly Detection

Generative adversarial networks (GANs) can generate hard-to-acquire anomalous data points as it has the ability of data augmentation and representative learning [12]. To overcome the difficulty of unavailability of data that represents anomalous behavior, GANs have recently been leveraged in application domains where AD is applied to images, such as the health sector, industrial manufacturing, video surveillance, etc.

### 8.3.1 Features of GANs

- They can generate new realistic-looking data and be used for data augmentation.
- They can perform representation learning.
- They learn the distribution of normal data so that it can be used to detect outliers or anomalous ones.
- They can be trained in an unsupervised manner to learn the real data distribution.
- They can also be used in semi-supervised and supervised AD processes, and for data augmentation.
- They leverage implicit density models.
- GANs use image datasets for AD processes.

The image datasets need to be pre-processed before being given as input to GANs. The data processing steps involve resizing, normalization, and cropping.

## 8 Exploring Advanced Artificial Intelligence for Anomaly Detection

There are three different GAN architectures used for AD as follows:

- Standard GANs
- Deep convolutional GANs
- Conditional GANs

Performance metrics to assess the GAN are as follows:

- Ability to generate synthetic/realistic-looking data (either by data augmentation or by representation learning)
- Structural similarity indices
- Peak signal-to-noise ratio (SNR)
- Area under the receiver operating characteristics curve (AUC-ROC)

### 8.3.2 Working Principle of GANs

The general framework of GAN has two deep neural networks (DNN) models such as follows:

- Generative DNN (G-GAN) model
- Discriminator DNN (D-DNN) model

The G-GAN is provided with a random noise vector as input and is trained to learn the real normal data distribution and to generate real-looking fake examples that are indistinguishable from the real normal data. The D-DNN is provided with the fake examples generated by the G-GAN and the real normal data. The D-DNN performs a binary decision by comparing its inputs and generates the classification error as output. Both the G-GAN and D-DNN are iteratively trained to tune their weights and biases until reaching a Nash equilibrium [13].

The iterative training process includes two loops namely the inner loop and the outer loop. In the inner loop, the D-DNN parameters are tuned to maximize classification accuracy in predicting correct labels for the real data and generated fake examples, whereas in the outer loop, the G-GAN parameters are tuned to generate the real-looking fake examples as indistinguishable from the real normal data [14]. The training of GAN is considered a zero-sum game problem in which the Nash equilibrium is reached once neither of the players can improve the situation. That is, the fake examples generated could not be distinguished from the real normal data by the D-DNN [15].

The semi-supervised AD systems leverage standard GANs, deep convolutional GANs, and unsupervised GANs for AD, whereas the unsupervised AD systems prefer to use standard GANs and compare its performance with AE-based AD approaches. The supervised AD systems use GANs to augment the dataset for the anomalous class [16].

GANs are leveraged for AD in applications with image datasets such as medicine, surveillance, and ID.
