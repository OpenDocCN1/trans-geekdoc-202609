![](bbox=[0.15, 0.1, 0.55, 0.27])

Figure 7. Structural diagram of the bidirectional gated recurrent unit [23].

$$\overrightarrow{h_{t}}=GRU(x_{t},\overrightarrow{h_{t-1}})$$ (10)

$$\overleftarrow{h_{t}}=GRU(x_{t},\overleftarrow{h_{t+1}})$$ (11)

In the above equations, GRU means the calculation process of the unidirectional GRU, $x_{t}$ is the input vector, $\overrightarrow{h_{t-1}}$ is the hidden state of the forward GRU, and $\overleftarrow{h_{t+1}}$ is the hidden state of the backward GRU.

The final output hidden state of the BiGRU combines the outputs of the forward and backward GRUs using a weight matrix calculated by Equation (12):

$$h_{t}=\overrightarrow{w_{h_{t}}}\overrightarrow{h_{t}}+\overleftarrow{w_{h_{t}}}\overleftarrow{h_{t}}+b_{t}$$ (12)

In the equation, $\overrightarrow{w_{h_{t}}}$ and $\overleftarrow{w_{h_{t}}}$ make up the weight matrix of the output layer and $b_{t}$ is the bias of the output layer.

# 3. Results

The XLNet-BiGRU-Att model was compared with the BERT-BiLSTM, BERT, and XLNet emotional analysis models. The parameter settings of each model are shown in Table 1. In the table, Batch Size is the amount of data for each parameter update, Epochs is the number of iterations in the training process, Embedding is the word vector dimension, and Lr is the learning rate set by the model. The parameters for XLNet-BiGRU-Att proposed in this paper are provided at the bottom of the table.

Table 1. Values of model parameters.

|Model | Batch Size | Epochs | Embedding | Lr |
|BERT-BiLSTM | 128 | 50 | 100 | 0.001 |
|XLNet | 256 | 50 | 100 | 0.001 |
|Bert | 64 | 300 | 768 | 0.001 |
|XLNet-BiGRU-Att | 256 | 300 | 768 | 0.001 |

Batch size is an important parameter for the training process, for which sizes of 2, 4, 8, 16, 32, 64, 128, 256, 512, . . . , are typically used. Within the appropriate range, the larger the batch is, the more accurate the descent direction is. Smaller batch sizes cause larger vibration, while larger batch sizes reduce the convergence speed, meaning that more epochs are needed, and may cause memory overflow. Convergence experiments with different batch sizes of 64, 128, and 256 were conducted; the learning curve is shown in Figure 8. It can be seen that the learning curve with the highest vibration has a batch size of 64. Although it reaches the minimum loss very fast, the loss begin to increase after 100 epochs. Therefore the training process with a batch size of 64 is not stable over 400 epochs. When the batch size is 128, the loss decreases slowly, and the model does not reach the best state