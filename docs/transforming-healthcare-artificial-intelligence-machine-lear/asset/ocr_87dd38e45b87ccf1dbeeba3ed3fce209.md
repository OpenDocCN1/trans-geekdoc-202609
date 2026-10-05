# 62 Transforming Healthcare

output nodes. This depth enables deep learning models to: One significant difference distinguishing deep learning models from classical ML is the feature extraction process. Traditional ML models require hand-crafted features, while deep learning one builds the features from data. including real-life images, audio, and text. Some of the noticeable architecture present in deep learning are: CNNs, which are mainly used in image processing, and Computer vision, which are generalised by convolutional layers that reuse the parameters in each Conv layer to perform feature mappings on the given images. Recurrent neural networks are artificial neural networks that introduce recurrent connections into the data. This type of architecture is used on sequential objects like time series and language data since there is past information in the previous steps. Generative models are a field where deep learning has also been applied, with the development of GANs (Generative Adversarial Networks) and VAEs (Variational Autoencoders) capable of generating new data points that resemble the input data.

# 3.4 MACHINE LEARNING AND DEEP LEARNING IN DISEASE DIAGNOSIS AND TREATMENT

# 3.4.1 Skin detection using autoencoder

An autoencoder is a neural network used for unsupervised learning, often applied for feature extraction or dimensionality reduction. In the context of skin cancer detection, an autoencoder can be trained on medical images to compress and reconstruct the data, thereby learning useful representations of skin cancer patterns. The encoder maps the input data $X \in R^n$ to a latent representation $Z \in R^m$, where $m<n$. Mathematically, the encoder can be written as

```
$Z = f_{\theta}(X) = \sigma(W_ex + b_e)$
```

Where $X$ is the input (e.g., skin cancer image), $W_e$ is the weight matrix of the encoder, $b_e$ is the bias term, $\sigma(\cdot)$ is the activation function (commonly ReLU, sigmoid, or tanh), and $Z$ is the latent space. The decoder endeavours to reconstruct the input data $\hat{X} \in R^n$. Mathematically, the decoder maps $Z$ back to the reconstructed input data. The decoder can be written as

```
$$\hat{X} = g_{\theta}(Z) = \sigma(W_dZ + b_d)$
```

where $W_d$ is the weight matrix of the decoder, $b_d$ is the bias term, and $\hat{X}$ is the reconstructed output. The goal of training the autoencoder is to