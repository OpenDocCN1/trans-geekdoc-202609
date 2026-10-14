```
real_out, fake_out = tf.split(self.model(inp_imgs), 2, axis=0) ③
cdiv_loss = tf.reduce_mean(fake_out, axis = 0) - tf.reduce_mean(
    real_out, axis = 0
) ④
reg_loss = self.alpha * tf.reduce_mean(
    real_out ** 2 + fake_out ** 2, axis = 0
) ⑤
loss = reg_loss + cdiv_loss
grads = training_tape.gradient(loss, self.model.trainable_variables) ⑥
self.optimizer.apply_gradients(
    zip(grads, self.model.trainable_variables)
)
self.loss_metric.update_state(loss)
self.reg_loss_metric.update_state(reg_loss)
self.cdiv_loss_metric.update_state(cdiv_loss)
self.real_out_metric.update_state(tf.reduce_mean(real_out, axis = 0))
self.fake_out_metric.update_state(tf.reduce_mean(fake_out, axis = 0))
return {m.name: m.result() for m in self.metrics}

def test_step(self, real_imgs): ⑦
    batch_size = real_imgs.shape[0]
    fake_imgs = tf.random.uniform((batch_size, 32, 32, 1)) * 2 - 1
    inp_imgs = tf.concat([real_imgs, fake_imgs], axis=0)
    real_out, fake_out = tf.split(self.model(inp_imgs), 2, axis=0)
    cdiv = tf.reduce_mean(fake_out, axis = 0) - tf.reduce_mean(
        real_out, axis = 0
    )
    self.cdiv_loss_metric.update_state(cdiv)
    self.real_out_metric.update_state(tf.reduce_mean(real_out, axis = 0))
    self.fake_out_metric.update_state(tf.reduce_mean(fake_out, axis = 0))
    return {m.name: m.result() for m in self.metrics[2:]}

ebm = EBM()
ebm.compile(optimizer=optimizers.Adam(learning_rate=0.0001), run_eagerly=True)
ebm.fit(x_train, epochs=60, validation_data = x_test,)
```

+   1. A small amount of random noise is added to the real images, to avoid the model overfitting to the training set.
+   2. A set of fake images are sampled from the buffer.
+   3. The real and fake images are run through the model to produce real and fake scores.
+   4. The contrastive divergence loss is simply the difference between the scores of real and fake observations.
+   5. A regularization loss is added to avoid the scores becoming too large.