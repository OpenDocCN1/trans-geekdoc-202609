# 12.5.6 The adversarial network

Finally, we’ll set up the GAN, which chains the generator and the discriminator. When trained, this model will move the generator in a direction that improves its ability to fool the discriminator. This model turns latent-space points into a classification decision—“fake” or “real”—and it’s meant to be trained with labels that are always “these are real images.” So training gan will update the weights of generator in a way that makes discriminator more likely to predict “real” when looking at fake images.

To recapitulate, this is what the training loop looks like schematically. For each epoch, you do the following:

+   1. Draw random points in the latent space (random noise).
+   2. Generate images with generator using this random noise.
+   3. Mix the generated images with real ones.
+   4. Train discriminator using these mixed images, with corresponding targets: either “real” (for the real images) or “fake” (for the generated images).
+   5. Draw new random points in the latent space.
+   6. Train generator using these random vectors, with targets that all say “these are real images.” This updates the weights of the generator to move them toward getting the discriminator to predict “these are real images” for generated images: this trains the generator to fool the discriminator.

Let’s implement it. Like in our VAE example, we’ll use a Model subclass with a custom train_step(). Note that we’ll use two optimizers (one for the generator and one for the discriminator), so we will also override compile() to allow for passing two optimizers.

```
Listing 12.36 The GAN Model

import tensorflow as tf

class GAN(keras.Model):
    def __init__(self, discriminator, generator, latent_dim):
        super().__init__()
        self.discriminator = discriminator
        self.generator = generator
        self.latent_dim = latent_dim
        self.d_loss_metric = keras.metrics.Mean(name="d_loss")
        self.g_loss_metric = keras.metrics.Mean(name="g_loss")

    def compile(self, d_optimizer, g_optimizer, loss_fn):
        super(GAN, self).compile()
        self.d_optimizer = d_optimizer
        self.g_optimizer = g_optimizer
        self.loss_fn = loss_fn

    @property
    def metrics(self):
        return [self.d_loss_metric, self.g_loss_metric]
```