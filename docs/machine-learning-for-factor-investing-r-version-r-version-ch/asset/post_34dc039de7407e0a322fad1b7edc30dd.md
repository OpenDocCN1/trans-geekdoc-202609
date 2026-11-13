
in the above chunk is the categorical accuracy. In multiclass classification, the accuracy is defined as the average accuracy over all classes and all predictions. Since a prediction for one instance is a vector of weights, the ‘terminal’ prediction is the class that is associated with the largest weight. The accuracy then measures the proportion of times when the prediction is equal to the realized value (i.e., when the class is correctly guessed by the model).

Finally, we proceed with the training of the model.

```
fit_NN_C <- model_C %>% 
  fit(NN_train_features, 
      NN_train_labels_C, 
      epochs = 20, batch_size = 512, 
      validation_data = list(NN_test_features, 
                             NN_test_labels_C), 
    verbose = 0, 
    callbacks = list( 
      callback_early_stopping(monitor = "val_loss", 
                              min_delta = 0.001, 
                              patience = 3, 
                              verbose = 0 
                              ) 
          ) 
        )
plot(fit_NN_C)
```

![](img/8861a37f775d09b4ba7a5151f604d9f5_130_0.png)

## FIGURE 7.8: Output from a trained neural network (classification task) with early stopping.

There is only one major difference here compared to the previous training call. In Keras, callbacks are functions that can be used at given stages of the learning process. In the above example, we use one such function to stop the algorithm when no progress has been made for some time.

When datasets are large, the training can be long, especially when batch sizes are small and/or the number of epochs is high. It is not guaranteed that going to the full number of epochs is useful, as the loss or metric functions may be plateauing much sooner. Hence, it can be very convenient to stop the process if no improvement is achieved during a specified time-frame. We set the number of epochs to 20, but the process will likely stop before that.

In the above code, the improvement is focused on validation accuracy ("val_acc"; one alternative is "val_loss"). The min_delta value sets the minimum improvement that needs to be attained for the algorithm to continue. Therefore, unless the validation accuracy gains 0.001 points at each epoch, the training will stop. Nevertheless, some flexibility is introduced via the patience parameter, which in our case asserts that the halting decision is made only after three consecutive epochs with no improvement. In the option, the verbose parameter dictates the amount of comments that is made by the function. For simplicity, we do not want any comments, hence this value is set to zero.

In Figure 7.8, the two graphs yield very different curves. One reason for that is the scale of the second graph. The range of accuracies is very narrow. Any change in this range does not represent much variation overall. The pattern is relatively clear on the training sample: the loss decreases, while the accuracy improves. Unfortunately, this does not translate to the testing sample which indicates that the model does not generalize well out-of-sample.

## 7.4.3 Custom losses

In Keras, it is possible to define user-specified loss functions. This may be interesting in some cases. For instance, the quadratic error has three terms \(y_i^2\), \(\hat{y}_i^2\) and \(-2y_i\hat{y}_i\). In practice, it can make sense to focus more on the latter term because it is the most essential: we do want predictions and realized values to have the same sign! Below we show how to optimize on a simple (product) function in Keras, \(l(y_i, \hat{y}_i) = (\hat{y}_i - \bar{m})^2 - \gamma(y_i - m)(\hat{y}_i - \bar{m})\), where \(m\) and \(\bar{m}\) are the sample averages of \(y_i\) and \(\hat{y}_i\). With \(\gamma > 2\), we give more weight to the cross term. We start with a simple architecture.

```r
model_custom <- keras_model_sequential()
model_custom %>% # This defines the structure of the network, i.e. how layers are organized
  layer_dense(units = 16, activation = 'relu', input_shape = ncol(NN_train_features)) %>% 
  layer_dense(units = 8, activation = 'sigmoid') %>% 
  layer_dense(units = 1) # No activation means linear activation: f(x) = x.
```

Then we code the loss function and integrate it to the model. The important trick is to resort to functions that are specific to the library (the k__functions). We code the variance of predicted values minus the scaled covariance between realized and predicted values. Below we use a scale of five.

