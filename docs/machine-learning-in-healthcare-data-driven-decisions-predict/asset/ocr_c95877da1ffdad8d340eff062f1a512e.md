In eq. (14) \( x_t \in R^d \) is the feature vector at time \( t \). At each time step \( t \), an LSTM cell computes.

# Forget gate:

```
\( f_t = \sigma \left( W_f \cdot [h_{t-1}, x_t] + b_f \right) \) (15)
```

# Input gate:

```
\( i_t = \sigma(W_i \cdot [h_{t-1}, x_t] + b_i) \) (16)
```

```
\( \hat{C}_t = tanh(W_c \cdot [h_{t-1}, x_t] + b_c) \) (17)
```

# Cell state update:

```
\( C_t = f_t \odot C_{t-1} + i_t \odot \hat{C}_t \) (18)
```

# Output gate:

```
\( O_t = \sigma(W_o \cdot [h_{t-1}, x_t] + b_o) \) (19)
```

```
\( h_t = o_t \odot tanh(C_t) \) (20)
```

In equation the above equations, \( W_f, W_i, W_c, \text{ and } W_o \) are the weight matrices, \( b_f, b_i, b_c, \text{ and } b_o \) are the biases, \( \sigma(.) \) is the sigmoid activation, \( tanh(.) \) is the hyperbolic tangent activation, and \( \odot \) is the element-wise multiplication.

The final prediction form LSTM use the final hidden state \( h_r \) for prediction:

```
\( \hat{y}_{LSTM} = \phi(W_y \cdot h_r + b_y) \) (21)
```

where \( \phi(.) \) is an activation function. Then combine XGBoost, CNN, and LSTM predictions as follows.

# Form CNN (image-based data):

```
\( \hat{y}_{CNN} = f_{CNN}(I; \theta_{CNN}) \) (22)
```

# From LSTM (longitudinal patient data):

```
\( \hat{y}_{LSTM} = f_{LSTM}(X; \theta_{LSTM}) \) (23)
```

# From XGBoost (structured tabular data):

```
\( \hat{y}_{XGB} = f_{XGB}(Z) \) (24)
```

In eqs. (22)–(24) \( I \) is the patient data, \( X \) is the sequential medical records, and \( Z \) is the structured tabular patient data. The ensemble fusion strategy combines these predictions as a weighted average ensemble as follows:

```
\( \hat{y}_{final} = \alpha . \hat{y}_{CNN} + \beta . \hat{y}_{LSTM} + \gamma . \hat{y}_{XGB} \) (25)
```