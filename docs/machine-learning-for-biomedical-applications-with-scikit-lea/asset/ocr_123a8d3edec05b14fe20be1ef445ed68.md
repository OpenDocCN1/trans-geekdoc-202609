(Eq. (10.1)):

```
$$\delta_{ik}^{(l)} = -\frac{\partial L_i}{\partial z_{ik}^{(l)}}$
```

The derivatives with respect to the weights $u_{jk}^{(l)}$ can be easily calculated using $\delta_{ik}^{(l)}$ using the chain rule:

```
$$\frac{\partial L_i}{\partial u_{jk}^{(l)}} = \frac{\partial L_i}{\partial z_{ik}^{(l)}} \cdot \frac{\partial z_{ik}^{(l)}}{\partial u_{jk}^{(l)}} = \delta_{ik}^{(l)} \cdot d_{ij}^{(l-1)}$
```

Once we have the weight gradients, we can update the weights using gradient descent (Eq. (10.7)) or another numerical technique, such as momentum. We will start the backpropagation by evaluating $\delta_{ik}^{(M)}$ for the last layer M:

```
$$\delta_{ik}^{(M)} = \frac{\partial L^{(M)}}{\partial z_{ik}^{(M)}} \cdot \frac{\partial f_M}{\partial a_{ik}^{(M)}}$
```

The value of $\delta_{ik}^{(M)}$ will depend on the choice of the loss function $L$ and the activation function $f_l$. For example, in the regression with sum of squared-errors loss and the identity activation, we might observe errors in the *predicted outputs* $\hat{y}_{ik} = a_{ik}^{(M)}$ compared to the expected outputs $y_i$:

```
$$\delta_{ik}^{(M)} = a_{ik}^{(M)} - \gamma_i$
```

Interestingly, the same result is obtained for the binary cross-entropy loss and the sigmoid activation. For more details on how to calculate these derivatives, refer to Sect. 9.1.2.

We will now show how we can backpropagate the output errors $\delta_{ik}^{(M)}$ into the other layers. We will use the chain rule to express $\delta_{jk}^{(l)}$ as follows:

```
$$\delta_{jk}^{(l)} = \sum_{k} \frac{\partial L_i}{\partial z_{ik}^{(l+1)}} \cdot \frac{\partial z_{ik}^{(l+1)}}{\partial z_{jk}^{(l)}} = \sum_{k} \delta_{ik}^{(l+1)} \cdot f'_{l+1}(z_{jk}^{(l+1)})$
```

where $f'_{jk}^{(l+1)} = \frac{\partial f_{l+1}}{\partial z_{jk}^{(l+1)}}$. We can therefore calculate the output errors $\delta_{jk}^{(l)}$ propagated to layer $l$ by summing up the output errors $\delta_{ik}^{(l+1)}$ weighted by the weights and the derivative of the activation for the layer $l+1$.

# **The training algorithm**

Training of the neural network can be summarized as follows:
 each iteration $n$ and for each sample $i$: