# Analysis of the Diffusion Model

We’ll now take a look at three different ways that we can use our trained model: for generation of new images, testing how the number of reverse diffusion steps affects quality, and interpolating between two images in the latent space.

# Generating images

In order to produce samples from our trained model, we can simply run the reverse diffusion process, ensuring that we denormalize the output at the end (i.e., take the pixel values back into the range [0, 1]). We can achieve this using the code in Example 8-12 inside the DiffusionModel class.

Example 8-12. Generating images using the diffusion model

```
class DiffusionModel(models.Model):
    ...
    def denormalize(self, images):
        images = self.normalizer.mean + images * self.normalizer.variance**0.5 ①
        return tf.clip_by_value(images, 0.0, 1.0)

    def generate(self, num_images, diffusion_steps):
        initial_noise = tf.random.normal(shape=(num_images, 64, 64, 3)) ①
        generated_images = self.reverse_diffusion(initial_noise, diffusion_steps) ②
        generated_images = self.denormalize(generated_images) ③
        return generated_images
```

+   ① Generate some initial noise maps.
+   ② Apply the reverse diffusion process.
+   ③ The images output by the network will have mean zero and unit variance, so we need to denormalize by reapplying the mean and variance calculated from the training data.