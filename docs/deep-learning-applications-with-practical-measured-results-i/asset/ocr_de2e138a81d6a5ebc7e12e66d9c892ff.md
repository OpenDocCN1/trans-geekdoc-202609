![](bbox=[0.25, 0.14, 0.75, 0.36])

Figure 1. An overview of the ConvLSTM Encoder–Decoder network (ConvLSTM).

Multivariate ALSTM Fully Convolutional Networks models are comprised of temporal convolutional blocks and an LSTM block, as depicted in Figure 2. The feature extractor consists of three stacked temporal convolutional blocks. In addition, the first two convolutional blocks conclude with a squeeze and excite block.

![](bbox=[0.22, 0.48, 0.82, 0.7])

Figure 2. Modified multivariate attention LSTM-FCN (MALSTM-FCN) network structure for time series forecasting.

We consider this model structure as a parallel structure of CNN (temporal convolutional blocks) and RNN (LSTM block). In order to study the regression problem, the final softmax layer used for classification is changed to a fully connected layer with 24 nodes.

# 3.4. M-TCN Model

The main characteristic of CNN is a local feature by convolving filters. For time series forecasting, the local correlation is reflected in the continuous change over a period of time within a small time slot. In addition, RNN models, such as LSTM, have always been considered as the best standard method to solve sequence problems; however, RNNs cannot be parallel, resulting in huge time-consumption compared to that of CNN. From those considerations, the overall framework of the model is designed based on CNN. Our aim is to distill the best practices in designing convolutional networks to be flexible and stable frameworks with a simple architecture and high efficiency for multivariate time series