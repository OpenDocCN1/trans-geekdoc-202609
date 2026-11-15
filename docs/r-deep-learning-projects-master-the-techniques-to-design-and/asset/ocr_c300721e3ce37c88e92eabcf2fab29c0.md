We begin as before:

```
library(keras)
mnist <- dataset_mnist()
X_train <- mnist$train$x
y_train <- mnist$train$y
X_test <- mnist$test$x
y_test <- mnist$test$y
```

But now we will exclude 7 from the training set, as it will be the outlier in our example.

```
## Exclude "7" from the training set. "7" will be the outlier
outlier_idxs <- which(y_train!=7, arr.ind = T)
X_train <- X_train[outlier_idxs,,]
y_test <- sapply(y_test, function(x) { ifelse(x==7,"outlier","normal") })
```

We continue as before, with re-scaling and reshaping before defining our autoencoder:

```
# reshape
dim(X_train) <- c(nrow(X_train), 784)
dim(X_test) <- c(nrow(X_test), 784)
# rescale
X_train <- X_train / 255
X_test <- X_test / 255
input_dim <- 28*28 #784
inner_layer_dim <- 32
# Create the autoencoder
input_layer <- layer_input (shape=c(input_dim))
encoder <- layer_dense (units=inner_layer_dim,
activation='relu') (input_layer)
decoder <- layer_dense (units=784) (encoder)
autoencoder <- keras_model (inputs=input_layer, outputs = decoder)
autoencoder %>% compile (optimizer='adam',
loss='mean_squared_error',
metrics=c('accuracy'))
history <- autoencoder %>% fit (
X_train,X_train,
epochs = 50, batch_size = 256,
validation_split=0.2
)
plot(history)
```