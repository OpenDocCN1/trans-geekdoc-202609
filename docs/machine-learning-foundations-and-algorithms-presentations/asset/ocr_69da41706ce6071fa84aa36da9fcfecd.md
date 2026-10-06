# # Output layers and loss functions

Binary classification:

+   - Output layer:

 Deterministic

 linear

$f = W^{(L)}h^{(L-1)} + b^{(L)}$

 hinge-loss

$l(\mathbf{x}_i, 	heta) = \max(0, 1 - y_i f(\mathbf{x}_i))$

![](bbox=[0.467, 0.655, 0.593, 0.715])

 Probabilistic

 sigmoid

$f = \sigma(\mathbf{W}^{(L)}\mathbf{h}^{(L-1)} + b^{(L)})$

 neg-loglike

+   - Loss function:

$l_i(\mathbf{x}_i, 	heta) = -c_i \log f(\mathbf{x}_i) - (1 - c_i) \log(1 - f(\mathbf{x}_i))$

![](bbox=[0.78, 0.715, 0.881, 0.775])