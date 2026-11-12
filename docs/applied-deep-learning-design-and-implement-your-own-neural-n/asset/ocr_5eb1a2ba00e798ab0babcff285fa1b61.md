![](bbox=[0.439, 0.102, 0.555, 0.345])

# Figure 7.6: Input i(t) or update $\gamma_u$ Gate of LSTM.j

The equation for the input gate is given as follows:

$\gamma_u = \sigma[(W_u (h_{t-1}, x_t) + b_u]$

Or

$i(t) = \sigma[(W(i)[h(t - 1), x(t)] + b(i)]$

It takes input as follows:

+   - The output from the previously hidden layer node, that is, h(t - 1).
+   - Finally, current input, that is, x(t).

And the output is passed through the sigmoid function, which results in values between 0 and 1.

# Output gate

It is also a sigmoid activation function-based ANN node. It decides what and how much part of the cell state will be provided as the output of the LSTM cell and will be the input to the next hidden state of the neural network.

It is also known as the focus vector. The equation for the output gate is given as follows:

$\gamma_o = \sigma[(W_o (h_{t-1}, x_t) + b_o]$

Or

$o(t) = \sigma[W (o)[h(t - 1, x(t)] + b(o)]$