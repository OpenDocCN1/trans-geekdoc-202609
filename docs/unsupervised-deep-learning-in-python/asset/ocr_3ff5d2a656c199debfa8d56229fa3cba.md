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