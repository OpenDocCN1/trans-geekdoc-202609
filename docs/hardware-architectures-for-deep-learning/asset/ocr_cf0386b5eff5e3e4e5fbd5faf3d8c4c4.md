# Hardware architectures for deep learning

![](bbox=[0.265, 0.075, 0.735, 0.335])

information to add, these decisions can now be made together. In this method, the information is forgotten only when its place is to store a new input data. In other words, a new value enters the state when an older item is forgotten. Equation (2.8) describes how the cell state will be calculated using this method:

$C_t = f_t * C_{t-1} + (1 - f_t) * \tilde{C}_t$  (2.8)

# 2.1.2 Gated recurrent units

The GRU model [11] is one of the most used RNN models that can be considered a variation of the LSTM. Among several changes that GRU makes on the baseline LSTM, its major modifications are twofold. First, it combines *forget* and *input* gates into a single *update* gate. Second, it also merges the cell state and hidden state. The resulting model (Figure 2.14) is simpler than standard LSTM models. GRUs have two gates: reset gate and *update* gate. Reset gate determines how to combine new input to the previous memory and *update* gate decides what information to throw away and what new information to add.

Equation (2.9) describes the behavior of this model, where $x_t, h_t, z_t, r_t$, and $\hat{h}_t$ represent input vector, output vector, update gate vector, rest gate vector, and current memory state:

```
$z_t = \sigma(W_z . [h_{t-1}, x_t])
r_t = \sigma(W_r . [h_{t-1}, x_t])
h_t = \tanh(W . [r_t * h_{t-1}, x_t])
h_t = (1 - z_t) * h_{t-1} + z_t * h_t$  (2.9)
```

Simply stated, unlike the LSTM model, the GRU is not required to use a memory unit to control the flow of information. Rather, it can directly use all hidden states without any control. GRUs have fewer parameters and can learn faster and need