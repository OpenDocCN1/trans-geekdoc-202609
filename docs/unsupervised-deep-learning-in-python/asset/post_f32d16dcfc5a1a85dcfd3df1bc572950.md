
This is almost trivial to do since it's just adding a bitmask to your input, or in other words, you generate a random vector of 0s and 1s, and do an element by element multiplication on X, to get your new X.

Ex.

```
from theano.tensor.shared_randomstreams import RandomStreams
ng = RandomStreams()
bitmask = rng.binomial(n=1, p=p, size=X.shape)
X = bitmask * X
```

Typically, we set the probability of generating a 0 to something less than 50%, so perhaps maybe something something like 30%, but researchers have found that up to 50% still provides good results.

# Stacked Autoencoders

In this section we are going to explore what happens when we take a bunch of autoencoders and put them together in layers.

The basic algorithm is this.

You train one autoencoder, and then fix its weights. Then you throw out the last layer, keeping only the input to hidden part.

Next, you take the output of the hidden layer of the first autoencoder, and you make that the input to another autoencoder.

And you just repeat this process for multiple autoencoders.

Ex:

Train:
—o—
x z x'

Keep:
—o
x z

Train another:
—o—
z z2 z'

Keep another:
—o
z z2

Train another:
—o—
z2 z3 z2'

Keep another:
—o
z2 z3

Finally, you end up with a stack of autoencoders, each designed simply to learn a more compact version of the previous layer.

What you end up with is a deep unsupervised network:

—o—o—
z z2 z3

Since each time we use an autoencoder, we are trying to get a more compact representation than what we had in the previous layer, we are going to want each layer to be smaller in size than the previous layer.

Note that this doesn't necessarily have to be the case. We could in fact have a huge number of hidden units in the middle layer. Theoretically, if we had N training samples, and N hidden units, then we could get a perfect reconstruction because each of the N columns of W could be responsible for reproducing a different sample.

You would think that this would lead to severe overfitting, however researchers found it does not overfit, and even a number of hidden units greater than N can work.

In our code, we will use classes and objects to represent the ANN and Autoencoder.

This will help us compartmentalize our code much better, given the fact that we can have an arbitrary number of autoencoders.

We can then simply make the hidden output of each autoencoder the input into the next autoencoder.

# Greedy layer-wise pretraining

The process that we've just talked about is called “greedy layer-wise pretraining”.

The reason it is called greedy you should understand if you have ever studied algorithms. Greedy intuitively means you make the best short-sighted decision, which in our case is simply training one layer of the autoencoder.

While it is theoretically not optimal, it actually helps a lot with supervised training, which is the next step, and that is why we call it pretraining.

The last step in the process is to add a logistic regression layer to the end of the stacked autoencoders.

Once you’ve done that, you’ve made what is called a deep neural network.

Since the last layer with logistic regression will have randomized weights, we will still need to do some backpropagation.

But what we find is that doing backpropagation at this point doesn’t take long, because the autoencoder weights already put us in the neighborhood of the correct answer.

So we just need to do a few epochs of backpropagation to “fine-tune” the network.

Notice that there are new things here in terms of architecture and functional forms, just a new concept using old ideas.

You already know how to do all this - build a neural network, build a neural network with multiple layers, do gradient descent in Theano, etc.

In the code, note that we assume as usual that we have a function getData() that returns some NxD matrix for the input data and an Nx1 vector for the output targets.

We will load training data and test data, so we’ll have Xtrain of size NTrainXD, Ytrain of size NTrainX1, Xtest of size NtestXD, and Ytest of size NtestX1.

Note that there is code for both the squared error objective and cross-entropy objective. Typically we use cross-entropy for 0/1 targets, but you’ll see that it works even better than squared error. We will explain why later in the book.

Let’s see the code:

```
def relu(x):
  return x * (x > 0)
```

```
def error_rate(p, t):
  return np.mean(p != t)
```

```
def init_weights(shape):
    return np.random.randn(*shape) / np.sqrt(sum(shape))
```

```
import numpy as np
import theano
import theano.tensor as T
import matplotlib.pyplot as plt
```

```
from sklearn.utils import shuffle

class AutoEncoder(object):
    def __init__(self, M):
        self.M = M
```

