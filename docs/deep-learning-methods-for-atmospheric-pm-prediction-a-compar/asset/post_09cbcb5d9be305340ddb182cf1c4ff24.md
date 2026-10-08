
# B. Cui et al.

# Atmospheric Pollution Research 14 (2023) 101833

![](img/563998e5c032c2da6a0d846b91d4c36e_6_0.png)

Fig. 6. Computational diagram of the attention mechanism.

the input.
The multi-head attention mechanism allows the model to focus not only on the position of the sequence, but also on the different heads, thereby allowing outputs of multiple independent-head attention (SHA) layers to serve as inputs in multiple sequence steps. To consider relationships between each pollution factor and the meteorological conditions, the multi-head attention mechanism treats each attention position, feature, and value as a whole. In this paper, attention layers serve to maximize the model's ability to capture the long-range dependencies:

## 2.6.1. CNN attention unit

This unit is based on the standard convolutional module and includes an attention mechanism to extract the features that have a significant impact on health. The CNN module consists of multiple layers of one-dimensional networks, with each layer consisting of a convolution, a normalization, and a linear layer. The attention mechanism consists of two parts, one for feature aggregation and the other for scale recovery, and is integrated with the output of the CNN layers. In this paper, the CNN model is a subsequence of the original time-series data, while the attention mechanism is used to extract relevant features. The attention mechanism is more powerful than that of the CNN, and it overwrites the CNN input with features. The outputs of the CNN modules are multiplied element-wise with the outputs of the attention mechanism, and the importance of each feature is determined relative to those of the others.

```
$MultiHead(Q, K, V) = Concat(head^1, ..., head^h)W^O$
```

where $head = Attention(QW^Q, KW^K, VW^V)$, where $W^Q, W^K, W^V \in \mathbb{R}^{d \times d_k}$ and $W^O \in \mathbb{R}^{hd_k \times d}$, where $h$ is the multi-head attention mechanism:

## 2.5.2. Encoder

In this study, the encoder consists of a sequence of $N=6$ identical units, each containing two sub-layers. Each encoder layer is identical to two remaining sub-layers that connect the input of the previous layer, and then each layer is normalized. The output of each sublayer is shown in Equation (7), where sublayer ($y$) is a function of $x$. We use residual connections across all layers, including the embedding layer, to produce dimensional output: $d = d = model\_size = 512$

```
$Output = LayerNorm(x + Sublayer(x)) $
```

## 2.6. LSTM unit

A gate is used to control the LSTM to extract long temporal patterns in the time series. The structure of the LSTM consists of a gate, a memory gate, and an output gate. The LSTM model consists of four gates: input gate, forget gate, cell gate, and output gate. Whether information in the unit is retained or not is determined by the forget gate. The new information in the input and the degree of feature extraction is controlled by the input gate. The output gate only passes the hidden state. The formula for the gate used to calculate the LSTM is:

```
$f_t = \sigma(W_f \cdot [h_{t-1}, x_t] + b_f)$
```

```
$i_t = \sigma(W_i \cdot [h_{t-1}, x_t] + b_i)$
```

```
$\tilde{c}_t = tanh(W_c \cdot [h_{t-1}, x_t] + b_c)$
```

```
$c_t = f_t \cdot c_{t-1} + i_t \cdot \tilde{c}_t$
```

```
$h_t = o_t \cdot tanh(c_t)$
```

## 2.6. LSTM-attention unit

A $PM_{2.5}$ concentration prediction model is constructed on a convolutional and LSTM model with an attention mechanism. The architecture, referred to as the CA in this study, is shown in Fig.1. The CA consists of a CNN attention unit, an LSTM. The C-attention unit integrates continuous overlapping sequences as its data input, while the LSTM uses the outputs of the C-unit as its input. Its prediction is resulted by the final layer of the LSTM unit:

![](img/563998e5c032c2da6a0d846b91d4c36e_7_0.png)

Fig. 7. CNN-LSTM attention model. CNN-LSTM, convolutional neural network long-short term memory mechanism.

$z_i = o_i * \tanh(A_i)$

where $z_i$ and $x_i$ are the outputs at time $t$ and $t-1$, respectively; $q_i$ is the input at time $t$; $f_i, l_i$ and $o_i$ are the outputs of the forget, input, and output gates, and $A_i$ is the activation function.

where $y_i$ and $y_i'$ are the target value and output model, respectively, $y_i$ is the mean of the target values.

## 7.2. Evaluation

The $R^2$, MAE, and MSE were used to evaluate the performance. The closer to 1, the better the performance. These metrics are calculated as:

$R^2 = 1 - \frac{\sum(y_i - \hat{y}_i)^2}{\sum(y_i - \bar{y})^2}$

$MAE = \frac{1}{n} \sum|y_i - \hat{y}_i|$

$MSE = \frac{1}{n} \sum(y_i - \hat{y}_i)^2$

## 3. Results and discussion

### 3.1. Training and results

The results of the Transformer and CNN-LSTM models are shown in Fig. 8. The CNN-LSTM-attention model effectively captures the gradient of concentration in each direction, and like the transformer model, it predicts time points beyond 1000 min well. However, Fig a and b show that for the first 1000 min, PM2.5 concentrations are consistent with the Transformer model, indicating that the Transformer is more effective in capturing the hidden relationships between the factors and meteorological factors.

### 3.2. Performance prediction

The hourly data from January 2013 to February 2015 was used as the learning data to train the model and predict the hourly data from January 2016 to February 2017. The learning data were divided into season, namely (March-May), summer (June-August), autumn (September-November), and winter (December-February) groups, respectively, for testing the model. From Fig. 10, the top curves in each panel present the values of PM2.5 concentration, the values predicted using the CNN-LSTM model and the values predicted using the Transformer model provides a more accurate prediction over the entire range. It should be noted that PM2.5 pollution was remarkably correlated with the local weather conditions, especially in autumn and winter when the air masses had a short duration, and the wind speeds were low, which were not conducive to the pollutant's diffusion, and an increase in the PM2.5 concentration. The data circled by red dashed lines in Fig. 9c shows that the Transformer model accurately predicted
