# Intrusion Detection on NF-BoT-IoT Dataset Using Artificial Intelligence

Figure 12.

![](bbox=[0.13, 0.15, 0.45, 0.34])

|  | precision | recall | f1-score | support |
|---|---|---|---|---|
| Benign | 0.000000 | 0.000000 | 0.000000 | 2662.000000 |
| DDoS | 0.000000 | 0.000000 | 0.000000 | 11367.000000 |
| DoS | 0.000000 | 0.000000 | 0.000000 | 11262.000000 |
| Reconnaissance | 78.626062 | 100.000000 | 88.034256 | 94367.000000 |
| Theft | 0.000000 | 0.000000 | 0.000000 | 362.000000 |
| accuracy | 78.626062 | 78.626062 | 78.626062 | 0.786261 |
| macro avg | 15.725212 | 20.000000 | 17.606851 | 120020.000000 |
| weighted avg | 61.820577 | 78.626062 | 69.217869 | 120020.000000 |

Figure 13.

```
modelName = 'ANN'
tf.keras.utils.plot_model(model,'./'+modelName+'_Archi.png',show_shapes=True)
model.summary()
```

Model: "sequential"

| Layer (type) | Output Shape | Param # |
|---|---|---|
| dense (Dense) | (None, 10) | 80 |
| dense_1 (Dense) | (None, 40) | 440 |
| dense_2 (Dense) | (None, 10) | 410 |
| dense_3 (Dense) | (None, 1) | 11 |
| dense_4 (Dense) | (None, 5) | 10 |

Total params: 951
Trainable params: 951
Non-trainable params: 0