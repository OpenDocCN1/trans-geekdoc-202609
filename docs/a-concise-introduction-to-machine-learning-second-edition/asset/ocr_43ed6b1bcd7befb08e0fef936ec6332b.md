![](bbox=[0.318, 0.175, 0.493, 0.281])

(a) Spatial separation of activations.

![](bbox=[0.517, 0.175, 0.682, 0.281])

(b) Spatial separation of latent variables.

![](bbox=[0.318, 0.319, 0.413, 0.406])

(c) First basis.

![](bbox=[0.461, 0.319, 0.555, 0.406])

(d) Second basis.

![](bbox=[0.594, 0.319, 0.689, 0.406])

(e) Bias.

![](bbox=[0.318, 0.448, 0.493, 0.574])

(f) Original.

![](bbox=[0.517, 0.448, 0.682, 0.574])

(g) Reconstruction.

Figure 9.4: Autoencoder with two hidden neurons applied to digits.

where $w_1^{(2)}, \dots, w_N^{(2)}$ are the columns of $W^{(2)}$. The elements of the $m^{th}$ hidden column are the weights of the synapses connecting the $m^{th}$ hidden neuron to the output neurons. Since the activations are clearly a linear combination of the columns and the bias, the columns can be seen as the basis functions of the model space from which that dataset is generated. The bias is a shift in the data space, necessary to reconstruct all training data. If the dataset *mean centred*, such a shift is unnecessary and the bias is zero. The application of the transfer function ensures that the output lies again in the same range as the input.

The error function to minimize

```
$E(w) = \frac{1}{N} \sum_{n=1}^{N} ||x_n - \psi(\phi(x_n))||^2 + \beta\Omega_s + \lambda\Omega_w,$$
```