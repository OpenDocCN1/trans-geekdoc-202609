**Table 1**
Detail of communication parameters configurations.

| Protocol layer | Parameter | Number of distinct values | Proposed values | Rationale |
|---|---|---|---|---|
| Physical | TP: Transmission Power (dBm) | 5-6 | -7, -5, -3, -1, 1, 3 | TP values are empirically chosen |
| | NN: Number of Active Nodes | 3 | 8, 16, 24 | 8, 16 and 24 sender nodes are used for transmission |
| | MT: Maximum Transmissions | 3 | 2, 4, 6 | To characterize packet delivery behavior |
| Application | PS: Packet Size (Bytes) | 3 | 25, 50, 75 | 802.15.4 accommodates small packet sizes |
| | IAT: Inter-Arrival Time (s) | 4 | NN = 8 | 2, 4, 6, 8 | The load ranges from very low to very high |
| | | | NN = 16 | 4, 6, 8, 10 | |
| | | | NN = 24 | 6, 8, 10, 12 | |

are provided as input to the ML models to figure out the prediction error. Mean Absolute Error (MAE) is used as the primary evaluation metric. Training is done using 55% of the data, with 15% data being used for validation. The remaining 30% of the data is used for testing.

# 2.3. Prediction model

ML offers huge potential in making QoS predictions in wireless scenarios. Since the QoS parameters like PDR, THP, as well as EC, are continuous, therefore regression-based models are suited for predicting such variables. We adopted a 10 layers DNN using JupyterHub running GPU-enabled notebook with Tensorflow and Keras API. The versatile constructs available in deep learning demonstrate very good prediction potential.

Considering the 8 proposed parameters and 8 metrics (PDR, THP, CPU, LPM, DLP, LSN, TX, and Off) to be predicted, the data can be represented using the following vector:

```
f_{(n,1)}, f_{(n,2)}, f_{(n,3)}, f_{(n,4)}, f_{(n,5)}, f_{(n,6)}, f_{(n,7)}, f_{(n,8)}, f_{(n,9)}, f_{(n,10)},
f_{(n,1.1)}, f_{(n,1.2)}, PDR, THP, CPU, LPM, DLPM, LSN, TX, Off
```

Where f and n represent input features (parameters) and row (record) number, whereas PDR, THP, CPU, LPM, DLPM, LSN, TX, and OFF are the metrics to be predicted using ML. This data is input to the DNN. The computation in DNN consists of the forward and backward passes. A forward pass is calculated using:

```
O_{[l]}^i = W_{[l]}^i \cdot X_{[l-1]}^i + c_{[l]}^i,
X_{[l]}^i = f_{(l)}(O_{[l]}^i),
```

where l represents the current layer, and O, W, X, C, and f represent output, weights of the inputs, a regression parameter, and an activation function, respectively. The activation function (e.g., ReLU) is applied to the output O to achieve input X for the next layer. Following a forward pass, a backward pass, where d represents the derivative, is calculated using:

```
dO_{[l]}^i = dX_{[l]}^i \times df_{(l)}(O_{[l]}^i).
dW_{[l]}^i = \frac{1}{n}(dO_{[l]}^i \cdot X_{[l]^T}^i),
dc_{[l]}^i = \frac{1}{n} \sum_{l=1}^n O_{[l]}^i,
dX_{[l-1]}^i = W_{[l]^T}^i \cdot dX_{[l]}^i,
```

Here T represent the transpose of relevant matrix. In order to update the weights and regression parameter, gradient descent is executed using:

```
W_{[l]}^i = W_{[l]}^i - \alpha \times dW_{[l]}^i.
```

```
b_{[l]}^i = b_{[l]}^i - \alpha \times dc_{[l]}^i.
```

The value for alpha is set to 0.001. The conventional values used for alpha are 0.1, 0.01, and 0.001. This choice of 0.001 is made empirically in this case. Before applying and evaluating the ML performance, the statistical (Pearson) correlations are calculated between the parameters and QoS metrics aiming to develop insight into the relationship between parameters and metrics under consideration. To evaluate the test data using the above-mentioned ML models, we use MAE as a metric. The whole workflow of the experiment and predictions is given in Fig. 3. As the proposed system is data-driven, it begins with a data source. The data can be in the form of a pre-recorded instance (and/or simulation) for bootstrapping the system. Any such data will have an underlying topology and parameters configuration. However, as the system run into production, it is supposed to interact with real deployments and collect live data from different installations of the WSN infrastructure in the IoT. The data needs to be pre-processed to achieve a structured format representing the communication parameters as features and the QoS metrics as labels or targets. This pre-processed data is shown in the form of a simple 2-dimensional table consisting of rows and columns. The data divided into train and test splits is passed through learning models to achieve sufficient accuracy. This first phase of training is carried out offline. Considering the accuracy and efficiency, a suitable model can be chosen for deployment.

# 3. Statistical analysis

In the following, an pictorial analysis of the relationship among the communication parameters and QoS metrics is presented.

# 3.1. Packet Delivery Ratio

The relationship of PDR with different communication parameters is shown in Fig. 4. The effect of NN and TP is revealed in Fig. 4(a). There is a very clear dropping trend in PDR as NN increase and TP decrease. The effect of NN alongside PS is shown in Fig. 4(b). The PDR decreases as PS increases in addition to the increase in NN. This confirms the trend observed in Fig. 4(a). The effect of NN and MT is depicted in Fig. 4(c). The 50th percentile of PDR tends to fall a little as MT increases, whereas, 25th percentile of PDR rises somewhat. This dual trend explains both the challenging conditions when higher values of MT are uses as well a positive impact of more transmission attempts. Fig. 4(d) highlights the impact of MT and TP on PDR. An increase in both TP and MT causes a rise in PDR values. The effect of PS and TP unveils the same trend (Fig. 4(e)) as witnessed in Fig. 4(d) in case of MT and TP. Smaller packets at a higher TP level make it more possible to reach the destination. Fig. 4(f) reveals the effect of PS and likely to reach PDR. It is again evident that PDR is