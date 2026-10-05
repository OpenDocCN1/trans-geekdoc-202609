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