
![](img/91c149cc24c3e5af2971580c9dda9d8b_349_0.png)

(a label or a number). When training an autoencoder, the input and the output is the same, that is, $(x, x)$.

Now you may be wondering what is the point of training a model that generates the same output as its input. If you take a closer look at Figure 10.11 you can see that the hidden layer has fewer units (only 2) than the input and output layers. When the data is passed from the input layer to the hidden layer it is ‘reduced’ (compressed). Then, the compressed data is reconstructed as it is passed to the subsequent layers until it reaches the output. Thus, the neural network will learn to compress and reconstruct the data at the same time. Once the network is trained, we can get rid of the layers after the middle hidden layer and use the ‘left-hand-side’ of the network to compress our data. The **encoder**. Then, we can use the right-hand-side to decompress the data. This part is called the **decoder**. In this example, the encoder and decoder consist of only 1 layer but they can have more (as we will see in the next section). In practice, you will not use autoencoders to compress files in your computer because there are more efficient methods to do that. Furthermore, the compression is *lossy*, that is, there is no guarantee that the reconstructed file will be exactly the same as the original. However, autoencoders have many applications including:

- Dimensionality reduction for visualization.
- Data denoising.
- Data generation (variational autoencoders).
- Anomaly detection (this is what we are interested in!).

Recall that when training a neural network we need to define a loss function. The function captures how well the network is learning. It measures how different the predictions are from the true expected outputs. In the context of autoencoders, this difference is known as the reconstruction error and can be measured using the mean squared error (similar to regression).

> In this section I introduced the most simple type of autoencoder but there are many variants as denoising autoencoders, variational autoencoders (VAEs), and so on. The Wikipedia page provides a good overview of the different types of autoencoders: https://en.wikipedia.org/wiki/Autoencoder

## CHAPTER 10. DETECTING ABNORMAL BEHAVIORS

### 10.3.1 Autoencoders for Anomaly Detection

```
keras_autoencoder_fish.R
```

Autoencoders can be used as anomaly detectors and we will use one to detect abnormal fish trajectories. The way this does is by training an autoencoder to compress and reconstruct the normal instances. Once the autoencoder has learned to encode normal instances, we can expect the reconstruction error to be small. When presented with out-of-the-normal instances, the autoencoder will have a hard time trying to reconstruct them and consequently, the reconstruction error will be deher. Similar to Isolation Forests where the tree length provides a measure of the rarity of an instance, the reconstruction error in autoencoders can be used as an anomaly score.

To tell whether an instance is abnormal or not, we can pass it through the autoencoder and compute its reconstruction error $\epsilon$. If $\epsilon > threshold$ the label can be regarded as abnormal.

Similar to what we did with the Isolation Forest, we will use the fishFeatures.csv file that contains the fish trajectories encoded as features. Each trajectory is composed of 8 numeric features based on acceleration and speed. We will use 80% of the normal instances to train the autoencoder. All abnormal instances will be used for the test set.

After splitting the data (the code is in keras_autoencoder_fish.R), we will normalize (standardize) it. The normalize.standard() function will normalize the data such that it has a mean of 0 and a standard deviation of 1.

```
$z = \frac{x - \mu}{\sigma} \quad (10.3)$
```

This is slightly different from the 0-1 normalization we have used before. The reason is that when scaling to 0-1 the min and max values from the train set need to be learned. If there are data points in the test set that have values outside the min and max they will be truncated. But since we expect anomalies to have rare values, then it is likely that they will be outside the train ranges and they will be truncated. After being truncated, abnormal instances could look more similar to the normal ones, it will be more difficult to spot them. By standardizing the data we make sure that the extreme values of the abnormal points are preserved. In this case, the parameters to be learned from the train set are $\mu$ and $\sigma$.
Once the data is normalized we can define the autoencoder.

```
autoencoder <- keras_model_sequential()

autoencoder <- %%
layer_dense(units = 32, activation = 'relu',
    input_shape = ncol(train.normal)-2) %%
layer_dense(units = 16, activation = 'relu') %%
layer_dense(units = 8, activation = 'relu') %%
layer_dense(units = 16, activation = 'relu') %%
layer_dense(units = 32, activation = 'relu') %%
layer_dense(units = ncol(train.normal)-2, activation = 'linear')
```

This is normal neural network with an input layer having the same number of units as number of features (8). This network has 5 hidden layers of size 32, 16, 8, 16, and 32, respectively. The output layer has 8 units (the same as the input). All activation functions are RELU the last one which is linear because the network should be able to produce any number as output. Now we can compile and fit the model.

```
autoencoder %% compile(
loss = 'mse',
optimizer = optimizer_sgd(lr = 0.01),
metrics = c('mse')
)
```

```
history <- autoencoder %%
as.matrix(train.normal[,-c(1:2)]]),
as.matrix(train.normal[,-c(1:2)]]),
```

![](img/91c149cc24c3e5af2971580c9dda9d8b_352_0.png)

Figure 10.12: Loss and MSE.

```
epochs = 100,
batch_size = 32,
validation_split = 0.10,
verbose = 2,
view_metrics = TRUE
```

We mean squared error (MSE) as the loss function. We use the normal instances in the train set as the input and expected output. The validation split is set to 10% so we can plot the reconstruction error (loss) on unseen instances. Finally, the model is trained for 100 epochs.

As the training progresses, the loss decreases. We can compute the MSE on the normal and abnormal test set. test.normal contains only normal instances and test.abnormal contains only abnormal instances.

```
# Compute MSE of normal test set.
autoencoder %>% evaluate(as.matrix(test.normal,-c(1:2))),
as.matrix(test.normal,-c(1:2)))
```

```
# loss mean_squared_error
# 0.06147528 0.06147528

# Compute MSE of abnormal test set.
autoencoder%% evaluate(as.matrix(test.abnormal[-c(1:2)]),
                                     as.matrix(test.abnormal[-c(1:2)]))
# loss mean_squared_error
# 2.660597 2.660597
```

Clearly, the MSE of the normal test set is much lower than the abnormal test set. This means the autoencoder had a difficult time trying to reconstruct the abnormal points because it never saw ones before.

To find a good threshold we can start by analyzing the reconstruction errors on the train set. First, we need to get the predictions.

```
# Predict values on the normal train set.
preds.train.normal <- autoencoder %%
predict_on_batch(as.matrix(train.normal[-c(1:2)]))
```

The variable preds.train.normal contains the predicted values for each feature and each instance. We can use these predictions to compute the reconstruction error by comparing them with the ground truth values. As reconstruction error we will use the squared errors. The function squared.errors() computes the reconstruction error for each instance.

```
# Compute individual squared errors in train set.
errors.train.normal <- squared_errors(preds.train.normal,
                                              as.matrix(train.normal[-c(1:2)]))
```

```
mean(errors.train.normal)
# [1] 0.8113273
```

```
quantile(errors.train.normal)
# 0% 25% 50% 75% 100%
# 0.0158690 0.2926631 0.4978471 0.8874694 15.0958992
```
