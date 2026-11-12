Let us consider that some information is coming from various sources, and the ANN node first adds up all these values coming from different sources and finally passes to the activation part.

Let us take an example to understand this better. From figure 7.2, take the RNN part. Now, let us say from branch h(t - 1) to h(t), the weight is w(t - 1).

And from branch I(t) to h(t), the weight is w(t), then the value at hidden node h(t) can be given as the summation of the product of the weight along with the previous state information as shown in the following equation:

```
h(t) = h(t - 1) x w(t - 1) + x(t) x w(t)
```

Now, this summation part is passed through the activation part, which can be written as follows:

```
Out(h(t)) = σ(h(t - 1) x w(t - 1) + x(t) x w(t))
```

Or we can write it as follows:

```
Out(h(t)) = 1 / e^-(h(t-1) x w(t-1) + x(t) x w(t))
```

Now, this output is being fed into the next neural network node, that is, h(t + 1), this is the behavior of a traditional ANN node being used in RNN.

So, now let us look at the gated unit of LSTM, which is used in place of RNN's hidden node. The Gated unit of LSTM is shown in figure 7.1. It has three gates, input gate (i), forget gate (f), and output gate (o). The sigmoid function is used to adjust the output between 0 and 1. The 0 value in forget gate disregards the old memory and resting the input gate to 0 disregards or ignores the newly computed state.

In figure 7.1, c(t) is a memory or cell update unit and it is used to store meaningful information. It is also known as the cell-state and is shown in figure 7.3. The gates shown in figure 7.1 are described in detail from section Forget gate to section Output gate.