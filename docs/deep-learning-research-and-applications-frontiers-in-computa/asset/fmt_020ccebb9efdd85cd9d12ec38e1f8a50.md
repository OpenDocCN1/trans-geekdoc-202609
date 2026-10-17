
# Introduction to Developmental Dysgraphia

According to prior studies, it is believed that the presence of dysgraphia is common among children with average IQ level and is also found among those who have not been diagnosed with any neurological or perceptual motor disorders.

The risk of developmental dysgraphia in children with neurodevelopmental disabilities is very high \[[9](#bodymatter-005.xhtml#b_9783110670905-005_ref_009)\]. In school-going children the risk is comparatively low and the percentage lies between 10 and 30 \[[8](#bodymatter-005.xhtml#b_9783110670905-005_ref_008)\]. It is clinically proved that handwriting difficulty is capable of making serious impact on an individual’s overall academic performance, psychology, and behavior \[[10](#bodymatter-005.xhtml#b_9783110670905-005_ref_010)\]. Thus, it is important to detect developmental dysgraphia at the earliest, to prevent uncontrollable and undesired manifestation in the adult life \[[11](#bodymatter-005.xhtml#b_9783110670905-005_ref_011)\].

Scientific studies substantiate the utility of an automated system for recognizing the handwriting process and proceed with assessing the same to distinguish handwriting features of children suffering from dysgraphia \[[8](#bodymatter-005.xhtml#b_9783110670905-005_ref_008), [12](#bodymatter-005.xhtml#b_9783110670905-005_ref_012), [13](#bodymatter-005.xhtml#b_9783110670905-005_ref_013), [14](#bodymatter-005.xhtml#b_9783110670905-005_ref_014)\]. However, as perceived, concepts of deep learning will throw more light on the aspects of features and would be more effective to diagnose and identify handwriting defects among patients of dysgraphia.

Previously, a system of automatic rating of dysgraphia based on HPSQ total score estimation was developed using the concept of machine learning which implemented handwriting parameterization techniques and intrawriter normalization approach.

# Variational Autoencoder (VAE)

For the first time, in this chapter, VAE, a deep learning technique to compress data, is used to identify common handwriting features in dysgraphia patients. Deep learning is a subset of unsupervised learning, also termed as hierarchical learning which has created huge impact on the field of machine learning \[[15](#bodymatter-005.xhtml#b_9783110670905-005_ref_015)\]. AE typically comprises dense, fully connected layers of a feedforward neural network; it consists of an encoder network and a decoder network. The encoder is compared to a convolution neural network (CNN). The input is processed using several hidden layers “h” inside an autoencoder. The input is encoded into a much smaller representation as an output. The output received from the particular layer consists of sufficient suitable information to be processed in the next layer of the network to produce necessary output format. It simultaneously assimilates an inference model to deduce the latent features of image data and comprehends a generative model for generating images from those deduced latent features. The input image is encoded and decoded by VAE. Following this, clustering is implemented which may lead to loss of information. The similarities and dissimilarities among the various characters contained in the dataset are depicted as the output of clustering of characters. Identification of handwritings manually is comparatively easier than of identification done by machines since handwriting varies from individual to individual.

VAE is considered as a neural network which can encrypt image into a direction in the latent space of `z` real numbers. For the sample that has been collected from a `z`-dimensional normal distribution, the direction is assumed to be arbitrary. Then, the decoder network decodes the encoded vector representation and obtains the original image. Random samples can be drawn from the distribution and fetch them into decoder network for which the latent space is `z`-dimensional normal distribution. From this new images can be obtained that are absent in the dataset we trained on. The architecture of the encoder is represented in [Figure 5.1](#bodymatter-005.xhtml#b_9783110670905-005_fig_001).

![Figure 5.1: The simplest form of representation of the encoder architecture.](graphic/converted/b_9783110670905-005_fig_001.png)

Figure 5.1: The simplest form of representation of the encoder architecture.

The pivotal facet of the VAE lies in the fact that its latent representation, `y` ∈ℙ^K is derived from a particular Gaussian distribution (i.e., `p(y) = N(y| μ, Σ)`, where `μ` denotes mean and `Σ` denotes covariance). The VAE is trained in an unsupervised manner as the output is basically the reconstructed version of the input. Let us consider the given set of training data is `S = {s[n]}[n][=1]^N`, the VAE comprises of a probabilistic encoder `qθ(y|s)`, that finds the latent representation `y` for the given set of input data `s`. It also consists of a probabilistic decoder `pϕ(s|y)` which reconstructs the input data for the specific latent representation, where `θ` represents the network parameter for encoder and `ϕ` represents the network parameter for decoder.

Optimization of the variational bound `L[VAE](θ, ⌀)` with respect to the parameters `θ` and `ϕ` in the encoder and decoder occurs learning VAE.

(5.1)
```
L_VAE(θ, ∅) = ∑_{n-1}^{n} - E_y ~ qθ(y|s_n)[log p∅(s_n|y) + KL(qθ(y|s_n)||p(y))]
```

Here, the first term is the reconstruction error that has been computed by taking the expectation with respect to the distribution of `y` while the second term denotes regularizer which is the Kullback–Leibler (KL) divergence between the estimated distribution `qθ(y|s[n])` and the true distribution `p(y)`. This divergence is the measurement of the amount of information lost while using `q` to represent `p`. The estimation of parameters can be done using an autoencoding variational Bayes algorithm \[[16](#bodymatter-005.xhtml#b_9783110670905-005_ref_016)\].

The pictorial representation of an encoder and decoder is given in [Figure 5.2(a)](#bodymatter-005.xhtml#b_9783110670905-005_fig_002) and [(b)](#bodymatter-005.xhtml#b_9783110670905-005_fig_002), respectively.

![Figure 5.2: (a) The encoder is used to compress data into latent space (y). (b) The decoder is used for reconstruction of given data which is a hidden representation.](graphic/converted/b_9783110670905-005_fig_002.png)

Figure 5.2: (a) The encoder is used to compress data into latent space (`y`). (b) The decoder is used for reconstruction of given data which is a hidden representation.

The encoder is said to be a neural network whose input is a data point `s` while output is a hidden representation `y`, having weights and biases `θ`. Specifically saying, let us consider `y` to be a 15 by 15 pixel photo of a handwritten digit. The encoder “encodes” the data which is 225-dimensional into a latent (hidden) representation space `y`, which is much less than 225 dimensions. This is conventionally termed to be a “bottleneck” because the encoder must be capable of efficient compression of the data into this lower-dimensional space.

From [Figure 5.2](#bodymatter-005.xhtml#b_9783110670905-005_fig_002), we can consider or assume the encoder to be denoted as `qθ(y|s)`. We know that the lower-dimensional space is arbitrary: the parameters to `qθ(y|s)`, which is a Gaussian probability density, is the output of the encoder. Sampling of this distribution can be done to obtain the noisy values of the representations `y`.
