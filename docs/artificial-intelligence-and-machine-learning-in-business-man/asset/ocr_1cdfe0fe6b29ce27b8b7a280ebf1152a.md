# Recurrent Neural Network-Based Long Short-Term Memory 209

Input variables are passed through the block (Figure 13.1) and activated using Sigmoid function. The gate $f_t$ decides what information to discard from the state using Sigmoid activation function $s=\frac{1}{1+e^{-x}}$ over the inputs $h_{t-1}$ and $x_t$, where $h_{t-1}$ is the input from previous hidden layer and $x_t$ is the input from the network.

```
$f_t = \sigma(W_f \cdot x_t + U_f \cdot h_{t-1} + b_f)$ (13.1)
```

Short-Term Memory networks (LSTMs) cell is shown below in Figure 13.1. Next steps decide which new information is going to store in the cell state. A sigmoid layer (i.e., input layer, $i_t$) outputs the updating value and $tanh$ layer

```
$tanh = \left(\frac{e^x-e^{-x}}{e^x+e^{-x}}ight)$ creates a vector value $a_t$
```

```
$i_t = \sigma(W_i \cdot x_t + U_i \cdot h_{t-1} + b_i)$
na_t = \tanh(W_a \cdot x_t + U_a \cdot h_{t-1} + b_a)$ (13.2)
```

Point-wise multiplication of these two layers is used when updating the cell state $C_{t-1}$ into $C_t$. The update is carried out by adding the multiplication of $f_t$ & old state $C_{t-1}$ with $i_t * \tilde{C}_t$.

```
$c_t = f_t \cdot c_{t-1} + i_t \cdot a_t$ (13.3)
```

Finally, the output operation is to be performed. The filtered version of the cell state will be the output. First, output gate decides which of the cell state going to output. We let cell state through $tanh$ layer and multiply with result of output gate to get the final output.

```
$o_t = \sigma(W_o \cdot x_t + U_o \cdot h_{t-1} + b_o)$
h_t = o_t * \tanh(c_t)$ (13.4)
```

For the simplicity of the calculation, we regroup the above parameters in a matrix form.

```
$S_t = \begin{bmatrix} i_t \ f_t \ o_t \end{bmatrix}, W = \begin{bmatrix} W_i \ W_f \ W_o \end{bmatrix}, U = \begin{bmatrix} U_i \ U_f \ U_o \end{bmatrix} \text{ (simplified structure based on image)) \ b = \begin{bmatrix} b_i \ b_f \ b_o \end{bmatrix}$ (13.5)
```

Before back-propagating the differences of the actual value and predicted value using LSTM approach, we calculate the loss function or error of the model.

```
$e = \frac{(o-\hat{o})^2}{2}$ (13.6)
```