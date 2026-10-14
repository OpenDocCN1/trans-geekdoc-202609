# Algorithm 1 Training

+   1: repeat
+   2: x₀ ~ q(x₀)
+   3: t ~ Uniform({1, …, T})
+   4: ε ~ N(0, I)
+   5: Take gradient descent step on
+      ∇θ || ε - εθ(√ᾱₜ x₀ + √1-ᾱₜ ε, t) ||²
+   6: until converged

Figure 8-7. The training process for a denoising diffusion model (source: Ho et al., 2020)

In Keras, we can code up this training step as illustrated in Example 8-5.

# Example 8-5. The train_step function of the Keras diffusion model

```
class DiffusionModel(models.Model):
    def __init__(self):
        super().__init__()
        self.normalizer = layers.Normalization()
        self.network = unet
        self.ema_network = models.clone_model(self.network)
        self.diffusion_schedule = cosine_diffusion_schedule
    ...
    def denoise(self, noisy_images, noise_rates, signal_rates, training):
        if training:
            network = self.network
        else:
            network = self.ema_network
        pred_noises = network(
            [noisy_images, noise_rates**2], training=training
        )
        pred_images = (noisy_images - noise_rates * pred_noises) / signal_rates
        return pred_noises, pred_images
    def train_step(self, images):
        images = self.normalizer(images, training=True) ①
        noises = tf.random.normal(shape=tf.shape(images)) ②
        batch_size = tf.shape(images)[0]
        diffusion_times = tf.random.uniform(
            shape=(batch_size, 1, 1, 1), minval=0.0, maxval=1.0
        ) ③
        noise_rates, signal_rates = self.cosine_diffusion_schedule(
            diffusion_times
        ) ④
        noisy_images = signal_rates * images + noise_rates * noises ⑤
```