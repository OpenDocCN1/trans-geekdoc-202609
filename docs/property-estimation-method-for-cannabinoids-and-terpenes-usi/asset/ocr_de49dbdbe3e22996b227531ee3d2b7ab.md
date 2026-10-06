validation and test set contain unseen values, relevant for testing the performance of the
model. The latter can be achieved using a metric that in most cases is similar to the
loss function shown in Eq.(2) and is thought the coefficient of determination ($R^2$) Hortúa et
al. (2020):

```
$R^2 = 1 - \frac{\sum(y_i-\hat{y}_i)^2}{\sum(y_i-\bar{y})^2}$
```

where $y$ is the average of the true parameters and the summations are performed over the
entire test set. $R^2$ ranges from 0 to 1, where 1 represents perfect inference. $R^2$ will be
used in this work as metric for measuring the performance of the NN Models. Finally, a
downside of the standard NNs is that they are sensitive to the training process and
hype-parameter choices, finding different set of weights each time they are trained,\which turn produce different predictions and high variance. An attempt approach
to reduce variance is to train multiple models instead of a single one and combine
the predictions from these models. This is called ensemble learning and it helps to reduce
t variance of predictions and can also result in better performance Tao (2019).

# ## 3. Analysis

In order to predict the melting point in terms of the establish chemical groups, we started
with single NN regression models. First, we built in TensorFlow a FNN consists for some
layers with 256, 128, 64 and 1 neurons, followed by an ELU activation function,
a Batch Normalization to optimize and accelerate the convergence, and a Dropout
layer (with a rate of 0.1), for regularization purposes. Here, we adopt Adam as the
optimizer, and a layer decay with 0.01 in its initial value, with a factor of 0.08
during each 10 epochs. On the other hand, the Conv1D architecture comprises of four
convolutional layers of 64, 32, 32, 16, then a MaxPooling layer is used to reduce
t features of the feature map, followed by four layers of 256,126,64 and 1
neurons. Before, each layer is followed by an ELU activation function, Batch
Normalization and Dropout (rate 0.1).

Table 1. Performance for different models in terms of $R^2$

| Metric/Model | Ensemble MSE | MAE | Huber | Single MSE | MAE | Huber |
|---|---|---|---|---|---|---||
| $R^2$-FNN | 0.88 | 0.84 | 0.84 | 0.83 | 0.82 | 0.82 |
| $R^2$-Conv1D | 0.87 | 0.87 | 0.87 | 0.81 | 0.80 | 0.83 |

The results of the performance for both, FNN and Conv1D for different loss functions are
reported in the right hand side of Table 1. As observed, both models seem to workeaching a decent coefficient of determination value. FNN model trained with MSE
is the best that was achieved using all single NN experiments, and the behavior of
 predicting unseen instances can also be seen in Fig.1a. Finally, we worked with
ensembles of Neural Networks (BNN) for order including variances during the
inference process, and improve the estimates for predictions. The schema for those
ensembles with either FNN or Conv1D are displayed in Fig.(2)-(3)respectively. For these
ensembles we added at the top of the models, an Average layer which provides of an
unique name for predicting the melting point. Furthermore, we could extract
information from the top-before layer to get the outputs for all the models in the ensemble
and, to be able to calculate the standard deviation for the predicted values. As we can