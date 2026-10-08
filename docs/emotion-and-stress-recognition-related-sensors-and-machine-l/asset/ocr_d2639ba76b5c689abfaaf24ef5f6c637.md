# Table 3. Confusion matrix, user-independent regression model based on BVP and ST features is used for stress detection.

| True/Predicted | Non-Stressed | Stressed |
|---|---|--|
| Non-stressed | 88.0% | 12.0% |
| Stressed | 26.6% | 73.4% |

# Table 4. Subject-wise balanced accuracy using user-independent model and a combination of BVP and ST features.

| Subject | Classification (%) | Regression (%) |
|---|---|--|
| NM | 64.3 | 84.6 |
| RY | 90.8 | 93.7 |
| BK | 87.0 | 88.3 |
| MT | 49.0 | 50.5 |
| EK | 59.3 | 60.7 |
| KGS | 88.3 | 93.7 |
| AD | 96.3 | 99.7 |
| GM | 69.9 | 95.0 |
| SJ | 82.2 | 74.7 |
| Mean | 74.1 (ST 16.7) | 82.3 (ST 17.0) |

When regression models outperform classification models in stress detection, the real benefit of regression models is that, unlike classification, they can be used to estimate the level of stress. Figure 1 shows how regression models estimate the level of stress to reported stress level values. The figure shows that in most cases the regression model has has managed to predict the level of stress. However, this approximation is not very accurate, and it is inconsistent. This suggests that the trained regression model is very sensitive to small changes in feature values, and moreover, the approximation does not work for all subjects (study subjects MT, Figure 1d and in the case of SJ, Figure 1j). In the case of MT, the model has not to manage the non-stressed state, and in the case of SJ, the regression of stressed state has caused similar reactions to every person. Figure 1 suggests that personal stress does not divide using regression model outputs as stressed and non-stressed (black horizontal line). In most cases, the level of this threshold is between 0.3 and 0.5. However, also in the case of MT and SJ the value of threshold is close to 1, and in the case of SJ, the value is close to 0. This underlines how special these cases are compared to other study subjects.

Table 5 shows mean square error (RMSE) of reported values for each subject as stress. As the level of the baseline was not measured during the data gathering, it was gathered by a best guess, and therefore cannot be considered as fact. In fact, also the predictions in Figure 1 suggest that the level of the stress is not containing the baseline and neither is it. The second column shows the RMSE from the value of the signal, and the third column shows the RMSE calculated from only driving the part of the signal as it contains target values defined by there. For instance, in the case of MT subject, there is a difference between two. Moreover, the R-squared value was calculated from each subject, and they are indicating the fact that does not work for each subject. In fact, R-squared is zero for three study subjects indicating that for these persons user-independent model is not able to predict any variation on response. Overall, the results of the Table 5 show the potential of predicting the level of stress using regression models. However, it also shows that at this point of the research, it only works for some study subjects and the