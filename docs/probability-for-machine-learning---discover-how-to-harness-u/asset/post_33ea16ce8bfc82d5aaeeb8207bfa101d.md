
Listing 23.18: Example of calculating the cross-entropy for each example.

Finally, we can calculate the average cross-entropy across the dataset and report it as the cross-entropy loss for the model on the dataset.

```
...
# calculate the average cross-entropy
mean_ce = mean(results)
print('Average Cross Entropy: %.3f nats' % mean_ce)
```

Listing 23.19: Example of calculating the average cross-entropy.

Tying this all together, the complete example is listed below.

```
# calculate cross entropy for classification problem
from math import log
from numpy import mean

# calculate cross entropy
def cross_entropy(p, q):
    return -sum([p[i]*log(q[i]) for i in range(len(p))])

# define classification data
p = [1, 1, 1, 1, 1, 0, 0, 0, 0, 0]
q = [0.8, 0.9, 0.9, 0.6, 0.8, 0.1, 0.4, 0.2, 0.1, 0.3]
# calculate cross entropy for each example
results = list()
for i in range(len(p)):
    # create the distribution for each event {0, 1}
    expected = [1.0 - p[i], p[i]]
    predicted = [1.0 - q[i], q[i]]
    # calculate cross entropy for the two events
    ce = cross_entropy(expected, predicted)
    print('> [y=%.1f, yhat=%.1f] ce: %.3f nats' % (p[i], q[i], ce))
    results.append(ce)

# calculate the average cross entropy
mean_ce = mean(results)
print('Average Cross Entropy: %.3f nats' % mean_ce)
```

Listing 23.20: Example of calculating the average cross-entropy between expected and predicted probabilities.

Running the example prints the actual and predicted probabilities for each example and the cross-entropy in nats. The final average cross-entropy loss across all examples is reported, in this case, as 0.247 nats.

```
>[y=1.0, yhat=0.8] ce: 0.223 nats
>[y=1.0, yhat=0.9] ce: 0.105 nats
>[y=1.0, yhat=0.9] ce: 0.105 nats
>[y=1.0, yhat=0.6] ce: 0.511 nats
>[y=1.0, yhat=0.8] ce: 0.223 nats
>[y=0.0, yhat=0.1] ce: 0.105 nats
>[y=0.0, yhat=0.4] ce: 0.511 nats
>[y=0.0, yhat=0.2] ce: 0.223 nats
>[y=0.0, yhat=0.1] ce: 0.105 nats
>[y=0.0, yhat=0.3] ce: 0.357 nats
Average Cross Entropy: 0.247 nats
```

Listing 23.21: Example output from cross-entropy between expected and predicted probabilities.

This is how cross-entropy loss is calculated when optimizing a logistic regression model or a neural network model under a cross-entropy loss function.

## 23.5.3 Calculate Cross-Entropy Using Keras

We can confirm the same calculation by using the `binary_crossentropy()` function from the Keras deep learning API to calculate the cross-entropy loss for our small dataset. The complete example is listed below. Note that this example assumes that you have the Keras library installed and configured with a backend library such as TensorFlow. If not, you can skip running this example.

```python
# calculate cross entropy with keras
from numpy import asarray
from keras import backend
from keras.losses import binary_crossentropy
# prepare classification data
p = asarray([1, 1, 1, 1, 1, 0, 0, 0, 0, 0])
q = asarray([0.8, 0.9, 0.9, 0.6, 0.8, 0.1, 0.4, 0.2, 0.1, 0.3])
# convert to keras variables
y_true = backend.variable(p)
y_pred = backend.variable(q)
# calculate the average cross-entropy
mean_ce = backend.eval(binary_crossentropy(y_true, y_pred))
print('Average Cross Entropy: %.3f nats' % mean_ce)
```

Listing 23.22: Example of calculating the average cross-entropy between expected and predicted probabilities with Keras.

Running the example, we can see that the same average cross-entropy loss of 0.247 nats is reported. This confirms the correct manual calculation of cross-entropy.

```text
Average Cross Entropy: 0.247 nats
```

Listing 23.23: Example output from calculating the average cross-entropy between expected and predicted probabilities with Keras.

We can see that we could just as easily minimize the KL divergence as a loss function instead of the cross-entropy. The specific values would be different, but the effect would be the same as the two values are proportional to each other (e.g. minus the constant of the entropy for P).

Minimizing this KL divergence corresponds exactly to minimizing the cross-entropy between the distributions.

> — Page 132, *Deep Learning*, 2016.

## 23.6 Difference Between Cross-Entropy and Log Loss

Cross-Entropy is not Log Loss, but they calculate the same quantity when used as loss functions for binary classification problems (introduced in Chapter 13).

### 23.6.1 Log Loss is the Negative Log Likelihood

