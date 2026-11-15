

### 8. Define placeholder variables (x and y) and initialize weight matrix and bias vector:

```
with(tf$name_scope('input'), {
# Define placeholder for input data
x <- tf$placeholder(tf$float32, shape=shape(NULL, step_size,
n_input), name="x")
y <- tf$placeholder(tf$float32, shape=shape(NULL, n.class), name='y')

# Define Weights and bias
weights <- tf$Variable(tf$random_normal(shape(n.hidden, n.class)))
bias <- tf$Variable(tf$random_normal(shape(n.class)))
})
```

### 9. Generate the predicted labels:

```
# Evaluate rnn cell output
yhat = rnn(x, weights, bias)
# Define the loss function and optimizer
cost =
tf$reduce_mean(tf$nn$softmax_cross_entropy_with_logits(logits=yhat,
labels=y))
optimizer = tf$train$AdamOptimizer(learning_rate=lr)$minimize(cost)
```

### 10. Run the optimization post initializing a session using the global variables initializer:

```
sess$run(tf$global_variables_initializer())
for(i in 1:iteration){
  spls <- sample(1:dim(trainData)[1], batch)
  sample_data <- trainData[spls,]
  sample_y <- labels[spls,]
  # Reshape sample into 16 sequence with each of 16 element
  sample_data = tf$reshape(sample_data, shape(batch, step_size,
  n_input))
  out <- optimizer$run(feed_dict = dict(x = sample_data$eval(),
  y = sample_y))
  if (i %% 1 == 0){
    cat("iteration - ", i, "Training Loss - ", cost$eval(feed_dict
    = dict(x = sample_data$eval(), y = sample_y)), "\n")
  }
}
```

### 11. Get the mean accuracy on valid_data:

```
valid_data = tf$reshape(validData, shape(-1, step_size, n_input))
cost$eval(feed_dict = dict(x = valid_data$eval(), y = labels_valid))
```

## How it works...

Any changes to the structure require model retraining. However, these assumptions may not be valid for a lot of sequential datasets, such as text-based classifications that may have varying input and output. RNN architecture helps to address the issue of variable input length.

The standard architecture for RNN with input and output is shown in the following figure:

![](img/88a9c35e3059565190fbb6413f1ca217_208_0.png)

Recurrent Neural Network architecture

The RNN architecture can be formulated as follows:

```
\mathbf{h}_t = f(\mathbf{h}_{t-1}, x_t ; S, W)
```

Where $h_t$ is state at time/index $t$ and $x_t$ is input at time/index $t$. The matrix $W$ represents weights to connect hidden nodes and $S$ connects input with the hidden layer. The output node at time/index $t$ is related to state $h_t$, as shown as follows:

```
\mathbf{y}_t = f(\mathbf{h}_t ; \mathbf{V})
```

In the previous Equations layer, weights remain constant across state and time.

## Setting up a bidirectional RNN model

Recurrent Neural Networks focus on capturing the sequential information at time t by using historical states only. However, bidirectional RNN trains the model from both directions using two RNN layers with one moving forwards from start to end and another RNN layer moving backwards from end to start of sequence.

Thus, the model is dependent on historical and future data. The bidirectional RNN models are useful where causal structure exists such as in text and speech. The unfolded structure of bidirectional RNN is shown in the following figure:

![](img/88a9c35e3059565190fbb6413f1ca217_209_0.png)

Unfolded bidirectional RNN architecture

## Getting ready

Install and set up TensorFlow:

- 1. Load required packages:
- 2. Load MNIST dataset.
- 3. The image from MNIST dataset is reduced to 16 x 16 pixels and normalized (Details are discussed in the Setting-up RNN model section).

## How to do it...

This section covers the steps to set-up a bidirectional RNN model.

- 1. Reset the graph and start an interactive session:

```
# Reset the graph and set-up a interactive session
tf$reset_default_graph()
sess<-tf$InteractiveSession()
```

- 2. Reduce image size to 16 x 16 pixels using the reduceImage function from Chapter 4, Data Representation using Autoencoders:

```
# Covert train data to 16 x 16 pixel image
trainData<-t(apply(mnist$train$images, 1, FUN=reduceImage))
validData<-t(apply(mnist$test$images, 1, FUN=reduceImage))
```

- 3. Extract labels for the defined train and valid datasets:

```
labels <- mnist$train$labels
labels_valid <- mnist$test$labels
```

- 4. Define model parameters such as the size of input pixels (n\_input), step size (step\_size), number of hidden layers (n.hidden), and number of outcome classes (n.classes):

```
# Define Model parameter
n_input<-16
step_size<-16
n_hidden<-64
n.class<-10
```

