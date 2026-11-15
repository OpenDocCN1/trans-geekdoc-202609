
where z₀ and zₚ are actual measured values and corresponding model values, zₜ are the average values of the evading index, and N is the total number of input data. The correlation coefficient (R) is valued from [−1, 1]. The absolute value of R close to 1 means a successful prediction.

## 19.6 Results and Discussion

Both types of neural networks (feed forward backpropagation and radial basis function) were combined with meta-heuristic algorithms (GA, PSO, CBO, ECBO). Meta-heuristic algorithms were used in the neural network in the training function. Comparison and examination of the results are displayed in different charts. These results include mean square error, root mean square error and correlation coefficient (R) etc. Figure 19.3 is related to feed forward neural network combined with CBO algorithm, which is displayed in four parts related to all data, training data, test data and validation data. Figure 19.4 is related to the radial basis function neural network combined with the CBO algorithm. Figures 19.5 and 19.6 show the results of feed forward and radial basis neural network combined with ECBO algorithm respectively. For brevity, in Figs. 19.4, 19.5, and 19.6, only the graphs related to the train data are given.

The correlations comparison of the test data for the four algorithms used in combination with the feed forward backpropagation neural network and radial basis function neural network are shown in Figs. 19.7 and 19.8.

As it is clear in Figs. 19.7 and 19.8, the forward method has created a better correlation than the radial method in the test data, and the ECBO algorithm shows better performance compared to other algorithm. The comparison of mean square error in feed forward backpropagation and radial basis function neural network is given in Figs. 19.9 and 19.10.

The graph comparing the mean square error of the train data in feed forward backpropagation and radial basis function method is as follows in Figs. 19.11 and 19.12.

The percentage of error in each of the used algorithms, separated by the percentage of train, test and validation for the feed forward backpropagation neural network and the radial basis function neural network, is shown below in Figs. 19.13 and 19.14.

The cost function considered in the used artificial neural networks is the mean squared error. The optimization of this cost function has been done by different meta-heuristic algorithms. The convergence diagrams of these cost functions for feed forward and radial basis function neural networks are shown in Figs. 19.15 and 19.16, respectively.

Table 19.2 shows error and performances values obtained by FFB.
Table 19.3 shows error and performances values obtained by RBF.

### All Data-CBO

![](img/4048998719320644ee88964326fd7995_375_0.png)

### R = 0.77625

![](img/4048998719320644ee88964326fd7995_375_1.png)

### MSE = 0.031744, RMSE = 0.17817

![](img/4048998719320644ee88964326fd7995_375_2.png)

### μₗ = -0.002486, σ = 0.17855

![](img/4048998719320644ee88964326fd7995_375_3.png)

(a)

### Train Data-CBO

![](img/4048998719320644ee88964326fd7995_375_4.png)

### R = 0.79805

![](img/4048998719320644ee88964326fd7995_375_5.png)

### MSE = 0.02312, RMSE = 0.1448

![](img/4048998719320644ee88964326fd7995_375_6.png)

### μₗ = -0.0014484, σ = 0.16679

![](img/4048998719320644ee88964326fd7995_375_7.png)

(b)

Fig. 19.3 Feed forward backpropagation-CBO a all data, b train data, c test data, d validation data

### Test Data-CBO

![](img/4048998719320644ee88964326fd7995_376_0.png)

### R = 0.78002

![](img/4048998719320644ee88964326fd7995_376_1.png)

### MSE = 0.052389, RMSE = 0.22889

![](img/4048998719320644ee88964326fd7995_376_2.png)

### μ = 0.020587, σ = 0.23139

![](img/4048998719320644ee88964326fd7995_376_3.png)

(c)

### Validation Data-CBO

![](img/4048998719320644ee88964326fd7995_376_4.png)

### R = 0.73058

![](img/4048998719320644ee88964326fd7995_376_5.png)

### MSE = 0.029742, RMSE = 0.17246

![](img/4048998719320644ee88964326fd7995_376_6.png)

### μ = -0.031132, σ = 0.17226

![](img/4048998719320644ee88964326fd7995_376_7.png)

(d)

![](img/4048998719320644ee88964326fd7995_377_0.png)

Fig. 19.4 Radial basis function-CBO (train data)

![](img/4048998719320644ee88964326fd7995_377_1.png)

Fig. 19.5 Feed forward backpropagation-ECBO (train data)

![](img/4048998719320644ee88964326fd7995_378_0.png)

Fig. 19.6 Radial basis function-ECBO (train data)

![](img/4048998719320644ee88964326fd7995_378_1.png)

Fig. 19.7 Correlation comparison in feed forward backpropagation neural network

![](img/4048998719320644ee88964326fd7995_379_0.png)

Fig. 19.8 Correlation comparison in radial basis function neural network

![](img/4048998719320644ee88964326fd7995_379_1.png)

GA PSO CBO ECBO

Fig. 19.9 Mean square error in feed forward backpropagation

![](img/4048998719320644ee88964326fd7995_380_0.png)

Fig. 19.10 Mean square error in radial basis function

![](img/4048998719320644ee88964326fd7995_380_1.png)

Fig. 19.11 Mean square error in train data

## 19.7 Proposed ECBO-FFB Approach Formulation

The performance of artificial neural networks is possible when the weight of the network along with its bias values in different layers are known. Unlike many previous studies in which only the optimized network structure is presented, and in order to provide a simple method to achieve the presented results, the network weights along with the bias values in different layers for ECBO-FFB which provide better results than The rest of the compounds are presented in Table 19.4.

### Table 19.2 FFB model error and performances

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

### Table 19.3 RBF model error and performances

| Method | Parameters (RBF) | MAE (KN) | NMAE % | MAPE % | MSE | RMSE | NRMSE % |
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
