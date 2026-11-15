# Table 19.2 FFB model error and performances

| Method | Parameters (FFB) | MAE (KN) | NMAE % | MAPE % | MSE | RMSE | NRMSE % |
|---|---|---|---|---|---|---|---|
| PSO | Training | 0.0041 | 0.2101 | 4.8127 | 0.0446 | 0.2111 | 10.8704 |
| | Testing | 0.0391 | 2.4771 | 21.5315 | 0.0579 | 0.2406 | 15.2326 |
| GA | Training | 0.0019 | 0.0958 | 2.2343 | 0.0466 | 0.2158 | 11.1127 |
| | Testing | 0.0419 | 4.659 | 21.8103 | 0.0336 | 0.1833 | 20.3712 |
| CBO | Training | 4.62E–04 | 0.0231 | 0.5338 | 0.023 | 0.1478 | 8.2424 |
| | Testing | 0.0488 | 3.5923 | 18.1854 | 0.0302 | 0.1738 | 12.799 |
| ECBO | Training | 4.72E–05 | 0.0027 | 0.5450 | 0.0214 | 0.1464 | 7.4648 |
| | Testing | 0.0062 | 0.442 | 3.7712 | 0.0251 | 0.1641 | 11.1133 |

# Table 19.3 RBF model error and performances

| Method | Parameters (FFB) | MAE (KN) | NMAE % | MAPE % | MSE | RMSE | NRMSE % |
|---|---|---|---|---|---|---|---|
| PSO | Training | 0.0088 | 0.4707 | 1.2509 | 0.0456 | 0.2136 | 11.4265 |
| | Testing | 6.93E–04 | 0.0381 | 23.7015 | 0.0704 | 0.2654 | 17.5787 |
| GA | Training | 0.0055 | 0.2848 | 0.6486 | 0.0462 | 0.2151 | 11.0744 |
| | Testing | 0.0268 | 2.7673 | 23.3315 | 0.0601 | 0.2452 | 25.2877 |
| CBO | Training | 0.001 | 0.0506 | 0.1224 | 0.0346 | 0.186 | 9.6018 |
| | Testing | 0.043 | 2.7291 | 24.0525 | 0.0591 | 0.2431 | 15.4129 |
| ECBO | Training | 0.00086 | 0.4754 | 0.9700 | 0.0302 | 0.1739 | 9.3018 |
| | Testing | 0.0068 | 0.4959 | 4.5841 | 0.0323 | 0.1797 | 14.3471 |

The mathematical equation between the normalized input parameters (D, H, fco, Ef , ff , tf ) and the normalized output (fcc) is presented as follows:

```
f_cc = Tangent Sigmoid
\times \left\{ b_0 + \sum_{k=1}^n \left[ Tangent Sigmoid \times LW \left( b_{1k} + \sum_{i=1}^m (IW_{ik} Z_i) \right) \right] \right\} (19.10)
```

fcc represents the normalized FRP strength, “Tangent Sigmoid” is the activation function, n indicates hidden layer neuron numbers, Zi indicates the normalized values of network input, m is the number of the input variables, IWik indicates the linking weights between the ith input and kth neuron in the hidden layer, LW is the link weight between the kth neuron in the hidden layer and the independent output neuron, b1k shows the bias in the kth neuron of the hidden layer and b0 is the bias value in the output layer bond strength relation between the FRP composite and the concrete can be as follows.