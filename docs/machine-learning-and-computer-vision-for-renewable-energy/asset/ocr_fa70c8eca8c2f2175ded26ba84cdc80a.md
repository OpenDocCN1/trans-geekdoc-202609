# AI Approach Towards Optimal Finding of Renewable Sources of Energy

```
$f_t = \sigma(W_f[h_{t-1}, x_t] + b_f)$ (13)
```

```
$i_t = \sigma(W_i[h_{t-1}, x_t] + b_i)$ (14)
```

```
$\hat{C} = tanh(W_c[h_{t-1}, x_t] + b_c)$ (15)
```

```
$C_t = f_t * C_{t-1} + i_t * \tilde{C}$ (16)
```

```
$o_t = \sigma(W_o[h_{t-1}, x_t] + b_o)$ (17)
```

```
$h_t = o_t * tanh(C_t)$ (18)
```

where xt and ht–1 denote the input sequence component of the current timestep and the hidden state from the previous timestep, respectively. The forgetting, input, and output gates are denoted by ft, it, and Ot, respectively. These gates’ outputs are determined through the application of a sigmoid activation function, yielding values between 0 and 1. The forget gate (ft) governs the extent to which the previous cell state should be disregarded. Subsequently, the current cell state (Ct) undergoes an update involving it and ~C, where ~Ct represents the candidate cell state. The weight matrices, denoted as Wf, Wi, Wc, and Wo, optimize the behavior of these gates and are learned during the LSTM training process on input samples. Additionally, bf, bi, and bo are referred to as biases.

```
$C_{1,j} = ReLU(Z^* h_{1,j} + b_{1,j})$ (19)
```

Here, (*) signifies the convolution operation. The result feature map of the initial convolutional layer is represented as C1j, where h1j denotes the Jth convolution kernel, and b1j is the bias term. The equation includes a rectified linear unit (ReLU) as the activation function, introducing non-linearity to the input. The ensuing feature map is subsequently input into the following convolutional layer, undergoing additional processing to extract more advanced features. Consequently, the Ith convolutional layer CI, generating the output feature space Jth, can be expressed as depicted in the equation.

```
$C_{I,j} = ReLU(C^*_{I-1,j} h_{I,j} + b_{I,j})$ (20)
```