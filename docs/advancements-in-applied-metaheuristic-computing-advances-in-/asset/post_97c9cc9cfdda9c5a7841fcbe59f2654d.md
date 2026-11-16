
The sigmoid normalization method has been used to normalize the original input signals as shown by Equation 5 (Nayak et al., 2012, 2014).

```
x_{norm} = \frac{1}{1 + e^{-\frac{(x_i - x_{min})}{(x_{max} - x_{min})}}}
```

Where \( x_{norm} \) is the normalized price, \( x_i \) is the current day closing price, \( x_{max} \) and \( x_{min} \) are the maximum and minimum price of the window respectively. The data within the current training set are normalized within [0, 1].

## 4.3 Experimental Setup

The normalized values are now considered as the input vector to the model. Let \( X(n) = [x_1, x_2, \cdots, x_n] \) be the normalized closing prices. Let \( W(n) = [w_1, w_2, \cdots, w_n] W(n) = [w_{11}, w_{12}, w_{13} \cdots, w_{n1} w_{n2}, w_{n3}] \) represent the elements of a weight vector associated with the input vector \( X(n) \) at the summing unit neuron as shown in Figure 3. Each input pattern \( X(n) \) is applied to the model sequentially and the desired closing prices value is supplied at the output neuron. Given the input, the model produces an output \( y(n) \), which acts as an estimate to the desired value.

The error signal \( e(n) \) is calculated as the difference between the desired response and the estimated output of the model. This is represented as in Equation 6.

```
e(n) = d(n) - y(n)
```

The error signal \( e(n) \) and the input vectors are employed to the weight update algorithm to compute the optimal weight vector.

Figure 5 shows the individual representation in GA for both MLP and RNN as they have one hidden layer.

Figure 6 presents the individual representation for ASONN-GA.

Figure 5. Individual representation of MLP and RNN model

| Weight Vector | Bias Values |
| :--- | :--- |
| Input and Hidden Layer: \( w_{11}, w_{12}, \dots, w_{nn} \) | Hidden: \( B_1 \cdots \cdots B_n \) |
| Hidden and Output Layer: \( v_1, v_1, \dots, v_n \) | Output: \( b_o \) |

Figure 6. Individual representation of ASONN-GA model

| Weight Vector | Bias Values |
| :--- | :--- |
| Input and Hidden Layer: \( w_{11}, w_{12}, \dots, w_{rm} \) | Hidden: \( B_h \dots\dots B_n \) |
| Hidden and Output Layer: \( v_1, v_1, \dots, v_n \) | Output: \( b_o \) |

To overcome the demerits of GD based back propagation, we employed the GA which is a popular global search optimization. We adopted the binary encoding for GA. Each weight and bias value constitute of 15 binary bits. For calculation of weighted sum at output neuron, the decimal equivalent of the binary chromosome is considered. A randomly initialized population with 50 genotypes is considered. GA was run for maximum 100 generations with the same population size. Parents are selected from the population by elitism method in which first 10% of the mating pools are selected from the best parents and the rest are selected by binary tournament selection method. A new offspring is generated from these parents using uniform crossover followed by mutation operator. In this experiment the crossover probability is taken as 0.5 and mutation probability is taken as 0.003. In this way the new population generated replaces the current population and the process continues until convergence occurs. The fitness of the best and average individuals in each generation increases towards a global optimum. The uniformity of the individuals increases gradually leading to convergence. Extensive experiments have been conducted and average results of 10 simulations have been collected. The same data sets are provided to each forecasting model and the computation time have been recorded. Table 2 summarizes the computation times for different models for different financial time series. It can be observed that the RNN model requires more computational time as compared to MLP due to more number of weight values. There is a substantial reduction in computational time in case of ASONN-GA as compared to MLP and RNN due to absence of hidden layer and simple architecture. The mean absolute errors (MAE) of 10 simulations from each model are considered for comparison and represented by Equation 7.

```
MAE = \frac{1}{10} \sum_{j=1}^{10} (\frac{1}{N} \sum_{i=1}^{N} |actual - estimated|) (7)
```

```
MAE = \frac{1}{10} \sum_{j=1}^{10} (\frac{1}{N} \sum_{i=1}^{N} |actual closing prices - estimated closing prices|)
```

Further, to find out the exact benefit of using higher order neural network based forecasting model over other models for different stock indices, performance gain is evaluated as follows at Equation

