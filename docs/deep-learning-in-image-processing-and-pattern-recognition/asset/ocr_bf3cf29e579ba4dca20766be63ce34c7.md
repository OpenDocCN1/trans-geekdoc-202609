The input for the reset and update gates is obtained through the fully connected layer that operates on the current input $x_t$ and the hidden state of the previous time point $h_{t-1}$. The reset gate $r_t$ is calculated by Equation (6), and $\sigma$ is a Sigmoid function which is used as an activation function. Thus, the result of the reset gate is a vector with a value between 0 and 1 which is similar to the gate in circuit. This value is then used to determine the relevancy of the hidden state of the previous time point. The candidate hidden state $\tilde{h}_t$ is determined by the input $x_t$, reset gate $r_t$, and prior hidden state $h_{t-1}$, as shown in Equation (7): the prior hidden state contains the information of both the current time and previous time, and is an important component of the current hidden state, although it is not the real current hidden state.

```
$r_t = \sigma(x_t w_{xr} + h_{t-1}w_{hr} + b_r)$  (6)
```

In the above equation, $t$ is the current time point, $t-1$ is the last time point, $x_t$ is the input vector of the current time, $h_{t-1}$ is the hidden state of the previous time point, $w_{hr}$ and $w_{xr}$ make up the weight matrix of the reset gate, and $b_r$ is the bias of the reset gate.

```
$\tilde{h}_t = \tanh(x_t w_{xh} + (r_t \circ h_{t-1})w_{hh} + b_h)$  (7)
```

Here, $w_{xh}$ and $w_{hh}$ make up the weight matrix of the candidate hidden state and $b_h$ is the bias of the candidate hidden state.

The update gate $z_t$ is calculated using Equation (8) and $\sigma$ is a Sigmoid function which is used as an activation function. Thus, the result of the reset gate is a vector with a value between 0 and 1, which is then used to determine the element of the previous hidden state that should be updated by the current candidate hidden state. For this reason, it is called the update gate.

```
$z_t = \sigma(x_t w_{xz} + h_{t-1}w_{hz} + b_z)$  (8)
```

In this equation, $x_t$ is the current input vector, $h_{t-1}$ is the hidden state of the previous time point, $w_{xz}$ and $w_{hz}$ make up the weight matrix of the update gate, and $b_z$ is the bias of the update gate.

The hidden state is the output of the GRU calculated using the candidate hidden state and the previous hidden state in Equation (9):

```
$h_t = z_t \circ h_{t-1} + (1 - z_t) \circ \tilde{h}_t$  (9)
```

Here, $z_t$ is the update gate, $h_{t-1}$ is the previous hidden state, $\tilde{h}_t$ is the current candidate hidden state, and $h_t$ is the current hidden state, which is the output of the GRU.

For the GRU, the output is only affected by the current input and the previous hidden state, and is not related to the subsequent state, making the GRU a unidirectional model. However, in order to extract effective features it is necessary to pay attention to the current information, the previous information, and the subsequent information. It can be easily understood that combining these contexts makes it easier to understand textual information. Based on this idea, BiGRU is proposed to combine forward GRU and backward GRU, making the output result the combination of the two GRUs by weight matrix. The structure of BiGRU is presented in Figure 7: it is composed of an input layer, forward GRU, backward GRU, and output layer. In the figure, $h_t$ is the hidden state of the forward GRU, $\overleftarrow{h}_t$ is the hidden state of the backward GRU, $x_t$ represents the input vectors of BiGRU, $\hat{h}_t$ is the output hidden state of BiGRU, and $x_t \in R^{k \times d}$, where $k$ is the batch size and $d$ is the length of the input vectors. The forward hidden state $h_t \in R^{k \times d}$ and the backward hidden state $\overleftarrow{h}_t \in R^{k \times d}$ are calculated using Equations (10) and (11).