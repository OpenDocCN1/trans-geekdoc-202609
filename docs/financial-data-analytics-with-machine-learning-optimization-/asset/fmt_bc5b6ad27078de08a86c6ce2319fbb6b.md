
The update for the weights at the output layer is therefore given by, for `k = 1, 2, ..., 100`, with a learning rate `η`,

[(15.9)](#c15.xhtml#R_c15-disp-0030)

```
w_{k,t}^o = w_{k,t-1}^o - (η / (√v_{k,t}^o + ε)) m_{k,t}^o
```

At the second hidden layer, we can work out using the chain rule that, at the `t`‐th iteration,

```
∂L / ∂w_{kj}^2 = (∂L / ∂ŷ) * (∂ŷ / ∂x̂^o) * (∂x̂^o / ∂ŷ_k^2) * (∂ŷ_k^2 / ∂x̂_k^2) * (∂x̂_k^2 / ∂w_{kj}^2)
              = -(y - ŷ_t) * 1_{(0,∞)} * (x̂_t^o) * w_{k,t-1}^o * 1_{(0,∞)} * (x̂_{k,t}^2) * ŷ_{j,t}^1
```

Similarly, the partial derivative of the loss function with respect to the weight associated with the input variables connecting to the first hidden layer can be computed by, at the `t`‐th iteration,
