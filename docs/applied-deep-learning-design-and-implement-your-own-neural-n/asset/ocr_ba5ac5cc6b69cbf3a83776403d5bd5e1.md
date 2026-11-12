And finally, the output of the hidden layer is given by the following:

```
$h_t = \gamma_o \odot \tanh c_t$
```

Or

```
$h(t) = o(t) \otimes tanh(c(t))$
```

So, the previously-mentioned steps describe the forward propagation in LSTM. Now, let us discuss how the process of backpropagation takes place in LSTM.

# Backpropagation in LSTM

The main purpose of backpropagation is to train neurons in the neural network. LSTM also uses a technique named backpropagation with time, similar to RNN.

But in RNN, the process of backpropagation updates only the neurons, whereas in LSTM, the process of backpropagation, along with updating the weights of the neurons, also makes learning the Gated units.

![](bbox=[0.14, 0.46, 0.86, 0.79])

Figure 7.8: Backpropagation in LSTM

We have already discussed weight updation in RNN using backpropagation over time. The process of the weight updation in LSTM is also the same as that of the RNN, so we will not discuss the weight updation process of LSTM in this chapter.