```r
custom_loss <- function(y, f){ # Defines the loss, we use gamma = 5
  return(k_mean((f - k_mean(f))*(f - k_mean(f)))-5*k_mean((y - k_mean(y))*(f - k_mean(f))))
}
model_custom %>% compile(
loss = function(y_true, y_pred, custom_loss(y_true, y_pred), # New loss function!
optimizer = optimizer_rmsprop(), # Optim method
metrics = c('mean_absolute_error') # Output metric
)
```

Finally, we are ready to train and briefly evaluate the performance of the model.

```r
fit_NN_cust <- model_custom %>% # Training features
fit(NN_train_features,
  NN_train_labels, # Training labels
  epochs = 10, batch_size = 512, # Training parameters
  validation_data = list(NN_test_features, NN_test_labels) # Test data
)
plot(fit_NN_cust)
```

![](img/8861a37f775d09b4ba7a5151f604d9f5_132_0.png)

The curves may go in opposite direction. One reason for that is that while improving correlation between realized and predicted values, we are also increasing the sum of squared predicted returns.

```
mean(predict(model_custom, NN_test_features) * NN_test_labels > 0) # Hit ratio
## [1] 0.4468864
```

The outcome could be improved. There are several directions that could help. One of them is arguably that the model should be dynamic and not static (see Chapter 12).

## 7.5 Recurrent networks

### 7.5.1 Presentation

Multilayer perceptrons are feed-forward networks because the data flows from left to right with no looping in between. For some particular tasks with sequential linkages (e.g., time-series or speech recognition), it might be useful to keep track of what happened with the previous sample (i.e., there is a natural ordering). One simple way to model 'memory' would be to consider the following network with only one intermediate layer:

\(\bar{y}_i = f^{(y)} \left( \sum_{j=1}^{U_1} h_{i,j} w_j^{(y)} + b^{(2)} \right)\)

\(\mathbf{h}_i = f^{(h)} \left( \sum_{k=1}^{U_0} x_{i,k} w_k^{(h,1)} + b^{(1)} + \underbrace{\sum_{k=1}^{U_1} w_k^{(h,2)} h_{i-1,k}}_{\text{memory part}} \right)\),

where \(h_0\) is customarily set at zero (vector-wise).

These kinds of models are often referred to as Elman (1990) models or to Jordan (1997) models if in the latter case \(h_{i-1}\) is replaced by \(y_{i-1}\) in the computation of \(h_i\). Both types of models fall under the overarching umbrella of Recurrent Neural Networks (RNNs).

The \(h_i\) is usually called the state or the hidden layer. The training of this model is complicated and must be done by unfolding the network over all instances to obtain a simple feed-forward network and train it regularly. We illustrate the unfolding principle in Figure 7.9. It shows a very deep network. The first input impacts the first layer and then the second one via \(h_1\) and all following layers in the same fashion. Likewise, the second input impacts all layers except the first and each instance \(i-1\) is going to impact the output \(\bar{y}_i\) and all outputs \(\bar{y}_j\) for \(j \ge i\). In Figure 7.9, the parameters that are trained are shown in blue. They appear many times, in fact, at each level of the unfolded network.

![](img/8861a37f775d09b4ba7a5151f604d9f5_133_0.png)

## FIGURE 7.9: Unfolding a recurrent network.

The main problem with the above architecture is the loss of memory induced by **vanishing gradients**. Because of the depth of the model, the chain rule used in the back-propagation will imply a large number of products of derivatives of activation functions. Now, as is shown in Figure 7.4, these functions are very smooth and their derivatives are most of the time smaller than one (in absolute value). Hence, multiplying many numbers smaller than one leads to very small figures: beyond some layers, the learning does not propagate because the adjustments are too small.

One way to prevent this progressive discounting of the memory was introduced in Hochreiter and Schmidhuber (1997) (Long-Short Term Memory - LSTM model). This model was subsequently simplified by the authors Chung et al. (2015) and we present this more parsimonious model below. The Gated Recurrent Unit (GRU) is a slightly more complicated
