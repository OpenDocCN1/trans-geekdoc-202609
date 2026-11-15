The output gates, as shown in the following figure, compute the output from the LSTM cell based on input $X_t$, previous layer output $h_{t-1}$ and current state $C_t$:

![](bbox=[0.105, 0.165, 0.895, 0.555])

Illustration of output gate

The output based on output gate can be computed as follows:

```
$O_t = \sigma(S_o x_t + W_o h_{t-1} + b_o)$
$h_t = O_t * \tanh(C_t)$
```