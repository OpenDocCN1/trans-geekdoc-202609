```
self.c_optimizer.apply_gradients(
    zip(c_gradient, self.critic.trainable_variables)
) ⑤

random_latent_vectors = tf.random.normal(
    shape=(batch_size, self.latent_dim)
)
with tf.GradientTape() as tape:
    fake_images = self.generator(random_latent_vectors, training=True)
    fake_predictions = self.critic(fake_images, training=True)
    g_loss = -tf.reduce_mean(fake_predictions) ⑥

gen_gradient = tape.gradient(g_loss, self.generator.trainable_variables)
self.g_optimizer.apply_gradients(
    zip(gen_gradient, self.generator.trainable_variables)
) ⑦

self.c_loss_metric.update_state(c_loss)
self.c_wass_loss_metric.update_state(c_wass_loss)
self.c_gp_metric.update_state(c_gp)
self.g_loss_metric.update_state(g_loss)

return {m.name: m.result() for m in self.metrics}
```

+   1. Perform three critic updates.
+   2. Calculate the Wasserstein loss for the critic—the difference between the average prediction for the fake images and the real images.
+   3. Calculate the gradient penalty term (see Example 4-8).
+   4. The critic loss function is a weighted sum of the Wasserstein loss and the gradient penalty.
+   5. Update the weights of the critic.
+   6. Calculate the Wasserstein loss for the generator.
+   7. Update the weights of the generator.

![](bbox=[0.16, 0.75, 0.24, 0.83])

# Batch Normalization in a WGAN-GP

One last consideration we should note before training a WGAN-GP is that batch normalization shouldn't be used in the critic. This is because batch normalization creates correlation between images in the same batch, which makes the gradient penalty loss less effective. Experiments have shown that WGAN-GPs can still produce excellent results even without batch normalization in the critic.