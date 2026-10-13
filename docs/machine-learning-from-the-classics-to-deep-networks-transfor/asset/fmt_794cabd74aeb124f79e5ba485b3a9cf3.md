
which leads to Eq. [(18.44)](#Chp018_885-995_B978044329238500024X.xhtml#deq80). Note, however, that this interpretation does not hold true if classes are mutually exclusive, which is the case in most classification tasks.

One can easily see that combining the above versions of the cross-entropy function with the logistic sigmoid nonlinearity “frees” the gradient of the cost, with respect to the synaptic weights of the *k*th output neuron, of the dependence on the derivative of the respective activation function. It can easily be shown that (Problem [18.7](#Chp018_885-995_B978044329238500024X.xhtml#o0050))

```
\frac{\partial J}{\partial\mathbf{\theta}_{j}^{L}} = \sum\limits_{n = 1}^{N}\delta_{nj}^{L}\mathbf{y}_{n}^{L - 1},\ j = 1,2,\ldots,k_{L},
```

where `δ[nj]^(L) = y[nj](ŷ[nj] − 1)` for the cross-entropy loss in Eq. [(18.41)](#Chp018_885-995_B978044329238500024X.xhtml#deq77) and `δ[nj]^(L) = ŷ[nj] − y[nj]` for the case of Eq. [(18.44)](#Chp018_885-995_B978044329238500024X.xhtml#deq80). Note that `y[n]^(L − 1)` is the vector of the outputs of the last hidden layer, `L − 1`.