- 5. Define training parameters such as learning rate (lr), number of inputs per batch run (batch), and number of iterations (iteration):

```
lr<-0.01
batch<-500
iteration = 100
```

- 6. Define a function to perform bidirectional Recurrent Neural Network:

```
bidirectionRNN<-function(x, weights, bias) {
# Unstack input into step_size
x = tf$unstack(x, step_size, 1)
# Forward lstm cell
rnn_cell_forward = tf$contrib$rnn$BasicRNNCell(n.hidden)
# Backward lstm cell
rnn_cell_backward = tf$contrib$rnn$BasicRNNCell(n.hidden)
# Get lstm cell output
cell_output =
tf$contrib$rnn$static_bidirectional_rnn(rnn_cell_forward,
rnn_cell_backward, x, dtype=tf$float32)
# Linear activation, using rnn inner loop last output
last_vec=tail(cell_output[[1]], n=1)[[1]]
return(tf$matmul(last_vec, weights) + bias)
}
```

- 7. Define an `eval_func` function to evaluate mean accuracy using actual (y) and predicted labels (yhat):

```
# Function to evaluate mean accuracy
eval_acc<-function(yhat, y) {
  # Count correct solution
  correct_Count = tf$equal(tf$argmax(yhat,1L), tf$argmax(y,1L))
  # Mean accuracy
  mean_accuracy = tf$reduce_mean(tf$cast(correct_Count,
  tf$float32))
  return(mean_accuracy)
}
```

- 8. Define placeholder variables (x and y) and initialize weight matrix and bias vector:

```
with(tf$name_scope('input'), {
  # Define placeholder for input data
  x = tf$placeholder(tf$float32, shape=shape(NULL, step_size,
  n_input), name='x')
  y <- tf$placeholder(tf$float32, shape=shape(NULL, n.class), name='y')

  # Define Weights and bias
  weights <- tf$Variable(tf$random_normal(shape(n.hidden, n.class)))
  bias <- tf$Variable(tf$random_normal(shape(n.class)))
})
```

- 9. Generate the predicted labels:

```
# Evaluate rnn cell output
yhat = bidirectionRNN(x, weights, bias)
```

- 10. Define the loss function and optimizer:

```
cost =
tf$reduce_mean(tf$nn$softmax_cross_entropy_with_logits(logits=yhat,
labels=y))
optimizer = tf$train$AdamOptimizer(learning_rate=lr)$minimize(cost)
```

- 11. Run the optimization post initializing a session using global variables initializer:

```
sess$run(tf$global_variables_initializer())
# Running optimization
for(i in 1:iteration){
  spls <- sample(1:dim(trainData)[1],batch)
  sample_data<-trainData[spls,]
  sample_y<-labels[spls,]
  # Reshape sample into 16 sequence with each of 16 element
  sample_data =tf$reshape(sample_data, shape(batch, step_size,
  n_input))
  out<-optimizer$run(feed_dict = dict(x=sample_data$eval(),
y=sample_y))
  if (i %% 1 == 0){
    cat("Iteration - ", i, "Training Loss - ", cost$eval(feed_dict
= dict (x=sample_data$eval(), y=sample_y)), "\n")
  }
}
```

- 12. Get the mean accuracy on valid data:

```
valid_data=tf$reshape(validData, shape(-1, step_size, n_input))
cost$eval(feed_dict=dict (x=valid_data$eval(), y=labels_valid))
```

- 13. The convergence of cost function for RNN is shown in the following figure:

![](img/88a9c35e3059565190fbb6413f1ca217_212_0.png)

Bidirectional Recurrent Neural Network convergence plot on MNIST dataset

## Setting up a deep RNN model

The RNN architecture is composed of input, hidden, and output layers. A RNN network can be made deep by decomposing the hidden layer into multiple groups or by adding computational nodes within RNN architecture such as including model computation such as multilayer perceptron for micro learning. The computational nodes can be added between input-hidden, hidden-hidden, and hidden-output connection. An example of a multilayer deep RNN model is shown in the following figure:

![](img/88a9c35e3059565190fbb6413f1ca217_213_0.png)

An example of two-layer Deep Recurrent Neural Network architecture

## How to do it...

The RNN models in TensorFlow can easily be extended to Deep RNN models by using MultiRNNCell. The previous rnn function can be replaced with the stacked_rnn function to achieve a deep RNN architecture:

- 1. Define the number of layers in the deep RNN architecture:

```
num_layers <- 3
```

- 2. Define a stacked_rnn function to perform multi-hidden layers deep RNN:

```
stacked_rnn<-function(x, weight, bias){
# Unstack input into step_size
x = tf$unstack(x, step_size, 1)
```

