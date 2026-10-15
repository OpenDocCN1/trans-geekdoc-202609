could have negative effects on consumer health [63]. On the other hand, values below 50 ppb were considered permissive. It was in our interest to classify the samples as suitable for consumption (tylosin concentrations < 50 ppb) or unsuitable for consumption (tylosin concentrations ≥ 50 ppb). For this, the multilayer perceptron neural network (MLP) technique was used.

The MLP operated in multistart mode, obtaining a better fit with a network with architecture consisting of two hidden layers (6,3), using a logistical activation function. A multiclass factor that corresponds to the origin of the milk was included in the data set due to the effect related to the complexity of the matrix (including interferences such as sugars, proteins, fat, urea and other soluble solids) alongside other 16 wave numbers (cm⁻¹) of interest. The performance in the discriminant analysis of real milk samples by several machine learning algorithms, logistic regression (LogR), partial least squares discriminant analysis (PLS-DA), CART, GBT and RF are compared below with the MLP reference previously developed (Table 3.3).

# Table 3.3. Quality parameters of the discriminatory analysis of a test subset containing 33 milk samples by the logistic regression model (LogR), PLS-DA, CART, GBT, RF and MLP.

| Model | True + | False + | True - | False - | Accuracy | CI - | CI + | Kappa | Sensitivity | Specicity | p |
|---|---|---|---|---|---|---|---|---|---|---|---|
| LogR | 8 | 7 | 6 | 12 | 0.424 | 0.255 | 0.608 | -0.13 | 0.461 | 0.400 | 0.989 |
| PLS-DA | 17 | 11 | 2 | 3 | 0.576 | 0.392 | 0.745 | 0.004 | 0.154 | 0.850 | 0.706 |
| CART | 20 | 13 | 0 | 0 | 0.606 | 0.421 | 0.771 | 0 | 0 | 1.000 | 0.575 |
| GBT | 18 | 2 | 11 | 2 | 0.878 | 0.718 | 0.966 | 0.746 | 0.846 | 0.900 | 6.02E-4 |
| RF | 18 | 1 | 12 | 2 | 0.909 | 0.757 | 0.981 | 0.812 | 0.923 | 0.900 | 1.16E-4 |
| MLP [28] | 20 | 0 | 13 | 0 | 1.000 | 0.894 | 1.000 | 1.000 | 1.000 | 1.000 | 6.65E-8 |

Taking into account the low concentrations of the contaminant, it is expected that the matrix effect will become very prevalent. For the same reasons discussed in the previous section, GBT and RF obtained satisfactory results in predicting the classes compared to the other algorithms, obtaining only two false negatives and a prediction accuracy > 0.85, with a confidence interval, CI, which includes the level of accuracy obtained by MLP. Classification trees, on the other hand, was insensitive to the negative class (C < 50 ppb) and irrelevant results were obtained with the parametric algorithms (LogR and PLS-DA). This is a strong indication of the trend of the non-linear distribution of the response. Only the last three models, including the two techniques based on an ensemble of decision trees with a resampling mechanism, produced statistically significant results (p <0.05).