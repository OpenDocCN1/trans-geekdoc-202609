The encoder only needs to map each input to a mean vector and a variance vector and does not need to worry about covariance between dimensions. Variational autoencoders assume that there is no correlation between dimensions in the latent space.

Variance values are always positive, so we actually choose to map to the logarithm of the variance, as this can take any real number in the range (−∞, ∞). This way we can use a neural network as the encoder to perform the mapping from the input image to the mean and log variance vectors.

To summarize, the encoder will take each input image and encode it to two vectors that together define a multivariate normal distribution in the latent space:

+   - **z_mean**
+     The mean point of the distribution
+   - **z_log_var**
+     The logarithm of the variance of each dimension

We can sample a point z from the distribution defined by these values using the following equation:

```
z = z_mean + z_sigma * epsilon
```

where:

```
z_sigma = exp(z_log_var * 0.5)
epsilon ~ N(0,I)
```

![](bbox=[0.15, 0.58, 0.25, 0.68])

The derivation of the relationship between z_sigma (σ) and z_log_var (log(σ²)) is as follows:

σ = exp ( log(σ) ) = exp ( 2 log(σ)/2 ) = exp ( log(σ²)/2 )

The decoder of a variational autoencoder is identical to the decoder of a plain autoencoder, giving the overall architecture shown in Figure 3-12.

![](bbox=[0.18, 0.7, 0.85, 0.8])

Figure 3-12. VAE architecture diagram