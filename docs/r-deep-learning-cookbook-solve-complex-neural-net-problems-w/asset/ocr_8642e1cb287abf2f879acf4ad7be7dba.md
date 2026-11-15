```
# Draw one sample z from Gaussian distribution
eps = tf$random_normal(shape(BATCH, n_h), 0, 1, dtype=tf$float32)
# z = mu + sigma*epsilon
z = tf$add(z_mean, tf$multiply(tf$sqrt (tf$exp (z_log_sigma_sq)),
eps))
# Use generator to determine mean of
# Bernoulli distribution of reconstructed input
x_reconstr_mean <- vae_decoder(z, network_weights[["decoder_w"]],
network_weights[[ "decoder_b"]])
return(list ("x_reconstr_mean"=x_reconstr_mean,
"z_log_sigma_sq"=z_log_sigma_sq, "z_mean"=z_mean))
}
```

# 9. Define the cost function for optimization:

```
# VAE cost function
vae_optimizer<-function(x, networkOutput){
x_reconstr_mean<-networkOutput$x_reconstr_mean
z_log_sigma_sq<-networkOutput$z_log_sigma_sq
z_mean<-networkOutput$z_mean
loss_reconstruction<--1*tf$reduce_sum(x*tf$log (1e-10 +
x_reconstr_mean)+
(1-x)* tf$log(1e-10 + 1 -
x_reconstr_mean), reduction_indices=shape (1))
loss_latent<--0.5*tf$reduce_sum(1+z_log_sigma_sq-
tf$square (z_mean)-
tf$exp (z_log_sigma_sq),
reduction_indices=shape (1))
cost = tf$reduce_mean (loss_reconstruction + loss_latent)
return(cost)
}
```

# 10. Set up the model to train:

```
# VAE Initialization
x = tf$placeholder(tf$float32, shape=shape(NULL, img_size_flat),
name='x')
network_weights<-model_init (n.hidden.enc.1, n.hidden.enc.2,
n.hidden.dec.1, n.hidden.dec.2,
n.input, n_h)
networkOutput<-network_ParEval (x, network_weights, n_h)
cost=vae_optimizer(x, networkOutput)
optimizer = tf$train$AdamOptimizer(lr)$minimize(cost)
```

# 11. Run optimization:

```
sess$run(tf$global_variables_initializer())
for(i in 1:ITERATION) {
```