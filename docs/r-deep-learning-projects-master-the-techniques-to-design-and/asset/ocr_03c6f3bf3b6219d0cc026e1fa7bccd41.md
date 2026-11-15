```
y_test <- test$Class
X_train <- train %>% select (-one_of(c("Time", "Class")))
X_test <- test %>% select (-one_of(c("Time", "Class")))
# Coerce the data frame to matrix to perform the training
X_train <- as.matrix(X_train)
X_test <- as.matrix(X_test)
```

Notice that we also excluded the `Class` and `Time` columns. We are ignoring the label and treating our fraud detection problem as an unsupervised learning problem, hence we need to remove the label column from the training data. As for the temporal information, as we saw before, there does not seem to be an obvious time trend. Furthermore, in real-life fraud detection scenarios, we are rather concerned about the intrinsic properties of the fraudster, for instance, device used, geolocation information or data from the CRM system, as well as account properties (balance, average transaction volume, and so on).

For the architecture of the autoencoder, instead of using one intermediate layer as before, we will now use a **stacked autoencoder**. A stacked autoencoder is nothing more than several layers of encoders, followed by layers of decoders. In this case, we will use a network with outer encoder-decoder layers of 14 fully connected neurons, two inner layers of 7 neurons and yet another inner layer of 7 neurons. You can experiment with different architectures and compare results with ours, there is no universally correct architecture for autoencoders, it relies merely on experience and on diagnosing your model via validation plots and other metrics.

Our input (and output) dimension is 29 in each case. The code to construct the autoencoder is:

```
library(keras)
input_dim <- 29
outer_layer_dim <- 14
inner_layer_dim <- 7
input_layer <- layer_input(shape=c(input_dim))
encoder <- layer_dense(units=outer_layer_dim,
activation='relu')(input_layer)
encoder <- layer_dense(units=inner_layer_dim, activation='relu')(encoder)
decoder <- layer_dense(units=inner_layer_dim)(encoder)
decoder <- layer_dense(units=outer_layer_dim)(decoder)
decoder <- layer_dense(units=input_dim)(decoder)
autoencoder <- keras_model(inputs=input_layer, outputs = decoder)
```