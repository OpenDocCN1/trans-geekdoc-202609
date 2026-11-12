\(\gamma_f = \sigma[(W_f (h_{t-1}, x_t) + b_f]\) (7.13)
\(\gamma_u = \sigma[(W_u (h_{t-1}, x_t) + b_u]\) (7.14)

The output gate is parameterized using \((W_o, b_o)\), where \(W_o\) is weight and \(b_o\) is corresponding bias with input as \((h_{t-1} x_t)\).

\(\gamma_o = \sigma[(W_o (h_{t-1}, x_t) + b_o]\) (7.15)

In the case of GRU, the final output is equal to the cell update; that is, \(h_t = c_t\) but in the case of LSTM output gate is used to generate the final output, as shown in equation (7.16):

\(h_t = \gamma_o \odot \tanh c_t\) (7.16)

The LSTM gated unit described previously is pictured in figure 7.1:

![](bbox=[0.22, 0.38, 0.78, 0.75])

Figure 7.1: LSTM Gated unit

Why are we moving from hidden layer nodes to Gated units? What is the advantage of using Gated units here in LSTMs?

Suppose for a sequence prediction example, we want to predict the sequence, say after the 500th timestamp in place of the 5th or 10th timestamp, the hidden layer nodes used in RNN forget all the information by then, but the gated units used in