Logistic loss refers to the loss function commonly used to optimize a logistic regression model. It may also be referred to as logarithmic loss (which is confusing) or simply log loss. Many models are optimized under a probabilistic framework called maximum likelihood estimation, or MLE, that involves finding a set of parameters that best explain the observed data.

This involves selecting a likelihood function that defines how likely a set of observations (data) are given model parameters. When a log likelihood function is used (which is common), it is often referred to as optimizing the log likelihood for the model. Because it is more common to minimize a function than to maximize it in practice, the log likelihood function is inverted by adding a negative sign to the front. This transforms it into a Negative Log Likelihood function or NLL for short. In deriving the log likelihood function under a framework of maximum likelihood estimation for a Bernoulli probability distribution functions (two classes), the calculation comes out to be:

$$\mathrm{NLL}(P,Q) = -\big(P(\mathit{class0}) \times \log(Q(\mathit{class0})) + P(\mathit{class1}) \times \log(Q(\mathit{class1}))\big) \tag{23.9}$$

This quantity can be averaged over all training examples by calculating the average of the log of the likelihood function. Negative log-likelihood for binary classification problems is often shortened to simply *log loss* as the loss function derived for logistic regression.

$$\text{log loss} = \text{negative log-likelihood, under a Bernoulli probability distribution} \tag{23.10}$$

We can see that the negative log-likelihood is the same calculation as is used for the cross-entropy for Bernoulli probability distribution functions (two events or classes). In fact, the negative log-likelihood for Multinoulli distributions (multiclass classification) also matches the calculation for cross-entropy.

### 23.6.2 Log Loss and Cross Entropy Calculate the Same Thing

For binary classification problems, *log loss*, *cross-entropy* and *negative log-likelihood* are used interchangeably. More generally, the terms *cross-entropy* and *negative log-likelihood* are used interchangeably in the context of loss functions for classification models.

> The negative log-likelihood for logistic regression is given by [...] This is also called the cross-entropy error function.

> — Page 246, *Machine Learning: A Probabilistic Perspective*, 2012.

Therefore, calculating log loss will give the same quantity as calculating the cross-entropy for Bernoulli probability distribution. We can confirm this by calculating the log loss using the `log_loss()` function from the scikit-learn API. Calculating the average log loss on the same set of actual and predicted probabilities from the previous section should give the same result as calculating the average cross-entropy. The complete example is listed below.

```python
# calculate log loss for classification problem with scikit-learn
from sklearn.metrics import log_loss
from numpy import asarray
# define classification data
p = [1, 1, 1, 1, 1, 0, 0, 0, 0, 0]
q = [0.8, 0.9, 0.9, 0.6, 0.8, 0.1, 0.4, 0.2, 0.1, 0.3]
# define data as expected, e.g. probability for each event {0, 1}
y_true = asarray([[1-v, v] for v in p])
y_pred = asarray([[1-v, v] for v in q])
# calculate the average log loss
ll = log_loss(y_true, y_pred)
print('Average Log Loss: %.3f' % ll)
```

Listing 23.24: Example of calculating the average log loss between expected and predicted probabilities.

Running the example gives the expected result of 0.247 log loss, which matches 0.247 nats when calculated using the average cross-entropy.

```text
Average Log Loss: 0.247
```

Listing 23.25: Example output from calculating the average log loss between expected and predicted probabilities.

This does not mean that log loss calculates cross-entropy or cross-entropy calculates log loss. Instead, they are different quantities, arrived at from different fields of study, that under the conditions of calculating a loss function for a classification task, result in an equivalent calculation and result. Specifically, a cross-entropy loss function is equivalent to a maximum likelihood function under a Bernoulli or Multinoulli probability distribution. This demonstrates a connection between the study of maximum likelihood estimation and information theory for discrete probability distributions.

It is not limited to discrete probability distributions, and this fact is surprising to many practitioners that hear it for the first time. Specifically, a linear regression optimized under the maximum likelihood estimation framework assumes a Gaussian continuous probability distribution for the target variable and involves minimizing the mean squared error function. This is equivalent to the cross-entropy for a random variable with a Gaussian probability distribution.

> Any loss consisting of a negative log-likelihood is a cross-entropy between the empirical distribution defined by the training set and the probability distribution defined by model. For example, mean squared error is the cross-entropy between the empirical distribution and a Gaussian model.
> 
> — Page 132, *Deep Learning*, 2016.

This is a little mind blowing, and comes from the field of differential entropy for continuous random variables. It means that if you calculate the mean squared error between two Gaussian random variables that cover the same events (have the same mean and standard deviation), then you are calculating the cross-entropy between the variables. It also means that if you are using mean squared error loss to optimize your neural network model for a regression problem, you are in effect using a cross entropy loss.
