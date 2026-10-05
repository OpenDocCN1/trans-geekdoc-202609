# 142 Soft Computing and Machine Learning with Python

**Table 1**: Item reliability, item fit, person reliability, person fit and used by instrument

| Test | Item reliability | Item INFIT (mean, SD) | Person reliability | Person INFIT (mean, SD) | Model |
|---|---|---|---|---||}{
| Inductive reasoning development test (TDRI) | 1.00 | .98, .17 | .85 | .98 | Dichotomous Rasch Model |
| TDRI's self-appraisal test (SA TDRI) | .98 | .98, .11 | .79 | .97, .31 | Dichotomous Rasch Model |
| Metacognitive control test (TCM) | .99 | 1.00, .13 | .80 | .99 | Dichotomous Rasch Model |
| TCM's self-appraisal test (SA TCM) | .98 | 1.02, .26 | .74 | .98, .20 | Dichotomous Rasch Model |
| Brazilian learning approaches scale—Deep learning items (DeepAP) | .99 | 1.00, .08 | .80 | 1.01, .69 | Partial Credit Rasch Model |
| Inductive reasoning development test (TDRI) | 1.00 | .98, .17 | .85 | .98, .91 | Dichotomous Rasch Model |

Total accuracy is the proportion of observations correctly classified:

```
$Acc = \frac{1}{n|T_E|} \sum_{x_i \in T_E} (y_i = C_k)$
```

where $n|T_E|$ is the number of observations in the testing set. In spite of being an important indicator of the measure of the general prediction's quality, the total accuracy is not an informative measure of the errors in each class. For example, a general accuracy of 80% can represent an error-free prediction for the C1 class, and an error of 40% for the C2 class. In the educational scenario, it is preferable to have lower error in the prediction of the low achievement class, as students at risk of academic failure compose this class. So, the sensitivity will be preferred over general accuracy and specificity. The sensitivity is the rate of observations correctly classified in a target class, e.g. C1 = low achievement, over the number of observations that belong to that class:

```
$Sens = \frac{\sum_{y_i \in T_E} 1(y_i = C_1)}{\sum_{y_i \in T_E} (C_1)}$
```

Specificity, on the other hand, is the rate of correctly classified observations of the non-target class, e.g. C2 = high achievement, over the number of observations that belong to that class: