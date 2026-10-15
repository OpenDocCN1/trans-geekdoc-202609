Table 6. Performances of Bankruptcy Prediction Model using F-measure.

| Feature selection methods | Classifiers | 1st year | 2nd year | 3rd year | 4th year | 5th year |
|---|---|---|---|---|---|---|
| SBS | SBSAda-Rip | 97.1 | 96.1 | 95.8 | 96.1 | 94.3 |
| SBS | AdaBoost+ C4.5 | 95.6 | 95.4 | 94.8 | 93.8 | 93 |
| SBS | AdaBoost+OneR | 95.8 | 94.9 | 94.2 | 94 | 93.2 |
| SBS | AdaBoost+PART | 96.5 | 95.8 | 95.5 | 93.7 | 91.3 |
| SBS | AdaBoost+CART | 96.2 | 95.8 | 94.7 | 95.3 | 93.6 |
| SBS | AdaBoost+RF | 94.6 | 95.3 | 94.9 | 93.1 | 92.9 |
| SFS | AdaBoost+JRip | 96.8 | 95.8 | 96.1 | 95.6 | 94.4 |
| SFS | AdaBoost+ C4.5 | 95.7 | 95.2 | 95.1 | 93.1 | 92.5 |
| SFS | AdaBoost+OneR | 95.5 | 94.5 | 94.1 | 93.9 | 93 |
| SFS | AdaBoost+PART | 96.8 | 95.4 | 95.3 | 94 | 93 |
| SFS | AdaBoost+CART | 96.9 | 95.3 | 94.7 | 95.3 | 93.6 |
| SFS | AdaBoost+RF | 95.7 | 94.9 | 94.5 | 92.9 | 93 |
| PSO | AdaBoost+JRip | 96 | 96.4 | 95.7 | 95.2 | 94.1 |
| PSO | AdaBoost+ C4.5 | 95.2 | 95.9 | 94.6 | 93.7 | 92.5 |
| PSO | AdaBoost+OneR | 94.9 | 94.3 | 94.4 | 93.5 | 93.2 |
| PSO | AdaBoost+PART | 94.9 | 95.2 | 94.7 | 93.8 | 92.4 |
| PSO | AdaBoost+CART | 96.5 | 95.3 | 94.7 | 95.2 | 93.6 |
| PSO | AdaBoost+RF | 94.6 | 94.8 | 94.1 | 93.1 | 92.4 |
| RSFS | AdaBoost+JRip | 96.8 | 96.5 | 95.3 | 95 | 94.2 |
| RSFS | AdaBoost+ C4.5 | 95.1 | 95.4 | 94.5 | 93.6 | 92.4 |
| RSFS | AdaBoost+OneR | 94.7 | 94.3 | 94.4 | 93.8 | 93.4 |
| RSFS | AdaBoost+PART | 94.9 | 95 | 94.4 | 93.7 | 93.1 |
| RSFS | AdaBoost+CART | 96.5 | 95.1 | 94.7 | 95.4 | 94.2 |
| RSFS | AdaBoost+RF | 94 | 95.5 | 94 | 92.9 | 91.9 |

# 5.6.3. Results for Research Question 2

Numerous studies have been successful in predicting corporate bankruptcy. Thus, we analyze the performance of our approach with that of different techniques conducted on the same Polish datasets. Table 7 presents the results of other studies and our own. This comparison takes into account two factors: the AUC measure and the interpretability of the models. The interpretability examines the ability of the classifier in extracting decision rules, the number of these rules, and the number of the extracted features.