# Inversion of Complex Surface Heat Flux Based on ConvLSTM

This network is a fully connected network. Its input is a tensor with the dimension of $L 	imes 1 	imes N_t$, where $L$ is the number of training samples and $N_t$ is the number of time samples. Each time sampling point acts as a separate node of the input, and the output of the network is the weight factor $w_0$ of each point affected by the heat flux or temperature of all points on the outer surface. All points on the inner surface are traversed to obtain $N$ intermediate functions. These functions are weighted in the network 2 to obtain the final output, which is the heat flux of the $i$-th point on the outer surface, as displayed in Figure 3.7:

# 3.3.3.2 Recurrent Neural Network

The temperature at the sampling is affected by the heat flux at times and locations during the whole heat transfer process of the experiment. The influence of two characteristics of time and space on the temperature should be taken into account when building the neural network, so the neural network used should contain two characteristics at the same time. Since the inverse heat problem to be solved in this experiment can be considered an evolutionary inverse problem of a dynamic problem, the RNN is a potential solution.

The classical RNN [23] is a kind of neural network used to process sequence data. Time series data refers to the data collected at different time points, and there is a logical relationship between the early and late data. For a standard RNN, with forward propagation algorithm is quite clear. The formula can be expressed in the following form:

```
$h(t) = \phi(Uz(t) + Wh(t) + b)$
```

```
$o(t) = Vh(t) + c$
```

```
$y(t) = \sigma(o(t))$
```

where $\phi$ and $\sigma$ are activation functions, $U, W$ and $V$ are weights, while $b$ and $c$ are offsets. The classical RNN structure is prone to suffer from the vanishing problem, so it is difficult to solve the long-term memory problem. In order to solve this problem, researchers have constructed a long-term memory network (LSTM) [24]. There are three gates in a single neuron of LSTM to protect and control the cell state: the first is called the forget gate, which will read two kinds of information $h_{t-1}$ and $x_t$ from the previous step, and output a value of 0-1 to the cell state $C_{t-1}$ to influence the influence of the previous cell state on the subsequent state. The formula can be written as follows:

```
$f_t = \sigma(W_f[h_{t-1}, x_t] + b_f)$
```

Next, an update gate determines the new memory stored in the cell state, which represents the selective forgetting process of information. Finally,