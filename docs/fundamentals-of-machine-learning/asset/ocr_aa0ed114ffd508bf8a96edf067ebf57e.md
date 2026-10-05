could generate outputs with the decoder so that autoencoders could be seen as generative models. However, the question is how to generate this variation in a way in order to generate novel examples which still represent the expected distribution of a target class. We usually do not know much about the structure of the latent space which prevents us from making systematic variations.

![](bbox=[0.186, 0.222, 0.817, 0.348])

Fig. 8.8 Outline of the idea behind a variational autoencoder (VAE). However, the sampling step in the middle is not a discrete operation through which we cannot propagate.

Variational autoencoders have recently addressed these problems in a systematic way. The basic idea is to impose a distribution of latent variables, which is commonly assumed to be a normal distribution

$P(z) = \mathcal{N}(0, 1).

From this decoder can generate targets $X$ with the target distribution $P(X)$. This is shown on the right in Fig. 8.8. In order to generate the encoding we use a deep network which generates outputs for the mean and variance. We will then sample a point from a Gaussian with the corresponding mean and variance that becomes the input to the decoder. Overall, we train this network as autoencoder minimizing the Kull-Leibler distance between the encoder and the assumed normal distribution. A remaining problem is, however, the sampling in the middle is a discrete function that cannot be differentiated. This would prevent us from backpropagating the reconstruction error to the encoder. However, we can implement the sampling in the following way. We choose a random

$\epsilon \sim \mathcal{N}(0, 1).

which we multiply the variance and add the mean from the encoder output. These operations are differentiable. This implementation is illustrated in Fig. 8.9. Hence, this is basically still an encoder with some immediate input and is trained on the reconstruction error, but also on the minimization of the Kull-Leibler distance between the encoder output and a normal distribution. The latter part of the loss function can also be seen as a regularizer for the latent space which enforces a desirable latent representation.

In the following, we show a minimal MNIST example implementation Keras following basically the excellent implementation of Francois Chollet. This version is an attempt to minimize the example so that it can be run without GPU. However, implementing deeper networks and training on more example, will give even better results.