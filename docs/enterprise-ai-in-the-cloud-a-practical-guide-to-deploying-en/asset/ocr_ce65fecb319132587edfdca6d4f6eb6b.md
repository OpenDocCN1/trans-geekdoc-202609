meanings of words and in generative models to create new data that is like the input training data.

> NOTE Autoencoders are versatile tools that can be used for both supervised and unsupervised learning.

The autoencoder is focused on creating the most compact representation of the input data, effectively reducing the dimensionality of the data.

The autoencoder has an input layer that's connected to an encoder, which is a series of hidden layers that reduce the dimensionality of the input data. It contains two functions. It contains an encoding function that transforms the input data into a lower-dimensional latent space representation, also known as an _encoding_. Figure 16.16 shows how an autoencoder works.

![](bbox=[0.121, 0.346, 0.881, 0.574])

# FIGURE 16.16: Schema of a basic autoencoder

The encoded data is then passed to a _decoder_, which is a series of hidden layers. The decoder layer uses a decoder function that re-creates the input data from the encoded representation. The output layer is compared to the input layer and the error is used to train the autoencoder.

Autoencoders can be used for the use cases listed in Table 16.6.