```
def fit(self, X, learning_rate=0.5, mu=0.99, epochs=1, batch_sz=100, show_fig=False):
    N, D = X.shape
    n_batches = N / batch_sz

    W0 = init_weights(D, M)
    self.W = theano.shared(W0)
    self.bh = theano.shared(np.zeros(M))
    self.bo = theano.shared(np.zeros(D))
    self.params = [self.W, self.bh, self.bo]
    self.forward_params = [self.W, self.bh]

    self.dW = theano.shared(np.zeros(W0.shape))
    self.dbh = theano.shared(np.zeros(M))
    self.dbo = theano.shared(np.zeros(D))
    self.dparams = [self.dW, self.dbh, self.dbo] # Inferred from context logic

    X_in = T.matrix('X_%s' % self.id)
    X_hat = self.forward_output(X_in)

    # attach it to the object so it can be used later
    # must be sigmoid because the output is also a sigmoid
    H = T.nnet.sigmoid(X_in.dot(self.W) + self.dbh)
    self.hidden_op = theano.function(
    inputs=[X_in],
    outputs=H,
    )

    # cost = ((X_in - X_hat) * (X_in - X_hat)).sum() / N
    cost = -(X_in * T.log(X_hat) + (1 - X_in) * T.log(1 - X_hat)).sum() / N
    cost_op = theano.function(
    inputs=[X_in],
    outputs=cost,
    )

    updates = [
    (p, p + mu*dp - learning_rate*T.grad(cost, p)) for p, dp in zip(self.params, self.dparams)
    ] + [
    (dp, mu*dp - learning_rate*T.grad(cost, p)) for p, dp in zip(self.params, self.dparams) # Note: OCR error corrected 'mu'
    ]
    train_op = theano.function(
    inputs=[X_in],
    updates=updates,
    )

```
costs = []
for i in xrange(epochs):
    print "epoch:", i
    X = shuffle(X)
for j in xrange(n_batches):
    batch = X[j*batch_sz:(j*batch_sz + batch_sz)]
    train_op(batch)
    the_cost = cost_op(X) # technically we could get the cost for Xtest
    print "j / n_batches:", j, "/", n_batches, "cost:", the_cost
    costs.append(the_cost)
```
```
if show_fig:
    plt.plot(costs)
    plt.show()
```

```
def forward_hidden(self, X):
    Z = T.nnet.sigmoid(X.dot(self.W) + self.bh)
    return Z
```

```
def forward_output(self, X):
    Z = self.forward_hidden(X)
    Y = T.nnet.sigmoid(Z.dot(self.W.T) + self.bo)
    return Y
```

```
@staticmethod
def createFromArrays(W, bh, bo):
    ae = AutoEncoder(W.shape[1])
    ae.W = theano.shared(W)
    ae.bh = theano.shared(bh)
    ae.bo = theano.shared(bo)
    ae.params = [ae.W, ae.bh, ae.bo]
    ae.forward_params = [ae.W, ae.bh]
```

```
class DNN(object):
    def __init__(self, hidden_layer_sizes, UnsupervisedModel=AutoEncoder):
        self.hidden_layers = []
        for M in hidden_layer_sizes:
            ae = UnsupervisedModel(M)
            self.hidden_layers.append(ae)
```

```
def fit(self, X, Y, Xtest, Ytest, pretrain=True, learning_rate=0.01, mu=0.99, reg=0.1,
epochs=1, batch_sz=100):
    # greedy layer-wise training of autoencoders
    pretrain_epochs = 1
    if not pretrain:
        pretrain_epochs = 0

    current_input = X
    for ae in self.hidden_layers:
        ae.fit(current_input, epochs=pretrain_epochs)

    # create current_input for the next layer
    current_input = ae.hidden_op(current_input)

    # initialize logistic regression layer
    N = len(Y)
    K = len(set(Y))
    W0 = init_weights(self.hidden_layers[-1].M, K)
    self.W = theano.shared(W0)
    self.b = theano.shared(np.zeros(K))

    self.params = [self.W, self.b]
```

```
for ae in self.hidden_layers:
    self.params += ae.forward_params

# for momentum
self.dW = theano.shared(np.zeros(W0.shape))
self.db = theano.shared(np.zeros(K))
self.dparams = [self.dW, self.db]
for ae in self.hidden_layers:
    self.dparams += ae.forward_dparams

X_in = T.matrix('X_in')
targets = T.vector('Targets')
pY = self.forward(X_in)

# squared_magnitude = [(p*p).sum(p) for p in self.params]
# reg_cost = T.sum(squared_magnitude)
cost = -T.mean(T.log(pY[T.arange(pY.shape[0]), targets]))+# reg*reg_cost
prediction = self.predict(X_in)
cost_predict_op = theano.function(
inputs=[X_in, targets],
outputs=[cost, prediction],
)
```
