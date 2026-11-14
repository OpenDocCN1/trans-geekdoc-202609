In most cases, two approaches, grid search and random search, can provide an acceptable configuration of hyper-parameters for a certain data set. Since there exist 19 hyper-parameters in the proposed MDNN, it is extremely time-consuming to assess all possible combinations of hyper-parameters. In the training process of the proposed MDNN, an initial guess of structural parameters is chosen to fix the network architecture referred to the successful practices in previous studies.\(^\text{35,58,59}\) To reduce the complexity of hyper-parameter optimization, the numbers of neurons in the hidden layers were scanned while the layer number of each task-specific FNN was fixed at four (three hidden layers and one output layer), since there were no significant improvements for more layers. Afterwards, a grid search was applied to find the optimal ranges of other hyper-parameters initially. The hyper-parameters were also fine-tuned into the optimal range manually. Herein, one or two hyper-parameters were tuned at a time manually, it should be observed whether the MDNN performance was improved on the validation sets after manual tuning. The finally adopted configuration of hyper-parameters are listed in Tables 5 and 6. After all the hyper-parameters were determined and validated, the model was tested on an external test eventually.

# 2.2.4 Statistical evaluation.

The following statistical indicators were employed as the performance metrics to evaluate the learned MDNN model.

Mean absolute error (MAE) is the measure of deviation between the predicted values and the experimental values, and it is obtained *via* eqn (4).

\(\text{MAE} = \frac{\sum_{i=0}^N |x_i^{\text{exp}} - x_i^{\text{pre}}|}{N}\) (4)

Table 5 The finally adopted structural hyper-parameters of the MDNN

| Hyper-parameters | Values |
|---|---|
| The dimension of embedding vectors | 48 |
| The memory dimension of the Tree-LSTM | 32 |
| The output dimension of the Tree-LSTM | 32 |
| The hidden layers of each task-specific FNN | 3 |
| The neuron number of each hidden layers in the FNNs | 32 |

Table 6 The finally adopted hyper-parameters of the training optimizers

| Hyper-parameters | Values | Tasks |
|---|---|---|
| The learning rate \(\eta_t\) | 0.020000 | Jointly, training the whole MDNN according to all properties |
| The learning rate \(\eta_1\) | 0.00120 | Alternatively, training the Tree-LSTM network according to FPT |
| The learning rate \(\eta_2\) | 0.00120 | Alternatively, training the Tree-LSTM network according to AIT |
| The learning rate \(\eta_3\) | 0.0006 | Alternatively, training the Tree-LSTM network according to LFL |
| The learning rate \(\eta_4\) | 0.00023 | Alternatively, training the Tree-LSTM network according to UFL |
| The learning rate \(\eta_1\) | 0.00120 | Alternatively, training the task-specific FNN according to FPT |
| The learning rate \(\eta_2\) | 0.00180 | Alternatively, training the task-specific FNN according to AIT |
| The learning rate \(\eta_3\) | 0.00009 | Alternatively, training the task-specific FNN according to LFL |
| The learning rate \(\eta_4\) | 0.00020 | Alternatively, training the task-specific FNN according to UFL |
| The batch size \(b_t\) | 32 | Jointly, training the whole MDNN according to all properties |
| The batch size \(b_1\) | 32 | Alternatively, for the Tree-LSTM and FNN corresponding to FPT |
| The batch size \(b_2\) | 32 | Alternatively, for the Tree-LSTM and FNN corresponding to AIT |
| The batch size \(b_3\) | 32 | Alternatively, for the Tree-LSTM and FNN corresponding to LFL |
| The batch size \(b_4\) | 32 | Alternatively, for the Tree-LSTM and FNN corresponding to UFL |

Mean percentage error (MPE) provides an average of percentage error by which the predicted values differ from the experimental values, and it is expressed as eqn (5).

\(\text{MPE} = \frac{1}{N} \sum_{i=0}^N \frac{|x_i^{\text{exp}} - x_i^{\text{pre}}|}{x_i^{\text{exp}}} \times 100\%\) (5)

Since the correlation analysis reported in the published literatures\(^\text{21,22,24,32,33,60,61}\) usually chose the correlation coefficients of \(r\) or \(R^2\) as the performance indicator, both of them were employed to assess the proposed MDNN in this research. The Pearson correlation coefficient,

\(r = \frac{\sum_{i=1}^n (x_i^{\text{exp}} - \overline{x^{\text{exp}}})(x_i^{\text{pre}} - \overline{x^{\text{pre}}})}{\sqrt{\sum_{i=1}^n (x_i^{\text{exp}} - \overline{x^{\text{exp}}})^2} \sqrt{\sum_{i=1}^n (x_i^{\text{pre}} - \overline{x^{\text{pre}}})^2}}\) (6)

The coefficient of determination,

\(R^2 = 1 - \frac{\sum_{i=1}^n (x_i^{\text{exp}} - x_i^{\text{pre}})^2}{\sum_{i=1}^n (x_i^{\text{exp}} - \overline{x^{\text{exp}}})^2}\) (7)

# 2.3 The outlier detection and AD determination

The outlier detection was also studied for deep learning based QSPRs in this work. The outliers of four tasks were detected with the empirical cumulative distribution function (ECDF) of the residuals between experimental and predicted values. The ECDF is a step function that increases by 1/n in every data point. Let \((X_1, ..., X_n)\) be independent, identically distributed real random variables with the common cumulative distribution function \(F(t)\), then the ECDF can be defined as shown in eqn (8) for a realization \((x_1, ..., x_n)\).

\(\widehat{F}_n(t) = \frac{\text{number of element in the sample } \le t}{n} = \frac{1}{n} \sum_{i=1}^n I_{X_i \le t}\) (8)

For a fixed \(t\), the indicator \(I_{X_i \le t}\) is a Bernoulli random variable with parameter \(p = F(t)\). The value of the ECDF is the