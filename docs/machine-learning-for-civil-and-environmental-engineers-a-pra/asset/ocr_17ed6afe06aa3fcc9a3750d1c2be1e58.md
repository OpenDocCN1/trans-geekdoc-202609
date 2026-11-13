# How does it work?

In an LSTM, the input gate determines which of the input values should be used to change the memory. In this process, the sigmoid function determines whether to allow 0 or 1 values through, and the tanh function assigns weight to the importance of the data on a scale of –1 to 1. Next to the input gate is the forget gate, and this gate identifies which part of the data should be removed (also via a sigmoid function). For each number in the cell state C_{t-1}, it looks at the preceding state (h_{t-1}) and the content input (X_t) and produces a number between zero (omit) and one (keep). Finally, the output gate with a sigmoid function determines whether to allow 0 or 1 values through. This gate also homes a tanh function that assigns weight to the values provided, determining their relevance on a scale of –1 to 1 and multiplying it with the sigmoid output.

# 4.1.1.15.1 Visualizing the RF Algorithm

Figure 4.19 shows the anatomy of an LSTM and outlines the cells and different gates involved in an LSTM.

![](bbox=[0.085, 0.295, 0.42, 0.455])

Figure 4.19 Sketch of LSTM.

# 4.1.1.15.2 Programming This Algorithm

The Python and R codes for LSTM are provided below:

# Python Package

```
```python
from keras.layers import LSTM
model = Sequential()
model.add(LSTM())
```
```

# R Package

```
```r
>library(keras)
>library(tensorflow)
>install_keras()
>install_tensorflow
>lstm_model %>% 
  layer_lstm(units = 50,
             batch_input_shape = c(1, 12, 1),
             return_sequences = TRUE,
             stateful = TRUE) %>% 
  layer_dropout(rate = 0.5) %>% 
  layer_lstm(units = 50,
             return_sequences = TRUE,
             stateful = TRUE) %>% 
  layer_dropout(rate = 0.5) %>% 
  time_distributed(keras::layer_dense(units = 1))
```
```