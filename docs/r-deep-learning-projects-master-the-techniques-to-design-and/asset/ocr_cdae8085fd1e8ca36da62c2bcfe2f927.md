Computation of the gradients \(\Delta w\) can be realized through the **backpropagation algorithm**.
The idea of the backpropagation algorithm is the following, we first travel through the
network and compute all outputs of the hidden layers and output layer; then moving
backward from the last layer, we calculate how much each node contributed to the error in
the final output and propagate it back to the previous layers. In our single-layer network,
the detailed steps are:

+   1. Compute \(a^{(2)}\) for the hidden layer and feed them to the output layer to compute
+   the outputs \(a^{(3)}\)

+   2. For the output layer, compute the derivative of the cost function of one sample
+   \(\delta_k^{(3)} = \frac{\delta}{\delta z_k^{(3)}} j(W) = -(y_k - a_k^{(3)}) . f'(z_k^{(3)})\)
+   
+   \(j(W)\) with regards to each unit,
+   
+   \(\delta^{(3)} = -(y - a^{(3)}) . f'(z^{(3)})\), rewritten for the entire layer

+   3. For the hidden layer, we compute the error term \(\delta^{(2)}\) based on a weighted average
+   of \(\delta^{(3)} : \delta^{(2)} = ((W^{(2)})^T \delta^{(3)}). f'(z^{(2)})\)

+   4. Compute the gradients applying the chain rule:

```
\(\triangle W^{(2)} = \frac{\partial J(W)}{\partial z_k^{(3)}} \frac{\partial z_k^{(3)}}{\partial W^{(2)}} = \delta^{(3)} (a^{(2)})^T\)
```

```
\(\triangle W^{(1)} = \frac{\partial J(W)}{\partial z_k^{(2)}} \frac{\partial z_k^{(2)}}{\partial W^{(1)}} = \delta^{(2)} (x)^T\)
```

We repeatedly update all weights by taking these steps until the cost function converges.

After a brief review of the single-layer network, we can then apply it as the second solution
to our digit classification project.

Again, we use the `nnet` package to implement our single-layer network:

```
> model_nn <- nnet(label ~ ., data=data_train, size=50, maxit=300,
MaxNWts=100000, decay=1e-4)
# weights: 39760
initial value 108597.598656
iter 10 value 27708.286001
iter 20 value 16027.005297
iter 30 value 14058.141050
iter 40 value 12615.442747
iter 50 value 11793.700937
```