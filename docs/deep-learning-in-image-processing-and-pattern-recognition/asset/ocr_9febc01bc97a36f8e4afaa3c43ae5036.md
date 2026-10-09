In order to further verify the superiority of DRSN-BiGRU in natural situations, the algorithm was also compared with DCNN-LSTM, CNN-BiGRU, and DRN-BiGRU in MELD dataset, and the results are shown in Table 7.

**Table 7.** Comparison result on MELD.

| Model | Neutral | Angry | Fear | Joy | Sadness | Disgust | Surprise |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| DCNN-LSTM | 68.32 | 52.13 | 54.21 | 50.32 | 55.43 | 53.31 | 56.65 |
| CNN-BiLSTM | 71.65 | 47.89 | 45.68 | 61.86 | 55.59 | 48.87 | 59.54 |
| DRN-BiGRU | 70.23 | 58.56 | 62.78 | 64.45 | 59.35 | 52.31 | 60.34 |
| DRSN-BiGRU | 74.59 | 73.52 | 70.20 | 73.27 | 71.63 | 60.19 | 70.56 |

The analysis of Table 7 reveals a notable decline in the performance of the four models on MELD, as opposed to their performance on CASIA and IEMOCAP. This outcome underscores the influence of naturalistic emotional complexity on the efficacy of these models. It is worth noting that DNSN-BiGRU yields the highest recognition accuracy for the seven emotions in question, establishing it as the optimal model for MELD.

In conclusion, the addition of residual shrinkage unit has led to significant improvements in speech emotion recognition accuracy for DRSN-BiGRU compared to CNN-BiGRU, DCNN, and DRN-BiGRU models. This is attributed to the residual network’s capability of transmitting shallow information to the deeper network and the automatic removal of redundant features by the shrinkage unit. These experiments confirm the effectiveness of this method in speech emotion recognition.

# **5.3. Complexity Analysis and Discussion**

The time complexity of a Deep Residual Shrinkage Network (DRSN) includes both forward and backward propagation. During forward propagation, the computing time complexity of DRSN is similar to that of a traditional fully connected neural network, $O(n^2)$, where $n$ is the number of input samples. This is because, in each convolution layer, convolution and pooling operations need to be performed for each input sample, and the results are then passed to the next layer. During backward propagation, the time complexity of DRSN depends on the implementation of the back propagation algorithm. If the standard back propagation algorithm is used, the time complexity is $O(nm)$, where $n$ is the number of samples and $m$ is the number of parameters in the network. This is because for each parameter, a gradient calculation needs to be performed, and the time complexity of computing a gradient for each one is $O(n)$.

The time complexity of this model is mainly reflected in the training process, so we discuss the time complexity of the training process. Due to the shared weights in the convolution layer, the size of the convolution kernel directly determines the training time complexity of the model. In this paper, a $3 \times 3$ convolution kernel is used, so its time complexity will be much smaller than the model uses $5 \times 5$ or $7 \times 7$ convolution kernel. The model structure also adopts a general DRSN structure, and there is no significant increase in network depth or the number of residual shrinkage units, so there is no significant improvement in time complexity. In addition, this paper adopts BiGRU, where the forgetting gate has forgetting characteristics, which can effectively avoid the gradient explosion problem happened during the training process. Overall, the time complexity of the entire model is controllable. When deploying the model, it is necessary to consider factors, such as the real-time requirements of the application scenario and the amount of data, and provide necessary computational support according to actual needs.