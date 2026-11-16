complex relationships between these variables. The output layer after employing a sigmoid activation function produces a prediction between 0 and 1and represents the likelihood of an individual having hypertension (Koul et al. 2022). Mathematically, it can be computed as shown in Equation (7) 

$$y = f(WxT + b)$$

where activation function is f, W defines the set of parameters, x in the input vector and b is the bias vector.

# 3.6 Evaluative metrics

Precision, accuracy, recall, as well as F1 score are fundamental metrics used for assessing the performance of classifiers (Kumar et al. 2021) (Table 1).

Table 1. Formulae of evaluative parameters.

| Metrics | Formulae |
|---|---|
| Accuracy | $\frac{True Positive + True Negative}{True Positive + True Negative + False Positive + False Negative}$ |
| Precision | $\frac{True Positive}{True Positive + False Positive}$ |
| Recall | $\frac{True Positive}{True Positive + False Negative}$ |
| F1 score | $2 \times \frac{Precision \times Recall}{Recall + Precision}$ |

# 4 RESULTS

In this section, the performance of the applied learning approaches has been assessed using the parameters listed in sec 3.6. Figure 4 shows a confusion matrix of size 2x2 that has been generated to compute the predicted and actual value of the binary class of hypertension dataset for different methods.

![](bbox=[0.22, 0.58, 0.78, 0.89])

Figure 4. Confusion matrix of the applied classifiers.