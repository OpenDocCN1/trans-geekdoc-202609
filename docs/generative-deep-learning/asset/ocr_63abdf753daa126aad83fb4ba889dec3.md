The latent variable z is sampled from the Gaussian defined by mu and logvar by sampling from a standard Gaussian and then scaling and shifting the sampled vector (Example 12-1).

# Example 12-1. Sampling z from the multivariate normal distribution defined by mu and logvar

```
eps = tf.random_normal(shape=tf.shape(mu))
sigma = tf.exp(logvar * 0.5)
z = mu + eps * sigma
```

# The decoder model

The decode model accepts a z vector as input and reconstructs the original image. In Figure 12-9 we linearly interpolate two of the dimensions of z to show how each dimension appears to encode a particular aspect of the track—in this example z[4] controls the immediate left/right direction of the track nearest the car and z[7] controls the sharpness of the approaching left turn.

This shows that the latent space that the VAE has learned is continuous and can be used to generate new track segments that have never before been observed by the agent.