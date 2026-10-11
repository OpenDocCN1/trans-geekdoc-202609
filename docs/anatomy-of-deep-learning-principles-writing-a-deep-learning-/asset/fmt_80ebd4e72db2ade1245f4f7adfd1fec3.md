
```python
def softmax(x):   
    a = np.max(x, axis=-1, keepdims=True)  
    e_x = np.exp(x - a)
    return e_x / np.sum(e_x, axis=-1, keepdims=True)

def cross_entropy_grad(Z, Y, onehot=False, softmax_out=False):  
    if softmax_out:
        F = Z
    else:
        F = softmax(Z)
    if onehot:
        dZ = (F - Y) / len(Z)
    else:
        m = len(Y)
        dZ = F.copy()
        dZ[np.arange(m), Y] -= 1
        dZ /= m
        # I_i = np.zeros_like(Z)
        # I_i[np.arange(len(Z)), Y] = 1    
        # return (F - I_i) / len(Z)  # Z.shape[0]
    return dZ
```

### 4.2.4 Derivation of back propagation of 2-layer neural network

#### 1. Reverse derivation of single sample

The backpropagation derivation algorithm calculates the gradient of the loss function with respect to the relevant variables of each layer according to the reverse calculation of the forward propagation of the neural network. The gradient $\frac{\partial\mathcal{L}}{\partial z^{[L]} z^{[L]}}$ of the loss function about the weighted sum of the output layer has been obtained before, and now we discuss how to find the gradient $\frac{\partial\mathcal{L}}{\partial z^{[l]} z^{[l]}}$ of the loss on the variables $W^{[l]}W^{[l]}$, $b^{[l]}b^{[l]}$, $a^{[l-1]}a^{[l-1]}$ of the layer based on Layer weighting and $z^{[l]}z^{[l]}$ gradient.

For a 2-layer neural network, how to find $\frac{\partial\mathcal{L}}{\partial W^{[2]} W^{[2]}},\frac{\partial\mathcal{L}}{\partial b^{[2]} b^{[2]}},\frac{\partial\mathcal{L}}{\partial a^{[1]} a^{[1]}}$?

$\mathcal{L}$ is $z^{[2]}z^{[2]}$ = ($z_1^{[2]}$, $z_2^{[2]}$, $z_3^{[2]}$) function, and $z^{[2]}z^{[2]}$ = $a^{[1]}a^{[1]}$$W^{[2]}$$W^{[2]}$ + $b$$b^{[2]}$, namely $z^{[2]}z^{[2]}$ is the function of $a^{[1]}a^{[1]}$, $W^{[2]}$$W^{[2]}$, $b^{[2]}$.

$$
\begin{matrix} 
z^{[2]} & {= (z_1^{[2]},z_2^{[2]},z_3^{[2]}) = (a_1^{[1]},a_2^{[1]},a_3^{[1]},a_4^{[1]})\begin{bmatrix} W_{11}^{(2)} & W_{12}^{(2)} & W_{13}^{(2)} \\ W_{21}^{(2)} & W_{22}^{(2)} & W_{23}^{(2)} \\ W_{31}^{(2)} & W_{32}^{(2)} & W_{34}^{(2)} \\ W_{41}^{(2)} & W_{42}^{(2)} & W_{44}^{(2)} \\ \end{bmatrix} + (b_1^{[2]},b_2^{[2]},b_3^{[2]})} \\ 
& {= (a_1^{[1]}W_{11}^{(2)} + a_2^{[1]}W_{21}^{(2)} + a_3^{[1]}W_{31}^{(2)} + a_4^{[1]}W_{41}^{(2)} + b_1^{[2]},} \\ 
& {\quad a_1^{[1]}W_{12}^{(2)} + a_2^{[1]}W_{22}^{(2)} + a_3^{[1]}W_{32}^{(2)} + a_4^{[1]}W_{42}^{(2)} + b_1^{[2]}} \\ 
& {\quad a_1^{[1]}W_{13}^{(2)} + a_2^{[1]}W_{23}^{(2)} + a_3^{[1]}W_{33}^{(2)} + a_4^{[1]}W_{43}^{(2)} + b_1^{[2]})} \\ 
\end{matrix}
$$

According to the chain derivation rule, there are:

$$
\frac{\partial\mathcal{L}}{\partial a_1^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}\frac{\partial z_1^{[2]}}{\partial a_1^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}\frac{\partial z_2^{[2]}}{\partial a_1^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_3^{[2]}}\frac{\partial z_3^{[2]}}{\partial a_1^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}W_{11}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{12}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{13}^{[2]}
$$

$$
\frac{\partial\mathcal{L}}{\partial a_2^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}\frac{\partial z_1^{[2]}}{\partial a_2^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}\frac{\partial z_2^{[2]}}{\partial a_2^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_3^{[2]}}\frac{\partial z_3^{[2]}}{\partial a_2^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}W_{21}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{22}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{23}^{[2]}
$$

$$
\frac{\partial\mathcal{L}}{\partial a_3^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}\frac{\partial z_1^{[2]}}{\partial a_3^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}\frac{\partial z_2^{[2]}}{\partial a_3^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_3^{[2]}}\frac{\partial z_3^{[2]}}{\partial a_3^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}W_{31}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{32}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{33}^{[2]}
$$

$$
\frac{\partial\mathcal{L}}{\partial a_4^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}\frac{\partial z_1^{[2]}}{\partial a_4^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}\frac{\partial z_2^{[2]}}{\partial a_4^{[1]}} + \frac{\partial\mathcal{L}}{\partial z_3^{[2]}}\frac{\partial z_3^{[2]}}{\partial a_4^{[1]}} = \frac{\partial\mathcal{L}}{\partial z_1^{[2]}}W_{41}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{42}^{[2]} + \frac{\partial\mathcal{L}}{\partial z_2^{[2]}}W_{43}^{[2]}
$$

Therefore:

$$
\begin{matrix} 
{\frac{\partial\mathcal{L}}{\partial a^{[1]}} = (\frac{\partial\mathcal{L}}{\partial a_1^{[1]}},\frac{\partial\mathcal{L}}{\partial a_2^{[1]}},\frac{\partial\mathcal{L}}{\partial a_3^{[1]}},\frac{\partial\mathcal{L}}{\partial a_3^{[1]}}) = (\frac{\partial\mathcal{L}}{\partial z_1^{[2]}},\frac{\partial\mathcal{L}}{\partial z_2^{[2]}},\frac{\partial\mathcal{L}}{\partial z_3^{[2]}})\begin{bmatrix} W_{11}^{(2)} & W_{21}^{(2)} & W_{31}^{(2)} & W_{41}^{(2)} \\ W_{12}^{(2)} & W_{22}^{(2)} & W_{32}^{(2)} & W_{42}^{(2)} \\ W_{13}^{(2)} & W_{23}^{(2)} & W_{33}^{(2)} & W_{43}^{(2)} \\ \end{bmatrix} = \frac{\partial\mathcal{L}}{\partial z^{[2]}}W^{[2]^T}} \\ 
\end{matrix}
$$

In the same way:
