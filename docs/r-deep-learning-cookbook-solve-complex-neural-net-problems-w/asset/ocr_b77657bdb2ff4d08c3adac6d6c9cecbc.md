```
spls <- sample(1:dim(trainData)[1], BATCH)
out<-optimizer$run(feed_dict = dict(x=trainData[spls,]))
if (i %% 100 == 0){
cat("Iteration - ", i, "Training Loss - ", cost$eval(feed_dict = dict(x=trainData[spls,])), "\\n")
}
}
```

# Output from the VAE autoencoder

+   1. The outcome can be generated using the following script:

```
spls <- sample(1:dim(trainData)[1], BATCH)
networkOutput_run<-sess$run(networkOutput, feed_dict = dict(x=trainData[spls,]))

# Plot reconstructed Image
x_sample<-trainData[spls,]
NROW<-nrow(networkOutput_run$x_reconstr_mean)
n.plot<-5
par(mfrow = c(n.plot, 2), mar = c(0.2, 0.2, 0.2, 0.2), oma = c(3, 3, 3, 3))
pltImages<-sample(1:NROW,n.plot)
for(i in pltIndices){
plot_mnist(x_sample[i,])
plot_mnist(networkOutput_run$x_reconstr_mean[i,])
}
```

The outcome obtained after 20,000 iterations from the preceding VAE autoencoder is shown in the following figure:

![](bbox=[0.333, 0.644, 0.666, 0.851])