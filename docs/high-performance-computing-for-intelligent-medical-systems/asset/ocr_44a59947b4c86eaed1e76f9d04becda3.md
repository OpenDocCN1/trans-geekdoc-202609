| | Specs | Score |
|---|---|---|
| 6 | numPeriodsPulses | 1864.725328 |
| 5 | numPulses | 1851.130248 |
| 0 | id | 397.462037 |
| 20 | class | 192.000000 |
| 1 | gender | 12.218525 |
| 15 | locDbShimmer | 5.659781 |
| 4 | RPDE | 1.785588 |
| 18 | apq11Shimmer | 0.812435 |
| 19 | ddaShimmer | 0.542172 |
| 14 | locShimmer | 0.540169 |
| 3 | DFA | 0.490823 |
| 17 | apq5Shimmer | 0.300749 |
| 16 | apq3Shimmer | 0.180714 |
| 2 | PPE | 0.154257 |
| 13 | ddpJitter | 0.108102 |
| 9 | locPctJitter | 0.093565 |
| 12 | ppq5Jitter | 0.065695 |
| 11 | rapJitter | 0.036044 |
| 7 | meanPeriodPulses | 0.017692 |
| 8 | stdDevPeriodPulses | 0.005754 |
| 10 | locAbsJitter | 0.000906 |

Figure 9.8. Representation of top most important features selects best classes.

# 9.5.5 Heat map

In this study we used Heat Map for observation target variables. Heat Map easily represents how features are correlated and easily finds which features are correlated with target variables (figure 9.10).

# 9.5.6 Evaluation of results after features selection

Table 9.3 represents experiment-III, we find the results after features selection. The Bagging Ensemble Method for Kappa (0.958), Overall Fraction Correct (0.98), Miss-classification Rate (0.02), Sensitivity (0.979), Specificity (0.983) and Prevalence (0.62) is better compared to all other selected algorithms, ‘Naïve Bayes, Decision Tree, Extra Tree and Random Forest’.

In figure 9.11, find the result Kappa (high), Overall Fraction Correct (high), Miss-classification Rate (low) and Sensitivity (high) compared with other algorithms.

# 9.6 Discussion

After all the experiments and their results we discuss the better performance of classifiers. In table 9.2 and figure 9.8, we find ‘Naïve Bayes, Decision Tree, Extra Tree, Random Forest and Bagging Ensemble’ have Kappa, 0.248, 0.304, 0.35, 0.563, **0.589**; Overall Fraction Correct, 0.63, 0.656, 0.683, 0.782, **0.795**; Mis-classification Rate, 0.37, 0.344, 0.317, 0.218, **0.205**; Sensitivity, 0.749, 0.749, 0.761, 0.774, **0.799**; Specificity, 0.496, 0.552, 0.585, 0.79, **0.79** and Prevalence, 0.528,