```
Performance Gain = 
\frac{(MAE of existing model - MAE of SONN model)}{MAE of existing model} 
(8)
```

## 4.4 Results Analysis From Closing Price Data

This sub section presents and analyses the prediction accuracies obtained from all the three forecasting models for the prediction of one-step-ahead closing price. Separate experiments have been conducted for the aforementioned real stock market time series. Table 3 presents the prediction error signals.

Table 3. Prediction error generated by MLP, RNN, and ASONN-GA for all closing price series

| | | MLP | RNN | ASONN-GA |
|---|---|---|---|---|
| **BSE** | Minimum | 0.000140 | 0.000100 | 0.000100 |
| | Maximum | 0.057200 | 0.060200 | 0.063700 |
| | Average | **0.014433** | **0.013958** | **0.013100** |
| | Std.Deviation | 0.011398 | 0.011247 | 0.011114 |
| **DJIA** | Minimum | 0.000000 | 0.000100 | 0.000000 |
| | Maximum | 0.030400 | 0.032000 | 0.031400 |
| | Average | **0.008060** | **0.008632** | **0.008024** |
| | Std.Deviation | 0.006975 | 0.006857 | 0.006928 |
| **NASDAQ** | Minimum | 0.000000 | 0.000000 | 0.000000 |
| | Maximum | 0.063400 | 0.057300 | 0.050300 |
| | Average | **0.016045** | **0.012511** | **0.010741** |
| | Std.Deviation | 0.013033 | 0.010415 | 0.008918 |
| **FTSE** | Minimum | 0.000000 | 0.000100 | 0.000000 |
| | Maximum | 0.073900 | 0.031100 | 0.032100 |
| | Average | **0.014741** | **0.008106** | **0.007910** |
| | Std.Deviation | 0.012637 | 0.006813 | 0.006802 |

From Table 3 it can be observed for BSE data set that the ASONN-GA model generates minimum average error, i.e. 0.013100 values as compared to MLP and RNN. RNN has an overall performance similar to that of MLP model. Comparing the performance of ASONN-GA to MLP and RNN, there is a gain in performance of 9.23515% and 6.147012% respectively.

For DJIA, MLP gives superior results as compared to RNN. However, the performance of ASONN-GA dominates that of MLP and RNN generating a minimal error of 0.008024. By adopting ASONN-GA, there is a % gain in performance of 0.445635% and 7.036159% as compared to MLP and RNN respectively.

The NASDAQ data set is provided to MLP, RNN and ASONN-GA model separately. Here also the ASONN-GA performs better than MLP and RNN. It can be observed that the ASONN-GA model generates lowest error value. It achieves significant better result over MLP and RNN. The % gain in error values are 33.05931% and 14.14995% when compared with MLP and RNN respectively.

The three forecasting models are employed to forecast the next day’s closing prices of FTSE financial time series. Here the RNN and ASONN-GA model give quite superior results as compared to MLP. The ASONN-GA model achieves 46.3386% and 2.4176% gain in performance as compared to MLP and RNN respectively. From the results the superiority of the ASONN-GA forecasting model has been very clearly established.

From the above discussed empirical results, it can be clearly established that the ASONN-GA model achieves better forecasting accuracies over other two conventional neural based models. To make it more clear the performance gain of ASONN-GA over MLP and RNN are calculated as in Equation 8. It can be observed that the ASONN-GA model gains a highest performance improvement over MLP for FTSE data, i.e. 46.3385% and lowest in case of DJIA, i.e. 0.445635%. The trend repeats for performance gain of ASONN-GA over RNN. There is a maximum performance gain over RNN in case of NASDAQ, i.e. 33.05931% and a minimum of 2.417577% in case of FTSE. On an average ASONN-GA achieves 22.26965% performance gain over MLP and 7.437674% over RNN while considering all the four data sets. The actual v/s estimated prices by the proposed ASONN-GA model are plotted and presented by Figure 7 - 10 for BSE, DJIA, NASDAQ, and FTSE respectively. From these figures it can be observed that the proposed model is quite able to estimate future prices very closer to the actual values.

## 4.5 Results Analysis From Exchange Rate Data

This sub section presents and analyses the prediction accuracies obtained from all the three forecasting models for the prediction of one-step-ahead exchange rate price.
