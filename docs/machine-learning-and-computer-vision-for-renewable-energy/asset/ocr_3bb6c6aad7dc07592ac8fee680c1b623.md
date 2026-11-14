# Electricity Demand Forecasting using Dual Stream TBATS-CNN-LSTM Architecture

Figure 2. Architecture of CNN

![](bbox=[0.143, 0.172, 0.873, 0.432])

2021), making the algorithm to add or remove information to the cell state called Get. An input gate (\(i_t\)), forget gate (\(f_t\)) and output gate (\(o_t\)) can be defined as

\(f_t = \sigma(W_f [h_{t-1, x_t}] + b_f)\) (8)

\(i_t = \sigma(W_i [h_{t-1, x_t}] + b_i),\) (9)

\(C_t = \tanh(W_c [h_{t-1, x_t}] b_c),\)
\(C_t = f_t C_{t-1} + i_t C_t,\)
\(O_t = \sigma(W_o [h_{t-1, x_t}] + b_0),\)
\(h_t = O_t \tanh(C_t)\) (10)

See Figure 3 for more illustration on LSTM architecture.

# Convolutional Neural Network-Long Short-Term Memory

A potent combination of CNN-LSTM (Convolutional Neural Network-Long Short-Term Memory) has been proposed to limit the employment of CNN for getting invaluable knowledge and learning ability with greater efficiency of the LSTM algorithm in a time-series-internal-representation-dependent manner